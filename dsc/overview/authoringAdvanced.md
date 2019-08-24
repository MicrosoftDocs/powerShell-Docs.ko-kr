---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: CI/CD 파이프라인에서 DSC의 역할 이해
ms.openlocfilehash: 7aec414b3d8e61d1daa1ce796184ac34dbbb43ce
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079831"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a><span data-ttu-id="28d74-103">CI/CD 파이프라인에서 DSC의 역할 이해</span><span class="sxs-lookup"><span data-stu-id="28d74-103">Understanding DSC's role in a CI/CD pipeline</span></span>

<span data-ttu-id="28d74-104">이 문서에서는 구성 및 리소스를 결합 하는 데 사용할 수 있는 방법의 유형을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-104">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="28d74-105">각 시나리오의 목표는 서버 배포 최종 상태에 연결하기 위해 여러 구성을 사용하는 경우 복잡성을 줄이기 위한 것으로 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-105">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span>
<span data-ttu-id="28d74-106">이에 대한 예제로는 애플리케이션 상태를 유지하는 애플리케이션 소유자 및 보안 기준의 변경을 해제하는 중앙 팀과 같이 서버 배포의 결과에 기여하는 여러 팀이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-106">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span>
<span data-ttu-id="28d74-107">장점 및 위험을 포함하여 각 접근 방식의 미묘한 차이는 여기에 자세히 설명돼 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-107">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![파이프라인](../images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="28d74-109">공동 작업 제작 기술의 유형</span><span class="sxs-lookup"><span data-stu-id="28d74-109">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="28d74-110">이 개념을 사용하기 위해 로컬 Configuration Manager에게 기본 제공된 두 가지 솔루션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-110">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

| <span data-ttu-id="28d74-111">개념</span><span class="sxs-lookup"><span data-stu-id="28d74-111">Concept</span></span> | <span data-ttu-id="28d74-112">자세한 정보</span><span class="sxs-lookup"><span data-stu-id="28d74-112">Detailed Information</span></span>
|-|-
| <span data-ttu-id="28d74-113">부분 구성</span><span class="sxs-lookup"><span data-stu-id="28d74-113">Partial Configurations</span></span> | [<span data-ttu-id="28d74-114">설명서</span><span class="sxs-lookup"><span data-stu-id="28d74-114">Documentation</span></span>](../pull-server/partialConfigs.md)
| <span data-ttu-id="28d74-115">복합 리소스</span><span class="sxs-lookup"><span data-stu-id="28d74-115">Composite Resources</span></span> | [<span data-ttu-id="28d74-116">설명서</span><span class="sxs-lookup"><span data-stu-id="28d74-116">Documentation</span></span>](../resources/authoringResourceComposite.md)

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="28d74-117">각 접근 방식의 영향에 대한 이해</span><span class="sxs-lookup"><span data-stu-id="28d74-117">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="28d74-118">서버 배포의 결과를 관리하려면 이러한 솔루션 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-118">Either of these solutions can be used to manage the outcome of a server deployment.</span></span>
<span data-ttu-id="28d74-119">그러나 각 방법을 사용하는 영향에는 큰 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-119">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="28d74-120">부분 구성</span><span class="sxs-lookup"><span data-stu-id="28d74-120">Partial Configurations</span></span>

<span data-ttu-id="28d74-121">부분 구성을 사용하는 경우 로컬 Configuration Manager는 여러 구성을 독립적으로 관리하도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-121">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span>
<span data-ttu-id="28d74-122">구성은 개별적으로 컴파일된 다음, 노드에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-122">Configurations are compiled independently and then assigned to the node.</span></span>
<span data-ttu-id="28d74-123">이렇게 하려면 LCM이 미리 각 구성의 이름으로 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-123">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![PartialConfiguration](../images/PartialConfiguration.jpg)

<span data-ttu-id="28d74-125">부분 구성은 종종 커뮤니케이션 또는 협업의 이점 없이 둘 이상의 팀에 서버의 구성에 대한 완벽한 제어를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-125">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="28d74-126">고객은 부분 구성이 리소스 충돌, 의도하지 않은 재정의 및 궁극적으로 자산의 참된 구성 제어 손실을 초래할 수 있다는 피드백을 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-126">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="28d74-127">또한 이 모델을 사용할 경우 각 제어 팀의 구성 변경이 릴리스 파이프라인을 통해 완벽하게 테스트되지 않아 프로덕션 환경에서 예기치 않은 결과를 초래할 수 있다는 피드백도 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-127">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="28d74-128">**서버에 릴리스된 모든 변경 내용을 평가하는 데 단일 파이프라인을 사용하는 것이 중요합니다.**</span><span class="sxs-lookup"><span data-stu-id="28d74-128">**It is critical that a single pipeline be used to evaluate all changes release to servers.**</span></span>

<span data-ttu-id="28d74-129">아래 그림에서 B 팀은 A 팀에 해당 부분 구성을 릴리스한 다음, A 팀은 두 구성이 모두 적용된 서버에 대해 해당 테스트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-129">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span>
<span data-ttu-id="28d74-130">이 모델에서 하나의 기관에만 프로덕션 환경에서 변경할 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-130">In this model, only one authority has permission to make changes in production.</span></span>

![PartialSinglePipeline](../images/PartialSinglePipeline.jpg)

<span data-ttu-id="28d74-132">B 팀에서 변경이 필요할 경우 A 팀의 원본 제어 환경에 대해 끌어오기 요청을 제출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-132">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span>
<span data-ttu-id="28d74-133">그런 다음, A 팀은 변경이 서버에서 호스팅된 서비스 또는 애플리케이션에서 오류를 일으키지 않을 것이라는 확신이 있는 경우 프로덕션 환경에 대한 릴리스 및 테스트 자동화를 사용하여 변경 내용을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-133">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="28d74-134">복합 리소스</span><span class="sxs-lookup"><span data-stu-id="28d74-134">Composite Resources</span></span>

