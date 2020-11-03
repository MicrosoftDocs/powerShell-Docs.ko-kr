---
description: PowerShell 6부터 개체의 기본 뷰는 PowerShell 소스 코드에서 정의 됩니다.  사용자 고유의 `Format.ps1xml` 파일을 만들어 개체 표시를 변경 하거나 PowerShell에서 만든 새 개체 유형에 대 한 기본 표시를 정의할 수 있습니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_format.ps1xml?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Format.ps1xml
ms.openlocfilehash: ea7a5262be912750b2a4ff6ce72060b31ccdfb8a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222313"
---
# <a name="about-formatps1xml"></a>Format.ps1xml 정보

## <a name="short-description"></a>간단한 설명

PowerShell 6부터 개체의 기본 뷰는 PowerShell 소스 코드에서 정의 됩니다.

사용자 고유의 `Format.ps1xml` 파일을 만들어 개체 표시를 변경 하거나 PowerShell에서 만든 새 개체 유형에 대 한 기본 표시를 정의할 수 있습니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell 6 부터는 기본 보기가 PowerShell 소스 코드에 정의 되어 있습니다. Powershell `Format.ps1xml` 5.1 이전 버전의 파일은 powershell 6 이상 버전에 없습니다.

Powershell 소스 코드는 PowerShell 콘솔에서 개체의 기본 표시를 정의 합니다. 사용자 고유의 `Format.ps1xml` 파일을 만들어 개체 표시를 변경 하거나 PowerShell에서 만든 새 개체 유형에 대 한 기본 표시를 정의할 수 있습니다.

PowerShell에서 개체를 표시 하면 구조화 된 서식 파일의 데이터를 사용 하 여 개체의 기본 표시를 확인 합니다. 서식 파일의 데이터는 개체가 테이블이 나 목록에서 렌더링 되는지 여부를 결정 하 고 기본적으로 표시 되는 속성을 결정 합니다.

서식 지정은 표시에만 영향을 줍니다. 파이프라인으로 전달 되는 개체 속성이 나 전달 되는 방법에는 영향을 주지 않습니다. `Format.ps1xml` 파일은 해시 테이블에 대 한 출력 형식을 사용자 지정 하는 데 사용할 수 없습니다.

`.ps1xml`서식 파일은 각 개체의 네 가지 뷰를 정의할 수 있습니다.

- 테이블
- 목록
- 넓게
- 사용자 지정

예를 들어 `Get-ChildItem` 명령의 출력이 명령으로 파이프 되 면는 `Format-List` `Format-List` 소스 코드에 정의 된 목록 뷰를 사용 하 여 파일 및 폴더 개체를 목록으로 표시 하는 방법을 결정 합니다.

서식 파일에 개체의 뷰가 두 개 이상 포함 된 경우 PowerShell은 찾은 첫 번째 뷰를 적용 합니다.

사용자 지정 파일에서 뷰는 뷰의 `Format.ps1xml` 이름을 설명 하는 XML 태그 집합, 개체를 적용할 수 있는 개체의 형식, 열 머리글 및 뷰의 본문에 표시 되는 속성에 의해 정의 됩니다. 파일의 형식은 `Format.ps1xml` 데이터가 사용자에 게 표시 되기 직전에 적용 됩니다.

## <a name="creating-new-formatps1xml-files"></a>새 Format.ps1xml 파일 만들기

기존 개체 뷰의 표시 형식을 변경 하거나 새 개체에 대 한 보기를 추가 하려면 고유한 `Format.ps1xml` 파일을 만든 다음 PowerShell 세션에 추가 합니다.

`Format.ps1xml`사용자 지정 보기를 정의 하는 파일을 만들려면 [Get formatdata](xref:Microsoft.PowerShell.Utility.Get-FormatData) 및 [Export-formatdata](xref:Microsoft.PowerShell.Utility.Export-FormatData) cmdlet을 사용 합니다. 텍스트 편집기를 사용 하 여 파일을 편집 합니다. 이 파일은의 하위 디렉터리와 같이 PowerShell에서 액세스할 수 있는 모든 디렉터리에 저장할 수 있습니다 `$HOME` .

현재 뷰의 서식을 변경 하려면 서식 파일에서 뷰를 찾은 다음 태그를 사용 하 여 보기를 변경 합니다. 새 개체 유형에 대 한 뷰를 만들려면 새 뷰를 만들거나 기존 뷰를 모델로 사용 합니다. 태그는 다음 섹션에 설명 되어 있습니다. 그런 다음 파일의 다른 모든 뷰를 삭제 하 여 파일을 검사 하는 모든 사용자가 해당 변경 내용을 명확 하 게 할 수 있습니다.

변경 내용을 저장 한 후에는 [업데이트 FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData) 를 사용 하 여 PowerShell 세션에 새 파일을 추가 합니다. 기본 제공 파일에 정의 된 보기 보다 보기가 우선적으로 적용 되도록 하려면 **PrependPath** 매개 변수를 사용 합니다. `Update-FormatData` 현재 세션에만 영향을 줍니다. 모든 이후 세션을 변경 하려면 `Update-FormatData` PowerShell 프로필에 명령을 추가 합니다.

### <a name="example-add-calendar-data-to-culture-objects"></a>예: culture 개체에 일정 데이터 추가

이 예제에서는 현재 PowerShell 세션에서 cmdlet에 의해 생성 된 문화권 개체의 형식을 변경 하는 방법을 보여 **줍니다.** `Get-Culture` 이 예제의 명령은 culture 개체의 기본 테이블 뷰 표시에 **Calendar** 속성을 추가 합니다.

