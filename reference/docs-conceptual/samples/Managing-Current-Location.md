---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 현재 위치 관리
ms.openlocfilehash: 42ab56759dec882d140f813c8614e578957722b3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030191"
---
# <a name="managing-current-location"></a><span data-ttu-id="9317d-103">현재 위치 관리</span><span class="sxs-lookup"><span data-stu-id="9317d-103">Managing Current Location</span></span>

<span data-ttu-id="9317d-104">파일 탐색기에서 폴더 시스템을 탐색할 경우 일반적으로 특정 작업 위치 즉, 현재 열려 있는 폴더에 위치합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-104">When navigating folder systems in File Explorer, you usually have a specific working location - namely, the current open folder.</span></span> <span data-ttu-id="9317d-105">현재 폴더에서 항목을 클릭하여 쉽게 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-105">Items in the current folder can be manipulated easily by clicking them.</span></span> <span data-ttu-id="9317d-106">명령줄 인터페이스(예: Cmd.exe)의 경우 특정 파일과 동일한 폴더에 있을 경우 파일의 전체 경로를 지정하지 않고 상대적으로 짧은 이름을 지정하여 파일에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-106">For command-line interfaces such as Cmd.exe, when you are in the same folder as a particular file, you can access it by specifying a relatively short name, rather than needing to specify the entire path to the file.</span></span> <span data-ttu-id="9317d-107">현재 디렉터리를 작업 디렉터리라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-107">The current directory is called the working directory.</span></span>

<span data-ttu-id="9317d-108">Windows PowerShell에서는 명사 **Location**을 사용하여 작업 디렉터리를 나타내고 cmdlet 패밀리를 구현하여 위치를 조사 및 조작합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-108">Windows PowerShell uses the noun **Location** to refer to the working directory, and implements a family of cmdlets to examine and manipulate your location.</span></span>

## <a name="getting-your-current-location-get-location"></a><span data-ttu-id="9317d-109">현재 위치 가져오기(Get-Location)</span><span class="sxs-lookup"><span data-stu-id="9317d-109">Getting Your Current Location (Get-Location)</span></span>

<span data-ttu-id="9317d-110">현재 디렉터리 위치의 경로를 확인하려면 **Get-Location** 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-110">To determine the path of your current directory location, enter the **Get-Location** command:</span></span>

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="9317d-111">Get-Location cmdlet은 BASH 셸의 **pwd** 명령과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-111">The Get-Location cmdlet is similar to the **pwd** command in the BASH shell.</span></span> <span data-ttu-id="9317d-112">Set-Location cmdlet은 Cmd.exe의 **cd** 명령과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-112">The Set-Location cmdlet is similar to the **cd** command in Cmd.exe.</span></span>

## <a name="setting-your-current-location-set-location"></a><span data-ttu-id="9317d-113">현재 위치 설정(Set-Location)</span><span class="sxs-lookup"><span data-stu-id="9317d-113">Setting Your Current Location (Set-Location)</span></span>

<span data-ttu-id="9317d-114">**Get-Location** 명령은 **Set-Location** 명령과 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-114">The **Get-Location** command is used with the **Set-Location** command.</span></span> <span data-ttu-id="9317d-115">**Set-Location** 명령을 사용하여 현재 디렉터리 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-115">The **Set-Location** command allows you to specify your current directory location.</span></span>

```powershell
Set-Location -Path C:\Windows
```

<span data-ttu-id="9317d-116">명령을 입력해도 명령의 효과에 대한 직접적인 피드백이 수신되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-116">After you enter the command, you will notice that you do not receive any direct feedback about the effect of the command.</span></span> <span data-ttu-id="9317d-117">출력이 항상 유용한 것은 아니므로 작업을 수행하는 대부분의 Windows PowerShell 명령은 출력을 거의 또는 전혀 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-117">Most Windows PowerShell commands that perform an action produce little or no output because the output is not always useful.</span></span> <span data-ttu-id="9317d-118">**Set-Location** 명령을 입력할 때 디렉터리가 성공적으로 변경되었는지 확인하려면 **Set-Location** 명령을 입력할 때 **-PassThru** 매개 변수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-118">To verify that a successful directory change has occurred when you enter the **Set-Location** command, include the **-PassThru** parameter when you enter the **Set-Location** command:</span></span>

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

