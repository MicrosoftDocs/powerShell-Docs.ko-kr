---
title: Functions
description: PowerShell 함수를 사용하면 스크립트에서 다시 사용할 수 있는 도구를 만들 수 있습니다.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: ca48f3020fa306f8a24328bd18648d5954c48a94
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438204"
---
# <a name="chapter-9---functions"></a>9장 - 함수

PowerShell 원라이너 또는 스크립트를 작성 중이고 다른 시나리오를 위해 수정하는 경우가 자주 발생하면 다시 사용할 수 있는 함수로 전환하는 것이 좋습니다.

보다 도구 지향적이기 때문에 가능한 한 함수를 작성하는 것이 좋습니다. 스크립트 모듈에 함수를 추가하고, 해당 모듈을 `$env:PSModulePath`에 배치하고, 물리적으로 저장 위치를 찾을 필요 없이 함수를 호출할 수 있습니다. PowerShellGet 모듈을 사용하면 NuGet 리포지토리에서 이러한 모듈을 쉽게 공유할 수 있습니다. PowerShellGet은 PowerShell 버전 5.0 이상에서 제공됩니다. PowerShell 버전 3.0 이상에서는 별도의 다운로드로 제공됩니다.

문제를 너무 복잡하게 만들지 마세요. 작업을 수행하기 위한 가장 간단한 방법을 사용하는 것이 좋습니다. 다시 사용하는 모든 코드에서는 별칭 및 위치 매개 변수를 사용하지 마세요. 가독성을 위해 코드를 서식 지정하는 것이 좋습니다. 값을 하드 코딩하지 말고 매개 변수 및 변수를 사용합니다. 불필요한 코드는 아무런 피해가 없더라도 작성하지 마세요. 불필요한 복잡성이 추가됩니다. PowerShell 코드를 작성할 때는 세부 사항에 대한 주의가 필요합니다.

## <a name="naming"></a>이름 지정

PowerShell에서 함수 이름을 지정할 때 승인된 동사와 단수 명사를 포함하는 [파스칼식 대/소문자][] 이름을 사용합니다. 또한 명사에 접두사를 사용하는 것이 좋습니다. 예: `<ApprovedVerb>-<Prefix><SingularNoun>`

PowerShell에는 `Get-Verb`를 실행하여 얻을 수 있는 승인된 동사의 목록이 있습니다.

```powershell
Get-Verb | Sort-Object -Property Verb
```

```Output
Verb        Group
----        -----
Add         Common
Approve     Lifecycle
Assert      Lifecycle
Backup      Data
Block       Security
Checkpoint  Data
Clear       Common
Close       Common
Compare     Data
Complete    Lifecycle
Compress    Data
Confirm     Lifecycle
Connect     Communications
Convert     Data
ConvertFrom Data
ConvertTo   Data
Copy        Common
Debug       Diagnostic
Deny        Lifecycle
Disable     Lifecycle
Disconnect  Communications
Dismount    Data
Edit        Data
Enable      Lifecycle
Enter       Common
Exit        Common
Expand      Data
Export      Data
Find        Common
Format      Common
Get         Common
Grant       Security
Group       Data
Hide        Common
Import      Data
Initialize  Data
Install     Lifecycle
Invoke      Lifecycle
Join        Common
Limit       Data
Lock        Common
Measure     Diagnostic
Merge       Data
Mount       Data
Move        Common
New         Common
Open        Common
Optimize    Common
Out         Data
Ping        Diagnostic
Pop         Common
Protect     Security
Publish     Data
Push        Common
Read        Communications
Receive     Communications
Redo        Common
Register    Lifecycle
Remove      Common
Rename      Common
Repair      Diagnostic
Request     Lifecycle
Reset       Common
Resize      Common
Resolve     Diagnostic
Restart     Lifecycle
Restore     Data
Resume      Lifecycle
Revoke      Security
Save        Data
Search      Common
Select      Common
Send        Communications
Set         Common
Show        Common
Skip        Common
Split       Common
Start       Lifecycle
Step        Common
Stop        Lifecycle
Submit      Lifecycle
Suspend     Lifecycle
Switch      Common
Sync        Data
Test        Diagnostic
Trace       Diagnostic
Unblock     Security
Undo        Common
Uninstall   Lifecycle
Unlock      Common
Unprotect   Security
Unpublish   Data
Unregister  Lifecycle
Update      Data
Use         Other
Wait        Lifecycle
Watch       Common
Write       Communications
```

