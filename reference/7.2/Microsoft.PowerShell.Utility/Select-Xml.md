---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-xml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Xml
ms.openlocfilehash: 7686ade747345b7c770772067007b8abf13aac3d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605206"
---
# <span data-ttu-id="cb171-102">Select-Xml</span><span class="sxs-lookup"><span data-stu-id="cb171-102">Select-Xml</span></span>

## <span data-ttu-id="cb171-103">개요</span><span class="sxs-lookup"><span data-stu-id="cb171-103">SYNOPSIS</span></span>
<span data-ttu-id="cb171-104">XML 문자열 또는 문서에서 텍스트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-104">Finds text in an XML string or document.</span></span>

## <span data-ttu-id="cb171-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cb171-105">SYNTAX</span></span>

### <span data-ttu-id="cb171-106">Xml (기본값)</span><span class="sxs-lookup"><span data-stu-id="cb171-106">Xml (Default)</span></span>

```
Select-Xml [-Xml] <XmlNode[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="cb171-107">경로</span><span class="sxs-lookup"><span data-stu-id="cb171-107">Path</span></span>

```
Select-Xml [-Path] <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="cb171-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="cb171-108">LiteralPath</span></span>

```
Select-Xml -LiteralPath <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="cb171-109">콘텐츠</span><span class="sxs-lookup"><span data-stu-id="cb171-109">Content</span></span>

```
Select-Xml -Content <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

## <span data-ttu-id="cb171-110">설명</span><span class="sxs-lookup"><span data-stu-id="cb171-110">DESCRIPTION</span></span>

<span data-ttu-id="cb171-111">**Select-xml** cmdlet을 사용 하면 XPath 쿼리를 사용 하 여 xml 문자열 및 문서에서 텍스트를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-111">The **Select-Xml** cmdlet lets you use XPath queries to search for text in XML strings and documents.</span></span>
<span data-ttu-id="cb171-112">XPath 쿼리를 입력 하 고 *Content*, *Path* 또는 *xml* 매개 변수를 사용 하 여 검색할 Xml을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-112">Enter an XPath query, and use the *Content*, *Path*, or *Xml* parameter to specify the XML to be searched.</span></span>

## <span data-ttu-id="cb171-113">예제</span><span class="sxs-lookup"><span data-stu-id="cb171-113">EXAMPLES</span></span>

### <span data-ttu-id="cb171-114">예제 1: AliasProperty 노드 선택</span><span class="sxs-lookup"><span data-stu-id="cb171-114">Example 1: Select AliasProperty nodes</span></span>

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

<span data-ttu-id="cb171-115">이 예제에서는 Types.ps1xml에 있는 별칭 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-115">This example gets the alias properties in the Types.ps1xml.</span></span>
<span data-ttu-id="cb171-116">이 파일에 대한 자세한 내용은 about_Types.ps1xml을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb171-116">(For information about this file, see about_Types.ps1xml.)</span></span>

<span data-ttu-id="cb171-117">첫 번째 명령은 Types.ps1xml 파일의 경로를 $Path 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-117">The first command saves the path to the Types.ps1xml file in the $Path variable.</span></span>

<span data-ttu-id="cb171-118">두 번째 명령은 AliasProperty 노드에 대한 XML 경로를 $XPath 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-118">The second command saves the XML path to the AliasProperty node in the $XPath variable.</span></span>

<span data-ttu-id="cb171-119">세 번째 명령은 **Select-Xml** cmdlet을 사용하여 Types.ps1xml 파일에서 XPath 문으로 식별된 AliasProperty 노드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-119">The third command uses the **Select-Xml** cmdlet to get the AliasProperty nodes that are identified by the XPath statement from the Types.ps1xml file.</span></span>
<span data-ttu-id="cb171-120">이 명령은 파이프라인 연산자를 사용 하 여 AliasProperty 노드를 Select-Object cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-120">The command uses a pipeline operator to send the AliasProperty nodes to the Select-Object cmdlet.</span></span>
<span data-ttu-id="cb171-121">*ExpandProperty* 매개 변수는 **Node** 개체를 확장 하 고 해당 Name 및 ReferencedMemberName 속성을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-121">The *ExpandProperty* parameter expands the **Node** object and returns its Name and ReferencedMemberName properties.</span></span>

