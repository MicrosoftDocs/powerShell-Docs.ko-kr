---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 9ae9c0e7c17a6a63da5487cce138ddce129b975b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214546"
---
# <span data-ttu-id="c2dbd-103">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c2dbd-103">Remove-ItemProperty</span></span>

## <span data-ttu-id="c2dbd-104">개요</span><span class="sxs-lookup"><span data-stu-id="c2dbd-104">SYNOPSIS</span></span>
<span data-ttu-id="c2dbd-105">항목에서 속성 및 해당 값을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-105">Deletes the property and its value from an item.</span></span>

## <span data-ttu-id="c2dbd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c2dbd-106">SYNTAX</span></span>

### <span data-ttu-id="c2dbd-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="c2dbd-107">Path (Default)</span></span>

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="c2dbd-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c2dbd-108">LiteralPath</span></span>

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="c2dbd-109">설명</span><span class="sxs-lookup"><span data-stu-id="c2dbd-109">DESCRIPTION</span></span>

<span data-ttu-id="c2dbd-110">`Remove-ItemProperty`Cmdlet은 항목에서 속성 및 해당 값을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-110">The `Remove-ItemProperty` cmdlet deletes a property and its value from an item.</span></span>
<span data-ttu-id="c2dbd-111">이 cmdlet을 사용하여 레지스트리 값과 이 값에 저장된 데이터를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-111">You can use it to delete registry values and the data that they store.</span></span>

## <span data-ttu-id="c2dbd-112">예제</span><span class="sxs-lookup"><span data-stu-id="c2dbd-112">EXAMPLES</span></span>

### <span data-ttu-id="c2dbd-113">예제 1: 레지스트리 값 삭제</span><span class="sxs-lookup"><span data-stu-id="c2dbd-113">Example 1: Delete a registry value</span></span>

<span data-ttu-id="c2dbd-114">이 명령은 "HKEY_LOCAL_MACHINE\Software" 레지스트리 키의 "SmpApplication" 하위 키에서 "SmpProperty" 레지스트리 값과 해당 데이터를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-114">This command deletes the "SmpProperty" registry value, and its data, from the "SmpApplication" subkey of the "HKEY_LOCAL_MACHINE\Software" registry key.</span></span>

<span data-ttu-id="c2dbd-115">명령은 파일 시스템 드라이브 ()에서 실행 되기 때문에 `PS C:\>` 드라이브, `HKLM:` 및 "소프트웨어" 키를 포함 하 여 "SmpApplication" 하위 키의 정규화 된 경로를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-115">Because the command is issued from a file system drive (`PS C:\>`), it includes the fully qualified path of the "SmpApplication" subkey, including the drive, `HKLM:`, and the "Software" key.</span></span>

<span data-ttu-id="c2dbd-116">**Name** 매개 변수를 사용 하 여 삭제할 레지스트리 값을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-116">It uses the **Name** parameter to identify the registry value that is being deleted.</span></span>

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

### <span data-ttu-id="c2dbd-117">예 2: HKCU 위치에서 레지스트리 값 삭제</span><span class="sxs-lookup"><span data-stu-id="c2dbd-117">Example 2: Delete a registry value from the HKCU location</span></span>

<span data-ttu-id="c2dbd-118">이러한 명령은 "HKEY_CURRENT_USER\Software\MyCompany"의 "MyApp" 하위 키에서 "Options" 레지스트리 값과 해당 데이터를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-118">These commands delete the "Options" registry value, and its data, from the "MyApp" subkey of "HKEY_CURRENT_USER\Software\MyCompany".</span></span>

<span data-ttu-id="c2dbd-119">첫 번째 명령은 cmdlet을 사용 하 여 `Set-Location` 현재 위치를 **HKEY_CURRENT_USER** 드라이브 ( `HKCU:` ) 및 "Software\MyCompany\MyApp" 하위 키로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-119">The first command uses the `Set-Location` cmdlet to change the current location to the **HKEY_CURRENT_USER** drive (`HKCU:`) and the "Software\MyCompany\MyApp" subkey.</span></span>

