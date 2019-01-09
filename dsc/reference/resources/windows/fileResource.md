---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 파일 리소스
ms.openlocfilehash: e5f7a91e5f19c8c7bbada090804d8f29a7cfedd5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047772"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="d7300-103">DSC 파일 리소스</span><span class="sxs-lookup"><span data-stu-id="d7300-103">DSC File Resource</span></span>

> <span data-ttu-id="d7300-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d7300-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="d7300-105">PowerShell DSC(필요한 상태 구성)의 파일 리소스에서는 대상 노드에 있는 파일 및 폴더를 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span>

><span data-ttu-id="d7300-106">**참고:** **MatchSource** 속성이 **$false**(기본값)로 설정된 경우 복사할 콘텐츠는 구성을 처음으로 적용할 때 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-106">**Note:** If the **MatchSource** property is set to **$false** (which is the default value), the contents to be copied are cached the first time the configuration is applied.</span></span>
><span data-ttu-id="d7300-107">이후 구성을 적용할 때 **SourcePath**로 지정된 경로에서 업데이트된 파일 및/또는 폴더가 있는지 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-107">Subsequent applications of the configuration will not check for updated files and/or folders in the path specified by **SourcePath**.</span></span> <span data-ttu-id="d7300-108">구성을 적용할 때마다 **SourcePath**에 파일 및/또는 폴더에 대한 업데이트가 있는지 확인하려면 **MatchSource**를 **$true**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-108">If you want to check for updates to the files and/or folders in **SourcePath** every time the configuration is applied, set **MatchSource** to **$true**.</span></span>

## <a name="syntax"></a><span data-ttu-id="d7300-109">구문</span><span class="sxs-lookup"><span data-stu-id="d7300-109">Syntax</span></span>
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="d7300-110">속성</span><span class="sxs-lookup"><span data-stu-id="d7300-110">Properties</span></span>

