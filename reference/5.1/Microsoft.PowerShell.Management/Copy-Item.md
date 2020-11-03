---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-Item
ms.openlocfilehash: 4c15ea0fd9c3fb3837ec2a23e8278016858df09d
ms.sourcegitcommit: 33ac34789e86ffb4e7e69453ae38fc0bd24933dd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/26/2020
ms.locfileid: "93219754"
---
# <span data-ttu-id="21a23-103">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="21a23-103">Copy-Item</span></span>

## <span data-ttu-id="21a23-104">개요</span><span class="sxs-lookup"><span data-stu-id="21a23-104">SYNOPSIS</span></span>
<span data-ttu-id="21a23-105">위치 간에 항목을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-105">Copies an item from one location to another.</span></span>

## <span data-ttu-id="21a23-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="21a23-106">SYNTAX</span></span>

### <span data-ttu-id="21a23-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="21a23-107">Path (Default)</span></span>

```
Copy-Item [-Path] <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-UseTransaction] [-FromSession <PSSession>] [-ToSession <PSSession>]
 [<CommonParameters>]
```

### <span data-ttu-id="21a23-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="21a23-108">LiteralPath</span></span>

```
Copy-Item -LiteralPath <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-UseTransaction] [-FromSession <PSSession>] [-ToSession <PSSession>]
 [<CommonParameters>]
```

## <span data-ttu-id="21a23-109">설명</span><span class="sxs-lookup"><span data-stu-id="21a23-109">DESCRIPTION</span></span>

<span data-ttu-id="21a23-110">`Copy-Item`Cmdlet은 한 위치에서 동일한 네임 스페이스의 다른 위치로 항목을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-110">The `Copy-Item` cmdlet copies an item from one location to another location in the same namespace.</span></span>
<span data-ttu-id="21a23-111">예를 들어 파일을 폴더에 복사할 수 있지만 인증서 드라이브에 파일을 복사할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-111">For instance, it can copy a file to a folder, but it can't copy a file to a certificate drive.</span></span>

<span data-ttu-id="21a23-112">이 cmdlet은 복사 되는 항목을 잘라내거나 삭제 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-112">This cmdlet doesn't cut or delete the items being copied.</span></span> <span data-ttu-id="21a23-113">Cmdlet에서 복사할 수 있는 특정 항목은 항목을 노출 하는 PowerShell 공급자에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-113">The particular items that the cmdlet can copy depend on the PowerShell provider that exposes the item.</span></span> <span data-ttu-id="21a23-114">예를 들어 파일 시스템 드라이브의 파일 및 디렉터리와 레지스트리 드라이브의 레지스트리 키 및 항목을 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-114">For instance, it can copy files and directories in a file system drive and registry keys and entries in the registry drive.</span></span>

<span data-ttu-id="21a23-115">이 cmdlet은 동일한 명령에서 항목을 복사 하 고 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-115">This cmdlet can copy and rename items in the same command.</span></span> <span data-ttu-id="21a23-116">항목의 이름을 바꾸려면 **Destination** 매개 변수 값에 새 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-116">To rename an item, enter the new name in the value of the **Destination** parameter.</span></span> <span data-ttu-id="21a23-117">항목의 이름을 바꾸고 복사 하지 않으려면 cmdlet을 사용 `Rename-Item` 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-117">To rename an item and not copy it, use the `Rename-Item` cmdlet.</span></span>

## <span data-ttu-id="21a23-118">예제</span><span class="sxs-lookup"><span data-stu-id="21a23-118">EXAMPLES</span></span>

### <span data-ttu-id="21a23-119">예제 1: 지정 된 디렉터리에 파일 복사</span><span class="sxs-lookup"><span data-stu-id="21a23-119">Example 1: Copy a file to the specified directory</span></span>

<span data-ttu-id="21a23-120">이 예에서는 `mar1604.log.txt` 파일을 디렉터리에 복사 `C:\Presentation` 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-120">This example copies the `mar1604.log.txt` file to the `C:\Presentation` directory.</span></span> <span data-ttu-id="21a23-121">원본 파일은 삭제 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-121">The original file isn't deleted.</span></span>

```powershell
Copy-Item "C:\Wabash\Logfiles\mar1604.log.txt" -Destination "C:\Presentation"
```

