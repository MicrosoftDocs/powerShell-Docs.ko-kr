---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 사용자 지정 입력란 만들기
description: 이 문서에서는 Windows PowerShell의 .NET Framework 양식 작성 기능을 사용하여 사용자 지정 입력 상자를 만드는 방법을 보여줍니다.
ms.openlocfilehash: b7786706d2461c329da429c1bd4971d7dc874d6d
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390085"
---
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="d2329-104">사용자 지정 입력란 만들기</span><span class="sxs-lookup"><span data-stu-id="d2329-104">Creating a Custom Input Box</span></span>

<span data-ttu-id="d2329-105">Windows PowerShell 3.0 이상 릴리스에서 Microsoft .NET Framework 양식 빌드 기능을 사용하여 그래픽 사용자 지정 입력란을 스크립팅합니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-105">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="d2329-106">사용자 지정 그래픽 입력란 만들기</span><span class="sxs-lookup"><span data-stu-id="d2329-106">Create a custom, graphical input box</span></span>

<span data-ttu-id="d2329-107">다음을 복사하여 Windows PowerShell ISE에 붙여넣은 다음 Windows PowerShell 스크립트(.ps1)로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-107">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Data Entry Form'
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
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)

$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)

$form.Topmost = $true

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

<span data-ttu-id="d2329-108">두 .NET Framework 클래스 **System.Drawing** 및 **System.Windows.Forms** 를 로드하여 스크립트가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-108">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="d2329-109">그런 다음 .NET Framework 클래스의 새 인스턴스인 **System.Windows.Forms.Form** 을 시작하면 컨트롤을 추가할 수 있는 새 양식 또는 창이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-109">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="d2329-110">Form 클래스의 인스턴스를 만든 후 이 클래스의 세 속성에 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-110">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="d2329-111">**Text.**</span><span class="sxs-lookup"><span data-stu-id="d2329-111">**Text.**</span></span> <span data-ttu-id="d2329-112">창의 제목이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-112">This becomes the title of the window.</span></span>

- <span data-ttu-id="d2329-113">**Size.**</span><span class="sxs-lookup"><span data-stu-id="d2329-113">**Size.**</span></span> <span data-ttu-id="d2329-114">양식의 크기(픽셀)입니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-114">This is the size of the form, in pixels.</span></span> <span data-ttu-id="d2329-115">이전 스크립트는 너비가 300픽셀이고 높이가 200픽셀인 양식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-115">The preceding script creates a form that's 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="d2329-116">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="d2329-116">**StartingPosition.**</span></span> <span data-ttu-id="d2329-117">이전 스크립트에서는 이 선택적 속성이 **CenterScreen** 으로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-117">This optional property is set to **CenterScreen** in the preceding script.</span></span>
  <span data-ttu-id="d2329-118">이 속성을 추가하지 않으면 양식을 열 때 위치가 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-118">If you don't add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="d2329-119">**StartingPosition** 을 **CenterScreen** 으로 설정하면 로드할 때마다 화면 가운데 양식이 자동으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-119">By setting the **StartingPosition** to **CenterScreen**, you're automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="d2329-120">그런 다음 양식에 대한 **확인** 단추를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-120">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="d2329-121">**확인** 단추의 크기와 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-121">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="d2329-122">이 예제에서는 단추가 양식의 위쪽 가장자리에서 120픽셀, 왼쪽 가장자리에서 75픽셀 위치에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-122">In this example, the button position is 120 pixels from the form's top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="d2329-123">단추의 높이는 23픽셀이고 길이는 75픽셀입니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-123">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="d2329-124">이 스크립트는 미리 정의된 Windows Forms 형식을 사용하여 단추 동작을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-124">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="d2329-125">마찬가지로 **취소** 단추를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-125">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="d2329-126">**취소** 단추는 위쪽에서 120픽셀, 창의 왼쪽 가장자리에서 150픽셀 위치에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-126">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

<span data-ttu-id="d2329-127">그런 다음 창에서 사용자에게 제공할 정보를 설명하는 레이블 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-127">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

<span data-ttu-id="d2329-128">사용자가 레이블 텍스트에 설명된 정보를 입력할 수 있는 컨트롤(여기서는 텍스트 상자)을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-128">Add the control (in this case, a text box) that lets users provide the information you've described in your label text.</span></span> <span data-ttu-id="d2329-129">세부적인 제어를 위해 텍스트 상자 이외에 다른 여러 컨트롤을 추가할 수 있습니다. 자세한 내용은 [System.Windows.Forms 네임스페이스](/dotnet/api/system.windows.forms)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2329-129">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](/dotnet/api/system.windows.forms).</span></span>

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

<span data-ttu-id="d2329-130">창을 다른 열린 창 및 대화 상자 위에 표시하려면 **Topmost** 속성을 **$true** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-130">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="d2329-131">이제 이 코드 줄을 추가하여 양식을 활성화하고 포커스를 만든 텍스트 상자로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-131">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```powershell
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="d2329-132">다음 코드 줄을 추가하여 Windows에 양식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-132">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="d2329-133">마지막으로 **If** 블록 내의 코드는 사용자가 텍스트 상자에 텍스트를 입력한 다음 **확인** 단추를 클릭하거나 **Enter** 키를 누를 때 양식으로 수행할 작업을 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="d2329-133">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="d2329-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d2329-134">See Also</span></span>

- <span data-ttu-id="d2329-135">[GitHub: Dave Wyatt's WinFormsExampleUpdates](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730941(v=technet.10))(GitHub: Dave Wyatt의 WinFormsExampleUpdates)</span><span class="sxs-lookup"><span data-stu-id="d2329-135">[GitHub: Dave Wyatt's WinFormsExampleUpdates](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730941(v=technet.10))</span></span>
- [<span data-ttu-id="d2329-136">Windows PowerShell Tip of the Week: 사용자 지정 입력란 만들기</span><span class="sxs-lookup"><span data-stu-id="d2329-136">Windows PowerShell Tip of the Week:  Creating a Custom Input Box</span></span>](https://technet.microsoft.com/library/ff730941.aspx)
