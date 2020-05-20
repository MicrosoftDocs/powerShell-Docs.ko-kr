---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: DSC 구성
ms.openlocfilehash: d7749ec88f9cca3e29c6b38d61fb73776af7ceb4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954500"
---
# <a name="dsc-configurations"></a><span data-ttu-id="32972-103">DSC 구성</span><span class="sxs-lookup"><span data-stu-id="32972-103">DSC Configurations</span></span>

> <span data-ttu-id="32972-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="32972-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="32972-105">DSC 구성은 특별한 형식의 함수를 정의하는 PowerShell 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="32972-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="32972-106">구성을 정의하려면 PowerShell 키워드 **Configuration**을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

<span data-ttu-id="32972-107">스크립트를 `.ps1` 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-107">Save the script as a `.ps1` file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="32972-108">구성 구문</span><span class="sxs-lookup"><span data-stu-id="32972-108">Configuration syntax</span></span>

<span data-ttu-id="32972-109">구성 스크립트는 다음의 부분들로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="32972-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="32972-110">**Configuration** 블록.</span><span class="sxs-lookup"><span data-stu-id="32972-110">The **Configuration** block.</span></span> <span data-ttu-id="32972-111">가장 바깥쪽 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="32972-111">This is the outermost script block.</span></span> <span data-ttu-id="32972-112">**Configuration** 키워드를 사용하고 이름을 제공하여 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="32972-113">이 경우 구성의 이름은 "MyDscConfiguration"입니다.</span><span class="sxs-lookup"><span data-stu-id="32972-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="32972-114">하나 이상의 **Node** 블록.</span><span class="sxs-lookup"><span data-stu-id="32972-114">One or more **Node** blocks.</span></span> <span data-ttu-id="32972-115">이 블록에서는 구성 중인 노드(컴퓨터 또는 VM)를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="32972-116">위의 구성에는 "TEST-PC1"이라는 컴퓨터를 대상으로 하는 하나의 **Node** 블록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32972-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span> <span data-ttu-id="32972-117">Node 블록에서는 여러 컴퓨터 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32972-117">The Node block can accept multiple computer names.</span></span>
- <span data-ttu-id="32972-118">하나 이상의 리소스 블록.</span><span class="sxs-lookup"><span data-stu-id="32972-118">One or more resource blocks.</span></span> <span data-ttu-id="32972-119">이 블록은 구성으로 구성 중인 리소스에 대한 속성을 설정하는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="32972-119">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="32972-120">이 경우 두 개의 리소스 블록이 있으며, 각각 "WindowsFeature" 리소스를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-120">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="32972-121">**Configuration** 블록 내에서는 PoweShell 함수에서 일반적으로 수행할 수도 있는 모든 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32972-121">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="32972-122">예를 들어 앞의 예에서는, 구성에서 대상 컴퓨터의 이름을 하드 코드하지 않으려는 경우 노드 이름에 대한 매개 변수를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32972-122">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

<span data-ttu-id="32972-123">이 예제에서는 구성을 컴파일할 때 **ComputerName** 매개 변수로 전달하여 노드의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-123">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="32972-124">이름의 기본값은 "localhost"입니다.</span><span class="sxs-lookup"><span data-stu-id="32972-124">The name defaults to "localhost".</span></span>

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

<span data-ttu-id="32972-125">**Node** 블록에서는 여러 컴퓨터 이름을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32972-125">The **Node** block can also accept multiple computer names.</span></span> <span data-ttu-id="32972-126">위의 예제에서 `-ComputerName` 매개 변수를 사용하거나, 쉼표로 구분된 컴퓨터 목록을 **Node** 블록에 직접 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32972-126">In the above example, you can either use the `-ComputerName` parameter, or pass a comma-separated list of computers directly to the **Node** block.</span></span>

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

<span data-ttu-id="32972-127">컴퓨터 목록을 **Node** 블록으로 지정하면 구성 내에서 배열 표기법을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-127">When specifying a list of computers to the **Node** block, from within a Configuration, you need to use array-notation.</span></span>

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a><span data-ttu-id="32972-128">구성 컴파일</span><span class="sxs-lookup"><span data-stu-id="32972-128">Compiling the configuration</span></span>

<span data-ttu-id="32972-129">구성을 시행할 수 있으려면 먼저 MOF 문서로 컴파일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-129">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="32972-130">PowerShell 함수를 호출하는 것처럼 구성을 호출하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="32972-130">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="32972-131">구성의 이름만을 포함하는 예제의 마지막 줄은 구성을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-131">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="32972-132">구성을 호출하려면 (다른 PowerShell 함수에서처럼) 함수가 전역 범위에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-132">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
> <span data-ttu-id="32972-133">스크립트를 "도트 소싱"하거나, F5 키를 사용하거나 ISE에서 **스크립트 실행** 단추를 클릭하여 구성 스크립트를 실행하면 이렇게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32972-133">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
> <span data-ttu-id="32972-134">스크립트를 도트 소싱하려면 명령을 `. .\myConfig.ps1`을 실행합니다. 여기서 `myConfig.ps1`은 구성을 포함하는 스크립트 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="32972-134">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="32972-135">구성을 호출하면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-135">When you call the configuration, it:</span></span>

