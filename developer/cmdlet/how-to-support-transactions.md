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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067861"
---
# <a name="how-to-support-transactions"></a>트랜잭션을 지원하는 방법

이 예제에서는 cmdlet에 트랜잭션에 대 한 지원을 추가 하는 기본 코드 요소를 보여 줍니다.

> [!IMPORTANT]
> Windows PowerShell에서 트랜잭션을 처리 하는 방법에 대 한 자세한 내용은 참조 하세요. [에 대 한 트랜잭션을][about_Transactions]합니다.

## <a name="to-support-transactions"></a>트랜잭션을 지원 하도록

1. Cmdlet 특성을 선언 하는 경우 cmdlet에서 트랜잭션을 지원 하도록 지정 합니다.
   Windows PowerShell cmdlet에서 트랜잭션을 지원 하는 경우 추가 `UseTransaction` 를 실행 하는 경우 cmdlet 매개 변수입니다.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. 입력 처리 메서드 중 하나를 추가 `if` 블록을 트랜잭션에 사용할 수 있는지 확인 합니다.
   경우는 `if` 문을 확인 `true`을 현재 트랜잭션의 컨텍스트 내에서이 문 내에서 작업을 수행할 수 있습니다.

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
