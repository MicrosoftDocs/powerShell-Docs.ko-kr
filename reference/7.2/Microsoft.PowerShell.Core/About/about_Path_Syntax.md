---
description: PowerShell의 전체 및 상대 경로 이름 형식에 대해 설명 합니다.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_path_syntax?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Path_Syntax
ms.openlocfilehash: 9a95865d67dc15bf79762987622b702b14faf6c6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599780"
---
# <a name="about-path-syntax"></a><span data-ttu-id="ed5c2-103">경로 구문 정보</span><span class="sxs-lookup"><span data-stu-id="ed5c2-103">About Path Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="ed5c2-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="ed5c2-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="ed5c2-105">PowerShell의 전체 및 상대 경로 이름 형식에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-105">Describes the full and relative path name formats in  PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="ed5c2-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="ed5c2-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="ed5c2-107">PowerShell 공급자를 통해 액세스할 수 있는 데이터 저장소의 모든 항목은 해당 경로 이름으로 고유 하 게 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-107">All items in a data store accessible through a PowerShell provider can be uniquely identified by their path names.</span></span> <span data-ttu-id="ed5c2-108">경로 이름은 항목 이름, 항목이 있는 컨테이너 및 하위 컨테이너 및 컨테이너에 액세스 하는 데 사용할 수 있는 PowerShell 드라이브의 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-108">A path name is a combination of the item name, the container and subcontainers in which the item is located, and the PowerShell drive through which the containers are accessed.</span></span>

<span data-ttu-id="ed5c2-109">PowerShell에서 경로 이름은 정규화 된 두 가지 유형, 즉 정규화 된 유형 및 상대 유형 중 하나로 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-109">In PowerShell, path names are divided into one of two types: fully qualified and relative.</span></span> <span data-ttu-id="ed5c2-110">정규화 된 경로 이름은 경로를 구성 하는 모든 요소로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-110">A fully qualified path name consists of all elements that make up a path.</span></span> <span data-ttu-id="ed5c2-111">다음 구문은 정규화 된 경로 이름의 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-111">The following syntax shows the elements in a fully qualified path name:</span></span>

```powershell
[<provider>::]<drive>:[\<container>[\<subcontainer>...]]\<item>
```

<span data-ttu-id="ed5c2-112">\<provider\>자리 표시자는 데이터 저장소에 액세스 하는 데 사용 하는 PowerShell 공급자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-112">The \<provider\> placeholder refers to the PowerShell provider through which you access the data store.</span></span> <span data-ttu-id="ed5c2-113">예를 들어 파일 시스템 공급자를 사용 하면 컴퓨터의 파일 및 디렉터리에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-113">For example, the FileSystem provider allows you to access the files and directories on your computer.</span></span> <span data-ttu-id="ed5c2-114">이 구문의 요소는 선택 사항이 며, 드라이브 이름이 모든 공급자에서 고유 하기 때문에 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-114">This element of the syntax is optional and is never needed because the drive names are unique across all providers.</span></span>

<span data-ttu-id="ed5c2-115">\<drive\>자리 표시자는 특정 powershell 공급자가 지 원하는 powershell 드라이브를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-115">The \<drive\> placeholder refers to the PowerShell drive that is supported by a particular PowerShell provider.</span></span> <span data-ttu-id="ed5c2-116">FileSystem 공급자의 경우 PowerShell 드라이브는 시스템에 구성 된 Windows 드라이브에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-116">In the case of the FileSystem provider, the PowerShell drives map to the Windows drives that are configured on your system.</span></span> <span data-ttu-id="ed5c2-117">예를 들어 시스템에 A: drive와 C: 드라이브가 포함 된 경우 FileSystem 공급자는 PowerShell에서 동일한 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-117">For example, if your system includes an A: drive and a C: drive, the FileSystem provider creates the same drives in PowerShell.</span></span>

<span data-ttu-id="ed5c2-118">드라이브를 지정한 후에는 해당 항목을 포함 하는 컨테이너와 하위 컨테이너를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-118">After you have specified the drive, you must specify any containers and subcontainers that contain the item.</span></span> <span data-ttu-id="ed5c2-119">컨테이너는 데이터 저장소에 있는 계층적 순서로 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-119">The containers must be specified in the hierarchical order in which they exist in the data store.</span></span> <span data-ttu-id="ed5c2-120">즉, 부모 컨테이너에서 시작 하 고 해당 부모 컨테이너의 자식 컨테이너 등으로 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-120">In other words, you must start with the parent container, then the child container in that parent container, and so on.</span></span> <span data-ttu-id="ed5c2-121">또한 각 컨테이너 앞에 백슬래시가와 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-121">In addition, each container must be preceded by a backslash.</span></span> <span data-ttu-id="ed5c2-122">PowerShell을 사용 하면 다른 PowerShells과의 호환성을 위해 슬래시를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-122">(Note that PowerShell allows you to use forward slashes for compatibility with other PowerShells.)</span></span>

