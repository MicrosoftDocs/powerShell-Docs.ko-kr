---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-runspacedebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-RunspaceDebug
ms.openlocfilehash: 26ab9b9135eedafa0238eab5c07aa7abb7880ed4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601851"
---
# <span data-ttu-id="2b58e-102">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="2b58e-102">Enable-RunspaceDebug</span></span>

## <span data-ttu-id="2b58e-103">개요</span><span class="sxs-lookup"><span data-stu-id="2b58e-103">SYNOPSIS</span></span>
<span data-ttu-id="2b58e-104">디버거가 연결 될 때까지 중단점이 유지 되는 runspace에서 디버깅을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b58e-104">Enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="2b58e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2b58e-105">SYNTAX</span></span>

### <span data-ttu-id="2b58e-106">RunspaceNameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="2b58e-106">RunspaceNameParameterSet (Default)</span></span>

```
Enable-RunspaceDebug [-BreakAll] [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="2b58e-107">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="2b58e-107">RunspaceParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="2b58e-108">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="2b58e-108">RunspaceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="2b58e-109">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="2b58e-109">RunspaceInstanceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="2b58e-110">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="2b58e-110">ProcessNameParameterSet</span></span>

```
Enable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="2b58e-111">설명</span><span class="sxs-lookup"><span data-stu-id="2b58e-111">DESCRIPTION</span></span>

<span data-ttu-id="2b58e-112">`Enable-RunspaceDebug`Cmdlet을 사용 하면 디버거가 연결 될 때까지 중단점이 유지 되는 runspace에서 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b58e-112">The `Enable-RunspaceDebug` cmdlet enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="2b58e-113">예제</span><span class="sxs-lookup"><span data-stu-id="2b58e-113">EXAMPLES</span></span>

### <span data-ttu-id="2b58e-114">1: 기본 runspace 디버거를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="2b58e-114">1: Enable the default runspace debugger</span></span>

```powershell
Enable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            True       False
```

## <span data-ttu-id="2b58e-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2b58e-115">PARAMETERS</span></span>

### <span data-ttu-id="2b58e-116">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="2b58e-116">-AppDomainName</span></span>

<span data-ttu-id="2b58e-117">PowerShell runspace를 호스트 하는 응용 프로그램 도메인의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2b58e-117">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="2b58e-118">-간</span><span class="sxs-lookup"><span data-stu-id="2b58e-118">-BreakAll</span></span>

<span data-ttu-id="2b58e-119">디버거가 현재 연결 되어 있는지 여부에 관계 없이 Runspace의 실행 중인 명령이 나 스크립트를 단계 모드에서 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b58e-119">Causes any running command or script in the Runspace to stop in step mode, regardless of whether a debugger is currently attached.</span></span> <span data-ttu-id="2b58e-120">디버거를 연결 하 여 현재 중지 지점을 디버그할 때까지 스크립트 또는 명령이 중지 된 상태로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b58e-120">The script or command will remain stopped until a debugger is attached to debug the current stop point.</span></span>

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

### <span data-ttu-id="2b58e-121">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="2b58e-121">-ProcessName</span></span>

<span data-ttu-id="2b58e-122">PowerShell runspace를 호스트 하는 프로세스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2b58e-122">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="2b58e-123">-Runspace</span><span class="sxs-lookup"><span data-stu-id="2b58e-123">-Runspace</span></span>

<span data-ttu-id="2b58e-124">사용할 하나 이상의 **Runspace** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="2b58e-124">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="2b58e-125">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="2b58e-125">-RunspaceId</span></span>

<span data-ttu-id="2b58e-126">하나 이상의 **Runspace** Id 번호를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b58e-126">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="2b58e-127">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="2b58e-127">-RunspaceInstanceId</span></span>

<span data-ttu-id="2b58e-128">하나 이상의 **Runspace** guid를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b58e-128">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="2b58e-129">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="2b58e-129">-RunspaceName</span></span>

<span data-ttu-id="2b58e-130">사용할 하나 이상의 **Runspace** 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2b58e-130">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="2b58e-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2b58e-131">CommonParameters</span></span>

<span data-ttu-id="2b58e-132">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2b58e-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2b58e-133">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2b58e-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2b58e-134">입력</span><span class="sxs-lookup"><span data-stu-id="2b58e-134">INPUTS</span></span>

## <span data-ttu-id="2b58e-135">출력</span><span class="sxs-lookup"><span data-stu-id="2b58e-135">OUTPUTS</span></span>

## <span data-ttu-id="2b58e-136">참고</span><span class="sxs-lookup"><span data-stu-id="2b58e-136">NOTES</span></span>

## <span data-ttu-id="2b58e-137">관련 링크</span><span class="sxs-lookup"><span data-stu-id="2b58e-137">RELATED LINKS</span></span>

[<span data-ttu-id="2b58e-138">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="2b58e-138">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="2b58e-139">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="2b58e-139">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)

