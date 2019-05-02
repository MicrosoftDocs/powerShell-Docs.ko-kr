---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
description: 대상 노드에 있는 로컬 그룹을 관리하는 메커니즘을 제공합니다.
title: DSC GroupSet 리소스
ms.openlocfilehash: afe4c4d33ac5620c411481e93d76a1f90c26deb9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077180"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="7674a-104">DSC GroupSet 리소스</span><span class="sxs-lookup"><span data-stu-id="7674a-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="7674a-105">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="7674a-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="7674a-106">Windows PowerShell DSC(Desired State Configuration)의 **GroupSet** 리소스에서는 대상 노드에 있는 로컬 그룹을 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="7674a-107">이 리소스는 `GroupName` 매개 변수에 지정된 각 그룹에 대해 [그룹 리소스](groupResource.md)를 호출하는 [복합 리소스](../../../resources/authoringResourceComposite.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-107">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="7674a-108">두 개 이상의 그룹에서 동일한 구성원 목록을 추가 및/또는 제거하거나 두 개 이상의 그룹을 제거하거나 구성원 목록이 동일한 두 개 이상의 그룹을 추가하려는 경우 이 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="7674a-109">구문</span><span class="sxs-lookup"><span data-stu-id="7674a-109">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="7674a-110">속성</span><span class="sxs-lookup"><span data-stu-id="7674a-110">Properties</span></span>

|  <span data-ttu-id="7674a-111">속성</span><span class="sxs-lookup"><span data-stu-id="7674a-111">Property</span></span>  |  <span data-ttu-id="7674a-112">설명</span><span class="sxs-lookup"><span data-stu-id="7674a-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="7674a-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="7674a-113">GroupName</span></span>| <span data-ttu-id="7674a-114">상태를 확인하려는 그룹의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="7674a-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="7674a-115">MembersToExclude</span></span>| <span data-ttu-id="7674a-116">그룹의 기존 구성원 자격에서 구성원을 제거하려면 이 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="7674a-117">이 속성의 값은 폼의 문자열 배열을 *Domain*\\*UserName* 형식의 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="7674a-118">구성에서 이 속성을 설정하는 경우 **Members** 속성을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="7674a-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="7674a-119">사용할 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="7674a-120">자격 증명</span><span class="sxs-lookup"><span data-stu-id="7674a-120">Credential</span></span>| <span data-ttu-id="7674a-121">원격 리소스에 액세스하는 데 필요한 자격 증명입니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="7674a-122">**참고**: 이 계정에는 로컬이 아닌 모든 계정을 그룹에 추가할 수 있는 Active Directory 사용 권한이 있어야 합니다. 그렇지 않으면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="7674a-123">Ensure</span><span class="sxs-lookup"><span data-stu-id="7674a-123">Ensure</span></span>| <span data-ttu-id="7674a-124">그룹이 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="7674a-125">그룹이 존재하지 않도록 하려면 이 속성을 "Absent"로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="7674a-126">그룹이 존재하도록 하려면 이 속성을 "Present"(기본값)로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="7674a-127">구성원</span><span class="sxs-lookup"><span data-stu-id="7674a-127">Members</span></span>| <span data-ttu-id="7674a-128">현재 그룹 구성원 자격을 지정된 구성원으로 바꾸려면 이 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="7674a-129">이 속성의 값은 폼의 문자열 배열을 *Domain*\\*UserName* 형식의 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="7674a-130">구성에서 이 속성을 설정하는 경우 **MembersToExclude** 또는 **MembersToInclude** 속성을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="7674a-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="7674a-131">사용할 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="7674a-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="7674a-132">MembersToInclude</span></span>| <span data-ttu-id="7674a-133">그룹의 기존 구성원 자격에 구성원을 추가하려면 이 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="7674a-134">이 속성의 값은 폼의 문자열 배열을 *Domain*\\*UserName* 형식의 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="7674a-135">구성에서 이 속성을 설정하는 경우 **Members** 속성을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="7674a-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="7674a-136">사용할 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="7674a-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7674a-137">DependsOn</span></span> | <span data-ttu-id="7674a-138">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7674a-139">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하는 구문은 \`DependsOn = "[ResourceType]ResourceName"\`\`입니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="7674a-140">예제 1: 그룹이 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="7674a-140">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="7674a-141">다음 예제에서는 "myGroup" 및 "myOtherGroup"이라는 두 그룹이 있는지 확인하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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
> <span data-ttu-id="7674a-142">이 예제에서는 편의상 일반 텍스트 자격 증명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7674a-142">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="7674a-143">구성 MOF 파일에서 자격 증명을 암호화하는 방법에 대한 자세한 내용은 [MOF 파일 보안](../../../pull-server/secureMOF.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7674a-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>
