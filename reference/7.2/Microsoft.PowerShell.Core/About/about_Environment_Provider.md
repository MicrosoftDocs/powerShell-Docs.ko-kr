---
description: 환경
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 환경 공급자
ms.openlocfilehash: f50558ba23d21b5ca145a06086c1c6d9b1fcd3bf
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600658"
---
# <a name="environment-provider"></a><span data-ttu-id="b03e6-103">환경 공급자</span><span class="sxs-lookup"><span data-stu-id="b03e6-103">Environment provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="b03e6-104">공급자 이름</span><span class="sxs-lookup"><span data-stu-id="b03e6-104">Provider name</span></span>
<span data-ttu-id="b03e6-105">환경</span><span class="sxs-lookup"><span data-stu-id="b03e6-105">Environment</span></span>

## <a name="drives"></a><span data-ttu-id="b03e6-106">드라이브</span><span class="sxs-lookup"><span data-stu-id="b03e6-106">Drives</span></span>

`Env:`

## <a name="capabilities"></a><span data-ttu-id="b03e6-107">기능</span><span class="sxs-lookup"><span data-stu-id="b03e6-107">Capabilities</span></span>

<span data-ttu-id="b03e6-108">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="b03e6-108">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="b03e6-109">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="b03e6-109">Short description</span></span>

<span data-ttu-id="b03e6-110">Windows 환경 변수에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-110">Provides access to the Windows environment variables.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="b03e6-111">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="b03e6-111">Detailed description</span></span>

<span data-ttu-id="b03e6-112">PowerShell **환경** 공급자를 통해 powershell에서 환경 변수 및 값을 가져오고 추가, 변경 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-112">The PowerShell **Environment** provider lets you get, add, change, clear, and delete environment variables and values in PowerShell.</span></span>

<span data-ttu-id="b03e6-113">**환경** 변수는 프로그램이 실행 되는 환경을 설명 하는 동적으로 명명 된 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-113">**Environment** variables are dynamically named variables that describe the environment in which your programs run.</span></span> <span data-ttu-id="b03e6-114">Windows 및 PowerShell은 환경 변수를 사용 하 여 시스템 및 프로세스 실행에 영향을 주는 영구 정보를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-114">Windows and PowerShell use environment variables to store persistent information that affect system and process execution.</span></span> <span data-ttu-id="b03e6-115">PowerShell 변수와 달리 환경 변수에는 범위 제약 조건이 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-115">Unlike PowerShell variables, environment variables are not subject to scope constraints.</span></span>

<span data-ttu-id="b03e6-116">**환경** 드라이브는 현재 사용자의 세션과 관련 된 환경 변수를 포함 하는 플랫 네임 스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-116">The **Environment** drive is a flat namespace containing the environment variables specific to the current user's session.</span></span> <span data-ttu-id="b03e6-117">환경 변수에는 자식 항목이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-117">The environment variables have no child items.</span></span>

<span data-ttu-id="b03e6-118">**환경** 공급자는이 문서에서 설명 하는 다음과 같은 cmdlet을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-118">The **Environment** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="b03e6-119">Get-Location</span><span class="sxs-lookup"><span data-stu-id="b03e6-119">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="b03e6-120">Set-Location</span><span class="sxs-lookup"><span data-stu-id="b03e6-120">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="b03e6-121">Get-Item</span><span class="sxs-lookup"><span data-stu-id="b03e6-121">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="b03e6-122">New-Item</span><span class="sxs-lookup"><span data-stu-id="b03e6-122">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="b03e6-123">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="b03e6-123">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="b03e6-124">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="b03e6-124">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="b03e6-125">이 공급자가 노출 하는 형식</span><span class="sxs-lookup"><span data-stu-id="b03e6-125">Types exposed by this provider</span></span>

<span data-ttu-id="b03e6-126">각 환경 변수는 [DictionaryEntry](/dotnet/api/system.collections.dictionaryentry) 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-126">Each environment variable is an instance of the [System.Collections.DictionaryEntry](/dotnet/api/system.collections.dictionaryentry) class.</span></span> <span data-ttu-id="b03e6-127">변수 이름은 사전 키입니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-127">The name of the variable is the dictionary key.</span></span> <span data-ttu-id="b03e6-128">환경 변수 값은 사전 값입니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-128">The value of the environment variable is the dictionary value.</span></span>

## <a name="navigating-the-environment-drive"></a><span data-ttu-id="b03e6-129">환경 드라이브 탐색</span><span class="sxs-lookup"><span data-stu-id="b03e6-129">Navigating the Environment drive</span></span>

