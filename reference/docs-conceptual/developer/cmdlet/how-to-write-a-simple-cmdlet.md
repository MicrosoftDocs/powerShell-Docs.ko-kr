---
title: 간단한 Cmdlet을 작성 하는 방법 | Microsoft Docs
ms.date: 01/15/2019
ms.openlocfilehash: 2ff0b47454804c9becd6f03ac521946b9596bb8b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784064"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="d36f4-102">Cmdlet을 작성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d36f4-102">How to write a cmdlet</span></span>

<span data-ttu-id="d36f4-103">이 문서에서는 cmdlet을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d36f4-103">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="d36f4-104">`Send-Greeting`Cmdlet은 단일 사용자 이름을 입력으로 사용 하 고 해당 사용자에 게 인사말을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="d36f4-104">The `Send-Greeting` cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="d36f4-105">Cmdlet은 많은 작업을 수행 하지 않지만이 예에서는 cmdlet의 주요 섹션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d36f4-105">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="d36f4-106">Cmdlet을 작성 하는 단계</span><span class="sxs-lookup"><span data-stu-id="d36f4-106">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="d36f4-107">클래스를 cmdlet으로 선언 하려면 **cmdlet** 특성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d36f4-107">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="d36f4-108">**Cmdlet** 특성은 cmdlet 이름에 대 한 동사와 명사를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d36f4-108">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="d36f4-109">**Cmdlet** 특성에 대 한 자세한 내용은 [cmdletattribute 선언](cmdlet-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d36f4-109">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="d36f4-110">클래스의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d36f4-110">Specify the name of the class.</span></span>

3. <span data-ttu-id="d36f4-111">다음 클래스 중 하나에서 cmdlet이 파생 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d36f4-111">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="d36f4-112">System.object.</span><span class="sxs-lookup"><span data-stu-id="d36f4-112">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="d36f4-113">PSCmdlet.</span><span class="sxs-lookup"><span data-stu-id="d36f4-113">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="d36f4-114">Cmdlet에 대 한 매개 변수를 정의 하려면 **매개 변수** 특성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d36f4-114">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="d36f4-115">이 경우 필수 매개 변수를 하나만 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d36f4-115">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="d36f4-116">**Parameter** 특성에 대 한 자세한 내용은 [parameterattribute 선언](parameter-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d36f4-116">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="d36f4-117">입력을 처리 하는 입력 처리 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d36f4-117">Override the input processing method that processes the input.</span></span> <span data-ttu-id="d36f4-118">이 경우에는 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드가 재정의 되 고,</span><span class="sxs-lookup"><span data-stu-id="d36f4-118">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="d36f4-119">인사말을 작성 하려면 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d36f4-119">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="d36f4-120">인사말이 다음과 같은 형식으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d36f4-120">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="d36f4-121">예제</span><span class="sxs-lookup"><span data-stu-id="d36f4-121">Example</span></span>

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify the
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

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

## <a name="see-also"></a><span data-ttu-id="d36f4-122">참조</span><span class="sxs-lookup"><span data-stu-id="d36f4-122">See also</span></span>

[<span data-ttu-id="d36f4-123">System.object.</span><span class="sxs-lookup"><span data-stu-id="d36f4-123">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="d36f4-124">PSCmdlet.</span><span class="sxs-lookup"><span data-stu-id="d36f4-124">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="d36f4-125">ProcessRecord입니다.</span><span class="sxs-lookup"><span data-stu-id="d36f4-125">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="d36f4-126">WriteObject입니다.</span><span class="sxs-lookup"><span data-stu-id="d36f4-126">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="d36f4-127">CmdletAttribute 선언</span><span class="sxs-lookup"><span data-stu-id="d36f4-127">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="d36f4-128">ParameterAttribute 선언</span><span class="sxs-lookup"><span data-stu-id="d36f4-128">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="d36f4-129">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="d36f4-129">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)
