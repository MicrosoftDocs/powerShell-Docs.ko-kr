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
# <a name="creating-a-management-odata-web-service"></a>관리 OData 웹 서비스 만들기

관리 ODATA IIS 확장은 Windows PowerShell cmdlet 및 OData 웹 서비스 엔터티로 스크립트를 통해 액세스 하 여 관리 데이터를 노출 하는 ASP.NET 웹 서비스 시작점과 끝점을 만들기 위한 인프라. OData 요청을 처리 하 여 Windows PowerShell 호출을 변환 하는 사용자가 있습니다. 제품 팀은 관리 데이터의 특정 집합을 노출 하는 끝점을 만들려면이 인프라를 기반으로 빌드할 수 있습니다.

다운로드 및 설치 합니다 [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) 샘플입니다. 웹 서비스를 배포 하는 지침을 따릅니다. 이 웹 서비스 만들기, 읽기, 업데이트 및 삭제 (CRUD) 작업을 통해 서비스 및 프로세스를 노출합니다. 웹 서비스에 대 한 CRUD 요청에는 요청한 작업을 수행 하는 Windows PowerShell 명령을 호출 합니다. CRUD 작업에서 기본 Windows PowerShell 명령 사이 매핑은 두 개의 스키마 파일과 schema.mof schema.xml에 의해 구현 됩니다. Schema.mof 파일이 사용 하 여 [Distributed Management Task Force](https://www.dmtf.org/) (DMTF) MOF (Managed Object) 표준입니다. Schema.xml 파일에 설명 된 XML 스키마를 사용 하 여 [리소스 매핑 스키마](./resource-mapping-schema.md)합니다.

> [!IMPORTANT]
> Windows Server 2008 R2 SP1 관리 ODATA IIS 확장을 사용 하기 전에 다음과 같은 기능을 활성화 되어야 합니다.
>
> 1.  IIS-WebServerRole
> 2.  IIS-웹 서버
> 3.  IIS-Http 추적
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>관리 OData 웹 서비스를 만들기 위한 단계

다음 항목에는 관리 OData 웹 서비스 만들기 및 배포 하는 방법을 설명 합니다.

- [관리 OData 웹 서비스에 리소스 추가](./adding-resources-to-a-management-odata-web-service.md)

- [관리 OData 웹 서비스에 대 한 사용자 지정 권한 부여를 구현합니다.](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [관리 OData 웹 서비스에 대 한 SessionConfiguration 구현](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [관리 OData 웹 서비스의 MOF 스키마 파일 작성](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [관리 OData 웹 서비스에 대 한 XML 스키마 파일 작성](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [관리 OData 웹 서비스에 대 한 Web.config 파일 작성](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [관리 OData 웹 서비스 배포](./deploying-a-management-odata-web-service.md)

- [관리 OData 엔터티를 연결합니다.](./associating-management-odata-entities.md)

## <a name="see-also"></a>참고 항목

[관리 ODATA IIS 확장 스키마 파일](./management-odata-iis-extension-schema-files.md)
