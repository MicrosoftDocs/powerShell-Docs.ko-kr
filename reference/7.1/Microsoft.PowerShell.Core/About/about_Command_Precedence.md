---
description: PowerShell에서 실행할 명령을 결정 하는 방법에 대해 설명 합니다.
Locale: en-US
ms.date: 02/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_precedence?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Precedence
ms.openlocfilehash: 30822ae18e7edfab2938c4fd697955881f64536d
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103196184"
---
# <a name="about-command-precedence"></a><span data-ttu-id="54004-103">명령 우선 순위 정보</span><span class="sxs-lookup"><span data-stu-id="54004-103">About Command Precedence</span></span>

## <a name="short-description"></a><span data-ttu-id="54004-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="54004-104">Short description</span></span>
<span data-ttu-id="54004-105">PowerShell에서 실행할 명령을 결정 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-105">Describes how PowerShell determines which command to run.</span></span>

## <a name="long-description"></a><span data-ttu-id="54004-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="54004-106">Long description</span></span>

<span data-ttu-id="54004-107">명령 우선 순위는 세션에 동일한 이름의 명령이 두 개 이상 포함 된 경우 PowerShell에서 실행할 명령을 결정 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-107">Command precedence describes how PowerShell determines which command to run when a session contains more than one command with the same name.</span></span> <span data-ttu-id="54004-108">세션 내의 명령은 동일한 이름의 명령으로 숨겨지거나 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-108">Commands within a session can be hidden or replaced by commands with the same name.</span></span> <span data-ttu-id="54004-109">이 문서에서는 숨겨진 명령 실행 방법과 명령 이름 충돌을 방지 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="54004-109">This article shows you how to run hidden commands and how to avoid command-name conflicts.</span></span>

## <a name="command-precedence"></a><span data-ttu-id="54004-110">명령 우선 순위</span><span class="sxs-lookup"><span data-stu-id="54004-110">Command precedence</span></span>

<span data-ttu-id="54004-111">PowerShell 세션에 동일한 이름의 명령이 두 개 이상 포함 된 경우 PowerShell은 다음 규칙을 사용 하 여 실행할 명령을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-111">When a PowerShell session includes more than one command that has the same name, PowerShell determines which command to run by using the following rules.</span></span>

<span data-ttu-id="54004-112">명령에 대 한 경로를 지정 하는 경우 PowerShell은 경로에 지정 된 위치에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-112">If you specify the path to a command, PowerShell runs the command at the location specified by the path.</span></span>

<span data-ttu-id="54004-113">예를 들어 다음 명령은 "C: TechDocs" 디렉터리에서 FindDocs.ps1 스크립트를 실행 합니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="54004-113">For example, the following command runs the FindDocs.ps1 script in the "C:\\TechDocs" directory:</span></span>

```
C:\TechDocs\FindDocs.ps1
```

<span data-ttu-id="54004-114">Powershell은 경로 환경 변수에 나열 된 경로에 명령이 없거나 `$env:path` 스크립트 파일의 경로를 지정 하지 않은 경우 powershell 스크립트를 포함 하 여 실행 파일 (네이티브) 명령을 실행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-114">As a security feature, PowerShell does not run executable (native) commands, including PowerShell scripts, unless the command is located in a path that is listed in the Path environment variable `$env:path` or unless you specify the path to the script file.</span></span>

