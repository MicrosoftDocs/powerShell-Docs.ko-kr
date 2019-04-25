---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 직접 항목 조작
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: 4caa7d2e0eecff9783556062d8503fe10e616fe5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086224"
---
# <a name="manipulating-items-directly"></a><span data-ttu-id="8ec02-103">직접 항목 조작</span><span class="sxs-lookup"><span data-stu-id="8ec02-103">Manipulating Items Directly</span></span>

<span data-ttu-id="8ec02-104">Windows PowerShell 드라이브에 표시되는 요소(예: 파일 시스템 드라이브의 파일 및 폴더, Windows PowerShell 레지스트리 드라이브의 레지스트리 키)를 Windows PowerShell에서는 *항목*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-104">The elements that you see in Windows PowerShell drives, such as the files and folders in the file system drives, and the registry keys in the Windows PowerShell registry drives, are called *items* in Windows PowerShell.</span></span> <span data-ttu-id="8ec02-105">이러한 항목 작업을 위한 cmdlet은 이름에 명사 **Item**이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-105">The cmdlets for working with them item have the noun **Item** in their names.</span></span>

<span data-ttu-id="8ec02-106">**Get-Command -Noun Item** 명령의 출력에는 9개의 Windows PowerShell 항목 cmdlet이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-106">The output of the **Get-Command -Noun Item** command shows that there are nine Windows PowerShell item cmdlets.</span></span>

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

## <a name="creating-new-items-new-item"></a><span data-ttu-id="8ec02-107">새 항목 만들기(New-Item)</span><span class="sxs-lookup"><span data-stu-id="8ec02-107">Creating New Items (New-Item)</span></span>

<span data-ttu-id="8ec02-108">파일 시스템에서 새 항목을 만들려면 **New-Item** cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-108">To create a new item in the file system, use the **New-Item** cmdlet.</span></span> <span data-ttu-id="8ec02-109">항목 경로에 **Path** 매개 변수를 포함하고, 값이 "file" 또는 "directory"인 **ItemType** 매개 변수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-109">Include the **Path** parameter with path to the item, and the **ItemType** parameter with a value of "file" or "directory".</span></span>

<span data-ttu-id="8ec02-110">예를 들어 C:\\Temp 디렉터리에서 "New.Directory"라는 새 디렉터리를 만들려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-110">For example, to create a new directory named "New.Directory"in the C:\\Temp directory,  type:</span></span>

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

<span data-ttu-id="8ec02-111">파일을 만들려면 **ItemType** 매개 변수의 값을 "file"로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-111">To create a file, change the value of the **ItemType** parameter to "file".</span></span> <span data-ttu-id="8ec02-112">예를 들어 New.Directory 디렉터리에서 "file1.txt" 파일을 만들려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-112">For example, to create a file named "file1.txt" in the New.Directory directory, type:</span></span>

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

<span data-ttu-id="8ec02-113">동일한 기술을 사용하여 새 레지스트리 키를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-113">You can use the same technique to create a new registry key.</span></span> <span data-ttu-id="8ec02-114">Windows 레지스트리에 있는 항목 유형만 키이므로 레지스트리 키는 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-114">In fact, a registry key is easier to create because the only item type in the Windows registry is a key.</span></span> <span data-ttu-id="8ec02-115">레지스트리 항목은 *properties* 항목입니다. 예를 들어 CurrentVersion 하위 키에서 "_Test" 키를 만들려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-115">(Registry entries are item *properties*.) For example, to create a key named "_Test" in the CurrentVersion subkey, type:</span></span>

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

<span data-ttu-id="8ec02-116">레지스트리 경로를 입력할 때 Windows PowerShell 드라이브 이름에 콜론(**:**)을 포함해야 합니다(예: HKLM: 및 HKCU:).</span><span class="sxs-lookup"><span data-stu-id="8ec02-116">When typing a registry path, be sure to include the colon (**:**) in the Windows PowerShell drive names, HKLM: and HKCU:.</span></span> <span data-ttu-id="8ec02-117">콜론이 없을 경우 Windows PowerShell에서는 경로의 드라이브 이름을 인식하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-117">Without the colon, Windows PowerShell does not recognize the drive name in the path.</span></span>

## <a name="why-registry-values-are-not-items"></a><span data-ttu-id="8ec02-118">레지스트리 값이 항목이 아닌 이유</span><span class="sxs-lookup"><span data-stu-id="8ec02-118">Why Registry Values are not Items</span></span>

<span data-ttu-id="8ec02-119">**Get-ChildItem** cmdlet을 사용하여 레지스트리 키에서 항목을 찾을 경우 실제 레지스트리 항목 또는 값이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-119">When you use the **Get-ChildItem** cmdlet to find the items in a registry key, you will never see actual registry entries or their values.</span></span>

<span data-ttu-id="8ec02-120">예를 들어 **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** 레지스트리 키에는 일반적으로 시스템을 시작할 때 실행되는 애플리케이션을 나타내는 여러 레지스트리 항목이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-120">For example, the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** usually contains several registry entries that represent applications that run when the system starts.</span></span>

