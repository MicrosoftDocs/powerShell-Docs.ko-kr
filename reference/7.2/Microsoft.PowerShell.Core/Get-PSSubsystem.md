---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssubsystem?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSubsystem
ms.openlocfilehash: 19129eb8a0b478d10fdbf1e35f15b7f86969b5fb
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194999"
---
# <span data-ttu-id="88840-102">Get-PSSubsystem</span><span class="sxs-lookup"><span data-stu-id="88840-102">Get-PSSubsystem</span></span>

## <span data-ttu-id="88840-103">개요</span><span class="sxs-lookup"><span data-stu-id="88840-103">SYNOPSIS</span></span>
<span data-ttu-id="88840-104">PowerShell에 등록 된 하위 시스템에 대 한 정보를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="88840-104">Retrieves information about the subsystems registered in PowerShell.</span></span>

## <span data-ttu-id="88840-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="88840-105">SYNTAX</span></span>

### <span data-ttu-id="88840-106">GetAllSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="88840-106">GetAllSet (Default)</span></span>

```
Get-PSSubsystem [<CommonParameters>]
```

### <span data-ttu-id="88840-107">GetByKindSet</span><span class="sxs-lookup"><span data-stu-id="88840-107">GetByKindSet</span></span>

```
Get-PSSubsystem -Kind <SubsystemKind> [<CommonParameters>]
```

### <span data-ttu-id="88840-108">GetByTypeSet</span><span class="sxs-lookup"><span data-stu-id="88840-108">GetByTypeSet</span></span>

```
Get-PSSubsystem -SubsystemType <Type> [<CommonParameters>]
```

## <span data-ttu-id="88840-109">설명</span><span class="sxs-lookup"><span data-stu-id="88840-109">DESCRIPTION</span></span>

<span data-ttu-id="88840-110">PowerShell에 등록 된 하위 시스템에 대 한 정보를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="88840-110">Retrieves information about the subsystems registered in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="88840-111">이는 실험적인 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="88840-111">This is an experimental feature.</span></span> <span data-ttu-id="88840-112">이 cmdlet은 `PSSubsystemPluginModel` 기능을 사용 하도록 설정한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88840-112">This cmdlet is only available when the `PSSubsystemPluginModel` feature is enabled.</span></span> <span data-ttu-id="88840-113">자세한 내용은 [실험적 기능 사용](/powershell/scripting/learn/experimental-features)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88840-113">For more information, see [Using Experimental Features](/powershell/scripting/learn/experimental-features).</span></span>

<span data-ttu-id="88840-114">기능을 사용하면 `System.Management.Automation.dll` 구성 요소를 자체 어셈블리에 있는 개별 하위 시스템으로 분리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88840-114">The feature makes it possible to separate components of `System.Management.Automation.dll` into individual subsystems that reside in their own assembly.</span></span> <span data-ttu-id="88840-115">이렇게 분리하면 핵심 PowerShell 엔진의 디스크 공간이 줄어들고 이 구성 요소가 최소 PowerShell 설치에 대한 선택적 기능이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88840-115">This separation reduces the disk footprint of the core PowerShell engine and allows these components to become optional features for a minimal PowerShell installation.</span></span>

<span data-ttu-id="88840-116">현재 **CommandPredictor** 하위 시스템만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="88840-116">Currently, only the **CommandPredictor** subsystem is supported.</span></span> <span data-ttu-id="88840-117">이 하위 시스템은 사용자 지정 예측 플러그 인을 제공하는 데 PSReadLine 모듈과 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="88840-117">This subsystem is used along with the PSReadLine module to provide custom prediction plugins.</span></span> <span data-ttu-id="88840-118">나중에 **Job**, **CommandCompleter**, **Remoting** 및 기타 구성 요소를 `System.Management.Automation.dll` 외부의 하위 시스템 어셈블리로 분리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88840-118">In future, **Job**, **CommandCompleter**, **Remoting** and other components could be separated into subsystem assemblies outside of `System.Management.Automation.dll`.</span></span>