### <span data-ttu-id="21a23-122">예 2: 디렉터리 내용을 기존 디렉터리에 복사</span><span class="sxs-lookup"><span data-stu-id="21a23-122">Example 2: Copy directory contents to an existing directory</span></span>

<span data-ttu-id="21a23-123">이 예에서는 디렉터리의 내용을 `C:\Logfiles` 기존 디렉터리에 복사 `C:\Drawings` 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-123">This example copies the contents of the `C:\Logfiles` directory into the existing `C:\Drawings` directory.</span></span> <span data-ttu-id="21a23-124">`Logfiles`디렉터리가 복사 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-124">The `Logfiles` directory isn't copied.</span></span>

<span data-ttu-id="21a23-125">디렉터리에 `Logfiles` 하위 디렉터리의 파일이 포함 된 경우 해당 하위 디렉터리는 파일 트리와 함께 그대로 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-125">If the `Logfiles` directory contains files in subdirectories, those subdirectories are copied with their file trees intact.</span></span> <span data-ttu-id="21a23-126">기본적으로 **Container** 매개 변수는 **True** 로 설정 되어 디렉터리 구조를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-126">By default, the **Container** parameter is set to **True** , which preserves the directory structure.</span></span>

```powershell
Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings" -Recurse
```

> [!NOTE]
> <span data-ttu-id="21a23-127">복사본에 디렉터리를 포함 해야 하는 경우 `Logfiles` 경로에서을 제거 합니다 `\*` . **Path**</span><span class="sxs-lookup"><span data-stu-id="21a23-127">If you need to include the `Logfiles` directory in the copy, remove the `\*` from the **Path**.</span></span>
> <span data-ttu-id="21a23-128">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="21a23-128">For example:</span></span>
>
> `Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings" -Recurse`

### <span data-ttu-id="21a23-129">예 3: 새 디렉터리에 디렉터리 및 콘텐츠 복사</span><span class="sxs-lookup"><span data-stu-id="21a23-129">Example 3: Copy directory and contents to a new directory</span></span>

<span data-ttu-id="21a23-130">이 예에서는 원본 디렉터리의 내용을 복사 `C:\Logfiles` 하 고 새 대상 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-130">This example copies the contents of the `C:\Logfiles` source directory and creates a new destination directory.</span></span> <span data-ttu-id="21a23-131">새 대상 디렉터리는 `\Logs` 에 생성 됩니다 `C:\Drawings` .</span><span class="sxs-lookup"><span data-stu-id="21a23-131">The new destination directory, `\Logs` is created in `C:\Drawings`.</span></span>

<span data-ttu-id="21a23-132">원본 디렉터리의 이름을 포함 하려면 **예 2** 에 표시 된 것 처럼 기존 대상 디렉터리에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-132">To include the source directory's name, copy to an existing destination directory as shown in **Example 2**.</span></span> <span data-ttu-id="21a23-133">또는 원본 디렉터리와 동일한를 사용 하 여 새 대상 디렉터리의 이름을로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-133">Or, name the new destination directory with the same as the source directory.</span></span>

```powershell
Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings\Logs" -Recurse
```

> [!NOTE]
> <span data-ttu-id="21a23-134">**경로** 에이 포함 되어 있으면 `\*` 하위 디렉터리 트리를 비롯 한 모든 디렉터리의 파일 내용이 새 대상 디렉터리에 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-134">If the **Path** includes `\*`, all the directory's file contents, including the subdirectory trees, are copied to the new destination directory.</span></span> <span data-ttu-id="21a23-135">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="21a23-135">For example:</span></span>
>
> `Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings\Logs" -Recurse`

### <span data-ttu-id="21a23-136">예제 4: 파일을 지정 된 디렉터리에 복사 하 고 파일 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-136">Example 4: Copy a file to the specified directory and rename the file</span></span>

<span data-ttu-id="21a23-137">이 예에서는 cmdlet을 사용 하 여 `Copy-Item` `Get-Widget.ps1` 디렉터리에서 디렉터리로 스크립트를 복사 `\\Server01\Share` `\\Server12\ScriptArchive` 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-137">This example uses the `Copy-Item` cmdlet to copy the `Get-Widget.ps1` script from the `\\Server01\Share` directory to the `\\Server12\ScriptArchive` directory.</span></span> <span data-ttu-id="21a23-138">복사 작업의 일부로 명령은 항목 이름을에서 `Get-Widget.ps1` 로 변경 `Get-Widget.ps1.txt` 하므로 메일 메시지에 첨부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-138">As part of the copy operation, the command changes the item name from `Get-Widget.ps1` to `Get-Widget.ps1.txt`, so it can be attached to email messages.</span></span>

