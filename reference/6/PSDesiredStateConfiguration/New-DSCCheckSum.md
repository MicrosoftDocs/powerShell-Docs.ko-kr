---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/new-dscchecksum?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-DscChecksum
ms.openlocfilehash: 2637cc092d3be2bb3bff051268ef288c81ef3ad7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212481"
---
# <span data-ttu-id="436b1-103">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="436b1-103">New-DscChecksum</span></span>

## <span data-ttu-id="436b1-104">개요</span><span class="sxs-lookup"><span data-stu-id="436b1-104">SYNOPSIS</span></span>
<span data-ttu-id="436b1-105">DSC 문서 및 DSC 리소스에 대 한 체크섬 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="436b1-105">Creates checksum files for DSC documents and DSC resources.</span></span>

## <span data-ttu-id="436b1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="436b1-106">SYNTAX</span></span>

```
New-DscChecksum [-Path] <String[]> [[-OutPath] <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="436b1-107">설명</span><span class="sxs-lookup"><span data-stu-id="436b1-107">DESCRIPTION</span></span>

<span data-ttu-id="436b1-108">**새-dscchecksum** Cmdlet은 PowerShell Dsc (필요한 상태 구성) 문서 및 압축 된 dsc 리소스에 대 한 체크섬 파일을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="436b1-108">The **New-DSCCheckSum** cmdlet generates checksum files for PowerShell Desired State Configuration (DSC) documents and compressed DSC resources.</span></span>
<span data-ttu-id="436b1-109">이 cmdlet은 끌어오기 모드에서 사용할 각 구성 및 리소스에 대 한 체크섬 파일을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="436b1-109">This cmdlet generates a checksum file for each configuration and resource to be used in pull mode.</span></span>
<span data-ttu-id="436b1-110">DSC 서비스는 체크섬을 사용 하 여 대상 노드에 올바른 구성 및 리소스가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="436b1-110">The DSC service uses the checksums to make sure that the correct configuration and resources exist on the target node.</span></span>
<span data-ttu-id="436b1-111">DSC 서비스 저장소에서 연결 된 DSC 문서와 압축 된 DSC 리소스와 함께 체크섬을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="436b1-111">Place the checksums together with the associated DSC documents and compressed DSC resources in the DSC service store.</span></span>

## <span data-ttu-id="436b1-112">예제</span><span class="sxs-lookup"><span data-stu-id="436b1-112">EXAMPLES</span></span>

### <span data-ttu-id="436b1-113">예 1: 특정 경로의 모든 구성에 대 한 체크섬 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="436b1-113">Example 1: Create checksum files for all configurations in a specific path</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="436b1-114">이 명령은 C:\DSC\Configurations 경로에 모든 구성에 대한 체크섬 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="436b1-114">This command creates checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="436b1-115">이미 있는 체크섬 파일은 모두 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="436b1-115">Any checksum files that already exist are skipped.</span></span>

### <span data-ttu-id="436b1-116">예 2: 특정 경로의 모든 구성에 대 한 체크섬 파일을 만들고 기존 체크섬 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="436b1-116">Example 2: Create checksum files for all configurations in a specific path and overwrite the existing checksum files</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\" -Force
```

<span data-ttu-id="436b1-117">이 명령은 C:\DSC\Configurations 경로에 모든 구성에 대한 새 체크섬 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="436b1-117">This command creates new checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="436b1-118">*Force* 매개 변수를 지정 하면 명령이 이미 있는 체크섬 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="436b1-118">Specifying the *Force* parameter causes the command to overwrite any checksum files that already exist.</span></span>

## <span data-ttu-id="436b1-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="436b1-119">PARAMETERS</span></span>

### <span data-ttu-id="436b1-120">-Confirm</span><span class="sxs-lookup"><span data-stu-id="436b1-120">-Confirm</span></span>

<span data-ttu-id="436b1-121">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="436b1-121">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="436b1-122">-Force</span><span class="sxs-lookup"><span data-stu-id="436b1-122">-Force</span></span>

<span data-ttu-id="436b1-123">cmdlet이 지정한 출력 파일을 덮어씀을 나타냅니다(파일이 이미 있는 경우).</span><span class="sxs-lookup"><span data-stu-id="436b1-123">Indicates that the cmdlet overwrites the specified output file if it already exists.</span></span>

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

### <span data-ttu-id="436b1-124">-OutPath</span><span class="sxs-lookup"><span data-stu-id="436b1-124">-OutPath</span></span>

<span data-ttu-id="436b1-125">체크섬 출력 파일의 경로 및 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="436b1-125">Specifies the path and file name of the output checksum file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="436b1-126">-Path</span><span class="sxs-lookup"><span data-stu-id="436b1-126">-Path</span></span>

<span data-ttu-id="436b1-127">입력 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="436b1-127">Specifies the path of the input file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ConfigurationPath

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="436b1-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="436b1-128">-WhatIf</span></span>

<span data-ttu-id="436b1-129">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="436b1-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="436b1-130">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="436b1-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="436b1-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="436b1-131">CommonParameters</span></span>

<span data-ttu-id="436b1-132">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="436b1-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="436b1-133">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="436b1-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="436b1-134">입력</span><span class="sxs-lookup"><span data-stu-id="436b1-134">INPUTS</span></span>

### <span data-ttu-id="436b1-135">없음</span><span class="sxs-lookup"><span data-stu-id="436b1-135">None</span></span>

## <span data-ttu-id="436b1-136">출력</span><span class="sxs-lookup"><span data-stu-id="436b1-136">OUTPUTS</span></span>

### <span data-ttu-id="436b1-137">System.Object</span><span class="sxs-lookup"><span data-stu-id="436b1-137">System.Object</span></span>

## <span data-ttu-id="436b1-138">참고</span><span class="sxs-lookup"><span data-stu-id="436b1-138">NOTES</span></span>

## <span data-ttu-id="436b1-139">관련 링크</span><span class="sxs-lookup"><span data-stu-id="436b1-139">RELATED LINKS</span></span>

[<span data-ttu-id="436b1-140">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="436b1-140">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)
