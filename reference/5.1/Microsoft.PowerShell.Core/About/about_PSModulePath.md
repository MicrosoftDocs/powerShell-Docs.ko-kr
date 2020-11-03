---
description: PSModulePath 환경 변수는 모듈 및 리소스를 찾기 위해 검색 되는 폴더 위치 목록을 포함 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_PSModulePath?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSModulePath
ms.openlocfilehash: 60373e534fb319195c187b8cb26c6aabc0f3b8b7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222666"
---
# <a name="about-psmodulepath"></a><span data-ttu-id="9ee4f-104">PSModulePath 정보</span><span class="sxs-lookup"><span data-stu-id="9ee4f-104">About PSModulePath</span></span>

<span data-ttu-id="9ee4f-105">`$env:PSModulePath`환경 변수는 모듈 및 리소스를 찾기 위해 검색 되는 폴더 위치 목록을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-105">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

<span data-ttu-id="9ee4f-106">기본적으로에 할당 되는 유효 위치는 `$env:PSModulePath` 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-106">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

- <span data-ttu-id="9ee4f-107">시스템 전체 위치: 이러한 폴더에는 PowerShell과 함께 제공 되는 모듈이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-107">System-wide locations: These folders contain modules that ship with PowerShell.</span></span> <span data-ttu-id="9ee4f-108">이러한 모듈은 폴더에 저장 됩니다 `$PSHOME\Modules` .</span><span class="sxs-lookup"><span data-stu-id="9ee4f-108">These modules are store in the `$PSHOME\Modules` folder.</span></span> <span data-ttu-id="9ee4f-109">Windows 관리 모듈이 설치 되는 위치 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-109">This is also the location where the Windows management modules are installed.</span></span>

- <span data-ttu-id="9ee4f-110">사용자가 설치한 모듈: 사용자가 설치 하는 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-110">User-installed modules: These are modules installed by the user.</span></span>
  <span data-ttu-id="9ee4f-111">`Install-Module` 에는 현재 사용자 또는 모든 사용자에 대해 모듈이 설치 되어 있는지 여부를 지정할 수 있는 **범위** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-111">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="9ee4f-112">자세한 내용은 [모듈 설치](xref:PowerShellGet.Install-Module)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-112">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

  - <span data-ttu-id="9ee4f-113">Windows에서 사용자 관련 **CurrentUser** 범위의 위치는 `$HOME\Documents\PowerShell\Modules` 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-113">On Windows, the location of the user-specific **CurrentUser** scope is the `$HOME\Documents\PowerShell\Modules` folder.</span></span> <span data-ttu-id="9ee4f-114">**AllUsers** 범위의 위치는 `$env:ProgramFiles\PowerShell\Modules` 입니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-114">The location of the **AllUsers** scope is `$env:ProgramFiles\PowerShell\Modules`.</span></span>
  - <span data-ttu-id="9ee4f-115">비 Windows 시스템에서 사용자 관련 **CurrentUser** 범위의 위치는 `$HOME/.local/share/powershell/Modules` 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-115">On non-Windows systems, the location of the user-specific **CurrentUser** scope is the `$HOME/.local/share/powershell/Modules` folder.</span></span> <span data-ttu-id="9ee4f-116">**AllUsers** 범위의 위치는 `/usr/local/share/powershell/Modules` 입니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-116">The location of the **AllUsers** scope is `/usr/local/share/powershell/Modules`.</span></span>

