---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-runspacedebug?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-RunspaceDebug
ms.openlocfilehash: 7a014c456a28f3fde8b272ee45e0d0c264131718
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215842"
---
# <span data-ttu-id="69698-103">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="69698-103">Disable-RunspaceDebug</span></span>

## <span data-ttu-id="69698-104">개요</span><span class="sxs-lookup"><span data-stu-id="69698-104">SYNOPSIS</span></span>
<span data-ttu-id="69698-105">하나 이상의 runspace에서 디버깅을 사용 하지 않도록 설정 하 고 보류 중인 모든 디버거 중지를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="69698-105">Disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="69698-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="69698-106">SYNTAX</span></span>

### <span data-ttu-id="69698-107">RunspaceNameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="69698-107">RunspaceNameParameterSet (Default)</span></span>

```
Disable-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="69698-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="69698-108">RunspaceParameterSet</span></span>

```
Disable-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="69698-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="69698-109">RunspaceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="69698-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="69698-110">RunspaceInstanceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="69698-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="69698-111">ProcessNameParameterSet</span></span>

```
Disable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="69698-112">설명</span><span class="sxs-lookup"><span data-stu-id="69698-112">DESCRIPTION</span></span>

<span data-ttu-id="69698-113">`Disable-RunspaceDebug`이 cmdlet은 하나 이상의 runspace에서 디버깅을 사용 하지 않도록 설정 하 고 보류 중인 모든 디버거 중지를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="69698-113">The `Disable-RunspaceDebug` cmdlet disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="69698-114">예제</span><span class="sxs-lookup"><span data-stu-id="69698-114">EXAMPLES</span></span>

### <span data-ttu-id="69698-115">1: 기본 runspace 디버거를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="69698-115">1: Disable the default runspace debugger</span></span>

```powershell
Disable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="69698-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="69698-116">PARAMETERS</span></span>

### <span data-ttu-id="69698-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="69698-117">-AppDomainName</span></span>

<span data-ttu-id="69698-118">PowerShell runspace를 호스트 하는 응용 프로그램 도메인의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="69698-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="69698-119">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="69698-119">-ProcessName</span></span>

<span data-ttu-id="69698-120">PowerShell runspace를 호스트 하는 프로세스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="69698-120">The name of the process that hosts the PowerShell runspace.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="69698-121">-Runspace</span><span class="sxs-lookup"><span data-stu-id="69698-121">-Runspace</span></span>

<span data-ttu-id="69698-122">사용할 하나 이상의 **Runspace** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="69698-122">One or more **Runspace** objects to be disabled.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.Runspace[]
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="69698-123">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="69698-123">-RunspaceId</span></span>

<span data-ttu-id="69698-124">하나 이상의 **Runspace** Id 번호를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="69698-124">One or more **Runspace** Id numbers to be disabled.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: RunspaceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="69698-125">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="69698-125">-RunspaceInstanceId</span></span>

<span data-ttu-id="69698-126">하나 이상의 **Runspace** guid를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="69698-126">One or more **Runspace** GUIDs to be disabled.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: RunspaceInstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="69698-127">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="69698-127">-RunspaceName</span></span>

<span data-ttu-id="69698-128">사용할 하나 이상의 **Runspace** 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="69698-128">One or more **Runspace** names to be disabled.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RunspaceNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="69698-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="69698-129">CommonParameters</span></span>

<span data-ttu-id="69698-130">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="69698-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="69698-131">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69698-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="69698-132">입력</span><span class="sxs-lookup"><span data-stu-id="69698-132">INPUTS</span></span>

## <span data-ttu-id="69698-133">출력</span><span class="sxs-lookup"><span data-stu-id="69698-133">OUTPUTS</span></span>

## <span data-ttu-id="69698-134">참고</span><span class="sxs-lookup"><span data-stu-id="69698-134">NOTES</span></span>

## <span data-ttu-id="69698-135">관련 링크</span><span class="sxs-lookup"><span data-stu-id="69698-135">RELATED LINKS</span></span>

[<span data-ttu-id="69698-136">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="69698-136">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

[<span data-ttu-id="69698-137">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="69698-137">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)

