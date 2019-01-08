---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 서비스 리소스
ms.openlocfilehash: 09571bd0eaa428e7d0bb7a533d6ad1c0c936e2cf
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047535"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="f27bc-103">DSC 서비스 리소스</span><span class="sxs-lookup"><span data-stu-id="f27bc-103">DSC Service Resource</span></span>

> <span data-ttu-id="f27bc-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f27bc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="f27bc-105">Windows PowerShell DSC(필요한 상태 구성)의 **서비스** 리소스에서는 대상 노드에 있는 서비스를 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f27bc-106">구문</span><span class="sxs-lookup"><span data-stu-id="f27bc-106">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="f27bc-107">속성</span><span class="sxs-lookup"><span data-stu-id="f27bc-107">Properties</span></span>

|  <span data-ttu-id="f27bc-108">속성</span><span class="sxs-lookup"><span data-stu-id="f27bc-108">Property</span></span>  |  <span data-ttu-id="f27bc-109">설명</span><span class="sxs-lookup"><span data-stu-id="f27bc-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="f27bc-110">이름</span><span class="sxs-lookup"><span data-stu-id="f27bc-110">Name</span></span>| <span data-ttu-id="f27bc-111">서비스 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-111">Indicates the service name.</span></span> <span data-ttu-id="f27bc-112">이 속성은 경우에 따라 표시 이름과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="f27bc-113">Get-Service cmdlet으로 서비스 목록과 현재 상태를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-113">You can get a list of the services and their current state with the Get-Service cmdlet.</span></span>|
| <span data-ttu-id="f27bc-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="f27bc-114">BuiltInAccount</span></span>| <span data-ttu-id="f27bc-115">서비스에 사용할 로그인 계정을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="f27bc-116">이 속성에 허용 되는 값은 **LocalService**하십시오 **LocalSystem**, 및 **NetworkService**합니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="f27bc-117">자격 증명</span><span class="sxs-lookup"><span data-stu-id="f27bc-117">Credential</span></span>| <span data-ttu-id="f27bc-118">서비스가 실행되는 계정에 대한 자격 증명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="f27bc-119">이 속성과 __BuiltinAccount__ 속성은 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-119">This property and the __BuiltinAccount__ property cannot be used together.</span></span>|
| <span data-ttu-id="f27bc-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f27bc-120">DependsOn</span></span>| <span data-ttu-id="f27bc-121">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f27bc-122">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-122">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="f27bc-123">StartupType</span><span class="sxs-lookup"><span data-stu-id="f27bc-123">StartupType</span></span>| <span data-ttu-id="f27bc-124">서비스의 시작 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-124">Indicates the startup type for the service.</span></span> <span data-ttu-id="f27bc-125">이 속성에 허용 되는 값은 **자동**하십시오 **사용 안 함**, 및 **수동**</span><span class="sxs-lookup"><span data-stu-id="f27bc-125">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="f27bc-126">State</span><span class="sxs-lookup"><span data-stu-id="f27bc-126">State</span></span>| <span data-ttu-id="f27bc-127">서비스에 대해 확인하려는 상태를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-127">Indicates the state you want to ensure for the service.</span></span>|
| <span data-ttu-id="f27bc-128">설명</span><span class="sxs-lookup"><span data-stu-id="f27bc-128">Description</span></span> | <span data-ttu-id="f27bc-129">대상 서비스에 대한 설명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-129">Indicates the description of the target service.</span></span>|
| <span data-ttu-id="f27bc-130">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f27bc-130">DisplayName</span></span> | <span data-ttu-id="f27bc-131">대상 서비스에 대한 표시 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-131">Indicates the display name of the target service.</span></span>|
| <span data-ttu-id="f27bc-132">Ensure</span><span class="sxs-lookup"><span data-stu-id="f27bc-132">Ensure</span></span> | <span data-ttu-id="f27bc-133">대상 서비스가 시스템에 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-133">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="f27bc-134">대상 서비스가 존재하지 않도록 하려면 이 속성을 **Absent**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-134">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="f27bc-135">대상 서비스가 존재하도록 하려면 이 속성을 **Present**(기본값)로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-135">Setting it to **Present** (the default value) ensures that target service exists.</span></span>|
| <span data-ttu-id="f27bc-136">경로</span><span class="sxs-lookup"><span data-stu-id="f27bc-136">Path</span></span> | <span data-ttu-id="f27bc-137">새 서비스에 대한 이진 파일의 경로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f27bc-137">Indicates the path to the binary file for a new service.</span></span>|

## <a name="example"></a><span data-ttu-id="f27bc-138">예제</span><span class="sxs-lookup"><span data-stu-id="f27bc-138">Example</span></span>

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