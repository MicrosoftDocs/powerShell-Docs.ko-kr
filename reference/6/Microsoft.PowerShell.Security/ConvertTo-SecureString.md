---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertto-securestring?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-SecureString
ms.openlocfilehash: 71b2a36601281d148bed6742ce3f3cb78e11acf4
ms.sourcegitcommit: df80c558e9a4b89c9798f084bd04012ece15155c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2020
ms.locfileid: "93225161"
---
# <span data-ttu-id="ac7be-103">ConvertTo-SecureString</span><span class="sxs-lookup"><span data-stu-id="ac7be-103">ConvertTo-SecureString</span></span>

## <span data-ttu-id="ac7be-104">개요</span><span class="sxs-lookup"><span data-stu-id="ac7be-104">SYNOPSIS</span></span>
<span data-ttu-id="ac7be-105">일반 텍스트 또는 암호화 된 문자열을 보안 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-105">Converts plain text or encrypted strings to secure strings.</span></span>

## <span data-ttu-id="ac7be-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ac7be-106">SYNTAX</span></span>

### <span data-ttu-id="ac7be-107">Secure (기본값)</span><span class="sxs-lookup"><span data-stu-id="ac7be-107">Secure (Default)</span></span>

```
ConvertTo-SecureString [-String] <String> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### <span data-ttu-id="ac7be-108">일반 텍스트</span><span class="sxs-lookup"><span data-stu-id="ac7be-108">PlainText</span></span>

```
ConvertTo-SecureString [-String] <String> [-AsPlainText] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="ac7be-109">열기</span><span class="sxs-lookup"><span data-stu-id="ac7be-109">Open</span></span>

```
ConvertTo-SecureString [-String] <String> [-Key <Byte[]>] [<CommonParameters>]
```

## <span data-ttu-id="ac7be-110">설명</span><span class="sxs-lookup"><span data-stu-id="ac7be-110">DESCRIPTION</span></span>

<span data-ttu-id="ac7be-111">`ConvertTo-SecureString`Cmdlet은 암호화 된 표준 문자열을 보안 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-111">The `ConvertTo-SecureString` cmdlet converts encrypted standard strings into secure strings.</span></span> <span data-ttu-id="ac7be-112">또한 일반 텍스트를 보안 문자열로 변환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-112">It can also convert plain text to secure strings.</span></span> <span data-ttu-id="ac7be-113">및와 함께 사용 `ConvertFrom-SecureString` 됩니다 `Read-Host` .</span><span class="sxs-lookup"><span data-stu-id="ac7be-113">It is used with `ConvertFrom-SecureString` and `Read-Host`.</span></span> <span data-ttu-id="ac7be-114">Cmdlet에서 생성 된 보안 문자열은 **SecureString** 유형의 매개 변수가 필요한 cmdlet 또는 함수와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-114">The secure string created by the cmdlet can be used with cmdlets or functions that require a parameter of type **SecureString**.</span></span> <span data-ttu-id="ac7be-115">Cmdlet을 사용 하 여 보안 문자열을 암호화 된 표준 문자열로 다시 변환할 수 있습니다 `ConvertFrom-SecureString` .</span><span class="sxs-lookup"><span data-stu-id="ac7be-115">The secure string can be converted back to an encrypted, standard string using the `ConvertFrom-SecureString` cmdlet.</span></span> <span data-ttu-id="ac7be-116">이렇게 하면 나중에 사용할 수 있도록 문자열을 파일에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-116">This enables it to be stored in a file for later use.</span></span>

