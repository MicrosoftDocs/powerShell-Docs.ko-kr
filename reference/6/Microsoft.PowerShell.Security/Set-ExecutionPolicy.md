---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ExecutionPolicy
ms.openlocfilehash: f8575c97c4279f285598e2b1bdf94786d92c841a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216881"
---
# <span data-ttu-id="583c8-103">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="583c8-103">Set-ExecutionPolicy</span></span>

## <span data-ttu-id="583c8-104">개요</span><span class="sxs-lookup"><span data-stu-id="583c8-104">SYNOPSIS</span></span>
<span data-ttu-id="583c8-105">Windows 컴퓨터에 대 한 PowerShell 실행 정책을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-105">Sets the PowerShell execution policies for Windows computers.</span></span>

## <span data-ttu-id="583c8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="583c8-106">SYNTAX</span></span>

### <span data-ttu-id="583c8-107">모두</span><span class="sxs-lookup"><span data-stu-id="583c8-107">All</span></span>

```
Set-ExecutionPolicy [-ExecutionPolicy] <ExecutionPolicy> [[-Scope] <ExecutionPolicyScope>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="583c8-108">설명</span><span class="sxs-lookup"><span data-stu-id="583c8-108">DESCRIPTION</span></span>

<span data-ttu-id="583c8-109">`Set-ExecutionPolicy`Cmdlet은 Windows 컴퓨터에 대 한 PowerShell 실행 정책을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-109">The `Set-ExecutionPolicy` cmdlet changes PowerShell execution policies for Windows computers.</span></span> <span data-ttu-id="583c8-110">자세한 내용은 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="583c8-110">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

<span data-ttu-id="583c8-111">Windows 이외의 컴퓨터에 대 한 PowerShell 6.0부터 기본 실행 정책은 **무제한** 이며 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-111">Beginning in PowerShell 6.0 for non-Windows computers, the default execution policy is **Unrestricted** and can't be changed.</span></span> <span data-ttu-id="583c8-112">`Set-ExecutionPolicy`Cmdlet을 사용할 수 있지만 PowerShell에서 지원 되지 않는 콘솔 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-112">The `Set-ExecutionPolicy` cmdlet is available, but PowerShell displays a console message that it's not supported.</span></span>

<span data-ttu-id="583c8-113">실행 정책은 PowerShell 보안 전략의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-113">An execution policy is part of the PowerShell security strategy.</span></span> <span data-ttu-id="583c8-114">실행 정책은 PowerShell 프로필과 같은 구성 파일을 로드 하거나 스크립트를 실행할 수 있는지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-114">Execution policies determine whether you can load configuration files, such as your PowerShell profile, or run scripts.</span></span> <span data-ttu-id="583c8-115">스크립트를 실행 하기 전에 디지털로 서명 해야 하는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-115">And, whether scripts must be digitally signed before they are run.</span></span>

<span data-ttu-id="583c8-116">`Set-ExecutionPolicy`Cmdlet의 기본 범위는 **LocalMachine** 이며이는 컴퓨터를 사용 하는 모든 사용자에 게 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-116">The `Set-ExecutionPolicy` cmdlet's default scope is **LocalMachine** , which affects everyone who uses the computer.</span></span> <span data-ttu-id="583c8-117">**LocalMachine** 에 대 한 실행 정책을 변경 하려면 **관리자 권한으로 실행** 을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-117">To change the execution policy for **LocalMachine** , start PowerShell with **Run as Administrator**.</span></span>

<span data-ttu-id="583c8-118">각 범위에 대 한 실행 정책을 우선 순위에 따라 표시 하려면를 사용 `Get-ExecutionPolicy -List` 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-118">To display the execution policies for each scope in the order of precedence, use `Get-ExecutionPolicy -List`.</span></span> <span data-ttu-id="583c8-119">PowerShell 세션의 유효 실행 정책을 매개 변수 없이 사용 하는 것을 확인 합니다 `Get-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="583c8-119">To see the effective execution policy for your PowerShell session use `Get-ExecutionPolicy` with no parameters.</span></span>

## <span data-ttu-id="583c8-120">예제</span><span class="sxs-lookup"><span data-stu-id="583c8-120">EXAMPLES</span></span>

### <span data-ttu-id="583c8-121">예제 1: 실행 정책 설정</span><span class="sxs-lookup"><span data-stu-id="583c8-121">Example 1: Set an execution policy</span></span>

