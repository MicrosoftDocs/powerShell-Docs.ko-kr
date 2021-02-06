---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-Item
ms.openlocfilehash: a47c017371fe5fe87618c11551cd1ecba76d5c60
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601862"
---
# <span data-ttu-id="1b60d-102">Move-Item</span><span class="sxs-lookup"><span data-stu-id="1b60d-102">Move-Item</span></span>

## <span data-ttu-id="1b60d-103">개요</span><span class="sxs-lookup"><span data-stu-id="1b60d-103">SYNOPSIS</span></span>
<span data-ttu-id="1b60d-104">항목의 위치를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-104">Moves an item from one location to another.</span></span>

## <span data-ttu-id="1b60d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1b60d-105">SYNTAX</span></span>

### <span data-ttu-id="1b60d-106">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="1b60d-106">Path (Default)</span></span>

```
Move-Item [-Path] <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1b60d-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1b60d-107">LiteralPath</span></span>

```
Move-Item -LiteralPath <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1b60d-108">설명</span><span class="sxs-lookup"><span data-stu-id="1b60d-108">DESCRIPTION</span></span>

<span data-ttu-id="1b60d-109">`Move-Item`Cmdlet은 속성, 내용 및 자식 항목을 포함 하 여 항목을 한 위치에서 다른 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-109">The `Move-Item` cmdlet moves an item, including its properties, contents, and child items, from one location to another location.</span></span> <span data-ttu-id="1b60d-110">이동하기 전과 후의 위치가 동일한 공급자에서 지원되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-110">The locations must be supported by the same provider.</span></span>
<span data-ttu-id="1b60d-111">예를 들어 디렉터리 간에 파일 또는 하위 디렉터리를 이동하거나 레지스트리 키 간에 레지스트리 하위 키를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-111">For example, it can move a file or subdirectory from one directory to another or move a registry subkey from one key to another.</span></span>
<span data-ttu-id="1b60d-112">항목을 이동하면 원래 위치에서 해당 항목이 삭제되고 새 위치에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-112">When you move an item, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="1b60d-113">예제</span><span class="sxs-lookup"><span data-stu-id="1b60d-113">EXAMPLES</span></span>

### <span data-ttu-id="1b60d-114">예제 1: 파일을 다른 디렉터리로 이동 하 고 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-114">Example 1: Move a file to another directory and rename it</span></span>

<span data-ttu-id="1b60d-115">이 명령은 `Test.txt` 드라이브에서 디렉터리로 파일을 이동 하 `C:` `E:\Temp` 고에서로 이름을 바꿉니다 `test.txt` `tst.txt` .</span><span class="sxs-lookup"><span data-stu-id="1b60d-115">This command moves the `Test.txt` file from the `C:` drive to the `E:\Temp` directory and renames it from `test.txt` to `tst.txt`.</span></span>

```powershell
Move-Item -Path C:\test.txt -Destination E:\Temp\tst.txt
```

### <span data-ttu-id="1b60d-116">예제 2: 디렉터리 및 해당 콘텐츠를 다른 디렉터리로 이동</span><span class="sxs-lookup"><span data-stu-id="1b60d-116">Example 2: Move a directory and its contents to another directory</span></span>

<span data-ttu-id="1b60d-117">이 명령은 `C:\Temp` 디렉터리와 해당 콘텐츠를 `C:\Logs` 디렉터리로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-117">This command moves the `C:\Temp` directory and its contents to the `C:\Logs` directory.</span></span>
<span data-ttu-id="1b60d-118">"Temp" 디렉터리와 모든 하위 디렉터리 및 파일이 "Logs" 디렉터리에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-118">The "Temp" directory, and all of its subdirectories and files, then appear in the "Logs" directory.</span></span>

```powershell
Move-Item -Path C:\Temp -Destination C:\Logs
```

### <span data-ttu-id="1b60d-119">예제 3: 지정 된 확장의 모든 파일을 현재 디렉터리에서 다른 디렉터리로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-119">Example 3: Move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="1b60d-120">이 명령은 `*.txt` 현재 디렉터리 (점 ()으로 표시 됨)에 있는 모든 텍스트 파일 () `.` 을 `C:\Logs` 디렉터리로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-120">This command moves all of the text files (`*.txt`) in the current directory (represented by a dot (`.`)) to the `C:\Logs` directory.</span></span>

```powershell
Move-Item -Path .\*.txt -Destination C:\Logs
```

