---
external help file: PSDesiredStateConfiguration-help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: 732db5a049a68e059db6062d2f6c3f850d579adc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605489"
---
# <span data-ttu-id="b0f19-102">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="b0f19-102">Invoke-DscResource</span></span>

## <span data-ttu-id="b0f19-103">개요</span><span class="sxs-lookup"><span data-stu-id="b0f19-103">SYNOPSIS</span></span>
<span data-ttu-id="b0f19-104">지정 된 PowerShell DSC (필요한 상태 구성) 리소스의 메서드를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-104">Runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

## <span data-ttu-id="b0f19-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b0f19-105">SYNTAX</span></span>

```
Invoke-DscResource [-Name] <String> [[-ModuleName] <ModuleSpecification>] [-Method] <String>
 [-Property] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="b0f19-106">설명</span><span class="sxs-lookup"><span data-stu-id="b0f19-106">DESCRIPTION</span></span>

<span data-ttu-id="b0f19-107">`Invoke-DscResource` cmdlet은 지정된 PowerShell DSC(Desired State Configuration) 리소스의 메서드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-107">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="b0f19-108">이 cmdlet은 구성 문서를 만들지 않고 DSC 리소스를 직접 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-108">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="b0f19-109">이 cmdlet을 사용 하 여 구성 관리 제품은 DSC 리소스를 사용 하 여 windows 또는 Linux를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-109">Using this cmdlet, configuration management products can manage windows or Linux by using DSC resources.</span></span> <span data-ttu-id="b0f19-110">이 cmdlet을 사용하면 디버깅을 사용하도록 설정한 상태에서 DSC 엔진이 실행 중일 때에도 리소스를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-110">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="b0f19-111">`Invoke-DscResource` 는 PowerShell 7의 실험적 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-111">`Invoke-DscResource` is an experimental feature in PowerShell 7.</span></span> <span data-ttu-id="b0f19-112">Cmdlet을 사용 하려면 다음 명령을 사용 하 여 cmdlet을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-112">To use the cmdlet, you must enable it using the following command.</span></span>
>
> `Enable-ExperimentalFeature PSDesiredStateConfiguration.InvokeDscResource`

## <span data-ttu-id="b0f19-113">예제</span><span class="sxs-lookup"><span data-stu-id="b0f19-113">EXAMPLES</span></span>

### <span data-ttu-id="b0f19-114">예제 1: 필수 속성을 지정 하 여 리소스의 Set 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-114">Example 1: Invoke the Set method of a resource by specifying its mandatory properties</span></span>

<span data-ttu-id="b0f19-115">이 예제에서는 **windowsprocess** 라는 리소스의 **Set** 메서드를 호출 하 고, 지정 된 Windows 프로세스를 시작 하기 위한 필수 **경로** 및 **인수** 속성을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-115">This example invokes the **Set** method of a resource named **WindowsProcess** and provides the mandatory **Path** and **Arguments** properties to start the specified Windows process.</span></span>

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

### <span data-ttu-id="b0f19-116">예제 2: 지정 된 모듈에 대 한 리소스의 테스트 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="b0f19-116">Example 2: Invoke the Test method of a resource for a specified module</span></span>

<span data-ttu-id="b0f19-117">이 예제에서는 **PSDesiredStateConfiguration** 라는 모듈에 있는 **windowsprocess** 라는 리소스의 **테스트** 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-117">This example invokes the **Test** method of a resource named **WindowsProcess**, which is in the module named **PSDesiredStateConfiguration**.</span></span>

```powershell
$SplatParam = @{
  Name = 'WindowsProcess'
  ModuleName = 'PSDesiredStateConfiguration'
  Property = @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''}
  Method = Test
}

