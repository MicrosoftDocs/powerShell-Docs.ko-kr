---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-cmsmessage?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CmsMessage
ms.openlocfilehash: fcc4305ee5a7198f78eb7b6ce735cf45b90bbf6f
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344860"
---
# <span data-ttu-id="b2687-103">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="b2687-103">Get-CmsMessage</span></span>

## <span data-ttu-id="b2687-104">개요</span><span class="sxs-lookup"><span data-stu-id="b2687-104">SYNOPSIS</span></span>
<span data-ttu-id="b2687-105">암호화 메시지 구문 형식을 사용 하 여 암호화 된 콘텐츠를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-105">Gets content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="b2687-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b2687-106">SYNTAX</span></span>

### <span data-ttu-id="b2687-107">ByContent</span><span class="sxs-lookup"><span data-stu-id="b2687-107">ByContent</span></span>

```
Get-CmsMessage [-Content] <String> [<CommonParameters>]
```

### <span data-ttu-id="b2687-108">ByPath</span><span class="sxs-lookup"><span data-stu-id="b2687-108">ByPath</span></span>

```
Get-CmsMessage [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="b2687-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="b2687-109">ByLiteralPath</span></span>

```
Get-CmsMessage [-LiteralPath] <String> [<CommonParameters>]
```

## <span data-ttu-id="b2687-110">설명</span><span class="sxs-lookup"><span data-stu-id="b2687-110">DESCRIPTION</span></span>

<span data-ttu-id="b2687-111">`Get-CmsMessage`Cmdlet은 CMS (암호화 메시지 구문) 형식을 사용 하 여 암호화 된 콘텐츠를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-111">The `Get-CmsMessage` cmdlet gets content that has been encrypted using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="b2687-112">CMS cmdlet은 [RFC5652](https://tools.ietf.org/html/rfc5652)에 설명 된 대로 암호화 된 메시지를 보호 하기 위해 IETF 형식을 사용 하 여 콘텐츠의 암호화 및 암호 해독을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-112">The CMS cmdlets support encryption and decryption of content using the IETF format for cryptographically protecting messages, as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

<span data-ttu-id="b2687-113">CMS 암호화 표준은 공개 키 암호화를 사용 합니다. 여기서는 콘텐츠를 암호화 하는 데 사용 되는 키 (공개 키)와 콘텐츠를 암호 해독 하는 데 사용 되는 키 (개인 키)가 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-113">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="b2687-114">공개 키는 광범위하게 공유할 수 있으며 중요한 데이터가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-114">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="b2687-115">콘텐츠가 이 퍼블릭 키로 암호화된 경우 프라이빗 키로만 암호 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-115">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="b2687-116">자세한 내용은 [공개 키 암호화](https://en.wikipedia.org/wiki/Public-key_cryptography)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b2687-116">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="b2687-117">`Get-CmsMessage` CMS 형식으로 암호화 된 콘텐츠를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-117">`Get-CmsMessage` gets content that has been encrypted in CMS format.</span></span> <span data-ttu-id="b2687-118">콘텐츠를 해독 하거나 보호를 해제 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-118">It does not decrypt or unprotect content.</span></span> <span data-ttu-id="b2687-119">이 cmdlet을 실행 하 여 cmdlet을 실행 하 여 암호화 한 콘텐츠를 가져올 수 있습니다 `Protect-CmsMessage` .</span><span class="sxs-lookup"><span data-stu-id="b2687-119">You can run this cmdlet to get content that you have encrypted by running the `Protect-CmsMessage` cmdlet.</span></span> <span data-ttu-id="b2687-120">암호화 된 내용에 대 한 경로를 통해 문자열로 해독 하려는 콘텐츠를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-120">You can specify content that you want to decrypt as a string, or by path to the encrypted content.</span></span> <span data-ttu-id="b2687-121">`Get-CmsMessage` `Unprotect-CmsMessage` 콘텐츠를 암호화 하는 데 사용 된 문서 암호화 인증서에 대 한 정보가 있는 경우의 결과를로 파이프 하 여 콘텐츠의 암호를 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-121">You can pipe the results of `Get-CmsMessage` to `Unprotect-CmsMessage` to decrypt the content, provided that you have information about the document encryption certificate that was used to encrypt the content.</span></span>

> [!NOTE]
> <span data-ttu-id="b2687-122">이 cmdlet은 Windows 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-122">This cmdlet is only available on Windows.</span></span>

## <span data-ttu-id="b2687-123">예제</span><span class="sxs-lookup"><span data-stu-id="b2687-123">EXAMPLES</span></span>

### <span data-ttu-id="b2687-124">예제 1: 암호화 된 콘텐츠 가져오기</span><span class="sxs-lookup"><span data-stu-id="b2687-124">Example 1: Get encrypted content</span></span>

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg.Content
```

