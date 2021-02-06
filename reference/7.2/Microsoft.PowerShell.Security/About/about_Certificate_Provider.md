---
description: 인증서
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/about/about_certificate_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 인증서 공급자
ms.openlocfilehash: 78536024e8e953a70485a7d950b187ba9a3fc405
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605002"
---
# <a name="certificate-provider"></a><span data-ttu-id="aea52-103">인증서 공급자</span><span class="sxs-lookup"><span data-stu-id="aea52-103">Certificate Provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="aea52-104">공급자 이름</span><span class="sxs-lookup"><span data-stu-id="aea52-104">Provider name</span></span>

<span data-ttu-id="aea52-105">인증서</span><span class="sxs-lookup"><span data-stu-id="aea52-105">Certificate</span></span>

## <a name="drives"></a><span data-ttu-id="aea52-106">드라이브</span><span class="sxs-lookup"><span data-stu-id="aea52-106">Drives</span></span>

`Cert:`

## <a name="capabilities"></a><span data-ttu-id="aea52-107">기능</span><span class="sxs-lookup"><span data-stu-id="aea52-107">Capabilities</span></span>

<span data-ttu-id="aea52-108">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="aea52-108">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="aea52-109">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="aea52-109">Short description</span></span>

<span data-ttu-id="aea52-110">PowerShell에서 x.509 인증서 저장소 및 인증서에 대 한 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-110">Provides access to X.509 certificate stores and certificates in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="aea52-111">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="aea52-111">Detailed description</span></span>

<span data-ttu-id="aea52-112">PowerShell **인증서** 공급자를 통해 powershell에서 인증서 및 인증서 저장소를 가져오고 추가, 변경 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-112">The PowerShell **Certificate** provider lets you get, add, change, clear, and delete certificates and certificate stores in PowerShell.</span></span>

<span data-ttu-id="aea52-113">**인증서** 드라이브는 컴퓨터의 인증서 저장소 및 인증서를 포함 하는 계층적 네임 스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-113">The **Certificate** drive is a hierarchical namespace containing the certificate stores and certificates on your computer.</span></span>

<span data-ttu-id="aea52-114">**인증서** 공급자는이 문서에서 설명 하는 다음과 같은 cmdlet을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-114">The **Certificate** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="aea52-115">Get-Location</span><span class="sxs-lookup"><span data-stu-id="aea52-115">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="aea52-116">Set-Location</span><span class="sxs-lookup"><span data-stu-id="aea52-116">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="aea52-117">Get-Item</span><span class="sxs-lookup"><span data-stu-id="aea52-117">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="aea52-118">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="aea52-118">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="aea52-119">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="aea52-119">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="aea52-120">Move-Item</span><span class="sxs-lookup"><span data-stu-id="aea52-120">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="aea52-121">New-Item</span><span class="sxs-lookup"><span data-stu-id="aea52-121">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="aea52-122">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="aea52-122">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="aea52-123">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="aea52-123">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="aea52-124">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="aea52-124">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="aea52-125">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="aea52-125">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="aea52-126">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="aea52-126">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [<span data-ttu-id="aea52-127">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="aea52-127">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="aea52-128">이 공급자가 노출 하는 형식</span><span class="sxs-lookup"><span data-stu-id="aea52-128">Types exposed by this provider</span></span>

<span data-ttu-id="aea52-129">인증서 드라이브는 다음 형식을 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-129">The Certificate drive exposes the following types.</span></span>

- <span data-ttu-id="aea52-130">저장소 위치 (Microsoft.powershell.commands.x509storelocation)-현재 사용자와 모든 사용자에 대 한 인증서를 그룹화 하는 상위 수준의 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-130">Store locations (Microsoft.PowerShell.Commands.X509StoreLocation), which are high-level containers that group the certificates for the current user and for all users.</span></span> <span data-ttu-id="aea52-131">각 시스템에는 CurrentUser 및 LocalMachine(모든 사용자) 저장소 위치가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-131">Each system has a CurrentUser and LocalMachine (all users) store location.</span></span>

- <span data-ttu-id="aea52-132">인증서 저장소 (System.security.cryptography.x509certificates.x509certificate2. X509Store)-인증서를 저장 하 고 관리 하는 물리적 저장소입니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-132">Certificates stores (System.Security.Cryptography.X509Certificates.X509Store), which are physical stores in which certificates are saved and managed.</span></span>

- <span data-ttu-id="aea52-133">X.509 **system.security.cryptography.x509certificates.x509certificate2. X509Certificate2** 인증서 이며, 각 인증서는 컴퓨터의 x.509 인증서를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-133">X.509 **System.Security.Cryptography.X509Certificates.X509Certificate2** certificates, each of which represent an X.509 certificate on the computer.</span></span>
  <span data-ttu-id="aea52-134">인증서는 지문으로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-134">Certificates are identified by their thumbprints.</span></span>

## <a name="navigating-the-certificate-drive"></a><span data-ttu-id="aea52-135">인증서 드라이브 탐색</span><span class="sxs-lookup"><span data-stu-id="aea52-135">Navigating the Certificate drive</span></span>

