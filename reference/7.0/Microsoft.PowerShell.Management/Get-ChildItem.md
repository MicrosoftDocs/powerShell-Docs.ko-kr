---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ChildItem
ms.openlocfilehash: f8a2276b6121958aedc4eb297d0565b369ee401f
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93209810"
---
# <span data-ttu-id="41c9c-103">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="41c9c-103">Get-ChildItem</span></span>

## <span data-ttu-id="41c9c-104">개요</span><span class="sxs-lookup"><span data-stu-id="41c9c-104">SYNOPSIS</span></span>

<span data-ttu-id="41c9c-105">하나 이상의 지정된 위치에서 항목 및 하위 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-105">Gets the items and child items in one or more specified locations.</span></span>

## <span data-ttu-id="41c9c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="41c9c-106">SYNTAX</span></span>

### <span data-ttu-id="41c9c-107">Items (기본값)</span><span class="sxs-lookup"><span data-stu-id="41c9c-107">Items (Default)</span></span>

```
Get-ChildItem [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>]
 [-Recurse] [-Depth <uint32>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>]
 [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### <span data-ttu-id="41c9c-108">LiteralItems</span><span class="sxs-lookup"><span data-stu-id="41c9c-108">LiteralItems</span></span>

```
Get-ChildItem [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>]
 [-Exclude <string[]>] [-Recurse] [-Depth <uint32>] [-Force] [-Name]
 [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden]
 [-ReadOnly] [-System] [<CommonParameters>]
```

## <span data-ttu-id="41c9c-109">설명</span><span class="sxs-lookup"><span data-stu-id="41c9c-109">DESCRIPTION</span></span>

<span data-ttu-id="41c9c-110">`Get-ChildItem`Cmdlet은 하나 이상의 지정 된 위치에 있는 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-110">The `Get-ChildItem` cmdlet gets the items in one or more specified locations.</span></span> <span data-ttu-id="41c9c-111">항목이 컨테이너인 경우 컨테이너 내에 있는 항목(하위 항목)을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-111">If the item is a container, it gets the items inside the container, known as child items.</span></span> <span data-ttu-id="41c9c-112">**재귀** 매개 변수를 사용 하 여 모든 자식 컨테이너의 항목을 가져오고 **Depth** 매개 변수를 사용 하 여 수준 수를 재귀적으로 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-112">You can use the **Recurse** parameter to get items in all child containers and use the **Depth** parameter to limit the number of levels to recurse.</span></span>

<span data-ttu-id="41c9c-113">`Get-ChildItem` 빈 디렉터리를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-113">`Get-ChildItem` doesn't display empty directories.</span></span> <span data-ttu-id="41c9c-114">명령에 `Get-ChildItem` **Depth** 또는 **재귀** 매개 변수가 포함 되어 있으면 빈 디렉터리가 출력에 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-114">When a `Get-ChildItem` command includes the **Depth** or **Recurse** parameters, empty directories aren't included in the output.</span></span>

<span data-ttu-id="41c9c-115">위치는 `Get-ChildItem` PowerShell 공급자가에 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-115">Locations are exposed to `Get-ChildItem` by PowerShell providers.</span></span> <span data-ttu-id="41c9c-116">위치는 파일 시스템 디렉터리, 레지스트리 하이브 또는 인증서 저장소 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-116">A location can be a file system directory, registry hive, or a certificate store.</span></span> <span data-ttu-id="41c9c-117">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41c9c-117">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="41c9c-118">예제</span><span class="sxs-lookup"><span data-stu-id="41c9c-118">EXAMPLES</span></span>

### <span data-ttu-id="41c9c-119">예제 1: 파일 시스템 디렉터리에서 자식 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="41c9c-119">Example 1: Get child items from a file system directory</span></span>

<span data-ttu-id="41c9c-120">이 예제에서는 파일 시스템 디렉터리에서 자식 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-120">This example gets the child items from a file system directory.</span></span> <span data-ttu-id="41c9c-121">파일 이름 및 하위 디렉터리 이름이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-121">The filenames and subdirectory names are displayed.</span></span> <span data-ttu-id="41c9c-122">빈 위치의 경우 명령이 출력을 반환 하지 않고 PowerShell 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-122">For empty locations, the command doesn't return any output and returns to the PowerShell prompt.</span></span>

<span data-ttu-id="41c9c-123">`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여 디렉터리를 지정 합니다 `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="41c9c-123">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test`.</span></span>
<span data-ttu-id="41c9c-124">`Get-ChildItem` PowerShell 콘솔에서 파일 및 디렉터리를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-124">`Get-ChildItem` displays the files and directories in the PowerShell console.</span></span>

```powershell
Get-ChildItem -Path C:\Test
```

