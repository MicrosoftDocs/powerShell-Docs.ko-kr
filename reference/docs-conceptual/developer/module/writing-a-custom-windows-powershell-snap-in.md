---
title: 사용자 지정 Windows PowerShell 스냅인 작성 | Microsoft Docs
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
ms.openlocfilehash: 9cf4499ec2992c6cfea83fc5d0bf51d0bbfaa96a
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811632"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="b85c8-102">사용자 지정 Windows PowerShell 스냅인 작성</span><span class="sxs-lookup"><span data-stu-id="b85c8-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="b85c8-103">이 예제에서는 특정 cmdlet을 등록 하는 Windows PowerShell 스냅인을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="b85c8-104">이 유형의 스냅인을 사용 하 여 등록할 cmdlet, 공급자, 형식 또는 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="b85c8-105">어셈블리의 모든 cmdlet 및 공급자를 등록 하는 스냅인을 작성 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 스냅인 작성](./writing-a-windows-powershell-snap-in.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b85c8-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="b85c8-106">특정 cmdlet을 등록 하는 Windows PowerShell 스냅인을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="b85c8-107">RunInstallerAttribute 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-107">Add the RunInstallerAttribute attribute.</span></span>
2. <span data-ttu-id="b85c8-108">[Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) 클래스에서 파생 되는 공용 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="b85c8-109">이 예제에서 클래스 이름은 "CustomPSSnapinTest"입니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="b85c8-110">스냅인 이름에 대 한 public 속성 (필수)을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="b85c8-111">스냅인의 이름을 지정할 때,,,,,,,,,,,,,,,,,,,,,,,, 등의 문자를 사용 하지 마십시오. `#` `.` `,` `(` `)` `{` `}` `[` `]` `&` `-` `/` `\` `$` `;` `:` `"` `'` `<` `>` `|` `?` `@` \`\` ` ```*`</span><span class="sxs-lookup"><span data-stu-id="b85c8-111">When naming snap-ins, do not use any of the following characters: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@`, `` ` ``, `*`</span></span>

   <span data-ttu-id="b85c8-112">이 예제에서 스냅인의 이름은 "CustomPSSnapInTest"입니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-112">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="b85c8-113">스냅인 공급 업체에 대 한 공용 속성 (필수)을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-113">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="b85c8-114">이 예제에서 공급 업체는 "Microsoft"입니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-114">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="b85c8-115">스냅인의 공급 업체 리소스에 대 한 공용 속성을 추가 합니다 (선택 사항).</span><span class="sxs-lookup"><span data-stu-id="b85c8-115">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="b85c8-116">이 예제에서 공급 업체 리소스는 "CustomPSSnapInTest, Microsoft"입니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-116">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="b85c8-117">스냅인에 대 한 설명에 대 한 public 속성 (필수)을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-117">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="b85c8-118">이 예제에서 설명은 "이는 및 cmdlet을 포함 하는 사용자 지정 Windows PowerShell 스냅인입니다 `Test-HelloWorld` `Test-CustomSnapinTest` ."입니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-118">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the `Test-HelloWorld` and `Test-CustomSnapinTest` cmdlets".</span></span>

7. <span data-ttu-id="b85c8-119">스냅인의 설명 리소스에 대 한 public 속성을 추가 합니다 (선택 사항).</span><span class="sxs-lookup"><span data-stu-id="b85c8-119">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="b85c8-120">이 예제에서 공급 업체 리소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-120">In this example, the vendor resource is:</span></span>

   > <span data-ttu-id="b85c8-121">CustomPSSnapInTest,이 스냅인은 테스트-HelloWorld 및 CustomSnapinTest cmdlet이 포함 된 사용자 지정 Windows PowerShell 스냅인입니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-121">CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="b85c8-122">[Runspace](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) 클래스를 사용 하 여 사용자 지정 스냅인 (옵션)에 속하는 cmdlet을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-122">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="b85c8-123">여기에 추가 된 정보에는 cmdlet의 이름, 해당 .NET 유형 및 cmdlet 도움말 파일 이름 (cmdlet 도움말 파일 이름의 형식)이 포함 됩니다 `name.dll-help.xml` .</span><span class="sxs-lookup"><span data-stu-id="b85c8-123">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be `name.dll-help.xml`).</span></span>

   <span data-ttu-id="b85c8-124">이 예제에서는 테스트-HelloWorld 및 TestCustomSnapinTest cmdlet을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-124">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="b85c8-125">사용자 지정 스냅인에 속하는 공급자를 지정 합니다 (선택 사항).</span><span class="sxs-lookup"><span data-stu-id="b85c8-125">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="b85c8-126">이 예제에서는 공급자를 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-126">This example does not specify any providers.</span></span>

10. <span data-ttu-id="b85c8-127">사용자 지정 스냅인에 속하는 형식을 지정 합니다 (선택 사항).</span><span class="sxs-lookup"><span data-stu-id="b85c8-127">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="b85c8-128">이 예제에서는 형식을 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-128">This example does not specify any types.</span></span>

11. <span data-ttu-id="b85c8-129">사용자 지정 스냅인에 속하는 형식을 지정 합니다 (선택 사항).</span><span class="sxs-lookup"><span data-stu-id="b85c8-129">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="b85c8-130">이 예에서는 형식을 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-130">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="b85c8-131">예제</span><span class="sxs-lookup"><span data-stu-id="b85c8-131">Example</span></span>

<span data-ttu-id="b85c8-132">이 예제에서는 및 cmdlet을 등록 하는 데 사용할 수 있는 사용자 지정 Windows PowerShell 스냅인을 작성 하는 방법을 보여 줍니다 `Test-HelloWorld` `Test-CustomSnapinTest` .</span><span class="sxs-lookup"><span data-stu-id="b85c8-132">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the `Test-HelloWorld` and `Test-CustomSnapinTest` cmdlets.</span></span> <span data-ttu-id="b85c8-133">이 예제에서 전체 어셈블리에는이 스냅인에서 등록 되지 않은 다른 cmdlet 및 공급자가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b85c8-133">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

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

<span data-ttu-id="b85c8-134">스냅인을 등록 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 프로그래머 가이드](../prog-guide/windows-powershell-programmer-s-guide.md)에서 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions/ms714644(v=vs.85)) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b85c8-134">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85)) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b85c8-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b85c8-135">See Also</span></span>

<span data-ttu-id="b85c8-136">[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="b85c8-136">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="b85c8-137">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="b85c8-137">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)