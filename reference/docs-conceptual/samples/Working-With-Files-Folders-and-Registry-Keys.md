---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 파일, 폴더 및 레지스트리 키 작업
ms.openlocfilehash: 0c8716c384827d0816e2847ff81232c14638681b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030766"
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="c775a-103">파일, 폴더 및 레지스트리 키 작업</span><span class="sxs-lookup"><span data-stu-id="c775a-103">Working With Files, Folders and Registry Keys</span></span>

<span data-ttu-id="c775a-104">Windows PowerShell에서는 명사 **Item**을 사용하여 Windows PowerShell 드라이브에 있는 항목을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="c775a-105">Windows PowerShell FileSystem 공급자를 처리할 때 **Item**은 파일, 폴더 또는 Windows PowerShell 드라이브일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="c775a-106">이러한 항목을 나열하고 사용하는 것은 대부분의 관리 설정의 기본적인 작업이므로 이러한 작업에 대해 자세히 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="c775a-107">파일, 폴더 및 레지스트리 키 열거(Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="c775a-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>

<span data-ttu-id="c775a-108">특정 위치에서 항목 모음을 가져오는 것은 그런 일반적인 작업이므로 **Get-ChildItem** cmdlet은 폴더와 같은 컨테이너 내에 있는 모든 항목을 반환하도록 특별히 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="c775a-109">C:\\Windows 폴더에 직접 포함되어 있는 모든 파일과 폴더를 반환하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

<span data-ttu-id="c775a-110">목록은 **Cmd.exe**에서 **dir** 명령을 입력하거나 UNIX 명령 셸에서 **ls** 명령을 입력할 때 표시되는 것과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="c775a-111">**Get-ChildItem** cmdlet의 매개 변수를 사용하여 매우 복잡한 목록을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="c775a-112">이제 몇 가지 시나리오를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="c775a-113">다음과 같이 입력하여 **Get-ChildItem** cmdlet의 구문을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="c775a-114">이러한 매개 변수를 조합하거나 일치시켜서 사용자 지정 출력을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-114">These parameters can be mixed and matched to get highly customized output.</span></span>

### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="c775a-115">모든 포함된 항목 나열(-Recurse)</span><span class="sxs-lookup"><span data-stu-id="c775a-115">Listing all Contained Items (-Recurse)</span></span>

<span data-ttu-id="c775a-116">Windows 폴더 내에 있는 항목과 하위 폴더에 포함된 모든 항목을 표시하려면 **Get-ChildItem**의 **Recurse** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="c775a-117">목록에는 Windows 폴더 내의 모든 항목과 하위 폴더의 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="c775a-118">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a><span data-ttu-id="c775a-119">이름별로 항목 필터링(-Name)</span><span class="sxs-lookup"><span data-stu-id="c775a-119">Filtering Items by Name (-Name)</span></span>

<span data-ttu-id="c775a-120">항목의 이름만 표시하려면 **Get-Childitem**의 **Name** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="c775a-121">숨겨진 항목을 강제로 나열(-Force)</span><span class="sxs-lookup"><span data-stu-id="c775a-121">Forcibly Listing Hidden Items (-Force)</span></span>

<span data-ttu-id="c775a-122">일반적으로 파일 탐색기 또는 Cmd.exe에 표시되지 않는 항목은 **Get-ChildItem** 명령의 출력에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="c775a-123">숨겨진 항목을 표시하려면 **Get-ChildItem**의 **Force** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="c775a-124">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-124">For example:</span></span>

```powershell
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="c775a-125">**Get-ChildItem** 명령의 일반적인 동작을 강제로 재정의할 수 있으므로 이 매개 변수의 이름은 Force입니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="c775a-126">Force는 cmdlet이 일반적으로 수행하지 않는 작업을 강제로 수행하는 데 널리 사용되는 매개 변수입니다. 단, 시스템 보안을 저해하는 작업은 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="c775a-127">와일드카드와 항목 이름 일치</span><span class="sxs-lookup"><span data-stu-id="c775a-127">Matching Item Names with Wildcards</span></span>

<span data-ttu-id="c775a-128">**Get-ChildItem** 명령에서 나열할 항목의 경로에 와일드카드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="c775a-129">와일드카드 일치는 Windows PowerShell 엔진에서 처리되므로 와일드카드를 허용하는 모든 cmdlet은 동일한 표기법을 사용하고 일치 동작이 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="c775a-130">Windows PowerShell 와일드카드 표기법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="c775a-131">별표(\*)는 0개 이상의 모든 문자를 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="c775a-132">물음표(?)는 정확히 한 문자를 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="c775a-133">왼쪽 대괄호(\[) 문자와 오른쪽 대괄호(]) 문자는 일치시킬 문자를 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="c775a-134">다음 예에서는 와일드카드 지정 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="c775a-135">Windows 디렉터리에서 접미사 **.log**를 포함하고 기본 이름이 정확히 5자인 모든 파일을 찾으려면 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

```
PS> Get-ChildItem -Path C:\Windows\?????.log

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

<span data-ttu-id="c775a-136">Windows 디렉터리에서 문자 **x**로 시작하는 모든 파일을 찾으려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="c775a-137">이름이 **x** 또는 **z**로 시작하는 모든 파일을 찾으려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

### <a name="excluding-items--exclude"></a><span data-ttu-id="c775a-138">항목 제외(-Exclude)</span><span class="sxs-lookup"><span data-stu-id="c775a-138">Excluding Items (-Exclude)</span></span>

<span data-ttu-id="c775a-139">Get-ChildItem의 **Exclude** 매개 변수를 사용하여 특정 항목을 제외할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="c775a-140">그러면 단일 문에서 복잡한 필터링을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="c775a-141">예를 들어 System32 폴더에서 Windows 시간 서비스 DLL을 찾으려고 하지만 DLL 이름이 "W"로 시작하고 "32"가 포함되어 있다는 것만 알고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="c775a-142">**w\&#42;32\&#42;.dll**과 같은 문은 조건을 만족하는 모든 DLL을 찾지만, 이름에 "95" 또는 "16"을 포함하는 Windows 95 및 16비트 Windows 호환 DLL도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="c775a-143">**Exclude** 매개 변수를 **\&#42;\[9516]\&#42;** 패턴과 함께 사용하여 이름에 이러한 숫자가 포함된 파일을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*

Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="c775a-144">Get-ChildItem 매개 변수 혼합</span><span class="sxs-lookup"><span data-stu-id="c775a-144">Mixing Get-ChildItem Parameters</span></span>

<span data-ttu-id="c775a-145">동일한 명령에 **Get-ChildItem** cmdlet의 여러 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="c775a-146">매개 변수를 혼합하기 전에 와일드카드 일치에 대해 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="c775a-147">예를 들어 다음 명령은 결과를 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-147">For example, the following command returns no results:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="c775a-148">Windows 폴더에 문자 "z"로 시작하는 DLL이 두 개 있지만 결과는 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="c775a-149">와일드카드를 경로의 일부로 지정했기 때문에 결과가 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="c775a-150">재귀적 명령이지만 **Get-ChildItem** cmdlet은 항목을 Windows 폴더에서 이름이 ".dll"로 끝나는 항목으로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="c775a-151">이름이 특정 패턴과 일치하는 파일에 대한 재귀 검색을 지정하려면 **-Include** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c775a-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```
