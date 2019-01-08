---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 구성 데이터의 자격 증명 옵션
ms.openlocfilehash: 10cf3456fcc7104b7dd779db30aebace54ba087a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046644"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="f173e-103">구성 데이터의 자격 증명 옵션</span><span class="sxs-lookup"><span data-stu-id="f173e-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="f173e-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="f173e-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="f173e-105">일반 텍스트 암호 및 도메인 사용자</span><span class="sxs-lookup"><span data-stu-id="f173e-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="f173e-106">암호화하지 않고 자격 증명을 포함하는 DSC를 구성하면 일반 텍스트 암호에 대한 오류 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="f173e-107">또한 DSC에서는 도메인 자격 증명을 사용하는 경우 경고를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="f173e-108">이러한 오류 및 경고 메시지가 발생하지 않도록 하려면, DSC 구성 데이터 키워드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="f173e-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="f173e-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="f173e-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="f173e-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="f173e-111">일반적으로 암호화되지 않은 일반 텍스트 암호를 저장/전송하는 작업은 안전하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="f173e-112">이 항목의 뒷부분에 설명된 기술을 사용하여 자격 증명을 보호하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="f173e-113">Azure Automation DSC 서비스를 사용하면 자격 증명을 중앙에서 관리하여 구성에서 컴파일하고 안전하게 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="f173e-114">자세한 내용은 다음을 참조하세요. [DSC 구성 컴파일 / 자격 증명 자산](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="f173e-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

<span data-ttu-id="f173e-115">다음은 일반 텍스트 자격 증명을 전달하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-115">The following is an example of passing plain text credentials:</span></span>

```powershell
#Prompt user for their credentials
#credentials will be unencrypted in the MOF
$promptedCreds = get-credential -Message "Please enter your credentials to generate a DSC MOF:"

# Store passwords in plaintext, in the document itself
# will also be stored in plaintext in the mof
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "User1"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

# DSC requires explicit confirmation before storing passwords insecurely
$ConfigurationData = @{
    AllNodes = @(
            @{
                # The "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
                NodeName="*"
                PSDscAllowPlainTextPassword = $true
            },
            #however, each node still needs to be explicitly defined for "*" to have meaning
            @{
                NodeName = "TestMachine1"
            },
            #we can also use a property to define node-specific passwords, although this is no more secure
            @{
                NodeName = "TestMachine2";
                UserName = "User2"
                LocalPassword = "ThisIsYetAnotherPlaintextPassword"
            }
        )
}

configuration unencryptedPasswordDemo
{
    Node "TestMachine1"
    {
        # We use the plaintext password to generate a new account
        User User1
        {
            UserName = $username
            Password = $credential
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }
        # We use the prompted password to add this account to the local admins group
        Group addToAdmin
        {
            # Ensure the user exists before we add the user to a group
            DependsOn = "[User]User1"
            Credential = $promptedCreds
            GroupName = "Administrators"
            Ensure = "Present"
            MembersToInclude = "User1"
        }
    }

    Node "TestMachine2"
    {
        # Now we'll use a node-specific password to this machine
        $password = $Node.LocalPassword | ConvertTo-SecureString -asPlainText -Force
        $username = $node.UserName
        [PSCredential] $nodeCred = New-Object System.Management.Automation.PSCredential($username,$password)

        User User2
        {
            UserName = $username
            Password = $nodeCred
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }

        Group addToAdmin
        {
            Credential = $promptedCreds
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }
}

# We declared the ConfigurationData in a local variable, but we need to pass it
# in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData

# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

<span data-ttu-id="f173e-116">이것이 "TestMachine1"에 대 한 구성에 의해 생성 되는 ".mof" 파일에서 발췌 한 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-116">This is an excerpt from the ".mof" file generated by the configuration for "TestMachine1".</span></span> <span data-ttu-id="f173e-117">`System.Security.SecureString` 에 사용 되는 구성 된 일반 텍스트로 변환 하 고 ".mof" 파일에 저장 한 `MSF_Credential`합니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-117">The `System.Security.SecureString` used in the configuration was converted to plain text and stored in the ".mof" file as a `MSF_Credential`.</span></span> <span data-ttu-id="f173e-118">`SecureString` 현재 사용자 프로필을 사용 하 여 암호화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-118">A `SecureString` is encrypted with the current users profile.</span></span> <span data-ttu-id="f173e-119">이 PowerShell 원격 관리의 모든 형태와 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-119">This works well with all forms of PowerShell remote management.</span></span> <span data-ttu-id="f173e-120">"Mof" 파일은 독립 실행형 구성 메커니즘을 되도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-120">A ".mof" file is designed to be a stand alone configuration mechanism.</span></span> <span data-ttu-id="f173e-121">PowerShell 5.0부터 노드에서 ".mof" 파일에 노드로 전송 하지만 미사용 암호화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-121">Beginning in PowerShell 5.0, ".mof" files on a Node are encrypted at rest, but not in transit to the Node.</span></span> <span data-ttu-id="f173e-122">즉, 노드를 적용 하면 "mof" 파일에서 암호 일반 텍스트로 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-122">This means that passwords in a ".mof" file are exposed as clear text when you apply them to a Node.</span></span> <span data-ttu-id="f173e-123">자격 증명을 암호화 하려면 사용 해야는 **끌어오기 서버**합니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-123">To encrypt credentials, you need to use a **Pull Server**.</span></span> <span data-ttu-id="f173e-124">자세한 내용은 [인증서를 사용 하 여 보안 MOF 파일](../pull-server/secureMOF.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-124">For more information, see [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>

```syntax
instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsYetAnotherPlaintextPassword";
 UserName = "User2";

};

