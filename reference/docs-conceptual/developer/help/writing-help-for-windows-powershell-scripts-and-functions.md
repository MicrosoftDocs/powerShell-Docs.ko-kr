---
title: PowerShell 스크립트 및 함수에 대 한 도움말 작성
ms.date: 09/13/2016
ms.openlocfilehash: 381c501d87b7381075f89412f654c6121493856e
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892917"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a><span data-ttu-id="3c441-102">PowerShell 스크립트 및 함수에 대 한 도움말 작성</span><span class="sxs-lookup"><span data-stu-id="3c441-102">Writing Help for PowerShell Scripts and Functions</span></span>

<span data-ttu-id="3c441-103">PowerShell 스크립트 및 함수는 다른 사용자와 공유 될 때마다 완전히 문서화 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-103">PowerShell scripts and functions should be fully documented whenever they are shared with others.</span></span>
<span data-ttu-id="3c441-104">`Get-Help`Cmdlet은 cmdlet에 대 한 도움말을 표시 하는 것과 같은 형식으로 스크립트 및 함수 도움말 항목을 표시 하 고 모든 `Get-Help` 매개 변수는 스크립트 및 함수 도움말 항목에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-104">The `Get-Help` cmdlet displays the script and function help topics in the same format as it displays help for cmdlets, and all of the `Get-Help` parameters work on script and function help topics.</span></span>

<span data-ttu-id="3c441-105">PowerShell 스크립트에는 스크립트에 대 한 도움말 항목과 스크립트의 각 함수에 대 한 도움말 항목이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-105">PowerShell scripts can include a help topic about the script and help topics about each functions in the script.</span></span> <span data-ttu-id="3c441-106">스크립트와 독립적으로 공유 되는 함수에는 고유한 도움말 항목이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-106">Functions that are shared independently of scripts can include their own help topics.</span></span>

<span data-ttu-id="3c441-107">이 문서에서는 도움말 항목의 형식 및 올바른 배치에 대해 설명 하 고 콘텐츠에 대 한 지침을 제안 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-107">This document explains the format and correct placement of the help topics, and it suggests guidelines for the content.</span></span>

## <a name="types-of-script-and-function-help"></a><span data-ttu-id="3c441-108">스크립트 유형 및 함수 도움말</span><span class="sxs-lookup"><span data-stu-id="3c441-108">Types of Script and Function Help</span></span>

### <a name="comment-based-help"></a><span data-ttu-id="3c441-109">주석 기반 도움말</span><span class="sxs-lookup"><span data-stu-id="3c441-109">Comment-Based Help</span></span>

<span data-ttu-id="3c441-110">스크립트나 함수를 설명 하는 도움말 항목을 스크립트나 함수 내의 주석 집합으로 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-110">The help topic that describes a script or function can be implemented as a set of comments within the script or function.</span></span> <span data-ttu-id="3c441-111">스크립트 및 스크립트의 함수에 대 한 주석 기반 도움말을 작성 하는 경우 주석 기반 도움말을 저장 하는 규칙에 주의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-111">When writing comment-based help for a script and for functions in a script, pay careful attention to the rules for placing the comment-based help.</span></span> <span data-ttu-id="3c441-112">배치는 `Get-Help` cmdlet이 도움말 항목과 스크립트 또는 함수를 연결 하는지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-112">The placement determines whether the `Get-Help` cmdlet associates the help topic with the script or a function.</span></span> <span data-ttu-id="3c441-113">주석 기반 도움말 항목을 작성 하는 방법에 대 한 자세한 내용은 [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3c441-113">For more information about writing comment-based help topics, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

### <a name="xml-based-command-help"></a><span data-ttu-id="3c441-114">XML 기반 명령 도움말</span><span class="sxs-lookup"><span data-stu-id="3c441-114">XML-Based Command Help</span></span>

<span data-ttu-id="3c441-115">스크립트나 함수를 설명 하는 도움말 항목은 명령 도움말 스키마를 사용 하는 XML 파일에서 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-115">The help topic that describes a script or function can be implemented in an XML file that uses the command help schema.</span></span> <span data-ttu-id="3c441-116">스크립트나 함수를 XML 파일에 연결 하려면 `ExternalHelp` comment 키워드와 xml 파일의 경로 및 이름을 차례로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-116">To associate the script or function with the XML file, use the `ExternalHelp` comment keyword followed by the path and name of the XML file.</span></span>

