---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 가져오기-테스트-설정
ms.openlocfilehash: 6d059518a49926bc5fb56e37e7d3d4d2c66bddec
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682203"
---
# <a name="get-test-set"></a><span data-ttu-id="6b081-103">가져오기-테스트-설정</span><span class="sxs-lookup"><span data-stu-id="6b081-103">Get-Test-Set</span></span>

><span data-ttu-id="6b081-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6b081-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

![가져오기, 테스트 및 설정](/media/get-test-set.png)

<span data-ttu-id="6b081-106">PowerShell Desired State Configuration 주위에 생성 된 **가져오기**, **테스트**, 및 **설정** 프로세스.</span><span class="sxs-lookup"><span data-stu-id="6b081-106">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="6b081-107">DSC [리소스](resources.md) 각각 이러한 각 작업을 완료 하는 메서드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span> <span data-ttu-id="6b081-108">에 [구성](../configurations/configurations.md), 리소스 블록을 리소스에 대 한 매개 변수는 키 입력을 정의한 **가져오기**를 **테스트**, 및 **설정** 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="6b081-109">에 대 한 구문은이 **서비스** 리소스 블록.</span><span class="sxs-lookup"><span data-stu-id="6b081-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="6b081-110">합니다 **서비스** 리소스는 Windows 서비스를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-110">The **Service** resource configures Windows services.</span></span>

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

<span data-ttu-id="6b081-111">**가져오기**, **테스트**, 및 **설정** 메서드를 **서비스** 리소스 이러한 값을 허용 하는 매개 변수 블록을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-111">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

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
> <span data-ttu-id="6b081-112">언어 및 리소스를 정의 하는 데 사용 되는 메서드를 결정 하는 방법을 **가져옵니다**, **테스트**, 및 **설정** 메서드 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-112">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="6b081-113">때문에 합니다 **서비스** 리소스에만 필수 키에 (`Name`), **서비스** 블록 리소스는이 처럼 간단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

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

<span data-ttu-id="6b081-114">위의 구성을 컴파일하는 경우 키에 대 한 지정 된 값이 생성 되는 ".mof" 파일에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-114">When you compile the Configuration above, the values you specify for a key are stored in the ".mof" file that is generated.</span></span> <span data-ttu-id="6b081-115">자세한 내용은 [MOF](/windows/desktop/wmisdk/managed-object-format--mof-)합니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

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

<span data-ttu-id="6b081-116">적용 하는 경우는 [로컬 구성 관리자](../managing-nodes/metaConfig.md) "Spooler" 값 ".mof" 파일에서 읽고에 전달 합니다 `-Name` 의 매개 변수를 **가져오기**, **테스트**, 및 **설정할** "MyService" 인스턴스에 대 한 메서드는 **서비스** 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) will read the value "Spooler" from the ".mof" file, and pass it to the `-Name` parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="6b081-117">get</span><span class="sxs-lookup"><span data-stu-id="6b081-117">Get</span></span>

