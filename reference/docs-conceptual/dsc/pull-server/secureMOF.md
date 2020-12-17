---
ms.date: 07/06/2020
keywords: dsc,powershell,configuration,setup
title: MOF 파일 보안
description: 이 문서에서는 대상 노드에서 MOF 파일이 암호화되었는지 확인하는 방법을 설명합니다.
ms.openlocfilehash: ca94a901468626e5644880574457d899a012d311
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97090350"
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="626a8-104">MOF 파일 보안</span><span class="sxs-lookup"><span data-stu-id="626a8-104">Securing the MOF File</span></span>

> <span data-ttu-id="626a8-105">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="626a8-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="626a8-106">DSC는 LCM(로컬 구성 관리자)가 원하는 최종 상태를 구현하는 MOF 파일에 저장된 정보를 적용하여 서버 노드의 구성을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-106">DSC manages the configuration of server nodes by applying information stored in a MOF file, where the Local Configuration Manager (LCM) implements the desired end state.</span></span> <span data-ttu-id="626a8-107">이 파일은 구성의 세부 정보를 포함하므로 안전하게 보관해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-107">Because this file contains the details of the configuration, it's important to keep it secure.</span></span> <span data-ttu-id="626a8-108">이 문서에서는 대상 노드에서 파일이 암호화되었는지 확인하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-108">This article describes how to ensure the target node has encrypted the file.</span></span>

<span data-ttu-id="626a8-109">PowerShell 버전 5.0부터 전체 MOF 파일은 `Start-DSCConfiguration` cmdlet을 사용하여 노드에 적용될 때 기본적으로 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-109">Beginning with PowerShell version 5.0, the entire MOF file is encrypted by default when it is applied to the node using the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="626a8-110">이 문서에 설명된 프로세스는 대상 노드가 다운로드한 구성을 시스템에 적용하기 전에 해독하고 읽을 수 있도록 하기 위해 인증서가 관리되지 않는 경우 풀 서비스 프로토콜을 사용하여 솔루션을 구현할 때만 필요합니다(예: Windows Server에서 사용할 수 있는 풀 서비스).</span><span class="sxs-lookup"><span data-stu-id="626a8-110">The process described in this article is required only when implementing a solution using the pull service protocol if certificates are not managed, to ensure configurations downloaded by the target node can be decrypted and read by the system before they are applied (for example, the pull service available in Windows Server).</span></span> <span data-ttu-id="626a8-111">[Azure 자동화 DSC](/azure/automation/automation-dsc-overview)에 등록된 노드에는 관리 오버 헤드가 필요 없는 서비스를 사용하여 자동으로 인증서가 설치되고 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-111">Nodes registered to [Azure Automation DSC](/azure/automation/automation-dsc-overview) will automatically have certificates installed and managed by the service with no administrative overhead required.</span></span>

> [!NOTE]
> <span data-ttu-id="626a8-112">이 항목에서는 암호화에 사용되는 인증서에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-112">This topic discusses certificates used for encryption.</span></span> <span data-ttu-id="626a8-113">암호화의 경우 프라이빗 키의 보안이 항상 유지되고 암호화는 문서에 대한 신뢰를 암시하지 않으므로 자체 서명된 인증서로도 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-113">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span> <span data-ttu-id="626a8-114">자체 서명된 인증서는 인증 목적으로 사용하면 _안 됩니다_.</span><span class="sxs-lookup"><span data-stu-id="626a8-114">Self-signed certificates should _not_ be used for authentication purposes.</span></span> <span data-ttu-id="626a8-115">인증 목적에는 신뢰할 수 있는 CA(인증 기관)의 인증서를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-115">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="626a8-116">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="626a8-116">Prerequisites</span></span>

<span data-ttu-id="626a8-117">DSC 구성을 보호하는 데 사용되는 자격 증명을 적절히 암호화하려면 다음의 항목이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-117">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

