---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-FormatData
ms.openlocfilehash: d42b108d469ed8989628a6c0b4214af4afc0db00
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605480"
---
# <span data-ttu-id="23d46-102">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="23d46-102">Export-FormatData</span></span>

## <span data-ttu-id="23d46-103">개요</span><span class="sxs-lookup"><span data-stu-id="23d46-103">SYNOPSIS</span></span>
<span data-ttu-id="23d46-104">현재 세션의 형식 지정 데이터를 형식 지정 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-104">Saves formatting data from the current session in a formatting file.</span></span>

## <span data-ttu-id="23d46-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="23d46-105">SYNTAX</span></span>

### <span data-ttu-id="23d46-106">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="23d46-106">ByPath (Default)</span></span>

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -Path <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

### <span data-ttu-id="23d46-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="23d46-107">ByLiteralPath</span></span>

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -LiteralPath <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

## <span data-ttu-id="23d46-108">설명</span><span class="sxs-lookup"><span data-stu-id="23d46-108">DESCRIPTION</span></span>

<span data-ttu-id="23d46-109">`Export-FormatData`Cmdlet은 현재 세션의 형식 지정 개체에서 PowerShell 형식 지정 파일 (format.ps1xml)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-109">The `Export-FormatData` cmdlet creates PowerShell formatting files (format.ps1xml) from the formatting objects in the current session.</span></span> <span data-ttu-id="23d46-110">이 클래스는를 반환 하 고 XML 형식의 파일로 저장 하는 **Extendedtypedefinition** 개체를 사용 `Get-FormatData` 합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-110">It takes the **ExtendedTypeDefinition** objects that `Get-FormatData` returns and saves them in a file in XML format.</span></span>

<span data-ttu-id="23d46-111">PowerShell에서는 서식 파일 (format.ps1xml)의 데이터를 사용 하 여 세션에서 Microsoft .NET Framework 개체의 기본 표시를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-111">PowerShell uses the data in formatting files (format.ps1xml) to generate the default display of Microsoft .NET Framework objects in the session.</span></span> <span data-ttu-id="23d46-112">사용자는 형식 지정 파일을 보고 편집할 수 있으며 Update-FormatData cmdlet을 사용하여 세션에 형식 지정 데이터를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-112">You can view and edit the formatting files and use the Update-FormatData cmdlet to add the formatting data to a session.</span></span>

<span data-ttu-id="23d46-113">PowerShell에서 파일의 형식을 지정 하는 방법에 대 한 자세한 내용은 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="23d46-113">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="23d46-114">예제</span><span class="sxs-lookup"><span data-stu-id="23d46-114">EXAMPLES</span></span>

### <span data-ttu-id="23d46-115">예제 1: 세션 형식 데이터 내보내기</span><span class="sxs-lookup"><span data-stu-id="23d46-115">Example 1: Export session format data</span></span>

```powershell
Get-FormatData -TypeName "*" | Export-FormatData -Path "allformat.ps1xml" -IncludeScriptBlock
```

<span data-ttu-id="23d46-116">이 명령은 세션의 모든 형식 데이터를 AllFormat.ps1xml 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-116">This command exports all of the format data in the session to the AllFormat.ps1xml file.</span></span>

<span data-ttu-id="23d46-117">이 명령은 cmdlet을 사용 하 여 `Get-FormatData` 세션의 형식 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-117">The command uses the `Get-FormatData` cmdlet to get the format data in the session.</span></span> <span data-ttu-id="23d46-118">`*` **TypeName** 매개 변수의 값 (모두)은 cmdlet에 게 세션의 모든 데이터를 가져오도록 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-118">A value of `*` (all) for the **TypeName** parameter directs the cmdlet to get all of the data in the session.</span></span>

<span data-ttu-id="23d46-119">이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 명령에서 형식 데이터를 `Get-FormatData` cmdlet으로 보냅니다 `Export-FormatData` .이 cmdlet은 형식 데이터를 AllFormat.ps1 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-119">The command uses a pipeline operator (`|`) to send the format data from the `Get-FormatData` command to the `Export-FormatData` cmdlet, which exports the format data to the AllFormat.ps1 file.</span></span>

