---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell에 대한 자세한 정보"
ms.assetid: 979654ae-7994-47f8-be43-d79e7a140143
ms.openlocfilehash: 5e6d1bb4d8915ba3c83ba0020b959e444b5211cd
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2018
---
# <a name="about-windows-powershell"></a><span data-ttu-id="2023d-103">Windows PowerShell에 대한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="2023d-103">About Windows PowerShell</span></span>
<span data-ttu-id="2023d-104">Windows PowerShell은 장기적인 문제를 제거하고 새로운 기능을 추가하여 명령줄 및 스크립팅 환경을 개선하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-104">Windows PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

## <a name="discoverability"></a><span data-ttu-id="2023d-105">검색 기능</span><span class="sxs-lookup"><span data-stu-id="2023d-105">Discoverability</span></span>
<span data-ttu-id="2023d-106">Windows PowerShell을 사용하면 해당 기능을 쉽게 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-106">Windows PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="2023d-107">예를 들어 Windows 서비스를 보고 변경하는 cmdlet 목록을 찾으려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-107">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```
Get-Command *-Service
```

<span data-ttu-id="2023d-108">작업을 수행하는 cmdlet을 검색한 후 Get-Help cmdlet을 사용하여 cmdlet에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-108">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the Get-Help cmdlet.</span></span> <span data-ttu-id="2023d-109">예를 들어 Get-Service cmdlet에 대한 도움말을 표시하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-109">For example, to display help about the Get-Service cmdlet, type:</span></span>

```
Get-Help Get-Service
```
<span data-ttu-id="2023d-110">대부분의 cmdlet은 조작한 다음 텍스트로 렌더링하여 표시할 수 있는 개체를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-110">Most cmdlets emit objects which can be manipulated and then rendered into text for display.</span></span> <span data-ttu-id="2023d-111">해당 cmdlet의 출력을 완벽하게 이해하려면 출력을 Get-Member cmdlet에 파이프합니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-111">To fully understand the output of that cmdlet, pipe its output to the Get-Member cmdlet.</span></span> <span data-ttu-id="2023d-112">예를 들어 다음 명령은 Get-Service cmdlet에 의한 개체 출력의 멤버에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-112">For example, the following command displays information about the members of the object output by the Get-Service cmdlet.</span></span>

```
Get-Service | Get-Member
```

## <a name="consistency"></a><span data-ttu-id="2023d-113">Consistency</span><span class="sxs-lookup"><span data-stu-id="2023d-113">Consistency</span></span>
<span data-ttu-id="2023d-114">시스템 관리는 내재된 복잡성을 제어하는 데 도움이 되는 일관된 인터페이스가 있는 도구 및 복잡한 노력일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-114">Managing systems can be a complex endeavor and tools that have a consistent interface help to control the inherent complexity.</span></span> <span data-ttu-id="2023d-115">일관성으로 알려진 명령줄 도구 및 스크립트 가능한 COM 개체는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-115">Unfortunately, neither command-line tools nor scriptable COM objects have been known for their consistency.</span></span>

<span data-ttu-id="2023d-116">Windows PowerShell의 일관성은 기본 자산 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-116">The consistency of Windows PowerShell is one of its primary assets.</span></span> <span data-ttu-id="2023d-117">예를 들어 Sort-Object cmdlet을 사용하는 방법을 배운 경우 해당 지식을 사용하여 모든 cmdlet의 출력을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-117">For example, if you learn how to use the Sort-Object cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span> <span data-ttu-id="2023d-118">각 cmdlet의 다른 정렬 루틴을 배울 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-118">You do not have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="2023d-119">또한 cmdlet 개발자는 해당 cmdlet의 정렬 기능을 디자인할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-119">In addition, cmdlet developers do not have to design sorting features for their cmdlets.</span></span> <span data-ttu-id="2023d-120">Windows PowerShell에서 기본 기능을 지원하는 프레임워크를 제공하며 인터페이스의 여러 측면에서 강제로 일관성을 유지하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-120">Windows PowerShell gives them a framework that provides the basic features and forces them to be consistent about many aspects of the interface.</span></span> <span data-ttu-id="2023d-121">프레임워크는 일반적으로 개발자가 선택하는 몇 가지 사항을 제거하지만, 그 대신 강력하고 사용하기 쉬운 cmdlet을 훨씬 더 간단하게 개발할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-121">The framework eliminates some of the choices that are typically left to the developer, but, in return, it makes the development of robust and easy-to-use cmdlets much simpler.</span></span>

