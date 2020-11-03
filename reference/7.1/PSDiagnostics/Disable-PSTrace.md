---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: 1922824a646e52238278612d3db5ce07624aae21
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217337"
---
# <span data-ttu-id="09eb5-102">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="09eb5-102">Disable-PSTrace</span></span>

## <span data-ttu-id="09eb5-103">개요</span><span class="sxs-lookup"><span data-stu-id="09eb5-103">SYNOPSIS</span></span>
<span data-ttu-id="09eb5-104">Microsoft-Windows PowerShell 이벤트 공급자 로그를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="09eb5-104">Disables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="09eb5-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="09eb5-105">SYNTAX</span></span>

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="09eb5-106">설명</span><span class="sxs-lookup"><span data-stu-id="09eb5-106">DESCRIPTION</span></span>

<span data-ttu-id="09eb5-107">이 cmdlet은 Microsoft-Windows PowerShell 이벤트 공급자의 운영 및 분석 이벤트 로그를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="09eb5-107">This cmdlet disables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="09eb5-108">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="09eb5-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="09eb5-109">예제</span><span class="sxs-lookup"><span data-stu-id="09eb5-109">EXAMPLES</span></span>

### <span data-ttu-id="09eb5-110">예 1: PowerShell에 대 한 분석 이벤트 로그 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="09eb5-110">Example 1: Disable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="09eb5-111">다음 예에서는 Microsoft-Windows PowerShell 공급자의 분석 이벤트 로그만 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="09eb5-111">The following example disables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Disable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="09eb5-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="09eb5-112">PARAMETERS</span></span>

### <span data-ttu-id="09eb5-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="09eb5-113">-AnalyticOnly</span></span>

<span data-ttu-id="09eb5-114">이 매개 변수를 사용 하는 경우 cmdlet은 Microsoft-Windows PowerShell 공급자의 분석 이벤트 로그를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="09eb5-114">When this parameter is used, the cmdlet disables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="09eb5-115">운영 이벤트 로그는 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="09eb5-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="09eb5-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="09eb5-116">CommonParameters</span></span>
<span data-ttu-id="09eb5-117">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="09eb5-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="09eb5-118">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="09eb5-118">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="09eb5-119">입력</span><span class="sxs-lookup"><span data-stu-id="09eb5-119">INPUTS</span></span>

### <span data-ttu-id="09eb5-120">없음</span><span class="sxs-lookup"><span data-stu-id="09eb5-120">None</span></span>

## <span data-ttu-id="09eb5-121">출력</span><span class="sxs-lookup"><span data-stu-id="09eb5-121">OUTPUTS</span></span>

### <span data-ttu-id="09eb5-122">없음</span><span class="sxs-lookup"><span data-stu-id="09eb5-122">None</span></span>

## <span data-ttu-id="09eb5-123">참고</span><span class="sxs-lookup"><span data-stu-id="09eb5-123">NOTES</span></span>

<span data-ttu-id="09eb5-124">이 cmdlet은 `Get-LogProperties` 및 cmdlet을 사용 `Set-LogProperties` 합니다.</span><span class="sxs-lookup"><span data-stu-id="09eb5-124">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="09eb5-125">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="09eb5-125">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="09eb5-126">관련 링크</span><span class="sxs-lookup"><span data-stu-id="09eb5-126">RELATED LINKS</span></span>

[<span data-ttu-id="09eb5-127">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="09eb5-127">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="09eb5-128">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="09eb5-128">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="09eb5-129">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="09eb5-129">Enable-PSTrace</span></span>](Enable-PSTrace.md)

