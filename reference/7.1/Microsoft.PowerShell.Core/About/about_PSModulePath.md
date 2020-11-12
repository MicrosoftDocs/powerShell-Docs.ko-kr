---
description: PSModulePath 환경 변수는 모듈 및 리소스를 찾기 위해 검색 되는 폴더 위치 목록을 포함 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_PSModulePath?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSModulePath
ms.openlocfilehash: 580c7a1d61e481448e2f49f62fb7d089922e72b5
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524793"
---
# <a name="about-psmodulepath"></a><span data-ttu-id="c1341-104">PSModulePath 정보</span><span class="sxs-lookup"><span data-stu-id="c1341-104">About PSModulePath</span></span>

<span data-ttu-id="c1341-105">`$env:PSModulePath`환경 변수는 모듈 및 리소스를 찾기 위해 검색 되는 폴더 위치 목록을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-105">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span> <span data-ttu-id="c1341-106">PowerShell은 모듈 (또는) 파일의 각 폴더를 재귀적으로 검색 `.psd1` `.psm1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-106">PowerShell recursively searches each folder for module (`.psd1` or `.psm1`) files.</span></span>

<span data-ttu-id="c1341-107">기본적으로에 할당 되는 유효 위치는 `$env:PSModulePath` 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-107">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

- <span data-ttu-id="c1341-108">시스템 전체 위치: 이러한 폴더에는 PowerShell과 함께 제공 되는 모듈이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-108">System-wide locations: These folders contain modules that ship with PowerShell.</span></span> <span data-ttu-id="c1341-109">이러한 모듈은 폴더에 저장 됩니다 `$PSHOME\Modules` .</span><span class="sxs-lookup"><span data-stu-id="c1341-109">These modules are store in the `$PSHOME\Modules` folder.</span></span> <span data-ttu-id="c1341-110">Windows 관리 모듈이 설치 되는 위치 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-110">This is also the location where the Windows management modules are installed.</span></span>

- <span data-ttu-id="c1341-111">사용자가 설치한 모듈: 사용자가 설치 하는 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-111">User-installed modules: These are modules installed by the user.</span></span>
  <span data-ttu-id="c1341-112">`Install-Module` 에는 현재 사용자 또는 모든 사용자에 대해 모듈이 설치 되어 있는지 여부를 지정할 수 있는 **범위** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-112">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="c1341-113">자세한 내용은 [모듈 설치](xref:PowerShellGet.Install-Module)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c1341-113">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

  - <span data-ttu-id="c1341-114">Windows에서 사용자 관련 **CurrentUser** 범위의 위치는 `$HOME\Documents\PowerShell\Modules` 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-114">On Windows, the location of the user-specific **CurrentUser** scope is the `$HOME\Documents\PowerShell\Modules` folder.</span></span> <span data-ttu-id="c1341-115">**AllUsers** 범위의 위치는 `$env:ProgramFiles\PowerShell\Modules` 입니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-115">The location of the **AllUsers** scope is `$env:ProgramFiles\PowerShell\Modules`.</span></span>
  - <span data-ttu-id="c1341-116">비 Windows 시스템에서 사용자 관련 **CurrentUser** 범위의 위치는 `$HOME/.local/share/powershell/Modules` 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-116">On non-Windows systems, the location of the user-specific **CurrentUser** scope is the `$HOME/.local/share/powershell/Modules` folder.</span></span> <span data-ttu-id="c1341-117">**AllUsers** 범위의 위치는 `/usr/local/share/powershell/Modules` 입니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-117">The location of the **AllUsers** scope is `/usr/local/share/powershell/Modules`.</span></span>