```powershell
Copy-Item "\\Server01\Share\Get-Widget.ps1" -Destination "\\Server12\ScriptArchive\Get-Widget.ps1.txt"
```

### <span data-ttu-id="21a23-139">예 5: 원격 컴퓨터에 파일 복사</span><span class="sxs-lookup"><span data-stu-id="21a23-139">Example 5: Copy a file to a remote computer</span></span>

<span data-ttu-id="21a23-140">의 자격 증명을 사용 하 여 **Server01** 라는 원격 컴퓨터에 대 한 세션이 만들어지고 `Contoso\User01` 이라는 변수에 결과가 저장 됩니다 `$Session` .</span><span class="sxs-lookup"><span data-stu-id="21a23-140">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="21a23-141">`Copy-Item`Cmdlet은 `test.log` `D:\Folder001` `C:\Folder001_Copy` 변수에 저장 된 세션 정보를 사용 하 여 폴더에서 원격 컴퓨터의 폴더로 복사 합니다 `$Session` .</span><span class="sxs-lookup"><span data-stu-id="21a23-141">The `Copy-Item` cmdlet copies `test.log` from the `D:\Folder001` folder to the `C:\Folder001_Copy` folder on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="21a23-142">원본 파일은 삭제 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-142">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "D:\Folder001\test.log" -Destination "C:\Folder001_Copy\" -ToSession $Session
```

### <span data-ttu-id="21a23-143">예제 6: 원격 컴퓨터에 폴더 복사</span><span class="sxs-lookup"><span data-stu-id="21a23-143">Example 6: Copy a folder to a remote computer</span></span>

<span data-ttu-id="21a23-144">의 자격 증명을 사용 하 여 **Server01** 라는 원격 컴퓨터에 대 한 세션이 만들어지고 `Contoso\User01` 이라는 변수에 결과가 저장 됩니다 `$Session` .</span><span class="sxs-lookup"><span data-stu-id="21a23-144">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="21a23-145">`Copy-Item`Cmdlet은 `D:\Folder002` `C:\Folder002_Copy` 변수에 저장 된 세션 정보를 사용 하 여 원격 컴퓨터의 디렉터리에 폴더를 복사 합니다 `$Session` .</span><span class="sxs-lookup"><span data-stu-id="21a23-145">The `Copy-Item` cmdlet copies the `D:\Folder002` folder to the `C:\Folder002_Copy` directory on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="21a23-146">**재귀** 스위치를 사용 하지 않고 하위 폴더 또는 파일은 복사 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-146">Any subfolders or files are not copied without using the **Recurse** switch.</span></span>
<span data-ttu-id="21a23-147">작업은 `Folder002_Copy` 폴더가 아직 없는 경우 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-147">The operation creates the `Folder002_Copy` folder if it doesn't already exist.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server02" -Credential "Contoso\User01"
Copy-Item "D:\Folder002\" -Destination "C:\Folder002_Copy\" -ToSession $Session
```

### <span data-ttu-id="21a23-148">예 7: 원격 컴퓨터에 폴더의 전체 콘텐츠를 재귀적으로 복사</span><span class="sxs-lookup"><span data-stu-id="21a23-148">Example 7: Recursively copy the entire contents of a folder to a remote computer</span></span>