```Output
   Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     08:29                Logs
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="41c9c-125">기본적으로 `Get-ChildItem` 는 모드 ( **특성** ), **LastWriteTime** , 파일 크기 ( **길이** ) 및 항목의 **이름을** 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-125">By default `Get-ChildItem` lists the mode ( **Attributes** ), **LastWriteTime** , file size ( **Length** ), and the **Name** of the item.</span></span> <span data-ttu-id="41c9c-126">**Mode** 속성의 문자는 다음과 같이 해석 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-126">The letters in the **Mode** property can be interpreted as follows:</span></span>

- <span data-ttu-id="41c9c-127">`l` 링크나</span><span class="sxs-lookup"><span data-stu-id="41c9c-127">`l` (link)</span></span>
- <span data-ttu-id="41c9c-128">`d` 디렉터리나</span><span class="sxs-lookup"><span data-stu-id="41c9c-128">`d` (directory)</span></span>
- <span data-ttu-id="41c9c-129">`a` 보관</span><span class="sxs-lookup"><span data-stu-id="41c9c-129">`a` (archive)</span></span>
- <span data-ttu-id="41c9c-130">`r` (읽기 전용)</span><span class="sxs-lookup"><span data-stu-id="41c9c-130">`r` (read-only)</span></span>
- <span data-ttu-id="41c9c-131">`h` 은선제거</span><span class="sxs-lookup"><span data-stu-id="41c9c-131">`h` (hidden)</span></span>
- <span data-ttu-id="41c9c-132">`s` (시스템).</span><span class="sxs-lookup"><span data-stu-id="41c9c-132">`s` (system).</span></span>

<span data-ttu-id="41c9c-133">모드 플래그에 대 한 자세한 내용은 [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41c9c-133">For more information about the mode flags, see [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression).</span></span>

### <span data-ttu-id="41c9c-134">예제 2: 디렉터리에서 자식 항목 이름 가져오기</span><span class="sxs-lookup"><span data-stu-id="41c9c-134">Example 2: Get child item names in a directory</span></span>

<span data-ttu-id="41c9c-135">이 예제에서는 디렉터리에 있는 항목의 이름만 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-135">This example lists only the names of items in a directory.</span></span>

<span data-ttu-id="41c9c-136">`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여 디렉터리를 지정 합니다 `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="41c9c-136">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test`.</span></span> <span data-ttu-id="41c9c-137">**Name** 매개 변수는 지정 된 경로에서 파일 또는 디렉터리 이름만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-137">The **Name** parameter returns only the file or directory names from the specified path.</span></span>

```powershell
Get-ChildItem -Path C:\Test -Name
```

```Output
Logs
anotherfile.txt
Command.txt
CreateTestFile.ps1
ReadOnlyFile.txt
```

### <span data-ttu-id="41c9c-138">예제 3: 현재 디렉터리 및 하위 디렉터리의 자식 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="41c9c-138">Example 3: Get child items in the current directory and subdirectories</span></span>

<span data-ttu-id="41c9c-139">이 예제에서는 현재 디렉터리와 해당 하위 디렉터리에 있는 .txt 파일을 표시 **합니다** .</span><span class="sxs-lookup"><span data-stu-id="41c9c-139">This example displays **.txt** files that are located in the current directory and its subdirectories.</span></span>

```powershell
Get-ChildItem -Path C:\Test\*.txt -Recurse -Force
```

```Output
    Directory: C:\Test\Logs\Adirectory

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile4.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile4.txt

    Directory: C:\Test\Logs\Backup

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 ATextFile.txt
-a----        2/12/2019     15:50             20 LogFile3.txt

    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="41c9c-140">`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여를 지정 `C:\Test\*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-140">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify `C:\Test\*.txt`.</span></span> <span data-ttu-id="41c9c-141">**Path** 는 별표 ( `*` ) 와일드 카드를 사용 하 여 파일 이름 확장명을 가진 모든 파일을 지정 `.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-141">**Path** uses the asterisk (`*`) wildcard to specify all files with the filename extension `.txt`.</span></span> <span data-ttu-id="41c9c-142">**재귀** 매개 변수는 **디렉터리:** 제목에 표시 된 것 처럼 **경로** 디렉터리에서 해당 하위 디렉터리를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-142">The **Recurse** parameter searches the **Path** directory its subdirectories, as shown in the **Directory:** headings.</span></span> <span data-ttu-id="41c9c-143">**Force** 매개 변수는 모드가 h 인 등의 숨겨진 파일을 표시 합니다 `hiddenfile.txt` . **h**</span><span class="sxs-lookup"><span data-stu-id="41c9c-143">The **Force** parameter displays hidden files such as `hiddenfile.txt` that have a mode of **h** .</span></span>

### <span data-ttu-id="41c9c-144">예제 4: Include 매개 변수를 사용 하 여 자식 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="41c9c-144">Example 4: Get child items using the Include parameter</span></span>

<span data-ttu-id="41c9c-145">이 예에서는 `Get-ChildItem` **Include** 매개 변수를 사용 하 여 **Path** 매개 변수로 지정 된 디렉터리에서 특정 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-145">In this example `Get-ChildItem` uses the **Include** parameter to find specific items from the directory specified by the **Path** parameter.</span></span>

```powershell
# When using the -Include parameter, if you don't include an asterisk in the path
# the command returns no output.
Get-ChildItem -Path C:\Test\ -Include *.txt
```

```Output

```

```powershell
Get-ChildItem -Path C:\Test\* -Include *.txt
```

```Output
    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="41c9c-146">`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여 **C:\Test** 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-146">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory **C:\Test** .</span></span> <span data-ttu-id="41c9c-147">**Path** 매개 변수에는 `*` 디렉터리의 내용을 지정 하는 후행 별표 () 와일드 카드가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-147">The **Path** parameter includes a trailing asterisk (`*`) wildcard to specify the directory's contents.</span></span>
<span data-ttu-id="41c9c-148">**Include** 매개 변수는 별표 ( `*` ) 와일드 카드를 사용 하 여 파일 확장명이 **.txt** 인 모든 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-148">The **Include** parameter uses an asterisk (`*`) wildcard to specify all files with the file name extension **.txt** .</span></span>

<span data-ttu-id="41c9c-149">**Include** 매개 변수를 사용 하는 경우 **경로** 매개 변수는 후행 별표 ( `*` ) 와일드 카드를 사용 하 여 디렉터리의 내용을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-149">When the **Include** parameter is used, the **Path** parameter needs a trailing asterisk (`*`) wildcard to specify the directory's contents.</span></span> <span data-ttu-id="41c9c-150">예들 들어 `-Path C:\Test\*`입니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-150">For example, `-Path C:\Test\*`.</span></span>

