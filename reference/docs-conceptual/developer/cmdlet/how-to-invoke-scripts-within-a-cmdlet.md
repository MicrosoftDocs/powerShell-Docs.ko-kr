---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 내에서 스크립트를 호출하는 방법
description: Cmdlet 내에서 스크립트를 호출하는 방법
ms.openlocfilehash: f4a43a1e1240854e57deac5721e1e070c1a45a51
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667031"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="b4c90-103">Cmdlet 내에서 스크립트를 호출하는 방법</span><span class="sxs-lookup"><span data-stu-id="b4c90-103">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="b4c90-104">이 예제에서는 cmdlet에 제공 된 스크립트를 호출 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b4c90-104">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="b4c90-105">이 스크립트는 cmdlet에 의해 실행 되며 해당 결과는 cmdlet에 [system.object](/dotnet/api/System.Management.Automation.PSObject) 로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4c90-105">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="b4c90-106">스크립트 블록을 호출 하려면</span><span class="sxs-lookup"><span data-stu-id="b4c90-106">To invoke a script block</span></span>

1. <span data-ttu-id="b4c90-107">명령은 스크립트 블록이 cmdlet에 제공 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c90-107">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="b4c90-108">스크립트 블록을 제공한 경우 명령은 필요한 매개 변수를 사용 하 여 스크립트 블록을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c90-108">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

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

2. <span data-ttu-id="b4c90-109">그런 다음 스크립트는 [system.object](/dotnet/api/System.Management.Automation.PSObject) 의 반환 된 컬렉션을 반복 하 여 필요한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c90-109">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b4c90-110">관련 항목</span><span class="sxs-lookup"><span data-stu-id="b4c90-110">See Also</span></span>

[<span data-ttu-id="b4c90-111">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="b4c90-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
