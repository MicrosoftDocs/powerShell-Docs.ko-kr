---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/18/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-timezone?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TimeZone
ms.openlocfilehash: 4bade5a583533c3156fb923a5257ebb7a4453a2b
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347536"
---
# <span data-ttu-id="b0028-103">Set-TimeZone</span><span class="sxs-lookup"><span data-stu-id="b0028-103">Set-TimeZone</span></span>

## <span data-ttu-id="b0028-104">개요</span><span class="sxs-lookup"><span data-stu-id="b0028-104">SYNOPSIS</span></span>
<span data-ttu-id="b0028-105">시스템 표준 시간대를 지정 된 표준 시간대로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0028-105">Sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="b0028-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b0028-106">SYNTAX</span></span>

### <span data-ttu-id="b0028-107">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="b0028-107">Name (Default)</span></span>

```
Set-TimeZone [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b0028-108">Id</span><span class="sxs-lookup"><span data-stu-id="b0028-108">Id</span></span>

```
Set-TimeZone -Id <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b0028-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="b0028-109">InputObject</span></span>

```
Set-TimeZone [-InputObject] <TimeZoneInfo> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b0028-110">설명</span><span class="sxs-lookup"><span data-stu-id="b0028-110">DESCRIPTION</span></span>

<span data-ttu-id="b0028-111">`Set-TimeZone`Cmdlet은 시스템 표준 시간대를 지정 된 표준 시간대로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0028-111">The `Set-TimeZone` cmdlet sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="b0028-112">예제</span><span class="sxs-lookup"><span data-stu-id="b0028-112">EXAMPLES</span></span>

### <span data-ttu-id="b0028-113">예제 1: Id로 표준 시간대 설정</span><span class="sxs-lookup"><span data-stu-id="b0028-113">Example 1: Set the time zone by Id</span></span>

<span data-ttu-id="b0028-114">이 예에서는 로컬 컴퓨터의 표준 시간대를 러시아어 표준 시간으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0028-114">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

```powershell
Set-TimeZone -Id "Russian Standard Time" -PassThru
```

```Output
Id                         : Russian Standard Time
DisplayName                : (UTC+03:00) Moscow, St. Petersburg
StandardName               : Russia TZ 2 Standard Time
DaylightName               : Russia TZ 2 Daylight Time
BaseUtcOffset              : 03:00:00
SupportsDaylightSavingTime : True
```

### <span data-ttu-id="b0028-115">예제 2: 이름을 기준으로 표준 시간대 설정</span><span class="sxs-lookup"><span data-stu-id="b0028-115">Example 2: Set the time zone by name</span></span>

<span data-ttu-id="b0028-116">이 예에서는 로컬 컴퓨터의 표준 시간대를 러시아어 표준 시간으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0028-116">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

```powershell
Set-TimeZone -Name "Russia TZ 2 Standard Time"
```

<span data-ttu-id="b0028-117">이전 예제에서 보았듯이 표준 시간대의 **Id** 와 **이름은** 항상 일치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b0028-117">As we saw in the previous example, the **Id** and the **Name** of the Time Zone do not always match.</span></span>
<span data-ttu-id="b0028-118">**Name** 매개 변수는 **TimeZoneInfo** 개체의 **standardname** 또는 **daylightname** 속성과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0028-118">The **Name** parameter must match the **StandardName** or **DaylightName** properties of the **TimeZoneInfo** object.</span></span>

## <span data-ttu-id="b0028-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b0028-119">PARAMETERS</span></span>

### <span data-ttu-id="b0028-120">-Id</span><span class="sxs-lookup"><span data-stu-id="b0028-120">-Id</span></span>

<span data-ttu-id="b0028-121">이 cmdlet이 설정 하는 표준 시간대의 ID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0028-121">Specifies the ID of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="b0028-122">다음 명령을 실행 하 여 표준 시간대 Id의 전체 목록을 가져올 수 있습니다 `Get-TimeZone -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="b0028-122">A full list of Time Zone IDs can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

```yaml
Type: System.String
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b0028-123">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b0028-123">-InputObject</span></span>

<span data-ttu-id="b0028-124">입력으로 사용할 **TimeZoneInfo** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0028-124">Specifies a **TimeZoneInfo** object to use as input.</span></span>

```yaml
Type: System.TimeZoneInfo
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b0028-125">-Name</span><span class="sxs-lookup"><span data-stu-id="b0028-125">-Name</span></span>

<span data-ttu-id="b0028-126">이 cmdlet이 설정 하는 표준 시간대의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0028-126">Specifies the name of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="b0028-127">다음 명령을 실행 하 여 표준 시간대 이름의 전체 목록을 가져올 수 있습니다 `Get-TimeZone -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="b0028-127">A full list of Time Zone names can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0028-128">-PassThru</span><span class="sxs-lookup"><span data-stu-id="b0028-128">-PassThru</span></span>

<span data-ttu-id="b0028-129">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b0028-129">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="b0028-130">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b0028-130">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="b0028-131">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b0028-131">-Confirm</span></span>

<span data-ttu-id="b0028-132">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="b0028-132">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0028-133">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b0028-133">-WhatIf</span></span>

<span data-ttu-id="b0028-134">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b0028-134">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b0028-135">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b0028-135">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0028-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b0028-136">CommonParameters</span></span>

<span data-ttu-id="b0028-137">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b0028-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b0028-138">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b0028-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b0028-139">입력</span><span class="sxs-lookup"><span data-stu-id="b0028-139">INPUTS</span></span>

### <span data-ttu-id="b0028-140">System.string, TimeZoneInfo, System.string</span><span class="sxs-lookup"><span data-stu-id="b0028-140">System.String, System.TimeZoneInfo, System.String</span></span>

## <span data-ttu-id="b0028-141">출력</span><span class="sxs-lookup"><span data-stu-id="b0028-141">OUTPUTS</span></span>

## <span data-ttu-id="b0028-142">참고</span><span class="sxs-lookup"><span data-stu-id="b0028-142">NOTES</span></span>

<span data-ttu-id="b0028-143">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0028-143">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="b0028-144">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b0028-144">RELATED LINKS</span></span>

[<span data-ttu-id="b0028-145">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="b0028-145">Get-TimeZone</span></span>](Get-TimeZone.md)