- <span data-ttu-id="41c9c-151">**재귀** 매개 변수를 명령에 추가 하는 경우 `*` **Path** 매개 변수의 후행 별표 ()는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-151">If the **Recurse** parameter is added to the command, the trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="41c9c-152">**재귀** 매개 변수는 **Path** 디렉터리와 해당 하위 디렉터리에서 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-152">The **Recurse** parameter gets items from the **Path** directory and its subdirectories.</span></span> <span data-ttu-id="41c9c-153">예를 들어 `-Path C:\Test\ -Recurse -Include *.txt`</span><span class="sxs-lookup"><span data-stu-id="41c9c-153">For example, `-Path C:\Test\ -Recurse -Include *.txt`</span></span>
- <span data-ttu-id="41c9c-154">후행 별표 ()가 `*` **Path** 매개 변수에 포함 되지 않은 경우 명령이 출력을 반환 하지 않고 PowerShell 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-154">If a trailing asterisk (`*`) isn't included in the **Path** parameter, the command doesn't return any output and returns to the PowerShell prompt.</span></span> <span data-ttu-id="41c9c-155">예들 들어 `-Path C:\Test\`입니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-155">For example, `-Path C:\Test\`.</span></span>

### <span data-ttu-id="41c9c-156">예 5: Exclude 매개 변수를 사용 하 여 자식 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="41c9c-156">Example 5: Get child items using the Exclude parameter</span></span>

<span data-ttu-id="41c9c-157">예제의 출력은 디렉터리 **C:\Test\Logs** 의 내용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-157">The example's output shows the contents of the directory **C:\Test\Logs** .</span></span> <span data-ttu-id="41c9c-158">출력은 **Exclude** 및 **재귀** 매개 변수를 사용 하는 다른 명령에 대 한 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-158">The output is a reference for the other commands that use the **Exclude** and **Recurse** parameters.</span></span>

```powershell
Get-ChildItem -Path C:\Test\Logs
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Adirectory
d-----        2/15/2019     08:28                AnEmptyDirectory
d-----        2/15/2019     13:21                Backup
-a----        2/12/2019     16:16             20 Afile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

```powershell
Get-ChildItem -Path C:\Test\Logs\* -Exclude A*
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Backup
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

<span data-ttu-id="41c9c-159">`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여 디렉터리를 지정 합니다 `C:\Test\Logs` .</span><span class="sxs-lookup"><span data-stu-id="41c9c-159">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test\Logs`.</span></span>
<span data-ttu-id="41c9c-160">**Exclude** 매개 변수는 별표 ( `*` ) 와일드 카드를 사용 하 여 또는로 시작 하는 **A** 파일 또는 **a** 디렉터리를 출력에서 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-160">The **Exclude** parameter uses the asterisk (`*`) wildcard to specify any files or directories that begin with **A** or **a** are excluded from the output.</span></span>

<span data-ttu-id="41c9c-161">**Exclude** 매개 변수를 사용 하는 경우 `*` **Path** 매개 변수의 후행 별표 ()는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-161">When the **Exclude** parameter is used, a trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="41c9c-162">예를 들어 `-Path C:\Test\Logs` 또는 `-Path C:\Test\Logs\*`입니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-162">For example, `-Path C:\Test\Logs` or `-Path C:\Test\Logs\*`.</span></span>

- <span data-ttu-id="41c9c-163">후행 별표 ()가 `*` **path** 매개 변수에 포함 되지 않은 경우 **path** 매개 변수의 내용이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-163">If a trailing asterisk (`*`) isn't included in the **Path** parameter, the contents of the **Path** parameter are displayed.</span></span> <span data-ttu-id="41c9c-164">예외는 **Exclude** 매개 변수의 값과 일치 하는 파일 이름 또는 하위 디렉터리 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-164">The exceptions are filenames or subdirectory names that match the **Exclude** parameter's value.</span></span>
- <span data-ttu-id="41c9c-165">`*` **Path** 매개 변수에 후행 별표 ()가 포함 된 경우이 명령은 **path** 매개 변수의 하위 디렉터리에 루트로 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-165">If a trailing asterisk (`*`) is included in the **Path** parameter, the command recurses into the **Path** parameter's subdirectories.</span></span> <span data-ttu-id="41c9c-166">예외는 **Exclude** 매개 변수의 값과 일치 하는 파일 이름 또는 하위 디렉터리 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-166">The exceptions are filenames or subdirectory names that match the **Exclude** parameter's value.</span></span>
- <span data-ttu-id="41c9c-167">**재귀 매개 변수가** 명령에 추가 되 면 **Path** 매개 변수에 후행 별표 ()가 포함 되어 있는지 여부에 관계 없이 재귀 출력이 동일 합니다 `*` .</span><span class="sxs-lookup"><span data-stu-id="41c9c-167">If the **Recurse** parameter is added to the command, the recursion output is the same whether or not the **Path** parameter includes a trailing asterisk (`*`).</span></span>

### <span data-ttu-id="41c9c-168">예제 6: 레지스트리 하이브에 레지스트리 키 가져오기</span><span class="sxs-lookup"><span data-stu-id="41c9c-168">Example 6: Get the registry keys from a registry hive</span></span>

<span data-ttu-id="41c9c-169">이 예제에서는에서 모든 레지스트리 키를 가져옵니다 `HKEY_LOCAL_MACHINE\HARDWARE` .</span><span class="sxs-lookup"><span data-stu-id="41c9c-169">This example gets all the registry keys from `HKEY_LOCAL_MACHINE\HARDWARE`.</span></span>

<span data-ttu-id="41c9c-170">`Get-ChildItem`**Path** 매개 변수를 사용 하 여 레지스트리 키를 지정 합니다 `HKLM:\HARDWARE` .</span><span class="sxs-lookup"><span data-stu-id="41c9c-170">`Get-ChildItem` uses the **Path** parameter to specify the registry key `HKLM:\HARDWARE`.</span></span> <span data-ttu-id="41c9c-171">레지스트리 키의 hive 경로와 최상위 수준은 PowerShell 콘솔에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-171">The hive's path and top level of registry keys are displayed in the PowerShell console.</span></span>

<span data-ttu-id="41c9c-172">자세한 내용은 [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41c9c-172">For more information, see [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md).</span></span>

```powershell
Get-ChildItem -Path HKLM:\HARDWARE
```

```Output
    Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name             Property
