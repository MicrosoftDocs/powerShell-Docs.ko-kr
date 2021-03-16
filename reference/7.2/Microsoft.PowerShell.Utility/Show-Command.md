---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/29/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Command
ms.openlocfilehash: 87bdd5a9610267b8fce9e391431d24872a77e2de
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600642"
---
# <span data-ttu-id="af3e3-102">Show-Command</span><span class="sxs-lookup"><span data-stu-id="af3e3-102">Show-Command</span></span>

## <span data-ttu-id="af3e3-103">개요</span><span class="sxs-lookup"><span data-stu-id="af3e3-103">SYNOPSIS</span></span>
<span data-ttu-id="af3e3-104">그래픽 창에 PowerShell 명령 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-104">Displays PowerShell command information in a graphical window.</span></span>

## <span data-ttu-id="af3e3-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="af3e3-105">SYNTAX</span></span>

```
Show-Command [[-Name] <String>] [-Height <Double>] [-Width <Double>] [-NoCommonParameter]
 [-ErrorPopup] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="af3e3-106">설명</span><span class="sxs-lookup"><span data-stu-id="af3e3-106">DESCRIPTION</span></span>

<span data-ttu-id="af3e3-107">`Show-Command`Cmdlet을 사용 하 여 명령 창에서 PowerShell 명령을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-107">The `Show-Command` cmdlet lets you create a PowerShell command in a command window.</span></span> <span data-ttu-id="af3e3-108">명령 창의 기능을 사용하여 명령을 실행하거나 해당 명령이 반환되도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-108">You can use the features of the command window to run the command or have it return the command to you.</span></span>

<span data-ttu-id="af3e3-109">`Show-Command` 는 매우 유용한 교육 및 학습 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-109">`Show-Command` is a very useful teaching and learning tool.</span></span> <span data-ttu-id="af3e3-110">`Show-Command` cmdlet, 함수, 워크플로 및 CIM 명령을 비롯 한 모든 명령 유형에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-110">`Show-Command` works on all command types, including cmdlets, functions, workflows and CIM commands.</span></span>

<span data-ttu-id="af3e3-111">매개 변수가 없으면 `Show-Command` 설치 된 모든 모듈에서 사용할 수 있는 모든 명령을 나열 하는 명령 창을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-111">Without parameters, `Show-Command` displays a command window that lists all available commands in all installed modules.</span></span> <span data-ttu-id="af3e3-112">모듈의 명령을 찾으려면 모듈 드롭다운 목록에서 원하는 모듈을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-112">To find the commands in a module, select the module from the Modules drop-down list.</span></span> <span data-ttu-id="af3e3-113">명령을 선택하려면 명령 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-113">To select a command, click the command name.</span></span>

<span data-ttu-id="af3e3-114">명령 창을 사용 하려면 이름을 사용 하거나 **명령 목록에서** 명령 이름을 클릭 하 여 명령을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-114">To use the command window, select a command, either by using the Name or by clicking the command name in the **Commands** list.</span></span> <span data-ttu-id="af3e3-115">각 매개 변수 집합은 별도의 탭에 표시 됩니다. 별표는 필수 매개 변수를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-115">Each parameter set is displayed on a separate tab. Asterisks indicate the mandatory parameters.</span></span> <span data-ttu-id="af3e3-116">매개 변수 값을 입력하려면 텍스트 상자에 값을 입력하거나 드롭다운 상자에서 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-116">To enter values for a parameter, type the value in the text box or select the value from the drop-down box.</span></span> <span data-ttu-id="af3e3-117">스위치 매개 변수를 추가하려면 매개 변수를 확인란을 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-117">To add a switch parameter, click to select the parameter check box.</span></span>

<span data-ttu-id="af3e3-118">준비되면 **Copy** 를 클릭하여 생성된 명령을 클립보드에 복사하거나 **Run** 을 클릭하여 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-118">When you're ready, you can click **Copy** to copy the command that you've created to the clipboard or click **Run** to run the command.</span></span> <span data-ttu-id="af3e3-119">**PassThru** 매개 변수를 사용 하 여 PowerShell 콘솔과 같은 호스트 프로그램에 명령을 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-119">You can also use the **PassThru** parameter to return the command to the host program, such as the PowerShell console.</span></span> <span data-ttu-id="af3e3-120">명령 선택을 취소 하 고 모든 명령을 표시 하는 뷰로 돌아가려면 Ctrl 키를 누르고 선택한 명령을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-120">To cancel the command selection and return to the view that displays all commands, press Ctrl and click the selected command.</span></span>

<span data-ttu-id="af3e3-121">PowerShell ISE (통합 스크립팅 환경)에서는 `Show-Command` 기본적으로 창의 변형이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-121">In the PowerShell Integrated Scripting Environment (ISE), a variation of the `Show-Command` window is displayed by default.</span></span> <span data-ttu-id="af3e3-122">이 명령 창을 사용 하는 방법에 대 한 자세한 내용은 PowerShell ISE 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="af3e3-122">For information about using this command window, see the PowerShell ISE Help topics.</span></span>

<span data-ttu-id="af3e3-123">이 cmdlet은 PowerShell 7에서 다시 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-123">This cmdlet was reintroduced in PowerShell 7.</span></span>

<span data-ttu-id="af3e3-124">이 cmdlet은 사용자 인터페이스를 필요로 하기 때문에 Windows Server Core 또는 Windows Nano Server에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-124">Because this cmdlet requires a user interface, it does not work on Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="af3e3-125">이 cmdlet은 Windows 데스크톱을 지 원하는 Windows 시스템 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-125">This cmdlet is only available on Windows systems that support the Windows Desktop.</span></span>

## <span data-ttu-id="af3e3-126">예제</span><span class="sxs-lookup"><span data-stu-id="af3e3-126">EXAMPLES</span></span>

### <span data-ttu-id="af3e3-127">예제 1: 명령 창 열기</span><span class="sxs-lookup"><span data-stu-id="af3e3-127">Example 1: Open the Commands window</span></span>

<span data-ttu-id="af3e3-128">이 예에서는 창의 기본 뷰를 표시 합니다 `Show-Command` .</span><span class="sxs-lookup"><span data-stu-id="af3e3-128">This example displays the default view of the `Show-Command` window.</span></span> <span data-ttu-id="af3e3-129">**명령** 창에는 컴퓨터에 설치 된 모든 모듈의 모든 명령 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-129">The **Commands** window displays a list of all commands in all modules that are installed on the computer.</span></span>

```powershell
Show-Command
```

### <span data-ttu-id="af3e3-130">예제 2: 명령 창에서 cmdlet 열기</span><span class="sxs-lookup"><span data-stu-id="af3e3-130">Example 2: Open a cmdlet in the Commands window</span></span>

<span data-ttu-id="af3e3-131">이 예에서는 `Invoke-Command` **명령** 창에 cmdlet을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-131">This example display the `Invoke-Command` cmdlet in the **Command** window.</span></span> <span data-ttu-id="af3e3-132">이 표시를 사용 하 여 명령을 실행할 수 있습니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="af3e3-132">You can use this display to run `Invoke-Command` commands.</span></span>

```powershell
Show-Command -Name "Invoke-Command"
```

### <span data-ttu-id="af3e3-133">예제 3: 지정 된 매개 변수를 사용 하 여 cmdlet 열기</span><span class="sxs-lookup"><span data-stu-id="af3e3-133">Example 3: Open a cmdlet with specified parameters</span></span>

<span data-ttu-id="af3e3-134">이 명령은 `Show-Command` cmdlet에 대 한 창을 엽니다 `Connect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="af3e3-134">This command opens a `Show-Command` window for the`Connect-PSSession`cmdlet.</span></span>