<span data-ttu-id="aea52-136">**인증서** 공급자는 인증서 네임 스페이스를 `Cert:` PowerShell의 드라이브로 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-136">The **Certificate** provider exposes the certificate namespace as the `Cert:` drive in PowerShell.</span></span> <span data-ttu-id="aea52-137">이 명령은 명령을 사용 하 여 `Set-Location` 현재 위치를 LocalMachine 저장소 위치의 루트 인증서 저장소로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-137">This command uses the `Set-Location` command to change the current location to the Root certificate store in the LocalMachine store location.</span></span> <span data-ttu-id="aea52-138">백슬래시 ( \\ ) 또는 슬래시 (/)를 사용 하 여 드라이브의 수준을 표시 `Cert:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-138">Use a backslash (\\) or a forward slash (/) to indicate a level of the `Cert:` drive.</span></span>

```powershell
Set-Location Cert:
```

<span data-ttu-id="aea52-139">다른 PowerShell 드라이브에서 인증서 공급자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-139">You can also work with the certificate provider from any other PowerShell drive.</span></span> <span data-ttu-id="aea52-140">다른 위치에서 별칭을 참조 하려면 `Cert:` 경로에 드라이브 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-140">To reference an alias from another location, use the `Cert:` drive name in the path.</span></span>

```powershell
PS Cert:\> Set-Location -Path LocalMachine\Root
```

<span data-ttu-id="aea52-141">파일 시스템 드라이브로 돌아가려면 드라이브 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-141">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="aea52-142">예를 들어 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-142">For example, type:</span></span>

```powershell
Set-Location C:
```

> [!NOTE]
> <span data-ttu-id="aea52-143">PowerShell은 별칭을 사용 하 여 공급자 경로 작업을 수행할 수 있는 친숙 한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-143">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="aea52-144">`dir`및 등의 명령은 `ls` 이제 [Get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)에 대 한 별칭입니다 `cd` .는 [집합 위치](xref:Microsoft.PowerShell.Management.Set-Location)에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-144">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span>
> <span data-ttu-id="aea52-145">및 `pwd` 은 [(는) 위치](xref:Microsoft.PowerShell.Management.Get-Location)에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-145">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="displaying-the-contents-of-the-cert-drive"></a><span data-ttu-id="aea52-146">Cert: 드라이브의 내용 표시</span><span class="sxs-lookup"><span data-stu-id="aea52-146">Displaying the Contents of the Cert: drive</span></span>

<span data-ttu-id="aea52-147">이 명령은 cmdlet을 사용 하 여 `Get-ChildItem` CurrentUser 인증서 저장소 위치에 인증서 저장소를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-147">This command uses the `Get-ChildItem` cmdlet to display the certificate stores in the CurrentUser certificate store location.</span></span>

<span data-ttu-id="aea52-148">드라이브에 없으면 `Cert:` 절대 경로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-148">If you are not in the `Cert:` drive, use an absolute path.</span></span>

```powershell
PS Cert:\CurrentUser\> Get-ChildItem
```

### <a name="displaying-certificate-properties-within-the-cert-drive"></a><span data-ttu-id="aea52-149">Cert: 드라이브 내 인증서 속성 표시</span><span class="sxs-lookup"><span data-stu-id="aea52-149">Displaying certificate properties within the Cert: drive</span></span>

<span data-ttu-id="aea52-150">이 예제에서는를 사용 하 여 인증서를 가져온 `Get-Item` 다음 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-150">This example gets a certificate with `Get-Item` and stores it in a variable.</span></span>
<span data-ttu-id="aea52-151">이 예에서는를 사용 하 여 새 인증서 스크립트 속성 (**DnsNameList**, **EnhancedKeyUsageList**, **SendAsTrustedIssuer**)을 보여 줍니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="aea52-151">The example shows the new certificate script properties (**DnsNameList**, **EnhancedKeyUsageList**, **SendAsTrustedIssuer**) using `Select-Object`.</span></span>

```powershell
$c = Get-Item cert:\LocalMachine\My\52A149D0393CE8A8D4AF0B172ED667A9E3A1F44E
$c | Format-List DnsNameList, EnhancedKeyUsageList, SendAsTrustedIssuer
```

```output
DnsNameList          : {SERVER01.contoso.com}
EnhancedKeyUsageList : {WiFi-Machine (1.3.6.1.4.1.311.42.2.6),
                       Client Authentication (1.3.6.1.5.5.7.3.2)}
SendAsTrustedIssuer  : False
```

### <a name="find-all-codesigning-certificates"></a><span data-ttu-id="aea52-152">모든 코드 서명 인증서 찾기</span><span class="sxs-lookup"><span data-stu-id="aea52-152">Find all CodeSigning certificates</span></span>

<span data-ttu-id="aea52-153">이 명령은 cmdlet의 **Codesigningcert** 및 **재귀** 매개 변수를 사용 하 여 `Get-ChildItem` 코드 서명 기관이 있는 컴퓨터의 모든 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-153">This command uses the **CodeSigningCert** and **Recurse** parameters of the `Get-ChildItem` cmdlet to get all of the certificates on the computer that have code-signing authority.</span></span>

```powershell
Get-ChildItem -Path cert: -CodeSigningCert -Recurse
```

### <a name="find-expired-certificates"></a><span data-ttu-id="aea52-154">만료 된 인증서 찾기</span><span class="sxs-lookup"><span data-stu-id="aea52-154">Find expired certificates</span></span>

<span data-ttu-id="aea52-155">이 명령은 cmdlet의 **ExpiringInDays** 매개 변수를 사용 하 여 `Get-ChildItem` 다음 30 일 내에 만료 되는 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-155">This command uses the **ExpiringInDays** parameter of the `Get-ChildItem` cmdlet to get certificates that will expire within the next 30 days.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine\WebHosting -ExpiringInDays 30
```

### <a name="find-server-ssl-certificates"></a><span data-ttu-id="aea52-156">서버 SSL 인증서 찾기</span><span class="sxs-lookup"><span data-stu-id="aea52-156">Find Server SSL Certificates</span></span>

<span data-ttu-id="aea52-157">이 명령은 cmdlet의 **Sslserverauthentication** 매개 변수를 사용 하 여 `Get-ChildItem` My 및 webhosting 저장소에 있는 모든 서버 SSL 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-157">This command uses the **SSLServerAuthentication** parameter of the `Get-ChildItem` cmdlet to get all Server SSL Certificates in the My and WebHosting stores.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine\My, cert:\LocalMachine\WebHosting `
  -SSLServerAuthentication