----             --------
ACPI
DESCRIPTION
DEVICEMAP
RESOURCEMAP
UEFI
```

```powershell
Get-ChildItem -Path HKLM:\HARDWARE -Exclude D*
```

```Output
   Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name                           Property
----                           --------
ACPI
RESOURCEMAP
```

<span data-ttu-id="41c9c-173">첫 번째 명령은 레지스트리 키의 내용을 보여 줍니다 `HKLM:\HARDWARE` .</span><span class="sxs-lookup"><span data-stu-id="41c9c-173">The first command shows the contents of the `HKLM:\HARDWARE` registry key.</span></span> <span data-ttu-id="41c9c-174">**Exclude** 매개 변수는 `Get-ChildItem` 로 시작 하는 하위 키를 반환 하지 않도록에 지시 합니다 `D*` .</span><span class="sxs-lookup"><span data-stu-id="41c9c-174">The **Exclude** parameter tells `Get-ChildItem` not to return any subkeys that start with `D*`.</span></span> <span data-ttu-id="41c9c-175">현재 **Exclude** 매개 변수는 항목 속성이 아닌 하위 키 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-175">Currently, the **Exclude** parameter only works on subkeys, not item properties.</span></span>

### <span data-ttu-id="41c9c-176">예 7: 코드 서명 기관을 사용 하 여 모든 인증서 가져오기</span><span class="sxs-lookup"><span data-stu-id="41c9c-176">Example 7: Get all certificates with code-signing authority</span></span>

<span data-ttu-id="41c9c-177">이 예제에서는 코드 서명 기관이 있는 PowerShell **Cert:** 드라이브에 있는 각 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-177">This example gets each certificate in the PowerShell **Cert:** drive that has code-signing authority.</span></span>

<span data-ttu-id="41c9c-178">`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여 **Cert:** provider를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-178">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the **Cert:** provider.</span></span> <span data-ttu-id="41c9c-179">**재귀** 매개 변수는 **경로** 및 해당 하위 디렉터리에 지정 된 디렉터리를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-179">The **Recurse** parameter searches the directory specified by **Path** and its subdirectories.</span></span> <span data-ttu-id="41c9c-180">**Codesigningcert** 매개 변수는 코드 서명 기관이 있는 인증서만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-180">The **CodeSigningCert** parameter gets only certificates that have code-signing authority.</span></span>

```powershell
Get-ChildItem -Path Cert:\* -Recurse -CodeSigningCert
```

<span data-ttu-id="41c9c-181">인증서 공급자 및 Cert: 드라이브에 대 한 자세한 내용은 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41c9c-181">For more information about the Certificate provider and the Cert: drive, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

### <span data-ttu-id="41c9c-182">예 8: Depth 매개 변수를 사용 하 여 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="41c9c-182">Example 8: Get items using the Depth parameter</span></span>

<span data-ttu-id="41c9c-183">이 예제에서는 디렉터리와 해당 하위 디렉터리에 있는 항목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-183">This example displays the items in a directory and its subdirectories.</span></span> <span data-ttu-id="41c9c-184">**Depth** 매개 변수는 재귀에 포함할 하위 디렉터리 수준 수를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-184">The **Depth** parameter determines the number of subdirectory levels to include in the recursion.</span></span> <span data-ttu-id="41c9c-185">빈 디렉터리는 출력에서 제외 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-185">Empty directories are excluded from the output.</span></span>

```powershell
Get-ChildItem -Path C:\Parent -Depth 2
```

```Output
    Directory: C:\Parent

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level1
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level2
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1\SubDir_Level2

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:22                SubDir_Level3
-a----        2/13/2019     08:55             26 file.txt
```

<span data-ttu-id="41c9c-186">`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여 **c:\parent** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-186">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify **C:\Parent** .</span></span> <span data-ttu-id="41c9c-187">**Depth** 매개 변수는 두 개의 재귀 수준을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-187">The **Depth** parameter specifies two levels of recursion.</span></span> <span data-ttu-id="41c9c-188">`Get-ChildItem`**Path** 매개 변수 및 두 개의 하위 디렉터리 수준에 지정 된 디렉터리의 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-188">`Get-ChildItem` displays the contents of the directory specified by the **Path** parameter and the two levels of subdirectories.</span></span>

### <span data-ttu-id="41c9c-189">예 9: 하드 링크 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="41c9c-189">Example 9: Getting hard link information</span></span>

<span data-ttu-id="41c9c-190">PowerShell 6.2에서 하드 링크 정보를 가져오기 위해 대체 뷰가 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-190">In PowerShell 6.2, an alternate view was added to get hard link information.</span></span>

```powershell
Get-ChildItem -Path C:\PathContainingHardLink | Format-Table -View childrenWithHardLink
```

### <span data-ttu-id="41c9c-191">예 9: 실험적 기능 PSUnixFileStat에 대 한 출력</span><span class="sxs-lookup"><span data-stu-id="41c9c-191">Example 9: Output for experimental feature PSUnixFileStat</span></span>

<span data-ttu-id="41c9c-192">Unix 시스템의 PowerShell 7에서 실험적 기능 **PSUnixFileStat** 는 unix와 비슷한 출력을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-192">In PowerShell 7 on Unix systems, the experimental feature **PSUnixFileStat** provides Unix-like output:</span></span>

```powershell
PS> Get-ChildItem /etc/r*
```

```Output
    Directory: /etc

