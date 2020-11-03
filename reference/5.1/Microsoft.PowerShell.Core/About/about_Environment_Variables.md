---
description: PowerShell에서 Windows 환경 변수에 액세스 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Environment_Variables
ms.openlocfilehash: 3004e01e59d30005ad2fbfa92897f43471a41384
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223514"
---
# <a name="about-environment-variables"></a><span data-ttu-id="9abb4-104">환경 변수 정보</span><span class="sxs-lookup"><span data-stu-id="9abb4-104">About Environment Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="9abb4-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="9abb4-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="9abb4-106">PowerShell에서 Windows 환경 변수에 액세스 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-106">Describes how to access Windows environment variables in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="9abb4-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="9abb4-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="9abb4-108">환경 변수는 운영 체제 환경에 대 한 정보를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-108">Environment variables store information about the operating system environment.</span></span> <span data-ttu-id="9abb4-109">이 정보에는 운영 체제 경로, 운영 체제에서 사용 하는 프로세서 수 및 임시 폴더의 위치와 같은 정보가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-109">This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders.</span></span>

<span data-ttu-id="9abb4-110">환경 변수는 운영 체제 및 기타 프로그램에서 사용 하는 데이터를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-110">The environment variables store data that is used by the operating system and other programs.</span></span> <span data-ttu-id="9abb4-111">예를 `WINDIR` 들어 환경 변수는 Windows 설치 디렉터리의 위치를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-111">For example, the `WINDIR` environment variable contains the location of the Windows installation directory.</span></span> <span data-ttu-id="9abb4-112">프로그램은이 변수의 값을 쿼리하여 Windows 운영 체제 파일이 있는 위치를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-112">Programs can query the value of this variable to determine where Windows operating system files are located.</span></span>

<span data-ttu-id="9abb4-113">PowerShell은 지원 되는 운영 체제 플랫폼에서 환경 변수를 액세스 하 고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-113">PowerShell can access and manage environment variables in any of the supported operating system platforms.</span></span> <span data-ttu-id="9abb4-114">PowerShell 환경 공급자는 환경 변수를 쉽게 확인 하 고 변경할 수 있도록 하 여이 프로세스를 간소화 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-114">The PowerShell environment provider simplifies this process by making it easy to view and change environment variables.</span></span>

<span data-ttu-id="9abb4-115">PowerShell의 다른 변수와 달리 환경 변수는 자식 프로세스 (예: 로컬 백그라운드 작업 및 모듈 멤버가 실행 되는 세션)에서 상속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-115">Environment variables, unlike other types of variables in PowerShell, are inherited by child processes, such as local background jobs and the sessions in which module members run.</span></span> <span data-ttu-id="9abb4-116">이렇게 하면 환경 변수가 부모 및 자식 프로세스에 필요한 값을 저장 하는 데 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-116">This makes environment variables well suited to storing values that are needed in both parent and child processes.</span></span>

## <a name="using-and-changing-environment-variables"></a><span data-ttu-id="9abb4-117">환경 변수 사용 및 변경</span><span class="sxs-lookup"><span data-stu-id="9abb4-117">Using and changing environment variables</span></span>

<span data-ttu-id="9abb4-118">Windows에서는 환경 변수를 다음과 같은 세 가지 범위로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-118">On Windows, environment variables can be defined in three scopes:</span></span>

- <span data-ttu-id="9abb4-119">컴퓨터 (또는 시스템) 범위</span><span class="sxs-lookup"><span data-stu-id="9abb4-119">Machine (or System) scope</span></span>
- <span data-ttu-id="9abb4-120">사용자 범위</span><span class="sxs-lookup"><span data-stu-id="9abb4-120">User scope</span></span>
- <span data-ttu-id="9abb4-121">프로세스 범위</span><span class="sxs-lookup"><span data-stu-id="9abb4-121">Process scope</span></span>