- <span data-ttu-id="32972-136">모든 변수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-136">Resolves all variables</span></span>
- <span data-ttu-id="32972-137">현재 디렉터리에 구성과 같은 이름으로 폴더를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-137">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="32972-138">새 디렉터리에 _NodeName_.mof라는 파일을 생성합니다. _NodeName_은 구성의 대상 노드 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="32972-138">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
  <span data-ttu-id="32972-139">노드가 두 개 이상 있을 경우에는 각 노드에 대해 MOF 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="32972-139">If there is more than one node, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="32972-140">MOF 파일은 대상 노드에 대한 모든 구성 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-140">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="32972-141">이 때문에 안전하게 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-141">Because of this, it's important to keep it secure.</span></span>
> <span data-ttu-id="32972-142">자세한 내용은 [MOF 파일 보안](../pull-server/secureMOF.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="32972-142">For more information, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>

<span data-ttu-id="32972-143">위의 첫 번째 구성을 컴파일하면 다음 폴더 구조가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="32972-143">Compiling the first configuration above results in the following folder structure:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

<span data-ttu-id="32972-144">구성에서 매개 변수를 사용하는 경우, 두 번째 예제에서처럼 컴파일 시 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-144">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="32972-145">다음과 같은 모습이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="32972-145">Here's how that would look:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="32972-146">구성에서 새 리소스 사용</span><span class="sxs-lookup"><span data-stu-id="32972-146">Using new resources in Your configuration</span></span>

<span data-ttu-id="32972-147">앞의 예제를 실행했다면 명시적으로 가져오지 않고 리소스를 사용하고 있다는 경고가 표시된 것을 보았을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32972-147">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="32972-148">오늘, DSC는 PSDesiredStateConfiguration 모듈의 일부로서 12개의 리소스와 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="32972-148">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>

<span data-ttu-id="32972-149">cmdlet인 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)는 시스템에 설치되어 있고 LCM에서 사용할 수 있는 리소스를 파악하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32972-149">The cmdlet, [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="32972-150">이러한 모듈은 `$env:PSModulePath`에 배치되어 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)에 의해 제대로 인식된 후에도 여전히 구성 내에서 로드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-150">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), they still need to be loaded within your configuration.</span></span>

<span data-ttu-id="32972-151">**Import-DscResource**는 **구성** 블록 내에서만 인식될 수 있는 동적 키워드이며, cmdlet이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="32972-151">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block, it is not a cmdlet.</span></span>
<span data-ttu-id="32972-152">**Import-DscResource**에서는 두 개의 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="32972-152">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="32972-153">**ModuleName**은 **Import-DscResource**를 사용하는 권장 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="32972-153">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="32972-154">가져올 리소스를 포함하는 모듈의 이름을 받습니다(모듈 이름으로 이루어진 문자열 배열도 받음).</span><span class="sxs-lookup"><span data-stu-id="32972-154">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="32972-155">**Name**은 가져올 리소스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="32972-155">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="32972-156">이 이름은 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)에 의해 "Name"으로 반환한 친숙한 이름이 아니라, 리소스 스키마를 정의할 때 사용된 클래스 이름입니다([Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)에 의해 **ResourceType**으로 반환됨).</span><span class="sxs-lookup"><span data-stu-id="32972-156">This is not the friendly name returned as "Name" by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span></span>

<span data-ttu-id="32972-157">`Import-DSCResource` 사용에 대한 자세한 내용은 [Import-DSCResource 사용](import-dscresource.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="32972-157">For more information on using `Import-DSCResource`, see [Using Import-DSCResource](import-dscresource.md)</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="32972-158">PowerShell v4 및 v5의 차이</span><span class="sxs-lookup"><span data-stu-id="32972-158">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="32972-159">PowerShell 4.0에서 DSC 리소스를 저장해야 하는 경우에는 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32972-159">There are differences in where DSC resources need to be stored in PowerShell 4.0.</span></span> <span data-ttu-id="32972-160">자세한 내용은 [리소스 위치](import-dscresource.md#resource-location)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="32972-160">For more information, see [Resource location](import-dscresource.md#resource-location).</span></span>

## <a name="see-also"></a><span data-ttu-id="32972-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="32972-161">See Also</span></span>

- [<span data-ttu-id="32972-162">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="32972-162">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="32972-163">DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="32972-163">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="32972-164">로컬 구성 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="32972-164">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
