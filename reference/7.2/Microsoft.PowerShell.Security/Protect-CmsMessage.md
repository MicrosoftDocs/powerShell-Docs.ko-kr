---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/protect-cmsmessage?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Protect-CmsMessage
ms.openlocfilehash: 57213b72bee5733f6e8089ff7dcbb9be82104d8a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602260"
---
# <span data-ttu-id="36279-102">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="36279-102">Protect-CmsMessage</span></span>

## <span data-ttu-id="36279-103">개요</span><span class="sxs-lookup"><span data-stu-id="36279-103">SYNOPSIS</span></span>
<span data-ttu-id="36279-104">암호화 메시지 구문 형식을 사용 하 여 콘텐츠를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="36279-104">Encrypts content by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="36279-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="36279-105">SYNTAX</span></span>

### <span data-ttu-id="36279-106">ByContent (기본값)</span><span class="sxs-lookup"><span data-stu-id="36279-106">ByContent (Default)</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <PSObject> [[-OutFile] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="36279-107">ByPath</span><span class="sxs-lookup"><span data-stu-id="36279-107">ByPath</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <String> [[-OutFile] <String>] [<CommonParameters>]
```

### <span data-ttu-id="36279-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="36279-108">ByLiteralPath</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <String> [[-OutFile] <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="36279-109">설명</span><span class="sxs-lookup"><span data-stu-id="36279-109">DESCRIPTION</span></span>

<span data-ttu-id="36279-110">`Protect-CmsMessage`Cmdlet은 CMS (암호화 메시지 구문) 형식을 사용 하 여 콘텐츠를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="36279-110">The `Protect-CmsMessage` cmdlet encrypts content by using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="36279-111">CMS cmdlet은 [RFC5652](https://tools.ietf.org/html/rfc5652.html)에 설명 된 대로 IETF 형식을 사용 하 여 콘텐츠의 암호화 및 암호 해독을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="36279-111">The CMS cmdlets support encryption and decryption of content using the IETF format as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="36279-112">CMS 암호화 표준은 공개 키 암호화를 사용 합니다. 여기서는 콘텐츠를 암호화 하는 데 사용 되는 키 (공개 키)와 콘텐츠를 암호 해독 하는 데 사용 되는 키 (개인 키)가 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36279-112">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="36279-113">공개 키는 광범위하게 공유할 수 있으며 중요한 데이터가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="36279-113">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="36279-114">콘텐츠가 이 퍼블릭 키로 암호화된 경우 프라이빗 키로만 암호 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36279-114">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="36279-115">자세한 내용은 [공개 키 암호화](https://en.wikipedia.org/wiki/Public-key_cryptography)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="36279-115">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="36279-116">Cmdlet을 실행 하려면 먼저 `Protect-CmsMessage` 암호화 인증서를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36279-116">Before you can run the `Protect-CmsMessage` cmdlet, you must have an encryption certificate set up.</span></span>
<span data-ttu-id="36279-117">PowerShell에서 인식할 수 있도록 암호화 인증서에는 데이터 암호화 인증서 (예: 코드 서명 및 암호화 된 메일의 Id)로 식별 하는 고유[EKU](/windows/desktop/SecCrypto/eku)(확장 키 사용) ID가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="36279-117">To be recognized in PowerShell, encryption certificates require a unique extended key usage ([EKU](/windows/desktop/SecCrypto/eku)) ID to identify them as data encryption certificates (such as the IDs for Code Signing and Encrypted Mail).</span></span> <span data-ttu-id="36279-118">문서 암호화에 사용할 수 있는 인증서의 예는이 항목의 예 1을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="36279-118">For an example of a certificate that would work for document encryption, see Example 1 in this topic.</span></span>

<span data-ttu-id="36279-119">PowerShell 7.1에 Linux 및 macOS에 대 한 지원이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="36279-119">Support for Linux and macOS was added in PowerShell 7.1.</span></span>

## <span data-ttu-id="36279-120">예제</span><span class="sxs-lookup"><span data-stu-id="36279-120">EXAMPLES</span></span>

### <span data-ttu-id="36279-121">예제 1: 콘텐츠 암호화를 위한 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="36279-121">Example 1: Create a certificate for encrypting content</span></span>

<span data-ttu-id="36279-122">Cmdlet을 실행 하려면 먼저 `Protect-CmsMessage` 암호화 인증서를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36279-122">Before you can run the `Protect-CmsMessage` cmdlet, you must create an encryption certificate.</span></span> <span data-ttu-id="36279-123">다음 텍스트를 사용 하 여 제목 줄의 이름을 이름, 전자 메일 또는 기타 식별자로 변경 하 고 인증서를 파일에 저장 합니다 (예: `DocumentEncryption.inf` 이 예제에 표시 된 것 처럼).</span><span class="sxs-lookup"><span data-stu-id="36279-123">Using the following text, change the name in the Subject line to your name, email, or other identifier, and save the certificate in a file (such as `DocumentEncryption.inf`, as shown in this example).</span></span>

```powershell
# Create .INF file for certreq
{[Version]
Signature = "$Windows NT$"

[Strings]
szOID_ENHANCED_KEY_USAGE = "2.5.29.37"
szOID_DOCUMENT_ENCRYPTION = "1.3.6.1.4.1.311.80.1"

[NewRequest]
Subject = "cn=youralias@emailaddress.com"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT_KEY_ENCIPHERMENT_KEY_USAGE | CERT_DATA_ENCIPHERMENT_KEY_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"

[Extensions]
%szOID_ENHANCED_KEY_USAGE% = "{text}%szOID_DOCUMENT_ENCRYPTION%"
} | Out-File -FilePath DocumentEncryption.inf