<span data-ttu-id="21a23-149">의 자격 증명을 사용 하 여 **Server01** 라는 원격 컴퓨터에 대 한 세션이 만들어지고 `Contoso\User01` 이라는 변수에 결과가 저장 됩니다 `$Session` .</span><span class="sxs-lookup"><span data-stu-id="21a23-149">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="21a23-150">`Copy-Item`Cmdlet은 `D:\Folder003` `C:\Folder003_Copy` 변수에 저장 된 세션 정보를 사용 하 여 폴더의 전체 내용을 원격 컴퓨터의 디렉터리에 복사 합니다 `$Session` .</span><span class="sxs-lookup"><span data-stu-id="21a23-150">The `Copy-Item` cmdlet copies the entire contents from the `D:\Folder003` folder to the `C:\Folder003_Copy` directory on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="21a23-151">하위 폴더는 파일 트리와 함께 그대로 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-151">The subfolders are copied with their file trees intact.</span></span> <span data-ttu-id="21a23-152">작업은 `Folder003_Copy` 폴더가 아직 없는 경우 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-152">The operation creates the `Folder003_Copy` folder if it doesn't already exist.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder003\" -Destination "C:\Folder003_Copy\" -ToSession $Session -Recurse
```

### <span data-ttu-id="21a23-153">예 8: 원격 컴퓨터에 파일을 복사한 다음 파일 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-153">Example 8: Copy a file to a remote computer and then rename the file</span></span>

<span data-ttu-id="21a23-154">의 자격 증명을 사용 하 여 **Server01** 라는 원격 컴퓨터에 대 한 세션이 만들어지고 `Contoso\User01` 이라는 변수에 결과가 저장 됩니다 `$Session` .</span><span class="sxs-lookup"><span data-stu-id="21a23-154">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="21a23-155">`Copy-Item`Cmdlet은 `scriptingexample.ps1` `D:\Folder004` `C:\Folder004_Copy` 변수에 저장 된 세션 정보를 사용 하 여 폴더에서 원격 컴퓨터의 폴더로 복사 합니다 `$Session` .</span><span class="sxs-lookup"><span data-stu-id="21a23-155">The `Copy-Item` cmdlet copies `scriptingexample.ps1` from the `D:\Folder004` folder to the `C:\Folder004_Copy` folder on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="21a23-156">복사 작업의 일부로 명령은 항목 이름을에서 `scriptingexample.ps1` 로 변경 `scriptingexample_copy.ps1` 하므로 메일 메시지에 첨부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-156">As part of the copy operation, the command changes the item name from `scriptingexample.ps1` to `scriptingexample_copy.ps1`, so it can be attached to email messages.</span></span> <span data-ttu-id="21a23-157">원본 파일은 삭제 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-157">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder004\scriptingexample.ps1" -Destination "C:\Folder004_Copy\scriptingexample_copy.ps1" -ToSession $Session
```

### <span data-ttu-id="21a23-158">예 9: 로컬 컴퓨터에 원격 파일 복사</span><span class="sxs-lookup"><span data-stu-id="21a23-158">Example 9: Copy a remote file to the local computer</span></span>

<span data-ttu-id="21a23-159">의 자격 증명을 사용 하 여 **Server01** 라는 원격 컴퓨터에 대 한 세션이 만들어지고 `Contoso\User01` 이라는 변수에 결과가 저장 됩니다 `$Session` .</span><span class="sxs-lookup"><span data-stu-id="21a23-159">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="21a23-160">`Copy-Item`Cmdlet은 `test.log` `C:\MyRemoteData\` `D:\MyLocalData` 변수에 저장 된 세션 정보를 사용 하 여 원격에서 로컬 폴더로 복사 합니다 `$Session` .</span><span class="sxs-lookup"><span data-stu-id="21a23-160">The `Copy-Item` cmdlet copies `test.log` from the remote `C:\MyRemoteData\` to the local `D:\MyLocalData` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="21a23-161">원본 파일은 삭제 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-161">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\test.log" -Destination "D:\MyLocalData\" -FromSession $Session
```

### <span data-ttu-id="21a23-162">예 10: 원격 폴더의 전체 콘텐츠를 로컬 컴퓨터에 복사</span><span class="sxs-lookup"><span data-stu-id="21a23-162">Example 10: Copy the entire contents of a remote folder to the local computer</span></span>