<span data-ttu-id="583c8-122">이 예제에서는 로컬 컴퓨터에 대 한 실행 정책을 설정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-122">This example shows how to set the execution policy for the local computer.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="583c8-123">`Set-ExecutionPolicy`Cmdlet은 **set-executionpolicy** 매개 변수를 사용 하 여 **RemoteSigned** 정책을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-123">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="583c8-124">**범위** 매개 변수는 기본 범위 값인 **LocalMachine** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-124">The **Scope** parameter specifies the default scope value, **LocalMachine**.</span></span> <span data-ttu-id="583c8-125">실행 정책 설정을 보려면 `Get-ExecutionPolicy` **List** 매개 변수와 함께 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-125">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="583c8-126">예 2: 그룹 정책와 충돌 하는 실행 정책 설정</span><span class="sxs-lookup"><span data-stu-id="583c8-126">Example 2: Set an execution policy that conflicts with a Group Policy</span></span>

<span data-ttu-id="583c8-127">이 명령은 **LocalMachine** 범위의 실행 정책을 **제한** 으로 설정 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-127">This command attempts to set the **LocalMachine** scope's execution policy to **Restricted**.</span></span>
<span data-ttu-id="583c8-128">**LocalMachine** 는 더 제한적 이지만 그룹 정책와 충돌 하기 때문에 효과적인 정책이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-128">**LocalMachine** is more restrictive, but isn't the effective policy because it conflicts with a Group Policy.</span></span> <span data-ttu-id="583c8-129">**제한** 된 정책은 레지스트리 hive **HKEY_LOCAL_MACHINE** 에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-129">The **Restricted** policy is written to the registry hive **HKEY_LOCAL_MACHINE**.</span></span>

```
PS> Set-ExecutionPolicy -ExecutionPolicy Restricted -Scope LocalMachine

Set-ExecutionPolicy : PowerShell updated your local preference successfully, but the setting is
overridden by the Group Policy applied to your system. Due to the override, your shell will retain
its current effective execution policy of "AllSigned". Contact your Group Policy administrator for
more information. At line:1 char:20 + Set-ExecutionPolicy <<<< restricted

PS> Get-ChildItem -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PowerShell\1\ShellIds

Name                    Property
----                    --------
Microsoft.PowerShell    Path            : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
                        ExecutionPolicy : Restricted
ScriptedDiagnostics     ExecutionPolicy : Unrestricted
```

<span data-ttu-id="583c8-130">`Set-ExecutionPolicy`Cmdlet은 **set-executionpolicy** 매개 변수를 사용 하 여 **제한** 된 정책을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-130">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **Restricted** policy.</span></span> <span data-ttu-id="583c8-131">**범위** 매개 변수는 기본 범위 값인 **LocalMachine** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-131">The **Scope** parameter specifies the default scope value, **LocalMachine**.</span></span>
<span data-ttu-id="583c8-132">`Get-ChildItem`Cmdlet은 **HKLM** 공급자에 **Path** 매개 변수를 사용 하 여 레지스트리 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-132">The `Get-ChildItem` cmdlet uses the **Path** parameter with the **HKLM** provider to specify registry location.</span></span>

### <span data-ttu-id="583c8-133">예 3: 로컬 컴퓨터에 원격 컴퓨터의 실행 정책 적용</span><span class="sxs-lookup"><span data-stu-id="583c8-133">Example 3: Apply the execution policy from a remote computer to a local computer</span></span>

