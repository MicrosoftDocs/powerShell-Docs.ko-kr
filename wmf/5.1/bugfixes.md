---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1의 버그 수정
ms.openlocfilehash: f53fc40b79a3906ac2025b0eff342c0705b82655
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795371"
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="f71e6-103">WMF 5.1의 버그 수정</span><span class="sxs-lookup"><span data-stu-id="f71e6-103">Bug Fixes in WMF 5.1</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="f71e6-104">버그 수정</span><span class="sxs-lookup"><span data-stu-id="f71e6-104">Bug fixes</span></span>

<span data-ttu-id="f71e6-105">WMF 5.1에서는 다음과 같은 주목할 만한 버그가 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a><span data-ttu-id="f71e6-106">모듈 자동 검색에서 완전히 적용함 `$env:PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="f71e6-106">Module auto-discovery fully honors `$env:PSModulePath`</span></span>

<span data-ttu-id="f71e6-107">모듈 자동 검색(명령을 호출할 때 명시적 Import-Module 없이 모듈을 자동으로 로드)이 WMF 3에 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span>
<span data-ttu-id="f71e6-108">도입될 때 PowerShell에서는 `$env:PSModulePath`를 사용하기 전에 `$PSHome\Modules`에 있는 명령을 확인했습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="f71e6-109">WMF5.1에서는 `$env:PSModulePath`를 완전히 적용하도록 이 동작을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span>
<span data-ttu-id="f71e6-110">따라서 PowerShell에서 제공하는 명령(예: `Get-ChildItem`)을 정의하는 사용자 작업 모듈이 자동으로 로드되고 기본 제공 명령을 올바로 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="f71e6-111">파일 리디렉션에서 더 이상 하드 코드하지 않음 `-Encoding Unicode`</span><span class="sxs-lookup"><span data-stu-id="f71e6-111">File redirection no longer hard-codes `-Encoding Unicode`</span></span>

<span data-ttu-id="f71e6-112">PowerShell의 모든 이전 버전에서는 PowerShell에서 `-Encoding Unicode`를 추가했으므로 파일 리디렉션 연산자(예: `Get-ChildItem > out.txt`)를 사용하여 파일 인코딩을 제어할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator, e.g. `Get-ChildItem > out.txt` because PowerShell added `-Encoding Unicode`.</span></span>

<span data-ttu-id="f71e6-113">WMF 5.1부터 이제 `$PSDefaultParameterValues`를 설정하여 리디렉션의 파일 인코딩을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="f71e6-114">구성원 액세스에서의 회귀 수정 `System.Reflection.TypeInfo`</span><span class="sxs-lookup"><span data-stu-id="f71e6-114">Fixed a regression in accessing members of `System.Reflection.TypeInfo`</span></span>

<span data-ttu-id="f71e6-115">WMF 5.0에 도입된 회귀가 `System.Reflection.RuntimeType`의 구성원(예: `[int].ImplementedInterfaces`) 액세스를 중단시켰습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, e.g. `[int].ImplementedInterfaces`.</span></span>
<span data-ttu-id="f71e6-116">이 버그는 WMF 5.1에서 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-116">This bug has been fixed in WMF 5.1.</span></span>


### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="f71e6-117">COM 개체의 몇 가지 문제 수정</span><span class="sxs-lookup"><span data-stu-id="f71e6-117">Fixed some issues with COM objects</span></span>

<span data-ttu-id="f71e6-118">WMF 5.0에서는 COM 개체에 대한 메서드를 호출하고 COM 개체의 속성에 액세스하는 새로운 COM 바인더를 도입했습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span>
<span data-ttu-id="f71e6-119">이 새 바인더는 성능을 크게 향상했지만 몇 가지 버그도 도입했습니다. 이 버그는 WMF 5.1에서 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="f71e6-120">인수 변환이 올바로 수행되지 않을 수도 있었음</span><span class="sxs-lookup"><span data-stu-id="f71e6-120">Argument conversions were not always performed correctly</span></span>

<span data-ttu-id="f71e6-121">다음 예제에서,</span><span class="sxs-lookup"><span data-stu-id="f71e6-121">In the following example:</span></span>

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="f71e6-122">SendKeys 메서드에는 문자열이 필요하지만 PowerShell은 문자를 문자열로 변환하지 않고 IDispatch::Invoke에서 변환을 수행하게 했습니다. IDispatch::Invoke는 VariantChangeType을 사용하여 변환을 수행하므로 이 예에서는 Volume.Mute 키 대신 '1', '7' 및 '3' 키가 보내졌습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-122">The SendKeys method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to IDispatch::Invoke, which uses VariantChangeType to do the conversion, which in this example resulted in sending the keys '1', '7', and '3' instead of the expected Volume.Mute key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="f71e6-123">열거 가능 COM 개체가 올바로 처리되지 않을 수도 있음</span><span class="sxs-lookup"><span data-stu-id="f71e6-123">Enumerable COM objects not always handled correctly</span></span>

<span data-ttu-id="f71e6-124">PowerShell에서는 대부분의 열거 가능 개체를 정상적으로 열거하지만 WMF 5.0에 도입된 회귀로 인해 IEnumerable을 구현하는 COM 개체가 열거되지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-124">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span>  <span data-ttu-id="f71e6-125">예:</span><span class="sxs-lookup"><span data-stu-id="f71e6-125">For example:</span></span>

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

<span data-ttu-id="f71e6-126">위의 예에서 WMF 5.0은 키/값 쌍을 열거하지 않고 Scripting.Dictionary를 파이프라인에 잘못 썼습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-126">In the above example, WMF 5.0 incorrectly wrote the Scripting.Dictionary to the pipeline instead of enumerating the key/value pairs.</span></span>

<span data-ttu-id="f71e6-127">이 변경으로 [issue 1752224 on Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)(Connect의 문제 1752224)도 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-127">This change also addresses [issue 1752224 on Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="f71e6-128">`[ordered]`는 클래스 내에서 허용되지 않았음</span><span class="sxs-lookup"><span data-stu-id="f71e6-128">`[ordered]` was not allowed inside classes</span></span>

<span data-ttu-id="f71e6-129">WMF 5.0에서는 클래스에 사용된 형식 리터럴의 유효성을 검사하는 클래스를 도입했습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span>
<span data-ttu-id="f71e6-130">`[ordered]`는 형식 리터럴로 보이지만 실제 .NET 형식이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span>
<span data-ttu-id="f71e6-131">WMF 5.0에서는 클래스 내에 있는 `[ordered]`에 대해 오류를 잘못 보고했습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="f71e6-132">여러 버전이 있는 정보 항목에 대한 도움말이 작동하지 않음</span><span class="sxs-lookup"><span data-stu-id="f71e6-132">Help on About topics with multiple versions does not work</span></span>

<span data-ttu-id="f71e6-133">WMF5.5.1 이전에는 모듈의 여러 버전이 설치되어 있고 이들 버전이 모두 about_PSReadline과 같은 하나의 도움말 항목을 공유한 경우 `help about_PSReadline`에서 여러 항목을 반환하므로 실제 도움말을 볼 수 있는 방법이 명확히 없었습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="f71e6-134">WMF 5.1에서는 항목의 최신 버전에 대한 도움말을 반환하여 이 문제를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="f71e6-135">`Get-Help`에서는 도움말이 필요한 버전을 지정하는 방법을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span>
<span data-ttu-id="f71e6-136">이 문제를 해결하려면 모듈 디렉터리로 이동하고 즐겨 사용하는 편집기와 같은 도구에서 직접 도움말을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="f71e6-137">powershell.exe가 STDIN에서 읽기 작동이 중지됨</span><span class="sxs-lookup"><span data-stu-id="f71e6-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="f71e6-138">고객이 네이티브 앱에서 `powershell -command -`를 사용하여 PowerShell을 실행함으로써 STDIN을 통해 스크립트를 전달하는 기능이 아쉽게도 콘솔 호스트의 다른 변경 내용으로 인해 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken due to other changes it the console host.</span></span>

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="f71e6-139">시작 시 powershell.exe의 CPU 사용량이 급증함</span><span class="sxs-lookup"><span data-stu-id="f71e6-139">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="f71e6-140">PowerShell은 로그인에 지연이 발생하지 않도록 WMI 쿼리를 사용하여 그룹 정책을 통해 시작되었는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-140">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span>
<span data-ttu-id="f71e6-141">WMI Win32_Process 클래스는 현지 표준 시간대 정보를 검색하려고 시도하므로 WMI 쿼리는 시스템의 모든 프로세스로 tzres.mui.dll을 삽입하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-141">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI Win32_Process class attempts to retrieve local timezone information.</span></span>
<span data-ttu-id="f71e6-142">따라서 wmiprvse(WMI 공급자 호스트)에서 CPU 사용량이 엄청나게 급증하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-142">This results in a large CPU spike in wmiprvse (the WMI provider host).</span></span>
<span data-ttu-id="f71e6-143">해결 방법은 WMI를 사용하는 대신 Win32 API 호출을 사용하여 같은 정보를 가져오는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f71e6-143">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>
