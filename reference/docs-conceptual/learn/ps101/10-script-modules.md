---
title: 스크립트 모듈
description: 스크립트 모듈은 여러 스크립트와 함수를 재사용 가능한 도구로 패키징할 수 있는 간편한 방법입니다.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 661ba725764e1f31df628f6c5f2d58d760656e37
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438284"
---
# <a name="chapter-10---script-modules"></a>10장 - 스크립트 모듈

PowerShell의 원라이너와 스크립트를 재사용 가능한 도구로 전환하는 기능은 자주 사용하면 대단히 강력한 도구가 됩니다. 함수를 스크립트 모듈에 패키지하면 더 전문적인 느낌을 주며 공유도 간단합니다.

## <a name="dot-sourcing-functions"></a>도트 소싱 함수

이전 장에서는 도트 소싱 함수는 다루지 않았습니다. 스크립트에 있는 함수가 모듈의 일부가 아니라면, 함수가 저장된 `.PS1` 파일을 도트 소싱해야만 함수를 메모리에 로드할 수 있습니다.

다음 함수는 `Get-MrPSVersion.ps1`로 저장되었습니다.

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}
```

스크립트를 실행하면 아무 일도 발생하지 않습니다.

```powershell
.\Get-MrPSVersion.ps1
```

함수를 호출하면 오류 메시지가 생성됩니다.

```powershell
Get-MrPSVersion
```

```Output
Get-MrPSVersion : The term 'Get-MrPSVersion' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [], CommandNotFou
   ndException
    + FullyQualifiedErrorId : CommandNotFoundException

```

함수가 **Function** PSDrive에 있는지 확인하면 함수가 메모리에 로드되었는지를 확인할 수 있습니다.

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
Get-ChildItem : Cannot find path 'Get-MrPSVersion' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path Function:\Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [Get-ChildItem],
   ItemNotFoundException
    + FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
```

함수를 포함하는 스크립트를 호출하면 함수가 스크립트 범위에 로드된다는 문제가 발생합니다. 스크립트가 완료되면 이 범위가 제거되고 함수도 함께 제거됩니다.

함수는 전역 범위로 로드해야 합니다. 이렇게 하려면 함수를 포함하는 스크립트를 도트 소싱해야 합니다. 상대 경로를 사용해도 됩니다.

```powershell
. .\Get-MrPSVersion.ps1
```

정규화된 경로도 사용할 수 있습니다.

```powershell
. C:\Demo\Get-MrPSVersion.ps1
```

경로 일부가 변수에 저장되었다면 경로의 나머지 부분과 함께 사용할 수 있습니다.
문자열 연결을 사용하여 변수를 경로의 나머지 부분과 결합할 필요는 없습니다.

```powershell
$Path = 'C:\'
. $Path\Get-MrPSVersion.ps1
```

이제 **Function** PSDrive를 확인하면 `Get-MrPSVersion` 함수가 존재합니다.

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-MrPSVersion
```

## <a name="script-modules"></a>스크립트 모듈

PowerShell에서의 스크립트 모듈은 함수를 하나 이상 포함하며 `.PS1` 파일이 아닌 `.PSM1` 파일로 저장되는 파일입니다.

스크립트 모듈을 만들려면 어떻게 해야 할까요? `New-Module` 같은 이름이 지정된 명령을 사용해야 한다고 생각하실지도 모릅니다. 이러한 생각이 틀릴 수도 있습니다. PowerShell에는 `New-Module`이라는 명령이 있지만 이 명령은 스크립트 모듈이 아닌 동적 모듈을 만듭니다. 필요한 명령을 찾았다고 생각하더라도 항상 명령 관련 도움말을 읽어야 합니다.

```powershell
help New-Module
```

```Output
NAME
    New-Module

SYNOPSIS
    Creates a new dynamic module that exists only in memory.

SYNTAX
    New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-ArgumentList <Object[]>]
    [-AsCustomObject] [-Cmdlet <String[]>] [-Function <String[]>] [-ReturnResult]
    [<CommonParameters>]

DESCRIPTION
    The New-Module cmdlet creates a dynamic module from a script block. The members of
    the dynamic module, such as functions and variables, are immediately available in
    the session and remain available until you close the session.

    Like static modules, by default, the cmdlets and functions in a dynamic module are
    exported and the variables and aliases are not. However, you can use the
    Export-ModuleMember cmdlet and the parameters of New-Module to override the defaults.

    You can also use the AsCustomObject parameter of New-Module to return the dynamic
    module as a custom object. The members of the modules, such as functions, are
    implemented as script methods of the custom object instead of being imported into
    the session.

    Dynamic modules exist only in memory, not on disk. Like all modules, the members of
    dynamic modules run in a private module scope that is a child of the global scope.
    Get-Module cannot get a dynamic module, but Get-Command can get the exported members.

    To make a dynamic module available to Get-Module , pipe a New-Module command to
    Import-Module, or pipe the module object that New-Module returns to Import-Module .
    This action adds the dynamic module to the Get-Module list, but it does not save the
    module to disk or make it persistent.

RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821495
    Export-ModuleMember
    Get-Module
    Import-Module
    Remove-Module

REMARKS
    To see the examples, type: "get-help New-Module -examples".
    For more information, type: "get-help New-Module -detailed".
    For technical information, type: "get-help New-Module -full".
    For online help, type: "get-help New-Module -online"
```

이전 장에서 함수가 승인된 동사를 사용하지 않으면 모듈을 가져올 때 경고 메시지가 생성된다고 설명했습니다. 다음 코드는 `New-Module` cmdlet을 사용하여 메모리에 동적 모듈을 만듭니다. 이 모듈에서는 승인되지 않은 동사 경고를 확인할 수 있습니다.

```powershell
New-Module -Name MyModule -ScriptBlock {

    function Return-MrOsVersion {
        Get-CimInstance -ClassName Win32_OperatingSystem |
        Select-Object -Property @{label='OperatingSystem';expression={$_.Caption}}
    }

    Export-ModuleMember -Function Return-MrOsVersion

} | Import-Module
```

```Output
WARNING: The names of some imported commands from the module 'MyModule' include
unapproved verbs that might make them less discoverable. To find the commands with
unapproved verbs, run the Import-Module command again with the Verbose parameter. For a
list of approved verbs, type Get-Verb.
```

다시 말하지만, 앞의 예제에서 `New-Module` cmdlet을 사용했지만 이것은 PowerShell에서 스크립트 모듈을 만드는 명령은 아닙니다.

`MyScriptModule.psm1`이라는 파일에 다음 두 함수를 저장하세요.

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}
```

함수 중 하나를 호출해 보세요.

```powershell
Get-MrComputerName
```