<span data-ttu-id="21a23-163">의 자격 증명을 사용 하 여 **Server01** 라는 원격 컴퓨터에 대 한 세션이 만들어지고 `Contoso\User01` 이라는 변수에 결과가 저장 됩니다 `$Session` .</span><span class="sxs-lookup"><span data-stu-id="21a23-163">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="21a23-164">`Copy-Item`Cmdlet은 `C:\MyRemoteData\scripts` `D:\MyLocalData` 변수에 저장 된 세션 정보를 사용 하 여 원격 폴더의 전체 콘텐츠를 로컬 폴더에 복사 합니다 `$Session` .</span><span class="sxs-lookup"><span data-stu-id="21a23-164">The `Copy-Item` cmdlet copies the entire contents from the remote `C:\MyRemoteData\scripts` folder to the local `D:\MyLocalData` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="21a23-165">Scripts 폴더에 하위 폴더의 파일이 포함 된 경우 해당 하위 폴더는 파일 트리와 함께 그대로 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-165">If the scripts folder contains files in subfolders, those subfolders are copied with their file trees intact.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\" -FromSession $Session
```

### <span data-ttu-id="21a23-166">예 11: 로컬 컴퓨터에 원격 폴더의 전체 콘텐츠를 재귀적으로 복사</span><span class="sxs-lookup"><span data-stu-id="21a23-166">Example 11: Recursively copy the entire contents of a remote folder to the local computer</span></span>

<span data-ttu-id="21a23-167">의 자격 증명을 사용 하 여 **Server01** 라는 원격 컴퓨터에 대 한 세션이 만들어지고 `Contoso\User01` 이라는 변수에 결과가 저장 됩니다 `$Session` .</span><span class="sxs-lookup"><span data-stu-id="21a23-167">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="21a23-168">`Copy-Item`Cmdlet은 `C:\MyRemoteData\scripts` `D:\MyLocalData\scripts` 변수에 저장 된 세션 정보를 사용 하 여 원격 폴더의 전체 콘텐츠를 로컬 폴더에 복사 합니다 `$Session` .</span><span class="sxs-lookup"><span data-stu-id="21a23-168">The `Copy-Item` cmdlet copies the entire contents from the remote `C:\MyRemoteData\scripts` folder to the local `D:\MyLocalData\scripts` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="21a23-169">**재귀** 매개 변수가 사용 되기 때문에이 작업은 스크립트 폴더를 만듭니다 (이미 존재 하지 않는 경우).</span><span class="sxs-lookup"><span data-stu-id="21a23-169">Because the **Recurse** parameter is used, the operation creates the scripts folder if it doesn't already exist.</span></span> <span data-ttu-id="21a23-170">Scripts 폴더에 하위 폴더의 파일이 포함 된 경우 해당 하위 폴더는 파일 트리와 함께 그대로 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-170">If the scripts folder contains files in subfolders, those subfolders are copied with their file trees intact.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\scripts" -FromSession $Session -Recurse
```

### <span data-ttu-id="21a23-171">예 12: 폴더 트리에서 현재 폴더로 파일을 재귀적으로 복사</span><span class="sxs-lookup"><span data-stu-id="21a23-171">Example 12: Recursively copy files from a folder tree into the current folder</span></span>

<span data-ttu-id="21a23-172">이 예에서는 다단계 폴더 구조에서 단일 플랫 폴더로 파일을 복사 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-172">This example shows how to copy files from a multilevel folder structure into a single flat folder.</span></span>
<span data-ttu-id="21a23-173">처음 세 명령은 기존 폴더 구조와 두 파일의 내용 (두 이름 모두)을 보여 줍니다 `file3.txt` .</span><span class="sxs-lookup"><span data-stu-id="21a23-173">The first three commands show the existing folder structure and the contents of two files, both names `file3.txt`.</span></span>

```powershell
PS C:\temp\test> (Get-ChildItem C:\temp\tree -Recurse).FullName
C:\temp\tree\subfolder
C:\temp\tree\file1.txt
C:\temp\tree\file2.txt
C:\temp\tree\file3.txt
C:\temp\tree\subfolder\file3.txt
C:\temp\tree\subfolder\file4.txt
C:\temp\tree\subfolder\file5.txt

PS C:\temp\test> Get-Content C:\temp\tree\file3.txt
This is file3.txt in the root folder

PS C:\temp\test> Get-Content C:\temp\tree\subfolder\file3.txt
This is file3.txt in the subfolder

PS C:\temp\test> Copy-Item -Path C:\temp\tree -Filter *.txt -Recurse -Container:$false
PS C:\temp\test> (Get-ChildItem . -Recurse).FullName
C:\temp\test\subfolder
C:\temp\test\file1.txt
C:\temp\test\file2.txt
C:\temp\test\file3.txt
C:\temp\test\file4.txt
C:\temp\test\file5.txt

PS C:\temp\test> Get-Content .\file3.txt
This is file3.txt in the subfolder
```

