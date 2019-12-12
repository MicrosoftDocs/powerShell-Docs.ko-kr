---
title: 주석 기반 도움말 항목 작성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e619ab16-90ad-46e9-9bde-d6dce492ba56
caps.latest.revision: 4
ms.openlocfilehash: e3d32f36b597088abc41e229bb0955c1b25504e6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361082"
---
# <a name="writing-comment-based-help-topics"></a><span data-ttu-id="d493b-102">설명 기반 도움말 항목 작성</span><span class="sxs-lookup"><span data-stu-id="d493b-102">Writing Comment-Based Help Topics</span></span>

<span data-ttu-id="d493b-103">특수 도움말 주석 키워드를 사용 하 여 함수 및 스크립트에 대 한 주석 기반 도움말 항목을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d493b-103">You can write comment-based Help topics for functions and scripts by using special Help comment keywords.</span></span>

 <span data-ttu-id="d493b-104">`Get-Help` cmdlet은 XML 파일에서 생성 된 cmdlet 도움말 항목을 표시 하는 것과 같은 형식으로 주석 기반 도움말을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d493b-104">The `Get-Help` cmdlet displays comment-based Help in the same format in which it displays the cmdlet Help topics that are generated from XML files.</span></span> <span data-ttu-id="d493b-105">사용자는 Detailed, Full, Example 및 Online과 같은 `Get-Help`의 모든 매개 변수를 사용 하 여 함수 및 스크립트 도움말을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d493b-105">Users can use all of the parameters of `Get-Help`, such as Detailed, Full, Example, and Online, to display function and script Help.</span></span>

 <span data-ttu-id="d493b-106">스크립트 및 함수에 대 한 XML 기반 도움말 항목을 작성 하 고 도움말 주석 키워드를 사용 하 여 사용자를 XML 기반 항목 또는 기타 항목으로 리디렉션할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d493b-106">You can also write XML-based Help topics for scripts and functions and use the Help comment keywords to redirect users to the XML-based topics or other topics.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d493b-107">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="d493b-107">In This Section</span></span>

 <span data-ttu-id="d493b-108">[주석 기반 도움말의 구문](./syntax-of-comment-based-help.md) 주석 기반 도움말의 구문에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d493b-108">[Syntax of Comment-Based Help](./syntax-of-comment-based-help.md) Describes the syntax of comment-based help.</span></span>

 <span data-ttu-id="d493b-109">[주석 기반 도움말 키워드](./comment-based-help-keywords.md) 주석 기반 도움말의 키워드를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="d493b-109">[Comment-Based Help Keywords](./comment-based-help-keywords.md) Lists the keywords in comment-based help.</span></span>

 <span data-ttu-id="d493b-110">[함수에 주석 기반 도움말 배치](./placing-comment-based-help-in-functions.md) 함수에 대 한 주석 기반 도움말을 넣을 위치를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d493b-110">[Placing Comment-Based Help in Functions](./placing-comment-based-help-in-functions.md) Shows where to place comment-based help for a function.</span></span>

 <span data-ttu-id="d493b-111">[스크립트에 주석 기반 도움말 배치](./placing-comment-based-help-in-scripts.md) 스크립트에 대 한 주석 기반 도움말을 넣을 위치를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d493b-111">[Placing Comment-Based Help in Scripts](./placing-comment-based-help-in-scripts.md) Shows where to place comment-based help for a script.</span></span>