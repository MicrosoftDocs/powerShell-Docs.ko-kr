---
description: Powershell `Format.ps1xml` 의 파일은 powershell 콘솔에서 개체의 기본 표시를 정의 합니다. 사용자 고유의 `Format.ps1xml` 파일을 만들어 개체 표시를 변경 하거나 PowerShell에서 만든 새 개체 유형에 대 한 기본 표시를 정의할 수 있습니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_format.ps1xml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Format.ps1xml
ms.openlocfilehash: be88007d23ab98b9c2f707b77f9c43578ba9887b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222761"
---
# <a name="about-formatps1xml"></a>Format.ps1xml 정보

## <a name="short-description"></a>간단한 설명

Powershell `Format.ps1xml` 의 파일은 powershell 콘솔에서 개체의 기본 표시를 정의 합니다. 사용자 고유의 `Format.ps1xml` 파일을 만들어 개체 표시를 변경 하거나 PowerShell에서 만든 새 개체 유형에 대 한 기본 표시를 정의할 수 있습니다.

## <a name="long-description"></a>자세한 설명입니다.

`Format.ps1xml`Powershell의 파일은 powershell에서 개체의 기본 표시를 정의 합니다. 사용자 고유의 `Format.ps1xml` 파일을 만들어 개체 표시를 변경 하거나 PowerShell에서 만든 새 개체 유형에 대 한 기본 표시를 정의할 수 있습니다.

PowerShell에서 개체를 표시 하면 구조화 된 서식 파일의 데이터를 사용 하 여 개체의 기본 표시를 확인 합니다. 서식 파일의 데이터는 개체가 테이블이 나 목록에서 렌더링 되는지 여부를 결정 하 고 기본적으로 표시 되는 속성을 결정 합니다.

서식 지정은 표시에만 영향을 줍니다. 파이프라인으로 전달 되는 개체 속성이 나 전달 되는 방법에는 영향을 주지 않습니다. `Format.ps1xml` 파일은 해시 테이블에 대 한 출력 형식을 사용자 지정 하는 데 사용할 수 없습니다.

PowerShell에는 7 개의 서식 파일이 포함 되어 있습니다. 이러한 파일은 설치 디렉터리 ()에 있습니다 `$PSHOME` . 각 파일은 Microsoft .NET Framework 개체의 그룹 표시를 정의 합니다.

1. `Certificate.Format.ps1xml`

   X.509 인증서 및 인증서 저장소와 같은 인증서 저장소의 개체입니다.

1. `DotNetTypes.Format.ps1xml`

   CultureInfo, FileVersionInfo 및 EventLogEntry 개체와 같은 기타 .NET Framework 형식

1. `FileSystem.Format.ps1xml`

   파일 및 디렉터리와 같은 파일 시스템 개체입니다.

1. `Help.Format.ps1xml`

   세부 정보 및 전체 보기, 매개 변수 및 예제와 같은 도움말 보기

1. `PowerShellCore.Format.ps1xml`

   PowerShell 핵심 cmdlet (예: 및)에 의해 생성 된 개체 `Get-Member` `Get-History` 입니다.

1. `PowerShellTrace.Format.ps1xml`

   Cmdlet에서 생성 된 개체와 같은 추적 개체 `Trace-Command` 입니다.

1. `Registry.Format.ps1xml`

   레지스트리 개체 (예: 키 및 항목)

서식 파일은 각 개체의 네 가지 뷰를 정의할 수 있습니다.

- 테이블
- 목록
- 넓게
- 사용자 지정

예를 들어 명령 출력을 `Get-ChildItem` 명령으로 파이프 하면는 `Format-List` `Format-List` 파일의 뷰를 사용 하 여 `FileSystem.Format.ps1xml` 파일 및 폴더 개체를 목록으로 표시 하는 방법을 결정 합니다.

서식 파일에 개체의 뷰가 두 개 이상 포함 된 경우 PowerShell은 찾은 첫 번째 뷰를 적용 합니다.

