---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 파일 리소스
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077333"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="0d71e-103">DSC 파일 리소스</span><span class="sxs-lookup"><span data-stu-id="0d71e-103">DSC File Resource</span></span>

> <span data-ttu-id="0d71e-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0d71e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="0d71e-105">PowerShell DSC(Desired State Configuration)의 파일 리소스에서는 대상 노드에 있는 파일 및 폴더를 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span> <span data-ttu-id="0d71e-106">**DestinationPath** 및 **SourcePath**는 둘 다 대상 노드에서 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-106">The **DestinationPath** and **SourcePath** must both be accessible by the target Node.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d71e-107">구문</span><span class="sxs-lookup"><span data-stu-id="0d71e-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="0d71e-108">속성</span><span class="sxs-lookup"><span data-stu-id="0d71e-108">Properties</span></span>

|<span data-ttu-id="0d71e-109">속성</span><span class="sxs-lookup"><span data-stu-id="0d71e-109">Property</span></span>       |<span data-ttu-id="0d71e-110">설명</span><span class="sxs-lookup"><span data-stu-id="0d71e-110">Description</span></span>                                                                   |<span data-ttu-id="0d71e-111">필수</span><span class="sxs-lookup"><span data-stu-id="0d71e-111">Required</span></span>|<span data-ttu-id="0d71e-112">Default</span><span class="sxs-lookup"><span data-stu-id="0d71e-112">Default</span></span>|
|---------------|------------------------------------------------------------------------------|--------|-------|
|<span data-ttu-id="0d71e-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="0d71e-113">DestinationPath</span></span>|<span data-ttu-id="0d71e-114">확인하려는 대상 노드의 위치는 `Present` 또는 `Absent`입니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-114">The location, on the target node, you want to ensure is `Present` or `Absent`.</span></span>|<span data-ttu-id="0d71e-115">예</span><span class="sxs-lookup"><span data-stu-id="0d71e-115">Yes</span></span>|<span data-ttu-id="0d71e-116">아니요</span><span class="sxs-lookup"><span data-stu-id="0d71e-116">No</span></span>|
|<span data-ttu-id="0d71e-117">특성</span><span class="sxs-lookup"><span data-stu-id="0d71e-117">Attributes</span></span>     |<span data-ttu-id="0d71e-118">대상으로 지정된 파일 또는 디렉터리에 대한 특성의 필요한 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-118">The desired state of the attributes for the targeted file or directory.</span></span> <span data-ttu-id="0d71e-119">유효한 값은 **Archive**, **Hidden**, **ReadOnly** 및 **System**입니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-119">Valid values are **Archive**, **Hidden**, **ReadOnly**, and **System**.</span></span>|<span data-ttu-id="0d71e-120">아니요</span><span class="sxs-lookup"><span data-stu-id="0d71e-120">No</span></span>|<span data-ttu-id="0d71e-121">없음</span><span class="sxs-lookup"><span data-stu-id="0d71e-121">None</span></span>|
|<span data-ttu-id="0d71e-122">체크섬</span><span class="sxs-lookup"><span data-stu-id="0d71e-122">Checksum</span></span>      |<span data-ttu-id="0d71e-123">두 파일이 동일한 것인지 결정할 때 사용할 체크섬 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-123">The checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="0d71e-124">유효한 값은 다음과 같습니다. SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span><span class="sxs-lookup"><span data-stu-id="0d71e-124">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|<span data-ttu-id="0d71e-125">아니요</span><span class="sxs-lookup"><span data-stu-id="0d71e-125">No</span></span>|<span data-ttu-id="0d71e-126">파일 또는 디렉터리 이름만 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-126">Only the file or directory name is compared.</span></span>|
|<span data-ttu-id="0d71e-127">콘텐츠</span><span class="sxs-lookup"><span data-stu-id="0d71e-127">Contents</span></span>       |<span data-ttu-id="0d71e-128">`File` 형식과 함께 사용할 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-128">Only valid when used with `File` type.</span></span> <span data-ttu-id="0d71e-129">Ensure에 대한 콘텐츠가 대상 파일에서 `Present` 또는 `Absent`임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-129">Indicates the contents to Ensure are `Present` or `Absent` from the targeted file.</span></span> |<span data-ttu-id="0d71e-130">아니요</span><span class="sxs-lookup"><span data-stu-id="0d71e-130">No</span></span>|<span data-ttu-id="0d71e-131">없음</span><span class="sxs-lookup"><span data-stu-id="0d71e-131">None</span></span>|
|<span data-ttu-id="0d71e-132">자격 증명</span><span class="sxs-lookup"><span data-stu-id="0d71e-132">Credential</span></span>     |<span data-ttu-id="0d71e-133">원본 파일과 같은 리소스에 액세스하는 데 필요한 자격 증명입니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-133">The credentials that are required to access resources, such as source files.</span></span>|<span data-ttu-id="0d71e-134">아니요</span><span class="sxs-lookup"><span data-stu-id="0d71e-134">No</span></span>|<span data-ttu-id="0d71e-135">대상 노드의 컴퓨터 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-135">The target node's Computer Account.</span></span> <span data-ttu-id="0d71e-136">(*참고 참조*)</span><span class="sxs-lookup"><span data-stu-id="0d71e-136">(*see note*)</span></span>|
|<span data-ttu-id="0d71e-137">Ensure</span><span class="sxs-lookup"><span data-stu-id="0d71e-137">Ensure</span></span>         |<span data-ttu-id="0d71e-138">대상 파일 또는 디렉터리의 필요한 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-138">The desired state of the target file or directory.</span></span> |<span data-ttu-id="0d71e-139">아니요</span><span class="sxs-lookup"><span data-stu-id="0d71e-139">No</span></span>|<span data-ttu-id="0d71e-140">**있음**</span><span class="sxs-lookup"><span data-stu-id="0d71e-140">**Present**</span></span>|
|<span data-ttu-id="0d71e-141">Force</span><span class="sxs-lookup"><span data-stu-id="0d71e-141">Force</span></span>          |<span data-ttu-id="0d71e-142">오류가 발생하는 액세스 작업(예: 파일 덮어쓰기나 비어 있지 않은 디렉터리 삭제)을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-142">Overrides access operations that would result in an error (such as overwriting a file or deleting a directory that is not empty).</span></span>|<span data-ttu-id="0d71e-143">아니요</span><span class="sxs-lookup"><span data-stu-id="0d71e-143">No</span></span>|`$false`|
|<span data-ttu-id="0d71e-144">Recurse</span><span class="sxs-lookup"><span data-stu-id="0d71e-144">Recurse</span></span>        |<span data-ttu-id="0d71e-145">`Directory` 형식과 함께 사용할 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-145">Only valid when used with `Directory` type.</span></span> <span data-ttu-id="0d71e-146">모든 하위 디렉터리에 대한 상태 작업을 재귀적으로 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-146">Performs the state operation recursively to all subdirectories.</span></span>|<span data-ttu-id="0d71e-147">아니요</span><span class="sxs-lookup"><span data-stu-id="0d71e-147">No</span></span>|`$false`|
|<span data-ttu-id="0d71e-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0d71e-148">DependsOn</span></span>      |<span data-ttu-id="0d71e-149">지정된 리소스에서 종속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-149">Sets a dependency on specified resource(s).</span></span> <span data-ttu-id="0d71e-150">이 리소스는 종속 리소스를 성공적으로 실행한 후에만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-150">This resource will only execute after successful execution of any dependent resources.</span></span> <span data-ttu-id="0d71e-151">구문 `"[ResourceType]ResourceName"`을 사용하여 종속 리소스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-151">You can specify dependent resources using the syntax `"[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="0d71e-152">[about_DependsOn](../../../configurations/resource-depends-on.md) 참조</span><span class="sxs-lookup"><span data-stu-id="0d71e-152">See [about_DependsOn](../../../configurations/resource-depends-on.md)</span></span>|<span data-ttu-id="0d71e-153">아니요</span><span class="sxs-lookup"><span data-stu-id="0d71e-153">No</span></span>|<span data-ttu-id="0d71e-154">없음</span><span class="sxs-lookup"><span data-stu-id="0d71e-154">None</span></span>|
|<span data-ttu-id="0d71e-155">SourcePath</span><span class="sxs-lookup"><span data-stu-id="0d71e-155">SourcePath</span></span>     |<span data-ttu-id="0d71e-156">파일 또는 폴더 리소스를 복사할 원본 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-156">The path from which to copy the file or folder resource.</span></span>|<span data-ttu-id="0d71e-157">아니요</span><span class="sxs-lookup"><span data-stu-id="0d71e-157">No</span></span>|<span data-ttu-id="0d71e-158">없음</span><span class="sxs-lookup"><span data-stu-id="0d71e-158">None</span></span>|
|<span data-ttu-id="0d71e-159">유형</span><span class="sxs-lookup"><span data-stu-id="0d71e-159">Type</span></span>           |<span data-ttu-id="0d71e-160">구성되는 리소스 종류입니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-160">The type of resource being configured.</span></span> <span data-ttu-id="0d71e-161">유효한 값은 `Directory` 및 `File`입니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-161">Valid values are `Directory` and `File`.</span></span>|<span data-ttu-id="0d71e-162">아니요</span><span class="sxs-lookup"><span data-stu-id="0d71e-162">No</span></span>|`File`|
|<span data-ttu-id="0d71e-163">MatchSource</span><span class="sxs-lookup"><span data-stu-id="0d71e-163">MatchSource</span></span>    |<span data-ttu-id="0d71e-164">리소스가 초기 복사 후에 소스 디렉터리에 추가된 새 파일을 모니터링해야 하는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-164">Determines if the resource should monitor for new files added to the source directory after the initial copy.</span></span> <span data-ttu-id="0d71e-165">`$true` 값은 초기 복사 후에 새 원본 파일을 대상으로 복사해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-165">A value of `$true` indicates that, after the initial copy, any new source files should be copied to the destination.</span></span> <span data-ttu-id="0d71e-166">`$False`로 설정하면 리소스가 소스 디렉터리의 콘텐츠를 캐시하고 초기 복사 후에 추가된 모든 파일을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-166">If set to `$False`, the resource caches the contents of the source directory and ignores any files added after the initial copy.</span></span>|<span data-ttu-id="0d71e-167">아니요</span><span class="sxs-lookup"><span data-stu-id="0d71e-167">No</span></span>|`$false`|

> [!WARNING]
> <span data-ttu-id="0d71e-168">`Credential` 또는 `PSRunAsCredential`(PS V.5)의 값을 지정하지 않으면 리소스는 대상 노드의 컴퓨터 계정을 사용하여 `SourcePath`에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-168">If you do not specify a value for `Credential` or `PSRunAsCredential` (PS V.5), the resource will use the computer account of the target node to access the `SourcePath`.</span></span>  <span data-ttu-id="0d71e-169">`SourcePath`가 UNC 공유이면 이 액세스로 인해 "액세스 거부" 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-169">When the `SourcePath` is a UNC share, this could result in an "Access Denied" error.</span></span> <span data-ttu-id="0d71e-170">이에 따라 권한이 설정되어 있는지 확인하거나, `Credential` 또는 `PSRunAsCredential` 속성을 사용하여 사용해야 하는 계정을 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="0d71e-170">Please ensure your permissions are set accordingly, or use the `Credential` or `PSRunAsCredential` properties to specify the account that should be used.</span></span>

## <a name="present-vs-absent"></a><span data-ttu-id="0d71e-171">Present 및 Absent</span><span class="sxs-lookup"><span data-stu-id="0d71e-171">Present vs. Absent</span></span>

<span data-ttu-id="0d71e-172">각 DSC 리소스는 `Ensure` 속성에 대해 지정하는 값에 따라 다른 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-172">Each DSC resource performs different operations based on the value you specify for the `Ensure` property.</span></span> <span data-ttu-id="0d71e-173">위의 속성에 대해 지정하는 값에 따라 수행되는 상태 작업이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-173">The values you specify for the above properties determines the state operation performed.</span></span>

### <a name="existence"></a><span data-ttu-id="0d71e-174">존재 여부</span><span class="sxs-lookup"><span data-stu-id="0d71e-174">Existence</span></span>

<span data-ttu-id="0d71e-175">`DestinationPath`만 지정하면 리소스는 경로가 있는지(`Present`) 또는 없는지(`Absent`) 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-175">When you only specify a `DestinationPath`, the resource ensures that the path exists (`Present`) or does not exist (`Absent`).</span></span>

### <a name="copy-operations"></a><span data-ttu-id="0d71e-176">복사 작업</span><span class="sxs-lookup"><span data-stu-id="0d71e-176">Copy Operations</span></span>

<span data-ttu-id="0d71e-177">**Directory**의 `Type` 값을 사용하여 `SourcePath` 및 `DestinationPath`를 지정하면 리소스는 소스 디렉터리를 대상 경로에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-177">When you specify a `SourcePath` and a `DestinationPath` with a `Type` value of **Directory**, the resource copies source directory to the destination path.</span></span> <span data-ttu-id="0d71e-178">`Recurse`, `Force` 및 `MatchSource` 속성은 수행되는 복사 작업 유형을 변경하지만, `Credential`은 소스 디렉터리에 액세스하는 데 사용할 계정을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-178">The properties `Recurse`, `Force`, and `MatchSource` change the type of copy operation performed, while `Credential` determines which account to use to access the source directory.</span></span>

### <a name="limitations"></a><span data-ttu-id="0d71e-179">제한 사항</span><span class="sxs-lookup"><span data-stu-id="0d71e-179">Limitations</span></span>

<span data-ttu-id="0d71e-180">`DestinationPath`와 함께 `Attributes` 속성에 `ReadOnly` 값을 지정한 경우 `Ensure = "Present"`는 지정된 경로를 만들지만, `Contents`는 파일의 콘텐츠를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-180">If you specified a value of `ReadOnly` for the `Attributes` property alongside a `DestinationPath`, `Ensure = "Present"` would create the path specified, while `Contents` would set the contents of the file.</span></span>  <span data-ttu-id="0d71e-181">`Absent` 상태 작업은 `Attributes` 속성을 완전히 무시하고 지정된 경로에 있는 모든 파일을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-181">An `Absent` state operation would ignore the `Attributes` property entirely, and remove any file at the specified path.</span></span>

## <a name="example"></a><span data-ttu-id="0d71e-182">예제</span><span class="sxs-lookup"><span data-stu-id="0d71e-182">Example</span></span>

<span data-ttu-id="0d71e-183">다음 예제에서는 파일 리소스를 사용하여 끌어오기 서버에서 대상 노드로 디렉터리 및 해당 하위 디렉터리를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-183">The following example copies a directory and its subdirectories from a pull server to a target node using the File Resource.</span></span> <span data-ttu-id="0d71e-184">작업이 성공하면 로그 리소스는 이벤트 로그에 확인 메시지를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-184">If the operation succeeds, the Log resource writes a confirmation message to the event log.</span></span>

<span data-ttu-id="0d71e-185">소스 디렉터리는 끌어오기 서버에서 공유되는 UNC 경로(`\\PullServer\DemoSource`)입니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-185">The source directory is a UNC path (`\\PullServer\DemoSource`) shared from the Pull Server.</span></span> <span data-ttu-id="0d71e-186">`Recurse` 속성을 사용하면 하위 디렉터리도 모두 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-186">The `Recurse` property ensures that all subdirectories are copied as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0d71e-187">대상 노드의 LCM은 기본적으로 로컬 시스템 계정의 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-187">The LCM on the target Node executes in the context of the local system account by default.</span></span> <span data-ttu-id="0d71e-188">**SourcePath**에 액세스 권한을 부여하려면 대상 노드의 컴퓨터 계정에 적절한 권한을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-188">To grant access to the **SourcePath**, give the target Node's computer account appropriate permissions.</span></span> <span data-ttu-id="0d71e-189">**Credential** 및 **PSDSCRunAsCredential**(v5)은 둘 다 LCM이 **SourcePath**에 액세스하는 데 사용하는 컨텍스트를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-189">The **Credential** and **PSDSCRunAsCredential** (v5) both change the context the LCM uses to access the **SourcePath**.</span></span> <span data-ttu-id="0d71e-190">**SourcePath**를 액세스하는 데 사용될 계정에도 액세스 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d71e-190">You still need to grant access to the account that will be used to access the **SourcePath**.</span></span>

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

<span data-ttu-id="0d71e-191">DSC에서 **자격 증명**을 사용하는 방법에 대한 자세한 내용은 [사용자로 실행](../../../configurations/runAsUser.md) 또는 [구성 데이터 자격 증명](../../../configurations/configDataCredentials.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0d71e-191">For more on using **Credentials** in DSC see [Run As User](../../../configurations/runAsUser.md) or [Config Data Credentials](../../../configurations/configDataCredentials.md).</span></span>