```powershell
Show-Command -Name "Connect-PSSession" -Height 700 -Width 1000 -ErrorPopup
```

<span data-ttu-id="af3e3-135">**Height** 및 **Width** 매개 변수는 명령 창의 차원을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-135">The **Height** and **Width** parameters specify the dimension of the command window.</span></span> <span data-ttu-id="af3e3-136">**Errorpopup** 매개 변수는 오류 명령 창을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-136">The **ErrorPopup** parameter displays the error command window.</span></span>

<span data-ttu-id="af3e3-137">**실행** 을 클릭 하면 명령줄 `Connect-PSSession` 에서 명령을 입력 하는 것과 마찬가지로 명령이 실행 됩니다 `Connect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="af3e3-137">When you click **Run**, the `Connect-PSSession` command runs, just as would if you typed the `Connect-PSSession` command at the command line.</span></span>

### <span data-ttu-id="af3e3-138">예제 4: cmdlet에 대 한 새로운 기본 매개 변수 값 지정</span><span class="sxs-lookup"><span data-stu-id="af3e3-138">Example 4: Specify new default parameter values for a cmdlet</span></span>

<span data-ttu-id="af3e3-139">이 예에서는 `$PSDefaultParameterValues` 자동 변수를 사용 하 여 cmdlet의 **Height**, **Width** 및 **errorpopup** 매개 변수에 대 한 새 기본값을 설정 합니다 `Show-Command` .</span><span class="sxs-lookup"><span data-stu-id="af3e3-139">This example uses the `$PSDefaultParameterValues` automatic variable to set new default values for the **Height**, **Width**, and **ErrorPopup** parameters of the `Show-Command` cmdlet.</span></span>

```powershell
$PSDefaultParameterValues = @{
    "Show-Command:Height" = 700
    "Show-Command:Width" = 1000
    "Show-Command:ErrorPopup" = $True
}
```

<span data-ttu-id="af3e3-140">이제 명령을 실행 하면 `Show-Command` 새 기본값이 자동으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-140">Now when you run a `Show-Command` command, the new defaults are applied automatically.</span></span> <span data-ttu-id="af3e3-141">모든 PowerShell 세션에서 이러한 기본값을 사용 하려면 `$PSDefaultParameterValues` powershell 프로필에 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-141">To use these default values in every PowerShell session, add the `$PSDefaultParameterValues` variable to your PowerShell profile.</span></span> <span data-ttu-id="af3e3-142">자세한 내용은 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) 및 [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="af3e3-142">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) and [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md).</span></span>

### <span data-ttu-id="af3e3-143">예 5: 표 뷰로 출력 보내기</span><span class="sxs-lookup"><span data-stu-id="af3e3-143">Example 5: Send output to a grid view</span></span>

<span data-ttu-id="af3e3-144">이 명령은 및 cmdlet을 함께 사용 하는 방법을 보여 줍니다 `Show-Command` `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="af3e3-144">This command shows how to use the `Show-Command` and `Out-GridView` cmdlets together.</span></span>

