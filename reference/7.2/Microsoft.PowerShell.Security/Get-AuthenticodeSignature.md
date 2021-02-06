---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-authenticodesignature?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-AuthenticodeSignature
ms.openlocfilehash: 16c61b1fd442eb68c458c3b524a8fc55d5eedcb6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600457"
---
# <span data-ttu-id="30f57-102">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="30f57-102">Get-AuthenticodeSignature</span></span>

## <span data-ttu-id="30f57-103">개요</span><span class="sxs-lookup"><span data-stu-id="30f57-103">SYNOPSIS</span></span>
<span data-ttu-id="30f57-104">파일의 Authenticode 서명에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-104">Gets information about the Authenticode signature for a file.</span></span>

## <span data-ttu-id="30f57-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="30f57-105">SYNTAX</span></span>

### <span data-ttu-id="30f57-106">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="30f57-106">ByPath (Default)</span></span>

```
Get-AuthenticodeSignature [-FilePath] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="30f57-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="30f57-107">ByLiteralPath</span></span>

```
Get-AuthenticodeSignature -LiteralPath <String[]> [<CommonParameters>]
```

### <span data-ttu-id="30f57-108">ByContent</span><span class="sxs-lookup"><span data-stu-id="30f57-108">ByContent</span></span>

```
Get-AuthenticodeSignature -SourcePathOrExtension <String[]> -Content <Byte[]> [<CommonParameters>]
```

## <span data-ttu-id="30f57-109">설명</span><span class="sxs-lookup"><span data-stu-id="30f57-109">DESCRIPTION</span></span>

<span data-ttu-id="30f57-110">`Get-AuthenticodeSignature`Cmdlet은 파일 또는 파일 콘텐츠의 Authenticode 서명에 대 한 정보를 바이트 배열로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-110">The `Get-AuthenticodeSignature` cmdlet gets information about the Authenticode signature for a file or file content as a byte array.</span></span> <span data-ttu-id="30f57-111">파일이 서명되지 않은 경우 정보는 검색되지만 필드가 비어 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-111">If the file is not signed, the information is retrieved, but the fields are blank.</span></span>

## <span data-ttu-id="30f57-112">예제</span><span class="sxs-lookup"><span data-stu-id="30f57-112">EXAMPLES</span></span>

### <span data-ttu-id="30f57-113">예 1: 파일에 대 한 Authenticode 서명 가져오기</span><span class="sxs-lookup"><span data-stu-id="30f57-113">Example 1: Get the Authenticode signature for a file</span></span>

```powershell
Get-AuthenticodeSignature -FilePath "C:\Test\NewScript.ps1"
```

<span data-ttu-id="30f57-114">이 명령은 NewScript.ps1 파일에서 Authenticode 서명 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-114">This command gets information about the Authenticode signature in the NewScript.ps1 file.</span></span> <span data-ttu-id="30f57-115">**FilePath** 매개 변수를 사용 하 여 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-115">It uses the **FilePath** parameter to specify the file.</span></span>

### <span data-ttu-id="30f57-116">예 2: 여러 파일에 대 한 Authenticode 서명 가져오기</span><span class="sxs-lookup"><span data-stu-id="30f57-116">Example 2: Get the Authenticode signature for multiple files</span></span>

```powershell
Get-AuthenticodeSignature test.ps1, test1.ps1, sign-file.ps1, makexml.ps1
```

<span data-ttu-id="30f57-117">이 명령은 명령줄에 나열 된 4 개 파일의 Authenticode 서명에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-117">This command gets information about the Authenticode signature for the four files listed at the command line.</span></span> <span data-ttu-id="30f57-118">이 예제에서 옵션 인 **FilePath** 매개 변수의 이름은 생략 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-118">In this example, the name of the **FilePath** parameter, which is optional, is omitted.</span></span>

### <span data-ttu-id="30f57-119">예 3: 여러 파일에 대해 유효한 Authenticode 서명만 가져오기</span><span class="sxs-lookup"><span data-stu-id="30f57-119">Example 3: Get only valid Authenticode signatures for multiple files</span></span>

```powershell
Get-ChildItem $PSHOME\*.* | ForEach-object {Get-AuthenticodeSignature $_} | Where-Object {$_.status -eq "Valid"}
```

<span data-ttu-id="30f57-120">이 명령은 `$PSHOME` 디렉터리에서 유효한 Authenticode 서명이 있는 모든 파일을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-120">This command lists all of the files in the `$PSHOME` directory that have a valid Authenticode signature.</span></span> <span data-ttu-id="30f57-121">`$PSHOME`자동 변수는 PowerShell 설치 디렉터리에 대 한 경로를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-121">The `$PSHOME` automatic variable contains the path to the PowerShell installation directory.</span></span>

<span data-ttu-id="30f57-122">이 명령은 cmdlet을 사용 하 여 `Get-ChildItem` 디렉터리의 파일을 `$PSHOME` 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-122">The command uses the `Get-ChildItem` cmdlet to get the files in the `$PSHOME` directory.</span></span> <span data-ttu-id="30f57-123">패턴을 사용 *합니다.*</span><span class="sxs-lookup"><span data-stu-id="30f57-123">It uses a pattern of *.*</span></span> <span data-ttu-id="30f57-124">디렉터리를 제외 하려면 (파일 이름에 점이 없는 파일도 제외)</span><span class="sxs-lookup"><span data-stu-id="30f57-124">to exclude directories (although it also excludes files without a dot in the filename).</span></span>

<span data-ttu-id="30f57-125">이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 파일을 `$PSHOME` cmdlet으로 보냅니다 `ForEach-Object` `Get-AuthenticodeSignature` .이 cmdlet은 각 파일에 대해를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-125">The command uses a pipeline operator (`|`) to send the files in `$PSHOME` to the `ForEach-Object` cmdlet, where `Get-AuthenticodeSignature` is called for each file.</span></span>

<span data-ttu-id="30f57-126">명령의 결과는 `Get-AuthenticodeSignature` `Where-Object` 유효한 상태로 서명 개체만 선택 하는 명령으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-126">The results of the `Get-AuthenticodeSignature` command are sent to a `Where-Object` command that selects only the signature objects with a status of Valid.</span></span>

### <span data-ttu-id="30f57-127">예제 4: 바이트 배열로 지정 된 파일 콘텐츠에 대 한 Authenticode 서명 가져오기</span><span class="sxs-lookup"><span data-stu-id="30f57-127">Example 4: Get the Authenticode signature for a file content specified as byte array</span></span>

```powershell
Get-AuthenticodeSignature -Content (Get-Content foo.ps1 -AsByteStream) -SourcePathorExtension ps1
```

<span data-ttu-id="30f57-128">이 명령은 파일의 콘텐츠에 대 한 Authenticode 서명에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-128">This command gets information about the Authenticode signature for the content of a file.</span></span> <span data-ttu-id="30f57-129">이 예에서는 파일 확장명이 파일의 내용과 함께 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-129">In this example, the file extension is specified along with the content of the file.</span></span>

## <span data-ttu-id="30f57-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="30f57-130">PARAMETERS</span></span>

### <span data-ttu-id="30f57-131">-콘텐츠</span><span class="sxs-lookup"><span data-stu-id="30f57-131">-Content</span></span>

<span data-ttu-id="30f57-132">Authenticode 서명이 검색 되는 바이트 배열인 파일의 콘텐츠입니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-132">Contents of a file as a byte array for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="30f57-133">이 매개 변수는 **SourcePathOrExtension** 매개 변수와 함께 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-133">This parameter must be used with **SourcePathOrExtension** parameter.</span></span> <span data-ttu-id="30f57-134">파일의 내용은 유니코드 (UTF-16LE) 형식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-134">The contents of the file must be in Unicode (UTF-16LE) format.</span></span>

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

### <span data-ttu-id="30f57-135">-FilePath</span><span class="sxs-lookup"><span data-stu-id="30f57-135">-FilePath</span></span>

<span data-ttu-id="30f57-136">검사할 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-136">Specifies the path to the file to examine.</span></span> <span data-ttu-id="30f57-137">와일드카드를 사용할 수 있지만 단일 파일로 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-137">Wildcards are permitted, but they must lead to a single file.</span></span> <span data-ttu-id="30f57-138">이 매개 변수의 값을 지정 하는 경우 명령줄에서 **FilePath** 를 입력할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-138">It is not necessary to type **FilePath** at the command line when you specify a value for this parameter.</span></span>

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

### <span data-ttu-id="30f57-139">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="30f57-139">-LiteralPath</span></span>

<span data-ttu-id="30f57-140">검사할 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-140">Specifies the path to the file being examined.</span></span> <span data-ttu-id="30f57-141">**FilePath** 와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-141">Unlike **FilePath**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="30f57-142">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-142">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="30f57-143">경로에 이스케이프 문자가 포함 되어 있으면 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-143">If the path includes an escape character, enclose it in single quotation marks.</span></span> <span data-ttu-id="30f57-144">작은따옴표는 모든 문자를 이스케이프 문자로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-144">Single quotation marks tell PowerShell not to interpret any characters as escape characters.</span></span>

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

### <span data-ttu-id="30f57-145">-SourcePathOrExtension</span><span class="sxs-lookup"><span data-stu-id="30f57-145">-SourcePathOrExtension</span></span>

<span data-ttu-id="30f57-146">Authenticode 서명이 검색 되는 콘텐츠의 파일 또는 파일 형식에 대 한 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-146">Path to the file or file type of the content for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="30f57-147">이 매개 변수는 파일 콘텐츠가 바이트 배열로 전달 되는 **콘텐츠와** 함께 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-147">This parameter is used with **Content** where file content is passed as a byte array.</span></span>

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

### <span data-ttu-id="30f57-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="30f57-148">CommonParameters</span></span>

<span data-ttu-id="30f57-149">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="30f57-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="30f57-150">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30f57-150">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="30f57-151">입력</span><span class="sxs-lookup"><span data-stu-id="30f57-151">INPUTS</span></span>

### <span data-ttu-id="30f57-152">System.String</span><span class="sxs-lookup"><span data-stu-id="30f57-152">System.String</span></span>

<span data-ttu-id="30f57-153">파일 경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Get-AuthenticodeSignature` .</span><span class="sxs-lookup"><span data-stu-id="30f57-153">You can pipe a string that contains a file path to `Get-AuthenticodeSignature`.</span></span>

