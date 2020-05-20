---
ms.date: 04/11/2018
keywords: dsc,powershell,configuration,setup
title: DSC SMB 끌어오기 서버 설정
ms.openlocfilehash: be41f7a708f1a129919fae8300fc4307441097f7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500698"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>DSC SMB 끌어오기 서버 설정

적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> 끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다. 관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.

DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) 끌어오기 서버는 대상 노드에서 DSC 구성 파일 및/또는 DSC 리소스를 요청 시 사용할 수 있게 해주는 SMB 파일 공유를 호스트하는 컴퓨터입니다.

DSC에 대해 SMB 끌어오기 서버를 사용하려면 다음을 수행해야 합니다.

- PowerShell 4.0 이상을 실행 중인 서버에서 SMB 파일 공유 설정
- PowerShell 4.0 이상을 실행 중인 클라이언트에서 해당 SMB 공유에서 끌어오도록 구성

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>XSmbShare 리소스를 사용하여 SMB 파일 공유 만들기

다양한 방법으로 SMB 파일 공유를 설정할 수 있지만 여기서는 DSC를 사용하여 설정하는 방법을 살펴봅니다.

### <a name="install-the-xsmbshare-resource"></a>XSmbShare 리소스 설치

[Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet을 호출하여 **xSmbShare** 모듈을 설치합니다.

> [!NOTE]
> `Install-Module`은 PowerShell 5.0에 포함된 **PowerShellGet** 모듈에 포함되어 있습니다.
> **xSmbShare**에는 SMB 파일 공유를 만드는 데 사용할 수 있는 DSC 리소스 **xSmbShare**가 포함되어 있습니다.

### <a name="create-the-directory-and-file-share"></a>디렉터리 및 파일 공유 만들기

다음 구성에서는 **파일** 리소스를 사용하여 공유의 디렉터리를 만들고 **xSmbShare** 리소스를 사용하여 SMB 공유를 설정합니다.

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
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

이 구성은 아직 없는 경우 `C:\DscSmbShare` 디렉터리를 만든 다음, 해당 디렉터리를 SMB 파일 공유로 사용합니다. **FullAccess**는 파일 공유에서 작성하거나 삭제해야 하는 계정에 부여되어야 합니다. **ReadAccess**는 공유로부터 구성 및/또는 DSC 리소스를 가져오는 클라이언트 노드에 제공되어야 합니다.

> [!NOTE]
> DSC는 기본적으로 시스템 계정으로 실행되므로 컴퓨터 자체가 공유에 액세스할 수 있어야 합니다.

### <a name="give-file-system-access-to-the-pull-client"></a>파일 시스템에 끌어오기 클라이언트에 대한 액세스 권한 부여

클라이언트 노드에 **ReadAccess**를 부여하면 해당 노드에서 SMB 공유에 액세스할 수 있지만 해당 공유 내의 파일이나 폴더에는 액세스할 수 없습니다. SMB 공유 폴더 및 하위 폴더에 대한 액세스 권한을 클라이언트 노드에 명시적으로 부여해야 합니다. DSC에서 [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) 모듈에 포함된 **cNtfsPermissionEntry** 리소스 사용을 추가하여 이렇게 할 수 있습니다.
다음 구성에서는 끌어오기 클라이언트에 ReadAndExecute 액세스를 부여하는 **cNtfsPermissionEntry** 블록을 추가합니다.

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

## <a name="placing-configurations-and-resources"></a>구성 및 리소스 배치

클라이언트 노드가 SMB 공유 폴더에서 끌어올 모든 구성 MOF 파일 및/또는 DSC 리소스를 저장합니다.

모든 구성 MOF 파일의 이름은 *ConfigurationID*.mof로 지정해야 합니다. 여기서 *ConfigurationID*는 대상 노드의 LCM의 **ConfigurationID** 속성의 값입니다. 끌어오기 클라이언트 구성에 대한 자세한 내용은 [구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID.md)을 참조하세요.

> [!NOTE]
> SMB 끌어오기 서버를 사용하는 경우 구성 ID를 사용해야 합니다. SMB에서는 구성 이름이 지원되지 않습니다.

각 리소스 모듈은 압축해야 하며 `{Module Name}_{Module Version}.zip` 패턴에 따라 이름을 지정해야 합니다. 예를 들어 모듈 버전이 3.1.2.0인 xWebAdminstration이라는 모듈은 'xWebAdministration_3.2.1.0.zip'으로 이름이 지정됩니다. 모듈의 각 버전은 단일 zip 파일에 포함되어야 합니다. zip 파일에서 다른 버전의 모듈이 지원되지 않습니다.
끌어오기 서버에서 사용할 DSC 리소스 모듈을 패키지하기 전에 디렉터리 구조를 약간 변경해야 합니다.

WMF 5.0의 DSC 리소스를 포함하는 모듈의 기본 형식은 `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`입니다.

끌어오기 서버에 대해 패키징하기 전에 `{Module version}` 폴더를 제거하면 되므로 경로는 `{Module Folder}\DscResources\{DSC Resource Folder}\`가 됩니다. 이렇게 변경하고 위에서 설명한 대로 폴더를 압축하여 이러한 zip 파일을 SMB 공유 폴더에 배치합니다.

## <a name="creating-the-mof-checksum"></a>MOF 체크섬 만들기

구성 MOF 파일은 대상 노드의 LCM이 구성에 대한 유효성을 검사할 수 있도록 체크섬 파일과 함께 사용해야 합니다. 체크섬을 만들려면 [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet을 호출합니다. 이 cmdlet은 구성 MOF가 있는 폴더를 지정하는 `Path` 매개 변수를 사용합니다. cmdlet은 `ConfigurationMOFName.mof.checksum`이라는 체크섬 파일을 만들며, 여기서 `ConfigurationMOFName`은 구성 mof 파일의 이름입니다. 지정된 폴더에 구성 MOF 파일이 두 개 이상 있는 경우, 폴더에 있는 각 구성에 대해 체크섬이 만들어집니다.

체크섬 파일은 구성 MOF 파일과 동일한 디렉터리에 있어야 하며(기본적으로 `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`), 동일한 이름에 확장명으로 `.checksum`을 사용해야 합니다.

> [!NOTE]
> 어떤 식으로든 구성 MOF 파일을 변경하는 경우 체크섬 파일도 다시 만들어야 합니다.

## <a name="setting-up-a-pull-client-for-smb"></a>SMB에 대한 끌어오기 클라이언트 설정

SMB 공유에서 구성 및/또는 리소스를 끌어오는 클라이언트를 설정하려면 구성 및 DSC 리소스를 끌어올 원본 공유를 지정하는 **ConfigurationRepositoryShare** 및 **ResourceRepositoryShare** 블록을 사용하여 클라이언트의 LCM(로컬 구성 관리자)을 구성합니다.

LCM 구성에 대한 자세한 내용은 [구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID.md)을 참조하세요.

> [!NOTE]
> 편의상 이 예제에서는 **PSDscAllowPlainTextPassword**를 사용하여 일반 텍스트 암호를 **Credential** 매개 변수에 전달하는 것을 허용합니다. 자격 증명을 더 안전하게 전달하는 방법에 대한 자세한 내용은 [구성 데이터의 자격 증명 옵션](../configurations/configDataCredentials.md)을 참조하세요. 리소스를 끌어오기만 하는 경우에도 SMB 끌어오기 서버에 대한 메타 구성의 **Settings** 블록에 **ConfigurationID**를 지정**해야** 합니다.

```powershell
$secpasswd = ConvertTo-SecureString "Pass1Word" -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential ("TestUser", $secpasswd)

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

## <a name="acknowledgements"></a>감사의 말

다음 분들에게 특히 감사드립니다.

- Mike F. Robbins. 그가 게시한 DSC에 SMB 사용에 대한 게시물은 이 항목의 내용을 알리는 데 도움이 되었습니다. 그의 블로그는 [Mike F Robbins](http://mikefrobbins.com/)입니다.
- Serge Nikalaichyk. **cNtfsAccessControl** 모듈을 작성했습니다. 이 모듈에 대한 원본은 [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl)에 있습니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell Desired State Configuration 개요](../overview/overview.md)

[구성 시행](enactingConfigurations.md)

[구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID.md)
