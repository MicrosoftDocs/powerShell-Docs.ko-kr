---
title: 확인을 요청 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 8cfbcacf93733667ffba63a252c86518c0919b57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863409"
---
# <a name="how-to-request-confirmations"></a>확인을 요청하는 방법

호출 하는 방법을 보여 주는이 예제는 [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 하 고 [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 에서 확인을 요청 하는 방법의 작업을 수행 하기 전에 사용자입니다.

> [!IMPORTANT]
> Windows PowerShell에서 이러한 요청을 처리 하는 방법에 대 한 자세한 내용은 참조 하십시오 [요청 확인](./requesting-confirmation-from-cmdlets.md)합니다.

## <a name="to-request-confirmation"></a>확인을 요청 하려면

1. 있는지 확인 합니다 `SupportsShouldProcess` cmdlet은 특성의 매개 변수는 설정 `true`합니다. (함수에 대 한 이것이 CmdletBinding 특성의 매개 변수입니다.)

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. 추가 `Force` cmdlet 매개 변수는 사용자 확인 요청을 재정의할 수 있도록 합니다.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. 추가 `if` 의 반환 값을 사용 하는 문은 합니다 [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 여부를 확인 하는 메서드는 [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 메서드가 호출 됩니다.

4. 추가 하 `if` 의 반환 값을 사용 하는 문은 합니다 [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 메서드 및 값을 `Force` 작업 해야 하는지 여부를 확인 하려면 매개 변수 수행 합니다.

## <a name="example"></a>예제

다음 코드 예제에서는 [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 및 [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 메서드 내에서 호출 되는 재정의 된 [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드. 그러나 다른 입력 처리 메서드에서에서 이러한 메서드를 호출할 수도 있습니다.

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
