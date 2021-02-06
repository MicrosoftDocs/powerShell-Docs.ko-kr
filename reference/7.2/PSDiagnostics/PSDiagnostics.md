---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: c61d6278-02a3-4618-ae37-a524d40a7f44
Module Name: PSDiagnostics
ms.date: 11/27/2018
schema: 2.0.0
title: PSDiagnostics 모듈
ms.openlocfilehash: f8426e88af9e498c484ed449c2cb1b4695c1a01c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602823"
---
# <span data-ttu-id="9198d-102">PSDiagnostics 모듈</span><span class="sxs-lookup"><span data-stu-id="9198d-102">PSDiagnostics Module</span></span>

## <span data-ttu-id="9198d-103">설명</span><span class="sxs-lookup"><span data-stu-id="9198d-103">Description</span></span>

<span data-ttu-id="9198d-104">PowerShell 진단 모듈에는 Windows의 PowerShell에서 ETW 추적을 사용할 수 있도록 하는 cmdlet 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9198d-104">The PowerShell Diagnostics Module contains a set of cmdlets that enables the use of ETW tracing in PowerShell on Windows.</span></span>

## <span data-ttu-id="9198d-105">PSDiagnostics Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9198d-105">PSDiagnostics Cmdlets</span></span>

### [<span data-ttu-id="9198d-106">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="9198d-106">Disable-PSTrace</span></span>](Disable-PSTrace.md)
<span data-ttu-id="9198d-107">Microsoft-Windows PowerShell 이벤트 공급자 로그를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9198d-107">Disables the Microsoft-Windows-PowerShell event provider logs.</span></span>

### [<span data-ttu-id="9198d-108">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="9198d-108">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)
<span data-ttu-id="9198d-109">PSWSManCombinedTrace를 사용 하 여 시작 된 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9198d-109">Stop the logging session started by Enable-PSWSManCombinedTrace.</span></span>

### [<span data-ttu-id="9198d-110">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="9198d-110">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)
<span data-ttu-id="9198d-111">-WSManTrace를 사용 하 여 시작한 WSMan 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9198d-111">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

### [<span data-ttu-id="9198d-112">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="9198d-112">Enable-PSTrace</span></span>](Enable-PSTrace.md)
<span data-ttu-id="9198d-113">Microsoft-Windows PowerShell 이벤트 공급자 로그를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9198d-113">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

### [<span data-ttu-id="9198d-114">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="9198d-114">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)
<span data-ttu-id="9198d-115">WSMan 및 PowerShell 공급자를 사용 하 여 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9198d-115">Start a logging session with the WSMan and PowerShell providers enabled.</span></span>

### [<span data-ttu-id="9198d-116">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="9198d-116">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
<span data-ttu-id="9198d-117">WSMan 공급자가 사용 하도록 설정 된 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9198d-117">Start a logging session with the WSMan providers enabled.</span></span>

### [<span data-ttu-id="9198d-118">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="9198d-118">Get-LogProperties</span></span>](Get-LogProperties.md)
<span data-ttu-id="9198d-119">Windows 이벤트 로그의 속성을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="9198d-119">Retrieves the properties of a Windows event log.</span></span>

### [<span data-ttu-id="9198d-120">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="9198d-120">Set-LogProperties</span></span>](Set-LogProperties.md)
<span data-ttu-id="9198d-121">Windows 이벤트 로그의 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="9198d-121">Changes the properties of a Windows event log.</span></span>

### [<span data-ttu-id="9198d-122">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="9198d-122">Start-Trace</span></span>](Start-Trace.md)
<span data-ttu-id="9198d-123">이벤트 추적 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9198d-123">Start an Event Trace logging session.</span></span>

### [<span data-ttu-id="9198d-124">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="9198d-124">Stop-Trace</span></span>](Stop-Trace.md)
<span data-ttu-id="9198d-125">이벤트 추적 로깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9198d-125">Stop an Event Trace logging session.</span></span>

