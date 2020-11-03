---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TimeZone
ms.openlocfilehash: ae937a7e72b2b1f2d5f455358a0034717e3e4634
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215394"
---
# <span data-ttu-id="6fc73-103">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="6fc73-103">Get-TimeZone</span></span>

## <span data-ttu-id="6fc73-104">개요</span><span class="sxs-lookup"><span data-stu-id="6fc73-104">SYNOPSIS</span></span>
<span data-ttu-id="6fc73-105">현재 표준 시간대 또는 사용 가능한 표준 시간대 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6fc73-105">Gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="6fc73-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6fc73-106">SYNTAX</span></span>

### <span data-ttu-id="6fc73-107">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="6fc73-107">Name (Default)</span></span>

```
Get-TimeZone [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="6fc73-108">Id</span><span class="sxs-lookup"><span data-stu-id="6fc73-108">Id</span></span>

```
Get-TimeZone -Id <String[]> [<CommonParameters>]
```

### <span data-ttu-id="6fc73-109">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="6fc73-109">ListAvailable</span></span>

```
Get-TimeZone [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="6fc73-110">설명</span><span class="sxs-lookup"><span data-stu-id="6fc73-110">DESCRIPTION</span></span>

<span data-ttu-id="6fc73-111">**표준** 시간대 cmdlet은 현재 표준 시간대 또는 사용 가능한 표준 시간대 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6fc73-111">The **Get-TimeZone** cmdlet gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="6fc73-112">예제</span><span class="sxs-lookup"><span data-stu-id="6fc73-112">EXAMPLES</span></span>

### <span data-ttu-id="6fc73-113">예 1: 현재 표준 시간대 가져오기</span><span class="sxs-lookup"><span data-stu-id="6fc73-113">Example 1: Get the current time zone</span></span>

```
PS C:\> Get-TimeZone
Pacific Standard Time
```

<span data-ttu-id="6fc73-114">이 명령은 현재 표준 시간대를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6fc73-114">This command gets the current time zone.</span></span>

### <span data-ttu-id="6fc73-115">예제 2: 지정 된 문자열과 일치 하는 표준 시간대 가져오기</span><span class="sxs-lookup"><span data-stu-id="6fc73-115">Example 2: Get time zones that match a specified string</span></span>

```
PS C:\> Get-TimeZone -Name "*pac*"
Pacific Standard Time (Mexico)

(UTC-08:00) Pacific Time (US &amp; Canada)

Pacific Standard Time

SA Pacific Standard Time

Pacific SA Standard Time

West Pacific Standard Time

Central Pacific Standard Time
```

<span data-ttu-id="6fc73-116">이 명령은 지정 된 와일드 카드와 일치 하는 모든 표준 시간대를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6fc73-116">This command gets all time zones that match the specified wildcard.</span></span>

### <span data-ttu-id="6fc73-117">예제 3: 사용 가능한 모든 표준 시간대 가져오기</span><span class="sxs-lookup"><span data-stu-id="6fc73-117">Example 3: Get all available time zones</span></span>

```
PS C:\> Get-TimeZone -ListAvailable
```

<span data-ttu-id="6fc73-118">이 명령은 사용 가능한 모든 표준 시간대를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6fc73-118">This command gets all available time zones.</span></span>

## <span data-ttu-id="6fc73-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6fc73-119">PARAMETERS</span></span>

### <span data-ttu-id="6fc73-120">-Id</span><span class="sxs-lookup"><span data-stu-id="6fc73-120">-Id</span></span>

<span data-ttu-id="6fc73-121">이 cmdlet이 가져오는 표준 시간대의 ID 또는 ID를 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc73-121">Specifies, as a string array, the ID or IDs of the time zones that this cmdlet gets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6fc73-122">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="6fc73-122">-ListAvailable</span></span>

<span data-ttu-id="6fc73-123">이 cmdlet은 사용 가능한 모든 표준 시간대를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6fc73-123">Indicates that this cmdlet gets all available time zones.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ListAvailable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6fc73-124">-Name</span><span class="sxs-lookup"><span data-stu-id="6fc73-124">-Name</span></span>

<span data-ttu-id="6fc73-125">이 cmdlet이 가져오는 표준 시간대의 이름 또는 이름을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fc73-125">Specifies, as a string array, the name or names of the time zones that this cmdlet gets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="6fc73-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6fc73-126">CommonParameters</span></span>

<span data-ttu-id="6fc73-127">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6fc73-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6fc73-128">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6fc73-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6fc73-129">입력</span><span class="sxs-lookup"><span data-stu-id="6fc73-129">INPUTS</span></span>

### <span data-ttu-id="6fc73-130">System.String[]</span><span class="sxs-lookup"><span data-stu-id="6fc73-130">System.String[]</span></span>

## <span data-ttu-id="6fc73-131">출력</span><span class="sxs-lookup"><span data-stu-id="6fc73-131">OUTPUTS</span></span>

### <span data-ttu-id="6fc73-132">TimeZoneInfo []</span><span class="sxs-lookup"><span data-stu-id="6fc73-132">System.TimeZoneInfo[]</span></span>

## <span data-ttu-id="6fc73-133">참고</span><span class="sxs-lookup"><span data-stu-id="6fc73-133">NOTES</span></span>

## <span data-ttu-id="6fc73-134">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6fc73-134">RELATED LINKS</span></span>

[<span data-ttu-id="6fc73-135">Set-TimeZone</span><span class="sxs-lookup"><span data-stu-id="6fc73-135">Set-TimeZone</span></span>](Set-TimeZone.md)
