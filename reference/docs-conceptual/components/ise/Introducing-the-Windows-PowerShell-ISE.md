---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Windows PowerShell ISE 소개
ms.openlocfilehash: 729c8535dbcfcd2c51070b8beac5d328375f36ae
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057426"
---
# <a name="the-windows-powershell-ise"></a><span data-ttu-id="9e661-103">Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="9e661-103">The Windows PowerShell ISE</span></span>

<span data-ttu-id="9e661-104">Windows PowerShell ISE(통합 스크립팅 환경)는 Windows PowerShell의 호스트 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="9e661-105">ISE에서는 단일 Windows 기반 그래픽 사용자 인터페이스에서 명령을 실행하고, 스크립트를 작성, 테스트 및 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-105">In the ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface.</span></span> <span data-ttu-id="9e661-106">이 ISE는 여러 줄 편집, 탭 완성, 구문 색 지정, 선택적 실행, 상황에 맞는 도움말 및 오른쪽에서 왼쪽으로 쓰는 언어 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-106">The ISE provides multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span> <span data-ttu-id="9e661-107">메뉴 항목 및 바로 가기 키가 Windows PowerShell 콘솔에서 수행하는 것과 동일한 많은 작업에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-107">Menu items and keyboard shortcuts are mapped to many of the same tasks that you would do in the Windows PowerShell console.</span></span> <span data-ttu-id="9e661-108">예를 들어 ISE에서 스크립트를 디버그할 때 편집 창에서 코드 줄을 마우스 오른쪽 단추로 클릭하여 중단점을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-108">For example, when you debug a script in the ISE, you can right-click on a line of code in the edit pane to set a breakpoint.</span></span>

## <a name="support"></a><span data-ttu-id="9e661-109">Support(지원)</span><span class="sxs-lookup"><span data-stu-id="9e661-109">Support</span></span>

<span data-ttu-id="9e661-110">ISE는 Windows PowerShell V2에 처음 도입되었고 PowerShell V3에서 다시 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-110">The ISE was first introduced with Windows PowerShell V2 and was re-designed with PowerShell V3.</span></span> <span data-ttu-id="9e661-111">ISE는 Windows PowerShell V5.1 이하의 모든 지원되는 Windows PowerShell 버전에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-111">The ISE is supported in all supported versions of Windows PowerShell up to and including Windows PowerShell V5.1.</span></span> <span data-ttu-id="9e661-112">그러나 ISE는 유지 관리 모드에 있고 새로운 기능이 추가될 가능성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-112">The ISE, however, is in maintenance mode and no new features are likely to be added.</span></span>
<span data-ttu-id="9e661-113">또한 PowerShell v6 이상에서는 ISE가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-113">Additionally, there is no support for the ISE with PowerShell v6 and beyond.</span></span> <span data-ttu-id="9e661-114">PowerShell 스크립트 등을 관리하는 데 그래픽 도구를 사용하려는 사용자는 [Visual Studio Code](https://code.visualstudio.com/)를 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-114">Users wanting a graphical tool with which to manage PowerShell scripts, etc, should consider [Visual Studio Code](https://code.visualstudio.com/).</span></span>

## <a name="key-features"></a><span data-ttu-id="9e661-115">주요 기능</span><span class="sxs-lookup"><span data-stu-id="9e661-115">Key Features</span></span>

<span data-ttu-id="9e661-116">Windows PowerShell ISE의 주요 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-116">Key features in Windows PowerShell ISE include:</span></span>

- <span data-ttu-id="9e661-117">여러 줄 편집: 명령 창에서 현재 줄 아래에 빈 줄을 삽입하려면 Shift+Enter를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-117">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>
- <span data-ttu-id="9e661-118">선택적 실행: 스크립트의 일부를 실행하려면 실행할 텍스트를 선택한 다음, **스크립트 실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-118">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="9e661-119">또는 F5 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-119">Or, press F5.</span></span>
- <span data-ttu-id="9e661-120">상황에 맞는 도움말: **Invoke-Item**을 입력한 다음, F1 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-120">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="9e661-121">도움말 파일이 **Invoke-Item** cmdlet에 대한 문서로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-121">The Help file opens to the article for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="9e661-122">Windows PowerShell ISE를 사용하여 해당 모양의 일부 측면을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-122">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="9e661-123">또한 자체 Windows PowerShell 프로필 스크립트도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-123">It also has its own Windows PowerShell profile script.</span></span>

## <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="9e661-124">Windows PowerShell ISE를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="9e661-124">To start the Windows PowerShell ISE</span></span>

<span data-ttu-id="9e661-125">**시작**을 클릭하고 **Windows PowerShell**을 선택한 후 고 **Windows PowerShell ISE**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-125">Click **Start**, select **Windows PowerShell**, and then click **Windows PowerShell ISE**.</span></span>
<span data-ttu-id="9e661-126">또는 임의 명령 셸이나 실행 상자에 `powershell_ise.exe`를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-126">Alternately, you can type `powershell_ise.exe` in any command shell or in the Run box.</span></span>

## <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="9e661-127">Windows PowerShell ISE에서 도움말을 가져오려면</span><span class="sxs-lookup"><span data-stu-id="9e661-127">To get Help in the Windows PowerShell ISE</span></span>

<span data-ttu-id="9e661-128">**도움말** 메뉴에서 **Windows PowerShell 도움말**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-128">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="9e661-129">또는 F1 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-129">Or, press F1.</span></span> <span data-ttu-id="9e661-130">열린 파일에는 Get-Help cmdlet에서 사용 가능한 모든 도움말을 비롯하여 Windows PowerShell ISE 및 Windows PowerShell이 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e661-130">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>
