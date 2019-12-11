---
ms.date: 06/27/2017
keywords: powershell,cmdlet
title: Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능
ms.openlocfilehash: c426b8cfb10829241ba244a5d840c91e1de9f66e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62058423"
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능

업데이트 날짜: 2013년 6월 24일

적용 대상: Windows Server 2012 R2, Windows Server 2012

Windows Server 2012 R2 및 Windows Server 2012의 Windows PowerShell 웹 액세스에는 제한적인 보안 모델이 있습니다. 사용자가 Windows PowerShell 웹 액세스 게이트웨이에 로그인하고 웹 기반 Windows PowerShell 콘솔을 사용할 수 있으려면 먼저 명시적으로 액세스 권한이 부여되어야 합니다.

## <a name="configuring-authorization-rules-and-site-security"></a>권한 부여 규칙 및 사이트 보안 구성

Windows PowerShell Web Access가 설치되고 게이트웨이가 구성되고 나면 사용자는 로그인 페이지를 브라우저에서 열 수 있지만 Windows PowerShell 웹 액세스 관리자가 사용자에게 액세스를 명시적으로 허용할 때까지는 로그인할 수 없습니다. ‘Windows PowerShell 웹 액세스’ 액세스 제어는 다음 표에 설명된 여러 Windows PowerShell cmdlet을 통해 관리할 수 있습니다. 권한 부여 규칙을 추가하거나 관리하는 작업에 해당하는 GUI는 없습니다.
[Windows PowerShell Web Access Cmdlets](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)(Windows PowerShell 웹 액세스 Cmdlet)를 참조하세요.

관리자는 Windows PowerShell 웹 액세스에 대한 `{0-n}` 인증 규칙을 정의할 수 있습니다. 기본 보안은 허용적이지 않고 제한적이며, 0 인증 규칙은 사용자가 어디에도 액세스할 수 없음을 의미합니다.

Windows Server 2012 R2의 [Add-PswaAuthorizationRule](/powershell/module/powershellwebaccess/add-pswaauthorizationrule?view=winserver2012r2-ps) 및 [Test-PswaAuthorizationRule](/powershell/module/powershellwebaccess/test-pswaauthorizationrule?view=winserver2012r2-ps)에는 원격 컴퓨터 또는 활성 Windows PowerShell 웹 액세스 세션에서 Windows PowerShell 웹 액세스 권한 부여 규칙을 추가 및 테스트할 수 있게 해주는 Credential 매개 변수가 포함되어 있습니다. Credential 매개 변수가 있는 다른 Windows PowerShell cmdlet과 마찬가지로는 PSCredential 개체를 매개 변수 값으로 지정할 수 있습니다. 원격 컴퓨터에 전달하려는 자격 증명이 포함된 PSCredential 개체를 만들려면 [Get-Credential](/powershell/module/microsoft.powershell.security/Get-Credential) cmdlet을 실행합니다.

Windows PowerShell 웹 액세스 인증 규칙은 허용 목록 규칙입니다. 각 규칙은 사용자, 대상 컴퓨터 및 지정된 대상 컴퓨터의 특정 Windows PowerShell [세션 구성](/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-5.1)(엔드포인트 또는 _runspace_라고도 함) 사이에 허용된 연결을 정의한 것입니다.
**runspace**에 대한 설명은 [PowerShell Runspace 사용 시작](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/) 를 참조하세요

> [!IMPORTANT]
> 사용자는 참인 규칙이 하나만 있어야 액세스 권한을 얻을 수 있습니다. 웹 기반 콘솔에서 모든 언어에 액세스할 수 있는 권한이든, Windows PowerShell 원격 관리 cmdlet에만 액세스할 수 있는 권한이든, 사용자에게 한 컴퓨터에 대한 액세스 권한이 주어지면 사용자는 첫 번째 대상 컴퓨터에 연결된 다른 컴퓨터에도 로그온(또는 홉)할 수 있습니다. Windows PowerShell 웹 액세스를 가장 안전하게 구성하는 방법은 사용자가 일반적으로 원격 작업을 수행할 수 있는 제한된 세션 구성만 액세스할 수 있도록 구성하는 것입니다.

