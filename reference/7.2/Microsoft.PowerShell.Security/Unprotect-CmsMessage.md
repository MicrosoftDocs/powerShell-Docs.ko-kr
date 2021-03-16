---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/unprotect-cmsmessage?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unprotect-CmsMessage
ms.openlocfilehash: ed1c80a70e8fc51c242be6f9369f0a0bd44cb9c8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601075"
---
# <span data-ttu-id="00293-102">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="00293-102">Unprotect-CmsMessage</span></span>

## <span data-ttu-id="00293-103">개요</span><span class="sxs-lookup"><span data-stu-id="00293-103">SYNOPSIS</span></span>
<span data-ttu-id="00293-104">암호화 메시지 구문 형식을 사용 하 여 암호화 된 콘텐츠를 해독 합니다.</span><span class="sxs-lookup"><span data-stu-id="00293-104">Decrypts content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="00293-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="00293-105">SYNTAX</span></span>

### <span data-ttu-id="00293-106">ByWinEvent (기본값)</span><span class="sxs-lookup"><span data-stu-id="00293-106">ByWinEvent (Default)</span></span>

```
Unprotect-CmsMessage [-EventLogRecord] <PSObject> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="00293-107">ByContent</span><span class="sxs-lookup"><span data-stu-id="00293-107">ByContent</span></span>

```
Unprotect-CmsMessage [-Content] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### <span data-ttu-id="00293-108">ByPath</span><span class="sxs-lookup"><span data-stu-id="00293-108">ByPath</span></span>

```
Unprotect-CmsMessage [-Path] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### <span data-ttu-id="00293-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="00293-109">ByLiteralPath</span></span>

```
Unprotect-CmsMessage [-LiteralPath] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="00293-110">설명</span><span class="sxs-lookup"><span data-stu-id="00293-110">DESCRIPTION</span></span>

