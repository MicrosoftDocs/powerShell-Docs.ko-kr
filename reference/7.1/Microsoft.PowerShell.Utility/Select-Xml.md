---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-xml?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Xml
ms.openlocfilehash: d744b1d151d50d95ebf359c6e1fce2cb5e206b5c
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389983"
---
# Select-Xml

## 개요
XML 문자열 또는 문서에서 텍스트를 찾습니다.

## SYNTAX

### Xml (기본값)

```
Select-Xml [-Xml] <XmlNode[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### 경로

```
Select-Xml [-Path] <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### LiteralPath

```
Select-Xml -LiteralPath <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### 콘텐츠

```
Select-Xml -Content <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

## 설명

**Select-xml** cmdlet을 사용 하면 XPath 쿼리를 사용 하 여 xml 문자열 및 문서에서 텍스트를 검색할 수 있습니다.
XPath 쿼리를 입력 하 고 *Content* , *Path* 또는 *xml* 매개 변수를 사용 하 여 검색할 Xml을 지정 합니다.

## 예제

### 예제 1: AliasProperty 노드 선택

```
PS C:\> $Path = "$Pshome\Types.ps1xml"
PS C:\> $XPath = "/Types/Type/Members/AliasProperty"
PS C:\> Select-Xml -Path $Path -XPath $Xpath | Select-Object -ExpandProperty Node
Name                 ReferencedMemberName
----                 --------------------
Count                Length
Name                 Key
Name                 ServiceName
RequiredServices     ServicesDependedOn
ProcessName          Name
Handles              Handlecount
VM                   VirtualSize
WS                   WorkingSetSize
Name                 ProcessName
Handles              Handlecount
VM                   VirtualMemorySize
WS                   WorkingSet
PM                   PagedMemorySize
NPM                  NonpagedSystemMemorySize
Name                 __Class
Namespace            ModuleName
```

이 예제에서는 Types.ps1xml에 있는 별칭 속성을 가져옵니다.
이 파일에 대한 자세한 내용은 about_Types.ps1xml을 참조하세요.

첫 번째 명령은 Types.ps1xml 파일의 경로를 $Path 변수에 저장합니다.

두 번째 명령은 AliasProperty 노드에 대한 XML 경로를 $XPath 변수에 저장합니다.

세 번째 명령은 **Select-Xml** cmdlet을 사용하여 Types.ps1xml 파일에서 XPath 문으로 식별된 AliasProperty 노드를 가져옵니다.
이 명령은 파이프라인 연산자를 사용 하 여 AliasProperty 노드를 Select-Object cmdlet으로 보냅니다.
*ExpandProperty* 매개 변수는 **Node** 개체를 확장 하 고 해당 Name 및 ReferencedMemberName 속성을 반환 합니다.

결과는 Types.ps1xml 파일에 있는 각 별칭 속성의 Name 및 ReferencedMemberName을 보여 줍니다.
예를 들어 **Length** 속성의 별칭인 **Count** 속성이 있습니다.

### 예제 2: XML 문서 입력

```
PS C:\> [xml]$Types = Get-Content $Pshome\Types.ps1xml
PS C:\> Select-Xml -Xml $Types -XPath "//MethodName"
```

이 예에서는 *xml 매개 변수* 를 사용 하 여 xml 문서를 **Select xml** cmdlet에 제공 하는 방법을 보여 줍니다.

첫 번째 명령은 Get-Content cmdlet을 사용 하 여 Types.ps1xml 파일의 내용을 가져오고 $Types 변수에 저장 합니다.
\[Xml은 \] 변수를 xml 개체로 캐스팅 합니다.

두 번째 명령은 **Select-Xml** cmdlet을 사용하여 Types.ps1xml 파일의 MethodName 노드를 가져옵니다.
*Xml* 매개 변수를 사용하여 $Types 변수의 XML 콘텐츠를 지정하고 *XPath* 매개 변수를 사용하여 MethodName 노드의 경로를 지정합니다.

