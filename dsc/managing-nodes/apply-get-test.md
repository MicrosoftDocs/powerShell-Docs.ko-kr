---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 노드에서 구성 적용, 가져오기 및 테스트
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402948"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="54f1d-103">노드에서 구성 적용, 가져오기 및 테스트</span><span class="sxs-lookup"><span data-stu-id="54f1d-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="54f1d-104">이 가이드에서는 대상 노드에 구성을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="54f1d-105">이 가이드는 다음 단계를로 세분화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="54f1d-106">구성 적용</span><span class="sxs-lookup"><span data-stu-id="54f1d-106">Apply a Configuration</span></span>

<span data-ttu-id="54f1d-107">적용 하 고 구성 관리를 위해 ".mof" 파일을 생성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="54f1d-108">다음 코드는이 가이드 전체에서 사용 되는 간단한 구성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

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

<span data-ttu-id="54f1d-109">이 구성을 컴파일하면 ".mof" 파일을 두 개 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="54f1d-110">구성을 적용 하려면 사용 합니다 [Start-dscconfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="54f1d-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="54f1d-111">`-Path` 매개 변수 ".mof" 파일이 있는 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="54f1d-112">없으면 `-Computername` 지정 된 `Start-DSCConfiguration` '.mof' 파일의 이름으로 지정 된 컴퓨터 이름에 각 구성을 적용 하려고 합니다 (\<computername\>.mof).</span><span class="sxs-lookup"><span data-stu-id="54f1d-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="54f1d-113">지정할 `-Verbose` 에 `Start-DSCConfiguration` 자세한 출력을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="54f1d-114">경우 `-Wait` 지정 하지 않으면 만든 하나의 작업을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="54f1d-115">만든 작업 하나가 포함 됩니다 **ChildJob** 에서 각 ".mof" 파일에 대 한 처리 `Start-DSCConfiguration`합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="54f1d-116">구성에 오랜 시간이 소요 됩니다 하 고 중지 하려는 사용할 수 있습니다 [Stop-dscconfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) 로컬 노드에서 응용 프로그램을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="54f1d-117">완료 되 면 반환 하는 작업 개체를 통해 작업의 상태를 볼 수 있습니다 [Get-job](/powershell/module/microsoft.powershell.core/get-job)합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

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

<span data-ttu-id="54f1d-118">보려는 **Verbose** 출력을 보려면 다음 명령을 사용 합니다 **Verbose** 스트림 각각에 대 한 **ChildJob**합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="54f1d-119">PowerShell 작업에 대 한 자세한 내용은 참조 하세요 [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

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

<span data-ttu-id="54f1d-120">PowerShell 5.0에서 시작 합니다 `-UseExisting` 매개 변수를 추가한 `Start-DSCConfiguration`합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="54f1d-121">지정 하 여 `-UseExisting`, cmdlet이 적용된 된 기존 구성에서 지정 하는 대신 사용 하도록 지시 합니다 `-Path` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="54f1d-122">구성 테스트</span><span class="sxs-lookup"><span data-stu-id="54f1d-122">Test a Configuration</span></span>

<span data-ttu-id="54f1d-123">사용 하 여 현재 적용 된 구성을 테스트할 수 있습니다 [Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="54f1d-124">`Test-DSCConfiguration` 돌아갑니다 `True` 노드인 준수 하는 경우 및 `False` 없는 경우.</span><span class="sxs-lookup"><span data-stu-id="54f1d-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="54f1d-125">PowerShell 5.0에서 시작 합니다 `-Detailed` 매개 변수 컬렉션을 사용 하 여 개체를 반환 하는 추가 되었습니다 **ResourcesInDesiredState** 고 **ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="54f1d-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="54f1d-126">PowerShell 5.0에서부터 적용 하지 않고 구성을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="54f1d-127">`-ReferenceConfiguration` 매개 변수는 노드를 테스트 하려면 "mof" 파일의 경로 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="54f1d-128">아니오 **설정** 노드에 대해 동작이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="54f1d-129">PowerShell 4.0에서 대안을 적용 하지 않고 구성을 테스트 하려면 있고 여기서 설명 하지 않은 합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="54f1d-130">구성 값을 얻으려면</span><span class="sxs-lookup"><span data-stu-id="54f1d-130">Get Configuration Values</span></span>

<span data-ttu-id="54f1d-131">합니다 [Get-dscconfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet은 현재 적용된 된 구성에 구성 된 모든 리소스에 대 한 현재 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="54f1d-132">샘플 구성에서에서 출력 성공적으로 적용 하는 경우 다음과 같이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

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

## <a name="get-configuration-status"></a><span data-ttu-id="54f1d-133">구성 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-133">Get Configuration Status</span></span>

<span data-ttu-id="54f1d-134">PowerShell 5.0부터 합니다 [Get-dscconfigurationstatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet을 사용 하면 적용 된 노드 구성의 기록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="54f1d-135">PowerShell DSC에 적용 하는 마지막 {{N}을 (를) 구성 하는 추적 **푸시** 하거나 **끌어오기** 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="54f1d-136">여기에 모든 *일관성* 검사에서 LCM에 의해 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="54f1d-137">기본적으로 `Get-DSCConfigurationStatus` 마지막 기록 항목에만 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="54f1d-138">사용 된 `-All` 모든 구성 상태 기록을 보려면 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="54f1d-139">간단한 설명을 위해 출력이 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-139">Output is truncated for brevity.</span></span>

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

## <a name="manage-configuration-documents"></a><span data-ttu-id="54f1d-140">구성 문서를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-140">Manage Configuration Documents</span></span>

<span data-ttu-id="54f1d-141">사용 하 여 노드 구성을 관리 하는 LCM **구성 문서**합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="54f1d-142">이러한 ".mof" files "C:\Windows\System32\Configuration" 디렉터리에 있어야합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="54f1d-143">PowerShell 5.0부터 합니다 [Remove-dscconfigurationdocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) 이후 일관성 검사를 중지 하거나 적용 하는 경우 오류를 가진 구성 제거 ".mof" 파일을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="54f1d-144">`-Stage` 매개 변수를 사용 하면 제거 하려는 ".mof" 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="54f1d-145">PowerShell 4.0에서 제거할 수 있습니다 여전히 이러한 ".mof" 파일을 사용 하 여 직접 [Remove-item](/powershell/module/microsoft.powershell.management/remove-item)합니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="54f1d-146">게시 구성</span><span class="sxs-lookup"><span data-stu-id="54f1d-146">Publish Configurations</span></span>

<span data-ttu-id="54f1d-147">PowerShell 5.0에서 시작 합니다 [Publish-dscconfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="54f1d-148">이 cmdlet을 사용 하면 원격 컴퓨터에 적용 하지 않고 ".mof" 파일을 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f1d-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="54f1d-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="54f1d-149">See also</span></span>

- [<span data-ttu-id="54f1d-150">가져오기, 테스트 및 설정</span><span class="sxs-lookup"><span data-stu-id="54f1d-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
