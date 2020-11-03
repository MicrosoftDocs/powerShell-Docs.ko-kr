---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: 903c4eb784c1bb86b66766c7dfb563f586545dc1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215610"
---
# <span data-ttu-id="e8e67-103">Add-Content</span><span class="sxs-lookup"><span data-stu-id="e8e67-103">Add-Content</span></span>

## <span data-ttu-id="e8e67-104">개요</span><span class="sxs-lookup"><span data-stu-id="e8e67-104">SYNOPSIS</span></span>
<span data-ttu-id="e8e67-105">파일에 단어를 추가하는 것과 같이 지정된 항목에 내용을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-105">Adds content to the specified items, such as adding words to a file.</span></span>

## <span data-ttu-id="e8e67-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e8e67-106">SYNTAX</span></span>

### <span data-ttu-id="e8e67-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="e8e67-107">Path (Default)</span></span>

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

### <span data-ttu-id="e8e67-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e8e67-108">LiteralPath</span></span>

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

## <span data-ttu-id="e8e67-109">설명</span><span class="sxs-lookup"><span data-stu-id="e8e67-109">DESCRIPTION</span></span>

<span data-ttu-id="e8e67-110">`Add-Content`Cmdlet은 지정 된 항목 또는 파일에 콘텐츠를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-110">The `Add-Content` cmdlet appends content to a specified item or file.</span></span> <span data-ttu-id="e8e67-111">명령에 내용을 입력하거나 해당 내용이 포함된 개체를 지정하여 내용을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-111">You can specify the content by typing the content in the command or by specifying an object that contains the content.</span></span>

