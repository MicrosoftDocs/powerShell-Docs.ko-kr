---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: 231c2e3d2e28463be35ff1c9d5dab5a5d958f430
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602056"
---
# <span data-ttu-id="86c15-102">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="86c15-102">Enable-PSTrace</span></span>

## <span data-ttu-id="86c15-103">개요</span><span class="sxs-lookup"><span data-stu-id="86c15-103">SYNOPSIS</span></span>
<span data-ttu-id="86c15-104">Microsoft-Windows PowerShell 이벤트 공급자 로그를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="86c15-104">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="86c15-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="86c15-105">SYNTAX</span></span>

```
Enable-PSTrace [-Force] [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="86c15-106">설명</span><span class="sxs-lookup"><span data-stu-id="86c15-106">DESCRIPTION</span></span>

<span data-ttu-id="86c15-107">이 cmdlet은 Microsoft-Windows PowerShell 이벤트 공급자의 운영 및 분석 이벤트 로그를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="86c15-107">This cmdlet enables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="86c15-108">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86c15-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="86c15-109">예제</span><span class="sxs-lookup"><span data-stu-id="86c15-109">EXAMPLES</span></span>

### <span data-ttu-id="86c15-110">예제 1: PowerShell에 대 한 분석 이벤트 로그 사용</span><span class="sxs-lookup"><span data-stu-id="86c15-110">Example 1: Enable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="86c15-111">다음 예에서는 Microsoft-Windows PowerShell 공급자의 분석 이벤트 로그만 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="86c15-111">The following example enables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Enable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="86c15-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="86c15-112">PARAMETERS</span></span>

### <span data-ttu-id="86c15-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="86c15-113">-AnalyticOnly</span></span>

<span data-ttu-id="86c15-114">이 매개 변수를 사용 하는 경우 cmdlet은 Microsoft-Windows PowerShell 공급자의 분석 이벤트 로그를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="86c15-114">When this parameter is used, the cmdlet enables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="86c15-115">운영 이벤트 로그는 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="86c15-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="86c15-116">-Force</span><span class="sxs-lookup"><span data-stu-id="86c15-116">-Force</span></span>

<span data-ttu-id="86c15-117">메시지를 표시 하지 않고 강제로 변경 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86c15-117">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="86c15-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="86c15-118">CommonParameters</span></span>
<span data-ttu-id="86c15-119">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="86c15-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="86c15-120">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86c15-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="86c15-121">입력</span><span class="sxs-lookup"><span data-stu-id="86c15-121">INPUTS</span></span>

### <span data-ttu-id="86c15-122">없음</span><span class="sxs-lookup"><span data-stu-id="86c15-122">None</span></span>

## <span data-ttu-id="86c15-123">출력</span><span class="sxs-lookup"><span data-stu-id="86c15-123">OUTPUTS</span></span>

### <span data-ttu-id="86c15-124">없음</span><span class="sxs-lookup"><span data-stu-id="86c15-124">None</span></span>

## <span data-ttu-id="86c15-125">참고</span><span class="sxs-lookup"><span data-stu-id="86c15-125">NOTES</span></span>

<span data-ttu-id="86c15-126">이 cmdlet은 `Get-LogProperties` 및 cmdlet을 사용 `Set-LogProperties` 합니다.</span><span class="sxs-lookup"><span data-stu-id="86c15-126">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="86c15-127">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86c15-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="86c15-128">관련 링크</span><span class="sxs-lookup"><span data-stu-id="86c15-128">RELATED LINKS</span></span>

[<span data-ttu-id="86c15-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="86c15-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="86c15-130">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="86c15-130">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="86c15-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="86c15-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)

