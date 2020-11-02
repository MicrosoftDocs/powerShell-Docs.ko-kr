---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Windows PowerShell 필요한 상태 구성 개요
description: DSC는 PowerShell에서 코드로 된 구성을 사용하여 IT 및 개발 인프라를 관리할 수 있게 해 주는 관리 플랫폼입니다.
ms.openlocfilehash: 4170603ea2733edb662a7ae32653676496cf7b5c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650910"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="3caac-104">Windows PowerShell 필요한 상태 구성 개요</span><span class="sxs-lookup"><span data-stu-id="3caac-104">Windows PowerShell Desired State Configuration Overview</span></span>

> <span data-ttu-id="3caac-105">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3caac-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="3caac-106">DSC는 PowerShell에서 코드로 된 구성을 사용하여 IT 및 개발 인프라를 관리할 수 있게 해 주는 관리 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="3caac-106">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="3caac-107">DSC를 사용하여 비즈니스에서 얻을 수 있는 이점은 [의사 결정자를 위한 필요한 상태 구성 개요](decisionMaker.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3caac-107">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="3caac-108">DSC를 사용하여 엔지니어링에서 얻을 수 있는 이점은 [엔지니어를 위한 필요한 상태 구성 개요](DscForEngineers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3caac-108">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="3caac-109">빨리 DSC를 사용하기 시작하려면 [DSC 빠른 시작](../quickstarts/website-quickstart.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3caac-109">To start using DSC quickly, see [DSC quick start](../quickstarts/website-quickstart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="3caac-110">주요 개념</span><span class="sxs-lookup"><span data-stu-id="3caac-110">Key Concepts</span></span>

<span data-ttu-id="3caac-111">DSC는 시스템의 구성, 배포 및 관리에 사용되는 선언적 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="3caac-111">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="3caac-112">이것은 세 가지 기본 요소로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3caac-112">It consists of three primary components:</span></span>

- <span data-ttu-id="3caac-113">[구성](../configurations/configurations.md)은 리소스의 인스턴스를 정의 및 구성하는 선언적 PowerShell 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="3caac-113">[Configurations](../configurations/configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span> <span data-ttu-id="3caac-114">구성 실행 시, DSC(및 구성에 의해 호출되는 리소스)는 시스템이 구성에 의해 배치된 상태로 존재하도록 단순히 "그대로 수행"하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3caac-114">Upon running the configuration, DSC (and the resources being called by the configuration) will simply "make it so", ensuring that the system exists in the state laid out by the configuration.</span></span> <span data-ttu-id="3caac-115">또한 DSC 구성은 idempotent입니다. LCM(로컬 구성 관리자)은 구성에서 선언하는 상태가 무엇이든 계속 컴퓨터가 해당 상태로 구성되어 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3caac-115">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="3caac-116">[리소스](../resources/resources.md)는 DSC에서 "실행을 맡는" 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="3caac-116">[Resources](../resources/resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="3caac-117">구성의 대상을 지정된 상태에 놓고 유지하는 코드가 여기에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3caac-117">They contain the code that put and keep the target of a configuration in the specified state.</span></span> <span data-ttu-id="3caac-118">리소스는 PowerShell 모듈 내에 상주하며, 파일이나 Windows 프로세스만큼 일반적이거나 Azure에서 실행되는 IIS 서버 또는 VM만큼 특별한 것을 모델링하도록 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3caac-118">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="3caac-119">[LCM(로컬 구성 관리자)](../managing-nodes/metaConfig.md)은 DSC에서 리소스와 구성 간 상호 작용을 이용할 때 사용하는 엔진입니다.</span><span class="sxs-lookup"><span data-stu-id="3caac-119">The [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span> <span data-ttu-id="3caac-120">LCM은 리소스가 구현한 제어 흐름을 사용하여 구성으로 정의된 상태를 유지하도록 시스템을 정기적으로 폴링합니다.</span><span class="sxs-lookup"><span data-stu-id="3caac-120">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span> <span data-ttu-id="3caac-121">시스템이 상태를 벗어나면 LCM은 리소스에 있는 코드를 호출하여 구성에 따라 “그대로 수행”하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3caac-121">If the system is out of state, the LCM makes calls to the code in resources to "make it so" according to the configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="3caac-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3caac-122">See Also</span></span>

- [<span data-ttu-id="3caac-123">DSC 구성</span><span class="sxs-lookup"><span data-stu-id="3caac-123">DSC Configurations</span></span>](../configurations/configurations.md)
- [<span data-ttu-id="3caac-124">DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="3caac-124">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="3caac-125">로컬 구성 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="3caac-125">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
