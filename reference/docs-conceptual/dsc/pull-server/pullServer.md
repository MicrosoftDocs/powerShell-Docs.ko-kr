---
ms.date: 01/08/2020
keywords: dsc,powershell,configuration,setup
title: DSC 끌어오기 서비스
ms.openlocfilehash: f171c3dc579dfb24a8c9fb87fbb50dccae619091
ms.sourcegitcommit: aaf1284dfec2e4c698009d6dc27ff103aaafd581
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76885390"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="b590b-103">원하는 상태 구성 끌어오기 서비스</span><span class="sxs-lookup"><span data-stu-id="b590b-103">Desired State Configuration Pull Service</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b590b-104">끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-104">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="b590b-105">관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-105">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="b590b-106">끌어오기 서비스 솔루션을 사용하여 LCM(로컬 구성 관리자)을 중앙 집중식으로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-106">Local Configuration Manager (LCM) can be centrally managed by a Pull Service solution.</span></span> <span data-ttu-id="b590b-107">이러한 접근 방법을 사용할 경우 관리되는 노드가 서비스에 등록되고, 해당 노드에 LCM 설정의 구성이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-107">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span> <span data-ttu-id="b590b-108">구성과 해당 구성에 대한 종속성으로 필요한 모든 DSC 리소스가 컴퓨터에 다운로드되고 LCM에서 구성을 관리하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-108">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span> <span data-ttu-id="b590b-109">관리하는 컴퓨터의 상태에 대한 정보는 보고를 위해 서비스에 업로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-109">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span> <span data-ttu-id="b590b-110">이 개념을 "끌어오기 서비스"라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-110">This concept is referred to as "pull service".</span></span>

<span data-ttu-id="b590b-111">풀 서비스에 대한 현재 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-111">The current options for pull service include:</span></span>

- <span data-ttu-id="b590b-112">Azure Automation 필요한 상태 구성 서비스</span><span class="sxs-lookup"><span data-stu-id="b590b-112">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="b590b-113">Windows Server에서 실행되는 끌어오기 서비스</span><span class="sxs-lookup"><span data-stu-id="b590b-113">A pull service running on Windows Server</span></span>
- <span data-ttu-id="b590b-114">커뮤니티에서 유지 관리하는 오픈 소스 솔루션</span><span class="sxs-lookup"><span data-stu-id="b590b-114">Community maintained open-source solutions</span></span>
- <span data-ttu-id="b590b-115">SMB 공유</span><span class="sxs-lookup"><span data-stu-id="b590b-115">An SMB share</span></span>

<span data-ttu-id="b590b-116">각 솔루션에 권장되는 크기는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-116">The recommended scale for each solution is as follows:</span></span>

|                   <span data-ttu-id="b590b-117">해결 방법</span><span class="sxs-lookup"><span data-stu-id="b590b-117">Solution</span></span>                   |              <span data-ttu-id="b590b-118">클라이언트 노드</span><span class="sxs-lookup"><span data-stu-id="b590b-118">Client nodes</span></span>              |
| -------------------------------------------- | -------------------------------------- |
| <span data-ttu-id="b590b-119">MDB/ESENT 데이터베이스를 사용하는 Windows 끌어오기 서버</span><span class="sxs-lookup"><span data-stu-id="b590b-119">Windows Pull Server using MDB/ESENT database</span></span> | <span data-ttu-id="b590b-120">최대 500개 노드</span><span class="sxs-lookup"><span data-stu-id="b590b-120">Up to 500 nodes</span></span>                        |
| <span data-ttu-id="b590b-121">SQL 데이터베이스를 사용하는 Windows 끌어오기 서버</span><span class="sxs-lookup"><span data-stu-id="b590b-121">Windows Pull Server using SQL database</span></span>       | <span data-ttu-id="b590b-122">최대 1000개 노드</span><span class="sxs-lookup"><span data-stu-id="b590b-122">Up to 1000 nodes</span></span>                       |
| <span data-ttu-id="b590b-123">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="b590b-123">Azure Automation DSC</span></span>                         | <span data-ttu-id="b590b-124">1000개 이상의 노드를 포함하는 시나리오</span><span class="sxs-lookup"><span data-stu-id="b590b-124">Scenarios with greater than 1000 nodes</span></span> |

