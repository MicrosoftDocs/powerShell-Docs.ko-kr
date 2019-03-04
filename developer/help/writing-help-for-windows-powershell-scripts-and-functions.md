---
title: PowerShell 스크립트 및 함수에 대 한 도움말 작성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: 98a3f61ff4fa2367f69357173d4e8e14288ff429
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857479"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a><span data-ttu-id="07585-102">PowerShell 스크립트 및 함수에 대 한 도움말 작성</span><span class="sxs-lookup"><span data-stu-id="07585-102">Writing Help for PowerShell Scripts and Functions</span></span>

<span data-ttu-id="07585-103">PowerShell 스크립트 및 함수 완벽 하 게 문서화 해야 때마다 다른 사용자와 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-103">PowerShell scripts and functions should be fully documented whenever they are shared with others.</span></span>
<span data-ttu-id="07585-104">합니다 `Get-Help` cmdlet 도움말 항목에서는 스크립트 및 함수 같은 형식으로 표시 하 고 모든 cmdlet에 대 한 도움말을 표시 하는 `Get-Help` 매개 변수는 함수 및 스크립트 도움말 항목에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-104">The `Get-Help` cmdlet displays the script and function help topics in the same format as it displays help for cmdlets, and all of the `Get-Help` parameters work on script and function help topics.</span></span>

<span data-ttu-id="07585-105">PowerShell 스크립트는 스크립트에서 스크립트에 대 한 도움말 항목 및 각 함수에 대 한 도움말 항목이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07585-105">PowerShell scripts can include a help topic about the script and help topics about each functions in the script.</span></span>
<span data-ttu-id="07585-106">스크립트와 독립적으로 공유 되는 함수 자체 도움말 항목을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07585-106">Functions that are shared independently of scripts can include their own help topics.</span></span>

<span data-ttu-id="07585-107">이 문서에서는 형식 및 도움말 항목의 올바른 배치를 설명 하 고 콘텐츠에 대 한 지침 제안 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-107">This document explains the format and correct placement of the help topics, and it suggests guidelines for the content.</span></span>

## <a name="types-of-script-and-function-help"></a><span data-ttu-id="07585-108">스크립트 및 함수 도움말 형식</span><span class="sxs-lookup"><span data-stu-id="07585-108">Types of Script and Function Help</span></span>