<span data-ttu-id="b03e6-130">**환경** 공급자는 드라이브에 해당 데이터 저장소를 노출 합니다 `Env:` .</span><span class="sxs-lookup"><span data-stu-id="b03e6-130">The **Environment** provider exposes its data store in the `Env:` drive.</span></span> <span data-ttu-id="b03e6-131">환경 변수를 사용 하려면 위치를 `Env:` drive ()로 변경 `Set-Location Env:` 하거나 다른 PowerShell 드라이브에서 작업 합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-131">To work with environment variables, change your location to the `Env:` drive (`Set-Location Env:`), or work from another PowerShell drive.</span></span> <span data-ttu-id="b03e6-132">다른 위치에서 환경 변수를 참조 하려면 `Env:` 경로에 드라이브 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-132">To reference an environment variable from another location, use the `Env:` drive name in the path.</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="b03e6-133">파일 시스템 드라이브로 돌아가려면 드라이브 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-133">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="b03e6-134">예를 들어 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-134">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="b03e6-135">다른 PowerShell 드라이브에서 **환경** 공급자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-135">You can also work with the **Environment** provider from any other PowerShell drive.</span></span> <span data-ttu-id="b03e6-136">다른 위치에서 환경 변수를 참조 하려면 경로에 드라이브 이름을 사용 `Env:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-136">To reference an environment variable from another location, use the drive name `Env:` in the path.</span></span>

<span data-ttu-id="b03e6-137">**환경** 공급자는 또한 변수 접두사를 사용 하 여 환경 변수를 노출 `$env:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-137">The **Environment** provider also exposes environment variables using a variable prefix of `$env:`.</span></span>  <span data-ttu-id="b03e6-138">다음 명령은 **ProgramFiles** 환경 변수의 내용을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-138">The following command views the contents of the **ProgramFiles** environment variable.</span></span> <span data-ttu-id="b03e6-139">`$env:`변수 접두사는 모든 PowerShell 드라이브에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-139">The `$env:` variable prefix can be used from any PowerShell drive.</span></span>

```
PS C:\> $env:ProgramFiles
C:\Program Files
```

<span data-ttu-id="b03e6-140">변수 접두사를 사용 하 여 환경 변수 값을 변경할 수도 있습니다 `$env:` .</span><span class="sxs-lookup"><span data-stu-id="b03e6-140">You can also change the value of an environment variable using the `$env:` variable prefix.</span></span>  <span data-ttu-id="b03e6-141">변경 내용은 활성 상태인 동안에만 현재 PowerShell 세션에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-141">Any changes made only pertain to the current PowerShell session for as long as it is active.</span></span>

> [!NOTE]
> <span data-ttu-id="b03e6-142">PowerShell은 별칭을 사용 하 여 공급자 경로 작업을 수행할 수 있는 친숙 한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-142">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="b03e6-143">`dir`및 등의 명령은 `ls` 이제 [Get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)에 대 한 별칭입니다 `cd` .는 [집합 위치](xref:Microsoft.PowerShell.Management.Set-Location)에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-143">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="b03e6-144">및 `pwd` 은 [(는) 위치](xref:Microsoft.PowerShell.Management.Get-Location)에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-144">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-environment-variables"></a><span data-ttu-id="b03e6-145">환경 변수 가져오기</span><span class="sxs-lookup"><span data-stu-id="b03e6-145">Getting environment variables</span></span>

<span data-ttu-id="b03e6-146">이 명령은 현재 세션의 모든 환경 변수를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-146">This command lists all the environment variables in the current session.</span></span>

```powershell
Get-Item -Path Env:
```

<span data-ttu-id="b03e6-147">모든 PowerShell 드라이브에서이 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-147">You can use this command from any PowerShell drive.</span></span>

<span data-ttu-id="b03e6-148">환경 공급자에는 컨테이너가 없으므로에서 사용 하는 경우 위의 명령이 동일한 효과를 가집니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="b03e6-148">The Environment provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Env:
```

### <a name="get-a-selected-environment-variable"></a><span data-ttu-id="b03e6-149">선택한 환경 변수 가져오기</span><span class="sxs-lookup"><span data-stu-id="b03e6-149">Get a selected environment variable</span></span>

<span data-ttu-id="b03e6-150">이 명령은 `WINDIR` 환경 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-150">This command gets the `WINDIR` environment Variable.</span></span>

```powershell
Get-ChildItem -Path Env:windir
```

<span data-ttu-id="b03e6-151">또한 변수 접두사 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-151">You can also use the variable prefix format as well.</span></span>

```powershell
$env:windir
```

## <a name="create-an-environment-variable"></a><span data-ttu-id="b03e6-152">환경 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="b03e6-152">Create an environment variable</span></span>

<span data-ttu-id="b03e6-153">이 명령은 `USERMODE` "비 관리자" 값을 사용 하 여 환경 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-153">This command creates the `USERMODE` environment variable with a value of "Non-Admin".</span></span> <span data-ttu-id="b03e6-154">`-Path`매개 변수 값은 드라이브에 새 항목을 만듭니다 `Env:` .</span><span class="sxs-lookup"><span data-stu-id="b03e6-154">The `-Path` parameter value creates the new item in the `Env:` drive.</span></span> <span data-ttu-id="b03e6-155">새 환경 변수는 활성 상태인 동안에만 현재 PowerShell 세션에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-155">The new environment variable is only usable in the current PowerShell session for as long as it is active.</span></span>

```powershell
PS C:\> New-Item -Path Env: -Name USERMODE -Value Non-Admin
```