<span data-ttu-id="ed5c2-123">컨테이너와 하위 컨테이너를 지정한 후에는 백슬래시 뒤에 항목 이름을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-123">After the container and subcontainers have been specified, you must provide the item name, preceded by a backslash.</span></span> <span data-ttu-id="ed5c2-124">예를 들어 C: \\ Windows System32 디렉터리에서 Shell.dll 파일의 정규화 된 경로 이름은 다음과 같습니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="ed5c2-124">For example, the fully qualified path name for the Shell.dll file in the C:\\Windows\\System32 directory is as follows:</span></span>

```powershell
C:\Windows\System32\Shell.dll
```

<span data-ttu-id="ed5c2-125">이 경우 컨테이너에 액세스 하는 드라이브는 C: 드라이브이 고, 최상위 컨테이너는 Windows이 고, 하위 컨테이너는 System32 (Windows 컨테이너 내에 있음)이 고, 항목은 Shell.dll입니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-125">In this case, the drive through which the containers are accessed is the C: drive, the top-level container is Windows, the subcontainer is System32 (located within the Windows container), and the item is Shell.dll.</span></span>

<span data-ttu-id="ed5c2-126">경우에 따라 정규화 된 경로 이름을 지정할 필요가 없으며 대신 상대 경로 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-126">In some situations, you do not need to specify a fully qualified path name and can instead use a relative path name.</span></span> <span data-ttu-id="ed5c2-127">상대 경로 이름은 현재 작업 위치를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-127">A relative path name is based on the current working location.</span></span> <span data-ttu-id="ed5c2-128">PowerShell을 사용 하면 현재 작업 위치를 기준으로 해당 위치에 따라 항목을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-128">PowerShell allows you to identify an item based on its location relative to the current working location.</span></span> <span data-ttu-id="ed5c2-129">특수 문자를 사용 하 여 상대 경로 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-129">You can specify relative path names by using special characters.</span></span> <span data-ttu-id="ed5c2-130">다음 표에서는 이러한 각 문자에 대해 설명 하 고 상대 경로 이름 및 정규화 된 경로 이름의 예를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-130">The following table describes each of these characters and provides examples of relative path names and fully qualified path names.</span></span> <span data-ttu-id="ed5c2-131">이 표의 예는 C:\Windows. 설정 되는 현재 작업 디렉터리를 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-131">The examples in the table are based on the current working directory being set to C:\Windows.</span></span>

|<span data-ttu-id="ed5c2-132">기호</span><span class="sxs-lookup"><span data-stu-id="ed5c2-132">Symbol</span></span>|<span data-ttu-id="ed5c2-133">설명</span><span class="sxs-lookup"><span data-stu-id="ed5c2-133">Description</span></span>               |<span data-ttu-id="ed5c2-134">상대 경로</span><span class="sxs-lookup"><span data-stu-id="ed5c2-134">Relative path</span></span>    |<span data-ttu-id="ed5c2-135">전체 경로</span><span class="sxs-lookup"><span data-stu-id="ed5c2-135">Full path</span></span>          |
|------|--------------------------|-----------------|-------------------|
|<span data-ttu-id="ed5c2-136">.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-136">.</span></span>     |<span data-ttu-id="ed5c2-137">현재 위치</span><span class="sxs-lookup"><span data-stu-id="ed5c2-137">Current location</span></span>          |<span data-ttu-id="ed5c2-138">.\\ 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="ed5c2-138">.\\System</span></span>        |<span data-ttu-id="ed5c2-139">c: \\ Windows \\ 시스템</span><span class="sxs-lookup"><span data-stu-id="ed5c2-139">c:\\Windows\\System</span></span>|
|<span data-ttu-id="ed5c2-140">..</span><span class="sxs-lookup"><span data-stu-id="ed5c2-140">..</span></span>    |<span data-ttu-id="ed5c2-141">현재 위치의 부모</span><span class="sxs-lookup"><span data-stu-id="ed5c2-141">Parent of current location</span></span>|<span data-ttu-id="ed5c2-142">..\\ 프로그램 파일</span><span class="sxs-lookup"><span data-stu-id="ed5c2-142">..\\Program Files</span></span>|<span data-ttu-id="ed5c2-143">c: \\ 프로그램 파일</span><span class="sxs-lookup"><span data-stu-id="ed5c2-143">c:\\Program Files</span></span>  |
|\     |<span data-ttu-id="ed5c2-144">현재의 드라이브 루트</span><span class="sxs-lookup"><span data-stu-id="ed5c2-144">Drive root of current</span></span>     |<span data-ttu-id="ed5c2-145">\\프로그램 파일</span><span class="sxs-lookup"><span data-stu-id="ed5c2-145">\\Program Files</span></span>  |<span data-ttu-id="ed5c2-146">c: \\ 프로그램 파일</span><span class="sxs-lookup"><span data-stu-id="ed5c2-146">c:\\Program Files</span></span>  |
|      |<span data-ttu-id="ed5c2-147">위치</span><span class="sxs-lookup"><span data-stu-id="ed5c2-147">location</span></span>                  |                 |                   |
|<span data-ttu-id="ed5c2-148">없음을</span><span class="sxs-lookup"><span data-stu-id="ed5c2-148">[none]</span></span>|<span data-ttu-id="ed5c2-149">특수 문자 없음</span><span class="sxs-lookup"><span data-stu-id="ed5c2-149">No special characters</span></span>     |<span data-ttu-id="ed5c2-150">시스템</span><span class="sxs-lookup"><span data-stu-id="ed5c2-150">System</span></span>           |<span data-ttu-id="ed5c2-151">c: \\ Windows \\ 시스템</span><span class="sxs-lookup"><span data-stu-id="ed5c2-151">c:\\Windows\\System</span></span>|

