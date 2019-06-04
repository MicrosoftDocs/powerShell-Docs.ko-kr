---
title: HelpInfo XML 스키마 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 0f965f4ee1ef92a6a538b52b4348c04366cabf66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082467"
---
# <a name="helpinfo-xml-schema"></a>HelpInfo XML 스키마

이 항목에서는 일반적으로 "HelpInfo XML 파일입니다." 라고 하 고 업데이트할 수 있는 도움말 정보 파일에 대 한 XML 스키마를 포함 합니다.

## <a name="helpinfo-xml-schema"></a>HelpInfo XML 스키마

HelpInfo XML 파일은 다음 XML 스키마를 기반으로 합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="http://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
  <element name="HelpInfo">
    <complexType>
      <sequence>
        <element name="HelpContentURI" type="anyURI" minOccurs="1" maxOccurs="1" />
        <element name="SupportedUICultures" minOccurs="1" maxOccurs="1">
          <complexType>
            <sequence>
              <element name="UICulture" minOccurs="1" maxOccurs="unbounded">
                <complexType>
                  <sequence>
                    <element name="UICultureName" type="language" minOccurs="1" maxOccurs="1" />
                    <element name="UICultureVersion" type="string" minOccurs="1" maxOccurs="1" />
                  </sequence>
                </complexType>
              </element>
            </sequence>
          </complexType>
        </element>
      </sequence>
    </complexType>
  </element>
</schema>
```

## <a name="helpinfo-xml-elements"></a>HelpInfo XML 요소

HelpInfo XML 파일에는 다음 요소가 포함 됩니다.

HelpContentURI는 도움말 모듈에 대 한 CAB 파일의 위치 URI를 포함 합니다. URI는 "http" 또는 "https"로 시작 해야 합니다. URI는 인터넷 위치를 지정 해야 하지만 CAB 파일 이름을 포함 하지 않아야 합니다. **HelpContentURI** 값 수 동일 또는 다른 합니다 **HelpInfoURI** 값입니다.

SupportedUICultures 모든 UI 문화권의 모듈 도움말 파일을 나타냅니다. 포함 **UICulture** 요소를 각각 나타내는 지정된 된 UI 문화권의 모듈에 대 한 도움말 파일의 집합입니다.

UICulture 지정된 된 UI 문화권의 모듈에 대 한 도움말 파일의 집합을 나타냅니다. 추가 된 **UICulture** 도움말 파일이 작성 되는 각 UI 문화권에 대 한 요소입니다.

UICultureName 도움말 파일이 작성 되는 UI 문화권에 대 한 언어 코드를 포함 합니다.

UICultureVersion "N1의 4 부 버전 번호를 포함합니다. N2입니다. N3 합니다. N4 "UI 문화권의 도움말 CAB 파일의 버전을 나타내는 형식입니다. 새 도움말에 지정 된 UI 문화권의 CAB 파일을 업로드할 때마다 버전 번호를 하나씩 늘립니다 **UICultureName**합니다. 이 값에 대 한 자세한 내용은 "버전 (시스템) MSDN에서" 클래스를 참조 하세요.