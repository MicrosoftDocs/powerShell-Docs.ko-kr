---
description: PowerShell 명령 프롬프트에서 명령을 편집 하는 방법에 대해 설명 합니다.
Locale: en-US
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_line_editing?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Line_Editing
ms.openlocfilehash: 2b9a320b92bc0a61efc9f9ed75078b17cdd9cbc9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601832"
---
# <a name="about-line-editing"></a><span data-ttu-id="2bcf3-103">줄 편집 정보</span><span class="sxs-lookup"><span data-stu-id="2bcf3-103">About Line Editing</span></span>

## <a name="short-description"></a><span data-ttu-id="2bcf3-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="2bcf3-104">Short description</span></span>

<span data-ttu-id="2bcf3-105">PowerShell 명령 프롬프트에서 명령을 편집 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-105">Describes how to edit commands at the PowerShell command prompt.</span></span>

## <a name="long-description"></a><span data-ttu-id="2bcf3-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-106">Long description</span></span>

<span data-ttu-id="2bcf3-107">Powershell 콘솔에는 PowerShell 명령 프롬프트에서 명령을 편집 하는 데 도움이 되는 몇 가지 유용한 바로 가기 키가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-107">The PowerShell console has some useful keyboard shortcuts to help you edit commands at the PowerShell command prompt.</span></span>

### <a name="add-a-line"></a><span data-ttu-id="2bcf3-108">선 추가</span><span class="sxs-lookup"><span data-stu-id="2bcf3-108">Add a line</span></span>

<span data-ttu-id="2bcf3-109">줄을 추가 하려면 <kbd>Shift</kbd> + <kbd>enter</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-109">To add a line, press <kbd>Shift</kbd>+<kbd>Enter</kbd>.</span></span>

<span data-ttu-id="2bcf3-110">여러 줄을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-110">You can add multiple lines.</span></span> <span data-ttu-id="2bcf3-111">각 추가 줄 `>>` 은 연속 프롬프트로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-111">Each additional line begins with `>>`, the continuation prompt.</span></span> <span data-ttu-id="2bcf3-112"><kbd>Enter</kbd> 키를 눌러 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-112">Press <kbd>Enter</kbd> to execute the command.</span></span>

### <a name="move-left-and-right"></a><span data-ttu-id="2bcf3-113">왼쪽 및 오른쪽으로 이동</span><span class="sxs-lookup"><span data-stu-id="2bcf3-113">Move left and right</span></span>

<span data-ttu-id="2bcf3-114">커서를 한 문자 왼쪽으로 이동 하려면 <kbd>왼쪽 화살표</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-114">To move the cursor one character to the left, press the <kbd>Left arrow</kbd>.</span></span>

<span data-ttu-id="2bcf3-115">커서를 한 단어 왼쪽으로 이동 하려면 <kbd>Ctrl</kbd> + <kbd>왼쪽 화살표</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-115">To move the cursor one word to the left, press <kbd>Ctrl</kbd>+<kbd>Left arrow</kbd>.</span></span>

<span data-ttu-id="2bcf3-116">커서를 한 문자 오른쪽으로 이동 하려면 <kbd>오른쪽 화살표</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-116">To move the cursor one character to the right, press the <kbd>Right arrow</kbd>.</span></span>

<span data-ttu-id="2bcf3-117">커서를 한 단어 오른쪽으로 이동 하려면 <kbd>Ctrl</kbd> + <kbd>오른쪽 화살표</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-117">To move the cursor one word to the right, press <kbd>Ctrl</kbd>+<kbd>Right arrow</kbd>.</span></span>

### <a name="move-to-a-lines-beginning-or-end"></a><span data-ttu-id="2bcf3-118">줄의 시작 또는 끝으로 이동</span><span class="sxs-lookup"><span data-stu-id="2bcf3-118">Move to a line's beginning or end</span></span>

<span data-ttu-id="2bcf3-119">줄의 시작 부분으로 이동 하려면 <kbd>Home</kbd>키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-119">To move to the beginning of a line, press <kbd>Home</kbd>.</span></span>

<span data-ttu-id="2bcf3-120">줄의 끝으로 이동 하려면 <kbd>end</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-120">To move to the end of a line, press <kbd>End</kbd>.</span></span>

