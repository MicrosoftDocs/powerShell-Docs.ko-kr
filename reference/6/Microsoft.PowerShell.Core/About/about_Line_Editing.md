---
description: PowerShell 명령 프롬프트에서 명령을 편집 하는 방법에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_line_editing?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Line_Editing
ms.openlocfilehash: 59516bf14ca273c495c3d126a40a76f31293735b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221521"
---
# <a name="about-line-editing"></a><span data-ttu-id="c1b39-104">줄 편집 정보</span><span class="sxs-lookup"><span data-stu-id="c1b39-104">About Line Editing</span></span>

## <a name="short-description"></a><span data-ttu-id="c1b39-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="c1b39-105">Short description</span></span>

<span data-ttu-id="c1b39-106">PowerShell 명령 프롬프트에서 명령을 편집 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-106">Describes how to edit commands at the PowerShell command prompt.</span></span>

## <a name="long-description"></a><span data-ttu-id="c1b39-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-107">Long description</span></span>

<span data-ttu-id="c1b39-108">Powershell 콘솔에는 PowerShell 명령 프롬프트에서 명령을 편집 하는 데 도움이 되는 몇 가지 유용한 바로 가기 키가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-108">The PowerShell console has some useful keyboard shortcuts to help you edit commands at the PowerShell command prompt.</span></span>

### <a name="add-a-line"></a><span data-ttu-id="c1b39-109">선 추가</span><span class="sxs-lookup"><span data-stu-id="c1b39-109">Add a line</span></span>

<span data-ttu-id="c1b39-110">줄을 추가 하려면 <kbd>Shift</kbd> + <kbd>enter</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-110">To add a line, press <kbd>Shift</kbd>+<kbd>Enter</kbd>.</span></span>

<span data-ttu-id="c1b39-111">여러 줄을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-111">You can add multiple lines.</span></span> <span data-ttu-id="c1b39-112">각 추가 줄 `>>` 은 연속 프롬프트로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-112">Each additional line begins with `>>`, the continuation prompt.</span></span> <span data-ttu-id="c1b39-113"><kbd>Enter</kbd> 키를 눌러 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-113">Press <kbd>Enter</kbd> to execute the command.</span></span>

### <a name="move-left-and-right"></a><span data-ttu-id="c1b39-114">왼쪽 및 오른쪽으로 이동</span><span class="sxs-lookup"><span data-stu-id="c1b39-114">Move left and right</span></span>

<span data-ttu-id="c1b39-115">커서를 한 문자 왼쪽으로 이동 하려면 <kbd>왼쪽 화살표</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-115">To move the cursor one character to the left, press the <kbd>Left arrow</kbd>.</span></span>

<span data-ttu-id="c1b39-116">커서를 한 단어 왼쪽으로 이동 하려면 <kbd>Ctrl</kbd> + <kbd>왼쪽 화살표</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-116">To move the cursor one word to the left, press <kbd>Ctrl</kbd>+<kbd>Left arrow</kbd>.</span></span>

<span data-ttu-id="c1b39-117">커서를 한 문자 오른쪽으로 이동 하려면 <kbd>오른쪽 화살표</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-117">To move the cursor one character to the right, press the <kbd>Right arrow</kbd>.</span></span>

<span data-ttu-id="c1b39-118">커서를 한 단어 오른쪽으로 이동 하려면 <kbd>Ctrl</kbd> + <kbd>오른쪽 화살표</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-118">To move the cursor one word to the right, press <kbd>Ctrl</kbd>+<kbd>Right arrow</kbd>.</span></span>

### <a name="move-to-a-lines-beginning-or-end"></a><span data-ttu-id="c1b39-119">줄의 시작 또는 끝으로 이동</span><span class="sxs-lookup"><span data-stu-id="c1b39-119">Move to a line's beginning or end</span></span>

<span data-ttu-id="c1b39-120">줄의 시작 부분으로 이동 하려면 <kbd>Home</kbd>키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-120">To move to the beginning of a line, press <kbd>Home</kbd>.</span></span>

<span data-ttu-id="c1b39-121">줄의 끝으로 이동 하려면 <kbd>end</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-121">To move to the end of a line, press <kbd>End</kbd>.</span></span>

