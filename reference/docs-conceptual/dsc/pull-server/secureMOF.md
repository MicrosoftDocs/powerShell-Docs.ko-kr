---
ms.date: 10/31/2017
keywords: dsc,powershell,configuration,setup
title: MOF 파일 보안
ms.openlocfilehash: ab03db8bf4ed7d412691ae87fd12da5131607886
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278473"
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="61874-103">MOF 파일 보안</span><span class="sxs-lookup"><span data-stu-id="61874-103">Securing the MOF File</span></span>

> <span data-ttu-id="61874-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="61874-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="61874-105">DSC는 LCM(로컬 구성 관리자)가 원하는 최종 상태를 구현하는 MOF 파일에 저장된 정보를 적용하여 서버 노드의 구성을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-105">DSC manages the configuration of server nodes by applying information stored in a MOF file, where the Local Configuration Manager (LCM) implements the desired end state.</span></span> <span data-ttu-id="61874-106">이 파일은 구성의 세부 정보를 포함하므로 안전하게 보관해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-106">Because this file contains the details of the configuration, it's important to keep it secure.</span></span> <span data-ttu-id="61874-107">이 항목은 대상 노드가 파일을 암호화했는지 확인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-107">This topic describes how to ensure the target node has encrypted the file.</span></span>

<span data-ttu-id="61874-108">PowerShell 버전 5.0부터 전체 MOF 파일은 `Start-DSCConfiguration` cmdlet을 사용하여 노드에 적용될 때 기본적으로 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="61874-108">Beginning with PowerShell version 5.0, the entire MOF file is encrypted by default when it is applied to the node using the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="61874-109">이 문서에 설명된 프로세스는 대상 노드가 다운로드한 구성을 시스템에 적용하기 전에 해독하고 읽을 수 있도록 하기 위해 인증서가 관리되지 않는 경우 풀 서비스 프로토콜을 사용하여 솔루션을 구현할 때만 필요합니다(예: Windows Server에서 사용할 수 있는 풀 서비스).</span><span class="sxs-lookup"><span data-stu-id="61874-109">The process described in this article is required only when implementing a solution using the pull service protocol if certificates are not managed, to ensure configurations downloaded by the target node can be decrypted and read by the system before they are applied (for example, the pull service available in Windows Server).</span></span> <span data-ttu-id="61874-110">[Azure 자동화 DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview)에 등록된 노드에는 관리 오버 헤드가 필요 없는 서비스를 사용하여 자동으로 인증서가 설치되고 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="61874-110">Nodes registered to [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) will automatically have certificates installed and managed by the service with no administrative overhead required.</span></span>

> [!NOTE]
> <span data-ttu-id="61874-111">이 항목에서는 암호화에 사용되는 인증서에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-111">This topic discusses certificates used for encryption.</span></span> <span data-ttu-id="61874-112">암호화의 경우 프라이빗 키의 보안이 항상 유지되고 암호화는 문서에 대한 신뢰를 암시하지 않으므로 자체 서명된 인증서로도 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-112">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span> <span data-ttu-id="61874-113">자체 서명된 인증서는 인증 목적으로 사용하면 *안 됩니다*.</span><span class="sxs-lookup"><span data-stu-id="61874-113">Self-signed certificates should *not* be used for authentication purposes.</span></span> <span data-ttu-id="61874-114">인증 목적에는 신뢰할 수 있는 CA(인증 기관)의 인증서를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-114">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="61874-115">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="61874-115">Prerequisites</span></span>

<span data-ttu-id="61874-116">DSC 구성을 보호하는 데 사용되는 자격 증명을 적절히 암호화하려면 다음의 항목이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-116">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

