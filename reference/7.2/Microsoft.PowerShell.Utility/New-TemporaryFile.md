---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-temporaryfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TemporaryFile
ms.openlocfilehash: 1c66cd3b1cc2fccc58cd75c367b41c445deb1e72
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602445"
---
# <span data-ttu-id="05d72-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="05d72-102">New-TemporaryFile</span></span>

## <span data-ttu-id="05d72-103">개요</span><span class="sxs-lookup"><span data-stu-id="05d72-103">SYNOPSIS</span></span>
<span data-ttu-id="05d72-104">임시 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="05d72-104">Creates a temporary file.</span></span>

## <span data-ttu-id="05d72-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="05d72-105">SYNTAX</span></span>

```
New-TemporaryFile [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="05d72-106">설명</span><span class="sxs-lookup"><span data-stu-id="05d72-106">DESCRIPTION</span></span>

<span data-ttu-id="05d72-107">이 cmdlet은 스크립트에서 사용할 수 있는 임시 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="05d72-107">This cmdlet creates temporary files that you can use in scripts.</span></span>

<span data-ttu-id="05d72-108">`New-TemporaryFile`Cmdlet은 파일 이름 확장명이 인 빈 파일을 만듭니다 `.tmp` .</span><span class="sxs-lookup"><span data-stu-id="05d72-108">The `New-TemporaryFile` cmdlet creates an empty file that has the `.tmp` file name extension.</span></span>
<span data-ttu-id="05d72-109">이 cmdlet은 파일의 이름을 `tmp<NNNN>.tmp` 로 `<NNNN>` 바꿉니다. 여기서는 임의의 16 진수입니다.</span><span class="sxs-lookup"><span data-stu-id="05d72-109">This cmdlet names the file `tmp<NNNN>.tmp`, where `<NNNN>` is a random hexadecimal number.</span></span>
<span data-ttu-id="05d72-110">Cmdlet은 **임시** 폴더에 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="05d72-110">The cmdlet creates the file in your **TEMP** folder.</span></span>

<span data-ttu-id="05d72-111">이 cmdlet은 [path. GetTempPath ()](/dotnet/api/system.io.path.gettemppath) 메서드를 사용 하 여 **임시** 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="05d72-111">This cmdlet uses the [Path.GetTempPath()](/dotnet/api/system.io.path.gettemppath) method to find your **TEMP** folder.</span></span> <span data-ttu-id="05d72-112">이 메서드는 다음 순서로 환경 변수가 있는지 확인 하 고 찾은 첫 번째 경로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="05d72-112">This method checks for the existence of environment variables in the following order and uses the first path found:</span></span>

- <span data-ttu-id="05d72-113">Windows 플랫폼에서:</span><span class="sxs-lookup"><span data-stu-id="05d72-113">On Windows platforms:</span></span>

  1. <span data-ttu-id="05d72-114">TMP 환경 변수로 지정 된 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="05d72-114">The path specified by the TMP environment variable.</span></span>
  1. <span data-ttu-id="05d72-115">TEMP 환경 변수로 지정 된 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="05d72-115">The path specified by the TEMP environment variable.</span></span>
  1. <span data-ttu-id="05d72-116">USERPROFILE 환경 변수로 지정 된 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="05d72-116">The path specified by the USERPROFILE environment variable.</span></span>
  1. <span data-ttu-id="05d72-117">Windows 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="05d72-117">The Windows directory.</span></span>

- <span data-ttu-id="05d72-118">Windows가 아닌 플랫폼에서: TMPDIR 환경 변수에 지정 된 경로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="05d72-118">On non-Windows platforms: Uses the path specified by the TMPDIR environment variable.</span></span>

## <span data-ttu-id="05d72-119">예제</span><span class="sxs-lookup"><span data-stu-id="05d72-119">EXAMPLES</span></span>

### <span data-ttu-id="05d72-120">예제 1: 임시 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="05d72-120">Example 1: Create a temporary file</span></span>

```powershell
$TempFile = New-TemporaryFile
```

<span data-ttu-id="05d72-121">이 명령은 `.tmp` 임시 폴더에 파일을 생성 한 다음 해당 파일에 대 한 참조를 `$TempFile` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="05d72-121">This command generates a `.tmp` file in your temporary folder, and then stores a reference to the file in the `$TempFile` variable.</span></span> <span data-ttu-id="05d72-122">스크립트에서 나중에이 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05d72-122">You can use this file later in your script.</span></span>

## <span data-ttu-id="05d72-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="05d72-123">PARAMETERS</span></span>

### <span data-ttu-id="05d72-124">-Confirm</span><span class="sxs-lookup"><span data-stu-id="05d72-124">-Confirm</span></span>

<span data-ttu-id="05d72-125">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="05d72-125">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="05d72-126">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="05d72-126">-WhatIf</span></span>

<span data-ttu-id="05d72-127">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="05d72-127">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="05d72-128">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05d72-128">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="05d72-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="05d72-129">CommonParameters</span></span>

<span data-ttu-id="05d72-130">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="05d72-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="05d72-131">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05d72-131">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="05d72-132">입력</span><span class="sxs-lookup"><span data-stu-id="05d72-132">INPUTS</span></span>

## <span data-ttu-id="05d72-133">출력</span><span class="sxs-lookup"><span data-stu-id="05d72-133">OUTPUTS</span></span>

### <span data-ttu-id="05d72-134">System.object</span><span class="sxs-lookup"><span data-stu-id="05d72-134">System.IO.FileInfo</span></span>

<span data-ttu-id="05d72-135">이 cmdlet은 임시 파일을 나타내는 **FileInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="05d72-135">This cmdlet returns a **FileInfo** object that represents the temporary file.</span></span>

## <span data-ttu-id="05d72-136">참고</span><span class="sxs-lookup"><span data-stu-id="05d72-136">NOTES</span></span>

## <span data-ttu-id="05d72-137">관련 링크</span><span class="sxs-lookup"><span data-stu-id="05d72-137">RELATED LINKS</span></span>

