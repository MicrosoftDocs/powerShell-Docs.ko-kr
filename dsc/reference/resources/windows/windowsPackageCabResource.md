---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC WindowsPackageCab 리소스
ms.openlocfilehash: 035944e7ca5c7469250c48a19b79f2f2d5d38e9a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681833"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="9a85c-103">DSC WindowsPackageCab 리소스</span><span class="sxs-lookup"><span data-stu-id="9a85c-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="9a85c-104">적용 대상: Windows PowerShell 5.1 이상</span><span class="sxs-lookup"><span data-stu-id="9a85c-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="9a85c-105">Windows PowerShell DSC(Desired State Configuration)의 **WindowsPackageCab** 리소스는 대상 노드에서 Windows 캐비닛(.cab) 패키지를 설치하거나 제거하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9a85c-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="9a85c-106">대상 노드에는 DISM PowerShell 모듈이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a85c-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="9a85c-107">자세한 내용은 [Windows PowerShell에서 DISM 사용](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9a85c-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>


## <a name="syntax"></a><span data-ttu-id="9a85c-108">구문</span><span class="sxs-lookup"><span data-stu-id="9a85c-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="9a85c-109">속성</span><span class="sxs-lookup"><span data-stu-id="9a85c-109">Properties</span></span>

|  <span data-ttu-id="9a85c-110">속성</span><span class="sxs-lookup"><span data-stu-id="9a85c-110">Property</span></span>  |  <span data-ttu-id="9a85c-111">설명</span><span class="sxs-lookup"><span data-stu-id="9a85c-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="9a85c-112">이름</span><span class="sxs-lookup"><span data-stu-id="9a85c-112">Name</span></span>| <span data-ttu-id="9a85c-113">특정 상태가 되게 할 패키지의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9a85c-113">Indicates the name of the package for you want to ensure a specific state.</span></span>|
| <span data-ttu-id="9a85c-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="9a85c-114">Ensure</span></span>| <span data-ttu-id="9a85c-115">패키지가 설치되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9a85c-115">Indicates if the package is installed.</span></span> <span data-ttu-id="9a85c-116">패키지가 설치되어 있지 않도록 하려면(또는 설치되어 있다면 패키지를 제거) 이 속성을 "Absent"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9a85c-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="9a85c-117">패키지가 설치되어 있도록 하려면 이 속성을 "Present"(기본값)으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9a85c-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="9a85c-118">경로</span><span class="sxs-lookup"><span data-stu-id="9a85c-118">Path</span></span>| <span data-ttu-id="9a85c-119">패키지가 있는 경로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9a85c-119">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="9a85c-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="9a85c-120">LogPath</span></span>| <span data-ttu-id="9a85c-121">패키지를 설치하거나 제거하기 위해 공급자가 로그 파일을 저장하도록 하려는 전체 경로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9a85c-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="9a85c-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9a85c-122">DependsOn</span></span> | <span data-ttu-id="9a85c-123">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9a85c-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9a85c-124">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 **ResourceName**이고 해당 형식이 **ResourceType**일 경우, 이 속성을 사용하는 구문은 \`DependsOn = "[ResourceType]ResourceName"\`\`입니다.</span><span class="sxs-lookup"><span data-stu-id="9a85c-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example"></a><span data-ttu-id="9a85c-125">예제</span><span class="sxs-lookup"><span data-stu-id="9a85c-125">Example</span></span>

<span data-ttu-id="9a85c-126">다음 예제 구성에서는 입력 매개 변수를 사용하며 `$Name` 매개 변수로 지정된 .cab 파일이 설치되어 있는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9a85c-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```