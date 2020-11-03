---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Item
ms.openlocfilehash: c49cc60ec6ebf3f62a94f5511b55d578337be804
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214458"
---
# <span data-ttu-id="371f2-103">Set-Item</span><span class="sxs-lookup"><span data-stu-id="371f2-103">Set-Item</span></span>

## <span data-ttu-id="371f2-104">개요</span><span class="sxs-lookup"><span data-stu-id="371f2-104">SYNOPSIS</span></span>
<span data-ttu-id="371f2-105">항목의 값을 명령에 지정된 값으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-105">Changes the value of an item to the value specified in the command.</span></span>

## <span data-ttu-id="371f2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="371f2-106">SYNTAX</span></span>

### <span data-ttu-id="371f2-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="371f2-107">Path (Default)</span></span>

```
Set-Item [-Path] <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="371f2-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="371f2-108">LiteralPath</span></span>

```
Set-Item -LiteralPath <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="371f2-109">설명</span><span class="sxs-lookup"><span data-stu-id="371f2-109">DESCRIPTION</span></span>

<span data-ttu-id="371f2-110">`Set-Item`Cmdlet은 변수 또는 레지스트리 키와 같은 항목의 값을 명령에 지정 된 값으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-110">The `Set-Item` cmdlet changes the value of an item, such as a variable or registry key, to the value specified in the command.</span></span>

## <span data-ttu-id="371f2-111">예제</span><span class="sxs-lookup"><span data-stu-id="371f2-111">EXAMPLES</span></span>

### <span data-ttu-id="371f2-112">예제 1: 별칭 만들기</span><span class="sxs-lookup"><span data-stu-id="371f2-112">Example 1: Create an alias</span></span>

<span data-ttu-id="371f2-113">이 명령은 Notepad의 np 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-113">This command creates an alias of np for Notepad.</span></span>

```powershell
Set-Item -Path alias:np -Value "c:\windows\notepad.exe"
```

### <span data-ttu-id="371f2-114">예제 2: 환경 변수 값 변경</span><span class="sxs-lookup"><span data-stu-id="371f2-114">Example 2: Change the value of an environment variable</span></span>

<span data-ttu-id="371f2-115">이 명령은 UserRole 환경 변수의 값을 Administrator로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-115">This command changes the value of the UserRole environment variable to Administrator.</span></span>

```powershell
Set-Item -Path env:UserRole -Value "Administrator"
```

### <span data-ttu-id="371f2-116">예제 3: prompt 함수 수정</span><span class="sxs-lookup"><span data-stu-id="371f2-116">Example 3: Modify your prompt function</span></span>

<span data-ttu-id="371f2-117">이 명령은 경로 앞에 시간을 표시 하도록 prompt 함수를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-117">This command changes the prompt function so that it displays the time before the path.</span></span>

```powershell
Set-Item -Path function:prompt -Value {'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '}
```

### <span data-ttu-id="371f2-118">예제 4: 프롬프트 함수에 대 한 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="371f2-118">Example 4: Set options for your prompt function</span></span>

<span data-ttu-id="371f2-119">이 명령은 prompt 함수에 대 한 **AllScope** 및 **ReadOnly** 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-119">This command sets the **AllScope** and **ReadOnly** options for the prompt function.</span></span>
<span data-ttu-id="371f2-120">이 명령은의 **Options** 동적 매개 변수를 사용 `Set-Item` 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-120">This command uses the **Options** dynamic parameter of `Set-Item`.</span></span>
<span data-ttu-id="371f2-121">**옵션** 매개 변수는 `Set-Item` **별칭** 또는 **함수** 공급자와 함께 사용 하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-121">The **Options** parameter is available in `Set-Item` only when you use it with the **Alias** or **Function** provider.</span></span>

```powershell
Set-Item -Path function:prompt -Options "AllScope,ReadOnly"
```

## <span data-ttu-id="371f2-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="371f2-122">PARAMETERS</span></span>

### <span data-ttu-id="371f2-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="371f2-123">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="371f2-124">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-124">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="371f2-125">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-125">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="371f2-126">-제외</span><span class="sxs-lookup"><span data-stu-id="371f2-126">-Exclude</span></span>

<span data-ttu-id="371f2-127">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-127">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="371f2-128">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-128">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="371f2-129">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-129">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="371f2-130">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-130">Wildcard characters are permitted.</span></span> <span data-ttu-id="371f2-131">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="371f2-131">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="371f2-132">-Filter</span><span class="sxs-lookup"><span data-stu-id="371f2-132">-Filter</span></span>

<span data-ttu-id="371f2-133">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-133">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="371f2-134">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-134">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="371f2-135">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-135">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="371f2-136">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-136">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="371f2-137">-Force</span><span class="sxs-lookup"><span data-stu-id="371f2-137">-Force</span></span>

<span data-ttu-id="371f2-138">Cmdlet이 읽기 전용 별칭 또는 변수와 같이 다른 방법으로는 변경할 수 없는 항목을 강제로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-138">Forces the cmdlet to set items that cannot otherwise be changed, such as read-only alias or variables.</span></span> <span data-ttu-id="371f2-139">이 cmdlet은 지속적인 별칭 또는 변수를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-139">The cmdlet cannot change constant aliases or variables.</span></span>
<span data-ttu-id="371f2-140">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-140">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="371f2-141">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="371f2-141">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="371f2-142">*Force* 매개 변수를 사용 하는 경우에도 cmdlet은 보안 제한을 재정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-142">Even using the *Force* parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="371f2-143">-포함</span><span class="sxs-lookup"><span data-stu-id="371f2-143">-Include</span></span>

<span data-ttu-id="371f2-144">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-144">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="371f2-145">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-145">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="371f2-146">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-146">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="371f2-147">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-147">Wildcard characters are permitted.</span></span> <span data-ttu-id="371f2-148">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="371f2-148">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="371f2-149">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="371f2-149">-LiteralPath</span></span>

