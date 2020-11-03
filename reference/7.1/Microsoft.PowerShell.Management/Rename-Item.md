---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Item
ms.openlocfilehash: b5dfd3e55ceadf4141e977f0fb879ba5d05538f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211521"
---
# <span data-ttu-id="72bf3-103">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="72bf3-103">Rename-Item</span></span>

## <span data-ttu-id="72bf3-104">개요</span><span class="sxs-lookup"><span data-stu-id="72bf3-104">SYNOPSIS</span></span>
<span data-ttu-id="72bf3-105">PowerShell 공급자 네임 스페이스에 있는 항목의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-105">Renames an item in a PowerShell provider namespace.</span></span>

## <span data-ttu-id="72bf3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="72bf3-106">SYNTAX</span></span>

### <span data-ttu-id="72bf3-107">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="72bf3-107">ByPath (Default)</span></span>

```
Rename-Item [-Path] <String> [-NewName] <String> [-Force] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="72bf3-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="72bf3-108">ByLiteralPath</span></span>

```
Rename-Item -LiteralPath <String> [-NewName] <String> [-Force] [-PassThru]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="72bf3-109">설명</span><span class="sxs-lookup"><span data-stu-id="72bf3-109">DESCRIPTION</span></span>

<span data-ttu-id="72bf3-110">`Rename-Item`Cmdlet은 지정 된 항목의 이름을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-110">The `Rename-Item` cmdlet changes the name of a specified item.</span></span> <span data-ttu-id="72bf3-111">이 cmdlet은 이름을 바꿀 항목의 내용에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-111">This cmdlet does not affect the content of the item being renamed.</span></span>

<span data-ttu-id="72bf3-112">`Rename-Item`새 이름과 함께 경로를 지정 하는 등을 사용 하 여 항목을 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-112">You can't use `Rename-Item` to move an item, such as by specifying a path together with the new name.</span></span> <span data-ttu-id="72bf3-113">항목을 이동 하 고 이름을 바꾸려면 cmdlet을 사용 `Move-Item` 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-113">To move and rename an item, use the `Move-Item` cmdlet.</span></span>

## <span data-ttu-id="72bf3-114">예제</span><span class="sxs-lookup"><span data-stu-id="72bf3-114">EXAMPLES</span></span>

### <span data-ttu-id="72bf3-115">예제 1: 파일 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="72bf3-115">Example 1: Rename a file</span></span>

<span data-ttu-id="72bf3-116">이 명령은 파일의 이름을 `daily_file.txt` 로 바꿉니다 `monday_file.txt` .</span><span class="sxs-lookup"><span data-stu-id="72bf3-116">This command renames the file `daily_file.txt` to `monday_file.txt`.</span></span>

```powershell
Rename-Item -Path "c:\logfiles\daily_file.txt" -NewName "monday_file.txt"
```

### <span data-ttu-id="72bf3-117">예제 2: 항목 이름 바꾸기 및 이동</span><span class="sxs-lookup"><span data-stu-id="72bf3-117">Example 2: Rename and move an item</span></span>

<span data-ttu-id="72bf3-118">`Rename-Item`를 사용 하 여 항목의 이름을 바꾸고 항목을 이동할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-118">You can't use `Rename-Item` to both rename and move an item.</span></span> <span data-ttu-id="72bf3-119">특히 경로가 **path** 매개 변수에 지정 된 경로와 동일한 경우가 아니면 **NewName** 매개 변수 값에 대 한 경로를 제공할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-119">Specifically, you can't supply a path for the value of the **NewName** parameter, unless the path is identical to the path specified in the **Path** parameter.</span></span> <span data-ttu-id="72bf3-120">경로가 다른 경우, 새 이름만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-120">Otherwise, only a new name is permitted.</span></span>

<span data-ttu-id="72bf3-121">이 예에서는 디렉터리의 현재 디렉터리에 있는 파일의 이름을 `project.txt` 로 바꿉니다 `old-project.txt` `D:\Archive` .</span><span class="sxs-lookup"><span data-stu-id="72bf3-121">This example attempts to rename the `project.txt` file in the current directory to `old-project.txt` in the `D:\Archive` directory.</span></span> <span data-ttu-id="72bf3-122">명령을 실행하면 오류가 출력에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-122">The result is the error shown in the output.</span></span>

```powershell
Rename-Item -Path "project.txt" -NewName "d:\archive\old-project.txt"
```

```Output
Rename-Item : can't rename because the target specified represents a path or device name.
At line:1 char:12
+ Rename-Item <<<<  -path project.txt -NewName d:\archive\old-project.txt
+ CategoryInfo          : InvalidArgument: (:) [Rename-Item], PS>  Move-Item -Path "project.txt" -De
stination "d:\archive\old-project.txt"
```

