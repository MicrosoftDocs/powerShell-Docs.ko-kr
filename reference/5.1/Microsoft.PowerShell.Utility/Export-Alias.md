---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-alias?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Alias
ms.openlocfilehash: 50b0ccf6c56613166d16648492b6b35e5714832e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214066"
---
# <span data-ttu-id="413bb-103">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="413bb-103">Export-Alias</span></span>

## <span data-ttu-id="413bb-104">개요</span><span class="sxs-lookup"><span data-stu-id="413bb-104">SYNOPSIS</span></span>
<span data-ttu-id="413bb-105">현재 정의된 별칭에 대한 정보를 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-105">Exports information about currently defined aliases to a file.</span></span>

## <span data-ttu-id="413bb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="413bb-106">SYNTAX</span></span>

### <span data-ttu-id="413bb-107">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="413bb-107">ByPath (Default)</span></span>

```
Export-Alias [-Path] <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append] [-Force]
 [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="413bb-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="413bb-108">ByLiteralPath</span></span>

```
Export-Alias -LiteralPath <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append]
 [-Force] [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="413bb-109">설명</span><span class="sxs-lookup"><span data-stu-id="413bb-109">DESCRIPTION</span></span>

<span data-ttu-id="413bb-110">`Export-Alias`Cmdlet은 현재 세션의 별칭을 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-110">The `Export-Alias` cmdlet exports the aliases in the current session to a file.</span></span>
<span data-ttu-id="413bb-111">출력 파일이 없으면 cmdlet에서 출력 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-111">If the output file does not exist, the cmdlet will create it.</span></span>

<span data-ttu-id="413bb-112">`Export-Alias` 는 특정 범위 또는 모든 범위의 별칭을 내보낼 수 있습니다. 또한 CSV 형식으로 데이터를 생성 하거나, 세션 또는 PowerShell 프로필에 추가할 수 있는 일련의 Set-Alias 명령으로 데이터를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-112">`Export-Alias` can export the aliases in a particular scope or all scopes, it can generate the data in CSV format or as a series of Set-Alias commands that you can add to a session or to a PowerShell profile.</span></span>

## <span data-ttu-id="413bb-113">예제</span><span class="sxs-lookup"><span data-stu-id="413bb-113">EXAMPLES</span></span>

### <span data-ttu-id="413bb-114">예제 1: 별칭 내보내기</span><span class="sxs-lookup"><span data-stu-id="413bb-114">Example 1: Export an alias</span></span>

```powershell
Export-Alias -Path "alias.csv"
```

<span data-ttu-id="413bb-115">이 명령은 현재 별칭 정보를 현재 디렉터리의 Alias.csv 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-115">This command exports current alias information to a file named Alias.csv in the current directory.</span></span>

### <span data-ttu-id="413bb-116">예 2: 내보내기 파일이 이미 존재 하지 않는 경우 별칭 내보내기</span><span class="sxs-lookup"><span data-stu-id="413bb-116">Example 2: Export an alias unless the export file already exists</span></span>

```powershell
Export-Alias -Path "alias.csv" -NoClobber
```

<span data-ttu-id="413bb-117">이 명령은 현재 세션의 별칭을 Alias.csv 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-117">This command exports the aliases in the current session to an Alias.csv file.</span></span>

<span data-ttu-id="413bb-118">**NoClobber** 매개 변수를 지정 하기 때문에 현재 디렉터리에 Alias.csv 파일이 이미 있으면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-118">Because the **NoClobber** parameter is specified, the command will fail if an Alias.csv file already exists in the current directory.</span></span>

### <span data-ttu-id="413bb-119">예제 3: 파일에 별칭 추가</span><span class="sxs-lookup"><span data-stu-id="413bb-119">Example 3: Append aliases to a file</span></span>

```powershell
Export-Alias -Path "alias.csv" -Append -Description "Appended Aliases" -Force
```

<span data-ttu-id="413bb-120">이 명령은 현재 세션의 별칭을 Alias.csv 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-120">This command appends the aliases in the current session to the Alias.csv file.</span></span>

<span data-ttu-id="413bb-121">이 명령은 **description** 매개 변수를 사용 하 여 파일의 맨 위에 있는 주석에 설명을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-121">The command uses the **Description** parameter to add a description to the comments at the top of the file.</span></span>

<span data-ttu-id="413bb-122">또한이 명령은 읽기 전용 특성이 있는 경우에도 **Force** 매개 변수를 사용 하 여 기존 Alias.csv 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-122">The command also uses the **Force** parameter to overwrite any existing Alias.csv files, even if they have the read-only attribute.</span></span>

### <span data-ttu-id="413bb-123">예 4: 스크립트로 별칭 내보내기</span><span class="sxs-lookup"><span data-stu-id="413bb-123">Example 4: Export aliases as a script</span></span>

```powershell
Export-Alias -Path "alias.ps1" -As Script
Add-Content -Path $Profile -Value (Get-Content alias.ps1)
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -FilePath .\alias.ps1
```

<span data-ttu-id="413bb-124">이 예에서는을 생성 하는 스크립트 파일 형식을 사용 하는 방법을 보여 줍니다 `Export-Alias` .</span><span class="sxs-lookup"><span data-stu-id="413bb-124">This example shows how to use the script file format that `Export-Alias` generates.</span></span>

<span data-ttu-id="413bb-125">첫 번째 명령은 세션의 별칭을 Alias.ps1 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-125">The first command exports the aliases in the session to the Alias.ps1 file.</span></span>
<span data-ttu-id="413bb-126">스크립트 값을 사용 하 여 **As** 매개 변수를 사용 하 여 각 별칭에 대해 Set-Alias 명령을 포함 하는 파일을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-126">It uses the **As** parameter with a value of Script to generate a file that contains a Set-Alias command for each alias.</span></span>

<span data-ttu-id="413bb-127">두 번째 명령은 Alias.ps1 파일의 별칭을 CurrentUser-CurrentHost 프로필에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-127">The second command adds the aliases in the Alias.ps1 file to the CurrentUser-CurrentHost profile.</span></span>
<span data-ttu-id="413bb-128">프로필에 대 한 경로는 변수에 저장 됩니다 `$Profile` .</span><span class="sxs-lookup"><span data-stu-id="413bb-128">The path to the profile is saved in the `$Profile` variable.</span></span>
<span data-ttu-id="413bb-129">이 명령은 cmdlet을 사용 하 여 `Get-Content` Alias.ps1 파일에서 별칭을 가져오고 cmdlet을 사용 하 여 `Add-Content` 프로필에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-129">The command uses the `Get-Content` cmdlet to get the aliases from the Alias.ps1 file and the `Add-Content` cmdlet to add them to the profile.</span></span>
<span data-ttu-id="413bb-130">자세한 내용은 about_Profiles를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="413bb-130">For more information, see about_Profiles.</span></span>

<span data-ttu-id="413bb-131">세 번째 및 네 번째 명령은 Alias.ps1 파일의 별칭을 Server01 컴퓨터의 원격 세션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-131">The third and fourth commands add the aliases in the Alias.ps1 file to a remote session on the Server01 computer.</span></span>
<span data-ttu-id="413bb-132">세 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-132">The third command uses the `New-PSSession` cmdlet to create the session.</span></span>
<span data-ttu-id="413bb-133">네 번째 명령은 cmdlet의 **FilePath** 매개 변수를 사용 하 여 `Invoke-Command` 새 세션에서 Alias.ps1 파일을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-133">The fourth command uses the **FilePath** parameter of the `Invoke-Command` cmdlet to run the Alias.ps1 file in the new session.</span></span>

## <span data-ttu-id="413bb-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="413bb-134">PARAMETERS</span></span>

### <span data-ttu-id="413bb-135">-추가</span><span class="sxs-lookup"><span data-stu-id="413bb-135">-Append</span></span>

<span data-ttu-id="413bb-136">이 cmdlet이 해당 파일의 기존 내용을 덮어쓰지 않고 지정 된 파일에 출력을 추가 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-136">Indicates that this cmdlet appends the output to the specified file, rather than overwriting the existing contents of that file.</span></span>

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

### <span data-ttu-id="413bb-137">-As</span><span class="sxs-lookup"><span data-stu-id="413bb-137">-As</span></span>

<span data-ttu-id="413bb-138">출력 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-138">Specifies the output format.</span></span>
<span data-ttu-id="413bb-139">기본값은 CSV입니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-139">CSV is the default.</span></span>
<span data-ttu-id="413bb-140">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-140">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="413bb-141">CSV입니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-141">CSV.</span></span>
<span data-ttu-id="413bb-142">CSV(쉼표로 구분된 값) 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-142">Comma-separated value (CSV) format.</span></span>
- <span data-ttu-id="413bb-143">스크립트.</span><span class="sxs-lookup"><span data-stu-id="413bb-143">Script.</span></span>
<span data-ttu-id="413bb-144">`Set-Alias`내보낸 각 별칭에 대 한 명령을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-144">Creates a `Set-Alias` command for each exported alias.</span></span>
<span data-ttu-id="413bb-145">출력 파일 이름 확장명을 .ps1으로 지정하면 별칭을 세션에 추가하는 스크립트로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-145">If you name the output file with a .ps1 file name extension, you can run it as a script to add the aliases to any session.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ExportAliasFormat
Parameter Sets: (All)
Aliases:
Accepted values: Csv, Script

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="413bb-146">-Description</span><span class="sxs-lookup"><span data-stu-id="413bb-146">-Description</span></span>

<span data-ttu-id="413bb-147">내보낸 파일에 대 한 설명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-147">Specifies the description of the exported file.</span></span>
<span data-ttu-id="413bb-148">설명은 파일의 위쪽 머리글 정보 다음에 주석으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-148">The description appears as a comment at the top of the file, following the header information.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="413bb-149">-Force</span><span class="sxs-lookup"><span data-stu-id="413bb-149">-Force</span></span>

<span data-ttu-id="413bb-150">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-150">Forces the command to run without asking for user confirmation.</span></span>

<span data-ttu-id="413bb-151">파일에 읽기 전용 특성이 설정되어 있는 경우에도 출력 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-151">Overwrites the output file, even if the read-only attribute is set on the file.</span></span>

<span data-ttu-id="413bb-152">기본적으로는 `Export-Alias` 읽기 전용 또는 숨김 특성이 설정 되어 있지 않거나 명령에 **NoClobber** 매개 변수가 사용 되는 경우를 제외 하 고는 경고 없이 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-152">By default, `Export-Alias` overwrites files without warning, unless the read-only or hidden attribute is set or the **NoClobber** parameter is used in the command.</span></span>
<span data-ttu-id="413bb-153">명령에 사용 되는 경우 **NoClobber** 매개 변수는 Force 매개 변수 보다 우선적으로 **적용** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-153">The **NoClobber** parameter takes precedence over the **Force** parameter when both are used in a command.</span></span>

<span data-ttu-id="413bb-154">**Force** 매개 변수는 `Export-Alias` hidden 특성을 가진 파일을 강제로 덮어쓸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-154">The **Force** parameter cannot force `Export-Alias` to overwrite files with the hidden attribute.</span></span>

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

### <span data-ttu-id="413bb-155">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="413bb-155">-LiteralPath</span></span>

<span data-ttu-id="413bb-156">출력 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-156">Specifies the path to the output file.</span></span>
<span data-ttu-id="413bb-157">**Path** 와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-157">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="413bb-158">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-158">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="413bb-159">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="413bb-159">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="413bb-160">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-160">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="413bb-161">-Name</span><span class="sxs-lookup"><span data-stu-id="413bb-161">-Name</span></span>

<span data-ttu-id="413bb-162">이름을 내보낼 별칭의 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-162">Specifies the names as an array of the aliases to export.</span></span>
<span data-ttu-id="413bb-163">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-163">Wildcards are permitted.</span></span>

<span data-ttu-id="413bb-164">기본적으로는 `Export-Alias` 세션 또는 범위의 모든 별칭을 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-164">By default, `Export-Alias` exports all aliases in the session or scope.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="413bb-165">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="413bb-165">-NoClobber</span></span>

<span data-ttu-id="413bb-166">`Export-Alias`명령에 **Force** 매개 변수가 사용 되는 경우에도이 cmdlet이 파일을 덮어쓰지 않도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-166">Indicates that this cmdlet prevents `Export-Alias` from overwriting any files, even if the **Force** parameter is used in the command.</span></span>

<span data-ttu-id="413bb-167">**NoClobber** 매개 변수를 생략 하면는 `Export-Alias` 파일에 읽기 전용 특성이 설정 되어 있지 않은 경우 경고 없이 기존 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-167">If the **NoClobber** parameter is omitted, `Export-Alias` will overwrite an existing file without warning, unless the read-only attribute is set on the file.</span></span>
<span data-ttu-id="413bb-168">*NoClobber* 은 읽기 전용 **Force** `Export-Alias` 특성으로 파일을 덮어쓸 수 있도록 하는 Force 매개 변수 보다 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-168">*NoClobber* takes precedence over the **Force** parameter, which permits `Export-Alias` to overwrite a file with the read-only attribute.</span></span>

<span data-ttu-id="413bb-169">*NoClobber* 를 설정 해도 **Append** 매개 변수는 기존 파일에 내용을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-169">*NoClobber* does not prevent the **Append** parameter from adding content to an existing file.</span></span>

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

### <span data-ttu-id="413bb-170">-PassThru</span><span class="sxs-lookup"><span data-stu-id="413bb-170">-PassThru</span></span>

<span data-ttu-id="413bb-171">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-171">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="413bb-172">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-172">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="413bb-173">-Path</span><span class="sxs-lookup"><span data-stu-id="413bb-173">-Path</span></span>

<span data-ttu-id="413bb-174">출력 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-174">Specifies the path to the output file.</span></span>
<span data-ttu-id="413bb-175">와일드카드를 사용할 수는 있지만 결과 경로 값은 하나의 파일 이름을 도출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-175">Wildcards are permitted, but the resulting path value must resolve to a single file name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="413bb-176">-범위</span><span class="sxs-lookup"><span data-stu-id="413bb-176">-Scope</span></span>

<span data-ttu-id="413bb-177">별칭을 내보낼 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-177">Specifies the scope from which the aliases should be exported.</span></span>
<span data-ttu-id="413bb-178">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-178">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="413bb-179">전역</span><span class="sxs-lookup"><span data-stu-id="413bb-179">Global</span></span>
- <span data-ttu-id="413bb-180">로컬</span><span class="sxs-lookup"><span data-stu-id="413bb-180">Local</span></span>
- <span data-ttu-id="413bb-181">스크립트</span><span class="sxs-lookup"><span data-stu-id="413bb-181">Script</span></span>
- <span data-ttu-id="413bb-182">현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)입니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-182">A number relative to the current scope (0 through the number of scopes where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="413bb-183">기본값은 Local입니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-183">The default value is Local.</span></span>
<span data-ttu-id="413bb-184">자세한 내용은 about_Scopes를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="413bb-184">For more information, see about_Scopes.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="413bb-185">-Confirm</span><span class="sxs-lookup"><span data-stu-id="413bb-185">-Confirm</span></span>

