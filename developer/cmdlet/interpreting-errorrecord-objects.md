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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058779"
---
# <a name="interpreting-errorrecord-objects"></a>ErrorRecord 개체 해석

대부분의 경우에는 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체 명령 또는 스크립트에서 생성 된 종료 되지 않는 오류를 나타냅니다. 종료 오류를 통해는 ErrorRecord의 추가 정보를 지정할 수도 합니다 [System.Management.Automation.Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) 인터페이스입니다.

스크립트 또는 해석 해야 스크립트나 명령을 실행 하는 동안 발생 하는 특정 오류를 처리 하는 호스트에 오류 처리기를 작성 하려는 경우는 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체를 확인 하는지 여부를 것 오류를 처리 하려는 클래스를 나타냅니다.

Cmdlet을 발견할 종료 하는 경우 또는 종료 되지 않는 오류, 오류 조건을 설명 하는 오류 레코드를 만들어야 합니다. 호스트 응용 프로그램 이러한 오류 레코드를 조사 하 고 모든 작업 오류를 완화는 수행 해야 합니다. 호스트 응용 프로그램 레코드를 처리 하는 데 실패 했지만 계속 수 하는 종료 되지 않는 오류에 대 한 오류 레코드 조사 해야 하 고 중지 하려면 파이프라인 종료 오류에 대 한 오류 레코드를 조사 해야 합니다.

> [!NOTE]
> 종료 오류에 대 한 cmdlet을 호출 합니다 [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드. 비종료 오류에 대 한 cmdlet을 호출 합니다 [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드.

## <a name="error-record-design"></a>오류 레코드 디자인

오류 레코드는 각 error 레코드에서 결합 된 정보가 고유한 지 확인 하는 동안 예외에 사용할 수 없는 추가 오류 정보를 제공 하도록 설계 되었습니다. 이 고유성 오류 조건을 식별할 수 있습니다 하 고 호스트 작업을 수행 해야 있도록 error 레코드의 다른 부분을 검사 하는 호스트 응용 프로그램을 허용 합니다.

## <a name="interpreting-error-records"></a>오류 레코드를 해석합니다.

오류를 파악 하기 error 레코드의 여러 부분을 검토할 수 있습니다. 이러한 파트는 다음과 같습니다.

- 오류 범주

- 오류 예외

- 정규화 된 오류 식별자 (FQID)

- 기타 정보

### <a name="the-error-category"></a>오류 범주

Error 레코드의 오류 범주를 사용 하면 제공한 미리 정의 된 상수 중 하나인 합니다 [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) 열거형입니다. 이 정보를 통해 사용할 수는 [System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) 의 속성을 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체입니다.

Cmdlet은 CloseError "," OpenError "," InvalidType "," ReadError, "및" WriteError 범주 및 기타 오류 범주를 지정할 수 있습니다. 호스트 응용 프로그램 오류 범주를 사용 하 여 오류 그룹을 캡처할 수 있습니다.

### <a name="the-exception"></a>예외

Error 레코드에 포함 된 예외는 cmdlet에서 제공 되며를 통해 액세스할 수 합니다 [System.Management.Automation.ErrorRecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) 의 속성을 [ System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체입니다.

호스트 응용 프로그램이 사용할 수는 `is` 예외가 특정 클래스 또는 파생된 클래스를 식별 하는 키워드입니다. 다음 예제에서와 같이 것 예외 형식에 따라 분기에 좋습니다.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

이 따라서 파생된 클래스 catch 합니다. 그러나 예외를 deserialize 하는 경우 문제가 있습니다.

### <a name="the-fqid"></a>FQID

FQID에 오류를 식별 하 여 가장 구체적인 정보입니다. Cmdlet 클래스와 오류를 보고 하는 원본 이름, cmdlet 정의 식별자를 포함 하는 문자열입니다. 일반적으로 오류 레코드는 Windows 이벤트 로그의 이벤트 레코드는 유사 합니다. 이벤트 레코드의 클래스를 식별 하는 다음 튜플은 FQID 비슷합니다: (*로그 이름*, *원본*합니다 *이벤트 ID*).

FQID 단일 문자열을 검사 하도록 설계 되었습니다. 그러나 사례 (가) 있는 오류 식별자는 호스트 응용 프로그램에서 구문 분석 하도록 설계 되었습니다. 다음 예제에서는 잘 구성 된 정규화 된 오류 식별자입니다.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

앞의 예에서 첫 번째 토큰 오류 식별자 뒤에 cmdlet 클래스의 이름이 있는 경우 오류 식별자는 단일 토큰 이거나 검사 식별자의 분기에 대 한 허용 하는 마침표로 구분 식별자를 수 있습니다. 오류 식별자에 공백 또는 문장 부호를 사용 하지 마세요. 것이 특히 중요를; 쉼표를 사용 하지 않도록 쉼표는 cmdlet 클래스 이름과 식별자를 구분 하려면 Windows PowerShell에서 사용 됩니다.

### <a name="other-information"></a>기타 정보

합니다 [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체 오류가 발생 한 환경을 설명 하는 정보를 제공할 수도 있습니다. 이 정보에는 오류 세부 정보, 호출 정보 및 오류가 발생할 때 처리 중이 던는 대상 개체와 같은 항목이 포함 됩니다. 이 정보는 호스트 응용 프로그램에 유용 하지만 오류를 파악 하기 일반적으로 사용 되는 것은 없습니다. 이 정보는 다음 속성을 통해 제공 됩니다.

[System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System.Management.Automation.ErrorRecord.InvocationInfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System.Management.Automation.ErrorRecord.TargetObject](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>참고 항목

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[비종료 오류 보고를 Cmdlet에 추가 합니다.](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell 오류 보고](./error-reporting-concepts.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
