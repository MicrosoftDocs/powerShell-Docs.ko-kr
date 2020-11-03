---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-psdrive?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSDrive
ms.openlocfilehash: 6f34e670a29ee65e4a37314472f89c463f0a49ab
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216945"
---
# <span data-ttu-id="ee618-103">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="ee618-103">Remove-PSDrive</span></span>

## <span data-ttu-id="ee618-104">개요</span><span class="sxs-lookup"><span data-stu-id="ee618-104">SYNOPSIS</span></span>
<span data-ttu-id="ee618-105">임시 PowerShell 드라이브를 삭제 하 고 매핑된 네트워크 드라이브의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-105">Deletes temporary PowerShell drives and disconnects mapped network drives.</span></span>

## <span data-ttu-id="ee618-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ee618-106">SYNTAX</span></span>

### <span data-ttu-id="ee618-107">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="ee618-107">Name (Default)</span></span>

```
Remove-PSDrive [-Name] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ee618-108">LiteralName</span><span class="sxs-lookup"><span data-stu-id="ee618-108">LiteralName</span></span>

```
Remove-PSDrive [-LiteralName] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ee618-109">설명</span><span class="sxs-lookup"><span data-stu-id="ee618-109">DESCRIPTION</span></span>

<span data-ttu-id="ee618-110">Cmdlet은 `Remove-PSDrive` cmdlet을 사용 하 여 만든 임시 PowerShell 드라이브를 삭제 합니다 `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="ee618-110">The `Remove-PSDrive` cmdlet deletes temporary PowerShell drives that were created by using the `New-PSDrive` cmdlet.</span></span>

<span data-ttu-id="ee618-111">Windows PowerShell 3.0부터는 `Remove-PSDrive` 의 매개 변수를 사용 하 여 만든 드라이브를 비롯 하 여 매핑된 네트워크 드라이브의 연결을 끊습니다 `Persist` `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="ee618-111">Beginning in Windows PowerShell 3.0, `Remove-PSDrive` also disconnects mapped network drives, including, but not limited to, drives created by using the `Persist` parameter of `New-PSDrive`.</span></span>

<span data-ttu-id="ee618-112">`Remove-PSDrive` Windows 실제 또는 논리적 드라이브를 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-112">`Remove-PSDrive` cannot delete Windows physical or logical drives.</span></span>

<span data-ttu-id="ee618-113">Windows PowerShell 3.0부터 외부 드라이브가 컴퓨터에 연결 된 경우 PowerShell에서 자동으로 새 드라이브를 나타내는 PSDrive를 파일 시스템에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-113">Beginning in Windows PowerShell 3.0, when an external drive is connected to the computer, PowerShell automatically adds a PSDrive to the file system that represents the new drive.</span></span>
<span data-ttu-id="ee618-114">PowerShell을 다시 시작할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-114">You do not need to restart PowerShell.</span></span>
<span data-ttu-id="ee618-115">마찬가지로 컴퓨터에서 외부 드라이브의 연결이 끊어지면 PowerShell에서 제거 된 드라이브를 나타내는 PSDrive를 자동으로 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-115">Similarly, when an external drive is disconnected from the computer, PowerShell automatically deletes the PSDrive that represents the removed drive.</span></span>

## <span data-ttu-id="ee618-116">예제</span><span class="sxs-lookup"><span data-stu-id="ee618-116">EXAMPLES</span></span>

### <span data-ttu-id="ee618-117">예 1: 파일 시스템 드라이브 제거</span><span class="sxs-lookup"><span data-stu-id="ee618-117">Example 1: Remove a file system drive</span></span>

<span data-ttu-id="ee618-118">이 명령은 "smp"라는 임시 파일 시스템 드라이브를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-118">This command removes a temporary file system drive named "smp".</span></span>

```powershell
Remove-PSDrive -Name smp
```

### <span data-ttu-id="ee618-119">예 2: 매핑된 네트워크 드라이브 제거</span><span class="sxs-lookup"><span data-stu-id="ee618-119">Example 2: Remove mapped network drives</span></span>

<span data-ttu-id="ee618-120">이 명령은 `Remove-PSDrive` 를 사용 하 여 X: 및 S: 매핑된 네트워크 드라이브의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-120">This command uses `Remove-PSDrive` to disconnect the X: and S: mapped network drives.</span></span>

```powershell
Get-PSDrive X, S | Remove-PSDrive
```

## <span data-ttu-id="ee618-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ee618-121">PARAMETERS</span></span>

### <span data-ttu-id="ee618-122">-Force</span><span class="sxs-lookup"><span data-stu-id="ee618-122">-Force</span></span>

<span data-ttu-id="ee618-123">현재 PowerShell 드라이브를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-123">Removes the current PowerShell drive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee618-124">-LiteralName</span><span class="sxs-lookup"><span data-stu-id="ee618-124">-LiteralName</span></span>

