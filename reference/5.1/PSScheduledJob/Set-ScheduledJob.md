---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJob
ms.openlocfilehash: 99dbdc84430c0a8b5cf505a22b139cd07236e160
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213369"
---
# <span data-ttu-id="1dfe0-103">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="1dfe0-103">Set-ScheduledJob</span></span>

## <span data-ttu-id="1dfe0-104">개요</span><span class="sxs-lookup"><span data-stu-id="1dfe0-104">SYNOPSIS</span></span>
<span data-ttu-id="1dfe0-105">예약된 작업을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-105">Changes scheduled jobs.</span></span>

## <span data-ttu-id="1dfe0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1dfe0-106">SYNTAX</span></span>

### <span data-ttu-id="1dfe0-107">ScriptBlock (기본값)</span><span class="sxs-lookup"><span data-stu-id="1dfe0-107">ScriptBlock (Default)</span></span>

```
Set-ScheduledJob [-Name <String>] [-ScriptBlock <ScriptBlock>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### <span data-ttu-id="1dfe0-108">FilePath</span><span class="sxs-lookup"><span data-stu-id="1dfe0-108">FilePath</span></span>

```
Set-ScheduledJob [-Name <String>] [-FilePath <String>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### <span data-ttu-id="1dfe0-109">실행</span><span class="sxs-lookup"><span data-stu-id="1dfe0-109">Execution</span></span>

```
Set-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-ClearExecutionHistory] [-PassThru]
 [<CommonParameters>]
```

## <span data-ttu-id="1dfe0-110">설명</span><span class="sxs-lookup"><span data-stu-id="1dfe0-110">DESCRIPTION</span></span>
<span data-ttu-id="1dfe0-111">**Set-ScheduledJob** cmdlet은 작업이 실행하는 명령 또는 작업을 실행하는 데 필요한 자격 증명과 같은 예약된 작업의 속성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-111">The **Set-ScheduledJob** cmdlet changes the properties of scheduled jobs, such as the commands that the jobs run or the credentials required to run the job.</span></span>
<span data-ttu-id="1dfe0-112">이 cmdlet을 사용하여 예약된 작업의 실행 기록을 지울 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-112">You can also use it to clear the execution history of the scheduled job.</span></span>

<span data-ttu-id="1dfe0-113">이 cmdlet을 사용 하려면 먼저 Get-ScheduledJob cmdlet을 사용 하 여 예약 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-113">To use this cmdlet, begin by using the Get-ScheduledJob cmdlet to get the scheduled job.</span></span>
<span data-ttu-id="1dfe0-114">그런 다음 예약 된 작업을 **set-scheduledjob** 로 파이프 하거나 작업을 변수에 저장 하 고 *InputObject* 매개 변수를 사용 하 여 작업을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-114">Then, pipe the scheduled job to **Set-ScheduledJob** or save the job in a variable and use the *InputObject* parameter to identify the job.</span></span>
<span data-ttu-id="1dfe0-115">**Set-ScheduledJob** 의 나머지 매개 변수를 사용하여 작업 속성을 변경하거나 실행 기록을 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-115">Use the remaining parameters of **Set-ScheduledJob** to change the job properties or clear the execution history.</span></span>

<span data-ttu-id="1dfe0-116">**Set-scheduledjob** 를 사용 하 여 예약 된 작업의 트리거 및 옵션을 변경할 수 있지만 추가 Jobtrigger, Set-jobtrigger 및 Set-ScheduledJobOption cmdlet을 사용 하면 이러한 작업을 보다 쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-116">Although you can use **Set-ScheduledJob** to change the triggers and options of a scheduled job, the Add-JobTrigger, Set-JobTrigger, and Set-ScheduledJobOption cmdlets provide much easier ways to accomplish those tasks.</span></span>
<span data-ttu-id="1dfe0-117">새 예약 된 작업을 만들려면 Register-ScheduledJob cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-117">To create a new scheduled job, use the Register-ScheduledJob cmdlet.</span></span>

<span data-ttu-id="1dfe0-118">**Set-scheduledjob** 의 *Trigger* 매개 변수는 작업을 시작 하는 하나 이상의 작업 트리거를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-118">The *Trigger* parameter of **Set-ScheduledJob** adds one or more job triggers that start the job.</span></span>
<span data-ttu-id="1dfe0-119">*Trigger* 매개 변수는 선택 사항 이므로 예약 된 작업을 만들고, 나중에 작업 트리거를 추가 하 고, *runnow* 매개 변수를 추가 하 여 즉시 작업을 시작 하거나, Start-Job cmdlet을 사용 하 여 언제 든 지 작업을 즉시 시작 하거나, 트리거된 예약 되지 않은 작업을 다른 작업의 템플릿으로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-119">The *Trigger* parameter is optional, so you can add triggers when you create the scheduled job, add job triggers later, add the *RunNow* parameter to start the job immediately, use the Start-Job cmdlet to start the job immediately at any time, or save the untriggered scheduled job as a template for other jobs.</span></span>

<span data-ttu-id="1dfe0-120">**Set-scheduledjob** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-120">**Set-ScheduledJob** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="1dfe0-121">예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-121">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="1dfe0-122">PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-122">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="1dfe0-123">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-123">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="1dfe0-124">예제</span><span class="sxs-lookup"><span data-stu-id="1dfe0-124">EXAMPLES</span></span>

### <span data-ttu-id="1dfe0-125">예제 1: 작업이 실행 하는 스크립트 변경</span><span class="sxs-lookup"><span data-stu-id="1dfe0-125">Example 1: Change the script that a job runs</span></span>

```
PS C:\> Get-ScheduledJob -Name "Inventory"
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-Inventory.ps1             True

The second command uses the Get-ScheduledJob cmdlet to get the Inventory scheduled job. A pipeline operator (|) sends the scheduled job to the **Set-ScheduledJob** cmdlet. The **Set-ScheduledJob** cmdlet uses the *Script* parameter to specify a new script, Get-FullInventory.ps1. The command uses the *Passthru* parameter to return the scheduled job after the change.
PS C:\> Get-ScheduledJob -Name "Inventory" | Set-ScheduledJob -FilePath "C:\Scripts\Get-FullInventory.ps1" -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-FullInventory.ps1         True
```

<span data-ttu-id="1dfe0-126">이 예제에서는 예약된 작업에서 실행되는 스크립트를 변경하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-126">This example shows how to change the script that is run in a scheduled job.</span></span>

<span data-ttu-id="1dfe0-127">첫 번째 명령은 Get-ScheduledJob cmdlet을 사용 하 여 Inventory 예약 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-127">The first command uses the Get-ScheduledJob cmdlet to get the Inventory scheduled job.</span></span>
<span data-ttu-id="1dfe0-128">출력은 작업에서 Get-Inventory.ps1 스크립트를 실행함을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-128">The output shows that the job runs the Get-Inventory.ps1 script.</span></span>

<span data-ttu-id="1dfe0-129">이 명령은 필수가 아닙니다. 단지 스크립트 변경의 결과를 보여 주기 위해 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-129">This command is not required; it is included only to show the effect of the script change.</span></span>

### <span data-ttu-id="1dfe0-130">예 2: 예약 된 작업의 실행 기록 삭제</span><span class="sxs-lookup"><span data-stu-id="1dfe0-130">Example 2: Delete the execution history of a scheduled job</span></span>

```
PS C:\> Get-ScheduledJob BackupArchive | Set-ScheduledJob -ClearExecutionHistory
```

<span data-ttu-id="1dfe0-131">이 명령은 BackupArchive 예약된 작업의 현재 실행 기록과 저장된 작업 결과를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-131">This command deletes the current execution history and saved job results for the BackupArchive scheduled job.</span></span>

<span data-ttu-id="1dfe0-132">이 명령은 Get-ScheduledJob cmdlet을 사용 하 여 BackupArchive 예약 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-132">The command uses the Get-ScheduledJob cmdlet to get the BackupArchive scheduled job.</span></span>
<span data-ttu-id="1dfe0-133">파이프라인 연산자(|)가 작업을 **Set-ScheduledJob** cmdlet으로 보내 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-133">A pipeline operator (|) sends the job to the **Set-ScheduledJob** cmdlet to change it.</span></span>
<span data-ttu-id="1dfe0-134">**Set-scheduledjob** Cmdlet은 *ClearExecutionHistory* 매개 변수를 사용 하 여 실행 기록과 저장 된 결과를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-134">The **Set-ScheduledJob** cmdlet uses the *ClearExecutionHistory* parameter to delete the execution history and saved results.</span></span>

<span data-ttu-id="1dfe0-135">예약된 작업의 실행 기록과 저장된 작업 결과에 대한 자세한 내용은 about_Scheduled_Jobs를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-135">For more information about the execution history and saved job results of scheduled jobs, see about_Scheduled_Jobs.</span></span>

### <span data-ttu-id="1dfe0-136">예 3: 원격 컴퓨터에서 예약 된 작업 변경</span><span class="sxs-lookup"><span data-stu-id="1dfe0-136">Example 3: Change scheduled jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -Computer "Server01, Server02" -ScriptBlock {Get-ScheduledJob | Set-ScheduledJob -InitializationScript \\SrvA\Scripts\SetForRun.ps1}
```

<span data-ttu-id="1dfe0-137">이 명령은 Server01 및 Server02 컴퓨터에 있는 모든 예약된 작업의 초기화 스크립트를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-137">This command changes the initialization script in all scheduled jobs on the Server01 and Server02 computers.</span></span>

<span data-ttu-id="1dfe0-138">이 명령은 Invoke-Command cmdlet을 사용 하 여 Server01 및 Server02 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-138">The command uses the Invoke-Command cmdlet to run a command on the Server01 and Server02 computers.</span></span>

<span data-ttu-id="1dfe0-139">원격 명령은 컴퓨터의 모든 예약 된 작업을 가져오는 Get-ScheduledJob 명령으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-139">The remote command begins with a Get-ScheduledJob command that gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="1dfe0-140">예약 된 작업은 **set-scheduledjob** cmdlet으로 파이프 되며,이 cmdlet은 초기화 스크립트를 SetForRun.ps1 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-140">The scheduled jobs are piped to the **Set-ScheduledJob** cmdlet, which changes the initialization script to SetForRun.ps1.</span></span>

## <span data-ttu-id="1dfe0-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1dfe0-141">PARAMETERS</span></span>

### <span data-ttu-id="1dfe0-142">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="1dfe0-142">-ArgumentList</span></span>
<span data-ttu-id="1dfe0-143">*FilePath* 매개 변수에 지정된 스크립트의 매개 변수 값이나 *ScriptBlock* 매개 변수에 지정된 명령의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-143">Specifies values for the parameters of the script that is specified by the *FilePath* parameter or for the command that is specified by the *ScriptBlock* parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1dfe0-144">-인증</span><span class="sxs-lookup"><span data-stu-id="1dfe0-144">-Authentication</span></span>
<span data-ttu-id="1dfe0-145">사용자 자격 증명을 인증하는 데 사용되는 메커니즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-145">Specifies the mechanism that is used to authenticate the user's credentials.</span></span>
<span data-ttu-id="1dfe0-146">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1dfe0-147">기본값</span><span class="sxs-lookup"><span data-stu-id="1dfe0-147">Default</span></span>
- <span data-ttu-id="1dfe0-148">Basic</span><span class="sxs-lookup"><span data-stu-id="1dfe0-148">Basic</span></span>
- <span data-ttu-id="1dfe0-149">Credssp</span><span class="sxs-lookup"><span data-stu-id="1dfe0-149">Credssp</span></span>
- <span data-ttu-id="1dfe0-150">다이제스트</span><span class="sxs-lookup"><span data-stu-id="1dfe0-150">Digest</span></span>
- <span data-ttu-id="1dfe0-151">Kerberos</span><span class="sxs-lookup"><span data-stu-id="1dfe0-151">Kerberos</span></span>
- <span data-ttu-id="1dfe0-152">Negotiate</span><span class="sxs-lookup"><span data-stu-id="1dfe0-152">Negotiate</span></span>
- <span data-ttu-id="1dfe0-153">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="1dfe0-153">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="1dfe0-154">기본값은 Default입니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-154">The default value is Default.</span></span>
<span data-ttu-id="1dfe0-155">이 매개 변수 값에 대 한 자세한 내용은 MSDN library에서 [Authenticationmechanism 열거](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-155">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) in the MSDN library.</span></span>

<span data-ttu-id="1dfe0-156">주의: 사용자의 자격 증명이 인증을 위해 원격 컴퓨터에 전달 되는 CredSSP (자격 증명 보안 지원 공급자) 인증은 원격 네트워크 공유에 액세스 하는 것과 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-156">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
<span data-ttu-id="1dfe0-157">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-157">This mechanism increases the security risk of the remote operation.</span></span>
<span data-ttu-id="1dfe0-158">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-158">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ScriptBlock, FilePath
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1dfe0-159">-ClearExecutionHistory</span><span class="sxs-lookup"><span data-stu-id="1dfe0-159">-ClearExecutionHistory</span></span>
<span data-ttu-id="1dfe0-160">예약된 작업의 현재 실행 기록과 저장된 결과를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-160">Deletes the current execution history and the saved results of the scheduled job.</span></span>

<span data-ttu-id="1dfe0-161">작업 실행 기록과 작업 결과는 예약된 작업과 함께 작업이 만들어진 컴퓨터의 $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs 디렉터리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-161">The job execution history and job results are saved with the scheduled job in the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs directory on the computer on which the job is created.</span></span>
<span data-ttu-id="1dfe0-162">실행 기록을 보려면 Get-Job cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-162">To see the execution history, use the Get-Job cmdlet.</span></span>
<span data-ttu-id="1dfe0-163">작업 결과를 가져오려면 Receive-Job cmdlet을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-163">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="1dfe0-164">이 매개 변수는 작업 스케줄러가 Windows 이벤트 로그에 쓰는 이벤트에 영향을 주지 않으며 Windows PowerShell에서 작업 결과를 저장하도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-164">This parameter does not affect the events that Task Scheduler writes to the Windows event logs and it does not stop Windows PowerShell from saving job results.</span></span>
<span data-ttu-id="1dfe0-165">저장되는 작업 결과 수를 관리하려면 *MaxResultCount* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-165">To manage the number of job results that are saved, use the *MaxResultCount* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Execution
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1dfe0-166">-Credential</span><span class="sxs-lookup"><span data-stu-id="1dfe0-166">-Credential</span></span>
<span data-ttu-id="1dfe0-167">예약된 작업을 실행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-167">Specifies a user account that has permission to run the scheduled job.</span></span>
<span data-ttu-id="1dfe0-168">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-168">The default is the current user.</span></span>

<span data-ttu-id="1dfe0-169">User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나 **PSCredential** 개체 (예: Get-Credential cmdlet의 개체)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-169">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one from the Get-Credential cmdlet.</span></span>
<span data-ttu-id="1dfe0-170">사용자 이름만 입력하면 암호를 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-170">If you enter only a user name, you will be prompted for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1dfe0-171">-FilePath</span><span class="sxs-lookup"><span data-stu-id="1dfe0-171">-FilePath</span></span>
<span data-ttu-id="1dfe0-172">예약된 작업이 실행하는 스크립트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-172">Specifies a script that the scheduled job runs.</span></span>
<span data-ttu-id="1dfe0-173">로컬 컴퓨터에 있는 .ps1 파일의 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-173">Enter the path to a .ps1 file on the local computer.</span></span>
<span data-ttu-id="1dfe0-174">스크립트 매개 변수의 기본값을 지정하려면 *ArgumentList* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-174">To specify default values for the script parameters, use the *ArgumentList* parameter.</span></span>
<span data-ttu-id="1dfe0-175">각 예약된 작업에 *ScriptBlock* 또는 *FilePath* 값이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-175">Every scheduled job must have either a *ScriptBlock* or *FilePath* value.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1dfe0-176">-또한 initializationscript</span><span class="sxs-lookup"><span data-stu-id="1dfe0-176">-InitializationScript</span></span>
<span data-ttu-id="1dfe0-177">Windows PowerShell 스크립트(.ps1)에 대한 정규화된 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-177">Specifies the fully qualified path to a Windows PowerShell script (.ps1).</span></span>
<span data-ttu-id="1dfe0-178">초기화 스크립트는 백그라운드 작업에 대해 만들어진 세션에서 *ScriptBlock* 매개 변수에 지정된 명령이나 *FilePath* 매개 변수에 지정된 스크립트보다 먼저 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-178">The initialization script runs in the session that is created for the background job before the commands that are specified by the *ScriptBlock* parameter or the script that is specified by the *FilePath* parameter.</span></span>
<span data-ttu-id="1dfe0-179">초기화 스크립트를 사용하여 파일, 함수 또는 별칭 추가, 디렉터리 만들기, 필수 조건 확인 등 세션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-179">You can use the initialization script to configure the session, such as adding files, functions, or aliases, creating directories, or checking for prerequisites.</span></span>

<span data-ttu-id="1dfe0-180">주요 작업 명령을 실행하는 스크립트를 지정하려면 *FilePath* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-180">To specify a script that runs the primary job commands, use the *FilePath* parameter.</span></span>

<span data-ttu-id="1dfe0-181">초기화 스크립트에서 종료 되지 않는 오류를 포함 하 여 오류를 생성 하는 경우 예약 된 작업의 현재 인스턴스가 실행 되지 않으며 상태는 실패입니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-181">If the initialization script generates an error, including a non-terminating error, the current instance of the scheduled job does not run and its status is Failed.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1dfe0-182">-InputObject</span><span class="sxs-lookup"><span data-stu-id="1dfe0-182">-InputObject</span></span>
<span data-ttu-id="1dfe0-183">변경할 예약된 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-183">Specifies the scheduled job to be changed.</span></span>
<span data-ttu-id="1dfe0-184">**ScheduledJobDefinition** 개체가 포함 된 변수를 입력 하거나 **ScheduledJobDefinition** 개체를 가져오는 명령 또는 식 (예: Get-ScheduledJob 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-184">Enter a variable that contains **ScheduledJobDefinition** objects or type a command or expression that gets **ScheduledJobDefinition** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="1dfe0-185">**ScheduledJobDefinition** 개체를 **set-scheduledjob** 로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-185">You can also pipe a **ScheduledJobDefinition** object to **Set-ScheduledJob** .</span></span>

<span data-ttu-id="1dfe0-186">여러 개의 예약된 작업을 지정할 경우 **Set-ScheduledJob** 은 모든 작업에 동일한 변경을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-186">If you specify multiple scheduled jobs, **Set-ScheduledJob** makes the same changes to all jobs.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1dfe0-187">-MaxResultCount</span><span class="sxs-lookup"><span data-stu-id="1dfe0-187">-MaxResultCount</span></span>
<span data-ttu-id="1dfe0-188">예약된 작업에 대해 유지 관리할 작업 결과 항목 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-188">Specifies how many job result entries are maintained for the scheduled job.</span></span>
<span data-ttu-id="1dfe0-189">기본값은 32입니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-189">The default value is 32.</span></span>

<span data-ttu-id="1dfe0-190">Windows PowerShell은 트리거된 각 예약된 작업 인스턴스의 실행 기록과 결과를 디스크에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-190">Windows PowerShell saves the execution history and results of each triggered instance of the scheduled job on disk.</span></span>
<span data-ttu-id="1dfe0-191">이 매개 변수 값은 이 예약된 작업에 대해 저장되는 작업 인스턴스 결과 수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-191">The value of this parameter determines the number of job instance results that are saved for this scheduled job.</span></span>
<span data-ttu-id="1dfe0-192">작업 인스턴스 결과 수가 이 값을 초과할 경우 Windows PowerShell은 가장 오래된 작업 인스턴스 결과를 삭제하여 최신 작업 인스턴스 결과를 저장할 공간을 확보합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-192">When the number of job instance results exceeds this value, Windows PowerShell deletes the results of the oldest job instance to make room for the results of the newest job instance.</span></span>

<span data-ttu-id="1dfe0-193">작업 실행 기록과 작업 결과는 \\ \<JobName\> \\ \<Timestamp\> 작업이 만들어진 컴퓨터의 $home \appdata\local\microsoft\windows\powershell\scheduledjobs \\output 디렉터리에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-193">The job execution history and job results are saved in the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\\\<JobName\>\Output\\\<Timestamp\> directories on the computer on which the job is created.</span></span>
<span data-ttu-id="1dfe0-194">실행 기록을 보려면 Get-Job cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-194">To see the execution history, use the Get-Job cmdlet.</span></span>
<span data-ttu-id="1dfe0-195">작업 결과를 가져오려면 Receive-Job cmdlet을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-195">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="1dfe0-196">*MaxResultCount* 매개 변수는 예약된 작업의 ExecutionHistoryLength 속성 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-196">The *MaxResultCount* parameter sets the value of the ExecutionHistoryLength property of the scheduled job.</span></span>

<span data-ttu-id="1dfe0-197">현재 실행 기록과 작업 결과를 삭제하려면 *ClearExecutionHistory* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-197">To delete the current execution history and job results, use the *ClearExecutionHistory* parameter.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1dfe0-198">-Name</span><span class="sxs-lookup"><span data-stu-id="1dfe0-198">-Name</span></span>
<span data-ttu-id="1dfe0-199">예약된 작업 및 예약된 작업 인스턴스의 새 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-199">Specifies a new name for the scheduled job and instances of the scheduled job.</span></span>
<span data-ttu-id="1dfe0-200">이름은 로컬 컴퓨터에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-200">The name must be unique on the local computer.</span></span>

<span data-ttu-id="1dfe0-201">변경할 예약 된 작업을 식별 하려면 *InputObject* 매개 변수를 사용 하거나 예약 된 작업을 Get-ScheduledJob에서 **set-scheduledjob** 로 파이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-201">To identify the scheduled job to be changed, use the *InputObject* parameter or pipe a scheduled job from Get-ScheduledJob to **Set-ScheduledJob** .</span></span>

<span data-ttu-id="1dfe0-202">이 매개 변수는 디스크에 있는 작업 인스턴스의 이름을 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-202">This parameter does not change the names of job instances on disk.</span></span>
<span data-ttu-id="1dfe0-203">이 명령이 완료된 후 시작되는 작업 인스턴스에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-203">It affects only job instances that are started after this command completes.</span></span>

```yaml
Type: System.String
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1dfe0-204">-PassThru</span><span class="sxs-lookup"><span data-stu-id="1dfe0-204">-PassThru</span></span>
<span data-ttu-id="1dfe0-205">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-205">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="1dfe0-206">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-206">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="1dfe0-207">-체제가 있어도 runas32</span><span class="sxs-lookup"><span data-stu-id="1dfe0-207">-RunAs32</span></span>
<span data-ttu-id="1dfe0-208">32비트 프로세스로 예약된 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-208">Runs the scheduled job in a 32-bit process.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1dfe0-209">-RunEvery</span><span class="sxs-lookup"><span data-stu-id="1dfe0-209">-RunEvery</span></span>

<span data-ttu-id="1dfe0-210">작업 실행 빈도를 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-210">Used to specify how often to run the job.</span></span> <span data-ttu-id="1dfe0-211">예를 들어이 옵션을 사용 하 여 15 분 마다 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-211">For example, use this option to run a job every 15 minutes.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1dfe0-212">-RunNow</span><span class="sxs-lookup"><span data-stu-id="1dfe0-212">-RunNow</span></span>
<span data-ttu-id="1dfe0-213">**Set-scheduledjob** cmdlet이 실행 되는 즉시 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-213">Starts a job immediately, as soon as the **Set-ScheduledJob** cmdlet is run.</span></span>
<span data-ttu-id="1dfe0-214">이 매개 변수를 사용할 경우 등록 후 즉시 Windows PowerShell스크립트를 실행하기 위해 작업 스케줄러를 트리거할 필요가 없으며 사용자가 시작 날짜 및 시간을 지정하는 트리거를 만들지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-214">This parameter eliminates the need to trigger Task Scheduler to run a Windows PowerShell script immediately after registration, and does not require users to create a trigger that specifies a starting date and time.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1dfe0-215">-Set-scheduledjoboption</span><span class="sxs-lookup"><span data-stu-id="1dfe0-215">-ScheduledJobOption</span></span>
<span data-ttu-id="1dfe0-216">예약된 작업에 대한 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-216">Sets options for the scheduled job.</span></span>
<span data-ttu-id="1dfe0-217">New-ScheduledJobOption cmdlet을 사용 하 여 만든 개체 또는 해시 테이블 값과 같은 **ScheduledJobOptions** 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-217">Enter a **ScheduledJobOptions** object, such as one that you create by using the New-ScheduledJobOption cmdlet, or a hash table value.</span></span>

<span data-ttu-id="1dfe0-218">예약 된 작업을 등록할 때 예약 된 작업에 대 한 옵션을 설정 하거나 Set-ScheduledJobOption 또는 **set-scheduledjob** cmdlet을 사용 하 여 옵션을 설정 하거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-218">You can set options for a scheduled job when you register the scheduled job or use the Set-ScheduledJobOption or **Set-ScheduledJob** cmdlets to set or change options.</span></span>

<span data-ttu-id="1dfe0-219">많은 옵션과 해당 기본값은 예약된 작업의 실행 여부와 시기를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-219">Many of the options and their default values determine whether and when a scheduled job runs.</span></span>
<span data-ttu-id="1dfe0-220">작업을 예약하기 전에 이러한 옵션을 검토해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-220">Be sure to review these options before scheduling a job.</span></span>
<span data-ttu-id="1dfe0-221">기본 값을 포함 하 여 예약 된 작업 옵션에 대 한 자세한 내용은 Set-scheduledjoboption를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-221">For a description of the scheduled job options, including the default values, see New-ScheduledJobOption.</span></span>

<span data-ttu-id="1dfe0-222">해시 테이블을 제출하려면 다음 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-222">To submit a hash table, use the following keys.</span></span>
<span data-ttu-id="1dfe0-223">다음 해시 테이블에 키와 해당 기본값이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-223">In the following hash table, the keys are shown with their default values.</span></span>

`@{# Power SettingsStartIfOnBattery=$False;StopIfGoingOnBattery=$True; WakeToRun=$False; # Idle SettingsStartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False;# Security settingsShowInTaskScheduler=$TrueRunElevated=$False;# MiscRunWithoutNetwork=$False;DoNotAllowDemandStart=$False;MultipleInstancePolicy=IgnoreNew# Can be IgnoreNew, Parallel, Queue, StopExisting}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1dfe0-224">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="1dfe0-224">-ScriptBlock</span></span>
<span data-ttu-id="1dfe0-225">예약된 작업이 실행하는 명령을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-225">Specifies the commands that the scheduled job runs.</span></span>
<span data-ttu-id="1dfe0-226">명령을 중괄호( { } )로 묶어 스크립트 블록을 만드세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-226">Enclose the commands in braces ( { } ) to create a script block.</span></span>
<span data-ttu-id="1dfe0-227">명령 매개 변수의 기본값을 지정하려면 *ArgumentList* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-227">To specify default values for command parameters, use the *ArgumentList* parameter.</span></span>

<span data-ttu-id="1dfe0-228">모든 Register-ScheduledJob 명령은 *ScriptBlock* 또는 *FilePath* 매개 변수를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-228">Every Register-ScheduledJob command must use either the *ScriptBlock* or *FilePath* parameters.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1dfe0-229">-트리거</span><span class="sxs-lookup"><span data-stu-id="1dfe0-229">-Trigger</span></span>
<span data-ttu-id="1dfe0-230">예약된 작업의 트리거를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-230">Specifies the triggers for the scheduled job.</span></span>
<span data-ttu-id="1dfe0-231">New-JobTrigger cmdlet이 반환 하는 개체 또는 작업 트리거 키 및 값의 해시 테이블 같은 **ScheduledJobTrigger** 개체를 하나 이상 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-231">Enter one or more **ScheduledJobTrigger** objects, such as the objects that the New-JobTrigger cmdlet returns, or a hash table of job trigger keys and values.</span></span>

<span data-ttu-id="1dfe0-232">작업 트리거는 일회성 또는 되풀이 일정에 따라 또는 이벤트가 발생 하는 경우 예약 된 작업을 자동으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-232">A job trigger starts a scheduled job automatically on a one-time or recurring scheduled or when an event occurs.</span></span>

<span data-ttu-id="1dfe0-233">작업 트리거는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-233">Job triggers are optional.</span></span>
<span data-ttu-id="1dfe0-234">예약 된 작업을 만들 때 트리거를 추가 하거나, Add-JobTrigger 또는 **set-scheduledjob** cmdlet을 사용 하 여 나중에 트리거를 추가 하거나, Start-Job cmdlet을 사용 하 여 예약 된 작업을 즉시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-234">You can add a trigger when you create the scheduled job, use the Add-JobTrigger or **Set-ScheduledJob** cmdlets to add triggers later, or use the Start-Job cmdlet to start the scheduled job immediately.</span></span>
<span data-ttu-id="1dfe0-235">작업 트리거 없는 예약된 작업을 만들어 유지 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-235">You can also create and maintain a scheduled job that has no job triggers.</span></span>

<span data-ttu-id="1dfe0-236">해시 테이블을 제출하려면 다음 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-236">To submit a hash table, use the following keys.</span></span>

<span data-ttu-id="1dfe0-237">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` 또는 유효한 시간 문자열입니다. `DaysOfWeek="Monday", "Wednesday"` (또는 요일 이름의 조합) `Interval=2` (또는 유효한 빈도 간격); `RandomDelay="30minutes"` (또는 유효한 timespan 문자열) `User="Domain1\User01"` 또는 모든 유효한 사용자 (AtLogon frequency 값 에서만 사용)</span><span class="sxs-lookup"><span data-stu-id="1dfe0-237">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (or any valid time string); `DaysOfWeek="Monday", "Wednesday"` (or any combination of day names); `Interval=2` (or any valid frequency interval); `RandomDelay="30minutes"` (or any valid timespan string); `User="Domain1\User01"` (or any valid user; used only with the AtLogon frequency value)</span></span>

<span data-ttu-id="1dfe0-238">}</span><span class="sxs-lookup"><span data-stu-id="1dfe0-238">}</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1dfe0-239">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1dfe0-239">CommonParameters</span></span>
<span data-ttu-id="1dfe0-240">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-240">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1dfe0-241">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-241">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1dfe0-242">입력</span><span class="sxs-lookup"><span data-stu-id="1dfe0-242">INPUTS</span></span>

