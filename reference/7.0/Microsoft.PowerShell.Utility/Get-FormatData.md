---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-formatdata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FormatData
ms.openlocfilehash: 22cdfce0ca9e591dfc97a6ac7ef2c1e0f0ed37ab
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210793"
---
# <span data-ttu-id="ee810-103">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="ee810-103">Get-FormatData</span></span>

## <span data-ttu-id="ee810-104">개요</span><span class="sxs-lookup"><span data-stu-id="ee810-104">SYNOPSIS</span></span>
<span data-ttu-id="ee810-105">현재 세션에 있는 형식 지정 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-105">Gets the formatting data in the current session.</span></span>

## <span data-ttu-id="ee810-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ee810-106">SYNTAX</span></span>

```
Get-FormatData [[-TypeName] <String[]>] [-PowerShellVersion <Version>] [<CommonParameters>]
```

## <span data-ttu-id="ee810-107">설명</span><span class="sxs-lookup"><span data-stu-id="ee810-107">DESCRIPTION</span></span>

<span data-ttu-id="ee810-108">`Get-FormatData`Cmdlet은 현재 세션의 형식 지정 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-108">The `Get-FormatData` cmdlet gets the formatting data in the current session.</span></span>

<span data-ttu-id="ee810-109">세션의 형식 지정 데이터에는 디렉터리에 있는 형식 지정 파일의 형식 지정, `Format.ps1xml` `$PSHOME` 세션으로 가져오는 모듈의 데이터 형식 지정, cmdlet을 사용 하 여 세션으로 가져오는 명령의 데이터 서식 지정 등이 포함 됩니다 `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="ee810-109">The formatting data in the session includes formatting data from `Format.ps1xml` formatting files, such as those in the `$PSHOME` directory, formatting data for modules that you import into the session, and formatting data for commands that you import into your session by using the `Import-PSSession` cmdlet.</span></span>

<span data-ttu-id="ee810-110">이 cmdlet을 사용하여 형식 지정 데이터를 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-110">You can use this cmdlet to examine the formatting data.</span></span> <span data-ttu-id="ee810-111">그런 다음 cmdlet을 사용 `Export-FormatData` 하 여 개체를 serialize 하 고 XML로 변환 하 여 파일에 저장할 수 있습니다 `Format.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="ee810-111">Then, you can use the `Export-FormatData` cmdlet to serialize the objects, convert them to XML, and save them in `Format.ps1xml` files.</span></span>

<span data-ttu-id="ee810-112">PowerShell에서 파일의 형식을 지정 하는 방법에 대 한 자세한 내용은 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ee810-112">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="ee810-113">예제</span><span class="sxs-lookup"><span data-stu-id="ee810-113">EXAMPLES</span></span>

### <span data-ttu-id="ee810-114">예제 1: 모든 형식 지정 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="ee810-114">Example 1: Get all formatting data</span></span>

<span data-ttu-id="ee810-115">이 예에서는 세션의 모든 형식 지정 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-115">This example gets all the formatting data in the session.</span></span>

```powershell
Get-FormatData -PowerShellVersion 5.1
```

