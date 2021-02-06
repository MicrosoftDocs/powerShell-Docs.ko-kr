---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/stop-trace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Trace
ms.openlocfilehash: 5727ae52326830fa16012722d0b801b7d43e50dd
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602230"
---
# <span data-ttu-id="d004c-102">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="d004c-102">Stop-Trace</span></span>

## <span data-ttu-id="d004c-103">개요</span><span class="sxs-lookup"><span data-stu-id="d004c-103">SYNOPSIS</span></span>
<span data-ttu-id="d004c-104">이벤트 추적 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d004c-104">Stop an Event Trace logging session.</span></span>

## <span data-ttu-id="d004c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d004c-105">SYNTAX</span></span>

```
Stop-Trace [-SessionName] <Object> [-ETS] [<CommonParameters>]
```

## <span data-ttu-id="d004c-106">설명</span><span class="sxs-lookup"><span data-stu-id="d004c-106">DESCRIPTION</span></span>

<span data-ttu-id="d004c-107">이 cmdlet은 Windows 이벤트 추적 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d004c-107">This cmdlet stops a Windows Event Trace logging session.</span></span>

<span data-ttu-id="d004c-108">이 cmdlet은 다음 cmdlet에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d004c-108">This cmdlet is used by the following cmdlets:</span></span>

- `Disable-PSWSManCombinedTrace`
- `Disable-WSManTrace`

<span data-ttu-id="d004c-109">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d004c-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="d004c-110">예제</span><span class="sxs-lookup"><span data-stu-id="d004c-110">EXAMPLES</span></span>

### <span data-ttu-id="d004c-111">예 1: WSMan 추적 로깅 세션 중지</span><span class="sxs-lookup"><span data-stu-id="d004c-111">Example 1: Stop a WSMan Trace logging session</span></span>

```powershell
Stop-Trace -SessionName 'wsmlog'
```

## <span data-ttu-id="d004c-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d004c-112">PARAMETERS</span></span>

### <span data-ttu-id="d004c-113">-%</span><span class="sxs-lookup"><span data-stu-id="d004c-113">-ETS</span></span>
<span data-ttu-id="d004c-114">이벤트 추적 세션 명령을 저장 하거나 예약 하지 않고 직접 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d004c-114">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

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

### <span data-ttu-id="d004c-115">-세션 이름</span><span class="sxs-lookup"><span data-stu-id="d004c-115">-SessionName</span></span>
<span data-ttu-id="d004c-116">중지할 이벤트 추적 세션의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d004c-116">The name of the Event Trace session to be stopped.</span></span>

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

### <span data-ttu-id="d004c-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d004c-117">CommonParameters</span></span>
<span data-ttu-id="d004c-118">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d004c-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d004c-119">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d004c-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d004c-120">입력</span><span class="sxs-lookup"><span data-stu-id="d004c-120">INPUTS</span></span>

### <span data-ttu-id="d004c-121">없음</span><span class="sxs-lookup"><span data-stu-id="d004c-121">None</span></span>

## <span data-ttu-id="d004c-122">출력</span><span class="sxs-lookup"><span data-stu-id="d004c-122">OUTPUTS</span></span>

### <span data-ttu-id="d004c-123">없음</span><span class="sxs-lookup"><span data-stu-id="d004c-123">None</span></span>

## <span data-ttu-id="d004c-124">참고</span><span class="sxs-lookup"><span data-stu-id="d004c-124">NOTES</span></span>

## <span data-ttu-id="d004c-125">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d004c-125">RELATED LINKS</span></span>

[<span data-ttu-id="d004c-126">이벤트 추적</span><span class="sxs-lookup"><span data-stu-id="d004c-126">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="d004c-127">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="d004c-127">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="d004c-128">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="d004c-128">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="d004c-129">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="d004c-129">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="d004c-130">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="d004c-130">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="d004c-131">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="d004c-131">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)

