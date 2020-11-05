---
ms.date: 06/12/2017
description: 이 문서는 DSC 끌어오기 서버를 배포하는 엔지니어를 지원할 모범 사례를 제공합니다.
keywords: dsc,powershell,configuration,setup
title: 끌어오기 서버 모범 사례
ms.openlocfilehash: 0021baa219a0936405eccf2cc7741e042f8bf09f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664324"
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="42005-104">끌어오기 서버 모범 사례</span><span class="sxs-lookup"><span data-stu-id="42005-104">Pull server best practices</span></span>

<span data-ttu-id="42005-105">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="42005-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="42005-106">끌어오기 서버(Windows 기능 *DSC-Service* )는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-106">The Pull Server (Windows Feature *DSC-Service* ) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="42005-107">관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-107">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="42005-108">요약: 이 문서는 솔루션을 준비하고 있는 엔지니어를 지원할 프로세스 및 확장성을 포함하기 위해 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-108">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="42005-109">세부 내용에서는 고객이 식별하고 제품 팀이 검증을 통해 미래에 대비하고 안정적이라고 간주되는 권장 사항으로 확인한 모범 사례를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-109">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

- <span data-ttu-id="42005-110">작성자: Michael Greene</span><span class="sxs-lookup"><span data-stu-id="42005-110">Author: Michael Greene</span></span>
- <span data-ttu-id="42005-111">검토자: Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="42005-111">Reviewers: Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>
- <span data-ttu-id="42005-112">게시 날짜: 2015년 4월</span><span class="sxs-lookup"><span data-stu-id="42005-112">Published: April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="42005-113">요약</span><span class="sxs-lookup"><span data-stu-id="42005-113">Abstract</span></span>

<span data-ttu-id="42005-114">이 문서는 Windows PowerShell 필요한 상태 구성 끌어오기 서버 구현을 준비 중인 사용자에게 공식 지침을 제공하기 위해 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-114">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="42005-115">끌어오기 서버는 몇 분만에 배포할 수 있는 간단한 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="42005-115">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="42005-116">이 문서는 배포 시 사용할 수 있는 기술적인 방법 지침도 제공하지만, 모범 사례와 배포 전 고려할 사항을 참조할 수 있다는 점에서 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-116">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span> <span data-ttu-id="42005-117">이 문서를 읽으려면 DSC에 대한 기본 사항과 DSC 배포에 포함되는 구성 요소를 설명하는 용어를 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-117">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="42005-118">자세한 내용은 [Windows PowerShell 필요한 상태 구성 개요](/powershell/scripting/dsc/overview/overview) 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42005-118">For more information, see the [Windows PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/overview) topic.</span></span> <span data-ttu-id="42005-119">DSC는 클라우드 주기에 따라 개선될 것이므로 끌어오기 서버를 비롯한 기본 기술도 발전하고 새로운 기능을 도입할 것으로 예상됩니다.</span><span class="sxs-lookup"><span data-stu-id="42005-119">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="42005-120">이 문서의 부록에 포함된 버전 테이블에서는 이전 릴리스에 대한 참조와 진취적인 디자인을 권장하기 위한 미래에 대비한 솔루션에 대한 참조를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-120">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="42005-121">이 문서의 두 가지 주요 섹션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-121">The two major sections of this document:</span></span>

- <span data-ttu-id="42005-122">구성 계획</span><span class="sxs-lookup"><span data-stu-id="42005-122">Configuration Planning</span></span>
- <span data-ttu-id="42005-123">설치 가이드</span><span class="sxs-lookup"><span data-stu-id="42005-123">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="42005-124">Windows Management Framework의 버전</span><span class="sxs-lookup"><span data-stu-id="42005-124">Versions of the Windows Management Framework</span></span>

<span data-ttu-id="42005-125">이 문서의 정보는 Windows Management Framework 5.0에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="42005-125">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="42005-126">끌어오기 서버를 배포 및 운영하는 데 WMF 5.0이 필요하지는 않지만 이 문서에서는 버전 5.0을 주로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-126">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="42005-127">Windows PowerShell 필요한 상태 구성</span><span class="sxs-lookup"><span data-stu-id="42005-127">Windows PowerShell Desired State Configuration</span></span>

