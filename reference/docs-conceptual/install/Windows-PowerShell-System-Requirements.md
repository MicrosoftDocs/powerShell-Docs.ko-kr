---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 시스템 요구 사항
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
ms.openlocfilehash: a9a7dc434d26876d6747526ad3ef6fa598376ac1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058306"
---
# <a name="windows-powershell-system-requirements"></a>Windows PowerShell 시스템 요구 사항
이 항목에서는 Windows PowerShell 3.0, Windows PowerShell 4.0, Windows PowerShell 5.0 및 Windows PowerShell 5.1과 특수 기능(예: Windows PowerShell ISE(통합 스크립팅 환경), CIM 명령 및 워크플로)에 대한 시스템 요구 사항을 보여 줍니다.

Windows® 8.1 및 Windows Server® 2012 R2에는 필요한 모든 프로그램이 포함되어 있습니다. 이 항목은 이전 버전의 Windows 사용자를 위한 것입니다.

## <a name="operating-system-requirements"></a>운영 체제 요구 사항
Windows PowerShell 5.1은 다음 버전의 Windows에서 실행됩니다.

- Windows Server 2019, 기본적으로 설치됨

- Windows Server 2016, 기본적으로 설치됨

- Windows Server 2012 R2, Windows PowerShell 5.1을 실행하려면 [Windows Management Framework 5.1](https://aka.ms/wmf5download) 설치

- Windows Server 2012, Windows PowerShell 5.0을 실행하려면 [Windows Management Framework 5.1](https://aka.ms/wmf5download) 설치

- Windows Server 2008 R2 서비스 팩 1, Windows PowerShell 5.1을 실행하려면 [Windows Management Framework 5.1](https://aka.ms/wmf5download) 설치

- Windows 10 버전 1607 이상 - 기본적으로 설치됨

- Windows 10 버전 1507, 1511 - Windows PowerShell 5.1을 실행하려면 [Windows Management Framework 5.1](https://aka.ms/wmf5download) 설치

- Windows 8.1, Windows PowerShell 5.1을 설치하려면 [Windows Management Framework 5.1](https://aka.ms/wmf5download) 설치

- Windows 7 서비스 팩 1, Windows PowerShell 5.1을 실행하려면 [Windows Management Framework 5.1](https://aka.ms/wmf5download) 설치

Windows PowerShell 5.0(Windows PowerShell 5.1 이전 버전) 은 다음 버전의 Windows에서 실행됩니다.

- Windows Server 2019, 이후 버전이 기본적으로 설치됨

- Windows Server 2016, 이후 버전이 기본적으로 설치됨

- Windows Server 2012 R2, Windows PowerShell 5.0을 실행하려면 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 설치

- Windows Server 2012, Windows PowerShell 5.0을 실행하려면 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 설치

- Windows Server 2008 R2 서비스 팩 1, Windows PowerShell 5.0을 실행하려면 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 설치

- Windows 10 버전 1607 이상 - 이후 버전이 기본적으로 설치됨

- Windows 10 버전 1507, 1511 - 기본적으로 설치됨

- Windows 8.1, Windows PowerShell 5.0을 실행하려면 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 설치

- Windows 7 서비스 팩 1, Windows PowerShell 5.0을 실행하려면 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 설치

Windows PowerShell 4.0은 다음 버전의 Windows에서 실행됩니다.

- Windows 8.1, 기본적으로 설치됨

- Windows Server 2012 R2, 기본적으로 설치됨

- Windows® 7 서비스 팩 1, Windows PowerShell 4.0을 실행하려면 [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) 설치

- Windows Server® 2008 R2 서비스 팩 1, Windows PowerShell 4.0을 실행하려면 [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) 설치

Windows PowerShell 3.0은 다음 버전의 Windows에서 실행됩니다.

- Windows 8, 기본적으로 설치됨

- Windows Server 2012, 기본적으로 설치됨

- Windows® 7 서비스 팩 1, Windows PowerShell 3.0을 실행하려면 [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) 설치

- Windows Server® 2008 R2 서비스 팩 1, Windows PowerShell 3.0을 실행하려면 [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) 설치

- Windows Server 2008 서비스 팩 2, Windows PowerShell 3.0을 실행하려면 [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) 설치

## <a name="microsoft-net-framework-requirements"></a>Microsoft .NET Framework 요구 사항
Windows PowerShell 5.1을 사용하려면 Microsoft .NET Framework 4.5 전체 설치가 필요합니다. Windows 8.1 및 Windows Server 2012 R2에는 Microsoft .NET Framework 4.5가 기본적으로 포함되어 있습니다.

Windows PowerShell 5.0을 사용하려면 Microsoft .NET Framework 4.5 전체 설치가 필요합니다. Windows 8.1 및 Windows Server 2012 R2에는 Microsoft .NET Framework 4.5가 기본적으로 포함되어 있습니다.

Windows PowerShell 4.0을 사용하려면 Microsoft .NET Framework 4.5 전체 설치가 필요합니다. Windows 8.1 및 Windows Server 2012 R2에는 Microsoft .NET Framework 4.5가 기본적으로 포함되어 있습니다.

Windows PowerShell 3.0을 사용하려면 Microsoft .NET Framework 4 전체 설치가 필요합니다. Windows 8 및 Windows Server 2012에는 이 요구 사항을 충족하는 Microsoft .NET Framework 4.5가 기본적으로 포함되어 있습니다.

Microsoft .NET Framework 4.5(dotNetFx45_Full_setup.exe)를 설치하려면 Microsoft 다운로드 센터에서 [Microsoft .NET Framework 4.5](https://go.microsoft.com/fwlink/?LinkID=242919)를 참조하세요.

Microsoft .NET Framework 4 전체 설치(dotNetFx40_Full_setup.exe)를 설치하려면 Microsoft 다운로드 센터에서 [Microsoft .NET Framework 4(웹 설치 관리자)](https://go.microsoft.com/fwlink/?LinkID=212931)를 참조하세요.

## <a name="windows-management-framework-40"></a>Windows Management Framework 4.0
Windows PowerShell 5.0을 사용하려면 Windows Server 2008 R2 SP1 및 Windows 7 SP1에 Windows Management Framework 4.0이 미리 설치되어 있어야 합니다.

## <a name="ws-management-30"></a>WS-Management 3.0
Windows PowerShell 3.0 및 Windows PowerShell 4.0을 사용하려면 WinRM 서비스 및 WSMan 프로토콜을 지원하는 WS-Management 3.0이 필요합니다. 이 프로그램은 Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 및 Windows Management Framework 3.0에 포함되어 있습니다.

## <a name="windows-management-instrumentation-30"></a>Windows Management Instrumentation 3.0
Windows PowerShell 3.0 및 Windows PowerShell 4.0을 사용하려면 WMI(Windows Management Instrumentation) 3.0이 필요합니다. 이 프로그램은 Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 및 Windows Management Framework 3.0에 포함되어 있습니다. 이 프로그램이 컴퓨터에 설치되어 있지 않으면 WMI가 필요한 기능(예: CIM 명령)이 실행되지 않습니다.

## <a name="common-language-runtime-40"></a>공용 언어 런타임 4.0
Windows PowerShell 3.0, Windows PowerShell 4.0 및 Windows PowerShell 5.0은 CLR(공용 언어 런타임) 4.0에 대해 컴파일됩니다.

## <a name="graphical-user-interface-requirements"></a>그래픽 사용자 인터페이스 요구 사항
Windows PowerShell은 그래픽 사용자 인터페이스를 요구하지 않는 콘솔 기반 애플리케이션입니다. 따라서 Windows Server 2012 R2 또는 Windows Server 2012의 Server Core 설치 옵션과 같이 화면 또는 모니터나 사용자 인터페이스가 없는 컴퓨터에 적합합니다.

그러나 다음과 같은 일부 항목에는 그래픽 사용자 인터페이스가 필요합니다. 자세한 내용은 각 항목에 대한 도움말 항목을 참조하세요.

- Windows PowerShell ISE(통합 스크립팅 환경)

- Cmdlet

    1.  [Out-GridView](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview)

    2.  [Show-Command](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Show-Command)

    3.  [Show-ControlPanelItem](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)

    4.  [Show-EventLog](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)

- 매개 변수

    1.  [Get-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet의 **ShowWindow** 매개 변수

    2.  [Register-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) 및 [Set-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration) cmdlet의 **ShowSecurityDescriptorUI** 매개 변수

## <a name="windows-powershell-engine-requirements"></a>Windows PowerShell 엔진 요구 사항
Windows PowerShell 4.0은 이전 버전인 Windows PowerShell 3.0 및 Windows PowerShell 2.0과 호환되도록 설계되었습니다. Windows PowerShell 2.0 및 Windows PowerShell 3.0용으로 작성된 cmdlet, 공급자, 스냅인, 모듈 및 스크립트는 Windows PowerShell 4.0에서 변경하지 않고 실행됩니다.

그러나 Microsoft .NET Framework 4의 런타임 정품 인증 정책 변경으로 인해 Windows PowerShell 2.0용으로 작성되고 CLR(공용 언어 런타임) 2.0으로 컴파일된 Windows PowerShell 호스트 프로그램은 CLR 4.0으로 컴파일된 Windows PowerShell 3.0에서 수정 없이 실행할 수 없습니다.

Windows PowerShell 2.0 엔진에는 최소한 Microsoft .NET Framework 2.0.50727이 필요합니다. 이 요구 사항은 Microsoft .NET Framework 3.5 서비스 팩 1에 의해 충족됩니다. Microsoft .NET Framework 4 이상 릴리스의 Microsoft .NET Framework에서는 이 요구 사항이 충족되지 않습니다.

Windows PowerShell 2.0 엔진을 추가 또는 설치하는 방법과 필수 버전의 Microsoft .NET Framework를 추가 또는 설치하는 방법에 대한 자세한 내용은 [Windows PowerShell 2.0 엔진 설치](Installing-the-Windows-PowerShell-2.0-Engine.md)를 참조하세요. Windows PowerShell 2.0 엔진을 시작하는 방법에 대한 자세한 내용은 [Windows PowerShell 2.0 엔진 시작](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md)을 참조하세요.

## <a name="windows-preinstallation-environment"></a>Windows 사전 설치 환경
Windows PowerShell 2.0, Windows PowerShell 3.0 및 Windows PowerShell 4.0은 Winows PE(Windows 사전 설치 환경)에서 실행됩니다. 그러나 다음 cmdlet은 지원되지 않습니다.

- [BITS(Background Intelligent Transfer Service) cmdlet](https://go.microsoft.com/fwlink/?LinkId=257514)

- [Get-EventLog](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)

- [Get-WinEvent](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)

- [Save-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Save-Help)

- [Update-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Update-Help)

또한 Windows PE에는 **WinRM** 서비스가 없습니다.

## <a name="see-also"></a>참고 항목
- [Windows PowerShell 시작](../getting-started/Getting-Started-with-Windows-PowerShell.md)
- [Windows PowerShell 설치](Installing-Windows-PowerShell.md)
- [Windows PowerShell 시작](../getting-started/Starting-Windows-PowerShell.md)
