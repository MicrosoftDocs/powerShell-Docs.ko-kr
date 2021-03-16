---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: 0e246a0e3737f4ed693ed31096fc76e878a4af54
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601465"
---
# <span data-ttu-id="e88d8-102">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="e88d8-102">Disable-PSTrace</span></span>

## <span data-ttu-id="e88d8-103">개요</span><span class="sxs-lookup"><span data-stu-id="e88d8-103">SYNOPSIS</span></span>
<span data-ttu-id="e88d8-104">Microsoft-Windows PowerShell 이벤트 공급자 로그를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e88d8-104">Disables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="e88d8-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e88d8-105">SYNTAX</span></span>

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="e88d8-106">설명</span><span class="sxs-lookup"><span data-stu-id="e88d8-106">DESCRIPTION</span></span>

<span data-ttu-id="e88d8-107">이 cmdlet은 Microsoft-Windows PowerShell 이벤트 공급자의 운영 및 분석 이벤트 로그를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e88d8-107">This cmdlet disables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="e88d8-108">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e88d8-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="e88d8-109">예제</span><span class="sxs-lookup"><span data-stu-id="e88d8-109">EXAMPLES</span></span>

### <span data-ttu-id="e88d8-110">예 1: PowerShell에 대 한 분석 이벤트 로그 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="e88d8-110">Example 1: Disable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="e88d8-111">다음 예에서는 Microsoft-Windows PowerShell 공급자의 분석 이벤트 로그만 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e88d8-111">The following example disables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Disable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="e88d8-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e88d8-112">PARAMETERS</span></span>

### <span data-ttu-id="e88d8-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="e88d8-113">-AnalyticOnly</span></span>

<span data-ttu-id="e88d8-114">이 매개 변수를 사용 하는 경우 cmdlet은 Microsoft-Windows PowerShell 공급자의 분석 이벤트 로그를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e88d8-114">When this parameter is used, the cmdlet disables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="e88d8-115">운영 이벤트 로그는 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e88d8-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="e88d8-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e88d8-116">CommonParameters</span></span>
<span data-ttu-id="e88d8-117">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e88d8-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e88d8-118">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e88d8-118">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e88d8-119">입력</span><span class="sxs-lookup"><span data-stu-id="e88d8-119">INPUTS</span></span>

### <span data-ttu-id="e88d8-120">없음</span><span class="sxs-lookup"><span data-stu-id="e88d8-120">None</span></span>

## <span data-ttu-id="e88d8-121">출력</span><span class="sxs-lookup"><span data-stu-id="e88d8-121">OUTPUTS</span></span>

### <span data-ttu-id="e88d8-122">없음</span><span class="sxs-lookup"><span data-stu-id="e88d8-122">None</span></span>

## <span data-ttu-id="e88d8-123">참고</span><span class="sxs-lookup"><span data-stu-id="e88d8-123">NOTES</span></span>

<span data-ttu-id="e88d8-124">이 cmdlet은 `Get-LogProperties` 및 cmdlet을 사용 `Set-LogProperties` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e88d8-124">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="e88d8-125">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e88d8-125">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="e88d8-126">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e88d8-126">RELATED LINKS</span></span>

[<span data-ttu-id="e88d8-127">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="e88d8-127">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="e88d8-128">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="e88d8-128">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="e88d8-129">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="e88d8-129">Enable-PSTrace</span></span>](Enable-PSTrace.md)