### <span data-ttu-id="1b60d-121">예제 4: 지정 된 확장의 모든 파일을 현재 디렉터리에서 다른 디렉터리로 재귀적으로 이동</span><span class="sxs-lookup"><span data-stu-id="1b60d-121">Example 4: Recursively move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="1b60d-122">이 명령은 현재 디렉터리와 모든 하위 디렉터리의 모든 텍스트 파일을 "C:\TextFiles" 디렉터리로 재귀적으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-122">This command moves all of the text files from the current directory and all subdirectories, recursively, to the "C:\TextFiles" directory.</span></span>

```powershell
Get-ChildItem -Path ".\*.txt" -Recurse | Move-Item -Destination "C:\TextFiles"
```

<span data-ttu-id="1b60d-123">이 명령은 cmdlet을 사용 하 여 `Get-ChildItem` 현재 디렉터리에 있는 모든 자식 항목 (점으로 표시 \[ \] )과 "*.txt" 파일 이름 확장명을 가진 하위 디렉터리를 가져옵니다. 재귀 매개 변수 **를** 사용 하 여 검색 재귀를 수행 하 고 Include 매개 변수를 사용* 하 여 ".txt" 파일로 검색을 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-123">The command uses the `Get-ChildItem` cmdlet to get all of the child items in the current directory (represented by the dot \[.\]) and its subdirectories that have a "*.txt" file name extension. It uses the **Recurse** parameter to make the retrieval recursive and the Include parameter to limit the retrieval to "*.txt" files.</span></span>

<span data-ttu-id="1b60d-124">파이프라인 연산자 ( `|` )는이 명령의 결과를에 전송 하 여 `Move-Item` 텍스트 파일을 "textfiles" 디렉터리로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-124">The pipeline operator (`|`) sends the results of this command to `Move-Item`, which moves the text files to the "TextFiles" directory.</span></span>

<span data-ttu-id="1b60d-125">"C:\Textfiles"로 이동 하는 파일의 이름이 같은 경우에는에서 `Move-Item` 오류를 표시 하 고 계속 되지만 각 이름을 가진 하나의 파일만 "C:\Textfiles"로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-125">If files that are to be moved to "C:\Textfiles" have the same name, `Move-Item` displays an error and continues, but it moves only one file with each name to "C:\Textfiles".</span></span>
<span data-ttu-id="1b60d-126">나머지 파일은 원래 디렉터리에 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-126">The other files remain in their original directories.</span></span>

<span data-ttu-id="1b60d-127">"Textfiles" 디렉터리 (또는 대상 경로의 다른 요소)가 없을 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-127">If the "Textfiles" directory (or any other element of the destination path) does not exist, the command fails.</span></span>
<span data-ttu-id="1b60d-128">**Force** 매개 변수를 사용 하더라도 누락 된 디렉터리는 생성 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-128">The missing directory is not created for you, even if you use the **Force** parameter.</span></span>
<span data-ttu-id="1b60d-129">`Move-Item` 첫 번째 항목을 "Textfiles" 라는 파일로 이동한 다음 파일이 이미 있음을 설명 하는 오류를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-129">`Move-Item` moves the first item to a file called "Textfiles" and then displays an error explaining that the file already exists.</span></span>

<span data-ttu-id="1b60d-130">또한 기본적으로는 `Get-ChildItem` 숨겨진 파일을 이동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-130">Also, by default, `Get-ChildItem` does not move hidden files.</span></span>
<span data-ttu-id="1b60d-131">숨겨진 파일을 이동 하려면에 **Force** 매개 변수를 사용 `Get-ChildItem` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-131">To move hidden files, use the **Force** parameter with `Get-ChildItem`.</span></span>

> [!NOTE]
> <span data-ttu-id="1b60d-132">Windows PowerShell 2.0에서 cmdlet의 **재귀** 매개 변수를 사용 하는 경우 `Get-ChildItem` **Path** 매개 변수 값은 컨테이너 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-132">In Windows PowerShell 2.0, when using the **Recurse** parameter of the `Get-ChildItem` cmdlet, the value of the **Path** parameter must be a container.</span></span>
> <span data-ttu-id="1b60d-133">**Include** 매개 변수를 사용 하 여 .txt 파일 이름 확장명 필터 ()를 지정 합니다 `Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles` .</span><span class="sxs-lookup"><span data-stu-id="1b60d-133">Use the **Include** parameter to specify the .txt file name extension filter (`Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles`).</span></span>

### <span data-ttu-id="1b60d-134">예 5: 레지스트리 키 및 값을 다른 키로 이동</span><span class="sxs-lookup"><span data-stu-id="1b60d-134">Example 5: Move registry keys and values to another key</span></span>