<span data-ttu-id="c1341-118">또한 Program Files 디렉터리와 같은 다른 디렉터리에 모듈을 설치 하는 설치 프로그램은 해당 위치를의 값에 추가할 수 있습니다 `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="c1341-118">In addition, setup programs that install modules in other directories, such as the Program Files directory, can append their locations to the value of `$env:PSModulePath`.</span></span>

> [!NOTE]
> <span data-ttu-id="c1341-119">Windows에서 사용자 지정 위치는 `PowerShell\Modules` 사용자 프로필의 **Documents** 폴더에 있는 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-119">On Windows, the user-specific location is the `PowerShell\Modules` folder located in the **Documents** folder in your user profile.</span></span> <span data-ttu-id="c1341-120">해당 위치의 특정 경로는 Windows의 버전에 따라 다르며 폴더 리디렉션을 사용 하는지 여부에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-120">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="c1341-121">Microsoft OneDrive는 **문서** 폴더의 위치를 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-121">Microsoft OneDrive can also change the location of your **Documents** folder.</span></span> <span data-ttu-id="c1341-122">다음 명령을 사용 하 여 **문서** 폴더의 위치를 확인할 수 있습니다 `[Environment]::GetFolderPath('MyDocuments')` .</span><span class="sxs-lookup"><span data-stu-id="c1341-122">You can verify the location of your **Documents** folder using the following command: `[Environment]::GetFolderPath('MyDocuments')`.</span></span>

## <a name="modifying-psmodulepath"></a><span data-ttu-id="c1341-123">PSModulePath 수정</span><span class="sxs-lookup"><span data-stu-id="c1341-123">Modifying PSModulePath</span></span>

<span data-ttu-id="c1341-124">현재 세션에 대 한 기본 모듈 디렉터리를 변경 하려면 다음 명령 형식을 사용 하 여 환경 변수 값을 변경 합니다 `PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="c1341-124">To change the default module directories for the current session, use the following command format to change the value of the `PSModulePath` environment variable.</span></span>

<span data-ttu-id="c1341-125">예를 들어 `C:\Program Files\Fabrikam\Modules` PSModulePath 환경 변수의 값에 디렉터리를 추가 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-125">For example, to add the `C:\Program Files\Fabrikam\Modules` directory to the value of the PSModulePath environment variable, type:</span></span>

```powershell
$Env:PSModulePath = $Env:PSModulePath+";C:\Program Files\Fabrikam\Modules"
```

<span data-ttu-id="c1341-126">명령의 세미콜론 ()은 `;` 목록에서 앞에 나오는 경로와 새 경로를 분리 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-126">The semi-colon (`;`) in the command separates the new path from the path that precedes it in the list.</span></span> <span data-ttu-id="c1341-127">Windows가 아닌 플랫폼에서 콜론 ()은 `:` 환경 변수의 경로 위치를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-127">On non-Windows platforms, the colon (`:`) separates the path locations in the environment variable.</span></span>

<span data-ttu-id="c1341-128">모든 세션에서의 값을 변경 하려면 `PSModulePath` PowerShell 프로필에 이전 명령을 추가 하거나 **Environment** 클래스의 **SetEnvironmentVariable** 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-128">To change the value of `PSModulePath` in every session, add the previous command to your PowerShell profile or use the **SetEnvironmentVariable** method of the **Environment** class.</span></span>

<span data-ttu-id="c1341-129">다음 명령은 **GetEnvironmentVariable** 메서드를 사용 하 여의 컴퓨터 설정을 가져오고 SetEnvironmentVariable 메서드를 사용 하 여 `PSModulePath` **SetEnvironmentVariable** `C:\Program Files\Fabrikam\Modules` 값에 경로를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-129">The following command uses the **GetEnvironmentVariable** method to get the machine setting of `PSModulePath` and the **SetEnvironmentVariable** method to add the `C:\Program Files\Fabrikam\Modules` path to the value.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'Machine')
```

<span data-ttu-id="c1341-130">사용자 설정에 대 한 경로를 추가 하려면 대상 값을 **사용자** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-130">To add a path to the user setting, change the target value to **User**.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'User')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'User')
```

<span data-ttu-id="c1341-131">**System.object** 클래스의 메서드에 대 한 자세한 내용은 [환경 메서드](/dotnet/api/system.environment)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c1341-131">For more information about the methods of the **System.Environment** class, see [Environment Methods](/dotnet/api/system.environment).</span></span>

## <a name="powershell-psmodulepath-construction"></a><span data-ttu-id="c1341-132">PowerShell PSModulePath 생성</span><span class="sxs-lookup"><span data-stu-id="c1341-132">PowerShell PSModulePath construction</span></span>

<span data-ttu-id="c1341-133">값은 `$env:PSModulePath` PowerShell이 시작 될 때마다 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-133">The value of `$env:PSModulePath` is constructed each time PowerShell starts.</span></span>
<span data-ttu-id="c1341-134">값은 PowerShell의 버전 및 실행 방법에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-134">The value varies by version of PowerShell and how it is launched.</span></span>

### <a name="windows-powershell-startup"></a><span data-ttu-id="c1341-135">Windows PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="c1341-135">Windows PowerShell startup</span></span>

