---
ms.date: 07/16/2020
keywords: dsc,powershell,configuration,setup
title: DSC 패키지 리소스
ms.openlocfilehash: faeebc5bac7caad733600720f1c9f3d916d4c0a8
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464012"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="44e65-103">DSC 패키지 리소스</span><span class="sxs-lookup"><span data-stu-id="44e65-103">DSC Package Resource</span></span>

> <span data-ttu-id="44e65-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="44e65-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="44e65-105">Windows PowerShell DSC(필요한 상태 구성)의 **Package** 리소스에서는 대상 노드에서 Windows Installer나 setup.exe 패키지와 같은 패키지를 설치하거나 제거하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="44e65-106">구문</span><span class="sxs-lookup"><span data-stu-id="44e65-106">Syntax</span></span>

```Syntax
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ ReturnCode = [UInt32[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="44e65-107">속성</span><span class="sxs-lookup"><span data-stu-id="44e65-107">Properties</span></span>

|<span data-ttu-id="44e65-108">속성</span><span class="sxs-lookup"><span data-stu-id="44e65-108">Property</span></span> |<span data-ttu-id="44e65-109">Description</span><span class="sxs-lookup"><span data-stu-id="44e65-109">Description</span></span> |
|---|---|
|<span data-ttu-id="44e65-110">속성</span><span class="sxs-lookup"><span data-stu-id="44e65-110">Name</span></span> |<span data-ttu-id="44e65-111">특정 상태가 되게 할 패키지의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-111">Indicates the name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="44e65-112">경로</span><span class="sxs-lookup"><span data-stu-id="44e65-112">Path</span></span> |<span data-ttu-id="44e65-113">패키지가 있는 경로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-113">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="44e65-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="44e65-114">ProductId</span></span> |<span data-ttu-id="44e65-115">패키지를 고유하게 식별하는 제품 ID를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-115">Indicates the product ID that uniquely identifies the package.</span></span> |
|<span data-ttu-id="44e65-116">인수</span><span class="sxs-lookup"><span data-stu-id="44e65-116">Arguments</span></span> |<span data-ttu-id="44e65-117">제공된 대로 패키지에 전달할 인수 문자열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="44e65-118">자격 증명</span><span class="sxs-lookup"><span data-stu-id="44e65-118">Credential</span></span> |<span data-ttu-id="44e65-119">원격 소스에 있는 패키지에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="44e65-120">이 속성은 패키지를 설치하는 데 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-120">This property is not used to install the package.</span></span> <span data-ttu-id="44e65-121">패키지는 항상 로컬 시스템에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-121">The package is always installed on the local system.</span></span> |
|<span data-ttu-id="44e65-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="44e65-122">LogPath</span></span> |<span data-ttu-id="44e65-123">패키지를 설치하거나 제거하기 위해 공급자가 로그 파일을 저장하도록 하려는 전체 경로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-123">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |
|<span data-ttu-id="44e65-124">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="44e65-124">ReturnCode</span></span> |<span data-ttu-id="44e65-125">예상된 반환 코드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-125">Indicates the expected return code.</span></span> <span data-ttu-id="44e65-126">실제 반환 코드가 여기에 제공된 예상 값과 일치하지 않는 경우 구성에서 오류를 반환하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-126">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="44e65-127">공용 속성</span><span class="sxs-lookup"><span data-stu-id="44e65-127">Common properties</span></span>

|<span data-ttu-id="44e65-128">속성</span><span class="sxs-lookup"><span data-stu-id="44e65-128">Property</span></span> |<span data-ttu-id="44e65-129">Description</span><span class="sxs-lookup"><span data-stu-id="44e65-129">Description</span></span> |
|---|---|
|<span data-ttu-id="44e65-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="44e65-130">DependsOn</span></span> |<span data-ttu-id="44e65-131">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="44e65-132">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="44e65-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="44e65-133">Ensure</span></span> |<span data-ttu-id="44e65-134">패키지가 설치되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-134">Indicates if the package is installed.</span></span> <span data-ttu-id="44e65-135">패키지가 설치되어 있지 않도록 하려면(또는 설치되어 있다면 패키지를 제거) 이 속성을 **Absent**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-135">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="44e65-136">패키지가 설치되어 있도록 하려면 이 속성을 **Present**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-136">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="44e65-137">기본값은 **Present**입니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="44e65-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="44e65-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="44e65-139">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="44e65-140">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="44e65-141">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="44e65-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="44e65-142">예제</span><span class="sxs-lookup"><span data-stu-id="44e65-142">Example</span></span>

<span data-ttu-id="44e65-143">이 예제에서는 지정된 경로에 있고 지정된 제품 ID를 갖는 .msi 설치 관리자를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="44e65-143">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```
