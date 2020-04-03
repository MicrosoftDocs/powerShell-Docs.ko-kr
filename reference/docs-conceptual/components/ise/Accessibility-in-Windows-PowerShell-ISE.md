---
ms.date: 12/19/2019
keywords: powershell,cmdlet
title: Windows PowerShell ISE의 접근성
ms.openlocfilehash: 89eff839d69fdbd5a1fa48b61dab627ef83f751b
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500957"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Windows PowerShell ISE의 접근성

이 항목에서는 유용한 Windows PowerShell ISE(통합 스크립팅 환경)의 접근성 기능에 대해 설명합니다.

- [콘솔 창과 스크립트 창의 크기 및 위치를 변경하는 방법](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
- [텍스트 편집 바로 가기 키](#keyboard-shortcuts-for-editing-text)
- [스크립트 실행 바로 가기 키](#keyboard-shortcuts-for-running-scripts)
- [보기 사용자 지정 바로 가기 키](#keyboard-shortcuts-for-customizing-the-view)
- [스크립트 디버그 바로 가기 키](#keyboard-shortcuts-for-debugging-scripts)
- [Windows PowerShell 탭 바로 가기](#keyboard-shortcuts-for-windows-powershell-tabs) 키
- [시작 및 종료 바로 가기 키](#keyboard-shortcuts-for-starting-and-exiting)
- [Cmdlet을 사용하여 중단점 관리](#breakpoint-management)

Microsoft는 모든 사용자가 제품 및 서비스를 더욱 쉽게 사용할 수 있도록 최선을 다하고 있습니다. 다음 항목에서는 장애가 있는 사용자도 Windows PowerShell ISE를 더욱 쉽게 이용할 수 있는 기능, 제품, 서비스에 대한 정보를 제공합니다.

Microsoft Windows의 접근성 기능 및 유틸리티 외에, 다음과 같은 기능을 통해 장애가 있는 사용자가 Windows PowerShell ISE를 더욱 쉽게 이용할 수 있습니다.

- 바로 가기 키

- 구문 색 지정 테이블 및 [$psISE.Options](object-model/The-ISEOptions-Object.md) 스크립팅 개체를 사용하여 다른 여러 색 설정을 수정하는 기능입니다.

- 텍스트 크기 변경

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>콘솔 창과 스크립트 창의 크기 및 위치를 변경하는 방법

다음 단계를 사용하여 콘솔 창과 스크립트 창의 크기 및 위치를 변경할 수 있습니다. Windows PowerShell ISE를 다시 열 때 크기 및 위치 변경 내용은 유지됩니다.

### <a name="to-resize-the-script-pane-and-console-pane"></a>스크립트 창과 콘솔 창의 크기를 조정하려면

1. 스크립트 창과 콘솔 창을 구분하는 선 위에 포인터를 놓습니다.

2. 마우스 포인터가 양쪽 화살표로 바뀌면 테두리를 끌어 창의 크기를 변경합니다.

### <a name="to-move-the-script-pane-and-console-pane"></a>스크립트 창과 콘솔 창을 이동하려면

다음 중 하나를 수행합니다.

- 스크립트 창을 콘솔 창 위로 이동하려면 <kbd>Ctrl</kbd>+<kbd>1</kbd>을 누르거나, 도구 모음에서 **위쪽에 스크립트 창 표시** 아이콘을 클릭하거나, **보기** 메뉴에서 **위쪽에 스크립트 창 표시**를 클릭합니다.

- 스크립트 창을 콘솔 창 오른쪽으로 이동하려면 <kbd>Ctrl</kbd>+<kbd>2</kbd>를 누르거나, 도구 모음에서 **오른쪽에 스크립트 창 표시** 아이콘을 클릭하거나, **보기** 메뉴에서 **오른쪽에 스크립트 창 표시**를 클릭합니다.

- 스크립트 창을 최대화하려면 <kbd>Ctrl</kbd>+<kbd>3</kbd>을 누르거나, 도구 모음에서 **스크립트 창 최대 표시** 아이콘을 클릭하거나, **보기** 메뉴에서 **스크립트 창 최대 표시**를 클릭합니다.

- 콘솔 창을 최대화하고 스크립트 창을 숨기려면 탭 행의 맨 오른쪽 가장자리에 있는 **스크립트 창 숨기기** 아이콘을 클릭하고 **보기** 메뉴에서 **스크립트 창 표시** 메뉴 옵션을 클릭하여 선택 취소합니다.

- 콘솔 창이 최대화되었을 때 스크립트 창을 표시하려면 탭 행의 맨 오른쪽 가장자리에 있는 **스크립트 창 표시** 아이콘을 클릭하거나 **보기** 메뉴에서 **스크립트 창 표시** 메뉴 옵션을 클릭하여 선택합니다.

## <a name="keyboard-shortcuts-for-editing-text"></a>텍스트 편집 바로 가기 키

텍스트를 편집할 때 다음과 같은 바로 가기 키를 사용할 수 있습니다.

|           작업            |       바로 가기 키       |          사용 위치           |
| --------------------------- | ------------------------------ | ------------------------- |
| **Copy**                    | <kbd>Ctrl</kbd>+<kbd>C</kbd>   | 스크립트 창, 콘솔 창 |
| **잘라내기**                     | <kbd>Ctrl</kbd>+<kbd>X</kbd>   | 스크립트 창, 콘솔 창 |
| **스크립트에서 찾기**          | <kbd>Ctrl</kbd>+<kbd>F</kbd>   | 스크립트 창               |
| **스크립트에서 다음 찾기**     | <kbd>F3</kbd>                  | 스크립트 창               |
| **스크립트에서 이전 찾기** | <kbd>Shift</kbd>+<kbd>F3</kbd> | 스크립트 창               |
| **붙여넣기**                   | <kbd>Ctrl</kbd>+<kbd>V</kbd>   | 스크립트 창, 콘솔 창 |
| **다시 실행**                    | <kbd>Ctrl</kbd>+<kbd>Y</kbd>   | 스크립트 창, 콘솔 창 |
| **스크립트에서 바꾸기**       | <kbd>Ctrl</kbd>+<kbd>H</kbd>   | 스크립트 창               |
| **저장**                    | <kbd>Ctrl</kbd>+<kbd>S</kbd>   | 스크립트 창               |
| **모두 선택**              | <kbd>Ctrl</kbd>+<kbd>A</kbd>   | 스크립트 창, 콘솔 창 |
| **실행 취소**                    | <kbd>Ctrl</kbd>+<kbd>Z</kbd>   | 스크립트 창, 콘솔 창 |

## <a name="keyboard-shortcuts-for-running-scripts"></a>스크립트 실행 바로 가기 키

스크립트 창에서 스크립트를 실행할 때 다음과 같은 바로 가기 키를 사용할 수 있습니다.

|            작업            |                                                                                                     바로 가기 키                                                                                                      |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **새로 만들기**                      | <kbd>Ctrl</kbd>+<kbd>N</kbd>                                                                                                                                                                                               |
| **열기**                     | <kbd>Ctrl</kbd>+<kbd>O</kbd>                                                                                                                                                                                               |
| **실행**                      | <kbd>F5</kbd>                                                                                                                                                                                                              |
| **선택 항목 실행**            | <kbd>F8</kbd>                                                                                                                                                                                                              |
| **실행 중지**           | <kbd>Ctrl</kbd>+<kbd>BREAK</kbd>. 컨텍스트가 명확한 경우(선택한 텍스트가 없는 경우) <kbd>Ctrl</kbd>+<kbd>C</kbd>를 사용할 수 있습니다.                                                                               |
| **Tab** 키를 눌러 다음 스크립트로 이동     | <kbd>Ctrl</kbd>+<kbd>Tab</kbd> **참고:** Tab 키를 눌러 다음 스크립트로 이동은 하나의 PowerShell 탭만 열려 있는 경우 또는 둘 이상의 PowerShell 탭이 열려 있지만 스크립트 창에 포커스가 있는 경우에 작동합니다.                |
| **Tab** 키를 눌러 이전 스크립트로 이동 | <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>Tab</kbd> **참고:** Tab 키를 눌러 이전 스크립트로 이동은 하나의 PowerShell 탭만 열려 있는 경우 또는 둘 이상의 PowerShell 탭이 열려 있고 스크립트 창에 포커스가 있는 경우에 작동합니다. |

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>보기 사용자 지정 바로 가기 키

Windows PowerShell ISE에서 보기를 사용자 지정할 때 다음과 같은 바로 가기 키를 사용할 수 있습니다. 애플리케이션의 모든 창에서 액세스할 수 있습니다.

|           작업           |         바로 가기 키        |
| -------------------------- | -------------------------------- |
| **콘솔 창으로 이동**     | <kbd>Ctrl</kbd>+<kbd>D</kbd>     |
| **스크립트 창으로 이동**      | <kbd>Ctrl</kbd>+<kbd>I</kbd>     |
| **스크립트 창 표시**       | <kbd>Ctrl</kbd>+<kbd>R</kbd>     |
| **스크립트 창 숨기기**       | <kbd>Ctrl</kbd>+<kbd>R</kbd>     |
| **스크립트 창 위로 이동**    | <kbd>Ctrl</kbd>+<kbd>1</kbd>     |
| **스크립트 창 오른쪽으로 이동** | <kbd>Ctrl</kbd>+<kbd>2</kbd>     |
| **스크립트 창 최대화**   | <kbd>Ctrl</kbd>+<kbd>3</kbd>     |
| **확대**                | <kbd>Ctrl</kbd>+<kbd>더하기</kbd>  |
| **축소**               | <kbd>Ctrl</kbd>+<kbd>빼기</kbd> |

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>스크립트 디버그 바로 가기 키

스크립트를 디버그할 때 다음과 같은 바로 가기 키를 사용할 수 있습니다.

|           작업           |               바로 가기 키                |                사용 위치                |
| -------------------------- | ---------------------------------------------- | ------------------------------------ |
| **실행/계속**           | <kbd>F5</kbd>                                  | 스크립트 창, 스크립트를 디버그할 때 |
| **한 단계씩 코드 실행**              | <kbd>F11</kbd>                                 | 스크립트 창, 스크립트를 디버그할 때 |
| **프로시저 단위 실행**              | <kbd>F10</kbd>                                 | 스크립트 창, 스크립트를 디버그할 때 |
| **프로시저 나가기**               | <kbd>Shift</kbd>+<kbd>F11</kbd>                | 스크립트 창, 스크립트를 디버그할 때 |
| **호출 스택 표시**     | <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>  | 스크립트 창, 스크립트를 디버그할 때 |
| **중단점 표시**       | <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>L</kbd>  | 스크립트 창, 스크립트를 디버그할 때 |
| **중단점 설정/해제**      | <kbd>F9</kbd>                                  | 스크립트 창, 스크립트를 디버그할 때 |
| **모든 중단점 제거** | <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>F9</kbd> | 스크립트 창, 스크립트를 디버그할 때 |
| **디버거 중지**          | <kbd>Shift</kbd>+<kbd>F5</kbd>                 | 스크립트 창, 스크립트를 디버그할 때 |

> [!NOTE]
> Windows PowerShell ISE에서 스크립트를 디버그할 때 Windows PowerShell 콘솔용으로 설계된 바로 가기 키를 사용할 수도 있습니다. 이러한 바로 가기를 사용하려면 콘솔 창에서 바로 가기를 입력하고 <kbd>ENTER</kbd> 키를 눌러야 합니다.

|                 작업                  |      바로 가기 키       |                사용 위치                 |
| --------------------------------------- | ---------------------------- | ------------------------------------- |
| **계속**                            | <kbd>C</kbd>                 | 콘솔 창, 스크립트를 디버그할 때 |
| **한 단계씩 코드 실행**                           | <kbd>S</kbd>                 | 콘솔 창, 스크립트를 디버그할 때 |
| **프로시저 단위 실행**                           | <kbd>V</kbd>                 | 콘솔 창, 스크립트를 디버그할 때 |
| **프로시저 나가기**                            | <kbd>O</kbd>                 | 콘솔 창, 스크립트를 디버그할 때 |
| **마지막 명령 반복**(한 단계씩 코드 실행/프로시저 단위 실행) | <kbd>Enter</kbd>             | 콘솔 창, 스크립트를 디버그할 때 |
| **호출 스택 표시**                  | <kbd>K</kbd>                 | 콘솔 창, 스크립트를 디버그할 때 |
| **디버깅 중지**                      | <kbd>Q</kbd>                 | 콘솔 창, 스크립트를 디버그할 때 |
| **스크립트 표시**                     | <kbd>L</kbd>                 | 콘솔 창, 스크립트를 디버그할 때 |
| **콘솔 디버깅 명령 표시**  | <kbd>H</kbd> 또는 <kbd>?</kbd> | 콘솔 창, 스크립트를 디버그할 때 |

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Windows PowerShell 탭 바로 가기 키

Windows PowerShell 탭을 사용할 때 다음과 같은 바로 가기 키를 사용할 수 있습니다.

|             작업              |                                 바로 가기 키                                  |
| ------------------------------- | ---------------------------------------------------------------------------------- |
| **PowerShell 탭 닫기**        | <kbd>Ctrl</kbd>+<kbd>W</kbd>                                                       |
| **새 PowerShell 탭**          | <kbd>Ctrl</kbd>+<kbd>T</kbd>                                                       |
| **이전 PowerShell 탭**     | <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>Tab</kbd>(PowerShell 탭에 열려 있는 파일이 없는 경우에만 해당) |
| **다음 Windows PowerShell 탭** | <kbd>Ctrl</kbd>+<kbd>Tab</kbd>(PowerShell 탭에 열려 있는 파일이 없는 경우에만 해당) |

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>시작 및 종료 바로 가기 키

다음과 같은 바로 가기 키를 사용하여 Windows PowerShell 콘솔(**PowerShell.exe**)을 시작하거나 Windows PowerShell ISE를 종료할 수 있습니다.

|                        작업                         |               바로 가기 키               |
| ----------------------------------------------------- | --------------------------------------------- |
| **종료**                                              | <kbd>Alt</kbd>+<kbd>F4</kbd>                  |
| **PowerShell.exe 시작** (Windows PowerShell 콘솔) | <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> |

## <a name="breakpoint-management"></a>중단점 관리

시각 장애가 있는 사용자의 경우 중단점 관리 cmdlet(예: [Get-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Get-PSBreakpoint) 및 [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint))을 통해 중단점 정보를 사용할 수 있습니다. 자세한 내용은 [Windows PowerShell ISE에서 스크립트를 디버그하는 방법](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md)에서 ‘중단점을 관리하는 방법’을 참조하세요.

## <a name="see-also"></a>참고 항목

[Windows PowerShell ISE 소개](Introducing-the-Windows-PowerShell-ISE.md)
