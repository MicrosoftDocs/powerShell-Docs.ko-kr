---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 다중 선택 목록 상자
ms.openlocfilehash: 7bf71fb76a11f88c4ad4790bf3a2b383d0babb81
ms.sourcegitcommit: 3e343f005fe76960c998ef1869a1a093d37ef349
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216076"
---
# <a name="multiple-selection-list-boxes"></a><span data-ttu-id="0a475-103">다중 선택 목록 상자</span><span class="sxs-lookup"><span data-stu-id="0a475-103">Multiple-selection List Boxes</span></span>

<span data-ttu-id="0a475-104">Windows PowerShell 3.0 이상 릴리스를 사용하여 사용자 지정 Windows Form에서 다중 선택 목록 상자 컨트롤을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-104">Use Windows PowerShell 3.0 and later releases to create a multiple-selection list box control in a custom Windows Form.</span></span>

## <a name="create-list-box-controls-that-allow-multiple-selections"></a><span data-ttu-id="0a475-105">다중 선택을 허용하는 목록 상자 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="0a475-105">Create list box controls that allow multiple selections</span></span>

<span data-ttu-id="0a475-106">다음을 복사하여 Windows PowerShell ISE에 붙여넣은 다음 Windows PowerShell 스크립트(.ps1)로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)

$listBox.SelectionMode = 'MultiExtended'

[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')

$listBox.Height = 70
$form.Controls.Add($listBox)
$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

<span data-ttu-id="0a475-107">두 .NET Framework 클래스 **System.Drawing** 및 **System.Windows.Forms**를 로드하여 스크립트가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="0a475-108">그런 다음 .NET Framework 클래스의 새 인스턴스인 **System.Windows.Forms.Form**을 시작하면 컨트롤을 추가할 수 있는 새 양식 또는 창이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="0a475-109">Form 클래스의 인스턴스를 만든 후 이 클래스의 세 속성에 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="0a475-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="0a475-110">**Text.**</span></span> <span data-ttu-id="0a475-111">창의 제목이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="0a475-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="0a475-112">**Size.**</span></span> <span data-ttu-id="0a475-113">양식의 크기(픽셀)입니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="0a475-114">이전 스크립트는 너비가 300픽셀이고 높이가 200픽셀인 양식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="0a475-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="0a475-115">**StartingPosition.**</span></span> <span data-ttu-id="0a475-116">이전 스크립트에서는 이 선택적 속성이 **CenterScreen**으로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="0a475-117">이 속성을 추가하지 않은 경우 양식을 열 때 위치가 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="0a475-118">**StartingPosition**을 **CenterScreen**으로 설정하면 양식이 로드할 때마다 화면 가운데 자동으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="0a475-119">그런 다음 양식에 대한 **확인** 단추를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="0a475-120">**확인** 단추의 크기와 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="0a475-121">이 예제에서는 단추가 양식의 위쪽 가장자리에서 120픽셀, 왼쪽 가장자리에서 75픽셀 위치에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="0a475-122">단추의 높이는 23픽셀이고 길이는 75픽셀입니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="0a475-123">이 스크립트는 미리 정의된 Windows Forms 형식을 사용하여 단추 동작을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="0a475-124">마찬가지로 **취소** 단추를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="0a475-125">**취소** 단추는 위쪽에서 120픽셀, 창의 왼쪽 가장자리에서 150픽셀 위치에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="0a475-126">그런 다음 창에서 사용자에게 제공할 정보를 설명하는 레이블 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

<span data-ttu-id="0a475-127">사용자가 레이블 텍스트에 설명된 정보를 입력할 수 있는 컨트롤(이 경우 목록 상자)을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-127">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="0a475-128">세부적인 제어를 위해 텍스트 상자 이외에 다른 여러 컨트롤을 추가할 수 있습니다. 자세한 내용은 MSDN에서 [System.Windows.Forms 네임스페이스](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a475-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

<span data-ttu-id="0a475-129">사용자가 목록에서 여러 값을 선택할 수 있도록 허용하는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-129">Here’s how you specify that you want to allow users to select multiple values from the list.</span></span>

```powershell
$listBox.SelectionMode = 'MultiExtended'
```

<span data-ttu-id="0a475-130">다음 섹션에서는 목록 상자에서 사용자에게 표시할 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-130">In the next section, you specify the values you want the list box to display to users.</span></span>

```powershell
[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')
```

<span data-ttu-id="0a475-131">목록 상자 컨트롤의 최대 높이를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-131">Specify the maximum height of the list box control.</span></span>

```powershell
$listBox.Height = 70
```

<span data-ttu-id="0a475-132">목록 상자 컨트롤을 양식에 추가하고 양식을 다른 창 및 대화 상자 위에 열도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-132">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="0a475-133">다음 코드 줄을 추가하여 Windows에 양식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-133">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="0a475-134">마지막으로 **If** 블록 내의 코드는 사용자가 목록 상자에서 하나 이상의 옵션을 선택한 다음 **확인** 단추를 클릭하거나 **Enter** 키를 누를 때 양식으로 수행할 작업을 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="0a475-134">Finally, the code inside the **If** block instructs Windows what to do with the form after users select one or more options from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="0a475-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a475-135">See Also</span></span>

- [<span data-ttu-id="0a475-136">주말 스크립터:  PowerShell GUI 예제 수정</span><span class="sxs-lookup"><span data-stu-id="0a475-136">Weekend Scripter:  Fixing PowerShell GUI Examples</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- <span data-ttu-id="0a475-137">[GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)(GitHub: Dave Wyatt의 WinFormsExampleUpdates)</span><span class="sxs-lookup"><span data-stu-id="0a475-137">[GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)</span></span>
- <span data-ttu-id="0a475-138">[Windows PowerShell Tip of the Week: Multi-Select List Boxes - And More!](https://technet.microsoft.com/library/ff730950.aspx)(이 주의 Windows PowerShell 팁: 다중 선택 목록 상자 등)</span><span class="sxs-lookup"><span data-stu-id="0a475-138">[Windows PowerShell Tip of the Week:  Multi-Select List Boxes - And More!](https://technet.microsoft.com/library/ff730950.aspx)</span></span>
