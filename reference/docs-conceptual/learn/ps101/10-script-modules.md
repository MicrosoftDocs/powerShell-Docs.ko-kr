---
title: 스크립트 모듈
description: 스크립트 모듈은 여러 스크립트와 함수를 재사용 가능한 도구로 패키징할 수 있는 간편한 방법입니다.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 661ba725764e1f31df628f6c5f2d58d760656e37
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438284"
---
# <a name="chapter-10---script-modules"></a><span data-ttu-id="3f6a3-103">10장 - 스크립트 모듈</span><span class="sxs-lookup"><span data-stu-id="3f6a3-103">Chapter 10 - Script modules</span></span>

<span data-ttu-id="3f6a3-104">PowerShell의 원라이너와 스크립트를 재사용 가능한 도구로 전환하는 기능은 자주 사용하면 대단히 강력한 도구가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-104">Turning your one-liners and scripts in PowerShell into reusable tools becomes even more important if it's something that you're going to use frequently.</span></span> <span data-ttu-id="3f6a3-105">함수를 스크립트 모듈에 패키지하면 더 전문적인 느낌을 주며 공유도 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-105">Packaging your functions in a script module makes them look and feel more professional and makes them easier to share.</span></span>

## <a name="dot-sourcing-functions"></a><span data-ttu-id="3f6a3-106">도트 소싱 함수</span><span class="sxs-lookup"><span data-stu-id="3f6a3-106">Dot-Sourcing Functions</span></span>

<span data-ttu-id="3f6a3-107">이전 장에서는 도트 소싱 함수는 다루지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-107">Something that we didn't talk about in the previous chapter is dot-sourcing functions.</span></span> <span data-ttu-id="3f6a3-108">스크립트에 있는 함수가 모듈의 일부가 아니라면, 함수가 저장된 `.PS1` 파일을 도트 소싱해야만 함수를 메모리에 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-108">When a function in a script isn't part of a module, the only way to load it into memory is to dot-source the `.PS1` file that it's saved in.</span></span>

<span data-ttu-id="3f6a3-109">다음 함수는 `Get-MrPSVersion.ps1`로 저장되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-109">The following function has been saved as `Get-MrPSVersion.ps1`.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}
```

<span data-ttu-id="3f6a3-110">스크립트를 실행하면 아무 일도 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-110">When you run the script, nothing happens.</span></span>

```powershell
.\Get-MrPSVersion.ps1
```

<span data-ttu-id="3f6a3-111">함수를 호출하면 오류 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-111">If you try to call the function, it generates an error message.</span></span>

```powershell
Get-MrPSVersion
```

```Output
Get-MrPSVersion : The term 'Get-MrPSVersion' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [], CommandNotFou
   ndException
    + FullyQualifiedErrorId : CommandNotFoundException

```

<span data-ttu-id="3f6a3-112">함수가 **Function** PSDrive에 있는지 확인하면 함수가 메모리에 로드되었는지를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-112">You can determine if functions are loaded into memory by checking to see if they exist on the **Function** PSDrive.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
Get-ChildItem : Cannot find path 'Get-MrPSVersion' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path Function:\Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [Get-ChildItem],
   ItemNotFoundException
    + FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
```

<span data-ttu-id="3f6a3-113">함수를 포함하는 스크립트를 호출하면 함수가 스크립트 범위에 로드된다는 문제가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-113">The problem with calling the script that contains the function is that the functions are loaded in the _Script_ scope.</span></span> <span data-ttu-id="3f6a3-114">스크립트가 완료되면 이 범위가 제거되고 함수도 함께 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-114">When the script completes, that scope is removed and the function is removed with it.</span></span>

<span data-ttu-id="3f6a3-115">함수는 전역 범위로 로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-115">The function needs to be loaded into the _Global_ scope.</span></span> <span data-ttu-id="3f6a3-116">이렇게 하려면 함수를 포함하는 스크립트를 도트 소싱해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-116">That can be accomplished by dot-sourcing the script that contains the function.</span></span> <span data-ttu-id="3f6a3-117">상대 경로를 사용해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-117">The relative path can be used.</span></span>

```powershell
. .\Get-MrPSVersion.ps1
```

