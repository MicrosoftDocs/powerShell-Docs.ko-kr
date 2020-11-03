---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-computersecurechannel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ComputerSecureChannel
ms.openlocfilehash: 20ea76e725a8ab53d7090078dc819a6297a639ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214345"
---
# <span data-ttu-id="36a4e-103">Test-ComputerSecureChannel</span><span class="sxs-lookup"><span data-stu-id="36a4e-103">Test-ComputerSecureChannel</span></span>

## <span data-ttu-id="36a4e-104">개요</span><span class="sxs-lookup"><span data-stu-id="36a4e-104">SYNOPSIS</span></span>
<span data-ttu-id="36a4e-105">로컬 컴퓨터와 해당 도메인 간의 보안 채널을 테스트 및 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-105">Tests and repairs the secure channel between the local computer and its domain.</span></span>

## <span data-ttu-id="36a4e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="36a4e-106">SYNTAX</span></span>

```
Test-ComputerSecureChannel [-Repair] [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="36a4e-107">설명</span><span class="sxs-lookup"><span data-stu-id="36a4e-107">DESCRIPTION</span></span>
<span data-ttu-id="36a4e-108">**테스트 ComputerSecureChannel** cmdlet은 트러스트 관계의 상태를 확인 하 여 로컬 컴퓨터와 해당 도메인 간의 채널이 제대로 작동 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-108">The **Test-ComputerSecureChannel** cmdlet verifies that the channel between the local computer and its domain is working correctly by checking the status of its trust relationships.</span></span>
<span data-ttu-id="36a4e-109">연결에 실패 하면 *Repair* 매개 변수를 사용 하 여 복원을 시도할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-109">If a connection fails, you can use the *Repair* parameter to try to restore it.</span></span>

<span data-ttu-id="36a4e-110">**테스트-ComputerSecureChannel** 은 채널이 제대로 작동 하는 경우 $True을 반환 하 고, 그렇지 않은 경우 $False 합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-110">**Test-ComputerSecureChannel** returns $True if the channel is working correctly and $False if it is not.</span></span>
<span data-ttu-id="36a4e-111">이 결과를 통해 함수와 스크립트의 조건문에서 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-111">This result lets you use the cmdlet in conditional statements in functions and scripts.</span></span>
<span data-ttu-id="36a4e-112">자세한 테스트 결과를 얻으려면 *Verbose* 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-112">To get more detailed test results, use the *Verbose* parameter.</span></span>

<span data-ttu-id="36a4e-113">이 cmdlet은 NetDom.exe와 비슷하게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-113">This cmdlet works much like NetDom.exe.</span></span>
<span data-ttu-id="36a4e-114">NetDom 및 **Test ComputerSecureChannel** 은 모두 **NetLogon** 서비스를 사용 하 여 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-114">Both NetDom and **Test-ComputerSecureChannel** use the **NetLogon** service to perform the actions.</span></span>

## <span data-ttu-id="36a4e-115">예제</span><span class="sxs-lookup"><span data-stu-id="36a4e-115">EXAMPLES</span></span>

### <span data-ttu-id="36a4e-116">예제 1: 로컬 컴퓨터와 해당 도메인 간의 채널 테스트</span><span class="sxs-lookup"><span data-stu-id="36a4e-116">Example 1: Test a channel between the local computer and its domain</span></span>

```
PS C:\> Test-ComputerSecureChannel
True
```

<span data-ttu-id="36a4e-117">이 명령은 로컬 컴퓨터와 해당 컴퓨터가 가입 된 도메인 간의 채널을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-117">This command tests the channel between the local computer and the domain to which it is joined.</span></span>

### <span data-ttu-id="36a4e-118">예 2: 로컬 컴퓨터와 도메인 컨트롤러 간의 채널 테스트</span><span class="sxs-lookup"><span data-stu-id="36a4e-118">Example 2: Test a channel between the local computer and a domain controller</span></span>

```
PS C:\> Test-ComputerSecureChannel -Server "DCName.fabrikam.com"
True
```

<span data-ttu-id="36a4e-119">이 명령은 테스트에 사용할 선호 도메인 컨트롤러를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-119">This command specifies a preferred domain controller for the test.</span></span>

### <span data-ttu-id="36a4e-120">예제 3: 로컬 컴퓨터와 해당 도메인 간의 채널 다시 설정</span><span class="sxs-lookup"><span data-stu-id="36a4e-120">Example 3: Reset the channel between the local computer and its domain</span></span>

```
PS C:\> Test-ComputerSecureChannel -Repair
True
```

<span data-ttu-id="36a4e-121">이 명령은 로컬 컴퓨터와 해당 도메인 간의 채널을 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-121">This command resets the channel between the local computer and its domain.</span></span>

### <span data-ttu-id="36a4e-122">예제 4: 테스트에 대 한 자세한 정보 표시</span><span class="sxs-lookup"><span data-stu-id="36a4e-122">Example 4: Display detailed information about the test</span></span>

```
PS C:\> Test-ComputerSecureChannel -verbose
VERBOSE: Performing operation "Test-ComputerSecureChannel" on Target "SERVER01".
True
VERBOSE: "The secure channel between 'SERVER01' and 'net.fabrikam.com' is alive and working correctly."
```

<span data-ttu-id="36a4e-123">이 명령은 *Verbose* 일반 매개 변수를 사용 하 여 작업에 대 한 자세한 메시지를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-123">This command uses the *Verbose* common parameter to request detailed messages about the operation.</span></span>
<span data-ttu-id="36a4e-124">자세한 정보에 대 *한 자세한 내용은 about_CommonParameters를 참조* 하세요.</span><span class="sxs-lookup"><span data-stu-id="36a4e-124">For more information about *Verbose* , see about_CommonParameters.</span></span>

### <span data-ttu-id="36a4e-125">예 5: 스크립트를 실행 하기 전에 연결 테스트</span><span class="sxs-lookup"><span data-stu-id="36a4e-125">Example 5: Test a connection before you run a script</span></span>

```
PS C:\> Set-Alias tcsc Test-ComputerSecureChannel
if (!(tcsc))
{Write-Host "Connection failed. Reconnect and retry."}
else { &(.\Get-Servers.ps1) }
```

<span data-ttu-id="36a4e-126">이 예제에서는 연결을 요구 하는 스크립트를 실행 하기 전에 **테스트 ComputerSecureChannel** 을 사용 하 여 연결을 테스트 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-126">This example shows how to use **Test-ComputerSecureChannel** to test a connection before you run a script that requires the connection.</span></span>

<span data-ttu-id="36a4e-127">첫 번째 명령은 Set-Alias cmdlet을 사용하여 cmdlet 이름의 별칭을 만들어</span><span class="sxs-lookup"><span data-stu-id="36a4e-127">The first command uses the Set-Alias cmdlet to create an alias for the cmdlet name.</span></span>
<span data-ttu-id="36a4e-128">공간을 저장하고 입력 오류를 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-128">This saves space and prevents typing errors.</span></span>

<span data-ttu-id="36a4e-129">**If** 문은 스크립트를 실행 하기 전에 **테스트-computersecurechannel** 이 반환 하는 값을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-129">The **If** statement checks the value that **Test-ComputerSecureChannel** returns before it runs a script.</span></span>

## <span data-ttu-id="36a4e-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="36a4e-130">PARAMETERS</span></span>

### <span data-ttu-id="36a4e-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="36a4e-131">-Credential</span></span>
<span data-ttu-id="36a4e-132">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-132">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="36a4e-133">User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나 **PSCredential** 개체 (예: Get-Credential cmdlet이 반환 하는 개체)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-133">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one that the Get-Credential cmdlet returns.</span></span>
<span data-ttu-id="36a4e-134">기본적으로 이 cmdlet은 현재 사용자의 자격 증명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-134">By default, the cmdlet uses the credentials of the current user.</span></span>

<span data-ttu-id="36a4e-135">*Credential* 매개 변수는 *repair* 매개 변수를 사용 하 여 컴퓨터와 도메인 간의 채널을 복구 하는 명령에 사용 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-135">The *Credential* parameter is designed for use in commands that use the *Repair* parameter to repair the channel between the computer and the domain.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a4e-136">-복구</span><span class="sxs-lookup"><span data-stu-id="36a4e-136">-Repair</span></span>
<span data-ttu-id="36a4e-137">이 cmdlet이 NetLogon 서비스에 의해 설정 된 채널을 제거한 다음 다시 작성 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-137">Indicates that this cmdlet removes and then rebuilds the channel established by the NetLogon service.</span></span>
<span data-ttu-id="36a4e-138">테스트에 실패 한 연결을 복원 하려면이 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-138">Use this parameter to try to restore a connection that has failed the test.</span></span>

<span data-ttu-id="36a4e-139">이 매개 변수를 사용하려면 현재 사용자가 로컬 컴퓨터 Administrators 그룹의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-139">To use this parameter, the current user must be a member of the Administrators group on the local computer.</span></span>

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

### <span data-ttu-id="36a4e-140">-Server</span><span class="sxs-lookup"><span data-stu-id="36a4e-140">-Server</span></span>
<span data-ttu-id="36a4e-141">명령을 실행할 도메인 컨트롤러를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-141">Specifies the domain controller to run the command.</span></span>
<span data-ttu-id="36a4e-142">이 매개 변수를 지정 하지 않으면이 cmdlet은 작업에 대 한 기본 도메인 컨트롤러를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-142">If this parameter is not specified, this cmdlet selects a default domain controller for the operation.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a4e-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="36a4e-143">-Confirm</span></span>
<span data-ttu-id="36a4e-144">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-144">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="36a4e-145">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="36a4e-145">-WhatIf</span></span>
<span data-ttu-id="36a4e-146">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-146">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="36a4e-147">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-147">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="36a4e-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36a4e-148">CommonParameters</span></span>
<span data-ttu-id="36a4e-149">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="36a4e-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="36a4e-150">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="36a4e-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="36a4e-151">입력</span><span class="sxs-lookup"><span data-stu-id="36a4e-151">INPUTS</span></span>

### <span data-ttu-id="36a4e-152">없음</span><span class="sxs-lookup"><span data-stu-id="36a4e-152">None</span></span>
<span data-ttu-id="36a4e-153">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-153">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="36a4e-154">출력</span><span class="sxs-lookup"><span data-stu-id="36a4e-154">OUTPUTS</span></span>

### <span data-ttu-id="36a4e-155">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="36a4e-155">System.Boolean</span></span>
<span data-ttu-id="36a4e-156">이 cmdlet은 연결이 올바르게 작동 하면 $True을 반환 하 고, 그렇지 않으면 $False 합니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-156">This cmdlet returns $True if the connection is working correctly and $False if it is not.</span></span>

## <span data-ttu-id="36a4e-157">참고</span><span class="sxs-lookup"><span data-stu-id="36a4e-157">NOTES</span></span>

* <span data-ttu-id="36a4e-158">Windows Vista 이상 버전의 windows 운영 체제에서 **테스트 컴퓨터 Securechannel** 명령을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 windows PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-158">To run a **Test-ComputerSecureChannel** command on Windows Vista and later versions of the Windows operating system, open Windows PowerShell by using the Run as administrator option.</span></span>
* <span data-ttu-id="36a4e-159">**테스트 ComputerSecureChannel** 은 Netlogon 서비스의 다양 한 측면을 제어 하는 **I_NetLogonControl2** 함수를 사용 하 여 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36a4e-159">**Test-ComputerSecureChannel** is implemented by using the **I_NetLogonControl2** function, which controls various aspects of the Netlogon service.</span></span>

## <span data-ttu-id="36a4e-160">관련 링크</span><span class="sxs-lookup"><span data-stu-id="36a4e-160">RELATED LINKS</span></span>

[<span data-ttu-id="36a4e-161">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="36a4e-161">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="36a4e-162">ComputerMachinePassword 재설정</span><span class="sxs-lookup"><span data-stu-id="36a4e-162">Reset-ComputerMachinePassword</span></span>](Reset-ComputerMachinePassword.md)

[<span data-ttu-id="36a4e-163">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="36a4e-163">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="36a4e-164">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="36a4e-164">Stop-Computer</span></span>](Stop-Computer.md)