<span data-ttu-id="cb171-122">결과는 Types.ps1xml 파일에 있는 각 별칭 속성의 Name 및 ReferencedMemberName을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-122">The result shows the Name and ReferencedMemberName of each alias property in the Types.ps1xml file.</span></span>
<span data-ttu-id="cb171-123">예를 들어 **Length** 속성의 별칭인 **Count** 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-123">For example, there is a **Count** property that is an alias of the **Length** property.</span></span>

### <span data-ttu-id="cb171-124">예제 2: XML 문서 입력</span><span class="sxs-lookup"><span data-stu-id="cb171-124">Example 2: Input an XML document</span></span>

```
PS C:\> [xml]$Types = Get-Content $Pshome\Types.ps1xml
PS C:\> Select-Xml -Xml $Types -XPath "//MethodName"
```

<span data-ttu-id="cb171-125">이 예에서는 *xml 매개 변수* 를 사용 하 여 xml 문서를 **Select xml** cmdlet에 제공 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-125">This example shows how to use the *XML* parameter to provide an XML document to the **Select-Xml** cmdlet.</span></span>

<span data-ttu-id="cb171-126">첫 번째 명령은 Get-Content cmdlet을 사용 하 여 Types.ps1xml 파일의 내용을 가져오고 $Types 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-126">The first command uses the Get-Content cmdlet to get the content of the Types.ps1xml file and save it in the $Types variable.</span></span>
<span data-ttu-id="cb171-127">\[Xml은 \] 변수를 xml 개체로 캐스팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-127">The \[xml\] casts the variable as an XML object.</span></span>

<span data-ttu-id="cb171-128">두 번째 명령은 **Select-Xml** cmdlet을 사용하여 Types.ps1xml 파일의 MethodName 노드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-128">The second command uses the **Select-Xml** cmdlet to get the MethodName nodes in the Types.ps1xml file.</span></span>
<span data-ttu-id="cb171-129">*Xml* 매개 변수를 사용하여 $Types 변수의 XML 콘텐츠를 지정하고 *XPath* 매개 변수를 사용하여 MethodName 노드의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-129">The command uses the *Xml* parameter to specify the XML content in the $Types variable and the *XPath* parameter to specify the path to the MethodName node.</span></span>

### <span data-ttu-id="cb171-130">예제 3: PowerShell 도움말 파일 검색</span><span class="sxs-lookup"><span data-stu-id="cb171-130">Example 3: Search PowerShell Help files</span></span>

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

<span data-ttu-id="cb171-131">이 예에서는 **Select-Xml** cmdlet을 사용 하 여 PowerShell xml 기반 cmdlet 도움말 파일을 검색 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-131">This example shows how to use the **Select-Xml** cmdlet to search the PowerShell XML-based cmdlet help files.</span></span>
<span data-ttu-id="cb171-132">각 도움말 파일의 제목 역할을 하는 cmdlet 이름 및 도움말 파일의 경로를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-132">In this example, we'll search for the cmdlet name that serves as a title for each help file and the path to the help file.</span></span>

<span data-ttu-id="cb171-133">첫 번째 명령은 도움말 파일에 사용되는 XML 네임스페이스를 나타내는 해시 테이블을 만든 다음 $Namespace 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-133">The first command creates a hash table that represents the XML namespace that is used for the help files and saves it in the $Namespace variable.</span></span>

### <span data-ttu-id="cb171-134">예제 4: XML을 입력 하는 다양 한 방법</span><span class="sxs-lookup"><span data-stu-id="cb171-134">Example 4: Different ways to input XML</span></span>

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

<span data-ttu-id="cb171-135">이 예에서는 XML을 **Select xml** cmdlet으로 전송 하는 두 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-135">This example shows two different ways to send XML to the **Select-Xml** cmdlet.</span></span>

<span data-ttu-id="cb171-136">첫 번째 명령은 $Xml 변수에 XML이 들어 있는 문자열을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-136">The first command saves a here-string that contains XML in the $Xml variable.</span></span>
<span data-ttu-id="cb171-137">here-string에 대한 자세한 내용은 about_Quoting_Rules를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb171-137">(For more information about here-strings, see about_Quoting_Rules.)</span></span>

### <span data-ttu-id="cb171-138">예 5: 기본 xmlns 네임 스페이스 사용</span><span class="sxs-lookup"><span data-stu-id="cb171-138">Example 5: Use the default xmlns namespace</span></span>