<span data-ttu-id="9ee4f-117">또한 Program Files 디렉터리와 같은 다른 디렉터리에 모듈을 설치 하는 설치 프로그램은 해당 위치를의 값에 추가할 수 있습니다 `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="9ee4f-117">In addition, setup programs that install modules in other directories, such as the Program Files directory, can append their locations to the value of `$env:PSModulePath`.</span></span>

> [!NOTE]
> <span data-ttu-id="9ee4f-118">Windows에서 사용자 지정 위치는 `PowerShell\Modules` 사용자 프로필의 **Documents** 폴더에 있는 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-118">On Windows, the user-specific location is the `PowerShell\Modules` folder located in the **Documents** folder in your user profile.</span></span> <span data-ttu-id="9ee4f-119">해당 위치의 특정 경로는 Windows의 버전에 따라 다르며 폴더 리디렉션을 사용 하는지 여부에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-119">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="9ee4f-120">Microsoft OneDrive는 **문서** 폴더의 위치를 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-120">Microsoft OneDrive can also change the location of your **Documents** folder.</span></span> <span data-ttu-id="9ee4f-121">다음 명령을 사용 하 여 **문서** 폴더의 위치를 확인할 수 있습니다 `[Environment]::GetFolderPath('MyDocuments')` .</span><span class="sxs-lookup"><span data-stu-id="9ee4f-121">You can verify the location of your **Documents** folder using the following command: `[Environment]::GetFolderPath('MyDocuments')`.</span></span>

## <a name="modifying-psmodulepath"></a><span data-ttu-id="9ee4f-122">PSModulePath 수정</span><span class="sxs-lookup"><span data-stu-id="9ee4f-122">Modifying PSModulePath</span></span>

<span data-ttu-id="9ee4f-123">현재 세션에 대 한 기본 모듈 디렉터리를 변경 하려면 다음 명령 형식을 사용 하 여 환경 변수 값을 변경 합니다 `PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="9ee4f-123">To change the default module directories for the current session, use the following command format to change the value of the `PSModulePath` environment variable.</span></span>

<span data-ttu-id="9ee4f-124">예를 들어 `C:\Program Files\Fabrikam\Modules` PSModulePath 환경 변수의 값에 디렉터리를 추가 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-124">For example, to add the `C:\Program Files\Fabrikam\Modules` directory to the value of the PSModulePath environment variable, type:</span></span>

```powershell
$Env:PSModulePath = $Env:PSModulePath+";C:\Program Files\Fabrikam\Modules"
```

<span data-ttu-id="9ee4f-125">명령의 세미콜론 ()은 `;` 목록에서 앞에 나오는 경로와 새 경로를 분리 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-125">The semi-colon (`;`) in the command separates the new path from the path that precedes it in the list.</span></span> <span data-ttu-id="9ee4f-126">Windows가 아닌 플랫폼에서 콜론 ()은 `:` 환경 변수의 경로 위치를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-126">On non-Windows platforms, the colon (`:`) separates the path locations in the environment variable.</span></span>

<span data-ttu-id="9ee4f-127">모든 세션에서의 값을 변경 하려면 `PSModulePath` PowerShell 프로필에 이전 명령을 추가 하거나 **Environment** 클래스의 **SetEnvironmentVariable** 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-127">To change the value of `PSModulePath` in every session, add the previous command to your PowerShell profile or use the **SetEnvironmentVariable** method of the **Environment** class.</span></span>

<span data-ttu-id="9ee4f-128">다음 명령은 **GetEnvironmentVariable** 메서드를 사용 하 여의 컴퓨터 설정을 가져오고 SetEnvironmentVariable 메서드를 사용 하 여 `PSModulePath` **SetEnvironmentVariable** `C:\Program Files\Fabrikam\Modules` 값에 경로를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-128">The following command uses the **GetEnvironmentVariable** method to get the machine setting of `PSModulePath` and the **SetEnvironmentVariable** method to add the `C:\Program Files\Fabrikam\Modules` path to the value.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'Machine')
```

<span data-ttu-id="9ee4f-129">사용자 설정에 대 한 경로를 추가 하려면 대상 값을 **사용자** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-129">To add a path to the user setting, change the target value to **User**.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'User')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'User')
```

<span data-ttu-id="9ee4f-130">**System.object** 클래스의 메서드에 대 한 자세한 내용은 [환경 메서드](/dotnet/api/system.environment)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-130">For more information about the methods of the **System.Environment** class, see [Environment Methods](/dotnet/api/system.environment).</span></span>

## <a name="powershell-psmodulepath-construction"></a><span data-ttu-id="9ee4f-131">PowerShell PSModulePath 생성</span><span class="sxs-lookup"><span data-stu-id="9ee4f-131">PowerShell PSModulePath construction</span></span>