<span data-ttu-id="583c8-134">이 명령은 원격 컴퓨터에서 실행 정책 개체를 가져오고 로컬 컴퓨터에 정책을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-134">This command gets the execution policy object from a remote computer and sets the policy on the local computer.</span></span> <span data-ttu-id="583c8-135">`Get-ExecutionPolicy` 파이프라인을 통해 **Microsoft.PowerShell.Exe된 정책** 개체를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-135">`Get-ExecutionPolicy` sends a **Microsoft.PowerShell.ExecutionPolicy** object down the pipeline.</span></span> <span data-ttu-id="583c8-136">`Set-ExecutionPolicy` 파이프라인 입력을 허용 하며 **set-executionpolicy** 매개 변수가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-136">`Set-ExecutionPolicy` accepts pipeline input and doesn't require the **ExecutionPolicy** parameter.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -ScriptBlock { Get-ExecutionPolicy } | Set-ExecutionPolicy
```

<span data-ttu-id="583c8-137">`Invoke-Command`이 cmdlet은 로컬 컴퓨터에서 실행 되 고 **ScriptBlock** 을 원격 컴퓨터로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-137">The `Invoke-Command` cmdlet is executed at the local computer and sends the **ScriptBlock** to the remote computer.</span></span> <span data-ttu-id="583c8-138">**ComputerName** 매개 변수는 원격 컴퓨터 **Server01** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-138">The **ComputerName** parameter specifies the remote computer, **Server01**.</span></span> <span data-ttu-id="583c8-139">**ScriptBlock** 매개 변수는 `Get-ExecutionPolicy` 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-139">The **ScriptBlock** parameter runs `Get-ExecutionPolicy` on the remote computer.</span></span> <span data-ttu-id="583c8-140">`Get-ExecutionPolicy`개체는 파이프라인에서로 전송 됩니다 `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="583c8-140">The `Get-ExecutionPolicy` object is sent down the pipeline to the `Set-ExecutionPolicy`.</span></span>
<span data-ttu-id="583c8-141">`Set-ExecutionPolicy` 실행 정책을 로컬 컴퓨터의 기본 범위인 **LocalMachine** 에 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-141">`Set-ExecutionPolicy` applies the execution policy to the local computer's default scope, **LocalMachine**.</span></span>

### <span data-ttu-id="583c8-142">예제 4: 실행 정책에 대 한 범위 설정</span><span class="sxs-lookup"><span data-stu-id="583c8-142">Example 4: Set the scope for an execution policy</span></span>

<span data-ttu-id="583c8-143">이 예제에서는 지정 된 범위 **CurrentUser** 에 대 한 실행 정책을 설정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-143">This example shows how to set an execution policy for a specified scope, **CurrentUser**.</span></span> <span data-ttu-id="583c8-144">**CurrentUser** 범위는이 범위를 설정 하는 사용자 에게만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-144">The **CurrentUser** scope only affects the user who sets this scope.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="583c8-145">`Set-ExecutionPolicy`**set-executionpolicy** 매개 변수를 사용 하 여 **AllSigned** 정책을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-145">`Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **AllSigned** policy.</span></span>
<span data-ttu-id="583c8-146">**Scope** 매개 변수는 **CurrentUser** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-146">The **Scope** parameter specifies the **CurrentUser**.</span></span> <span data-ttu-id="583c8-147">실행 정책 설정을 보려면 `Get-ExecutionPolicy` **List** 매개 변수와 함께 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-147">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

<span data-ttu-id="583c8-148">사용자에 대 한 유효 실행 정책이 **AllSigned** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-148">The effective execution policy for the user becomes **AllSigned**.</span></span>

### <span data-ttu-id="583c8-149">예 5: 현재 사용자에 대 한 실행 정책 제거</span><span class="sxs-lookup"><span data-stu-id="583c8-149">Example 5: Remove the execution policy for the current user</span></span>

<span data-ttu-id="583c8-150">이 예에서는 **정의 되지 않은** 실행 정책을 사용 하 여 지정 된 범위에 대 한 실행 정책을 제거 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-150">This example shows how use the **Undefined** execution policy to remove an execution policy for a specified scope.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       Undefined
 LocalMachine    RemoteSigned
```

<span data-ttu-id="583c8-151">`Set-ExecutionPolicy`**set-executionpolicy** 매개 변수를 사용 하 여 **정의 되지 않은** 정책을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-151">`Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **Undefined** policy.</span></span>
<span data-ttu-id="583c8-152">**Scope** 매개 변수는 **CurrentUser** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-152">The **Scope** parameter specifies the **CurrentUser**.</span></span> <span data-ttu-id="583c8-153">실행 정책 설정을 보려면 `Get-ExecutionPolicy` **List** 매개 변수와 함께 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-153">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="583c8-154">예 6: 현재 PowerShell 세션에 대 한 실행 정책 설정</span><span class="sxs-lookup"><span data-stu-id="583c8-154">Example 6: Set the execution policy for the current PowerShell session</span></span>

