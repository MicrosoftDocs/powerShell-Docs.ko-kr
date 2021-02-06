---
description: 파일을 사용 하 여 `Types.ps1xml` PowerShell에서 사용 되는 개체 유형을 확장 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_types.ps1xml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Types.ps1xml
ms.openlocfilehash: 9a87394631d3318f3fb3f4b2a0cb2ab8d25408d0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599341"
---
# <a name="about-typesps1xml"></a>Types.ps1xml 정보

## <a name="short-description"></a>간단한 설명
파일을 사용 하 여 `Types.ps1xml` PowerShell에서 사용 되는 개체 유형을 확장 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

확장 유형 데이터는 PowerShell에서 개체 유형의 추가 속성 및 메서드 ("멤버")를 정의 합니다. 확장 유형 데이터를 PowerShell 세션에 추가 하는 방법에는 두 가지가 있습니다.

- `Types.ps1xml` file: 확장 유형 데이터를 정의 하는 XML 파일입니다.
- `Update-TypeData`: `Types.ps1xml` 파일을 다시 로드 하 고 현재 세션의 형식에 대 한 확장 데이터를 정의 하는 cmdlet입니다.

이 항목에서는 파일에 대해 설명 `Types.ps1xml` 합니다. Cmdlet을 사용 하 여 동적 확장 유형 데이터를 현재 세션에 추가 하는 방법에 대 한 자세한 내용은 `Update-TypeData` [update-typedata](xref:Microsoft.PowerShell.Utility.Update-TypeData)를 참조 하세요.

## <a name="about-extended-type-data"></a>확장 유형 데이터 정보

확장 유형 데이터는 PowerShell에서 개체 유형의 추가 속성 및 메서드 ("멤버")를 정의 합니다. PowerShell에서 지 원하는 모든 형식을 확장 하 고 개체 형식에 정의 된 속성을 사용 하는 것과 동일한 방식으로 추가 된 속성 및 메서드를 사용할 수 있습니다.

예를 들어 PowerShell은 cmdlet이 반환 하는 개체와 같은 모든 개체에 **DateTime** 속성을 추가 `System.DateTime` `Get-Date` 합니다.

```powershell
(Get-Date).DateTime
```

```Output
Sunday, January 29, 2012 9:43:57 AM
```

PowerShell에서 속성을 추가 하 고 powershell 에서만 표시 되기 때문에 [System. datetime](/dotnet/api/system.datetime) 구조체의 설명에서 **datetime** 속성을 찾지 못합니다.

PowerShell은 내부적으로 확장 형식의 기본 집합을 정의 합니다. 이 형식 정보는 시작 시 모든 PowerShell 세션에서 로드 됩니다. **DateTime** 속성은이 기본 집합의 일부입니다. PowerShell 6 이전에는 형식 정의가 `Types.ps1xml` powershell 설치 디렉터리 ()에 파일을 저장 했습니다 `$PSHOME` .

## <a name="adding-extended-type-data-to-powershell"></a>PowerShell에 확장 형식 데이터 추가

PowerShell 세션에는 확장 유형 데이터의 세 가지 원본이 있습니다.

- PowerShell에서 정의 되는는 모든 PowerShell 세션에 자동으로 로드 됩니다. PowerShell 6부터이 정보는 PowerShell로 컴파일되며 더 이상 파일에 제공 되지 않습니다 `Types.ps1xml` .

- `Types.ps1xml`모듈을 현재 세션으로 가져올 때 모듈 내보내기 파일이 로드 됩니다.

- Cmdlet을 사용 하 여 정의 된 확장 유형 데이터 `Update-TypeData` 는 현재 세션에만 추가 됩니다. 파일에 저장 되지 않습니다.

세션에서 세 소스의 확장 유형 데이터는 동일한 방식으로 개체에 적용 되며 지정 된 유형의 모든 개체에서 사용할 수 있습니다.

## <a name="the-typedata-cmdlets"></a>Update-typedata cmdlet

다음 cmdlet은 PowerShell 3.0 이상의 **Microsoft powershell** 모듈에 포함 되어 있습니다.