<span data-ttu-id="3f6a3-118">정규화된 경로도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-118">The fully qualified path can also be used.</span></span>

```powershell
. C:\Demo\Get-MrPSVersion.ps1
```

<span data-ttu-id="3f6a3-119">경로 일부가 변수에 저장되었다면 경로의 나머지 부분과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-119">If a portion of the path is stored in a variable, it can be combined with the remainder of the path.</span></span>
<span data-ttu-id="3f6a3-120">문자열 연결을 사용하여 변수를 경로의 나머지 부분과 결합할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-120">There's no reason to use string concatenation to combine the variable together with the remainder of the path.</span></span>

```powershell
$Path = 'C:\'
. $Path\Get-MrPSVersion.ps1
```

<span data-ttu-id="3f6a3-121">이제 **Function** PSDrive를 확인하면 `Get-MrPSVersion` 함수가 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-121">Now when I check the **Function** PSDrive, the `Get-MrPSVersion` function exists.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-MrPSVersion
```

## <a name="script-modules"></a><span data-ttu-id="3f6a3-122">스크립트 모듈</span><span class="sxs-lookup"><span data-stu-id="3f6a3-122">Script Modules</span></span>

<span data-ttu-id="3f6a3-123">PowerShell에서의 스크립트 모듈은 함수를 하나 이상 포함하며 `.PS1` 파일이 아닌 `.PSM1` 파일로 저장되는 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-123">A script module in PowerShell is simply a file containing one or more functions that's saved as a `.PSM1` file instead of a `.PS1` file.</span></span>

<span data-ttu-id="3f6a3-124">스크립트 모듈을 만들려면 어떻게 해야 할까요?</span><span class="sxs-lookup"><span data-stu-id="3f6a3-124">How do you create a script module?</span></span> <span data-ttu-id="3f6a3-125">`New-Module` 같은 이름이 지정된 명령을 사용해야 한다고 생각하실지도 모릅니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-125">You're probably guessing with a command named something like `New-Module`.</span></span> <span data-ttu-id="3f6a3-126">이러한 생각이 틀릴 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-126">Your assumption would be wrong.</span></span> <span data-ttu-id="3f6a3-127">PowerShell에는 `New-Module`이라는 명령이 있지만 이 명령은 스크립트 모듈이 아닌 동적 모듈을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-127">While there is a command in PowerShell named `New-Module`, that command creates a dynamic module, not a script module.</span></span> <span data-ttu-id="3f6a3-128">필요한 명령을 찾았다고 생각하더라도 항상 명령 관련 도움말을 읽어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-128">Always be sure to read the help for a command even when you think you've found the command you need.</span></span>

```powershell
help New-Module
```

```Output
NAME
    New-Module

SYNOPSIS
    Creates a new dynamic module that exists only in memory.

SYNTAX
    New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-ArgumentList <Object[]>]
    [-AsCustomObject] [-Cmdlet <String[]>] [-Function <String[]>] [-ReturnResult]
    [<CommonParameters>]

DESCRIPTION
    The New-Module cmdlet creates a dynamic module from a script block. The members of
    the dynamic module, such as functions and variables, are immediately available in
    the session and remain available until you close the session.

    Like static modules, by default, the cmdlets and functions in a dynamic module are
    exported and the variables and aliases are not. However, you can use the
    Export-ModuleMember cmdlet and the parameters of New-Module to override the defaults.

    You can also use the AsCustomObject parameter of New-Module to return the dynamic
    module as a custom object. The members of the modules, such as functions, are
    implemented as script methods of the custom object instead of being imported into
    the session.

    Dynamic modules exist only in memory, not on disk. Like all modules, the members of
    dynamic modules run in a private module scope that is a child of the global scope.
    Get-Module cannot get a dynamic module, but Get-Command can get the exported members.

    To make a dynamic module available to Get-Module , pipe a New-Module command to
    Import-Module, or pipe the module object that New-Module returns to Import-Module .
    This action adds the dynamic module to the Get-Module list, but it does not save the
    module to disk or make it persistent.

RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821495
    Export-ModuleMember
    Get-Module
    Import-Module
    Remove-Module

