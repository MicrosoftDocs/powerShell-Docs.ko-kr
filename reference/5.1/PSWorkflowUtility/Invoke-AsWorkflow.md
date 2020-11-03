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
# Invoke-AsWorkflow

## 개요
명령 또는 식을 Windows PowerShell 워크플로로 실행합니다.

## SYNTAX

### Command (기본값)

```
Invoke-AsWorkflow [-CommandName <String>] [-Parameter <Hashtable>] [-InputObject <Object>] [<CommonParameters>]
```

### 식

```
Invoke-AsWorkflow [-Expression <String>] [-InputObject <Object>] [<CommonParameters>]
```

## 설명

`Invoke-AsWorkflow`워크플로는 워크플로에서 모든 명령 또는 식을 인라인 스크립트로 실행 합니다.
이러한 워크플로는 표준 워크플로 의미 체계를 사용하고 모든 워크플로 일반 매개 변수를 포함하며 중지, 다시 시작 및 복구 기능을 비롯한 모든 워크플로 이점을 포함합니다.

워크플로는 중요한 데이터를 수집하는 오래 실행되는 명령을 위해 설계되었지만 모든 명령을 실행하는 데 사용할 수 있습니다.
자세한 내용은 [about_Workflows](../PSWorkflow/About/about_Workflows.md)를 참조 하세요.

또한 이 명령에 워크플로 일반 매개 변수를 추가할 수 있습니다.
워크플로 일반 매개 변수에 대 한 자세한 내용은을 참조 하십시오 [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)

이 워크플로는 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예 1: 워크플로로 cmdlet 실행

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

이 명령은 수백 대 `Get-ExecutionPolicy` 의 컴퓨터에서 cmdlet을 워크플로로 실행 합니다.

이 명령은 **CommandName** 매개 변수를 사용하여 워크플로에서 실행되는 cmdlet을 지정합니다.
또한 이 명령은 **PSComputerName** 워크플로 일반 매개 변수를 사용하여 명령이 실행되는 컴퓨터를 지정합니다.
**PSComputerName** 매개 변수 값은 `Get-Content` Servers.txt 파일에서 컴퓨터 이름 목록을 가져오는 명령입니다.
값을 사용 하기 전에 Windows PowerShell에서 명령을 실행 하도록 지시 하기 위해 매개 변수 값은 괄호로 묶여 `Get-Command` 있습니다.

모든 원격 명령과 마찬가지로 이 명령이 로컬 컴퓨터에서 실행되는 경우(PSComputerName 매개 변수 값이 로컬 컴퓨터를 포함하는 경우) "관리자 권한으로 실행" 옵션을 사용하여 Windows PowerShell을 시작해야 합니다.

### 예제 2: 매개 변수를 사용 하 여 cmdlet 실행

```powershell
$s = Import-Csv .\Servers.csv -Header ServerName, ServerID
Invoke-AsWorkflow -CommandName Get-ExecutionPolicy -Parameter @{Scope="Process"} -PSComputerName {$s.ServerName} -PSConnectionRetryCount 5
```

첫 번째 명령은 cmdlet을 사용 하 여 `Import-Csv` Servers.csv 파일의 콘텐츠에서 개체를 만듭니다. 이 명령은 매개 변수를 사용 하 여 `Header` `ServerName` 대상 컴퓨터의 이름을 포함 하는 열에 대 한 속성을 만듭니다 ("원격 노드" 라고도 함). 이 명령은 결과를 `$s` 변수에 저장 합니다.

두 번째 명령은 워크플로를 사용 하 여 `Invoke-AsWorkflow` `Get-ExecutionPolicy` Servers.csv 파일의 컴퓨터에서 명령을 실행 합니다. 이 명령은의 **CommandName** 매개 변수를 사용 하 여 `Invoke-AsWorkflow`  워크플로에서 실행할 명령을 지정 합니다. 의 매개 변수를 사용 하 여 `Parameter` `Invoke-AsWorkflow` `Scope` `Get-ExecutionPolicy` **Process** 의 값으로 cmdlet의 매개 변수를 지정 합니다. 또한이 명령은 `PSConnectionRetryCount` 워크플로 일반 매개 변수를 사용 하 여 각 컴퓨터에서 5 번의 시도로 명령을 제한 하 고 `PSComputerName` 워크플로 일반 매개 변수를 사용 하 여 원격 노드 (대상 컴퓨터)의 이름을 지정 합니다. 매개 변수의 값은 `PSComputerName` `ServerName` 변수의 모든 개체에 대 한 속성을 가져오는 식입니다 `$s` .

