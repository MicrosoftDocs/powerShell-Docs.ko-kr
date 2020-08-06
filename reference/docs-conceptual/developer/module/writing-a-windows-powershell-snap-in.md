---
title: Windows PowerShell 스냅인 작성 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.openlocfilehash: 02603c54fb9852a8b78ecf68e3ee387d1fd418fc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779094"
---
# <a name="writing-a-windows-powershell-snap-in"></a>Windows PowerShell 스냅인 작성

이 예제에서는 어셈블리의 모든 cmdlet 및 Windows PowerShell 공급자를 등록 하는 데 사용할 수 있는 Windows PowerShell 스냅인을 작성 하는 방법을 보여 줍니다.

이 유형의 스냅인을 사용 하 여 등록 하려는 cmdlet 및 공급자를 선택 하지 않습니다. 등록 된 항목을 선택할 수 있는 스냅인을 작성 하려면 [사용자 지정 Windows PowerShell 스냅인 작성](./writing-a-custom-windows-powershell-snap-in.md)을 참조 하세요.

### <a name="writing-a-windows-powershell-snap-in"></a>Windows PowerShell 스냅인 작성

1. RunInstallerAttribute 특성을 추가 합니다.

2. [Add-pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) 클래스에서 파생 되는 공용 클래스를 만듭니다.

    이 예제에서 클래스 이름은 "GetProcPSSnapIn01"입니다.

3. 스냅인 이름에 대 한 public 속성 (필수)을 추가 합니다. 스냅인의 이름을 지정할 때,,,,,,,,,,,,,,,,,,,,,,,, 등의 문자를 사용 하지 마십시오. `#` `.` `,` `(` `)` `{` `}` `[` `]` `&` `-` `/` `\` `$` `;` `:` `"` `'` `<` `>` `|` `?` `@` `` ` ```*`

    이 예제에서 스냅인의 이름은 "GetProcPSSnapIn01"입니다.

4. 스냅인 공급 업체에 대 한 공용 속성 (필수)을 추가 합니다.

    이 예제에서 공급 업체는 "Microsoft"입니다.

5. 스냅인의 공급 업체 리소스에 대 한 공용 속성을 추가 합니다 (선택 사항).

    이 예제에서 공급 업체 리소스는 "GetProcPSSnapIn01, Microsoft"입니다.

6. 스냅인에 대 한 설명에 대 한 public 속성 (필수)을 추가 합니다.

    이 예제에서 설명은 "This is the Windows PowerShell 스냅인은 get proc cmdlet을 등록 합니다."입니다.

7. 스냅인의 설명 리소스에 대 한 public 속성을 추가 합니다 (선택 사항).

    이 예제에서 공급 업체 리소스는 "GetProcPSSnapIn01" 이며,이는 get proc cmdlet을 등록 하는 Windows PowerShell 스냅인입니다.

## <a name="example"></a>예제

이 예제에서는 Windows PowerShell 셸에서 Get Proc cmdlet을 등록 하는 데 사용할 수 있는 Windows PowerShell 스냅인을 작성 하는 방법을 보여 줍니다. 이 예제에서 전체 어셈블리는 GetProcPSSnapIn01 스냅인 클래스와 `Get-Proc` cmdlet 클래스만 포함 합니다.

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

## <a name="see-also"></a>참고 항목

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
