---
external help file: Microsoft.PowerShell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflowUtility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflowutility/invoke-asworkflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-AsWorkflow
ms.openlocfilehash: b96bce9fe4d574fe2b7e9c7c0f1e05ee0508adce
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213354"
---
# <span data-ttu-id="ea087-103">Invoke-AsWorkflow</span><span class="sxs-lookup"><span data-stu-id="ea087-103">Invoke-AsWorkflow</span></span>

## <span data-ttu-id="ea087-104">개요</span><span class="sxs-lookup"><span data-stu-id="ea087-104">SYNOPSIS</span></span>
<span data-ttu-id="ea087-105">명령 또는 식을 Windows PowerShell 워크플로로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-105">Runs a command or expression as a Windows PowerShell Workflow.</span></span>

## <span data-ttu-id="ea087-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ea087-106">SYNTAX</span></span>

### <span data-ttu-id="ea087-107">Command (기본값)</span><span class="sxs-lookup"><span data-stu-id="ea087-107">Command (Default)</span></span>

```
Invoke-AsWorkflow [-CommandName <String>] [-Parameter <Hashtable>] [-InputObject <Object>] [<CommonParameters>]
```

### <span data-ttu-id="ea087-108">식</span><span class="sxs-lookup"><span data-stu-id="ea087-108">Expression</span></span>

```
Invoke-AsWorkflow [-Expression <String>] [-InputObject <Object>] [<CommonParameters>]
```

## <span data-ttu-id="ea087-109">설명</span><span class="sxs-lookup"><span data-stu-id="ea087-109">DESCRIPTION</span></span>

<span data-ttu-id="ea087-110">`Invoke-AsWorkflow`워크플로는 워크플로에서 모든 명령 또는 식을 인라인 스크립트로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-110">The `Invoke-AsWorkflow` workflow runs any command or expression as an inline script in a workflow.</span></span>
<span data-ttu-id="ea087-111">이러한 워크플로는 표준 워크플로 의미 체계를 사용하고 모든 워크플로 일반 매개 변수를 포함하며 중지, 다시 시작 및 복구 기능을 비롯한 모든 워크플로 이점을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-111">These workflows use the standard workflow semantics, have all workflow common parameters, and have all benefits of workflows, including the ability to stop, resume, and recover.</span></span>