<span data-ttu-id="42005-128">DSC(필요한 상태 구성)는 CIM(Common Information Model)을 설명하는 MOF(Managed Object Format)라는 산업 구문을 사용하여 구성 데이터를 배포 및 관리할 수 있는 관리 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="42005-128">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="42005-129">오픈 소스 프로젝트인 OMI(Open Management Infrastructure)는 Linux 및 네트워크 하드웨어 운영 체제를 비롯한 다양한 플랫폼에서 이러한 표준을 성공적으로 개발하기 위해 마련되었습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-129">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="42005-130">자세한 내용은 [DMTF page linking to MOF specifications](https://www.dmtf.org/standards/cim)(MOF 사양에 연결되는 DMTF 페이지) 및 [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php)(OMI 문서 및 원본)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42005-130">For more information, see the [DMTF page linking to MOF specifications](https://www.dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="42005-131">Windows PowerShell에서는 선언적 구성을 만들고 관리하는 데 사용할 수 있는 필요한 상태 구성의 언어 확장 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-131">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="42005-132">끌어오기 서버 역할</span><span class="sxs-lookup"><span data-stu-id="42005-132">Pull server role</span></span>

<span data-ttu-id="42005-133">끌어오기 서버는 구성을 저장하여 대상 노드에서 액세스할 수 있게 하는 중앙 집중식 서비스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-133">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="42005-134">끌어오기 서버 역할은 웹 서버 인스턴스나 SMB 파일 공유로 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-134">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="42005-135">웹 서버 기능에는 OData 인터페이스가 포함되며 필요에 따라 구성이 적용될 때 대상 노드가 성공 또는 실패에 대한 확인을 다시 보고하는 기능도 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-135">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="42005-136">이 기능은 많은 수의 대상 노드가 있는 환경에서 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-136">This functionality is useful in environments where there are a large number of target nodes.</span></span> <span data-ttu-id="42005-137">대상 노드(클라이언트라고도 함)가 끌어오기 서버를 가리키도록 구성한 후 최신 구성 데이터 및 모든 필수 스크립트가 다운로드되어 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="42005-137">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="42005-138">이 작업은 일회성 배포 또는 되풀이 작업으로 수행될 수 있으므로 끌어오기 서버가 대규모 변경을 관리하기 위한 중요한 자산도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42005-138">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="42005-139">자세한 내용은 [Windows PowerShell 필요한 상태 구성 끌어오기 서버](pullserver.md) 및 [밀어넣기 및 끌어오기 구성 모드](pullserver.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42005-139">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](pullserver.md) and [Push and Pull Configuration Modes](pullserver.md).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="42005-140">구성 계획</span><span class="sxs-lookup"><span data-stu-id="42005-140">Configuration planning</span></span>

<span data-ttu-id="42005-141">엔터프라이즈 소프트웨어 배포의 경우 올바른 아키텍처를 계획하고 배포를 완료하는 데 필요한 단계를 준비하기 위해 미리 수집할 수 있는 정보가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-141">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="42005-142">다음 섹션에서는 준비하는 방법 및 미리 수행해야 할 수 있는 조직 연결과 관련된 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-142">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="42005-143">소프트웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="42005-143">Software requirements</span></span>

<span data-ttu-id="42005-144">끌어오기 서버를 배포하려면 Windows Server의 DSC 서비스 기능이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-144">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="42005-145">이 기능은 Windows Server 2012에서 도입되었으며 WMF(Windows Management Framework)의 지속적인 릴리스를 통해 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-145">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="42005-146">소프트웨어 다운로드</span><span class="sxs-lookup"><span data-stu-id="42005-146">Software downloads</span></span>

<span data-ttu-id="42005-147">DSC 끌어오기 서버를 배포하려면 Windows 업데이트에서 최신 콘텐츠를 설치하고 최신 버전의 Windows Management Framework와 끌어오기 서버 프로비전을 자동화하는 DSC 모듈을 다운로드하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-147">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="42005-148">WMF</span><span class="sxs-lookup"><span data-stu-id="42005-148">WMF</span></span>

