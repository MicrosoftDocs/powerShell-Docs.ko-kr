---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 10/15/2020
schema: 2.0.0
ms.openlocfilehash: 5cb8ddbd06f8b7fdbadae0b7c738e26a68ff5c48
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605022"
---
# <span data-ttu-id="36975-101">Get-PSSubsystem</span><span class="sxs-lookup"><span data-stu-id="36975-101">Get-PSSubsystem</span></span>

## <span data-ttu-id="36975-102">개요</span><span class="sxs-lookup"><span data-stu-id="36975-102">SYNOPSIS</span></span>
<span data-ttu-id="36975-103">PowerShell에 등록 된 하위 시스템에 대 한 정보를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="36975-103">Retrieves information about the subsystems registered in PowerShell.</span></span>

## <span data-ttu-id="36975-104">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="36975-104">SYNTAX</span></span>

### <span data-ttu-id="36975-105">GetAllSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="36975-105">GetAllSet (Default)</span></span>

```
Get-PSSubsystem [<CommonParameters>]
```

### <span data-ttu-id="36975-106">GetByKindSet</span><span class="sxs-lookup"><span data-stu-id="36975-106">GetByKindSet</span></span>

```
Get-PSSubsystem -Kind <SubsystemKind> [<CommonParameters>]
```

### <span data-ttu-id="36975-107">GetByTypeSet</span><span class="sxs-lookup"><span data-stu-id="36975-107">GetByTypeSet</span></span>

```
Get-PSSubsystem -SubsystemType <Type> [<CommonParameters>]
```

## <span data-ttu-id="36975-108">설명</span><span class="sxs-lookup"><span data-stu-id="36975-108">DESCRIPTION</span></span>

<span data-ttu-id="36975-109">PowerShell에 등록 된 하위 시스템에 대 한 정보를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="36975-109">Retrieves information about the subsystems registered in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="36975-110">이는 실험적인 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="36975-110">This is an experimental feature.</span></span> <span data-ttu-id="36975-111">이 cmdlet은 `PSSubsystemPluginModel` 기능을 사용 하도록 설정한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36975-111">This cmdlet is only available when the `PSSubsystemPluginModel` feature is enabled.</span></span> <span data-ttu-id="36975-112">자세한 내용은 [실험적 기능 사용](/powershell/scripting/learn/experimental-features)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="36975-112">For more information, see [Using Experimental Features](/powershell/scripting/learn/experimental-features).</span></span>

<span data-ttu-id="36975-113">기능을 사용하면 `System.Management.Automation.dll` 구성 요소를 자체 어셈블리에 있는 개별 하위 시스템으로 분리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36975-113">The feature makes it possible to separate components of `System.Management.Automation.dll` into individual subsystems that reside in their own assembly.</span></span> <span data-ttu-id="36975-114">이렇게 분리하면 핵심 PowerShell 엔진의 디스크 공간이 줄어들고 이 구성 요소가 최소 PowerShell 설치에 대한 선택적 기능이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36975-114">This separation reduces the disk footprint of the core PowerShell engine and allows these components to become optional features for a minimal PowerShell installation.</span></span>

<span data-ttu-id="36975-115">현재 **CommandPredictor** 하위 시스템만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="36975-115">Currently, only the **CommandPredictor** subsystem is supported.</span></span> <span data-ttu-id="36975-116">이 하위 시스템은 사용자 지정 예측 플러그 인을 제공하는 데 PSReadLine 모듈과 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="36975-116">This subsystem is used along with the PSReadLine module to provide custom prediction plugins.</span></span> <span data-ttu-id="36975-117">나중에 **Job**, **CommandCompleter**, **Remoting** 및 기타 구성 요소를 `System.Management.Automation.dll` 외부의 하위 시스템 어셈블리로 분리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36975-117">In future, **Job**, **CommandCompleter**, **Remoting** and other components could be separated into subsystem assemblies outside of `System.Management.Automation.dll`.</span></span>

## <span data-ttu-id="36975-118">예제</span><span class="sxs-lookup"><span data-stu-id="36975-118">EXAMPLES</span></span>

### <span data-ttu-id="36975-119">예제 1-사용 가능한 모든 하위 시스템 표시</span><span class="sxs-lookup"><span data-stu-id="36975-119">Example 1 - Display all available subsystems</span></span>

```powershell
Get-PSSubsystem
```

```Output
Kind              SubsystemType     IsRegistered Implementations
----              -------------     ------------ ---------------
CommandPredictor  ICommandPredictor        False {}
```

### <span data-ttu-id="36975-120">예제 2-특정 종류의 사용 가능한 모든 하위 시스템 표시</span><span class="sxs-lookup"><span data-stu-id="36975-120">Example 2 - Display all available subsystems of a specific kind</span></span>

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

## <span data-ttu-id="36975-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="36975-121">PARAMETERS</span></span>

### <span data-ttu-id="36975-122">-종류</span><span class="sxs-lookup"><span data-stu-id="36975-122">-Kind</span></span>


<span data-ttu-id="36975-123">반환할 하위 시스템의 종류를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36975-123">Specifies the kind of subsystem to be returned.</span></span> <span data-ttu-id="36975-124">유효한 값은 `CommandPredictor` 입니다.</span><span class="sxs-lookup"><span data-stu-id="36975-124">Valid values are: `CommandPredictor`.</span></span>

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

### <span data-ttu-id="36975-125">-SubsystemType</span><span class="sxs-lookup"><span data-stu-id="36975-125">-SubsystemType</span></span>

<span data-ttu-id="36975-126">반환 될 하위 시스템의 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36975-126">Specifies the type of subsystem to be returned.</span></span>

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

### <span data-ttu-id="36975-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36975-127">CommonParameters</span></span>

<span data-ttu-id="36975-128">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="36975-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="36975-129">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="36975-129">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="36975-130">입력</span><span class="sxs-lookup"><span data-stu-id="36975-130">INPUTS</span></span>

### <span data-ttu-id="36975-131">System.object. 하위 시스템 종류</span><span class="sxs-lookup"><span data-stu-id="36975-131">System.Management.Automation.Subsystem.SubsystemKind</span></span>

### <span data-ttu-id="36975-132">System.Type</span><span class="sxs-lookup"><span data-stu-id="36975-132">System.Type</span></span>

## <span data-ttu-id="36975-133">출력</span><span class="sxs-lookup"><span data-stu-id="36975-133">OUTPUTS</span></span>

### <span data-ttu-id="36975-134">System.object. 하위 시스템</span><span class="sxs-lookup"><span data-stu-id="36975-134">System.Management.Automation.Subsystem.SubsystemInfo</span></span>

## <span data-ttu-id="36975-135">참고</span><span class="sxs-lookup"><span data-stu-id="36975-135">NOTES</span></span>

## <span data-ttu-id="36975-136">관련 링크</span><span class="sxs-lookup"><span data-stu-id="36975-136">RELATED LINKS</span></span>

[<span data-ttu-id="36975-137">about_experimental_features</span><span class="sxs-lookup"><span data-stu-id="36975-137">about_experimental_features</span></span>](about/about_experimental_features.md)

[<span data-ttu-id="36975-138">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="36975-138">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="36975-139">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="36975-139">Enable-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="36975-140">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="36975-140">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="36975-141">실험적 기능 사용</span><span class="sxs-lookup"><span data-stu-id="36975-141">Using Experimental Features</span></span>](/powershell/scripting/learn/experimental-features)
