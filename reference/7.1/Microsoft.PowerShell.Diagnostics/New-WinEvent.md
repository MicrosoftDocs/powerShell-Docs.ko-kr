---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/new-winevent?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WinEvent
ms.openlocfilehash: 8605782176a96fa1901af352ceda8b453d2f1af8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217274"
---
# <span data-ttu-id="34b07-103">New-WinEvent</span><span class="sxs-lookup"><span data-stu-id="34b07-103">New-WinEvent</span></span>

## <span data-ttu-id="34b07-104">개요</span><span class="sxs-lookup"><span data-stu-id="34b07-104">SYNOPSIS</span></span>
<span data-ttu-id="34b07-105">지정된 이벤트 공급자에 대한 Windows 이벤트 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="34b07-105">Creates a new Windows event for the specified event provider.</span></span>

## <span data-ttu-id="34b07-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="34b07-106">SYNTAX</span></span>

```
New-WinEvent [-ProviderName] <String> [-Id] <Int32> [-Version <Byte>] [[-Payload] <Object[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="34b07-107">설명</span><span class="sxs-lookup"><span data-stu-id="34b07-107">DESCRIPTION</span></span>

<span data-ttu-id="34b07-108">**New-WinEvent** cmdlet은 이벤트 공급자에 대해 ETW(Windows용 이벤트 추적) 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="34b07-108">The **New-WinEvent** cmdlet creates an Event Tracing for Windows (ETW) event for an event provider.</span></span>
<span data-ttu-id="34b07-109">이 cmdlet을 사용 하 여 PowerShell에서 ETW 채널에 이벤트를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b07-109">You can use this cmdlet to add events to ETW channels from PowerShell.</span></span>

## <span data-ttu-id="34b07-110">예제</span><span class="sxs-lookup"><span data-stu-id="34b07-110">EXAMPLES</span></span>

### <span data-ttu-id="34b07-111">예 1</span><span class="sxs-lookup"><span data-stu-id="34b07-111">Example 1</span></span>

```powershell
PS C:\> New-WinEvent -ProviderName Microsoft-Windows-PowerShell -Id 45090 -Payload @("Workflow", "Running")
```

<span data-ttu-id="34b07-112">이 명령은 **New-WinEvent** cmdlet을 사용하여 Microsoft-Windows-PowerShell 공급자에 대해 이벤트 45090을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="34b07-112">This command uses the **New-WinEvent** cmdlet to create event 45090 for the Microsoft-Windows-PowerShell provider.</span></span>

## <span data-ttu-id="34b07-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="34b07-113">PARAMETERS</span></span>

### <span data-ttu-id="34b07-114">-Id</span><span class="sxs-lookup"><span data-stu-id="34b07-114">-Id</span></span>

<span data-ttu-id="34b07-115">계측 매니페스트를 통해 등록된 이벤트 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34b07-115">Specifies an event id that was registered through an instrumentation manifest.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="34b07-116">-페이로드</span><span class="sxs-lookup"><span data-stu-id="34b07-116">-Payload</span></span>

<span data-ttu-id="34b07-117">이벤트에 대한 메시지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34b07-117">Specifies the message for the event.</span></span> <span data-ttu-id="34b07-118">이벤트 로그에 이벤트를 기록하면 페이로드가 이벤트 개체의 **Message** 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="34b07-118">When the event is written to an event log, the payload is stored in the **Message** property of the event object.</span></span>

<span data-ttu-id="34b07-119">지정 된 페이로드가 이벤트 정의의 페이로드와 일치 하지 않으면 PowerShell에서 경고를 생성 하지만 명령은 여전히 성공 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b07-119">When the specified payload does not match the payload in the event definition, PowerShell generates a warning, but the command still succeeds.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="34b07-120">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="34b07-120">-ProviderName</span></span>

<span data-ttu-id="34b07-121">"Microsoft-Windows-PowerShell"과 같이 이벤트를 이벤트 로그에 기록하는 이벤트 공급자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34b07-121">Specifies the event provider that writes the event to an event log, such as "Microsoft-Windows-PowerShell".</span></span> <span data-ttu-id="34b07-122">ETW 이벤트 공급자는 이벤트를 ETW 세션에 기록하는 논리적 엔터티입니다.</span><span class="sxs-lookup"><span data-stu-id="34b07-122">An ETW event provider is a logical entity that writes events to ETW sessions.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="34b07-123">-Version</span><span class="sxs-lookup"><span data-stu-id="34b07-123">-Version</span></span>

<span data-ttu-id="34b07-124">이벤트의 버전 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34b07-124">Specifies the version number of the event.</span></span> <span data-ttu-id="34b07-125">이벤트 번호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="34b07-125">Type the event number.</span></span> <span data-ttu-id="34b07-126">PowerShell은 숫자를 필요한 바이트 형식으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b07-126">PowerShell converts the number to the required Byte type.</span></span>

<span data-ttu-id="34b07-127">이 매개 변수를 사용하면 동일한 이벤트의 다른 버전이 정의될 때 이벤트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b07-127">This parameter lets you specify an event when different versions of the same event are defined.</span></span>

```yaml
Type: System.Byte
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="34b07-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="34b07-128">CommonParameters</span></span>

<span data-ttu-id="34b07-129">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="34b07-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="34b07-130">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34b07-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="34b07-131">입력</span><span class="sxs-lookup"><span data-stu-id="34b07-131">INPUTS</span></span>

### <span data-ttu-id="34b07-132">없음</span><span class="sxs-lookup"><span data-stu-id="34b07-132">None</span></span>

<span data-ttu-id="34b07-133">이 cmdlet은 파이프라인에서 입력을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34b07-133">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="34b07-134">출력</span><span class="sxs-lookup"><span data-stu-id="34b07-134">OUTPUTS</span></span>

### <span data-ttu-id="34b07-135">없음</span><span class="sxs-lookup"><span data-stu-id="34b07-135">None</span></span>

<span data-ttu-id="34b07-136">이 cmdlet은 아무 출력도 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34b07-136">This cmdlet does to generate any output.</span></span>

## <span data-ttu-id="34b07-137">참고</span><span class="sxs-lookup"><span data-stu-id="34b07-137">NOTES</span></span>

* <span data-ttu-id="34b07-138">공급자가 이벤트 로그에도 기록 하면 Get-WinEvent cmdlet을 사용 하 여 이벤트 로그에서 이벤트를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b07-138">After the provider writes the even to an eventlog, you can use the Get-WinEvent cmdlet to get the event from the event log.</span></span>

## <span data-ttu-id="34b07-139">관련 링크</span><span class="sxs-lookup"><span data-stu-id="34b07-139">RELATED LINKS</span></span>

[<span data-ttu-id="34b07-140">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="34b07-140">Get-WinEvent</span></span>](Get-WinEvent.md)