<span data-ttu-id="8ec02-121">하지만 **Get-ChildItem**을 사용하여 키의 하위 항목을 찾을 경우 키의 **OptionalComponents** 하위 키만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-121">However, when you use **Get-ChildItem** to look for child items in the key, all you will see is the **OptionalComponents** subkey of the key:</span></span>

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

<span data-ttu-id="8ec02-122">레지스트리 항목을 항목으로 처리하면 편리하지만 레지스트리 항목의 경로를 고유하게 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-122">Although it would be convenient to treat registry entries as items, you cannot specify a path to a registry entry in a way that ensures that it is unique.</span></span> <span data-ttu-id="8ec02-123">**Run** 레지스트리 하위 키와 **Run** 하위 키의 **(Default)** 레지스트리 항목 간에 경로 표기법이 구분되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-123">The path notation does not distinguish between the registry subkey named **Run** and the **(Default)** registry entry in the **Run** subkey.</span></span> <span data-ttu-id="8ec02-124">또한 레지스트리 항목 이름에 백슬래시(**\\**) 문자를 사용할 수 있으므로, 레지스트리 항목이 항목인 경우 경로 표기법을 사용하여 **Windows\\CurrentVersion\\Run** 레지스트리 항목을 해당 경로에 있는 하위 키와 구분할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-124">Furthermore, because registry entry names can contain the backslash character (**\\**), if registry entries were items, then you could not use the path notation to distinguish a registry entry named **Windows\\CurrentVersion\\Run** from the subkey that is located in that path.</span></span>

## <a name="renaming-existing-items-rename-item"></a><span data-ttu-id="8ec02-125">기존 항목 이름 바꾸기(Rename-Item)</span><span class="sxs-lookup"><span data-stu-id="8ec02-125">Renaming Existing Items (Rename-Item)</span></span>

<span data-ttu-id="8ec02-126">파일 또는 폴더의 이름을 변경하려면 **Rename-Item** cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-126">To change the name of a file or folder, use the **Rename-Item** cmdlet.</span></span> <span data-ttu-id="8ec02-127">다음 명령은 **file1.txt** 파일의 이름을 **fileOne.txt**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-127">The following command changes the name of the **file1.txt** file to **fileOne.txt**.</span></span>

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

<span data-ttu-id="8ec02-128">**Rename-Item** cmdlet은 파일 또는 폴더의 이름을 변경할 수 있지만 항목을 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-128">The **Rename-Item** cmdlet can change the name of a file or a folder, but it cannot move an item.</span></span> <span data-ttu-id="8ec02-129">다음 명령은 파일을 New.Directory 디렉터리에서 Temp 디렉터리로 이동하므로 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-129">The following command fails because it attempts to move the file from the New.Directory directory to the Temp directory.</span></span>

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a><span data-ttu-id="8ec02-130">항목 이동(Move-Item)</span><span class="sxs-lookup"><span data-stu-id="8ec02-130">Moving Items (Move-Item)</span></span>

<span data-ttu-id="8ec02-131">파일 또는 폴더를 이동하려면 **Move-Item** cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-131">To move a file or folder, use the **Move-Item** cmdlet.</span></span>

<span data-ttu-id="8ec02-132">예를 들어 다음 명령은 New.Directory 디렉터리를 C:\\temp 디렉터리에서 C: 드라이브의 루트로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-132">For example, the following command moves the New.Directory directory from the C:\\temp directory to the root of the C: drive.</span></span> <span data-ttu-id="8ec02-133">항목이 이동되었는지 확인하려면 **Move-Item** cmdlet의 **PassThru** 매개 변수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-133">To verify that the item was moved, include the **PassThru** parameter of the **Move-Item** cmdlet.</span></span> <span data-ttu-id="8ec02-134">**Passthru**가 없을 경우 **Move-Item** cmdlet은 결과를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-134">Without **Passthru**, the **Move-Item** cmdlet does not display any results.</span></span>

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a><span data-ttu-id="8ec02-135">항목 복사(Copy-Item)</span><span class="sxs-lookup"><span data-stu-id="8ec02-135">Copying Items (Copy-Item)</span></span>

<span data-ttu-id="8ec02-136">다른 셸에서의 복사 작업에 대해 잘 알고 있는 경우 Windows PowerShell의 **Copy-Item** cmdlet 동작이 특이함을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-136">If you are familiar with the copy operations in other shells, you might find the behavior of the **Copy-Item** cmdlet in Windows PowerShell to be unusual.</span></span> <span data-ttu-id="8ec02-137">항목을 한 위치에서 다른 위치로 이동할 경우 Copy-Item은 기본적으로 해당 내용을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-137">When you copy an item from one location to another, Copy-Item does not copy its contents by default.</span></span>

<span data-ttu-id="8ec02-138">예를 들어 **New.Directory** 디렉터리를 C: 드라이브에서 C:\\temp 디렉터리로 복사할 경우 명령은 성공하지만 New.Directory 디렉터리의 파일이 복사되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-138">For example, if you copy the **New.Directory** directory from the C: drive to the C:\\temp directory, the command succeeds, but the files in the New.Directory directory are not copied.</span></span>

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

