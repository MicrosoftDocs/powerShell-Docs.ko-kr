---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC 레지스트리 리소스
ms.openlocfilehash: 3acd79fa81bc731f344d810371b961dc3af3a11d
ms.sourcegitcommit: 1ab59991c18e1b9692333d5e58ce649eaa75594f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84203650"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="1bd79-103">DSC 레지스트리 리소스</span><span class="sxs-lookup"><span data-stu-id="1bd79-103">DSC Registry Resource</span></span>

> <span data-ttu-id="1bd79-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="1bd79-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="1bd79-105">PowerShell DSC(필요한 상태 구성)의 **레지스트리** 리소스에서는 대상 노드에 있는 레지스트리 키와 값을 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="1bd79-106">구문</span><span class="sxs-lookup"><span data-stu-id="1bd79-106">Syntax</span></span>

```Syntax
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Present | Absent }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="1bd79-107">속성</span><span class="sxs-lookup"><span data-stu-id="1bd79-107">Properties</span></span>

|<span data-ttu-id="1bd79-108">속성</span><span class="sxs-lookup"><span data-stu-id="1bd79-108">Property</span></span> |<span data-ttu-id="1bd79-109">Description</span><span class="sxs-lookup"><span data-stu-id="1bd79-109">Description</span></span> |
|---|---|
|<span data-ttu-id="1bd79-110">키</span><span class="sxs-lookup"><span data-stu-id="1bd79-110">Key</span></span> |<span data-ttu-id="1bd79-111">특정 상태를 확인하려는 레지스트리 키의 경로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="1bd79-112">이 경로는 하이브를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-112">This path must include the hive.</span></span> |
|<span data-ttu-id="1bd79-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="1bd79-113">ValueName</span></span> |<span data-ttu-id="1bd79-114">레지스트리 값의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="1bd79-115">레지스트리 키를 추가하거나 제거하려면 **ValueType** 또는 **ValueData**를 지정하지 않고 이 속성을 빈 문자열로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-115">To add or remove a registry key, specify this property as an empty string without specifying **ValueType** or **ValueData**.</span></span> <span data-ttu-id="1bd79-116">레지스트리 키의 기본값을 수정하거나 제거하려면 **ValueType** 또는 **ValueData**도 지정하고 이 속성을 빈 문자열로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying **ValueType** or **ValueData**.</span></span> |
|<span data-ttu-id="1bd79-117">Force</span><span class="sxs-lookup"><span data-stu-id="1bd79-117">Force</span></span> |<span data-ttu-id="1bd79-118">지정된 레지스트리 키가 있을 경우, **Force**를 사용하면 새 값으로 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-118">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="1bd79-119">하위 키가 포함된 레지스트리 키를 삭제하는 경우에는 이 속성을 `$true`로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-119">If deleting a registry key with subkeys, this needs to be `$true`.</span></span> |
|<span data-ttu-id="1bd79-120">Hex</span><span class="sxs-lookup"><span data-stu-id="1bd79-120">Hex</span></span> |<span data-ttu-id="1bd79-121">데이터가 16진수 형식으로 표현될 것인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-121">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="1bd79-122">지정하는 경우 DWORD/QWORD 값 데이터가 16진수 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-122">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="1bd79-123">다른 형식에 대해서는 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-123">Not valid for other types.</span></span> <span data-ttu-id="1bd79-124">기본값은 `$false`입니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="1bd79-125">ValueData</span><span class="sxs-lookup"><span data-stu-id="1bd79-125">ValueData</span></span> |<span data-ttu-id="1bd79-126">레지스트리 값에 대한 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-126">The data for the registry value.</span></span> |
|<span data-ttu-id="1bd79-127">ValueType</span><span class="sxs-lookup"><span data-stu-id="1bd79-127">ValueType</span></span> |<span data-ttu-id="1bd79-128">값의 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-128">Indicates the type of the value.</span></span> <span data-ttu-id="1bd79-129">지원되는 형식은 다음과 같습니다. **문자열**(REG_SZ), **이진**(REG-BINARY), **Dword**(32-bit REG_DWORD), **Qword**(64-bit REG_QWORD), **MultiString**(REG_MULTI_SZ), **ExpandString**(REG_EXPAND_SZ).</span><span class="sxs-lookup"><span data-stu-id="1bd79-129">The supported types are: **String** (REG_SZ), **Binary** (REG-BINARY), **Dword** (32-bit REG_DWORD), **Qword** (64-bit REG_QWORD), **MultiString** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ).</span></span> |

## <a name="common-properties"></a><span data-ttu-id="1bd79-130">공용 속성</span><span class="sxs-lookup"><span data-stu-id="1bd79-130">Common properties</span></span>

|<span data-ttu-id="1bd79-131">속성</span><span class="sxs-lookup"><span data-stu-id="1bd79-131">Property</span></span> |<span data-ttu-id="1bd79-132">Description</span><span class="sxs-lookup"><span data-stu-id="1bd79-132">Description</span></span> |
|---|---|
|<span data-ttu-id="1bd79-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1bd79-133">DependsOn</span></span> |<span data-ttu-id="1bd79-134">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1bd79-135">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="1bd79-136">Ensure</span><span class="sxs-lookup"><span data-stu-id="1bd79-136">Ensure</span></span> |<span data-ttu-id="1bd79-137">키와 값의 존재 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-137">Indicates if the key and value exist.</span></span> <span data-ttu-id="1bd79-138">존재하도록 하려면 이 속성을 **Present**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-138">To ensure that they do, set this property to **Present**.</span></span> <span data-ttu-id="1bd79-139">존재하지 않도록 하려면 이 속성을 **Absent**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-139">To ensure that they do not exist, set the property to **Absent**.</span></span> <span data-ttu-id="1bd79-140">기본값은 **Present**입니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-140">The default value is **Present**.</span></span> |
|<span data-ttu-id="1bd79-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="1bd79-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="1bd79-142">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-142">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="1bd79-143">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-143">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="1bd79-144">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1bd79-144">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="examples"></a><span data-ttu-id="1bd79-145">예</span><span class="sxs-lookup"><span data-stu-id="1bd79-145">Examples</span></span>

### <a name="example-1-ensure-specified-value-and-data-under-specified-registry-key"></a><span data-ttu-id="1bd79-146">예제 1: 지정된 값과 데이터가 지정된 레지스트리 키에 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="1bd79-146">Example 1: Ensure specified Value and Data under specified registry key</span></span>

<span data-ttu-id="1bd79-147">이 예에서는 "ExampleKey1" 라는 키에 속하는 레지스트리 값 "TestValue"가 `HKEY\_LOCAL\_MACHINE` 하이브에 있고 데이터 "TestData"가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-147">This example ensures that the registry value "TestValue" under a key named "ExampleKey1" is present in the `HKEY\_LOCAL\_MACHINE` hive and has the data "TestData".</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey1"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

### <a name="example-2-ensure-specified-registry-key-exists"></a><span data-ttu-id="1bd79-148">예제 2: 지정된 레지스트리 키가 존재하는지 확인</span><span class="sxs-lookup"><span data-stu-id="1bd79-148">Example 2: Ensure specified registry key exists</span></span>

<span data-ttu-id="1bd79-149">이 예제에서는 "ExampleKe2"라는 키가 **HKEY\_LOCAL\_MACHINE** 하이브에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-149">This example ensures that a key named "ExampleKey2" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey2"
        ValueName   = ""
    }
}
```

> [!NOTE]
> <span data-ttu-id="1bd79-150">`HKEY_CURRENT_USER` 하이브에서 레지스트리 설정을 변경하려면 구성이 시스템이 아닌 사용자 자격 증명을 사용하여 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-150">Changing a registry setting in the `HKEY_CURRENT_USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="1bd79-151">**PsDscRunAsCredential** 속성을 사용하여 구성에 대한 사용자 자격 증명을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bd79-151">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="1bd79-152">예제는 [사용자 자격 증명을 사용하여 DSC 실행](../../../configurations/runAsUser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1bd79-152">For an example, see [Running DSC with user credentials](../../../configurations/runAsUser.md).</span></span>