UnixMode   User Group    LastWriteTime Size Name
--------   ---- -----    ------------- ---- ----
drwxr-xr-x root wheel  9/30/2019 19:19  128 racoon
-rw-r--r-- root wheel  9/26/2019 18:20 1560 rc.common
-rw-r--r-- root wheel  7/31/2017 17:30 1560 rc.common~previous
-rw-r--r-- root wheel  9/27/2019 20:34 5264 rc.netboot
lrwxr-xr-x root wheel  11/8/2019 15:35   22 resolv.conf -> /private/var/run/resolv.conf
-rw-r--r-- root wheel 10/23/2019 17:41    0 rmtab
-rw-r--r-- root wheel 10/23/2019 17:41 1735 rpc
-rw-r--r-- root wheel  7/25/2017 18:37 1735 rpc~previous
-rw-r--r-- root wheel 10/23/2019 18:42  891 rtadvd.conf
-rw-r--r-- root wheel  8/24/2017 21:54  891 rtadvd.conf~previous
```

<span data-ttu-id="41c9c-193">이제 출력의 일부인 새 속성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-193">The new properties that are now part of the output are:</span></span>

- <span data-ttu-id="41c9c-194">모든 수 **x 모드** 는 Unix 시스템에 표시 되는 파일 사용 권한입니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-194">**UnixMode** is the file permissions as represented on a Unix system</span></span>
- <span data-ttu-id="41c9c-195">**사용자** 가 파일 소유자입니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-195">**User** is the file owner</span></span>
- <span data-ttu-id="41c9c-196">**그룹이 그룹 소유자입니다.**</span><span class="sxs-lookup"><span data-stu-id="41c9c-196">**Group** is the group owner</span></span>
- <span data-ttu-id="41c9c-197">**크기** 는 Unix 시스템에 표시 되는 파일 또는 디렉터리의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-197">**Size** is the size of the file or directory as represented on a Unix system</span></span>

## <span data-ttu-id="41c9c-198">매개 변수</span><span class="sxs-lookup"><span data-stu-id="41c9c-198">Parameters</span></span>

### <span data-ttu-id="41c9c-199">-특성</span><span class="sxs-lookup"><span data-stu-id="41c9c-199">-Attributes</span></span>

<span data-ttu-id="41c9c-200">지정된 특성을 갖는 파일 및 폴더를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-200">Gets files and folders with the specified attributes.</span></span> <span data-ttu-id="41c9c-201">이 매개 변수는 모든 특성을 지원하며 복잡한 특성 조합을 지정할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-201">This parameter supports all attributes and lets you specify complex combinations of attributes.</span></span>

<span data-ttu-id="41c9c-202">예를 들어 암호화되거나 압축된 비시스템 파일(디렉터리 아님)을 가져오려면 다음과 같이 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="41c9c-202">For example, to get non-system files (not directories) that are encrypted or compressed, type:</span></span>

`Get-ChildItem -Attributes !Directory+!System+Encrypted, !Directory+!System+Compressed`

<span data-ttu-id="41c9c-203">일반적으로 사용 되는 특성이 있는 파일 및 폴더를 찾으려면 **attributes** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-203">To find files and folders with commonly used attributes, use the **Attributes** parameter.</span></span> <span data-ttu-id="41c9c-204">또는 매개 변수 **디렉터리** , **파일** , **숨김** , **읽기 전용** 및 **시스템** 입니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-204">Or, the parameters **Directory** , **File** , **Hidden** , **ReadOnly** , and **System** .</span></span>

<span data-ttu-id="41c9c-205">**Attributes** 매개 변수는 다음 속성을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-205">The **Attributes** parameter supports the following properties:</span></span>

- <span data-ttu-id="41c9c-206">**보관**</span><span class="sxs-lookup"><span data-stu-id="41c9c-206">**Archive**</span></span>
- <span data-ttu-id="41c9c-207">**Compressed**</span><span class="sxs-lookup"><span data-stu-id="41c9c-207">**Compressed**</span></span>
- <span data-ttu-id="41c9c-208">**디바이스**</span><span class="sxs-lookup"><span data-stu-id="41c9c-208">**Device**</span></span>
- <span data-ttu-id="41c9c-209">**디렉터리**</span><span class="sxs-lookup"><span data-stu-id="41c9c-209">**Directory**</span></span>
- <span data-ttu-id="41c9c-210">**암호화됨**</span><span class="sxs-lookup"><span data-stu-id="41c9c-210">**Encrypted**</span></span>
- <span data-ttu-id="41c9c-211">**숨김**</span><span class="sxs-lookup"><span data-stu-id="41c9c-211">**Hidden**</span></span>
- <span data-ttu-id="41c9c-212">**및 Itystream**</span><span class="sxs-lookup"><span data-stu-id="41c9c-212">**IntegrityStream**</span></span>
- <span data-ttu-id="41c9c-213">**보통**</span><span class="sxs-lookup"><span data-stu-id="41c9c-213">**Normal**</span></span>
- <span data-ttu-id="41c9c-214">**NoScrubData**</span><span class="sxs-lookup"><span data-stu-id="41c9c-214">**NoScrubData**</span></span>
- <span data-ttu-id="41c9c-215">**NotContentIndexed**</span><span class="sxs-lookup"><span data-stu-id="41c9c-215">**NotContentIndexed**</span></span>
- <span data-ttu-id="41c9c-216">**라인인**</span><span class="sxs-lookup"><span data-stu-id="41c9c-216">**Offline**</span></span>
- <span data-ttu-id="41c9c-217">**읽기 전용**</span><span class="sxs-lookup"><span data-stu-id="41c9c-217">**ReadOnly**</span></span>
- <span data-ttu-id="41c9c-218">**ReparsePoint**</span><span class="sxs-lookup"><span data-stu-id="41c9c-218">**ReparsePoint**</span></span>
- <span data-ttu-id="41c9c-219">**SparseFile**</span><span class="sxs-lookup"><span data-stu-id="41c9c-219">**SparseFile**</span></span>
- <span data-ttu-id="41c9c-220">**시스템**</span><span class="sxs-lookup"><span data-stu-id="41c9c-220">**System**</span></span>
- <span data-ttu-id="41c9c-221">**임시**</span><span class="sxs-lookup"><span data-stu-id="41c9c-221">**Temporary**</span></span>

<span data-ttu-id="41c9c-222">이러한 특성에 대 한 설명은 [Fileattributes 열거](/dotnet/api/system.io.fileattributes)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41c9c-222">For a description of these attributes, see the [FileAttributes Enumeration](/dotnet/api/system.io.fileattributes).</span></span>

<span data-ttu-id="41c9c-223">특성을 결합 하려면 다음 연산자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-223">To combine attributes, use the following operators:</span></span>

- <span data-ttu-id="41c9c-224">`!` 나타내지</span><span class="sxs-lookup"><span data-stu-id="41c9c-224">`!` (NOT)</span></span>
- <span data-ttu-id="41c9c-225">`+` 하거나</span><span class="sxs-lookup"><span data-stu-id="41c9c-225">`+` (AND)</span></span>
- <span data-ttu-id="41c9c-226">`,` 디스크나</span><span class="sxs-lookup"><span data-stu-id="41c9c-226">`,` (OR)</span></span>

<span data-ttu-id="41c9c-227">연산자와 해당 특성 사이에 공백을 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="41c9c-227">Don't use spaces between an operator and its attribute.</span></span> <span data-ttu-id="41c9c-228">쉼표 뒤에 공백이 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-228">Spaces are accepted after commas.</span></span>

<span data-ttu-id="41c9c-229">공통 특성의 경우 다음 약어를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-229">For common attributes, use the following abbreviations:</span></span>

- <span data-ttu-id="41c9c-230">`D` 디렉터리나</span><span class="sxs-lookup"><span data-stu-id="41c9c-230">`D` (Directory)</span></span>
- <span data-ttu-id="41c9c-231">`H` 은선제거</span><span class="sxs-lookup"><span data-stu-id="41c9c-231">`H` (Hidden)</span></span>
- <span data-ttu-id="41c9c-232">`R` (읽기 전용)</span><span class="sxs-lookup"><span data-stu-id="41c9c-232">`R` (Read-only)</span></span>
- <span data-ttu-id="41c9c-233">`S` 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="41c9c-233">`S` (System)</span></span>

```yaml
Type: System.Management.Automation.FlagsExpression`1[System.IO.FileAttributes]
Parameter Sets: (All)
Aliases:
Accepted values: Archive, Compressed, Device, Directory, Encrypted, Hidden, IntegrityStream, Normal, NoScrubData, NotContentIndexed, Offline, ReadOnly, ReparsePoint, SparseFile, System, Temporary

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41c9c-234">-깊이</span><span class="sxs-lookup"><span data-stu-id="41c9c-234">-Depth</span></span>

<span data-ttu-id="41c9c-235">이 매개 변수는 PowerShell 5.0에 추가 되었으며 재귀의 깊이를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-235">This parameter was added in PowerShell 5.0 and enables you to control the depth of recursion.</span></span> <span data-ttu-id="41c9c-236">기본적으로는 `Get-ChildItem` 부모 디렉터리의 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-236">By default, `Get-ChildItem` displays the contents of the parent directory.</span></span> <span data-ttu-id="41c9c-237">**Depth** 매개 변수는 재귀에 포함 된 하위 디렉터리 수준 수를 결정 하 고 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-237">The **Depth** parameter determines the number of subdirectory levels that are included in the recursion and displays the contents.</span></span>

<span data-ttu-id="41c9c-238">예를 들어에는 `Depth 2` **Path** 매개 변수의 디렉터리, 첫 번째 수준의 하위 디렉터리 및 하위 디렉터리의 두 번째 수준이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-238">For example, `Depth 2` includes the **Path** parameter's directory, first level of subdirectories, and second level of subdirectories.</span></span> <span data-ttu-id="41c9c-239">기본적으로 디렉터리 이름과 파일 이름은 출력에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-239">By default directory names and filenames are included in the output.</span></span>

> [!NOTE]
> <span data-ttu-id="41c9c-240">PowerShell 또는 **cmd.exe** 의 Windows 컴퓨터에서 **tree.com** 명령을 사용 하 여 디렉터리 구조에 대 한 그래픽 보기를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-240">On a Windows computer from PowerShell or **cmd.exe** , you can display a graphical view of a directory structure with the **tree.com** command.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41c9c-241">-Directory</span><span class="sxs-lookup"><span data-stu-id="41c9c-241">-Directory</span></span>

<span data-ttu-id="41c9c-242">디렉터리 목록을 가져오려면 **directory 매개 변수를 사용** 하거나 **Directory** 속성에 **Attributes** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-242">To get a list of directories, use the **Directory** parameter or the **Attributes** parameter with the **Directory** property.</span></span> <span data-ttu-id="41c9c-243">**디렉터리** 에는 **재귀** 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-243">You can use the **Recurse** parameter with **Directory** .</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ad, d

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41c9c-244">-제외</span><span class="sxs-lookup"><span data-stu-id="41c9c-244">-Exclude</span></span>

<span data-ttu-id="41c9c-245">이 cmdlet이 작업에서 제외 하는 속성 또는 속성을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-245">Specifies, as a string array, a property or property that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="41c9c-246">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-246">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="41c9c-247">경로 요소 또는 패턴 (예: 또는)을 입력 `*.txt` `A*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-247">Enter a path element or pattern, such as `*.txt` or `A*`.</span></span> <span data-ttu-id="41c9c-248">와일드카드 문자가 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-248">Wildcard characters are accepted.</span></span>

