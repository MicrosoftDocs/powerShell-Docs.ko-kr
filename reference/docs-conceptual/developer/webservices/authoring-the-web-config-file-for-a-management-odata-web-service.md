---
title: 관리 OData 웹 서비스에 대 한 web.config 파일 작성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569f5d5-9746-40c0-be5e-f218bc4560f7
caps.latest.revision: 4
ms.openlocfilehash: 8e5897c3df38689e80d2135dfb82898bf9a05b86
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561484"
---
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a><span data-ttu-id="e79f2-102">관리 OData 웹 서비스용 Web.config 파일 작성</span><span class="sxs-lookup"><span data-stu-id="e79f2-102">Authoring the Web.config file for a Management OData web service</span></span>

<span data-ttu-id="e79f2-103">관리 OData 웹 서비스를 배포 하려면 먼저 [Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) 및 [register-pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) 인터페이스를 구현 하는 dll과 XML 스키마 파일을 가리키도록 web.config 파일을 구성 해야 합니다 .이 파일을 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e79f2-103">Before you can deploy your Management OData web service, you must configure the web.config file to point to the XML schema files and the DLLs that implement the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) and [System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interfaces.</span></span>

## <a name="sample-config-file"></a><span data-ttu-id="e79f2-104">샘플 구성 파일</span><span class="sxs-lookup"><span data-stu-id="e79f2-104">Sample config file</span></span>

<span data-ttu-id="e79f2-105">다음은 웹 서비스에 대 한 web.config 파일의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="e79f2-105">The following is an example of what the web.config file for your web service looks like.</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
   <configSections>
      <section name="managementOdata" type="Microsoft.Management.Odata.Core.DSConfiguration, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL" />
   </configSections>
   <managementOdata schemaFileName="Schema.mof" resourceMappingFileName="Schema.xml">
      <customAuthorization type="Microsoft.Samples.Management.OData.RoleBasedPlugins.CustomAuthorization" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      <powershell>
         <sessionConfiguration type="Microsoft.Samples.Management.OData.RoleBasedPlugins.SessionConfiguration" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      </powershell>
      <commandInvocation enabled="true" />
      <wcfDataServicesConfig>
      </wcfDataServicesConfig>
   </managementOdata>
   <system.serviceModel>
      <behaviors>
         <serviceBehaviors>
            <behavior>
                  <serviceAuthorization serviceAuthorizationManagerType="Microsoft.Management.Odata.Core.CustomAuthorizationManager, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
            </behavior>
         </serviceBehaviors>
      </behaviors>
      <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
   </system.serviceModel>
   <system.webServer>
      <security>
         <authentication>
            <anonymousAuthentication enabled="false" />
            <basicAuthentication enabled="true" />
            <windowsAuthentication enabled="false" />
         </authentication>
      </security>
  </system.webServer>
</configuration>

```

## <a name="see-also"></a><span data-ttu-id="e79f2-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e79f2-106">See Also</span></span>

[<span data-ttu-id="e79f2-107">관리 OData 웹 서비스에 대한 사용자 지정 권한 부여 구현</span><span class="sxs-lookup"><span data-stu-id="e79f2-107">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[<span data-ttu-id="e79f2-108">관리 OData 웹 서비스에 대한 SessionConfiguration 구현</span><span class="sxs-lookup"><span data-stu-id="e79f2-108">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[<span data-ttu-id="e79f2-109">관리 OData 웹 서비스용 MOF 스키마 파일 작성</span><span class="sxs-lookup"><span data-stu-id="e79f2-109">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="e79f2-110">관리 OData 웹 서비스용 XML 스키마 파일 작성</span><span class="sxs-lookup"><span data-stu-id="e79f2-110">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="e79f2-111">관리 OData 웹 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="e79f2-111">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)