이전 예제에서는 **Verb** 열을 기준으로 결과를 정렬했습니다. **Group** 열은 이러한 동사를 사용하는 방법을 설명합니다. 모듈에 함수를 추가할 때 PowerShell에서 승인된 동사를 선택하는 것이 중요합니다. 승인되지 않은 동사를 선택하면 로드 시 모듈에서 경고 메시지를 생성합니다. 이러한 경고 메시지는 비전문가가 만든 함수처럼 보이게 만듭니다. 또한 승인되지 않은 동사는 함수 검색 가능성을 제한합니다.

## <a name="a-simple-function"></a>간단한 함수

PowerShell의 함수는 함수 키워드와 함수 이름, 여는 중괄호 및 닫는 중괄호를 사용하여 선언됩니다. 함수가 실행하는 코드는 이 중괄호 안에 포함됩니다.

```powershell
function Get-Version {
    $PSVersionTable.PSVersion
}
```

표시된 함수는 PowerShell의 버전을 반환하는 간단한 예제입니다.

```powershell
Get-Version
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

`Get-Version`과 같은 이름의 함수와 PowerShell 기본 명령 또는 다른 사용자가 작성할 수 있는 명령은 이름 충돌이 생길 가능성이 높습니다. 함수의 명사 부분에 접두사를 지정하도록 권장하는 이유는 이름 충돌을 방지하는 데 도움이 되기 때문입니다. 다음 예제에서는 접두사 "PS"를 사용합니다.

```powershell
function Get-PSVersion {
    $PSVersionTable.PSVersion
}
```

이름을 제외하면 이 함수는 이전 함수와 동일합니다.

```powershell
Get-PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

PS와 같은 명사를 접두사로 사용하는 경우에도 여전히 이름 충돌이 발생할 수 있습니다. 필자는 일반적으로 함수 명사에 이니셜을 접두사로 추가합니다. 표준을 개발하고 일관되게 적용하세요.

```powershell
function Get-MrPSVersion {
    $PSVersionTable.PSVersion
}
```

다음 함수는 다른 PowerShell 명령과의 이름 충돌을 방지하기 위해 보다 알기 쉬운 이름을 사용한다는 점을 제외하면 이전의 두 함수와 다르지 않습니다.

```powershell
Get-MrPSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

함수가 메모리에 로드되면 **Function** PSDrive에서 볼 수 있습니다.

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-Version
Function        Get-PSVersion
Function        Get-MrPSVersion
```

현재 세션에서 이러한 함수를 제거하려면 **Function** PSDrive에서 제거하거나 PowerShell을 닫았다가 다시 열어야 합니다.

```powershell
Get-ChildItem -Path Function:\Get-*Version | Remove-Item
```

함수가 실제로 제거되었는지 확인합니다.

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

함수가 모듈의 일부로 로드된 경우 모듈을 언로드하고 제거할 수 있습니다.

```powershell
Remove-Module -Name <ModuleName>
```

`Remove-Module` cmdlet은 현재 PowerShell 세션의 메모리에서 모듈을 제거하고 시스템 또는 디스크에서는 제거하지 않습니다.

## <a name="parameters"></a>매개 변수

값을 정적으로 할당하지 마세요. 매개 변수와 변수를 사용하는 것이 좋습니다. 매개 변수의 이름을 지정할 때는 가능한 한 매개 변수 이름에 기본 cmdlet과 동일한 이름을 사용합니다.

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

매개 변수 이름에 **Computer**, **ServerName** 또는 **Host**가 아니라 **ComputerName**을 사용한 이유가 무엇일까요? 기본 cmdlet과 같이 함수를 표준화하려고 했기 때문입니다.

시스템의 모든 명령을 쿼리하고 특정 매개 변수 이름이 있는 값을 반환하는 함수를 만들겠습니다.

