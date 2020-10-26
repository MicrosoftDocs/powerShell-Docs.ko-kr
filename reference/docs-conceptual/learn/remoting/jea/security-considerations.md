---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: JEA 보안 고려 사항
description: JEA를 통해 사용자는 전체 관리자 액세스 권한을 갖지 않고도 관리 명령을 실행할 수 있으므로 높은 권한이 있는 보안 그룹에서 해당 사용자를 제거할 수 있습니다.
ms.openlocfilehash: f65f9d6c6620261de0a9c8de7812637565ca1806
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501578"
---
# <a name="jea-security-considerations"></a>JEA 보안 고려 사항

JEA를 사용하면 컴퓨터의 영구 관리자 수를 줄여 보안 상태를 개선할 수 있습니다. JEA는 PowerShell 세션 구성을 사용하여 시스템을 관리할 수 있는 사용자에 대한 새 진입점을 만듭니다. 관리 작업을 수행하기 위해 머신에 대한 상승된(그러나 제한되지는 않은) 액세스 권한이 필요한 사용자에게 JEA 엔드포인트에 대한 액세스 권한을 부여할 수 있습니다. JEA를 통해 사용자는 전체 관리자 액세스 권한을 갖지 않고도 관리 명령을 실행할 수 있으므로 높은 권한이 있는 보안 그룹에서 해당 사용자를 제거할 수 있습니다.

## <a name="run-as-account"></a>실행 계정

각 JEA 엔드포인트에는 지정된 **실행** 계정이 있습니다. 이는 연결하는 사용자의 작업이 실행되는 계정입니다. 이 계정은 [세션 구성 파일](session-configurations.md)에서 구성할 수 있으며, 선택한 계정은 엔드포인트의 보안에 상당한 영향을 줍니다.

**가상 계정** 은 **실행** 계정을 구성하는 권장 방법입니다. 가상 계정은 연결하는 사용자가 JEA 세션 기간 동안 사용하도록 만들어지는 일회성 임시 로컬 계정입니다. 해당 세션이 종료되는 즉시 가상 계정은 제거되고 더 이상 사용할 수 없게 됩니다. 연결하는 사용자는 가상 계정의 자격 증명을 알지 못합니다. 가상 계정은 원격 데스크톱 또는 비제한 PowerShell 엔드포인트와 같은 다른 방법을 통해 시스템에 액세스하는 데 사용할 수 없습니다.

기본적으로 가상 계정은 머신의 로컬 **관리자** 그룹에 속합니다. 따라서 시스템의 모든 항목을 관리할 수 있는 모든 권한은 있지만, 네트워크의 리소스를 관리할 수 있는 권한은 없습니다.
다른 머신에서 인증할 때 사용자 컨텍스트는 가상 계정이 아니라 로컬 컴퓨터 계정이 됩니다.

도메인 컨트롤러는 로컬 **관리자** 그룹이 없으므로 특수한 경우입니다. 대신, 가상 계정은 **Domain Admins** 에 속하며 도메인 컨트롤러에서 디렉터리 서비스를 관리할 수 있습니다. 도메인 ID는 여전히 JEA 세션이 인스턴스화된 도메인 컨트롤러에서 사용할 수 있도록 제한됩니다. 모든 네트워크 액세스는 대신 도메인 컨트롤러 컴퓨터 개체에서 온 것으로 표시됩니다.

두 경우 모두 가상 계정이 속한 보안 그룹을 명시적으로 정의할 수 있습니다. 이는 로컬 또는 도메인 관리자 권한 없이 작업을 수행될 수 있는 좋은 방법입니다. 이미 관리자에 대해 정의된 보안 그룹이 있는 경우 해당 그룹에 가상 계정 멤버 자격을 부여합니다. 가상 계정 그룹 멤버 자격은 워크스테이션 및 멤버 서버의 로컬 보안 그룹으로 제한됩니다. 도메인 컨트롤러에서 가상 계정은 도메인 보안 그룹의 멤버여야 합니다.
가상 계정이 하나 이상의 보안 그룹에 추가되면 더 이상 기본 그룹(로컬 또는 도메인 관리자)에 속하지 않습니다.

다음 표에는 가능한 구성 옵셥과 가상 계정에 대한 해당 사용 권한이 요약되어 있습니다.

|        컴퓨터 유형         | 가상 계정 그룹 구성 |                   로컬 사용자 컨텍스트                    | 네트워크 사용자 컨텍스트 |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| 도메인 컨트롤러            | Default                             | 도메인 사용자, ' *DOMAIN* \Domain Admins'의 구성원         | 컴퓨터 계정     |
| 도메인 컨트롤러            | 도메인 그룹 A 및 B               | 도메인 사용자, ' *DOMAIN* \A', ' *DOMAIN* \B'의 구성원       | 컴퓨터 계정     |
| 구성원 서버 또는 워크스테이션 | Default                             | 로컬 사용자, ' *BUILTIN* \Administrators'의 구성원        | 컴퓨터 계정     |
| 구성원 서버 또는 워크스테이션 | 로컬 그룹 C 및 D                | 로컬 사용자, ' *COMPUTER* \C' 및 ' *COMPUTER* \D'의 구성원 | 컴퓨터 계정     |