```powershell
Show-Command Get-ChildItem | Out-GridView
```

<span data-ttu-id="af3e3-145">이 명령은 cmdlet을 사용 하 여 `Show-Command` cmdlet에 대 한 명령 창을 엽니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="af3e3-145">The command uses the `Show-Command` cmdlet to open a command window for the`Get-ChildItem`cmdlet.</span></span>
<span data-ttu-id="af3e3-146">**실행** 단추를 클릭 하면 `Get-ChildItem` 명령이 실행 되 고 출력이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-146">When you click the **Run** button, the `Get-ChildItem` command runs and generates output.</span></span> <span data-ttu-id="af3e3-147">파이프라인 연산자 (|)가 `Get-ChildItem` cmdlet으로 명령의 출력을 보냅니다 `Out-GridView` .이 cmdlet은 `Get-ChildItem` 대화형 창에 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-147">The pipeline operator ( | ) sends the output of the `Get-ChildItem` command to the `Out-GridView` cmdlet, which displays the `Get-ChildItem` output in an interactive window.</span></span>

### <span data-ttu-id="af3e3-148">예제 6: 명령 창에서 만든 명령 표시</span><span class="sxs-lookup"><span data-stu-id="af3e3-148">Example 6: Display a command that you create in the Commands window</span></span>

<span data-ttu-id="af3e3-149">이 예에서는 창에서 만든 명령을 보여 줍니다 `Show-Command` .</span><span class="sxs-lookup"><span data-stu-id="af3e3-149">This example shows the command that you created in the `Show-Command` window.</span></span> <span data-ttu-id="af3e3-150">이 명령은 **PassThru** 매개 변수를 사용 하 여 결과를 문자열로 반환 합니다 `Show-Command` .</span><span class="sxs-lookup"><span data-stu-id="af3e3-150">The command uses the **PassThru** parameter, which returns the `Show-Command` results in a string.</span></span>