- <span data-ttu-id="626a8-118">**인증서를 발급하고 배포할 여러 가지 방법**.</span><span class="sxs-lookup"><span data-stu-id="626a8-118">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="626a8-119">이 항목 및 해당 예제에서는 Active Directory 인증 기관을 사용 중이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-119">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="626a8-120">Active Directory 인증서 서비스에 대한 자세한 배경 정보는 [Active Directory 인증서 서비스 개요](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831740(v=ws.11))를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="626a8-120">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831740(v=ws.11)).</span></span>
- <span data-ttu-id="626a8-121">**대상 노드에 대한 관리 권한**.</span><span class="sxs-lookup"><span data-stu-id="626a8-121">**Administrative access to the target node or nodes**.</span></span>
- <span data-ttu-id="626a8-122">**각 대상 노드에 해당 개인 저장소에 저장된 암호화 가능 인증서가 있습니다**.</span><span class="sxs-lookup"><span data-stu-id="626a8-122">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="626a8-123">Windows PowerShell에서 저장소 경로는 Cert:\LocalMachine\My입니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-123">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="626a8-124">이 항목의 예제에서는 [기본 인증서 템플릿](/previous-versions/windows/it-pro/windows-server-2003/cc740061(v=ws.10))에 있는(다른 인증서 템플릿과 함께) "워크스테이션 인증" 템플릿을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-124">The examples in this topic use the "workstation authentication" template, which you can find (along with other certificate templates) at [Default Certificate Templates](/previous-versions/windows/it-pro/windows-server-2003/cc740061(v=ws.10)).</span></span>
- <span data-ttu-id="626a8-125">이 구성을 대상 노드 외의 컴퓨터에서 실행하려는 경우 **인증서의 공개 키를 내보내고**, 구성을 실행할 컴퓨터로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-125">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="626a8-126">**퍼블릭** 키만 내보내도록 합니다. 프라이빗 키는 안전하게 보관하세요.</span><span class="sxs-lookup"><span data-stu-id="626a8-126">Make sure that you export only the **public** key; keep the private key secure.</span></span>

> [!NOTE]
> <span data-ttu-id="626a8-127">암호화의 경우 스크립트 리소스에는 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-127">Script Resources have limitations when it comes to encryption.</span></span> <span data-ttu-id="626a8-128">자세한 내용은 [스크립트 리소스](../reference/resources/windows/scriptResource.md#known-limitations)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="626a8-128">For more information, see [Script Resource](../reference/resources/windows/scriptResource.md#known-limitations)</span></span>

