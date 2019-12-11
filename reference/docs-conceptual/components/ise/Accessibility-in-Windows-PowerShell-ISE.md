---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell ISE의 접근성
ms.openlocfilehash: 416b18dd492ca04d98b5adf9f7f0f88ea495740a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030640"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Windows PowerShell ISE의 접근성

이 항목에서는 유용한 Windows PowerShell ISE(통합 스크립팅 환경)의 접근성 기능에 대해 설명합니다.

* [콘솔 창과 스크립트 창의 크기 및 위치를 변경하는 방법](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
* [텍스트 편집 바로 가기 키](#keyboard-shortcuts-for-editing-text)
* [스크립트 실행 바로 가기 키](#keyboard-shortcuts-for-running-scripts)
* [보기 사용자 지정 바로 가기 키](#keyboard-shortcuts-for-customizing-the-view)
* [스크립트 디버그 바로 가기 키](#keyboard-shortcuts-for-debugging-scripts)
* [Windows PowerShell 탭 바로 가기](#keyboard-shortcuts-for-windows-powershell-tabs) 키
* [시작 및 종료 바로 가기 키](#keyboard-shortcuts-for-starting-and-exiting)

Microsoft는 모든 사용자가 제품 및 서비스를 더욱 쉽게 사용할 수 있도록 최선을 다하고 있습니다. 다음 항목에서는 장애가 있는 사용자도 Windows PowerShell ISE를 더욱 쉽게 이용할 수 있는 기능, 제품, 서비스에 대한 정보를 제공합니다.

Windows PowerShell ISE에서는 고대비 모드를 지원합니다. 시각 장애가 있는 사용자의 경우 중단점 관리 cmdlet(예: [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) 및 [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420))을 통해 중단점 정보를 사용할 수 있습니다. 자세한 내용은 [Windows PowerShell ISE에서 스크립트를 디버그하는 방법](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md)에서 ‘중단점을 관리하는 방법’을 참조하세요. Microsoft Windows의 접근성 기능 및 유틸리티 외에, 다음과 같은 기능을 통해 장애가 있는 사용자가 Windows PowerShell ISE를 더욱 쉽게 이용할 수 있습니다.

- 바로 가기 키

- 구문 색 지정 테이블 및 [$psISE.Options](https://technet.microsoft.com/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb) 스크립팅 개체를 사용하여 다른 여러 색 설정을 수정하는 기능입니다.

- 텍스트 크기 변경

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>콘솔 창과 스크립트 창의 크기 및 위치를 변경하는 방법

다음 단계를 사용하여 콘솔 창과 스크립트 창의 크기 및 위치를 변경할 수 있습니다. Windows PowerShell ISE를 다시 열 때 크기 및 위치 변경 내용은 유지됩니다.

### <a name="to-resize-the-script-pane-and-console-pane"></a>스크립트 창과 콘솔 창의 크기를 조정하려면

1. 스크립트 창과 콘솔 창을 구분하는 선 위에 포인터를 놓습니다.

2. 마우스 포인터가 양쪽 화살표로 바뀌면 테두리를 끌어 창의 크기를 변경합니다.

### <a name="to-move-the-script-pane-and-console-pane"></a>스크립트 창과 콘솔 창을 이동하려면

다음 중 하나를 수행합니다.

- 스크립트 창을 콘솔 창 위로 이동하려면 **CTRL+1**을 누르거나, 도구 모음에서 **위쪽에 스크립트 창 표시** 아이콘을 클릭하거나, **보기** 메뉴에서 **위쪽에 스크립트 창 표시**를 클릭합니다.

- 스크립트 창을 콘솔 창 오른쪽으로 이동하려면 **Ctrl+2**를 누르거나, 도구 모음에서 **오른쪽에 스크립트 창 표시** 아이콘을 클릭하거나, **보기** 메뉴에서 **오른쪽에 스크립트 창 표시**를 클릭합니다.

- 스크립트 창을 최대화하려면 **Ctrl+3**을 누르거나, 도구 모음에서 **스크립트 창 최대 표시** 아이콘을 클릭하거나, **보기** 메뉴에서 **스크립트 창 최대 표시**를 클릭합니다.

- 콘솔 창을 최대화하고 스크립트 창을 숨기려면 탭 행의 맨 오른쪽 가장자리에 있는 **스크립트 창 숨기기** 아이콘을 클릭하고 **보기** 메뉴에서 **스크립트 창 표시** 메뉴 옵션을 클릭하여 선택 취소합니다.

- 콘솔 창이 최대화되었을 때 스크립트 창을 표시하려면 탭 행의 맨 오른쪽 가장자리에 있는 **스크립트 창 표시** 아이콘을 클릭하거나 **보기** 메뉴에서 **스크립트 창 표시** 메뉴 옵션을 클릭하여 선택합니다.

## <a name="keyboard-shortcuts-for-editing-text"></a>텍스트 편집 바로 가기 키

텍스트를 편집할 때 다음과 같은 바로 가기 키를 사용할 수 있습니다.

|작업|바로 가기 키|사용 위치|
|----------|----------------------|----------|
|**복사**|CTRL+C|스크립트 창, 콘솔 창|
|**잘라내기**|CTRL+X|스크립트 창, 콘솔 창|
|**스크립트에서 찾기**|Ctrl+F|스크립트 창|
|**스크립트에서 다음 찾기**|F3|스크립트 창|
|**스크립트에서 이전 찾기**|SHIFT+F3|스크립트 창|
|**붙여넣기**|CTRL+V|스크립트 창, 콘솔 창|
|**다시 실행**|CTRL+Y|스크립트 창, 콘솔 창|
|**스크립트에서 바꾸기**|CTRL+H|스크립트 창|
|**저장**|Ctrl+S|스크립트 창|
|**모두 선택**|CTRL+A|스크립트 창, 콘솔 창|
|**실행 취소**|CTRL+Z|스크립트 창, 콘솔 창|

## <a name="keyboard-shortcuts-for-running-scripts"></a>스크립트 실행 바로 가기 키

스크립트 창에서 스크립트를 실행할 때 다음과 같은 바로 가기 키를 사용할 수 있습니다.

|작업|바로 가기 키|
|----------|---------------------|
|**새로 만들기**|CTRL+N|
|**열기**|CTRL+O|
|**실행**|F5|
|**선택 항목 실행**|F8|
|**실행 중지**|CTRL+BREAK 컨텍스트가 명확한 경우(선택한 텍스트가 없는 경우) Ctrl+C를 사용할 수 있습니다.|
|**Tab** 키를 눌러 다음 스크립트로 이동|CTRL+TAB **참고:** Tab 키를 눌러 다음 스크립트로 이동은 하나의 PowerShell 탭만 열려 있는 경우 또는 둘 이상의 PowerShell 탭이 열려 있지만 스크립트 창에 포커스가 있는 경우에 작동합니다.|
|**Tab** 키를 눌러 이전 스크립트로 이동|CTRL+SHIFT+TAB **참고:** Tab 키를 눌러 이전 스크립트로 이동은 하나의 PowerShell 탭만 열려 있는 경우 또는 둘 이상의 PowerShell 탭이 열려 있고 스크립트 창에 포커스가 있는 경우에 작동합니다.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>보기 사용자 지정 바로 가기 키

Windows PowerShell ISE에서 보기를 사용자 지정할 때 다음과 같은 바로 가기 키를 사용할 수 있습니다. 애플리케이션의 모든 창에서 액세스할 수 있습니다.

|작업|바로 가기 키|
|----------|---------------------|
|**콘솔 창으로 이동**|CTRL+D|
|**스크립트 창으로 이동**|CTRL+I|
|**스크립트 창 표시**|CTRL+R|
|**스크립트 창 숨기기**|CTRL+R|
||
|**스크립트 창 위로 이동**|CTRL+1|
|**스크립트 창 오른쪽으로 이동**|CTRL+2|
|**스크립트 창 최대화**|CTRL+3|
|**확대**|CTRL+더하기 기호|
|**축소**|CTRL+빼기 기호|

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>스크립트 디버그 바로 가기 키

스크립트를 디버그할 때 다음과 같은 바로 가기 키를 사용할 수 있습니다.

|작업|바로 가기 키|사용 위치|
|----------|---------------------|----------|
|**실행/계속**|F5|스크립트 창, 스크립트를 디버그할 때|
|**한 단계씩 코드 실행**|F11|스크립트 창, 스크립트를 디버그할 때|
|**프로시저 단위 실행**|F10|스크립트 창, 스크립트를 디버그할 때|
|**프로시저 나가기**|SHIFT+F11|스크립트 창, 스크립트를 디버그할 때|
|**호출 스택 표시**|CTRL+SHIFT+D|스크립트 창, 스크립트를 디버그할 때|
|**중단점 표시**|CTRL+SHIFT+L|스크립트 창, 스크립트를 디버그할 때|
|**중단점 설정/해제**|F9|스크립트 창, 스크립트를 디버그할 때|
|**모든 중단점 제거**|CTRL+SHIFT+F9|스크립트 창, 스크립트를 디버그할 때|
|**디버거 중지**|SHIFT+F5|스크립트 창, 스크립트를 디버그할 때|

> [!NOTE]
>
> Windows PowerShell ISE에서 스크립트를 디버그할 때 Windows PowerShell 콘솔용으로 설계된 바로 가기 키를 사용할 수도 있습니다. 이러한 바로 가기를 사용하려면 콘솔 창에서 바로 가기를 입력하고 Enter 키를 눌러야 합니다.

|작업|바로 가기 키|사용 위치|
|----------|---------------------|----------|
|**계속**|C|콘솔 창, 스크립트를 디버그할 때|
|**한 단계씩 코드 실행**|S|콘솔 창, 스크립트를 디버그할 때|
|**프로시저 단위 실행**|V|콘솔 창, 스크립트를 디버그할 때|
|**프로시저 나가기**|O|콘솔 창, 스크립트를 디버그할 때|
|**마지막 명령 반복**(한 단계씩 코드 실행 또는 프로시저 단위 실행)|Enter 키|콘솔 창, 스크립트를 디버그할 때|
|**호출 스택 표시**|K|콘솔 창, 스크립트를 디버그할 때|
|**디버깅 중지**|Q|콘솔 창, 스크립트를 디버그할 때|
|**스크립트 표시**|L|콘솔 창, 스크립트를 디버그할 때|
|**콘솔 디버깅 명령 표시**|H 또는 ?|콘솔 창, 스크립트를 디버그할 때|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Windows PowerShell 탭 바로 가기 키

Windows PowerShell 탭을 사용할 때 다음과 같은 바로 가기 키를 사용할 수 있습니다.

|작업|바로 가기 키|
|----------|---------------------|
|**PowerShell 탭 닫기**|CTRL+W|
|**새 PowerShell 탭**|CTRL+T|
|**이전 PowerShell 탭**|CTRL+SHIFT+TAB. 이 바로 가기는 PowerShell 탭에 열려 있는 파일이 없는 경우에만 작동합니다.|
|**다음 Windows PowerShell 탭**|CTRL+TAB. 이 바로 가기는 PowerShell 탭에 열려 있는 파일이 없는 경우에만 작동합니다.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>시작 및 종료 바로 가기 키

다음과 같은 바로 가기 키를 사용하여 Windows PowerShell 콘솔(PowerShell.exe)을 시작하거나 Windows PowerShell ISE를 종료할 수 있습니다.

|작업|바로 가기 키|
|----------|---------------------|
|**종료**|Alt+F4|
|**PowerShell.exe 시작** (Windows PowerShell 콘솔)|CTRL+SHIFT+P|

## <a name="see-also"></a>참고 항목

[Windows PowerShell ISE 소개](Introducing-the-Windows-PowerShell-ISE.md)
