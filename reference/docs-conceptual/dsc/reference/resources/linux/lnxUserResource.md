---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Linux용 DSC nxUser 리소스
ms.openlocfilehash: 4cf8080fbfa58e082ed007d42d6aa2648d1cf58a
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557178"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="27475-103">Linux용 DSC nxUser 리소스</span><span class="sxs-lookup"><span data-stu-id="27475-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="27475-104">PowerShell DSC(필요한 상태 구성)의 **nxUser** 리소스에서는 Linux 노드에 있는 로컬 사용자를 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="27475-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="27475-105">구문</span><span class="sxs-lookup"><span data-stu-id="27475-105">Syntax</span></span>

```Syntax
nxUser <string> #ResourceName
{
    UserName = <string>
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="27475-106">속성</span><span class="sxs-lookup"><span data-stu-id="27475-106">Properties</span></span>

|<span data-ttu-id="27475-107">속성</span><span class="sxs-lookup"><span data-stu-id="27475-107">Property</span></span> |<span data-ttu-id="27475-108">특정 상태를 확인하려는 계정 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="27475-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
|<span data-ttu-id="27475-109">UserName</span><span class="sxs-lookup"><span data-stu-id="27475-109">UserName</span></span> |<span data-ttu-id="27475-110">파일 또는 디렉터리에 대한 상태를 확인하려는 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27475-110">Specifies the location where you want to ensure the state for a file or directory.</span></span> |
|<span data-ttu-id="27475-111">FullName</span><span class="sxs-lookup"><span data-stu-id="27475-111">FullName</span></span> |<span data-ttu-id="27475-112">사용자 계정에 사용할 전체 이름을 포함하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="27475-112">A string that contains the full name to use for the user account.</span></span> |
|<span data-ttu-id="27475-113">Description</span><span class="sxs-lookup"><span data-stu-id="27475-113">Description</span></span> |<span data-ttu-id="27475-114">사용자 계정에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="27475-114">The description for the user account.</span></span> |
|<span data-ttu-id="27475-115">암호</span><span class="sxs-lookup"><span data-stu-id="27475-115">Password</span></span> |<span data-ttu-id="27475-116">Linux 컴퓨터용으로 적절한 형태의 사용자 암호 해시입니다.</span><span class="sxs-lookup"><span data-stu-id="27475-116">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="27475-117">일반적으로 솔트된 SHA-256 또는 SHA-512 해시입니다.</span><span class="sxs-lookup"><span data-stu-id="27475-117">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="27475-118">Debian 및 Ubuntu Linux에서 이 값은 `mkpasswd` 명령을 사용하여 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27475-118">On Debian and Ubuntu Linux, this value can be generated with the `mkpasswd` command.</span></span> <span data-ttu-id="27475-119">다른 Linux 배포판의 경우 Python의 암호화 라이브러리의 암호화 방법을 사용하여 해시를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27475-119">For other Linux distros, the crypt method of Python's Crypt library can be used to generate the hash.</span></span> |
|<span data-ttu-id="27475-120">사용 안 함</span><span class="sxs-lookup"><span data-stu-id="27475-120">Disabled</span></span> |<span data-ttu-id="27475-121">계정이 활성화되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="27475-121">Indicates whether the account is enabled.</span></span> <span data-ttu-id="27475-122">이 계정을 사용하지 않도록 하려면 이 속성을 `$true`로 설정하고, 사용하도록 하려면 `$false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="27475-122">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span> |
|<span data-ttu-id="27475-123">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="27475-123">PasswordChangeRequired</span></span> |<span data-ttu-id="27475-124">사용자가 암호를 변경할 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="27475-124">Indicates whether the user can change the password.</span></span> <span data-ttu-id="27475-125">사용자가 암호를 변경할 수 없도록 하려면 이 속성을 `$true`로 설정하고, 사용자가 암호를 변경할 수 있도록 하려면 `$false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="27475-125">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="27475-126">기본값은 `$false`입니다.</span><span class="sxs-lookup"><span data-stu-id="27475-126">The default value is `$false`.</span></span> <span data-ttu-id="27475-127">이 속성은 사용자 계정이 이전에 존재하지 않아서 만들어지는 경우에만 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="27475-127">This property is only evaluated if the user account did not exist previously and is being created.</span></span> |
|<span data-ttu-id="27475-128">HomeDirectory</span><span class="sxs-lookup"><span data-stu-id="27475-128">HomeDirectory</span></span> |<span data-ttu-id="27475-129">사용자에 대한 홈 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="27475-129">The home directory for the user.</span></span> |
|<span data-ttu-id="27475-130">GroupID</span><span class="sxs-lookup"><span data-stu-id="27475-130">GroupID</span></span> |<span data-ttu-id="27475-131">사용자에 대한 주 그룹 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="27475-131">The primary group ID for the user.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="27475-132">공용 속성</span><span class="sxs-lookup"><span data-stu-id="27475-132">Common properties</span></span>

|<span data-ttu-id="27475-133">속성</span><span class="sxs-lookup"><span data-stu-id="27475-133">Property</span></span> |<span data-ttu-id="27475-134">Description</span><span class="sxs-lookup"><span data-stu-id="27475-134">Description</span></span> |
|---|---|
|<span data-ttu-id="27475-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="27475-135">DependsOn</span></span> |<span data-ttu-id="27475-136">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="27475-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="27475-137">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="27475-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="27475-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="27475-138">Ensure</span></span> |<span data-ttu-id="27475-139">계정이 존재하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27475-139">Specifies whether the account exists.</span></span> <span data-ttu-id="27475-140">계정이 존재하도록 하려면 이 속성을 **Present**로 설정하고, 계정이 존재하지 않도록 하려면 **Absent**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="27475-140">Set this property to **Present** to ensure that the account exists, and set it to **Absent** to ensure that the account does not exist.</span></span> |

## <a name="example"></a><span data-ttu-id="27475-141">예제</span><span class="sxs-lookup"><span data-stu-id="27475-141">Example</span></span>

<span data-ttu-id="27475-142">다음 예제에서는 사용자 "monuser"가 존재하고 "DBusers" 그룹의 구성원임을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="27475-142">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
   nxUser UserExample{
      UserName = "monuser"
      Description = "Monitoring user"
      Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
      Ensure = "Present"
      HomeDirectory = "/home/monuser"
   }

   nxGroup GroupExample{
      GroupName = "DBusers"
      Ensure = "Present"
      MembersToInclude = "monuser"
      DependsOn = "[nxUser]UserExample"
   }
}
```