보안 감사 이벤트 및 애플리케이션 이벤트 로그를 보면 각 JEA 사용자 세션에 고유 가상 계정이 있음을 알 수 있습니다. 이 고유한 계정은 JEA 엔드포인트에서 명령을 실행한 원래 사용자까지 거슬러 올라가 추적하는 데 도움이 됩니다. 가상 계정 이름은 `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>` 형식을 따릅니다. 예를 들어 도메인 **Contoso** 의 사용자 **Alice** 가 JEA 엔드포인트에서 서비스를 다시 시작하면 모든 서비스 제어 관리자 이벤트와 연결된 사용자 이름은 `WinRM Virtual Users\WinRM_VA_1_contoso_alice`가 됩니다.

**gMSA(그룹 관리 서비스 계정)** 는 구성원 서버가 JEA 세션에서 네트워크 리소스에 대한 액세스 권한을 가져야 할 경우에 유용합니다. 예를 들어 JEA 엔드포인트를 사용하여 다른 머신에 호스트되는 REST API 서비스에 대한 액세스를 제어하는 경우 REST API를 호출하는 함수를 작성하는 것은 쉽지만 API로 인증하려면 네트워크 ID가 필요합니다. 그룹 관리 서비스 계정을 사용하면 계정을 사용할 수 있는 컴퓨터를 유지 관리하면서 두 번째 홉을 가능하게 합니다. gMSA의 유효 권한은 gMSA 계정이 속하는 보안 그룹(로컬 또는 도메인)에 의해 정의됩니다.

JEA 엔드포인트가 gMSA를 사용하도록 구성된 경우 모든 JEA 사용자의 작업은 같은 gMSA에서 온 것으로 표시됩니다. 특정 사용자까지 거슬러 올라가 작업을 추적하는 유일한 방법은 PowerShell 세션 기록에서 실행된 명령 세트를 식별하는 것입니다.

