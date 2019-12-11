---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC WindowsProcess 리소스
ms.openlocfilehash: e168cdebb04f7ec83b73a537a5f188299f40d8b7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952840"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="e2405-103">DSC WindowsProcess 리소스</span><span class="sxs-lookup"><span data-stu-id="e2405-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="e2405-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="e2405-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="e2405-105">Windows PowerShell DSC(필요한 상태 구성)의 **WindowsProcess** 리소스에서는 대상 노드에서 프로세스를 구성하는 메커니즘을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="e2405-106">구문</span><span class="sxs-lookup"><span data-stu-id="e2405-106">Syntax</span></span>

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="e2405-107">속성</span><span class="sxs-lookup"><span data-stu-id="e2405-107">Properties</span></span>

|<span data-ttu-id="e2405-108">속성</span><span class="sxs-lookup"><span data-stu-id="e2405-108">Property</span></span> |<span data-ttu-id="e2405-109">설명</span><span class="sxs-lookup"><span data-stu-id="e2405-109">Description</span></span> |
|---|---|
|<span data-ttu-id="e2405-110">인수</span><span class="sxs-lookup"><span data-stu-id="e2405-110">Arguments</span></span> |<span data-ttu-id="e2405-111">프로세스에 그대로 전달할 인수의 문자열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="e2405-112">몇 개의 인수를 전달해야 하는 경우 모두 이 문자열에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-112">If you need to pass several arguments, put them all in this string.</span></span> |
|<span data-ttu-id="e2405-113">경로</span><span class="sxs-lookup"><span data-stu-id="e2405-113">Path</span></span> |<span data-ttu-id="e2405-114">프로세스 실행 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-114">The path to the process executable.</span></span> <span data-ttu-id="e2405-115">실행 파일의 정규화된 경로가 아니라 파일 이름인 경우 DSC 리소스는 환경 `$env:Path` 변수를 검색하여 실행 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment `$env:Path` variable to find the executable file.</span></span> <span data-ttu-id="e2405-116">이 속성의 값이 정규화된 경로인 경우 DSC는 `$env:Path` 변수를 사용하여 파일을 찾지 않으며 경로가 없는 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-116">If the value of this property is a fully qualified path, DSC will not use the `$env:Path` variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="e2405-117">상대 경로는 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-117">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="e2405-118">자격 증명</span><span class="sxs-lookup"><span data-stu-id="e2405-118">Credential</span></span> |<span data-ttu-id="e2405-119">프로세스를 시작하기 위한 자격 증명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-119">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="e2405-120">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="e2405-120">StandardErrorPath</span></span> |<span data-ttu-id="e2405-121">표준 오류를 쓸 디렉터리 경로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-121">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="e2405-122">거기에 있던 기존 파일은 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-122">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="e2405-123">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="e2405-123">StandardInputPath</span></span> |<span data-ttu-id="e2405-124">표준 입력 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-124">Indicates the standard input location.</span></span> |
|<span data-ttu-id="e2405-125">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="e2405-125">StandardOutputPath</span></span> |<span data-ttu-id="e2405-126">표준 출력을 쓸 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-126">Indicates the location to write the standard output.</span></span> <span data-ttu-id="e2405-127">거기에 있던 기존 파일은 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-127">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="e2405-128">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="e2405-128">WorkingDirectory</span></span> |<span data-ttu-id="e2405-129">프로세스에 대한 현재 작업 디렉터리로 사용할 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-129">Indicates the location that will be used as the current working directory for the process.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="e2405-130">공용 속성</span><span class="sxs-lookup"><span data-stu-id="e2405-130">Common properties</span></span>

|<span data-ttu-id="e2405-131">속성</span><span class="sxs-lookup"><span data-stu-id="e2405-131">Property</span></span> |<span data-ttu-id="e2405-132">설명</span><span class="sxs-lookup"><span data-stu-id="e2405-132">Description</span></span> |
|---|---|
|<span data-ttu-id="e2405-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e2405-133">DependsOn</span></span> |<span data-ttu-id="e2405-134">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e2405-135">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="e2405-136">Ensure</span><span class="sxs-lookup"><span data-stu-id="e2405-136">Ensure</span></span> |<span data-ttu-id="e2405-137">프로세스가 존재하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-137">Indicates if the process exists.</span></span> <span data-ttu-id="e2405-138">프로세스가 존재하도록 하려면 이 속성을 **Present**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-138">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="e2405-139">그렇지 않으면, **Absent**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-139">Otherwise, set it to **Absent**.</span></span> <span data-ttu-id="e2405-140">기본값은 **Present**입니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-140">The default value is **Present**.</span></span> |
|<span data-ttu-id="e2405-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="e2405-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="e2405-142">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2405-142">Sets the credential for running the entire resource as.</span></span> |