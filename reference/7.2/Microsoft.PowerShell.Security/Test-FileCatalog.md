---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/test-filecatalog?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-FileCatalog
ms.openlocfilehash: 0a990b1c0c46cda06c5239a4c8fde55b29296376
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "99603268"
---
# <span data-ttu-id="a9e78-102">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="a9e78-102">Test-FileCatalog</span></span>

## <span data-ttu-id="a9e78-103">개요</span><span class="sxs-lookup"><span data-stu-id="a9e78-103">SYNOPSIS</span></span>
<span data-ttu-id="a9e78-104">`Test-FileCatalog` 카탈로그 파일 (.cat)에 포함 된 해시가 실제 파일의 해시와 일치 하는지 유효성을 검사 하기 위해 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-104">`Test-FileCatalog` validates whether the hashes contained in a catalog file (.cat) matches the hashes of the actual files in order to validate their authenticity.</span></span>

<span data-ttu-id="a9e78-105">이 cmdlet은 Windows 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-105">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="a9e78-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a9e78-106">SYNTAX</span></span>

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>] [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a9e78-107">설명</span><span class="sxs-lookup"><span data-stu-id="a9e78-107">DESCRIPTION</span></span>

<span data-ttu-id="a9e78-108">`Test-FileCatalog` 카탈로그 파일 (.cat)의 파일 해시를 디스크에 있는 실제 파일의 해시와 비교 하 여 파일 신뢰성의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-108">`Test-FileCatalog` validates the authenticity of files by comparing the file hashes of a catalog file (.cat) with the hashes of actual files on disk.</span></span> <span data-ttu-id="a9e78-109">불일치를 발견 하면 ValidationFailed로 상태를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-109">If it detects any mismatches, it returns the status as ValidationFailed.</span></span> <span data-ttu-id="a9e78-110">사용자는 -Detailed 매개 변수를 사용하여 이 모든 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-110">Users can retrieve all this information by using the -Detailed parameter.</span></span> <span data-ttu-id="a9e78-111">또한이 `Get-AuthenticodeSignature` cmdlet은 카탈로그 파일에서 cmdlet을 호출 하는 것과 동일한 Signature 속성에 카탈로그의 서명 상태를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-111">It also displays signing status of catalog in Signature property which is equivalent to calling `Get-AuthenticodeSignature` cmdlet on the catalog file.</span></span> <span data-ttu-id="a9e78-112">사용자는 -FilesToSkip 매개 변수를 사용하여 유효성 검사 시 파일을 건너뛸 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-112">Users can also skip any file during validation by using the -FilesToSkip parameter.</span></span>

<span data-ttu-id="a9e78-113">이 cmdlet은 Windows 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-113">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="a9e78-114">예제</span><span class="sxs-lookup"><span data-stu-id="a9e78-114">EXAMPLES</span></span>

### <span data-ttu-id="a9e78-115">예제 1: 파일 카탈로그 만들기 및 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="a9e78-115">Example 1: Create and validate a file catalog</span></span>

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0

Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Valid
```

### <span data-ttu-id="a9e78-116">예제 2: 자세한 출력을 사용 하 여 파일 카탈로그 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="a9e78-116">Example 2: Validate a file catalog with detailed output</span></span>

```powershell
Test-FileCatalog -Detailed -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Status        : Valid
HashAlgorithm : SHA256
CatalogItems  : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
PathItems     : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
Signature     : System.Management.Automation.Signature
```

## <span data-ttu-id="a9e78-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a9e78-117">PARAMETERS</span></span>

### <span data-ttu-id="a9e78-118">-CatalogFilePath</span><span class="sxs-lookup"><span data-stu-id="a9e78-118">-CatalogFilePath</span></span>

<span data-ttu-id="a9e78-119">유효성 검사에 사용할 해시가 포함 된 카탈로그 파일 (.cat)의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-119">A path to a catalog file (.cat) that contains the hashes to be used for validation.</span></span>

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

### <span data-ttu-id="a9e78-120">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a9e78-120">-Confirm</span></span>

<span data-ttu-id="a9e78-121">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-121">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a9e78-122">-Detailed</span><span class="sxs-lookup"><span data-stu-id="a9e78-122">-Detailed</span></span>

<span data-ttu-id="a9e78-123">추가 정보를 반환 합니다 `CatalogInformation` .이 개체에는 테스트 한 파일, 예상/실제 해시 및 서명 된 카탈로그 파일의 Authenticode 서명이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-123">Returns more information a more detailed `CatalogInformation` object that contains the files tested, their expected/actual hashes, and an Authenticode signature of the catalog file if it's signed.</span></span>

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

### <span data-ttu-id="a9e78-124">-FilesToSkip</span><span class="sxs-lookup"><span data-stu-id="a9e78-124">-FilesToSkip</span></span>

<span data-ttu-id="a9e78-125">유효성 검사의 일부로 테스트 하면 안 되는 경로 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-125">An array of paths that should not be tested as part of the validation.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9e78-126">-Path</span><span class="sxs-lookup"><span data-stu-id="a9e78-126">-Path</span></span>

<span data-ttu-id="a9e78-127">카탈로그 파일에 대해 유효성을 검사 해야 하는 폴더 또는 파일의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-127">A folder or array of files that should be validated against the catalog file.</span></span>

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

### <span data-ttu-id="a9e78-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a9e78-128">-WhatIf</span></span>

<span data-ttu-id="a9e78-129">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-129">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a9e78-130">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a9e78-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a9e78-131">CommonParameters</span></span>

<span data-ttu-id="a9e78-132">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a9e78-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a9e78-133">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9e78-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a9e78-134">입력</span><span class="sxs-lookup"><span data-stu-id="a9e78-134">INPUTS</span></span>

### <span data-ttu-id="a9e78-135">System.io.directoryinfo [], System.string []</span><span class="sxs-lookup"><span data-stu-id="a9e78-135">System.IO.DirectoryInfo[], System.String[]</span></span>

<span data-ttu-id="a9e78-136">파이프라인은 `DirectoryInfo` 유효성을 검사 해야 하는 파일의 경로를 나타내는 문자열 또는 개체의 배열을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-136">The pipeline accepts an array of strings or `DirectoryInfo` objects that represent paths to the files that need to be validated.</span></span>

## <span data-ttu-id="a9e78-137">출력</span><span class="sxs-lookup"><span data-stu-id="a9e78-137">OUTPUTS</span></span>

### <span data-ttu-id="a9e78-138">CatalogValidationStatus.</span><span class="sxs-lookup"><span data-stu-id="a9e78-138">System.Management.Automation.CatalogValidationStatus</span></span>

<span data-ttu-id="a9e78-139">또는의 값을 포함 하는 기본 반환 형식입니다 `Valid` `ValidationFailed` .</span><span class="sxs-lookup"><span data-stu-id="a9e78-139">The default return type containing a value of either `Valid` or `ValidationFailed`.</span></span>

### <span data-ttu-id="a9e78-140">CatalogInformation.</span><span class="sxs-lookup"><span data-stu-id="a9e78-140">System.Management.Automation.CatalogInformation</span></span>

<span data-ttu-id="a9e78-141">을 사용 하 여 `-Detailed` 유효성 검사를 통과 하거나 포함 하지 않을 수 있는 특정 파일을 분석 하는 데 사용할 수 있는 보다 자세한 개체를 사용 하는 경우, 필요한 해시 및 검색 된 알고리즘과 카탈로그에서 사용 되는 알고리즘입니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-141">A more detailed object returned when using `-Detailed` which can be used to analyze specific files that may or may not have passed validation, which hashes were expected vs. found, and the algorithm used in the catalog.</span></span>

## <span data-ttu-id="a9e78-142">참고</span><span class="sxs-lookup"><span data-stu-id="a9e78-142">NOTES</span></span>

<span data-ttu-id="a9e78-143">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9e78-143">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="a9e78-144">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a9e78-144">RELATED LINKS</span></span>

[<span data-ttu-id="a9e78-145">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="a9e78-145">New-FileCatalog</span></span>](New-FileCatalog.md)

[<span data-ttu-id="a9e78-146">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a9e78-146">PowerShellGet</span></span>](/powershell/module/PowerShellGet)