## <a name="overall-process"></a><span data-ttu-id="626a8-129">전체 프로세스</span><span class="sxs-lookup"><span data-stu-id="626a8-129">Overall process</span></span>

 1. <span data-ttu-id="626a8-130">인증서, 키 및 지문을 설정하여, 각 대상 노드에 인증서의 복사본이 있고, 구성 컴퓨터에 공개 키와 지문이 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-130">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 1. <span data-ttu-id="626a8-131">공개 키의 경로와 지문을 포함하는 구성 데이터 블록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-131">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 1. <span data-ttu-id="626a8-132">로컬 구성 관리자가 인증서 및 지문을 사용하여 구성 데이터를 해독하도록 함으로써 대상 노드에 대해 원하는 구성을 정의하고 대상 노드에서 암호 해독을 설정하는 구성 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-132">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 1. <span data-ttu-id="626a8-133">로컬 구성 관리자 설정을 설정하고 DSC 구성을 시작할 구성을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-133">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![자격 증명 암호화의 프로세스 흐름](media/secureMOF/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="626a8-135">인증서 요구 사항</span><span class="sxs-lookup"><span data-stu-id="626a8-135">Certificate Requirements</span></span>

<span data-ttu-id="626a8-136">자격 증명 암호화를 적용하려면 DSC 구성을 작성하는 데 사용되는 컴퓨터에서 **신뢰할 수 있는**_대상 노드_ 에서 공개 키 인증서를 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-136">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span> <span data-ttu-id="626a8-137">이 공개 키 인증서를 DSC 자격 증명 암호화에 사용하려면 다음과 같은 특정 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-137">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>

1. <span data-ttu-id="626a8-138">**키 사용**:</span><span class="sxs-lookup"><span data-stu-id="626a8-138">**Key Usage**:</span></span>
   - <span data-ttu-id="626a8-139">포함해야 함: 'KeyEncipherment' 및 'DataEncipherment'.</span><span class="sxs-lookup"><span data-stu-id="626a8-139">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="626a8-140">포함하지 _않아야_ 함: 'Digital Signature'.</span><span class="sxs-lookup"><span data-stu-id="626a8-140">Should _not_ contain: 'Digital Signature'.</span></span>
1. <span data-ttu-id="626a8-141">**확장된 키 사용**:</span><span class="sxs-lookup"><span data-stu-id="626a8-141">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="626a8-142">포함해야 함: 문서 암호화(1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="626a8-142">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="626a8-143">포함하지 _않아야_ 함: 클라이언트 인증(1.3.6.1.5.5.7.3.2) 및 서버 인증(1.3.6.1.5.5.7.3.1).</span><span class="sxs-lookup"><span data-stu-id="626a8-143">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
1. <span data-ttu-id="626a8-144">인증서에 대한 프라이빗 키를 \*대상 노드_에서 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-144">The Private Key for the certificate is available on the \*Target Node_.</span></span>
1. <span data-ttu-id="626a8-145">인증서의 **공급자** 는 "Microsoft RSA SChannel Cryptographic Provider"여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-145">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="626a8-146">키 사용 ‘디지털 서명’ 또는 인증 EKU 중 하나를 포함하는 인증서를 사용할 수 있지만 이 경우 암호화 키가 오용되기 쉽고 공격에 취약해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-146">Although you can use a certificate containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="626a8-147">따라서 이러한 키 사용 및 EKU를 포함하지 않고 DSC 자격 증명을 보호하기 위해 특별히 만든 인증서를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-147">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>

<span data-ttu-id="626a8-148">이러한 기준을 충족하는 _대상 노드_ 의 모든 기존 인증서는 DSC 자격 증명을 보호하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-148">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="626a8-149">인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="626a8-149">Certificate creation</span></span>

<span data-ttu-id="626a8-150">필요한 암호화 인증서(퍼블릭-프라이빗 키 쌍)를 만들고 사용하기 위한 두 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-150">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="626a8-151">**대상 노드** 에서 만든 후 공개 키를 **제작 노드** 로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-151">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
1. <span data-ttu-id="626a8-152">**제작 노드** 에서 만든 후 전체 키 쌍을 **대상 노드** 로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-152">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="626a8-153">MOF의 자격 증명 암호 해독에 사용되는 프라이빗 키는 항상 대상 노드에 머무르므로 1번 방법을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-153">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>

### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="626a8-154">대상 노드에서 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="626a8-154">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="626a8-155">**대상 노드** 에서 프라이빗 키는 MOF의 암호를 해독하는 데 사용되기 때문에 보안을 유지해야 합니다. 이를 위한 가장 손쉬운 방법은 **대상 노드** 에서 프라이빗 키 인증서를 만들고, DSC 구성을 MOF 파일로 제작하는 데 사용하는 컴퓨터로 **퍼블릭 키 인증서** 를 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-155">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span> <span data-ttu-id="626a8-156">다음 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="626a8-156">The following example:</span></span>

1. <span data-ttu-id="626a8-157">**대상 노드** 에서 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-157">creates a certificate on the **Target node**</span></span>
1. <span data-ttu-id="626a8-158">**대상 노드** 에서 공개 키 인증서를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-158">exports the public key certificate on the **Target node**.</span></span>
1. <span data-ttu-id="626a8-159">공개 키 인증서를 **제작 노드** 에 있는 **내** 인증서 저장소로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-159">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="626a8-160">대상 노드: 인증서를 만들고 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-160">On the Target Node: create and export the certificate</span></span>

> <span data-ttu-id="626a8-161">대상 노드: Windows Server 2016 및 Windows 10</span><span class="sxs-lookup"><span data-stu-id="626a8-161">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="626a8-162">내보내고 나면 `DscPublicKey.cer`을 **제작 노드** 로 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-162">Once exported, the `DscPublicKey.cer` would need to be copied to the **Authoring Node**.</span></span>

> <span data-ttu-id="626a8-163">대상 노드: Windows Server 2012 R2/Windows 8.1 이하 버전</span><span class="sxs-lookup"><span data-stu-id="626a8-163">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

> [!WARNING]
> <span data-ttu-id="626a8-164">Windows 10 및 Windows Server 2016 이전의 Windows 운영 체제에서는 `New-SelfSignedCertificate` cmdlet이 **Type** 매개 변수를 지원하지 않으므로, 이 운영 체제에서는 이 인증서를 만들기 위한 대체 방법이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-164">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span> <span data-ttu-id="626a8-165">이 경우 `makecert.exe` 또는 `certutil.exe`를 사용해 인증서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-165">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span> <span data-ttu-id="626a8-166">이 예제에서는 인증서를 만드는 대체 방법으로 Microsoft 스크립트 센터의 [New-SelfSignedCertificateEx.ps1](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) 스크립트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-166">This example uses the [New-SelfSignedCertificateEx.ps1](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) script from Microsoft Script Center as an alternate way to create the certificate.</span></span> <span data-ttu-id="626a8-167">이 스크립트의 업데이트된 버전은 PowerShell 갤러리의 [PSPKI](https://www.powershellgallery.com/packages/PSPKI/) 모듈에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-167">An updated version of this script is available in the [PSPKI](https://www.powershellgallery.com/packages/PSPKI/) module in the PowerShell Gallery.</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="626a8-168">내보내고 나면 ```DscPublicKey.cer```을 **제작 노드** 로 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-168">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="626a8-169">제작 노드: 인증서의 공개 키를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-169">On the Authoring Node: import the cert's public key</span></span>

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="626a8-170">제작 노드에서 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="626a8-170">Creating the Certificate on the Authoring Node</span></span>

<span data-ttu-id="626a8-171">또는, 암호화 인증서를 **제작 노드** 에서 만들고, **프라이빗 키** 를 사용해 PFX 파일로 내보낸 다음 **대상 노드** 에서 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-171">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span> <span data-ttu-id="626a8-172">이것이 _Nano Server_ 에서 DSC 자격 증명 암호화를 구현하는 최신 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-172">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span> <span data-ttu-id="626a8-173">PFX는 암호로 보호되어 있지만 전송 중에도 보호 상태가 유지되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-173">Although the PFX is secured with a password it should be kept secure during transit.</span></span> <span data-ttu-id="626a8-174">다음 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="626a8-174">The following example:</span></span>

1. <span data-ttu-id="626a8-175">**제작 노드** 에서 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-175">creates a certificate on the **Authoring node**.</span></span>
1. <span data-ttu-id="626a8-176">**제작 노드** 에서 프라이빗 키를 포함하여 인증서를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-176">exports the certificate including the private key on the **Authoring node**.</span></span>
1. <span data-ttu-id="626a8-177">**제작 노드** 에서 프라이빗 키를 제거하고, 퍼블릭 키 인증서는 **내** 저장소에 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-177">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
1. <span data-ttu-id="626a8-178">프라이빗 키 인증서를 **대상 노드** 에 있는 My(개인) 인증서 저장소로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-178">imports the private key certificate into the My(Personal) certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="626a8-179">**대상 노드** 에서 신뢰할 수 있도록 루트 저장소에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-179">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="626a8-180">제작 노드: 인증서를 만들고 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-180">On the Authoring Node: create and export the certificate</span></span>

> <span data-ttu-id="626a8-181">대상 노드: Windows Server 2016 및 Windows 10</span><span class="sxs-lookup"><span data-stu-id="626a8-181">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the private key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

<span data-ttu-id="626a8-182">내보내고 나면 `DscPrivateKey.pfx`을 **대상 노드** 로 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-182">Once exported, the `DscPrivateKey.pfx` would need to be copied to the **Target Node**.</span></span>

> <span data-ttu-id="626a8-183">대상 노드: Windows Server 2012 R2/Windows 8.1 이하 버전</span><span class="sxs-lookup"><span data-stu-id="626a8-183">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

> [!WARNING]
> <span data-ttu-id="626a8-184">Windows 10 및 Windows Server 2016 이전의 Windows 운영 체제에서는 `New-SelfSignedCertificate` cmdlet이 **Type** 매개 변수를 지원하지 않으므로, 이 운영 체제에서는 이 인증서를 만들기 위한 대체 방법이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-184">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span> <span data-ttu-id="626a8-185">이 경우 `makecert.exe` 또는 `certutil.exe`를 사용해 인증서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-185">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span> <span data-ttu-id="626a8-186">대체 방법은 Microsoft 스크립트 센터에서 [New-SelfSignedCertificateEx.ps1](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) 스크립트를 다운로드한 후 이를 대신 사용해 인증서를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-186">An alternate method is to download the [New-SelfSignedCertificateEx.ps1](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) script from Microsoft Script Center and use it to create the certificate instead:</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="626a8-187">대상 노드: 인증서의 프라이빗 키를 신뢰할 수 있는 루트로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-187">On the Target Node: import the cert's private key as a trusted root</span></span>

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="626a8-188">구성 데이터</span><span class="sxs-lookup"><span data-stu-id="626a8-188">Configuration data</span></span>

<span data-ttu-id="626a8-189">구성 데이터 블록은 자격 증명을 암호화할지 여부, 암호화 방법 및 기타 정보에 대해 작업을 수행할 대상 노드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-189">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="626a8-190">구성 데이터 블록에 대한 자세한 내용은 [분리 및 환경 데이터 구성](../configurations/configData.md)를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-190">For more information on the configuration data block, see [Separating Configuration and Environment Data](../configurations/configData.md).</span></span>

<span data-ttu-id="626a8-191">자격 증명 암호화와 관련된 각 노드에 대해 구성할 수 있는 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-191">The elements that can be configured for each node that are related to credential encryption are:</span></span>

- <span data-ttu-id="626a8-192">**NodeName** - 자격 증명 암호화가 구성되는 대상 노드의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-192">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
- <span data-ttu-id="626a8-193">**PsDscAllowPlainTextPassword** - 암호화되지 않은 자격 증명을 이 노드로 전달할 수 있는지 여부입니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-193">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="626a8-194">이 요소는 사용하지 **않는 것이 좋습니다**.</span><span class="sxs-lookup"><span data-stu-id="626a8-194">This is **not recommended**.</span></span>
- <span data-ttu-id="626a8-195">**Thumbprint** - _대상 노드_ 의 DSC 구성에서 자격 증명의 암호를 해독하는 데 사용되는 인증서의 지문입니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-195">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="626a8-196">**이 인증서는 대상 노드의 로컬 컴퓨터 인증서 저장소에 있어야 합니다.**</span><span class="sxs-lookup"><span data-stu-id="626a8-196">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
- <span data-ttu-id="626a8-197">**CertificateFile** - _대상 노드_ 의 인증서를 암호화하는 데 사용할 인증서 파일(공개 키만 포함)입니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-197">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="626a8-198">DER로 인코딩된 바이너리 X.509 또는 Base-64로 인코딩된 X.509 형식 인증서 파일 중 하나여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-198">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="626a8-199">이 예제에서는 명명된 targetNode, 공개 키 인증서 파일 경로(명명된 targetNode.cer) 및 공개 키의 지문에 대해 작업을 수행할 대상 노드를 지정하는 구성 데이터 블록을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-199">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

```powershell
$ConfigData= @{
    AllNodes = @(
            @{
                # The name of the node we are describing
                NodeName = "targetNode"

                # The path to the .cer file containing the
                # public key of the Encryption Certificate
                # used to encrypt credentials for this node
                CertificateFile = "C:\publicKeys\targetNode.cer"


                # The thumbprint of the Encryption Certificate
                # used to decrypt the credentials on target node
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8"
            }
        )
    }
```

## <a name="configuration-script"></a><span data-ttu-id="626a8-200">구성 스크립트</span><span class="sxs-lookup"><span data-stu-id="626a8-200">Configuration script</span></span>

<span data-ttu-id="626a8-201">구성 스크립트 자체에서 `PsCredential` 매개 변수를 사용하여 자격 증명이 가능한 가장 짧은 시간 동안 저장되도록 하세요.</span><span class="sxs-lookup"><span data-stu-id="626a8-201">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="626a8-202">제공된 예제를 실행하면 DSC에서 자격 증명을 묻는 메시지를 표시한 다음, 구성 데이터 블록의 대상 노드와 연결된 CertificateFile을 사용하여 MOF 파일을 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-202">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="626a8-203">이 코드 예제에서는 보호되는 공유의 파일을 사용자에게 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-203">This code example copies a file from a share that is secured to a user.</span></span>

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
    )

    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }
    }
}
```

## <a name="setting-up-decryption"></a><span data-ttu-id="626a8-204">암호 해독 설정</span><span class="sxs-lookup"><span data-stu-id="626a8-204">Setting up decryption</span></span>

<span data-ttu-id="626a8-205">[Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)이 작동하기 위해서는 먼저 각 대상 노드의 로컬 구성 관리자에게 자격 증명 해독에 사용할 인증서를 알려줘야 합니다. 이때 CertificateID 리소스를 사용하여 인증서의 지문을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-205">Before [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate's thumbprint.</span></span> <span data-ttu-id="626a8-206">이 예제 함수는 적절한 로컬 인증서를 찾을 것입니다(사용하려는 인증서를 정확히 찾도록 사용자 지정해야 할 수도 있습니다.).</span><span class="sxs-lookup"><span data-stu-id="626a8-206">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

```powershell
# Get the certificate that works for encryption
function Get-LocalEncryptionCertificateThumbprint
{
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
        {
            return $_.Thumbprint
        }
    }
}
```

<span data-ttu-id="626a8-207">지문으로 인증서가 식별되면 해당 값을 사용하도록 구성 스크립트를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-207">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
    )

    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }

        LocalConfigurationManager
        {
             CertificateId = $node.Thumbprint
        }
    }
}
```

