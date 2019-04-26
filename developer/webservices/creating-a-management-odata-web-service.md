---
title: 관리 OData 웹 서비스 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080699"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="18fd6-102">관리 OData 웹 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="18fd6-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="18fd6-103">관리 ODATA IIS 확장은 Windows PowerShell cmdlet 및 OData 웹 서비스 엔터티로 스크립트를 통해 액세스 하 여 관리 데이터를 노출 하는 ASP.NET 웹 서비스 시작점과 끝점을 만들기 위한 인프라.</span><span class="sxs-lookup"><span data-stu-id="18fd6-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="18fd6-104">OData 요청을 처리 하 여 Windows PowerShell 호출을 변환 하는 사용자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18fd6-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="18fd6-105">제품 팀은 관리 데이터의 특정 집합을 노출 하는 끝점을 만들려면이 인프라를 기반으로 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18fd6-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="18fd6-106">다운로드 및 설치 합니다 [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="18fd6-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="18fd6-107">웹 서비스를 배포 하는 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="18fd6-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="18fd6-108">이 웹 서비스 만들기, 읽기, 업데이트 및 삭제 (CRUD) 작업을 통해 서비스 및 프로세스를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="18fd6-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="18fd6-109">웹 서비스에 대 한 CRUD 요청에는 요청한 작업을 수행 하는 Windows PowerShell 명령을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="18fd6-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="18fd6-110">CRUD 작업에서 기본 Windows PowerShell 명령 사이 매핑은 두 개의 스키마 파일과 schema.mof schema.xml에 의해 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="18fd6-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="18fd6-111">Schema.mof 파일이 사용 하 여 [Distributed Management Task Force](https://www.dmtf.org/) (DMTF) MOF (Managed Object) 표준입니다.</span><span class="sxs-lookup"><span data-stu-id="18fd6-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="18fd6-112">Schema.xml 파일에 설명 된 XML 스키마를 사용 하 여 [리소스 매핑 스키마](./resource-mapping-schema.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="18fd6-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="18fd6-113">Windows Server 2008 R2 SP1 관리 ODATA IIS 확장을 사용 하기 전에 다음과 같은 기능을 활성화 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18fd6-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="18fd6-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="18fd6-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="18fd6-115">IIS-웹 서버</span><span class="sxs-lookup"><span data-stu-id="18fd6-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="18fd6-116">IIS-Http 추적</span><span class="sxs-lookup"><span data-stu-id="18fd6-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="18fd6-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="18fd6-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="18fd6-118">관리 OData 웹 서비스를 만들기 위한 단계</span><span class="sxs-lookup"><span data-stu-id="18fd6-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="18fd6-119">다음 항목에는 관리 OData 웹 서비스 만들기 및 배포 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="18fd6-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="18fd6-120">관리 OData 웹 서비스에 리소스 추가</span><span class="sxs-lookup"><span data-stu-id="18fd6-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="18fd6-121">관리 OData 웹 서비스에 대 한 사용자 지정 권한 부여를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="18fd6-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="18fd6-122">관리 OData 웹 서비스에 대 한 SessionConfiguration 구현</span><span class="sxs-lookup"><span data-stu-id="18fd6-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="18fd6-123">관리 OData 웹 서비스의 MOF 스키마 파일 작성</span><span class="sxs-lookup"><span data-stu-id="18fd6-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="18fd6-124">관리 OData 웹 서비스에 대 한 XML 스키마 파일 작성</span><span class="sxs-lookup"><span data-stu-id="18fd6-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="18fd6-125">관리 OData 웹 서비스에 대 한 Web.config 파일 작성</span><span class="sxs-lookup"><span data-stu-id="18fd6-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="18fd6-126">관리 OData 웹 서비스 배포</span><span class="sxs-lookup"><span data-stu-id="18fd6-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="18fd6-127">관리 OData 엔터티를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="18fd6-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="18fd6-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="18fd6-128">See Also</span></span>

[<span data-ttu-id="18fd6-129">관리 ODATA IIS 확장 스키마 파일</span><span class="sxs-lookup"><span data-stu-id="18fd6-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