<span data-ttu-id="583c8-155">**프로세스** 범위는 현재 PowerShell 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-155">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="583c8-156">실행 정책은 환경 변수에 저장 되며 `$env:PSExecutionPolicyPreference` 세션을 닫을 때 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-156">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference` and is deleted when the session is closed.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope Process
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       AllSigned
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="583c8-157">는 `Set-ExecutionPolicy` **set-executionpolicy** 매개 변수를 사용 하 여 **AllSigned** 정책을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-157">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **AllSigned** policy.</span></span> <span data-ttu-id="583c8-158">**범위** 매개 변수는 값 **프로세스** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-158">The **Scope** parameter specifies the value **Process**.</span></span> <span data-ttu-id="583c8-159">실행 정책 설정을 보려면 `Get-ExecutionPolicy` **List** 매개 변수와 함께 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-159">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="583c8-160">예 7: 실행 정책을 변경 하지 않고 실행 하는 스크립트 차단 해제</span><span class="sxs-lookup"><span data-stu-id="583c8-160">Example 7: Unblock a script to run it without changing the execution policy</span></span>

<span data-ttu-id="583c8-161">이 예에서는 **RemoteSigned** 실행 정책으로 서명 되지 않은 스크립트를 실행 하지 못하게 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-161">This example shows how the **RemoteSigned** execution policy prevents you from running unsigned scripts.</span></span>

<span data-ttu-id="583c8-162">Cmdlet을 사용 **하기 전에** 스크립트의 코드를 읽고 안전 하 게 확인 하는 것이 가장 좋습니다 `Unblock-File` .</span><span class="sxs-lookup"><span data-stu-id="583c8-162">A best practice is to read the script's code and verify it's safe **before** using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="583c8-163">`Unblock-File`Cmdlet은 실행할 수 있도록 스크립트를 차단 해제 하지만 실행 정책을 변경 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-163">The `Unblock-File` cmdlet unblocks scripts so they can run, but doesn't change the execution policy.</span></span>

```
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

.\Start-ActivityTracker.ps1 : File .\Start-ActivityTracker.ps1 cannot be loaded.
The file .\Start-ActivityTracker.ps1 is not digitally signed.
The script will not execute on the system.
For more information, see about_Execution_Policies at https://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], PSSecurityException
+ FullyQualifiedErrorId : UnauthorizedAccess

PS> Unblock-File -Path .\Start-ActivityTracker.ps1

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

