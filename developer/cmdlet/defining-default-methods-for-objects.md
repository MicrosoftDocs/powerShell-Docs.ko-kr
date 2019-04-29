---
title: 개체에 대 한 기본 메서드를 정의 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: fa0f0371856d8723af7ec17a4306de209a481a18
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068218"
---
# <a name="defining-default-methods-for-objects"></a>개체에 대한 기본 메서드 정의

.NET Framework 개체를 확장 하는 경우 코드 메서드 및 스크립트 메서드를 개체에 추가할 수 있습니다. 이러한 메서드를 정의 하는 데 사용 되는 XML은 다음 섹션에 설명 되어 있습니다.

> [!NOTE]
> 다음 섹션의 예는 Windows PowerShell 설치 디렉터리에서 Types.ps1xml 형식 파일에서 (`$pshome`).

## <a name="code-methods"></a>코드 메서드

코드 메서드는.NET Framework 개체의 정적 메서드를 참조합니다.

다음 예제에서는 **ConvertLargeIntegerToInt64** 메서드가 추가 되는 [System.Xml.Xmlnode? Displayproperty =](/dotnet/api/System.Xml.XmlNode) 형식입니다. 합니다 [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) 요소 코드 메서드로 확장된 메서드를 정의 합니다. 합니다 [이름을](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) 요소 확장 메서드의 이름을 지정 합니다. 그 뿐만 아니라 [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) 요소는 정적 메서드를 지정 합니다. (추가할 수도 있습니다는 [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) 의 멤버에는 요소는 [구성원 집합](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) 요소입니다.)

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodemethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a>스크립트 메서드

스크립트 메서드 값을 스크립트의 출력 메서드를 정의 합니다. 다음 예제에서는 **ConvertToDateTime** 메서드가 추가 되는 [System.Management.Managementobject? Displayproperty =](/dotnet/api/System.Management.ManagementObject) 형식입니다. 합니다 [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) 요소 스크립트 메서드로 확장된 메서드를 정의 합니다. 합니다 [이름을](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) 요소 확장 메서드의 이름을 지정 합니다. 그 뿐만 아니라 [스크립트](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) 요소 메서드 값을 생성 하는 스크립트를 지정 합니다. (추가할 수도 있습니다는 [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) 의 멤버에는 요소는 [구성원 집합](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) 요소입니다.)

```xml
<Type>
  <Name>System.Management.ManagementObject</Name>
  <Members>
    <ScriptMethod>
      <Name>ConvertToDateTime</Name>
      <Script>
        [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
      </Script>
    </ScriptMethod>
  </Members>
</Type>
```

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)