<span data-ttu-id="9ee4f-132">값은 `$env:PSModulePath` PowerShell이 시작 될 때마다 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-132">The value of `$env:PSModulePath` is constructed each time PowerShell starts.</span></span>
<span data-ttu-id="9ee4f-133">값은 PowerShell의 버전 및 실행 방법에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-133">The value varies by version of PowerShell and how it is launched.</span></span>

### <a name="windows-powershell-startup"></a><span data-ttu-id="9ee4f-134">Windows PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="9ee4f-134">Windows PowerShell startup</span></span>

<span data-ttu-id="9ee4f-135">Windows PowerShell은 다음 논리를 사용 하 여 `PSModulePath` 시작 시를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-135">Windows PowerShell uses the following logic to construct the `PSModulePath` at startup:</span></span>

- <span data-ttu-id="9ee4f-136">`PSModulePath`존재 하지 않는 경우 **CurrentUser** , **AllUsers** 및 `$PSHOME` modules 경로를 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-136">If `PSModulePath` doesn't exist, combine **CurrentUser** , **AllUsers** , and the `$PSHOME` modules paths</span></span>
- <span data-ttu-id="9ee4f-137">`PSModulePath`존재 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="9ee4f-137">If `PSModulePath` does exist:</span></span>
  - <span data-ttu-id="9ee4f-138">가 `PSModulePath` 모듈 경로를 포함 하는 경우 `$PSHOME` :</span><span class="sxs-lookup"><span data-stu-id="9ee4f-138">If `PSModulePath` contains `$PSHOME` modules path:</span></span>
    - <span data-ttu-id="9ee4f-139">모듈 경로 앞에 **AllUsers** 모듈 경로가 삽입 됨 `$PSHOME`</span><span class="sxs-lookup"><span data-stu-id="9ee4f-139">**AllUsers** modules path is inserted before `$PSHOME` modules path</span></span>
  - <span data-ttu-id="9ee4f-140">사람이</span><span class="sxs-lookup"><span data-stu-id="9ee4f-140">else:</span></span>
    - <span data-ttu-id="9ee4f-141">`PSModulePath`사용자가 의도적으로 위치를 제거 했기 때문에 정의 된 대로만 사용 `$PSHOME`</span><span class="sxs-lookup"><span data-stu-id="9ee4f-141">Just use `PSModulePath` as defined since the user deliberately removed the `$PSHOME` location</span></span>