파일에서 뷰는 뷰의 `Format.ps1xml` 이름을 설명 하는 XML 태그 집합, 개체를 적용할 수 있는 개체의 형식, 열 머리글 및 뷰의 본문에 표시 되는 속성에 의해 정의 됩니다. 파일의 형식은 `Format.ps1xml` 데이터가 사용자에 게 표시 되기 직전에 적용 됩니다.

## <a name="creating-new-formatps1xml-files"></a>새 Format.ps1xml 파일 만들기

`.ps1xml`PowerShell과 함께 설치 되는 파일은 서식에 스크립트 블록을 포함할 수 있으므로 변조를 방지 하기 위해 디지털로 서명 됩니다. 기존 개체 뷰의 표시 형식을 변경 하거나 새 개체에 대 한 보기를 추가 하려면 고유한 `Format.ps1xml` 파일을 만든 다음 PowerShell 세션에 추가 합니다.

새 파일을 만들려면 기존 파일을 복사 `Format.ps1xml` 합니다. 새 파일에는 아무 이름이 나 지정할 수 있지만 `.ps1xml` 파일 이름 확장명이 있어야 합니다. PowerShell에 액세스할 수 있는 모든 디렉터리에 새 파일을 저장할 수 있지만 PowerShell 설치 디렉터리 ( `$PSHOME` ) 또는 설치 디렉터리의 하위 디렉터리에 파일을 저장 하는 것이 유용 합니다.

현재 뷰의 서식을 변경 하려면 서식 파일에서 뷰를 찾은 다음 태그를 사용 하 여 보기를 변경 합니다. 새 개체 유형에 대 한 뷰를 만들려면 새 뷰를 만들거나 기존 뷰를 모델로 사용 합니다. 태그는 다음 섹션에 설명 되어 있습니다. 그런 다음 파일의 다른 모든 뷰를 삭제 하 여 파일을 검사 하는 모든 사용자가 해당 변경 내용을 명확 하 게 할 수 있습니다.

변경 내용을 저장 한 후 cmdlet을 사용 `Update-FormatData` 하 여 PowerShell 세션에 새 파일을 추가 합니다. 기본 제공 파일에 정의 된 보기 보다 보기가 우선적으로 적용 되도록 하려면 **PrependPath** 매개 변수를 사용 합니다.
`Update-FormatData` 현재 세션에만 영향을 줍니다. 모든 이후 세션을 변경 하려면 `Update-FormatData` PowerShell 프로필에 명령을 추가 합니다.

### <a name="example-adding-calendar-data-to-culture-objects"></a>예: culture 개체에 일정 데이터 추가

이 예제에서는 현재 PowerShell 세션에서 cmdlet에 의해 생성 된 문화권 개체의 형식을 변경 하는 방법을 보여 **줍니다.** `Get-Culture` 이 예제의 명령은 culture 개체의 기본 테이블 뷰 표시에 **Calendar** 속성을 추가 합니다.

첫 번째 단계는 `Format.ps1xml` culture 개체의 현재 보기를 포함 하는 파일을 찾는 것입니다. 다음 `Select-String` 명령은 파일을 찾습니다.

```powershell
$Parms = @{
  Path = "$PSHOME\*Format.ps1xml"
  Pattern = "System.Globalization.CultureInfo"
}

Select-String @Parms
```

```Output
C:\Windows\System32\WindowsPowerShell\v1.0\DotNetTypes.format.ps1xml:113:
     <Name>System.Globalization.CultureInfo</Name>
C:\Windows\System32\WindowsPowerShell\v1.0\DotNetTypes.format.ps1xml:115:
<TypeName>System.Globalization.CultureInfo</TypeName>
```

이 명령은 정의가 파일에 있음을 나타냅니다 `DotNetTypes.Format.ps1xml` .

다음 명령은 파일 내용을 새 파일인에 복사 `MyDotNetTypes.Format.ps1xml` 합니다.

