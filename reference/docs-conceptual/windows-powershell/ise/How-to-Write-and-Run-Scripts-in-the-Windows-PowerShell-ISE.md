---
ms.date: 01/02/2020
title: Windows PowerShell ISE에서 스크립트를 작성 및 실행하는 방법
description: 이 문서에서는 스크립트 창에서 스크립트를 만들고, 편집, 실행 및 저장하는 방법을 설명합니다.
ms.openlocfilehash: 8e85da1d4eecbb975f2dd799c91512e0081309d2
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663650"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Windows PowerShell ISE에서 스크립트를 작성 및 실행하는 방법

이 문서에서는 스크립트 창에서 스크립트를 만들고, 편집, 실행 및 저장하는 방법을 설명합니다.

## <a name="how-to-create-and-run-scripts"></a>스크립트를 만들고 실행하는 방법

스크립트 창에서 Windows PowerShell 파일을 열고 편집할 수 있습니다. Windows PowerShell에서 중요한 특정 파일 형식은 스크립트 파일(`.ps1`), 스크립트 데이터 파일(`.psd1`) 및 스크립트 모듈 파일(`.psm1`)입니다. 이러한 파일 형식은 스크립트 창 편집기에서 구문별로 색이 지정됩니다. 스크립트 창에서 열 수도 있는 다른 일반적인 파일 형식은 구성 파일(`.ps1xml`), XML 파일 및 텍스트 파일입니다.

> [!NOTE]
> Windows PowerShell 실행 정책은 스크립트를 실행하고 Windows PowerShell 프로필 및 구성 파일을 로드할 수 있는지 여부를 결정합니다. 기본 실행 정책인 Restricted는 모든 스크립트 실행과 프로필 로드를 차단합니다. 프로필 로드 및 사용을 허용하도록 실행 정책을 변경하려면 [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) 및 [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)을 참조하세요.

### <a name="to-create-a-new-script-file"></a>새 스크립트 파일을 만들려면

도구 모음에서 **새로 만들기** 를 클릭하거나 **파일** 메뉴에서 **새로 만들기** 를 클릭합니다. 생성된 파일은 현재 PowerShell 탭 아래의 새 파일 탭에 나타납니다. PowerShell 탭은 탭이 두 개 이상 있는 경우에만 표시됩니다. 기본적으로 스크립트 형식의 파일(`.ps1`)이 생성되지만 새 이름과 확장명으로 저장할 수 있습니다. 동일한 PowerShell 탭에서 여러 스크립트 파일을 만들 수 있습니다.

### <a name="to-open-an-existing-script"></a>기존 스크립트를 열려면

도구 모음에서 **열기** 를 클릭하거나 **파일** 메뉴에서 **열기** 를 클릭합니다. **열기** 대화 상자에서 열려는 파일을 선택합니다. 열린 파일이 새 탭에 나타납니다.

### <a name="to-close-a-script-tab"></a>스크립트 탭을 닫으려면

닫으려는 파일 탭의 **닫기** 아이콘( **X** )을 클릭하거나 **파일** 메뉴, **닫기** 를 차례로 클릭합니다.

파일이 마지막으로 저장된 후에 변경된 경우 변경 내용을 저장하거나 취소하라는 메시지가 표시됩니다.

### <a name="to-display-the-file-path"></a>파일 경로를 표시하려면

파일 탭에서 파일 이름을 가리킵니다. 스크립트 파일의 정규화된 경로가 도구 설명에 표시됩니다.

### <a name="to-run-a-script"></a>스크립트를 실행하려면

도구 모음에서 **스크립트 실행** 을 클릭하거나 **파일** 메뉴에서 **실행** 을 클릭합니다.

### <a name="to-run-a-portion-of-a-script"></a>스크립트의 일부를 실행하려면

1. 스크립트 창에서 스크립트의 일부를 선택합니다.
2. **파일** 메뉴에서 **선택 영역 실행** 을 클릭하거나 도구 모음에서 **선택 영역 실행** 을 클릭합니다.

