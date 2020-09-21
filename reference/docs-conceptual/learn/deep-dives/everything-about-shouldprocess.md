---
title: ShouldProcess에 대해 알고 싶은 모든 것
description: ShouldProcess는 자주 간과되는 중요 기능입니다. WhatIf 및 Confirm 매개 변수를 사용하면 함수에 쉽게 추가할 수 있습니다.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 6bd4dbd5255203f2daf804163aa2a84d992d6697
ms.sourcegitcommit: 0afff6edbe560e88372dd5f1cdf51d77f9349972
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86469738"
---
# <a name="everything-you-wanted-to-know-about-shouldprocess"></a>ShouldProcess에 대해 알고 싶은 모든 것

PowerShell 함수에는 사용자와의 상호 작용 방식을 크게 개선하는 몇 가지 기능이 있습니다.
자주 간과되는 한 가지 중요한 기능은 `-WhatIf` 및 `-Confirm` 지원이며 함수에도 쉽게 추가할 수 있습니다. 이 문서에서는 이 기능을 구현하는 방법을 자세히 설명합니다.

> [!NOTE]
> 이 문서의 [원래 버전][]은 [@KevinMarquette][]가 작성한 블로그에 나옵니다. PowerShell 팀은 이 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다. [PowerShellExplained.com][]에 있는 그의 블로그를 확인하세요.

함수에서 사용 설정하면 사용자에게 필요한 보안 네트워크를 제공할 수 있는 단순한 기능입니다. 위험할 수 있는 명령을 처음으로 수행할 때는 겁이 나기 마련입니다. `-WhatIf`를 이용해 이를 실행하면 결과는 크게 차이 납니다.

## <a name="commonparameters"></a>CommonParameters

이러한 [공통 매개 변수][]구현 방법을 살펴보기 전에 먼저 사용 방법을 간단하게 살펴보겠습니다.

## <a name="using--whatif"></a>-WhatIf 사용

명령에서 `-WhatIf` 매개 변수를 지원한다면 명령을 변경하는 대신 명령이 수행하는 작업을 확인할 수 있습니다. 문제가 될 수 있는 작업을 하기 전에 명령이 미칠 영향을 테스트하면 도움이 됩니다.

```powershell
PS C:\temp> Remove-Item -Path .\myfile1.txt -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

명령이 `ShouldProcess`를 올바르게 구현한다면 명령이 유발한 변경 내용이 모두 표시되어야 합니다. 다음은 와일드카드를 사용하여 여러 파일을 삭제하는 예입니다.

```powershell
PS C:\temp> Remove-Item -Path * -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\myfile2.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\importantfile.txt".
```

## <a name="using--confirm"></a>-Confirm 사용

`-WhatIf`를 지원하는 명령은 `-Confirm`도 지원합니다. 이 기능을 이용하면 수행하기 전에 작업을 확인할 수 있습니다.

```powershell
PS C:\temp> Remove-Item .\myfile1.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

계속하거나, 변경을 건너뛰거나, 스크립트를 중지하는 옵션이 제공됩니다. 도움말 프롬프트에서 다음과 같이 각 옵션을 설명합니다.

```Output
Y - Continue with only the next step of the operation.
A - Continue with all the steps of the operation.
N - Skip this operation and proceed with the next operation.
L - Skip this operation and all subsequent operations.
S - Pause the current pipeline and return to the command prompt. Type "exit" to resume the pipeline.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

### <a name="localization"></a>지역화

이 프롬프트는 PowerShell에서 지역화되므로 언어는 운영 체제의 언어를 기준으로 변경됩니다. PowerShell에서는 사용자를 위해 이 기능도 관리합니다.

### <a name="switch-parameters"></a>Switch 매개 변수

값을 스위치 매개 변수로 전달하는 방법을 간단하게 살펴보겠습니다. 이 매개 변수를 호출하는 주된 이유는 호출하는 함수에 매개 변수 값을 전달해야 할 때가 잦기 때문입니다.

첫 번째 방법은 모든 매개 변수에 사용할 수 있는 구체적인 매개 변수 구문이지만 일반적으로는 스위치 매개 변수에 사용합니다. 콜론을 지정하여 값을 매개 변수에 연결합니다.

```powershell
Remove-Item -Path:* -WhatIf:$true
```

변수에서도 같은 작업을 수행할 수 있습니다.

```powershell
$DoWhatIf = $true
Remove-Item -Path * -WhatIf:$DoWhatIf
```

두 번째 방법은 해시 테이블을 사용하여 값을 스플랫하는 것입니다.

```powershell
$RemoveSplat = @{
    Path = '*'
    WhatIf = $true
}
Remove-Item @RemoveSplat
```

해시 테이블이나 스플래팅을 잘 모르신다면 [해시 테이블에 대해 알고 싶은 모든 것][]을 다루는 다른 문서를 참조하세요.

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

`-WhatIf` 및 `-Confirm` 지원을 사용 설정하는 첫 번째 단계는 함수의 `CmdletBinding`에서 `SupportsShouldProcess`를 지정하는 것입니다.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt
}
```