### <a name="comment-based-help"></a><span data-ttu-id="07585-109">주석 기반 도움말</span><span class="sxs-lookup"><span data-stu-id="07585-109">Comment-Based Help</span></span>
<span data-ttu-id="07585-110">스크립트 또는 함수 내에서 주석의 집합으로 스크립트 또는 함수를 설명 하는 도움말 항목을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07585-110">The help topic that describes a script or function can be implemented as a set of comments within the script or function.</span></span>
<span data-ttu-id="07585-111">스크립트 및 함수에 대 한 설명 기반 도움말 스크립트에서를 작성할 때는 주석 기반 도움말을 배치에 대 한 규칙 주의 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-111">When writing comment-based help for a script and for functions in a script, pay careful attention to the rules for placing the comment-based help.</span></span>
<span data-ttu-id="07585-112">위치에 따라 결정 여부는 `Get-Help` cmdlet 스크립트 또는 함수를 사용 하 여 도움말 항목을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-112">The placement determines whether the `Get-Help` cmdlet associates the help topic with the script or a function.</span></span>
<span data-ttu-id="07585-113">주석 기반 도움말 항목을 작성 하는 방법에 대 한 자세한 내용은 참조 하세요. [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-113">For more information about writing comment-based help topics, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

### <a name="xml-based-command-help"></a><span data-ttu-id="07585-114">XML 기반 명령 도움말</span><span class="sxs-lookup"><span data-stu-id="07585-114">XML-Based Command Help</span></span>
<span data-ttu-id="07585-115">명령 도움말 스키마를 사용 하는 XML 파일에 스크립트 또는 함수를 설명 하는 도움말 항목을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07585-115">The help topic that describes a script or function can be implemented in an XML file that uses the command help schema.</span></span>
<span data-ttu-id="07585-116">XML 파일을 사용 하 여 스크립트 또는 함수를 연결 하려면 사용는 `ExternalHelp` 키워드 뒤에 XML 파일의 이름과 경로 주석 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-116">To associate the script or function with the XML file, use the `ExternalHelp` comment keyword followed by the path and name of the XML file.</span></span>

<span data-ttu-id="07585-117">경우는 `ExternalHelp` 키워드를 사용할 수 있는지 설명 기반 도움말을 통해 우선, 주석, 경우에 `Get-Help` 값과 일치 하는 도움말 파일을 찾을 수 없습니다는 `ExternalHelp` 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="07585-117">When the `ExternalHelp` comment keyword is present, it takes precedence over comment-based help, even when `Get-Help` cannot find a help file that matches the value of the `ExternalHelp` keyword.</span></span>

### <a name="online-help"></a><span data-ttu-id="07585-118">온라인 도움말</span><span class="sxs-lookup"><span data-stu-id="07585-118">Online Help</span></span>
<span data-ttu-id="07585-119">인터넷에서 도움말 항목을 게시 하 고 다음 직접 `Get-Help` 항목을 열입니다.</span><span class="sxs-lookup"><span data-stu-id="07585-119">You can post your help topics on the Internet and then direct `Get-Help` to open the topics.</span></span>
<span data-ttu-id="07585-120">주석 기반 도움말 항목을 작성 하는 방법에 대 한 자세한 내용은 참조 하세요. [온라인 도움말 지원](../module/supporting-online-help.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-120">For more information about writing comment-based help topics, see [Supporting Online Help](../module/supporting-online-help.md).</span></span>

<span data-ttu-id="07585-121">개념 ("정보") 스크립트 및 함수에 대 한 항목 작성에 대 한 설정 된 메서드가 없는 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-121">There is no established method for writing conceptual ("About") topics for scripts and functions.</span></span>
<span data-ttu-id="07585-122">그러나 명령 도움말 항목의 관련 링크 섹션에 인터넷 목록에 대 한 개념적인 항목 항목 및 해당 Url 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07585-122">However, you can post conceptual topics on the Internet list the topics and their URLs in the Related Links section of a command help topic.</span></span>

## <a name="content-considerations-for-script-and-function-help"></a><span data-ttu-id="07585-123">스크립트 및 함수에 대 한 콘텐츠 고려 사항 도움말</span><span class="sxs-lookup"><span data-stu-id="07585-123">Content Considerations for Script and Function Help</span></span>

- <span data-ttu-id="07585-124">사용 가능한 명령 도움말 섹션 중 일부를 사용 하 여 매우 간단한 도움말 항목을 작성 하는 경우에 명확한 설명은 스크립트 또는 함수 매개 변수를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-124">If you are writing a very brief help topic with only a few of the available command help sections, be sure to include clear descriptions of the script or function parameters.</span></span> <span data-ttu-id="07585-125">예제에서는 설명을 생략 하기로 한 경우에 예제 섹션에서 하나 또는 두 개의 샘플 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-125">Also include one or two sample commands in the examples section, even if you decide to omit example descriptions.</span></span>

- <span data-ttu-id="07585-126">모든 설명으로 스크립트 또는 함수의 명령 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-126">In all descriptions, refer to the command as a script or function.</span></span> <span data-ttu-id="07585-127">이 정보를 파악 하 고 명령을 관리 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07585-127">This information helps the user to understand and manage the command.</span></span>

  <span data-ttu-id="07585-128">예를 들어, 다음을 자세히 기술 한 새 항목 명령을 스크립트 임을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07585-128">For example, the following detailed description states that the New-Topic command is a script.</span></span> <span data-ttu-id="07585-129">이 실행할 때 전체 이름과 경로 지정 하는 데 필요한 사용자를 게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="07585-129">This reminds users that they need to specify the path and full name when they run it.</span></span>

  > <span data-ttu-id="07585-130">"새 항목 스크립트 입력된 파일에서 각 항목 이름에 대 한 빈 개념 항목을 만드는"</span><span class="sxs-lookup"><span data-stu-id="07585-130">"The New-Topic script creates a blank conceptual topic for each topic name in the input file..."</span></span>

  <span data-ttu-id="07585-131">다음 자세한 설명을 나타내는 `Disable-PSRemoting` 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="07585-131">The following detailed description states that `Disable-PSRemoting` is a function.</span></span> <span data-ttu-id="07585-132">이 정보는 세션 중 일부는 의해 숨겨질 수 명령 우선 순위가 높은, 동일한 이름 가진 여러 명령이 포함 된 경우 사용자에 게 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-132">This information is particularly useful to users when the session includes multiple commands with the same name, some of which might be hidden by a command with higher precedence.</span></span>

  > <span data-ttu-id="07585-133">`Disable-PSRemoting` 함수 로컬 컴퓨터의 모든 세션 구성을 사용 하지 않도록 설정 하는 중...</span><span class="sxs-lookup"><span data-stu-id="07585-133">The `Disable-PSRemoting` function disables all session configurations on the local computer...</span></span>

- <span data-ttu-id="07585-134">스크립트 도움말 항목을 전체적으로 스크립트를 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-134">In a script help topic, explain how to use the script as a whole.</span></span> <span data-ttu-id="07585-135">스크립트에서 함수에 대 한 도움말 항목을 한도 작성 하는 경우 스크립트 도움말 항목에 함수를 언급 하 고 스크립트 도움말 항목의 관련 링크 섹션에 함수 도움말 항목에 대 한 참조를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-135">If you are also writing help topics for functions in the script, mention the functions in your script help topic and include references to the function help topics in the Related Links section of the script help topic.</span></span> <span data-ttu-id="07585-136">반대로, 함수를 스크립트의 일부 이면 설명 함수 도움말 항목의 함수에 스크립트를 어떻게 사용할 수 있습니다 하지 독립적으로 수행 하는 역할입니다.</span><span class="sxs-lookup"><span data-stu-id="07585-136">Conversely, when a function is part of a script, explain in the function help topic the role that the function plays in the script and how it might be used independently.</span></span> <span data-ttu-id="07585-137">다음 함수 도움말 항목의 관련 링크 섹션의 스크립트 도움말 항목을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-137">Then list the script help topic in the Related Links section of the function help topic.</span></span>

- <span data-ttu-id="07585-138">스크립트 도움말 항목에 대 한 예제를 작성 하는 경우에 예제 명령에서 스크립트 파일의 경로를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-138">When writing examples for a script help topic, be sure to include the path to the script file in the example command.</span></span> <span data-ttu-id="07585-139">이러한 경로 지정 해야 명시적으로 스크립트는 현재 디렉터리의 경우에 사용자가 기억 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-139">This reminds users that they must specify the path explicitly, even when the script is in the current directory.</span></span>

- <span data-ttu-id="07585-140">함수 도움말 항목에는 함수가 현재 세션에만 존재 하 고, 다른 세션에서 사용 하려면 PowerShell 프로필을 추가 하거나, 추가 사용자에 게 알림.</span><span class="sxs-lookup"><span data-stu-id="07585-140">In a function help topic, remind users that the function exists only in the current session and, to use it in other sessions, they need to add it, or add it a PowerShell profile.</span></span>

- <span data-ttu-id="07585-141">`Get-Help` 스크립트 파일 및 도움말 항목 파일의 올바른 위치에 저장 되는 경우에 스크립트 또는 함수에 대 한 도움말 항목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-141">`Get-Help` displays the help topic for a script or function only when the script file and help topic files are saved in the correct locations.</span></span> <span data-ttu-id="07585-142">따라서 PowerShell을 설치 또는 저장 하거나 함수나 스크립트 도움말 항목의 스크립트 또는 함수를 설치 하기 위한 지침을 포함 하도록 유용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07585-142">Therefore, it is not useful to include instructions for installing PowerShell, or saving or installing the script or function in a script or function help topic.</span></span> <span data-ttu-id="07585-143">대신 스크립트 또는 함수를 배포 하는 데 사용 하는 문서에는 설치 지침을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-143">Instead, include any installation instructions in the document that you use to distribute the script or function.</span></span>

## <a name="see-also"></a><span data-ttu-id="07585-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07585-144">See Also</span></span>

 [<span data-ttu-id="07585-145">스크립트 및 함수에 대 한 XML 기반 도움말 항목을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-145">Writing XML-Based Help Topics for Scripts and Functions</span></span>](./writing-xml-based-help-topics-for-scripts-and-functions.md)

 [<span data-ttu-id="07585-146">명령에 대 한 XML 기반 도움말 항목을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="07585-146">Writing XML-Based Help Topics for Commands</span></span>](./writing-xml-based-help-topics-for-commands.md)

 [<span data-ttu-id="07585-147">쓰기 설명 기반 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="07585-147">Writing Comment-Based Help Topics</span></span>](./writing-comment-based-help-topics.md)
