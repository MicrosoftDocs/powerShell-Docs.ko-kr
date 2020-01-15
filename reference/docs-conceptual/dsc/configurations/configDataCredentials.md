---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 구성 데이터의 자격 증명 옵션
ms.openlocfilehash: aac27f1ff4b4287b53745fa3b946fb3de84771c2
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870560"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="74297-103">구성 데이터의 자격 증명 옵션</span><span class="sxs-lookup"><span data-stu-id="74297-103">Credentials Options in Configuration Data</span></span>

> <span data-ttu-id="74297-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="74297-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="74297-105">일반 텍스트 암호 및 도메인 사용자</span><span class="sxs-lookup"><span data-stu-id="74297-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="74297-106">암호화하지 않고 자격 증명을 포함하는 DSC를 구성하면 일반 텍스트 암호에 대한 오류 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="74297-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span> <span data-ttu-id="74297-107">또한 DSC에서는 도메인 자격 증명을 사용하는 경우 경고를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="74297-107">Also, DSC will generate a warning when using domain credentials.</span></span> <span data-ttu-id="74297-108">이러한 오류 및 경고 메시지가 발생하지 않도록 하려면, DSC 구성 데이터 키워드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="74297-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>

- <span data-ttu-id="74297-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="74297-109">**PsDscAllowPlainTextPassword**</span></span>
- <span data-ttu-id="74297-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="74297-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="74297-111">일반적으로 암호화되지 않은 일반 텍스트 암호를 저장/전송하는 작업은 안전하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="74297-112">이 항목의 뒷부분에 설명된 기술을 사용하여 자격 증명을 보호하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span> <span data-ttu-id="74297-113">Azure Automation DSC 서비스를 사용하면 자격 증명을 중앙에서 관리하여 구성에서 컴파일하고 안전하게 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span> <span data-ttu-id="74297-114">자세한 내용은 [DSC 구성 컴파일/자격 증명 자산](/azure/automation/automation-dsc-compile#credential-assets)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74297-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="74297-115">DSC에서의 자격 증명 처리</span><span class="sxs-lookup"><span data-stu-id="74297-115">Handling Credentials in DSC</span></span>

<span data-ttu-id="74297-116">기본적으로 DSC 구성 리소스는 `Local System`으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="74297-116">DSC configuration resources run as `Local System` by default.</span></span> <span data-ttu-id="74297-117">그러나 일부 리소스는 `Package` 리소스가 특정 사용자 계정으로 소프트웨어를 설치해야 할 때와 같은 경우 자격 증명을 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="74297-117">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="74297-118">이전 리소스에서는 하드 코드된 `Credential` 속성 이름을 사용하여 이 문제를 처리했습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-118">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span> <span data-ttu-id="74297-119">WMF 5.0에서는 모든 리소스에 대해 자동 `PsDscRunAsCredential` 속성을 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-119">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span> <span data-ttu-id="74297-120">`PsDscRunAsCredential` 사용에 대한 자세한 내용은 [사용자 자격 증명을 사용하여 DSC 실행](runAsUser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74297-120">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span> <span data-ttu-id="74297-121">최신 리소스와 사용자 지정 리소스에서는 자격 증명에 대한 고유한 속성을 만드는 대신 이 자동 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-121">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="74297-122">일부 리소스의 디자인이 특정한 이유로 여러 자격 증명을 사용하게 되면 이러한 리소스는 고유한 자격 증명 속성을 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74297-122">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="74297-123">리소스에 대해 사용 가능한 자격 증명 속성을 찾으려면 `Get-DscResource -Name ResourceName -Syntax`나 ISE의 Intellisense(`CTRL+SPACE`)를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="74297-123">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

```powershell
Get-DscResource -Name Group -Syntax
```

```Output
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

<span data-ttu-id="74297-124">이 예제에서는 `PSDesiredStateConfiguration` 기본 제공 DSC 리소스 모듈의 [그룹](../resources/resources.md) 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="74297-124">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span> <span data-ttu-id="74297-125">로컬 그룹을 만들고 구성원을 추가 또는 제거할 수 있으며,</span><span class="sxs-lookup"><span data-stu-id="74297-125">It can create local groups and add or remove members.</span></span> <span data-ttu-id="74297-126">`Credential` 속성 및 자동 `PsDscRunAsCredential` 속성도 둘 다 받습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-126">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span> <span data-ttu-id="74297-127">그러나 리소스는 `Credential` 속성만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="74297-127">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="74297-128">`PsDscRunAsCredential` 속성에 대한 자세한 내용은 [사용자 자격 증명을 사용하여 DSC 실행](runAsUser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74297-128">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="74297-129">예제: 그룹 리소스 자격 증명 속성</span><span class="sxs-lookup"><span data-stu-id="74297-129">Example: The Group resource Credential property</span></span>

<span data-ttu-id="74297-130">DSC는 `Local System`에서 실행되므로, DSC에는 이미 로컬 사용자 및 그룹을 변경할 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-130">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span> <span data-ttu-id="74297-131">추가된 구성원이 로컬 계정이라면 자격 증명이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-131">If the member added is a local account, then no credential is necessary.</span></span> <span data-ttu-id="74297-132">`Group` 리소스에서 로컬 그룹에 도메인 계정을 추가한다면, 자격 증명이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="74297-132">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="74297-133">Active Directory에 대한 익명 쿼리는 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-133">Anonymous queries to Active Directory are not allowed.</span></span> <span data-ttu-id="74297-134">`Group` 리소스의 `Credential` 속성은 Active Directory에 대해 쿼리하는 데 사용된 도메인 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="74297-134">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span> <span data-ttu-id="74297-135">대부분의 경우 사용자는 기본적으로 Active Directory에 있는 대부분의 개체에 대해 *읽기*가 가능하므로 이것은 일반 사용자 계정일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-135">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="74297-136">예제 구성</span><span class="sxs-lookup"><span data-stu-id="74297-136">Example Configuration</span></span>

<span data-ttu-id="74297-137">다음 코드 예제에서는 DSC를 사용하여 도메인 사용자로 로컬 그룹을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="74297-137">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="74297-138">이 코드는 오류 메시지와 경고 메시지를 모두 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="74297-138">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="74297-139">이 예제에는 두 가지 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-139">This example has two issues:</span></span>

1. <span data-ttu-id="74297-140">오류에서는 일반 텍스트 암호는 권장되지 않는다고 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="74297-140">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="74297-141">경고에서는 도메인 자격 증명을 사용하지 말라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="74297-141">A warning advises against using a domain credential</span></span>

<span data-ttu-id="74297-142">플래그 **PSDSCAllowPlainTextPassword** 및 **PSDSCAllowDomainUser**는 사용자에게 관련된 위험을 알리는 오류 및 경고를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-142">The flags **PSDSCAllowPlainTextPassword** and **PSDSCAllowDomainUser** suppress the error and warning informing the user of the risk involved.</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="74297-143">PSDSCAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="74297-143">PSDSCAllowPlainTextPassword</span></span>

<span data-ttu-id="74297-144">첫 번째 오류 메시지에는 설명이 있는 URL이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-144">The first error message has a URL with documentation.</span></span> <span data-ttu-id="74297-145">이 링크에서는 [ConfigurationData](./configData.md) 구조와 인증서를 사용하여 암호를 암호화하는 방법에 대해 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="74297-145">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span> <span data-ttu-id="74297-146">인증서 및 DSC에 대한 자세한 내용은 [이 게시물을 읽어 보세요](https://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="74297-146">For more information on certificates and DSC [read this post](https://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="74297-147">일반 텍스트 암호를 적용하려면 다음과 같이 리소스의 구성 데이터 섹션에 `PsDscAllowPlainTextPassword` 키워드가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74297-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

### <a name="localhostmof"></a><span data-ttu-id="74297-148">localhost.mof</span><span class="sxs-lookup"><span data-stu-id="74297-148">localhost.mof</span></span>

<span data-ttu-id="74297-149">**PSDSCAllowPlainTextPassword** 플래그는 사용자가 MOF 파일에 일반 텍스트 암호를 저장할 경우의 위험을 확인하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="74297-149">The **PSDSCAllowPlainTextPassword** flag requires that the user acknowledge the risk of storing plain text passwords in a MOF file.</span></span> <span data-ttu-id="74297-150">생성된 MOF 파일에서는 **SecureString**을 포함하는 **PSCredential** 개체가 사용된 경우에도 암호가 일반 텍스트로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="74297-150">In the generated MOF file, even though a **PSCredential** object containing a **SecureString** was used, the passwords still appear as plain text.</span></span> <span data-ttu-id="74297-151">유일하게 자격 증명이 공개되는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="74297-151">This is the only time the credentials are exposed.</span></span> <span data-ttu-id="74297-152">이 MOF 파일에 대한 액세스 권한을 얻으면 누구나 관리자 계정에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-152">Gaining access to this MOF file gives anyone access to the Administrator account.</span></span>

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

### <a name="credentials-in-transit-and-at-rest"></a><span data-ttu-id="74297-153">전송 중 및 미사용 중인 자격 증명</span><span class="sxs-lookup"><span data-stu-id="74297-153">Credentials in transit and at rest</span></span>

- <span data-ttu-id="74297-154">**PSDscAllowPlainTextPassword** 플래그는 일반 텍스트 암호를 포함하는 MOF 파일의 컴파일을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="74297-154">The **PSDscAllowPlainTextPassword** flag allows the compilation of MOF files that contain passwords in clear text.</span></span> <span data-ttu-id="74297-155">일반 텍스트 암호를 포함하는 MOF 파일을 저장할 때 주의하세요.</span><span class="sxs-lookup"><span data-stu-id="74297-155">Take precautions when storing MOF files containing clear text passwords.</span></span>
- <span data-ttu-id="74297-156">MOF 파일이 **밀어넣기** 모드에서 노드에 전달되면 **AllowUnencrypted** 매개 변수를 사용하여 기본값을 재정의하지 않는 한, WinRM에서는 통신을 암호화하여 일반 텍스트 암호를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="74297-156">When the MOF file is delivered to a Node in **Push** mode, WinRM encrypts the communication to protect the clear text password unless you override the default with the **AllowUnencrypted** parameter.</span></span>
  - <span data-ttu-id="74297-157">인증서로 MOF를 암호화하면 노드에 적용되기 전에 미사용 중인 MOF 파일이 보호됩니다.</span><span class="sxs-lookup"><span data-stu-id="74297-157">Encrypting the MOF with a certificate protects the MOF file at rest before it has been applied to a node.</span></span>
- <span data-ttu-id="74297-158">**끌어오기** 모드에서는 Internet Information Server에 지정된 프로토콜을 통해 트래픽을 암호화하는 데 HTTPS를 사용하도록 Windows 끌어오기 서버를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-158">In **Pull** mode, you can configure Windows pull server to use HTTPS to encrypt traffic using the protocol specified in Internet Information Server.</span></span> <span data-ttu-id="74297-159">자세한 내용은 [DSC 끌어오기 클라이언트 설정](../pull-server/pullclient.md) 및 [인증서로 MOF 파일 보호](../pull-server/secureMOF.md) 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74297-159">For more information, see the articles [Setting up a DSC pull client](../pull-server/pullclient.md) and [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>
  - <span data-ttu-id="74297-160">[Azure Automation State Configuration](/azure/automation/automation-dsc-overview) 서비스에서는 끌어오기 트래픽이 항상 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="74297-160">In the [Azure Automation State Configuration](/azure/automation/automation-dsc-overview) service, Pull traffic is always encrypted.</span></span>
- <span data-ttu-id="74297-161">PowerShell 5.0부터, 노드에서 미사용 중인 MOF 파일은 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="74297-161">On the Node, MOF files are encrypted at rest Beginning in PowerShell 5.0.</span></span>
  - <span data-ttu-id="74297-162">PowerShell 4.0에서는 미사용 중인 MOF 파일이 노드로 밀어넣거나 끌어올 때 인증서로 암호화되지 않는 한 해당 파일은 암호화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-162">In PowerShell 4.0 MOF files are unencrypted at rest unless they are encrypted with a certificate when they pushed or pulled to the Node.</span></span>

<span data-ttu-id="74297-163">**Microsoft에서는 일반 텍스트 암호가 상당한 보안 위험이 있으므로 사용하지 말 것을 권고합니다.**</span><span class="sxs-lookup"><span data-stu-id="74297-163">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="74297-164">도메인 자격 증명</span><span class="sxs-lookup"><span data-stu-id="74297-164">Domain Credentials</span></span>

<span data-ttu-id="74297-165">예제 구성 스크립트를 다시 실행(암호화를 사용하든 사용하지 않든)해도 여전히 자격 증명에 대한 도메인 계정을 사용하지 않는 것이 좋다는 경고가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="74297-165">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span> <span data-ttu-id="74297-166">로컬 계정을 사용하면 다른 서버에 사용할 수 있는 도메인 자격 증명이 노출될 가능성을 없어집니다.</span><span class="sxs-lookup"><span data-stu-id="74297-166">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="74297-167">**DSC 리소스에서 자격 증명을 사용할 경우 가능하면 도메인 계정보다는 로컬 계정을 사용하도록 합니다.**</span><span class="sxs-lookup"><span data-stu-id="74297-167">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="74297-168">자격 증명의 `Username` 속성에 '\\'또는'\@'가 없다면 DSC에서는 이것을 도메인 계정으로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="74297-168">If there is a '\\' or '\@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span> <span data-ttu-id="74297-169">사용자 이름의 도메인 부분에 "localhost", "127.0.0.1" 및 "::1"에 대한 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74297-169">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="74297-170">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="74297-170">PSDscAllowDomainUser</span></span>

<span data-ttu-id="74297-171">위의 DSC `Group` 리소스 예제에서 Active Directory 도메인에 대해 쿼리하려면 도메인 계정이 *있어야 합니다*.</span><span class="sxs-lookup"><span data-stu-id="74297-171">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span> <span data-ttu-id="74297-172">이 경우 다음과 같이 `PSDscAllowDomainUser` 속성을 `ConfigurationData` 블록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="74297-172">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="74297-173">이제 구성 스크립트가 오류 또는 경고 없이 MOF 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="74297-173">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
