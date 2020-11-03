---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: c61d6278-02a3-4618-ae37-a524d40a7f44
Module Name: PSDiagnostics
ms.date: 11/27/2018
schema: 2.0.0
title: PSDiagnostics 모듈
ms.openlocfilehash: 47a5bff321d4d94744abe41bc4bd62568997d5a7
ms.sourcegitcommit: 3571b9e87e8881adbf7984cda46a63891039a987
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2020
ms.locfileid: "93209573"
---
# <span data-ttu-id="72a07-103">PSDiagnostics 모듈</span><span class="sxs-lookup"><span data-stu-id="72a07-103">PSDiagnostics Module</span></span>

## <span data-ttu-id="72a07-104">Description</span><span class="sxs-lookup"><span data-stu-id="72a07-104">Description</span></span>

<span data-ttu-id="72a07-105">PowerShell 진단 모듈에는 Windows의 PowerShell에서 ETW 추적을 사용할 수 있도록 하는 cmdlet 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72a07-105">The PowerShell Diagnostics Module contains a set of cmdlets that enables the use of ETW tracing in PowerShell on Windows.</span></span>

## <span data-ttu-id="72a07-106">PSDiagnostics Cmdlet</span><span class="sxs-lookup"><span data-stu-id="72a07-106">PSDiagnostics Cmdlets</span></span>

### [<span data-ttu-id="72a07-107">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="72a07-107">Disable-PSTrace</span></span>](Disable-PSTrace.md)
<span data-ttu-id="72a07-108">Microsoft-Windows PowerShell 이벤트 공급자 로그를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="72a07-108">Disables the Microsoft-Windows-PowerShell event provider logs.</span></span>

### [<span data-ttu-id="72a07-109">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="72a07-109">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)
<span data-ttu-id="72a07-110">PSWSManCombinedTrace를 사용 하 여 시작 된 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="72a07-110">Stop the logging session started by Enable-PSWSManCombinedTrace.</span></span>

### [<span data-ttu-id="72a07-111">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="72a07-111">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)
<span data-ttu-id="72a07-112">-WSManTrace를 사용 하 여 시작한 WSMan 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="72a07-112">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

### [<span data-ttu-id="72a07-113">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="72a07-113">Enable-PSTrace</span></span>](Enable-PSTrace.md)
<span data-ttu-id="72a07-114">Microsoft-Windows PowerShell 이벤트 공급자 로그를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="72a07-114">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

### [<span data-ttu-id="72a07-115">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="72a07-115">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)
<span data-ttu-id="72a07-116">WSMan 및 PowerShell 공급자를 사용 하 여 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="72a07-116">Start a logging session with the WSMan and PowerShell providers enabled.</span></span>

### [<span data-ttu-id="72a07-117">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="72a07-117">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
<span data-ttu-id="72a07-118">WSMan 공급자가 사용 하도록 설정 된 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="72a07-118">Start a logging session with the WSMan providers enabled.</span></span>

### [<span data-ttu-id="72a07-119">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="72a07-119">Get-LogProperties</span></span>](Get-LogProperties.md)
<span data-ttu-id="72a07-120">Windows 이벤트 로그의 속성을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="72a07-120">Retrieves the properties of a Windows event log.</span></span>

### [<span data-ttu-id="72a07-121">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="72a07-121">Set-LogProperties</span></span>](Set-LogProperties.md)
<span data-ttu-id="72a07-122">Windows 이벤트 로그의 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="72a07-122">Changes the properties of a Windows event log.</span></span>

### [<span data-ttu-id="72a07-123">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="72a07-123">Start-Trace</span></span>](Start-Trace.md)
<span data-ttu-id="72a07-124">이벤트 추적 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="72a07-124">Start an Event Trace logging session.</span></span>

### [<span data-ttu-id="72a07-125">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="72a07-125">Stop-Trace</span></span>](Stop-Trace.md)
<span data-ttu-id="72a07-126">이벤트 추적 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="72a07-126">Stop an Event Trace logging session.</span></span>

