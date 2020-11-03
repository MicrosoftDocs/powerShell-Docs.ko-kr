---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: fc58e0bcfdd0b4ee7c7ee383b44f7d7f428c34c0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213562"
---
# <span data-ttu-id="ee65d-102">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="ee65d-102">Disable-PSTrace</span></span>

## <span data-ttu-id="ee65d-103">개요</span><span class="sxs-lookup"><span data-stu-id="ee65d-103">SYNOPSIS</span></span>
<span data-ttu-id="ee65d-104">Microsoft-Windows PowerShell 이벤트 공급자 로그를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee65d-104">Disables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="ee65d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ee65d-105">SYNTAX</span></span>

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="ee65d-106">설명</span><span class="sxs-lookup"><span data-stu-id="ee65d-106">DESCRIPTION</span></span>

<span data-ttu-id="ee65d-107">이 cmdlet은 Microsoft-Windows PowerShell 이벤트 공급자의 운영 및 분석 이벤트 로그를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee65d-107">This cmdlet disables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="ee65d-108">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee65d-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="ee65d-109">예제</span><span class="sxs-lookup"><span data-stu-id="ee65d-109">EXAMPLES</span></span>

### <span data-ttu-id="ee65d-110">예 1: PowerShell에 대 한 분석 이벤트 로그 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="ee65d-110">Example 1: Disable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="ee65d-111">다음 예에서는 Microsoft-Windows PowerShell 공급자의 분석 이벤트 로그만 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee65d-111">The following example disables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Disable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="ee65d-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ee65d-112">PARAMETERS</span></span>

### <span data-ttu-id="ee65d-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="ee65d-113">-AnalyticOnly</span></span>

<span data-ttu-id="ee65d-114">이 매개 변수를 사용 하는 경우 cmdlet은 Microsoft-Windows PowerShell 공급자의 분석 이벤트 로그를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee65d-114">When this parameter is used, the cmdlet disables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="ee65d-115">운영 이벤트 로그는 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ee65d-115">The Operational event log is not changed.</span></span>

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

## <span data-ttu-id="ee65d-116">입력</span><span class="sxs-lookup"><span data-stu-id="ee65d-116">INPUTS</span></span>

### <span data-ttu-id="ee65d-117">없음</span><span class="sxs-lookup"><span data-stu-id="ee65d-117">None</span></span>

## <span data-ttu-id="ee65d-118">출력</span><span class="sxs-lookup"><span data-stu-id="ee65d-118">OUTPUTS</span></span>

### <span data-ttu-id="ee65d-119">System.Object</span><span class="sxs-lookup"><span data-stu-id="ee65d-119">System.Object</span></span>

## <span data-ttu-id="ee65d-120">참고</span><span class="sxs-lookup"><span data-stu-id="ee65d-120">NOTES</span></span>

<span data-ttu-id="ee65d-121">이 cmdlet은 `Get-LogProperties` 및 cmdlet을 사용 `Set-LogProperties` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee65d-121">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="ee65d-122">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee65d-122">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="ee65d-123">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ee65d-123">RELATED LINKS</span></span>

[<span data-ttu-id="ee65d-124">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="ee65d-124">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="ee65d-125">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="ee65d-125">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="ee65d-126">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="ee65d-126">Enable-PSTrace</span></span>](Enable-PSTrace.md)
