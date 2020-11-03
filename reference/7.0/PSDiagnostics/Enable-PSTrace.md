---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: fea84d9ae83eae88f9a665e8a49aaf2e6743127d
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211361"
---
# <span data-ttu-id="b8faf-102">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="b8faf-102">Enable-PSTrace</span></span>

## <span data-ttu-id="b8faf-103">개요</span><span class="sxs-lookup"><span data-stu-id="b8faf-103">SYNOPSIS</span></span>
<span data-ttu-id="b8faf-104">Microsoft-Windows PowerShell 이벤트 공급자 로그를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8faf-104">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="b8faf-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b8faf-105">SYNTAX</span></span>

```
Enable-PSTrace [-Force] [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="b8faf-106">설명</span><span class="sxs-lookup"><span data-stu-id="b8faf-106">DESCRIPTION</span></span>

<span data-ttu-id="b8faf-107">이 cmdlet은 Microsoft-Windows PowerShell 이벤트 공급자의 운영 및 분석 이벤트 로그를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8faf-107">This cmdlet enables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="b8faf-108">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8faf-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="b8faf-109">예제</span><span class="sxs-lookup"><span data-stu-id="b8faf-109">EXAMPLES</span></span>

### <span data-ttu-id="b8faf-110">예제 1: PowerShell에 대 한 분석 이벤트 로그 사용</span><span class="sxs-lookup"><span data-stu-id="b8faf-110">Example 1: Enable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="b8faf-111">다음 예에서는 Microsoft-Windows PowerShell 공급자의 분석 이벤트 로그만 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8faf-111">The following example enables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Enable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="b8faf-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b8faf-112">PARAMETERS</span></span>

### <span data-ttu-id="b8faf-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="b8faf-113">-AnalyticOnly</span></span>

<span data-ttu-id="b8faf-114">이 매개 변수를 사용 하는 경우 cmdlet은 Microsoft-Windows PowerShell 공급자의 분석 이벤트 로그를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8faf-114">When this parameter is used, the cmdlet enables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="b8faf-115">운영 이벤트 로그는 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8faf-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="b8faf-116">-Force</span><span class="sxs-lookup"><span data-stu-id="b8faf-116">-Force</span></span>

<span data-ttu-id="b8faf-117">메시지를 표시 하지 않고 강제로 변경 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8faf-117">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="b8faf-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b8faf-118">CommonParameters</span></span>
<span data-ttu-id="b8faf-119">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b8faf-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b8faf-120">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b8faf-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b8faf-121">입력</span><span class="sxs-lookup"><span data-stu-id="b8faf-121">INPUTS</span></span>

### <span data-ttu-id="b8faf-122">없음</span><span class="sxs-lookup"><span data-stu-id="b8faf-122">None</span></span>

## <span data-ttu-id="b8faf-123">출력</span><span class="sxs-lookup"><span data-stu-id="b8faf-123">OUTPUTS</span></span>

### <span data-ttu-id="b8faf-124">없음</span><span class="sxs-lookup"><span data-stu-id="b8faf-124">None</span></span>

## <span data-ttu-id="b8faf-125">참고</span><span class="sxs-lookup"><span data-stu-id="b8faf-125">NOTES</span></span>

<span data-ttu-id="b8faf-126">이 cmdlet은 `Get-LogProperties` 및 cmdlet을 사용 `Set-LogProperties` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8faf-126">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="b8faf-127">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8faf-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="b8faf-128">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b8faf-128">RELATED LINKS</span></span>

[<span data-ttu-id="b8faf-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="b8faf-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="b8faf-130">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="b8faf-130">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="b8faf-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="b8faf-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)
