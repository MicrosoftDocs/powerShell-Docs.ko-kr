---
ms.date: 11/21/2019
ms.topic: reference
title: PowerShell 스크립트 모듈을 작성하는 방법
description: PowerShell 스크립트 모듈을 작성하는 방법
ms.openlocfilehash: c44b09a915501fb10773ab11cf13136d5035ba69
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649146"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="daced-103">PowerShell 스크립트 모듈을 작성하는 방법</span><span class="sxs-lookup"><span data-stu-id="daced-103">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="daced-104">스크립트 모듈은 확장에 저장 된 유효한 PowerShell 스크립트입니다 `.psm1` .</span><span class="sxs-lookup"><span data-stu-id="daced-104">A script module is any valid PowerShell script saved in a `.psm1` extension.</span></span> <span data-ttu-id="daced-105">이 확장을 통해 PowerShell 엔진은 파일에서 규칙 및 모듈 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-105">This extension allows the PowerShell engine to use rules and module cmdlets on your file.</span></span> <span data-ttu-id="daced-106">이러한 기능 중 대부분은 다른 시스템에 코드를 설치 하 고 범위를 관리 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="daced-106">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="daced-107">더 복잡 한 설치 및 솔루션을 설명 하는 모듈 매니페스트 파일을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-107">You can also use a module manifest file, which describes more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="daced-108">PowerShell 스크립트 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="daced-108">Writing a PowerShell script module</span></span>

<span data-ttu-id="daced-109">스크립트 모듈을 만들려면 유효한 PowerShell 스크립트를 파일에 저장 `.psm1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="daced-109">To create a script module, save a valid PowerShell script to a `.psm1` file.</span></span> <span data-ttu-id="daced-110">스크립트와 저장 된 디렉터리는 동일한 이름을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daced-110">The script and the directory where it's stored must use the same name.</span></span> <span data-ttu-id="daced-111">예를 들어 라는 스크립트는 `MyPsScript.psm1` 라는 디렉터리에 저장 됩니다 `MyPsScript` .</span><span class="sxs-lookup"><span data-stu-id="daced-111">For example, a script named `MyPsScript.psm1` is stored in a directory named `MyPsScript`.</span></span>

<span data-ttu-id="daced-112">모듈의 디렉터리는에 지정 된 경로에 있어야 합니다 `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="daced-112">The module's directory needs to be in a path specified in `$env:PSModulePath`.</span></span> <span data-ttu-id="daced-113">모듈의 디렉터리에는 스크립트를 실행 하는 데 필요한 모든 리소스와 모듈 작동 방식을 설명 하는 모듈 매니페스트 파일이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-113">The module's directory can contain any resources that are needed to run the script, and a module manifest file that describes to PowerShell how your module works.</span></span>

## <a name="create-a-basic-powershell-module"></a><span data-ttu-id="daced-114">기본 PowerShell 모듈 만들기</span><span class="sxs-lookup"><span data-stu-id="daced-114">Create a basic PowerShell module</span></span>

<span data-ttu-id="daced-115">다음 단계에서는 PowerShell 모듈을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="daced-115">The following steps describe how to create a PowerShell module.</span></span>

