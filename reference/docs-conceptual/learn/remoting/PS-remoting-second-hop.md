---
ms.date: 05/14/2020
keywords: powershell,cmdlet
title: PowerShell 원격에서 두 번째 홉 만들기
description: 이 문서에서는 보안 관련 사항 및 권장 사항을 포함하여 PowerShell 원격에 대한 두 번째 홉 인증을 구성하는 다양한 방법을 설명합니다.
ms.openlocfilehash: 905b27b4e6c612249c945a741bbe0d2ba9ae28aa
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501374"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>PowerShell 원격에서 두 번째 홉 만들기

"두 번째 홉 문제"는 다음과 같은 상황을 말합니다.

1. _ServerA_ 에 로그인되어 있습니다.
2. _ServerA_ 에서 원격 PowerShell 세션을 시작하여 _ServerB_ 에 연결합니다.
3. PowerShell 원격 세션을 통해 _ServerB_ 에서 실행하는 명령이 _ServerC_ 에 있는 리소스에 액세스하려고 합니다.
4. PowerShell 원격 세션을 만드는 데 사용한 자격 증명이 _ServerB_ 에서 _ServerC_ 로 전달되지 않았으므로 _ServerC_ 에 있는 리소스에 대한 액세스가 거부됩니다.

이 문제를 해결하는 방법은 여러 가지가 있습니다. 다음 표에서는 기본 설정 순서대로 메서드를 보여 줍니다.

|                      구성                       |                                  참고                                  |
| -------------------------------------------------------- | ---------------------------------------------------------------------- |
| CredSSP                                                  | 사용 편의성과 보안의 균형                                      |
| 리소스 기반 Kerberos 제한 위임           | 더 간단한 구성으로 보안 강화                             |
| Kerberos 제한 위임                          | 높은 보안이지만 도메인 관리자가 필요함                         |
| Kerberos 위임(비제한)                      | 권장하지 않음                                                        |
| JEA(Just Enough Administration)                         | 최상의 보안을 제공할 수 있지만 더 자세한 구성 필요 |
| RunAs를 사용한 PSSessionConfiguration                       | 구성하기에 더 간단하지만 자격 증명 관리 필요                |
| `Invoke-Command` 스크립트 블록 내에서 자격 증명 전달 | 사용하기에 가장 간단하지만 자격 증명을 제공해야 함                       |

## <a name="credssp"></a>CredSSP

인증에 [Credential Security Support Provider (CredSSP)][credssp](CredSSP(자격 증명 보안 지원 공급자))를 사용할 수 있습니다.
CredSSP는 원격 서버(_ServerB_)에 자격 증명을 캐시하므로, 이를 사용하면 자격 증명 도난 공격을 받을 수 있습니다. 원격 컴퓨터의 보안이 손상되면 공격자가 사용자의 자격 증명에 액세스할 수 있습니다. 기본적으로 CredSSP는 클라이언트 및 서버 컴퓨터 모두에서 사용하지 않도록 설정됩니다. 가장 신뢰할 수 있는 환경에서만 CredSSP를 사용하도록 설정해야 합니다. 예를 들어 도메인 컨트롤러는 매우 신뢰할 수 있으므로 도메인 관리자는 도메인 컨트롤러에 연결합니다.

PowerShell 원격에 CredSSP 사용 시의 보안 우려 사항에 대한 자세한 내용은 [Accidental Sabotage: Beware of CredSSP][beware](고의적 파괴: CredSSP 조심)를 참조하세요.

자격 증명 도난 공격에 대한 자세한 내용은 [PtH(Pass-the-Hash) 공격 및 기타 자격 증명 도난 완화][pth]를 참조하세요.

PowerShell 원격에 대해 CredSSP를 사용하도록 설정하고 사용하는 방법의 예는 [Enable PowerShell "Second-Hop" Functionality with CredSSP(CredSSP를 사용하여 PowerShell "두 번째 홉" 기능 사용)][credssp-psblog]을 참조하세요.

**장점**

- Windows Server 2008 이상이 설치된 모든 서버에 대해 작동합니다.

