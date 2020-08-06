---
title: 사용자 지정 Windows PowerShell 스냅인 작성 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- snap-ins [PowerShell SDK], custom PSSnapin example
- cmdlets [PowerShell SDK], specified in snap-ins
ms.openlocfilehash: 3672dcc2e962b6795888ab5be3d461380e379315
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779219"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>사용자 지정 Windows PowerShell 스냅인 작성

이 예제에서는 특정 cmdlet을 등록 하는 Windows PowerShell 스냅인을 작성 하는 방법을 보여 줍니다.

이 유형의 스냅인을 사용 하 여 등록할 cmdlet, 공급자, 형식 또는 형식을 지정 합니다. 어셈블리의 모든 cmdlet 및 공급자를 등록 하는 스냅인을 작성 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 스냅인 작성](./writing-a-windows-powershell-snap-in.md)을 참조 하세요.

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>특정 cmdlet을 등록 하는 Windows PowerShell 스냅인을 작성 합니다.

1. RunInstallerAttribute 특성을 추가 합니다.
2. [Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) 클래스에서 파생 되는 공용 클래스를 만듭니다.

   이 예제에서 클래스 이름은 "CustomPSSnapinTest"입니다.

3. 스냅인 이름에 대 한 public 속성 (필수)을 추가 합니다. 스냅인의 이름을 지정할 때,,,,,,,,,,,,,,,,,,,,,,,, 등의 문자를 사용 하지 마십시오. `#` `.` `,` `(` `)` `{` `}` `[` `]` `&` `-` `/` `\` `$` `;` `:` `"` `'` `<` `>` `|` `?` `@` `` ` ```*`

   이 예제에서 스냅인의 이름은 "CustomPSSnapInTest"입니다.

4. 스냅인 공급 업체에 대 한 공용 속성 (필수)을 추가 합니다.

   이 예제에서 공급 업체는 "Microsoft"입니다.

5. 스냅인의 공급 업체 리소스에 대 한 공용 속성을 추가 합니다 (선택 사항).

   이 예제에서 공급 업체 리소스는 "CustomPSSnapInTest, Microsoft"입니다.

6. 스냅인에 대 한 설명에 대 한 public 속성 (필수)을 추가 합니다.

   이 예제에서 설명은 "이는 및 cmdlet을 포함 하는 사용자 지정 Windows PowerShell 스냅인입니다 `Test-HelloWorld` `Test-CustomSnapinTest` ."입니다.

7. 스냅인의 설명 리소스에 대 한 public 속성을 추가 합니다 (선택 사항).

   이 예제에서 공급 업체 리소스는 다음과 같습니다.

   > CustomPSSnapInTest,이 스냅인은 테스트-HelloWorld 및 CustomSnapinTest cmdlet이 포함 된 사용자 지정 Windows PowerShell 스냅인입니다.

8. [Runspace](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) 클래스를 사용 하 여 사용자 지정 스냅인 (옵션)에 속하는 cmdlet을 지정 합니다. 여기에 추가 된 정보에는 cmdlet의 이름, 해당 .NET 유형 및 cmdlet 도움말 파일 이름 (cmdlet 도움말 파일 이름의 형식)이 포함 됩니다 `name.dll-help.xml` .

   이 예제에서는 테스트-HelloWorld 및 TestCustomSnapinTest cmdlet을 추가 합니다.

9. 사용자 지정 스냅인에 속하는 공급자를 지정 합니다 (선택 사항).

   이 예제에서는 공급자를 지정 하지 않습니다.

10. 사용자 지정 스냅인에 속하는 형식을 지정 합니다 (선택 사항).

    이 예제에서는 형식을 지정 하지 않습니다.

11. 사용자 지정 스냅인에 속하는 형식을 지정 합니다 (선택 사항).

    이 예에서는 형식을 지정 하지 않습니다.

## <a name="example"></a>예제

이 예제에서는 및 cmdlet을 등록 하는 데 사용할 수 있는 사용자 지정 Windows PowerShell 스냅인을 작성 하는 방법을 보여 줍니다 `Test-HelloWorld` `Test-CustomSnapinTest` . 이 예제에서 전체 어셈블리에는이 스냅인에서 등록 되지 않은 다른 cmdlet 및 공급자가 포함 될 수 있습니다.

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

스냅인을 등록 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 프로그래머 가이드](../prog-guide/windows-powershell-programmer-s-guide.md)에서 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions/ms714644(v=vs.85)) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