<span data-ttu-id="9ee4f-142">**CurrentUser** 모듈 경로에는 사용자 범위가 없는 경우에만 접두사로 추가 됩니다 `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="9ee4f-142">The **CurrentUser** module path is prefixed only if User scope `$env:PSModulePath` doesn't exist.</span></span> <span data-ttu-id="9ee4f-143">그렇지 않으면 사용자 범위가 `$env:PSModulePath` 정의 된 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-143">Otherwise, the User scope `$env:PSModulePath` is used as defined.</span></span>

### <a name="powershell-core-6-startup"></a><span data-ttu-id="9ee4f-144">PowerShell Core 6 시작</span><span class="sxs-lookup"><span data-stu-id="9ee4f-144">PowerShell Core 6 startup</span></span>

<span data-ttu-id="9ee4f-145">Powershell Core 6은 `$env:PSModulePath` powershell에서 시작 된 것을 감지 하는 경우 콘텐츠를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-145">PowerShell Core 6 doesn't use contents of `$env:PSModulePath` if it detects it was started from PowerShell.</span></span> <span data-ttu-id="9ee4f-146">다음을 사용 하 여 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-146">It overwrites it with:</span></span>

- <span data-ttu-id="9ee4f-147">**CurrentUser** 모듈 경로 + **AllUsers** 모듈 경로 + `$PSHOME` 모듈 경로 + Windows PowerShell `$PSHOME` 모듈 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-147">**CurrentUser** modules path + **AllUsers** modules path + `$PSHOME` modules path + Windows PowerShell `$PSHOME` modules path.</span></span>

### <a name="powershell-7-startup"></a><span data-ttu-id="9ee4f-148">PowerShell 7 시작</span><span class="sxs-lookup"><span data-stu-id="9ee4f-148">PowerShell 7 startup</span></span>

<span data-ttu-id="9ee4f-149">Windows에서 대부분의 환경 변수에 대해 사용자 범위 변수가 존재 하는 경우 새 프로세스는 동일한 이름의 컴퓨터 범위 변수가 있는 경우에도 해당 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-149">In Windows, for most environment variables, if the User-scoped variable exists, a new process uses that value only even if a Machine-scoped variable of the same name exists.</span></span>

<span data-ttu-id="9ee4f-150">PowerShell 7에서 `PSModulePath` 는 `Path` 환경 변수가 Windows에서 처리 되는 방식과 유사 하 게 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-150">In PowerShell 7, `PSModulePath` is treated similar to how the `Path` environment variable is treated on Windows.</span></span> <span data-ttu-id="9ee4f-151">Windows에서 `Path` 는 다른 환경 변수와 다르게 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-151">On Windows, `Path` is treated differently from other environment variables.</span></span> <span data-ttu-id="9ee4f-152">프로세스가 시작 되 면 Windows는 사용자 범위를 `Path` 컴퓨터 범위와 결합 합니다 `Path` .</span><span class="sxs-lookup"><span data-stu-id="9ee4f-152">When a process is started, Windows combines the User-scoped `Path` with the Machine-scoped `Path`.</span></span>

- <span data-ttu-id="9ee4f-153">사용자 범위를 검색 합니다. `PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="9ee4f-153">Retrieve the User-scoped `PSModulePath`</span></span>
- <span data-ttu-id="9ee4f-154">상속 된 환경 변수를 처리 하는 비교 `PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="9ee4f-154">Compare to process inherited `PSModulePath` environment variable</span></span>
  - <span data-ttu-id="9ee4f-155">동일한 경우:</span><span class="sxs-lookup"><span data-stu-id="9ee4f-155">If the same:</span></span>
    - <span data-ttu-id="9ee4f-156">**AllUsers** `PSModulePath` 환경 변수의 의미 체계에 따라 끝에 AllUsers를 추가 합니다. `Path`</span><span class="sxs-lookup"><span data-stu-id="9ee4f-156">Append the **AllUsers** `PSModulePath` to the end following the semantics of the `Path` environment variable</span></span>
    - <span data-ttu-id="9ee4f-157">Windows `System32` 경로는 정의 된 컴퓨터에서 제공 `PSModulePath` 되므로 명시적으로 추가할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-157">The Windows `System32` path comes from the machine defined `PSModulePath` so does not need to be added explicitly</span></span>
  - <span data-ttu-id="9ee4f-158">다른 경우 사용자가 명시적으로 수정 하 고 **AllUsers** 를 추가 하지 않는 것으로 처리 합니다. `PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="9ee4f-158">If different, treat as though user explicitly modified it and don't append **AllUsers** `PSModulePath`</span></span>
- <span data-ttu-id="9ee4f-159">PS7 사용자, 시스템 및 `$PSHOME` 경로를 해당 순서로 접두사로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-159">Prefix with PS7 User, System, and `$PSHOME` paths in that order</span></span>
  - <span data-ttu-id="9ee4f-160">이 `powershell.config.json` 사용자 범위를 포함 하는 경우 `PSModulePath` 사용자에 대 한 기본값 대신 해당 사용자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-160">If `powershell.config.json` contains a user scoped `PSModulePath`, use that instead of the default for the user</span></span>
  - <span data-ttu-id="9ee4f-161">`powershell.config.json`에 시스템 범위가 포함 된 경우 `PSModulePath` 시스템에 대 한 기본값 대신이를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-161">If `powershell.config.json` contains a system scoped `PSModulePath`, use that instead of the default for the system</span></span>

<span data-ttu-id="9ee4f-162">Unix 시스템은 사용자 및 시스템 환경 변수를 분리 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-162">Unix systems don't have a separation of User and System environment variables.</span></span>
<span data-ttu-id="9ee4f-163">`PSModulePath` 는 상속 되며 PS7 경로는 접두사가 아직 정의 되지 않은 경우 접두사로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-163">`PSModulePath` is inherited and the PS7-specific paths are prefixed if not already defined.</span></span>

### <a name="starting-windows-powershell-from-powershell-7"></a><span data-ttu-id="9ee4f-164">PowerShell 7에서 Windows PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="9ee4f-164">Starting Windows PowerShell from PowerShell 7</span></span>