<span data-ttu-id="3c441-117">`ExternalHelp`설명 키워드가 있으면에서 `Get-Help` 키워드의 값과 일치 하는 도움말 파일을 찾을 수 없는 경우에도 주석 기반 도움말 보다 우선적으로 적용 됩니다 `ExternalHelp` .</span><span class="sxs-lookup"><span data-stu-id="3c441-117">When the `ExternalHelp` comment keyword is present, it takes precedence over comment-based help, even when `Get-Help` cannot find a help file that matches the value of the `ExternalHelp` keyword.</span></span>

### <a name="online-help"></a><span data-ttu-id="3c441-118">온라인 도움말</span><span class="sxs-lookup"><span data-stu-id="3c441-118">Online Help</span></span>

<span data-ttu-id="3c441-119">인터넷에서 도움말 항목을 게시 한 다음 직접 `Get-Help` 항목을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-119">You can post your help topics on the internet and then direct `Get-Help` to open the topics.</span></span> <span data-ttu-id="3c441-120">주석 기반 도움말 항목을 작성 하는 방법에 대 한 자세한 내용은 [온라인 도움말 지원](../module/supporting-online-help.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="3c441-120">For more information about writing comment-based help topics, see [Supporting Online Help](../module/supporting-online-help.md).</span></span>

<span data-ttu-id="3c441-121">스크립트 및 함수에 대 한 개념 ("정보") 항목을 작성 하는 방법은 설정 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-121">There is no established method for writing conceptual ("About") topics for scripts and functions.</span></span>
<span data-ttu-id="3c441-122">그러나 도움말 항목의 관련 링크 섹션에 있는 항목 및 해당 Url은 인터넷 목록의 개념 항목에 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-122">However, you can post conceptual topics on the internet list the topics and their URLs in the Related Links section of a command help topic.</span></span>

## <a name="content-considerations-for-script-and-function-help"></a><span data-ttu-id="3c441-123">스크립트 및 함수 도움말에 대 한 내용 고려 사항</span><span class="sxs-lookup"><span data-stu-id="3c441-123">Content Considerations for Script and Function Help</span></span>

- <span data-ttu-id="3c441-124">사용 가능한 명령 도움말 섹션 중 일부만 포함 하는 매우 간단한 도움말 항목을 작성 하는 경우 스크립트 또는 함수 매개 변수에 대 한 명확한 설명을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-124">If you are writing a very brief help topic with only a few of the available command help sections, be sure to include clear descriptions of the script or function parameters.</span></span> <span data-ttu-id="3c441-125">예제 섹션에서 예제 설명을 생략 하는 경우에도 하나 또는 두 개의 샘플 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-125">Also include one or two sample commands in the examples section, even if you decide to omit example descriptions.</span></span>