<span data-ttu-id="41c9c-249">`*` **Path** 매개 변수의 후행 별표 ()는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-249">A trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="41c9c-250">예를 들어 `-Path C:\Test\Logs` 또는 `-Path C:\Test\Logs\*`입니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-250">For example, `-Path C:\Test\Logs` or `-Path C:\Test\Logs\*`.</span></span> <span data-ttu-id="41c9c-251">후행 별표 ( `*` )가 포함 된 경우 명령은 **Path** 매개 변수의 하위 디렉터리에 루트로.</span><span class="sxs-lookup"><span data-stu-id="41c9c-251">If a trailing asterisk (`*`) is included, the command recurses into the **Path** parameter's subdirectories.</span></span> <span data-ttu-id="41c9c-252">별표 ()를 사용 하지 않으면 `*` **Path** 매개 변수의 콘텐츠가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-252">Without the asterisk (`*`), the contents of the **Path** parameter are displayed.</span></span> <span data-ttu-id="41c9c-253">자세한 내용은 예 5 및 메모 섹션에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-253">More details are included in Example 5 and the Notes section.</span></span>

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

### <span data-ttu-id="41c9c-254">-File</span><span class="sxs-lookup"><span data-stu-id="41c9c-254">-File</span></span>

<span data-ttu-id="41c9c-255">파일 목록을 가져오려면 **File** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-255">To get a list of files, use the **File** parameter.</span></span> <span data-ttu-id="41c9c-256">**파일** 에는 **재귀** 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-256">You can use the **Recurse** parameter with **File** .</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: af

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41c9c-257">-Filter</span><span class="sxs-lookup"><span data-stu-id="41c9c-257">-Filter</span></span>

