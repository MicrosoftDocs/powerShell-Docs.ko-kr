---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 레지스트리 리소스
ms.openlocfilehash: e0ae1a4a27edc08c4e6ccd47786426917eb1ccb4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076959"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="d8f68-103">DSC 레지스트리 리소스</span><span class="sxs-lookup"><span data-stu-id="d8f68-103">DSC Registry Resource</span></span>

<span data-ttu-id="d8f68-104">_적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="d8f68-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="d8f68-105">PowerShell DSC(Desired State Configuration)의 **레지스트리** 리소스에서는 대상 노드에 있는 레지스트리 키와 값을 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8f68-106">구문</span><span class="sxs-lookup"><span data-stu-id="d8f68-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="d8f68-107">속성</span><span class="sxs-lookup"><span data-stu-id="d8f68-107">Properties</span></span>

| <span data-ttu-id="d8f68-108">속성</span><span class="sxs-lookup"><span data-stu-id="d8f68-108">Property</span></span> | <span data-ttu-id="d8f68-109">설명</span><span class="sxs-lookup"><span data-stu-id="d8f68-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="d8f68-110">키</span><span class="sxs-lookup"><span data-stu-id="d8f68-110">Key</span></span>| <span data-ttu-id="d8f68-111">특정 상태를 확인하려는 레지스트리 키의 경로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="d8f68-112">이 경로는 하이브를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-112">This path must include the hive.</span></span>|
| <span data-ttu-id="d8f68-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="d8f68-113">ValueName</span></span>| <span data-ttu-id="d8f68-114">레지스트리 값의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="d8f68-115">레지스트리 키를 추가하거나 제거하려면 ValueType 또는 ValueData를 지정하지 않고 이 속성을 빈 문자열로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="d8f68-116">레지스트리 키의 기본값을 수정하거나 제거하려면 ValueType 또는 ValueData도 지정하고 이 속성을 빈 문자열로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="d8f68-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="d8f68-117">Ensure</span></span>| <span data-ttu-id="d8f68-118">키와 값의 존재 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="d8f68-119">존재하도록 하려면 이 속성을 "Present"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="d8f68-120">존재하지 않도록 하려면 이 속성을 "Absent"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="d8f68-121">기본값은 "Present"입니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-121">The default value is "Present".</span></span>|
| <span data-ttu-id="d8f68-122">Force</span><span class="sxs-lookup"><span data-stu-id="d8f68-122">Force</span></span>| <span data-ttu-id="d8f68-123">지정된 레지스트리 키가 있을 경우, **Force**를 사용하면 새 값으로 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-123">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="d8f68-124">하위 키가 포함된 레지스트리 키를 삭제하는 경우에는 이 속성을 **$true**로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-124">If deleting a registry key with subkeys, this needs to be **$true**</span></span> |
| <span data-ttu-id="d8f68-125">Hex</span><span class="sxs-lookup"><span data-stu-id="d8f68-125">Hex</span></span>| <span data-ttu-id="d8f68-126">데이터가 16진수 형식으로 표현될 것인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="d8f68-127">지정하는 경우 DWORD/QWORD 값 데이터가 16진수 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="d8f68-128">다른 형식에 대해서는 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-128">Not valid for other types.</span></span> <span data-ttu-id="d8f68-129">기본값은 **$false**입니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-129">The default value is **$false**.</span></span>|
| <span data-ttu-id="d8f68-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d8f68-130">DependsOn</span></span>| <span data-ttu-id="d8f68-131">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d8f68-132">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 **ResourceName**이고 해당 형식이 **ResourceType**일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-132">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="d8f68-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="d8f68-133">ValueData</span></span>| <span data-ttu-id="d8f68-134">레지스트리 값에 대한 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-134">The data for the registry value.</span></span>|
| <span data-ttu-id="d8f68-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="d8f68-135">ValueType</span></span>| <span data-ttu-id="d8f68-136">값의 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-136">Indicates the type of the value.</span></span> <span data-ttu-id="d8f68-137">지원되는 형식은 다음과 같습니다. 문자열(REG_SZ), 이진(REG-BINARY), Dword 32비트(REG_DWORD), Qword 64비트(REG_QWORD), 다중 문자열(REG_MULTI_SZ), 확장 가능한 문자열(REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="d8f68-137">The supported types are: String (REG_SZ), Binary (REG-BINARY), Dword 32-bit (REG_DWORD), Qword 64-bit (REG_QWORD), Multi-string (REG_MULTI_SZ), Expandable string (REG_EXPAND_SZ)</span></span> |

## <a name="example"></a><span data-ttu-id="d8f68-138">예제</span><span class="sxs-lookup"><span data-stu-id="d8f68-138">Example</span></span>

<span data-ttu-id="d8f68-139">이 예제에서는 "ExampleKey"라는 키가 **HKEY\_LOCAL\_MACHINE** 하이브에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-139">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> <span data-ttu-id="d8f68-140">`HKEY\CURRENT\USER` 하이브에서 레지스트리 설정을 변경하려면 구성이 시스템이 아닌 사용자 자격 증명을 사용하여 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-140">Changing a registry setting in the `HKEY\CURRENT\USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="d8f68-141">**PsDscRunAsCredential** 속성을 사용하여 구성에 대한 사용자 자격 증명을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8f68-141">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="d8f68-142">예제는 [사용자 자격 증명을 사용하여 DSC 실행](../../../configurations/runAsUser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d8f68-142">For an example, see [Running DSC with user credentials](../../../configurations/runAsUser.md).</span></span>