```powershell
Copy-Item $PSHome\DotNetTypes.format.ps1xml MyDotNetTypes.Format.ps1xml
```

`MyDotNetTypes.Format.ps1xml`XML 또는 텍스트 편집기 (예: Visual Studio Code)에서 파일을 엽니다. **System.web** 개체 섹션을 찾습니다. 다음 XML은 **CultureInfo** 개체의 뷰를 정의 합니다. 개체에는 **TableControl** 보기만 있습니다.

```xml
<View>
  <Name>System.Globalization.CultureInfo</Name>
  <ViewSelectedBy>
    <TypeName>Deserialized.System.Globalization.CultureInfo</TypeName>
    <TypeName>System.Globalization.CultureInfo</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>16</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>16</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
            <PropertyName>LCID</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

열기 `<?xml>` , `<Configuration>` 및 `<ViewDefinitions>` 태그와 닫는 `<ViewDefinitions>` 및 `<Configuration>` 태그를 제외 하 고 파일의 나머지 부분을 삭제 합니다. 디지털 서명이 있는 경우 사용자 지정 파일에서 삭제 `Format.ps1xml` 합니다.

`MyDotNetTypes.Format.ps1xml`이제 파일이 다음 샘플과 같이 표시 됩니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Configuration>
<ViewDefinitions>
<View>
  <Name>System.Globalization.CultureInfo</Name>
  <ViewSelectedBy>
    <TypeName>Deserialized.System.Globalization.CultureInfo</TypeName>
    <TypeName>System.Globalization.CultureInfo</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>16</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>16</Width>
      </TableColumnHeader>
      <TableColumnHeader/>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
            <PropertyName>LCID</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
</ViewDefinitions>
</Configuration>
```

새 태그 집합을 추가 하 여 **Calendar** 속성의 새 열을 만듭니다 `<TableColumnHeader>` . **Calendar** 속성의 값은 long 일 수 있으므로 값으로 45 문자를 지정 `<Width>` 합니다.

```xml
<TableHeaders>
  <TableColumnHeader>
    <Width>16</Width>
  </TableColumnHeader>
  <TableColumnHeader>
    <Width>16</Width>
  </TableColumnHeader>
  <TableColumnHeader>
    <Width>45</Width>
  </TableColumnHeader>
  <TableColumnHeader/>
</TableHeaders>
```

및 태그를 사용 하 여 테이블 행에 **일정** 에 대 한 새 열 항목을 추가 합니다 `<TableColumnItem>` `<PropertyName` .

```xml
<TableRowEntries>
  <TableRowEntry>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName>LCID</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>Name</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>Calendar</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>DisplayName</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>
```

파일을 저장하고 닫습니다. `Update-FormatData`를 사용 하 여 현재 PowerShell 세션에 새 서식 파일을 추가 합니다.

이 예에서는 **PrependPath** 매개 변수를 사용 하 여 새 파일을 원래 파일 보다 우선 순위가 더 높은 순서로 만듭니다. 자세한 내용은 [업데이트 FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData)를 참조 하세요.

```powershell
Update-FormatData -PrependPath $PSHOME\MyDotNetTypes.Format.ps1xml
```

변경을 테스트 하려면 `Get-Culture` **Calendar** 속성을 포함 하는 출력을 입력 하 고 검토 합니다.

```powershell
Get-Culture
```

```Output
LCID Name  Calendar                               DisplayName
---- ----  --------                               -----------
1033 en-US System.Globalization.GregorianCalendar English (United States)
```

## <a name="the-xml-in-formatps1xml-files"></a>Format.ps1xml 파일의 XML

GitHub의 PowerShell 소스 코드 리포지토리에서 전체 스키마 정의를 [.Xsd 형식](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) 으로 찾을 수 있습니다.

각 파일의 **viewdefinitions** 섹션에는 `Format.ps1xml` `<View>` 각 뷰를 정의 하는 태그가 포함 되어 있습니다. 일반적인 `<View>` 태그는 다음 태그를 포함 합니다.

