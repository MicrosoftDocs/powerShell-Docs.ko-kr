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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067844"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="55834-102">확인을 요청하는 방법</span><span class="sxs-lookup"><span data-stu-id="55834-102">How to Request Confirmations</span></span>

<span data-ttu-id="55834-103">호출 하는 방법을 보여 주는이 예제는 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 하 고 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 에서 확인을 요청 하는 방법의 작업을 수행 하기 전에 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="55834-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="55834-104">Windows PowerShell에서 이러한 요청을 처리 하는 방법에 대 한 자세한 내용은 참조 하십시오 [요청 확인](./requesting-confirmation-from-cmdlets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="55834-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="55834-105">확인을 요청 하려면</span><span class="sxs-lookup"><span data-stu-id="55834-105">To request confirmation</span></span>

1. <span data-ttu-id="55834-106">있는지 확인 합니다 `SupportsShouldProcess` cmdlet은 특성의 매개 변수는 설정 `true`합니다.</span><span class="sxs-lookup"><span data-stu-id="55834-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="55834-107">(함수에 대 한 이것이 CmdletBinding 특성의 매개 변수입니다.)</span><span class="sxs-lookup"><span data-stu-id="55834-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="55834-108">추가 `Force` cmdlet 매개 변수는 사용자 확인 요청을 재정의할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="55834-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="55834-109">추가 `if` 의 반환 값을 사용 하는 문은 합니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 여부를 확인 하는 메서드는 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 메서드가 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55834-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="55834-110">추가 하 `if` 의 반환 값을 사용 하는 문은 합니다 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 메서드 및 값을 `Force` 작업 해야 하는지 여부를 확인 하려면 매개 변수 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="55834-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="55834-111">예제</span><span class="sxs-lookup"><span data-stu-id="55834-111">Example</span></span>

<span data-ttu-id="55834-112">다음 코드 예제에서는 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 하 고 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 메서드 재정의 내에서 호출 됩니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드.</span><span class="sxs-lookup"><span data-stu-id="55834-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="55834-113">그러나 다른 입력 처리 메서드에서에서 이러한 메서드를 호출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55834-113">However, you can also call these methods from the other input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="55834-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="55834-114">See Also</span></span>

<span data-ttu-id="55834-115">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="55834-115">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
