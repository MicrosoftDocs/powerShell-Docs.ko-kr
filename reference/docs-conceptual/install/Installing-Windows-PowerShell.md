---
ms.date: 08/09/2017
keywords: powershell,cmdlet,다운로드,설치,설정,windows 10, windows 8.1, windows 8.0,windows 7
title: Windows PowerShell 설치
ms.openlocfilehash: 345cde8012bece730e7217ed16be6175ad26bb28
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62086479"
---
# <a name="installing-windows-powershell"></a>Windows PowerShell 설치

Windows PowerShell은 Windows 7 SP1 및 Windows Server 2008 R2 SP1부터 모든 Windows에 기본적으로 설치되어 제공됩니다.

PowerShell 6 이상에 관심이 있는 경우 Windows PowerShell 대신 PowerShell Core를 설치해야 합니다. 이 경우 [Windows에서 PowerShell Core 설치](Installing-PowerShell-Core-on-Windows.md)를 참조하세요.

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>Windows 10, 8.1, 8.0 및 7에서 PowerShell 찾기

Windows 버전에 따라 위치가 바뀌므로 때때로 Windows에서 PowerShell 콘솔 또는 ISE(통합 스크립팅 환경)를 찾기가 어려울 수 있습니다.

다음 표는 사용 중인 Windows 버전에서 PowerShell을 찾는 데 도움이 됩니다.
여기에 나열된 모든 버전은 업데이트가 포함되지 않은 릴리스된 원래 버전입니다.

### <a name="for-console"></a>콘솔의 경우

버전 | 위치
-- | --
Windows 10 | 왼쪽 아래 모서리에 있는 Windows 아이콘을 클릭하고 PowerShell 입력을 시작합니다.
Windows 8.1, 8.0 | 시작 화면에서 PowerShell 입력을 시작합니다.<br/>바탕 화면에 있는 경우 왼쪽 아래 모서리에 있는 Windows 아이콘을 클릭하고 PowerShell 입력을 시작합니다.
Windows 7 SP1 | 왼쪽 아래 모서리에 있는 Windows 아이콘을 클릭하고 검색 상자에서 PowerShell 입력을 시작합니다.

### <a name="for-ise"></a>ISE의 경우

버전 | 위치
-- | --
Windows 10 | 왼쪽 아래 모서리에 있는 Windows 아이콘을 클릭하고 ISE 입력을 시작합니다.
Windows 8.1, 8.0 | 시작 화면에서 **PowerShell ISE**를 입력합니다.<br/>바탕 화면에 있는 경우 왼쪽 아래 모서리에 있는 Windows 아이콘을 클릭하고 **PowerShell ISE**를 입력합니다.
Windows 7 SP1 | 왼쪽 아래 모서리에 있는 Windows 아이콘을 클릭하고 검색 상자에서 PowerShell 입력을 시작합니다.

## <a name="finding-powershell-in-windows-server-versions"></a>Windows Server 버전에서 PowerShell 찾기

Windows Server 2008 R2부터 GUI(그래픽 사용자 인터페이스) 없이 Windows 운영 체제를 설치할 수 있습니다.
GUI가 없는 Windows Server 버전은 이름이 **Core** 버전으로 지정되고 GUI가 있는 버전은 이름이 **Desktop**으로 지정됩니다.

### <a name="windows-server-core-editions"></a>Windows Server Core 버전

모든 Core 버전에서는 서버에 로그온하면 Windows 명령 프롬프트 창이 표시됩니다.

`powershell`을 입력하고 **Enter** 키를 눌러 명령 프롬프트 세션 내에서 PowerShell을 시작합니다.
`exit`를 입력하여 PowerShell 세션을 종료하고 명령 프롬프트로 돌아갑니다.

### <a name="windows-server-desktop-editions"></a>Windows Server Desktop 버전

모든 Desktop 버전에서는 왼쪽 아래 모서리에 있는 Windows 아이콘을 클릭하고 PowerShell 입력을 시작합니다.
콘솔 및 ISE 옵션을 모두 이용할 수 있습니다.

위 규칙에 대한 유일한 예외는 Windows Server 2008 R2 SP1의 ISE입니다. 이 경우에는 왼쪽 아래 모서리에 있는 Windows 아이콘을 클릭하고 PowerShell ISE를 입력합니다.

## <a name="how-to-check-the-version-of-powershell"></a>PowerShell 버전을 확인하는 방법

설치한 PowerShell 버전을 찾으려면 PowerShell 콘솔(또는 ISE)을 시작하고 `$PSVersionTable`을 입력한 다음 **Enter** 키를 누릅니다. `PSVersion` 값을 찾습니다.

## <a name="upgrading-existing-windows-powershell"></a>기존 Windows PowerShell 업그레이드

PowerShell 설치 패키지는 WMF 설치 관리자 내에 제공됩니다.
WMF 설치 관리자 버전은 PowerShell 버전과 일치합니다. Windows PowerShell용 독립 실행형 설치 관리자는 없습니다.

Windows에서 기존 PowerShell 버전을 업데이트해야 할 경우 다음 표를 사용하여 업데이트하려는 PowerShell 버전의 설치 관리자를 찾습니다.

Windows | PS 3.0 | PS 4.0 | PS 5.0 | PS 5.1 |
--|--|--|--|--|
Windows 10(참고 1 참조)<br/>Windows Server 2016 | - | - | - | 설치됨
Windows 8.1<br/>Windows Server 2012 R2 | - | 설치됨 | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 8<br/>Windows Server 2012 | 설치됨 | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 7 SP1<br/>Windows Server 2008 R2 SP1 | [WMF 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> [!NOTE]
>
> 자동으로 업데이트되도록 설정된 Windows 10의 초기 릴리스에서는 PowerShell이 버전 5.0에서 5.1로 업데이트됩니다.
>
> Windows 업데이트를 통해 Windows 10의 원래 버전이 업데이트되지 않으면 PowerShell 버전은 5.0입니다.

## <a name="need-azure-powershell"></a>Azure PowerShell 필요

**Azure PowerShell**을 찾는 경우 [Overview of Azure PowerShell](/powershell/azure/overview)(Azure PowerShell 개요)에서 시작할 수 있습니다.

그러지 않으면 [Install and configure Azure PowerShell](/powershell/azure/install-az-ps)(Azure PowerShell 설치 및 구성)이 필요할 수 있습니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 시스템 요구 사항](Windows-PowerShell-System-Requirements.md)

[Windows PowerShell 시작](../getting-started/Starting-Windows-PowerShell.md)
