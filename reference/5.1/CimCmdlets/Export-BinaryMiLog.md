---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/export-binarymilog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-BinaryMiLog
ms.openlocfilehash: 1d202b7bbda359f859838475eb9f37730506bd1f
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194357"
---
# <span data-ttu-id="a0361-103">Export-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="a0361-103">Export-BinaryMiLog</span></span>

## <span data-ttu-id="a0361-104">개요</span><span class="sxs-lookup"><span data-stu-id="a0361-104">SYNOPSIS</span></span>
<span data-ttu-id="a0361-105">개체 또는 개체의 이진 인코딩된 표현을 만들어 파일에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0361-105">Creates a binary encoded representation of an object or objects and stores it in a file.</span></span>

## <span data-ttu-id="a0361-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a0361-106">SYNTAX</span></span>

```
Export-BinaryMiLog [-InputObject <CimInstance>] [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="a0361-107">설명</span><span class="sxs-lookup"><span data-stu-id="a0361-107">DESCRIPTION</span></span>

<span data-ttu-id="a0361-108">`Export-BinaryMILog`Cmdlet은 개체 또는 개체의 이진 기반 표현을 만들어 파일에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0361-108">The `Export-BinaryMILog` cmdlet creates a binary-based representation of an object or objects and stores it in a file.</span></span> <span data-ttu-id="a0361-109">그런 다음 cmdlet을 사용 하 여 `Import-BinaryMiLog` 해당 파일의 내용을 기반으로 저장 된 개체를 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0361-109">You can then use the `Import-BinaryMiLog` cmdlet to re-create the saved object based on the contents of that file.</span></span>

<span data-ttu-id="a0361-110">이 cmdlet은 `Import-Clixml` `Export-BinaryMILog` 결과 개체를 이진 인코딩 파일에 저장 한다는 점을 제외 하 고와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="a0361-110">This cmdlet is similar to `Import-Clixml`, except that `Export-BinaryMILog` stores the resulting object in a binary encoded file.</span></span>

## <span data-ttu-id="a0361-111">예제</span><span class="sxs-lookup"><span data-stu-id="a0361-111">EXAMPLES</span></span>

### <span data-ttu-id="a0361-112">예제 1-CimInstances의 이진 표현 만들기</span><span class="sxs-lookup"><span data-stu-id="a0361-112">Example 1 - Create a binary representation of CimInstances</span></span>

```powershell
Get-CimInstance Win32_Process | Export-BinaryMiLog -Path "Processes.bmil"
```

<span data-ttu-id="a0361-113">이 명령은 Path 매개 변수로 지정 된 이진 MI 로그 파일에 **CimInstances** 를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a0361-113">This command exports **CimInstances** to a binary MI log file specified by the Path parameter.</span></span> <span data-ttu-id="a0361-114">이 파일을 가져와서 **CimInstances** 를 다시 만드는 방법에 대 한 자세한 내용은 Import-BinaryMiLog의 예제를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a0361-114">See the example for Import-BinaryMiLog to see how to recreate the **CimInstances** by importing this file.</span></span>

## <span data-ttu-id="a0361-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a0361-115">PARAMETERS</span></span>

### <span data-ttu-id="a0361-116">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a0361-116">-InputObject</span></span>

<span data-ttu-id="a0361-117">이 cmdlet에 대한 입력을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a0361-117">Specifies the input to this cmdlet.</span></span> <span data-ttu-id="a0361-118">이 매개 변수를 사용하거나 이 cmdlet에 입력을 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0361-118">You can use this parameter, or you can pipe the input to this cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a0361-119">-Path</span><span class="sxs-lookup"><span data-stu-id="a0361-119">-Path</span></span>

<span data-ttu-id="a0361-120">개체의 이진 표현을 저장할 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0361-120">Specifies the path of the file in which to store the binary representation of the object.</span></span> <span data-ttu-id="a0361-121">**Path** 매개 변수는 와일드 카드 및 상대 경로를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0361-121">The **Path** parameter supports wildcards and relative paths.</span></span> <span data-ttu-id="a0361-122">이 cmdlet은 경로가 둘 이상의 파일로 확인 될 경우 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0361-122">This cmdlet generates an error if the path resolves to more than one file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a0361-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a0361-123">CommonParameters</span></span>

<span data-ttu-id="a0361-124">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a0361-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a0361-125">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0361-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a0361-126">입력</span><span class="sxs-lookup"><span data-stu-id="a0361-126">INPUTS</span></span>

### <span data-ttu-id="a0361-127">Ciminstance 개체로.</span><span class="sxs-lookup"><span data-stu-id="a0361-127">Microsoft.Management.Infrastructure.CimInstance</span></span>

## <span data-ttu-id="a0361-128">출력</span><span class="sxs-lookup"><span data-stu-id="a0361-128">OUTPUTS</span></span>

### <span data-ttu-id="a0361-129">System.Object</span><span class="sxs-lookup"><span data-stu-id="a0361-129">System.Object</span></span>

## <span data-ttu-id="a0361-130">참고</span><span class="sxs-lookup"><span data-stu-id="a0361-130">NOTES</span></span>

## <span data-ttu-id="a0361-131">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a0361-131">RELATED LINKS</span></span>

[<span data-ttu-id="a0361-132">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="a0361-132">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="a0361-133">Import-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="a0361-133">Import-BinaryMiLog</span></span>](import-binarymilog.md)

[<span data-ttu-id="a0361-134">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="a0361-134">Import-Clixml</span></span>](../microsoft.powershell.utility/import-clixml.md)