```
PS C:\> $SnippetNamespace = @{snip = "http://schemas.microsoft.com/PowerShell/Snippets"}

The second command uses the **Select-Xml** cmdlet to get the content of the Title element of each snippet. It uses the *Path* parameter to specify the Snippets directory and the *Namespace* parameter to specify the namespace in the $SnippetNamespace variable. The value of the *XPath* parameter is the "snip" namespace key, a colon (:), and the name of the Title element.The command uses a pipeline operator (|) to send each **Node** property that **Select-Xml** returns to the ForEach-Object cmdlet, which gets the title in the value of the **InnerXml** property of the node.
PS C:\> Select-Xml -Path $Home\Documents\WindowsPowerShell\Snippets -Namespace $SnippetNamespace -XPath "//snip:Title" | foreach {$_.Node.Innerxml}
```

<span data-ttu-id="cb171-139">이 예에서는 기본 xmlns 네임 스페이스를 사용 하는 XML 문서에서 **Select-Xml** cmdlet을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-139">This example shows how to use the **Select-Xml** cmdlet with XML documents that use the default xmlns namespace.</span></span>
<span data-ttu-id="cb171-140">Windows PowerShell ISE 사용자 생성 조각 파일의 제목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-140">The example gets the titles of Windows PowerShell ISE user-created snippet files.</span></span>
<span data-ttu-id="cb171-141">조각에 대한 자세한 내용은 New-IseSnippet을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb171-141">For information about snippets, see New-IseSnippet.</span></span>

<span data-ttu-id="cb171-142">첫 번째 명령은 코드 조각 XML 파일에서 사용 하는 기본 네임 스페이스에 대 한 해시 테이블을 만든 다음이를 $SnippetNamespace 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-142">The first command creates a hash table for the default namespace that snippet XML files use and assigns it to the $SnippetNamespace variable.</span></span>
<span data-ttu-id="cb171-143">해시 테이블 값은 조각 XML의 XMLNS 스키마 URI입니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-143">The hash table value is the XMLNS schema URI in the snippet XML.</span></span>
<span data-ttu-id="cb171-144">해시 테이블 키 이름 캡처는 임의의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-144">The hash table key name, snip, is arbitrary.</span></span>
<span data-ttu-id="cb171-145">예약 되지 않은 이름을 사용할 수 있지만 xmlns는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-145">You can use any name that is not reserved, but you cannot use xmlns.</span></span>

## <span data-ttu-id="cb171-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cb171-146">PARAMETERS</span></span>

### <span data-ttu-id="cb171-147">-콘텐츠</span><span class="sxs-lookup"><span data-stu-id="cb171-147">-Content</span></span>

<span data-ttu-id="cb171-148">검색할 XML이 포함된 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-148">Specifies a string that contains the XML to search.</span></span>
<span data-ttu-id="cb171-149">문자열을 **선택-Xml** 로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-149">You can also pipe strings to **Select-Xml**.</span></span>

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

### <span data-ttu-id="cb171-150">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="cb171-150">-LiteralPath</span></span>

<span data-ttu-id="cb171-151">검색할 XML 파일의 경로 및 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-151">Specifies the paths and file names of the XML files to search.</span></span>
<span data-ttu-id="cb171-152">*Path* 와 달리 *LiteralPath* 매개 변수 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-152">Unlike *Path*, the value of the *LiteralPath* parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="cb171-153">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-153">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="cb171-154">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="cb171-154">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="cb171-155">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-155">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="cb171-156">-Namespace</span><span class="sxs-lookup"><span data-stu-id="cb171-156">-Namespace</span></span>

<span data-ttu-id="cb171-157">XML에서 사용되는 네임스페이스의 해시 테이블을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-157">Specifies a hash table of the namespaces used in the XML.</span></span>
<span data-ttu-id="cb171-158">@ {} 형식을 사용 \<namespaceName\>  =  \<namespaceValue\> 하십시오.</span><span class="sxs-lookup"><span data-stu-id="cb171-158">Use the format @{\<namespaceName\> = \<namespaceValue\>}.</span></span>

