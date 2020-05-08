---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 파일 및 폴더 작업
ms.openlocfilehash: 8876ff70adbd10c9019f6d80ce7ad327f2932c74
ms.sourcegitcommit: 08acbea14c69a347f2f46aafcb215a5233c7d830
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82691497"
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="04a32-103">파일 및 폴더 작업</span><span class="sxs-lookup"><span data-stu-id="04a32-103">Working with Files and Folders</span></span>

<span data-ttu-id="04a32-104">Windows PowerShell 드라이브를 탐색하고 드라이브 항목을 조작하는 것은 Windows의 실제 디스크 드라이브에 있는 파일 및 폴더를 조작하는 것과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="04a32-105">이 섹션에서는 PowerShell을 사용하여 특정 파일 및 폴더 조작 작업을 처리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-105">This section discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

## <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="04a32-106">폴더 내의 모든 파일 및 폴더 표시</span><span class="sxs-lookup"><span data-stu-id="04a32-106">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="04a32-107">`Get-ChildItem`을 사용하여 폴더 바로 아래에 있는 항목을 모두 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-107">You can get all items directly within a folder by using `Get-ChildItem`.</span></span> <span data-ttu-id="04a32-108">선택적 **Force** 매개 변수를 추가하면 숨겨진 항목이나 시스템 항목을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="04a32-109">예를 들어 다음 명령은 Windows의 실제 C 드라이브와 마찬가지로 Windows PowerShell C 드라이브 바로 아래에 있는 내용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="04a32-110">이 명령은 `Cmd.exe`의 `DIR` 명령 또는 UNIX 셸의 `ls`를 사용하는 것과 매우 유사한 방법으로 바로 아래에 포함된 항목만 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-110">The command lists only the directly contained items, much like using `Cmd.exe`'s `DIR` command or `ls` in a UNIX shell.</span></span> <span data-ttu-id="04a32-111">포함된 항목을 모두 보려면 `-Recurse` 매개 변수도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-111">In order to show contained items, you need to specify the `-Recurse` parameter as well.</span></span> <span data-ttu-id="04a32-112">작업을 완료하는 데 시간이 많이 걸릴 수 있습니다. C 드라이브에 있는 모든 항목을 표시하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="04a32-113">`Get-ChildItem`은 **Path**, **Filter**, **Include** 및 **Exclude** 매개 변수로 항목을 필터링할 수 있지만 이러한 변수는 일반적으로 이름을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-113">`Get-ChildItem` can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="04a32-114">`Where-Object`를 사용하여 항목의 다른 속성을 기반으로 복잡한 필터링을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-114">You can perform complex filtering based on other properties of items by using `Where-Object`.</span></span>

<span data-ttu-id="04a32-115">다음 명령은Program Files 폴더 내에서 2005년 10월 1일 이후 마지막으로 수정되었고 1MB보다 작거나 10MB보다 크지 않은 모든 실행 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a><span data-ttu-id="04a32-116">파일 및 폴더 복사</span><span class="sxs-lookup"><span data-stu-id="04a32-116">Copying Files and Folders</span></span>

<span data-ttu-id="04a32-117">`Copy-Item`을 사용하여 복사를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-117">Copying is done with `Copy-Item`.</span></span> <span data-ttu-id="04a32-118">다음 명령은 C:\\boot.ini를 C:\\boot.bak에 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="04a32-119">대상 파일이 이미 있는 경우 복사가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="04a32-120">기존 파일을 덮어쓰려면 다음과 같이 **Force** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-120">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="04a32-121">이 명령은 대상 파일이 읽기 전용인 경우에도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="04a32-122">폴더 복사도 동일한 방식으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-122">Folder copying works the same way.</span></span> <span data-ttu-id="04a32-123">다음 명령은 폴더 `C:\temp\test1`을 새 폴더 `C:\temp\DeleteMe`에 재귀적으로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-123">This command copies the folder `C:\temp\test1` to the new folder `C:\temp\DeleteMe` recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="04a32-124">선택한 항목을 복사할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-124">You can also copy a selection of items.</span></span> <span data-ttu-id="04a32-125">다음 명령은 `C:\data`의 임의 위치에 포함된 모든 .txt 파일을 `C:\temp\text`로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-125">The following command copies all .txt files contained anywhere in `C:\data` to `C:\temp\text`:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="04a32-126">다른 도구를 사용하여 계속 파일 시스템 복사를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="04a32-127">Windows PowerShell에서는 **Scripting.FileSystemObject**와 같은 XCOPY, ROBOCOPY 및 COM 개체를 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="04a32-128">예를 들어 다음과 같이 Windows 스크립트 호스트인 **Scripting.FileSystem COM** 클래스를 사용하여 `C:\boot.ini`를 `C:\boot.bak`에 백업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up `C:\boot.ini` to `C:\boot.bak`:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a><span data-ttu-id="04a32-129">파일 및 폴더 만들기</span><span class="sxs-lookup"><span data-stu-id="04a32-129">Creating Files and Folders</span></span>

<span data-ttu-id="04a32-130">새 항목 만들기는 Windows PowerShell 공급자에서 동일한 방식으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="04a32-131">Windows PowerShell 공급자에 한 가지 이상의 항목 유형이 있는 경우 항목 유형을 지정해야 합니다. 예를 들어 FileSystem Windows PowerShell 공급자는 디렉터리와 파일을 구별합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="04a32-132">다음 명령은 새 폴더 `C:\temp\New Folder`를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-132">This command creates a new folder `C:\temp\New Folder`:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="04a32-133">다음 명령은 새 빈 파일 `C:\temp\New Folder\file.txt`를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-133">This command creates a new empty file `C:\temp\New Folder\file.txt`</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