<span data-ttu-id="413bb-186">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-186">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="413bb-187">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="413bb-187">-WhatIf</span></span>

<span data-ttu-id="413bb-188">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-188">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="413bb-189">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-189">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="413bb-190">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="413bb-190">CommonParameters</span></span>

<span data-ttu-id="413bb-191">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="413bb-191">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="413bb-192">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="413bb-192">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="413bb-193">입력</span><span class="sxs-lookup"><span data-stu-id="413bb-193">INPUTS</span></span>

### <span data-ttu-id="413bb-194">없음</span><span class="sxs-lookup"><span data-stu-id="413bb-194">None.</span></span>

<span data-ttu-id="413bb-195">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-195">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="413bb-196">출력</span><span class="sxs-lookup"><span data-stu-id="413bb-196">OUTPUTS</span></span>

### <span data-ttu-id="413bb-197">없음 또는 System.management.automation.aliasinfo</span><span class="sxs-lookup"><span data-stu-id="413bb-197">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="413bb-198">**Passthru** 매개 변수를 사용 하는 경우는 `Export-Alias` 별칭을 나타내는 **system.management.automation.aliasinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-198">When you use the **Passthru** parameter, `Export-Alias` returns a **System.Management.Automation.AliasInfo** object that represents the alias.</span></span>
<span data-ttu-id="413bb-199">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-199">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="413bb-200">참고</span><span class="sxs-lookup"><span data-stu-id="413bb-200">NOTES</span></span>

* <span data-ttu-id="413bb-201">파일로만 Export-Alias를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="413bb-201">You can only Export-Aliases to a file.</span></span>

## <span data-ttu-id="413bb-202">관련 링크</span><span class="sxs-lookup"><span data-stu-id="413bb-202">RELATED LINKS</span></span>

[<span data-ttu-id="413bb-203">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="413bb-203">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="413bb-204">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="413bb-204">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="413bb-205">New-Alias</span><span class="sxs-lookup"><span data-stu-id="413bb-205">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="413bb-206">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="413bb-206">Set-Alias</span></span>](Set-Alias.md)