### <span data-ttu-id="72bf3-123">예제 3: 레지스트리 키 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="72bf3-123">Example 3: Rename a registry key</span></span>

<span data-ttu-id="72bf3-124">이 예제에서는 **광고** 에서 **Marketing** 으로 레지스트리 키의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-124">This example renames a registry key from **Advertising** to **Marketing** .</span></span> <span data-ttu-id="72bf3-125">명령이 완료되면 키 이름만 바뀌고 키의 레지스트리 항목은 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-125">When the command is complete, the key is renamed, but the registry entries in the key are unchanged.</span></span>

```powershell
Rename-Item -Path "HKLM:\Software\MyCompany\Advertising" -NewName "Marketing"
```

### <span data-ttu-id="72bf3-126">예제 4: 여러 파일 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="72bf3-126">Example 4: Rename multiple files</span></span>

<span data-ttu-id="72bf3-127">이 예제에서는 `*.txt` 현재 디렉터리에 있는 모든 파일의 이름을로 바꿉니다 `*.log` .</span><span class="sxs-lookup"><span data-stu-id="72bf3-127">This example renames all the `*.txt` files in the current directory to `*.log`.</span></span>

```powershell
Get-ChildItem *.txt
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.TXT
-a----        10/3/2019   7:46 AM           2918 Monday.Txt
-a----        10/3/2019   7:47 AM           2918 Wednesday.txt
```

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.Name -replace '.txt','.log' }
Get-ChildItem *.log
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.log
-a----        10/3/2019   7:46 AM           2918 Monday.log
-a----        10/3/2019   7:47 AM           2918 Wednesday.log
```

<span data-ttu-id="72bf3-128">`Get-ChildItem`Cmdlet은 파일 확장명이 있는 현재 폴더의 모든 파일 `.txt` 을 가져와로 파이프 합니다 `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="72bf3-128">The `Get-ChildItem` cmdlet gets all the files in the current folder that have a `.txt` file extension then pipes them to `Rename-Item`.</span></span> <span data-ttu-id="72bf3-129">**Newname** 값은 값이 **newname** 매개 변수로 전송 되기 전에 실행 되는 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-129">The value of **NewName** is a script block that runs before the value is submitted to the **NewName** parameter.</span></span>

<span data-ttu-id="72bf3-130">스크립트 블록에서 `$_` 자동 변수는 파이프라인을 통해 명령에 제공 되는 각 파일 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-130">In the script block, the `$_` automatic variable represents each file object as it comes to the command through the pipeline.</span></span> <span data-ttu-id="72bf3-131">스크립트 블록은 연산자를 사용 하 여 `-replace` 각 파일의 파일 확장명을로 바꿉니다 `.log` .</span><span class="sxs-lookup"><span data-stu-id="72bf3-131">The script block uses the `-replace` operator to replace the file extension of each file with `.log`.</span></span> <span data-ttu-id="72bf3-132">연산자를 사용 하는 일치는 `-replace` 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-132">Notice that matching using the `-replace` operator is not case sensitive.</span></span>

## <span data-ttu-id="72bf3-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="72bf3-133">PARAMETERS</span></span>

### <span data-ttu-id="72bf3-134">-Credential</span><span class="sxs-lookup"><span data-stu-id="72bf3-134">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="72bf3-135">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-135">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="72bf3-136">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-136">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="72bf3-137">-Force</span><span class="sxs-lookup"><span data-stu-id="72bf3-137">-Force</span></span>

<span data-ttu-id="72bf3-138">숨겨진 파일 또는 읽기 전용 파일이 나 읽기 전용 별칭 또는 변수와 같이 다른 방법으로는 변경할 수 없는 항목의 이름을 강제로 바꾸도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-138">Forces the cmdlet to rename items that can't otherwise be changed, such as hidden or read-only files or read-only aliases or variables.</span></span> <span data-ttu-id="72bf3-139">Cmdlet은 상수 별칭 또는 변수를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-139">The cmdlet can't change constant aliases or variables.</span></span>
<span data-ttu-id="72bf3-140">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-140">Implementation varies from provider to provider.</span></span> <span data-ttu-id="72bf3-141">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="72bf3-141">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="72bf3-142">**Force** 매개 변수를 사용 하는 경우에도 cmdlet은 보안 제한을 재정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-142">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="72bf3-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="72bf3-143">-LiteralPath</span></span>

