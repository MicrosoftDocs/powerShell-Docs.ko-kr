---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 목록 상자에서 항목 선택
ms.openlocfilehash: 048bccd403e01e2290a8930a0faba30d4c7caa73
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "77706175"
---
# <a name="selecting-items-from-a-list-box"></a><span data-ttu-id="3b709-103">목록 상자에서 항목 선택</span><span class="sxs-lookup"><span data-stu-id="3b709-103">Selecting Items from a List Box</span></span>

<span data-ttu-id="3b709-104">Windows PowerShell 3.0 이상 릴리스를 사용하여 목록 상자 컨트롤에서 항목을 선택할 수 있는 대화 상자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-104">Use Windows PowerShell 3.0 and later releases to create a dialog box that lets users select items from a list box control.</span></span>

## <a name="create-a-list-box-control-and-select-items-from-it"></a><span data-ttu-id="3b709-105">목록 상자 컨트롤을 만들고 이 컨트롤에서 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-105">Create a list box control, and select items from it</span></span>

<span data-ttu-id="3b709-106">다음을 복사하여 Windows PowerShell ISE에 붙여넣은 다음 Windows PowerShell 스크립트(.ps1)로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)

$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80

[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')

$form.Controls.Add($listBox)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

<span data-ttu-id="3b709-107">두 .NET Framework 클래스 **System.Drawing** 및 **System.Windows.Forms**를 로드하여 스크립트가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="3b709-108">그런 다음 .NET Framework 클래스의 새 인스턴스인 **System.Windows.Forms.Form**을 시작하면 컨트롤을 추가할 수 있는 새 양식 또는 창이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

<span data-ttu-id="3b709-109">Form 클래스의 인스턴스를 만든 후 이 클래스의 세 속성에 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="3b709-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="3b709-110">**Text.**</span></span> <span data-ttu-id="3b709-111">창의 제목이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="3b709-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="3b709-112">**Size.**</span></span> <span data-ttu-id="3b709-113">양식의 크기(픽셀)입니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="3b709-114">이전 스크립트는 너비가 300픽셀이고 높이가 200픽셀인 양식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="3b709-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="3b709-115">**StartingPosition.**</span></span> <span data-ttu-id="3b709-116">이전 스크립트에서는 이 선택적 속성이 **CenterScreen**으로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-116">This optional property is set to **CenterScreen** in the preceding script.</span></span>
  <span data-ttu-id="3b709-117">이 속성을 추가하지 않은 경우 양식을 열 때 위치가 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="3b709-118">**StartingPosition**을 **CenterScreen**으로 설정하면 양식이 로드할 때마다 화면 가운데 자동으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="3b709-119">그런 다음 양식에 대한 **확인** 단추를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="3b709-120">**확인** 단추의 크기와 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="3b709-121">이 예제에서는 단추가 양식의 위쪽 가장자리에서 120픽셀, 왼쪽 가장자리에서 75픽셀 위치에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="3b709-122">단추의 높이는 23픽셀이고 길이는 75픽셀입니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="3b709-123">이 스크립트는 미리 정의된 Windows Forms 형식을 사용하여 단추 동작을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)
```

<span data-ttu-id="3b709-124">마찬가지로 **취소** 단추를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="3b709-125">**취소** 단추는 위쪽에서 120픽셀, 창의 왼쪽 가장자리에서 150픽셀 위치에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

<span data-ttu-id="3b709-126">그런 다음 창에서 사용자에게 제공할 정보를 설명하는 레이블 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-126">Next, provide label text on your window that describes the information you want users to provide.</span></span> <span data-ttu-id="3b709-127">이 경우 사용자가 컴퓨터를 선택하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-127">In this case, you want users to select a computer.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

<span data-ttu-id="3b709-128">사용자가 레이블 텍스트에 설명된 정보를 입력할 수 있는 컨트롤(이 경우 목록 상자)을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-128">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="3b709-129">세부적인 제어를 위해 목록 상자 이외에 다른 여러 컨트롤을 추가할 수 있습니다. 자세한 내용은 MSDN에서 [System.Windows.Forms 네임스페이스](/dotnet/api/system.windows.forms)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b709-129">There are many other controls you can apply besides list boxes; for more controls, see [System.Windows.Forms Namespace](/dotnet/api/system.windows.forms) on MSDN.</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

<span data-ttu-id="3b709-130">다음 섹션에서는 목록 상자에서 사용자에게 표시할 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-130">In the next section, you specify the values you want the list box to display to users.</span></span>

> [!NOTE]
> <span data-ttu-id="3b709-131">이 스크립트로 만든 목록 상자에서는 하나만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-131">The list box created by this script allows only one selection.</span></span> <span data-ttu-id="3b709-132">여러 항목을 선택할 수 있는 목록 상자 컨트롤을 만들려면 **SelectionMode** 속성 값을 다음과 같이 지정합니다. `$listBox.SelectionMode = 'MultiExtended'`.</span><span class="sxs-lookup"><span data-stu-id="3b709-132">To create a list box control that allows multiple selections, specify a value for the **SelectionMode** property, similarly to the following: `$listBox.SelectionMode = 'MultiExtended'`.</span></span> <span data-ttu-id="3b709-133">자세한 내용은 [다중 선택 목록 상자](Multiple-selection-List-Boxes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b709-133">For more information, see [Multiple-selection List Boxes](Multiple-selection-List-Boxes.md).</span></span>

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
```

<span data-ttu-id="3b709-134">목록 상자 컨트롤을 양식에 추가하고 양식을 다른 창 및 대화 상자 위에 열도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-134">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="3b709-135">다음 코드 줄을 추가하여 Windows에 양식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-135">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="3b709-136">마지막으로 **If** 블록 내의 코드는 사용자가 목록 상자에서 옵션을 선택한 다음 **확인** 단추를 클릭하거나 **Enter** 키를 누를 때 양식으로 수행할 작업을 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="3b709-136">Finally, the code inside the **If** block instructs Windows what to do with the form after users select an option from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="3b709-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3b709-137">See Also</span></span>

- <span data-ttu-id="3b709-138">[GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)(GitHub: Dave Wyatt의 WinFormsExampleUpdates)</span><span class="sxs-lookup"><span data-stu-id="3b709-138">[GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)</span></span>
- <span data-ttu-id="3b709-139">[Windows PowerShell Tip of the Week: 목록 상자에서 항목 선택](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730949(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="3b709-139">[Windows PowerShell Tip of the Week:  Selecting Items from a List Box](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730949(v=technet.10))</span></span>
