---
ms.date: 12/14/2020
title: PowerShell에서 실험적 기능 사용
description: 현재 사용 가능한 실험적 기능과 사용 방법을 나열합니다.
ms.openlocfilehash: f97cea1dff4030da22be1efbe3cd5cbb7a9f3527
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685278"
---
# <a name="using-experimental-features-in-powershell"></a>PowerShell에서 실험적 기능 사용

PowerShell의 실험적 기능 지원에서는 PowerShell 또는 PowerShell 모듈에서 기존의 안정적인 기능과 함께 실험적 기능을 사용할 수 있는 메커니즘을 제공합니다.

실험적 기능은 디자인이 완성되지 않은 기능입니다. 사용자는 이 기능을 테스트하고 피드백을 제공할 수 있습니다. 실험적 기능이 완성되면 해당 디자인 변경 내용은 호환성이 손상되는 변경이 됩니다.

> [!CAUTION]
> 이로 인해 중단이 발생할 수 있으므로 실험적 기능은 프로덕션에서 사용하기에 적합하지 않습니다. 실험적 기능은 공식적으로 지원되지 않습니다. 하지만 피드백과 버그 보고서는 언제나 환영합니다. [GitHub 소스 리포지토리](https://github.com/PowerShell/PowerShell/issues/new/choose)에서 문제를 제출할 수 있습니다.

이러한 기능을 사용 설정 또는 해제하는 방법은 [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features)를 참조하세요.

## <a name="available-features"></a>사용 가능한 기능

이 문서에서는 사용 가능한 실험적 기능과 해당 기능을 사용하는 방법을 설명합니다.

|                            속성                            |   6.2   |   7.0   |   7.1   |   7.2   |
| ---------------------------------------------------------- | :-----: | :-----: | :-----: | :-----: |
| PSTempDrive(PS 7.0 이상에서 일반)                        | &check; |         |         |         |
| PSUseAbbreviationExpansion(PS 7.0 이상에서 일반)         | &check; |         |         |         |
| PSNullConditionalOperators(PS 7.1 이상에서 주요 기능)         |         | &check; |         |         |
| PSUnixFileStat(비 Windows 전용 - PS 7.1 이상에서 주요 기능)  |         | &check; |         |         |
| PSCommandNotFoundSuggestion                                | &check; | &check; | &check; | &check; |
| PSImplicitRemotingBatching                                 | &check; | &check; | &check; | &check; |
| Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace |         | &check; | &check; | &check; |
| PSDesiredStateConfiguration.InvokeDscResource              |         | &check; | &check; | &check; |
| PSNativePSPathResolution                                   |         |         | &check; | &check; |
| PSCultureInvariantReplaceOperator                          |         |         | &check; | &check; |
| PSNotApplyErrorActionToStderr                              |         |         | &check; | &check; |
| PSSubsystemPluginModel                                     |         |         | &check; | &check; |
| PSAnsiProgress                                             |         |         |         | &check; |
| PSAnsiRendering                                            |         |         |         | &check; |

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

## <a name="psansirendering"></a>PSAnsiRendering

이 실험은 PowerShell 7.2에서 추가되었습니다. 이 기능을 사용하면 PowerShell 엔진이 텍스트를 출력하고 `$PSStyle` 자동 변수를 추가하여 문자열 출력의 ANSI 렌더링을 제어하는 방법을 변경할 수 있습니다.

```powershell
PS> $PSStyle | Get-Member

   TypeName: System.Management.Automation.PSStyle

Name             MemberType Definition
----             ---------- ----------
Equals           Method     bool Equals(System.Object obj)
FormatHyperlink  Method     string FormatHyperlink(string text, uri link)
GetHashCode      Method     int GetHashCode()
GetType          Method     type GetType()
ToString         Method     string ToString()
Background       Property   System.Management.Automation.PSStyle+BackgroundColor Background {get;}
Blink            Property   string Blink {get;}
BlinkOff         Property   string BlinkOff {get;}
Bold             Property   string Bold {get;}
BoldOff          Property   string BoldOff {get;}
Foreground       Property   System.Management.Automation.PSStyle+ForegroundColor Foreground {get;}
Formatting       Property   System.Management.Automation.PSStyle+FormattingData Formatting {get;}
Hidden           Property   string Hidden {get;}
HiddenOff        Property   string HiddenOff {get;}
Italic           Property   string Italic {get;}
ItalicOff        Property   string ItalicOff {get;}
OutputRendering  Property   System.Management.Automation.OutputRendering OutputRendering {get;set;}
Progress         Property   System.Management.Automation.PSStyle+ProgressConfiguration Progress {get;}
Reset            Property   string Reset {get;}
Reverse          Property   string Reverse {get;}
ReverseOff       Property   string ReverseOff {get;}
Strikethrough    Property   string Strikethrough {get;}
StrikethroughOff Property   string StrikethroughOff {get;}
Underline        Property   string Underline {get;}
UnderlineOff     Property   string UnderlineOff {get;}
```

기본 멤버는 이름에 매핑되는 ANSI 이스케이프 시퀀스의 문자열을 반환합니다. 사용자 지정을 허용하도록 값을 설정할 수 있습니다.

자세한 내용은 [about_Automatic_Variables](/reference/7.2/Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)를 참조하세요.

> [!NOTE]
> C# 개발자는 싱글톤으로 `PSStyle`에 액세스할 수 있습니다. 사용법은 다음과 같습니다.
>
> ```csharp
> string output = $"{PSStyle.Instance.Foreground.Red}{PSStyle.Instance.Bold}Hello{PSStyle.Instance.Reset}";
> ```
>
> `PSStyle`은 System.Management.Automation 네임스페이스에 있습니다.

`$PSStyle`에 대한 액세스와 함께 PowerShell 엔진도 변경됩니다. PowerShell 서식 지정 시스템은 `$PSStyle.OutputRendering`을 반영하도록 업데이트되었습니다.

- `StringDecorated` 형식이 ANSI 이스케이프된 문자열을 처리하기 위해 추가되었습니다.
- 문자열에 ANSI 이스케이스 시퀀스가 포함된 경우나 문자열에 ESC 또는 C1 CSI가 포함된 경우 반환하도록 `string IsDecorated` 부울 속성이 추가되었습니다.
- `Length` 속성은 ANSI 이스케이프 시퀀스가 없는 텍스트의 길이 _만_ 반환합니다.
- `StringDecorated Substring(int contentLength)` 메서드는 인덱스 0에서 시작하여 ANSI 이스케이스 시퀀스가 포함되지 않는 콘텐츠 길이까지 substring을 반환합니다. 이 메서드는 문자열을 자르고 인쇄 가능한 공간을 차지하지 않는 ANSI 이스케이프 시퀀스를 유지하기 위해 테이블 서식 지정에 필요합니다.
- `string ToString()` 메서드는 동일하게 유지하고 문자열의 일반 텍스트 버전을 반환합니다.
- `string ToString(bool Ansi)` 메서드는 `Ansi` 매개 변수가 true인 경우 원시 ANSI 포함 문자열을 반환합니다. 아니면, ANSI 이스케이프 시퀀스가 제거된 일반 텍스트 버전이 반환됩니다.

`FormatHyperlink(string text, uri link)`는 하이퍼링크를 데코레이트하는 데 사용되는 ANSI 이스케이프 시퀀스가 포함된 문자열을 반환합니다. [Windows 터미널](https://www.microsoft.com/p/windows-terminal/9n0dx20hk701) 같은 일부 터미널 호스트는 터미널에서 렌더링된 텍스트를 클릭할 수 있도록 만드는 이 태그를 지원합니다.

## <a name="psansiprogress"></a>PSAnsiProgress

이 실험은 PowerShell 7.2에서 추가되었습니다. 이 기능을 통해 `$PSStyle.Progress` 멤버를 추가하고 진행률 보기 표시줄 렌더링을 제어할 수 있습니다.

- `$PSStyle.Progress.Style` - 렌더링 스타일을 설정하는 ANSI 문자열입니다.
- `$PSStyle.Progress.MaxWidth` - 보기의 최대 너비를 설정합니다. 콘솔 너비를 `0`으로 설정합니다.
  기본값은 `120`입니다.
- `$PSStyle.Progress.View` - `Minimal` 및 `Classic` 값을 포함하는 열거형입니다. `Classic`은 변경 내용이 없는 기존 렌더링입니다. `Minimal`은 최소한의 단일 줄 렌더링입니다. 기본값은 `Minimal`입니다.

다음 예에서는 렌더링 스타일을 최소 진행률 표시줄로 업데이트합니다.

```powershell
$PSStyle.Progress.View.Minimal
```

> [!NOTE]
> 이 기능을 사용하려면 실험적 기능인 **PSAnsiRendering** 을 사용하도록 설정되어 있어야 합니다.

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

이 기능은 Unix와 비슷한 파일 목록을 사용할 수 있도록 파일 시스템 공급자의 출력에 Unix **stat** API의 데이터를 포함하는 새로운 동작을 제공합니다. 기본 Unix 형식 시스템의 일반 식 `stat(2)` API를 포함하는 **UnixStat** 라는 파일 시스템 공급자에서 새 note 속성을 추가합니다.

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

> [!NOTE]
> 이 기능은 실험적 단계를 벗어났으며 PowerShell 7.1 이상에서 주요 기능입니다.

## <a name="psuseabbreviationexpansion"></a>PSUseAbbreviationExpansion

이 기능을 사용하면 축약된 cmdlet 및 함수에 대한 탭 완성 기능을 사용할 수 있습니다.

다음은 그 예입니다. 

- `i-psdf<tab>`는 `Import-PowerShellDataFile`을 반환합니다.
- `u-akvmssdr<tab>``Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`를 반환합니다

이는 탭 완성 기능에만 사용할 수 있으므로(대화형) `i-psdf`는 스크립트에서 유효한 cmdlet 이름이 아닙니다.

> [!NOTE]
> 이 기능은 실험적 단계를 벗어났으며 PowerShell 7 이상에서 주요 기능입니다.

## <a name="pssubsystempluginmodel"></a>PSSubsystemPluginModel

이 기능은 PowerShell에서 하위 시스템 플러그 인 모델을 사용하도록 설정합니다. 기능을 사용하면 `System.Management.Automation.dll` 구성 요소를 자체 어셈블리에 있는 개별 하위 시스템으로 분리할 수 있습니다. 이렇게 분리하면 핵심 PowerShell 엔진의 디스크 공간이 줄어들고 이 구성 요소가 최소 PowerShell 설치에 대한 선택적 기능이 될 수 있습니다.

현재 **CommandPredictor** 하위 시스템만 지원됩니다. 이 하위 시스템은 사용자 지정 예측 플러그 인을 제공하는 데 PSReadLine 모듈과 함께 사용됩니다. 나중에 **Job**, **CommandCompleter**, **Remoting** 및 기타 구성 요소를 `System.Management.Automation.dll` 외부의 하위 시스템 어셈블리로 분리할 수 있습니다.

실험적 기능으로는 새로운 cmdlet [Get-PSSubsystem](xref:Microsoft.PowerShell.Core.Get-PSSubsystem)이 있습니다. 이 cmdlet은 이 기능을 사용하도록 설정한 경우에만 사용할 수 있습니다. 이 cmdlet은 시스템에서 사용할 수 있는 하위 시스템에 대한 정보를 반환합니다.