```Output
Get-MrComputerName : The term 'Get-MrComputerName' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrComputerName
    + CategoryInfo          : ObjectNotFound: (Get-MrComputerName:String) [], CommandNot
   FoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

함수를 찾을 수 없다는 오류 메시지가 생성됩니다. 예전처럼 **Function** PSDrive를 확인하면 함수가 여기에도 없다는 사실을 알게 됩니다.

`Import-Module` cmdlet을 사용하면 파일을 수동으로 가져올 수 있습니다.

```powershell
Import-Module C:\MyScriptModule.psm1
```

모듈 자동 로드 기능은 PowerShell 버전 3에서 도입되었습니다. 모듈 자동 로드를 사용하려면 스크립트 모듈을 `.PSM1` 파일과 기본 이름이 같은 폴더에, 그리고 `$env:PSModulePath`에 지정된 위치에 저장해야 합니다.

```powershell
$env:PSModulePath
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules;C:\Program Files\WindowsPowerShell\
Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules;C:\Program Files (x86)\Microsof
t SQL Server\130\Tools\PowerShell\Modules\
```

결과는 읽기 쉽지 않습니다. 경로는 세미콜론으로 구분되므로 결과를 분할하여 각 경로를 개별 줄에서 반환할 수 있습니다. 이렇게 하면 쿼리 가독성이 높아집니다.

```powershell
$env:PSModulePath -split ';'
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules
C:\Program Files\WindowsPowerShell\Modules
C:\Windows\system32\WindowsPowerShell\v1.0\Modules
C:\Program Files (x86)\Microsoft SQL Server\130\Tools\PowerShell\Modules\
```

목록의 처음 세 경로는 기본값입니다. SQL Server Management Studio가 설치되었을 때 마지막 경로가 추가되었습니다. 모듈 자동 로드가 작동하려면 `MyScriptModule.psm1` 파일이 세 경로 중 하나 안에 있는 `MyScriptModule`이라는 폴더에 있어야 합니다.

아직은 시도하진 마세요. 필자의 현재 사용자 경로는 목록의 첫 번째 사용자 경로가 아닙니다. 필자는 PowerShell을 실행할 때 사용하는 것과는 다른 사용자로 Windows에 로그인하므로 이 경로는 거의 사용하지 않습니다. 따라서 일반 문서 폴더에 위치하지 않습니다.

두 번째 경로는 **AllUsers** 경로입니다. 전체 모듈을 저장하는 곳입니다.

세 번째 경로는 `C:\Windows\System32`에 있습니다. 운영 체제 폴더 내에 위치하기 때문에 오직 Microsoft만 이 위치에 모듈을 저장할 수 있습니다.

`.PSM1` 파일이 올바른 경로에 위치하면 모듈은 자체 명령 중 하나가 호출될 때 자동으로 로드됩니다.

## <a name="module-manifests"></a>모듈 매니페스트

모든 모듈에는 모듈 매니페스트가 있어야 합니다. 모듈 매니페스트에는 모듈 관련 메타데이터가 포함됩니다.
모듈 매니페스트 파일의 파일 확장명은 `.PSD1`입니다. 파일 확장명이 `.PSD1`이지만 모듈 매니페스트가 아닌 파일도 있습니다. 모듈 매니페스트 파일은 DSC 구성의 환경 부분을 저장하는 등의 작업에도 사용할 수 있습니다. `New-ModuleManifest`는 모듈 매니페스트를 만드는 데 사용합니다. **Path**는 유일한 필수 값입니다. 그러나 **RootModule**이 지정되지 않으면 모듈은 작동하지 않습니다. 모듈을 PowerShellGet을 이용해 NuGet 리포지토리에 업로드하기로 했다면 **Author**와 **Description**을 지정하는 것이 좋습니다. 해당 시나리오에 필요한 값이기 때문입니다.

매니페스트가 없는 모듈의 버전은 0.0입니다. 모듈에 매니페스트가 없다는 확실한 증거입니다.

```powershell
Get-Module -Name MyScriptModule
```

```Output
ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Script     0.0        myscriptmodule                      {Get-MrComputerName, Get-MrP...
```

모든 권장 정보를 사용하여 모듈 매니페스트를 만들 수 있습니다.

```powershell
New-ModuleManifest -Path $env:ProgramFiles\WindowsPowerShell\Modules\MyScriptModule\MyScriptModule.psd1 -RootModule MyScriptModule -Author 'Mike F Robbins' -Description 'MyScriptModule' -CompanyName 'mikefrobbins.com'
```

모듈 매니페스트를 처음 만들 때 이 정보 중 일부가 누락되었다면 `Update-ModuleManifest`를 이용해 나중에 추가하거나 업데이트할 수 있습니다. `New-ModuleManifest`를 사용하여 만든 매니페스트를 다시 만들면 안 됩니다. GUID가 변경되기 때문입니다.

## <a name="defining-public-and-private-functions"></a>퍼블릭 및 프라이빗 함수 정의

비공개이며 모듈 내의 다른 함수에서만 액세스할 수 있는 도우미 함수를 이용할 수 있습니다. 모듈의 사용자는 도우미 함수에 액세스할 수 없습니다. 이 작업은 두 가지 방법으로 수행합니다.

모범 사례를 따르지 않으며 `.PSM1` 파일만 있다면 `Export-ModuleMember` cmdlet을 사용하는 방법밖에 없습니다.

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}

Export-ModuleMember -Function Get-MrPSVersion
```

이전 예제에서는 모듈의 사용자만 `Get-MrPSVersion` 함수를 사용할 수 있지만 `Get-MrComputerName` 함수는 모듈 내의 다른 함수에서 사용할 수 있습니다.

```powershell
Get-Command -Module MyScriptModule

CommandType     Name                        Version    Source
-----------     ----                        -------    ------
Function        Get-MrPSVersion             1.0        MyScript...
```

(필수 작업인) 모듈 매니페스트를 모듈에 추가했다면, 모듈 매니페스트의 **FunctionsToExport** 섹션에서 내보낼 개별 함수를 지정하는 방법을 권장합니다.

```powershell
FunctionsToExport = 'Get-MrPSVersion'
```

`.PSM1` 파일의 `Export-ModuleMember`와 모듈 매니페이스의 **FunctionsToExport** 섹션을 모두 사용할 필요는 없습니다. 하나만 사용하면 됩니다.

## <a name="summary"></a>요약

이 장에서는 함수를 PowerShell의 스크립트 모듈으로 전환하는 방법을 알아보았습니다. 그리고 스크립트 모듈의 모듈 매니페스트를 만드는 작업을 포함한 스크립트 모듈 생성 모범 사례도 확인했습니다.

## <a name="review"></a>검토

1. 스크립트 모듈을 만들려면 어떻게 해야 하나요?
1. 함수에서 승인된 동사를 사용하는 것이 왜 중요한가요?
1. PowerShell에서 스크립트 모듈을 만들려면 어떻게 해야 하나요?
1. 모듈에서 특정 함수만 내보내는 두 가지 방법은 무엇인가요?
1. 명령이 호출될 때 모듈을 자동으로 로드하려면 어떻게 해야 하나요?

## <a name="recommended-reading"></a>권장 참조 항목

- [PowerShell 스크립트 모듈 및 모듈 매니페스트를 만드는 방법][]
- [about_Modules][]
- [New-ModuleManifest][]
- [Export-ModuleMember][]

<!-- link references -->
[PowerShell 스크립트 모듈 및 모듈 매니페스트를 만드는 방법]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Export-ModuleMember]: /powershell/module/microsoft.powershell.core/export-modulemember
