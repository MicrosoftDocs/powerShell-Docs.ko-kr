---
title: 필요한 개발 지침 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: a4b228be91bba27670b26fe21e765ae942afe968
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860719"
---
# <a name="required-development-guidelines"></a>필수 개발 지침

Cmdlet을 작성 하는 경우 다음 지침을 따라야 합니다. Cmdlet 및 cmdlet 코드 작성에 대 한 지침을 디자인 하기 위한 지침으로 구분 됩니다. 이러한 지침을 따르지 않으면 cmdlet 수 실패 하 고 cmdlet을 사용할 때 사용자에 게 열악 한 환경이 있을 합니다.

## <a name="in-this-topic"></a>이 항목의 내용

### <a name="design-guidelines"></a>디자인 지침

- [승인 된 동사 (RD01) 사용](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Cmdlet 이름: 문자를 사용할 수 없습니다 (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [사용할 수 없는 매개 변수 이름 (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [확인 요청 (RD04)를 지원 합니다.](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Force 매개 변수 (RD05) 대화형 세션에 대 한 지원](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [문서 출력 개체 (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>코드 지침

- [Cmdlet 또는 PSCmdlet 클래스 (RC01)에서 파생](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Cmdlet 특성 (RC02)를 지정 합니다.](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [입력 처리 메서드 (RC03)를 재정의 합니다.](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [OutputType 특성 (RC04)를 지정 합니다.](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [출력 개체 (RC05)에 대 한 핸들을 보유 하지는 않습니다](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [오류를 안정적으로 처리 (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Cmdlet (RC07)를 배포 하는 Windows PowerShell 모듈을 사용 합니다.](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>디자인 지침

Cmdlet 및 기타 cmdlet을 사용 하 여 간에 일관 된 사용자 환경을 보장 하려면 cmdlet을 디자인할 때 다음 지침을 따라야 합니다. 상황에 적용 되는 디자인 지침을 찾으면 유사한 지침에 대 한 코드 지침 확인 해야 합니다.

### <a name="use-only-approved-verbs-rd01"></a>승인 된 동사 (RD01) 사용

Cmdlet 특성에 지정 된 동사는 인식할 수 있는 Windows PowerShell에서 제공 하는 동사 집합에서 가져와야 합니다. 하지 금지 동의어 중 하나 여야 합니다. Cmdlet 동사를 지정 하려면 다음 열거형으로 정의 된 상수 문자열을 사용 합니다.

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

승인 된 동사 이름에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사](./approved-verbs-for-windows-powershell-commands.md)합니다.

사용자가 검색 가능 하 고 필요한 cmdlet 이름 집합이 필요합니다. 사용자가 쉽게 검색 하는 시스템의 기능 및 cmdlet이 수행 하는 빠른 평가 내릴 수 있도록 적절 한 동사를 사용 합니다. 예를 들어, 이름이 "start"로 시작 하는 시스템에서 모든 명령 목록을 가져옵니다를 다음 명령줄 명령을: `get-command start-*`합니다. 다른 cmdlet에서 cmdlet을 구분 하기 위해 cmdlet의 명사를 사용 합니다. 명사는 작업을 수행할 수는 리소스를 나타냅니다. 동사 작업 자체가 표시 됩니다.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Cmdlet 이름: 문자를 사용할 수 없습니다 (RD02)

Cmdlet에 이름을 지정할 때 다음과 같은 특수 문자가 사용 하지 마십시오.

|문자|이름|
|---------------|----------|
|#|숫자 기호|
|,|쉼표|
|()|괄호|
|{}|중괄호|
|[]|대괄호|
|&|앰퍼샌드|
|-|하이픈 **참고 합니다.**  명사에서 동사를 구분 하려면 하이픈을 사용할 수 있지만 동사 또는 명사 내에서 사용할 수 없습니다.|
|/|슬래시 기호|
|\|backslash|
|$|달러 기호|
|^|캐럿|
|;|세미콜론으로|
|:|콜론|
|"|큰따옴표|
|'|작은따옴표|
|<>|꺾쇠 괄호|
|&#124;|세로 막대|
|?|물음표|
|@|at 기호|
|' | 다시 눈금 (억음 악센트 기호)|
|*|별표|
|%|백분율 기호|
|+|더하기 기호|
|=|등호 기호|
|~|tilda|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>사용할 수 없는 매개 변수 이름 (RD03)

Windows PowerShell 모든 cmdlet에는 매개 변수 및 특정 상황에서 추가 되는 추가 매개 변수는 공통 집합을 제공 합니다. 사용자가 직접 cmdlet을 디자인할 때 다음 이름을 사용할 수 없습니다. 확인, Debug, ErrorAction, ErrorVariable, OutVariable, OutBuffer, WarningAction, WarningVariable, WhatIf, UseTransaction, Verbose 및 합니다. 이러한 매개 변수에 대 한 자세한 내용은 참조 하세요. [일반 매개 변수 이름](./common-parameter-names.md)합니다.

### <a name="support-confirmation-requests-rd04"></a>확인 요청 (RD04)를 지원 합니다.

시스템을 수정 하는 작업을 수행 하는 cmdlet에 대 한 호출을 [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 확인을 요청 하 여 특별 한 경우에 호출 하는 메서드는 [ System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 메서드. (합니다 [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 후에 메서드를 호출 해야 합니다 [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 메서드는.)

Cmdlet 설정 하 여 확인 요청 지원함을 지정 해야 하는 이러한 호출을 수행 하는 `SupportsShouldProcess` Cmdlet 특성의 키워드입니다. 이 특성을 설정 하는 방법에 대 한 자세한 내용은 참조 하세요. [Cmdlet 특성 선언을](./cmdlet-attribute-declaration.md)합니다.

> [!NOTE]
> Cmdlet 특성 cmdlet 클래스의 cmdlet에 대 한 호출을 지원 하는지 나타내는 경우는 [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 메서드, 및 cmdlet에 대 한 호출에 실패 했습니다는 [ System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 메서드는 사용자 시스템을 예기치 않게 수정할 수 있습니다.

사용 된 [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 시스템 수정에 대 한 메서드. 사용자 기본 설정 및 `Whatif` 매개 변수 컨트롤을 [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 메서드. 반면에 [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 호출 잠재적으로 위험한 수정에 대 한 추가 확인을 수행 합니다. 이 메서드는 사용자 기본 설정에 의해 제어 되지 또는 `Whatif` 매개 변수입니다. Cmdlet을 호출 하는 경우는 [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 가 메서드를는 `Force` 이러한 두 가지 방법에 대 한 호출을 무시 하는 하 고 작업을 진행 하는 매개 변수입니다. 이것이 중요 한 cmdlet에 비 대화형 스크립트와 호스트에서 사용할 수 있기 때문입니다.

Cmdlet에서 이러한 호출을 지원 하는 경우 사용자는 작업이 실제로 수행 되어야 하는지 여부를 확인할 수 있습니다. 예를 들어 합니다 [Stop-process](/powershell/module/microsoft.powershell.management/stop-process) cmdlet 호출을 [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Winlogon 체제를 비롯 한 중요 한 프로세스의 집합을 중지 하기 전에 및 Spoolsrv 처리 합니다.

이러한 메서드를 지원에 대 한 자세한 내용은 참조 하세요. [요청 확인](./requesting-confirmation-from-cmdlets.md)합니다.

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Force 매개 변수 (RD05) 대화형 세션에 대 한 지원

Cmdlet에 대화형으로 사용 되는 경우 항상 제공 프롬프트 또는 입력 줄 읽기와 같은 대화형 동작을 재정의 하려면 Force 매개 변수). 이것이 중요 한 cmdlet에 비 대화형 스크립트와 호스트에서 사용할 수 있기 때문입니다. 대화형 호스트에서 다음 메서드를 구현할 수 있습니다.

- [System.Management.Automation.Host.PSHostUserInterface.Prompt*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection.PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForCredential*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLine*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLineAsSecureString*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>문서 출력 개체 (RD06)

Windows PowerShell 파이프라인에 기록 되는 개체를 사용 합니다. 각 cmdlet에서 반환 되는 개체를 활용 하는 사용자에 대 한 순서 대로 반환 되는 개체를 문서화 해야 및 해당 반환 된 개체의 멤버는 용도를 문서화 해야 합니다.

## <a name="code-guidelines"></a>코드 지침

Cmdlet 코드를 작성할 때 다음 지침을 따라야 합니다. 상황에 적용 되는 코드 지침을 찾으면 유사한 지침에 대 한 디자인 지침 확인 해야 합니다.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Cmdlet 또는 PSCmdlet 클래스 (RC01)에서 파생

Cmdlet에서 파생 되어야 합니다 [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) 또는 [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 기본 클래스입니다. 파생 되는 Cmdlet를 [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) 클래스는 Windows PowerShell 런타임에 종속 되지 않습니다. 모든 Microsoft.NET Framework 언어에서 직접 호출할 수 있습니다. 파생 되는 Cmdlet를 [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 클래스는 Windows PowerShell 런타임에 따라 달라 집니다. 따라서 runspace 내에서 실행 됩니다.

구현 하는 모든 cmdlet 클래스는 공용 클래스 여야 합니다. 이러한 cmdlet은 클래스에 대 한 자세한 내용은 참조 하세요. [Cmdlet 개요](./cmdlet-overview.md)합니다.

### <a name="specify-the-cmdlet-attribute-rc02"></a>Cmdlet 특성 (RC02)를 지정 합니다.

Windows PowerShell에서 인식 되도록 하려면 cmdlet에 대 한 Cmdlet 특성을 사용 하 여 해당.NET Framework 클래스를 지정 합니다. 이 특성의 cmdlet은 다음 기능을 지정합니다.

- Cmdlet을 식별 하는 동사-명사 쌍입니다.

- 여러 매개 변수 집합이 지정 되 면 사용 되는 기본 매개 변수 집합입니다. Windows PowerShell에 사용 하도록 설정 하는 매개 변수를 확인 하는 데 충분 한 정보가 없는 경우 기본 매개 변수 집합이 사용 됩니다.

- Cmdlet에 대 한 호출을 지원 하는지 나타냅니다 합니다 [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 메서드. 이 메서드는 cmdlet은 시스템에 변경의 작업을 수행 하기 전에 사용자에 게 확인 메시지를 표시 합니다. 확인 요청을 적용 하는 방법을 하는 방법에 대 한 자세한 내용은 참조 하세요. [요청 확인](./requesting-confirmation-from-cmdlets.md)합니다.

- 확인 메시지와 연결 된 작업의 영향 수준 (또는 심각도)를 나타냅니다. 대부분의 경우에서 기본값인 보통 사용할 해야 합니다. 영향 수준을 사용자에 게 표시 되는 확인 요청에 미치는 영향에 대 한 자세한 내용은 참조 하세요. [요청 확인](./requesting-confirmation-from-cmdlets.md)합니다.

Cmdlet 특성을 선언 하는 방법에 대 한 자세한 내용은 참조 하세요. [CmdletAttribute 선언의](./cmdlet-attribute-declaration.md)합니다.

### <a name="override-an-input-processing-method-rc03"></a>입력 처리 메서드 (RC03)를 재정의 합니다.

Windows PowerShell 환경에 참여할 수 있는 cmdlet에 대 한 재정의 해야 다음 중 하나 이상이 *처리 방법을 입력*합니다.

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 이 메서드는 한 번 및 사전 처리 기능을 제공 하는 것입니다.

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 이 메서드는 여러 번 및 레코드에서 기능을 제공 하는 것입니다.

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 이 메서드는 한 번 및 후 처리 기능을 제공 하는 것입니다.

### <a name="specify-the-outputtype-attribute-rc04"></a>OutputType 특성 (RC04)를 지정 합니다.

(Windows PowerShell 2.0에 도입 됨) OutputType 특성에는 cmdlet에 파이프라인에 반환 하는.NET Framework 형식을 지정 합니다. Cmdlet의 출력 형식을 지정 하 여에서 반환한 개체 cmdlet 띄는 다른 cmdlet에서 만들 수 있습니다. 이 특성을 사용 하 여 cmdlet 클래스를 지정 하는 방법에 대 한 자세한 내용은 참조 하세요. [OutputType 특성 선언을](./outputtype-attribute-declaration.md)합니다.

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>출력 개체 (RC05)에 대 한 핸들을 보유 하지는 않습니다

Cmdlet에 전달 되는 개체에 대 한 모든 핸들을 유지 하지 해야 합니다 [System.Management.Automation.Cmdlet.WriteObject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드. 이러한 개체를 전달 하 여 파이프라인에서 다음 cmdlet 또는 스크립트에서 사용 됩니다. 개체에 대 한 핸들을 유지 하는 경우 두 엔터티 오류가 발생 하는 각 개체에 소유 됩니다.

### <a name="handle-errors-robustly-rc06"></a>오류를 안정적으로 처리 (RC06)

기본적으로 관리 환경을 검색 하 고 관리 하는 시스템에 대 한 중요 한 변경한. 따라서 cmdlet 오류를 올바르게 처리 하는 중요 한 것입니다. 오류 레코드에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 오류 보고](./error-reporting-concepts.md)합니다.

- 레코드가 더 이상 처리를 계속할 cmdlet를 방지 하는 오류, 경우에 종료 오류가 있습니다. Cmdlet을 호출 해야 합니다 [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 참조 하는 메서드는 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체입니다. Cmdlet으로는 예외가 포착 되지, Windows PowerShell 런타임 자체 보다 적은 정보를 포함 하는 종료 오류를 throw 합니다.

- Cmdlet (예를 들어, 레코드 다른 프로세스에 의해 생성), 파이프라인에서 들어오는 레코드를 비종료 오류 다음에 대 한 작업을 중지 하지 않습니다를 호출 해야 합니다는 [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 를 참조 하는 메서드를 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체입니다. 종료 되지 않는 오류의 예로 특정 프로세스를 중지 하지 못하는 경우 발생 하는 오류입니다. 호출 된 [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 사용 하면 일관 되 게 요청한 작업을 수행 하는 데 실패 하는 특정 작업에 대 한 정보를 유지 합니다. Cmdlet에 처리 해야 하지 각 레코드 최대한 독립적으로 합니다.

- 합니다 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 에서 참조 되는 개체를 [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 고 [ System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드의 핵심 예외가 필요 합니다. 사용 하는 예외를 확인 하는 경우.NET Framework 디자인 지침을 따릅니다. 오류 의미상 동일한 경우 기존 예외로, 예외 또는 해당 예외에서 파생 합니다. 그렇지 않으면 새 예외 또는 예외 계층에서 직접 파생 되는 [System.Exception](/dotnet/api/System.Exception) 형식입니다.

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체는 사용자에 대 한 오류를 그룹화 하는 오류 범주에도 필요 합니다. 값을 설정 하 여 범주에 따라 오류를 볼 수는 `$ErrorView` CategoryView 셸 변수입니다. 가능한 범주는 정의한 합니다 [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) 열거형입니다.

- Cmdlet는 새 스레드를 만드는 경우 해당 스레드에서 실행 되는 코드는 처리 되지 않은 예외를 throw 하는 경우, Windows PowerShell은 오류를 catch 하지 않습니다 및 프로세스를 종료 합니다.

- 개체 처리 되지 않은 예외를 발생 시키는 해당 소멸자에서 코드가 있을 경우 Windows PowerShell은 오류를 catch 하지 않습니다 및 프로세스를 종료 합니다. 이 개체는 처리 되지 않은 예외가 발생 하는 Dispose 메서드를 호출 하는 경우에 발생 합니다.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Cmdlet (RC07)를 배포 하는 Windows PowerShell 모듈을 사용 합니다.

패키지 배포 cmdlet을 Windows PowerShell 모듈을 만듭니다. 모듈에 대 한 지원은 Windows PowerShell 2.0에서 도입 되었습니다. 이진 모듈 파일 (이 기능은 매우 유용 cmdlet을 테스트 하는 경우)으로 직접 cmdlet 클래스를 포함 하는 어셈블리를 사용할 수 있습니다 또는 cmdlet 어셈블리를 참조 하는 모듈 매니페스트를 만들 수 있습니다. (또한 추가 기존 스냅인 어셈블리 모듈을 사용 하는 경우입니다.) 모듈에 대 한 자세한 내용은 참조 하십시오 [Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)합니다.

## <a name="see-also"></a>참고 항목

[좋습니다 개발 지침](./strongly-encouraged-development-guidelines.md)

[자문 개발 지침](./advisory-development-guidelines.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
