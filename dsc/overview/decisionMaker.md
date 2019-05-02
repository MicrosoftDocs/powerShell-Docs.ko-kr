---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 의사 결정자를 위한 Desired State Configuration 개요
ms.openlocfilehash: ce554d4bb994d4b1816d9d9c24599e4ef0e1c593
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079594"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a><span data-ttu-id="ae6a0-103">의사 결정자를 위한 Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="ae6a0-103">Desired State Configuration Overview for Decision Makers</span></span>

<span data-ttu-id="ae6a0-104">이 문서에서는 Windows PowerShell DSC(Desired State Configuration)를 사용하는 비즈니스 혜택에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-104">This document describes the business benefits of using Windows PowerShell Desired State Configuration (DSC).</span></span> <span data-ttu-id="ae6a0-105">기술 가이드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-105">It is not a technical guide.</span></span>

## <a name="what-is-desired-state-configuration"></a><span data-ttu-id="ae6a0-106">Desired State Configuration이란?</span><span class="sxs-lookup"><span data-stu-id="ae6a0-106">What Is Desired State Configuration?</span></span>

<span data-ttu-id="ae6a0-107">PowerShell DSC(Desired State Configuration)는 개방형 표준에 따라 Windows에 기본 제공되는 구성 관리 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-107">PowerShell Desired State Configuration is a configuration management platform built into Windows that is based on open standards.</span></span> <span data-ttu-id="ae6a0-108">DSC는 확장 중은 물론, 배포 수명 주기의 각 단계(개발, 테스트, 사전 프로덕션, 프로덕션)에서 안정적이고 일관되게 작동할 수 있을 만큼 유연합니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-108">DSC is flexible enough to function reliably and consistently in each stage of the deployment lifecycle (development, test, pre-production, production), as well as during scale-out.</span></span>

