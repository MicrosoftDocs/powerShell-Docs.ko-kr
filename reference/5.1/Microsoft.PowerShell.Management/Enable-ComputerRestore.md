---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/enable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ComputerRestore
ms.openlocfilehash: f9616a7f9af4dd2fa45e150bb64eef65427b4947
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215490"
---
# <span data-ttu-id="5abb3-103">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="5abb3-103">Enable-ComputerRestore</span></span>

## <span data-ttu-id="5abb3-104">개요</span><span class="sxs-lookup"><span data-stu-id="5abb3-104">SYNOPSIS</span></span>
<span data-ttu-id="5abb3-105">지정된 파일 시스템 드라이브에서 시스템 복원 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-105">Enables the System Restore feature on the specified file system drive.</span></span>

## <span data-ttu-id="5abb3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5abb3-106">SYNTAX</span></span>

```
Enable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5abb3-107">설명</span><span class="sxs-lookup"><span data-stu-id="5abb3-107">DESCRIPTION</span></span>
<span data-ttu-id="5abb3-108">**Enable computerrestore** cmdlet은 하나 이상의 파일 시스템 드라이브에서 시스템 복원 기능을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-108">The **Enable-ComputerRestore** cmdlet turns on the System Restore feature on one or more file system drives.</span></span>
<span data-ttu-id="5abb3-109">그 결과 Restore-Computer cmdlet 같은 도구를 사용하여 컴퓨터를 이전 상태로 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-109">As a result, you can use tools, such as the Restore-Computer cmdlet, to restore the computer to a previous state.</span></span>

<span data-ttu-id="5abb3-110">시스템 복원은 이 기능을 사용할 수 있는 모든 드라이브에서 기본적으로 사용하도록 설정되지만 Disable-ComputerRestore cmdlet을 사용하는 등의 방법으로 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-110">By default, System Restore is enabled on all eligible drives, but you can disable it, such as by using the Disable-ComputerRestore cmdlet.</span></span>
<span data-ttu-id="5abb3-111">드라이브에서 시스템 복원을 사용하도록 설정하거나 다시 사용하도록 설정하려면 먼저 또는 동시에 시스템 드라이브에서 시스템 복원을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-111">To enable (or re-enable) System Restore on any drive, it must be enabled on the system drive, either first or concurrently.</span></span>
<span data-ttu-id="5abb3-112">각 드라이브의 시스템 복원 상태를 찾으려면 Rstrui.exe를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-112">To find the state of System Restore for each drive, use Rstrui.exe.</span></span>

<span data-ttu-id="5abb3-113">시스템 복원 지점과 ComputerRestore cmdlet은 Windows 7, Windows Vista 및 Windows XP와 같은 클라이언트 운영 체제에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-113">System restore points and the ComputerRestore cmdlets are supported only on client operating systems, such as Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="5abb3-114">예제</span><span class="sxs-lookup"><span data-stu-id="5abb3-114">EXAMPLES</span></span>

### <span data-ttu-id="5abb3-115">예 1: 지정한 드라이브에서 시스템 복원을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="5abb3-115">Example 1: Enable System Restore on the specified drive</span></span>

```
PS C:\> Enable-ComputerRestore -Drive "C:\"
```

<span data-ttu-id="5abb3-116">이 명령은 로컬 컴퓨터의 C: 드라이브에서 시스템 복원을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-116">This command enables System Restore on the C: drive of the local computer.</span></span>

### <span data-ttu-id="5abb3-117">예 2: 여러 드라이브에서 시스템 복원 사용</span><span class="sxs-lookup"><span data-stu-id="5abb3-117">Example 2: Enable System Restore on multiple drives</span></span>

```
PS C:\> Enable-ComputerRestore -Drive "C:\", "D:\"
```

<span data-ttu-id="5abb3-118">이 명령은 로컬 컴퓨터의 C: 및 D: 드라이브에서 시스템 복원을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-118">This command enables System Restore on the C: and D: drives of the local computer.</span></span>

## <span data-ttu-id="5abb3-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5abb3-119">PARAMETERS</span></span>

### <span data-ttu-id="5abb3-120">-드라이브</span><span class="sxs-lookup"><span data-stu-id="5abb3-120">-Drive</span></span>
<span data-ttu-id="5abb3-121">파일 시스템 드라이브를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-121">Specifies the file system drives.</span></span>
<span data-ttu-id="5abb3-122">하나 이상의 파일 시스템 드라이브 문자를 입력 합니다. 여기에는 각각 콜론과 백슬래시가 오고 따옴표 (예: C:\)로 묶여 있습니다. 또는 D:\.</span><span class="sxs-lookup"><span data-stu-id="5abb3-122">Enter one or more file system drive letters, each followed by a colon and a backslash and enclosed in quotation marks, such as C:\ or D:\.</span></span>
<span data-ttu-id="5abb3-123">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-123">This parameter is required.</span></span>

<span data-ttu-id="5abb3-124">드라이브가 로컬 컴퓨터에 매핑되어 있는 경우에도 이 cmdlet을 사용하여 원격 네트워크 드라이브에서 시스템 복원을 사용하도록 설정할 수 없으며 외부 드라이브와 같이 시스템 복원에 사용할 수 없는 드라이브에서는 시스템 복원을 사용하도록 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-124">You cannot use this cmdlet to enable System Restore on a remote network drive, even if the drive is mapped to the local computer, and you cannot enable System Restore on drives that are not eligible for System Restore, such as external drives.</span></span>

<span data-ttu-id="5abb3-125">드라이브에서 시스템 복원을 사용하도록 설정하려면 미리 또는 동시에 시스템 드라이브에서 시스템 복원을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-125">To enable System Restore on any drive, System Restore must be enabled on the system drive, either before or concurrently.</span></span>

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

### <span data-ttu-id="5abb3-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5abb3-126">-Confirm</span></span>
<span data-ttu-id="5abb3-127">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5abb3-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5abb3-128">-WhatIf</span></span>
<span data-ttu-id="5abb3-129">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5abb3-130">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5abb3-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5abb3-131">CommonParameters</span></span>
<span data-ttu-id="5abb3-132">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5abb3-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5abb3-133">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5abb3-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5abb3-134">입력</span><span class="sxs-lookup"><span data-stu-id="5abb3-134">INPUTS</span></span>

### <span data-ttu-id="5abb3-135">없음</span><span class="sxs-lookup"><span data-stu-id="5abb3-135">None</span></span>
<span data-ttu-id="5abb3-136">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-136">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="5abb3-137">출력</span><span class="sxs-lookup"><span data-stu-id="5abb3-137">OUTPUTS</span></span>

### <span data-ttu-id="5abb3-138">없음</span><span class="sxs-lookup"><span data-stu-id="5abb3-138">None</span></span>
<span data-ttu-id="5abb3-139">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-139">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5abb3-140">참고</span><span class="sxs-lookup"><span data-stu-id="5abb3-140">NOTES</span></span>

* <span data-ttu-id="5abb3-141">Windows Vista 이상 버전에서이 cmdlet을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-141">To run this cmdlet on Windows Vista and later versions of Windows, open Windows PowerShell with the Run as administrator option.</span></span>

  <span data-ttu-id="5abb3-142">시스템 복원에 적합 한 파일 시스템 드라이브를 찾으려면 제어판의 시스템에서 시스템 보호 탭을 참조 하세요. Windows PowerShell에서이 탭을 열려면를 입력 `SystemPropertiesProtection` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-142">To find the file system drives that are eligible for system restore, in System in Control Panel, see the System Protection tab. To open this tab in Windows PowerShell, type `SystemPropertiesProtection`.</span></span>

  <span data-ttu-id="5abb3-143">이 cmdlet은 WMI(Windows Management Instrumentation) (WMI) **SystemRestore** 클래스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5abb3-143">This cmdlet uses the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

*

## <span data-ttu-id="5abb3-144">관련 링크</span><span class="sxs-lookup"><span data-stu-id="5abb3-144">RELATED LINKS</span></span>

[<span data-ttu-id="5abb3-145">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="5abb3-145">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="5abb3-146">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="5abb3-146">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="5abb3-147">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="5abb3-147">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="5abb3-148">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="5abb3-148">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="5abb3-149">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="5abb3-149">Restore-Computer</span></span>](Restore-Computer.md)
