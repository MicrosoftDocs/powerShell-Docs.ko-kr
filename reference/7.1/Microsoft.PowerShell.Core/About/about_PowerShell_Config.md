---
description: 레지스트리 구성을 대체 하는 PowerShell Core에 대 한 구성 파일입니다.
keywords: PowerShell
Locale: en-US
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Config
ms.openlocfilehash: fd4467845cf2b895401a55cbb7abd88b7b72af76
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222017"
---
# <a name="about-powershell-config"></a><span data-ttu-id="586c4-104">PowerShell 구성 정보</span><span class="sxs-lookup"><span data-stu-id="586c4-104">About PowerShell Config</span></span>

## <a name="short-description"></a><span data-ttu-id="586c4-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="586c4-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="586c4-106">레지스트리 구성을 대체 하는 PowerShell Core에 대 한 구성 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-106">Configuration files for PowerShell Core, replacing Registry configuration.</span></span>

## <a name="long-description"></a><span data-ttu-id="586c4-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="586c4-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="586c4-108">이 `powershell.config.json` 파일에는 PowerShell Core에 대 한 구성 설정이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-108">The `powershell.config.json` file contains configuration settings for PowerShell Core.</span></span> <span data-ttu-id="586c4-109">PowerShell은 시작할 때이 구성을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-109">PowerShell loads this configuration at startup.</span></span> <span data-ttu-id="586c4-110">설정은 런타임에 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-110">The settings can also be modified at runtime.</span></span> <span data-ttu-id="586c4-111">이전에는 이러한 설정이 PowerShell 용 Windows 레지스트리에 저장 되었지만 이제 macOS 및 Linux에서 구성을 사용 하기 위해 파일에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-111">Previously, these settings were stored in the Windows Registry for PowerShell, but are now contained in a file to enable configuration on macOS and Linux.</span></span>

> [!WARNING]
> <span data-ttu-id="586c4-112">파일에 `powershell.config.json` 잘못 된 JSON이 포함 된 경우 PowerShell은 대화형 세션을 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-112">If the `powershell.config.json` file contains invalid JSON PowerShell cannot start an interactive session.</span></span>
> <span data-ttu-id="586c4-113">이 경우 구성 파일을 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-113">If this occurs, you must fix the configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="586c4-114">구성 파일의 인식할 수 없는 키 또는 잘못 된 값은 자동으로 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-114">Unrecognized keys or invalid values in the configuration file will be silently ignored.</span></span>

### <a name="allusers-shared-configuration"></a><span data-ttu-id="586c4-115">AllUsers (공유) 구성</span><span class="sxs-lookup"><span data-stu-id="586c4-115">AllUsers (shared) configuration</span></span>

<span data-ttu-id="586c4-116">`powershell.config.json`디렉터리의 파일은 `$PSHOME` 해당 powershell core 설치에서 실행 되는 모든 powershell core 세션의 구성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-116">A `powershell.config.json` file in the `$PSHOME` directory defines the configuration for all PowerShell Core sessions running from that PowerShell Core installation.</span></span>

> [!NOTE]
> <span data-ttu-id="586c4-117">`$PSHOME`위치는 실행 중인 System.Management.Automation.dll 어셈블리와 동일한 디렉터리로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-117">The `$PSHOME` location is defined as the same directory as the executing System.Management.Automation.dll assembly.</span></span> <span data-ttu-id="586c4-118">이는 호스트 된 PowerShell SDK 인스턴스에도 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-118">This applies to hosted PowerShell SDK instances as well.</span></span>

### <a name="currentuser-per-user-configurations"></a><span data-ttu-id="586c4-119">CurrentUser (사용자 단위) 구성</span><span class="sxs-lookup"><span data-stu-id="586c4-119">CurrentUser (per-user) configurations</span></span>

