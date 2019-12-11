---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Windows PowerShell ISE 소개
ms.openlocfilehash: 1723c11f38966cfffec9a6b3e4cb7b2304f19e7a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416275"
---
# <a name="the-windows-powershell-ise"></a><span data-ttu-id="8eb24-103">Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="8eb24-103">The Windows PowerShell ISE</span></span>

<span data-ttu-id="8eb24-104">Windows PowerShell ISE(통합 스크립팅 환경)는 Windows PowerShell의 호스트 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="8eb24-105">ISE에서는 단일 Windows 기반 그래픽 사용자 인터페이스에서 명령을 실행하고, 스크립트를 작성, 테스트 및 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-105">In the ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface.</span></span> <span data-ttu-id="8eb24-106">이 ISE는 여러 줄 편집, 탭 완성, 구문 색 지정, 선택적 실행, 상황에 맞는 도움말 및 오른쪽에서 왼쪽으로 쓰는 언어 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-106">The ISE provides multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span> <span data-ttu-id="8eb24-107">메뉴 항목 및 바로 가기 키가 Windows PowerShell 콘솔에서 수행하는 것과 동일한 많은 작업에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-107">Menu items and keyboard shortcuts are mapped to many of the same tasks that you would do in the Windows PowerShell console.</span></span> <span data-ttu-id="8eb24-108">예를 들어 ISE에서 스크립트를 디버그할 때 편집 창에서 코드 줄을 마우스 오른쪽 단추로 클릭하여 중단점을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-108">For example, when you debug a script in the ISE, you can right-click on a line of code in the edit pane to set a breakpoint.</span></span>

## <a name="support"></a><span data-ttu-id="8eb24-109">Support(지원)</span><span class="sxs-lookup"><span data-stu-id="8eb24-109">Support</span></span>

<span data-ttu-id="8eb24-110">ISE는 Windows PowerShell V2에 처음 도입되었고 PowerShell V3에서 다시 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-110">The ISE was first introduced with Windows PowerShell V2 and was re-designed with PowerShell V3.</span></span> <span data-ttu-id="8eb24-111">ISE는 Windows PowerShell V5.1 이하의 모든 지원되는 Windows PowerShell 버전에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-111">The ISE is supported in all supported versions of Windows PowerShell up to and including Windows PowerShell V5.1.</span></span>

> [!NOTE]
> <span data-ttu-id="8eb24-112">PowerShell ISE는 더 이상 활성 기능 개발에 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-112">The PowerShell ISE is no longer in active feature development.</span></span> <span data-ttu-id="8eb24-113">Windows의 배송 구성 요소로서 보안 및 우선 순위가 높은 서비스 수정 사항을 위해 공식적으로 계속 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-113">As a shipping component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span>
> <span data-ttu-id="8eb24-114">현재 Windows에서 ISE를 제거할 계획은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-114">We currently have no plans to remove the ISE from Windows.</span></span>
>
> <span data-ttu-id="8eb24-115">PowerShell v6 이상에서는 ISE가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-115">There is no support for the ISE in PowerShell v6 and beyond.</span></span> <span data-ttu-id="8eb24-116">ISE를 대체하려는 사용자는 [PowerShell 확장](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell)을 통해 [Visual Studio Code](https://code.visualstudio.com/)를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-116">Users looking for replacement for the ISE should use [Visual Studio Code](https://code.visualstudio.com/) with the [PowerShell Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).</span></span>

## <a name="key-features"></a><span data-ttu-id="8eb24-117">주요 기능</span><span class="sxs-lookup"><span data-stu-id="8eb24-117">Key Features</span></span>

<span data-ttu-id="8eb24-118">Windows PowerShell ISE의 주요 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-118">Key features in Windows PowerShell ISE include:</span></span>

- <span data-ttu-id="8eb24-119">여러 줄 편집: 명령 창에서 현재 줄 아래에 빈 줄을 삽입하려면 <kbd>SHIFT</kbd>+<kbd>ENTER</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-119">Multiline editing: To insert a blank line under the current line in the Command pane, press <kbd>SHIFT</kbd>+<kbd>ENTER</kbd>.</span></span>
- <span data-ttu-id="8eb24-120">선택적 실행: 스크립트의 일부를 실행하려면 실행할 텍스트를 선택한 다음, **스크립트 실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-120">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="8eb24-121">또는 <kbd>F5</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-121">Or, press <kbd>F5</kbd>.</span></span>
- <span data-ttu-id="8eb24-122">상황에 맞는 도움말: `Invoke-Item`을 입력하고 <kbd>F1</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-122">Context-sensitive help: Type `Invoke-Item`, and then press <kbd>F1</kbd>.</span></span> <span data-ttu-id="8eb24-123">도움말 파일이 `Invoke-Item` cmdlet에 대한 문서로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-123">The Help file opens to the article for the `Invoke-Item` cmdlet.</span></span>

<span data-ttu-id="8eb24-124">Windows PowerShell ISE를 사용하여 해당 모양의 일부 측면을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-124">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="8eb24-125">또한 자체 Windows PowerShell 프로필 스크립트도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-125">It also has its own Windows PowerShell profile script.</span></span>

## <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="8eb24-126">Windows PowerShell ISE를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="8eb24-126">To start the Windows PowerShell ISE</span></span>

<span data-ttu-id="8eb24-127">**시작**을 클릭하고 **Windows PowerShell**을 선택한 후 고 **Windows PowerShell ISE**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-127">Click **Start**, select **Windows PowerShell**, and then click **Windows PowerShell ISE**.</span></span>
<span data-ttu-id="8eb24-128">또는 임의 명령 셸이나 실행 상자에 `powershell_ise.exe`를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-128">Alternately, you can type `powershell_ise.exe` in any command shell or in the Run box.</span></span>

## <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="8eb24-129">Windows PowerShell ISE에서 도움말을 가져오려면</span><span class="sxs-lookup"><span data-stu-id="8eb24-129">To get Help in the Windows PowerShell ISE</span></span>

<span data-ttu-id="8eb24-130">**도움말** 메뉴에서 **Windows PowerShell 도움말**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-130">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="8eb24-131">또는 <kbd>F1</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-131">Or, press <kbd>F1</kbd>.</span></span> <span data-ttu-id="8eb24-132">열린 파일에는 `Get-Help` cmdlet에서 사용 가능한 모든 도움말을 비롯하여 Windows PowerShell ISE 및 Windows PowerShell이 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eb24-132">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all the help available from the `Get-Help` cmdlet.</span></span>
