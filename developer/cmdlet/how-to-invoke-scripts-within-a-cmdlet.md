---
title: Cmdlet 내에서 스크립트를 호출 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067878"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="9975a-102">Cmdlet 내에서 스크립트를 호출하는 방법</span><span class="sxs-lookup"><span data-stu-id="9975a-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="9975a-103">이 예제에서는 cmdlet에 제공 된 스크립트를 호출 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9975a-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="9975a-104">Cmdlet 스크립트를 실행 하 고 그 결과의 컬렉션으로 cmdlet에 반환 됩니다 [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="9975a-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="9975a-105">스크립트 블록을 호출 하려면</span><span class="sxs-lookup"><span data-stu-id="9975a-105">To invoke a script block</span></span>

1. <span data-ttu-id="9975a-106">명령은 스크립트 블록을 cmdlet에 제공 된 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9975a-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="9975a-107">스크립트 블록을 제공한 경우이 명령은 해당 필수 매개 변수를 사용 하 여 스크립트 블록을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="9975a-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. <span data-ttu-id="9975a-108">스크립트의 반환 된 컬렉션을 반복 하는 차례로 [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) 개체 및 필요한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9975a-108">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

    ```c
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a><span data-ttu-id="9975a-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9975a-109">See Also</span></span>

<span data-ttu-id="9975a-110">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="9975a-110">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