<span data-ttu-id="9abb4-122">_프로세스_ 범위는 현재 프로세스 또는 PowerShell 세션에서 사용할 수 있는 환경 변수를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-122">The _Process_ scope contains the environment variables available in the current process, or PowerShell session.</span></span> <span data-ttu-id="9abb4-123">이 변수 목록은 부모 프로세스에서 상속 되며 _컴퓨터_ 및 _사용자_ 범위의 변수에 의해 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-123">This list of variables is inherited from the parent process and is constructed from the variables in the _Machine_ and _User_ scopes.</span></span>

<span data-ttu-id="9abb4-124">환경 공급자와 함께 변수 구문을 사용 하 여 cmdlet을 사용 하지 않고 환경 변수의 값을 표시 하 고 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-124">You can display and change the values of environment variables without using a cmdlet by using a variable syntax with the environment provider.</span></span> <span data-ttu-id="9abb4-125">환경 변수의 값을 표시 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-125">To display the value of an environment variable, use the following syntax:</span></span>

```
$Env:<variable-name>
```

<span data-ttu-id="9abb4-126">예를 들어 환경 변수의 값을 표시 하려면 `WINDIR` PowerShell 명령 프롬프트에서 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-126">For example, to display the value of the `WINDIR` environment variable, type the following command at the PowerShell command prompt:</span></span>

```powershell
$Env:windir
```

<span data-ttu-id="9abb4-127">이 구문에서 달러 기호 ()는 `$` 변수를 나타내고 drive name ()은 `Env:` 환경 변수와 변수 이름 ()을 나타냅니다 `windir` .</span><span class="sxs-lookup"><span data-stu-id="9abb4-127">In this syntax, the dollar sign (`$`) indicates a variable, and the drive name (`Env:`) indicates an environment variable followed by the variable name (`windir`).</span></span>

<span data-ttu-id="9abb4-128">PowerShell에서 환경 변수를 변경 하는 경우 변경 내용은 현재 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-128">When you change environment variables in PowerShell, the change affects only the current session.</span></span> <span data-ttu-id="9abb4-129">이 동작은 `Set` Windows 명령 셸에서 명령의 동작과 비슷하며 `Setenv` UNIX 기반 환경의 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-129">This behavior resembles the behavior of the `Set` command in the Windows Command Shell and the `Setenv` command in UNIX-based environments.</span></span> <span data-ttu-id="9abb4-130">컴퓨터 또는 사용자 범위에서 값을 변경 하려면 **system.object** 클래스의 메서드를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-130">To change values in the Machine or User scopes, you must use the methods of the **System.Environment** class.</span></span>

<span data-ttu-id="9abb4-131">컴퓨터 범위 변수를 변경 하려면에도 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-131">To make changes to Machine-scoped variables, must also have permission.</span></span> <span data-ttu-id="9abb4-132">충분 한 권한이 없는 상태에서 값을 변경 하려고 하면 명령이 실패 하 고 PowerShell에서 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-132">If you try to change a value without sufficient permission, the command fails and PowerShell displays an error.</span></span>

<span data-ttu-id="9abb4-133">다음 구문을 사용 하 여 cmdlet을 사용 하지 않고 변수 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-133">You can change the values of variables without using a cmdlet using the following syntax:</span></span>

```powershell
$Env:<variable-name> = "<new-value>"
```

<span data-ttu-id="9abb4-134">예를 들어 `;c:\temp` 환경 변수 값에를 추가 하려면 `Path` 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-134">For example, to append `;c:\temp` to the value of the `Path` environment variable, use the following syntax:</span></span>

```powershell
$Env:Path += ";c:\temp"
```

<span data-ttu-id="9abb4-135">항목 cmdlet (예:, 및)을 사용 `Set-Item` `Remove-Item` `Copy-Item` 하 여 환경 변수 값을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-135">You can also use the Item cmdlets, such as `Set-Item`, `Remove-Item`, and `Copy-Item` to change the values of environment variables.</span></span> <span data-ttu-id="9abb4-136">예를 들어 cmdlet을 사용 하 여 `Set-Item` `;c:\temp` 환경 변수 값에 추가 하려면 `Path` 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-136">For example, to use the `Set-Item` cmdlet to append `;c:\temp` to the value of the `Path` environment variable, use the following syntax:</span></span>

