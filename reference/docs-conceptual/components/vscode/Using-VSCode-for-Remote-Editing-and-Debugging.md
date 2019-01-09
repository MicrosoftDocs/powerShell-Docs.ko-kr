---
title: Visual Studio Code를 사용하여 원격 편집 및 디버깅
description: Visual Studio Code를 사용하여 원격 편집 및 디버깅
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655637"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="d6bea-103">Visual Studio Code를 사용하여 원격 편집 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="d6bea-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="d6bea-104">ISE에 익숙한 사용자에 대해 것을 기억할 것 실행할 수 있습니다 `psedit file.ps1` ISE에서 마우스 오른쪽 단추로 파일-로컬 또는 원격-열려는 통합된 콘솔에서.</span><span class="sxs-lookup"><span data-stu-id="d6bea-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="d6bea-105">결과적으로,이 기능은 또한 VSCode 용 PowerShell 확장에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="d6bea-106">이 가이드에서는 작업을 수행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d6bea-107">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="d6bea-107">Prerequisites</span></span>

<span data-ttu-id="d6bea-108">이 가이드에서는 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="d6bea-109">원격 리소스 (예: VM, 컨테이너)에 액세스할 수</span><span class="sxs-lookup"><span data-stu-id="d6bea-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="d6bea-110">호스트 컴퓨터에서 실행 되는 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6bea-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="d6bea-111">VSCode 및 VSCode 용 PowerShell 확장</span><span class="sxs-lookup"><span data-stu-id="d6bea-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="d6bea-112">이 기능은 Windows PowerShell 및 PowerShell Core에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="d6bea-113">이 기능은 WinRM, PowerShell Direct 또는 SSH를 통해 원격 컴퓨터에 연결할 때에 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="d6bea-114">SSH를 사용 하려면 Windows를 사용 하는 경우 체크 아웃 합니다 [SSH의 Win32 버전](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="d6bea-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="d6bea-115">다음</span><span class="sxs-lookup"><span data-stu-id="d6bea-115">Let's go</span></span>

<span data-ttu-id="d6bea-116">이 섹션에서는 살펴보겠습니다 원격으로 편집 하 고 Azure에서 실행 중인 Ubuntu VM에 내 MacBook Pro에서 디버깅 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="d6bea-117">I 사용 하지 않을 수도 Windows, 하지만 **프로세스는 동일**합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="d6bea-118">로컬 파일 열기-EditorFile를 사용 하 여 편집</span><span class="sxs-lookup"><span data-stu-id="d6bea-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="d6bea-119">PowerShell 확장을 사용 하 여 VSCode에서 시작 하 고 PowerShell 통합 콘솔을 열에 입력할 수 있습니다 `Open-EditorFile foo.ps1` 또는 `psedit foo.ps1` 를 편집기에서 직접 로컬 foo.ps1 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![로컬에서 제대로 작동 오픈 EditorFile foo.ps1](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="d6bea-121">foo.ps1 이미 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="d6bea-122">여기에서 다음과 같은 것을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-122">From there, we can:</span></span>

<span data-ttu-id="d6bea-123">여백에 중단점을 추가할 ![여백에 중단점을 추가 합니다.](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="d6bea-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="d6bea-124">및 PowerShell 스크립트를 디버그 하려면 f5 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="d6bea-125">![로컬 PowerShell 스크립트 디버깅](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="d6bea-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="d6bea-126">디버깅 하는 동안 디버그 콘솔과 상호 작용, 왼쪽 및 디버깅 도구는 다른 모든 표준에 대 한 범위에서 변수를 확인 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="d6bea-127">원격 파일 열기-EditorFile를 사용 하 여 편집</span><span class="sxs-lookup"><span data-stu-id="d6bea-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="d6bea-128">이제 원격 파일 편집 및 디버깅에 대해 알아보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="d6bea-129">단계는 거의 동일는 하나만 가장 먼저-원격 서버에는 PowerShell 세션을 입력 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="d6bea-130">이렇게 하려면에 대 한 cmdlet이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="d6bea-131">라고 `Enter-PSSession`합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="d6bea-132">Cmdlet의 축소 기능이 축소 설명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="d6bea-133">`Enter-PSSession -ComputerName foo` WinRM 통해 세션 시작</span><span class="sxs-lookup"><span data-stu-id="d6bea-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="d6bea-134">`Enter-PSSession -ContainerId foo` 및 `Enter-PSSession -VmId foo` PowerShell Direct를 통해 세션 시작</span><span class="sxs-lookup"><span data-stu-id="d6bea-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="d6bea-135">`Enter-PSSession -HostName foo` SSH 통해 세션 시작</span><span class="sxs-lookup"><span data-stu-id="d6bea-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="d6bea-136">에 대 한 자세한 내용은 `Enter-PSSession`, 문서를 체크 아웃 [여기](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6)합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="d6bea-137">사용해 보려고 SSH 원격 이므로 Azure에서 Ubuntu VM에 macOS에서 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="d6bea-138">첫째, 통합 콘솔에서이 Enter-pssession을 실행 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="d6bea-139">때문에 세션에는 알 수 `[something]` 프롬프트에 왼쪽에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![Enter-pssession에 대 한 호출](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="d6bea-141">여기에서 우리가 해결할 수는 정확한 단계는 로컬 스크립트를 편집 하 던 것 처럼 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="d6bea-142">실행 `Open-EditorFile test.ps1` 나 `psedit test.ps1` 원격 열려는 `test.ps1` 파일 ![test.ps1 파일 열기-EditorFile](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="d6bea-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="d6bea-143">중단점 파일/설정 편집</span><span class="sxs-lookup"><span data-stu-id="d6bea-143">Edit the file/set breakpoints</span></span> ![편집 하 고 중단점 설정](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="d6bea-145">원격 파일 f5 키를 눌러 디버깅을 시작합니다</span><span class="sxs-lookup"><span data-stu-id="d6bea-145">Start debugging (F5) the remote file</span></span>

![원격 파일 디버깅](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="d6bea-147">이것이 전부입니다!</span><span class="sxs-lookup"><span data-stu-id="d6bea-147">That's all there's to it!</span></span> <span data-ttu-id="d6bea-148">원격 디버깅 및 VSCode에서 PowerShell을 편집 하는 방법에 대 한 질문의 선택을 취소 하는 데 도움이이 가이드는 하시기 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="d6bea-149">를 문제가 있는 경우 자유롭게 사안의 [GitHub 리포지토리에서](http://github.com/powershell/vscode-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bea-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>
