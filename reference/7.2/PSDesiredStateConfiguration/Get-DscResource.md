---
external help file: PSDesiredStateConfiguration-help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscResource
ms.openlocfilehash: dbc036562da0172dc4406f169891d2cd1c5e4098
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599755"
---
# <span data-ttu-id="72b91-102">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="72b91-102">Get-DscResource</span></span>

## <span data-ttu-id="72b91-103">개요</span><span class="sxs-lookup"><span data-stu-id="72b91-103">SYNOPSIS</span></span>
<span data-ttu-id="72b91-104">컴퓨터에 있는 DSC (Desired State Configuration) 리소스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="72b91-104">Gets Desired State Configuration (DSC) resources present on the computer.</span></span>

## <span data-ttu-id="72b91-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="72b91-105">SYNTAX</span></span>

```
Get-DscResource [[-Name] <String[]>] [[-Module] <Object>] [-Syntax] [<CommonParameters>]
```

## <span data-ttu-id="72b91-106">설명</span><span class="sxs-lookup"><span data-stu-id="72b91-106">DESCRIPTION</span></span>

<span data-ttu-id="72b91-107">`Get-DscResource`Cmdlet은 컴퓨터에 있는 POWERSHELL DSC 리소스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="72b91-107">The `Get-DscResource` cmdlet retrieves the PowerShell DSC resources present on the computer.</span></span> <span data-ttu-id="72b91-108">이 cmdlet은 PSModulePath에 설치 된 리소스만 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="72b91-108">This cmdlet discovers only the resources installed in the PSModulePath.</span></span> <span data-ttu-id="72b91-109">사용자가 만든 기본 제공 및 사용자 지정 공급자에 대 한 세부 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="72b91-109">It shows the details about built-in and custom providers, which are created by the user.</span></span> <span data-ttu-id="72b91-110">또한이 cmdlet은 모듈로 패키지 되거나 런타임에 생성 되는 다른 구성 인 복합 리소스에 대 한 세부 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="72b91-110">This cmdlet also shows details about composite resources, which are other configurations that are packaged as module or created at run time in the session.</span></span>

## <span data-ttu-id="72b91-111">예제</span><span class="sxs-lookup"><span data-stu-id="72b91-111">EXAMPLES</span></span>

### <span data-ttu-id="72b91-112">예제 1: 로컬 컴퓨터의 모든 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="72b91-112">Example 1: Get all resources on the local computer</span></span>

```powershell
Get-DscResource
```

<span data-ttu-id="72b91-113">이 명령은 로컬 컴퓨터의 모든 리소스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="72b91-113">This command gets all the resources on the local computer.</span></span>

### <span data-ttu-id="72b91-114">예제 2: 이름을 지정 하 여 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="72b91-114">Example 2: Get a resource by specifying the name</span></span>

```powershell
Get-DscResource -Name "WindowsFeature"
```

<span data-ttu-id="72b91-115">이 명령은 WindowsFeature 리소스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="72b91-115">This command gets the WindowsFeature resource.</span></span>

### <span data-ttu-id="72b91-116">예제 3: 모듈에서 모든 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="72b91-116">Example 3: Get all the resources from a module</span></span>

```powershell
Get-DscResource -Module "xHyper-V"
```

<span data-ttu-id="72b91-117">이 명령은 xHyper 모듈에서 모든 리소스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="72b91-117">This command gets all the resources from the xHyper-V module.</span></span>

### <span data-ttu-id="72b91-118">예제 4: 와일드 카드 문자를 사용 하 여 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="72b91-118">Example 4: Get a resource by using wildcard characters</span></span>

```powershell
Get-DscResource -Name P*,r*
```

<span data-ttu-id="72b91-119">이 명령은 **Name** 매개 변수로 지정 된 와일드 카드 패턴과 일치 하는 모든 리소스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="72b91-119">This command gets all resources that match the wildcard pattern specified by the **Name** parameter.</span></span>

### <span data-ttu-id="72b91-120">예 5: 리소스 구문 가져오기</span><span class="sxs-lookup"><span data-stu-id="72b91-120">Example 5: Get a resource syntax</span></span>

```powershell
Get-DscResource -Name "WindowsFeature" -Syntax
```

