---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Item
ms.openlocfilehash: c4a0243c528cbe1a28cad99cf6fa8d91018d9b3c
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692676"
---
# <span data-ttu-id="c968b-102">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="c968b-102">Remove-Item</span></span>

## <span data-ttu-id="c968b-103">개요</span><span class="sxs-lookup"><span data-stu-id="c968b-103">SYNOPSIS</span></span>
<span data-ttu-id="c968b-104">지정된 항목을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-104">Deletes the specified items.</span></span>

## <span data-ttu-id="c968b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c968b-105">SYNTAX</span></span>

### <span data-ttu-id="c968b-106">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="c968b-106">Path (Default)</span></span>

```
Remove-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="c968b-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c968b-107">LiteralPath</span></span>

```
Remove-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="c968b-108">설명</span><span class="sxs-lookup"><span data-stu-id="c968b-108">DESCRIPTION</span></span>

<span data-ttu-id="c968b-109">`Remove-Item`Cmdlet은 하나 이상의 항목을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-109">The `Remove-Item` cmdlet deletes one or more items.</span></span> <span data-ttu-id="c968b-110">여러 공급자에서 지원 되므로 파일, 폴더, 레지스트리 키, 변수, 별칭 및 함수를 포함 하 여 다양 한 유형의 항목을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-110">Because it is supported by many providers, it can delete many different types of items, including files, folders, registry keys, variables, aliases, and functions.</span></span>

## <span data-ttu-id="c968b-111">예제</span><span class="sxs-lookup"><span data-stu-id="c968b-111">EXAMPLES</span></span>

### <span data-ttu-id="c968b-112">예 1: 파일 이름 확장명이 있는 파일 삭제</span><span class="sxs-lookup"><span data-stu-id="c968b-112">Example 1: Delete files that have any file name extension</span></span>

<span data-ttu-id="c968b-113">이 예에서는 폴더에서 점 ()이 포함 된 모든 파일을 삭제 `.` `C:\Test` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-113">This example deletes all of the files that have names that include a dot (`.`) from the `C:\Test` folder.</span></span> <span data-ttu-id="c968b-114">이 명령에는 점이 지정 되어 있으므로 파일 이름 확장명이 없는 폴더나 파일은 삭제 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-114">Because the command specifies a dot, the command does not delete folders or files that have no file name extension.</span></span>

```powershell
Remove-Item C:\Test\*.*
```

### <span data-ttu-id="c968b-115">예제 2: 폴더의 문서 파일 일부 삭제</span><span class="sxs-lookup"><span data-stu-id="c968b-115">Example 2: Delete some of the document files in a folder</span></span>

