---
ms.date: 09/14/2020
title: PowerShell에서 실험적 기능 사용
description: 현재 사용 가능한 실험적 기능과 사용 방법을 나열합니다.
ms.openlocfilehash: 74623240bfb19022ae342a5d23e2ed4f455afa45
ms.sourcegitcommit: 30c0c1563f8e840f24b65297e907f3583d90e677
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90574473"
---
# <a name="using-experimental-features-in-powershell"></a>PowerShell에서 실험적 기능 사용

PowerShell의 실험적 기능 지원에서는 PowerShell 또는 PowerShell 모듈에서 기존의 안정적인 기능과 함께 실험적 기능을 사용할 수 있는 메커니즘을 제공합니다.

실험적 기능은 디자인이 완성되지 않은 기능입니다. 사용자는 이 기능을 테스트하고 피드백을 제공할 수 있습니다. 실험적 기능이 완성되면 해당 디자인 변경 내용은 호환성이 손상되는 변경이 됩니다.

> [!CAUTION]
> 이로 인해 중단이 발생할 수 있으므로 실험적 기능은 프로덕션에서 사용하기에 적합하지 않습니다. 실험적 기능은 공식적으로 지원되지 않습니다. 하지만 피드백과 버그 보고서는 언제나 환영합니다. [GitHub 소스 리포지토리](https://github.com/PowerShell/PowerShell/issues/new/choose)에서 문제를 제출할 수 있습니다.

이러한 기능을 사용 설정 또는 해제하는 방법은 [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features)를 참조하세요.

## <a name="available-features"></a>사용 가능한 기능

이 문서에서는 사용 가능한 실험적 기능과 해당 기능을 사용하는 방법을 설명합니다.

|                            속성                            |   6.2   |   7.0   |   7.1   |
| ---------------------------------------------------------- | :-----: | :-----: | :-----: |
| PSTempDrive(PS 7.0 이상에서 일반)                        | &check; |         |         |
| PSUseAbbreviationExpansion(PS 7.0 이상에서 일반)         | &check; |         |         |
| PSCommandNotFoundSuggestion                                | &check; | &check; | &check; |
| PSImplicitRemotingBatching                                 | &check; | &check; | &check; |
| Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace |         | &check; | &check; |
| PSDesiredStateConfiguration.InvokeDscResource              |         | &check; | &check; |
| PSNullConditionalOperators(PS 7.1 이상에서 주요 기능)         |         | &check; |         |
| PSUnixFileStat(Windows가 아닌 경우만 해당)                          |         | &check; | &check; |
| PSNativePSPathResolution(PS 7.1 이상에서 주요 기능)           |         |         |         |
| PSCultureInvariantReplaceOperator                          |         |         | &check; |
| PSNotApplyErrorActionToStderr                              |         |         | &check; |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a>Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace

PowerShell 7.0에서 이 실험은 사용자가 디버거를 연결할 때 PowerShell이 현재 위치에서 즉시 중단할지 여부를 결정할 수 있도록 `Debug-Runspace` 및 `Debug-Job` cmdlet에서 **BreakAll** 매개 변수를 활성화합니다.

PowerShell 7.1에서 이 실험은 `*-PSBreakpoint` cmdlet에 **Runspace** 매개 변수도 추가합니다.

- `Disable-PSBreakpoint`
- `Enable-PSBreakpoint`
- `Get-PSBreakpoint`
- `Remove-PSBreakpoint`
- `Set-PSBreakpoint`

**Runspace** 매개 변수는 지정된 Runspace에서 중단점과 상호 작용할 **Runspace** 개체를 지정합니다.

```powershell
Start-Job -ScriptBlock {
    Set-PSBreakpoint -Command Start-Sleep
    Start-Sleep -Seconds 10
}

$runspace = Get-Runspace -Id 1

$breakpoint = Get-PSBreakPoint -Runspace $runspace
```

이 예제에서는 작업이 시작되고 `Set-PSBreakPoint`가 실행될 때 중단되도록 중단점이 설정되어 있습니다. Runspace는 변수에 저장되고 **Runspace** 매개 변수를 사용하여 `Get-PSBreakPoint` 명령에 전달됩니다. 그런 다음 `$breakpoint` 변수에서 중단점을 검사할 수 있습니다.

## <a name="pscommandnotfoundsuggestion"></a>PSCommandNotFoundSuggestion

**CommandNotFoundException** 다음에 유사 일치 검색을 기반으로 가능한 명령을 추천합니다.

```powershell
PS> get
```

```Output
get: The term 'get' is not recognized as the name of a cmdlet, function, script file, or operable
program. Check the spelling of the name, or if a path was included, verify that the path is correct
and try again.

Suggestion [4,General]: The most similar commands are: set, del, ft, gal, gbp, gc, gci, gcm, gdr,
gcs.
```

## <a name="pscultureinvariantreplaceoperator"></a>PSCultureInvariantReplaceOperator

`-replace` 연산자 문의 왼쪽 피연산자가 문자열이 아닌 경우 해당 피연산자는 문자열로 변환됩니다.

이 기능을 사용하지 않도록 설정하면 `-replace` 연산자는 문화권 구분 문자열 변환을 수행합니다.
예를 들어 문화권이 프랑스어(fr)로 설정된 경우 값 `1.2`는 문자열 `1,2`로 변환됩니다.

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

이 기능을 사용하도록 설정하는 경우:

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a>PSDesiredStateConfiguration.InvokeDscResource

비 Windows 시스템에서 MOF 컴파일이 가능해지고 LCM 없이 `Invoke-DSCResource`를 사용할 수 있도록 합니다.

## <a name="psimplicitremotingbatching"></a>PSImplicitRemotingBatching

이 기능은 셸에 입력한 명령을 검사합니다. 모든 명령이 간단한 파이프라인을 구성하는 암시적 원격 구현 프록시 명령인 경우 명령이 함께 일괄 처리되고 단일 원격 파이프라인으로 호출됩니다.

예제:

```powershell
# Create remote session and import TestIMod module
$s = nsn -host remoteMachine
icm $s { ipmo 'C:\Users\user\Documents\WindowsPowerShell\Modules\TestIMod\TestIMod.psd1' }
Import-PSSession $s -mod testimod

$maxProcs = 1000
$filter = 'pwsh','powershell*','wmi*'

# Without batching, this pipeline takes approximately 12 seconds to run
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 12
Milliseconds      : 463

# But with the batching experimental feature enabled, it takes approximately 0.20 seconds
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 209
```

위에서 설명한 것처럼 일괄 처리 기능을 사용하도록 설정하면 세 개의 암시적 원격 구현 프록시 명령 `Get-AllProcesses`, `Select-Custom`, `Group-Stuff`가 원격 세션에서 실행되고 파이프라인의 결과는 클라이언트에 반환되는 유일한 데이터입니다. 이렇게 하면 클라이언트와 원격 세션 간에 전송되는 데이터의 양이 줄어들고 개체 직렬화 및 역직렬화도 감소합니다.

## <a name="psnativepspathresolution"></a>PSNativePSPathResolution

FileSystem 공급자를 사용하는 PSDrive 경로를 네이티브 명령에 전달하는 경우 확인된 파일 경로가 네이티브 명령에 전달됩니다. 따라서 이제 `code temp:/test.txt`와 같은 명령이 정상적으로 작동합니다.

또한 Windows에서 `~`로 시작하는 경로는 전체 경로로 확인되고 네이티브 명령에 전달됩니다. 두 경우 모두 해당 경로는 관련 운영 체제에 대한 디렉터리 구분 기호로 정규화됩니다.

- 경로가 PSDrive 또는 `~`(Windows)가 아닌 경우 경로 정규화가 발생하지 않습니다.
- 경로가 작은따옴표로 묶여 있으면 이를 확인하여 리터럴로 처리하지 않습니다.

> [!NOTE]
> 이 기능은 실험적 단계를 벗어났으며 PowerShell 7.1 이상에서 주요 기능입니다.

## <a name="psnotapplyerroractiontostderr"></a>PSNotApplyErrorActionToStderr

이 실험적 기능을 사용하는 경우 리디렉션 연산자(`2>&1`)를 사용하는 경우처럼 네이티브 명령에서 리디렉션된 오류 레코드는 `$Error` 변수에 기록되지 않으며 기본 설정 변수 `$ErrorActionPreference`는 리디렉션된 출력에 영향을 주지 않습니다.

많은 네이티브 명령이 추가 정보에 대한 대체 스트림으로 `stderr`에 기록합니다. 이 동작은 오류를 살펴볼 때 혼동을 일으킬 수 있으며, `$ErrorActionPreference`가 출력에서 알림을 차단하는 상태로 설정된 경우 사용자에 대한 추가 출력 정보가 손실될 수 있습니다.

네이티브 명령에 0이 아닌 종료 코드가 있으면 `$?`가 `$false`로 설정됩니다. 종료 코드가 0인 경우 `$?`가 `$true`로 설정됩니다.

## <a name="psnullconditionaloperators"></a>PSNullConditionalOperators

Null 조건부 멤버 액세스 연산자 `?.` 및 `?[]`에 대한 새 연산자를 도입합니다. Null 멤버 액세스 연산자는 스칼라 형식 및 배열 형식에 사용할 수 있습니다. 변수가 null이 아닌 경우 액세스한 멤버의 값을 반환합니다. 변수 값이 null이면 null을 반환합니다.

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

`propname` 속성에 액세스하고 `$x`가 null이 아닌 경우에만 해당 값이 반환됩니다. 마찬가지로 인덱서는 `$x`가 null이 아닌 경우에만 사용됩니다. `$x`가 null이면 null이 반환됩니다.

`?.` 및 `?[]` 연산자는 멤버 액세스 연산자이며 변수 이름과 연산자 사이에 공백을 사용할 수 없습니다.

PowerShell에서는 변수 이름의 일부로 `?`를 허용하므로 변수 이름과 연산자 사이에 공백 없이 연산자를 사용하는 경우 명확성이 필요합니다. 명확성을 위해 변수는 변수 이름 주위에 `{}`를 사용해야 합니다(예: `${x?}?.propertyName` 또는 `${y}?[0]`).

> [!NOTE]
> 이 기능은 실험적 단계를 벗어났으며 PowerShell 7.1 이상에서 주요 기능입니다.

## <a name="pstempdrive"></a>PSTempDrive

사용자의 임시 디렉터리 경로에 매핑된 `TEMP:` PSDrive를 만듭니다.

> [!NOTE]
> 이 기능은 실험적 단계를 벗어났으며 PowerShell 7 이상에서 주요 기능입니다.

## <a name="psunixfilestat"></a>PSUnixFileStat

이 기능은 Unix와 비슷한 파일 목록을 사용할 수 있도록 파일 시스템 공급자의 출력에 Unix **stat** API의 데이터를 포함하는 새로운 동작을 제공합니다. 기본 Unix 형식 시스템의 일반 식 `stat(2)` API를 포함하는 **UnixStat**라는 파일 시스템 공급자에서 새 note 속성을 추가합니다.

`Get-ChildItem`의 출력은 다음과 비슷합니다.

```powershell
dir | select -first 4 -skip 5


    Directory: /Users/jimtru/src/github/forks/JamesWTruher/PowerShell-1

UnixMode   User      Group           LastWriteTime        Size Name
--------   ----      -----           -------------        ---- ----
drwxr-xr-x jimtru    staff        10/23/2019 13:16         416 test
drwxr-xr-x jimtru    staff         11/8/2019 10:37         896 tools
-rw-r--r-- jimtru    staff         11/8/2019 10:37      112858 build.psm1
-rw-r--r-- jimtru    staff         11/8/2019 10:37      201297 CHANGELOG.md
```

## <a name="psuseabbreviationexpansion"></a>PSUseAbbreviationExpansion

이 기능을 사용하면 축약된 cmdlet 및 함수에 대한 탭 완성 기능을 사용할 수 있습니다.

다음은 그 예입니다. 

- `i-psdf<tab>`는 `Import-PowerShellDataFile`을 반환합니다.
- `u-akvmssdr<tab>``Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`를 반환합니다

이는 탭 완성 기능에만 사용할 수 있으므로(대화형) `i-psdf`는 스크립트에서 유효한 cmdlet 이름이 아닙니다.

> [!NOTE]
> 이 기능은 실험적 단계를 벗어났으며 PowerShell 7 이상에서 주요 기능입니다.
