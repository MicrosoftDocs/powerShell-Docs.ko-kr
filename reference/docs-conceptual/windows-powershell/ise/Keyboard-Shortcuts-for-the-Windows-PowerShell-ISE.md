---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Windows PowerShell ISE 바로 가기 키
ms.openlocfilehash: ee1b5961f8528d44330345bc49368e61970861ca
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809769"
---
# <a name="keyboard-shortcuts-for-the-windows-powershell-ise"></a>Windows PowerShell ISE 바로 가기 키

다음 바로 가기 키를 사용하여 Windows PowerShell® ISE(통합 스크립팅 환경)에서 작업을 수행할 수 있습니다. Windows PowerShell ISE는 Windows Server 및 Windows 클라이언트 운영 체제의 일부로 사용할 수 있지만, [Windows Management Framework 4.0 다운로드 패키지](https://go.microsoft.com/fwlink/?LinkID=293881)의 일부로 이전 Windows 운영 체제에 설치되어 있을 수도 있습니다.

## <a name="keyboard-shortcuts-for-editing-text"></a>텍스트 편집 바로 가기 키

텍스트를 편집할 때 다음과 같은 바로 가기 키를 사용할 수 있습니다.

|              작업              |       바로 가기 키       |                                                                                                                                                 사용 위치                                                                                                                                                 |
| -------------------------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **도움말**                         | <kbd>F1</kbd>                  | 스크립트 창 **중요:** <kbd>F1</kbd> 도움말을 웹의 TechNet 라이브러리 또는 다운로드한 도움말에서 가져오도록 지정할 수 있습니다(`Update-Help` 참조). 선택하려면 **도구**, **옵션**을 차례로 클릭하고 **일반 설정** 탭에서 **온라인 콘텐츠 대신 로컬 도움말 콘텐츠 사용**을 설정하거나 선택 취소합니다. |
| **Copy**                         | <kbd>Ctrl</kbd>+<kbd>C</kbd>   | 스크립트 창, 명령 창, 출력 창                                                                                                                                                                                                                                                                 |
| **잘라내기**                          | <kbd>Ctrl</kbd>+<kbd>X</kbd>   | 스크립트 창, 명령 창                                                                                                                                                                                                                                                                              |
| **개요 확장 또는 축소** | <kbd>Ctrl</kbd>+<kbd>M</kbd>   | 스크립트 창                                                                                                                                                                                                                                                                                            |
| **스크립트에서 찾기**               | <kbd>Ctrl</kbd>+<kbd>F</kbd>   | 스크립트 창                                                                                                                                                                                                                                                                                            |
| **스크립트에서 다음 찾기**          | <kbd>F3</kbd>                  | 스크립트 창                                                                                                                                                                                                                                                                                            |
| **스크립트에서 이전 찾기**      | <kbd>Shift</kbd>+<kbd>F3</kbd> | 스크립트 창                                                                                                                                                                                                                                                                                            |
| **일치하는 중괄호 찾기**          | <kbd>Ctrl</kbd>+<kbd>]</kbd>   | 스크립트 창                                                                                                                                                                                                                                                                                            |
| **붙여넣기**                        | <kbd>Ctrl</kbd>+<kbd>V</kbd>   | 스크립트 창, 명령 창                                                                                                                                                                                                                                                                              |
| **다시 실행**                         | <kbd>Ctrl</kbd>+<kbd>Y</kbd>   | 스크립트 창, 명령 창                                                                                                                                                                                                                                                                              |
| **스크립트에서 바꾸기**            | <kbd>Ctrl</kbd>+<kbd>H</kbd>   | 스크립트 창                                                                                                                                                                                                                                                                                            |
| **저장**                         | <kbd>Ctrl</kbd>+<kbd>S</kbd>   | 스크립트 창                                                                                                                                                                                                                                                                                            |
| **모두 선택**                   | <kbd>Ctrl</kbd>+<kbd>A</kbd>   | 스크립트 창, 명령 창, 출력 창                                                                                                                                                                                                                                                                 |
| **코드 조각 표시**                | <kbd>Ctrl</kbd>+<kbd>J</kbd>   | 스크립트 창, 명령 창                                                                                                                                                                                                                                                                              |
| **실행 취소**                         | <kbd>Ctrl</kbd>+<kbd>Z</kbd>   | 스크립트 창, 명령 창                                                                                                                                                                                                                                                                              |