<span data-ttu-id="00293-111">`Unprotect-CmsMessage`Cmdlet은 CMS (암호화 메시지 구문) 형식을 사용 하 여 암호화 된 콘텐츠의 암호를 해독 합니다.</span><span class="sxs-lookup"><span data-stu-id="00293-111">The `Unprotect-CmsMessage` cmdlet decrypts content that has been encrypted by using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="00293-112">CMS cmdlet은 [RFC5652](https://tools.ietf.org/html/rfc5652)에 설명 된 대로 암호화 된 메시지를 보호 하기 위해 IETF 표준 형식을 사용 하 여 콘텐츠의 암호화 및 암호 해독을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="00293-112">The CMS cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages, as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

<span data-ttu-id="00293-113">CMS 암호화 표준은 공개 키 암호화를 사용 합니다. 여기서는 콘텐츠를 암호화 하는 데 사용 되는 키 (공개 키)와 콘텐츠를 암호 해독 하는 데 사용 되는 키 (개인 키)가 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="00293-113">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="00293-114">공개 키는 광범위하게 공유할 수 있으며 중요한 데이터가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="00293-114">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="00293-115">콘텐츠가 이 퍼블릭 키로 암호화된 경우 프라이빗 키로만 암호 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00293-115">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="00293-116">자세한 내용은 [공개 키 암호화](https://en.wikipedia.org/wiki/Public-key_cryptography)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00293-116">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="00293-117">`Unprotect-CmsMessage` CMS 형식으로 암호화 된 콘텐츠를 해독 합니다.</span><span class="sxs-lookup"><span data-stu-id="00293-117">`Unprotect-CmsMessage` decrypts content that has been encrypted in CMS format.</span></span> <span data-ttu-id="00293-118">이 cmdlet을 실행 하 여 cmdlet을 실행 하 여 암호화 한 콘텐츠의 암호를 해독할 수 있습니다 `Protect-CmsMessage` .</span><span class="sxs-lookup"><span data-stu-id="00293-118">You can run this cmdlet to decrypt content that you have encrypted by running the `Protect-CmsMessage` cmdlet.</span></span> <span data-ttu-id="00293-119">암호화 된 내용에 대 한 경로를 통해 암호화 이벤트 로그 레코드 ID 번호를 기준으로 암호 해독 하려는 콘텐츠를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00293-119">You can specify content that you want to decrypt as a string, by the encryption event log record ID number, or by path to the encrypted content.</span></span> <span data-ttu-id="00293-120">`Unprotect-CmsMessage`Cmdlet은 암호 해독 된 콘텐츠를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="00293-120">The `Unprotect-CmsMessage` cmdlet returns the decrypted content.</span></span>

<span data-ttu-id="00293-121">PowerShell 7.1에 Linux 및 macOS에 대 한 지원이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="00293-121">Support for Linux and macOS was added in PowerShell 7.1.</span></span>

## <span data-ttu-id="00293-122">예제</span><span class="sxs-lookup"><span data-stu-id="00293-122">EXAMPLES</span></span>

### <span data-ttu-id="00293-123">예제 1: 메시지 암호 해독</span><span class="sxs-lookup"><span data-stu-id="00293-123">Example 1: Decrypt a message</span></span>

<span data-ttu-id="00293-124">다음 예제에서는 리터럴 경로에 있는 콘텐츠의 암호를 해독 `C:\Users\Test\Documents\PowerShell` 합니다.</span><span class="sxs-lookup"><span data-stu-id="00293-124">In the following example, you decrypt content that is located at the literal path `C:\Users\Test\Documents\PowerShell`.</span></span> <span data-ttu-id="00293-125">필수 **To** 매개 변수 값의 경우이 예제에서는 암호화를 수행 하는 데 사용 된 인증서의 지문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="00293-125">For the value of the required **To** parameter, this example uses the thumbprint of the certificate that was used to perform the encryption.</span></span> <span data-ttu-id="00293-126">해독 된 메시지 "새 중단 모두 실행 명령"이 결과에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="00293-126">The decrypted message, "Try the new Break All command," is the result.</span></span>

```powershell
$parameters = @{
  LiteralPath = "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
  To = '0f 8j b1 ab e0 ce 35 1d 67 d2 f2 6f a2 d2 00 cl 22 z9 m9 85'
}
Unprotect-CmsMessage -LiteralPath @parameters
```

```Output
Try the new Break All command
```

## <span data-ttu-id="00293-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="00293-127">PARAMETERS</span></span>

### <span data-ttu-id="00293-128">-콘텐츠</span><span class="sxs-lookup"><span data-stu-id="00293-128">-Content</span></span>

<span data-ttu-id="00293-129">암호화 된 문자열 또는 암호화 된 문자열을 포함 하는 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00293-129">Specifies an encrypted string, or a variable containing an encrypted string.</span></span>

```yaml
Type: System.String
Parameter Sets: ByContent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="00293-130">-EventLogRecord</span><span class="sxs-lookup"><span data-stu-id="00293-130">-EventLogRecord</span></span>

<span data-ttu-id="00293-131">CMS 암호화 작업을 나타내는 이벤트 로그 레코드 ID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00293-131">Specifies an event log record ID that represents a CMS encryption operation.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByWinEvent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="00293-132">-IncludeContext</span><span class="sxs-lookup"><span data-stu-id="00293-132">-IncludeContext</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00293-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="00293-133">-LiteralPath</span></span>

<span data-ttu-id="00293-134">해독 하려는 암호화 된 콘텐츠의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00293-134">Specifies the path to encrypted content that you want to decrypt.</span></span> <span data-ttu-id="00293-135">**Path** 와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="00293-135">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="00293-136">어떠한 문자도 와일드카드 문자로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00293-136">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="00293-137">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="00293-137">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="00293-138">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="00293-138">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00293-139">-Path</span><span class="sxs-lookup"><span data-stu-id="00293-139">-Path</span></span>

<span data-ttu-id="00293-140">해독 하려는 암호화 된 콘텐츠의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00293-140">Specifies the path to encrypted content that you want to decrypt.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00293-141">-To</span><span class="sxs-lookup"><span data-stu-id="00293-141">-To</span></span>

<span data-ttu-id="00293-142">다음 형식으로 식별 된 하나 이상의 CMS 메시지 받는 사람을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00293-142">Specifies one or more CMS message recipients, identified in any of the following formats:</span></span>

- <span data-ttu-id="00293-143">실제 인증서 (인증서 공급자에서 검색 됨)</span><span class="sxs-lookup"><span data-stu-id="00293-143">An actual certificate (as retrieved from the certificate provider).</span></span>
- <span data-ttu-id="00293-144">인증서를 포함 하는 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="00293-144">Path to the a file containing the certificate.</span></span>
- <span data-ttu-id="00293-145">인증서를 포함 하는 디렉터리의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="00293-145">Path to a directory containing the certificate.</span></span>
- <span data-ttu-id="00293-146">인증서의 지문 (인증서 저장소를 찾는 데 사용 됨)</span><span class="sxs-lookup"><span data-stu-id="00293-146">Thumbprint of the certificate (used to look in the certificate store).</span></span>
- <span data-ttu-id="00293-147">인증서 저장소를 찾는 데 사용 되는 인증서의 주체 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="00293-147">Subject name of the certificate (used to look in the certificate store).</span></span>

```yaml
Type: System.Management.Automation.CmsMessageRecipient[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00293-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="00293-148">CommonParameters</span></span>

<span data-ttu-id="00293-149">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="00293-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="00293-150">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00293-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="00293-151">입력</span><span class="sxs-lookup"><span data-stu-id="00293-151">INPUTS</span></span>

### <span data-ttu-id="00293-152">EventLogRecord 또는 System.string이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00293-152">System.Diagnostics.Eventing.Reader.EventLogRecord or System.String</span></span>

<span data-ttu-id="00293-153">암호화 된 콘텐츠를 포함 하는 개체를로 파이프 할 수 있습니다 `Unprotect-CmsMessage` .</span><span class="sxs-lookup"><span data-stu-id="00293-153">You can pipe an object containing encrypted content to `Unprotect-CmsMessage`.</span></span>

## <span data-ttu-id="00293-154">출력</span><span class="sxs-lookup"><span data-stu-id="00293-154">OUTPUTS</span></span>

### <span data-ttu-id="00293-155">System.String</span><span class="sxs-lookup"><span data-stu-id="00293-155">System.String</span></span>

<span data-ttu-id="00293-156">암호화 되지 않은 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="00293-156">The unencrypted message.</span></span>

## <span data-ttu-id="00293-157">참고</span><span class="sxs-lookup"><span data-stu-id="00293-157">NOTES</span></span>

## <span data-ttu-id="00293-158">관련 링크</span><span class="sxs-lookup"><span data-stu-id="00293-158">RELATED LINKS</span></span>

[<span data-ttu-id="00293-159">about_Providers</span><span class="sxs-lookup"><span data-stu-id="00293-159">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="00293-160">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="00293-160">Get-CmsMessage</span></span>](Get-CmsMessage.md)

[<span data-ttu-id="00293-161">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="00293-161">Protect-CmsMessage</span></span>](Protect-CmsMessage.md)