<span data-ttu-id="54004-115">현재 디렉터리에 있는 스크립트를 실행 하려면 전체 경로를 지정 하거나 현재 디렉터리를 나타내는 점을 입력 합니다 `.\` .</span><span class="sxs-lookup"><span data-stu-id="54004-115">To run a script that is in the current directory, specify the full path, or type a dot `.\` to represent the current directory.</span></span>

<span data-ttu-id="54004-116">예를 들어 현재 디렉터리에서 FindDocs.ps1 파일을 실행 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-116">For example, to run the FindDocs.ps1 file in the current directory, type:</span></span>

```
.\FindDocs.ps1
```

### <a name="using-wildcards-in-execution"></a><span data-ttu-id="54004-117">실행 시 와일드 카드 사용</span><span class="sxs-lookup"><span data-stu-id="54004-117">Using wildcards in execution</span></span>

<span data-ttu-id="54004-118">명령 실행에서 와일드 카드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-118">You may use wildcards in command execution.</span></span> <span data-ttu-id="54004-119">와일드 카드 문자를 사용 하는 것을 *와일드 카드 사용* 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-119">Using wildcard characters is also known as *globbing*.</span></span>

<span data-ttu-id="54004-120">PowerShell은 리터럴 일치를 위해 와일드 카드와 일치 하는 파일을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-120">PowerShell executes a file that has a wildcard match, before a literal match.</span></span>

<span data-ttu-id="54004-121">예를 들어 다음과 같은 파일을 포함 하는 디렉터리를 생각해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-121">For example, consider a directory with the following files:</span></span>

```
Get-ChildItem C:\temp\test


    Directory: C:\temp\test


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        5/20/2019   2:29 PM             28 a.ps1
-a----        5/20/2019   2:29 PM             28 [a1].ps1
```

<span data-ttu-id="54004-122">두 스크립트 파일의 내용이 동일 합니다. `$MyInvocation.MyCommand.Path` .</span><span class="sxs-lookup"><span data-stu-id="54004-122">Both script files have the same content: `$MyInvocation.MyCommand.Path`.</span></span>
<span data-ttu-id="54004-123">이 명령은 호출 되는 스크립트의 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-123">This command displays the name of the script that is invoked.</span></span>

<span data-ttu-id="54004-124">를 실행 하면 `[a1].ps1` `a.ps1` 파일이 리터럴 일치 이더라도 파일이 실행 됩니다 `[a1].ps1` .</span><span class="sxs-lookup"><span data-stu-id="54004-124">When you run `[a1].ps1`, the file `a.ps1` is executed even though the file `[a1].ps1` is a literal match.</span></span>

```powershell
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\a.ps1
```

<span data-ttu-id="54004-125">이제 파일을 삭제 `a.ps1` 하 고 다시 실행 해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="54004-125">Now let's delete the `a.ps1` file and attempt to run it again.</span></span>

```powershell
Remove-Item C:\temp\test\a.ps1
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\[a1].ps1
```

<span data-ttu-id="54004-126">`[a1].ps1`리터럴 일치가 해당 와일드 카드 패턴과 일치 하는 유일한 파일 이기 때문에이 시간을 실행 하는 출력에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-126">You can see from the output that `[a1].ps1` runs this time because the literal match is the only file match for that wildcard pattern.</span></span>

<span data-ttu-id="54004-127">PowerShell에서 와일드 카드를 사용 하는 방법에 대 한 자세한 내용은 [about_Wildcards](about_Wildcards.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="54004-127">For more information about how PowerShell uses wildcards, see [about_Wildcards](about_Wildcards.md).</span></span>

> [!NOTE]
> <span data-ttu-id="54004-128">검색을 상대 경로로 제한 하려면 스크립트 이름 앞에 경로를 붙여야 합니다 `.\` .</span><span class="sxs-lookup"><span data-stu-id="54004-128">To limit the search to a relative path, you must prefix the script name with the `.\` path.</span></span> <span data-ttu-id="54004-129">이렇게 하면 해당 상대 경로에 있는 파일에 대 한 명령 검색을 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-129">This limits the search for commands to files in that relative path.</span></span> <span data-ttu-id="54004-130">이 접두사가 없으면 다른 PowerShell 구문이 충돌 하 고 파일을 찾을 수 있도록 보장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54004-130">Without this prefix, other PowerShell syntax may conflict and there are few guarantees that the file will be found.</span></span>

<span data-ttu-id="54004-131">경로를 지정 하지 않으면 PowerShell은 현재 세션에 로드 된 모든 항목에 대해 명령을 실행할 때 다음과 같은 우선 순위 순서를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-131">If you do not specify a path, PowerShell uses the following precedence order when it runs commands for all items loaded in the current session:</span></span>

  1. <span data-ttu-id="54004-132">Alias</span><span class="sxs-lookup"><span data-stu-id="54004-132">Alias</span></span>
  2. <span data-ttu-id="54004-133">함수</span><span class="sxs-lookup"><span data-stu-id="54004-133">Function</span></span>
  3. <span data-ttu-id="54004-134">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="54004-134">Cmdlet</span></span>
  4. <span data-ttu-id="54004-135">외부 실행 파일 (프로그램 및 비 PowerShell 스크립트)</span><span class="sxs-lookup"><span data-stu-id="54004-135">External executable files (programs and non-PowerShell scripts)</span></span>

<span data-ttu-id="54004-136">따라서 "help"를 입력 하는 경우 PowerShell은 먼저 라는 이름의 별칭을 찾은 다음 라는 함수를 찾은 `help` 다음 `Help` 마지막으로 이라는 cmdlet을 찾습니다 `Help` .</span><span class="sxs-lookup"><span data-stu-id="54004-136">Therefore, if you type "help", PowerShell first looks for an alias named `help`, then a function named `Help`, and finally a cmdlet named `Help`.</span></span> <span data-ttu-id="54004-137">찾은 첫 번째 항목을 실행 `help` 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-137">It runs the first `help` item that it finds.</span></span>

<span data-ttu-id="54004-138">예를 들어 세션에 cmdlet이 포함 되 고 두 함수 모두 명명 된 경우 `Get-Map` `Get-Map` PowerShell에서 함수를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-138">For example, if your session contains a cmdlet and a function, both named `Get-Map`, when you type `Get-Map`, PowerShell runs the function.</span></span>

> [!NOTE]
> <span data-ttu-id="54004-139">이는 로드 된 명령에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54004-139">This only applies to loaded commands.</span></span> <span data-ttu-id="54004-140">`build` `build` 현재 세션으로 로드 되지 않은 모듈 내에 이름이 인 함수에 대 한 실행 파일과 별칭이 있으면 `Invoke-Build` PowerShell에서 실행 파일을 대신 실행 합니다 `build` .</span><span class="sxs-lookup"><span data-stu-id="54004-140">If there is a `build` executable and an Alias `build` for a function with the name of `Invoke-Build` inside a module that is not loaded into the current session, PowerShell runs the `build` executable instead.</span></span> <span data-ttu-id="54004-141">이 경우 외부 실행 파일을 찾으면 모듈을 자동으로 로드 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-141">It does not auto-load modules if it finds the external executable in this case.</span></span> <span data-ttu-id="54004-142">지정 된 이름의 별칭, 함수 또는 cmdlet을 호출 하 여 모듈의 자동 로드를 트리거하는 외부 실행 파일이 없는 경우에만 해당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54004-142">It is only when no external executable is found that an alias, function, or cmdlet with the given name is invoked, thereby triggering auto-loading of its module.</span></span>

<span data-ttu-id="54004-143">세션에 이름이 같은 동일한 유형의 항목이 포함 되어 있으면 PowerShell에서 최신 항목을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-143">When the session contains items of the same type that have the same name, PowerShell runs the newer item.</span></span>

<span data-ttu-id="54004-144">예를 들어 모듈에서 다른 cmdlet을 가져오는 경우 `Get-Date` 를 입력 하면 `Get-Date` PowerShell에서 네이티브 버전을 통해 가져온 버전을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-144">For example, if you import another `Get-Date` cmdlet from a module, when you type `Get-Date`, PowerShell runs the imported version over the native one.</span></span>

## <a name="hidden-and-replaced-items"></a><span data-ttu-id="54004-145">숨겨진 항목과 대체 항목</span><span class="sxs-lookup"><span data-stu-id="54004-145">Hidden and replaced items</span></span>

<span data-ttu-id="54004-146">이러한 규칙의 결과로 항목을 동일한 이름의 항목으로 바꾸거나 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-146">As a result of these rules, items can be replaced or hidden by items with the same name.</span></span>

<span data-ttu-id="54004-147">항목 이름을 모듈 또는 스냅인 이름으로 정규화 하는 등의 방법으로 원래 항목에 액세스할 수 있는 경우 항목은 "숨김" 또는 "숨김" 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="54004-147">Items are "hidden" or "shadowed" if you can still access the original item, such as by qualifying the item name with a module or snap-in name.</span></span>

<span data-ttu-id="54004-148">예를 들어 세션에서 cmdlet과 이름이 동일한 함수를 가져오는 경우이 cmdlet은 스냅인 또는 모듈에서 가져온 것 이기 때문에 숨겨집니다 (대체 되지는 않음).</span><span class="sxs-lookup"><span data-stu-id="54004-148">For example, if you import a function that has the same name as a cmdlet in the session, the cmdlet is hidden (but not replaced) because it was imported from a snap-in or module.</span></span>

<span data-ttu-id="54004-149">원본 항목에 더 이상 액세스할 수 없는 경우 항목은 "교체 됨" 또는 "덮어쓰기" 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54004-149">Items are "replaced" or "overwritten" if you can no longer access the original item.</span></span>

<span data-ttu-id="54004-150">예를 들어 세션의 변수와 이름이 같은 변수를 가져오는 경우 원래 변수가 바뀌고 더 이상 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-150">For example, if you import a variable that has the same name as a variable in the session, the original variable is replaced and is no longer accessible.</span></span>
<span data-ttu-id="54004-151">모듈 이름을 사용 하 여 변수를 한정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-151">You cannot qualify a variable with a module name.</span></span>

<span data-ttu-id="54004-152">또한 명령줄에 함수를 입력 한 다음 동일한 이름의 함수를 가져오면 원래 함수가 바뀌고 더 이상 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-152">Also, if you type a function at the command line and then import a function with the same name, the original function is replaced and is no longer accessible.</span></span>

### <a name="finding-hidden-commands"></a><span data-ttu-id="54004-153">숨겨진 명령 찾기</span><span class="sxs-lookup"><span data-stu-id="54004-153">Finding hidden commands</span></span>

<span data-ttu-id="54004-154">[Get 명령](xref:Microsoft.PowerShell.Core.Get-Command) Cmdlet의 **all** 매개 변수는 숨겨지거나 바뀐 경우에도 지정 된 이름의 모든 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="54004-154">The **All** parameter of the [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) cmdlet gets all commands with the specified name, even if they are hidden or replaced.</span></span> <span data-ttu-id="54004-155">PowerShell 3.0부터 기본적으로 `Get-Command` 명령 이름을 입력할 때 실행 되는 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="54004-155">Beginning in PowerShell 3.0, by default, `Get-Command` gets only the commands that run when you type the command name.</span></span>

<span data-ttu-id="54004-156">다음 예의 세션에는 `Get-Date` 함수와 [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-156">In the following examples, the session includes a `Get-Date` function and a [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet.</span></span>

<span data-ttu-id="54004-157">다음 명령은를 `Get-Date` 입력할 때 실행 되는 명령을 가져옵니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="54004-157">The following command gets the `Get-Date` command that runs when you type `Get-Date`.</span></span>

```powershell
Get-Command Get-Date
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
```

<span data-ttu-id="54004-158">다음 명령은 **all** 매개 변수를 사용 하 여 모든 `Get-Date` 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="54004-158">The following command uses the **All** parameter to get all `Get-Date` commands.</span></span>

```powershell
Get-Command Get-Date -All
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
Cmdlet          Get-Date                  Microsoft.PowerShell.Utility
```

### <a name="running-hidden-commands"></a><span data-ttu-id="54004-159">숨겨진 명령 실행</span><span class="sxs-lookup"><span data-stu-id="54004-159">Running hidden commands</span></span>

<span data-ttu-id="54004-160">동일한 이름을 가질 수 있는 다른 명령과 명령을 구분 하는 항목 속성을 지정 하 여 특정 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-160">You can run particular commands by specifying item properties that distinguish the command from other commands that might have the same name.</span></span> <span data-ttu-id="54004-161">이 메서드를 사용 하 여 모든 명령을 실행할 수 있지만 숨겨진 명령을 실행 하는 데 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-161">You can use this method to run any command, but it is especially useful for running hidden commands.</span></span>

#### <a name="qualified-names"></a><span data-ttu-id="54004-162">정규화된 이름</span><span class="sxs-lookup"><span data-stu-id="54004-162">Qualified names</span></span>

<span data-ttu-id="54004-163">Cmdlet의 모듈 정규화 된 이름을 사용 하면 동일한 이름의 항목으로 숨겨진 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-163">Using the module-qualified name of a cmdlet allows you to run commands hidden by an item with the same name.</span></span> <span data-ttu-id="54004-164">예를 들어 `Get-Date` 이 cmdlet을 모듈 이름으로 정규화 하 여 실행할 수 있습니다 **.**</span><span class="sxs-lookup"><span data-stu-id="54004-164">For example, you can run the `Get-Date` cmdlet by qualifying it with its module name **Microsoft.PowerShell.Utility**.</span></span>

<span data-ttu-id="54004-165">배포 하려는 스크립트를 작성할 때이 기본 방법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-165">Use this preferred method when writing scripts that you intend to distribute.</span></span> <span data-ttu-id="54004-166">스크립트가 실행 되는 세션에 있을 수 있는 명령을 예측할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-166">You cannot predict which commands might be present in the session in which the script runs.</span></span>

```powershell
New-Alias -Name "Get-Date" -Value "Get-ChildItem"
Microsoft.PowerShell.Utility\Get-Date
```

```output
Tuesday, September 4, 2018 8:17:25 AM
```

<span data-ttu-id="54004-167">`New-Map`모듈에 의해 추가 된 명령을 실행 하려면 모듈의 정규화 된 `MapFunctions` 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-167">To run a `New-Map` command that was added by the `MapFunctions` module, use its module-qualified name:</span></span>

```powershell
MapFunctions\New-Map
```

<span data-ttu-id="54004-168">명령을 가져온 모듈을 찾으려면 명령의 **ModuleName** 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-168">To find the module from which a command was imported, use the **ModuleName** property of commands.</span></span>

```
(Get-Command <command-name>).ModuleName
```

<span data-ttu-id="54004-169">예를 들어 cmdlet의 원본을 찾으려면 다음과 같이 `Get-Date` 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-169">For example, to find the source of the `Get-Date` cmdlet, type:</span></span>

```powershell
(Get-Command Get-Date).ModuleName
```

```output
Microsoft.PowerShell.Utility
```

> [!NOTE]
> <span data-ttu-id="54004-170">변수나 별칭은 한정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-170">You cannot qualify variables or aliases.</span></span>

#### <a name="call-operator"></a><span data-ttu-id="54004-171">Call 연산자</span><span class="sxs-lookup"><span data-stu-id="54004-171">Call operator</span></span>

<span data-ttu-id="54004-172">또한 연산자를 사용 `Call` `&` 하 여 숨겨진 명령을 [get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) (별칭은 "Dir") 또는 import-module과 결합 하 여 실행할 수 있습니다 `Get-Command` . [](xref:Microsoft.PowerShell.Core.Get-Module)</span><span class="sxs-lookup"><span data-stu-id="54004-172">You can also use the `Call` operator `&` to run hidden commands by combining it with a call to [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) (the alias is "dir"), `Get-Command` or [Get-Module](xref:Microsoft.PowerShell.Core.Get-Module).</span></span>

<span data-ttu-id="54004-173">Call 연산자는 자식 범위에서 문자열과 스크립트 블록을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-173">The call operator executes strings and script blocks in a child scope.</span></span> <span data-ttu-id="54004-174">자세한 내용은 [about_Operators](about_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="54004-174">For more information, see [about_Operators](about_Operators.md).</span></span>

<span data-ttu-id="54004-175">예를 들어 라는 별칭을 사용 하 여 숨겨진 함수를 사용 하는 경우 `Map` `Map` 다음 명령을 사용 하 여 함수를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-175">For example, if you have a function named `Map` that is hidden by an alias named `Map`, use the following command to run the function.</span></span>

```powershell
&(Get-Command -Name Map -CommandType Function)
```

<span data-ttu-id="54004-176">또는</span><span class="sxs-lookup"><span data-stu-id="54004-176">or</span></span>

```powershell
&(dir Function:\map)
```

<span data-ttu-id="54004-177">숨겨진 명령을 변수에 저장 하 여 쉽게 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-177">You can also save your hidden command in a variable to make it easier to run.</span></span>

<span data-ttu-id="54004-178">예를 들어 다음 명령은 함수를 변수에 저장 한 `Map` `$myMap` 다음 연산자를 사용 하 여 `Call` 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-178">For example, the following command saves the `Map` function in the `$myMap` variable and then uses the `Call` operator to run it.</span></span>

```powershell
$myMap = (Get-Command -Name map -CommandType function)
&($myMap)
```

### <a name="replaced-items"></a><span data-ttu-id="54004-179">바뀐 항목</span><span class="sxs-lookup"><span data-stu-id="54004-179">Replaced items</span></span>

<span data-ttu-id="54004-180">"대체" 항목은 더 이상 액세스할 수 없는 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="54004-180">A "replaced" item is one that you can no longer access.</span></span> <span data-ttu-id="54004-181">모듈 또는 스냅인에서 같은 이름의 항목을 가져와서 항목을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-181">You can replace items by importing items of the same name from a module or snap-in.</span></span>

<span data-ttu-id="54004-182">예를 들어 `Get-Map` 세션에 함수를 입력 하 고 라는 함수를 가져오면 `Get-Map` 원래 함수를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-182">For example, if you type a `Get-Map` function in your session, and you import a function called `Get-Map`, it replaces the original function.</span></span> <span data-ttu-id="54004-183">현재 세션에서 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-183">You cannot retrieve it in the current session.</span></span>

<span data-ttu-id="54004-184">호출 연산자나 정규화 된 이름을 사용 하 여 실행할 수 없으므로 변수와 별칭을 숨길 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="54004-184">Variables and aliases cannot be hidden because you cannot use a call operator or a qualified name to run them.</span></span> <span data-ttu-id="54004-185">모듈 또는 스냅인에서 변수와 별칭을 가져오면 세션의 변수가 동일한 이름으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="54004-185">When you import variables and aliases from a module or snap-in, they replace variables in the session with the same name.</span></span>

### <a name="avoiding-name-conflicts"></a><span data-ttu-id="54004-186">이름 충돌 방지</span><span class="sxs-lookup"><span data-stu-id="54004-186">Avoiding name conflicts</span></span>

<span data-ttu-id="54004-187">명령 이름 충돌을 관리 하는 가장 좋은 방법은이를 방지 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="54004-187">The best way to manage command name conflicts is to prevent them.</span></span> <span data-ttu-id="54004-188">명령의 이름을 사용 하는 경우 고유한 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-188">When you name your commands, use a unique name.</span></span> <span data-ttu-id="54004-189">예를 들어 명령의 명사에 이니셜 또는 회사 이름 머리글자어를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-189">For example, add your initials or company name acronym to the nouns in your commands.</span></span>

<span data-ttu-id="54004-190">또한 PowerShell 모듈 또는 다른 세션에서 세션으로 명령을 가져올 때 `Prefix` [import-module](xref:Microsoft.PowerShell.Core.Import-Module) 또는의 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-190">Also, when you import commands into your session from a PowerShell module or from another session, use the `Prefix` parameter of the [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module) or</span></span>

<span data-ttu-id="54004-191">[가져오기-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession) cmdlet을 통해 명령 이름의 명사에 접두사를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="54004-191">[Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession) cmdlet to add a prefix to the nouns in the names of commands.</span></span>

<span data-ttu-id="54004-192">예를 들어 다음 명령은 `Get-Date` `Set-Date` 모듈을 가져올 때 PowerShell과 함께 제공 되는 및 cmdlet과의 충돌을 방지 합니다 `DateFunctions` .</span><span class="sxs-lookup"><span data-stu-id="54004-192">For example, the following command avoids any conflict with the `Get-Date` and `Set-Date` cmdlets that come with PowerShell when you import the `DateFunctions` module.</span></span>

```powershell
Import-Module -Name DateFunctions -Prefix ZZ
```

<span data-ttu-id="54004-193">자세한 내용은 다음을 참조 `Import-Module` `Import-PSSession` 하세요.</span><span class="sxs-lookup"><span data-stu-id="54004-193">For more information, see `Import-Module` and `Import-PSSession` below.</span></span>

## <a name="see-also"></a><span data-ttu-id="54004-194">참고 항목</span><span class="sxs-lookup"><span data-stu-id="54004-194">See also</span></span>

- [<span data-ttu-id="54004-195">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="54004-195">about_Path_Syntax</span></span>](about_Path_Syntax.md)
- [<span data-ttu-id="54004-196">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="54004-196">about_Aliases</span></span>](about_Aliases.md)
- [<span data-ttu-id="54004-197">about_Functions</span><span class="sxs-lookup"><span data-stu-id="54004-197">about_Functions</span></span>](about_Functions.md)
- [<span data-ttu-id="54004-198">Alias-Provider</span><span class="sxs-lookup"><span data-stu-id="54004-198">Alias-Provider</span></span>](../../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)
- [<span data-ttu-id="54004-199">Function-Provider</span><span class="sxs-lookup"><span data-stu-id="54004-199">Function-Provider</span></span>](../../Microsoft.PowerShell.Core/About/about_Function_Provider.md)
- [<span data-ttu-id="54004-200">Get-Command</span><span class="sxs-lookup"><span data-stu-id="54004-200">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)
- [<span data-ttu-id="54004-201">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="54004-201">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)
- [<span data-ttu-id="54004-202">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="54004-202">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)

