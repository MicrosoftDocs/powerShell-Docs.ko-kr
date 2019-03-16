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
# <a name="writing-a-windows-powershell-snap-in"></a>Windows PowerShell 스냅인 작성

이 예제에서는 Windows PowerShell 스냅인에서 어셈블리의 모든 cmdlet 및 Windows PowerShell 공급자를 등록 하는 작성 하는 방법을 보여 줍니다.

이 유형의 스냅인을 선택 하지 않으면는 cmdlet 및 공급자를 등록 합니다. 등록 된 항목을 선택할 수 있는 스냅인 쓸 참조 [사용자 지정 Windows PowerShell 스냅인 작성](./writing-a-custom-windows-powershell-snap-in.md)합니다.

### <a name="writing-a-windows-powershell-snap-in"></a>Windows PowerShell 스냅인 작성

1. RunInstallerAttribute 특성을 추가 합니다.

2. 파생 되는 공용 클래스를 만들어야 합니다 [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) 클래스입니다.

    이 예제에서는 클래스 이름은 "GetProcPSSnapIn01"입니다.

3. (필수) 스냅인의 이름에 대 한 공용 속성을 추가 합니다. 스냅인 이름을 지정 하는 경우 사용 하지 마십시오는 다음 문자: # 합니다. , ( ) { } [ ] & - /\ $ ; : " ' \< > ; ? @ ` *

    이 예제에서는 스냅인 이름이 "GetProcPSSnapIn01"입니다.

4. (필수) 스냅인의 공급 업체에 대 한 공용 속성을 추가 합니다.

    이 예제에서는 공급 업체는 "Microsoft"입니다.

5. (선택 사항) 스냅인의 공급 업체 리소스에 대 한 공용 속성을 추가 합니다.

    이 예제에서는 공급 업체 리소스가 "GetProcPSSnapIn01, Microsoft"입니다.

6. (필수) 스냅인의 설명에 대 한 공용 속성을 추가 합니다.

    이 예의 설명은 "This is get-proc cmdlet을 등록 하는 Windows PowerShell 스냅인"입니다.

7. (선택 사항) 스냅인의 설명 리소스에 대 한 공용 속성을 추가 합니다.

    이 예제에서는 공급 업체 리소스가 "GetProcPSSnapIn01,이 get-proc cmdlet을 등록 하는 Windows PowerShell 스냅인"입니다.

## <a name="example"></a>예제

이 예제에서는 Windows PowerShell 스냅인을 Windows PowerShell 셸에 Get-proc cmdlet을 등록 하는 작성 하는 방법을 보여 줍니다. 이 예제에서는 전체 어셈블리는 포함 된 GetProcPSSnapIn01 스냅인 클래스 및는 Get-proc cmdlet 클래스에 유의 합니다.

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

[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
