---
title: InitialSessionState 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: 9140d03e046def2fbbcc2a842b9ea1b9e1fa2985
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367622"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="da445-102">InitialSessionState 만들기</span><span class="sxs-lookup"><span data-stu-id="da445-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="da445-103">PowerShell 명령은 runspace에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="da445-103">PowerShell commands run in a runspace.</span></span>
<span data-ttu-id="da445-104">응용 프로그램에서 PowerShell을 호스트 하려면 [runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) 개체를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da445-104">To host PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>
<span data-ttu-id="da445-105">모든 runspace에는 [Runspace InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체가 연결 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da445-105">Every runspace has an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span>
<span data-ttu-id="da445-106">InitialSessionState는 runspace의 특성을 지정 합니다. 예를 들어 runspace에 사용할 수 있는 명령, 변수 및 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="da445-106">The InitialSessionState specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="da445-107">기본 InitialSessionState 만들기</span><span class="sxs-lookup"><span data-stu-id="da445-107">Create a default InitialSessionState</span></span>

<span data-ttu-id="da445-108">**InitialSessionState** 클래스의 [Createdefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) 및 [initialsessionstate.createdefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) 메서드를 사용 하 여 **InitialSessionState** 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da445-108">The [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) and [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods of the **InitialSessionState** class can be used to create an **InitialSessionState** object.</span></span>
<span data-ttu-id="da445-109">**Createdefault** 메서드는 모든 기본 제공 명령을 로드 하 여 **InitialSessionState** 을 만들지만 **initialsessionstate.createdefault2** 메서드는 PowerShell을 호스트 하는 데 필요한 명령만 로드 합니다. Microsoft. PowerShell. 핵심 모듈).</span><span class="sxs-lookup"><span data-stu-id="da445-109">The **CreateDefault** method creates an **InitialSessionState** with all of the built-in commands loaded, while the **CreateDefault2** method loads only the commands required to host PowerShell (the commands from the Microsoft.PowerShell.Core module).</span></span>

<span data-ttu-id="da445-110">호스트 응용 프로그램에서 사용할 수 있는 명령을 추가로 제한 하려면 제한 된 runspace를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da445-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span>
<span data-ttu-id="da445-111">자세한 내용은 [제한 된 Runspace 만들기](creating-a-constrained-runspace.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="da445-111">For information, see [Creating a constrained runspace](creating-a-constrained-runspace.md).</span></span>

<span data-ttu-id="da445-112">다음 코드에서는 **InitialSessionState**을 만들고 runspace에 할당 하 고 해당 runspace에서 파이프라인에 명령을 추가 하 고 명령을 호출 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="da445-112">The following code shows how to create an **InitialSessionState**, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span>
<span data-ttu-id="da445-113">명령 추가 및 호출에 대 한 자세한 내용은 [명령 추가 및 호출](adding-and-invoking-commands.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="da445-113">For more information about adding and invoking commands, see [Adding and invoking commands](adding-and-invoking-commands.md).</span></span>

```csharp
namespace SampleHost
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  class HostP4b
  {
    static void Main(string[] args)
    {
      // Call the InitialSessionState.CreateDefault method to create
      // an empty InitialSessionState object, and then add the
      // elements that will be available when the runspace is opened.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      SessionStateVariableEntry var1 = new
          SessionStateVariableEntry("test1",
                                    "MyVar1",
                                    "Initial session state MyVar1 test");
      iss.Variables.Add(var1);

      SessionStateVariableEntry var2 = new
          SessionStateVariableEntry("test2",
                                    "MyVar2",
                                    "Initial session state MyVar2 test");
      iss.Variables.Add(var2);

      // Call the RunspaceFactory.CreateRunspace(InitialSessionState)
      // method to create the runspace where the pipeline is run.
      Runspace rs = RunspaceFactory.CreateRunspace(iss);
      rs.Open();

      // Call the PowerShell.Create() method to create the PowerShell object,
      // and then specify the runspace and commands to the pipeline.
      // and create the command pipeline.
      PowerShell ps = PowerShell.Create();
      ps.Runspace = rs;
      ps.AddCommand("Get-Variable");
      ps.AddArgument("test*");

      Console.WriteLine("Variable             Value");
      Console.WriteLine("--------------------------");

      // Call the PowerShell.Invoke() method to run
      // the pipeline synchronously.
      foreach (PSObject result in ps.Invoke())
      {
        Console.WriteLine("{0,-20}{1}",
            result.Members["Name"].Value,
            result.Members["Value"].Value);
      } // End foreach.

      // Close the runspace to free resources.
      rs.Close();

    } // End Main.
  } // End SampleHost.
}
```

## <a name="see-also"></a><span data-ttu-id="da445-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="da445-114">See Also</span></span>

[<span data-ttu-id="da445-115">제한 된 runspace 만들기</span><span class="sxs-lookup"><span data-stu-id="da445-115">Creating a constrained runspace</span></span>](creating-a-constrained-runspace.md)

[<span data-ttu-id="da445-116">명령 추가 및 호출</span><span class="sxs-lookup"><span data-stu-id="da445-116">Adding and invoking commands</span></span>](adding-and-invoking-commands.md)