### <a name="to-stop-a-running-script"></a>실행 중인 스크립트를 중지하려면

실행 중인 스크립트를 중지하는 몇 가지 방법이 있습니다.

- 도구 모음에서 **작업 중지** 를 클릭합니다.
- <kbd>Ctrl</kbd>+<kbd>BREAK</kbd>을 누릅니다.
- **파일** 메뉴를 선택하고 **작업 중지** 를 클릭합니다.

일부 텍스트가 현재 선택되지 않은 경우에는 <kbd>Ctrl</kbd>+<kbd>C</kbd>를 눌러도 됩니다. 텍스트가 선택된 경우 <kbd>Ctrl</kbd>+<kbd>C</kbd>는 선택한 텍스트의 복사 기능에 매핑됩니다.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>스크립트 창에서 텍스트를 작성 및 편집하는 방법

스크립트 창에서 텍스트를 복사, 잘라내기, 붙여넣기, 찾기 및 바꿀 수 있습니다. 방금 수행한 마지막 작업을 실행 취소하거나 다시 실행할 수도 있습니다. 이러한 작업을 위한 바로 가기 키는 모든 Windows 애플리케이션에 사용되는 바로 가기 키와 동일합니다.

### <a name="to-enter-text-in-the-script-pane"></a>스크립트 창에 텍스트를 입력하려면

1. 스크립트 창에서 아무 곳이나 클릭하거나 **보기** 메뉴에서 **스크립트 창으로 이동** 을 클릭하여 커서를 스크립트 창으로 이동합니다.
2. 스크립트를 만듭니다. Windows PowerShell ISE에서는 구문 색 지정 및 탭 완성 기능을 통해 풍부한 편집 환경이 구현됩니다.
3. 탭 완성 기능을 사용하여 보다 쉽게 입력하는 방법에 대한 자세한 내용은 [스크립트 창 및 콘솔 창에서 탭 완성 기능을 사용하는 방법](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)을 참조하세요.

### <a name="to-find-text-in-the-script-pane"></a>스크립트 창에서 텍스트를 찾으려면

1. 모든 위치에서 텍스트를 찾으려면 <kbd>Ctrl</kbd>+<kbd>F</kbd>를 누르거나, **편집** 메뉴에서 **스크립트에서 찾기** 를 클릭합니다.
2. 커서 뒤에서 텍스트를 찾으려면 <kbd>F3</kbd> 키를 누르거나, **편집** 메뉴에서 **스크립트에서 다음 찾기** 를 클릭합니다.
3. 커서 앞에서 텍스트를 찾으려면 <kbd>Shift</kbd>+<kbd>F3</kbd> 키를 누르거나, **편집** 메뉴에서 **스크립트에서 이전 찾기** 를 클릭합니다.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>스크립트 창에서 텍스트를 찾아 바꾸려면

<kbd>Ctrl</kbd>+<kbd>H</kbd>를 누르거나, **편집** 메뉴에서 **스크립트에서 바꾸기** 를 클릭합니다. 찾으려는 텍스트와 바꿀 텍스트를 입력하고 <kbd>Enter</kbd> 키를 누릅니다.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>스크립트 창에서 특정 텍스트 줄로 이동하려면

1. 스크립트 창에서 <kbd>Ctrl</kbd>+<kbd>G</kbd>를 누르거나, **편집** 메뉴에서 **줄 이동** 을 클릭합니다.

2. 줄 번호를 입력합니다.

### <a name="to-copy-text-in-the-script-pane"></a>스크립트 창에서 텍스트를 복사하려면

1. 스크립트 창에서 복사할 텍스트를 선택합니다.

2. <kbd>Ctrl</kbd>+<kbd>C</kbd>를 누르거나, 도구 모음에서 **복사** 아이콘을 클릭하거나, **편집** 메뉴에서 **복사** 를 클릭합니다.

### <a name="to-cut-text-in-the-script-pane"></a>스크립트 창에서 텍스트를 잘라내려면

