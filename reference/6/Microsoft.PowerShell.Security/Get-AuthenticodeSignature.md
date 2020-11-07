---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-authenticodesignature?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-AuthenticodeSignature
ms.openlocfilehash: 351d666efad82d48d6d0390f98b472316602db1d
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343711"
---
# <span data-ttu-id="9e2fa-103">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="9e2fa-103">Get-AuthenticodeSignature</span></span>

## <span data-ttu-id="9e2fa-104">개요</span><span class="sxs-lookup"><span data-stu-id="9e2fa-104">SYNOPSIS</span></span>
<span data-ttu-id="9e2fa-105">파일의 Authenticode 서명에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-105">Gets information about the Authenticode signature for a file.</span></span>

## <span data-ttu-id="9e2fa-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9e2fa-106">SYNTAX</span></span>

### <span data-ttu-id="9e2fa-107">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="9e2fa-107">ByPath (Default)</span></span>

```
Get-AuthenticodeSignature [-FilePath] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="9e2fa-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="9e2fa-108">ByLiteralPath</span></span>

```
Get-AuthenticodeSignature -LiteralPath <String[]> [<CommonParameters>]
```

### <span data-ttu-id="9e2fa-109">ByContent</span><span class="sxs-lookup"><span data-stu-id="9e2fa-109">ByContent</span></span>

```
Get-AuthenticodeSignature -SourcePathOrExtension <String[]> -Content <Byte[]> [<CommonParameters>]
```

## <span data-ttu-id="9e2fa-110">설명</span><span class="sxs-lookup"><span data-stu-id="9e2fa-110">DESCRIPTION</span></span>

<span data-ttu-id="9e2fa-111">`Get-AuthenticodeSignature`Cmdlet은 파일 또는 파일 콘텐츠의 Authenticode 서명에 대 한 정보를 바이트 배열로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-111">The `Get-AuthenticodeSignature` cmdlet gets information about the Authenticode signature for a file or file content as a byte array.</span></span> <span data-ttu-id="9e2fa-112">파일이 서명되지 않은 경우 정보는 검색되지만 필드가 비어 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-112">If the file is not signed, the information is retrieved, but the fields are blank.</span></span>

## <span data-ttu-id="9e2fa-113">예제</span><span class="sxs-lookup"><span data-stu-id="9e2fa-113">EXAMPLES</span></span>

### <span data-ttu-id="9e2fa-114">예 1: 파일에 대 한 Authenticode 서명 가져오기</span><span class="sxs-lookup"><span data-stu-id="9e2fa-114">Example 1: Get the Authenticode signature for a file</span></span>

```powershell
Get-AuthenticodeSignature -FilePath "C:\Test\NewScript.ps1"
```

<span data-ttu-id="9e2fa-115">이 명령은 NewScript.ps1 파일에서 Authenticode 서명 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-115">This command gets information about the Authenticode signature in the NewScript.ps1 file.</span></span> <span data-ttu-id="9e2fa-116">**FilePath** 매개 변수를 사용 하 여 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-116">It uses the **FilePath** parameter to specify the file.</span></span>

### <span data-ttu-id="9e2fa-117">예 2: 여러 파일에 대 한 Authenticode 서명 가져오기</span><span class="sxs-lookup"><span data-stu-id="9e2fa-117">Example 2: Get the Authenticode signature for multiple files</span></span>

```powershell
Get-AuthenticodeSignature test.ps1, test1.ps1, sign-file.ps1, makexml.ps1
```

<span data-ttu-id="9e2fa-118">이 명령은 명령줄에 나열 된 4 개 파일의 Authenticode 서명에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-118">This command gets information about the Authenticode signature for the four files listed at the command line.</span></span> <span data-ttu-id="9e2fa-119">이 예제에서 옵션 인 **FilePath** 매개 변수의 이름은 생략 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-119">In this example, the name of the **FilePath** parameter, which is optional, is omitted.</span></span>

### <span data-ttu-id="9e2fa-120">예 3: 여러 파일에 대해 유효한 Authenticode 서명만 가져오기</span><span class="sxs-lookup"><span data-stu-id="9e2fa-120">Example 3: Get only valid Authenticode signatures for multiple files</span></span>

```powershell
Get-ChildItem $PSHOME\*.* | ForEach-object {Get-AuthenticodeSignature $_} | Where-Object {$_.status -eq "Valid"}
```

<span data-ttu-id="9e2fa-121">이 명령은 `$PSHOME` 디렉터리에서 유효한 Authenticode 서명이 있는 모든 파일을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-121">This command lists all of the files in the `$PSHOME` directory that have a valid Authenticode signature.</span></span> <span data-ttu-id="9e2fa-122">`$PSHOME`자동 변수는 PowerShell 설치 디렉터리에 대 한 경로를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-122">The `$PSHOME` automatic variable contains the path to the PowerShell installation directory.</span></span>

<span data-ttu-id="9e2fa-123">이 명령은 cmdlet을 사용 하 여 `Get-ChildItem` 디렉터리의 파일을 `$PSHOME` 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-123">The command uses the `Get-ChildItem` cmdlet to get the files in the `$PSHOME` directory.</span></span> <span data-ttu-id="9e2fa-124">패턴을 사용 *합니다.*</span><span class="sxs-lookup"><span data-stu-id="9e2fa-124">It uses a pattern of *.*</span></span> <span data-ttu-id="9e2fa-125">디렉터리를 제외 하려면 (파일 이름에 점이 없는 파일도 제외)</span><span class="sxs-lookup"><span data-stu-id="9e2fa-125">to exclude directories (although it also excludes files without a dot in the filename).</span></span>

<span data-ttu-id="9e2fa-126">이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 파일을 `$PSHOME` cmdlet으로 보냅니다 `ForEach-Object` `Get-AuthenticodeSignature` .이 cmdlet은 각 파일에 대해를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-126">The command uses a pipeline operator (`|`) to send the files in `$PSHOME` to the `ForEach-Object` cmdlet, where `Get-AuthenticodeSignature` is called for each file.</span></span>

<span data-ttu-id="9e2fa-127">명령의 결과는 `Get-AuthenticodeSignature` `Where-Object` 유효한 상태로 서명 개체만 선택 하는 명령으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-127">The results of the `Get-AuthenticodeSignature` command are sent to a `Where-Object` command that selects only the signature objects with a status of Valid.</span></span>

### <span data-ttu-id="9e2fa-128">예제 4: 바이트 배열로 지정 된 파일 콘텐츠에 대 한 Authenticode 서명 가져오기</span><span class="sxs-lookup"><span data-stu-id="9e2fa-128">Example 4: Get the Authenticode signature for a file content specified as byte array</span></span>

```powershell
Get-AuthenticodeSignature -Content (Get-Content foo.ps1 -AsByteStream) -SourcePathorExtension ps1
```

<span data-ttu-id="9e2fa-129">이 명령은 파일의 콘텐츠에 대 한 Authenticode 서명에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-129">This command gets information about the Authenticode signature for the content of a file.</span></span> <span data-ttu-id="9e2fa-130">이 예에서는 파일 확장명이 파일의 내용과 함께 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-130">In this example, the file extension is specified along with the content of the file.</span></span>

## <span data-ttu-id="9e2fa-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9e2fa-131">PARAMETERS</span></span>

### <span data-ttu-id="9e2fa-132">-콘텐츠</span><span class="sxs-lookup"><span data-stu-id="9e2fa-132">-Content</span></span>

<span data-ttu-id="9e2fa-133">Authenticode 서명이 검색 되는 바이트 배열인 파일의 콘텐츠입니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-133">Contents of a file as a byte array for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="9e2fa-134">이 매개 변수는 **SourcePathOrExtension** 매개 변수와 함께 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-134">This parameter must be used with **SourcePathOrExtension** parameter.</span></span> <span data-ttu-id="9e2fa-135">파일의 내용은 유니코드 (UTF-16LE) 형식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-135">The contents of the file must be in Unicode (UTF-16LE) format.</span></span>

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

### <span data-ttu-id="9e2fa-136">-FilePath</span><span class="sxs-lookup"><span data-stu-id="9e2fa-136">-FilePath</span></span>

<span data-ttu-id="9e2fa-137">검사할 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-137">Specifies the path to the file to examine.</span></span> <span data-ttu-id="9e2fa-138">와일드카드를 사용할 수 있지만 단일 파일로 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-138">Wildcards are permitted, but they must lead to a single file.</span></span> <span data-ttu-id="9e2fa-139">이 매개 변수의 값을 지정 하는 경우 명령줄에서 **FilePath** 를 입력할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-139">It is not necessary to type **FilePath** at the command line when you specify a value for this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="9e2fa-140">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9e2fa-140">-LiteralPath</span></span>

<span data-ttu-id="9e2fa-141">검사할 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-141">Specifies the path to the file being examined.</span></span> <span data-ttu-id="9e2fa-142">**FilePath** 와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-142">Unlike **FilePath** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="9e2fa-143">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-143">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="9e2fa-144">경로에 이스케이프 문자가 포함 되어 있으면 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-144">If the path includes an escape character, enclose it in single quotation marks.</span></span> <span data-ttu-id="9e2fa-145">작은따옴표는 모든 문자를 이스케이프 문자로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-145">Single quotation marks tell PowerShell not to interpret any characters as escape characters.</span></span>

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

### <span data-ttu-id="9e2fa-146">-SourcePathOrExtension</span><span class="sxs-lookup"><span data-stu-id="9e2fa-146">-SourcePathOrExtension</span></span>

<span data-ttu-id="9e2fa-147">Authenticode 서명이 검색 되는 콘텐츠의 파일 또는 파일 형식에 대 한 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-147">Path to the file or file type of the content for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="9e2fa-148">이 매개 변수는 파일 콘텐츠가 바이트 배열로 전달 되는 **콘텐츠와** 함께 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-148">This parameter is used with **Content** where file content is passed as a byte array.</span></span>

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

### <span data-ttu-id="9e2fa-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9e2fa-149">CommonParameters</span></span>

<span data-ttu-id="9e2fa-150">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9e2fa-151">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-151">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="9e2fa-152">입력</span><span class="sxs-lookup"><span data-stu-id="9e2fa-152">INPUTS</span></span>

### <span data-ttu-id="9e2fa-153">System.String</span><span class="sxs-lookup"><span data-stu-id="9e2fa-153">System.String</span></span>

<span data-ttu-id="9e2fa-154">파일 경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Get-AuthenticodeSignature` .</span><span class="sxs-lookup"><span data-stu-id="9e2fa-154">You can pipe a string that contains a file path to `Get-AuthenticodeSignature`.</span></span>

