---
title: 개체에 대 한 기본 메서드 정의 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 10917de9e897fc1eed362430d63ff5b9cb7e813d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774595"
---
# <a name="defining-default-methods-for-objects"></a>개체에 대한 기본 메서드 정의

.NET Framework 개체를 확장 하는 경우 개체에 코드 메서드 및 스크립트 메서드를 추가할 수 있습니다.
이러한 메서드를 정의 하는 데 사용 되는 XML은 다음 섹션에 설명 되어 있습니다.

> [!NOTE]
> 다음 섹션의 예제는 `Types.ps1xml` Windows PowerShell 설치 디렉터리 ()의 형식 파일에서 가져온 것 `$PSHOME` 입니다. 자세한 내용은 [Types.ps1Xml 정보](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)를 참조 하세요.

## <a name="code-methods"></a>코드 메서드

코드 메서드가 .NET Framework 개체의 정적 메서드를 참조 합니다.

다음 예제에서는 **ToString** 메서드가 [System.Xml.Xml노드](/dotnet/api/System.Xml.XmlNode) 형식에 추가 됩니다. [Pscodemethod](/dotnet/api/system.management.automation.pscodemethod) 요소는 확장 메서드를 코드 메서드로 정의 합니다. [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) 요소는 확장 메서드의 이름을 지정 합니다. 그리고 [Codereference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) 요소는 정적 메서드를 지정 합니다. [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) 요소의 멤버에 [pscodemethod](/dotnet/api/system.management.automation.pscodemethod) 요소를 추가할 수도 있습니다.

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodeMethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a>스크립트 메서드

스크립트 메서드는 값이 스크립트의 출력을 포함 하는 메서드를 정의 합니다. 다음 예제에서는 **ConvertToDateTime** 메서드를 [system.web 개체](/dotnet/api/System.Management.ManagementObject) 형식에 추가 합니다. [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) 요소는 확장 메서드를 스크립트 메서드로 정의 합니다. [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) 요소는 확장 메서드의 이름을 지정 합니다. [스크립트](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) 요소는 메서드 값을 생성 하는 스크립트를 지정 합니다. [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) 요소의 멤버에 [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) 요소를 추가할 수도 있습니다.

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

## <a name="see-also"></a>참조

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)