<span data-ttu-id="c1341-136">Windows PowerShell은 다음 논리를 사용 하 여 `PSModulePath` 시작 시를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-136">Windows PowerShell uses the following logic to construct the `PSModulePath` at startup:</span></span>

- <span data-ttu-id="c1341-137">`PSModulePath`존재 하지 않는 경우 **CurrentUser** , **AllUsers** 및 `$PSHOME` modules 경로를 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-137">If `PSModulePath` doesn't exist, combine **CurrentUser** , **AllUsers** , and the `$PSHOME` modules paths</span></span>
- <span data-ttu-id="c1341-138">`PSModulePath`존재 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="c1341-138">If `PSModulePath` does exist:</span></span>
  - <span data-ttu-id="c1341-139">가 `PSModulePath` 모듈 경로를 포함 하는 경우 `$PSHOME` :</span><span class="sxs-lookup"><span data-stu-id="c1341-139">If `PSModulePath` contains `$PSHOME` modules path:</span></span>
    - <span data-ttu-id="c1341-140">모듈 경로 앞에 **AllUsers** 모듈 경로가 삽입 됨 `$PSHOME`</span><span class="sxs-lookup"><span data-stu-id="c1341-140">**AllUsers** modules path is inserted before `$PSHOME` modules path</span></span>
  - <span data-ttu-id="c1341-141">사람이</span><span class="sxs-lookup"><span data-stu-id="c1341-141">else:</span></span>
    - <span data-ttu-id="c1341-142">`PSModulePath`사용자가 의도적으로 위치를 제거 했기 때문에 정의 된 대로만 사용 `$PSHOME`</span><span class="sxs-lookup"><span data-stu-id="c1341-142">Just use `PSModulePath` as defined since the user deliberately removed the `$PSHOME` location</span></span>

<span data-ttu-id="c1341-143">**CurrentUser** 모듈 경로에는 사용자 범위가 없는 경우에만 접두사로 추가 됩니다 `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="c1341-143">The **CurrentUser** module path is prefixed only if User scope `$env:PSModulePath` doesn't exist.</span></span> <span data-ttu-id="c1341-144">그렇지 않으면 사용자 범위가 `$env:PSModulePath` 정의 된 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-144">Otherwise, the User scope `$env:PSModulePath` is used as defined.</span></span>

### <a name="powershell-core-6-startup"></a><span data-ttu-id="c1341-145">PowerShell Core 6 시작</span><span class="sxs-lookup"><span data-stu-id="c1341-145">PowerShell Core 6 startup</span></span>

<span data-ttu-id="c1341-146">Powershell Core 6은 `$env:PSModulePath` powershell에서 시작 된 것을 감지 하는 경우 콘텐츠를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-146">PowerShell Core 6 doesn't use contents of `$env:PSModulePath` if it detects it was started from PowerShell.</span></span> <span data-ttu-id="c1341-147">다음을 사용 하 여 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-147">It overwrites it with:</span></span>

- <span data-ttu-id="c1341-148">**CurrentUser** 모듈 경로 + **AllUsers** 모듈 경로 + `$PSHOME` 모듈 경로 + Windows PowerShell `$PSHOME` 모듈 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-148">**CurrentUser** modules path + **AllUsers** modules path + `$PSHOME` modules path + Windows PowerShell `$PSHOME` modules path.</span></span>

### <a name="powershell-7-startup"></a><span data-ttu-id="c1341-149">PowerShell 7 시작</span><span class="sxs-lookup"><span data-stu-id="c1341-149">PowerShell 7 startup</span></span>

<span data-ttu-id="c1341-150">Windows에서 대부분의 환경 변수에 대해 사용자 범위 변수가 존재 하는 경우 새 프로세스는 동일한 이름의 컴퓨터 범위 변수가 있는 경우에도 해당 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-150">In Windows, for most environment variables, if the User-scoped variable exists, a new process uses that value only even if a Machine-scoped variable of the same name exists.</span></span>

<span data-ttu-id="c1341-151">PowerShell 7에서 `PSModulePath` 는 `Path` 환경 변수가 Windows에서 처리 되는 방식과 유사 하 게 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-151">In PowerShell 7, `PSModulePath` is treated similar to how the `Path` environment variable is treated on Windows.</span></span> <span data-ttu-id="c1341-152">Windows에서 `Path` 는 다른 환경 변수와 다르게 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-152">On Windows, `Path` is treated differently from other environment variables.</span></span> <span data-ttu-id="c1341-153">프로세스가 시작 되 면 Windows는 사용자 범위를 `Path` 컴퓨터 범위와 결합 합니다 `Path` .</span><span class="sxs-lookup"><span data-stu-id="c1341-153">When a process is started, Windows combines the User-scoped `Path` with the Machine-scoped `Path`.</span></span>

- <span data-ttu-id="c1341-154">사용자 범위를 검색 합니다. `PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="c1341-154">Retrieve the User-scoped `PSModulePath`</span></span>
- <span data-ttu-id="c1341-155">상속 된 환경 변수를 처리 하는 비교 `PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="c1341-155">Compare to process inherited `PSModulePath` environment variable</span></span>
  - <span data-ttu-id="c1341-156">동일한 경우:</span><span class="sxs-lookup"><span data-stu-id="c1341-156">If the same:</span></span>
    - <span data-ttu-id="c1341-157">**AllUsers** `PSModulePath` 환경 변수의 의미 체계에 따라 끝에 AllUsers를 추가 합니다. `Path`</span><span class="sxs-lookup"><span data-stu-id="c1341-157">Append the **AllUsers** `PSModulePath` to the end following the semantics of the `Path` environment variable</span></span>
    - <span data-ttu-id="c1341-158">Windows `System32` 경로는 정의 된 컴퓨터에서 제공 `PSModulePath` 되므로 명시적으로 추가할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-158">The Windows `System32` path comes from the machine defined `PSModulePath` so does not need to be added explicitly</span></span>
  - <span data-ttu-id="c1341-159">다른 경우 사용자가 명시적으로 수정 하 고 **AllUsers** 를 추가 하지 않는 것으로 처리 합니다. `PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="c1341-159">If different, treat as though user explicitly modified it and don't append **AllUsers** `PSModulePath`</span></span>
