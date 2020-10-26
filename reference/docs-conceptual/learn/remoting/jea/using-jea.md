---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: JEA 사용
description: 이 문서에서는 JEA 엔드포인트에 연결하고 사용할 수 있는 다양한 방법을 설명합니다.
ms.openlocfilehash: b3d81cc0aa76549c81136e5a1a5af28df9c6fa7a
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501544"
---
# <a name="using-jea"></a><span data-ttu-id="40fe0-104">JEA 사용</span><span class="sxs-lookup"><span data-stu-id="40fe0-104">Using JEA</span></span>

<span data-ttu-id="40fe0-105">이 문서에서는 JEA 엔드포인트에 연결하고 사용할 수 있는 다양한 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-105">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="40fe0-106">대화형으로 JEA 사용</span><span class="sxs-lookup"><span data-stu-id="40fe0-106">Using JEA interactively</span></span>

<span data-ttu-id="40fe0-107">JEA 구성을 테스트하거나 사용자를 위한 간단한 작업이 있는 경우, 일반적인 PowerShell 원격 세션과 동일한 방법으로 JEA를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-107">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="40fe0-108">복잡한 원격 작업의 경우 [암시적 원격](#using-jea-with-implicit-remoting)을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-108">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="40fe0-109">암시적 원격을 통해 사용자는 데이터 개체를 로컬에서 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-109">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="40fe0-110">대화형으로 JEA를 사용하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-110">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="40fe0-111">연결하는 컴퓨터의 이름(로컬 머신일 수 있음)</span><span class="sxs-lookup"><span data-stu-id="40fe0-111">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="40fe0-112">해당 컴퓨터에 등록된 JEA 엔드포인트의 이름</span><span class="sxs-lookup"><span data-stu-id="40fe0-112">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="40fe0-113">해당 컴퓨터의 JEA 엔드포인트에 액세스할 수 있는 자격 증명</span><span class="sxs-lookup"><span data-stu-id="40fe0-113">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="40fe0-114">해당 정보를 통해 [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) 또는 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet을 사용하여 JEA 세션을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-114">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="40fe0-115">현재 사용자 계정이 JEA 엔드포인트에 액세스할 수 있는 경우 **Credential** 매개 변수를 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-115">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="40fe0-116">PowerShell 프롬프트가 `[localhost]: PS>`로 변경되면 이제 원격 JEA 세션과 상호 작용하고 있음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-116">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="40fe0-117">`Get-Command`를 실행하여 사용할 수 있는 명령을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-117">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="40fe0-118">사용 가능한 매개 변수 또는 허용되는 매개 변수 값에 대한 제한이 있는지 알아보려면 관리자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="40fe0-118">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="40fe0-119">JEA 세션은 NoLanguage 모드로 작동된다는 것을 기억하세요.</span><span class="sxs-lookup"><span data-stu-id="40fe0-119">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="40fe0-120">일반적으로 PowerShell을 사용하는 방법 중 일부는 사용하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-120">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="40fe0-121">예를 들어 변수를 사용하여 데이터를 저장하거나 cmdlet에서 반환된 개체의 속성을 검사할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-121">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="40fe0-122">다음 예제에서는 동일한 명령을 NoLanguage 모드에서 작동하도록 하는 두 가지 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-122">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

