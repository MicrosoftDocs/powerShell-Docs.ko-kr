---
ms.date: 07/08/2020
keywords: dsc,powershell,configuration,setup
title: Get-Test-Set
description: 이 문서는 DSC 구성에서 Get, Test, Set 메서드를 구현하는 방법을 보여 줍니다.
ms.openlocfilehash: e0da1452a1237c550f52a4a4f9e4400f801ed7cd
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646804"
---
# <a name="get-test-set"></a><span data-ttu-id="1cf1a-104">Get-Test-Set</span><span class="sxs-lookup"><span data-stu-id="1cf1a-104">Get-Test-Set</span></span>

><span data-ttu-id="1cf1a-105">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1cf1a-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1cf1a-106">PowerShell Desired State Configuration은 **Get** , **Test** 및 **Set** 프로세스 주위에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-106">PowerShell Desired State Configuration is constructed around a **Get** , **Test** , and **Set** process.</span></span> <span data-ttu-id="1cf1a-107">DSC [리소스](resources.md)에는 각각 이와 같은 각 작업을 완료하는 메서드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span>
<span data-ttu-id="1cf1a-108">[구성](../configurations/configurations.md)에서 리소스 블록을 정의하여 리소스의 **Get** , **Test** 및 **Set** 메서드에 대한 매개 변수가 되는 키를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get** , **Test** , and **Set** methods.</span></span>

<span data-ttu-id="1cf1a-109">이 구문은 **Service** 리소스 블록의 구문입니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="1cf1a-110">**Service** 리소스는 Windows 서비스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-110">The **Service** resource configures Windows services.</span></span>

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="1cf1a-111">**Service** 리소스의 **Get** , **Test** 및 **Set** 메서드에는 이 값을 허용하는 매개 변수 블록이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-111">The **Get** , **Test** , and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

```powershell
param
(
    [parameter(Mandatory = $true)]
    [ValidateNotNullOrEmpty()]
    [System.String]
    $Name,

    [System.String]
    [ValidateSet("Automatic", "Manual", "Disabled")]
    $StartupType,

    [System.String]
    [ValidateSet("LocalSystem", "LocalService", "NetworkService")]
    $BuiltInAccount,

    [System.Management.Automation.PSCredential]
    [ValidateNotNull()]
    $Credential,

    [System.String]
    [ValidateSet("Running", "Stopped")]
    $State="Running",

    [System.String]
    [ValidateNotNullOrEmpty()]
    $DisplayName,

    [System.String]
    [ValidateNotNullOrEmpty()]
    $Description,

    [System.String]
    [ValidateNotNullOrEmpty()]
    $Path,

    [System.String[]]
    [ValidateNotNullOrEmpty()]
    $Dependencies,

    [System.String]
    [ValidateSet("Present", "Absent")]
    $Ensure="Present"
)
```

> [!NOTE]
> <span data-ttu-id="1cf1a-112">리소스를 정의하는 데 사용되는 언어 및 메서드에 따라 **Get** , **Test** 및 **Set** 메서드를 정의하는 방법이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-112">The language and method used to define the resource determines how the **Get** , **Test** , and **Set** methods will be defined.</span></span>

<span data-ttu-id="1cf1a-113">**Service** 리소스에는 하나의 필수 키(`Name`)만 있으므로 **Service** 블록 리소스는 다음과 같이 간단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

```powershell
Configuration TestConfig
{
    Import-DSCResource -Name Service
    Node localhost
    {
        Service "MyService"
        {
            Name = "Spooler"
        }
    }
}
```

<span data-ttu-id="1cf1a-114">위의 구성을 컴파일하면 키에 지정하는 값이 생성된 `.mof` 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-114">When you compile the Configuration above, the values you specify for a key are stored in the `.mof` file that is generated.</span></span> <span data-ttu-id="1cf1a-115">자세한 내용은 [MOF](/windows/desktop/wmisdk/managed-object-format--mof-)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

