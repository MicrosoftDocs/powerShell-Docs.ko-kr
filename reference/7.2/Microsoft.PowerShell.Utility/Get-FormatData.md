---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FormatData
ms.openlocfilehash: 28eab1709de12ec5d391009aacccfd4e973a8b9b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601439"
---
# <span data-ttu-id="257b0-102">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="257b0-102">Get-FormatData</span></span>

## <span data-ttu-id="257b0-103">개요</span><span class="sxs-lookup"><span data-stu-id="257b0-103">SYNOPSIS</span></span>
<span data-ttu-id="257b0-104">현재 세션에 있는 형식 지정 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="257b0-104">Gets the formatting data in the current session.</span></span>

## <span data-ttu-id="257b0-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="257b0-105">SYNTAX</span></span>

```
Get-FormatData [[-TypeName] <String[]>] [-PowerShellVersion <Version>] [<CommonParameters>]
```

## <span data-ttu-id="257b0-106">설명</span><span class="sxs-lookup"><span data-stu-id="257b0-106">DESCRIPTION</span></span>

<span data-ttu-id="257b0-107">`Get-FormatData`Cmdlet은 현재 세션의 형식 지정 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="257b0-107">The `Get-FormatData` cmdlet gets the formatting data in the current session.</span></span>

<span data-ttu-id="257b0-108">세션의 형식 지정 데이터에는 디렉터리에 있는 형식 지정 파일의 형식 지정, `Format.ps1xml` `$PSHOME` 세션으로 가져오는 모듈의 데이터 형식 지정, cmdlet을 사용 하 여 세션으로 가져오는 명령의 데이터 서식 지정 등이 포함 됩니다 `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="257b0-108">The formatting data in the session includes formatting data from `Format.ps1xml` formatting files, such as those in the `$PSHOME` directory, formatting data for modules that you import into the session, and formatting data for commands that you import into your session by using the `Import-PSSession` cmdlet.</span></span>

<span data-ttu-id="257b0-109">이 cmdlet을 사용하여 형식 지정 데이터를 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="257b0-109">You can use this cmdlet to examine the formatting data.</span></span> <span data-ttu-id="257b0-110">그런 다음 cmdlet을 사용 `Export-FormatData` 하 여 개체를 serialize 하 고 XML로 변환 하 여 파일에 저장할 수 있습니다 `Format.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="257b0-110">Then, you can use the `Export-FormatData` cmdlet to serialize the objects, convert them to XML, and save them in `Format.ps1xml` files.</span></span>

<span data-ttu-id="257b0-111">PowerShell에서 파일의 형식을 지정 하는 방법에 대 한 자세한 내용은 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="257b0-111">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="257b0-112">예제</span><span class="sxs-lookup"><span data-stu-id="257b0-112">EXAMPLES</span></span>

### <span data-ttu-id="257b0-113">예제 1: 모든 형식 지정 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="257b0-113">Example 1: Get all formatting data</span></span>

<span data-ttu-id="257b0-114">이 예에서는 세션의 모든 형식 지정 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="257b0-114">This example gets all the formatting data in the session.</span></span>

```powershell
Get-FormatData
```

### <span data-ttu-id="257b0-115">예제 2: 형식 이름으로 형식 지정 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="257b0-115">Example 2: Get formatting data by type name</span></span>

<span data-ttu-id="257b0-116">이 예제에서는 이름이로 시작 하는 형식 지정 데이터 항목을 가져옵니다 `System.Management.Automation.Cmd` .</span><span class="sxs-lookup"><span data-stu-id="257b0-116">This example gets the formatting data items whose names begin with `System.Management.Automation.Cmd`.</span></span>

```powershell
Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
```

### <span data-ttu-id="257b0-117">예제 3: 형식 지정 데이터 개체 검사</span><span class="sxs-lookup"><span data-stu-id="257b0-117">Example 3: Examine a formatting data object</span></span>

<span data-ttu-id="257b0-118">이 예제에서는 형식 지정 데이터 개체를 가져오고 해당 속성을 검사하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="257b0-118">This example shows how to get a formatting data object and examine its properties.</span></span>

```powershell
$F = Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
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

### <span data-ttu-id="257b0-119">예제 4: 형식 지정 데이터 가져오기 및 내보내기</span><span class="sxs-lookup"><span data-stu-id="257b0-119">Example 4: Get formatting data and export it</span></span>

<span data-ttu-id="257b0-120">이 예제에서는 및를 사용 하 여 `Get-FormatData` `Export-FormatData` 모듈에 의해 추가 된 서식 지정 데이터를 내보내는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="257b0-120">This example shows how to use `Get-FormatData` and `Export-FormatData` to export the formatting data that is added by a module.</span></span>

```powershell
$A = Get-FormatData
Import-Module bitstransfer
$B = Get-FormatData
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

<span data-ttu-id="257b0-121">처음 4 개 명령은 `Get-FormatData` , `Import-Module` 및 cmdlet을 사용 `Compare-Object` 하 여 **BitsTransfer** 모듈이 세션에 추가 하는 형식 유형을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="257b0-121">The first four commands use the `Get-FormatData`, `Import-Module`, and `Compare-Object` cmdlets to identify the format type that the **BitsTransfer** module adds to the session.</span></span>