## <span data-ttu-id="9e2fa-155">출력</span><span class="sxs-lookup"><span data-stu-id="9e2fa-155">OUTPUTS</span></span>

### <span data-ttu-id="9e2fa-156">System.object..</span><span class="sxs-lookup"><span data-stu-id="9e2fa-156">System.Management.Automation.Signature</span></span>

<span data-ttu-id="9e2fa-157">`Get-AuthenticodeSignature` 가져오는 각 시그니처에 대 한 서명 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-157">`Get-AuthenticodeSignature` returns a signature object for each signature that it gets.</span></span>

## <span data-ttu-id="9e2fa-158">참고</span><span class="sxs-lookup"><span data-stu-id="9e2fa-158">NOTES</span></span>

<span data-ttu-id="9e2fa-159">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-159">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="9e2fa-160">PowerShell의 Authenticode 서명에 대 한 자세한 내용은 [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e2fa-160">For information about Authenticode signatures in PowerShell, see [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md).</span></span>

## <span data-ttu-id="9e2fa-161">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9e2fa-161">RELATED LINKS</span></span>

[<span data-ttu-id="9e2fa-162">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="9e2fa-162">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="9e2fa-163">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="9e2fa-163">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="9e2fa-164">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="9e2fa-164">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

[<span data-ttu-id="9e2fa-165">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="9e2fa-165">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="9e2fa-166">about_Signing</span><span class="sxs-lookup"><span data-stu-id="9e2fa-166">about_Signing</span></span>](../Microsoft.PowerShell.Core/About/about_Signing.md)
