---
description: PowerShell 워크플로 기능에 대 한 간략 한 소개를 제공 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_workflows?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Workflows
ms.openlocfilehash: fbd8ee62b1e9c6969d489c5024c33f5cca883dc6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221849"
---
# <a name="about-workflows"></a>워크플로 정보

## <a name="short-description"></a>간단한 설명

PowerShell 워크플로 기능에 대 한 간략 한 소개를 제공 합니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell 워크플로는 [Windows Workflow Foundation](/dotnet/framework/windows-workflow-foundation) 의 이점을 powershell로 제공 하 고 워크플로를 작성 하 고 실행할 수 있도록 합니다.

Powershell 워크플로는 powershell 3.0에서 도입 되었으며 모듈은 PowerShell 5.1까지 사용할 수 있습니다. PowerShell 워크플로에 대 한 자세한 내용은 [워크플로 가이드](/previous-versions/powershell/scripting/components/workflows-guide) 및 [Windows PowerShell 워크플로 작성](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)을 참조 하세요.

## <a name="about-workflows"></a>워크플로 정보

워크플로는 일련의 관련 작업으로 구성 된 명령입니다. 일반적으로 다른 유형의 환경에서 많은 수의 데이터를 수집 하 여 수백 대의 컴퓨터를 변경 하는 데 오랜 시간 동안 실행 됩니다.

워크플로는 XAML, Windows Workflow Foundation에 사용 되는 언어 또는 PowerShell 언어로 작성할 수 있습니다. 워크플로는 일반적으로 모듈에 패키지 되며 도움말 항목을 포함 합니다. 자세한 내용은 [XAML 개요 (WPF)](/dotnet/framework/wpf/advanced/xaml-overview-wpf)를 참조 하세요.

워크플로는 다시 부팅 하 고 일반적인 오류 로부터 자동으로 복구할 수 있기 때문에 IT 환경에서 중요 합니다. 워크플로 처리를 중단 하지 않고 워크플로를 실행 하는 세션 및 컴퓨터에서 연결을 끊고 다시 연결 하 고, 데이터 손실 없이 워크플로를 일시 중단 하 고 다시 시작할 수 있습니다. 워크플로의 각 작업을 기록 하 고 참조를 감사할 수 있습니다.
워크플로는 작업으로 실행 될 수 있으며 PowerShell의 예약 된 작업 기능을 사용 하 여 예약할 수 있습니다.

워크플로의 상태와 데이터는 워크플로의 시작과 끝 및 지정 된 지점에 저장 되거나 유지 됩니다. 워크플로 지 속성 지점은 데이터베이스 스냅숏 또는 프로그램 검사점과 같은 작업을 수행 하 여 중단 및 오류의 영향 으로부터 워크플로를 보호 합니다. 워크플로에서 오류를 복구할 수 없는 경우 처음부터 광범위 한 워크플로를 다시 실행 하는 대신 지속형 데이터를 사용 하 고 마지막 지 속성 지점에서 재개할 수 있습니다.

## <a name="workflow-requirements-and-configuration"></a>워크플로 요구 사항 및 구성

PowerShell 워크플로 구성은 다음 요소로 구성 됩니다.

- 워크플로를 실행 하는 클라이언트 컴퓨터
- 클라이언트 컴퓨터 또는 원격 컴퓨터의 워크플로 세션 **PSSession**
- 워크플로 활동의 영향을 받는 대상 컴퓨터인 관리 되는 노드입니다.

워크플로 세션은 필요 하지 않지만 권장 됩니다. **Pssessions** 는 PowerShell의 강력한 복구 및 연결 되지 않은 세션 기능을 활용 하 여 연결 되지 않은 워크플로 세션을 복구할 수 있습니다. 자세한 내용은 [about_Remote_Disconnected_Sessions](../../Microsoft.PowerShell.Core/About/about_Remote_Disconnected_Sessions.md) 를 참조 하세요.

워크플로 세션이 실행 되는 컴퓨터와 클라이언트 컴퓨터는 관리 되는 노드가 될 수 있으므로 모든 역할을 충족 하는 단일 컴퓨터에서 워크플로를 실행할 수 있습니다.

클라이언트 컴퓨터와 워크플로 세션이 실행 되는 컴퓨터에서 PowerShell 3.0을 실행 해야 합니다. Windows Server 운영 체제의 Server Core 설치 옵션을 포함 하 여 적합 한 모든 시스템이 지원 됩니다.