- <span data-ttu-id="c1341-160">PS7 사용자, 시스템 및 `$PSHOME` 경로를 해당 순서로 접두사로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-160">Prefix with PS7 User, System, and `$PSHOME` paths in that order</span></span>
  - <span data-ttu-id="c1341-161">이 `powershell.config.json` 사용자 범위를 포함 하는 경우 `PSModulePath` 사용자에 대 한 기본값 대신 해당 사용자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-161">If `powershell.config.json` contains a user scoped `PSModulePath`, use that instead of the default for the user</span></span>
  - <span data-ttu-id="c1341-162">`powershell.config.json`에 시스템 범위가 포함 된 경우 `PSModulePath` 시스템에 대 한 기본값 대신이를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-162">If `powershell.config.json` contains a system scoped `PSModulePath`, use that instead of the default for the system</span></span>

<span data-ttu-id="c1341-163">Unix 시스템은 사용자 및 시스템 환경 변수를 분리 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-163">Unix systems don't have a separation of User and System environment variables.</span></span>
<span data-ttu-id="c1341-164">`PSModulePath` 는 상속 되며 PS7 경로는 접두사가 아직 정의 되지 않은 경우 접두사로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-164">`PSModulePath` is inherited and the PS7-specific paths are prefixed if not already defined.</span></span>

### <a name="starting-windows-powershell-from-powershell-7"></a><span data-ttu-id="c1341-165">PowerShell 7에서 Windows PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="c1341-165">Starting Windows PowerShell from PowerShell 7</span></span>

<span data-ttu-id="c1341-166">이 설명에서 _Windows PowerShell_ 은 및를 모두 의미 `powershell.exe` `powershell_ise.exe` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-166">For this discussion, _Windows PowerShell_ means both `powershell.exe` and `powershell_ise.exe`.</span></span>