**Pass-thru 자격 증명** 은 **실행** 계정을 지정하지 않은 경우에 사용됩니다. PowerShell은 연결하는 사용자의 자격 증명을 사용하여 원격 서버에서 명령을 실행합니다. 이를 위해서는 연결하는 사용자에게 권한 있는 관리 그룹에 대한 액세스 권한을 직접 부여해야 합니다. 이 구성은 JEA에 권장되지 **않습니다** . 연결하는 사용자에게 이미 관리자 권한이 있으면 JEA를 피하고 다른 비제한 방법을 통해 시스템을 관리할 수 있습니다. 자세한 내용은 [JEA는 관리자로부터 보호하지 않음](#jea-doesnt-protect-against-admins) 방법에 대한 아래 섹션을 참조하세요.

**표준 실행 계정** 을 사용하면 전체 PowerShell 세션이 실행되는 사용자 계정을 지정할 수 있습니다. 고정 **실행** 계정(`-RunAsCredential` 매개 변수 포함)을 사용하는 세션 구성은 JEA를 인식하지 않습니다. 역할 정의가 더 이상 예상대로 작동하지 않습니다. 엔드포인트에 액세스할 수 있는 권한이 부여된 모든 사용자에게 동일한 역할이 할당됩니다.

특정 사용자까지 거슬러 올라가 작업을 추적하는 어려움이 있고 사용자를 역할에 매핑하기 위한 지원이 부족하기 때문에 JEA 엔드포인트에서 **RunAsCredential** 을 사용하면 안 됩니다.

## <a name="winrm-endpoint-acl"></a>WinRM 엔드포인트 ACL

일반 PowerShell 원격 엔드포인트와 마찬가지로 각 JEA 엔드포인트에는 JEA 엔드포인트로 인증할 수 있는 사용자를 제어하는 별도의 ACL(액세스 제어 목록)이 있습니다. 잘못 구성된 경우 신뢰할 수 있는 사용자가 JEA 엔드포인트에 액세스하지 못할 수 있으며 신뢰할 수 없는 사용자가 액세스할 수 있습니다. WinRM ACL은 JEA 역할에 대한 사용자 매핑에는 영향을 주지 않습니다. 매핑은 엔드포인트를 등록하는 데 사용되는 세션 구성 파일의 **RoleDefinitions** 필드에 의해 제어됩니다.

기본적으로 JEA 엔드포인트에 여러 역할 기능이 있는 경우 WinRM ACL은 매핑된 모든 사용자에 대한 액세스를 허용하도록 구성됩니다. 예를 들어 다음 명령을 사용하여 구성된 JEA 세션은 `CONTOSO\JEA_Lev1` 및 `CONTOSO\JEA_Lev2`에 대한 모든 액세스 권한을 부여합니다.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

[Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet을 사용하여 사용자 권한을 감사할 수 있습니다.

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

액세스 권한을 갖는 사용자를 변경하려면 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI`를 실행하여 대화형 프롬프트를 사용하거나 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>`을 실행하여 사용 권한을 업데이트합니다. JEA 엔드포인트에 액세스하려면 사용자에게 최소한 *Invoke* 권한이 있어야 합니다.

정의된 역할을 액세스 권한이 있는 모든 사용자에게 매핑하지 않는 JEA 엔드포인트를 만드는 것이 가능합니다. 이러한 사용자는 JEA 세션을 시작할 수 있지만 기본 cmdlet에만 액세스할 수 있습니다. `Get-PSSessionCapability`를 실행하여 JEA 엔드포인트의 사용자 권한을 감사할 수 있습니다. 자세한 내용은 [JEA에 대한 감사 및 보고](audit-and-report.md)를 참조하세요.

## <a name="least-privilege-roles"></a>최소 권한 역할

JEA 역할을 디자인할 때는 백그라운드에서 실행되는 가상 및 그룹 관리 서비스 계정이 로컬 머신에 제한 없이 액세스할 수 있다는 점을 기억해야 합니다. JEA 역할 기능은 해당 권한 컨텍스트에서 실행할 수 있는 명령과 애플리케이션을 제한하는 데 도움이 됩니다.
잘못 디자인된 역할은 사용자가 JEA 경계를 벗어나거나 중요한 정보에 액세스할 수 있는 위험한 명령을 허용할 수 있습니다.

예를 들어 다음과 같은 역할 기능 항목을 생각해 봅니다.

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

이 역할 기능을 통해 사용자는 **Microsoft.PowerShell.Management** 모듈에서 명사 **Process** 를 사용하여 모든 PowerShell cmdlet을 실행할 수 있습니다. 사용자는 `Get-Process`와 같은 cmdlet에 액세스하여 시스템에서 실행되고 있는 애플리케이션을 확인하고 `Stop-Process`에 액세스하여 응답 없는 애플리케이션을 종료해야 할 수 있습니다. 그러나 이 항목은 전체 관리자 권한으로 임의 프로그램을 시작하는 데 사용될 수 있는 `Start-Process`도 허용합니다. 프로그램을 시스템에 로컬로 설치할 필요가 없습니다. 연결된 사용자는 사용자에게 로컬 관리자 권한을 부여하고 맬웨어를 실행하는 파일 공유에서 프로그램을 시작할 수 있습니다.

이 역할 기능의 더 안전한 버전은 다음과 같습니다.

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

역할 기능에 와일드카드를 사용하지 마세요. 정기적으로 [유효한 사용자 권한을 감사](audit-and-report.md#check-effective-rights-for-a-specific-user)하여 사용자가 액세스할 수 있는 명령을 파악하세요.

## <a name="jea-doesnt-protect-against-admins"></a>JEA는 관리자로부터 보호하지 않음

JEA의 핵심 원칙 중 하나는 관리자가 아닌 사용자가 일부 관리 작업을 수행할 수 있도록 하는 것입니다. JEA는 이미 관리자 권한이 있는 사용자로부터 보호하지 않습니다. **Domain Admins** , 로컬 **관리자** 또는 기타 높은 권한 있는 그룹에 속한 사용자는 다른 방법을 통해 JEA의 보호를 우회할 수 있습니다. 예를 들어 RDP를 사용하여 로그인하거나 원격 MMC 콘솔을 사용하거나 비제한 PowerShell 엔드포인트에 연결할 수 있습니다. 또한 시스템의 로컬 관리자는 JEA 구성을 수정하여 추가 사용자를 허용하거나 사용자가 해당 JEA 세션에서 수행할 수 있는 작업의 범위를 확장할 수 있도록 역할 기능을 변경할 수 있습니다. JEA 사용자의 확장된 사용 권한을 평가하여 시스템에 대한 권한 있는 액세스 권한을 얻는 다른 방법이 있는지 확인해야 합니다.

일반적인 방법은 정기적인 일상 유지 관리에는 JEA를 사용하고 비상 상황에서 사용자가 일시적으로 로컬 관리자가 될 수 있도록 하는 Just In Time 권한 있는 액세스 권한 관리 솔루션을 사용하는 것입니다. 이렇게 하면 사용자가 시스템에서 영구 관리자가 아니지만, 해당 권한 사용을 문서화하는 워크플로를 완료하는 경우에만 해당 권한을 얻을 수 있도록 할 수 있습니다.
