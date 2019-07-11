---
title: Windows PowerShell 오류 기록 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error category [PowerShell SDK]
- error identifier [PowerShell SDK]
- error records [PowerShell SDK]
- error category string [PowerShell SDK]
ms.assetid: bdd66fea-eb63-4bb6-9cbe-9a799e5e0db5
caps.latest.revision: 9
ms.openlocfilehash: 5412d88b690a1f5f1ef387416e3bf9da3a32c95d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735069"
---
# <a name="windows-powershell-error-records"></a>Windows PowerShell 오류 레코드

Cmdlet에 전달 해야 합니다는 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 종료 및 종료 되지 않는 오류에 대 한 오류 조건을 식별 하는 개체입니다.

합니다 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체에는 다음 정보를 포함 합니다.

- 오류를 설명 하는 예외입니다. 종종 이것이 cmdlet 포착 하 고 오류 레코드를 변환 하는 예외입니다. 모든 오류 레코드에는 예외가 있어야 합니다.

Cmdlet는 예외를 catch 하지 않은, 새 예외 하며 가장 오류 조건을 설명 하는 예외 클래스를 선택 합니다. 그러나 필요가 없습니다를 통해 액세스할 수 있기 때문에 예외를 throw 하는 [System.Management.Automation.ErrorRecord.Exception](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) 의 속성을 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)개체입니다.

- 특정 오류 처리기를 사용 하 여 특정 오류 조건을 처리 하 게 진단 목적 및 Windows PowerShell 스크립트에서 사용할 수 있는 대상된 지정자를 제공 하는 오류 식별자입니다. 모든 오류 레코드 오류 식별자를 포함 해야 합니다 (오류 식별자 참조).

- 진단 용도로 사용할 수 있는 일반 지정자를 제공 하는 오류 범주입니다. 모든 오류 레코드에는 오류 범주를 지정 해야 합니다 (오류 범주 참조).

- 선택적 대체 오류 메시지 및 권장 되는 작업 (대체 오류 메시지 참조).

- 오류를 발생 시킨 cmdlet에 대 한 선택적 호출 정보입니다. 이 정보는 Windows PowerShell에서 지정 됩니다 (호출 메시지 참조).

- 오류가 발생 했을 때 처리 되 고 있던 대상 개체입니다. 이 입력된 개체를 수 있습니다 또는 cmdlet에서 처리 하는 다른 개체 일 수 있습니다. 명령에 대 한 예를 들어 `remove-item -recurse c:\somedirectory`, "c:\somedirectory\lockedfile"에 대 한 FileInfo 개체의 인스턴스를 오류일 수 있습니다. 대상 개체 정보를 선택 사항입니다.

## <a name="error-identifier"></a>오류 식별자

오류 레코드를 만든 경우 cmdlet 내에서 오류 조건을 지정 하는 식별자를 지정 합니다. Windows PowerShell 오류 정규화 된 식별자를 만들기 위해 cmdlet의 이름으로 대상으로 지정 된 식별자를 결합 합니다. 정규화 된 오류 식별자를 통해 액세스할 수는 [System.Management.Automation.ErrorRecord.FullyQualifiedErrorId](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) 의 속성을 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)개체입니다. 오류 식별자 단독으로 사용할 수 없는 경우 사용할 수 있는 정규화 된 오류 식별자의 일부로 합니다.

오류 레코드를 만들 때 오류 식별자를 생성 하려면 다음 지침을 따르세요.

- 오류 조건에 특정 오류 식별자를 확인 합니다. 진단 목적 및 특정 오류 처리기를 사용 하 여 특정 오류 조건을 처리 하는 스크립트에 대 한 오류 식별자를 대상으로 합니다. 사용자 오류 식별자를 사용 하 여 오류와 해당 소스 식별에 있어야 합니다. 또한 오류 식별자는 새 예외 서브 클래스 필요 하지 않은 있도록 기존 예외 로부터 특정 오류 조건에 대 한 보고 사용 하도록 설정 합니다.

