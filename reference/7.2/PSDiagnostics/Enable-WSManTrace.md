---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: a9d91eab94666186c13f8d5c928d83055f6dbefa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605487"
---
# <span data-ttu-id="c2c34-102">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="c2c34-102">Enable-WSManTrace</span></span>

## <span data-ttu-id="c2c34-103">개요</span><span class="sxs-lookup"><span data-stu-id="c2c34-103">SYNOPSIS</span></span>
<span data-ttu-id="c2c34-104">WSMan 공급자가 사용 하도록 설정 된 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c34-104">Start a logging session with the WSMan providers enabled.</span></span>

## <span data-ttu-id="c2c34-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c2c34-105">SYNTAX</span></span>

```
Enable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="c2c34-106">설명</span><span class="sxs-lookup"><span data-stu-id="c2c34-106">DESCRIPTION</span></span>
<span data-ttu-id="c2c34-107">이 cmdlet은 WSMan 공급자가 사용 하도록 설정 된 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c34-107">This cmdlet starts a logging session with the WSMan providers enabled.</span></span> <span data-ttu-id="c2c34-108">다음 이벤트 공급자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c34-108">The following event providers are enabled:</span></span>

- <span data-ttu-id="c2c34-109">이벤트 전달</span><span class="sxs-lookup"><span data-stu-id="c2c34-109">Event Forwarding</span></span>
- <span data-ttu-id="c2c34-110">IpmiDrv</span><span class="sxs-lookup"><span data-stu-id="c2c34-110">IpmiDrv</span></span>
- <span data-ttu-id="c2c34-111">IPMIPrv</span><span class="sxs-lookup"><span data-stu-id="c2c34-111">IPMIPrv</span></span>
- <span data-ttu-id="c2c34-112">WinRM</span><span class="sxs-lookup"><span data-stu-id="c2c34-112">WinRM</span></span>
- <span data-ttu-id="c2c34-113">WinrsCmd</span><span class="sxs-lookup"><span data-stu-id="c2c34-113">WinrsCmd</span></span>
- <span data-ttu-id="c2c34-114">WinrsExe</span><span class="sxs-lookup"><span data-stu-id="c2c34-114">WinrsExe</span></span>
- <span data-ttu-id="c2c34-115">WinrsMgr</span><span class="sxs-lookup"><span data-stu-id="c2c34-115">WinrsMgr</span></span>
- <span data-ttu-id="c2c34-116">WSManProvHost</span><span class="sxs-lookup"><span data-stu-id="c2c34-116">WSManProvHost</span></span>

<span data-ttu-id="c2c34-117">세션의 이름은 ' wsmlog '입니다.</span><span class="sxs-lookup"><span data-stu-id="c2c34-117">The session is named 'wsmlog'.</span></span>

<span data-ttu-id="c2c34-118">이 cmdlet은 cmdlet을 사용 합니다 `Start-Trace` .</span><span class="sxs-lookup"><span data-stu-id="c2c34-118">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="c2c34-119">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c34-119">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="c2c34-120">예제</span><span class="sxs-lookup"><span data-stu-id="c2c34-120">EXAMPLES</span></span>

### <span data-ttu-id="c2c34-121">예 1: WSMan 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c34-121">Example 1: Start a WSMan logging session.</span></span>

```powershell
Enable-WSManTrace
```

## <span data-ttu-id="c2c34-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c2c34-122">PARAMETERS</span></span>

### <span data-ttu-id="c2c34-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c2c34-123">CommonParameters</span></span>

<span data-ttu-id="c2c34-124">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c2c34-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c2c34-125">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c2c34-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c2c34-126">입력</span><span class="sxs-lookup"><span data-stu-id="c2c34-126">INPUTS</span></span>

### <span data-ttu-id="c2c34-127">없음</span><span class="sxs-lookup"><span data-stu-id="c2c34-127">None</span></span>

## <span data-ttu-id="c2c34-128">출력</span><span class="sxs-lookup"><span data-stu-id="c2c34-128">OUTPUTS</span></span>

### <span data-ttu-id="c2c34-129">없음</span><span class="sxs-lookup"><span data-stu-id="c2c34-129">None</span></span>

## <span data-ttu-id="c2c34-130">참고</span><span class="sxs-lookup"><span data-stu-id="c2c34-130">NOTES</span></span>

## <span data-ttu-id="c2c34-131">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c2c34-131">RELATED LINKS</span></span>

[<span data-ttu-id="c2c34-132">이벤트 추적</span><span class="sxs-lookup"><span data-stu-id="c2c34-132">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="c2c34-133">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="c2c34-133">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="c2c34-134">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="c2c34-134">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