시작 하려면 소스 코드 파일에서 형식 데이터를 가져오고 `Format.ps1xml` 문화권 개체의 현재 뷰를 포함 하는 파일을 만듭니다.

```powershell
Get-FormatData -TypeName System.Globalization.CultureInfo |
  Export-FormatData -Path $HOME\Format\CultureInfo.Format.ps1xml
```

`CultureInfo.Format.ps1xml`XML 또는 텍스트 편집기 (예: Visual Studio Code)에서 파일을 엽니다. 다음 XML은 **CultureInfo** 개체의 뷰를 정의 합니다.

`CultureInfo.Format.ps1xml`파일은 다음 샘플과 같이 표시 됩니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.Globalization.CultureInfo</Name>
      <ViewSelectedBy>
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
          <TableColumnHeader />
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
Update-FormatData -PrependPath $HOME\Format\CultureInfo.Format.ps1xml
```

변경을 테스트 하려면 `Get-Culture` **Calendar** 속성을 포함 하는 출력을 입력 하 고 검토 합니다.

```powershell
Get-Culture
```

```Output
LCID  Name   Calendar                                DisplayName
----  ----   --------                                -----------
1033  en-US  System.Globalization.GregorianCalendar  English (United States)
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

## <a name="tracing-formatps1xml-file-use"></a>Xml 파일 사용 추적 Format.ps1

파일 로드 또는 응용 프로그램에서 오류를 검색 하려면 `Format.ps1xml` `Trace-Command` 다음 형식 구성 요소 중 하나를 **Name** 매개 변수 값으로 사용 하 여 cmdlet을 사용 합니다.

- FormatFileLoading
- FormatViewBinding

자세한 내용은 [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) 및 [TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)을 참조 하세요.

## <a name="signing-a-formatps1xml-file"></a>Format.ps1xml 파일에 서명

파일의 사용자를 보호 하려면 `Format.ps1xml` 디지털 서명을 사용 하 여 파일에 서명 합니다. 자세한 내용은 [about_Signing](about_Signing.md)를 참조 하세요.

## <a name="sample-xml-for-a-format-table-custom-view"></a>Format-Table 사용자 지정 보기에 대 한 샘플 XML

다음 XML 샘플에서는 `Format-Table` 에서 만든 **System.io.directoryinfo** 및 **system.object** 개체에 대 한 사용자 지정 뷰를 만듭니다 `Get-ChildItem` . 사용자 지정 보기의 이름을 **mygciview** 로 지정 하 고 테이블에 **CreationTime** 열을 추가 합니다.

사용자 지정 뷰를 만들려면 `Get-FormatData` 및 cmdlet을 사용 `Export-FormatData` 하 여 파일을 생성 `.ps1xml` 합니다. 그런 다음 파일을 편집 `.ps1xml` 하 여 사용자 지정 보기에 대 한 코드를 만듭니다. `.ps1xml`PowerShell에서 액세스할 수 있는 모든 디렉터리에 파일을 저장할 수 있습니다. 예를 들어의 하위 디렉터리 `$HOME` 입니다.

파일이 만들어진 후에는 `.ps1xml` cmdlet을 사용 `Update-FormatData` 하 여 현재 PowerShell 세션에 뷰를 포함 합니다. 또는 모든 PowerShell 세션에서 보기를 사용할 수 있어야 하는 경우에는 update 명령을 PowerShell 프로필에 추가 합니다.

이 예에서는 사용자 지정 뷰에서 테이블 형식을 사용 해야 합니다. 그렇지 않으면이 `Format-Table` 실패 합니다.

`Format-Table` **View** 매개 변수와 함께 사용 하 여 사용자 지정 보기의 이름 **mygciview** 를 지정 하 고 **CreationTime** 열을 사용 하 여 테이블의 출력 형식을 지정 합니다. 명령이 실행 되는 방법에 대 한 예는 [서식 테이블](xref:Microsoft.PowerShell.Utility.Format-Table)을 참조 하십시오.

> [!NOTE]
> 소스 코드에서 서식 XML을 가져와서 사용자 지정 보기를 만들 수 있지만 원하는 결과를 얻으려면 더 많은 개발이 필요할 수 있습니다.

다음 명령에는 `Get-FormatData` 모든 로컬 서식 지정 정보가 반환 되도록 **PowerShellVersion** 매개 변수에 대 한 대체 방법이 있습니다. `-PowerShellVersion $PSVersionTable.PSVersion`특정 PowerShell 버전이 아닌를 사용 합니다.

```powershell
Get-FormatData -PowerShellVersion 5.1 -TypeName System.IO.DirectoryInfo |
   Export-FormatData -Path ./Mygciview.Format.ps1xml
Update-FormatData -AppendPath ./Mygciview.Format.ps1xml
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>mygciview</Name>
      <ViewSelectedBy>
        <TypeName>System.IO.DirectoryInfo</TypeName>
        <TypeName>System.IO.FileInfo</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>PSParentPath</PropertyName>
      </GroupBy>
      <TableControl>
        <TableHeaders>
          <TableColumnHeader>
            <Label>Mode</Label>
            <Width>7</Width>
            <Alignment>Left</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>LastWriteTime</Label>
            <Width>26</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>CreationTime</Label>
            <Width>26</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>Length</Label>
            <Width>14</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>Name</Label>
            <Alignment>Left</Alignment>
          </TableColumnHeader>
        </TableHeaders>
        <TableRowEntries>
          <TableRowEntry>
            <Wrap />
            <TableColumnItems>
              <TableColumnItem>
                <PropertyName>ModeWithoutHardLink</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>LastWriteTime</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>CreationTime</PropertyName>
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