<span data-ttu-id="586c4-120">사용자 범위 구성 디렉터리에 파일을 배치 하 여 사용자 별로 PowerShell을 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-120">You can also configure PowerShell on a per-user basis by placing the file in the user-scope configuration directory.</span></span> <span data-ttu-id="586c4-121">명령을 사용 하 여 플랫폼에서 사용자 구성 디렉터리를 찾을 수 있습니다 `Split-Path $PROFILE.CurrentUserCurrentHost` .</span><span class="sxs-lookup"><span data-stu-id="586c4-121">The user configuration directory can be found across platforms with the command `Split-Path $PROFILE.CurrentUserCurrentHost`.</span></span>

## <a name="general-configuration-settings"></a><span data-ttu-id="586c4-122">일반 구성 설정</span><span class="sxs-lookup"><span data-stu-id="586c4-122">General configuration settings</span></span>

### <a name="executionpolicy"></a><span data-ttu-id="586c4-123">ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="586c4-123">ExecutionPolicy</span></span>

> [!IMPORTANT]
> <span data-ttu-id="586c4-124">이 구성은 Windows 플랫폼에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-124">This configuration only applies on Windows platforms.</span></span>

<span data-ttu-id="586c4-125">PowerShell 세션에 대 한 실행 정책을 구성 하 여 실행할 수 있는 스크립트를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-125">Configures the execution policy for PowerShell sessions, determining what scripts can be run.</span></span> <span data-ttu-id="586c4-126">기본적으로 PowerShell은 기존 실행 정책을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-126">By default, PowerShell uses the existing execution policy.</span></span>

<span data-ttu-id="586c4-127">AllUsers 구성의 경우이는 **LocalMachine** 실행 정책을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-127">For AllUsers configurations, this sets the **LocalMachine** execution policy.</span></span>
<span data-ttu-id="586c4-128">CurrentUser 구성의 경우 **currentuser** 실행 정책을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-128">For CurrentUser configurations, this sets the **CurrentUser** execution policy.</span></span>

> [!NOTE]
> <span data-ttu-id="586c4-129">Cmdlet은를 사용 하 여 [`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy) 호출할 때 AllUsers 구성 파일에서이 설정을 수정 `-Scope LocalMachine` 하 고를 사용 하 여 호출할 때 CurrentUser 구성 파일에서이 설정을 수정 `-Scope CurrentUser` 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-129">The [`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy) cmdlet modifies this setting in the AllUsers configuration file when invoked with `-Scope LocalMachine`, and modifies this setting in the CurrentUser configuration file when invoked with `-Scope CurrentUser`.</span></span>

```Schema
"<shell-id>:ExecutionPolicy": "<execution-policy>"
```

<span data-ttu-id="586c4-130">위치:</span><span class="sxs-lookup"><span data-stu-id="586c4-130">Where:</span></span>

- <span data-ttu-id="586c4-131">`<shell-id>` 현재 PowerShell 호스트의 ID를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-131">`<shell-id>` refers to the ID of the current PowerShell host.</span></span>
  <span data-ttu-id="586c4-132">일반적인 PowerShell Core의 경우 `Microsoft.PowerShell` 입니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-132">For normal PowerShell Core, this is `Microsoft.PowerShell`.</span></span>
  <span data-ttu-id="586c4-133">PowerShell 세션에서를 사용 하 여 검색할 수 있습니다 `$ShellId` .</span><span class="sxs-lookup"><span data-stu-id="586c4-133">In any PowerShell session, you can discover it with `$ShellId`.</span></span>
- <span data-ttu-id="586c4-134">`<execution-policy>` 가 유효한 실행 정책 이름을 참조 하는 경우</span><span class="sxs-lookup"><span data-stu-id="586c4-134">`<execution-policy>` refers to a valid execution policy name.</span></span>

