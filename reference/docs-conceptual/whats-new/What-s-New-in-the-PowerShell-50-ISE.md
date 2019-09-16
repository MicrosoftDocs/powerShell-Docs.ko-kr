---
ms.date: 09/06/2019
keywords: powershell,cmdlet
title: PowerShell 5.0 ISE의 새로운 기능
ms.openlocfilehash: a719baef0da1600f0a5377e1b72c81b67e37eef2
ms.sourcegitcommit: a74ae7ed089301992fed201fbe55d827a622afa0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70746216"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a>Windows PowerShell 5.0 ISE의 새로운 기능

이 항목에서는 Windows PowerShell ISE(통합 스크립팅 환경) 버전에서 도입된 새로운 기능과 업데이트된 기능에 대해 설명합니다.

## <a name="feature-description"></a>기능 설명

Windows PowerShell ISE는 그래픽 환경 및 직관적인 환경에서 스크립트 및 모듈을 작성, 실행 및 테스트할 수 있는 호스트 애플리케이션입니다. 구문 색 지정, 탭 완성, 시각적 디버깅, 유니코드 규정 준수 및 상황에 맞는 도움말과 같은 주요 기능을 통해 풍부한 스크립팅 환경을 제공합니다.

자세한 내용은 [Windows PowerShell ISE 소개](../components/ise/Introducing-the-Windows-PowerShell-ISE.md)를 참조하세요.

다음 표에는 Windows PowerShell에 있는 이 Windows PowerShell ISE 릴리스용의 새로운 기능과 변경된 기능이 나와 있습니다.

## <a name="intellisense"></a>IntelliSense

> ISE 3.0에서 추가되었습니다.

IntelliSense는 Windows PowerShell ISE의 일부인 자동 완성 지원 기능입니다.
IntelliSense는 입력하는 동안 잠재적으로 일치하는 cmdlet, 매개 변수, 매개 변수 값, 파일 또는 폴더가 포함된 클릭 가능한 메뉴를 표시합니다.

**이와 같은 변경을 통해 더해지는 가치**

IntelliSense를 추가하면 Windows PowerShell ISE를 사용하여 스크립트를 작성할 때 cmdlet과 구문을 더 쉽게 검색할 수 있습니다. 새 스크립트를 만드는 동안 Windows PowerShell ISE를 사용하여 Windows PowerShell에 대해 알아볼 수도 있습니다.

**달라진 기능**

Windows PowerShell ISE에서 cmdlet을 입력하면 스크롤 및 클릭 가능한 메뉴가 표시되므로 적절한 명령을 찾아서 선택할 수 있습니다.

## <a name="snippets"></a>코드 조각

> ISE 3.0에서 추가되었습니다.

*코드 조각*은 Windows PowerShell ISE에서 만든 스크립트에 삽입할 수 있는 Windows PowerShell 코드의 짧은 부분입니다. Windows PowerShell ISE에는 기본 코드 조각 집합이 포함되어 있습니다. Windows PowerShell ISE에서 작업하는 동안 `New-Snippet` cmdlet을 사용하여 코드 조각을 추가할 수 있습니다.

**이와 같은 변경을 통해 더해지는 가치**

코드 조각을 사용하면 빠르게 스크립트를 조합하고 만들어 사용자 환경을 자동화할 수 있습니다.

**달라진 기능**

Windows PowerShell 3.0 이상에서 코드 조각을 사용하려면 **편집** 메뉴에서 **조각 시작**을 클릭하거나 <kbd>Ctrl</kbd>+<kbd>J</kbd>를 누릅니다.

## <a name="add-on-tools"></a>추가 기능 도구

> PowerShell 3.0에서 추가되었습니다.

이제 Windows PowerShell ISE는 개체 모델을 사용하여 추가 기능 도구를 지원합니다. 이러한 추가 기능은 콘솔에서 세로 또는 가로 창으로 표시되는 WPF(Windows Presentation Foundation) 컨트롤입니다. 하나의 창에 있는 여러 가지 추가 기능 도구는 탭 컨트롤로 표시됩니다. 타사에서 만든 추가 기능 도구를 추가하거나 제거할 수도 있습니다. 자세한 내용은 [Windows PowerShell ISE 스크립팅 개체 모델의 용도](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)를 참조하세요.

