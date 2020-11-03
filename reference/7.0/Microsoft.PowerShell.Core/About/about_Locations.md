---
description: PowerShell에서 작업 위치에 있는 항목에 액세스 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_locations?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Locations
ms.openlocfilehash: 77a6d7676e08c9a8c67fed38423406eddf004300
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222201"
---
# <a name="about_locations"></a><span data-ttu-id="5c0ff-104">about_Locations</span><span class="sxs-lookup"><span data-stu-id="5c0ff-104">about_Locations</span></span>

## <a name="short-description"></a><span data-ttu-id="5c0ff-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="5c0ff-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="5c0ff-106">PowerShell에서 작업 위치에 있는 항목에 액세스 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-106">Describes how to access items from the working location in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="5c0ff-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="5c0ff-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="5c0ff-108">현재 작업 위치는 명령이 가리키는 기본 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-108">The current working location is the default location to which commands point.</span></span>
<span data-ttu-id="5c0ff-109">즉, 명령의 영향을 받는 항목 또는 위치에 대 한 명시적 경로를 제공 하지 않는 경우 PowerShell에서 사용 하는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-109">In other words, this is the location that PowerShell uses if you do not supply an explicit path to the item or location that is affected by the command.</span></span> <span data-ttu-id="5c0ff-110">대부분의 경우 현재 작업 위치는 PowerShell FileSystem 공급자를 통해 액세스 하는 드라이브 이며 경우에 따라 해당 드라이브의 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-110">In most cases, the current working location is a drive accessed through the PowerShell FileSystem provider and, in some cases, a directory on that drive.</span></span>
<span data-ttu-id="5c0ff-111">예를 들어 현재 작업 위치를 다음 위치로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-111">For example, you might set your current working location to the following location:</span></span>

```powershell
C:\Program Files\Windows PowerShell
```

<span data-ttu-id="5c0ff-112">따라서 다른 경로를 명시적으로 제공 하지 않는 한 모든 명령이이 위치에서 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-112">As a result, all commands are processed from this location unless another path is explicitly provided.</span></span>

<span data-ttu-id="5c0ff-113">PowerShell은 드라이브가 현재 드라이브가 아닌 경우에도 각 드라이브에 대 한 현재 작업 위치를 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-113">PowerShell maintains the current working location for each drive even when the drive is not the current drive.</span></span> <span data-ttu-id="5c0ff-114">이렇게 하면 다른 위치의 드라이브만 참조 하 여 현재 작업 위치에서 항목에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-114">This allows you to access items from the current working location by referring only to the drive of another location.</span></span>
<span data-ttu-id="5c0ff-115">예를 들어 현재 작업 위치가 C: Windows 라고 가정 \\ 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-115">For example, suppose that your current working location is C:\\Windows.</span></span> <span data-ttu-id="5c0ff-116">이제 다음 명령을 사용 하 여 현재 작업 위치를 HKLM: 드라이브로 변경 한다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-116">Now, suppose you use the following command to change your current working location to the HKLM: drive:</span></span>

```powershell
Set-Location HKLM:
```

<span data-ttu-id="5c0ff-117">현재 위치는 이제 레지스트리 드라이브 이지만 \\ 다음 예제와 같이 c: 드라이브를 사용 하 여 c: Windows 디렉터리의 항목에 계속 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-117">Although your current location is now the registry drive, you can still access items in the C:\\Windows directory simply by using the C: drive, as shown in the following example:</span></span>

```powershell
Get-ChildItem C:
```

<span data-ttu-id="5c0ff-118">PowerShell은 해당 드라이브의 현재 작업 위치가 Windows 디렉터리인 것을 기억 하므로 해당 디렉터리에서 항목을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-118">PowerShell remembers that your current working location for that drive is the Windows directory, so it retrieves items from that directory.</span></span> <span data-ttu-id="5c0ff-119">다음 명령을 실행 하면 결과가 동일 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-119">The results would be the same if you ran the following command:</span></span>

```powershell
Get-ChildItem C:\Windows
```

<span data-ttu-id="5c0ff-120">PowerShell에서 Get-Location 명령을 사용 하 여 현재 작업 위치를 확인 하 고 Set-Location 명령을 사용 하 여 현재 작업 위치를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-120">In PowerShell, you can use the Get-Location command to determine the current working location, and you can use the Set-Location command to set the current working location.</span></span> <span data-ttu-id="5c0ff-121">예를 들어 다음 명령은 현재 작업 위치를 C: 드라이브의 Windows 디렉터리로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-121">For example, the following command sets the current working location to the Windows directory of the C: drive:</span></span>

```powershell
Set-Location c:\windows
```

<span data-ttu-id="5c0ff-122">현재 작업 위치를 설정한 후에는 다음 예제에 표시 된 것 처럼 명령에 드라이브 이름 (콜론)을 포함 하 여 다른 드라이브의 항목에 계속 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-122">After you set the current working location, you can still access items from other drives simply by including the drive name (followed by a colon) in the command, as shown in the following example:</span></span>