```

### <a name="find-expired-certificates-on-remote-computers"></a><span data-ttu-id="aea52-158">원격 컴퓨터에서 만료 된 인증서 찾기</span><span class="sxs-lookup"><span data-stu-id="aea52-158">Find expired certificates on remote computers</span></span>

<span data-ttu-id="aea52-159">이 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Get-ChildItem` Srv01 및 Srv02 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-159">This command uses the `Invoke-Command` cmdlet to run a `Get-ChildItem` command on the Srv01 and Srv02 computers.</span></span> <span data-ttu-id="aea52-160">**ExpiringInDays** 매개 변수의 값이 0 이면 Srv01 및 Srv02 컴퓨터에서 만료 된 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-160">A value of zero (0) in the **ExpiringInDays** parameter gets certificates on the Srv01 and Srv02 computers that have expired.</span></span>

```powershell
Invoke-Command -ComputerName Srv01, Srv02 {Get-ChildItem -Path cert:\* `
  -Recurse -ExpiringInDays 0}
```

### <a name="combining-filters-to-find-a-specific-set-of-certificates"></a><span data-ttu-id="aea52-161">필터를 결합 하 여 특정 인증서 집합 찾기</span><span class="sxs-lookup"><span data-stu-id="aea52-161">Combining filters to find a specific set of certificates</span></span>

<span data-ttu-id="aea52-162">이 명령은 다음 특성이 있는 LocalMachine 저장소 위치의 모든 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-162">This command gets all certificates in the LocalMachine store location that have the following attributes:</span></span>

- <span data-ttu-id="aea52-163">DNS 이름에 "fabrikam"이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-163">"fabrikam" in their DNS name</span></span>
- <span data-ttu-id="aea52-164">EKU의 "클라이언트 인증"</span><span class="sxs-lookup"><span data-stu-id="aea52-164">"Client Authentication" in their EKU</span></span>
- <span data-ttu-id="aea52-165">`$true` **SendAsTrustedIssuer** 속성에 대 한 값</span><span class="sxs-lookup"><span data-stu-id="aea52-165">a value of `$true` for the **SendAsTrustedIssuer** property</span></span>
- <span data-ttu-id="aea52-166">다음 30 일 이내에 만료 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-166">do not expire within the next 30 days.</span></span>

<span data-ttu-id="aea52-167">**Notafter** 속성은 인증서 만료 날짜를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-167">The **NotAfter** property stores the certificate expiration date.</span></span>

```powershell
[DateTime] $ValidThrough = (Get-Date) + (New-TimeSpan -Days 30)
Get-ChildItem -Path cert:\* -Recurse -DNSName "*fabrikam*" `
  -EKU "*Client Authentication*" | Where-Object {
                                     $_.SendAsTrustedIssuer -and `
                                     $_.NotAfter -gt $ValidThrough
                                   }
```

## <a name="opening-the-certificates-mmc-snap-in"></a><span data-ttu-id="aea52-168">인증서 MMC 스냅인 열기</span><span class="sxs-lookup"><span data-stu-id="aea52-168">Opening the Certificates MMC Snap-in</span></span>

<span data-ttu-id="aea52-169">`Invoke-Item`이 cmdlet은 기본 응용 프로그램을 사용 하 여 지정한 경로를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-169">The `Invoke-Item` cmdlet will use the default application to open a path you specify.</span></span> <span data-ttu-id="aea52-170">인증서의 경우 기본 응용 프로그램은 인증서 MMC 스냅인입니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-170">For certificates, the default application is the Certificates MMC snap-in.</span></span>

<span data-ttu-id="aea52-171">이 명령은 지정된 인증서를 관리할 인증서 MMC 스냅인을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-171">This command opens the Certificates MMC snap-in to manage the specified certificate.</span></span>

```powershell
Invoke-Item cert:\CurrentUser\my\6B8223358119BB08840DEE50FD8AF9EA776CE66B
```

## <a name="copying-certificates"></a><span data-ttu-id="aea52-172">인증서 복사</span><span class="sxs-lookup"><span data-stu-id="aea52-172">Copying Certificates</span></span>

<span data-ttu-id="aea52-173">인증서를 복사 하는 기능은 **인증서** 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-173">Copying certificates is not supported by the **Certificate** provider.</span></span> <span data-ttu-id="aea52-174">인증서를 복사 하려고 하면이 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-174">When you attempt to copy a certificate, you see this error.</span></span>

```
$path = "Cert:\LocalMachine\Root\E2C0F6662D3C569705B4B31FE2CBF3434094B254"
PS Cert:\LocalMachine\> Copy-Item -Path $path -Destination .\CA\
Copy-Item : Provider operation stopped because the provider does not support
this operation.
At line:1 char:1
+ Copy-Item -Path $path -Destination .\CA\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotImplemented: (:) [Copy-Item],
                              PSNotSupportedException
    + FullyQualifiedErrorId : NotSupported,
                              Microsoft.PowerShell.Commands.CopyItemCommand
```

## <a name="moving-certificates"></a><span data-ttu-id="aea52-175">인증서 이동</span><span class="sxs-lookup"><span data-stu-id="aea52-175">Moving Certificates</span></span>

### <a name="move-all-ssl-server-authentication-certs-to-the-webhosting-store"></a><span data-ttu-id="aea52-176">모든 SSL 서버 인증 인증서를 WebHosting 저장소로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-176">Move all SSL Server authentication certs to the WebHosting store</span></span>

<span data-ttu-id="aea52-177">이 명령은 cmdlet을 사용 하 여 `Move-Item` 내 저장소에서 WebHosting 저장소로 인증서를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-177">This command uses the `Move-Item` cmdlet to move a certificate from the My store to the WebHosting store.</span></span>

<span data-ttu-id="aea52-178">`Move-Item` 는 인증서 저장소를 이동 하지 않으며 인증서를 다른 저장소 위치로 이동 하지 않습니다 (예: 인증서를 LocalMachine에서 CurrentUser로 이동).</span><span class="sxs-lookup"><span data-stu-id="aea52-178">`Move-Item` will not move certificate stores and it will not move certificates to a different store location, such as moving a certificate from LocalMachine to CurrentUser.</span></span> <span data-ttu-id="aea52-179">`Move-Item`Cmdlet은 인증서를 이동 하지만 개인 키는 이동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-179">The `Move-Item` cmdlet moves certificates, but it does not move private keys.</span></span>

<span data-ttu-id="aea52-180">이 명령은 cmdlet의 **Sslserverauthentication** 매개 변수를 사용 하 여 `Get-ChildItem` 내 인증서 저장소에서 SSL 서버 인증 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-180">This command uses the **SSLServerAuthentication** parameter of the `Get-ChildItem` cmdlet to get SSL server authentication certificates in the MY certificate store.</span></span>

<span data-ttu-id="aea52-181">반환 된 인증서는 cmdlet으로 파이프 되어 `Move-Item` 인증서를 WebHosting 저장소로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-181">The returned certificates are piped to the `Move-Item` cmdlet, which moves the certificates to the WebHosting store.</span></span>

```powershell
Get-ChildItem cert:\LocalMachine\My -SSLServerAuthentication | Move-Item `
  -Destination cert:\LocalMachine\WebHosting
```

