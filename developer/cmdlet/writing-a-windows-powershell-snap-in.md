---
title: Windows PowerShell 스냅인 작성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.assetid: 875024f4-e02b-4416-80b9-af5e5b50aad6
caps.latest.revision: 7
ms.openlocfilehash: 465ab9e8fa29716ce0f46ad0dcf01d0ddd615bcd
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322931"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="92de7-102">Windows PowerShell 스냅인 작성</span><span class="sxs-lookup"><span data-stu-id="92de7-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="92de7-103">이 예제에서는 어셈블리의 모든 cmdlet 및 Windows PowerShell 공급자를 등록 하는 데 사용할 수 있는 Windows PowerShell 스냅인을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="92de7-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="92de7-104">이 유형의 스냅인을 사용 하 여 등록 하려는 cmdlet 및 공급자를 선택 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92de7-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="92de7-105">등록 된 항목을 선택할 수 있는 스냅인을 작성 하려면 [사용자 지정 Windows PowerShell 스냅인 작성](./writing-a-custom-windows-powershell-snap-in.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="92de7-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="92de7-106">Windows PowerShell 스냅인 작성</span><span class="sxs-lookup"><span data-stu-id="92de7-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="92de7-107">RunInstallerAttribute 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="92de7-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="92de7-108">[Add-pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) 클래스에서 파생 되는 공용 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="92de7-108">Create a public class that derives from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="92de7-109">이 예제에서 클래스 이름은 "GetProcPSSnapIn01"입니다.</span><span class="sxs-lookup"><span data-stu-id="92de7-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="92de7-110">스냅인 이름에 대 한 public 속성 (필수)을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="92de7-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="92de7-111">스냅인의 이름을 지정할 때 # 문자를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="92de7-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="92de7-112">, () {} [] &AMP;-/\ $; : "' \< >;?</span><span class="sxs-lookup"><span data-stu-id="92de7-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="92de7-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="92de7-113">@ \` \*</span></span>

    <span data-ttu-id="92de7-114">이 예제에서 스냅인의 이름은 "GetProcPSSnapIn01"입니다.</span><span class="sxs-lookup"><span data-stu-id="92de7-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="92de7-115">스냅인 공급 업체에 대 한 공용 속성 (필수)을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="92de7-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="92de7-116">이 예제에서 공급 업체는 "Microsoft"입니다.</span><span class="sxs-lookup"><span data-stu-id="92de7-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="92de7-117">스냅인의 공급 업체 리소스에 대 한 공용 속성을 추가 합니다 (선택 사항).</span><span class="sxs-lookup"><span data-stu-id="92de7-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="92de7-118">이 예제에서 공급 업체 리소스는 "GetProcPSSnapIn01, Microsoft"입니다.</span><span class="sxs-lookup"><span data-stu-id="92de7-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="92de7-119">스냅인에 대 한 설명에 대 한 public 속성 (필수)을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="92de7-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="92de7-120">이 예제에서 설명은 "This is the Windows PowerShell 스냅인은 get proc cmdlet을 등록 합니다."입니다.</span><span class="sxs-lookup"><span data-stu-id="92de7-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="92de7-121">스냅인의 설명 리소스에 대 한 public 속성을 추가 합니다 (선택 사항).</span><span class="sxs-lookup"><span data-stu-id="92de7-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="92de7-122">이 예제에서 공급 업체 리소스는 "GetProcPSSnapIn01" 이며,이는 get proc cmdlet을 등록 하는 Windows PowerShell 스냅인입니다.</span><span class="sxs-lookup"><span data-stu-id="92de7-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="92de7-123">예제</span><span class="sxs-lookup"><span data-stu-id="92de7-123">Example</span></span>

<span data-ttu-id="92de7-124">이 예제에서는 Windows PowerShell 셸에서 Get Proc cmdlet을 등록 하는 데 사용할 수 있는 Windows PowerShell 스냅인을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="92de7-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="92de7-125">이 예제에서 전체 어셈블리에는 GetProcPSSnapIn01 스냅인 클래스와 Get Proc cmdlet 클래스만 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92de7-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="92de7-126">관련 항목</span><span class="sxs-lookup"><span data-stu-id="92de7-126">See Also</span></span>

[<span data-ttu-id="92de7-127">Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법</span><span class="sxs-lookup"><span data-stu-id="92de7-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="92de7-128">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="92de7-128">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
