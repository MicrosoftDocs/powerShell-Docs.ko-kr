---
title: Cmdlet 내에서 Cmdlet을 호출 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: d4564b51b74422cdaec3878b227ffc6be7c97949
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855889"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="e698b-102">Cmdlet 내에서 Cmdlet을 호출하는 방법</span><span class="sxs-lookup"><span data-stu-id="e698b-102">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="e698b-103">이 예제에서는 호출된 cmdlet의 기능을 개발 하는 cmdlet에 추가할 수 있는 다른 cmdlet 내에서 cmdlet을 호출 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e698b-103">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="e698b-104">이 예제는 `Get-Process` cmdlet은 로컬 컴퓨터에서 실행 되는 프로세스를 가져오려면 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e698b-104">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="e698b-105">에 대 한 호출을 `Get-Process` cmdlet은 다음 명령과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="e698b-105">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="e698b-106">이 명령은 이름이 "a"부터 "t" 문자로 시작 하는 모든 프로세스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e698b-106">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="e698b-107">직접 파생 되는 cmdlet에만 호출할 수 있습니다 합니다 [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="e698b-107">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="e698b-108">파생 되는 cmdlet를 호출할 수 없습니다는 [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="e698b-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="e698b-109">Cmdlet 내에서 cmdlet을 호출 하려면</span><span class="sxs-lookup"><span data-stu-id="e698b-109">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="e698b-110">Cmdlet이 호출을 정의 하는 어셈블리를 참조 하는지 확인 하 고 적절 한 `using` 문을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e698b-110">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="e698b-111">이 예제에서는 다음 네임 스페이스 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e698b-111">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="e698b-112">Cmdlet의 메서드를 처리 하는 입력을 호출할 cmdlet의 새 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e698b-112">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="e698b-113">이 예제에서는 형식의 개체로 [Microsoft.Powershell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) cmdlet 호출 될 때 사용 되는 인수를 포함 하는 문자열과 함께 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="e698b-113">In this example, an object of type [Microsoft.Powershell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="e698b-114">호출 된 [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 메서드를 호출 하는 `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e698b-114">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="e698b-115">예제</span><span class="sxs-lookup"><span data-stu-id="e698b-115">Example</span></span>

<span data-ttu-id="e698b-116">이 예는 `Get-Process` cmdlet 내에서 호출 되는 [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) cmdlet의 메서드.</span><span class="sxs-lookup"><span data-stu-id="e698b-116">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;   // Windows PowerShell assembly.
using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify an
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "GreetingInvoke")]
  public class SendGreetingInvokeCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the BeginProcessing method to invoke
    // the Get-Process cmdlet.
    protected override void BeginProcessing()
    {
      GetProcessCommand gp = new GetProcessCommand();
      gp.Name = new string[] { "[a-t]*" };
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="e698b-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e698b-117">See Also</span></span>

<span data-ttu-id="e698b-118">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="e698b-118">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
