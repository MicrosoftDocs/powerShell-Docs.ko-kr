---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: 9314aaf7c444f9a1159b301135d4130737daa439
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215553"
---
# <span data-ttu-id="e5730-103">Clear-RecycleBin</span><span class="sxs-lookup"><span data-stu-id="e5730-103">Clear-RecycleBin</span></span>

## <span data-ttu-id="e5730-104">개요</span><span class="sxs-lookup"><span data-stu-id="e5730-104">SYNOPSIS</span></span>
<span data-ttu-id="e5730-105">휴지통의 내용을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e5730-105">Clears the contents of a recycle bin.</span></span>

## <span data-ttu-id="e5730-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e5730-106">SYNTAX</span></span>

### <span data-ttu-id="e5730-107">모두</span><span class="sxs-lookup"><span data-stu-id="e5730-107">All</span></span>

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e5730-108">설명</span><span class="sxs-lookup"><span data-stu-id="e5730-108">DESCRIPTION</span></span>

<span data-ttu-id="e5730-109">`Clear-RecycleBin`Cmdlet은 컴퓨터 휴지통의 콘텐츠를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5730-109">The `Clear-RecycleBin` cmdlet deletes the content of a computer's recycle bin.</span></span> <span data-ttu-id="e5730-110">이 작업은 Windows **빈 휴지통** 을 사용 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e5730-110">This action is like using Windows **Empty Recycle Bin** .</span></span>

## <span data-ttu-id="e5730-111">예제</span><span class="sxs-lookup"><span data-stu-id="e5730-111">EXAMPLES</span></span>

### <span data-ttu-id="e5730-112">1: 모든 휴지통 지우기</span><span class="sxs-lookup"><span data-stu-id="e5730-112">1: Clear all recycle bins</span></span>

<span data-ttu-id="e5730-113">이 예제에서는 모든 로컬 컴퓨터의 휴지통이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="e5730-113">In this example, all the local computer's recycle bins are cleared.</span></span>

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="e5730-114">`Clear-RecycleBin` 로컬 컴퓨터의 모든 휴지통을 지우도록 사용자에 게 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5730-114">`Clear-RecycleBin` prompts the user for confirmation to clear all recycle bins on the local computer.</span></span>

### <span data-ttu-id="e5730-115">2: 지정 된 휴지통 지우기</span><span class="sxs-lookup"><span data-stu-id="e5730-115">2: Clear a specified recycle bin</span></span>

<span data-ttu-id="e5730-116">이 예제에서는 지정 된 드라이브 문자에 대 한 휴지통을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e5730-116">This example clears the recycle bin for a specified drive letter.</span></span>

```powershell
Clear-RecycleBin -DriveLetter C
```

<span data-ttu-id="e5730-117">`Clear-RecycleBin`**r** 매개 변수를 사용 하 여 **C** 볼륨의 휴지통을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5730-117">`Clear-RecycleBin` uses the **DriveLetter** parameter to specify the recycle bin on the **C** volume.</span></span> <span data-ttu-id="e5730-118">사용자에 게 명령을 실행 하기 위한 확인 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5730-118">The user is prompted for confirmation to run the command.</span></span>

### <span data-ttu-id="e5730-119">3: 확인 하지 않고 모든 휴지통 지우기</span><span class="sxs-lookup"><span data-stu-id="e5730-119">3: Clear all recycle bins without confirmation</span></span>

<span data-ttu-id="e5730-120">이 예에서는 로컬 컴퓨터의 휴지통을 지우도록 확인 하는 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e5730-120">This example doesn't prompt for confirmation to clear the local computer's recycle bins.</span></span>

```powershell
Clear-RecycleBin -Force
```

<span data-ttu-id="e5730-121">`Clear-RecycleBin` 는 **Force** 매개 변수를 사용 하 고 로컬 컴퓨터의 모든 휴지통을 지우도록 사용자에 게 확인 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e5730-121">`Clear-RecycleBin` uses the **Force** parameter and doesn't prompt the user for confirmation to clear all recycle bins on the local computer.</span></span>

<span data-ttu-id="e5730-122">대신을 `-Force` 로 바꿉니다 `-Confirm:$false` .</span><span class="sxs-lookup"><span data-stu-id="e5730-122">An alternative is to replace `-Force` with `-Confirm:$false`.</span></span>

## <span data-ttu-id="e5730-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e5730-123">PARAMETERS</span></span>

### <span data-ttu-id="e5730-124">-R</span><span class="sxs-lookup"><span data-stu-id="e5730-124">-DriveLetter</span></span>

<span data-ttu-id="e5730-125">단일 드라이브 문자 또는 드라이브 문자 배열에 대해 지울 휴지통을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5730-125">Specifies the recycle bin to clear for a single drive letter or an array of drive letters.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e5730-126">-Force</span><span class="sxs-lookup"><span data-stu-id="e5730-126">-Force</span></span>

<span data-ttu-id="e5730-127">사용자에 게 휴지통 선택을 취소 하기 위한 확인 메시지가 표시 되지 않도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5730-127">Specifies that the user isn't prompted for confirmation to clear a recycle bin.</span></span>

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

### <span data-ttu-id="e5730-128">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e5730-128">-Confirm</span></span>

<span data-ttu-id="e5730-129">Cmdlet을 실행 하기 전에 사용자 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5730-129">Prompts for user confirmation before running the cmdlet.</span></span> <span data-ttu-id="e5730-130">**Confirm** 매개 변수가 지정 되지 않은 경우에도 사용자에 게 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5730-130">The user is prompted for confirmation even if the **Confirm** parameter isn't specified.</span></span>

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

### <span data-ttu-id="e5730-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e5730-131">-WhatIf</span></span>

<span data-ttu-id="e5730-132">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Clear-RecycleBin` .</span><span class="sxs-lookup"><span data-stu-id="e5730-132">Shows what would happen if `Clear-RecycleBin` runs.</span></span> <span data-ttu-id="e5730-133">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e5730-133">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="e5730-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e5730-134">CommonParameters</span></span>

<span data-ttu-id="e5730-135">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e5730-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e5730-136">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5730-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e5730-137">입력</span><span class="sxs-lookup"><span data-stu-id="e5730-137">INPUTS</span></span>

## <span data-ttu-id="e5730-138">출력</span><span class="sxs-lookup"><span data-stu-id="e5730-138">OUTPUTS</span></span>

### <span data-ttu-id="e5730-139">없음</span><span class="sxs-lookup"><span data-stu-id="e5730-139">None</span></span>

## <span data-ttu-id="e5730-140">참고</span><span class="sxs-lookup"><span data-stu-id="e5730-140">NOTES</span></span>

## <span data-ttu-id="e5730-141">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e5730-141">RELATED LINKS</span></span>