```powershell
Show-Command -PassThru
```

```Output
Get-EventLog -LogName "Windows PowerShell" -Newest 5
```

<span data-ttu-id="af3e3-151">예를 들어 `Show-Command` `Get-EventLog` Windows PowerShell 이벤트 로그에 있는 5 개의 최신 이벤트를 가져오는 명령을 만든 다음 **확인** 을 클릭 하면이 명령은 위에 표시 된 출력을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-151">For example, if you use the `Show-Command` window to create a `Get-EventLog` command that gets the five newest events in the Windows PowerShell event log, and then click **OK**, the command returns the output shown above.</span></span> <span data-ttu-id="af3e3-152">명령 문자열을 보면 PowerShell을 배우는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-152">Viewing the command string helps you learn PowerShell.</span></span>

### <span data-ttu-id="af3e3-153">예 7: 변수에 명령 저장</span><span class="sxs-lookup"><span data-stu-id="af3e3-153">Example 7: Save a command to a variable</span></span>

<span data-ttu-id="af3e3-154">이 예에서는 cmdlet의 **PassThru** 매개 변수를 사용할 때 가져오는 명령 문자열을 실행 하는 방법을 보여 줍니다 `Show-Command` .</span><span class="sxs-lookup"><span data-stu-id="af3e3-154">This example shows how to run the command string that you get when you use the **PassThru** parameter of the `Show-Command` cmdlet.</span></span> <span data-ttu-id="af3e3-155">이 전략을 사용하면 명령을 보고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-155">This strategy lets you see the command and use it.</span></span>

```powershell
$C = Show-Command -PassThru
$C
Invoke-Expression $C
```

```Output
Get-EventLog -LogName "PowerShell" -Newest 5

Index Time          EntryType   Source                 InstanceID Message
----- ----          ---------   ------                 ---------- -------
11520 Dec 16 16:37  Information Windows PowerShell            400 Engine state is changed from None to Available...
11519 Dec 16 16:37  Information Windows PowerShell            600 Provider "Variable" is Started. ...
11518 Dec 16 16:37  Information Windows PowerShell            600 Provider "Registry" is Started. ...
11517 Dec 16 16:37  Information Windows PowerShell            600 Provider "Function" is Started. ...
11516 Dec 16 16:37  Information Windows PowerShell            600 Provider "FileSystem" is Started. ...
```

<span data-ttu-id="af3e3-156">첫 번째 명령은 cmdlet의 **PassThru** 매개 변수를 사용 하 여 `Show-Command` 명령 결과를 변수에 저장 합니다 `$C` .</span><span class="sxs-lookup"><span data-stu-id="af3e3-156">The first command uses the **PassThru** parameter of the `Show-Command` cmdlet and saves the results of the command in the `$C` variable.</span></span> <span data-ttu-id="af3e3-157">이 경우 `Show-Command` `Get-EventLog` Windows PowerShell 이벤트 로그에 있는 5 개의 최신 이벤트를 가져오는 명령을 만드는 데 창을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-157">In this case, we use the `Show-Command` window to create a `Get-EventLog` command that gets the five newest events in the Windows PowerShell event log.</span></span> <span data-ttu-id="af3e3-158">**확인** 을 클릭 하면에서 `Show-Command` 변수에 저장 되는 명령 문자열을 반환 `$C` 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-158">When you click **OK**, `Show-Command` returns the command string, which is saved in the `$C` variable.</span></span>

### <span data-ttu-id="af3e3-159">예 8: 명령의 출력을 변수에 저장</span><span class="sxs-lookup"><span data-stu-id="af3e3-159">Example 8: Save the output of a command to a variable</span></span>

<span data-ttu-id="af3e3-160">이 예에서는 **Errorpopup** 매개 변수를 사용 하 여 명령의 출력을 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-160">This example uses the **ErrorPopup** parameter to save the output of a command in a variable.</span></span>

```powershell
$P = Show-Command Get-Process -ErrorPopup
$P
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    473      33    94096     112532   709     2.06   4492 powershell
```

