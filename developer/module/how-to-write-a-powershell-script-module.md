---
title: PowerShell 스크립트 모듈을 작성 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: e8b7151538235cdf7183b78aa8df7e596d6bcfd9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859009"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="521c3-102">PowerShell 스크립트 모듈을 작성하는 방법</span><span class="sxs-lookup"><span data-stu-id="521c3-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="521c3-103">스크립트 모듈은 기본적으로 모든 유효한 PowerShell 스크립트를. psm1 확장에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-103">A script module is essentially any valid PowerShell script saved in a .psm1 extension.</span></span> <span data-ttu-id="521c3-104">이 확장 파일에서 다양 한 규칙 및 cmdlet을 사용 하도록 PowerShell 엔진을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-104">This extension allows the PowerShell engine to use a number of rules and cmdlets on your file.</span></span> <span data-ttu-id="521c3-105">대부분의 이러한 기능 범위를 관리 하는 것은 물론 다른 시스템에서 코드를 설치 하는 데는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="521c3-106">또한 좀 더 복잡 한 설치 및 솔루션을 설명할 수 있습니다 하는 모듈 매니페스트 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-106">You can also use a module manifest file, which can describe even more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="521c3-107">PowerShell 스크립트 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="521c3-107">Writing a PowerShell Script Module</span></span>

<span data-ttu-id="521c3-108">. Psm1 파일에 유효한 PowerShell 스크립트를 저장 하 고 다음 PowerShell 찾을 수 있는 위치한 디렉터리에 해당 파일을 저장 하 여 스크립트 모듈을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-108">You create a script module by saving a valid PowerShell script to a .psm1 file, and then saving that file in a directory located where PowerShell can find it.</span></span> <span data-ttu-id="521c3-109">스크립트를 실행 하는 데 필요한 모든 리소스를 배치할 수도 있습니다 해당 폴더에서 매니페스트 파일이 설명 하는 powershell 모듈의 작동 원리입니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-109">In that folder you can also place any resources you need to run your script, as well as a manifest file that describes to PowerShell how your module works.</span></span>

#### <a name="to-create-a-basic-powershell-module"></a><span data-ttu-id="521c3-110">기본 PowerShell 모듈을 만들려면</span><span class="sxs-lookup"><span data-stu-id="521c3-110">To create a basic PowerShell Module</span></span>