<span data-ttu-id="6b081-118">합니다 **가져올** 메서드는 리소스의 대상 노드에 구성 된 대로 리소스의 상태를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="6b081-119">이 상태로 반환 되는 [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="6b081-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="6b081-120">키를 **hashtable** 됩니다 구성 가능한 값 또는 매개 변수는 리소스를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="6b081-121">**가져오기** 메서드를 직접 매핑합니다 합니다 [Get-dscconfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6b081-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="6b081-122">호출 하는 경우 `Get-DSCConfiguration`, LCM 실행 합니다 **가져올** 현재 적용된 된 구성의 각 리소스는 메서드.</span><span class="sxs-lookup"><span data-stu-id="6b081-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="6b081-123">LCM는 각 해당 리소스 인스턴스에 대 한 매개 변수로 ".mof" 파일에 저장 된 키 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-123">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="6b081-124">샘플 출력은이 **서비스** "Spooler" 서비스를 구성 하는 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

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
                       this service, you won’t be able to print or see your printers.
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

<span data-ttu-id="6b081-125">출력의 현재 값 속성을 구성할 수 있습니다 표시 합니다 **서비스** 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

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

## <a name="test"></a><span data-ttu-id="6b081-126">테스트</span><span class="sxs-lookup"><span data-stu-id="6b081-126">Test</span></span>

<span data-ttu-id="6b081-127">합니다 **테스트** 메서드는 리소스의 대상 노드 리소스의 현재 호환 되는 경우 결정 *필요한 상태*합니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's *desired state*.</span></span> <span data-ttu-id="6b081-128">합니다 **테스트** 메서드가 반환 `$True` 또는 `$False` 노드 규격 인지 여부를 나타낼 때만 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-128">The **Test** method returns `$True` or `$False` only to indicate whether the Node is compliant.</span></span>
<span data-ttu-id="6b081-129">호출 하는 경우 [Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), LCM 호출 합니다 **테스트** 현재 적용된 된 구성의 각 리소스는 메서드.</span><span class="sxs-lookup"><span data-stu-id="6b081-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="6b081-130">LCM는 각 해당 리소스 인스턴스에 대 한 매개 변수로 ".mof" 파일에 저장 된 키 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="6b081-131">경우 모든 개별 리소스의 결과인 **테스트** 는 `$False`, `Test-DSCConfiguration` 반환 `$False` 노드 규격 임을 나타내는입니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-131">If the result of any individual resource's **Test** is `$False`, `Test-DSCConfiguration` returns `$False` indicating that the Node is not compliant.</span></span> <span data-ttu-id="6b081-132">경우 모든 리소스 **테스트** 메서드는 반환 `$True`, `Test-DSCConfiguration` 반환 `$True` 노드 규격 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-132">If all resource's **Test** methods return `$True`, `Test-DSCConfiguration` returns `$True` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="6b081-133">PowerShell 5.0부터는 `-Detailed` 매개 변수 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-133">Beginning in PowerShell 5.0, the `-Detailed` parameter was added.</span></span> <span data-ttu-id="6b081-134">지정 `-Detailed` 하면 `Test-DSCConfiguration` 호환 및 호환 되지 않는 리소스에 대 한 결과의 컬렉션을 포함 하는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-134">Specifying `-Detailed` causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="6b081-135">자세한 내용은 참조 하세요. [Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span><span class="sxs-lookup"><span data-stu-id="6b081-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="6b081-136">Set(영문)</span><span class="sxs-lookup"><span data-stu-id="6b081-136">Set</span></span>

<span data-ttu-id="6b081-137">합니다 **설정** 메서드는 리소스의 노드 리소스의 준수를 강제로 시도할지 *필요한 상태*합니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="6b081-138">합니다 **설정** 메서드를 사용할 계획이 **idempotent**, 즉 **설정** 여러 번 실행 하 고 항상 오류 없이 같은 결과 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-138">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span>  <span data-ttu-id="6b081-139">실행할 때 [Start-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), 각 리소스에 현재 적용된 된 구성 LCM 순환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="6b081-140">LCM ".mof" 파일에서 현재 리소스 인스턴스에 대 한 키 값을 검색 하 고 매개 변수로 사용 하 여 **테스트** 메서드.</span><span class="sxs-lookup"><span data-stu-id="6b081-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="6b081-141">경우는 **테스트** 메서드가 반환 `$True`, 노드는 현재 리소스, 호환 및 **설정** 메서드를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-141">If the **Test** method returns `$True`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="6b081-142">경우는 **테스트** 반환 `$False`, 노드인 비준수입니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-142">If the **Test** returns `$False`, the Node is non-compliant.</span></span>  <span data-ttu-id="6b081-143">LCM은 리소스 인스턴스의 키 값 매개 변수로 전달 리소스의 **설정** 메서드를 준수 하려면 노드를 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="6b081-144">지정 하 여 합니다 `-Verbose` 하 고 `-Wait` 매개 변수에서의 진행률을 확인할 수 있습니다는 `Start-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6b081-144">By specifying the `-Verbose` and `-Wait` parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="6b081-145">이 예제에서는 노드 준수 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="6b081-146">합니다 `Verbose` 나타내는 출력을 **설정** 메서드 작업을 건너뛰었습니다.</span><span class="sxs-lookup"><span data-stu-id="6b081-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6b081-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6b081-147">See also</span></span>

- [<span data-ttu-id="6b081-148">Azure Automation DSC 개요</span><span class="sxs-lookup"><span data-stu-id="6b081-148">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="6b081-149">Setting up an SMB pull server(SMB 끌어오기 서버 설정)</span><span class="sxs-lookup"><span data-stu-id="6b081-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="6b081-150">Configuring a pull client(끌어오기 클라이언트 구성)</span><span class="sxs-lookup"><span data-stu-id="6b081-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
