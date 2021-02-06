---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: ef333edaa091e96df11a8288e9b16f133614c1e0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600440"
---
# <span data-ttu-id="efc99-102">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="efc99-102">Enable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="efc99-103">개요</span><span class="sxs-lookup"><span data-stu-id="efc99-103">SYNOPSIS</span></span>
<span data-ttu-id="efc99-104">WSMan 및 PowerShell 공급자를 사용 하 여 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc99-104">Start a logging session with the WSMan and PowerShell providers enabled.</span></span>

## <span data-ttu-id="efc99-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="efc99-105">SYNTAX</span></span>

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## <span data-ttu-id="efc99-106">설명</span><span class="sxs-lookup"><span data-stu-id="efc99-106">DESCRIPTION</span></span>

<span data-ttu-id="efc99-107">이 cmdlet은 다음 PowerShell 공급자를 사용 하 여 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc99-107">This cmdlet starts a logging session with the following PowerShell providers enabled:</span></span>

- <span data-ttu-id="efc99-108">Microsoft-Windows-PowerShell</span><span class="sxs-lookup"><span data-stu-id="efc99-108">Microsoft-Windows-PowerShell</span></span>
- <span data-ttu-id="efc99-109">Microsoft-Windows-WinRM</span><span class="sxs-lookup"><span data-stu-id="efc99-109">Microsoft-Windows-WinRM</span></span>

<span data-ttu-id="efc99-110">세션의 이름은 ' PSTrace '입니다.</span><span class="sxs-lookup"><span data-stu-id="efc99-110">The session is named 'PSTrace'.</span></span>

<span data-ttu-id="efc99-111">이 cmdlet은 cmdlet을 사용 합니다 `Start-Trace` .</span><span class="sxs-lookup"><span data-stu-id="efc99-111">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="efc99-112">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc99-112">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="efc99-113">예제</span><span class="sxs-lookup"><span data-stu-id="efc99-113">EXAMPLES</span></span>

### <span data-ttu-id="efc99-114">예제 1: 결합 된 로깅 세션 시작</span><span class="sxs-lookup"><span data-stu-id="efc99-114">Example 1: Start a combined logging session</span></span>

```powershell
Enable-PSWSManCombinedTrace
```

## <span data-ttu-id="efc99-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="efc99-115">PARAMETERS</span></span>

### <span data-ttu-id="efc99-116">-DoNotOverwriteExistingTrace</span><span class="sxs-lookup"><span data-stu-id="efc99-116">-DoNotOverwriteExistingTrace</span></span>

<span data-ttu-id="efc99-117">기본적으로 이벤트는 "$pshome \Traces\PSTrace.etl"에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="efc99-117">By default, the events are written to "$pshome\Traces\PSTrace.etl".</span></span> <span data-ttu-id="efc99-118">이 매개 변수를 사용 하는 경우 cmdlet은 "$pshome \Traces\ PSTrace_ {guid} .etl"의 고유한 파일 이름을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="efc99-118">When this parameter is used, the cmdlet creates a unique filename: "$pshome\Traces\PSTrace_{guid}.etl"</span></span>

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

### <span data-ttu-id="efc99-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="efc99-119">CommonParameters</span></span>

<span data-ttu-id="efc99-120">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="efc99-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="efc99-121">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="efc99-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="efc99-122">입력</span><span class="sxs-lookup"><span data-stu-id="efc99-122">INPUTS</span></span>

### <span data-ttu-id="efc99-123">없음</span><span class="sxs-lookup"><span data-stu-id="efc99-123">None</span></span>

## <span data-ttu-id="efc99-124">출력</span><span class="sxs-lookup"><span data-stu-id="efc99-124">OUTPUTS</span></span>

### <span data-ttu-id="efc99-125">없음</span><span class="sxs-lookup"><span data-stu-id="efc99-125">None</span></span>

## <span data-ttu-id="efc99-126">참고</span><span class="sxs-lookup"><span data-stu-id="efc99-126">NOTES</span></span>

## <span data-ttu-id="efc99-127">관련 링크</span><span class="sxs-lookup"><span data-stu-id="efc99-127">RELATED LINKS</span></span>

[<span data-ttu-id="efc99-128">이벤트 추적</span><span class="sxs-lookup"><span data-stu-id="efc99-128">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="efc99-129">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="efc99-129">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="efc99-130">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="efc99-130">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