Task 1:
```

<span data-ttu-id="583c8-164">는 `Set-ExecutionPolicy` **set-executionpolicy** 매개 변수를 사용 하 여 **RemoteSigned** 정책을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-164">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="583c8-165">정책은 기본 범위인 **LocalMachine** 에 대해 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-165">The policy is set for the default scope, **LocalMachine**.</span></span>

<span data-ttu-id="583c8-166">`Get-ExecutionPolicy`이 cmdlet은 **RemoteSigned** 가 현재 PowerShell 세션에 대 한 유효한 실행 정책 임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-166">The `Get-ExecutionPolicy` cmdlet shows that **RemoteSigned** is the effective execution policy for the current PowerShell session.</span></span>

<span data-ttu-id="583c8-167">현재 디렉터리에서 **Start-ActivityTracker.ps1** 스크립트가 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-167">The **Start-ActivityTracker.ps1** script is executed from the current directory.</span></span> <span data-ttu-id="583c8-168">스크립트가 디지털 서명 되지 않았기 때문에 **RemoteSigned** 에 의해 스크립트가 차단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-168">The script is blocked by **RemoteSigned** because the script isn't digitally signed.</span></span>

<span data-ttu-id="583c8-169">이 예제에서는 스크립트의 코드를 검토 하 고 실행 해도 안전한 지 확인 했습니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-169">For this example, the script's code was reviewed and verified as safe to run.</span></span> <span data-ttu-id="583c8-170">`Unblock-File`Cmdlet은 **Path** 매개 변수를 사용 하 여 스크립트를 차단 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-170">The `Unblock-File` cmdlet uses the **Path** parameter to unblock the script.</span></span>

<span data-ttu-id="583c8-171">`Unblock-File`에서 실행 정책이 변경 되지 않았는지 확인 하려면는 `Get-ExecutionPolicy` 유효한 실행 정책 **RemoteSigned** 를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-171">To verify that `Unblock-File` didn't change the execution policy, `Get-ExecutionPolicy` displays the effective execution policy, **RemoteSigned**.</span></span>

<span data-ttu-id="583c8-172">현재 디렉터리에서 **Start-ActivityTracker.ps1** 스크립트가 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-172">The script, **Start-ActivityTracker.ps1** is executed from the current directory.</span></span> <span data-ttu-id="583c8-173">스크립트가 cmdlet에 의해 차단이 해제 되었기 때문에 스크립트가 실행 되기 시작 합니다 `Unblock-File` .</span><span class="sxs-lookup"><span data-stu-id="583c8-173">The script begins to run because it was unblocked by the `Unblock-File` cmdlet.</span></span>

## <span data-ttu-id="583c8-174">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="583c8-174">PARAMETERS</span></span>

### <span data-ttu-id="583c8-175">-Confirm</span><span class="sxs-lookup"><span data-stu-id="583c8-175">-Confirm</span></span>

<span data-ttu-id="583c8-176">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-176">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="583c8-177">-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="583c8-177">-ExecutionPolicy</span></span>

<span data-ttu-id="583c8-178">실행 정책을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-178">Specifies the execution policy.</span></span> <span data-ttu-id="583c8-179">그룹 정책이 없고 각 범위의 실행 정책이 **Undefined** 로 설정 된 경우 **제한** 된 모든 사용자에 대 한 유효 정책이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-179">If there are no Group Policies and each scope's execution policy is set to **Undefined** , then **Restricted** becomes the effective policy for all users.</span></span>

<span data-ttu-id="583c8-180">허용 되는 실행 정책 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-180">The acceptable execution policy values are as follows:</span></span>

- <span data-ttu-id="583c8-181">**AllSigned**.</span><span class="sxs-lookup"><span data-stu-id="583c8-181">**AllSigned**.</span></span> <span data-ttu-id="583c8-182">로컬 컴퓨터에 작성 된 스크립트를 포함 하 여 모든 스크립트와 구성 파일에 신뢰할 수 있는 게시자가 서명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-182">Requires that all scripts and configuration files are signed by a trusted publisher, including scripts written on the local computer.</span></span>
- <span data-ttu-id="583c8-183">**바이패스**.</span><span class="sxs-lookup"><span data-stu-id="583c8-183">**Bypass**.</span></span> <span data-ttu-id="583c8-184">아무것도 차단되지 않으며 경고 또는 프롬프트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-184">Nothing is blocked and there are no warnings or prompts.</span></span>
- <span data-ttu-id="583c8-185">**Default** 입니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-185">**Default**.</span></span> <span data-ttu-id="583c8-186">기본 실행 정책을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-186">Sets the default execution policy.</span></span> <span data-ttu-id="583c8-187">Windows 클라이언트 또는 Windows server **RemoteSigned** 에 대해 **제한** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-187">**Restricted** for Windows clients or **RemoteSigned** for Windows servers.</span></span>
- <span data-ttu-id="583c8-188">**RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="583c8-188">**RemoteSigned**.</span></span> <span data-ttu-id="583c8-189">인터넷에서 다운로드 한 모든 스크립트와 구성 파일에 신뢰할 수 있는 게시자가 서명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-189">Requires that all scripts and configuration files downloaded from the Internet are signed by a trusted publisher.</span></span> <span data-ttu-id="583c8-190">Windows server 컴퓨터에 대 한 기본 실행 정책입니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-190">The default execution policy for Windows server computers.</span></span>
- <span data-ttu-id="583c8-191">**제한** 됨.</span><span class="sxs-lookup"><span data-stu-id="583c8-191">**Restricted**.</span></span> <span data-ttu-id="583c8-192">구성 파일을 로드 하거나 스크립트를 실행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-192">Doesn't load configuration files or run scripts.</span></span> <span data-ttu-id="583c8-193">기본 실행 정책 Windows 클라이언트 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-193">The default execution policy Windows client computers.</span></span>
- <span data-ttu-id="583c8-194">**정의 되지 않았습니다**.</span><span class="sxs-lookup"><span data-stu-id="583c8-194">**Undefined**.</span></span> <span data-ttu-id="583c8-195">범위에 대해 설정 된 실행 정책이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-195">No execution policy is set for the scope.</span></span> <span data-ttu-id="583c8-196">그룹 정책에 의해 설정 되지 않은 범위에서 할당 된 실행 정책을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-196">Removes an assigned execution policy from a scope that is not set by a Group Policy.</span></span> <span data-ttu-id="583c8-197">모든 범위의 실행 정책이 **정의** 되지 않은 경우 유효 실행 정책이 **제한** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-197">If the execution policy in all scopes is **Undefined** , the effective execution policy is **Restricted**.</span></span>
- <span data-ttu-id="583c8-198">**무제한**.</span><span class="sxs-lookup"><span data-stu-id="583c8-198">**Unrestricted**.</span></span> <span data-ttu-id="583c8-199">PowerShell 6.0부터이는 비 Windows 컴퓨터에 대 한 기본 실행 정책이 며 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-199">Beginning in PowerShell 6.0, this is the default execution policy for non-Windows computers and can't be changed.</span></span> <span data-ttu-id="583c8-200">모든 구성 파일을 로드하고 모든 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-200">Loads all configuration files and runs all scripts.</span></span> <span data-ttu-id="583c8-201">인터넷에서 다운로드 한 서명 되지 않은 스크립트를 실행할 경우 실행 하기 전에 사용 권한을 묻는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-201">If you run an unsigned script that was downloaded from the internet, you're prompted for permission before it runs.</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: AllSigned, Bypass, Default, RemoteSigned, Restricted, Undefined, Unrestricted

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="583c8-202">-Force</span><span class="sxs-lookup"><span data-stu-id="583c8-202">-Force</span></span>

<span data-ttu-id="583c8-203">모든 확인 메시지를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-203">Suppresses all the confirmation prompts.</span></span> <span data-ttu-id="583c8-204">예기치 않은 결과를 방지 하려면이 매개 변수에 주의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-204">Use caution with this parameter to avoid unexpected results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="583c8-205">-범위</span><span class="sxs-lookup"><span data-stu-id="583c8-205">-Scope</span></span>

<span data-ttu-id="583c8-206">실행 정책의 영향을 받는 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-206">Specifies the scope that is affected by an execution policy.</span></span> <span data-ttu-id="583c8-207">기본 범위는 **LocalMachine** 입니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-207">The default scope is **LocalMachine**.</span></span>

<span data-ttu-id="583c8-208">유효한 실행 정책은 다음과 같이 우선 순위에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-208">The effective execution policy is determined by the order of precedence as follows:</span></span>

- <span data-ttu-id="583c8-209">**MachinePolicy**.</span><span class="sxs-lookup"><span data-stu-id="583c8-209">**MachinePolicy**.</span></span> <span data-ttu-id="583c8-210">컴퓨터의 모든 사용자에 대해 그룹 정책 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-210">Set by a Group Policy for all users of the computer.</span></span>
- <span data-ttu-id="583c8-211">**Userpolicy**.</span><span class="sxs-lookup"><span data-stu-id="583c8-211">**UserPolicy**.</span></span> <span data-ttu-id="583c8-212">컴퓨터의 현재 사용자에 대 한 그룹 정책 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-212">Set by a Group Policy for the current user of the computer.</span></span>
- <span data-ttu-id="583c8-213">**프로세스**.</span><span class="sxs-lookup"><span data-stu-id="583c8-213">**Process**.</span></span> <span data-ttu-id="583c8-214">현재 PowerShell 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-214">Affects only the current PowerShell session.</span></span>
- <span data-ttu-id="583c8-215">**CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="583c8-215">**CurrentUser**.</span></span> <span data-ttu-id="583c8-216">현재 사용자 에게만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-216">Affects only the current user.</span></span>
- <span data-ttu-id="583c8-217">**LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="583c8-217">**LocalMachine**.</span></span> <span data-ttu-id="583c8-218">컴퓨터의 모든 사용자에 게 영향을 주는 기본 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-218">Default scope that affects all users of the computer.</span></span>

<span data-ttu-id="583c8-219">**프로세스** 범위는 현재 PowerShell 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-219">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="583c8-220">실행 정책은 레지스트리가 아닌 환경 변수에 저장 됩니다 `$env:PSExecutionPolicyPreference` .</span><span class="sxs-lookup"><span data-stu-id="583c8-220">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference`, rather than the registry.</span></span> <span data-ttu-id="583c8-221">PowerShell 세션이 닫히면 변수와 값이 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-221">When the PowerShell session is closed, the variable and value are deleted.</span></span>

