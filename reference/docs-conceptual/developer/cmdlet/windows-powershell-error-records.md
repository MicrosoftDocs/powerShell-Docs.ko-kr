---
title: Windows PowerShell 오류 레코드 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- error category [PowerShell SDK]
- error identifier [PowerShell SDK]
- error records [PowerShell SDK]
- error category string [PowerShell SDK]
ms.openlocfilehash: 52243916adf18b4f3a1e00f1fb4199c2619946e9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783979"
---
# <a name="windows-powershell-error-records"></a>Windows PowerShell 오류 레코드

Cmdlet은 종료 및 종료 되지 않는 오류에 대 한 오류 조건을 식별 하는 [ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체를 전달 해야 합니다.

[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체는 다음 정보를 포함 합니다.

- 오류를 설명 하는 예외입니다. 이는 cmdlet이 발생 하 여 오류 레코드로 변환 된 경우를 제외 하는 경우가 많습니다. 모든 오류 레코드는 예외를 포함 해야 합니다.

Cmdlet이 예외를 catch 하지 않으면 새 예외를 만들고 오류 조건을 가장 잘 설명 하는 예외 클래스를 선택 해야 합니다. 그러나 [ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체의 [ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) 속성을 통해 액세스할 수 있기 때문에 예외를 throw 할 필요는 없습니다 (예외를 throw 할 필요는 없음).

- 진단 목적 및 Windows PowerShell 스크립트를 사용 하 여 특정 오류 처리기로 특정 오류 조건을 처리 하는 데 사용할 수 있는 대상 지정자를 제공 하는 오류 식별자입니다. 모든 오류 레코드는 오류 식별자 (오류 식별자 참조)를 포함 해야 합니다.

- 진단 목적으로 사용할 수 있는 일반 지정자를 제공 하는 오류 범주입니다. 모든 오류 레코드는 오류 범주를 지정 해야 합니다 (오류 범주 참조).

- 선택적 대체 오류 메시지와 권장 작업 (대체 오류 메시지 참조).

- 오류를 throw 한 cmdlet에 대 한 선택적 호출 정보입니다. 이 정보는 Windows PowerShell에서 지정 됩니다 (호출 메시지 참조).

- 오류가 발생 했을 때 처리 중 이었던 대상 개체입니다. 이는 입력 개체 일 수도 있고 cmdlet이 처리 하는 다른 개체 일 수도 있습니다. 예를 들어 명령의 경우 `remove-item -recurse c:\somedirectory` 오류는 "c:\somedirectory\lockedfile"에 대 한 FileInfo 개체의 인스턴스일 수 있습니다. 대상 개체 정보는 선택 사항입니다.

## <a name="error-identifier"></a>오류 식별자

오류 레코드를 만들 때 cmdlet 내에서 오류 조건을 지정 하는 식별자를 지정 합니다. Windows PowerShell은 대상 식별자를 cmdlet 이름과 결합 하 여 정규화 된 오류 식별자를 만듭니다. 정규화 된 오류 식별자에는 [ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체의 FullyQualifiedErrorId 속성을 통해 액세스할 수 있습니다. [ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) . 오류 식별자는 단독으로 사용할 수 없습니다. 정규화 된 오류 식별자의 일부로만 사용할 수 있습니다.

오류 레코드를 만들 때 오류 식별자를 생성 하려면 다음 지침을 따르십시오.

- 오류 조건에 해당 하는 오류 식별자를 만듭니다. 진단 목적 및 특정 오류 처리기의 특정 오류 조건을 처리 하는 스크립트에 대해 오류 식별자를 대상으로 지정 합니다. 사용자는 오류 식별자를 사용 하 여 오류와 해당 소스를 식별할 수 있어야 합니다. 또한 오류 식별자를 사용 하면 기존 예외의 특정 오류 조건에 대 한 보고를 사용 하 여 새 예외 서브 클래스가 필요 하지 않습니다.

- 일반적으로 다른 오류 식별자를 다른 코드 경로에 할당 합니다. 최종 사용자는 특정 식별자를 활용 합니다. 일반적으로 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 또는 [Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 를 호출 하는 각 코드 경로에는 고유한 식별자가 있습니다. 규칙으로 오류 메시지에 대 한 새 템플릿 문자열을 정의할 때 새 식별자를 정의 하 고 그 반대의 경우도 마찬가지입니다. 오류 메시지를 식별자로 사용 하지 마십시오.

- 특정 오류 식별자를 사용 하 여 코드를 게시 하는 경우 전체 제품 지원 기간에 대해 해당 식별자를 사용 하 여 오류 의미 체계를 설정 합니다. 원래 컨텍스트와 의미상 다른 컨텍스트에서 다시 사용 하지 마십시오. 이 오류의 의미 체계가 변경 되 면 새 식별자를 만든 다음 사용 합니다.

- 일반적으로 특정 오류 식별자는 특정 CLR 형식의 예외에만 사용 해야 합니다. 예외의 형식이 나 대상 개체의 형식이 변경 되 면 새 식별자를 만든 다음 사용 합니다.

- 보고 하는 오류에 해당 하는 오류 식별자에 대 한 텍스트를 선택 합니다. 표준 .NET Framework 명명 및 대문자화 규칙을 사용 합니다. 공백 또는 문장 부호를 사용 하지 마십시오. 오류 식별자를 지역화 하지 않습니다.

- 오류 식별자를 재현할 수 없는 방식으로 동적으로 생성 하지 마십시오. 예를 들어 프로세스 ID와 같은 오류 정보를 통합 하지 마십시오. 오류 식별자는 동일한 오류 조건이 발생 하는 다른 사용자에 게 표시 되는 오류 식별자에 해당 하는 경우에만 유용 합니다.

## <a name="error-category"></a>오류 범주

오류 레코드를 만들 때 [ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) 열거형에 정의 된 상수 중 하나를 사용 하 여 오류 범주를 지정 합니다. Windows PowerShell은 사용자가 변수를로 설정 하는 경우 오류 범주를 사용 하 여 오류 정보를 표시 합니다 `$ErrorView` `"CategoryView"` .

[ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) **NotSpecified** 상수를 사용 하지 마십시오. 오류 또는 오류를 발생 시킨 작업에 대 한 정보가 있는 경우 해당 범주가 완벽 하 게 일치 하지 않는 경우에도 오류 또는 작업을 가장 잘 설명 하는 범주를 선택 합니다.

Windows PowerShell에 표시 되는 정보는 범주-뷰 문자열 이라고 하며 [Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) 클래스의 속성에서 빌드됩니다. 이 클래스는 [ErrorRecord. CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) 속성을 통해 액세스 됩니다.

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

다음 목록에는 표시 되는 정보가 나와 있습니다.

- Category: Windows PowerShell 정의 [ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) 상수입니다.

- TargetName: 기본적으로 오류가 발생 했을 때 cmdlet이 처리 하는 개체의 이름입니다. 또는 다른 cmdlet 정의 문자열입니다.

- TargetType: 기본적으로 대상 개체의 형식입니다. 또는 다른 cmdlet 정의 문자열입니다.

- 활동: 기본적으로 오류 레코드를 만든 cmdlet의 이름입니다. 또는 다른 cmdlet 정의 문자열입니다.

- 이유: 기본적으로 예외 형식입니다. 또는 다른 cmdlet 정의 문자열입니다.

## <a name="replacement-error-message"></a>대체 오류 메시지

Cmdlet에 대 한 오류 레코드를 개발 하는 경우 오류에 대 한 기본 오류 메시지는 [system.object](/dotnet/api/System.Exception.Message) 속성의 기본 메시지 텍스트에서 가져옵니다. 이 속성은 메시지 텍스트가 디버깅 목적 으로만 사용 되는 읽기 전용 속성입니다 (.NET Framework 지침에 따라). 기본 메시지 텍스트를 바꾸거나 보완 하는 오류 메시지를 만드는 것이 좋습니다. 사용자에 게 친숙 하 고 cmdlet에 대 한 보다 구체적인 메시지를 만듭니다.

대체 메시지는 [system.web. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) 개체에서 제공 됩니다. 이 개체의 다음 생성자 중 하나를 사용 하 여 Windows PowerShell에서 사용할 수 있는 추가 지역화 정보를 제공 합니다.

- [Errordetails (cmdlet, string, string, Object [])](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Management_Automation_Cmdlet_System_String_System_String_System_Object___): 템플릿 문자열이 Cmdlet이 구현 된 어셈블리와 동일한 어셈블리에 있는 리소스 문자열이 면이 생성자를 사용 하 고, 또는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) 의 재정의를 통해 템플릿 문자열을 로드 하려는 경우이 생성자를 사용 합니다.

- [Errordetails (Assembly, string, string, Object [])](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Reflection_Assembly_System_String_System_String_System_Object___): 템플릿 문자열이 다른 어셈블리에 있고 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString)의 재정의를 통해 로드 하지 않는 경우이 생성자를 사용 합니다.

대체 메시지는 약간의 차이를 제외 하 고 예외 메시지를 작성 하기 위한 .NET Framework 디자인 지침을 따라야 합니다. 지침에서는 개발자를 위해 예외 메시지를 작성 해야 합니다. 이러한 대체 메시지는 cmdlet 사용자에 대해 작성 해야 합니다.

[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 또는 [Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드를 호출 하기 전에 대체 오류 메시지를 추가 해야 합니다 (대체 오류 메시지). 대체 메시지를 추가 하려면 오류 레코드의 [ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) 속성을 설정 합니다. 이 속성을 설정 하면 Windows PowerShell에서 기본 메시지 텍스트 대신 [system.object](/dotnet/api/System.Management.Automation.ErrorDetails.Message) 를 표시 합니다..

## <a name="recommended-action-information"></a>권장 작업 정보

또한 [이 개체는](/dotnet/api/System.Management.Automation.ErrorDetails) 오류가 발생 하는 경우 권장 되는 동작에 대 한 정보를 제공할 수 있습니다.

## <a name="invocation-information"></a>호출 정보

Cmdlet에서 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 또는 [Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 를 사용 하 여 오류 레코드를 보고 하면 Windows PowerShell에서 오류가 발생 했을 때 호출 된 명령을 설명 하는 정보를 자동으로 추가 합니다. 이 정보는 명령에 의해 호출 된 cmdlet의 이름, 명령 자체 및 파이프라인이 나 스크립트에 대 한 정보를 포함 하는 [Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo) 개체에 의해 제공 됩니다. 이 속성은 읽기 전용입니다.

## <a name="see-also"></a>참고 항목

[WriteError입니다.](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Throwterminatingerror *입니다.](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[ErrorCategory.](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0)

[Errorcategoryinfo.](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[ErrorRecord.](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.object 세부 정보](/dotnet/api/System.Management.Automation.ErrorDetails)

[Invocationinfo.](/dotnet/api/System.Management.Automation.InvocationInfo)

[Windows PowerShell 오류 보고](./error-reporting-concepts.md)

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)
