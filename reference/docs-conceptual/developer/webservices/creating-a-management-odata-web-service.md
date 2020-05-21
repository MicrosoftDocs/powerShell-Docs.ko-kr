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
ms.openlocfilehash: f903c99300a34c0dfbed598738e96142588d69d9
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83691476"
---
# <a name="creating-a-management-odata-web-service"></a>관리 OData 웹 서비스 만들기

관리 ODATA IIS 확장은 Windows PowerShell cmdlet 및 스크립트를 통해 액세스 하는 관리 데이터를 OData 웹 서비스 엔터티로 노출 하는 ASP.NET 웹 서비스 끝점을 만들기 위한 인프라입니다. OData 요청을 처리 하 고 Windows PowerShell 호출로 변환 하 여이 작업을 수행 합니다. 제품 팀은이 인프라를 기반으로 구축 하 여 특정 관리 데이터 집합을 노출 하는 끝점을 만들 수 있습니다.

[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) 샘플을 다운로드 하 여 설치 합니다. 지침에 따라 웹 서비스를 배포 합니다. 이 웹 서비스는 CRUD (만들기, 읽기, 업데이트 및 삭제) 작업을 통해 서비스 및 프로세스를 노출 합니다. 웹 서비스에 대 한 CRUD 요청은 요청 된 작업을 수행 하는 Windows PowerShell 명령을 호출 합니다. CRUD 작업과 기본 Windows PowerShell 명령 간의 매핑은 두 개의 스키마 파일인 schema. mof 및 schema .xml에 의해 구현 됩니다. 스키마 .mof 파일은 DMTF ( [Distributed Management Task Force](https://www.dmtf.org/) ) Mof (Managed Object) 표준을 사용 합니다. Schema .xml 파일은 [리소스 매핑 스키마](./resource-mapping-schema.md)에 설명 된 xml 스키마를 사용 합니다.

> [!IMPORTANT]
> Windows Server 2008 R2 s p 1에서 관리 ODATA IIS 확장을 사용 하도록 설정 하기 전에 다음 기능을 사용 하도록 설정 해야 합니다.
>
> 1. IIS-WebServerRole
> 2. IIS-웹 서버
> 3. IIS-Http 추적
> 4. IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>관리 OData 웹 서비스를 만드는 단계

다음 항목에서는 관리 OData 웹 서비스를 만들고 배포 하는 방법에 대해 설명 합니다.

- [관리 OData 웹 서비스에 리소스 추가](./adding-resources-to-a-management-odata-web-service.md)

- [관리 OData 웹 서비스에 대한 사용자 지정 권한 부여 구현](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [관리 OData 웹 서비스에 대한 SessionConfiguration 구현](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [관리 OData 웹 서비스용 MOF 스키마 파일 작성](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [관리 OData 웹 서비스용 XML 스키마 파일 작성](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [관리 OData 웹 서비스용 Web.config 파일 작성](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [관리 OData 웹 서비스 배포](./deploying-a-management-odata-web-service.md)

- [관리 OData 엔터티 연결](./associating-management-odata-entities.md)

## <a name="see-also"></a>참고 항목

[관리 ODATA IIS 확장 스키마 파일](./management-odata-iis-extension-schema-files.md)