**이와 같은 변경을 통해 더해지는 가치**

추가 기능을 사용하면 기능 추가 및 스크립팅 환경 향상이 가능한 도구로 Windows PowerShell ISE를 확장하고 사용자 지정할 수 있습니다.

**달라진 기능**

Windows PowerShell ISE 3.0 이상에는 **Commands** 추가 기능이 포함되어 있습니다. **Commands** 추가 기능을 사용하면 cmdlet을 찾고 **스크립트** 창과 **콘솔** 창에서 cmdlet에 대한 도움말을 나란히 액세스할 수 있습니다.

**추가 기능** 메뉴의 **추가 기능 도구 웹 사이트 열기** 명령을 사용하여 추가 기능을 더 찾을 수 있습니다.

## <a name="restart-manager-and-auto-save"></a>관리자 다시 시작 및 자동 저장

> PowerShell 3.0에서 추가되었습니다.

이제 Windows PowerShell ISE에서 열려 있는 스크립트를 2분마다 개별 위치에 자동으로 저장합니다. 예기치 않은 충돌로 인해 또는 다시 부팅하여 Windows PowerShell ISE가 다시 시작되면 스크립트를 저장하지 않았더라도 마지막 세션에 열려 있던 스크립트가 복구됩니다.

자동 저장 간격을 변경하려면 콘솔 창에서 다음 명령을 실행합니다. `$psise.Options.AutoSaveMinuteInterval`.

**이와 같은 변경을 통해 더해지는 가치**

이제 열려 있는 스크립트가 자동으로 저장된다는 것을 알고 Windows PowerShell ISE 내에서 작업할 수 있습니다.

**달라진 기능**

Windows PowerShell ISE 2.0은 스크립트를 자동으로 저장하지 않습니다.

## <a name="most-recently-used-list"></a>가장 최근에 사용한 목록

> PowerShell 3.0에서 추가되었습니다.

이제 Windows PowerShell ISE에 가장 최근에 사용한 파일 목록이 있습니다. Windows PowerShell ISE에서 파일을 열면 **파일** 메뉴의 가장 최근에 사용한 목록에 해당 파일이 추가됩니다.

가장 최근에 사용한 목록의 기본 파일 수를 변경하려면 콘솔 창에서 다음 명령을 실행합니다. `$psise.Options.MruCount`.

**이와 같은 변경을 통해 더해지는 가치**

이제 가장 최근에 사용한 목록을 통해 최근에 사용한 파일을 쉽게 액세스할 수 있습니다.

**달라진 기능**

Windows PowerShell ISE 2.0에는 가장 최근에 사용한 목록이 없습니다.

## <a name="console-pane"></a>콘솔 창

> PowerShell 3.0에서 추가되었습니다.

Windows PowerShell ISE의 첫 번째 릴리스에서 제공된 별도의 명령 및 출력 창이 단일 콘솔 창으로 결합되었습니다. 콘솔 창의 기능과 모양은 일반적인 Windows PowerShell 콘솔과 유사하지만 다음과 같은 기능이 향상되었습니다.

- XML 구문을 포함하여 입력 텍스트(출력 텍스트가 아님)의 구문 색 지정
- IntelliSense
- 중괄호 일치
- 오류 표시
- 전체 유니코드 지원
- <kbd>F1</kbd> 상황에 맞는 도움말
- <kbd>Ctrl</kbd>+<kbd>F1</kbd> 상황에 맞는 Show-Command
- 복잡한 스크립트 및 오른쪽에서 왼쪽으로 쓰는 언어 지원
- 글꼴 지원
- 확대/축소
- 줄 선택 및 블록 선택 모드
- <kbd>위쪽 화살표</kbd>를 눌러 콘솔에서 기록을 볼 때 명령줄에 입력된 콘텐츠 유지

**이와 같은 변경을 통해 더해지는 가치**

