---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restore-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-Computer
ms.openlocfilehash: 824e9a24693c7a7de01358a048a0df55be333263
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214474"
---
# <span data-ttu-id="645fe-103">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="645fe-103">Restore-Computer</span></span>

## <span data-ttu-id="645fe-104">개요</span><span class="sxs-lookup"><span data-stu-id="645fe-104">SYNOPSIS</span></span>
<span data-ttu-id="645fe-105">로컬 컴퓨터에서 시스템 복원을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-105">Starts a system restore on the local computer.</span></span>

## <span data-ttu-id="645fe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="645fe-106">SYNTAX</span></span>

```
Restore-Computer [-RestorePoint] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="645fe-107">설명</span><span class="sxs-lookup"><span data-stu-id="645fe-107">DESCRIPTION</span></span>
<span data-ttu-id="645fe-108">**Restore-computer** cmdlet은 로컬 컴퓨터를 지정한 시스템 복원 지점으로 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-108">The **Restore-Computer** cmdlet restores the local computer to the specified system restore point.</span></span>

<span data-ttu-id="645fe-109">**복원-** 컴퓨터를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-109">**Restore-Computer** restarts the computer.</span></span>
<span data-ttu-id="645fe-110">다시 시작 작업 중 복원이 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-110">The restore is completed during the restart operation.</span></span>

<span data-ttu-id="645fe-111">시스템 복원 지점과 **복원-컴퓨터** 는 windows 7, windows Vista 및 windows XP와 같은 클라이언트 운영 체제 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-111">System restore points and **Restore-Computer** are supported only on client operating systems, such as Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="645fe-112">예제</span><span class="sxs-lookup"><span data-stu-id="645fe-112">EXAMPLES</span></span>

### <span data-ttu-id="645fe-113">예 1: 로컬 컴퓨터 복원</span><span class="sxs-lookup"><span data-stu-id="645fe-113">Example 1: Restore the local computer</span></span>

```
PS C:\> Restore-Computer -RestorePoint 253
```

<span data-ttu-id="645fe-114">이 명령은 로컬 컴퓨터를 시퀀스 번호가 253 인 복원 지점으로 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-114">This command restores the local computer to the restore point that has sequence number 253.</span></span>

### <span data-ttu-id="645fe-115">예 2: 확인을 사용 하 여 로컬 컴퓨터 복원</span><span class="sxs-lookup"><span data-stu-id="645fe-115">Example 2: Restore the local computer with confirmation</span></span>

```
PS C:\> Restore-Computer -RestorePoint 255 -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Restore-Computer" .
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="645fe-116">이 명령은 로컬 컴퓨터를 시퀀스 번호가 255 인 복원 지점으로 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-116">This command restores the local computer to the restore point that has sequence number 255.</span></span>
<span data-ttu-id="645fe-117">*Confirm* 매개 변수를 사용 하 여 실제로 작업을 수행 하기 전에 사용자에 게 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-117">It uses the *Confirm* parameter to prompt the user before actually performing the operation.</span></span>

### <span data-ttu-id="645fe-118">예 3: 컴퓨터 복원 및 상태 확인</span><span class="sxs-lookup"><span data-stu-id="645fe-118">Example 3: Restore a computer and check the status</span></span>

```
PS C:\> Get-ComputerRestorePoint
PS C:\> Restore-Computer -RestorePoint 255
PS C:\> Get-ComputerRestorePoint -LastStatus
```

<span data-ttu-id="645fe-119">이 명령은 시스템 복원을 실행한 다음 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-119">These commands run a system restore and then check its status.</span></span>

<span data-ttu-id="645fe-120">첫 번째 명령은 **get-computerrestorepoint** 를 사용 하 여 로컬 컴퓨터의 복원 위치를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-120">The first command uses **Get-ComputerRestorePoint** to get the restore points on the local computer.</span></span>

<span data-ttu-id="645fe-121">두 번째 명령은 시퀀스 번호가 255 인 복원 지점으로 컴퓨터를 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-121">The second command restores the computer to the restore point with sequence number 255.</span></span>

<span data-ttu-id="645fe-122">세 번째 명령은 *get-computerrestorepoint* Cmdlet의 *LastStatus* 매개 변수를 사용 하 여 복원 작업의 상태를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-122">The third command uses the *LastStatus* parameter of *Get-ComputerRestorePoint* cmdlet to check the status of the restore operation.</span></span>
<span data-ttu-id="645fe-123">**복원 컴퓨터** 는 강제로 다시 시작 되기 때문에 컴퓨터가 다시 시작 된 후이 명령이 입력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-123">Because **Restore-Computer** forces a restart, this command would be entered after the computer restarts.</span></span>

## <span data-ttu-id="645fe-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="645fe-124">PARAMETERS</span></span>

### <span data-ttu-id="645fe-125">-RestorePoint</span><span class="sxs-lookup"><span data-stu-id="645fe-125">-RestorePoint</span></span>
<span data-ttu-id="645fe-126">복원 지점의 시퀀스 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-126">Specifies the sequence number of the restore point.</span></span>
<span data-ttu-id="645fe-127">시퀀스 번호를 찾으려면 Get-ComputerRestorePoint cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-127">To find the sequence number, use the Get-ComputerRestorePoint cmdlet.</span></span>
<span data-ttu-id="645fe-128">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-128">This parameter is required.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: SequenceNumber, SN, RP

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="645fe-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="645fe-129">-Confirm</span></span>
<span data-ttu-id="645fe-130">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="645fe-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="645fe-131">-WhatIf</span></span>
<span data-ttu-id="645fe-132">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="645fe-133">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="645fe-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="645fe-134">CommonParameters</span></span>
<span data-ttu-id="645fe-135">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="645fe-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="645fe-136">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="645fe-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="645fe-137">입력</span><span class="sxs-lookup"><span data-stu-id="645fe-137">INPUTS</span></span>

### <span data-ttu-id="645fe-138">없음</span><span class="sxs-lookup"><span data-stu-id="645fe-138">None</span></span>
<span data-ttu-id="645fe-139">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-139">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="645fe-140">출력</span><span class="sxs-lookup"><span data-stu-id="645fe-140">OUTPUTS</span></span>

### <span data-ttu-id="645fe-141">없음</span><span class="sxs-lookup"><span data-stu-id="645fe-141">None</span></span>
<span data-ttu-id="645fe-142">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-142">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="645fe-143">참고</span><span class="sxs-lookup"><span data-stu-id="645fe-143">NOTES</span></span>

* <span data-ttu-id="645fe-144">Windows Vista 이상 버전의 windows 운영 체제에서 Restore-Computer 명령을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-144">To run a Restore-Computer command on Windows Vista and later versions of the Windows operating system, open Windows PowerShell by using the Run as administrator option.</span></span>
* <span data-ttu-id="645fe-145">이 cmdlet은 WMI(Windows Management Instrumentation) (WMI) **SystemRestore** 클래스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="645fe-145">This cmdlet uses the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

## <span data-ttu-id="645fe-146">관련 링크</span><span class="sxs-lookup"><span data-stu-id="645fe-146">RELATED LINKS</span></span>

[<span data-ttu-id="645fe-147">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="645fe-147">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="645fe-148">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="645fe-148">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="645fe-149">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="645fe-149">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="645fe-150">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="645fe-150">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="645fe-151">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="645fe-151">Restart-Computer</span></span>](Restart-Computer.md)
