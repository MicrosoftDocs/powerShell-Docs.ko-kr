---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 구성 데이터 사용
ms.openlocfilehash: f2d25b9ced805fb4c91378ebfe840104eb6ce52a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080223"
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="63dce-103">DSC에서 구성 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="63dce-103">Using configuration data in DSC</span></span>

> <span data-ttu-id="63dce-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="63dce-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="63dce-105">기본 제공 DSC**ConfigurationData** 매개 변수를 사용하여 구성 내에서 사용할 수 있는 데이터를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-105">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span>
<span data-ttu-id="63dce-106">그러면 여러 노드 또는 다양한 환경에 사용할 수 있는 단일 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-106">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span>
<span data-ttu-id="63dce-107">예를 들어 애플리케이션을 개발할 경우 한 구성을 개발 및 프로덕션 환경 모두에 사용하고 구성 데이터를 사용하여 각 환경의 데이터를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="63dce-108">이 항목에서는 **ConfigurationData** 해시 테이블의 구조를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-108">This topic describes the structure of the **ConfigurationData** hashtable.</span></span>
<span data-ttu-id="63dce-109">구성 데이터를 사용하는 방법에 대한 예제는 [구성 및 환경 데이터 분리](separatingEnvData.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63dce-109">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="63dce-110">ConfigurationData 일반 매개 변수</span><span class="sxs-lookup"><span data-stu-id="63dce-110">The ConfigurationData common parameter</span></span>

<span data-ttu-id="63dce-111">DSC 구성에서는 구성을 컴파일할 때 지정하는 일반 매개 변수 **ConfigurationData**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-111">A DSC configuration takes a common parameter, **ConfigurationData**, that you specify when you compile the configuration.</span></span>
<span data-ttu-id="63dce-112">구성을 컴파일하는 방법에 대한 자세한 내용은 [DSC 구성](configurations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63dce-112">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="63dce-113">**ConfigurationData** 매개 변수는 **AllNodes**라는 키가 하나 이상 있어야 하는 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-113">The **ConfigurationData** parameter is a hashtable that must have at least one key named **AllNodes**.</span></span>
<span data-ttu-id="63dce-114">다른 키도 하나 이상 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-114">It can also have one or more other keys.</span></span>

> [!NOTE]
> <span data-ttu-id="63dce-115">이 항목의 예제에서는 명명된**AllNodes** 키가 아닌 단일 추가 키 `NonNodeData`를 사용하지만, 추가 키는 원하는 수만큼 포함하고 원하는 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-115">The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

<span data-ttu-id="63dce-116">**AllNodes** 키의 값은 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-116">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="63dce-117">이 배열의 각 요소도 **NodeName**이라는 키가 하나 이상 있어야 하는 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-117">Each element of this array is also a hash table that must have at least one key named **NodeName**:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="63dce-118">각 해시 테이블에도 다른 키를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-118">You can add other keys to each hash table as well:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="63dce-119">모든 노드에 한 속성을 적용하려면 **AllNodes** 배열에 **NodeName**이 `*`인 원소를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-119">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span>
<span data-ttu-id="63dce-120">예를 들어 모든 노드에 `LogPath` 속성을 지정하기 위해 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-120">For example, to give every node a `LogPath` property, you could do this:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

<span data-ttu-id="63dce-121">이 작업은 이름이 `LogPath`이고 값이 `"C:\Logs"`인 속성을 다른 블록 각각에(`VM-1`, `VM-2`, `VM-3`) 추가하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-121">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="63dce-122">ConfigurationData 해시 테이블 정의</span><span class="sxs-lookup"><span data-stu-id="63dce-122">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="63dce-123">**ConfigurationData**는 이전 예제에서와 같이 구성과 동일한 스크립트 파일 내에서 변수로 정의할 수도 있고, 별도의 `.psd1` 파일에서 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-123">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span>
<span data-ttu-id="63dce-124">**ConfigurationData**를 `.psd1` 파일에 정의하려면 구성 데이터를 나타내는 해시 테이블만 포함된 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-124">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="63dce-125">예를 들어, 이름이 `MyData.psd1`이고 다음과 같은 내용이 있는 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-125">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="63dce-126">구성 데이터와 함께 구성 컴파일</span><span class="sxs-lookup"><span data-stu-id="63dce-126">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="63dce-127">구성 데이터를 정의한 구성을 컴파일하려면 **ConfigurationData** 매개 변수의 값으로 구성 데이터를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-127">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="63dce-128">이렇게 하면 **AllNodes** 배열의 각 항목에 대해 MOF 파일이 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-128">This will create a MOF file for each entry in the **AllNodes** array.</span></span>
<span data-ttu-id="63dce-129">각 MOF 파일의 이름은 해당하는 배열 항목의 `NodeName` 속성으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-129">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="63dce-130">예를 들어 위의 `MyData.psd1` 파일에서와 같이 구성 데이터를 정의하는 경우 해당 구성을 컴파일하면 `VM-1.mof` 및 `VM-2.mof` 파일이 둘 다 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-130">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="63dce-131">변수를 사용하여 구성 데이터와 함께 구성 컴파일</span><span class="sxs-lookup"><span data-stu-id="63dce-131">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="63dce-132">구성과 동일한 `.ps1` 파일에 변수로 정의된 구성 데이터를 사용하려면 구성을 컴파일할 때 **ConfigurationData** 매개 변수 값으로 변수 이름을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-132">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="63dce-133">데이터 파일을 사용하여 구성 데이터와 함께 구성 컴파일</span><span class="sxs-lookup"><span data-stu-id="63dce-133">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="63dce-134">.psd1 파일에 정의된 구성 데이터를 사용하려면 구성을 컴파일할 때 해당 파일의 경로와 이름을 **ConfigurationData** 매개 변수 값으로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-134">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="63dce-135">구성에 ConfigurationData 변수 사용</span><span class="sxs-lookup"><span data-stu-id="63dce-135">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="63dce-136">DSC에서는 구성 스크립트에 사용할 수 있는 다음 특수 변수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-136">DSC provides the following special variables that can be used in a configuration script:</span></span>

- <span data-ttu-id="63dce-137">**$AllNodes**는 **ConfigurationData**에 정의된 노드의 컬렉션 전체를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-137">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData**.</span></span> <span data-ttu-id="63dce-138">**AllNodes** 컬렉션은 **.Where()** 및 **.ForEach()** 를 사용하여 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-138">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()**.</span></span>
- <span data-ttu-id="63dce-139">**ConfigurationData**는 구성을 컴파일할 때 매개 변수로 전달된 해시 테이블 전체를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-139">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>
- <span data-ttu-id="63dce-140">**MyTypeName**에는 변수가 사용되는 [구성](configurations.md) 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-140">**MyTypeName** contains the [configuration](configurations.md) name the variable is used in.</span></span> <span data-ttu-id="63dce-141">예를 들어 `MyDscConfiguration` 구성에서 `$MyTypeName`에는 `MyDscConfiguration` 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-141">For example, in the configuration `MyDscConfiguration`, the `$MyTypeName` will have a value of `MyDscConfiguration`.</span></span>
- <span data-ttu-id="63dce-142">**Node**는 **AllNodes** 컬렉션이 **.Where()** 또는 **.ForEach()** 로 필터링된 후에 특정 항목을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-142">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()**.</span></span>
  - <span data-ttu-id="63dce-143">[about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)의 이 메서드에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-143">You can read more about these methods in [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="63dce-144">비노드 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="63dce-144">Using non-node data</span></span>

<span data-ttu-id="63dce-145">이전 예제에서 살펴본 것처럼, **ConfigurationData** 해시 테이블은 필수 **AllNodes** 키 외에 키를 하나 이상 추가로 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-145">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span>
<span data-ttu-id="63dce-146">이 항목의 예제에서는 추가 노드를 하나만 사용했으며 이름을 `NonNodeData`로 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-146">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span>
<span data-ttu-id="63dce-147">그러나 추가 키는 원하는 수만큼 정의할 수 있으며 원하는 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63dce-147">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="63dce-148">비노드 데이터 사용 예제는 [구성 및 환경 데이터 분리](separatingEnvData.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63dce-148">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="63dce-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63dce-149">See Also</span></span>

- [<span data-ttu-id="63dce-150">구성 데이터의 자격 증명 옵션</span><span class="sxs-lookup"><span data-stu-id="63dce-150">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="63dce-151">DSC 구성</span><span class="sxs-lookup"><span data-stu-id="63dce-151">DSC Configurations</span></span>](configurations.md)