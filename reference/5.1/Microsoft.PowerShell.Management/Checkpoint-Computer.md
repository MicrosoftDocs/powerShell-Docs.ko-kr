---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/checkpoint-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Checkpoint-Computer
ms.openlocfilehash: 61f8d626cd45cfe47f0e65a3043696a01c97ca20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215609"
---
# <span data-ttu-id="1e12b-103">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="1e12b-103">Checkpoint-Computer</span></span>

## <span data-ttu-id="1e12b-104">개요</span><span class="sxs-lookup"><span data-stu-id="1e12b-104">SYNOPSIS</span></span>
<span data-ttu-id="1e12b-105">로컬 컴퓨터에 시스템 복원 지점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e12b-105">Creates a system restore point on the local computer.</span></span>

## <span data-ttu-id="1e12b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1e12b-106">SYNTAX</span></span>

```
Checkpoint-Computer [-Description] <String> [[-RestorePointType] <String>] [<CommonParameters>]
```

## <span data-ttu-id="1e12b-107">설명</span><span class="sxs-lookup"><span data-stu-id="1e12b-107">DESCRIPTION</span></span>

<span data-ttu-id="1e12b-108">`Checkpoint-Computer`Cmdlet은 로컬 컴퓨터에 시스템 복원 지점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e12b-108">The `Checkpoint-Computer` cmdlet creates a system restore point on the local computer.</span></span>

<span data-ttu-id="1e12b-109">시스템 복원 지점과 `Checkpoint-Computer` cmdlet은 windows 8, windows 7, Windows Vista 및 WINDOWS XP와 같은 클라이언트 운영 체제 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e12b-109">System restore points and the `Checkpoint-Computer` cmdlet are supported only on client operating systems, such as Windows 8, Windows 7, Windows Vista, and Windows XP.</span></span>

<span data-ttu-id="1e12b-110">Windows 8부터는 `Checkpoint-Computer` 매일 둘 이상의 검사점을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e12b-110">Beginning in Windows 8, `Checkpoint-Computer` cannot create more than one checkpoint each day.</span></span>

## <span data-ttu-id="1e12b-111">예제</span><span class="sxs-lookup"><span data-stu-id="1e12b-111">EXAMPLES</span></span>

### <span data-ttu-id="1e12b-112">예 1: 시스템 복원 지점 만들기</span><span class="sxs-lookup"><span data-stu-id="1e12b-112">Example 1: Create a system restore point</span></span>

```powershell
Checkpoint-Computer -Description "Install MyApp"
```

<span data-ttu-id="1e12b-113">이 명령은 Install MyApp 라는 시스템 복원 지점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e12b-113">This command creates a system restore point called Install MyApp.</span></span>
<span data-ttu-id="1e12b-114">"Install MyApp"라는 시스템 복원 지점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e12b-114">It uses the default APPLICATION_INSTALL restore point type.</span></span>

### <span data-ttu-id="1e12b-115">예 2: 시스템 MODIFY_SETTINGS 복원 지점 만들기</span><span class="sxs-lookup"><span data-stu-id="1e12b-115">Example 2: Create a system MODIFY_SETTINGS restore point</span></span>

```powershell
Checkpoint-Computer -Description "ChangeNetSettings" -RestorePointType MODIFY_SETTINGS
```

<span data-ttu-id="1e12b-116">이 명령은 "ChangeNetSettings"라는 MODIFY_SETTINGS 시스템 복원 지점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e12b-116">This command creates a MODIFY_SETTINGS system restore point called "ChangeNetSettings".</span></span>

## <span data-ttu-id="1e12b-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1e12b-117">PARAMETERS</span></span>

### <span data-ttu-id="1e12b-118">-Description</span><span class="sxs-lookup"><span data-stu-id="1e12b-118">-Description</span></span>

<span data-ttu-id="1e12b-119">복원 지점에 대한 설명이 포함된 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e12b-119">Specifies a descriptive name for the restore point.</span></span>
<span data-ttu-id="1e12b-120">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1e12b-120">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e12b-121">-RestorePointType</span><span class="sxs-lookup"><span data-stu-id="1e12b-121">-RestorePointType</span></span>