<span data-ttu-id="c968b-116">이 예에서는 현재 폴더에서 파일 이름 확장명이 있는 모든 파일을 삭제 하 `.doc` 고가 포함 되지 않은 이름을 삭제 `*1*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-116">This example deletes from the current folder all files that have a `.doc` file name extension and a name that does not include `*1*`.</span></span>

```powershell
Remove-Item * -Include *.doc -Exclude *1*
```

<span data-ttu-id="c968b-117">와일드 카드 문자 ()를 사용 하 여 `*` 현재 폴더의 내용을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-117">It uses the wildcard character (`*`) to specify the contents of the current folder.</span></span> <span data-ttu-id="c968b-118">**Include** 및 **Exclude** 매개 변수를 사용 하 여 삭제할 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-118">It uses the **Include** and **Exclude** parameters to specify the files to delete.</span></span>

### <span data-ttu-id="c968b-119">예제 3: 숨겨진 읽기 전용 파일 삭제</span><span class="sxs-lookup"><span data-stu-id="c968b-119">Example 3: Delete hidden, read-only files</span></span>

<span data-ttu-id="c968b-120">이 명령은 *숨겨지거나* *읽기 전용인* 파일을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-120">This command deletes a file that is both *hidden* and *read-only*.</span></span>

```powershell
Remove-Item -Path C:\Test\hidden-RO-file.txt -Force
```

<span data-ttu-id="c968b-121">**Path** 매개 변수를 사용 하 여 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-121">It uses the **Path** parameter to specify the file.</span></span> <span data-ttu-id="c968b-122">**Force** 매개 변수를 사용 하 여 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-122">It uses the **Force** parameter to delete it.</span></span> <span data-ttu-id="c968b-123">**Force** 가 없으면 _읽기_ 전용 파일이 나 _숨겨진_ 파일을 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-123">Without **Force**, you cannot delete _read-only_ or _hidden_ files.</span></span>

### <span data-ttu-id="c968b-124">예 4: 재귀적으로 하위 폴더의 파일 삭제</span><span class="sxs-lookup"><span data-stu-id="c968b-124">Example 4: Delete files in subfolders recursively</span></span>

<span data-ttu-id="c968b-125">이 명령은 현재 폴더와 모든 하위 폴더에 있는 모든 CSV 파일을 재귀적으로 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-125">This command deletes all of the CSV files in the current folder and all subfolders recursively.</span></span>

<span data-ttu-id="c968b-126">의 **재귀적** 매개 변수에는 `Remove-Item` 알려진 문제가 있으므로이 예제의 명령은를 사용 하 여 `Get-ChildItem` 원하는 파일을 가져온 다음 파이프라인 연산자를 사용 하 여에 전달 `Remove-Item` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-126">Because the **Recurse** parameter in `Remove-Item` has a known issue, the command in this example uses `Get-ChildItem` to get the desired files, and then uses the pipeline operator to pass them to `Remove-Item`.</span></span>

```powershell
Get-ChildItem * -Include *.csv -Recurse | Remove-Item
```

<span data-ttu-id="c968b-127">명령에서 `Get-ChildItem` **Path** 에는 `*` 현재 폴더의 콘텐츠를 나타내는 ()의 값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-127">In the `Get-ChildItem` command, **Path** has a value of (`*`), which represents the contents of the current folder.</span></span> <span data-ttu-id="c968b-128">**Include** 를 사용 하 여 CSV 파일 형식을 지정 하 고 재귀적으로 검색을 수행 하 **는 데 재귀를 사용 합니다** .</span><span class="sxs-lookup"><span data-stu-id="c968b-128">It uses **Include** to specify the CSV file type, and it uses **Recurse** to make the retrieval recursive.</span></span> <span data-ttu-id="c968b-129">파일 형식 (예:)을 지정 하려고 하면 `-Path *.csv` cmdlet은 검색의 주체를 자식 항목이 없는 파일로 해석 하 고 **재귀적** 으로 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-129">If you try to specify the file type the path, such as `-Path *.csv`, the cmdlet interprets the subject of the search to be a file that has no child items, and **Recurse** fails.</span></span>

### <span data-ttu-id="c968b-130">예 5: 재귀적으로 하위 키 삭제</span><span class="sxs-lookup"><span data-stu-id="c968b-130">Example 5: Delete subkeys recursively</span></span>

<span data-ttu-id="c968b-131">이 명령은 "OldApp" 레지스트리 키와 모든 하위 키 및 값을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-131">This command deletes the "OldApp" registry key and all its subkeys and values.</span></span> <span data-ttu-id="c968b-132">를 사용 `Remove-Item` 하 여 키를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-132">It uses `Remove-Item` to remove the key.</span></span> <span data-ttu-id="c968b-133">경로를 지정 하지만 선택적 매개 변수 이름 (**path**)은 생략 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-133">The path is specified, but the optional parameter name (**Path**) is omitted.</span></span>

<span data-ttu-id="c968b-134">**재귀** 매개 변수는 "oldapp" 키의 모든 내용을 재귀적으로 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-134">The **Recurse** parameter deletes all of the contents of the "OldApp" key recursively.</span></span> <span data-ttu-id="c968b-135">키에 하위 키가 포함 되어 있고 **재귀** 매개 변수를 생략 하면 키의 내용을 삭제할 것인지를 확인 하는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-135">If the key contains subkeys and you omit the **Recurse** parameter, you are prompted to confirm that you want to delete the contents of the key.</span></span>

```powershell
Remove-Item HKLM:\Software\MyCompany\OldApp -Recurse
```

### <span data-ttu-id="c968b-136">예제 6: 특수 문자를 사용 하 여 파일 삭제</span><span class="sxs-lookup"><span data-stu-id="c968b-136">Example 6: Deleting files with special characters</span></span>

<span data-ttu-id="c968b-137">다음 예제에서는 대괄호 또는 괄호와 같은 특수 문자가 포함 된 파일을 삭제 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-137">The following example shows how to delete files that contain special characters like brackets or parentheses.</span></span>

```powershell
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*'
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*' | ForEach-Object { Remove-Item -LiteralPath $_.Name }
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
```

### <span data-ttu-id="c968b-138">예 7: 대체 데이터 스트림 제거</span><span class="sxs-lookup"><span data-stu-id="c968b-138">Example 7: Remove an alternate data stream</span></span>

<span data-ttu-id="c968b-139">이 예에서는 cmdlet의 **Stream** 동적 매개 변수를 사용 하 여 `Remove-Item` 대체 데이터 스트림을 삭제 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-139">This example shows how to use the **Stream** dynamic parameter of the `Remove-Item` cmdlet to delete an alternate data stream.</span></span> <span data-ttu-id="c968b-140">Stream 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-140">The stream parameter is introduced in Windows PowerShell 3.0.</span></span>

```powershell
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
   FileName: \\C:\Test\Copy-Script.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