- `<Name>` 뷰의 이름을 식별 합니다.
- `<ViewSelectedBy>` 뷰가 적용 되는 개체 유형을 지정 합니다.
- `<GroupBy>` 뷰의 항목을 그룹으로 결합 하는 방법을 지정 합니다.
- `<TableControl>`,, 및에는 `<ListControl>` `<WideControl>` `<CustomControl>` 각 항목이 표시 되는 방법을 지정 하는 태그가 포함 되어 있습니다.

### <a name="viewselectedby-tag"></a>ViewSelectedBy 태그

`<ViewSelectedBy>`태그는 `<TypeName>` 뷰가 적용 되는 각 개체 유형에 대 한 태그를 포함할 수 있습니다. 또는 `<SelectionSetName>` 태그를 사용 하 여 다른 곳에 정의 된 선택 집합을 참조 하는 태그를 포함할 수 있습니다 `<SelectionSet>` .

### <a name="groupby-tag"></a>GroupBy 태그

태그에는 항목을 그룹화 하는 데 기준이 되는 `<GroupBy>` `<PropertyName>` 개체 속성을 지정 하는 태그가 포함 되어 있습니다. 또한 `<Label>` 각 그룹의 레이블로 사용할 문자열을 지정 하는 태그 또는 `<CustomControlName>` 태그를 사용 하 여 다른 곳에서 정의 된 사용자 지정 컨트롤을 참조 하는 태그를 포함 `<Control>` 합니다. 태그에는 태그 `<Control>` `<Name>` 와 태그가 포함 `<CustomControl>` 됩니다.

### <a name="tablecontroltag"></a>TableControlTag

태그에는 `<TableControl>` 일반적 `<TableHeaders>` 으로 `<TableRowEntries>` 테이블의 헤드 및 행에 대 한 서식을 정의 하는 및 태그가 포함 됩니다. 태그에는 `<TableHeaders>` 일반적으로, `<TableColumnHeader>` 및 태그가 포함 된 태그가 포함 되어 있습니다 `<Label>` `<Width>` `<Alignment>` . `<TableRowEntries>`태그에는 `<TableRowEntry>` 테이블의 각 행에 대 한 태그가 포함 되어 있습니다. 태그에는 `<TableRowEntry>` `<TableColumnItems>` `<TableColumnItem>` 행의 각 열에 대 한 태그가 포함 된 태그가 포함 되어 있습니다. 일반적으로 `<TableColumnItem>` 태그는 `<PropertyName>` 정의 된 위치에 표시 되는 개체 속성을 식별 하는 태그 또는 `<ScriptBlock>` 위치에 표시 될 결과를 계산 하는 스크립트 코드를 포함 하는 태그를 포함 합니다.

> [!NOTE]
> 계산 된 결과가 유용할 수 있는 위치에 스크립트 블록을 사용할 수도 있습니다.

태그에는 `<TableColumnItem>` `<FormatString>` 속성 또는 계산 된 결과가 표시 되는 방법을 지정 하는 태그가 포함 될 수도 있습니다.

### <a name="listcontrol-tag"></a>이 listcontrol 태그

태그에는 `<ListControl>` 일반적으로 `<ListEntries>` 태그가 포함 됩니다. 태그에 `<ListEntries>` 는 `<ListEntry>` 태그가 포함 됩니다. 태그에 `<ListEntry>` 는 `<ListItems>` 태그가 포함 됩니다. 태그는 태그를 포함 하 `<ListItems>` 는 태그를 포함 합니다 `<ListItem>` `<PropertyName>` . `<PropertyName>`태그는 목록의 지정 된 위치에 표시 되는 개체 속성을 지정 합니다. 선택 집합을 사용 하 여 뷰 선택을 정의 하는 경우 `<ListControl>` 및 `<ListEntry>` 태그는 하나 이상의 `<EntrySelectedBy>` 태그를 포함 하는 태그를 포함할 수도 있습니다 `<TypeName>` . 이러한 `<TypeName>` 태그는 태그가 표시할 개체 유형을 지정 합니다 `<ListControl>` .

