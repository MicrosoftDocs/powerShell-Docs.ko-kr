---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: PowerShell 스크립팅
ms.openlocfilehash: 281f2e798b3d3fa1c150b079d633cb7e8490dcec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058491"
---
# <a name="powershell"></a><span data-ttu-id="98cea-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="98cea-103">PowerShell</span></span>

<span data-ttu-id="98cea-104">PowerShell은 .NET에서 구축된 작업 기반 명령줄 셸 및 스크립팅 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-104">PowerShell is a task-based command-line shell and scripting language built on .NET.</span></span>
<span data-ttu-id="98cea-105">PowerShell을 통해 시스템 관리자 및 고급 사용자는 운영 체제(Linux, macOS 및 Windows) 및 프로세스를 관리하는 작업을 신속하게 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-105">PowerShell helps system administrators and power-users rapidly automate tasks that manage operating systems (Linux, macOS, and Windows) and processes.</span></span>

<span data-ttu-id="98cea-106">PowerShell 명령을 사용하면 명령줄에서 컴퓨터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-106">PowerShell commands let you manage computers from the command line.</span></span> <span data-ttu-id="98cea-107">PowerShell 공급자는 파일 시스템에 액세스하는 것처럼 쉽게, 레지스트리 및 인증서 저장소와 같은 데이터 저장소에 액세스하도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-107">PowerShell providers let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="98cea-108">PowerShell은 충분한 식을 포함하는 파서와 완전히 개발된 스크립트 언어를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-108">PowerShell includes a rich expression parser and a fully developed scripting language.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="98cea-109">PowerShell이 오픈 소스로 제공됨</span><span class="sxs-lookup"><span data-stu-id="98cea-109">PowerShell is open-source</span></span>

<span data-ttu-id="98cea-110">이제 GitHub에서 PowerShell 기본 소스 코드를 사용할 수 있으며 커뮤니티 참여가 개방됩니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-110">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="98cea-111">[GitHub의 PowerShell 소스](https://github.com/powershell/powershell)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="98cea-111">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="98cea-112">[Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell)(PowerShell 다운로드)에서 필요한 비트로 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-112">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="98cea-113">또는 [시작](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)에서 둘러보기로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-113">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="98cea-114">PowerShell 디자인 목표</span><span class="sxs-lookup"><span data-stu-id="98cea-114">PowerShell design goals</span></span>

<span data-ttu-id="98cea-115">PowerShell은 장기적인 문제를 제거하고 새로운 기능을 추가하여 명령줄 및 스크립팅 환경을 개선하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-115">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="98cea-116">검색 기능</span><span class="sxs-lookup"><span data-stu-id="98cea-116">Discoverability</span></span>

