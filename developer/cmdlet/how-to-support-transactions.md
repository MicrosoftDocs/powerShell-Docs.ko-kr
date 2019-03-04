---
title: 트랜잭션을 지원 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4732e38c-b1a0-4de7-b6de-75dbde850488
caps.latest.revision: 8
ms.openlocfilehash: c5eea216efd8048aee5768c78c0b48617670f091
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857119"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="b919a-102">트랜잭션을 지원하는 방법</span><span class="sxs-lookup"><span data-stu-id="b919a-102">How to Support Transactions</span></span>

<span data-ttu-id="b919a-103">이 예제에서는 cmdlet에 트랜잭션에 대 한 지원을 추가 하는 기본 코드 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b919a-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b919a-104">Windows PowerShell에서 트랜잭션을 처리 하는 방법에 대 한 자세한 내용은 참조 하세요. [에 대 한 트랜잭션을][about_Transactions]합니다.</span><span class="sxs-lookup"><span data-stu-id="b919a-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="b919a-105">트랜잭션을 지원 하도록</span><span class="sxs-lookup"><span data-stu-id="b919a-105">To support transactions</span></span>

1. <span data-ttu-id="b919a-106">Cmdlet 특성을 선언 하는 경우 cmdlet에서 트랜잭션을 지원 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b919a-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="b919a-107">Windows PowerShell cmdlet에서 트랜잭션을 지원 하는 경우 추가 `UseTransaction` 를 실행 하는 경우 cmdlet 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b919a-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="b919a-108">입력 처리 메서드 중 하나를 추가 `if` 블록을 트랜잭션에 사용할 수 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b919a-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="b919a-109">경우는 `if` 문을 확인 `true`을 현재 트랜잭션의 컨텍스트 내에서이 문 내에서 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b919a-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="b919a-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b919a-110">See Also</span></span>

<span data-ttu-id="b919a-111">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="b919a-111">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
