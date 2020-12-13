---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 오류 보고
description: Cmdlet 오류 보고
ms.openlocfilehash: f06cf98183d56249080623895bd1f5a3e070cefd
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653408"
---
# <a name="cmdlet-error-reporting"></a>Cmdlet 오류 보고

Cmdlet은 오류 종료 오류 또는 종료 되지 않는 오류에 따라 오류를 다르게 보고 해야 합니다. 종료 오류는 파이프라인이 즉시 종료 되도록 하는 오류 또는 처리를 계속할 이유가 없을 때 발생 하는 오류입니다. 종료 되지 않는 오류는 현재 오류 조건을 보고 하는 오류 이지만 cmdlet은 입력 개체를 계속 처리할 수 있습니다. 종료 되지 않는 오류가 발생 하면 일반적으로 사용자에 게 문제에 대 한 알림이 표시 되지만이 cmdlet은 다음 입력 개체를 계속 처리 합니다.

## <a name="terminating-and-nonterminating-errors"></a>종료 및 비 종료 오류

다음 지침을 사용 하 여 오류 조건이 종료 오류 인지 아니면 종료 되지 않는 오류 인지를 확인할 수 있습니다.

- 오류 조건으로 인해 cmdlet이 더 이상 입력 개체를 성공적으로 처리 하지 못하는 경우 그렇다면 종료 오류입니다.

- 특정 입력 개체 또는 입력 개체의 하위 집합과 관련 된 오류 조건 입니까? 그럴 경우 종료 되지 않는 오류입니다.

- 이 cmdlet은 다른 입력 개체에서 처리가 성공할 수 있는 여러 입력 개체를 허용 하나요? 그럴 경우 종료 되지 않는 오류입니다.

- 여러 입력 개체를 사용할 수 있는 cmdlet은 특정 상황이 단일 입력 개체에만 적용 되는 경우에도 종료 및 종료 되지 않는 오류를 결정 해야 합니다.

- Cmdlet은 원하는 수의 입력 개체를 수신 하 고 종료 예외를 throw 하기 전에 원하는 수의 성공 또는 오류 개체를 보낼 수 있습니다. 수신 된 입력 개체의 수와 전송 된 성공 및 오류 개체의 수에는 관계가 없습니다.

- 0-1 입력 개체만 허용 하 고 0-1 출력 개체만 생성할 수 있는 cmdlet은 오류를 종료 오류로 처리 하 고 종료 예외를 생성 합니다.

## <a name="reporting-nonterminating-errors"></a>종료 되지 않는 오류 보고

종료 되지 않는 오류에 대 한 보고는 항상 cmdlet의 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드 또는 system.object 구현 내에서 수행 [해야 합니다 (](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 예를 들어,, 또는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) ... s a s.). 이러한 오류 유형은 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 하 여 오류 스트림으로 오류 레코드를 전송 하 여 보고 됩니다.

## <a name="reporting-terminating-errors"></a>종료 오류 보고

종료 오류는 예외를 throw 하거나 [ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드를 호출 하 여 보고 됩니다. 또한 cmdlet은 **OutOfMemory** 와 같은 예외를 catch 하 고 다시 throw 할 수 있지만, PowerShell 런타임이 이러한 예외를 catch 하는 것 처럼 예외를 다시 throw 하는 것은 필요 하지 않습니다.

상황과 관련 된 문제에 대 한 사용자 고유의 예외를 정의 하거나 해당 오류 레코드를 사용 하 여 기존 예외에 추가 정보를 추가할 수도 있습니다.

## <a name="error-records"></a>오류 레코드

PowerShell에서는 [ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체를 사용 하 여 종료 되지 않는 오류 조건을 설명 합니다. 각 개체는 오류 범주 정보, 선택적 대상 개체 및 오류 조건에 대 한 세부 정보를 제공 합니다.

### <a name="error-identifiers"></a>오류 식별자

오류 식별자는 cmdlet 내에서 오류 조건을 식별 하는 간단한 문자열입니다.
PowerShell은이 식별자와 cmdlet 식별자를 결합 하 여 나중에 오류 스트림을 필터링 하거나 오류를 기록 하거나, 특정 오류에 응답할 때 또는 다른 사용자별 작업을 수행할 때 사용할 수 있는 정규화 된 오류 식별자를 만듭니다.

오류 식별자를 지정할 때는 다음 지침을 따라야 합니다.

- 다른 코드 경로에 서로 다른 매우 구체적인 오류 식별자를 할당 합니다. [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 또는 [ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 를 호출 하는 각 코드 경로에는 고유한 오류 식별자가 있어야 합니다.

- 오류 식별자는 종료 및 종료 되지 않는 오류 모두에 대 한 CLR (공용 언어 런타임) 예외 유형에 대해 고유 해야 합니다.

- Cmdlet 또는 PowerShell 공급자의 버전 간에 오류 식별자의 의미 체계를 변경 하지 마세요. 오류 식별자의 의미 체계가 설정 된 후에는 cmdlet의 수명 주기 내내 일정 하 게 유지 되어야 합니다.

- 종료 오류의 경우 특정 CLR 예외 유형에 대해 고유한 오류 식별자를 사용 합니다. 예외 형식이 변경 되 면 새 오류 식별자를 사용 합니다.

- 종료 되지 않는 오류의 경우 특정 입력 개체에 대 한 특정 오류 식별자를 사용 합니다.

- 보고 되는 오류에 해당 하는 tersely 식별자에 대 한 텍스트를 선택 합니다. 공백 또는 문장 부호를 사용 하지 않습니다.

- 재현 하지 않는 오류 식별자는 생성 하지 않습니다. 예를 들어 프로세스 식별자를 포함 하는 식별자를 생성 하지 않습니다. 오류 식별자는 동일한 문제가 발생 하는 다른 사용자에 게 표시 되는 식별자에 해당 하는 경우에만 유용 합니다.

### <a name="error-categories"></a>오류 범주

오류 범주는 사용자에 대 한 오류를 그룹화 하는 데 사용 됩니다. PowerShell은 이러한 범주 및 cmdlet을 정의 하 고 PowerShell 공급자는 오류 레코드를 생성할 때 이러한 범주와 cmdlet 중 하나를 선택 해야 합니다.

사용할 수 있는 오류 범주에 대 한 설명은 [ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) 열거를 참조 하세요. 일반적으로 가능한 경우 **noerror**, **UndefinedError** 및 **genericerror** 를 사용 하지 않도록 해야 합니다.

사용자는 `$ErrorView` **categoryview** 로 설정 된 범주에 따라 오류를 볼 수 있습니다.

## <a name="see-also"></a>참고 항목

[Cmdlet 개요](./cmdlet-overview.md)

[Cmdlet 출력 형식](./types-of-cmdlet-output.md)

[Windows PowerShell 참조](../windows-powershell-reference.md)
