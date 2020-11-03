---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-authenticodesignature?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-AuthenticodeSignature
ms.openlocfilehash: 4ec4261326e43b2f811d201bf45e6854b4f478ea
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214209"
---
# <span data-ttu-id="d6f48-103">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="d6f48-103">Set-AuthenticodeSignature</span></span>

## <span data-ttu-id="d6f48-104">개요</span><span class="sxs-lookup"><span data-stu-id="d6f48-104">SYNOPSIS</span></span>
<span data-ttu-id="d6f48-105">PowerShell 스크립트 또는 다른 파일에 [Authenticode](/windows-hardware/drivers/install/authenticode) 서명을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-105">Adds an [Authenticode](/windows-hardware/drivers/install/authenticode) signature to a PowerShell script or other file.</span></span>

## <span data-ttu-id="d6f48-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d6f48-106">SYNTAX</span></span>

### <span data-ttu-id="d6f48-107">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="d6f48-107">ByPath (Default)</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] [-FilePath] <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d6f48-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="d6f48-108">ByLiteralPath</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -LiteralPath <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d6f48-109">ByContent</span><span class="sxs-lookup"><span data-stu-id="d6f48-109">ByContent</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -SourcePathOrExtension <String[]>
 -Content <Byte[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d6f48-110">설명</span><span class="sxs-lookup"><span data-stu-id="d6f48-110">DESCRIPTION</span></span>

<span data-ttu-id="d6f48-111">`Set-AuthenticodeSignature`Cmdlet은 SIP (Subject Interface Package)를 지 원하는 모든 파일에 Authenticode 서명을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-111">The `Set-AuthenticodeSignature` cmdlet adds an Authenticode signature to any file that supports Subject Interface Package (SIP).</span></span>

<span data-ttu-id="d6f48-112">PowerShell 스크립트 파일에서 서명은 스크립트에서 실행 되는 명령의 끝을 나타내는 텍스트 블록 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-112">In a PowerShell script file, the signature takes the form of a block of text that indicates the end of the instructions that are executed in the script.</span></span> <span data-ttu-id="d6f48-113">이 cmdlet이 실행될 때 파일에 서명이 있는 경우 해당 서명은 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-113">If there is a signature in the file when this cmdlet runs, that signature is removed.</span></span>

## <span data-ttu-id="d6f48-114">예제</span><span class="sxs-lookup"><span data-stu-id="d6f48-114">EXAMPLES</span></span>

### <span data-ttu-id="d6f48-115">예 1-로컬 인증서 저장소의 인증서를 사용 하 여 스크립트 서명</span><span class="sxs-lookup"><span data-stu-id="d6f48-115">Example 1 - Sign a script using a certificate from the local certificate store</span></span>

<span data-ttu-id="d6f48-116">이러한 명령은 PowerShell 인증서 공급자에서 코드 서명 인증서를 검색 하 여 PowerShell 스크립트에 서명 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-116">These commands retrieve a code-signing certificate from the PowerShell certificate provider and use it to sign a PowerShell script.</span></span>

```powershell
$cert=Get-ChildItem -Path Cert:\CurrentUser\My -CodeSigningCert
Set-AuthenticodeSignature -FilePath PsTestInternet2.ps1 -Certificate $cert
```

<span data-ttu-id="d6f48-117">첫 번째 명령은 `Get-ChildItem` cmdlet 및 PowerShell 인증서 공급자를 사용 하 여 `Cert:\CurrentUser\My` 인증서 저장소의 하위 디렉터리에 있는 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-117">The first command uses the `Get-ChildItem` cmdlet and the PowerShell certificate provider to get the certificates in the `Cert:\CurrentUser\My` subdirectory of the certificate store.</span></span> <span data-ttu-id="d6f48-118">`Cert:`드라이브는 인증서 공급자가 노출 하는 드라이브입니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-118">The `Cert:` drive is the drive exposed by the certificate provider.</span></span> <span data-ttu-id="d6f48-119">인증서 공급자 에서만 지원 되는 **Codesigningcert** 매개 변수는 검색 된 인증서를 코드 서명 기관이 있는 인증서로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-119">The **CodeSigningCert** parameter, which is supported only by the certificate provider, limits the certificates retrieved to those with code-signing authority.</span></span> <span data-ttu-id="d6f48-120">이 명령은 결과를 `$cert` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-120">The command stores the result in the `$cert` variable.</span></span>

<span data-ttu-id="d6f48-121">두 번째 명령은 cmdlet을 사용 하 여 `Set-AuthenticodeSignature` 스크립트에 서명 합니다 `PSTestInternet2.ps1` .</span><span class="sxs-lookup"><span data-stu-id="d6f48-121">The second command uses the `Set-AuthenticodeSignature` cmdlet to sign the `PSTestInternet2.ps1` script.</span></span> <span data-ttu-id="d6f48-122">**FilePath** 매개 변수를 사용 하 여 스크립트의 이름을 지정 하 고 **certificate** 매개 변수를 사용 하 여 인증서를 변수에 저장 하도록 지정 합니다 `$cert` .</span><span class="sxs-lookup"><span data-stu-id="d6f48-122">It uses the **FilePath** parameter to specify the name of the script and the **Certificate** parameter to specify that the certificate is stored in the `$cert` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="d6f48-123">에서 **Codesigningcert** 매개 변수를 사용 하면 `Get-ChildItem` 코드 서명 기관이 있는 인증서만 반환 되 고 개인 키가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-123">Using the **CodeSigningCert** parameter with `Get-ChildItem` only returns certificates that have code-signing authority and contain a private key.</span></span> <span data-ttu-id="d6f48-124">개인 키가 없는 경우 서명에는 인증서를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-124">If there is no private key, the certificates cannot be used for signing.</span></span>

### <span data-ttu-id="d6f48-125">예 2-PFX 파일의 인증서를 사용 하 여 스크립트 서명</span><span class="sxs-lookup"><span data-stu-id="d6f48-125">Example 2 - Sign a script using a certificate from a PFX file</span></span>

<span data-ttu-id="d6f48-126">이러한 명령은 cmdlet을 사용 `Get-PfxCertificate` 하 여 코드 서명 인증서를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-126">These commands use the `Get-PfxCertificate` cmdlet to load a code signing certificate.</span></span> <span data-ttu-id="d6f48-127">그런 다음 PowerShell 스크립트에 서명 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-127">Then, use it to sign a PowerShell script.</span></span>

```powershell
$cert = Get-PfxCertificate -FilePath C:\Test\Mysign.pfx
Set-AuthenticodeSignature -FilePath ServerProps.ps1 -Certificate $cert
```

<span data-ttu-id="d6f48-128">첫 번째 명령은 cmdlet을 사용 하 여 `Get-PfxCertificate` C:\Test\MySign.pfx 인증서를 변수에 로드 합니다 `$cert` .</span><span class="sxs-lookup"><span data-stu-id="d6f48-128">The first command uses the `Get-PfxCertificate` cmdlet to load the C:\Test\MySign.pfx certificate into the `$cert` variable.</span></span>

<span data-ttu-id="d6f48-129">두 번째 명령은를 사용 하 여 `Set-AuthenticodeSignature` 스크립트에 서명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-129">The second command uses `Set-AuthenticodeSignature` to sign the script.</span></span> <span data-ttu-id="d6f48-130">의 **FilePath** 매개 변수는 `Set-AuthenticodeSignature` 서명 되는 스크립트 파일의 경로를 지정 하 고 **Cert** 매개 변수는 `$cert` 인증서를 포함 하는 변수를에 전달 `Set-AuthenticodeSignature` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-130">The **FilePath** parameter of `Set-AuthenticodeSignature` specifies the path to the script file being signed and the **Cert** parameter passes the `$cert` variable containing the certificate to `Set-AuthenticodeSignature`.</span></span>

<span data-ttu-id="d6f48-131">인증서 파일이 암호로 보호 된 경우 PowerShell에서 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-131">If the certificate file is password protected, PowerShell prompts you for the password.</span></span>

### <span data-ttu-id="d6f48-132">예제 3-루트 인증 기관을 포함 하는 서명 추가</span><span class="sxs-lookup"><span data-stu-id="d6f48-132">Example 3 - Add a signature that includes the root authority</span></span>

<span data-ttu-id="d6f48-133">이 명령은 신뢰 체인에 루트 기관을 포함하는 디지털 서명을 추가하며 타사 타임스탬프 서버에서 서명됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-133">This command adds a digital signature that includes the root authority in the trust chain, and it is signed by a third-party timestamp server.</span></span>

```powershell
Set-AuthenticodeSignature -FilePath c:\scripts\Remodel.ps1 -Certificate $cert -IncludeChain All -TimestampServer "http://timestamp.fabrikam.com/scripts/timstamper.dll"
```

<span data-ttu-id="d6f48-134">이 명령은 **FilePath** 매개 변수를 사용 하 여 서명할 스크립트를 지정 하 고 **certificate** 매개 변수를 사용 하 여 변수에 저장 된 인증서를 지정 합니다 `$cert` .</span><span class="sxs-lookup"><span data-stu-id="d6f48-134">The command uses the **FilePath** parameter to specify the script being signed and the **Certificate** parameter to specify the certificate that is saved in the `$cert` variable.</span></span> <span data-ttu-id="d6f48-135">**명령은 includechain** 매개 변수를 사용 하 여 루트 기관을 포함 하 여 신뢰 체인의 모든 서명을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-135">It uses the **IncludeChain** parameter to include all of the signatures in the trust chain, including the root authority.</span></span> <span data-ttu-id="d6f48-136">또한 **이 명령은 timestampserver** 매개 변수를 사용 하 여 서명에 타임 스탬프를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-136">It also uses the **TimeStampServer** parameter to add a timestamp to the signature.</span></span>
<span data-ttu-id="d6f48-137">그러면 인증서가 만료되어도 스크립트에 오류가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-137">This prevents the script from failing when the certificate expires.</span></span>

## <span data-ttu-id="d6f48-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d6f48-138">PARAMETERS</span></span>

### <span data-ttu-id="d6f48-139">-인증서</span><span class="sxs-lookup"><span data-stu-id="d6f48-139">-Certificate</span></span>

<span data-ttu-id="d6f48-140">스크립트 또는 파일을 서명하는 데 사용할 인증서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-140">Specifies the certificate that will be used to sign the script or file.</span></span> <span data-ttu-id="d6f48-141">인증서를 나타내는 개체 또는 인증서를 가져오는 식을 저장할 변수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-141">Enter a variable that stores an object representing the certificate or an expression that gets the certificate.</span></span>

<span data-ttu-id="d6f48-142">인증서를 찾으려면를 사용 `Get-PfxCertificate` 하거나 `Get-ChildItem` 인증서 드라이브에서 cmdlet을 사용 `Cert:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-142">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate `Cert:` drive.</span></span> <span data-ttu-id="d6f48-143">인증서가 유효 하지 않거나 권한이 없는 경우 `code-signing` 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-143">If the certificate is not valid or does not have `code-signing` authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d6f48-144">-FilePath</span><span class="sxs-lookup"><span data-stu-id="d6f48-144">-FilePath</span></span>

<span data-ttu-id="d6f48-145">서명할 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-145">Specifies the path to a file that is being signed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d6f48-146">-Force</span><span class="sxs-lookup"><span data-stu-id="d6f48-146">-Force</span></span>

<span data-ttu-id="d6f48-147">cmdlet이 읽기 전용 파일에 서명을 추가할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-147">Allows the cmdlet to append a signature to a read-only file.</span></span> <span data-ttu-id="d6f48-148">**Force** 매개 변수를 사용 하는 경우에도 cmdlet은 보안 제한을 재정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-148">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d6f48-149">-HashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="d6f48-149">-HashAlgorithm</span></span>

<span data-ttu-id="d6f48-150">Windows에서 파일의 디지털 서명을 컴퓨팅하는 데 사용하는 해싱 알고리즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-150">Specifies the hashing algorithm that Windows uses to compute the digital signature for the file.</span></span>

<span data-ttu-id="d6f48-151">PowerShell 3.0의 경우 기본값은 Windows 기본 해싱 알고리즘인 SHA256입니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-151">For PowerShell 3.0, the default is SHA256, which is the Windows default hashing algorithm.</span></span> <span data-ttu-id="d6f48-152">PowerShell 2.0의 경우 기본값은 SHA1입니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-152">For PowerShell 2.0, the default is SHA1.</span></span> <span data-ttu-id="d6f48-153">다른 해싱 알고리즘으로 서명된 파일은 다른 시스템에서 인식되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-153">Files that are signed with a different hashing algorithm might not be recognized on other systems.</span></span> <span data-ttu-id="d6f48-154">지원 되는 알고리즘은 운영 체제의 버전에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-154">Which algorithms are supported depends on the version of the operating system.</span></span>

<span data-ttu-id="d6f48-155">가능한 값 목록은 [HashAlgorithmName 구조체](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d6f48-155">For a list of possible values, see [HashAlgorithmName Struct](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SHA256
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d6f48-156">-명령은 includechain</span><span class="sxs-lookup"><span data-stu-id="d6f48-156">-IncludeChain</span></span>

<span data-ttu-id="d6f48-157">인증서 신뢰 체인의 인증서가 디지털 서명에 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-157">Determines which certificates in the certificate trust chain are included in the digital signature.</span></span>
<span data-ttu-id="d6f48-158">**Notroot** 는 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-158">**NotRoot** is the default.</span></span>

<span data-ttu-id="d6f48-159">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-159">Valid values are:</span></span>

- <span data-ttu-id="d6f48-160">서명자: 서명자의 인증서만 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-160">Signer: Includes only the signer's certificate.</span></span>
- <span data-ttu-id="d6f48-161">NotRoot: 루트 인증 기관을 제외 하 고 인증서 체인의 모든 인증서를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-161">NotRoot: Includes all of the certificates in the certificate chain, except for the root authority.</span></span>
- <span data-ttu-id="d6f48-162">모두: 인증서 체인의 모든 인증서를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-162">All: Includes all the certificates in the certificate chain.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: NotRoot
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d6f48-163">-이 명령은 timestampserver</span><span class="sxs-lookup"><span data-stu-id="d6f48-163">-TimestampServer</span></span>

<span data-ttu-id="d6f48-164">지정된 타임스탬프 서버를 사용하여 서명에 타임스탬프를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-164">Uses the specified time stamp server to add a time stamp to the signature.</span></span> <span data-ttu-id="d6f48-165">타임스탬프 서버의 URL을 문자열로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-165">Type the URL of the time stamp server as a string.</span></span>

<span data-ttu-id="d6f48-166">타임스탬프는 인증서를 파일에 추가한 정확한 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-166">The time stamp represents the exact time that the certificate was added to the file.</span></span> <span data-ttu-id="d6f48-167">타임스탬프를 사용하면 사용자 및 프로그램에서 서명 당시 인증서가 유효했는지를 확인할 수 있으므로 인증서가 만료되어도 스크립트 오류를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-167">A time stamp prevents the script from failing if the certificate expires because users and programs can verify that the certificate was valid at the time of signing.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d6f48-168">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d6f48-168">-LiteralPath</span></span>

<span data-ttu-id="d6f48-169">서명할 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-169">Specifies the path to a file that is being signed.</span></span> <span data-ttu-id="d6f48-170">**FilePath** 와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-170">Unlike **FilePath** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="d6f48-171">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-171">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="d6f48-172">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="d6f48-172">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="d6f48-173">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-173">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d6f48-174">-SourcePathOrExtension</span><span class="sxs-lookup"><span data-stu-id="d6f48-174">-SourcePathOrExtension</span></span>

<span data-ttu-id="d6f48-175">디지털 서명이 추가 된 콘텐츠의 파일 또는 파일 형식에 대 한 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-175">Path to the file or file type of the content for which the digital signature is added.</span></span> <span data-ttu-id="d6f48-176">이 매개 변수는 파일 콘텐츠가 바이트 배열로 전달 되는 **콘텐츠와** 함께 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-176">This parameter is used with **Content** where file content is passed as a byte array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d6f48-177">-콘텐츠</span><span class="sxs-lookup"><span data-stu-id="d6f48-177">-Content</span></span>

<span data-ttu-id="d6f48-178">디지털 서명을 추가 하는 바이트 배열인 파일의 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-178">Contents of a file as a byte array for which the digital signature is added.</span></span> <span data-ttu-id="d6f48-179">이 매개 변수는 **SourcePathOrExtension** 매개 변수와 함께 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-179">This parameter must be used with **SourcePathOrExtension** parameter.</span></span> <span data-ttu-id="d6f48-180">파일의 내용은 유니코드 (UTF-16LE) 형식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-180">The contents of the file must be in Unicode (UTF-16LE) format.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d6f48-181">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d6f48-181">-Confirm</span></span>

<span data-ttu-id="d6f48-182">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-182">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d6f48-183">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d6f48-183">-WhatIf</span></span>

<span data-ttu-id="d6f48-184">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-184">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d6f48-185">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f48-185">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d6f48-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d6f48-186">CommonParameters</span></span>

<span data-ttu-id="d6f48-187">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d6f48-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d6f48-188">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6f48-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d6f48-189">입력</span><span class="sxs-lookup"><span data-stu-id="d6f48-189">INPUTS</span></span>

### <span data-ttu-id="d6f48-190">System.String</span><span class="sxs-lookup"><span data-stu-id="d6f48-190">System.String</span></span>

<span data-ttu-id="d6f48-191">파일 경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Set-AuthenticodeSignature` .</span><span class="sxs-lookup"><span data-stu-id="d6f48-191">You can pipe a string that contains the file path to `Set-AuthenticodeSignature`.</span></span>

## <span data-ttu-id="d6f48-192">출력</span><span class="sxs-lookup"><span data-stu-id="d6f48-192">OUTPUTS</span></span>

### <span data-ttu-id="d6f48-193">System.object..</span><span class="sxs-lookup"><span data-stu-id="d6f48-193">System.Management.Automation.Signature</span></span>

## <span data-ttu-id="d6f48-194">참고</span><span class="sxs-lookup"><span data-stu-id="d6f48-194">NOTES</span></span>

## <span data-ttu-id="d6f48-195">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d6f48-195">RELATED LINKS</span></span>

[<span data-ttu-id="d6f48-196">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="d6f48-196">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="d6f48-197">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="d6f48-197">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="d6f48-198">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="d6f48-198">Get-PfxCertificate</span></span>](Get-PfxCertificate.md)

[<span data-ttu-id="d6f48-199">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="d6f48-199">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

[<span data-ttu-id="d6f48-200">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="d6f48-200">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="d6f48-201">about_Signing</span><span class="sxs-lookup"><span data-stu-id="d6f48-201">about_Signing</span></span>](../Microsoft.PowerShell.Core/About/about_Signing.md)