<span data-ttu-id="af3e3-161">창에서 오류를 표시할 수 있을 뿐 아니라 **ErrorPopup** 은 새 명령을 만들지 않고 명령 출력을 현재 명령에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-161">In addition to displaying errors in a window, **ErrorPopup** returns command output to the current command, instead of creating a new command.</span></span> <span data-ttu-id="af3e3-162">이 명령을 실행 하면 `Show-Command` 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-162">When you run this command, the `Show-Command` window opens.</span></span> <span data-ttu-id="af3e3-163">창 기능을 사용하여 매개 변수 값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-163">You can use the window features to set parameter values.</span></span> <span data-ttu-id="af3e3-164">명령을 실행 하려면 창에서 **실행** 단추를 클릭 합니다 `Show-Command` .</span><span class="sxs-lookup"><span data-stu-id="af3e3-164">To run the command, click the **Run** button in the `Show-Command` window.</span></span>

## <span data-ttu-id="af3e3-165">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="af3e3-165">PARAMETERS</span></span>

### <span data-ttu-id="af3e3-166">-ErrorPopup</span><span class="sxs-lookup"><span data-stu-id="af3e3-166">-ErrorPopup</span></span>

<span data-ttu-id="af3e3-167">Cmdlet이 명령줄에 표시 하는 것 외에도 팝업 창에 오류를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-167">Indicates that the cmdlet displays errors in a pop-up window, in addition to displaying them at the command line.</span></span> <span data-ttu-id="af3e3-168">기본적으로 창에서 실행 되는 명령을 실행 하면 오류가 발생 하는 경우 `Show-Command` 명령줄 에서만 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-168">By default, when a command that is run in a `Show-Command` window generates an error, the error is displayed only at the command line.</span></span>

<span data-ttu-id="af3e3-169">또한 창에서 **실행** 단추를 사용 하 여 명령을 실행 하는 경우 `Show-Command` **errorpopup** 매개 변수는 명령을 실행 하 고 해당 출력을 새 명령으로 반환 하는 대신 명령 결과를 현재 명령으로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-169">Also, when you run the command (by using the **Run** button in the `Show-Command` window), the **ErrorPopup** parameter returns the command results to the current command, instead of running the command and returning its output to a new command.</span></span> <span data-ttu-id="af3e3-170">이 기능을 사용하여 명령 결과를 변수에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-170">You can use this feature to save the command results in a variable.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af3e3-171">-높이</span><span class="sxs-lookup"><span data-stu-id="af3e3-171">-Height</span></span>

<span data-ttu-id="af3e3-172">`Show-Command`창의 높이 (픽셀)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-172">Specifies the height of the `Show-Command` window in pixels.</span></span> <span data-ttu-id="af3e3-173">300과 화면 해상도의 픽셀 수 사이의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-173">Enter a value between 300 and the number of pixels in the screen resolution.</span></span> <span data-ttu-id="af3e3-174">값이 너무 커서 화면에 명령 창을 표시할 수 없는 경우에서 오류를 `Show-Command` 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-174">If the value is too large to display the command window on the screen, `Show-Command` generates an error.</span></span> <span data-ttu-id="af3e3-175">기본 높이는 600픽셀입니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-175">The default height is 600 pixels.</span></span> <span data-ttu-id="af3e3-176">`Show-Command` **Name** 매개 변수를 포함 하는 명령의 경우 기본 높이는 300 픽셀입니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-176">For a `Show-Command` command that includes the **Name** parameter, the default height is 300 pixels.</span></span>

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af3e3-177">-Name</span><span class="sxs-lookup"><span data-stu-id="af3e3-177">-Name</span></span>

<span data-ttu-id="af3e3-178">지정된 명령에 대한 명령 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-178">Displays a command window for the specified command.</span></span> <span data-ttu-id="af3e3-179">한 명령의 이름 (예: cmdlet, 함수 또는 CIM 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-179">Enter the name of one command, such as the name of a cmdlet, function, or CIM command.</span></span> <span data-ttu-id="af3e3-180">이 매개 변수를 생략 하면는 `Show-Command` 컴퓨터에 설치 된 모든 모듈의 모든 PowerShell 명령을 나열 하는 명령 창을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-180">If you omit this parameter, `Show-Command` displays a command window that lists all of the PowerShell commands in all modules installed on the computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CommandName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af3e3-181">-NoCommonParameter</span><span class="sxs-lookup"><span data-stu-id="af3e3-181">-NoCommonParameter</span></span>

