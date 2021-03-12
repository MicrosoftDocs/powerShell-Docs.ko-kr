---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
keywords: PowerShell
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: 3adfa4be7aae03120d2334a57c39d7e6351bcb16
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103196203"
---
# <span data-ttu-id="e74ba-103">PSReadLine 모듈</span><span class="sxs-lookup"><span data-stu-id="e74ba-103">PSReadLine Module</span></span>

## <span data-ttu-id="e74ba-104">설명</span><span class="sxs-lookup"><span data-stu-id="e74ba-104">Description</span></span>

<span data-ttu-id="e74ba-105">PSReadLine 모듈에는 PowerShell에서 명령줄 편집 환경을 사용자 지정할 수 있는 cmdlet이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e74ba-105">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="e74ba-106">PowerShell 7.1은 PSReadLine v 2.1과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e74ba-106">PowerShell 7.1 shipped with PSReadLine v2.1.</span></span> <span data-ttu-id="e74ba-107">이러한 문서는 PSReadLine v 2.1 문서입니다.</span><span class="sxs-lookup"><span data-stu-id="e74ba-107">These articles document PSReadLine v2.1.</span></span>

> [!NOTE]
> <span data-ttu-id="e74ba-108">PowerShell 7.0부터 PowerShell은 화면 판독기 프로그램이 검색 된 경우 Windows에서 PSReadLine 자동 로드를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="e74ba-108">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="e74ba-109">현재 PSReadLine은 화면 판독기에서 제대로 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e74ba-109">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="e74ba-110">Windows에서 PowerShell 7.0의 기본 렌더링 및 형식이 제대로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e74ba-110">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="e74ba-111">필요한 경우 모듈을 수동으로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e74ba-111">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="e74ba-112">PSReadLine Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e74ba-112">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="e74ba-113">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="e74ba-113">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="e74ba-114">PSReadLine의 주 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="e74ba-114">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="e74ba-115">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="e74ba-115">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="e74ba-116">PSReadLine 모듈에 대 한 바인딩된 키 함수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e74ba-116">Gets the bound key functions for the PSReadLine module.</span></span>

### [<span data-ttu-id="e74ba-117">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="e74ba-117">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="e74ba-118">구성할 수 있는 옵션의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e74ba-118">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="e74ba-119">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="e74ba-119">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="e74ba-120">이 함수는 PSReadLine의 주 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="e74ba-120">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="e74ba-121">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="e74ba-121">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="e74ba-122">키 바인딩을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e74ba-122">Removes a key binding.</span></span>

### [<span data-ttu-id="e74ba-123">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="e74ba-123">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="e74ba-124">키를 사용자 정의 또는 PSReadLine 키 처리기 함수에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="e74ba-124">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="e74ba-125">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="e74ba-125">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="e74ba-126">**Psreadline** 에서 명령줄 편집의 동작을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e74ba-126">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

