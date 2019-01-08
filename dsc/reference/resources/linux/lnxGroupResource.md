---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Linux용 DSC nxGroup 리소스
ms.openlocfilehash: c61b6ab4a8c56d085b5297dcfc7582187d54f946
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047832"
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="de06f-103">Linux용 DSC nxGroup 리소스</span><span class="sxs-lookup"><span data-stu-id="de06f-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="de06f-104">PowerShell DSC(필요한 상태 구성)의 **nxGroup** 리소스에서는 Linux 노드에 있는 로컬 그룹을 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="de06f-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="de06f-105">구문</span><span class="sxs-lookup"><span data-stu-id="de06f-105">Syntax</span></span>

```
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present } ]
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="de06f-106">속성</span><span class="sxs-lookup"><span data-stu-id="de06f-106">Properties</span></span>

|  <span data-ttu-id="de06f-107">속성</span><span class="sxs-lookup"><span data-stu-id="de06f-107">Property</span></span> |  <span data-ttu-id="de06f-108">설명</span><span class="sxs-lookup"><span data-stu-id="de06f-108">Description</span></span> |
|---|---|
| <span data-ttu-id="de06f-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="de06f-109">GroupName</span></span>| <span data-ttu-id="de06f-110">특정 상태를 확인하려는 그룹의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="de06f-110">Specifies the name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="de06f-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="de06f-111">Ensure</span></span>| <span data-ttu-id="de06f-112">해당 그룹이 존재하는지를 확인할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="de06f-112">Determines whether to check if the group exists.</span></span> <span data-ttu-id="de06f-113">해당 그룹이 존재하도록 하려면 이 속성을 "Present"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="de06f-113">Set this property to "Present" to ensure the group exists.</span></span> <span data-ttu-id="de06f-114">해당 그룹이 존재하지 않도록 하려면 이 속성을 "Absent"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="de06f-114">Set it to "Absent" to ensure the group does not exist.</span></span> <span data-ttu-id="de06f-115">기본값은 "Present"입니다.</span><span class="sxs-lookup"><span data-stu-id="de06f-115">The default value is "Present".</span></span>|
| <span data-ttu-id="de06f-116">구성원</span><span class="sxs-lookup"><span data-stu-id="de06f-116">Members</span></span>| <span data-ttu-id="de06f-117">그룹을 형성하는 구성원을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="de06f-117">Specifies the members that form the group.</span></span>|
| <span data-ttu-id="de06f-118">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="de06f-118">MembersToInclude</span></span>| <span data-ttu-id="de06f-119">이 그룹의 구성원이 되도록 할 사용자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="de06f-119">Specifies the users who you want to ensure are members of the group.</span></span>|
| <span data-ttu-id="de06f-120">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="de06f-120">MembersToExclude</span></span>| <span data-ttu-id="de06f-121">이 그룹의 구성원이 되지 않도록 할 사용자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="de06f-121">Specifies the users who you want to ensure are not members of the group.</span></span>|
| <span data-ttu-id="de06f-122">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="de06f-122">PreferredGroupID</span></span>| <span data-ttu-id="de06f-123">가능한 경우 그룹 ID를 제공된 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="de06f-123">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="de06f-124">현재 그룹 ID가 사용 중이라면 다음의 사용 가능한 그룹 ID가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="de06f-124">If the group id is currently in use, the next available group id is used.</span></span>|
| <span data-ttu-id="de06f-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="de06f-125">DependsOn</span></span> | <span data-ttu-id="de06f-126">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="de06f-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="de06f-127">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 **ID**가 **ResourceName**이고 해당 형식이 **ResourceType**일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = '[ResourceType]ResourceName'`입니다.</span><span class="sxs-lookup"><span data-stu-id="de06f-127">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="de06f-128">예제</span><span class="sxs-lookup"><span data-stu-id="de06f-128">Example</span></span>

<span data-ttu-id="de06f-129">다음 예제에서는 사용자 ‘monuser’가 존재하고 ‘DBusers’ 그룹의 구성원임을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="de06f-129">The following example ensures that the user 'monuser' exists and is a member of the group 'DBusers'.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```