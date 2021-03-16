---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 870d8e9797ff2cfce14034706f704c0e1c954fc2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601065"
---
# <span data-ttu-id="31ee2-102">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="31ee2-102">Remove-ItemProperty</span></span>

## <span data-ttu-id="31ee2-103">개요</span><span class="sxs-lookup"><span data-stu-id="31ee2-103">SYNOPSIS</span></span>
<span data-ttu-id="31ee2-104">항목에서 속성 및 해당 값을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-104">Deletes the property and its value from an item.</span></span>

## <span data-ttu-id="31ee2-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="31ee2-105">SYNTAX</span></span>

### <span data-ttu-id="31ee2-106">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="31ee2-106">Path (Default)</span></span>

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="31ee2-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="31ee2-107">LiteralPath</span></span>

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="31ee2-108">설명</span><span class="sxs-lookup"><span data-stu-id="31ee2-108">DESCRIPTION</span></span>

<span data-ttu-id="31ee2-109">`Remove-ItemProperty`Cmdlet은 항목에서 속성 및 해당 값을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-109">The `Remove-ItemProperty` cmdlet deletes a property and its value from an item.</span></span>
<span data-ttu-id="31ee2-110">이 cmdlet을 사용하여 레지스트리 값과 이 값에 저장된 데이터를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-110">You can use it to delete registry values and the data that they store.</span></span>

## <span data-ttu-id="31ee2-111">예제</span><span class="sxs-lookup"><span data-stu-id="31ee2-111">EXAMPLES</span></span>

### <span data-ttu-id="31ee2-112">예제 1: 레지스트리 값 삭제</span><span class="sxs-lookup"><span data-stu-id="31ee2-112">Example 1: Delete a registry value</span></span>

<span data-ttu-id="31ee2-113">이 명령은 레지스트리 키의 "SmpApplication" 하위 키에서 "SmpProperty" 레지스트리 값과 해당 데이터를 삭제 `HKEY_LOCAL_MACHINE\Software` 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-113">This command deletes the "SmpProperty" registry value, and its data, from the "SmpApplication" subkey of the `HKEY_LOCAL_MACHINE\Software` registry key.</span></span>

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

<span data-ttu-id="31ee2-114">명령은 파일 시스템 드라이브 ()에서 실행 되기 때문에 `PS C:\>` 드라이브, `HKLM:` 및 "소프트웨어" 키를 포함 하 여 "SmpApplication" 하위 키의 정규화 된 경로를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-114">Because the command is issued from a file system drive (`PS C:\>`), it includes the fully qualified path of the "SmpApplication" subkey, including the drive, `HKLM:`, and the "Software" key.</span></span>

### <span data-ttu-id="31ee2-115">예 2: HKCU 위치에서 레지스트리 값 삭제</span><span class="sxs-lookup"><span data-stu-id="31ee2-115">Example 2: Delete a registry value from the HKCU location</span></span>

<span data-ttu-id="31ee2-116">이러한 명령은 "HKEY_CURRENT_USER\Software\MyCompany"의 "MyApp" 하위 키에서 "Options" 레지스트리 값과 해당 데이터를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-116">These commands delete the "Options" registry value, and its data, from the "MyApp" subkey of "HKEY_CURRENT_USER\Software\MyCompany".</span></span>

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

<span data-ttu-id="31ee2-117">첫 번째 명령은 cmdlet을 사용 하 여 `Set-Location` 현재 위치를 **HKEY_CURRENT_USER** 드라이브 ( `HKCU:` ) 및 하위 키로 변경 합니다 `Software\MyCompany\MyApp` .</span><span class="sxs-lookup"><span data-stu-id="31ee2-117">The first command uses the `Set-Location` cmdlet to change the current location to the **HKEY_CURRENT_USER** drive (`HKCU:`) and the `Software\MyCompany\MyApp` subkey.</span></span>

