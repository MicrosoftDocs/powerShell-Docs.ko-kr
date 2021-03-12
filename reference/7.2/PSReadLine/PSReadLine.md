---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: 9425f72ce4002fa871ef6b687d76f92ddf6b489e
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103193904"
---
# <span data-ttu-id="469fa-102">PSReadLine 모듈</span><span class="sxs-lookup"><span data-stu-id="469fa-102">PSReadLine Module</span></span>

## <span data-ttu-id="469fa-103">설명</span><span class="sxs-lookup"><span data-stu-id="469fa-103">Description</span></span>

<span data-ttu-id="469fa-104">PSReadLine 모듈에는 PowerShell에서 명령줄 편집 환경을 사용자 지정할 수 있는 cmdlet이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="469fa-104">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="469fa-105">이러한 문서는 PSReadLine v 2.2.0의 현재 베타 버전을 문서화 합니다.</span><span class="sxs-lookup"><span data-stu-id="469fa-105">These articles document the current beta version of PSReadLine v2.2.0.</span></span>

> [!NOTE]
> <span data-ttu-id="469fa-106">PowerShell 7.0부터 PowerShell은 화면 판독기 프로그램이 검색 된 경우 Windows에서 PSReadLine 자동 로드를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="469fa-106">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="469fa-107">현재 PSReadLine은 화면 판독기에서 제대로 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="469fa-107">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="469fa-108">Windows에서 PowerShell 7.0의 기본 렌더링 및 형식이 제대로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="469fa-108">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="469fa-109">필요한 경우 모듈을 수동으로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="469fa-109">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="469fa-110">PSReadLine Cmdlet</span><span class="sxs-lookup"><span data-stu-id="469fa-110">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="469fa-111">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="469fa-111">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="469fa-112">PSReadLine의 주 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="469fa-112">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="469fa-113">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="469fa-113">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="469fa-114">PSReadLine 모듈에 대 한 바인딩된 키 함수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="469fa-114">Gets the bound key functions for the PSReadLine module.</span></span>

### [<span data-ttu-id="469fa-115">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="469fa-115">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="469fa-116">구성할 수 있는 옵션의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="469fa-116">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="469fa-117">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="469fa-117">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="469fa-118">이 함수는 PSReadLine의 주 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="469fa-118">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="469fa-119">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="469fa-119">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="469fa-120">키 바인딩을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="469fa-120">Removes a key binding.</span></span>

### [<span data-ttu-id="469fa-121">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="469fa-121">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="469fa-122">키를 사용자 정의 또는 PSReadLine 키 처리기 함수에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="469fa-122">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="469fa-123">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="469fa-123">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="469fa-124">**Psreadline** 에서 명령줄 편집의 동작을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="469fa-124">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

