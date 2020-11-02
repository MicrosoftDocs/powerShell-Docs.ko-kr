---
ms.date: 09/20/2019
ms.topic: reference
title: DSC 서비스 리소스
description: DSC 서비스 리소스
ms.openlocfilehash: 24121688bc46dcef70e3751d243d140fb7fcc7c9
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142627"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="e04bc-103">DSC 서비스 리소스</span><span class="sxs-lookup"><span data-stu-id="e04bc-103">DSC Service Resource</span></span>

> <span data-ttu-id="e04bc-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="e04bc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="e04bc-105">Windows PowerShell DSC(필요한 상태 구성)의 **서비스** 리소스에서는 대상 노드에 있는 서비스를 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="e04bc-106">구문</span><span class="sxs-lookup"><span data-stu-id="e04bc-106">Syntax</span></span>

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Ignore | Running | Stopped }  ]
    [ Dependencies = [string[]] ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="e04bc-107">속성</span><span class="sxs-lookup"><span data-stu-id="e04bc-107">Properties</span></span>

|<span data-ttu-id="e04bc-108">속성</span><span class="sxs-lookup"><span data-stu-id="e04bc-108">Property</span></span> |<span data-ttu-id="e04bc-109">Description</span><span class="sxs-lookup"><span data-stu-id="e04bc-109">Description</span></span> |
|---|---|
|<span data-ttu-id="e04bc-110">속성</span><span class="sxs-lookup"><span data-stu-id="e04bc-110">Name</span></span> |<span data-ttu-id="e04bc-111">서비스 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-111">Indicates the service name.</span></span> <span data-ttu-id="e04bc-112">이 속성은 경우에 따라 표시 이름과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="e04bc-113">`Get-Service` cmdlet으로 서비스 목록과 현재 상태를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-113">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="e04bc-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="e04bc-114">BuiltInAccount</span></span> |<span data-ttu-id="e04bc-115">서비스에 사용할 로그인 계정을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="e04bc-116">이 속성에 허용된 값은 **LocalService** , **LocalSystem** 및 **NetworkService** 입니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-116">The values that are allowed for this property are: **LocalService** , **LocalSystem** , and **NetworkService** .</span></span> |
|<span data-ttu-id="e04bc-117">자격 증명</span><span class="sxs-lookup"><span data-stu-id="e04bc-117">Credential</span></span> |<span data-ttu-id="e04bc-118">서비스가 실행되는 계정에 대한 자격 증명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="e04bc-119">이 속성과 **BuiltinAccount** 속성은 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-119">This property and the **BuiltinAccount** property cannot be used together.</span></span> |
|<span data-ttu-id="e04bc-120">StartupType</span><span class="sxs-lookup"><span data-stu-id="e04bc-120">StartupType</span></span> |<span data-ttu-id="e04bc-121">서비스의 시작 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-121">Indicates the startup type for the service.</span></span> <span data-ttu-id="e04bc-122">이 속성에 허용된 값은 **Automatic** , **Disabled** 및 **Manual** 입니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-122">The values that are allowed for this property are: **Automatic** , **Disabled** , and **Manual** .</span></span> |
|<span data-ttu-id="e04bc-123">시스템 상태</span><span class="sxs-lookup"><span data-stu-id="e04bc-123">State</span></span> |<span data-ttu-id="e04bc-124">서비스에 대해 확인하려는 상태를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-124">Indicates the state you want to ensure for the service.</span></span> <span data-ttu-id="e04bc-125">값은 다음과 같습니다. **실행 중** 또는 **중지됨** .</span><span class="sxs-lookup"><span data-stu-id="e04bc-125">The values are: **Running** or **Stopped** .</span></span> |
|<span data-ttu-id="e04bc-126">종속성</span><span class="sxs-lookup"><span data-stu-id="e04bc-126">Dependencies</span></span> | <span data-ttu-id="e04bc-127">서비스에 포함되어야 하는 종속성 이름의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-127">An array of the names of the dependencies the service should have.</span></span> |
|<span data-ttu-id="e04bc-128">설명</span><span class="sxs-lookup"><span data-stu-id="e04bc-128">Description</span></span> |<span data-ttu-id="e04bc-129">대상 서비스에 대한 설명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-129">Indicates the description of the target service.</span></span> |
|<span data-ttu-id="e04bc-130">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e04bc-130">DisplayName</span></span> |<span data-ttu-id="e04bc-131">대상 서비스에 대한 표시 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-131">Indicates the display name of the target service.</span></span> |
|<span data-ttu-id="e04bc-132">경로</span><span class="sxs-lookup"><span data-stu-id="e04bc-132">Path</span></span> |<span data-ttu-id="e04bc-133">새 서비스에 대한 이진 파일의 경로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-133">Indicates the path to the binary file for a new service.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="e04bc-134">공용 속성</span><span class="sxs-lookup"><span data-stu-id="e04bc-134">Common properties</span></span>

|<span data-ttu-id="e04bc-135">속성</span><span class="sxs-lookup"><span data-stu-id="e04bc-135">Property</span></span> |<span data-ttu-id="e04bc-136">Description</span><span class="sxs-lookup"><span data-stu-id="e04bc-136">Description</span></span> |
|---|---|
|<span data-ttu-id="e04bc-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e04bc-137">DependsOn</span></span> |<span data-ttu-id="e04bc-138">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e04bc-139">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-139">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="e04bc-140">Ensure</span><span class="sxs-lookup"><span data-stu-id="e04bc-140">Ensure</span></span> |<span data-ttu-id="e04bc-141">대상 서비스가 시스템에 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-141">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="e04bc-142">대상 서비스가 존재하지 않도록 하려면 이 속성을 **Absent** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-142">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="e04bc-143">서비스가 존재하도록 하려면 이 속성을 **Present** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-143">Setting it to **Present** ensures that target service exists.</span></span> <span data-ttu-id="e04bc-144">기본값은 **Present** 입니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-144">The default value is **Present** .</span></span> |
|<span data-ttu-id="e04bc-145">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="e04bc-145">PsDscRunAsCredential</span></span> |<span data-ttu-id="e04bc-146">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-146">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="e04bc-147">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e04bc-147">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="e04bc-148">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e04bc-148">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="e04bc-149">예제</span><span class="sxs-lookup"><span data-stu-id="e04bc-149">Example</span></span>

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```