<span data-ttu-id="31ee2-118">두 번째 명령은를 사용 하 여 " `Remove-ItemProperty` MyApp" 하위 키에서 "Options" 레지스트리 값과 해당 데이터를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-118">The second command uses `Remove-ItemProperty` to remove the "Options" registry value, and its data, from the "MyApp" subkey.</span></span> <span data-ttu-id="31ee2-119">**Path** 가 필요 하기 때문에 명령은 점 ()을 사용 `.` 하 여 현재 위치를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-119">Because **Path** is required, the command uses a dot (`.`) to indicate the current location.</span></span> <span data-ttu-id="31ee2-120">**Confirm** 매개 변수는 값을 삭제 하기 전에 사용자에 게 메시지를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-120">The **Confirm** parameter requests a user prompt before deleting the value.</span></span>

### <span data-ttu-id="31ee2-121">예제 3: 파이프라인을 사용 하 여 레지스트리 값 제거</span><span class="sxs-lookup"><span data-stu-id="31ee2-121">Example 3: Remove a registry value by using the pipeline</span></span>

<span data-ttu-id="31ee2-122">이 명령은 레지스트리 키에서 "NoOfEmployees" 레지스트리 값과 해당 데이터를 삭제 `HKLM\Software\MyCompany` 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-122">This command deletes the "NoOfEmployees" registry value, and its data, from the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
```

<span data-ttu-id="31ee2-123">이 명령은 cmdlet을 사용 하 여 `Get-Item` 레지스트리 키를 나타내는 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-123">The command uses the `Get-Item` cmdlet to get an item that represents the registry key.</span></span>
<span data-ttu-id="31ee2-124">파이프라인 연산자 ()를 사용 하 여 `|` 개체를로 보냅니다 `Remove-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="31ee2-124">It uses a pipeline operator (`|`) to send the object to `Remove-ItemProperty`.</span></span>
<span data-ttu-id="31ee2-125">그런 다음의 **name** 매개 변수를 사용 하 여 `Remove-ItemProperty` 레지스트리 값의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-125">Then, it uses the **Name** parameter of `Remove-ItemProperty` to specify the name of the registry value.</span></span>

## <span data-ttu-id="31ee2-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="31ee2-126">PARAMETERS</span></span>

### <span data-ttu-id="31ee2-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="31ee2-127">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="31ee2-128">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-128">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="31ee2-129">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-129">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="31ee2-130">-제외</span><span class="sxs-lookup"><span data-stu-id="31ee2-130">-Exclude</span></span>

<span data-ttu-id="31ee2-131">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-131">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="31ee2-132">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-132">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="31ee2-133">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-133">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="31ee2-134">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-134">Wildcard characters are permitted.</span></span> <span data-ttu-id="31ee2-135">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="31ee2-135">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="31ee2-136">-Filter</span><span class="sxs-lookup"><span data-stu-id="31ee2-136">-Filter</span></span>

<span data-ttu-id="31ee2-137">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-137">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="31ee2-138">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-138">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="31ee2-139">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-139">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="31ee2-140">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-140">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="31ee2-141">-Force</span><span class="sxs-lookup"><span data-stu-id="31ee2-141">-Force</span></span>

<span data-ttu-id="31ee2-142">Cmdlet이 다른 방법으로는 사용자가 액세스할 수 없는 개체의 속성을 강제로 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-142">Forces the cmdlet to remove a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="31ee2-143">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-143">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="31ee2-144">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31ee2-144">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="31ee2-145">-포함</span><span class="sxs-lookup"><span data-stu-id="31ee2-145">-Include</span></span>

<span data-ttu-id="31ee2-146">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-146">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="31ee2-147">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-147">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="31ee2-148">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-148">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="31ee2-149">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-149">Wildcard characters are permitted.</span></span> <span data-ttu-id="31ee2-150">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="31ee2-150">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="31ee2-151">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="31ee2-151">-LiteralPath</span></span>

