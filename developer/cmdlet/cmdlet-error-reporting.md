---
title: Cmdlet은 오류 보고 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error records [PowerShell], terminating
- non-terminating errors [PowerShell]
- error records [PowerShell]
- terminating errors [PowerShell]
- error records [PowerShell], non-terminating
ms.assetid: 0b014035-52ea-44cb-ab38-bbe463c5465a
caps.latest.revision: 8
ms.openlocfilehash: 45f5934314a2871ceb921c7a66b9dfb658d0bd99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068592"
---
# <a name="cmdlet-error-reporting"></a>Cmdlet 오류 보고

Cmdlet 오류는 오류를 종료 하는 여부에 따라 다르게 오류 또는 종료 되지 않는 오류를 보고 해야 합니다. 종료 오류는 파이프라인을 즉시 종료 하는 오류 또는 처리를 계속할 필요가 없는 경우 발생 하는 오류입니다. 종료 되지 않는 오류는 현재 오류 조건을 보고 하는 해당 오류 있지만 cmdlet을 계속 입력된 개체를 처리할 수 있습니다. 종료 되지 않는 오류를 사용 하 여 사용자가 일반적으로 문제의 알림을 있지만 cmdlet은 다음 입력된 개체를 처리 됩니다.

## <a name="terminating-and-nonterminating-errors"></a>종료 및 종료 되지 않는 오류

종료 오류 또는 종료 되지 않는 오류를 오류 상태 인지 확인 하려면 다음 지침을 사용할 수 있습니다.

- 오류 조건을 사용할 수 없게 cmdlet을 추가로 입력된 개체를 성공적으로 처리? 그렇다면 종료 오류입니다.

- 특정 입력된 개체에서 입력된 개체의 하위 집합에 관련 된 오류 조건? 그렇다면 종료 되지 않는 오류입니다.

- Cmdlet은 다른 입력된 개체에 대해 배포할 수 있습니다. 처리는 이러한 여러 입력된 개체를 받아들이지? 그렇다면 종료 되지 않는 오류입니다.

- 여러 개의 입력된 개체를 적용할 수 있는 Cmdlet은 특정 상황만 단일 입력된 개체에 적용 하는 경우에 종료 하는 종료 되지 않는 오류 사이의 결정 해야 합니다.

- Cmdlet 임의 개수의 입력된 개체를 수신 하 고 종료 예외를 throw 하기 전에 임의 개수의 성공 또는 오류 개체를 보낼 수 있습니다. 받은 입력된 개체의 수와 전송 성공 및 오류 개체 수 간의 관계가 없습니다.

- 0-1만 개체를 입력 하 고만 0-1 생성 적용할 수 있는 Cmdlet에는 개체를 종료 오류를 오류로 처리 하 고 종료 예외를 생성 해야 출력 합니다.

## <a name="reporting-nonterminating-errors"></a>종료 되지 않는 오류를 보고합니다.

종료 되지 않는 오류를 보고 해야 항상 내에서 수행할 cmdlet의 구현의 합니다 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 메서드를 [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드 또는 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 메서드. 호출에서 이러한 종류의 오류를 보고 합니다 [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 오류 스트림에 오류 레코드를 다시 전송 하는 메서드.

## <a name="reporting-terminating-errors"></a>종료 오류를 보고합니다.

예외를 throw 하거나 호출 하 여 종료 오류를 보고 합니다 [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드. 그러나 Windows PowerShell 런타임도 catch는으로 다시 예외를 throw 할 필요 하지 않습니다도 catch 하 고 다시 OutOfMemory 같은 예외를 throw 할 수 있습니다 cmdlet에 주의 합니다.

또한 해당 오류 레코드를 사용 하 여 기존 예외에 정보를 추가 하거나 상황에 관련 된 문제에 대 한 사용자 고유의 예외를 정의할 수 있습니다.

## <a name="error-records"></a>오류 레코드

Windows PowerShell 사용 하 여 종료 되지 않는 오류 조건을 설명 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체입니다. 각 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체는 오류 범주 정보, 선택적 대상 개체 및 오류 조건에 대 한 세부 정보를 제공 합니다.

### <a name="error-identifiers"></a>오류 식별자

오류 식별자는 간단한 문자열을 cmdlet 내에서 오류 조건을 식별 합니다. Windows PowerShell cmdlet은 식별자를 나중에 특정 오류에 응답할 때 오류 스트림 또는 오류를 필터링 하는 경우에 사용할 수 있는 정규화 된 오류 식별자를 만들 수 있는 또는 다른 사용자 고유의 활동을 사용 하 여이 식별자를 결합 합니다.

오류 식별자를 지정 하는 경우 다음 지침을 따라야 합니다.

- 서로 다른 코드 경로에 다른 항상 특정 오류 식별자를 할당 합니다. 호출 하는 각 코드 경로 [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 하거나 [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 고유 오류 식별자 있어야 합니다.

- 오류 식별자 종료 및 종료 되지 않는 오류에 대 한 CLR 예외 형식으로 고유 해야 합니다.

- Cmdlet 또는 Windows PowerShell 공급자의 버전 간에 오류 식별자의 의미 체계를 변경 하지 마세요. 오류 식별자의 의미 체계 설정 되 면 cmdlet의 수명 주기 전체에서 일정 유지 되어야 합니다.

- 종료 오류에 대 한 특정 CLR 예외 형식에 대 한 고유 오류 식별자를 사용 합니다. 예외 형식을 변경 하는 경우 새 오류 식별자를 사용 합니다.

- 종료 되지 않는 오류에 대 한 특정 입력된 개체에 대 한 특정 오류 식별자를 사용 합니다.

- 상품 보고 된 오류에 해당 하는 식별자에 대 한 텍스트를 선택 합니다. 공백 또는 문장 부호를 사용 하지 마세요.

- 재현 가능 하지 않은 오류 식별자를 생성 하지 않습니다. 예를 들어 프로세스 식별자를 포함 하는 식별자를 생성 하지 않습니다. 오류 식별자는 다른 사용자가 동일한 문제가 발생 하는 표시 되는 식별자에 해당 하는 경우에 유용 합니다.

### <a name="error-categories"></a>오류 범주

오류 범주는 최종 사용자에 대 한 오류를 그룹화 하는 데 사용 됩니다. 이러한 범주를 정의 하는 Windows PowerShell 및 cmdlet과 Windows PowerShell 공급자 오류 레코드를 생성 하는 경우 선택 해야 합니다.

사용할 수 있는 오류 범주에 대 한 참조를 [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) 열거형입니다. 일반적으로 사용 가능한 GenericError noerror 였습니다, UndefinedError, 하면 안 됩니다.

사용자 범주를 기반으로 설정 하는 경우 오류를 볼 수 있습니다 "`$ErrorView`"를 "CategoryView"입니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell Cmdlet](./cmdlet-overview.md)

[Cmdlet 출력](./types-of-cmdlet-output.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