## <a name="running-the-configuration"></a><span data-ttu-id="626a8-208">구성 실행</span><span class="sxs-lookup"><span data-stu-id="626a8-208">Running the configuration</span></span>

<span data-ttu-id="626a8-209">이 시점에서 두 개의 파일을 출력하는 구성을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-209">At this point, you can run the configuration, which will output two files:</span></span>

- <span data-ttu-id="626a8-210">로컬 머신 저장소에 저장되어 있고 지문으로 식별되는 인증서를 사용하여 자격 증명을 해독하도록 로컬 구성 관리자를 구성하는 `*.meta.mof ` 파일.</span><span class="sxs-lookup"><span data-stu-id="626a8-210">A `*.meta.mof `file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span>
  <span data-ttu-id="626a8-211">[Set-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/Set-DscLocalConfigurationManager)가 `*.meta.mof ` 파일을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-211">[Set-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/Set-DscLocalConfigurationManager) applies the `*.meta.mof `file.</span></span>
- <span data-ttu-id="626a8-212">실제로 구성을 적용하는 MOF 파일.</span><span class="sxs-lookup"><span data-stu-id="626a8-212">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="626a8-213">Start-DscConfiguration이 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-213">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="626a8-214">다음 명령들은 해당 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-214">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="626a8-215">이 예제에서는 대상 노드에 DSC 구성을 밀어넣습니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-215">This example would push the DSC configuration to the target node.</span></span> <span data-ttu-id="626a8-216">DSC 끌어오기 서버를 사용할 수 있는 경우 이 서버를 사용하여 DSC 구성을 적용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-216">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="626a8-217">DSC 끌어오기 서버를 사용하여 DSC 구성을 적용하는 방법에 대한 자세한 내용은 [DSC 끌어오기 클라이언트 설정](pullClient.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="626a8-217">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="626a8-218">자격 증명 암호화 모듈 예제</span><span class="sxs-lookup"><span data-stu-id="626a8-218">Credential Encryption Module Example</span></span>

<span data-ttu-id="626a8-219">다음은 이러한 모든 단계와 공개 키를 내보내고 복사하는 도우미 cmdlet을 통합하는 전체 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="626a8-219">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
    )

    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }

        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)

    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"

    $ConfigData=    @{
        AllNodes = @(
                        @{
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration")

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
}

#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)

    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
        $certificates = dir Cert:\LocalMachine\my

        $certificates | %{
                    # Verify the certificate is for Encryption and valid
            if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
            {
                # Create the folder to hold the exported public key
                $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                if (! (Test-Path $folder))
                {
                    md $folder | Out-Null
                }

                # Export the public key to a well known location
                $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer")

                # Return the thumbprint, and exported certificate path
                return @($_.Thumbprint,$certPath);
            }
        }
    }

    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}

Start-CredentialEncryptionExample
```