### 예제 3: PowerShell 도움말 파일 검색

```
PS C:\> $Namespace = @{command = "http://schemas.microsoft.com/maml/dev/command/2004/10"; maml = "http://schemas.microsoft.com/maml/2004/10"; dev = "http://schemas.microsoft.com/maml/dev/2004/10"}

The second command saves the path to the help files in the $Path variable.If there are no help files in this path on your computer, use the Update-Help cmdlet to download the help files. For more information about Updatable Help, see about_Updatable_Help (https://go.microsoft.com/fwlink/?LinkId=235801).
PS C:\> $Path = "$Pshome\en-us\*dll-Help.xml"

The third command uses the **Select-Xml** cmdlet to search the XML for cmdlet names by finding Command:Name element anywhere in the files. It saves the results in the $Xml variable.**Select-Xml** returns a **SelectXmlInfo** object that has a Node property, which is a **System.Xml.XmlElement** object. The Node property has an InnerXML property, which contains the actual XML that is retrieved.
PS C:\> $Xml = Select-Xml -Path $Path -Namespace $Namespace -XPath "//command:name"

The fourth command sends the XML in the $Xml variable to the Format-Table cmdlet. The **Format-Table** command uses a calculated property to get the Node.InnerXML property of each object in the $Xml variable, trim the white space before and after the text, and display it in the table, along with the path to the source file.
PS C:\> $Xml | Format-Table @{Label="Name"; Expression= {($_.node.innerxml).trim()}}, Path -AutoSize

Name                    Path
----                    ----
Export-Counter          C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Get-Counter             C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Get-WinEvent            C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Import-Counter          C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Add-Computer            C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
Add-Content             C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
Checkpoint-Computer     C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
...
```

이 예에서는 **Select-Xml** cmdlet을 사용 하 여 PowerShell xml 기반 cmdlet 도움말 파일을 검색 하는 방법을 보여 줍니다.
각 도움말 파일의 제목 역할을 하는 cmdlet 이름 및 도움말 파일의 경로를 검색합니다.

첫 번째 명령은 도움말 파일에 사용되는 XML 네임스페이스를 나타내는 해시 테이블을 만든 다음 $Namespace 변수에 저장합니다.

### 예제 4: XML을 입력 하는 다양 한 방법

```
PS C:\> $Xml = @"
<?xml version="1.0" encoding="utf-8"?>
<Book>
  <projects>
    <project name="Book1" date="2009-01-20">
      <editions>
        <edition language="English">En.Book1.com</edition>
        <edition language="German">Ge.Book1.Com</edition>
        <edition language="French">Fr.Book1.com</edition>
        <edition language="Polish">Pl.Book1.com</edition>
      </editions>
    </project>
  </projects>
</Book>
"@

The second command uses the *Content* parameter of **Select-Xml** to specify the XML in the $Xml variable.
PS C:\> Select-Xml -Content $Xml -XPath "//edition" | foreach {$_.node.InnerXML}

En.Book1.com
Ge.Book1.Com
Fr.Book1.com
Pl.Book1.com

The third command is equivalent to the second. It uses a pipeline operator (|) to send the XML in the $Xml variable to the **Select-Xml** cmdlet.
PS C:\> $Xml | Select-Xml -XPath "//edition" | foreach {$_.node.InnerXML}

En.Book1.com
Ge.Book1.Com
Fr.Book1.com
Pl.Book1.com
```

이 예에서는 XML을 **Select xml** cmdlet으로 전송 하는 두 가지 방법을 보여 줍니다.

첫 번째 명령은 $Xml 변수에 XML이 들어 있는 문자열을 저장 합니다.
here-string에 대한 자세한 내용은 about_Quoting_Rules를 참조하세요.

### 예 5: 기본 xmlns 네임 스페이스 사용