<span data-ttu-id="586c4-135">다음 예에서는 PowerShell의 실행 정책을로 설정 합니다 `RemoteSigned` .</span><span class="sxs-lookup"><span data-stu-id="586c4-135">The following example sets the execution policy of PowerShell to `RemoteSigned`.</span></span>

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "RemoteSigned"
}
```

<span data-ttu-id="586c4-136">Windows에서는 및의에서 해당 하는 레지스트리 키를 찾을 수 있습니다 `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` `HKEY_LOCAL_MACHINE` `HKEY_CURRENT_USER` .</span><span class="sxs-lookup"><span data-stu-id="586c4-136">In Windows, the equivalent registry keys can be found in `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` under `HKEY_LOCAL_MACHINE` and `HKEY_CURRENT_USER`.</span></span>

### <a name="psmodulepath"></a><span data-ttu-id="586c4-137">PSModulePath</span><span class="sxs-lookup"><span data-stu-id="586c4-137">PSModulePath</span></span>

<span data-ttu-id="586c4-138">이 PowerShell 세션에 대해 PSModulePath 구성 요소를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-138">Overrides a PSModulePath component for this PowerShell session.</span></span> <span data-ttu-id="586c4-139">현재 사용자에 대 한 구성 인 경우 CurrentUser 모듈 경로를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-139">If the configuration is for the current user, sets the CurrentUser module path.</span></span> <span data-ttu-id="586c4-140">모든 사용자 용으로 구성 된 경우에는 AllUser 모듈 경로를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-140">If the configuration is for all users, sets the AllUser module path.</span></span>

> [!WARNING]
> <span data-ttu-id="586c4-141">여기에서 AllUsers 또는 CurrentUser 모듈 경로를 구성 해도 PowerShellGet 모듈에 대 한 범위가 지정 된 설치 위치 (예: [Install-module)](/powershell/module/powershellget/install-module)는 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-141">Configuring an AllUsers or CurrentUser module path here will not change the scoped installation location for PowerShellGet modules like [Install-Module](/powershell/module/powershellget/install-module).</span></span>
> <span data-ttu-id="586c4-142">이러한 cmdlet은 항상 *기본* 모듈 경로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-142">These cmdlets always use the *default* module paths.</span></span>

<span data-ttu-id="586c4-143">값을 설정 하지 않으면 해당 모듈 경로 구성 요소의 기본값이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-143">If no value is set, the default value for the respective module path component will be used.</span></span> <span data-ttu-id="586c4-144">이러한 기본값에 대 한 자세한 내용은 [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="586c4-144">See [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath) for more details on these defaults.</span></span>

<span data-ttu-id="586c4-145">이 설정을 사용 하면 CMD에서 허용 하는 것과 `%` 같은 방식으로 환경 변수를 문자 간에 포함 하 여 사용할 수 있습니다 `"%HOME%\Documents\PowerShell\Modules"` .</span><span class="sxs-lookup"><span data-stu-id="586c4-145">This setting allows environment variables to be used by embedding them between `%` characters, like `"%HOME%\Documents\PowerShell\Modules"`, in the same way as CMD allows.</span></span> <span data-ttu-id="586c4-146">이 구문은 Linux 및 macOS에도 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-146">This syntax also applies on Linux and macOS.</span></span> <span data-ttu-id="586c4-147">예제는 아래를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="586c4-147">See below for examples.</span></span>

```Schema
"PSModulePath": "<ps-module-path>"
```

<span data-ttu-id="586c4-148">위치:</span><span class="sxs-lookup"><span data-stu-id="586c4-148">Where:</span></span>

- <span data-ttu-id="586c4-149">`<ps-module-path>` 는 모듈 디렉터리의 절대 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-149">`<ps-module-path>` is the absolute path to a module directory.</span></span> <span data-ttu-id="586c4-150">모든 사용자 구성에서는 AllUsers 공유 모듈 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-150">For all user configurations, this is the AllUsers shared module directory.</span></span> <span data-ttu-id="586c4-151">현재 사용자 구성의 경우 CurrentUser 모듈 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-151">For current user configurations, this is CurrentUser module directory.</span></span>

<span data-ttu-id="586c4-152">이 예제에서는 Windows 환경에 대 한 PSModulePath 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-152">This example shows a PSModulePath configuration for a Windows environment:</span></span>

```json
{
  "PSModulePath": "C:\\Program Files\\PowerShell\\6\\Modules"
}
```

<span data-ttu-id="586c4-153">이 예제에서는 macOS 또는 Linux 환경에 대 한 PSModulePath 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-153">This example shows a PSModulePath configuration for a macOS or Linux environment:</span></span>

```json
{
  "PSModulePath": "/opt/powershell/6/Modules"
}
```

<span data-ttu-id="586c4-154">이 예제에서는 PSModulePath 구성에 환경 변수를 포함 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-154">This example shows embedding an environment variable in a PSModulePath configuration.</span></span> <span data-ttu-id="586c4-155">`HOME`환경 변수와 `/` 디렉터리 구분 기호를 사용 하면 Windows, macos 및 Linux에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-155">Note that using the `HOME` environment variable and the `/` directory separator, this will work on Windows, macOS and Linux.</span></span>

```json
{
  "PSModulePath": "%HOME%/Documents/PowerShell/Modules"
}
```

<span data-ttu-id="586c4-156">이 예제에서는 macOS 및 Linux 에서만 작동 하는 PSModulePath 구성에 환경 변수를 포함 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-156">This example shows embedding an environment variable in a PSModulePath configuration that will only work on macOS and Linux:</span></span>

```json
{
  "PSModulePath": "%XDG_CONFIG_HOME%/powershell/Modules"
}
```

> [!NOTE]
> <span data-ttu-id="586c4-157">PowerShell 변수는 PSModulePath 구성에 포함 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-157">PowerShell variables cannot be embedded in PSModulePath configurations.</span></span>
> <span data-ttu-id="586c4-158">Linux 및 macOS에 대 한 PSModulePath 구성은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-158">PSModulePath configurations on Linux and macOS are case-sensitive.</span></span> <span data-ttu-id="586c4-159">PSModulePath 구성에서는 플랫폼에 대해 올바른 디렉터리 구분 기호를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-159">A PSModulePath configuration must use valid directory separators for the platform.</span></span> <span data-ttu-id="586c4-160">MacOS 및 Linux에서이는를 의미 `/` 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-160">On macOS and Linux, this means `/`.</span></span> <span data-ttu-id="586c4-161">Windows에서는 `/` 및가 모두 `\` 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-161">On Windows, both `/` and `\` will work.</span></span>

### <a name="experimentalfeatures"></a><span data-ttu-id="586c4-162">ExperimentalFeatures</span><span class="sxs-lookup"><span data-stu-id="586c4-162">ExperimentalFeatures</span></span>

<span data-ttu-id="586c4-163">PowerShell에서 사용할 수 있는 실험적 기능의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-163">The names of the experimental features to enable in PowerShell.</span></span>
<span data-ttu-id="586c4-164">기본적으로는 실험적 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-164">By default, no experimental features are enabled.</span></span>
<span data-ttu-id="586c4-165">기본값은 빈 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-165">The default value is an empty array.</span></span>

```Schema
"ExperimentalFeatures": ["<experimental-feature-name>", ...]
```

<span data-ttu-id="586c4-166">위치:</span><span class="sxs-lookup"><span data-stu-id="586c4-166">Where:</span></span>

- <span data-ttu-id="586c4-167">`<experimental-feature-name>` 사용할 수 있는 실험적 기능의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-167">`<experimental-feature-name>` is the name of an experimental feature to enable.</span></span>

<span data-ttu-id="586c4-168">다음 예에서는 PowerShell이 시작 될 때 **Psimplicitremoting** 및 **PSUseAbbreviationExpansion** 실험적 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-168">The following example enables the **PSImplicitRemoting** and **PSUseAbbreviationExpansion** experimental features when PowerShell starts up.</span></span>

```json
{
  "ExperimentalFeatures": [
    "PSImplicitRemotingBatching",
    "PSUseAbbreviationExpansion"
  ]
}
```

<span data-ttu-id="586c4-169">실험적 기능에 대 한 자세한 내용은 [POWERSHELL RFC 29][RFC0029]를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="586c4-169">For more information on experimental features, see [PowerShell RFC 29][RFC0029].</span></span>

## <a name="non-windows-logging-configuration"></a><span data-ttu-id="586c4-170">비 Windows 로깅 구성</span><span class="sxs-lookup"><span data-stu-id="586c4-170">Non-Windows logging configuration</span></span>

> [!IMPORTANT]
> <span data-ttu-id="586c4-171">이 섹션의 구성 옵션은 macOS 및 Linux에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-171">The configuration options in this section only apply to macOS and Linux.</span></span>
> <span data-ttu-id="586c4-172">Windows에 대 한 로깅은 Windows 이벤트 뷰어에서 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-172">Logging for Windows is managed by the Windows Event Viewer.</span></span>

<span data-ttu-id="586c4-173">PowerShell 구성 파일에서 macOS 및 Linux에 대 한 PowerShell의 로깅을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-173">PowerShell's logging on macOS and Linux can be configured in the PowerShell configuration file.</span></span> <span data-ttu-id="586c4-174">비 Windows 시스템에 대 한 PowerShell 로깅에 대 한 전체 설명은 [로깅 정보](./about_Logging_Non-Windows.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="586c4-174">For a full description of PowerShell logging for non-Windows systems, see [About Logging](./about_Logging_Non-Windows.md).</span></span>

### <a name="logidentity"></a><span data-ttu-id="586c4-175">LogIdentity</span><span class="sxs-lookup"><span data-stu-id="586c4-175">LogIdentity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="586c4-176">이 설정은 macOS 및 Linux 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-176">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="586c4-177">시스템 로그에 쓰는 데 사용 되는 id 이름을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-177">Sets the identity name used to write to the system log.</span></span> <span data-ttu-id="586c4-178">기본값은 "powershell"입니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-178">The default value is "powershell".</span></span>

```Schema
"LogIdentity": "<log-identity>"
```

<span data-ttu-id="586c4-179">위치:</span><span class="sxs-lookup"><span data-stu-id="586c4-179">Where:</span></span>

- <span data-ttu-id="586c4-180">`<log-identity>` PowerShell에서 syslog에 쓰는 데 사용 해야 하는 문자열 id입니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-180">`<log-identity>` is the string identity that PowerShell should use for writing to syslog.</span></span>

> [!NOTE]
> <span data-ttu-id="586c4-181">설치한 각 PowerShell 인스턴스에 대해 서로 다른 **Logidentity** 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-181">You may want to have different **LogIdentity** values for each different instance of PowerShell you have installed.</span></span>

<span data-ttu-id="586c4-182">이 예제에서는 PowerShell의 미리 보기 릴리스에 대 한 **Logidentity** 를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-182">In this example, we are configuring the **LogIdentity** for a preview release of PowerShell.</span></span>

```json
{
  "LogIdentity": "powershell-preview"
}
```

### <a name="loglevel"></a><span data-ttu-id="586c4-183">LogLevel</span><span class="sxs-lookup"><span data-stu-id="586c4-183">LogLevel</span></span>

> [!IMPORTANT]
> <span data-ttu-id="586c4-184">이 설정은 macOS 및 Linux 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-184">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="586c4-185">PowerShell에서 기록해 야 하는 최소 심각도 수준을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-185">Specifies the minimum severity level at which PowerShell should log.</span></span>

```Schema
"LogLevel": "<log-level>|default"
```

<span data-ttu-id="586c4-186">위치:</span><span class="sxs-lookup"><span data-stu-id="586c4-186">Where:</span></span>

- <span data-ttu-id="586c4-187">`<log-level>` 다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-187">`<log-level>` is one of:</span></span>
  - <span data-ttu-id="586c4-188">Always</span><span class="sxs-lookup"><span data-stu-id="586c4-188">Always</span></span>
  - <span data-ttu-id="586c4-189">중요</span><span class="sxs-lookup"><span data-stu-id="586c4-189">Critical</span></span>
  - <span data-ttu-id="586c4-190">오류</span><span class="sxs-lookup"><span data-stu-id="586c4-190">Error</span></span>
  - <span data-ttu-id="586c4-191">경고</span><span class="sxs-lookup"><span data-stu-id="586c4-191">Warning</span></span>
  - <span data-ttu-id="586c4-192">정보 제공</span><span class="sxs-lookup"><span data-stu-id="586c4-192">Informational</span></span>
  - <span data-ttu-id="586c4-193">자세히</span><span class="sxs-lookup"><span data-stu-id="586c4-193">Verbose</span></span>
  - <span data-ttu-id="586c4-194">디버그</span><span class="sxs-lookup"><span data-stu-id="586c4-194">Debug</span></span>

> [!NOTE]
> <span data-ttu-id="586c4-195">로그 수준을 설정 하면 상위 로그 수준을 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-195">Setting a the log level enables all log levels above it.</span></span>

<span data-ttu-id="586c4-196">이 설정을 **기본값으로** 설정 하면 기본값으로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-196">Setting this setting to **default** will be interpreted as the default value.</span></span>
<span data-ttu-id="586c4-197">기본값은 **정보 제공** 입니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-197">The default value is **Informational**.</span></span>

<span data-ttu-id="586c4-198">다음 예에서는 값을 **Verbose** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-198">The following example sets the value to **Verbose**.</span></span>

```json
{
  "LogLevel": "Verbose"
}
```

### <a name="logchannels"></a><span data-ttu-id="586c4-199">LogChannels</span><span class="sxs-lookup"><span data-stu-id="586c4-199">LogChannels</span></span>

> [!IMPORTANT]
> <span data-ttu-id="586c4-200">이 설정은 macOS 및 Linux 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-200">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="586c4-201">사용할 수 있는 로깅 채널을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-201">Determines which logging channels are enabled.</span></span>

```Schema
"LogChannels": "<log-channel>,..."
```

<span data-ttu-id="586c4-202">위치:</span><span class="sxs-lookup"><span data-stu-id="586c4-202">Where:</span></span>

- <span data-ttu-id="586c4-203">`<log-channel>` 다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-203">`<log-channel>` is one of:</span></span>
  - <span data-ttu-id="586c4-204">운영-PowerShell 작업에 대 한 기본 정보를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-204">Operational - logs basic information about PowerShell activities</span></span>
  - <span data-ttu-id="586c4-205">분석-자세한 진단 정보를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-205">Analytic - logs more detailed diagnostic information</span></span>

<span data-ttu-id="586c4-206">기본값은 **작동** 입니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-206">The default value is **Operational**.</span></span> <span data-ttu-id="586c4-207">두 채널을 모두 사용 하려면 두 값을 쉼표로 구분 된 단일 문자열로 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-207">To enable both channels, include both values as a single comma-separated string.</span></span> <span data-ttu-id="586c4-208">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-208">For example:</span></span>

```json
{
  "LogChannels": "Operational,Analytic"
}
```

### <a name="logkeywords"></a><span data-ttu-id="586c4-209">LogKeywords</span><span class="sxs-lookup"><span data-stu-id="586c4-209">LogKeywords</span></span>

> [!IMPORTANT]
> <span data-ttu-id="586c4-210">이 설정은 macOS 및 Linux 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-210">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="586c4-211">로깅할 PowerShell 부분을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-211">Determines which parts of PowerShell are logged.</span></span> <span data-ttu-id="586c4-212">기본적으로 모든 로그 키워드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-212">By default, all log keywords are enabled.</span></span> <span data-ttu-id="586c4-213">여러 키워드를 사용 하도록 설정 하려면 쉼표로 구분 된 단일 문자열에서 값을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-213">To enable multiple keywords, list the values in a single comma-separated string.</span></span>

```Schema
"LogKeywords": "<log-keyword>,..."
```

<span data-ttu-id="586c4-214">위치:</span><span class="sxs-lookup"><span data-stu-id="586c4-214">Where:</span></span>

- <span data-ttu-id="586c4-215">`<log-keyword>` 다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-215">`<log-keyword>` is one of:</span></span>
  - <span data-ttu-id="586c4-216">Runspace-runspace 관리</span><span class="sxs-lookup"><span data-stu-id="586c4-216">Runspace - runspace management</span></span>
  - <span data-ttu-id="586c4-217">파이프라인 파이프라인 작업</span><span class="sxs-lookup"><span data-stu-id="586c4-217">Pipeline - pipeline operations</span></span>
  - <span data-ttu-id="586c4-218">프로토콜-통신 프로토콜 처리 (예: PSRP)</span><span class="sxs-lookup"><span data-stu-id="586c4-218">Protocol - communication protocol handling, such as PSRP</span></span>
  - <span data-ttu-id="586c4-219">전송-전송 계층 지원 (예: SSH)</span><span class="sxs-lookup"><span data-stu-id="586c4-219">Transport - transport layer support, such as SSH</span></span>
  - <span data-ttu-id="586c4-220">호스트-PowerShell 호스트 기능 (예: 콘솔 상호 작용)</span><span class="sxs-lookup"><span data-stu-id="586c4-220">Host - PowerShell host functionality, for example console interaction</span></span>
  - <span data-ttu-id="586c4-221">Cmdlet-PowerShell builtin cmdlet</span><span class="sxs-lookup"><span data-stu-id="586c4-221">Cmdlets -PowerShell builtin cmdlets</span></span>
  - <span data-ttu-id="586c4-222">Serializer-serialization 논리</span><span class="sxs-lookup"><span data-stu-id="586c4-222">Serializer - serialization logic</span></span>
  - <span data-ttu-id="586c4-223">세션-PowerShell 세션 상태</span><span class="sxs-lookup"><span data-stu-id="586c4-223">Session - PowerShell session state</span></span>
  - <span data-ttu-id="586c4-224">ManagedPlugin-WSMan 플러그 인</span><span class="sxs-lookup"><span data-stu-id="586c4-224">ManagedPlugin - WSMan plugin</span></span>

> [!NOTE]
> <span data-ttu-id="586c4-225">PowerShell의 알려진 부분에서 특정 동작을 진단 하려고 하지 않는 한이 값을 설정 하지 않으면 일반적으로이 값을 설정 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-225">It is generally advised to leave this value unset unless you are trying to diagnose a specific behavior in a known part of PowerShell.</span></span>
> <span data-ttu-id="586c4-226">이 값을 변경 하면 기록 되는 정보의 양만 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-226">Changing this value only decreases the amount of information logged.</span></span>

<span data-ttu-id="586c4-227">이 예에서는 로그를 runspace 작업, 파이프라인 논리 및 cmdlet 사용으로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-227">This example limits the logging to runspace operations, pipeline logic, and cmdlet use.</span></span> <span data-ttu-id="586c4-228">다른 모든 로깅은 생략 됩니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-228">All other logging will be omitted.</span></span>

```json
"LogKeywords": "Runspace,Pipeline,Cmdlets"
```

<!--

## Group policy configuration

### ScriptExecution

### ScriptBlockLogging

### ProtectedEventLogging

### Transcription

### UpdateableHelp

### ConsoleSessionConfiguration

-->

## <a name="more-example-configurations"></a><span data-ttu-id="586c4-229">추가 예제 구성</span><span class="sxs-lookup"><span data-stu-id="586c4-229">More example configurations</span></span>

### <a name="example-windows-configuration"></a><span data-ttu-id="586c4-230">Windows 구성 예</span><span class="sxs-lookup"><span data-stu-id="586c4-230">Example Windows configuration</span></span>

<span data-ttu-id="586c4-231">이 구성에는 명시적으로 설정 된 추가 설정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-231">This configuration has more settings explicitly set:</span></span>

- <span data-ttu-id="586c4-232">이 PowerShell 설치에 대 한 실행 정책은 `AllSigned`</span><span class="sxs-lookup"><span data-stu-id="586c4-232">Execution policy for this PowerShell installation is `AllSigned`</span></span>
- <span data-ttu-id="586c4-233">CurrentUser 모듈 경로를 공유 드라이브의 모듈 디렉터리로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-233">The CurrentUser module path is set to a module directory on a shared drive</span></span>
- <span data-ttu-id="586c4-234">`PSImplicitRemotingBatching`실험적 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-234">The `PSImplicitRemotingBatching` experimental feature is enabled</span></span>

> [!NOTE]
> <span data-ttu-id="586c4-235">`ExecutionPolicy`여기에 나와 있는 및 `PSModulePath` 설정은 모듈 경로에서 `\` 및 구분 문자를 사용 하 `;` 고 실행 정책이 `Unrestricted` (UNIX와 비슷한 플랫폼에서 유일 하 게 허용 되는 정책)가 아니기 때문에 Windows 플랫폼 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-235">The `ExecutionPolicy` and `PSModulePath` settings here would only work on a Windows platform, since the module path uses `\` and `;` separator characters and the execution policy is not `Unrestricted` (the only policy allowed on UNIX-like platforms).</span></span>

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "AllSigned",
  "PSModulePath": "Z:\\Marisol's Shared Drive\\Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
}
```

