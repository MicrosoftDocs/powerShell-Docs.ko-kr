---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: JEA 사용
ms.openlocfilehash: fa3d3a3c8bc0090ec9ad788585ec5df933134173
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084048"
---
# <a name="using-jea"></a><span data-ttu-id="9171f-103">JEA 사용</span><span class="sxs-lookup"><span data-stu-id="9171f-103">Using JEA</span></span>

> <span data-ttu-id="9171f-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="9171f-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="9171f-105">이 항목에서는 JEA 엔드포인트에 연결하고 JEA 엔드포인트를 사용할 수 있는 다양한 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-105">This topic describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="9171f-106">대화형으로 JEA 사용</span><span class="sxs-lookup"><span data-stu-id="9171f-106">Using JEA interactively</span></span>

<span data-ttu-id="9171f-107">JEA 구성을 테스트하거나 사용자가 수행할 작업이 간단한 경우 일반적인 PowerShell 원격 세션과 같은 방법으로 JEA를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-107">If you are testing your JEA configuration or have simple tasks for users to perform, you can use JEA the same way you would a regular PowerShell remoting session.</span></span>
<span data-ttu-id="9171f-108">복잡한 원격 작업의 경우 대신 [암시적 원격](#using-jea-with-implicit-remoting)을 사용하여 사용자가 로컬에서 데이터 개체를 작동할 수 있도록 함으로써 사용자가 더 쉽게 작업할 수 있게 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-108">For complex remoting tasks, it is recommended to use [implicit remoting](#using-jea-with-implicit-remoting) instead to make it easier for your users by allowing users to operate with the data objects locally.</span></span>

<span data-ttu-id="9171f-109">대화형으로 JEA를 사용하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-109">To use JEA interactively, you will need:</span></span>
- <span data-ttu-id="9171f-110">연결하는 컴퓨터의 이름(로컬 컴퓨터일 수 있음)</span><span class="sxs-lookup"><span data-stu-id="9171f-110">The name of the computer you are connecting to (can be the local machine)</span></span>
- <span data-ttu-id="9171f-111">해당 컴퓨터에 등록된 JEA 엔드포인트의 이름</span><span class="sxs-lookup"><span data-stu-id="9171f-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="9171f-112">JEA 엔드포인트에 대한 액세스 권한이 있는 컴퓨터의 자격 증명</span><span class="sxs-lookup"><span data-stu-id="9171f-112">Credentials for the computer that have access to the JEA endpoint</span></span>

<span data-ttu-id="9171f-113">해당 정보를 가지고 [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) 또는 [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession)을 사용하여 JEA 세션을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-113">With that information in hand, you can start a JEA session using [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="9171f-114">현재 로그인한 계정에 JEA 엔드포인트에 대한 액세스 권한이 있는 경우 `-Credential` 매개 변수를 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-114">If the account you're currently logged in as has access to the JEA endpoint, you can omit the `-Credential` parameter.</span></span>

<span data-ttu-id="9171f-115">PowerShell 프롬프트가 `[localhost]: PS>`로 변경되면 이제 원격 JEA 세션과 상호 작용하다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-115">When the PowerShell prompt changes to `[localhost]: PS>` you will know that you are now interacting with the remote JEA session.</span></span>
<span data-ttu-id="9171f-116">`Get-Command`를 실행하여 사용할 수 있는 명령을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-116">You can run `Get-Command` to check which commands are available.</span></span>
<span data-ttu-id="9171f-117">관리자에게 사용할 수 있는 매개 변수 또는 허용되는 매개 변수 값에 대한 제한이 있는지를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-117">You will need to consult with your administrator to learn if there are any restrictions on the available parameters or allowable parameter values.</span></span>

<span data-ttu-id="9171f-118">참고로, JEA 세션은 NoLanguage 모드에서 작동하므로 일반적으로 PowerShell을 사용하는 방법 중 일부를 사용하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-118">As a reminder, JEA sessions operate in NoLanguage mode, so some of the ways you typically use PowerShell may not be available.</span></span>
<span data-ttu-id="9171f-119">예를 들어 변수를 사용하여 데이터를 저장하거나 cmdlet에서 반환된 개체의 속성을 검사할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-119">For instance, you cannot use variables to store data or inspect the properties on objects returned from cmdlets.</span></span>
<span data-ttu-id="9171f-120">아래의 예제는 현재 PowerShell을 사용할 수 있는 방법의 예와 같은 명령을 NoLanguage 모드에서 작동하도록 하는 두 가지 접근 방식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-120">The below example shows an example of how you may be using PowerShell today, and two approaches to get the same command working in NoLanguage mode.</span></span>

```powershell
# Using variables in NoLanguage mode is disallowed, so the following will not work
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# Better yet, use parameter sets that don't require extra data to be passed in when possible
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="9171f-121">이 접근 방식을 어렵게 만드는 더 복잡한 명령 호출의 경우 [암시적 원격](#using-jea-with-implicit-remoting) 사용 또는 원하는 기능을 래핑하는 [사용자 지정 함수 만들기](role-capabilities.md#creating-custom-functions)를 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="9171f-121">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you desire.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="9171f-122">암시적 원격을 통해 JEA 사용</span><span class="sxs-lookup"><span data-stu-id="9171f-122">Using JEA with implicit remoting</span></span>

<span data-ttu-id="9171f-123">PowerShell은 로컬 컴퓨터에서 원격 컴퓨터의 프록시 cmdlet을 가져와 로컬 명령인 것처럼 상호 작용할 수 있는 대체 원격 모델을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-123">PowerShell supports an alternative remoting model where you can import proxy cmdlets from a remote machine on your local computer and interact with them as if they were local commands.</span></span>
<span data-ttu-id="9171f-124">이를 암시적 원격이라고 하며, 이 내용은 [이 *Hey, Scripting Guy!* 블로그 게시물](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/)에 잘 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-124">This is called implicit remoting, and is explained well in [this *Hey, Scripting Guy!* blog post](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="9171f-125">암시적 원격은 전체 언어 모드에서 JEA cmdlet으로 작업할 수 있게 해주므로 JEA 작업 시 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-125">Implicit remoting is particularly useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span>
<span data-ttu-id="9171f-126">즉, Tab 키 완성 기능과 변수를 사용하고 개체를 조작할 수 있으며 로컬 스크립트를 사용하여 JEA 엔드포인트에 대해 더 쉽게 자동화할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-126">This means you can use tab completion, variables, manipulate objects, and even use local scripts to more easily automate against a JEA endpoint.</span></span>
<span data-ttu-id="9171f-127">프록시 명령을 호출할 때마다 데이터는 원격 컴퓨터의 JEA 엔드포인트로 전송되어 거기서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-127">Anytime you invoke a proxy command, the data will be sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="9171f-128">암시적 원격은 기존 PowerShell 세션에서 cmdlet을 가져오는 방식으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-128">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span>
<span data-ttu-id="9171f-129">필요에 따라 원격 시스템에 대한 명령을 구분하기 위해 각 프록시 cmdlet의 명사에 원하는 문자열을 접두사로 붙일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-129">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing to distinguish which commands are for the remote system.</span></span>
<span data-ttu-id="9171f-130">모든 프록시 명령을 포함하는 임시 스크립트 모듈이 만들어지고 이를 로컬 PowerShell 세션 기간 동안 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-130">A temporary script module containing all of the proxy commands will be created and can be used for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="9171f-131">기본 JEA cmdlet의 대한 제약 조건으로 인해 일부 시스템은 전체 JEA 세션을 가져오지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-131">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span>
> <span data-ttu-id="9171f-132">이 문제를 해결하려면 필요한 명령의 이름을 명시적으로 `-CommandName` 매개 변수에 제공하여 JEA 세션에서 필요한 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-132">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span>
> <span data-ttu-id="9171f-133">향후 업데이트에서 영향을 받는 시스템에서 전체 JEA 세션을 가져와 이 문제를 해결할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-133">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="9171f-134">기본 JEA 매개 변수에 대한 제약 조건으로 인해 JEA 세션을 가져올 수 없는 경우 아래 단계에 따라 가져온 집합에서 기본 명령을 필터링해 제외할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-134">If you are unable to import a JEA session due to constraints on the default JEA parameters, you can follow the steps below to filter out the default commands from the imported set.</span></span>
<span data-ttu-id="9171f-135">여전히 `Select-Object`와 같은 명령을 사용할 수 있습니다. JEA 세션의 원격 버전 대신 컴퓨터에 설치된 로컬 버전을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-135">You will still be able to use commands like `Select-Object` -- you'll just use the local version installed on your computer instead of the remote one in the JEA session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Get a list of all the commands on the JEA endpoint
$commands = Invoke-Command -Session $jeasession -ScriptBlock { Get-Command }

# Filter out the default cmdlets
$jeaDefaultCmdlets = 'Clear-Host', 'Exit-PSSession', 'Get-Command', 'Get-FormatData', 'Get-Help', 'Measure-Object', 'Out-Default', 'Select-Object'
$filteredCommands = $commands.Name | Where-Object { $jeaDefaultCmdlets -notcontains $_ }

# Import only commands explicitly added in role capabilities and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA' -CommandName $filteredCommands
```

<span data-ttu-id="9171f-136">[Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession)을 사용하여 암시적 원격에서 프록시 설정된 cmdlet을 유지할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-136">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="9171f-137">암시적 원격에 대한 자세한 내용은 [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) 및 [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module)에 대한 도움말 문서를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="9171f-137">For more information about implicit remoting, check out the help documentation for [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) and [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="9171f-138">프로그래밍 방식으로 JEA 사용</span><span class="sxs-lookup"><span data-stu-id="9171f-138">Using JEA programmatically</span></span>

<span data-ttu-id="9171f-139">사내 기술 지원팀 앱 및 웹 사이트와 같은 자동화 시스템 및 사용자 애플리케이션에서 JEA를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-139">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and web sites.</span></span>
<span data-ttu-id="9171f-140">접근 방식은 비제한 PowerShell 엔드포인트와 통신하는 앱을 빌드하는 것과 같지만, 프로그램이 JEA가 원격 세션에서 실행될 수 있는 명령을 제한하고 있음을 인식해야 한다는 주의 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-140">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints, with the caveat that the program should be aware that JEA is limiting the commands that can be run in the remote session.</span></span>

<span data-ttu-id="9171f-141">간단한 일회성 작업의 경우 [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command)를 사용하여 JEA를 사용하는 명령 집합을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-141">For simple, one-off tasks, you can use [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) to run a set of commands using JEA.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="9171f-142">JEA 세션에 연결할 때 사용할 수 있는 명령을 확인하려면 `Get-Command`를 실행하고 결과를 반복하여 허용되는 매개 변수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-142">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="9171f-143">C# 앱을 빌드하는 경우 [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) 개체에 구성 이름을 지정하여 JEA 세션에 연결하는 PowerShell runspace를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-143">If you are building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) object.</span></span>

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/library/system.management.automation.pscredential(v=vs.85).aspx)

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
                    false,                 // Use SSL
                    computerName,          // Computer name
                    5985,                  // WSMan Port
                    "/wsman",              // WSMan Path
                    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),  // Connection URI with config name
                    creds);                // Credentials
