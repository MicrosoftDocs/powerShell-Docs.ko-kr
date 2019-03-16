---
title: Cmdlet에서 확인을 요청 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.assetid: 37d6e87f-57b7-40bd-b645-392cf0b6e88e
caps.latest.revision: 13
ms.openlocfilehash: 0c0517ef7fbd5ae6434773a2dfe276f3a8c35f39
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057408"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Cmdlet에서 확인 요청

Cmdlet은 Windows PowerShell 환경 외부에서 시스템 변경 작업을 수행 될 때 확인을 요청 해야 합니다. 예를 들어, 사용자 계정을 추가 하거나 프로세스를 중지 하려고 cmdlet 인 경우 진행 하기 전에 cmdlet을 확인 하는 사용자를 요구 해야 합니다. 반면, cmdlet 변경 되기 직전에 Windows PowerShell 변수를 cmdlet 확인이 필요 하도록 필요가 없습니다.

확인을 요청 하기 위해 cmdlet 나타내야 확인 요청을 지원 하 고 호출 해야 합니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 고 [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (선택 사항) 방법 확인 요청 메시지를 표시 합니다.

## <a name="supporting-confirmation-requests"></a>확인 요청 지원

확인 요청을 지원 하려면 cmdlet을 설정 해야 합니다 `SupportsShouldProcess` cmdlet은 특성의 매개 변수 `true`합니다. 이 통해 합니다 `Confirm` 고 `WhatIf` Windows PowerShell에서 제공 하는 cmdlet 매개 변수입니다. `Confirm` 확인 요청을 표시 되는지 여부를 매개 변수로 사용자를 제어할 수 있습니다. `WhatIf` 매개 변수 cmdlet은 메시지를 표시 하거나 해당 작업을 수행 해야 하는지 여부를 확인할 수 있습니다. 수동으로 추가 하지 마십시오 합니다 `Confirm` 및 `WhatIf` cmdlet 매개 변수입니다.

다음 예제에서는 확인 요청을 지 원하는 Cmdlet 특성 선언을 보여 줍니다.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>확인 요청 메서드를 호출합니다.

Cmdlet 코드에서 호출 된 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 시스템을 변경 하는 작업을 수행 하기 전에 메서드. 경우 호출의 값을 반환 하므로 cmdlet 설계 `false`, 작업이 수행 되지 않습니다 및 cmdlet에서 다음 작업을 처리 합니다.

## <a name="calling-the-shouldcontinue-method"></a>ShouldContinue 메서드를 호출합니다.

대부분의 cmdlet 확인만 사용 하 여 요청을 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 메서드. 그러나 일부 경우에는 추가 확인이 필요할 수 있습니다. 이러한 경우에 대 한 보완 합니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 에 대 한 호출을 사용 하 여 호출 합니다 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 메서드. Cmdlet 또는 공급자의 범위 보다 세부적인 제어를 허용 하는이 **모두 예** 확인 프롬프트에 응답 합니다.

Cmdlet을 호출 하는 경우는 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 메서드인 cmdlet도 제공 해야 합니다는 `Force` 스위치 매개 변수입니다. 사용자 지정 하는 경우 `Force` cmdlet을 계속 호출 해야 사용자가 cmdlet를 호출 하면 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)에 대 한 호출을 무시 해야 하지만 [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)합니다.

[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 사용자 없습니다 묻는 비 대화형 환경에서 호출 될 때 예외가 throw 됩니다. 추가 된 `Force` 매개 변수 확인 비 대화형 환경에서 호출 될 때 명령이 수행 여전히 수 있습니다.

다음 예제에서는 호출 하는 방법을 보여 줍니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 하 고 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)합니다.

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

동작을 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 호출 cmdlet가 호출 되는 환경에 따라 달라질 수 있습니다. 이전 지침을 사용 하 여 cmdlet은 호스트 환경에 관계 없이 다른 cmdlet과 일관 되 게 작동 하는지 확인 하는 데 도움이 됩니다.

호출의 예는 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 메서드를 참조 하십시오 [요청 확인 하는 방법을](./how-to-request-confirmations.md)합니다.

## <a name="specify-the-impact-level"></a>영향 수준을 지정 합니다.

Cmdlet를 만들 때 변경의 영향 수준 (심각도)를 지정 합니다. 이 위해 값을 설정 합니다 `ConfirmImpact` 높음, 중간 또는 낮음 Cmdlet 특성의 매개 변수입니다. 에 대 한 값을 지정할 수 있습니다 `ConfirmImpact` 만 지정 하는 경우도 `SupportsShouldProcess` cmdlet에 대 한 매개 변수입니다.

대부분의 cmdlet에 대 한 필요가 없습니다를 명시적으로 지정 `ConfirmImpact`합니다.  대신 사용 중간은 매개 변수의 기본값입니다. 설정한 경우 `ConfirmImpact` 높음으로 작업이 기본적으로 확인 됩니다. 하드 디스크 볼륨을 다시 포맷 하는 등 항상 중단 작업의 경우이 설정은 예약 합니다.

## <a name="calling-non-confirmation-methods"></a>확인 되지 않은 메서드 호출

Cmdlet 또는 공급자는 메시지를 전송 해야 하지만 확인을 요청 하지, 다음 세 가지 메서드를 호출할 수 있습니다. 사용 하지 않도록 합니다 [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 때문에 이러한 유형의 메시지를 전송 하는 방법 [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 출력은 혼합 cmdlet 또는 공급자의 표준 출력에 스크립트 작성을 어렵게 만듭니다.

- 사용자를 주의 하 고 작업을 계속 하는 cmdlet 또는 공급자를 호출할 수 있습니다 합니다 [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) 메서드.

- 사용자를 사용 하 여 검색할 수 있는 추가 정보를 제공 하는 `Verbose` 매개 변수, cmdlet 또는 공급자를 호출할 수는 [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 메서드.

- 제품 지원이 필요 하거나 다른 개발자를 위한 디버깅 수준 세부 정보를 제공, cmdlet 또는 공급자를 호출할 수 있습니다 합니다 [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 메서드. 사용 하 여이 정보를 검색할 수는 `Debug` 매개 변수입니다.

Cmdlet 및 공급자의 경우 Windows PowerShell의 외부 시스템을 변경 하는 작업을 수행 하기 전에 확인을 요청에 다음 메서드를 호출 하는 먼저:

- [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

호출 하 여 그렇게 합니다 [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 사용자 명령을 호출 하는 방식에 따라 작업을 확인 하 라는 메시지는 메서드.

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