## <a name="changing-an-environment-variable"></a><span data-ttu-id="b03e6-156">환경 변수 변경</span><span class="sxs-lookup"><span data-stu-id="b03e6-156">Changing an environment variable</span></span>

### <a name="rename-an-environment-variable"></a><span data-ttu-id="b03e6-157">환경 변수 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="b03e6-157">Rename an environment variable</span></span>

<span data-ttu-id="b03e6-158">이 명령은 cmdlet을 사용 하 여 `Rename-Item` `USERMODE` 사용자가 만든 환경 변수의 이름을 변경 `USERROLE` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-158">This command uses the `Rename-Item` cmdlet to change the name of the `USERMODE` environment variable that you created to `USERROLE`.</span></span> <span data-ttu-id="b03e6-159">시스템에서 사용하는 환경 변수의 이름을 변경하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="b03e6-159">Do not change the name of an environment variable that the system uses.</span></span> <span data-ttu-id="b03e6-160">이러한 변경 내용은 현재 세션에만 영향을 주지만 이로 인해 시스템 또는 프로그램이 제대로 작동하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-160">Although these changes affect only the current session, they might cause the system or a program to operate incorrectly.</span></span>

```powershell
Rename-Item -Path Env:USERMODE -NewName USERROLE
```

### <a name="change-an-environment-variable"></a><span data-ttu-id="b03e6-161">환경 변수 변경</span><span class="sxs-lookup"><span data-stu-id="b03e6-161">Change an environment variable</span></span>

<span data-ttu-id="b03e6-162">이 명령은 cmdlet을 사용 하 여 `Set-Item` 환경 변수 값을 `USERROLE` "Administrator"로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-162">This command uses the `Set-Item` cmdlet to change the value of the `USERROLE` environment variable to "Administrator".</span></span>

```powershell
Set-Item -Path Env:USERROLE -Value Administrator
```

## <a name="copy-an-environment-variable"></a><span data-ttu-id="b03e6-163">환경 변수 복사</span><span class="sxs-lookup"><span data-stu-id="b03e6-163">Copy an environment variable</span></span>

<span data-ttu-id="b03e6-164">이 명령은 환경 변수 값 `USERROLE` 을 `USERROLE2` 환경 변수에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-164">This command copies the value of the `USERROLE` environment variable to the `USERROLE2` environment Variable.</span></span>

```powershell
Copy-Item -Path Env:USERROLE -Destination Env:USERROLE2
```

## <a name="remove-an-environment-variable"></a><span data-ttu-id="b03e6-165">환경 변수 제거</span><span class="sxs-lookup"><span data-stu-id="b03e6-165">Remove an environment variable</span></span>

<span data-ttu-id="b03e6-166">이 명령은 `USERROLE2` 현재 세션에서 환경 변수를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-166">This command deletes the `USERROLE2` environment variable from the current session.</span></span>

```powershell
Remove-Item -Path Env:USERROLE2
```

## <a name="remove-an-environment-variable-with-clear-item"></a><span data-ttu-id="b03e6-167">Clear-Item를 사용 하 여 환경 변수 제거</span><span class="sxs-lookup"><span data-stu-id="b03e6-167">Remove an environment variable with Clear-Item</span></span>

<span data-ttu-id="b03e6-168">이 명령은 `USERROLE` 해당 값의 선택을 취소 하 여 환경 변수를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-168">This command deletes the `USERROLE` environment variable by clearing its value.</span></span>

```powershell
Clear-Item -Path Env:USERROLE
```

## <a name="using-the-pipeline"></a><span data-ttu-id="b03e6-169">파이프라인 사용</span><span class="sxs-lookup"><span data-stu-id="b03e6-169">Using the pipeline</span></span>

<span data-ttu-id="b03e6-170">공급자 cmdlet은 파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-170">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="b03e6-171">파이프라인을 사용 하 여 cmdlet 간에 공급자 데이터를 전송 하 여 작업을 간소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-171">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="b03e6-172">공급자 cmdlet에서 파이프라인을 사용 하는 방법에 대 한 자세한 내용은이 문서 전체에서 제공 되는 cmdlet 참조를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b03e6-172">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="b03e6-173">도움말 보기</span><span class="sxs-lookup"><span data-stu-id="b03e6-173">Getting help</span></span>

<span data-ttu-id="b03e6-174">Windows PowerShell 3.0부터는 이러한 cmdlet이 파일 시스템 드라이브에서 동작하는 방식을 설명하는 공급자 cmdlet에 대한 사용자 지정된 도움말 항목을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-174">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="b03e6-175">파일 시스템 드라이브에 맞게 사용자 지정 된 도움말 항목을 보려면 파일 시스템 드라이브에서 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 명령을 실행 하거나 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 의 매개 변수를 사용 하 여 파일 시스템 드라이브를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b03e6-175">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path env:
```

## <a name="see-also"></a><span data-ttu-id="b03e6-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b03e6-176">See also</span></span>

[<span data-ttu-id="b03e6-177">about_Providers</span><span class="sxs-lookup"><span data-stu-id="b03e6-177">about_Providers</span></span>](../About/about_Providers.md)
