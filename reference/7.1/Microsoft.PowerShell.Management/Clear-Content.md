---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-content?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Content
ms.openlocfilehash: 89ac365524658612dd878cf8c2c462a40a278487
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692747"
---
# <span data-ttu-id="90a38-102">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="90a38-102">Clear-Content</span></span>

## <span data-ttu-id="90a38-103">개요</span><span class="sxs-lookup"><span data-stu-id="90a38-103">SYNOPSIS</span></span>
<span data-ttu-id="90a38-104">항목의 내용을 삭제하지만 항목 자체는 삭제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-104">Deletes the contents of an item, but does not delete the item.</span></span>

## <span data-ttu-id="90a38-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="90a38-105">SYNTAX</span></span>

### <span data-ttu-id="90a38-106">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="90a38-106">Path (Default)</span></span>

```
Clear-Content [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

### <span data-ttu-id="90a38-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="90a38-107">LiteralPath</span></span>

```
Clear-Content -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

## <span data-ttu-id="90a38-108">설명</span><span class="sxs-lookup"><span data-stu-id="90a38-108">DESCRIPTION</span></span>

<span data-ttu-id="90a38-109">`Clear-Content`Cmdlet은 파일에서 텍스트를 삭제 하는 것과 같이 항목의 내용을 삭제 하지만 항목은 삭제 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-109">The `Clear-Content` cmdlet deletes the contents of an item, such as deleting the text from a file, but it does not delete the item.</span></span>
<span data-ttu-id="90a38-110">따라서 항목이 있지만 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-110">As a result, the item exists, but it is empty.</span></span>
<span data-ttu-id="90a38-111">는와 `Clear-Content` 유사 `Clear-Item` 하지만 값이 있는 항목 대신 내용이 있는 항목에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-111">The `Clear-Content` is similar to `Clear-Item`, but it works on items with contents, instead of items with values.</span></span>

## <span data-ttu-id="90a38-112">예제</span><span class="sxs-lookup"><span data-stu-id="90a38-112">EXAMPLES</span></span>

### <span data-ttu-id="90a38-113">예제 1: 디렉터리에서 모든 콘텐츠 삭제</span><span class="sxs-lookup"><span data-stu-id="90a38-113">Example 1: Delete all content from a directory</span></span>

```powershell
Clear-Content "..\SmpUsers\*\init.txt"
```

<span data-ttu-id="90a38-114">이 명령은 SmpUsers 디렉터리의 모든 하위 디렉터리에 있는 "init.txt" 파일에서 모든 내용을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-114">This command deletes all of the content from the "init.txt" files in all subdirectories of the SmpUsers directory.</span></span>
<span data-ttu-id="90a38-115">파일은 삭제되지 않고 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-115">The files are not deleted, but they are empty.</span></span>

### <span data-ttu-id="90a38-116">예제 2: 와일드 카드를 사용 하 여 모든 파일의 내용 삭제</span><span class="sxs-lookup"><span data-stu-id="90a38-116">Example 2: Delete content of all files with a wildcard</span></span>

```powershell
Clear-Content -Path "*" -Filter "*.log" -Force
```

<span data-ttu-id="90a38-117">이 명령은 읽기 전용 특성을 가진 파일을 포함하여 현재 디렉터리에서 파일 이름 확장명이 ".log"인 모든 파일의 내용을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-117">This command deletes the contents of all files in the current directory with the ".log" file name extension, including files with the read-only attribute.</span></span> <span data-ttu-id="90a38-118">경로의 별표 ( \* )는 현재 디렉터리에 있는 모든 항목을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-118">The asterisk (\*) in the path represents all items in the current directory.</span></span> <span data-ttu-id="90a38-119">**Force** 매개 변수는 명령이 읽기 전용 파일에 적용 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-119">The **Force** parameter makes the command effective on read-only files.</span></span> <span data-ttu-id="90a38-120">필터를 사용 하 여 .log 파일 이름 확장명을 가진 파일에 대 한 명령을 제한 합니다. 경로에 .log를 지정 하는 대신 \* 작업을 더 빠르게 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-120">Using a filter to restrict the command to files with the .log file name extension instead of specifying \*.log in the path makes the operation faster.</span></span>

### <span data-ttu-id="90a38-121">예제 3: 스트림에서 모든 데이터 지우기</span><span class="sxs-lookup"><span data-stu-id="90a38-121">Example 3: Clear all data from a stream</span></span>

<span data-ttu-id="90a38-122">이 예에서는 cmdlet이 `Clear-Content` 스트림을 그대로 두고 대체 데이터 스트림에서 콘텐츠를 지우는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-122">This example shows how the `Clear-Content` cmdlet clears the content from an alternate data stream while leaving the stream intact.</span></span>

