---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 패키지 리소스
ms.openlocfilehash: 9285df71a303c9a53dd50d450272575a64e962e7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077197"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="5ef12-103">DSC 패키지 리소스</span><span class="sxs-lookup"><span data-stu-id="5ef12-103">DSC Package Resource</span></span>

<span data-ttu-id="5ef12-104">_적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="5ef12-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="5ef12-105">Windows PowerShell DSC(필요한 상태 구성)의 **Package** 리소스에서는 대상 노드에서 Windows Installer나 setup.exe 패키지와 같은 패키지를 설치하거나 제거하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef12-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="5ef12-106">구문</span><span class="sxs-lookup"><span data-stu-id="5ef12-106">Syntax</span></span>

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="5ef12-107">속성</span><span class="sxs-lookup"><span data-stu-id="5ef12-107">Properties</span></span>

| <span data-ttu-id="5ef12-108">속성</span><span class="sxs-lookup"><span data-stu-id="5ef12-108">Property</span></span> | <span data-ttu-id="5ef12-109">설명</span><span class="sxs-lookup"><span data-stu-id="5ef12-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="5ef12-110">이름</span><span class="sxs-lookup"><span data-stu-id="5ef12-110">Name</span></span>| <span data-ttu-id="5ef12-111">특정 상태가 되게 할 패키지의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5ef12-111">Indicates the name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="5ef12-112">경로</span><span class="sxs-lookup"><span data-stu-id="5ef12-112">Path</span></span>| <span data-ttu-id="5ef12-113">패키지가 있는 경로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5ef12-113">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="5ef12-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="5ef12-114">ProductId</span></span>| <span data-ttu-id="5ef12-115">패키지를 고유하게 식별하는 제품 ID를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5ef12-115">Indicates the product ID that uniquely identifies the package.</span></span>|
| <span data-ttu-id="5ef12-116">인수</span><span class="sxs-lookup"><span data-stu-id="5ef12-116">Arguments</span></span>| <span data-ttu-id="5ef12-117">제공된 대로 패키지에 전달할 인수 문자열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef12-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="5ef12-118">자격 증명</span><span class="sxs-lookup"><span data-stu-id="5ef12-118">Credential</span></span>| <span data-ttu-id="5ef12-119">원격 소스에 있는 패키지에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef12-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="5ef12-120">이 속성은 패키지를 설치하는 데 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef12-120">This property is not used to install the package.</span></span> <span data-ttu-id="5ef12-121">패키지는 항상 로컬 시스템에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef12-121">The package is always installed on the local system.</span></span>|
| <span data-ttu-id="5ef12-122">Ensure</span><span class="sxs-lookup"><span data-stu-id="5ef12-122">Ensure</span></span>| <span data-ttu-id="5ef12-123">패키지가 설치되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5ef12-123">Indicates if the package is installed.</span></span> <span data-ttu-id="5ef12-124">패키지가 설치되어 있지 않도록 하려면(또는 설치되어 있다면 패키지를 제거) 이 속성을 "Absent"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef12-124">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="5ef12-125">패키지가 설치되어 있도록 하려면 이 속성을 "Present"(기본값)으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef12-125">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="5ef12-126">LogPath</span><span class="sxs-lookup"><span data-stu-id="5ef12-126">LogPath</span></span>| <span data-ttu-id="5ef12-127">패키지를 설치하거나 제거하기 위해 공급자가 로그 파일을 저장하도록 하려는 전체 경로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5ef12-127">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="5ef12-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5ef12-128">DependsOn</span></span> | <span data-ttu-id="5ef12-129">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5ef12-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5ef12-130">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 **ResourceName**이고 해당 형식이 **ResourceType**일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="5ef12-130">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="5ef12-131">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="5ef12-131">ReturnCode</span></span>| <span data-ttu-id="5ef12-132">예상된 반환 코드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5ef12-132">Indicates the expected return code.</span></span> <span data-ttu-id="5ef12-133">실제 반환 코드가 여기에 제공된 예상 값과 일치하지 않는 경우 구성에서 오류를 반환하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ef12-133">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|

## <a name="example"></a><span data-ttu-id="5ef12-134">예제</span><span class="sxs-lookup"><span data-stu-id="5ef12-134">Example</span></span>

<span data-ttu-id="5ef12-135">이 예제에서는 지정된 경로에 있고 지정된 제품 ID를 갖는 .msi 설치 관리자를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef12-135">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

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