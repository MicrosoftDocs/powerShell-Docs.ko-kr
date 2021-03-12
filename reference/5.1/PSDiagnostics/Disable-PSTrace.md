---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: 50d4118c5805a59d291d8dd17f467e7b47d34b46
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194514"
---
# <span data-ttu-id="d9bff-102">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="d9bff-102">Disable-PSTrace</span></span>

## <span data-ttu-id="d9bff-103">개요</span><span class="sxs-lookup"><span data-stu-id="d9bff-103">SYNOPSIS</span></span>
<span data-ttu-id="d9bff-104">Microsoft-Windows PowerShell 이벤트 공급자 로그를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9bff-104">Disables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="d9bff-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d9bff-105">SYNTAX</span></span>

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="d9bff-106">설명</span><span class="sxs-lookup"><span data-stu-id="d9bff-106">DESCRIPTION</span></span>

<span data-ttu-id="d9bff-107">이 cmdlet은 Microsoft-Windows PowerShell 이벤트 공급자의 운영 및 분석 이벤트 로그를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9bff-107">This cmdlet disables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="d9bff-108">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9bff-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="d9bff-109">예제</span><span class="sxs-lookup"><span data-stu-id="d9bff-109">EXAMPLES</span></span>

### <span data-ttu-id="d9bff-110">예 1: PowerShell에 대 한 분석 이벤트 로그 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="d9bff-110">Example 1: Disable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="d9bff-111">다음 예에서는 Microsoft-Windows PowerShell 공급자의 분석 이벤트 로그만 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9bff-111">The following example disables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Disable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="d9bff-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d9bff-112">PARAMETERS</span></span>

### <span data-ttu-id="d9bff-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="d9bff-113">-AnalyticOnly</span></span>

<span data-ttu-id="d9bff-114">이 매개 변수를 사용 하는 경우 cmdlet은 Microsoft-Windows PowerShell 공급자의 분석 이벤트 로그를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9bff-114">When this parameter is used, the cmdlet disables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="d9bff-115">운영 이벤트 로그는 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d9bff-115">The Operational event log is not changed.</span></span>

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

## <span data-ttu-id="d9bff-116">입력</span><span class="sxs-lookup"><span data-stu-id="d9bff-116">INPUTS</span></span>

### <span data-ttu-id="d9bff-117">None</span><span class="sxs-lookup"><span data-stu-id="d9bff-117">None</span></span>

## <span data-ttu-id="d9bff-118">출력</span><span class="sxs-lookup"><span data-stu-id="d9bff-118">OUTPUTS</span></span>

### <span data-ttu-id="d9bff-119">System.Object</span><span class="sxs-lookup"><span data-stu-id="d9bff-119">System.Object</span></span>

## <span data-ttu-id="d9bff-120">참고</span><span class="sxs-lookup"><span data-stu-id="d9bff-120">NOTES</span></span>

<span data-ttu-id="d9bff-121">이 cmdlet은 `Get-LogProperties` 및 cmdlet을 사용 `Set-LogProperties` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9bff-121">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="d9bff-122">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9bff-122">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="d9bff-123">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d9bff-123">RELATED LINKS</span></span>

[<span data-ttu-id="d9bff-124">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="d9bff-124">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="d9bff-125">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="d9bff-125">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="d9bff-126">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="d9bff-126">Enable-PSTrace</span></span>](Enable-PSTrace.md)
