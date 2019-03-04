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
ms.openlocfilehash: 20b7fdce1d31e3dee4598a7595962fca1c99d80a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863349"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>사용자 지정 Windows PowerShell 스냅인 작성

이 예제에서는 특정 cmdlet을 등록 하는 Windows PowerShell 스냅인 작성 하는 방법을 보여 줍니다.

스냅인의 형식과이 cmdlet, 공급자, 형식 또는 형식 등록을 지정 합니다. 어셈블리의 모든 cmdlet 및 공급자를 등록 하는 스냅인 작성 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 스냅인 작성](./writing-a-windows-powershell-snap-in.md)합니다.

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>Windows PowerShell 스냅인을 작성 하는 특정 cmdlet를 등록 합니다.

1. RunInstallerAttribute 특성을 추가 합니다.

2. 파생 되는 공용 클래스를 만들어야 합니다 [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) 클래스입니다.

   이 예제에서는 클래스 이름은 "CustomPSSnapinTest"입니다.

3. (필수) 스냅인의 이름에 대 한 공용 속성을 추가 합니다. 스냅인 이름을 지정 하는 경우 사용 하지 마십시오는 다음 문자: # 합니다. , ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ? @ ` *

   이 예제에서는 스냅인 이름이 "CustomPSSnapInTest"입니다.

4. (필수) 스냅인의 공급 업체에 대 한 공용 속성을 추가 합니다.

   이 예제에서는 공급 업체는 "Microsoft"입니다.

5. (선택 사항) 스냅인의 공급 업체 리소스에 대 한 공용 속성을 추가 합니다.

   이 예제에서는 공급 업체 리소스가 "CustomPSSnapInTest, Microsoft"입니다.

6. (필수) 스냅인의 설명에 대 한 공용 속성을 추가 합니다.

   이 예제에서는 설명은 다음과 같습니다. "This is 사용자 지정 Windows PowerShell 스냅인에서 HelloWorld 테스트 및 테스트 CustomSnapinTest cmdlet을 포함 하는".

7. (선택 사항) 스냅인의 설명 리소스에 대 한 공용 속성을 추가 합니다.

   이 예제에서는 공급 업체 리소스가 "CustomPSSnapInTest,이 사용자 지정 Windows PowerShell 스냅인에서 HelloWorld 테스트 및 테스트 CustomSnapinTest cmdlet이 포함 된"입니다.

8. 사용자 지정 스냅인 (선택 사항) 사용 하 여 속하는 cmdlet은 지정 된 [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) 클래스입니다. 여기에 추가 정보에는 cmdlet, 해당.NET 형식 및 cmdlet 도움말 파일 이름 (cmdlet 도움말 파일 이름 형식의 되었거나 name.dll help.xml 이어야 함)의 이름을 포함 됩니다.

   이 예제에서는 테스트 HelloWorld 및 TestCustomSnapinTest cmdlet을 추가합니다.

9. 사용자 지정 스냅인 (선택 사항)에 속해 있는 공급자를 지정 합니다.

   이 예제에서는 모든 공급자를 지정 하지 않습니다.

10. 사용자 지정 스냅인 (선택 사항)에 속해 있는 유형을 지정 합니다.

    이 예제에서는 모든 형식을 지정 하지 않습니다.

11. 사용자 지정 스냅인 (선택 사항)에 속하는 형식을 지정 합니다.

    이 예제에서는 모든 형식 지정 하지 않습니다.

## <a name="example"></a>예제

이 예제에서는 사용자 지정 Windows PowerShell 스냅인에서 HelloWorld 테스트 및 테스트 CustomSnapinTest cmdlet을 등록 하는 작성 하는 방법을 보여 줍니다. 이 예제에서는 완전 한 어셈블리를 포함할 수 있습니다 다른 cmdlet와 공급자가 스냅인에서 등록 하지는 알아야 합니다.

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

스냅인을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) 에 [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md)합니다.

## <a name="see-also"></a>참고 항목

[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