<span data-ttu-id="9ee4f-165">이 설명에서 _Windows PowerShell_ 은 및를 모두 의미 `powershell.exe` `powershell_ise.exe` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-165">For this discussion, _Windows PowerShell_ means both `powershell.exe` and `powershell_ise.exe`.</span></span>

<span data-ttu-id="9ee4f-166">의 값은 `$env:PSModulePath` 다음 수정 사항을 사용 하 여에 복사 됩니다 `WinPSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="9ee4f-166">The value of `$env:PSModulePath` is copied to `WinPSModulePath` with the following modifications:</span></span>

- <span data-ttu-id="9ee4f-167">PS7 사용자 모듈 경로를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-167">Remove PS7 the User module path</span></span>
- <span data-ttu-id="9ee4f-168">시스템 모듈 경로 PS7 제거</span><span class="sxs-lookup"><span data-stu-id="9ee4f-168">Remove PS7 the System module path</span></span>
- <span data-ttu-id="9ee4f-169">PS7 모듈 경로를 제거 합니다. `$PSHOME`</span><span class="sxs-lookup"><span data-stu-id="9ee4f-169">Remove PS7 the `$PSHOME` module path</span></span>

<span data-ttu-id="9ee4f-170">PS7 모듈이 Windows PowerShell에서 로드 되지 않도록 PS7 경로가 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-170">The PS7 paths are removed so that PS7 modules don't get loaded in Windows PowerShell.</span></span> <span data-ttu-id="9ee4f-171">`WinPSModulePath`Windows PowerShell을 시작할 때이 값이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-171">The `WinPSModulePath` value is used when starting Windows PowerShell.</span></span>

### <a name="starting-powershell-7-from-windows-powershell"></a><span data-ttu-id="9ee4f-172">Windows PowerShell에서 PowerShell 7 시작</span><span class="sxs-lookup"><span data-stu-id="9ee4f-172">Starting PowerShell 7 from Windows PowerShell</span></span>

<span data-ttu-id="9ee4f-173">PowerShell 7 시작은 Windows PowerShell에서 추가한 경로를 상속 하는 것과 함께 그대로 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-173">The PowerShell 7 startup continues as-is with the addition of inheriting paths that Windows PowerShell added.</span></span> <span data-ttu-id="9ee4f-174">PS7 경로는 접두사로 지정 되므로 기능 문제가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-174">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

### <a name="starting-powershell-6-from-powershell-7"></a><span data-ttu-id="9ee4f-175">PowerShell 7에서 PowerShell 6 시작</span><span class="sxs-lookup"><span data-stu-id="9ee4f-175">Starting PowerShell 6 from PowerShell 7</span></span>

<span data-ttu-id="9ee4f-176">PowerShell Core 6은 `$env:PSModulePath` 를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-176">PowerShell Core 6 overwrites `$env:PSModulePath`.</span></span> <span data-ttu-id="9ee4f-177">변경 내용이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-177">No changes are made.</span></span>

### <a name="starting-powershell-7-from-powershell-6"></a><span data-ttu-id="9ee4f-178">PowerShell 6에서 PowerShell 7 시작</span><span class="sxs-lookup"><span data-stu-id="9ee4f-178">Starting PowerShell 7 from PowerShell 6</span></span>

<span data-ttu-id="9ee4f-179">Powershell 7 시작은 PowerShell Core 6이 추가 된 상속 경로를 추가 하 여 그대로 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-179">The PowerShell 7 startup continues as-is with the addition of inheriting paths that PowerShell Core 6 added.</span></span> <span data-ttu-id="9ee4f-180">PS7 경로는 접두사로 지정 되므로 기능 문제가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ee4f-180">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ee4f-181">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ee4f-181">See also</span></span>

- [<span data-ttu-id="9ee4f-182">about_Modules</span><span class="sxs-lookup"><span data-stu-id="9ee4f-182">about_Modules</span></span>](about_Modules.md)
- [<span data-ttu-id="9ee4f-183">환경 메서드</span><span class="sxs-lookup"><span data-stu-id="9ee4f-183">Environment Methods</span></span>](/dotnet/api/system.environment)