### <a name="widecontrol-tag"></a>WideControl 태그

태그에는 `<WideControl>` 일반적으로 `<WideEntries>` 태그가 포함 됩니다. `<WideEntries>`태그는 하나 이상의 태그를 포함 합니다 `<WideEntry>` . 태그에는 `<WideEntry>` 일반적으로 `<PropertyName>` 뷰의 지정 된 위치에 표시할 속성을 지정 하는 태그가 포함 되어 있습니다. 태그에는 `<PropertyName>` `<FormatString>` 속성이 표시 되는 방법을 지정 하는 태그가 포함 될 수 있습니다.

### <a name="customcontrol-tag"></a>CustomControl 태그

태그를 사용 하 여 `<CustomControl>` 형식을 정의 하는 스크립트 블록을 사용할 수 있습니다. 태그에는 `<CustomControl>` 일반적으로 `<CustomEntries>` 여러 태그를 포함 하는 태그가 포함 되어 있습니다 `<CustomEntry>` . 각 `<CustomEntry>` 태그에는 `<CustomItem>` `<Text>` ,, `<Indentation>` `<ExpressionBinding>` 및 태그를 포함 하 여 보기에서 지정 된 위치의 내용과 서식을 지정 하는 다양 한 태그를 포함할 수 있는 태그가 포함 되어 있습니다 `<NewLine>` .

## <a name="default-displays-in-typesps1xml"></a>Types.ps1xml에 기본 표시

일부 기본 개체 형식의 기본 표시는 디렉터리의 파일에 정의 되어 있습니다 `Types.ps1xml` `$PSHOME` . 노드 이름은 **Psstandardmembers** 이며 하위 노드는 다음 태그 중 하나를 사용 합니다.

- `<DefaultDisplayProperty>`
- `<DefaultDisplayPropertySet>`
- `<DefaultKeyPropertySet>`

자세한 내용은 [about_Types.ps1xml](about_Types.ps1xml.md)을 참조 하세요.

## <a name="tracing-formatps1xml-file-use"></a>Xml 파일 사용 추적 Format.ps1

파일 로드 또는 응용 프로그램에서 오류를 검색 하려면 `Format.ps1xml` `Trace-Command` 다음 형식 구성 요소 중 하나를 **Name** 매개 변수 값으로 사용 하 여 cmdlet을 사용 합니다.

- FormatFileLoading
- FormatViewBinding

자세한 내용은 [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) 및 [TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)을 참조 하세요.

## <a name="signing-a-formatps1xml-file"></a>Format.ps1xml 파일에 서명

파일의 사용자를 보호 하려면 `Format.ps1xml` 디지털 서명을 사용 하 여 파일에 서명 합니다. 자세한 내용은 [about_Signing](about_Signing.md)를 참조 하세요.

## <a name="sample-xml-for-a-format-table-custom-view"></a>Format-Table 사용자 지정 보기에 대 한 샘플 XML

다음 샘플에서는 `Format-Table` 에서 만든 **System.io.directoryinfo** 및 **system.object** 개체에 대 한 사용자 지정 뷰를 만듭니다 `Get-ChildItem` . 사용자 지정 보기의 이름을 **mygciview** 로 지정 하 고 테이블에 **CreationTime** 열을 추가 합니다.

사용자 지정 보기는 `FileSystem.Format.ps1xml` PowerShell 5.1에 저장 된 파일의 편집 된 버전에서 만들어집니다 `$PSHOME` .

사용자 지정 파일을 저장 한 후에는를 `.ps1xml` 사용 `Update-FormatData` 하 여 PowerShell 세션에 뷰를 포함 합니다. 이 예에서는 사용자 지정 뷰에서 테이블 형식을 사용 해야 합니다. 그렇지 않으면이 `Format-Table` 실패 합니다.

