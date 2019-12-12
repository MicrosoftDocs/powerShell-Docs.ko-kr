---
title: ErrorRecord 개체 해석 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: 32ebf2531237bfd1042310ccc4155193a58401fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365422"
---
# <a name="interpreting-errorrecord-objects"></a>ErrorRecord 개체 해석

대부분의 경우 [ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체는 명령 또는 스크립트에 의해 생성 되는 종료 되지 않는 오류를 나타냅니다. 종료 오류는 [Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) 인터페이스를 통해 ErrorRecord에서 추가 정보를 지정할 수도 있습니다.

스크립트나 스크립트를 실행 하는 동안 발생 하는 특정 오류를 처리 하는 스크립트 또는 호스트에 오류 처리기를 쓰려면 [ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체를 해석 하 여 처리 하려는 오류 클래스를 나타내는지 여부를 확인 해야 합니다.

Cmdlet이 종료 또는 종료 되지 않는 오류를 발견 하면 오류 조건을 설명 하는 오류 레코드를 만들어야 합니다. 호스트 응용 프로그램은 이러한 오류 레코드를 조사 하 고 오류를 완화 하는 모든 작업을 수행 해야 합니다. 또한 호스트 응용 프로그램은 레코드를 처리 하는 데 실패 했지만 계속 진행할 수 있는 종료 되지 않는 오류에 대 한 오류 레코드를 조사 해야 하며, 파이프라인을 중지 시킨 종료 오류에 대 한 오류 레코드를 조사 해야 합니다.

> [!NOTE]
> 종료 오류의 경우 cmdlet은 [Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드를 호출 합니다. 종료 되지 않는 오류의 경우 cmdlet은 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 합니다.

## <a name="error-record-design"></a>오류 레코드 디자인

오류 레코드는 각 오류 레코드의 조합 된 정보가 고유한 지 확인 하는 동안 예외에서 사용할 수 없는 추가 오류 정보를 제공 하도록 설계 되었습니다. 이 고유성을 통해 호스트 응용 프로그램은 오류 조건 및 호스트에서 수행 해야 하는 작업을 식별할 수 있도록 오류 레코드의 다른 부분을 검사할 수 있습니다.

## <a name="interpreting-error-records"></a>오류 레코드 해석

오류 레코드의 여러 부분을 검토 하 여 오류를 식별할 수 있습니다. 이러한 구성 요소에는 다음이 포함 됩니다.

- 오류 범주

- 오류 예외

- 정규화 된 오류 식별자 (FQID)

- 기타 정보

### <a name="the-error-category"></a>오류 범주

오류 레코드의 오류 범주는 [Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) 열거형에서 제공 하는 미리 정의 된 상수 중 하나입니다. 이 정보는 [ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체의 [ErrorRecord. CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) 속성을 통해 사용할 수 있습니다.

Cmdlet은 CloseError, OpenError, InvalidType, ReadError 및 WriteError 범주와 기타 오류 범주를 지정할 수 있습니다. 호스트 응용 프로그램은 오류 범주를 사용 하 여 오류 그룹을 캡처할 수 있습니다.

### <a name="the-exception"></a>예외입니다.

오류 레코드에 포함 된 예외는 cmdlet에 의해 제공 되며 [ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체의 [ErrorRecord *](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) 속성을 통해 액세스할 수 있습니다 ().

호스트 응용 프로그램은 `is` 키워드를 사용 하 여 예외가 특정 클래스 인지 또는 파생 클래스 인지를 식별할 수 있습니다. 다음 예제와 같이 예외 형식에 대해 분기 하는 것이 좋습니다.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

이러한 방식으로 파생 된 클래스를 catch 할 수 있습니다. 그러나 예외가 deserialize 되는 경우 문제가 발생 합니다.

### <a name="the-fqid"></a>FQID

FQID는 오류를 식별 하는 데 사용할 수 있는 가장 구체적인 정보입니다. Cmdlet 정의 식별자, cmdlet 클래스 이름 및 오류를 보고 한 소스를 포함 하는 문자열입니다. 일반적으로 오류 레코드는 Windows 이벤트 로그의 이벤트 레코드와 유사 합니다. FQID는 이벤트 레코드의 클래스를 식별 하는 다음 튜플과 유사 합니다. (*로그 이름*, *원본*, *이벤트 ID*).

FQID는 단일 문자열로 검사 되도록 설계 되었습니다. 그러나 오류 식별자가 호스트 응용 프로그램에서 구문 분석 하도록 디자인 된 경우도 있습니다. 다음 예제는 잘 구성 된 정규화 된 오류 식별자입니다.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

이전 예제에서 첫 번째 토큰은 오류 식별자 이며, 그 뒤에 cmdlet 클래스 이름이 옵니다. 오류 식별자는 단일 토큰이 될 수도 있고 식별자 검사에 대 한 분기를 허용 하는 점으로 구분 된 식별자 일 수도 있습니다. 오류 식별자에 공백이 나 문장 부호를 사용 하지 마십시오. 특히 쉼표를 사용 하지 않는 것이 중요 합니다. Windows PowerShell에서는 쉼표를 사용 하 여 식별자와 cmdlet 클래스 이름을 구분 합니다.

### <a name="other-information"></a>기타 정보

[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체는 또한 오류가 발생 한 환경을 설명 하는 정보를 제공할 수 있습니다. 이 정보에는 오류 정보, 호출 정보 및 오류가 발생 했을 때 처리 중 이었던 대상 개체와 같은 항목이 포함 됩니다. 이 정보는 호스트 응용 프로그램에 유용할 수 있지만 일반적으로 오류를 식별 하는 데 사용 되지 않습니다. 이 정보는 다음 속성을 통해 제공 됩니다.

[ErrorRecord에 대 한 자세한 정보](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[ErrorRecord. InvocationInfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[ErrorRecord. TargetObject](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>참고 항목

[ErrorRecord.](/dotnet/api/System.Management.Automation.ErrorRecord)

[Errorcategory.](/dotnet/api/System.Management.Automation.ErrorCategory)

[Errorcategoryinfo.](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[WriteError입니다.](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Throwterminatingerror *입니다.](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[Cmdlet에 종료 되지 않는 오류 보고 추가](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell 오류 보고](./error-reporting-concepts.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