REMARKS
    To see the examples, type: "get-help New-Module -examples".
    For more information, type: "get-help New-Module -detailed".
    For technical information, type: "get-help New-Module -full".
    For online help, type: "get-help New-Module -online"
```

<span data-ttu-id="3f6a3-129">이전 장에서 함수가 승인된 동사를 사용하지 않으면 모듈을 가져올 때 경고 메시지가 생성된다고 설명했습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-129">In the previous chapter, I mentioned that functions should use approved verbs otherwise they'll generate a warning message when the module is imported.</span></span> <span data-ttu-id="3f6a3-130">다음 코드는 `New-Module` cmdlet을 사용하여 메모리에 동적 모듈을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-130">The following code uses the `New-Module` cmdlet to create a dynamic module in memory.</span></span> <span data-ttu-id="3f6a3-131">이 모듈에서는 승인되지 않은 동사 경고를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-131">This module demonstrates the unapproved verb warning.</span></span>

```powershell
New-Module -Name MyModule -ScriptBlock {

    function Return-MrOsVersion {
        Get-CimInstance -ClassName Win32_OperatingSystem |
        Select-Object -Property @{label='OperatingSystem';expression={$_.Caption}}
    }

    Export-ModuleMember -Function Return-MrOsVersion

} | Import-Module
```

```Output
WARNING: The names of some imported commands from the module 'MyModule' include
unapproved verbs that might make them less discoverable. To find the commands with
unapproved verbs, run the Import-Module command again with the Verbose parameter. For a
list of approved verbs, type Get-Verb.
```

<span data-ttu-id="3f6a3-132">다시 말하지만, 앞의 예제에서 `New-Module` cmdlet을 사용했지만 이것은 PowerShell에서 스크립트 모듈을 만드는 명령은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-132">Just to reiterate, although the `New-Module` cmdlet was used in the previous example, that's not the command for creating script modules in PowerShell.</span></span>

<span data-ttu-id="3f6a3-133">`MyScriptModule.psm1`이라는 파일에 다음 두 함수를 저장하세요.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-133">Save the following two functions in a file named `MyScriptModule.psm1`.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}
```

<span data-ttu-id="3f6a3-134">함수 중 하나를 호출해 보세요.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-134">Try to call one of the functions.</span></span>

```powershell
Get-MrComputerName
```

