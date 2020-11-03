---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: 7e34db6eb29bf60da5ce1217653db815347d69ae
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217601"
---
# <span data-ttu-id="4a54c-103">Clear-RecycleBin</span><span class="sxs-lookup"><span data-stu-id="4a54c-103">Clear-RecycleBin</span></span>

## <span data-ttu-id="4a54c-104">개요</span><span class="sxs-lookup"><span data-stu-id="4a54c-104">SYNOPSIS</span></span>
<span data-ttu-id="4a54c-105">휴지통의 내용을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="4a54c-105">Clears the contents of a recycle bin.</span></span>

## <span data-ttu-id="4a54c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4a54c-106">SYNTAX</span></span>

### <span data-ttu-id="4a54c-107">모두</span><span class="sxs-lookup"><span data-stu-id="4a54c-107">All</span></span>

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4a54c-108">설명</span><span class="sxs-lookup"><span data-stu-id="4a54c-108">DESCRIPTION</span></span>

<span data-ttu-id="4a54c-109">`Clear-RecycleBin`Cmdlet은 컴퓨터 휴지통의 콘텐츠를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a54c-109">The `Clear-RecycleBin` cmdlet deletes the content of a computer's recycle bin.</span></span> <span data-ttu-id="4a54c-110">이 작업은 Windows **빈 휴지통** 을 사용 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4a54c-110">This action is like using Windows **Empty Recycle Bin**.</span></span>

<span data-ttu-id="4a54c-111">이 cmdlet은 PowerShell 7에서 다시 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4a54c-111">This cmdlet was readded in PowerShell 7.</span></span>

## <span data-ttu-id="4a54c-112">예제</span><span class="sxs-lookup"><span data-stu-id="4a54c-112">EXAMPLES</span></span>

### <span data-ttu-id="4a54c-113">1: 모든 휴지통 지우기</span><span class="sxs-lookup"><span data-stu-id="4a54c-113">1: Clear all recycle bins</span></span>

<span data-ttu-id="4a54c-114">이 예제에서는 모든 로컬 컴퓨터의 휴지통이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="4a54c-114">In this example, all the local computer's recycle bins are cleared.</span></span>

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="4a54c-115">`Clear-RecycleBin` 로컬 컴퓨터의 모든 휴지통을 지우도록 사용자에 게 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a54c-115">`Clear-RecycleBin` prompts the user for confirmation to clear all recycle bins on the local computer.</span></span>

### <span data-ttu-id="4a54c-116">2: 지정 된 휴지통 지우기</span><span class="sxs-lookup"><span data-stu-id="4a54c-116">2: Clear a specified recycle bin</span></span>

<span data-ttu-id="4a54c-117">이 예제에서는 지정 된 드라이브 문자에 대 한 휴지통을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="4a54c-117">This example clears the recycle bin for a specified drive letter.</span></span>

```powershell
Clear-RecycleBin -DriveLetter C
```

<span data-ttu-id="4a54c-118">`Clear-RecycleBin`**r** 매개 변수를 사용 하 여 **C** 볼륨의 휴지통을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a54c-118">`Clear-RecycleBin` uses the **DriveLetter** parameter to specify the recycle bin on the **C** volume.</span></span> <span data-ttu-id="4a54c-119">사용자에 게 명령을 실행 하기 위한 확인 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a54c-119">The user is prompted for confirmation to run the command.</span></span>

### <span data-ttu-id="4a54c-120">3: 확인 하지 않고 모든 휴지통 지우기</span><span class="sxs-lookup"><span data-stu-id="4a54c-120">3: Clear all recycle bins without confirmation</span></span>

<span data-ttu-id="4a54c-121">이 예에서는 로컬 컴퓨터의 휴지통을 지우도록 확인 하는 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4a54c-121">This example doesn't prompt for confirmation to clear the local computer's recycle bins.</span></span>

```powershell
Clear-RecycleBin -Force
```

<span data-ttu-id="4a54c-122">`Clear-RecycleBin` 는 **Force** 매개 변수를 사용 하 고 로컬 컴퓨터의 모든 휴지통을 지우도록 사용자에 게 확인 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4a54c-122">`Clear-RecycleBin` uses the **Force** parameter and doesn't prompt the user for confirmation to clear all recycle bins on the local computer.</span></span>

<span data-ttu-id="4a54c-123">대신을 `-Force` 로 바꿉니다 `-Confirm:$false` .</span><span class="sxs-lookup"><span data-stu-id="4a54c-123">An alternative is to replace `-Force` with `-Confirm:$false`.</span></span>

## <span data-ttu-id="4a54c-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4a54c-124">PARAMETERS</span></span>

### <span data-ttu-id="4a54c-125">-R</span><span class="sxs-lookup"><span data-stu-id="4a54c-125">-DriveLetter</span></span>

<span data-ttu-id="4a54c-126">단일 드라이브 문자 또는 드라이브 문자 배열에 대해 지울 휴지통을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a54c-126">Specifies the recycle bin to clear for a single drive letter or an array of drive letters.</span></span>

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

### <span data-ttu-id="4a54c-127">-Force</span><span class="sxs-lookup"><span data-stu-id="4a54c-127">-Force</span></span>

<span data-ttu-id="4a54c-128">사용자에 게 휴지통 선택을 취소 하기 위한 확인 메시지가 표시 되지 않도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a54c-128">Specifies that the user isn't prompted for confirmation to clear a recycle bin.</span></span>

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

### <span data-ttu-id="4a54c-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4a54c-129">-Confirm</span></span>

<span data-ttu-id="4a54c-130">Cmdlet을 실행 하기 전에 사용자 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a54c-130">Prompts for user confirmation before running the cmdlet.</span></span> <span data-ttu-id="4a54c-131">**Confirm** 매개 변수가 지정 되지 않은 경우에도 사용자에 게 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a54c-131">The user is prompted for confirmation even if the **Confirm** parameter isn't specified.</span></span>

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

### <span data-ttu-id="4a54c-132">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4a54c-132">-WhatIf</span></span>

<span data-ttu-id="4a54c-133">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Clear-RecycleBin` .</span><span class="sxs-lookup"><span data-stu-id="4a54c-133">Shows what would happen if `Clear-RecycleBin` runs.</span></span> <span data-ttu-id="4a54c-134">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4a54c-134">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="4a54c-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4a54c-135">CommonParameters</span></span>

<span data-ttu-id="4a54c-136">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4a54c-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4a54c-137">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a54c-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4a54c-138">입력</span><span class="sxs-lookup"><span data-stu-id="4a54c-138">INPUTS</span></span>

## <span data-ttu-id="4a54c-139">출력</span><span class="sxs-lookup"><span data-stu-id="4a54c-139">OUTPUTS</span></span>

### <span data-ttu-id="4a54c-140">없음</span><span class="sxs-lookup"><span data-stu-id="4a54c-140">None</span></span>

## <span data-ttu-id="4a54c-141">참고</span><span class="sxs-lookup"><span data-stu-id="4a54c-141">NOTES</span></span>

## <span data-ttu-id="4a54c-142">관련 링크</span><span class="sxs-lookup"><span data-stu-id="4a54c-142">RELATED LINKS</span></span>