<span data-ttu-id="ac7be-117">변환 되는 표준 문자열이 지정 된 키를 사용 하 여 암호화 된 경우 `ConvertFrom-SecureString` 동일한 키를 cmdlet의 **키** 또는 **securekey** 매개 변수 값으로 제공 해야 합니다 `ConvertTo-SecureString` .</span><span class="sxs-lookup"><span data-stu-id="ac7be-117">If the standard string being converted was encrypted with `ConvertFrom-SecureString` using a specified key, that same key must be provided as the value of the **Key** or **SecureKey** parameter of the `ConvertTo-SecureString` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="ac7be-118">[DotNet](/dotnet/api/system.security.securestring#remarks)마다 SecureString의 콘텐츠는 비 Windows 시스템에서 암호화 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-118">Note that per [DotNet](/dotnet/api/system.security.securestring#remarks), the contents of a SecureString are not encrypted on non-Windows systems.</span></span>

## <span data-ttu-id="ac7be-119">예제</span><span class="sxs-lookup"><span data-stu-id="ac7be-119">EXAMPLES</span></span>

### <span data-ttu-id="ac7be-120">예제 1: 보안 문자열을 암호화 된 문자열로 변환</span><span class="sxs-lookup"><span data-stu-id="ac7be-120">Example 1: Convert a secure string to an encrypted string</span></span>

<span data-ttu-id="ac7be-121">이 예제에서는 사용자 입력에서 보안 문자열을 만들고 보안 문자열을 암호화된 표준 문자열로 변환한 다음 암호화된 표준 문자열을 보안 문자열로 다시 변환하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-121">This example shows how to create a secure string from user input, convert the secure string to an encrypted standard string, and then convert the encrypted standard string back to a secure string.</span></span>

```powershell
PS C:\> $Secure = Read-Host -AsSecureString
PS C:\> $Secure
System.Security.SecureString
PS C:\> $Encrypted = ConvertFrom-SecureString -SecureString $Secure
PS C:\> $Encrypted
01000000d08c9ddf0115d1118c7a00c04fc297eb010000001a114d45b8dd3f4aa11ad7c0abdae98000000000
02000000000003660000a8000000100000005df63cea84bfb7d70bd6842e7efa79820000000004800000a000
000010000000f10cd0f4a99a8d5814d94e0687d7430b100000008bf11f1960158405b2779613e9352c6d1400
0000e6b7bf46a9d485ff211b9b2a2df3bd6eb67aae41
PS C:\> $Secure2 = ConvertTo-SecureString -String $Encrypted
PS C:\> $Secure2
System.Security.SecureString
```

<span data-ttu-id="ac7be-122">첫 번째 명령은 cmdlet의 **Assecurestring** 매개 변수를 사용 하 여 `Read-Host` 보안 문자열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-122">The first command uses the **AsSecureString** parameter of the `Read-Host` cmdlet to create a secure string.</span></span> <span data-ttu-id="ac7be-123">명령을 입력 한 후 입력 하는 모든 문자는 보안 문자열로 변환 된 후 변수에 저장 됩니다 `$Secure` .</span><span class="sxs-lookup"><span data-stu-id="ac7be-123">After you enter the command, any characters that you type are converted into a secure string and then saved in the `$Secure` variable.</span></span>

<span data-ttu-id="ac7be-124">두 번째 명령은 변수의 내용을 표시 합니다 `$Secure` .</span><span class="sxs-lookup"><span data-stu-id="ac7be-124">The second command displays the contents of the `$Secure` variable.</span></span> <span data-ttu-id="ac7be-125">`$Secure`변수에 보안 문자열이 포함 되어 있으므로 PowerShell은 **system.object** 형식만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-125">Because the `$Secure` variable contains a secure string, PowerShell displays only the **System.Security.SecureString** type.</span></span>

<span data-ttu-id="ac7be-126">세 번째 명령은 cmdlet을 사용 하 여 `ConvertFrom-SecureString` 변수의 보안 문자열을 `$Secure` 암호화 된 표준 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-126">The third command uses the `ConvertFrom-SecureString` cmdlet to convert the secure string in the `$Secure` variable into an encrypted standard string.</span></span> <span data-ttu-id="ac7be-127">결과를 `$Encrypted` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-127">It saves the result in the `$Encrypted` variable.</span></span>

<span data-ttu-id="ac7be-128">네 번째 명령은 변수 값에 암호화 된 문자열을 표시 합니다 `$Encrypted` .</span><span class="sxs-lookup"><span data-stu-id="ac7be-128">The fourth command displays the encrypted string in the value of the `$Encrypted` variable.</span></span>

<span data-ttu-id="ac7be-129">다섯 번째 명령은 cmdlet을 사용 하 여 `ConvertTo-SecureString` 변수의 암호화 된 표준 문자열을 `$Encrypted` 다시 보안 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-129">The fifth command uses the `ConvertTo-SecureString` cmdlet to convert the encrypted standard string in the `$Encrypted` variable back into a secure string.</span></span> <span data-ttu-id="ac7be-130">결과를 `$Secure2` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-130">It saves the result in the `$Secure2` variable.</span></span>
<span data-ttu-id="ac7be-131">여섯 번째 명령은 변수의 값을 표시 합니다 `$Secure2` .</span><span class="sxs-lookup"><span data-stu-id="ac7be-131">The sixth command displays the value of the `$Secure2` variable.</span></span> <span data-ttu-id="ac7be-132">SecureString 유형은 명령이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-132">The SecureString type indicates that the command was successful.</span></span>

### <span data-ttu-id="ac7be-133">예제 2: 파일의 암호화 된 문자열에서 보안 문자열 만들기</span><span class="sxs-lookup"><span data-stu-id="ac7be-133">Example 2: Create a secure string from an encrypted string in a file</span></span>

<span data-ttu-id="ac7be-134">이 예제에서는 파일에 저장된 암호화된 표준 문자열에서 보안 문자열을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-134">This example shows how to create a secure string from an encrypted standard string that is saved in a file.</span></span>

```powershell
$Secure = Read-Host -AsSecureString
$Encrypted = ConvertFrom-SecureString -SecureString $Secure -Key (1..16)
$Encrypted | Set-Content Encrypted.txt
$Secure2 = Get-Content Encrypted.txt | ConvertTo-SecureString -Key (1..16)
```

<span data-ttu-id="ac7be-135">첫 번째 명령은 cmdlet의 **Assecurestring** 매개 변수를 사용 하 여 `Read-Host` 보안 문자열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-135">The first command uses the **AsSecureString** parameter of the `Read-Host` cmdlet to create a secure string.</span></span> <span data-ttu-id="ac7be-136">명령을 입력 한 후 입력 하는 모든 문자는 보안 문자열로 변환 된 후 변수에 저장 됩니다 `$Secure` .</span><span class="sxs-lookup"><span data-stu-id="ac7be-136">After you enter the command, any characters that you type are converted into a secure string and then saved in the `$Secure` variable.</span></span>

<span data-ttu-id="ac7be-137">두 번째 명령은 cmdlet을 사용 하 여 `ConvertFrom-SecureString` `$Secure` 지정 된 키를 사용 하 여 변수의 보안 문자열을 암호화 된 표준 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-137">The second command uses the `ConvertFrom-SecureString` cmdlet to convert the secure string in the `$Secure` variable into an encrypted standard string by using the specified key.</span></span> <span data-ttu-id="ac7be-138">콘텐츠는 변수에 저장 됩니다 `$Encrypted` .</span><span class="sxs-lookup"><span data-stu-id="ac7be-138">The contents are saved in the `$Encrypted` variable.</span></span>

<span data-ttu-id="ac7be-139">세 번째 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 변수 값을 `$Encrypted` cmdlet으로 보냅니다 `Set-Content` . 그러면이 cmdlet이 Encrypted.txt 파일에 값을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-139">The third command uses a pipeline operator (`|`) to send the value of the `$Encrypted` variable to the `Set-Content` cmdlet, which saves the value in the Encrypted.txt file.</span></span>

<span data-ttu-id="ac7be-140">네 번째 명령은 cmdlet을 사용 하 여 `Get-Content` Encrypted.txt 파일에서 암호화 된 표준 문자열을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-140">The fourth command uses the `Get-Content` cmdlet to get the encrypted standard string in the Encrypted.txt file.</span></span> <span data-ttu-id="ac7be-141">이 명령은 파이프라인 연산자를 사용 하 여 암호화 된 문자열을 cmdlet으로 보냅니다 `ConvertTo-SecureString` .이 cmdlet은 지정 된 키를 사용 하 여 보안 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-141">The command uses a pipeline operator to send the encrypted string to the `ConvertTo-SecureString` cmdlet, which converts it to a secure string by using the specified key.</span></span>
<span data-ttu-id="ac7be-142">결과는 변수에 저장 됩니다 `$Secure2` .</span><span class="sxs-lookup"><span data-stu-id="ac7be-142">The results are saved in the `$Secure2` variable.</span></span>

### <span data-ttu-id="ac7be-143">예제 3: 일반 텍스트 문자열을 보안 문자열로 변환</span><span class="sxs-lookup"><span data-stu-id="ac7be-143">Example 3: Convert a plain text string to a secure string</span></span>

<span data-ttu-id="ac7be-144">이 명령은 일반 텍스트 문자열을 `P@ssW0rD!` 보안 문자열로 변환 하 고 결과를 `$Secure_String_Pwd` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-144">This command converts the plain text string `P@ssW0rD!` into a secure string and stores the result in the `$Secure_String_Pwd` variable.</span></span> <span data-ttu-id="ac7be-145">**Asplaintext** 매개 변수를 사용 하려면 **Force** 매개 변수도 명령에 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-145">To use the **AsPlainText** parameter, the **Force** parameter must also be included in the command.</span></span>

```powershell
$Secure_String_Pwd = ConvertTo-SecureString "P@ssW0rD!" -AsPlainText -Force
```

> [!CAUTION]
> <span data-ttu-id="ac7be-146">스크립트나 명령줄에서 일반 텍스트 문자열을 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-146">You should avoid using plain text strings in script or from the command line.</span></span> <span data-ttu-id="ac7be-147">일반 텍스트는 이벤트 로그 및 명령 기록 로그에 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-147">The plain text can show up in event logs and command history logs.</span></span>

## <span data-ttu-id="ac7be-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ac7be-148">PARAMETERS</span></span>

### <span data-ttu-id="ac7be-149">-AsPlainText</span><span class="sxs-lookup"><span data-stu-id="ac7be-149">-AsPlainText</span></span>

<span data-ttu-id="ac7be-150">보안 문자열로 변환할 일반 텍스트 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-150">Specifies a plain text string to convert to a secure string.</span></span> <span data-ttu-id="ac7be-151">보안 문자열 cmdlet을 사용하여 기밀 텍스트를 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-151">The secure string cmdlets help protect confidential text.</span></span> <span data-ttu-id="ac7be-152">텍스트는 개인 정보 보호를 위해 암호화되며 사용한 후 컴퓨터 메모리에서 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-152">The text is encrypted for privacy and is deleted from computer memory after it is used.</span></span> <span data-ttu-id="ac7be-153">이 매개 변수를 사용하여 일반 텍스트를 입력으로 제공할 경우 시스템에서 이러한 방식으로 해당 입력을 보호할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-153">If you use this parameter to provide plain text as input, the system cannot protect that input in this manner.</span></span> <span data-ttu-id="ac7be-154">이 매개 변수를 사용 하려면 **Force** 매개 변수도 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-154">To use this parameter, you must also specify the **Force** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ac7be-155">-Force</span><span class="sxs-lookup"><span data-stu-id="ac7be-155">-Force</span></span>

<span data-ttu-id="ac7be-156">**Asplaintext** 매개 변수를 사용 하는 경우의 의미를 이해 하 고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-156">Confirms that you understand the implications of using the **AsPlainText** parameter and still want to use it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ac7be-157">-키</span><span class="sxs-lookup"><span data-stu-id="ac7be-157">-Key</span></span>

<span data-ttu-id="ac7be-158">원래 보안 문자열을 암호화 된 표준 문자열로 변환 하는 데 사용 되는 암호화 키를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-158">Specifies the encryption key used to convert the original secure string into the encrypted standard string.</span></span> <span data-ttu-id="ac7be-159">유효한 키 길이는 16, 24 및 32 바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-159">Valid key lengths are 16, 24 and 32 bytes.</span></span>

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

### <span data-ttu-id="ac7be-160">-SecureKey</span><span class="sxs-lookup"><span data-stu-id="ac7be-160">-SecureKey</span></span>

<span data-ttu-id="ac7be-161">원래 보안 문자열을 암호화 된 표준 문자열로 변환 하는 데 사용 되는 암호화 키를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-161">Specifies the encryption key used to convert the original secure string into the encrypted standard string.</span></span> <span data-ttu-id="ac7be-162">제공하는 키는 보안 문자열 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-162">The key must be provided in the format of a secure string.</span></span> <span data-ttu-id="ac7be-163">보안 문자열은 키로 사용할 바이트 배열로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-163">The secure string will be converted to a byte array to be used as the key.</span></span> <span data-ttu-id="ac7be-164">유효한 보안 키 길이는 8, 12 및 16 코드 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-164">Valid secure key lengths are 8, 12 and 16 code points.</span></span>

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

### <span data-ttu-id="ac7be-165">-문자열</span><span class="sxs-lookup"><span data-stu-id="ac7be-165">-String</span></span>

<span data-ttu-id="ac7be-166">보안 문자열로 변환할 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-166">Specifies the string to convert to a secure string.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ac7be-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ac7be-167">CommonParameters</span></span>

<span data-ttu-id="ac7be-168">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ac7be-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ac7be-169">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ac7be-169">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ac7be-170">입력</span><span class="sxs-lookup"><span data-stu-id="ac7be-170">INPUTS</span></span>

### <span data-ttu-id="ac7be-171">System.String</span><span class="sxs-lookup"><span data-stu-id="ac7be-171">System.String</span></span>

<span data-ttu-id="ac7be-172">암호화 된 표준 문자열을로 파이프 할 수 있습니다 `ConvertTo-SecureString` .</span><span class="sxs-lookup"><span data-stu-id="ac7be-172">You can pipe a standard encrypted string to `ConvertTo-SecureString`.</span></span>

## <span data-ttu-id="ac7be-173">출력</span><span class="sxs-lookup"><span data-stu-id="ac7be-173">OUTPUTS</span></span>

### <span data-ttu-id="ac7be-174">System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="ac7be-174">System.Security.SecureString</span></span>

<span data-ttu-id="ac7be-175">`ConvertTo-SecureString`**SecureString** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-175">`ConvertTo-SecureString` returns a **SecureString** object.</span></span>

## <span data-ttu-id="ac7be-176">참고</span><span class="sxs-lookup"><span data-stu-id="ac7be-176">NOTES</span></span>

<span data-ttu-id="ac7be-177">이모티콘 등의 일부 문자는 해당 문자를 포함 하는 문자열의 여러 코드 요소에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7be-177">Some characters, such as emoticons, correspond to several code points in the string that contains them.</span></span> <span data-ttu-id="ac7be-178">암호에 사용 되는 경우 문제 및 오해를 일으킬 수 있으므로 이러한 문자를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="ac7be-178">Avoid using these characters because they may cause problems and misunderstandings when used in a password.</span></span>

## <span data-ttu-id="ac7be-179">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ac7be-179">RELATED LINKS</span></span>

[<span data-ttu-id="ac7be-180">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="ac7be-180">ConvertFrom-SecureString</span></span>](ConvertFrom-SecureString.md)

[<span data-ttu-id="ac7be-181">Read-Host</span><span class="sxs-lookup"><span data-stu-id="ac7be-181">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)