<span data-ttu-id="98cea-117">PowerShell을 사용하면 해당 기능을 쉽게 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-117">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="98cea-118">예를 들어 Windows 서비스를 보고 변경하는 cmdlet 목록을 찾으려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-118">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="98cea-119">작업을 수행하는 cmdlet을 검색한 후 `Get-Help` cmdlet을 사용하여 cmdlet에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-119">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="98cea-120">예를 들어 `Get-Service` cmdlet에 대한 도움말을 표시하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-120">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```

<span data-ttu-id="98cea-121">대부분의 cmdlet은 조작한 다음 텍스트로 렌더링하여 표시할 수 있는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-121">Most cmdlets return objects that can be manipulated and then rendered as text for display.</span></span> <span data-ttu-id="98cea-122">해당 cmdlet의 출력을 완벽하게 이해하려면 출력을 `Get-Member` cmdlet에 파이프합니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-122">To fully understand the output of a cmdlet, pipe the output to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="98cea-123">예를 들어 다음 명령은 `Get-Service` cmdlet에 의한 개체 출력의 멤버에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-123">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="98cea-124">일관성</span><span class="sxs-lookup"><span data-stu-id="98cea-124">Consistency</span></span>

<span data-ttu-id="98cea-125">시스템 관리는 복잡한 작업일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-125">Managing systems can be a complex task.</span></span> <span data-ttu-id="98cea-126">도구에는 내재된 복잡성을 제어하는 데 도움이 되는 일관된 인터페이스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-126">Tools that have a consistent interface help to control the inherent complexity.</span></span> <span data-ttu-id="98cea-127">그렇지만 일관성이 입증된 명령줄 도구 및 스크립트 가능한 COM(구성 요소 개체 모델) 개체는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-127">Unfortunately, command-line tools and scriptable Component Object Model (COM) objects aren't known for their consistency.</span></span>

<span data-ttu-id="98cea-128">PowerShell의 일관성은 기본 자산 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-128">The consistency of PowerShell is one of its primary assets.</span></span> <span data-ttu-id="98cea-129">예를 들어 `Sort-Object` cmdlet을 사용하는 방법을 배운 경우 해당 지식을 사용하여 모든 cmdlet의 출력을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-129">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span> <span data-ttu-id="98cea-130">각 cmdlet의 다른 정렬 루틴을 배울 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-130">You don't have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="98cea-131">또한 cmdlet 개발자는 해당 cmdlet의 정렬 기능을 디자인할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-131">Additionally, cmdlet developers don't have to design sorting features for their cmdlets.</span></span> <span data-ttu-id="98cea-132">PowerShell은 일관성을 강제하는 기본 기능이 있는 프레임워크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-132">PowerShell provides a framework with the basic features that forces consistency.</span></span> <span data-ttu-id="98cea-133">이 프레임워크를 사용하면 개발자가 선택해야 할 사항이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-133">The framework eliminates some choices that are left to the developer.</span></span> <span data-ttu-id="98cea-134">하지만 cmdlet의 개발은 훨씬 더 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-134">But, in return, it makes the development of cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="98cea-135">대화형 및 스크립팅 환경</span><span class="sxs-lookup"><span data-stu-id="98cea-135">Interactive and scripting environments</span></span>

<span data-ttu-id="98cea-136">Windows 명령 프롬프트는 명령줄 도구 및 기본 스크립팅에 액세스할 수 있는 대화형 셸을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-136">The Windows Command Prompt provides an interactive shell with access to command-line tools and basic scripting.</span></span> <span data-ttu-id="98cea-137">WSH(Windows Script Host)에는 스크립트 가능한 명령줄 도구와 COM 자동화 개체가 있지만 대화형 셸은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-137">Windows Script Host (WSH) has scriptable command-line tools and COM automation objects, but doesn't provide an interactive shell.</span></span>

<span data-ttu-id="98cea-138">PowerShell은 대화형 셸과 스크립팅 환경을 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-138">PowerShell combines an interactive shell and a scripting environment.</span></span> <span data-ttu-id="98cea-139">PowerShell은 명령줄 도구, COM 개체 및 .NET 클래스 라이브러리에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-139">PowerShell can access command-line tools, COM objects, and .NET class libraries.</span></span> <span data-ttu-id="98cea-140">이러한 기능 조합으로 대화형 사용자, 스크립트 작성자 및 시스템 관리자의 역량이 확장될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-140">This combination of features extends the capabilities of the interactive user, the script writer, and the system administrator.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="98cea-141">개체 방향</span><span class="sxs-lookup"><span data-stu-id="98cea-141">Object orientation</span></span>

<span data-ttu-id="98cea-142">PowerShell은 텍스트가 아닌 개체를 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-142">PowerShell is based on object not text.</span></span> <span data-ttu-id="98cea-143">명령의 출력은 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-143">The output of a command is an object.</span></span> <span data-ttu-id="98cea-144">파이프라인을 통해 출력 개체를 다른 명령에 입력으로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-144">You can send the output object, through the pipeline, to another command as its input.</span></span>

<span data-ttu-id="98cea-145">이 파이프라인은 다른 셸에 익숙한 사용자에게 친숙한 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-145">This pipeline provides a familiar interface for people experienced with other shells.</span></span> <span data-ttu-id="98cea-146">PowerShell은 텍스트가 아니라 개체를 전송하여 이 개념을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-146">PowerShell extends this concept by sending objects rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="98cea-147">스크립팅으로 쉽게 전환</span><span class="sxs-lookup"><span data-stu-id="98cea-147">Easy transition to scripting</span></span>

<span data-ttu-id="98cea-148">PowerShell의 명령 검색 기능을 사용하면 대화형 명령 입력에서 스크립트 생성 및 실행으로 쉽게 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-148">PowerShell's command discoverability makes it easy to transition from typing commands interactively to creating and running scripts.</span></span> <span data-ttu-id="98cea-149">PowerShell 기록 및 내역을 통해 명령을 스크립트로 사용할 수 있게 쉽게 파일로 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98cea-149">PowerShell transcripts and history make it easy to copy commands to a file for use as a script.</span></span>
