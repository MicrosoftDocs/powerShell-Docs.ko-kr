---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 특정 버전의 설치된 리소스 가져오기
description: 이 문서에서는 특정 버전의 리소스 모듈을 설치하고 구성으로 가져오는 방법을 보여 줍니다.
ms.openlocfilehash: bb7b3273a5a3fed94fecd90dd3ea1e623fbc332b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645048"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="ceede-104">특정 버전의 설치된 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="ceede-104">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="ceede-105">적용 대상: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ceede-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="ceede-106">PowerShell 5.0에서 DSC 리소스의 개별 버전을 컴퓨터에 병렬로 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceede-106">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="ceede-107">리소스 모듈은 리소스의 개별 버전을 버전 명명된 폴더에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceede-107">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="ceede-108">개별 리소스 버전을 병렬로 설치</span><span class="sxs-lookup"><span data-stu-id="ceede-108">Installing separate resource versions side by side</span></span>

<span data-ttu-id="ceede-109">[Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet의 **MinimumVersion** , **MaximumVersion** 및 **RequiredVersion** 를 사용하여 설치할 모듈 버전을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceede-109">You can use the **MinimumVersion** , **MaximumVersion** , and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="ceede-110">버전을 지정하지 않고 **Install-Module** 을 호출하면 가장 최근 버전이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceede-110">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="ceede-111">예를 들어 **xFailOverCluster** 모듈의 여러 버전이 있고, 각 버전에는 **xCluster** 리소스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceede-111">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="ceede-112">버전 번호를 지정하지 않고 **Install-Module** 을 호출하면 가장 최근 버전의 모듈이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceede-112">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```Output
ImplementedAs   Name          ModuleName           Version    Properties
-------------   ----          ----------           -------    ----------
PowerShell      xCluster      xFailOverCluster     1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="ceede-113">특정 버전의 모듈을 설치하려면 **RequiredVersion** 1.1.0.0을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ceede-113">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="ceede-114">이렇게 하면 설치된 버전과 함께 지정된 버전이 병렬로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceede-114">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="ceede-115">이제 `Get-DSCResource`를 사용할 때 두 버전의 모듈이 함께 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceede-115">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```Output
ImplementedAs   Name          ModuleName            Version    Properties
-------------   ----          ----------            -------    ----------
PowerShell      xCluster      xFailOverCluster      1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster      xFailOverCluster      1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="ceede-116">구성에서 리소스 버전 지정</span><span class="sxs-lookup"><span data-stu-id="ceede-116">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="ceede-117">컴퓨터에 개별 리소스 버전이 설치되어 있으면, 해당 리소스의 버전을 지정한 후 구성에서 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ceede-117">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="ceede-118">이 작업은 **Import-DscResource** 키워드의 **ModuleVersion** 매개 변수를 지정하여 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ceede-118">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="ceede-119">하나가 넘는 버전이 설치된 리소스의 리소스 모듈 버전을 지정하지 않으면 구성에서 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ceede-119">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="ceede-120">다음 구성에서는 호출할 리소스의 버전을 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ceede-120">The following configuration shows how to specify the version of the resource to call:</span></span>

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

<span data-ttu-id="ceede-121">Import-DscResource의 ModuleVersion 매개 변수는 PowerShell 4.0에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ceede-121">The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="ceede-122">PowerShell 4.0에서는 모듈 사양 개체를 Import-DscResource의 ModuleName 매개 변수로 전달하여 모듈 버전을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceede-122">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="ceede-123">모듈 사양 개체는 ModuleName 및 RequiredVersion 키가 포함된 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="ceede-123">A module specification object is a hash table that contains ModuleName and RequiredVersion keys.</span></span> <span data-ttu-id="ceede-124">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="ceede-124">For example:</span></span>

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

<span data-ttu-id="ceede-125">이 작업은 PowerShell 5.0에서도 동작하지만, 이 경우 **ModuleVersion** 매개 변수를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ceede-125">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="ceede-126">추가 정보</span><span class="sxs-lookup"><span data-stu-id="ceede-126">See also</span></span>

- [<span data-ttu-id="ceede-127">DSC 구성</span><span class="sxs-lookup"><span data-stu-id="ceede-127">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="ceede-128">DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="ceede-128">DSC Resources</span></span>](../resources/resources.md)
