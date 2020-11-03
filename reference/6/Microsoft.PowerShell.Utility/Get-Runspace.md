---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Runspace
ms.openlocfilehash: 12530b9cf30b34598dfc3a049f5553920abecc4f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216642"
---
# <span data-ttu-id="84a70-103">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="84a70-103">Get-Runspace</span></span>

## <span data-ttu-id="84a70-104">개요</span><span class="sxs-lookup"><span data-stu-id="84a70-104">SYNOPSIS</span></span>
<span data-ttu-id="84a70-105">PowerShell 호스트 프로세스 내의 활성 runspace를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="84a70-105">Gets active runspaces within a PowerShell host process.</span></span>

## <span data-ttu-id="84a70-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="84a70-106">SYNTAX</span></span>

### <span data-ttu-id="84a70-107">NameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="84a70-107">NameParameterSet (Default)</span></span>

```
Get-Runspace [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="84a70-108">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="84a70-108">IdParameterSet</span></span>

```
Get-Runspace [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="84a70-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="84a70-109">InstanceIdParameterSet</span></span>

```
Get-Runspace [-InstanceId] <Guid[]> [<CommonParameters>]
```

## <span data-ttu-id="84a70-110">설명</span><span class="sxs-lookup"><span data-stu-id="84a70-110">DESCRIPTION</span></span>

<span data-ttu-id="84a70-111">`Get-Runspace`Cmdlet은 PowerShell 호스트 프로세스에서 활성 runspace를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="84a70-111">The `Get-Runspace` cmdlet gets active runspaces in a PowerShell host process.</span></span>

## <span data-ttu-id="84a70-112">예제</span><span class="sxs-lookup"><span data-stu-id="84a70-112">EXAMPLES</span></span>

### <span data-ttu-id="84a70-113">예제 1: runspace 가져오기</span><span class="sxs-lookup"><span data-stu-id="84a70-113">Example 1: Get runspaces</span></span>

```powershell
Get-Runspace
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
  2 Runspace2       localhost       Local         Opened        Available
  3 Runspace3       localhost       Local         Opened        Available
```

### <span data-ttu-id="84a70-114">예제 2: Id로 runspace 가져오기</span><span class="sxs-lookup"><span data-stu-id="84a70-114">Example 2: Get runspace by Id</span></span>

```powershell
Get-Runspace -Id 2
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  2 Runspace2       localhost       Local         Opened        Available
```

### <span data-ttu-id="84a70-115">예제 3: 이름으로 runspace 가져오기</span><span class="sxs-lookup"><span data-stu-id="84a70-115">Example 3: Get runspace by Name</span></span>

```powershell
Get-Runspace -Name Runspace1
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

### <span data-ttu-id="84a70-116">예제 4: InstanceId로 runspace 가져오기</span><span class="sxs-lookup"><span data-stu-id="84a70-116">Example 4: Get runspace by InstanceId</span></span>

<span data-ttu-id="84a70-117">이 예제에서는 매개 변수를 사용 하 여 사용 가능한 runspace를 식별 하 `Name` 고 반환 개체를 변수에 저장 `$activeRunspace` 합니다.</span><span class="sxs-lookup"><span data-stu-id="84a70-117">In this example, we identify an available runspace using the `Name` parameter and store the return object to the variable `$activeRunspace`.</span></span> <span data-ttu-id="84a70-118">이렇게 하면 이후 실행에서 **Runspace** 의 속성을 사용할 수 있습니다 `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="84a70-118">This allows you to use the properties of the **Runspace** in subsequent runs of `Get-Runspace`.</span></span>

```powershell
$activeRunspace = Get-Runspace -Name Runspace1
Get-Runspace -InstanceId $activeRunspace.InstanceId
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

## <span data-ttu-id="84a70-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="84a70-119">PARAMETERS</span></span>

### <span data-ttu-id="84a70-120">-Id</span><span class="sxs-lookup"><span data-stu-id="84a70-120">-Id</span></span>

<span data-ttu-id="84a70-121">Runspace의 Id를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="84a70-121">Specifies the Id of a runspace</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="84a70-122">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="84a70-122">-InstanceId</span></span>

<span data-ttu-id="84a70-123">실행 중인 작업의 인스턴스 ID GUID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="84a70-123">Specifies the instance ID GUID of a running job.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="84a70-124">-Name</span><span class="sxs-lookup"><span data-stu-id="84a70-124">-Name</span></span>

<span data-ttu-id="84a70-125">Runspace의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="84a70-125">Specifies the Name of a runspace</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="84a70-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="84a70-126">CommonParameters</span></span>

<span data-ttu-id="84a70-127">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="84a70-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="84a70-128">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="84a70-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="84a70-129">입력</span><span class="sxs-lookup"><span data-stu-id="84a70-129">INPUTS</span></span>

## <span data-ttu-id="84a70-130">출력</span><span class="sxs-lookup"><span data-stu-id="84a70-130">OUTPUTS</span></span>

### <span data-ttu-id="84a70-131">Runspace입니다.</span><span class="sxs-lookup"><span data-stu-id="84a70-131">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="84a70-132">명령의 결과를로 파이프 할 수 있습니다 `Get-Runspace` `Debug-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="84a70-132">You can pipe the results of a `Get-Runspace` command to `Debug-Runspace`.</span></span>

## <span data-ttu-id="84a70-133">참고</span><span class="sxs-lookup"><span data-stu-id="84a70-133">NOTES</span></span>

## <span data-ttu-id="84a70-134">관련 링크</span><span class="sxs-lookup"><span data-stu-id="84a70-134">RELATED LINKS</span></span>

[<span data-ttu-id="84a70-135">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="84a70-135">Debug-Runspace</span></span>](Debug-Runspace.md)
