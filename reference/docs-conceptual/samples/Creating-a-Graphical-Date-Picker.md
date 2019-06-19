---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 그래픽 날짜 선택 만들기
ms.openlocfilehash: d05445963b41af61a61aa29a425e638d43fb5d9d
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030241"
---
# <a name="creating-a-graphical-date-picker"></a>그래픽 날짜 선택 만들기

Windows PowerShell 3.0 이상 릴리스를 사용하여 날짜를 선택할 수 있는 그래픽 달력 스타일 컨트롤이 포함된 양식을 만듭니다.

## <a name="create-a-graphical-date-picker-control"></a>그래픽 날짜 선택 컨트롤 만들기

다음을 복사하여 Windows PowerShell ISE에 붙여넣은 다음 Windows PowerShell 스크립트(.ps1)로 저장합니다.

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

다음 두 .NET Framework 클래스를 로드하여 스크립트를 시작합니다. **System.Drawing** 및 **System.Windows.Forms**.
그런 다음 .NET Framework 클래스의 새 인스턴스인 **Windows.Forms.Form**을 시작하면 컨트롤을 추가할 수 있는 새 양식 또는 창이 제공됩니다.

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

이 예제에서는 **Property** 속성 및 해시 테이블을 사용하여 이 클래스의 네 가지 속성에 값을 할당합니다.

1. **StartPosition**: 이 속성을 추가하지 않은 경우 양식을 열 때 위치가 자동으로 선택됩니다.
   속성을 **CenterScreen**으로 설정하면 양식이 로드할 때마다 화면 가운데 자동으로 표시됩니다.

2. **Size**: 양식의 크기(픽셀)입니다.
   이전 스크립트는 너비가 243픽셀이고 높이가 230픽셀인 양식을 만듭니다.

3. **Text**: 창의 제목이 됩니다.

4. **최상위**: 이 속성을 `$true`로 설정하면, 창을 다른 열린 창 및 대화 상자로 적용할 수 있습니다.

이제 달력 컨트롤을 만들어서 양식에 추가합니다.
이 예에서는 현재 날짜가 강조 표시되거나 원으로 표시되지 않습니다.
사용자는 달력에서 날짜를 한 번에 하나씩만 선택할 수 있습니다.

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

그런 다음 양식에 대한 **확인** 단추를 만듭니다.
**확인** 단추의 크기와 동작을 지정합니다.
이 예에서는 단추가 양식의 위쪽 가장자리에서 165픽셀, 왼쪽 가장자리에서 38픽셀 위치에 배치됩니다.
단추의 높이는 23픽셀이고 길이는 75픽셀입니다.
이 스크립트는 미리 정의된 Windows Forms 형식을 사용하여 단추 동작을 결정합니다.

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

마찬가지로 **취소** 단추를 만듭니다.
**취소** 단추는 위쪽에서 165픽셀, 창의 왼쪽 가장자리에서 113픽셀 위치에 있습니다.

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

다음 코드 줄을 추가하여 Windows에 양식을 표시합니다.

```powershell
$result = $form.ShowDialog()
```

마지막으로 `if` 블록 내의 코드는 사용자가 달력에서 날짜를 선택한 다음 **확인** 단추를 클릭하거나 **Enter** 키를 누를 때 양식으로 수행할 작업을 지시합니다.
Windows PowerShell에 선택된 날짜가 표시됩니다.

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>참고 항목

- [Hey Scripting Guy:  왜 이런 PowerShell GUI가 작동하지 않나요?](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt의 WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [이번 주 Windows PowerShell 팁:  그래픽 날짜 선택 만들기](https://technet.microsoft.com/library/ff730942.aspx)
