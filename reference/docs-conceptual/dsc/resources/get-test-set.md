---
ms.date: 07/08/2020
keywords: dsc,powershell,configuration,setup
title: Get-Test-Set
ms.openlocfilehash: f7b7e947a85832365a783e40c25a25bfaa9fff8d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771518"
---
# <a name="get-test-set"></a><span data-ttu-id="852f1-103">Get-Test-Set</span><span class="sxs-lookup"><span data-stu-id="852f1-103">Get-Test-Set</span></span>

><span data-ttu-id="852f1-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="852f1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="852f1-105">PowerShell Desired State Configuration은 **Get**, **Test** 및 **Set** 프로세스 주위에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-105">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="852f1-106">DSC [리소스](resources.md)에는 각각 이와 같은 각 작업을 완료하는 메서드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-106">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span>
<span data-ttu-id="852f1-107">[구성](../configurations/configurations.md)에서 리소스 블록을 정의하여 리소스의 **Get**, **Test** 및 **Set** 메서드에 대한 매개 변수가 되는 키를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-107">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="852f1-108">이 구문은 **Service** 리소스 블록의 구문입니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-108">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="852f1-109">**Service** 리소스는 Windows 서비스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-109">The **Service** resource configures Windows services.</span></span>

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

<span data-ttu-id="852f1-110">**Service** 리소스의 **Get**, **Test** 및 **Set** 메서드에는 이 값을 허용하는 매개 변수 블록이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-110">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

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
> <span data-ttu-id="852f1-111">리소스를 정의하는 데 사용되는 언어 및 메서드에 따라 **Get**, **Test** 및 **Set** 메서드를 정의하는 방법이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-111">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="852f1-112">**Service** 리소스에는 하나의 필수 키(`Name`)만 있으므로 **Service** 블록 리소스는 다음과 같이 간단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-112">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

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

<span data-ttu-id="852f1-113">위의 구성을 컴파일하면 키에 지정하는 값이 생성된 `.mof` 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-113">When you compile the Configuration above, the values you specify for a key are stored in the `.mof` file that is generated.</span></span> <span data-ttu-id="852f1-114">자세한 내용은 [MOF](/windows/desktop/wmisdk/managed-object-format--mof-)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="852f1-114">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

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

<span data-ttu-id="852f1-115">적용되면 LCM([로컬 구성 관리자](../managing-nodes/metaConfig.md))이 `.mof` 파일에서 “Spooler” 값을 읽고 **Service** 리소스의 “MyService” 인스턴스에 대한 **Get**, **Test** 및 **Set**의 **Name** 매개 변수에 해당 값을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-115">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) (LCM) will read the value "Spooler" from the `.mof` file, and pass it to the **Name** parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="852f1-116">가져오기</span><span class="sxs-lookup"><span data-stu-id="852f1-116">Get</span></span>

<span data-ttu-id="852f1-117">리소스의 **Get** 메서드는 대상 노드에서 구성되어 있는 리소스의 상태를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-117">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="852f1-118">이 상태는 [해시 테이블](/powershell/module/microsoft.powershell.core/about/about_hash_tables)로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-118">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>
<span data-ttu-id="852f1-119">**해시 테이블**의 키는 구성 가능한 값이거나 리소스가 허용하는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-119">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="852f1-120">**Get** 메서드는 [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet에 직접 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-120">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="852f1-121">`Get-DSCConfiguration`을 호출하면 LCM은 현재 적용된 구성에서 각 리소스의 **Get** 메서드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-121">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="852f1-122">LCM은 `.mof` 파일에 저장된 키 값을 각 해당 리소스 인스턴스의 매개 변수로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-122">The LCM uses the key values stored in the `.mof` file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="852f1-123">이 출력은 “Spooler” 서비스를 구성하는 **Service** 리소스의 샘플 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-123">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

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

<span data-ttu-id="852f1-124">출력에는 **Service** 리소스에서 구성 가능한 현재 값 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-124">The output shows the current value properties configurable by the **Service** resource.</span></span>

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

## <a name="test"></a><span data-ttu-id="852f1-125">테스트</span><span class="sxs-lookup"><span data-stu-id="852f1-125">Test</span></span>