이런 식으로 `SupportsShouldProcess`를 지정하면 이제 `-WhatIf`(또는 `-Confirm`)를 사용하여 함수를 호출할 수 있습니다.

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

`-WhatIf`라는 매개 변수는 만들지 않았습니다. `SupportsShouldProcess`를 지정하면 자동으로 생성되기 때문입니다. `Test-ShouldProcess`에서 `-WhatIf` 매개 변수를 지정하면 우리가 호출하는 항목은 `-WhatIf` 처리도 수행합니다.

### <a name="trust-but-verify"></a>신뢰하되 확인하세요

우리가 호출하는 모든 요소가 `-WhatIf` 값을 상속한다고 신뢰하면 위험합니다. 나머지 예제에서 이러한 신뢰가 효과가 없으며 다른 명령을 호출할 때는 더욱 그렇다고 가정하겠습니다. 여러분에게도 이 방법을 권장합니다.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt -WhatIf:$WhatIf
}
```

다른 내용을 설명한 다음 이 내용을 다시 다루겠습니다.

## <a name="pscmdletshouldprocess"></a>$PSCmdlet.ShouldProcess

`SupportsShouldProcess`를 구현하는 메서드는 `$PSCmdlet.ShouldProcess`입니다. `$PSCmdlet.ShouldProcess(...)`를 호출하면 어떤 논리를 사용자가 처리하고 PowerShell에서 나머지를 처리하는지 확인할 수 있습니다. 예제를 확인해보겠습니다.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        $file.Delete()
    }
}
```

`$PSCmdlet.ShouldProcess($file.name)`를 호출하면 `-WhatIf`(및 `-Confirm` 매개 변수)를 확인하고 적절하게 처리합니다. `-WhatIf`는 `ShouldProcess`가 변경 설명을 출력하고 `$false`를 반환하게 합니다.

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

`-Confirm`를 사용하여 호출하면 스크립트가 일시 중지되고 사용자에게 진행 여부를 묻는 메시지가 표시됩니다. 사용자가 `Y`를 선택하면 `$true`가 반환됩니다.

```powershell
PS> Test-ShouldProcess -Confirm
Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

`$PSCmdlet.ShouldProcess`의 놀라운 기능은 자세한 정보를 출력할 수도 있다는 것입니다. `ShouldProcess`를 구현할 때 자주 이 기능을 사용합니다.

```powershell
PS> Test-ShouldProcess -Verbose
VERBOSE: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

### <a name="overloads"></a>오버로드

다양한 매개 변수를 사용하여 메시지를 사용자 지정하는 `$PSCmdlet.ShouldProcess`용 몇 가지 오버 로드가 존재합니다. 첫 번째 오버로드는 위의 예제에서 이미 확인했습니다. 이 오버로드에 대해 좀 더 자세히 살펴보겠습니다.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    if($PSCmdlet.ShouldProcess('TARGET')){
        # ...
    }
}
```

이 오버로드는 함수 이름과 대상(매개 변수 값)을 모두 포함하는 출력을 생성합니다.

```powershell
What if: Performing the operation "Test-ShouldProcess" on target "TARGET".
```

두 번째 매개 변수를 작업으로 지정하면 메시지 내 함수 이름 대신 작업 값을 사용합니다.

```powershell
## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".
```

다음 방법은 메시지를 완전히 사용자 지정하는 매개 변수 3개를 지정하는 것입니다. 매개 변수 3개를 사용하면 첫 번째 매개 변수는 전체 메시지가 됩니다. 두 번째 매개 변수는 여전히 `-Confirm` 메시지 출력에서 사용합니다.

```powershell
## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

