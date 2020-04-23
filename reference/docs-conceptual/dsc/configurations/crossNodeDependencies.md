---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 노드 간 종속성 지정
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954110"
---
# <a name="specifying-cross-node-dependencies"></a>노드 간 종속성 지정

> 적용 대상: Windows Powershell 5.0

DSC는 다른 노드에서 구성에 대한 종속성을 지정하기 위한 구성에 사용할 수 있는 특별한 리소스 **WaitForAll**, **WaitForAny** 및 **WaitForSome**을 제공합니다. 이러한 리소스의 동작은 다음과 같습니다.

- **WaitForAll**: **NodeName** 속성에 정의된 모든 대상 노드에서 지정된 리소스가 원하는 상태이면 성공합니다.
- **WaitForAny**: **NodeName** 속성에 정의된 대상 노드 중 최소 하나 이상에서 지정된 리소스가 원하는 상태이면 성공합니다.
- **WaitForSome**: **NodeName** 속성과 더불어 **NodeCount** 속성을 지정합니다. **NodeCount**에서 지정되고 **NodeName** 속성에서 정의된 최소 숫자의 노드에서 리소스가 원하는 상태이면 리소스가 성공합니다.

## <a name="syntax"></a>구문

**WaitForAll** 및 **WaitForAny** 리소스는 동일한 구문을 공유합니다. 아래 예제에서 \<ResourceType\>을 **WaitForAny** 또는 **WaitForAll**로 바꿉니다.
**DependsOn** 키워드처럼 "[ResourceType]ResourceName"으로 이름 형식을 지정해야 합니다. 리소스가 개별 [구성](configurations.md)에 속하는 경우에는 **ConfigurationName**을 형식 문자열 "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]"에 포함합니다. **NodeName**은 현재 리소스가 기다려야 하는 컴퓨터 또는 노드입니다.

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

**WaitForSome** 리소스에는 위의 예제와 비슷한 구문이 있지만, **NodeCount** 키가 추가됩니다. **NodeCount**는 현재 리소스가 기다려야 하는 노드 수를 나타냅니다.

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

모든 **WaitForXXXX**는 다음 구문 키를 공유합니다.

|속성|  Description   |
|---------|---------------------|
| RetryIntervalSec| 다시 시도할 때까지의 시간(초)입니다. 최소값은 1입니다.|
| RetryCount| 최대 다시 시도 횟수입니다.|
| ThrottleLimit| 동시에 연결하는 컴퓨터의 수입니다. 기본값은 `New-CimSession` 기본값입니다.|
| DependsOn | 이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 자세한 내용은 [DependsOn](resource-depends-on.md)을 참조하세요.|
| PsDscRunAsCredential | [사용자 자격 증명을 사용하여 DSC 실행](./runAsUser.md) 참조 |

## <a name="using-waitforxxxx-resources"></a>WaitForXXXX 리소스 사용

각 **WaitForXXXX** 리소스는 지정된 리소스가 지정된 노드에서 완료될 때까지 기다립니다.
동일한 구성의 다른 리소스는 **DependsOn** 키를 사용하는 **WaitForXXXX** 리소스에 따라 ‘달라’질 수 있습니다. 

예를 들어 다음 구성에서 대상 노드는 대상 노드가 도메인에 가입하기 전에 **xADDomain** 리소스가 **MyDC** 노드에서 최대 30번의 시도를 15초 간격으로 완료할 때까지 대기합니다.

기본적으로 **WaitForXXX** 리소스는 한 번 시도한 다음, 실패합니다. 필수는 아니지만 일반적으로 **RetryCount** 및 **RetryIntervalSec**을 지정할 수 있습니다.

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

구성을 컴파일하면 두 개의 ".mof" 파일이 생성됩니다. [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet을 사용하여 대상 노드에 ".mof" 파일을 적용합니다.

> [!NOTE]
> **WaitForXXX** 리소스는 Windows 원격 관리를 사용하여 다른 노드의 상태를 확인합니다.
> WinRM에 대한 포트 및 보안 요구 사항에 대한 자세한 내용은 [PowerShell Remoting 보안 고려 사항](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [DSC 구성](configurations.md)
- [리소스 종속성 나열](resource-depends-on.md)
- [DSC 리소스](../resources/resources.md)
- [로컬 구성 관리자 구성](../managing-nodes/metaConfig.md)