<span data-ttu-id="b590b-125">**권장 솔루션**이며, 대부분의 기능에서 사용 가능한 옵션은 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)입니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-125">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="b590b-126">Azure 서비스는 개인 데이터 센터의 온-프레미스에 있는 노드를 관리하거나 Azure와 AWS 같은 퍼블릭 클라우드에 있는 노드를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-126">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span> <span data-ttu-id="b590b-127">서버를 인터넷에 직접 연결할 수 없는 개인 환경의 경우, 아웃바운드 트래픽을 게시된 Azure IP 범위로만 제한하세요([Azure Datacenter IP Ranges](https://www.microsoft.com/download/details.aspx?id=41653)(Azure 데이터 센터 IP 범위) 참조).</span><span class="sxs-lookup"><span data-stu-id="b590b-127">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="b590b-128">Windows Server의 풀 서비스에서 현재 사용할 수 없는 온라인 서비스의 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-128">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>

- <span data-ttu-id="b590b-129">전송 중 및 미사용 중인 모든 데이터 암호화</span><span class="sxs-lookup"><span data-stu-id="b590b-129">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="b590b-130">클라이언트 인증서 자동 생성 및 관리</span><span class="sxs-lookup"><span data-stu-id="b590b-130">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="b590b-131">[암호/자격 증명](/azure/automation/automation-credentials) 또는 서버 이름이나 연결 문자열 같은[변수](/azure/automation/automation-variables)를 중앙에서 관리하기 위한 비밀 저장소</span><span class="sxs-lookup"><span data-stu-id="b590b-131">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="b590b-132">[LCM 구성](../managing-nodes/metaConfig.md#basic-settings) 노드를 중앙에서 관리</span><span class="sxs-lookup"><span data-stu-id="b590b-132">Centrally manage node [LCM configuration](../managing-nodes/metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="b590b-133">중앙에서 클라이언트 노드에 구성 할당</span><span class="sxs-lookup"><span data-stu-id="b590b-133">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="b590b-134">프로덕션으로 전환하기 전에 테스트를 위해 “카나리아 그룹”에 구성 변경 내용 릴리스</span><span class="sxs-lookup"><span data-stu-id="b590b-134">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="b590b-135">그래픽 보고</span><span class="sxs-lookup"><span data-stu-id="b590b-135">Graphical reporting</span></span>
  - <span data-ttu-id="b590b-136">DSC 리소스 수준 단위에서 상태 세부 정보</span><span class="sxs-lookup"><span data-stu-id="b590b-136">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="b590b-137">문제 해결을 위해 클라이언트 시스템의 상세 오류 메시지</span><span class="sxs-lookup"><span data-stu-id="b590b-137">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="b590b-138">경고, 자동화된 작업, 보고 및 경고용 Android/iOS 앱에 대해 [Azure Log Analytics와 통합](/azure/automation/automation-dsc-diagnostics)</span><span class="sxs-lookup"><span data-stu-id="b590b-138">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="b590b-139">Windows Server의 DSC 끌어오기 서비스</span><span class="sxs-lookup"><span data-stu-id="b590b-139">DSC pull service in Windows Server</span></span>

<span data-ttu-id="b590b-140">Windows Server에서 실행할 끌어오기 서비스를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-140">It is possible to configure a pull service to run on Windows Server.</span></span> <span data-ttu-id="b590b-141">Windows Server에 포함된 끌어오기 서비스 솔루션에는 다운로드할 구성/모듈을 저장하고 보고서 데이터를 데이터베이스에 캡처하는 기능한 포함되어 있다는 사실을 알아두세요.</span><span class="sxs-lookup"><span data-stu-id="b590b-141">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data into a database.</span></span> <span data-ttu-id="b590b-142">Azure의 서비스에서 제공하는 다양한 기능은 포함되어 있지 않으므로 서비스가 사용되는 방식을 평가하기에 좋은 도구는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-142">It does not include many of the capabilities offered by the service in Azure and so, is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="b590b-143">Windows Server에서 제공되는 끌어오기 서버는 해당 노드에서 요청하면 OData 인터페이스를 사용하여 DSC 구성 파일을 대상 노드에 사용할 수 있도록 하는 IIS의 웹 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-143">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="b590b-144">끌어오기 서버 사용을 위한 요구 사항:</span><span class="sxs-lookup"><span data-stu-id="b590b-144">Requirements for using a pull server:</span></span>

- <span data-ttu-id="b590b-145">다음 항목을 실행 중인 서버:</span><span class="sxs-lookup"><span data-stu-id="b590b-145">A server running:</span></span>
  - <span data-ttu-id="b590b-146">WMF/PowerShell 4.0 이상</span><span class="sxs-lookup"><span data-stu-id="b590b-146">WMF/PowerShell 4.0 or greater</span></span>
  - <span data-ttu-id="b590b-147">IIS 서버 역할</span><span class="sxs-lookup"><span data-stu-id="b590b-147">IIS server role</span></span>
  - <span data-ttu-id="b590b-148">DSC 서비스</span><span class="sxs-lookup"><span data-stu-id="b590b-148">DSC Service</span></span>
- <span data-ttu-id="b590b-149">인증서를 생성하여 대상 노드에서 LCM(로컬 구성 관리자)에 전달된 자격 증명을 보호할 방법이 있으면 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-149">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="b590b-150">가져오기 서비스를 호스트하도록 Windows Server를 구성하는 가장 좋은 방법은 DSC 구성을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-150">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span> <span data-ttu-id="b590b-151">예제 스크립트는 아래에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-151">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="b590b-152">지원되는 데이터베이스 시스템</span><span class="sxs-lookup"><span data-stu-id="b590b-152">Supported database systems</span></span>

| <span data-ttu-id="b590b-153">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="b590b-153">WMF 4.0</span></span> |       <span data-ttu-id="b590b-154">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="b590b-154">WMF 5.0</span></span>        |       <span data-ttu-id="b590b-155">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="b590b-155">WMF 5.1</span></span>        | <span data-ttu-id="b590b-156">WMF 5.1(Windows Server Insider Preview 17090)</span><span class="sxs-lookup"><span data-stu-id="b590b-156">WMF 5.1 (Windows Server Insider Preview 17090)</span></span> |
| ------- | -------------------- | -------------------- | ---------------------------------------------- |
| <span data-ttu-id="b590b-157">MDB</span><span class="sxs-lookup"><span data-stu-id="b590b-157">MDB</span></span>     | <span data-ttu-id="b590b-158">ESENT(기본값), MDB</span><span class="sxs-lookup"><span data-stu-id="b590b-158">ESENT (Default), MDB</span></span> | <span data-ttu-id="b590b-159">ESENT(기본값), MDB</span><span class="sxs-lookup"><span data-stu-id="b590b-159">ESENT (Default), MDB</span></span> | <span data-ttu-id="b590b-160">ESENT(기본값), SQL Server, MDB</span><span class="sxs-lookup"><span data-stu-id="b590b-160">ESENT (Default), SQL Server, MDB</span></span>               |

<span data-ttu-id="b590b-161">[Windows Server Insider Preview](https://www.microsoft.com/software-download/windowsinsiderpreviewserver) 17090 릴리스부터 SQL Server는 끌어오기 서비스(Windows 기능 *DSC-Service*)에 지원되는 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-161">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span> <span data-ttu-id="b590b-162">이는 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)로 마이그레이션되지 않은 대규모 DSC 환경의 규모를 조정하기 위한 새로운 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-162">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> [!NOTE]
> <span data-ttu-id="b590b-163">SQL Server 지원은 WMF 5.1(이하)의 이전 버전에 추가되지 않으며, Windows Server 17090 이상 버전에서만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-163">SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="b590b-164">SQL Server를 사용하도록 끌어오기 서버를 구성하려면 **SqlProvider**를 `$true`로, **SqlConnectionString**을 유효한 SQL Server 연결 문자열로 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="b590b-164">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span> <span data-ttu-id="b590b-165">자세한 내용은 [SqlClient 연결 문자열](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b590b-165">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="b590b-166">**xDscWebService**를 사용한 SQL Server 구성의 예를 보려면 먼저 [xDscWebService 리소스 사용](#using-the-xdscwebservice-resource)을 읽은 후 [GitHub의 Sample_xDscWebServiceRegistration_UseSQLProvider.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1)을 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="b590b-166">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="b590b-167">xDscWebService 리소스 사용</span><span class="sxs-lookup"><span data-stu-id="b590b-167">Using the xDscWebService resource</span></span>

<span data-ttu-id="b590b-168">웹 끌어오기 서버를 설정하는 가장 쉬운 방법은 **xPSDesiredStateConfiguration** 모듈에 포함된 **xDscWebService** 리소스를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-168">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="b590b-169">다음 단계에서는 웹 서비스를 설정하는 `Configuration`에서 리소스를 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-169">The following steps explain how to use the resource in a `Configuration` that sets up the web service.</span></span>

1. <span data-ttu-id="b590b-170">[Install-Module](/reference/6/PowerShellGet/Install-Module.md) cmdlet을 호출하여 **xPSDesiredStateConfiguration** 모듈을 설치하세요.</span><span class="sxs-lookup"><span data-stu-id="b590b-170">Call the [Install-Module](/reference/6/PowerShellGet/Install-Module.md) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span>

   > [!NOTE]
   > <span data-ttu-id="b590b-171">`Install-Module`은 PowerShell 5.0 이상에 포함된 **PowerShellGet** 모듈에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-171">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0 and higher.</span></span>

1. <span data-ttu-id="b590b-172">조직 내 또는 공공 기관 내의 신뢰할 수 있는 인증 기관에서 DSC 끌어오기 서버에 대한 SSL 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-172">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="b590b-173">기관에서 받은 인증서는 일반적으로 PFX 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-173">The certificate received from the authority is usually in the PFX format.</span></span>
1. <span data-ttu-id="b590b-174">`CERT:\LocalMachine\My`라는 기본 위치에 DSC 끌어오기 서버 역할을 할 노드의 인증서를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-174">Install the certificate on the node that will become the DSC Pull server in the default location, which should be `CERT:\LocalMachine\My`.</span></span>
   - <span data-ttu-id="b590b-175">인증서 지문을 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-175">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="b590b-176">등록 키로 사용할 GUID를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-176">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="b590b-177">PowerShell을 사용하여 생성하려면 PS 프롬프트에 '`[guid]::newGuid()`' 또는 '`New-Guid`'를 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-177">To generate one using PowerShell enter the following at the PS prompt and press enter: `[guid]::newGuid()` or `New-Guid`.</span></span> <span data-ttu-id="b590b-178">이 키는 클라이언트 노드에서 등록할 때 인증할 공유 키로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-178">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="b590b-179">자세한 내용은 아래 등록 키 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b590b-179">For more information, see the Registration Key section below.</span></span>
1. <span data-ttu-id="b590b-180">PowerShell ISE에서 다음의 구성 스크립트(**xPSDesiredStateConfiguration** 모듈의 폴더에 `Sample_xDscWebServiceRegistration.ps1`으로 포함됨)를 시작합니다(<kbd>F5</kbd>).</span><span class="sxs-lookup"><span data-stu-id="b590b-180">In the PowerShell ISE, start (<kbd>F5</kbd>) the following configuration script (included in the folder of the **xPSDesiredStateConfiguration** module as `Sample_xDscWebServiceRegistration.ps1`) .</span></span> <span data-ttu-id="b590b-181">이 스크립트는 끌어오기 서버를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-181">This script sets up the pull server.</span></span>

    ```powershell
    configuration Sample_xDscWebServiceRegistration
    {
        param
        (
            [string[]]$NodeName = 'localhost',

            [ValidateNotNullOrEmpty()]
            [string] $certificateThumbPrint,

            [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
        )

        Import-DSCResource -ModuleName PSDesiredStateConfiguration
        Import-DSCResource -ModuleName xPSDesiredStateConfiguration

        Node $NodeName
        {
            WindowsFeature DSCServiceFeature
            {
                Ensure = "Present"
                Name   = "DSC-Service"
            }

            xDscWebService PSDSCPullServer
            {
                Ensure                  = "Present"
                EndpointName            = "PSDSCPullServer"
                Port                    = 8080
                PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
                CertificateThumbPrint   = $certificateThumbPrint
                ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                State                   = "Started"
                DependsOn               = "[WindowsFeature]DSCServiceFeature"
                RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
                AcceptSelfSignedCertificates = $true
                UseSecurityBestPractices     = $true
                Enable32BitAppOnWin64   = $false
            }

            File RegistrationKeyFile
            {
                Ensure          = 'Present'
                Type            = 'File'
                DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
                Contents        = $RegistrationKey
            }
        }
    }
    ```

1. <span data-ttu-id="b590b-182">구성을 실행합니다. 이때 SSL 인증서의 지문을 **certificateThumbPrint** 매개 변수로 전달하고 GUID 등록 키를 **RegistrationKey** 매개 변수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-182">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="b590b-183">등록 키</span><span class="sxs-lookup"><span data-stu-id="b590b-183">Registration Key</span></span>

<span data-ttu-id="b590b-184">구성 ID 대신 구성 이름을 사용할 수 있도록 클라이언트 노드가 서버에 등록할 수 있도록 하려면 위 구성에서 만든 등록 키가 `C:\Program Files\WindowsPowerShell\DscService`에서 `RegistrationKeys.txt`라는 파일에 저장되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-184">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="b590b-185">등록 키는 끌어오기 서버에 클라이언트를 처음 등록할 때 사용되는 공유 암호 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-185">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="b590b-186">클라이언트는 등록이 완료되면 끌어오기 서버에 고유하게 인증하는 데 사용되는 자체 서명된 인증서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-186">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="b590b-187">이 인증서의 지문은 로컬에 저장되고 끌어오기 서버의 URL과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-187">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="b590b-188">PowerShell 4.0에서는 등록 키가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-188">Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="b590b-189">끌어오기 서버에 인증하도록 노드를 구성하려면 이 끌어오기 서버에 등록할 모든 대상 노드의 메타 구성에 등록 키가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-189">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="b590b-190">아래 메타 구성에서 **RegistrationKey**는 대상 머신이 성공적으로 등록된 후에 제거되며, 해당 값은 끌어오기 서버의 `RegistrationKeys.txt` 파일에 저장된 값과 일치해야 합니다(이 예제의 경우 '140a952b-b9d6-406b-b416-e0f759c9c0e4').</span><span class="sxs-lookup"><span data-stu-id="b590b-190">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value must match the value stored in the `RegistrationKeys.txt` file on the pull server ('140a952b-b9d6-406b-b416-e0f759c9c0e4' for this example).</span></span> <span data-ttu-id="b590b-191">등록 키 값을 알면 대상 컴퓨터가 끌어오기 서버에 등록할 수 있으므로 등록 키 값을 항상 안전하게 보관하세요.</span><span class="sxs-lookup"><span data-stu-id="b590b-191">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to set up pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> [!NOTE]
> <span data-ttu-id="b590b-192">**ReportServerWeb** 섹션을 사용하면 보고 데이터를 끌어오기 서버로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-192">The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="b590b-193">메타 구성 파일에 **ConfigurationID** 속성이 없으면 끌어오기 서버가 V2 버전의 끌어오기 서버 프로토콜을 지원하므로 초기 등록이 필요하다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-193">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span> <span data-ttu-id="b590b-194">반대로 **ConfigurationID**가 있으면 V1 버전의 끌어오기 서버 프로토콜이 사용되고 등록 처리가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-194">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

> [!NOTE]
> <span data-ttu-id="b590b-195">밀어넣기 시나리오의 현재 릴리스에는 버그가 있기 때문에 끌어오기 서버에 등록하지 않은 노드에 대해 메타 구성 파일에서 ConfigurationID 속성을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-195">In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="b590b-196">따라서 V1 끌어오기 서버 프로토콜이 강제로 사용되고 등록 실패 메시지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-196">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="b590b-197">구성 및 리소스 배치</span><span class="sxs-lookup"><span data-stu-id="b590b-197">Placing configurations and resources</span></span>

<span data-ttu-id="b590b-198">끌어오기 서버 설정이 완료되면 끌어오기 서버 구성의 **ConfigurationPath** 및 **ModulePath** 속성에 정의된 폴더에 끌어올 대상 노드에 사용할 수 있는 모듈 및 구성을 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-198">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span> <span data-ttu-id="b590b-199">이러한 파일은 특정 형식이어야만 끌어오기 서버에서 올바로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-199">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="b590b-200">DSC 리소스 모듈 패키지 형식</span><span class="sxs-lookup"><span data-stu-id="b590b-200">DSC resource module package format</span></span>

<span data-ttu-id="b590b-201">각 리소스 모듈은 압축해야 하며 `{Module Name}_{Module Version}.zip` 패턴에 따라 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-201">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>

<span data-ttu-id="b590b-202">예를 들어 모듈 버전이 3.1.2.0인 `xWebAdministration_3.1.2.0.zip`이라는 모듈은 **xWebAdminstration**으로 이름이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-202">For example, a module named **xWebAdminstration** with a module version of 3.1.2.0 would be named `xWebAdministration_3.1.2.0.zip`.</span></span> <span data-ttu-id="b590b-203">모듈의 각 버전은 단일 zip 파일에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-203">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="b590b-204">각 zip 파일에 리소스의 단일 버전만 있으므로 단일 디렉터리에서 여러 모듈 버전을 지원하는 WMF 5.0에서 추가된 모듈 형식은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-204">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="b590b-205">따라서 끌어오기 서버에서 사용할 DSC 리소스 모듈을 패키징하기 전에 디렉터리 구조를 약간 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-205">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span> <span data-ttu-id="b590b-206">WMF 5.0의 DSC 리소스를 포함하는 모듈의 기본 형식은 `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`입니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-206">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="b590b-207">끌어오기 서버에 대해 패키징하기 전에 **{모듈 버전}** 폴더를 제거하면 되므로 경로는 `{Module Folder}\DscResources\{DSC Resource Folder}\`가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-207">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="b590b-208">이렇게 변경하고 위에서 설명한 대로 폴더를 압축하여 이러한 zip 파일을 **ModulePath** 폴더에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-208">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="b590b-209">`New-DscChecksum {module zip file}`을 사용하여 새로 추가된 모듈에 대한 체크섬 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-209">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="b590b-210">구성 MOF 형식</span><span class="sxs-lookup"><span data-stu-id="b590b-210">Configuration MOF format</span></span>

<span data-ttu-id="b590b-211">구성 MOF 파일은 대상 노드의 LCM이 구성에 대한 유효성을 검사할 수 있도록 체크섬 파일과 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-211">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="b590b-212">체크섬을 만들려면 [New-DscChecksum](/reference/6/PSDesiredStateConfiguration/New-DSCCheckSum.md) cmdlet을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-212">To create a checksum, call the [New-DscChecksum](/reference/6/PSDesiredStateConfiguration/New-DSCCheckSum.md) cmdlet.</span></span> <span data-ttu-id="b590b-213">이 cmdlet은 구성 MOF가 있는 폴더를 지정하는 **Path** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-213">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="b590b-214">cmdlet은 `ConfigurationMOFName.mof.checksum`이라는 체크섬 파일을 만들며, 여기서 `ConfigurationMOFName`은 구성 mof 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-214">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="b590b-215">지정된 폴더에 구성 MOF 파일이 두 개 이상 있는 경우, 폴더에 있는 각 구성에 대해 체크섬이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-215">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span> <span data-ttu-id="b590b-216">MOF 파일 및 연관된 체크섬 파일을 **ConfigurationPath** 폴더에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-216">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="b590b-217">어떤 식으로든 구성 MOF 파일을 변경하는 경우 체크섬 파일도 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-217">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="b590b-218">도구</span><span class="sxs-lookup"><span data-stu-id="b590b-218">Tooling</span></span>

<span data-ttu-id="b590b-219">끌어오기 서버를 더 간단히 설정하고 유효성을 검사하고 관리할 수 있도록 xPSDesiredStateConfiguration 모듈의 최신 버전에는 다음 도구가 예제로 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-219">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="b590b-220">끌어오기 서버에서 사용할 DSC 리소스 모듈 및 구성 파일을 패키징하는 데 도움이 되는 모듈:</span><span class="sxs-lookup"><span data-stu-id="b590b-220">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span>
   <span data-ttu-id="b590b-221">[PublishModulesAndMofsToPullServer.psm1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetup.psm1).</span><span class="sxs-lookup"><span data-stu-id="b590b-221">[PublishModulesAndMofsToPullServer.psm1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetup.psm1).</span></span>
   <span data-ttu-id="b590b-222">다음은 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-222">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="b590b-223">끌어오기 서버가 올바로 구성되었는지 확인하는 스크립트:</span><span class="sxs-lookup"><span data-stu-id="b590b-223">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="b590b-224">[PullServerSetupTests.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetupTest/DscPullServerSetupTest.ps1).</span><span class="sxs-lookup"><span data-stu-id="b590b-224">[PullServerSetupTests.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetupTest/DscPullServerSetupTest.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="b590b-225">끌어오기 서비스에 대한 커뮤니티 솔루션</span><span class="sxs-lookup"><span data-stu-id="b590b-225">Community Solutions for Pull Service</span></span>

<span data-ttu-id="b590b-226">DSC 커뮤니티는 끌어오기 서비스 프로토콜을 구현하는 여러 가지 솔루션을 제작했습니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-226">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span> <span data-ttu-id="b590b-227">이러한 솔루션은 온-프레미스 환경에 끌어오기 서비스 기능을 제공하며, 증분 향상 기능으로 커뮤니티에 다시 기여할 수 있는 기회를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-227">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="b590b-228">Tug</span><span class="sxs-lookup"><span data-stu-id="b590b-228">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="b590b-229">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="b590b-229">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="b590b-230">끌어오기 클라이언트 구성</span><span class="sxs-lookup"><span data-stu-id="b590b-230">Pull client configuration</span></span>

<span data-ttu-id="b590b-231">다음 항목에서는 끌어오기 클라이언트를 설정하는 것에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b590b-231">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="b590b-232">구성 ID를 사용하여 DSC 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="b590b-232">Set up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="b590b-233">구성 이름을 사용하여 DSC 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="b590b-233">Set up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="b590b-234">부분 구성</span><span class="sxs-lookup"><span data-stu-id="b590b-234">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="b590b-235">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b590b-235">See also</span></span>

- [<span data-ttu-id="b590b-236">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="b590b-236">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="b590b-237">구성 시행</span><span class="sxs-lookup"><span data-stu-id="b590b-237">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="b590b-238">DSC 보고서 서버 사용</span><span class="sxs-lookup"><span data-stu-id="b590b-238">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="b590b-239">[[MS-DSCPM]: 필요한 상태 구성 끌어오기 모델 프로토콜](https://docs.microsoft.com/openspecs/windows_protocols/ms-dscpm/ea744c01-51a2-4000-9ef2-312711dcc8c9)</span><span class="sxs-lookup"><span data-stu-id="b590b-239">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://docs.microsoft.com/openspecs/windows_protocols/ms-dscpm/ea744c01-51a2-4000-9ef2-312711dcc8c9)</span></span>
- <span data-ttu-id="b590b-240">[[MS-DSCPM]: 필요한 상태 구성 끌어오기 모델 프로토콜 오류](https://docs.microsoft.com/openspecs/windows_protocols/ms-winerrata/f5fc7ae3-9172-41e8-ac6a-2a5a5b7bfaf5)</span><span class="sxs-lookup"><span data-stu-id="b590b-240">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://docs.microsoft.com/openspecs/windows_protocols/ms-winerrata/f5fc7ae3-9172-41e8-ac6a-2a5a5b7bfaf5)</span></span>