- `Get-TypeData`: 현재 세션에서 확장 유형 데이터를 가져옵니다.
- `Update-TypeData`: `Types.ps1xml` 파일을 다시 로드 합니다. 확장 유형 데이터를 현재 세션에 추가 합니다.
- `Remove-TypeData`: 현재 세션에서 확장 유형 데이터를 제거 합니다.

이러한 cmdlet에 대 한 자세한 내용은 각 cmdlet에 대 한 도움말 항목을 참조 하세요.

## <a name="built-in-typesps1xml-files"></a>기본 제공 Types.ps1xml 파일

`Types.ps1xml`디렉터리의 파일은 `$PSHOME` 모든 세션에 자동으로 추가 됩니다.

`Types.ps1xml`Powershell 설치 디렉터리 ()의 파일은 `$PSHOME` powershell에서 사용 되는 개체에 속성 및 메서드를 추가할 수 있는 XML 기반 텍스트 파일입니다. PowerShell에는 `Types.ps1xml` .net 형식에 여러 요소를 추가 하는 기본 제공 파일이 있지만 추가 `Types.ps1xml` 파일을 만들어 형식을 더 확장할 수 있습니다.

예를 들어 기본적으로 array 개체 ()에는 `System.Array` 배열의 개체 수를 나열 하는 **Length** 속성이 있습니다. 그러나 이름 **길이** 는 속성을 명확 하 게 설명 하지 않으므로 PowerShell은 같은 값을 표시 하는 **Count** 라는 별칭 속성을 추가 합니다. 다음 XML은 형식에 **Count** 속성을 추가 합니다 `System.Array` .

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>
        Length
      </ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

새 **AliasProperty** 을 가져오려면 `Get-Member` 다음 예제와 같이 배열에 대해 명령을 사용 합니다.

```powershell
Get-Member -InputObject (1,2,3,4)
```

이 명령은 다음 결과를 반환 합니다.

```Output
Name       MemberType    Definition
----       ----------    ----------
Count      AliasProperty Count = Length
Address    Method        System.Object& Address(Int32)
Clone      Method        System.Object Clone()
CopyTo     Method        System.Void CopyTo(Array array, Int32 index):
Equals     Method        System.Boolean Equals(Object obj)
Get        Method        System.Object Get(Int32)
# ...
```

따라서 PowerShell에서 배열의 **Count** 속성 또는 **Length** 속성 중 하나를 사용할 수 있습니다. 다음은 그 예입니다. 

```powershell
(1, 2, 3, 4).count
4
```

```powershell
(1, 2, 3, 4).length
4
```

## <a name="creating-new-typesps1xml-files"></a>새 Types.ps1xml 파일 만들기

`.ps1xml`PowerShell과 함께 설치 되는 파일은 서식에 스크립트 블록을 포함할 수 있으므로 변조를 방지 하기 위해 디지털로 서명 됩니다. 따라서 .NET 형식에 속성 또는 메서드를 추가 하려면 고유한 `Types.ps1xml` 파일을 만든 다음 PowerShell 세션에 추가 합니다.

새 파일을 만들려면 기존 파일을 복사 하 여 시작 `Types.ps1xml` 합니다. 새 파일에는 아무 이름이 나 지정할 수 있지만 `.ps1xml` 파일 이름 확장명이 있어야 합니다. PowerShell에 액세스할 수 있는 모든 디렉터리에 새 파일을 저장할 수 있지만 PowerShell 설치 디렉터리 ( `$PSHOME` ) 또는 설치 디렉터리의 하위 디렉터리에 파일을 저장 하는 것이 유용 합니다.

새 파일을 저장 한 후 cmdlet을 사용 `Update-TypeData` 하 여 PowerShell 세션에 새 파일을 추가 합니다. 형식이 정의 된 기본 제공 형식 보다 우선적으로 적용 되도록 하려면 cmdlet의 **PrependData** 매개 변수를 사용 합니다 `Update-TypeData` . `Update-TypeData` 현재 세션에만 영향을 줍니다. 이후 모든 세션을 변경 하려면 콘솔을 내보내거나 `Update-TypeData` PowerShell 프로필에 명령을 추가 합니다.

