---
description: PowerShell 7에 대 한 Windows PowerShell 호환성 기능을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_Compatibility
ms.openlocfilehash: 522c9d2169e49584915450813ad28dfc5e0d5ca2
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220817"
---
# <a name="about-windows-powershell-compatibility"></a>Windows PowerShell 호환성 정보

## <a name="short-description"></a>간단한 설명

PowerShell 7에 대 한 Windows PowerShell 호환성 기능을 설명 합니다.

## <a name="long-description"></a>자세한 설명

모듈 매니페스트가 PowerShell Core와 호환 되는 것으로 표시 되지 않는 한 폴더의 모듈은 `%windir%\system32\WindowsPowerShell\v1.0\Modules` Windows Powershell 호환성 기능을 통해 백그라운드 Windows powershell 5.1 프로세스에 로드 됩니다.

### <a name="using-the-compatibility-feature"></a>호환성 기능 사용

Windows PowerShell 호환성 기능을 사용 하 여 첫 번째 모듈을 가져오는 경우 PowerShell `WinPSCompatSession` 은 백그라운드 Windows powershell 5.1 프로세스에서 실행 되는 라는 원격 세션을 만듭니다. 이 프로세스는 호환성 기능이 첫 번째 모듈을 가져올 때 생성 됩니다. 마지막 해당 모듈이 제거 되거나 (를 사용 하 여 `Remove-Module` ) PowerShell 프로세스가 종료 되 면 프로세스가 닫힙니다.

세션에서 로드 된 모듈은 `WinPSCompatSession` 암시적 원격을 통해 사용 되며 현재 PowerShell 세션에 반영 됩니다. PowerShell 작업에 사용 되는 것과 동일한 전송 방법입니다.

모듈을 세션으로 가져올 때 `WinPSCompatSession` 암시적 원격은 사용자의 디렉터리에 프록시 모듈을 생성 `$env:Temp` 하 고이 프록시 모듈을 현재 PowerShell 세션으로 가져옵니다. 이렇게 하면 PowerShell에서 모듈이 Windows PowerShell 호환성 기능을 사용 하 여 로드 되었는지 검색할 수 있습니다.

세션을 만든 후에는 deserialize 된 개체에서 제대로 작동 하지 않는 작업에 사용할 수 있습니다. 전체 파이프라인은 Windows PowerShell에서 실행 되며 최종 결과만 반환 됩니다. 다음은 그 예입니다. 

```powershell
$s = Get-PSSession -Name WinPSCompatSession
Invoke-Command -Session $s -ScriptBlock {
  "Running in Windows PowerShell version $($PSVersionTable.PSVersion)"
}
```

호환성 기능은 다음 두 가지 방법으로 호출할 수 있습니다.

- 명시적으로 **UseWindowsPowerShell** 매개 변수를 사용 하 여 모듈을 가져옵니다.

   ```powershell
   Import-Module -Name ScheduledTasks -UseWindowsPowerShell
   ```

- 명령 검색을 통해 모듈 이름, 경로 또는 자동 로드로 Windows PowerShell 모듈을 가져와 암시적으로.

   ```powershell
   Import-Module -Name ServerManager
   Get-AppLockerPolicy -Local
   ```

   아직 로드 되지 않은 경우를 실행할 때 AppLocker 모듈이 자동으로 로드 됩니다  `Get-AppLockerPolicy` .

Windows PowerShell 호환성은 `WindowsPowerShellCompatibilityModuleDenyList` powershell 구성 파일의 설정에 나열 된 모듈을 로드 하는 것을 차단 합니다.

이 설정의 기본값은 다음과 같습니다.

```json
"WindowsPowerShellCompatibilityModuleDenyList":  [
   "PSScheduledJob","BestPractices","UpdateServices"
]
```

### <a name="managing-implicit-module-loading"></a>암시적 모듈 로드 관리

Windows PowerShell 호환성 기능의 암시적 가져오기 동작을 사용 하지 않도록 설정 하려면 `DisableImplicitWinCompat` powershell 구성 파일의 설정을 사용 합니다. 이 설정은 파일에 추가할 수 있습니다 `powershell.config.json` . 자세한 내용은 [about_powershell_config](about_powershell_config.md)를 참조 하세요.

이 예제에서는 Windows PowerShell 호환성의 암시적 모듈 로드 기능을 사용 하지 않도록 설정 하는 구성 파일을 만드는 방법을 보여 줍니다.

```powershell
$ConfigPath = "$PSHOME\DisableWinCompat.powershell.config.json"
$ConfigJSON = ConvertTo-Json -InputObject @{
  "DisableImplicitWinCompat" = $true
  "Microsoft.PowerShell:ExecutionPolicy" = "RemoteSigned"
}
$ConfigJSON | Out-File -Force $ConfigPath
pwsh -settingsFile $ConfigPath
```

모듈 호환성에 대 한 최신 정보는 [PowerShell 7 모듈 호환성](https://aka.ms/PSModuleCompat) 목록을 참조 하세요.

### <a name="managing-cmdlet-clobbering"></a>Cmdlet clobbering 관리

Windows PowerShell 호환성 기능은 암시적 원격을 사용 하 여 호환성 모드에서 모듈을 로드 합니다. 그러면 모듈에서 내보낸 명령이 현재 PowerShell 7 세션에서 이름이 같은 명령 보다 우선적으로 적용 됩니다. PowerShell 7.0.0 릴리스에는 PowerShell과 함께 제공 되는 핵심 모듈이 포함 되어 있습니다.

PowerShell 7.1에서는 다음 핵심 PowerShell 모듈을 레지스터가 하지 않도록 동작이 변경 되었습니다.

- ConsoleHost
- Microsoft.PowerShell.Diagnostics
- Microsoft.PowerShell.Host
- Microsoft.PowerShell.Management
- Microsoft.PowerShell.Security
- Microsoft.PowerShell.Utility
- Microsoft.WSMan.Management

PowerShell 7.1에는 호환성 모드로 레지스터가 되지 않아야 하는 추가 모듈을 나열 하는 기능도 추가 되었습니다.

`WindowsPowerShellCompatibilityNoClobberModuleList`PowerShell 구성 파일에 설정을 추가할 수 있습니다. 이 설정의 값은 쉼표로 구분 된 모듈 이름 목록입니다. 이 설정의 기본값은 다음과 같습니다.

```json
"WindowsPowerShellCompatibilityNoClobberModuleList": [ ]
```

## <a name="limitations"></a>제한 사항

Windows PowerShell 호환성 기능:

1. Windows 컴퓨터 에서만 로컬로 작동
1. Windows PowerShell 5.1이 필요 합니다.
1. 라이브 개체가 아닌 serialize 된 cmdlet 매개 변수 및 반환 값에 대해 작동 합니다.
1. Windows PowerShell 원격 세션으로 가져온 모든 모듈은 동일한 runspace를 공유 합니다.

## <a name="keywords"></a>키워드

about_Windows_PowerShell_Compatibility

## <a name="see-also"></a>참고 항목

[about_Modules](about_Modules.md)

[모듈 가져오기](xref:Microsoft.PowerShell.Core.Import-Module)

