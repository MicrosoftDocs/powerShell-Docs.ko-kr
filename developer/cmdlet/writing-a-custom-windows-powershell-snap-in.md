---
title: 사용자 지정 Windows PowerShell 스냅인에서 쓰기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], custom PSSnapin example
- cmdlets [PowerShell SDK], specified in snap-ins
ms.assetid: 55c8b5cb-8ee2-4080-afc4-3f09c9f20128
caps.latest.revision: 6
ms.openlocfilehash: 4d50ef4dcd75d5c0ba802fbcfe2d7d1d7c954707
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795592"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="404d3-102">사용자 지정 Windows PowerShell 스냅인 작성</span><span class="sxs-lookup"><span data-stu-id="404d3-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="404d3-103">이 예제에서는 특정 cmdlet을 등록 하는 Windows PowerShell 스냅인 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="404d3-104">스냅인의 형식과이 cmdlet, 공급자, 형식 또는 형식 등록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="404d3-105">어셈블리의 모든 cmdlet 및 공급자를 등록 하는 스냅인 작성 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 스냅인 작성](./writing-a-windows-powershell-snap-in.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="404d3-106">Windows PowerShell 스냅인을 작성 하는 특정 cmdlet를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="404d3-107">RunInstallerAttribute 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="404d3-108">파생 되는 공용 클래스를 만들어야 합니다 [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="404d3-109">이 예제에서는 클래스 이름은 "CustomPSSnapinTest"입니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="404d3-110">(필수) 스냅인의 이름에 대 한 공용 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="404d3-111">스냅인 이름을 지정 하는 경우 사용 하지 마십시오는 다음 문자: # 합니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="404d3-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span><span class="sxs-lookup"><span data-stu-id="404d3-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span></span> <span data-ttu-id="404d3-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="404d3-113">@ \` \*</span></span>

   <span data-ttu-id="404d3-114">이 예제에서는 스냅인 이름이 "CustomPSSnapInTest"입니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-114">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="404d3-115">(필수) 스냅인의 공급 업체에 대 한 공용 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-115">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="404d3-116">이 예제에서는 공급 업체는 "Microsoft"입니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="404d3-117">(선택 사항) 스냅인의 공급 업체 리소스에 대 한 공용 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="404d3-118">이 예제에서는 공급 업체 리소스가 "CustomPSSnapInTest, Microsoft"입니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-118">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="404d3-119">(필수) 스냅인의 설명에 대 한 공용 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-119">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="404d3-120">이 예제에서는 설명은 다음과 같습니다. "This is 사용자 지정 Windows PowerShell 스냅인에서 HelloWorld 테스트 및 테스트 CustomSnapinTest cmdlet을 포함 하는".</span><span class="sxs-lookup"><span data-stu-id="404d3-120">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

7. <span data-ttu-id="404d3-121">(선택 사항) 스냅인의 설명 리소스에 대 한 공용 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-121">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="404d3-122">이 예제에서는 공급 업체 리소스가 "CustomPSSnapInTest,이 사용자 지정 Windows PowerShell 스냅인에서 HelloWorld 테스트 및 테스트 CustomSnapinTest cmdlet이 포함 된"입니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-122">In this example, the vendor resource is "CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="404d3-123">사용자 지정 스냅인 (선택 사항) 사용 하 여 속하는 cmdlet은 지정 된 [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-123">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="404d3-124">여기에 추가 정보에는 cmdlet, 해당.NET 형식 및 cmdlet 도움말 파일 이름 (cmdlet 도움말 파일 이름 형식의 되었거나 name.dll help.xml 이어야 함)의 이름을 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-124">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be name.dll-help.xml).</span></span>

   <span data-ttu-id="404d3-125">이 예제에서는 테스트 HelloWorld 및 TestCustomSnapinTest cmdlet을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-125">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="404d3-126">사용자 지정 스냅인 (선택 사항)에 속해 있는 공급자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-126">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="404d3-127">이 예제에서는 모든 공급자를 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-127">This example does not specify any providers.</span></span>

10. <span data-ttu-id="404d3-128">사용자 지정 스냅인 (선택 사항)에 속해 있는 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-128">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="404d3-129">이 예제에서는 모든 형식을 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-129">This example does not specify any types.</span></span>

11. <span data-ttu-id="404d3-130">사용자 지정 스냅인 (선택 사항)에 속하는 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-130">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="404d3-131">이 예제에서는 모든 형식 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-131">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="404d3-132">예제</span><span class="sxs-lookup"><span data-stu-id="404d3-132">Example</span></span>

<span data-ttu-id="404d3-133">이 예제에서는 사용자 지정 Windows PowerShell 스냅인에서 HelloWorld 테스트 및 테스트 CustomSnapinTest cmdlet을 등록 하는 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-133">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the Test-HelloWorld and Test-CustomSnapinTest cmdlets.</span></span> <span data-ttu-id="404d3-134">이 예제에서는 완전 한 어셈블리를 포함할 수 있습니다 다른 cmdlet와 공급자가 스냅인에서 등록 하지는 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-134">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

```csharp
[RunInstaller(true)]
public class CustomPSSnapinTest : CustomPSSnapIn
{
  /// <summary>
  /// Creates an instance of CustomPSSnapInTest class.
  /// </summary>
  public CustomPSSnapinTest()
          : base()
  {
  }

  /// <summary>
  /// Specify the name of the custom PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "CustomPSSnapInTest";
    }
  }

  /// <summary>
  /// Specify the vendor for the custom PowerShell snap-in.
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
  /// Use the format: resourceBaseName,resourceName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
        return "CustomPSSnapInTest,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the custom PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
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
        return "CustomPSSnapInTest,This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the cmdlets that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<CmdletConfigurationEntry> _cmdlets;
  public override Collection<CmdletConfigurationEntry> Cmdlets
  {
    get
    {
      if (_cmdlets == null)
      {
        _cmdlets = new Collection<CmdletConfigurationEntry>();
        _cmdlets.Add(new CmdletConfigurationEntry("test-customsnapintest", typeof(TestCustomSnapinTest), "TestCmdletHelp.dll-help.xml"));
        _cmdlets.Add(new CmdletConfigurationEntry("test-helloworld", typeof(TestHelloWorld), "HelloWorldHelp.dll-help.xml"));
      }

      return _cmdlets;
    }
  }

  /// <summary>
  /// Specify the providers that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<ProviderConfigurationEntry> _providers;
  public override Collection<ProviderConfigurationEntry> Providers
  {
    get
    {
      if (_providers == null)
      {
        _providers = new Collection<ProviderConfigurationEntry>();
      }

      return _providers;
    }
  }

  /// <summary>
  /// Specify the types that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<TypeConfigurationEntry> _types;
  public override Collection<TypeConfigurationEntry> Types
  {
    get
    {
      if (_types == null)
      {
        _types = new Collection<TypeConfigurationEntry>();
      }

      return _types;
    }
  }

  /// <summary>
  /// Specify the formats that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<FormatConfigurationEntry> _formats;
  public override Collection<FormatConfigurationEntry> Formats
  {
    get
    {
      if (_formats == null)
      {
        _formats = new Collection<FormatConfigurationEntry>();
      }

      return _formats;
    }
  }
}
```

<span data-ttu-id="404d3-135">스냅인을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) 에 [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="404d3-135">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="404d3-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="404d3-136">See Also</span></span>

[<span data-ttu-id="404d3-137">Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법</span><span class="sxs-lookup"><span data-stu-id="404d3-137">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="404d3-138">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="404d3-138">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
