---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: 9abc91086d42ec7b813695e241820947f7fb0acc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213545"
---
# <span data-ttu-id="20599-102">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="20599-102">Enable-PSTrace</span></span>

## <span data-ttu-id="20599-103">개요</span><span class="sxs-lookup"><span data-stu-id="20599-103">SYNOPSIS</span></span>
<span data-ttu-id="20599-104">Microsoft-Windows PowerShell 이벤트 공급자 로그를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20599-104">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="20599-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="20599-105">SYNTAX</span></span>

```
Enable-PSTrace [-Force] [-AnalyticOnly]
```

## <span data-ttu-id="20599-106">설명</span><span class="sxs-lookup"><span data-stu-id="20599-106">DESCRIPTION</span></span>

<span data-ttu-id="20599-107">이 cmdlet은 Microsoft-Windows PowerShell 이벤트 공급자의 운영 및 분석 이벤트 로그를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20599-107">This cmdlet enables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="20599-108">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20599-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="20599-109">예제</span><span class="sxs-lookup"><span data-stu-id="20599-109">EXAMPLES</span></span>

### <span data-ttu-id="20599-110">예제 1: PowerShell에 대 한 분석 이벤트 로그 사용</span><span class="sxs-lookup"><span data-stu-id="20599-110">Example 1: Enable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="20599-111">다음 예에서는 Microsoft-Windows PowerShell 공급자의 분석 이벤트 로그만 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20599-111">The following example enables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Enable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="20599-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="20599-112">PARAMETERS</span></span>

### <span data-ttu-id="20599-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="20599-113">-AnalyticOnly</span></span>

<span data-ttu-id="20599-114">이 매개 변수를 사용 하는 경우 cmdlet은 Microsoft-Windows PowerShell 공급자의 분석 이벤트 로그를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20599-114">When this parameter is used, the cmdlet enables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="20599-115">운영 이벤트 로그는 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="20599-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="20599-116">-Force</span><span class="sxs-lookup"><span data-stu-id="20599-116">-Force</span></span>

<span data-ttu-id="20599-117">메시지를 표시 하지 않고 강제로 변경 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="20599-117">Used to force the change without prompting.</span></span>

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

## <span data-ttu-id="20599-118">입력</span><span class="sxs-lookup"><span data-stu-id="20599-118">INPUTS</span></span>

### <span data-ttu-id="20599-119">없음</span><span class="sxs-lookup"><span data-stu-id="20599-119">None</span></span>

## <span data-ttu-id="20599-120">출력</span><span class="sxs-lookup"><span data-stu-id="20599-120">OUTPUTS</span></span>

### <span data-ttu-id="20599-121">System.Object</span><span class="sxs-lookup"><span data-stu-id="20599-121">System.Object</span></span>

## <span data-ttu-id="20599-122">참고</span><span class="sxs-lookup"><span data-stu-id="20599-122">NOTES</span></span>

<span data-ttu-id="20599-123">이 cmdlet은 `Get-LogProperties` 및 cmdlet을 사용 `Set-LogProperties` 합니다.</span><span class="sxs-lookup"><span data-stu-id="20599-123">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="20599-124">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20599-124">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="20599-125">관련 링크</span><span class="sxs-lookup"><span data-stu-id="20599-125">RELATED LINKS</span></span>

[<span data-ttu-id="20599-126">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="20599-126">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="20599-127">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="20599-127">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="20599-128">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="20599-128">Disable-PSTrace</span></span>](Disable-PSTrace.md)