<span data-ttu-id="ee618-125">드라이브의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-125">Specifies the name of the drive.</span></span>

<span data-ttu-id="ee618-126">**LiteralName** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-126">The value of **LiteralName** is used exactly as typed.</span></span>
<span data-ttu-id="ee618-127">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-127">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="ee618-128">이름에 이스케이프 문자가 포함된 경우 이름을 작은따옴표(')로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-128">If the name includes escape characters, enclose it in single quotation marks (').</span></span>
<span data-ttu-id="ee618-129">작은따옴표는 PowerShell이 어떤 문자도 이스케이프 시퀀스로 해석 하지 않도록 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-129">Single quotation marks instruct PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ee618-130">-Name</span><span class="sxs-lookup"><span data-stu-id="ee618-130">-Name</span></span>

<span data-ttu-id="ee618-131">제거할 드라이브의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-131">Specifies the names of the drives to remove.</span></span>
<span data-ttu-id="ee618-132">드라이브 이름 뒤에 콜론(:)을 입력하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="ee618-132">Do not type a colon (:) after the drive name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ee618-133">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="ee618-133">-PSProvider</span></span>

<span data-ttu-id="ee618-134">**Psprovider** 개체의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-134">Specifies an array of **PSProvider** objects.</span></span>
<span data-ttu-id="ee618-135">이 cmdlet은 지정 된 PowerShell 공급자와 연결 된 모든 드라이브를 제거 하 고 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-135">This cmdlet removes and disconnects all of the drives associated with the specified PowerShell provider.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ee618-136">-범위</span><span class="sxs-lookup"><span data-stu-id="ee618-136">-Scope</span></span>

<span data-ttu-id="ee618-137">드라이브의 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-137">Specifies a scope for the drive.</span></span>
<span data-ttu-id="ee618-138">이 매개 변수에 허용 되는 값은 전역, 로컬 및 스크립트 이거나 현재 범위를 기준으로 하는 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-138">The acceptable values for this parameter are: Global, Local, and Script, or a number relative to the current scope.</span></span> <span data-ttu-id="ee618-139">범위는 0에서 범위 수 까지입니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-139">Scopes number 0 through the number of scopes.</span></span> <span data-ttu-id="ee618-140">현재 범위 번호는 0이 고 해당 부모는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-140">The current scope number is 0 and its parent is 1.</span></span>
<span data-ttu-id="ee618-141">자세한 내용은 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ee618-141">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ee618-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ee618-142">-Confirm</span></span>

<span data-ttu-id="ee618-143">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ee618-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ee618-144">-WhatIf</span></span>

<span data-ttu-id="ee618-145">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-145">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ee618-146">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ee618-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ee618-147">CommonParameters</span></span>

<span data-ttu-id="ee618-148">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ee618-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ee618-149">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee618-149">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="ee618-150">입력</span><span class="sxs-lookup"><span data-stu-id="ee618-150">INPUTS</span></span>

### <span data-ttu-id="ee618-151">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="ee618-151">System.Management.Automation.PSDriveInfo</span></span>

<span data-ttu-id="ee618-152">Cmdlet 등의 드라이브 개체를 cmdlet으로 파이프 할 수 있습니다 `Get-PSDrive` `Remove-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="ee618-152">You can pipe a drive object, such as one from the `Get-PSDrive` cmdlet, to the `Remove-PSDrive` cmdlet.</span></span>

## <span data-ttu-id="ee618-153">출력</span><span class="sxs-lookup"><span data-stu-id="ee618-153">OUTPUTS</span></span>

### <span data-ttu-id="ee618-154">없음</span><span class="sxs-lookup"><span data-stu-id="ee618-154">None</span></span>

<span data-ttu-id="ee618-155">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-155">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="ee618-156">참고</span><span class="sxs-lookup"><span data-stu-id="ee618-156">NOTES</span></span>

- <span data-ttu-id="ee618-157">`Remove-PSDrive`Cmdlet은 PowerShell 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ee618-157">The `Remove-PSDrive` cmdlet is designed to work with the data exposed by any PowerShell provider.</span></span> <span data-ttu-id="ee618-158">세션의 공급자를 나열 하려면 cmdlet을 사용 합니다 `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="ee618-158">To list the providers in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="ee618-159">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee618-159">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="ee618-160">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ee618-160">RELATED LINKS</span></span>

[<span data-ttu-id="ee618-161">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="ee618-161">Get-PSDrive</span></span>](Get-PSDrive.md)

[<span data-ttu-id="ee618-162">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="ee618-162">New-PSDrive</span></span>](New-PSDrive.md)

[<span data-ttu-id="ee618-163">about_Providers</span><span class="sxs-lookup"><span data-stu-id="ee618-163">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
