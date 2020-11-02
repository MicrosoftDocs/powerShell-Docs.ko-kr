---
ms.date: 01/02/2020
title: Windows PowerShell ISE에서 PowerShell 탭을 만드는 방법
description: Windows PowerShell ISE(통합 스크립팅 환경)의 탭을 사용하면 동일한 애플리케이션 내에 여러 실행 환경을 동시에 만들고 사용할 수 있습니다. 각 PowerShell 탭은 별개의 실행 환경 또는 세션에 해당합니다.
ms.openlocfilehash: 62054014be9890b3fa0296f717f65a85534628d8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663790"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="0953a-104">Windows PowerShell ISE에서 PowerShell 탭을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="0953a-104">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>

<span data-ttu-id="0953a-105">Windows PowerShell ISE(통합 스크립팅 환경)의 탭을 사용하면 동일한 애플리케이션 내에 여러 실행 환경을 동시에 만들고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-105">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span> <span data-ttu-id="0953a-106">각 PowerShell 탭은 별개의 실행 환경 또는 세션에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-106">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> [!NOTE]
> <span data-ttu-id="0953a-107">하나의 탭에서 만드는 변수, 함수 및 별칭은 다른 탭으로 이전되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-107">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="0953a-108">서로 다른 Windows PowerShell 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-108">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="0953a-109">다음 단계를 수행하여 Windows PowerShell 탭을 열거나 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-109">Use the following steps to open or close a tab in Windows PowerShell.</span></span> <span data-ttu-id="0953a-110">탭의 이름을 바꾸려면 Windows PowerShell 탭 스크립팅 개체의 [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-110">To rename a tab, set the [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="0953a-111">새 PowerShell 탭을 만들고 사용하려면</span><span class="sxs-lookup"><span data-stu-id="0953a-111">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="0953a-112">**파일** 메뉴에서 **새 PowerShell 탭** 을 클릭합니다. 새 PowerShell 탭은 항상 활성 창으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-112">On the **File** menu, click **New PowerShell Tab** . The new PowerShell tab always opens as the active window.</span></span> <span data-ttu-id="0953a-113">PowerShell 탭은 열리는 순서대로 번호가 매겨집니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-113">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span> <span data-ttu-id="0953a-114">각 탭은 해당 Windows PowerShell 콘솔 창에 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-114">Each tab is associated with its own Windows PowerShell console window.</span></span> <span data-ttu-id="0953a-115">동시 최대 32개의 PowerShell 탭과 해당 세션을 열 수 있습니다(Windows PowerShell ISE 2.0에서는 8개로 제한됨).</span><span class="sxs-lookup"><span data-stu-id="0953a-115">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="0953a-116">도구 모음에서 **새로 만들기** 또는 **열기** 아이콘을 클릭할 때는 새 탭과 별개의 세션이 만들어지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-116">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span> <span data-ttu-id="0953a-117">대신, 이러한 단추는 현재 활성 탭과 세션에서 새 스크립트 파일이나 기존 스크립트 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-117">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span> <span data-ttu-id="0953a-118">각 탭과 세션에서 여러 개의 스크립트 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-118">You can have multiple script files open with each tab and session.</span></span> <span data-ttu-id="0953a-119">세션에 대한 스크립트 탭은 연결된 세션이 활성 상태인 경우에만 세션 탭 아래에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-119">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="0953a-120">PowerShell 탭을 활성화하려면 탭을 클릭합니다. 열려 있는 모든 PowerShell 탭 중에서 선택하려면 **보기** 메뉴에서 사용할 PowerShell 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-120">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="0953a-121">새 원격 PowerShell 탭을 만들고 사용하려면</span><span class="sxs-lookup"><span data-stu-id="0953a-121">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="0953a-122">**파일** 메뉴에서 **새 원격 PowerShell 탭** 을 클릭하여 원격 컴퓨터에서 세션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-122">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span> <span data-ttu-id="0953a-123">대화 상자가 나타나고 원격 연결을 설정하는 데 필요한 세부 정보를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-123">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span> <span data-ttu-id="0953a-124">원격 탭은 로컬 PowerShell 탭과 똑같이 작동하지만 명령과 스크립트가 원격 컴퓨터에서 실행된다는 점만 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-124">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="0953a-125">PowerShell 탭을 닫으려면</span><span class="sxs-lookup"><span data-stu-id="0953a-125">To close a PowerShell Tab</span></span>

<span data-ttu-id="0953a-126">탭을 닫으려면 다음 방법 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-126">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="0953a-127">닫으려는 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-127">Click the tab that you want to close.</span></span>

- <span data-ttu-id="0953a-128">**파일** 메뉴에서 **PowerShell 탭 닫기** 를 클릭하거나 활성 탭에서 닫기 단추( **X** )를 클릭하여 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-128">On the **File** menu, click **Close PowerShell Tab** , or click the Close button ( **X** ) on an active tab to close the tab.</span></span>

<span data-ttu-id="0953a-129">닫으려는 PowerShell 탭에 저장되지 않은 파일이 열려 있는 경우 파일을 저장할지 또는 삭제할지를 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-129">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span> <span data-ttu-id="0953a-130">스크립트를 저장하는 방법에 대한 자세한 내용은 [스크립트 저장 방법](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0953a-130">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="0953a-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0953a-131">See Also</span></span>

- [<span data-ttu-id="0953a-132">Windows PowerShell ISE 소개</span><span class="sxs-lookup"><span data-stu-id="0953a-132">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="0953a-133">Windows PowerShell ISE에서 콘솔 창을 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="0953a-133">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)