## <a name="typesps1xml-and-add-member"></a>Xml 및 Add-Member Types.ps1

이 `Types.ps1xml` 파일은 영향을 받는 PowerShell 세션에서 지정 된 .net 형식의 모든 개체 인스턴스에 대 한 속성 및 메서드를 추가 합니다. 그러나 개체의 한 인스턴스에만 속성 또는 메서드를 추가 해야 하는 경우에는 cmdlet을 사용 `Add-Member` 합니다.

자세한 내용은 [구성원 추가](xref:Microsoft.PowerShell.Utility.Add-Member)를 참조 하세요.

## <a name="example-adding-an-age-member-to-fileinfo-objects"></a>예: FileInfo 개체에 Age 멤버 추가

이 예제에서는 **Age** 속성을 **system.object** 개체에 추가 하는 방법을 보여 줍니다. 파일의 보존 기간은 만든 시간과 현재 시간 (일) 간의 차이입니다.

**Age** 속성은 스크립트 블록을 사용 하 여 계산 되므로 `<ScriptProperty>` 새 **age** 속성의 모델로 사용할 태그를 찾습니다.

다음 XML 코드를 파일에 저장 `$PSHOME\MyTypes.ps1xml` 합니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Types>
  <Type>
    <Name>System.IO.FileInfo</Name>
    <Members>
      <ScriptProperty>
        <Name>Age</Name>
        <GetScriptBlock>
          ((Get-Date) - ($this.CreationTime)).Days
        </GetScriptBlock>
      </ScriptProperty>
    </Members>
  </Type>
