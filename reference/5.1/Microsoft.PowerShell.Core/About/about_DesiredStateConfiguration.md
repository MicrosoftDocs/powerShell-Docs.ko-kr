---
description: PowerShell DSC (필요한 상태 구성) 기능에 대 한 간략 한 소개를 제공 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_desiredstateconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_DesiredStateConfiguration
ms.openlocfilehash: 5d088934ffc953ad19be401bce72f6287f0fde07
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387025"
---
# <a name="about_desiredstateconfiguration"></a><span data-ttu-id="238fa-104">about_DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="238fa-104">about_DesiredStateConfiguration</span></span>

## <a name="short-description"></a><span data-ttu-id="238fa-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="238fa-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="238fa-106">PowerShell DSC (필요한 상태 구성) 기능에 대 한 간략 한 소개를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-106">Provides a brief introduction to the PowerShell Desired State Configuration (DSC) feature.</span></span>

## <a name="long-description"></a><span data-ttu-id="238fa-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="238fa-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="238fa-108">DSC는 소프트웨어 서비스에 대 한 구성 데이터를 배포 및 관리 하 고 이러한 서비스가 실행 되는 환경을 관리할 수 있도록 하는 PowerShell의 관리 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-108">DSC is a management platform in PowerShell that enables deploying and managing configuration data for software services, and managing the environment in which these services run.</span></span>

<span data-ttu-id="238fa-109">DSC는 소프트웨어 환경의 상태를 구성 하는 방법을 선언적으로 지정 하는 데 사용할 수 있는 PowerShell 언어 확장, 새 cmdlet 및 리소스 집합을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-109">DSC provides a set of PowerShell language extensions, new cmdlets, and resources that you can use to declaratively specify how you want the state of your software environment to be configured.</span></span> <span data-ttu-id="238fa-110">또한 기존 구성을 유지하고 관리하는 수단을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-110">It also provides a means to maintain and manage existing configurations.</span></span>

<span data-ttu-id="238fa-111">DSC는 PowerShell 4.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-111">DSC is introduced in PowerShell 4.0.</span></span>

<span data-ttu-id="238fa-112">DSC에 대 한 자세한 내용은 [PowerShell 필요한 상태 구성 개요](/powershell/scripting/dsc/overview/overview)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="238fa-112">For detailed information about DSC, see [PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/overview).</span></span>

## <a name="developing-dsc-resources-with-classes"></a><span data-ttu-id="238fa-113">클래스를 사용 하 여 DSC 리소스 개발</span><span class="sxs-lookup"><span data-stu-id="238fa-113">DEVELOPING DSC RESOURCES WITH CLASSES</span></span>

<span data-ttu-id="238fa-114">PowerShell 5.0부터 클래스를 사용 하 여 DSC 리소스를 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-114">Starting in PowerShell 5.0, you can develop DSC resources by using classes.</span></span>
<span data-ttu-id="238fa-115">자세한 내용은 [about_Classes](about_Classes.md)및 [PowerShell 클래스를 사용 하 여 사용자 지정 DSC 리소스 작성](/powershell/scripting/dsc/resources/authoringresourceclass)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="238fa-115">For more information, see [about_Classes](about_Classes.md), and [Writing a custom DSC resource with PowerShell classes](/powershell/scripting/dsc/resources/authoringresourceclass).</span></span>

## <a name="using-dsc"></a><span data-ttu-id="238fa-116">DSC 사용</span><span class="sxs-lookup"><span data-stu-id="238fa-116">USING DSC</span></span>

