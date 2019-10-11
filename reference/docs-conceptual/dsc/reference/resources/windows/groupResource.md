---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC 그룹 리소스
ms.openlocfilehash: 695a914683c6daff44dd2a6c94b6353acf881030
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954660"
---
# <a name="dsc-group-resource"></a><span data-ttu-id="c506d-103">DSC 그룹 리소스</span><span class="sxs-lookup"><span data-stu-id="c506d-103">DSC Group Resource</span></span>

> <span data-ttu-id="c506d-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="c506d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="c506d-105">Windows PowerShell DSC(필요한 상태 구성)의 **그룹** 리소스에서는 대상 노드에 있는 로컬 그룹을 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-105">The **Group** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c506d-106">구문</span><span class="sxs-lookup"><span data-stu-id="c506d-106">Syntax</span></span>

```Syntax
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="c506d-107">속성</span><span class="sxs-lookup"><span data-stu-id="c506d-107">Properties</span></span>

|<span data-ttu-id="c506d-108">속성</span><span class="sxs-lookup"><span data-stu-id="c506d-108">Property</span></span> |<span data-ttu-id="c506d-109">설명</span><span class="sxs-lookup"><span data-stu-id="c506d-109">Description</span></span> |
|---|---|
|<span data-ttu-id="c506d-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="c506d-110">GroupName</span></span> |<span data-ttu-id="c506d-111">상태를 확인하려는 그룹의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-111">The name of the group for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="c506d-112">자격 증명</span><span class="sxs-lookup"><span data-stu-id="c506d-112">Credential</span></span> |<span data-ttu-id="c506d-113">원격 리소스에 액세스하는 데 필요한 자격 증명입니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="c506d-114">이 계정에는 로컬이 아닌 모든 계정을 그룹에 추가할 수 있는 Active Directory 사용 권한이 있어야 합니다. 그렇지 않으면 구성이 대상 노드에서 실행될 때 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-114">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
|<span data-ttu-id="c506d-115">설명</span><span class="sxs-lookup"><span data-stu-id="c506d-115">Description</span></span> |<span data-ttu-id="c506d-116">그룹에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-116">The description of the group.</span></span> |
|<span data-ttu-id="c506d-117">구성원</span><span class="sxs-lookup"><span data-stu-id="c506d-117">Members</span></span> |<span data-ttu-id="c506d-118">현재 그룹 구성원 자격을 지정된 구성원으로 바꾸려면 이 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-118">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="c506d-119">이 속성의 값은 `Domain\UserName` 형식의 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-119">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="c506d-120">구성에서 이 속성을 설정하는 경우 **MembersToExclude** 또는 **MembersToInclude** 속성을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="c506d-120">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="c506d-121">사용할 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-121">Doing so generates an error.</span></span> |
|<span data-ttu-id="c506d-122">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="c506d-122">MembersToExclude</span></span> |<span data-ttu-id="c506d-123">그룹의 기존 구성원 자격에서 구성원을 제거하려면 이 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-123">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="c506d-124">이 속성의 값은 `Domain\UserName` 형식의 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-124">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="c506d-125">구성에서 이 속성을 설정하는 경우 **Members** 속성을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="c506d-125">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="c506d-126">사용할 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-126">Doing so generates an error.</span></span> |
|<span data-ttu-id="c506d-127">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="c506d-127">MembersToInclude</span></span> |<span data-ttu-id="c506d-128">그룹의 기존 구성원 자격에 구성원을 추가하려면 이 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-128">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="c506d-129">이 속성의 값은 `Domain\UserName` 형식의 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-129">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="c506d-130">구성에서 이 속성을 설정하는 경우 **Members** 속성을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="c506d-130">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="c506d-131">사용할 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-131">Doing so will generate an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="c506d-132">공용 속성</span><span class="sxs-lookup"><span data-stu-id="c506d-132">Common properties</span></span>

|<span data-ttu-id="c506d-133">속성</span><span class="sxs-lookup"><span data-stu-id="c506d-133">Property</span></span> |<span data-ttu-id="c506d-134">설명</span><span class="sxs-lookup"><span data-stu-id="c506d-134">Description</span></span> |
|---|---|
|<span data-ttu-id="c506d-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c506d-135">DependsOn</span></span> |<span data-ttu-id="c506d-136">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c506d-137">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="c506d-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="c506d-138">Ensure</span></span> |<span data-ttu-id="c506d-139">그룹이 존재하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-139">Indicates if the group exists.</span></span> <span data-ttu-id="c506d-140">그룹이 존재하지 않도록 하려면 이 속성을 **Absent**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-140">Set this property to **Absent** to ensure that the group does not exist.</span></span> <span data-ttu-id="c506d-141">그룹이 존재하도록 하려면 이 속성을 **Present**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-141">Setting it to **Present** ensures that the group exists.</span></span> <span data-ttu-id="c506d-142">기본값은 **Present**입니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-142">The default value is **Present**.</span></span> |
|<span data-ttu-id="c506d-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="c506d-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="c506d-144">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="c506d-145">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="c506d-146">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c506d-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensure-group-is-not-present"></a><span data-ttu-id="c506d-147">예제 1: 그룹이 존재하지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-147">Example 1: Ensure group is not present</span></span>

<span data-ttu-id="c506d-148">다음 예제에서는 “TestGroup”이라는 그룹이 없음을 확인하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-148">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present"
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2-add-domain-user-to-local-group"></a><span data-ttu-id="c506d-149">예제 2: 로컬 그룹에 도메인 사용자 추가</span><span class="sxs-lookup"><span data-stu-id="c506d-149">Example 2: Add domain user to local group</span></span>

<span data-ttu-id="c506d-150">다음 예제에서는 Active Directory 사용자를 로컬 관리자 그룹에 다중 머신 랩 빌드의 일부로 추가하는 방법을 보여줍니다. 여기에서 사용자는 이미 로컬 관리자 계정에 대해 PSCredential을 사용하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-150">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Administrator account.</span></span> <span data-ttu-id="c506d-151">이것은 또한 도메인 승급 후 도메인 관리자 계정에도 사용되므로, 기존 PSCredential을 도메인 자격 증명으로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-151">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span> <span data-ttu-id="c506d-152">그런 다음 구성원 서버에서 도메인 사용자를 로컬 관리자 그룹에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-152">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a><span data-ttu-id="c506d-153">예제 3</span><span class="sxs-lookup"><span data-stu-id="c506d-153">Example 3</span></span>

<span data-ttu-id="c506d-154">다음 예제에서는 TigerTeamSource.Contoso.Com 서버의 로컬 그룹 TigerTeamAdmins에 특정 도메인 계정 Contoso\JerryG가 포함되지 않도록 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c506d-154">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSource {
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node TigerTeamSource.Contoso.Com {
        Group TigerTeamAdmins {
            GroupName        = 'TigerTeamAdmins'
            Ensure           = 'Present'
            MembersToExclude = "Contoso\JerryG"
        }
    }
}
```