<span data-ttu-id="9317d-119">Windows PowerShell에서 **-PassThru** 매개 변수를 많은 Set 명령과 함께 사용하여 기본 출력이 없는 경우에 결과에 대한 정보를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-119">The **-PassThru** parameter can be used with many Set commands in Windows PowerShell to return information about the result in cases in which there is no default output.</span></span>

<span data-ttu-id="9317d-120">대부분의 UNIX 및 Windows 명령 셸에서와 동일한 방법으로 현재 위치를 기준으로 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-120">You can specify paths relative to your current location in the same way as you would in most UNIX and Windows command shells.</span></span> <span data-ttu-id="9317d-121">상대 경로에 대한 표준 표기법에서 점( **.** )은 현재 폴더를 나타내고, 이중 점( **..** )은 현재 위치의 부모 디렉터리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-121">In standard notation for relative paths, a period (**.**)represents your current folder, and a doubled period (**..**) represents the parent directory of your current location.</span></span>

<span data-ttu-id="9317d-122">예를 들어 **C:\\Windows** 폴더에 있는 경우 점( **.** )은 **C:\\Windows**를 나타내고 이중 점( **..** )은 **C:** 를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-122">For example, if you are in the **C:\\Windows** folder, a period (**.**)represents **C:\\Windows** and double periods (**..**) represent **C:**.</span></span> <span data-ttu-id="9317d-123">다음과 같이 입력하여 현재 위치에서 C: 드라이브의 루트로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-123">You can change from your current location to the root of the C: drive by typing:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

<span data-ttu-id="9317d-124">이 기술은 파일 시스템 드라이브가 아닌 Windows PowerShell 드라이브(예: **HKLM:** )에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-124">The same technique works on Windows PowerShell drives that are not file system drives, such as **HKLM:**.</span></span> <span data-ttu-id="9317d-125">다음과 같이 입력하여 현재 위치를 레지스트리의 HKLM\\Software 키로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-125">You can set your location to the HKLM\\Software key in the registry by typing:</span></span>

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

<span data-ttu-id="9317d-126">그런 다음 상대 경로를 사용하여 디렉터리 위치를 부모 디렉터리(Windows PowerShell HKLM: 드라이브의 루트)로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-126">You can then change the directory location to the parent directory, which is the root of the Windows PowerShell HKLM: drive, by using a relative path:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

<span data-ttu-id="9317d-127">Set-Location을 입력하거나 Set-Location에 대한 기본 제공 Windows PowerShell 별칭(cd, chdir, sl)을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-127">You can type Set-Location or use any of the built-in Windows PowerShell aliases for Set-Location (cd, chdir, sl).</span></span> <span data-ttu-id="9317d-128">예:</span><span class="sxs-lookup"><span data-stu-id="9317d-128">For example:</span></span>

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a><span data-ttu-id="9317d-129">최근 위치 저장 및 다시 호출(Push-Location 및 Pop-Location)</span><span class="sxs-lookup"><span data-stu-id="9317d-129">Saving and Recalling Recent Locations (Push-Location and Pop-Location)</span></span>

<span data-ttu-id="9317d-130">위치를 변경할 때 이전 위치를 추적하여 해당 위치로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-130">When changing locations, it is helpful to keep track of where you have been and to be able to return to your previous location.</span></span> <span data-ttu-id="9317d-131">Windows PowerShell의 **Push-Location** cmdlet은 확인한 디렉터리 경로의 순차적 기록("스택")을 만듭니다. 따라서 보조 **Pop-Location** cmdlet을 사용하여 디렉터리 경로 기록의 이전 단계로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-131">The **Push-Location** cmdlet in Windows PowerShell creates a ordered history (a "stack") of directory paths where you have been, and you can step back through the history of directory paths by using the complementary **Pop-Location** cmdlet.</span></span>

<span data-ttu-id="9317d-132">예를 들어 Windows PowerShell은 일반적으로 사용자의 홈 디렉터리에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-132">For example, Windows PowerShell typically starts in the user's home directory.</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="9317d-133">단어 *스택*은 .NET Framework를 비롯한 다양한 프로그래밍 설정에서 특별한 의미로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-133">The word *stack* has a special meaning in many programming settings, including .NET Framework.</span></span> <span data-ttu-id="9317d-134">항목의 물리적 스택과 마찬가지로 스택에 넣은 마지막 항목을 스택에서 첫 번째 항목으로 끌어올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-134">Like a physical stack of items, the last item you put onto the stack is the first item that you can pull off the stack.</span></span> <span data-ttu-id="9317d-135">항목을 스택에 추가하는 것을 구어체로 항목을 스택에 "푸시"한다고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-135">Adding an item to a stack is colloquially known as "pushing" the item onto the stack.</span></span> <span data-ttu-id="9317d-136">항목을 스택에서 끌어오는 것을 구어체로 항목을 스택에서 "꺼낸"다고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-136">Pulling an item off the stack is colloquially known as "popping" the item off the stack.</span></span>

