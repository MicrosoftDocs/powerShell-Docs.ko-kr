---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 노드에서 구성 적용, 가져오기 및 테스트
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953840"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="dc8b9-103">노드에서 구성 적용, 가져오기 및 테스트</span><span class="sxs-lookup"><span data-stu-id="dc8b9-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="dc8b9-104">이 가이드에서는 대상 노드에서 구성을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="dc8b9-105">이 가이드는 다음 단계로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="dc8b9-106">구성 적용</span><span class="sxs-lookup"><span data-stu-id="dc8b9-106">Apply a Configuration</span></span>

<span data-ttu-id="dc8b9-107">구성을 적용 및 관리하려면 “.mof” 파일을 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="dc8b9-108">다음 코드는 이 가이드 전체에서 사용되는 간단한 구성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

<span data-ttu-id="dc8b9-109">이 구성을 컴파일하면 두 개의 ".mof" 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="dc8b9-110">구성을 적용하려면 [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="dc8b9-111">`-Path` 매개 변수는 ".mof" 파일이 있는 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="dc8b9-112">`-Computername`을 지정하지 않으면 `Start-DSCConfiguration`에서는 '.mof' 파일의 이름(\<computername\>.mof)으로 지정된 컴퓨터 이름에 각 구성을 적용하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="dc8b9-113">더 자세한 정보 출력을 보려면 `-Verbose`를 `Start-DSCConfiguration`으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="dc8b9-114">`-Wait`를 지정하지 않으면 생성된 하나의 작업이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="dc8b9-115">생성된 작업에는 `Start-DSCConfiguration`을 통해 처리된 각 ".mof" 파일에 대해 하나의 **ChildJob**이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="dc8b9-116">구성에 시간이 오래 걸리는 경우 구성을 중지하려면 [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)을 사용하여 로컬 노드에서 애플리케이션을 중지하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="dc8b9-117">완료되면 [Get-Job](/powershell/module/microsoft.powershell.core/get-job)에서 반환된 작업 개체를 통해 작업 상태를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

<span data-ttu-id="dc8b9-118">**자세한 정보** 출력을 보려면 다음 명령을 사용하여 각 **ChildJob**의 **자세한 정보** 스트림을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="dc8b9-119">PowerShell 작업에 대한 자세한 내용은 [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="dc8b9-120">PowerShell 5.0부터, `-UseExisting` 매개 변수가 `Start-DSCConfiguration`에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="dc8b9-121">`-UseExisting`을 지정하면 `-Path` 매개 변수로 지정된 구성 대신 기존 적용된 구성을 사용하도록 cmdlet에 지시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="dc8b9-122">구성 테스트</span><span class="sxs-lookup"><span data-stu-id="dc8b9-122">Test a Configuration</span></span>

<span data-ttu-id="dc8b9-123">[Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)을 사용하여 현재 적용된 구성을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="dc8b9-124">`Test-DSCConfiguration`은 노드가 준수 상태이면 `True`를 반환하고, 준수 상태가 아니면 `False`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="dc8b9-125">PowerShell 5.0부터, **ResourcesInDesiredState** 및 **ResourcesNotInDesiredState**에 대한 컬렉션이 포함된 개체를 반환하는 `-Detailed` 매개 변수가 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="dc8b9-126">PowerShell 5.0부터, 구성을 적용하지 않고 구성을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="dc8b9-127">`-ReferenceConfiguration` 매개 변수는 ".mof" 파일의 경로를 사용하여 노드를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="dc8b9-128">**Set** 작업은 노드에서 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="dc8b9-129">PowerShell 4.0에는 구성을 적용하지 않고 구성을 테스트하는 해결 방법이 있지만, 여기서는 해당 내용을 설명하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="dc8b9-130">구성 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="dc8b9-130">Get Configuration Values</span></span>

<span data-ttu-id="dc8b9-131">[Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet은 현재 적용된 구성에 있는 모든 구성된 리소스의 현재 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="dc8b9-132">성공적으로 적용된 경우 이 간단한 구성의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a><span data-ttu-id="dc8b9-133">구성 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="dc8b9-133">Get Configuration Status</span></span>

<span data-ttu-id="dc8b9-134">PowerShell 5.0부터, [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet을 사용하여 노드에 적용된 구성의 기록을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="dc8b9-135">PowerShell DSC는 **밀어넣기** 또는 **끌어오기** 모드에 적용된 마지막 {{N}}개 구성을 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="dc8b9-136">여기에는 LCM을 통해 실행된 모든 ‘일관성’ 검사가 포함됩니다. </span><span class="sxs-lookup"><span data-stu-id="dc8b9-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="dc8b9-137">기본적으로 `Get-DSCConfigurationStatus`는 마지막 기록 항목만 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="dc8b9-138">모든 구성 상태 기록을 보려면 `-All` 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="dc8b9-139">간단한 설명을 위해 출력이 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-139">Output is truncated for brevity.</span></span>

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a><span data-ttu-id="dc8b9-140">구성 문서 관리</span><span class="sxs-lookup"><span data-stu-id="dc8b9-140">Manage Configuration Documents</span></span>

<span data-ttu-id="dc8b9-141">LCM은 **구성 문서**를 사용하여 노드의 구성을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="dc8b9-142">이 ".mof" 파일은 "C:\Windows\System32\Configuration" 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="dc8b9-143">PowerShell 5.0부터, [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)를 사용하면 ".mof" 파일을 제거하여 미래 일관성 검사를 중지하거나 적용될 때 오류가 있는 구성을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="dc8b9-144">`-Stage` 매개 변수를 사용하여 제거할 ".mof" 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="dc8b9-145">PowerShell 4.0에서는 [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item)을 사용하여 직접 이 ".mof" 파일을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="dc8b9-146">구성 게시</span><span class="sxs-lookup"><span data-stu-id="dc8b9-146">Publish Configurations</span></span>

<span data-ttu-id="dc8b9-147">PowerShell 5.0부터, [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="dc8b9-148">이 cmdlet을 사용하여 ".mof" 파일을 적용하지 않고 원격 컴퓨터에 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc8b9-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="dc8b9-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dc8b9-149">See also</span></span>

- [<span data-ttu-id="dc8b9-150">가져오기, 테스트 및 설정</span><span class="sxs-lookup"><span data-stu-id="dc8b9-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