- <span data-ttu-id="61874-117">**인증서를 발급하고 배포할 여러 가지 방법**.</span><span class="sxs-lookup"><span data-stu-id="61874-117">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="61874-118">이 항목 및 해당 예제에서는 Active Directory 인증 기관을 사용 중이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-118">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="61874-119">Active Directory 인증서 서비스에 대한 자세한 배경 정보를 알려면 [Active Directory 인증서 서비스 개요](https://technet.microsoft.com/library/hh831740.aspx) 및 [Windows Server 2008의 Active Directory 인증서 서비스](https://technet.microsoft.com/windowsserver/dd448615.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="61874-119">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
- <span data-ttu-id="61874-120">**대상 노드에 대한 관리 권한**.</span><span class="sxs-lookup"><span data-stu-id="61874-120">**Administrative access to the target node or nodes**.</span></span>
- <span data-ttu-id="61874-121">**각 대상 노드에 해당 개인 저장소에 저장된 암호화 가능 인증서가 있습니다**.</span><span class="sxs-lookup"><span data-stu-id="61874-121">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="61874-122">Windows PowerShell에서 저장소 경로는 Cert:\LocalMachine\My입니다.</span><span class="sxs-lookup"><span data-stu-id="61874-122">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="61874-123">이 항목의 예제에서는 [기본 인증서 템플릿](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx)에 있는(다른 인증서 템플릿과 함께) "워크스테이션 인증" 템플릿을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-123">The examples in this topic use the "workstation authentication" template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
- <span data-ttu-id="61874-124">이 구성을 대상 노드 외의 컴퓨터에서 실행하려는 경우 **인증서의 공개 키를 내보내고**, 구성을 실행할 컴퓨터로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="61874-124">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="61874-125">**퍼블릭** 키만 내보내도록 합니다. 프라이빗 키는 안전하게 보관하세요.</span><span class="sxs-lookup"><span data-stu-id="61874-125">Make sure that you export only the **public** key; keep the private key secure.</span></span>