## <a name="deleting-certificates-and-private-keys"></a><span data-ttu-id="aea52-182">인증서 및 개인 키 삭제</span><span class="sxs-lookup"><span data-stu-id="aea52-182">Deleting Certificates and Private Keys</span></span>

<span data-ttu-id="aea52-183">`Remove-Item`Cmdlet은 사용자가 지정 하는 인증서를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-183">The `Remove-Item` cmdlet will remove certificates that you specify.</span></span> <span data-ttu-id="aea52-184">`-DeleteKey`동적 매개 변수는 개인 키를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-184">The `-DeleteKey` dynamic parameter deletes the private key.</span></span>

### <a name="delete-a-certificate-from-the-ca-store"></a><span data-ttu-id="aea52-185">CA 저장소에서 인증서를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-185">Delete a Certificate from the CA store</span></span>

<span data-ttu-id="aea52-186">이 명령은 CA 인증서 저장소에서 인증서를 삭제하지만 연결된 개인 키는 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-186">This command deletes a certificate from the CA certificate store, but leaves the associated private key intact.</span></span>

<span data-ttu-id="aea52-187">드라이브에서 `Cert:` `Remove-Item` Cmdlet은 **deletekey**, **Path**, **WhatIf** 및 **Confirm** 매개 변수만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-187">In the `Cert:` drive, the `Remove-Item` cmdlet supports only the **DeleteKey**, **Path**, **WhatIf**, and **Confirm** parameters.</span></span> <span data-ttu-id="aea52-188">다른 모든 매개 변수는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-188">All other parameters are ignored.</span></span>

```powershell
Remove-Item cert:\LocalMachine\CA\5DDC44652E62BF9AA1116DC41DE44AB47C87BDD0
```

### <a name="delete-a-certificate-using-a-wildcards-in-the-dns-name"></a><span data-ttu-id="aea52-189">DNS 이름에 와일드 카드를 사용 하 여 인증서 삭제</span><span class="sxs-lookup"><span data-stu-id="aea52-189">Delete a Certificate using a wildcards in the DNS name</span></span>

<span data-ttu-id="aea52-190">이 명령은 DNS 이름에 "Fabrikam"이 포함된 모든 인증서를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-190">This command deletes all certificates that have a DNS name that contains "Fabrikam".</span></span> <span data-ttu-id="aea52-191">이 cmdlet은 cmdlet의 **DNSName** 매개 변수를 사용 하 여 인증서를 가져오고 cmdlet을 사용 하 여 `Get-ChildItem` 인증서를 `Remove-Item` 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-191">It uses the **DNSName** parameter of the `Get-ChildItem` cmdlet to get the certificates and the `Remove-Item` cmdlet to delete them.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine -DnsName *Fabrikam* | Remove-Item
```

### <a name="delete-private-keys-from-a-remote-computer"></a><span data-ttu-id="aea52-192">원격 컴퓨터에서 개인 키 삭제</span><span class="sxs-lookup"><span data-stu-id="aea52-192">Delete private keys from a remote computer</span></span>

<span data-ttu-id="aea52-193">이 명령 시리즈는 원격 컴퓨터에서 위임을 사용하도록 설정하고, 인증서 및 연결된 개인 키를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-193">This series of commands enables delegation and then deletes the certificate and associated private key on a remote computer.</span></span> <span data-ttu-id="aea52-194">원격 컴퓨터에서 개인 키를 삭제하려면 위임된 자격 증명을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-194">To delete a private key on a remote computer, you must use delegated credentials.</span></span>

<span data-ttu-id="aea52-195">Cmdlet을 사용 `Enable-WSManCredSSP` 하 여 S1 원격 컴퓨터의 클라이언트에서 CredSSP (Credential Security Service Provider) 인증을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-195">Use the `Enable-WSManCredSSP` cmdlet to enable Credential Security Service Provider (CredSSP) authentication on a client on the S1 remote computer.</span></span>
<span data-ttu-id="aea52-196">CredSSP는 대리 인증을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-196">CredSSP permits delegated authentication.</span></span>

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer S1
```

<span data-ttu-id="aea52-197">Cmdlet을 사용 `Connect-WSMan` 하 여 S1 컴퓨터를 로컬 컴퓨터의 WinRM 서비스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-197">Use the `Connect-WSMan` cmdlet to connect the S1 computer to the WinRM service on the local computer.</span></span> <span data-ttu-id="aea52-198">이 명령이 완료 되 면 S1 컴퓨터가 PowerShell의 로컬 드라이브에 표시 됩니다 `WSMan:` .</span><span class="sxs-lookup"><span data-stu-id="aea52-198">When this command completes, the S1 computer appears in the local `WSMan:` drive in PowerShell.</span></span>

```powershell
Connect-WSMan -ComputerName S1 -Credential Domain01\Admin01
```

<span data-ttu-id="aea52-199">이제 WSMan: 드라이브에서 Set-Item cmdlet을 사용 하 여 WinRM 서비스에 대 한 CredSSP 특성을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-199">Now, you can use the Set-Item cmdlet in the WSMan: drive to enable the CredSSP attribute for the WinRM service.</span></span>

```powershell
Set-Item -Path WSMan:\S1\Service\Auth\CredSSP -Value $true
```

