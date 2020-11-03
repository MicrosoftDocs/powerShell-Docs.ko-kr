---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-executionpolicy?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExecutionPolicy
ms.openlocfilehash: d33961d9c0b1980d84d35a33c45d965e84231914
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217497"
---
# <span data-ttu-id="3f5e8-103">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="3f5e8-103">Get-ExecutionPolicy</span></span>

## <span data-ttu-id="3f5e8-104">개요</span><span class="sxs-lookup"><span data-stu-id="3f5e8-104">SYNOPSIS</span></span>
<span data-ttu-id="3f5e8-105">현재 세션에 대한 실행 정책을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-105">Gets the execution policies for the current session.</span></span>

## <span data-ttu-id="3f5e8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3f5e8-106">SYNTAX</span></span>

### <span data-ttu-id="3f5e8-107">모두</span><span class="sxs-lookup"><span data-stu-id="3f5e8-107">All</span></span>

```
Get-ExecutionPolicy [[-Scope] <ExecutionPolicyScope>] [-List] [<CommonParameters>]
```

## <span data-ttu-id="3f5e8-108">설명</span><span class="sxs-lookup"><span data-stu-id="3f5e8-108">DESCRIPTION</span></span>

<span data-ttu-id="3f5e8-109">각 범위에 대 한 실행 정책을 우선 순위에 따라 표시 하려면를 사용 `Get-ExecutionPolicy -List` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-109">To display the execution policies for each scope in the order of precedence, use `Get-ExecutionPolicy -List`.</span></span> <span data-ttu-id="3f5e8-110">PowerShell 세션의 유효 실행 정책을 매개 변수 없이 사용 하는 것을 확인 합니다 `Get-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="3f5e8-110">To see the effective execution policy for your PowerShell session use `Get-ExecutionPolicy` with no parameters.</span></span>

<span data-ttu-id="3f5e8-111">유효 실행 정책은에 의해 설정 되 고 설정 그룹 정책 하는 실행 정책에 의해 결정 됩니다 `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="3f5e8-111">The effective execution policy is determined by execution policies that are set by `Set-ExecutionPolicy` and Group Policy settings.</span></span>

<span data-ttu-id="3f5e8-112">자세한 내용은 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-112">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="3f5e8-113">예제</span><span class="sxs-lookup"><span data-stu-id="3f5e8-113">EXAMPLES</span></span>

### <span data-ttu-id="3f5e8-114">예제 1: 모든 실행 정책 가져오기</span><span class="sxs-lookup"><span data-stu-id="3f5e8-114">Example 1: Get all execution policies</span></span>

<span data-ttu-id="3f5e8-115">이 명령은 각 범위에 대 한 실행 정책을 우선 순위에 따라 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-115">This command displays the execution policies for each scope in the order of precedence.</span></span>

```powershell
Get-ExecutionPolicy -List
```

```Output
Scope          ExecutionPolicy
-----          ---------------
MachinePolicy  Undefined
UserPolicy     Undefined
Process        Undefined
CurrentUser    AllSigned
LocalMachine   Undefined
```

<span data-ttu-id="3f5e8-116">`Get-ExecutionPolicy`Cmdlet은 **List** 매개 변수를 사용 하 여 각 범위의 실행 정책을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-116">The `Get-ExecutionPolicy` cmdlet uses the **List** parameter to display each scope's execution policy.</span></span>

### <span data-ttu-id="3f5e8-117">예제 2: 실행 정책 설정</span><span class="sxs-lookup"><span data-stu-id="3f5e8-117">Example 2: Set an execution policy</span></span>

<span data-ttu-id="3f5e8-118">이 예제에서는 로컬 컴퓨터에 대 한 실행 정책을 설정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-118">This example shows how to set an execution policy for the local computer.</span></span>

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
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="3f5e8-119">`Set-ExecutionPolicy`Cmdlet은 **set-executionpolicy** 매개 변수를 사용 하 여 **RemoteSigned** 정책을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-119">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="3f5e8-120">**범위** 매개 변수는 기본 범위 값인 **LocalMachine** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-120">The **Scope** parameter specifies the default scope value, **LocalMachine**.</span></span> <span data-ttu-id="3f5e8-121">실행 정책 설정을 보려면 `Get-ExecutionPolicy` **List** 매개 변수와 함께 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-121">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="3f5e8-122">예 3: 유효 실행 정책 가져오기</span><span class="sxs-lookup"><span data-stu-id="3f5e8-122">Example 3: Get the effective execution policy</span></span>

<span data-ttu-id="3f5e8-123">이 예에서는 PowerShell 세션의 유효 실행 정책을 표시 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-123">This example shows how to display the effective execution policy for a PowerShell session.</span></span>

```
PS> Get-ExecutionPolicy -List

        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned

