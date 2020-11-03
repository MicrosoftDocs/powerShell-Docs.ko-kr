---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-printer?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Printer
ms.openlocfilehash: 552ccc39cc19d625c5173df360fa20a10c6040c1
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210313"
---
# <span data-ttu-id="b0e9d-103">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="b0e9d-103">Out-Printer</span></span>

## <span data-ttu-id="b0e9d-104">개요</span><span class="sxs-lookup"><span data-stu-id="b0e9d-104">SYNOPSIS</span></span>
<span data-ttu-id="b0e9d-105">출력을 프린터로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-105">Sends output to a printer.</span></span>

## <span data-ttu-id="b0e9d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b0e9d-106">SYNTAX</span></span>

```
Out-Printer [[-Name] <String>] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="b0e9d-107">설명</span><span class="sxs-lookup"><span data-stu-id="b0e9d-107">DESCRIPTION</span></span>

<span data-ttu-id="b0e9d-108">`Out-Printer`이 cmdlet은 출력을 기본 프린터로 보내거나 다른 프린터 (지정 된 경우)로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-108">The `Out-Printer` cmdlet sends output to the default printer or to an alternate printer, if one is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="b0e9d-109">이 cmdlet은 PowerShell 7에서 다시 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-109">This cmdlet was reintroduced in PowerShell 7.</span></span> <span data-ttu-id="b0e9d-110">이 cmdlet은 Windows 데스크톱을 지 원하는 Windows 시스템 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-110">This cmdlet is only available on Windows systems that support the Windows Desktop.</span></span>

## <span data-ttu-id="b0e9d-111">예제</span><span class="sxs-lookup"><span data-stu-id="b0e9d-111">EXAMPLES</span></span>

### <span data-ttu-id="b0e9d-112">예 1-기본 프린터에 인쇄할 파일 보내기</span><span class="sxs-lookup"><span data-stu-id="b0e9d-112">Example 1 - Send a file to be printed on the default printer</span></span>

<span data-ttu-id="b0e9d-113">이 예제에서는 `Out-Printer` 에 **경로** 매개 변수가 없는 경우에도 파일을 인쇄 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-113">This example shows how to print a file, even though `Out-Printer` does not have a **Path** parameter.</span></span>

```powershell
Get-Content -Path ./readme.txt | Out-Printer
```

<span data-ttu-id="b0e9d-114">`Get-Content``readme.txt`현재 디렉터리에 있는 파일의 내용을 가져오고로 파이프 하 여 `Out-Printer` 기본 프린터로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-114">`Get-Content`gets the contents of the `readme.txt` file in the current directory and pipes it to `Out-Printer`, which sends it to the default printer.</span></span>

### <span data-ttu-id="b0e9d-115">예제 2: 원격 프린터에 문자열 인쇄</span><span class="sxs-lookup"><span data-stu-id="b0e9d-115">Example 2: Print a string to a remote printer</span></span>

<span data-ttu-id="b0e9d-116">이 예제에서는 `Hello, World` Server01의 **Prt 6B 컬러** 프린터에 인쇄 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-116">This example prints `Hello, World` to the **Prt-6B Color** printer on Server01.</span></span>

```powershell
"Hello, World" | Out-Printer -Name "\\Server01\Prt-6B Color"
```

<span data-ttu-id="b0e9d-117">**Name** 매개 변수는 기본값이 아닌 특정 프린터를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-117">The **Name** parameter selects a specific printer, rather than the default.</span></span>

### <span data-ttu-id="b0e9d-118">예제 3-기본 프린터에 도움말 항목 인쇄</span><span class="sxs-lookup"><span data-stu-id="b0e9d-118">Example 3 - Print a help topic to the default printer</span></span>

<span data-ttu-id="b0e9d-119">이 예에서는에 대 한 도움말 항목의 전체 버전을 인쇄 합니다 `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="b0e9d-119">This example prints the full version of the Help topic for `Get-CimInstance`.</span></span>

```powershell
$H = Get-Help -Full Get-CimInstance
Out-Printer -InputObject $H
```

