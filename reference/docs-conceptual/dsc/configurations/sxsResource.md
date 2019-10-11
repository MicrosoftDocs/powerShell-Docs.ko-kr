---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 특정 버전의 설치된 리소스 가져오기
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953990"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a>특정 버전의 설치된 리소스 가져오기

> 적용 대상: Windows Powershell 5.0

PowerShell 5.0에서 DSC 리소스의 개별 버전을 컴퓨터에 병렬로 설치할 수 있습니다. 리소스 모듈은 리소스의 개별 버전을 버전 명명된 폴더에 저장할 수 있습니다.

## <a name="installing-separate-resource-versions-side-by-side"></a>개별 리소스 버전을 병렬로 설치

[Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet의 **MinimumVersion**, **MaximumVersion** 및 **RequiredVersion**를 사용하여 설치할 모듈 버전을 지정할 수 있습니다. 버전을 지정하지 않고 **Install-Module**을 호출하면 가장 최근 버전이 설치됩니다.

예를 들어 **xFailOverCluster** 모듈의 여러 버전이 있고, 각 버전에는 **xCluster** 리소스가 포함되어 있습니다. 버전 번호를 지정하지 않고 **Install-Module**을 호출하면 가장 최근 버전의 모듈이 설치됩니다.

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

특정 버전의 모듈을 설치하려면 **RequiredVersion** 1.1.0.0을 지정합니다. 이렇게 하면 설치된 버전과 함께 지정된 버전이 병렬로 설치됩니다.

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

이제 `Get-DSCResource`를 사용할 때 두 버전의 모듈이 함께 나열됩니다.

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>구성에서 리소스 버전 지정

컴퓨터에 개별 리소스 버전이 설치되어 있으면, 해당 리소스의 버전을 지정한 후 구성에서 사용해야 합니다. 이 작업은 **Import-DscResource** 키워드의 **ModuleVersion** 매개 변수를 지정하여 수행합니다. 하나가 넘는 버전이 설치된 리소스의 리소스 모듈 버전을 지정하지 않으면 구성에서 오류가 발생합니다.

다음 구성에서는 호출할 리소스의 버전을 지정하는 방법을 보여 줍니다.

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

>참고: Import-DscResource의 ModuleVersion 매개 변수는 PowerShell 4.0에서 사용할 수 없습니다. PowerShell 4.0에서는 모듈 사양 개체를 Import-DscResource의 ModuleName 매개 변수로 전달하여 모듈 버전을 지정할 수 있습니다. 모듈 사양 개체는 ModuleName 및 RequiredVersion 키가 포함된 해시 테이블입니다. 예:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

이 작업은 PowerShell 5.0에서도 동작하지만, 이 경우 **ModuleVersion** 매개 변수를 사용하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목

- [DSC 구성](configurations.md)
- [DSC 리소스](../resources/resources.md)
