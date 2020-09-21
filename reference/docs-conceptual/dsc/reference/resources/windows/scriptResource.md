---
ms.date: 07/16/2020
keywords: dsc,powershell,configuration,setup
title: DSC 스크립트 리소스
ms.openlocfilehash: 9b89981c17e87b3681c6416c7dee44a75c432ea1
ms.sourcegitcommit: eb6a7c01e6385809656ac828b9211683e0b1a6fe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2020
ms.locfileid: "89041132"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="7a9b1-103">DSC 스크립트 리소스</span><span class="sxs-lookup"><span data-stu-id="7a9b1-103">DSC Script Resource</span></span>

> <span data-ttu-id="7a9b1-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="7a9b1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="7a9b1-105">Windows PowerShell DSC(필요한 상태 구성)의 `Script` 리소스에서는 대상 노드에서 Windows PowerShell 스크립트 블록을 실행하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-105">The `Script` resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="7a9b1-106">`Script` 리소스는 사용자가 정의하는 스크립트 블록이 포함되는 `GetScript`
`SetScript` 및 `TestScript` 속성을 사용하여 해당 DSC 상태 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-106">The `Script` resource uses `GetScript`
`SetScript`, and `TestScript` properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="7a9b1-107">구문</span><span class="sxs-lookup"><span data-stu-id="7a9b1-107">Syntax</span></span>