`Format-Table` **View** 매개 변수와 함께 사용 하 여 사용자 지정 보기의 이름을 지정 하 고 테이블의 출력 형식을 지정 합니다. 명령이 실행 되는 방법에 대 한 예는 [서식 테이블](xref:Microsoft.PowerShell.Utility.Format-Table)을 참조 하십시오.

```powershell
$Parms = @{
  Path = "$PSHOME\*Format.ps1xml"
  Pattern = "System.IO.DirectoryInfo"
}
Select-String @Parms
Copy-Item $PSHome\FileSystem.format.ps1xml .\MyFileSystem.Format.ps1xml
Update-FormatData -PrependPath $PSHOME\Format\MyFileSystem.Format.ps1xml
```

> [!NOTE]
> 줄 너비 제한 내에서 XML 샘플을 맞추려면 일부 들여쓰기를 압축 하 고 코드에서 줄 바꿈을 사용 해야 했습니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Configuration>
    <SelectionSets>
        <SelectionSet>
            <Name>FileSystemTypes</Name>
            <Types>
                <TypeName>System.IO.DirectoryInfo</TypeName>
                <TypeName>System.IO.FileInfo</TypeName>
            </Types>
        </SelectionSet>
    </SelectionSets>
<Controls>
<Control>
<Name>FileSystemTypes-GroupingFormat</Name>
<CustomControl>
 <CustomEntries>
  <CustomEntry>
    <CustomItem>
    <Frame>
    <LeftIndent>4</LeftIndent>
    <CustomItem>
    <Text AssemblyName="System.Management.Automation"
    BaseName="FileSystemProviderStrings"
    ResourceId="DirectoryDisplayGrouping"/>
    <ExpressionBinding>
     <ScriptBlock>
      $_.PSParentPath.Replace("Microsoft.PowerShell.Core\FileSystem::", "")
     </ScriptBlock>
    </ExpressionBinding>
    <NewLine/>
    </CustomItem>
    </Frame>
    </CustomItem>
    </CustomEntry>
 </CustomEntries>
</CustomControl>
</Control>
</Controls>
<ViewDefinitions>
    <View>
    <Name>mygciview</Name>
    <ViewSelectedBy>
        <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <GroupBy>
      <PropertyName>PSParentPath</PropertyName>
      <CustomControlName>FileSystemTypes-GroupingFormat</CustomControlName>
    </GroupBy>
        <TableControl>
            <TableHeaders>
                <TableColumnHeader>
                    <Label>Mode</Label>
                    <Width>7</Width>
                    <Alignment>left</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>LastWriteTime</Label>
                    <Width>25</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>CreationTime</Label>
                    <Width>25</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>Length</Label>
                    <Width>14</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader/>
            </TableHeaders>
            <TableRowEntries>
                <TableRowEntry>
                    <Wrap/>
                    <TableColumnItems>
                        <TableColumnItem>
                            <PropertyName>Mode</PropertyName>
                        </TableColumnItem>
                        <TableColumnItem>
                            <ScriptBlock>
                                [String]::Format("{0,10}  {1,8}",
                                    $_.LastWriteTime.ToString("d"),
                                    $_.LastWriteTime.ToString("t"))
                            </ScriptBlock>
                        </TableColumnItem>
                        <TableColumnItem>
                            <ScriptBlock>
                                [String]::Format("{0,10}  {1,8}",
                                    $_.CreationTime.ToString("d"),
                                    $_.LastWriteTime.ToString("t"))
                            </ScriptBlock>
                        </TableColumnItem>
                        <TableColumnItem>
                        <PropertyName>Length</PropertyName>
                        </TableColumnItem>
                        <TableColumnItem>
                            <PropertyName>Name</PropertyName>
                        </TableColumnItem>
                    </TableColumnItems>
                </TableRowEntry>
            </TableRowEntries>
        </TableControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a>참고 항목

[Export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[Get-FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[형식 스키마 XML 참조](/powershell/scripting/developer/format/format-schema-xml-reference)

[Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command)

[Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[PowerShell 형식 지정 파일 작성](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
