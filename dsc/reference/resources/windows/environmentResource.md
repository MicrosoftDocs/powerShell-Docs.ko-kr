---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 환경 리소스
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077537"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="3a652-103">DSC 환경 리소스</span><span class="sxs-lookup"><span data-stu-id="3a652-103">DSC Environment Resource</span></span>

> <span data-ttu-id="3a652-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3a652-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="3a652-105">PowerShell DSC(필요한 상태 구성)의 __Environment__ 리소스에서는 시스템 환경 변수를 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3a652-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="3a652-106">구문</span><span class="sxs-lookup"><span data-stu-id="3a652-106">Syntax</span></span>
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="3a652-107">속성</span><span class="sxs-lookup"><span data-stu-id="3a652-107">Properties</span></span>

|  <span data-ttu-id="3a652-108">속성</span><span class="sxs-lookup"><span data-stu-id="3a652-108">Property</span></span>  |  <span data-ttu-id="3a652-109">설명</span><span class="sxs-lookup"><span data-stu-id="3a652-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="3a652-110">이름</span><span class="sxs-lookup"><span data-stu-id="3a652-110">Name</span></span>| <span data-ttu-id="3a652-111">특정 상태를 확인하려는 환경 변수의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3a652-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="3a652-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="3a652-112">Ensure</span></span>| <span data-ttu-id="3a652-113">변수가 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3a652-113">Indicates if a variable exists.</span></span> <span data-ttu-id="3a652-114">변수가 없는 경우 환경 변수를 만들거나 변수가 이미 있는 경우 그 값이 __Value__ 속성을 통해 제공된 값과 일치하는지 확인하려면 이 속성을 __있음__으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a652-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="3a652-115">변수가 존재하는 경우 변수를 삭제하려면 이 속성을 __없음__으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a652-115">Set it to __Absent__ to delete the variable if it exists.</span></span>|
| <span data-ttu-id="3a652-116">경로</span><span class="sxs-lookup"><span data-stu-id="3a652-116">Path</span></span>| <span data-ttu-id="3a652-117">구성 중인 환경 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3a652-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="3a652-118">변수가 __Path__ 변수이면 이 속성을 __$true__로 설정하고, 그렇지 않으면 __$false__로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a652-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="3a652-119">기본값은 __$false__입니다.</span><span class="sxs-lookup"><span data-stu-id="3a652-119">The default is __$false__.</span></span> <span data-ttu-id="3a652-120">구성되고 있는 변수가 __Path__ 변수라면, __Value__ 속성을 통해 제공된 값은 기존 값에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a652-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>|
| <span data-ttu-id="3a652-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="3a652-121">DependsOn</span></span> | <span data-ttu-id="3a652-122">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3a652-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3a652-123">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="3a652-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="3a652-124">Value</span><span class="sxs-lookup"><span data-stu-id="3a652-124">Value</span></span>| <span data-ttu-id="3a652-125">환경 변수에 할당할 값입니다.</span><span class="sxs-lookup"><span data-stu-id="3a652-125">The value to assign to the environment variable.</span></span>|

## <a name="example"></a><span data-ttu-id="3a652-126">예제</span><span class="sxs-lookup"><span data-stu-id="3a652-126">Example</span></span>

<span data-ttu-id="3a652-127">다음 예제에서는 __TestEnvironmentVariable__이 있고 그 값이 __TestValue__인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3a652-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="3a652-128">없을 경우 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3a652-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```