<span data-ttu-id="90a38-123">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Content` `Zone.Identifier` 인터넷에서 다운로드 된 Copy-Script.ps1 파일의 스트림 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-123">The first command uses the `Get-Content` cmdlet to get the content of the `Zone.Identifier` stream in the Copy-Script.ps1 file, which was downloaded from the Internet.</span></span>

<span data-ttu-id="90a38-124">두 번째 명령은 cmdlet을 사용 하 여 `Clear-Content` 콘텐츠를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-124">The second command uses the `Clear-Content` cmdlet to clear the content.</span></span>

<span data-ttu-id="90a38-125">세 번째 명령은 첫 번째 명령을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-125">The third command repeats the first command.</span></span> <span data-ttu-id="90a38-126">콘텐츠가 제거 되었는지 확인 하지만 스트림은 그대로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-126">It verifies that the content is cleared, but the stream remains.</span></span> <span data-ttu-id="90a38-127">스트림이 삭제 된 경우이 명령은 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-127">If the stream were deleted, the command would generate an error.</span></span>

<span data-ttu-id="90a38-128">이와 같은 메서드를 사용 하 여 대체 데이터 스트림의 내용을 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-128">You can use a method like this one to clear the content of an alternate data stream.</span></span> <span data-ttu-id="90a38-129">하지만 인터넷에서 다운로드한 파일을 차단하는 보안 검사를 제거하는 것은 권장되는 방법이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-129">However, it is not the recommended way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="90a38-130">다운로드 한 파일이 안전한 지 확인 하려면 cmdlet을 사용 `Unblock-File` 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-130">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

```
PS C:\> Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

[ZoneTransfer]
ZoneId=3

PS C:\>Clear-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

PS C:\>Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
PS C:\>
```

## <span data-ttu-id="90a38-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="90a38-131">PARAMETERS</span></span>

### <span data-ttu-id="90a38-132">-스트림</span><span class="sxs-lookup"><span data-stu-id="90a38-132">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="90a38-133">이 매개 변수는 Windows 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-133">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="90a38-134">콘텐츠에 대 한 대체 데이터 스트림을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-134">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="90a38-135">스트림이 없는 경우이 cmdlet은이를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-135">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="90a38-136">와일드카드 문자는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-136">Wildcard characters are not supported.</span></span>

<span data-ttu-id="90a38-137">**스트림은** 파일 시스템 공급자가에 추가 하는 동적 매개 변수입니다 `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="90a38-137">**Stream** is a dynamic parameter that the FileSystem provider adds to `Clear-Content`.</span></span> <span data-ttu-id="90a38-138">이 매개 변수는 파일 시스템 드라이브 에서만 작동 하며 파일 및 디렉터리에서 대체 데이터 스트림의 내용을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-138">This parameter works only in file system drives, and will clear the content of alternative data streams on both files and directories.</span></span>

<span data-ttu-id="90a38-139">Cmdlet을 사용 하 여 `Clear-Content` 와 같이 최소라 대체 데이터 스트림의 콘텐츠를 변경할 수 있습니다 `Zone.Identifier` .</span><span class="sxs-lookup"><span data-stu-id="90a38-139">You can use the `Clear-Content` cmdlet to change the content of amy alternate data stream, such as `Zone.Identifier`.</span></span> <span data-ttu-id="90a38-140">그러나이 방법은 인터넷에서 다운로드 된 파일을 차단 하는 보안 검사를 제거 하는 방법으로 권장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-140">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="90a38-141">다운로드 한 파일이 안전한 지 확인 하려면 cmdlet을 사용 `Unblock-File` 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-141">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="90a38-142">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-142">This parameter was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="90a38-143">PowerShell 7.2 `Clear-Content` 부터는 디렉터리 및 파일에서 대체 데이터 스트림의 내용을 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-143">As of PowerShell 7.2, `Clear-Content` can clear the content of alternative data streams from directories as well as files.</span></span>

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

### <span data-ttu-id="90a38-144">-Credential</span><span class="sxs-lookup"><span data-stu-id="90a38-144">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="90a38-145">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-145">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="90a38-146">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 Invoke 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-146">To impersonate another user, or elevate your credentials when running this cmdlet, use Invoke-Command.</span></span>

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

### <span data-ttu-id="90a38-147">-제외</span><span class="sxs-lookup"><span data-stu-id="90a38-147">-Exclude</span></span>

<span data-ttu-id="90a38-148">이 cmdlet이 콘텐츠 경로에서 생략 하는 문자열을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-148">Specifies, as a string array, strings that this cmdlet omits from the path to the content.</span></span> <span data-ttu-id="90a38-149">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-149">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="90a38-150">경로 요소 또는 패턴(예: "\*.txt")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-150">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="90a38-151">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-151">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="90a38-152">-Filter</span><span class="sxs-lookup"><span data-stu-id="90a38-152">-Filter</span></span>

<span data-ttu-id="90a38-153">공급자의 형식 또는 언어에 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-153">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="90a38-154">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-154">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="90a38-155">와일드카드 사용을 포함한 필터 구문은 공급자에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-155">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="90a38-156">필터는 개체가 검색 된 후 개체를 검색 한 후 개체를 검색 하는 대신 개체를 검색할 때 필터를 적용 하기 때문에 다른 매개 변수 보다 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-156">Filters are more efficient than other parameters, because the provider applies them when retrieving the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="90a38-157">-Force</span><span class="sxs-lookup"><span data-stu-id="90a38-157">-Force</span></span>