<span data-ttu-id="ed5c2-152">명령에 경로 이름을 사용 하는 경우 정규화 된 경로 이름 또는 상대 경로를 사용 하는 것과 동일한 방식으로 해당 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-152">When using a path name in a command, you enter that name in the same way whether you use a fully qualified path name or a relative one.</span></span> <span data-ttu-id="ed5c2-153">예를 들어 현재 작업 디렉터리는 C:\Windows..</span><span class="sxs-lookup"><span data-stu-id="ed5c2-153">For example, suppose that your current working directory is C:\Windows.</span></span> <span data-ttu-id="ed5c2-154">다음 Get-ChildItem 명령은 C:\Techdocs 디렉터리에 있는 모든 항목을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-154">The following Get-ChildItem command retrieves all items in the C:\Techdocs directory:</span></span>

```powershell
Get-ChildItem \techdocs
```

<span data-ttu-id="ed5c2-155">백슬래시는 현재 작업 위치의 드라이브 루트를 사용 해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-155">The backslash indicates that the drive root of the current working location should be used.</span></span> <span data-ttu-id="ed5c2-156">작업 디렉터리는 C: Windows 이므로 \\ 드라이브 루트는 c: 드라이브입니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-156">Because the working directory is C:\\Windows, the drive root is the C: drive.</span></span> <span data-ttu-id="ed5c2-157">Techdocs 디렉터리는 루트에서 벗어나 있으므로 백슬래시로 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-157">Because the techdocs directory is located off the root, you need to specify only the backslash.</span></span>

<span data-ttu-id="ed5c2-158">다음 명령을 사용 하 여 동일한 결과를 달성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-158">You can achieve the same results by using the following command:</span></span>

```powershell
Get-ChildItem c:\techdocs
```

<span data-ttu-id="ed5c2-159">정규화 된 경로 이름 또는 상대 경로 이름을 사용 하는지 여부에 관계 없이 경로 이름은 항목을 찾았지만 해당 항목이 다른 컨테이너의 다른 항목과 동일한 이름을 공유 하는 경우에도 항목을 고유 하 게 식별 하기 때문에 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-159">Regardless of whether you use a fully qualified path name or a relative path name, a path name is important not only because it locates an item but also because it uniquely identifies the item even if that item shares the same name as another item in a different container.</span></span>

<span data-ttu-id="ed5c2-160">예를 들어 각각 Results.txt 라는 두 개의 파일이 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-160">For instance, suppose that you have two files that are each named Results.txt.</span></span>
<span data-ttu-id="ed5c2-161">첫 번째 파일은 C: \\ Techdocs 1 월 이라는 디렉터리에 \\ 있고, 두 번째 파일은 c: \\ Techdocs 2 월 이라는 디렉터리에 \\ 있습니다. 첫 번째 파일 (C: \\ Techdocs \\ JanResults.txt)의 경로 이름 \\ 및 두 번째 파일의 경로 이름 (c: \\ Techdocs \\ 2 월 \\Results.txt)을 사용 하 여 두 파일을 명확 하 게 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed5c2-161">The first file is in a directory named C:\\Techdocs\\Jan, and the second file is in a directory named C:\\Techdocs\\Feb. The path name for the first file (C:\\Techdocs\\Jan\\Results.txt) and the path name for the second file (C:\\Techdocs\\Feb\\Results.txt) allow you to clearly distinguish between the two files.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed5c2-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ed5c2-162">SEE ALSO</span></span>

[<span data-ttu-id="ed5c2-163">about_Locations</span><span class="sxs-lookup"><span data-stu-id="ed5c2-163">about_Locations</span></span>](about_Locations.md)