PS> Get-ExecutionPolicy

AllSigned
```

<span data-ttu-id="3f5e8-124">`Get-ExecutionPolicy`Cmdlet은 **List** 매개 변수를 사용 하 여 각 범위의 실행 정책을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-124">The `Get-ExecutionPolicy` cmdlet uses the **List** parameter to display each scope's execution policy.</span></span> <span data-ttu-id="3f5e8-125">`Get-ExecutionPolicy`매개 변수 없이 cmdlet을 실행 하 여 유효 실행 정책 **AllSigned** 를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-125">The `Get-ExecutionPolicy` cmdlet is run without a parameter to display the effective execution policy, **AllSigned**.</span></span>

### <span data-ttu-id="3f5e8-126">예제 4: 실행 정책을 변경 하지 않고 실행 하는 스크립트 차단 해제</span><span class="sxs-lookup"><span data-stu-id="3f5e8-126">Example 4: Unblock a script to run it without changing the execution policy</span></span>

<span data-ttu-id="3f5e8-127">이 예에서는 **RemoteSigned** 실행 정책으로 서명 되지 않은 스크립트를 실행 하지 못하게 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-127">This example shows how the **RemoteSigned** execution policy prevents you from running unsigned scripts.</span></span>

<span data-ttu-id="3f5e8-128">Cmdlet을 사용 **하기 전에** 스크립트의 코드를 읽고 안전 하 게 확인 하는 것이 가장 좋습니다 `Unblock-File` .</span><span class="sxs-lookup"><span data-stu-id="3f5e8-128">A best practice is to read the script's code and verify it's safe **before** using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="3f5e8-129">`Unblock-File`Cmdlet은 실행할 수 있도록 스크립트를 차단 해제 하지만 실행 정책을 변경 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-129">The `Unblock-File` cmdlet unblocks scripts so they can run, but doesn't change the execution policy.</span></span>

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

<span data-ttu-id="3f5e8-130">는 `Set-ExecutionPolicy` **set-executionpolicy** 매개 변수를 사용 하 여 **RemoteSigned** 정책을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-130">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="3f5e8-131">정책은 기본 범위인 **LocalMachine** 에 대해 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-131">The policy is set for the default scope, **LocalMachine**.</span></span>

<span data-ttu-id="3f5e8-132">`Get-ExecutionPolicy`이 cmdlet은 **RemoteSigned** 가 현재 PowerShell 세션에 대 한 유효한 실행 정책 임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-132">The `Get-ExecutionPolicy` cmdlet shows that **RemoteSigned** is the effective execution policy for the current PowerShell session.</span></span>

<span data-ttu-id="3f5e8-133">현재 디렉터리에서 **Start-ActivityTracker.ps1** 스크립트가 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-133">The **Start-ActivityTracker.ps1** script is executed from the current directory.</span></span> <span data-ttu-id="3f5e8-134">스크립트가 디지털 서명 되지 않았기 때문에 **RemoteSigned** 에 의해 스크립트가 차단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-134">The script is blocked by **RemoteSigned** because the script isn't digitally signed.</span></span>

<span data-ttu-id="3f5e8-135">이 예제에서는 스크립트의 코드를 검토 하 고 실행 해도 안전한 지 확인 했습니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-135">For this example, the script's code was reviewed and verified as safe to run.</span></span> <span data-ttu-id="3f5e8-136">`Unblock-File`Cmdlet은 **Path** 매개 변수를 사용 하 여 스크립트를 차단 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-136">The `Unblock-File` cmdlet uses the **Path** parameter to unblock the script.</span></span>

<span data-ttu-id="3f5e8-137">`Unblock-File`에서 실행 정책이 변경 되지 않았는지 확인 하려면는 `Get-ExecutionPolicy` 유효한 실행 정책 **RemoteSigned** 를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-137">To verify that `Unblock-File` didn't change the execution policy, `Get-ExecutionPolicy` displays the effective execution policy, **RemoteSigned**.</span></span>

<span data-ttu-id="3f5e8-138">현재 디렉터리에서 **Start-ActivityTracker.ps1** 스크립트가 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-138">The script, **Start-ActivityTracker.ps1** is executed from the current directory.</span></span> <span data-ttu-id="3f5e8-139">스크립트가 cmdlet에 의해 차단이 해제 되었기 때문에 스크립트가 실행 되기 시작 합니다 `Unblock-File` .</span><span class="sxs-lookup"><span data-stu-id="3f5e8-139">The script begins to run because it was unblocked by the `Unblock-File` cmdlet.</span></span>

## <span data-ttu-id="3f5e8-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3f5e8-140">PARAMETERS</span></span>

### <span data-ttu-id="3f5e8-141">-목록</span><span class="sxs-lookup"><span data-stu-id="3f5e8-141">-List</span></span>

<span data-ttu-id="3f5e8-142">우선 순위대로 나열된, 세션에 대한 모든 실행 정책 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-142">Gets all execution policy values for the session listed in precedence order.</span></span> <span data-ttu-id="3f5e8-143">기본적으로는 `Get-ExecutionPolicy` 유효 실행 정책만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-143">By default, `Get-ExecutionPolicy` gets only the effective execution policy.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3f5e8-144">-범위</span><span class="sxs-lookup"><span data-stu-id="3f5e8-144">-Scope</span></span>

<span data-ttu-id="3f5e8-145">실행 정책의 영향을 받는 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-145">Specifies the scope that is affected by an execution policy.</span></span>

<span data-ttu-id="3f5e8-146">유효한 실행 정책은 다음과 같이 우선 순위에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-146">The effective execution policy is determined by the order of precedence as follows:</span></span>

- <span data-ttu-id="3f5e8-147">**MachinePolicy**.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-147">**MachinePolicy**.</span></span> <span data-ttu-id="3f5e8-148">컴퓨터의 모든 사용자에 대해 그룹 정책 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-148">Set by a Group Policy for all users of the computer.</span></span>
- <span data-ttu-id="3f5e8-149">**Userpolicy**.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-149">**UserPolicy**.</span></span> <span data-ttu-id="3f5e8-150">컴퓨터의 현재 사용자에 대 한 그룹 정책 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-150">Set by a Group Policy for the current user of the computer.</span></span>
- <span data-ttu-id="3f5e8-151">**프로세스**.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-151">**Process**.</span></span> <span data-ttu-id="3f5e8-152">현재 PowerShell 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-152">Affects only the current PowerShell session.</span></span>
- <span data-ttu-id="3f5e8-153">**CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-153">**CurrentUser**.</span></span> <span data-ttu-id="3f5e8-154">현재 사용자 에게만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-154">Affects only the current user.</span></span>
- <span data-ttu-id="3f5e8-155">**LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-155">**LocalMachine**.</span></span> <span data-ttu-id="3f5e8-156">컴퓨터의 모든 사용자에 게 영향을 주는 기본 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-156">Default scope that affects all users of the computer.</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 0
Default value: Effective execution policy
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3f5e8-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3f5e8-157">CommonParameters</span></span>

<span data-ttu-id="3f5e8-158">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3f5e8-159">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3f5e8-160">입력</span><span class="sxs-lookup"><span data-stu-id="3f5e8-160">INPUTS</span></span>

### <span data-ttu-id="3f5e8-161">없음</span><span class="sxs-lookup"><span data-stu-id="3f5e8-161">None</span></span>

<span data-ttu-id="3f5e8-162">`Get-ExecutionPolicy` 파이프라인의 입력을 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-162">`Get-ExecutionPolicy` doesn't accept input from the pipeline.</span></span>

## <span data-ttu-id="3f5e8-163">출력</span><span class="sxs-lookup"><span data-stu-id="3f5e8-163">OUTPUTS</span></span>

### <span data-ttu-id="3f5e8-164">Microsoft.PowerShell.Exe이상 정책</span><span class="sxs-lookup"><span data-stu-id="3f5e8-164">Microsoft.PowerShell.ExecutionPolicy</span></span>

## <span data-ttu-id="3f5e8-165">참고</span><span class="sxs-lookup"><span data-stu-id="3f5e8-165">NOTES</span></span>

<span data-ttu-id="3f5e8-166">실행 정책은 PowerShell 보안 전략의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-166">An execution policy is part of the PowerShell security strategy.</span></span> <span data-ttu-id="3f5e8-167">실행 정책은 PowerShell 프로필과 같은 구성 파일을 로드 하거나 스크립트를 실행할 수 있는지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-167">Execution policies determine whether you can load configuration files, such as your PowerShell profile, or run scripts.</span></span> <span data-ttu-id="3f5e8-168">스크립트를 실행 하기 전에 디지털로 서명 해야 하는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5e8-168">And, whether scripts must be digitally signed before they are run.</span></span>

## <span data-ttu-id="3f5e8-169">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3f5e8-169">RELATED LINKS</span></span>

[<span data-ttu-id="3f5e8-170">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="3f5e8-170">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)

[<span data-ttu-id="3f5e8-171">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="3f5e8-171">about_Group_Policy_Settings</span></span>](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[<span data-ttu-id="3f5e8-172">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="3f5e8-172">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="3f5e8-173">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="3f5e8-173">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="3f5e8-174">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="3f5e8-174">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