Invoke-DscResource @SplatParam
```

## <span data-ttu-id="b0f19-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b0f19-118">PARAMETERS</span></span>

### <span data-ttu-id="b0f19-119">-메서드</span><span class="sxs-lookup"><span data-stu-id="b0f19-119">-Method</span></span>

<span data-ttu-id="b0f19-120">이 cmdlet이 호출 하는 리소스의 메서드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-120">Specifies the method of the resource that this cmdlet invokes.</span></span> <span data-ttu-id="b0f19-121">이 매개 변수에 허용 되는 값은 **Get**, **Set** 및 **Test** 입니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-121">The acceptable values for this parameter are: **Get**, **Set**, and **Test**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0f19-122">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="b0f19-122">-ModuleName</span></span>

<span data-ttu-id="b0f19-123">이 cmdlet이 지정 된 리소스를 호출 하는 모듈의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-123">Specifies the name of the module from which this cmdlet invokes the specified resource.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b0f19-124">-Name</span><span class="sxs-lookup"><span data-stu-id="b0f19-124">-Name</span></span>

<span data-ttu-id="b0f19-125">시작할 DSC 리소스의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-125">Specifies the name of the DSC resource to start.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b0f19-126">-속성</span><span class="sxs-lookup"><span data-stu-id="b0f19-126">-Property</span></span>

<span data-ttu-id="b0f19-127">해시 테이블의 리소스 속성 이름 및 해당 값을 키와 값으로 각각 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-127">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0f19-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b0f19-128">CommonParameters</span></span>

<span data-ttu-id="b0f19-129">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b0f19-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b0f19-130">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b0f19-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b0f19-131">입력</span><span class="sxs-lookup"><span data-stu-id="b0f19-131">INPUTS</span></span>

### <span data-ttu-id="b0f19-132">System.String</span><span class="sxs-lookup"><span data-stu-id="b0f19-132">System.String</span></span>

### <span data-ttu-id="b0f19-133">ModuleSpecification.</span><span class="sxs-lookup"><span data-stu-id="b0f19-133">Microsoft.PowerShell.Commands.ModuleSpecification</span></span>

## <span data-ttu-id="b0f19-134">출력</span><span class="sxs-lookup"><span data-stu-id="b0f19-134">OUTPUTS</span></span>

### <span data-ttu-id="b0f19-135">System.Object</span><span class="sxs-lookup"><span data-stu-id="b0f19-135">System.Object</span></span>

## <span data-ttu-id="b0f19-136">참고</span><span class="sxs-lookup"><span data-stu-id="b0f19-136">NOTES</span></span>

- <span data-ttu-id="b0f19-137">이전에는 Windows PowerShell 5.1 리소스가 **PsDscRunAsCredential** 키를 사용 하 여 사용자 컨텍스트에 지정 되지 않는 한 시스템 컨텍스트에서 실행 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-137">Previously, Windows PowerShell 5.1 resources ran under System context unless specified with user context using the key **PsDscRunAsCredential**.</span></span> <span data-ttu-id="b0f19-138">PowerShell 7.0에서 리소스는 사용자의 컨텍스트에서 실행 되 고 **PsDscRunAsCredential** 는 더 이상 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-138">In PowerShell 7.0, Resources run in the user's context, and **PsDscRunAsCredential** is no longer supported.</span></span> <span data-ttu-id="b0f19-139">이 키를 사용 하는 이전 구성에서는 예외가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-139">Previous configurations using this key will throw an exception.</span></span>

- <span data-ttu-id="b0f19-140">PowerShell 7에서는 `Invoke-DscResource` 더 이상 WMI DSC 리소스의 호출을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-140">As of PowerShell 7, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="b0f19-141">여기에는 **PSDesiredStateConfiguration** 의 **File** 및 **Log** 리소스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0f19-141">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration**.</span></span>

## <span data-ttu-id="b0f19-142">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b0f19-142">RELATED LINKS</span></span>

[<span data-ttu-id="b0f19-143">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="b0f19-143">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="b0f19-144">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="b0f19-144">Get-DscResource</span></span>](Get-DscResource.md)