<span data-ttu-id="1e12b-122">복원 지점의 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e12b-122">Specifies the type of restore point.</span></span>
<span data-ttu-id="1e12b-123">기본값은 APPLICATION_INSTALL입니다.</span><span class="sxs-lookup"><span data-stu-id="1e12b-123">The default is APPLICATION_INSTALL.</span></span>

<span data-ttu-id="1e12b-124">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1e12b-124">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1e12b-125">APPLICATION_INSTALL</span><span class="sxs-lookup"><span data-stu-id="1e12b-125">APPLICATION_INSTALL</span></span>
- <span data-ttu-id="1e12b-126">APPLICATION_UNINSTALL</span><span class="sxs-lookup"><span data-stu-id="1e12b-126">APPLICATION_UNINSTALL</span></span>
- <span data-ttu-id="1e12b-127">DEVICE_DRIVER_INSTALL</span><span class="sxs-lookup"><span data-stu-id="1e12b-127">DEVICE_DRIVER_INSTALL</span></span>
- <span data-ttu-id="1e12b-128">MODIFY_SETTINGS</span><span class="sxs-lookup"><span data-stu-id="1e12b-128">MODIFY_SETTINGS</span></span>
- <span data-ttu-id="1e12b-129">CANCELLED_OPERATION</span><span class="sxs-lookup"><span data-stu-id="1e12b-129">CANCELLED_OPERATION</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: RPT
Accepted values: APPLICATION_INSTALL, APPLICATION_UNINSTALL, DEVICE_DRIVER_INSTALL, MODIFY_SETTINGS, CANCELLED_OPERATION

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1e12b-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1e12b-130">CommonParameters</span></span>

<span data-ttu-id="1e12b-131">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1e12b-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1e12b-132">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e12b-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="1e12b-133">입력</span><span class="sxs-lookup"><span data-stu-id="1e12b-133">INPUTS</span></span>

### <span data-ttu-id="1e12b-134">없음</span><span class="sxs-lookup"><span data-stu-id="1e12b-134">None</span></span>

<span data-ttu-id="1e12b-135">개체를에 연결할 수 없습니다 `Checkpoint-Computer` .</span><span class="sxs-lookup"><span data-stu-id="1e12b-135">You cannot pipe objects to `Checkpoint-Computer`.</span></span>

## <span data-ttu-id="1e12b-136">출력</span><span class="sxs-lookup"><span data-stu-id="1e12b-136">OUTPUTS</span></span>

### <span data-ttu-id="1e12b-137">없음</span><span class="sxs-lookup"><span data-stu-id="1e12b-137">None</span></span>

<span data-ttu-id="1e12b-138">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e12b-138">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1e12b-139">참고</span><span class="sxs-lookup"><span data-stu-id="1e12b-139">NOTES</span></span>

- <span data-ttu-id="1e12b-140">이 cmdlet은 **BEGIN_SYSTEM_CHANGE** 이벤트와 함께 **SystemRestore** 클래스의 **CreateRestorePoint** 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e12b-140">This cmdlet uses the **CreateRestorePoint** method of the **SystemRestore** class with a **BEGIN_SYSTEM_CHANGE** event.</span></span>
- <span data-ttu-id="1e12b-141">Windows 8부터는 `Checkpoint-Computer` 매일 둘 이상의 시스템 복원 지점을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e12b-141">Beginning in Windows 8, `Checkpoint-Computer` cannot create more than one system restore point each day.</span></span> <span data-ttu-id="1e12b-142">24시간이 지나기 전에 새 복원 지점을 만들려고 하면 Windows PowerShell에서 다음 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="1e12b-142">If you try to create a new restore point before the 24-hour period has elapsed, Windows PowerShell generates the following error:</span></span>

  `"A new system restore point cannot be created because one has already been created within the past 24 hours.
  Please try again later."`

## <span data-ttu-id="1e12b-143">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1e12b-143">RELATED LINKS</span></span>

[<span data-ttu-id="1e12b-144">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="1e12b-144">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="1e12b-145">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="1e12b-145">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="1e12b-146">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="1e12b-146">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="1e12b-147">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="1e12b-147">Restore-Computer</span></span>](Restore-Computer.md)
