---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-tracesource?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TraceSource
ms.openlocfilehash: d136dd46eaceb65b5c512e3ff5c98e13d685d45e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216634"
---
# <span data-ttu-id="b86dc-103">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="b86dc-103">Get-TraceSource</span></span>

## <span data-ttu-id="b86dc-104">개요</span><span class="sxs-lookup"><span data-stu-id="b86dc-104">SYNOPSIS</span></span>
<span data-ttu-id="b86dc-105">추적을 위해 계측 된 PowerShell 구성 요소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b86dc-105">Gets PowerShell components that are instrumented for tracing.</span></span>

## <span data-ttu-id="b86dc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b86dc-106">SYNTAX</span></span>

```
Get-TraceSource [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="b86dc-107">설명</span><span class="sxs-lookup"><span data-stu-id="b86dc-107">DESCRIPTION</span></span>

<span data-ttu-id="b86dc-108">**TraceSource** cmdlet은 현재 사용 중인 PowerShell 구성 요소의 추적 원본을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b86dc-108">The **Get-TraceSource** cmdlet gets the trace sources for PowerShell components that are currently in use.</span></span>
<span data-ttu-id="b86dc-109">데이터를 사용 하 여 추적할 수 있는 PowerShell 구성 요소를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b86dc-109">You can use the data to determine which PowerShell components you can trace.</span></span>
<span data-ttu-id="b86dc-110">추적할 때 구성 요소가 내부 처리의 각 단계에 대한 상세 메시지를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b86dc-110">When tracing, the component generates detailed messages about each step in its internal processing.</span></span>
<span data-ttu-id="b86dc-111">개발자는 추적 데이터를 사용하여 데이터 흐름, 프로그램 실행 및 오류를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="b86dc-111">Developers use the trace data to monitor data flow, program execution, and errors.</span></span>

<span data-ttu-id="b86dc-112">추적 cmdlet은 PowerShell 개발자 용으로 만들어졌지만 모든 사용자가 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b86dc-112">The tracing cmdlets were designed for PowerShell developers, but they are available to all users.</span></span>

## <span data-ttu-id="b86dc-113">예제</span><span class="sxs-lookup"><span data-stu-id="b86dc-113">EXAMPLES</span></span>

### <span data-ttu-id="b86dc-114">예제 1: 이름별로 추적 소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="b86dc-114">Example 1: Get trace sources by name</span></span>

```
PS C:\> Get-TraceSource -Name "*provider*"
```

<span data-ttu-id="b86dc-115">이 명령은 공급자가 포함 된 이름이 있는 추적 원본을 모두 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b86dc-115">This command gets all of the trace sources that have names that include provider.</span></span>

### <span data-ttu-id="b86dc-116">예제 2: 모든 추적 원본 가져오기</span><span class="sxs-lookup"><span data-stu-id="b86dc-116">Example 2: Get all trace sources</span></span>

```
PS C:\> Get-TraceSource
```

<span data-ttu-id="b86dc-117">이 명령은 추적할 수 있는 모든 PowerShell 구성 요소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b86dc-117">This command gets all of the PowerShell components that can be traced.</span></span>

## <span data-ttu-id="b86dc-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b86dc-118">PARAMETERS</span></span>

### <span data-ttu-id="b86dc-119">-Name</span><span class="sxs-lookup"><span data-stu-id="b86dc-119">-Name</span></span>

<span data-ttu-id="b86dc-120">가져올 추적 소스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b86dc-120">Specifies the trace sources to get.</span></span>
<span data-ttu-id="b86dc-121">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="b86dc-121">Wildcards are permitted.</span></span>
<span data-ttu-id="b86dc-122">매개 변수 이름 *이름은* 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b86dc-122">The parameter name *Name* is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="b86dc-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b86dc-123">CommonParameters</span></span>

<span data-ttu-id="b86dc-124">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b86dc-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b86dc-125">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b86dc-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b86dc-126">입력</span><span class="sxs-lookup"><span data-stu-id="b86dc-126">INPUTS</span></span>

### <span data-ttu-id="b86dc-127">System.String</span><span class="sxs-lookup"><span data-stu-id="b86dc-127">System.String</span></span>

<span data-ttu-id="b86dc-128">추적 소스의 이름을 포함 하는 문자열을 **TraceSource** 로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b86dc-128">You can pipe a string that contains the name of a trace source to **Get-TraceSource** .</span></span>

## <span data-ttu-id="b86dc-129">출력</span><span class="sxs-lookup"><span data-stu-id="b86dc-129">OUTPUTS</span></span>

### <span data-ttu-id="b86dc-130">시스템 관리..</span><span class="sxs-lookup"><span data-stu-id="b86dc-130">System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="b86dc-131">**TraceSource** 는 추적 원본을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b86dc-131">**Get-TraceSource** returns objects that represent the trace sources.</span></span>

## <span data-ttu-id="b86dc-132">참고</span><span class="sxs-lookup"><span data-stu-id="b86dc-132">NOTES</span></span>

## <span data-ttu-id="b86dc-133">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b86dc-133">RELATED LINKS</span></span>

[<span data-ttu-id="b86dc-134">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="b86dc-134">Set-TraceSource</span></span>](Set-TraceSource.md)

[<span data-ttu-id="b86dc-135">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="b86dc-135">Trace-Command</span></span>](Trace-Command.md)