```Syntax
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> <span data-ttu-id="7a9b1-108">`GetScript`, `TestScript` 및 `SetScript` 블록은 문자열로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-108">`GetScript` `TestScript`, and `SetScript` blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="7a9b1-109">속성</span><span class="sxs-lookup"><span data-stu-id="7a9b1-109">Properties</span></span>

|  <span data-ttu-id="7a9b1-110">속성</span><span class="sxs-lookup"><span data-stu-id="7a9b1-110">Property</span></span>  |                                          <span data-ttu-id="7a9b1-111">Description</span><span class="sxs-lookup"><span data-stu-id="7a9b1-111">Description</span></span>                                          |
| ---------- | --------------------------------------------------------------------------------------------- |
| <span data-ttu-id="7a9b1-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="7a9b1-112">GetScript</span></span>  | <span data-ttu-id="7a9b1-113">노드의 현재 상태를 반환하는 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-113">A script block that returns the current state of the Node.</span></span>                                    |
| <span data-ttu-id="7a9b1-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="7a9b1-114">SetScript</span></span>  | <span data-ttu-id="7a9b1-115">노드가 원하는 상태가 아닐 때 DSC가 준수 적용을 위해 사용하는 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span> |
| <span data-ttu-id="7a9b1-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="7a9b1-116">TestScript</span></span> | <span data-ttu-id="7a9b1-117">노드가 원하는 상태인지를 확인하는 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-117">A script block that determines if the Node is in the desired state.</span></span>                           |
| <span data-ttu-id="7a9b1-118">자격 증명</span><span class="sxs-lookup"><span data-stu-id="7a9b1-118">Credential</span></span> | <span data-ttu-id="7a9b1-119">자격 증명이 필요한 경우 이 스크립트를 실행하는 데 사용할 자격 증명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-119">Indicates the credentials to use for running this script, if credentials are required.</span></span>        |

## <a name="common-properties"></a><span data-ttu-id="7a9b1-120">공용 속성</span><span class="sxs-lookup"><span data-stu-id="7a9b1-120">Common properties</span></span>

|       <span data-ttu-id="7a9b1-121">속성</span><span class="sxs-lookup"><span data-stu-id="7a9b1-121">Property</span></span>       |                                            <span data-ttu-id="7a9b1-122">Description</span><span class="sxs-lookup"><span data-stu-id="7a9b1-122">Description</span></span>                                            |
| -------------------- | ------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="7a9b1-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7a9b1-123">DependsOn</span></span>            | <span data-ttu-id="7a9b1-124">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> |
| <span data-ttu-id="7a9b1-125">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7a9b1-125">PsDscRunAsCredential</span></span> | <span data-ttu-id="7a9b1-126">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-126">Sets the credential for running the entire resource as.</span></span>                                           |

> [!NOTE]
> <span data-ttu-id="7a9b1-127">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-127">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="7a9b1-128">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-128">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="7a9b1-129">추가 정보</span><span class="sxs-lookup"><span data-stu-id="7a9b1-129">Additional information</span></span>

#### <a name="getscript"></a><span data-ttu-id="7a9b1-130">GetScript</span><span class="sxs-lookup"><span data-stu-id="7a9b1-130">GetScript</span></span>

<span data-ttu-id="7a9b1-131">DSC는 `GetScript`의 출력을 사용하지 않습니다. [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet은 `GetScript`를 실행하여 노드의 현재 상태를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-131">DSC does not use the output from `GetScript` The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes `GetScript` to retrieve a node's current state.</span></span> <span data-ttu-id="7a9b1-132">`GetScript`의 반환 값이 필요하지 않습니다. 반환 값을 지정하는 경우 해당 값이 문자열인 **Result** 키가 포함된 해시 테이블이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-132">A return value is not required from `GetScript` If you specify a return value, it must be a hashtable containing a **Result** key whose value is a String.</span></span>

#### <a name="testscript"></a><span data-ttu-id="7a9b1-133">TestScript</span><span class="sxs-lookup"><span data-stu-id="7a9b1-133">TestScript</span></span>

<span data-ttu-id="7a9b1-134">`TestScript`는 `SetScript`를 실행해야 하는지 여부를 확인하기 위해 DSC에 의해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-134">`TestScript` is executed by DSC to determine if `SetScript` should be run.</span></span> <span data-ttu-id="7a9b1-135">`TestScript`가 `$false`를 반환하는 경우 DSC는 `SetScript`를 실행하여 노드를 원하는 상태로 다시 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-135">If `TestScript` returns `$false`, DSC executes `SetScript` to bring the node back to the desired state.</span></span> <span data-ttu-id="7a9b1-136">부울 값을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-136">It must return a boolean value.</span></span> <span data-ttu-id="7a9b1-137">`$true`의 결과는 노드가 규정을 준수하며 `SetScript`를 실행하지 않아야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-137">A result of `$true` indicates that the node is compliant and `SetScript` should not executed.</span></span>

<span data-ttu-id="7a9b1-138">[Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet은 `TestScript`를 실행하여 `Script` 리소스에 대한 노드 준수 상태를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-138">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes `TestScript` to retrieve the nodes compliance with the `Script` resources.</span></span> <span data-ttu-id="7a9b1-139">그러나 이 경우에는 `TestScript` 블록이 반환하는 결과에 관계없이 `SetScript`는 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-139">However, in this case, `SetScript` does not run, no matter what `TestScript` block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="7a9b1-140">`TestScript`의 모든 출력은 해당 반환 값의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-140">All output from your `TestScript` is part of its return value.</span></span> <span data-ttu-id="7a9b1-141">PowerShell은 표시되는 출력을 0이 아닌 것으로 해석합니다. 즉, `TestScript`는 노드 상태에 관계없이 `$true`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-141">PowerShell interprets unsuppressed output as non-zero, which means that your `TestScript` will return `$true` regardless of your node's state.</span></span> <span data-ttu-id="7a9b1-142">이로 인해 예상치 못한 결과, 가양성이 발생하고, 문제를 해결하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-142">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

#### <a name="setscript"></a><span data-ttu-id="7a9b1-143">SetScript</span><span class="sxs-lookup"><span data-stu-id="7a9b1-143">SetScript</span></span>

<span data-ttu-id="7a9b1-144">`SetScript`는 노드를 수정하여 원하는 상태를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-144">`SetScript` modifies the node to enforce the desired state.</span></span> <span data-ttu-id="7a9b1-145">이 속성은 `TestScript` 스크립트 블록이 `$false`를 반환하는 경우 DSC에 의해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-145">It is called by DSC if the `TestScript` script block returns `$false`.</span></span> <span data-ttu-id="7a9b1-146">`SetScript`에는 반환 값이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-146">The `SetScript` should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="7a9b1-147">예</span><span class="sxs-lookup"><span data-stu-id="7a9b1-147">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="7a9b1-148">예제 1: 스크립트 리소스를 사용하여 샘플 텍스트 쓰기</span><span class="sxs-lookup"><span data-stu-id="7a9b1-148">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="7a9b1-149">이 예제에서는 각 노드에서 `C:\TempFolder\TestFile.txt`의 존재 여부를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-149">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="7a9b1-150">존재하지 않는 경우 `SetScript`를 사용하여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-150">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="7a9b1-151">`GetScript`는 파일의 내용을 반환하고, 해당 반환 값은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-151">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="7a9b1-152">예제 2: 스크립트 리소스를 사용하여 버전 정보 비교</span><span class="sxs-lookup"><span data-stu-id="7a9b1-152">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="7a9b1-153">이 예제에서는 작성 컴퓨터의 텍스트 파일에서 _규격_ 버전 정보를 검색한 후 `$version` 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-153">This example retrieves the _compliant_ version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="7a9b1-154">노드의 MOF 파일을 생성할 때 DSC는 각 스크립트 블록의 `$using:version` 변수를 `$version` 변수의 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-154">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>
<span data-ttu-id="7a9b1-155">실행 동안 _규격_ 버전은 각 노드의 텍스트 파일에 저장되고, 후속 실행에서 비교 및 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-155">During execution, the _compliant_ version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state.Result -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state.Result,$using:version)
                    return $true
                }
                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            }
        }
    }
}
```

