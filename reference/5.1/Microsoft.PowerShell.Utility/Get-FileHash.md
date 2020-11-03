---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FileHash
ms.openlocfilehash: ce0ecdfc216680f255718b1a03f78276364b1c50
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213985"
---
# <span data-ttu-id="dfb84-103">Get-FileHash</span><span class="sxs-lookup"><span data-stu-id="dfb84-103">Get-FileHash</span></span>

## <span data-ttu-id="dfb84-104">개요</span><span class="sxs-lookup"><span data-stu-id="dfb84-104">SYNOPSIS</span></span>
<span data-ttu-id="dfb84-105">지정한 해시 알고리즘을 사용하여 파일에 대한 해시 값을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-105">Computes the hash value for a file by using a specified hash algorithm.</span></span>

## <span data-ttu-id="dfb84-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dfb84-106">SYNTAX</span></span>

### <span data-ttu-id="dfb84-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="dfb84-107">Path (Default)</span></span>

```
Get-FileHash [-Path] <String[]> [-Algorithm <String>] [<CommonParameters>]
```

### <span data-ttu-id="dfb84-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="dfb84-108">LiteralPath</span></span>

```
Get-FileHash -LiteralPath <String[]> [-Algorithm <String>] [<CommonParameters>]
```

### <span data-ttu-id="dfb84-109">STREAM</span><span class="sxs-lookup"><span data-stu-id="dfb84-109">Stream</span></span>

```
Get-FileHash -InputStream <Stream> [-Algorithm <String>] [<CommonParameters>]
```

## <span data-ttu-id="dfb84-110">설명</span><span class="sxs-lookup"><span data-stu-id="dfb84-110">DESCRIPTION</span></span>

<span data-ttu-id="dfb84-111">`Get-FileHash`Cmdlet은 지정 된 해시 알고리즘을 사용 하 여 파일에 대 한 해시 값을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-111">The `Get-FileHash` cmdlet computes the hash value for a file by using a specified hash algorithm.</span></span>
<span data-ttu-id="dfb84-112">해시 값은 파일 내용에 해당하는 고유한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-112">A hash value is a unique value that corresponds to the content of the file.</span></span> <span data-ttu-id="dfb84-113">파일 이름, 확장명 또는 기타 지정으로 파일 내용을 식별하는 대신 해시는 파일 내용에 고유한 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-113">Rather than identifying the contents of a file by its file name, extension, or other designation, a hash assigns a unique value to the contents of a file.</span></span> <span data-ttu-id="dfb84-114">파일 내용과 해시 값을 변경하지 않고 파일 이름과 확장명을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-114">File names and extensions can be changed without altering the content of the file, and without changing the hash value.</span></span> <span data-ttu-id="dfb84-115">마찬가지로 이름 또는 확장명을 변경 하지 않고 파일의 콘텐츠를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-115">Similarly, the file's content can be changed without changing the name or extension.</span></span> <span data-ttu-id="dfb84-116">그러나 파일 내용에서 한 문자라도 변경하면 파일의 해시 값이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-116">However, changing even a single character in the contents of a file changes the hash value of the file.</span></span>

<span data-ttu-id="dfb84-117">해시 값은 파일 내용이 변경되지 않았음을 확인하는 암호화된 보안 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-117">The purpose of hash values is to provide a cryptographically-secure way to verify that the contents of a file have not been changed.</span></span> <span data-ttu-id="dfb84-118">MD5 및 SHA1을 비롯 한 일부 해시 알고리즘은 더 이상 공격 으로부터 안전 하 게 고려 되지 않지만, 보안 해시 알고리즘의 목표는 실수로 또는 악의적 또는 무단 시도로 파일의 콘텐츠를 변경할 수 없도록 렌더링 하 고 동일한 해시 값을 유지 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-118">While some hash algorithms, including MD5 and SHA1, are no longer considered secure against attack, the goal of a secure hash algorithm is to render it impossible to change the contents of a file -- either by accident, or by malicious or unauthorized attempt -- and maintain the same hash value.</span></span> <span data-ttu-id="dfb84-119">해시 값을 사용하여 두 개의 파일 내용이 같은지 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-119">You can also use hash values to determine if two different files have exactly the same content.</span></span> <span data-ttu-id="dfb84-120">두 파일의 해시 값이 같으면 파일 내용도 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-120">If the hash values of two files are identical, the contents of the files are also identical.</span></span>

