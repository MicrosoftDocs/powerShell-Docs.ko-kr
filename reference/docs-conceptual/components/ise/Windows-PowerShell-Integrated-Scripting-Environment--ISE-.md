---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell ISE(통합 스크립팅 환경)
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
ms.openlocfilehash: 3002c2cb7213b1c2d7201dddf5ff3c0651fad767
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054716"
---
# <a name="windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell ISE(통합 스크립팅 환경)

Windows PowerShell ISE(통합 스크립팅 환경)는 Windows PowerShell 엔진 및 언어에 대한 두 호스트 중 하나입니다. ISE를 통해 Windows PowerShell 콘솔에서는 사용할 수 없는 방식으로 스크립트를 작성, 실행 및 테스트할 수 있습니다. ISE는 색 구문 지정, 탭 완성, IntelliSense, 시각적 디버깅 및 상황에 맞는 도움말을 추가합니다.

ISE를 사용하면 콘솔 창에서 명령을 실행할 수 있지만 스크립트의 소스 코드와 ISE에 연결할 수 있는 다른 도구를 동시에 보는 데 사용할 수 있는 창도 지원됩니다. 동시에 여러 스크립트 창을 열 수도 있으며, 이 기능은 다른 스크립트나 모듈에서 정의된 함수를 사용하는 스크립트를 디버그할 때 특히 유용합니다.

## <a name="whats-new"></a>새로운 기능

다음은 최신 PowerShell 릴리스의 ISE에 추가된 몇 가지 기능입니다.

### <a name="added-in-powershell-30-windows-server-2012-windows-8"></a>PowerShell 3.0에서 추가되었습니다(Windows Server 2012, Windows 8).

**Intellisense**는 입력하는 동안 일치하는 cmdlet, 매개 변수, 매개 변수 값, 파일 또는 폴더 메뉴를 표시하여 명령을 자동으로 완성합니다.

**코드 조각**은 작성하는 스크립트에 쉽게 삽입할 수 있는 코드의 짧은 섹션입니다. 유용한 코드 조각 컬렉션이 상자에 포함되어 있으며, **New-Snippet** cmdlet을 사용하여 더 만들 수 있습니다.

[Windows PowerShell ISE 스크립팅 개체 모델](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md)과 상호 작용하는 코드를 작성하여 ISE에 기능을 추가하는 **추가 기능 도구**를 만들 수 있습니다.

이러한 도구는 탭 창에 컨트롤을 표시하거나 백그라운드에서 보이지 않게 작업할 수 있습니다. **명령** 추가 기능은 좋은 예이며, 버전 3.0 이상에 포함되어 사용 가능한 명령 목록과 해당 도움말을 표시합니다.

**다시 시작 관리자 및 자동 저장**은 크래시가 발생하거나 예기치 않게 다시 시작될 경우 작업이 손실되지 않도록 2분마다 스크립트를 자동으로 저장합니다.

이제 자주 사용하는 파일에 쉽게 액세스할 수 있도록 **가장 최근에 사용한 목록**이 파일 열기 메뉴에 포함되었습니다.

**병합된 콘솔 창**. 이전 버전의 ISE에서는 별개의 명령 창과 출력 창이 있었습니다. 이제 Windows PowerShell 콘솔에 표시되는 방식과 더 유사한 단일 창으로 결합되었습니다.

**명령줄 스위치**. 몇 가지 새로운 명령줄 스위치를 통해 ISE 작동 방식을 보다 자세히 제어할 수 있습니다. -NoProfile은 프로필 스크립트를 실행하지 않고 ISE를 시작합니다. –Help는 ISE를 사용하여 도움말 창을 엽니다. –mta는 "다중 스레드 아파트 모드"로 ISE를 시작합니다. 기본값은 단일 스레드입니다.

**새 편집기 기능**을 사용하면 더 쉽게 코드를 만들고 읽을 수 있습니다.

- **XML 구문 색 지정**. 이제 ISE 편집기에서 Windows PowerShell 구문에 색을 지정하는 것과 동일한 방법으로 XML 구문에 색을 지정합니다.

- **중괄호 일치**. ISEWindows PowerShell ISE는 여는 중괄호 수와 닫는 중괄호 수가 일치하도록, 일치하는 중괄호를 강조 표시합니다. Ctrl-\[를 사용하면 커서가 있는 여는 중괄호와 일치하는 닫는 중괄호를 찾을 수 있습니다.

- **개요 보기**. 왼쪽 여백에서 더하기 및 빼기 기호를 클릭하여 코드 섹션을 확장하거나 축소할 수 있습니다. 이렇게 하면 긴 스크립트에서 원하는 코드를 더 쉽게 찾을 수 있습니다.

- **텍스트 끌어서 놓기**. 텍스트 블록을 선택한 후 다른 위치로 끌어서 이동할 수 있습니다. Ctrl 키를 누른 채 선택한 텍스트를 끌면 이동되지 않고 복사됩니다.

- **구문 분석 오류 표시**. 입력할 때 Windows PowerShell에서 스크립트를 검사합니다. 오류가 검색되면 문제를 일으키는 코드 아래에 빨간색 물결 무늬가 표시됩니다. 표시된 오류를 마우스로 가리키면 발견된 문제가 도구 설명에 표시됩니다.

- **확대/축소**. 텍스트를 확대하여 읽기 쉽게 만들거나, 축소하여 ISE 창의 오른쪽 아래에 있는 슬라이더를 통해 전체적인 내용을 확인할 수 있습니다.

- **서식 있는 텍스트 복사 및 붙여넣기**. ISE에서 클립보드로 복사하는 경우 선택한 텍스트의 글꼴, 크기 및 색 정보가 포함됩니다.

- **블록 선택**. Alt 키를 누른 채 스크립트 창에서 마우스로 텍스트를 선택하거나 **Alt+Shift+화살표**를 눌러 블록 모양의 텍스트를 선택할 수 있습니다.

### <a name="added-in-powershell-20-windows-server-2008-r2-windows-7"></a>PowerShell 2.0에서 추가되었습니다(Windows Server 2008 R2, Windows 7).

ISE는 PowerShell v2.0에서 도입되었습니다.

## <a name="requirements-for-running-the-windows-powershell-ise"></a>Windows PowerShell ISE 실행을 위한 요구 사항

ISE는 Windows PowerShell v2.0 이상을 실행할 수 있는 모든 Windows 컴퓨터에서 사용할 수 있습니다. 각 버전의 Windows 및 Windows Server에는 특정 버전의 Windows PowerShell 및 ISE가 포함되어 있지만 WMF(Windows Management Framework)를 설치하여 사용 가능한 최신 버전으로 업그레이드할 수 있습니다. 자세한 내용은 [WMF](/powershell/wmf) 설명서를 참조하세요.

> [!NOTE]
> Windows PowerShell ISE에는 그래픽 사용자 인터페이스가 필요하므로 Windows Server의 Server Core 옵션에서 실행할 수 없습니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell ISE 스크립팅 개체 모델의 용도](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)