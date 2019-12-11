---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC ProcessSet 리소스
ms.openlocfilehash: 72925d3a9516f5c0040427773a3b1d66034667bb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953130"
---
# <a name="dsc-processset-resource"></a><span data-ttu-id="ade6c-103">DSC ProcessSet 리소스</span><span class="sxs-lookup"><span data-stu-id="ade6c-103">DSC ProcessSet Resource</span></span>

> <span data-ttu-id="ade6c-104">적용 대상: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="ade6c-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="ade6c-105">Windows PowerShell DSC(필요한 상태 구성)의 **ProcessSet** 리소스에서는 대상 노드에서 프로세스를 구성하는 메커니즘을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="ade6c-106">구문</span><span class="sxs-lookup"><span data-stu-id="ade6c-106">Syntax</span></span>

```Syntax
ProcessSet [string] #ResourceName
{
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="ade6c-107">속성</span><span class="sxs-lookup"><span data-stu-id="ade6c-107">Properties</span></span>

|<span data-ttu-id="ade6c-108">속성</span><span class="sxs-lookup"><span data-stu-id="ade6c-108">Property</span></span> |<span data-ttu-id="ade6c-109">설명</span><span class="sxs-lookup"><span data-stu-id="ade6c-109">Description</span></span> |
|---|---|
|<span data-ttu-id="ade6c-110">경로</span><span class="sxs-lookup"><span data-stu-id="ade6c-110">Path</span></span> |<span data-ttu-id="ade6c-111">프로세스 실행 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-111">The path to the process executable.</span></span> <span data-ttu-id="ade6c-112">실행 파일의 정규화된 경로가 아니라 파일 이름인 경우 DSC 리소스는 환경 `$env:Path` 변수를 검색하여 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-112">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment `$env:Path` variable to find the files.</span></span> <span data-ttu-id="ade6c-113">이 속성의 값이 정규화된 경로인 경우 DSC는 `$env:Path` 환경 변수를 사용하여 파일을 찾지 않으며 경로가 없는 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-113">If the values of this property are fully qualified paths, DSC will not use the `$env:Path` environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="ade6c-114">상대 경로는 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-114">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="ade6c-115">자격 증명</span><span class="sxs-lookup"><span data-stu-id="ade6c-115">Credential</span></span> |<span data-ttu-id="ade6c-116">프로세스를 시작하기 위한 자격 증명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-116">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="ade6c-117">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="ade6c-117">StandardErrorPath</span></span> |<span data-ttu-id="ade6c-118">프로세스가 표준 오류를 쓰는 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-118">The path to which the processes write standard error.</span></span> <span data-ttu-id="ade6c-119">거기에 있던 기존 파일은 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-119">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="ade6c-120">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="ade6c-120">StandardInputPath</span></span> |<span data-ttu-id="ade6c-121">프로세스가 표준 입력을 받는 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-121">The stream from which the process receives standard input.</span></span> |
|<span data-ttu-id="ade6c-122">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="ade6c-122">StandardOutputPath</span></span> |<span data-ttu-id="ade6c-123">프로세스가 표준 출력을 쓰는 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-123">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="ade6c-124">거기에 있던 기존 파일은 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-124">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="ade6c-125">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="ade6c-125">WorkingDirectory</span></span> |<span data-ttu-id="ade6c-126">프로세스에 대한 현재 작업 디렉터리로 사용되는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-126">The location used as the current working directory for the processes.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="ade6c-127">공용 속성</span><span class="sxs-lookup"><span data-stu-id="ade6c-127">Common properties</span></span>

|<span data-ttu-id="ade6c-128">속성</span><span class="sxs-lookup"><span data-stu-id="ade6c-128">Property</span></span> |<span data-ttu-id="ade6c-129">설명</span><span class="sxs-lookup"><span data-stu-id="ade6c-129">Description</span></span> |
|---|---|
|<span data-ttu-id="ade6c-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ade6c-130">DependsOn</span></span> |<span data-ttu-id="ade6c-131">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ade6c-132">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="ade6c-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="ade6c-133">Ensure</span></span> |<span data-ttu-id="ade6c-134">프로세스가 존재하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-134">Specifies whether the processes exists.</span></span> <span data-ttu-id="ade6c-135">프로세스가 존재하도록 하려면 이 속성을 **Present**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-135">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="ade6c-136">그렇지 않으면, **Absent**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-136">Otherwise, set it to **Absent**.</span></span> <span data-ttu-id="ade6c-137">기본값은 **Present**입니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="ade6c-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="ade6c-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="ade6c-139">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="ade6c-140">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ade6c-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="ade6c-141">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ade6c-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>