### <a name="quick-parameter-reference"></a>빠른 매개 변수 참조

사용해야 하는 매개 변수 확인만이 목적이라면 다양한 `-WhatIf` 시나리오에서 매개 변수에 따라 메시지가 어떻게 달라지는지 보여주는 빠른 참조를 확인하세요.

```powershell
## $PSCmdlet.ShouldProcess('TARGET')
What if: Performing the operation "FUNCTION_NAME" on target "TARGET".

## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".

## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

주로 이 기능을 매개 변수 2개와 함께 사용합니다.

### <a name="shouldprocessreason"></a>ShouldProcessReason

다른 오버로드보다 더 고급 기능인 네 번째 오버로드가 있습니다. 이 오버로드를 이용하면 `ShouldProcess`를 실행한 이유를 알 수 있습니다. 대신 `$WhatIf`가 `$true`인지 확인하면 되므로 이 내용은 참조용으로만 수록했습니다.

```powershell
$reason = ''
if($PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION',[ref]$reason)){
    Write-Output "Some Action"
}
$reason
```

`$reason` 변수를 `[ref]`를 사용하는 참조 변수로서 네 번째 매개 변수에 전달해야 합니다. `ShouldProcess`는 `$reason`을 값 `None` 또는 `WhatIf`로 채웁니다. 이 기능이 유용하다고 생각하지 않아 사용하지 않습니다.

### <a name="where-to-place-it"></a>배치 장소

`ShouldProcess`를 사용하면 스크립트 보안을 강화할 수 있습니다. 따라서 스크립트를 변경할 때는 이 기능을 사용해야 합니다. `$PSCmdlet.ShouldProcess` 호출을 변경하는 부분과 최대한 가깝게 배치하는 편입니다.

```powershell
## general logic and variable work
if ($PSCmdlet.ShouldProcess('TARGET','OPERATION')){
    # Change goes here
}
```

항목 컬렉션을 처리할 때는 항목별로 호출합니다. 따라서 호출은 foreach 루프 내에 배치됩니다.

```powershell
foreach ($node in $collection){
    # general logic and variable work
    if ($PSCmdlet.ShouldProcess($node,'OPERATION')){
        # Change goes here
    }
}
```

`ShouldProcess`를 변경하는 부분 근처에 배치하는 이유는 `-WhatIf`가 지정되면 최대한 많은 코드를 실행하고 싶기 때문입니다. 사용자가 이러한 오류를 확인할 수 있도록 가능하다면 설정 및 유효성 검사를 실행합니다.

제 프로젝트의 유효성을 검사하는 Pester 테스트에서도 이 기능을 즐겨 사용합니다. Pester에서 모형을 만들기 어려운 로직이 있다면 `ShouldProcess`에서 이를 래핑한 다음 테스트에서 `-WhatIf`를 이용해 호출합니다. 코드는 일부라도 테스트하는 것이 좋습니다.

### <a name="whatifpreference"></a>$WhatIfPreference

우리에게 있는 첫 번째 기본 설정 변수는 `$WhatIfPreference`입니다. 기본값은 `$false`입니다. `$true`로 설정하면 함수는 `-WhatIf`에서 지정한 대로 실행됩니다. 이를 세션에서 설정하면 모든 명령이 `-WhatIf` 실행을 수행합니다.

`-WhatIf`로 함수를 호출하면 `$WhatIfPreference` 값은 함수 범위 내에서 `$true`로 설정됩니다.

## <a name="confirmimpact"></a>ConfirmImpact

제 예제 대부분은 `-WhatIf`를 대상으로 하지만 지금까지 배운 모든 항목은 `-Confirm`를 사용하여 사용자에게 메시지를 표시합니다. 함수의 `ConfirmImpact`를 높음으로 설정하면 `-Confirm`으로 호출했을 때처럼 사용자에게 메시지가 표시됩니다.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param()

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

이 `Test-ShouldProcess` 호출은 `High`의 영향 때문에 `-Confirm` 작업을 수행합니다.

```powershell
PS> Test-ShouldProcess

Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "TARGET".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y
Some Action
```

하지만 사용자에게 메시지를 표시하지 않으면 다른 스크립트에서 사용하기 어렵다는 문제가 발생합니다. 이 경우 `$false`를 `-Confirm`으로 전달하면 메시지를 표시하지 않을 수 있습니다.

```powershell
PS> Test-ShouldProcess -Confirm:$false
Some Action
```

`-Force` 지원을 추가하는 방법은 이후 섹션에서 살펴보겠습니다.

### <a name="confirmpreference"></a>$ConfirmPreference

`$ConfirmPreference`는 `ConfirmImpact`에서 실행 확인 메시지를 표시하는 시점을 제어하는 자동 변수입니다. 다음은 `$ConfirmPreference`와 `ConfirmImpact` 모두에서 사용할 수 있는 값입니다.

- `High`
- `Medium`
- `Low`
- `None`

이러한 값을 사용하면 각 함수에 다양한 수준의 영향을 지정할 수 있습니다. `$ConfirmPreference`를 `ConfirmImpact`보다 높은 값으로 설정하면 실행 확인 메시지가 표시되지 않습니다.

기본적으로 `$ConfirmPreference`는 `High`로 설정되며 `ConfirmImpact`는 `Medium`입니다. 함수에서 사용자에게 메시지를 자동으로 표시되게 하려면 `ConfirmImpact`를 `High`로 설정하면 됩니다. 그렇지 않다면 위험할 때는 `Medium`으로 설정하고 명령이 프로덕션 환경에서 항상 안전하게 실행될 때는 `Low`로 설정해야 합니다. `none`으로 설정하면 `-Confirm`을 지정해도 메시지가 표시되지 않습니다(하지만 `-WhatIf` 지원은 계속 제공됩니다).

`-Confirm`으로 함수를 호출하면 `$ConfirmPreference` 값은 함수 범위 내에서 `Low`로 설정됩니다.

### <a name="suppressing-nested-confirm-prompts"></a>중첩된 확인 메시지 표시 안 함

`$ConfirmPreference`를 이용하면 호출하는 함수를 기준으로 선택할 수 있습니다. 이렇게 하면 확인 메시지를 추가하는 시나리오를 만들 수 있고 호출하는 함수도 사용자에게 메시지를 표시합니다.

메시지 표시를 이미 처리했을 때 호출하는 명령에 `-Confirm:$false`를 지정하곤 합니다.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        Remove-Item -Path $file.FullName -Confirm:$false
    }
}
```