```

```powershell
Remove-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
Get-Item : Could not open alternate data stream 'Zone.Identifier' of file 'C:\Test\Copy-Script.ps1'.
At line:1 char:1
+ Get-Item 'C:\Test\Copy-Script.ps1' -Stream Zone.Identifier
+ [!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()]~~
    + CategoryInfo          : ObjectNotFound: (C:\Test\Copy-Script.ps1:String) [Get-Item], FileNotFoundE
   xception
    + FullyQualifiedErrorId : AlternateDataStreamNotFound,Microsoft.PowerShell.Commands.GetItemCommand

```

<span data-ttu-id="c968b-141">**Stream** 매개 변수는 `Get-Item` `Zone.Identifier` 파일의 스트림을 가져옵니다 `Copy-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="c968b-141">The **Stream** parameter `Get-Item` gets the `Zone.Identifier` stream of the `Copy-Script.ps1` file.</span></span> <span data-ttu-id="c968b-142">`Remove-Item`**stream** 매개 변수를 사용 하 여 `Zone.Identifier` 파일의 스트림을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-142">`Remove-Item` uses the **Stream** parameter to remove the `Zone.Identifier` stream of the file.</span></span> <span data-ttu-id="c968b-143">마지막으로이 `Get-Item` cmdlet은 스트림이 삭제 된 것을 보여 줍니다 `Zone.Identifier` .</span><span class="sxs-lookup"><span data-stu-id="c968b-143">Finally, the `Get-Item` cmdlet shows that the `Zone.Identifier` stream was deleted.</span></span>

## <span data-ttu-id="c968b-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c968b-144">PARAMETERS</span></span>

### <span data-ttu-id="c968b-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="c968b-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="c968b-146">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-146">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="c968b-147">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="c968b-148">-제외</span><span class="sxs-lookup"><span data-stu-id="c968b-148">-Exclude</span></span>

<span data-ttu-id="c968b-149">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-149">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="c968b-150">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-150">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c968b-151">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-151">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="c968b-152">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-152">Wildcard characters are permitted.</span></span> <span data-ttu-id="c968b-153">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="c968b-153">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="c968b-154">-Filter</span><span class="sxs-lookup"><span data-stu-id="c968b-154">-Filter</span></span>

<span data-ttu-id="c968b-155">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-155">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="c968b-156">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-156">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="c968b-157">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-157">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span> <span data-ttu-id="c968b-158">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-158">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="c968b-159">-Force</span><span class="sxs-lookup"><span data-stu-id="c968b-159">-Force</span></span>