[Windows PowerShell Web Access Cmdlets](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)(Windows PowerShell 웹 액세스 Cmdlet)에 참조된 cmdlet을 사용하면 Windows PowerShell 웹 액세스 게이트웨이의 사용자에게 권한을 부여하는 데 사용되는 일련의 액세스 규칙을 만들 수 있습니다. 이러한 규칙은 대상 컴퓨터에 대한 ACL(액세스 제어 목록)과는 다른 것으로 웹 액세스에 대한 추가 보안 계층을 제공합니다. 보안에 대한 자세한 내용은 다음 섹션에서 설명됩니다.

사용자가 위의 보안 계층을 하나도 통과하지 못하면 브라우저 창에 일반적인 '액세스 거부' 메시지가 표시됩니다. 자세한 보안 정보가 게이트웨이 서버에서 기록되지만 최종 사용자에게는 통과한 보안 계층 개수 또는 로그인이나 인증에 실패한 계층에 대한 정보가 표시되지 않습니다.

권한 부여 규칙을 구성하는 방법에 대한 자세한 내용은 이 항목의 [권한 부여 규칙 구성](#configuring-authorization-rules-and-site-security)을 참조하세요.

### <a name="security"></a>보안

Windows PowerShell 웹 액세스 보안 모델은 웹 기반 콘솔의 최종 사용자와 대상 컴퓨터 간의 4단계 계층으로 구성됩니다. Windows PowerShell 웹 액세스 관리자는 IIS 관리자 콘솔에서의 추가 구성을 통해 보안 계층을 추가할 수 있습니다. IIS 관리자 콘솔에서 웹 사이트를 보호하는 방법에 대한 자세한 내용은 [웹 서버 보안 구성(IIS7)](https://technet.microsoft.com/library/cc731278)을 참조하세요.

IIS 모범 사례 및 서비스 거부 공격 방지에 대한 자세한 내용은 [서비스 거부 공격 방지를 위한 모범 사례](https://technet.microsoft.com/library/cc750213)를 참조하세요.
관리자는 인증 소프트웨어 정품을 추가로 구매하여 설치할 수도 있습니다.

다음 표에는 최종 사용자와 대상 컴퓨터 간의 4단계 보안 계층이 설명되어 있습니다.

|수준|계층|
|-|-|
|1|[IIS 웹 서버 보안 기능](#iis-web-server-security-features)|
|2|[Windows PowerShell 웹 액세스 양식 기반 게이트웨이 인증](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[Windows PowerShell 웹 액세스 권한 부여 규칙](#windows-powershell-web-access-authorization-rules)|
|4|[대상 인증 및 권한 부여 규칙](#target-authentication-and-authorization-rules)|

각 계층에 대한 자세한 내용은 다음 제목 아래에서 찾을 수 있습니다.

#### <a name="iis-web-server-security-features"></a>IIS 웹 서버 보안 기능

Windows PowerShell 웹 액세스 사용자는 게이트웨이에서 자신의 계정을 인증하려면 항상 사용자 이름과 암호를 제공해야 합니다. 하지만 Windows PowerShell 웹 액세스 관리자는 클라이언트 인증서 인증을 선택적으로 켜거나 끌 수도 있습니다(테스트 인증서를 사용하도록 설정하고 나중에 정품 인증서를 구성하는 방법은 [Windows PowerShell 웹 액세스 설치 및 사용](install-and-use-windows-powershell-web-access.md) 참조).

선택적인 클라이언트 인증서 기능을 사용하려면 최종 사용자에게 사용자 이름과 암호 이외에 유효한 클라이언트 인증서가 있어야 하며, 이러한 기능은 웹 서버(IIS) 구성의 일부로 포함됩니다. 클라이언트 인증서 계층이 사용하도록 설정되면 Windows PowerShell 웹 액세스 로그인 페이지에서는 사용자의 로그인 자격 증명을 확인하기 전에 사용자에게 유효한 인증서를 제공하라는 메시지를 표시합니다. 클라이언트 인증서 인증에서는 클라이언트 인증서를 자동으로 확인합니다. 유효한 인증서가 없으면 Windows PowerShell 웹 액세스에서 사용자에게 인증서를 제공하라는 메시지를 표시합니다. 유효한 클라이언트 인증서가 검색되면 Windows PowerShell 웹 액세스에서 사용자가 해당하는 사용자 이름과 암호를 입력할 로그인 페이지를 엽니다.

이는 IIS 웹 서버에서 제공되는 추가 보안 설정의 한 예입니다. 기타 IIS 보안 기능에 대한 자세한 내용은 [웹 서버 보안 구성(IIS 7)](https://technet.microsoft.com/library/cc731278)을 참조하세요.

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Windows PowerShell 웹 액세스 양식 기반 게이트웨이 인증

Windows PowerShell 웹 액세스 로그인 페이지에서는 자격 증명 세트(사용자 이름과 암호)를 요구하며, 대상 컴퓨터에 대해 다른 자격 증명을 제공할 수 있는 옵션을 사용자에게 제공합니다.
사용자가 대체 자격 증명을 제공하지 않으면 게이트웨이 연결에 사용되는 기본 사용자 이름과 암호가 대상 컴퓨터와 연결하는 데에도 사용됩니다.

이렇게 요구된 자격 증명은 Windows PowerShell 웹 액세스 게이트웨이에서 인증됩니다. 이러한 자격 증명은 로컬 Windows PowerShell 웹 액세스 게이트웨이 서버나 Active Directory의 유효한 사용자 계정이어야 합니다.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Windows PowerShell 웹 액세스 권한 부여 규칙

사용자가 게이트웨이에서 인증되고 나면 Windows PowerShell 웹 액세스는 권한 부여 규칙을 점검하여 요청된 대상 컴퓨터에 대한 액세스 권한이 사용자에게 있는지 확인합니다. 권한 부여에 성공하면 사용자의 자격 증명이 대상 컴퓨터에 전달됩니다.

이러한 규칙은 사용자가 게이트웨이에서 인증된 이후에만 평가할 수 있으며, 그 전에 대상 컴퓨터에서 사용자를 인증할 수 있습니다.

#### <a name="target-authentication-and-authorization-rules"></a>대상 인증 및 권한 부여 규칙

Windows PowerShell 웹 액세스의 보안을 위한 마지막 계층은 대상 컴퓨터의 자체 보안 구성입니다. 사용자는 대상 컴퓨터와 Windows PowerShell 웹 액세스 권한 부여 규칙에 적절한 액세스 권한이 구성되어 있어야 Windows PowerShell 웹 액세스를 통해 대상 컴퓨터를 관리할 수 있는 Windows PowerShell 웹 기반 콘솔을 실행할 수 있습니다.

이 계층은 사용자가 [Enter-PSSession](/powershell/module/microsoft.powershell.core/Enter-PSSession) 또는 [New-PSSession](/powershell/module/microsoft.powershell.core/new-pssession) cmdlet을 실행하여 Windows PowerShell 내에서 대상 컴퓨터에 대한 원격 Windows PowerShell 세션을 만들려고 하는 경우 연결 시도를 평가하는 동일한 보안 메커니즘을 제공합니다.

기본적으로 Windows PowerShell 웹 액세스에서는 게이트웨이와 대상 컴퓨터를 모두 인증하는 데 기본 사용자 이름과 암호를 사용합니다. 하지만 **옵션 연결 설정**섹션의 웹 기반 로그인 페이지에는 대상 컴퓨터에 다른 자격 증명을 제공하는 옵션이 있으므로, 필요에 따라 적절히 사용할 수 있습니다. 사용자가 대체 자격 증명을 제공하지 않으면 게이트웨이 연결에 사용되는 기본 사용자 이름과 암호가 대상 컴퓨터와 연결하는 데에도 사용됩니다.

권한 부여 규칙을 사용하면 사용자가 특정 세션 구성에 액세스할 수 있도록 허용할 수 있습니다. Windows PowerShell 웹 액세스에 대한 _제한된 runspace_나 세션 구성을 만들어 특정 사용자가 Windows PowerShell 웹 액세스에 로그인할 때 특정 세션 구성에만 연결할 수 있도록 구성할 수 있습니다. ACL(액세스 제어 목록)을 사용하면 특정 엔드포인트에 액세스할 수 있는 사용자를 지정할 수 있으며, 이 섹션에 설명된 권한 부여 규칙을 통해 특정 사용자 집합의 엔드포인트에 대한 액세스를 추가로 제한할 수 있습니다. 제한된 runspace에 대한 자세한 내용은 MSDN의 [Creating a constrained runspace](https://msdn.microsoft.com/library/dn614668)(제한된 runspace 만들기)를 참조하세요.

### <a name="configuring-authorization-rules"></a>권한 부여 규칙 구성

관리자는 Windows PowerShell 웹 액세스 사용자에 대해 자신의 Windows PowerShell 원격 관리 환경에서 이미 정의되어 있는 동일한 권한 부여 규칙을 사용하려고 할 수 있습니다. 이 섹션의 첫 번째 절차에서는 단일 세션 구성 내에서 한 컴퓨터를 관리하기 위해 로그인하는 한 명의 사용자에게 액세스를 허용하는 안전한 권한 부여 규칙을 추가하는 방법을 설명합니다. 두 번째 절차에서는 더 이상 필요하지 않는 권한 부여 규칙을 제거하는 방법을 설명합니다.

특정 사용자가 Windows PowerShell 웹 액세스의 제한된 runspace 내에서만 작업할 수 있도록 사용자 지정 세션 구성을 사용하려는 경우, 사용자 지정 세션 구성을 만든 후에 이를 참조하는 권한 규칙을 추가합니다. Windows PowerShell 웹 액세스 cmdlet을 사용하여 사용자 지정 세션 구성을 만들 수는 없습니다. 사용자 지정 세션 구성을 만드는 방법에 대한 자세한 내용은 [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files)를 참조하세요.

Windows PowerShell 웹 액세스 cmdlet에서는 와일드카드 문자(\*)를 단독으로 사용할 수 있습니다. 문자열에 포함된 와일드카드 문자는 지원되지 않으므로 속성(사용자, 컴퓨터 또는 세션 구성)당 하나의 와일드카드 문자를 단독으로 사용합니다.

> [!NOTE]
> 권한 부여 규칙을 사용하여 사용자에게 액세스 권한을 허용하고 Windows PowerShell 웹 액세스 환경을 보호하는 여러 가지 방법에 대해서는 이 항목의 [기타 권한 부여 규칙 시나리오 예](#other-authorization-rule-scenario-examples)를 참조하세요.

#### <a name="to-add-a-restrictive-authorization-rule"></a>제한적인 권한 부여 규칙을 추가하려면

1. 다음 중 하나를 수행하여 관리자 권한으로 Windows PowerShell 세션을 엽니다.

   - Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.

   - Windows **시작** 화면에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.

2. 세션 구성을 사용하여 사용자 액세스를 제한하는 단계(**옵션**):

   사용할 세션 구성이 규칙에 이미 있는지 확인합니다.

   해당 구성을 아직 만들지 않은 경우 [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files)에서 세션 구성을 만드는 방법에 대한 지침을 따르세요.

3. 이 권한 부여 규칙을 통해 특정 사용자는 일반적으로 액세스 권한을 갖고 있는 네트워크상의 한 컴퓨터에만 액세스할 수 있으며, 일반적인 스크립팅 및 cmdlet 환경에 해당하는 특정 세션 구성에 액세스할 수 있습니다. 다음을 입력하고 **Enter** 키를 누릅니다.

   ```
   Add-PswaAuthorizationRule -UserName <domain\user | computer\user> `
      -ComputerName <computer_name> -ConfigurationName <session_configuration_name>
   ```

   - 다음 예에서는 _Contoso_ 도메인의 _JSmith_라는 사용자에게 _Contoso_214_ 컴퓨터를 관리하고, _NewAdminsOnly_라는 세션 구성을 사용할 수 있는 액세스 권한이 부여됩니다.

   ```powershell
   Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' `
      -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly
   ```

4. **Get-PswaAuthorizationRule** cmdlet 또는 `Test-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName** <computer_name>`을 실행하여 이 규칙이 생성되어 있는지 확인합니다.
   정의합니다(예: `Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214`).

#### <a name="to-remove-an-authorization-rule"></a>권한 부여 규칙을 제거하려면

1. Windows PowerShell 세션이 아직 열려 있지 않으면 이 섹션에 나와 있는 [제한적인 권한 부여 규칙을 추가하려면](#to-add-a-restrictive-authorization-rule)의 1단계를 참조하세요.

2. 다음을 입력한 다음 **Enter** 키를 누릅니다(여기서 *rule ID*는 제거하려는 규칙의 고유한 ID 번호를 나타냄).

   ```
   Remove-PswaAuthorizationRule -ID <rule ID>
   ```

   또는 제거할 규칙의 ID 번호는 모르지만 이름을 알고 있다면 다음 예와 같이 해당 규칙의 이름을 가져온 다음 `Remove-PswaAuthorizationRule` cmdlet에 파이프하여 규칙을 제거합니다.

   ```
   Get-PswaAuthorizationRule `
      -RuleName <rule-name> | Remove-PswaAuthorizationRule
   ```

> [!NOTE]
> 지정된 권한 부여 규칙을 삭제할지 확인하는 메시지는 표시되지 않으므로, **Enter** 키를 누르면 규칙이 삭제됩니다. 따라서 `Remove-PswaAuthorizationRule` cmdlet을 실행하기 전에 권한 부여 규칙을 제거할 것인지 확실히 해야 합니다.

#### <a name="other-authorization-rule-scenario-examples"></a>기타 권한 부여 규칙 시나리오 예

모든 Windows PowerShell 세션에서는 세션 구성을 사용하는데, 세션에 세션 구성이 지정되어 있지 않은 경우 Microsoft.PowerShell이라고 하는 기본 제공 Windows PowerShell 세션 구성이 Windows PowerShell에서 기본적으로 사용됩니다. 이 기본 세션 구성에는 컴퓨터에서 사용할 수 있는 모든 cmdlet이 포함되어 있습니다. 관리자는 제한된 runspace(최종 사용자가 제한된 범위의 cmdlet과 작업을 수행할 수 있음)가 사용된 세션 구성을 정의하여 모든 컴퓨터에 대한 액세스를 제한할 수 있습니다. 한 컴퓨터에 대해 모든 언어에 액세스할 수 있거나 Windows PowerShell 원격 관리 cmdlet에만 액세스할 수 있도록 허용된 사용자는 첫 번째 컴퓨터에 연결된 다른 컴퓨터에도 연결할 수 있습니다. 제한된 runspace를 정의하면 사용자가 허용된 자신의 Windows PowerShell runspace에서 다른 컴퓨터를 액세스할 수 없게 되어 Windows PowerShell 웹 액세스 환경의 보안을 강화할 수 있습니다. 그룹 정책을 사용하여 관리자가 Windows PowerShell 웹 액세스를 통해 액세스할 수 있도록 구성하려는 모든 컴퓨터에 세션 구성을 배포할 수 있습니다. 세션 구성에 대한 자세한 내용은 [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)를 참조하세요. 아래 이 시나리오에 대한 몇 가지 예가 나와 있습니다.

- 관리자는 제한된 runspace가 사용되는 **PswaEndpoint**라는 엔드포인트를 만듭니다. 그런 다음, `*,*,PswaEndpoint`라는 규칙을 만들고 엔드포인트를 다른 컴퓨터에 배포합니다. 이 규칙을 통해 모든 사용자는 **PswaEndpoint**라는 엔드포인트가 있는 모든 컴퓨터에 액세스할 수 있습니다.
  이 규칙이 규칙 집합에 유일하게 정의되어 있는 규칙이라면 이 엔드포인트가 없는 컴퓨터에는 액세스할 수 없습니다.

- 관리자는 제한된 runspace가 사용되는 **PswaEndpoint**라는 엔드포인트를 만들었으며, 특정 사용자만 액세스할 수 있도록 제한하려고 합니다. 관리자는 **Level1Support**라는 사용자 그룹을 만들고 다음 규칙, 즉 **Level1Support,\*,PswaEndpoint**를 정의합니다. 이 규칙에서는 **Level1Support** 그룹의 모든 사용자가 **PswaEndpoint** 구성이 사용된 모든 컴퓨터에 액세스할 수 있도록 허용합니다. 이와 마찬가지로, 특정 컴퓨터 집합에만 액세스하도록 제한할 수도 있습니다.

- 일부 관리자는 특정 사용자에게 다른 사용자보다 많은 액세스 권한을 제공합니다. 예를 들어 관리자는 **Admins**과 **BasicSupport**라는 두 개의 사용자 그룹을 만듭니다. 또한 관리자는 제한된 runspace가 사용되는 **PswaEndpoint**라는 엔드포인트를 만들고, **Admins,\*,\*** 및 **BasicSupport,\*,PswaEndpoint**라는 두 개의 규칙을 정의합니다. 첫 번째 규칙에서는 **Admin** 그룹의 모든 사용자에게 모든 컴퓨터에 대한 액세스 권한을 제공하지만, 두 번째 규칙에서는 **BasicSupport** 그룹의 모든 사용자에게 **PswaEndpoint**가 포함된 컴퓨터에만 액세스할 수 있는 권한을 제공합니다.

- 관리자는 개인 테스트 환경을 구축했으며, 권한을 부여받은 모든 네트워크 사용자가 일반적으로 액세스하던 네트워크상의 모든 컴퓨터와, 일반적으로 액세스하던 모든 세션 구성에 액세스할 수 있도록 허용하려고 합니다. 이 권한 부여 규칙은 개인 테스트 환경에서 사용되므로 관리자는 보안성이 없는 권한 부여 규칙을 만듭니다. - 관리자는 `Add-PswaAuthorizationRule * * *` cmdlet을 실행합니다(여기서 와일드카드 문자 **\*** 는 각각 모든 사용자, 모든 컴퓨터 및 모든 구성을 나타냄). - 이 규칙은 `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *` cmdlet과 동일합니다.

  > [!NOTE]
  > 이 규칙은 보안 환경에서는 사용하지 않는 것이 좋으며, Windows PowerShell 웹 액세스 권한 부여 규칙에서 제공되는 보안 계층을 무시합니다.

- 관리자는 사용자가 작업 그룹과 도메인을 모두 포함하는 환경에서 대상 컴퓨터에 연결할 수 있도록 해야 합니다. 여기서 작업 그룹 컴퓨터는 도메인의 대상 컴퓨터에 연결하는 데 사용되기도 하며, 도메인 컴퓨터는 작업 그룹의 대상 컴퓨터에 연결하는 데 사용되기도 합니다. 관리자에게는 작업 그룹의 게이트웨이 서버인 *PswaServer*가 있고, 대상 컴퓨터 *srv1.contoso.com* 은 도메인에 있습니다. 사용자 *Chris*는 작업 그룹 게이트웨이 서버와 대상 컴퓨터에서 모두 인증된 로컬 사용자입니다. 작업 그룹 서버에서 Chris의 사용자 이름은 *chrisLocal*;이며, 대상 컴퓨터에서는 *contoso\\chris*입니다. 관리자는 다음 규칙을 추가하여 Chris에게 srv1.contoso.com에 대한 액세스 권한을 부여합니다.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal `
   -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

위 규칙의 예에서는 게이트웨이 서버에서 Chris를 인증한 다음 *srv1*에 대한 액세스 권한을 부여합니다. 로그인 페이지에서 Chris는 **옵션 연결 설정** 영역(*contoso\\chris*)에서 두 번째 자격 증명 집합을 입력해야 합니다. 게이트웨이 서버는 추가 자격 증명 집합을 사용하여 대상 컴퓨터인 *srv1.contoso.com*에서 사용자를 인증합니다.

위 시나리오에서는 다음 작업에 성공하고 한 가지 이상의 권한 부여 규칙에 따라 허용된 후에만 Windows PowerShell 웹 액세스를 대상 컴퓨터에 연결할 수 있습니다.

1. *server_name*\\*user_name* 형식의 사용자 이름을 권한 부여 규칙에 추가하여 작업 그룹 게이트웨이 서버에서 인증

2. **옵션 연결 설정** 영역의 로그인 페이지에서 제공된 대체 자격 증명을 사용하여 대상 컴퓨터에서 인증

   > [!NOTE]
   > 게이트웨이 및 대상 컴퓨터가 다른 작업 그룹이나 도메인에 있을 경우, 두 개의 작업 그룹 컴퓨터나 두 개의 도메인 또는 작업 그룹과 도메인 간에 트러스트 관계가 설정되어 있어야 합니다. 이 관계는 Windows PowerShell 웹 액세스 권한 부여 규칙 cmdlet을 사용하여 구성할 수 없습니다. 권한 규칙이 컴퓨터 간의 트러스트 관계를 정의하지는 않습니다. 즉 권한 규칙은 특정 대상 컴퓨터와 세션 구성에 연결하는 사용자만 인증할 수 있습니다. 서로 다른 도메인 간에 트러스트 관계를 구성하는 방법에 대한 자세한 내용은 [도메인 및 포리스트 트러스트 만들기](https://technet.microsoft.com/library/cc794775.aspx)를 참조하세요.
   > 신뢰할 수 있는 호스트 목록에 작업 그룹 컴퓨터를 추가하는 방법에 대한 자세한 내용은 [서버 관리자를 통한 원격 관리](https://technet.microsoft.com/library/dd759202.aspx)를 참조하세요.

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>여러 사이트에 단일 권한 부여 규칙 집합 사용

권한 부여 규칙은 XML 파일에 저장됩니다. 기본적으로 XML 파일의 경로 이름은 `$env:windir\Web\PowershellWebAccess\data\AuthorizationRules.xml`입니다.

권한 부여 규칙 XML 파일은 **powwa.config** 파일에 저장되며 이 파일은 `$env:windir\Web\PowershellWebAccess\data`에 있습니다. 관리자는 기본 설정이나 요구 사항에 맞춰 이 **powwa.config**에 포함된 기본 경로를 변경할 수 있습니다. 관리자가 파일 위치를 변경할 수 있으므로 여러 Windows PowerShell 웹 액세스 게이트웨이에서 동일한 권한 부여 규칙을 사용해야 할 경우 그러한 구성이 가능합니다.

## <a name="session-management"></a>세션 관리

기본적으로 Windows PowerShell 웹 액세스에서는 사용자가 한 번에 세 세션까지 사용할 수 있습니다. 하지만 IIS 관리자를 사용하여 사용자당 여러 세션을 지원하도록 웹 애플리케이션의 **web.config** 파일을 편집할 수 있습니다. **web.config** 파일의 경로는 `$env:windir\Web\PowerShellWebAccess\wwwroot\Web.config` 입니다.

기본적으로 IIS 웹 서버는 설정이 편집될 경우 애플리케이션 풀을 다시 시작하도록 구성됩니다. 예를 들어 **web.config** 파일이 변경되면 애플리케이션 풀이 다시 시작됩니다. **Windows PowerShell 웹 액세스**에서는 메모리 내 세션 상태가 사용되므로, 애플리케이션 풀이 다시 시작되면 **Windows PowerShell 웹 액세스** 세션에 로그인한 사용자는 해당 세션을 잃어버리게 됩니다.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>로그인 페이지의 기본 매개 변수 설정

Windows PowerShell 웹 액세스 게이트웨이가 Windows Server 2012 R2에서 실행되는 경우 Windows PowerShell 웹 액세스 로그인 페이지에 표시되는 설정에 대한 기본값을 구성할 수 있습니다. 이전 단락에 설명된 **web.config** 파일에서 값을 구성할 수 있습니다. 로그인 페이지 설정에 대한 기본값은 web.config 파일의 **appSettings** 섹션에 있습니다. 다음은 **appSettings** 섹션의 예입니다. 이러한 설정에 유효한 값은 대부분 Windows PowerShell에서 [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) cmdlet의 해당 매개 변수에 대한 값과 동일합니다.

예를 들어 다음 코드 블록에 표시된 `defaultApplicationName` 키는 대상 컴퓨터의 **$PSSessionApplicationName** 기본 설정 변수 값입니다.

```xml
  <appSettings>
      <add key="maxSessionsAllowedPerUser" value="3"/>
      <add key="defaultPortNumber" value="5985"/>
      <add key="defaultSSLPortNumber" value="5986"/>
      <add key="defaultApplicationName" value="WSMAN"/>
      <add key="defaultUseSslSelection" value="0"/>
      <add key="defaultAuthenticationType" value="0"/>
      <add key="defaultAllowRedirection" value="0"/>
      <add key="defaultConfigurationName" value="Microsoft.PowerShell"/>
  </appSettings>
```

### <a name="time-outs-and-unplanned-disconnections"></a>시간 제한 및 계획되지 않은 연결 끊김

Windows PowerShell 웹 액세스 세션의 시간이 초과됩니다. Windows Server 2012에서 실행되는 Windows PowerShell 웹 액세스에서는 15분 동안 세션 활동이 없을 경우 로그인한 사용자에게 시간 초과 메시지가 표시됩니다. 이 메시지가 표시된 후 5분 이내에 사용자가 응답하지 않으면 세션이 종료되고 사용자는 로그아웃됩니다. IIS 관리자에서 웹 사이트 설정 중 세션의 시간 초과 기간을 변경할 수 있습니다.

Windows Server 2012 R2에서 실행되는 Windows PowerShell 웹 액세스에서는 기본적으로 20분 동안 활동이 없을 경우 세션이 시간 초과됩니다. 사용자가 직접 세션을 닫았기 때문이 아니라 네트워크 오류나 기타 계획되지 않은 종료 또는 실패로 인해 웹 기반 콘솔의 세션에서 연결이 끊어진 경우 클라이언트 쪽의 시간 제한 기간이 경과할 때까지 Windows PowerShell 웹 액세스 세션이 대상 컴퓨터에 연결된 상태로 계속 실행됩니다. 기본값인 20분 또는 게이트웨이 관리자가 지정한 시간 제한 기간 중 더 짧은 시간 후에 세션 연결이 끊어집니다.

게이트웨이 서버가 Windows Server 2012 R2를 실행하는 경우 Windows PowerShell 웹 액세스를 통해 사용자가 나중에 저장된 세션에 다시 연결할 수 있지만 네트워크 오류, 계획되지 않은 종료 또는 기타 실패로 인해 세션 연결이 끊어진 경우에는 게이트웨이 관리자가 지정한 시간 제한 기간이 경과할 때까지 사용자가 저장된 세션을 보거나 다시 연결할 수 없습니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 웹 액세스 설치 및 사용](https://technet.microsoft.com/library/hh831611(v=ws.11).aspx)

[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)

[Windows PowerShell Web Access Cmdlets](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)(Windows PowerShell 웹 액세스 Cmdlet)