# After you have created your certificate file, run the following command to add
# the certificate file to the certificate store. Now you are ready to encrypt and
# decrypt content with the next two examples.
certreq.exe -new DocumentEncryption.inf DocumentEncryption.cer
```

### <span data-ttu-id="36279-124">예 2: 전자 메일로 보낸 메시지 암호화</span><span class="sxs-lookup"><span data-stu-id="36279-124">Example 2: Encrypt a message sent by email</span></span>

```powershell
$Protected = "Hello World" | Protect-CmsMessage -To "*youralias@emailaddress.com*"
```

<span data-ttu-id="36279-125">다음 예에서는 "헬로 월드" 메시지를 cmdlet으로 파이프 하 여 암호화 한 `Protect-CmsMessage` 다음 암호화 된 메시지를 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="36279-125">In the following example, you encrypt a message, "Hello World", by piping it to the `Protect-CmsMessage` cmdlet, and then save the encrypted message in a variable.</span></span> <span data-ttu-id="36279-126">**To** 매개 변수는 인증서의 제목 줄 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36279-126">The **To** parameter uses the value of the Subject line in the certificate.</span></span>

### <span data-ttu-id="36279-127">예제 3: 문서 암호화 인증서 보기</span><span class="sxs-lookup"><span data-stu-id="36279-127">Example 3: View document encryption certificates</span></span>

```
PS C:\> cd Cert:\CurrentUser\My
PS Cert:\CurrentUser\My> Get-ChildItem -DocumentEncryptionCert
```

<span data-ttu-id="36279-128">인증서 공급자에서 문서 암호화 인증서를 보려면 인증서 공급자가 로드 된 경우에만 사용할 수 있는 [Get ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)의 **documentencryptioncert** 동적 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36279-128">To view document encryption certificates in the certificate provider, you can add the **DocumentEncryptionCert** dynamic parameter of [Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md), available only when the certificate provider is loaded.</span></span>

## <span data-ttu-id="36279-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="36279-129">PARAMETERS</span></span>

### <span data-ttu-id="36279-130">-콘텐츠</span><span class="sxs-lookup"><span data-stu-id="36279-130">-Content</span></span>

<span data-ttu-id="36279-131">암호화 하려는 콘텐츠를 포함 하는 **PSObject** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36279-131">Specifies a **PSObject** that contains content that you want to encrypt.</span></span> <span data-ttu-id="36279-132">예를 들어 이벤트 메시지의 내용을 암호화 한 다음, 메시지 (이 예제에서는)를 포함 하는 변수를 `$Event` **콘텐츠** 매개 변수의 값으로 사용할 수 있습니다 `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1` .</span><span class="sxs-lookup"><span data-stu-id="36279-132">For example, you can encrypt the content of an event message, and then use the variable containing the message (`$Event`, in this example) as the value of the **Content** parameter: `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1`.</span></span> <span data-ttu-id="36279-133">Cmdlet을 사용 하 여 `Get-Content` Microsoft Word 문서와 같은 파일의 내용을 가져오고 **콘텐츠** 매개 변수 값으로 사용 하는 변수에 콘텐츠를 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36279-133">You can also use the `Get-Content` cmdlet to get the contents of a file, such as a Microsoft Word document, and save the content in a variable that you use as the value of the **Content** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByContent
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="36279-134">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="36279-134">-LiteralPath</span></span>

<span data-ttu-id="36279-135">암호화 하려는 콘텐츠의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36279-135">Specifies the path to content that you want to encrypt.</span></span> <span data-ttu-id="36279-136">**Path** 와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="36279-136">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="36279-137">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36279-137">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="36279-138">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="36279-138">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="36279-139">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36279-139">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36279-140">-출력</span><span class="sxs-lookup"><span data-stu-id="36279-140">-OutFile</span></span>

<span data-ttu-id="36279-141">암호화 된 콘텐츠를 전송 하려는 파일의 경로와 파일 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36279-141">Specifies the path and file name of a file to which you want to send the encrypted content.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36279-142">-Path</span><span class="sxs-lookup"><span data-stu-id="36279-142">-Path</span></span>

<span data-ttu-id="36279-143">암호화 하려는 콘텐츠의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36279-143">Specifies the path to content that you want to encrypt.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36279-144">-To</span><span class="sxs-lookup"><span data-stu-id="36279-144">-To</span></span>

<span data-ttu-id="36279-145">다음 형식으로 식별 된 하나 이상의 CMS 메시지 받는 사람을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36279-145">Specifies one or more CMS message recipients, identified in any of the following formats:</span></span>

- <span data-ttu-id="36279-146">실제 인증서 (인증서 공급자에서 검색 됨)</span><span class="sxs-lookup"><span data-stu-id="36279-146">An actual certificate (as retrieved from the certificate provider).</span></span>
- <span data-ttu-id="36279-147">인증서를 포함 하는 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="36279-147">Path to the file containing the certificate.</span></span>
- <span data-ttu-id="36279-148">인증서를 포함 하는 디렉터리의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="36279-148">Path to a directory containing the certificate.</span></span>
- <span data-ttu-id="36279-149">인증서의 지문 (인증서 저장소를 찾는 데 사용 됨)</span><span class="sxs-lookup"><span data-stu-id="36279-149">Thumbprint of the certificate (used to look in the certificate store).</span></span>
- <span data-ttu-id="36279-150">인증서 저장소를 찾는 데 사용 되는 인증서의 주체 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="36279-150">Subject name of the certificate (used to look in the certificate store).</span></span>

```yaml
Type: System.Management.Automation.CmsMessageRecipient[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36279-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36279-151">CommonParameters</span></span>

<span data-ttu-id="36279-152">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="36279-152">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="36279-153">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="36279-153">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="36279-154">입력</span><span class="sxs-lookup"><span data-stu-id="36279-154">INPUTS</span></span>

## <span data-ttu-id="36279-155">출력</span><span class="sxs-lookup"><span data-stu-id="36279-155">OUTPUTS</span></span>

## <span data-ttu-id="36279-156">참고</span><span class="sxs-lookup"><span data-stu-id="36279-156">NOTES</span></span>

## <span data-ttu-id="36279-157">관련 링크</span><span class="sxs-lookup"><span data-stu-id="36279-157">RELATED LINKS</span></span>

[<span data-ttu-id="36279-158">about_Providers</span><span class="sxs-lookup"><span data-stu-id="36279-158">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="36279-159">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="36279-159">Get-CmsMessage</span></span>](Get-CmsMessage.md)

[<span data-ttu-id="36279-160">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="36279-160">Unprotect-CmsMessage</span></span>](Unprotect-CmsMessage.md)