## <a name="keyboard-shortcuts-for-running-scripts"></a>스크립트 실행 바로 가기 키

스크립트 창에서 스크립트를 실행할 때 다음과 같은 바로 가기 키를 사용할 수 있습니다.

|            작업            |                                                                                                             바로 가기 키                                                                                                             |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **새로 만들기**                      | <kbd>Ctrl</kbd>+<kbd>N</kbd>                                                                                                                                                                                                              |
| **열기**                     | <kbd>Ctrl</kbd>+<kbd>O</kbd>                                                                                                                                                                                                              |
| **실행**                      | <kbd>F5</kbd>                                                                                                                                                                                                                             |
| **선택 항목 실행**            | <kbd>F8</kbd>                                                                                                                                                                                                                             |
| **실행 중지**           | <kbd>Ctrl</kbd>+<kbd>BREAK</kbd>. 컨텍스트가 명확한 경우(선택한 텍스트가 없는 경우) <kbd>Ctrl</kbd>+<kbd>C</kbd>를 사용할 수 있습니다.                                                                                              |
| **Tab** 키를 눌러 다음 스크립트로 이동     | <kbd>Ctrl</kbd>+<kbd>Tab</kbd> **참고:** Tab 키를 눌러 다음 스크립트로 이동은 하나의 Windows PowerShell 탭만 열려 있는 경우 또는 둘 이상의 Windows PowerShell 탭이 열려 있지만 스크립트 창에 포커스가 있는 경우에 작동합니다.               |
| **Tab** 키를 눌러 이전 스크립트로 이동 | <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>Tab</kbd> **참고:** Tab 키를 눌러 이전 스크립트로 이동은 하나의 Windows PowerShell 탭만 열려 있는 경우 또는 둘 이상의 Windows PowerShell 탭이 열려 있고 스크립트 창에 포커스가 있는 경우에 작동합니다. |

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>보기 사용자 지정 바로 가기 키

Windows PowerShell ISE에서 보기를 사용자 지정할 때 다음과 같은 바로 가기 키를 사용할 수 있습니다. 애플리케이션의 모든 창에서 액세스할 수 있습니다.

|                        작업                         |               바로 가기 키               |
| ----------------------------------------------------- | --------------------------------------------- |
| **명령 창(v2) 또는 콘솔 창(v3 이상)으로 이동** | <kbd>Ctrl</kbd>+<kbd>D</kbd>                  |
| **출력 창(v2에만 해당)으로 이동**                       | <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>O</kbd> |
| **스크립트 창으로 이동**                                 | <kbd>Ctrl</kbd>+<kbd>I</kbd>                  |
| **스크립트 창 표시**                                  | <kbd>Ctrl</kbd>+<kbd>R</kbd>                  |
| **스크립트 창 숨기기**                                  | <kbd>Ctrl</kbd>+<kbd>R</kbd>                  |
| **스크립트 창 위로 이동**                               | <kbd>Ctrl</kbd>+<kbd>1</kbd>                  |
| **스크립트 창 오른쪽으로 이동**                            | <kbd>Ctrl</kbd>+<kbd>2</kbd>                  |
| **스크립트 창 최대화**                              | <kbd>Ctrl</kbd>+<kbd>3</kbd>                  |
| **확대**                                           | <kbd>Ctrl</kbd>+<kbd>+</kbd>                  |
| **축소**                                          | <kbd>Ctrl</kbd>+<kbd>-</kbd>                  |

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>스크립트 디버그 바로 가기 키

스크립트를 디버그할 때 다음과 같은 바로 가기 키를 사용할 수 있습니다.

