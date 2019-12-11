---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 그래픽 날짜 선택 만들기
ms.openlocfilehash: d05445963b41af61a61aa29a425e638d43fb5d9d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030241"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="f2033-103">그래픽 날짜 선택 만들기</span><span class="sxs-lookup"><span data-stu-id="f2033-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="f2033-104">Windows PowerShell 3.0 이상 릴리스를 사용하여 날짜를 선택할 수 있는 그래픽 달력 스타일 컨트롤이 포함된 양식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="f2033-105">그래픽 날짜 선택 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="f2033-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="f2033-106">다음을 복사하여 Windows PowerShell ISE에 붙여넣은 다음 Windows PowerShell 스크립트(.ps1)로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}

$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)

$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="f2033-107">다음 두 .NET Framework 클래스를 로드하여 스크립트를 시작합니다. **System.Drawing** 및 **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="f2033-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span>
<span data-ttu-id="f2033-108">그런 다음 .NET Framework 클래스의 새 인스턴스인 **Windows.Forms.Form**을 시작하면 컨트롤을 추가할 수 있는 새 양식 또는 창이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

<span data-ttu-id="f2033-109">이 예제에서는 **Property** 속성 및 해시 테이블을 사용하여 이 클래스의 네 가지 속성에 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-109">This example assigns values to four properties of this class by using the **Property** property and hashtable.</span></span>

1. <span data-ttu-id="f2033-110">**StartPosition**: 이 속성을 추가하지 않은 경우 양식을 열 때 위치가 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-110">**StartPosition**: If you don’t add this property, Windows selects a location when the form is opened.</span></span>
   <span data-ttu-id="f2033-111">속성을 **CenterScreen**으로 설정하면 양식이 로드할 때마다 화면 가운데 자동으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-111">By setting this property to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

2. <span data-ttu-id="f2033-112">**Size**: 양식의 크기(픽셀)입니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-112">**Size**: This is the size of the form, in pixels.</span></span>
   <span data-ttu-id="f2033-113">이전 스크립트는 너비가 243픽셀이고 높이가 230픽셀인 양식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-113">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

3. <span data-ttu-id="f2033-114">**Text**: 창의 제목이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-114">**Text**: This becomes the title of the window.</span></span>

4. <span data-ttu-id="f2033-115">**최상위**: 이 속성을 `$true`로 설정하면, 창을 다른 열린 창 및 대화 상자로 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-115">**Topmost**: By setting this property to `$true`, you can force the window to open atop other open windows and dialog boxes.</span></span>

<span data-ttu-id="f2033-116">이제 달력 컨트롤을 만들어서 양식에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-116">Next, create and then add a calendar control in your form.</span></span>
<span data-ttu-id="f2033-117">이 예에서는 현재 날짜가 강조 표시되거나 원으로 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-117">In this example, the current day is not highlighted or circled.</span></span>
<span data-ttu-id="f2033-118">사용자는 달력에서 날짜를 한 번에 하나씩만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-118">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

<span data-ttu-id="f2033-119">그런 다음 양식에 대한 **확인** 단추를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-119">Next, create an **OK** button for your form.</span></span>
<span data-ttu-id="f2033-120">**확인** 단추의 크기와 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-120">Specify the size and behavior of the **OK** button.</span></span>
<span data-ttu-id="f2033-121">이 예에서는 단추가 양식의 위쪽 가장자리에서 165픽셀, 왼쪽 가장자리에서 38픽셀 위치에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-121">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span>
<span data-ttu-id="f2033-122">단추의 높이는 23픽셀이고 길이는 75픽셀입니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span>
<span data-ttu-id="f2033-123">이 스크립트는 미리 정의된 Windows Forms 형식을 사용하여 단추 동작을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="f2033-124">마찬가지로 **취소** 단추를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-124">Similarly, you create a **Cancel** button.</span></span>
<span data-ttu-id="f2033-125">**취소** 단추는 위쪽에서 165픽셀, 창의 왼쪽 가장자리에서 113픽셀 위치에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-125">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="f2033-126">다음 코드 줄을 추가하여 Windows에 양식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-126">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="f2033-127">마지막으로 `if` 블록 내의 코드는 사용자가 달력에서 날짜를 선택한 다음 **확인** 단추를 클릭하거나 **Enter** 키를 누를 때 양식으로 수행할 작업을 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-127">Finally, the code inside the `if` block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span>
<span data-ttu-id="f2033-128">Windows PowerShell에 선택된 날짜가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2033-128">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="f2033-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2033-129">See Also</span></span>

- [<span data-ttu-id="f2033-130">Hey Scripting Guy:  왜 이런 PowerShell GUI가 작동하지 않나요?</span><span class="sxs-lookup"><span data-stu-id="f2033-130">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="f2033-131">GitHub: Dave Wyatt의 WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="f2033-131">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="f2033-132">이번 주 Windows PowerShell 팁:  그래픽 날짜 선택 만들기</span><span class="sxs-lookup"><span data-stu-id="f2033-132">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](https://technet.microsoft.com/library/ff730942.aspx)