## <span data-ttu-id="88840-119">예제</span><span class="sxs-lookup"><span data-stu-id="88840-119">EXAMPLES</span></span>

### <span data-ttu-id="88840-120">예제 1-사용 가능한 모든 하위 시스템 표시</span><span class="sxs-lookup"><span data-stu-id="88840-120">Example 1 - Display all available subsystems</span></span>

```powershell
Get-PSSubsystem
```

```Output
Kind              SubsystemType     IsRegistered Implementations
----              -------------     ------------ ---------------
CommandPredictor  ICommandPredictor        False {}
```

### <span data-ttu-id="88840-121">예제 2-특정 종류의 사용 가능한 모든 하위 시스템 표시</span><span class="sxs-lookup"><span data-stu-id="88840-121">Example 2 - Display all available subsystems of a specific kind</span></span>

```powershell
PS> Get-PSSubsystem -Kind CommandPredictor | Format-List
```

```Output
Kind                      : CommandPredictor
SubsystemType             : System.Management.Automation.Subsystem.ICommandPredictor
AllowUnregistration       : True
AllowMultipleRegistration : True
RequiredCmdlets           : {}
RequiredFunctions         : {}
IsRegistered              : False
Implementations           : {}
```

## <span data-ttu-id="88840-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="88840-122">PARAMETERS</span></span>

### <span data-ttu-id="88840-123">-종류</span><span class="sxs-lookup"><span data-stu-id="88840-123">-Kind</span></span>


<span data-ttu-id="88840-124">반환할 하위 시스템의 종류를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88840-124">Specifies the kind of subsystem to be returned.</span></span> <span data-ttu-id="88840-125">유효한 값은 `CommandPredictor` 입니다.</span><span class="sxs-lookup"><span data-stu-id="88840-125">Valid values are: `CommandPredictor`.</span></span>

```yaml
Type: System.Management.Automation.Subsystem.SubsystemKind
Parameter Sets: GetByKindSet
Aliases:
Accepted values: CommandPredictor

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="88840-126">-SubsystemType</span><span class="sxs-lookup"><span data-stu-id="88840-126">-SubsystemType</span></span>

<span data-ttu-id="88840-127">반환 될 하위 시스템의 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88840-127">Specifies the type of subsystem to be returned.</span></span>

```yaml
Type: System.Type
Parameter Sets: GetByTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="88840-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="88840-128">CommonParameters</span></span>

<span data-ttu-id="88840-129">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="88840-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="88840-130">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88840-130">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="88840-131">입력</span><span class="sxs-lookup"><span data-stu-id="88840-131">INPUTS</span></span>

### <span data-ttu-id="88840-132">System.object. 하위 시스템 종류</span><span class="sxs-lookup"><span data-stu-id="88840-132">System.Management.Automation.Subsystem.SubsystemKind</span></span>

### <span data-ttu-id="88840-133">System.Type</span><span class="sxs-lookup"><span data-stu-id="88840-133">System.Type</span></span>

## <span data-ttu-id="88840-134">출력</span><span class="sxs-lookup"><span data-stu-id="88840-134">OUTPUTS</span></span>

### <span data-ttu-id="88840-135">System.object. 하위 시스템</span><span class="sxs-lookup"><span data-stu-id="88840-135">System.Management.Automation.Subsystem.SubsystemInfo</span></span>

## <span data-ttu-id="88840-136">참고</span><span class="sxs-lookup"><span data-stu-id="88840-136">NOTES</span></span>

## <span data-ttu-id="88840-137">관련 링크</span><span class="sxs-lookup"><span data-stu-id="88840-137">RELATED LINKS</span></span>

[<span data-ttu-id="88840-138">about_experimental_features</span><span class="sxs-lookup"><span data-stu-id="88840-138">about_experimental_features</span></span>](about/about_experimental_features.md)

[<span data-ttu-id="88840-139">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="88840-139">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="88840-140">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="88840-140">Enable-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="88840-141">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="88840-141">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="88840-142">실험적 기능 사용</span><span class="sxs-lookup"><span data-stu-id="88840-142">Using Experimental Features</span></span>](/powershell/scripting/learn/experimental-features)
