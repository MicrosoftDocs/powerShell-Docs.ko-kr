---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspacedebug?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-RunspaceDebug
ms.openlocfilehash: dbe78dd81641786b0079ef5326c849c2bde008dc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216641"
---
# <span data-ttu-id="790b5-103">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="790b5-103">Get-RunspaceDebug</span></span>

## <span data-ttu-id="790b5-104">개요</span><span class="sxs-lookup"><span data-stu-id="790b5-104">SYNOPSIS</span></span>
<span data-ttu-id="790b5-105">Runspace 디버깅 옵션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="790b5-105">Shows runspace debugging options.</span></span>

## <span data-ttu-id="790b5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="790b5-106">SYNTAX</span></span>

### <span data-ttu-id="790b5-107">RunspaceNameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="790b5-107">RunspaceNameParameterSet (Default)</span></span>

```
Get-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="790b5-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="790b5-108">RunspaceParameterSet</span></span>

```
Get-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="790b5-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="790b5-109">RunspaceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="790b5-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="790b5-110">RunspaceInstanceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="790b5-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="790b5-111">ProcessNameParameterSet</span></span>

```
Get-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="790b5-112">설명</span><span class="sxs-lookup"><span data-stu-id="790b5-112">DESCRIPTION</span></span>

<span data-ttu-id="790b5-113">`Get-RunspaceDebug`Cmdlet은 runspace 디버깅 옵션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="790b5-113">The `Get-RunspaceDebug` cmdlet shows runspace debugging options.</span></span>

## <span data-ttu-id="790b5-114">예제</span><span class="sxs-lookup"><span data-stu-id="790b5-114">EXAMPLES</span></span>

### <span data-ttu-id="790b5-115">1: 기본 runspace 디버거의 상태를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="790b5-115">1: Show the state of the default runspace debugger</span></span>

```powershell
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="790b5-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="790b5-116">PARAMETERS</span></span>

### <span data-ttu-id="790b5-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="790b5-117">-AppDomainName</span></span>

<span data-ttu-id="790b5-118">PowerShell runspace를 호스트 하는 응용 프로그램 도메인의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="790b5-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="790b5-119">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="790b5-119">-ProcessName</span></span>

<span data-ttu-id="790b5-120">PowerShell runspace를 호스트 하는 프로세스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="790b5-120">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="790b5-121">-Runspace</span><span class="sxs-lookup"><span data-stu-id="790b5-121">-Runspace</span></span>

<span data-ttu-id="790b5-122">사용할 하나 이상의 **Runspace** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="790b5-122">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="790b5-123">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="790b5-123">-RunspaceId</span></span>

<span data-ttu-id="790b5-124">하나 이상의 **Runspace** Id 번호를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="790b5-124">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="790b5-125">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="790b5-125">-RunspaceInstanceId</span></span>

<span data-ttu-id="790b5-126">하나 이상의 **Runspace** guid를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="790b5-126">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="790b5-127">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="790b5-127">-RunspaceName</span></span>

<span data-ttu-id="790b5-128">사용할 하나 이상의 **Runspace** 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="790b5-128">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="790b5-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="790b5-129">CommonParameters</span></span>

<span data-ttu-id="790b5-130">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="790b5-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="790b5-131">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="790b5-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="790b5-132">입력</span><span class="sxs-lookup"><span data-stu-id="790b5-132">INPUTS</span></span>

## <span data-ttu-id="790b5-133">출력</span><span class="sxs-lookup"><span data-stu-id="790b5-133">OUTPUTS</span></span>

## <span data-ttu-id="790b5-134">참고</span><span class="sxs-lookup"><span data-stu-id="790b5-134">NOTES</span></span>

## <span data-ttu-id="790b5-135">관련 링크</span><span class="sxs-lookup"><span data-stu-id="790b5-135">RELATED LINKS</span></span>

[<span data-ttu-id="790b5-136">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="790b5-136">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="790b5-137">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="790b5-137">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)
