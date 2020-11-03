---
external help file: PSReadLine-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/psconsolehostreadline?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSConsoleHostReadLine
ms.openlocfilehash: 2dee8287558e9d5c001000fc5a57a859febee1a3
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93224729"
---
# <span data-ttu-id="ab3ba-103">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="ab3ba-103">PSConsoleHostReadLine</span></span>

## <span data-ttu-id="ab3ba-104">개요</span><span class="sxs-lookup"><span data-stu-id="ab3ba-104">SYNOPSIS</span></span>
<span data-ttu-id="ab3ba-105">이 함수는 PSReadLine의 주 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3ba-105">This function is the main entry point for PSReadLine.</span></span>

## <span data-ttu-id="ab3ba-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ab3ba-106">SYNTAX</span></span>

```
PSConsoleHostReadLine
```

## <span data-ttu-id="ab3ba-107">설명</span><span class="sxs-lookup"><span data-stu-id="ab3ba-107">DESCRIPTION</span></span>

<span data-ttu-id="ab3ba-108">`PSConsoleHostReadLine` 는 PSReadLine 모듈에 대 한 주 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3ba-108">`PSConsoleHostReadLine` is the main entry point for the PSReadLine module.</span></span> <span data-ttu-id="ab3ba-109">PowerShell 콘솔 호스트는 PSReadLine 모듈을 자동으로 로드 하 고이 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3ba-109">The PowerShell console host automatically loads the PSReadLine module and calls this function.</span></span> <span data-ttu-id="ab3ba-110">정상적인 운영 조건에서이 함수는 명령줄에서 사용 하기 위한 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="ab3ba-110">Under normal operating conditions, this function is not intended to be used from the command line.</span></span>

<span data-ttu-id="ab3ba-111">확장 지점은 `PSConsoleHostReadLine` 콘솔 호스트에서 특수 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3ba-111">The extension point `PSConsoleHostReadLine` is special to the console host.</span></span> <span data-ttu-id="ab3ba-112">호스트는이 이름을 사용 하 여 별칭, 함수 또는 스크립트를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3ba-112">The host calls any alias, function, or script with this name.</span></span> <span data-ttu-id="ab3ba-113">PSReadLine은 콘솔 호스트에서 호출 되도록이 함수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3ba-113">PSReadLine defines this function so that it is called from the console host.</span></span>

## <span data-ttu-id="ab3ba-114">예제</span><span class="sxs-lookup"><span data-stu-id="ab3ba-114">EXAMPLES</span></span>

### <span data-ttu-id="ab3ba-115">예 1</span><span class="sxs-lookup"><span data-stu-id="ab3ba-115">Example 1</span></span>

<span data-ttu-id="ab3ba-116">이 함수는 명령줄에서 사용 하기 위한 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="ab3ba-116">This function is not intended to be used from the command line.</span></span>

## <span data-ttu-id="ab3ba-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ab3ba-117">PARAMETERS</span></span>

## <span data-ttu-id="ab3ba-118">입력</span><span class="sxs-lookup"><span data-stu-id="ab3ba-118">INPUTS</span></span>

### <span data-ttu-id="ab3ba-119">없음</span><span class="sxs-lookup"><span data-stu-id="ab3ba-119">None</span></span>

## <span data-ttu-id="ab3ba-120">출력</span><span class="sxs-lookup"><span data-stu-id="ab3ba-120">OUTPUTS</span></span>

### <span data-ttu-id="ab3ba-121">없음</span><span class="sxs-lookup"><span data-stu-id="ab3ba-121">None</span></span>

## <span data-ttu-id="ab3ba-122">참고</span><span class="sxs-lookup"><span data-stu-id="ab3ba-122">NOTES</span></span>

## <span data-ttu-id="ab3ba-123">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ab3ba-123">RELATED LINKS</span></span>

[<span data-ttu-id="ab3ba-124">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="ab3ba-124">about_PSReadLine</span></span>](./About/about_PSReadLine.md)