이렇게 하면 이전 경고로 돌아갑니다. `-WhatIf`를 함수에 전달하지 않을 때와 `-Confirm`을 함수에 전달할 때는 미묘한 차이가 발생합니다. 여기에 대해서는 나중에 다시 살펴보겠습니다.

## <a name="pscmdletshouldcontinue"></a>$PSCmdlet.ShouldContinue

`ShouldProcess`에서 제공하는 것보다 더 높은 수준의 제어가 필요하다면 `ShouldContinue`를 이용해 메시지를 직접 트리거하면 됩니다. `ShouldContinue`는 실행할 때마다 메시지를 표시하기 때문에 `$ConfirmPreference`, `ConfirmImpact`, `-Confirm`, `$WhatIfPreference`, `-WhatIf`는 무시됩니다.

얼핏 보면 `ShouldProcess`는 `ShouldContinue`와 혼동하기 쉽습니다. 저는 `ShouldProcess`를 자주 사용하는데 매개 변수가 `CmdletBinding`의 `SupportsShouldProcess`에서 호출되기 때문입니다.
거의 모든 시나리오에서는 `ShouldProcess`를 사용해야 합니다. 그래서 이 방법을 가장 먼저 설명했습니다.

실제로 작동하는 `ShouldContinue`를 살펴보겠습니다.

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    if($PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

이것은 옵션이 적은 더 간단한 메시지를 표시합니다.

```powershell
Test-ShouldContinue

Second
TARGET
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

`ShouldContinue`의 가장 큰 문제는 항상 메시지를 표시하기 때문에 사용자가 상호적으로 실행해야 한다는 것입니다. 항상 다른 스크립트에서 사용할 수 있는 도구를 이용해 작성해야 합니다. 이 작업을 수행하려면 `-Force`를 구현해야 합니다. 이 방법은 나중에 다시 살펴보겠습니다.

### <a name="yes-to-all"></a>모두 예

이것은 `ShouldProcess`에서는 자동으로 처리되지만 `ShouldContinue`에서는 약간의 작업이 필요합니다. 논리 제어를 위해 몇 가지 값을 참조로 전달해야 하는 두 번째 메서드 오버로드가 있습니다.

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    $collection = 1..5
    $yesToAll = $false
    $noToAll = $false

    foreach($target in $collection) {

        $continue = $PSCmdlet.ShouldContinue(
                "TARGET_$target",
                'OPERATION',
                [ref]$yesToAll,
                [ref]$noToAll
            )

        if ($continue){
            Write-Output "Some Action [$target]"
        }
    }
}
```

실행 중인 모습을 표시하고자 `foreach` 루프와 컬렉션을 추가했습니다. 쉽게 읽을 수 있도록 `if` 문에서 `ShouldContinue` 호출을 가져왔습니다. 네 가지 매개 변수로 메서드를 호출하면 읽기가 어려워지기 시작하지만 최대한 깔끔하게 표시하고자 노력했습니다.

## <a name="implementing--force"></a>-Force 구현

`ShouldProcess`와 `ShouldContinue`는 서로 다른 방법으로 `-Force`를 구현해야 합니다. 이러한 구현의 어려운 점은 `ShouldProcess`는 언제나 실행해야 하지만 `ShouldContinue`는 `-Force`를 지정했다면 실행하지 않아야 한다는 것입니다.

### <a name="shouldprocess--force"></a>ShouldProcess -Force

`ConfirmImpact`를 `high`로 설정한다면 사용자는 가장 먼저 `-Force`를 이용해 이를 무시하려 할 것입니다. 가장 먼저 하는 일이기도 합니다.

```powershell
Test-ShouldProcess -Force
Error: Test-ShouldProcess: A parameter cannot be found that matches parameter name 'force'.
```

`ConfirmImpact` 섹션의 내용을 떠올려보면, 이것은 다음처럼 호출해야 합니다.

```powershell
Test-ShouldProcess -Confirm:$false
```

이 작업을 수행해야 하며 `-Confirm:$false`가 `ShouldContinue`를 무시하지 않는다는 사실을 모르는 사람도 있습니다.
따라서 사용자의 안전을 위해 `-Force`를 구현해야 합니다. 이 전체 예제를 살펴보세요.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param(
        [Switch]$Force
    )

    if ($Force -and -not $Confirm){
        $ConfirmPreference = 'None'
    }

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

우리는 자체 `-Force` 스위치를 매개 변수로 추가하고, `CmdletBinding`에 `SupportsShouldProcess`를 추가할 때 사용할 수 있는 `$Confirm` 자동 매개 변수를 사용합니다.

```powershell
[CmdletBinding(
    SupportsShouldProcess,
    ConfirmImpact = 'High'
)]
param(
    [Switch]$Force
)
```

여기서 `-Force`를 집중적으로 다룹니다.

```powershell
if ($Force -and -not $Confirm){
    $ConfirmPreference = 'None'
}
```

사용자가 `-Force`를 지정한다면 우리는 사용자가 `-Confirm`도 지정할 때까지는 확인 메시지를 표시하지 않으려 합니다. 이렇게 하면 사용자는 변경 내용을 적용하면서도 여전히 변경 내용을 확인할 수 있습니다. 그러면 우리는 로컬 범위에 `$ConfirmPreference`를 설정하여 `ShouldProcess` 호출이 이를 발견하게 합니다.

```powershell
if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
```

사용자가 `-Force`와 `-WhatIf`를 모두 지정한다면 `-WhatIf`가 우선해야 합니다. 이 방법은 `ShouldProcess` 처리를 유지하는데 `-WhatIf`는 항상 처리되기 때문입니다.

`ShouldProcess`가 있는 `if` 문에 `$Force` 값에 대한 검사를 추가하면 안 됩니다. 이 시나리오에는 안티 패턴에 해당하지만 `ShouldContinue`에 관한 다음 섹션에서 보여드리겠습니다.

### <a name="shouldcontinue--force"></a>ShouldContinue -Force

이것은 `ShouldContinue`를 사용하여 `-Force`를 구현하는 올바른 방법입니다.

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param(
        [Switch]$Force
    )

    if($Force -or $PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

`$Force`를 `-or` 연산자 왼쪽에 배치하여 먼저 평가받게 합니다. 이런 방식으로 작성하면 `if` 문의 실행을 단축할 수 있습니다. `$force`가 `$true`라면 `ShouldContinue`는 실행되지 않습니다.

```powershell
PS> Test-ShouldContinue -Force
Some Action
```

`ShouldContinue`에서 지원하지 않으므로 이 시나리오에서는 `-Confirm`이나 `-WhatIf`에 대해서는 걱정하지 않아도 됩니다. 따라서 `ShouldProcess`와는 다르게 처리해야 합니다.

## <a name="scope-issues"></a>범위 문제

`-WhatIf`와 `-Confirm` 사용은 함수 내의 모든 요소와 함수가 호출하는 모든 요소에 적용되어야 합니다. 이를 위해 함수의 로컬 범위에서 `$WhatIfPreference`을 `$true`로 설정하거나 `$ConfirmPreference`를 `Low`로 설정합니다. 다른 함수를 호출하는 경우 `ShouldProcess` 호출은 이러한 값을 사용합니다.

실제로 대부분의 경우에 올바르게 작동합니다. 같은 범위에서 기본 제공 cmdlet 또는 함수를 호출한다면 언제나 올바르게 작동합니다. 콘솔의 스크립트 모듈에 있는 스크립트나 함수를 호출할 때도 마찬가지입니다.

제대로 작동하지 않는 경우는 스크립트 또는 스크립트 모듈이 다른 스크립트 모듈에서 함수를 호출할 때입니다. 큰 문제가 아닌 것처럼 보일 수도 있지만 여러분이 생성하거나 PSGallery에서 가져오는 모듈은 대부분 스크립트 모듈입니다.

가장 핵심적인 문제는 다른 스크립트 모듈의 함수에서 호출될 때는 스크립트 모듈이 `$WhatIfPreference` 또는 `$ConfirmPreference`(그리고 기타 다양한 요소)의 값을 상속하지 않는다는 것입니다.

이를 일반 규칙으로 요약하는 가장 좋은 방법은 이진 모듈에 서는 제대로 작동하지만 스크립트 모듈에서는 그렇지 않을 수도 있다고 정리하는 것입니다. 확신이 들지 않을 때 우리는 테스트해 보거나 제대로 작동하지 않을 것이라 가정합니다.

개인적으로 이것이 대단히 위험하다고 생각하는데, 고립된 상태에서는 정상적으로 작동하지만 서로 호출하면 정상적으로 작동하지 못하는 여러 모듈에 `-WhatIf` 지원을 추가하는 상황이 발생하기 때문입니다.

우리는 GitHub RFC를 이용해 이 문제를 해결합니다. 자세한 내용은 [스크립트 모듈 범위 이상으로 실행 기본 설정 전파][RFC]를 참조하세요.

## <a name="in-closing"></a>맺음말

사용해야 할 때마다 `ShouldProcess` 사용 방법을 확인합니다. `ShouldProcess`를 `ShouldContinue`와 구분하는 데 시간이 오래 걸립니다. 사용할 매개 변수를 거의 매번 조회해야 합니다. 그러니 혼란스러울 때가 있더라도 걱정할 필요가 없습니다. 이 문서는 필요할 때 여기서 참조하실 수 있습니다. 저도 자주 참조하겠습니다.

이 게시물이 마음에 든다면 아래 링크를 사용하여 Twitter에서 의견을 공유해 주세요. 제 콘텐츠에서 도움을 얻은 사람들의 의견을 언제나 환영합니다.

<!-- link references -->
[원래 버전]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[공통 매개 변수]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[해시 테이블에 대해 알고 싶은 모든 것]: everything-about-hashtable.md
[RFC]: https://github.com/PowerShell/PowerShell-RFC/pull/221#issuecomment-592954839
