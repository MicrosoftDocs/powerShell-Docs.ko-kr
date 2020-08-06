---
title: Cmdlet에서 Cmdlet을 호출 하는 방법 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2d5b0788d3310d0dd7b311f86c497afe8eec9d11
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784149"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="36638-102">Cmdlet 내에서 Cmdlet을 호출하는 방법</span><span class="sxs-lookup"><span data-stu-id="36638-102">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="36638-103">이 예에서는 다른 cmdlet 내에서 cmdlet을 호출 하는 방법을 보여 줍니다 .이 cmdlet을 사용 하면 호출 되는 cmdlet의 기능을 개발 중인 cmdlet에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36638-103">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="36638-104">이 예제에서는 cmdlet을 `Get-Process` 호출 하 여 로컬 컴퓨터에서 실행 중인 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="36638-104">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="36638-105">Cmdlet에 대 한 호출은 `Get-Process` 다음 명령과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="36638-105">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="36638-106">이 명령은 이름이 "a"에서 "t" 까지의 문자로 시작 하는 모든 프로세스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="36638-106">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="36638-107">[System.object](/dotnet/api/System.Management.Automation.Cmdlet) 클래스에서 직접 파생 되는 cmdlet만 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36638-107">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="36638-108">[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 클래스에서 파생 된 cmdlet을 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36638-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="36638-109">Cmdlet에서 cmdlet을 호출 하려면</span><span class="sxs-lookup"><span data-stu-id="36638-109">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="36638-110">호출할 cmdlet을 정의 하는 어셈블리가 참조 되 고 적절 한 `using` 문이 추가 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="36638-110">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="36638-111">이 예제에서는 다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="36638-111">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="36638-112">Cmdlet의 입력 처리 메서드에서 호출할 cmdlet의 새 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="36638-112">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="36638-113">이 예제에서는 cmdlet을 호출할 때 사용 되는 인수를 포함 하는 문자열과 함께 [Microsoft. PowerShell. Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) 형식의 개체가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36638-113">In this example, an object of type [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="36638-114">Cmdlet을 호출 하려면 [system.web. invoke \*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 메서드를 호출 합니다. `Get-Process`</span><span class="sxs-lookup"><span data-stu-id="36638-114">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="36638-115">예제</span><span class="sxs-lookup"><span data-stu-id="36638-115">Example</span></span>

<span data-ttu-id="36638-116">이 예제에서 cmdlet은 `Get-Process` cmdlet의 system.object를 실행 하는 [프로세스](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 에서 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36638-116">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="36638-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="36638-117">See Also</span></span>

[<span data-ttu-id="36638-118">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="36638-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