## <a name="overall-process"></a><span data-ttu-id="61874-126">전체 프로세스</span><span class="sxs-lookup"><span data-stu-id="61874-126">Overall process</span></span>

 1. <span data-ttu-id="61874-127">인증서, 키 및 지문을 설정하여, 각 대상 노드에 인증서의 복사본이 있고, 구성 컴퓨터에 공개 키와 지문이 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-127">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 2. <span data-ttu-id="61874-128">공개 키의 경로와 지문을 포함하는 구성 데이터 블록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="61874-128">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 3. <span data-ttu-id="61874-129">로컬 구성 관리자가 인증서 및 지문을 사용하여 구성 데이터를 해독하도록 함으로써 대상 노드에 대해 원하는 구성을 정의하고 대상 노드에서 암호 해독을 설정하는 구성 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="61874-129">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 4. <span data-ttu-id="61874-130">로컬 구성 관리자 설정을 설정하고 DSC 구성을 시작할 구성을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-130">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![Diagram1](media/secureMOF/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="61874-132">인증서 요구 사항</span><span class="sxs-lookup"><span data-stu-id="61874-132">Certificate Requirements</span></span>

<span data-ttu-id="61874-133">자격 증명 암호화를 적용하려면 DSC 구성을 작성하는 데 사용되는 컴퓨터에서 _신뢰할 수 있는_**대상 노드**에서 공개 키 인증서를 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-133">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span> <span data-ttu-id="61874-134">이 공개 키 인증서를 DSC 자격 증명 암호화에 사용하려면 다음과 같은 특정 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-134">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>

1. <span data-ttu-id="61874-135">**키 사용**:</span><span class="sxs-lookup"><span data-stu-id="61874-135">**Key Usage**:</span></span>
   - <span data-ttu-id="61874-136">'KeyEncipherment' 및 'DataEncipherment'를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-136">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="61874-137">'디지털 서명'을 포함하지 _않아야_ 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-137">Should _not_ contain: 'Digital Signature'.</span></span>
2. <span data-ttu-id="61874-138">**확장된 키 사용**:</span><span class="sxs-lookup"><span data-stu-id="61874-138">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="61874-139">문서 암호화(1.3.6.1.4.1.311.80.1)를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-139">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="61874-140">클라이언트 인증(1.3.6.1.5.5.7.3.2) 및 서버 인증(1.3.6.1.5.5.7.3.1)을 포함하지 _않아야_ 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-140">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
3. <span data-ttu-id="61874-141">인증서에 대한 프라이빗 키를 \*대상 노드_에서 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-141">The Private Key for the certificate is available on the \*Target Node_.</span></span>
4. <span data-ttu-id="61874-142">인증서의 **공급자**는 "Microsoft RSA SChannel Cryptographic Provider"여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-142">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="61874-143">키 사용 '디지털 서명' 또는 인증 EKU 중 하나를 포함하는 인증서를 사용할 수 있지만 이 경우 암호화 키가 오용되기 쉽고 공격에 취약해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61874-143">Although you can use a certificate with containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="61874-144">따라서 이러한 키 사용 및 EKU를 포함하지 않고 DSC 자격 증명을 보호하기 위해 특별히 만든 인증서를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="61874-144">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>

<span data-ttu-id="61874-145">이러한 기준을 충족하는 _대상 노드_의 모든 기존 인증서는 DSC 자격 증명을 보호하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61874-145">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="61874-146">인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="61874-146">Certificate creation</span></span>

<span data-ttu-id="61874-147">필요한 암호화 인증서(퍼블릭-프라이빗 키 쌍)를 만들고 사용하기 위한 두 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61874-147">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="61874-148">**대상 노드**에서 만든 후 공개 키를 **제작 노드**로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="61874-148">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
2. <span data-ttu-id="61874-149">**제작 노드**에서 만든 후 전체 키 쌍을 **대상 노드**로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="61874-149">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="61874-150">MOF의 자격 증명 암호 해독에 사용되는 프라이빗 키는 항상 대상 노드에 머무르므로 1번 방법을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="61874-150">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>

### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="61874-151">대상 노드에서 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="61874-151">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="61874-152">**대상 노드**에서 프라이빗 키는 MOF의 암호를 해독하는 데 사용되기 때문에 보안을 유지해야 합니다. 이를 위한 가장 손쉬운 방법은 **대상 노드**에서 프라이빗 키 인증서를 만들고, DSC 구성을 MOF 파일로 제작하는 데 사용하는 컴퓨터로 **퍼블릭 키 인증서**를 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="61874-152">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span> <span data-ttu-id="61874-153">다음 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="61874-153">The following example:</span></span>

1. <span data-ttu-id="61874-154">**대상 노드**에서 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="61874-154">creates a certificate on the **Target node**</span></span>
2. <span data-ttu-id="61874-155">**대상 노드**에서 공개 키 인증서를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="61874-155">exports the public key certificate on the **Target node**.</span></span>
3. <span data-ttu-id="61874-156">공개 키 인증서를 **제작 노드**에 있는 **내** 인증서 저장소로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="61874-156">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="61874-157">대상 노드: 인증서를 만들고 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="61874-157">On the Target Node: create and export the certificate</span></span>

> <span data-ttu-id="61874-158">대상 노드: Windows Server 2016 및 Windows 10</span><span class="sxs-lookup"><span data-stu-id="61874-158">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="61874-159">내보내고 나면 `DscPublicKey.cer`을 **제작 노드**로 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-159">Once exported, the `DscPublicKey.cer` would need to be copied to the **Authoring Node**.</span></span>

> <span data-ttu-id="61874-160">대상 노드: Windows Server 2012 R2/Windows 8.1 이하 버전</span><span class="sxs-lookup"><span data-stu-id="61874-160">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>
> [!WARNING]
> <span data-ttu-id="61874-161">Windows 10 및 Windows Server 2016 이전의 Windows 운영 체제에서는 `New-SelfSignedCertificate` cmdlet이 **Type** 매개 변수를 지원하지 않으므로, 이 운영 체제에서는 이 인증서를 만들기 위한 대체 방법이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-161">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span> <span data-ttu-id="61874-162">이 경우 `makecert.exe` 또는 `certutil.exe`를 사용해 인증서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61874-162">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span> <span data-ttu-id="61874-163">대체 방법은 [Microsoft 스크립트 센터에서 New-SelfSignedCertificateEx.ps1 스크립트를 다운로드](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6)한 후 이를 대신 사용해 인증서를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="61874-163">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

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

<span data-ttu-id="61874-164">내보내고 나면 ```DscPublicKey.cer```을 **제작 노드**로 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-164">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="61874-165">제작 노드: 인증서의 공개 키를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="61874-165">On the Authoring Node: import the cert's public key</span></span>

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="61874-166">제작 노드에서 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="61874-166">Creating the Certificate on the Authoring Node</span></span>

<span data-ttu-id="61874-167">또는, 암호화 인증서를 **제작 노드**에서 만들고, **프라이빗 키**를 사용해 PFX 파일로 내보낸 다음 **대상 노드**에서 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61874-167">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span> <span data-ttu-id="61874-168">이것이 _Nano Server_에서 DSC 자격 증명 암호화를 구현하는 최신 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="61874-168">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span> <span data-ttu-id="61874-169">PFX는 암호로 보호되어 있지만 전송 중에도 보호 상태가 유지되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-169">Although the PFX is secured with a password it should be kept secure during transit.</span></span> <span data-ttu-id="61874-170">다음 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="61874-170">The following example:</span></span>

1. <span data-ttu-id="61874-171">**제작 노드**에서 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="61874-171">creates a certificate on the **Authoring node**.</span></span>
2. <span data-ttu-id="61874-172">**제작 노드**에서 프라이빗 키를 포함하여 인증서를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="61874-172">exports the certificate including the private key on the **Authoring node**.</span></span>
3. <span data-ttu-id="61874-173">**제작 노드**에서 프라이빗 키를 제거하고, 퍼블릭 키 인증서는 **내** 저장소에 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-173">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
4. <span data-ttu-id="61874-174">프라이빗 키 인증서를 **대상 노드**에 있는 My(개인) 인증서 저장소로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="61874-174">imports the private key certificate into the My(Personal) certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="61874-175">**대상 노드**에서 신뢰할 수 있도록 루트 저장소에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-175">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="61874-176">제작 노드: 인증서를 만들고 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="61874-176">On the Authoring Node: create and export the certificate</span></span>

> <span data-ttu-id="61874-177">대상 노드: Windows Server 2016 및 Windows 10</span><span class="sxs-lookup"><span data-stu-id="61874-177">Target Node: Windows Server 2016 and Windows 10</span></span>

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

<span data-ttu-id="61874-178">내보내고 나면 `DscPrivateKey.pfx`을 **대상 노드**로 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-178">Once exported, the `DscPrivateKey.pfx` would need to be copied to the **Target Node**.</span></span>

> <span data-ttu-id="61874-179">대상 노드: Windows Server 2012 R2/Windows 8.1 이하 버전</span><span class="sxs-lookup"><span data-stu-id="61874-179">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>
> [!WARNING]
> <span data-ttu-id="61874-180">Windows 10 및 Windows Server 2016 이전의 Windows 운영 체제에서는 `New-SelfSignedCertificate` cmdlet이 **Type** 매개 변수를 지원하지 않으므로, 이 운영 체제에서는 이 인증서를 만들기 위한 대체 방법이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-180">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span> <span data-ttu-id="61874-181">이 경우 `makecert.exe` 또는 `certutil.exe`를 사용해 인증서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61874-181">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span> <span data-ttu-id="61874-182">대체 방법은 [Microsoft 스크립트 센터에서 New-SelfSignedCertificateEx.ps1 스크립트를 다운로드](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6)한 후 이를 대신 사용해 인증서를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="61874-182">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

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

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="61874-183">대상 노드: 인증서의 프라이빗 키를 신뢰할 수 있는 루트로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="61874-183">On the Target Node: import the cert's private key as a trusted root</span></span>

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="61874-184">구성 데이터</span><span class="sxs-lookup"><span data-stu-id="61874-184">Configuration data</span></span>

<span data-ttu-id="61874-185">구성 데이터 블록은 자격 증명을 암호화할지 여부, 암호화 방법 및 기타 정보에 대해 작업을 수행할 대상 노드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-185">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="61874-186">구성 데이터 블록에 대한 자세한 내용은 [분리 및 환경 데이터 구성](../configurations/configData.md)를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-186">For more information on the configuration data block, see [Separating Configuration and Environment Data](../configurations/configData.md).</span></span>

<span data-ttu-id="61874-187">자격 증명 암호화와 관련된 각 노드에 대해 구성할 수 있는 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="61874-187">The elements that can be configured for each node that are related to credential encryption are:</span></span>

- <span data-ttu-id="61874-188">**NodeName** - 자격 증명 암호화가 구성되는 대상 노드의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="61874-188">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
- <span data-ttu-id="61874-189">**PsDscAllowPlainTextPassword** - 암호화되지 않은 자격 증명을 이 노드로 전달할 수 있는지 여부입니다.</span><span class="sxs-lookup"><span data-stu-id="61874-189">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="61874-190">이 요소는 사용하지 **않는 것이 좋습니다**.</span><span class="sxs-lookup"><span data-stu-id="61874-190">This is **not recommended**.</span></span>
- <span data-ttu-id="61874-191">**Thumbprint** - _대상 노드_의 DSC 구성에서 자격 증명의 암호를 해독하는 데 사용되는 인증서의 지문입니다.</span><span class="sxs-lookup"><span data-stu-id="61874-191">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="61874-192">**이 인증서는 대상 노드의 로컬 컴퓨터 인증서 저장소에 있어야 합니다.**</span><span class="sxs-lookup"><span data-stu-id="61874-192">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
- <span data-ttu-id="61874-193">**CertificateFile** - _대상 노드_의 인증서를 암호화하는 데 사용할 인증서 파일(공개 키만 포함)입니다.</span><span class="sxs-lookup"><span data-stu-id="61874-193">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="61874-194">DER로 인코딩된 바이너리 X.509 또는 Base-64로 인코딩된 X.509 형식 인증서 파일 중 하나여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-194">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="61874-195">이 예제에서는 명명된 targetNode, 공개 키 인증서 파일 경로(명명된 targetNode.cer) 및 공개 키의 지문에 대해 작업을 수행할 대상 노드를 지정하는 구성 데이터 블록을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="61874-195">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

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
            };
        );
    }