### <a name="example-3-utilizing-parameters-in-a-script-resource"></a><span data-ttu-id="7a9b1-156">예 3: 스크립트 리소스에서 매개 변수 활용</span><span class="sxs-lookup"><span data-stu-id="7a9b1-156">Example 3: Utilizing parameters in a Script resource</span></span>

<span data-ttu-id="7a9b1-157">이 예제에서는 `using` 범위를 사용하여 스크립트 리소스 내에서 매개 변수에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-157">This example accesses parameters from within the Script resource by making use of the `using` scope.</span></span>
<span data-ttu-id="7a9b1-158">**ConfigurationData**는 비슷한 방법으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-158">Please note that **ConfigurationData** can be accessed in a similar way.</span></span> <span data-ttu-id="7a9b1-159">예제 2와 같이 버전은 대상 노드의 로컬 파일 내에 저장되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-159">Like example 2, a version is expected to be stored inside a local file on the target node.</span></span> <span data-ttu-id="7a9b1-160">그러나 로컬 파일 경로와 버전은 모두 구성 가능하며 구성 데이터에서 코드를 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-160">Both the local file path as well as the version are configurable however, decoupling code from configuration data.</span></span>

```powershell
Configuration ScriptTest
{
    param
    (
        [Version]
        $Version,

        [string]
        $FilePath
    )

    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content -Path $using:FilePath
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:Version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }

                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                Set-Content -Path $using:FilePath -Value $using:Version
            }
        }
    }
}
```

<span data-ttu-id="7a9b1-161">결과인 MOF 파일에는 `using` 범위를 통해 액세스 되는 변수와 해당 값이 포함되며</span><span class="sxs-lookup"><span data-stu-id="7a9b1-161">The resulting MOF file includes the variables and their values accessed through the `using` scope.</span></span>
<span data-ttu-id="7a9b1-162">변수를 사용하는 각 scriptblock에 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-162">They are injected into each scriptblock which uses the variables.</span></span> <span data-ttu-id="7a9b1-163">간결성을 위해 테스트 및 설정 스크립트가 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-163">Test and Set scripts have been removed for brevity:</span></span>

```Output
instance of MSFT_ScriptResource as $MSFT_ScriptResource1ref
{
 GetScript = "$FilePath ='C:\\Config.ini'\n\n $currentVersion = Get-Content -Path $FilePath\n return @{ 'Result' = \"$currentVersion\" }\n";
 TestScript = ...;
 SetScript = ...;
};
```

### <a name="known-limitations"></a><span data-ttu-id="7a9b1-164">알려진 제한 사항</span><span class="sxs-lookup"><span data-stu-id="7a9b1-164">Known Limitations</span></span>

- <span data-ttu-id="7a9b1-165">끌어오기 또는 푸시 서버 모델을 사용하는 경우 스크립트 리소스 내에서 전달되는 자격 증명은 항상 신뢰할 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-165">Credentials being passed within a script resource are not always reliable when using a pull or push server model.</span></span> <span data-ttu-id="7a9b1-166">이 경우 스크립트 리소스를 사용하는 것보다는 전체 리소스를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b1-166">It is recommended to use a full resource rather than use a script resource in this case.</span></span>
