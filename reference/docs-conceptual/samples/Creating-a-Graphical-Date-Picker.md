---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 그래픽 날짜 선택 만들기
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 6dd43a3b1f4c67633ad1755de3db88eb8c6772c8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402180"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="37ab5-103">그래픽 날짜 선택 만들기</span><span class="sxs-lookup"><span data-stu-id="37ab5-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="37ab5-104">Windows PowerShell 3.0 이상 릴리스를 사용하여 날짜를 선택할 수 있는 그래픽 달력 스타일 컨트롤이 포함된 양식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="37ab5-105">그래픽 날짜 선택 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="37ab5-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="37ab5-106">다음을 복사하여 Windows PowerShell ISE에 붙여넣은 다음 Windows PowerShell 스크립트(.ps1)로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form

$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'

$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="37ab5-107">다음 두 .NET Framework 클래스를 로드하여 이 스크립트를 시작합니다. **System.Drawing** 및 **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="37ab5-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="37ab5-108">그런 다음 .NET Framework 클래스의 새 인스턴스인 **Windows.Forms.Form**을 시작하면 컨트롤을 추가할 수 있는 새 양식 또는 창이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form
```

<span data-ttu-id="37ab5-109">Form 클래스의 인스턴스를 만든 후 이 클래스의 세 속성에 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="37ab5-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="37ab5-110">**Text.**</span></span> <span data-ttu-id="37ab5-111">창의 제목이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="37ab5-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="37ab5-112">**Size.**</span></span> <span data-ttu-id="37ab5-113">양식의 크기(픽셀)입니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="37ab5-114">이전 스크립트는 너비가 243픽셀이고 높이가 230픽셀인 양식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-114">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

- <span data-ttu-id="37ab5-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="37ab5-115">**StartingPosition.**</span></span> <span data-ttu-id="37ab5-116">이전 스크립트에서는 이 선택적 속성이 **CenterScreen**으로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="37ab5-117">이 속성을 추가하지 않은 경우 양식을 열 때 위치가 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="37ab5-118">**StartingPosition**을 **CenterScreen**으로 설정하면 양식이 로드할 때마다 화면 가운데 자동으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="37ab5-119">이제 달력 컨트롤을 만들어서 양식에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-119">Next, create and then add a calendar control in your form.</span></span> <span data-ttu-id="37ab5-120">이 예에서는 현재 날짜가 강조 표시되거나 원으로 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-120">In this example, the current day is not highlighted or circled.</span></span> <span data-ttu-id="37ab5-121">사용자는 달력에서 날짜를 한 번에 하나씩만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-121">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

<span data-ttu-id="37ab5-122">그런 다음 양식에 대한 **확인** 단추를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-122">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="37ab5-123">**확인** 단추의 크기와 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-123">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="37ab5-124">이 예에서는 단추가 양식의 위쪽 가장자리에서 165픽셀, 왼쪽 가장자리에서 38픽셀 위치에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-124">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="37ab5-125">단추의 높이는 23픽셀이고 길이는 75픽셀입니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-125">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="37ab5-126">이 스크립트는 미리 정의된 Windows Forms 형식을 사용하여 단추 동작을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-126">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="37ab5-127">마찬가지로 **취소** 단추를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-127">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="37ab5-128">**취소** 단추는 위쪽에서 165픽셀, 창의 왼쪽 가장자리에서 113픽셀 위치에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-128">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="37ab5-129">창을 다른 열린 창 및 대화 상자 위에 표시하려면 **Topmost** 속성을 **$true**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="37ab5-130">다음 코드 줄을 추가하여 Windows에 양식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-130">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="37ab5-131">마지막으로 **If** 블록 내의 코드는 사용자가 달력에서 날짜를 선택한 다음 **확인** 단추를 클릭하거나 **Enter** 키를 누를 때 양식으로 수행할 작업을 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-131">Finally, the code inside the **If** block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="37ab5-132">Windows PowerShell에 선택된 날짜가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="37ab5-132">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="37ab5-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="37ab5-133">See Also</span></span>

- [<span data-ttu-id="37ab5-134">스크립팅 작성자: 이러한 PowerShell GUI 예제가 작동하지 않는 이유는 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="37ab5-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="37ab5-135">GitHub Dave Wyatt의 WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="37ab5-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="37ab5-136">Windows PowerShell Tip of the Week: 그래픽 날짜 선택 만들기</span><span class="sxs-lookup"><span data-stu-id="37ab5-136">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](https://technet.microsoft.com/library/ff730942.aspx)