```Output
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMBFWxlZWhv
bG1AbGljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYP5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNXmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPRwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84AHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1AtDj7nSJc=
-----END CMS-----
```

<span data-ttu-id="b2687-125">이 명령은 C:\Users\Test\Documents\PowerShell\Future_Plans.txt에 있는 암호화 된 콘텐츠를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-125">This command gets encrypted content located at C:\Users\Test\Documents\PowerShell\Future_Plans.txt.</span></span>

### <span data-ttu-id="b2687-126">예제 2: Unprotect-CmsMessage로 암호화 된 콘텐츠 파이프</span><span class="sxs-lookup"><span data-stu-id="b2687-126">Example 2: Pipe encrypted content to Unprotect-CmsMessage</span></span>

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg | Unprotect-CmsMessage -To "cn=youralias@emailaddress.com"
```

```Output
Try the new Break All command
```

<span data-ttu-id="b2687-127">이 명령은 예제 1에서 cmdlet의 결과를 파이프 하 여 `Get-CmsMessage` `Unprotect-CmsMessage` 메시지의 암호를 해독 하 고 일반 텍스트로 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-127">This command pipes the results of the `Get-CmsMessage` cmdlet from Example 1 to `Unprotect-CmsMessage`, to decrypt the message and read it in plain text.</span></span> <span data-ttu-id="b2687-128">이 경우 **To** 매개 변수 값은 암호화 인증서의 제목 줄 값입니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-128">In this case, the value of the **To** parameter is the value of the encrypting certificate's Subject line.</span></span> <span data-ttu-id="b2687-129">해독 된 메시지 "새 중단 모두 실행 명령"이 결과에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-129">The decrypted message, "Try the new Break All command," is the result.</span></span>

## <span data-ttu-id="b2687-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b2687-130">PARAMETERS</span></span>

### <span data-ttu-id="b2687-131">-콘텐츠</span><span class="sxs-lookup"><span data-stu-id="b2687-131">-Content</span></span>

<span data-ttu-id="b2687-132">암호화 된 문자열 또는 암호화 된 문자열을 포함 하는 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-132">Specifies an encrypted string, or a variable containing an encrypted string.</span></span>

```yaml
Type: System.String
Parameter Sets: ByContent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b2687-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b2687-133">-LiteralPath</span></span>

<span data-ttu-id="b2687-134">가져올 암호화 된 콘텐츠의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-134">Specifies the path to encrypted content that you want to get.</span></span> <span data-ttu-id="b2687-135">**Path** 와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-135">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="b2687-136">어떠한 문자도 와일드카드 문자로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-136">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="b2687-137">경로에 이스케이프 문자가 포함 된 경우 각 항목을 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-137">If the path includes escape characters, enclose each one in single quotation marks.</span></span>
<span data-ttu-id="b2687-138">작은따옴표는 포함 된 문자를 이스케이프 문자로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-138">Single quotation marks tell PowerShell not to interpret enclosed characters as escape characters.</span></span>

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

### <span data-ttu-id="b2687-139">-Path</span><span class="sxs-lookup"><span data-stu-id="b2687-139">-Path</span></span>

<span data-ttu-id="b2687-140">해독 하려는 암호화 된 콘텐츠의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-140">Specifies the path to encrypted content that you want to decrypt.</span></span>

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

### <span data-ttu-id="b2687-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b2687-141">CommonParameters</span></span>

<span data-ttu-id="b2687-142">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b2687-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b2687-143">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b2687-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b2687-144">입력</span><span class="sxs-lookup"><span data-stu-id="b2687-144">INPUTS</span></span>

## <span data-ttu-id="b2687-145">출력</span><span class="sxs-lookup"><span data-stu-id="b2687-145">OUTPUTS</span></span>

## <span data-ttu-id="b2687-146">참고</span><span class="sxs-lookup"><span data-stu-id="b2687-146">NOTES</span></span>

<span data-ttu-id="b2687-147">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2687-147">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="b2687-148">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b2687-148">RELATED LINKS</span></span>

[<span data-ttu-id="b2687-149">about_Providers</span><span class="sxs-lookup"><span data-stu-id="b2687-149">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="b2687-150">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="b2687-150">Protect-CmsMessage</span></span>](Protect-CmsMessage.md)

[<span data-ttu-id="b2687-151">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="b2687-151">Unprotect-CmsMessage</span></span>](Unprotect-CmsMessage.md)