<span data-ttu-id="238fa-117">DSC를 사용 하 여 환경을 구성 하려면 먼저 구성 키워드를 사용 하 여 PowerShell 스크립트 블록을 정의 하 고 그 뒤에 식별자를 사용 하 여 블록을 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-117">To use DSC to configure your environment, first define a PowerShell script block using the Configuration keyword, followed by an identifier, which is in turn followed by the pair of curly braces delimiting the block.</span></span> <span data-ttu-id="238fa-118">구성 블록 내에서 환경의 각 노드 (컴퓨터)에 대해 원하는 구성 상태를 지정 하는 노드 블록을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-118">Inside the configuration block you can define node blocks that specify the desired configuration state for each node (computer) in the environment.</span></span> <span data-ttu-id="238fa-119">노드 블록은 Node 키워드를 사용 하 여 시작 하 고, 대상 컴퓨터의 이름은 변수가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-119">A node block starts with the Node keyword, followed by the name of the target computer, which can be a variable.</span></span> <span data-ttu-id="238fa-120">컴퓨터 이름 뒤에는 노드 블록을 구분 하는 중괄호가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-120">After the computer name, come the curly braces that delimit the node block.</span></span> <span data-ttu-id="238fa-121">노드 블록 내에서 리소스 블록을 정의 하 여 특정 리소스를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-121">Inside the node block, you can define resource blocks to configure specific resources.</span></span> <span data-ttu-id="238fa-122">리소스 블록은 리소스의 형식 이름으로 시작 하 여 다음 예제에 표시 된 것 처럼 블록을 구분 하는 중괄호 뒤에 해당 블록에 대해 지정 하려는 식별자가 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-122">A resource block starts with the type name of the resource, followed by the identifier you want to specify for that block, followed by the curly braces that delimit the block, as shown in the following example.</span></span>

```powershell
Configuration MyWebConfig {
    # Parameters are optional
    param ($MachineName, $WebsiteFilePath)
    # A Configuration block can have one or more Node blocks
    Node $MachineName
    {
        # Next, specify one or more resource blocks
        # WindowsFeature is one of the resources you can use in a Node block
        # This example ensures the Web Server (IIS) role is installed
        WindowsFeature IIS
        {
            # To ensure that the role is not installed, set Ensure to "Absent"
            Ensure = "Present"
            Name = "Web-Server" # Use the Name property from Get-WindowsFeature
        }

        # You can use the File resource to create files and folders
        # "WebDirectory" is the name you want to use to refer to this instance
        File WebDirectory
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File"
            Recurse = $true
            SourcePath = $WebsiteFilePath
            DestinationPath = "C:\inetpub\wwwroot"

            # Ensure that the IIS block is successfully run first before
            # configuring this resource
            DependsOn = "[WindowsFeature]IIS"  # Use for dependencies
        }
    }
}
```

<span data-ttu-id="238fa-123">구성을 만들려면 PowerShell 함수를 호출 하는 것과 동일한 방식으로 구성 블록을 호출 합니다 .이 함수는 정의 된 것으로 예상 되는 매개 변수를 전달 합니다 (위 예제에서는 2 개).</span><span class="sxs-lookup"><span data-stu-id="238fa-123">To create a configuration, invoke the Configuration block the same way you would invoke a PowerShell function, passing in any expected parameters you may have defined (two in the example above).</span></span> <span data-ttu-id="238fa-124">예를 들어,이 경우는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-124">For example, in this case:</span></span>

```powershell
MyWebConfig -MachineName "TestMachine" -WebsiteFilePath `
  "\\filesrv\WebFiles" -OutputPath "C:\Windows\system32\temp"