<span data-ttu-id="c2dbd-120">두 번째 명령은를 사용 하 여 " `Remove-ItemProperty` MyApp" 하위 키에서 "Options" 레지스트리 값과 해당 데이터를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-120">The second command uses `Remove-ItemProperty` to remove the "Options" registry value, and its data, from the "MyApp" subkey.</span></span>
<span data-ttu-id="c2dbd-121">**Path** 가 필요 하기 때문에 명령은 점 ('. ')을 사용 하 여 현재 위치를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-121">Because **Path** is required, the command uses a dot ('.') to indicate the current location.</span></span>
<span data-ttu-id="c2dbd-122">**Name** 을 사용 하 여 삭제할 레지스트리 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-122">It uses **Name** to specify which registry value to delete.</span></span>
<span data-ttu-id="c2dbd-123">**Confirm** 매개 변수를 사용 하 여 값을 삭제 하기 전에 사용자 프롬프트를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-123">It uses the **Confirm** parameter to request a user prompt before deleting the value.</span></span>

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

### <span data-ttu-id="c2dbd-124">예제 3: 파이프라인을 사용 하 여 레지스트리 값 제거</span><span class="sxs-lookup"><span data-stu-id="c2dbd-124">Example 3: Remove a registry value by using the pipeline</span></span>

<span data-ttu-id="c2dbd-125">이 명령은 "HKLM\Software\MyCompany" 레지스트리 키에서 "NoOfEmployees" 레지스트리 값과 해당 데이터를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-125">This command deletes the "NoOfEmployees" registry value, and its data, from the "HKLM\Software\MyCompany" registry key.</span></span>

<span data-ttu-id="c2dbd-126">이 명령은 cmdlet을 사용 하 여 `Get-Item` 레지스트리 키를 나타내는 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-126">The command uses the `Get-Item` cmdlet to get an item that represents the registry key.</span></span>
<span data-ttu-id="c2dbd-127">파이프라인 연산자 ()를 사용 하 여 `|` 개체를로 보냅니다 `Remove-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="c2dbd-127">It uses a pipeline operator (`|`) to send the object to `Remove-ItemProperty`.</span></span>
<span data-ttu-id="c2dbd-128">그런 다음의 **name** 매개 변수를 사용 하 여 `Remove-ItemProperty` 레지스트리 값의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-128">Then, it uses the **Name** parameter of `Remove-ItemProperty` to specify the name of the registry value.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
```

## <span data-ttu-id="c2dbd-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c2dbd-129">PARAMETERS</span></span>

### <span data-ttu-id="c2dbd-130">-Credential</span><span class="sxs-lookup"><span data-stu-id="c2dbd-130">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="c2dbd-131">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-131">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="c2dbd-132">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-132">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c2dbd-133">-제외</span><span class="sxs-lookup"><span data-stu-id="c2dbd-133">-Exclude</span></span>

<span data-ttu-id="c2dbd-134">이 cmdlet이 생략 하는 항목을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-134">Specifies items that this cmdlet omits.</span></span>
<span data-ttu-id="c2dbd-135">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-135">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="c2dbd-136">경로 요소 또는 패턴(예: "\*.txt")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-136">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="c2dbd-137">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-137">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c2dbd-138">-Filter</span><span class="sxs-lookup"><span data-stu-id="c2dbd-138">-Filter</span></span>

<span data-ttu-id="c2dbd-139">공급자의 형식 또는 언어로 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-139">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="c2dbd-140">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-140">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="c2dbd-141">와일드 카드 문자를 포함 한 필터 구문은 공급자에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-141">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="c2dbd-142">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-142">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c2dbd-143">-Force</span><span class="sxs-lookup"><span data-stu-id="c2dbd-143">-Force</span></span>

<span data-ttu-id="c2dbd-144">Cmdlet이 다른 방법으로는 사용자가 액세스할 수 없는 개체의 속성을 강제로 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-144">Forces the cmdlet to remove a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="c2dbd-145">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-145">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="c2dbd-146">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-146">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="c2dbd-147">-포함</span><span class="sxs-lookup"><span data-stu-id="c2dbd-147">-Include</span></span>

<span data-ttu-id="c2dbd-148">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-148">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="c2dbd-149">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-149">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="c2dbd-150">경로 요소 또는 패턴(예: "\*.txt")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-150">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="c2dbd-151">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-151">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c2dbd-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c2dbd-152">-LiteralPath</span></span>