<span data-ttu-id="c968b-160">숨겨진 파일 또는 읽기 전용 파일이 나 읽기 전용 별칭 또는 변수와 같이 다른 방법으로는 변경할 수 없는 항목을 cmdlet에서 제거 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-160">Forces the cmdlet to remove items that cannot otherwise be changed, such as hidden or read-only files or read-only aliases or variables.</span></span> <span data-ttu-id="c968b-161">cmdlet은 상수 별칭 또는 변수를 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-161">The cmdlet cannot remove constant aliases or variables.</span></span>
<span data-ttu-id="c968b-162">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-162">Implementation varies from provider to provider.</span></span> <span data-ttu-id="c968b-163">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c968b-163">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="c968b-164">**Force** 매개 변수를 사용 하는 경우에도 cmdlet은 보안 제한을 재정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-164">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="c968b-165">-포함</span><span class="sxs-lookup"><span data-stu-id="c968b-165">-Include</span></span>

<span data-ttu-id="c968b-166">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-166">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="c968b-167">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-167">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c968b-168">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-168">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="c968b-169">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-169">Wildcard characters are permitted.</span></span> <span data-ttu-id="c968b-170">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="c968b-170">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="c968b-171">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c968b-171">-LiteralPath</span></span>

<span data-ttu-id="c968b-172">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-172">Specifies a path to one or more locations.</span></span> <span data-ttu-id="c968b-173">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-173">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="c968b-174">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-174">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="c968b-175">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="c968b-175">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="c968b-176">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-176">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="c968b-177">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c968b-177">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="c968b-178">-Path</span><span class="sxs-lookup"><span data-stu-id="c968b-178">-Path</span></span>

<span data-ttu-id="c968b-179">제거할 항목의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-179">Specifies a path of the items being removed.</span></span>
<span data-ttu-id="c968b-180">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-180">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="c968b-181">-재귀</span><span class="sxs-lookup"><span data-stu-id="c968b-181">-Recurse</span></span>

<span data-ttu-id="c968b-182">이 cmdlet은 지정 된 위치와 해당 위치의 모든 하위 항목에서 항목을 삭제 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-182">Indicates that this cmdlet deletes the items in the specified locations and in all child items of the locations.</span></span>

<span data-ttu-id="c968b-183">**Include** 매개 변수와 함께 사용 하는 경우 **재귀** 매개 변수는 모든 하위 폴더 또는 모든 자식 항목을 삭제 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-183">When it is used with the **Include** parameter, the **Recurse** parameter might not delete all subfolders or all child items.</span></span> <span data-ttu-id="c968b-184">이것은 알려진 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-184">This is a known issue.</span></span> <span data-ttu-id="c968b-185">해결 방법으로, `Get-ChildItem -Recurse` `Remove-Item` 이 항목의 "예제 4"에 설명 된 대로 명령의 파이프 결과를로 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-185">As a workaround, try piping results of the `Get-ChildItem -Recurse` command to `Remove-Item`, as described in "Example 4" in this topic.</span></span>

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

### <span data-ttu-id="c968b-186">-스트림</span><span class="sxs-lookup"><span data-stu-id="c968b-186">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="c968b-187">이 매개 변수는 Windows 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-187">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="c968b-188">**Stream** 매개 변수는 파일 시스템 공급자가에 추가 하는 동적 매개 변수입니다 `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="c968b-188">The **Stream** parameter is a dynamic parameter that the FileSystem provider adds to `Remove-Item`.</span></span>
<span data-ttu-id="c968b-189">이 매개 변수는 파일 시스템 드라이브에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-189">This parameter works only in file system drives.</span></span>