이러한 명령은 수백 대 `Get-ExecutionPolicy` 의 컴퓨터에서 명령을 워크플로로 실행 합니다.
이 명령은 `Scope` cmdlet의 매개 변수를 `Get-ExecutionPolicy` **Process** 값과 함께 사용 하 여 현재 세션의 실행 정책을 가져옵니다.

### 예제 3: 식을 워크플로로 실행

```powershell
Invoke-AsWorkflow -Expression "ipconfig /all" -PSComputerName (Get-Content DomainControllers.txt) -AsJob -JobName IPConfig
```

```output
Id     Name          PSJobTypeName   State         HasMoreData   Location                Command
--     ----          -------------   -----         -----------   --------                -------
2      IpConfig      PSWorkflowJob   Completed     True          Server01, Server01...   Invoke-AsWorkflow
```

이 명령은 워크플로를 사용 하 여 `Invoke-AsWorkflow` DomainControllers.txt 파일에 나열 된 컴퓨터에서 워크플로 작업으로 Ipconfig 명령을 실행 합니다.

이 명령은 매개 변수를 사용 하 여 `Expression` 실행할 식을 지정 합니다.
`PSComputerName`워크플로 일반 매개 변수를 사용 하 여 원격 노드 (대상 컴퓨터)의 이름을 지정 합니다.

또한이 명령은 `AsJob` 및 `JobName` 워크플로 일반 매개 변수를 사용 하 여 각 컴퓨터에서 "Ipconfig" 작업 이름으로 워크플로를 백그라운드 작업으로 실행 합니다.

`ContainerParentJob` `System.Management.Automation.ContainerParentJob` 이 명령은 각 컴퓨터에서 워크플로 작업을 포함 하는 개체 ()를 반환 합니다.

## PARAMETERS

### -CommandName

지정된 cmdlet 또는 고급 함수를 워크플로로 실행합니다.
Cmdlet 또는 함수 이름 (예:, 또는)을 입력 `Update-Help` `Set-ExecutionPolicy` `Set-NetFirewallRule` 합니다.

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

### -식

이 cmdlet이 워크플로로 실행 되는 식을 지정 합니다.
식을 문자열로 입력 합니다 (예:) `"ipconfig /all"` .
식에 공백이나 특수 문자가 포함된 경우 식을 따옴표로 묶습니다.

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

###  매개 변수

매개 변수에 지정 된 명령의 매개 변수 및 매개 변수 값을 지정 합니다 `CommandName` .
각 키가 매개 변수 이름이 고 해당 값이와 같은 매개 변수 값인 해시 테이블을 입력 `@{ExecutionPolicy="AllSigned"}` 합니다.

해시 테이블에 대 한 자세한 내용은 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)를 참조 하세요.

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

### -InputObject

파이프라인 입력을 허용 하는 데 사용 됩니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

### WorkflowCommonParameters

또한이 cmdlet은 워크플로 관련 일반 매개 변수를 지원 합니다.
자세한 내용은 [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)를 참조 하세요.

## 입력

### System.Object

모든 개체를 매개 변수로 파이프 할 수 있습니다 `InputObject` .

## 출력

### 없음

이 명령에서 어떠한 출력도 생성되지 않습니다.
그러나 출력을 생성할 수도 있는 워크플로를 실행합니다.

## 참고

## 관련 링크

[New-PSWorkflowExecutionOption](../PSWorkflow/New-PSWorkflowExecutionOption.md)

[New-PSWorkflowSession](../PSWorkflow/New-PSWorkflowSession.md)

[about_Workflows](../PSWorkflow/About/about_Workflows.md)

[about_Workflow_Common_Parameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)
