---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: JEA 보안 고려 사항
ms.openlocfilehash: 9526e141517601ae3b6d6932cd3536fdf49aa9a6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084779"
---
# <a name="jea-security-considerations"></a>JEA 보안 고려 사항

> 적용 대상: Windows Powershell 5.0

JEA를 사용하면 컴퓨터의 영구 관리자 수를 줄여 보안 상태를 개선할 수 있습니다.
오용을 방지하기 위해 기본적으로 단단히 잠긴 시스템을 사용자가 관리하기 위한 진입점(PowerShell 세션 구성)을 만들어 이렇게 할 수 있습니다.
관리 작업을 수행하기 위해 컴퓨터에 대한 일부(그러나 제한되지는 않은) 액세스 권한이 필요한 사용자에게 JEA 엔드포인트에 대한 액세스 권한을 부여할 수 있습니다.
JEA를 통해 사용자는 직접 관리자 액세스 권한을 갖지 않고도 관리 명령을 실행할 수 있으므로 높은 권한이 있는 보안 그룹에서 해당 사용자를 제거할 수 있습니다(해당 사용자를 표준 사용자로 만듦).

이 항목에서는 JEA 보안 모델 및 모범 사례를 더 자세히 설명합니다.

## <a name="run-as-account"></a>실행 계정

각 JEA 엔드포인트에는 지정된 "실행 계정"이 있으며, 이 계정은 연결하는 사용자의 작업이 수행되는 계정입니다.
이 계정은 [세션 구성 파일](session-configurations.md)에서 구성할 수 있으며, 선택한 계정은 엔드포인트의 보안에 상당한 영향을 줍니다.

**가상 계정**은 실행 계정을 구성하는 권장 방법입니다.
가상 계정은 연결하는 사용자가 JEA 세션 기간 동안 사용하도록 만들어지는 일회성 임시 로컬 계정입니다.
해당 세션이 종료되는 즉시 가상 계정은 제거되고 더 이상 사용될 수 없습니다.
연결하는 사용자는 가상 계정의 자격 증명을 알지 못하므로 원격 데스크톱 또는 비제한 PowerShell 엔드포인트와 같은 다른 방법을 통해 가상 계정을 사용하여 시스템에 액세스할 수 없습니다.

기본적으로 가상 계정은 컴퓨터의 로컬 관리자 그룹에 속합니다.
따라서 시스템의 모든 항목을 관리할 수 있는 모든 권한은 있지만, 네트워크의 리소스를 관리할 수 있는 권한은 없습니다.
다른 컴퓨터에서 인증할 때 사용자 컨텍스트는 가상 계정이 아니라 로컬 컴퓨터 계정이 됩니다.

도메인 컨트롤러는 로컬 관리자 그룹이라는 개념이 없으므로 특수한 경우입니다.
대신, Domain Admins에 속한 가상 계정으로 도메인 컨트롤러에서 디렉터리 서비스를 관리할 수 있습니다.
도메인 ID는 여전히 JEA 세션이 인스턴스화된 도메인 컨트롤러에서 사용하도록 제한되며, 모든 네트워크 액세스는 대신 도메인 컨트롤러 컴퓨터 개체에서 오는 것처럼 보입니다.

두 경우 모두 가상 계정이 속해야 하는 보안 그룹을 명시적으로 정의할 수도 있습니다.
수행하는 작업이 로컬/도메인 관리자 권한 없이 수행될 수 있는 작업인 경우 이렇게 하는 것이 좋습니다.
이미 관리자에 대해 정의된 보안 그룹이 있는 경우 필요한 권한을 부여하려면 해당 그룹에 가상 계정 구성원 자격을 부여하기만 하면 됩니다.
가상 계정 그룹 구성원 자격은 워크스테이션 및 구성원 서버에서 로컬 보안 그룹으로 제한되지만, 도메인 컨트롤러에서는 도메인 보안 그룹의 구성원일 수만 있습니다.
가상 계정이 속하는 보안 그룹을 하나 이상 지정하고 나면 가상 계정이 더 이상 기본 그룹(로컬 관리자 또는 도메인 관리자)에 속하지 않게 됩니다.

아래 표에는 가상 계정에 대한 가능한 구성 옵션 및 해당 사용 권한이 요약되어 있습니다.

컴퓨터 유형                | 가상 계정 그룹 구성 | 로컬 사용자 컨텍스트                                      | 네트워크 사용자 컨텍스트
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
도메인 컨트롤러            | Default                             | 도메인 사용자, '*DOMAIN*\Domain Admins'의 구성원         | 컴퓨터 계정
도메인 컨트롤러            | 도메인 그룹 A 및 B               | 도메인 사용자, '*DOMAIN*\A', '*DOMAIN*\B'의 구성원       | 컴퓨터 계정
구성원 서버 또는 워크스테이션 | Default                             | 로컬 사용자, '*BUILTIN*\Administrators'의 구성원        | 컴퓨터 계정
구성원 서버 또는 워크스테이션 | 로컬 그룹 C 및 D                | 로컬 사용자, '*COMPUTER*\C' 및 '*COMPUTER*\D'의 구성원 | 컴퓨터 계정