<span data-ttu-id="b0e9d-120">`Get-Help` 에 대 한 도움말 항목의 전체 버전을 가져와서 `Get-CimInstance` 변수에 저장 합니다 `$H` .</span><span class="sxs-lookup"><span data-stu-id="b0e9d-120">`Get-Help` gets the full version of the Help topic for `Get-CimInstance` and stores it in the `$H` variable.</span></span> <span data-ttu-id="b0e9d-121">**InputObject** 매개 변수는의 값을 `$H` 에 전달 `Out-Printer` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-121">The **InputObject** parameter passes the value of `$H` to `Out-Printer`.</span></span>

## <span data-ttu-id="b0e9d-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b0e9d-122">PARAMETERS</span></span>

### <span data-ttu-id="b0e9d-123">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b0e9d-123">-InputObject</span></span>

<span data-ttu-id="b0e9d-124">프린터로 보낼 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-124">Specifies the objects to be sent to the printer.</span></span> <span data-ttu-id="b0e9d-125">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-125">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b0e9d-126">-Name</span><span class="sxs-lookup"><span data-stu-id="b0e9d-126">-Name</span></span>

<span data-ttu-id="b0e9d-127">지정 된 프린터로 출력을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-127">Sends the output to the specified printer.</span></span> <span data-ttu-id="b0e9d-128">매개 변수 이름 **이름은** 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-128">The parameter name **Name** is optional.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PrinterName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0e9d-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b0e9d-129">CommonParameters</span></span>

<span data-ttu-id="b0e9d-130">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b0e9d-131">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b0e9d-132">입력</span><span class="sxs-lookup"><span data-stu-id="b0e9d-132">INPUTS</span></span>

### <span data-ttu-id="b0e9d-133">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="b0e9d-133">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b0e9d-134">모든 개체를로 파이프 할 수 있습니다 `Out-Printer` .</span><span class="sxs-lookup"><span data-stu-id="b0e9d-134">You can pipe any object to `Out-Printer`.</span></span>

## <span data-ttu-id="b0e9d-135">출력</span><span class="sxs-lookup"><span data-stu-id="b0e9d-135">OUTPUTS</span></span>

### <span data-ttu-id="b0e9d-136">없음</span><span class="sxs-lookup"><span data-stu-id="b0e9d-136">None</span></span>

<span data-ttu-id="b0e9d-137">`Out-Printer` 는 개체를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-137">`Out-Printer` does not return any objects.</span></span>

## <span data-ttu-id="b0e9d-138">참고</span><span class="sxs-lookup"><span data-stu-id="b0e9d-138">NOTES</span></span>

<span data-ttu-id="b0e9d-139">동사를 포함 하는 cmdlet은 `Out` 개체의 형식을 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-139">The cmdlets that contain the `Out` verb do not format objects.</span></span> <span data-ttu-id="b0e9d-140">단지 렌더링 하 여 지정 된 표시 대상으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-140">They just render them and send them to the specified display destination.</span></span> <span data-ttu-id="b0e9d-141">포맷 되지 않은 개체를 cmdlet에 보내면 `Out` cmdlet이 해당 개체를 렌더링 하기 전에 형식 지정 cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-141">If you send an unformatted object to an `Out` cmdlet, the cmdlet sends it to a formatting cmdlet before rendering it.</span></span>

<span data-ttu-id="b0e9d-142">`Out-Printer` 데이터를 프린터로 보내지만 출력 개체를 파이프라인으로 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-142">`Out-Printer` sends data to the printer, but does not emit any output objects to the pipeline.</span></span> <span data-ttu-id="b0e9d-143">의 출력을로 파이프 하는 경우는 `Out-Printer` `Get-Member` 지정 된 개체가 없다는 `Get-Member` 것을 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0e9d-143">If you pipe the output of `Out-Printer` to `Get-Member`, `Get-Member` reports that no objects have been specified.</span></span>

## <span data-ttu-id="b0e9d-144">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b0e9d-144">RELATED LINKS</span></span>

[<span data-ttu-id="b0e9d-145">Out-File</span><span class="sxs-lookup"><span data-stu-id="b0e9d-145">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="b0e9d-146">Out-String</span><span class="sxs-lookup"><span data-stu-id="b0e9d-146">Out-String</span></span>](Out-String.md)