### <a name="example-non-windows-configuration"></a><span data-ttu-id="586c4-236">예: 비 Windows 구성</span><span class="sxs-lookup"><span data-stu-id="586c4-236">Example non-Windows configuration</span></span>

<span data-ttu-id="586c4-237">이 구성은 macOS 또는 Linux 에서만 작동 하는 여러 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-237">This configuration sets a number of options that only work in macOS or Linux:</span></span>

- <span data-ttu-id="586c4-238">CurrentUser 모듈 경로는의 사용자 지정 모듈 디렉터리로 설정 됩니다. `$HOME`</span><span class="sxs-lookup"><span data-stu-id="586c4-238">The CurrentUser module path is set to a custom module directory in `$HOME`</span></span>
- <span data-ttu-id="586c4-239">**Psimplicitremo의 일괄 처리** 실험적 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-239">The **PSImplicitRemotingBatching** experimental feature is enabled</span></span>
- <span data-ttu-id="586c4-240">자세한 로깅을 위해 PowerShell 로깅 수준이 **Verbose** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-240">The PowerShell logging level is set to **Verbose** , for more logging</span></span>
- <span data-ttu-id="586c4-241">이 PowerShell 설치는 **홈 powershell** id를 사용 하 여 로그에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="586c4-241">This PowerShell installation writes to the logs using the **home-powershell** identity.</span></span>

```json
{
  "PSModulePath": "%HOME%/.powershell/Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
  "LogLevel": "Verbose",
  "LogIdentity": "home-powershell"
}
```

## <a name="see-also"></a><span data-ttu-id="586c4-242">참고 항목</span><span class="sxs-lookup"><span data-stu-id="586c4-242">See also</span></span>

[<span data-ttu-id="586c4-243">실행 정책 정보</span><span class="sxs-lookup"><span data-stu-id="586c4-243">About Execution Policies</span></span>](./about_Execution_Policies.md)

[<span data-ttu-id="586c4-244">자동 변수 정보</span><span class="sxs-lookup"><span data-stu-id="586c4-244">About Automatic Variables</span></span>](./about_Automatic_Variables.md)

[RFC0029]: https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md

