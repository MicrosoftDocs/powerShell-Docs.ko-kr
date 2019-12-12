---
title: 개체에 대 한 속성 확장 | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 3b14007384cca0d0cfa35655aee437adf73b1ff0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364452"
---
# <a name="extending-properties-for-objects"></a>개체 속성 확장

.NET Framework 개체를 확장 하는 경우 개체에 별칭 속성, 코드 속성, 메모 속성, 스크립트 속성 및 속성 집합을 추가할 수 있습니다. 이러한 속성을 정의 하는 XML은 다음 섹션에 설명 되어 있습니다.

> [!NOTE]
> 다음 섹션의 예는 PowerShell 설치 디렉터리 (`$PSHOME`)의 기본 `Types.ps1xml` 형식 파일에서 가져온 것입니다. 자세한 내용은 [Types.ps1xml 정보](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)를 참조 하세요.

## <a name="alias-properties"></a>별칭 속성

별칭 속성은 기존 속성의 새 이름을 정의 합니다.

다음 예제에서는 **Count** 속성이 [system.object](/dotnet/api/System.Array) 형식에 추가 됩니다. [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) 요소는 확장 속성을 별칭 속성으로 정의 합니다. [Name](/dotnet/api/system.management.automation.psmemberinfo.name) 요소는 새 이름을 지정 합니다. [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) 요소는 별칭에 의해 참조 되는 기존 속성을 지정 합니다. [MemberSets](/dotnet/api/system.management.automation.psmemberset) 요소의 멤버에 `AliasProperty` 요소를 추가할 수도 있습니다.

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

## <a name="code-properties"></a>코드 속성

코드 속성은 .NET Framework 개체의 정적 속성을 참조 합니다.

다음 예제에서 **Mode** 속성은 [system.io.directoryinfo](/dotnet/api/System.IO.DirectoryInfo) 형식에 추가 됩니다. [Codeproperty](/dotnet/api/system.management.automation.pscodeproperty) 요소는 확장 속성을 코드 속성으로 정의 합니다. [Name](/dotnet/api/system.management.automation.psmemberinfo.name) 요소는 확장 속성의 이름을 지정 합니다. 그리고 [Getcodereference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) 요소는 확장 속성이 참조 하는 정적 메서드를 정의 합니다. [MemberSets](/dotnet/api/system.management.automation.psmemberset) 요소의 멤버에 `CodeProperty` 요소를 추가할 수도 있습니다.

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>Microsoft.PowerShell.Commands.FileSystemProvider</TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

## <a name="note-properties"></a>참고 속성

Note 속성은 정적 값이 있는 속성을 정의 합니다.

다음 예제에서 값이 항상 **Success**인 **Status** 속성은 [system.io.directoryinfo](/dotnet/api/System.IO.DirectoryInfo) 형식에 추가 됩니다. [Note property](/dotnet/api/system.management.automation.psnoteproperty) 요소는 확장 속성을 note 속성으로 정의 합니다. [Name](/dotnet/api/system.management.automation.psmemberinfo.name) 요소는 확장 속성의 이름을 지정 합니다. [Value](/dotnet/api/system.management.automation.psnoteproperty.value) 요소는 확장 속성의 정적 값을 지정 합니다. [MemberSets](/dotnet/api/system.management.automation.psmemberset) 요소의 멤버에 `NoteProperty` 요소를 추가할 수도 있습니다.

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

## <a name="script-properties"></a>스크립트 속성

스크립트 속성은 값이 스크립트의 출력 인 속성을 정의 합니다.

다음 예제에서는 **VersionInfo** 속성이 [system.object](/dotnet/api/System.IO.FileInfo) 형식에 추가 됩니다. [Scriptproperty](/dotnet/api/system.management.automation.psscriptproperty) 요소는 확장 속성을 스크립트 속성으로 정의 합니다. [Name](/dotnet/api/system.management.automation.psmemberinfo.name) 요소는 확장 속성의 이름을 지정 합니다. [Getscriptblock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) 요소는 속성 값을 생성 하는 스크립트를 지정 합니다. [MemberSets](/dotnet/api/system.management.automation.psmemberset) 요소의 멤버에 `ScriptProperty` 요소를 추가할 수도 있습니다.

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
        [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

## <a name="property-sets"></a>속성 집합

속성 집합은 집합의 이름으로 참조할 수 있는 확장 속성의 그룹을 정의 합니다.
예를 들어 [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**property** 매개 변수는 표시할 특정 속성 집합을 지정할 수 있습니다. 속성 집합을 지정 하면 해당 집합에 속한 속성만 표시 됩니다.

개체에 대해 정의할 수 있는 속성 집합의 수에는 제한이 없습니다. 그러나 개체의 기본 표시 속성을 정의 하는 데 사용 되는 속성 집합은 **Psstandardmembers** 멤버 집합 내에서 지정 해야 합니다. `Types.ps1xml` 형식 파일에서 기본 속성 집합 이름에는 **Defaultdisplayproperty**, **DefaultDisplayPropertySet**및 **DefaultKeyPropertySet**가 포함 됩니다. **Psstandardmembers** 멤버 집합에 추가 하는 모든 추가 속성 집합은 무시 됩니다.

다음 예제에서는 **DefaultDisplayPropertySet** 속성 집합이 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 형식의 **psstandardmembers** 멤버 집합에 추가 됩니다. [PropertySet](/dotnet/api/system.management.automation.pspropertyset) 요소는 속성의 그룹을 정의 합니다. [Name](/dotnet/api/system.management.automation.psmemberinfo.name) 요소는 속성 집합의 이름을 지정 합니다. 그리고 [Referencedproperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) 요소는 집합의 속성을 지정 합니다. 또한 [Type](/dotnet/api/system.management.automation.pstypename) 요소의 멤버에 `PropertySet` 요소를 추가할 수 있습니다.

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
           <Name>DefaultDisplayPropertySet</Name>
           <ReferencedProperties>
            <Name>Status</Name
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

## <a name="see-also"></a>참고 항목

[Types.ps1xml 정보](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[시스템 관리. 자동화](/dotnet/api/System.Management.Automation)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