- <span data-ttu-id="3c441-126">모든 설명에서 스크립트 또는 함수로 명령을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3c441-126">In all descriptions, refer to the command as a script or function.</span></span> <span data-ttu-id="3c441-127">이 정보는 사용자가 명령을 이해 하 고 관리 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-127">This information helps the user to understand and manage the command.</span></span>

  <span data-ttu-id="3c441-128">예를 들어, 다음의 자세한 설명은 새 항목 명령이 스크립트 라는 것을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-128">For example, the following detailed description states that the New-Topic command is a script.</span></span>
  <span data-ttu-id="3c441-129">이를 통해 사용자에 게 경로 및 전체 이름을 지정 해야 함을 사용자에 게 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-129">This reminds users that they need to specify the path and full name when they run it.</span></span>

  > <span data-ttu-id="3c441-130">"새 항목 스크립트는 입력 파일의 각 항목 이름에 대 한 빈 개념 항목을 만듭니다."</span><span class="sxs-lookup"><span data-stu-id="3c441-130">"The New-Topic script creates a blank conceptual topic for each topic name in the input file..."</span></span>

  <span data-ttu-id="3c441-131">다음은 함수에 대 한 자세한 설명입니다 `Disable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="3c441-131">The following detailed description states that `Disable-PSRemoting` is a function.</span></span> <span data-ttu-id="3c441-132">이 정보는 세션에 이름이 같은 명령이 여러 개 포함 되어 있는 경우 사용자에 게 특히 유용 합니다 .이 중 일부는 우선 순위가 높은 명령에 의해 숨겨질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-132">This information is particularly useful to users when the session includes multiple commands with the same name, some of which might be hidden by a command with higher precedence.</span></span>

  > <span data-ttu-id="3c441-133">이 `Disable-PSRemoting` 함수는 로컬 컴퓨터의 모든 세션 구성을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-133">The `Disable-PSRemoting` function disables all session configurations on the local computer...</span></span>

- <span data-ttu-id="3c441-134">스크립트 도움말 항목에서 전체 스크립트를 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-134">In a script help topic, explain how to use the script as a whole.</span></span> <span data-ttu-id="3c441-135">또한 스크립트에서 함수에 대 한 도움말 항목을 작성 하는 경우 스크립트 도움말 항목의 함수에 대해 설명 하 고 스크립트 도움말 항목의 관련 링크 섹션에 있는 함수 도움말 항목에 대 한 참조를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-135">If you are also writing help topics for functions in the script, mention the functions in your script help topic and include references to the function help topics in the Related Links section of the script help topic.</span></span>
  <span data-ttu-id="3c441-136">반대로 함수가 스크립트의 일부인 경우 함수 도움말 항목에서 함수가 스크립트에서 수행 하는 역할과 독립적으로 사용 되는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-136">Conversely, when a function is part of a script, explain in the function help topic the role that the function plays in the script and how it might be used independently.</span></span> <span data-ttu-id="3c441-137">그런 다음 함수 도움말 항목의 관련 링크 섹션에 있는 스크립트 도움말 항목을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-137">Then list the script help topic in the Related Links section of the function help topic.</span></span>

- <span data-ttu-id="3c441-138">스크립트 도움말 항목에 대 한 예제를 작성할 때는 예제 명령에 스크립트 파일의 경로를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-138">When writing examples for a script help topic, be sure to include the path to the script file in the example command.</span></span> <span data-ttu-id="3c441-139">이렇게 하면 스크립트가 현재 디렉터리에 있는 경우에도 사용자에 게 경로를 명시적으로 지정 해야 한다는 사실을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-139">This reminds users that they must specify the path explicitly, even when the script is in the current directory.</span></span>

- <span data-ttu-id="3c441-140">함수 도움말 항목에서 현재 세션에만 존재 하는 함수를 사용자에 게 알려 서 다른 세션에서 사용 하려면 해당 함수를 추가 하거나 PowerShell 프로필을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-140">In a function help topic, remind users that the function exists only in the current session and, to use it in other sessions, they need to add it, or add it a PowerShell profile.</span></span>

- <span data-ttu-id="3c441-141">`Get-Help`스크립트 파일 및 도움말 항목 파일을 올바른 위치에 저장 한 경우에만 스크립트나 함수에 대 한 도움말 항목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-141">`Get-Help` displays the help topic for a script or function only when the script file and help topic files are saved in the correct locations.</span></span> <span data-ttu-id="3c441-142">따라서 PowerShell 설치에 대 한 지침을 포함 하거나 스크립트나 함수 도움말 항목에서 스크립트나 함수를 저장 하거나 설치 하는 데 대 한 지침을 포함 하는 것은 유용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-142">Therefore, it is not useful to include instructions for installing PowerShell, or saving or installing the script or function in a script or function help topic.</span></span> <span data-ttu-id="3c441-143">대신 스크립트나 함수를 배포 하는 데 사용 하는 문서에 설치 지침을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c441-143">Instead, include any installation instructions in the document that you use to distribute the script or function.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c441-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c441-144">See Also</span></span>

[<span data-ttu-id="3c441-145">설명 기반 도움말 항목 작성</span><span class="sxs-lookup"><span data-stu-id="3c441-145">Writing Comment-Based Help Topics</span></span>](./writing-comment-based-help-topics.md)
