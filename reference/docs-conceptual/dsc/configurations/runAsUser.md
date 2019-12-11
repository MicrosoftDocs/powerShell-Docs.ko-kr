---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 리소스와 함께 자격 증명 사용
ms.openlocfilehash: fea2e3cad8d081c17853e127203f1d40d98c5de2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953980"
---
# <a name="use-credentials-with-dsc-resources"></a><span data-ttu-id="f91bb-103">DSC 리소스와 함께 자격 증명 사용</span><span class="sxs-lookup"><span data-stu-id="f91bb-103">Use Credentials with DSC Resources</span></span>

> <span data-ttu-id="f91bb-104">적용 대상: Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="f91bb-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="f91bb-105">구성에서 자동 **PsDscRunAsCredential** 속성을 사용하여 지정된 자격 증명 집합으로 DSC 리소스를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f91bb-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span> <span data-ttu-id="f91bb-106">기본적으로 DSC는 각 리소스를 시스템 계정으로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f91bb-106">By default, DSC runs each resource as the system account.</span></span> <span data-ttu-id="f91bb-107">하지만 특정 사용자 컨텍스트에서 MSI 패키지 설치, 사용자 레지스트리 키 설정, 사용자의 특정 로컬 디렉터리 액세스, 또는 네트워크 공유에 액세스와 같이 사용자로 실행이 필요한 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f91bb-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span> <span data-ttu-id="f91bb-108">**PSDSCRunAssential**에 지정한 모든 계정에 대해 대상 머신에서 **SeInteractiveLogonRight**이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f91bb-108">The **SeInteractiveLogonRight** is required, by the target machine, for any account you specify to **PSDSCRunAsCredential**.</span></span> <span data-ttu-id="f91bb-109">자세한 내용은 [계정 권한 상수](/windows/desktop/secauthz/account-rights-constants)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f91bb-109">For more information, see [Account Rights Constants](/windows/desktop/secauthz/account-rights-constants).</span></span>

<span data-ttu-id="f91bb-110">모든 DSC 리소스에는 사용자 자격 증명([PSCredential](/dotnet/api/system.management.automation.pscredential) 개체)으로 설정할 수 있는 **PsDscRunAsCredential** 속성이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f91bb-110">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](/dotnet/api/system.management.automation.pscredential) object).</span></span> <span data-ttu-id="f91bb-111">자격 증명을 구성에서 속성 값으로 하드 코드하거나 값을 [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential)로 설정할 수 있습니다. 후자의 경우 구성을 컴파일할 때 자격 증명을 지정하라는 메시지가 표시됩니다(구성 컴파일에 대해서는 [구성](configurations.md) 참조).</span><span class="sxs-lookup"><span data-stu-id="f91bb-111">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f91bb-112">PowerShell 5.0에서는 복합 리소스를 호출하는 구성에 **PsDscRunAsCredential** 속성을 사용하는 기능은 지원되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f91bb-112">In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span> <span data-ttu-id="f91bb-113">PowerShell 5.1에서는 복합 리소스를 호출하는 구성에 **PsDscRunAsCredential** 속성이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f91bb-113">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span> <span data-ttu-id="f91bb-114">PowerShell 4.0에서는 **PsDscRunAsCredential** 속성을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f91bb-114">The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="f91bb-115">다음 예제에서는 `Get-Credential`을 사용하여 사용자에게 자격 증명을 지정하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f91bb-115">In the following example, `Get-Credential` is used to prompt the user for credentials.</span></span> <span data-ttu-id="f91bb-116">**Registry** 리소스는 Windows 명령 프롬프트 창의 배경색을 지정하는 레지스트리 키를 변경하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f91bb-116">The **Registry** resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

```powershell
Configuration ChangeCmdBackGroundColor
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        Registry CmdPath
        {
            Key                  = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'
            ValueName            = 'DefaultColor'
            ValueData            = '1F'
            ValueType            = 'DWORD'
            Ensure               = 'Present'
            Force                = $true
            Hex                  = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

ChangeCmdBackGroundColor -ConfigurationData $configData
```

> [!NOTE]
> <span data-ttu-id="f91bb-117">이 예제에서는 `C:\publicKeys\targetNode.cer`에 유효한 인증서가 있고 해당 인증서의 지문이 표시된 값이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="f91bb-117">This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span> <span data-ttu-id="f91bb-118">DSC 구성 MOF 파일에서 자격 증명을 암호화하는 방법에 대한 자세한 내용은 [MOF 파일 보안](../pull-server/secureMOF.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f91bb-118">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>
