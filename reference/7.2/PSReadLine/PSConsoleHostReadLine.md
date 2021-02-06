---
external help file: PSReadLine-help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/psconsolehostreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSConsoleHostReadLine
ms.openlocfilehash: e02f06137395e187cfe86eb1aeb4b30dbb3f09f1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605483"
---
# <span data-ttu-id="0a36a-102">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="0a36a-102">PSConsoleHostReadLine</span></span>

## <span data-ttu-id="0a36a-103">개요</span><span class="sxs-lookup"><span data-stu-id="0a36a-103">SYNOPSIS</span></span>
<span data-ttu-id="0a36a-104">이 함수는 PSReadLine의 주 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="0a36a-104">This function is the main entry point for PSReadLine.</span></span>

## <span data-ttu-id="0a36a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0a36a-105">SYNTAX</span></span>

```
PSConsoleHostReadLine
```

## <span data-ttu-id="0a36a-106">설명</span><span class="sxs-lookup"><span data-stu-id="0a36a-106">DESCRIPTION</span></span>

<span data-ttu-id="0a36a-107">`PSConsoleHostReadLine` 는 PSReadLine 모듈에 대 한 주 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="0a36a-107">`PSConsoleHostReadLine` is the main entry point for the PSReadLine module.</span></span> <span data-ttu-id="0a36a-108">PowerShell 콘솔 호스트는 PSReadLine 모듈을 자동으로 로드 하 고이 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a36a-108">The PowerShell console host automatically loads the PSReadLine module and calls this function.</span></span> <span data-ttu-id="0a36a-109">정상적인 운영 조건에서이 함수는 명령줄에서 사용 하기 위한 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0a36a-109">Under normal operating conditions, this function is not intended to be used from the command line.</span></span>

<span data-ttu-id="0a36a-110">확장 지점은 `PSConsoleHostReadLine` 콘솔 호스트에서 특수 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a36a-110">The extension point `PSConsoleHostReadLine` is special to the console host.</span></span> <span data-ttu-id="0a36a-111">호스트는이 이름을 사용 하 여 별칭, 함수 또는 스크립트를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a36a-111">The host calls any alias, function, or script with this name.</span></span> <span data-ttu-id="0a36a-112">PSReadLine은 콘솔 호스트에서 호출 되도록이 함수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a36a-112">PSReadLine defines this function so that it is called from the console host.</span></span>

## <span data-ttu-id="0a36a-113">예제</span><span class="sxs-lookup"><span data-stu-id="0a36a-113">EXAMPLES</span></span>

### <span data-ttu-id="0a36a-114">예제 1</span><span class="sxs-lookup"><span data-stu-id="0a36a-114">Example 1</span></span>

<span data-ttu-id="0a36a-115">이 함수는 명령줄에서 사용 하기 위한 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0a36a-115">This function is not intended to be used from the command line.</span></span>

## <span data-ttu-id="0a36a-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0a36a-116">PARAMETERS</span></span>

## <span data-ttu-id="0a36a-117">입력</span><span class="sxs-lookup"><span data-stu-id="0a36a-117">INPUTS</span></span>

### <span data-ttu-id="0a36a-118">없음</span><span class="sxs-lookup"><span data-stu-id="0a36a-118">None</span></span>

## <span data-ttu-id="0a36a-119">출력</span><span class="sxs-lookup"><span data-stu-id="0a36a-119">OUTPUTS</span></span>

### <span data-ttu-id="0a36a-120">없음</span><span class="sxs-lookup"><span data-stu-id="0a36a-120">None</span></span>

## <span data-ttu-id="0a36a-121">참고</span><span class="sxs-lookup"><span data-stu-id="0a36a-121">NOTES</span></span>

## <span data-ttu-id="0a36a-122">관련 링크</span><span class="sxs-lookup"><span data-stu-id="0a36a-122">RELATED LINKS</span></span>

[<span data-ttu-id="0a36a-123">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="0a36a-123">about_PSReadLine</span></span>](./About/about_PSReadLine.md)

