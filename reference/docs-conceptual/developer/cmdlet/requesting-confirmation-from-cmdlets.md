---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet에서 확인 요청
description: Cmdlet에서 확인 요청
ms.openlocfilehash: fd869d50b185cb4d38269640df58ec284a32da50
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646403"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Cmdlet에서 확인 요청

Cmdlet은 Windows PowerShell 환경 외부에 있는 시스템을 변경 하려고 할 때 확인을 요청 해야 합니다. 예를 들어 cmdlet에서 사용자 계정을 추가 하거나 프로세스를 중지 하려는 경우에는 cmdlet을 실행 하기 전에 사용자의 확인이 필요 합니다. 반면에 cmdlet이 Windows PowerShell 변수를 변경 하려는 경우에는 cmdlet에 확인이 필요 하지 않습니다.

확인 요청을 수행 하기 위해 cmdlet은 확인 요청을 지원 하도록 지정 해야 하며, 확인 요청 메시지를 표시 하려면 [system.web](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .. n a m a. a m a. a m [a.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)

## <a name="supporting-confirmation-requests"></a>확인 요청 지원

확인 요청을 지원 하려면 cmdlet에서 `SupportsShouldProcess` cmdlet 특성의 매개 변수를로 설정 해야 합니다 `true` . 이를 통해 `Confirm` `WhatIf` Windows PowerShell에서 제공 하는 및 cmdlet 매개 변수를 사용할 수 있습니다. `Confirm`사용자는 매개 변수를 사용 하 여 확인 요청이 표시 되는지 여부를 제어할 수 있습니다. `WhatIf`사용자는 매개 변수를 사용 하 여 cmdlet이 메시지를 표시 하거나 작업을 수행할지 여부를 결정할 수 있습니다. `Confirm`Cmdlet에 및 매개 변수를 수동으로 추가 하지 마십시오 `WhatIf` .

다음 예에서는 확인 요청을 지 원하는 Cmdlet 특성 선언을 보여 줍니다.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>확인 요청 메서드 호출

Cmdlet 코드에서 시스템을 변경 하는 작업을 수행 하기 전에 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 메서드를 호출 합니다. 호출에서 값을 반환 하는 경우 `false` 작업이 수행 되지 않고 cmdlet이 다음 작업을 처리 하도록 cmdlet을 디자인 합니다.

## <a name="calling-the-shouldcontinue-method"></a>ShouldContinue 메서드 호출

대부분의 cmdlet은 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 사용 하 여 확인을 요청 합니다. 그러나 일부 경우에는 추가 확인이 필요할 수 있습니다. 이러한 경우 [에는 system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하 여.. s a s.. n a m a [..](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 이렇게 하면 cmdlet 또는 공급자가 확인 프롬프트에 대 한 **모든 응답에** 대 한 예의 범위를 보다 세밀 하 게 제어할 수 있습니다.

Cmdlet이 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 하는 경우에는 cmdlet에서 `Force` 스위치 매개 변수도 제공 해야 합니다. 사용자가 cmdlet을 호출할 때 사용자가 지정 하는 경우 `Force` cmdlet은 여전히 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)를 호출 해야 하지만,이 프로세스는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)호출을 무시 해야 합니다.

사용자에 게 메시지가 표시 되지 않는 비 대화형 환경에서 호출 되는 경우 [에는 예외가 throw 됩니다.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 매개 변수를 추가 하면 `Force` 비 대화형 환경에서 호출 하는 경우에도 명령을 수행할 수 있습니다.

다음 예제에서는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하는 [방법과. n](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)a m a. n a m a. a m a를 호출 하는 방법을 보여 줍니다.

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

[System.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하는 동작은 cmdlet이 호출 되는 환경에 따라 달라질 수 있습니다. 위의 지침을 사용 하면 호스트 환경에 관계 없이 cmdlet이 다른 cmdlet과 일관 되 게 동작 하도록 할 수 있습니다.

[System.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하는 방법에 대 한 예제는 확인 [을 요청 하는 방법](./how-to-request-confirmations.md)을 참조 하세요.

## <a name="specify-the-impact-level"></a>영향 수준 지정

Cmdlet을 만들 때 변경의 영향 수준 (심각도)을 지정 합니다. 이렇게 하려면 `ConfirmImpact` Cmdlet 특성의 매개 변수 값을 높음, 중간 또는 낮음으로 설정 합니다. `ConfirmImpact` `SupportsShouldProcess` Cmdlet에 대 한 매개 변수를 지정 하는 경우에만 값을 지정할 수 있습니다.

대부분의 cmdlet에 대해를 명시적으로 지정할 필요는 없습니다 `ConfirmImpact` .  대신 매개 변수의 기본 설정인 Medium을 사용 합니다. 높게 설정 하면 `ConfirmImpact` 작업이 기본적으로 확인 됩니다. 하드 디스크 볼륨을 다시 포맷 하는 등의 매우 방해가 되는 작업에 대해이 설정을 예약 합니다.

## <a name="calling-non-confirmation-methods"></a>확인 되지 않은 메서드 호출

Cmdlet 또는 공급자가 메시지를 전송 해야 하지만 확인을 요청 하지 않는 경우 다음 세 가지 메서드를 호출할 수 있습니다. [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드를 사용 하 여 이러한 형식의 메시지를 보내는 것이 좋습니다. [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 출력은 Cmdlet 또는 공급자의 일반적인 출력과 함께 혼합 스크립트를 작성 하기 어려울 수 있기 때문입니다.

- 사용자가 작업을 수행 하 고 작업을 계속 하기 위해 cmdlet 또는 공급자는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) 를 호출할 수 있습니다.

- 사용자가 매개 변수를 사용 하 여 검색할 수 있는 추가 정보를 제공 하기 위해 `Verbose` cmdlet 또는 공급자는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 를 호출할 수 있습니다.

- 다른 개발자 또는 제품 지원에 대 한 디버깅 수준 세부 정보를 제공 하기 위해 cmdlet 또는 공급자는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 를 호출할 수 있습니다. 사용자는 매개 변수를 사용 하 여이 정보를 검색할 수 있습니다 `Debug` .

Cmdlet 및 공급자는 먼저 다음 메서드를 호출 하 여 Windows PowerShell 외부에서 시스템을 변경 하는 작업을 수행 하기 전에 확인을 요청 합니다.

- [System.object를 처리 합니다.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System.web.. a n a.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

사용자가 명령을 호출 하는 방법에 따라 작업을 확인 하 라는 메시지를 표시 하는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하 여이 작업을 수행 합니다.

## <a name="see-also"></a>관련 항목

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)
