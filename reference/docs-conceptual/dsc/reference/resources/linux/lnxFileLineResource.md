---
ms.date: 07/17/2020
ms.topic: reference
title: Linux nxFileLine 리소스용 DSC
description: Linux nxFileLine 리소스용 DSC
ms.openlocfilehash: b342021176e4d8584afec82173f31bf5191ad264
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644751"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="db242-103">Linux nxFileLine 리소스용 DSC</span><span class="sxs-lookup"><span data-stu-id="db242-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="db242-104">PowerShell DSC(필요한 상태 구성)의 **nxFileLine** 리소스에서는 Linux 노드 상의 구성 파일 내 줄을 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="db242-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="db242-105">구문</span><span class="sxs-lookup"><span data-stu-id="db242-105">Syntax</span></span>

```Syntax
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="db242-106">속성</span><span class="sxs-lookup"><span data-stu-id="db242-106">Properties</span></span>

|<span data-ttu-id="db242-107">속성</span><span class="sxs-lookup"><span data-stu-id="db242-107">Property</span></span> |<span data-ttu-id="db242-108">Description</span><span class="sxs-lookup"><span data-stu-id="db242-108">Description</span></span> |
|---|---|
|<span data-ttu-id="db242-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="db242-109">FilePath</span></span> |<span data-ttu-id="db242-110">대상 노드에서 줄을 관리하는 파일의 전체 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="db242-110">The full path to the file to manage lines in on the target node.</span></span> |
|<span data-ttu-id="db242-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="db242-111">ContainsLine</span></span> |<span data-ttu-id="db242-112">파일에 존재하도록 할 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="db242-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="db242-113">이 줄은 파일에 존재하지 않는 경우 파일에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="db242-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="db242-114">**ContainsLine** 은 필수지만 필요하지 않은 경우 빈 문자열(`ContainsLine = ""`)로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db242-114">**ContainsLine** is mandatory, but can be set to an empty string (`ContainsLine = ""`) if it is not needed.</span></span> |
|<span data-ttu-id="db242-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="db242-115">DoesNotContainPattern</span></span> |<span data-ttu-id="db242-116">파일에 존재할 수 없는 줄에 대한 정규식 패턴입니다.</span><span class="sxs-lookup"><span data-stu-id="db242-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="db242-117">파일에 존재하고 이 정규식과 일치하는 모든 줄의 경우 파일에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="db242-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="db242-118">공용 속성</span><span class="sxs-lookup"><span data-stu-id="db242-118">Common properties</span></span>

|<span data-ttu-id="db242-119">속성</span><span class="sxs-lookup"><span data-stu-id="db242-119">Property</span></span> |<span data-ttu-id="db242-120">Description</span><span class="sxs-lookup"><span data-stu-id="db242-120">Description</span></span> |
|---|---|
|<span data-ttu-id="db242-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="db242-121">DependsOn</span></span> |<span data-ttu-id="db242-122">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="db242-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="db242-123">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="db242-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="example"></a><span data-ttu-id="db242-124">예제</span><span class="sxs-lookup"><span data-stu-id="db242-124">Example</span></span>

<span data-ttu-id="db242-125">다음 예제에서는 **nxFileLine** 리소스를 사용하여 사용자: monuser가 not requiretty로 구성되도록 `/etc/sudoers` 파일을 구성하는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db242-125">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = "/etc/sudoers"
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```
