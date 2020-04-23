---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Windows PowerShell ISE에서 콘솔 창을 사용하는 방법
ms.openlocfilehash: f0ef07e410ed494f5732eab360c4e050c9c09a7f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736150"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a><span data-ttu-id="87ae9-103">Windows PowerShell ISE에서 콘솔 창을 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="87ae9-103">How to Use the Console Pane in the Windows PowerShell ISE</span></span>

<span data-ttu-id="87ae9-104">Windows PowerShell ISE(통합 스크립팅 환경)의 콘솔 창은 독립 실행형 Windows PowerShell ISE 콘솔 창과 똑같이 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="87ae9-104">The Console pane in the Windows PowerShell Integrated Scripting Environment (ISE) operates exactly like the stand-alone Windows PowerShell ISE console window.</span></span>

<span data-ttu-id="87ae9-105">콘솔 창에서 명령을 실행하려면 명령을 입력한 다음, <kbd>Enter</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="87ae9-105">To run a command in the Console Pane, type a command, and then press <kbd>ENTER</kbd>.</span></span> <span data-ttu-id="87ae9-106">연속해서 실행할 여러 명령을 입력하려면 명령 사이에 <kbd>Shift</kbd>+<kbd>Enter</kbd>를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="87ae9-106">To enter multiple commands that you want to execute in sequence, type <kbd>SHIFT</kbd>+<kbd>ENTER</kbd> between commands.</span></span> <span data-ttu-id="87ae9-107">명령 입력에 대한 도움말은 [스크립트 창 및 콘솔 창에서 탭 완성 기능을 사용하는 방법](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87ae9-107">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for help in typing commands.</span></span>

<span data-ttu-id="87ae9-108">명령을 중지하려면 도구 모음에서 **작업 중지**를 클릭하거나 <kbd>Ctrl</kbd>+<kbd>BREAK</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="87ae9-108">To stop a command, on the toolbar, click **Stop Operation**, or press <kbd>CTRL</kbd>+<kbd>BREAK</kbd>.</span></span> <span data-ttu-id="87ae9-109">컨텍스트가 명확한 경우에는 <kbd>Ctrl</kbd>+<kbd>C</kbd>를 사용하여 명령을 중지할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87ae9-109">You can also use <kbd>CTRL</kbd>+<kbd>C</kbd> to stop a command if the context is unambiguous.</span></span> <span data-ttu-id="87ae9-110">예를 들어 현재 창에서 일부 텍스트를 선택한 경우 <kbd>Ctrl</kbd>+<kbd>C</kbd>는 복사 작업에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="87ae9-110">For example, if some text has been selected in the current Pane, then <kbd>CTRL</kbd>+<kbd>C</kbd> maps to the copy operation.</span></span>

<span data-ttu-id="87ae9-111">Windows PowerShell v3부터 출력 창이 콘솔 창과 결합되었습니다.</span><span class="sxs-lookup"><span data-stu-id="87ae9-111">Beginning in Windows PowerShell v3, the Output pane was combined with the Console pane.</span></span> <span data-ttu-id="87ae9-112">이렇게 하면 독립 실행형 Windows PowerShell 콘솔처럼 동작하는 이점이 있으며, 서로 별개일 때 필요한 절차의 차이점이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="87ae9-112">This has the benefit of behaving like the stand-alone Windows PowerShell console and eliminates the differences in procedures that were needed when they were separate.</span></span> <span data-ttu-id="87ae9-113">다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87ae9-113">You can:</span></span>

- <span data-ttu-id="87ae9-114">다른 창에 붙여넣기 위해 콘솔 창에서 텍스트를 선택하여 클립보드로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="87ae9-114">Select and copy text from the Console pane to the Clipboard for pasting in any other window.</span></span> <span data-ttu-id="87ae9-115">텍스트를 선택하려면 출력 창에서 마우스를 클릭하고 누른 채 캡처할 텍스트 위로 마우스를 끕니다.</span><span class="sxs-lookup"><span data-stu-id="87ae9-115">To select text, click and hold the mouse in the output pane while dragging the mouse over the text you want to capture.</span></span> <span data-ttu-id="87ae9-116"><kbd>Shift</kbd> 키를 누른 채 커서 화살표 키를 사용하여 텍스트를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87ae9-116">You can also use the cursor arrow keys while holding <kbd>SHIFT</kbd> to select text.</span></span> <span data-ttu-id="87ae9-117">그런 다음, <kbd>Ctrl</kbd>+<kbd>C</kbd>를 누르거나 도구 모음에서 **복사** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87ae9-117">Then press <kbd>CTRL</kbd>+<kbd>C</kbd> or click the **Copy** icon in the toolbar.</span></span>

- <span data-ttu-id="87ae9-118">선택한 텍스트를 현재 커서 위치에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="87ae9-118">Paste the selected text at a current cursor position.</span></span> <span data-ttu-id="87ae9-119">도구 모음에서 **붙여넣기** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87ae9-119">Click the **Paste** icon on the toolbar.</span></span>

- <span data-ttu-id="87ae9-120">콘솔 창에서 모든 텍스트를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="87ae9-120">Clear all the text in the Console pane.</span></span> <span data-ttu-id="87ae9-121">콘솔 창을 지우려면 도구 모음에서 **콘솔 창 지우기** 아이콘을 클릭하거나 `Clear-Host` 명령 또는 해당 별칭인 `cls`를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87ae9-121">To clear the Console pane, you can click the **Clear Console Pane** icon on the toolbar, or run the command `Clear-Host` or its alias, `cls`.</span></span>

## <a name="see-also"></a><span data-ttu-id="87ae9-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="87ae9-122">See Also</span></span>

- [<span data-ttu-id="87ae9-123">Windows PowerShell ISE 소개</span><span class="sxs-lookup"><span data-stu-id="87ae9-123">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
