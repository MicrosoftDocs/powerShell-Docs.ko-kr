---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 노드 간 종속성 지정
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402199"
---
# <a name="specifying-cross-node-dependencies"></a>노드 간 종속성 지정

> 적용 대상: Windows Powershell 5.0

DSC는 다른 노드에서 구성에 대한 종속성을 지정하기 위한 구성에 사용할 수 있는 특별한 리소스 **WaitForAll**, **WaitForAny** 및 **WaitForSome**을 제공합니다. 이러한 리소스의 동작은 다음과 같습니다.

- **WaitForAll**: 지정된 된 리소스에 정의 된 모든 대상 노드에서 필요한 상태 이면 성공 합니다 **NodeName** 속성입니다.
- **WaitForAny**: 지정된 된 리소스에 정의 된 대상 노드 중 하나 이상에서 필요한 상태 이면 성공 합니다 **NodeName** 속성입니다.
- **WaitForSome**: 지정 된 **NodeCount** 속성 외에을 **NodeName** 속성입니다. **NodeCount**에서 지정되고 **NodeName** 속성에서 정의된 최소 숫자의 노드에서 리소스가 원하는 상태이면 리소스가 성공합니다.

## <a name="syntax"></a>구문

**WaitForAll** 하 고 **WaitForAny** 리소스는 동일한 구문을 공유 합니다. 바꿉니다 \<ResourceType\> 중 하나를 사용 하 여 아래 예제의 **WaitForAny** 또는 **WaitForAll**합니다.
같은 합니다 **DependsOn** "[ResourceType] ResourceName"으로 이름의 형식을 해야 키워드입니다. 별도의 리소스가 속한 경우 [구성](configurations.md)를 포함 합니다 **ConfigurationName** 서식이 지정 된 문자열에서 "[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName]"입니다. 합니다 **NodeName** 컴퓨터 또는 노드를 현재 리소스 기다려야 합니다.

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

합니다 **WaitForSome** 리소스 위의 예와 비슷한 구문을 갖지만 추가 합니다 **NodeCount** 키입니다. 합니다 **NodeCount** 현재 리소스에서 대기 해야 하는 노드 수를 나타냅니다.

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

모든 **WaitForXXXX** 다음 구문을 키를 공유 합니다.

|  속성 |  설명 | | RetryIntervalSec | 다시 시도 하기 전에 시간 (초) 수입니다. 최소값은 1입니다. | | RetryCount | 최대 다시 시도 횟수입니다. | | ThrottleLimit | 동시에 연결 하는 컴퓨터의 수입니다. 기본값은 `New-CimSession` 기본. | | DependsOn | 이 리소스를 구성 하기 전에 다른 리소스의 구성을 실행 해야 함을 나타냅니다. 자세한 내용은 [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | 참조 [DSC를 사용 하 여 사용자 자격 증명을 사용 하 여](./runAsUser.md) |


## <a name="using-waitforxxxx-resources"></a>WaitForXXXX 리소스 사용

각 **WaitForXXXX** 지정 된 노드에서 완료 하려면 지정된 된 리소스에 대 한 리소스를 대기 합니다. 그런 다음 동일한 구성의 다른 리소스 *에 따라 달라 집니다* 는 **WaitForXXXX** 사용 하 여 리소스를 **DependsOn** 키입니다.

예를 들어 다음 구성에서 대상 노드는 대상 노드가 도메인에 가입하기 전에 **xADDomain** 리소스가 **MyDC** 노드에서 최대 30번의 시도를 15초 간격으로 완료할 때까지 대기합니다.

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

구성을 컴파일하면 두 ".mof" 파일이 생성 됩니다. ".Mof" 파일을 모두 사용 하 여 대상 노드에 적용 합니다 [Start-dscconfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet

>**참고:** WaitForXXX 기본적으로 리소스 번 시도 하 고 실패 합니다. 필요한 경우에 일반적으로 하려는 지정 된 **RetryCount** 및 **RetryIntervalSec**합니다.

## <a name="see-also"></a>참고 항목

- [DSC 구성](configurations.md)
- [리소스 종속성을 사용 하 여](resource-depends-on.md)
- [DSC 리소스](../resources/resources.md)
- [로컬 구성 관리자 구성](../managing-nodes/metaConfig.md)