보안 감사 이벤트 및 애플리케이션 이벤트 로그를 보면 각 JEA 사용자 세션에 고유 가상 계정이 있는 것을 알 수 있습니다.
이는 JEA 엔드포인트에서 사용자 작업을 추적할 때 명령을 실행한 원래 사용자까지 거슬러 올라가 추적하는 데 도움이 됩니다.
가상 계정 이름은 "WinRM Virtual Users\\WinRM\_VA\_*ACCOUNTNUMBER*\_*DOMAIN*\_*sAMAccountName*" 형식을 따릅니다. 예를 들어 도메인 "Contoso"의 사용자 "Alice"가 JEA 엔드포인트에서 서비스를 다시 시작하면 모든 서비스 제어 관리자 이벤트와 연결된 사용자 이름은 "WinRM Virtual Users\\WinRM\_VA\_1\_contoso\_alice"가 됩니다.


**gMSA(그룹 관리 서비스 계정)** 는 구성원 서버가 JEA 세션에서 네트워크 리소스에 대한 액세스 권한을 가져야 할 경우에 유용합니다.
이 경우에 대한 예제 사용 사례는 다른 컴퓨터에서 호스트되는 REST API에 대한 액세스를 제어하는 데 사용되는 JEA 엔드포인트입니다.
REST API에 대한 원하는 호출을 만드는 함수를 작성하기는 쉽지만, API로 인증하려면 네트워크 ID가 필요합니다.
그룹 관리 서비스 계정을 사용하면 계정을 사용할 수 있는 컴퓨터를 여전히 제어하면서도 "두 번째 홉"을 가능하게 합니다.
gMSA의 유효 권한은 gMSA 계정이 속하는 보안 그룹(로컬 또는 도메인)에 의해 정의됩니다.

JEA 엔드포인트가 gMSA 계정을 사용하도록 구성된 경우 모든 JEA 사용자의 작업은 같은 그룹 관리 서비스 계정에서 온 것으로 표시됩니다.
특정 사용자까지 거슬러 올라가 작업을 추적할 수 있는 유일한 방법은 PowerShell 세션 기록에서 실행된 명령 집합을 식별하는 것뿐입니다.