<span data-ttu-id="dfb84-121">기본적으로 cmdlet은 `Get-FileHash` SHA256 알고리즘을 사용 하지만 대상 운영 체제에서 지 원하는 모든 해시 알고리즘을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-121">By default, the `Get-FileHash` cmdlet uses the SHA256 algorithm, although any hash algorithm that is supported by the target operating system can be used.</span></span>

## <span data-ttu-id="dfb84-122">예제</span><span class="sxs-lookup"><span data-stu-id="dfb84-122">EXAMPLES</span></span>

### <span data-ttu-id="dfb84-123">예제 1: 파일에 대 한 해시 값 계산</span><span class="sxs-lookup"><span data-stu-id="dfb84-123">Example 1: Compute the hash value for a file</span></span>

<span data-ttu-id="dfb84-124">이 예에서는 cmdlet을 사용 하 여 `Get-FileHash` 파일에 대 한 해시 값을 계산 합니다 `Powershell.exe` .</span><span class="sxs-lookup"><span data-stu-id="dfb84-124">This example uses the `Get-FileHash` cmdlet to compute the hash value for the `Powershell.exe` file.</span></span>
<span data-ttu-id="dfb84-125">사용된 해시 알고리즘은 기본값인 SHA256입니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-125">The hash algorithm used is the default, SHA256.</span></span> <span data-ttu-id="dfb84-126">출력을 cmdlet으로 파이프 하 여 `Format-List` 출력을 목록 형식으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-126">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash $PSHOME\powershell.exe | Format-List
```

```Output
Algorithm : SHA256
Hash      : 908B64B1971A979C7E3E8CE4621945CBA84854CB98D76367B791A6E22B5F6D53
Path      : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
```

### <span data-ttu-id="dfb84-127">예제 2: ISO 파일에 대 한 해시 값 계산</span><span class="sxs-lookup"><span data-stu-id="dfb84-127">Example 2: Compute the hash value for an ISO file</span></span>

<span data-ttu-id="dfb84-128">이 예제에서는 `Get-FileHash` cmdlet 및 **SHA384** 알고리즘을 사용 하 여 관리자가 인터넷에서 다운로드 한 ISO 파일의 해시 값을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-128">This example uses the `Get-FileHash` cmdlet and the **SHA384** algorithm to compute the hash value for an ISO file that an administrator has downloaded from the internet.</span></span> <span data-ttu-id="dfb84-129">출력을 cmdlet으로 파이프 하 여 `Format-List` 출력을 목록 형식으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-129">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash C:\Users\user1\Downloads\Contoso8_1_ENT.iso -Algorithm SHA384 | Format-List
```

```Output
Algorithm : SHA384
Hash      : 20AB1C2EE19FC96A7C66E33917D191A24E3CE9DAC99DB7C786ACCE31E559144FEAFC695C58E508E2EBBC9D3C96F21FA3
Path      : C:\Users\user1\Downloads\Contoso8_1_ENT.iso
```

### <span data-ttu-id="dfb84-130">예제 3: 스트림의 해시 값 계산</span><span class="sxs-lookup"><span data-stu-id="dfb84-130">Example 3: Compute the hash value of a stream</span></span>

<span data-ttu-id="dfb84-131">이 예에서는 [Powershell 릴리스 페이지](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4)에서 패키지를 다운로드 하는 데 **시스템 .net. WebClient** 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-131">For this example, we get are using **System.Net.WebClient** to download a package from the [Powershell release page](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4).</span></span> <span data-ttu-id="dfb84-132">또한 릴리스 페이지는 각 패키지 파일의 SHA256 해시를 문서화 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-132">The release page also documents the SHA256 hash of each package file.</span></span> <span data-ttu-id="dfb84-133">게시 된 해시 값을 계산 하는 해시 값과 비교할 수 있습니다 `Get-FileHash` .</span><span class="sxs-lookup"><span data-stu-id="dfb84-133">We can compare the published hash value with the one we calculate with `Get-FileHash`.</span></span>