Cmdlet을 포함 하는 워크플로를 실행 하려면 관리 되는 노드에 Windows PowerShell 2.0 이상이 있어야 합니다. 워크플로에 cmdlet이 포함 되어 있지 않으면 관리 되는 노드에 PowerShell이 필요 하지 않습니다. PowerShell이 없는 컴퓨터에 WMI(Windows Management Instrumentation) (WMI) 및 CIM(Common Information Model) (CIM) 명령을 포함 하는 워크플로를 실행할 수 있습니다.

## <a name="how-to-get-workflows"></a>워크플로를 가져오는 방법

워크플로는 일반적으로 모듈에 패키지 됩니다. 워크플로를 포함 하는 모듈을 가져오려면 모듈의 명령을 사용 하거나 cmdlet을 사용 `Import-Module` 합니다.
모듈의 명령을 처음 사용할 때 자동으로 모듈을 가져옵니다.

컴퓨터에 설치 된 모듈에서 워크플로를 찾으려면 `Get-Command` cmdlet의 **CommandType** 매개 변수를 사용 합니다.

```powershell
Get-Command -CommandType Workflow
```

## <a name="how-to-run-workflows"></a>워크플로를 실행 하는 방법

워크플로를 실행 하려면 다음 절차를 따르십시오.

1. 관리 되는 노드가 로컬 컴퓨터인 경우에는이 단계가 필요 하지 않습니다.
   그렇지 않으면 클라이언트 컴퓨터에서 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.

   ```powershell
   Start-Process PowerShell -Verb RunAs
   ```

1. 워크플로 세션을 실행 하는 컴퓨터와 cmdlet을 포함 하는 워크플로의 영향을 받는 관리 되는 노드에서 PowerShell 원격을 사용 하도록 설정 합니다.

   참여 하는 각 컴퓨터에서이 단계를 한 번만 수행 하면 됩니다.

   Cmdlet을 포함 하는 워크플로를 실행 하는 경우에만이 단계가 필요 합니다. 워크플로 세션이 클라이언트 컴퓨터에서 실행 되는 경우 또는 PowerShell 3.0를 실행 하는 모든 관리 되는 노드에서 클라이언트 컴퓨터에서 원격 기능을 사용 하도록 설정할 필요는 없습니다.

   원격 기능을 사용 하도록 설정 하려면 cmdlet을 사용 `Enable-PSRemoting` 합니다.

   ```powershell
   Enable-PSRemoting -Force
   ```

   **스크립트 실행** 그룹 정책 설정을 사용 하 여 원격 기능을 사용 하도록 설정할 수 있습니다. 자세한 내용은 [about_Group_Policy_Settings](../../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md) 및 [about_Execution_Policies](../../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)를 참조 하세요.

1. `New-PSWorkflowSession`또는 `New-PSSession` cmdlet을 사용 하 여 워크플로 세션을 만듭니다.

   `New-PSWorkflowSession`Cmdlet은 대상 컴퓨터에서 기본 제공 되는 **Microsoft PowerShell 워크플로** 세션 구성을 사용 하는 세션을 시작 합니다. 이 세션 구성에는 스크립트, 형식 및 서식 파일, 워크플로에 대해 설계 된 옵션이 포함 됩니다.

   또는 cmdlet을 사용 `New-PSSession` 합니다. **ConfigurationName** 매개 변수를 사용 하 여 **Microsoft. PowerShell 워크플로** 세션 구성을 지정 합니다. 이 명령은 cmdlet을 사용 하는 것과 같습니다 `New-PSWorkflowSession` .

   다른 방법은 cmdlet을 사용 하는 것입니다 `New-PSSession` . **ConfigurationName** 매개 변수를 사용 하 여 **Microsoft. PowerShell 워크플로** 세션 구성을 지정 합니다.

   로컬 컴퓨터에서 다음을 수행 합니다.

   ```powershell
   $ws = New-PSWorkflowSession
   ```

   원격 컴퓨터에서 다음을 수행 합니다.

   ```powershell
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

   워크플로 세션 컴퓨터의 관리자 인 경우 cmdlet을 사용 `New-PSWorkflowExecutionOption` 하 여 워크플로 세션 구성에 대 한 사용자 지정 옵션 설정을 만들 수 있습니다. Cmdlet을 사용 `Set-PSSessionConfiguration` 하 여 세션 구성을 변경할 수 있습니다.

   ```powershell
   $sto = New-PSWorkflowExecutionOption -MaxConnectedSessions 150
   Invoke-Command -ComputerName Server01 `
   {Set-PSSessionConfiguration Microsoft.PowerShell.Workflow `
   -SessionTypeOption $Using:sto}
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