<span data-ttu-id="583c8-222">**CurrentUser** 범위에 대 한 실행 정책은 레지스트리 hive **HKEY_LOCAL_USER** 에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-222">Execution policies for the **CurrentUser** scope are written to the registry hive **HKEY_LOCAL_USER**.</span></span>

<span data-ttu-id="583c8-223">**LocalMachine** 범위에 대 한 실행 정책은 레지스트리 hive **HKEY_LOCAL_MACHINE** 에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-223">Execution policies for the **LocalMachine** scope are written to the registry hive **HKEY_LOCAL_MACHINE**.</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 1
Default value: LocalMachine
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="583c8-224">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="583c8-224">-WhatIf</span></span>

<span data-ttu-id="583c8-225">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-225">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="583c8-226">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-226">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="583c8-227">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="583c8-227">CommonParameters</span></span>

<span data-ttu-id="583c8-228">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="583c8-228">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="583c8-229">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="583c8-229">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="583c8-230">입력</span><span class="sxs-lookup"><span data-stu-id="583c8-230">INPUTS</span></span>

### <span data-ttu-id="583c8-231">Microsoft.PowerShell.Exe, System.string</span><span class="sxs-lookup"><span data-stu-id="583c8-231">Microsoft.PowerShell.ExecutionPolicy, System.String</span></span>