> [!IMPORTANT]
> <span data-ttu-id="04a32-134">**Force** 스위치를 `New-Item` 명령과 함께 사용하여 폴더를 만들 때 폴더가 이미 있으면 폴더를 덮어쓰거나 바꾸지 _않습니다_.</span><span class="sxs-lookup"><span data-stu-id="04a32-134">When using the **Force** switch with the `New-Item` command to create a folder, and the folder already exists, it _won't_ overwrite or replace the folder.</span></span> <span data-ttu-id="04a32-135">단지 기존 폴더 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-135">It will simply return the existing folder object.</span></span> <span data-ttu-id="04a32-136">그러나 이미 존재하는 파일에 `New-Item -Force`를 사용하는 경우 파일을 완전히 _덮어쓰게 됩니다_.</span><span class="sxs-lookup"><span data-stu-id="04a32-136">However, if you use `New-Item -Force` on a file that already exists, the file _will_ be completely overwritten.</span></span>

## <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="04a32-137">폴더 내의 모든 파일 및 폴더 제거</span><span class="sxs-lookup"><span data-stu-id="04a32-137">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="04a32-138">`Remove-Item`을 사용하여 포함된 항목을 제거할 수 있지만 이 항목에 다른 항목이 들어 있는 경우 제거를 확인하는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-138">You can remove contained items using `Remove-Item`, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="04a32-139">예를 들어 다른 항목이 들어 있는 `C:\temp\DeleteMe`라는 폴더를 삭제하려는 경우 다음과 같이 삭제하기 전에 확인 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-139">For example, if you attempt to delete the folder `C:\temp\DeleteMe` that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the Recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="04a32-140">폴더에 들어 있는 각 항목에 대해 이 메시지가 나타나지 않게 하려면 다음과 같이 **Recurse** 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-140">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-drive"></a><span data-ttu-id="04a32-141">로컬 폴더를 드라이브로 매핑</span><span class="sxs-lookup"><span data-stu-id="04a32-141">Mapping a Local Folder as a drive</span></span>

<span data-ttu-id="04a32-142">`New-PSDrive` 명령을 사용하여 로컬 폴더를 매핑할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-142">You can also map a local folder, using the `New-PSDrive` command.</span></span> <span data-ttu-id="04a32-143">다음 명령은 로컬 Program Files 디렉터리에 있는 로컬 드라이브 `P:`를 만듭니다(PowerShell 세션에서만 표시됨).</span><span class="sxs-lookup"><span data-stu-id="04a32-143">The following command creates a local drive `P:` rooted in the local Program Files directory, visible only from the PowerShell session:</span></span>

```powershell
New-PSDrive -Name P -Root $env:ProgramFiles -PSProvider FileSystem
```

<span data-ttu-id="04a32-144">그러면 네트워크 드라이브와 마찬가지로 Windows PowerShell 내에 매핑된 드라이브가 Windows PowerShell 셸에 즉시 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-144">Just as with network drives, drives mapped within Windows PowerShell are immediately visible to the Windows PowerShell shell.</span></span> <span data-ttu-id="04a32-145">파일 탐색기에서 표시되는 매핑된 드라이브를 만들기 위해서는 매개 변수 `-Persist`가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-145">In order to create a mapped drive visible from File Explorer, the parameter `-Persist` is needed.</span></span> <span data-ttu-id="04a32-146">그러나 원격 경로만 Persist와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-146">However, only remote paths can be used with Persist.</span></span>

## <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="04a32-147">텍스트 파일을 배열로 읽어오기</span><span class="sxs-lookup"><span data-stu-id="04a32-147">Reading a Text File into an Array</span></span>

<span data-ttu-id="04a32-148">일반적으로 텍스트 데이터는 개별 데이터 요소로 취급되는 별도의 줄이 포함된 파일에 스토리지됩니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-148">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="04a32-149">`Get-Content` cmdlet을 사용하여 다음과 같이 한 단계에서 전체 파일을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-149">The `Get-Content` cmdlet can be used to read an entire file in one step, as shown here:</span></span>

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

<span data-ttu-id="04a32-150">`Get-Content`는 파일에서 읽은 데이터를 한 줄에 하나의 요소가 표시된 배열로 취급합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-150">`Get-Content` already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="04a32-151">다음과 같이 반환된 내용의 **Length**를 확인하면 이를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-151">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="04a32-152">이 명령은 정보 목록을 Windows PowerShell로 직접 가져오는 경우 가장 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-152">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="04a32-153">예를 들어 파일의 각 줄에 하나의 이름을 사용하여 컴퓨터 이름 또는 IP 주소 목록을 `C:\temp\domainMembers.txt` 파일에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-153">For example, you might store a list of computer names or IP addresses in a file `C:\temp\domainMembers.txt`, with one name on each line of the file.</span></span> <span data-ttu-id="04a32-154">`Get-Content`를 사용하여 파일 내용을 검색하고 `$Computers` 변수에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-154">You can use `Get-Content` to retrieve the file contents and put them in the variable `$Computers`:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="04a32-155">이제 `$Computers`는 각 요소에 있는 컴퓨터 이름이 포함된 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="04a32-155">`$Computers` is now an array containing a computer name in each element.</span></span>