</Types>
```

`Update-TypeData`를 실행 하 여 `Types.ps1xml` 현재 세션에 새 파일을 추가 합니다. 이 명령은 **PrependData** 매개 변수를 사용 하 여 새 파일을 원래 정의 보다 높은 우선 순위 순서 대로 추가 합니다.

에 대 한 자세한 내용은 `Update-TypeData` [update-typedata](xref:Microsoft.PowerShell.Utility.Update-TypeData)를 참조 하세요.

```powershell
Update-Typedata -PrependPath $PSHOME\MyTypes.ps1xml
```

변경을 테스트 하려면 명령을 실행 하 여 `Get-ChildItem` 디렉터리에서 PowerShell.exe 파일을 가져온 다음 파일을 `$PSHOME` cmdlet으로 파이프 하 여 `Format-List` 파일의 모든 속성을 나열 합니다. 변경의 결과로 **Age** 속성이 목록에 표시 됩니다.

```powershell
Get-ChildItem $PSHOME\pwsh.exe | Select-Object Age
```

```Output
142
```

## <a name="the-xml-in-typesps1xml-files"></a>Types.ps1xml 파일의 XML

전체 스키마 정의는 GitHub의 PowerShell 소스 코드 리포지토리에서 [Types. xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Types.xsd) 에서 찾을 수 있습니다.

`<Types>`태그는 파일에 정의 된 모든 형식을 포함 합니다. 태그는 하나만 있어야 합니다 `<Types>` .

파일에 언급 된 각 .NET 형식은 태그로 표시 되어야 합니다 `<Type>` .

형식 태그는 다음 태그를 포함 해야 합니다.

`<Name>`: 영향을 받는 .NET 형식의 이름을 포함 합니다.

`<Members>`: .NET 형식에 대해 정의 된 새 속성 및 메서드에 대 한 태그를 포함 합니다.

다음 멤버 태그는 태그 내부에 있을 수 있습니다 `<Members>` .

`<AliasProperty>`: 기존 속성의 새 이름을 정의 합니다.

태그에는 `<AliasProperty>` `<Name>` 새 속성의 이름을 지정 하는 태그와 `<ReferencedMemberName>` 기존 속성을 지정 하는 태그가 있어야 합니다.

예를 들어 **Count** alias 속성은 array 개체의 **Length** 속성에 대 한 별칭입니다.

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

`<CodeMethod>`: .NET 클래스의 정적 메서드를 참조 합니다.

태그에는 `<CodeMethod>` `<Name>` 새 메서드의 이름을 지정 하는 태그와 `<GetCodeReference>` 메서드가 정의 된 코드를 지정 하는 태그가 있어야 합니다.

예를 들어 개체의 **모드** 속성은 `System.IO.DirectoryInfo` PowerShell FileSystem 공급자에 정의 된 코드 속성입니다.

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

`<CodeProperty>`: .NET 클래스의 정적 메서드를 참조 합니다.

태그에는 `<CodeProperty>` `<Name>` 새 속성의 이름을 지정 하는 태그와 `<GetCodeReference>` 속성이 정의 된 코드를 지정 하는 태그가 있어야 합니다.

예를 들어 개체의 **모드** 속성은 `System.IO.DirectoryInfo` PowerShell FileSystem 공급자에 정의 된 코드 속성입니다.

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

`<MemberSet>`: 멤버 컬렉션 (속성 및 메서드)을 정의 합니다.

`<MemberSet>`태그는 기본 태그 안에 표시 `<Members>` 됩니다. 태그는 `<Name>` 멤버 집합의 이름 및 `<Members>` 집합의 멤버 (속성 및 메서드)를 포함 하는 보조 태그를 둘러싸는 태그를 묶어야 합니다. 속성 (예: `<NoteProperty>` 또는 `<ScriptProperty>` ) 또는 메서드 (예: 또는)를 만드는 모든 태그는 `<Method>` `<ScriptMethod>` 집합의 멤버일 수 있습니다.

`Types.ps1xml`파일에서 태그는 `<MemberSet>` PowerShell에서 .net 개체의 기본 뷰를 정의 하는 데 사용 됩니다. 이 경우 멤버 집합의 이름 (태그 내의 값 `<Name>` )은 항상 **Psstandardmembers** 이며 속성 이름 (태그의 값 `<Name>` )은 다음 중 하나입니다.

- `DefaultDisplayProperty`: 개체의 단일 속성입니다.

- `DefaultDisplayPropertySet`: 개체의 하나 이상의 속성입니다.

- `DefaultKeyPropertySet`: 개체의 하나 이상의 키 속성입니다. 키 속성은 세션 기록에 있는 항목의 ID 수와 같은 속성 값의 인스턴스를 식별 합니다.

예를 들어 다음 XML은 cmdlet에서 반환 되는 서비스 (개체)의 기본 표시를 정의 합니다 `System.ServiceProcess.ServiceController` `Get-Service` . **Status**, **Name** 및 **DisplayName** 속성으로 설정 된 기본 속성으로 구성 된 **psstandardmembers** 라는 구성원 집합을 정의 합니다.

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
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

`<Method>`: 기본 개체의 네이티브 메서드를 참조 합니다.

`<Methods>`: 개체의 메서드 컬렉션입니다.

`<NoteProperty>`: 정적 값을 사용 하 여 속성을 정의 합니다.

태그에는 `<NoteProperty>` `<Name>` 새 속성의 이름을 지정 하는 태그와 `<Value>` 속성의 값을 지정 하는 태그가 있어야 합니다.

예를 들어 다음 XML은 **system.io.directoryinfo** 개체에 대 한 **상태** 속성을 만듭니다. **Status** 속성의 값은 항상 **Success** 입니다.

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

`<ParameterizedProperty>`: 인수를 사용 하 고 값을 반환 하는 속성입니다.

`<Properties>`: 개체 속성의 컬렉션입니다.

`<Property>`: 기본 개체의 속성입니다.

`<PropertySet>`: 개체의 속성 컬렉션을 정의 합니다.

태그에는 `<PropertySet>` `<Name>` 속성 집합의 이름과 `<ReferencedProperty>` 속성을 지정 하는 태그를 지정 하는 태그가 있어야 합니다. 속성의 이름은 태그로 묶여 있습니다 `<Name>` .

에서 `Types.ps1xml` `<PropertySet>` 태그는 개체의 기본 표시에 대 한 속성 집합을 정의 하는 데 사용 됩니다. 태그의 태그에서 **Psstandardmembers** 값으로 기본 표시를 식별할 수 있습니다 `<Name>` `<MemberSet>` .

예를 들어 다음 XML은 개체에 대 한 **상태** 속성을 만듭니다 `System.IO.DirectoryInfo` . **Status** 속성의 값은 항상 **Success** 입니다.

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
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

`<ScriptMethod>`: 값이 스크립트의 출력을 포함 하는 메서드를 정의 합니다.

태그에는 `<ScriptMethod>` `<Name>` 새 메서드의 이름을 지정 하는 태그와 `<Script>` 메서드 결과를 반환 하는 스크립트 블록을 포함 하는 태그가 있어야 합니다.

예를 들어 `ConvertToDateTime` `ConvertFromDateTime` 관리 개체 ()의 및 메서드는 `System.System.Management.ManagementObject` `ToDateTime` `ToDmtfDateTime` 클래스의 및 정적 메서드를 사용 하는 스크립트 메서드입니다 `System.Management.ManagementDateTimeConverter` .

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
 <ScriptMethod>
   <Name>ConvertFromDateTime</Name>
   <Script>
   [System.Management.ManagementDateTimeConverter]::ToDmtfDateTime($args[0])
   </Script>
 </ScriptMethod>
 </Members>
</Type>
```