<span data-ttu-id="31ee2-152">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-152">Specifies a path to one or more locations.</span></span> <span data-ttu-id="31ee2-153">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-153">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="31ee2-154">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-154">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="31ee2-155">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="31ee2-155">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="31ee2-156">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-156">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="31ee2-157">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="31ee2-157">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="31ee2-158">-Name</span><span class="sxs-lookup"><span data-stu-id="31ee2-158">-Name</span></span>

<span data-ttu-id="31ee2-159">제거할 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-159">Specifies the names of the properties to remove.</span></span>
<span data-ttu-id="31ee2-160">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-160">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="31ee2-161">-Path</span><span class="sxs-lookup"><span data-stu-id="31ee2-161">-Path</span></span>

<span data-ttu-id="31ee2-162">속성이 제거 되는 항목의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-162">Specifies the path of the item whose properties are being removed.</span></span>
<span data-ttu-id="31ee2-163">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-163">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="31ee2-164">-Confirm</span><span class="sxs-lookup"><span data-stu-id="31ee2-164">-Confirm</span></span>

<span data-ttu-id="31ee2-165">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-165">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="31ee2-166">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="31ee2-166">-WhatIf</span></span>

<span data-ttu-id="31ee2-167">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-167">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="31ee2-168">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-168">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="31ee2-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="31ee2-169">CommonParameters</span></span>

<span data-ttu-id="31ee2-170">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-170">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="31ee2-171">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31ee2-171">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="31ee2-172">입력</span><span class="sxs-lookup"><span data-stu-id="31ee2-172">INPUTS</span></span>

### <span data-ttu-id="31ee2-173">System.String</span><span class="sxs-lookup"><span data-stu-id="31ee2-173">System.String</span></span>

<span data-ttu-id="31ee2-174">경로를 포함 하지만 리터럴 경로를 포함 하지 않는 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-174">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="31ee2-175">출력</span><span class="sxs-lookup"><span data-stu-id="31ee2-175">OUTPUTS</span></span>

### <span data-ttu-id="31ee2-176">없음</span><span class="sxs-lookup"><span data-stu-id="31ee2-176">None</span></span>

<span data-ttu-id="31ee2-177">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-177">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="31ee2-178">참고</span><span class="sxs-lookup"><span data-stu-id="31ee2-178">NOTES</span></span>

- <span data-ttu-id="31ee2-179">PowerShell 레지스트리 공급자에서 레지스트리 값은 레지스트리 키 또는 하위 키의 속성으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-179">In the PowerShell Registry provider, registry values are considered to be properties of a registry key or subkey.</span></span> <span data-ttu-id="31ee2-180">**Get-itemproperty** cmdlet을 사용 하 여 이러한 값을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-180">You can use the **ItemProperty** cmdlets to manage these values.</span></span>
- <span data-ttu-id="31ee2-181">`Remove-ItemProperty` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-181">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="31ee2-182">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="31ee2-182">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="31ee2-183">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31ee2-183">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="31ee2-184">관련 링크</span><span class="sxs-lookup"><span data-stu-id="31ee2-184">RELATED LINKS</span></span>

[<span data-ttu-id="31ee2-185">Get-Item</span><span class="sxs-lookup"><span data-stu-id="31ee2-185">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="31ee2-186">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="31ee2-186">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="31ee2-187">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="31ee2-187">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="31ee2-188">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="31ee2-188">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="31ee2-189">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="31ee2-189">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="31ee2-190">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="31ee2-190">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="31ee2-191">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="31ee2-191">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="31ee2-192">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="31ee2-192">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="31ee2-193">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="31ee2-193">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="31ee2-194">Set-Location</span><span class="sxs-lookup"><span data-stu-id="31ee2-194">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="31ee2-195">about_Providers</span><span class="sxs-lookup"><span data-stu-id="31ee2-195">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