<span data-ttu-id="c2dbd-153">속성의 현재 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-153">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="c2dbd-154">**Path** 매개 변수와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-154">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="c2dbd-155">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-155">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="c2dbd-156">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-156">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="c2dbd-157">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-157">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c2dbd-158">-Name</span><span class="sxs-lookup"><span data-stu-id="c2dbd-158">-Name</span></span>

<span data-ttu-id="c2dbd-159">제거할 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-159">Specifies the names of the properties to remove.</span></span>
<span data-ttu-id="c2dbd-160">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-160">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="c2dbd-161">-Path</span><span class="sxs-lookup"><span data-stu-id="c2dbd-161">-Path</span></span>

<span data-ttu-id="c2dbd-162">속성이 제거 되는 항목의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-162">Specifies the path of the item whose properties are being removed.</span></span>
<span data-ttu-id="c2dbd-163">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-163">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="c2dbd-164">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="c2dbd-164">-UseTransaction</span></span>

<span data-ttu-id="c2dbd-165">활성 트랜잭션에 명령을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-165">Includes the command in the active transaction.</span></span>
<span data-ttu-id="c2dbd-166">이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-166">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="c2dbd-167">자세한 내용은 about_Transactions를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-167">For more information, see about_Transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c2dbd-168">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c2dbd-168">-Confirm</span></span>

<span data-ttu-id="c2dbd-169">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-169">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c2dbd-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c2dbd-170">-WhatIf</span></span>

<span data-ttu-id="c2dbd-171">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-171">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c2dbd-172">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-172">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c2dbd-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c2dbd-173">CommonParameters</span></span>

<span data-ttu-id="c2dbd-174">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-174">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="c2dbd-175">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-175">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c2dbd-176">입력</span><span class="sxs-lookup"><span data-stu-id="c2dbd-176">INPUTS</span></span>

### <span data-ttu-id="c2dbd-177">System.String</span><span class="sxs-lookup"><span data-stu-id="c2dbd-177">System.String</span></span>

<span data-ttu-id="c2dbd-178">경로를 포함 하지만 리터럴 경로를 포함 하지 않는 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-178">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="c2dbd-179">출력</span><span class="sxs-lookup"><span data-stu-id="c2dbd-179">OUTPUTS</span></span>

### <span data-ttu-id="c2dbd-180">없음</span><span class="sxs-lookup"><span data-stu-id="c2dbd-180">None</span></span>

<span data-ttu-id="c2dbd-181">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-181">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="c2dbd-182">참고</span><span class="sxs-lookup"><span data-stu-id="c2dbd-182">NOTES</span></span>

<span data-ttu-id="c2dbd-183">PowerShell 레지스트리 공급자에서 레지스트리 값은 레지스트리 키 또는 하위 키의 속성으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-183">In the PowerShell Registry provider, registry values are considered to be properties of a registry key or subkey.</span></span> <span data-ttu-id="c2dbd-184">**Get-itemproperty** cmdlet을 사용 하 여 이러한 값을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-184">You can use the **ItemProperty** cmdlets to manage these values.</span></span>

<span data-ttu-id="c2dbd-185">`Remove-ItemProperty` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-185">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="c2dbd-186">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-186">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="c2dbd-187">자세한 내용은 About_Providers를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c2dbd-187">For more information, see about_Providers.</span></span>

## <span data-ttu-id="c2dbd-188">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c2dbd-188">RELATED LINKS</span></span>

[<span data-ttu-id="c2dbd-189">Get-Item</span><span class="sxs-lookup"><span data-stu-id="c2dbd-189">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="c2dbd-190">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c2dbd-190">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="c2dbd-191">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c2dbd-191">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="c2dbd-192">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c2dbd-192">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="c2dbd-193">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c2dbd-193">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="c2dbd-194">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c2dbd-194">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="c2dbd-195">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="c2dbd-195">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="c2dbd-196">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c2dbd-196">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="c2dbd-197">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c2dbd-197">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="c2dbd-198">about_Providers</span><span class="sxs-lookup"><span data-stu-id="c2dbd-198">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
