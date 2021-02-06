---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-default?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Default
ms.openlocfilehash: d650a9280982703e09ec22698c3848a616abb067
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601259"
---
# <span data-ttu-id="e385e-102">Out-Default</span><span class="sxs-lookup"><span data-stu-id="e385e-102">Out-Default</span></span>

## <span data-ttu-id="e385e-103">개요</span><span class="sxs-lookup"><span data-stu-id="e385e-103">SYNOPSIS</span></span>
<span data-ttu-id="e385e-104">출력을 기본 포맷터와 기본 출력 cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e385e-104">Sends the output to the default formatter and to the default output cmdlet.</span></span>

## <span data-ttu-id="e385e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e385e-105">SYNTAX</span></span>

```
Out-Default [-Transcript] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="e385e-106">설명</span><span class="sxs-lookup"><span data-stu-id="e385e-106">DESCRIPTION</span></span>

<span data-ttu-id="e385e-107">PowerShell `Out-Default` 은 모든 파이프라인의 끝에 자동으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e385e-107">PowerShell automatically adds `Out-Default` to the end of every pipeline.</span></span> <span data-ttu-id="e385e-108">`Out-Default` 개체 스트림을 서식 지정 하 고 출력 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e385e-108">`Out-Default` decides how to format and output the object stream.</span></span> <span data-ttu-id="e385e-109">개체 스트림이 문자열 스트림이 면가 `Out-Default` `Out-Host` 호스트에서 제공 하는 적절 한 api를 호출 하는에 직접 파이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="e385e-109">If the object stream is a stream of strings, `Out-Default` pipes these directly to `Out-Host` which calls the appropriate APIs provided by the host.</span></span> <span data-ttu-id="e385e-110">개체 스트림에 문자열이 없는 경우는 `Out-Default` 개체를 검사 하 여 수행할 작업을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e385e-110">If the object stream does not contain strings, `Out-Default` inspects the object to determine what to do.</span></span>
<span data-ttu-id="e385e-111">먼저 개체 유형을 확인 하 고이 개체 유형에 대해 등록 된 _뷰가_ 있는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e385e-111">First it looks at the object type and determines whether there is a registered _view_ for this object type.</span></span>

<span data-ttu-id="e385e-112">PowerShell은 `Update-FormatData` 모든 사용자가 개체 유형에 대 한 뷰를 등록할 수 있는 XML 스키마 및 메커니즘 (cmdlet)을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e385e-112">PowerShell defines XML schema and a mechanism (the `Update-FormatData` cmdlet) where anyone can register views for an object type.</span></span> <span data-ttu-id="e385e-113">모든 개체 유형에 대해 **넓은**, **목록**, **테이블** 또는 **사용자 지정** 뷰를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e385e-113">You can specify **wide**, **list**, **table**, or **custom** views for any object type.</span></span> <span data-ttu-id="e385e-114">보기는 표시할 속성과 표시 되는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e385e-114">The views specify which properties to display and how they should be displayed.</span></span> <span data-ttu-id="e385e-115">뷰가 등록 된 경우 사용할 포맷터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e385e-115">If a view is registered, it defines which formatter to use.</span></span> <span data-ttu-id="e385e-116">따라서 등록 된 뷰가 **테이블** 뷰가 면에서 개체를 `Out-Default` 로 스트리밍합니다 `Format-Table | Out-Host` .</span><span class="sxs-lookup"><span data-stu-id="e385e-116">So if the registered view is a **table** view, `Out-Default` streams the objects to `Format-Table | Out-Host`.</span></span> <span data-ttu-id="e385e-117">`Format-Table` 개체를 형식 지정 레코드의 스트림으로 변환 하 고 (뷰 정의의 데이터로 구동), `Out-Host` 형식 지정 레코드를 호스트 인터페이스에 대 한 호출로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e385e-117">`Format-Table` transforms the objects into a stream of Formatting records (driven by the data in the view definition) and `Out-Host` transforms the formatting records into calls on the Host interface.</span></span>

## <span data-ttu-id="e385e-118">예제</span><span class="sxs-lookup"><span data-stu-id="e385e-118">EXAMPLES</span></span>

### <span data-ttu-id="e385e-119">예제 1</span><span class="sxs-lookup"><span data-stu-id="e385e-119">Example 1</span></span>

<span data-ttu-id="e385e-120">이 cmdlet은 최종 사용자가 직접 실행할 수는 없지만 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e385e-120">While this cmdlet is not intended to be run directly by the end user, it can be.</span></span>

```powershell
Get-Process | Select-Object -First 5 | Out-Default
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     12     2.56       5.20       0.00    7376   0 aesm_service
     48    34.32      18.10      26.64    9320  13 AlertusDesktopAlert
     24    13.97      12.74       0.77   12656  13 ApplicationFrameHost
      8     1.79       4.41       0.00    8180   0 AppVShNotify
      9     1.99       5.07       0.19   19320  13 AppVShNotify
```

## <span data-ttu-id="e385e-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e385e-121">PARAMETERS</span></span>

### <span data-ttu-id="e385e-122">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e385e-122">-InputObject</span></span>

<span data-ttu-id="e385e-123">cmdlet에 대한 입력을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="e385e-123">Accepts input to the cmdlet.</span></span>

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

### <span data-ttu-id="e385e-124">-성적 증명서</span><span class="sxs-lookup"><span data-stu-id="e385e-124">-Transcript</span></span>

<span data-ttu-id="e385e-125">출력을 PowerShell의 기록 서비스로 보낼지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e385e-125">Determines whether the output should be sent to PowerShell's transcription services.</span></span>

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

### <span data-ttu-id="e385e-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e385e-126">CommonParameters</span></span>

<span data-ttu-id="e385e-127">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e385e-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e385e-128">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e385e-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e385e-129">입력</span><span class="sxs-lookup"><span data-stu-id="e385e-129">INPUTS</span></span>

## <span data-ttu-id="e385e-130">출력</span><span class="sxs-lookup"><span data-stu-id="e385e-130">OUTPUTS</span></span>

## <span data-ttu-id="e385e-131">참고</span><span class="sxs-lookup"><span data-stu-id="e385e-131">NOTES</span></span>

## <span data-ttu-id="e385e-132">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e385e-132">RELATED LINKS</span></span>

[<span data-ttu-id="e385e-133">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="e385e-133">Format-Custom</span></span>](../Microsoft.PowerShell.Utility/Format-Custom.md)

[<span data-ttu-id="e385e-134">Format-List</span><span class="sxs-lookup"><span data-stu-id="e385e-134">Format-List</span></span>](../Microsoft.PowerShell.Utility/Format-List.md)

[<span data-ttu-id="e385e-135">Format-Table</span><span class="sxs-lookup"><span data-stu-id="e385e-135">Format-Table</span></span>](../Microsoft.PowerShell.Utility/Format-Table.md)

[<span data-ttu-id="e385e-136">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="e385e-136">Format-Wide</span></span>](../Microsoft.PowerShell.Utility/Format-Wide.md)

[<span data-ttu-id="e385e-137">about_Format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="e385e-137">about_Format.ps1xml</span></span>](About/about_Format.ps1xml.md)

[<span data-ttu-id="e385e-138">PowerShell 서식 지정 및 출력의 작동 방식</span><span class="sxs-lookup"><span data-stu-id="e385e-138">How PowerShell Formatting and Outputting REALLY works</span></span>](https://devblogs.microsoft.com/powershell/how-powershell-formatting-and-outputting-really-works/)