```Output
Get-MrComputerName : The term 'Get-MrComputerName' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrComputerName
    + CategoryInfo          : ObjectNotFound: (Get-MrComputerName:String) [], CommandNot
   FoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

<span data-ttu-id="3f6a3-135">함수를 찾을 수 없다는 오류 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-135">An error message is generated saying the function can't be found.</span></span> <span data-ttu-id="3f6a3-136">예전처럼 **Function** PSDrive를 확인하면 함수가 여기에도 없다는 사실을 알게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-136">You could also check the **Function** PSDrive just like before and you'll find that it doesn't exist there either.</span></span>

<span data-ttu-id="3f6a3-137">`Import-Module` cmdlet을 사용하면 파일을 수동으로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-137">You could manually import the file with the `Import-Module` cmdlet.</span></span>

```powershell
Import-Module C:\MyScriptModule.psm1
```

<span data-ttu-id="3f6a3-138">모듈 자동 로드 기능은 PowerShell 버전 3에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-138">The module autoloading feature was introduced in PowerShell version 3.</span></span> <span data-ttu-id="3f6a3-139">모듈 자동 로드를 사용하려면 스크립트 모듈을 `.PSM1` 파일과 기본 이름이 같은 폴더에, 그리고 `$env:PSModulePath`에 지정된 위치에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-139">To take advantage of module autoloading, a script module needs to be saved in a folder with the same base name as the `.PSM1` file and in a location specified in `$env:PSModulePath`.</span></span>

```powershell
$env:PSModulePath
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules;C:\Program Files\WindowsPowerShell\
Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules;C:\Program Files (x86)\Microsof
t SQL Server\130\Tools\PowerShell\Modules\
```

<span data-ttu-id="3f6a3-140">결과는 읽기 쉽지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-140">The results are difficult to read.</span></span> <span data-ttu-id="3f6a3-141">경로는 세미콜론으로 구분되므로 결과를 분할하여 각 경로를 개별 줄에서 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-141">Since the paths are separated by a semicolon, you can split the results to return each path on a separate line.</span></span> <span data-ttu-id="3f6a3-142">이렇게 하면 쿼리 가독성이 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-142">This makes them easier to read.</span></span>

```powershell
$env:PSModulePath -split ';'
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules
C:\Program Files\WindowsPowerShell\Modules
C:\Windows\system32\WindowsPowerShell\v1.0\Modules
C:\Program Files (x86)\Microsoft SQL Server\130\Tools\PowerShell\Modules\
```

<span data-ttu-id="3f6a3-143">목록의 처음 세 경로는 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-143">The first three paths in the list are the default.</span></span> <span data-ttu-id="3f6a3-144">SQL Server Management Studio가 설치되었을 때 마지막 경로가 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-144">When SQL Server Management Studio was installed, it added the last path.</span></span> <span data-ttu-id="3f6a3-145">모듈 자동 로드가 작동하려면 `MyScriptModule.psm1` 파일이 세 경로 중 하나 안에 있는 `MyScriptModule`이라는 폴더에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-145">For module autoloading to work, the `MyScriptModule.psm1` file needs to be located in a folder named `MyScriptModule` directly inside one of those paths.</span></span>

<span data-ttu-id="3f6a3-146">아직은 시도하진 마세요.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-146">Not so fast.</span></span> <span data-ttu-id="3f6a3-147">필자의 현재 사용자 경로는 목록의 첫 번째 사용자 경로가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-147">For me, my current user path isn't the first one in the list.</span></span> <span data-ttu-id="3f6a3-148">필자는 PowerShell을 실행할 때 사용하는 것과는 다른 사용자로 Windows에 로그인하므로 이 경로는 거의 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-148">I almost never use that path since I log into Windows with a different user than the one I use to run PowerShell.</span></span> <span data-ttu-id="3f6a3-149">따라서 일반 문서 폴더에 위치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-149">That means it's not located in my normal Documents folder.</span></span>

<span data-ttu-id="3f6a3-150">두 번째 경로는 **AllUsers** 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-150">The second path is the **AllUsers** path.</span></span> <span data-ttu-id="3f6a3-151">전체 모듈을 저장하는 곳입니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-151">This is the location where I store all of my modules.</span></span>

<span data-ttu-id="3f6a3-152">세 번째 경로는 `C:\Windows\System32`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-152">The third path is underneath `C:\Windows\System32`.</span></span> <span data-ttu-id="3f6a3-153">운영 체제 폴더 내에 위치하기 때문에 오직 Microsoft만 이 위치에 모듈을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-153">Only Microsoft should be storing modules in that location since it resides within the operating systems folder.</span></span>

<span data-ttu-id="3f6a3-154">`.PSM1` 파일이 올바른 경로에 위치하면 모듈은 자체 명령 중 하나가 호출될 때 자동으로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-154">Once the `.PSM1` file is located in the correct path, the module will load automatically when one of its commands is called.</span></span>

## <a name="module-manifests"></a><span data-ttu-id="3f6a3-155">모듈 매니페스트</span><span class="sxs-lookup"><span data-stu-id="3f6a3-155">Module Manifests</span></span>

<span data-ttu-id="3f6a3-156">모든 모듈에는 모듈 매니페스트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-156">All modules should have a module manifest.</span></span> <span data-ttu-id="3f6a3-157">모듈 매니페스트에는 모듈 관련 메타데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-157">A module manifest contains metadata about your module.</span></span>
<span data-ttu-id="3f6a3-158">모듈 매니페스트 파일의 파일 확장명은 `.PSD1`입니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-158">The file extension for a module manifest file is `.PSD1`.</span></span> <span data-ttu-id="3f6a3-159">파일 확장명이 `.PSD1`이지만 모듈 매니페스트가 아닌 파일도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-159">Not all files with a `.PSD1` extension are module manifests.</span></span> <span data-ttu-id="3f6a3-160">모듈 매니페스트 파일은 DSC 구성의 환경 부분을 저장하는 등의 작업에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-160">They can also be used for things such as storing the environmental portion of a DSC configuration.</span></span> <span data-ttu-id="3f6a3-161">`New-ModuleManifest`는 모듈 매니페스트를 만드는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-161">`New-ModuleManifest` is used to create a module manifest.</span></span> <span data-ttu-id="3f6a3-162">**Path**는 유일한 필수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-162">**Path** is the only value that's required.</span></span> <span data-ttu-id="3f6a3-163">그러나 **RootModule**이 지정되지 않으면 모듈은 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-163">However, the module won't work if **RootModule** isn't specified.</span></span> <span data-ttu-id="3f6a3-164">모듈을 PowerShellGet을 이용해 NuGet 리포지토리에 업로드하기로 했다면 **Author**와 **Description**을 지정하는 것이 좋습니다. 해당 시나리오에 필요한 값이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-164">It's a good idea to specify **Author** and **Description** in case you decide to upload your module to a NuGet repository with PowerShellGet since those values are required in that scenario.</span></span>

<span data-ttu-id="3f6a3-165">매니페스트가 없는 모듈의 버전은 0.0입니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-165">The version of a module without a manifest is 0.0.</span></span> <span data-ttu-id="3f6a3-166">모듈에 매니페스트가 없다는 확실한 증거입니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-166">This is a dead giveaway that the module doesn't have a manifest.</span></span>

```powershell
Get-Module -Name MyScriptModule
```

```Output
ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Script     0.0        myscriptmodule                      {Get-MrComputerName, Get-MrP...
```

<span data-ttu-id="3f6a3-167">모든 권장 정보를 사용하여 모듈 매니페스트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-167">The module manifest can be created with all of the recommended information.</span></span>

```powershell
New-ModuleManifest -Path $env:ProgramFiles\WindowsPowerShell\Modules\MyScriptModule\MyScriptModule.psd1 -RootModule MyScriptModule -Author 'Mike F Robbins' -Description 'MyScriptModule' -CompanyName 'mikefrobbins.com'
```

<span data-ttu-id="3f6a3-168">모듈 매니페스트를 처음 만들 때 이 정보 중 일부가 누락되었다면 `Update-ModuleManifest`를 이용해 나중에 추가하거나 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-168">If any of this information is missed during the initial creation of the module manifest, it can be added or updated later using `Update-ModuleManifest`.</span></span> <span data-ttu-id="3f6a3-169">`New-ModuleManifest`를 사용하여 만든 매니페스트를 다시 만들면 안 됩니다. GUID가 변경되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-169">Don't recreate the manifest using `New-ModuleManifest` once it's already created because the GUID will change.</span></span>

## <a name="defining-public-and-private-functions"></a><span data-ttu-id="3f6a3-170">퍼블릭 및 프라이빗 함수 정의</span><span class="sxs-lookup"><span data-stu-id="3f6a3-170">Defining Public and Private Functions</span></span>

<span data-ttu-id="3f6a3-171">비공개이며 모듈 내의 다른 함수에서만 액세스할 수 있는 도우미 함수를 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-171">You may have helper functions that you may want to be private and only accessible by other functions within the module.</span></span> <span data-ttu-id="3f6a3-172">모듈의 사용자는 도우미 함수에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-172">They are not intended to be accessible to users of your module.</span></span> <span data-ttu-id="3f6a3-173">이 작업은 두 가지 방법으로 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-173">There are a couple of different ways to accomplish this.</span></span>

<span data-ttu-id="3f6a3-174">모범 사례를 따르지 않으며 `.PSM1` 파일만 있다면 `Export-ModuleMember` cmdlet을 사용하는 방법밖에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-174">If you're not following the best practices and only have a `.PSM1` file, then your only option is to use the `Export-ModuleMember` cmdlet.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}

Export-ModuleMember -Function Get-MrPSVersion
```

<span data-ttu-id="3f6a3-175">이전 예제에서는 모듈의 사용자만 `Get-MrPSVersion` 함수를 사용할 수 있지만 `Get-MrComputerName` 함수는 모듈 내의 다른 함수에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-175">In the previous example, only the `Get-MrPSVersion` function is available to the users of your module, but the `Get-MrComputerName` function is available to other functions within the module itself.</span></span>

```powershell
Get-Command -Module MyScriptModule

CommandType     Name                        Version    Source
-----------     ----                        -------    ------
Function        Get-MrPSVersion             1.0        MyScript...
```

<span data-ttu-id="3f6a3-176">(필수 작업인) 모듈 매니페스트를 모듈에 추가했다면, 모듈 매니페스트의 **FunctionsToExport** 섹션에서 내보낼 개별 함수를 지정하는 방법을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-176">If you've added a module manifest to your module (and you should), then I recommend specifying the individual functions you want to export in the **FunctionsToExport** section of the module manifest.</span></span>

```powershell
FunctionsToExport = 'Get-MrPSVersion'
```

<span data-ttu-id="3f6a3-177">`.PSM1` 파일의 `Export-ModuleMember`와 모듈 매니페이스의 **FunctionsToExport** 섹션을 모두 사용할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-177">It's not necessary to use both `Export-ModuleMember` in the `.PSM1` file and the **FunctionsToExport** section of the module manifest.</span></span> <span data-ttu-id="3f6a3-178">하나만 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-178">One or the other is sufficient.</span></span>

## <a name="summary"></a><span data-ttu-id="3f6a3-179">요약</span><span class="sxs-lookup"><span data-stu-id="3f6a3-179">Summary</span></span>

<span data-ttu-id="3f6a3-180">이 장에서는 함수를 PowerShell의 스크립트 모듈으로 전환하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-180">In this chapter you've learned how to turn your functions into a script module in PowerShell.</span></span> <span data-ttu-id="3f6a3-181">그리고 스크립트 모듈의 모듈 매니페스트를 만드는 작업을 포함한 스크립트 모듈 생성 모범 사례도 확인했습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6a3-181">You've also leaned some of the best practices for creating script modules such as creating a module manifest for your script module.</span></span>

## <a name="review"></a><span data-ttu-id="3f6a3-182">검토</span><span class="sxs-lookup"><span data-stu-id="3f6a3-182">Review</span></span>

1. <span data-ttu-id="3f6a3-183">스크립트 모듈을 만들려면 어떻게 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="3f6a3-183">How do you create a script module in PowerShell?</span></span>
1. <span data-ttu-id="3f6a3-184">함수에서 승인된 동사를 사용하는 것이 왜 중요한가요?</span><span class="sxs-lookup"><span data-stu-id="3f6a3-184">Why is it important for your functions to use an approved verb?</span></span>
1. <span data-ttu-id="3f6a3-185">PowerShell에서 스크립트 모듈을 만들려면 어떻게 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="3f6a3-185">How do you create a module manifest in PowerShell?</span></span>
1. <span data-ttu-id="3f6a3-186">모듈에서 특정 함수만 내보내는 두 가지 방법은 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="3f6a3-186">What are the two options for exporting only certain functions from your module?</span></span>
1. <span data-ttu-id="3f6a3-187">명령이 호출될 때 모듈을 자동으로 로드하려면 어떻게 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="3f6a3-187">What is required for your modules to load automatically when a command is called?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="3f6a3-188">권장 참조 항목</span><span class="sxs-lookup"><span data-stu-id="3f6a3-188">Recommended Reading</span></span>

- <span data-ttu-id="3f6a3-189">[PowerShell 스크립트 모듈 및 모듈 매니페스트를 만드는 방법][]</span><span class="sxs-lookup"><span data-stu-id="3f6a3-189">[How to Create PowerShell Script Modules and Module Manifests][]</span></span>
- <span data-ttu-id="3f6a3-190">[about_Modules][]</span><span class="sxs-lookup"><span data-stu-id="3f6a3-190">[about_Modules][]</span></span>
- <span data-ttu-id="3f6a3-191">[New-ModuleManifest][]</span><span class="sxs-lookup"><span data-stu-id="3f6a3-191">[New-ModuleManifest][]</span></span>
- <span data-ttu-id="3f6a3-192">[Export-ModuleMember][]</span><span class="sxs-lookup"><span data-stu-id="3f6a3-192">[Export-ModuleMember][]</span></span>

<!-- link references -->
[PowerShell 스크립트 모듈 및 모듈 매니페스트를 만드는 방법]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[How to Create PowerShell Script Modules and Module Manifests]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Export-ModuleMember]: /powershell/module/microsoft.powershell.core/export-modulemember
