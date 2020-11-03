---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/disable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ComputerRestore
ms.openlocfilehash: 941829c3caa0f6bb2f5712dda9eb7d8c36908062
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215497"
---
# <span data-ttu-id="190d0-103">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="190d0-103">Disable-ComputerRestore</span></span>

## <span data-ttu-id="190d0-104">개요</span><span class="sxs-lookup"><span data-stu-id="190d0-104">SYNOPSIS</span></span>
<span data-ttu-id="190d0-105">지정된 파일 시스템 드라이브에서 시스템 복원 기능을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-105">Disables the System Restore feature on the specified file system drive.</span></span>

## <span data-ttu-id="190d0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="190d0-106">SYNTAX</span></span>

```
Disable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="190d0-107">설명</span><span class="sxs-lookup"><span data-stu-id="190d0-107">DESCRIPTION</span></span>
<span data-ttu-id="190d0-108">**Disable ComputerRestore** cmdlet은 하나 이상의 파일 시스템 드라이브에서 시스템 복원 기능을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-108">The **Disable-ComputerRestore** cmdlet turns off the System Restore feature on one or more file system drives.</span></span>
<span data-ttu-id="190d0-109">따라서 컴퓨터를 복원하려는 시도가 지정된 드라이브에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-109">As a result, attempts to restore the computer do not affect the specified drive.</span></span>

<span data-ttu-id="190d0-110">모든 드라이브에서 시스템 복원을 사용하지 않도록 설정하려면 먼저 또는 동시에 시스템 드라이브에서 사용하지 않도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-110">To disable System Restore on any drive, it must be disabled on the system drive, either first or concurrently.</span></span>

<span data-ttu-id="190d0-111">시스템 복원을 사용하도록 다시 설정하려면 Enable-ComputerRestore cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-111">To re-enable System Restore, use the Enable-ComputerRestore cmdlet.</span></span>
<span data-ttu-id="190d0-112">각 드라이브의 시스템 복원 상태를 찾으려면 Rstrui.exe를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-112">To find the state of System Restore for each drive, use Rstrui.exe.</span></span>

<span data-ttu-id="190d0-113">시스템 복원 지점과 ComputerRestore cmdlet은 Windows 7, Windows Vista 및 Windows XP와 같은 클라이언트 운영 체제에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-113">System restore points and the ComputerRestore cmdlets are supported only on client operating systems, such as Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="190d0-114">예제</span><span class="sxs-lookup"><span data-stu-id="190d0-114">EXAMPLES</span></span>

### <span data-ttu-id="190d0-115">예 1: 지정한 드라이브에서 시스템 복원을 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="190d0-115">Example 1: Disable System Restore on the specified drive</span></span>

```
PS C:\> Disable-ComputerRestore -Drive "C:\"
```

<span data-ttu-id="190d0-116">이 명령은 C: 드라이브에서 시스템 복원을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-116">This command disables System Restore on the C: drive.</span></span>

### <span data-ttu-id="190d0-117">예 2: 여러 드라이브에서 시스템 복원을 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="190d0-117">Example 2: Disable System Restore on multiple drives</span></span>

```
PS C:\> Disable-ComputerRestore "C:\", "D:\"
```

<span data-ttu-id="190d0-118">이 명령은 C: 및 D: 드라이브에서 시스템 복원을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-118">This command disables System Restore on the C: and D: drives.</span></span>
<span data-ttu-id="190d0-119">이 명령은 *drive* 매개 변수를 사용 하지만 드라이브 매개 변수 이름은 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-119">The command uses the *Drive* parameter, but it omits the Drive parameter name.</span></span>

## <span data-ttu-id="190d0-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="190d0-120">PARAMETERS</span></span>

### <span data-ttu-id="190d0-121">-드라이브</span><span class="sxs-lookup"><span data-stu-id="190d0-121">-Drive</span></span>
<span data-ttu-id="190d0-122">파일 시스템 드라이브를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-122">Specifies the file system drives.</span></span>
<span data-ttu-id="190d0-123">하나 이상의 파일 시스템 드라이브 문자를 입력 합니다. 여기에는 각각 콜론과 백슬래시가 오고 따옴표 (예: C:\)로 묶여 있습니다. 또는 D:\.</span><span class="sxs-lookup"><span data-stu-id="190d0-123">Enter one or more file system drive letters, each followed by a colon and a backslash and enclosed in quotation marks, such as C:\ or D:\.</span></span>
<span data-ttu-id="190d0-124">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-124">This parameter is required.</span></span>

<span data-ttu-id="190d0-125">이 cmdlet을 사용하면 드라이브가 로컬 컴퓨터에 매핑된 경우에도 원격 네트워크 드라이브에서 시스템 복원을 사용하지 않도록 설정할 수 없으며, 외장형 드라이브와 같이 시스템 복원에 적합하지 않은 드라이브에서 시스템 복원을 사용하지 않도록 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-125">You cannot use this cmdlet to disable System Restore on a remote network drive, even if the drive is mapped to the local computer, and you cannot disable System Restore on drives that are not eligible for System Restore, such as external drives.</span></span>

<span data-ttu-id="190d0-126">모든 드라이브에서 시스템 복원을 사용하지 않도록 설정하려면 먼저 또는 동시에 시스템 드라이브에서 시스템 복원을 사용하지 않도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-126">To disable System Restore on any drive, System Restore must be disabled on the system drive, either before or concurrently.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="190d0-127">-Confirm</span><span class="sxs-lookup"><span data-stu-id="190d0-127">-Confirm</span></span>
<span data-ttu-id="190d0-128">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-128">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="190d0-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="190d0-129">-WhatIf</span></span>
<span data-ttu-id="190d0-130">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-130">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="190d0-131">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-131">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="190d0-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="190d0-132">CommonParameters</span></span>
<span data-ttu-id="190d0-133">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="190d0-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="190d0-134">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="190d0-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="190d0-135">입력</span><span class="sxs-lookup"><span data-stu-id="190d0-135">INPUTS</span></span>

### <span data-ttu-id="190d0-136">없음</span><span class="sxs-lookup"><span data-stu-id="190d0-136">None</span></span>
<span data-ttu-id="190d0-137">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-137">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="190d0-138">출력</span><span class="sxs-lookup"><span data-stu-id="190d0-138">OUTPUTS</span></span>

### <span data-ttu-id="190d0-139">없음</span><span class="sxs-lookup"><span data-stu-id="190d0-139">None</span></span>
<span data-ttu-id="190d0-140">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-140">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="190d0-141">참고</span><span class="sxs-lookup"><span data-stu-id="190d0-141">NOTES</span></span>

* <span data-ttu-id="190d0-142">Windows Vista 이상 버전에서이 cmdlet을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-142">To run this cmdlet on Windows Vista and later versions of Windows, open Windows PowerShell with the Run as administrator option.</span></span>

  <span data-ttu-id="190d0-143">시스템 복원에 적합 한 파일 시스템 드라이브를 찾으려면 제어판의 시스템에서 시스템 보호 탭을 참조 하세요. Windows PowerShell에서이 탭을 열려면를 입력 `SystemPropertiesProtection` 합니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-143">To find the file system drives that are eligible for system restore, in System in Control Panel, see the System Protection tab. To open this tab in Windows PowerShell, type `SystemPropertiesProtection`.</span></span>

  <span data-ttu-id="190d0-144">이 cmdlet은 WMI(Windows Management Instrumentation) (WMI) **SystemRestore** 클래스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="190d0-144">This cmdlet uses the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

*

## <span data-ttu-id="190d0-145">관련 링크</span><span class="sxs-lookup"><span data-stu-id="190d0-145">RELATED LINKS</span></span>

[<span data-ttu-id="190d0-146">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="190d0-146">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="190d0-147">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="190d0-147">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="190d0-148">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="190d0-148">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="190d0-149">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="190d0-149">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="190d0-150">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="190d0-150">Restore-Computer</span></span>](Restore-Computer.md)