## <a name="interactive-and-scripting-environments"></a><span data-ttu-id="2023d-122">대화형 및 스크립팅 환경</span><span class="sxs-lookup"><span data-stu-id="2023d-122">Interactive and Scripting Environments</span></span>
<span data-ttu-id="2023d-123">Windows PowerShell은 명령줄 도구와 COM 개체에 대한 액세스를 제공하고 .NET FCL(Framework 클래스 라이브러리)의 기능을 사용할 수 있게 해주는 결합된 대화형 및 스크립팅 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-123">Windows PowerShell is a combined interactive and scripting environment that gives you access to command-line tools and COM objects, and also enables you to use the power of the .NET Framework Class Library (FCL).</span></span>

<span data-ttu-id="2023d-124">이 환경은 대화형 환경에 여러 명령줄 도구를 제공하는 Windows 명령 프롬프트를 개선합니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-124">This environment improves upon the Windows Command Prompt, which provides an interactive environment with multiple command-line tools.</span></span> <span data-ttu-id="2023d-125">또한 여러 명령줄 도구와 COM 자동화 개체를 사용할 수 있게 하지만 대화형 환경을 제공하지 않는 WSH(Windows 스크립트 호스트) 스크립트를 개선합니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-125">It also improves upon Windows Script Host (WSH) scripts, which let you use multiple command-line tools and COM automation objects, but do not provide an interactive environment.</span></span>

<span data-ttu-id="2023d-126">Windows PowerShell은 이러한 모든 기능에 대한 액세스를 결합하여 대화형 사용자와 스크립트 작성자의 능력을 확장하고 시스템 관리를 보다 관리가 용이하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-126">By combining access to all of these features, Windows PowerShell extends the ability of the interactive user and the script writer, and makes system administration more manageable.</span></span>

## <a name="object-orientation"></a><span data-ttu-id="2023d-127">개체 방향</span><span class="sxs-lookup"><span data-stu-id="2023d-127">Object Orientation</span></span>
<span data-ttu-id="2023d-128">텍스트로 명령을 입력하여 Windows PowerShell을 조작하지만 Windows PowerShell은 텍스트가 아니라 개체를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-128">Although you interact with Windows PowerShell by typing commands in text, Windows PowerShell is based on objects, not text.</span></span> <span data-ttu-id="2023d-129">명령의 출력은 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-129">The output of a command is an object.</span></span> <span data-ttu-id="2023d-130">출력 개체를 다른 명령에 입력으로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-130">You can send the output object to another command as its input.</span></span> <span data-ttu-id="2023d-131">결과적으로, Windows PowerShell은 다른 셸에 익숙한 사용자에게 친숙한 인터페이스를 제공하는 동시에 새롭고 강력한 명령줄 패러다임을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-131">As a result, Windows PowerShell provides a familiar interface to people experienced with other shells, while introducing a new and powerful command-line paradigm.</span></span> <span data-ttu-id="2023d-132">텍스트 대신 개체를 보낼 수 있게 함으로써 명령 간에 데이터를 보내는 개념을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-132">It extends the concept of sending data between commands by enabling you to send objects, rather than text.</span></span>

## <a name="easy-transition-to-scripting"></a><span data-ttu-id="2023d-133">스크립팅으로 쉽게 전환</span><span class="sxs-lookup"><span data-stu-id="2023d-133">Easy Transition to Scripting</span></span>
<span data-ttu-id="2023d-134">Windows PowerShell을 사용하면 대화형 명령 입력에서 스크립트 생성 및 실행으로 쉽게 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-134">Windows PowerShell makes it easy to transition from typing commands interactively to creating and running scripts.</span></span> <span data-ttu-id="2023d-135">Windows PowerShell 명령 프롬프트에서 명령을 입력하여 작업을 수행하는 명령을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-135">You can type commands at the Windows PowerShell command prompt to discover the commands that perform a task.</span></span> <span data-ttu-id="2023d-136">그런 다음 스크립트로 사용하기 위해 파일에 복사하기 전에 해당 명령을 기록에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2023d-136">Then, you can save those commands in a transcript or a history before copying them to a file for use as a script.</span></span>
