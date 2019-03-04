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
# <a name="how-to-write-a-powershell-script-module"></a>PowerShell 스크립트 모듈을 작성하는 방법

스크립트 모듈은 기본적으로 모든 유효한 PowerShell 스크립트를. psm1 확장에 저장 합니다. 이 확장 파일에서 다양 한 규칙 및 cmdlet을 사용 하도록 PowerShell 엔진을 사용 합니다. 대부분의 이러한 기능 범위를 관리 하는 것은 물론 다른 시스템에서 코드를 설치 하는 데는 것입니다. 또한 좀 더 복잡 한 설치 및 솔루션을 설명할 수 있습니다 하는 모듈 매니페스트 파일을 사용할 수 있습니다.

## <a name="writing-a-powershell-script-module"></a>PowerShell 스크립트 모듈 작성

. Psm1 파일에 유효한 PowerShell 스크립트를 저장 하 고 다음 PowerShell 찾을 수 있는 위치한 디렉터리에 해당 파일을 저장 하 여 스크립트 모듈을 만듭니다. 스크립트를 실행 하는 데 필요한 모든 리소스를 배치할 수도 있습니다 해당 폴더에서 매니페스트 파일이 설명 하는 powershell 모듈의 작동 원리입니다.

#### <a name="to-create-a-basic-powershell-module"></a>기본 PowerShell 모듈을 만들려면

1. 기존 PowerShell 스크립트를 가져오고. psm1 확장을 사용 하 여 스크립트를 저장 합니다.

   확장 저장 합니다. psm1 사용 하 여 스크립트와 같은 모듈 cmdlet을 사용할 수를 의미 [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)에서. 이러한 cmdlet는 주로 있도록 하면 쉽게 가져오고 내보낼 수 있습니다에 코드를 다른 사용자의 시스템에 존재 합니다. (대체 솔루션 로드 한 후 다른 시스템 도트 소싱 코드 시작 특히 확장 가능한 솔루션이 없는 활성 메모리로 것입니다.) 자세한 내용은 참조는 **변수와 모듈 Cmdlet** 섹션 [Windows PowerShell 모듈](./understanding-a-windows-powershell-module.md) 는 기본적으로 스크립트에서 모든 함수 됩니다. psm1에 가져오기는 사용자에 게 액세스할 수 있습니다 파일을 하지만 속성 수신 되지 않습니다.

   Show-calendar, 자격이 부여 하는 예제 PowerShell 스크립트는이 항목의 끝에서 제공 됩니다.

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

2. 특정 함수 또는 속성에 대 한 사용자 액세스를 제어 하려는 경우 호출할 [Export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) 스크립트의 끝입니다.

   페이지의 맨 아래에 있는 코드 예제는 하나의 함수를 기본적으로 노출 됩니다. 그러나 다음 코드에 설명 된 대로, 노출 하려는 함수 아웃 명시적으로 호출 하는 하는 것이 좋습니다.

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   모듈 매니페스트를 사용 하 여 무엇을 가져오나 제한할 수 있습니다. 자세한 내용은 [PowerShell 모듈을 가져오는](./importing-a-powershell-module.md) 하 고 [PowerShell 모듈 매니페스트 작성 방법](./how-to-write-a-powershell-module-manifest.md).

3. 사용자 고유의 모듈을 로드 해야 하는 모듈에 있는 경우에 대 한 호출을 사용 하 여 사용할 수 있습니다 `Import-Module`, 사용자 고유의 모듈의 맨 위에 있는 합니다.

   `Import-Module` 시스템을 대상으로 지정 된 모듈을 가져오는 cmdlet입니다. 따라서도 사용 됩니다 절차에서 나중에 자신만 모듈을 설치 하려면. 이 페이지의 맨 아래에 샘플 코드 가져오기 모듈을 사용 하지 않습니다. 그러나 못해서 하는 경우 다음 코드에 설명 된 대로 파일의 맨 위에 있는 나열 됩니다.

   ```powershell
   Import-Module GenericModule
   ```

4. PowerShell 도움말 시스템에 모듈을 설명 하려는 경우 또는 파일 내에서 표준 도움말 주석으로 추가 도움말 파일을 사용 하 여이 수행할 수 있습니다.

   이 항목의 맨 아래에 있는 코드 샘플에는 주석이 도움말 정보가 포함 됩니다. 따라서 원하는 경우에 추가 도움말 콘텐츠를 포함 하는 확장 된 XML 파일을 작성할 수 있습니다. 자세한 내용은 [작성에 대 한 Windows PowerShell 모듈 도움말](./writing-help-for-windows-powershell-modules.md)합니다.

5. 추가 모듈, XML 파일 또는 모듈을 사용 하 여 패키징하고 하려는 기타 콘텐츠 경우 모듈 매니페스트를 사용 하 여이 수행할 수 있습니다.

   모듈 매니페스트는 다른 모듈, 디렉터리 레이아웃, 버전 번호, 저자 데이터 및 기타 정보가의 이름이 포함 된 파일. PowerShell 모듈 매니페스트 파일을 사용 하 여 구성 하 고 솔루션을 배포 합니다. 그러나이 예에서는 비교적 간단한 특성상 매니페스트 파일로 필요 하지 않습니다. 자세한 내용은 [모듈 매니페스트](./how-to-write-a-powershell-module-manifest.md)합니다.

6. 를 설치 및 모듈을 실행 하려면 적절 한 PowerShell 경로 중 하나에 모듈을 저장 하 고 호출할 `Import-Module`합니다.

   에 있는 모듈을 설치할 수 있는 경로 `$env:PSModulePath` 전역 변수입니다. 예를 들어, 시스템에서 모듈을 저장 하기 위한 일반적인 경로 것 `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`입니다. 단일. psm1 파일만 경우에 존재 하 여 모듈에 대 한 폴더를 만들려고 해야 합니다. 호출에서 모듈의 위치에 전달 해야 이러한 경로 중 하나에 모듈을 저장 하지 않은 경우 `Import-Module`합니다. (그렇지 않으면 PowerShell 없게 찾을.) PowerShell 3.0부터 모듈의 PowerShell 모듈 경로 중 하나에 배치 했으면, 필요가 없습니다 명시적으로 가져와야 합니다: 함수를 호출 하는 사용자를 단순히 필요는 자동으로 로드 합니다. 모듈 경로에 대 한 자세한 내용은 참조 하세요. [PowerShell 모듈을 가져오는](./importing-a-powershell-module.md) 하 고 [PSModulePath 환경 변수](./modifying-the-psmodulepath-installation-path.md)합니다.

7. 활성 서비스에서 모듈을 제거 하려면 호출할 [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)합니다.

사실은 [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) 모듈 제거-활성 메모리에서 삭제 되지 않습니다 실제로 해당 모듈 파일을 저장 한 위치에서.

### <a name="show-calendar-code-example"></a>Show-calendar 코드 예제

다음 예제 Show-calendar 라는 단일 함수를 포함 하는 간단한 스크립트 모듈입니다. 이 함수는 달력의 시각적 표현을 표시합니다. 또한 샘플 개요, 설명, 매개 변수 값 및 예제에 대 한 PowerShell 도움말 문자열을 포함합니다. 코드의 마지막 줄은 모듈을 가져올 때 Show-calendar 함수 모듈 구성원으로 내보낼 수 있다고 note 합니다.

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
