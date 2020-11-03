---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspacedebug?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-RunspaceDebug
ms.openlocfilehash: 627b1446f37b951eb5455ca1d9b41ec5453e2cc7
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210753"
---
# <span data-ttu-id="aa50d-103">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="aa50d-103">Get-RunspaceDebug</span></span>

## <span data-ttu-id="aa50d-104">개요</span><span class="sxs-lookup"><span data-stu-id="aa50d-104">SYNOPSIS</span></span>
<span data-ttu-id="aa50d-105">Runspace 디버깅 옵션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa50d-105">Shows runspace debugging options.</span></span>

## <span data-ttu-id="aa50d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aa50d-106">SYNTAX</span></span>

### <span data-ttu-id="aa50d-107">RunspaceNameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="aa50d-107">RunspaceNameParameterSet (Default)</span></span>

```
Get-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="aa50d-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="aa50d-108">RunspaceParameterSet</span></span>

```
Get-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="aa50d-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="aa50d-109">RunspaceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="aa50d-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="aa50d-110">RunspaceInstanceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="aa50d-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="aa50d-111">ProcessNameParameterSet</span></span>

```
Get-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="aa50d-112">설명</span><span class="sxs-lookup"><span data-stu-id="aa50d-112">DESCRIPTION</span></span>

<span data-ttu-id="aa50d-113">`Get-RunspaceDebug`Cmdlet은 runspace 디버깅 옵션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa50d-113">The `Get-RunspaceDebug` cmdlet shows runspace debugging options.</span></span>

## <span data-ttu-id="aa50d-114">예제</span><span class="sxs-lookup"><span data-stu-id="aa50d-114">EXAMPLES</span></span>

### <span data-ttu-id="aa50d-115">1: 기본 runspace 디버거의 상태를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa50d-115">1: Show the state of the default runspace debugger</span></span>

```powershell
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="aa50d-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aa50d-116">PARAMETERS</span></span>

### <span data-ttu-id="aa50d-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="aa50d-117">-AppDomainName</span></span>

<span data-ttu-id="aa50d-118">PowerShell runspace를 호스트 하는 응용 프로그램 도메인의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="aa50d-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="aa50d-119">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="aa50d-119">-ProcessName</span></span>

<span data-ttu-id="aa50d-120">PowerShell runspace를 호스트 하는 프로세스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="aa50d-120">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="aa50d-121">-Runspace</span><span class="sxs-lookup"><span data-stu-id="aa50d-121">-Runspace</span></span>

<span data-ttu-id="aa50d-122">사용할 하나 이상의 **Runspace** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="aa50d-122">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="aa50d-123">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="aa50d-123">-RunspaceId</span></span>

<span data-ttu-id="aa50d-124">하나 이상의 **Runspace** Id 번호를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa50d-124">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="aa50d-125">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="aa50d-125">-RunspaceInstanceId</span></span>

<span data-ttu-id="aa50d-126">하나 이상의 **Runspace** guid를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa50d-126">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="aa50d-127">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="aa50d-127">-RunspaceName</span></span>

<span data-ttu-id="aa50d-128">사용할 하나 이상의 **Runspace** 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="aa50d-128">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="aa50d-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aa50d-129">CommonParameters</span></span>

<span data-ttu-id="aa50d-130">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aa50d-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aa50d-131">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa50d-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aa50d-132">입력</span><span class="sxs-lookup"><span data-stu-id="aa50d-132">INPUTS</span></span>

## <span data-ttu-id="aa50d-133">출력</span><span class="sxs-lookup"><span data-stu-id="aa50d-133">OUTPUTS</span></span>

## <span data-ttu-id="aa50d-134">참고</span><span class="sxs-lookup"><span data-stu-id="aa50d-134">NOTES</span></span>

## <span data-ttu-id="aa50d-135">관련 링크</span><span class="sxs-lookup"><span data-stu-id="aa50d-135">RELATED LINKS</span></span>

[<span data-ttu-id="aa50d-136">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="aa50d-136">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="aa50d-137">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="aa50d-137">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)
