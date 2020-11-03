---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: f7ec371e0d9826dc095fbf71c4785cae2856875b
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209072"
---
# <span data-ttu-id="7f893-103">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="7f893-103">Disable-WSManTrace</span></span>

## <span data-ttu-id="7f893-104">개요</span><span class="sxs-lookup"><span data-stu-id="7f893-104">SYNOPSIS</span></span>
<span data-ttu-id="7f893-105">-WSManTrace를 사용 하 여 시작한 WSMan 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f893-105">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

## <span data-ttu-id="7f893-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7f893-106">SYNTAX</span></span>

```
Disable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="7f893-107">설명</span><span class="sxs-lookup"><span data-stu-id="7f893-107">DESCRIPTION</span></span>
<span data-ttu-id="7f893-108">이 cmdlet은-WSManTrace를 사용 하 여 시작한 WSMan 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f893-108">This cmdlet stops the WSMan logging session started by Enable-WSManTrace.</span></span>

<span data-ttu-id="7f893-109">이 cmdlet은 cmdlet을 사용 합니다 `Stop-Trace` .</span><span class="sxs-lookup"><span data-stu-id="7f893-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="7f893-110">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f893-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="7f893-111">예제</span><span class="sxs-lookup"><span data-stu-id="7f893-111">EXAMPLES</span></span>

### <span data-ttu-id="7f893-112">예제 1: WSMan 추적 중지</span><span class="sxs-lookup"><span data-stu-id="7f893-112">Example 1: Stop a WSMan trace</span></span>

```powershell
Disable-WSManTrace
```

## <span data-ttu-id="7f893-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7f893-113">PARAMETERS</span></span>

### <span data-ttu-id="7f893-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7f893-114">CommonParameters</span></span>

<span data-ttu-id="7f893-115">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7f893-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7f893-116">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f893-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7f893-117">입력</span><span class="sxs-lookup"><span data-stu-id="7f893-117">INPUTS</span></span>

### <span data-ttu-id="7f893-118">없음</span><span class="sxs-lookup"><span data-stu-id="7f893-118">None</span></span>

## <span data-ttu-id="7f893-119">출력</span><span class="sxs-lookup"><span data-stu-id="7f893-119">OUTPUTS</span></span>

### <span data-ttu-id="7f893-120">없음</span><span class="sxs-lookup"><span data-stu-id="7f893-120">None</span></span>

## <span data-ttu-id="7f893-121">참고</span><span class="sxs-lookup"><span data-stu-id="7f893-121">NOTES</span></span>

## <span data-ttu-id="7f893-122">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7f893-122">RELATED LINKS</span></span>

[<span data-ttu-id="7f893-123">이벤트 추적</span><span class="sxs-lookup"><span data-stu-id="7f893-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="7f893-124">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="7f893-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="7f893-125">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="7f893-125">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