- 일반적으로 서로 다른 코드 경로에 다른 오류 식별자를 할당 합니다. 최종 사용자가 특정 식별자에서 이점을 제공합니다. 호출 하는 각 코드 경로 종종 [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 또는 [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 자체 식별자. 일반적으로 오류 메시지 및 그 반대로 새 템플릿 문자열을 정의 하는 경우 새 식별자를 정의 합니다. 오류 메시지 식별자로 사용 하지 마세요.

- 특정 오류 식별자를 사용 하 여 코드를 게시할 때 전체 제품에 대 한 해당 식별자를 사용 하 여 오류의 의미 체계 지원 수명 주기 설정할 수 있습니다. 원래 컨텍스트에서 의미 체계가 다른 컨텍스트에서 재사용 하지 않습니다. 이 오류의 의미 체계를 변경 하는 경우 만들고 새 식별자를 사용 하 여 합니다.

- 일반적으로 특정 CLR 형식의 예외에 대해서만 특정 오류 식별자를 사용 해야 합니다. 예외의 형식 또는 대상 개체의 변경 되 면 만들고 새 식별자를 사용 하 여 합니다.

- 간결 하 게 해당 오류를 보고 하는 오류 식별자에 대 한 텍스트를 선택 합니다. 표준.NET Framework 명명 및 대/소문자 규칙을 사용 합니다. 공백 또는 문장 부호를 사용 하지 마세요. 오류 식별자를 지역화 하지 않습니다.

- 재현할 수 없는 방식으로 오류 식별자를 동적으로 생성 하지 않습니다. 예를 들어, 프로세스 ID와 같은 오류 정보를 통합 하지 않습니다 오류 식별자는 동일한 오류 조건이 발생 한 다른 사용자가 볼 오류 식별자에 해당 하는 경우에 유용 합니다.

## <a name="error-category"></a>오류 범주

오류 레코드를 만들 때 정의 된 상수 중 하나를 사용 하 여 오류의 범주를 지정 합니다 [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) 열거형입니다. Windows PowerShell의 오류 범주를 사용 하 여 사용자가 설정 된 경우 오류 정보를 표시 하는 `$ErrorView` 변수를 `"CategoryView"`입니다.

사용 하지 않도록 합니다 [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) **NotSpecified** 상수입니다. 또는 오류를 발생 시킨 작업에 대 한 오류에 대 한 정보를 사용 하는 경우 범주를 완벽 하 게 일치 하지 않습니다. 경우에 오류 또는 작업을 가장 잘 설명 하는 범주를 선택 합니다.

Windows PowerShell에서 표시 되는 정보는 종류별 보기 문자열로 참조 되며의 속성에서 빌드되는 [System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) 클래스입니다. (이 클래스는 오류를 통해서나 [System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) 속성입니다.)

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

다음 목록에서는 표시 되는 정보를 설명 합니다.

- 범주: Windows PowerShell 정의한 [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) 상수입니다.

- TargetName: 기본적으로 개체의 이름을 cmdlet가 처리 오류가 발생 합니다. 또는 다른 cmdlet 정의한 문자열입니다.

- TargetType: 기본적으로 대상 개체의 형식입니다. 또는 다른 cmdlet 정의한 문자열입니다.

- 활동: 기본적으로 오류 레코드를 생성 하는 cmdlet의 이름입니다. 또는 일부 다른 cmdlet 정의한 문자열입니다.

- 이유: 기본적으로 예외 형식입니다. 또는 다른 cmdlet 정의한 문자열입니다.

## <a name="replacement-error-message"></a>대체 오류 메시지

기본 메시지 텍스트에서 오류에 대 한 기본 오류 메시지는 cmdlet에 대 한 오류 레코드를 개발 하는 경우는 [System.Exception.Message](/dotnet/api/System.Exception.Message) 속성입니다. 해당 메시지 텍스트는만 디버깅용으로 사용 (.NET Framework 지침)에 따라 읽기 전용 속성입니다. 기본 메시지 텍스트를 확대 하거나이 대체 하는 오류 메시지를 만드는 것이 좋습니다. Cmdlet에 더 친숙 하 고 자세한 메시지를 확인 합니다.

대체 메시지에서 제공 되는 [System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) 개체입니다. Windows PowerShell에서 사용할 수 있는 추가 지역화 정보를 제공 하기 때문에이 개체의 생성자 중 하나를 사용 합니다.

- [ErrorDetails(Cmdlet, String, String, Object[])](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Management_Automation_Cmdlet_System_String_System_String_System_Object___): 템플릿 문자열에는 cmdlet를 구현 하는 동일한 어셈블리에 리소스 문자열 또는 재정의 통해 템플릿 문자열을 로드 하려는 경우이 생성자를 사용 하 여 [System.Management.Automation.Cmdlet.GetResourceString ](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) 메서드.

- [ErrorDetails(Assembly, String, String, Object[])](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Reflection_Assembly_System_String_System_String_System_Object___): 이 생성자를 사용 하 여 템플릿 문자열에는 다른 어셈블리 내에 있고 재정의 통해 것을 로드 하지 [System.Management.Automation.Cmdlet.GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString)합니다.

대체 메시지는 약간의 차이점이 사용 하 여 예외 메시지를 작성 하기 위한.NET Framework 디자인 지침을 따라야 합니다. 예외 메시지 개발자를 위한 기록 되어야 하는 지침 상태입니다. Cmdlet은 사용자에 대 한 이러한 대체 메시지를 작성 되어야 합니다.

전에 교체 오류 메시지를 추가 해야 합니다 [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 또는 [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드를 호출 합니다. 대체 메시지를 추가 하려면 설정 합니다 [System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) error 레코드의 속성입니다. 이 속성을 설정 하는 경우 Windows PowerShell에 표시 됩니다는 [System.Management.Automation.ErrorDetails.Message*](/dotnet/api/System.Management.Automation.ErrorDetails.Message) 기본 메시지 텍스트 대신 속성입니다.

## <a name="recommended-action-information"></a>작업 정보를 권장합니다.

합니다 [System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) 개체 오류가 발생 하는 경우 권장 되는 작업에 대 한 정보를 제공할 수도 있습니다.

## <a name="invocation-information"></a>호출 정보

Cmdlet을 사용 하는 경우 [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 하거나 [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) Windows PowerShell 오류 레코드를 보고 하려면 오류가 발생할 때 호출 된 명령을 설명 하는 정보를 자동으로 추가 합니다. 이 정보는 [System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo) 명령 자체를 명령에 의해 호출 된 cmdlet의 이름이 포함 된 개체 및 파이프라인 또는 스크립트에 대 한 정보입니다. 이 속성은 읽기 전용입니다.

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Windows PowerShell 오류 보고](./error-reporting-concepts.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
