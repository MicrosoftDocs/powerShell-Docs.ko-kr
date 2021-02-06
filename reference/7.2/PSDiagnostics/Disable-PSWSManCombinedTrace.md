---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pswsmancombinedtrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSWSManCombinedTrace
ms.openlocfilehash: 690a8b050fd0e16033a585df210db340f41a83a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600820"
---
# <span data-ttu-id="1e008-102">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="1e008-102">Disable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="1e008-103">개요</span><span class="sxs-lookup"><span data-stu-id="1e008-103">SYNOPSIS</span></span>
<span data-ttu-id="1e008-104">PSWSManCombinedTrace를 사용 하 여 시작 된 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e008-104">Stop the logging session started by Enable-PSWSManCombinedTrace.</span></span>

## <span data-ttu-id="1e008-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1e008-105">SYNTAX</span></span>

```
Disable-PSWSManCombinedTrace [<CommonParameters>]
```

## <span data-ttu-id="1e008-106">설명</span><span class="sxs-lookup"><span data-stu-id="1e008-106">DESCRIPTION</span></span>

<span data-ttu-id="1e008-107">이 cmdlet은에 의해 시작 된 로깅 세션을 중지 `Enable-PSWSManCombinedTrace` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e008-107">This cmdlet stops the logging session started by `Enable-PSWSManCombinedTrace`.</span></span>

<span data-ttu-id="1e008-108">이 cmdlet은 cmdlet을 사용 합니다 `Stop-Trace` .</span><span class="sxs-lookup"><span data-stu-id="1e008-108">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="1e008-109">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e008-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="1e008-110">예제</span><span class="sxs-lookup"><span data-stu-id="1e008-110">EXAMPLES</span></span>

### <span data-ttu-id="1e008-111">예제 1: 결합 된 로깅 세션 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="1e008-111">Example 1: Disable the combined logging session</span></span>

```powershell
Disable-PSWSManCombinedTrace
```

## <span data-ttu-id="1e008-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1e008-112">PARAMETERS</span></span>

### <span data-ttu-id="1e008-113">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1e008-113">CommonParameters</span></span>

<span data-ttu-id="1e008-114">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1e008-114">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1e008-115">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e008-115">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1e008-116">입력</span><span class="sxs-lookup"><span data-stu-id="1e008-116">INPUTS</span></span>

### <span data-ttu-id="1e008-117">없음</span><span class="sxs-lookup"><span data-stu-id="1e008-117">None</span></span>

## <span data-ttu-id="1e008-118">출력</span><span class="sxs-lookup"><span data-stu-id="1e008-118">OUTPUTS</span></span>

### <span data-ttu-id="1e008-119">없음</span><span class="sxs-lookup"><span data-stu-id="1e008-119">None</span></span>

## <span data-ttu-id="1e008-120">참고</span><span class="sxs-lookup"><span data-stu-id="1e008-120">NOTES</span></span>

## <span data-ttu-id="1e008-121">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1e008-121">RELATED LINKS</span></span>

[<span data-ttu-id="1e008-122">이벤트 추적</span><span class="sxs-lookup"><span data-stu-id="1e008-122">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="1e008-123">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="1e008-123">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="1e008-124">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="1e008-124">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

