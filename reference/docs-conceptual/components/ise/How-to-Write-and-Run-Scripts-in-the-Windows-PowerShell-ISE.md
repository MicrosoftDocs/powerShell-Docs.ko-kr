---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Windows PowerShell ISE에서 스크립트를 작성 및 실행하는 방법
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 61db5e18f05e8e334cd9ba6dab2cf15dee7390cc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402599"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="17d1d-103">Windows PowerShell ISE에서 스크립트를 작성 및 실행하는 방법</span><span class="sxs-lookup"><span data-stu-id="17d1d-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="17d1d-104">이 문서에서는 스크립트 창에서 스크립트를 만들고, 편집, 실행 및 저장하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-104">This article describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="17d1d-105">스크립트를 만들고 실행하는 방법</span><span class="sxs-lookup"><span data-stu-id="17d1d-105">How to create and run scripts</span></span>

<span data-ttu-id="17d1d-106">스크립트 창에서 Windows PowerShell 파일을 열고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="17d1d-107">Windows PowerShell에서 중요한 특정 파일 형식은 스크립트 파일(.ps1), 스크립트 데이터 파일(.psd1) 및 스크립트 모듈 파일(.psm1)입니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="17d1d-108">이러한 파일 형식은 스크립트 창 편집기에서 구문별로 색이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="17d1d-109">스크립트 창에서 열 수도 있는 다른 일반적인 파일 형식은 구성 파일(.ps1xml), XML 파일 및 텍스트 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="17d1d-110">Windows PowerShell 실행 정책은 스크립트를 실행하고 Windows PowerShell 프로필 및 구성 파일을 로드할 수 있는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="17d1d-111">기본 실행 정책인 Restricted는 모든 스크립트 실행과 프로필 로드를 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="17d1d-112">프로필 로드 및 사용을 허용하도록 실행 정책을 변경하려면 [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) 및 [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17d1d-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) and [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="17d1d-113">새 스크립트 파일을 만들려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-113">To create a new script file</span></span>

<span data-ttu-id="17d1d-114">도구 모음에서 **새로 만들기**를 클릭하거나 **파일** 메뉴에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-114">On the toolbar, click **New**, or on the **File** menu, click **New**.</span></span> <span data-ttu-id="17d1d-115">생성된 파일은 현재 PowerShell 탭 아래의 새 파일 탭에 나타납니다. PowerShell 탭은 탭이 두 개 이상 있는 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="17d1d-116">기본적으로 스크립트 형식의 파일(.ps1)이 생성되지만 새 이름과 확장명으로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="17d1d-117">동일한 PowerShell 탭에서 여러 스크립트 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="17d1d-118">기존 스크립트를 열려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-118">To open an existing script</span></span>

<span data-ttu-id="17d1d-119">도구 모음에서 **열기**를 클릭하거나 **파일** 메뉴에서 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="17d1d-120">**열기** 대화 상자에서 열려는 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="17d1d-121">열린 파일이 새 탭에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="17d1d-122">스크립트 탭을 닫으려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-122">To close a script tab</span></span>

<span data-ttu-id="17d1d-123">닫으려는 파일 탭의 **닫기** 아이콘(X)을 클릭하거나 **파일** 메뉴, **닫기**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-123">Click the **Close** icon (X) of the file tab you want to close or select the **File** menu and click **Close**.</span></span>

<span data-ttu-id="17d1d-124">파일이 마지막으로 저장된 후에 변경된 경우 변경 내용을 저장하거나 취소하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-124">If the file has been altered since it was last saved, you're prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="17d1d-125">파일 경로를 표시하려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-125">To display the file path</span></span>

<span data-ttu-id="17d1d-126">파일 탭에서 파일 이름을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-126">On the file tab, point to the file name.</span></span> <span data-ttu-id="17d1d-127">스크립트 파일의 정규화된 경로가 도구 설명에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-127">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="17d1d-128">스크립트를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-128">To run a script</span></span>

<span data-ttu-id="17d1d-129">도구 모음에서 **스크립트 실행**을 클릭하거나 **파일** 메뉴에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-129">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="17d1d-130">스크립트의 일부를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-130">To run a portion of a script</span></span>

1. <span data-ttu-id="17d1d-131">스크립트 창에서 스크립트의 일부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-131">In the Script Pane, select a portion of a script.</span></span>
2. <span data-ttu-id="17d1d-132">**파일** 메뉴에서 **선택 영역 실행**을 클릭하거나 도구 모음에서 **선택 영역 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-132">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="17d1d-133">실행 중인 스크립트를 중지하려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-133">To stop a running script</span></span>

<span data-ttu-id="17d1d-134">실행 중인 스크립트를 중지하는 몇 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-134">There are several ways to stop a running script.</span></span>

- <span data-ttu-id="17d1d-135">도구 모음에서 **작업 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-135">Click **Stop Operation** on the toolbar</span></span>
- <span data-ttu-id="17d1d-136">Ctrl+Break를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-136">Press CTRL+BREAK</span></span>
- <span data-ttu-id="17d1d-137">**파일** 메뉴를 선택하고 **작업 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-137">Select the **File** menu and click **Stop Operation**.</span></span>

<span data-ttu-id="17d1d-138">일부 텍스트가 현재 선택되지 않은 경우에는 **Ctrl+C**를 눌러도 됩니다. 텍스트가 선택된 경우 **Ctrl+C**는 선택한 텍스트의 복사 기능에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-138">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="17d1d-139">스크립트 창에서 텍스트를 작성 및 편집하는 방법</span><span class="sxs-lookup"><span data-stu-id="17d1d-139">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="17d1d-140">스크립트 창에서 텍스트를 복사, 잘라내기, 붙여넣기, 찾기 및 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-140">You can copy, cut, paste, find, and replace text in the Script Pane.</span></span> <span data-ttu-id="17d1d-141">방금 수행한 마지막 작업을 실행 취소하거나 다시 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="17d1d-142">이러한 작업을 위한 바로 가기 키는 모든 Windows 애플리케이션에 사용되는 바로 가기 키와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-142">The keyboard shortcuts for these actions are the same shortcuts used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="17d1d-143">스크립트 창에 텍스트를 입력하려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="17d1d-144">스크립트 창에서 아무 곳이나 클릭하거나 **보기** 메뉴에서 **스크립트 창으로 이동**을 클릭하여 커서를 스크립트 창으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>
2. <span data-ttu-id="17d1d-145">스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-145">Create a script.</span></span> <span data-ttu-id="17d1d-146">Windows PowerShell ISE에서는 구문 색 지정 및 탭 완성 기능을 통해 풍부한 편집 환경이 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-146">Syntax coloring and tab completion provide a richer editing experience in Windows PowerShell ISE.</span></span>
3. <span data-ttu-id="17d1d-147">탭 완성 기능을 사용하여 보다 쉽게 입력하는 방법에 대한 자세한 내용은 [스크립트 창 및 콘솔 창에서 탭 완성 기능을 사용하는 방법](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17d1d-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="17d1d-148">스크립트 창에서 텍스트를 찾으려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="17d1d-149">모든 위치에서 텍스트를 찾으려면 **Ctrl+F**를 누르거나, **편집** 메뉴에서 **스크립트에서 찾기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>
2. <span data-ttu-id="17d1d-150">커서 뒤에서 텍스트를 찾으려면 **F3** 키를 누르거나, **편집** 메뉴에서 **스크립트에서 다음 찾기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>
3. <span data-ttu-id="17d1d-151">커서 앞에서 텍스트를 찾으려면 **Shift+F3** 키를 누르거나, **편집** 메뉴에서 **스크립트에서 이전 찾기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="17d1d-152">스크립트 창에서 텍스트를 찾아 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="17d1d-153">**Ctrl+H**를 누르거나, **편집** 메뉴에서 **스크립트에서 바꾸기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-153">Press **CTRL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="17d1d-154">찾으려는 텍스트와 바꿀 텍스트를 입력하고 **Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-154">Enter the text you want to find and the replacement text, then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="17d1d-155">스크립트 창에서 특정 텍스트 줄로 이동하려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="17d1d-156">스크립트 창에서 **Ctrl+G**를 누르거나, **편집** 메뉴에서 **줄 이동**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="17d1d-157">줄 번호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="17d1d-158">스크립트 창에서 텍스트를 복사하려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="17d1d-159">스크립트 창에서 복사할 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="17d1d-160">**Ctrl+C**를 누르거나, 도구 모음에서 **복사** 아이콘을 클릭하거나, **편집** 메뉴에서 **복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="17d1d-161">스크립트 창에서 텍스트를 잘라내려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="17d1d-162">스크립트 창에서 잘라낼 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-162">In the Script Pane, select the text that you want to cut.</span></span>
2. <span data-ttu-id="17d1d-163">**Ctrl+X**를 누르거나, 도구 모음에서 **잘라내기** 아이콘을 클릭하거나, **편집** 메뉴에서 **잘라내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="17d1d-164">스크립트 창에 텍스트를 붙여넣으려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="17d1d-165">**Ctrl+V**를 누르거나, 도구 모음에서 **붙여넣기** 아이콘을 클릭하거나, **편집** 메뉴에서 **붙여넣기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="17d1d-166">스크립트 창에서 작업을 실행 취소하려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="17d1d-167">**Ctrl+Z**를 누르거나, 도구 모음에서 **실행 취소** 아이콘을 클릭하거나, **편집** 메뉴에서 **실행 취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="17d1d-168">스크립트 창에서 작업을 다시 실행하려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="17d1d-169">**Ctrl+Y**를 누르거나, 도구 모음에서 **다시 실행** 아이콘을 클릭하거나, **편집** 메뉴에서 **다시 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="17d1d-170">스크립트를 저장하는 방법</span><span class="sxs-lookup"><span data-stu-id="17d1d-170">How to save a script</span></span>

<span data-ttu-id="17d1d-171">변경된 이후 저장되지 않은 파일을 표시하기 위해 스크립트 이름 옆에 별표가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-171">An asterisk appears next to the script name to mark a file that hasn't been saved since it was changed.</span></span> <span data-ttu-id="17d1d-172">파일을 저장하면 별표가 사라집니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-172">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="17d1d-173">스크립트를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-173">To save a script</span></span>

<span data-ttu-id="17d1d-174">**Ctrl+S**를 누르거나, 도구 모음에서 **저장** 아이콘을 클릭하거나, **파일** 메뉴에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-174">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="17d1d-175">스크립트를 저장하고 이름을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-175">To save and name a script</span></span>

1. <span data-ttu-id="17d1d-176">**파일** 메뉴에서 **다른 이름으로 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-176">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="17d1d-177">**다른 이름으로 저장** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-177">The **Save As** dialog box will appear.</span></span>
2. <span data-ttu-id="17d1d-178">**파일 이름** 상자에 파일의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-178">In the **File name** box, enter a name for the file.</span></span>
3. <span data-ttu-id="17d1d-179">**파일 형식** 상자에서 파일 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-179">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="17d1d-180">예를 들어 **파일 형식** 상자에서 ‘PowerShell 스크립트(\*.ps1)’를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-180">For example, in the **Save as type** box, select 'PowerShell Scripts (\*.ps1)'.</span></span>
4. <span data-ttu-id="17d1d-181">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-181">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="17d1d-182">ASCII 인코딩 형식으로 스크립트를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="17d1d-182">To save a script in ASCII encoding</span></span>

<span data-ttu-id="17d1d-183">기본적으로 Windows PowerShell ISE에서는 새 스크립트 파일(.ps1), 스크립트 데이터 파일(.psd1) 및 스크립트 모듈 파일(.psm1)을 유니코드(BigEndianUnicode)로 저장합니다. 스크립트를 ASCII(ANSI) 등의 다른 인코딩으로 저장하려면 [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) 개체의 **Save** 또는 **SaveAs** 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-183">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) object.</span></span>

<span data-ttu-id="17d1d-184">다음 명령은 ASCII 인코딩을 사용하여 새 스크립트를 MyScript.ps1로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-184">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="17d1d-185">다음 명령은 현재 스크립트 파일을 이름은 같지만 ASCII 인코딩을 사용하는 파일로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-185">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="17d1d-186">다음 명령은 현재 파일의 인코딩을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-186">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="17d1d-187">Windows PowerShell ISE에서는 다음 인코딩 옵션을 지원합니다. ASCII, BigEndianUnicode, 유니코드, UTF32, UTF7, UTF8, 및 기본입니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-187">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8, and Default.</span></span> <span data-ttu-id="17d1d-188">기본값 옵션의 값은 시스템에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-188">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="17d1d-189">Windows PowerShell ISE에서는 저장 또는 다른 이름으로 저장을 사용하는 경우 스크립트 파일의 인코딩이 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17d1d-189">Windows PowerShell ISE doesn't change the encoding of script files when you use the Save or Save As commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="17d1d-190">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17d1d-190">See Also</span></span>

- [<span data-ttu-id="17d1d-191">Windows PowerShell ISE 탐색</span><span class="sxs-lookup"><span data-stu-id="17d1d-191">Exploring the Windows PowerShell ISE</span></span>](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
