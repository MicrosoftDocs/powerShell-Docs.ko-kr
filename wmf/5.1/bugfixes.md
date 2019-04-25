---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1의 버그 수정
ms.openlocfilehash: f53fc40b79a3906ac2025b0eff342c0705b82655
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085051"
---
# <a name="bug-fixes-in-wmf-51"></a>WMF 5.1의 버그 수정

## <a name="bug-fixes"></a>버그 수정

WMF 5.1에서는 다음과 같은 주목할 만한 버그가 수정되었습니다.

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a>모듈 자동 검색에서 완전히 적용함 `$env:PSModulePath`

모듈 자동 검색(명령을 호출할 때 명시적 Import-Module 없이 모듈을 자동으로 로드)이 WMF 3에 도입되었습니다.
도입될 때 PowerShell에서는 `$env:PSModulePath`를 사용하기 전에 `$PSHome\Modules`에 있는 명령을 확인했습니다.

WMF5.1에서는 `$env:PSModulePath`를 완전히 적용하도록 이 동작을 변경합니다.
따라서 PowerShell에서 제공하는 명령(예: `Get-ChildItem`)을 정의하는 사용자 작업 모듈이 자동으로 로드되고 기본 제공 명령을 올바로 재정의할 수 있습니다.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>파일 리디렉션에서 더 이상 하드 코드하지 않음 `-Encoding Unicode`

PowerShell의 모든 이전 버전에서는 PowerShell에서 `-Encoding Unicode`를 추가했으므로 파일 리디렉션 연산자(예: `Get-ChildItem > out.txt`)를 사용하여 파일 인코딩을 제어할 수 없습니다.

WMF 5.1부터 이제 `$PSDefaultParameterValues`를 설정하여 리디렉션의 파일 인코딩을 변경할 수 있습니다.

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>구성원 액세스에서의 회귀 수정 `System.Reflection.TypeInfo`

WMF 5.0에 도입된 회귀가 `System.Reflection.RuntimeType`의 구성원(예: `[int].ImplementedInterfaces`) 액세스를 중단시켰습니다.
이 버그는 WMF 5.1에서 수정되었습니다.


### <a name="fixed-some-issues-with-com-objects"></a>COM 개체의 몇 가지 문제 수정

WMF 5.0에서는 COM 개체에 대한 메서드를 호출하고 COM 개체의 속성에 액세스하는 새로운 COM 바인더를 도입했습니다.
이 새 바인더는 성능을 크게 향상했지만 몇 가지 버그도 도입했습니다. 이 버그는 WMF 5.1에서 수정되었습니다.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>인수 변환이 올바로 수행되지 않을 수도 있었음

다음 예제에서,

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

SendKeys 메서드에는 문자열이 필요하지만 PowerShell은 문자를 문자열로 변환하지 않고 IDispatch::Invoke에서 변환을 수행하게 했습니다. IDispatch::Invoke는 VariantChangeType을 사용하여 변환을 수행하므로 이 예에서는 Volume.Mute 키 대신 '1', '7' 및 '3' 키가 보내졌습니다.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>열거 가능 COM 개체가 올바로 처리되지 않을 수도 있음

PowerShell에서는 대부분의 열거 가능 개체를 정상적으로 열거하지만 WMF 5.0에 도입된 회귀로 인해 IEnumerable을 구현하는 COM 개체가 열거되지 못했습니다.  예:

```powershell
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

위의 예에서 WMF 5.0은 키/값 쌍을 열거하지 않고 Scripting.Dictionary를 파이프라인에 잘못 썼습니다.

이 변경으로 [issue 1752224 on Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)(Connect의 문제 1752224)도 해결됩니다.

### <a name="ordered-was-not-allowed-inside-classes"></a>`[ordered]`는 클래스 내에서 허용되지 않았음

WMF 5.0에서는 클래스에 사용된 형식 리터럴의 유효성을 검사하는 클래스를 도입했습니다.
`[ordered]`는 형식 리터럴로 보이지만 실제 .NET 형식이 아닙니다.
WMF 5.0에서는 클래스 내에 있는 `[ordered]`에 대해 오류를 잘못 보고했습니다.

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>여러 버전이 있는 정보 항목에 대한 도움말이 작동하지 않음

WMF5.5.1 이전에는 모듈의 여러 버전이 설치되어 있고 이들 버전이 모두 about_PSReadline과 같은 하나의 도움말 항목을 공유한 경우 `help about_PSReadline`에서 여러 항목을 반환하므로 실제 도움말을 볼 수 있는 방법이 명확히 없었습니다.

WMF 5.1에서는 항목의 최신 버전에 대한 도움말을 반환하여 이 문제를 수정합니다.

`Get-Help`에서는 도움말이 필요한 버전을 지정하는 방법을 제공하지 않습니다.
이 문제를 해결하려면 모듈 디렉터리로 이동하고 즐겨 사용하는 편집기와 같은 도구에서 직접 도움말을 표시합니다.

### <a name="powershellexe-reading-from-stdin-stopped-working"></a>powershell.exe가 STDIN에서 읽기 작동이 중지됨

고객이 네이티브 앱에서 `powershell -command -`를 사용하여 PowerShell을 실행함으로써 STDIN을 통해 스크립트를 전달하는 기능이 아쉽게도 콘솔 호스트의 다른 변경 내용으로 인해 손상되었습니다.

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a>시작 시 powershell.exe의 CPU 사용량이 급증함

PowerShell은 로그인에 지연이 발생하지 않도록 WMI 쿼리를 사용하여 그룹 정책을 통해 시작되었는지를 확인합니다.
WMI Win32_Process 클래스는 현지 표준 시간대 정보를 검색하려고 시도하므로 WMI 쿼리는 시스템의 모든 프로세스로 tzres.mui.dll을 삽입하게 됩니다.
따라서 wmiprvse(WMI 공급자 호스트)에서 CPU 사용량이 엄청나게 급증하게 됩니다.
해결 방법은 WMI를 사용하는 대신 Win32 API 호출을 사용하여 같은 정보를 가져오는 것입니다.