<span data-ttu-id="cb171-159">XML이 xmlns로 시작 하는 기본 네임 스페이스를 사용 하는 경우 네임 스페이스 이름에 대해 임의 키를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-159">When the XML uses the default namespace, which begins with xmlns, use an arbitrary key for the namespace name.</span></span>
<span data-ttu-id="cb171-160">Xmlns는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-160">You cannot use xmlns.</span></span>
<span data-ttu-id="cb171-161">XPath 문에서 각 노드 이름에 네임 스페이스 이름 및 콜론 (예://namespaceName: Node)을 접두사로 붙입니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-161">In the XPath statement, prefix each node name with the namespace name and a colon, such as //namespaceName:Node.</span></span>

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

### <span data-ttu-id="cb171-162">-Path</span><span class="sxs-lookup"><span data-stu-id="cb171-162">-Path</span></span>

<span data-ttu-id="cb171-163">검색할 XML 파일의 경로 및 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-163">Specifies the path and file names of the XML files to search.</span></span>
<span data-ttu-id="cb171-164">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-164">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="cb171-165">-Xml</span><span class="sxs-lookup"><span data-stu-id="cb171-165">-Xml</span></span>

<span data-ttu-id="cb171-166">하나 이상의 XML 노드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-166">Specifies one or more XML nodes.</span></span>

<span data-ttu-id="cb171-167">XML 문서는 XML 노드의 컬렉션으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-167">An XML document will be processed as a collection of XML nodes.</span></span>
<span data-ttu-id="cb171-168">XML 문서를 **선택 xml** 로 파이프 하면 각 문서 노드는 파이프라인을 통해 제공 되는 대로 별도로 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-168">If you pipe an XML document to **Select-Xml**, each document node will be searched separately as it comes through the pipeline.</span></span>

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

### <span data-ttu-id="cb171-169">-XPath</span><span class="sxs-lookup"><span data-stu-id="cb171-169">-XPath</span></span>

<span data-ttu-id="cb171-170">XPath 검색 쿼리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-170">Specifies an XPath search query.</span></span>
<span data-ttu-id="cb171-171">쿼리 언어는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-171">The query language is case-sensitive.</span></span>
<span data-ttu-id="cb171-172">이 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-172">This parameter is required.</span></span>

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

### <span data-ttu-id="cb171-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cb171-173">CommonParameters</span></span>

<span data-ttu-id="cb171-174">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cb171-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cb171-175">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb171-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cb171-176">입력</span><span class="sxs-lookup"><span data-stu-id="cb171-176">INPUTS</span></span>

### <span data-ttu-id="cb171-177">System.string 또는 System.Xml.Xml노드</span><span class="sxs-lookup"><span data-stu-id="cb171-177">System.String or System.Xml.XmlNode</span></span>

<span data-ttu-id="cb171-178">경로 또는 XML 노드를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-178">You can pipe a path or XML node to this cmdlet.</span></span>

## <span data-ttu-id="cb171-179">출력</span><span class="sxs-lookup"><span data-stu-id="cb171-179">OUTPUTS</span></span>

### <span data-ttu-id="cb171-180">SelectXmlInfo.</span><span class="sxs-lookup"><span data-stu-id="cb171-180">Microsoft.PowerShell.Commands.SelectXmlInfo</span></span>

## <span data-ttu-id="cb171-181">참고</span><span class="sxs-lookup"><span data-stu-id="cb171-181">NOTES</span></span>

<span data-ttu-id="cb171-182">XPath는 XML 문서의 부분을 식별하도록 설계된 표준 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="cb171-182">XPath is a standard language that is designed to identify parts of an XML document.</span></span> <span data-ttu-id="cb171-183">XPath 언어에 대 한 자세한 내용은 [이벤트 선택](/previous-versions//aa385231(v=vs.85))의 [Xpath 참조](/dotnet/standard/data/xml/select-nodes-using-xpath-navigation) 및 선택 필터 섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="cb171-183">For more information about the XPath language, see [XPath Reference](/dotnet/standard/data/xml/select-nodes-using-xpath-navigation) and the Selection Filters section of [Event Selection](/previous-versions//aa385231(v=vs.85)).</span></span>

## <span data-ttu-id="cb171-184">관련 링크</span><span class="sxs-lookup"><span data-stu-id="cb171-184">RELATED LINKS</span></span>

[<span data-ttu-id="cb171-185">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="cb171-185">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)