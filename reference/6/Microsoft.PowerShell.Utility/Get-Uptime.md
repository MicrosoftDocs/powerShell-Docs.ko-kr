---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uptime?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Uptime
ms.openlocfilehash: 999ef16ef3065c26dc1d51e49c5ba5793af7db4a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216593"
---
# <span data-ttu-id="a19db-102">Get-Uptime</span><span class="sxs-lookup"><span data-stu-id="a19db-102">Get-Uptime</span></span>

## <span data-ttu-id="a19db-103">개요</span><span class="sxs-lookup"><span data-stu-id="a19db-103">SYNOPSIS</span></span>
<span data-ttu-id="a19db-104">마지막 부팅 이후 **TimeSpan** 을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a19db-104">Get the **TimeSpan** since last boot.</span></span>

## <span data-ttu-id="a19db-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a19db-105">SYNTAX</span></span>

### <span data-ttu-id="a19db-106">Timespan (기본값)</span><span class="sxs-lookup"><span data-stu-id="a19db-106">Timespan (Default)</span></span>

```
Get-Uptime [<CommonParameters>]
```

### <span data-ttu-id="a19db-107">이후</span><span class="sxs-lookup"><span data-stu-id="a19db-107">Since</span></span>

```
Get-Uptime [-Since] [<CommonParameters>]
```

## <span data-ttu-id="a19db-108">설명</span><span class="sxs-lookup"><span data-stu-id="a19db-108">DESCRIPTION</span></span>

<span data-ttu-id="a19db-109">이 cmdlet은 운영 체제의 마지막 부팅 이후 경과 된 시간을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a19db-109">This cmdlet returns the time elapsed since the last boot of the operating system.</span></span>

<span data-ttu-id="a19db-110">`Get-Uptime`Cmdlet은 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a19db-110">The `Get-Uptime` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="a19db-111">예제</span><span class="sxs-lookup"><span data-stu-id="a19db-111">EXAMPLES</span></span>

### <span data-ttu-id="a19db-112">예제 1-마지막 부팅 이후 시간 표시</span><span class="sxs-lookup"><span data-stu-id="a19db-112">Example 1 - Show time since last boot</span></span>

```powershell
Get-Uptime
```

```Output
Days              : 9
Hours             : 0
Minutes           : 9
Seconds           : 45
Milliseconds      : 0
Ticks             : 7781850000000
TotalDays         : 9.00677083333333
TotalHours        : 216.1625
TotalMinutes      : 12969.75
TotalSeconds      : 778185
TotalMilliseconds : 778185000
```

### <span data-ttu-id="a19db-113">예 2-마지막 부팅 시간 표시</span><span class="sxs-lookup"><span data-stu-id="a19db-113">Example 2 - Show the time of the last boot</span></span>

```powershell
Get-Uptime -Since
```

```Output
Tuesday, June 18, 2019 2:34:56 PM
```

## <span data-ttu-id="a19db-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a19db-114">PARAMETERS</span></span>

### <span data-ttu-id="a19db-115">-이후</span><span class="sxs-lookup"><span data-stu-id="a19db-115">-Since</span></span>

<span data-ttu-id="a19db-116">Cmdlet이 운영 체제가 마지막으로 부팅 된 시간을 나타내는 **DateTime** 개체를 반환 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a19db-116">Cause the cmdlet to return a **DateTime** object representing the last time that the operating system was booted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Since
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a19db-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a19db-117">CommonParameters</span></span>

<span data-ttu-id="a19db-118">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a19db-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a19db-119">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a19db-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a19db-120">입력</span><span class="sxs-lookup"><span data-stu-id="a19db-120">INPUTS</span></span>

### <span data-ttu-id="a19db-121">없음</span><span class="sxs-lookup"><span data-stu-id="a19db-121">None</span></span>

## <span data-ttu-id="a19db-122">출력</span><span class="sxs-lookup"><span data-stu-id="a19db-122">OUTPUTS</span></span>

### <span data-ttu-id="a19db-123">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="a19db-123">System.TimeSpan</span></span>

<span data-ttu-id="a19db-124">이는 매개 변수를 사용 하지 않는 경우의 기본 반환 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a19db-124">This is the default return type when no parameters are used.</span></span>

### <span data-ttu-id="a19db-125">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="a19db-125">System.DateTime</span></span>

<span data-ttu-id="a19db-126">이 형식은 **이후** 매개 변수를 사용할 때 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a19db-126">This type is returned when using the **Since** parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="a19db-127">Windows 빠른 시작을 사용 하는 경우 Windows에서는 **Lastbootuptime 시간** 에 저장 된 값을 업데이트 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a19db-127">If Windows fast startup is enabled, Windows does not update the value stored in **LastBootUpTime** .</span></span> <span data-ttu-id="a19db-128">빠른 시작을 사용 하지 않도록 설정 하려면 다음 명령을 실행 `Powercfg -h off` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a19db-128">To disable fast startup, run the following command: `Powercfg -h off`.</span></span>
>
> <span data-ttu-id="a19db-129">Windows 빠른 시작에 대 한 자세한 내용은 절전 모드에서 절전 모드에서 [빠른 시작을 구별](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation)하는 방법을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a19db-129">For more information about Windows fast startup, see [Distinguishing Fast Startup from Wake-from-Hibernation](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation).</span></span>

## <span data-ttu-id="a19db-130">참고</span><span class="sxs-lookup"><span data-stu-id="a19db-130">NOTES</span></span>

<span data-ttu-id="a19db-131">Windows에서 반환 되는 값은 WMI에 있는 **Win32_OperatingSystem** 클래스의 **lastbootuptime 시간** 속성과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="a19db-131">On Windows, the value returned is the same as the **LastBootUpTime** property of the **Win32_OperatingSystem** class in WMI.</span></span>

## <span data-ttu-id="a19db-132">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a19db-132">RELATED LINKS</span></span>

[<span data-ttu-id="a19db-133">Win32_OperatingSystem</span><span class="sxs-lookup"><span data-stu-id="a19db-133">Win32_OperatingSystem</span></span>](/windows/win32/cimwin32prov/win32-operatingsystem#properties)
