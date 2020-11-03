---
description: 환경
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 환경 공급자
ms.openlocfilehash: 44f2f123da3066bc08e2b1ef0ec25c24b18799bc
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222097"
---
# <a name="environment-provider"></a>환경 공급자

## <a name="provider-name"></a>공급자 이름
Environment

## <a name="drives"></a>드라이브

`Env:`

## <a name="capabilities"></a>기능

**ShouldProcess**

## <a name="short-description"></a>간단한 설명

Windows 환경 변수에 액세스할 수 있도록 합니다.

## <a name="detailed-description"></a>자세한 설명

PowerShell **환경** 공급자를 통해 powershell에서 환경 변수 및 값을 가져오고 추가, 변경 및 삭제할 수 있습니다.

**환경** 변수는 프로그램이 실행 되는 환경을 설명 하는 동적으로 명명 된 변수입니다. Windows 및 PowerShell은 환경 변수를 사용 하 여 시스템 및 프로세스 실행에 영향을 주는 영구 정보를 저장 합니다. PowerShell 변수와 달리 환경 변수에는 범위 제약 조건이 적용 되지 않습니다.

**환경** 드라이브는 현재 사용자의 세션과 관련 된 환경 변수를 포함 하는 플랫 네임 스페이스입니다. 환경 변수에는 자식 항목이 없습니다.

**환경** 공급자는이 문서에서 설명 하는 다음과 같은 cmdlet을 지원 합니다.

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a>이 공급자가 노출 하는 형식

각 환경 변수는 [DictionaryEntry](/dotnet/api/system.collections.dictionaryentry) 클래스의 인스턴스입니다. 변수 이름은 사전 키입니다. 환경 변수 값은 사전 값입니다.

## <a name="navigating-the-environment-drive"></a>환경 드라이브 탐색

**환경** 공급자는 드라이브에 해당 데이터 저장소를 노출 합니다 `Env:` . 환경 변수를 사용 하려면 위치를 `Env:` drive ()로 변경 `Set-Location Env:` 하거나 다른 PowerShell 드라이브에서 작업 합니다. 다른 위치에서 환경 변수를 참조 하려면 `Env:` 경로에 드라이브 이름을 사용 합니다.

```powershell
Set-Location Env:
```

파일 시스템 드라이브로 돌아가려면 드라이브 이름을 입력합니다. 예를 들어 다음과 같이 입력합니다.

```powershell
Set-Location C:
```

다른 PowerShell 드라이브에서 **환경** 공급자를 사용할 수도 있습니다. 다른 위치에서 환경 변수를 참조 하려면 경로에 드라이브 이름을 사용 `Env:` 합니다.

**환경** 공급자는 또한 변수 접두사를 사용 하 여 환경 변수를 노출 `$env:` 합니다.  다음 명령은 **ProgramFiles** 환경 변수의 내용을 봅니다. `$env:`변수 접두사는 모든 PowerShell 드라이브에서 사용할 수 있습니다.

```
PS C:\> $env:ProgramFiles
C:\Program Files
```

변수 접두사를 사용 하 여 환경 변수 값을 변경할 수도 있습니다 `$env:` .  변경 내용은 활성 상태인 동안에만 현재 PowerShell 세션에 적용 됩니다.

> [!NOTE]
> PowerShell은 별칭을 사용 하 여 공급자 경로 작업을 수행할 수 있는 친숙 한 방법을 제공 합니다. `dir`및 등의 명령은 `ls` 이제 [Get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)에 대 한 별칭입니다 `cd` .는 [집합 위치](xref:Microsoft.PowerShell.Management.Set-Location)에 대 한 별칭입니다. 및 `pwd` 은 [(는) 위치](xref:Microsoft.PowerShell.Management.Get-Location)에 대 한 별칭입니다.

## <a name="getting-environment-variables"></a>환경 변수 가져오기

이 명령은 현재 세션의 모든 환경 변수를 나열 합니다.

```powershell
Get-Item -Path Env:
```

