---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: WinRMSecurity
ms.openlocfilehash: 59717e4806857e6760de523335bbee6028da8e84
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402540"
---
# <a name="powershell-remoting-security-considerations"></a>PowerShell Remoting 보안 고려 사항

PowerShell Remoting을 사용해 Windows 시스템을 관리하는 것이 좋습니다. Windows Server 2012 R2에서는 PowerShell Remoting이 기본적으로 사용됩니다. 이 문서에서는 PowerShell 원격을 사용할 때의 보안 문제, 권장 사항, 모범 사례 등을 설명합니다.

## <a name="what-is-powershell-remoting"></a>PowerShell Remoting이란?

PowerShell 원격은 [Web Services for Managment (WS-Managment)](https://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf)(WS-Managment(Web Services for Managment))의 Microsoft 구현인 [Windows Remote Management (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426.aspx)(WinRM(Windows 원격 관리))를 사용하여 사용자가 원격 컴퓨터에서 PowerShell 명령을 실행할 수 있도록 합니다. PowerShell Remoting 사용에 관한 자세한 내용은 [원격 명령 실행](https://technet.microsoft.com/library/dd819505.aspx)에서 확인할 수 있습니다.

PowerShell 원격은 원격 컴퓨터에서의 실행을 위해 cmdlet의 **ComputerName** 매개 변수를 사용하는 것과 다릅니다. 후자의 경우 RPC(원격 프로시저 호출)를 기본 프로토콜로 사용합니다.

## <a name="powershell-remoting-default-settings"></a>PowerShell Remoting 기본 설정

PowerShell Remoting 및 WinRM은 다음 포트에서 수신 대기합니다.

- HTTP: 5985
- HTTPS: 5986

기본적으로 PowerShell 원격은 Administrators 그룹 구성원의 연결만 허용합니다. 세션은 사용자 컨텍스트에서 시작되므로 PowerShell 원격을 통해 연결된 상태에서는 개별 사용자 및 그룹에 적용된 모든 운영 체제 액세스 제어가 계속해서 적용됩니다.

개인 네트워크에서는 PowerShell Remoting용 기본 Windows 방화벽 규칙이 모든 연결을 수락합니다. 공용 네트워크에서는 기본 Windows 방화벽 규칙이 동일한 서브넷 내에서만 PowerShell 원격 연결을 허용합니다. 공용 네트워크에서 모든 연결에 대해 PowerShell Remoting을 열려면 해당 규칙을 명시적으로 변경해야 합니다.

>**경고:** 공용 네트워크용 방화벽 규칙은 잠재적으로 악의적인 외부 연결 시도로부터 컴퓨터를 보호합니다. 이 규칙을 제거할 때는 주의하세요.

## <a name="process-isolation"></a>프로세스 격리

PowerShell Remoting은 컴퓨터 간 통신을 위해 [WinRM(Windows Remote Management)](https://msdn.microsoft.com/library/windows/desktop/aa384426)을 사용합니다.
WinRM은 네트워크 서비스 계정 아래에서 서비스로 실행되며, 사용자 계정으로 실행되는 격리 프로세스를 생성해 PowerShell 인스턴스를 호스트합니다. 한 명의 사용자로 실행하는 PowerShell의 인스턴스는 다른 사용자로 PowerShell 인스턴스를 실행하는 프로세스에 액세스할 수 없습니다.

## <a name="event-logs-generated-by-powershell-remoting"></a>PowerShell 원격에서 생성된 이벤트 로그

FireEye는 Powershell 원격 세션에서 생성된 이벤트 로그와 기타 보안 증명에 대한 훌륭한 요약을 제공했으며, 이 내용은 [Investigating PowerShell Attacks](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf)(PowerShell 공격 조사)에 나와 있습니다.

## <a name="encryption-and-transport-protocols"></a>암호화 및 전송 프로토콜

PowerShell 원격 연결 보안은 초기 인증 및 지속적인 통신의 두 가지 관점으로 고려하는 것이 좋습니다.

사용된 전송 프로토콜(HTTP 또는 HTTPS)에 관계 없이 PowerShell Remoting은 초기 인증 후 세션별 AES-256 대칭 키를 사용해 모든 통신을 항상 암호화합니다.

### <a name="initial-authentication"></a>초기 인증

인증을 통해 클라이언트-서버, 그리고 이상적으로 서버-클라이언트의 ID를 확인합니다.

클라이언트가 컴퓨터 이름(server01 또는 server01.contoso.com)을 사용해 도메인 서버에 연결되는 경우 기본 인증 프로토콜은 [Kerberos](https://msdn.microsoft.com/library/windows/desktop/aa378747.aspx)입니다.
Kerberos는 모든 종류의 다시 사용할 수 있는 자격 증명을 보내지 않고 사용자 ID 및 서버 ID를 모두 보장합니다.

클라이언트가 IP 주소를 사용해 도메인 서버에 연결되는 경우 또는 작업 그룹 서버에 연결되는 경우 Kerberos 인증은 사용할 수 없습니다. 이 경우 PowerShell 원격은 [NTLM authentication protocol(NTLM 인증 프로토콜)](https://msdn.microsoft.com/library/windows/desktop/aa378749.aspx)을 사용합니다. NTLM 인증 프로토콜은 어떠한 위임 가능 자격 증명도 보내지 않고 사용자 ID를 보장합니다. 사용자 ID를 입증하기 위해 NTLM 프로토콜은 클라이언트와 서버 모두 암호 자체를 교환하지 않고 사용자 암호에서 세션 키를 계산하도록 요구합니다. 서버는 일반적으로 사용자 암호를 모르므로 사용자 암호를 알고 서버의 세션 키를 저장하는 도메인 컨트롤러와 통신합니다.

그러나 NTLM 프로토콜은 서버 ID를 보장하지 않습니다. 인증에 NTLM을 사용하는 모든 프로토콜에서와 마찬가지로 도메인에 가입된 컴퓨터의 컴퓨터 계정에 액세스할 수 있는 공격자는 도메인 컨트롤러의 호출하여 NTLM 세션 키를 계산하고 서버를 가장할 수 있습니다.

NTLM 기반 인증은 기본적으로 사용하지 않도록 설정되어 있습니다. 하지만 대상 서버에 SSL을 구성하거나 클라이언트에서 WinRM TrustedHosts 설정을 구성해 허용할 수도 있습니다.

#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a>NTLM 기반 연결 동안 SSL 인증서를 사용해 서버 ID 유효성 검사

NTLM 인증 프로토콜은 대상 서버의 ID를 보장하지 않으므로(사용자의 암호를 이미 아는 경우는 제외) PowerShell Remoting에 SSL을 사용하도록 대상 서버를 구성할 수 없습니다. 대상 서버에 SSL 인증서를 할당하면(클라이언트도 신뢰하는 인증 기관에서 발급한 경우) 사용자 ID와 서버 ID를 모두 보장하는 NTLM 기반 인증을 수행할 수 있습니다.

#### <a name="ignoring-ntlm-based-server-identity-errors"></a>NTLM 기반 서버 ID 오류 무시

NTLM 연결을 위해 서버에 SSL 인증서를 배포할 수 없는 경우 서버를 WinRM **TrustedHosts** 목록에 추가하여 결과 ID 오류를 표시하지 않을 수 있습니다. 서버 이름을 TrustedHosts 목록에 추가한다고 호스트 자체를 신뢰할 수 있음을 나타내는 것은 아닙니다. NTLM 인증 프로토콜이 사용자가 연결하려는 호스트에 실제로 연결하는 중인지 보장할 수 없기 때문입니다.
대신에 TrustedHosts 설정을 서버의 ID를 확인하지 못해 발생하는 오류를 숨기려는 호스트 목록으로 간주해야 합니다.


### <a name="ongoing-communication"></a>진행 중인 통신

초기 인증이 완료되면 [PowerShell Remoting Protocol(PowerShell 원격 프로토콜)](https://msdn.microsoft.com/library/dd357801.aspx)이 모든 진행 중인 통신을 세션별 AES-256 대칭 키를 사용해 암호화합니다.


## <a name="making-the-second-hop"></a>두 번째 홉 만들기

기본적으로 PowerShell Remoting은 인증을 위해 Kerberos(사용 가능한 경우) 또는 NTLM을 사용합니다. 이 두 프로토콜은 모두 자격 증명을 보내지 않고 원격 컴퓨터를 인증합니다.
이는 가장 안전한 인증 방법입니다. 하지만 원격 컴퓨터에 사용자의 자격 증명이 없으므로 사용자를 대신해 다른 컴퓨터나 서비스에 액세스할 수 없습니다.
이를 "두 번째 홉 문제"라고 합니다.

이 문제를 방지하는 방법은 여러 가지가 있습니다. 이러한 방법에 대한 설명과 각 방법의 장점과 단점은 [PowerShell 원격에서 두 번째 홉 만들기](PS-remoting-second-hop.md)를 참조하세요.