<span data-ttu-id="42005-149">Windows Server 2012 R2에는 DSC 서비스라는 기능이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-149">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="42005-150">DSC 서비스 기능은 OData 엔드포인트를 지원하는 이진 파일을 비롯한 끌어오기 서버 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-150">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span> <span data-ttu-id="42005-151">WMF는 Windows Server에 포함되어 있으며 Windows Server 릴리스 사이에 빠른 주기로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="42005-151">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span>
<span data-ttu-id="42005-152">[WMF 5.0의 새 버전](https://www.microsoft.com/download/details.aspx?id=54616)에는 DSC 서비스 기능에 대한 업데이트가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-152">[New versions of WMF 5.0](https://www.microsoft.com/download/details.aspx?id=54616) can include updates to the DSC Service feature.</span></span> <span data-ttu-id="42005-153">따라서 WMF의 최신 릴리스를 다운로드하고 릴리스 정보를 검토하여 해당 릴리스에 DSC 서비스 기능에 대한 업데이트가 포함되어 있는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-153">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="42005-154">업데이트 또는 시나리오의 디자인 상태가 안정적 또는 실험적으로 나열되는지를 나타내는 릴리스 정보 섹션도 검토해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-154">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span> <span data-ttu-id="42005-155">빠른 릴리스 주기를 달성하기 위해 WMF가 미리 보기로 릴리스된 동안에도 기능을 프로덕션 환경에서 사용할 수 있도록 개별 기능을 안정적이라고 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-155">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span> <span data-ttu-id="42005-156">지금까지 WMF 릴리스에서 업데이트된 다른 기능은 다음과 같습니다(자세한 내용은 WMF 릴리스 정보 참조).</span><span class="sxs-lookup"><span data-stu-id="42005-156">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

- <span data-ttu-id="42005-157">Windows PowerShell, Windows PowerShell ISE(통합 스크립팅</span><span class="sxs-lookup"><span data-stu-id="42005-157">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
- <span data-ttu-id="42005-158">환경), Windows PowerShell 웹 서비스(관리 OData</span><span class="sxs-lookup"><span data-stu-id="42005-158">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
- <span data-ttu-id="42005-159">IIS 확장), Windows PowerShell DSC(필요한 상태 구성)</span><span class="sxs-lookup"><span data-stu-id="42005-159">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="42005-160">WinRM(Windows 원격 관리), WMI(Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="42005-160">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="42005-161">DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="42005-161">DSC resource</span></span>

<span data-ttu-id="42005-162">DSC 구성 스크립트를 사용하여 서비스를 프로비전하면 끌어오기 서버 배포를 간소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-162">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="42005-163">이 문서에는 프로덕션 준비가 된 서버 노드를 배포하는 데 사용할 수 있는 구성 스크립트가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-163">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="42005-164">구성 스크립트를 사용하려면 Windows Server에 포함되지 않은 DSC 모듈이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-164">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="42005-165">필요한 모듈 이름은 DSC 리소스 **xDscWebService** 를 포함하는 **xPSDesiredStateConfiguration** 입니다.</span><span class="sxs-lookup"><span data-stu-id="42005-165">The required module name is **xPSDesiredStateConfiguration** , which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="42005-166">XPSDesiredStateConfiguration 모듈은 [여기](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d)에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-166">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="42005-167">**PowerShellGet** 모듈에서 `Install-Module` cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-167">Use the `Install-Module` cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="42005-168">**PowerShellGet** 모듈은 모듈을 다음 위치로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-168">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="42005-169">계획 작업</span><span class="sxs-lookup"><span data-stu-id="42005-169">Planning task</span></span>

- <span data-ttu-id="42005-170">Windows Server 2012 R2용 설치 파일에 액세스할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="42005-170">Do you have access to the installation files for Windows Server 2012 R2?</span></span>
- <span data-ttu-id="42005-171">배포 환경에서 인터넷에 액세스하여 온라인 갤러리에서 WMF 및 모듈을 다운로드할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="42005-171">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>
- <span data-ttu-id="42005-172">운영 체제를 설치한 후 최신 보안 업데이트를 어떻게 설치하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-172">How will you install the latest security updates after installing the operating system?</span></span>
- <span data-ttu-id="42005-173">환경에서 인터넷에 액세스하여 업데이트를 다운로드할 수 있거나 로컬 WSUS(Windows Server Update Services) 서버가 있나요?</span><span class="sxs-lookup"><span data-stu-id="42005-173">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>
- <span data-ttu-id="42005-174">오프라인 추가를 통해 업데이트를 이미 포함하는 Windows Server 설치 파일에 액세스할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="42005-174">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>

### <a name="hardware-requirements"></a><span data-ttu-id="42005-175">하드웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="42005-175">Hardware requirements</span></span>

<span data-ttu-id="42005-176">끌어오기 서버 배포는 물리적 서버와 가상 서버 모두에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="42005-176">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="42005-177">끌어오기 서버의 크기 요구 사항은 Windows Server 2012 R2의 요구 사항과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-177">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

- <span data-ttu-id="42005-178">CPU: 1.4GHz 64비트 프로세서</span><span class="sxs-lookup"><span data-stu-id="42005-178">CPU: 1.4 GHz 64-bit processor</span></span>
- <span data-ttu-id="42005-179">메모리: 512MB</span><span class="sxs-lookup"><span data-stu-id="42005-179">Memory: 512 MB</span></span>
- <span data-ttu-id="42005-180">디스크 공간: 32GB</span><span class="sxs-lookup"><span data-stu-id="42005-180">Disk Space: 32 GB</span></span>
- <span data-ttu-id="42005-181">네트워크: 기가비트 이더넷 어댑터</span><span class="sxs-lookup"><span data-stu-id="42005-181">Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="42005-182">계획 작업</span><span class="sxs-lookup"><span data-stu-id="42005-182">Planning task</span></span>

- <span data-ttu-id="42005-183">물리적 하드웨어에 배포하나요? 가상화 플랫폼에 배포하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-183">Will you deploy on physical hardware or on a virtualization platform?</span></span>
- <span data-ttu-id="42005-184">대상 환경에 대한 새 서버를 요청하는 절차는 어떻게 되나요?</span><span class="sxs-lookup"><span data-stu-id="42005-184">What is the process to request a new server for your target environment?</span></span>
- <span data-ttu-id="42005-185">서버를 사용할 수 있을 때까지 걸리는 평균 소요 시간은 어떻게 되나요?</span><span class="sxs-lookup"><span data-stu-id="42005-185">What is the average turnaround time for a server to become available?</span></span>
- <span data-ttu-id="42005-186">필요한 서버의 크기는 어떻게 되나요?</span><span class="sxs-lookup"><span data-stu-id="42005-186">What size server will you request?</span></span>

### <a name="accounts"></a><span data-ttu-id="42005-187">계정</span><span class="sxs-lookup"><span data-stu-id="42005-187">Accounts</span></span>

<span data-ttu-id="42005-188">끌어오기 서버 인스턴스를 배포하는 데 필요한 서비스 계정 요구 사항은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-188">There are no service account requirements to deploy a pull server instance.</span></span> <span data-ttu-id="42005-189">그러나 로컬 사용자 계정의 컨텍스트에서 웹 사이트를 실행할 수 있는 시나리오가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-189">However, there are scenarios where the website could run in the context of a local user account.</span></span> <span data-ttu-id="42005-190">웹 사이트 콘텐츠를 위해 스토리지 공유에 액세스해야 하고 Windows Server 또는 스토리지 공유를 호스트하는 디바이스가 도메인에 연결되지 않은 경우를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-190">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="42005-191">DNS 레코드</span><span class="sxs-lookup"><span data-stu-id="42005-191">DNS records</span></span>

<span data-ttu-id="42005-192">끌어오기 서버 환경에서 작동하는 클라이언트를 구성할 때 사용할 서버 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-192">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="42005-193">테스트 환경에서는 일반적으로 서버 호스트 이름이 사용되거나 DNS 이름 확인을 사용할 수 없는 경우 서버의 IP 주소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-193">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span> <span data-ttu-id="42005-194">프로덕션 환경 또는 프로덕션 배포를 나타내기 위해 설계된 랩 환경에서는 DNS CNAME 레코드를 만드는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-194">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="42005-195">DNS CNAME을 사용하면 호스트(A) 레코드를 참조하는 별칭을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-195">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span> <span data-ttu-id="42005-196">추가 이름 레코드는 나중에 변경이 필요한 경우 유연성을 높이기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="42005-196">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span> <span data-ttu-id="42005-197">CNAME은 클라이언트 구성을 격리할 수 있으므로 끌어오기 서버를 교체하거나 끌어오기 서버를 추가하는 등 서버 환경을 변경할 때 해당하는 클라이언트 구성을 변경할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-197">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="42005-198">DNS 레코드의 이름을 선택할 때는 항상 솔루션 아키텍처를 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="42005-198">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span> <span data-ttu-id="42005-199">부하 분산을 사용하는 경우 HTTPS를 통한 트래픽을 보호하는 데 사용되는 인증서가 DNS 레코드와 동일한 이름을 공유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-199">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

|       <span data-ttu-id="42005-200">시나리오</span><span class="sxs-lookup"><span data-stu-id="42005-200">Scenario</span></span>        |                                                                                         <span data-ttu-id="42005-201">모범 사례</span><span class="sxs-lookup"><span data-stu-id="42005-201">Best Practice</span></span>
|:--------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
|<span data-ttu-id="42005-202">테스트 환경</span><span class="sxs-lookup"><span data-stu-id="42005-202">Test Environment</span></span>       | <span data-ttu-id="42005-203">가능하면 계획된 프로덕션 환경을 재현합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-203">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="42005-204">간단한 구성에는 서버 호스트 이름이 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-204">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="42005-205">DNS를 사용할 수 없는 경우 호스트 이름 대신 IP 주소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-205">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>
|<span data-ttu-id="42005-206">단일 노드 배포</span><span class="sxs-lookup"><span data-stu-id="42005-206">Single Node Deployment</span></span> | <span data-ttu-id="42005-207">서버 호스트 이름을 가리키는 DNS CNAME 레코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="42005-207">Create a DNS CNAME record that points to the server hostname.</span></span>

<span data-ttu-id="42005-208">자세한 내용은 [Windows Server에서 DNS 라운드 로빈 구성](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10))을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42005-208">For more information, see [Configuring DNS Round Robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span></span>

<span data-ttu-id="42005-209">계획 작업</span><span class="sxs-lookup"><span data-stu-id="42005-209">Planning task</span></span>

- <span data-ttu-id="42005-210">DNS 레코드를 만들고 변경하기 위해 누구에게 연결해야 하는지 아나요?</span><span class="sxs-lookup"><span data-stu-id="42005-210">Do you know who to contact to have DNS records created and changed?</span></span>
- <span data-ttu-id="42005-211">DNS 레코드 요청의 평균 소요 시간은 얼마나 되나요?</span><span class="sxs-lookup"><span data-stu-id="42005-211">What is the average turnaround for a request for a DNS record?</span></span>
- <span data-ttu-id="42005-212">서버의 정적 호스트 이름(A) 레코드를 요청해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-212">Do you need to request static Hostname (A) records for servers?</span></span>
- <span data-ttu-id="42005-213">CNAME으로 무엇을 요청하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-213">What will you request as a CNAME?</span></span>
- <span data-ttu-id="42005-214">필요한 경우 어떤 유형의 부하 분산 솔루션은 활용하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-214">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="42005-215">(자세한 내용은 부하 분산이라는 섹션 참조)</span><span class="sxs-lookup"><span data-stu-id="42005-215">(see section titled Load Balancing for details)</span></span>

### <a name="public-key-infrastructure"></a><span data-ttu-id="42005-216">공개 키 인프라</span><span class="sxs-lookup"><span data-stu-id="42005-216">Public Key Infrastructure</span></span>

<span data-ttu-id="42005-217">오늘날의 대부분의 조직에서는 네트워크 트래픽 특히, 서버 구성 방법과 같은 중요한 데이터를 포함하는 트래픽을 전송 중 유효성을 검사하거나 암호화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-217">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="42005-218">일반 텍스트의 클라이언트 요청을 지원하는 HTTP를 사용하여 끌어오기 서버를 배포할 수도 있지만 HTTPS를 사용하여 트래픽 보안을 유지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-218">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="42005-219">DSC 리소스 **xPSDesiredStateConfiguration** 에 있는 매개 변수 집합을 사용하여 HTTPS를 사용하도록 서비스를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-219">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="42005-220">끌어오기 서버의 HTTPS 트래픽 보안을 설정하는 데 필요한 인증서 요구 사항은 다른 HTTPS 웹 사이트 보안 설정과 다르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-220">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="42005-221">Windows Server 인증서 서비스의 **웹 서버** 템플릿은 필요한 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-221">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="42005-222">계획 작업</span><span class="sxs-lookup"><span data-stu-id="42005-222">Planning task</span></span>

- <span data-ttu-id="42005-223">인증서 요청이 자동화되지 않은 경우 인증서를 요청하기 위해 누구에게 연락해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-223">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>
- <span data-ttu-id="42005-224">요청의 평균 소요 시간은 얼마나 되나요?</span><span class="sxs-lookup"><span data-stu-id="42005-224">What is the average turnaround for the request?</span></span>
- <span data-ttu-id="42005-225">인증서 파일을 어떻게 전송받나요?</span><span class="sxs-lookup"><span data-stu-id="42005-225">How will the certificate file be transferred to you?</span></span>
- <span data-ttu-id="42005-226">인증서 프라이빗 키를 어떻게 전송받나요?</span><span class="sxs-lookup"><span data-stu-id="42005-226">How will the certificate private key be transferred to you?</span></span>
- <span data-ttu-id="42005-227">기본 만료 시간은 얼마나 되나요?</span><span class="sxs-lookup"><span data-stu-id="42005-227">How long is the default expiration time?</span></span>
- <span data-ttu-id="42005-228">끌어오기 서버 환경의 DNS 이름을 정한 경우 이 이름을 인증서 이름에 사용할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="42005-228">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>

### <a name="choosing-an-architecture"></a><span data-ttu-id="42005-229">아키텍처 선택</span><span class="sxs-lookup"><span data-stu-id="42005-229">Choosing an architecture</span></span>

<span data-ttu-id="42005-230">IIS 또는 SMB 파일 공유에 호스트된 웹 서비스를 사용하여 끌어오기 서버를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-230">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="42005-231">대부분의 경우 웹 서비스 옵션을 사용하면 유연성이 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="42005-231">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="42005-232">HTTPS 트래픽이 네트워크 경계를 트래버스하는 경우는 드물지 않지만, SMB 트래픽은 네트워크 간에 차단되거나 필터링되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-232">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="42005-233">또한 웹 서비스에서는 중앙에서 가시성 향상을 위해 클라이언트가 상태를 서버에 다시 보고하는 메커니즘을 제공하는 준수 서버 또는 웹 보고 관리자(두 항목 모두 이 설명서의 이후 버전에서 다룸)를 포함하는 오션도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-233">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span> <span data-ttu-id="42005-234">SMB는 정책에서 웹 서버를 사용하면 안 되도록 지정하는 환경 및 웹 서버 역할을 필요하지 않게 하는 다른 환경 요구 사항에 대한 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-234">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span> <span data-ttu-id="42005-235">두 경우 모두 트래픽 서명 및 암호화에 필요한 요구 사항을 평가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-235">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="42005-236">HTTPS, SMB 서명 및 IPSEC 정책 모두 고려할 만한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="42005-236">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="42005-237">부하 분산</span><span class="sxs-lookup"><span data-stu-id="42005-237">Load balancing</span></span>

<span data-ttu-id="42005-238">웹 서비스와 상호 작용하는 클라이언트는 단일 응답으로 반환되는 정보를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-238">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="42005-239">순차 요청이 필요하지 않으므로 부하 분산 플랫폼이 임의의 시점에 세션이 단일 서버에서 유지 관리되는지 확인할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-239">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="42005-240">계획 작업</span><span class="sxs-lookup"><span data-stu-id="42005-240">Planning task</span></span>

- <span data-ttu-id="42005-241">트래픽 부하를 서버 간에 분산하기 위해 어떤 솔루션을 사용하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-241">What solution will be used for load balancing traffic across servers?</span></span>
- <span data-ttu-id="42005-242">하드웨어 부하 분산 디바이스를 사용할 경우 디바이스에 새 구성을 추가하도록 누가 요청하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-242">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>
- <span data-ttu-id="42005-243">부하 분산된 새 웹 서비스를 구성하는 요청의 평균 소요 시간은 얼마나 되나요?</span><span class="sxs-lookup"><span data-stu-id="42005-243">What is the average turnaround for a request to configure a new load balanced web service?</span></span>
- <span data-ttu-id="42005-244">요청에 어떤 정보가 필요하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-244">What information will be required for the request?</span></span>
- <span data-ttu-id="42005-245">추가 IP를 요청해야 하나요? 아니면 부하 분산을 담당하는 팀이 이를 처리하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-245">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>
- <span data-ttu-id="42005-246">필요한 DNS 레코드가 있고 부하 분산 솔루션을 구성하는 팀에 이 레코드가 필요하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-246">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>
- <span data-ttu-id="42005-247">부하 분산 솔루션을 사용하려면 PKI를 디바이스에서 처리해야 하나요? 또는 세션 요구 사항이 없는 경우 부하 분산 솔루션에서 HTTPS 트래픽 부하를 분산할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="42005-247">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="42005-248">끌어오기 서버에서 구성 및 모듈 준비</span><span class="sxs-lookup"><span data-stu-id="42005-248">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="42005-249">구성 계획의 일환으로 끌어오기 서버에서 호스트할 DSC에 모듈 및 구성을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-249">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="42005-250">구성 계획을 위해 콘텐츠를 준비하고 끌어오기 서버에 배포하는 방법에 대한 기본 사항을 이해하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-250">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="42005-251">향후 이 섹션이 확장되어 DSC 끌어오기 서버 운영 가이드에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="42005-251">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span> <span data-ttu-id="42005-252">이 가이드에서는 자동화를 사용하여 시간에 따라 모듈 및 구성을 관리하는 일일 프로세스를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-252">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="42005-253">DSC 모듈</span><span class="sxs-lookup"><span data-stu-id="42005-253">DSC modules</span></span>

<span data-ttu-id="42005-254">구성을 요청하는 클라이언트는 필수 DSC 모듈이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-254">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="42005-255">끌어오기 서버는 클라이언트로의 DSC 모듈 주문형 배포를 자동화합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-255">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="42005-256">끌어오기 서버를 처음으로 랩 또는 개념 증명으로 배포하는 경우에는 PowerShell 갤러리와 같은 공용 리포지토리 또는 DSC 모듈용 PowerShell.org GitHub 리포지토리에서 제공되는 DSC 모듈을 사용할 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-256">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="42005-257">PowerShell 갤러리와 같은 신뢰할 수 있는 온라인 원본인 경우에도 공용 리포지토리에서 다운로드하는 모든 모듈은 프로덕션에서 사용하기 전에 모듈을 사용할 환경에 대한 PowerShell 경험 및 지식이 있는 사용자가 검토해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-257">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="42005-258">이 작업을 수행하는 동안 모듈에서 제거할 수 있는 설명서 및 예제 스크립트와 같은 추가 페이로드가 있는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-258">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="42005-259">이렇게 하면 모듈을 네트워크를 통해 서버에서 클라이언트로 다운로드하는 첫 번째 요청에서 클라이언트당 네트워크 대역폭이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="42005-259">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="42005-260">각 모듈은 모듈 페이로드를 포함하는 ModuleName_Version.zip이라는 특정 형식의 ZIP 파일로 패키지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-260">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="42005-261">파일을 서버에 복사한 후 체크섬 파일을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-261">After the file is copied to the server a checksum file must be created.</span></span>
<span data-ttu-id="42005-262">클라이언트가 서버에 연결할 때 이 체크섬을 사용하여 DSC 모듈의 콘텐츠가 게시된 후 변경되지 않았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-262">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="42005-263">계획 작업</span><span class="sxs-lookup"><span data-stu-id="42005-263">Planning task</span></span>

- <span data-ttu-id="42005-264">테스트 또는 랩 환경을 계획하는 경우 유효성을 검사하기 위해 어떤 시나리오가 중요할까요?</span><span class="sxs-lookup"><span data-stu-id="42005-264">If you are planning a test or lab environment which scenarios are key to validate?</span></span>
- <span data-ttu-id="42005-265">필요한 모든 사항을 처리할 리소스를 포함하는 공개된 모듈이 있나요? 아니면 리소스를 직접 만들어야 하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-265">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>
- <span data-ttu-id="42005-266">인터넷에 액세스하여 공용 모듈을 검색할 수 있는 환경인가요?</span><span class="sxs-lookup"><span data-stu-id="42005-266">Will your environment have Internet access to retrieve public modules?</span></span>
- <span data-ttu-id="42005-267">누가 DSC 모듈을 검토하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-267">Who will be responsible for reviewing DSC modules?</span></span>
- <span data-ttu-id="42005-268">프로덕션 환경을 계획하는 경우 DSC 모듈을 저장하기 위한 로컬 리포지토리로 무엇을 사용할 예정인가요?</span><span class="sxs-lookup"><span data-stu-id="42005-268">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>
- <span data-ttu-id="42005-269">중앙 팀이 애플리케이션 팀의 DSC 모듈을 수락할 계획인가요?</span><span class="sxs-lookup"><span data-stu-id="42005-269">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="42005-270">절차는 어떻게 되나요?</span><span class="sxs-lookup"><span data-stu-id="42005-270">What will the process be?</span></span>
- <span data-ttu-id="42005-271">원본 리포지토리에서 서버로 프로덕션이 준비된 DSC 모듈의 패키징, 복사 및 체크섬 만들기를 자동화할 계획인가요?</span><span class="sxs-lookup"><span data-stu-id="42005-271">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>
- <span data-ttu-id="42005-272">귀하의 팀이 자동화 플랫폼을 관리할 계획인가요?</span><span class="sxs-lookup"><span data-stu-id="42005-272">Will your team be responsible for managing the automation platform as well?</span></span>

#### <a name="dsc-configurations"></a><span data-ttu-id="42005-273">DSC 구성</span><span class="sxs-lookup"><span data-stu-id="42005-273">DSC configurations</span></span>

<span data-ttu-id="42005-274">끌어오기 서버의 용도는 DSC 구성을 클라이언트 노드에 배포하기 위한 중앙 집중식 메커니즘을 제공하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="42005-274">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="42005-275">구성은 서버에 MOF 문서로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="42005-275">The configurations are stored on the server as MOF documents.</span></span> <span data-ttu-id="42005-276">각 문서의 이름은 고유한 **GUID** 를 사용하여 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="42005-276">Each document will be named with a unique **Guid**.</span></span> <span data-ttu-id="42005-277">클라이언트가 끌어오기 서버와 연결하도록 구성된 경우 요청해야 하는 구성의 **GUID** 도 제공받습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-277">When clients are configured to connect with a pull server, they are also given the **Guid** for the configuration they should request.</span></span> <span data-ttu-id="42005-278">**GUID** 로 구성을 참조하는 이 시스템은 글로벌 고유성을 보장하며 구성을 노드별로 세부적으로 적용하거나 구성이 동일한 여러 서버에 걸친 역할 구성으로 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-278">This system of referencing configurations by **Guid** guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="42005-279">GUID</span><span class="sxs-lookup"><span data-stu-id="42005-279">Guids</span></span>

<span data-ttu-id="42005-280">끌어오기 서버 배포를 고려할 때 구성 **GUID** 계획에 더욱 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-280">Planning for configuration **Guids** is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="42005-281">**GUID** 처리 방법에 대한 특별한 요구 사항은 없으며 환경마다 프로세스가 고유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-281">There is no specific requirement for how to handle **Guids** and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="42005-282">중앙에 저장된 CSV 파일, 단순한 SQL 테이블, CMDB, 다른 도구 또는 소프트웨어 솔루션과 통합해야 하는 복잡한 솔루션 등 프로세스가 단순하거나 복잡할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-282">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="42005-283">두 가지 일반적인 접근 방식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-283">There are two general approaches:</span></span>

- <span data-ttu-id="42005-284">**서버당 GUID 할당** - 모든 서버 구성을 개별적으로 확실히 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-284">**Assigning Guids per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="42005-285">서버 수가 적은 환경에서 효과적인 이 접근 방식을 채택하면 정확하게 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-285">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
- <span data-ttu-id="42005-286">**서버 역할당 GUID 할당** - 웹 서버와 같이 동일한 기능을 수행하는 모든 서버가 동일한 GUID를 사용하여 필요한 구성 데이터를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-286">**Assigning Guids per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span> <span data-ttu-id="42005-287">여러 서버가 동일한 GUID를 공유하는 경우 구성이 변경되면 이들 서버가 모두 동시에 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="42005-287">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

  <span data-ttu-id="42005-288">GUID는 악의적인 의도를 가진 사람에 의해 환경의 서버 배포 및 구성 방법에 대한 정보를 얻는 데 활용될 수 있으므로 중요한 데이터로 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-288">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="42005-289">자세한 내용은 [PowerShell 필요한 상태 구성 끌어오기 모드에서 GUID 안전하게 할당](https://devblogs.microsoft.com/powershell/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42005-289">For more information, see [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://devblogs.microsoft.com/powershell/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span></span>

<span data-ttu-id="42005-290">계획 작업</span><span class="sxs-lookup"><span data-stu-id="42005-290">Planning task</span></span>

- <span data-ttu-id="42005-291">구성이 준비되면 누가 끌어오기 서버 폴더로 복사하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-291">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>
- <span data-ttu-id="42005-292">구성을 애플리케이션 팀에서 작성하는 경우 구성을 전달하는 프로세스는 어떻게 되나요?</span><span class="sxs-lookup"><span data-stu-id="42005-292">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>
- <span data-ttu-id="42005-293">구성이 여러 팀에서 작성되면 리포지토리를 사용하여 저장하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-293">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>
- <span data-ttu-id="42005-294">구성을 서버에 복사하고 구성이 준비되면 체크섬을 만드는 프로세스를 자동화하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-294">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>
- <span data-ttu-id="42005-295">GUID를 서버 또는 역할에 매핑하는 방법은 무엇이고 GUID를 어디에 저장하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-295">How will you map Guids to servers or roles, and where will this be stored?</span></span>
- <span data-ttu-id="42005-296">클라이언트 머신을 구성하는 프로세스로 무엇을 사용하며, 구성 GUID를 만들고 저장하는 프로세스와 어떻게 통합하나요?</span><span class="sxs-lookup"><span data-stu-id="42005-296">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration Guids?</span></span>

## <a name="installation-guide"></a><span data-ttu-id="42005-297">설치 가이드</span><span class="sxs-lookup"><span data-stu-id="42005-297">Installation Guide</span></span>

<span data-ttu-id="42005-298">*이 문서에 제공된 스크립트는 안정적인 예제입니다. 스크립트를 프로덕션 환경에서 실행하기 전에 항상 신중히 검토하세요.*</span><span class="sxs-lookup"><span data-stu-id="42005-298">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="42005-299">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="42005-299">Prerequisites</span></span>

<span data-ttu-id="42005-300">서버에서 PowerShell 버전을 확인하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-300">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="42005-301">가능하면 최신 버전의 Windows Management Framework로 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-301">If possible, upgrade to the latest version of Windows Management Framework.</span></span> <span data-ttu-id="42005-302">그리고 다음 명령을 사용하여 `xPsDesiredStateConfiguration` 모듈을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-302">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="42005-303">이 명령은 모듈을 다운로드하기 전에 사용자의 승인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-303">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="42005-304">설치 및 구성 스크립트</span><span class="sxs-lookup"><span data-stu-id="42005-304">Installation and configuration scripts</span></span>

<span data-ttu-id="42005-305">DSC 끌어오기 서버를 배포하는 최상의 방법은 DSC 구성 스크립트를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="42005-305">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="42005-306">이 문서에서는 DSC 웹 서비스만 구성하는 기본 설정과 DSC 웹 서비스를 포함하는 엔드투엔드 Windows Server를 구성하는 고급 설정이 모두 포함된 스크립트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-306">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="42005-307">참고: 현재 `xPSDesiredStateConfiguration` DSC 모듈을 사용하려면 EN-US 로캘의 서버가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-307">Note: Currently the `xPSDesiredStateConfiguration` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="42005-308">Windows Server 2012에 대한 기본 구성</span><span class="sxs-lookup"><span data-stu-id="42005-308">Basic configuration for Windows Server 2012</span></span>

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="42005-309">Windows Server 2012 R2에 대한 고급 구성</span><span class="sxs-lookup"><span data-stu-id="42005-309">Advanced configuration for Windows Server 2012 R2</span></span>

```powershell
# This is an advanced Configuration example for Pull Server production deployments
# on Windows Server 2012 R2. Many of the features demonstrated are optional and
# provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority,
        # complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider
        # modifying the default port, possibly leveraging port 443 in environments where that is
        # enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a><span data-ttu-id="42005-310">끌어오기 서버 기능 확인</span><span class="sxs-lookup"><span data-stu-id="42005-310">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the
# default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="42005-311">클라이언트 구성</span><span class="sxs-lookup"><span data-stu-id="42005-311">Configure clients</span></span>

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="42005-312">추가 참조, 코드 조각 및 예제</span><span class="sxs-lookup"><span data-stu-id="42005-312">Additional references, snippets, and examples</span></span>

<span data-ttu-id="42005-313">이 예제에서는 테스트를 위해 클라이언트 연결을 수동으로 시작하는 방법(WMF5 필요)을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="42005-313">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DscConfiguration –Wait -Verbose
```

<span data-ttu-id="42005-314">[Add-DnsServerResourceRecordName](/powershell/module/dnsserver/add-dnsserverresourcerecordcname) cmdlet은 CNAME 형식 레코드를 DNS 영역에 추가하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="42005-314">The [Add-DnsServerResourceRecordName](/powershell/module/dnsserver/add-dnsserverresourcerecordcname) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="42005-315">[체크섬을 만들고 DSC MOF를 SMB 끌어오기 서버에 게시](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0)하는 PowerShell 함수는 필요한 체크섬을 자동으로 생성한 다음 MOF 구성과 체크섬 파일을 SMB 끌어오기 서버에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="42005-315">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="42005-316">부록 - ODATA 서비스 데이터 파일 형식 이해</span><span class="sxs-lookup"><span data-stu-id="42005-316">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="42005-317">OData 웹 서비스를 포함하는 끌어오기 서버 배포 중 정보를 만들기 위해 데이터 파일이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="42005-317">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="42005-318">파일 형식은 아래 설명된 대로 운영 체제에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="42005-318">The type of file depends on the operating system, as described below.</span></span>

- <span data-ttu-id="42005-319">**Windows Server 2012** - 파일 형식은 항상 `.mdb`입니다.</span><span class="sxs-lookup"><span data-stu-id="42005-319">**Windows Server 2012** - The file type will always be `.mdb`</span></span>
- <span data-ttu-id="42005-320">**Windows Server 2012 R2** - 구성에서 `.mdb`를 지정하지 않은 경우 파일 형식은 기본적으로 `.edb`입니다.</span><span class="sxs-lookup"><span data-stu-id="42005-320">**Windows Server 2012 R2** - The file type will default to `.edb` unless a `.mdb` is specified in the configuration</span></span>

<span data-ttu-id="42005-321">끌어오기 서버를 설치하기 위한 [고급 예제 스크립트](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts)에서는 web.config 파일 설정을 자동으로 제어하여 파일 형식으로 인한 오류 발생을 방지하는 방법에 대한 예제도 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42005-321">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>
