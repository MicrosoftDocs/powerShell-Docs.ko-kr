---
title: 주석 기반 도움말 항목을 작성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e619ab16-90ad-46e9-9bde-d6dce492ba56
caps.latest.revision: 4
ms.openlocfilehash: e3d32f36b597088abc41e229bb0955c1b25504e6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083181"
---
# <a name="writing-comment-based-help-topics"></a><span data-ttu-id="57a01-102">설명 기반 도움말 항목 작성</span><span class="sxs-lookup"><span data-stu-id="57a01-102">Writing Comment-Based Help Topics</span></span>

<span data-ttu-id="57a01-103">특별 한 도움말 설명을 키워드를 사용 하 여 함수 및 스크립트에 대 한 설명 기반 도움말 항목을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a01-103">You can write comment-based Help topics for functions and scripts by using special Help comment keywords.</span></span>

 <span data-ttu-id="57a01-104">`Get-Help` cmdlet 설명 기반 도움말 XML 파일에서 생성 되는 cmdlet 도움말 항목을 표시 하는 동일한 형식으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a01-104">The `Get-Help` cmdlet displays comment-based Help in the same format in which it displays the cmdlet Help topics that are generated from XML files.</span></span> <span data-ttu-id="57a01-105">사용자의 매개 변수를 모두 사용할 수 있습니다 `Get-Help`자세히, 등 전체, 예제, 온라인, 함수를 표시 하 고 도움말을 스크립트에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a01-105">Users can use all of the parameters of `Get-Help`, such as Detailed, Full, Example, and Online, to display function and script Help.</span></span>

 <span data-ttu-id="57a01-106">스크립트 및 함수에 대 한 XML 기반 도움말 항목을 작성 하 고 도움말 주석 키워드를 사용 하 여 XML 기반 항목 또는 기타 항목에 사용자를 리디렉션할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a01-106">You can also write XML-based Help topics for scripts and functions and use the Help comment keywords to redirect users to the XML-based topics or other topics.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="57a01-107">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="57a01-107">In This Section</span></span>

 <span data-ttu-id="57a01-108">[주석 기반 도움말 구문의](./syntax-of-comment-based-help.md) 설명 기반 도움말의 구문을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a01-108">[Syntax of Comment-Based Help](./syntax-of-comment-based-help.md) Describes the syntax of comment-based help.</span></span>

 <span data-ttu-id="57a01-109">[주석 기반 도움말 키워드](./comment-based-help-keywords.md) 설명 기반 도움말 키워드를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a01-109">[Comment-Based Help Keywords](./comment-based-help-keywords.md) Lists the keywords in comment-based help.</span></span>

 <span data-ttu-id="57a01-110">[함수의 주석 기반 도움말을 배치](./placing-comment-based-help-in-functions.md) 함수에 대 한 설명 기반 도움말을 배치할 위치를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="57a01-110">[Placing Comment-Based Help in Functions](./placing-comment-based-help-in-functions.md) Shows where to place comment-based help for a function.</span></span>

 <span data-ttu-id="57a01-111">[스크립트에서 주석 기반 도움말을 배치](./placing-comment-based-help-in-scripts.md) 스크립트에 대 한 설명 기반 도움말을 배치할 위치를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="57a01-111">[Placing Comment-Based Help in Scripts](./placing-comment-based-help-in-scripts.md) Shows where to place comment-based help for a script.</span></span>