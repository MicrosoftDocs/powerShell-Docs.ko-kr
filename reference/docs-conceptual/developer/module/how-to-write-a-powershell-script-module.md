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
ms.openlocfilehash: b2a929a1724f77f0516ad24cfd90f6d6053ed19e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360692"
---
# <a name="how-to-write-a-powershell-script-module"></a>PowerShell 스크립트 모듈을 작성하는 방법

스크립트 모듈은 기본적으로 .psm1 확장에 저장 된 유효한 PowerShell 스크립트입니다. 이 확장을 통해 PowerShell 엔진은 파일에 여러 규칙과 cmdlet을 사용할 수 있습니다. 이러한 기능 중 대부분은 다른 시스템에 코드를 설치 하 고 범위를 관리 하는 데 도움이 됩니다. 더 복잡 한 설치 및 솔루션을 설명할 수 있는 모듈 매니페스트 파일을 사용할 수도 있습니다.

## <a name="writing-a-powershell-script-module"></a>PowerShell 스크립트 모듈 작성

유효한 PowerShell 스크립트를 .psm1 파일에 저장 한 다음 PowerShell에서 찾을 수 있는 디렉터리에 해당 파일을 저장 하 여 스크립트 모듈을 만듭니다. 이 폴더에는 스크립트를 실행 하는 데 필요한 리소스와 PowerShell의 작동 방식을 설명 하는 매니페스트 파일이 있을 수도 있습니다.

#### <a name="to-create-a-basic-powershell-module"></a>기본 PowerShell 모듈을 만들려면

1. 기존 PowerShell 스크립트를 사용 하 고 .psm1 확장명을 사용 하 여 스크립트를 저장 합니다.

   .Psm1 확장을 사용 하 여 스크립트를 저장 하면 모듈 cmdlet (예: [import-module)](/powershell/module/Microsoft.PowerShell.Core/Import-Module)을 사용할 수 있습니다. 이러한 cmdlet은 주로 코드를 다른 사용자의 시스템으로 쉽게 가져오고 내보낼 수 있도록 하기 위해 존재 합니다. (대체 솔루션은 다른 시스템에서 코드를 로드 한 다음, 해당 코드를 확장 가능한 솔루션이 아닌 활성 메모리로 로드 하는 것입니다.) 자세한 내용은 [Windows PowerShell 모듈](./understanding-a-windows-powershell-module.md) 의 **모듈 cmdlet 및 변수** 섹션을 참조 하세요. 기본적으로 스크립트의 모든 함수는 .psm1 파일을 가져오는 사용자가 액세스할 수 있지만 속성은 사용할 수 없습니다.

   이 항목의 끝에 `Show-Calendar` 이라는 예제 PowerShell 스크립트를 사용할 수 있습니다.

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

2. 특정 기능 또는 속성에 대 한 사용자 액세스를 제어 하려면 스크립트의 끝에서 [export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) 를 호출 합니다.

   페이지 맨 아래에 있는 예제 코드는 기본적으로 노출 되는 함수를 하나만 포함 합니다. 그러나 다음 코드에 설명 된 대로 노출할 함수를 명시적으로 호출 하는 것이 좋습니다.

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   모듈 매니페스트를 사용 하 여 가져올 항목을 제한할 수도 있습니다. 자세한 내용은 [Powershell 모듈 가져오기](./importing-a-powershell-module.md) 및 [powershell 모듈 매니페스트를 작성 하는 방법](./how-to-write-a-powershell-module-manifest.md)을 참조 하세요.

3. 사용자 고유의 모듈을 로드 해야 하는 모듈이 있는 경우 해당 모듈의 맨 위에 있는 `Import-Module`에 대 한 호출과 함께 사용할 수 있습니다.

   `Import-Module`은 대상 모듈을 시스템으로 가져오는 cmdlet입니다. 따라서 사용자 고유의 모듈을 설치 하는 절차의 이후 시점에도 사용 됩니다. 이 페이지의 맨 아래에 있는 샘플 코드는 가져오기 모듈을 사용 하지 않습니다. 그러나 다음 코드에 설명 된 것 처럼 파일의 맨 위에 나열 됩니다.

   ```powershell
   Import-Module GenericModule
   ```

4. PowerShell 도움말 시스템에 대 한 모듈을 설명 하려면 파일 내에서 표준 도움말 주석을 사용 하거나 추가 도움말 파일을 만들 수 있습니다.

   이 항목의 맨 아래에 있는 코드 샘플에는 주석의 도움말 정보가 포함 되어 있습니다. 추가 도움말 콘텐츠를 포함 하는 확장 된 XML 파일을 작성할 수도 있습니다. 자세한 내용은 [Windows PowerShell 모듈에 대 한 도움말 작성](./writing-help-for-windows-powershell-modules.md)을 참조 하세요.

5. 모듈을 사용 하 여 패키징할 추가 모듈, XML 파일 또는 다른 콘텐츠가 있는 경우 모듈 매니페스트를 사용 하 여이 작업을 수행할 수 있습니다.

   모듈 매니페스트는 다른 모듈의 이름, 디렉터리 레이아웃, 버전 번호, 작성자 데이터 및 기타 정보를 포함 하는 파일입니다. PowerShell은 모듈 매니페스트 파일을 사용 하 여 솔루션을 구성 하 고 배포 합니다. 그러나이 예제의 상대적으로 간단한 특성으로 인해 매니페스트 파일은 필요 하지 않습니다. 자세한 내용은 [모듈 매니페스트](./how-to-write-a-powershell-module-manifest.md)를 참조 하세요.

6. 모듈을 설치 하 고 실행 하려면 모듈을 적절 한 PowerShell 경로 중 하나에 저장 하 고 `Import-Module`에 대 한 호출을 수행 합니다.

   모듈을 설치할 수 있는 경로는 `$env:PSModulePath` 전역 변수에 있습니다. 예를 들어 시스템에 모듈을 저장 하는 일반적인 경로는 `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`입니다. .Psm1 파일만 있는 경우에도 모듈을 포함 하는 폴더를 만들어야 합니다. 이러한 경로 중 하나에 모듈을 저장 하지 않은 경우 `Import-Module`에 대 한 호출에서 모듈의 위치를 전달 해야 합니다. 그렇지 않으면 PowerShell에서 해당 파일을 찾을 수 없습니다. PowerShell 3.0부터 PowerShell 모듈 경로 중 하나에 모듈을 배치한 경우 명시적으로 가져올 필요가 없습니다. 사용자가 함수를 호출 하면 모듈이 자동으로 로드 됩니다.
   모듈 경로에 대 한 자세한 내용은 [PowerShell 모듈](./importing-a-powershell-module.md) 및 [PSModulePath 환경 변수](./modifying-the-psmodulepath-installation-path.md)가져오기를 참조 하세요.

7. 활성 서비스에서 모듈을 제거 하려면 [제거 모듈](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)을 호출 합니다.

   [제거 모듈](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) 은 활성 메모리에서 모듈을 제거 합니다. 모듈 파일을 저장 한 위치에서 실제로 삭제 하지는 않습니다.

### <a name="show-calendar-code-example"></a>표시-일정 코드 예제

다음 예는 `Show-Calendar` 이라는 단일 함수를 포함 하는 간단한 스크립트 모듈입니다.
이 함수는 달력의 시각적 표시를 표시 합니다. 또한이 샘플에는 개요, description, 매개 변수 값 및 예제에 대 한 PowerShell 도움말 문자열이 포함 되어 있습니다. 코드의 마지막 줄은 모듈을 가져올 때 `Show-Calendar` 함수를 모듈 멤버로 내보낼지 확인 합니다.

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