<span data-ttu-id="c1b39-122">줄이 추가 된 경우 <kbd>Home</kbd> 또는 <kbd>end</kbd> 를 두 번 눌러 줄의 시작 또는 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-122">If lines were added, press <kbd>Home</kbd> or <kbd>End</kbd> twice to move to the beginning or end of the lines.</span></span>

### <a name="delete-characters"></a><span data-ttu-id="c1b39-123">문자 삭제</span><span class="sxs-lookup"><span data-stu-id="c1b39-123">Delete characters</span></span>

<span data-ttu-id="c1b39-124">커서 위치 뒤의 문자를 삭제 하려면 <kbd>백스페이스</kbd>키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-124">To delete the character behind the cursor's position, press <kbd>Backspace</kbd>.</span></span>

<span data-ttu-id="c1b39-125">커서의 위치에서 문자를 삭제 하려면 <kbd>delete</kbd>키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-125">To delete the character at the cursor's position, press <kbd>Delete</kbd>.</span></span>

### <a name="delete-characters-from-a-line"></a><span data-ttu-id="c1b39-126">줄에서 문자 삭제</span><span class="sxs-lookup"><span data-stu-id="c1b39-126">Delete characters from a line</span></span>

<span data-ttu-id="c1b39-127">커서의 위치에서 줄의 끝까지 모든 문자를 삭제 하려면 <kbd>Ctrl</kbd> + <kbd>end</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-127">To delete all the characters from the cursor's position to the end of a line, press <kbd>Ctrl</kbd>+<kbd>End</kbd>.</span></span>

<span data-ttu-id="c1b39-128">커서 위치에서 줄의 시작 부분까지 모든 문자를 삭제 하려면 <kbd>ctrl</kbd> + <kbd>Home</kbd>을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-128">To delete all the characters from the cursor's position to the beginning of a line, press <kbd>Ctrl</kbd>+<kbd>Home</kbd>.</span></span>

<span data-ttu-id="c1b39-129">줄이 추가 되 면 현재 줄에서 문자를 삭제 하 고 추가 된 줄을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-129">If lines were added, characters are deleted from the current line and the lines that were added.</span></span>

### <a name="insert-and-overstrike-mode"></a><span data-ttu-id="c1b39-130">Insert 및 겹쳐쓰기 모드</span><span class="sxs-lookup"><span data-stu-id="c1b39-130">Insert and overstrike mode</span></span>

<span data-ttu-id="c1b39-131">덮어쓰기 모드로 변경 하려면 <kbd>Insert</kbd>키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-131">To change to overwrite mode, press <kbd>Insert</kbd>.</span></span> <span data-ttu-id="c1b39-132">삽입 모드로 돌아가려면 <kbd>insert</kbd> 를 다시 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-132">To return to insert mode, press <kbd>Insert</kbd> again.</span></span>

### <a name="tab-completion"></a><span data-ttu-id="c1b39-133">탭 완성</span><span class="sxs-lookup"><span data-stu-id="c1b39-133">Tab completion</span></span>

<span data-ttu-id="c1b39-134">Cmdlet 이름, 매개 변수 또는 경로를 완료 하려면 <kbd>tab</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-134">To complete a cmdlet name, a parameter, or a path, press the <kbd>Tab</kbd> key.</span></span> <span data-ttu-id="c1b39-135">값 목록을 스크롤하려면 <kbd>tab</kbd> 키를 다시 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c1b39-135">To scroll through a list of values, press the <kbd>Tab</kbd> key again.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1b39-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c1b39-136">See also</span></span>

[<span data-ttu-id="c1b39-137">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="c1b39-137">about_Command_Syntax</span></span>](about_Command_Syntax.md)

[<span data-ttu-id="c1b39-138">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="c1b39-138">about_Path_Syntax</span></span>](about_Path_Syntax.md)

[<span data-ttu-id="c1b39-139">about_PSReadline</span><span class="sxs-lookup"><span data-stu-id="c1b39-139">about_PSReadline</span></span>](../../PSReadline/About/about_PSReadline.md)
