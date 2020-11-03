---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 02/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/compress-archive?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compress-Archive
ms.openlocfilehash: 7bf349c82133b275f0539db7b78c3583d00da31c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215114"
---
# <span data-ttu-id="2bb38-103">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="2bb38-103">Compress-Archive</span></span>

## <span data-ttu-id="2bb38-104">개요</span><span class="sxs-lookup"><span data-stu-id="2bb38-104">SYNOPSIS</span></span>
<span data-ttu-id="2bb38-105">지정 된 파일 및 디렉터리에서 압축 된 보관 파일 또는 압축 된 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-105">Creates a compressed archive, or zipped file, from specified files and directories.</span></span>

## <span data-ttu-id="2bb38-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2bb38-106">SYNTAX</span></span>

### <span data-ttu-id="2bb38-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="2bb38-107">Path (Default)</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2bb38-108">PathWithUpdate</span><span class="sxs-lookup"><span data-stu-id="2bb38-108">PathWithUpdate</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Update
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2bb38-109">PathWithForce</span><span class="sxs-lookup"><span data-stu-id="2bb38-109">PathWithForce</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Force
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2bb38-110">LiteralPathWithUpdate</span><span class="sxs-lookup"><span data-stu-id="2bb38-110">LiteralPathWithUpdate</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Update [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2bb38-111">LiteralPathWithForce</span><span class="sxs-lookup"><span data-stu-id="2bb38-111">LiteralPathWithForce</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Force [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2bb38-112">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2bb38-112">LiteralPath</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2bb38-113">설명</span><span class="sxs-lookup"><span data-stu-id="2bb38-113">DESCRIPTION</span></span>

<span data-ttu-id="2bb38-114">`Compress-Archive`Cmdlet은 하나 이상의 지정 된 파일 또는 디렉터리에서 압축 되거나 압축 된 보관 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-114">The `Compress-Archive` cmdlet creates a compressed, or zipped, archive file from one or more specified files or directories.</span></span> <span data-ttu-id="2bb38-115">아카이브는 배포 및 저장을 용이 하 게 하기 위해 선택적 압축을 사용 하 여 여러 파일을 단일 zip 파일로 패키지 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-115">An archive packages multiple files, with optional compression, into a single zipped file for easier distribution and storage.</span></span> <span data-ttu-id="2bb38-116">**CompressionLevel** 매개 변수로 지정 된 압축 알고리즘을 사용 하 여 보관 파일을 압축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-116">An archive file can be compressed by using the compression algorithm specified by the **CompressionLevel** parameter.</span></span>

<span data-ttu-id="2bb38-117">`Compress-Archive`Cmdlet은 MICROSOFT .NET API [System.IO.Compression.Zip보관](/dotnet/api/system.io.compression.ziparchive) 을 사용 하 여 파일을 압축 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-117">The `Compress-Archive` cmdlet uses the Microsoft .NET API [System.IO.Compression.ZipArchive](/dotnet/api/system.io.compression.ziparchive) to compress files.</span></span>
<span data-ttu-id="2bb38-118">기본 API의 제한이 있으므로 최대 파일 크기는 2gb입니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-118">The maximum file size is 2 GB because there's a limitation of the underlying API.</span></span>

<span data-ttu-id="2bb38-119">일부 예제에서는 스 플랫를 사용 하 여 코드 샘플의 줄 길이를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-119">Some examples use splatting to reduce the line length of the code samples.</span></span> <span data-ttu-id="2bb38-120">자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2bb38-120">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="2bb38-121">예제</span><span class="sxs-lookup"><span data-stu-id="2bb38-121">EXAMPLES</span></span>

### <span data-ttu-id="2bb38-122">예 1: 파일을 압축 하 여 보관 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="2bb38-122">Example 1: Compress files to create an archive file</span></span>

<span data-ttu-id="2bb38-123">이 예에서는 다른 디렉터리의 파일을 압축 하 여 보관 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-123">This example compresses files from different directories and creates an archive file.</span></span> <span data-ttu-id="2bb38-124">와일드 카드는 특정 파일 확장명을 가진 모든 파일을 가져오는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-124">A wildcard is used to get all files with a particular file extension.</span></span> <span data-ttu-id="2bb38-125">**경로** 에 파일 이름만 지정 되므로 보관 파일에 디렉터리 구조가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-125">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
$compress = @{
  Path = "C:\Reference\Draftdoc.docx", "C:\Reference\Images\*.vsd"
  CompressionLevel = "Fastest"
  DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

<span data-ttu-id="2bb38-126">**Path** 매개 변수는 와일드 카드를 사용 하 여 특정 파일 이름 및 파일 이름을 허용 `*.vsd` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-126">The **Path** parameter accepts specific file names and file names with wildcards, `*.vsd`.</span></span> <span data-ttu-id="2bb38-127">**경로** 는 쉼표로 구분 된 목록을 사용 하 여 다른 디렉터리에서 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-127">The **Path** uses a comma-separated list to get files from different directories.</span></span> <span data-ttu-id="2bb38-128">압축 수준이 **가장 빠르게** 처리 시간을 단축 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-128">The compression level is **Fastest** to reduce processing time.</span></span> <span data-ttu-id="2bb38-129">**DestinationPath** 매개 변수는 파일의 위치를 지정 합니다 `Draft.zip` .</span><span class="sxs-lookup"><span data-stu-id="2bb38-129">The **DestinationPath** parameter specifies the location for the `Draft.zip` file.</span></span> <span data-ttu-id="2bb38-130">`Draft.zip`파일에는 `Draftdoc.docx` 및 확장명이 있는 모든 파일이 포함 되어 있습니다 `.vsd` .</span><span class="sxs-lookup"><span data-stu-id="2bb38-130">The `Draft.zip` file contains `Draftdoc.docx` and all the files with a `.vsd` extension.</span></span>

### <span data-ttu-id="2bb38-131">예제 2: LiteralPath를 사용 하 여 파일 압축</span><span class="sxs-lookup"><span data-stu-id="2bb38-131">Example 2: Compress files using a LiteralPath</span></span>

<span data-ttu-id="2bb38-132">이 예에서는 명명 된 특정 파일을 압축 하 고 새 보관 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-132">This example compresses specific named files and creates a new archive file.</span></span> <span data-ttu-id="2bb38-133">**경로** 에 파일 이름만 지정 되므로 보관 파일에 디렉터리 구조가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-133">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
$compress = @{
LiteralPath= "C:\Reference\Draft Doc.docx", "C:\Reference\Images\diagram2.vsd"
CompressionLevel = "Fastest"
DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

<span data-ttu-id="2bb38-134">**LiteralPath** 매개 변수는 와일드 카드를 허용 하지 않으므로 절대 경로 및 파일 이름이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-134">Absolute path and file names are used because the **LiteralPath** parameter doesn't accept wildcards.</span></span> <span data-ttu-id="2bb38-135">**경로** 는 쉼표로 구분 된 목록을 사용 하 여 다른 디렉터리에서 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-135">The **Path** uses a comma-separated list to get files from different directories.</span></span> <span data-ttu-id="2bb38-136">압축 수준이 **가장 빠르게** 처리 시간을 단축 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-136">The compression level is **Fastest** to reduce processing time.</span></span> <span data-ttu-id="2bb38-137">**DestinationPath** 매개 변수는 파일의 위치를 지정 합니다 `Draft.zip` .</span><span class="sxs-lookup"><span data-stu-id="2bb38-137">The **DestinationPath** parameter specifies the location for the `Draft.zip` file.</span></span> <span data-ttu-id="2bb38-138">파일에는 `Draft.zip` 및만 포함 `Draftdoc.docx` `diagram2.vsd` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-138">The `Draft.zip` file only contains `Draftdoc.docx` and `diagram2.vsd`.</span></span>

### <span data-ttu-id="2bb38-139">예 3: 루트 디렉터리를 포함 하는 디렉터리 압축</span><span class="sxs-lookup"><span data-stu-id="2bb38-139">Example 3: Compress a directory that includes the root directory</span></span>

<span data-ttu-id="2bb38-140">이 예제에서는 디렉터리를 압축 하 고 루트 디렉터리와 모든 파일 및 하위 디렉터리를 **포함** 하는 보관 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-140">This example compresses a directory and creates an archive file that **includes** the root directory, and all its files and subdirectories.</span></span> <span data-ttu-id="2bb38-141">**경로** 에서 루트 디렉터리를 지정 하기 때문에 보관 파일에는 디렉터리 구조가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-141">The archive file has a directory structure because the **Path** specifies a root directory.</span></span>

```powershell
Compress-Archive -Path C:\Reference -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="2bb38-142">`Compress-Archive`**Path** 매개 변수를 사용 하 여 루트 디렉터리를 지정 `C:\Reference` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-142">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference`.</span></span> <span data-ttu-id="2bb38-143">**DestinationPath** 매개 변수는 보관 파일의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-143">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="2bb38-144">`Draft.zip`보관 파일에는 `Reference` 루트 디렉터리와 모든 파일 및 하위 디렉터리가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-144">The `Draft.zip` archive includes the `Reference` root directory, and all its files and subdirectories.</span></span>

### <span data-ttu-id="2bb38-145">예 4: 루트 디렉터리를 제외 하는 디렉터리 압축</span><span class="sxs-lookup"><span data-stu-id="2bb38-145">Example 4: Compress a directory that excludes the root directory</span></span>

<span data-ttu-id="2bb38-146">이 예에서는 **경로** 에서 별표 () 와일드 카드를 사용 하기 때문에 디렉터리를 압축 하 고 루트 디렉터리를 **제외** 하는 보관 파일을 만듭니다 `*` .</span><span class="sxs-lookup"><span data-stu-id="2bb38-146">This example compresses a directory and creates an archive file that **excludes** the root directory because the **Path** uses an asterisk (`*`) wildcard.</span></span> <span data-ttu-id="2bb38-147">보관 파일에는 루트 디렉터리의 파일 및 하위 디렉터리를 포함 하는 디렉터리 구조가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-147">The archive contains a directory structure that contains the root directory's files and subdirectories.</span></span>

```powershell
Compress-Archive -Path C:\Reference\* -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="2bb38-148">`Compress-Archive`**Path** 매개 변수를 사용 하 여 `C:\Reference` 별표 () 와일드 카드를 사용 하 여 루트 디렉터리를 지정 `*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-148">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference` with an asterisk (`*`) wildcard.</span></span> <span data-ttu-id="2bb38-149">**DestinationPath** 매개 변수는 보관 파일의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-149">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="2bb38-150">`Draft.zip`보관 파일에는 루트 디렉터리의 파일 및 하위 디렉터리가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-150">The `Draft.zip` archive contains the root directory's files and subdirectories.</span></span> <span data-ttu-id="2bb38-151">`Reference`루트 디렉터리는 보관 파일에서 제외 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-151">The `Reference` root directory is excluded from the archive.</span></span>

### <span data-ttu-id="2bb38-152">예 5: 루트 디렉터리의 파일만 압축</span><span class="sxs-lookup"><span data-stu-id="2bb38-152">Example 5: Compress only the files in a root directory</span></span>

<span data-ttu-id="2bb38-153">이 예제에서는 루트 디렉터리의 파일만 압축 하 고 보관 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-153">This example compresses only the files in a root directory and creates an archive file.</span></span> <span data-ttu-id="2bb38-154">파일만 압축 되므로 아카이브에는 디렉터리 구조가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-154">There's no directory structure in the archive because only files are compressed.</span></span>

```powershell
Compress-Archive -Path C:\Reference\*.* -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="2bb38-155">`Compress-Archive`**Path** 매개 변수를 사용 하 여 `C:\Reference` 스타 별 **점 별** () 와일드 카드를 사용 하 여 루트 디렉터리를 지정 합니다 `*.*` .</span><span class="sxs-lookup"><span data-stu-id="2bb38-155">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference` with a **star-dot-star** (`*.*`) wildcard.</span></span> <span data-ttu-id="2bb38-156">**DestinationPath** 매개 변수는 보관 파일의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-156">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="2bb38-157">`Draft.zip`보관 파일에는 `Reference` 루트 디렉터리의 파일만 포함 되 고 루트 디렉터리는 제외 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-157">The `Draft.zip` archive only contains the `Reference` root directory's files and the root directory is excluded.</span></span>

### <span data-ttu-id="2bb38-158">예제 6: 파이프라인을 사용 하 여 파일 보관</span><span class="sxs-lookup"><span data-stu-id="2bb38-158">Example 6: Use the pipeline to archive files</span></span>

<span data-ttu-id="2bb38-159">이 예제에서는 파일을 파이프라인으로 전송 하 여 보관 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-159">This example sends files down the pipeline to create an archive.</span></span> <span data-ttu-id="2bb38-160">**경로** 에 파일 이름만 지정 되므로 보관 파일에 디렉터리 구조가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-160">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
Get-ChildItem -Path C:\Reference\Afile.txt, C:\Reference\Images\Bfile.txt |
  Compress-Archive -DestinationPath C:\Archives\PipelineFiles.zip
```

<span data-ttu-id="2bb38-161">`Get-ChildItem`**Path** 매개 변수를 사용 하 여 다른 디렉터리에서 두 개의 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-161">`Get-ChildItem` uses the **Path** parameter to specify two files from different directories.</span></span> <span data-ttu-id="2bb38-162">각 파일은 **FileInfo** 개체로 표시 되며 파이프라인에서로 전송 됩니다 `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="2bb38-162">Each file is represented by a **FileInfo** object and is sent down the pipeline to `Compress-Archive`.</span></span>
<span data-ttu-id="2bb38-163">지정 된 두 파일은에 보관 되어 `PipelineFiles.zip` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-163">The two specified files are archived in `PipelineFiles.zip`.</span></span>

### <span data-ttu-id="2bb38-164">예 7: 파이프라인을 사용 하 여 디렉터리 보관</span><span class="sxs-lookup"><span data-stu-id="2bb38-164">Example 7: Use the pipeline to archive a directory</span></span>

<span data-ttu-id="2bb38-165">이 예에서는 파이프라인에서 디렉터리를 전송 하 여 보관 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-165">This example sends a directory down the pipeline to create an archive.</span></span> <span data-ttu-id="2bb38-166">파일은 **system.io.directoryinfo** 개체로 서 **FileInfo** 개체와 디렉터리로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-166">Files are sent as **FileInfo** objects and directories as **DirectoryInfo** objects.</span></span> <span data-ttu-id="2bb38-167">보관 디렉터리 구조는 루트 디렉터리를 포함 하지 않지만 해당 파일 및 하위 디렉터리는 보관 파일에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-167">The archive's directory structure doesn't include the root directory, but its files and subdirectories are included in the archive.</span></span>

```powershell
Get-ChildItem -Path C:\LogFiles | Compress-Archive -DestinationPath C:\Archives\PipelineDir.zip
```

<span data-ttu-id="2bb38-168">`Get-ChildItem`**Path** 매개 변수를 사용 하 여 `C:\LogFiles` 루트 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-168">`Get-ChildItem` uses the **Path** parameter to specify the `C:\LogFiles` root directory.</span></span> <span data-ttu-id="2bb38-169">각 **FileInfo** 및 **system.io.directoryinfo** 개체는 파이프라인으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-169">Each **FileInfo** and **DirectoryInfo** object is sent down the pipeline.</span></span>

<span data-ttu-id="2bb38-170">`Compress-Archive` 각 개체를 `PipelineDir.zip` 보관 파일에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-170">`Compress-Archive` adds each object to the `PipelineDir.zip` archive.</span></span> <span data-ttu-id="2bb38-171">파이프라인 개체가 매개 변수 위치 0으로 수신 되기 때문에 **Path** 매개 변수를 지정 하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-171">The **Path** parameter isn't specified because the pipeline objects are received into parameter position 0.</span></span>

### <span data-ttu-id="2bb38-172">예 8: 재귀가 보관에 영향을 줄 수 있는 방법</span><span class="sxs-lookup"><span data-stu-id="2bb38-172">Example 8: How recursion can affect archives</span></span>

<span data-ttu-id="2bb38-173">이 예제에서는 재귀가 보관 파일의 파일을 중복 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-173">This example shows how recursion can duplicate files in your archive.</span></span> <span data-ttu-id="2bb38-174">예를 들어를 `Get-ChildItem` **재귀** 매개 변수와 함께 사용 하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-174">For example, if you use `Get-ChildItem` with the **Recurse** parameter.</span></span> <span data-ttu-id="2bb38-175">재귀 프로세스에서 각 **FileInfo** 및 **system.io.directoryinfo** 개체는 파이프라인으로 전송 되어 보관에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-175">As recursion processes, each **FileInfo** and **DirectoryInfo** object is sent down the pipeline and added to the archive.</span></span>

```powershell
Get-ChildItem -Path C:\TestLog -Recurse |
  Compress-Archive -DestinationPath C:\Archives\PipelineRecurse.zip
```

<span data-ttu-id="2bb38-176">`C:\TestLog`디렉터리에 파일이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-176">The `C:\TestLog` directory doesn't contain any files.</span></span> <span data-ttu-id="2bb38-177">파일이 포함 된 라는 하위 디렉터리를 포함 `testsub` `testlog.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-177">It does contain a subdirectory named `testsub` that contains the `testlog.txt` file.</span></span>

<span data-ttu-id="2bb38-178">`Get-ChildItem`**Path** 매개 변수를 사용 하 여 루트 디렉터리를 지정 `C:\TestLog` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-178">`Get-ChildItem` uses the **Path** parameter to specify the root directory, `C:\TestLog`.</span></span> <span data-ttu-id="2bb38-179">**재귀** 매개 변수는 파일 및 디렉터리를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-179">The **Recurse** parameter processes the files and directories.</span></span> <span data-ttu-id="2bb38-180">및 FileInfo 개체에 대해 **system.io.directoryinfo** 개체가 생성 됩니다 `testsub` **FileInfo** `testlog.txt` .</span><span class="sxs-lookup"><span data-stu-id="2bb38-180">A **DirectoryInfo** object is created for `testsub` and a **FileInfo** object `testlog.txt`.</span></span>

<span data-ttu-id="2bb38-181">각 개체는 파이프라인에서로 전송 됩니다 `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="2bb38-181">Each object is sent down the pipeline to `Compress-Archive`.</span></span> <span data-ttu-id="2bb38-182">**DestinationPath** 는 보관 파일의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-182">The **DestinationPath** specifies the location for the archive file.</span></span> <span data-ttu-id="2bb38-183">파이프라인 개체가 매개 변수 위치 0으로 수신 되기 때문에 **Path** 매개 변수를 지정 하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-183">The **Path** parameter isn't specified because the pipeline objects are received into parameter position 0.</span></span>

<span data-ttu-id="2bb38-184">다음 요약에서는 `PipelineRecurse.zip` 중복 파일을 포함 하는 보관 파일의 내용에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-184">The following summary describes the `PipelineRecurse.zip` archive's contents that contains a duplicate file:</span></span>

- <span data-ttu-id="2bb38-185">**System.io.directoryinfo** 개체는 디렉터리를 만들고 `testsub` `testlog.txt` 원래 디렉터리 구조를 반영 하는 파일을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-185">The **DirectoryInfo** object creates the `testsub` directory and contains the `testlog.txt` file, which reflects the original directory structure.</span></span>
- <span data-ttu-id="2bb38-186">**FileInfo** 개체는 `testlog.txt` 아카이브의 루트에 중복을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-186">The **FileInfo** object creates a duplicate `testlog.txt` in the archive's root.</span></span> <span data-ttu-id="2bb38-187">재귀가 파일 개체를로 보내기 때문에 중복 된 파일이 생성 됩니다 `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="2bb38-187">The duplicate file is created because recursion sent a file object to `Compress-Archive`.</span></span> <span data-ttu-id="2bb38-188">파이프라인으로 전송 된 각 개체가 보관에 추가 되기 때문에이 동작이 예상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-188">This behavior is expected because each object sent down the pipeline is added to the archive.</span></span>

### <span data-ttu-id="2bb38-189">예 9: 기존 보관 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="2bb38-189">Example 9: Update an existing archive file</span></span>

<span data-ttu-id="2bb38-190">이 예에서는 디렉터리에서 기존 보관 파일인 `Draft.Zip` 를 업데이트 `C:\Archives` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-190">This example updates an existing archive file, `Draft.Zip`, in the `C:\Archives` directory.</span></span> <span data-ttu-id="2bb38-191">이 예에서 기존 보관 파일에는 루트 디렉터리와 해당 파일 및 하위 디렉터리가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-191">In this example, the existing archive file contains the root directory, and its files and subdirectories.</span></span>

```powershell
Compress-Archive -Path C:\Reference -Update -DestinationPath C:\Archives\Draft.Zip
```

<span data-ttu-id="2bb38-192">명령은 `Draft.Zip` `C:\Reference` 디렉터리와 해당 하위 디렉터리에 있는 기존 파일의 최신 버전으로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-192">The command updates `Draft.Zip` with newer versions of existing files in the `C:\Reference` directory and its subdirectories.</span></span> <span data-ttu-id="2bb38-193">또는 해당 하위 디렉터리에 추가 된 새 파일 `C:\Reference` 은 업데이트 된 보관 파일에 포함 됩니다 `Draft.Zip` .</span><span class="sxs-lookup"><span data-stu-id="2bb38-193">And, new files that were added to `C:\Reference` or its subdirectories are included in the updated `Draft.Zip` archive.</span></span>

## <span data-ttu-id="2bb38-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2bb38-194">PARAMETERS</span></span>

### <span data-ttu-id="2bb38-195">-CompressionLevel</span><span class="sxs-lookup"><span data-stu-id="2bb38-195">-CompressionLevel</span></span>

<span data-ttu-id="2bb38-196">보관 파일을 만들 때 적용할 압축 크기를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-196">Specifies how much compression to apply when you're creating the archive file.</span></span> <span data-ttu-id="2bb38-197">더 빠른 압축을 사용 하면 파일을 만드는 데 시간이 더 소요 되지만 파일 크기가 커질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-197">Faster compression requires less time to create the file, but can result in larger file sizes.</span></span>

<span data-ttu-id="2bb38-198">이 매개 변수를 지정 하지 않으면 명령에서 기본값인 **최적** 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-198">If this parameter isn't specified, the command uses the default value, **Optimal** .</span></span>

<span data-ttu-id="2bb38-199">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-199">The following are the acceptable values for this parameter:</span></span>

- <span data-ttu-id="2bb38-200">**가장 빠름** .</span><span class="sxs-lookup"><span data-stu-id="2bb38-200">**Fastest** .</span></span> <span data-ttu-id="2bb38-201">가장 빠른 압축 방법을 사용 하 여 처리 시간을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-201">Use the fastest compression method available to reduce processing time.</span></span> <span data-ttu-id="2bb38-202">더 빠른 압축으로 인해 파일 크기가 커질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-202">Faster compression can result in larger file sizes.</span></span>
- <span data-ttu-id="2bb38-203">**Nocompression** .</span><span class="sxs-lookup"><span data-stu-id="2bb38-203">**NoCompression** .</span></span> <span data-ttu-id="2bb38-204">원본 파일을 압축 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-204">Doesn't compress the source files.</span></span>
- <span data-ttu-id="2bb38-205">**최적** .</span><span class="sxs-lookup"><span data-stu-id="2bb38-205">**Optimal** .</span></span> <span data-ttu-id="2bb38-206">처리 시간은 파일 크기에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-206">Processing time is dependent on file size.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Optimal, NoCompression, Fastest

Required: False
Position: Named
Default value: Optimal
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2bb38-207">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2bb38-207">-Confirm</span></span>

<span data-ttu-id="2bb38-208">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-208">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2bb38-209">-DestinationPath</span><span class="sxs-lookup"><span data-stu-id="2bb38-209">-DestinationPath</span></span>

<span data-ttu-id="2bb38-210">이 매개 변수는 필수 이며 보관 출력 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-210">This parameter is required and specifies the path to the archive output file.</span></span> <span data-ttu-id="2bb38-211">**DestinationPath** 에는 압축 된 파일의 이름, 압축 된 파일에 대 한 절대 경로 또는 상대 경로를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-211">The **DestinationPath** should include the name of the zipped file, and either the absolute or relative path to the zipped file.</span></span>

<span data-ttu-id="2bb38-212">**DestinationPath** 의 파일 이름에 파일 이름 확장명이 없는 경우 `.zip` cmdlet은 `.zip` 파일 이름 확장명을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-212">If the file name in **DestinationPath** doesn't have a `.zip` file name extension, the cmdlet adds the `.zip` file name extension.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2bb38-213">-Force</span><span class="sxs-lookup"><span data-stu-id="2bb38-213">-Force</span></span>

<span data-ttu-id="2bb38-214">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-214">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithForce, LiteralPathWithForce
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2bb38-215">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2bb38-215">-LiteralPath</span></span>

<span data-ttu-id="2bb38-216">아카이브 압축 파일에 추가 하려는 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-216">Specifies the path or paths to the files that you want to add to the archive zipped file.</span></span> <span data-ttu-id="2bb38-217">**Path** 매개 변수와 달리 **LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-217">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="2bb38-218">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-218">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="2bb38-219">경로에 이스케이프 문자가 포함 된 경우 각 이스케이프 문자를 작은따옴표로 묶어 PowerShell에서 문자를 이스케이프 시퀀스로 해석 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-219">If the path includes escape characters, enclose each escape character in single quotation marks, to instruct PowerShell not to interpret any characters as escape sequences.</span></span>
<span data-ttu-id="2bb38-220">여러 경로를 지정 하 고 출력 압축 파일의 여러 위치에 파일을 포함 하려면 쉼표를 사용 하 여 경로를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-220">To specify multiple paths, and include files in multiple locations in your output zipped file, use commas to separate the paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPathWithUpdate, LiteralPathWithForce, LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2bb38-221">-PassThru</span><span class="sxs-lookup"><span data-stu-id="2bb38-221">-PassThru</span></span>

<span data-ttu-id="2bb38-222">Cmdlet이 생성 된 보관 파일을 나타내는 파일 개체를 출력 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-222">Causes the cmdlet to output a file object representing the archive file created.</span></span>

<span data-ttu-id="2bb38-223">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-223">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2bb38-224">-Path</span><span class="sxs-lookup"><span data-stu-id="2bb38-224">-Path</span></span>

<span data-ttu-id="2bb38-225">아카이브 압축 파일에 추가 하려는 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-225">Specifies the path or paths to the files that you want to add to the archive zipped file.</span></span> <span data-ttu-id="2bb38-226">여러 경로를 지정 하 고 여러 위치에 파일을 포함 하려면 쉼표를 사용 하 여 경로를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-226">To specify multiple paths, and include files in multiple locations, use commas to separate the paths.</span></span>

<span data-ttu-id="2bb38-227">이 매개 변수는 와일드 카드 문자를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-227">This parameter accepts wildcard characters.</span></span> <span data-ttu-id="2bb38-228">와일드 카드 문자를 사용 하 여 디렉터리의 모든 파일을 보관 파일에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-228">Wildcard characters allow you to add all files in a directory to your archive file.</span></span>

<span data-ttu-id="2bb38-229">루트 디렉터리와 함께 와일드 카드를 사용 하면 보관 파일의 내용에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-229">Using wildcards with a root directory affects the archive's contents:</span></span>

- <span data-ttu-id="2bb38-230">루트 디렉터리와 모든 파일 및 하위 디렉터리를 **포함** 하는 보관 파일을 만들려면 **경로** 에 와일드 카드 없이 루트 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-230">To create an archive that **includes** the root directory, and all its files and subdirectories, specify the root directory in the **Path** without wildcards.</span></span> <span data-ttu-id="2bb38-231">`-Path C:\Reference`</span><span class="sxs-lookup"><span data-stu-id="2bb38-231">For example: `-Path C:\Reference`</span></span>
- <span data-ttu-id="2bb38-232">루트 디렉터리를 **제외** 하 고 모든 파일 및 하위 디렉터리를 zips 보관 파일을 만들려면 별표 ( `*` ) 와일드 카드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-232">To create an archive that **excludes** the root directory, but zips all its files and subdirectories, use the asterisk (`*`) wildcard.</span></span> <span data-ttu-id="2bb38-233">`-Path C:\Reference\*`</span><span class="sxs-lookup"><span data-stu-id="2bb38-233">For example: `-Path C:\Reference\*`</span></span>
- <span data-ttu-id="2bb38-234">루트 디렉터리의 파일만 zips 보관 파일을 만들려면 **star-점선** ( `*.*` ) 와일드 카드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-234">To create an archive that only zips the files in the root directory, use the **star-dot-star** (`*.*`) wildcard.</span></span> <span data-ttu-id="2bb38-235">루트의 하위 디렉터리는 보관 파일에 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-235">Subdirectories of the root aren't included in the archive.</span></span> <span data-ttu-id="2bb38-236">`-Path C:\Reference\*.*`</span><span class="sxs-lookup"><span data-stu-id="2bb38-236">For example: `-Path C:\Reference\*.*`</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path, PathWithUpdate, PathWithForce
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="2bb38-237">-업데이트</span><span class="sxs-lookup"><span data-stu-id="2bb38-237">-Update</span></span>

<span data-ttu-id="2bb38-238">보관의 이전 파일 버전을 이름이 같은 최신 파일 버전으로 바꿔 지정 된 보관 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-238">Updates the specified archive by replacing older file versions in the archive with newer file versions that have the same names.</span></span> <span data-ttu-id="2bb38-239">이 매개 변수를 추가 하 여 기존 보관 파일에 파일을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-239">You can also add this parameter to add files to an existing archive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithUpdate, LiteralPathWithUpdate
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2bb38-240">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2bb38-240">-WhatIf</span></span>

<span data-ttu-id="2bb38-241">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-241">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="2bb38-242">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-242">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="2bb38-243">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2bb38-243">CommonParameters</span></span>

<span data-ttu-id="2bb38-244">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2bb38-244">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2bb38-245">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2bb38-245">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2bb38-246">입력</span><span class="sxs-lookup"><span data-stu-id="2bb38-246">INPUTS</span></span>

### <span data-ttu-id="2bb38-247">System.String</span><span class="sxs-lookup"><span data-stu-id="2bb38-247">System.String</span></span>

<span data-ttu-id="2bb38-248">하나 이상의 파일에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-248">You can pipe a string that contains a path to one or more files.</span></span>

## <span data-ttu-id="2bb38-249">출력</span><span class="sxs-lookup"><span data-stu-id="2bb38-249">OUTPUTS</span></span>

### <span data-ttu-id="2bb38-250">System.object</span><span class="sxs-lookup"><span data-stu-id="2bb38-250">System.IO.FileInfo</span></span>

<span data-ttu-id="2bb38-251">이 cmdlet은 **PassThru** 매개 변수를 사용 하는 경우에만 **FileInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-251">The cmdlet only returns a **FileInfo** object when you use the **PassThru** parameter.</span></span>

## <span data-ttu-id="2bb38-252">참고</span><span class="sxs-lookup"><span data-stu-id="2bb38-252">NOTES</span></span>

<span data-ttu-id="2bb38-253">재귀를 사용 하 여 개체를 아래로 보내면 보관 파일의 파일이 중복 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-253">Using recursion and sending objects down the pipeline can duplicate files in your archive.</span></span> <span data-ttu-id="2bb38-254">예를 들어를 `Get-ChildItem` **재귀** 매개 변수와 함께 사용 하는 경우 파이프라인으로 전송 된 각 **FileInfo** 및 **system.io.directoryinfo** 개체가 보관에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-254">For example, if you use `Get-ChildItem` with the **Recurse** parameter, each **FileInfo** and **DirectoryInfo** object that's sent down the pipeline is added to the archive.</span></span>

<span data-ttu-id="2bb38-255">[ZIP 파일 사양은](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ASCII가 아닌 문자를 포함 하는 파일 이름을 인코딩 하는 표준 방법을 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-255">The [ZIP file specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) does not specify a standard way of encoding filenames that contain non-ASCII characters.</span></span> <span data-ttu-id="2bb38-256">`Compress-Archive`Cmdlet은 utf-8 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-256">The `Compress-Archive` cmdlet uses UTF-8 encoding.</span></span> <span data-ttu-id="2bb38-257">다른 ZIP 보관 도구는 다른 인코딩 체계를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-257">Other ZIP archive tools may use a different encoding scheme.</span></span> <span data-ttu-id="2bb38-258">UTF-8 인코딩을 사용 하 여 저장 되지 않은 파일 이름을 가진 파일을 추출할 때는 `Expand-Archive` 보관 파일에 있는 원시 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-258">When extracting files with filenames not stored using UTF-8 encoding, `Expand-Archive` uses the raw value found in the archive.</span></span> <span data-ttu-id="2bb38-259">이로 인해 보관 파일에 저장 된 원본 파일 이름과 다른 파일 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bb38-259">This can result in a filename that is different than the source filename stored in the archive.</span></span>

## <span data-ttu-id="2bb38-260">관련 링크</span><span class="sxs-lookup"><span data-stu-id="2bb38-260">RELATED LINKS</span></span>

[<span data-ttu-id="2bb38-261">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="2bb38-261">Expand-Archive</span></span>](Expand-Archive.md)

[<span data-ttu-id="2bb38-262">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="2bb38-262">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)
