---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 리소스 디버그
description: 이 문서에서는 DSC 구성에 디버깅을 사용하도록 설정하는 방법을 보여 줍니다.
ms.openlocfilehash: 5dda217e8dc9cc4b8699c82153c1a588d405d99e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654129"
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="540d3-104">DSC 리소스 디버그</span><span class="sxs-lookup"><span data-stu-id="540d3-104">Debugging DSC resources</span></span>

> <span data-ttu-id="540d3-105">적용 대상: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="540d3-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="540d3-106">PowerShell 5.0에서는 구성이 적용됨에 따라 DSC 리소스를 디버그할 수 있도록 해주는 새로운 기능이 DSC(필요한 상태 구성)에 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-106">In PowerShell 5.0, a new feature was introduced in Desired State Configuration (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="540d3-107">DSC 디버그 사용</span><span class="sxs-lookup"><span data-stu-id="540d3-107">Enabling DSC debugging</span></span>

<span data-ttu-id="540d3-108">리소스를 디버그할 수 있으려면 먼저, [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet을 호출하여 디버그할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-108">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet.</span></span> <span data-ttu-id="540d3-109">이 cmdlet은 필수 매개 변수인 **BreakAll** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-109">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span>

<span data-ttu-id="540d3-110">[Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)를 호출한 결과를 보면 디버그할 수 있게 되어 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-110">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span></span>

<span data-ttu-id="540d3-111">다음의 PowerShell 출력은 디버그 사용의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-111">The following PowerShell output shows the result of enabling debugging:</span></span>

```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```

## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="540d3-112">디버그를 사용하도록 설정된 구성 시작</span><span class="sxs-lookup"><span data-stu-id="540d3-112">Starting a configuration with debug enabled</span></span>

<span data-ttu-id="540d3-113">DSC 리소스를 디버그하려면 해당 리소스를 호출하는 구성을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-113">To debug a DSC resource, you start a configuration that calls that resource.</span></span> <span data-ttu-id="540d3-114">예를 들어 **WindowsFeature** 리소스를 호출하여 "WindowsPowerShellWebAccess" 기능이 설치되어 있는지 확인하는 간단한 구성을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-114">For this example, we'll look at a simple configuration that calls the **WindowsFeature** resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```

<span data-ttu-id="540d3-115">구성을 컴파일한 후에는 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)을 호출하여 구성을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-115">After compiling the configuration, start it by calling [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span></span> <span data-ttu-id="540d3-116">이 구성은 LCM(로컬 구성 관리자)이 구성의 첫 번째 리소스를 호출하면 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-116">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span> <span data-ttu-id="540d3-117">`-Verbose` 및 `-Wait` 매개 변수를 사용하는 경우, 출력에 디버그를 시작하려면 입력해야 하는 줄이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-117">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

```powershell
Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.
Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```

<span data-ttu-id="540d3-118">이 시점에서 LCM은 리소스를 호출하고 첫 번째 중단점으로 이동했습니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-118">At this point, the LCM has called the resource, and come to the first break point.</span></span> <span data-ttu-id="540d3-119">출력의 마지막 세 줄에는 프로세스에 연결하여 리소스 스크립트의 디버그를 시작하는 방법이 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-119">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="540d3-120">리소스 스크립트 디버그</span><span class="sxs-lookup"><span data-stu-id="540d3-120">Debugging the resource script</span></span>

<span data-ttu-id="540d3-121">PowerShell ISE의 새 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-121">Start a new instance of the PowerShell ISE.</span></span> <span data-ttu-id="540d3-122">콘솔 창에서 `Start-DscConfiguration` 출력으로부터 나온 결과의 마지막 세 줄을 명령으로 입력하여 `<credentials>`를 올바른 사용자 자격 증명으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-122">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span> <span data-ttu-id="540d3-123">이제 다음과 유사한 프롬프트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-123">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="540d3-124">리소스 스크립트가 스크립트 창에 열리고 디버거가 **Test-TargetResource** 함수(클래스 기반 리소스의 **Test()** 메서드)의 첫째 줄에서 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-124">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span> <span data-ttu-id="540d3-125">이제 ISE에서 디버그 명령을 사용하여 리소스 스크립트 단계별 실행, 변수 값 확인, 호출 스택 보기 등을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-125">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span> <span data-ttu-id="540d3-126">리소스 스크립트 (또는 클래스)의 모든 줄은 중단점으로 설정된다는 점을 기억하세요.</span><span class="sxs-lookup"><span data-stu-id="540d3-126">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="540d3-127">DSC 디버그 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="540d3-127">Disabling DSC debugging</span></span>

<span data-ttu-id="540d3-128">[Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)를 호출한 후 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)을 호출하면 항상 구성으로 인해 디버거가 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-128">After calling [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), all calls to [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="540d3-129">구성이 정상적으로 실행되도록 하려면 [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet을 호출하여 디버깅을 사용하지 않도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-129">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="540d3-130">재부팅해도 LCM의 디버그 상태가 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-130">Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="540d3-131">디버깅을 사용하도록 설정하는 경우 재부팅 후 구성을 시작하면 여전히 디버거가 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="540d3-131">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>

## <a name="see-also"></a><span data-ttu-id="540d3-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="540d3-132">See Also</span></span>

- [<span data-ttu-id="540d3-133">MOF를 사용하여 사용자 지정 DSC 리소스 작성</span><span class="sxs-lookup"><span data-stu-id="540d3-133">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="540d3-134">PowerShell 클래스를 사용하여 사용자 지정 DSC 리소스 작성</span><span class="sxs-lookup"><span data-stu-id="540d3-134">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