```powershell
Set-Item -Path Env:Path -Value ($Env:Path + ";C:\Temp")
```

<span data-ttu-id="9abb4-137">이 명령에서 값은 단위로 해석 되도록 괄호로 묶여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-137">In this command, the value is enclosed in parentheses so that it is interpreted as a unit.</span></span>

## <a name="environment-variables-that-store-preferences"></a><span data-ttu-id="9abb4-138">기본 설정을 저장 하는 환경 변수</span><span class="sxs-lookup"><span data-stu-id="9abb4-138">Environment variables that store preferences</span></span>

<span data-ttu-id="9abb4-139">PowerShell 기능은 환경 변수를 사용 하 여 사용자 기본 설정을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-139">PowerShell features can use environment variables to store user preferences.</span></span>
<span data-ttu-id="9abb4-140">이러한 변수는 기본 설정 변수 처럼 작동 하지만 생성 된 세션의 자식 세션에서 상속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-140">These variables work like preference variables, but they are inherited by child sessions of the sessions in which they are created.</span></span> <span data-ttu-id="9abb4-141">기본 설정 변수에 대 한 자세한 내용은 [about_preference_variables](about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9abb4-141">For more information about preference variables, see [about_preference_variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="9abb4-142">기본 설정을 저장 하는 환경 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-142">The environment variables that store preferences include:</span></span>

- <span data-ttu-id="9abb4-143">PSExecutionPolicyPreference</span><span class="sxs-lookup"><span data-stu-id="9abb4-143">PSExecutionPolicyPreference</span></span>

  <span data-ttu-id="9abb4-144">현재 세션에 대 한 실행 정책 집합을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-144">Stores the execution policy set for the current session.</span></span> <span data-ttu-id="9abb4-145">이 환경 변수는 단일 세션에 대 한 실행 정책을 설정 하는 경우에만 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-145">This environment variable exists only when you set an execution policy for a single session.</span></span>
  <span data-ttu-id="9abb4-146">두 가지 방법으로이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-146">You can do this in two different ways.</span></span>

  - <span data-ttu-id="9abb4-147">**Set-executionpolicy** 매개 변수를 사용 하 여 명령줄에서 세션을 시작 하 여 세션에 대 한 실행 정책을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-147">Start a session from the command line using the **ExecutionPolicy** parameter to set the execution policy for the session.</span></span>

  - <span data-ttu-id="9abb4-148">`Set-ExecutionPolicy` cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-148">Use the `Set-ExecutionPolicy` cmdlet.</span></span> <span data-ttu-id="9abb4-149">값이 "Process" 인 Scope 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-149">Use the Scope parameter with a value of "Process".</span></span>

    <span data-ttu-id="9abb4-150">자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9abb4-150">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

- <span data-ttu-id="9abb4-151">PSModuleAnalysisCachePath</span><span class="sxs-lookup"><span data-stu-id="9abb4-151">PSModuleAnalysisCachePath</span></span>

  <span data-ttu-id="9abb4-152">PowerShell에서는 모듈 및 해당 cmdlet에 대 한 데이터를 캐시 하는 데 사용 되는 파일을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-152">PowerShell provides control over the file that is used to cache data about modules and their cmdlets.</span></span> <span data-ttu-id="9abb4-153">명령을 검색 하는 동안 시작할 때 캐시를 읽고 모듈을 가져온 후 백그라운드 스레드에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-153">The cache is read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

  <span data-ttu-id="9abb4-154">캐시의 기본 위치는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-154">Default location of the cache is:</span></span>

  - `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell`

  <span data-ttu-id="9abb4-155">캐시의 기본 파일 이름은 `ModuleAnalysisCache` 입니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-155">The default filename for the cache is `ModuleAnalysisCache`.</span></span> <span data-ttu-id="9abb4-156">캐시의 기본 위치를 변경 하려면 PowerShell을 시작 하기 전에 환경 변수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-156">To change the default location of the cache, set the environment variable before starting PowerShell.</span></span> <span data-ttu-id="9abb4-157">이 환경 변수에 대 한 변경 내용은 자식 프로세스에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-157">Changes to this environment variable only affect child processes.</span></span>
  <span data-ttu-id="9abb4-158">PowerShell이 파일을 만들고 쓸 수 있는 전체 경로(파일 이름 포함)를 값으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-158">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span>

  > [!NOTE]
  > <span data-ttu-id="9abb4-159">명령 검색이 제대로 작동 하지 않는 경우 (예: Intellisense에 존재 하지 않는 명령이 표시 되는 경우) 캐시 파일을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-159">If command discovery isn't working correctly, for example Intellisense shows commands that don't exist, you can delete the cache file.</span></span> <span data-ttu-id="9abb4-160">다음에 PowerShell을 시작할 때 캐시가 다시 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-160">The cache is recreated the next time you start PowerShell.</span></span>

  <span data-ttu-id="9abb4-161">파일 캐시를 사용하지 않도록 설정하려면 이 값을 다음과 같은 잘못된 위치로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-161">To disable the file cache, set this value to an invalid location, for example:</span></span>

  ```powershell
  # `NUL` here is a special device on Windows that cannot be written to
  $env:PSModuleAnalysisCachePath = 'NUL'
  ```

  <span data-ttu-id="9abb4-162">이렇게 하면 **NUL** 장치에 대 한 경로가 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-162">This sets the path to the **NUL** device.</span></span> <span data-ttu-id="9abb4-163">PowerShell에서 경로에 쓸 수 없지만 오류가 반환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-163">PowerShell can't write to the path but no error is returned.</span></span> <span data-ttu-id="9abb4-164">추적 프로그램을 사용 하 여 보고 된 오류를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-164">You can see the errors reported using a tracer:</span></span>

  ```powershell
  Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
  ```

- <span data-ttu-id="9abb4-165">PSDisableModuleAnalysisCacheCleanup</span><span class="sxs-lookup"><span data-stu-id="9abb4-165">PSDisableModuleAnalysisCacheCleanup</span></span>

  <span data-ttu-id="9abb4-166">모듈 분석 캐시를 작성할 때 PowerShell은 불필요 하 게 큰 캐시를 방지 하기 위해 더 이상 존재 하지 않는 모듈을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-166">When writing out the module analysis cache, PowerShell checks for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="9abb4-167">이러한 검사를 사용 하지 않는 것이 좋습니다 .이 경우이 환경 변수 값을로 설정 하 여 해제할 수 있습니다 `1` .</span><span class="sxs-lookup"><span data-stu-id="9abb4-167">Sometimes these checks are not desirable, in which case you can turn them off by setting this environment variable value to `1`.</span></span>

  <span data-ttu-id="9abb4-168">이 환경 변수를 설정 하면 현재 프로세스에 즉시 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-168">Setting this environment variable takes effect immediately in the current process.</span></span>

- <span data-ttu-id="9abb4-169">PSModulePath</span><span class="sxs-lookup"><span data-stu-id="9abb4-169">PSModulePath</span></span>

  <span data-ttu-id="9abb4-170">`$env:PSModulePath`환경 변수는 모듈 및 리소스를 찾기 위해 검색 되는 폴더 위치 목록을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-170">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

  <span data-ttu-id="9abb4-171">기본적으로에 할당 되는 유효 위치는 `$env:PSModulePath` 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-171">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

  - <span data-ttu-id="9abb4-172">시스템 전체 위치: 이러한 폴더에는 PowerShell과 함께 제공 되는 모듈이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-172">System-wide locations: These folders contain modules that ship with PowerShell.</span></span> <span data-ttu-id="9abb4-173">모듈은 위치에 저장 됩니다 `$PSHOME\Modules` .</span><span class="sxs-lookup"><span data-stu-id="9abb4-173">The modules are store in the `$PSHOME\Modules` location.</span></span> <span data-ttu-id="9abb4-174">또한 Windows 관리 모듈이 설치 되는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-174">Also, This is the location where the Windows management modules are installed.</span></span>

  - <span data-ttu-id="9abb4-175">사용자가 설치한 모듈: 사용자가 설치 하는 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-175">User-installed modules: These are modules installed by the user.</span></span>
    <span data-ttu-id="9abb4-176">`Install-Module` 에는 현재 사용자 또는 모든 사용자에 대해 모듈이 설치 되어 있는지 여부를 지정할 수 있는 **범위** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-176">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="9abb4-177">자세한 내용은 [모듈 설치](xref:PowerShellGet.Install-Module)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9abb4-177">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

    - <span data-ttu-id="9abb4-178">Windows에서 사용자 관련 **CurrentUser** 범위의 위치는 `$HOME\Documents\PowerShell\Modules` 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-178">On Windows, the location of the user-specific **CurrentUser** scope is the `$HOME\Documents\PowerShell\Modules` folder.</span></span> <span data-ttu-id="9abb4-179">**AllUsers** 범위의 위치는 `$env:ProgramFiles\PowerShell\Modules` 입니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-179">The location of the **AllUsers** scope is `$env:ProgramFiles\PowerShell\Modules`.</span></span>

  <span data-ttu-id="9abb4-180">또한 Program Files 디렉터리와 같은 다른 디렉터리에 모듈을 설치 하는 설치 프로그램은 해당 위치를의 값에 추가할 수 있습니다 `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="9abb4-180">In addition, setup programs that install modules in other directories, such as the Program Files directory, can append their locations to the value of `$env:PSModulePath`.</span></span>

  <span data-ttu-id="9abb4-181">자세한 내용은 [about_PSModulePath](about_PSModulePath.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9abb4-181">For more information, see [about_PSModulePath](about_PSModulePath.md).</span></span>

## <a name="managing-environment-variables"></a><span data-ttu-id="9abb4-182">환경 변수 관리</span><span class="sxs-lookup"><span data-stu-id="9abb4-182">Managing environment variables</span></span>

<span data-ttu-id="9abb4-183">PowerShell은 환경 변수를 관리 하는 여러 가지 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-183">PowerShell provides several different methods for managing environment variables.</span></span>

- <span data-ttu-id="9abb4-184">환경 공급자 드라이브</span><span class="sxs-lookup"><span data-stu-id="9abb4-184">The Environment provider drive</span></span>
- <span data-ttu-id="9abb4-185">항목 cmdlet</span><span class="sxs-lookup"><span data-stu-id="9abb4-185">The Item cmdlets</span></span>
- <span data-ttu-id="9abb4-186">.NET **System. Environment** 클래스</span><span class="sxs-lookup"><span data-stu-id="9abb4-186">The .NET **System.Environment** class</span></span>
- <span data-ttu-id="9abb4-187">Windows에서 시스템 제어판</span><span class="sxs-lookup"><span data-stu-id="9abb4-187">On Windows, the System Control Panel</span></span>

### <a name="using-the-environment-provider"></a><span data-ttu-id="9abb4-188">환경 공급자 사용</span><span class="sxs-lookup"><span data-stu-id="9abb4-188">Using the Environment provider</span></span>

<span data-ttu-id="9abb4-189">각 환경 변수는 **DictionaryEntry** 클래스의 인스턴스로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-189">Each environment variable is represented by an instance of the **System.Collections.DictionaryEntry** class.</span></span> <span data-ttu-id="9abb4-190">각 **DictionaryEntry** 개체에서 환경 변수의 이름은 사전 키입니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-190">In each **DictionaryEntry** object, the name of the environment variable is the dictionary key.</span></span> <span data-ttu-id="9abb4-191">변수 값은 사전 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-191">The value of the variable is the dictionary value.</span></span>

<span data-ttu-id="9abb4-192">PowerShell에서 환경 변수를 나타내는 개체의 속성 및 메서드를 표시 하려면 cmdlet을 사용 합니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="9abb4-192">To display the properties and methods of the object that represents an environment variable in PowerShell, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="9abb4-193">예를 들어 드라이브의 모든 개체에 대 한 메서드 및 속성을 표시 하려면 `Env:` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-193">For example, to display the methods and properties of all the objects in the `Env:` drive, type:</span></span>

```powershell
Get-Item -Path Env:* | Get-Member
```

<span data-ttu-id="9abb4-194">PowerShell 환경 공급자를 통해 PowerShell 드라이브 (드라이브)의 환경 변수에 액세스할 수 있습니다 `Env:` .</span><span class="sxs-lookup"><span data-stu-id="9abb4-194">The PowerShell Environment provider lets you access environment variables in a PowerShell drive (the `Env:` drive).</span></span> <span data-ttu-id="9abb4-195">이 드라이브는 파일 시스템 드라이브와 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-195">This drive looks much like a file system drive.</span></span> <span data-ttu-id="9abb4-196">드라이브로 이동 하려면 `Env:` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-196">To go to the `Env:` drive, type:</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="9abb4-197">콘텐츠 cmdlet을 사용 하 여 환경 변수 값을 가져오거나 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-197">Use the Content cmdlets to get or set the values of an environment variable.</span></span>

```powershell
PS Env:\> Set-Content -Path Test -Value 'Test value'
PS Env:\> Get-Content -Path Test
Test value
```

<span data-ttu-id="9abb4-198">다른 PowerShell 드라이브에서 드라이브의 환경 변수를 볼 수 있으며 `Env:` , `Env:` 드라이브로 이동 하 여 환경 변수를 확인 하 고 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-198">You can view the environment variables in the `Env:` drive from any other PowerShell drive, and you can go into the `Env:` drive to view and change the environment variables.</span></span>

### <a name="using-item-cmdlets"></a><span data-ttu-id="9abb4-199">항목 cmdlet 사용</span><span class="sxs-lookup"><span data-stu-id="9abb4-199">Using Item cmdlets</span></span>

<span data-ttu-id="9abb4-200">환경 변수를 참조 하는 경우 `Env:` 드라이브 이름 뒤에 변수 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-200">When you refer to an environment variable, type the `Env:` drive name followed by the name of the variable.</span></span> <span data-ttu-id="9abb4-201">예를 들어 환경 변수의 값을 표시 하려면 `COMPUTERNAME` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-201">For example, to display the value of the `COMPUTERNAME` environment variable, type:</span></span>

```powershell
Get-ChildItem Env:Computername
```

<span data-ttu-id="9abb4-202">모든 환경 변수의 값을 표시 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-202">To display the values of all the environment variables, type:</span></span>

```powershell
Get-ChildItem Env:
```

<span data-ttu-id="9abb4-203">환경 변수에는 자식 항목이 없으므로 및의 출력은 `Get-Item` `Get-ChildItem` 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-203">Because environment variables do not have child items, the output of `Get-Item` and `Get-ChildItem` is the same.</span></span>

<span data-ttu-id="9abb4-204">기본적으로 PowerShell은 검색 되는 순서 대로 환경 변수를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-204">By default, PowerShell displays the environment variables in the order in which it retrieves them.</span></span> <span data-ttu-id="9abb4-205">환경 변수 목록을 변수 이름별로 정렬 하려면 명령의 출력을 `Get-ChildItem` cmdlet으로 파이프 합니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="9abb4-205">To sort the list of environment variables by variable name, pipe the output of a `Get-ChildItem` command to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="9abb4-206">예를 들어 모든 PowerShell 드라이브에서 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-206">For example, from any PowerShell drive, type:</span></span>

```powershell
Get-ChildItem Env: | Sort Name
```

<span data-ttu-id="9abb4-207">`Env:`Cmdlet을 사용 하 여 드라이브로 이동할 수도 있습니다 `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="9abb4-207">You can also go into the `Env:` drive by using the `Set-Location` cmdlet:</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="9abb4-208">드라이브에 있는 경우 `Env:` `Env:` 경로에서 드라이브 이름을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-208">When you are in the `Env:` drive, you can omit the `Env:` drive name from the path.</span></span> <span data-ttu-id="9abb4-209">예를 들어 모든 환경 변수를 표시 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-209">For example, to display all the environment variables, type:</span></span>

```powershell
PS Env:\> Get-ChildItem
```

<span data-ttu-id="9abb4-210">`COMPUTERNAME`드라이브 내에서 변수의 값을 표시 하려면 `Env:` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-210">To display the value of the `COMPUTERNAME` variable from within the `Env:` drive, type:</span></span>

```powershell
PS Env:\> Get-ChildItem ComputerName
```

### <a name="saving-changes-to-environment-variables"></a><span data-ttu-id="9abb4-211">환경 변수에 대 한 변경 내용 저장</span><span class="sxs-lookup"><span data-stu-id="9abb4-211">Saving changes to environment variables</span></span>

<span data-ttu-id="9abb4-212">Windows에서 환경 변수를 영구적으로 변경 하려면 시스템 제어판을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-212">To make a persistent change to an environment variable on Windows, use the System Control Panel.</span></span> <span data-ttu-id="9abb4-213">**고급 시스템 설정** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-213">Select **Advanced System Settings**.</span></span> <span data-ttu-id="9abb4-214">**고급** 탭에서 **환경 변수 ...** 를 클릭 합니다. **사용자** 및 **시스템** (컴퓨터) 범위에서 기존 환경 변수를 추가 하거나 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-214">On the **Advanced** tab, click **Environment Variable...**. You can add or edit existing environment variables in the **User** and **System** (Machine) scopes.</span></span> <span data-ttu-id="9abb4-215">Windows는 세션 및 시스템 다시 시작 간에 유지 되도록 레지스트리에 이러한 값을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-215">Windows writes these values to the Registry so that they persist across sessions and system restarts.</span></span>

<span data-ttu-id="9abb4-216">또는 PowerShell 프로필에서 환경 변수를 추가 하거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-216">Alternately, you can add or change environment variables in your PowerShell profile.</span></span> <span data-ttu-id="9abb4-217">이 방법은 모든 버전의 PowerShell에서 지원 되는 플랫폼에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-217">This method works for any version of PowerShell on any supported platform.</span></span>

### <a name="using-systemenvironment-methods"></a><span data-ttu-id="9abb4-218">System.object 메서드 사용</span><span class="sxs-lookup"><span data-stu-id="9abb4-218">Using System.Environment methods</span></span>

<span data-ttu-id="9abb4-219">**System.object** 클래스는 변수의 범위를 지정할 수 있는 **GetEnvironmentVariable** 및 **SetEnvironmentVariable** 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-219">The **System.Environment** class provides **GetEnvironmentVariable** and **SetEnvironmentVariable** methods that allow you to specify the scope of the variable.</span></span>

<span data-ttu-id="9abb4-220">다음 예제에서는 **GetEnvironmentVariable** 메서드를 사용 하 여의 컴퓨터 설정을 가져오고 `PSModulePath` **SetEnvironmentVariable** 메서드를 사용 하 여 `C:\Program Files\Fabrikam\Modules` 값에 경로를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9abb4-220">The following example uses the **GetEnvironmentVariable** method to get the machine setting of `PSModulePath` and the **SetEnvironmentVariable** method to add the `C:\Program Files\Fabrikam\Modules` path to the value.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable("PSModulePath", $newpath, 'Machine')
```

<span data-ttu-id="9abb4-221">**System.object** 클래스의 메서드에 대 한 자세한 내용은 [환경 메서드](/dotnet/api/system.environment)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9abb4-221">For more information about the methods of the **System.Environment** class, see [Environment Methods](/dotnet/api/system.environment).</span></span>

## <a name="see-also"></a><span data-ttu-id="9abb4-222">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9abb4-222">SEE ALSO</span></span>

- [<span data-ttu-id="9abb4-223">환경 (공급자)</span><span class="sxs-lookup"><span data-stu-id="9abb4-223">Environment (provider)</span></span>](../About/about_Environment_Provider.md)
- [<span data-ttu-id="9abb4-224">about_Modules</span><span class="sxs-lookup"><span data-stu-id="9abb4-224">about_Modules</span></span>](about_Modules.md)
