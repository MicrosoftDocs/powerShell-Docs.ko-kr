---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/new-filecatalog?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-FileCatalog
ms.openlocfilehash: 230f027a021017e948c8c53e5e6d0c092127ad85
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602675"
---
# <span data-ttu-id="46529-102">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="46529-102">New-FileCatalog</span></span>

## <span data-ttu-id="46529-103">개요</span><span class="sxs-lookup"><span data-stu-id="46529-103">SYNOPSIS</span></span>
<span data-ttu-id="46529-104">`New-FileCatalog` 파일의 신뢰성을 확인 하는 데 사용할 수 있는 파일 해시의 카탈로그 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46529-104">`New-FileCatalog` creates a catalog file of file hashes that can be used to validate the authenticity of a file.</span></span>

## <span data-ttu-id="46529-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="46529-105">SYNTAX</span></span>

```
New-FileCatalog [-CatalogVersion <Int32>] [-CatalogFilePath] <String> [[-Path] <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="46529-106">설명</span><span class="sxs-lookup"><span data-stu-id="46529-106">DESCRIPTION</span></span>

<span data-ttu-id="46529-107">`New-FileCatalog` 폴더 및 파일 집합에 대 한 [Windows 카탈로그 파일](/windows-hardware/drivers/install/catalog-files) 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46529-107">`New-FileCatalog` creates a [Windows catalog file](/windows-hardware/drivers/install/catalog-files) for a set of folders and files.</span></span> <span data-ttu-id="46529-108">이 카탈로그 파일에는 제공 된 경로에 있는 모든 파일에 대 한 해시가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46529-108">This catalog file contains hashes for all files in the provided paths.</span></span> <span data-ttu-id="46529-109">사용자는 카탈로그를 만든 시간 이후 폴더가 변경 되었는지 여부를 확인할 수 있도록 해당 파일을 사용 하 여 카탈로그를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46529-109">Users can then distribute the catalog with their files so that users can validate whether any changes have been made to the folders since catalog creation time.</span></span>

<span data-ttu-id="46529-110">카탈로그 버전 1과 2가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="46529-110">Catalog versions 1 and 2 are supported.</span></span> <span data-ttu-id="46529-111">버전 1은 (사용 되지 않음) SHA1 해시 알고리즘을 사용 하 여 파일 해시를 만들고 버전 2는 s h a 1을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="46529-111">Version 1 uses the (deprecated) SHA1 hashing algorithm to create file hashes, and version 2 uses SHA256.</span></span> <span data-ttu-id="46529-112">Windows Server 2008 R2 또는 Windows 7에서는 카탈로그 버전 2가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46529-112">Catalog version 2 is not supported on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="46529-113">Windows 8, Windows Server 2012 및 이후 운영 체제에서는 카탈로그 버전 2를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46529-113">You should use catalog version 2 on Windows 8, Windows Server 2012, and later operating systems.</span></span>

## <span data-ttu-id="46529-114">예제</span><span class="sxs-lookup"><span data-stu-id="46529-114">EXAMPLES</span></span>

### <span data-ttu-id="46529-115">예제 1:에 대 한 파일 카탈로그 만들기 `Microsoft.PowerShell.Utility`</span><span class="sxs-lookup"><span data-stu-id="46529-115">Example 1: Create a file catalog for `Microsoft.PowerShell.Utility`</span></span>

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         11/2/2018 11:58 AM            950 Microsoft.PowerShell.Utility.cat
```

## <span data-ttu-id="46529-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="46529-116">PARAMETERS</span></span>

### <span data-ttu-id="46529-117">-CatalogFilePath</span><span class="sxs-lookup"><span data-stu-id="46529-117">-CatalogFilePath</span></span>

<span data-ttu-id="46529-118">카탈로그 파일 (.cat)을 배치 해야 하는 파일이 나 폴더에 대 한 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="46529-118">A path to a file or folder where the catalog file (.cat) should be placed.</span></span> <span data-ttu-id="46529-119">폴더 경로를 지정 하는 경우 기본 파일 이름이 `catalog.cat` 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46529-119">If a folder path is specified, the default filename `catalog.cat` will be used.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="46529-120">-CatalogVersion</span><span class="sxs-lookup"><span data-stu-id="46529-120">-CatalogVersion</span></span>

<span data-ttu-id="46529-121">`1.0` `2.0` 카탈로그 버전을 지정 하기 위해 또는 가능한 값을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="46529-121">Accepts `1.0` or `2.0` as possible values for specifying the catalog version.</span></span> <span data-ttu-id="46529-122">`1.0` 가능 하면 안전 하지 않은 SHA-1 해시 알고리즘을 사용 하 고 `2.0` 보안 sha-256 알고리즘을 사용 하지만 `1.0` Windows 7 및 Server 2008 r 2에서 유일 하 게 지원 되는 알고리즘을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46529-122">`1.0` should be used avoided whenever possible, as it uses the insecure SHA-1 hash algorithm, while `2.0` uses the secure SHA-256 algorithm However, `1.0` is the only supported algorithm on Windows 7 and Server 2008R2.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46529-123">-Path</span><span class="sxs-lookup"><span data-stu-id="46529-123">-Path</span></span>

<span data-ttu-id="46529-124">카탈로그 파일에 포함 되어야 하는 파일이 나 폴더에 대 한 경로 또는 경로 배열을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="46529-124">Accepts a path or array of paths to files or folders that should be included in the catalog file.</span></span> <span data-ttu-id="46529-125">폴더를 지정 하면 폴더의 모든 파일도 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46529-125">If a folder is specified, all the files in the folder will be included as well.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="46529-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="46529-126">-Confirm</span></span>

<span data-ttu-id="46529-127">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="46529-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="46529-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="46529-128">-WhatIf</span></span>

<span data-ttu-id="46529-129">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="46529-129">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="46529-130">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46529-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="46529-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="46529-131">CommonParameters</span></span>

<span data-ttu-id="46529-132">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="46529-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="46529-133">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46529-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="46529-134">입력</span><span class="sxs-lookup"><span data-stu-id="46529-134">INPUTS</span></span>

### <span data-ttu-id="46529-135">System.String</span><span class="sxs-lookup"><span data-stu-id="46529-135">System.String</span></span>

<span data-ttu-id="46529-136">파이프라인은 카탈로그 파일 이름으로 사용 되는 문자열을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="46529-136">The pipeline takes a string that is used as the catalog filename.</span></span>

## <span data-ttu-id="46529-137">출력</span><span class="sxs-lookup"><span data-stu-id="46529-137">OUTPUTS</span></span>

### <span data-ttu-id="46529-138">System.object</span><span class="sxs-lookup"><span data-stu-id="46529-138">System.IO.FileInfo</span></span>

## <span data-ttu-id="46529-139">참고</span><span class="sxs-lookup"><span data-stu-id="46529-139">NOTES</span></span>

<span data-ttu-id="46529-140">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46529-140">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="46529-141">관련 링크</span><span class="sxs-lookup"><span data-stu-id="46529-141">RELATED LINKS</span></span>

[<span data-ttu-id="46529-142">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="46529-142">Test-FileCatalog</span></span>](Test-FileCatalog.md)

[<span data-ttu-id="46529-143">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="46529-143">PowerShellGet</span></span>](/powerShell/module/powershellget)