```powershell
function Get-MrParameterCount {
    param (
        [string[]]$ParameterName
    )

    foreach ($Parameter in $ParameterName) {
        $Results = Get-Command -ParameterName $Parameter -ErrorAction SilentlyContinue

        [pscustomobject]@{
            ParameterName = $Parameter
            NumberOfCmdlets = $Results.Count
        }
    }
}
```

아래에 표시된 결과에서 볼 수 있듯이 **ComputerName** 매개 변수가 있는 명령이 39개 있습니다. **Computer**, **ServerName**, **Host** 또는 **Machine** 같은 매개 변수를 포함하는 cmdlet은 없습니다.

```powershell
Get-MrParameterCount -ParameterName ComputerName, Computer, ServerName, Host, Machine
```

```Output
ParameterName NumberOfCmdlets
------------- ---------------
ComputerName               39
Computer                    0
ServerName                  0
Host                        0
Machine                     0
```

또한 매개 변수 이름에 기본 cmdlet과 동일한 대/소문자를 사용하는 것이 좋습니다. `computername`이 아니라 `ComputerName`을 사용합니다. 이렇게 하면 함수는 기본 cmdlet과 비슷하게 표시됩니다. 이미 PowerShell에 익숙한 사람이라면 매우 편안하게 느낄 것입니다.

## <a name="advanced-functions"></a>고급 함수

PowerShell의 함수를 고급 함수로 설정하는 것은 매우 간단합니다. 함수와 고급 함수 간의 차이점 중 하나는 고급 함수는 함수에 자동으로 추가되는 여러 공통 매개 변수를 포함한다는 것입니다. 이러한 공통 매개 변수에는 **Verbose** 및 **Debug** 같은 매개 변수가 포함됩니다.

이전 섹션에서 사용된 `Test-MrParameter` 함수로 시작하겠습니다.

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

`Test-MrParameter` 함수에는 공통 매개 변수가 없다는 것을 알고 있어야 합니다. 몇 가지 방법으로 공통 매개 변수를 확인할 수 있습니다. 한 방법은 `Get-Command`를 사용하여 구문을 보는 것입니다.

```powershell
Get-Command -Name Test-MrParameter -Syntax
```

```Output
Test-MrParameter [[-ComputerName] <Object>]
```

다른 방법은 `Get-Command`를 사용하여 매개 변수로 드릴다운하는 것입니다.

```powershell
(Get-Command -Name Test-MrParameter).Parameters.Keys
```

```Output
ComputerName
```

함수를 고급 함수로 전환하려면 `CmdletBinding`을 추가합니다.