<span data-ttu-id="41c9c-258">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-258">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="41c9c-259">[파일 시스템](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터를 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-259">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="41c9c-260">필터는 다른 매개 변수 보다 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-260">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="41c9c-261">공급자는 검색 된 개체를 PowerShell에서 필터링 하는 대신 개체를 가져올 때 필터를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-261">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="41c9c-262">필터 문자열은 파일을 열거 하기 위해 .NET API에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-262">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="41c9c-263">API는 `*` 및 `?` 와일드 카드만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-263">The API only supports `*` and `?` wildcards.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="41c9c-264">-FollowSymlink</span><span class="sxs-lookup"><span data-stu-id="41c9c-264">-FollowSymlink</span></span>

<span data-ttu-id="41c9c-265">기본적으로 cmdlet은 `Get-ChildItem` 재귀 중에 발견 된 디렉터리에 대 한 기호화 된 링크를 표시 하지만 재귀는 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-265">By default, the `Get-ChildItem` cmdlet displays symbolic links to directories found during recursion, but doesn't recurse into them.</span></span> <span data-ttu-id="41c9c-266">**FollowSymlink** 매개 변수를 사용 하 여 해당 기호화 된 링크를 대상으로 하는 디렉터리를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-266">Use the **FollowSymlink** parameter to search the directories that target those symbolic links.</span></span> <span data-ttu-id="41c9c-267">**FollowSymlink** 는 동적 매개 변수 이며 **FileSystem** 공급자 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-267">The **FollowSymlink** is a dynamic parameter and is supported only in the **FileSystem** provider.</span></span>

<span data-ttu-id="41c9c-268">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-268">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="41c9c-269">-Force</span><span class="sxs-lookup"><span data-stu-id="41c9c-269">-Force</span></span>

<span data-ttu-id="41c9c-270">사용자가 숨겨진 또는 시스템 파일과 같이 다른 방법으로는 액세스할 수 없는 항목을 cmdlet에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-270">Allows the cmdlet to get items that otherwise can't be accessed by the user, such as hidden or system files.</span></span> <span data-ttu-id="41c9c-271">**Force** 매개 변수는 보안 제한을 재정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-271">The **Force** parameter doesn't override security restrictions.</span></span> <span data-ttu-id="41c9c-272">구현은 공급자 간에 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-272">Implementation varies among providers.</span></span> <span data-ttu-id="41c9c-273">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41c9c-273">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="41c9c-274">-Hidden</span><span class="sxs-lookup"><span data-stu-id="41c9c-274">-Hidden</span></span>

<span data-ttu-id="41c9c-275">**숨겨진 항목만** **가져오려면 hidden 속성** 을 사용 하 여 Hidden 매개 변수 또는 **Attributes** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-275">To get only hidden items, use the **Hidden** parameter or the **Attributes** parameter with the **Hidden** property.</span></span> <span data-ttu-id="41c9c-276">기본적으로는 `Get-ChildItem` 숨겨진 항목을 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-276">By default, `Get-ChildItem` doesn't display hidden items.</span></span> <span data-ttu-id="41c9c-277">**Force** 매개 변수를 사용 하 여 숨겨진 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-277">Use the **Force** parameter to get hidden items.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ah, h

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41c9c-278">-포함</span><span class="sxs-lookup"><span data-stu-id="41c9c-278">-Include</span></span>

<span data-ttu-id="41c9c-279">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-279">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="41c9c-280">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-280">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="41c9c-281">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-281">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="41c9c-282">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-282">Wildcard characters are permitted.</span></span> <span data-ttu-id="41c9c-283">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="41c9c-283">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="41c9c-284">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="41c9c-284">-LiteralPath</span></span>

<span data-ttu-id="41c9c-285">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-285">Specifies a path to one or more locations.</span></span> <span data-ttu-id="41c9c-286">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-286">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="41c9c-287">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-287">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="41c9c-288">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="41c9c-288">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="41c9c-289">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-289">Single quotation marks tell PowerShell to not interpret any characters as escape sequences.</span></span>

<span data-ttu-id="41c9c-290">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41c9c-290">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralItems
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="41c9c-291">-Name</span><span class="sxs-lookup"><span data-stu-id="41c9c-291">-Name</span></span>

<span data-ttu-id="41c9c-292">위치의 항목 이름만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-292">Gets only the names of the items in the location.</span></span> <span data-ttu-id="41c9c-293">출력은 파이프라인에서 다른 명령으로 전송할 수 있는 문자열 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-293">The output is a string object that can be sent down the pipeline to other commands.</span></span> <span data-ttu-id="41c9c-294">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-294">Wildcards are permitted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="41c9c-295">-Path</span><span class="sxs-lookup"><span data-stu-id="41c9c-295">-Path</span></span>

