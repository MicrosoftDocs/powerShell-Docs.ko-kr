---
title: Windows PowerShell 스냅인에서 쓰기 | Microsoft Docs
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
ms.openlocfilehash: 0c99f4bcfe5e2d34d31714dc85a53b5e8abe0925
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057793"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="5800f-102">Windows PowerShell 스냅인 작성</span><span class="sxs-lookup"><span data-stu-id="5800f-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="5800f-103">이 예제에서는 Windows PowerShell 스냅인에서 어셈블리의 모든 cmdlet 및 Windows PowerShell 공급자를 등록 하는 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="5800f-104">이 유형의 스냅인을 선택 하지 않으면는 cmdlet 및 공급자를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="5800f-105">등록 된 항목을 선택할 수 있는 스냅인 쓸 참조 [사용자 지정 Windows PowerShell 스냅인 작성](./writing-a-custom-windows-powershell-snap-in.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="5800f-106">Windows PowerShell 스냅인 작성</span><span class="sxs-lookup"><span data-stu-id="5800f-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="5800f-107">RunInstallerAttribute 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="5800f-108">파생 되는 공용 클래스를 만들어야 합니다 [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-108">Create a public class that derives from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="5800f-109">이 예제에서는 클래스 이름은 "GetProcPSSnapIn01"입니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="5800f-110">(필수) 스냅인의 이름에 대 한 공용 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="5800f-111">스냅인 이름을 지정 하는 경우 사용 하지 마십시오는 다음 문자: # 합니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="5800f-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span><span class="sxs-lookup"><span data-stu-id="5800f-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="5800f-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="5800f-113">@ \` \*</span></span>

    <span data-ttu-id="5800f-114">이 예제에서는 스냅인 이름이 "GetProcPSSnapIn01"입니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="5800f-115">(필수) 스냅인의 공급 업체에 대 한 공용 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="5800f-116">이 예제에서는 공급 업체는 "Microsoft"입니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="5800f-117">(선택 사항) 스냅인의 공급 업체 리소스에 대 한 공용 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="5800f-118">이 예제에서는 공급 업체 리소스가 "GetProcPSSnapIn01, Microsoft"입니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="5800f-119">(필수) 스냅인의 설명에 대 한 공용 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="5800f-120">이 예의 설명은 "This is get-proc cmdlet을 등록 하는 Windows PowerShell 스냅인"입니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="5800f-121">(선택 사항) 스냅인의 설명 리소스에 대 한 공용 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="5800f-122">이 예제에서는 공급 업체 리소스가 "GetProcPSSnapIn01,이 get-proc cmdlet을 등록 하는 Windows PowerShell 스냅인"입니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="5800f-123">예제</span><span class="sxs-lookup"><span data-stu-id="5800f-123">Example</span></span>

<span data-ttu-id="5800f-124">이 예제에서는 Windows PowerShell 스냅인을 Windows PowerShell 셸에 Get-proc cmdlet을 등록 하는 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="5800f-125">이 예제에서는 전체 어셈블리는 포함 된 GetProcPSSnapIn01 스냅인 클래스 및는 Get-proc cmdlet 클래스에 유의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5800f-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5800f-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5800f-126">See Also</span></span>

[<span data-ttu-id="5800f-127">Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법</span><span class="sxs-lookup"><span data-stu-id="5800f-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="5800f-128">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="5800f-128">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