<span data-ttu-id="c1341-167">의 값은 `$env:PSModulePath` 다음 수정 사항을 사용 하 여에 복사 됩니다 `WinPSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="c1341-167">The value of `$env:PSModulePath` is copied to `WinPSModulePath` with the following modifications:</span></span>

- <span data-ttu-id="c1341-168">PS7 사용자 모듈 경로를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-168">Remove PS7 the User module path</span></span>
- <span data-ttu-id="c1341-169">시스템 모듈 경로 PS7 제거</span><span class="sxs-lookup"><span data-stu-id="c1341-169">Remove PS7 the System module path</span></span>
- <span data-ttu-id="c1341-170">PS7 모듈 경로를 제거 합니다. `$PSHOME`</span><span class="sxs-lookup"><span data-stu-id="c1341-170">Remove PS7 the `$PSHOME` module path</span></span>

<span data-ttu-id="c1341-171">PS7 모듈이 Windows PowerShell에서 로드 되지 않도록 PS7 경로가 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-171">The PS7 paths are removed so that PS7 modules don't get loaded in Windows PowerShell.</span></span> <span data-ttu-id="c1341-172">`WinPSModulePath`Windows PowerShell을 시작할 때이 값이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-172">The `WinPSModulePath` value is used when starting Windows PowerShell.</span></span>

### <a name="starting-powershell-7-from-windows-powershell"></a><span data-ttu-id="c1341-173">Windows PowerShell에서 PowerShell 7 시작</span><span class="sxs-lookup"><span data-stu-id="c1341-173">Starting PowerShell 7 from Windows PowerShell</span></span>

<span data-ttu-id="c1341-174">PowerShell 7 시작은 Windows PowerShell에서 추가한 경로를 상속 하는 것과 함께 그대로 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-174">The PowerShell 7 startup continues as-is with the addition of inheriting paths that Windows PowerShell added.</span></span> <span data-ttu-id="c1341-175">PS7 경로는 접두사로 지정 되므로 기능 문제가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-175">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

### <a name="starting-powershell-6-from-powershell-7"></a><span data-ttu-id="c1341-176">PowerShell 7에서 PowerShell 6 시작</span><span class="sxs-lookup"><span data-stu-id="c1341-176">Starting PowerShell 6 from PowerShell 7</span></span>

<span data-ttu-id="c1341-177">PowerShell Core 6은 `$env:PSModulePath` 를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-177">PowerShell Core 6 overwrites `$env:PSModulePath`.</span></span> <span data-ttu-id="c1341-178">변경 내용이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-178">No changes are made.</span></span>

### <a name="starting-powershell-7-from-powershell-6"></a><span data-ttu-id="c1341-179">PowerShell 6에서 PowerShell 7 시작</span><span class="sxs-lookup"><span data-stu-id="c1341-179">Starting PowerShell 7 from PowerShell 6</span></span>

<span data-ttu-id="c1341-180">Powershell 7 시작은 PowerShell Core 6이 추가 된 상속 경로를 추가 하 여 그대로 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-180">The PowerShell 7 startup continues as-is with the addition of inheriting paths that PowerShell Core 6 added.</span></span> <span data-ttu-id="c1341-181">PS7 경로는 접두사로 지정 되므로 기능 문제가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-181">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

## <a name="module-search-behavior"></a><span data-ttu-id="c1341-182">모듈 검색 동작</span><span class="sxs-lookup"><span data-stu-id="c1341-182">Module search behavior</span></span>

<span data-ttu-id="c1341-183">PowerShell은 모듈 (또는) 파일에 대 한 **PSModulePath** 의 각 폴더를 재귀적으로 검색 `.psd1` `.psm1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-183">PowerShell recursively searches each folder in the **PSModulePath** for module (`.psd1` or `.psm1`) files.</span></span> <span data-ttu-id="c1341-184">이 검색 패턴을 사용 하면 동일한 모듈의 여러 버전을 서로 다른 폴더에 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-184">This search pattern allows multiple versions of the same module to be installed in different folders.</span></span> <span data-ttu-id="c1341-185">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="c1341-185">For example:</span></span>

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules\PowerShellGet

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----           8/14/2020  5:56 PM                1.0.0.1
d----           9/13/2019  3:53 PM                2.1.2
```

<span data-ttu-id="c1341-186">기본적으로 PowerShell은 여러 버전이 발견 될 때 모듈의 가장 높은 버전 번호를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-186">By default, PowerShell loads the highest version number of a module when multiple versions are found.</span></span> <span data-ttu-id="c1341-187">특정 버전을 로드 하려면 `Import-Module` **FullyQualifiedName** 매개 변수와 함께를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1341-187">To load a specific version, use `Import-Module` with the **FullyQualifiedName** parameter.</span></span> <span data-ttu-id="c1341-188">자세한 내용은 [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c1341-188">For more information, see [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module).</span></span>

## <a name="see-also"></a><span data-ttu-id="c1341-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c1341-189">See also</span></span>

- [<span data-ttu-id="c1341-190">about_Modules</span><span class="sxs-lookup"><span data-stu-id="c1341-190">about_Modules</span></span>](about_Modules.md)
- [<span data-ttu-id="c1341-191">환경 메서드</span><span class="sxs-lookup"><span data-stu-id="c1341-191">Environment Methods</span></span>](/dotnet/api/system.environment)
