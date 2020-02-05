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
ms.openlocfilehash: 8142a620f0f71de3d2a6b33fc2e45092b5743a54
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995996"
---
# <a name="helpinfo-xml-schema"></a>HelpInfo XML 스키마

이 항목에는 업데이트할 수 있는 도움말 정보 파일에 대 한 XML 스키마가 포함 되어 있습니다 (일반적으로 "HelpInfo XML 파일" 이라고 함).

## <a name="helpinfo-xml-schema"></a>HelpInfo XML 스키마

HelpInfo XML 파일은 다음 XML 스키마를 기반으로 합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="https://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
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

HelpInfo XML 파일에는 다음 요소가 포함 되어 있습니다.

HelpContentURI에는 모듈에 대 한 도움말 CAB 파일 위치의 URI가 포함 됩니다. URI는 "http" 또는 "https"로 시작 해야 합니다. URI는 인터넷 위치를 지정 해야 하지만 CAB 파일 이름을 포함 하지 않아야 합니다. **Helpcontenturi** 값은 **HelpInfoURI** 값과 같거나 다를 수 있습니다.

SupportedUICultures는 모든 UI 문화권의 모듈 도움말 파일을 나타냅니다. 각각 지정 된 UI 문화권의 모듈에 대 한 도움말 파일 집합을 나타내는 **UICulture** 요소를 포함 합니다.

UICulture는 지정 된 UI 문화권의 모듈에 대 한 도움말 파일 집합을 나타냅니다. 도움말 파일이 작성 되는 각 UI 문화권에 대 한 **UICulture** 요소를 추가 합니다.

UICultureName에는 도움말 파일이 작성 되는 UI 문화권에 대 한 언어 코드가 포함 되어 있습니다.

UICultureVersion에는 "N1. N2. N3. N4 "UI 문화권에서 도움말 CAB 파일의 버전을 나타내는 형식입니다. **UICultureName**로 지정 된 UI 문화권에 새 도움말 CAB 파일을 업로드할 때마다이 버전 번호를 늘립니다. 이 값에 대 한 자세한 내용은 MSDN의 "버전 클래스 (시스템)"를 참조 하십시오.