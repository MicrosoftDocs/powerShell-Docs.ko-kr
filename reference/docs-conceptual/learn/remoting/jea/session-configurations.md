---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: JEA 세션 구성
description: 세션 구성은 JEA 엔드포인트를 사용할 수 있는 사용자 및 해당 사용자가 액세스할 수 있는 역할을 정의합니다.
ms.openlocfilehash: b616d5bf260bbdfe89b6422fd4a8b4866f7fdc67
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501561"
---
# <a name="jea-session-configurations"></a>JEA 세션 구성

JEA 엔드포인트는 PowerShell 세션 구성 파일을 만들고 등록하여 시스템에 등록합니다. 세션 구성은 JEA 엔드포인트를 사용할 수 있는 사용자 및 해당 사용자가 액세스할 수 있는 역할을 정의합니다. 또한 JEA 세션의 모든 사용자에게 적용되는 글로벌 설정을 정의합니다.

## <a name="create-a-session-configuration-file"></a>세션 구성 파일 만들기

JEA 엔드포인트를 등록하려면 해당 엔드포인트가 구성되는 방법을 지정해야 합니다. 고려해야 할 많은 옵션이 있습니다. 가장 중요한 옵션은 다음과 같습니다.

- JEA 엔드포인트에 액세스할 수 있는 사용자
- 할당된 역할
- JEA가 내부적으로 사용하는 ID
- JEA 엔드포인트의 이름

이러한 옵션은 PowerShell 세션 구성 파일로 알려진 확장명이 `.pssc`인 PowerShell 데이터 파일에 정의되어 있습니다. 세션 구성 파일은 임의의 텍스트 편집기를 사용하여 편집할 수 있습니다.

다음 명령을 실행하여 빈 템플릿 구성 파일을 만듭니다.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> 템플릿 파일에는 기본적으로 가장 일반적인 구성 옵션만 포함되어 있습니다. 생성된 PSSC에 적용 가능한 모든 설정을 포함하려면 `-Full` 스위치를 사용하세요.

`-SessionType RestrictedRemoteServer` 필드는 세션 구성이 보안 관리를 위해 JEA에서 사용됨을 나타냅니다. 이 유형의 세션은 **NoLanguage** 모드에서 작동하며 다음과 같은 기본 명령(및 별칭)에만 액세스할 수 있습니다.

- Clear-Host(cls, clear)
- Exit-PSSession(exsn, exit)
- Get-Command(gcm)
- Get-FormatData
- Get-Help
- Measure-Object(measure)
- Out-Default
- Select-Object(select)

PowerShell 공급자와 외부 프로그램(실행 파일 또는 스크립트)은 모두 사용할 수 없습니다.

언어 모드에 대한 자세한 내용은 [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes)를 참조하세요.

### <a name="choose-the-jea-identity"></a>JEA ID 선택

백그라운드에서 JEA에는 연결된 사용자의 명령을 실행할 때 사용할 ID(계정)가 필요합니다.
세션 구성 파일에서 JEA가 사용하는 ID를 정의합니다.

#### <a name="local-virtual-account"></a>로컬 가상 계정

로컬 가상 계정은 JEA 엔드포인트에 대해 정의된 모든 역할이 로컬 머신을 관리하는 데 사용되고 로컬 관리자 계정으로 명령을 성공적으로 실행할 수 있는 경우에 유용합니다.
가상 계정은 특정 사용자에게 고유하고 해당 PowerShell 세션 기간 동안만 지속하는 임시 계정입니다. 구성원 서버 또는 워크스테이션에서 가상 계정은 로컬 컴퓨터의 **Administrators** 그룹에 속합니다. Active Directory 도메인 컨트롤러에서 가상 계정은 도메인의 **Domain Admins** 그룹에 속합니다.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

세션 구성에서 정의된 역할에 전체 관리 권한이 필요하지 않는 경우 가상 계정이 속할 보안 그룹을 지정할 수 있습니다. 구성원 서버 또는 워크스테이션에서 지정된 보안 그룹은 도메인의 그룹이 아니라 로컬 그룹이어야 합니다.

하나 이상의 보안 그룹을 지정하면 가상 계정이 로컬 또는 도메인 관리자 그룹에 할당되지 않습니다.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> 가상 계정에는 일시적으로 로컬 서버 보안 정책에서 서비스 권한으로 로그온 권한이 부여됩니다. 정책에서 지정된 VirtualAccountGroups 중 하나에 이 권한이 이미 부여된 경우 개별 가상 계정은 더 이상 추가되지 않고 정책에서 제거됩니다. 도메인 컨트롤러와 같이 도메인 컨트롤러 보안 정책에 대한 수정 버전을 긴밀히 감사하는 시나리오에 유용할 수 있습니다. 2018년 11월 이후 롤업을 포함한 Windows Server 2016 또는 2019년 1월 이후 롤업을 포함한 Windows Server 2019에서만 제공됩니다.

#### <a name="group-managed-service-account"></a>그룹 관리 서비스 계정

