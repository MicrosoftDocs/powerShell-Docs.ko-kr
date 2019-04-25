---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 28f4f8ae2bbddc8fb5ef9d95d3061a91fcc8ffe2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058729"
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>구성에서 동일한 중복 리소스 허용

DSC는 구성 내에서 충돌하는 리소스 정의를 허용하거나 처리하지 않습니다. 충돌을 해결하려고 하지 않고 단순히 실패합니다. 구성 다시 사용이 복합 리소스 등을 통해 더 많이 활용되면 충돌이 더 자주 발생합니다. 충돌하는 리소스 정의가 동일하면 DSC가 지능적이어서 이를 허용해야 합니다. 이 릴리스에서는 정의가 동일한 리소스 인스턴스가 여러 개 있어도 됩니다.

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

이전 릴리스에서는 'Web-Server' 역할을 설치하려는 WindowsFeature FE_IIS와 WindowsFeature Worker_IIS 인스턴스 간의 충돌로 인해 컴파일이 실패했습니다. 이러한 두 구성에서 구성하려는 *모든* 속성이 동일합니다. 이러한 두 리소스의 *모든* 속성이 동일하므로 이제 컴파일이 성공합니다.

두 리소스 간에 다른 속성이 있으면 동일한 것으로 간주되지 않고 컴파일이 실패합니다.

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

WindowsFeature FE_IIS와 WindowsFeature Worker_IIS 리소스가 더 이상 동일하지 않아 충돌하므로 매우 유사한 이 구성이 실패하게 됩니다.
