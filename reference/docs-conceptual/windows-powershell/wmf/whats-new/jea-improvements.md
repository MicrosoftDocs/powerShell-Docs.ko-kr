---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: JEA(Just Enough Administration)에 대한 개선 사항
ms.openlocfilehash: 9bb45ad2ddd459b99fc58610dfd8145992093624
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808919"
---
# <a name="improvements-to-just-enough-administration-jea"></a>JEA(Just Enough Administration)에 대한 개선 사항

충분한 관리는 PowerShell 원격을 통해 역할 기반 관리를 가능하게 하는 WMF 5.0의 새로운 기능입니다. 이 기능은 관리자가 아닌 사용자가 특정 명령, 스크립트 및 실행 파일을 관리자 권한으로 실행할 수 있도록 허용하여 기존의 제한된 엔드포인트 인프라를 확장합니다. 또한 사용자 환경의 전체 관리자 수는 줄이고 보안은 향상시킬 수 있습니다.

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>JEA 엔드포인트와의 파일 복사 제한

이제 원격으로 JEA 엔드포인트로나 JEA 엔드포인트에서 파일을 복사할 수 있으며 연결하는 사용자는 시스템에서 ‘어떤’ 파일도 복사할 수 없습니다. 이것이 가능하려면 연결하는 사용자에 대해 사용자 드라이브를 탑재하도록 PSSC 파일을 구성합니다. 사용자 드라이브는 연결하는 각 사용자에게 고유하고 세션 간에 유지되는 새 PSDrive입니다. `Copy-Item`을 사용하여 JEA 세션으로나 JEA 세센에서 파일을 복사하는 경우에는 사용자 드라이브에만 액세스할 수 있습니다. 다른 PSDrive로 파일을 복사하려고 하면 실패합니다.

JEA 세션 구성 파일에서 사용자 드라이브를 설정하려면 다음과 같은 새 필드를 사용합니다.

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

사용자 드라이브를 지원하는 폴더가 생성되는 위치`$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\` 엔드포인트에 연결하는 각 사용자에 대해 `$env:USERDOMAIN_$env:USERNAME`이라는 이름으로 폴더가 만들어집니다.

사용자 드라이브를 활용하고 사용자 드라이브를 노출하도록 구성된 JEA 엔드포인트로 또는 JEA 엔드포인트에서 파일을 복사하려면 `Copy-Item`에서 `-ToSession` 및 `-FromSession` 매개 변수를 사용합니다.

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine.
# You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

그런 다음 사용자 드라이브에 저장된 데이터를 처리하는 사용자 지정 함수를 작성하고 역할 기능 파일에서 이러한 함수를 사용자가 사용할 수 있도록 설정할 수 있습니다.

## <a name="support-for-group-managed-service-accounts"></a>그룹 관리 서비스 계정 지원

경우에 따라 사용자가 JEA 세션에서 수행해야 하는 작업을 위해 로컬 컴퓨터에 없는 리소스에 액세스해야 할 수 있습니다. JEA 세션이 가상 계정을 사용하도록 구성된 경우 이러한 리소스에 연결하려는 시도는 가상 계정이나 연결된 사용자가 아니라 로컬 컴퓨터의 ID가 하는 것으로 보입니다. TP5에서는 [그룹 관리 서비스 계정](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\))의 컨텍스트에서 JEA를 실행할 수 있도록 설정되어 있으므로 도메인 ID를 사용하여 네트워크 리소스에 훨씬 더 쉽게 액세스할 수 있습니다.

gMSA 계정으로 실행되도록 JEA 세션을 구성하려면 PSSC 파일에서 다음과 같은 새 키를 사용합니다.

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> 그룹 관리 서비스 계정은 격리나 제한된 범위의 가상 계정을 제공하지 않습니다.
> 연결하는 모든 사용자는 동일한 gMSA ID를 공유하므로 기업 전체에서 권한이 있을 수 있습니다. gMSA를 사용할 때는 주의해야 하며 항상 가능한 경우 로컬 컴퓨터로 제한된 가상 계정을 선택하는 것이 좋습니다.

## <a name="conditional-access-policies"></a>조건부 액세스 정책

JEA는 사용자가 JEA를 관리할 시스템에 연결된 경우 수행할 수 있는 작업을 제한하는 데 유용하지만, 사용자가 JEA를 사용할 수 있는 *시기*도 제한하려면 어떻게 하나요? 사용자가 JEA 세션을 설정하려면 속해 있어야 하는 보안 그룹을 지정할 수 있는 구성 옵션이 세션 구성 파일(.pssc)에 추가되었습니다. 이 옵션은 환경에 JIT(Just In Time) 시스템이 있고 사용자가 높은 권한의 JEA 엔드포인트에 액세스하기 전에 권한을 높이도록 하려는 경우에 특히 유용합니다.

PSSC 파일의 새 *RequiredGroups* 필드를 사용하여 사용자가 JEA에 연결할 수 있는지 여부를 결정하는 논리를 지정할 수 있습니다. 이를 위해서는 'And' 및 'Or' 키를 사용하는 해시테이블(필요에 따라 중첩됨)을 지정하여 규칙을 만듭니다. 다음은 이 필드를 사용하는 방법의 몇 가지 예입니다.

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a>수정됨: 이제 Windows Server 2008 R2에서 가상 계정이 지원됨

WMF 5.1에서는 이제 Windows Server 2008 R2에서 가상 계정을 사용할 수 있으므로 Windows Server 2008 R2부터 2016까지, 구성 및 기능 패리티를 일관되게 설정할 수 있습니다. Windows 7에서 JEA를 사용할 경우에는 가상 계정이 계속 지원되지 않습니다.
