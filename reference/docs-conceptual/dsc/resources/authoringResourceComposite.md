---
ms.date: 07/08/2020
keywords: dsc,powershell,configuration,setup
title: 복합 리소스 - DSC 구성을 리소스로 사용
description: 이 문서에서는 복합 리소스를 만들고 삭제하는 방법을 설명합니다.
ms.openlocfilehash: c1f0e3b45c3a393c04700b5a4bc88be365794820
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667303"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="8f705-104">복합 리소스: DSC 구성을 자원으로 사용</span><span class="sxs-lookup"><span data-stu-id="8f705-104">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="8f705-105">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8f705-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="8f705-106">실제 상황에서, 구성은 다양 한 리소스를 호출하고 무수한 속성을 설정하므로 길고 복잡해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-106">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="8f705-107">이러한 복잡성을 해결하는 데 도움이 되도록 Windows PowerShell DSC(필요한 상태 구성) 구성을 다른 구성에 대한 리소스로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-107">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="8f705-108">이것을 복합 리소스라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-108">This is called a composite resource.</span></span> <span data-ttu-id="8f705-109">복합 리소스는 매개 변수를 사용하는 DSC 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-109">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="8f705-110">구성의 매개 변수는 리소스의 속성으로서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-110">The parameters of the configuration act as the properties of the resource.</span></span>
<span data-ttu-id="8f705-111">구성은 `.schema.psm1` 확장을 사용하여 파일로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-111">The configuration is saved as a file with a `.schema.psm1` extension.</span></span> <span data-ttu-id="8f705-112">MOF 스키마와 일반적인 DSC 리소스의 리소스 스크립트를 모두 대신합니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-112">It takes the place of both the MOF schema, and the resource script in a typical DSC resource.</span></span> <span data-ttu-id="8f705-113">DSC 리소스에 대한 자세한 내용은 [Windows PowerShell 필요한 상태 구성 리소스](resources.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8f705-113">For more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="8f705-114">복합 리소스 만들기</span><span class="sxs-lookup"><span data-stu-id="8f705-114">Creating the composite resource</span></span>

<span data-ttu-id="8f705-115">이 예제에서는 다양한 기존 리소스를 호출하여 가상 컴퓨터를 구성하는 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-115">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="8f705-116">구성 블록에서 설정되는 값을 지정하는 대신 구성에서는 매개 변수를 가져와서 구성 블록에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-116">Instead of specifying the values to be set in configuration blocks, the configuration takes in parameters that are then used in the configuration blocks.</span></span>

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Create VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="8f705-117">DSC는 현재, 복합 리소스 내에서 복합 리소스 또는 중첩된 구성을 배치하도록 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-117">DSC doesn't currently support placing composite resources or nested configurations within a composite resource.</span></span>

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="8f705-118">구성을 복합 리소스로서 저장</span><span class="sxs-lookup"><span data-stu-id="8f705-118">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="8f705-119">매개 변수가 있는 구성을 DSC 리소스로 사용하려면, 이 구성을 다른 MOF 기반 리소스의 디렉터리 구조과 같은 디렉터리 구조에 저장하고 이름을 `.schema.psm1` 확장으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-119">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a `.schema.psm1` extension.</span></span> <span data-ttu-id="8f705-120">이 예에서는 파일 이름을 `xVirtualMachine.schema.psm1`로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-120">For this example, we'll name the file `xVirtualMachine.schema.psm1`.</span></span> <span data-ttu-id="8f705-121">다음 줄을 포함하는 `xVirtualMachine.psd1`이라는 매니페스트도 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-121">You also need to create a manifest named `xVirtualMachine.psd1` that contains the following line.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

> [!NOTE]
> <span data-ttu-id="8f705-122">`MyDscResources.psd1` 외에 `MyDscResources` 폴더 아래의 모든 리소스에 대한 모듈 매니페스트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-122">This is in addition to `MyDscResources.psd1`, the module manifest for all resources under the `MyDscResources` folder.</span></span>

<span data-ttu-id="8f705-123">완료되면 폴더 구조는 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-123">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
        |- MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="8f705-124">이제 리소스는 `Get-DscResource` cmdlet을 사용하여 검색할 수 있으며, 해당 속성은 해당 cmdlet이나, Windows PowerShell ISE에서 <kbd>Ctrl</kbd>+<kbd>Space</kbd> 자동 완성을 사용하여 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-124">The resource is now discoverable by using the `Get-DscResource` cmdlet, and its properties are discoverable by either that cmdlet or by using <kbd>Ctrl</kbd>+<kbd>Space</kbd> autocomplete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="8f705-125">복합 리소스 사용</span><span class="sxs-lookup"><span data-stu-id="8f705-125">Using the composite resource</span></span>

<span data-ttu-id="8f705-126">다음으로 복합 리소스를 호출하는 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-126">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="8f705-127">이 구성은 xVirtualMachine 복합 리소스를 호출하여 가상 컴퓨터를 만든 다음, **xComputer** 리소스를 호출하여 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-127">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

```powershell
configuration RenameVM
{
    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

<span data-ttu-id="8f705-128">또한 이 리소스를 사용하여 VM 이름 배열을 xVirtualMachine 리소스에 전달하여 여러 VM을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-128">You can also use this resource to create multiple VMs by passing in an array of VM names to the xVirtualMachine resource.</span></span>

```PowerShell
Configuration MultipleVms
{
    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VMs
        {
            VMName = "IIS01", "SQL01", "SQL02"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="8f705-129">PsDscRunAsCredential 지원</span><span class="sxs-lookup"><span data-stu-id="8f705-129">Supporting PsDscRunAsCredential</span></span>

> [!NOTE]
> <span data-ttu-id="8f705-130">**PsDscRunAsCredential** 은 PowerShell 5.0이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-130">**PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="8f705-131">**PsDscRunAsCredential** 속성을 [DSC 구성](../configurations/configurations.md) 리소스 블록에서 사용하면 지정된 자격 증명 집합으로 리소스를 실행해야 함을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-131">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span> <span data-ttu-id="8f705-132">자세한 내용은 [사용자 자격 증명을 사용하여 DSC 실행](../configurations/runAsUser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8f705-132">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="8f705-133">사용자 지정 리소스 내에서 사용자 컨텍스트에 액세스하려는 경우 `$PsDscContext` 자동 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-133">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="8f705-134">예를 들어 다음 코드는 리소스가 자세한 정보 출력 스트림으로 실행되는 사용자 컨텍스트를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="8f705-134">For example, the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="8f705-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8f705-135">See Also</span></span>

### <a name="concepts"></a><span data-ttu-id="8f705-136">개념</span><span class="sxs-lookup"><span data-stu-id="8f705-136">Concepts</span></span>

- [<span data-ttu-id="8f705-137">Writing a custom DSC resource with MOF(MOF를 사용하여 사용자 지정 DSC 리소스 작성)</span><span class="sxs-lookup"><span data-stu-id="8f705-137">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="8f705-138">Windows PowerShell 필요한 상태 구성 시작</span><span class="sxs-lookup"><span data-stu-id="8f705-138">Get Started with Windows PowerShell Desired State Configuration</span></span>](../overview/overview.md)
