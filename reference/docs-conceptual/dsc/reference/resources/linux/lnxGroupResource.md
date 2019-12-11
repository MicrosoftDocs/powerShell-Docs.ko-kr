---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Linux용 DSC nxGroup 리소스
ms.openlocfilehash: 098ae2e8ab183934ec3c185c0fd237731b1353dc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953210"
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="74e74-103">Linux용 DSC nxGroup 리소스</span><span class="sxs-lookup"><span data-stu-id="74e74-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="74e74-104">PowerShell DSC(필요한 상태 구성)의 **nxGroup** 리소스에서는 Linux 노드에 있는 로컬 그룹을 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="74e74-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="74e74-105">구문</span><span class="sxs-lookup"><span data-stu-id="74e74-105">Syntax</span></span>

```Syntax
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ PreferredGroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present } ]
}
```

## <a name="properties"></a><span data-ttu-id="74e74-106">속성</span><span class="sxs-lookup"><span data-stu-id="74e74-106">Properties</span></span>

|<span data-ttu-id="74e74-107">속성</span><span class="sxs-lookup"><span data-stu-id="74e74-107">Property</span></span> |<span data-ttu-id="74e74-108">설명</span><span class="sxs-lookup"><span data-stu-id="74e74-108">Description</span></span> |
|---|---|
|<span data-ttu-id="74e74-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="74e74-109">GroupName</span></span> |<span data-ttu-id="74e74-110">특정 상태를 확인하려는 그룹의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="74e74-110">Specifies the name of the group for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="74e74-111">구성원</span><span class="sxs-lookup"><span data-stu-id="74e74-111">Members</span></span> |<span data-ttu-id="74e74-112">그룹을 형성하는 구성원을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="74e74-112">Specifies the members that form the group.</span></span> |
|<span data-ttu-id="74e74-113">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="74e74-113">MembersToInclude</span></span> |<span data-ttu-id="74e74-114">이 그룹의 구성원이 되도록 할 사용자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="74e74-114">Specifies the users who you want to ensure are members of the group.</span></span> |
|<span data-ttu-id="74e74-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="74e74-115">MembersToExclude</span></span> |<span data-ttu-id="74e74-116">이 그룹의 구성원이 되지 않도록 할 사용자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="74e74-116">Specifies the users who you want to ensure are not members of the group.</span></span> |
|<span data-ttu-id="74e74-117">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="74e74-117">PreferredGroupID</span></span> |<span data-ttu-id="74e74-118">가능한 경우 그룹 ID를 제공된 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="74e74-118">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="74e74-119">현재 그룹 ID가 사용 중이라면 다음의 사용 가능한 그룹 ID가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="74e74-119">If the group id is currently in use, the next available group id is used.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="74e74-120">공용 속성</span><span class="sxs-lookup"><span data-stu-id="74e74-120">Common properties</span></span>

|<span data-ttu-id="74e74-121">속성</span><span class="sxs-lookup"><span data-stu-id="74e74-121">Property</span></span> |<span data-ttu-id="74e74-122">설명</span><span class="sxs-lookup"><span data-stu-id="74e74-122">Description</span></span> |
|---|---|
|<span data-ttu-id="74e74-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="74e74-123">DependsOn</span></span> |<span data-ttu-id="74e74-124">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="74e74-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="74e74-125">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="74e74-125">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="74e74-126">Ensure</span><span class="sxs-lookup"><span data-stu-id="74e74-126">Ensure</span></span> |<span data-ttu-id="74e74-127">해당 그룹이 존재하는지를 확인할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="74e74-127">Determines whether to check if the group exists.</span></span> <span data-ttu-id="74e74-128">해당 그룹이 존재하도록 하려면 이 속성을 **Present**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="74e74-128">Set this property to **Present** to ensure the group exists.</span></span> <span data-ttu-id="74e74-129">해당 그룹이 존재하지 않도록 하려면 이 속성을 **Absent**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="74e74-129">Set it to **Absent** to ensure the group does not exist.</span></span> <span data-ttu-id="74e74-130">기본값은 **Present**입니다.</span><span class="sxs-lookup"><span data-stu-id="74e74-130">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="74e74-131">예제</span><span class="sxs-lookup"><span data-stu-id="74e74-131">Example</span></span>

<span data-ttu-id="74e74-132">다음 예제에서는 사용자 ‘monuser’가 존재하고 ‘DBusers’ 그룹의 구성원임을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="74e74-132">The following example ensures that the user 'monuser' exists and is a member of the group 'DBusers'.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
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