이러한 콘솔 창 변경 내용이 추가되어 콘솔 인터페이스와 보다 일치하는 스크립팅 환경을 제공합니다.

**달라진 기능**

Windows PowerShell ISE 2.0에는 별도의 명령 창과 출력 창이 있습니다.

## <a name="command-line-switches"></a>명령줄 스위치

> PowerShell 3.0에서 추가되었습니다.

**powershell_ise.exe**를 입력하여 명령줄에서 Windows PowerShell ISE를 시작하면 다음과 같은 새 명령줄 스위치를 추가할 수 있습니다.

- `-NoProfile`: `$profile`을 실행하지 않고 Windows PowerShell ISE를 시작합니다.
- `-Help`: 도움말 창을 표시합니다.
- `-mta`: 다중 스레드 아파트 모드로 Windows PowerShell ISE를 시작합니다. Windows PowerShell ISE에 대한 기본 작업 모드는 단일 스레드 아파트 모드, 즉 `-sta`입니다.

**이와 같은 변경을 통해 더해지는 가치**

이러한 명령줄 스위치가 추가되어 Windows PowerShell ISE가 실행되는 환경을 제어할 수 있습니다.

**달라진 기능**

Windows PowerShell ISE 2.0에서는 이러한 명령줄 스위치를 인식할 수 없습니다.

## <a name="new-editor-features"></a>새 편집기 기능

> PowerShell 3.0에서 추가되었습니다.

다른 Windows PowerShell ISE에는 다음과 같은 편집 기능이 포함됩니다.

- **XML 구문 색 지정** - 이제 Windows PowerShell ISE에서 Windows PowerShell 구문에 색을 지정하는 것과 동일한 방법으로 XML 구문에 색을 지정합니다.
- **중괄호 일치** - Windows PowerShell ISE에는 중괄호 일치 및 강조 표시가 포함되어 있으며, 다음과 같은 방법으로 사용할 수 있습니다. 예를 들어 여는 중괄호가 선택되어 있는 경우 **일치 항목으로 이동** 명령 또는 <kbd>Ctrl</kbd>+<kbd>]</kbd>를 사용하면 닫는 중괄호를 찾습니다.
- **개요 보기** 스크립트 창에서 개요 기능을 지원하므로 왼쪽 여백의 더하기 또는 빼기 기호를 클릭하여 코드의 섹션을 축소하거나 확장할 수 있습니다. 중괄호 또는 `#region` 및 `#endregion` 태그를 사용하여 축소 가능한 섹션의 시작이나 끝을 표시할 수 있습니다. 모든 영역을 확장하거나 축소하려면 <kbd>Ctrl</kbd>+<kbd>M</kbd>을 누릅니다.
- **텍스트 끌어서 놓기** - 이제 Windows PowerShell ISE에서 텍스트 끌어서 놓기를 지원합니다. 텍스트 블록을 선택한 다음 텍스트를 편집기 또는 콘솔의 다른 위치로 끌어서 이동할 수 있습니다. <kbd>Ctrl</kbd> 키를 누른 채 선택한 텍스트를 끄는 경우 마우스 단추를 놓으면 텍스트가 새 위치에 복사됩니다. 이 버전의 Windows PowerShell ISE에서 파일을 Windows PowerShell ISE로 끌어다 놓으면 Windows PowerShell ISE에서 파일이 열립니다.
- **구문 분석 오류 표시** - 빨간색 밑줄을 사용하여 구문 분석 오류를 표시합니다. 표시된 오류 위에 마우스를 놓으면 코드에서 검색된 문제가 도구 설명 텍스트에 표시됩니다.
- **확대/축소** - 확대/축소 슬라이더(Windows PowerShell ISE 창의 오른쪽 맨 아래에 있음)를 사용하거나 콘솔 창에 `$psise.options.Zoom` 명령을 입력하여 콘솔 콘텐츠의 확대/축소 비율을 설정할 수 있습니다.
- **서식 있는 텍스트 복사 및 붙여넣기** - Windows PowerShell ISE에서 클립보드로 복사하면 원래 선택 항목의 글꼴, 크기 및 색상 정보가 유지됩니다.
- **블록 선택** - <kbd>ALT</kbd> 키를 누른 채 스크립트 창에서 마우스로 텍스트를 선택하거나 <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>화살표</kbd>를 눌러 텍스트 블록을 선택할 수 있습니다.

