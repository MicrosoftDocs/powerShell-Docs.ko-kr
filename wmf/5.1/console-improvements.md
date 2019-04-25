---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: WMF 5.1의 향상된 콘솔
ms.openlocfilehash: a8e82e2f973916c2ed5007eba90ee6f2b7a9a769
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085144"
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="a2346-103">WMF 5.1의 향상된 콘솔</span><span class="sxs-lookup"><span data-stu-id="a2346-103">Console Improvements in WMF 5.1</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="a2346-104">향상된 PowerShell 콘솔</span><span class="sxs-lookup"><span data-stu-id="a2346-104">PowerShell console improvements</span></span>

<span data-ttu-id="a2346-105">콘솔 환경을 개선하기 위해 WMF 5.1의 powershell.exe가 다음과 같이 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a2346-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

### <a name="vt100-support"></a><span data-ttu-id="a2346-106">VT100 지원</span><span class="sxs-lookup"><span data-stu-id="a2346-106">VT100 support</span></span>

<span data-ttu-id="a2346-107">Windows 10에서는 [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences)(VT100 이스케이프 스퀀스)에 대한 지원을 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="a2346-107">Windows 10 added support for [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences).</span></span>
<span data-ttu-id="a2346-108">PowerShell에서는 표 너비를 계산할 때 특정 VT100 서식 이스케이프 시퀀스를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="a2346-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="a2346-109">또한 PowerShell에서는 VT100이 지원되는지 여부를 결정하는 서식 코드에 사용할 수 있는 새로운 API도 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="a2346-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span>
<span data-ttu-id="a2346-110">예:</span><span class="sxs-lookup"><span data-stu-id="a2346-110">For example:</span></span>

```powershell
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```

<span data-ttu-id="a2346-111">다음은 `Select-String`의 일치 항목을 강조 표시하는 데 사용할 수 있는 전체 [예제](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7)입니다.</span><span class="sxs-lookup"><span data-stu-id="a2346-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from `Select-String`.</span></span>
<span data-ttu-id="a2346-112">예제를 `MatchInfo.format.ps1xml`이라는 파일로 저장하고 프로필 또는 다른 위치에서 사용하려면 `Update-FormatData -Prepend MatchInfo.format.ps1xml`을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a2346-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="a2346-113">VT100 이스케이프 시퀀스는 Windows 10 Anniversary 업데이트부터만 지원되며 이전 시스템에서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a2346-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update; they are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="a2346-114">PSReadline의 Vi 모드 지원</span><span class="sxs-lookup"><span data-stu-id="a2346-114">Vi mode support in PSReadline</span></span>

<span data-ttu-id="a2346-115">[PSReadline](https://github.com/lzybkr/PSReadLine)은 vi 모드에 대한 지원을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a2346-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="a2346-116">Vi 모드를 사용하려면 `Set-PSReadlineOption -EditMode Vi`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a2346-116">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="a2346-117">대화형 입력을 사용한 리디렉션된 stdin</span><span class="sxs-lookup"><span data-stu-id="a2346-117">Redirected stdin with interactive input</span></span>

<span data-ttu-id="a2346-118">이전 버전에서는 stdin이 리디렉션되고 명령을 대화형으로 입력하려는 경우 `powershell -File -`을 사용하여 PowerShell을 시작해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a2346-118">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="a2346-119">WMF 5.1에서 검색하기 어려운 이 옵션이 더 이상 필요하지 않으며</span><span class="sxs-lookup"><span data-stu-id="a2346-119">With WMF 5.1, this hard to discover option is no longer necessary.</span></span>
<span data-ttu-id="a2346-120">`powershell` 등과 같은 옵션 없이 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2346-120">You can start PowerShell without any options, e.g. `powershell`.</span></span>

<span data-ttu-id="a2346-121">PSReadline에서는 현재 리디렉션된 stdin을 지원하지 않으며 리디렉션된 stdin을 사용하는 기본 제공 명령줄 편집 환경이 매우 제한되어 있습니다. 예를 들어 화살표 키가 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a2346-121">Note that PSReadline does not currently support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span>
<span data-ttu-id="a2346-122">PSReadline의 이후 릴리스에서는 이 문제가 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2346-122">A future release of PSReadline should address this issue.</span></span>