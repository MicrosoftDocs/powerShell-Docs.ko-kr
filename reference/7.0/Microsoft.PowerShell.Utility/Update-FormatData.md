---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-formatdata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-FormatData
ms.openlocfilehash: 209e5cf9ab5809767b4135817640ffe7c2d69175
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210498"
---
# <span data-ttu-id="06c6d-103">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="06c6d-103">Update-FormatData</span></span>

## <span data-ttu-id="06c6d-104">개요</span><span class="sxs-lookup"><span data-stu-id="06c6d-104">SYNOPSIS</span></span>
<span data-ttu-id="06c6d-105">현재 세션에 있는 형식 지정 데이터를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-105">Updates the formatting data in the current session.</span></span>

## <span data-ttu-id="06c6d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="06c6d-106">SYNTAX</span></span>

```
Update-FormatData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="06c6d-107">설명</span><span class="sxs-lookup"><span data-stu-id="06c6d-107">DESCRIPTION</span></span>

<span data-ttu-id="06c6d-108">Cmdlet은 형식 지정 `Update-FormatData` 파일의 형식 지정 데이터를 현재 세션으로 다시 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-108">The `Update-FormatData` cmdlet reloads the formatting data from formatting files into the current session.</span></span> <span data-ttu-id="06c6d-109">이 cmdlet을 사용 하면 PowerShell을 다시 시작 하지 않고도 형식 지정 데이터를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-109">This cmdlet lets you update the formatting data without restarting PowerShell.</span></span>

<span data-ttu-id="06c6d-110">매개 변수가 없으면 `Update-FormatData` 이전에 로드 한 형식 지정 파일을 다시 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-110">Without parameters, `Update-FormatData` reloads the formatting files that it loaded previously.</span></span>
<span data-ttu-id="06c6d-111">의 매개 변수를 사용 `Update-FormatData` 하 여 새 형식 지정 파일을 세션에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-111">You can use the parameters of `Update-FormatData` to add new formatting files to the session.</span></span>

<span data-ttu-id="06c6d-112">서식 파일은 파일 이름 확장명을 사용 하는 XML 형식의 텍스트 파일 `format.ps1xml` 입니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-112">Formatting files are text files in XML format with the `format.ps1xml` file name extension.</span></span> <span data-ttu-id="06c6d-113">이 파일의 형식 지정 데이터는 세션에서 Microsoft .NET Framework 개체의 표시를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-113">The formatting data in the files defines the display of Microsoft .NET Framework objects in the session.</span></span>

<span data-ttu-id="06c6d-114">PowerShell이 시작 되 면 PowerShell 소스 코드에서 형식 데이터를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-114">When PowerShell starts, it loads the format data from the PowerShell source code.</span></span> <span data-ttu-id="06c6d-115">그러나 사용자 지정 format.ps1xml 파일을 만들어 현재 세션의 형식을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-115">However, you can create custom format.ps1xml files to update formatting in the current session.</span></span> <span data-ttu-id="06c6d-116">`Update-FormatData`PowerShell을 다시 시작 하지 않고를 사용 하 여 형식 지정 데이터를 현재 세션으로 다시 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-116">You can use `Update-FormatData` to reload the formatting data into the current session without restarting PowerShell.</span></span> <span data-ttu-id="06c6d-117">이 방법은 형식 지정 파일을 추가하거나 변경했지만 세션을 중단하지 않으려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-117">This is useful when you have added or changed a formatting file, but do not want to interrupt the session.</span></span>

<span data-ttu-id="06c6d-118">PowerShell에서 파일의 형식을 지정 하는 방법에 대 한 자세한 내용은 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="06c6d-118">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="06c6d-119">예제</span><span class="sxs-lookup"><span data-stu-id="06c6d-119">EXAMPLES</span></span>

### <span data-ttu-id="06c6d-120">예제 1: 이전에 로드 한 서식 파일 다시 로드</span><span class="sxs-lookup"><span data-stu-id="06c6d-120">Example 1: Reload previously loaded formatting files</span></span>

```powershell
Update-FormatData
```

<span data-ttu-id="06c6d-121">이 명령은 이전에 로드한 형식 지정 파일을 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-121">This command reloads the formatting files that it loaded previously.</span></span>

### <span data-ttu-id="06c6d-122">예 2: 형식 지정 파일 및 추적 및 로그 서식 파일 다시 로드</span><span class="sxs-lookup"><span data-stu-id="06c6d-122">Example 2: Reload formatting files and trace and log formatting files</span></span>

```powershell
Update-FormatData -AppendPath "trace.format.ps1xml, log.format.ps1xml"
```

<span data-ttu-id="06c6d-123">이 명령은 두 개의 새 파일 Trace.format.ps1xml 및 Log.format.ps1xml을 비롯한 형식 지정 파일을 세션으로 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-123">This command reloads the formatting files into the session, including two new files, Trace.format.ps1xml and Log.format.ps1xml.</span></span>

<span data-ttu-id="06c6d-124">이 명령은 **Appendpath** 매개 변수를 사용 하므로 기본 제공 파일의 형식 지정 데이터 이후에 새 파일의 형식 지정 데이터가 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-124">Because the command uses the **AppendPath** parameter, the formatting data in the new files is loaded after the formatting data from the built-in files.</span></span>

<span data-ttu-id="06c6d-125">새 파일에 기본 제공 파일에서 참조 되지 않는 개체에 대 한 형식 지정 데이터가 포함 되어 있으므로 **Appendpath** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-125">The **AppendPath** parameter is used because the new files contain formatting data for objects that are not referenced in the built-in files.</span></span>

### <span data-ttu-id="06c6d-126">예제 3: 서식 파일 편집 및 다시 로드</span><span class="sxs-lookup"><span data-stu-id="06c6d-126">Example 3: Edit a formatting file and reload it</span></span>

```powershell
Update-FormatData -PrependPath "c:\test\NewFiles.format.ps1xml"