<span data-ttu-id="72b91-121">이 명령은 WindowsFeature 리소스를 가져오고 리소스에 대한 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="72b91-121">This command gets the WindowsFeature resource, and shows the syntax for the resource.</span></span>

### <span data-ttu-id="72b91-122">예제 6: 리소스에 대 한 모든 속성 가져오기</span><span class="sxs-lookup"><span data-stu-id="72b91-122">Example 6: Get all the properties for a resource</span></span>

```powershell
Get-DscResource -Name "User" | Select-Object -ExpandProperty Properties
```

<span data-ttu-id="72b91-123">이 명령은 사용자 리소스를 가져온 다음 파이프라인 연산자를 사용하여 사용자 리소스의 모든 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="72b91-123">This command gets the User resource, and then uses the pipeline operator to return all the properties for the User resource.</span></span>

### <span data-ttu-id="72b91-124">예 7: 지정 된 버전의 지정 된 모듈에서 모든 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="72b91-124">Example 7: Get all the resources from a specified module with a specified version</span></span>

```powershell
Get-DscResource -Module @{ModuleName='xHyper-V';RequiredVersion='3.0.0.0'}
```

<span data-ttu-id="72b91-125">이 명령은 3.0.0.0 버전의 xHyper 모듈에서 모든 리소스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="72b91-125">This command gets all the resources from xHyper-V module with version 3.0.0.0.</span></span>

## <span data-ttu-id="72b91-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="72b91-126">PARAMETERS</span></span>

### <span data-ttu-id="72b91-127">-모듈</span><span class="sxs-lookup"><span data-stu-id="72b91-127">-Module</span></span>

<span data-ttu-id="72b91-128">DSC 리소스를 볼 모듈의 이름 또는 정규화 된 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="72b91-128">Specifies the name or fully qualified name of the module for which to view the DSC resource.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="72b91-129">-Name</span><span class="sxs-lookup"><span data-stu-id="72b91-129">-Name</span></span>

<span data-ttu-id="72b91-130">보려는 DSC 리소스의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="72b91-130">Specifies an array of names of the DSC resource to view.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="72b91-131">-구문</span><span class="sxs-lookup"><span data-stu-id="72b91-131">-Syntax</span></span>

<span data-ttu-id="72b91-132">Cmdlet이 지정 된 DSC 리소스의 구문 보기를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="72b91-132">Indicates that the cmdlet returns the syntax view of the specified DSC resources.</span></span> <span data-ttu-id="72b91-133">반환 된 구문은 PowerShell 스크립트에서 리소스를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="72b91-133">The returned syntax shows how to use the resources in a PowerShell script.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="72b91-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="72b91-134">CommonParameters</span></span>

<span data-ttu-id="72b91-135">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="72b91-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="72b91-136">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="72b91-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="72b91-137">입력</span><span class="sxs-lookup"><span data-stu-id="72b91-137">INPUTS</span></span>

### <span data-ttu-id="72b91-138">System.String[]</span><span class="sxs-lookup"><span data-stu-id="72b91-138">System.String[]</span></span>

### <span data-ttu-id="72b91-139">System.Object</span><span class="sxs-lookup"><span data-stu-id="72b91-139">System.Object</span></span>

## <span data-ttu-id="72b91-140">출력</span><span class="sxs-lookup"><span data-stu-id="72b91-140">OUTPUTS</span></span>

### <span data-ttu-id="72b91-141">DesiredStateConfiguration. DscResourceInfo []</span><span class="sxs-lookup"><span data-stu-id="72b91-141">Microsoft.PowerShell.DesiredStateConfiguration.DscResourceInfo[]</span></span>

### <span data-ttu-id="72b91-142">string[]</span><span class="sxs-lookup"><span data-stu-id="72b91-142">string[]</span></span>

## <span data-ttu-id="72b91-143">참고</span><span class="sxs-lookup"><span data-stu-id="72b91-143">NOTES</span></span>

## <span data-ttu-id="72b91-144">관련 링크</span><span class="sxs-lookup"><span data-stu-id="72b91-144">RELATED LINKS</span></span>

[<span data-ttu-id="72b91-145">PowerShell 필요한 상태 구성 개요</span><span class="sxs-lookup"><span data-stu-id="72b91-145">PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="72b91-146">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="72b91-146">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)