```
instance of MSFT_ServiceResource as $MSFT_ServiceResource1ref
{
SourceInfo = "::5::1::Service";
 ModuleName = "PsDesiredStateConfiguration";
 ResourceID = "[Service]MyService";
 Name = "Spooler";

ModuleVersion = "1.0";

 ConfigurationName = "Test";

};
```

<span data-ttu-id="1cf1a-116">적용되면 LCM( [로컬 구성 관리자](../managing-nodes/metaConfig.md))이 `.mof` 파일에서 “Spooler” 값을 읽고 **Service** 리소스의 “MyService” 인스턴스에 대한 **Get** , **Test** 및 **Set** 의 **Name** 매개 변수에 해당 값을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) (LCM) will read the value "Spooler" from the `.mof` file, and pass it to the **Name** parameter of the **Get** , **Test** , and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="1cf1a-117">가져오기</span><span class="sxs-lookup"><span data-stu-id="1cf1a-117">Get</span></span>

<span data-ttu-id="1cf1a-118">리소스의 **Get** 메서드는 대상 노드에서 구성되어 있는 리소스의 상태를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="1cf1a-119">이 상태는 [해시 테이블](/powershell/module/microsoft.powershell.core/about/about_hash_tables)로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="1cf1a-120">**해시 테이블** 의 키는 구성 가능한 값이거나 리소스가 허용하는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="1cf1a-121">**Get** 메서드는 [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet에 직접 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span>
<span data-ttu-id="1cf1a-122">`Get-DSCConfiguration`을 호출하면 LCM은 현재 적용된 구성에서 각 리소스의 **Get** 메서드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="1cf1a-123">LCM은 `.mof` 파일에 저장된 키 값을 각 해당 리소스 인스턴스의 매개 변수로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-123">The LCM uses the key values stored in the `.mof` file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="1cf1a-124">이 출력은 “Spooler” 서비스를 구성하는 **Service** 리소스의 샘플 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

```output
ConfigurationName    : Test
DependsOn            :
ModuleName           : PsDesiredStateConfiguration
ModuleVersion        : 1.1
PsDscRunAsCredential :
ResourceId           : [Service]Spooler
SourceInfo           :
BuiltInAccount       : LocalSystem
Credential           :
Dependencies         : {RPCSS, http}
Description          : This service spools print jobs and handles interaction with the printer.  If you turn off
                       this service, you won't be able to print or see your printers.
DisplayName          : Print Spooler
Ensure               :
Name                 : Spooler
Path                 : C:\WINDOWS\System32\spoolsv.exe
StartupType          : Automatic
State                : Running
Status               :
PSComputerName       :
CimClassName         : MSFT_ServiceResource
```

<span data-ttu-id="1cf1a-125">출력에는 **Service** 리소스에서 구성 가능한 현재 값 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

## <a name="test"></a><span data-ttu-id="1cf1a-126">테스트</span><span class="sxs-lookup"><span data-stu-id="1cf1a-126">Test</span></span>

<span data-ttu-id="1cf1a-127">리소스의 **Test** 메서드는 대상 노드가 현재 리소스의 ‘원하는 상태’를 준수하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's _desired state_.</span></span> <span data-ttu-id="1cf1a-128">**Test** 메서드는 `$true` 또는 `$false`만 반환하여 노드의 준수 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-128">The **Test** method returns `$true` or `$false` only to indicate whether the Node is compliant.</span></span> <span data-ttu-id="1cf1a-129">[Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)을 호출하면 LCM은 현재 적용된 구성에서 각 리소스의 **Test** 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="1cf1a-130">LCM은 ".mof" 파일에 저장된 키 값을 각 해당 리소스 인스턴스의 매개 변수로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="1cf1a-131">개별 리소스 **Test** 의 결과가 `$false`이면 `Test-DSCConfiguration`은 노드가 준수하지 않음을 나타내는 `$false`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-131">If the result of any individual resource's **Test** is `$false`, `Test-DSCConfiguration` returns `$false` indicating that the Node is not compliant.</span></span> <span data-ttu-id="1cf1a-132">모든 리소스 **Test** 메서드가 `$true`를 반환하면 `Test-DSCConfiguration`은 노드가 준수함을 나타내는 `$true`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-132">If all resource's **Test** methods return `$true`, `Test-DSCConfiguration` returns `$true` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="1cf1a-133">PowerShell 5.0부터, **Detailed** 매개 변수가 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-133">Beginning in PowerShell 5.0, the **Detailed** parameter was added.</span></span> <span data-ttu-id="1cf1a-134">**Detailed** 를 지정하면 `Test-DSCConfiguration`에서 준수 및 비준수 리소스에 대한 결과 컬렉션을 포함하는 개체가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-134">Specifying **Detailed** causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="1cf1a-135">자세한 내용은 [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

## <a name="set"></a><span data-ttu-id="1cf1a-136">설정</span><span class="sxs-lookup"><span data-stu-id="1cf1a-136">Set</span></span>

<span data-ttu-id="1cf1a-137">리소스의 **Set** 메서드는 노드가 리소스의 ‘원하는 상태’를 강제로 준수하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="1cf1a-138">**Set** 메서드는 **멱등성(idempotent)** 이 되어야 합니다. 이는 **Set** 이 여러 번 실행되고 오류 없이 항상 동일한 결과를 가져올 수 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-138">The **Set** method is meant to be **idempotent** , which means that **Set** could be run multiple times and always get the same result without errors.</span></span> <span data-ttu-id="1cf1a-139">[Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration)을 실행하면 LCM은 현재 적용된 구성에서 각 리소스를 순환합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="1cf1a-140">LCM은 “.mof” 파일에서 현재 리소스 인스턴스의 키 값을 검색하고 **Test** 메서드의 매개 변수로 이 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="1cf1a-141">**Test** 메서드가 `$true`를 반환하면 노드는 현재 리소스를 준수하고 **Set** 메서드를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-141">If the **Test** method returns `$true`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="1cf1a-142">**Test** 가 `$false`를 반환하면 노드는 비준수 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-142">If the **Test** returns `$false`, the Node is non-compliant.</span></span> <span data-ttu-id="1cf1a-143">LCM은 리소스 인스턴스의 키 값을 매개 변수로 리소스의 **Set** 메서드에 전달하여 노드를 준수 상태로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="1cf1a-144">**Verbose** 및 **Wait** 매개 변수를 지정하여 `Start-DSCConfiguration` cmdlet의 진행 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-144">By specifying the **Verbose** and **Wait** parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="1cf1a-145">이 예제에서 노드는 이미 준수 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="1cf1a-146">`Verbose` 출력은 **Set** 메서드를 건너뛰었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1cf1a-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

```
PS> Start-DSCConfiguration -Verbose -Wait -UseExisting

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
ApplyConfiguration,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid
S-1-5-21-124525095-708259637-1543119021-1282804.
VERBOSE: [SERVER01]:                            [] Starting consistency engine.
VERBOSE: [SERVER01]:                            [] Checking consistency for current configuration.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module
C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\DscResources\MSFT_ServiceResource\MSFT
_ServiceResource.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [[Service]Spooler] Importing the module MSFT_ServiceResource in
force mode.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Service]Spooler]  in 0.2540 seconds.
VERBOSE: [SERVER01]: LCM:  [ Skip   Set      ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [] Consistency check completed.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 1.379 seconds
```

## <a name="see-also"></a><span data-ttu-id="1cf1a-147">참조</span><span class="sxs-lookup"><span data-stu-id="1cf1a-147">See also</span></span>

- [<span data-ttu-id="1cf1a-148">Azure Automation DSC 개요</span><span class="sxs-lookup"><span data-stu-id="1cf1a-148">Azure Automation DSC Overview</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="1cf1a-149">SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="1cf1a-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="1cf1a-150">끌어오기 클라이언트 구성</span><span class="sxs-lookup"><span data-stu-id="1cf1a-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