```powershell
function Test-MrCmdletBinding {

    [CmdletBinding()] #<<-- This turns a regular function into an advanced function
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

`CmdletBinding`을 추가하면 공통 매개 변수가 자동으로 추가됩니다. `CmdletBinding`에는 `param` 블록이 필요하지만 `param` 블록은 비워 둘 수 있습니다.

```powershell
Get-Command -Name Test-MrCmdletBinding -Syntax
```

```Output
Test-MrCmdletBinding [[-ComputerName] <Object>] [<CommonParameters>]
```

`Get-Command` 매개 변수로 드릴다운하면 공통 매개 변수 이름을 포함하여 실제 매개 변수 이름이 표시됩니다.

```powershell
(Get-Command -Name Test-MrCmdletBinding).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
```

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

`SupportsShouldProcess`는 **WhatIf** 및 **Confirm** 매개 변수를 추가합니다. 이러한 매개 변수는 변경하는 명령에만 필요합니다.

```powershell
function Test-MrSupportsShouldProcess {

    [CmdletBinding(SupportsShouldProcess)]
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

이제 **WhatIf** 및 **Confirm** 매개 변수가 있는 것을 확인할 수 있습니다.

```powershell
Get-Command -Name Test-MrSupportsShouldProcess -Syntax
```

```Output
Test-MrSupportsShouldProcess [[-ComputerName] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

다시 한 번 `Get-Command`를 사용하여 WhatIf 및 Confirm과 함께 공통 매개 변수 이름을 포함하는 실제 매개 변수 이름의 목록을 반환할 수도 있습니다.

```powershell
(Get-Command -Name Test-MrSupportsShouldProcess).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
WhatIf
Confirm
```

## <a name="parameter-validation"></a>매개 변수 유효성 검사

조기에 입력의 유효성을 검사합니다. 유효한 입력 없이 실행될 수 없는 경우 경로에서 코드가 계속되도록 허용할 필요가 없습니다.

항상 매개 변수에 사용되는 변수를 입력하세요(데이터 형식을 지정).

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

이전 예제에서는 **ComputerName** 매개 변수의 데이터 형식으로 **String**을 지정했습니다. 이렇게 하면 단일 컴퓨터 이름만 지정할 수 있습니다. 쉼표로 구분된 목록을 통해 둘 이상의 컴퓨터 이름을 지정하면 오류가 발생합니다.

```powershell
Test-MrParameterValidation -ComputerName Server01, Server02
```

```Output
Test-MrParameterValidation : Cannot process argument transformation on parameter
'ComputerName'. Cannot convert value to type System.String.
At line:1 char:42
+ Test-MrParameterValidation -ComputerName Server01, Server02
+
    + CategoryInfo          : InvalidData: (:) [Test-MrParameterValidation], ParameterBindingArg
     umentTransformationException
    + FullyQualifiedErrorId : ParameterArgumentTransformationError,Test-MrParameterValidation
```

현재 정의에서 문제는 **ComputerName** 매개 변수의 값을 생략해도 함수는 유효하지만 함수를 성공적으로 완료하려면 값이 필요하다는 것입니다. 여기에서 `Mandatory` 매개 변수 특성이 유용해집니다.

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

이전 예제에 사용된 구문은 PowerShell 버전 3.0 이상과 호환됩니다.
`[Parameter(Mandatory=$true)]`를 대신 지정하면 함수를 PowerShell 버전 2.0 이상과 호환되도록 만들 수 있습니다. **ComputerName**은 필수이므로 값이 하나 지정되지 않으면 함수는 값을 묻는 메시지를 표시합니다.

```powershell
Test-MrParameterValidation
```

```Output
cmdlet Test-MrParameterValidation at command pipeline position 1
Supply values for the following parameters:
ComputerName:
```

**ComputerName** 매개 변수에 둘 이상의 값을 허용하려면 **String** 데이터 형식을 사용하되 문자열 배열을 허용하도록 여는 대괄호와 닫는 대괄호를 데이터 형식에 추가합니다.

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string[]]$ComputerName
    )

    Write-Output $ComputerName

}
```

**ComputerName** 매개 변수가 지정되지 않은 경우 이 매개 변수에 대한 기본값을 지정할 수도 있습니다.
문제는 기본값을 필수 매개 변수와 함께 사용할 수 없다는 것입니다. 대신 `ValidateNotNullOrEmpty` 매개 변수 유효성 검사 특성을 기본값과 함께 사용해야 합니다.

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    Write-Output $ComputerName

}
```

기본값을 설정하는 경우에도 정적 값을 사용하지 마세요. 이전 예제에서는 값이 제공되지 않은 경우 자동으로 로컬 컴퓨터 이름으로 변환되는 `$env:COMPUTERNAME`이 기본값으로 사용됩니다.

## <a name="verbose-output"></a>자세한 정보 출력

인라인 주석은 특히 복잡한 코드를 작성하는 경우에는 유용하지만 사용자가 코드 자체를 확인하지 않는 한 볼 수 없습니다.

다음 예제에 표시된 함수는 `foreach` 루프에 인라인 주석이 포함되어 있습니다. 이 주석은 찾기가 그다지 어렵지 않을 수 있지만, 함수가 수백 개의 코드 줄을 포함한다고 가정해 보세요.

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        #Attempting to perform some action on $Computer <<-- Don't use
        #inline comments like this, use write verbose instead.
        Write-Output $Computer
    }

}
```

더 나은 옵션은 인라인 주석 대신 `Write-Verbose`를 사용하는 것입니다.

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        Write-Verbose -Message "Attempting to perform some action on $Computer"
        Write-Output $Computer
    }

}
```

**Verbose** 매개 변수 없이 함수를 호출하면 자세한 정보 출력이 표시되지 않습니다.

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02
```