`<ScriptProperty>`: 값이 스크립트의 출력 인 속성을 정의 합니다.

태그에는 `<ScriptProperty>` `<Name>` 새 속성의 이름과 `<GetScriptBlock>` 속성 값을 반환 하는 스크립트 블록을 포함 하는 태그를 지정 하는 태그가 있어야 합니다.

예를 들어 GetVersionInfo 개체의 **VersionInfo** 속성은 **FileVersionInfo** **개체의**  정적 메서드의 **FullName** 속성을 사용 하 여 생성 되는 스크립트 속성입니다.

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

자세한 내용은 [Windows POWERSHELL SDK (소프트웨어 개발 키트)](/powershell/scripting/developer/windows-powershell)를 참조 하세요.

## <a name="update-typedata"></a>Update-TypeData

`Types.ps1xml`PowerShell 세션에 파일을 로드 하려면 cmdlet을 실행 `Update-TypeData` 합니다. 파일의 형식이 기본 제공 파일의 형식 보다 우선적으로 적용 되도록 하려면 `Types.ps1xml` 의 **PrependData** 매개 변수를 추가 합니다 `Update-TypeData` . `Update-TypeData` 현재 세션에만 영향을 줍니다. 이후 모든 세션을 변경 하려면 세션을 내보내거나 `Update-TypeData` PowerShell 프로필에 명령을 추가 합니다.

속성에서 발생 하거나 명령에 속성을 추가 하 여 발생 하는 예외는 `Update-TypeData` 에 오류를 보고 하지 않습니다 `StdErr` . 이는 형식 지정 및 출력 중 많은 일반 유형에서 발생하는 예외를 표시하지 않기 위한 것입니다. .NET 속성을 가져오는 경우 다음 예제와 같이 메서드 구문을 대신 사용 하 여 예외를 제거 하는 문제를 해결할 수 있습니다.

```powershell
"hello".get_Length()
```

메서드 구문은 .NET 속성에만 사용할 수 있습니다. Cmdlet을 실행 하 여 추가 된 속성은 `Update-TypeData` 메서드 구문을 사용할 수 없습니다.

## <a name="signing-a-typesps1xml-file"></a>Types.ps1xml 파일에 서명

파일의 사용자를 보호 하려면 `Types.ps1xml` 디지털 서명을 사용 하 여 파일에 서명 하면 됩니다. 자세한 내용은 [about_Signing](about_Signing.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[about_Signing](about_Signing.md)

[Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item)

[Copy-ItemProperty](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)

[Get-TypeData](xref:Microsoft.PowerShell.Utility.Get-TypeData)

[Remove-TypeData](xref:Microsoft.PowerShell.Utility.Remove-TypeData)

[Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData)