> [!IMPORTANT]
> <span data-ttu-id="ee810-116">전체 형식 형식 지정 정보가 반환 되도록 하려면 **PowerShellVersion** `5.1` 의 로컬 호출을 사용할 때 항상 값과 함께 PowerShellVersion 매개 변수를 포함 해야 합니다 `Get-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="ee810-116">To ensure that the complete type formatting information is returned, you should always include the **PowerShellVersion** parameter with the value `5.1` when using a local invocation of `Get-FormatData`.</span></span> <span data-ttu-id="ee810-117">매개 변수와 값을 생략 하면 올바른 형식 정보를 모두 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-117">If the parameter and value are omitted, you may not get all the correct type information.</span></span>

### <span data-ttu-id="ee810-118">예제 2: 형식 이름으로 형식 지정 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="ee810-118">Example 2: Get formatting data by type name</span></span>

<span data-ttu-id="ee810-119">이 예제에서는 이름이로 시작 하는 형식 지정 데이터 항목을 가져옵니다 `System.Management.Automation.Cmd` .</span><span class="sxs-lookup"><span data-stu-id="ee810-119">This example gets the formatting data items whose names begin with `System.Management.Automation.Cmd`.</span></span>

```powershell
Get-FormatData -TypeName 'System.Management.Automation.Cmd*' -PowerShellVersion 5.1
```

### <span data-ttu-id="ee810-120">예제 3: 형식 지정 데이터 개체 검사</span><span class="sxs-lookup"><span data-stu-id="ee810-120">Example 3: Examine a formatting data object</span></span>

<span data-ttu-id="ee810-121">이 예제에서는 형식 지정 데이터 개체를 가져오고 해당 속성을 검사하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-121">This example shows how to get a formatting data object and examine its properties.</span></span>

```powershell
$F = Get-FormatData -TypeName 'System.Management.Automation.Cmd*' -PowerShellVersion 5.1
$F
```

```Output
TypeName        FormatViewDefinition
--------        --------------------
HelpInfoShort   {help , TableControl}
```

```powershell
$F.FormatViewDefinition[0].control
```

```Output
Headers          : {System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader}
Rows             : {System.Management.Automation.TableControlRow}
AutoSize         : False
HideTableHeaders : False
GroupBy          :
OutOfBand        : False
```

```powershell
$F.FormatViewDefinition[0].control.Headers
```

```Output
Label       Alignment Width
-----       --------- -----
CommandType Undefined    15
Name        Undefined    50
Version     Undefined    10
Source      Undefined     0
```

### <span data-ttu-id="ee810-122">예제 4: 형식 지정 데이터 가져오기 및 내보내기</span><span class="sxs-lookup"><span data-stu-id="ee810-122">Example 4: Get formatting data and export it</span></span>

<span data-ttu-id="ee810-123">이 예제에서는 및를 사용 하 여 `Get-FormatData` `Export-FormatData` 모듈에 의해 추가 된 서식 지정 데이터를 내보내는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-123">This example shows how to use `Get-FormatData` and `Export-FormatData` to export the formatting data that is added by a module.</span></span>

```powershell
$A = Get-FormatData -PowerShellVersion 5.1
Import-Module bitstransfer
$B = Get-FormatData -PowerShellVersion 5.1
Compare-Object $A $B
```

```Output
InputObject                                                SideIndicator
-----------                                                -------------
Microsoft.BackgroundIntelligentTransfer.Management.BitsJob =>
```

```powershell
Get-FormatData *bits* | Export-FormatData -FilePath c:\test\bits.format.ps1xml
Get-Content c:\test\bits.format.ps1xml
```

```Output
<?xml version="1.0" encoding="utf-8"?><Configuration><ViewDefinitions>
<View><Name>Microsoft.BackgroundIntelligentTransfer.Management.BitsJob</Name>
...
```

<span data-ttu-id="ee810-124">처음 4 개 명령은 `Get-FormatData` , `Import-Module` 및 cmdlet을 사용 `Compare-Object` 하 여 **BitsTransfer** 모듈이 세션에 추가 하는 형식 유형을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-124">The first four commands use the `Get-FormatData`, `Import-Module`, and `Compare-Object` cmdlets to identify the format type that the **BitsTransfer** module adds to the session.</span></span>

<span data-ttu-id="ee810-125">다섯 번째 명령은 cmdlet을 사용 하 여 `Get-FormatData` **BitsTransfer** 모듈이 추가 하는 형식 유형을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-125">The fifth command uses the `Get-FormatData` cmdlet to get the format type that the **BitsTransfer** module adds.</span></span> <span data-ttu-id="ee810-126">파이프라인 연산자 ()를 사용 하 여 `|` 형식 형식 개체를 cmdlet으로 보냅니다 `Export-FormatData` .이 cmdlet은 다시 XML로 변환 하 여 지정 된 파일에 저장 `format.ps1xml` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-126">It uses a pipeline operator (`|`) to send the format type object to the `Export-FormatData` cmdlet, which converts it back to XML and saves it in the specified `format.ps1xml` file.</span></span>

<span data-ttu-id="ee810-127">마지막 명령은 파일 내용의 발췌를 표시 합니다 `format.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="ee810-127">The final command shows an excerpt of the `format.ps1xml` file content.</span></span>