<span data-ttu-id="28d74-135">복합 리소스는 단순히 리소스로 패키지된 DSC 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-135">A composite resource is simply a DSC Configuration packaged as a resource.</span></span>
<span data-ttu-id="28d74-136">복합 리소스를 허용하기 위해 LCM 구성에 대한 특별한 요구 사항은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-136">There are no special requirements for configuring LCM to accept composite resources.</span></span>
<span data-ttu-id="28d74-137">이 리소스는 하나의 MOF 파일의 새 구성 및 단일 컴파일 결과 내에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-137">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![CompositeResource](../images/CompositeResource.jpg)

<span data-ttu-id="28d74-139">복한 리소스에 대한 일반적인 시나리오는 두 개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-139">There are two common scenarios for composite resources.</span></span>
<span data-ttu-id="28d74-140">첫 번째 시나리오는 복잡성 및 고유한 추상 개념을 줄이는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-140">The first is to reduce complexity and abstract unique concepts.</span></span>
<span data-ttu-id="28d74-141">두 번째는 모든 테스트를 통과한 후 애플리케이션 팀이 해당 릴리스 파이프라인을 통해 프로덕션 환경에 안전하게 배포하도록 패키지된 기준을 허용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-141">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

<span data-ttu-id="28d74-142">복합 리소스는 작업 완성도를 빌드하면서 파이프라인을 사용하여 컴퍼지션 및 협업 둘 다의 수준을 올립니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-142">Composite resources promote both composition and collaboration using a pipeline while building operational maturity</span></span>

<span data-ttu-id="28d74-143">인식하지 않으면서 이미 복합 리소스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-143">You might be already using composite resources without realizing it.</span></span>
<span data-ttu-id="28d74-144">예제는 **ServiceSet**입니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-144">An example is **ServiceSet**.</span></span>
<span data-ttu-id="28d74-145">이 리소스는 개별적으로 나열하지 않고 여러 Windows 서비스의 상태를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-145">This resource manages the state of multiple Windows Services without listing them individually.</span></span>
<span data-ttu-id="28d74-146">Name 속성은 각 서비스의 이름을 제공하려면 문자열 배열을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-146">The Name property accepts an array of strings to provide the name of each service.</span></span>
<span data-ttu-id="28d74-147">구성을 컴파일하면 MOF에는 ServiceSet에 전달된 각 Name에 대한 고유한 서비스 섹션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-147">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="28d74-148">조직에는 모든 서버에 설치해야 하는 "에이전트" 또는 "미들웨어"가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-148">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span>
<span data-ttu-id="28d74-149">복합 리소스는 종속성, 설정 및 이러한 모든 도구 및 유틸리티의 구성을 관리하기 위한 최상의 해결책입니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-149">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="28d74-150">여러 서버에 걸쳐 있는 솔루션의 담당자 또는 담당팀은 해당 요구 사항을 포함하는 구성을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-150">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span>
<span data-ttu-id="28d74-151">다음으로, 복합 리소스 설명서에 제공된 지침을 사용하여 구성을 복합 리소스로 패키지합니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-151">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span>
<span data-ttu-id="28d74-152">마지막으로, 애플리케이션 팀이 해당 구성에서 새 복합 리소스를 사용할 수 있는 파일 공유 또는 NuGet 피드와 같은 위치에 해당 복합 리소스를 게시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-152">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="28d74-153">팀이 새 버전을 릴리스할 때마다 해당 복합 리소스에 대한 모듈 매니페스트의 버전 번호가 증가하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-153">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span>
<span data-ttu-id="28d74-154">애플리케이션 팀은 애플리케이션 종속성을 관리하기 위해 작성하는 구성에 복합 리소스를 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-154">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span>
<span data-ttu-id="28d74-155">운영/보안 팀이 해당 리소스의 새 버전을 릴리스하는 경우 새 변경 내용에 대해 애플리케이션 팀에 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-155">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="28d74-156">애플리케이션 팀은 유일한 변경 내용이 기준이 되는 프로덕션 환경에 대해 릴리스를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-156">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="28d74-157">그러나 이렇게 하면 서비스 중단 위험 전에 애플리케이션에 대한 영향을 평가할 기회가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-157">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

<span data-ttu-id="28d74-158">참고 - 복합 리소스 사용에 대한 피드백에는 변경하려면 새 MOF의 컴파일 및 릴리스가 필요하다는 비판이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-158">Note - Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span>
<span data-ttu-id="28d74-159">이것은 의도적입니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-159">This is by design.</span></span>
<span data-ttu-id="28d74-160">각 새 구성 릴리스는 각 리소스의 특정 버전에 대한 정적 참조를 포함해야 하며, 프로덕션 서버 노드에 연결되기 전에 테스트를 통해 유효성이 검사되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-160">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span>
<span data-ttu-id="28d74-161">소스 제어에서 변경 내용을 테스트하고 릴리스하는 프로세스를 통해 소규모지만 잦은 일괄 처리로 변경을 릴리스하기 위한 안전한 환경이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="28d74-161">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="28d74-162">핵심 인프라를 관리하기 위해 릴리스 파이프라인을 사용하는 방법에 대한 자세한 내용은 [릴리스 파이프라인 모델](../further-reading/whitepapers.md) 백서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="28d74-162">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](../further-reading/whitepapers.md).</span></span>
