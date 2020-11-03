---
description: FileSystem
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/18/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_filesystem_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 파일 시스템 공급자
ms.openlocfilehash: 8407dd11c3c9ead10b081b937fbac3db82735eb3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220946"
---
# <a name="filesystem-provider"></a><span data-ttu-id="2db19-104">파일 시스템 공급자</span><span class="sxs-lookup"><span data-stu-id="2db19-104">FileSystem provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="2db19-105">공급자 이름</span><span class="sxs-lookup"><span data-stu-id="2db19-105">Provider name</span></span>
<span data-ttu-id="2db19-106">FileSystem</span><span class="sxs-lookup"><span data-stu-id="2db19-106">FileSystem</span></span>

## <a name="drives"></a><span data-ttu-id="2db19-107">드라이브</span><span class="sxs-lookup"><span data-stu-id="2db19-107">Drives</span></span>

<span data-ttu-id="2db19-108">`C:`, `D:` ...</span><span class="sxs-lookup"><span data-stu-id="2db19-108">`C:`, `D:` ...</span></span>

## <a name="capabilities"></a><span data-ttu-id="2db19-109">기능</span><span class="sxs-lookup"><span data-stu-id="2db19-109">Capabilities</span></span>

<span data-ttu-id="2db19-110">**필터** , **shouldprocess**</span><span class="sxs-lookup"><span data-stu-id="2db19-110">**Filter** , **ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="2db19-111">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="2db19-111">Short description</span></span>

<span data-ttu-id="2db19-112">파일 및 디렉터리에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-112">Provides access to files and directories.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="2db19-113">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="2db19-113">Detailed description</span></span>

<span data-ttu-id="2db19-114">PowerShell **FileSystem** 공급자를 사용 하 여 powershell에서 파일 및 디렉터리를 가져오고 추가, 변경 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-114">The PowerShell **FileSystem** provider lets you get, add, change, clear, and delete files and directories in PowerShell.</span></span>

<span data-ttu-id="2db19-115">**FileSystem** 드라이브는 컴퓨터의 디렉터리와 파일을 포함 하는 계층적 네임 스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-115">The **FileSystem** drives are a hierarchical namespace containing the directories and files on your computer.</span></span> <span data-ttu-id="2db19-116">**FileSystem** 드라이브는 논리적 또는 물리적 드라이브, 디렉터리 또는 매핑된 네트워크 공유 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-116">A **FileSystem** drive can be a logical or phsyical drive, directory, or mapped network share.</span></span>

<span data-ttu-id="2db19-117">이라는 드라이브가 `TEMP:` 사용자의 임시 디렉터리 경로에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-117">A drive called `TEMP:` will be mapped to the user's temporary directory path.</span></span>

>[!NOTE]
> <span data-ttu-id="2db19-118">TEMP: 드라이브의 내용은 PowerShell에서 자동으로 제거 되지 않으며 관리할 사용자 또는 운영 체제에 따라 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-118">Contents in the TEMP: drive are not automatically removed by PowerShell and is up to the user or operating system to manage.</span></span>