<span data-ttu-id="2bcf3-121">줄이 추가 된 경우 <kbd>Home</kbd> 또는 <kbd>end</kbd> 를 두 번 눌러 줄의 시작 또는 끝으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-121">If lines were added, press <kbd>Home</kbd> or <kbd>End</kbd> twice to move to the beginning or end of the lines.</span></span>

### <a name="delete-characters"></a><span data-ttu-id="2bcf3-122">문자 삭제</span><span class="sxs-lookup"><span data-stu-id="2bcf3-122">Delete characters</span></span>

<span data-ttu-id="2bcf3-123">커서 위치 뒤의 문자를 삭제 하려면 <kbd>백스페이스</kbd>키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-123">To delete the character behind the cursor's position, press <kbd>Backspace</kbd>.</span></span>

<span data-ttu-id="2bcf3-124">커서의 위치에서 문자를 삭제 하려면 <kbd>delete</kbd>키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-124">To delete the character at the cursor's position, press <kbd>Delete</kbd>.</span></span>

### <a name="delete-characters-from-a-line"></a><span data-ttu-id="2bcf3-125">줄에서 문자 삭제</span><span class="sxs-lookup"><span data-stu-id="2bcf3-125">Delete characters from a line</span></span>

<span data-ttu-id="2bcf3-126">커서의 위치에서 줄의 끝까지 모든 문자를 삭제 하려면 <kbd>Ctrl</kbd> + <kbd>end</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-126">To delete all the characters from the cursor's position to the end of a line, press <kbd>Ctrl</kbd>+<kbd>End</kbd>.</span></span>

<span data-ttu-id="2bcf3-127">커서 위치에서 줄의 시작 부분까지 모든 문자를 삭제 하려면 <kbd>ctrl</kbd> + <kbd>Home</kbd>을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-127">To delete all the characters from the cursor's position to the beginning of a line, press <kbd>Ctrl</kbd>+<kbd>Home</kbd>.</span></span>

<span data-ttu-id="2bcf3-128">줄이 추가 되 면 현재 줄에서 문자를 삭제 하 고 추가 된 줄을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-128">If lines were added, characters are deleted from the current line and the lines that were added.</span></span>

### <a name="insert-and-overstrike-mode"></a><span data-ttu-id="2bcf3-129">Insert 및 겹쳐쓰기 모드</span><span class="sxs-lookup"><span data-stu-id="2bcf3-129">Insert and overstrike mode</span></span>

<span data-ttu-id="2bcf3-130">덮어쓰기 모드로 변경 하려면 <kbd>Insert</kbd>키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-130">To change to overwrite mode, press <kbd>Insert</kbd>.</span></span> <span data-ttu-id="2bcf3-131">삽입 모드로 돌아가려면 <kbd>insert</kbd> 를 다시 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-131">To return to insert mode, press <kbd>Insert</kbd> again.</span></span>

### <a name="tab-completion"></a><span data-ttu-id="2bcf3-132">탭 완성</span><span class="sxs-lookup"><span data-stu-id="2bcf3-132">Tab completion</span></span>

<span data-ttu-id="2bcf3-133">Cmdlet 이름, 매개 변수 또는 경로를 완료 하려면 <kbd>tab</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-133">To complete a cmdlet name, a parameter, or a path, press the <kbd>Tab</kbd> key.</span></span> <span data-ttu-id="2bcf3-134">값 목록을 스크롤하려면 <kbd>tab</kbd> 키를 다시 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2bcf3-134">To scroll through a list of values, press the <kbd>Tab</kbd> key again.</span></span>

## <a name="see-also"></a><span data-ttu-id="2bcf3-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2bcf3-135">See also</span></span>

[<span data-ttu-id="2bcf3-136">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="2bcf3-136">about_Command_Syntax</span></span>](about_Command_Syntax.md)

[<span data-ttu-id="2bcf3-137">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="2bcf3-137">about_Path_Syntax</span></span>](about_Path_Syntax.md)

[<span data-ttu-id="2bcf3-138">about_PSReadline</span><span class="sxs-lookup"><span data-stu-id="2bcf3-138">about_PSReadline</span></span>](../../PSReadline/About/about_PSReadline.md)

