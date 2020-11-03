---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-temporaryfile?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TemporaryFile
ms.openlocfilehash: c4bfe6b4ed04ae638421c18f5095403057dc03c9
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210345"
---
# <span data-ttu-id="76da7-103">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="76da7-103">New-TemporaryFile</span></span>

## <span data-ttu-id="76da7-104">개요</span><span class="sxs-lookup"><span data-stu-id="76da7-104">SYNOPSIS</span></span>
<span data-ttu-id="76da7-105">임시 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="76da7-105">Creates a temporary file.</span></span>

## <span data-ttu-id="76da7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="76da7-106">SYNTAX</span></span>

```
New-TemporaryFile [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="76da7-107">설명</span><span class="sxs-lookup"><span data-stu-id="76da7-107">DESCRIPTION</span></span>

<span data-ttu-id="76da7-108">이 cmdlet은 스크립트에서 사용할 수 있는 임시 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="76da7-108">This cmdlet creates temporary files that you can use in scripts.</span></span>

<span data-ttu-id="76da7-109">`New-TemporaryFile`Cmdlet은 파일 이름 확장명이 인 빈 파일을 만듭니다 `.tmp` .</span><span class="sxs-lookup"><span data-stu-id="76da7-109">The `New-TemporaryFile` cmdlet creates an empty file that has the `.tmp` file name extension.</span></span>
<span data-ttu-id="76da7-110">이 cmdlet은 파일의 이름을 `tmp<NNNN>.tmp` 로 `<NNNN>` 바꿉니다. 여기서는 임의의 16 진수입니다.</span><span class="sxs-lookup"><span data-stu-id="76da7-110">This cmdlet names the file `tmp<NNNN>.tmp`, where `<NNNN>` is a random hexadecimal number.</span></span>
<span data-ttu-id="76da7-111">Cmdlet은 **임시** 폴더에 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="76da7-111">The cmdlet creates the file in your **TEMP** folder.</span></span>

<span data-ttu-id="76da7-112">이 cmdlet은 [path. GetTempPath ()](/dotnet/api/system.io.path.gettemppath) 메서드를 사용 하 여 **임시** 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="76da7-112">This cmdlet uses the [Path.GetTempPath()](/dotnet/api/system.io.path.gettemppath) method to find your **TEMP** folder.</span></span> <span data-ttu-id="76da7-113">이 메서드는 다음 순서로 환경 변수가 있는지 확인 하 고 찾은 첫 번째 경로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="76da7-113">This method checks for the existence of environment variables in the following order and uses the first path found:</span></span>

- <span data-ttu-id="76da7-114">Windows 플랫폼에서:</span><span class="sxs-lookup"><span data-stu-id="76da7-114">On Windows platforms:</span></span>

  1. <span data-ttu-id="76da7-115">TMP 환경 변수로 지정 된 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="76da7-115">The path specified by the TMP environment variable.</span></span>
  1. <span data-ttu-id="76da7-116">TEMP 환경 변수로 지정 된 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="76da7-116">The path specified by the TEMP environment variable.</span></span>
  1. <span data-ttu-id="76da7-117">USERPROFILE 환경 변수로 지정 된 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="76da7-117">The path specified by the USERPROFILE environment variable.</span></span>
  1. <span data-ttu-id="76da7-118">Windows 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="76da7-118">The Windows directory.</span></span>

- <span data-ttu-id="76da7-119">Windows가 아닌 플랫폼에서: TMPDIR 환경 변수에 지정 된 경로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="76da7-119">On non-Windows platforms: Uses the path specified by the TMPDIR environment variable.</span></span>

## <span data-ttu-id="76da7-120">예제</span><span class="sxs-lookup"><span data-stu-id="76da7-120">EXAMPLES</span></span>

### <span data-ttu-id="76da7-121">예제 1: 임시 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="76da7-121">Example 1: Create a temporary file</span></span>

```powershell
$TempFile = New-TemporaryFile
```

<span data-ttu-id="76da7-122">이 명령은 `.tmp` 임시 폴더에 파일을 생성 한 다음 해당 파일에 대 한 참조를 `$TempFile` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="76da7-122">This command generates a `.tmp` file in your temporary folder, and then stores a reference to the file in the `$TempFile` variable.</span></span> <span data-ttu-id="76da7-123">스크립트에서 나중에이 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76da7-123">You can use this file later in your script.</span></span>

## <span data-ttu-id="76da7-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="76da7-124">PARAMETERS</span></span>

### <span data-ttu-id="76da7-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="76da7-125">-Confirm</span></span>

<span data-ttu-id="76da7-126">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="76da7-126">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="76da7-127">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="76da7-127">-WhatIf</span></span>

<span data-ttu-id="76da7-128">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="76da7-128">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="76da7-129">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76da7-129">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="76da7-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="76da7-130">CommonParameters</span></span>

<span data-ttu-id="76da7-131">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="76da7-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="76da7-132">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76da7-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="76da7-133">입력</span><span class="sxs-lookup"><span data-stu-id="76da7-133">INPUTS</span></span>

## <span data-ttu-id="76da7-134">출력</span><span class="sxs-lookup"><span data-stu-id="76da7-134">OUTPUTS</span></span>

### <span data-ttu-id="76da7-135">System.object</span><span class="sxs-lookup"><span data-stu-id="76da7-135">System.IO.FileInfo</span></span>

<span data-ttu-id="76da7-136">이 cmdlet은 임시 파일을 나타내는 **FileInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="76da7-136">This cmdlet returns a **FileInfo** object that represents the temporary file.</span></span>

## <span data-ttu-id="76da7-137">참고</span><span class="sxs-lookup"><span data-stu-id="76da7-137">NOTES</span></span>

## <span data-ttu-id="76da7-138">관련 링크</span><span class="sxs-lookup"><span data-stu-id="76da7-138">RELATED LINKS</span></span>