<span data-ttu-id="ae6a0-109">DSC의 중심은 [구성](../configurations/configurations.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-109">DSC centers around [configurations](../configurations/configurations.md).</span></span>
<span data-ttu-id="ae6a0-110">구성은 특정한 특징을 가진 컴퓨터("노드")로 구성된 환경을 읽기 쉽게 설명한 문서입니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-110">A configuration is an easy-to-read document that describes an environment made up of computers ("nodes") with specific characteristics.</span></span>
<span data-ttu-id="ae6a0-111">이 특성은 특정 Windows 기능을 사용할 수 있도록 할 만큼 간단하거나 SharePoint를 배포할 만큼 복잡할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-111">These characteristics can be as simple as ensuring a specific Windows feature is enabled or as complex as deploying SharePoint.</span></span>

<span data-ttu-id="ae6a0-112">DSC에서는 모니터링 및 보고 기능도 기본적으로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-112">DSC also has monitoring and reporting built in.</span></span>
<span data-ttu-id="ae6a0-113">시스템이 더 이상 호환하지 않는 경우 DSC에서는 경고를 발생시키고 시스템을 수정하는 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-113">If a system is no longer compliant, DSC can raise an alert and act to correct the system.</span></span>

## <a name="benefits-of-using-desired-state-configuration"></a><span data-ttu-id="ae6a0-114">Desired State Configuration을 사용할 때의 이점</span><span class="sxs-lookup"><span data-stu-id="ae6a0-114">Benefits of Using Desired State Configuration</span></span>

<span data-ttu-id="ae6a0-115">구성은 쉽게 읽고 저장하고 업데이트하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-115">Configurations are designed to be easily read, stored, and updated.</span></span>
<span data-ttu-id="ae6a0-116">구성에서는 대상 디바이스를 해당 상태에 배치하는 방법에 대한 지침을 작성하는 대신 대상 디바이스가 있어야 하는 상태를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-116">Configurations declare the state target devices should be in, instead of writing instructions for how to put them in that state.</span></span>
<span data-ttu-id="ae6a0-117">따라서 DSC를 통해 구성에 대해 배우고, 구성을 채택하고, 구현하고 유지 관리하는 데에 훨씬 적은 비용이 듭니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-117">This makes it much less costly to learn, adopt, implement, and maintain configuration through DSC.</span></span>

<span data-ttu-id="ae6a0-118">구성을 만드는 것은 복잡한 배포 단계를 단일 위치에서 "단일 데이터 소스(single source of truth)"로 캡처함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-118">Creating configurations means that complex deployment steps are captured as a "single source of truth" in a single location.</span></span>
<span data-ttu-id="ae6a0-119">이렇게 하면 특정 컴퓨터 집합의 반복된 배포의 오류 발생률이 훨씬 낮아지고,</span><span class="sxs-lookup"><span data-stu-id="ae6a0-119">This makes repeated deployments of a specific set of machines much less error-prone.</span></span>
<span data-ttu-id="ae6a0-120">결국 더 빠르고 안정적으로 배포할 수 있어 복잡한 배포의 소요 시간이 짧아집니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-120">In turn, making deployments faster and more reliable which enables a quick turnaround on complex deployments.</span></span>

<span data-ttu-id="ae6a0-121">[PowerShell 갤러리](https://powershellgallery.com)를 통해 구성을 공유할 수도 있습니다. 즉, 완료해야 하는 작업에 대한 일반적인 시나리오 및 모범 사례가 이미 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-121">Configurations are also shareable via the [PowerShell Gallery](https://powershellgallery.com) meaning common scenarios and best practices might already exist for the work that needs to be done.</span></span>


## <a name="desired-state-configuration-and-devops"></a><span data-ttu-id="ae6a0-122">Desired State Configuration 및 DevOps</span><span class="sxs-lookup"><span data-stu-id="ae6a0-122">Desired State Configuration and DevOps</span></span>

<span data-ttu-id="ae6a0-123">DSC는 내부 사용자든 외부 사용자든 최종 사용자에게 가치를 제공하는 데 중점을 둔 빠른 배포와 반복이 가능한 사용자, 프로세스 및 도구의 조합인 [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx)를 사용하여 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-123">DSC was designed with [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) in mind, a combination of people, processes, and tools that allow for rapid deployment and iteration focused on delivering value to end users whether internal or external.</span></span>
<span data-ttu-id="ae6a0-124">단일 구성으로 환경을 정의하면 개발자가 해당 요구 사항을 구성으로 인코딩하고, 해당 구성을 소스 제어에 대해 검사할 수 있습니다. 운영 팀은 오류가 발생하기 쉬운 수동 프로세스를 거치지 않고 쉽게 코드를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-124">Having a single configuration define an environment means that developers can encode their requirements into a configuration, check that configuration into source control, and operation teams can easily deploy code without having to go through error-prone manual processes.</span></span>

<span data-ttu-id="ae6a0-125">구성은 [데이터 기반](../configurations/configData.md)이기도 해서 운영 팀이 개발자의 개입 없이 환경을 쉽게 식별하고 변경할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-125">Configurations are also [data-driven](../configurations/configData.md), which makes it easier for ops to identify and change environments without developer intervention.</span></span>

## <a name="desired-state-configuration-on-premises-and-off-premises"></a><span data-ttu-id="ae6a0-126">Desired State Configuration 온-프레미스 및 오프-프레미스</span><span class="sxs-lookup"><span data-stu-id="ae6a0-126">Desired State Configuration On-Premises and Off-Premises</span></span>
<span data-ttu-id="ae6a0-127">DSC는 온-프레미스 배포와 오프-프레미스 배포를 모두 관리하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-127">DSC can be used to manage both on-premise and off-premise deployments.</span></span>
<span data-ttu-id="ae6a0-128">온-프레미스 솔루션의 경우 DSC에는 컴퓨터 관리를 중앙에 집중하고 그 상태에 대해 보고하는 데 사용할 수 있는 [끌어오기 서버](../pull-server/pullServer.md)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-128">For on-premise solutions, DSC has a [pull server](../pull-server/pullServer.md) that can be used to centralize management of machines and report on their status.</span></span>
<span data-ttu-id="ae6a0-129">클라우드 솔루션의 경우 DSC는 Windows를 사용할 수 있는 곳이라면 어디서든 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-129">For cloud solutions, DSC is usable wherever Windows is usable.</span></span>
<span data-ttu-id="ae6a0-130">DSC의 보고를 중앙에 집중하는 [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/)와 같은 Desired State Configuration을 기반으로 하는 Azure의 특정 제공 기능도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-130">There are also specific offerings from Azure built on Desired State Configuration, such as [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), which centralizes reporting of DSC.</span></span>

## <a name="dsc-and-compatibility"></a><span data-ttu-id="ae6a0-131">DSC 및 호환성</span><span class="sxs-lookup"><span data-stu-id="ae6a0-131">DSC and Compatibility</span></span>

<span data-ttu-id="ae6a0-132">DSC는 Windows Server 2012 R2에서 도입되었지만 WMF(Windows Management Framework) 패키지를 통해 이전 운영 체제에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-132">Although DSC was introduced in Windows Server 2012 R2, it is available for down-level operating systems via the Windows Management Framework (WMF) package.</span></span>
<span data-ttu-id="ae6a0-133">WMF에 대한 자세한 정보는 [PowerShell homepage(PowerShell 홈페이지)](/powershell/)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-133">More information about the WMF can be found on the [PowerShell homepage](/powershell/).</span></span>

<span data-ttu-id="ae6a0-134">DSC는 Linux를 관리하는 데에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-134">DSC can also be used to manage Linux.</span></span> <span data-ttu-id="ae6a0-135">자세한 내용은 [Linux용 DSC 시작](../getting-started/lnxGettingStarted.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ae6a0-135">For more information, see [Getting Started with DSC for Linux](../getting-started/lnxGettingStarted.md).</span></span>
