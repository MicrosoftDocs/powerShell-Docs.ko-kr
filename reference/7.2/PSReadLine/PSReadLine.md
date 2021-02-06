---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: da71d4ef896befaadd7ed64f9a013dc19508a54c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600138"
---
# <span data-ttu-id="74fe6-102">PSReadLine 모듈</span><span class="sxs-lookup"><span data-stu-id="74fe6-102">PSReadLine Module</span></span>

## <span data-ttu-id="74fe6-103">설명</span><span class="sxs-lookup"><span data-stu-id="74fe6-103">Description</span></span>

<span data-ttu-id="74fe6-104">PSReadLine 모듈에는 PowerShell에서 명령줄 편집 환경을 사용자 지정할 수 있는 cmdlet이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74fe6-104">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="74fe6-105">이러한 문서는 PSReadLine v 2.0 문서입니다.</span><span class="sxs-lookup"><span data-stu-id="74fe6-105">These articles documents PSReadLine v2.0.</span></span> <span data-ttu-id="74fe6-106">이 버전은 PowerShell v6 및 Windows 10 10 월 2018 업데이트 (빌드 1809)에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74fe6-106">This version ships in PowerShell v6 and the Windows 10 October 2018 Update (Build 1809).</span></span>

> [!NOTE]
> <span data-ttu-id="74fe6-107">PowerShell 7.0부터 PowerShell은 화면 판독기 프로그램이 검색 된 경우 Windows에서 PSReadLine 자동 로드를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="74fe6-107">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="74fe6-108">현재 PSReadLine은 화면 판독기에서 제대로 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74fe6-108">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="74fe6-109">Windows에서 PowerShell 7.0의 기본 렌더링 및 형식이 제대로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="74fe6-109">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="74fe6-110">필요한 경우 모듈을 수동으로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74fe6-110">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="74fe6-111">PSReadLine Cmdlet</span><span class="sxs-lookup"><span data-stu-id="74fe6-111">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="74fe6-112">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="74fe6-112">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="74fe6-113">PSReadLine의 주 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="74fe6-113">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="74fe6-114">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="74fe6-114">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="74fe6-115">PSReadLine 모듈에 대 한 바인딩된 키 함수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="74fe6-115">Gets the bound key functions for the PSReadLine module.</span></span>

### [<span data-ttu-id="74fe6-116">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="74fe6-116">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="74fe6-117">구성할 수 있는 옵션의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="74fe6-117">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="74fe6-118">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="74fe6-118">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="74fe6-119">이 함수는 PSReadLine의 주 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="74fe6-119">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="74fe6-120">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="74fe6-120">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="74fe6-121">키 바인딩을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="74fe6-121">Removes a key binding.</span></span>

### [<span data-ttu-id="74fe6-122">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="74fe6-122">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="74fe6-123">키를 사용자 정의 또는 PSReadLine 키 처리기 함수에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="74fe6-123">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="74fe6-124">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="74fe6-124">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="74fe6-125">**Psreadline** 에서 명령줄 편집의 동작을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="74fe6-125">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

