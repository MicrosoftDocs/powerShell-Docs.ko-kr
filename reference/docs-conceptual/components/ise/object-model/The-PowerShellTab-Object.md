---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: PowerShellTab 개체
ms.openlocfilehash: bfa11b553f97b7b27b974855ff4e8f1a48c33fea
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67028912"
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="e40ce-103">PowerShellTab 개체</span><span class="sxs-lookup"><span data-stu-id="e40ce-103">The PowerShellTab Object</span></span>

<span data-ttu-id="e40ce-104">**PowerShellTab** 개체는 Windows PowerShell 런타임 환경을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="e40ce-105">메서드</span><span class="sxs-lookup"><span data-stu-id="e40ce-105">Methods</span></span>

### <a name="invoke-script-"></a><span data-ttu-id="e40ce-106">Invoke\( Script \)</span><span class="sxs-lookup"><span data-stu-id="e40ce-106">Invoke\( Script \)</span></span>

<span data-ttu-id="e40ce-107">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e40ce-108">PowerShell 탭에서 지정된 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="e40ce-109">이 메서드는 이 메서드가 실행되는 PowerShell 탭이 아닌, 다른 PowerShell 탭에 대해서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="e40ce-110">개체 또는 값을 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-110">It does not return any object or value.</span></span> <span data-ttu-id="e40ce-111">코드가 어떤 변수든 수정한다면, 해당 변경 내용은 해당 명령이 호출된 탭에서 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

<span data-ttu-id="e40ce-112">**Script** - System.Management.Automation.ScriptBlock 또는 문자열. 실행할 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="e40ce-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="e40ce-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>

<span data-ttu-id="e40ce-114">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e40ce-115">PowerShell 탭에서 지정된 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="e40ce-116">이 메서드는 이 메서드가 실행되는 PowerShell 탭이 아닌, 다른 PowerShell 탭에 대해서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="e40ce-117">스크립트 블록이 실행되고, 스크립트에서 반환되는 모든 값은 명령을 호출한 실행 환경에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="e40ce-118">**millesecondsTimeout** 값이 지정하는 시간보다 명령이 실행되는 데 더 오래 걸린다면 "작업 시간이 초과되었습니다."라는 예외와 함께 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

<span data-ttu-id="e40ce-119">**Script** - System.Management.Automation.ScriptBlock 또는 문자열. 실행할 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

<span data-ttu-id="e40ce-120">**\[useNewScope\]** - 기본적으로 **$true**로 설정되는 선택적 부울. **$true**로 설정된 경우 명령을 실행할 새 범위가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-120">**\[useNewScope\]** -  Optional Boolean that defaults to **$true** If set to **$true**, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="e40ce-121">명령으로 지정되는 PowerShell 탭의 런타임 환경을 수정하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

<span data-ttu-id="e40ce-122">**\[millisecondsTimeout\]** - 기본값이 **500**인 선택적 정수.</span><span class="sxs-lookup"><span data-stu-id="e40ce-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="e40ce-123">이 명령이 지정된 시간 안에 완료되지 않으면 이 명령은 "작업 시간이 초과되었습니다"라는 메시지와 함께 **TimeoutException**을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

```powershell
# Create a new PowerShell tab and then switch back to the first
$psISE.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0])

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1', $false)
# You can switch to the other tab and type '$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope)
# and returns it through the pipeline to this tab to store in $a
$a = $psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z')
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
Measure-Command {$psISE.PowerShellTabs[1].InvokeSynchronous('sleep 10', $false, 5000)}
```

## <a name="properties"></a><span data-ttu-id="e40ce-124">속성</span><span class="sxs-lookup"><span data-stu-id="e40ce-124">Properties</span></span>

### <a name="addonsmenu"></a><span data-ttu-id="e40ce-125">AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="e40ce-125">AddOnsMenu</span></span>

<span data-ttu-id="e40ce-126">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e40ce-127">PowerShell 탭에 대한 추가 기능 메뉴를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