```
PS C:\> $SnippetNamespace = @{snip = "http://schemas.microsoft.com/PowerShell/Snippets"}

The second command uses the **Select-Xml** cmdlet to get the content of the Title element of each snippet. It uses the *Path* parameter to specify the Snippets directory and the *Namespace* parameter to specify the namespace in the $SnippetNamespace variable. The value of the *XPath* parameter is the "snip" namespace key, a colon (:), and the name of the Title element.The command uses a pipeline operator (|) to send each **Node** property that **Select-Xml** returns to the ForEach-Object cmdlet, which gets the title in the value of the **InnerXml** property of the node.
PS C:\> Select-Xml -Path $Home\Documents\WindowsPowerShell\Snippets -Namespace $SnippetNamespace -XPath "//snip:Title" | foreach {$_.Node.Innerxml}
```

이 예에서는 기본 xmlns 네임 스페이스를 사용 하는 XML 문서에서 **Select-Xml** cmdlet을 사용 하는 방법을 보여 줍니다.
Windows PowerShell ISE 사용자 생성 조각 파일의 제목을 가져옵니다.
조각에 대한 자세한 내용은 New-IseSnippet을 참조하세요.

첫 번째 명령은 코드 조각 XML 파일에서 사용 하는 기본 네임 스페이스에 대 한 해시 테이블을 만든 다음이를 $SnippetNamespace 변수에 할당 합니다.
해시 테이블 값은 조각 XML의 XMLNS 스키마 URI입니다.
해시 테이블 키 이름 캡처는 임의의 이름입니다.
예약 되지 않은 이름을 사용할 수 있지만 xmlns는 사용할 수 없습니다.

## PARAMETERS

### -콘텐츠

검색할 XML이 포함된 문자열을 지정합니다.
문자열을 **선택-Xml** 로 파이프 할 수도 있습니다.

```yaml
Type: System.String[]
Parameter Sets: Content
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

검색할 XML 파일의 경로 및 파일 이름을 지정합니다.
*Path* 와 달리 *LiteralPath* 매개 변수 값은 입력한 대로 사용됩니다.
어떠한 문자도 와일드카드로 해석되지 않습니다.
이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.
작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Namespace

XML에서 사용되는 네임스페이스의 해시 테이블을 지정합니다.
@ {} 형식을 사용 \<namespaceName\>  =  \<namespaceValue\> 하십시오.

XML이 xmlns로 시작 하는 기본 네임 스페이스를 사용 하는 경우 네임 스페이스 이름에 대해 임의 키를 사용 합니다.
Xmlns는 사용할 수 없습니다.
XPath 문에서 각 노드 이름에 네임 스페이스 이름 및 콜론 (예://namespaceName: Node)을 접두사로 붙입니다.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

검색할 XML 파일의 경로 및 파일 이름을 지정합니다.
와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Xml

하나 이상의 XML 노드를 지정합니다.

XML 문서는 XML 노드의 컬렉션으로 처리됩니다.
XML 문서를 **선택 xml** 로 파이프 하면 각 문서 노드는 파이프라인을 통해 제공 되는 대로 별도로 검색 됩니다.

```yaml
Type: System.Xml.XmlNode[]
Parameter Sets: Xml
Aliases: Node

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -XPath

XPath 검색 쿼리를 지정합니다.
쿼리 언어는 대/소문자를 구분합니다.
이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.string 또는 System.Xml.Xml노드

경로 또는 XML 노드를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### SelectXmlInfo.

## 참고

XPath는 XML 문서의 부분을 식별하도록 설계된 표준 언어입니다. XPath 언어에 대 한 자세한 내용은 [이벤트 선택](/previous-versions//aa385231(v=vs.85))의 [Xpath 참조](/dotnet/standard/data/xml/select-nodes-using-xpath-navigation) 및 선택 필터 섹션을 참조 하십시오.

## 관련 링크

[ConvertTo-Xml](ConvertTo-Xml.md)
