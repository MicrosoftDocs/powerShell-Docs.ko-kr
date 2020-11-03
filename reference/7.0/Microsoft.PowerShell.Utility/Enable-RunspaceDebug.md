---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-runspacedebug?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-RunspaceDebug
ms.openlocfilehash: dc33195db1ddfb0c2b3e87aaab44845e9f6580a7
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211490"
---
# <span data-ttu-id="919f1-103">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="919f1-103">Enable-RunspaceDebug</span></span>

## <span data-ttu-id="919f1-104">개요</span><span class="sxs-lookup"><span data-stu-id="919f1-104">SYNOPSIS</span></span>
<span data-ttu-id="919f1-105">디버거가 연결 될 때까지 중단점이 유지 되는 runspace에서 디버깅을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="919f1-105">Enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="919f1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="919f1-106">SYNTAX</span></span>

### <span data-ttu-id="919f1-107">RunspaceNameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="919f1-107">RunspaceNameParameterSet (Default)</span></span>

```
Enable-RunspaceDebug [-BreakAll] [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="919f1-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="919f1-108">RunspaceParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="919f1-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="919f1-109">RunspaceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="919f1-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="919f1-110">RunspaceInstanceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="919f1-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="919f1-111">ProcessNameParameterSet</span></span>

```
Enable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="919f1-112">설명</span><span class="sxs-lookup"><span data-stu-id="919f1-112">DESCRIPTION</span></span>

<span data-ttu-id="919f1-113">`Enable-RunspaceDebug`Cmdlet을 사용 하면 디버거가 연결 될 때까지 중단점이 유지 되는 runspace에서 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="919f1-113">The `Enable-RunspaceDebug` cmdlet enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="919f1-114">예제</span><span class="sxs-lookup"><span data-stu-id="919f1-114">EXAMPLES</span></span>

### <span data-ttu-id="919f1-115">1: 기본 runspace 디버거를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="919f1-115">1: Enable the default runspace debugger</span></span>

```powershell
Enable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            True       False
```

## <span data-ttu-id="919f1-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="919f1-116">PARAMETERS</span></span>

### <span data-ttu-id="919f1-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="919f1-117">-AppDomainName</span></span>

<span data-ttu-id="919f1-118">PowerShell runspace를 호스트 하는 응용 프로그램 도메인의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="919f1-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="919f1-119">-간</span><span class="sxs-lookup"><span data-stu-id="919f1-119">-BreakAll</span></span>

<span data-ttu-id="919f1-120">디버거가 현재 연결 되어 있는지 여부에 관계 없이 Runspace의 실행 중인 명령이 나 스크립트를 단계 모드에서 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="919f1-120">Causes any running command or script in the Runspace to stop in step mode, regardless of whether a debugger is currently attached.</span></span> <span data-ttu-id="919f1-121">디버거를 연결 하 여 현재 중지 지점을 디버그할 때까지 스크립트 또는 명령이 중지 된 상태로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="919f1-121">The script or command will remain stopped until a debugger is attached to debug the current stop point.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: RunspaceNameParameterSet, RunspaceParameterSet, RunspaceIdParameterSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="919f1-122">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="919f1-122">-ProcessName</span></span>

<span data-ttu-id="919f1-123">PowerShell runspace를 호스트 하는 프로세스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="919f1-123">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="919f1-124">-Runspace</span><span class="sxs-lookup"><span data-stu-id="919f1-124">-Runspace</span></span>

<span data-ttu-id="919f1-125">사용할 하나 이상의 **Runspace** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="919f1-125">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="919f1-126">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="919f1-126">-RunspaceId</span></span>

<span data-ttu-id="919f1-127">하나 이상의 **Runspace** Id 번호를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="919f1-127">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="919f1-128">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="919f1-128">-RunspaceInstanceId</span></span>

<span data-ttu-id="919f1-129">하나 이상의 **Runspace** guid를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="919f1-129">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="919f1-130">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="919f1-130">-RunspaceName</span></span>

<span data-ttu-id="919f1-131">사용할 하나 이상의 **Runspace** 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="919f1-131">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="919f1-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="919f1-132">CommonParameters</span></span>

<span data-ttu-id="919f1-133">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="919f1-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="919f1-134">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="919f1-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="919f1-135">입력</span><span class="sxs-lookup"><span data-stu-id="919f1-135">INPUTS</span></span>

## <span data-ttu-id="919f1-136">출력</span><span class="sxs-lookup"><span data-stu-id="919f1-136">OUTPUTS</span></span>

## <span data-ttu-id="919f1-137">참고</span><span class="sxs-lookup"><span data-stu-id="919f1-137">NOTES</span></span>

## <span data-ttu-id="919f1-138">관련 링크</span><span class="sxs-lookup"><span data-stu-id="919f1-138">RELATED LINKS</span></span>

[<span data-ttu-id="919f1-139">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="919f1-139">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="919f1-140">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="919f1-140">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)
