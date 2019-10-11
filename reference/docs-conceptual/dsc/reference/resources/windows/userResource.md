---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC 사용자 리소스
ms.openlocfilehash: dec432c2ff1b4e4408165fef391e77cbf1d85ac4
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953010"
---
# <a name="dsc-user-resource"></a><span data-ttu-id="c4e57-103">DSC 사용자 리소스</span><span class="sxs-lookup"><span data-stu-id="c4e57-103">DSC User Resource</span></span>

> <span data-ttu-id="c4e57-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="c4e57-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="c4e57-105">Windows PowerShell DSC(필요한 상태 구성)의 **사용자** 리소스에서는 대상 노드에 있는 로컬 사용자 계정을 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-105">The **User** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c4e57-106">구문</span><span class="sxs-lookup"><span data-stu-id="c4e57-106">Syntax</span></span>

```Syntax
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="c4e57-107">속성</span><span class="sxs-lookup"><span data-stu-id="c4e57-107">Properties</span></span>

|<span data-ttu-id="c4e57-108">속성</span><span class="sxs-lookup"><span data-stu-id="c4e57-108">Property</span></span> |<span data-ttu-id="c4e57-109">설명</span><span class="sxs-lookup"><span data-stu-id="c4e57-109">Description</span></span> |
|---|---|
|<span data-ttu-id="c4e57-110">UserName</span><span class="sxs-lookup"><span data-stu-id="c4e57-110">UserName</span></span> |<span data-ttu-id="c4e57-111">특정 상태를 확인하려는 계정 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-111">Indicates the account name for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="c4e57-112">설명</span><span class="sxs-lookup"><span data-stu-id="c4e57-112">Description</span></span> |<span data-ttu-id="c4e57-113">사용자 계정에 대해 사용할 설명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-113">Indicates the description you want to use for the user account.</span></span> |
|<span data-ttu-id="c4e57-114">사용 안 함</span><span class="sxs-lookup"><span data-stu-id="c4e57-114">Disabled</span></span> |<span data-ttu-id="c4e57-115">계정이 사용되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="c4e57-116">이 계정을 사용하지 않도록 하려면 이 속성을 `$true`로 설정하고, 사용하도록 하려면 `$false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-116">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span> |
|<span data-ttu-id="c4e57-117">FullName</span><span class="sxs-lookup"><span data-stu-id="c4e57-117">FullName</span></span> |<span data-ttu-id="c4e57-118">사용자 계정에 대해 사용할 전체 이름으로 문자열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-118">Represents a string with the full name you want to use for the user account.</span></span> |
|<span data-ttu-id="c4e57-119">암호</span><span class="sxs-lookup"><span data-stu-id="c4e57-119">Password</span></span> |<span data-ttu-id="c4e57-120">이 계정에 사용할 암호를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-120">Indicates the password you want to use for this account.</span></span> |
|<span data-ttu-id="c4e57-121">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="c4e57-121">PasswordChangeNotAllowed</span></span> |<span data-ttu-id="c4e57-122">사용자가 암호를 변경할 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-122">Indicates if the user can change the password.</span></span> <span data-ttu-id="c4e57-123">사용자가 암호를 변경할 수 없도록 하려면 이 속성을 `$true`로 설정하고, 사용자가 암호를 변경할 수 있도록 하려면 `$false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-123">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="c4e57-124">기본값은 `$false`입니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="c4e57-125">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="c4e57-125">PasswordChangeRequired</span></span> |<span data-ttu-id="c4e57-126">사용자가 다음 로그인 시 암호를 변경해야 하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-126">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="c4e57-127">사용자가 암호를 변경해야 하는 경우 이 속성을 `$true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-127">Set this property to `$true` if the user must change the password.</span></span> <span data-ttu-id="c4e57-128">기본값은 `$true`입니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-128">The default value is `$true`.</span></span> |
|<span data-ttu-id="c4e57-129">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="c4e57-129">PasswordNeverExpires</span></span> |<span data-ttu-id="c4e57-130">암호가 만료될지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-130">Indicates if the password will expire.</span></span> <span data-ttu-id="c4e57-131">이 계정에 대한 암호가 절대로 만료되지 않도록 하려면, 이 속성을 `$true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-131">To ensure that the password for this account will never expire, set this property to `$true`.</span></span> <span data-ttu-id="c4e57-132">암호가 만료될 경우 `$false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-132">Set it to `$false` if the password will expire.</span></span> <span data-ttu-id="c4e57-133">기본값은 `$false`입니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-133">The default value is `$false`.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="c4e57-134">공용 속성</span><span class="sxs-lookup"><span data-stu-id="c4e57-134">Common properties</span></span>

|<span data-ttu-id="c4e57-135">속성</span><span class="sxs-lookup"><span data-stu-id="c4e57-135">Property</span></span> |<span data-ttu-id="c4e57-136">설명</span><span class="sxs-lookup"><span data-stu-id="c4e57-136">Description</span></span> |
|---|---|
|<span data-ttu-id="c4e57-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c4e57-137">DependsOn</span></span> |<span data-ttu-id="c4e57-138">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c4e57-139">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-139">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="c4e57-140">Ensure</span><span class="sxs-lookup"><span data-stu-id="c4e57-140">Ensure</span></span> |<span data-ttu-id="c4e57-141">계정이 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-141">Indicates if the account exists.</span></span> <span data-ttu-id="c4e57-142">계정이 존재하도록 하려면 이 속성을 **Present**로 설정하고, 계정이 존재하지 않도록 하려면 **Absent**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-142">Set this property to **Present** to ensure that the account exists, and set it to **Absent** to ensure that the account does not exist.</span></span> <span data-ttu-id="c4e57-143">기본값은 **Present**입니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-143">The default value is **Present**.</span></span> |
|<span data-ttu-id="c4e57-144">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="c4e57-144">PsDscRunAsCredential</span></span> |<span data-ttu-id="c4e57-145">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-145">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="c4e57-146">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c4e57-146">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="c4e57-147">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c4e57-147">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="c4e57-148">예제</span><span class="sxs-lookup"><span data-stu-id="c4e57-148">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```