<span data-ttu-id="aea52-200">Cmdlet을 사용 하 여 s1 컴퓨터에서 원격 세션을 시작 하 `New-PSSession` 고 CredSSP 인증을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-200">Start a remote session on the s1 computer using the `New-PSSession` cmdlet, and specify CredSSP authentication.</span></span> <span data-ttu-id="aea52-201">세션을 `$s` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-201">Saves the session in the `$s` variable.</span></span>

```powershell
$s  = New-PSSession S1 -Authentication CredSSP -Credential Domain01\Admin01
```

<span data-ttu-id="aea52-202">마지막으로, cmdlet을 사용 `Invoke-Command` 하 여 `Remove-Item` 변수의 세션에서 명령을 실행 `$s` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-202">Finally, use the `Invoke-Command` cmdlet to run a `Remove-Item` command in the session in the `$s` variable.</span></span> <span data-ttu-id="aea52-203">이 `Remove-Item` 명령은 **deletekey** 매개 변수를 사용 하 여 지정 된 인증서와 함께 개인 키를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-203">The `Remove-Item` command uses the **DeleteKey** parameter to remove the private key along with the specified certificate.</span></span>

```powershell
Invoke-Command -Session $s { Remove-Item `
  -Path cert:\LocalMachine\My\D2D38EBA60CAA1C12055A2E1C83B15AD450110C2 `
  -DeleteKey
  }
```

### <a name="delete-expired-certificates"></a><span data-ttu-id="aea52-204">만료 된 인증서 삭제</span><span class="sxs-lookup"><span data-stu-id="aea52-204">Delete expired Certificates</span></span>

<span data-ttu-id="aea52-205">이 명령은 cmdlet의 **ExpiringInDays** 매개 변수 값을 0으로 사용 `Get-ChildItem` 하 여 만료 된 webhosting 저장소에서 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-205">This command uses the **ExpiringInDays** parameter of the `Get-ChildItem` cmdlet with a value of 0 to get certificates in the WebHosting store that have expired.</span></span>

<span data-ttu-id="aea52-206">반환 된 인증서를 포함 하는 변수는 cmdlet으로 파이프 되어 해당 변수를 `Remove-Item` 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-206">The variable containing the returned certificates is piped to the `Remove-Item` cmdlet, which deletes them.</span></span> <span data-ttu-id="aea52-207">이 명령은 **deletekey** 매개 변수를 사용 하 여 인증서와 함께 개인 키를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-207">The command uses the **DeleteKey** parameter to delete the private key along with the certificate.</span></span>

```powershell
$expired = Get-ChildItem cert:\LocalMachine\WebHosting -ExpiringInDays 0
$expired | Remove-Item -DeleteKey
```

## <a name="creating-certificates"></a><span data-ttu-id="aea52-208">인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="aea52-208">Creating Certificates</span></span>

<span data-ttu-id="aea52-209">`New-Item`Cmdlet은 **인증서** 공급자에 새 인증서를 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-209">The `New-Item` cmdlet does not create new certificates in the **Certificate** provider.</span></span> <span data-ttu-id="aea52-210">[New-selfsignedcertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet을 사용 하 여 테스트용 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-210">Use the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet to create a certificate for testing purposes.</span></span>

## <a name="creating-certificate-stores"></a><span data-ttu-id="aea52-211">인증서 저장소 만들기</span><span class="sxs-lookup"><span data-stu-id="aea52-211">Creating Certificate Stores</span></span>

<span data-ttu-id="aea52-212">Cert: 드라이브에서 `New-Item` cmdlet은 LocalMachine 저장소 위치에 인증서 저장소를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-212">In the Cert: drive, the `New-Item` cmdlet creates certificate stores in the LocalMachine store location.</span></span> <span data-ttu-id="aea52-213">**Name**, **Path**, **WhatIf** 및 **Confirm** 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-213">It supports the **Name**, **Path**, **WhatIf**, and **Confirm** parameters.</span></span> <span data-ttu-id="aea52-214">다른 모든 매개 변수는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-214">All other parameters are ignored.</span></span> <span data-ttu-id="aea52-215">이 명령은 새 인증서 저장소를 나타내는 **system.security.cryptography.x509certificates.x509certificate2** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-215">The command returns a **System.Security.Cryptography.X509Certificates.X509Store** that represents the new certificate store.</span></span>

<span data-ttu-id="aea52-216">이 명령은 LocalMachine 저장소 위치에서 이름이 "CustomStore"인 새 인증서 저장소를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-216">This command creates a new certificate store named "CustomStore" in the LocalMachine store location.</span></span>

```powershell
New-Item -Path cert:\LocalMachine\CustomStore
```

### <a name="create-a-new-certificate-store-on-a-remote-computer"></a><span data-ttu-id="aea52-217">원격 컴퓨터에 새 인증서 저장소 만들기</span><span class="sxs-lookup"><span data-stu-id="aea52-217">Create a new certificate store on a remote computer</span></span>

<span data-ttu-id="aea52-218">이 명령은 Server01 컴퓨터의 LocalMachine 저장소 위치에 이름이 "HostingStore"인 새 인증서 저장소를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-218">This command creates a new certificate store named "HostingStore" in the LocalMachine store location on the Server01 computer.</span></span>

<span data-ttu-id="aea52-219">이 명령은 cmdlet을 사용 `Invoke-Command` 하 여 `New-Item` Server01 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-219">The command uses the `Invoke-Command` cmdlet to run a `New-Item` command on the Server01 computer.</span></span> <span data-ttu-id="aea52-220">이 명령은 새 인증서 저장소를 나타내는 **system.security.cryptography.x509certificates.x509certificate2** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-220">The command returns a **System.Security.Cryptography.X509Certificates.X509Store** that represents the new certificate store.</span></span>

```powershell
Invoke-Command { New-Item -Path cert:\LocalMachine\CustomStore } `
  -ComputerName Server01