1. <span data-ttu-id="daced-116">확장을 사용 하 여 PowerShell 스크립트를 저장 `.psm1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="daced-116">Save a PowerShell script with a `.psm1` extension.</span></span> <span data-ttu-id="daced-117">스크립트와 스크립트를 저장할 디렉터리에 동일한 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="daced-117">Use the same name for the script and the directory where the script is saved.</span></span>

   <span data-ttu-id="daced-118">확장을 사용 하 여 스크립트를 저장 `.psm1` 하면 모듈 cmdlet (예: [import-module)](/powershell/module/Microsoft.PowerShell.Core/Import-Module)을 사용할 수 있다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="daced-118">Saving a script with the `.psm1` extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span> <span data-ttu-id="daced-119">모듈 cmdlet은 코드를 다른 사용자의 시스템으로 가져오고 내보낼 수 있도록 주로 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="daced-119">The module cmdlets exist primarily so that you can import and export your code onto other user's systems.</span></span> <span data-ttu-id="daced-120">대체 솔루션은 다른 시스템에서 코드를 로드 한 다음 해당 코드를 확장 가능한 솔루션이 아닌 활성 메모리로 로드 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="daced-120">The alternate solution would be to load your code on other systems and then dot-source it into active memory, which isn't a scalable solution.</span></span> <span data-ttu-id="daced-121">자세한 내용은 [Windows PowerShell 모듈 이해](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="daced-121">For more information, see [Understanding a Windows PowerShell Module](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables).</span></span>
   <span data-ttu-id="daced-122">기본적으로 사용자가 `.psm1` 파일을 가져올 때 스크립트의 모든 함수에 액세스할 수 있지만 변수는 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-122">By default, when users import your `.psm1` file, all functions in your script are accessible, but variables aren't.</span></span>

   <span data-ttu-id="daced-123">`Show-Calendar`이 문서의 끝에 있는 예제 PowerShell 스크립트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-123">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this article.</span></span>

   ```powershell
   function Show-Calendar {
   param(
       [DateTime] $start = [DateTime]::Today,
       [DateTime] $end = $start,
       $firstDayOfWeek,
       [int[]] $highlightDay,
       [string[]] $highlightDate = [DateTime]::Today.ToString()
       )

       #actual code for the function goes here see the end of the topic for the complete code sample
   }
   ```

2. <span data-ttu-id="daced-124">특정 함수 또는 변수에 대 한 사용자 액세스를 제어 하려면 스크립트의 끝에서 [export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="daced-124">To control user access to certain functions or variables, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="daced-125">문서의 맨 아래에 있는 예제 코드는 기본적으로 노출 되는 함수를 하나만 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="daced-125">The example code at the bottom of the article has only one function, which by default would be exposed.</span></span> <span data-ttu-id="daced-126">그러나 다음 코드에 설명 된 대로 노출할 함수를 명시적으로 호출 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-126">However, it's recommended you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="daced-127">모듈 매니페스트를 사용 하 여 가져온 항목을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-127">You can restrict what's imported using a module manifest.</span></span> <span data-ttu-id="daced-128">자세한 내용은 [Powershell 모듈 가져오기](./importing-a-powershell-module.md) 및 [powershell 모듈 매니페스트를 작성 하는 방법](./how-to-write-a-powershell-module-manifest.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="daced-128">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="daced-129">사용자 고유의 모듈을 로드 해야 하는 모듈이 있는 경우 `Import-Module` 모듈의 맨 위에 있는를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-129">If you have modules that your own module needs to load, you can use `Import-Module`, at the top of your module.</span></span>

   <span data-ttu-id="daced-130">`Import-Module`Cmdlet은 대상 모듈을 시스템으로 가져오며, 프로시저의 이후 단계에서 사용자 고유의 모듈을 설치 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-130">The `Import-Module` cmdlet imports a targeted module onto a system, and can be used at a later point in the procedure to install your own module.</span></span> <span data-ttu-id="daced-131">이 문서의 맨 아래에 있는 샘플 코드는 가져오기 모듈을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-131">The sample code at the bottom of this article doesn't use any import modules.</span></span> <span data-ttu-id="daced-132">그러나이 경우 다음 코드와 같이 파일의 맨 위에 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="daced-132">But if it did, they would be listed at the top of the file, as shown in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="daced-133">PowerShell 도움말 시스템에 대 한 모듈을 설명 하려면 파일 내에서 표준 도움말 주석을 사용 하거나 추가 도움말 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-133">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="daced-134">이 문서의 맨 아래에 있는 코드 샘플에는 주석에 대 한 도움말 정보가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-134">The code sample at the bottom of this article includes the help information in the comments.</span></span> <span data-ttu-id="daced-135">추가 도움말 콘텐츠를 포함 하는 확장 된 XML 파일을 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-135">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="daced-136">자세한 내용은 [Windows PowerShell 모듈에 대 한 도움말 작성](./writing-help-for-windows-powershell-modules.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="daced-136">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="daced-137">모듈을 사용 하 여 패키지 하려는 추가 모듈, XML 파일 또는 다른 콘텐츠가 있는 경우 모듈 매니페스트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-137">If you have additional modules, XML files, or other content you want to package with your module, you can use a module manifest.</span></span>

   <span data-ttu-id="daced-138">모듈 매니페스트는 다른 모듈의 이름, 디렉터리 레이아웃, 버전 번호, 작성자 데이터 및 기타 정보를 포함 하는 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="daced-138">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="daced-139">PowerShell은 모듈 매니페스트 파일을 사용 하 여 솔루션을 구성 하 고 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="daced-139">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="daced-140">자세한 내용은 [PowerShell 모듈 매니페스트를 작성 하는 방법](./how-to-write-a-powershell-module-manifest.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="daced-140">For more information, see [How to write a PowerShell module manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="daced-141">모듈을 설치 하 고 실행 하려면 모듈을 적절 한 PowerShell 경로 중 하나에 저장 하 고를 사용 `Import-Module` 합니다.</span><span class="sxs-lookup"><span data-stu-id="daced-141">To install and run your module, save the module to one of the appropriate PowerShell paths, and use `Import-Module`.</span></span>

   <span data-ttu-id="daced-142">모듈을 설치할 수 있는 경로는 `$env:PSModulePath` 전역 변수에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-142">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="daced-143">예를 들어 시스템에 모듈을 저장 하는 일반적인 경로는 `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>` 입니다.</span><span class="sxs-lookup"><span data-stu-id="daced-143">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="daced-144">단일 파일 일 지라도 스크립트 모듈과 동일한 이름을 사용 하는 모듈에 대 한 디렉터리를 만들어야 `.psm1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="daced-144">Be sure to create a directory for your module that uses the same name as the script module, even if it's only a single `.psm1` file.</span></span> <span data-ttu-id="daced-145">이러한 경로 중 하나에 모듈을 저장 하지 않은 경우 명령에서 모듈의 위치를 지정 해야 `Import-Module` 합니다.</span><span class="sxs-lookup"><span data-stu-id="daced-145">If you didn't save your module to one of these paths, you would have to specify the module's location in the `Import-Module` command.</span></span> <span data-ttu-id="daced-146">그렇지 않으면 PowerShell이 모듈을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-146">Otherwise, PowerShell wouldn't be able to find the module.</span></span>

   <span data-ttu-id="daced-147">PowerShell 3.0부터 PowerShell 모듈 경로 중 하나에 모듈을 배치한 경우 명시적으로 가져올 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-147">Starting with PowerShell 3.0, if you've placed your module in one of the PowerShell module paths, you don't need to explicitly import it.</span></span> <span data-ttu-id="daced-148">사용자가 함수를 호출 하면 모듈이 자동으로 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="daced-148">Your module is automatically loaded when a user calls your function.</span></span> <span data-ttu-id="daced-149">모듈 경로에 대 한 자세한 내용은 [PowerShell 모듈 가져오기](./importing-a-powershell-module.md) 및 [PSModulePath 설치 경로 수정](./modifying-the-psmodulepath-installation-path.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="daced-149">For more information about the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [Modifying the PSModulePath Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="daced-150">현재 PowerShell 세션의 활성 서비스에서 모듈을 제거 하려면 [모듈 제거](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="daced-150">To remove a module from active service in the current PowerShell session, use [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   > [!NOTE]
   > <span data-ttu-id="daced-151">`Remove-Module` 현재 PowerShell 세션에서 모듈을 제거 하지만 모듈을 제거 하거나 모듈의 파일을 삭제 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-151">`Remove-Module` removes a module from the current PowerShell session, but doesn't uninstall the module or delete the module's files.</span></span>