|           작업           |               바로 가기 키                |                사용 위치                |
| -------------------------- | ---------------------------------------------- | ------------------------------------ |
| **실행/계속**           | <kbd>F5</kbd>                                  | 스크립트 창, 스크립트를 디버그할 때 |
| **한 단계씩 코드 실행**              | <kbd>F11</kbd>                                 | 스크립트 창, 스크립트를 디버그할 때 |
| **프로시저 단위 실행**              | <kbd>F10</kbd>                                 | 스크립트 창, 스크립트를 디버그할 때 |
| **프로시저 나가기**               | <kbd>Shift</kbd>+<kbd><kbd>F11</kbd></kbd>     | 스크립트 창, 스크립트를 디버그할 때 |
| **호출 스택 표시**     | <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>  | 스크립트 창, 스크립트를 디버그할 때 |
| **중단점 표시**       | <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>L</kbd>  | 스크립트 창, 스크립트를 디버그할 때 |
| **중단점 설정/해제**      | <kbd>F9</kbd>                                  | 스크립트 창, 스크립트를 디버그할 때 |
| **모든 중단점 제거** | <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>F9</kbd> | 스크립트 창, 스크립트를 디버그할 때 |
| **디버거 중지**          | <kbd>Shift</kbd>+<kbd>F5</kbd>                 | 스크립트 창, 스크립트를 디버그할 때 |

> [!NOTE]
> Windows PowerShell ISE에서 스크립트를 디버그할 때 Windows PowerShell 콘솔용으로 설계된 바로 가기 키를 사용할 수도 있습니다. 이러한 바로 가기를 사용하려면 명령 창에서 바로 가기를 입력하고 <kbd>Enter</kbd> 키를 눌러야 합니다.

|                        작업                        | 바로 가기 키 |                사용 위치                 |
| ---------------------------------------------------- | ----------------- | ------------------------------------- |
| **계속**                                         | `C`               | 콘솔 창, 스크립트를 디버그할 때 |
| **한 단계씩 코드 실행**                                        | `S`               | 콘솔 창, 스크립트를 디버그할 때 |
| **프로시저 단위 실행**                                        | `V`               | 콘솔 창, 스크립트를 디버그할 때 |
| **프로시저 나가기**                                         | `O`               | 콘솔 창, 스크립트를 디버그할 때 |
| **마지막 명령 반복**(한 단계씩 코드 실행 또는 프로시저 단위 실행) | <kbd>Enter</kbd>  | 콘솔 창, 스크립트를 디버그할 때 |
| **호출 스택 표시**                               | `K`               | 콘솔 창, 스크립트를 디버그할 때 |
| **디버깅 중지**                                   | `Q`               | 콘솔 창, 스크립트를 디버그할 때 |
| **스크립트 표시**                                  | `L`               | 콘솔 창, 스크립트를 디버그할 때 |
| **콘솔 디버깅 명령 표시**               | `H` 또는 `?`        | 콘솔 창, 스크립트를 디버그할 때 |

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Windows PowerShell 탭 바로 가기 키

Windows PowerShell 탭을 사용할 때 다음과 같은 바로 가기 키를 사용할 수 있습니다.

|             작업              |                                                        바로 가기 키                                                        |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **PowerShell 탭 닫기**        | <kbd>Ctrl</kbd>+<kbd>W</kbd>                                                                                                    |
| **새 PowerShell 탭**          | <kbd>Ctrl</kbd>+<kbd>T</kbd>                                                                                                    |
| **이전 PowerShell 탭**     | <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>Tab</kbd> 이 바로 가기는 Windows PowerShell 탭에 열려 있는 파일이 없는 경우에만 작동합니다. |
| **다음 Windows PowerShell 탭** | <kbd>Ctrl</kbd>+<kbd>Tab</kbd>. 이 바로 가기는 Windows PowerShell 탭에 열려 있는 파일이 없는 경우에만 작동합니다.                  |

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>시작 및 종료 바로 가기 키

다음과 같은 바로 가기 키를 사용하여 Windows PowerShell 콘솔(PowerShell.exe)을 시작하거나 Windows PowerShell ISE를 종료할 수 있습니다.

|                        작업                        |               바로 가기 키               |
| ---------------------------------------------------- | --------------------------------------------- |
| **종료**                                             | <kbd>Alt</kbd>+<kbd>F4</kbd>                  |
| **PowerShell.exe 시작**(Windows PowerShell 콘솔) | <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> |

## <a name="see-also"></a>참고 항목

- [PowerShell Magazine: Windows PowerShell ISE 바로 가기 키의 전체 목록](https://www.powershellmagazine.com/2013/01/29/the-complete-list-of-powershell-ise-3-0-keyboard-shortcuts/)
