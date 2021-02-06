---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspacedebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-RunspaceDebug
ms.openlocfilehash: a77695fe32345fda8e6a0284cd29becb432a4273
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599767"
---
# <span data-ttu-id="c312a-102">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="c312a-102">Get-RunspaceDebug</span></span>

## <span data-ttu-id="c312a-103">개요</span><span class="sxs-lookup"><span data-stu-id="c312a-103">SYNOPSIS</span></span>
<span data-ttu-id="c312a-104">Runspace 디버깅 옵션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c312a-104">Shows runspace debugging options.</span></span>

## <span data-ttu-id="c312a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c312a-105">SYNTAX</span></span>

### <span data-ttu-id="c312a-106">RunspaceNameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="c312a-106">RunspaceNameParameterSet (Default)</span></span>

```
Get-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="c312a-107">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="c312a-107">RunspaceParameterSet</span></span>

```
Get-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="c312a-108">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="c312a-108">RunspaceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="c312a-109">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="c312a-109">RunspaceInstanceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="c312a-110">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="c312a-110">ProcessNameParameterSet</span></span>

```
Get-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="c312a-111">설명</span><span class="sxs-lookup"><span data-stu-id="c312a-111">DESCRIPTION</span></span>

<span data-ttu-id="c312a-112">`Get-RunspaceDebug`Cmdlet은 runspace 디버깅 옵션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c312a-112">The `Get-RunspaceDebug` cmdlet shows runspace debugging options.</span></span>

## <span data-ttu-id="c312a-113">예제</span><span class="sxs-lookup"><span data-stu-id="c312a-113">EXAMPLES</span></span>

### <span data-ttu-id="c312a-114">1: 기본 runspace 디버거의 상태를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c312a-114">1: Show the state of the default runspace debugger</span></span>

```powershell
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="c312a-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c312a-115">PARAMETERS</span></span>

### <span data-ttu-id="c312a-116">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="c312a-116">-AppDomainName</span></span>

<span data-ttu-id="c312a-117">PowerShell runspace를 호스트 하는 응용 프로그램 도메인의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c312a-117">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="c312a-118">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="c312a-118">-ProcessName</span></span>

<span data-ttu-id="c312a-119">PowerShell runspace를 호스트 하는 프로세스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c312a-119">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="c312a-120">-Runspace</span><span class="sxs-lookup"><span data-stu-id="c312a-120">-Runspace</span></span>

<span data-ttu-id="c312a-121">사용할 하나 이상의 **Runspace** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="c312a-121">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="c312a-122">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="c312a-122">-RunspaceId</span></span>

<span data-ttu-id="c312a-123">하나 이상의 **Runspace** Id 번호를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c312a-123">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="c312a-124">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="c312a-124">-RunspaceInstanceId</span></span>

<span data-ttu-id="c312a-125">하나 이상의 **Runspace** guid를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c312a-125">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="c312a-126">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="c312a-126">-RunspaceName</span></span>

<span data-ttu-id="c312a-127">사용할 하나 이상의 **Runspace** 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c312a-127">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="c312a-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c312a-128">CommonParameters</span></span>

<span data-ttu-id="c312a-129">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c312a-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c312a-130">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c312a-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c312a-131">입력</span><span class="sxs-lookup"><span data-stu-id="c312a-131">INPUTS</span></span>

## <span data-ttu-id="c312a-132">출력</span><span class="sxs-lookup"><span data-stu-id="c312a-132">OUTPUTS</span></span>

## <span data-ttu-id="c312a-133">참고</span><span class="sxs-lookup"><span data-stu-id="c312a-133">NOTES</span></span>

## <span data-ttu-id="c312a-134">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c312a-134">RELATED LINKS</span></span>

[<span data-ttu-id="c312a-135">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="c312a-135">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="c312a-136">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="c312a-136">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