1. 스크립트 창에서 잘라낼 텍스트를 선택합니다.
2. <kbd>Ctrl</kbd>+<kbd>X</kbd>를 누르거나, 도구 모음에서 **잘라내기** 아이콘을 클릭하거나, **편집** 메뉴에서 **잘라내기** 를 클릭합니다.

### <a name="to-paste-text-into-the-script-pane"></a>스크립트 창에 텍스트를 붙여넣으려면

<kbd>Ctrl</kbd>+<kbd>V</kbd>를 누르거나, 도구 모음에서 **붙여넣기** 아이콘을 클릭하거나, **편집** 메뉴에서 **붙여넣기** 를 클릭합니다.

### <a name="to-undo-an-action-in-the-script-pane"></a>스크립트 창에서 작업을 실행 취소하려면

<kbd>Ctrl</kbd>+<kbd>Z</kbd>를 누르거나, 도구 모음에서 **실행 취소** 아이콘을 클릭하거나, **편집** 메뉴에서 **실행 취소** 를 클릭합니다.

### <a name="to-redo-an-action-in-the-script-pane"></a>스크립트 창에서 작업을 다시 실행하려면

<kbd>Ctrl</kbd>+<kbd>Y</kbd>를 누르거나, 도구 모음에서 **다시 실행** 아이콘을 클릭하거나, **편집** 메뉴에서 **다시 실행** 을 클릭합니다.

## <a name="how-to-save-a-script"></a>스크립트를 저장하는 방법

변경된 이후 저장되지 않은 파일을 표시하기 위해 스크립트 이름 옆에 별표가 나타납니다. 파일을 저장하면 별표가 사라집니다.

### <a name="to-save-a-script"></a>스크립트를 저장하려면

<kbd>Ctrl</kbd>+<kbd>S</kbd>를 누르거나, 도구 모음에서 **저장** 아이콘을 클릭하거나, **파일** 메뉴에서 **저장** 을 클릭합니다.

### <a name="to-save-and-name-a-script"></a>스크립트를 저장하고 이름을 지정하려면

1. **파일** 메뉴에서 **다른 이름으로 저장** 을 클릭합니다. **다른 이름으로 저장** 대화 상자가 나타납니다.
2. **파일 이름** 상자에 파일의 이름을 입력합니다.
3. **파일 형식** 상자에서 파일 형식을 선택합니다. 예를 들어 **파일 형식** 상자에서 ‘PowerShell 스크립트(`*.ps1`)’를 선택합니다.
4. **저장** 을 클릭합니다.

### <a name="to-save-a-script-in-ascii-encoding"></a>ASCII 인코딩 형식으로 스크립트를 저장하려면

기본적으로 Windows PowerShell ISE에서는 새 스크립트 파일(`.ps1`), 스크립트 데이터 파일(`.psd1`) 및 스크립트 모듈 파일(`.psm1`)을 유니코드(BigEndianUnicode)로 저장합니다. 스크립트를 ASCII(ANSI) 등의 다른 인코딩으로 저장하려면 [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) 개체의 **Save** 또는 **SaveAs** 메서드를 사용합니다.

다음 명령은 ASCII 인코딩을 사용하여 새 스크립트를 MyScript.ps1로 저장합니다.

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

다음 명령은 현재 스크립트 파일을 이름은 같지만 ASCII 인코딩을 사용하는 파일로 바꿉니다.

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

다음 명령은 현재 파일의 인코딩을 가져옵니다.

```powershell
$psISE.CurrentFile.encoding
```

Windows PowerShell ISE에서는 인코딩 옵션 ASCII, BigEndianUnicode, 유니코드, UTF32, UTF7, UTF8 및 기본값을 지원합니다. 기본값 옵션의 값은 시스템에 따라 다릅니다.

Windows PowerShell ISE에서는 저장 또는 다른 이름으로 저장을 사용하는 경우 스크립트 파일의 인코딩이 변경되지 않습니다.

## <a name="see-also"></a>참고 항목

- [Windows PowerShell ISE 탐색](exploring-the-windows-powershell-ise.md)