```powershell
$wc = [System.Net.WebClient]::new()
$pkgurl = 'https://github.com/PowerShell/PowerShell/releases/download/v6.2.4/powershell_6.2.4-1.debian.9_amd64.deb'
$publishedHash = '8E28E54D601F0751922DE24632C1E716B4684876255CF82304A9B19E89A9CCAC'
$FileHash = Get-FileHash -InputStream ($wc.OpenRead($pkgurl))
$FileHash.Hash -eq $publishedHash
```

```Output
True
```

### <span data-ttu-id="dfb84-134">예제 4: 문자열의 해시 계산</span><span class="sxs-lookup"><span data-stu-id="dfb84-134">Example 4: Compute the hash of a string</span></span>

<span data-ttu-id="dfb84-135">PowerShell은 문자열의 해시를 계산 하는 cmdlet을 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-135">PowerShell does not provide a cmdlet to compute the hash of a string.</span></span> <span data-ttu-id="dfb84-136">그러나 문자열을 스트림에 쓰고의 **InputStream** 매개 변수를 사용 `Get-FileHash` 하 여 해시 값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-136">However, you can write a string to a stream and use the **InputStream** parameter of `Get-FileHash` to get the hash value.</span></span>

```powershell
$stringAsStream = [System.IO.MemoryStream]::new()
$writer = [System.IO.StreamWriter]::new($stringAsStream)
$writer.write("Hello world")
$writer.Flush()
$stringAsStream.Position = 0
Get-FileHash -InputStream $stringAsStream | Select-Object Hash
```

```Output
Hash
----
64EC88CA00B268E5BA1A35678A1B5316D212F4F366B2477232534A8AECA37F3C
```

## <span data-ttu-id="dfb84-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dfb84-137">PARAMETERS</span></span>

### <span data-ttu-id="dfb84-138">-알고리즘</span><span class="sxs-lookup"><span data-stu-id="dfb84-138">-Algorithm</span></span>

<span data-ttu-id="dfb84-139">지정 된 파일 또는 스트림의 내용에 대 한 해시 값을 계산 하는 데 사용할 암호화 해시 함수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-139">Specifies the cryptographic hash function to use for computing the hash value of the contents of the specified file or stream.</span></span> <span data-ttu-id="dfb84-140">암호화 해시 함수에는 동일한 해시 값을 가진 두 개의 다른 파일을 찾을 수 없는 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-140">A cryptographic hash function has the property that it is infeasible to find two different files with the same hash value.</span></span> <span data-ttu-id="dfb84-141">해시 함수는 디지털 서명과 함께 데이터 무결성에 주로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-141">Hash functions are commonly used with digital signatures and for data integrity.</span></span> <span data-ttu-id="dfb84-142">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-142">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="dfb84-143">SHA1</span><span class="sxs-lookup"><span data-stu-id="dfb84-143">SHA1</span></span>
- <span data-ttu-id="dfb84-144">SHA256</span><span class="sxs-lookup"><span data-stu-id="dfb84-144">SHA256</span></span>
- <span data-ttu-id="dfb84-145">SHA384</span><span class="sxs-lookup"><span data-stu-id="dfb84-145">SHA384</span></span>
- <span data-ttu-id="dfb84-146">SHA512</span><span class="sxs-lookup"><span data-stu-id="dfb84-146">SHA512</span></span>
- <span data-ttu-id="dfb84-147">MACTripleDES</span><span class="sxs-lookup"><span data-stu-id="dfb84-147">MACTripleDES</span></span>
- <span data-ttu-id="dfb84-148">MD5</span><span class="sxs-lookup"><span data-stu-id="dfb84-148">MD5</span></span>
- <span data-ttu-id="dfb84-149">RIPEMD160</span><span class="sxs-lookup"><span data-stu-id="dfb84-149">RIPEMD160</span></span>