<span data-ttu-id="21a23-174">`Copy-Item`Cmdlet은 **Container** 매개 변수를로 설정 합니다 `$false` .</span><span class="sxs-lookup"><span data-stu-id="21a23-174">The `Copy-Item` cmdlet has the **Container** parameter set to `$false`.</span></span> <span data-ttu-id="21a23-175">이렇게 하면 소스 폴더의 내용이 복사 되지만 폴더 구조는 유지 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-175">This causes the contents of the source folder to be copied but does not preserve the folder structure.</span></span> <span data-ttu-id="21a23-176">동일한 이름을 가진 파일은 대상 폴더에서 덮어쓰여집니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-176">Notice that files with the same name are overwritten in the destination folder.</span></span>

## <span data-ttu-id="21a23-177">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="21a23-177">PARAMETERS</span></span>

### <span data-ttu-id="21a23-178">-Confirm</span><span class="sxs-lookup"><span data-stu-id="21a23-178">-Confirm</span></span>

<span data-ttu-id="21a23-179">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-179">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="21a23-180">-컨테이너</span><span class="sxs-lookup"><span data-stu-id="21a23-180">-Container</span></span>

<span data-ttu-id="21a23-181">이 cmdlet은 복사 작업 중에 컨테이너 개체를 유지 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-181">Indicates that this cmdlet preserves container objects during the copy operation.</span></span> <span data-ttu-id="21a23-182">기본적으로 **Container** 매개 변수는 **True** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-182">By default, the **Container** parameter is set to **True**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21a23-183">-Credential</span><span class="sxs-lookup"><span data-stu-id="21a23-183">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="21a23-184">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-184">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="21a23-185">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-185">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="21a23-186">-Destination</span><span class="sxs-lookup"><span data-stu-id="21a23-186">-Destination</span></span>

<span data-ttu-id="21a23-187">새 위치의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-187">Specifies the path to the new location.</span></span> <span data-ttu-id="21a23-188">기본값은 현재 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-188">The default is the current directory.</span></span>

<span data-ttu-id="21a23-189">복사할 항목의 이름을 바꾸려면 **Destination** 매개 변수 값에 새 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-189">To rename the item being copied, specify a new name in the value of the **Destination** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21a23-190">-제외</span><span class="sxs-lookup"><span data-stu-id="21a23-190">-Exclude</span></span>

<span data-ttu-id="21a23-191">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-191">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="21a23-192">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-192">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="21a23-193">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-193">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="21a23-194">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="21a23-195">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="21a23-195">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="21a23-196">-Filter</span><span class="sxs-lookup"><span data-stu-id="21a23-196">-Filter</span></span>

<span data-ttu-id="21a23-197">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-197">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="21a23-198">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-198">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="21a23-199">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-199">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="21a23-200">필터는 다른 매개 변수 보다 더 효율적입니다. 공급자는 검색 된 후 개체를 PowerShell로 필터링 하는 대신 cmdlet이 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-200">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span>

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

### <span data-ttu-id="21a23-201">-Force</span><span class="sxs-lookup"><span data-stu-id="21a23-201">-Force</span></span>

<span data-ttu-id="21a23-202">이 cmdlet이 다른 방법으로는 변경할 수 없는 항목 (예: 읽기 전용 파일 또는 별칭)을 복사 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-202">Indicates that this cmdlet copies items that can't otherwise be changed, such as copying over a read-only file or alias.</span></span>

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

### <span data-ttu-id="21a23-203">-FromSession</span><span class="sxs-lookup"><span data-stu-id="21a23-203">-FromSession</span></span>

<span data-ttu-id="21a23-204">원격 파일이 복사 되는 **PSSession** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-204">Specifies the **PSSession** object from which a remote file is being copied.</span></span> <span data-ttu-id="21a23-205">이 매개 변수를 사용 하는 경우 **Path** 및 **LiteralPath** 매개 변수는 원격 컴퓨터의 로컬 경로를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-205">When you use this parameter, the **Path** and **LiteralPath** parameters refer to the local path on the remote machine.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21a23-206">-포함</span><span class="sxs-lookup"><span data-stu-id="21a23-206">-Include</span></span>

<span data-ttu-id="21a23-207">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-207">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="21a23-208">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-208">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="21a23-209">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-209">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="21a23-210">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-210">Wildcard characters are permitted.</span></span> <span data-ttu-id="21a23-211">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="21a23-211">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="21a23-212">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="21a23-212">-LiteralPath</span></span>