// Now, use the connection info to create a runspace where you can run the commands
using (Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo))
{
    // Open the runspace
    runspace.Open();

    using (PowerShell ps = PowerShell.Create())
    {
        // Set the PowerShell object to use the JEA runspace
        ps.Runspace = runspace;

        // Now you can add and invoke commands
        ps.AddCommand("Get-Command");
        foreach (var result in ps.Invoke())
        {
            Console.WriteLine(result);
        }
    }

    // Close the runspace
    runspace.Close();
}
```

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="9171f-144">JEA와 PowerShell Direct 함께 사용</span><span class="sxs-lookup"><span data-stu-id="9171f-144">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="9171f-145">Windows 10 및 Windows Server 2016의 Hyper-V는 가상 컴퓨터의 네트워크 구성 또는 원격 관리 설정에 관계없이 Hyper-V 관리자가 PowerShell을 사용하여 가상 컴퓨터를 관리할 수 있게 해주는 기능인 [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-145">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), a feature which allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="9171f-146">PowerShell Direct와 JEA를 함께 사용하여 Hyper-V 관리자에게 VM에 대한 제한된 액세스 권한을 부여할 수 있습니다. 이는 VM에 대한 네트워크 연결이 끊어진 상태에서 데이터 센터 관리자가 네트워크 설정을 수정해야 할 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-146">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM, which can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="9171f-147">PowerShell Direct를 통해 JEA를 사용하는 데 필요한 추가 구성은 없지만, 가상 컴퓨터 내부에서 실행되는 운영 체제는 Windows 10 또는 Windows Server 2016이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-147">No additional configuration is required to use JEA over PowerShell Direct, however the operating system running inside the virtual machine must be Windows 10 or Windows Server 2016.</span></span>
<span data-ttu-id="9171f-148">Hyper-V 관리자는 PSRemoting cmdlet에 대해 `-VMName` 또는 `-VMId` 매개 변수를 사용하여 JEA 엔드포인트에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-148">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="9171f-149">Hyper-V 관리자가 사용하여 시스템을 관리하는 권한 이외의 권한은 없는 전용 로컬 사용자를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-149">It is strongly recommended that you create a dedicated local user with no other rights to manage the system for your Hyper-V administrators to use.</span></span>
<span data-ttu-id="9171f-150">권한 없는 사용자도 비제한 PowerShell을 사용하는 등 기본적으로 Windows 컴퓨터에는 여전히 로그인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-150">Remember that even an unprivileged user can still log into a Windows machine by default, including using unconstrained PowerShell.</span></span>
<span data-ttu-id="9171f-151">따라서 권한 없는 사용자가 파일 시스템 일부를 탐색하여 OS 환경에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-151">That will allow them to browse (some of) the file system and learn more about your OS environment.</span></span>
<span data-ttu-id="9171f-152">Hyper-V 관리자가 PowerShell Direct와 JEA를 사용하여 VM에 액세스만 할 수 있도록 하려면 Hyper-V 관리자의 JEA 계정에 대한 로컬 로그온 권한을 거부해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9171f-152">To lock down a Hyper-V administrator to only access a VM using PowerShell Direct with JEA, you will need to deny local logon rights to the Hyper-V admin's JEA account.</span></span>
