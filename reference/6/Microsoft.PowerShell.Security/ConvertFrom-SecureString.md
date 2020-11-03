---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: 8a151da1b60b1956e580f9a0393d4eb137ef3447
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2020
ms.locfileid: "93217962"
---
# <span data-ttu-id="2f53d-103">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="2f53d-103">ConvertFrom-SecureString</span></span>

## <span data-ttu-id="2f53d-104">개요</span><span class="sxs-lookup"><span data-stu-id="2f53d-104">SYNOPSIS</span></span>
<span data-ttu-id="2f53d-105">보안 문자열을 암호화 된 표준 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-105">Converts a secure string to an encrypted standard string.</span></span>

## <span data-ttu-id="2f53d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2f53d-106">SYNTAX</span></span>

### <span data-ttu-id="2f53d-107">Secure (기본값)</span><span class="sxs-lookup"><span data-stu-id="2f53d-107">Secure (Default)</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### <span data-ttu-id="2f53d-108">열기</span><span class="sxs-lookup"><span data-stu-id="2f53d-108">Open</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-Key <Byte[]>] [<CommonParameters>]
```

## <span data-ttu-id="2f53d-109">설명</span><span class="sxs-lookup"><span data-stu-id="2f53d-109">DESCRIPTION</span></span>

<span data-ttu-id="2f53d-110">**Convertfrom-csv** cmdlet은 보안 문자열 ( **system.web** )을 암호화 된 표준 문자열 ( **system.string** )로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-110">The **ConvertFrom-SecureString** cmdlet converts a secure string ( **System.Security.SecureString** ) into an encrypted standard string ( **System.String** ).</span></span> <span data-ttu-id="2f53d-111">보안 문자열과 달리 암호화된 기본 문자열은 나중에 사용할 수 있도록 파일에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-111">Unlike a secure string, an encrypted standard string can be saved in a file for later use.</span></span> <span data-ttu-id="2f53d-112">암호화 된 표준 문자열은 cmdlet을 사용 하 여 보안 문자열 형식으로 다시 변환할 수 있습니다 `ConvertTo-SecureString` .</span><span class="sxs-lookup"><span data-stu-id="2f53d-112">The encrypted standard string can be converted back to its secure string format by using the `ConvertTo-SecureString` cmdlet.</span></span>

<span data-ttu-id="2f53d-113">**Key** 또는 **SecureKey** 매개 변수를 사용하여 암호화 키를 지정한 경우 AES(Advanced Encryption) 암호화 알고리즘이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-113">If an encryption key is specified by using the **Key** or **SecureKey** parameters, the Advanced Encryption Standard (AES) encryption algorithm is used.</span></span> <span data-ttu-id="2f53d-114">지정한 키 길이는 128, 192 및 256비트여야 합니다. AES 암호화 알고리즘에서 이러한 길이를 지원하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-114">The specified key must have a length of 128, 192, or 256 bits because those are the key lengths supported by the AES encryption algorithm.</span></span> <span data-ttu-id="2f53d-115">지정된 키가 없을 경우 Windows Data Protection API(DPAPI)가 기본 문자열 표현을 암호화하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-115">If no key is specified, the Windows Data Protection API (DPAPI) is used to encrypt the standard string representation.</span></span>

> [!NOTE]
> <span data-ttu-id="2f53d-116">[DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks)마다 SecureString의 콘텐츠는 비 Windows 시스템에서 암호화 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-116">Note that per [DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks), the contents of a SecureString are not encrypted on non-Windows systems.</span></span>

## <span data-ttu-id="2f53d-117">예제</span><span class="sxs-lookup"><span data-stu-id="2f53d-117">EXAMPLES</span></span>

### <span data-ttu-id="2f53d-118">예제 1: 보안 문자열 만들기</span><span class="sxs-lookup"><span data-stu-id="2f53d-118">Example 1: Create a secure string</span></span>

```powershell
$SecureString = Read-Host -AsSecureString
```

<span data-ttu-id="2f53d-119">이 명령은 명령 프롬프트에 입력된 문자에서 보안 문자열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-119">This command creates a secure string from characters that you type at the command prompt.</span></span> <span data-ttu-id="2f53d-120">명령을 입력한 다음 보안 문자열로 저장할 문자열을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="2f53d-120">After entering the command, type the string you want to store as a secure string.</span></span> <span data-ttu-id="2f53d-121">`*`입력 하는 각 문자를 나타내는 별표 ()가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-121">An asterisk (`*`) is displayed to represent each character that you type.</span></span>

### <span data-ttu-id="2f53d-122">예제 2: 보안 문자열을 암호화 된 표준 문자열로 변환</span><span class="sxs-lookup"><span data-stu-id="2f53d-122">Example 2: Convert a secure string to an encrypted standard string</span></span>

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

<span data-ttu-id="2f53d-123">이 명령은 변수의 보안 문자열 `$SecureString` 을 암호화 된 표준 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-123">This command converts the secure string in the `$SecureString` variable to an encrypted standard string.</span></span> <span data-ttu-id="2f53d-124">결과로 생성 되는 암호화 된 표준 문자열은 `$StandardString` 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-124">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

### <span data-ttu-id="2f53d-125">예제 3:192 비트 키를 사용 하 여 보안 문자열을 암호화 된 표준 문자열로 변환</span><span class="sxs-lookup"><span data-stu-id="2f53d-125">Example 3: Convert a secure string to an encrypted standard string with a 192-bit key</span></span>

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

<span data-ttu-id="2f53d-126">이러한 명령은 AES (AES(Advanced Encryption Standard)) 알고리즘을 사용 하 여 변수에 저장 된 보안 문자열을 `$SecureString` 192 비트 키를 사용 하는 암호화 된 표준 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-126">These commands use the Advanced Encryption Standard (AES) algorithm to convert the secure string stored in the `$SecureString` variable to an encrypted standard string with a 192-bit key.</span></span> <span data-ttu-id="2f53d-127">결과로 생성 되는 암호화 된 표준 문자열은 `$StandardString` 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-127">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

<span data-ttu-id="2f53d-128">첫 번째 명령은 변수에 키를 저장 합니다 `$Key` .</span><span class="sxs-lookup"><span data-stu-id="2f53d-128">The first command stores a key in the `$Key` variable.</span></span> <span data-ttu-id="2f53d-129">키는 24 개의 10 진수 숫자로 이루어진 배열이 며, 각 숫자는 부호 없는 단일 바이트에 맞게 256 미만 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-129">The key is an array of 24 decimal numerals, each of which must be less than 256 to fit within a single unsigned byte.</span></span>

<span data-ttu-id="2f53d-130">각 10 진수는 단일 바이트 (8 비트)를 나타내므로 키의 24 자리 숫자는 총 192 비트 (8 x 24)가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-130">Because each decimal numeral represents a single byte (8 bits), the key has 24 digits for a total of 192 bits (8 x 24).</span></span> <span data-ttu-id="2f53d-131">이것이 AES 알고리즘의 유효한 키 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-131">This is a valid key length for the AES algorithm.</span></span>

<span data-ttu-id="2f53d-132">두 번째 명령은 변수의 키를 사용 하 여 `$Key` 보안 문자열을 암호화 된 표준 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-132">The second command uses the key in the `$Key` variable to convert the secure string to an encrypted standard string.</span></span>

## <span data-ttu-id="2f53d-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2f53d-133">PARAMETERS</span></span>

### <span data-ttu-id="2f53d-134">-키</span><span class="sxs-lookup"><span data-stu-id="2f53d-134">-Key</span></span>

<span data-ttu-id="2f53d-135">암호화 키를 바이트 배열로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-135">Specifies the encryption key as a byte array.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: Open
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f53d-136">-SecureKey</span><span class="sxs-lookup"><span data-stu-id="2f53d-136">-SecureKey</span></span>

<span data-ttu-id="2f53d-137">암호화 키를 보안 문자열로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-137">Specifies the encryption key as a secure string.</span></span> <span data-ttu-id="2f53d-138">보안 문자열 값은 키로 사용되기 전에 바이트 배열로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-138">The secure string value is converted to a byte array before being used as the key.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: Secure
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f53d-139">-SecureString</span><span class="sxs-lookup"><span data-stu-id="2f53d-139">-SecureString</span></span>

<span data-ttu-id="2f53d-140">암호화된 기본 문자열로 변환할 보안 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-140">Specifies the secure string to convert to an encrypted standard string.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2f53d-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2f53d-141">CommonParameters</span></span>

<span data-ttu-id="2f53d-142">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-142">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`,`-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span>
<span data-ttu-id="2f53d-143">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f53d-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2f53d-144">입력</span><span class="sxs-lookup"><span data-stu-id="2f53d-144">INPUTS</span></span>

### <span data-ttu-id="2f53d-145">System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="2f53d-145">System.Security.SecureString</span></span>

<span data-ttu-id="2f53d-146">**Securestring** 개체를 convertfrom-csv에 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-146">You can pipe a **SecureString** object to ConvertFrom-SecureString.</span></span>

## <span data-ttu-id="2f53d-147">출력</span><span class="sxs-lookup"><span data-stu-id="2f53d-147">OUTPUTS</span></span>

### <span data-ttu-id="2f53d-148">System.String</span><span class="sxs-lookup"><span data-stu-id="2f53d-148">System.String</span></span>

<span data-ttu-id="2f53d-149">ConvertFrom-SecureString은 기본 문자열 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-149">ConvertFrom-SecureString returns a standard string object.</span></span>

## <span data-ttu-id="2f53d-150">참고</span><span class="sxs-lookup"><span data-stu-id="2f53d-150">NOTES</span></span>

- <span data-ttu-id="2f53d-151">명령 프롬프트에 입력 된 문자에서 보안 문자열을 만들려면 cmdlet의 **Assecurestring** 매개 변수를 사용 `Read-Host` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-151">To create a secure string from characters that are typed at the command prompt, use the **AsSecureString** parameter of the `Read-Host` cmdlet.</span></span>
- <span data-ttu-id="2f53d-152">**키 또는** **securekey** 매개 변수를 사용 하 여 키를 지정 하는 경우 키 길이가 정확 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-152">When you use the **Key** or **SecureKey** parameters to specify a key, the key length must be correct.</span></span> <span data-ttu-id="2f53d-153">예를 들어 128 비트의 키를 16 진수 숫자의 바이트 배열로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-153">For example, a key of 128 bits can be specified as a byte array of 16 decimal numerals.</span></span>
  <span data-ttu-id="2f53d-154">마찬가지로 192 비트 및 256 비트 키는 각각 24 및 32 10 진수 숫자의 바이트 배열에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-154">Similarly, 192-bit and 256-bit keys correspond to byte arrays of 24 and 32 decimal numerals, respectively.</span></span>
- <span data-ttu-id="2f53d-155">이모티콘 등의 일부 문자는 해당 문자를 포함 하는 문자열의 여러 코드 요소에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53d-155">Some characters, such as emoticons, correspond to several code points in the string that contains them.</span></span> <span data-ttu-id="2f53d-156">암호에 사용 되는 경우 문제 및 오해를 일으킬 수 있으므로 이러한 문자를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="2f53d-156">Avoid using these characters because they may cause problems and misunderstandings when used in a password.</span></span>

## <span data-ttu-id="2f53d-157">관련 링크</span><span class="sxs-lookup"><span data-stu-id="2f53d-157">RELATED LINKS</span></span>

[<span data-ttu-id="2f53d-158">ConvertTo-SecureString</span><span class="sxs-lookup"><span data-stu-id="2f53d-158">ConvertTo-SecureString</span></span>](ConvertTo-SecureString.md)

[<span data-ttu-id="2f53d-159">Read-Host</span><span class="sxs-lookup"><span data-stu-id="2f53d-159">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)
