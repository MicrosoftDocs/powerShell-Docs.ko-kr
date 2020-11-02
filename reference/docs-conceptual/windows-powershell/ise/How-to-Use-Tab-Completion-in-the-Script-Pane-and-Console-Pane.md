---
ms.date: 01/02/2020
title: 스크립트 창 및 콘솔 창에서 탭 완성 기능을 사용하는 방법
description: 스크립트 창 및 콘솔 창에서 탭 완성 기능을 사용하는 방법
ms.openlocfilehash: d59a324ef5ca8eb882814c51bd9b7780b5916e81
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663678"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a><span data-ttu-id="ddcf4-103">스크립트 창 및 콘솔 창에서 탭 완성 기능을 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="ddcf4-103">How to Use Tab Completion in the Script Pane and Console Pane</span></span>

<span data-ttu-id="ddcf4-104">탭 완성 기능은 스크립트 창이나 명령 창에 텍스트를 입력할 때 자동 도움말을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ddcf4-104">Tab completion provides automatic help when you are typing in the Script Pane or in the Command Pane.</span></span> <span data-ttu-id="ddcf4-105">이 기능을 활용하려면 다음 단계를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="ddcf4-105">Use the following steps to take advantage of this feature:</span></span>

## <a name="to-automatically-complete-a-command-entry"></a><span data-ttu-id="ddcf4-106">명령 입력을 자동으로 완성하려면</span><span class="sxs-lookup"><span data-stu-id="ddcf4-106">To automatically complete a command entry</span></span>

<span data-ttu-id="ddcf4-107">명령 창이나 스크립트 창에서 명령의 일부 문자를 입력한 다음 <kbd>Tab</kbd> 키를 눌러 원하는 완성 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ddcf4-107">In the Command Pane or Script Pane, type a few characters of a command and then press <kbd>TAB</kbd> to select the desired completion text.</span></span> <span data-ttu-id="ddcf4-108">처음에 입력한 텍스트로 시작하는 항목이 여러 개이면 원하는 항목이 나타날 때까지 계속 <kbd>Tab</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ddcf4-108">If multiple items begin with the text that you initially typed, then continue pressing <kbd>TAB</kbd> until the item you want appears.</span></span> <span data-ttu-id="ddcf4-109">탭 완성 기능을 사용하면 cmdlet 이름, 매개 변수 이름, 변수 이름, 개체 속성 이름 또는 파일 경로를 쉽게 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddcf4-109">Tab completion can help with typing a cmdlet name, parameter name, variable name, object property name, or a file path.</span></span>

> [!NOTE]
> <span data-ttu-id="ddcf4-110">스크립트 창에서는 `.ps1`, `.psd1` 또는 `.psm1` 파일을 편집하고 있는 경우에만 <kbd>Tab</kbd> 키를 눌러 명령을 자동으로 완성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddcf4-110">In the Script Pane, pressing <kbd>TAB</kbd> will automatically complete a command only when you are editing `.ps1`, `.psd1`, or `.psm1` files.</span></span> <span data-ttu-id="ddcf4-111">명령 창에서 입력하는 경우에는 탭 완성 기능이 항상 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="ddcf4-111">Tab completion works any time when you are typing in the Command Pane.</span></span>

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a><span data-ttu-id="ddcf4-112">cmdlet 매개 변수 입력을 자동으로 완성하려면</span><span class="sxs-lookup"><span data-stu-id="ddcf4-112">To automatically complete a cmdlet parameter entry</span></span>

<span data-ttu-id="ddcf4-113">명령 창이나 스크립트 창에서 cmdlet 뒤에 대시를 입력한 다음, <kbd>Tab</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ddcf4-113">In the Command Pane or Script pane, type a cmdlet followed by a dash and then press <kbd>TAB</kbd>.</span></span>

<span data-ttu-id="ddcf4-114">예를 들어 `Get-Process -`를 입력한 다음, <kbd>Tab</kbd> 키를 눌러 여러 번 해당 cmdlet에 대한 각 매개 변수를 차례로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ddcf4-114">For example, type `Get-Process -` and then press <kbd>TAB</kbd> multiple times to display each of the parameters for the cmdlet in turn.</span></span>

## <a name="see-also"></a><span data-ttu-id="ddcf4-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ddcf4-115">See Also</span></span>

- [<span data-ttu-id="ddcf4-116">Windows PowerShell ISE 소개</span><span class="sxs-lookup"><span data-stu-id="ddcf4-116">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="ddcf4-117">PowerShell 탭을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="ddcf4-117">How to Create a PowerShell Tab</span></span>](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