```

## <a name="creating-client-certificates-for-ws-man"></a><span data-ttu-id="aea52-221">WS-Man에 대 한 클라이언트 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="aea52-221">Creating Client Certificates for WS-Man</span></span>

<span data-ttu-id="aea52-222">이 명령은 **ws-management** 클라이언트에서 사용할 수 있는 **ClientCertificate** 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-222">This command creates **ClientCertificate** entry that can be used by the **WS-Management** client.</span></span> <span data-ttu-id="aea52-223">새 **ClientCertificate** 가 **ClientCertificate** 디렉터리 아래에 "ClientCertificate_1234567890"로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-223">The new **ClientCertificate** will show up under the **ClientCertificate** directory as "ClientCertificate_1234567890".</span></span> <span data-ttu-id="aea52-224">모든 매개 변수는 필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-224">All of the parameters are mandatory.</span></span> <span data-ttu-id="aea52-225">**발급자** 는 발급자 인증서의 손 도장 (thumbprint) 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-225">The **Issuer** needs to be thumbprint of the issuers certificate.</span></span>

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* -Credential $cred
```

## <a name="deleting-certificate-stores"></a><span data-ttu-id="aea52-226">인증서 저장소 삭제</span><span class="sxs-lookup"><span data-stu-id="aea52-226">Deleting Certificate Stores</span></span>

### <a name="delete-a-certificate-store-from-a-remote-computer"></a><span data-ttu-id="aea52-227">원격 컴퓨터에서 인증서 저장소를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-227">Delete a certificate store from a remote computer</span></span>

<span data-ttu-id="aea52-228">이 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Remove-Item` S1 및 S2 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-228">This command uses the `Invoke-Command` cmdlet to run a `Remove-Item` command on the S1 and S2 computers.</span></span> <span data-ttu-id="aea52-229">이 명령에는 저장소를 `Remove-Item` 삭제 하기 전에 저장소에서 인증서를 삭제 하는 **재귀** 매개 변수가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-229">The `Remove-Item` command includes the **Recurse** parameter, which deletes the certificates in the store before it deletes the store.</span></span>

```powershell
Invoke-Command { Remove-Item -Path cert:\LocalMachine\TestStore -Recurse } `
  -ComputerName S1, S2
```

## <a name="dynamic-parameters"></a><span data-ttu-id="aea52-230">동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="aea52-230">Dynamic parameters</span></span>

<span data-ttu-id="aea52-231">동적 매개 변수는 PowerShell 공급자가 추가 하는 cmdlet 매개 변수 이며, 공급자 사용 드라이브에서 cmdlet을 사용 하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-231">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span> <span data-ttu-id="aea52-232">이러한 매개 변수는 인증서 공급자의 모든 하위 디렉터리에서 유효 하지만 인증서에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-232">These parameters are valid in all subdirectories of the Certificate provider, but are effective only on certificates.</span></span>

> [!NOTE]
> <span data-ttu-id="aea52-233">속성에 대해 필터링을 수행 하는 매개 변수도 `EnhancedKeyUsageList` 빈 속성 값을 가진 항목을 반환 `EnhancedKeyUsageList` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-233">Parameters that perform filtering against the `EnhancedKeyUsageList` property also return items with an empty `EnhancedKeyUsageList` property value.</span></span>
> <span data-ttu-id="aea52-234">빈 **EnhancedKeyUsageList** 있는 인증서를 모든 용도로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-234">Certificates that have an empty **EnhancedKeyUsageList** can be used for all purposes.</span></span>

<span data-ttu-id="aea52-235">다음 인증서 공급자 매개 변수는 PowerShell 7.1에서 다시 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-235">The following Certificate provider parameters were reintroduced in PowerShell 7.1.</span></span>

- <span data-ttu-id="aea52-236">DNSName</span><span class="sxs-lookup"><span data-stu-id="aea52-236">DNSName</span></span>
- <span data-ttu-id="aea52-237">DocumentEncryptionCert</span><span class="sxs-lookup"><span data-stu-id="aea52-237">DocumentEncryptionCert</span></span>
- <span data-ttu-id="aea52-238">EKU</span><span class="sxs-lookup"><span data-stu-id="aea52-238">EKU</span></span>
- <span data-ttu-id="aea52-239">ExpiringInDays</span><span class="sxs-lookup"><span data-stu-id="aea52-239">ExpiringInDays</span></span>
- <span data-ttu-id="aea52-240">SSLServerAuthentication</span><span class="sxs-lookup"><span data-stu-id="aea52-240">SSLServerAuthentication</span></span>

### <a name="codesigningcert-systemmanagementautomationswitchparameter"></a><span data-ttu-id="aea52-241">CodeSigningCert를 <></span><span class="sxs-lookup"><span data-stu-id="aea52-241">CodeSigningCert <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="aea52-242">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="aea52-242">Cmdlets supported</span></span>