```

## <a name="configuration-script"></a><span data-ttu-id="61874-196">구성 스크립트</span><span class="sxs-lookup"><span data-stu-id="61874-196">Configuration script</span></span>

<span data-ttu-id="61874-197">구성 스크립트 자체에서 `PsCredential` 매개 변수를 사용하여 자격 증명이 가능한 가장 짧은 시간 동안 저장되도록 하세요.</span><span class="sxs-lookup"><span data-stu-id="61874-197">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="61874-198">제공된 예제를 실행하면 DSC에서 자격 증명을 묻는 메시지를 표시한 다음, 구성 데이터 블록의 대상 노드와 연결된 CertificateFile을 사용하여 MOF 파일을 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-198">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="61874-199">이 코드 예제에서는 보호되는 공유의 파일을 사용자에게 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-199">This code example copies a file from a share that is secured to a user.</span></span>

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

## <a name="setting-up-decryption"></a><span data-ttu-id="61874-200">암호 해독 설정</span><span class="sxs-lookup"><span data-stu-id="61874-200">Setting up decryption</span></span>

<span data-ttu-id="61874-201">[`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx)이 작동할 수 있도록 하려면 먼저 각 대상 노드의 로컬 Configuration Manager에게 인증서의 지문 확인을 위해 CertificateID 리소스를 사용하여 인증서를 해독하는 데 사용할 인증서를 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="61874-201">Before [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate's thumbprint.</span></span> <span data-ttu-id="61874-202">이 예제 함수는 적절한 로컬 인증서를 찾을 것입니다(사용하려는 인증서를 정확히 찾도록 사용자 지정해야 할 수도 있습니다.).</span><span class="sxs-lookup"><span data-stu-id="61874-202">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

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

<span data-ttu-id="61874-203">지문으로 인증서가 식별되면 해당 값을 사용하도록 구성 스크립트를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61874-203">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

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

## <a name="running-the-configuration"></a><span data-ttu-id="61874-204">구성 실행</span><span class="sxs-lookup"><span data-stu-id="61874-204">Running the configuration</span></span>

<span data-ttu-id="61874-205">이 시점에서 두 개의 파일을 출력하는 구성을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61874-205">At this point, you can run the configuration, which will output two files:</span></span>

- <span data-ttu-id="61874-206">로컬 컴퓨터 저장소에 저장되어 있고 지문으로 식별되는 인증서를 사용하여 자격 증명을 해독하도록 로컬 구성 관리자를 구성하는 \*.meta.mof 파일.</span><span class="sxs-lookup"><span data-stu-id="61874-206">A \*.meta.mof file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span>
  <span data-ttu-id="61874-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx)가 \*.meta.mof 파일을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) applies the \*.meta.mof file.</span></span>
- <span data-ttu-id="61874-208">실제로 구성을 적용하는 MOF 파일.</span><span class="sxs-lookup"><span data-stu-id="61874-208">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="61874-209">Start-DscConfiguration이 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-209">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="61874-210">다음 명령들은 해당 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="61874-210">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="61874-211">이 예제에서는 대상 노드에 DSC 구성을 밀어넣습니다.</span><span class="sxs-lookup"><span data-stu-id="61874-211">This example would push the DSC configuration to the target node.</span></span> <span data-ttu-id="61874-212">DSC 끌어오기 서버를 사용할 수 있는 경우 이 서버를 사용하여 DSC 구성을 적용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61874-212">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="61874-213">DSC 끌어오기 서버를 사용하여 DSC 구성을 적용하는 방법에 대한 자세한 내용은 [DSC 끌어오기 클라이언트 설정](pullClient.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="61874-213">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="61874-214">자격 증명 암호화 모듈 예제</span><span class="sxs-lookup"><span data-stu-id="61874-214">Credential Encryption Module Example</span></span>

<span data-ttu-id="61874-215">다음은 이러한 모든 단계와 공개 키를 내보내고 복사하는 도우미 cmdlet을 통합하는 전체 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="61874-215">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

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
