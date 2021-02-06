---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: 647a7676eddf2175bf29e02b3482cc9c7c4d8ebe
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602052"
---
# <span data-ttu-id="d22ff-102">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="d22ff-102">Disable-WSManTrace</span></span>

## <span data-ttu-id="d22ff-103">개요</span><span class="sxs-lookup"><span data-stu-id="d22ff-103">SYNOPSIS</span></span>
<span data-ttu-id="d22ff-104">-WSManTrace를 사용 하 여 시작한 WSMan 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d22ff-104">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

## <span data-ttu-id="d22ff-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d22ff-105">SYNTAX</span></span>

```
Disable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="d22ff-106">설명</span><span class="sxs-lookup"><span data-stu-id="d22ff-106">DESCRIPTION</span></span>
<span data-ttu-id="d22ff-107">이 cmdlet은-WSManTrace를 사용 하 여 시작한 WSMan 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d22ff-107">This cmdlet stops the WSMan logging session started by Enable-WSManTrace.</span></span>

<span data-ttu-id="d22ff-108">이 cmdlet은 cmdlet을 사용 합니다 `Stop-Trace` .</span><span class="sxs-lookup"><span data-stu-id="d22ff-108">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="d22ff-109">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d22ff-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="d22ff-110">예제</span><span class="sxs-lookup"><span data-stu-id="d22ff-110">EXAMPLES</span></span>

### <span data-ttu-id="d22ff-111">예제 1: WSMan 추적 중지</span><span class="sxs-lookup"><span data-stu-id="d22ff-111">Example 1: Stop a WSMan trace</span></span>

```powershell
Disable-WSManTrace
```

## <span data-ttu-id="d22ff-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d22ff-112">PARAMETERS</span></span>

### <span data-ttu-id="d22ff-113">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d22ff-113">CommonParameters</span></span>

<span data-ttu-id="d22ff-114">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d22ff-114">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d22ff-115">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d22ff-115">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d22ff-116">입력</span><span class="sxs-lookup"><span data-stu-id="d22ff-116">INPUTS</span></span>

### <span data-ttu-id="d22ff-117">없음</span><span class="sxs-lookup"><span data-stu-id="d22ff-117">None</span></span>

## <span data-ttu-id="d22ff-118">출력</span><span class="sxs-lookup"><span data-stu-id="d22ff-118">OUTPUTS</span></span>

### <span data-ttu-id="d22ff-119">없음</span><span class="sxs-lookup"><span data-stu-id="d22ff-119">None</span></span>

## <span data-ttu-id="d22ff-120">참고</span><span class="sxs-lookup"><span data-stu-id="d22ff-120">NOTES</span></span>

## <span data-ttu-id="d22ff-121">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d22ff-121">RELATED LINKS</span></span>

[<span data-ttu-id="d22ff-122">이벤트 추적</span><span class="sxs-lookup"><span data-stu-id="d22ff-122">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="d22ff-123">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="d22ff-123">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="d22ff-124">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="d22ff-124">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)

