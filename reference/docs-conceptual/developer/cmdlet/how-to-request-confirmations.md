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
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369682"
---
# <a name="how-to-request-confirmations"></a>확인을 요청하는 방법

이 예제에서는 작업을 수행 하기 전에 사용자의 확인을 요청 하는 데 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 및 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 하는 방법을 보여 줍니다.

> [!IMPORTANT]
> Windows PowerShell에서 이러한 요청을 처리 하는 방법에 대 한 자세한 내용은 [확인 요청](./requesting-confirmation-from-cmdlets.md)을 참조 하십시오.

## <a name="to-request-confirmation"></a>확인 요청

1. Cmdlet 특성의 `SupportsShouldProcess` 매개 변수가 `true`로 설정 되었는지 확인 합니다. 함수의 경우이는 CmdletBinding 특성의 매개 변수입니다.

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. 사용자가 확인 요청을 재정의할 수 있도록 cmdlet에 `Force` 매개 변수를 추가 합니다.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. [System.object의](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 반환 값을 사용 하는 `if` 문을 추가 하 여 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 하는지 여부를 확인 합니다 .이 메서드를 사용 합니다.

4. [System.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 의 반환 값을 사용 하 고 `Force` 매개 변수의 값을 사용 하 여 작업을 수행할지 여부를 결정 하는 두 번째 `if` 문을 추가 합니다.

## <a name="example"></a>예제

다음 코드 예제 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 및 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)는 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드에서 재정의하는 동안 호출됩니다. 그러나 다른 입력 처리 메서드에서 이러한 메서드를 호출할 수도 있습니다.

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