**단점**

- 보안 취약성이 있습니다.
- 클라이언트 역할과 서버 역할을 둘 다 구성해야 합니다.
- 보호된 사용자 그룹에서 작동하지 않습니다. 자세한 내용은 [보호된 사용자 보안 그룹][protected-users]을 참조하세요.

## <a name="kerberos-constrained-delegation"></a>Kerberos 제한 위임

레거시 제한 위임(리소스 기반 아님)을 사용하여 두 번째 홉을 만들 수 있습니다. "모든 인증 프로토콜 사용" 옵션을 사용하여 프로토콜 전환을 허용하도록 Kerberos 제한 위임을 구성합니다.

**장점**

- 특수 코딩이 필요하지 않습니다.
- 자격 증명이 저장되지 않습니다.

**단점**

- WinRM에 대한 두 번째 홉을 지원하지 않습니다.
- 구성하려면 도메인 관리자 액세스 권한이 필요합니다.
- 원격 서버(_ServerB_)의 Active Directory 개체에 대해 구성해야 합니다.
- 도메인 하나로 제한됩니다. 도메인 또는 포리스트를 벗어날 수 없습니다.
- 개체 및 SPN(서비스 사용자 이름)을 업데이트할 수 있는 권한이 필요합니다.
- _ServerB_ 는 사용자 개입 없이 사용자를 대신하여 _ServerC_ 로 Kerberos 티켓을 가져올 수 있습니다.

> [!NOTE]
> **계정이 민감하여 위임할 수 없음** 속성이 설정된 Active Directory 계정은 위임할 수 없습니다. 자세한 내용은 [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts][blog](보안 초점: 권한 있는 계정에 대한 '계정이 민감하여 위임할 수 없음' 분석) 및 [Kerberos Authentication Tools and Settings][ktools](Kerberos 인증 도구 및 설정)를 참조하세요.

## <a name="resource-based-kerberos-constrained-delegation"></a>리소스 기반 Kerberos 제한 위임

리소스 기반 Kerberos 제한 위임(Windows Server 2012에 도입됨)을 사용하여 리소스가 있는 서버 개체에 대한 자격 증명 위임을 구성합니다. 위에서 설명한 두 번째 홉 시나리오에서 위임된 자격 증명을 허용할 위치를 지정하도록 _ServerC_ 를 구성합니다.

**장점**

- 자격 증명이 저장되지 않습니다.
- PowerShell cmdlet을 사용하여 구성됩니다. 특수 코딩이 필요하지 않습니다.
- 구성하는 데 도메인 관리자 액세스 권한이 필요하지 않습니다.
- 도메인 및 포리스트에서 작동합니다.

**단점**

- Windows Server 2012 이상이 필요합니다.
- WinRM에 대한 두 번째 홉을 지원하지 않습니다.
- 개체 및 SPN(서비스 사용자 이름)을 업데이트할 수 있는 권한이 필요합니다.

> [!NOTE]
> **계정이 민감하여 위임할 수 없음** 속성이 설정된 Active Directory 계정은 위임할 수 없습니다. 자세한 내용은 [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts][blog](보안 초점: 권한 있는 계정에 대한 '계정이 민감하여 위임할 수 없음' 분석) 및 [Kerberos Authentication Tools and Settings][ktools](Kerberos 인증 도구 및 설정)를 참조하세요.

### <a name="example"></a>예제

_ServerB_ 의 위임된 자격 증명을 허용하도록 _ServerC_ 에 대해 리소스 기반 제한 위임을 구성하는 PowerShell 예제를 살펴보겠습니다. 이 예제에서는 모든 서버가 Windows Server 2012 이상을 실행하고 있으며 서버가 속하는 각 도메인에 하나 이상의 Windows Server 2012 도메인 컨트롤러가 있다고 가정합니다.

제한 위임을 구성하기 전에 먼저 `RSAT-AD-PowerShell` 기능을 추가하여 Active Directory PowerShell 모듈을 설치한 다음 해당 모듈을 세션으로 가져와야 합니다.