```powershell
Get-ChildItem HKLM:\software
```

<span data-ttu-id="5c0ff-123">예제 명령은 레지스트리에서 HKEY 로컬 컴퓨터 hive의 소프트웨어 컨테이너에 있는 항목 목록을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-123">The example command retrieves a list of items in the Software container of the HKEY Local Machine hive in the registry.</span></span>

<span data-ttu-id="5c0ff-124">또한 PowerShell을 사용 하면 특수 문자를 사용 하 여 현재 작업 위치와 부모 위치를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-124">PowerShell also allows you to use special characters to represent the current working location and its parent location.</span></span> <span data-ttu-id="5c0ff-125">현재 작업 위치를 나타내려면 단일 마침표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-125">To represent the current working location, use a single period.</span></span> <span data-ttu-id="5c0ff-126">현재 작업 위치의 부모를 나타내려면 두 개의 마침표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-126">To represent the parent of the current working location, use two periods.</span></span> <span data-ttu-id="5c0ff-127">예를 들어 다음은 현재 작업 위치에 있는 시스템 하위 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-127">For example, the following specifies the System subdirectory in the current working location:</span></span>

```powershell
Get-ChildItem .\system
```

<span data-ttu-id="5c0ff-128">현재 작업 위치가 C: windows 인 경우 \\ 이 명령은 c: windows 시스템의 모든 항목 목록을 반환 합니다 \\ \\ .</span><span class="sxs-lookup"><span data-stu-id="5c0ff-128">If the current working location is C:\\Windows, this command returns a list of all the items in C:\\Windows\\System.</span></span> <span data-ttu-id="5c0ff-129">그러나 두 개의 기간을 사용 하는 경우 다음 예제와 같이 현재 작업 디렉터리의 부모 디렉터리가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-129">However, if you use two periods, the parent directory of the current working directory is used, as shown in the following example:</span></span>

```powershell
Get-ChildItem ..\"program files"
```

<span data-ttu-id="5c0ff-130">이 경우 PowerShell은 두 기간을 C: 드라이브로 처리 하므로,이 명령은 C: Program Files 디렉터리의 모든 항목을 검색 합니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="5c0ff-130">In this case, PowerShell treats the two periods as the C: drive, so the command retrieves all the items in the C:\\Program Files directory.</span></span>

<span data-ttu-id="5c0ff-131">슬래시로 시작 하는 경로는 현재 드라이브의 루트에서 경로를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-131">A path beginning with a slash identifies a path from the root of the current drive.</span></span> <span data-ttu-id="5c0ff-132">예를 들어 현재 작업 위치가 C: \\ Program Files \\ PowerShell 이면 드라이브의 루트는 c입니다. 따라서 다음 명령은 C: Windows 디렉터리의 모든 항목을 나열 합니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="5c0ff-132">For example, if your current working location is C:\\Program Files\\PowerShell, the root of your drive is C. Therefore, the following command lists all items in the C:\\Windows directory:</span></span>

```powershell
Get-ChildItem \windows
```

<span data-ttu-id="5c0ff-133">컨테이너 또는 항목의 이름을 제공할 때 드라이브 이름, 슬래시 또는 마침표로 시작 하는 경로를 지정 하지 않으면 컨테이너 또는 항목이 현재 작업 위치에 있는 것으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c0ff-133">If you do not specify a path beginning with a drive name, slash, or period when supplying the name of a container or item, the container or item is assumed to be located in the current working location.</span></span> <span data-ttu-id="5c0ff-134">예를 들어 현재 작업 위치가 C: windows 인 경우 \\ 다음 명령은 c: \\ windows 시스템 디렉터리에 있는 모든 항목을 반환 합니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="5c0ff-134">For example, if your current working location is C:\\Windows, the following command returns all the items in the C:\\Windows\\System directory:</span></span>

```powershell
Get-ChildItem system
```

<span data-ttu-id="5c0ff-135">디렉터리 이름이 아닌 파일 이름을 지정 하는 경우 PowerShell은 해당 파일에 대 한 세부 정보를 반환 합니다 (해당 파일이 현재 작업 위치에 있는 것으로 가정).</span><span class="sxs-lookup"><span data-stu-id="5c0ff-135">If you specify a file name rather than a directory name, PowerShell returns details about that file (assuming that file is located in the current working location).</span></span>

## <a name="see-also"></a><span data-ttu-id="5c0ff-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5c0ff-136">SEE ALSO</span></span>

[<span data-ttu-id="5c0ff-137">Set-Location</span><span class="sxs-lookup"><span data-stu-id="5c0ff-137">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)

[<span data-ttu-id="5c0ff-138">about_Providers</span><span class="sxs-lookup"><span data-stu-id="5c0ff-138">about_Providers</span></span>](about_Providers.md)

[<span data-ttu-id="5c0ff-139">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="5c0ff-139">about_Path_Syntax</span></span>](about_Path_Syntax.md)
