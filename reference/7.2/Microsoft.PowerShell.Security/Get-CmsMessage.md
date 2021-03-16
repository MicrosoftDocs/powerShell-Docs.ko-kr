---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-cmsmessage?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CmsMessage
ms.openlocfilehash: 421b49139f4750787b6c1c04d8a41a624755109a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600848"
---
# <span data-ttu-id="6524d-102">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="6524d-102">Get-CmsMessage</span></span>

## <span data-ttu-id="6524d-103">개요</span><span class="sxs-lookup"><span data-stu-id="6524d-103">SYNOPSIS</span></span>
<span data-ttu-id="6524d-104">암호화 메시지 구문 형식을 사용 하 여 암호화 된 콘텐츠를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-104">Gets content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="6524d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6524d-105">SYNTAX</span></span>

### <span data-ttu-id="6524d-106">ByContent</span><span class="sxs-lookup"><span data-stu-id="6524d-106">ByContent</span></span>

```
Get-CmsMessage [-Content] <String> [<CommonParameters>]
```

### <span data-ttu-id="6524d-107">ByPath</span><span class="sxs-lookup"><span data-stu-id="6524d-107">ByPath</span></span>

```
Get-CmsMessage [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="6524d-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="6524d-108">ByLiteralPath</span></span>

```
Get-CmsMessage [-LiteralPath] <String> [<CommonParameters>]
```

## <span data-ttu-id="6524d-109">설명</span><span class="sxs-lookup"><span data-stu-id="6524d-109">DESCRIPTION</span></span>

<span data-ttu-id="6524d-110">`Get-CmsMessage`Cmdlet은 CMS (암호화 메시지 구문) 형식을 사용 하 여 암호화 된 콘텐츠를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-110">The `Get-CmsMessage` cmdlet gets content that has been encrypted using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="6524d-111">CMS cmdlet은 [RFC5652](https://tools.ietf.org/html/rfc5652)에 설명 된 대로 암호화 된 메시지를 보호 하기 위해 IETF 형식을 사용 하 여 콘텐츠의 암호화 및 암호 해독을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-111">The CMS cmdlets support encryption and decryption of content using the IETF format for cryptographically protecting messages, as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

<span data-ttu-id="6524d-112">CMS 암호화 표준은 공개 키 암호화를 사용 합니다. 여기서는 콘텐츠를 암호화 하는 데 사용 되는 키 (공개 키)와 콘텐츠를 암호 해독 하는 데 사용 되는 키 (개인 키)가 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-112">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="6524d-113">공개 키는 광범위하게 공유할 수 있으며 중요한 데이터가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-113">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="6524d-114">콘텐츠가 이 퍼블릭 키로 암호화된 경우 프라이빗 키로만 암호 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-114">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="6524d-115">자세한 내용은 [공개 키 암호화](https://en.wikipedia.org/wiki/Public-key_cryptography)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6524d-115">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="6524d-116">`Get-CmsMessage` CMS 형식으로 암호화 된 콘텐츠를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-116">`Get-CmsMessage` gets content that has been encrypted in CMS format.</span></span> <span data-ttu-id="6524d-117">콘텐츠를 해독 하거나 보호를 해제 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-117">It does not decrypt or unprotect content.</span></span> <span data-ttu-id="6524d-118">이 cmdlet을 실행 하 여 cmdlet을 실행 하 여 암호화 한 콘텐츠를 가져올 수 있습니다 `Protect-CmsMessage` .</span><span class="sxs-lookup"><span data-stu-id="6524d-118">You can run this cmdlet to get content that you have encrypted by running the `Protect-CmsMessage` cmdlet.</span></span> <span data-ttu-id="6524d-119">암호화 된 내용에 대 한 경로를 통해 문자열로 해독 하려는 콘텐츠를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-119">You can specify content that you want to decrypt as a string, or by path to the encrypted content.</span></span> <span data-ttu-id="6524d-120">`Get-CmsMessage` `Unprotect-CmsMessage` 콘텐츠를 암호화 하는 데 사용 된 문서 암호화 인증서에 대 한 정보가 있는 경우의 결과를로 파이프 하 여 콘텐츠의 암호를 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-120">You can pipe the results of `Get-CmsMessage` to `Unprotect-CmsMessage` to decrypt the content, provided that you have information about the document encryption certificate that was used to encrypt the content.</span></span>

<span data-ttu-id="6524d-121">PowerShell 7.1에 Linux 및 macOS에 대 한 지원이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-121">Support for Linux and macOS was added in PowerShell 7.1.</span></span>

## <span data-ttu-id="6524d-122">예제</span><span class="sxs-lookup"><span data-stu-id="6524d-122">EXAMPLES</span></span>

### <span data-ttu-id="6524d-123">예제 1: 암호화 된 콘텐츠 가져오기</span><span class="sxs-lookup"><span data-stu-id="6524d-123">Example 1: Get encrypted content</span></span>

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

<span data-ttu-id="6524d-124">이 명령은 C:\Users\Test\Documents\PowerShell\Future_Plans.txt에 있는 암호화 된 콘텐츠를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-124">This command gets encrypted content located at C:\Users\Test\Documents\PowerShell\Future_Plans.txt.</span></span>

### <span data-ttu-id="6524d-125">예제 2: Unprotect-CmsMessage로 암호화 된 콘텐츠 파이프</span><span class="sxs-lookup"><span data-stu-id="6524d-125">Example 2: Pipe encrypted content to Unprotect-CmsMessage</span></span>

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg | Unprotect-CmsMessage -To "cn=youralias@emailaddress.com"
```