### <span data-ttu-id="ee810-128">예 5: 지정 된 버전의 PowerShell을 기반으로 하 여 형식 지정 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="ee810-128">Example 5: Get formatting data based on the specified version of PowerShell</span></span>

<span data-ttu-id="ee810-129">이 예제에서는를 사용 하 여 `Get-FormatData` 지정 된 **TypeName** 및 PowerShell 버전에 대 한 형식 데이터를 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-129">This example shows how to use `Get-FormatData` to get format data for a specified **TypeName** and PowerShell version.</span></span>

```powershell
Get-FormatData -TypeName 'Microsoft.Powershell.Utility.FileHash' -PowerShellVersion $PSVersionTable.PSVersion

TypeNames                               FormatViewDefinition
---------                               --------------------
{Microsoft.Powershell.Utility.FileHash} {Microsoft.Powershell.Utility.FileHash}
```

## <span data-ttu-id="ee810-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ee810-130">PARAMETERS</span></span>

### <span data-ttu-id="ee810-131">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="ee810-131">-PowerShellVersion</span></span>

<span data-ttu-id="ee810-132">이 cmdlet이 형식 지정 데이터에 대해 가져오는 PowerShell 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-132">Specify the version of PowerShell this cmdlet gets for the formatting data.</span></span> <span data-ttu-id="ee810-133">마침표로 구분 된 두 자리 숫자를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-133">Enter a two digit number separated by a period.</span></span>

<span data-ttu-id="ee810-134">이 매개 변수는 이전 버전의 PowerShell을 실행 하는 원격 컴퓨터에서 호환성을 개선 하기 위해 PowerShell 5.1에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-134">This parameter was added in PowerShell 5.1 to improve compatibility when remoting computers running older versions of PowerShell.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee810-135">-TypeName</span><span class="sxs-lookup"><span data-stu-id="ee810-135">-TypeName</span></span>

<span data-ttu-id="ee810-136">이 cmdlet이 형식 지정 데이터에 대해 가져오는 형식 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-136">Specifies the type names that this cmdlet gets for the formatting data.</span></span>
<span data-ttu-id="ee810-137">유형 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-137">Enter the type names.</span></span>
<span data-ttu-id="ee810-138">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-138">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="ee810-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ee810-139">CommonParameters</span></span>

<span data-ttu-id="ee810-140">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ee810-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ee810-141">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee810-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ee810-142">입력</span><span class="sxs-lookup"><span data-stu-id="ee810-142">INPUTS</span></span>

### <span data-ttu-id="ee810-143">없음</span><span class="sxs-lookup"><span data-stu-id="ee810-143">None</span></span>

<span data-ttu-id="ee810-144">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ee810-144">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="ee810-145">출력</span><span class="sxs-lookup"><span data-stu-id="ee810-145">OUTPUTS</span></span>

### <span data-ttu-id="ee810-146">System.web. ExtendedTypeDefinition</span><span class="sxs-lookup"><span data-stu-id="ee810-146">System.Management.Automation.ExtendedTypeDefinition</span></span>

## <span data-ttu-id="ee810-147">참고</span><span class="sxs-lookup"><span data-stu-id="ee810-147">NOTES</span></span>

## <span data-ttu-id="ee810-148">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ee810-148">RELATED LINKS</span></span>

[<span data-ttu-id="ee810-149">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="ee810-149">Export-FormatData</span></span>](Export-FormatData.md)

[<span data-ttu-id="ee810-150">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="ee810-150">Update-FormatData</span></span>](Update-FormatData.md)