|  <span data-ttu-id="d7300-111">속성</span><span class="sxs-lookup"><span data-stu-id="d7300-111">Property</span></span>  |  <span data-ttu-id="d7300-112">설명</span><span class="sxs-lookup"><span data-stu-id="d7300-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="d7300-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="d7300-113">DestinationPath</span></span>| <span data-ttu-id="d7300-114">파일 또는 디렉터리에 대한 상태를 확인하려는 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-114">Indicates the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="d7300-115">특성</span><span class="sxs-lookup"><span data-stu-id="d7300-115">Attributes</span></span>| <span data-ttu-id="d7300-116">대상으로 지정된 파일 또는 디렉터리에 대한 특성의 필요한 상태를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-116">Specifies the desired state of the attributes for the targeted file or directory.</span></span>|
| <span data-ttu-id="d7300-117">체크섬</span><span class="sxs-lookup"><span data-stu-id="d7300-117">Checksum</span></span>| <span data-ttu-id="d7300-118">두 파일이 동일한 것인지 결정할 때 사용할 체크섬 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-118">Indicates the checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="d7300-119">__Checksum__을 지정하지 않은 경우 비교에 파일 또는 디렉터리 이름만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-119">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="d7300-120">유효한 값은 다음과 같습니다. Sha-1, SHA-256, SHA-512, createdDate, modifiedDate 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-120">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|
| <span data-ttu-id="d7300-121">콘텐츠</span><span class="sxs-lookup"><span data-stu-id="d7300-121">Contents</span></span>| <span data-ttu-id="d7300-122">특정 문자열과 같이 파일의 내용을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-122">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="d7300-123">자격 증명</span><span class="sxs-lookup"><span data-stu-id="d7300-123">Credential</span></span>| <span data-ttu-id="d7300-124">이러한 액세스가 필요한 경우 소스 파일과 같은 리소스에 액세스하는 데 필요한 자격 증명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-124">Indicates the credentials that are required to access resources, such as source files, if such access is required.</span></span>|
| <span data-ttu-id="d7300-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="d7300-125">Ensure</span></span>| <span data-ttu-id="d7300-126">파일이나 디렉터리가 있는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-126">Indicates if the file or directory exists.</span></span> <span data-ttu-id="d7300-127">파일 또는 디렉터리가 존재하지 않도록 하려면 이 속성을 "Absent"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-127">Set this property to "Absent" to ensure that the file or directory does not exist.</span></span> <span data-ttu-id="d7300-128">파일 또는 디렉터리가 존재하도록 하려면 이 속성을 "Present"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-128">Set it to "Present" to ensure that the file or directory does exist.</span></span> <span data-ttu-id="d7300-129">기본값은 "Present"입니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-129">The default is "Present".</span></span>|
| <span data-ttu-id="d7300-130">Force</span><span class="sxs-lookup"><span data-stu-id="d7300-130">Force</span></span>| <span data-ttu-id="d7300-131">특정 파일 작업(예: 파일 덮어쓰기나 비어 있지 않은 디렉터리 삭제)을 수행하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-131">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="d7300-132">Force 속성을 사용하면 이러한 오류가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-132">Using the Force property overrides such errors.</span></span> <span data-ttu-id="d7300-133">기본값은 __$false__입니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-133">The default value is __$false__.</span></span>|
| <span data-ttu-id="d7300-134">Recurse</span><span class="sxs-lookup"><span data-stu-id="d7300-134">Recurse</span></span>| <span data-ttu-id="d7300-135">하위 디렉터리가 포함되어 있는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-135">Indicates if subdirectories are included.</span></span> <span data-ttu-id="d7300-136">하위 디렉터리가 포함되도록 하려면 이 속성을 __$true__로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-136">Set this property to __$true__ to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="d7300-137">기본값은 __$false__입니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-137">The default is __$false__.</span></span> <span data-ttu-id="d7300-138">**참고**: 이 속성은 Type 속성은 디렉터리에 설정 된 경우에 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-138">**Note**: This property is only valid when the Type property is set to Directory.</span></span>|
| <span data-ttu-id="d7300-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d7300-139">DependsOn</span></span> | <span data-ttu-id="d7300-140">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d7300-141">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-141">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="d7300-142">SourcePath</span><span class="sxs-lookup"><span data-stu-id="d7300-142">SourcePath</span></span>| <span data-ttu-id="d7300-143">파일 또는 폴더 리소스를 복사해 올 소스 경로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-143">Indicates the path from which to copy the file or folder resource.</span></span>|
| <span data-ttu-id="d7300-144">유형</span><span class="sxs-lookup"><span data-stu-id="d7300-144">Type</span></span>| <span data-ttu-id="d7300-145">구성되는 리소스가 디렉터리인지 또는 파일인지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-145">Indicates if the resource being configured is a directory or a file.</span></span> <span data-ttu-id="d7300-146">리소스가 디렉터리임을 나타내려면 이 속성을 "Directory"로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-146">Set this property to "Directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="d7300-147">리소스가 파일을 나타내려면 이 속성을 "File"로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-147">Set it to "File" to indicate that the resource is a file.</span></span> <span data-ttu-id="d7300-148">기본값은 "File"입니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-148">The default value is “File”.</span></span>|
| <span data-ttu-id="d7300-149">MatchSource</span><span class="sxs-lookup"><span data-stu-id="d7300-149">MatchSource</span></span>| <span data-ttu-id="d7300-150">기본값 __$false__로 설정되면, 소스의 파일이 모두(예: 파일 A, B 및 C) 구성이 처음 적용된 대상에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-150">If set to the default value of __$false__, then any files on the source (say, files A, B, and C) will be added to the destination the first time the configuration is applied.</span></span> <span data-ttu-id="d7300-151">새 파일(D)이 소스에 추가되면, 구성이 나중에 다시 적용되는 경우에도 이 파일은 대상에 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-151">If a new file (D) is added to the source, it will not be added to the destination, even when the configuration is re-applied later.</span></span> <span data-ttu-id="d7300-152">값이 __$true__이면, 구성이 적용될 때마다 나중에 소스(예: 이 예의 파일 D)에서 발견되는 새 파일이 대상에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-152">If the value is __$true__, then each time the configuration is applied, new files subsequently found on the source (such as file D in this example) are added to the destination.</span></span> <span data-ttu-id="d7300-153">기본값은 **$false**입니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-153">The default value is **$false**.</span></span>|

## <a name="example"></a><span data-ttu-id="d7300-154">예제</span><span class="sxs-lookup"><span data-stu-id="d7300-154">Example</span></span>

<span data-ttu-id="d7300-155">다음 예제에서는 파일 리소스를 사용하여 소스 컴퓨터(예: "끌어오기" 서버)에서 경로가 `C:\Users\Public\Documents\DSCDemo\DemoSource`인 디렉터리가 대상 노드에도 있도록(모든 하위 디렉터리와 함께) 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-155">The following example shows how to use the File resource to ensure that a directory with the path `C:\Users\Public\Documents\DSCDemo\DemoSource` on a source computer (such as the “pull” server) is also present (along with all subdirectories) on the target node.</span></span> <span data-ttu-id="d7300-156">또한 완료되면 로그에 확인 메시지도 쓰고 로깅 작업 전에 파일 검사 작업이 실행되도록 하는 구문도 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d7300-156">It also writes a confirmatory message to the log when complete and includes a statement to ensure that the file-checking operation runs prior to the logging operation.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```