---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC 파일 리소스
ms.openlocfilehash: 4c6945d4cdcbc64ac6d52db563823efe8fd0247e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954680"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="b2003-103">DSC 파일 리소스</span><span class="sxs-lookup"><span data-stu-id="b2003-103">DSC File Resource</span></span>

> <span data-ttu-id="b2003-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="b2003-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="b2003-105">Windows PowerShell DSC(필요한 상태 구성)의 **File** 리소스에서는 대상 노드에 있는 파일 및 폴더를 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-105">The **File** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span> <span data-ttu-id="b2003-106">**DestinationPath** 및 **SourcePath**는 둘 다 대상 노드에서 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-106">**DestinationPath** and **SourcePath** must both be accessible by the target Node.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2003-107">구문</span><span class="sxs-lookup"><span data-stu-id="b2003-107">Syntax</span></span>

```Syntax
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="b2003-108">속성</span><span class="sxs-lookup"><span data-stu-id="b2003-108">Properties</span></span>

|<span data-ttu-id="b2003-109">속성</span><span class="sxs-lookup"><span data-stu-id="b2003-109">Property</span></span> |<span data-ttu-id="b2003-110">Description</span><span class="sxs-lookup"><span data-stu-id="b2003-110">Description</span></span> |
|---|---|
|<span data-ttu-id="b2003-111">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="b2003-111">DestinationPath</span></span> |<span data-ttu-id="b2003-112">확인하려는 대상 노드의 위치는 **Ensure** 상태의 **Present** 또는 **Absent**입니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-112">The location, on the target node, you want to ensure is **Present** or **Absent** with **Ensure**.</span></span> |
|<span data-ttu-id="b2003-113">특성</span><span class="sxs-lookup"><span data-stu-id="b2003-113">Attributes</span></span> |<span data-ttu-id="b2003-114">대상으로 지정된 파일 또는 디렉터리에 대한 특성의 필요한 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-114">The desired state of the attributes for the targeted file or directory.</span></span> <span data-ttu-id="b2003-115">유효한 값은 _Archive_, _Hidden_, _ReadOnly_ 및 _System_입니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-115">Valid values are _Archive_, _Hidden_, _ReadOnly_, and _System_.</span></span> |
|<span data-ttu-id="b2003-116">체크섬</span><span class="sxs-lookup"><span data-stu-id="b2003-116">Checksum</span></span> |<span data-ttu-id="b2003-117">두 파일이 동일한 것인지 결정할 때 사용할 체크섬 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-117">The checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="b2003-118">유효한 값은 다음과 같습니다. **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span><span class="sxs-lookup"><span data-stu-id="b2003-118">Valid values include: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span></span> |
|<span data-ttu-id="b2003-119">콘텐츠</span><span class="sxs-lookup"><span data-stu-id="b2003-119">Contents</span></span> |<span data-ttu-id="b2003-120">**Type** **File** 형식과 함께 사용할 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-120">Only valid when used with **Type** **File**.</span></span> <span data-ttu-id="b2003-121">**Ensure**에 대한 콘텐츠가 대상 파일에서 **Present** 또는 **Absent**임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-121">Indicates the contents to **Ensure** are **Present** or **Absent** from the targeted file.</span></span> |
|<span data-ttu-id="b2003-122">자격 증명</span><span class="sxs-lookup"><span data-stu-id="b2003-122">Credential</span></span> |<span data-ttu-id="b2003-123">원본 파일과 같은 리소스에 액세스하는 데 필요한 자격 증명입니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-123">The credentials that are required to access resources, such as source files.</span></span> |
|<span data-ttu-id="b2003-124">Force</span><span class="sxs-lookup"><span data-stu-id="b2003-124">Force</span></span> |<span data-ttu-id="b2003-125">오류가 발생하는 액세스 작업(예: 파일 덮어쓰기나 비어 있지 않은 디렉터리 삭제)을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-125">Overrides access operations that would result in an error (such as overwriting a file or deleting a directory that is not empty).</span></span> <span data-ttu-id="b2003-126">기본값은 `$false`입니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-126">Default value is `$false`.</span></span> |
|<span data-ttu-id="b2003-127">Recurse</span><span class="sxs-lookup"><span data-stu-id="b2003-127">Recurse</span></span> |<span data-ttu-id="b2003-128">**Type** **Directory** 형식과 함께 사용할 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-128">Only valid when used with **Type** **Directory**.</span></span> <span data-ttu-id="b2003-129">모든 하위 디렉터리에 대한 상태 작업을 재귀적으로 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-129">Performs the state operation recursively to all subdirectories.</span></span> <span data-ttu-id="b2003-130">기본값은 `$false`입니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-130">Default value is `$false`.</span></span> |
|<span data-ttu-id="b2003-131">SourcePath</span><span class="sxs-lookup"><span data-stu-id="b2003-131">SourcePath</span></span> |<span data-ttu-id="b2003-132">파일 또는 폴더 리소스를 복사할 원본 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-132">The path from which to copy the file or folder resource.</span></span> |
|<span data-ttu-id="b2003-133">Type</span><span class="sxs-lookup"><span data-stu-id="b2003-133">Type</span></span> |<span data-ttu-id="b2003-134">구성되는 리소스 종류입니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-134">The type of resource being configured.</span></span> <span data-ttu-id="b2003-135">유효한 값은 **Directory** 및 **File**입니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-135">Valid values are **Directory** and **File**.</span></span> <span data-ttu-id="b2003-136">기본값은 **File**입니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-136">Default value is **File**.</span></span> |
|<span data-ttu-id="b2003-137">MatchSource</span><span class="sxs-lookup"><span data-stu-id="b2003-137">MatchSource</span></span> |<span data-ttu-id="b2003-138">리소스가 초기 복사 후에 소스 디렉터리에 추가된 새 파일을 모니터링해야 하는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-138">Determines if the resource should monitor for new files added to the source directory after the initial copy.</span></span> <span data-ttu-id="b2003-139">`$true` 값은 초기 복사 후에 새 원본 파일을 대상으로 복사해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-139">A value of `$true` indicates that, after the initial copy, any new source files should be copied to the destination.</span></span> <span data-ttu-id="b2003-140">`$false`로 설정하면 리소스가 소스 디렉터리의 콘텐츠를 캐시하고 초기 복사 후에 추가된 모든 파일을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-140">If set to `$false`, the resource caches the contents of the source directory and ignores any files added after the initial copy.</span></span> <span data-ttu-id="b2003-141">기본값은 `$false`입니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-141">Default value is `$false`.</span></span> |

> [!WARNING]
> <span data-ttu-id="b2003-142">**Credential** 또는 **PSRunAsCredential**의 값을 지정하지 않으면 리소스는 대상 노드의 컴퓨터 계정을 사용하여 **SourcePath**에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-142">If you do not specify a value for **Credential** or **PSRunAsCredential**, the resource will use the computer account of the target node to access the **SourcePath**.</span></span> <span data-ttu-id="b2003-143">**SourcePath**가 UNC 공유이면 이 액세스로 인해 "액세스 거부" 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-143">When the **SourcePath** is a UNC share, this could result in an "Access Denied" error.</span></span> <span data-ttu-id="b2003-144">이에 따라 권한이 설정되어 있는지 확인하거나, **Credential** 또는 **PSRunAsCredential** 속성을 사용하여 사용해야 하는 계정을 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="b2003-144">Please ensure your permissions are set accordingly, or use the **Credential** or **PSRunAsCredential** properties to specify the account that should be used.</span></span>

## <a name="common-properties"></a><span data-ttu-id="b2003-145">공용 속성</span><span class="sxs-lookup"><span data-stu-id="b2003-145">Common properties</span></span>

|<span data-ttu-id="b2003-146">속성</span><span class="sxs-lookup"><span data-stu-id="b2003-146">Property</span></span> |<span data-ttu-id="b2003-147">Description</span><span class="sxs-lookup"><span data-stu-id="b2003-147">Description</span></span> |
|---|---|
|<span data-ttu-id="b2003-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b2003-148">DependsOn</span></span> |<span data-ttu-id="b2003-149">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b2003-150">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="b2003-151">Ensure</span><span class="sxs-lookup"><span data-stu-id="b2003-151">Ensure</span></span> |<span data-ttu-id="b2003-152">**Destination**에서 파일 및**콘텐츠**가 존재하는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-152">Determines whether the file and **Contents** at the **Destination** should exist or not.</span></span> <span data-ttu-id="b2003-153">해당 파일이 존재하도록 하려면 이 속성을 **Present**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-153">Set this property to **Present** to ensure the file exists.</span></span> <span data-ttu-id="b2003-154">내용이 없도록 하려면 이 속성을 **Absent**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-154">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="b2003-155">기본값은 **Present**입니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-155">The default value is **Present**.</span></span> |
|<span data-ttu-id="b2003-156">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="b2003-156">PsDscRunAsCredential</span></span> |<span data-ttu-id="b2003-157">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-157">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="b2003-158">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-158">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="b2003-159">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b2003-159">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="b2003-160">추가 정보</span><span class="sxs-lookup"><span data-stu-id="b2003-160">Additional information</span></span>

- <span data-ttu-id="b2003-161">**DestinationPath**만 지정하면 리소스는 경로가 있는지(**Present**일 경우) 또는 없는지(**Absent**일 경우) 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-161">When you only specify a **DestinationPath**, the resource ensures that the path exists if **Present** or does not exist if **Absent**.</span></span>
- <span data-ttu-id="b2003-162">**Directory**의 **Type** 값을 사용하여 **SourcePath** 및 **DestinationPath**를 지정하면 리소스는 소스 디렉터리를 대상 경로에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-162">When you specify a **SourcePath** and a **DestinationPath** with a **Type** value of **Directory**, the resource copies source directory to the destination path.</span></span> <span data-ttu-id="b2003-163">**Recurse**, **Force** 및 **MatchSource** 속성은 수행되는 복사 작업 유형을 변경하지만, **Credential**은 소스 디렉터리에 액세스하는 데 사용할 계정을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-163">The properties **Recurse**, **Force**, and **MatchSource** change the type of copy operation performed, while **Credential** determines which account to use to access the source directory.</span></span>
- <span data-ttu-id="b2003-164">**DestinationPath**와 함께 **Attributes** 속성에 대해 **ReadOnly** 값을 지정한 경우 **Ensure** **Present**는 지정된 경로를 만들고, **Contents**는 파일의 콘텐츠를 설정할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-164">If you specified a value of **ReadOnly** for the **Attributes** property alongside a **DestinationPath**, **Ensure** **Present** would create the path specified, while **Contents** would set the contents of the file.</span></span> <span data-ttu-id="b2003-165">**Ensure** **Absent** 설정은 **Attributes** 속성을 완전히 무시하고 지정된 경로에 있는 모든 파일을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-165">An **Ensure** **Absent** setting would ignore the **Attributes** property entirely, and remove any file at the specified path.</span></span>

## <a name="example"></a><span data-ttu-id="b2003-166">예제</span><span class="sxs-lookup"><span data-stu-id="b2003-166">Example</span></span>

<span data-ttu-id="b2003-167">다음 예제에서는 파일 리소스를 사용하여 끌어오기 서버에서 대상 노드로 디렉터리 및 해당 하위 디렉터리를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-167">The following example copies a directory and its subdirectories from a pull server to a target node using the File Resource.</span></span> <span data-ttu-id="b2003-168">작업이 성공하면 로그 리소스는 이벤트 로그에 확인 메시지를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-168">If the operation succeeds, the Log resource writes a confirmation message to the event log.</span></span>

<span data-ttu-id="b2003-169">소스 디렉터리는 끌어오기 서버에서 공유되는 UNC 경로(`\\PullServer\DemoSource`)입니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-169">The source directory is a UNC path (`\\PullServer\DemoSource`) shared from the Pull Server.</span></span> <span data-ttu-id="b2003-170">**Recurse** 속성을 사용하면 하위 디렉터리도 모두 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-170">The **Recurse** property ensures that all subdirectories are copied as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b2003-171">대상 노드의 LCM은 기본적으로 로컬 시스템 계정의 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-171">The LCM on the target Node executes in the context of the local system account by default.</span></span> <span data-ttu-id="b2003-172">**SourcePath**에 액세스 권한을 부여하려면 대상 노드의 컴퓨터 계정에 적절한 권한을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-172">To grant access to the **SourcePath**, give the target Node's computer account appropriate permissions.</span></span> <span data-ttu-id="b2003-173">**Credential** 및 **PSDSCRunAsCredential**은 둘 다 LCM이 **SourcePath**에 액세스하는 데 사용하는 컨텍스트를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-173">The **Credential** and **PSDSCRunAsCredential** both change the context the LCM uses to access the **SourcePath**.</span></span> <span data-ttu-id="b2003-174">**SourcePath**를 액세스하는 데 사용될 계정에도 액세스 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2003-174">You still need to grant access to the account that will be used to access the **SourcePath**.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

<span data-ttu-id="b2003-175">DSC에서 **자격 증명**을 사용하는 방법에 대한 자세한 내용은 [사용자로 실행](../../../configurations/runAsUser.md) 또는 [구성 데이터 자격 증명](../../../configurations/configDataCredentials.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b2003-175">For more on using **Credentials** in DSC see [Run As User](../../../configurations/runAsUser.md) or [Config Data Credentials](../../../configurations/configDataCredentials.md).</span></span>