---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: d7942abff2974064c52a8a9ac086a280959b3a63
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/27/2021
ms.locfileid: "99600420"
---
# <span data-ttu-id="bfd70-102">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="bfd70-102">Import-PowerShellDataFile</span></span>

## <span data-ttu-id="bfd70-103">개요</span><span class="sxs-lookup"><span data-stu-id="bfd70-103">SYNOPSIS</span></span>
<span data-ttu-id="bfd70-104">`.PSD1`파일의 내용을 호출 하지 않고 파일에서 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bfd70-104">Imports values from a `.PSD1` file without invoking its contents.</span></span>

## <span data-ttu-id="bfd70-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bfd70-105">SYNTAX</span></span>

### <span data-ttu-id="bfd70-106">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="bfd70-106">ByPath (Default)</span></span>

```
Import-PowerShellDataFile [-Path] <String[]> [-SkipLimitCheck] [<CommonParameters>]
```

### <span data-ttu-id="bfd70-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="bfd70-107">ByLiteralPath</span></span>

```
Import-PowerShellDataFile [-LiteralPath] <String[]> [-SkipLimitCheck] [<CommonParameters>]
```

## <span data-ttu-id="bfd70-108">설명</span><span class="sxs-lookup"><span data-stu-id="bfd70-108">DESCRIPTION</span></span>

<span data-ttu-id="bfd70-109">`Import-PowerShellDataFile`Cmdlet은 파일에 정의 된 해시 테이블에서 키-값 쌍을 안전 하 게 가져옵니다 `.PSD1` .</span><span class="sxs-lookup"><span data-stu-id="bfd70-109">The `Import-PowerShellDataFile` cmdlet safely imports key-value pairs from hashtables defined in a `.PSD1` file.</span></span> <span data-ttu-id="bfd70-110">파일의 내용에 따라를 사용 하 여 값을 가져올 수 있습니다 `Invoke-Expression` .</span><span class="sxs-lookup"><span data-stu-id="bfd70-110">The values could be imported using `Invoke-Expression` on the contents of the file.</span></span>
<span data-ttu-id="bfd70-111">그러나는 `Invoke-Expression` 파일에 포함 된 모든 코드를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd70-111">However, `Invoke-Expression` runs any code contained in the file.</span></span> <span data-ttu-id="bfd70-112">이렇게 하면 원치 않는 결과가 생성 되거나 안전 하지 않은 코드가 실행 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd70-112">This could produce unwanted results or execute unsafe code.</span></span> <span data-ttu-id="bfd70-113">`Import-PowerShellDataFile` 코드를 호출 하지 않고 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bfd70-113">`Import-PowerShellDataFile` imports the data without invoking the code.</span></span> <span data-ttu-id="bfd70-114">기본적으로 500 키 제한이 있지만 **SkipLimitCheck** 스위치를 사용 하 여 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd70-114">By default there is a 500 key limit but can be bypassed with the **SkipLimitCheck** switch.</span></span>

## <span data-ttu-id="bfd70-115">예제</span><span class="sxs-lookup"><span data-stu-id="bfd70-115">EXAMPLES</span></span>

### <span data-ttu-id="bfd70-116">예제 1: PSD1에서 값 검색</span><span class="sxs-lookup"><span data-stu-id="bfd70-116">Example 1: Retrieve values from PSD1</span></span>

<span data-ttu-id="bfd70-117">이 예에서는 파일 내에 보관 된 해시 테이블에 저장 된 키-값 쌍을 검색 합니다 `Configuration.psd1` .</span><span class="sxs-lookup"><span data-stu-id="bfd70-117">This example retrieves the key-value pairs stored in the hashtable kept inside the `Configuration.psd1` file.</span></span> <span data-ttu-id="bfd70-118">`Get-Content` 는 파일의 내용을 표시 하는 데 사용 됩니다 `Configuration.psd1` .</span><span class="sxs-lookup"><span data-stu-id="bfd70-118">`Get-Content` is used to show the contents of the `Configuration.psd1` file.</span></span>

```powershell
Get-Content .\Configuration.psd1
$config = Import-PowerShellDataFile .\Configuration.psd1
$config.AllNodes
```

```Output
@{
    AllNodes = @(
        @{
            NodeName = 'DSC-01'
        }
        @{
            NodeName = 'DSC-02'
        }
    )
}

Name                           Value
----                           -----
NodeName                       DSC-01
NodeName                       DSC-02
```

## <span data-ttu-id="bfd70-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bfd70-119">PARAMETERS</span></span>

### <span data-ttu-id="bfd70-120">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="bfd70-120">-LiteralPath</span></span>

<span data-ttu-id="bfd70-121">가져올 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="bfd70-121">The path to the file being imported.</span></span> <span data-ttu-id="bfd70-122">경로의 모든 문자는 리터럴 값으로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd70-122">All characters in the path are treated as literal values.</span></span>
<span data-ttu-id="bfd70-123">와일드 카드 문자는 처리 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd70-123">Wildcard characters are not processed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bfd70-124">-Path</span><span class="sxs-lookup"><span data-stu-id="bfd70-124">-Path</span></span>

<span data-ttu-id="bfd70-125">가져올 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="bfd70-125">The path to the file being imported.</span></span> <span data-ttu-id="bfd70-126">와일드 카드를 사용할 수 있지만 첫 번째 일치 하는 파일만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bfd70-126">Wildcards are allowed but only the first matching file is imported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bfd70-127">-SkipLimitCheck</span><span class="sxs-lookup"><span data-stu-id="bfd70-127">-SkipLimitCheck</span></span>

<span data-ttu-id="bfd70-128">기본적으로 `Import-PowerShellDataFile` 는 파일에서 500 키만 가져옵니다 `.psd1` .</span><span class="sxs-lookup"><span data-stu-id="bfd70-128">By default `Import-PowerShellDataFile` imports only 500 keys from a `.psd1` file.</span></span> <span data-ttu-id="bfd70-129">**SkipLimitCheck** 를 사용 하 여 500 개 이상의 키를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bfd70-129">Use **SkipLimitCheck** to import more than 500 keys.</span></span>

```yaml
Type: Switch
Parameter Sets: All
Aliases:

Required: False
Position: 0
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bfd70-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bfd70-130">CommonParameters</span></span>

<span data-ttu-id="bfd70-131">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bfd70-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bfd70-132">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bfd70-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="bfd70-133">입력</span><span class="sxs-lookup"><span data-stu-id="bfd70-133">INPUTS</span></span>

## <span data-ttu-id="bfd70-134">출력</span><span class="sxs-lookup"><span data-stu-id="bfd70-134">OUTPUTS</span></span>

### <span data-ttu-id="bfd70-135">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="bfd70-135">System.Collections.Hashtable</span></span>

## <span data-ttu-id="bfd70-136">참고</span><span class="sxs-lookup"><span data-stu-id="bfd70-136">NOTES</span></span>

## <span data-ttu-id="bfd70-137">관련 링크</span><span class="sxs-lookup"><span data-stu-id="bfd70-137">RELATED LINKS</span></span>

[<span data-ttu-id="bfd70-138">Invoke-Expression</span><span class="sxs-lookup"><span data-stu-id="bfd70-138">Invoke-Expression</span></span>](Invoke-Expression.md)

[<span data-ttu-id="bfd70-139">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="bfd70-139">Import-LocalizedData</span></span>](Import-LocalizedData.md)