<span data-ttu-id="1b60d-135">이 명령은의 "MyCompany" 레지스트리 키에 있는 레지스트리 키와 값 `HKLM\Software` 을 "MyNewCompany" 키로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-135">This command moves the registry keys and values within the "MyCompany" registry key in `HKLM\Software` to the "MyNewCompany" key.</span></span>
<span data-ttu-id="1b60d-136">와일드 카드 문자 ( `*` )는 키 자체가 아니라 "MyCompany" 키의 내용을 이동 해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-136">The wildcard character (`*`) indicates that the contents of the "MyCompany" key should be moved, not the key itself.</span></span>
<span data-ttu-id="1b60d-137">이 명령에서 선택적 **경로** 및 **대상** 매개 변수 이름은 생략 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-137">In this command, the optional **Path** and **Destination** parameter names are omitted.</span></span>

```powershell
Move-Item "HKLM:\software\mycompany\*" "HKLM:\software\mynewcompany"
```

### <span data-ttu-id="1b60d-138">예제 6: 디렉터리 및 해당 콘텐츠를 지정 된 디렉터리의 하위 디렉터리로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-138">Example 6: Move a directory and its contents to a subdirectory of the specified directory</span></span>

<span data-ttu-id="1b60d-139">이 명령은 "로그 \[ 9 월 \` 06 \] " 디렉터리와 해당 내용을 "logs \[ 2006 \] " 디렉터리로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-139">This command moves the "Logs\[Sept\`06\]" directory (and its contents) into the "Logs\[2006\]" directory.</span></span>

```powershell
Move-Item -LiteralPath 'Logs[Sept`06]' -Destination 'Logs[2006]'
```

<span data-ttu-id="1b60d-140">원본 디렉터리 이름에 왼쪽 대괄호와 오른쪽 대괄호 문자 ("  \[ " 및 "")가 포함 되어 있기 때문에 LiteralPath 매개 변수가 경로 대신 사용 됩니다 \] .</span><span class="sxs-lookup"><span data-stu-id="1b60d-140">The **LiteralPath** parameter is used instead of **Path**, because the original directory name includes left bracket and right bracket characters ("\[" and "\]").</span></span>
<span data-ttu-id="1b60d-141">또한 경로는 작은따옴표 (' ')로 묶여 있으므로 억음 기호 ( \` )는 잘못 해석 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-141">The path is also enclosed in single quotation marks (' '), so that the backtick symbol (\`) is not misinterpreted.</span></span>

<span data-ttu-id="1b60d-142">대상 변수는 잘못 해석 될 수 있는 대괄호가 포함 되어 있으므로 작은따옴표 안에 포함 해야 하기 때문에 **destination** 매개 변수에는 리터럴 경로가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-142">The **Destination** parameter does not require a literal path, because the Destination variable also must be enclosed in single quotation marks, because it includes brackets that can be misinterpreted.</span></span>

## <span data-ttu-id="1b60d-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1b60d-143">PARAMETERS</span></span>

### <span data-ttu-id="1b60d-144">-Credential</span><span class="sxs-lookup"><span data-stu-id="1b60d-144">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="1b60d-145">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-145">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="1b60d-146">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-146">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="1b60d-147">-Destination</span><span class="sxs-lookup"><span data-stu-id="1b60d-147">-Destination</span></span>

<span data-ttu-id="1b60d-148">항목을 이동할 위치의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-148">Specifies the path to the location where the items are being moved.</span></span>
<span data-ttu-id="1b60d-149">기본값은 현재 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-149">The default is the current directory.</span></span>
<span data-ttu-id="1b60d-150">와일드카드를 사용할 수 있지만 결과는 하나의 위치를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-150">Wildcards are permitted, but the result must specify a single location.</span></span>

<span data-ttu-id="1b60d-151">이동할 항목의 이름을 바꾸려면 **Destination** 매개 변수 값에 새 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-151">To rename the item being moved, specify a new name in the value of the **Destination** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="1b60d-152">-제외</span><span class="sxs-lookup"><span data-stu-id="1b60d-152">-Exclude</span></span>

<span data-ttu-id="1b60d-153">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-153">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="1b60d-154">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-154">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1b60d-155">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-155">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="1b60d-156">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-156">Wildcard characters are permitted.</span></span> <span data-ttu-id="1b60d-157">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="1b60d-157">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="1b60d-158">-Filter</span><span class="sxs-lookup"><span data-stu-id="1b60d-158">-Filter</span></span>

<span data-ttu-id="1b60d-159">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-159">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="1b60d-160">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-160">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="1b60d-161">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-161">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="1b60d-162">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-162">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="1b60d-163">-Force</span><span class="sxs-lookup"><span data-stu-id="1b60d-163">-Force</span></span>

<span data-ttu-id="1b60d-164">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-164">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="1b60d-165">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-165">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="1b60d-166">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b60d-166">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="1b60d-167">-포함</span><span class="sxs-lookup"><span data-stu-id="1b60d-167">-Include</span></span>

<span data-ttu-id="1b60d-168">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-168">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="1b60d-169">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-169">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1b60d-170">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-170">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="1b60d-171">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-171">Wildcard characters are permitted.</span></span> <span data-ttu-id="1b60d-172">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="1b60d-172">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="1b60d-173">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1b60d-173">-LiteralPath</span></span>

<span data-ttu-id="1b60d-174">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-174">Specifies a path to one or more locations.</span></span> <span data-ttu-id="1b60d-175">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-175">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="1b60d-176">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-176">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="1b60d-177">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="1b60d-177">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="1b60d-178">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-178">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="1b60d-179">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b60d-179">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="1b60d-180">-PassThru</span><span class="sxs-lookup"><span data-stu-id="1b60d-180">-PassThru</span></span>

<span data-ttu-id="1b60d-181">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-181">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="1b60d-182">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-182">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="1b60d-183">-Path</span><span class="sxs-lookup"><span data-stu-id="1b60d-183">-Path</span></span>

<span data-ttu-id="1b60d-184">항목의 현재 위치 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-184">Specifies the path to the current location of the items.</span></span>
<span data-ttu-id="1b60d-185">기본값은 현재 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-185">The default is the current directory.</span></span>
<span data-ttu-id="1b60d-186">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-186">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="1b60d-187">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1b60d-187">-Confirm</span></span>

<span data-ttu-id="1b60d-188">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-188">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1b60d-189">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1b60d-189">-WhatIf</span></span>

<span data-ttu-id="1b60d-190">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-190">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="1b60d-191">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-191">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1b60d-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1b60d-192">CommonParameters</span></span>

<span data-ttu-id="1b60d-193">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-193">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="1b60d-194">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b60d-194">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="1b60d-195">입력</span><span class="sxs-lookup"><span data-stu-id="1b60d-195">INPUTS</span></span>

### <span data-ttu-id="1b60d-196">System.String</span><span class="sxs-lookup"><span data-stu-id="1b60d-196">System.String</span></span>

<span data-ttu-id="1b60d-197">이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-197">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="1b60d-198">출력</span><span class="sxs-lookup"><span data-stu-id="1b60d-198">OUTPUTS</span></span>

### <span data-ttu-id="1b60d-199">없음 또는 이동 된 항목을 나타내는 개체</span><span class="sxs-lookup"><span data-stu-id="1b60d-199">None or an object representing the moved item</span></span>

<span data-ttu-id="1b60d-200">*PassThru* 매개 변수를 사용 하는 경우이 cmdlet은 이동 된 항목을 나타내는 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-200">When you use the *PassThru* parameter, this cmdlet generates an object representing the moved item.</span></span>
<span data-ttu-id="1b60d-201">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-201">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1b60d-202">참고</span><span class="sxs-lookup"><span data-stu-id="1b60d-202">NOTES</span></span>

- <span data-ttu-id="1b60d-203">이 cmdlet은 동일한 공급자가 지 원하는 드라이브 간에 파일을 이동 하지만 디렉터리는 동일한 드라이브 내 에서만 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-203">This cmdlet will move files between drives that are supported by the same provider, but it will move directories only within the same drive.</span></span>
- <span data-ttu-id="1b60d-204">명령에서 `Move-Item` 항목의 속성, 내용 및 자식 항목을 이동 하기 때문에 기본적으로 모든 이동이 재귀적으로 진행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-204">Because a `Move-Item` command moves the properties, contents, and child items of an item, all moves are recursive by default.</span></span>
- <span data-ttu-id="1b60d-205">이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-205">This cmdlet is designed to work with the data exposed by any provider.</span></span>
  <span data-ttu-id="1b60d-206">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b60d-206">To list the providers available in your session, type `Get-PSProvider`.</span></span>
  <span data-ttu-id="1b60d-207">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b60d-207">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="1b60d-208">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1b60d-208">RELATED LINKS</span></span>

[<span data-ttu-id="1b60d-209">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="1b60d-209">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="1b60d-210">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="1b60d-210">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="1b60d-211">Get-Item</span><span class="sxs-lookup"><span data-stu-id="1b60d-211">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="1b60d-212">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="1b60d-212">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="1b60d-213">New-Item</span><span class="sxs-lookup"><span data-stu-id="1b60d-213">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="1b60d-214">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="1b60d-214">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="1b60d-215">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="1b60d-215">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="1b60d-216">Set-Item</span><span class="sxs-lookup"><span data-stu-id="1b60d-216">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="1b60d-217">about_Providers</span><span class="sxs-lookup"><span data-stu-id="1b60d-217">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