<span data-ttu-id="dfb84-150">값을 지정하지 않거나 매개 변수를 생략할 경우 기본값은 SHA256입니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-150">If no value is specified, or if the parameter is omitted, the default value is SHA256.</span></span>

<span data-ttu-id="dfb84-151">보안상, 더 이상 안전하지 않은 MD5 및 SHA1은 간단한 변경 유효성 검사에만 사용해야 하며 공격이나 조작으로부터 보호해야 하는 파일의 해시 값을 생성하는 데 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-151">For security reasons, MD5 and SHA1, which are no longer considered secure, should only be used for simple change validation, and should not be used to generate hash values for files that require protection from attack or tampering.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: SHA1, SHA256, SHA384, SHA512, MACTripleDES, MD5, RIPEMD160

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dfb84-152">-InputStream</span><span class="sxs-lookup"><span data-stu-id="dfb84-152">-InputStream</span></span>

<span data-ttu-id="dfb84-153">입력 스트림을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-153">Specifies the input stream.</span></span>

```yaml
Type: System.IO.Stream
Parameter Sets: Stream
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dfb84-154">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="dfb84-154">-LiteralPath</span></span>

<span data-ttu-id="dfb84-155">파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-155">Specifies the path to a file.</span></span> <span data-ttu-id="dfb84-156">**Path** 매개 변수와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-156">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="dfb84-157">어떠한 문자도 와일드카드 문자로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-157">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="dfb84-158">경로에 이스케이프 문자가 포함되어 있으면 경로를 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-158">If the path includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="dfb84-159">작은따옴표는 PowerShell에서 문자를 이스케이프 시퀀스로 해석 하지 않도록 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-159">Single quotation marks instruct PowerShell not to interpret characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="dfb84-160">-Path</span><span class="sxs-lookup"><span data-stu-id="dfb84-160">-Path</span></span>

<span data-ttu-id="dfb84-161">하나 이상의 파일에 대 한 경로를 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-161">Specifies the path to one or more files as an array.</span></span> <span data-ttu-id="dfb84-162">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-162">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="dfb84-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dfb84-163">CommonParameters</span></span>

<span data-ttu-id="dfb84-164">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dfb84-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dfb84-165">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dfb84-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dfb84-166">입력</span><span class="sxs-lookup"><span data-stu-id="dfb84-166">INPUTS</span></span>

### <span data-ttu-id="dfb84-167">System.String</span><span class="sxs-lookup"><span data-stu-id="dfb84-167">System.String</span></span>

<span data-ttu-id="dfb84-168">`Get-FileHash`하나 이상의 파일에 대 한 경로를 포함 하는 cmdlet에 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-168">You can pipe a string to the `Get-FileHash` cmdlet that contains a path to one or more files.</span></span>

## <span data-ttu-id="dfb84-169">출력</span><span class="sxs-lookup"><span data-stu-id="dfb84-169">OUTPUTS</span></span>

### <span data-ttu-id="dfb84-170">Microsoft. Powershell. FileHash</span><span class="sxs-lookup"><span data-stu-id="dfb84-170">Microsoft.Powershell.Utility.FileHash</span></span>

<span data-ttu-id="dfb84-171">`Get-FileHash` 지정 된 파일에 대 한 경로, 계산 된 해시의 값 및 해시를 계산 하는 데 사용 되는 알고리즘을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb84-171">`Get-FileHash` returns an object that represents the path to the specified file, the value of the computed hash, and the algorithm used to compute the hash.</span></span>

## <span data-ttu-id="dfb84-172">참고</span><span class="sxs-lookup"><span data-stu-id="dfb84-172">NOTES</span></span>

## <span data-ttu-id="dfb84-173">관련 링크</span><span class="sxs-lookup"><span data-stu-id="dfb84-173">RELATED LINKS</span></span>

[<span data-ttu-id="dfb84-174">Format-List</span><span class="sxs-lookup"><span data-stu-id="dfb84-174">Format-List</span></span>](Format-List.md)
