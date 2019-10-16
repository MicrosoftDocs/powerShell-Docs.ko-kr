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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359722"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="8d579-102">관리 OData 웹 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="8d579-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="8d579-103">관리 ODATA IIS 확장은 Windows PowerShell cmdlet 및 스크립트를 통해 액세스 하는 관리 데이터를 OData 웹 서비스 엔터티로 노출 하는 ASP.NET 웹 서비스 끝점을 만들기 위한 인프라입니다.</span><span class="sxs-lookup"><span data-stu-id="8d579-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="8d579-104">OData 요청을 처리 하 고 Windows PowerShell 호출로 변환 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d579-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="8d579-105">제품 팀은이 인프라를 기반으로 구축 하 여 특정 관리 데이터 집합을 노출 하는 끝점을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d579-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="8d579-106">[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) 샘플을 다운로드 하 여 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d579-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="8d579-107">지침에 따라 웹 서비스를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d579-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="8d579-108">이 웹 서비스는 CRUD (만들기, 읽기, 업데이트 및 삭제) 작업을 통해 서비스 및 프로세스를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d579-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="8d579-109">웹 서비스에 대 한 CRUD 요청은 요청 된 작업을 수행 하는 Windows PowerShell 명령을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d579-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="8d579-110">CRUD 작업과 기본 Windows PowerShell 명령 간의 매핑은 두 개의 스키마 파일인 schema. mof 및 schema .xml에 의해 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d579-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="8d579-111">스키마 .mof 파일은 DMTF ( [Distributed Management Task Force](https://www.dmtf.org/) ) Mof (Managed Object) 표준을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d579-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="8d579-112">Schema .xml 파일은 [리소스 매핑 스키마](./resource-mapping-schema.md)에 설명 된 xml 스키마를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d579-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8d579-113">Windows Server 2008 R2 s p 1에서 관리 ODATA IIS 확장을 사용 하도록 설정 하기 전에 다음 기능을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d579-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="8d579-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="8d579-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="8d579-115">IIS-웹 서버</span><span class="sxs-lookup"><span data-stu-id="8d579-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="8d579-116">IIS-Http 추적</span><span class="sxs-lookup"><span data-stu-id="8d579-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="8d579-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="8d579-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="8d579-118">관리 OData 웹 서비스를 만드는 단계</span><span class="sxs-lookup"><span data-stu-id="8d579-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="8d579-119">다음 항목에서는 관리 OData 웹 서비스를 만들고 배포 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d579-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="8d579-120">관리 OData 웹 서비스에 리소스 추가</span><span class="sxs-lookup"><span data-stu-id="8d579-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="8d579-121">관리 OData 웹 서비스에 대 한 사용자 지정 권한 부여 구현</span><span class="sxs-lookup"><span data-stu-id="8d579-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="8d579-122">관리 OData 웹 서비스에 대 한 SessionConfiguration 구현</span><span class="sxs-lookup"><span data-stu-id="8d579-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="8d579-123">관리 OData 웹 서비스용 MOF 스키마 파일 작성</span><span class="sxs-lookup"><span data-stu-id="8d579-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="8d579-124">관리 OData 웹 서비스에 대 한 XML 스키마 파일 작성</span><span class="sxs-lookup"><span data-stu-id="8d579-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="8d579-125">관리 OData 웹 서비스용 web.config 파일 작성</span><span class="sxs-lookup"><span data-stu-id="8d579-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="8d579-126">관리 OData 웹 서비스 배포</span><span class="sxs-lookup"><span data-stu-id="8d579-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="8d579-127">관리 OData 엔터티 연결</span><span class="sxs-lookup"><span data-stu-id="8d579-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="8d579-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8d579-128">See Also</span></span>

[<span data-ttu-id="8d579-129">관리 ODATA IIS 확장 스키마 파일</span><span class="sxs-lookup"><span data-stu-id="8d579-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
