---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 스냅인 작성
description: Windows PowerShell 스냅인 작성
ms.openlocfilehash: f658c2fa1211bfb77d2e8edd3999ce7f92df13bb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659449"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="58e0f-103">Windows PowerShell 스냅인 작성</span><span class="sxs-lookup"><span data-stu-id="58e0f-103">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="58e0f-104">이 예제에서는 어셈블리의 모든 cmdlet 및 Windows PowerShell 공급자를 등록 하는 데 사용할 수 있는 Windows PowerShell 스냅인을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="58e0f-104">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="58e0f-105">이 유형의 스냅인을 사용 하 여 등록 하려는 cmdlet 및 공급자를 선택 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="58e0f-105">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="58e0f-106">등록 된 항목을 선택할 수 있는 스냅인을 작성 하려면 [사용자 지정 Windows PowerShell 스냅인 작성](./writing-a-custom-windows-powershell-snap-in.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="58e0f-106">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="58e0f-107">Windows PowerShell 스냅인 작성</span><span class="sxs-lookup"><span data-stu-id="58e0f-107">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="58e0f-108">RunInstallerAttribute 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="58e0f-108">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="58e0f-109">[Add-pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) 클래스에서 파생 되는 공용 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="58e0f-109">Create a public class that derives from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="58e0f-110">이 예제에서 클래스 이름은 "GetProcPSSnapIn01"입니다.</span><span class="sxs-lookup"><span data-stu-id="58e0f-110">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="58e0f-111">스냅인 이름에 대 한 public 속성 (필수)을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="58e0f-111">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="58e0f-112">스냅인의 이름을 지정할 때,,,,,,,,,,,,,,,,,,,,,,,, 등의 문자를 사용 하지 마십시오. `#` `.` `,` `(` `)` `{` `}` `[` `]` `&` `-` `/` `\` `$` `;` `:` `"` `'` `<` `>` `|` `?` `@` \`\` ` ```*`</span><span class="sxs-lookup"><span data-stu-id="58e0f-112">When naming snap-ins, do not use any of the following characters: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@`, `` ` ``, `*`</span></span>

    <span data-ttu-id="58e0f-113">이 예제에서 스냅인의 이름은 "GetProcPSSnapIn01"입니다.</span><span class="sxs-lookup"><span data-stu-id="58e0f-113">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="58e0f-114">스냅인 공급 업체에 대 한 공용 속성 (필수)을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="58e0f-114">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="58e0f-115">이 예제에서 공급 업체는 "Microsoft"입니다.</span><span class="sxs-lookup"><span data-stu-id="58e0f-115">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="58e0f-116">스냅인의 공급 업체 리소스에 대 한 공용 속성을 추가 합니다 (선택 사항).</span><span class="sxs-lookup"><span data-stu-id="58e0f-116">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="58e0f-117">이 예제에서 공급 업체 리소스는 "GetProcPSSnapIn01, Microsoft"입니다.</span><span class="sxs-lookup"><span data-stu-id="58e0f-117">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="58e0f-118">스냅인에 대 한 설명에 대 한 public 속성 (필수)을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="58e0f-118">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="58e0f-119">이 예제에서 설명은 "This is the Windows PowerShell 스냅인은 get proc cmdlet을 등록 합니다."입니다.</span><span class="sxs-lookup"><span data-stu-id="58e0f-119">In this example, the description is "This is a Windows PowerShell snap-in that registers the  get-proc cmdlet".</span></span>

7. <span data-ttu-id="58e0f-120">스냅인의 설명 리소스에 대 한 public 속성을 추가 합니다 (선택 사항).</span><span class="sxs-lookup"><span data-stu-id="58e0f-120">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="58e0f-121">이 예제에서 공급 업체 리소스는 "GetProcPSSnapIn01" 이며,이는 get proc cmdlet을 등록 하는 Windows PowerShell 스냅인입니다.</span><span class="sxs-lookup"><span data-stu-id="58e0f-121">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in  that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="58e0f-122">예제</span><span class="sxs-lookup"><span data-stu-id="58e0f-122">Example</span></span>

<span data-ttu-id="58e0f-123">이 예제에서는 Windows powershell 셸에서 Get-Proc cmdlet을 등록 하는 데 사용할 수 있는 Windows PowerShell 스냅인을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="58e0f-123">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="58e0f-124">이 예제에서 전체 어셈블리는 GetProcPSSnapIn01 스냅인 클래스와 `Get-Proc` cmdlet 클래스만 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="58e0f-124">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the `Get-Proc` cmdlet class.</span></span>

```csharp
[RunInstaller(true)]
public class GetProcPSSnapIn01 : PSSnapIn
{
  /// <summary>
  /// Create an instance of the GetProcPSSnapIn01 class.
  /// </summary>
  public GetProcPSSnapIn01()
         : base()
  {
  }

  /// <summary>
  /// Specify the name of the PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "GetProcPSSnapIn01";
    }
  }

  /// <summary>
  /// Specify the vendor for the PowerShell snap-in.
  /// </summary>
  public override string Vendor
  {
    get
    {
      return "Microsoft";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the vendor.
  /// Use the format: resourceBaseName,VendorName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
      return "GetProcPSSnapIn01,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the description.
  /// Use the format: resourceBaseName,Description.
  /// </summary>
  public override string DescriptionResource
  {
    get
    {
      return "GetProcPSSnapIn01,This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="58e0f-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="58e0f-125">See Also</span></span>

<span data-ttu-id="58e0f-126">[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="58e0f-126">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="58e0f-127">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="58e0f-127">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
