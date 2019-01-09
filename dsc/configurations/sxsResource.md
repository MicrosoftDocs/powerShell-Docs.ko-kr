---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 특정 버전의 설치된 리소스 가져오기
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402207"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="0bcaa-103">특정 버전의 설치된 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="0bcaa-103">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="0bcaa-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="0bcaa-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="0bcaa-105">PowerShell 5.0에서 DSC 리소스의 개별 버전 나란히 컴퓨터에 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bcaa-105">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="0bcaa-106">리소스 모듈 이름을 갖는 폴더가 버전에서 별도 버전의 리소스를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bcaa-106">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="0bcaa-107">별도 리소스 버전 side-by-side 설치</span><span class="sxs-lookup"><span data-stu-id="0bcaa-107">Installing separate resource versions side by side</span></span>

<span data-ttu-id="0bcaa-108">[Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet의 **MinimumVersion**, **MaximumVersion** 및 **RequiredVersion**를 사용하여 설치할 모듈 버전을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bcaa-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="0bcaa-109">버전을 지정하지 않고 **Install-Module**을 호출하면 가장 최근 버전이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="0bcaa-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="0bcaa-110">예를 들어 **xFailOverCluster** 모듈의 여러 버전이 있고, 각 버전에는 **xCluster** 리소스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bcaa-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="0bcaa-111">호출 **Install-module** 번호 버전을 지정 하지 않고 모듈의 최신 버전을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bcaa-111">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="0bcaa-112">모듈의 특정 버전을 설치 하려면 지정 된 **RequiredVersion** 1.1.0.0 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bcaa-112">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="0bcaa-113">이 설치 된 버전과 함께 지정된 된 버전을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="0bcaa-113">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="0bcaa-114">모두 표시 하는 이제 사용 하면 모듈의 버전 나열 `Get-DSCResource`합니다.</span><span class="sxs-lookup"><span data-stu-id="0bcaa-114">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="0bcaa-115">구성에서 리소스 버전 지정</span><span class="sxs-lookup"><span data-stu-id="0bcaa-115">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="0bcaa-116">컴퓨터에 설치 된 별도 리소스 버전에 있는 경우 구성에서 사용 하는 경우 해당 리소스의 버전을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bcaa-116">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="0bcaa-117">이 작업은 **Import-DscResource** 키워드의 **ModuleVersion** 매개 변수를 지정하여 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0bcaa-117">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="0bcaa-118">하나가 넘는 버전이 설치된 리소스의 리소스 모듈 버전을 지정하지 않으면 구성에서 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0bcaa-118">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="0bcaa-119">다음 구성에서는 호출할 리소스의 버전을 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0bcaa-119">The following configuration shows how to specify the version of the resource to call:</span></span>

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

><span data-ttu-id="0bcaa-120">참고: Import-dscresource의 ModuleVersion 매개 변수를 PowerShell 4.0에서 사용할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="0bcaa-120">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="0bcaa-121">PowerShell 4.0에서는 모듈 사양 개체를 Import-DscResource의 ModuleName 매개 변수로 전달하여 모듈 버전을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bcaa-121">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="0bcaa-122">모듈 사양 개체는 ModuleName 및 RequiredVersion 키가 포함된 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="0bcaa-122">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="0bcaa-123">예:</span><span class="sxs-lookup"><span data-stu-id="0bcaa-123">For example:</span></span>

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

<span data-ttu-id="0bcaa-124">이 작업은 PowerShell 5.0에서도 동작하지만, 이 경우 **ModuleVersion** 매개 변수를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0bcaa-124">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="0bcaa-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0bcaa-125">See also</span></span>

- [<span data-ttu-id="0bcaa-126">DSC 구성</span><span class="sxs-lookup"><span data-stu-id="0bcaa-126">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="0bcaa-127">DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="0bcaa-127">DSC Resources</span></span>](../resources/resources.md)
