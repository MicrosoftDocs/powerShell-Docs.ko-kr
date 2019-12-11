---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 구성 데이터의 자격 증명 옵션
ms.openlocfilehash: 660c3643f7eb2e9ccb91bd992747fb9d5da0ccdb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954540"
---
# <a name="credentials-options-in-configuration-data"></a>구성 데이터의 자격 증명 옵션

>적용 대상: Windows Powershell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>일반 텍스트 암호 및 도메인 사용자

암호화하지 않고 자격 증명을 포함하는 DSC를 구성하면 일반 텍스트 암호에 대한 오류 메시지가 생성됩니다.
또한 DSC에서는 도메인 자격 증명을 사용하는 경우 경고를 생성합니다.
이러한 오류 및 경고 메시지가 발생하지 않도록 하려면, DSC 구성 데이터 키워드를 사용합니다.

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> 일반적으로 암호화되지 않은 일반 텍스트 암호를 저장/전송하는 작업은 안전하지 않습니다. 이 항목의 뒷부분에 설명된 기술을 사용하여 자격 증명을 보호하는 것이 좋습니다.
> Azure Automation DSC 서비스를 사용하면 자격 증명을 중앙에서 관리하여 구성에서 컴파일하고 안전하게 저장할 수 있습니다.
> 자세한 내용은 [DSC 구성 컴파일/자격 증명 자산](/azure/automation/automation-dsc-compile#credential-assets)을 참조하세요.

## <a name="handling-credentials-in-dsc"></a>DSC에서의 자격 증명 처리

기본적으로 DSC 구성 리소스는 `Local System`으로 실행됩니다.
그러나 일부 리소스는 `Package` 리소스가 특정 사용자 계정으로 소프트웨어를 설치해야 할 때와 같은 경우 자격 증명을 필요로 합니다.

이전 리소스에서는 하드 코드된 `Credential` 속성 이름을 사용하여 이 문제를 처리했습니다.
WMF 5.0에서는 모든 리소스에 대해 자동 `PsDscRunAsCredential` 속성을 추가했습니다.
`PsDscRunAsCredential` 사용에 대한 자세한 내용은 [사용자 자격 증명을 사용하여 DSC 실행](runAsUser.md)을 참조하세요.
최신 리소스와 사용자 지정 리소스에서는 자격 증명에 대한 고유한 속성을 만드는 대신 이 자동 속성을 사용할 수 있습니다.

> [!NOTE]
> 일부 리소스의 디자인이 특정한 이유로 여러 자격 증명을 사용하게 되면 이러한 리소스는 고유한 자격 증명 속성을 갖게 됩니다.

리소스에 대해 사용 가능한 자격 증명 속성을 찾으려면 `Get-DscResource -Name ResourceName -Syntax`나 ISE의 Intellisense(`CTRL+SPACE`)를 사용하세요.

```powershell
PS C:\> Get-DscResource -Name Group -Syntax
Group [String] #ResourceName
{
    GroupName = [string]
    [Credential = [PSCredential]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Members = [string[]]]
    [MembersToExclude = [string[]]]
    [MembersToInclude = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

이 예제에서는 `PSDesiredStateConfiguration` 기본 제공 DSC 리소스 모듈의 [그룹](../resources/resources.md) 리소스를 사용합니다.
로컬 그룹을 만들고 구성원을 추가 또는 제거할 수 있으며,
`Credential` 속성 및 자동 `PsDscRunAsCredential` 속성도 둘 다 받습니다.
그러나 리소스는 `Credential` 속성만 사용합니다.

`PsDscRunAsCredential` 속성에 대한 자세한 내용은 [사용자 자격 증명을 사용하여 DSC 실행](runAsUser.md)을 참조하세요.

## <a name="example-the-group-resource-credential-property"></a>예: 그룹 리소스 자격 증명 속성

DSC는 `Local System`에서 실행되므로, DSC에는 이미 로컬 사용자 및 그룹을 변경할 권한이 있습니다.
추가된 구성원이 로컬 계정이라면 자격 증명이 필요하지 않습니다.
`Group` 리소스에서 로컬 그룹에 도메인 계정을 추가한다면, 자격 증명이 필요합니다.

Active Directory에 대한 익명 쿼리는 허용되지 않습니다.
`Group` 리소스의 `Credential` 속성은 Active Directory에 대해 쿼리하는 데 사용된 도메인 계정입니다.
대부분의 경우 사용자는 기본적으로 Active Directory에 있는 대부분의 개체에 대해 *읽기*가 가능하므로 이것은 일반 사용자 계정일 수 있습니다.

## <a name="example-configuration"></a>예제 구성

다음 코드 예제에서는 DSC를 사용하여 도메인 사용자로 로컬 그룹을 채웁니다.

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred
```

이 코드는 오류 메시지와 경고 메시지를 모두 생성합니다.

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing property 'Credential' OF
TYPE 'Group': Converting and storing encrypted passwords as plain text is not recommended.
For more information on securing credentials in MOF file, please refer to MSDN blog:
https://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:341 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance
WARNING: It is not recommended to use domain credential for node 'localhost'. In order to suppress
the warning, you can add a property named 'PSDscAllowDomainUser' with a value of $true to your DSC
configuration data for node 'localhost'.

Compilation errors occurred while processing configuration
'DomainCredentialExample'. Please review the errors reported in error stream and modify your
configuration code appropriately.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3917 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (DomainCredentialExample:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```

이 예제에는 두 가지 문제가 있습니다.

1. 오류에서는 일반 텍스트 암호는 권장되지 않는다고 설명합니다.
2. 경고에서는 도메인 자격 증명을 사용하지 말라고 합니다.

플래그 **PSDSCAllowPlainTextPassword** 및 **PSDSCAllowDomainUser**는 사용자에게 관련된 위험을 알리는 오류 및 경고를 표시하지 않습니다.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

첫 번째 오류 메시지에는 설명이 있는 URL이 있습니다.
이 링크에서는 [ConfigurationData](./configData.md) 구조와 인증서를 사용하여 암호를 암호화하는 방법에 대해 설명입니다.
인증서 및 DSC에 대한 자세한 내용은 [이 게시물을 읽어 보세요](https://aka.ms/certs4dsc).

일반 텍스트 암호를 적용하려면 다음과 같이 리소스의 구성 데이터 섹션에 `PsDscAllowPlainTextPassword` 키워드가 있어야 합니다.

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

### <a name="localhostmof"></a>localhost.mof

**PSDSCAllowPlainTextPassword** 플래그는 사용자가 MOF 파일에 일반 텍스트 암호를 저장할 경우의 위험을 확인하도록 합니다. 생성된 MOF 파일에서는 **SecureString**을 포함하는 **PSCredential** 개체가 사용된 경우에도 암호가 일반 텍스트로 나타납니다. 유일하게 자격 증명이 공개되는 경우입니다. 이 MOF 파일에 대한 액세스 권한을 얻으면 누구나 관리자 계정에 액세스할 수 있습니다.

```
/*
@TargetNode='localhost'
@GeneratedBy=Administrator
@GenerationDate=01/31/2019 06:43:13
@GenerationHost=Server01
*/

instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsAPlaintextPassword";
 UserName = "Administrator";

};

instance of MSFT_GroupResource as $MSFT_GroupResource1ref
{
ResourceID = "[Group]DomainUserToLocalGroup";
 MembersToInclude = {
    "contoso\\alice"
};
 Credential = $MSFT_Credential1ref;
 SourceInfo = "::11::9::Group";
 GroupName = "ApplicationAdmins";
 ModuleName = "PSDesiredStateConfiguration";

ModuleVersion = "1.0";

 ConfigurationName = "DomainCredentialExample";

};
```

### <a name="credentials-in-transit-and-at-rest"></a>전송 중 및 미사용 중인 자격 증명

- **PSDscAllowPlainTextPassword** 플래그는 일반 텍스트 암호를 포함하는 MOF 파일의 컴파일을 허용합니다.
  일반 텍스트 암호를 포함하는 MOF 파일을 저장할 때 주의하세요.
- MOF 파일이 **밀어넣기** 모드에서 노드에 전달되면 **AllowUnencrypted** 매개 변수를 사용하여 기본값을 재정의하지 않는 한, WinRM에서는 통신을 암호화하여 일반 텍스트 암호를 보호합니다.
  - 인증서로 MOF를 암호화하면 노드에 적용되기 전에 미사용 중인 MOF 파일이 보호됩니다.
- **끌어오기** 모드에서는 Internet Information Server에 지정된 프로토콜을 통해 트래픽을 암호화하는 데 HTTPS를 사용하도록 Windows 끌어오기 서버를 구성할 수 있습니다. 자세한 내용은 [DSC 끌어오기 클라이언트 설정](../pull-server/pullclient.md) 및 [인증서로 MOF 파일 보호](../pull-server/secureMOF.md) 문서를 참조하세요.
  - [Azure Automation State Configuration](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) 서비스에서는 끌어오기 트래픽이 항상 암호화됩니다.
- PowerShell 5.0부터, 노드에서 미사용 중인 MOF 파일은 암호화됩니다.
  - PowerShell 4.0에서는 미사용 중인 MOF 파일이 노드로 밀어넣거나 끌어올 때 인증서로 암호화되지 않는 한 해당 파일은 암호화되지 않습니다.

**Microsoft에서는 일반 텍스트 암호가 상당한 보안 위험이 있으므로 사용하지 말 것을 권고합니다.**

## <a name="domain-credentials"></a>도메인 자격 증명

예제 구성 스크립트를 다시 실행(암호화를 사용하든 사용하지 않든)해도 여전히 자격 증명에 대한 도메인 계정을 사용하지 않는 것이 좋다는 경고가 생성됩니다.
로컬 계정을 사용하면 다른 서버에 사용할 수 있는 도메인 자격 증명이 노출될 가능성을 없어집니다.

**DSC 리소스에서 자격 증명을 사용할 경우 가능하면 도메인 계정보다는 로컬 계정을 사용하도록 합니다.**

자격 증명의 `Username` 속성에 '\\'또는'\@'가 없다면 DSC에서는 이것을 도메인 계정으로 처리합니다.
사용자 이름의 도메인 부분에 "localhost", "127.0.0.1" 및 "::1"에 대한 예외가 있습니다.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

위의 DSC `Group` 리소스 예제에서 Active Directory 도메인에 대해 쿼리하려면 도메인 계정이 *있어야 합니다*.
이 경우 다음과 같이 `PSDscAllowDomainUser` 속성을 `ConfigurationData` 블록에 추가합니다.

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

이제 구성 스크립트가 오류 또는 경고 없이 MOF 파일을 생성합니다.
