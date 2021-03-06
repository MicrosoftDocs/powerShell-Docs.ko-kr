---
ms.date: 01/02/2020
title: Windows PowerShell ISE 탐색
description: 이 문서에서는 Windows PowerShell ISE를 간략히 설명합니다.
ms.topic: conceptual
ms.custom: ISE-F1-page
ms.openlocfilehash: 91161763c817972a62b4da1558a7ca119d8c8616
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97090449"
---
# <a name="exploring-the-windows-powershell-ise"></a>Windows PowerShell ISE 탐색

Windows PowerShell ISE(통합 스크립팅 환경)를 사용하여 명령 및 스크립트를 만들고, 실행하고, 디버그할 수 있습니다. Windows PowerShell ISE는 메뉴 모음, Windows PowerShell 탭, 도구 모음, 스크립트 탭, 스크립트 창, 콘솔 창, 상태 표시줄, 텍스트 크기 슬라이더, 상황에 맞는 도움말 등으로 구성됩니다.

## <a name="menu-bar"></a>메뉴 모음

메뉴 모음에는 **파일**, **편집**, **보기**, **도구**, **디버그**, **추가 기능** 및 **도움말** 메뉴가 있습니다. 메뉴의 단추를 사용하여 Windows PowerShell ISE에서 스크립트를 작성 및 실행하고 명령을 실행하는 것과 관련된 작업을 수행할 수 있습니다. 또한 [ISE 개체 모델 계층 구조](object-model/The-ISE-Object-Model-Hierarchy.md)를 사용하는 스크립트를 실행하여 메뉴 모음에 [추가 기능 도구](object-model/The-ISEAddOnTool-Object.md)를 배치할 수 있습니다.

## <a name="windows-powershell-tabs"></a>Windows PowerShell 탭

Windows PowerShell 탭은 Windows PowerShell 스크립트가 실행되는 환경입니다. Windows PowerShell ISE에서 새 Windows PowerShell 탭을 열어 로컬 컴퓨터나 원격 컴퓨터에 별도의 환경을 만들 수 있습니다. 최대 8개의 PowerShell 탭을 동시에 열 수 있습니다.

자세한 내용은 [Windows PowerShell ISE에서 PowerShell 탭을 만드는 방법](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)을 참조하세요.

## <a name="toolbar"></a>도구 모음

도구 모음에는 다음과 같은 단추가 있습니다.

|             단추             |                                                                                     함수                                                                                     |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **새로 만들기**                        | 새 스크립트를 엽니다.                                                                                                                                                              |
| **열기**                       | 기존 스크립트 또는 파일을 엽니다.                                                                                                                                                |
| **저장**                       | 스크립트 또는 파일을 저장합니다.                                                                                                                                                          |
| **잘라내기**                        | 선택한 텍스트를 잘라내어 클립보드에 복사합니다.                                                                                                                           |
| **Copy**                       | 선택한 텍스트를 클립보드로 복사합니다.                                                                                                                                       |
| **붙여넣기**                      | 클립보드의 내용을 커서 위치에 붙여넣습니다.                                                                                                                     |
| **출력 창 지우기**          | 출력 창에서 모든 내용을 지웁니다.                                                                                                                                           |
| **실행 취소**                       | 방금 수행한 작업을 취소합니다.                                                                                                                                     |
| **다시 실행**                       | 방금 실행 취소한 작업을 수행합니다.                                                                                                                                        |
| **스크립트 실행**                 | 스크립트를 실행합니다.                                                                                                                                                                   |
| **선택 항목 실행**              | 선택한 스크립트 부분을 실행합니다.                                                                                                                                             |
| **실행 중지**             | 실행 중인 스크립트를 중지합니다.                                                                                                                                                  |
| **새 원격 PowerShell 탭**  | 원격 컴퓨터에서 세션을 설정하는 새 PowerShell 탭을 만듭니다. 대화 상자가 나타나고 원격 연결을 설정하는 데 필요한 세부 정보를 입력하라는 메시지가 표시됩니다. |
| **PowerShell.exe 시작**       | PowerShell 콘솔을 엽니다.                                                                                                                                                      |
| **스크립트 창 위쪽에 표시**       | 표시에서 스크립트 창을 맨 위로 이동합니다.                                                                                                                                 |
| **스크립트 창 오른쪽에 표시**     | 표시에서 스크립트 창을 오른쪽으로 이동합니다.                                                                                                                               |
| **스크립트 창 최대 표시** | 스크립트 창을 최대화합니다.                                                                                                                                                       |

## <a name="script-tab"></a>스크립트 탭

편집 중인 스크립트의 이름을 표시합니다. 스크립트 탭을 클릭하여 편집할 스크립트를 선택할 수 있습니다.

스크립트 탭을 가리키면 스크립트 파일의 정규화된 경로가 도구 설명에 표시됩니다.

## <a name="script-pane"></a>스크립트 창

스크립트를 만들고 실행할 수 있습니다. 스크립트 창에서 기존 스크립트를 열고, 편집하고, 실행할 수 있습니다. 자세한 내용은 [Windows PowerShell ISE에서 스크립트를 작성 및 실행하는 방법](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md)을 참조하세요.

## <a name="console-pane"></a>콘솔 창

실행한 명령 및 스크립트의 결과를 표시합니다. 콘솔 창에서 명령을 실행할 수 있습니다. 콘솔 창에서 내용을 복사하고 지울 수도 있습니다.

자세한 내용은 다음 문서를 참조하세요.

- [Windows PowerShell ISE에서 콘솔 창을 사용하는 방법](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)
- [Windows PowerShell ISE에서 스크립트를 디버그하는 방법](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md)
- [스크립트 창 및 콘솔 창에서 탭 완성 기능을 사용하는 방법](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)

## <a name="status-bar"></a>상태 표시줄

실행하는 명령 및 스크립트가 완료되었는지 여부를 확인할 수 있습니다. 상태 표시줄은 맨 아래에 표시됩니다. 오류 메시지의 선택한 부분이 상태 표시줄에 표시됩니다.

## <a name="text-size-slider"></a>텍스트 크기 슬라이더

화면에서 텍스트 크기를 크게 하거나 작게 합니다.

## <a name="help"></a>도움말

Windows PowerShell ISE에 대한 도움말은 docs.microsoft.com에서 사용할 수 있습니다. **도움말** 메뉴에서 **Windows PowerShell ISE 도움말** 을 클릭하거나 스크립트 창이나 콘솔 창에서 커서가 cmdlet 이름에 있는 경우를 제외하고 아무 곳에서나 <kbd>F1</kbd> 키를 누르면 도움말을 열 수 있습니다.
**도움말** 메뉴에서 `Update-Help` cmdlet을 실행하여 cmdlet에 대한 모든 매개 변수를 표시하고 사용하기 쉬운 형태로 매개 변수를 입력할 수 있게 하여 명령 생성을 지원하는 명령 창을 표시할 수도 있습니다.

## <a name="see-also"></a>참고 항목

- [Windows PowerShell ISE 소개](Introducing-the-Windows-PowerShell-ISE.md)
- [Windows PowerShell ISE에서 프로필을 사용하는 방법](How-to-Use-Profiles-in-Windows-PowerShell-ISE.md)
- [Windows PowerShell ISE의 접근성](Accessibility-in-Windows-PowerShell-ISE.md)
- [Windows PowerShell ISE 바로 가기 키](Keyboard-Shortcuts-for-the-Windows-PowerShell-ISE.md)
