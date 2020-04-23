---
ms.date: 12/12/2018
keywords: dsc,powershell,리소스,갤러리,설정
title: 구성에 매개 변수 추가
ms.openlocfilehash: 9dd9f2be58c13840be2b24e7e21a0d4af79b67cc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "80263155"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="be839-103">구성에 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="be839-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="be839-104">함수처럼, 사용자 입력에 따라 더 동적인 구성을 허용하도록 [구성](configurations.md)을 매개 변수화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="be839-105">단계는 [함수 및 매개 변수](/powershell/module/microsoft.powershell.core/about/about_functions)에 설명된 단계와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="be839-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="be839-106">이 예제에서는 "Spooler" 서비스를 "Running"으로 구성하는 기본 구성으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="be839-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="be839-107">기본 제공 구성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="be839-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="be839-108">함수와 달리 [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) 특성은 기능을 추가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="be839-109">[일반 매개 변수](/powershell/module/microsoft.powershell.core/about/about_commonparameters) 외에도 구성에서는 매개 변수를 정의할 필요 없이 다음 기본 제공 매개 변수를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|        <span data-ttu-id="be839-110">매개 변수</span><span class="sxs-lookup"><span data-stu-id="be839-110">Parameter</span></span>        |                                         <span data-ttu-id="be839-111">Description</span><span class="sxs-lookup"><span data-stu-id="be839-111">Description</span></span>                                          |
| ----------------------- | -------------------------------------------------------------------------------------------- |
| `-InstanceName`         | <span data-ttu-id="be839-112">[복합 구성](compositeconfigs.md)을 정의하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="be839-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>                             |
| `-DependsOn`            | <span data-ttu-id="be839-113">[복합 구성](compositeconfigs.md)을 정의하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="be839-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>                             |
| `-PSDSCRunAsCredential` | <span data-ttu-id="be839-114">[복합 구성](compositeconfigs.md)을 정의하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="be839-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>                             |
| `-ConfigurationData`    | <span data-ttu-id="be839-115">구성에서 사용하도록 구조적 [구성 데이터](configData.md)를 전달하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="be839-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span> |
| `-OutputPath`           | <span data-ttu-id="be839-116">"\<computername\>.mof" 파일을 컴파일할 위치를 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="be839-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>                      |

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="be839-117">구성에 고유한 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="be839-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="be839-118">기본 제공 매개 변수 외에 고유한 매개 변수를 구성에 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span>
<span data-ttu-id="be839-119">매개 변수 블록은 함수처럼 구성 선언 내부로 직접 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="be839-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="be839-120">구성 매개 변수 블록은 **Node** 선언 외부 및 *import* 문 위에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be839-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="be839-121">매개 변수를 추가하면 더 강력하고 동적인 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="be839-122">ComputerName 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="be839-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="be839-123">추가할 수 있는 첫 번째 매개 변수는 `-Computername` 매개 변수이므로 구성에 전달하는 모든 `-Computername`에 대해 ".mof" 파일을 동적으로 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="be839-124">함수처럼, 사용자가 `-ComputerName` 값을 전달하지 않는 경우 기본값을 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="be839-125">구성 내에서 Node 블록을 정의할 때 `-ComputerName` 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="be839-126">매개 변수를 사용하여 구성 호출</span><span class="sxs-lookup"><span data-stu-id="be839-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="be839-127">구성에 매개 변수를 추가한 후 cmdlet에서 사용하는 것처럼 이 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="be839-128">여러 .mof 파일 컴파일</span><span class="sxs-lookup"><span data-stu-id="be839-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="be839-129">Node 블록은 쉼표로 구분된 컴퓨터 이름 목록을 사용할 수 있고 각 컴퓨터 이름에 대해 ".mof" 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="be839-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="be839-130">다음 예제를 실행하여 `-ComputerName` 매개 변수에 전달된 모든 컴퓨터에 대해 ".mof" 파일을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="be839-131">구성의 고급 매개 변수</span><span class="sxs-lookup"><span data-stu-id="be839-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="be839-132">`-ComputerName` 매개 변수 외에도 서비스 이름 및 상태에 대한 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span>
<span data-ttu-id="be839-133">다음 예제에서는 `-ServiceName`을 사용하여 매개 변수 블록을 추가하고 이 매개 변수를 **Service** 리소스 블록을 동적으로 정의하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="be839-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="be839-134">또한 `-State` 매개 변수를 추가하여 **Service** 리소스 블록에서 **State**를 동적으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="be839-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="be839-135">더 고급 시나리오에서는 동적 데이터를 구조적 [구성 데이터](configData.md)로 이동하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-135">In more advanced scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="be839-136">예제 구성에서는 이제 동적 `$ServiceName`을 사용하지만 이 매개 변수를 지정하지 않을 경우 컴파일 시 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="be839-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="be839-137">이 예제와 같이 기본값을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="be839-138">하지만 이 경우에는 간단히 사용자에게 `$ServiceName` 매개 변수를 지정하도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="be839-139">`parameter` 특성을 사용하여 구성의 매개 변수에 유효성 검사 및 파이프라인 지원을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="be839-140">모든 매개 변수 선언 위에 아래 예제와 같이 `parameter` 특성 블록을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="be839-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="be839-141">각 `parameter` 특성에 대한 인수를 지정하여 정의된 매개 변수의 측면을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="be839-142">다음 예제에서는 `$ServiceName`을 **Mandatory** 매개 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="be839-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="be839-143">`$State` 매개 변수의 경우 사용자가 미리 정의된 세트(예: Running, Stopped) 외부 값을 지정하지 못하도록 합니다. `ValidationSet*` 특성은 사용자가 미리 정의된 세트(예: Running, Stopped) 외부 값을 지정하지 못하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="be839-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="be839-144">다음 예제에서는 `ValidationSet` 특성을 `$State` 매개 변수에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="be839-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="be839-145">`$State` 매개 변수를 **Mandatory**로 설정하지 않을 것이므로 기본값을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be839-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="be839-146">`parameter` 특성을 사용하는 경우 `validation` 특성을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="be839-147">`parameter`about_Functions_Advanced_Parameters[에서 ](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters) 및 validation 특성에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="be839-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="be839-148">완전 매개 변수화된 구성</span><span class="sxs-lookup"><span data-stu-id="be839-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="be839-149">이제 사용자가 `-InstanceName`, `-ServiceName`을 지정하도록 하고 `-State` 매개 변수의 유효성을 검사하는 매개 변수화된 구성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be839-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="be839-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="be839-150">See also</span></span>

- [<span data-ttu-id="be839-151">DSC 구성에 대한 도움말 작성</span><span class="sxs-lookup"><span data-stu-id="be839-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="be839-152">동적 구성</span><span class="sxs-lookup"><span data-stu-id="be839-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="be839-153">구성에서 구성 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="be839-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="be839-154">구성 및 환경 데이터 분리</span><span class="sxs-lookup"><span data-stu-id="be839-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
