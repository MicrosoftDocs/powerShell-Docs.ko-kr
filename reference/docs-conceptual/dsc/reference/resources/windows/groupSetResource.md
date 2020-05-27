---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
description: 대상 노드에 있는 로컬 그룹을 관리하는 메커니즘을 제공합니다.
title: DSC GroupSet 리소스
ms.openlocfilehash: 99b9cafdd4d799e18e1b9b1f08d7dd41ec435711
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560341"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="dfe94-104">DSC GroupSet 리소스</span><span class="sxs-lookup"><span data-stu-id="dfe94-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="dfe94-105">적용 대상: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="dfe94-105">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="dfe94-106">Windows PowerShell DSC(필요한 상태 구성)의 **GroupSet** 리소스에서는 대상 노드에 있는 로컬 그룹을 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="dfe94-107">이 리소스는 `GroupName` 매개 변수에 지정된 각 그룹에 대해 [그룹 리소스](groupResource.md)를 호출하는 [복합 리소스](../../../resources/authoringResourceComposite.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-107">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="dfe94-108">두 개 이상의 그룹에서 동일한 구성원 목록을 추가 및/또는 제거하거나 두 개 이상의 그룹을 제거하거나 구성원 목록이 동일한 두 개 이상의 그룹을 추가하려는 경우 이 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="dfe94-109">구문</span><span class="sxs-lookup"><span data-stu-id="dfe94-109">Syntax</span></span>

```Syntax
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Members = [string[]] ]
    [ Description = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="dfe94-110">속성</span><span class="sxs-lookup"><span data-stu-id="dfe94-110">Properties</span></span>

|<span data-ttu-id="dfe94-111">속성</span><span class="sxs-lookup"><span data-stu-id="dfe94-111">Property</span></span> |<span data-ttu-id="dfe94-112">Description</span><span class="sxs-lookup"><span data-stu-id="dfe94-112">Description</span></span> |
|---|---|
|<span data-ttu-id="dfe94-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="dfe94-113">GroupName</span></span> |<span data-ttu-id="dfe94-114">상태를 확인하려는 그룹의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-114">The names of the groups for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="dfe94-115">구성원</span><span class="sxs-lookup"><span data-stu-id="dfe94-115">Members</span></span> |<span data-ttu-id="dfe94-116">현재 그룹 구성원 자격을 지정된 구성원으로 바꾸려면 이 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-116">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="dfe94-117">이 속성의 값은 `Domain\UserName` 형식의 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-117">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="dfe94-118">구성에서 이 속성을 설정하는 경우 **MembersToExclude** 또는 **MembersToInclude** 속성을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="dfe94-118">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="dfe94-119">사용할 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-119">Doing so will generate an error.</span></span> |
|<span data-ttu-id="dfe94-120">Description</span><span class="sxs-lookup"><span data-stu-id="dfe94-120">Description</span></span> |<span data-ttu-id="dfe94-121">그룹에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-121">The description of the group.</span></span> |
|<span data-ttu-id="dfe94-122">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="dfe94-122">MembersToInclude</span></span> |<span data-ttu-id="dfe94-123">그룹의 기존 구성원 자격에 구성원을 추가하려면 이 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-123">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="dfe94-124">이 속성의 값은 `Domain\UserName` 형식의 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-124">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="dfe94-125">구성에서 이 속성을 설정하는 경우 **Members** 속성을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="dfe94-125">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="dfe94-126">사용할 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-126">Doing so will generate an error.</span></span> |
|<span data-ttu-id="dfe94-127">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="dfe94-127">MembersToExclude</span></span> |<span data-ttu-id="dfe94-128">그룹의 기존 구성원 자격에서 구성원을 제거하려면 이 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-128">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="dfe94-129">이 속성의 값은 `Domain\UserName` 형식의 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-129">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="dfe94-130">구성에서 이 속성을 설정하는 경우 **Members** 속성을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="dfe94-130">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="dfe94-131">사용할 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-131">Doing so will generate an error.</span></span> |
|<span data-ttu-id="dfe94-132">자격 증명</span><span class="sxs-lookup"><span data-stu-id="dfe94-132">Credential</span></span> |<span data-ttu-id="dfe94-133">원격 리소스에 액세스하는 데 필요한 자격 증명입니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-133">The credentials required to access remote resources.</span></span> <span data-ttu-id="dfe94-134">이 계정에는 로컬이 아닌 모든 계정을 그룹에 추가할 수 있는 Active Directory 사용 권한이 있어야 합니다. 그렇지 않으면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-134">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="dfe94-135">공용 속성</span><span class="sxs-lookup"><span data-stu-id="dfe94-135">Common properties</span></span>

|<span data-ttu-id="dfe94-136">속성</span><span class="sxs-lookup"><span data-stu-id="dfe94-136">Property</span></span> |<span data-ttu-id="dfe94-137">Description</span><span class="sxs-lookup"><span data-stu-id="dfe94-137">Description</span></span> |
|---|---|
|<span data-ttu-id="dfe94-138">DependsOn</span><span class="sxs-lookup"><span data-stu-id="dfe94-138">DependsOn</span></span> |<span data-ttu-id="dfe94-139">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-139">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="dfe94-140">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-140">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="dfe94-141">Ensure</span><span class="sxs-lookup"><span data-stu-id="dfe94-141">Ensure</span></span> |<span data-ttu-id="dfe94-142">그룹이 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-142">Indicates whether the groups exist.</span></span> <span data-ttu-id="dfe94-143">그룹이 존재하지 않도록 하려면 이 속성을 **Absent**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-143">Set this property to **Absent** to ensure that the groups do not exist.</span></span> <span data-ttu-id="dfe94-144">**Present**로 설정하면 그룹이 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-144">Setting it to **Present** ensures that the groups exist.</span></span> <span data-ttu-id="dfe94-145">기본값은 **Present**입니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-145">The default value is **Present**.</span></span> |
|<span data-ttu-id="dfe94-146">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="dfe94-146">PsDscRunAsCredential</span></span> |<span data-ttu-id="dfe94-147">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-147">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="dfe94-148">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-148">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="dfe94-149">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dfe94-149">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="dfe94-150">예제 1: 그룹이 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="dfe94-150">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="dfe94-151">다음 예제에서는 "myGroup" 및 "myOtherGroup"이라는 두 그룹이 있는지 확인하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-151">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE]
> <span data-ttu-id="dfe94-152">이 예제에서는 편의상 일반 텍스트 자격 증명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dfe94-152">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="dfe94-153">구성 MOF 파일에서 자격 증명을 암호화하는 방법에 대한 자세한 내용은 [MOF 파일 보안](../../../pull-server/secureMOF.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dfe94-153">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>