<span data-ttu-id="72bf3-144">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-144">Specifies a path to one or more locations.</span></span> <span data-ttu-id="72bf3-145">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-145">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="72bf3-146">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-146">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="72bf3-147">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="72bf3-147">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="72bf3-148">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="72bf3-149">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="72bf3-149">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="72bf3-150">-NewName</span><span class="sxs-lookup"><span data-stu-id="72bf3-150">-NewName</span></span>

<span data-ttu-id="72bf3-151">항목의 새 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-151">Specifies the new name of the item.</span></span> <span data-ttu-id="72bf3-152">경로와 이름을 함께 입력하지 말고 이름만 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-152">Enter only a name, not a path and name.</span></span> <span data-ttu-id="72bf3-153">**Path 매개 변수에** 지정 된 경로와 다른 경로를 입력 하면에서 `Rename-Item` 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-153">If you enter a path that differs from the path that is specified in the **Path** parameter, `Rename-Item` generates an error.</span></span>
<span data-ttu-id="72bf3-154">항목의 이름을 바꾸고 항목을 이동 하려면를 사용 `Move-Item` 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-154">To rename and move an item, use `Move-Item`.</span></span>

<span data-ttu-id="72bf3-155">**NewName** 매개 변수 값에는 와일드 카드 문자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-155">You can't use wildcard characters in the value of the **NewName** parameter.</span></span> <span data-ttu-id="72bf3-156">여러 파일의 이름을 지정 하려면 정규식에 **Replace** 연산자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-156">To specify a name for multiple files, use the **Replace** operator in a regular expression.</span></span> <span data-ttu-id="72bf3-157">Replace 연산자에 대 한 자세한 내용은 [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="72bf3-157">For more information about the Replace operator, see [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="72bf3-158">-PassThru</span><span class="sxs-lookup"><span data-stu-id="72bf3-158">-PassThru</span></span>

<span data-ttu-id="72bf3-159">파이프라인에 대 한 항목을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-159">Returns an object that represents the item to the pipeline.</span></span> <span data-ttu-id="72bf3-160">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-160">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="72bf3-161">-Path</span><span class="sxs-lookup"><span data-stu-id="72bf3-161">-Path</span></span>

<span data-ttu-id="72bf3-162">이름을 바꿀 항목의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-162">Specifies the path of the item to rename.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="72bf3-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="72bf3-163">-Confirm</span></span>

<span data-ttu-id="72bf3-164">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="72bf3-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="72bf3-165">-WhatIf</span></span>

<span data-ttu-id="72bf3-166">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-166">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="72bf3-167">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="72bf3-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="72bf3-168">CommonParameters</span></span>

<span data-ttu-id="72bf3-169">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="72bf3-169">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="72bf3-170">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="72bf3-170">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="72bf3-171">입력</span><span class="sxs-lookup"><span data-stu-id="72bf3-171">INPUTS</span></span>

### <span data-ttu-id="72bf3-172">System.String</span><span class="sxs-lookup"><span data-stu-id="72bf3-172">System.String</span></span>

<span data-ttu-id="72bf3-173">이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-173">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="72bf3-174">출력</span><span class="sxs-lookup"><span data-stu-id="72bf3-174">OUTPUTS</span></span>

### <span data-ttu-id="72bf3-175">없음 또는 이름이 바뀐 항목을 나타내는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-175">None or an object that represents the renamed item.</span></span>

<span data-ttu-id="72bf3-176">이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 이름이 바뀐 항목을 나타내는 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-176">This cmdlet generates an object that represents the renamed item, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="72bf3-177">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-177">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="72bf3-178">참고</span><span class="sxs-lookup"><span data-stu-id="72bf3-178">NOTES</span></span>

<span data-ttu-id="72bf3-179">`Rename-Item` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-179">`Rename-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="72bf3-180">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PsProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="72bf3-180">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="72bf3-181">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="72bf3-181">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="72bf3-182">관련 링크</span><span class="sxs-lookup"><span data-stu-id="72bf3-182">RELATED LINKS</span></span>

[<span data-ttu-id="72bf3-183">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="72bf3-183">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="72bf3-184">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="72bf3-184">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="72bf3-185">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="72bf3-185">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="72bf3-186">Get-Item</span><span class="sxs-lookup"><span data-stu-id="72bf3-186">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="72bf3-187">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="72bf3-187">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="72bf3-188">Move-Item</span><span class="sxs-lookup"><span data-stu-id="72bf3-188">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="72bf3-189">New-Item</span><span class="sxs-lookup"><span data-stu-id="72bf3-189">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="72bf3-190">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="72bf3-190">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="72bf3-191">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="72bf3-191">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="72bf3-192">Set-Item</span><span class="sxs-lookup"><span data-stu-id="72bf3-192">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="72bf3-193">about_Providers</span><span class="sxs-lookup"><span data-stu-id="72bf3-193">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