**Verbose** 매개 변수를 사용하여 호출하면 자세한 정보 출력이 표시됩니다.

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02 -Verbose
```

## <a name="pipeline-input"></a>파이프라인 입력

함수에서 파이프라인 입력을 허용하도록 하려면 몇 가지 추가 코딩이 필요합니다. 이 책의 앞부분에서 설명한 것처럼 명령은 **값 기준**(형식 기준) 또는 **속성 이름 기준**으로 파이프라인 입력을 허용할 수 있습니다. 네이티브 명령과 마찬가지로 함수를 작성하여 이러한 유형의 입력 중 하나 또는 둘 모두를 허용할 수 있습니다.

**값 기준**으로 파이프라인 입력을 허용하려면 해당 매개 변수에 `ValueFromPipeline` 매개 변수 특성을 지정합니다. 각 데이터 형식 중 하나에서만 **값 기준**으로 파이프라인 입력을 수락할 수 있다는 데 유의해야 합니다. 예를 들어 문자열 입력을 허용하는 두 개의 매개 변수가 있는 경우 이 중 하나만 **값 기준**으로 파이프라인 입력을 허용할 수 있습니다. 두 문자열 매개 변수 모두에 지정할 경우 파이프라인 입력이 어느 매개 변수에 바인딩할지 알 수 없기 때문입니다. 이것이 필자가 이 유형의 파이프라인 입력을 **값 기준** 대신 _형식 기준_으로 부르는 또 다른 이유입니다.

파이프라인 입력은 `foreach` 루프에서 항목이 처리되는 방식과 비슷하게 한 번에 한 항목으로 제공됩니다.
배열을 입력으로 허용하는 경우 최소한 `process` 블록이 이들 각 항목을 처리하는 데 필요합니다. 단일 값만 입력으로 허용하는 경우에는 `process` 블록이 필요하지 않지만 일관성을 위해 지정하는 것이 좋습니다.

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline)]
        [string[]]$ComputerName
    )

    PROCESS {
        Write-Output $ComputerName
    }

}
```

**속성 이름 기준**으로 파이프라인 입력을 허용하는 것은 비슷하지만 `ValueFromPipelineByPropertyName` 매개 변수 특성을 사용하여 지정되고 데이터 형식에 관계없이 원하는 수의 매개 변수에 지정될 수 있다는 점만 다릅니다. 핵심은 파이프되는 명령의 출력이 매개 변수 이름 또는 함수의 매개 변수 별칭과 일치하는 속성 이름을 포함해야 한다는 점입니다.

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
            Write-Output $ComputerName
    }

}
```

`BEGIN` 및 `END` 블록은 선택 사항입니다. `BEGIN`은 `PROCESS` 블록 앞에 지정되고 파이프라인에서 수신되는 항목 이전에 초기 작업을 수행하는 데 사용됩니다. 다음을 이해하는 것이 중요합니다. 파이프되는 값은 `BEGIN` 블록에서 액세스할 수 없습니다. `END` 블록은 `PROCESS` 블록 다음에 지정되고, 파이프된 항목이 모두 처리되면 정리에 사용됩니다.

## <a name="error-handling"></a>오류 처리

다음 예제에 표시된 함수는 컴퓨터에 연결할 수 없을 때 처리되지 않은 예외를 생성합니다.

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            Test-WSMan -ComputerName $Computer
        }
    }

}
```

PowerShell에서는 오류를 처리하는 몇 가지 다른 방법이 있습니다. `Try/Catch`는 오류를 처리하는 최신 방법입니다.

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

이전 예제에 표시된 함수는 오류 처리를 사용하지만 처리되지 않은 예외도 생성합니다. 명령이 종료 오류를 생성하지 않기 때문입니다. 이를 이해하는 것도 중요합니다. 종료 오류만 catch됩니다. 종료되지 않는 오류를 종료하는 오류로 설정하려면 **Stop**을 값으로 사용하여 **ErrorAction** 매개 변수를 지정합니다.

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer -ErrorAction Stop
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

반드시 필요한 경우가 아니면 전역 `$ErrorActionPreference` 변수를 수정하지 마세요. PowerShell 함수 내에서 직접 .NET과 같은 항목을 사용하는 경우 명령 자체에서 **ErrorAction**을 지정할 수 없습니다. 이 시나리오에서는 전역 `$ErrorActionPreference` 변수를 변경해야 할 수 있지만, 변경하는 경우 명령을 시도해본 후 즉시 다시 변경하세요.

