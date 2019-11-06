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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369682"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="fefb9-102">확인을 요청하는 방법</span><span class="sxs-lookup"><span data-stu-id="fefb9-102">How to Request Confirmations</span></span>

<span data-ttu-id="fefb9-103">이 예제에서는 작업을 수행 하기 전에 사용자의 확인을 요청 하는 데 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 및 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fefb9-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fefb9-104">Windows PowerShell에서 이러한 요청을 처리 하는 방법에 대 한 자세한 내용은 [확인 요청](./requesting-confirmation-from-cmdlets.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fefb9-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="fefb9-105">확인 요청</span><span class="sxs-lookup"><span data-stu-id="fefb9-105">To request confirmation</span></span>

1. <span data-ttu-id="fefb9-106">Cmdlet 특성의 `SupportsShouldProcess` 매개 변수가 `true`로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fefb9-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="fefb9-107">함수의 경우이는 CmdletBinding 특성의 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="fefb9-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="fefb9-108">사용자가 확인 요청을 재정의할 수 있도록 cmdlet에 `Force` 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fefb9-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="fefb9-109">[System.object의](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 반환 값을 사용 하는 `if` 문을 추가 하 여 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 하는지 여부를 확인 합니다 .이 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fefb9-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="fefb9-110">[System.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 의 반환 값을 사용 하 고 `Force` 매개 변수의 값을 사용 하 여 작업을 수행할지 여부를 결정 하는 두 번째 `if` 문을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fefb9-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="fefb9-111">예제</span><span class="sxs-lookup"><span data-stu-id="fefb9-111">Example</span></span>

<span data-ttu-id="fefb9-112">다음 코드 예제 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 및 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)는 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드에서 재정의하는 동안 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="fefb9-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="fefb9-113">그러나 다른 입력 처리 메서드에서 이러한 메서드를 호출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fefb9-113">However, you can also call these methods from the other input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fefb9-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fefb9-114">See Also</span></span>

<span data-ttu-id="fefb9-115">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="fefb9-115">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