<span data-ttu-id="e8e67-112">다음 예제를 위해 파일이 나 디렉터리를 만들어야 하는 경우에는 [새 항목](New-Item.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8e67-112">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="e8e67-113">예제</span><span class="sxs-lookup"><span data-stu-id="e8e67-113">EXAMPLES</span></span>

### <span data-ttu-id="e8e67-114">예제 1: 예외를 사용 하 여 모든 텍스트 파일에 문자열 추가</span><span class="sxs-lookup"><span data-stu-id="e8e67-114">Example 1: Add a string to all text files with an exception</span></span>

<span data-ttu-id="e8e67-115">이 예제에서는 현재 디렉터리에 있는 텍스트 파일에 값을 추가 하지만 파일 이름에 따라 파일을 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-115">This example appends a value to text files in the current directory but excludes files based on their file name.</span></span>

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

<span data-ttu-id="e8e67-116">`Add-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 모든 .txt 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-116">The `Add-Content` cmdlet uses the **Path** parameter to specify all .txt files in the current directory.</span></span> <span data-ttu-id="e8e67-117">**Exclude** 매개 변수는 지정 된 패턴과 일치 하는 파일 이름을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-117">The **Exclude** parameter ignores file names that match the specified pattern.</span></span> <span data-ttu-id="e8e67-118">**값** 매개 변수는 파일에 기록 되는 텍스트 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-118">The **Value** parameter specifies the text string that is written to the files.</span></span>

<span data-ttu-id="e8e67-119">이 파일의 내용을 표시 하려면 [Get Content](Get-Content.md) 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-119">Use [Get-Content](Get-Content.md) to display the contents of these files.</span></span>

### <span data-ttu-id="e8e67-120">예제 2: 지정 된 파일의 끝에 날짜 추가</span><span class="sxs-lookup"><span data-stu-id="e8e67-120">Example 2: Add a date to the end of the specified files</span></span>

<span data-ttu-id="e8e67-121">이 예에서는 현재 디렉터리에 있는 파일에 날짜를 추가 하 고 PowerShell 콘솔에 해당 날짜를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-121">This example appends the date to files in the current directory and displays the date in the PowerShell console.</span></span>

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

<span data-ttu-id="e8e67-122">`Add-Content`Cmdlet은 **Path** 및 **Value** 매개 변수를 사용 하 여 현재 디렉터리에 두 개의 새 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-122">The `Add-Content` cmdlet uses the **Path** and **Value** parameters to create two new files in the current directory.</span></span> <span data-ttu-id="e8e67-123">**값** 매개 변수는 `Get-Date` 날짜를 가져와서 날짜를 전달 하는 cmdlet을 지정 합니다 `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="e8e67-123">The **Value** parameter specifies the `Get-Date` cmdlet to get the date and passes the date to `Add-Content`.</span></span> <span data-ttu-id="e8e67-124">`Add-Content`Cmdlet은 각 파일에 날짜를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-124">The `Add-Content` cmdlet writes the date to each file.</span></span> <span data-ttu-id="e8e67-125">**PassThru** 매개 변수는 날짜 개체를 나타내는 개체를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-125">The **PassThru** parameter passes an object that represents the date object.</span></span> <span data-ttu-id="e8e67-126">전달 된 개체를 받을 다른 cmdlet이 없으므로 PowerShell 콘솔에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-126">Because there is no other cmdlet to receive the passed object, it is displayed in the PowerShell console.</span></span> <span data-ttu-id="e8e67-127">`Get-Content`Cmdlet은 업데이트 된 파일인 DateTimeFile1을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-127">The `Get-Content` cmdlet displays the updated file, DateTimeFile1.log.</span></span>

### <span data-ttu-id="e8e67-128">예제 3: 지정 된 파일의 내용을 다른 파일에 추가</span><span class="sxs-lookup"><span data-stu-id="e8e67-128">Example 3: Add the contents of a specified file to another file</span></span>

<span data-ttu-id="e8e67-129">이 예제에서는 파일에서 콘텐츠를 가져오고 해당 내용을 다른 파일에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-129">This example gets the content from a file and appends that content into another file.</span></span>

```powershell
Add-Content -Path .\CopyToFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\CopyToFile.txt
```

<span data-ttu-id="e8e67-130">`Add-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 새 파일을 지정 CopyToFile.txt 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-130">The `Add-Content` cmdlet uses the **Path** parameter to specify the new file in the current directory, CopyToFile.txt.</span></span> <span data-ttu-id="e8e67-131">**값** 매개 변수는 cmdlet을 사용 하 여 `Get-Content` CopyFromFile.txt 파일의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-131">The **Value** parameter uses the `Get-Content` cmdlet to get the contents of the file, CopyFromFile.txt.</span></span> <span data-ttu-id="e8e67-132">Cmdlet 주위의 괄호는 명령이 `Get-Content` 시작 되기 전에 명령이 완료 되도록 합니다 `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="e8e67-132">The parentheses around the `Get-Content` cmdlet ensure that the command finishes before the `Add-Content` command begins.</span></span> <span data-ttu-id="e8e67-133">**값** 매개 변수는에 전달 됩니다 `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="e8e67-133">The **Value** parameter is passed to `Add-Content`.</span></span> <span data-ttu-id="e8e67-134">`Add-Content`Cmdlet은 CopyToFile.txt 파일에 데이터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-134">The `Add-Content` cmdlet appends the data to the CopyToFile.txt file.</span></span> <span data-ttu-id="e8e67-135">`Get-Content`Cmdlet은 CopyToFile.txt 업데이트 된 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-135">The `Get-Content` cmdlet displays the updated file, CopyToFile.txt.</span></span>

### <span data-ttu-id="e8e67-136">예제 4: 변수를 사용 하 여 지정 된 파일의 내용을 다른 파일에 추가</span><span class="sxs-lookup"><span data-stu-id="e8e67-136">Example 4: Use a variable to add the contents of a specified file to another file</span></span>

<span data-ttu-id="e8e67-137">이 예제에서는 파일에서 콘텐츠를 가져와서 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-137">This example gets the content from a file and stores the content in a variable.</span></span> <span data-ttu-id="e8e67-138">변수는 다른 파일에 콘텐츠를 추가 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-138">The variable is used to append the content into another file.</span></span>

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

<span data-ttu-id="e8e67-139">`Get-Content`Cmdlet은 CopyFromFile.txt의 내용을 가져오고 해당 내용을 변수에 저장 합니다 `$From` .</span><span class="sxs-lookup"><span data-stu-id="e8e67-139">The `Get-Content` cmdlet gets the contents of CopyFromFile.txt and stores the contents in the `$From` variable.</span></span> <span data-ttu-id="e8e67-140">`Add-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 CopyToFile.txt 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-140">The `Add-Content` cmdlet uses the **Path** parameter to specify the CopyToFile.txt file in the current directory.</span></span> <span data-ttu-id="e8e67-141">**값** 매개 변수는 변수를 사용 하 여 `$From` 에 콘텐츠를 전달 합니다 `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="e8e67-141">The **Value** parameter uses the `$From` variable and passes the content to `Add-Content`.</span></span> <span data-ttu-id="e8e67-142">`Add-Content`Cmdlet은 CopyToFile.txt 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-142">The `Add-Content` cmdlet updates the CopyToFile.txt file.</span></span> <span data-ttu-id="e8e67-143">이 `Get-Content` cmdlet은 CopyToFile.txt를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-143">The `Get-Content` cmdlet displays CopyToFile.txt.</span></span>

### <span data-ttu-id="e8e67-144">예 5: 새 파일 만들기 및 콘텐츠 복사</span><span class="sxs-lookup"><span data-stu-id="e8e67-144">Example 5: Create a new file and copy content</span></span>

<span data-ttu-id="e8e67-145">이 예에서는 새 파일을 만들고 기존 파일의 내용을 새 파일에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-145">This example creates a new file and copies an existing file's content into the new file.</span></span>

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

<span data-ttu-id="e8e67-146">`Add-Content`Cmdlet은 **Path** 및 **Value** 매개 변수를 사용 하 여 현재 디렉터리에 새 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-146">The `Add-Content` cmdlet uses the **Path** and **Value** parameters to create a new file in the current directory.</span></span> <span data-ttu-id="e8e67-147">**값** 매개 변수는 cmdlet을 사용 하 여 `Get-Content` 기존 파일 CopyFromFile.txt의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-147">The **Value** parameter uses the `Get-Content` cmdlet to get the contents of an existing file, CopyFromFile.txt.</span></span> <span data-ttu-id="e8e67-148">Cmdlet 주위의 괄호는 명령이 `Get-Content` 시작 되기 전에 명령이 완료 되도록 합니다 `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="e8e67-148">The parentheses around the `Get-Content` cmdlet ensure that the command finishes before the `Add-Content` command begins.</span></span> <span data-ttu-id="e8e67-149">**값** 매개 변수는 NewFile.txt 파일을 업데이트 하는에 대 한 콘텐츠를 전달 합니다 `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="e8e67-149">The **Value** parameter passes the content to `Add-Content` which updates the NewFile.txt file.</span></span> <span data-ttu-id="e8e67-150">`Get-Content`Cmdlet은 NewFile.txt 새 파일의 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-150">The `Get-Content` cmdlet displays the contents of the new file, NewFile.txt.</span></span>

### <span data-ttu-id="e8e67-151">예제 6: 읽기 전용 파일에 콘텐츠 추가</span><span class="sxs-lookup"><span data-stu-id="e8e67-151">Example 6: Add content to a read-only file</span></span>

<span data-ttu-id="e8e67-152">이 명령은 **IsReadOnly** File 특성이 True로 설정 된 경우에도 해당 값을 파일에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-152">This command adds the value to the file even if the **IsReadOnly** file attribute is set to True.</span></span>
<span data-ttu-id="e8e67-153">읽기 전용 파일을 만드는 단계는 예제에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-153">The steps to create a read-only file are included in the example.</span></span>

```powershell
New-Item -Path .\IsReadOnlyTextFile.txt -ItemType File
Set-ItemProperty -Path .\IsReadOnlyTextFile.txt -Name IsReadOnly -Value $True
Get-ChildItem -Path .\IsReadOnlyTextFile.txt
Add-Content -Path .\IsReadOnlyTextFile.txt -Value 'Add value to read-only text file' -Force
Get-Content -Path .\IsReadOnlyTextFile.txt
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-ar---        1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

<span data-ttu-id="e8e67-154">`New-Item`Cmdlet은 **Path** 및 **ItemType** 매개 변수를 사용 하 여 현재 디렉터리에 IsReadOnlyTextFile.txt 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-154">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the file IsReadOnlyTextFile.txt in the current directory.</span></span> <span data-ttu-id="e8e67-155">`Set-ItemProperty`Cmdlet은 **Name** 및 **Value** 매개 변수를 사용 하 여 파일의 **IsReadOnly** 속성을 True로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-155">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to True.</span></span> <span data-ttu-id="e8e67-156">`Get-ChildItem`이 cmdlet은 파일이 비어 있고 (0) 읽기 전용 특성 ()을 포함 하 고 있는 것을 보여 줍니다 `r` .</span><span class="sxs-lookup"><span data-stu-id="e8e67-156">The `Get-ChildItem` cmdlet shows the file is empty (0) and has the read-only attribute (`r`).</span></span> <span data-ttu-id="e8e67-157">`Add-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-157">The `Add-Content` cmdlet uses the **Path** parameter to specify the file.</span></span> <span data-ttu-id="e8e67-158">**값** 매개 변수는 파일에 추가할 텍스트 문자열을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-158">The **Value** parameter includes the text string to append to the file.</span></span> <span data-ttu-id="e8e67-159">**Force** 매개 변수는 읽기 전용 파일에 텍스트를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-159">The **Force** parameter writes the text to the read-only file.</span></span> <span data-ttu-id="e8e67-160">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 파일의 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-160">The `Get-Content` cmdlet uses the **Path** parameter to display the file's contents.</span></span>

<span data-ttu-id="e8e67-161">읽기 전용 특성을 제거 하려면 `Set-ItemProperty` **값** 매개 변수를로 설정 하 여 명령을 사용 `False` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-161">To remove the read-only attribute, use the `Set-ItemProperty` command with the **Value** parameter set to `False`.</span></span>

## <span data-ttu-id="e8e67-162">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e8e67-162">PARAMETERS</span></span>

### <span data-ttu-id="e8e67-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e8e67-163">-Confirm</span></span>

<span data-ttu-id="e8e67-164">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e8e67-165">-Credential</span><span class="sxs-lookup"><span data-stu-id="e8e67-165">-Credential</span></span>

<span data-ttu-id="e8e67-166">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-166">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="e8e67-167">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-167">The default is the current user.</span></span>

<span data-ttu-id="e8e67-168">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="e8e67-168">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="e8e67-169">사용자 이름을 입력하면 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-169">If you type a user name, you will be prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="e8e67-170">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-170">This parameter is not supported by any providers installed with PowerShell.</span></span>

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

### <span data-ttu-id="e8e67-171">-Encoding</span><span class="sxs-lookup"><span data-stu-id="e8e67-171">-Encoding</span></span>

<span data-ttu-id="e8e67-172">대상 파일의 인코딩 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-172">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="e8e67-173">기본값은 `Default`입니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-173">The default value is `Default`.</span></span>

<span data-ttu-id="e8e67-174">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-174">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="e8e67-175">`Ascii` ASCII (7 비트) 문자 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-175">`Ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="e8e67-176">`BigEndianUnicode` 에서는 u t f-16을 빅 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-176">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="e8e67-177">`BigEndianUTF32` 는 빅 endian 바이트 순서를 사용 하 여 u t f-32을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-177">`BigEndianUTF32` Uses UTF-32 with the big-endian byte order.</span></span>
- <span data-ttu-id="e8e67-178">`Byte` 문자 집합을 바이트 시퀀스로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-178">`Byte` Encodes a set of characters into a sequence of bytes.</span></span>
- <span data-ttu-id="e8e67-179">`Default` 시스템의 활성 코드 페이지에 해당 하는 인코딩을 사용 합니다 (일반적으로 ANSI).</span><span class="sxs-lookup"><span data-stu-id="e8e67-179">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="e8e67-180">`Oem` 시스템의 현재 OEM 코드 페이지에 해당 하는 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-180">`Oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="e8e67-181">`String`**유니코드** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-181">`String` Same as **Unicode** .</span></span>
- <span data-ttu-id="e8e67-182">`Unicode` 는 u t f-16을 약간 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-182">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="e8e67-183">`Unknown`**유니코드** 와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-183">`Unknown` Same as **Unicode** .</span></span>
- <span data-ttu-id="e8e67-184">`UTF7` 는 u t f-7을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-184">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="e8e67-185">`UTF8` 는 u t f-8을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-185">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="e8e67-186">`UTF32` 는 u t f-32을 작은 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-186">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

<span data-ttu-id="e8e67-187">Encoding은 파일 시스템 공급자가 cmdlet에 추가 하는 동적 매개 변수입니다 `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="e8e67-187">Encoding is a dynamic parameter that the FileSystem provider adds to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="e8e67-188">이 매개 변수는 파일 시스템 드라이브에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-188">This parameter works only in file system drives.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, Byte, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8e67-189">-제외</span><span class="sxs-lookup"><span data-stu-id="e8e67-189">-Exclude</span></span>

<span data-ttu-id="e8e67-190">지정된 항목을 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-190">Omits the specified items.</span></span> <span data-ttu-id="e8e67-191">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-191">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e8e67-192">경로 요소 또는 패턴 (예: .txt)을 입력 합니다 **\* .**</span><span class="sxs-lookup"><span data-stu-id="e8e67-192">Enter a path element or pattern, such as **\*.txt** .</span></span> <span data-ttu-id="e8e67-193">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-193">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="e8e67-194">-Filter</span><span class="sxs-lookup"><span data-stu-id="e8e67-194">-Filter</span></span>

<span data-ttu-id="e8e67-195">공급자의 형식 또는 언어에 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-195">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="e8e67-196">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-196">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e8e67-197">와일드카드 사용을 포함한 필터 구문은 공급자에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-197">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="e8e67-198">개체를 검색할 때 공급자가 필터를 적용 하기 때문에 **필터** 는 다른 매개 변수 보다 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-198">**Filters** are more efficient than other parameters because the provider applies filters when objects are retrieved.</span></span> <span data-ttu-id="e8e67-199">그렇지 않으면 PowerShell은 개체가 검색 된 후 필터를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-199">Otherwise, PowerShell processes filters after the objects are retrieved.</span></span>

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

### <span data-ttu-id="e8e67-200">-Force</span><span class="sxs-lookup"><span data-stu-id="e8e67-200">-Force</span></span>

<span data-ttu-id="e8e67-201">읽기 전용 특성을 재정의하여 읽기 전용 파일에 내용을 추가할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-201">Overrides the read-only attribute, allowing you to add content to a read-only file.</span></span> <span data-ttu-id="e8e67-202">예를 들어 **Force** 는 읽기 전용 특성을 재정의하거나, 디렉터리를 만들어 파일 경로를 완성할 수 있지만 파일 사용 권한을 변경하지는 못합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-202">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="e8e67-203">-포함</span><span class="sxs-lookup"><span data-stu-id="e8e67-203">-Include</span></span>

<span data-ttu-id="e8e67-204">지정된 항목만 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-204">Adds only the specified items.</span></span> <span data-ttu-id="e8e67-205">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-205">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e8e67-206">경로 요소 또는 패턴 (예: .txt)을 입력 합니다 **\* .**</span><span class="sxs-lookup"><span data-stu-id="e8e67-206">Enter a path element or pattern, such as **\*.txt** .</span></span> <span data-ttu-id="e8e67-207">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-207">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="e8e67-208">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e8e67-208">-LiteralPath</span></span>

<span data-ttu-id="e8e67-209">추가 내용을 받는 항목의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-209">Specifies the path to the items that receive the additional content.</span></span> <span data-ttu-id="e8e67-210">**Path** 와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-210">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="e8e67-211">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-211">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="e8e67-212">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="e8e67-212">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="e8e67-213">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-213">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="e8e67-214">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="e8e67-214">-NoNewline</span></span>

<span data-ttu-id="e8e67-215">이 cmdlet이 콘텐츠에 새 줄 또는 캐리지 리턴을 추가 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-215">Indicates that this cmdlet does not add a new line or carriage return to the content.</span></span>

<span data-ttu-id="e8e67-216">입력 개체의 문자열 표현은 연결 되어 출력을 형성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-216">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="e8e67-217">출력 문자열 사이에 공백이 나 줄바꿈 삽입 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-217">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="e8e67-218">마지막 출력 문자열 뒤에는 줄 바꿈이 추가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-218">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="e8e67-219">-PassThru</span><span class="sxs-lookup"><span data-stu-id="e8e67-219">-PassThru</span></span>

<span data-ttu-id="e8e67-220">추가된 내용을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-220">Returns an object representing the added content.</span></span> <span data-ttu-id="e8e67-221">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-221">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="e8e67-222">-Path</span><span class="sxs-lookup"><span data-stu-id="e8e67-222">-Path</span></span>

<span data-ttu-id="e8e67-223">추가 내용을 받는 항목의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-223">Specifies the path to the items that receive the additional content.</span></span> <span data-ttu-id="e8e67-224">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-224">Wildcards are permitted.</span></span> <span data-ttu-id="e8e67-225">여러 경로를 지정하는 경우 쉼표를 사용하여 경로를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-225">If you specify multiple paths, use commas to separate the paths.</span></span>

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

### <span data-ttu-id="e8e67-226">-스트림</span><span class="sxs-lookup"><span data-stu-id="e8e67-226">-Stream</span></span>

<span data-ttu-id="e8e67-227">콘텐츠에 대 한 대체 데이터 스트림을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-227">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="e8e67-228">스트림이 없는 경우이 cmdlet은이를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-228">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="e8e67-229">와일드카드 문자는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-229">Wildcard characters are not supported.</span></span>

<span data-ttu-id="e8e67-230">**스트림은** 파일 시스템 공급자가에 추가 하는 동적 매개 변수입니다 `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="e8e67-230">**Stream** is a dynamic parameter that the FileSystem provider adds to `Add-Content`.</span></span> <span data-ttu-id="e8e67-231">이 매개 변수는 파일 시스템 드라이브에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-231">This parameter works only in file system drives.</span></span>

<span data-ttu-id="e8e67-232">Cmdlet을 사용 하 여 `Add-Content` 영역의 콘텐츠를 변경할 수 있습니다 **. 식별자** 대체 데이터 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-232">You can use the `Add-Content` cmdlet to change the content of the **Zone.Identifier** alternate data stream.</span></span> <span data-ttu-id="e8e67-233">그러나이 방법은 인터넷에서 다운로드 된 파일을 차단 하는 보안 검사를 제거 하는 방법으로 권장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-233">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="e8e67-234">다운로드 한 파일이 안전한 지 확인 하려면 cmdlet을 사용 `Unblock-File` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-234">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="e8e67-235">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-235">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="e8e67-236">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="e8e67-236">-UseTransaction</span></span>

<span data-ttu-id="e8e67-237">활성 트랜잭션에 명령을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-237">Includes the command in the active transaction.</span></span> <span data-ttu-id="e8e67-238">이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-238">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="e8e67-239">자세한 내용은 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8e67-239">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="e8e67-240">-Value</span><span class="sxs-lookup"><span data-stu-id="e8e67-240">-Value</span></span>

<span data-ttu-id="e8e67-241">추가할 내용을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-241">Specifies the content to be added.</span></span> <span data-ttu-id="e8e67-242">**이 데이터는 내부용 으로만 사용 되** 는 따옴표로 묶인 문자열을 입력 하거나를 생성 하는 **DateTime** 개체와 같이 콘텐츠가 포함 된 개체를 지정 `Get-Date` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-242">Type a quoted string, such as **This data is for internal use only** , or specify an object that contains content, such as the **DateTime** object that `Get-Date` generates.</span></span>

<span data-ttu-id="e8e67-243">경로는 단지 문자열 이므로 경로를 입력 하 여 파일의 내용을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-243">You cannot specify the contents of a file by typing its path, because the path is just a string.</span></span>
<span data-ttu-id="e8e67-244">명령을 사용 하 여 `Get-Content` 콘텐츠를 가져와서 **Value** 매개 변수에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-244">You can use a `Get-Content` command to get the content and pass it to the **Value** parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e8e67-245">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e8e67-245">-WhatIf</span></span>

<span data-ttu-id="e8e67-246">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-246">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="e8e67-247">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-247">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e8e67-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e8e67-248">CommonParameters</span></span>

<span data-ttu-id="e8e67-249">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-249">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="e8e67-250">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8e67-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e8e67-251">입력</span><span class="sxs-lookup"><span data-stu-id="e8e67-251">INPUTS</span></span>

### <span data-ttu-id="e8e67-252">System.object, System.web. PSCredential</span><span class="sxs-lookup"><span data-stu-id="e8e67-252">System.Object, System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="e8e67-253">값, 경로 또는 자격 증명을로 파이프 할 수 있습니다 `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="e8e67-253">You can pipe values, paths, or credentials to `Set-Content`.</span></span>

## <span data-ttu-id="e8e67-254">출력</span><span class="sxs-lookup"><span data-stu-id="e8e67-254">OUTPUTS</span></span>

### <span data-ttu-id="e8e67-255">없음 또는 System.String</span><span class="sxs-lookup"><span data-stu-id="e8e67-255">None or System.String</span></span>

<span data-ttu-id="e8e67-256">**PassThru** 매개 변수를 사용 하는 경우는 `Add-Content` 콘텐츠를 나타내는 **system.string** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-256">When you use the **PassThru** parameter, `Add-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="e8e67-257">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-257">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e8e67-258">참고</span><span class="sxs-lookup"><span data-stu-id="e8e67-258">NOTES</span></span>

<span data-ttu-id="e8e67-259">개체를로 파이프 하면 `Add-Content` 개체가 항목에 추가 되기 전에 문자열로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-259">When you pipe an object to `Add-Content`, the object is converted to a string before it is added to the item.</span></span> <span data-ttu-id="e8e67-260">개체 유형에 따라 문자열 형식이 결정되지만 형식이 개체의 기본 표시 형식과 다를 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-260">The object type determines the string format, but the format might be different than the default display of the object.</span></span> <span data-ttu-id="e8e67-261">문자열 형식을 제어하려면 보내는 cmdlet의 형식 지정 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-261">To control the string format, use the formatting parameters of the sending cmdlet.</span></span>

<span data-ttu-id="e8e67-262">의 기본 제공 별칭인를 참조할 수도 있습니다 `Add-Content` `ac` .</span><span class="sxs-lookup"><span data-stu-id="e8e67-262">You can also refer to `Add-Content` by its built-in alias, `ac`.</span></span> <span data-ttu-id="e8e67-263">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8e67-263">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="e8e67-264">`Add-Content`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-264">The `Add-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="e8e67-265">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8e67-265">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="e8e67-266">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8e67-266">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="e8e67-267">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e8e67-267">RELATED LINKS</span></span>

[<span data-ttu-id="e8e67-268">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="e8e67-268">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="e8e67-269">about_Providers</span><span class="sxs-lookup"><span data-stu-id="e8e67-269">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="e8e67-270">about_Transactions</span><span class="sxs-lookup"><span data-stu-id="e8e67-270">about_Transactions</span></span>](../Microsoft.PowerShell.Core/About/about_Transactions.md)

[<span data-ttu-id="e8e67-271">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="e8e67-271">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="e8e67-272">Get-Content</span><span class="sxs-lookup"><span data-stu-id="e8e67-272">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="e8e67-273">Get-Item</span><span class="sxs-lookup"><span data-stu-id="e8e67-273">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="e8e67-274">New-Item</span><span class="sxs-lookup"><span data-stu-id="e8e67-274">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="e8e67-275">Set-Content</span><span class="sxs-lookup"><span data-stu-id="e8e67-275">Set-Content</span></span>](Set-Content.md)