# OutputPath is optional
```

<span data-ttu-id="238fa-125">그러면 지정 된 경로에 노드당 MOF 파일이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-125">This generates a MOF file per node at the path you specify.</span></span> <span data-ttu-id="238fa-126">이러한 MOF 파일은 각 노드에 대해 원하는 구성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-126">These MOF files specify the desired configuration for each node.</span></span> <span data-ttu-id="238fa-127">그런 다음, 다음 cmdlet을 사용 하 여 구성 MOF 파일을 구문 분석 하 고 각 노드를 해당 구성으로 보내고 이러한 구성을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-127">Next, use the following cmdlet to parse the configuration MOF files, send each node its corresponding configuration, and enact those configurations.</span></span> <span data-ttu-id="238fa-128">클래스 기반 DSC 리소스에 대 한 별도의 MOF 파일을 만들 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-128">Note that you do not need to create a separate MOF file for class-based DSC resources.</span></span>

```powershell
Start-DscConfiguration -Verbose -Wait -Path "C:\Windows\system32\temp"
```

## <a name="using-dsc-to-maintain-configuration-state"></a><span data-ttu-id="238fa-129">DSC를 사용 하 여 구성 상태 유지 관리</span><span class="sxs-lookup"><span data-stu-id="238fa-129">USING DSC TO MAINTAIN CONFIGURATION STATE</span></span>

<span data-ttu-id="238fa-130">DSC를 사용 하면 구성이 idempotent 됩니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-130">With DSC, configuration is idempotent.</span></span> <span data-ttu-id="238fa-131">즉, DSC를 사용 하 여 동일한 구성을 두 번 이상 시행 하는 경우 결과 구성 상태는 항상 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-131">This means that if you use DSC to enact the same configuration more than once, the resulting configuration state will always be the same.</span></span> <span data-ttu-id="238fa-132">따라서 환경의 모든 노드가 원하는 구성 상태에서 데이터베이스가 드리프트 수 있는 것으로 의심 되는 경우 동일한 DSC 구성을 다시 설정 하 여 다시 원하는 상태로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-132">Because of this, if you suspect that any nodes in your environment may have drifted from the desired state of configuration, you can enact the same DSC configuration again to bring them back to the desired state.</span></span> <span data-ttu-id="238fa-133">상태가 원하는 상태에서 데이터베이스가 드리프트 된 리소스만 처리 하도록 구성 스크립트를 수정할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-133">You do not need to modify the configuration script to address only those resources whose state has drifted from the desired state.</span></span>

<span data-ttu-id="238fa-134">다음 예에서는 지정 된 노드에 대 한 실제 구성 상태가 노드의 마지막 DSC 구성에서 데이터베이스가 드리프트 여부를 확인 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-134">The following example shows how you can verify whether the actual state of configuration on a given node has drifted from the last DSC configuration enacted on the node.</span></span> <span data-ttu-id="238fa-135">이 예제에서는 로컬 컴퓨터의 구성을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-135">In this example we are checking the configuration of the local computer.</span></span>

```powershell
$session = New-CimSession -ComputerName "localhost"
Test-DscConfiguration -CimSession $session
```

## <a name="built-in-dsc-resources"></a><span data-ttu-id="238fa-136">기본 제공 DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="238fa-136">BUILT-IN DSC RESOURCES</span></span>

<span data-ttu-id="238fa-137">구성 스크립트에서 다음과 같은 기본 제공 리소스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-137">You can use the following built-in resources in your configuration scripts:</span></span>

|<span data-ttu-id="238fa-138">name</span><span class="sxs-lookup"><span data-stu-id="238fa-138">Name</span></span>                  |<span data-ttu-id="238fa-139">속성</span><span class="sxs-lookup"><span data-stu-id="238fa-139">Properties</span></span>                                         |
|----------------------|---------------------------------------------------|
|<span data-ttu-id="238fa-140">파일</span><span class="sxs-lookup"><span data-stu-id="238fa-140">File</span></span>                  |<span data-ttu-id="238fa-141">{DestinationPath, Attributes, Checksum, Content ...}</span><span class="sxs-lookup"><span data-stu-id="238fa-141">{DestinationPath, Attributes, Checksum, Content...}</span></span>|
|<span data-ttu-id="238fa-142">보관</span><span class="sxs-lookup"><span data-stu-id="238fa-142">Archive</span></span>               |<span data-ttu-id="238fa-143">{Destination, Path, Checksum, Credential ...}</span><span class="sxs-lookup"><span data-stu-id="238fa-143">{Destination, Path, Checksum, Credential...}</span></span>       |
|<span data-ttu-id="238fa-144">Environment</span><span class="sxs-lookup"><span data-stu-id="238fa-144">Environment</span></span>           |<span data-ttu-id="238fa-145">{Name, DependsOn, 확인, 경로 ...}</span><span class="sxs-lookup"><span data-stu-id="238fa-145">{Name, DependsOn, Ensure, Path...}</span></span>                 |
|<span data-ttu-id="238fa-146">그룹</span><span class="sxs-lookup"><span data-stu-id="238fa-146">Group</span></span>                 |<span data-ttu-id="238fa-147">{GroupName, Credential, DependsOn, Description ...}</span><span class="sxs-lookup"><span data-stu-id="238fa-147">{GroupName, Credential, DependsOn, Description...}</span></span> |
|<span data-ttu-id="238fa-148">로그</span><span class="sxs-lookup"><span data-stu-id="238fa-148">Log</span></span>                   |<span data-ttu-id="238fa-149">{Message, DependsOn, PsDscRunAsCredential}</span><span class="sxs-lookup"><span data-stu-id="238fa-149">{Message, DependsOn, PsDscRunAsCredential}</span></span>         |
|<span data-ttu-id="238fa-150">패키지</span><span class="sxs-lookup"><span data-stu-id="238fa-150">Package</span></span>               |<span data-ttu-id="238fa-151">{Name, Path, ProductId, Arguments ...}</span><span class="sxs-lookup"><span data-stu-id="238fa-151">{Name, Path, ProductId, Arguments...}</span></span>              |
|<span data-ttu-id="238fa-152">레지스트리</span><span class="sxs-lookup"><span data-stu-id="238fa-152">Registry</span></span>              |<span data-ttu-id="238fa-153">{Key, ValueName, DependsOn, 확인 ...}</span><span class="sxs-lookup"><span data-stu-id="238fa-153">{Key, ValueName, DependsOn, Ensure...}</span></span>             |
|<span data-ttu-id="238fa-154">스크립트</span><span class="sxs-lookup"><span data-stu-id="238fa-154">Script</span></span>                |<span data-ttu-id="238fa-155">{GetScript, SetScript, TestScript, Credential ...}</span><span class="sxs-lookup"><span data-stu-id="238fa-155">{GetScript, SetScript, TestScript, Credential...}</span></span>  |
|<span data-ttu-id="238fa-156">서비스</span><span class="sxs-lookup"><span data-stu-id="238fa-156">Service</span></span>               |<span data-ttu-id="238fa-157">{Name, 속성과 builtinaccount, Credential, 종속성 ...}</span><span class="sxs-lookup"><span data-stu-id="238fa-157">{Name, BuiltInAccount, Credential, Dependencies...}</span></span>|
|<span data-ttu-id="238fa-158">사용자</span><span class="sxs-lookup"><span data-stu-id="238fa-158">User</span></span>                  |<span data-ttu-id="238fa-159">{UserName, DependsOn, Description, Disabled ...}</span><span class="sxs-lookup"><span data-stu-id="238fa-159">{UserName, DependsOn, Description, Disabled...}</span></span>    |
|<span data-ttu-id="238fa-160">WaitForAll</span><span class="sxs-lookup"><span data-stu-id="238fa-160">WaitForAll</span></span>            |<span data-ttu-id="238fa-161">{NodeName, Context.resourcename, DependsOn, PsDscRunAsC ...}</span><span class="sxs-lookup"><span data-stu-id="238fa-161">{NodeName, ResourceName, DependsOn, PsDscRunAsC...}</span></span>|
|<span data-ttu-id="238fa-162">WaitForAny</span><span class="sxs-lookup"><span data-stu-id="238fa-162">WaitForAny</span></span>            |<span data-ttu-id="238fa-163">{NodeName, Context.resourcename, DependsOn, PsDscRunAsC ...}</span><span class="sxs-lookup"><span data-stu-id="238fa-163">{NodeName, ResourceName, DependsOn, PsDscRunAsC...}</span></span>|
|<span data-ttu-id="238fa-164">WaitForSome</span><span class="sxs-lookup"><span data-stu-id="238fa-164">WaitForSome</span></span>           |<span data-ttu-id="238fa-165">{NodeCount, NodeName, Context.resourcename, DependsOn ...}</span><span class="sxs-lookup"><span data-stu-id="238fa-165">{NodeCount, NodeName, ResourceName, DependsOn...}</span></span>  |
|<span data-ttu-id="238fa-166">WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="238fa-166">WindowsFeature</span></span>        |<span data-ttu-id="238fa-167">{Name, Credential, DependsOn, 확인 ...}</span><span class="sxs-lookup"><span data-stu-id="238fa-167">{Name, Credential, DependsOn, Ensure...}</span></span>           |
|<span data-ttu-id="238fa-168">WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="238fa-168">WindowsOptionalFeature</span></span>|<span data-ttu-id="238fa-169">{Name, DependsOn, 확인, LogLevel ...}</span><span class="sxs-lookup"><span data-stu-id="238fa-169">{Name, DependsOn, Ensure, LogLevel...}</span></span>             |
|<span data-ttu-id="238fa-170">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="238fa-170">WindowsProcess</span></span>        |<span data-ttu-id="238fa-171">{Arguments, Path, Credential, DependsOn ...}</span><span class="sxs-lookup"><span data-stu-id="238fa-171">{Arguments, Path, Credential, DependsOn...}</span></span>        |

<span data-ttu-id="238fa-172">시스템에서 사용할 수 있는 DSC 리소스 목록을 가져오려면 cmdlet을 실행 `Get-DscResource` 합니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-172">To get a list of available DSC resources on your system, run the `Get-DscResource` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="238fa-173">7\.0 이전 PowerShell 버전에서 `Get-DscResource`는 클래스 기반 DSC 리소스를 찾지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-173">In PowerShell versions below 7.0, `Get-DscResource` does not find Class based DSC resources.</span></span>

<span data-ttu-id="238fa-174">이 항목의 예제에서는 파일 및 Add-windowsfeature 리소스를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-174">The example in this topic demonstrates how to use the File and WindowsFeature resources.</span></span> <span data-ttu-id="238fa-175">리소스에 사용할 수 있는 모든 속성을 보려면 PowerShell ISE의 구성 스크립트 내에서 리소스 키워드 (예: 파일)에 커서를 삽입 하 고 <kbd>ctrl</kbd> + <kbd>스페이스바</kbd> 를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-175">To see all properties that you can use with a resource, insert the cursor in the resource keyword (for example, File) within your configuration script in PowerShell ISE, hold down <kbd>CTRL</kbd>+<kbd>SPACEBAR</kbd></span></span>

## <a name="find-more-resources"></a><span data-ttu-id="238fa-176">추가 리소스 찾기</span><span class="sxs-lookup"><span data-stu-id="238fa-176">FIND MORE RESOURCES</span></span>

<span data-ttu-id="238fa-177">PowerShell 및 DSC 사용자 커뮤니티 및 Microsoft에서 만든 다른 많은 DSC 리소스를 다운로드 하 여 설치 하 고 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="238fa-177">You can download, install, and learn about many other available DSC resources that have been created by the PowerShell and DSC user community, and by Microsoft.</span></span> <span data-ttu-id="238fa-178">[PowerShell 갤러리](https://www.powershellgallery.com/) 를 방문 하 여 사용 가능한 DSC 리소스를 찾아보고 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="238fa-178">Visit the [PowerShell Gallery](https://www.powershellgallery.com/) to browse and learn about available DSC resources.</span></span>

## <a name="see-also"></a><span data-ttu-id="238fa-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="238fa-179">SEE ALSO</span></span>

[<span data-ttu-id="238fa-180">PowerShell 필요한 상태 구성 개요</span><span class="sxs-lookup"><span data-stu-id="238fa-180">PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="238fa-181">기본 제공 PowerShell 필요한 상태 구성 리소스</span><span class="sxs-lookup"><span data-stu-id="238fa-181">Built-In PowerShell Desired State Configuration Resources</span></span>](/powershell/scripting/dsc/resources/resources)

[<span data-ttu-id="238fa-182">사용자 지정 PowerShell 필요한 상태 구성 리소스 빌드</span><span class="sxs-lookup"><span data-stu-id="238fa-182">Build Custom PowerShell Desired State Configuration Resources</span></span>](/powershell/scripting/dsc/resources/authoringResource)
