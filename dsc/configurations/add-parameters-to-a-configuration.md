---
ms.date: 12/12/2018
keywords: dsc, powershell, 리소스, 갤러리, 설치
title: 구성에 매개 변수 추가
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402556"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="64ec6-103">구성에 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="64ec6-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="64ec6-104">함수에서 처럼 [구성을](configurations.md) 사용자 입력을 기반으로 하는 보다 동적인 구성을 허용 하 여 매개 변수화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="64ec6-105">단계에 설명 된 내용과 비슷합니다 [매개 변수를 사용 하 여 함수](/powershell/module/microsoft.powershell.core/about/about_functions)합니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="64ec6-106">이 예제에서는 "Running" 이어야 하는 "Spooler" 서비스를 구성 하는 기본 구성을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
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

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="64ec6-107">기본 제공 구성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="64ec6-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="64ec6-108">함수와 달리 그러나 합니다 [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) 특성 추가 기능이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="64ec6-109">외에 [일반 매개 변수](/powershell/module/microsoft.powershell.core/about/about_commonparameters), 구성을 다음 매개 변수를 정의 할 필요 없이 기본 제공을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="64ec6-110">매개 변수</span><span class="sxs-lookup"><span data-stu-id="64ec6-110">Parameter</span></span>  |<span data-ttu-id="64ec6-111">설명</span><span class="sxs-lookup"><span data-stu-id="64ec6-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="64ec6-112">정의에 사용 되는 [복합 구성](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="64ec6-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="64ec6-113">정의에 사용 되는 [복합 구성](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="64ec6-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="64ec6-114">정의에 사용 되는 [복합 구성](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="64ec6-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="64ec6-115">전달 하는 데에 구조적 [구성 데이터](configData.md) 구성에 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="64ec6-116">위치를 지정 하는 데에 "\<computername\>.mof" 파일 컴파일</span><span class="sxs-lookup"><span data-stu-id="64ec6-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="64ec6-117">구성에 사용자 고유의 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="64ec6-118">기본 제공 매개 변수 외에도 사용자 구성에도 고유한 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="64ec6-119">매개 변수 블록 함수 처럼 구성 선언 내에서 직접 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="64ec6-120">구성 매개 변수 블록을 하나 밖에 있어야 **노드** 선언 및 위에 *가져오기* 문입니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="64ec6-121">매개 변수를 추가 하면 더 강력 하 고 동적 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="64ec6-122">ComputerName 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="64ec6-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="64ec6-123">첫 번째 매개 변수인 추가할 수 있습니다는 `-Computername` 에 대 한 "mof" 파일을 동적으로 컴파일할 수 있도록 하는 매개 변수 `-Computername` 구성에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="64ec6-124">함수와 마찬가지로 정의할 수도 있습니다는 기본값을 사용자에 대 한 값에 통과 하지 못하는 경우 `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="64ec6-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="64ec6-125">구성에 지정할 수 있습니다 다음에 `-ComputerName` 노드 블록을 정의할 때 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="64ec6-126">에 대 한 구성 매개 변수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="64ec6-127">구성에 매개 변수를 추가한 후 cmdlet을 사용 하는 것 처럼 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="64ec6-128">여러.mof 파일 컴파일</span><span class="sxs-lookup"><span data-stu-id="64ec6-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="64ec6-129">노드 블록 컴퓨터 이름의 쉼표로 구분 된 목록을 그대로 사용할 수도 있습니다 및 각각에 대해 ".mof" 파일을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="64ec6-130">에 전달 된 컴퓨터의 모든 ".mof" 파일을 생성 하려면 다음 예제에서는 실행할 수 있습니다는 `-ComputerName` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="64ec6-131">구성에서 고급 매개 변수</span><span class="sxs-lookup"><span data-stu-id="64ec6-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="64ec6-132">이외에 `-ComputerName` 매개 변수, 서비스 이름 및 상태에 대 한 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="64ec6-133">사용 하 여 매개 변수 블록을 추가 하는 다음 예제는 `-ServiceName` 매개 변수 동적으로 정의 하는 데 사용 합니다 **서비스** 리소스 블록.</span><span class="sxs-lookup"><span data-stu-id="64ec6-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="64ec6-134">또한 추가 `-State` 매개 변수를 동적으로 정의할 합니다 **상태** 에 **서비스** 리소스 블록.</span><span class="sxs-lookup"><span data-stu-id="64ec6-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

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

    # It is best practice to implicitly import any required resources or modules.
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
> <span data-ttu-id="64ec6-135">더 많은 advacned 시나리오에서 동적 데이터는 구조적으로 이동할 것이 더 적절 해야 [구성 데이터](configData.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="64ec6-136">지금 구성을 예제에서는 동적 `$ServiceName`를 지정 하지 않으면 컴파일 오류가 발생 하지만 합니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="64ec6-137">이 예제와 같이 기본 값을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="64ec6-138">이 인스턴스에서 그러나 편이 사용자에 대 한 값을 지정 하려면 강제 적용 하는 `$ServiceName` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="64ec6-139">`parameter` 특성을 사용 하면 추가 유효성 검사 및 파이프라인 지원 구성에 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="64ec6-140">모든 매개 변수 선언 위에 추가 합니다 `parameter` 아래 예제와 같이 특성 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="64ec6-141">각 인수를 지정할 수 있습니다 `parameter` 여러 측면을 제어할 정의 된 매개 변수 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="64ec6-142">다음 예에서는 합니다 `$ServiceName` 는 **필수** 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="64ec6-143">에 대 한 합니다 `$State` 미리 정의 된 집합 외부의 값을 지정할 필요가 없도록 사용자를 방지 하고자 매개 변수 (실행 중인, 중지 됨)는 `ValidationSet*`특성 (예: 실행 중, 미리 정의 된 집합 외부의 값을 지정할 필요가 없도록 사용자를 방해 중지 됨).</span><span class="sxs-lookup"><span data-stu-id="64ec6-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="64ec6-144">다음 예제에 추가 합니다 `ValidationSet` 특성을 `$State` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="64ec6-145">확인 하지 않을 것 이므로 합니다 `$State` 매개 변수 **필수**에 대 한 기본값을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="64ec6-146">지정할 필요가 없습니다를 `parameter` 사용 하는 경우 특성을 `validation` 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="64ec6-147">에 대 한 자세한 내용은 합니다 `parameter` 및 유효성 검사 특성 [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="64ec6-148">매개 변수가 있는 완벽 하 게 구성</span><span class="sxs-lookup"><span data-stu-id="64ec6-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="64ec6-149">이제 사용자가 지정 하는 매개 변수가 있는 구성을 `-InstanceName`, `-ServiceName`, 유효성을 검사 하 고는 `-State` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

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

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="64ec6-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="64ec6-150">See also</span></span>

- [<span data-ttu-id="64ec6-151">DSC 구성에 대한 도움말 작성</span><span class="sxs-lookup"><span data-stu-id="64ec6-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="64ec6-152">동적 구성</span><span class="sxs-lookup"><span data-stu-id="64ec6-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="64ec6-153">구성에 구성 데이터를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="64ec6-154">별도 구성 및 환경 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="64ec6-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