# Edit the NewFiles.format.ps1 file.

Update-FormatData
```

<span data-ttu-id="06c6d-127">이 예제에서는 형식 지정 파일을 편집한 후 다시 로드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-127">This example shows how to reload a formatting file after you have edited it.</span></span>

<span data-ttu-id="06c6d-128">첫 번째 명령은 NewFiles.format.ps1xml 파일을 세션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-128">The first command adds the NewFiles.format.ps1xml file to the session.</span></span> <span data-ttu-id="06c6d-129">**PrependPath** 매개 변수를 사용 합니다 .이 파일에는 기본 제공 파일에서 참조 되는 개체에 대 한 형식 지정 데이터가 포함 되어 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-129">It uses the **PrependPath** parameter because the file contains formatting data for objects that are referenced in the built-in files.</span></span>

<span data-ttu-id="06c6d-130">NewFiles.format.ps1xml 파일을 추가 하 고 이러한 세션에서 테스트 한 후에는 작성자가 파일을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-130">After adding the NewFiles.format.ps1xml file and testing it in these sessions, the author edits the file.</span></span>

<span data-ttu-id="06c6d-131">두 번째 명령은 cmdlet을 사용 하 여 `Update-FormatData` 형식 지정 파일을 다시 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-131">The second command uses the `Update-FormatData` cmdlet to reload the formatting files.</span></span> <span data-ttu-id="06c6d-132">NewFiles.format.ps1xml 파일이 이전에 로드 되었으므로는 `Update-FormatData` 매개 변수를 사용 하지 않고 자동으로 다시 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-132">Because the NewFiles.format.ps1xml file was previously loaded, `Update-FormatData` automatically reloads it without using parameters.</span></span>

## <span data-ttu-id="06c6d-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="06c6d-133">PARAMETERS</span></span>

### <span data-ttu-id="06c6d-134">-AppendPath</span><span class="sxs-lookup"><span data-stu-id="06c6d-134">-AppendPath</span></span>

<span data-ttu-id="06c6d-135">이 cmdlet이 세션에 추가 하는 형식 지정 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-135">Specifies formatting files that this cmdlet adds to the session.</span></span> <span data-ttu-id="06c6d-136">파일은 PowerShell에서 기본 제공 형식 지정 파일을 로드 한 후에 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-136">The files are loaded after PowerShell loads the built-in formatting files.</span></span>

<span data-ttu-id="06c6d-137">.NET 개체의 형식을 지정 하는 경우 PowerShell은 각 .NET 유형에 대해 찾은 첫 번째 형식 지정 정의를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-137">When formatting .NET objects, PowerShell uses the first formatting definition that it finds for each .NET type.</span></span> <span data-ttu-id="06c6d-138">**Appendpath** 매개 변수를 사용 하는 경우 PowerShell은 사용자가 추가 하는 형식 지정 데이터를 찾기 전에 기본 제공 파일에서 데이터를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-138">If you use the **AppendPath** parameter, PowerShell searches the data from the built-in files before it encounters the formatting data that you are adding.</span></span>

<span data-ttu-id="06c6d-139">이 매개 변수를 사용하면 기본 형식 지정 파일에서 참조되지 않는 .NET 개체의 형식을 지정하는 파일을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-139">Use this parameter to add a file that formats a .NET object that is not referenced in the built-in formatting files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="06c6d-140">-PrependPath</span><span class="sxs-lookup"><span data-stu-id="06c6d-140">-PrependPath</span></span>

<span data-ttu-id="06c6d-141">이 cmdlet이 세션에 추가 하는 형식 지정 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-141">Specifies formatting files that this cmdlet adds to the session.</span></span> <span data-ttu-id="06c6d-142">파일은 PowerShell에서 기본 제공 형식 지정 파일을 로드 하기 전에 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-142">The files are loaded before PowerShell loads the built-in formatting files.</span></span>

<span data-ttu-id="06c6d-143">.NET 개체의 형식을 지정 하는 경우 PowerShell은 각 .NET 유형에 대해 찾은 첫 번째 형식 지정 정의를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-143">When formatting .NET objects, PowerShell uses the first formatting definition that it finds for each .NET type.</span></span> <span data-ttu-id="06c6d-144">**PrependPath** 매개 변수를 사용 하는 경우 PowerShell은 기본 제공 파일의 형식 지정 데이터를 발생 하기 전에 추가 하는 파일에서 데이터를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-144">If you use the **PrependPath** parameter, PowerShell searches the data from the files that you are adding before it encounters the formatting data from the built-in files.</span></span>

<span data-ttu-id="06c6d-145">이 매개 변수를 사용하면 기본 형식 지정 파일에서도 참조되는 .NET 개체의 형식을 지정하는 파일을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-145">Use this parameter to add a file that formats a .NET object that is also referenced in the built-in formatting files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="06c6d-146">-Confirm</span><span class="sxs-lookup"><span data-stu-id="06c6d-146">-Confirm</span></span>

<span data-ttu-id="06c6d-147">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-147">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="06c6d-148">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="06c6d-148">-WhatIf</span></span>

<span data-ttu-id="06c6d-149">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-149">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="06c6d-150">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-150">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="06c6d-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="06c6d-151">CommonParameters</span></span>

<span data-ttu-id="06c6d-152">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="06c6d-152">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="06c6d-153">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="06c6d-153">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="06c6d-154">입력</span><span class="sxs-lookup"><span data-stu-id="06c6d-154">INPUTS</span></span>

### <span data-ttu-id="06c6d-155">System.String</span><span class="sxs-lookup"><span data-stu-id="06c6d-155">System.String</span></span>

<span data-ttu-id="06c6d-156">추가 경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Update-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="06c6d-156">You can pipe a string that contains the append path to `Update-FormatData`.</span></span>

## <span data-ttu-id="06c6d-157">출력</span><span class="sxs-lookup"><span data-stu-id="06c6d-157">OUTPUTS</span></span>

### <span data-ttu-id="06c6d-158">없음</span><span class="sxs-lookup"><span data-stu-id="06c6d-158">None</span></span>

<span data-ttu-id="06c6d-159">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-159">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="06c6d-160">참고</span><span class="sxs-lookup"><span data-stu-id="06c6d-160">NOTES</span></span>

- <span data-ttu-id="06c6d-161">`Update-FormatData` 는 모듈에서 가져온 세션의 명령에 대 한 형식 지정 데이터도 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-161">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="06c6d-162">모듈에 대 한 형식 지정 파일이 변경 되 면 `Update-FormatData` 명령을 실행 하 여 가져온 명령에 대 한 형식 지정 데이터를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-162">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="06c6d-163">모듈을 다시 가져올 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="06c6d-163">You do not need to import the module again.</span></span>

## <span data-ttu-id="06c6d-164">관련 링크</span><span class="sxs-lookup"><span data-stu-id="06c6d-164">RELATED LINKS</span></span>

[<span data-ttu-id="06c6d-165">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="06c6d-165">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="06c6d-166">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="06c6d-166">Export-FormatData</span></span>](Export-FormatData.md)