<span data-ttu-id="21a23-213">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-213">Specifies a path to one or more locations.</span></span> <span data-ttu-id="21a23-214">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-214">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="21a23-215">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-215">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="21a23-216">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="21a23-216">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="21a23-217">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-217">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="21a23-218">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="21a23-218">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="21a23-219">-PassThru</span><span class="sxs-lookup"><span data-stu-id="21a23-219">-PassThru</span></span>

<span data-ttu-id="21a23-220">작업 중인 항목을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-220">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="21a23-221">기본적으로이 cmdlet은 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-221">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="21a23-222">-Path</span><span class="sxs-lookup"><span data-stu-id="21a23-222">-Path</span></span>

<span data-ttu-id="21a23-223">복사할 항목의 경로를 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-223">Specifies, as a string array, the path to the items to copy.</span></span> <span data-ttu-id="21a23-224">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-224">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="21a23-225">-재귀</span><span class="sxs-lookup"><span data-stu-id="21a23-225">-Recurse</span></span>

<span data-ttu-id="21a23-226">이 cmdlet이 재귀적 복사를 수행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-226">Indicates that this cmdlet does a recursive copy.</span></span>

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

### <span data-ttu-id="21a23-227">-ToSession</span><span class="sxs-lookup"><span data-stu-id="21a23-227">-ToSession</span></span>

<span data-ttu-id="21a23-228">원격 파일이 복사 되는 **PSSession** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-228">Specifies the **PSSession** object to which a remote file is being copied.</span></span> <span data-ttu-id="21a23-229">이 매개 변수를 사용 하는 경우 **대상** 매개 변수는 원격 컴퓨터의 로컬 경로를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-229">When you use this parameter, the **Destination** parameter refers to the local path on the remote machine.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21a23-230">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="21a23-230">-UseTransaction</span></span>

<span data-ttu-id="21a23-231">활성 트랜잭션에 명령을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-231">Includes the command in the active transaction.</span></span> <span data-ttu-id="21a23-232">이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-232">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="21a23-233">자세한 내용은 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21a23-233">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="21a23-234">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="21a23-234">-WhatIf</span></span>

<span data-ttu-id="21a23-235">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-235">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="21a23-236">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-236">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="21a23-237">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="21a23-237">CommonParameters</span></span>

<span data-ttu-id="21a23-238">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-238">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="21a23-239">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21a23-239">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="21a23-240">입력</span><span class="sxs-lookup"><span data-stu-id="21a23-240">INPUTS</span></span>

### <span data-ttu-id="21a23-241">System.String</span><span class="sxs-lookup"><span data-stu-id="21a23-241">System.String</span></span>

<span data-ttu-id="21a23-242">이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-242">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="21a23-243">출력</span><span class="sxs-lookup"><span data-stu-id="21a23-243">OUTPUTS</span></span>

### <span data-ttu-id="21a23-244">없음 또는 복사한 항목을 나타내는 개체</span><span class="sxs-lookup"><span data-stu-id="21a23-244">None or an object representing the copied item</span></span>

<span data-ttu-id="21a23-245">**PassThru** 매개 변수를 사용 하는 경우이 cmdlet은 복사 된 항목을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-245">When you use the **PassThru** parameter, this cmdlet returns an object that represents the copied item.</span></span> <span data-ttu-id="21a23-246">그렇지 않으면이 cmdlet은 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-246">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="21a23-247">참고</span><span class="sxs-lookup"><span data-stu-id="21a23-247">NOTES</span></span>

<span data-ttu-id="21a23-248">이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-248">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="21a23-249">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="21a23-249">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="21a23-250">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21a23-250">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="21a23-251">관련 링크</span><span class="sxs-lookup"><span data-stu-id="21a23-251">RELATED LINKS</span></span>

[<span data-ttu-id="21a23-252">about_Providers</span><span class="sxs-lookup"><span data-stu-id="21a23-252">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="21a23-253">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="21a23-253">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="21a23-254">Get-Item</span><span class="sxs-lookup"><span data-stu-id="21a23-254">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="21a23-255">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="21a23-255">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="21a23-256">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="21a23-256">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="21a23-257">Move-Item</span><span class="sxs-lookup"><span data-stu-id="21a23-257">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="21a23-258">New-Item</span><span class="sxs-lookup"><span data-stu-id="21a23-258">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="21a23-259">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="21a23-259">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="21a23-260">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="21a23-260">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="21a23-261">Set-Item</span><span class="sxs-lookup"><span data-stu-id="21a23-261">Set-Item</span></span>](Set-Item.md)
