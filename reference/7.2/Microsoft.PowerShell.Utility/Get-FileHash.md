---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FileHash
ms.openlocfilehash: 0b31409d1da56979887e606b76ddf20532b188c1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601451"
---
# <span data-ttu-id="de6c7-102">Get-FileHash</span><span class="sxs-lookup"><span data-stu-id="de6c7-102">Get-FileHash</span></span>

## <span data-ttu-id="de6c7-103">개요</span><span class="sxs-lookup"><span data-stu-id="de6c7-103">SYNOPSIS</span></span>
<span data-ttu-id="de6c7-104">지정한 해시 알고리즘을 사용하여 파일에 대한 해시 값을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-104">Computes the hash value for a file by using a specified hash algorithm.</span></span>

## <span data-ttu-id="de6c7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="de6c7-105">SYNTAX</span></span>

### <span data-ttu-id="de6c7-106">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="de6c7-106">Path (Default)</span></span>

```
Get-FileHash [-Path] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### <span data-ttu-id="de6c7-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="de6c7-107">LiteralPath</span></span>

```
Get-FileHash [-LiteralPath] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### <span data-ttu-id="de6c7-108">StreamParameterSet</span><span class="sxs-lookup"><span data-stu-id="de6c7-108">StreamParameterSet</span></span>

```
Get-FileHash [-InputStream] <Stream> [[-Algorithm] <String>] [<CommonParameters>]
```

## <span data-ttu-id="de6c7-109">설명</span><span class="sxs-lookup"><span data-stu-id="de6c7-109">DESCRIPTION</span></span>

<span data-ttu-id="de6c7-110">`Get-FileHash`Cmdlet은 지정 된 해시 알고리즘을 사용 하 여 파일에 대 한 해시 값을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-110">The `Get-FileHash` cmdlet computes the hash value for a file by using a specified hash algorithm.</span></span>
<span data-ttu-id="de6c7-111">해시 값은 파일 내용에 해당하는 고유한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-111">A hash value is a unique value that corresponds to the content of the file.</span></span> <span data-ttu-id="de6c7-112">파일 이름, 확장명 또는 기타 지정으로 파일 내용을 식별하는 대신 해시는 파일 내용에 고유한 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-112">Rather than identifying the contents of a file by its file name, extension, or other designation, a hash assigns a unique value to the contents of a file.</span></span> <span data-ttu-id="de6c7-113">파일 내용과 해시 값을 변경하지 않고 파일 이름과 확장명을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-113">File names and extensions can be changed without altering the content of the file, and without changing the hash value.</span></span> <span data-ttu-id="de6c7-114">마찬가지로 이름 또는 확장명을 변경 하지 않고 파일의 콘텐츠를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-114">Similarly, the file's content can be changed without changing the name or extension.</span></span> <span data-ttu-id="de6c7-115">그러나 파일 내용에서 한 문자라도 변경하면 파일의 해시 값이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-115">However, changing even a single character in the contents of a file changes the hash value of the file.</span></span>

<span data-ttu-id="de6c7-116">해시 값은 파일 내용이 변경되지 않았음을 확인하는 암호화된 보안 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-116">The purpose of hash values is to provide a cryptographically-secure way to verify that the contents of a file have not been changed.</span></span> <span data-ttu-id="de6c7-117">MD5 및 SHA1을 비롯 한 일부 해시 알고리즘은 더 이상 공격 으로부터 안전 하 게 고려 되지 않지만, 보안 해시 알고리즘의 목표는 실수로 또는 악의적 또는 무단 시도로 파일의 콘텐츠를 변경할 수 없도록 렌더링 하 고 동일한 해시 값을 유지 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-117">While some hash algorithms, including MD5 and SHA1, are no longer considered secure against attack, the goal of a secure hash algorithm is to render it impossible to change the contents of a file -- either by accident, or by malicious or unauthorized attempt -- and maintain the same hash value.</span></span> <span data-ttu-id="de6c7-118">해시 값을 사용하여 두 개의 파일 내용이 같은지 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-118">You can also use hash values to determine if two different files have exactly the same content.</span></span> <span data-ttu-id="de6c7-119">두 파일의 해시 값이 같으면 파일 내용도 같습니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-119">If the hash values of two files are identical, the contents of the files are also identical.</span></span>

<span data-ttu-id="de6c7-120">기본적으로 cmdlet은 `Get-FileHash` SHA256 알고리즘을 사용 하지만 대상 운영 체제에서 지 원하는 모든 해시 알고리즘을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-120">By default, the `Get-FileHash` cmdlet uses the SHA256 algorithm, although any hash algorithm that is supported by the target operating system can be used.</span></span>

## <span data-ttu-id="de6c7-121">예제</span><span class="sxs-lookup"><span data-stu-id="de6c7-121">EXAMPLES</span></span>

### <span data-ttu-id="de6c7-122">예제 1: 파일에 대 한 해시 값 계산</span><span class="sxs-lookup"><span data-stu-id="de6c7-122">Example 1: Compute the hash value for a file</span></span>

