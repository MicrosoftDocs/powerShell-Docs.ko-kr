---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: 70ce4849e78262fc3553502d307e1df4e9ecfcf3
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209075"
---
# <span data-ttu-id="f6c1a-103">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="f6c1a-103">Enable-WSManTrace</span></span>

## <span data-ttu-id="f6c1a-104">개요</span><span class="sxs-lookup"><span data-stu-id="f6c1a-104">SYNOPSIS</span></span>
<span data-ttu-id="f6c1a-105">WSMan 공급자가 사용 하도록 설정 된 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6c1a-105">Start a logging session with the WSMan providers enabled.</span></span>

## <span data-ttu-id="f6c1a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f6c1a-106">SYNTAX</span></span>

```
Enable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="f6c1a-107">설명</span><span class="sxs-lookup"><span data-stu-id="f6c1a-107">DESCRIPTION</span></span>
<span data-ttu-id="f6c1a-108">이 cmdlet은 WSMan 공급자가 사용 하도록 설정 된 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6c1a-108">This cmdlet starts a logging session with the WSMan providers enabled.</span></span> <span data-ttu-id="f6c1a-109">다음 이벤트 공급자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6c1a-109">The following event providers are enabled:</span></span>

- <span data-ttu-id="f6c1a-110">이벤트 전달</span><span class="sxs-lookup"><span data-stu-id="f6c1a-110">Event Forwarding</span></span>
- <span data-ttu-id="f6c1a-111">IpmiDrv</span><span class="sxs-lookup"><span data-stu-id="f6c1a-111">IpmiDrv</span></span>
- <span data-ttu-id="f6c1a-112">IPMIPrv</span><span class="sxs-lookup"><span data-stu-id="f6c1a-112">IPMIPrv</span></span>
- <span data-ttu-id="f6c1a-113">WinRM</span><span class="sxs-lookup"><span data-stu-id="f6c1a-113">WinRM</span></span>
- <span data-ttu-id="f6c1a-114">WinrsCmd</span><span class="sxs-lookup"><span data-stu-id="f6c1a-114">WinrsCmd</span></span>
- <span data-ttu-id="f6c1a-115">WinrsExe</span><span class="sxs-lookup"><span data-stu-id="f6c1a-115">WinrsExe</span></span>
- <span data-ttu-id="f6c1a-116">WinrsMgr</span><span class="sxs-lookup"><span data-stu-id="f6c1a-116">WinrsMgr</span></span>
- <span data-ttu-id="f6c1a-117">WSManProvHost</span><span class="sxs-lookup"><span data-stu-id="f6c1a-117">WSManProvHost</span></span>

<span data-ttu-id="f6c1a-118">세션의 이름은 ' wsmlog '입니다.</span><span class="sxs-lookup"><span data-stu-id="f6c1a-118">The session is named 'wsmlog'.</span></span>

<span data-ttu-id="f6c1a-119">이 cmdlet은 cmdlet을 사용 합니다 `Start-Trace` .</span><span class="sxs-lookup"><span data-stu-id="f6c1a-119">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="f6c1a-120">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6c1a-120">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="f6c1a-121">예제</span><span class="sxs-lookup"><span data-stu-id="f6c1a-121">EXAMPLES</span></span>

### <span data-ttu-id="f6c1a-122">예 1: WSMan 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6c1a-122">Example 1: Start a WSMan logging session.</span></span>

```powershell
Enable-WSManTrace
```

## <span data-ttu-id="f6c1a-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f6c1a-123">PARAMETERS</span></span>

### <span data-ttu-id="f6c1a-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f6c1a-124">CommonParameters</span></span>

<span data-ttu-id="f6c1a-125">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f6c1a-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f6c1a-126">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6c1a-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f6c1a-127">입력</span><span class="sxs-lookup"><span data-stu-id="f6c1a-127">INPUTS</span></span>

### <span data-ttu-id="f6c1a-128">없음</span><span class="sxs-lookup"><span data-stu-id="f6c1a-128">None</span></span>

## <span data-ttu-id="f6c1a-129">출력</span><span class="sxs-lookup"><span data-stu-id="f6c1a-129">OUTPUTS</span></span>

### <span data-ttu-id="f6c1a-130">없음</span><span class="sxs-lookup"><span data-stu-id="f6c1a-130">None</span></span>

## <span data-ttu-id="f6c1a-131">참고</span><span class="sxs-lookup"><span data-stu-id="f6c1a-131">NOTES</span></span>

## <span data-ttu-id="f6c1a-132">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f6c1a-132">RELATED LINKS</span></span>

[<span data-ttu-id="f6c1a-133">이벤트 추적</span><span class="sxs-lookup"><span data-stu-id="f6c1a-133">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="f6c1a-134">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="f6c1a-134">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="f6c1a-135">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="f6c1a-135">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)
