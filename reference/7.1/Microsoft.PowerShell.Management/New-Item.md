---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Item
ms.openlocfilehash: 50a7dba8c4e9cb1cfabd42f39e9fdfb43f22f9b1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211602"
---
# <span data-ttu-id="30775-103">New-Item</span><span class="sxs-lookup"><span data-stu-id="30775-103">New-Item</span></span>

## <span data-ttu-id="30775-104">개요</span><span class="sxs-lookup"><span data-stu-id="30775-104">SYNOPSIS</span></span>
<span data-ttu-id="30775-105">새 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30775-105">Creates a new item.</span></span>

## <span data-ttu-id="30775-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="30775-106">SYNTAX</span></span>

### <span data-ttu-id="30775-107">pathSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="30775-107">pathSet (Default)</span></span>

```
New-Item [-Path] <String[]> [-ItemType <String>] [-Value <Object>] [-Force] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="30775-108">nameSet</span><span class="sxs-lookup"><span data-stu-id="30775-108">nameSet</span></span>

```
New-Item [[-Path] <String[]>] -Name <String> [-ItemType <String>] [-Value <Object>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="30775-109">설명</span><span class="sxs-lookup"><span data-stu-id="30775-109">DESCRIPTION</span></span>

<span data-ttu-id="30775-110">`New-Item`Cmdlet은 새 항목을 만들고 해당 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-110">The `New-Item` cmdlet creates a new item and sets its value.</span></span> <span data-ttu-id="30775-111">만들 수 있는 항목의 형식은 항목의 위치에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="30775-111">The types of items that can be created depend on the location of the item.</span></span> <span data-ttu-id="30775-112">예를 들어 파일 시스템에서는 `New-Item` 파일 및 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30775-112">For example, in the file system, `New-Item` creates files and folders.</span></span> <span data-ttu-id="30775-113">레지스트리에서 `New-Item` 레지스트리 키와 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30775-113">In the registry, `New-Item` creates registry keys and entries.</span></span>

<span data-ttu-id="30775-114">`New-Item` 또한에서 만드는 항목의 값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-114">`New-Item` can also set the value of the items that it creates.</span></span> <span data-ttu-id="30775-115">예를 들어 새 파일을 만들 때는 `New-Item` 파일에 초기 콘텐츠를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-115">For example, when it creates a new file, `New-Item` can add initial content to the file.</span></span>

## <span data-ttu-id="30775-116">예제</span><span class="sxs-lookup"><span data-stu-id="30775-116">EXAMPLES</span></span>

### <span data-ttu-id="30775-117">예제 1: 현재 디렉터리에 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="30775-117">Example 1: Create a file in the current directory</span></span>

<span data-ttu-id="30775-118">이 명령은 현재 디렉터리에 "testfile1.txt" 라는 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30775-118">This command creates a text file that is named "testfile1.txt" in the current directory.</span></span> <span data-ttu-id="30775-119">**Path** 매개 변수 값의 점 ('. ')은 현재 디렉터리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="30775-119">The dot ('.') in the value of the **Path** parameter indicates the current directory.</span></span> <span data-ttu-id="30775-120">**Value** 매개 변수 뒤에 오는 따옴표로 묶인 텍스트는 파일에 내용으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30775-120">The quoted text that follows the **Value** parameter is added to the file as content.</span></span>

```powershell
New-Item -Path . -Name "testfile1.txt" -ItemType "file" -Value "This is a text string."
```

### <span data-ttu-id="30775-121">예제 2: 디렉터리 만들기</span><span class="sxs-lookup"><span data-stu-id="30775-121">Example 2: Create a directory</span></span>

<span data-ttu-id="30775-122">이 명령은 드라이브에 "Logfiles" 라는 디렉터리를 만듭니다 `C:` .</span><span class="sxs-lookup"><span data-stu-id="30775-122">This command creates a directory named "Logfiles" in the `C:` drive.</span></span> <span data-ttu-id="30775-123">**ItemType** 매개 변수는 새 항목이 파일 또는 기타 파일 시스템 개체가 아닌 디렉터리 임을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-123">The **ItemType** parameter specifies that the new item is a directory, not a file or other file system object.</span></span>

```powershell
New-Item -Path "c:\" -Name "logfiles" -ItemType "directory"
```

### <span data-ttu-id="30775-124">예제 3: 프로필 만들기</span><span class="sxs-lookup"><span data-stu-id="30775-124">Example 3: Create a profile</span></span>

<span data-ttu-id="30775-125">이 명령은 변수에 의해 지정 된 경로에 PowerShell 프로필을 만듭니다 `$profile` .</span><span class="sxs-lookup"><span data-stu-id="30775-125">This command creates a PowerShell profile in the path that is specified by the `$profile` variable.</span></span>

<span data-ttu-id="30775-126">프로필을 사용 하 여 PowerShell을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-126">You can use profiles to customize PowerShell.</span></span> <span data-ttu-id="30775-127">`$profile` 는 "CurrentUser/CurrentHost" 프로필의 경로와 파일 이름을 저장 하는 자동 (기본 제공) 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="30775-127">`$profile` is an automatic (built-in) variable that stores the path and file name of the "CurrentUser/CurrentHost" profile.</span></span> <span data-ttu-id="30775-128">PowerShell에서 경로와 파일 이름을 저장 하는 경우에도 기본적으로 프로필은 존재 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-128">By default, the profile does not exist, even though PowerShell stores a path and file name for it.</span></span>

<span data-ttu-id="30775-129">이 명령에서 변수는 `$profile` 파일의 경로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="30775-129">In this command, the `$profile` variable represents the path of the file.</span></span> <span data-ttu-id="30775-130">**ItemType** 매개 변수는 명령이 파일을 생성 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-130">**ItemType** parameter specifies that the command creates a file.</span></span> <span data-ttu-id="30775-131">**Force** 매개 변수를 사용 하면 경로의 디렉터리가 없는 경우에도 프로필 경로에 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-131">The **Force** parameter lets you create a file in the profile path, even when the directories in the path do not exist.</span></span>

<span data-ttu-id="30775-132">프로필을 만든 후 프로필에 별칭, 함수 및 스크립트를 입력 하 여 셸을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-132">After you create a profile, you can enter aliases, functions, and scripts in the profile to customize your shell.</span></span>

<span data-ttu-id="30775-133">자세한 내용은 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) 및 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="30775-133">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) and [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

```powershell
New-Item -Path $profile -ItemType "file" -Force
```

### <span data-ttu-id="30775-134">예제 4: 다른 디렉터리에 디렉터리 만들기</span><span class="sxs-lookup"><span data-stu-id="30775-134">Example 4: Create a directory in a different directory</span></span>

<span data-ttu-id="30775-135">이 예제에서는 "C:\PS-Test" 디렉터리에 새 Scripts 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30775-135">This example creates a new Scripts directory in the "C:\PS-Test" directory.</span></span>

<span data-ttu-id="30775-136">새 디렉터리 항목인 "Scripts"의 이름은 **name** 값에 지정 되지 않고 **Path** 매개 변수 값에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30775-136">The name of the new directory item, "Scripts", is included in the value of **Path** parameter, instead of being specified in the value of **Name** .</span></span> <span data-ttu-id="30775-137">구문과 같이 두 명령 형식 모두 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-137">As indicated by the syntax, either command form is valid.</span></span>

```powershell
New-Item -ItemType "directory" -Path "c:\ps-test\scripts"
```

### <span data-ttu-id="30775-138">예 5: 여러 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="30775-138">Example 5: Create multiple files</span></span>

<span data-ttu-id="30775-139">이 예제에서는 두 개의 다른 디렉터리에 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30775-139">This example creates files in two different directories.</span></span> <span data-ttu-id="30775-140">**Path** 는 여러 문자열을 사용 하므로 여러 항목을 만드는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-140">Because **Path** takes multiple strings, you can use it to create multiple items.</span></span>

```powershell
New-Item -ItemType "file" -Path "c:\ps-test\test.txt", "c:\ps-test\Logs\test.log"
```

### <span data-ttu-id="30775-141">예제 6: 와일드 카드를 사용 하 여 여러 디렉터리에 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="30775-141">Example 6: Use wildcards to create files in multiple directories</span></span>

<span data-ttu-id="30775-142">`New-Item`Cmdlet은 **Path** 매개 변수에서 와일드 카드를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-142">The `New-Item` cmdlet supports wildcards in the **Path** parameter.</span></span> <span data-ttu-id="30775-143">다음 명령은 `temp.txt` **Path** 매개 변수에서 와일드 카드에 의해 지정 된 모든 디렉터리에 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30775-143">The following command creates a `temp.txt` file in all of the directories specified by the wildcards in the **Path** parameter.</span></span>

```powershell
Get-ChildItem -Path C:\Temp\
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d-----        5/15/2019   6:45 AM        1   One
d-----        5/15/2019   6:45 AM        1   Two
d-----        5/15/2019   6:45 AM        1   Three
```

```powershell
New-Item -Path * -Name temp.txt -ItemType File | Select-Object FullName
```

```Output
FullName
--------
C:\Temp\One\temp.txt
C:\Temp\Three\temp.txt
C:\Temp\Two\temp.txt
```

<span data-ttu-id="30775-144">`Get-ChildItem`Cmdlet은 디렉터리 아래에 세 개의 디렉터리를 표시 합니다 `C:\Temp` .</span><span class="sxs-lookup"><span data-stu-id="30775-144">The `Get-ChildItem` cmdlet shows three directories under the `C:\Temp` directory.</span></span> <span data-ttu-id="30775-145">Cmdlet은 와일드 카드를 사용 하 여 `New-Item` `temp.txt` 현재 디렉터리의 모든 디렉터리에 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30775-145">Using wildcards the `New-Item` cmdlet creates a `temp.txt` file in all of the directories under the current directory.</span></span> <span data-ttu-id="30775-146">`New-Item`Cmdlet은 `Select-Object` 새로 만든 파일의 경로를 확인 하기 위해 파이프 하 여 만든 항목을 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-146">The `New-Item` cmdlet outputs the items you created, which is piped to `Select-Object` to verify the paths of the newly created files.</span></span>

### <span data-ttu-id="30775-147">예 7: 파일이 나 폴더에 대 한 바로 가기 링크 만들기</span><span class="sxs-lookup"><span data-stu-id="30775-147">Example 7: Create a symbolic link to a file or folder</span></span>

<span data-ttu-id="30775-148">이 예제에서는 현재 폴더의 Notice.txt 파일에 대 한 바로 가기 링크를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30775-148">This example creates a symbolic link to the Notice.txt file in the current folder.</span></span>

```powershell
$link = New-Item -ItemType SymbolicLink -Path .\link -Target .\Notice.txt
$link | Select-Object LinkType, Target
```

```Output
LinkType     Target
--------     ------
SymbolicLink {.\Notice.txt}
```

<span data-ttu-id="30775-149">이 예제에서 **Target** 은 **값** 매개 변수에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="30775-149">In this example, **Target** is an alias for the **Value** parameter.</span></span> <span data-ttu-id="30775-150">기호화 된 링크의 대상은 상대 경로일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-150">The target of the symbolic link can be a relative path.</span></span> <span data-ttu-id="30775-151">PowerShell v 6.2 이전에는 대상이 정규화 된 경로 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-151">Prior to PowerShell v6.2, the target must be a fully-qualified path.</span></span>

<span data-ttu-id="30775-152">PowerShell 7.1부터 이제 상대 경로를 사용 하 여 Windows의 폴더에 대 한 **값인 symboliclink** 를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-152">Beginning in PowerShell 7.1, you can now create to a **SymbolicLink** to a folder on Windows using a relative path.</span></span>

### <span data-ttu-id="30775-153">예 8:-Force 매개 변수를 사용 하 여 폴더 다시 만들기 시도</span><span class="sxs-lookup"><span data-stu-id="30775-153">Example 8: Use the -Force parameter to attempt to recreate folders</span></span>

<span data-ttu-id="30775-154">이 예제에서는 안에 파일이 있는 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30775-154">This example creates a folder with a file inside.</span></span> <span data-ttu-id="30775-155">그런 다음를 사용 하 여 동일한 폴더를 만듭니다 `-Force` .</span><span class="sxs-lookup"><span data-stu-id="30775-155">Then, attempts to create the same folder using `-Force`.</span></span> <span data-ttu-id="30775-156">폴더를 덮어쓰지는 않지만 파일을 그대로 만든 상태로 기존 폴더 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-156">It will not overwrite the folder but simply return the existing folder object with the file created intact.</span></span>

```powershell
PS> New-Item -Path .\TestFolder -ItemType Directory
PS> New-Item -Path .\TestFolder\TestFile.txt -ItemType File

PS> New-Item -Path .\TestFolder -ItemType Directory -Force

    Directory: C:\
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         5/1/2020   8:03 AM                TestFolder

PS> Get-ChildItem .\TestFolder\

    Directory: C:\TestFolder
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:03 AM              0 TestFile.txt
```

### <span data-ttu-id="30775-157">예 9:-Force 매개 변수를 사용 하 여 기존 파일 덮어쓰기</span><span class="sxs-lookup"><span data-stu-id="30775-157">Example 9: Use the -Force parameter to overwrite existing files</span></span>

<span data-ttu-id="30775-158">이 예에서는 값을 사용 하 여 파일을 만든 다음를 사용 하 여 파일을 다시 만듭니다 `-Force` .</span><span class="sxs-lookup"><span data-stu-id="30775-158">This example creates a file with a value and then recreates the file using `-Force`.</span></span> <span data-ttu-id="30775-159">이렇게 하면 기존 파일이 덮어쓰므로 length 속성에서 볼 수 있는 것 처럼 내용이 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30775-159">This overwrites The existing file and it will lose it's content as you can see by the length property</span></span>

```powershell
PS> New-Item ./TestFile.txt -ItemType File -Value 'This is just a test file'

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM             24 TestFile.txt

New-Item ./TestFile.txt -ItemType File -Force

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM              0 TestFile.txt
```

> [!NOTE]
> <span data-ttu-id="30775-160">스위치와 함께를 사용 하 여 `New-Item` `-Force` 레지스트리 키를 만드는 경우 명령은 파일을 덮어쓸 때와 동일 하 게 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-160">When using `New-Item` with the `-Force` switch to create registry keys, the command will behave the same as when overwriting a file.</span></span> <span data-ttu-id="30775-161">레지스트리 키가 이미 있는 경우 키와 모든 속성 및 값은 빈 레지스트리 키로 덮어쓰여집니다.</span><span class="sxs-lookup"><span data-stu-id="30775-161">If the registry key already exists, the key and all properties and values will be overwritten with an empty registry key.</span></span>

## <span data-ttu-id="30775-162">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="30775-162">PARAMETERS</span></span>

### <span data-ttu-id="30775-163">-Credential</span><span class="sxs-lookup"><span data-stu-id="30775-163">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="30775-164">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-164">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="30775-165">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면를 사용 `Invoke-Command` 합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-165">To impersonate another user or elevate your credentials when running this cmdlet, use `Invoke-Command`.</span></span>

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

### <span data-ttu-id="30775-166">-Force</span><span class="sxs-lookup"><span data-stu-id="30775-166">-Force</span></span>

<span data-ttu-id="30775-167">이 cmdlet이 기존 읽기 전용 항목을 쓰는 항목을 강제로 만들도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-167">Forces this cmdlet to create an item that writes over an existing read-only item.</span></span> <span data-ttu-id="30775-168">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="30775-168">Implementation varies from provider to provider.</span></span> <span data-ttu-id="30775-169">**Force** 매개 변수를 사용 하는 경우에도 cmdlet은 보안 제한을 재정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-169">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="30775-170">-ItemType</span><span class="sxs-lookup"><span data-stu-id="30775-170">-ItemType</span></span>

<span data-ttu-id="30775-171">새 항목의 공급자별 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-171">Specifies the provider-specified type of the new item.</span></span> <span data-ttu-id="30775-172">이 매개 변수의 사용 가능한 값은 현재 사용 중인 공급자에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="30775-172">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="30775-173">위치가 드라이브에 있는 경우 `FileSystem` 다음 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-173">If your location is in a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="30775-174">파일</span><span class="sxs-lookup"><span data-stu-id="30775-174">File</span></span>
- <span data-ttu-id="30775-175">디렉터리</span><span class="sxs-lookup"><span data-stu-id="30775-175">Directory</span></span>
- <span data-ttu-id="30775-176">값인 symboliclink</span><span class="sxs-lookup"><span data-stu-id="30775-176">SymbolicLink</span></span>
- <span data-ttu-id="30775-177">분기 동기화</span><span class="sxs-lookup"><span data-stu-id="30775-177">Junction</span></span>
- <span data-ttu-id="30775-178">Hardlink create</span><span class="sxs-lookup"><span data-stu-id="30775-178">HardLink</span></span>

> [!NOTE]
> <span data-ttu-id="30775-179">`SymbolicLink`Windows에서 형식을 만들려면 관리자 권한 상승이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-179">Creating a `SymbolicLink` type on Windows requires elevation as administrator.</span></span> <span data-ttu-id="30775-180">그러나 개발자 모드를 사용 하는 Windows 10 (빌드 14972 이상)에서는 더 이상 사용 권한 상승을 사용 하 여 기호 링크를 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-180">However, Windows 10 (build 14972 or newer) with Developer Mode enabled no longer requires elevation creating symbolic links.</span></span>

<span data-ttu-id="30775-181">드라이브에 `Certificate` 다음과 같은 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-181">In a `Certificate` drive, these are the values you can specify:</span></span>

- <span data-ttu-id="30775-182">인증서 공급자</span><span class="sxs-lookup"><span data-stu-id="30775-182">Certificate Provider</span></span>
- <span data-ttu-id="30775-183">인증서</span><span class="sxs-lookup"><span data-stu-id="30775-183">Certificate</span></span>
- <span data-ttu-id="30775-184">스토어</span><span class="sxs-lookup"><span data-stu-id="30775-184">Store</span></span>
- <span data-ttu-id="30775-185">StoreLocation</span><span class="sxs-lookup"><span data-stu-id="30775-185">StoreLocation</span></span>

<span data-ttu-id="30775-186">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="30775-186">For more information see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="30775-187">-Name</span><span class="sxs-lookup"><span data-stu-id="30775-187">-Name</span></span>

<span data-ttu-id="30775-188">새 항목의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-188">Specifies the name of the new item.</span></span> <span data-ttu-id="30775-189">**Name** 또는 **path** 매개 변수 값에서 새 항목의 이름을 지정 하 고 **이름** 또는 **경로** 값에 새 항목의 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-189">You can specify the name of the new item in the **Name** or **Path** parameter value, and you can specify the path of the new item in **Name** or **Path** value.</span></span> <span data-ttu-id="30775-190">**Name** 매개 변수를 사용 하 여 전달 된 항목 이름은 **Path** 매개 변수의 값을 기준으로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30775-190">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: nameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="30775-191">-Path</span><span class="sxs-lookup"><span data-stu-id="30775-191">-Path</span></span>

<span data-ttu-id="30775-192">새 항목의 위치 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-192">Specifies the path of the location of the new item.</span></span> <span data-ttu-id="30775-193">**경로** 를 생략할 경우 기본값은 현재 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="30775-193">The default is the current location when **Path** is omitted.</span></span> <span data-ttu-id="30775-194">**이름** 에 새 항목의 이름을 지정 하거나 **경로** 에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-194">You can specify the name of the new item in **Name** , or include it in **Path** .</span></span> <span data-ttu-id="30775-195">**Name** 매개 변수를 사용 하 여 전달 된 항목 이름은 **Path** 매개 변수의 값을 기준으로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30775-195">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

<span data-ttu-id="30775-196">이 cmdlet의 경우 **Path** 매개 변수는 다른 Cmdlet의 **LiteralPath** 매개 변수와 유사 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-196">For this cmdlet, the **Path** parameter works like the **LiteralPath** parameter of other cmdlets.</span></span>
<span data-ttu-id="30775-197">와일드 카드 문자는 해석 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-197">Wildcard characters are not interpreted.</span></span> <span data-ttu-id="30775-198">모든 문자는 위치의 공급자에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30775-198">All characters are passed to the location's provider.</span></span> <span data-ttu-id="30775-199">공급자는 모든 문자를 지원 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-199">The provider may not support all characters.</span></span> <span data-ttu-id="30775-200">예를 들어, 별표 () 문자를 포함 하는 파일 이름을 만들 수 없습니다 `*` .</span><span class="sxs-lookup"><span data-stu-id="30775-200">For example, you cannot create a filename that contains an asterisk (`*`) character.</span></span>

```yaml
Type: System.String[]
Parameter Sets: pathSet
Aliases:

Required: True (pathSet), False (nameSet)
Position: 0
Default value: Current location
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="30775-201">-Value</span><span class="sxs-lookup"><span data-stu-id="30775-201">-Value</span></span>

<span data-ttu-id="30775-202">새 항목의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-202">Specifies the value of the new item.</span></span> <span data-ttu-id="30775-203">값을로 파이프 할 수도 있습니다 `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="30775-203">You can also pipe a value to `New-Item`.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Target

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="30775-204">-Confirm</span><span class="sxs-lookup"><span data-stu-id="30775-204">-Confirm</span></span>

<span data-ttu-id="30775-205">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-205">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="30775-206">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="30775-206">-WhatIf</span></span>

<span data-ttu-id="30775-207">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-207">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="30775-208">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-208">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="30775-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="30775-209">CommonParameters</span></span>

<span data-ttu-id="30775-210">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-210">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="30775-211">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30775-211">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="30775-212">입력</span><span class="sxs-lookup"><span data-stu-id="30775-212">INPUTS</span></span>

### <span data-ttu-id="30775-213">System.Object</span><span class="sxs-lookup"><span data-stu-id="30775-213">System.Object</span></span>

<span data-ttu-id="30775-214">새 항목의 값을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-214">You can pipe a value for the new item to this cmdlet.</span></span>

## <span data-ttu-id="30775-215">출력</span><span class="sxs-lookup"><span data-stu-id="30775-215">OUTPUTS</span></span>

### <span data-ttu-id="30775-216">System.Object</span><span class="sxs-lookup"><span data-stu-id="30775-216">System.Object</span></span>

<span data-ttu-id="30775-217">이 cmdlet은 만든 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-217">This cmdlet returns the item that it creates.</span></span>

## <span data-ttu-id="30775-218">참고</span><span class="sxs-lookup"><span data-stu-id="30775-218">NOTES</span></span>

<span data-ttu-id="30775-219">`New-Item` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="30775-219">`New-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="30775-220">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PsProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="30775-220">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="30775-221">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30775-221">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="30775-222">관련 링크</span><span class="sxs-lookup"><span data-stu-id="30775-222">RELATED LINKS</span></span>

[<span data-ttu-id="30775-223">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="30775-223">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="30775-224">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="30775-224">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="30775-225">Get-Item</span><span class="sxs-lookup"><span data-stu-id="30775-225">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="30775-226">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="30775-226">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="30775-227">Move-Item</span><span class="sxs-lookup"><span data-stu-id="30775-227">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="30775-228">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="30775-228">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="30775-229">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="30775-229">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="30775-230">Set-Item</span><span class="sxs-lookup"><span data-stu-id="30775-230">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="30775-231">about_Providers</span><span class="sxs-lookup"><span data-stu-id="30775-231">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

