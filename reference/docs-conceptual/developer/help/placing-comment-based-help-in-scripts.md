---
ms.date: 09/12/2016
ms.topic: reference
title: 스크립트에 설명 기반 도움말 배치
description: 스크립트에 설명 기반 도움말 배치
ms.openlocfilehash: b0d32b7ab063269085899a643b0c3a17da2073fc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645447"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="0618b-103">스크립트에 설명 기반 도움말 배치</span><span class="sxs-lookup"><span data-stu-id="0618b-103">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="0618b-104">이 항목에서는 스크립트 `Get-Help` 에서 주석 기반 도움말 항목을 스크립트에 연결 하 고 스크립트에 포함 될 수 있는 함수와 연결 하지 않도록 스크립트에 대 한 주석 기반 도움말을 넣을 위치에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="0618b-104">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="0618b-105">스크립트에 대 한 Comment-Based 도움말 위치</span><span class="sxs-lookup"><span data-stu-id="0618b-105">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="0618b-106">스크립트 파일의 시작 부분에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0618b-106">At the beginning of the script file.</span></span>

  <span data-ttu-id="0618b-107">스크립트 도움말은 주석 및 빈 줄만 스크립트에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0618b-107">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="0618b-108">스크립트 파일의 끝에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0618b-108">At the end of the script file.</span></span>

  <span data-ttu-id="0618b-109">스크립트 본문의 첫 번째 항목 (도움말)이 함수 선언 인 경우 스크립트 도움말과 함수 선언 끝 사이에 두 개 이상의 빈 줄이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0618b-109">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="0618b-110">그렇지 않으면 도움말은 스크립트에 대 한 도움말이 아니라 함수에 대 한 도움말로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0618b-110">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="0618b-111">스크립트의 도움말 배치 예</span><span class="sxs-lookup"><span data-stu-id="0618b-111">Examples of Help Placement in a Script</span></span>

<span data-ttu-id="0618b-112">다음 예에서는 스크립트에 대 한 주석 기반 도움말의 각 배치 옵션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0618b-112">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="0618b-113">스크립트의 시작 부분에 있는 도움말</span><span class="sxs-lookup"><span data-stu-id="0618b-113">Help at the Beginning of a Script</span></span>

<span data-ttu-id="0618b-114">다음 예에서는 스크립트의 시작 부분에 있는 주석 기반을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0618b-114">The following example shows comment-based at the beginning of a script.</span></span>

```powershell
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="0618b-115">스크립트의 끝에 있는 도움말</span><span class="sxs-lookup"><span data-stu-id="0618b-115">Help at the End of a Script</span></span>

 <span data-ttu-id="0618b-116">다음 예에서는 스크립트의 끝에 있는 주석 기반을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0618b-116">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>
```