<span data-ttu-id="8ec02-139">**C:\\temp\\New.Directory**의 내용을 표시하면 파일이 포함되지 않은 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-139">If you display the contents of **C:\\temp\\New.Directory**, you will find that it contains no files:</span></span>

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

<span data-ttu-id="8ec02-140">**Copy-Item** cmdlet이 새 위치에 내용을 복사하지 않는 이유는 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="8ec02-140">Why doesn't the **Copy-Item** cmdlet copy the contents to the new location?</span></span>

<span data-ttu-id="8ec02-141">**Copy-Item** cmdlet은 제네릭으로 설계되었으므로, 파일 및 폴더를 복사하는 데 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-141">The **Copy-Item** cmdlet was designed to be generic; it is not just for copying files and folders.</span></span> <span data-ttu-id="8ec02-142">또한 파일 및 폴더를 복사할 때 포함된 항목은 제외하고 컨테이너만 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-142">Also, even when copying files and folders, you might want to copy only the container and not the items within it.</span></span>

<span data-ttu-id="8ec02-143">폴더의 모든 내용을 복사하려면 명령에 **Copy-Item** cmdlet의 **Recurse** 매개 변수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-143">To copy all of the contents of a folder, include the **Recurse** parameter of the **Copy-Item** cmdlet in the command.</span></span> <span data-ttu-id="8ec02-144">내용을 포함하지 않고 디렉터리를 이미 복사한 경우 **Force** 매개 변수를 추가하여 빈 폴더를 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-144">If you have already copied the directory without its contents, add the **Force** parameter, which allows you to overwrite the empty folder.</span></span>

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

## <a name="deleting-items-remove-item"></a><span data-ttu-id="8ec02-145">항목 삭제(Remove-Item)</span><span class="sxs-lookup"><span data-stu-id="8ec02-145">Deleting Items (Remove-Item)</span></span>

<span data-ttu-id="8ec02-146">파일 및 폴더를 삭제하려면 **Remove-Item** cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-146">To delete files and folders, use the **Remove-Item** cmdlet.</span></span> <span data-ttu-id="8ec02-147">되돌릴 수 없는 중요한 변경을 수행하는 Windows PowerShell cmdlet(예: **Remove-Item**)은 명령을 입력할 때 종종 확인 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-147">Windows PowerShell cmdlets, such as **Remove-Item**, that can make significant, irreversible changes will often prompt for confirmation when you enter its commands.</span></span> <span data-ttu-id="8ec02-148">예를 들어 **New.Directory** 폴더를 제거하려는 경우 폴더에 파일이 포함되어 있으므로 명령을 확인하는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-148">For example, if you try to remove the **New.Directory** folder, you will be prompted to confirm the command, because the folder contains files:</span></span>

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="8ec02-149">**예**가 기본 응답이므로 폴더와 해당 파일을 삭제하려면 **Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-149">Because **Yes** is the default response, to delete the folder and its files, press the **Enter** key.</span></span> <span data-ttu-id="8ec02-150">확인하지 않고 폴더를 제거하려면 **-Recurse** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-150">To remove the folder without confirming, use the **-Recurse** parameter.</span></span>

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a><span data-ttu-id="8ec02-151">항목 실행(Invoke-Item)</span><span class="sxs-lookup"><span data-stu-id="8ec02-151">Executing Items (Invoke-Item)</span></span>

<span data-ttu-id="8ec02-152">Windows PowerShell에서는 **Invoke-Item** cmdlet을 사용하여 파일 또는 폴더에 대한 기본 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-152">Windows PowerShell uses the **Invoke-Item** cmdlet to perform a default action for a file or folder.</span></span> <span data-ttu-id="8ec02-153">이 기본 작업은 레지스트리에 있는 기본 애플리케이션 처리기에 의해 결정되며, 파일 탐색기에서 항목을 두 번 클릭하는 경우와 효과는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-153">This default action is determined by the default application handler in the registry; the effect is the same as if you double-click the item in File Explorer.</span></span>

<span data-ttu-id="8ec02-154">예를 들어 다음 명령을 실행한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-154">For example, suppose you run the following command:</span></span>

```powershell
Invoke-Item C:\WINDOWS
```

<span data-ttu-id="8ec02-155">C:\\Windows 폴더를 두 번 클릭한 것처럼 C:\\Windows에 있는 탐색기 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-155">An Explorer window that is located in C:\\Windows appears, just as if you had double-clicked the C:\\Windows folder.</span></span>

<span data-ttu-id="8ec02-156">Windows Vista 이전 시스템에서 **Boot.ini** 파일을 호출할 경우:</span><span class="sxs-lookup"><span data-stu-id="8ec02-156">If you invoke the **Boot.ini** file on a system prior to Windows Vista:</span></span>

```powershell
Invoke-Item C:\boot.ini
```

<span data-ttu-id="8ec02-157">.ini 파일 형식이 메모장과 연결되어 있는 경우 boot.ini 파일이 메모장에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8ec02-157">If the .ini file type is associated with Notepad, the boot.ini file opens in Notepad.</span></span>