<span data-ttu-id="af3e3-182">이 cmdlet이 명령 표시의 일반 매개 변수 섹션을 생략 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-182">Indicates that this cmdlet omits the Common Parameters section of the command display.</span></span> <span data-ttu-id="af3e3-183">기본적으로 일반 매개 변수는 명령 창의 맨 아래에 있는 확장 가능한 섹션에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-183">By default, the Common Parameters appear in an expandable section at the bottom of the command window.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af3e3-184">-PassThru</span><span class="sxs-lookup"><span data-stu-id="af3e3-184">-PassThru</span></span>

<span data-ttu-id="af3e3-185">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-185">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="af3e3-186">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-186">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="af3e3-187">명령 문자열을 실행 하려면 명령 프롬프트에서 해당 문자열을 복사 하 여 붙여넣고 변수에 저장 한 다음 cmdlet을 사용 `Invoke-Expression` 하 여 변수에 문자열을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-187">To run the command string, copy and paste it at the command prompt or save it in a variable and use the `Invoke-Expression` cmdlet to run the string in the variable.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af3e3-188">-너비</span><span class="sxs-lookup"><span data-stu-id="af3e3-188">-Width</span></span>

<span data-ttu-id="af3e3-189">`Show-Command`창의 너비 (픽셀)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-189">Specifies the width of the `Show-Command` window in pixels.</span></span> <span data-ttu-id="af3e3-190">300과 화면 해상도의 픽셀 수 사이의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-190">Enter a value between 300 and the number of pixels in the screen resolution.</span></span> <span data-ttu-id="af3e3-191">값이 너무 커서 화면에 명령 창을 표시할 수 없는 경우에서 오류를 `Show-Command` 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-191">If the value is too large to display the command window on the screen, `Show-Command` generates an error.</span></span> <span data-ttu-id="af3e3-192">기본 높이는 300픽셀입니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-192">The default width is 300 pixels.</span></span>

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af3e3-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="af3e3-193">CommonParameters</span></span>

<span data-ttu-id="af3e3-194">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="af3e3-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="af3e3-195">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="af3e3-195">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="af3e3-196">입력</span><span class="sxs-lookup"><span data-stu-id="af3e3-196">INPUTS</span></span>

### <span data-ttu-id="af3e3-197">없음</span><span class="sxs-lookup"><span data-stu-id="af3e3-197">None</span></span>

<span data-ttu-id="af3e3-198">입력을로 파이프 할 수 없습니다 `Show-Command` .</span><span class="sxs-lookup"><span data-stu-id="af3e3-198">You cannot pipe input to `Show-Command`.</span></span>

## <span data-ttu-id="af3e3-199">출력</span><span class="sxs-lookup"><span data-stu-id="af3e3-199">OUTPUTS</span></span>

### <span data-ttu-id="af3e3-200">None, System.string, System.object</span><span class="sxs-lookup"><span data-stu-id="af3e3-200">None, System.String, System.Object</span></span>

<span data-ttu-id="af3e3-201">**PassThru** 매개 변수를 사용 하는 경우는 `Show-Command` 명령 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-201">When you use the **PassThru** parameter, `Show-Command` returns a command string.</span></span> <span data-ttu-id="af3e3-202">**Errorpopup** 매개 변수를 사용 하는 경우 `Show-Command` 명령 출력 (모든 개체)을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-202">When you use the **ErrorPopup** parameter, `Show-Command` returns the command output (any object).</span></span> <span data-ttu-id="af3e3-203">그렇지 않으면에서 `Show-Command` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-203">Otherwise, `Show-Command` does not generate any output.</span></span>

## <span data-ttu-id="af3e3-204">참고</span><span class="sxs-lookup"><span data-stu-id="af3e3-204">NOTES</span></span>

<span data-ttu-id="af3e3-205">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-205">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="af3e3-206">`Show-Command` 는 원격 세션에서 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af3e3-206">`Show-Command` does not work in remote sessions.</span></span>

## <span data-ttu-id="af3e3-207">관련 링크</span><span class="sxs-lookup"><span data-stu-id="af3e3-207">RELATED LINKS</span></span>