<span data-ttu-id="9317d-137">현재 위치를 스택에 푸시한 다음 Local Settings 폴더로 이동하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-137">To push the current location onto the stack, and then move to the Local Settings folder, type:</span></span>

```powershell
Push-Location -Path "Local Settings"
```

<span data-ttu-id="9317d-138">이제 다음과 같이 입력하여 Local Settings 위치를 스택으로 푸시하고 Temp 폴더로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-138">You can then push the Local Settings location onto the stack and move to the Temp folder by typing:</span></span>

```powershell
Push-Location -Path Temp
```

<span data-ttu-id="9317d-139">**Get-Location** 명령을 입력하여 디렉터리가 변경되었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-139">You can verify that you changed directories by entering the **Get-Location** command:</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

<span data-ttu-id="9317d-140">그런 다음 **Pop-Location** 명령을 입력하여 최근에 방문한 디렉터리로 바로 이동하고 **Get-Location** 명령을 입력하여 변경을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-140">You can then pop back into the most recently visited directory by entering the **Pop-Location** command, and verify the change by entering the **Get-Location** command:</span></span>

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

<span data-ttu-id="9317d-141">**Set-Location** cmdlet에서와 마찬가지로 **Pop-Location** cmdlet을 입력할 때 **-PassThru** 매개 변수를 포함하여 입력한 디렉터리를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-141">Just as with the **Set-Location** cmdlet, you can include the **-PassThru** parameter when you enter the **Pop-Location** cmdlet to display the directory that you entered:</span></span>

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

<span data-ttu-id="9317d-142">Location cmdlet을 네트워크 경로와 함께 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-142">You can also use the Location cmdlets with network paths.</span></span> <span data-ttu-id="9317d-143">FS01 서버와 Public이라는 공유가 있는 경우 다음과 같이 입력하여 위치를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-143">If you have a server named FS01 with an share named Public, you can change your location by typing</span></span>

```powershell
Set-Location \\FS01\Public
```

<span data-ttu-id="9317d-144">또는</span><span class="sxs-lookup"><span data-stu-id="9317d-144">or</span></span>

```powershell
Push-Location \\FS01\Public
```

<span data-ttu-id="9317d-145">**Push-Location** 및 **Set-Location** 명령을 사용하여 위치를 사용 가능한 드라이브로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-145">You can use the **Push-Location** and **Set-Location** commands to change the location to any available drive.</span></span> <span data-ttu-id="9317d-146">예를 들어 드라이브 문자가 D인 로컬 CD-ROM 드라이브에 데이터 CD가 들어 있는 경우 **Set-Location D:** 명령을 입력하여 위치를 CD 드라이브로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-146">For example, if you have a local CD-ROM drive with drive letter D that contains a data CD, you can change the location to the CD drive by entering the **Set-Location D:** command.</span></span>

<span data-ttu-id="9317d-147">드라이브가 비어 있으면 다음과 같은 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-147">If the drive is empty, you will get the following error message:</span></span>

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

<span data-ttu-id="9317d-148">명령줄 인터페이스를 사용하는 경우 파일 탐색기를 사용하여 사용 가능한 물리적 드라이브를 찾는 데 어려움이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-148">When you are using a command-line interface, it is not convenient to use File Explorer to examine the available physical drives.</span></span> <span data-ttu-id="9317d-149">또한 파일 탐색기에는 모든 Windows PowerShell 드라이브가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-149">Also, File Explorer would not show you the all of the Windows PowerShell drives.</span></span> <span data-ttu-id="9317d-150">Windows PowerShell에서는 Windows PowerShell 드라이브를 조작하는 다양한 명령을 제공합니다. 이에 대해서는 다음에 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="9317d-150">Windows PowerShell provides a set of commands for manipulating Windows PowerShell drives, and we will talk about these next.</span></span>
