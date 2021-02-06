---
external help file: PSDesiredStateConfiguration-help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/new-dscchecksum?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-DscChecksum
ms.openlocfilehash: 8b8d0c545cdb36b6184a0670a52a5a30aa33a465
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602809"
---
# <span data-ttu-id="6e64a-102">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="6e64a-102">New-DscChecksum</span></span>

## <span data-ttu-id="6e64a-103">개요</span><span class="sxs-lookup"><span data-stu-id="6e64a-103">SYNOPSIS</span></span>
<span data-ttu-id="6e64a-104">DSC 문서 및 DSC 리소스에 대 한 체크섬 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6e64a-104">Creates checksum files for DSC documents and DSC resources.</span></span>

## <span data-ttu-id="6e64a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6e64a-105">SYNTAX</span></span>

```
New-DscChecksum [-Path] <String[]> [[-OutPath] <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6e64a-106">설명</span><span class="sxs-lookup"><span data-stu-id="6e64a-106">DESCRIPTION</span></span>

<span data-ttu-id="6e64a-107">**새-dscchecksum** Cmdlet은 PowerShell Dsc (필요한 상태 구성) 문서 및 압축 된 dsc 리소스에 대 한 체크섬 파일을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e64a-107">The **New-DSCCheckSum** cmdlet generates checksum files for PowerShell Desired State Configuration (DSC) documents and compressed DSC resources.</span></span>
<span data-ttu-id="6e64a-108">이 cmdlet은 끌어오기 모드에서 사용할 각 구성 및 리소스에 대 한 체크섬 파일을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e64a-108">This cmdlet generates a checksum file for each configuration and resource to be used in pull mode.</span></span>
<span data-ttu-id="6e64a-109">DSC 서비스는 체크섬을 사용 하 여 대상 노드에 올바른 구성 및 리소스가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e64a-109">The DSC service uses the checksums to make sure that the correct configuration and resources exist on the target node.</span></span>
<span data-ttu-id="6e64a-110">DSC 서비스 저장소에서 연결 된 DSC 문서와 압축 된 DSC 리소스와 함께 체크섬을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e64a-110">Place the checksums together with the associated DSC documents and compressed DSC resources in the DSC service store.</span></span>

## <span data-ttu-id="6e64a-111">예제</span><span class="sxs-lookup"><span data-stu-id="6e64a-111">EXAMPLES</span></span>

### <span data-ttu-id="6e64a-112">예 1: 특정 경로의 모든 구성에 대 한 체크섬 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="6e64a-112">Example 1: Create checksum files for all configurations in a specific path</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="6e64a-113">이 명령은 C:\DSC\Configurations 경로에 모든 구성에 대한 체크섬 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6e64a-113">This command creates checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="6e64a-114">이미 있는 체크섬 파일은 모두 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="6e64a-114">Any checksum files that already exist are skipped.</span></span>

### <span data-ttu-id="6e64a-115">예 2: 특정 경로의 모든 구성에 대 한 체크섬 파일을 만들고 기존 체크섬 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="6e64a-115">Example 2: Create checksum files for all configurations in a specific path and overwrite the existing checksum files</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\" -Force
```

<span data-ttu-id="6e64a-116">이 명령은 C:\DSC\Configurations 경로에 모든 구성에 대한 새 체크섬 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6e64a-116">This command creates new checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="6e64a-117">*Force* 매개 변수를 지정 하면 명령이 이미 있는 체크섬 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="6e64a-117">Specifying the *Force* parameter causes the command to overwrite any checksum files that already exist.</span></span>

## <span data-ttu-id="6e64a-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6e64a-118">PARAMETERS</span></span>

### <span data-ttu-id="6e64a-119">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6e64a-119">-Confirm</span></span>

<span data-ttu-id="6e64a-120">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="6e64a-120">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6e64a-121">-Force</span><span class="sxs-lookup"><span data-stu-id="6e64a-121">-Force</span></span>

<span data-ttu-id="6e64a-122">cmdlet이 지정한 출력 파일을 덮어씀을 나타냅니다(파일이 이미 있는 경우).</span><span class="sxs-lookup"><span data-stu-id="6e64a-122">Indicates that the cmdlet overwrites the specified output file if it already exists.</span></span>

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

### <span data-ttu-id="6e64a-123">-OutPath</span><span class="sxs-lookup"><span data-stu-id="6e64a-123">-OutPath</span></span>

<span data-ttu-id="6e64a-124">체크섬 출력 파일의 경로 및 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e64a-124">Specifies the path and file name of the output checksum file.</span></span>

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

### <span data-ttu-id="6e64a-125">-Path</span><span class="sxs-lookup"><span data-stu-id="6e64a-125">-Path</span></span>

<span data-ttu-id="6e64a-126">입력 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e64a-126">Specifies the path of the input file.</span></span>

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

### <span data-ttu-id="6e64a-127">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6e64a-127">-WhatIf</span></span>

<span data-ttu-id="6e64a-128">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6e64a-128">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6e64a-129">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e64a-129">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6e64a-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6e64a-130">CommonParameters</span></span>

<span data-ttu-id="6e64a-131">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6e64a-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6e64a-132">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e64a-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6e64a-133">입력</span><span class="sxs-lookup"><span data-stu-id="6e64a-133">INPUTS</span></span>

### <span data-ttu-id="6e64a-134">없음</span><span class="sxs-lookup"><span data-stu-id="6e64a-134">None</span></span>

## <span data-ttu-id="6e64a-135">출력</span><span class="sxs-lookup"><span data-stu-id="6e64a-135">OUTPUTS</span></span>

### <span data-ttu-id="6e64a-136">System.Object</span><span class="sxs-lookup"><span data-stu-id="6e64a-136">System.Object</span></span>

## <span data-ttu-id="6e64a-137">참고</span><span class="sxs-lookup"><span data-stu-id="6e64a-137">NOTES</span></span>

## <span data-ttu-id="6e64a-138">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6e64a-138">RELATED LINKS</span></span>

[<span data-ttu-id="6e64a-139">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="6e64a-139">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