```powershell
# Using variables is prohibited in NoLanguage mode. The following will not work:
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# You can also use parameter sets that don't require extra data to be passed in
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="40fe0-123">이 접근 방식을 어렵게 만드는 더 복잡한 명령 호출의 경우 [암시적 원격](#using-jea-with-implicit-remoting) 사용 또는 필요한 기능을 래핑하는 [사용자 지정 함수 만들기](role-capabilities.md#creating-custom-functions)를 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="40fe0-123">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="40fe0-124">암시적 원격을 통해 JEA 사용</span><span class="sxs-lookup"><span data-stu-id="40fe0-124">Using JEA with implicit remoting</span></span>

<span data-ttu-id="40fe0-125">PowerShell에는 원격 머신에서 프록시 cmdlet을 가져와 로컬 명령인 것처럼 상호 작용할 수 있는 암시적 원격 모델이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-125">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="40fe0-126">암시적 원격은 이 **Hey, Scripting Guy!** 에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-126">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="40fe0-127">[블로그 게시물](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="40fe0-127">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="40fe0-128">암시적 원격은 전체 언어 모드에서 JEA cmdlet으로 작업할 수 있게 해주므로 JEA 작업 시 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-128">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="40fe0-129">탭 완성, 변수, 개체 조작 및 로컬 스크립트를 사용하여 JEA 엔드포인트에 대한 작업을 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-129">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="40fe0-130">프록시 명령을 호출할 때마다 데이터는 원격 머신의 JEA 엔드포인트로 전송되어 거기서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-130">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="40fe0-131">암시적 원격은 기존 PowerShell 세션에서 cmdlet을 가져오는 방식으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-131">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="40fe0-132">필요에 따라 각 프록시 cmdlet의 명사에 선택한 문자열을 접두사로 붙일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-132">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="40fe0-133">이 접두사를 사용하면 원격 시스템에 대한 명령을 구별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-133">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="40fe0-134">모든 프록시 명령을 포함하는 임시 스크립트 모듈이 만들어지고 이를 로컬 PowerShell 세션 기간 동안 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-134">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="40fe0-135">기본 JEA cmdlet의 대한 제약 조건으로 인해 일부 시스템은 전체 JEA 세션을 가져오지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-135">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="40fe0-136">이 문제를 해결하려면 필요한 명령의 이름을 명시적으로 `-CommandName` 매개 변수에 제공하여 JEA 세션에서 필요한 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-136">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="40fe0-137">향후 업데이트에서 영향을 받는 시스템에서 전체 JEA 세션을 가져와 이 문제를 해결할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-137">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="40fe0-138">기본 매개 변수의 JEA 제약 조건으로 인해 JEA 세션을 가져올 수 없는 경우 아래 단계에 따라 가져온 집합에서 기본 명령을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-138">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="40fe0-139">`Select-Object`와 같은 명령을 계속 사용할 수 있지만, 원격 JEA 세션에서 가져온 로컬 버전 대신 컴퓨터에 설치된 로컬 버전을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-139">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

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

<span data-ttu-id="40fe0-140">[Export-PSSession](/powershell/module/microsoft.powershell.utility/Export-PSSession)을 사용하여 암시적 원격에서 프록시 설정된 cmdlet을 유지할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-140">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/module/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="40fe0-141">암시적 원격에 대한 자세한 내용은 [Import-PSSession](/powershell/module/microsoft.powershell.utility/import-pssession) 및 [Import-Module](/powershell/module/microsoft.powershell.core/import-module)에 대한 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40fe0-141">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/module/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/module/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="40fe0-142">프로그래밍 방식으로 JEA 사용</span><span class="sxs-lookup"><span data-stu-id="40fe0-142">Using JEA programmatically</span></span>

<span data-ttu-id="40fe0-143">사내 기술 지원팀 앱 및 웹 사이트와 같은 자동화 시스템 및 사용자 애플리케이션에서도 JEA를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-143">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="40fe0-144">이 접근 방식은 비제한 PowerShell 엔드포인트와 통신하는 앱을 빌드하는 방법과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-144">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="40fe0-145">프로그램이 JEA에 의해 적용된 제한 사항으로 작동하도록 설계되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-145">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="40fe0-146">간단한 일회성 작업의 경우 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command)를 사용하여 JEA 섹션에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-146">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="40fe0-147">JEA 세션에 연결할 때 사용할 수 있는 명령을 확인하려면 `Get-Command`를 실행하고 결과를 반복하여 허용되는 매개 변수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-147">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="40fe0-148">C# 앱을 빌드하는 경우 [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) 개체에 구성 이름을 지정하여 JEA 세션에 연결하는 PowerShell runspace를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-148">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
// See https://docs.microsoft.com/dotnet/api/system.management.automation.pscredential
var creds        = // create a PSCredential object here

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
    false,                 // Use SSL
    computerName,          // Computer name
    5985,                  // WSMan Port
    "/wsman",              // WSMan Path
                           // Connection URI with config name
    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),
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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="40fe0-149">JEA와 PowerShell Direct 함께 사용</span><span class="sxs-lookup"><span data-stu-id="40fe0-149">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="40fe0-150">Windows 10 및 Windows Server 2016의 Hyper-V는 가상 머신의 네트워크 구성 또는 원격 관리 설정에 관계없이 Hyper-V 관리자가 PowerShell을 사용하여 가상 머신을 관리할 수 있게 해주는 기능인 [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-150">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="40fe0-151">JEA와 함께 PowerShell Direct를 사용하여 Hyper-V 관리자에게 VM에 대한 제한된 액세스 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-151">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="40fe0-152">이는 VM에 대한 네트워크 연결이 끊어지고 네트워크 설정을 수정하기 위해 데이터 센터 관리자가 필요한 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-152">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="40fe0-153">PowerShell Direct에서 JEA를 사용하기 위한 추가 구성이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-153">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="40fe0-154">그러나 가상 머신 내에서 실행되는 게스트 운영 체제는 Windows 10, Windows Server 2016 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-154">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="40fe0-155">Hyper-V 관리자는 PSRemoting cmdlet에 대해 `-VMName` 또는 `-VMId` 매개 변수를 사용하여 JEA 엔드포인트에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-155">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="40fe0-156">Hyper-V 관리자가 사용할 수 있도록 시스템을 관리하는 데 필요한 최소 권한을 가진 전용 사용자 계정을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-156">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="40fe0-157">권한 없는 사용자도 비제한 PowerShell 사용을 포함하여 기본적으로 Windows 컴퓨터에 로그인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-157">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="40fe0-158">따라서 권한 없는 사용자가 파일 시스템을 탐색하여 OS 환경에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-158">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="40fe0-159">Hyper-V 관리자를 제한하고 JEA와 함께 PowerShell Direct를 사용하여 VM에만 액세스하도록 제한하려면 Hyper-V 관리자의 JEA 계정에 대한 로컬 로그온 권한을 거부해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40fe0-159">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
