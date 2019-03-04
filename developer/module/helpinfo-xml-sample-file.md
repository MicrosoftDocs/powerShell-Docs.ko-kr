---
title: HelpInfo XML 파일 예제 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6544070f-5549-407f-8603-5df60fe9e013
caps.latest.revision: 7
ms.openlocfilehash: 11804db56ec47554e82f04fe6954920ad9577370
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856639"
---
# <a name="helpinfo-xml-sample-file"></a>HelpInfo XML 샘플 파일

이 항목에서는 일반적으로 "HelpInfo XML 파일입니다." 라고 잘못된 업데이트할 수 있는 도움말 정보 파일의 샘플이 표시 됩니다. 이 샘플 파일에서 ui 문화권 UI 문화권 이름별 사전순으로 정렬 됩니다. 모범 사례에는 알파벳 순서 있지만 필요 하지 않습니다.

## <a name="helpinfo-xml-sample-file"></a>HelpInfo XML 샘플 파일

```xml

<?xml version="1.0" encoding="utf-8"?>
<HelpInfo xmlns="http://schemas.microsoft.com/powershell/help/2010/05">
   <HelpContentURI>http://go.microsoft.com/fwlink/?LinkID=141553</HelpContentURI>
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