1. 워크플로 세션에서 워크플로를 실행 합니다. 관리 되는 노드 (대상 컴퓨터)의 이름을 지정 하려면 **PSComputerName** 워크플로 일반 매개 변수를 사용 합니다.

   다음 예제에서는 **테스트** 워크플로 라는 워크플로를 실행 합니다.

   여기서 관리 되는 노드는 워크플로 세션을 호스트 하는 컴퓨터입니다.

   ```powershell
   Invoke-Command -Session $ws {Test-Workflow}
   ```

   여기에서 관리 되는 노드는 원격 컴퓨터입니다.

   ```powershell
   Invoke-Command -Session $ws{
   Test-Workflow -PSComputerName Server01, Server02 }
   ```

   다음 예제에서는 수백 대의 컴퓨터에서 **테스트 워크플로** 를 실행 합니다. `Get-Content`Cmdlet은 텍스트 파일에서 컴퓨터 이름을 가져와서 `$Servers` 로컬 컴퓨터의 변수에 저장 합니다.

   `Invoke-Command` 범위 한정자를 사용 하 여 `$Using` `$Servers` 로컬 세션에서 변수를 정의 합니다. 범위 한정자에 대 한 자세한 내용은 `$Using` [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)를 참조 하세요.

   ```powershell
   $Servers = Get-Content Servers.txt
   Invoke-Command -Session $ws {Test-Workflow -PSComputerName $Using:Servers }
   ```

## <a name="using-workflow-common-parameters"></a>워크플로 일반 매개 변수 사용

워크플로 일반 매개 변수는 PowerShell이 모든 워크플로에 자동으로 추가 하는 매개 변수 집합입니다. 워크플로에서 **Cmdletbinding** 특성을 사용 하지 않는 경우에도 PowerShell은 모든 워크플로에 cmdlet 일반 매개 변수를 추가 합니다.

예를 들어 다음 워크플로는 매개 변수를 정의 하지 않습니다. 그러나 워크플로를 실행 하는 경우 **CommonParameters** 와 **WorkflowCommonParameters** 가 모두 포함 됩니다.

```powershell
workflow Test-Workflow {Get-Process}
Get-Command Test-Workflow -Syntax
```

```powershell
Test-Workflow [<WorkflowCommonParameters>] [<CommonParameters>]
```

워크플로 일반 매개 변수에는 워크플로를 실행 하는 데 필수적인 몇 가지 매개 변수가 포함 되어 있습니다. 예를 들어 **PSComputerName** 일반 매개 변수는 워크플로가 영향을 주는 관리 되는 노드를 지정 합니다.

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02
}
```

**Pspersist** 워크플로 일반 매개 변수는 워크플로 데이터가 유지 되는 시기를 결정 합니다. 이를 통해 지 속성 포인트를 정의 하지 않는 워크플로에 활동 간 지 속성 지점을 추가할 수 있습니다.

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPersist:$True
}
```

다른 워크플로 일반 매개 변수를 사용 하면 관리 되는 노드에 대 한 원격 연결의 특성을 지정할 수 있습니다. 이름 및 기능은 원격 cmdlet의 매개 변수 (포함)와 유사 `Invoke-Command` 합니다.

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPort 443
}
```

관리 되는 노드에 대 한 연결을 정의 하는 **PS 접두사** 워크플로 일반 매개 변수에서 워크플로 세션에 대 한 연결을 정의 하는 원격 매개 변수를 구분 합니다.

```powershell
$ws = New-PSSession -ComputerName Server01 -ConfigurationName Microsoft.PowerShell.Workflow

Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSConfigurationName Microsoft.PowerShell.Workflow
}
```

일부 워크플로 일반 매개 변수는 여러 원격 노드에 대해 서로 다른 워크플로 일반 매개 변수 값을 지정할 수 있는 **PSParameterCollection** 매개 변수와 같은 워크플로에 고유 합니다. 워크플로 일반 매개 변수에 대 한 목록 및 설명은 [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[Invoke-AsWorkflow](xref:PSWorkflowUtility.Invoke-AsWorkflow)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Psworkflow](xref:PSWorkflow) cmdlet

[워크플로 가이드](/previous-versions/powershell/scripting/components/workflows-guide)

[Windows PowerShell 워크플로 작성](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
