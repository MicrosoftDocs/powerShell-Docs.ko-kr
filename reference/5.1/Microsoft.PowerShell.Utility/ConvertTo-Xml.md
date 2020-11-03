---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-xml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Xml
ms.openlocfilehash: e5bf7d5f0574b7e1503f229d2dee11f3bcaba43a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214089"
---
# <span data-ttu-id="41149-103">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="41149-103">ConvertTo-Xml</span></span>

## <span data-ttu-id="41149-104">개요</span><span class="sxs-lookup"><span data-stu-id="41149-104">SYNOPSIS</span></span>
<span data-ttu-id="41149-105">개체의 XML 기반 표시를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="41149-105">Creates an XML-based representation of an object.</span></span>

## <span data-ttu-id="41149-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="41149-106">SYNTAX</span></span>

```
ConvertTo-Xml [-Depth <Int32>] [-InputObject] <PSObject> [-NoTypeInformation] [-As <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="41149-107">설명</span><span class="sxs-lookup"><span data-stu-id="41149-107">DESCRIPTION</span></span>

<span data-ttu-id="41149-108">`ConvertTo-Xml`Cmdlet은 하나 이상의 .net 개체에 대 한 [XML 기반](/dotnet/api/system.xml.xmldocument) 표현을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="41149-108">The `ConvertTo-Xml` cmdlet creates an [XML-based](/dotnet/api/system.xml.xmldocument) representation of one or more .NET objects.</span></span> <span data-ttu-id="41149-109">이 cmdlet을 사용 하려면 하나 이상의 개체를 cmdlet으로 파이프 하거나 **InputObject** 매개 변수를 사용 하 여 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41149-109">To use this cmdlet, pipe one or more objects to the cmdlet, or use the **InputObject** parameter to specify the object.</span></span>

<span data-ttu-id="41149-110">여러 개체를로 파이프 `ConvertTo-Xml` 하거나 **InputObject** 매개 변수를 사용 하 여 여러 개체를 전송 하는 경우는 `ConvertTo-Xml` 모든 개체의 표현을 포함 하는 단일 메모리 내 XML 문서를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="41149-110">When you pipe multiple objects to `ConvertTo-Xml` or use the **InputObject** parameter to submit multiple objects, `ConvertTo-Xml` returns a single, in-memory XML document that includes representations of all of the objects.</span></span>

<span data-ttu-id="41149-111">이 cmdlet은 결과 XML을 [export-clixml](./Export-Clixml.md) 를 사용 하 여 `Export-Clixml` 개체로 다시 가져올 수 있는 [CLI (공용 언어 인프라) xml](https://www.ecma-international.org/publications/standards/Ecma-335.htm) 파일에 저장 한다는 점을 제외 하 고는 [Import-Clixml](./Import-Clixml.md)내보내기와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="41149-111">This cmdlet is similar to [Export-Clixml](./Export-Clixml.md) except that `Export-Clixml` stores the resulting XML in a [Common Language Infrastructure(CLI) XML](https://www.ecma-international.org/publications/standards/Ecma-335.htm) file that can be reimported as objects with [Import-Clixml](./Import-Clixml.md).</span></span> <span data-ttu-id="41149-112">`ConvertTo-Xml` XML 문서의 메모리 내 표현을 반환 하므로 PowerShell에서 계속 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41149-112">`ConvertTo-Xml` returns an in-memory representation of an XML document, so you can continue to process it in PowerShell.</span></span> <span data-ttu-id="41149-113">`ConvertTo-Xml` 에는 개체를 CLI XML로 변환할 수 있는 옵션이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="41149-113">`ConvertTo-Xml` does not have an option to convert objects to CLI XML.</span></span>

## <span data-ttu-id="41149-114">예제</span><span class="sxs-lookup"><span data-stu-id="41149-114">EXAMPLES</span></span>

### <span data-ttu-id="41149-115">예제 1: 날짜를 XML로 변환</span><span class="sxs-lookup"><span data-stu-id="41149-115">Example 1: Convert a date to XML</span></span>

```
PS C:\> Get-Date | ConvertTo-Xml
```

<span data-ttu-id="41149-116">이 명령은 현재 날짜 ( **DateTime** 개체)를 XML로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="41149-116">This command converts the current date (a **DateTime** object) to XML.</span></span>

### <span data-ttu-id="41149-117">예제 2: 프로세스를 XML로 변환</span><span class="sxs-lookup"><span data-stu-id="41149-117">Example 2: Convert processes to XML</span></span>

```
PS C:\> ConvertTo-Xml -As "Document" -InputObject (Get-Process) -Depth 3
```

<span data-ttu-id="41149-118">이 명령은 컴퓨터의 모든 프로세스를 나타내는 프로세스 개체를 XML 문서로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="41149-118">This command converts the process objects that represent all of the processes on the computer into an XML document.</span></span> <span data-ttu-id="41149-119">개체는 수준 3까지 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="41149-119">The objects are expanded to a depth of three levels.</span></span>

## <span data-ttu-id="41149-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="41149-120">PARAMETERS</span></span>

### <span data-ttu-id="41149-121">-As</span><span class="sxs-lookup"><span data-stu-id="41149-121">-As</span></span>

<span data-ttu-id="41149-122">출력 형식을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="41149-122">Determines the output format.</span></span>
<span data-ttu-id="41149-123">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="41149-123">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="41149-124">문자열.</span><span class="sxs-lookup"><span data-stu-id="41149-124">String.</span></span>
<span data-ttu-id="41149-125">단일 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="41149-125">Returns a single string.</span></span>
- <span data-ttu-id="41149-126">스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="41149-126">Stream.</span></span>
<span data-ttu-id="41149-127">문자열의 배열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="41149-127">Returns an array of strings.</span></span>
- <span data-ttu-id="41149-128">문서입니다.</span><span class="sxs-lookup"><span data-stu-id="41149-128">Document.</span></span>
<span data-ttu-id="41149-129">**XmlDocument** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="41149-129">Returns an **XmlDocument** object.</span></span>

<span data-ttu-id="41149-130">기본값은 Document입니다.</span><span class="sxs-lookup"><span data-stu-id="41149-130">The default value is Document.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Stream, String, Document

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41149-131">-깊이</span><span class="sxs-lookup"><span data-stu-id="41149-131">-Depth</span></span>

<span data-ttu-id="41149-132">XML 표시에 포함되는 포함 개체 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41149-132">Specifies how many levels of contained objects are included in the XML representation.</span></span> <span data-ttu-id="41149-133">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="41149-133">The default value is 1.</span></span>

<span data-ttu-id="41149-134">예를 들어 개체의 속성에 또 개체가 포함된 경우 포함 개체 속성의 XML 표시를 저장하려면 수준을 2로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41149-134">For example, if the object's properties also contain objects, to save an XML representation of the properties of the contained objects, you must specify a depth of 2.</span></span>

<span data-ttu-id="41149-135">Types.ps1xml 파일에서 개체 유형에 대한 기본값을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41149-135">The default value can be overridden for the object type in the Types.ps1xml files.</span></span> <span data-ttu-id="41149-136">자세한 내용은 about_Types.ps1xml을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41149-136">For more information, see about_Types.ps1xml.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41149-137">-InputObject</span><span class="sxs-lookup"><span data-stu-id="41149-137">-InputObject</span></span>

<span data-ttu-id="41149-138">변환할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41149-138">Specifies the object to be converted.</span></span> <span data-ttu-id="41149-139">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="41149-139">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="41149-140">개체를 **convertto-html** 로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41149-140">You can also pipe objects to **ConvertTo-XML** .</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="41149-141">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="41149-141">-NoTypeInformation</span></span>

<span data-ttu-id="41149-142">개체 노드에서 Type 특성을 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="41149-142">Omits the Type attribute from the object nodes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41149-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="41149-143">CommonParameters</span></span>

<span data-ttu-id="41149-144">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="41149-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="41149-145">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41149-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="41149-146">입력</span><span class="sxs-lookup"><span data-stu-id="41149-146">INPUTS</span></span>

### <span data-ttu-id="41149-147">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="41149-147">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="41149-148">모든 개체를 **convertto-html** 로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41149-148">You can pipe any object to **ConvertTo-XML** .</span></span>

## <span data-ttu-id="41149-149">출력</span><span class="sxs-lookup"><span data-stu-id="41149-149">OUTPUTS</span></span>

### <span data-ttu-id="41149-150">System.string 또는 System.Xml.Xml문서</span><span class="sxs-lookup"><span data-stu-id="41149-150">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="41149-151">*As* 매개 변수 값은 **convertto-html에서** 반환 하는 개체의 유형을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41149-151">The value of the *As* parameter determines the type of object that **ConvertTo-XML** returns.</span></span>

## <span data-ttu-id="41149-152">참고</span><span class="sxs-lookup"><span data-stu-id="41149-152">NOTES</span></span>

## <span data-ttu-id="41149-153">관련 링크</span><span class="sxs-lookup"><span data-stu-id="41149-153">RELATED LINKS</span></span>

[<span data-ttu-id="41149-154">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="41149-154">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="41149-155">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="41149-155">ConvertTo-Html</span></span>](ConvertTo-Html.md)

[<span data-ttu-id="41149-156">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="41149-156">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="41149-157">가져오기-날짜</span><span class="sxs-lookup"><span data-stu-id="41149-157">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="41149-158">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="41149-158">Import-Clixml</span></span>](Import-Clixml.md)
