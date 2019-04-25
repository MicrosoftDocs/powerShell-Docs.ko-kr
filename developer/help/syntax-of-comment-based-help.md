---
title: 주석 기반 도움말 구문의 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083215"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="d2490-102">설명 기반 도움말 구문</span><span class="sxs-lookup"><span data-stu-id="d2490-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="d2490-103">이 섹션에 설명 기반 도움말의 구문을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d2490-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="d2490-104">구문 다이어그램</span><span class="sxs-lookup"><span data-stu-id="d2490-104">Syntax Diagram</span></span>

 <span data-ttu-id="d2490-105">주석 기반 도움말에 대 한 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d2490-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="d2490-106">구문 설명</span><span class="sxs-lookup"><span data-stu-id="d2490-106">Syntax Description</span></span>

 <span data-ttu-id="d2490-107">주석 기반 도움말은 일련의 주석으로 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2490-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="d2490-108">주석, 각 줄 앞에 주석 기호 (#)를 입력 하거나 사용할 수는 "\<#" 및 "#>" 기호를 주석 블록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2490-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="d2490-109">주석 블록 내에서 모든 줄을 주석으로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2490-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="d2490-110">각 섹션에 설명 기반 도움말 키워드 정의한 각 키워드는 점 (.) 뒤에</span><span class="sxs-lookup"><span data-stu-id="d2490-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="d2490-111">키워드는 임의의 순서로 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2490-111">The keywords can appear in any order.</span></span> <span data-ttu-id="d2490-112">키워드 이름은 대/소문자 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2490-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="d2490-113">주석 블록에는 도움말 키워드를 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2490-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="d2490-114">동일한 주석 블록에 여러 번 나타날 수 일부의 예제와 같은 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="d2490-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="d2490-115">각 키워드에 대 한 도움말 콘텐츠를 키워드 다음 줄에서 시작 하 고 여러 줄으로 나누어 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2490-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="d2490-116">주석 기반 도움말 항목의 줄을 모두 연속적 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2490-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="d2490-117">주석 기반 도움말 항목의 도움말 항목을 포함 되지 않은 주석 같이 마지막 아닌 도움말 주석 줄과 설명 기반 도움말의 시작 부분 사이의 빈 줄을 하나 이상 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2490-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="d2490-118">예를 들어, 다음 설명 기반 도움말 항목을 포함 합니다. 설명 키워드와 해당 값은 함수 또는 스크립트의 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="d2490-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```