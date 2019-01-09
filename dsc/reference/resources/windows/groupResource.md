---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 그룹 리소스
ms.openlocfilehash: 9894150f6f749fc23efd4ce2b155b18788557d1d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047573"
---
# <a name="dsc-group-resource"></a><span data-ttu-id="bce82-103">DSC 그룹 리소스</span><span class="sxs-lookup"><span data-stu-id="bce82-103">DSC Group Resource</span></span>

> <span data-ttu-id="bce82-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bce82-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="bce82-105">Windows PowerShell DSC(필요한 상태 구성)의 그룹 리소스에서는 대상 노드에 있는 로컬 그룹을 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="bce82-106">구문</span><span class="sxs-lookup"><span data-stu-id="bce82-106">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="bce82-107">속성</span><span class="sxs-lookup"><span data-stu-id="bce82-107">Properties</span></span>

|  <span data-ttu-id="bce82-108">속성</span><span class="sxs-lookup"><span data-stu-id="bce82-108">Property</span></span>  |  <span data-ttu-id="bce82-109">설명</span><span class="sxs-lookup"><span data-stu-id="bce82-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="bce82-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="bce82-110">GroupName</span></span>| <span data-ttu-id="bce82-111">상태를 확인하려는 그룹의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-111">The name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="bce82-112">자격 증명</span><span class="sxs-lookup"><span data-stu-id="bce82-112">Credential</span></span>| <span data-ttu-id="bce82-113">원격 리소스에 액세스하는 데 필요한 자격 증명입니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="bce82-114">**참고**: 이 계정에는 로컬이 아닌 모든 계정을 그룹에 추가할 수 있는 Active Directory 사용 권한이 있어야 합니다. 그렇지 않으면 구성이 대상 노드에서 실행될 때 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
| <span data-ttu-id="bce82-115">설명</span><span class="sxs-lookup"><span data-stu-id="bce82-115">Description</span></span>| <span data-ttu-id="bce82-116">그룹에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-116">The description of the group.</span></span>|
| <span data-ttu-id="bce82-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="bce82-117">Ensure</span></span>| <span data-ttu-id="bce82-118">그룹이 존재하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-118">Indicates if the group exists.</span></span> <span data-ttu-id="bce82-119">그룹이 존재하지 않도록 하려면 이 속성을 "Absent"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="bce82-120">그룹이 존재하도록 하려면 이 속성을 "Present"(기본값)으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>|
| <span data-ttu-id="bce82-121">구성원</span><span class="sxs-lookup"><span data-stu-id="bce82-121">Members</span></span>| <span data-ttu-id="bce82-122">현재 그룹 구성원 자격을 지정된 구성원으로 바꾸려면 이 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="bce82-123">이 속성의 값은 폼의 문자열 배열을 *Domain*\\*UserName* 형식의 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="bce82-124">구성에서 이 속성을 설정하는 경우 **MembersToExclude** 또는 **MembersToInclude** 속성을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="bce82-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="bce82-125">사용할 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-125">Doing so generates an error.</span></span>|
| <span data-ttu-id="bce82-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="bce82-126">MembersToExclude</span></span>| <span data-ttu-id="bce82-127">그룹의 기존 구성원 자격에서 구성원을 제거하려면 이 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="bce82-128">이 속성의 값은 폼의 문자열 배열을 *Domain*\\*UserName* 형식의 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="bce82-129">구성에서 이 속성을 설정하는 경우 **Members** 속성을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="bce82-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="bce82-130">사용할 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-130">Doing so generates an error.</span></span>|
| <span data-ttu-id="bce82-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="bce82-131">MembersToInclude</span></span>| <span data-ttu-id="bce82-132">그룹의 기존 구성원 자격에 구성원을 추가하려면 이 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="bce82-133">이 속성의 값은 폼의 문자열 배열을 *Domain*\\*UserName* 형식의 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="bce82-134">구성에서 이 속성을 설정하는 경우 **Members** 속성을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="bce82-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="bce82-135">사용할 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-135">Doing so will generate an error.</span></span>|
| <span data-ttu-id="bce82-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="bce82-136">DependsOn</span></span> | <span data-ttu-id="bce82-137">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bce82-138">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하는 구문은 \`DependsOn = "[ResourceType]ResourceName"\`\`입니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="bce82-139">예제 1</span><span class="sxs-lookup"><span data-stu-id="bce82-139">Example 1</span></span>

<span data-ttu-id="bce82-140">다음 예제에서는 “TestGroup”이라는 그룹이 없음을 확인하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a><span data-ttu-id="bce82-141">예 2</span><span class="sxs-lookup"><span data-stu-id="bce82-141">Example 2</span></span>

<span data-ttu-id="bce82-142">다음 예제에서는 Active Directory 사용자를 로컬 관리자 그룹에 다중 컴퓨터 랩 빌드의 일부로 추가하는 방법을 보여줍니다. 이 빌드에서 사용자는 이미 로컬 관리자 계정에 대해 PSCredential을 사용하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Adminstrator account.</span></span>
<span data-ttu-id="bce82-143">이것은 또한 도메인 승급 후 도메인 관리자 계정에도 사용되므로, 기존 PSCredential을 도메인 자격 증명으로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-143">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span>
<span data-ttu-id="bce82-144">그런 다음 구성원 서버에서 도메인 사용자를 로컬 관리자 그룹에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-144">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

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

## <a name="example-3"></a><span data-ttu-id="bce82-145">예제 3</span><span class="sxs-lookup"><span data-stu-id="bce82-145">Example 3</span></span>

<span data-ttu-id="bce82-146">다음 예제에서는 TigerTeamSource.Contoso.Com 서버의 로컬 그룹 TigerTeamAdmins에 특정 도메인 계정 Contoso\JerryG가 포함되지 않도록 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bce82-146">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSrouce {
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