<span data-ttu-id="ea087-112">워크플로는 중요한 데이터를 수집하는 오래 실행되는 명령을 위해 설계되었지만 모든 명령을 실행하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-112">Workflows are designed for long-running commands that collect critical data, but can be used to run any command.</span></span>
<span data-ttu-id="ea087-113">자세한 내용은 [about_Workflows](../PSWorkflow/About/about_Workflows.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ea087-113">For more information, see [about_Workflows](../PSWorkflow/About/about_Workflows.md).</span></span>

<span data-ttu-id="ea087-114">또한 이 명령에 워크플로 일반 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-114">You can also add workflow common parameters to this command.</span></span>
<span data-ttu-id="ea087-115">워크플로 일반 매개 변수에 대 한 자세한 내용은을 참조 하십시오 [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)</span><span class="sxs-lookup"><span data-stu-id="ea087-115">For more information about workflow common parameters, see [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)</span></span>

<span data-ttu-id="ea087-116">이 워크플로는 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-116">This workflow is introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="ea087-117">예제</span><span class="sxs-lookup"><span data-stu-id="ea087-117">EXAMPLES</span></span>

### <span data-ttu-id="ea087-118">예 1: 워크플로로 cmdlet 실행</span><span class="sxs-lookup"><span data-stu-id="ea087-118">Example 1: Run a cmdlet as a workflow</span></span>

```powershell
Invoke-AsWorkflow -PSComputerName (Get-Content Servers.txt) -CommandName Get-ExecutionPolicy
```

```output
PSComputerName                     PSSourceJobInstanceId                   Value
--------------                     ---------------------                   -----
Server01                           77b1cdf8-8226-4662-9067-cd2fa5c3b711    AllSigned
Server02                           a33542d7-3cdd-4339-ab99-0e7cd8e59462    Unrestricted
Server03                           279bac28-066a-4646-9497-8fcdcfe9757e    AllSigned
localhost                          0d858009-2cc4-47a4-a2e0-da17dc2883d0    RemoteSigned
```

<span data-ttu-id="ea087-119">이 명령은 수백 대 `Get-ExecutionPolicy` 의 컴퓨터에서 cmdlet을 워크플로로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-119">This command runs the `Get-ExecutionPolicy` cmdlet as a workflow on hundreds of computers.</span></span>

<span data-ttu-id="ea087-120">이 명령은 **CommandName** 매개 변수를 사용하여 워크플로에서 실행되는 cmdlet을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-120">The command uses the **CommandName** parameter to specify the cmdlet that runs in the workflow.</span></span>
<span data-ttu-id="ea087-121">또한 이 명령은 **PSComputerName** 워크플로 일반 매개 변수를 사용하여 명령이 실행되는 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-121">It uses the **PSComputerName** workflow common parameter to specify the computers on which the command runs.</span></span>
<span data-ttu-id="ea087-122">**PSComputerName** 매개 변수 값은 `Get-Content` Servers.txt 파일에서 컴퓨터 이름 목록을 가져오는 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-122">The value of the **PSComputerName** parameter is a `Get-Content` command that gets a list of computer names from the Servers.txt file.</span></span>
<span data-ttu-id="ea087-123">값을 사용 하기 전에 Windows PowerShell에서 명령을 실행 하도록 지시 하기 위해 매개 변수 값은 괄호로 묶여 `Get-Command` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-123">The parameter value is enclosed in parentheses to direct Windows PowerShell to run the `Get-Command` command before using the value.</span></span>

<span data-ttu-id="ea087-124">모든 원격 명령과 마찬가지로 이 명령이 로컬 컴퓨터에서 실행되는 경우(PSComputerName 매개 변수 값이 로컬 컴퓨터를 포함하는 경우) "관리자 권한으로 실행" 옵션을 사용하여 Windows PowerShell을 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-124">As with all remote commands, if the command runs on the local computer, (if the value of the PSComputerName parameter includes the local computer), you must start Windows PowerShell with the "Run as administrator" option.</span></span>

### <span data-ttu-id="ea087-125">예제 2: 매개 변수를 사용 하 여 cmdlet 실행</span><span class="sxs-lookup"><span data-stu-id="ea087-125">Example 2: Run a cmdlet with parameters</span></span>

```powershell
$s = Import-Csv .\Servers.csv -Header ServerName, ServerID
Invoke-AsWorkflow -CommandName Get-ExecutionPolicy -Parameter @{Scope="Process"} -PSComputerName {$s.ServerName} -PSConnectionRetryCount 5
```

<span data-ttu-id="ea087-126">첫 번째 명령은 cmdlet을 사용 하 여 `Import-Csv` Servers.csv 파일의 콘텐츠에서 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-126">The first command uses the `Import-Csv` cmdlet to create an object from the content in the Servers.csv file.</span></span> <span data-ttu-id="ea087-127">이 명령은 매개 변수를 사용 하 여 `Header` `ServerName` 대상 컴퓨터의 이름을 포함 하는 열에 대 한 속성을 만듭니다 ("원격 노드" 라고도 함).</span><span class="sxs-lookup"><span data-stu-id="ea087-127">The command uses the `Header` parameter to create a `ServerName` property for the column that contains the names of the target computers, also known as "remote nodes."</span></span> <span data-ttu-id="ea087-128">이 명령은 결과를 `$s` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-128">The command saves the result in the `$s` variable.</span></span>

<span data-ttu-id="ea087-129">두 번째 명령은 워크플로를 사용 하 여 `Invoke-AsWorkflow` `Get-ExecutionPolicy` Servers.csv 파일의 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-129">The second command uses the `Invoke-AsWorkflow` workflow to run a `Get-ExecutionPolicy` command on the computers in the Servers.csv file.</span></span> <span data-ttu-id="ea087-130">이 명령은의 **CommandName** 매개 변수를 사용 하 여 `Invoke-AsWorkflow`  워크플로에서 실행할 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-130">The command uses the **CommandName** parameter of `Invoke-AsWorkflow`  to specify the command to run in the workflow.</span></span> <span data-ttu-id="ea087-131">의 매개 변수를 사용 하 여 `Parameter` `Invoke-AsWorkflow` `Scope` `Get-ExecutionPolicy` **Process** 의 값으로 cmdlet의 매개 변수를 지정 합니다. 또한이 명령은 `PSConnectionRetryCount` 워크플로 일반 매개 변수를 사용 하 여 각 컴퓨터에서 5 번의 시도로 명령을 제한 하 고 `PSComputerName` 워크플로 일반 매개 변수를 사용 하 여 원격 노드 (대상 컴퓨터)의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-131">It uses the `Parameter` parameter of `Invoke-AsWorkflow` to specify the `Scope` parameter of the `Get-ExecutionPolicy` cmdlet with a value of **Process** .The command also uses the `PSConnectionRetryCount` workflow common parameter to limit the command to five attempts on each computer and the `PSComputerName` workflow common parameter to specify the names of the remote nodes (target computers).</span></span> <span data-ttu-id="ea087-132">매개 변수의 값은 `PSComputerName` `ServerName` 변수의 모든 개체에 대 한 속성을 가져오는 식입니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="ea087-132">The value of the `PSComputerName` parameter is an expression that gets the `ServerName` property of every object in the `$s` variable.</span></span>

<span data-ttu-id="ea087-133">이러한 명령은 수백 대 `Get-ExecutionPolicy` 의 컴퓨터에서 명령을 워크플로로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-133">These commands run a `Get-ExecutionPolicy` command as a workflow on hundreds of computers.</span></span>
<span data-ttu-id="ea087-134">이 명령은 `Scope` cmdlet의 매개 변수를 `Get-ExecutionPolicy` **Process** 값과 함께 사용 하 여 현재 세션의 실행 정책을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-134">The command uses the `Scope` parameter of the `Get-ExecutionPolicy` cmdlet with a value of **Process** to get the execution policy in the current session.</span></span>

### <span data-ttu-id="ea087-135">예제 3: 식을 워크플로로 실행</span><span class="sxs-lookup"><span data-stu-id="ea087-135">Example 3: Run an expression as a workflow</span></span>

```powershell
Invoke-AsWorkflow -Expression "ipconfig /all" -PSComputerName (Get-Content DomainControllers.txt) -AsJob -JobName IPConfig
```

```output
Id     Name          PSJobTypeName   State         HasMoreData   Location                Command
--     ----          -------------   -----         -----------   --------                -------
2      IpConfig      PSWorkflowJob   Completed     True          Server01, Server01...   Invoke-AsWorkflow
```

<span data-ttu-id="ea087-136">이 명령은 워크플로를 사용 하 여 `Invoke-AsWorkflow` DomainControllers.txt 파일에 나열 된 컴퓨터에서 워크플로 작업으로 Ipconfig 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-136">This command uses the `Invoke-AsWorkflow` workflow to run an Ipconfig command as a workflow job on the computers listed in the DomainControllers.txt file.</span></span>

<span data-ttu-id="ea087-137">이 명령은 매개 변수를 사용 하 여 `Expression` 실행할 식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-137">The command uses the `Expression` parameter to specify the expression to run.</span></span>
<span data-ttu-id="ea087-138">`PSComputerName`워크플로 일반 매개 변수를 사용 하 여 원격 노드 (대상 컴퓨터)의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-138">It uses the `PSComputerName` workflow common parameter to specify the names of the remote nodes (target computers).</span></span>

<span data-ttu-id="ea087-139">또한이 명령은 `AsJob` 및 `JobName` 워크플로 일반 매개 변수를 사용 하 여 각 컴퓨터에서 "Ipconfig" 작업 이름으로 워크플로를 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-139">The command also uses the `AsJob` and `JobName` workflow common parameters to run the workflow as a background job on each computer with the "Ipconfig" job name.</span></span>

<span data-ttu-id="ea087-140">`ContainerParentJob` `System.Management.Automation.ContainerParentJob` 이 명령은 각 컴퓨터에서 워크플로 작업을 포함 하는 개체 ()를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-140">The command returns a `ContainerParentJob` object (`System.Management.Automation.ContainerParentJob`) that contains the workflow jobs on each computer.</span></span>

## <span data-ttu-id="ea087-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ea087-141">PARAMETERS</span></span>

### <span data-ttu-id="ea087-142">-CommandName</span><span class="sxs-lookup"><span data-stu-id="ea087-142">-CommandName</span></span>

<span data-ttu-id="ea087-143">지정된 cmdlet 또는 고급 함수를 워크플로로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-143">Runs the specified cmdlet or advanced function as a workflow.</span></span>
<span data-ttu-id="ea087-144">Cmdlet 또는 함수 이름 (예:, 또는)을 입력 `Update-Help` `Set-ExecutionPolicy` `Set-NetFirewallRule` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-144">Enter the cmdlet or function name, such as `Update-Help`, `Set-ExecutionPolicy`, or `Set-NetFirewallRule`.</span></span>

```yaml
Type: System.String
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ea087-145">-식</span><span class="sxs-lookup"><span data-stu-id="ea087-145">-Expression</span></span>

<span data-ttu-id="ea087-146">이 cmdlet이 워크플로로 실행 되는 식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-146">Specifies the  expression that this cmdlet runs as a workflow.</span></span>
<span data-ttu-id="ea087-147">식을 문자열로 입력 합니다 (예:) `"ipconfig /all"` .</span><span class="sxs-lookup"><span data-stu-id="ea087-147">Enter the expression as a string, such as `"ipconfig /all"`.</span></span>
<span data-ttu-id="ea087-148">식에 공백이나 특수 문자가 포함된 경우 식을 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-148">If the expression includes spaces or special characters, enclose the expression in quotation marks.</span></span>

```yaml
Type: System.String
Parameter Sets: Expression
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ea087-149"> 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ea087-149">-Parameter</span></span>

<span data-ttu-id="ea087-150">매개 변수에 지정 된 명령의 매개 변수 및 매개 변수 값을 지정 합니다 `CommandName` .</span><span class="sxs-lookup"><span data-stu-id="ea087-150">Specifies the parameters and parameter values of the command that is specified in the `CommandName` parameter.</span></span>
<span data-ttu-id="ea087-151">각 키가 매개 변수 이름이 고 해당 값이와 같은 매개 변수 값인 해시 테이블을 입력 `@{ExecutionPolicy="AllSigned"}` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-151">Enter a hash table in which each key is a parameter name and its value is the parameter value, such as `@{ExecutionPolicy="AllSigned"}`.</span></span>

<span data-ttu-id="ea087-152">해시 테이블에 대 한 자세한 내용은 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ea087-152">For information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ea087-153">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ea087-153">-InputObject</span></span>

<span data-ttu-id="ea087-154">파이프라인 입력을 허용 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-154">Used to allows pipeline input.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ea087-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ea087-155">CommonParameters</span></span>

<span data-ttu-id="ea087-156">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ea087-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ea087-157">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea087-157">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

### <span data-ttu-id="ea087-158">WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="ea087-158">WorkflowCommonParameters</span></span>

<span data-ttu-id="ea087-159">또한이 cmdlet은 워크플로 관련 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-159">This cmdlet also supports workflow specific common parameters.</span></span>
<span data-ttu-id="ea087-160">자세한 내용은 [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ea087-160">For information, see [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md).</span></span>

## <span data-ttu-id="ea087-161">입력</span><span class="sxs-lookup"><span data-stu-id="ea087-161">INPUTS</span></span>

### <span data-ttu-id="ea087-162">System.Object</span><span class="sxs-lookup"><span data-stu-id="ea087-162">System.Object</span></span>

<span data-ttu-id="ea087-163">모든 개체를 매개 변수로 파이프 할 수 있습니다 `InputObject` .</span><span class="sxs-lookup"><span data-stu-id="ea087-163">You can pipe any object to the `InputObject` parameter.</span></span>

## <span data-ttu-id="ea087-164">출력</span><span class="sxs-lookup"><span data-stu-id="ea087-164">OUTPUTS</span></span>

### <span data-ttu-id="ea087-165">없음</span><span class="sxs-lookup"><span data-stu-id="ea087-165">None</span></span>

<span data-ttu-id="ea087-166">이 명령에서 어떠한 출력도 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-166">This command does not generate any output.</span></span>
<span data-ttu-id="ea087-167">그러나 출력을 생성할 수도 있는 워크플로를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ea087-167">However, it runs the workflow, which might generate output.</span></span>

## <span data-ttu-id="ea087-168">참고</span><span class="sxs-lookup"><span data-stu-id="ea087-168">NOTES</span></span>

## <span data-ttu-id="ea087-169">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ea087-169">RELATED LINKS</span></span>

[<span data-ttu-id="ea087-170">New-PSWorkflowExecutionOption</span><span class="sxs-lookup"><span data-stu-id="ea087-170">New-PSWorkflowExecutionOption</span></span>](../PSWorkflow/New-PSWorkflowExecutionOption.md)

[<span data-ttu-id="ea087-171">New-PSWorkflowSession</span><span class="sxs-lookup"><span data-stu-id="ea087-171">New-PSWorkflowSession</span></span>](../PSWorkflow/New-PSWorkflowSession.md)

[<span data-ttu-id="ea087-172">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="ea087-172">about_Workflows</span></span>](../PSWorkflow/About/about_Workflows.md)

[<span data-ttu-id="ea087-173">about_Workflow_Common_Parameters</span><span class="sxs-lookup"><span data-stu-id="ea087-173">about_Workflow_Common_Parameters</span></span>](../PSWorkflow/About/about_WorkflowCommonParameters.md)