## <a name="comment-based-help"></a>주석 기반 도움말

함수를 공유하는 다른 사용자가 사용 방법을 알 수 있도록 함수에 주석 기반 도움말을 추가하는 것이 모범 사례로 간주됩니다.

```powershell
function Get-MrAutoStoppedService {

<#
.SYNOPSIS
    Returns a list of services that are set to start automatically, are not
    currently running, excluding the services that are set to delayed start.

.DESCRIPTION
    Get-MrAutoStoppedService is a function that returns a list of services from
    the specified remote computer(s) that are set to start automatically, are not
    currently running, and it excludes the services that are set to start automatically
    with a delayed startup.

.PARAMETER ComputerName
    The remote computer(s) to check the status of the services on.

.PARAMETER Credential
    Specifies a user account that has permission to perform this action. The default
    is the current user.

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1', 'Server2'

.EXAMPLE
     'Server1', 'Server2' | Get-MrAutoStoppedService

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1' -Credential (Get-Credential)

.INPUTS
    String

.OUTPUTS
    PSCustomObject

.NOTES
    Author:  Mike F Robbins
    Website: http://mikefrobbins.com
    Twitter: @mikefrobbins
#>

    [CmdletBinding()]
    param (

    )

    #Function Body

}
```

함수에 주석 기반 도움말을 추가하는 경우 기본 제공 명령과 마찬가지로 도움말을 검색할 수 있습니다.

PowerShell에서 함수를 작성하는 모든 구문은 특히 이제 막 시작하는 사용자에게는 압도적으로 느껴질 수 있습니다. 필자는 가끔 특정 구문이 기억나지 않을 때 별도의 모니터에서 ISE의 두 번째 복사본을 열고 함수의 코드를 입력하는 동안 "Cmdlet(고급 함수) -전체" 코드 조각을 확인합니다. PowerShell ISE에서 <kbd>Ctrl</kbd>+<kbd>J</kbd> 키 조합을 사용하여 이 코드 조각에 액세스할 수 있습니다.

## <a name="summary"></a>요약

이 장에서는 함수를 고급 함수로 전환하는 방법과 매개 변수 유효성 검사, 자세한 정보 출력, 파이프라인 입력, 오류 처리, 주석 기반 도움말 등 PowerShell 함수를 작성할 때 고려해야 할 중요한 요소 몇 가지를 포함하여 PowerShell에서 함수를 작성하는 기본 사항을 알아보았습니다.

## <a name="review"></a>검토

1. PowerShell에서 승인된 동사 목록을 얻으려면 어떻게 하나요?
1. PowerShell 함수를 고급 함수로 전환하려면 어떻게 하나요?
1. **WhatIf** 및 **Confirm** 매개 변수는 언제 PowerShell 함수에 추가해야 하나요?
1. 종료되지 않는 오류를 종료하는 오류로 전환하려면 어떻게 하나요?
1. 주석 기반 도움말을 함수에 추가해야 하는 이유는 무엇인가요?

## <a name="recommended-reading"></a>권장 참조 항목

- [about_Functions][]
- [about_Functions_Advanced_Parameters][]
- [about_CommonParameters][]
- [about_Functions_CmdletBindingAttribute][]
- [about_Functions_Advanced][]
- [about_Try_Catch_Finally][]
- [about_Comment_Based_Help][]
- [비디오: 고급 함수 및 스크립트 모듈을 사용하여 PowerShell 도구 작성][]

<!-- link references -->
[about_Functions]: /powershell/module/microsoft.powershell.core/about/about_functions
[about_Functions_Advanced_Parameters]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters
[about_CommonParameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[about_Functions_CmdletBindingAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute
[about_Functions_Advanced]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[about_Try_Catch_Finally]: /powershell/module/microsoft.powershell.core/about/about_try_catch_finally
[about_Comment_Based_Help]: /powershell/module/microsoft.powershell.core/about/about_comment_based_help
[비디오: 고급 함수 및 스크립트 모듈을 사용하여 PowerShell 도구 작성]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/) [파스칼식 대/소문자]: /dotnet/standard/design-guidelines/capitalization-conventionss