<span data-ttu-id="852f1-126">리소스의 **Test** 메서드는 대상 노드가 현재 리소스의 ‘원하는 상태’를 준수하는지 확인합니다.__</span><span class="sxs-lookup"><span data-stu-id="852f1-126">The **Test** method of a resource determines if the target node is currently compliant with the resource's _desired state_.</span></span> <span data-ttu-id="852f1-127">**Test** 메서드는 `$true` 또는 `$false`만 반환하여 노드의 준수 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-127">The **Test** method returns `$true` or `$false` only to indicate whether the Node is compliant.</span></span> <span data-ttu-id="852f1-128">[Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)을 호출하면 LCM은 현재 적용된 구성에서 각 리소스의 **Test** 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-128">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="852f1-129">LCM은 ".mof" 파일에 저장된 키 값을 각 해당 리소스 인스턴스의 매개 변수로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-129">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="852f1-130">개별 리소스 **Test**의 결과가 `$false`이면 `Test-DSCConfiguration`은 노드가 준수하지 않음을 나타내는 `$false`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-130">If the result of any individual resource's **Test** is `$false`, `Test-DSCConfiguration` returns `$false` indicating that the Node is not compliant.</span></span> <span data-ttu-id="852f1-131">모든 리소스 **Test** 메서드가 `$true`를 반환하면 `Test-DSCConfiguration`은 노드가 준수함을 나타내는 `$true`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-131">If all resource's **Test** methods return `$true`, `Test-DSCConfiguration` returns `$true` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="852f1-132">PowerShell 5.0부터, **Detailed** 매개 변수가 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-132">Beginning in PowerShell 5.0, the **Detailed** parameter was added.</span></span> <span data-ttu-id="852f1-133">**Detailed**를 지정하면 `Test-DSCConfiguration`에서 준수 및 비준수 리소스에 대한 결과 컬렉션을 포함하는 개체가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-133">Specifying **Detailed** causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="852f1-134">자세한 내용은 [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="852f1-134">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="852f1-135">설정</span><span class="sxs-lookup"><span data-stu-id="852f1-135">Set</span></span>

<span data-ttu-id="852f1-136">리소스의 **Set** 메서드는 노드가 리소스의 ‘원하는 상태’를 강제로 준수하도록 합니다.\*\*</span><span class="sxs-lookup"><span data-stu-id="852f1-136">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="852f1-137">**Set** 메서드는 **멱등성(idempotent)** 이 되어야 합니다. 이는 **Set**이 여러 번 실행되고 오류 없이 항상 동일한 결과를 가져올 수 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-137">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span> <span data-ttu-id="852f1-138">[Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration)을 실행하면 LCM은 현재 적용된 구성에서 각 리소스를 순환합니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-138">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="852f1-139">LCM은 “.mof” 파일에서 현재 리소스 인스턴스의 키 값을 검색하고 **Test** 메서드의 매개 변수로 이 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-139">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="852f1-140">**Test** 메서드가 `$true`를 반환하면 노드는 현재 리소스를 준수하고 **Set** 메서드를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-140">If the **Test** method returns `$true`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="852f1-141">**Test**가 `$false`를 반환하면 노드는 비준수 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-141">If the **Test** returns `$false`, the Node is non-compliant.</span></span> <span data-ttu-id="852f1-142">LCM은 리소스 인스턴스의 키 값을 매개 변수로 리소스의 **Set** 메서드에 전달하여 노드를 준수 상태로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-142">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="852f1-143">**Verbose** 및 **Wait** 매개 변수를 지정하여 `Start-DSCConfiguration` cmdlet의 진행 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-143">By specifying the **Verbose** and **Wait** parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="852f1-144">이 예제에서 노드는 이미 준수 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-144">In this example, the Node is already compliant.</span></span> <span data-ttu-id="852f1-145">`Verbose` 출력은 **Set** 메서드를 건너뛰었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="852f1-145">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="852f1-146">참조</span><span class="sxs-lookup"><span data-stu-id="852f1-146">See also</span></span>

- [<span data-ttu-id="852f1-147">Azure Automation DSC 개요</span><span class="sxs-lookup"><span data-stu-id="852f1-147">Azure Automation DSC Overview</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="852f1-148">SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="852f1-148">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="852f1-149">끌어오기 클라이언트 구성</span><span class="sxs-lookup"><span data-stu-id="852f1-149">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
