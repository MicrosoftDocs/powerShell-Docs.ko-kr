---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TimeZone
ms.openlocfilehash: 22034eeac6988478a5f2ff87b2582cc5e1acc1c0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599958"
---
# <span data-ttu-id="3d700-102">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="3d700-102">Get-TimeZone</span></span>

## <span data-ttu-id="3d700-103">개요</span><span class="sxs-lookup"><span data-stu-id="3d700-103">SYNOPSIS</span></span>
<span data-ttu-id="3d700-104">현재 표준 시간대 또는 사용 가능한 표준 시간대 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3d700-104">Gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="3d700-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3d700-105">SYNTAX</span></span>

### <span data-ttu-id="3d700-106">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="3d700-106">Name (Default)</span></span>

```
Get-TimeZone [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="3d700-107">Id</span><span class="sxs-lookup"><span data-stu-id="3d700-107">Id</span></span>

```
Get-TimeZone -Id <String[]> [<CommonParameters>]
```

### <span data-ttu-id="3d700-108">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="3d700-108">ListAvailable</span></span>

```
Get-TimeZone [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="3d700-109">설명</span><span class="sxs-lookup"><span data-stu-id="3d700-109">DESCRIPTION</span></span>

<span data-ttu-id="3d700-110">**표준** 시간대 cmdlet은 현재 표준 시간대 또는 사용 가능한 표준 시간대 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3d700-110">The **Get-TimeZone** cmdlet gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="3d700-111">예제</span><span class="sxs-lookup"><span data-stu-id="3d700-111">EXAMPLES</span></span>

### <span data-ttu-id="3d700-112">예 1: 현재 표준 시간대 가져오기</span><span class="sxs-lookup"><span data-stu-id="3d700-112">Example 1: Get the current time zone</span></span>

```
PS C:\> Get-TimeZone
Pacific Standard Time
```

<span data-ttu-id="3d700-113">이 명령은 현재 표준 시간대를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3d700-113">This command gets the current time zone.</span></span>

### <span data-ttu-id="3d700-114">예제 2: 지정 된 문자열과 일치 하는 표준 시간대 가져오기</span><span class="sxs-lookup"><span data-stu-id="3d700-114">Example 2: Get time zones that match a specified string</span></span>

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

<span data-ttu-id="3d700-115">이 명령은 지정 된 와일드 카드와 일치 하는 모든 표준 시간대를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3d700-115">This command gets all time zones that match the specified wildcard.</span></span>

### <span data-ttu-id="3d700-116">예제 3: 사용 가능한 모든 표준 시간대 가져오기</span><span class="sxs-lookup"><span data-stu-id="3d700-116">Example 3: Get all available time zones</span></span>

```
PS C:\> Get-TimeZone -ListAvailable
```

<span data-ttu-id="3d700-117">이 명령은 사용 가능한 모든 표준 시간대를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3d700-117">This command gets all available time zones.</span></span>

## <span data-ttu-id="3d700-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3d700-118">PARAMETERS</span></span>

### <span data-ttu-id="3d700-119">-Id</span><span class="sxs-lookup"><span data-stu-id="3d700-119">-Id</span></span>

<span data-ttu-id="3d700-120">이 cmdlet이 가져오는 표준 시간대의 ID 또는 ID를 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d700-120">Specifies, as a string array, the ID or IDs of the time zones that this cmdlet gets.</span></span>

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

### <span data-ttu-id="3d700-121">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="3d700-121">-ListAvailable</span></span>

<span data-ttu-id="3d700-122">이 cmdlet은 사용 가능한 모든 표준 시간대를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3d700-122">Indicates that this cmdlet gets all available time zones.</span></span>

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

### <span data-ttu-id="3d700-123">-Name</span><span class="sxs-lookup"><span data-stu-id="3d700-123">-Name</span></span>

<span data-ttu-id="3d700-124">이 cmdlet이 가져오는 표준 시간대의 이름 또는 이름을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d700-124">Specifies, as a string array, the name or names of the time zones that this cmdlet gets.</span></span>

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

### <span data-ttu-id="3d700-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3d700-125">CommonParameters</span></span>

<span data-ttu-id="3d700-126">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3d700-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3d700-127">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d700-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3d700-128">입력</span><span class="sxs-lookup"><span data-stu-id="3d700-128">INPUTS</span></span>

### <span data-ttu-id="3d700-129">System.String[]</span><span class="sxs-lookup"><span data-stu-id="3d700-129">System.String[]</span></span>

## <span data-ttu-id="3d700-130">출력</span><span class="sxs-lookup"><span data-stu-id="3d700-130">OUTPUTS</span></span>

### <span data-ttu-id="3d700-131">TimeZoneInfo []</span><span class="sxs-lookup"><span data-stu-id="3d700-131">System.TimeZoneInfo[]</span></span>

## <span data-ttu-id="3d700-132">참고</span><span class="sxs-lookup"><span data-stu-id="3d700-132">NOTES</span></span>

<span data-ttu-id="3d700-133">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d700-133">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="3d700-134">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3d700-134">RELATED LINKS</span></span>

[<span data-ttu-id="3d700-135">Set-TimeZone</span><span class="sxs-lookup"><span data-stu-id="3d700-135">Set-TimeZone</span></span>](Set-TimeZone.md)
