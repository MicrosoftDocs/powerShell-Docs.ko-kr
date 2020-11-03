---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspacedebug?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-RunspaceDebug
ms.openlocfilehash: 821b532dc44702af4243bf36ca7f5d4089a057d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213026"
---
# <span data-ttu-id="5a8e0-103">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="5a8e0-103">Get-RunspaceDebug</span></span>

## <span data-ttu-id="5a8e0-104">개요</span><span class="sxs-lookup"><span data-stu-id="5a8e0-104">SYNOPSIS</span></span>
<span data-ttu-id="5a8e0-105">Runspace 디버깅 옵션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a8e0-105">Shows runspace debugging options.</span></span>

## <span data-ttu-id="5a8e0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5a8e0-106">SYNTAX</span></span>

### <span data-ttu-id="5a8e0-107">RunspaceNameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="5a8e0-107">RunspaceNameParameterSet (Default)</span></span>

```
Get-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="5a8e0-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="5a8e0-108">RunspaceParameterSet</span></span>

```
Get-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="5a8e0-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="5a8e0-109">RunspaceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="5a8e0-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="5a8e0-110">RunspaceInstanceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="5a8e0-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="5a8e0-111">ProcessNameParameterSet</span></span>

```
Get-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="5a8e0-112">설명</span><span class="sxs-lookup"><span data-stu-id="5a8e0-112">DESCRIPTION</span></span>

<span data-ttu-id="5a8e0-113">`Get-RunspaceDebug`Cmdlet은 runspace 디버깅 옵션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a8e0-113">The `Get-RunspaceDebug` cmdlet shows runspace debugging options.</span></span>

## <span data-ttu-id="5a8e0-114">예제</span><span class="sxs-lookup"><span data-stu-id="5a8e0-114">EXAMPLES</span></span>

### <span data-ttu-id="5a8e0-115">1: 기본 runspace 디버거의 상태를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a8e0-115">1: Show the state of the default runspace debugger</span></span>

```powershell
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="5a8e0-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5a8e0-116">PARAMETERS</span></span>

### <span data-ttu-id="5a8e0-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="5a8e0-117">-AppDomainName</span></span>

<span data-ttu-id="5a8e0-118">PowerShell runspace를 호스트 하는 응용 프로그램 도메인의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5a8e0-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="5a8e0-119">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="5a8e0-119">-ProcessName</span></span>

<span data-ttu-id="5a8e0-120">PowerShell runspace를 호스트 하는 프로세스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5a8e0-120">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="5a8e0-121">-Runspace</span><span class="sxs-lookup"><span data-stu-id="5a8e0-121">-Runspace</span></span>

<span data-ttu-id="5a8e0-122">사용할 하나 이상의 **Runspace** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="5a8e0-122">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="5a8e0-123">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="5a8e0-123">-RunspaceId</span></span>

<span data-ttu-id="5a8e0-124">하나 이상의 **Runspace** Id 번호를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a8e0-124">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="5a8e0-125">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="5a8e0-125">-RunspaceInstanceId</span></span>

<span data-ttu-id="5a8e0-126">하나 이상의 **Runspace** guid를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a8e0-126">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="5a8e0-127">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="5a8e0-127">-RunspaceName</span></span>

<span data-ttu-id="5a8e0-128">사용할 하나 이상의 **Runspace** 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5a8e0-128">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="5a8e0-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5a8e0-129">CommonParameters</span></span>

<span data-ttu-id="5a8e0-130">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5a8e0-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5a8e0-131">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5a8e0-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5a8e0-132">입력</span><span class="sxs-lookup"><span data-stu-id="5a8e0-132">INPUTS</span></span>

## <span data-ttu-id="5a8e0-133">출력</span><span class="sxs-lookup"><span data-stu-id="5a8e0-133">OUTPUTS</span></span>

## <span data-ttu-id="5a8e0-134">참고</span><span class="sxs-lookup"><span data-stu-id="5a8e0-134">NOTES</span></span>

## <span data-ttu-id="5a8e0-135">관련 링크</span><span class="sxs-lookup"><span data-stu-id="5a8e0-135">RELATED LINKS</span></span>

[<span data-ttu-id="5a8e0-136">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="5a8e0-136">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="5a8e0-137">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="5a8e0-137">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

