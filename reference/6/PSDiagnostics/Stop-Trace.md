---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/stop-trace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Trace
ms.openlocfilehash: 48027fe707660f7844c28bf5f8916b0f51e0d4d1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214913"
---
# <span data-ttu-id="59cd5-103">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="59cd5-103">Stop-Trace</span></span>

## <span data-ttu-id="59cd5-104">개요</span><span class="sxs-lookup"><span data-stu-id="59cd5-104">SYNOPSIS</span></span>
<span data-ttu-id="59cd5-105">이벤트 추적 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="59cd5-105">Stop an Event Trace logging session.</span></span>

## <span data-ttu-id="59cd5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="59cd5-106">SYNTAX</span></span>

```
Stop-Trace [-SessionName] <Object> [-ETS] [<CommonParameters>]
```

## <span data-ttu-id="59cd5-107">설명</span><span class="sxs-lookup"><span data-stu-id="59cd5-107">DESCRIPTION</span></span>

<span data-ttu-id="59cd5-108">이 cmdlet은 Windows 이벤트 추적 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="59cd5-108">This cmdlet stops a Windows Event Trace logging session.</span></span>

<span data-ttu-id="59cd5-109">이 cmdlet은 다음 cmdlet에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59cd5-109">This cmdlet is used by the following cmdlets:</span></span>

- `Disable-PSWSManCombinedTrace`
- `Disable-WSManTrace`

<span data-ttu-id="59cd5-110">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59cd5-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="59cd5-111">예제</span><span class="sxs-lookup"><span data-stu-id="59cd5-111">EXAMPLES</span></span>

### <span data-ttu-id="59cd5-112">예 1: WSMan 추적 로깅 세션 중지</span><span class="sxs-lookup"><span data-stu-id="59cd5-112">Example 1: Stop a WSMan Trace logging session</span></span>

```powershell
Stop-Trace -SessionName 'wsmlog'
```

## <span data-ttu-id="59cd5-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="59cd5-113">PARAMETERS</span></span>

### <span data-ttu-id="59cd5-114">-%</span><span class="sxs-lookup"><span data-stu-id="59cd5-114">-ETS</span></span>
<span data-ttu-id="59cd5-115">이벤트 추적 세션 명령을 저장 하거나 예약 하지 않고 직접 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="59cd5-115">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="59cd5-116">-세션 이름</span><span class="sxs-lookup"><span data-stu-id="59cd5-116">-SessionName</span></span>
<span data-ttu-id="59cd5-117">중지할 이벤트 추적 세션의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="59cd5-117">The name of the Event Trace session to be stopped.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="59cd5-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="59cd5-118">CommonParameters</span></span>
<span data-ttu-id="59cd5-119">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="59cd5-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="59cd5-120">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59cd5-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="59cd5-121">입력</span><span class="sxs-lookup"><span data-stu-id="59cd5-121">INPUTS</span></span>

### <span data-ttu-id="59cd5-122">없음</span><span class="sxs-lookup"><span data-stu-id="59cd5-122">None</span></span>

## <span data-ttu-id="59cd5-123">출력</span><span class="sxs-lookup"><span data-stu-id="59cd5-123">OUTPUTS</span></span>

### <span data-ttu-id="59cd5-124">없음</span><span class="sxs-lookup"><span data-stu-id="59cd5-124">None</span></span>

## <span data-ttu-id="59cd5-125">참고</span><span class="sxs-lookup"><span data-stu-id="59cd5-125">NOTES</span></span>

## <span data-ttu-id="59cd5-126">관련 링크</span><span class="sxs-lookup"><span data-stu-id="59cd5-126">RELATED LINKS</span></span>

[<span data-ttu-id="59cd5-127">이벤트 추적</span><span class="sxs-lookup"><span data-stu-id="59cd5-127">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="59cd5-128">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="59cd5-128">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="59cd5-129">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="59cd5-129">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="59cd5-130">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="59cd5-130">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="59cd5-131">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="59cd5-131">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="59cd5-132">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="59cd5-132">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
