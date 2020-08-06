---
title: 트랜잭션 지원 방법 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6fda27394091195b589afef5ee53c6d3bec4efc0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786614"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="48109-102">트랜잭션을 지원하는 방법</span><span class="sxs-lookup"><span data-stu-id="48109-102">How to Support Transactions</span></span>

<span data-ttu-id="48109-103">이 예제에서는 cmdlet에 대 한 트랜잭션에 대 한 지원을 추가 하는 기본 코드 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="48109-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="48109-104">Windows PowerShell에서 트랜잭션을 처리 하는 방법에 대 한 자세한 내용은 [트랜잭션 정보][about_Transactions]를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="48109-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="48109-105">트랜잭션을 지원 하려면</span><span class="sxs-lookup"><span data-stu-id="48109-105">To support transactions</span></span>

1. <span data-ttu-id="48109-106">Cmdlet 특성을 선언 하는 경우 cmdlet이 트랜잭션을 지원 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="48109-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="48109-107">Cmdlet이 트랜잭션을 지원할 때 Windows PowerShell은 cmdlet을 `UseTransaction` 실행할 때 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="48109-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="48109-108">입력 처리 방법 중 하나에서 블록을 추가 `if` 하 여 트랜잭션을 사용할 수 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="48109-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="48109-109">`if`문이로 확인 되 면 `true` 현재 트랜잭션의 컨텍스트 내에서이 문 내의 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48109-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="48109-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="48109-110">See Also</span></span>

[<span data-ttu-id="48109-111">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="48109-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