**이와 같은 변경을 통해 더해지는 가치**

추가 편집 기능은 보다 일관되고 강력한 편집 환경을 제공합니다.

**달라진 기능**

Windows PowerShell ISE 2.0에는 이러한 향상된 편집 기능이 없었습니다.

## <a name="new-help-viewer-window"></a>새 도움말 뷰어 창

> PowerShell 3.0에서 추가되었습니다.

커서가 cmdlet에 있을 때 <kbd>F1</kbd> 키를 누르거나 cmdlet 일부를 강조 표시하면 강조 표시된 cmdlet에 대한 상황에 맞는 도움말이 새 도움말 뷰어에 표시됩니다. Windows PowerShell **정보** 도움말을 표시하려면 콘솔 창에 `operators`를 입력한 다음 <kbd>F1</kbd> 키를 누릅니다.

이 기능을 사용하려면 먼저 Microsoft 웹 사이트에서 최신 버전의 Windows PowerShell 도움말 항목을 다운로드합니다. 도움말 항목을 다운로드하는 가장 간단한 방법은 관리자 권한으로 Windows PowerShell ISE를 실행할 때 콘솔 창에서 `Update-Help` cmdlet을 실행하는 것입니다.

<kbd>F1</kbd> 키가 도움말을 찾는 위치를 변경할 수 있습니다. **도구**/**옵션** 메뉴의 **일반 설정** 탭에서 **기타 설정** 아래에 있는 **온라인 콘텐츠 대신 로컬 도움말 콘텐츠 사용** 확인란을 설정하거나 선택을 취소할 수 있습니다. 이 확인란을 선택하면 클라이언트는 모듈 폴더에 다운로드된 도움말에서 cmdlet 도움말을 찾습니다. 이 확인란을 선택하지 않으면 클라이언트가 온라인 도움말을 찾습니다.

**이와 같은 변경을 통해 더해지는 가치**

현재 cmdlet 또는 스크립트를 종료하지 않고 상황에 맞는 도움말을 사용함으로써 통합된 학습 환경을 제공합니다.

**달라진 기능**

이전 버전의 Windows PowerShell ISE에서 <kbd>F1</kbd> 키를 누르면 로컬 컴퓨터의 도움말 파일이 열렸습니다. Windows PowerShell ISE 3.0 이상에서는 검색 및 구성할 수 있는 cmdlet 도움말이 포함된 창이 열립니다. 이 도움말 환경은 Windows PowerShell ISE 3.0의 새로운 기능이며, 업데이트 가능한 도움말은 Windows PowerShell 3.0의 새로운 기능입니다.

## <a name="show-command-cmdlet"></a>Show-Command cmdlet

> PowerShell 3.0에서 추가되었습니다.

`Show-Command` cmdlet을 사용하면 그래픽 양식에 입력하여 cmdlet 또는 함수를 작성하거나 실행할 수 있습니다. 이 양식을 사용하면 사용자가 그래픽 환경에서 Windows PowerShell을 사용할 수 있습니다.
또한 `Show-Command`를 사용하면 고급 스크립터가 Windows PowerShell 기반 GUI를 빠르게 만들 수 있습니다.

**이와 같은 변경을 통해 더해지는 가치**

Windows PowerShell 스크립트에서 `Show-Command`를 사용하면 익숙한 그래픽 환경을 사용자에게 제공할 수 있습니다. `Show-Command`는 초급 사용자가 Windows PowerShell을 익히는 데 도움이 될 수도 있습니다.

**달라진 기능**

`Show-Command`는 새로운 Windows PowerShell ISE 3.0입니다.

## <a name="see-also"></a>참고 항목

Windows PowerShell ISE 사용에 대한 자세한 내용은 [Windows PowerShell 통합 스크립팅 환경 탐색](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)을 참조하세요.