<span data-ttu-id="41c9c-296">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-296">Specifies a path to one or more locations.</span></span> <span data-ttu-id="41c9c-297">와일드 카드가 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-297">Wildcards are accepted.</span></span> <span data-ttu-id="41c9c-298">기본 위치는 현재 디렉터리 ()입니다 `.` .</span><span class="sxs-lookup"><span data-stu-id="41c9c-298">The default location is the current directory (`.`).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Items
Aliases:

Required: False
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="41c9c-299">-ReadOnly</span><span class="sxs-lookup"><span data-stu-id="41c9c-299">-ReadOnly</span></span>

<span data-ttu-id="41c9c-300">읽기 전용 항목만 가져오려면 **readonly** 매개 변수 또는 **Attributes** 매개 변수 **readonly** 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-300">To get only read-only items, use the **ReadOnly** parameter or the **Attributes** parameter **ReadOnly** property.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ar

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41c9c-301">-재귀</span><span class="sxs-lookup"><span data-stu-id="41c9c-301">-Recurse</span></span>

<span data-ttu-id="41c9c-302">지정된 위치와 해당 위치의 모든 하위 항목에서 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-302">Gets the items in the specified locations and in all child items of the locations.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: s

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41c9c-303">-System</span><span class="sxs-lookup"><span data-stu-id="41c9c-303">-System</span></span>

<span data-ttu-id="41c9c-304">시스템 파일 및 디렉터리만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-304">Gets only system files and directories.</span></span> <span data-ttu-id="41c9c-305">시스템 파일 및 폴더만 가져오려면 **system** 매개 변수 또는 **Attributes** 매개 변수 **시스템** 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-305">To get only system files and folders, use the **System** parameter or **Attributes** parameter **System** property.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: as

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41c9c-306">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="41c9c-306">CommonParameters</span></span>

<span data-ttu-id="41c9c-307">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="41c9c-307">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="41c9c-308">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41c9c-308">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="41c9c-309">입력</span><span class="sxs-lookup"><span data-stu-id="41c9c-309">INPUTS</span></span>

### <span data-ttu-id="41c9c-310">System.String</span><span class="sxs-lookup"><span data-stu-id="41c9c-310">System.String</span></span>

<span data-ttu-id="41c9c-311">경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="41c9c-311">You can pipe a string that contains a path to `Get-ChildItem`.</span></span>

## <span data-ttu-id="41c9c-312">출력</span><span class="sxs-lookup"><span data-stu-id="41c9c-312">OUTPUTS</span></span>

### <span data-ttu-id="41c9c-313">System.Object</span><span class="sxs-lookup"><span data-stu-id="41c9c-313">System.Object</span></span>

<span data-ttu-id="41c9c-314">을 반환 하는 개체의 형식은 `Get-ChildItem` 공급자 드라이브 경로의 개체에 의해 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-314">The type of object that `Get-ChildItem` returns is determined by the objects in the provider drive path.</span></span>

### <span data-ttu-id="41c9c-315">System.String</span><span class="sxs-lookup"><span data-stu-id="41c9c-315">System.String</span></span>

<span data-ttu-id="41c9c-316">**Name** 매개 변수를 사용 하는 경우는 `Get-ChildItem` 개체 이름을 문자열로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-316">If you use the **Name** parameter, `Get-ChildItem` returns the object names as strings.</span></span>

## <span data-ttu-id="41c9c-317">참고</span><span class="sxs-lookup"><span data-stu-id="41c9c-317">NOTES</span></span>

- <span data-ttu-id="41c9c-318">`Get-ChildItem` 는 기본 제공 별칭,, 및 중 하나를 사용 하 여 실행할 수 있습니다 `ls` `dir` `gci` .</span><span class="sxs-lookup"><span data-stu-id="41c9c-318">`Get-ChildItem` can be run using any of the built-in aliases, `ls`, `dir`, and `gci`.</span></span> <span data-ttu-id="41c9c-319">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41c9c-319">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="41c9c-320">`Get-ChildItem` 숨겨진 항목은 기본적으로 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-320">`Get-ChildItem` doesn't get hidden items by default.</span></span> <span data-ttu-id="41c9c-321">숨겨진 항목을 가져오려면 **Force** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-321">To get hidden items, use the **Force** parameter.</span></span>
- <span data-ttu-id="41c9c-322">`Get-ChildItem`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-322">The `Get-ChildItem` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="41c9c-323">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41c9c-323">To list the providers available in your session, type `Get-PSProvider`.</span></span>
  <span data-ttu-id="41c9c-324">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41c9c-324">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="41c9c-325">관련 링크</span><span class="sxs-lookup"><span data-stu-id="41c9c-325">RELATED LINKS</span></span>

[<span data-ttu-id="41c9c-326">about_Certificate_Provider</span><span class="sxs-lookup"><span data-stu-id="41c9c-326">about_Certificate_Provider</span></span>](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)

[<span data-ttu-id="41c9c-327">about_Providers</span><span class="sxs-lookup"><span data-stu-id="41c9c-327">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="41c9c-328">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="41c9c-328">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="41c9c-329">about_Registry_Provider</span><span class="sxs-lookup"><span data-stu-id="41c9c-329">about_Registry_Provider</span></span>](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)

[<span data-ttu-id="41c9c-330">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="41c9c-330">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="41c9c-331">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="41c9c-331">Get-Alias</span></span>](../Microsoft.PowerShell.Utility/Get-Alias.md)

[<span data-ttu-id="41c9c-332">Get-Item</span><span class="sxs-lookup"><span data-stu-id="41c9c-332">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="41c9c-333">Get-Location</span><span class="sxs-lookup"><span data-stu-id="41c9c-333">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="41c9c-334">Get-Process</span><span class="sxs-lookup"><span data-stu-id="41c9c-334">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="41c9c-335">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="41c9c-335">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="41c9c-336">Split-Path</span><span class="sxs-lookup"><span data-stu-id="41c9c-336">Split-Path</span></span>](Split-Path.md)