instance of MSFT_UserResource as $MSFT_UserResource1ref
{
ResourceID = "[User]User2";
 Description = "local account";
 UserName = "User2";
 Ensure = "Present";
 Password = $MSFT_Credential1ref;
 Disabled = False;
 SourceInfo = "::66::9::User";
 PasswordNeverExpires = True;
 ModuleName = "PsDesiredStateConfiguration";
 PasswordChangeRequired = False;

ModuleVersion = "1.0";

 ConfigurationName = "unencryptedPasswordDemo";

};
```

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="f173e-125">DSC에서의 자격 증명 처리</span><span class="sxs-lookup"><span data-stu-id="f173e-125">Handling Credentials in DSC</span></span>

<span data-ttu-id="f173e-126">기본적으로 DSC 구성 리소스는 `Local System`으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-126">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="f173e-127">그러나 일부 리소스는 `Package` 리소스가 특정 사용자 계정으로 소프트웨어를 설치해야 할 때와 같은 경우 자격 증명을 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-127">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="f173e-128">이전 리소스에서는 하드 코드된 `Credential` 속성 이름을 사용하여 이 문제를 처리했습니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-128">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="f173e-129">WMF 5.0에서는 모든 리소스에 대해 자동 `PsDscRunAsCredential` 속성을 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-129">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="f173e-130">`PsDscRunAsCredential` 사용에 대한 자세한 내용은 [사용자 자격 증명을 사용하여 DSC 실행](runAsUser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f173e-130">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="f173e-131">최신 리소스와 사용자 지정 리소스에서는 자격 증명에 대한 고유한 속성을 만드는 대신 이 자동 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-131">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="f173e-132">일부 리소스의 디자인이 특정한 이유로 여러 자격 증명을 사용하게 되면 이러한 리소스는 고유한 자격 증명 속성을 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-132">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="f173e-133">리소스에 대해 사용 가능한 자격 증명 속성을 찾으려면 `Get-DscResource -Name ResourceName -Syntax`나 ISE의 Intellisense(`CTRL+SPACE`)를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="f173e-133">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="f173e-134">이 예제에서는 `PSDesiredStateConfiguration` 기본 제공 DSC 리소스 모듈의 [그룹](../resources/resources.md) 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-134">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="f173e-135">로컬 그룹을 만들고 구성원을 추가 또는 제거할 수 있으며,</span><span class="sxs-lookup"><span data-stu-id="f173e-135">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="f173e-136">`Credential` 속성 및 자동 `PsDscRunAsCredential` 속성도 둘 다 받습니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-136">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="f173e-137">그러나 리소스는 `Credential` 속성만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-137">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="f173e-138">`PsDscRunAsCredential` 속성에 대한 자세한 내용은 [사용자 자격 증명을 사용하여 DSC 실행](runAsUser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f173e-138">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="f173e-139">예: 그룹 리소스 자격 증명 속성</span><span class="sxs-lookup"><span data-stu-id="f173e-139">Example: The Group resource Credential property</span></span>

<span data-ttu-id="f173e-140">DSC는 `Local System`에서 실행되므로, DSC에는 이미 로컬 사용자 및 그룹을 변경할 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-140">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="f173e-141">추가된 구성원이 로컬 계정이라면 자격 증명이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-141">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="f173e-142">`Group` 리소스에서 로컬 그룹에 도메인 계정을 추가한다면, 자격 증명이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-142">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="f173e-143">Active Directory에 대한 익명 쿼리는 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-143">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="f173e-144">`Group` 리소스의 `Credential` 속성은 Active Directory에 대해 쿼리하는 데 사용된 도메인 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-144">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="f173e-145">대부분의 경우 사용자는 기본적으로 Active Directory에 있는 대부분의 개체에 대해 *읽기*가 가능하므로 이것은 일반 사용자 계정일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-145">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="f173e-146">예제 구성</span><span class="sxs-lookup"><span data-stu-id="f173e-146">Example Configuration</span></span>

<span data-ttu-id="f173e-147">다음 코드 예제에서는 DSC를 사용하여 도메인 사용자로 로컬 그룹을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-147">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="f173e-148">이 코드는 오류 메시지와 경고 메시지를 모두 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-148">This code generates both an error and warning message:</span></span>

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing
property 'Credential' OF TYPE 'Group': Converting and storing encrypted
passwords as plain text is not recommended. For more information on securing
credentials in MOF file, please refer to MSDN blog:
http://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:297 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance

WARNING: It is not recommended to use domain credential for node 'localhost'.
In order to suppress the warning, you can add a property named
'PSDscAllowDomainUser' with a value of $true to your DSC configuration data
for node 'localhost'.
```