<span data-ttu-id="23d46-120">이 `Export-FormatData` 명령은 **IncludeScriptBlock** 매개 변수를 사용 하 여 파일의 형식 데이터에 스크립트 블록을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-120">The `Export-FormatData` command uses the **IncludeScriptBlock** parameter to include script blocks in the format data in the file.</span></span>

### <span data-ttu-id="23d46-121">예 2: 형식에 대 한 형식 데이터 내보내기</span><span class="sxs-lookup"><span data-stu-id="23d46-121">Example 2: Export format data for a type</span></span>

```powershell
$F = Get-FormatData -TypeName "helpinfoshort"
Export-FormatData -InputObject $F -Path "c:\test\help.format.ps1xml" -IncludeScriptBlock
```

<span data-ttu-id="23d46-122">이러한 명령은 **Helpinfoshort** 유형의 형식 데이터를 Help.format.ps1xml 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-122">These commands export the format data for the **HelpInfoShort** type to the Help.format.ps1xml file.</span></span>

<span data-ttu-id="23d46-123">첫 번째 명령은 cmdlet을 사용 하 여 `Get-FormatData` **Helpinfoshort** 유형의 형식 데이터를 가져온 다음 변수에 저장 합니다 `$F` .</span><span class="sxs-lookup"><span data-stu-id="23d46-123">The first command uses the `Get-FormatData` cmdlet to get the format data for the **HelpInfoShort** type, and it saves it in the `$F` variable.</span></span>

<span data-ttu-id="23d46-124">두 번째 명령은 cmdlet의 **InputObject** 매개 변수 `Export-FormatData` 를 사용 하 여 변수에 저장 된 형식 데이터를 입력 합니다 `$F` .</span><span class="sxs-lookup"><span data-stu-id="23d46-124">The second command uses the **InputObject** parameter of the `Export-FormatData` cmdlet to enter the format data saved in the `$F` variable.</span></span> <span data-ttu-id="23d46-125">또한 **IncludeScriptBlock** 매개 변수를 사용 하 여 스크립트 블록을 출력에 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-125">It also uses the **IncludeScriptBlock** parameter to include script blocks in the output.</span></span>

### <span data-ttu-id="23d46-126">예제 3: 스크립트 블록 없이 형식 데이터 내보내기</span><span class="sxs-lookup"><span data-stu-id="23d46-126">Example 3: Export format data without a script block</span></span>

```powershell
Get-FormatData -TypeName "System.Diagnostics.Process" | Export-FormatData -Path process.format.ps1xml
Update-FormatData -PrependPath ".\process.format.ps1xml"
Get-Process p*
```

```Output
Handles  NPM(K)  PM(K)  WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------  -----  ----- -----   ------    -- -----------
323                                       5600 powershell
336                                       3900 powershell_ise
138                                       4076 PresentationFontCache
```

