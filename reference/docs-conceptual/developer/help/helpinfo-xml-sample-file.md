---
ms.date: 09/12/2016
ms.topic: reference
title: HelpInfo XML 샘플 파일
description: HelpInfo XML 샘플 파일
ms.openlocfilehash: 321793d61ab5df3cccc7c353b6c93f5a7275b533
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647776"
---
# <a name="helpinfo-xml-sample-file"></a>HelpInfo XML 샘플 파일

이 항목에서는 일반적으로 "HelpInfo XML file" 이라고 하는 올바른 형식의 업데이트할 수 있는 도움말 정보 파일의 샘플을 보여 줍니다. 이 샘플 파일에서 UI 문화권 요소는 UI 문화권 이름에 따라 사전순으로 정렬 됩니다. 사전순으로 정렬 하는 것이 좋지만 필수는 아닙니다.

## <a name="helpinfo-xml-sample-file"></a>HelpInfo XML 샘플 파일

```xml

<?xml version="1.0" encoding="utf-8"?>
<HelpInfo xmlns="http://schemas.microsoft.com/powershell/help/2010/05">
   <HelpContentURI>https://go.microsoft.com/fwlink/?LinkID=141553</HelpContentURI>
   <SupportedUICultures>
    <UICulture>
      <UICultureName>de-DE</UICultureName>
      <UICultureVersion>2.15.0.10</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>en-US</UICultureName>
      <UICultureVersion>3.2.0.7</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>it-IT</UICultureName>
      <UICultureVersion>1.1.0.5</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>ja-JP</UICultureName>
      <UICultureVersion>3.2.0.4</UICultureVersion>
    </UICulture>
   </SupportedUICultures>
</HelpInfo>

```
