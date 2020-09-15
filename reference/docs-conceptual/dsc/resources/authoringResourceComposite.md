---
ms.date: 07/08/2020
keywords: dsc,powershell,configuration,setup
title: 복합 리소스--DSC 구성을 리소스로 사용
ms.openlocfilehash: 1baa5e4ca5dfa808edc4452db4874a83aa78107e
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217545"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>복합 리소스: DSC 구성을 자원으로 사용

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

실제 상황에서, 구성은 다양 한 리소스를 호출하고 무수한 속성을 설정하므로 길고 복잡해질 수 있습니다. 이러한 복잡성을 해결하는 데 도움이 되도록 Windows PowerShell DSC(필요한 상태 구성) 구성을 다른 구성에 대한 리소스로 사용할 수 있습니다. 이것을 복합 리소스라고 합니다. 복합 리소스는 매개 변수를 사용하는 DSC 구성입니다. 구성의 매개 변수는 리소스의 속성으로서 작동합니다.
구성은 `.schema.psm1` 확장을 사용하여 파일로 저장됩니다. MOF 스키마와 일반적인 DSC 리소스의 리소스 스크립트를 모두 대신합니다. DSC 리소스에 대한 자세한 내용은 [Windows PowerShell 필요한 상태 구성 리소스](resources.md)를 참조하세요.

## <a name="creating-the-composite-resource"></a>복합 리소스 만들기

이 예제에서는 다양한 기존 리소스를 호출하여 가상 컴퓨터를 구성하는 구성을 만듭니다. 구성 블록에서 설정되는 값을 지정하는 대신 구성에서는 매개 변수를 가져와서 구성 블록에 사용합니다.

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
> DSC는 현재, 복합 리소스 내에서 복합 리소스 또는 중첩된 구성을 배치하도록 지원하지 않습니다.

### <a name="saving-the-configuration-as-a-composite-resource"></a>구성을 복합 리소스로서 저장

매개 변수가 있는 구성을 DSC 리소스로 사용하려면, 이 구성을 다른 MOF 기반 리소스의 디렉터리 구조과 같은 디렉터리 구조에 저장하고 이름을 `.schema.psm1` 확장으로 지정합니다. 이 예에서는 파일 이름을 `xVirtualMachine.schema.psm1`로 지정합니다. 다음 줄을 포함하는 `xVirtualMachine.psd1`이라는 매니페스트도 만들어야 합니다.

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

> [!NOTE]
> `MyDscResources.psd1` 외에 `MyDscResources` 폴더 아래의 모든 리소스에 대한 모듈 매니페스트를 나타냅니다.

완료되면 폴더 구조는 다음과 같아야 합니다.

```
$env: psmodulepath
    |- MyDscResources
        |- MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

이제 리소스는 `Get-DscResource` cmdlet을 사용하여 검색할 수 있으며, 해당 속성은 해당 cmdlet이나, Windows PowerShell ISE에서 <kbd>Ctrl</kbd>+<kbd>Space</kbd> 자동 완성을 사용하여 검색할 수 있습니다.

## <a name="using-the-composite-resource"></a>복합 리소스 사용

다음으로 복합 리소스를 호출하는 구성을 만듭니다. 이 구성은 xVirtualMachine 복합 리소스를 호출하여 가상 컴퓨터를 만든 다음, **xComputer** 리소스를 호출하여 이름을 변경합니다.

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

또한 이 리소스를 사용하여 VM 이름 배열을 xVirtualMachine 리소스에 전달하여 여러 VM을 만들 수도 있습니다.

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

## <a name="supporting-psdscrunascredential"></a>PsDscRunAsCredential 지원

> [!NOTE]
> **PsDscRunAsCredential**은 PowerShell 5.0이상에서 지원됩니다.

**PsDscRunAsCredential** 속성을 [DSC 구성](../configurations/configurations.md) 리소스 블록에서 사용하면 지정된 자격 증명 집합으로 리소스를 실행해야 함을 지정할 수 있습니다. 자세한 내용은 [사용자 자격 증명을 사용하여 DSC 실행](../configurations/runAsUser.md)을 참조하세요.

사용자 지정 리소스 내에서 사용자 컨텍스트에 액세스하려는 경우 `$PsDscContext` 자동 변수를 사용할 수 있습니다.

예를 들어 다음 코드는 리소스가 자세한 정보 출력 스트림으로 실행되는 사용자 컨텍스트를 작성합니다.

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>참고 항목

### <a name="concepts"></a>개념

- [Writing a custom DSC resource with MOF(MOF를 사용하여 사용자 지정 DSC 리소스 작성)](authoringResourceMOF.md)
- [Windows PowerShell 필요한 상태 구성 시작](../overview/overview.md)