<span data-ttu-id="583c8-232">실행 정책 개체 또는 실행 정책의 이름을 포함 하는 문자열을로 파이프 할 수 있습니다 `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="583c8-232">You can pipe an execution policy object or a string that contains the name of an execution policy to `Set-ExecutionPolicy`.</span></span>

## <span data-ttu-id="583c8-233">출력</span><span class="sxs-lookup"><span data-stu-id="583c8-233">OUTPUTS</span></span>

### <span data-ttu-id="583c8-234">없음</span><span class="sxs-lookup"><span data-stu-id="583c8-234">None</span></span>

<span data-ttu-id="583c8-235">`Set-ExecutionPolicy` 는 출력을 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-235">`Set-ExecutionPolicy` doesn't return any output.</span></span>

## <span data-ttu-id="583c8-236">참고</span><span class="sxs-lookup"><span data-stu-id="583c8-236">NOTES</span></span>

<span data-ttu-id="583c8-237">`Set-ExecutionPolicy` 는 그룹 정책에 의해 설정 되므로 **MachinePolicy** 및 **userpolicy** 범위를 변경 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-237">`Set-ExecutionPolicy` doesn't change the **MachinePolicy** and **UserPolicy** scopes because they are set by Group Policies.</span></span>

<span data-ttu-id="583c8-238">`Set-ExecutionPolicy` 사용자 기본 설정이 정책 보다 더 제한적 이더라도는 그룹 정책를 재정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-238">`Set-ExecutionPolicy` doesn't override a Group Policy, even if the user preference is more restrictive than the policy.</span></span>

<span data-ttu-id="583c8-239">컴퓨터 또는 사용자에 대 한 **스크립트 실행 설정** 그룹 정책 사용 하도록 설정 된 경우 사용자 기본 설정이 저장 되지만 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-239">If the Group Policy **Turn on Script Execution** is enabled for the computer or user, the user preference is saved, but it is not effective.</span></span> <span data-ttu-id="583c8-240">PowerShell은 충돌을 설명 하는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="583c8-240">PowerShell displays a message that explains the conflict.</span></span>

## <span data-ttu-id="583c8-241">관련 링크</span><span class="sxs-lookup"><span data-stu-id="583c8-241">RELATED LINKS</span></span>

[<span data-ttu-id="583c8-242">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="583c8-242">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="583c8-243">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="583c8-243">about_Group_Policy_Settings</span></span>](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[<span data-ttu-id="583c8-244">about_Providers</span><span class="sxs-lookup"><span data-stu-id="583c8-244">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="583c8-245">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="583c8-245">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="583c8-246">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="583c8-246">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="583c8-247">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="583c8-247">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="583c8-248">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="583c8-248">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="583c8-249">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="583c8-249">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="583c8-250">Unblock-File</span><span class="sxs-lookup"><span data-stu-id="583c8-250">Unblock-File</span></span>](../Microsoft.PowerShell.Utility/Unblock-File.md)