## <a name="show-calendar-code-example"></a><span data-ttu-id="daced-152">Show-Calendar 코드 예제</span><span class="sxs-lookup"><span data-stu-id="daced-152">Show-Calendar code example</span></span>

<span data-ttu-id="daced-153">다음 예제는 라는 단일 함수를 포함 하는 스크립트 모듈입니다 `Show-Calendar` .</span><span class="sxs-lookup"><span data-stu-id="daced-153">The following example is a script module that contains a single function named `Show-Calendar`.</span></span> <span data-ttu-id="daced-154">이 함수는 달력의 시각적 표시를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="daced-154">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="daced-155">이 샘플에는 개요, 설명, 매개 변수 값 및 코드에 대 한 PowerShell 도움말 문자열이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daced-155">The sample contains the PowerShell Help strings for the synopsis, description, parameter values, and code.</span></span> <span data-ttu-id="daced-156">모듈을 가져올 때 `Export-ModuleMember` 명령은 `Show-Calendar` 함수를 모듈 멤버로 내보내도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="daced-156">When the module is imported, the `Export-ModuleMember` command ensures that the `Show-Calendar` function is exported as a module member.</span></span>

```powershell
<#
 .Synopsis
  Displays a visual representation of a calendar.

 .Description
  Displays a visual representation of a calendar. This function supports multiple months
  and lets you highlight specific date ranges or days.

 .Parameter Start
  The first month to display.

 .Parameter End
  The last month to display.

 .Parameter FirstDayOfWeek
  The day of the month on which the week begins.

 .Parameter HighlightDay
  Specific days (numbered) to highlight. Used for date ranges like (25..31).
  Date ranges are specified by the Windows PowerShell range syntax. These dates are
  enclosed in square brackets.

 .Parameter HighlightDate
  Specific days (named) to highlight. These dates are surrounded by asterisks.

 .Example
   # Show a default display of this month.
   Show-Calendar

 .Example
   # Display a date range.
   Show-Calendar -Start "March, 2010" -End "May, 2010"

 .Example
   # Highlight a range of days.
   Show-Calendar -HighlightDay (1..10 + 22) -HighlightDate "December 25, 2008"
#>
function Show-Calendar {
param(
    [DateTime] $start = [DateTime]::Today,
    [DateTime] $end = $start,
    $firstDayOfWeek,
    [int[]] $highlightDay,
    [string[]] $highlightDate = [DateTime]::Today.ToString()
    )

## Determine the first day of the start and end months.
$start = New-Object DateTime $start.Year,$start.Month,1
$end = New-Object DateTime $end.Year,$end.Month,1

## Convert the highlighted dates into real dates.
[DateTime[]] $highlightDate = [DateTime[]] $highlightDate

## Retrieve the DateTimeFormat information so that the
## calendar can be manipulated.
$dateTimeFormat  = (Get-Culture).DateTimeFormat
if($firstDayOfWeek)
{
    $dateTimeFormat.FirstDayOfWeek = $firstDayOfWeek
}

$currentDay = $start

## Process the requested months.
while($start -le $end)
{
    ## Return to an earlier point in the function if the first day of the month
    ## is in the middle of the week.
    while($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek)
    {
        $currentDay = $currentDay.AddDays(-1)
    }

    ## Prepare to store information about this date range.
    $currentWeek = New-Object PsObject
    $dayNames = @()
    $weeks = @()

    ## Continue processing dates until the function reaches the end of the month.
    ## The function continues until the week is completed with
    ## days from the next month.
    while(($currentDay -lt $start.AddMonths(1)) -or
        ($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek))
    {
        ## Determine the day names to use to label the columns.
        $dayName = "{0:ddd}" -f $currentDay
        if($dayNames -notcontains $dayName)
        {
            $dayNames += $dayName
        }

        ## Pad the day number for display, highlighting if necessary.
        $displayDay = " {0,2} " -f $currentDay.Day

        ## Determine whether to highlight a specific date.
        if($highlightDate)
        {
            $compareDate = New-Object DateTime $currentDay.Year,
                $currentDay.Month,$currentDay.Day
            if($highlightDate -contains $compareDate)
            {
                $displayDay = "*" + ("{0,2}" -f $currentDay.Day) + "*"
            }
        }

        ## Otherwise, highlight as part of a date range.
        if($highlightDay -and ($highlightDay[0] -eq $currentDay.Day))
        {
            $displayDay = "[" + ("{0,2}" -f $currentDay.Day) + "]"
            $null,$highlightDay = $highlightDay
        }

        ## Add the day of the week and the day of the month as note properties.
        $currentWeek | Add-Member NoteProperty $dayName $displayDay

        ## Move to the next day of the month.
        $currentDay = $currentDay.AddDays(1)

        ## If the function reaches the next week, store the current week
        ## in the week list and continue.
        if($currentDay.DayOfWeek -eq $dateTimeFormat.FirstDayOfWeek)
        {
            $weeks += $currentWeek
            $currentWeek = New-Object PsObject
        }
    }

    ## Format the weeks as a table.
    $calendar = $weeks | Format-Table $dayNames -AutoSize | Out-String

    ## Add a centered header.
    $width = ($calendar.Split("`n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " `n" + $padding + $header + "`n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
