---
external help file: Microsoft.PowerShell.Archive-help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 02/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/compress-archive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compress-Archive
ms.openlocfilehash: 58807ba0745a6b09e7956547425c489b427d4f4b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599565"
---
# <span data-ttu-id="7fe94-102">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="7fe94-102">Compress-Archive</span></span>

## <span data-ttu-id="7fe94-103">개요</span><span class="sxs-lookup"><span data-stu-id="7fe94-103">SYNOPSIS</span></span>
<span data-ttu-id="7fe94-104">지정 된 파일 및 디렉터리에서 압축 된 보관 파일 또는 압축 된 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-104">Creates a compressed archive, or zipped file, from specified files and directories.</span></span>

## <span data-ttu-id="7fe94-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7fe94-105">SYNTAX</span></span>

### <span data-ttu-id="7fe94-106">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="7fe94-106">Path (Default)</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7fe94-107">PathWithUpdate</span><span class="sxs-lookup"><span data-stu-id="7fe94-107">PathWithUpdate</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Update
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7fe94-108">PathWithForce</span><span class="sxs-lookup"><span data-stu-id="7fe94-108">PathWithForce</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Force
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7fe94-109">LiteralPathWithUpdate</span><span class="sxs-lookup"><span data-stu-id="7fe94-109">LiteralPathWithUpdate</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Update [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7fe94-110">LiteralPathWithForce</span><span class="sxs-lookup"><span data-stu-id="7fe94-110">LiteralPathWithForce</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Force [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7fe94-111">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7fe94-111">LiteralPath</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7fe94-112">설명</span><span class="sxs-lookup"><span data-stu-id="7fe94-112">DESCRIPTION</span></span>

<span data-ttu-id="7fe94-113">`Compress-Archive`Cmdlet은 하나 이상의 지정 된 파일 또는 디렉터리에서 압축 되거나 압축 된 보관 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-113">The `Compress-Archive` cmdlet creates a compressed, or zipped, archive file from one or more specified files or directories.</span></span> <span data-ttu-id="7fe94-114">아카이브는 배포 및 저장을 용이 하 게 하기 위해 선택적 압축을 사용 하 여 여러 파일을 단일 zip 파일로 패키지 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-114">An archive packages multiple files, with optional compression, into a single zipped file for easier distribution and storage.</span></span> <span data-ttu-id="7fe94-115">**CompressionLevel** 매개 변수로 지정 된 압축 알고리즘을 사용 하 여 보관 파일을 압축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-115">An archive file can be compressed by using the compression algorithm specified by the **CompressionLevel** parameter.</span></span>

<span data-ttu-id="7fe94-116">`Compress-Archive`Cmdlet은 MICROSOFT .NET API [System.IO.Compression.Zip보관](/dotnet/api/system.io.compression.ziparchive) 을 사용 하 여 파일을 압축 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-116">The `Compress-Archive` cmdlet uses the Microsoft .NET API [System.IO.Compression.ZipArchive](/dotnet/api/system.io.compression.ziparchive) to compress files.</span></span>
<span data-ttu-id="7fe94-117">기본 API의 제한이 있으므로 최대 파일 크기는 2gb입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-117">The maximum file size is 2 GB because there's a limitation of the underlying API.</span></span>

<span data-ttu-id="7fe94-118">일부 예제에서는 스 플랫를 사용 하 여 코드 샘플의 줄 길이를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-118">Some examples use splatting to reduce the line length of the code samples.</span></span> <span data-ttu-id="7fe94-119">자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7fe94-119">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="7fe94-120">예제</span><span class="sxs-lookup"><span data-stu-id="7fe94-120">EXAMPLES</span></span>

### <span data-ttu-id="7fe94-121">예 1: 파일을 압축 하 여 보관 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="7fe94-121">Example 1: Compress files to create an archive file</span></span>

<span data-ttu-id="7fe94-122">이 예에서는 다른 디렉터리의 파일을 압축 하 여 보관 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-122">This example compresses files from different directories and creates an archive file.</span></span> <span data-ttu-id="7fe94-123">와일드 카드는 특정 파일 확장명을 가진 모든 파일을 가져오는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-123">A wildcard is used to get all files with a particular file extension.</span></span> <span data-ttu-id="7fe94-124">**경로** 에 파일 이름만 지정 되므로 보관 파일에 디렉터리 구조가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-124">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
$compress = @{
  Path = "C:\Reference\Draftdoc.docx", "C:\Reference\Images\*.vsd"
  CompressionLevel = "Fastest"
  DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

<span data-ttu-id="7fe94-125">**Path** 매개 변수는 와일드 카드를 사용 하 여 특정 파일 이름 및 파일 이름을 허용 `*.vsd` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-125">The **Path** parameter accepts specific file names and file names with wildcards, `*.vsd`.</span></span> <span data-ttu-id="7fe94-126">**경로** 는 쉼표로 구분 된 목록을 사용 하 여 다른 디렉터리에서 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-126">The **Path** uses a comma-separated list to get files from different directories.</span></span> <span data-ttu-id="7fe94-127">압축 수준이 **가장 빠르게** 처리 시간을 단축 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-127">The compression level is **Fastest** to reduce processing time.</span></span> <span data-ttu-id="7fe94-128">**DestinationPath** 매개 변수는 파일의 위치를 지정 합니다 `Draft.zip` .</span><span class="sxs-lookup"><span data-stu-id="7fe94-128">The **DestinationPath** parameter specifies the location for the `Draft.zip` file.</span></span> <span data-ttu-id="7fe94-129">`Draft.zip`파일에는 `Draftdoc.docx` 및 확장명이 있는 모든 파일이 포함 되어 있습니다 `.vsd` .</span><span class="sxs-lookup"><span data-stu-id="7fe94-129">The `Draft.zip` file contains `Draftdoc.docx` and all the files with a `.vsd` extension.</span></span>

### <span data-ttu-id="7fe94-130">예제 2: LiteralPath를 사용 하 여 파일 압축</span><span class="sxs-lookup"><span data-stu-id="7fe94-130">Example 2: Compress files using a LiteralPath</span></span>

<span data-ttu-id="7fe94-131">이 예에서는 명명 된 특정 파일을 압축 하 고 새 보관 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-131">This example compresses specific named files and creates a new archive file.</span></span> <span data-ttu-id="7fe94-132">**경로** 에 파일 이름만 지정 되므로 보관 파일에 디렉터리 구조가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-132">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
$compress = @{
LiteralPath= "C:\Reference\Draft Doc.docx", "C:\Reference\Images\diagram2.vsd"
CompressionLevel = "Fastest"
DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

<span data-ttu-id="7fe94-133">**LiteralPath** 매개 변수는 와일드 카드를 허용 하지 않으므로 절대 경로 및 파일 이름이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-133">Absolute path and file names are used because the **LiteralPath** parameter doesn't accept wildcards.</span></span> <span data-ttu-id="7fe94-134">**경로** 는 쉼표로 구분 된 목록을 사용 하 여 다른 디렉터리에서 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-134">The **Path** uses a comma-separated list to get files from different directories.</span></span> <span data-ttu-id="7fe94-135">압축 수준이 **가장 빠르게** 처리 시간을 단축 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-135">The compression level is **Fastest** to reduce processing time.</span></span> <span data-ttu-id="7fe94-136">**DestinationPath** 매개 변수는 파일의 위치를 지정 합니다 `Draft.zip` .</span><span class="sxs-lookup"><span data-stu-id="7fe94-136">The **DestinationPath** parameter specifies the location for the `Draft.zip` file.</span></span> <span data-ttu-id="7fe94-137">파일에는 `Draft.zip` 및만 포함 `Draftdoc.docx` `diagram2.vsd` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-137">The `Draft.zip` file only contains `Draftdoc.docx` and `diagram2.vsd`.</span></span>

### <span data-ttu-id="7fe94-138">예 3: 루트 디렉터리를 포함 하는 디렉터리 압축</span><span class="sxs-lookup"><span data-stu-id="7fe94-138">Example 3: Compress a directory that includes the root directory</span></span>

<span data-ttu-id="7fe94-139">이 예제에서는 디렉터리를 압축 하 고 루트 디렉터리와 모든 파일 및 하위 디렉터리를 **포함** 하는 보관 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-139">This example compresses a directory and creates an archive file that **includes** the root directory, and all its files and subdirectories.</span></span> <span data-ttu-id="7fe94-140">**경로** 에서 루트 디렉터리를 지정 하기 때문에 보관 파일에는 디렉터리 구조가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-140">The archive file has a directory structure because the **Path** specifies a root directory.</span></span>

```powershell
Compress-Archive -Path C:\Reference -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="7fe94-141">`Compress-Archive`**Path** 매개 변수를 사용 하 여 루트 디렉터리를 지정 `C:\Reference` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-141">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference`.</span></span> <span data-ttu-id="7fe94-142">**DestinationPath** 매개 변수는 보관 파일의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-142">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="7fe94-143">`Draft.zip`보관 파일에는 `Reference` 루트 디렉터리와 모든 파일 및 하위 디렉터리가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-143">The `Draft.zip` archive includes the `Reference` root directory, and all its files and subdirectories.</span></span>

### <span data-ttu-id="7fe94-144">예 4: 루트 디렉터리를 제외 하는 디렉터리 압축</span><span class="sxs-lookup"><span data-stu-id="7fe94-144">Example 4: Compress a directory that excludes the root directory</span></span>

<span data-ttu-id="7fe94-145">이 예에서는 **경로** 에서 별표 () 와일드 카드를 사용 하기 때문에 디렉터리를 압축 하 고 루트 디렉터리를 **제외** 하는 보관 파일을 만듭니다 `*` .</span><span class="sxs-lookup"><span data-stu-id="7fe94-145">This example compresses a directory and creates an archive file that **excludes** the root directory because the **Path** uses an asterisk (`*`) wildcard.</span></span> <span data-ttu-id="7fe94-146">보관 파일에는 루트 디렉터리의 파일 및 하위 디렉터리를 포함 하는 디렉터리 구조가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-146">The archive contains a directory structure that contains the root directory's files and subdirectories.</span></span>

```powershell
Compress-Archive -Path C:\Reference\* -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="7fe94-147">`Compress-Archive`**Path** 매개 변수를 사용 하 여 `C:\Reference` 별표 () 와일드 카드를 사용 하 여 루트 디렉터리를 지정 `*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-147">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference` with an asterisk (`*`) wildcard.</span></span> <span data-ttu-id="7fe94-148">**DestinationPath** 매개 변수는 보관 파일의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-148">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="7fe94-149">`Draft.zip`보관 파일에는 루트 디렉터리의 파일 및 하위 디렉터리가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-149">The `Draft.zip` archive contains the root directory's files and subdirectories.</span></span> <span data-ttu-id="7fe94-150">`Reference`루트 디렉터리는 보관 파일에서 제외 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-150">The `Reference` root directory is excluded from the archive.</span></span>

### <span data-ttu-id="7fe94-151">예 5: 루트 디렉터리의 파일만 압축</span><span class="sxs-lookup"><span data-stu-id="7fe94-151">Example 5: Compress only the files in a root directory</span></span>

<span data-ttu-id="7fe94-152">이 예제에서는 루트 디렉터리의 파일만 압축 하 고 보관 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-152">This example compresses only the files in a root directory and creates an archive file.</span></span> <span data-ttu-id="7fe94-153">파일만 압축 되므로 아카이브에는 디렉터리 구조가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-153">There's no directory structure in the archive because only files are compressed.</span></span>

```powershell
Compress-Archive -Path C:\Reference\*.* -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="7fe94-154">`Compress-Archive`**Path** 매개 변수를 사용 하 여 `C:\Reference` 스타 별 **점 별** () 와일드 카드를 사용 하 여 루트 디렉터리를 지정 합니다 `*.*` .</span><span class="sxs-lookup"><span data-stu-id="7fe94-154">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference` with a **star-dot-star** (`*.*`) wildcard.</span></span> <span data-ttu-id="7fe94-155">**DestinationPath** 매개 변수는 보관 파일의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-155">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="7fe94-156">`Draft.zip`보관 파일에는 `Reference` 루트 디렉터리의 파일만 포함 되 고 루트 디렉터리는 제외 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-156">The `Draft.zip` archive only contains the `Reference` root directory's files and the root directory is excluded.</span></span>

### <span data-ttu-id="7fe94-157">예제 6: 파이프라인을 사용 하 여 파일 보관</span><span class="sxs-lookup"><span data-stu-id="7fe94-157">Example 6: Use the pipeline to archive files</span></span>

<span data-ttu-id="7fe94-158">이 예제에서는 파일을 파이프라인으로 전송 하 여 보관 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-158">This example sends files down the pipeline to create an archive.</span></span> <span data-ttu-id="7fe94-159">**경로** 에 파일 이름만 지정 되므로 보관 파일에 디렉터리 구조가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-159">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
Get-ChildItem -Path C:\Reference\Afile.txt, C:\Reference\Images\Bfile.txt |
  Compress-Archive -DestinationPath C:\Archives\PipelineFiles.zip
```

<span data-ttu-id="7fe94-160">`Get-ChildItem`**Path** 매개 변수를 사용 하 여 다른 디렉터리에서 두 개의 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-160">`Get-ChildItem` uses the **Path** parameter to specify two files from different directories.</span></span> <span data-ttu-id="7fe94-161">각 파일은 **FileInfo** 개체로 표시 되며 파이프라인에서로 전송 됩니다 `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="7fe94-161">Each file is represented by a **FileInfo** object and is sent down the pipeline to `Compress-Archive`.</span></span>
<span data-ttu-id="7fe94-162">지정 된 두 파일은에 보관 되어 `PipelineFiles.zip` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-162">The two specified files are archived in `PipelineFiles.zip`.</span></span>

### <span data-ttu-id="7fe94-163">예 7: 파이프라인을 사용 하 여 디렉터리 보관</span><span class="sxs-lookup"><span data-stu-id="7fe94-163">Example 7: Use the pipeline to archive a directory</span></span>

<span data-ttu-id="7fe94-164">이 예에서는 파이프라인에서 디렉터리를 전송 하 여 보관 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-164">This example sends a directory down the pipeline to create an archive.</span></span> <span data-ttu-id="7fe94-165">파일은 **system.io.directoryinfo** 개체로 서 **FileInfo** 개체와 디렉터리로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-165">Files are sent as **FileInfo** objects and directories as **DirectoryInfo** objects.</span></span> <span data-ttu-id="7fe94-166">보관 디렉터리 구조는 루트 디렉터리를 포함 하지 않지만 해당 파일 및 하위 디렉터리는 보관 파일에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-166">The archive's directory structure doesn't include the root directory, but its files and subdirectories are included in the archive.</span></span>

```powershell
Get-ChildItem -Path C:\LogFiles | Compress-Archive -DestinationPath C:\Archives\PipelineDir.zip
```

<span data-ttu-id="7fe94-167">`Get-ChildItem`**Path** 매개 변수를 사용 하 여 `C:\LogFiles` 루트 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-167">`Get-ChildItem` uses the **Path** parameter to specify the `C:\LogFiles` root directory.</span></span> <span data-ttu-id="7fe94-168">각 **FileInfo** 및 **system.io.directoryinfo** 개체는 파이프라인으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-168">Each **FileInfo** and **DirectoryInfo** object is sent down the pipeline.</span></span>

<span data-ttu-id="7fe94-169">`Compress-Archive` 각 개체를 `PipelineDir.zip` 보관 파일에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-169">`Compress-Archive` adds each object to the `PipelineDir.zip` archive.</span></span> <span data-ttu-id="7fe94-170">파이프라인 개체가 매개 변수 위치 0으로 수신 되기 때문에 **Path** 매개 변수를 지정 하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-170">The **Path** parameter isn't specified because the pipeline objects are received into parameter position 0.</span></span>

### <span data-ttu-id="7fe94-171">예 8: 재귀가 보관에 영향을 줄 수 있는 방법</span><span class="sxs-lookup"><span data-stu-id="7fe94-171">Example 8: How recursion can affect archives</span></span>

<span data-ttu-id="7fe94-172">이 예제에서는 재귀가 보관 파일의 파일을 중복 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-172">This example shows how recursion can duplicate files in your archive.</span></span> <span data-ttu-id="7fe94-173">예를 들어를 `Get-ChildItem` **재귀** 매개 변수와 함께 사용 하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-173">For example, if you use `Get-ChildItem` with the **Recurse** parameter.</span></span> <span data-ttu-id="7fe94-174">재귀 프로세스에서 각 **FileInfo** 및 **system.io.directoryinfo** 개체는 파이프라인으로 전송 되어 보관에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-174">As recursion processes, each **FileInfo** and **DirectoryInfo** object is sent down the pipeline and added to the archive.</span></span>

```powershell
Get-ChildItem -Path C:\TestLog -Recurse |
  Compress-Archive -DestinationPath C:\Archives\PipelineRecurse.zip
```

<span data-ttu-id="7fe94-175">`C:\TestLog`디렉터리에 파일이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-175">The `C:\TestLog` directory doesn't contain any files.</span></span> <span data-ttu-id="7fe94-176">파일이 포함 된 라는 하위 디렉터리를 포함 `testsub` `testlog.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-176">It does contain a subdirectory named `testsub` that contains the `testlog.txt` file.</span></span>

<span data-ttu-id="7fe94-177">`Get-ChildItem`**Path** 매개 변수를 사용 하 여 루트 디렉터리를 지정 `C:\TestLog` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-177">`Get-ChildItem` uses the **Path** parameter to specify the root directory, `C:\TestLog`.</span></span> <span data-ttu-id="7fe94-178">**재귀** 매개 변수는 파일 및 디렉터리를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-178">The **Recurse** parameter processes the files and directories.</span></span> <span data-ttu-id="7fe94-179">및 FileInfo 개체에 대해 **system.io.directoryinfo** 개체가 생성 됩니다 `testsub`  `testlog.txt` .</span><span class="sxs-lookup"><span data-stu-id="7fe94-179">A **DirectoryInfo** object is created for `testsub` and a **FileInfo** object `testlog.txt`.</span></span>

<span data-ttu-id="7fe94-180">각 개체는 파이프라인에서로 전송 됩니다 `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="7fe94-180">Each object is sent down the pipeline to `Compress-Archive`.</span></span> <span data-ttu-id="7fe94-181">**DestinationPath** 는 보관 파일의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-181">The **DestinationPath** specifies the location for the archive file.</span></span> <span data-ttu-id="7fe94-182">파이프라인 개체가 매개 변수 위치 0으로 수신 되기 때문에 **Path** 매개 변수를 지정 하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-182">The **Path** parameter isn't specified because the pipeline objects are received into parameter position 0.</span></span>

<span data-ttu-id="7fe94-183">다음 요약에서는 `PipelineRecurse.zip` 중복 파일을 포함 하는 보관 파일의 내용에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-183">The following summary describes the `PipelineRecurse.zip` archive's contents that contains a duplicate file:</span></span>

- <span data-ttu-id="7fe94-184">**System.io.directoryinfo** 개체는 디렉터리를 만들고 `testsub` `testlog.txt` 원래 디렉터리 구조를 반영 하는 파일을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-184">The **DirectoryInfo** object creates the `testsub` directory and contains the `testlog.txt` file, which reflects the original directory structure.</span></span>
- <span data-ttu-id="7fe94-185">**FileInfo** 개체는 `testlog.txt` 아카이브의 루트에 중복을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-185">The **FileInfo** object creates a duplicate `testlog.txt` in the archive's root.</span></span> <span data-ttu-id="7fe94-186">재귀가 파일 개체를로 보내기 때문에 중복 된 파일이 생성 됩니다 `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="7fe94-186">The duplicate file is created because recursion sent a file object to `Compress-Archive`.</span></span> <span data-ttu-id="7fe94-187">파이프라인으로 전송 된 각 개체가 보관에 추가 되기 때문에이 동작이 예상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-187">This behavior is expected because each object sent down the pipeline is added to the archive.</span></span>

### <span data-ttu-id="7fe94-188">예 9: 기존 보관 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="7fe94-188">Example 9: Update an existing archive file</span></span>

<span data-ttu-id="7fe94-189">이 예에서는 디렉터리에서 기존 보관 파일인 `Draft.Zip` 를 업데이트 `C:\Archives` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-189">This example updates an existing archive file, `Draft.Zip`, in the `C:\Archives` directory.</span></span> <span data-ttu-id="7fe94-190">이 예에서 기존 보관 파일에는 루트 디렉터리와 해당 파일 및 하위 디렉터리가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-190">In this example, the existing archive file contains the root directory, and its files and subdirectories.</span></span>

```powershell
Compress-Archive -Path C:\Reference -Update -DestinationPath C:\Archives\Draft.Zip
```

<span data-ttu-id="7fe94-191">명령은 `Draft.Zip` `C:\Reference` 디렉터리와 해당 하위 디렉터리에 있는 기존 파일의 최신 버전으로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-191">The command updates `Draft.Zip` with newer versions of existing files in the `C:\Reference` directory and its subdirectories.</span></span> <span data-ttu-id="7fe94-192">또는 해당 하위 디렉터리에 추가 된 새 파일 `C:\Reference` 은 업데이트 된 보관 파일에 포함 됩니다 `Draft.Zip` .</span><span class="sxs-lookup"><span data-stu-id="7fe94-192">And, new files that were added to `C:\Reference` or its subdirectories are included in the updated `Draft.Zip` archive.</span></span>

## <span data-ttu-id="7fe94-193">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7fe94-193">PARAMETERS</span></span>

### <span data-ttu-id="7fe94-194">-CompressionLevel</span><span class="sxs-lookup"><span data-stu-id="7fe94-194">-CompressionLevel</span></span>

<span data-ttu-id="7fe94-195">보관 파일을 만들 때 적용할 압축 크기를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-195">Specifies how much compression to apply when you're creating the archive file.</span></span> <span data-ttu-id="7fe94-196">더 빠른 압축을 사용 하면 파일을 만드는 데 시간이 더 소요 되지만 파일 크기가 커질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-196">Faster compression requires less time to create the file, but can result in larger file sizes.</span></span>

<span data-ttu-id="7fe94-197">이 매개 변수를 지정 하지 않으면 명령에서 기본값인 **최적** 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-197">If this parameter isn't specified, the command uses the default value, **Optimal**.</span></span>

<span data-ttu-id="7fe94-198">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-198">The following are the acceptable values for this parameter:</span></span>

- <span data-ttu-id="7fe94-199">**가장 빠름**.</span><span class="sxs-lookup"><span data-stu-id="7fe94-199">**Fastest**.</span></span> <span data-ttu-id="7fe94-200">가장 빠른 압축 방법을 사용 하 여 처리 시간을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-200">Use the fastest compression method available to reduce processing time.</span></span> <span data-ttu-id="7fe94-201">더 빠른 압축으로 인해 파일 크기가 커질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-201">Faster compression can result in larger file sizes.</span></span>
- <span data-ttu-id="7fe94-202">**Nocompression**.</span><span class="sxs-lookup"><span data-stu-id="7fe94-202">**NoCompression**.</span></span> <span data-ttu-id="7fe94-203">원본 파일을 압축 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-203">Doesn't compress the source files.</span></span>
- <span data-ttu-id="7fe94-204">**최적**.</span><span class="sxs-lookup"><span data-stu-id="7fe94-204">**Optimal**.</span></span> <span data-ttu-id="7fe94-205">처리 시간은 파일 크기에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-205">Processing time is dependent on file size.</span></span>

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

### <span data-ttu-id="7fe94-206">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7fe94-206">-Confirm</span></span>

<span data-ttu-id="7fe94-207">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-207">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7fe94-208">-DestinationPath</span><span class="sxs-lookup"><span data-stu-id="7fe94-208">-DestinationPath</span></span>

<span data-ttu-id="7fe94-209">이 매개 변수는 필수 이며 보관 출력 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-209">This parameter is required and specifies the path to the archive output file.</span></span> <span data-ttu-id="7fe94-210">**DestinationPath** 에는 압축 된 파일의 이름, 압축 된 파일에 대 한 절대 경로 또는 상대 경로를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-210">The **DestinationPath** should include the name of the zipped file, and either the absolute or relative path to the zipped file.</span></span>

<span data-ttu-id="7fe94-211">**DestinationPath** 의 파일 이름에 파일 이름 확장명이 없는 경우 `.zip` cmdlet은 `.zip` 파일 이름 확장명을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-211">If the file name in **DestinationPath** doesn't have a `.zip` file name extension, the cmdlet adds the `.zip` file name extension.</span></span>

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

### <span data-ttu-id="7fe94-212">-Force</span><span class="sxs-lookup"><span data-stu-id="7fe94-212">-Force</span></span>

<span data-ttu-id="7fe94-213">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-213">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="7fe94-214">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7fe94-214">-LiteralPath</span></span>

<span data-ttu-id="7fe94-215">아카이브 압축 파일에 추가 하려는 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-215">Specifies the path or paths to the files that you want to add to the archive zipped file.</span></span> <span data-ttu-id="7fe94-216">**Path** 매개 변수와 달리 **LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-216">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="7fe94-217">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-217">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="7fe94-218">경로에 이스케이프 문자가 포함 된 경우 각 이스케이프 문자를 작은따옴표로 묶어 PowerShell에서 문자를 이스케이프 시퀀스로 해석 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-218">If the path includes escape characters, enclose each escape character in single quotation marks, to instruct PowerShell not to interpret any characters as escape sequences.</span></span>
<span data-ttu-id="7fe94-219">여러 경로를 지정 하 고 출력 압축 파일의 여러 위치에 파일을 포함 하려면 쉼표를 사용 하 여 경로를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-219">To specify multiple paths, and include files in multiple locations in your output zipped file, use commas to separate the paths.</span></span>

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

### <span data-ttu-id="7fe94-220">-PassThru</span><span class="sxs-lookup"><span data-stu-id="7fe94-220">-PassThru</span></span>

<span data-ttu-id="7fe94-221">Cmdlet이 생성 된 보관 파일을 나타내는 파일 개체를 출력 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-221">Causes the cmdlet to output a file object representing the archive file created.</span></span>

<span data-ttu-id="7fe94-222">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-222">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="7fe94-223">-Path</span><span class="sxs-lookup"><span data-stu-id="7fe94-223">-Path</span></span>

<span data-ttu-id="7fe94-224">아카이브 압축 파일에 추가 하려는 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-224">Specifies the path or paths to the files that you want to add to the archive zipped file.</span></span> <span data-ttu-id="7fe94-225">여러 경로를 지정 하 고 여러 위치에 파일을 포함 하려면 쉼표를 사용 하 여 경로를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-225">To specify multiple paths, and include files in multiple locations, use commas to separate the paths.</span></span>

<span data-ttu-id="7fe94-226">이 매개 변수는 와일드 카드 문자를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-226">This parameter accepts wildcard characters.</span></span> <span data-ttu-id="7fe94-227">와일드 카드 문자를 사용 하 여 디렉터리의 모든 파일을 보관 파일에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-227">Wildcard characters allow you to add all files in a directory to your archive file.</span></span>

<span data-ttu-id="7fe94-228">루트 디렉터리와 함께 와일드 카드를 사용 하면 보관 파일의 내용에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-228">Using wildcards with a root directory affects the archive's contents:</span></span>

- <span data-ttu-id="7fe94-229">루트 디렉터리와 모든 파일 및 하위 디렉터리를 **포함** 하는 보관 파일을 만들려면 **경로** 에 와일드 카드 없이 루트 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-229">To create an archive that **includes** the root directory, and all its files and subdirectories, specify the root directory in the **Path** without wildcards.</span></span> <span data-ttu-id="7fe94-230">예: `-Path C:\Reference`</span><span class="sxs-lookup"><span data-stu-id="7fe94-230">For example: `-Path C:\Reference`</span></span>
- <span data-ttu-id="7fe94-231">루트 디렉터리를 **제외** 하 고 모든 파일 및 하위 디렉터리를 zips 보관 파일을 만들려면 별표 ( `*` ) 와일드 카드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-231">To create an archive that **excludes** the root directory, but zips all its files and subdirectories, use the asterisk (`*`) wildcard.</span></span> <span data-ttu-id="7fe94-232">예: `-Path C:\Reference\*`</span><span class="sxs-lookup"><span data-stu-id="7fe94-232">For example: `-Path C:\Reference\*`</span></span>
- <span data-ttu-id="7fe94-233">루트 디렉터리의 파일만 zips 보관 파일을 만들려면 **star-점선** ( `*.*` ) 와일드 카드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-233">To create an archive that only zips the files in the root directory, use the **star-dot-star** (`*.*`) wildcard.</span></span> <span data-ttu-id="7fe94-234">루트의 하위 디렉터리는 보관 파일에 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-234">Subdirectories of the root aren't included in the archive.</span></span> <span data-ttu-id="7fe94-235">예: `-Path C:\Reference\*.*`</span><span class="sxs-lookup"><span data-stu-id="7fe94-235">For example: `-Path C:\Reference\*.*`</span></span>

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

### <span data-ttu-id="7fe94-236">-업데이트</span><span class="sxs-lookup"><span data-stu-id="7fe94-236">-Update</span></span>

<span data-ttu-id="7fe94-237">보관의 이전 파일 버전을 이름이 같은 최신 파일 버전으로 바꿔 지정 된 보관 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-237">Updates the specified archive by replacing older file versions in the archive with newer file versions that have the same names.</span></span> <span data-ttu-id="7fe94-238">이 매개 변수를 추가 하 여 기존 보관 파일에 파일을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-238">You can also add this parameter to add files to an existing archive.</span></span>

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

### <span data-ttu-id="7fe94-239">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7fe94-239">-WhatIf</span></span>

<span data-ttu-id="7fe94-240">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-240">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="7fe94-241">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-241">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="7fe94-242">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7fe94-242">CommonParameters</span></span>

<span data-ttu-id="7fe94-243">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7fe94-243">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7fe94-244">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7fe94-244">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7fe94-245">입력</span><span class="sxs-lookup"><span data-stu-id="7fe94-245">INPUTS</span></span>

### <span data-ttu-id="7fe94-246">System.String</span><span class="sxs-lookup"><span data-stu-id="7fe94-246">System.String</span></span>

<span data-ttu-id="7fe94-247">하나 이상의 파일에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-247">You can pipe a string that contains a path to one or more files.</span></span>

## <span data-ttu-id="7fe94-248">출력</span><span class="sxs-lookup"><span data-stu-id="7fe94-248">OUTPUTS</span></span>

### <span data-ttu-id="7fe94-249">System.object</span><span class="sxs-lookup"><span data-stu-id="7fe94-249">System.IO.FileInfo</span></span>

<span data-ttu-id="7fe94-250">이 cmdlet은 **PassThru** 매개 변수를 사용 하는 경우에만 **FileInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-250">The cmdlet only returns a **FileInfo** object when you use the **PassThru** parameter.</span></span>

## <span data-ttu-id="7fe94-251">참고</span><span class="sxs-lookup"><span data-stu-id="7fe94-251">NOTES</span></span>

<span data-ttu-id="7fe94-252">재귀를 사용 하 여 개체를 아래로 보내면 보관 파일의 파일이 중복 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-252">Using recursion and sending objects down the pipeline can duplicate files in your archive.</span></span> <span data-ttu-id="7fe94-253">예를 들어를 `Get-ChildItem` **재귀** 매개 변수와 함께 사용 하는 경우 파이프라인으로 전송 된 각 **FileInfo** 및 **system.io.directoryinfo** 개체가 보관에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-253">For example, if you use `Get-ChildItem` with the **Recurse** parameter, each **FileInfo** and **DirectoryInfo** object that's sent down the pipeline is added to the archive.</span></span>

<span data-ttu-id="7fe94-254">[ZIP 파일 사양은](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ASCII가 아닌 문자를 포함 하는 파일 이름을 인코딩 하는 표준 방법을 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-254">The [ZIP file specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) does not specify a standard way of encoding filenames that contain non-ASCII characters.</span></span> <span data-ttu-id="7fe94-255">`Compress-Archive`Cmdlet은 utf-8 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-255">The `Compress-Archive` cmdlet uses UTF-8 encoding.</span></span> <span data-ttu-id="7fe94-256">다른 ZIP 보관 도구는 다른 인코딩 체계를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-256">Other ZIP archive tools may use a different encoding scheme.</span></span> <span data-ttu-id="7fe94-257">UTF-8 인코딩을 사용 하 여 저장 되지 않은 파일 이름을 가진 파일을 추출할 때는 `Expand-Archive` 보관 파일에 있는 원시 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-257">When extracting files with filenames not stored using UTF-8 encoding, `Expand-Archive` uses the raw value found in the archive.</span></span> <span data-ttu-id="7fe94-258">이로 인해 보관 파일에 저장 된 원본 파일 이름과 다른 파일 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe94-258">This can result in a filename that is different than the source filename stored in the archive.</span></span>

## <span data-ttu-id="7fe94-259">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7fe94-259">RELATED LINKS</span></span>

[<span data-ttu-id="7fe94-260">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="7fe94-260">Expand-Archive</span></span>](Expand-Archive.md)

[<span data-ttu-id="7fe94-261">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="7fe94-261">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

