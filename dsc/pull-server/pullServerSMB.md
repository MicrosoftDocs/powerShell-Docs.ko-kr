---
ms.date: 04/11/2018
keywords: dsc,powershell,configuration,setup
title: DSC SMB 끌어오기 서버 설정
ms.openlocfilehash: 722120369df9ff383a02c69111e0bacf2e2e76a5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402260"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="57a18-103">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="57a18-103">Setting up a DSC SMB pull server</span></span>

<span data-ttu-id="57a18-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="57a18-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="57a18-105">끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="57a18-106">관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="57a18-107">DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) 끌어오기 서버는 대상 노드에서 DSC 구성 파일 및/또는 DSC 리소스를 요청 시 사용할 수 있게 해주는 SMB 파일 공유를 호스트하는 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-107">A DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="57a18-108">DSC에 대해 SMB 끌어오기 서버를 사용하려면 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-108">To use an SMB pull server for DSC, you have to:</span></span>

- <span data-ttu-id="57a18-109">PowerShell 4.0 이상을 실행 중인 서버에서 SMB 파일 공유 설정</span><span class="sxs-lookup"><span data-stu-id="57a18-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="57a18-110">PowerShell 4.0 이상을 실행 중인 클라이언트에서 해당 SMB 공유에서 끌어오도록 구성</span><span class="sxs-lookup"><span data-stu-id="57a18-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="57a18-111">XSmbShare 리소스를 사용하여 SMB 파일 공유 만들기</span><span class="sxs-lookup"><span data-stu-id="57a18-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="57a18-112">다양한 방법으로 SMB 파일 공유를 설정할 수 있지만 여기서는 DSC를 사용하여 설정하는 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="57a18-113">XSmbShare 리소스 설치</span><span class="sxs-lookup"><span data-stu-id="57a18-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="57a18-114">[Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet을 호출하여 **xSmbShare** 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-114">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xSmbShare** module.</span></span>

> [!NOTE]
> <span data-ttu-id="57a18-115">`Install-Module`은 PowerShell 5.0에 포함된 **PowerShellGet** 모듈에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-115">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="57a18-116">[PackageManagement PowerShell 모듈 미리 보기](https://www.microsoft.com/en-us/download/details.aspx?id=49186)에서 PowerShell 3.0 및 4.0용 **PowerShellGet** 모듈을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-116">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
> <span data-ttu-id="57a18-117">**xSmbShare**에는 SMB 파일 공유를 만드는 데 사용할 수 있는 DSC 리소스 **xSmbShare**가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-117">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="57a18-118">디렉터리 및 파일 공유 만들기</span><span class="sxs-lookup"><span data-stu-id="57a18-118">Create the directory and file share</span></span>

<span data-ttu-id="57a18-119">다음 구성에서는 **파일** 리소스를 사용하여 공유의 디렉터리를 만들고 **xSmbShare** 리소스를 사용하여 SMB 공유를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-119">The following configuration uses the **File** resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

```powershell
Configuration SmbShare
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

<span data-ttu-id="57a18-120">구성 디렉터리를 만들고 `C:\DscSmbShare`존재 하지 않는 경우 다음 해당 디렉터리를 사용 하 여 SMB 파일 공유로, 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-120">The configuration creates the directory `C:\DscSmbShare`, if it doesn't already exist, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="57a18-121">**FullAccess** 에 쓰거나 파일 공유에서 삭제 해야 하는 모든 계정에 부여 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-121">**FullAccess** should be given to any account that needs to write to or delete from the file share.</span></span> <span data-ttu-id="57a18-122">**ReadAccess** 공유를 구성 및/또는 DSC 리소스를 가져오는 모든 클라이언트 노드에 제공 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-122">**ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share.</span></span>

> [!NOTE]
> <span data-ttu-id="57a18-123">DSC 하므로 컴퓨터 자체를 공유에 액세스할 수 있어야 합니다. 시스템 계정으로 기본적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-123">DSC runs as the system account by default, so the computer itself must have access to the share.</span></span>

### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="57a18-124">파일 시스템에 끌어오기 클라이언트에 대한 액세스 권한 부여</span><span class="sxs-lookup"><span data-stu-id="57a18-124">Give file system access to the pull client</span></span>

<span data-ttu-id="57a18-125">클라이언트 노드에 **ReadAccess**를 부여하면 해당 노드에서 SMB 공유에 액세스할 수 있지만 해당 공유 내의 파일이나 폴더에는 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-125">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="57a18-126">클라이언트는 SMB 공유 폴더 및 하위 폴더에 대 한 노드 액세스를 명시적으로 부여 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-126">You have to explicitly grant client nodes access to the SMB share folder and subfolders.</span></span> <span data-ttu-id="57a18-127">DSC에서 [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) 모듈에 포함된 **cNtfsPermissionEntry** 리소스 사용을 추가하여 이렇게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-127">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="57a18-128">다음 구성에서는 끌어오기 클라이언트에 ReadAndExecute 액세스를 부여하는 **cNtfsPermissionEntry** 블록을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-128">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

```powershell
Configuration DSCSMB
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare
    Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DscSmbShare'
            Principal = 'myDomain\Contoso-Server$'
            AccessControlInformation = @(
                cNtfsAccessControlInformation
                {
                    AccessControlType = 'Allow'
                    FileSystemRights = 'ReadAndExecute'
                    Inheritance = 'ThisFolderSubfoldersAndFiles'
                    NoPropagateInherit = $false
                }
            )
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="57a18-129">구성 및 리소스 배치</span><span class="sxs-lookup"><span data-stu-id="57a18-129">Placing configurations and resources</span></span>

<span data-ttu-id="57a18-130">클라이언트 노드가 SMB 공유 폴더에서 끌어올 모든 구성 MOF 파일 및/또는 DSC 리소스를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-130">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="57a18-131">모든 구성 MOF 파일의 이름은 *ConfigurationID*.mof로 지정해야 합니다. 여기서 *ConfigurationID*는 대상 노드의 LCM의 **ConfigurationID** 속성의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-131">Any configuration MOF file must be named *ConfigurationID*.mof, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="57a18-132">끌어오기 클라이언트 구성에 대한 자세한 내용은 [구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57a18-132">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="57a18-133">SMB 끌어오기 서버를 사용하는 경우 구성 ID를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-133">You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="57a18-134">SMB에서는 구성 이름이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-134">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="57a18-135">각 리소스 모듈은 압축해야 하며 `{Module Name}_{Module Version}.zip` 패턴에 따라 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-135">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="57a18-136">예를 들어 모듈 버전이 3.1.2.0인 xWebAdminstration이라는 모듈은 'xWebAdministration_3.2.1.0.zip'으로 이름이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-136">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="57a18-137">모듈의 각 버전은 단일 zip 파일에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-137">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="57a18-138">서로 다른 버전의 모듈 zip 파일에 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-138">Separate versions of a module in a zip file are not supported.</span></span> <span data-ttu-id="57a18-139">끌어오기 서버에서 사용할 DSC 리소스 모듈을 패키징하기를 전에 디렉터리 구조를 약간 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-139">Before packaging up DSC resource modules for use with pull server, you need to make a small change to the directory structure.</span></span>

<span data-ttu-id="57a18-140">WMF 5.0의 DSC 리소스를 포함하는 모듈의 기본 형식은 `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`입니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-140">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>

<span data-ttu-id="57a18-141">끌어오기 서버에 대해 패키징하기 전에 `{Module version}` 폴더를 제거하면 되므로 경로는 `{Module Folder}\DscResources\{DSC Resource Folder}\`가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-141">Before packaging up for the pull server simply remove the `{Module version}` folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="57a18-142">이렇게 변경하고 위에서 설명한 대로 폴더를 압축하여 이러한 zip 파일을 SMB 공유 폴더에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-142">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="57a18-143">MOF 체크섬 만들기</span><span class="sxs-lookup"><span data-stu-id="57a18-143">Creating the MOF checksum</span></span>

<span data-ttu-id="57a18-144">구성 MOF 파일은 대상 노드의 LCM이 구성에 대한 유효성을 검사할 수 있도록 체크섬 파일과 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-144">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="57a18-145">체크섬을 만들려면 [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-145">To create a checksum, call the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="57a18-146">이 cmdlet은 구성 MOF가 있는 폴더를 지정하는 `Path` 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-146">The cmdlet takes a `Path` parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="57a18-147">cmdlet은 `ConfigurationMOFName.mof.checksum`이라는 체크섬 파일을 만들며, 여기서 `ConfigurationMOFName`은 구성 mof 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-147">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="57a18-148">지정된 폴더에 구성 MOF 파일이 두 개 이상 있는 경우, 폴더에 있는 각 구성에 대해 체크섬이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-148">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="57a18-149">체크섬 파일은 구성 MOF 파일과 동일한 디렉터리에 있어야 하며(기본적으로 `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`), 동일한 이름에 확장명으로 `.checksum`을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-149">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

> [!NOTE]
> <span data-ttu-id="57a18-150">어떤 식으로든 구성 MOF 파일을 변경하는 경우 체크섬 파일도 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-150">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="57a18-151">SMB에 대한 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="57a18-151">Setting up a pull client for SMB</span></span>

<span data-ttu-id="57a18-152">SMB 공유에서 구성 및/또는 리소스를 끌어오는 클라이언트를 설정하려면 구성 및 DSC 리소스를 끌어올 원본 공유를 지정하는 **ConfigurationRepositoryShare** 및 **ResourceRepositoryShare** 블록을 사용하여 클라이언트의 LCM(로컬 구성 관리자)을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-152">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="57a18-153">LCM 구성에 대한 자세한 내용은 [구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57a18-153">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="57a18-154">편의상 이 예제에서는 **PSDscAllowPlainTextPassword**를 사용하여 일반 텍스트 암호를 **Credential** 매개 변수에 전달하는 것을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-154">For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="57a18-155">자격 증명을 더 안전하게 전달하는 방법에 대한 자세한 내용은 [구성 데이터의 자격 증명 옵션](../configurations/configDataCredentials.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57a18-155">For information about passing credentials more securely, see [Credentials Options in Configuration Data](../configurations/configDataCredentials.md).</span></span>
>
> <span data-ttu-id="57a18-156">리소스를 끌어오기만 하는 경우에도 SMB 끌어오기 서버에 대한 메타 구성의 **Settings** 블록에 **ConfigurationID**를 지정**해야** 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-156">You **MUST** specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

```powershell
$secpasswd = ConvertTo-SecureString “Pass1Word” -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential (“TestUser”, $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }

         ConfigurationRepositoryShare SmbConfigShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds

        }
    }
}