- [<span data-ttu-id="aea52-243">Get-Item</span><span class="sxs-lookup"><span data-stu-id="aea52-243">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

- [<span data-ttu-id="aea52-244">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="aea52-244">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="aea52-245">이 매개 변수는 **EnhancedKeyUsageList** 속성 값에 "코드 서명"이 있는 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-245">This parameter gets certificates that have "Code Signing" in their **EnhancedKeyUsageList** property value.</span></span>

### <a name="deletekey-systemmanagementautomationswitchparameter"></a><span data-ttu-id="aea52-246">DeleteKey를 <></span><span class="sxs-lookup"><span data-stu-id="aea52-246">DeleteKey <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="aea52-247">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="aea52-247">Cmdlets supported</span></span>

- [<span data-ttu-id="aea52-248">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="aea52-248">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)

<span data-ttu-id="aea52-249">이 매개 변수는 인증서를 삭제할 때 연결 된 개인 키를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-249">This parameter deletes the associated private key when it deletes the certificate.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aea52-250">원격 컴퓨터의 저장소에 있는 사용자 인증서와 연결 된 개인 키를 삭제 하려면 `Cert:\CurrentUser` 위임 된 자격 증명을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-250">To delete a private key that is associated with a user certificate in the `Cert:\CurrentUser` store on a remote computer, you must use delegated credentials.</span></span> <span data-ttu-id="aea52-251">`Invoke-Command`Cmdlet은 **CredSSP** 매개 변수를 사용 하 여 자격 증명 위임을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-251">The `Invoke-Command` cmdlet supports credential delegation using the **CredSSP** parameter.</span></span> <span data-ttu-id="aea52-252">`Remove-Item`및 자격 증명 위임을 사용 하기 전에 보안 위험을 고려해 야 합니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="aea52-252">You should consider any security risks before using `Remove-Item` with `Invoke-Command` and credential delegation.</span></span>

<span data-ttu-id="aea52-253">이 매개 변수는 PowerShell 7.1에서 다시 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-253">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="dnsname-microsoftpowershellcommandsdnsnamerepresentation"></a><span data-ttu-id="aea52-254">DnsName <. DnsNameRepresentation></span><span class="sxs-lookup"><span data-stu-id="aea52-254">DnsName <Microsoft.PowerShell.Commands.DnsNameRepresentation></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="aea52-255">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="aea52-255">Cmdlets supported</span></span>

- [<span data-ttu-id="aea52-256">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="aea52-256">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="aea52-257">이 매개 변수는 인증서의 **DNSNameList** 속성에 지정 된 도메인 이름 또는 이름 패턴이 있는 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-257">This parameter gets certificates that have the specified domain name or name pattern in the **DNSNameList** property of the certificate.</span></span> <span data-ttu-id="aea52-258">이 매개 변수 값은 "Unicode" 또는 "ASCII" 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-258">The value of this parameter can either be "Unicode" or "ASCII".</span></span> <span data-ttu-id="aea52-259">Punycode 값은 유니코드로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-259">Punycode values are converted to Unicode.</span></span> <span data-ttu-id="aea52-260">와일드 카드 문자 ( `*` )를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-260">Wildcard characters (`*`) are permitted.</span></span>

<span data-ttu-id="aea52-261">이 매개 변수는 PowerShell 7.1에서 다시 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-261">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="documentencryptioncert-systemmanagementautomationswitchparameter"></a><span data-ttu-id="aea52-262">Document메이 Cert <>입니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-262">DocumentEncryptionCert <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="aea52-263">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="aea52-263">Cmdlets supported</span></span>

- [<span data-ttu-id="aea52-264">Get-Item</span><span class="sxs-lookup"><span data-stu-id="aea52-264">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

- [<span data-ttu-id="aea52-265">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="aea52-265">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="aea52-266">이 매개 변수는 **EnhancedKeyUsageList** 속성 값에 "문서 암호화"가 있는 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-266">This parameter gets certificates that have "Document Encryption" in their **EnhancedKeyUsageList** property value.</span></span>

### <a name="eku-systemstring"></a><span data-ttu-id="aea52-267">EKU <System.string></span><span class="sxs-lookup"><span data-stu-id="aea52-267">EKU <System.String></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="aea52-268">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="aea52-268">Cmdlets supported</span></span>

- [<span data-ttu-id="aea52-269">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="aea52-269">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="aea52-270">이 매개 변수는 인증서의 속성에 지정 된 텍스트 또는 텍스트 패턴이 있는 인증서를 가져옵니다 `EnhancedKeyUsageList` .</span><span class="sxs-lookup"><span data-stu-id="aea52-270">This parameter gets certificates that have the specified text or text pattern in the `EnhancedKeyUsageList` property of the certificate.</span></span> <span data-ttu-id="aea52-271">와일드 카드 문자 ( `*` )를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-271">Wildcard characters (`*`) are permitted.</span></span> <span data-ttu-id="aea52-272">속성에는 `EnhancedKeyUsageList` EKU의 이름 및 OID 필드가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-272">The `EnhancedKeyUsageList` property contains the friendly name and the OID fields of the EKU.</span></span>

<span data-ttu-id="aea52-273">이 매개 변수는 PowerShell 7.1에서 다시 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-273">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="expiringindays-systemint32"></a><span data-ttu-id="aea52-274">ExpiringInDays <></span><span class="sxs-lookup"><span data-stu-id="aea52-274">ExpiringInDays <System.Int32></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="aea52-275">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="aea52-275">Cmdlets supported</span></span>

- [<span data-ttu-id="aea52-276">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="aea52-276">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="aea52-277">이 매개 변수는 지정 된 일 수 또는 그 이전에 만료 되는 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-277">This parameter gets certificates that are expiring in or before the specified number of days.</span></span> <span data-ttu-id="aea52-278">0값을 지정하면 만료된 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-278">A value of 0 (zero) gets certificates that have expired.</span></span>

<span data-ttu-id="aea52-279">이 매개 변수는 PowerShell 7.1에서 다시 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-279">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="itemtype-string"></a><span data-ttu-id="aea52-280">ItemType \<String\></span><span class="sxs-lookup"><span data-stu-id="aea52-280">ItemType \<String\></span></span>

<span data-ttu-id="aea52-281">이 매개 변수를 사용 하 여에서 만든 항목의 형식을 지정할 수 있습니다 `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="aea52-281">This parameter allows you to specify the type of item created by `New-Item`.</span></span>

<span data-ttu-id="aea52-282">드라이브에는 `Certificate` 다음 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-282">In a `Certificate` drive, the following values are allowed:</span></span>

- <span data-ttu-id="aea52-283">인증서 공급자</span><span class="sxs-lookup"><span data-stu-id="aea52-283">Certificate Provider</span></span>
- <span data-ttu-id="aea52-284">인증서</span><span class="sxs-lookup"><span data-stu-id="aea52-284">Certificate</span></span>
- <span data-ttu-id="aea52-285">스토어</span><span class="sxs-lookup"><span data-stu-id="aea52-285">Store</span></span>
- <span data-ttu-id="aea52-286">StoreLocation</span><span class="sxs-lookup"><span data-stu-id="aea52-286">StoreLocation</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="aea52-287">지원되는 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="aea52-287">Cmdlets Supported</span></span>

- [<span data-ttu-id="aea52-288">New-Item</span><span class="sxs-lookup"><span data-stu-id="aea52-288">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sslserverauthentication-systemmanagementautomationswitchparameter"></a><span data-ttu-id="aea52-289">SSLServerAuthentication을 <></span><span class="sxs-lookup"><span data-stu-id="aea52-289">SSLServerAuthentication <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="aea52-290">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="aea52-290">Cmdlets supported</span></span>

- [<span data-ttu-id="aea52-291">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="aea52-291">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="aea52-292">SSL 웹 호스팅을 위한 서버 인증서만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-292">Gets only server certificates for SSL web hosting.</span></span> <span data-ttu-id="aea52-293">이 매개 변수는 속성 값에 "서버 인증"이 있는 인증서를 가져옵니다 `EnhancedKeyUsageList` .</span><span class="sxs-lookup"><span data-stu-id="aea52-293">This parameter gets certificates that have "Server Authentication" in their `EnhancedKeyUsageList` property value.</span></span>

<span data-ttu-id="aea52-294">이 매개 변수는 PowerShell 7.1에서 다시 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-294">This parameter was reintroduced in PowerShell 7.1</span></span>

## <a name="script-properties"></a><span data-ttu-id="aea52-295">스크립트 속성</span><span class="sxs-lookup"><span data-stu-id="aea52-295">Script properties</span></span>

<span data-ttu-id="aea52-296">인증서를 쉽게 검색 하 고 관리할 수 있도록 인증서를 나타내는 새 스크립트 속성이 **x509Certificate2** 개체에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-296">New script properties have been added to the **x509Certificate2** object that represents the certificates to make it easy to search and manage the certificates.</span></span>

- <span data-ttu-id="aea52-297">`DnsNameList`: 속성을 채우기 위해 `DnsNameList` 인증서 공급자는 SAN (SubjectAlternativeName) 확장의 DNSName 항목에서 콘텐츠를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-297">`DnsNameList`: To populate the `DnsNameList` property, the Certificate provider copies the content from the DNSName entry in the SubjectAlternativeName (SAN) extension.</span></span> <span data-ttu-id="aea52-298">SAN 확장이 비어 있으면 속성은 인증서의 제목 필드에 있는 내용으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-298">If the SAN extension is empty, the property is populated with content from the Subject field of the certificate.</span></span>

- <span data-ttu-id="aea52-299">`EnhancedKeyUsageList`: 속성을 채우기 위해 `EnhancedKeyUsageList` 인증서 공급자는 인증서에 있는 EKU (EnhancedKeyUsage) 필드의 OID 속성을 복사 하 여 친숙 한 이름을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-299">`EnhancedKeyUsageList`: To populate the `EnhancedKeyUsageList` property, the Certificate provider copies the OID properties of the EnhancedKeyUsage (EKU) field in the certificate and creates a friendly name for it.</span></span>

- <span data-ttu-id="aea52-300">`SendAsTrustedIssuer`: 속성을 채우기 위해 `SendAsTrustedIssuer` 인증서 공급자는 `SendAsTrustedIssuer` 인증서에서 속성을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-300">`SendAsTrustedIssuer`: To populate the `SendAsTrustedIssuer` property, the Certificate provider copies the `SendAsTrustedIssuer` property from the certificate.</span></span>  <span data-ttu-id="aea52-301">자세한 내용은 [클라이언트 인증에 대 한 신뢰할 수 있는 발급자 관리](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aea52-301">For more information see [Management of trusted issuers for client authentication](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers).</span></span>

<span data-ttu-id="aea52-302">이러한 새 기능을 통해 DNS 이름과 만료 날짜를 기준으로 인증서를 검색하고, EKU(확장된 키 사용) 속성의 값으로 클라이언트 및 서버 인증 인증서를 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-302">These new features let you search for certificates based on their DNS names and expiration dates, and distinguish client and server authentication certificates by the value of their Enhanced Key Usage (EKU) properties.</span></span>

## <a name="using-the-pipeline"></a><span data-ttu-id="aea52-303">파이프라인 사용</span><span class="sxs-lookup"><span data-stu-id="aea52-303">Using the pipeline</span></span>

<span data-ttu-id="aea52-304">공급자 cmdlet은 파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-304">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="aea52-305">파이프라인을 사용 하 여 cmdlet 간에 공급자 데이터를 전송 하 여 작업을 간소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-305">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="aea52-306">공급자 cmdlet에서 파이프라인을 사용 하는 방법에 대 한 자세한 내용은이 문서 전체에서 제공 되는 cmdlet 참조를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aea52-306">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="aea52-307">도움말 보기</span><span class="sxs-lookup"><span data-stu-id="aea52-307">Getting help</span></span>

<span data-ttu-id="aea52-308">Windows PowerShell 3.0부터는 이러한 cmdlet이 파일 시스템 드라이브에서 동작하는 방식을 설명하는 공급자 cmdlet에 대한 사용자 지정된 도움말 항목을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-308">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="aea52-309">파일 시스템 드라이브에 맞게 사용자 지정 된 도움말 항목을 보려면 파일 시스템 드라이브에서 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 명령을 실행 하거나 `-Path` 의 매개 변수를 사용 `Get-Help` 하 여 파일 시스템 드라이브를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aea52-309">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of `Get-Help` to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path cert:
```

## <a name="see-also"></a><span data-ttu-id="aea52-310">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aea52-310">See also</span></span>

[<span data-ttu-id="aea52-311">about_Providers</span><span class="sxs-lookup"><span data-stu-id="aea52-311">about_Providers</span></span>](../../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="aea52-312">about_Signing</span><span class="sxs-lookup"><span data-stu-id="aea52-312">about_Signing</span></span>](../../Microsoft.PowerShell.Core/About/about_Signing.md)

[<span data-ttu-id="aea52-313">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="aea52-313">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)

[<span data-ttu-id="aea52-314">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="aea52-314">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[<span data-ttu-id="aea52-315">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="aea52-315">Get-PfxCertificate</span></span>](xref:Microsoft.PowerShell.Security.Get-PfxCertificate)