<span data-ttu-id="371f2-150">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-150">Specifies a path to one or more locations.</span></span> <span data-ttu-id="371f2-151">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-151">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="371f2-152">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-152">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="371f2-153">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="371f2-153">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="371f2-154">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-154">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="371f2-155">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="371f2-155">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="371f2-156">-PassThru</span><span class="sxs-lookup"><span data-stu-id="371f2-156">-PassThru</span></span>

<span data-ttu-id="371f2-157">항목을 나타내는 개체를 파이프라인으로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-157">Passes an object that represents the item to the pipeline.</span></span>
<span data-ttu-id="371f2-158">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-158">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="371f2-159">-Path</span><span class="sxs-lookup"><span data-stu-id="371f2-159">-Path</span></span>

<span data-ttu-id="371f2-160">항목 위치의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-160">Specifies a path of the location of the items.</span></span>
<span data-ttu-id="371f2-161">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-161">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="371f2-162">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="371f2-162">-UseTransaction</span></span>

<span data-ttu-id="371f2-163">활성 트랜잭션에 명령을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-163">Includes the command in the active transaction.</span></span>
<span data-ttu-id="371f2-164">이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-164">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="371f2-165">자세한 내용은 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="371f2-165">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="371f2-166">-Value</span><span class="sxs-lookup"><span data-stu-id="371f2-166">-Value</span></span>

<span data-ttu-id="371f2-167">항목의 새 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-167">Specifies a new value for the item.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="371f2-168">-Confirm</span><span class="sxs-lookup"><span data-stu-id="371f2-168">-Confirm</span></span>

<span data-ttu-id="371f2-169">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-169">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="371f2-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="371f2-170">-WhatIf</span></span>

<span data-ttu-id="371f2-171">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-171">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="371f2-172">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-172">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="371f2-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="371f2-173">CommonParameters</span></span>

<span data-ttu-id="371f2-174">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-174">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="371f2-175">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="371f2-175">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="371f2-176">입력</span><span class="sxs-lookup"><span data-stu-id="371f2-176">INPUTS</span></span>

### <span data-ttu-id="371f2-177">System.Object</span><span class="sxs-lookup"><span data-stu-id="371f2-177">System.Object</span></span>

<span data-ttu-id="371f2-178">항목의 새 값을 나타내는 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-178">You can pipe an object that represents the new value of the item to this cmdlet.</span></span>

## <span data-ttu-id="371f2-179">출력</span><span class="sxs-lookup"><span data-stu-id="371f2-179">OUTPUTS</span></span>

### <span data-ttu-id="371f2-180">없음 또는 새 항목 또는 변경 된 항목을 나타내는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-180">None or an object representing the new or changed item.</span></span>

<span data-ttu-id="371f2-181">이 cmdlet은 *PassThru* 매개 변수를 지정 하는 경우 항목을 나타내는 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-181">This cmdlet generates an object that represent the item, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="371f2-182">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-182">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="371f2-183">참고</span><span class="sxs-lookup"><span data-stu-id="371f2-183">NOTES</span></span>

- <span data-ttu-id="371f2-184">`Set-Item` 은 (는) PowerShell FileSystem 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-184">`Set-Item` is not supported by the PowerShell FileSystem provider.</span></span> <span data-ttu-id="371f2-185">파일 시스템에 있는 항목의 값을 변경 하려면 cmdlet을 사용 `Set-Content` 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-185">To change the values of items in the file system, use the `Set-Content` cmdlet.</span></span>
- <span data-ttu-id="371f2-186">및 레지스트리 드라이브에서 `HKLM:` `HKCU:` `Set-Item` 레지스트리 키의 (기본값) 값에 있는 데이터를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-186">In the Registry drives, `HKLM:` and `HKCU:`, `Set-Item` changes the data in the (Default) value of a registry key.</span></span>
  - <span data-ttu-id="371f2-187">레지스트리 키의 이름을 만들고 변경 하려면 `New-Item` 및 cmdlet을 사용 `Rename-Item` 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-187">To create and change the names of registry keys, use the `New-Item` and `Rename-Item` cmdlet.</span></span>
  - <span data-ttu-id="371f2-188">레지스트리 값의 이름과 데이터를 변경 하려면 `New-ItemProperty` , 및 cmdlet을 사용 `Set-ItemProperty` `Rename-ItemProperty` 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-188">To change the names and data in registry values, use the `New-ItemProperty`, `Set-ItemProperty`, and `Rename-ItemProperty` cmdlets.</span></span>
- <span data-ttu-id="371f2-189">`Set-Item` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-189">`Set-Item` is designed to work with the data exposed by any provider.</span></span>
  <span data-ttu-id="371f2-190">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PsProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="371f2-190">To list the providers available in your session, type `Get-PsProvider`.</span></span>
  <span data-ttu-id="371f2-191">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="371f2-191">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="371f2-192">관련 링크</span><span class="sxs-lookup"><span data-stu-id="371f2-192">RELATED LINKS</span></span>

[<span data-ttu-id="371f2-193">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="371f2-193">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="371f2-194">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="371f2-194">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="371f2-195">Get-Item</span><span class="sxs-lookup"><span data-stu-id="371f2-195">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="371f2-196">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="371f2-196">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="371f2-197">Move-Item</span><span class="sxs-lookup"><span data-stu-id="371f2-197">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="371f2-198">New-Item</span><span class="sxs-lookup"><span data-stu-id="371f2-198">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="371f2-199">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="371f2-199">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="371f2-200">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="371f2-200">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="371f2-201">about_Providers</span><span class="sxs-lookup"><span data-stu-id="371f2-201">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
