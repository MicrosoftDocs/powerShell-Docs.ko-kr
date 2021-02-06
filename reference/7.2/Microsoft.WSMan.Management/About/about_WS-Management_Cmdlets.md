---
description: Windows PowerShell에서 WS-Management cmdlet을 사용 하기 위한 배경으로 WS-MANAGEMENT (Web Services for Management)에 대 한 개요를 제공 합니다.
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WS Management_Cmdlets
ms.openlocfilehash: faf0f0b08d604f7568ac316557788eea21feea8d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600450"
---
# <a name="about-ws-management-cmdlets"></a>WS-Management Cmdlet 정보

## <a name="short-description"></a>간단한 설명

Windows PowerShell에서 WS-Management cmdlet을 사용 하기 위한 배경으로 WS-MANAGEMENT (Web Services for Management)에 대 한 개요를 제공 합니다.

## <a name="long-description"></a>자세한 설명

이 항목에서는 Windows PowerShell에서 WS-Management cmdlet을 사용 하기 위한 배경으로 WS-MANAGEMENT (Web Services for Management)에 대 한 개요를 제공 합니다. 또한이 항목에서는 WS-MANAGEMENT에 대 한 자세한 정보를 제공 하는 링크를 제공 합니다. WS-Management의 Microsoft 구현은 WinRM (Windows 원격 관리)이 라고도 합니다.

## <a name="about-ws-management"></a>WS-Management 정보

Windows 원격 관리는 서로 다른 공급 업체의 하드웨어 및 운영 체제를 상호 운용할 수 있도록 하는 표준 SOAP 기반 방화벽 친화적인 프로토콜인 WS-Management 프로토콜의 Microsoft 구현입니다. WS-Management 프로토콜 사양은 시스템에서 IT (정보 기술) 인프라를 통해 관리 정보에 액세스 하 고 교환할 수 있는 일반적인 방법을 제공 합니다. WS-Management 및 IPMI (Intelligent Platform Management Interface)는 이벤트 수집기와 함께 Windows 하드웨어 관리 기능의 구성 요소입니다.

WS-Management 프로토콜은 다음 표준 웹 서비스 사양을 기반으로 합니다. HTTPS, SOAP over HTTP (WS-I profile), SOAP 1.2, WS-ADDRESSING, WS-TRUST, WS-FEDERATION 및 WS 이벤트입니다.

## <a name="ws-management-and-wmi"></a>WS-Management 및 WMI

WS-Management은 WMI (WMI(Windows Management Instrumentation))에서 제공 하는 데이터를 검색 하는 데 사용할 수 있습니다. WS-Management 스크립팅 API 또는 WinRM 명령줄 도구를 사용 하는 스크립트나 응용 프로그램을 사용 하 여 WMI 데이터를 가져올 수 있습니다. WS-Management는 포함 된 개체를 비롯 한 대부분의 익숙한 WMI 클래스와 작업을 지원 합니다. WMI를 활용 하 여 리소스에 대 한 데이터를 수집 하거나 Windows 기반 컴퓨터에서 리소스를 관리할 수 WS-Management. 즉, 기존 WMI 클래스 집합을 통해 엔터프라이즈의 디스크, 네트워크 어댑터, 서비스 또는 프로세스와 같은 개체에 대 한 데이터를 가져올 수 있습니다. 표준 WMI IPMI 공급자에서 사용할 수 있는 하드웨어 데이터에도 액세스할 수 있습니다.

## <a name="ws-management-windows-powershell-provider-wsman"></a>WS-Management Windows PowerShell 공급자 (WSMan)

WSMan 공급자는 사용 가능한 WS-Management 구성 설정에 대 한 계층 구조 보기를 제공 합니다. 공급자를 사용 하 여 다양 한 WS-Management 구성 옵션을 탐색 하 고 설정할 수 있습니다.

## <a name="ws-management-configuration"></a>WS-Management 구성

WS-Management 설치 및 구성 되지 않은 경우 Windows PowerShell 원격을 사용할 수 없으며, WS-Management cmdlet이 실행 되지 않으며, WS-Management 스크립트가 실행 되지 않으며, WSMan 공급자가 데이터 작업을 수행할 수 없습니다. WS-Management 명령줄 도구, WinRM 및 이벤트 전달은 WS-Management 구성에 따라 달라 집니다.

## <a name="ws-management-cmdlets"></a>WS-Management Cmdlet

WS-Management 기능은 cmdlet 및 WSMan 공급자 집합을 포함 하는 모듈을 통해 Windows PowerShell에서 구현 됩니다. 이러한 cmdlet을 사용 하 여 로컬 및 원격 컴퓨터에서 WS-Management 설정을 관리 하는 데 필요한 종단 간 작업을 완료할 수 있습니다.

다음 WS-Management cmdlet을 사용할 수 있습니다.

## <a name="connection-cmdlets"></a>연결 Cmdlet

- 연결-WSMan: 원격 컴퓨터의 WS-Management (WinRM) 서비스에 로컬 컴퓨터를 연결 합니다.

- Disconnect-WSMan: 원격 컴퓨터의 WS-Management (WinRM) 서비스에서 로컬 컴퓨터의 연결을 끊습니다.