<span data-ttu-id="257b0-122">다섯 번째 명령은 cmdlet을 사용 하 여 `Get-FormatData` **BitsTransfer** 모듈이 추가 하는 형식 유형을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="257b0-122">The fifth command uses the `Get-FormatData` cmdlet to get the format type that the **BitsTransfer** module adds.</span></span> <span data-ttu-id="257b0-123">파이프라인 연산자 ()를 사용 하 여 `|` 형식 형식 개체를 cmdlet으로 보냅니다 `Export-FormatData` .이 cmdlet은 다시 XML로 변환 하 여 지정 된 파일에 저장 `format.ps1xml` 합니다.</span><span class="sxs-lookup"><span data-stu-id="257b0-123">It uses a pipeline operator (`|`) to send the format type object to the `Export-FormatData` cmdlet, which converts it back to XML and saves it in the specified `format.ps1xml` file.</span></span>

<span data-ttu-id="257b0-124">마지막 명령은 파일 내용의 발췌를 표시 합니다 `format.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="257b0-124">The final command shows an excerpt of the `format.ps1xml` file content.</span></span>

### <span data-ttu-id="257b0-125">예 5: 지정 된 버전의 PowerShell을 기반으로 하 여 형식 지정 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="257b0-125">Example 5: Get formatting data based on the specified version of PowerShell</span></span>

<span data-ttu-id="257b0-126">이 예제에서는를 사용 하 여 `Get-FormatData` 지정 된 **TypeName** 및 PowerShell 버전에 대 한 형식 데이터를 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="257b0-126">This example shows how to use `Get-FormatData` to get format data for a specified **TypeName** and PowerShell version.</span></span>

```powershell
Get-FormatData -TypeName 'Microsoft.Powershell.Utility.FileHash' -PowerShellVersion $PSVersionTable.PSVersion

TypeNames                               FormatViewDefinition
---------                               --------------------
{Microsoft.Powershell.Utility.FileHash} {Microsoft.Powershell.Utility.FileHash}
```

## <span data-ttu-id="257b0-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="257b0-127">PARAMETERS</span></span>

### <span data-ttu-id="257b0-128">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="257b0-128">-PowerShellVersion</span></span>

<span data-ttu-id="257b0-129">이 cmdlet이 형식 지정 데이터에 대해 가져오는 PowerShell 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="257b0-129">Specify the version of PowerShell this cmdlet gets for the formatting data.</span></span> <span data-ttu-id="257b0-130">마침표로 구분 된 두 자리 숫자를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="257b0-130">Enter a two digit number separated by a period.</span></span>

<span data-ttu-id="257b0-131">이 매개 변수는 이전 버전의 PowerShell을 실행 하는 원격 컴퓨터에서 호환성을 개선 하기 위해 PowerShell 5.1에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="257b0-131">This parameter was added in PowerShell 5.1 to improve compatibility when remoting computers running older versions of PowerShell.</span></span>

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

### <span data-ttu-id="257b0-132">-TypeName</span><span class="sxs-lookup"><span data-stu-id="257b0-132">-TypeName</span></span>

<span data-ttu-id="257b0-133">이 cmdlet이 형식 지정 데이터에 대해 가져오는 형식 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="257b0-133">Specifies the type names that this cmdlet gets for the formatting data.</span></span>
<span data-ttu-id="257b0-134">유형 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="257b0-134">Enter the type names.</span></span>
<span data-ttu-id="257b0-135">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="257b0-135">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="257b0-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="257b0-136">CommonParameters</span></span>

<span data-ttu-id="257b0-137">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="257b0-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="257b0-138">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="257b0-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="257b0-139">입력</span><span class="sxs-lookup"><span data-stu-id="257b0-139">INPUTS</span></span>

### <span data-ttu-id="257b0-140">없음</span><span class="sxs-lookup"><span data-stu-id="257b0-140">None</span></span>

<span data-ttu-id="257b0-141">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="257b0-141">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="257b0-142">출력</span><span class="sxs-lookup"><span data-stu-id="257b0-142">OUTPUTS</span></span>

### <span data-ttu-id="257b0-143">System.web. ExtendedTypeDefinition</span><span class="sxs-lookup"><span data-stu-id="257b0-143">System.Management.Automation.ExtendedTypeDefinition</span></span>

## <span data-ttu-id="257b0-144">참고</span><span class="sxs-lookup"><span data-stu-id="257b0-144">NOTES</span></span>

## <span data-ttu-id="257b0-145">관련 링크</span><span class="sxs-lookup"><span data-stu-id="257b0-145">RELATED LINKS</span></span>

[<span data-ttu-id="257b0-146">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="257b0-146">Export-FormatData</span></span>](Export-FormatData.md)

[<span data-ttu-id="257b0-147">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="257b0-147">Update-FormatData</span></span>](Update-FormatData.md)