<span data-ttu-id="de6c7-123">이 예에서는 cmdlet을 사용 하 여 `Get-FileHash` 파일에 대 한 해시 값을 계산 합니다 `/etc/apt/sources.list` .</span><span class="sxs-lookup"><span data-stu-id="de6c7-123">This example uses the `Get-FileHash` cmdlet to compute the hash value for the `/etc/apt/sources.list` file.</span></span> <span data-ttu-id="de6c7-124">사용 된 해시 알고리즘은 기본값인 **SHA256** 입니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-124">The hash algorithm used is the default, **SHA256**.</span></span> <span data-ttu-id="de6c7-125">출력을 cmdlet으로 파이프 하 여 `Format-List` 출력을 목록 형식으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-125">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash /etc/apt/sources.list | Format-List
```

```Output
Algorithm : SHA256
Hash      : 3CBCFDDEC145E3382D592266BE193E5BE53443138EE6AB6CA09FF20DF609E268
Path      : /etc/apt/sources.list
```

### <span data-ttu-id="de6c7-126">예제 2: ISO 파일에 대 한 해시 값 계산</span><span class="sxs-lookup"><span data-stu-id="de6c7-126">Example 2: Compute the hash value for an ISO file</span></span>

<span data-ttu-id="de6c7-127">이 예제에서는 `Get-FileHash` cmdlet 및 **SHA384** 알고리즘을 사용 하 여 관리자가 인터넷에서 다운로드 한 ISO 파일의 해시 값을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-127">This example uses the `Get-FileHash` cmdlet and the **SHA384** algorithm to compute the hash value for an ISO file that an administrator has downloaded from the internet.</span></span> <span data-ttu-id="de6c7-128">출력을 cmdlet으로 파이프 하 여 `Format-List` 출력을 목록 형식으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-128">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash C:\Users\user1\Downloads\Contoso8_1_ENT.iso -Algorithm SHA384 | Format-List
```

```Output
Algorithm : SHA384
Hash      : 20AB1C2EE19FC96A7C66E33917D191A24E3CE9DAC99DB7C786ACCE31E559144FEAFC695C58E508E2EBBC9D3C96F21FA3
Path      : C:\Users\user1\Downloads\Contoso8_1_ENT.iso
```

### <span data-ttu-id="de6c7-129">예제 3: 스트림의 해시 값 계산</span><span class="sxs-lookup"><span data-stu-id="de6c7-129">Example 3: Compute the hash value of a stream</span></span>

<span data-ttu-id="de6c7-130">이 예에서는 [Powershell 릴리스 페이지](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4)에서 패키지를 다운로드 하는 데 **시스템 .net. WebClient** 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-130">For this example, we get are using **System.Net.WebClient** to download a package from the [Powershell release page](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4).</span></span> <span data-ttu-id="de6c7-131">또한 릴리스 페이지는 각 패키지 파일의 SHA256 해시를 문서화 합니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-131">The release page also documents the SHA256 hash of each package file.</span></span> <span data-ttu-id="de6c7-132">게시 된 해시 값을 계산 하는 해시 값과 비교할 수 있습니다 `Get-FileHash` .</span><span class="sxs-lookup"><span data-stu-id="de6c7-132">We can compare the published hash value with the one we calculate with `Get-FileHash`.</span></span>

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

### <span data-ttu-id="de6c7-133">예제 4: 문자열의 해시 계산</span><span class="sxs-lookup"><span data-stu-id="de6c7-133">Example 4: Compute the hash of a string</span></span>

<span data-ttu-id="de6c7-134">PowerShell은 문자열의 해시를 계산 하는 cmdlet을 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-134">PowerShell does not provide a cmdlet to compute the hash of a string.</span></span> <span data-ttu-id="de6c7-135">그러나 문자열을 스트림에 쓰고의 **InputStream** 매개 변수를 사용 `Get-FileHash` 하 여 해시 값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-135">However, you can write a string to a stream and use the **InputStream** parameter of `Get-FileHash` to get the hash value.</span></span>

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

## <span data-ttu-id="de6c7-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="de6c7-136">PARAMETERS</span></span>

### <span data-ttu-id="de6c7-137">-알고리즘</span><span class="sxs-lookup"><span data-stu-id="de6c7-137">-Algorithm</span></span>