<span data-ttu-id="90a38-158">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-158">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="90a38-159">-포함</span><span class="sxs-lookup"><span data-stu-id="90a38-159">-Include</span></span>

<span data-ttu-id="90a38-160">이 cmdlet이 지우는 콘텐츠를 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-160">Specifies, as a string array, content that this cmdlet clears.</span></span> <span data-ttu-id="90a38-161">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-161">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="90a38-162">경로 요소 또는 패턴(예: "\*.txt")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-162">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="90a38-163">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-163">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="90a38-164">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="90a38-164">-LiteralPath</span></span>

<span data-ttu-id="90a38-165">내용을 삭제할 항목의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-165">Specifies the paths to the items from which content is deleted.</span></span> <span data-ttu-id="90a38-166">**Path** 매개 변수와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-166">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="90a38-167">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-167">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="90a38-168">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="90a38-168">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="90a38-169">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-169">Single quotation marks tell having PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="90a38-170">-Path</span><span class="sxs-lookup"><span data-stu-id="90a38-170">-Path</span></span>

<span data-ttu-id="90a38-171">내용을 삭제할 항목의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-171">Specifies the paths to the items from which content is deleted.</span></span> <span data-ttu-id="90a38-172">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-172">Wildcards are permitted.</span></span> <span data-ttu-id="90a38-173">경로는 컨테이너가 아니라 항목의 경로여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-173">The paths must be paths to items, not to containers.</span></span> <span data-ttu-id="90a38-174">예를 들어 디렉터리의 경로가 아니라 하나 이상의 파일 경로를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-174">For example, you must specify a path to one or more files, not a path to a directory.</span></span> <span data-ttu-id="90a38-175">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-175">Wildcards are permitted.</span></span> <span data-ttu-id="90a38-176">이 매개 변수는 필수이지만 매개 변수 이름("Path")은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-176">This parameter is required, but the parameter name ("Path") is optional.</span></span>

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

### <span data-ttu-id="90a38-177">-Confirm</span><span class="sxs-lookup"><span data-stu-id="90a38-177">-Confirm</span></span>

<span data-ttu-id="90a38-178">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-178">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="90a38-179">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="90a38-179">-WhatIf</span></span>

<span data-ttu-id="90a38-180">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-180">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="90a38-181">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-181">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="90a38-182">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="90a38-182">CommonParameters</span></span>

<span data-ttu-id="90a38-183">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="90a38-183">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="90a38-184">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90a38-184">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="90a38-185">입력</span><span class="sxs-lookup"><span data-stu-id="90a38-185">INPUTS</span></span>

### <span data-ttu-id="90a38-186">None</span><span class="sxs-lookup"><span data-stu-id="90a38-186">None</span></span>

<span data-ttu-id="90a38-187">개체를에 연결할 수 없습니다 `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="90a38-187">You cannot pipe objects to `Clear-Content`.</span></span>

## <span data-ttu-id="90a38-188">출력</span><span class="sxs-lookup"><span data-stu-id="90a38-188">OUTPUTS</span></span>

### <span data-ttu-id="90a38-189">None</span><span class="sxs-lookup"><span data-stu-id="90a38-189">None</span></span>

<span data-ttu-id="90a38-190">이 cmdlet은 개체를 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-190">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="90a38-191">참고</span><span class="sxs-lookup"><span data-stu-id="90a38-191">NOTES</span></span>

<span data-ttu-id="90a38-192">`Clear-Content`PowerShell FileSystem 공급자 및 콘텐츠를 조작 하는 다른 공급자와 함께를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-192">You can use `Clear-Content` with the PowerShell FileSystem provider and with other providers that manipulate content.</span></span> <span data-ttu-id="90a38-193">PowerShell 인증서 또는 레지스트리 공급자에서 관리 하는 항목과 같이 콘텐츠로 간주 되지 않는 항목을 지우려면를 사용 `Clear-Item` 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-193">To clear items that are not considered to be content, such as items managed by the PowerShell Certificate or Registry providers, use `Clear-Item`.</span></span>

<span data-ttu-id="90a38-194">`Clear-Content`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-194">The `Clear-Content` cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="90a38-195">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PsProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="90a38-195">To list the providers available in your session, type `Get-PsProvider`.</span></span>
<span data-ttu-id="90a38-196">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90a38-196">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="90a38-197">관련 링크</span><span class="sxs-lookup"><span data-stu-id="90a38-197">RELATED LINKS</span></span>

[<span data-ttu-id="90a38-198">Add-Content</span><span class="sxs-lookup"><span data-stu-id="90a38-198">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="90a38-199">Get-Content</span><span class="sxs-lookup"><span data-stu-id="90a38-199">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="90a38-200">Get-Item</span><span class="sxs-lookup"><span data-stu-id="90a38-200">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="90a38-201">Set-Content</span><span class="sxs-lookup"><span data-stu-id="90a38-201">Set-Content</span></span>](Set-Content.md)

[<span data-ttu-id="90a38-202">about_Providers</span><span class="sxs-lookup"><span data-stu-id="90a38-202">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

