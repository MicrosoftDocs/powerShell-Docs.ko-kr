---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Module
ms.openlocfilehash: 2954bbec68b837a73e5365ab6a1e8ecb501d4898
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599355"
---
# Remove-Module

## 개요
현재 세션에서 모듈을 제거합니다.

## SYNTAX

### name

```
Remove-Module [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FullyQualifiedName

```
Remove-Module [-FullyQualifiedName] <ModuleSpecification[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ModuleInfo

```
Remove-Module [-ModuleInfo] <PSModuleInfo[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

**Remove-Module** cmdlet은 cmdlet 및 함수와 같은 모듈의 멤버를 현재 세션에서 제거합니다.

모듈에 어셈블리(.dll)가 포함되어 있을 경우 어셈블리를 통해 구현된 모든 멤버가 제거되지만 어셈블리는 언로드되지 않습니다.

이 cmdlet은 모듈을 제거하거나 컴퓨터에서 삭제하지 않고
현재 PowerShell 세션에만 영향을 줍니다.

## 예제

### 예제 1: 모듈 제거

```powershell
Remove-Module -Name "BitsTransfer"
```

이 명령은 현재 세션에서 BitsTransfer 모듈을 제거합니다.

### 예제 2: 모든 모듈 제거

```powershell
Get-Module | Remove-Module
```

이 명령은 현재 세션에서 모든 모듈을 제거합니다.

### 예제 3: 파이프라인을 사용 하 여 모듈 제거

```powershell
"FileTransfer", "PSDiagnostics" | Remove-Module -Verbose
```

```Output
VERBOSE: Performing operation "Remove-Module" on Target "filetransfer (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\filetransfer\filetransfer.psd1')".
VERBOSE: Performing operation "Remove-Module" on Target "Microsoft.BackgroundIntelligentTransfer.Management (Path: 'C:\Windows\assembly\GAC_MSIL\Microsoft.BackgroundIntelligentTransfer.Management\1.0.0.0__31bf3856ad364e35\Microsoft.BackgroundIntelligentTransfe
r.Management.dll')".
VERBOSE: Performing operation "Remove-Module" on Target "psdiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\psdiagnostics.psd1')".
VERBOSE: Removing imported function 'Start-Trace'.
VERBOSE: Removing imported function 'Stop-Trace'.
VERBOSE: Removing imported function 'Enable-WSManTrace'.
VERBOSE: Removing imported function 'Disable-WSManTrace'.
VERBOSE: Removing imported function 'Enable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Disable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Set-LogProperties'.
VERBOSE: Removing imported function 'Get-LogProperties'.
VERBOSE: Removing imported function 'Enable-PSTrace'.
VERBOSE: Removing imported function 'Disable-PSTrace'.
VERBOSE: Performing operation "Remove-Module" on Target "PSDiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\PSDiagnostics.psm1')".
```

이 명령은 현재 세션에서 BitsTransfer 및 PSDiagnostics 모듈을 제거합니다.

파이프라인 연산자(|)를 사용하여 모듈 이름을 **Remove-Module** 로 보냅니다.
또한 *Verbose* 일반 매개 변수를 사용하여 제거된 멤버에 대한 자세한 정보를 가져옵니다.

*자세한 정보* 메시지는 제거 된 항목을 표시 합니다.
BitsTransfer 모듈은 해당 cmdlet을 구현하는 어셈블리와 자체 어셈블리가 있는 중첩 모듈을 포함하기 때문에 메시지가 서로 다릅니다.
PSDiagnostics 모듈에는 함수를 내보내는 모듈 스크립트 파일(.psm1)이 포함되어 있습니다.

### 예제 4: ModuleInfo를 사용 하 여 모듈 제거

```powershell
$a = Get-Module BitsTransfer
Remove-Module -ModuleInfo $a
```

이 명령은 *Moduleinfo* 매개 변수를 사용 하 여 BitsTransfer 모듈을 제거 합니다.

## PARAMETERS

### -Force

이 cmdlet이 읽기 전용 모듈을 제거 함을 나타냅니다.
기본적으로 **Remove-Module** 은 읽기-쓰기 모듈만 제거합니다.

**ReadOnly** 및 **ReadWrite** 값은 모듈의 **AccessMode** 속성에 저장됩니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedName

제거할 모듈의 정규화 된 이름을 지정 합니다.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ModuleInfo

제거할 모듈 개체를 지정합니다.
모듈 개체 (**Psmoduleinfo**)를 포함 하는 변수를 입력 하거나 모듈 개체를 가져오는 명령 (예: Get-Module 명령)을 입력 합니다.
모듈 개체를 **Remove-Module** 로 파이프할 수도 있습니다.

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

제거할 모듈의 이름을 지정합니다.
와일드카드 문자를 사용할 수 있습니다.
이름 문자열을 **Remove-Module** 로 파이프할 수도 있습니다.

```yaml
Type: System.String[]
Parameter Sets: name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.string, System.web. a p a.

모듈 이름 및 모듈 개체를 **제거** 로 파이프 할 수 있습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

모듈을 제거 하는 경우 모듈에 실행 되는 이벤트가 있습니다.
이 이벤트를 사용 하면 모듈이 제거 될 때 반응할 수 있으며 리소스 해제와 같은 일부 정리 작업을 수행할 수 있습니다. 예제:

$OnRemoveScript = {

  \# 정리 수행

  $cachedSessions | Remove-PSSession

}

$ExecutionContext SessionState + = $OnRemoveScript

전체 일관성을 위해 PowerShell 프로세스를 닫을 때에도 유용할 수 있습니다.

Register-EngineEvent-SourceIdentifier ([PsEngineEvent]:: 종료)-Action $OnRemoveScript

## 관련 링크

[Get-Module](Get-Module.md)

[모듈 가져오기](Import-Module.md)