```powershell
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a><span data-ttu-id="e40ce-128">CanInvoke</span><span class="sxs-lookup"><span data-stu-id="e40ce-128">CanInvoke</span></span>

<span data-ttu-id="e40ce-129">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e40ce-130">스크립트를 [Invoke( Script )](#invoke-script-) 메서드로 호출할 수 있으면 **$true** 값을 반환하는 읽기 전용 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-130">The read-only Boolean property that returns a **$true** value if a script can be invoked with the [Invoke( Script )](#invoke-script-) method.</span></span>

```powershell
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab.
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psISE.PowerShellTabs[1]
$secondTab.CanInvoke
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke
```

### <a name="consolepane"></a><span data-ttu-id="e40ce-131">Consolepane</span><span class="sxs-lookup"><span data-stu-id="e40ce-131">Consolepane</span></span>

<span data-ttu-id="e40ce-132">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>  <span data-ttu-id="e40ce-133">Windows PowerShell ISE 2.0에서는 이 속성의 이름이 **CommandPane**이었습니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

<span data-ttu-id="e40ce-134">콘솔 창 [editor](The-ISEEditor-Object.md) 개체를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-134">The read-only property that gets the Console pane [editor](The-ISEEditor-Object.md) object.</span></span>

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a><span data-ttu-id="e40ce-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e40ce-135">DisplayName</span></span>

<span data-ttu-id="e40ce-136">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e40ce-137">PowerShell 탭에 표시되는 텍스트를 가져오거나 설정하는 읽기-쓰기 속성입니다. 기본적으로 탭 이름은 "PowerShell #"이며, 여기서 #은 숫자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab. By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a><span data-ttu-id="e40ce-138">ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="e40ce-138">ExpandedScript</span></span>

<span data-ttu-id="e40ce-139">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-139">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e40ce-140">스크립트 창이 확장 또는 숨겨져 있는지 여부를 결정하는 읽기-쓰기를 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-140">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a><span data-ttu-id="e40ce-141">파일</span><span class="sxs-lookup"><span data-stu-id="e40ce-141">Files</span></span>

<span data-ttu-id="e40ce-142">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-142">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e40ce-143">PowerShell 탭에 열려 있는 [스크립트 파일 컬렉션](The-ISEFileCollection-Object.md)을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-143">The read-only property that gets the [collection of script files](The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a><span data-ttu-id="e40ce-144">출력</span><span class="sxs-lookup"><span data-stu-id="e40ce-144">Output</span></span>

<span data-ttu-id="e40ce-145">이 기능은 Windows PowerShell ISE 2.0에는 있었지만 그 이후 버전의 ISE에서 제거되었거나 이름이 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-145">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="e40ce-146">Windows PowerShell ISE의 이후 버전에서는 동일한 용도로 **ConsolePane** 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-146">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

<span data-ttu-id="e40ce-147">현재 [편집기](The-ISEEditor-Object.md)의 출력 창을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-147">The read-only property that gets the Output pane of the current [editor](The-ISEEditor-Object.md).</span></span>

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a><span data-ttu-id="e40ce-148">Prompt</span><span class="sxs-lookup"><span data-stu-id="e40ce-148">Prompt</span></span>

<span data-ttu-id="e40ce-149">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-149">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e40ce-150">현재 프롬프트 텍스트를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-150">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="e40ce-151">참고: **Prompt** 함수는 사용자 프로필로 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-151">Note: the **Prompt** function can be overridden by the user'™s profile.</span></span> <span data-ttu-id="e40ce-152">결과가 단순 문자열이 아니라면 이 속성은 아무 것도 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-152">If the result is other than a simple string, then this property returns nothing.</span></span>

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a><span data-ttu-id="e40ce-153">ShowCommands</span><span class="sxs-lookup"><span data-stu-id="e40ce-153">ShowCommands</span></span>

<span data-ttu-id="e40ce-154">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e40ce-155">현재 명령 창이 표시되어 있는지 여부를 나타내는 읽기-쓰기 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-155">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a><span data-ttu-id="e40ce-156">StatusText</span><span class="sxs-lookup"><span data-stu-id="e40ce-156">StatusText</span></span>

<span data-ttu-id="e40ce-157">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-157">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e40ce-158">**PowerShellTab** 상태 텍스트를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-158">The read-only property that gets the **PowerShellTab** status text.</span></span>

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a><span data-ttu-id="e40ce-159">HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="e40ce-159">HorizontalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="e40ce-160">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-160">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e40ce-161">가로 추가 기능 도구 창이 현재 열려 있는지 여부를 나타내는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-161">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a><span data-ttu-id="e40ce-162">VerticalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="e40ce-162">VerticalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="e40ce-163">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-163">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e40ce-164">세로 추가 기능 도구 창이 현재 열려 있는지 여부를 나타내는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e40ce-164">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="e40ce-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e40ce-165">See Also</span></span>

- [<span data-ttu-id="e40ce-166">PowerShellTabCollection 개체</span><span class="sxs-lookup"><span data-stu-id="e40ce-166">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md)
- [<span data-ttu-id="e40ce-167">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="e40ce-167">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="e40ce-168">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="e40ce-168">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