<span data-ttu-id="2db19-119">**FileSystem** 공급자는이 문서에서 설명 하는 다음과 같은 cmdlet을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-119">The **FileSystem** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="2db19-120">Get-Location</span><span class="sxs-lookup"><span data-stu-id="2db19-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="2db19-121">Set-Location</span><span class="sxs-lookup"><span data-stu-id="2db19-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="2db19-122">Get-Item</span><span class="sxs-lookup"><span data-stu-id="2db19-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="2db19-123">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="2db19-123">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="2db19-124">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="2db19-124">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="2db19-125">Move-Item</span><span class="sxs-lookup"><span data-stu-id="2db19-125">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="2db19-126">New-Item</span><span class="sxs-lookup"><span data-stu-id="2db19-126">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="2db19-127">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="2db19-127">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="2db19-128">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2db19-128">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="2db19-129">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2db19-129">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="2db19-130">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="2db19-130">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="2db19-131">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2db19-131">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="2db19-132">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="2db19-132">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="2db19-133">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2db19-133">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="2db19-134">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="2db19-134">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="2db19-135">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="2db19-135">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)
- [<span data-ttu-id="2db19-136">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="2db19-136">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [<span data-ttu-id="2db19-137">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="2db19-137">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="2db19-138">이 공급자가 노출 하는 형식</span><span class="sxs-lookup"><span data-stu-id="2db19-138">Types exposed by this provider</span></span>

<span data-ttu-id="2db19-139">파일은 [system.object](/dotnet/api/system.io.fileinfo) 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-139">Files are instances of the [System.IO.FileInfo](/dotnet/api/system.io.fileinfo) class.</span></span>  <span data-ttu-id="2db19-140">디렉터리는 [system.io.directoryinfo](/dotnet/api/system.io.directoryinfo) 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-140">Directories are instances of the [System.IO.DirectoryInfo](/dotnet/api/system.io.directoryinfo) class.</span></span>

## <a name="navigating-the-filesystem-drives"></a><span data-ttu-id="2db19-141">파일 시스템 드라이브 탐색</span><span class="sxs-lookup"><span data-stu-id="2db19-141">Navigating the FileSystem drives</span></span>

<span data-ttu-id="2db19-142">**FileSystem** 공급자는 컴퓨터의 논리 드라이브를 PowerShell 드라이브로 매핑하여 해당 데이터 저장소를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-142">The **FileSystem** provider exposes its data stores by mapping any logical drives on the computer as PowerShell drives.</span></span> <span data-ttu-id="2db19-143">**파일 시스템** 드라이브로 작업 하려면 드라이브 이름 뒤에 콜론 ()을 사용 하 여 위치를 드라이브로 변경할 수 있습니다 `:` .</span><span class="sxs-lookup"><span data-stu-id="2db19-143">To work with a **FileSystem** drive you can change your location to a drive uing the drive name followed by a colon (`:`).</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="2db19-144">다른 PowerShell 드라이브에서 **FileSystem** 공급자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-144">You can also work with the **FileSystem** provider from any other PowerShell drive.</span></span> <span data-ttu-id="2db19-145">다른 위치에서 파일 또는 디렉터리를 참조 하려면 경로에 드라이브 이름 ( `C:` , `D:` , ...)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-145">To reference a file or directory from another location, use the drive name (`C:`, `D:`, ...) in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="2db19-146">PowerShell은 별칭을 사용 하 여 공급자 경로 작업을 수행할 수 있는 친숙 한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-146">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="2db19-147">`dir`및 등의 명령은 `ls` 이제 [Get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)에 대 한 별칭입니다 `cd` .는 [집합 위치](xref:Microsoft.PowerShell.Management.Set-Location)에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-147">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="2db19-148">및 `pwd` 은 [(는) 위치](xref:Microsoft.PowerShell.Management.Get-Location)에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-148">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-files-and-directories"></a><span data-ttu-id="2db19-149">파일 및 디렉터리 가져오기</span><span class="sxs-lookup"><span data-stu-id="2db19-149">Getting files and directories</span></span>

<span data-ttu-id="2db19-150">`Get-ChildItem`Cmdlet은 현재 위치에 있는 모든 파일과 디렉터리를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-150">The `Get-ChildItem` cmdlet returns all files and directories in the current location.</span></span> <span data-ttu-id="2db19-151">검색을 위해 다른 경로를 지정 하 고 기본 제공 매개 변수를 사용 하 여 재귀 깊이를 필터링 및 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-151">You can specify a different path to search and use built in parameters to filter and control the recursion depth.</span></span>

```powershell
Get-ChildItem
```

<span data-ttu-id="2db19-152">Cmdlet 사용에 대 한 자세한 내용은 [가져오기-자식 항목](xref:Microsoft.PowerShell.Management.Get-ChildItem)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2db19-152">To read more about cmdlet usage, see [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem).</span></span>

## <a name="copying-files-and-directories"></a><span data-ttu-id="2db19-153">파일 및 디렉터리 복사</span><span class="sxs-lookup"><span data-stu-id="2db19-153">Copying files and directories</span></span>

<span data-ttu-id="2db19-154">`Copy-Item`Cmdlet은 지정한 위치에 파일 및 디렉터리를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-154">The `Copy-Item` cmdlet copies files and directories to a location you specify.</span></span>
<span data-ttu-id="2db19-155">매개 변수는와 유사 하 게 필터링 및 재귀적으로 사용할 수 있습니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="2db19-155">Parameters are available to filter and recurse, similar to `Get-ChildItem`.</span></span>

<span data-ttu-id="2db19-156">다음 명령은 경로 "C:\temp"의 모든 파일 및 디렉터리 \" 를 "C:\\temp" 폴더로 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-156">The following command copies all of the files and directories under the path "C:\temp\" to the folder "C:\Windows\Temp".</span></span>

```powershell
Copy-Item -Path C:\temp\* -Destination C:\Windows\Temp -Recurse -File
```

<span data-ttu-id="2db19-157">`Copy-Item` 확인 메시지를 표시 하지 않고 대상 디렉터리의 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-157">`Copy-Item` overwrites files in the destination directory without prompting for confirmation.</span></span>

<span data-ttu-id="2db19-158">이 명령은 디렉터리의 `a.txt` 파일을 `C:\a` 디렉터리에 복사 `C:\a\bb` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-158">This command copies the `a.txt` file from the `C:\a` directory to the `C:\a\bb` directory.</span></span>

```powershell
Copy-Item -Path C:\a\a.txt -Destination C:\a\bb\a.txt
```

<span data-ttu-id="2db19-159">디렉터리의 모든 디렉터리와 파일 `C:\a` 을 디렉터리에 복사 `C:\c` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-159">Copies all the directories and files in the `C:\a` directory to the `C:\c` directory.</span></span> <span data-ttu-id="2db19-160">복사할 디렉터리가 대상 디렉터리에 이미 있는 경우에는 Force 매개 변수를 사용하지 않은 한 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-160">If any of the directories to copy already exist in the destination directory, the command will fail unless you specify the Force parameter.</span></span>

```powershell
Copy-Item -Path C:\a\* -Destination C:\c -Recurse
```

<span data-ttu-id="2db19-161">자세한 내용은 [복사 항목](xref:Microsoft.PowerShell.Management.Copy-Item)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2db19-161">For more information, see [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item).</span></span>

## <a name="moving-files-and-directories"></a><span data-ttu-id="2db19-162">파일 및 디렉터리 이동</span><span class="sxs-lookup"><span data-stu-id="2db19-162">Moving files and directories</span></span>

<span data-ttu-id="2db19-163">이 명령은 디렉터리의 `c.txt` 파일 `C:\a` 을 디렉터리로 이동 합니다 `C:\a\aa` .</span><span class="sxs-lookup"><span data-stu-id="2db19-163">This command moves the `c.txt` file in the `C:\a` directory to the `C:\a\aa` directory:</span></span>

```powershell
Move-Item -Path C:\a\c.txt -Destination C:\a\aa
```

<span data-ttu-id="2db19-164">이 명령은 이름이 같은 기존 파일을 자동으로 덮어쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-164">The command will not automatically overwrite an existing file that has the same name.</span></span> <span data-ttu-id="2db19-165">cmdlet이 기존 파일을 덮어쓰도록 강제하려면 Force 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-165">To force the cmdlet to overwrite an existing file, specify the Force parameter.</span></span>

<span data-ttu-id="2db19-166">이동할 디렉터리가 현재 위치인 경우에는 해당 디렉터리를 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-166">You cannot move a directory when that directory is the current location.</span></span> <span data-ttu-id="2db19-167">`Move-Item`를 사용 하 여 현재 위치에서 디렉터리를 이동 하는 경우이 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-167">When you use `Move-Item` to move the directory at the current location, you see this error.</span></span>

```
C:\temp> Move-Item -Path C:\temp\ -Destination C:\Windows\Temp

Move-Item : Cannot move item because the item at 'C:\temp\' is in use.
At line:1 char:1
+ Move-Item C:\temp\ C:\temp2\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Move-Item], PSInvalidOperationException
    + FullyQualifiedErrorId : InvalidOperation,Microsoft.PowerShell.Commands.MoveItemCommand
```

## <a name="managing-file-content"></a><span data-ttu-id="2db19-168">파일 콘텐츠 관리</span><span class="sxs-lookup"><span data-stu-id="2db19-168">Managing file content</span></span>

### <a name="get-the-content-of-a-file"></a><span data-ttu-id="2db19-169">파일의 콘텐츠 가져오기</span><span class="sxs-lookup"><span data-stu-id="2db19-169">Get the content of a file</span></span>

<span data-ttu-id="2db19-170">이 명령은 "Test.txt" 파일의 콘텐츠를 가져와 콘솔에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-170">This command gets the contents of the "Test.txt" file and displays them in the console.</span></span>

```powershell
Get-Content -Path Test.txt
```

<span data-ttu-id="2db19-171">파일 내용을 다른 cmdlet으로 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-171">You can pipe the contents of the file to another cmdlet.</span></span> <span data-ttu-id="2db19-172">예를 들어 다음 명령은 파일의 내용을 읽은 `Test.txt` 다음 [convertto-html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) cmdlet에 대 한 입력으로 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-172">For example, the following command reads the contents of the `Test.txt` file and then supplies them as input to the [ConvertTo-Html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) cmdlet:</span></span>

```powershell
Get-Content -Path Test.txt | ConvertTo-Html
```

<span data-ttu-id="2db19-173">공급자 경로에 달러 기호 ()를 접두사로 사용 하 여 파일의 내용을 검색할 수도 있습니다 `$` .</span><span class="sxs-lookup"><span data-stu-id="2db19-173">You can also retrieve the content of a file by prefixing its provider path with the dollar sign (`$`).</span></span> <span data-ttu-id="2db19-174">변수 명명 제한으로 인해 경로를 중괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-174">The path must be enclosed in curly braces due to variable naming restrictions.</span></span> <span data-ttu-id="2db19-175">자세한 내용은 [about_Variables](about_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2db19-175">For more information, see [about_Variables](about_Variables.md).</span></span>

```powershell
${C:\Windows\System32\Drivers\etc\hosts}
```

### <a name="add-content-to-a-file"></a><span data-ttu-id="2db19-176">파일에 콘텐츠 추가</span><span class="sxs-lookup"><span data-stu-id="2db19-176">Add content to a file</span></span>

<span data-ttu-id="2db19-177">이 명령은 "test content" 문자열을 파일에 추가 합니다 `Test.txt` .</span><span class="sxs-lookup"><span data-stu-id="2db19-177">This command appends the "test content" string to the `Test.txt` file:</span></span>

```powershell
Add-Content -Path test.txt -Value "test content"
```

<span data-ttu-id="2db19-178">파일의 기존 내용은 `Test.txt` 삭제 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-178">The existing content in the `Test.txt` file is not deleted.</span></span>

### <a name="replace-the-content-of-a-file"></a><span data-ttu-id="2db19-179">파일의 내용을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-179">Replace the content of a file</span></span>

<span data-ttu-id="2db19-180">이 명령은 파일의 내용을 `Test.txt` "test content" 문자열로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-180">This command replaces the contents of the `Test.txt` file with the "test content" string:</span></span>

```powershell
Set-Content -Path test.txt -Value "test content"
```

<span data-ttu-id="2db19-181">의 내용을 덮어씁니다 `Test.txt` .</span><span class="sxs-lookup"><span data-stu-id="2db19-181">It overwrites the contents of `Test.txt`.</span></span> <span data-ttu-id="2db19-182">[새 항목](xref:Microsoft.PowerShell.Management.New-Item) Cmdlet의 **Value** 매개 변수를 사용 하 여 파일을 만들 때 파일에 콘텐츠를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-182">You can use the **Value** parameter of the [New-Item](xref:Microsoft.PowerShell.Management.New-Item) cmdlet to add content to a file when you create it.</span></span>

### <a name="loop-through-the-contents-of-a-file"></a><span data-ttu-id="2db19-183">파일의 콘텐츠를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-183">Loop through the contents of a file</span></span>

<span data-ttu-id="2db19-184">기본적으로 cmdlet은 `Get-Content` 줄 끝 문자를 구분 기호로 사용 하므로 파일을 문자열 컬렉션으로 가져오고 각 줄을 파일의 한 문자열로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-184">By default, the `Get-Content` cmdlet uses the end-of-line character as its delimiter, so it gets a file as a collection of strings, with each line as one string in the file.</span></span>

<span data-ttu-id="2db19-185">매개 변수를 사용 `-Delimiter` 하 여 대체 구분 기호를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-185">You can use the `-Delimiter` parameter to specify an alternate delimiter.</span></span> <span data-ttu-id="2db19-186">이를 섹션의 끝 또는 다음 섹션의 시작을 나타내는 문자로 설정하면 파일을 논리적 부분으로 분할할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-186">If you set it to the characters that denote the end of a section or the beginning of the next section, you can split the file into logical parts.</span></span>

<span data-ttu-id="2db19-187">첫 번째 명령은 파일을 가져와 `Employees.txt` 섹션으로 분할 합니다. 각 섹션은 "직원의 끝 레코드" 라는 단어로 끝나는 후 변수에 저장 합니다 `$e` .</span><span class="sxs-lookup"><span data-stu-id="2db19-187">The first command gets the `Employees.txt` file and splits it into sections, each of which ends with the words "End of Employee Record" and it saves it in the `$e` variable.</span></span>

<span data-ttu-id="2db19-188">두 번째 명령은 배열 표기법을 사용 하 여에서 컬렉션의 첫 번째 항목을 가져옵니다 `$e` .</span><span class="sxs-lookup"><span data-stu-id="2db19-188">The second command uses array notation to get the first item in the collection in `$e`.</span></span> <span data-ttu-id="2db19-189">PowerShell 배열은 0부터 시작 하므로 인덱스는 0을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-189">It uses an index of 0, because PowerShell arrays are zero-based.</span></span>

<span data-ttu-id="2db19-190">Cmdlet에 대 한 자세한 내용은 `Get-Content` [get-help](xref:Microsoft.PowerShell.Management.Get-Content)의 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2db19-190">For more information about `Get-Content` cmdlet, see the help topic for the [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content).</span></span>

<span data-ttu-id="2db19-191">배열에 대 한 자세한 내용은 [about_Arrays](../About/about_Arrays.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2db19-191">For more information about arrays, see [about_Arrays](../About/about_Arrays.md).</span></span>

```powershell
$e = Get-Content c:\test\employees.txt -Delimited "End Of Employee Record"
$e[0]
```

## <a name="managing-security-descriptors"></a><span data-ttu-id="2db19-192">보안 설명자 관리</span><span class="sxs-lookup"><span data-stu-id="2db19-192">Managing security descriptors</span></span>

### <a name="view-the-acl-for-a-file"></a><span data-ttu-id="2db19-193">파일에 대 한 ACL 보기</span><span class="sxs-lookup"><span data-stu-id="2db19-193">View the ACL for a file</span></span>

<span data-ttu-id="2db19-194">이 명령은 [accesscontrol-namespace. system.security.accesscontrol.filesecurity](/dotnet/api/system.security.accesscontrol.filesecurity) 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-194">This command returns a [System.Security.AccessControl.FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) object:</span></span>

```powershell
Get-Acl -Path test.txt | Format-List -Property *
```

<span data-ttu-id="2db19-195">이 개체에 대 한 자세한 내용은 명령을 [Get Member](xref:Microsoft.PowerShell.Utility.Get-Member) cmdlet에 파이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-195">For more information about this object, pipe the command to the [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member) cmdlet.</span></span> <span data-ttu-id="2db19-196">또는 MSDN (Microsoft Developer Network) 라이브러리의 "[System.security.accesscontrol.filesecurity](/dotnet/api/system.security.accesscontrol.filesecurity) 클래스"를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2db19-196">Or, see "[FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) Class" in the MSDN (Microsoft Developer Network) library.</span></span>

### <a name="modify-the-acl-for-a-file"></a><span data-ttu-id="2db19-197">파일에 대 한 ACL 수정</span><span class="sxs-lookup"><span data-stu-id="2db19-197">Modify the ACL for a file</span></span>

### <a name="create-and-set-an-acl-for-a-file"></a><span data-ttu-id="2db19-198">파일에 대 한 ACL을 만들고 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-198">Create and set an ACL for a file</span></span>

## <a name="creating-files-and-directories"></a><span data-ttu-id="2db19-199">파일 및 디렉터리 만들기</span><span class="sxs-lookup"><span data-stu-id="2db19-199">Creating files and directories</span></span>

### <a name="create-a-directory"></a><span data-ttu-id="2db19-200">디렉터리 만들기</span><span class="sxs-lookup"><span data-stu-id="2db19-200">Create a directory</span></span>

<span data-ttu-id="2db19-201">이 명령은 `logfiles` 드라이브에 디렉터리를 만듭니다 `C` .</span><span class="sxs-lookup"><span data-stu-id="2db19-201">This command creates the `logfiles` directory on the `C` drive:</span></span>

```powershell
New-Item -Path c:\ -Name logfiles -Type directory
```

<span data-ttu-id="2db19-202">PowerShell에는 새 `mkdir` `md` 디렉터리를 만드는 데 [새 항목](xref:Microsoft.PowerShell.Management.New-Item) cmdlet을 사용 하는 함수 (별칭)도 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-202">PowerShell also includes a `mkdir` function (alias `md`) that uses the [New-Item](xref:Microsoft.PowerShell.Management.New-Item) cmdlet to create a new directory.</span></span>

### <a name="create-a-file"></a><span data-ttu-id="2db19-203">파일 만들기</span><span class="sxs-lookup"><span data-stu-id="2db19-203">Create a file</span></span>

<span data-ttu-id="2db19-204">이 명령은 `log2.txt` 디렉터리에 파일을 만든 `C:\logfiles` 다음 "test log" 문자열을 파일에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-204">This command creates the `log2.txt` file in the `C:\logfiles` directory and then adds the "test log" string to the file:</span></span>

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file
```

### <a name="create-a-file-with-content"></a><span data-ttu-id="2db19-205">콘텐츠를 포함하는 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="2db19-205">Create a file with content</span></span>

<span data-ttu-id="2db19-206">디렉터리에 라는 파일을 만들고이 파일 `log2.txt` `C:\logfiles` 에 "test log" 문자열을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-206">Creates a file called `log2.txt` in the `C:\logfiles` directory and adds the string "test log" to the file.</span></span>

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file -Value "test log"
```

## <a name="renaming-files-and-directories"></a><span data-ttu-id="2db19-207">파일 및 디렉터리 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="2db19-207">Renaming files and directories</span></span>

### <a name="rename-a-file"></a><span data-ttu-id="2db19-208">파일 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="2db19-208">Rename a file</span></span>

<span data-ttu-id="2db19-209">이 명령은 `a.txt` 디렉터리의 파일 이름을 `C:\a` `b.txt` 다음과 같이 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-209">This command renames the `a.txt` file in the `C:\a` directory to `b.txt`:</span></span>

```powershell
Rename-Item -Path c:\a\a.txt -NewName b.txt
```

### <a name="rename-a-directory"></a><span data-ttu-id="2db19-210">디렉터리 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="2db19-210">Rename a directory</span></span>

<span data-ttu-id="2db19-211">이 명령은 디렉터리의 이름을 `C:\a\cc` `C:\a\dd` 다음과 같이 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-211">This command renames the `C:\a\cc` directory to `C:\a\dd`:</span></span>

```powershell
Rename-Item -Path c:\a\cc -NewName dd
```

## <a name="deleting-files-and-directories"></a><span data-ttu-id="2db19-212">파일 및 디렉터리 삭제</span><span class="sxs-lookup"><span data-stu-id="2db19-212">Deleting files and directories</span></span>

### <a name="delete-a-file"></a><span data-ttu-id="2db19-213">파일 삭제</span><span class="sxs-lookup"><span data-stu-id="2db19-213">Delete a file</span></span>

<span data-ttu-id="2db19-214">이 명령은 `Test.txt` 현재 디렉터리에서 파일을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-214">This command deletes the `Test.txt` file in the current directory:</span></span>

```powershell
Remove-Item -Path test.txt
```

### <a name="delete-files-using-wildcards"></a><span data-ttu-id="2db19-215">와일드 카드를 사용 하 여 파일 삭제</span><span class="sxs-lookup"><span data-stu-id="2db19-215">Delete files using wildcards</span></span>

<span data-ttu-id="2db19-216">이 명령은 현재 디렉터리에서 파일 이름 확장명이 인 모든 파일을 삭제 합니다 `.xml` .</span><span class="sxs-lookup"><span data-stu-id="2db19-216">This command deletes all the files in the current directory that have the `.xml` file name extension:</span></span>

```powershell
Remove-Item -Path *.xml
```

## <a name="starting-a-program-by-invoking-an-associated-file"></a><span data-ttu-id="2db19-217">연결 된 파일을 호출 하 여 프로그램 시작</span><span class="sxs-lookup"><span data-stu-id="2db19-217">Starting a program by invoking an associated file</span></span>

### <a name="invoke-a-file"></a><span data-ttu-id="2db19-218">파일 호출</span><span class="sxs-lookup"><span data-stu-id="2db19-218">Invoke a file</span></span>

<span data-ttu-id="2db19-219">첫 번째 명령은 [get-help](xref:Microsoft.PowerShell.Management.Get-Service) cmdlet을 사용 하 여 로컬 서비스에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-219">The first command uses the [Get-Service](xref:Microsoft.PowerShell.Management.Get-Service) cmdlet to get information about local services.</span></span>

<span data-ttu-id="2db19-220">[내보내기-Csv](xref:Microsoft.PowerShell.Utility.Export-Csv) cmdlet으로 정보를 파이프 한 다음 해당 정보를 파일에 저장 `Services.csv` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-220">It pipes the information to the [Export-Csv](xref:Microsoft.PowerShell.Utility.Export-Csv) cmdlet and then stores that information in the `Services.csv` file.</span></span>

<span data-ttu-id="2db19-221">두 번째 명령은 [Invoke 항목](xref:Microsoft.PowerShell.Management.Invoke-Item) 을 사용 하 여 `services.csv` 확장과 연결 된 프로그램에서 파일을 엽니다 `.csv` .</span><span class="sxs-lookup"><span data-stu-id="2db19-221">The second command uses [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item) to open the `services.csv` file in the program associated with the `.csv` extension:</span></span>

```powershell
Get-Service | Export-Csv -Path services.csv
Invoke-Item -Path services.csv
```

## <a name="getting-files-and-folders-with-specified-attributes"></a><span data-ttu-id="2db19-222">지정 된 특성을 사용 하 여 파일 및 폴더 가져오기</span><span class="sxs-lookup"><span data-stu-id="2db19-222">Getting files and folders with specified attributes</span></span>

### <a name="get-system-files"></a><span data-ttu-id="2db19-223">시스템 파일 가져오기</span><span class="sxs-lookup"><span data-stu-id="2db19-223">Get System files</span></span>

<span data-ttu-id="2db19-224">이 명령은 현재 디렉터리 및 하위 디렉터리에 있는 시스템 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-224">This command gets system files in the current directory and its subdirectories.</span></span>

<span data-ttu-id="2db19-225">매개 변수를 사용 하 여 `-File` 디렉터리가 아닌 파일만 가져오고 매개 변수를 사용 하 여 `-System` "system" 특성이 있는 항목만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-225">It uses the `-File` parameter to get only files (not directories) and the `-System` parameter to get only items with the "system" attribute.</span></span>

<span data-ttu-id="2db19-226">매개 변수를 사용 하 여 `-Recurse` 현재 디렉터리와 모든 하위 디렉터리의 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-226">It uses the `-Recurse` parameter to get the items in the current directory and all subdirectories.</span></span>

```powershell
Get-ChildItem -File -System -Recurse
```

### <a name="get-hidden-files"></a><span data-ttu-id="2db19-227">숨겨진 파일 가져오기</span><span class="sxs-lookup"><span data-stu-id="2db19-227">Get Hidden files</span></span>

<span data-ttu-id="2db19-228">이 명령은 현재 디렉터리의 숨겨진 파일을 비롯한 모든 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-228">This command gets all files, including hidden files, in the current directory.</span></span>

<span data-ttu-id="2db19-229">이 매개 변수는 두 개의 값이 있는 **Attributes** 매개 변수를 사용 합니다 .이 매개 변수는 `!Directory+Hidden` 숨겨진 파일을 가져오고 `!Directory` 다른 모든 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-229">It uses the **Attributes** parameter with two values, `!Directory+Hidden`, which gets hidden files, and `!Directory`, which gets all other files.</span></span>

```powershell
Get-ChildItem -Attributes !Directory,!Directory+Hidden
```

<span data-ttu-id="2db19-230">`dir -att !d,!d+h` 는이 명령과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-230">`dir -att !d,!d+h` is the equivalent of this command.</span></span>

### <a name="get-compressed-and-encrypted-files"></a><span data-ttu-id="2db19-231">압축 및 암호화 된 파일 가져오기</span><span class="sxs-lookup"><span data-stu-id="2db19-231">Get Compressed and Encrypted files</span></span>

<span data-ttu-id="2db19-232">이 명령은 압축 또는 암호화된 현재 디렉터리의 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-232">This command gets files in the current directory that are either compressed or encrypted.</span></span>

<span data-ttu-id="2db19-233">이 메서드는 `-Attributes` 매개 변수를 두 값 (및)으로 사용 `Compressed` `Encrypted` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-233">It uses the `-Attributes` parameter with two values, `Compressed` and `Encrypted`.</span></span> <span data-ttu-id="2db19-234">값은 `,` "OR" 연산자를 나타내는 쉼표로 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-234">The values are separated by a comma `,` which represents the "OR" operator.</span></span>

```powershell
Get-ChildItem -Attributes Compressed,Encrypted
```

## <a name="dynamic-parameters"></a><span data-ttu-id="2db19-235">동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="2db19-235">Dynamic parameters</span></span>

<span data-ttu-id="2db19-236">동적 매개 변수는 PowerShell 공급자가 추가 하는 cmdlet 매개 변수 이며, 공급자 사용 드라이브에서 cmdlet을 사용 하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-236">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="encoding-microsoftpowershellcommandsfilesystemcmdletproviderencoding"></a><span data-ttu-id="2db19-237">Encoding \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\></span><span class="sxs-lookup"><span data-stu-id="2db19-237">Encoding \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\></span></span>

<span data-ttu-id="2db19-238">파일 인코딩을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-238">Specifies the file encoding.</span></span> <span data-ttu-id="2db19-239">기본값은 ASCII입니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-239">The default is ASCII.</span></span>

- <span data-ttu-id="2db19-240">**Ascii** : ascii (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-240">**ASCII** :  Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="2db19-241">**BigEndianUnicode** : 빅 endian 바이트 순서를 사용 하 여 utf-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-241">**BigEndianUnicode** :  Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="2db19-242">**문자열** : 문자열에 인코딩 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-242">**String** :  Uses the encoding type for a string.</span></span>
- <span data-ttu-id="2db19-243">**Unicode** : 작은 endian 바이트 순서를 사용 하 여 utf-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-243">**Unicode** :  Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="2db19-244">**UTF7** : u t f-7 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-244">**UTF7** :   Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="2db19-245">**UTF8** : utf-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-245">**UTF8** :  Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="2db19-246">**UTF8BOM** : 바이트 순서 표시 (BOM)를 사용 하 여 utf-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-246">**UTF8BOM** : Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="2db19-247">**UF8NOBOM** : BOM (바이트 순서 표시) 없이 utf-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-247">**UF8NOBOM** : Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="2db19-248">**UTF32** : u t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-248">**UTF32** :  Encodes in UTF-32 format.</span></span>
- <span data-ttu-id="2db19-249">**기본값** : 설치 된 기본 코드 페이지에서 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-249">**Default** : Encodes in the default installed code page.</span></span>
- <span data-ttu-id="2db19-250">**OEM** : MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-250">**OEM** : Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="2db19-251">**알 수 없음** : 인코딩 유형을 알 수 없거나 잘못 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-251">**Unknown** :  The encoding type is unknown or invalid.</span></span> <span data-ttu-id="2db19-252">데이터가 Binary로 처리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-252">The data can be treated as binary.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="2db19-253">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="2db19-253">Cmdlets supported</span></span>

- [<span data-ttu-id="2db19-254">Add-Content</span><span class="sxs-lookup"><span data-stu-id="2db19-254">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="2db19-255">Get-Content</span><span class="sxs-lookup"><span data-stu-id="2db19-255">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="2db19-256">Set-Content</span><span class="sxs-lookup"><span data-stu-id="2db19-256">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="delimiter-systemstring"></a><span data-ttu-id="2db19-257">Delimiter \<System.String\></span><span class="sxs-lookup"><span data-stu-id="2db19-257">Delimiter \<System.String\></span></span>

<span data-ttu-id="2db19-258">[Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)가 파일을 읽는 동안 파일을 개체로 나누는 데 사용하는 구분 기호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-258">Specifies the delimiter that [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) uses to divide the file into objects while it reads.</span></span>

<span data-ttu-id="2db19-259">기본값은 `\n` 줄 끝 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-259">The default is `\n`, the end-of-line character.</span></span>

<span data-ttu-id="2db19-260">텍스트 파일을 읽을 때 [Get Content](xref:Microsoft.PowerShell.Management.Get-Content) 는 각각 구분 기호 문자로 끝나는 문자열 개체의 컬렉션을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-260">When reading a text file, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) returns a collection of string objects, each of which ends with the delimiter character.</span></span>

<span data-ttu-id="2db19-261">파일에 존재 하지 않는 구분 기호를 입력 하면 [Get Content](xref:Microsoft.PowerShell.Management.Get-Content) 는 전체 파일을 구분 되지 않은 단일 개체로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-261">Entering a delimiter that does not exist in the file, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) returns the entire file as a single, un-delimited object.</span></span>

<span data-ttu-id="2db19-262">이 매개 변수를 사용하여 "End of Example"과 같은 파일 구분 기호를 지정하여 큰 파일을 여러 개의 더 작은 파일로 분할할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-262">You can use this parameter to split a large file into smaller files by specifying a file separator, such as "End of Example", as the delimiter.</span></span> <span data-ttu-id="2db19-263">구분 기호는 보존되고(삭제되지 않음) 각 파일 섹션의 마지막 항목이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-263">The delimiter is preserved (not discarded) and becomes the last item in each file section.</span></span>

> [!NOTE]
> <span data-ttu-id="2db19-264">현재 `-Delimiter` 매개 변수 값이 빈 문자열인 경우 [Get Content](xref:Microsoft.PowerShell.Management.Get-Content) 는 아무것도 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-264">Currently, when the value of the `-Delimiter` parameter is an empty string, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) does not return anything.</span></span>
> <span data-ttu-id="2db19-265">이것은 알려진 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-265">This is a known issue.</span></span> <span data-ttu-id="2db19-266">강제로 [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)가 전체 파일을 구분되지 않은 단일 문자열로 반환하게 하려면 파일에 존재하지 않는 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-266">To force [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) to return the entire file as a single, undelimited string, enter a value that does not exist in the file.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="2db19-267">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="2db19-267">Cmdlets supported</span></span>

- [<span data-ttu-id="2db19-268">Get-Content</span><span class="sxs-lookup"><span data-stu-id="2db19-268">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="wait-systemmanagementautomationswitchparameter"></a><span data-ttu-id="2db19-269">Wait \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="2db19-269">Wait \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="2db19-270">내용이 파일에 추가되기를 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-270">Waits for content to be appended to the file.</span></span> <span data-ttu-id="2db19-271">내용이 추가되면 추가된 내용을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-271">If content is appended, it returns the appended content.</span></span> <span data-ttu-id="2db19-272">내용이 변경된 경우에는 전체 파일을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-272">If the content has changed, it returns the entire file.</span></span>

<span data-ttu-id="2db19-273">기다리는 동안 [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)는 Ctrl+C를 눌러 사용자가 중단할 때까지 1초에 한 번씩 파일을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-273">When waiting, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) checks the file once each second until you interrupt it, such as by pressing CTRL+C.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="2db19-274">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="2db19-274">Cmdlets supported</span></span>

- [<span data-ttu-id="2db19-275">Get-Content</span><span class="sxs-lookup"><span data-stu-id="2db19-275">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="attributes-flagsexpression"></a><span data-ttu-id="2db19-276">Attributes \<FlagsExpression\></span><span class="sxs-lookup"><span data-stu-id="2db19-276">Attributes \<FlagsExpression\></span></span>

<span data-ttu-id="2db19-277">지정된 특성을 갖는 파일 및 폴더를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-277">Gets files and folders with the specified attributes.</span></span> <span data-ttu-id="2db19-278">이 매개 변수는 모든 특성을 지원하며 복잡한 특성 조합을 지정할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-278">This parameter supports all attributes and lets you specify complex combinations of attributes.</span></span>

<span data-ttu-id="2db19-279">`-Attributes`매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-279">The `-Attributes` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="2db19-280">`-Attributes`매개 변수는 다음 특성을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-280">The `-Attributes` parameter supports the following attributes:</span></span>

- <span data-ttu-id="2db19-281">**보관**</span><span class="sxs-lookup"><span data-stu-id="2db19-281">**Archive**</span></span>
- <span data-ttu-id="2db19-282">**Compressed**</span><span class="sxs-lookup"><span data-stu-id="2db19-282">**Compressed**</span></span>
- <span data-ttu-id="2db19-283">**디바이스**</span><span class="sxs-lookup"><span data-stu-id="2db19-283">**Device**</span></span>
- <span data-ttu-id="2db19-284">**디렉터리**</span><span class="sxs-lookup"><span data-stu-id="2db19-284">**Directory**</span></span>
- <span data-ttu-id="2db19-285">**암호화됨**</span><span class="sxs-lookup"><span data-stu-id="2db19-285">**Encrypted**</span></span>
- <span data-ttu-id="2db19-286">**숨김**</span><span class="sxs-lookup"><span data-stu-id="2db19-286">**Hidden**</span></span>
- <span data-ttu-id="2db19-287">**보통**</span><span class="sxs-lookup"><span data-stu-id="2db19-287">**Normal**</span></span>
- <span data-ttu-id="2db19-288">**NotContentIndexed**</span><span class="sxs-lookup"><span data-stu-id="2db19-288">**NotContentIndexed**</span></span>
- <span data-ttu-id="2db19-289">**라인인**</span><span class="sxs-lookup"><span data-stu-id="2db19-289">**Offline**</span></span>
- <span data-ttu-id="2db19-290">**읽기 전용**</span><span class="sxs-lookup"><span data-stu-id="2db19-290">**ReadOnly**</span></span>
- <span data-ttu-id="2db19-291">**ReparsePoint**</span><span class="sxs-lookup"><span data-stu-id="2db19-291">**ReparsePoint**</span></span>
- <span data-ttu-id="2db19-292">**SparseFile**</span><span class="sxs-lookup"><span data-stu-id="2db19-292">**SparseFile**</span></span>
- <span data-ttu-id="2db19-293">**시스템**</span><span class="sxs-lookup"><span data-stu-id="2db19-293">**System**</span></span>
- <span data-ttu-id="2db19-294">**임시**</span><span class="sxs-lookup"><span data-stu-id="2db19-294">**Temporary**</span></span>

<span data-ttu-id="2db19-295">이러한 특성에 대 한 설명은 [Fileattributes](/dotnet/api/system.io.fileattributes) 열거를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2db19-295">For a description of these attributes, see the [FileAttributes](/dotnet/api/system.io.fileattributes) enumeration.</span></span>

<span data-ttu-id="2db19-296">다음 연산자를 사용하여 특성을 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-296">Use the following operators to combine attributes.</span></span>

- <span data-ttu-id="2db19-297">`!` -NOT</span><span class="sxs-lookup"><span data-stu-id="2db19-297">`!` - NOT</span></span>
- <span data-ttu-id="2db19-298">`+` -및</span><span class="sxs-lookup"><span data-stu-id="2db19-298">`+` - AND</span></span>
- <span data-ttu-id="2db19-299">`,` -또는</span><span class="sxs-lookup"><span data-stu-id="2db19-299">`,` - OR</span></span>

<span data-ttu-id="2db19-300">연산자 및 해당 특성 사이에는 공백이 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-300">No spaces are permitted between an operator and its attribute.</span></span> <span data-ttu-id="2db19-301">그러나 쉼표 앞에는 공백이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-301">However, spaces are permitted before commas.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="2db19-302">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="2db19-302">Cmdlets supported</span></span>

- [<span data-ttu-id="2db19-303">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="2db19-303">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="directory-systemmanagementautomationswitchparameter"></a><span data-ttu-id="2db19-304">Directory \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="2db19-304">Directory \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="2db19-305">디렉터리(폴더)를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-305">Gets directories (folders).</span></span>

<span data-ttu-id="2db19-306">`-Directory`매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-306">The `-Directory` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="2db19-307">디렉터리만 가져오려면 매개 변수를 사용 하 `-Directory` 고 `-File` 매개 변수를 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-307">To get only directories, use the `-Directory` parameter and omit the `-File` parameter.</span></span> <span data-ttu-id="2db19-308">디렉터리를 제외 하려면 매개 변수를 사용 하 고 매개 변수를 `-File` 생략 `-Directory` 하거나 `-Attributes` 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-308">To exclude directories, use the `-File` parameter and omit the `-Directory` parameter, or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="2db19-309">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="2db19-309">Cmdlets supported</span></span>

- [<span data-ttu-id="2db19-310">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="2db19-310">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="file-systemmanagementautomationswitchparameter"></a><span data-ttu-id="2db19-311">File \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="2db19-311">File \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="2db19-312">파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-312">Gets files.</span></span>

<span data-ttu-id="2db19-313">`-File`매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-313">The `-File` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="2db19-314">파일만 가져오려면 매개 변수를 사용 하 `-File` 고 `-Directory` 매개 변수를 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-314">To get only files, use the `-File` parameter and omit the `-Directory` parameter.</span></span> <span data-ttu-id="2db19-315">파일을 제외 하려면 매개 변수를 사용 하 고 매개 변수를 `-Directory` 생략 `-File` 하거나 `-Attributes` 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-315">To exclude files, use the `-Directory` parameter and omit the `-File` parameter, or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="2db19-316">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="2db19-316">Cmdlets supported</span></span>

- [<span data-ttu-id="2db19-317">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="2db19-317">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="hidden-systemmanagementautomationswitchparameter"></a><span data-ttu-id="2db19-318">Hidden \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="2db19-318">Hidden \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="2db19-319">숨겨진 파일 및 디렉터리(폴더)만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-319">Gets only hidden files and directories (folders).</span></span> <span data-ttu-id="2db19-320">기본적으로 [Get ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) 은 숨겨지지 않은 항목만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-320">By default, [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) gets only non-hidden items.</span></span>

<span data-ttu-id="2db19-321">`-Hidden`매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-321">The `-Hidden` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="2db19-322">숨겨진 항목만 가져오려면 매개 변수 `-Hidden` , 해당 `h` 또는 `ah` 별칭 또는 매개 변수의 **숨겨진** 값을 사용 합니다 `-Attributes` .</span><span class="sxs-lookup"><span data-stu-id="2db19-322">To get only hidden items, use the `-Hidden` parameter, its `h` or `ah` aliases, or the **Hidden** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="2db19-323">숨겨진 항목을 제외 하려면 매개 변수를 생략 `-Hidden` 하거나 `-Attributes` 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-323">To exclude hidden items, omit the `-Hidden` parameter or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="2db19-324">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="2db19-324">Cmdlets supported</span></span>

- [<span data-ttu-id="2db19-325">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="2db19-325">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="readonly-systemmanagementautomationswitchparameter"></a><span data-ttu-id="2db19-326">ReadOnly \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="2db19-326">ReadOnly \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="2db19-327">읽기 전용 파일 및 디렉터리(폴더)만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-327">Gets only read-only files and directories (folders).</span></span>

<span data-ttu-id="2db19-328">`-ReadOnly`매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-328">The `-ReadOnly` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="2db19-329">읽기 전용 항목만 가져오려면 매개 변수의 `-ReadOnly` `ar` 별칭 또는 매개 변수의 **ReadOnly** 값을 사용 `-Attributes` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-329">To get only read-only items, use the `-ReadOnly` parameter, its `ar` alias, or the **ReadOnly** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="2db19-330">읽기 전용 항목을 제외 하려면 `-Attributes` 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-330">To exclude read-only items, use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="2db19-331">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="2db19-331">Cmdlets supported</span></span>

- [<span data-ttu-id="2db19-332">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="2db19-332">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="system-systemmanagementautomationswitchparameter"></a><span data-ttu-id="2db19-333">System \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="2db19-333">System \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="2db19-334">시스템 파일 및 디렉터리(폴더)만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-334">Gets only system files and directories (folders).</span></span>

<span data-ttu-id="2db19-335">`-System`매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-335">The `-System` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="2db19-336">시스템 파일 및 폴더만 가져오려면 매개 변수의 `-System` `as` 별칭 또는 매개 변수의 **시스템** 값을 사용 `-Attributes` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-336">To get only system files and folders, use the `-System` parameter, its `as` alias, or the **System** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="2db19-337">시스템 파일 및 폴더를 제외 하려면 `-Attributes` 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-337">To exclude system files and folders, use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="2db19-338">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="2db19-338">Cmdlets supported</span></span>

- [<span data-ttu-id="2db19-339">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="2db19-339">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="newerthan-systemdatetime"></a><span data-ttu-id="2db19-340">NewerThan \<System.DateTime\></span><span class="sxs-lookup"><span data-stu-id="2db19-340">NewerThan \<System.DateTime\></span></span>

<span data-ttu-id="2db19-341">`$True` `LastWriteTime` 파일의 값이 지정 된 날짜 보다 크면를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-341">Returns `$True` when the `LastWriteTime` value of a file is greater than the specified date.</span></span> <span data-ttu-id="2db19-342">그 외의 경우 `$False`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-342">Otherwise, it returns `$False`.</span></span>

<span data-ttu-id="2db19-343">날짜/시간 개체와 같은 [datetime](/dotnet/api/system.datetime) 개체를 입력 합니다. 예를 들어, 날짜/ [시간](/dotnet/api/system.datetime) 개체 (예: [)](xref:Microsoft.PowerShell.Utility.Get-Date) 로 변환할 수 있는 문자열 `"August 10, 2011 2:00 PM"` 입니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-343">Enter a [DateTime](/dotnet/api/system.datetime) object, such as one that the [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet returns, or a string that can be converted to a [DateTime](/dotnet/api/system.datetime) object, such as `"August 10, 2011 2:00 PM"`.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="2db19-344">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="2db19-344">Cmdlets supported</span></span>

- [<span data-ttu-id="2db19-345">Test-Path</span><span class="sxs-lookup"><span data-stu-id="2db19-345">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="olderthan-systemdatetime"></a><span data-ttu-id="2db19-346">OlderThan \<System.DateTime\></span><span class="sxs-lookup"><span data-stu-id="2db19-346">OlderThan \<System.DateTime\></span></span>

<span data-ttu-id="2db19-347">`$True` `LastWriteTime` 파일의 값이 지정 된 날짜 보다 작은 경우를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-347">Returns `$True` when the `LastWriteTime` value of a file is less than the specified date.</span></span> <span data-ttu-id="2db19-348">그 외의 경우 `$False`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-348">Otherwise, it returns `$False`.</span></span>

<span data-ttu-id="2db19-349">날짜/시간 개체와 같은 [datetime](/dotnet/api/system.datetime) 개체를 입력 합니다. 예를 들어, 날짜/ [시간](/dotnet/api/system.datetime) 개체 (예: [)](xref:Microsoft.PowerShell.Utility.Get-Date) 로 변환할 수 있는 문자열 `"August 10, 2011 2:00 PM"` 입니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-349">Enter a [DateTime](/dotnet/api/system.datetime) object, such as one that the [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet returns, or a string that can be converted to a [DateTime](/dotnet/api/system.datetime) object, such as `"August 10, 2011 2:00 PM"`.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="2db19-350">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="2db19-350">Cmdlets supported</span></span>

- [<span data-ttu-id="2db19-351">Test-Path</span><span class="sxs-lookup"><span data-stu-id="2db19-351">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="stream-systemstring"></a><span data-ttu-id="2db19-352">Stream \<System.String\></span><span class="sxs-lookup"><span data-stu-id="2db19-352">Stream \<System.String\></span></span>

<span data-ttu-id="2db19-353">대체 데이터 스트림을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-353">Manages alternate data streams.</span></span> <span data-ttu-id="2db19-354">스트림 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-354">Enter the stream name.</span></span> <span data-ttu-id="2db19-355">와일드 카드는 파일 시스템 드라이브의 항목 [가져오기](xref:Microsoft.PowerShell.Management.Get-Item) 및 [제거](xref:Microsoft.PowerShell.Management.Remove-Item) 명령에만 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-355">Wildcards are permitted only in [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item) for and [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item) commands in a file system drive.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="2db19-356">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="2db19-356">Cmdlets supported</span></span>

- [<span data-ttu-id="2db19-357">Add-Content</span><span class="sxs-lookup"><span data-stu-id="2db19-357">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="2db19-358">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="2db19-358">Clear-Content</span></span>](xref:Microsoft.PowerShell.Management.Clear-Content)
- [<span data-ttu-id="2db19-359">Get-Item</span><span class="sxs-lookup"><span data-stu-id="2db19-359">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="2db19-360">Get-Content</span><span class="sxs-lookup"><span data-stu-id="2db19-360">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="2db19-361">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="2db19-361">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="2db19-362">Set-Content</span><span class="sxs-lookup"><span data-stu-id="2db19-362">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="raw-switchparameter"></a><span data-ttu-id="2db19-363">Raw \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="2db19-363">Raw \<SwitchParameter\></span></span>

<span data-ttu-id="2db19-364">줄 바꿈 문자를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-364">Ignores newline characters.</span></span> <span data-ttu-id="2db19-365">내용을 단일 항목으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-365">Returns contents as a single item.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="2db19-366">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="2db19-366">Cmdlets supported</span></span>

- [<span data-ttu-id="2db19-367">Get-Content</span><span class="sxs-lookup"><span data-stu-id="2db19-367">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="itemtype-string"></a><span data-ttu-id="2db19-368">ItemType \<String\></span><span class="sxs-lookup"><span data-stu-id="2db19-368">ItemType \<String\></span></span>

<span data-ttu-id="2db19-369">이 매개 변수를 사용 하 여 만들 항목의 tye을 지정할 수 있습니다. `New-Item`</span><span class="sxs-lookup"><span data-stu-id="2db19-369">This parameter allows you to specify the tye of item to create with `New-Item`</span></span>

<span data-ttu-id="2db19-370">이 매개 변수의 사용 가능한 값은 현재 사용 중인 공급자에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-370">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="2db19-371">드라이브에는 `FileSystem` 다음 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-371">In a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="2db19-372">파일</span><span class="sxs-lookup"><span data-stu-id="2db19-372">File</span></span>
- <span data-ttu-id="2db19-373">디렉터리</span><span class="sxs-lookup"><span data-stu-id="2db19-373">Directory</span></span>
- <span data-ttu-id="2db19-374">값인 symboliclink</span><span class="sxs-lookup"><span data-stu-id="2db19-374">SymbolicLink</span></span>
- <span data-ttu-id="2db19-375">분기 동기화</span><span class="sxs-lookup"><span data-stu-id="2db19-375">Junction</span></span>
- <span data-ttu-id="2db19-376">Hardlink create</span><span class="sxs-lookup"><span data-stu-id="2db19-376">HardLink</span></span>

### <a name="cmdlets-supported"></a><span data-ttu-id="2db19-377">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="2db19-377">Cmdlets supported</span></span>

- [<span data-ttu-id="2db19-378">New-Item</span><span class="sxs-lookup"><span data-stu-id="2db19-378">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="2db19-379">파이프라인 사용</span><span class="sxs-lookup"><span data-stu-id="2db19-379">Using the pipeline</span></span>

<span data-ttu-id="2db19-380">공급자 cmdlet은 파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-380">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="2db19-381">파이프라인을 사용 하 여 cmdlet 간에 공급자 데이터를 전송 하 여 작업을 간소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-381">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="2db19-382">공급자 cmdlet에서 파이프라인을 사용 하는 방법에 대 한 자세한 내용은이 문서 전체에서 제공 되는 cmdlet 참조를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2db19-382">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="2db19-383">도움말 보기</span><span class="sxs-lookup"><span data-stu-id="2db19-383">Getting help</span></span>

<span data-ttu-id="2db19-384">Windows PowerShell 3.0부터는 이러한 cmdlet이 파일 시스템 드라이브에서 동작하는 방식을 설명하는 공급자 cmdlet에 대한 사용자 지정된 도움말 항목을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-384">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="2db19-385">파일 시스템 드라이브에 맞게 사용자 지정 된 도움말 항목을 보려면 파일 시스템 드라이브에서 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 명령을 실행 하거나 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 의 매개 변수를 사용 하 여 파일 시스템 드라이브를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2db19-385">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path c:
```

## <a name="see-also"></a><span data-ttu-id="2db19-386">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2db19-386">See also</span></span>

[<span data-ttu-id="2db19-387">about_Providers</span><span class="sxs-lookup"><span data-stu-id="2db19-387">about_Providers</span></span>](../About/about_Providers.md)