```Output
Try the new Break All command
```

<span data-ttu-id="6524d-126">이 명령은 예제 1에서 cmdlet의 결과를 파이프 하 여 `Get-CmsMessage` `Unprotect-CmsMessage` 메시지의 암호를 해독 하 고 일반 텍스트로 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-126">This command pipes the results of the `Get-CmsMessage` cmdlet from Example 1 to `Unprotect-CmsMessage`, to decrypt the message and read it in plain text.</span></span> <span data-ttu-id="6524d-127">이 경우 **To** 매개 변수 값은 암호화 인증서의 제목 줄 값입니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-127">In this case, the value of the **To** parameter is the value of the encrypting certificate's Subject line.</span></span> <span data-ttu-id="6524d-128">해독 된 메시지 "새 중단 모두 실행 명령"이 결과에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-128">The decrypted message, "Try the new Break All command," is the result.</span></span>

## <span data-ttu-id="6524d-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6524d-129">PARAMETERS</span></span>

### <span data-ttu-id="6524d-130">-콘텐츠</span><span class="sxs-lookup"><span data-stu-id="6524d-130">-Content</span></span>

<span data-ttu-id="6524d-131">암호화 된 문자열 또는 암호화 된 문자열을 포함 하는 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-131">Specifies an encrypted string, or a variable containing an encrypted string.</span></span>

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

### <span data-ttu-id="6524d-132">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6524d-132">-LiteralPath</span></span>

<span data-ttu-id="6524d-133">가져올 암호화 된 콘텐츠의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-133">Specifies the path to encrypted content that you want to get.</span></span> <span data-ttu-id="6524d-134">**Path** 와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-134">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="6524d-135">어떠한 문자도 와일드카드 문자로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-135">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="6524d-136">경로에 이스케이프 문자가 포함 된 경우 각 항목을 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-136">If the path includes escape characters, enclose each one in single quotation marks.</span></span>
<span data-ttu-id="6524d-137">작은따옴표는 포함 된 문자를 이스케이프 문자로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-137">Single quotation marks tell PowerShell not to interpret enclosed characters as escape characters.</span></span>

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

### <span data-ttu-id="6524d-138">-Path</span><span class="sxs-lookup"><span data-stu-id="6524d-138">-Path</span></span>

<span data-ttu-id="6524d-139">해독 하려는 암호화 된 콘텐츠의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6524d-139">Specifies the path to encrypted content that you want to decrypt.</span></span>

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

### <span data-ttu-id="6524d-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6524d-140">CommonParameters</span></span>

<span data-ttu-id="6524d-141">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6524d-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6524d-142">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6524d-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6524d-143">입력</span><span class="sxs-lookup"><span data-stu-id="6524d-143">INPUTS</span></span>

## <span data-ttu-id="6524d-144">출력</span><span class="sxs-lookup"><span data-stu-id="6524d-144">OUTPUTS</span></span>

## <span data-ttu-id="6524d-145">참고</span><span class="sxs-lookup"><span data-stu-id="6524d-145">NOTES</span></span>

## <span data-ttu-id="6524d-146">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6524d-146">RELATED LINKS</span></span>

[<span data-ttu-id="6524d-147">about_Providers</span><span class="sxs-lookup"><span data-stu-id="6524d-147">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="6524d-148">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="6524d-148">Protect-CmsMessage</span></span>](Protect-CmsMessage.md)

[<span data-ttu-id="6524d-149">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="6524d-149">Unprotect-CmsMessage</span></span>](Unprotect-CmsMessage.md)
