---
title: Visual Studio Code를 사용하여 원격 편집 및 디버깅
description: Visual Studio Code를 사용하여 원격 편집 및 디버깅
ms.date: 06/13/2019
ms.openlocfilehash: 0394348b4dfbe813549c02035e9d3b035cba72e4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784642"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="8c051-103">Visual Studio Code를 사용하여 원격 편집 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="8c051-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="8c051-104">ISE에 친숙한 사용자는 통합 콘솔에서 `psedit file.ps1`을 실행하여 ISE에서 바로 로컬 또는 원격 파일을 열 수 있다는 것을 기억할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-104">For those of you that are familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="8c051-105">이 기능은 VSCode용 PowerShell 확장에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-105">This feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="8c051-106">이 가이드에서는 수행 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-106">This guide shows you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8c051-107">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="8c051-107">Prerequisites</span></span>

<span data-ttu-id="8c051-108">이 가이드에서는 다음이 준비되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="8c051-109">액세스할 수 있는 원격 리소스(예: VM, 컨테이너)</span><span class="sxs-lookup"><span data-stu-id="8c051-109">A remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="8c051-110">해당 리소스를 실행하는 PowerShell 및 호스트 머신</span><span class="sxs-lookup"><span data-stu-id="8c051-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="8c051-111">VSCode 및 VSCode용 PowerShell 확장</span><span class="sxs-lookup"><span data-stu-id="8c051-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="8c051-112">이 기능은 Windows PowerShell 및 PowerShell Core에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="8c051-113">이 기능은 WinRM, PowerShell Direct 또는 SSH를 통해 원격 컴퓨터에 연결할 경우에도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="8c051-114">Windows를 사용 중이지만 SSH를 사용하려면 [Win32 버전의 SSH](https://github.com/PowerShell/Win32-OpenSSH)를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8c051-115">`Open-EditorFile` 및 `psedit` 명령은 VSCode용 PowerShell 확장으로 만든 **PowerShell 통합 콘솔**에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-115">The `Open-EditorFile` and `psedit` commands only work in the **PowerShell Integrated Console** created by the PowerShell extension for VSCode.</span></span>

## <a name="usage-examples"></a><span data-ttu-id="8c051-116">사용 예</span><span class="sxs-lookup"><span data-stu-id="8c051-116">Usage examples</span></span>

<span data-ttu-id="8c051-117">이 예제에서는 Azure에서 실행되는 Ubuntu VM에 대한 내 MacBook Pro의 원격 편집 및 디버깅을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-117">These examples show remote editing and debugging from a MacBook Pro to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="8c051-118">프로세스는 Windows와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-118">The process is identical on Windows.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="8c051-119">Open-EditorFile을 사용한 로컬 파일 편집</span><span class="sxs-lookup"><span data-stu-id="8c051-119">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="8c051-120">VSCode용 PowerShell 확장을 시작하고 PowerShell 통합 콘솔을 연 상태에서 `Open-EditorFile foo.ps1` 또는 `psedit foo.ps1`을 입력하여 편집기에서 바로 로컬 foo.ps1 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-120">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Open-EditorFile foo.ps1은 로컬에서 작동함](media/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> <span data-ttu-id="8c051-122">`foo.ps1` 파일이 이미 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-122">The file `foo.ps1` must already exist.</span></span>

<span data-ttu-id="8c051-123">이 상태에서 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-123">From there, we can:</span></span>

- <span data-ttu-id="8c051-124">여백에 중단점 추가</span><span class="sxs-lookup"><span data-stu-id="8c051-124">Add breakpoints to the gutter</span></span>

  ![여백에 중단점 추가](media/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- <span data-ttu-id="8c051-126">F5 키를 눌러 PowerShell 스크립트를 디버깅합니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-126">Hit F5 to debug the PowerShell script.</span></span>

  ![로컬 PowerShell 스크립트 디버깅](media/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

<span data-ttu-id="8c051-128">디버깅하는 동안 디버그 콘솔을 조작하고, 왼쪽 범위의 변수 및 모든 기타 표준 디버깅 도구를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-128">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="8c051-129">Open-EditorFile을 사용한 원격 파일 편집</span><span class="sxs-lookup"><span data-stu-id="8c051-129">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="8c051-130">이제 원격 파일 편집 및 디버깅을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-130">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="8c051-131">단계는 거의 동일하고, 먼저 수행해야 하는 하나의 작업은 원격 서버에 대한 PowerShell 세션을 시작하는 것뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-131">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="8c051-132">이 작업을 수행할 cmdlet이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-132">There's a cmdlet for to do so.</span></span> <span data-ttu-id="8c051-133">이 cmdlet을 `Enter-PSSession`라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-133">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="8c051-134">cmdlet에 대한 간략한 설명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-134">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="8c051-135">`Enter-PSSession -ComputerName foo`는 WinRM을 통해 세션을 시작함</span><span class="sxs-lookup"><span data-stu-id="8c051-135">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="8c051-136">`Enter-PSSession -ContainerId foo` 및 `Enter-PSSession -VmId foo`는 PowerShell Direct를 통해 세션을 시작함</span><span class="sxs-lookup"><span data-stu-id="8c051-136">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="8c051-137">`Enter-PSSession -HostName foo`는 SSH를 통해 세션을 시작함</span><span class="sxs-lookup"><span data-stu-id="8c051-137">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="8c051-138">자세한 내용은 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession)의 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c051-138">For more information, see the documentation for [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span></span>

<span data-ttu-id="8c051-139">macOS에서 Azure의 Ubuntu VM로 이동 중이므로 원격에 SSH를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-139">Since we are going from macOS to an Ubuntu VM in Azure, we are using SSH for remoting.</span></span>

<span data-ttu-id="8c051-140">첫째, 통합 콘솔에서 `Enter-PSSession`을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-140">First, in the Integrated Console, run `Enter-PSSession`.</span></span> <span data-ttu-id="8c051-141">`[<hostname>]`이 프롬프트 왼쪽에 표시되면 원격 세션에 연결된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-141">You're connected to the remote session when `[<hostname>]` shows up to the left of your prompt.</span></span>

![Enter-PSSession을 호출하여 원격 세션에 연결](media/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

<span data-ttu-id="8c051-143">이제 로컬 스크립트를 편집하는 것처럼 같은 단계를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-143">Now, we can do the same steps as if we are editing a local script.</span></span>

1. <span data-ttu-id="8c051-144">`Open-EditorFile test.ps1` 또는 `psedit test.ps1`을 실행하여 원격 `test.ps1` 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-144">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file</span></span>

  ![원격 시스템에서 스크립트 편집](media/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. <span data-ttu-id="8c051-146">파일 편집/중단점 설정</span><span class="sxs-lookup"><span data-stu-id="8c051-146">Edit the file/set breakpoints</span></span>

   ![중단점 편집 및 설정](media/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. <span data-ttu-id="8c051-148">원격 파일 디버그 시작(F5)</span><span class="sxs-lookup"><span data-stu-id="8c051-148">Start debugging (F5) the remote file</span></span>

   ![원격 스크립트 디버깅](media/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

<span data-ttu-id="8c051-150">문제가 있는 경우 [GitHub 리포지토리](https://github.com/powershell/vscode-powershell)에서 문제를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c051-150">If you have any problems, you can open issues in the [GitHub repo](https://github.com/powershell/vscode-powershell).</span></span>
