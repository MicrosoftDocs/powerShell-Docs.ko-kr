---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 목록 상자에서 항목 선택
description: 이 문서에서는 Windows PowerShell의 .NET Framework 양식 작성 기능을 사용하여 목록 상자 컨트롤을 만드는 방법을 보여줍니다.
ms.openlocfilehash: cfd6110a9cfcc3cea891d68d8ce7be5b332a949a
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501051"
---
# <a name="selecting-items-from-a-list-box"></a>목록 상자에서 항목 선택

Windows PowerShell 3.0 이상 릴리스를 사용하여 목록 상자 컨트롤에서 항목을 선택할 수 있는 대화 상자를 만듭니다.

## <a name="create-a-list-box-control-and-select-items-from-it"></a>목록 상자 컨트롤을 만들고 이 컨트롤에서 항목을 선택합니다.

다음을 복사하여 Windows PowerShell ISE에 붙여넣은 다음 Windows PowerShell 스크립트(.ps1)로 저장합니다.

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

두 .NET Framework 클래스 **System.Drawing** 및 **System.Windows.Forms** 를 로드하여 스크립트가 시작됩니다. 그런 다음 .NET Framework 클래스의 새 인스턴스인 **System.Windows.Forms.Form** 을 시작하면 컨트롤을 추가할 수 있는 새 양식 또는 창이 제공됩니다.

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

Form 클래스의 인스턴스를 만든 후 이 클래스의 세 속성에 값을 할당합니다.

- **Text.** 창의 제목이 됩니다.

- **Size.** 양식의 크기(픽셀)입니다. 이전 스크립트는 너비가 300픽셀이고 높이가 200픽셀인 양식을 만듭니다.

- **StartingPosition.** 이전 스크립트에서는 이 선택적 속성이 **CenterScreen** 으로 설정되어 있습니다.
  이 속성을 추가하지 않으면 양식을 열 때 위치가 자동으로 선택됩니다. **StartingPosition** 을 **CenterScreen** 으로 설정하면 로드할 때마다 화면 가운데 양식이 자동으로 표시됩니다.

```powershell
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

그런 다음 양식에 대한 **확인** 단추를 만듭니다. **확인** 단추의 크기와 동작을 지정합니다. 이 예제에서는 단추가 양식의 위쪽 가장자리에서 120픽셀, 왼쪽 가장자리에서 75픽셀 위치에 배치됩니다. 단추의 높이는 23픽셀이고 길이는 75픽셀입니다. 이 스크립트는 미리 정의된 Windows Forms 형식을 사용하여 단추 동작을 결정합니다.

```powershell
$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)
```

마찬가지로 **취소** 단추를 만듭니다. **취소** 단추는 위쪽에서 120픽셀, 창의 왼쪽 가장자리에서 150픽셀 위치에 있습니다.

```powershell
$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

그런 다음 창에서 사용자에게 제공할 정보를 설명하는 레이블 텍스트를 입력합니다. 이 경우 사용자가 컴퓨터를 선택하도록 합니다.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

사용자가 레이블 텍스트에 설명된 정보를 입력할 수 있는 컨트롤(여기서는 목록 상자)을 추가합니다. 세부적인 제어를 위해 목록 상자 이외에 다른 여러 컨트롤을 추가할 수 있습니다. 자세한 내용은 MSDN에서 [System.Windows.Forms 네임스페이스](/dotnet/api/system.windows.forms)를 참조하세요.

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

다음 섹션에서는 목록 상자에서 사용자에게 표시할 값을 지정합니다.

> [!NOTE]
> 이 스크립트로 만든 목록 상자에서는 하나만 선택할 수 있습니다. 여러 항목을 선택할 수 있는 목록 상자 컨트롤을 만들려면 **SelectionMode** 속성 값을 다음과 같이 지정합니다. `$listBox.SelectionMode = 'MultiExtended'`. 자세한 내용은 [다중 선택 목록 상자](Multiple-selection-List-Boxes.md)를 참조하세요.

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
```

목록 상자 컨트롤을 양식에 추가하고 양식을 다른 창 및 대화 상자 위에 열도록 지시합니다.

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

다음 코드 줄을 추가하여 Windows에 양식을 표시합니다.

```powershell
$result = $form.ShowDialog()
```

마지막으로 **If** 블록 내의 코드는 사용자가 목록 상자에서 옵션을 선택한 다음 **확인** 단추를 클릭하거나 **Enter** 키를 누를 때 양식으로 수행할 작업을 지시합니다.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a>참고 항목

- [GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)(GitHub: Dave Wyatt의 WinFormsExampleUpdates)
- [Windows PowerShell Tip of the Week: 목록 상자에서 항목 선택](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730949(v=technet.10))
