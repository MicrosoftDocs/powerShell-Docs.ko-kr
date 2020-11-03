---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: cfe73dea98cdf858f1364e1daf434334b57a62cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217082"
---
# <span data-ttu-id="a408f-103">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="a408f-103">Enable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="a408f-104">개요</span><span class="sxs-lookup"><span data-stu-id="a408f-104">SYNOPSIS</span></span>
<span data-ttu-id="a408f-105">WSMan 및 PowerShell 공급자를 사용 하 여 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a408f-105">Start a logging session with the WSMan and PowerShell providers enabled.</span></span>

## <span data-ttu-id="a408f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a408f-106">SYNTAX</span></span>

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## <span data-ttu-id="a408f-107">설명</span><span class="sxs-lookup"><span data-stu-id="a408f-107">DESCRIPTION</span></span>

<span data-ttu-id="a408f-108">이 cmdlet은 다음 PowerShell 공급자를 사용 하 여 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a408f-108">This cmdlet starts a logging session with the following PowerShell providers enabled:</span></span>

- <span data-ttu-id="a408f-109">Microsoft-Windows-PowerShell</span><span class="sxs-lookup"><span data-stu-id="a408f-109">Microsoft-Windows-PowerShell</span></span>
- <span data-ttu-id="a408f-110">Microsoft-Windows-WinRM</span><span class="sxs-lookup"><span data-stu-id="a408f-110">Microsoft-Windows-WinRM</span></span>

<span data-ttu-id="a408f-111">세션의 이름은 ' PSTrace '입니다.</span><span class="sxs-lookup"><span data-stu-id="a408f-111">The session is named 'PSTrace'.</span></span>

<span data-ttu-id="a408f-112">이 cmdlet은 cmdlet을 사용 합니다 `Start-Trace` .</span><span class="sxs-lookup"><span data-stu-id="a408f-112">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="a408f-113">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a408f-113">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="a408f-114">예제</span><span class="sxs-lookup"><span data-stu-id="a408f-114">EXAMPLES</span></span>

### <span data-ttu-id="a408f-115">예제 1: 결합 된 로깅 세션 시작</span><span class="sxs-lookup"><span data-stu-id="a408f-115">Example 1: Start a combined logging session</span></span>

```powershell
Enable-PSWSManCombinedTrace
```

## <span data-ttu-id="a408f-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a408f-116">PARAMETERS</span></span>

### <span data-ttu-id="a408f-117">-DoNotOverwriteExistingTrace</span><span class="sxs-lookup"><span data-stu-id="a408f-117">-DoNotOverwriteExistingTrace</span></span>

<span data-ttu-id="a408f-118">기본적으로 이벤트는 "$pshome \Traces\PSTrace.etl"에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a408f-118">By default, the events are written to "$pshome\Traces\PSTrace.etl".</span></span> <span data-ttu-id="a408f-119">이 매개 변수를 사용 하는 경우 cmdlet은 "$pshome \Traces\ PSTrace_ {guid} .etl"의 고유한 파일 이름을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a408f-119">When this parameter is used, the cmdlet creates a unique filename: "$pshome\Traces\PSTrace_{guid}.etl"</span></span>

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

### <span data-ttu-id="a408f-120">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a408f-120">CommonParameters</span></span>

<span data-ttu-id="a408f-121">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a408f-121">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a408f-122">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a408f-122">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a408f-123">입력</span><span class="sxs-lookup"><span data-stu-id="a408f-123">INPUTS</span></span>

### <span data-ttu-id="a408f-124">없음</span><span class="sxs-lookup"><span data-stu-id="a408f-124">None</span></span>

## <span data-ttu-id="a408f-125">출력</span><span class="sxs-lookup"><span data-stu-id="a408f-125">OUTPUTS</span></span>

### <span data-ttu-id="a408f-126">없음</span><span class="sxs-lookup"><span data-stu-id="a408f-126">None</span></span>

## <span data-ttu-id="a408f-127">참고</span><span class="sxs-lookup"><span data-stu-id="a408f-127">NOTES</span></span>

## <span data-ttu-id="a408f-128">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a408f-128">RELATED LINKS</span></span>

[<span data-ttu-id="a408f-129">이벤트 추적</span><span class="sxs-lookup"><span data-stu-id="a408f-129">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="a408f-130">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="a408f-130">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="a408f-131">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="a408f-131">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)