**Pass-thru 자격 증명**은 실행 계정을 지정하지 않은 상태로 PowerShell에서 연결 사용자의 자격 증명을 원격 서버의 실행 명령에 연결하려 할 때 사용됩니다.
이 구성은 연결하는 사용자에게 권한 있는 관리 그룹에 대한 직접 액세스 권한을 부여해야 하므로 JEA에는 권장되지 *않습니다*.
연결하는 사용자에게 이미 관리자 권한이 있으면 JEA를 전부 피하고 다른 비제한 방법을 통해 시스템을 관리할 수 있습니다.
자세한 내용은 [JEA는 관리자로부터 보호하지 않음](#jea-does-not-protect-against-admins) 방법에 대한 아래 섹션을 참조하세요.

**표준 실행 계정**을 사용하여 전체 PowerShell 세션이 실행될 사용자 계정을 지정할 수 있습니다.
고정 실행 계정을 사용하도록 설정된 세션 구성(`-RunAsCredential` 매개 변수 사용)은 JEA를 인식하지 않으므로 이는 중요한 구분입니다.
즉, 역할 정의가 더 이상 예상대로 작동하지 않고 엔드포인트에 액세스할 수 있는 권한이 있는 모든 사용자에게 같은 역할이 할당됩니다.

특정 사용자까지 거슬러 올라가 작업을 추적하는 어려움이 있고 사용자를 역할에 매핑하는 지원이 없으므로 JEA 엔드포인트에는 RunAsCredential을 사용하면 안 됩니다.

## <a name="winrm-endpoint-acl"></a>WinRM 엔드포인트 ACL

일반 PowerShell 원격 엔드포인트와 마찬가지로 WinRM 구성에는 JEA 엔드포인트에서 인증할 수 있는 사용자를 제어하는 별도의 ACL(액세스 제어 목록)이 JEA 엔드포인트별로 설정되어 있습니다.
잘못 구성된 경우 신뢰할 수 있는 사용자가 JEA 엔드포인트에 액세스할 수 없거나 신뢰할 수 없는 사용자가 액세스 권한을 얻을 수도 있습니다.
그러나 WinRM ACL이 사용자를 JEA 역할에 매핑하는 것에 영향을 주지는 않습니다.
이러한 매핑은 시스템에 등록된 세션 구성 파일의 *RoleDefinitions* 필드에 의해 제어됩니다.

기본적으로 세션 구성 파일 및 하나 이상의 역할 기능을 사용하여 JEA 엔드포인트를 등록하면 WinRM ACL은 하나 이상의 역할에 대한 모든 사용자 매핑이 엔드포인트에 액세스할 수 있도록 구성됩니다.
예를 들어 다음 명령을 사용하여 구성된 JEA 세션은 *CONTOSO\JEA\_Lev1* 및 *CONTOSO\JEA\_Lev2*에 대한 모든 권한을 부여합니다.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

[Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet을 사용하여 사용자 권한을 감사할 수 있습니다.

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

액세스 권한을 갖는 사용자를 변경하려면 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI`를 실행하여 대화형 프롬프트를 사용하거나 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>`을 실행하여 사용 권한을 업데이트합니다.
JEA 엔드포인트에 액세스하려면 사용자에게 최소한 *Invoke* 권한이 있어야 합니다.

추가 사용자가 JEA 엔드포인트에 대한 액세스 권한을 부여받았지만 세션 구성 파일에 정의된 어떠한 역할에도 속하지 않는 경우 JEA 세션을 시작할 수는 있지만 기본 cmdlet에만 액세스할 수 있습니다.
`Get-PSSessionCapability`를 실행하여 JEA 엔드포인트의 사용자 권한을 감사할 수 있습니다.
JEA 엔드포인트에서 사용자가 액세스할 수 있는 명령 감사에 대한 자세한 내용은 [JEA에 대한 감사 및 보고](audit-and-report.md) 문서를 확인하세요.

## <a name="least-privilege-roles"></a>최소 권한 역할

JEA 역할을 디자인할 때는 백그라운드에서 실행되는 가상 또는 그룹 관리 서비스 계정이 흔히 로컬 컴퓨터를 관리할 수 있는 무제한 액세스 권한을 가진다는 사실을 기억해야 합니다.
JEA 역할 기능은 해당 권한 있는 컨텍스트를 사용하여 실행될 수 있는 명령 및 애플리케이션을 제한하여 사용될 수 있는 계정을 제한하는 데 도움이 됩니다.
잘못 디자인된 역할은 사용자가 JEA 경계를 벗어나거나 중요 정보에 대한 액세스 권한을 획득할 수 있는 위험한 명령이 실행되게 할 수 있습니다.

예를 들어 다음과 같은 역할 기능 항목을 생각해 봅니다.

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

이 역할 기능을 통해 사용자는 Microsoft.PowerShell.Management 모듈에서 명사 "Process"를 사용하여 모든 PowerShell cmdlet을 실행할 수 있습니다.
사용자는 `Get-Process`와 같은 cmdlet에 액세스하여 시스템에서 실행되고 있는 애플리케이션을 파악하고 `Stop-Process`에 액세스하여 응답 없는 애플리케이션을 종료해야 할 수 있습니다.
그러나 이 항목은 전체 관리자 권한으로 임의 프로그램을 시작하는 데 사용될 수 있는 `Start-Process`도 허용합니다.
프로그램이 시스템에 로컬로 설치될 필요가 없으므로 악의적 사용자가 연결하는 사용자에게 로컬 관리자 권한을 부여하고 맬웨어를 실행하는 등의 작업을 수행하는 프로그램을 파일 공유에서 손쉽게 시작할 수 있습니다.

이 역할 기능의 더 안전한 버전은 다음과 같습니다.

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

역할 기능에 와일드카드를 사용하지 말고 정기적으로 [유효 사용자 권한을 감사](audit-and-report.md#check-effective-rights-for-a-specific-user)하여 사용자가 액세스할 수 있는 명령을 파악해야 합니다.

## <a name="jea-does-not-protect-against-admins"></a>JEA는 관리자로부터 보호하지 않음

JEA의 핵심 원칙 중 하나는 관리자가 아닌 사용자가 *일부* 관리 작업을 수행할 수 있도록 하는 것입니다.
JEA는 이미 관리자 권한이 있는 사용자로부터 보호하지 않습니다.
환경의 "도메인 관리자", "로컬 관리자" 또는 기타 높은 권한이 있는 그룹에 속하는 사용자는 다른 방법을 통해 컴퓨터에 로그인하여 여전히 JEA의 보호를 해결할 수 있습니다.
예를 들어 RDP를 사용하여 로그인하거나 원격 MMC 콘솔을 사용하거나 비제한 PowerShell 엔드포인트에 연결할 수 있습니다.
시스템의 로컬 관리자는 추가 사용자가 시스템을 관리할 수 있도록 하거나 역할 기능을 변경하여 사용자가 해당 JEA 세션에서 수행할 수 있는 작업의 범위를 확장할 수 있도록 JEA 구성을 수정할 수도 있습니다.
따라서 JEA 사용자의 확장된 사용 권한을 평가하여 시스템에 대한 권한 있는 액세스 권한을 얻을 수 있는 다른 방법이 있는지 확인해야 합니다.

일반적인 방법은 정기적인 일상 유지 관리에는 JEA를 사용하고 비상 상황에서 사용자가 일시적으로 로컬 관리자가 될 수 있도록 하는 "Just In Time" 권한 있는 액세스 권한 관리 솔루션을 사용하는 것입니다.
이렇게 하면 사용자가 시스템에서 영구 관리자가 아니지만, 해당 사용 권한 사용을 문서화하는 워크플로를 완료하는 경우에만 해당 권한을 얻을 수 있도록 할 수 있습니다.