## <span data-ttu-id="30f57-154">출력</span><span class="sxs-lookup"><span data-stu-id="30f57-154">OUTPUTS</span></span>

### <span data-ttu-id="30f57-155">System.object..</span><span class="sxs-lookup"><span data-stu-id="30f57-155">System.Management.Automation.Signature</span></span>

<span data-ttu-id="30f57-156">`Get-AuthenticodeSignature` 가져오는 각 시그니처에 대 한 서명 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-156">`Get-AuthenticodeSignature` returns a signature object for each signature that it gets.</span></span>

## <span data-ttu-id="30f57-157">참고</span><span class="sxs-lookup"><span data-stu-id="30f57-157">NOTES</span></span>

<span data-ttu-id="30f57-158">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30f57-158">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="30f57-159">PowerShell의 Authenticode 서명에 대 한 자세한 내용은 [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="30f57-159">For information about Authenticode signatures in PowerShell, see [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md).</span></span>

## <span data-ttu-id="30f57-160">관련 링크</span><span class="sxs-lookup"><span data-stu-id="30f57-160">RELATED LINKS</span></span>

[<span data-ttu-id="30f57-161">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="30f57-161">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="30f57-162">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="30f57-162">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="30f57-163">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="30f57-163">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

[<span data-ttu-id="30f57-164">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="30f57-164">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="30f57-165">about_Signing</span><span class="sxs-lookup"><span data-stu-id="30f57-165">about_Signing</span></span>](../Microsoft.PowerShell.Core/About/about_Signing.md)
