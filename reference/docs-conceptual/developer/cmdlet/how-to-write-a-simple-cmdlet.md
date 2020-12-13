---
ms.date: 01/15/2019
ms.topic: reference
title: 간단한 Cmdlet을 작성하는 방법
description: 간단한 Cmdlet을 작성하는 방법
ms.openlocfilehash: 59dce5d797f80647e0b70a1f80faf67198652082
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646494"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="42b07-103">Cmdlet을 작성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="42b07-103">How to write a cmdlet</span></span>

<span data-ttu-id="42b07-104">이 문서에서는 cmdlet을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="42b07-104">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="42b07-105">`Send-Greeting`Cmdlet은 단일 사용자 이름을 입력으로 사용 하 고 해당 사용자에 게 인사말을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="42b07-105">The `Send-Greeting` cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="42b07-106">Cmdlet은 많은 작업을 수행 하지 않지만이 예에서는 cmdlet의 주요 섹션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="42b07-106">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="42b07-107">Cmdlet을 작성 하는 단계</span><span class="sxs-lookup"><span data-stu-id="42b07-107">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="42b07-108">클래스를 cmdlet으로 선언 하려면 **cmdlet** 특성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="42b07-108">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="42b07-109">**Cmdlet** 특성은 cmdlet 이름에 대 한 동사와 명사를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="42b07-109">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="42b07-110">**Cmdlet** 특성에 대 한 자세한 내용은 [cmdletattribute 선언](cmdlet-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42b07-110">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="42b07-111">클래스의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="42b07-111">Specify the name of the class.</span></span>

3. <span data-ttu-id="42b07-112">다음 클래스 중 하나에서 cmdlet이 파생 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="42b07-112">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="42b07-113">System.object.</span><span class="sxs-lookup"><span data-stu-id="42b07-113">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="42b07-114">PSCmdlet.</span><span class="sxs-lookup"><span data-stu-id="42b07-114">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="42b07-115">Cmdlet에 대 한 매개 변수를 정의 하려면 **매개 변수** 특성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="42b07-115">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="42b07-116">이 경우 필수 매개 변수를 하나만 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="42b07-116">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="42b07-117">**Parameter** 특성에 대 한 자세한 내용은 [parameterattribute 선언](parameter-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42b07-117">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="42b07-118">입력을 처리 하는 입력 처리 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="42b07-118">Override the input processing method that processes the input.</span></span> <span data-ttu-id="42b07-119">이 경우에는 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드가 재정의 되 고,</span><span class="sxs-lookup"><span data-stu-id="42b07-119">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="42b07-120">인사말을 작성 하려면 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="42b07-120">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="42b07-121">인사말이 다음과 같은 형식으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42b07-121">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="42b07-122">예제</span><span class="sxs-lookup"><span data-stu-id="42b07-122">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="42b07-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="42b07-123">See also</span></span>

[<span data-ttu-id="42b07-124">System.object.</span><span class="sxs-lookup"><span data-stu-id="42b07-124">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="42b07-125">PSCmdlet.</span><span class="sxs-lookup"><span data-stu-id="42b07-125">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="42b07-126">ProcessRecord입니다.</span><span class="sxs-lookup"><span data-stu-id="42b07-126">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="42b07-127">WriteObject입니다.</span><span class="sxs-lookup"><span data-stu-id="42b07-127">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="42b07-128">CmdletAttribute 선언</span><span class="sxs-lookup"><span data-stu-id="42b07-128">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="42b07-129">ParameterAttribute 선언</span><span class="sxs-lookup"><span data-stu-id="42b07-129">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

<span data-ttu-id="42b07-130">[Writing a Windows PowerShell Cmdlet](writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="42b07-130">[Writing a Windows PowerShell Cmdlet](writing-a-windows-powershell-cmdlet.md)</span></span>
