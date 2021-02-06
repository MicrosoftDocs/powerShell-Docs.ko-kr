---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Runspace
ms.openlocfilehash: 34843894cb6253e3d8e89072cf79cb9237d4fc19
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600448"
---
# <span data-ttu-id="3fe95-102">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="3fe95-102">Get-Runspace</span></span>

## <span data-ttu-id="3fe95-103">개요</span><span class="sxs-lookup"><span data-stu-id="3fe95-103">SYNOPSIS</span></span>
<span data-ttu-id="3fe95-104">PowerShell 호스트 프로세스 내의 활성 runspace를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3fe95-104">Gets active runspaces within a PowerShell host process.</span></span>

## <span data-ttu-id="3fe95-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3fe95-105">SYNTAX</span></span>

### <span data-ttu-id="3fe95-106">NameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="3fe95-106">NameParameterSet (Default)</span></span>

```
Get-Runspace [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="3fe95-107">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="3fe95-107">IdParameterSet</span></span>

```
Get-Runspace [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="3fe95-108">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="3fe95-108">InstanceIdParameterSet</span></span>

```
Get-Runspace [-InstanceId] <Guid[]> [<CommonParameters>]
```

## <span data-ttu-id="3fe95-109">설명</span><span class="sxs-lookup"><span data-stu-id="3fe95-109">DESCRIPTION</span></span>

<span data-ttu-id="3fe95-110">`Get-Runspace`Cmdlet은 PowerShell 호스트 프로세스에서 활성 runspace를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3fe95-110">The `Get-Runspace` cmdlet gets active runspaces in a PowerShell host process.</span></span>

## <span data-ttu-id="3fe95-111">예제</span><span class="sxs-lookup"><span data-stu-id="3fe95-111">EXAMPLES</span></span>

### <span data-ttu-id="3fe95-112">예제 1: runspace 가져오기</span><span class="sxs-lookup"><span data-stu-id="3fe95-112">Example 1: Get runspaces</span></span>

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

### <span data-ttu-id="3fe95-113">예제 2: Id로 runspace 가져오기</span><span class="sxs-lookup"><span data-stu-id="3fe95-113">Example 2: Get runspace by Id</span></span>

```powershell
Get-Runspace -Id 2
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  2 Runspace2       localhost       Local         Opened        Available
```

### <span data-ttu-id="3fe95-114">예제 3: 이름으로 runspace 가져오기</span><span class="sxs-lookup"><span data-stu-id="3fe95-114">Example 3: Get runspace by Name</span></span>

```powershell
Get-Runspace -Name Runspace1
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

### <span data-ttu-id="3fe95-115">예제 4: InstanceId로 runspace 가져오기</span><span class="sxs-lookup"><span data-stu-id="3fe95-115">Example 4: Get runspace by InstanceId</span></span>

<span data-ttu-id="3fe95-116">이 예제에서는 매개 변수를 사용 하 여 사용 가능한 runspace를 식별 하 `Name` 고 반환 개체를 변수에 저장 `$activeRunspace` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fe95-116">In this example, we identify an available runspace using the `Name` parameter and store the return object to the variable `$activeRunspace`.</span></span> <span data-ttu-id="3fe95-117">이렇게 하면 이후 실행에서 **Runspace** 의 속성을 사용할 수 있습니다 `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="3fe95-117">This allows you to use the properties of the **Runspace** in subsequent runs of `Get-Runspace`.</span></span>

```powershell
$activeRunspace = Get-Runspace -Name Runspace1
Get-Runspace -InstanceId $activeRunspace.InstanceId
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

## <span data-ttu-id="3fe95-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3fe95-118">PARAMETERS</span></span>

### <span data-ttu-id="3fe95-119">-Id</span><span class="sxs-lookup"><span data-stu-id="3fe95-119">-Id</span></span>

<span data-ttu-id="3fe95-120">Runspace의 Id를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fe95-120">Specifies the Id of a runspace</span></span>

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

### <span data-ttu-id="3fe95-121">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="3fe95-121">-InstanceId</span></span>

<span data-ttu-id="3fe95-122">실행 중인 작업의 인스턴스 ID GUID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fe95-122">Specifies the instance ID GUID of a running job.</span></span>

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

### <span data-ttu-id="3fe95-123">-Name</span><span class="sxs-lookup"><span data-stu-id="3fe95-123">-Name</span></span>

<span data-ttu-id="3fe95-124">Runspace의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fe95-124">Specifies the Name of a runspace</span></span>

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

### <span data-ttu-id="3fe95-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3fe95-125">CommonParameters</span></span>

<span data-ttu-id="3fe95-126">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3fe95-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3fe95-127">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3fe95-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3fe95-128">입력</span><span class="sxs-lookup"><span data-stu-id="3fe95-128">INPUTS</span></span>

## <span data-ttu-id="3fe95-129">출력</span><span class="sxs-lookup"><span data-stu-id="3fe95-129">OUTPUTS</span></span>

### <span data-ttu-id="3fe95-130">Runspace입니다.</span><span class="sxs-lookup"><span data-stu-id="3fe95-130">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="3fe95-131">명령의 결과를로 파이프 할 수 있습니다 `Get-Runspace` `Debug-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="3fe95-131">You can pipe the results of a `Get-Runspace` command to `Debug-Runspace`.</span></span>

## <span data-ttu-id="3fe95-132">참고</span><span class="sxs-lookup"><span data-stu-id="3fe95-132">NOTES</span></span>

## <span data-ttu-id="3fe95-133">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3fe95-133">RELATED LINKS</span></span>

[<span data-ttu-id="3fe95-134">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="3fe95-134">Debug-Runspace</span></span>](Debug-Runspace.md)

