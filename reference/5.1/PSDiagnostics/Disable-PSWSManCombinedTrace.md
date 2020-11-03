---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pswsmancombinedtrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSWSManCombinedTrace
ms.openlocfilehash: 4a98941de072b9b57b89a25bc180c0ee391d8b63
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213561"
---
# <span data-ttu-id="cbe9f-103">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="cbe9f-103">Disable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="cbe9f-104">개요</span><span class="sxs-lookup"><span data-stu-id="cbe9f-104">SYNOPSIS</span></span>
<span data-ttu-id="cbe9f-105">PSWSManCombinedTrace를 사용 하 여 시작 된 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbe9f-105">Stop the logging session started by Enable-PSWSManCombinedTrace.</span></span>

## <span data-ttu-id="cbe9f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cbe9f-106">SYNTAX</span></span>

```
Disable-PSWSManCombinedTrace [<CommonParameters>]
```

## <span data-ttu-id="cbe9f-107">설명</span><span class="sxs-lookup"><span data-stu-id="cbe9f-107">DESCRIPTION</span></span>

<span data-ttu-id="cbe9f-108">이 cmdlet은에 의해 시작 된 로깅 세션을 중지 `Enable-PSWSManCombinedTrace` 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbe9f-108">This cmdlet stops the logging session started by `Enable-PSWSManCombinedTrace`.</span></span>

<span data-ttu-id="cbe9f-109">이 cmdlet은 cmdlet을 사용 합니다 `Stop-Trace` .</span><span class="sxs-lookup"><span data-stu-id="cbe9f-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="cbe9f-110">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbe9f-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="cbe9f-111">예제</span><span class="sxs-lookup"><span data-stu-id="cbe9f-111">EXAMPLES</span></span>

### <span data-ttu-id="cbe9f-112">예제 1: 결합 된 로깅 세션 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="cbe9f-112">Example 1: Disable the combined logging session</span></span>

```powershell
Disable-PSWSManCombinedTrace
```

## <span data-ttu-id="cbe9f-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cbe9f-113">PARAMETERS</span></span>

### <span data-ttu-id="cbe9f-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cbe9f-114">CommonParameters</span></span>

<span data-ttu-id="cbe9f-115">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cbe9f-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cbe9f-116">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cbe9f-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cbe9f-117">입력</span><span class="sxs-lookup"><span data-stu-id="cbe9f-117">INPUTS</span></span>

### <span data-ttu-id="cbe9f-118">없음</span><span class="sxs-lookup"><span data-stu-id="cbe9f-118">None</span></span>

## <span data-ttu-id="cbe9f-119">출력</span><span class="sxs-lookup"><span data-stu-id="cbe9f-119">OUTPUTS</span></span>

### <span data-ttu-id="cbe9f-120">System.Object</span><span class="sxs-lookup"><span data-stu-id="cbe9f-120">System.Object</span></span>

## <span data-ttu-id="cbe9f-121">참고</span><span class="sxs-lookup"><span data-stu-id="cbe9f-121">NOTES</span></span>

## <span data-ttu-id="cbe9f-122">관련 링크</span><span class="sxs-lookup"><span data-stu-id="cbe9f-122">RELATED LINKS</span></span>

[<span data-ttu-id="cbe9f-123">이벤트 추적</span><span class="sxs-lookup"><span data-stu-id="cbe9f-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="cbe9f-124">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="cbe9f-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="cbe9f-125">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="cbe9f-125">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)