$ConfigurationData = @{
    AllNodes = @(
        @{
            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="localhost"
            PSDscAllowPlainTextPassword = $true
        })
}
```

## <a name="acknowledgements"></a><span data-ttu-id="57a18-157">감사의 말</span><span class="sxs-lookup"><span data-stu-id="57a18-157">Acknowledgements</span></span>

<span data-ttu-id="57a18-158">개인 특히 감사 드립니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-158">Special thanks to the following individuals:</span></span>

- <span data-ttu-id="57a18-159">Mike F. Robbins. 그가 게시한 DSC에 SMB 사용에 대한 게시물은 이 항목의 내용을 알리는 데 도움이 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-159">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="57a18-160">그의 블로그는 [Mike F Robbins](http://mikefrobbins.com/)입니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-160">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="57a18-161">Serge Nikalaichyk. **cNtfsAccessControl** 모듈을 작성했습니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-161">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="57a18-162">이 모듈에 대한 원본은 [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl)에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a18-162">The source for this module is at [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span></span>

## <a name="see-also"></a><span data-ttu-id="57a18-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="57a18-163">See also</span></span>

[<span data-ttu-id="57a18-164">Windows PowerShell 필요한 상태 구성 개요</span><span class="sxs-lookup"><span data-stu-id="57a18-164">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)

[<span data-ttu-id="57a18-165">구성 시행</span><span class="sxs-lookup"><span data-stu-id="57a18-165">Enacting configurations</span></span>](enactingConfigurations.md)

[<span data-ttu-id="57a18-166">구성 ID를 사용하여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="57a18-166">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)
