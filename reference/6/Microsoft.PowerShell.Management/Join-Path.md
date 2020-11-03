---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/join-path?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-Path
ms.openlocfilehash: 7752688a04057861fffdbc7b30c293239acb132e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213193"
---
# <span data-ttu-id="99f51-103">Join-Path</span><span class="sxs-lookup"><span data-stu-id="99f51-103">Join-Path</span></span>

## <span data-ttu-id="99f51-104">개요</span><span class="sxs-lookup"><span data-stu-id="99f51-104">SYNOPSIS</span></span>
<span data-ttu-id="99f51-105">경로와 하위 경로를 단일 경로로 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-105">Combines a path and a child path into a single path.</span></span>

## <span data-ttu-id="99f51-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="99f51-106">SYNTAX</span></span>

```
Join-Path [-Path] <String[]> [-ChildPath] <String> [[-AdditionalChildPath] <String[]>] [-Resolve]
 [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="99f51-107">설명</span><span class="sxs-lookup"><span data-stu-id="99f51-107">DESCRIPTION</span></span>

<span data-ttu-id="99f51-108">`Join-Path`Cmdlet은 경로와 하위 경로를 단일 경로로 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-108">The `Join-Path` cmdlet combines a path and child-path into a single path.</span></span>
<span data-ttu-id="99f51-109">공급자가 경로 구분 기호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-109">The provider supplies the path delimiters.</span></span>

## <span data-ttu-id="99f51-110">예제</span><span class="sxs-lookup"><span data-stu-id="99f51-110">EXAMPLES</span></span>

### <span data-ttu-id="99f51-111">예제 1: 경로를 하위 경로와 결합</span><span class="sxs-lookup"><span data-stu-id="99f51-111">Example 1: Combine a path with a child path</span></span>

```powershell
PS C:\> Join-Path -Path "path" -ChildPath "childpath"
```

```output
path\childpath
```

<span data-ttu-id="99f51-112">이 명령은 `Join-Path` 를 사용 하 여 경로를 childpath와 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-112">This command uses `Join-Path` to combine a path with a childpath.</span></span>

<span data-ttu-id="99f51-113">명령은 공급자에서 실행 되므로 경로를 `FileSystem` `\` 조인 하는 구분 기호를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-113">Since the command is executed from the `FileSystem` provider, it provides the `\` delimiter to join the paths.</span></span>

### <span data-ttu-id="99f51-114">예제 2: 디렉터리 구분 기호가 이미 포함 된 경로 결합</span><span class="sxs-lookup"><span data-stu-id="99f51-114">Example 2: Combine paths that already contain directory separators</span></span>

```powershell
PS C:\> Join-Path -Path "path\" -ChildPath "\childpath"
```

```output
path\childpath
```

<span data-ttu-id="99f51-115">기존 디렉터리 구분 기호 `\` 를 처리 하 고 `Path``ChildPath`</span><span class="sxs-lookup"><span data-stu-id="99f51-115">Existing directory separators `\` and handled so there is only one separator between `Path` and `ChildPath`</span></span>

### <span data-ttu-id="99f51-116">예제 3: 경로를 자식 경로에 조인 하 여 파일 및 폴더 표시</span><span class="sxs-lookup"><span data-stu-id="99f51-116">Example 3: Display files and folders by joining a path with a child path</span></span>

```powershell
Join-Path "C:\win*" "System*" -Resolve
```

<span data-ttu-id="99f51-117">이 명령은 C:\Win \* 경로 및 시스템 자식 경로를 조인 하 여 참조 되는 파일 및 폴더를 표시 합니다 \* .</span><span class="sxs-lookup"><span data-stu-id="99f51-117">This command displays the files and folders that are referenced by joining the C:\Win\* path and the System\* child path.</span></span>
<span data-ttu-id="99f51-118">과 동일한 파일 및 폴더를 표시 `Get-ChildItem` 하지만 각 항목의 정규화 된 경로를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-118">It displays the same files and folders as `Get-ChildItem`, but it displays the fully qualified path to each item.</span></span>
<span data-ttu-id="99f51-119">이 명령에서는 `Path` 및 `ChildPath` 선택적 매개 변수 이름이 생략 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-119">In this command, the `Path` and `ChildPath` optional parameter names are omitted.</span></span>

### <span data-ttu-id="99f51-120">예제 4: PowerShell 레지스트리 공급자와 Join-Path 사용</span><span class="sxs-lookup"><span data-stu-id="99f51-120">Example 4: Use Join-Path with the PowerShell registry provider</span></span>

```powershell
PS HKLM:\> Join-Path -Path System -ChildPath *ControlSet* -Resolve
```

```output
HKLM:\System\ControlSet001
HKLM:\System\CurrentControlSet
```

<span data-ttu-id="99f51-121">이 명령은 `HKLM\System` 를 포함 하는 레지스트리 하위 키에 레지스트리 키를 표시 합니다 `ControlSet` .</span><span class="sxs-lookup"><span data-stu-id="99f51-121">This command displays the registry keys in the `HKLM\System` registry subkey that include `ControlSet`.</span></span>

<span data-ttu-id="99f51-122">`Resolve`매개 변수는 현재 공급자 경로에서 와일드 카드를 포함 하 여 조인 된 경로를 확인 하려고 시도 합니다.`HKLM:\`</span><span class="sxs-lookup"><span data-stu-id="99f51-122">The `Resolve` parameter, attempts to resolve the joined path, including wildcards from the current provider path `HKLM:\`</span></span>

### <span data-ttu-id="99f51-123">예 5: 여러 경로 루트를 하위 경로와 결합</span><span class="sxs-lookup"><span data-stu-id="99f51-123">Example 5: Combine multiple path roots with a child path</span></span>

```powershell
Join-Path -Path C:, D:, E:, F: -ChildPath New
```

```output
C:\New
D:\New
E:\New
F:\New
```

<span data-ttu-id="99f51-124">이 명령은 `Join-Path` 를 사용 하 여 여러 경로 루트를 하위 경로와 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-124">This command uses `Join-Path` to combine multiple path roots with a child path.</span></span>

> [!NOTE]
> <span data-ttu-id="99f51-125">로 지정 된 드라이브가 `Path` 존재 해야 합니다. 그렇지 않으면 해당 항목의 조인이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-125">The Drives specified by `Path` must exist or the join of that entry will fail.</span></span>

### <span data-ttu-id="99f51-126">예제 6: 파일 시스템 드라이브의 루트를 하위 경로와 결합</span><span class="sxs-lookup"><span data-stu-id="99f51-126">Example 6: Combine the roots of a file system drive with a child path</span></span>

```powershell
Get-PSDrive -PSProvider filesystem | ForEach-Object {$_.root} | Join-Path -ChildPath "Subdir"
```

```output
C:\Subdir
D:\Subdir
```

<span data-ttu-id="99f51-127">이 명령은 콘솔에 있는 각 PowerShell 파일 시스템 드라이브의 루트를 Subdir 하위 경로와 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-127">This command combines the roots of each PowerShell file system drive in the console with the Subdir child path.</span></span>

<span data-ttu-id="99f51-128">이 명령은 cmdlet을 사용 하 여 `Get-PSDrive` FileSystem 공급자가 지 원하는 PowerShell 드라이브를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-128">The command uses the `Get-PSDrive` cmdlet to get the PowerShell drives supported by the FileSystem provider.</span></span>
<span data-ttu-id="99f51-129">`ForEach-Object`문은 개체의 Root 속성만 선택 `PSDriveInfo` 하 고 지정 된 자식 경로와 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-129">The `ForEach-Object` statement selects only the Root property of the `PSDriveInfo` objects and combines it with the specified child path.</span></span>

<span data-ttu-id="99f51-130">출력은 컴퓨터의 PowerShell 드라이브에 C:\Program Files 디렉터리에 매핑된 드라이브가 포함 되어 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-130">The output shows that the PowerShell drives on the computer included a drive mapped to the C:\Program Files directory.</span></span>

### <span data-ttu-id="99f51-131">예제 7: 경로를 무한 개수에 결합</span><span class="sxs-lookup"><span data-stu-id="99f51-131">Example 7: Combine an indefinite number of paths</span></span>

```powershell
Join-Path a b c d e f g
```

```Output
a\b\c\d\e\f\g
```

<span data-ttu-id="99f51-132">`AdditionalChildPath`매개 변수를 사용 하면 개수에 제한 없이 경로를 조인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-132">The `AdditionalChildPath` parameter allows the joining of an unlimited number of paths.</span></span>

<span data-ttu-id="99f51-133">이 예제에서는 매개 변수 이름이 사용 되지 않으므로 "a"는에, " `Path` b"는 `ChildPath` 및 "c-g"에 바인딩합니다. `AdditionalChildPath`</span><span class="sxs-lookup"><span data-stu-id="99f51-133">In this example, no parameter names are used, thus "a" binds to `Path`, "b" to `ChildPath` and "c-g" to `AdditionalChildPath`</span></span>

## <span data-ttu-id="99f51-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="99f51-134">PARAMETERS</span></span>

### <span data-ttu-id="99f51-135">-AdditionalChildPath</span><span class="sxs-lookup"><span data-stu-id="99f51-135">-AdditionalChildPath</span></span>

<span data-ttu-id="99f51-136">*Path* 매개 변수의 값에 추가할 추가 요소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-136">Specifies additional elements to append to the value of the *Path* parameter.</span></span> <span data-ttu-id="99f51-137">`ChildPath`매개 변수는 여전히 필수 이며 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-137">The `ChildPath` parameter is still mandatory and must be specified as well.</span></span>

<span data-ttu-id="99f51-138">이 매개 변수는 `ValueFromRemainingArguments` 무제한 개수의 경로를 조인할 수 있도록 하는 속성을 사용 하 여 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-138">This parameter is specified with the `ValueFromRemainingArguments` property which enables joining an indefinite number of paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="99f51-139">-ChildPath</span><span class="sxs-lookup"><span data-stu-id="99f51-139">-ChildPath</span></span>

<span data-ttu-id="99f51-140">매개 변수 값에 추가할 요소를 지정 합니다 `Path` .</span><span class="sxs-lookup"><span data-stu-id="99f51-140">Specifies the elements to append to the value of the `Path` parameter.</span></span>
<span data-ttu-id="99f51-141">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-141">Wildcards are permitted.</span></span>
<span data-ttu-id="99f51-142">매개 변수 `ChildPath` 이름 ("ChildPath")은 선택 사항 이지만 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-142">The `ChildPath` parameter is required, although the parameter name ("ChildPath") is optional.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="99f51-143">-Credential</span><span class="sxs-lookup"><span data-stu-id="99f51-143">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="99f51-144">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-144">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="99f51-145">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-145">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="99f51-146">-Path</span><span class="sxs-lookup"><span data-stu-id="99f51-146">-Path</span></span>

<span data-ttu-id="99f51-147">하위 경로를 추가할 기본 경로를 하나 이상 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-147">Specifies the main path (or paths) to which the child-path is appended.</span></span>
<span data-ttu-id="99f51-148">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-148">Wildcards are permitted.</span></span>

<span data-ttu-id="99f51-149">값은 경로 `Path` 를 조인 하는 공급자를 결정 하 고 경로 구분 기호를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-149">The value of `Path` determines which provider joins the paths and adds the path delimiters.</span></span>
<span data-ttu-id="99f51-150">매개 변수 `Path` 이름 ("Path")은 선택 사항 이지만 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-150">The `Path` parameter is required, although the parameter name ("Path") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="99f51-151">-해결</span><span class="sxs-lookup"><span data-stu-id="99f51-151">-Resolve</span></span>

<span data-ttu-id="99f51-152">이 cmdlet이 현재 공급자의 조인 된 경로를 확인 하려고 시도 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-152">Indicates that this cmdlet should attempt to resolve the joined path from the current provider.</span></span>

- <span data-ttu-id="99f51-153">와일드 카드를 사용 하는 경우 cmdlet은 조인 된 경로와 일치 하는 모든 경로를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-153">If wildcards are used, the cmdlet returns all paths that match the joined path.</span></span>
- <span data-ttu-id="99f51-154">와일드 **카드를 사용 하지 않는** 경우 경로가 없으면 cmdlet이 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-154">If **no** wildcards are used, the cmdlet will error if the path does not exist.</span></span>

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

### <span data-ttu-id="99f51-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="99f51-155">CommonParameters</span></span>

<span data-ttu-id="99f51-156">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="99f51-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="99f51-157">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99f51-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="99f51-158">입력</span><span class="sxs-lookup"><span data-stu-id="99f51-158">INPUTS</span></span>

### <span data-ttu-id="99f51-159">System.String</span><span class="sxs-lookup"><span data-stu-id="99f51-159">System.String</span></span>

<span data-ttu-id="99f51-160">이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-160">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="99f51-161">출력</span><span class="sxs-lookup"><span data-stu-id="99f51-161">OUTPUTS</span></span>

### <span data-ttu-id="99f51-162">System.String</span><span class="sxs-lookup"><span data-stu-id="99f51-162">System.String</span></span>

<span data-ttu-id="99f51-163">이 cmdlet은 결과 경로를 포함 하는 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-163">This cmdlet returns a string that contains the resulting path.</span></span>

## <span data-ttu-id="99f51-164">참고</span><span class="sxs-lookup"><span data-stu-id="99f51-164">NOTES</span></span>

<span data-ttu-id="99f51-165">경로 명사 (Path cmdlet)를 포함 하는 cmdlet은 경로 이름을 조작 하 고 모든 PowerShell 공급자가 해석할 수 있는 간결한 형식으로 이름을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-165">The cmdlets that contain the Path noun (the Path cmdlets) manipulate path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="99f51-166">이 cmdlet은 경로 이름의 전체 또는 일부를 특정 형식으로 표시하려는 프로그램 및 스크립트에 사용하도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-166">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="99f51-167">Dirname, Normpath, Realpath, Join 또는 기타 경로 조작자를 사용할 때와 같은 방법으로 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-167">Use them like you would use Dirname, Normpath, Realpath, Join, or other path manipulators.</span></span>

<span data-ttu-id="99f51-168">`FileSystem`, 및 공급자를 포함 하 여 여러 공급자와 함께 path cmdlet을 사용할 수 있습니다 `Registry` `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="99f51-168">You can use the path cmdlets with several providers, including the `FileSystem`, `Registry`, and `Certificate` providers.</span></span>

<span data-ttu-id="99f51-169">이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-169">This cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="99f51-170">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="99f51-170">To list the providers available in your session, type `Get-PSProvider`.</span></span>
<span data-ttu-id="99f51-171">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99f51-171">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="99f51-172">관련 링크</span><span class="sxs-lookup"><span data-stu-id="99f51-172">RELATED LINKS</span></span>

[<span data-ttu-id="99f51-173">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="99f51-173">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="99f51-174">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="99f51-174">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="99f51-175">Split-Path</span><span class="sxs-lookup"><span data-stu-id="99f51-175">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="99f51-176">Test-Path</span><span class="sxs-lookup"><span data-stu-id="99f51-176">Test-Path</span></span>](Test-Path.md)

[<span data-ttu-id="99f51-177">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="99f51-177">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="99f51-178">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="99f51-178">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="99f51-179">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="99f51-179">Get-PSDrive</span></span>](Get-PSDrive.md)