<span data-ttu-id="de6c7-138">지정 된 파일 또는 스트림의 내용에 대 한 해시 값을 계산 하는 데 사용할 암호화 해시 함수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-138">Specifies the cryptographic hash function to use for computing the hash value of the contents of the specified file or stream.</span></span> <span data-ttu-id="de6c7-139">암호화 해시 함수에는 동일한 해시 값을 가진 두 개의 다른 파일을 찾을 수 없는 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-139">A cryptographic hash function has the property that it is infeasible to find two different files with the same hash value.</span></span> <span data-ttu-id="de6c7-140">해시 함수는 디지털 서명과 함께 데이터 무결성에 주로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-140">Hash functions are commonly used with digital signatures and for data integrity.</span></span> <span data-ttu-id="de6c7-141">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-141">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="de6c7-142">SHA1</span><span class="sxs-lookup"><span data-stu-id="de6c7-142">SHA1</span></span>
- <span data-ttu-id="de6c7-143">SHA256</span><span class="sxs-lookup"><span data-stu-id="de6c7-143">SHA256</span></span>
- <span data-ttu-id="de6c7-144">SHA384</span><span class="sxs-lookup"><span data-stu-id="de6c7-144">SHA384</span></span>
- <span data-ttu-id="de6c7-145">SHA512</span><span class="sxs-lookup"><span data-stu-id="de6c7-145">SHA512</span></span>
- <span data-ttu-id="de6c7-146">MD5</span><span class="sxs-lookup"><span data-stu-id="de6c7-146">MD5</span></span>

<span data-ttu-id="de6c7-147">값을 지정하지 않거나 매개 변수를 생략할 경우 기본값은 SHA256입니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-147">If no value is specified, or if the parameter is omitted, the default value is SHA256.</span></span>

<span data-ttu-id="de6c7-148">보안상, 더 이상 안전하지 않은 MD5 및 SHA1은 간단한 변경 유효성 검사에만 사용해야 하며 공격이나 조작으로부터 보호해야 하는 파일의 해시 값을 생성하는 데 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-148">For security reasons, MD5 and SHA1, which are no longer considered secure, should only be used for simple change validation, and should not be used to generate hash values for files that require protection from attack or tampering.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: SHA1, SHA256, SHA384, SHA512, MD5

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="de6c7-149">-InputStream</span><span class="sxs-lookup"><span data-stu-id="de6c7-149">-InputStream</span></span>

<span data-ttu-id="de6c7-150">입력 스트림을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-150">Specifies the input stream.</span></span>

```yaml
Type: System.IO.Stream
Parameter Sets: StreamParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="de6c7-151">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="de6c7-151">-LiteralPath</span></span>

<span data-ttu-id="de6c7-152">파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-152">Specifies the path to a file.</span></span> <span data-ttu-id="de6c7-153">**Path** 매개 변수와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-153">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="de6c7-154">어떠한 문자도 와일드카드 문자로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-154">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="de6c7-155">경로에 이스케이프 문자가 포함되어 있으면 경로를 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-155">If the path includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="de6c7-156">작은따옴표는 PowerShell에서 문자를 이스케이프 시퀀스로 해석 하지 않도록 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-156">Single quotation marks instruct PowerShell not to interpret characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="de6c7-157">-Path</span><span class="sxs-lookup"><span data-stu-id="de6c7-157">-Path</span></span>

<span data-ttu-id="de6c7-158">하나 이상의 파일에 대 한 경로를 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-158">Specifies the path to one or more files as an array.</span></span> <span data-ttu-id="de6c7-159">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-159">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="de6c7-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="de6c7-160">CommonParameters</span></span>

<span data-ttu-id="de6c7-161">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="de6c7-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="de6c7-162">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="de6c7-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="de6c7-163">입력</span><span class="sxs-lookup"><span data-stu-id="de6c7-163">INPUTS</span></span>

### <span data-ttu-id="de6c7-164">System.String</span><span class="sxs-lookup"><span data-stu-id="de6c7-164">System.String</span></span>

<span data-ttu-id="de6c7-165">`Get-FileHash`하나 이상의 파일에 대 한 경로를 포함 하는 cmdlet에 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-165">You can pipe a string to the `Get-FileHash` cmdlet that contains a path to one or more files.</span></span>

## <span data-ttu-id="de6c7-166">출력</span><span class="sxs-lookup"><span data-stu-id="de6c7-166">OUTPUTS</span></span>

### <span data-ttu-id="de6c7-167">Microsoft. Powershell. FileHash</span><span class="sxs-lookup"><span data-stu-id="de6c7-167">Microsoft.Powershell.Utility.FileHash</span></span>

<span data-ttu-id="de6c7-168">`Get-FileHash` 지정 된 파일에 대 한 경로, 계산 된 해시의 값 및 해시를 계산 하는 데 사용 되는 알고리즘을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="de6c7-168">`Get-FileHash` returns an object that represents the path to the specified file, the value of the computed hash, and the algorithm used to compute the hash.</span></span>

## <span data-ttu-id="de6c7-169">참고</span><span class="sxs-lookup"><span data-stu-id="de6c7-169">NOTES</span></span>

## <span data-ttu-id="de6c7-170">관련 링크</span><span class="sxs-lookup"><span data-stu-id="de6c7-170">RELATED LINKS</span></span>

[<span data-ttu-id="de6c7-171">Format-List</span><span class="sxs-lookup"><span data-stu-id="de6c7-171">Format-List</span></span>](Format-List.md)

