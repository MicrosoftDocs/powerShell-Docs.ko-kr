---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 2.0 엔진 설치
ms.openlocfilehash: a2b78755e7e44e2523baee5477fadc94eab485b1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030970"
---
# <a name="installing-the-windows-powershell-20-engine"></a>Windows PowerShell 2.0 엔진 설치
이 항목에서는 Windows PowerShell 2.0 엔진을 설치하는 방법을 설명합니다.

Windows PowerShell 3.0은 이전 버전인 Windows PowerShell 2.0과 호환되도록 설계되었습니다. Windows PowerShell 2.0 및 Windows PowerShell 3.0용으로 작성된 cmdlet, 공급자, 스냅인, 모듈 및 스크립트는 Windows PowerShell 4.0에서 변경하지 않고 실행됩니다. 그러나 Microsoft .NET Framework 4의 런타임 정품 인증 정책 변경으로 인해 Windows PowerShell 2.0용으로 작성되고 CLR(공용 언어 런타임) 2.0으로 컴파일된 Windows PowerShell 호스트 프로그램은 CLR 4.0으로 컴파일된 Windows PowerShell의 이후 릴리스에서 수정 없이 실행할 수 없습니다.

이러한 변경의 영향을 받는 이전 버전의 명령 및 호스트 프로그램과 호환성을 유지하기 위해 Windows PowerShell 2.0, Windows PowerShell 3.0 및 Windows PowerShell 4.0 엔진은 나란히 실행되도록 설계되었습니다. 또한 Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012 및 Windows Management Framework 3.0에는 Windows PowerShell 2.0 엔진이 포함되어 있습니다. Windows PowerShell 2.0 엔진은 기존 스크립트 또는 호스트 프로그램이 Windows PowerShell 3.0, Windows PowerShell 4.0 또는 Microsoft .NET Framework 4와 호환되지 않아 실행할 수 없는 경우에만 사용됩니다. 이러한 경우는 많지 않을 것으로 예상됩니다.

Windows PowerShell 2.0 엔진은 Windows Server 2012 R2, Windows 8.1, Windows® 8 및 Windows Server® 2012의 선택적 기능입니다. 이전 버전의 Windows에서 Windows Management Framework 3.0을 설치하면 Windows PowerShell 3.0 설치가 Windows PowerShell 설치 디렉터리의 Windows PowerShell 2.0 설치를 완전히 바꿉니다. 그러나 Windows PowerShell 2.0 엔진은 유지됩니다.

Windows PowerShell 2.0 엔진을 시작하는 방법에 대한 자세한 내용은 [Windows PowerShell 2.0 엔진 시작](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md)을 참조하세요.

## <a name="on-windows-81-and-windows-8"></a>Windows 8.1 및 Windows 8에서
Windows 8.1 및 Windows 8에서는 Windows PowerShell 2.0 엔진 기능이 기본적으로 설정되어 있습니다. 그러나 이 기능을 사용하려면 필요한 Microsoft .NET Framework 3.5에 대한 옵션을 설정해야 합니다. 이 섹션에서는 Windows PowerShell 2.0 엔진 기능을 설정 및 해제하는 방법도 설명합니다.

#### <a name="to-turn-on-net-framework-35"></a>.NET Framework 3.5를 설정하려면

1. **시작** 화면에서 **Windows 기능**을 입력합니다.

2. **앱** 바에서 **설정**을 클릭한 다음 **Windows 기능 설정 또는 해제**를 클릭합니다.

3. **Windows 기능** 상자에서 **.NET Framework 3.5(.NET 2.0 및 3.0 포함)** 을 클릭하여 선택합니다.

    **.NET Framework 3.5(.NET 2.0 및 3.0 포함)** 를 선택하면 상자가 채워져 기능의 일부만 선택되었음을 나타냅니다. 그러나 Windows PowerShell 2.0 엔진에는 이것만으로 충분합니다.

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a>Windows PowerShell 2.0 엔진을 설정 및 해제하려면

1. **시작** 화면에서 **Windows 기능**을 입력합니다.

2. **앱** 바에서 **설정**을 클릭한 다음 **Windows 기능 설정 또는 해제**를 클릭합니다.

3. **Windows 기능** 상자에서 **Windows PowerShell 2.0** 노드를 확장하고 **Windows PowerShell 2.0 엔진** 상자를 클릭하여 선택하거나 선택을 취소합니다.

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a>Windows Server 2012 R2 및 Windows Server 2012에서
Windows PowerShell 2.0 엔진과 Microsoft .NET Framework 3.5 기능을 추가하려면 다음 절차를 따르세요. Windows PowerShell 2.0 엔진에는 최소한 Microsoft .NET Framework 2.0.50727이 필요합니다. 이 요구 사항은 Microsoft .NET Framework 3.5에 의해 충족됩니다.

#### <a name="to-add-the-net-framework-35-feature"></a>.NET Framework 3.5 기능을 추가하려면

1. **서버 관리자**의 **관리** 메뉴에서 **역할 및 기능 추가**를 선택합니다.

    또는 **서버 관리자**에서 **모든 서버**를 클릭하고 서버 이름 마우스 오른쪽 단추로 클릭한 다음 **역할 및 기능 추가**를 선택합니다.

2. **설치 유형** 페이지에서 **역할 기반 또는 기능 기반 설치**를 선택합니다.

3. **기능** 페이지에서 **.NET 3.5 Framework 기능** 노드를 확장하고 **.NET Framework 3.5(.NET 2.0 및 3.0 포함)** 를 선택합니다.

    해당 노드 아래에 있는 다른 옵션은 Windows PowerShell 2.0 엔진에 필요하지 않습니다.

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a>Windows PowerShell 2.0 엔진 기능을 추가하려면

- **서버 관리자**의 **관리** 메뉴에서 **역할 및 기능 추가**를 선택합니다.

    또는 **서버 관리자**에서 **모든 서버**를 클릭하고 서버 이름 마우스 오른쪽 단추로 클릭한 다음 **역할 및 기능 추가**를 선택합니다.

- **설치 유형** 페이지에서 **역할 기반 또는 기능 기반 설치**를 선택합니다.

- **기능** 페이지에서 **Windows PowerShell(설치됨)** 노드를 확장하고 **Windows PowerShell 2.0 엔진**을 선택합니다.

Windows PowerShell 2.0 엔진을 시작하는 방법에 대한 자세한 내용은 [Windows PowerShell 2.0 엔진 시작](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md)을 참조하세요.

## <a name="on-earlier-systems"></a>이전 시스템
Windows 7, Windows Server 2008 R2 및 Windows Server 2012에 Windows PowerShell 4.0을 설치하는 [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) 패키지에는 Windows PowerShell 2.0 엔진이 포함되어 있습니다. 추가 설치, 설정 또는 구성 없이 Windows PowerShell 2.0 엔진을 사용할 수 있고 사용할 준비가 됩니다.

Windows 7, Windows Server 2008 R2 및 Windows Server 2008에 Windows PowerShell 3.0을 설치하는 Windows Management Framework 3.0 패키지에는 Windows PowerShell 2.0 엔진이 포함되어 있습니다. 추가 설치, 설정 또는 구성 없이 Windows PowerShell 2.0 엔진을 사용할 수 있고 사용할 준비가 됩니다.

## <a name="see-also"></a>참고 항목
- [Windows PowerShell 시스템 요구 사항](Windows-PowerShell-System-Requirements.md)
- [Windows PowerShell 설치](Installing-Windows-PowerShell.md)
- [Windows PowerShell 시작](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
- [Windows PowerShell 2.0 엔진 시작](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md)
