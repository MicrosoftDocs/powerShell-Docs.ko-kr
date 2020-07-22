---
title: HelpInfo XML 샘플 파일
ms.date: 09/12/2016
ms.openlocfilehash: ccd1f61d8d40232a3e6d2228d382ef4895e13d3d
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893512"
---
# <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="8d1a3-102">HelpInfo XML 샘플 파일</span><span class="sxs-lookup"><span data-stu-id="8d1a3-102">HelpInfo XML Sample File</span></span>

<span data-ttu-id="8d1a3-103">이 항목에서는 일반적으로 "HelpInfo XML file" 이라고 하는 올바른 형식의 업데이트할 수 있는 도움말 정보 파일의 샘플을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8d1a3-103">This topic displays a sample of a well-formed Updatable Help Information file, commonly known as "HelpInfo XML file."</span></span> <span data-ttu-id="8d1a3-104">이 샘플 파일에서 UI 문화권 요소는 UI 문화권 이름에 따라 사전순으로 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d1a3-104">In this sample file, the UI culture elements are arranged in alphabetical order by UI culture name.</span></span> <span data-ttu-id="8d1a3-105">사전순으로 정렬 하는 것이 좋지만 필수는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="8d1a3-105">Alphabetical ordering is a best practice, but it is not required.</span></span>

## <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="8d1a3-106">HelpInfo XML 샘플 파일</span><span class="sxs-lookup"><span data-stu-id="8d1a3-106">HelpInfo XML Sample File</span></span>

```xml

<?xml version="1.0" encoding="utf-8"?>
<HelpInfo xmlns="https://schemas.microsoft.com/powershell/help/2010/05">
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
