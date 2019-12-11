---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 리소스 작성 검사 목록
ms.openlocfilehash: c0a18169b5e9f6ba0c3848b00725731453763611
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952880"
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="17128-103">리소스 작성 검사 목록</span><span class="sxs-lookup"><span data-stu-id="17128-103">Resource authoring checklist</span></span>

<span data-ttu-id="17128-104">이 검사 목록은 새 DSC 리소스를 작성할 때 따를 모범 사례 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="17128-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="17128-105">리소스 모듈에 모든 리소스에 대한 .psd1 파일과 schema.mof가 포함되어 있음</span><span class="sxs-lookup"><span data-stu-id="17128-105">Resource module contains .psd1 file and schema.mof for every resource</span></span>

<span data-ttu-id="17128-106">리소스가 올바른 구조이고 필요한 파일을 모두 포함하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="17128-107">모든 리소스 모듈에 .psd1 파일이 포함되어 있고 모든 비복합 리소스에 schema.mof 파일이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span> <span data-ttu-id="17128-108">스키마가 포함되지 않은 리소스는 `Get-DscResource`로 나열되지 않고 사용자는 ISE에서 해당 모듈에 대해 코드를 작성할 때 intellisense를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-108">Resources that do not contain schema will not be listed by `Get-DscResource` and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span>
<span data-ttu-id="17128-109">[xPSDesiredStateConfiguration 리소스 모듈](https://github.com/PowerShell/xPSDesiredStateConfiguration)의 일부인 xRemoteFile 리소스에 대한 디렉터리 구조는 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="17128-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>

```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="17128-110">리소스 및 스키마가 올바름</span><span class="sxs-lookup"><span data-stu-id="17128-110">Resource and schema are correct</span></span>

<span data-ttu-id="17128-111">리소스 스키마(\*.schema.mof) 파일을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-111">Verify the resource schema (\*.schema.mof) file.</span></span> <span data-ttu-id="17128-112">[DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0)(DSC 리소스 디자이너)를 사용하여 스키마를 개발하고 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to help develop and test your schema.</span></span>
<span data-ttu-id="17128-113">다음 사항을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="17128-113">Make sure that:</span></span>

- <span data-ttu-id="17128-114">속성 형식이 올바릅니다. 예를 들어 숫자 값을 허용하는 속성에 문자열을 사용하지 마세요. 대신 UInt32나 다른 숫자 형식을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-114">Property types are correct (e.g. don't use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="17128-115">속성 특성이 다음과 같이 올바르게 지정되었습니다([key], [required], [write], [read]).</span><span class="sxs-lookup"><span data-stu-id="17128-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="17128-116">스키마에서 하나 이상의 매개 변수가 [key]로 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="17128-117">[read] 속성은 [required], [key], [write] 중 하나와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="17128-118">[read]를 제외한 여러 한정자가 지정된 경우 [key]가 우선적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="17128-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="17128-119">[write] 및 [required]가 지정된 경우 [required]가 우선적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="17128-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="17128-120">ValueMap이 적절하게 지정되었습니다. 예:</span><span class="sxs-lookup"><span data-stu-id="17128-120">ValueMap is specified where appropriate Example:</span></span>

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- <span data-ttu-id="17128-121">식별 이름이 지정되고 DSC 명명 규칙을 준수합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-121">Friendly name is specified and confirms to DSC naming conventions</span></span>

  <span data-ttu-id="17128-122">예: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span><span class="sxs-lookup"><span data-stu-id="17128-122">Example: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span></span>

- <span data-ttu-id="17128-123">모든 필드에 의미 있는 설명이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-123">Every field has meaningful description.</span></span> <span data-ttu-id="17128-124">PowerShell GitHub 리포지토리에는 [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)(xRemoteFile용 .schema.mof)과 같은 좋은 예가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-124">The PowerShell GitHub repository has good examples, such as [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="17128-125">또한 [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0)(DSC 리소스 디자이너)의 **Test-xDscResource** 및 **Test-xDscSchema** cmdlet을 사용하여 리소스 및 스키마를 자동으로 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-125">Additionally, you should use **Test-xDscResource** and **Test-xDscSchema** cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to automatically verify the resource and schema:</span></span>

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

<span data-ttu-id="17128-126">예:</span><span class="sxs-lookup"><span data-stu-id="17128-126">For example:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="17128-127">리소스가 오류 없이 로드됨</span><span class="sxs-lookup"><span data-stu-id="17128-127">Resource loads without errors</span></span>

<span data-ttu-id="17128-128">리소스 모듈을 로드할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-128">Check whether the resource module can be successfully loaded.</span></span>
<span data-ttu-id="17128-129">이 작업은 `Import-Module <resource_module> -force`을 실행하고 오류가 발생하지 않는지 확인하거나, 테스트 자동화를 작성하여 수동으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-129">This can be achieved manually, by running `Import-Module <resource_module> -force` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="17128-130">후자의 경우 테스트 사례에서 다음 구조를 따를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-130">In case of the latter, you can follow this structure in your test case:</span></span>

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw "Module was not imported correctly. Errors returned: $error"
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="17128-131">리소스가 양성 사례에서 idempotent임</span><span class="sxs-lookup"><span data-stu-id="17128-131">Resource is idempotent in the positive case</span></span>

<span data-ttu-id="17128-132">DSC 리소스의 기본 특성 중 하나는 멱등성(idempotence)입니다.</span><span class="sxs-lookup"><span data-stu-id="17128-132">One of the fundamental characteristics of DSC resources is idempotence.</span></span> <span data-ttu-id="17128-133">즉, 해당 리소스를 포함하는 DSC 구성을 여러 번 적용하면 항상 같은 결과가 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="17128-133">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="17128-134">예를 들면 다음과 같은 파일 리소스를 포함하는 구성을 만드는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="17128-134">For example, if we create a configuration which contains the following File resource:</span></span>

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

<span data-ttu-id="17128-135">처음으로 적용한 후 test.txt 파일이 `C:\test` 폴더에 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-135">After applying it for the first time, file test.txt should appear in `C:\test` folder.</span></span> <span data-ttu-id="17128-136">그러나 동일한 구성의 후속 실행에서도 컴퓨터의 상태는 변경되지 않아야 합니다. 예를 들어 `test.txt` 파일의 복사본이 만들어지지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-136">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the `test.txt` file should be created).</span></span>
<span data-ttu-id="17128-137">리소스가 idempotent인지 확인하려면 리소스를 직접 테스트할 때 `Set-TargetResource`를 반복적으로 호출하거나 종단 간 테스트를 수행할 때 `Start-DscConfiguration`을 여러 번 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-137">To ensure a resource is idempotent you can repeatedly call `Set-TargetResource` when testing the resource directly, or call `Start-DscConfiguration` multiple times when doing end to end testing.</span></span> <span data-ttu-id="17128-138">결과는 모든 실행 후에 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-138">The result should be the same after every run.</span></span>

## <a name="test-user-modification-scenario"></a><span data-ttu-id="17128-139">테스트 사용자 수정 시나리오</span><span class="sxs-lookup"><span data-stu-id="17128-139">Test user modification scenario</span></span>

<span data-ttu-id="17128-140">컴퓨터의 상태를 변경한 다음 DSC를 다시 실행하면 `Set-TargetResource` 및 `Test-TargetResource`가 올바르게 작동하는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-140">By changing the state of the machine and then rerunning DSC, you can verify that `Set-TargetResource` and `Test-TargetResource` function properly.</span></span> <span data-ttu-id="17128-141">수행해야 하는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-141">Here are steps you should take:</span></span>

1. <span data-ttu-id="17128-142">원하는 상태가 아닌 리소스에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-142">Start with the resource not in the desired state.</span></span>
2. <span data-ttu-id="17128-143">리소스에서 구성을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-143">Run configuration with your resource</span></span>
3. <span data-ttu-id="17128-144">`Test-DscConfiguration`이 True를 반환하는지 확인</span><span class="sxs-lookup"><span data-stu-id="17128-144">Verify `Test-DscConfiguration` returns True</span></span>
4. <span data-ttu-id="17128-145">구성된 항목이 원하는 상태에서 해제되도록 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-145">Modify the configured item to be out of the desired state</span></span>
5. <span data-ttu-id="17128-146">`Test-DscConfiguration`이 false를 반환하는지 확인</span><span class="sxs-lookup"><span data-stu-id="17128-146">Verify `Test-DscConfiguration` returns false</span></span>

<span data-ttu-id="17128-147">다음은 레지스트리 키 리소스를 사용하는 보다 구체적인 예입니다.</span><span class="sxs-lookup"><span data-stu-id="17128-147">Here's a more concrete example using Registry resource:</span></span>

1. <span data-ttu-id="17128-148">원하는 상태가 아닌 레지스트리 키에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-148">Start with registry key not in the desired state</span></span>
2. <span data-ttu-id="17128-149">구성에서 `Start-DscConfiguration`을 실행하여 원하는 상태로 전환하고 통과하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-149">Run `Start-DscConfiguration` with a configuration to put it in the desired state and verify it passes.</span></span>
3. <span data-ttu-id="17128-150">`Test-DscConfiguration`을 실행하고 true를 반환하는지 확인</span><span class="sxs-lookup"><span data-stu-id="17128-150">Run `Test-DscConfiguration` and verify it returns true</span></span>
4. <span data-ttu-id="17128-151">키의 값을 수정하여 원하는 상태가 되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-151">Modify the value of the key so that it is not in the desired state</span></span>
5. <span data-ttu-id="17128-152">`Test-DscConfiguration`을 실행하고 false를 반환하는지 확인</span><span class="sxs-lookup"><span data-stu-id="17128-152">Run `Test-DscConfiguration` and verify it returns false</span></span>
6. <span data-ttu-id="17128-153">`Get-TargetResource` 기능을 `Get-DscConfiguration`을 사용하여 확인했습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-153">`Get-TargetResource` functionality was verified using `Get-DscConfiguration`</span></span>

<span data-ttu-id="17128-154">`Get-TargetResource`는 리소스의 현재 상태에 대한 세부 정보를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-154">`Get-TargetResource` should return details of the current state of the resource.</span></span> <span data-ttu-id="17128-155">구성을 적용한 후 `Get-DscConfiguration`을 호출하고 출력에 컴퓨터의 현재 상태가 올바르게 반영되는지 확인하여 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-155">Make sure to test it by calling `Get-DscConfiguration` after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="17128-156">`Start-DscConfiguration`을 호출할 때 이 영역의 문제가 나타나지 않으므로 별도로 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-156">It's important to test it separately, since any issues in this area won't appear when calling `Start-DscConfiguration`.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="17128-157">**Get/Set/Test-TargetResource** 함수 직접 호출</span><span class="sxs-lookup"><span data-stu-id="17128-157">Call **Get/Set/Test-TargetResource** functions directly</span></span>

<span data-ttu-id="17128-158">리소스에 구현된 **Get/Set/Test-TargetResource** 함수를 직접 호출하고 예상대로 작동하는지 확인하여 이 함수를 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-158">Make sure you test the **Get/Set/Test-TargetResource** functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="17128-159">**Start-DscConfiguration**을 사용하여 종단 간 확인</span><span class="sxs-lookup"><span data-stu-id="17128-159">Verify End to End using **Start-DscConfiguration**</span></span>

<span data-ttu-id="17128-160">**Get/Set/Test-TargetResource** 함수를 직접 호출하여 테스트하는 것이 중요하지만 이런 방식으로 모든 문제가 검색되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="17128-160">Testing **Get/Set/Test-TargetResource** functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="17128-161">`Start-DscConfiguration` 또는 끌어오기 서버 사용에 테스트의 초점을 맞추어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-161">You should focus significant part of your testing on using `Start-DscConfiguration` or the pull server.</span></span> <span data-ttu-id="17128-162">실제로 사용자가 리소스를 사용하는 방법이므로 이러한 테스트 유형의 중요성을 간과해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17128-162">In fact, this is how users will use the resource, so don't underestimate the significance of this type of tests.</span></span>
<span data-ttu-id="17128-163">가능한 문제 유형:</span><span class="sxs-lookup"><span data-stu-id="17128-163">Possible types of issues:</span></span>

- <span data-ttu-id="17128-164">DSC 에이전트가 서비스로 실행되기 때문에 자격 증명/세션이 다르게 동작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span>  <span data-ttu-id="17128-165">여기에서 모든 기능을 종단 간 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="17128-166">`Start-DscConfiguration`에 의해 출력된 오류가 `Set-TargetResource` 함수를 직접 호출할 때 표시되는 오류와 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-166">Errors output by `Start-DscConfiguration` may be different than those displayed when calling the `Set-TargetResource` function directly.</span></span>

## <a name="test-compatability-on-all-dsc-supported-platforms"></a><span data-ttu-id="17128-167">모든 DSC 지원 플랫폼에서 호환성 테스트</span><span class="sxs-lookup"><span data-stu-id="17128-167">Test compatability on all DSC supported platforms</span></span>

<span data-ttu-id="17128-168">리소스는 모든 DSC 지원 플랫폼(Windows Server 2008 R2 이상)에서 작동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="17128-169">최신 버전의 DSC를 가져오려면 OS에 최신 WMF(Windows Management Framework)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="17128-170">리소스가 디자인에 따라 이러한 플랫폼 일부에서 작동하지 않을 경우 특정 오류 메시지가 반환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="17128-171">또한 호출하는 cmdlet이 특정 컴퓨터에 있는지 여부를 리소스에서 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="17128-172">Windows Server 2012에서는 Windows Server 2008 R2에서 WMF가 설치된 경우에도 제공하지 않는 많은 새로운 cmdlet이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="17128-173">Windows 클라이언트에서 확인(해당되는 경우)</span><span class="sxs-lookup"><span data-stu-id="17128-173">Verify on Windows Client (if applicable)</span></span>

<span data-ttu-id="17128-174">매우 일반적인 테스트 간격은 Windows의 서버 버전에서만 리소스를 확인하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="17128-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="17128-175">또한 많은 리소스가 클라이언트 SKU에서 작동하도록 설계되었으므로 해당되는 경우 해당 플랫폼에서도 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-175">Many resources are also designed to work on Client SKUs, so if that's true in your case, don't forget to test it on those platforms as well.</span></span>

## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="17128-176">Get-DSCResource에서 리소스를 나열함</span><span class="sxs-lookup"><span data-stu-id="17128-176">Get-DSCResource lists the resource</span></span>

<span data-ttu-id="17128-177">모듈을 배포한 후 `Get-DscResource`를 호출하면 결과로 리소스를 나열해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-177">After deploying the module, calling `Get-DscResource` should list your resource among others as a result.</span></span> <span data-ttu-id="17128-178">목록에서 리소스를 찾을 수 없으면 해당 리소스에 대한 schema.mof 파일이 있는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="17128-178">If you can't find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>

## <a name="resource-module-contains-examples"></a><span data-ttu-id="17128-179">리소스 모듈에 예제가 포함되어 있음</span><span class="sxs-lookup"><span data-stu-id="17128-179">Resource module contains examples</span></span>

<span data-ttu-id="17128-180">다른 사용자가 사용 방법을 이해하는 데 도움이 되는 우수한 예제 만들기.</span><span class="sxs-lookup"><span data-stu-id="17128-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="17128-181">따라서 이 작업은 중요하며 특히 많은 사용자가 샘플 코드를 설명서로 처리하기 때문에 더욱 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-181">This is crucial, especially since many users treat sample code as documentation.</span></span>

- <span data-ttu-id="17128-182">먼저 모듈에 포함될 예제를 결정해야 합니다. 최소한 리소스에 대한 가장 중요한 사용 사례를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="17128-183">엔드투엔드 시나리오에서 함께 작동해야 하는 여러 가지 리소스가 모듈에 포함된 경우 기본적인 엔드투엔드 예제가 첫 번째로 포함되는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="17128-184">초기 예제는 매우 간단해야 합니다. 즉, 관리할 수 있는 작은 청크(예: 새 VHD 만들기)로 리소스를 시작하는 방법이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="17128-185">이후 예제는 이 예제를 기반으로 해야 하며(예: VHD에서 VM 만들기, VM 제거, VM 수정) 고급 기능(예: 동적 메모리로 VM 만들기)을 보여 주어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="17128-186">예제 구성을 매개 변수화해야 합니다. 즉, 모든 값을 매개 변수로 구성에 전달해야 하며 하드 코드된 값이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>

  ```powershell
  configuration Sample_xRemoteFile_DownloadFile
  {
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
  }
  ```

- <span data-ttu-id="17128-187">예제 스크립트의 끝에 실제 값으로 구성을 호출하는 방법에 대한 예제를 포함(주석으로 처리)하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-187">It's a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span>
  <span data-ttu-id="17128-188">예를 들어 위의 구성에서는 UserAgent를 지정하는 가장 좋은 방법이 다음과 같은지 확실하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-188">For example, in the configuration above it isn't necessarily obvious that the best way to specify UserAgent is:</span></span>

  <span data-ttu-id="17128-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` 이 경우 주석을 사용하여 구성의 올바른 실행을 명확히 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- <span data-ttu-id="17128-190">각 예제에 대해 용도, 매개 변수의 의미를 설명하는 간단한 설명을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="17128-191">리소스에 가장 중요한 시나리오가 예제에 포함되었는지 확인하고 누락된 내용이 없을 경우 모두 실행되고 머신이 원하는 상태로 전환되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-191">Make sure examples cover most the important scenarios for your resource and if there's nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="17128-192">오류 메시지가 이해하기 쉽고 사용자가 문제를 해결하는 데 도움이 됨</span><span class="sxs-lookup"><span data-stu-id="17128-192">Error messages are easy to understand and help users solve problems</span></span>

<span data-ttu-id="17128-193">좋은 오류 메시지는 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-193">Good error messages should be:</span></span>

- <span data-ttu-id="17128-194">존재: 오류 메시지의 가장 큰 문제는 종종 존재하지 않는다는 점이므로 실제로 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-194">There: The biggest problem with error messages is that they often don't exist, so make sure they are there.</span></span>
- <span data-ttu-id="17128-195">이해하기 쉬움: 사용자가 읽을 수 있고 명확하지 않은 오류 코드가 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="17128-196">정확함: 문제를 정확하게 설명해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-196">Precise: Describe what's exactly the problem</span></span>
- <span data-ttu-id="17128-197">건설적임: 문제를 해결하는 방법을 조언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="17128-198">정중함: 사용자를 비난하거나 기분 나쁘게 하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-198">Polite: Don't blame user or make them feel bad</span></span>

<span data-ttu-id="17128-199">리소스 함수를 직접 실행할 때 반환되는 오류와 다를 수 있으므로 종단 간 시나리오에서 `Start-DscConfiguration`을 사용하여 오류를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-199">Make sure you verify errors in End to End scenarios (using `Start-DscConfiguration`), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="17128-200">로그 메시지는 이해하기 쉽고 정보를 제공해야 함(–verbose, –debug 및 ETW 로그 포함)</span><span class="sxs-lookup"><span data-stu-id="17128-200">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span>

<span data-ttu-id="17128-201">리소스에 의해 출력된 로그가 이해하기 쉽고 사용자에게 값을 제공하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-201">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span> <span data-ttu-id="17128-202">리소스는 사용자에게 도움이 될 수 있는 모든 정보를 출력해야 하지만 로그가 많을수록 항상 더 좋은 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="17128-202">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="17128-203">추가 값을 제공하지 않는 데이터의 출력 및 중복성을 방지해야 합니다. 즉, 원하는 항목을 찾기 위해 수백 개의 로그 항목을 검토하는 일이 없도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-203">You should avoid redundancy and outputting data which does not provide additional value – don't make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="17128-204">물론 로그가 없는 것도 이 문제에 적합한 솔루션은 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-204">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="17128-205">테스트할 때 ETW 로그뿐만 아니라 자세한 정보 로그 및 디버그 로그(`–Verbose` 및 `–Debug` 스위치를 적절히 사용하여 `Start-DscConfiguration` 실행)도 분석해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-205">When testing, you should also analyze verbose and debug logs (by running `Start-DscConfiguration` with `–Verbose` and `–Debug` switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="17128-206">DSC ETW 로그를 보려면 이벤트 뷰어로 이동하고 애플리케이션 및 서비스 - Microsoft - Windows - Desired State Configuration 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="17128-206">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span>  <span data-ttu-id="17128-207">기본적으로 작동 채널이 있지만 구성을 실행하기 전에 분석 및 디버그 채널을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-207">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span>
<span data-ttu-id="17128-208">분석/디버그 채널을 사용하려면 다음 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-208">To enable Analytic/Debug channels, you can execute script below:</span></span>

```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="17128-209">리소스 구현에 하드 코드된 경로가 포함되지 않음</span><span class="sxs-lookup"><span data-stu-id="17128-209">Resource implementation does not contain hardcoded paths</span></span>

<span data-ttu-id="17128-210">리소스 구현에 하드 코드된 경로가 없는지 확인합니다. 특히 언어(en-us)를 가정하거나 사용할 수 있는 시스템 변수가 있는 경우는 더욱 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-210">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span>
<span data-ttu-id="17128-211">리소스에서 특정 경로에 액세스해야 하는 경우 다른 컴퓨터에서는 달라질 수 있으므로 경로를 하드코딩하는 대신 환경 변수를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="17128-211">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="17128-212">예:</span><span class="sxs-lookup"><span data-stu-id="17128-212">Example:</span></span>

<span data-ttu-id="17128-213">다음 문자열 대신에</span><span class="sxs-lookup"><span data-stu-id="17128-213">Instead of:</span></span>

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

<span data-ttu-id="17128-214">다음과 같이 작성:</span><span class="sxs-lookup"><span data-stu-id="17128-214">You can write:</span></span>

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="17128-215">리소스 구현에 사용자 정보가 포함되지 않음</span><span class="sxs-lookup"><span data-stu-id="17128-215">Resource implementation does not contain user information</span></span>

<span data-ttu-id="17128-216">코드에 메일 이름, 계정 정보 또는 사람 이름이 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-216">Make sure there are no email names, account information, or names of people in the code.</span></span>

## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="17128-217">리소스가 유효한/잘못된 자격 증명으로 테스트됨</span><span class="sxs-lookup"><span data-stu-id="17128-217">Resource was tested with valid/invalid credentials</span></span>

<span data-ttu-id="17128-218">리소스에서 자격 증명을 매개 변수로 사용하는 경우:</span><span class="sxs-lookup"><span data-stu-id="17128-218">If your resource takes a credential as parameter:</span></span>

- <span data-ttu-id="17128-219">로컬 시스템(또는 원격 리소스에 대한 컴퓨터 계정)에 액세스 권한이 없는 경우에 리소스가 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-219">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="17128-220">Get, Set 및 Test에 지정된 자격 증명에서 리소스가 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-220">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="17128-221">리소스에서 공유에 액세스하는 경우 지원해야 하는 다음과 같은 모든 변형을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-221">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="17128-222">표준 Windows 공유</span><span class="sxs-lookup"><span data-stu-id="17128-222">Standard windows shares.</span></span>
  - <span data-ttu-id="17128-223">DFS 공유</span><span class="sxs-lookup"><span data-stu-id="17128-223">DFS shares.</span></span>
  - <span data-ttu-id="17128-224">SAMBA 공유(Linux를 지원하려는 경우)</span><span class="sxs-lookup"><span data-stu-id="17128-224">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="17128-225">리소스에 대화형 입력이 필요하지 않음</span><span class="sxs-lookup"><span data-stu-id="17128-225">Resource does not require interactive input</span></span>

<span data-ttu-id="17128-226">**Get/Set/Test-TargetResource** 함수는 자동으로 실행되어야 하며 모든 실행 단계에서 사용자의 입력을 대기하지 않아야 합니다. 예를 들어 이러한 함수 내부에서 `Get-Credential`을 사용해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17128-226">**Get/Set/Test-TargetResource** functions should be executed automatically and must not wait for user's input at any stage of execution (e.g. you should not use `Get-Credential` inside these functions).</span></span> <span data-ttu-id="17128-227">사용자의 입력을 제공해야 하는 경우 컴파일 단계 중 매개 변수로 구성에 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-227">If you need to provide user's input, you should pass it to the configuration as parameter during the compilation phase.</span></span>

## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="17128-228">리소스 기능이 철저하게 테스트됨</span><span class="sxs-lookup"><span data-stu-id="17128-228">Resource functionality was thoroughly tested</span></span>

<span data-ttu-id="17128-229">이 검사 목록에는 테스트해야 하거나 누락되는 경우가 많은 항목이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-229">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="17128-230">다양한 테스트가 있을 수 있으며, 주로 테스트하고 있지만 여기에 언급되지 않은 리소스와 관련된 기능 테스트입니다.</span><span class="sxs-lookup"><span data-stu-id="17128-230">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="17128-231">부정적인 테스트 사례를 기억해 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-231">Don't forget about negative test cases.</span></span>

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="17128-232">모범 사례: 리소스 모듈에 ResourceDesignerTests.ps1 스크립트가 포함된 Tests 폴더가 있음</span><span class="sxs-lookup"><span data-stu-id="17128-232">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span>

<span data-ttu-id="17128-233">리소스 모듈 내에 “Tests” 폴더를 만들고 `ResourceDesignerTests.ps1` 파일을 만든 다음 지정된 모듈의 모든 리소스에 대해 **Test-xDscResource** 및 **Test-xDscSchema**를 사용하여 테스트를 추가하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-233">It's a good practice to create folder "Tests" inside resource module, create `ResourceDesignerTests.ps1` file and add tests using **Test-xDscResource** and **Test-xDscSchema** for all resources in given module.</span></span>
<span data-ttu-id="17128-234">이런 방식으로 지정된 모듈에서 모든 리소스의 스키마에 대해 신속하게 유효성을 검사하고 게시하기 전에 온전성 검사를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-234">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span>
<span data-ttu-id="17128-235">xRemoteFile의 경우 `ResourceTests.ps1`이 다음과 같이 간단하게 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-235">For xRemoteFile, `ResourceTests.ps1` could look as simple as:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a><span data-ttu-id="17128-236">모범 사례: 리소스 폴더에 스키마를 생성하는 리소스 디자이너 스크립트가 있음</span><span class="sxs-lookup"><span data-stu-id="17128-236">Best practice: Resource folder contains resource designer script for generating schema</span></span>

<span data-ttu-id="17128-237">각 리소스에는 리소스의 mof 스키마를 생성하는 리소스 디자이너 스크립트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-237">Each resource should contain a resource designer script which generates a mof schema of the resource.</span></span> <span data-ttu-id="17128-238">이 파일은 `<ResourceName>\ResourceDesignerScripts`에 저장되며 이름은 Generate `<ResourceName>Schema.ps1`로 지정됩니다. xRemoteFile 리소스의 경우 이 파일을 `GenerateXRemoteFileSchema.ps1`이라고 하며 다음을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-238">This file should be placed in `<ResourceName>\ResourceDesignerScripts` and be named Generate `<ResourceName>Schema.ps1` For xRemoteFile resource this file would be called `GenerateXRemoteFileSchema.ps1` and contain:</span></span>

```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```

## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="17128-239">모범 사례: 리소스에서 -WhatIf를 지원함</span><span class="sxs-lookup"><span data-stu-id="17128-239">Best practice: Resource supports -WhatIf</span></span>

<span data-ttu-id="17128-240">리소스에서 “위험한” 작업을 수행하고 있는 경우 `-WhatIf` 기능을 구현하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-240">If your resource is performing "dangerous" operations, it's a good practice to implement `-WhatIf` functionality.</span></span> <span data-ttu-id="17128-241">완료된 후에는 명령이 `-WhatIf` 스위치 없이 실행된 경우 수행된 작업에 대해 `-WhatIf` 출력이 올바르게 설명하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-241">After it's done, make sure that `-WhatIf` output correctly describes operations which would happen if command was executed without `-WhatIf` switch.</span></span>
<span data-ttu-id="17128-242">또한 `–WhatIf` 스위치가 있으면 작업이 실행되지 않고 노드의 상태가 변경되지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17128-242">Also, verify that operations does not execute (no changes to the node's state are made) when `–WhatIf` switch is present.</span></span>
<span data-ttu-id="17128-243">예를 들어 파일 리소스를 테스트한다고 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-243">For example, let's assume we are testing File resource.</span></span> <span data-ttu-id="17128-244">다음은 "test" 콘텐츠로 `test.txt` 파일을 만드는 간단한 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="17128-244">Below is simple configuration which creates file `test.txt` with contents "test":</span></span>

```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```

<span data-ttu-id="17128-245">`-WhatIf` 스위치를 사용하여 구성을 컴파일한 다음 실행하면 출력에서 구성을 실행할 때 수행된 작업을 정확하게 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="17128-245">If we compile and then execute the configuration with the `-WhatIf` switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="17128-246">그러나 구성 자체는 실행되지 않았습니다. `test.txt` 파일이 생성되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-246">The configuration itself however was not executed (`test.txt` file was not created).</span></span>

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="17128-247">이 목록은 완벽하지는 않지만 DSC 리소스를 디자인, 개발 및 테스트하는 동안 발생할 수 있는 여러 가지 중요한 문제를 다루고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17128-247">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>
