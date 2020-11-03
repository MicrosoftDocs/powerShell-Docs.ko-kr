---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: 90cb571f93243e6fbc59970e5602911e17e25ec7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213546"
---
# <span data-ttu-id="17990-103">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="17990-103">Disable-WSManTrace</span></span>

## <span data-ttu-id="17990-104">개요</span><span class="sxs-lookup"><span data-stu-id="17990-104">SYNOPSIS</span></span>
<span data-ttu-id="17990-105">-WSManTrace를 사용 하 여 시작한 WSMan 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="17990-105">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

## <span data-ttu-id="17990-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="17990-106">SYNTAX</span></span>

```
Disable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="17990-107">설명</span><span class="sxs-lookup"><span data-stu-id="17990-107">DESCRIPTION</span></span>
<span data-ttu-id="17990-108">이 cmdlet은-WSManTrace를 사용 하 여 시작한 WSMan 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="17990-108">This cmdlet stops the WSMan logging session started by Enable-WSManTrace.</span></span>

<span data-ttu-id="17990-109">이 cmdlet은 cmdlet을 사용 합니다 `Stop-Trace` .</span><span class="sxs-lookup"><span data-stu-id="17990-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="17990-110">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17990-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="17990-111">예제</span><span class="sxs-lookup"><span data-stu-id="17990-111">EXAMPLES</span></span>

### <span data-ttu-id="17990-112">예제 1: WSMan 추적 중지</span><span class="sxs-lookup"><span data-stu-id="17990-112">Example 1: Stop a WSMan trace</span></span>

```powershell
Disable-WSManTrace
```

## <span data-ttu-id="17990-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="17990-113">PARAMETERS</span></span>

### <span data-ttu-id="17990-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="17990-114">CommonParameters</span></span>

<span data-ttu-id="17990-115">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="17990-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="17990-116">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17990-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="17990-117">입력</span><span class="sxs-lookup"><span data-stu-id="17990-117">INPUTS</span></span>

### <span data-ttu-id="17990-118">없음</span><span class="sxs-lookup"><span data-stu-id="17990-118">None</span></span>

## <span data-ttu-id="17990-119">출력</span><span class="sxs-lookup"><span data-stu-id="17990-119">OUTPUTS</span></span>

### <span data-ttu-id="17990-120">System.Object</span><span class="sxs-lookup"><span data-stu-id="17990-120">System.Object</span></span>

## <span data-ttu-id="17990-121">참고</span><span class="sxs-lookup"><span data-stu-id="17990-121">NOTES</span></span>

## <span data-ttu-id="17990-122">관련 링크</span><span class="sxs-lookup"><span data-stu-id="17990-122">RELATED LINKS</span></span>

[<span data-ttu-id="17990-123">이벤트 추적</span><span class="sxs-lookup"><span data-stu-id="17990-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="17990-124">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="17990-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="17990-125">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="17990-125">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