GMSA(그룹 관리 서비스 계정)는 JEA 사용자가 파일 공유 및 웹 서비스 등의 네트워크 리소스에 액세스해야 하는 경우 사용하기에 적합한 ID입니다. GMSA는 도메인 내의 모든 머신에 있는 리소스를 인증하는 데 사용되는 도메인 ID를 제공합니다. GMSA가 제공하는 권한은 액세스 중인 리소스에 의해 결정됩니다. 머신 또는 서비스 관리자가 GMSA에 대한 권한을 명시적으로 부여하지 않는 한, 모든 머신 또는 서비스에 대한 관리자 권한도 없습니다.

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

GMSA는 필요한 경우에만 사용해야 합니다.

- GMSA를 사용할 때 사용자에 대한 작업을 거슬러 올라가서 추적하는 것은 어렵습니다. 모든 사용자는 동일한 실행 ID를 공유합니다. PowerShell 세션 기록 및 로그를 검토하여 개별 사용자와 해당 작업 간의 상관 관계를 지정해야 합니다.

- GMSA는 연결하는 사용자가 액세스할 필요가 없는 많은 네트워크 리소스에 대한 액세스 권한을 가질 수 있습니다. 항상 JEA 세션에서 유효 권한을 제한하여 최소 권한 원칙을 따르도록 합니다.

> [!NOTE]
> 그룹 관리 서비스 계정은 PowerShell 5.1 이상을 사용하는 도메인 조인 머신에서만 사용할 수 있습니다.

JEA 세션 보안에 대한 자세한 내용은 [보안 고려 사항](security-considerations.md) 문서를 참조하세요.

### <a name="session-transcripts"></a>세션 기록

사용자의 세션의 기록을 자동으로 기록하도록 JEA 엔드포인트를 구성하는 것이 좋습니다. PowerShell 세션 기록은 연결하는 사용자, 사용자에게 할당된 실행 ID 및 사용자가 실행한 명령에 대한 정보를 포함합니다. 이러한 기록은 시스템에 대한 특정 변경 내용을 수행한 사용자를 파악해야 하는 감사 팀에게 유용할 수 있습니다.

세션 구성 파일에서 자동 기록을 구성하려면 기록이 저장되는 폴더의 경로를 제공합니다.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

기록은 디렉터리에 대한 읽기 및 쓰기 권한이 필요한 **로컬 시스템** 계정에 의해 폴더에 기록됩니다. 표준 사용자는 폴더에 대한 액세스 권한이 없어야 합니다. 기록을 감사할 수 있는 액세스 권한이 있는 보안 관리자의 수를 제한합니다.

### <a name="user-drive"></a>사용자 드라이브

연결하는 사용자가 JEA 엔드포인트간에 파일을 복사해야 하는 경우 세션 구성 파일에서 사용자 드라이브를 사용하도록 설정할 수 있습니다. 사용자 드라이브는 각 연결하는 사용자에 대해 고유한 폴더에 매핑되는 **PSDrive** 입니다. 이 폴더를 통해 사용자는 전체 파일 시스템에 대한 액세스 권한을 부여하거나 FileSystem 공급자를 노출하지 않고 시스템으로 간에 파일을 복사할 수 있습니다. 사용자 드라이브 콘텐츠는 세션 전체에서 유지되어 네트워크 연결이 중단될 수 있는 상황을 수용합니다.

```powershell
MountUserDrive = $true
```

기본적으로 사용자 드라이브를 사용하여 사용자당 최대 50MB의 데이터를 저장할 수 있습니다. *UserDriveMaximumSize* 필드를 사용하여 사용자가 사용할 수 있는 데이터의 양을 제한할 수 있습니다.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

사용자 드라이브의 데이터가 유지되지 않게 하려는 경우 매일 밤 자동으로 폴더를 정리하도록 시스템에 대한 예약된 작업을 구성할 수 있습니다.

> [!NOTE]
> 사용자 드라이브는 PowerShell 5.1 이상에서만 사용할 수 있습니다.

PSDrives에 대한 자세한 내용은 [PowerShell 드라이브 관리](/powershell/scripting/samples/managing-windows-powershell-drives)를 참조하세요.

### <a name="role-definitions"></a>역할 정의

세션 구성 파일의 역할 정의는 **역할** 에 대한 **사용자** 의 매핑을 정의합니다. 이 필드에 포함된 모든 사용자 또는 그룹은 등록될 때 JEA 엔드포인트에 대한 사용 권한이 부여됩니다.
각 사용자 또는 그룹은 해시 테이블의 키로 한 번만 포함될 수 있지만, 역할은 여러 개가 할당될 수 있습니다. 역할 기능의 이름은 `.psrc` 확장명이 없는 역할 기능 파일의 이름이어야 합니다.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

사용자가 역할 정의에서 둘 이상의 그룹에 속하는 경우 각 역할에 대한 액세스 권한을 얻게 됩니다. 두 역할이 같은 cmdlet에 대한 액세스 권한을 부여하는 경우 사용자에게 최대로 허용되는 매개 변수 집합이 부여됩니다.