<span data-ttu-id="23d46-127">이 예에서는 명령에서 **IncludeScriptBlock** 매개 변수를 생략 하는 경우의 결과를 보여 줍니다 `Export-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="23d46-127">This example shows the effect of omitting the **IncludeScriptBlock** parameter from an `Export-FormatData` command.</span></span>

<span data-ttu-id="23d46-128">첫 번째 명령은 cmdlet을 사용 하 여 `Get-FormatData` Get-Process cmdlet이 반환 하는 **system.object** 개체의 형식 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-128">The first command uses the `Get-FormatData` cmdlet to get the format data for the **System.Diagnostics.Process** object that the Get-Process cmdlet returns.</span></span> <span data-ttu-id="23d46-129">이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 형식 지정 데이터를 cmdlet으로 보냅니다 `Export-FormatData` .이 cmdlet은 현재 디렉터리의 Process.format.ps1xml 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-129">The command uses a pipeline operator (`|`) to send the formatting data to the `Export-FormatData` cmdlet, which exports it to the Process.format.ps1xml file in the current directory.</span></span>

<span data-ttu-id="23d46-130">이 경우 `Export-FormatData` 명령은 **IncludeScriptBlock** 매개 변수를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-130">In this case, the `Export-FormatData` command does not use the **IncludeScriptBlock** parameter.</span></span>

<span data-ttu-id="23d46-131">두 번째 명령은 cmdlet을 사용 하 여 `Update-FormatData` Process.format.ps1xml 파일을 현재 세션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-131">The second command uses the `Update-FormatData` cmdlet to add the Process.format.ps1xml file to the current session.</span></span> <span data-ttu-id="23d46-132">이 명령은 **PrependPath** 매개 변수를 사용 하 여 Process.format.ps1xml 파일의 프로세스 개체에 대 한 형식 지정 데이터가 프로세스 개체에 대 한 표준 형식 지정 데이터 보다 먼저 검색 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-132">The command uses the **PrependPath** parameter to ensure that the formatting data for process objects in the Process.format.ps1xml file is found before the standard formatting data for process objects.</span></span>

<span data-ttu-id="23d46-133">세 번째 명령은 이 변경 사항의 효과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-133">The third command shows the effects of this change.</span></span> <span data-ttu-id="23d46-134">이 명령은 cmdlet을 사용 하 여 `Get-Process` 이름이 P로 시작 하는 프로세스를 가져옵니다. 출력은 스크립트 블록을 사용 하 여 계산 된 속성 값이 표시 되지 않는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-134">The command uses the `Get-Process` cmdlet to get processes that have names that begin with P. The output shows that property values that are calculated by using script blocks are missing from the display.</span></span>

## <span data-ttu-id="23d46-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="23d46-135">PARAMETERS</span></span>

### <span data-ttu-id="23d46-136">-Force</span><span class="sxs-lookup"><span data-stu-id="23d46-136">-Force</span></span>

<span data-ttu-id="23d46-137">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-137">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23d46-138">-IncludeScriptBlock</span><span class="sxs-lookup"><span data-stu-id="23d46-138">-IncludeScriptBlock</span></span>

<span data-ttu-id="23d46-139">형식 데이터의 스크립트 블록을 내보낼지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-139">Indicates whether script blocks in the format data are exported.</span></span>

<span data-ttu-id="23d46-140">스크립트 블록에는 코드가 포함되어 있어 악의적으로 사용될 수 있으므로 기본적으로 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-140">Because script blocks contain code and can be used maliciously, they are not exported by default.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23d46-141">-InputObject</span><span class="sxs-lookup"><span data-stu-id="23d46-141">-InputObject</span></span>

<span data-ttu-id="23d46-142">내보낼 형식 데이터 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-142">Specifies the format data objects to be exported.</span></span> <span data-ttu-id="23d46-143">개체를 포함 하는 변수를 입력 하거나 개체를 가져오는 명령 (예: 명령)을 입력 합니다 `Get-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="23d46-143">Enter a variable that contains the objects or a command that gets the objects, such as a `Get-FormatData` command.</span></span> <span data-ttu-id="23d46-144">에서로 개체를 파이프 할 수도 `Get-FormatData` 있습니다 `Export-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="23d46-144">You can also pipe the objects from `Get-FormatData` to `Export-FormatData`.</span></span>

```yaml
Type: System.Management.Automation.ExtendedTypeDefinition[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="23d46-145">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="23d46-145">-LiteralPath</span></span>

<span data-ttu-id="23d46-146">출력 파일의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-146">Specifies a location for the output file.</span></span> <span data-ttu-id="23d46-147">**Path** 매개 변수와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-147">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="23d46-148">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-148">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="23d46-149">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="23d46-149">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="23d46-150">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-150">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23d46-151">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="23d46-151">-NoClobber</span></span>

<span data-ttu-id="23d46-152">Cmdlet이 기존 파일을 덮어쓰지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-152">Indicates that the cmdlet does not overwrite existing files.</span></span> <span data-ttu-id="23d46-153">기본적으로는 `Export-FormatData` 파일에 읽기 전용 특성이 있는 경우를 제외 하 고는 경고 없이 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-153">By default, `Export-FormatData` overwrites files without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="23d46-154">읽기 전용 `Export-FormatData` 파일을 덮어쓰도록 지시 하려면 **Force** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-154">To direct `Export-FormatData` to overwrite read-only files, use the **Force** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23d46-155">-Path</span><span class="sxs-lookup"><span data-stu-id="23d46-155">-Path</span></span>

<span data-ttu-id="23d46-156">출력 파일의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-156">Specifies a location for the output file.</span></span>
<span data-ttu-id="23d46-157">파일 이름 확장명이 format.ps1xml인 파일 이름과 경로(선택 사항)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-157">Enter a path (optional) and file name with a format.ps1xml file name extension.</span></span>
<span data-ttu-id="23d46-158">경로를 생략 하면에서 `Export-FormatData` 현재 디렉터리에 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-158">If you omit the path, `Export-FormatData` creates the file in the current directory.</span></span>

<span data-ttu-id="23d46-159">. Types.ps1xml 이외의 파일 이름 확장명을 사용 하는 경우 cmdlet은 `Update-FormatData` 파일을 인식 하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-159">If you use a file name extension other than .ps1xml, the `Update-FormatData` cmdlet will not recognize the file.</span></span>

<span data-ttu-id="23d46-160">기존 파일을 지정 하는 경우 `Export-FormatData` 파일에 읽기 전용 특성이 없으면에서 경고 없이 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-160">If you specify an existing file, `Export-FormatData` overwrites the file without warning, unless the file has the read-only attribute.</span></span> <span data-ttu-id="23d46-161">읽기 전용 파일을 덮어쓰려면 **Force** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-161">To overwrite a read-only file, use the **Force** parameter.</span></span> <span data-ttu-id="23d46-162">파일을 덮어쓰지 않도록 하려면 **NoClobber** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-162">To prevent files from being overwritten, use the **NoClobber** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: FilePath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23d46-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="23d46-163">CommonParameters</span></span>

<span data-ttu-id="23d46-164">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="23d46-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="23d46-165">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23d46-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="23d46-166">입력</span><span class="sxs-lookup"><span data-stu-id="23d46-166">INPUTS</span></span>

### <span data-ttu-id="23d46-167">System.web. ExtendedTypeDefinition</span><span class="sxs-lookup"><span data-stu-id="23d46-167">System.Management.Automation.ExtendedTypeDefinition</span></span>

<span data-ttu-id="23d46-168">**Extendedtypedefinition** 개체를에서로 파이프 할 수 있습니다 `Get-FormatData` `Export-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="23d46-168">You can pipe **ExtendedTypeDefinition** objects from `Get-FormatData` to `Export-FormatData`.</span></span>

## <span data-ttu-id="23d46-169">출력</span><span class="sxs-lookup"><span data-stu-id="23d46-169">OUTPUTS</span></span>

### <span data-ttu-id="23d46-170">없음</span><span class="sxs-lookup"><span data-stu-id="23d46-170">None</span></span>

<span data-ttu-id="23d46-171">`Export-FormatData` 는 개체를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-171">`Export-FormatData` does not return any objects.</span></span>
<span data-ttu-id="23d46-172">파일을 생성하여 지정된 경로에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-172">It generates a file and saves it in the specified path.</span></span>

## <span data-ttu-id="23d46-173">참고</span><span class="sxs-lookup"><span data-stu-id="23d46-173">NOTES</span></span>

- <span data-ttu-id="23d46-174">내보낸 형식 지정 파일을 포함하여 모든 형식 지정 파일을 사용하려면 세션에 대한 실행 정책에서 스크립트와 구성 파일의 실행을 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23d46-174">To use any formatting file, including an exported formatting file, the execution policy for the session must allow scripts and configuration files to run.</span></span> <span data-ttu-id="23d46-175">자세한 내용은 [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23d46-175">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="23d46-176">관련 링크</span><span class="sxs-lookup"><span data-stu-id="23d46-176">RELATED LINKS</span></span>

[<span data-ttu-id="23d46-177">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="23d46-177">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="23d46-178">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="23d46-178">Update-FormatData</span></span>](Update-FormatData.md)
