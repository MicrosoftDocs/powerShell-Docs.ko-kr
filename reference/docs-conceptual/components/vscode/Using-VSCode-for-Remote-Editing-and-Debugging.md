---
title: Visual Studio Code를 사용하여 원격 편집 및 디버깅
description: Visual Studio Code를 사용하여 원격 편집 및 디버깅
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086677"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="d52a4-103">Visual Studio Code를 사용하여 원격 편집 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="d52a4-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="d52a4-104">ISE에 친숙한 사용자는 통합 콘솔에서 `psedit file.ps1`을 실행하여 ISE에서 바로 로컬 또는 원격 파일을 열 수 있다는 것을 기억할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="d52a4-105">결과적으로 이 기능은 VSCode용 PowerShell 확장에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="d52a4-106">이 가이드에서는 사용 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d52a4-107">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="d52a4-107">Prerequisites</span></span>

<span data-ttu-id="d52a4-108">이 가이드에서는 다음이 준비되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="d52a4-109">액세스할 수 있는 원격 리소스(예: VM, 컨테이너)</span><span class="sxs-lookup"><span data-stu-id="d52a4-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="d52a4-110">해당 리소스를 실행하는 PowerShell 및 호스트 머신</span><span class="sxs-lookup"><span data-stu-id="d52a4-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="d52a4-111">VSCode 및 VSCode용 PowerShell 확장</span><span class="sxs-lookup"><span data-stu-id="d52a4-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="d52a4-112">이 기능은 Windows PowerShell 및 PowerShell Core에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="d52a4-113">이 기능은 WinRM, PowerShell Direct 또는 SSH를 통해 원격 컴퓨터에 연결할 경우에도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="d52a4-114">Windows를 사용 중이지만 SSH를 사용하려면 [Win32 버전의 SSH](https://github.com/PowerShell/Win32-OpenSSH)를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="d52a4-115">다음</span><span class="sxs-lookup"><span data-stu-id="d52a4-115">Let's go</span></span>

<span data-ttu-id="d52a4-116">이 섹션에서는 Azure에서 실행되는 Ubuntu VM에 대한 내 MacBook Pro의 원격 편집 및 디버깅을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="d52a4-117">Windows를 사용하지 않을 수 있지만 **프로세스는 동일합니다**.</span><span class="sxs-lookup"><span data-stu-id="d52a4-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="d52a4-118">Open-EditorFile을 사용한 로컬 파일 편집</span><span class="sxs-lookup"><span data-stu-id="d52a4-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="d52a4-119">VSCode용 PowerShell 확장을 시작하고 PowerShell 통합 콘솔을 연 상태에서 `Open-EditorFile foo.ps1` 또는 `psedit foo.ps1`을 입력하여 편집기에서 바로 로컬 foo.ps1 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Open-EditorFile foo.ps1은 로컬에서 작동함](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="d52a4-121">기존 foo.ps1이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="d52a4-122">이 상태에서 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-122">From there, we can:</span></span>

<span data-ttu-id="d52a4-123">여백에 중단점을 추가하고 ![여백에 중단점 추가](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="d52a4-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="d52a4-124">F5 키를 눌러 PowerShell 스크립트를 디버그합니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="d52a4-125">![PowerShell 로컬 스크립트 디버그](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="d52a4-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="d52a4-126">디버깅하는 동안 디버그 콘솔을 조작하고, 왼쪽 범위의 변수 및 모든 기타 표준 디버깅 도구를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="d52a4-127">Open-EditorFile을 사용한 원격 파일 편집</span><span class="sxs-lookup"><span data-stu-id="d52a4-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="d52a4-128">이제 원격 파일 편집 및 디버깅을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="d52a4-129">단계는 거의 동일하고, 먼저 수행해야 하는 하나의 작업은 원격 서버에 대한 PowerShell 세션을 시작하는 것뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="d52a4-130">이 작업을 수행할 cmdlet이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="d52a4-131">이 cmdlet을 `Enter-PSSession`라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="d52a4-132">cmdlet에 대한 간략한 설명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="d52a4-133">`Enter-PSSession -ComputerName foo`는 WinRM을 통해 세션을 시작함</span><span class="sxs-lookup"><span data-stu-id="d52a4-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="d52a4-134">`Enter-PSSession -ContainerId foo` 및 `Enter-PSSession -VmId foo`는 PowerShell Direct를 통해 세션을 시작함</span><span class="sxs-lookup"><span data-stu-id="d52a4-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="d52a4-135">`Enter-PSSession -HostName foo`는 SSH를 통해 세션을 시작함</span><span class="sxs-lookup"><span data-stu-id="d52a4-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="d52a4-136">`Enter-PSSession`에 대한 자세한 내용은 [여기서](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6) 문서를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="d52a4-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="d52a4-137">macOS에서 Azure의 Ubuntu VM로 이동 중이므로 원격에 SSH를 사용하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="d52a4-138">먼저, 통합 콘솔에서 Enter-PSSession을 실행하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="d52a4-139">`[something]`이 프롬프트의 왼쪽에 표시되므로 해당 세션에 있음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![Enter-PSSession 호출](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="d52a4-141">여기에서 로컬 스크립트를 편집하는 것처럼 정확한 단계를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="d52a4-142">`Open-EditorFile test.ps1` 또는 `psedit test.ps1`을 실행하여 원격 `test.ps1` 파일 ![Open-EditorFile test.ps1 파일](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="d52a4-143">파일 편집/중단점 설정</span><span class="sxs-lookup"><span data-stu-id="d52a4-143">Edit the file/set breakpoints</span></span> ![중단점 편집 및 설정](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="d52a4-145">원격 파일 디버그 시작(F5)</span><span class="sxs-lookup"><span data-stu-id="d52a4-145">Start debugging (F5) the remote file</span></span>

![원격 파일 디버깅](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="d52a4-147">이것이 전부입니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-147">That's all there's to it!</span></span> <span data-ttu-id="d52a4-148">이 가이드가 VSCode에서 PowerShell을 원격 디버깅 및 편집하는 작업에 관련된 모든 질문을 해결하는 데 도움이 되었기를 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="d52a4-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="d52a4-149">문제가 있는 경우 [GitHub 리포지토리](http://github.com/powershell/vscode-powershell)에서 자유롭게 문제를 시작하세요.</span><span class="sxs-lookup"><span data-stu-id="d52a4-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>