### <span data-ttu-id="1dfe0-243">Set-scheduledjob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="1dfe0-243">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="1dfe0-244">예약된 작업을 **Set-ScheduledJob** 으로 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-244">You can pipe scheduled jobs to **Set-ScheduledJob** .</span></span>

## <span data-ttu-id="1dfe0-245">출력</span><span class="sxs-lookup"><span data-stu-id="1dfe0-245">OUTPUTS</span></span>

### <span data-ttu-id="1dfe0-246">None 또는 Set-scheduledjob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="1dfe0-246">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="1dfe0-247">*Passthru* 매개 변수를 사용할 경우 **Set-ScheduledJob** 은 변경된 예약된 작업을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-247">If you use the *Passthru* parameter, **Set-ScheduledJob** returns the scheduled job that was changed.</span></span>
<span data-ttu-id="1dfe0-248">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1dfe0-248">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1dfe0-249">참고</span><span class="sxs-lookup"><span data-stu-id="1dfe0-249">NOTES</span></span>

## <span data-ttu-id="1dfe0-250">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1dfe0-250">RELATED LINKS</span></span>

[<span data-ttu-id="1dfe0-251">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="1dfe0-251">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="1dfe0-252">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="1dfe0-252">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="1dfe0-253">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="1dfe0-253">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="1dfe0-254">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="1dfe0-254">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="1dfe0-255">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="1dfe0-255">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="1dfe0-256">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="1dfe0-256">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="1dfe0-257">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="1dfe0-257">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="1dfe0-258">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="1dfe0-258">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="1dfe0-259">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="1dfe0-259">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="1dfe0-260">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="1dfe0-260">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="1dfe0-261">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="1dfe0-261">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="1dfe0-262">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="1dfe0-262">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="1dfe0-263">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="1dfe0-263">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="1dfe0-264">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="1dfe0-264">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="1dfe0-265">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="1dfe0-265">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="1dfe0-266">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="1dfe0-266">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
