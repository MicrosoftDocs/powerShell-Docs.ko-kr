---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: 535cad057db406eaa48259288e34da6da4ed1cbb
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210146"
---
# <span data-ttu-id="05191-103">Start-Sleep</span><span class="sxs-lookup"><span data-stu-id="05191-103">Start-Sleep</span></span>

## <span data-ttu-id="05191-104">개요</span><span class="sxs-lookup"><span data-stu-id="05191-104">SYNOPSIS</span></span>
<span data-ttu-id="05191-105">지정한 기간 동안 스크립트 또는 세션의 활동을 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="05191-105">Suspends the activity in a script or session for the specified period of time.</span></span>

## <span data-ttu-id="05191-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="05191-106">SYNTAX</span></span>

### <span data-ttu-id="05191-107">초 (기본값)</span><span class="sxs-lookup"><span data-stu-id="05191-107">Seconds (Default)</span></span>

```
Start-Sleep [-Seconds] <Double> [<CommonParameters>]
```

### <span data-ttu-id="05191-108">밀리초</span><span class="sxs-lookup"><span data-stu-id="05191-108">Milliseconds</span></span>

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## <span data-ttu-id="05191-109">설명</span><span class="sxs-lookup"><span data-stu-id="05191-109">DESCRIPTION</span></span>

<span data-ttu-id="05191-110">`Start-Sleep`Cmdlet은 지정 된 기간 동안 스크립트나 세션의 작업을 일시 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="05191-110">The `Start-Sleep` cmdlet suspends the activity in a script or session for the specified period of time.</span></span> <span data-ttu-id="05191-111">작업이 완료될 때까지 대기, 작업을 반복하기 전에 일시 중지 등의 많은 작업에 이 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05191-111">You can use it for many tasks, such as waiting for an operation to complete or pausing before repeating an operation.</span></span>

## <span data-ttu-id="05191-112">예제</span><span class="sxs-lookup"><span data-stu-id="05191-112">EXAMPLES</span></span>

### <span data-ttu-id="05191-113">예제 1:15 초 동안 모든 명령 중지</span><span class="sxs-lookup"><span data-stu-id="05191-113">Example 1: Sleep all commands for 15 seconds</span></span>

```powershell
Start-Sleep -s 15
```

### <span data-ttu-id="05191-114">예제 2:1.5 초 동안 모든 명령 중지</span><span class="sxs-lookup"><span data-stu-id="05191-114">Example 2: Sleep all commands for 1.5 seconds</span></span>

<span data-ttu-id="05191-115">이 예제에서는 세션의 모든 명령을 1 초 동안 절전 모드로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05191-115">This example makes all the commands in the session sleep for one and one-half of a seconds.</span></span>

```powershell
Start-Sleep -Seconds 1.5
```

## <span data-ttu-id="05191-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="05191-116">PARAMETERS</span></span>

### <span data-ttu-id="05191-117">-밀리초</span><span class="sxs-lookup"><span data-stu-id="05191-117">-Milliseconds</span></span>

<span data-ttu-id="05191-118">리소스가 일시 중단되는 기간(밀리초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="05191-118">Specifies how long the resource sleeps in milliseconds.</span></span> <span data-ttu-id="05191-119">매개 변수는 **m** 으로 축약 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05191-119">The parameter can be abbreviated as **m** .</span></span>

```yaml
Type: System.Int32
Parameter Sets: Milliseconds
Aliases: ms

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="05191-120">-초</span><span class="sxs-lookup"><span data-stu-id="05191-120">-Seconds</span></span>

<span data-ttu-id="05191-121">리소스가 일시 중단되는 기간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="05191-121">Specifies how long the resource sleeps in seconds.</span></span> <span data-ttu-id="05191-122">매개 변수 이름을 생략 **하거나로 약어를 지정할** 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05191-122">You can omit the parameter name or you can abbreviate it as **s** .</span></span> <span data-ttu-id="05191-123">PowerShell 6.2.0부터이 매개 변수는 이제 소수 자릿수 값을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="05191-123">Beginning in PowerShell 6.2.0, this parameter now accepts fractional values.</span></span>

```yaml
Type: System.Double
Parameter Sets: Seconds
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="05191-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="05191-124">CommonParameters</span></span>

<span data-ttu-id="05191-125">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="05191-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="05191-126">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05191-126">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="05191-127">입력</span><span class="sxs-lookup"><span data-stu-id="05191-127">INPUTS</span></span>

### <span data-ttu-id="05191-128">System.Int32</span><span class="sxs-lookup"><span data-stu-id="05191-128">System.Int32</span></span>

<span data-ttu-id="05191-129">초 수를로 파이프 할 수 있습니다 `Start-Sleep` .</span><span class="sxs-lookup"><span data-stu-id="05191-129">You can pipe the number of seconds to `Start-Sleep`.</span></span>

## <span data-ttu-id="05191-130">출력</span><span class="sxs-lookup"><span data-stu-id="05191-130">OUTPUTS</span></span>

### <span data-ttu-id="05191-131">없음</span><span class="sxs-lookup"><span data-stu-id="05191-131">None</span></span>

<span data-ttu-id="05191-132">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05191-132">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="05191-133">참고</span><span class="sxs-lookup"><span data-stu-id="05191-133">NOTES</span></span>

- <span data-ttu-id="05191-134">의 기본 제공 별칭인를 참조할 수도 있습니다 `Start-Sleep` `sleep` .</span><span class="sxs-lookup"><span data-stu-id="05191-134">You can also refer to `Start-Sleep` by its built-in alias, `sleep`.</span></span> <span data-ttu-id="05191-135">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05191-135">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="05191-136">`Ctrl+C` 에서 중단 `Start-Sleep` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05191-136">`Ctrl+C` breaks out of `Start-Sleep`.</span></span>
  - <span data-ttu-id="05191-137">`Ctrl+C` 는 중단 되지 않습니다 `[Threading.Thread]::Sleep` .</span><span class="sxs-lookup"><span data-stu-id="05191-137">`Ctrl+C` does not break out of `[Threading.Thread]::Sleep`.</span></span> <span data-ttu-id="05191-138">자세한 내용은 [Sleep 메서드](/dotnet/api/system.threading.thread.sleep)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05191-138">For more information, see [Thread.Sleep Method](/dotnet/api/system.threading.thread.sleep).</span></span>

## <span data-ttu-id="05191-139">관련 링크</span><span class="sxs-lookup"><span data-stu-id="05191-139">RELATED LINKS</span></span>
