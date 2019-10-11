---
title: 필수 개발 지침 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: e68e43a91f9139e8d3dc636b5740121515aab2e6
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986681"
---
# <a name="required-development-guidelines"></a>필수 개발 지침

Cmdlet을 작성할 때는 다음 지침을 따라야 합니다. Cmdlet을 디자인 하기 위한 지침과 cmdlet 코드를 작성 하기 위한 지침으로 구분 됩니다. 이러한 지침을 따르지 않으면 cmdlet이 실패 하 고 사용자가 cmdlet을 사용 하는 경우 사용자에 게 좋지 않은 경험이 있을 수 있습니다.

## <a name="in-this-topic"></a>이 항목의 내용

### <a name="design-guidelines"></a>디자인 지침

- [승인 된 동사로만 사용 (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Cmdlet 이름: 사용할 수 없는 문자 (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [사용할 수 없는 매개 변수 이름 (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [지원 확인 요청 (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [대화형 세션의 Force 매개 변수 지원 (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [문서 출력 개체 (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>코드 지침

- [Cmdlet 또는 PSCmdlet 클래스에서 파생 합니다 (RC01).](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Cmdlet 특성 지정 (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [입력 처리 메서드 재정의 (RC03)](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [OutputType 특성 지정 (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [출력 개체에 대 한 핸들을 유지 하지 않습니다 (RC05).](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [강력 하 게 오류 처리 (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Windows PowerShell 모듈을 사용 하 여 Cmdlet 배포 (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>디자인 지침

Cmdlet을 사용할 때와 다른 cmdlet을 사용할 때 일관 된 사용자 환경을 보장 하기 위해 cmdlet을 디자인할 때는 다음 지침을 따라야 합니다. 상황에 적용 되는 디자인 지침을 찾았으면 유사한 지침에 대 한 코드 지침을 확인 해야 합니다.

### <a name="use-only-approved-verbs-rd01"></a>승인 된 동사로만 사용 (RD01)

Cmdlet 특성에 지정 된 동사는 Windows PowerShell에서 제공 하는 인식 된 동사 집합에서 가져와야 합니다. 금지 된 동의어 중 하나가 아니어야 합니다. 다음 열거형으로 정의 된 상수 문자열을 사용 하 여 cmdlet 동사를 지정 합니다.

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

승인 된 동사 이름에 대 한 자세한 내용은 [Cmdlet 동사](./approved-verbs-for-windows-powershell-commands.md)를 참조 하세요.

사용자에 게는 검색 가능 하 고 필요한 cmdlet 이름 집합이 필요 합니다. 사용자가 cmdlet이 수행 하는 작업을 신속 하 게 평가 하 고 시스템의 기능을 쉽게 검색할 수 있도록 적절 한 동사를 사용 합니다. 예를 들어 다음 명령줄 명령은 시스템에서 이름이 "start" `get-command start-*`로 시작 하는 모든 명령 목록을 가져옵니다. Cmdlet에서 명사를 사용 하 여 cmdlet을 다른 cmdlet과 구분 합니다. 명사는 작업이 수행 되는 리소스를 나타냅니다. 작업 자체는 동사로 표시 됩니다.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Cmdlet 이름: 사용할 수 없는 문자 (RD02)

Cmdlet의 이름을 입력할 때 다음 특수 문자를 사용 하지 마십시오.

|문자|이름|
|---------------|----------|
|#|숫자 기호|
|,|쉼표로|
|()|괄호|
|{}|묶습니다|
|[]|각괄호|
|&|안에서|
|-|하이픈 **메모:**  하이픈은 명사에서 동사를 구분 하는 데 사용할 수 있지만 명사 또는 동사 내에서 사용할 수 없습니다.|
|/|슬래시 표시|
|\\| 백슬래시|
|$|달러 기호|
|^|caret|
|;|;|
|:|탑재|
|"|큰따옴표|
|'|작은따옴표|
|<>|꺾쇠 괄호|
|&#124;|세로 막대|
|?|물음표|
|@|at 기호|
|`|뒤로 눈금 (억음 악센트)|
|*|찾으려면|
|%|백분율 기호|
|+|더하기 기호|
|=|등호 기호|
|~|물결표|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>사용할 수 없는 매개 변수 이름 (RD03)

Windows PowerShell은 모든 cmdlet에 매개 변수를 설정 하 고 특정 상황에서 추가 되는 추가 매개 변수를 제공 합니다. 사용자 고유의 cmdlet을 디자인 하는 경우 다음 이름을 사용할 수 없습니다. Confirm, Debug, ErrorAction, Erroraction, OutBuffer, OutVariable, WarningAction, WarningVariable, WhatIf, UseTransaction 및 Verbose입니다. 이러한 매개 변수에 대 한 자세한 내용은 [일반 매개 변수 이름](./common-parameter-names.md)을 참조 하세요.

### <a name="support-confirmation-requests-rd04"></a>지원 확인 요청 (RD04)

시스템을 수정 하는 작업을 수행 하는 cmdlet의 경우에는 확인을 요청 하기 위해 [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하 고, 특수 한 경우에는를 [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) . n a m. System.object를 호출한 후에만 [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 해야 합니다 .이 메서드 [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 호출한 후에만 호출 해야 합니다.

이러한 호출을 수행 하려면 cmdlet에서 cmdlet 특성의 키워드를 `SupportsShouldProcess` 설정 하 여 확인 요청을 지원 하도록 지정 해야 합니다. 이 특성을 설정 하는 방법에 대 한 자세한 내용은 [Cmdlet 특성 선언](./cmdlet-attribute-declaration.md)을 참조 하세요.

> [!NOTE]
> Cmdlet 클래스의 Cmdlet 특성에서 cmdlet이 [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 대 한 호출을 지원 하 고, cmdlet이에 대 한 호출을 지원 하지 [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 예기치 않게 수정할 수 있는 방법입니다.

시스템 수정에는 [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 사용 하 여 시스템을 수정 합니다. 사용자 기본 설정 및 `WhatIf` 매개 변수는 [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 제어 합니다. 이와 대조적으로, 잠재적으로 위험할 [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 에 대 한 추가 검사를 수행 합니다. 이 메서드는 사용자 기본 설정 또는 `WhatIf` 매개 변수를 통해 제어 되지 않습니다. Cmdlet이 [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 하는 경우이 메서드는 이러한 두 메서드에 대 한 호출을 무시 하 고 작업 `Force` 을 진행 하는 매개 변수를 포함 해야 합니다. 이는 cmdlet을 비 대화형 스크립트 및 호스트에서 사용할 수 있기 때문에 중요 합니다.

Cmdlet이 이러한 호출을 지 원하는 경우 사용자는 작업을 실제로 수행할지 여부를 결정할 수 있습니다. 예를 들어, [Stop Process](/powershell/module/microsoft.powershell.management/stop-process) cmdlet은 시스템, Winlogon 및 spoolsv.exe 프로세스를 포함 하 여 중요 한 프로세스 집합을 중지 하기 전에 [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 합니다.

이러한 메서드를 지 원하는 방법에 대 한 자세한 내용은 [확인 요청](./requesting-confirmation-from-cmdlets.md)을 참조 하세요.

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>대화형 세션의 Force 매개 변수 지원 (RD05)

Cmdlet을 대화형으로 사용 하는 경우 항상 Force 매개 변수를 제공 하 여 프롬프트 또는 입력 줄 읽기와 같은 대화형 작업을 재정의 합니다. 이는 cmdlet을 비 대화형 스크립트 및 호스트에서 사용할 수 있기 때문에 중요 합니다. 대화형 호스트에서 다음 메서드를 구현할 수 있습니다.

- [System.Management.Automation.Host.PSHostUserInterface.Prompt*.](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection.PromptForChoice.](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForCredential*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLine*.](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLineAsSecureString*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>문서 출력 개체 (RD06)

Windows PowerShell은 파이프라인에 기록 된 개체를 사용 합니다. 사용자가 각 cmdlet에서 반환 되는 개체를 활용 하려면 반환 되는 개체를 문서화 하 고 반환 된 개체의 멤버가 사용 되는 내용을 문서화 해야 합니다.

## <a name="code-guidelines"></a>코드 지침

Cmdlet 코드를 작성할 때는 다음 지침을 따라야 합니다. 사용자의 상황에 적용 되는 코드 지침을 찾았으면 유사한 지침에 대 한 디자인 지침을 확인 해야 합니다.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Cmdlet 또는 PSCmdlet 클래스에서 파생 합니다 (RC01).

Cmdlet은 [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 기본 클래스 또는 클래스에서 파생 되어야 [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.Cmdlet) 경우). [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) 클래스에서 파생 되는 Cmdlet은 Windows PowerShell 런타임에 종속 되지 않습니다. 모든 Microsoft .NET Framework 언어에서 직접 호출할 수 있습니다. [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 클래스에서 파생 되는 Cmdlet은 Windows PowerShell 런타임에 따라 다릅니다. 따라서 runspace 내에서 실행 됩니다.

구현 하는 모든 cmdlet 클래스는 public 클래스 여야 합니다. 이러한 cmdlet 클래스에 대 한 자세한 내용은 [Cmdlet 개요](./cmdlet-overview.md)를 참조 하세요.

### <a name="specify-the-cmdlet-attribute-rc02"></a>Cmdlet 특성 지정 (RC02)

Windows PowerShell에서 cmdlet을 인식 하려면 해당 .NET Framework 클래스를 Cmdlet 특성으로 데코레이팅 해야 합니다. 이 특성은 cmdlet의 다음 기능을 지정 합니다.

- Cmdlet을 식별 하는 동사 및 명사 쌍입니다.

- 여러 매개 변수 집합을 지정할 때 사용 되는 기본 매개 변수 집합입니다. 기본 매개 변수 집합은 Windows PowerShell에 사용할 매개 변수 집합을 결정 하기에 충분 한 정보가 없을 때 사용 됩니다.

- Cmdlet에서 [System.Management.Automation.Cmdlet.ShouldProcesst](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 에 대 한 호출을 지원 하는지 여부를 나타냅니다. 이 메서드는 cmdlet이 시스템을 변경 하기 전에 사용자에 게 확인 메시지를 표시 합니다. 확인 요청을 수행 하는 방법에 대 한 자세한 내용은 [확인 요청](./requesting-confirmation-from-cmdlets.md)을 참조 하세요.

- 확인 메시지와 연결 된 동작의 영향 수준 또는 심각도를 지정 합니다. 대부분의 경우 기본값 Medium을 사용 해야 합니다. 영향 수준이 사용자에 게 표시 되는 확인 요청에 미치는 영향에 대 한 자세한 내용은 [확인 요청](./requesting-confirmation-from-cmdlets.md)을 참조 하십시오.

Cmdlet 특성을 선언 하는 방법에 대 한 자세한 내용은 [Cmdletattribute 선언](./cmdlet-attribute-declaration.md)을 참조 하세요.

### <a name="override-an-input-processing-method-rc03"></a>입력 처리 메서드 재정의 (RC03)

Cmdlet이 Windows PowerShell 환경에 참여 하려면 다음 *입력 처리 방법*중 하나 이상을 재정의 해야 합니다.

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 는 한 번만 호출 되며 전처리 기능을 제공 하는 데 사용 됩니다.

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 이 메서드는 여러 번 호출 되며 레코드를 기록 하는 기능을 제공 하는 데 사용 됩니다.

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 는 한 번만 호출 되며 사후 처리 기능을 제공 하는 데 사용 됩니다.

### <a name="specify-the-outputtype-attribute-rc04"></a>OutputType 특성 지정 (RC04)

OutputType 특성 (Windows PowerShell 2.0에 도입 됨)은 cmdlet이 파이프라인으로 반환 하는 .NET Framework 유형을 지정 합니다. Cmdlet의 출력 형식을 지정 하 여 cmdlet에서 반환 되는 개체를 다른 cmdlet에서 더 검색 가능 하 게 합니다. 이 특성으로 cmdlet 클래스를 데코레이팅하는 방법에 대 한 자세한 내용은 [OutputType 특성 선언](./outputtype-attribute-declaration.md)을 참조 하세요.

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>출력 개체에 대 한 핸들을 유지 하지 않습니다 (RC05).

Cmdlet은 [System.Management.Automation.Cmdlet.WriteObject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드에 전달 되는 개체에 대 한 핸들을 유지 하면 안 됩니다. 이러한 개체는 파이프라인의 다음 cmdlet에 전달 되거나 스크립트에서 사용 됩니다. 개체에 대 한 핸들을 유지 하는 경우 두 엔터티가 각 개체를 소유 하므로 오류가 발생 합니다.

### <a name="handle-errors-robustly-rc06"></a>강력 하 게 오류 처리 (RC06)

관리 환경에서는 기본적으로 관리 중인 시스템을 검색 하 고 중요 한 변경을 수행 합니다. 따라서 cmdlet에서 오류를 올바르게 처리 하는 것이 중요 합니다. 오류 레코드에 대 한 자세한 내용은 [Windows PowerShell 오류 보고](./error-reporting-concepts.md)를 참조 하세요.

- 오류가 발생 하 여 cmdlet이 더 이상 레코드를 계속 처리할 수 없으면 종료 오류가 발생 합니다. 이 cmdlet은 [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.ErrorRecord) 개체를 참조 하는 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드를 호출 해야 합니다. Cmdlet에서 예외를 catch 하지 않으면 Windows PowerShell 런타임 자체에서 더 작은 정보를 포함 하는 종료 오류를 throw 합니다.

- 파이프라인에서 발생 하는 다음 레코드 (예: 다른 프로세스에 의해 생성 된 레코드)에서 작업을 중지 하지 않는 종료 되지 않는 오류의 경우 cmdlet은 [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 해야 합니다. [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)](/dotnet/api/System.Management.Automation.ErrorRecord) 개체를 참조 합니다. 종료 되지 않는 오류의 예는 특정 프로세스를 중지 하는 데 실패 하는 경우 발생 하는 오류입니다. [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 하면 사용자가 요청 된 작업을 일관 되 게 수행 하 고 실패 한 특정 작업에 대 한 정보를 유지할 수 있습니다. Cmdlet은 각 레코드를 가능한 한 독립적으로 처리 해야 합니다.

- [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 및 [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드에서 참조하는 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체에는 다음이 필요합니다 핵심에 예외가 있습니다. 사용할 예외를 결정할 때 .NET Framework 디자인 지침을 따릅니다. 오류가 기존 예외와 의미상 동일한 경우 해당 예외를 사용 하거나 해당 예외에서 파생 합니다. 그렇지 않으면 [system.object](/dotnet/api/System.Exception) 형식에서 직접 새 예외 또는 예외 계층을 파생 시킵니다.

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체에는 사용자에 대 한 오류를 그룹화 하는 오류 범주도 필요 합니다. 사용자는 `$ErrorView` shell 변수 값을 categoryview로 설정 하 여 범주를 기반으로 오류를 볼 수 있습니다. 가능한 범주는 [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) 열거형에 의해 정의 됩니다.

- Cmdlet이 새 스레드를 만드는 경우 해당 스레드에서 실행 중인 코드가 처리 되지 않은 예외를 throw 하는 경우 Windows PowerShell에서 오류를 catch 하지 않고 프로세스를 종료 합니다.

- 개체의 소멸자에 처리 되지 않은 예외가 발생 하는 코드가 있는 경우 Windows PowerShell에서 오류를 catch 하지 않고 프로세스를 종료 합니다. 이는 개체가 처리 되지 않은 예외를 발생 시키는 Dispose 메서드를 호출 하는 경우에도 발생 합니다.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Windows PowerShell 모듈을 사용 하 여 Cmdlet 배포 (RC07)

Cmdlet을 패키지 하 고 배포 하는 Windows PowerShell 모듈을 만듭니다. 모듈에 대 한 지원은 Windows PowerShell 2.0에서 도입 되었습니다. Cmdlet 클래스를 포함 하는 어셈블리를 이진 모듈 파일 (cmdlet 테스트 시 매우 유용)로 직접 사용 하거나 cmdlet 어셈블리를 참조 하는 모듈 매니페스트를 만들 수 있습니다. 모듈을 사용할 때 기존 스냅인 어셈블리를 추가할 수도 있습니다. 모듈에 대 한 자세한 내용은 [Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)을 참조 하세요.

## <a name="see-also"></a>관련 항목

[권장 되는 개발 지침](./strongly-encouraged-development-guidelines.md)

[자문 개발 지침](./advisory-development-guidelines.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
