---
title: 주석 기반 도움말 구문 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367762"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="c9081-102">설명 기반 도움말 구문</span><span class="sxs-lookup"><span data-stu-id="c9081-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="c9081-103">이 섹션에서는 주석 기반 도움말의 구문에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9081-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="c9081-104">구문 다이어그램</span><span class="sxs-lookup"><span data-stu-id="c9081-104">Syntax Diagram</span></span>

 <span data-ttu-id="c9081-105">주석 기반 도움말의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c9081-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="c9081-106">구문 설명</span><span class="sxs-lookup"><span data-stu-id="c9081-106">Syntax Description</span></span>

 <span data-ttu-id="c9081-107">주석 기반 도움말은 일련의 주석으로 작성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9081-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="c9081-108">주석의 각 줄 앞에 주석 기호 (#)를 입력 하거나 "\< #" 및 "# >" 기호를 사용 하 여 주석 블록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9081-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="c9081-109">주석 블록 내의 모든 줄은 주석으로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9081-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="c9081-110">주석 기반 도움말의 각 섹션은 키워드로 정의 되며 각 키워드 앞에 점 (.)이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9081-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="c9081-111">키워드는 순서에 관계 없이 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9081-111">The keywords can appear in any order.</span></span> <span data-ttu-id="c9081-112">키워드 이름은 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9081-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="c9081-113">주석 블록은 하나 이상의 도움말 키워드를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9081-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="c9081-114">예제와 같은 일부 키워드는 동일한 주석 블록에 여러 번 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9081-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="c9081-115">각 키워드에 대 한 도움말 콘텐츠는 키워드 뒤의 줄에서 시작 하 여 여러 줄에 걸쳐 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9081-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="c9081-116">주석 기반 도움말 항목의 모든 줄은 연속적 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9081-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="c9081-117">주석 기반 도움말 항목이 도움말 항목에 포함 되지 않은 주석을 따르는 경우에는 마지막으로 지원 되지 않는 주석 줄과 주석 기반 도움말의 시작 부분 사이에 하나 이상의 빈 줄이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9081-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="c9081-118">예를 들어 다음 주석 기반 도움말 항목에는가 포함 되어 있습니다. 함수 또는 스크립트에 대 한 설명 인 description 키워드와 해당 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c9081-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```