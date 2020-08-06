---
title: 확인을 요청 하는 방법 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ebe928724f1b750afc11c1e3c1207375f4ec8e42
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784098"
---
# <a name="how-to-request-confirmations"></a>확인을 요청하는 방법

이 예제에서는 작업을 수행 하기 전에 사용자의 확인을 요청 하는 데 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 및 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 하는 방법을 보여 줍니다.

> [!IMPORTANT]
> Windows PowerShell에서 이러한 요청을 처리 하는 방법에 대 한 자세한 내용은 [확인 요청](./requesting-confirmation-from-cmdlets.md)을 참조 하십시오.

## <a name="to-request-confirmation"></a>확인 요청

1. `SupportsShouldProcess`Cmdlet 특성의 매개 변수가로 설정 되었는지 확인 `true` 합니다. 함수의 경우이는 CmdletBinding 특성의 매개 변수입니다.

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. `Force`사용자가 확인 요청을 재정의할 수 있도록 cmdlet에 매개 변수를 추가 합니다.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. System.object `if` 의 반환 값을 사용 하는 문을 추가 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 하 여 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 하는지 여부를 확인 합니다 .이 메서드는.

4. `if` [System.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 의 반환 값 및 매개 변수 값을 사용 하 여 작업을 수행할지 여부를 결정 하는 두 번째 문을 추가 합니다 `Force` .

## <a name="example"></a>예제

다음 코드 예제에서 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 재정의 하는 동안에는 [system.web](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .. n a m a. a m a. a m a. a m [a.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 그러나 다른 입력 처리 메서드에서 이러한 메서드를 호출할 수도 있습니다.

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

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)
