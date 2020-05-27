---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC WindowsPackageCab 리소스
ms.openlocfilehash: 1b1b8b6d065882400608d26a991318fec9ad5747
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563943"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="b61b2-103">DSC WindowsPackageCab 리소스</span><span class="sxs-lookup"><span data-stu-id="b61b2-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="b61b2-104">적용 대상: Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="b61b2-104">Applies To: Windows PowerShell 5.1</span></span>

<span data-ttu-id="b61b2-105">Windows PowerShell DSC(Desired State Configuration)의 **WindowsPackageCab** 리소스는 대상 노드에서 Windows 캐비닛(.cab) 패키지를 설치하거나 제거하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b61b2-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="b61b2-106">대상 노드에는 DISM PowerShell 모듈이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b61b2-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="b61b2-107">자세한 내용은 [Windows PowerShell에서 DISM 사용](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b61b2-107">For information, see [Use DISM in Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>

## <a name="syntax"></a><span data-ttu-id="b61b2-108">구문</span><span class="sxs-lookup"><span data-stu-id="b61b2-108">Syntax</span></span>

```Syntax
{
    Name = [string]
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    Ensure = [string] { Absent | Present }
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="b61b2-109">속성</span><span class="sxs-lookup"><span data-stu-id="b61b2-109">Properties</span></span>

|<span data-ttu-id="b61b2-110">속성</span><span class="sxs-lookup"><span data-stu-id="b61b2-110">Property</span></span> |<span data-ttu-id="b61b2-111">Description</span><span class="sxs-lookup"><span data-stu-id="b61b2-111">Description</span></span> |
|---|---|
|<span data-ttu-id="b61b2-112">속성</span><span class="sxs-lookup"><span data-stu-id="b61b2-112">Name</span></span> |<span data-ttu-id="b61b2-113">특정 상태가 되게 할 패키지의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b61b2-113">Indicates the name of the package for you want to ensure a specific state.</span></span> |
|<span data-ttu-id="b61b2-114">SourcePath</span><span class="sxs-lookup"><span data-stu-id="b61b2-114">SourcePath</span></span> |<span data-ttu-id="b61b2-115">패키지가 있는 경로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b61b2-115">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="b61b2-116">LogPath</span><span class="sxs-lookup"><span data-stu-id="b61b2-116">LogPath</span></span> |<span data-ttu-id="b61b2-117">패키지를 설치하거나 제거하기 위해 공급자가 로그 파일을 저장하도록 하려는 전체 경로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b61b2-117">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="b61b2-118">공용 속성</span><span class="sxs-lookup"><span data-stu-id="b61b2-118">Common properties</span></span>

|<span data-ttu-id="b61b2-119">속성</span><span class="sxs-lookup"><span data-stu-id="b61b2-119">Property</span></span> |<span data-ttu-id="b61b2-120">Description</span><span class="sxs-lookup"><span data-stu-id="b61b2-120">Description</span></span> |
|---|---|
|<span data-ttu-id="b61b2-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b61b2-121">DependsOn</span></span> |<span data-ttu-id="b61b2-122">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b61b2-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b61b2-123">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="b61b2-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="b61b2-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="b61b2-124">Ensure</span></span> |<span data-ttu-id="b61b2-125">패키지가 설치되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b61b2-125">Indicates if the package is installed.</span></span> <span data-ttu-id="b61b2-126">패키지가 설치되어 있지 않도록 하려면(또는 설치되어 있다면 패키지를 제거) 이 속성을 **Absent**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b61b2-126">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="b61b2-127">패키지가 설치되어 있도록 하려면 이 속성을 **Present**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b61b2-127">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="b61b2-128">**Ensure**는 **WindowsPackageCab** 리소스의 필수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="b61b2-128">**Ensure** is a required property on the **WindowsPackageCab** resource.</span></span> |
|<span data-ttu-id="b61b2-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="b61b2-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="b61b2-130">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b61b2-130">Sets the credential for running the entire resource as.</span></span> |

## <a name="example"></a><span data-ttu-id="b61b2-131">예제</span><span class="sxs-lookup"><span data-stu-id="b61b2-131">Example</span></span>

<span data-ttu-id="b61b2-132">다음 예제 구성에서는 입력 매개 변수를 사용하며 `$Name` 매개 변수로 지정된 .cab 파일이 설치되어 있는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b61b2-132">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

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