역할 정의 필드에서 로컬 사용자 또는 그룹을 지정할 때는 **localhost** 또는 와일드카드가 아닌 컴퓨터 이름을 사용해야 합니다. `$env:COMPUTERNAME` 변수를 검사하여 컴퓨터 이름을 확인할 수 있습니다.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>역할 기능 검색 순서

위의 예제에 표시된 것처럼 역할 기능은 역할 기능 파일의 기본 이름으로 참조됩니다. 파일의 기본 이름은 확장명이 없는 파일 이름입니다. 시스템에서 동일한 이름의 여러 역할 기능을 사용할 수 있는 경우 PowerShell은 암시적 검색 순서를 사용하여 유효 역할 기능 파일을 선택합니다. JEA는 이름이 같은 모든 역할 기능 파일에 대한 액세스 권한을 부여하지 **않습니다** .

JEA에서는 `$env:PSModulePath` 환경 변수를 사용하여 역할 기능 파일을 검색할 경로를 확인합니다. JEA는 이러한 경로 각각에서 "RoleCapabilities" 하위 폴더가 포함된 유효한 PowerShell 모듈을 찾습니다. 모듈을 가져오는 경우와 마찬가지로, JEA는 같은 이름의 사용자 지정 역할 기능보다 Windows와 함께 제공되는 역할 기능을 선호합니다.

명명에 관한 다른 모든 충돌의 경우는 Windows에서 디렉터리의 파일을 열거하는 순서에 따라 우선순위가 결정됩니다. 순서는 알파벳순으로 보장되지는 않습니다. 지정된 이름과 일치하는 첫 번째 역할 기능으로 검색된 것이 연결 사용자에게 사용됩니다. 역할 기능 검색 순서가 결정적이지 않으므로 역할 기능에는 고유한 파일 이름이 있는 것이 **좋습니다** .

### <a name="conditional-access-rules"></a>조건부 액세스 규칙

**RoleDefinitions** 필드에 포함된 모든 사용자 및 그룹에는 자동으로 JEA 엔드포인트에 대한 액세스 권한이 부여됩니다. 조건부 액세스 규칙을 사용하면 이 액세스 권한을 구체화하고 사용자가 할당된 역할에 영향을 주지 않는 추가 보안 그룹에 속하도록 할 수 있습니다. 이 기능은 Just In Time 권한 있는 액세스 권한 관리 솔루션, 스마트 카드 인증 또는 기타 다단계 인증 솔루션을 JEA와 통합하려는 경우에 유용합니다.

조건부 액세스 규칙은 세션 구성 파일에서 RequiredGroups 필드에 정의됩니다.
여기서 'And' 및 'Or' 키를 사용하여 규칙을 구성하는 해시 테이블(필요에 따라 중첩됨)을 제공할 수 있습니다. 다음은 이 필드를 사용하는 방법의 몇 가지 예입니다.

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> 조건부 액세스 규칙은 PowerShell 5.1 이상에서만 사용할 수 있습니다.

### <a name="other-properties"></a>기타 속성

세션 구성 파일도 역할 기능 파일이 수행할 수 있는 모든 작업을 수행할 수 있지만, 연결하는 사용자에게 다른 명령에 대한 액세스 권한을 부여하는 기능은 제외됩니다. 모든 사용자가 특정 cmdlet, 함수 또는 공급자에 액세스할 수 있게 하려는 경우 세션 구성 파일에서 직접 이렇게 할 수 있습니다.
세션 구성 파일에서 지원되는 속성의 전체 목록을 보려면 `Get-Help New-PSSessionConfigurationFile -Full`을 실행합니다.

## <a name="testing-a-session-configuration-file"></a>세션 구성 파일 테스트

[Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet을 사용하여 세션 구성 파일을 테스트할 수 있습니다. `.pssc` 파일을 수동으로 편집한 경우 세션 구성 파일을 테스트하는 것이 좋습니다. 테스트를 통해 구문이 올바른지 확인합니다. 세션 구성 파일이 이 테스트에 실패하면 시스템에 등록할 수 없습니다.

## <a name="sample-session-configuration-file"></a>샘플 세션 구성 파일

다음 예제에서는 JEA에 대한 세션 구성을 만들고 유효성을 검사하는 방법을 보여줍니다. 역할 정의는 편의성과 가독성을 위해 생성되어 `$roles` 변수에 저장되어 있습니다. 이는 작업을 수행하기 위한 요구 사항은 아닙니다.

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>세션 구성 파일 업데이트

역할에 대한 사용자의 매핑을 비롯한 JEA 세션 구성의 속성을 변경하려면 JEA 세션 구성을 [등록 취소](register-jea.md#unregistering-jea-configurations)해야 합니다. 그런 다음, 업데이트된 세션 구성 파일을 사용하여 JEA 세션 구성을 [다시 등록](register-jea.md)합니다.

## <a name="next-steps"></a>다음 단계

- [JEA 구성 등록](register-jea.md)
- [JEA 역할 작성](role-capabilities.md)
