---
title: 관리 OData 웹 서비스에 대 한 XML 스키마 파일을 작성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: a806d012097d107b6cc35710b9a93f2b27dd1ace
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857979"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="e2f12-102">관리 OData 웹 서비스용 XML 스키마 파일 작성</span><span class="sxs-lookup"><span data-stu-id="e2f12-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="e2f12-103">웹 서비스를 노출 하는 리소스를 정의한 후 (참조 [관리 OData 웹 서비스의 MOF 스키마 파일을 제작](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), 지원 되는 구현 하는 기본 Windows PowerShell cmdlet에 대 한 해당 리소스를 매핑 준수 하는 XML 파일을 만들어 각 리소스에 대 한 작업을 [리소스 매핑 스키마](./resource-mapping-schema.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f12-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="e2f12-104">또한 XML 파일 리소스에 액세스 하려면 클라이언트에서 사용 되는 Url을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f12-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="e2f12-105">Mappng 리소스 url</span><span class="sxs-lookup"><span data-stu-id="e2f12-105">Mappng resources to URLs</span></span>

<span data-ttu-id="e2f12-106">XML 파일의 첫 번째 부분에 액세스 하는 데 사용 되는 Url에 MOF 스키마 파일에 정의 된 리소스를 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f12-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="e2f12-107">다음 예제에서는 해당 매핑을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e2f12-107">The following example shows that mapping.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<ResourceMetadata xmlns="http://schemas.microsoft.com/powershell-web-services/2010/09">
    <SchemaNamespace>PswsTest</SchemaNamespace>
    <ContainerName>PSWSEntityContainer</ContainerName>
    <Resources>
        <Resource>
            <RelativeUrl>Service</RelativeUrl>
            <Class>PswsTest_Service</Class>
        </Resource>
        <Resource>
            <RelativeUrl>Process</RelativeUrl>
            <Class>PswsTest_Process</Class>
        </Resource>
    </Resources>
```

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="e2f12-108">CRUD 작업에 매핑 cmdlet</span><span class="sxs-lookup"><span data-stu-id="e2f12-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="e2f12-109">CRUD에 해당 하는 cmdlet을 지정 합니다 (만들기, 읽기, 업데이트 및 삭제) 리소스를 지 원하는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="e2f12-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="e2f12-110">관리 odata에서 [리소스 매핑 스키마](./resource-mapping-schema.md), CRUD 작업은 다음과 같이 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2f12-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="e2f12-111">CRUD 명령</span><span class="sxs-lookup"><span data-stu-id="e2f12-111">CRUD command</span></span>|<span data-ttu-id="e2f12-112">XML 요소</span><span class="sxs-lookup"><span data-stu-id="e2f12-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="e2f12-113">만들기</span><span class="sxs-lookup"><span data-stu-id="e2f12-113">Create</span></span>|<span data-ttu-id="e2f12-114">만들기</span><span class="sxs-lookup"><span data-stu-id="e2f12-114">Create</span></span>|
|<span data-ttu-id="e2f12-115">읽기</span><span class="sxs-lookup"><span data-stu-id="e2f12-115">Read</span></span>|<span data-ttu-id="e2f12-116">쿼리</span><span class="sxs-lookup"><span data-stu-id="e2f12-116">Query</span></span>|
|<span data-ttu-id="e2f12-117">업데이트</span><span class="sxs-lookup"><span data-stu-id="e2f12-117">Update</span></span>|<span data-ttu-id="e2f12-118">업데이트</span><span class="sxs-lookup"><span data-stu-id="e2f12-118">Update</span></span>|
|<span data-ttu-id="e2f12-119">삭제</span><span class="sxs-lookup"><span data-stu-id="e2f12-119">Delete</span></span>|<span data-ttu-id="e2f12-120">삭제</span><span class="sxs-lookup"><span data-stu-id="e2f12-120">Delete</span></span>|

<span data-ttu-id="e2f12-121">다음 예제에서 만들기, 읽기 및 업데이트 작업에 대 한 매핑을 보여 줍니다.는 `Service` 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="e2f12-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

```xml
<ClassImplementations>
        <Class>
            <Name>PswsTest_Service</Name>
            <CmdletImplementation>
                <Query>
                    <Cmdlet>Get-Service</Cmdlet>
                        <FieldParameterMap>
                            <Field>
                                <FieldName>ServiceName</FieldName>
                                <ParameterName>Name</ParameterName>
                            </Field>
                        </FieldParameterMap>
                        <ParameterSets>
                            <ParameterSet>
                                <Name>Default</Name>
                                <Parameter><Name>Name</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>DisplayName</Name>
                                <Parameter><Name>DisplayName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>InputObject</Name>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Query>
                <Update>
                    <Cmdlet>Set-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>Name</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>Status</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                        <ParameterSet>
                            <Name>InputObject</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Update>
                <Create>
                    <Cmdlet>New-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>__AllParameterSets</Name>
                            <Parameter><Name>BinaryPathName</Name></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>DependsOn</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Create>
            </CmdletImplementation>
        </Class>
```

## <a name="see-also"></a><span data-ttu-id="e2f12-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2f12-122">See Also</span></span>

[<span data-ttu-id="e2f12-123">관리 OData 웹 서비스의 MOF 스키마 파일 작성</span><span class="sxs-lookup"><span data-stu-id="e2f12-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="e2f12-124">리소스 매핑 스키마</span><span class="sxs-lookup"><span data-stu-id="e2f12-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="e2f12-125">관리 OData 웹 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="e2f12-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)