```powershell
Add-WindowsFeature RSAT-AD-PowerShell
Import-Module ActiveDirectory
Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount
```

이제 사용할 수 있는 여러 cmdlet에 **PrincipalsAllowedToDelegateToAccount** 매개 변수가 있습니다.

```Output
CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

**PrincipalsAllowedToDelegateToAccount** 매개 변수는 Active Directory 개체 특성 **msDS-AllowedToActOnBehalfOfOtherIdentity** 를 설정합니다. 이 특성은 자격 증명을 연결된 계정(이 예제에서는 _ServerA_ 의 머신 계정이 됨)에 위임할 수 있는 권한이 있는 계정을 지정하는 ACL(액세스 제어 목록)을 포함합니다.

이제 서버를 나타내는 데 사용할 변수를 설정하겠습니다.

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

WinRM(및 따라서 PowerShell 원격)은 기본적으로 컴퓨터 계정으로 실행됩니다. `winrm` 서비스의 **StartName** 속성을 살펴보아 이를 확인할 수 있습니다.

```powershell
Get-CimInstance Win32_Service -Filter 'Name="winrm"' | Select-Object StartName
```

```Output
StartName
---------
NT AUTHORITY\NetworkService
```

_ServerC_ 가 _ServerB_ 의 PowerShell 원격 세션으로부터의 위임을 허용하도록 _ServerC_ 에 대한 **PrincipalsAllowedToDelegateToAccount** 매개 변수를 _ServerB_ 의 컴퓨터 개체로 설정해야 합니다.

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

Kerberos [KDC(키 배포 센터)](/windows/win32/secauthn/key-distribution-center)는 15분마다 거부된 액세스 시도(부정 캐시)를 캐시합니다. _ServerB_ 가 이전에 _ServerC_ 에 액세스하려고 시도한 경우 다음 명령을 호출하여 _ServerB_ 의 캐시를 지워야 합니다.

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

캐시를 지우기 위해 컴퓨터를 다시 시작하거나 15분 이상 기다려야 할 수도 있습니다.

캐시를 지운 후 _ServerA_ 에서 _ServerB_ 를 거쳐 _ServerC_ 까지 코드를 실행할 수 있습니다.

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

이 예제에서 `$using` 변수는 `$ServerC` 변수가 _ServerB_ 에 표시되도록 하는 데 사용됩니다.
`$using` 변수에 대한 자세한 내용은 [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables)를 참조하세요.

여러 서버가 _ServerC_ 에 자격 증명을 위임할 수 있도록 하려면 _ServerC_ 에 대한 **PrincipalsAllowedToDelegateToAccount** 매개 변수 값을 배열로 설정합니다.

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

도메인에 걸쳐 두 번째 홉을 만들려는 경우 _ServerB_ 가 속하는 도메인의 도메인 컨트롤러에 대한 FQDN(정규화된 도메인 이름)을 추가합니다.

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

ServerC에 자격 증명을 위임하는 기능을 제거하려면 _ServerC_ 에 대한 **PrincipalsAllowedToDelegateToAccount** 매개 변수 값을 `$null`로 설정합니다.

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>리소스 기반 Kerberos 제한 위임에 대한 정보

- [Kerberos 인증의 새로운 기능][whats-new]
- [How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1][kcd2012-1](Windows Server 2012에서 Kerberos 제한 위임의 불편을 줄이는 방법, 1부)
- [How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2][kcd2012-2](Windows Server 2012에서 Kerberos 제한 위임의 불편을 줄이는 방법, 2부)
- [Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication][kcdpaper](Windows 통합 인증을 사용한 Azure Active Directory 애플리케이션 프록시 배포에 대한 Kerberos 제한 인증 이해)
- [[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2]([MS-ADA2]: Active Directory 스키마 특성 M2.210 특성 msDS-AllowedToActOnBehalfOfOtherIdentity)
- [[MS-SFU] Kerberos 프로토콜 확장: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy][MS-SFU]([MS-SFU]: Kerberos 프로토콜 확장: 사용자 서비스 및 제한 위임 프로토콜 1.3.2 S4U2proxy)
- [Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount][remote-admin](PrincipalsAllowedToDelegateToAccount를 사용한 제한 위임 없는 원격 관리)

## <a name="kerberos-delegation-unconstrained"></a>Kerberos 위임(비제한)

Kerberos 비제한 위임을 사용하여 두 번째 홉을 만들 수도 있습니다. 모든 Kerberos 시나리오와 마찬가지로 자격 증명은 저장되지 않습니다. 이 메서드는 WinRM에 대한 두 번째 홉을 지원하지 않습니다.

> [!WARNING]
> 이 메서드를 사용할 경우 위임된 자격 증명이 사용되는 위치를 제어할 수 없습니다. CredSSP보다 안전하지 않습니다. 이 메서드는 테스트 시나리오에만 사용해야 합니다.

## <a name="just-enough-administration-jea"></a>JEA(Just Enough Administration)

JEA를 사용하여 PowerShell 세션 동안 관리자가 실행할 수 있는 명령을 제한할 수 있습니다. 두 번째 홉 문제를 해결하는 데 JEA를 사용할 수 있습니다.

JEA에 대한 자세한 내용은 [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview)을 참조하세요.

**장점**

- 가상 계정을 사용할 경우 암호를 유지 관리할 필요가 없습니다.

**단점**

- WMF 5.0 이상이 필요합니다.
- 모든 중간 서버(_ServerB_)에 대한 구성이 필요합니다.

## <a name="pssessionconfiguration-using-runas"></a>RunAs를 사용한 PSSessionConfiguration

_ServerB_ 에 대한 세션 구성을 만들고 해당 **RunAsCredential** 매개 변수를 설정할 수 있습니다.

**PSSessionConfiguration** 및 **RunAs** 를 사용하여 두 번째 홉 문제를 해결하는 방법에 대한 자세한 내용은 [다중 홉 PowerShell 원격에 대한 다른 해결 방법][pssessionconfig]을 참조하세요.

**장점**

- WMF 3.0 이상이 설치된 모든 서버에서 작동합니다.

**단점**

- 모든 중간 서버(_ServerB_)에 대해 **PSSessionConfiguration** 및 **RunAs** 를 구성해야 합니다.
- 도메인 **RunAs** 계정을 사용할 경우 암호를 유지 관리해야 합니다.

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Invoke-Command 스크립트 블록 내에 자격 증명 전달

[Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet 호출의 **ScriptBlock** 매개 변수 내에 자격 증명을 전달할 수 있습니다.

**장점**

- 특별한 서버 구성이 필요하지 않습니다.
- WMF 2.0 이상을 실행하는 모든 서버에서 작동합니다.

**단점**

- 불편한 코드 기법이 필요합니다.
- WMF 2.0을 실행하는 경우 원격 세션으로 인수를 전달하는 데 서로 다른 구문이 필요합니다.

### <a name="example"></a>예제

다음 예제에서는 **Invoke-Command** 스크립트 블록으로 자격 증명을 전달하는 방법을 보여 줍니다.

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a>참고 항목

[PowerShell Remoting 보안 고려 사항](WinRMSecurity.md)

<!-- link references -->
[blog]: /archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts
[ktools]: /previous-versions/windows/it-pro/windows-server-2003/cc738673(v=ws.10)
[credssp]: /windows/win32/secauthn/credential-security-support-provider
[beware]: https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp
[pth]: https://www.microsoft.com/download/details.aspx?id=36036
[credssp-psblog]: https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/
[whats-new]: /previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831747(v=ws.11)
[kcd2012-1]: https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1
[kcd2012-2]: https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2
[kcdpaper]: https://aka.ms/kcdpaper
[MS-ADA2]: /openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405
[MS-SFU]: /openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a
[remote-admin]: /archive/blogs/taylorb/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount
[pssessionconfig]: /archive/blogs/sergey_babkins_blog/another-solution-to-multi-hop-powershell-remoting
[protected-users]: /windows-server/security/credentials-protection-and-management/protected-users-security-group