<span data-ttu-id="c968b-190">를 사용 `Remove-Item` 하 여와 같은 대체 데이터 스트림을 삭제할 수 있습니다 `Zone.Identifier` .</span><span class="sxs-lookup"><span data-stu-id="c968b-190">You can use `Remove-Item` to delete an alternative data stream, such as `Zone.Identifier`.</span></span>
<span data-ttu-id="c968b-191">하지만 인터넷에서 다운로드한 파일을 차단하는 보안 검사를 제거하는 것은 권장되는 방법이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-191">However, it is not the recommended way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="c968b-192">다운로드 한 파일이 안전한 지 확인 하려면 cmdlet을 사용 `Unblock-File` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-192">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="c968b-193">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-193">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c968b-194">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c968b-194">-Confirm</span></span>

<span data-ttu-id="c968b-195">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-195">Prompts you for confirmation before running the cmdlet.</span></span> <span data-ttu-id="c968b-196">자세한 내용은 다음 아티클을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c968b-196">For more information, see the following articles:</span></span>

- [<span data-ttu-id="c968b-197">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="c968b-197">about_Preference_Variables</span></span>](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)
- [<span data-ttu-id="c968b-198">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="c968b-198">about_Functions_CmdletBindingAttribute</span></span>](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)

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

### <span data-ttu-id="c968b-199">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c968b-199">-WhatIf</span></span>

<span data-ttu-id="c968b-200">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-200">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="c968b-201">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-201">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c968b-202">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c968b-202">CommonParameters</span></span>

<span data-ttu-id="c968b-203">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c968b-203">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c968b-204">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c968b-204">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>


## <span data-ttu-id="c968b-205">입력</span><span class="sxs-lookup"><span data-stu-id="c968b-205">INPUTS</span></span>

### <span data-ttu-id="c968b-206">System.String</span><span class="sxs-lookup"><span data-stu-id="c968b-206">System.String</span></span>

<span data-ttu-id="c968b-207">경로를 포함 하지만 리터럴 경로를 포함 하지 않는 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-207">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="c968b-208">출력</span><span class="sxs-lookup"><span data-stu-id="c968b-208">OUTPUTS</span></span>

### <span data-ttu-id="c968b-209">None</span><span class="sxs-lookup"><span data-stu-id="c968b-209">None</span></span>

<span data-ttu-id="c968b-210">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-210">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="c968b-211">참고</span><span class="sxs-lookup"><span data-stu-id="c968b-211">NOTES</span></span>

<span data-ttu-id="c968b-212">`Remove-Item`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-212">The `Remove-Item` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="c968b-213">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PsProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-213">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="c968b-214">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c968b-214">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="c968b-215">**재귀** 매개 변수를 사용 하지 않고 항목을 포함 하는 폴더를 삭제 하려고 하면 cmdlet에서 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-215">When you try to delete a folder that contains items without using the **Recurse** parameter, the cmdlet prompts for confirmation.</span></span> <span data-ttu-id="c968b-216">`-Confirm:$false`를 사용 해도 프롬프트가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-216">Using `-Confirm:$false` does not suppress the prompt.</span></span> <span data-ttu-id="c968b-217">이것은 의도적인 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c968b-217">This is by design.</span></span>

## <span data-ttu-id="c968b-218">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c968b-218">RELATED LINKS</span></span>

[<span data-ttu-id="c968b-219">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="c968b-219">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="c968b-220">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="c968b-220">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="c968b-221">Get-Item</span><span class="sxs-lookup"><span data-stu-id="c968b-221">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="c968b-222">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="c968b-222">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="c968b-223">Move-Item</span><span class="sxs-lookup"><span data-stu-id="c968b-223">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="c968b-224">New-Item</span><span class="sxs-lookup"><span data-stu-id="c968b-224">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="c968b-225">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c968b-225">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="c968b-226">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="c968b-226">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="c968b-227">Set-Item</span><span class="sxs-lookup"><span data-stu-id="c968b-227">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="c968b-228">about_Providers</span><span class="sxs-lookup"><span data-stu-id="c968b-228">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="c968b-229">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="c968b-229">about_Preference_Variables</span></span>](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)

[<span data-ttu-id="c968b-230">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="c968b-230">about_Functions_CmdletBindingAttribute</span></span>](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)