## <a name="management-data-cmdlets"></a>Management-Data Cmdlet

- Get WSManInstance: 리소스 URI로 지정 된 리소스 인스턴스에 대 한 관리 정보를 표시 합니다.

- -WSManAction 호출: 리소스 URI 및 선택기에 의해 지정 된 대상 개체에서 작업을 호출 합니다.

- 새-WSManInstance: 새 관리 리소스 인스턴스를 만듭니다.

- -WSManInstance 제거: 관리 리소스 인스턴스를 삭제 합니다.

- Set-WSManInstance: 리소스와 관련 된 관리 정보를 수정 합니다.

## <a name="setup-and-configuration-cmdlets"></a>설정 및 구성 Cmdlet

- Set-wsmanquickconfig: 원격 관리를 위해 로컬 컴퓨터를 구성 합니다.
  Set-WSManQuickConfig cmdlet을 사용 하 여 WS-Management (WinRM) 서비스에 대 한 원격 연결을 허용 하도록 WS-Management을 구성할 수 있습니다. Set-WSManQuickConfig cmdlet은 다음 작업을 수행 합니다.
  - WS-Management (WinRM) 서비스가 실행 중인지 여부를 확인 합니다. WinRM 서비스가 실행 되 고 있지 않으면 Set-WSManQuickConfig cmdlet에서 서비스를 시작 합니다.
  - WS-Management (WinRM) 서비스 시작 유형을 자동으로 설정 합니다.
  - 모든 IP 주소의 요청을 수락 하는 수신기를 만듭니다. 기본 전송 프로토콜은 HTTP입니다.
  - WS-Management 트래픽에 대 한 방화벽 예외를 사용 하도록 설정 합니다.

  참고: Windows Vista, Windows Server 2008 및 이후 버전의 Windows에서이 cmdlet을 실행 하려면 "관리자 권한으로 실행" 옵션을 사용 하 여 Windows PowerShell을 시작 해야 합니다.

- 테스트-WSMan: WS-Management 설치 및 구성 되었는지 확인 합니다. Test-WSMan cmdlet은 WS-Management (WinRM) 서비스가 실행 중이 고 로컬 컴퓨터 또는 원격 컴퓨터에서 구성 되었는지 여부를 테스트 합니다.

- Enable-wsmancredssp: 클라이언트 컴퓨터에서 CredSSP 인증을 사용 하지 않도록 설정 합니다.

- Enable-wsmancredssp: 클라이언트 컴퓨터에서 CredSSP 인증을 사용 하도록 설정 합니다.

- Enable-wsmancredssp: 클라이언트 컴퓨터에 대 한 CredSSP 관련 구성을 가져옵니다.

## <a name="ws-management-specific-cmdlets"></a>WS-MANAGEMENT 관련 Cmdlet

- 새-WSManSessionOption: WS-Management cmdlet의 하나 이상의 매개 변수에 대 한 입력으로 사용할 WSManSessionOption 개체를 만듭니다.

## <a name="additional-ws-management-information"></a>추가 WS-Management 정보

WS 관리에 대 한 자세한 내용은 Windows 설명서에서 다음 항목을 참조 하세요.

[Windows 원격 관리](/windows/win32/winrm/portal)

[Windows 원격 관리 정보](/windows/win32/winrm/about-windows-remote-management)

[Windows 원격 관리 설치 및 구성](/windows/win32/winrm/installation-and-configuration-for-windows-remote-management)

[Windows 원격 관리 아키텍처](/windows/win32/winrm/windows-remote-management-architecture)

[WS-Management 프로토콜](/windows/win32/winrm/ws-management-protocol)

[Windows 원격 관리 및 WMI](/windows/win32/winrm/windows-remote-management-and-wmi)

[리소스 URI](/windows/win32/winrm/resource-uris)

[원격 하드웨어 관리](/windows/win32/winrm/remote-hardware-management)

[이벤트](/windows/win32/winrm/events)

## <a name="see-also"></a>참고 항목

[Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan)

[Disable-WSManCredSSP](xref:Microsoft.WSMan.Management.Disable-WSManCredSSP)

[Disconnect-WSMan](xref:Microsoft.WSMan.Management.Disconnect-WSMan)

[Enable-WSManCredSSP](xref:Microsoft.WSMan.Management.Enable-WSManCredSSP)

[Get-WSManCredSSP](xref:Microsoft.WSMan.Management.Get-WSManCredSSP)

[Get-WSManInstance](xref:Microsoft.WSMan.Management.Get-WSManInstance)

[Invoke-WSManAction](xref:Microsoft.WSMan.Management.Invoke-WSManAction)

[New-WSManInstance](xref:Microsoft.WSMan.Management.New-WSManInstance)

[Remove-WSManInstance](xref:Microsoft.WSMan.Management.Remove-WSManInstance)

[Set-WSManInstance](xref:Microsoft.WSMan.Management.Set-WSManInstance)

[Set-WSManQuickConfig](xref:Microsoft.WSMan.Management.Set-WSManQuickConfig)

[Test-WSMan](xref:Microsoft.WSMan.Management.Test-WSMan)