<span data-ttu-id="f173e-149">이 예제에는 두 가지 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-149">This example has two issues:</span></span>
1. <span data-ttu-id="f173e-150">오류에서는 일반 텍스트 암호는 권장되지 않는다고 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-150">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="f173e-151">경고에서는 도메인 자격 증명을 사용하지 말라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-151">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="f173e-152">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="f173e-152">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="f173e-153">첫 번째 오류 메시지에는 설명이 있는 URL이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-153">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="f173e-154">이 링크에서는 [ConfigurationData](./configData.md) 구조와 인증서를 사용하여 암호를 암호화하는 방법에 대해 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-154">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="f173e-155">인증서 및 DSC에 대한 자세한 내용은 [이 게시물을 읽어 보세요](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="f173e-155">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="f173e-156">일반 텍스트 암호를 적용하려면 다음과 같이 리소스의 구성 데이터 섹션에 `PsDscAllowPlainTextPassword` 키워드가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-156">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred -ConfigurationData $cd
```

> [!NOTE]
> <span data-ttu-id="f173e-157">`NodeName` 은 별표와 같을 수 없으며 특정 노드 이름은 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-157">`NodeName` cannot equal asterisk, a specific node name is mandatory.</span></span>

<span data-ttu-id="f173e-158">**Microsoft에서는 일반 텍스트 암호가 상당한 보안 위험이 있으므로 사용하지 말 것을 권고합니다.**</span><span class="sxs-lookup"><span data-stu-id="f173e-158">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="f173e-159">도메인 자격 증명</span><span class="sxs-lookup"><span data-stu-id="f173e-159">Domain Credentials</span></span>

<span data-ttu-id="f173e-160">예제 구성 스크립트를 다시 실행(암호화를 사용하든 사용하지 않든)해도 여전히 자격 증명에 대한 도메인 계정을 사용하지 않는 것이 좋다는 경고가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-160">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="f173e-161">로컬 계정을 사용하면 다른 서버에 사용할 수 있는 도메인 자격 증명이 노출될 가능성을 없어집니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-161">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="f173e-162">**DSC 리소스에서 자격 증명을 사용할 경우 가능하면 도메인 계정보다는 로컬 계정을 사용하도록 합니다.**</span><span class="sxs-lookup"><span data-stu-id="f173e-162">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="f173e-163">자격 증명의 `Username` 속성에 '\' 또는 '@'가 없다면 DSC에서는 이것을 도메인 계정으로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-163">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="f173e-164">사용자 이름의 도메인 부분에 "localhost", "127.0.0.1" 및 "::1"에 대한 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-164">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="f173e-165">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="f173e-165">PSDscAllowDomainUser</span></span>

<span data-ttu-id="f173e-166">위의 DSC `Group` 리소스 예제에서 Active Directory 도메인에 대해 쿼리하려면 도메인 계정이 *있어야 합니다*.</span><span class="sxs-lookup"><span data-stu-id="f173e-166">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="f173e-167">이 경우 다음과 같이 `PSDscAllowDomainUser` 속성을 `ConfigurationData` 블록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-167">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

```powershell
$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            # PSDscAllowPlainTextPassword = $true
            CertificateFile = "C:\PublicKeys\server1.cer"
        }
    )
}
```

<span data-ttu-id="f173e-168">이제 구성 스크립트가 오류 또는 경고 없이 MOF 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f173e-168">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
