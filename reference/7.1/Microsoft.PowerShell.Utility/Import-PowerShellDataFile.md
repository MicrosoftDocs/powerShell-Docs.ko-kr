---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: f83718f56a3c01ca59fcda697201ff4a3598b54a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212962"
---
# <span data-ttu-id="42d6d-103">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="42d6d-103">Import-PowerShellDataFile</span></span>

## <span data-ttu-id="42d6d-104">개요</span><span class="sxs-lookup"><span data-stu-id="42d6d-104">SYNOPSIS</span></span>
<span data-ttu-id="42d6d-105">`.PSD1`파일의 내용을 호출 하지 않고 파일에서 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="42d6d-105">Imports values from a `.PSD1` file without invoking its contents.</span></span>

## <span data-ttu-id="42d6d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="42d6d-106">SYNTAX</span></span>

### <span data-ttu-id="42d6d-107">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="42d6d-107">ByPath (Default)</span></span>

```
Import-PowerShellDataFile [-Path] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="42d6d-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="42d6d-108">ByLiteralPath</span></span>

```
Import-PowerShellDataFile [-LiteralPath] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="42d6d-109">설명</span><span class="sxs-lookup"><span data-stu-id="42d6d-109">DESCRIPTION</span></span>

<span data-ttu-id="42d6d-110">`Import-PowerShellDataFile`Cmdlet은 파일에 정의 된 해시 테이블에서 키-값 쌍을 안전 하 게 가져옵니다 `.PSD1` .</span><span class="sxs-lookup"><span data-stu-id="42d6d-110">The `Import-PowerShellDataFile` cmdlet safely imports key-value pairs from hashtables defined in a `.PSD1` file.</span></span> <span data-ttu-id="42d6d-111">파일의 내용에 따라를 사용 하 여 값을 가져올 수 있습니다 `Invoke-Expression` .</span><span class="sxs-lookup"><span data-stu-id="42d6d-111">The values could be imported using `Invoke-Expression` on the contents of the file.</span></span>
<span data-ttu-id="42d6d-112">그러나는 `Invoke-Expression` 파일에 포함 된 모든 코드를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="42d6d-112">However, `Invoke-Expression` runs any code contained in the file.</span></span> <span data-ttu-id="42d6d-113">이렇게 하면 원치 않는 결과가 생성 되거나 안전 하지 않은 코드가 실행 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42d6d-113">This could produce unwanted results or execute unsafe code.</span></span> <span data-ttu-id="42d6d-114">`Import-PowerShellDataFile` 코드를 호출 하지 않고 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="42d6d-114">`Import-PowerShellDataFile` imports the data without invoking the code.</span></span>

## <span data-ttu-id="42d6d-115">예제</span><span class="sxs-lookup"><span data-stu-id="42d6d-115">EXAMPLES</span></span>

### <span data-ttu-id="42d6d-116">예제 1: PSD1에서 값 검색</span><span class="sxs-lookup"><span data-stu-id="42d6d-116">Example 1: Retrieve values from PSD1</span></span>

<span data-ttu-id="42d6d-117">이 예에서는 파일 내에 보관 된 해시 테이블에 저장 된 키-값 쌍을 검색 합니다 `Configuration.psd1` .</span><span class="sxs-lookup"><span data-stu-id="42d6d-117">This example retrieves the key-value pairs stored in the hashtable kept inside the `Configuration.psd1` file.</span></span> <span data-ttu-id="42d6d-118">`Get-Content` 는 파일의 내용을 표시 하는 데 사용 됩니다 `Configuration.psd1` .</span><span class="sxs-lookup"><span data-stu-id="42d6d-118">`Get-Content` is used to show the contents of the `Configuration.psd1` file.</span></span>

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

## <span data-ttu-id="42d6d-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="42d6d-119">PARAMETERS</span></span>

### <span data-ttu-id="42d6d-120">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="42d6d-120">-LiteralPath</span></span>

<span data-ttu-id="42d6d-121">가져올 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="42d6d-121">The path to the file being imported.</span></span> <span data-ttu-id="42d6d-122">경로의 모든 문자는 리터럴 값으로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42d6d-122">All characters in the path are treated as literal values.</span></span>
<span data-ttu-id="42d6d-123">와일드 카드 문자는 처리 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="42d6d-123">Wildcard characters are not processed.</span></span>

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

### <span data-ttu-id="42d6d-124">-Path</span><span class="sxs-lookup"><span data-stu-id="42d6d-124">-Path</span></span>

<span data-ttu-id="42d6d-125">가져올 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="42d6d-125">The path to the file being imported.</span></span> <span data-ttu-id="42d6d-126">와일드 카드를 사용할 수 있지만 첫 번째 일치 하는 파일만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="42d6d-126">Wildcards are allowed but only the first matching file is imported.</span></span>

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

### <span data-ttu-id="42d6d-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="42d6d-127">CommonParameters</span></span>

<span data-ttu-id="42d6d-128">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="42d6d-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="42d6d-129">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42d6d-129">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="42d6d-130">입력</span><span class="sxs-lookup"><span data-stu-id="42d6d-130">INPUTS</span></span>

## <span data-ttu-id="42d6d-131">출력</span><span class="sxs-lookup"><span data-stu-id="42d6d-131">OUTPUTS</span></span>

### <span data-ttu-id="42d6d-132">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="42d6d-132">System.Collections.Hashtable</span></span>

## <span data-ttu-id="42d6d-133">참고</span><span class="sxs-lookup"><span data-stu-id="42d6d-133">NOTES</span></span>

## <span data-ttu-id="42d6d-134">관련 링크</span><span class="sxs-lookup"><span data-stu-id="42d6d-134">RELATED LINKS</span></span>

[<span data-ttu-id="42d6d-135">Invoke-Expression</span><span class="sxs-lookup"><span data-stu-id="42d6d-135">Invoke-Expression</span></span>](Invoke-Expression.md)

[<span data-ttu-id="42d6d-136">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="42d6d-136">Import-LocalizedData</span></span>](Import-LocalizedData.md)