모든 PowerShell 드라이브에서이 명령을 사용할 수 있습니다.

환경 공급자에는 컨테이너가 없으므로에서 사용 하는 경우 위의 명령이 동일한 효과를 가집니다 `Get-ChildItem` .

```powershell
Get-ChildItem -Path Env:
```

### <a name="get-a-selected-environment-variable"></a>선택한 환경 변수 가져오기

이 명령은 `WINDIR` 환경 변수를 가져옵니다.

```powershell
Get-ChildItem -Path Env:windir
```

또한 변수 접두사 형식을 사용할 수 있습니다.

```powershell
$env:windir
```

## <a name="create-an-environment-variable"></a>환경 변수 만들기

이 명령은 `USERMODE` "비 관리자" 값을 사용 하 여 환경 변수를 만듭니다. `-Path`매개 변수 값은 드라이브에 새 항목을 만듭니다 `Env:` . 새 환경 변수는 활성 상태인 동안에만 현재 PowerShell 세션에서 사용할 수 있습니다.

```powershell
PS C:\> New-Item -Path Env: -Name USERMODE -Value Non-Admin
```

## <a name="changing-an-environment-variable"></a>환경 변수 변경

### <a name="rename-an-environment-variable"></a>환경 변수 이름 바꾸기

이 명령은 cmdlet을 사용 하 여 `Rename-Item` `USERMODE` 사용자가 만든 환경 변수의 이름을 변경 `USERROLE` 합니다. 시스템에서 사용하는 환경 변수의 이름을 변경하지 마세요. 이러한 변경 내용은 현재 세션에만 영향을 주지만 이로 인해 시스템 또는 프로그램이 제대로 작동하지 않을 수도 있습니다.

```powershell
Rename-Item -Path Env:USERMODE -NewName USERROLE
```

### <a name="change-an-environment-variable"></a>환경 변수 변경

이 명령은 cmdlet을 사용 하 여 `Set-Item` 환경 변수 값을 `USERROLE` "Administrator"로 변경 합니다.

```powershell
Set-Item -Path Env:USERROLE -Value Administrator
```

## <a name="copy-an-environment-variable"></a>환경 변수 복사

이 명령은 환경 변수 값 `USERROLE` 을 `USERROLE2` 환경 변수에 복사 합니다.

```powershell
Copy-Item -Path Env:USERROLE -Destination Env:USERROLE2
```

## <a name="remove-an-environment-variable"></a>환경 변수 제거

이 명령은 `USERROLE2` 현재 세션에서 환경 변수를 삭제 합니다.

```powershell
Remove-Item -Path Env:USERROLE2
```

## <a name="remove-an-environment-variable-with-clear-item"></a>Clear-Item를 사용 하 여 환경 변수 제거

이 명령은 `USERROLE` 해당 값의 선택을 취소 하 여 환경 변수를 삭제 합니다.

```powershell
Clear-Item -Path Env:USERROLE
```

## <a name="using-the-pipeline"></a>파이프라인 사용

공급자 cmdlet은 파이프라인 입력을 허용 합니다. 파이프라인을 사용 하 여 cmdlet 간에 공급자 데이터를 전송 하 여 작업을 간소화할 수 있습니다.
공급자 cmdlet에서 파이프라인을 사용 하는 방법에 대 한 자세한 내용은이 문서 전체에서 제공 되는 cmdlet 참조를 참조 하세요.

## <a name="getting-help"></a>도움말 보기

Windows PowerShell 3.0부터는 이러한 cmdlet이 파일 시스템 드라이브에서 동작하는 방식을 설명하는 공급자 cmdlet에 대한 사용자 지정된 도움말 항목을 볼 수 있습니다.

파일 시스템 드라이브에 맞게 사용자 지정 된 도움말 항목을 보려면 파일 시스템 드라이브에서 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 명령을 실행 하거나 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 의 매개 변수를 사용 하 여 파일 시스템 드라이브를 지정 합니다.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path env:
```

## <a name="see-also"></a>참고 항목

[about_Providers](../About/about_Providers.md)

