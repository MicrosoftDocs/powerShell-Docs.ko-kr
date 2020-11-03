---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 07/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/expand-archive?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Expand-Archive
ms.openlocfilehash: 41d571747a9b81cafff8c0ca20d5121163ece452
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "93218074"
---
# <span data-ttu-id="3c168-103">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="3c168-103">Expand-Archive</span></span>

## <span data-ttu-id="3c168-104">개요</span><span class="sxs-lookup"><span data-stu-id="3c168-104">SYNOPSIS</span></span>
<span data-ttu-id="3c168-105">지정 된 보관 파일 (zip)에서 파일을 추출 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-105">Extracts files from a specified archive (zipped) file.</span></span>

## <span data-ttu-id="3c168-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3c168-106">SYNTAX</span></span>

### <span data-ttu-id="3c168-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="3c168-107">Path (Default)</span></span>

```
Expand-Archive [-Path] <String> [[-DestinationPath] <String>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="3c168-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3c168-108">LiteralPath</span></span>

```
Expand-Archive -LiteralPath <String> [[-DestinationPath] <String>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="3c168-109">설명</span><span class="sxs-lookup"><span data-stu-id="3c168-109">DESCRIPTION</span></span>

<span data-ttu-id="3c168-110">Cmdlet은 지정 된 `Expand-Archive` 압축 된 보관 파일에서 지정 된 대상 폴더로 파일을 추출 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-110">The `Expand-Archive` cmdlet extracts files from a specified zipped archive file to a specified destination folder.</span></span> <span data-ttu-id="3c168-111">보관 파일을 사용 하면 여러 파일을 패키지 하 고 필요에 따라 압축 하 여 보다 쉽게 배포 하 고 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-111">An archive file allows multiple files to be packaged, and optionally compressed, into a single zipped file for easier distribution and storage.</span></span>

## <span data-ttu-id="3c168-112">예제</span><span class="sxs-lookup"><span data-stu-id="3c168-112">EXAMPLES</span></span>

### <span data-ttu-id="3c168-113">예제 1: 보관 파일의 콘텐츠 추출</span><span class="sxs-lookup"><span data-stu-id="3c168-113">Example 1: Extract the contents of an archive</span></span>

<span data-ttu-id="3c168-114">이 예제에서는 **DestinationPath** 매개 변수로 지정 된 폴더로 기존 보관 파일의 콘텐츠를 추출 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-114">This example extracts the contents of an existing archive file into the folder specified by the **DestinationPath** parameter.</span></span>

```powershell
Expand-Archive -LiteralPath 'C:\Archives\Draft[v1].Zip' -DestinationPath C:\Reference
```

<span data-ttu-id="3c168-115">이 예에서는 **LiteralPath** 매개 변수를 사용 합니다 .이 경우 파일 이름에는 와일드 카드로 해석 될 수 있는 문자가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-115">In this example, the **LiteralPath** parameter is used because the filename contains characters that could be interpreted as wildcards.</span></span>

### <span data-ttu-id="3c168-116">예 2: 현재 폴더에서 보관 파일의 압축 풀기</span><span class="sxs-lookup"><span data-stu-id="3c168-116">Example 2: Extract the contents of an archive in the current folder</span></span>

<span data-ttu-id="3c168-117">이 예제에서는 현재 폴더에 있는 기존 보관 파일의 콘텐츠를 **DestinationPath** 매개 변수로 지정 된 폴더로 추출 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-117">This example extracts the contents of an existing archive file in the current folder into the folder specified by the **DestinationPath** parameter.</span></span>

```powershell
Expand-Archive -Path Draftv2.Zip -DestinationPath C:\Reference
```

## <span data-ttu-id="3c168-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3c168-118">PARAMETERS</span></span>

### <span data-ttu-id="3c168-119">-DestinationPath</span><span class="sxs-lookup"><span data-stu-id="3c168-119">-DestinationPath</span></span>

<span data-ttu-id="3c168-120">기본적으로는 `Expand-Archive` ZIP 파일과 동일한 이름의 폴더를 현재 위치에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-120">By default, `Expand-Archive` creates a folder in the current location that is the same name as the ZIP file.</span></span> <span data-ttu-id="3c168-121">매개 변수를 사용 하 여 다른 폴더에 대 한 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-121">The parameter allows you to specify the path to a different folder.</span></span> <span data-ttu-id="3c168-122">대상 폴더가 없으면 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-122">The target folder is created if it does not exist.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: A folder in the current location
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c168-123">-Force</span><span class="sxs-lookup"><span data-stu-id="3c168-123">-Force</span></span>

<span data-ttu-id="3c168-124">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-124">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="3c168-125">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3c168-125">-LiteralPath</span></span>

<span data-ttu-id="3c168-126">보관 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-126">Specifies the path to an archive file.</span></span> <span data-ttu-id="3c168-127">**Path** 매개 변수와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-127">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="3c168-128">와일드카드 문자는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-128">Wildcard characters are not supported.</span></span> <span data-ttu-id="3c168-129">경로에 이스케이프 문자가 포함 된 경우 각 이스케이프 문자를 작은따옴표로 묶어 PowerShell에서 문자를 이스케이프 시퀀스로 해석 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-129">If the path includes escape characters, enclose each escape character in single quotation marks, to instruct PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3c168-130">-Path</span><span class="sxs-lookup"><span data-stu-id="3c168-130">-Path</span></span>

<span data-ttu-id="3c168-131">보관 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-131">Specifies the path to the archive file.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3c168-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3c168-132">-Confirm</span></span>

<span data-ttu-id="3c168-133">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-133">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c168-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3c168-134">-WhatIf</span></span>

<span data-ttu-id="3c168-135">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-135">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="3c168-136">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-136">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c168-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3c168-137">CommonParameters</span></span>
<span data-ttu-id="3c168-138">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3c168-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3c168-139">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c168-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3c168-140">입력</span><span class="sxs-lookup"><span data-stu-id="3c168-140">INPUTS</span></span>

### <span data-ttu-id="3c168-141">System.String</span><span class="sxs-lookup"><span data-stu-id="3c168-141">System.String</span></span>

<span data-ttu-id="3c168-142">기존 보관 파일에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-142">You can pipe a string that contains a path to an existing archive file.</span></span>

## <span data-ttu-id="3c168-143">출력</span><span class="sxs-lookup"><span data-stu-id="3c168-143">OUTPUTS</span></span>

### <span data-ttu-id="3c168-144">없음</span><span class="sxs-lookup"><span data-stu-id="3c168-144">None</span></span>

## <span data-ttu-id="3c168-145">참고</span><span class="sxs-lookup"><span data-stu-id="3c168-145">NOTES</span></span>

<span data-ttu-id="3c168-146">[ZIP 파일 사양은](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ASCII가 아닌 문자를 포함 하는 파일 이름을 인코딩 하는 표준 방법을 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-146">The [ZIP file specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) does not specify a standard way of encoding filenames that contain non-ASCII characters.</span></span> <span data-ttu-id="3c168-147">`Compress-Archive`Cmdlet은 utf-8 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-147">The `Compress-Archive` cmdlet uses UTF-8 encoding.</span></span> <span data-ttu-id="3c168-148">다른 ZIP 보관 도구는 다른 인코딩 체계를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-148">Other ZIP archive tools may use a different encoding scheme.</span></span> <span data-ttu-id="3c168-149">UTF-8 인코딩을 사용 하 여 저장 되지 않은 파일 이름을 가진 파일을 추출할 때는 `Expand-Archive` 보관 파일에 있는 원시 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-149">When extracting files with filenames not stored using UTF-8 encoding, `Expand-Archive` uses the raw value found in the archive.</span></span> <span data-ttu-id="3c168-150">이로 인해 보관 파일에 저장 된 원본 파일 이름과 다른 파일 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c168-150">This can result in a filename that is different than the source filename stored in the archive.</span></span>

## <span data-ttu-id="3c168-151">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3c168-151">RELATED LINKS</span></span>

[<span data-ttu-id="3c168-152">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="3c168-152">Compress-Archive</span></span>](compress-archive.md)