1. <span data-ttu-id="521c3-111">기존 PowerShell 스크립트를 가져오고. psm1 확장을 사용 하 여 스크립트를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-111">Take an existing PowerShell script, and save the script with a .psm1 extension.</span></span>

   <span data-ttu-id="521c3-112">확장 저장 합니다. psm1 사용 하 여 스크립트와 같은 모듈 cmdlet을 사용할 수를 의미 [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)에서.</span><span class="sxs-lookup"><span data-stu-id="521c3-112">Saving a script with the .psm1 extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), on it.</span></span> <span data-ttu-id="521c3-113">이러한 cmdlet는 주로 있도록 하면 쉽게 가져오고 내보낼 수 있습니다에 코드를 다른 사용자의 시스템에 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-113">These cmdlets exist primarily so that you can easily import and export your code onto other user's systems.</span></span> <span data-ttu-id="521c3-114">(대체 솔루션 로드 한 후 다른 시스템 도트 소싱 코드 시작 특히 확장 가능한 솔루션이 없는 활성 메모리로 것입니다.) 자세한 내용은 참조는 **변수와 모듈 Cmdlet** 섹션 [Windows PowerShell 모듈](./understanding-a-windows-powershell-module.md) 는 기본적으로 스크립트에서 모든 함수 됩니다. psm1에 가져오기는 사용자에 게 액세스할 수 있습니다 파일을 하지만 속성 수신 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-114">(The alternate solution would be to load up your code on other systems and then dot-source it into active memory, which isn't a particularly scalable solution.) For more information see the **Module Cmdlets and Variables** section in [Windows PowerShell Modules](./understanding-a-windows-powershell-module.md) Note that, by default, all functions in your script will be accessible to users who import your .psm1 file, but properties will not.</span></span>

   <span data-ttu-id="521c3-115">Show-calendar, 자격이 부여 하는 예제 PowerShell 스크립트는이 항목의 끝에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-115">An example PowerShell script, entitled Show-Calendar, is available at the end of this topic.</span></span>

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

2. <span data-ttu-id="521c3-116">특정 함수 또는 속성에 대 한 사용자 액세스를 제어 하려는 경우 호출할 [Export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) 스크립트의 끝입니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-116">If you wish to control user access to certain functions or properties, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="521c3-117">페이지의 맨 아래에 있는 코드 예제는 하나의 함수를 기본적으로 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-117">The example code at the bottom of the page has only one function, which by default would be exposed.</span></span> <span data-ttu-id="521c3-118">그러나 다음 코드에 설명 된 대로, 노출 하려는 함수 아웃 명시적으로 호출 하는 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-118">However, it is recommended that you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="521c3-119">모듈 매니페스트를 사용 하 여 무엇을 가져오나 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-119">You can also restrict what is imported using a module manifest.</span></span> <span data-ttu-id="521c3-120">자세한 내용은 [PowerShell 모듈을 가져오는](./importing-a-powershell-module.md) 하 고 [PowerShell 모듈 매니페스트 작성 방법](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="521c3-120">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="521c3-121">사용자 고유의 모듈을 로드 해야 하는 모듈에 있는 경우에 대 한 호출을 사용 하 여 사용할 수 있습니다 `Import-Module`, 사용자 고유의 모듈의 맨 위에 있는 합니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-121">If you have modules that your own module needs to have loaded, you can use them with a call to `Import-Module`, at the top of your own module.</span></span>

   <span data-ttu-id="521c3-122">`Import-Module` 시스템을 대상으로 지정 된 모듈을 가져오는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-122">`Import-Module` is a cmdlet that imports a targeted module onto a system.</span></span> <span data-ttu-id="521c3-123">따라서도 사용 됩니다 절차에서 나중에 자신만 모듈을 설치 하려면.</span><span class="sxs-lookup"><span data-stu-id="521c3-123">As such, it is also used at a later point in the procedure to install your own module as well.</span></span> <span data-ttu-id="521c3-124">이 페이지의 맨 아래에 샘플 코드 가져오기 모듈을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-124">The sample code at the bottom of this page does not use any import modules.</span></span> <span data-ttu-id="521c3-125">그러나 못해서 하는 경우 다음 코드에 설명 된 대로 파일의 맨 위에 있는 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-125">If it did, however, they would be listed at the top of the file, as described in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="521c3-126">PowerShell 도움말 시스템에 모듈을 설명 하려는 경우 또는 파일 내에서 표준 도움말 주석으로 추가 도움말 파일을 사용 하 여이 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-126">If you want to describe your module to the PowerShell Help system, you can do so either with the standard help comments inside the file, or with an additional Help file.</span></span>

   <span data-ttu-id="521c3-127">이 항목의 맨 아래에 있는 코드 샘플에는 주석이 도움말 정보가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-127">The code sample at the bottom of this topic includes the help information in the comments.</span></span> <span data-ttu-id="521c3-128">따라서 원하는 경우에 추가 도움말 콘텐츠를 포함 하는 확장 된 XML 파일을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-128">If you so choose, you could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="521c3-129">자세한 내용은 [작성에 대 한 Windows PowerShell 모듈 도움말](./writing-help-for-windows-powershell-modules.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-129">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="521c3-130">추가 모듈, XML 파일 또는 모듈을 사용 하 여 패키징하고 하려는 기타 콘텐츠 경우 모듈 매니페스트를 사용 하 여이 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-130">If you have additional modules, XML files, or other content you want to package up with your module, you can do so with a module manifest.</span></span>

   <span data-ttu-id="521c3-131">모듈 매니페스트는 다른 모듈, 디렉터리 레이아웃, 버전 번호, 저자 데이터 및 기타 정보가의 이름이 포함 된 파일.</span><span class="sxs-lookup"><span data-stu-id="521c3-131">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="521c3-132">PowerShell 모듈 매니페스트 파일을 사용 하 여 구성 하 고 솔루션을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-132">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="521c3-133">그러나이 예에서는 비교적 간단한 특성상 매니페스트 파일로 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-133">However, due to the relatively simple nature of this example, a manifest file was not needed.</span></span> <span data-ttu-id="521c3-134">자세한 내용은 [모듈 매니페스트](./how-to-write-a-powershell-module-manifest.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-134">For more information, see [Module Manifests](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="521c3-135">를 설치 및 모듈을 실행 하려면 적절 한 PowerShell 경로 중 하나에 모듈을 저장 하 고 호출할 `Import-Module`합니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-135">To install and run your module, save the module to one of the appropriate PowerShell paths, and make a call to `Import-Module`.</span></span>

   <span data-ttu-id="521c3-136">에 있는 모듈을 설치할 수 있는 경로 `$env:PSModulePath` 전역 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-136">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="521c3-137">예를 들어, 시스템에서 모듈을 저장 하기 위한 일반적인 경로 것 `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`입니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-137">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="521c3-138">단일. psm1 파일만 경우에 존재 하 여 모듈에 대 한 폴더를 만들려고 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-138">Be sure to create a folder for your module to exist in, even if it is only a single .psm1 file.</span></span> <span data-ttu-id="521c3-139">호출에서 모듈의 위치에 전달 해야 이러한 경로 중 하나에 모듈을 저장 하지 않은 경우 `Import-Module`합니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-139">If you did not save your module to one of these paths, you would have to pass in the location of your module in the call to `Import-Module`.</span></span> <span data-ttu-id="521c3-140">(그렇지 않으면 PowerShell 없게 찾을.) PowerShell 3.0부터 모듈의 PowerShell 모듈 경로 중 하나에 배치 했으면, 필요가 없습니다 명시적으로 가져와야 합니다: 함수를 호출 하는 사용자를 단순히 필요는 자동으로 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-140">(Otherwise, PowerShell would not be able to find it.) Starting with PowerShell 3.0, if you have placed your module on one of the PowerShell module paths, you do not need to explicitly import it: simply having a user call your function will automatically load it.</span></span> <span data-ttu-id="521c3-141">모듈 경로에 대 한 자세한 내용은 참조 하세요. [PowerShell 모듈을 가져오는](./importing-a-powershell-module.md) 하 고 [PSModulePath 환경 변수](./modifying-the-psmodulepath-installation-path.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-141">For more information on the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [PSModulePath Environment Variable](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="521c3-142">활성 서비스에서 모듈을 제거 하려면 호출할 [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)합니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-142">To remove a module from active service, make a call to [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

<span data-ttu-id="521c3-143">사실은 [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) 모듈 제거-활성 메모리에서 삭제 되지 않습니다 실제로 해당 모듈 파일을 저장 한 위치에서.</span><span class="sxs-lookup"><span data-stu-id="521c3-143">Note that [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) removes your module from active memory - it does not actually delete it from where you saved the module files.</span></span>

### <a name="show-calendar-code-example"></a><span data-ttu-id="521c3-144">Show-calendar 코드 예제</span><span class="sxs-lookup"><span data-stu-id="521c3-144">Show-Calendar code example</span></span>

<span data-ttu-id="521c3-145">다음 예제 Show-calendar 라는 단일 함수를 포함 하는 간단한 스크립트 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-145">The following example is a simple script module that contains a single function named Show-Calendar.</span></span> <span data-ttu-id="521c3-146">이 함수는 달력의 시각적 표현을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-146">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="521c3-147">또한 샘플 개요, 설명, 매개 변수 값 및 예제에 대 한 PowerShell 도움말 문자열을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-147">In addition, the sample contains the PowerShell Help strings for the synopsis, description, parameter values, and example.</span></span> <span data-ttu-id="521c3-148">코드의 마지막 줄은 모듈을 가져올 때 Show-calendar 함수 모듈 구성원으로 내보낼 수 있다고 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="521c3-148">Note that the last line of code indicates that the Show-Calendar function will be exported as a module member when the module is imported.</span></span>

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
    $width = ($calendar.Split("'n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " 'n" + $padding + $header + "'n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
