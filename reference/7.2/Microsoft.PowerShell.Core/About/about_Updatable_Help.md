---
description: PowerShell에서 업데이트할 수 있는 도움말 시스템에 대해 설명 합니다.
Locale: en-US
ms.date: 08/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_updatable_help?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Updatable_Help
ms.openlocfilehash: d688448b5aab8ec35ab5d57b444ad9902b8e8ecd
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599358"
---
# <a name="about-updatable-help"></a><span data-ttu-id="4228d-103">업데이트할 수 있는 도움말 정보</span><span class="sxs-lookup"><span data-stu-id="4228d-103">About Updatable Help</span></span>

## <a name="short-description"></a><span data-ttu-id="4228d-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="4228d-104">Short description</span></span>
<span data-ttu-id="4228d-105">PowerShell에서 업데이트할 수 있는 도움말 시스템에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-105">Describes the updatable help system in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="4228d-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-106">Long description</span></span>

<span data-ttu-id="4228d-107">PowerShell은 PowerShell cmdlet 및 개념에 대 한 최신 도움말 항목에 액세스할 수 있는 여러 가지 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-107">PowerShell provides several different ways to access the most up-to-date help topics for PowerShell cmdlets and concepts.</span></span>

<span data-ttu-id="4228d-108">PowerShell 3.0에 도입 된 업데이트할 수 있는 도움말 시스템은 명령줄에서 읽을 수 있도록 로컬 컴퓨터에 항상 최신 도움말 항목을 제공 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-108">The Updatable Help system, introduced in PowerShell 3.0, is designed to assure that you always have the newest help topics on your local computer so that you can read them at the command line.</span></span> <span data-ttu-id="4228d-109">최신 도움말 파일을 사용할 수 있게 될 때마다 도움말 파일을 다운로드 하 여 설치 하 고 업데이트 하는 것이 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-109">It makes it easy to download and install help files and to update them whenever newer help files become available.</span></span>

<span data-ttu-id="4228d-110">엔터프라이즈의 여러 컴퓨터와 인터넷에 액세스할 수 없는 컴퓨터에 대 한 업데이트 된 도움말을 제공 하기 위해 업데이트할 수 있는 도움말을 사용 하 여 도움말 파일을 파일 시스템 디렉터리 또는 파일 공유로 다운로드 한 다음 파일 공유에서 도움말 파일을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-110">To provide updated help for multiple computers in an enterprise and for computers that do not have access to the internet, Updatable Help lets you download help files to a filesystem directory or file share, and then install the help files from the file share.</span></span>

<span data-ttu-id="4228d-111">PowerShell 4.0에서 **HelpInfoUri** 속성은 Windows PowerShell 원격을 통해 유지 됩니다 .이를 통해 `Save-Help` 원격 컴퓨터에 설치 된 모듈에 대해 작업을 수행할 수 있지만, 로컬 컴퓨터에 반드시 설치 해야 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-111">In PowerShell 4.0, the **HelpInfoUri** property is preserved over Windows PowerShell remoting, which allows `Save-Help` to work for modules that are installed on a remote computer, but are not necessarily installed on the local computer.</span></span> <span data-ttu-id="4228d-112">인터넷에 액세스할 수 없는 컴퓨터에서를 실행 하 여 **psmoduleinfo** 개체를 디스크 또는 이동식 미디어 (예: USB 드라이브)에 저장 하 `Export-Clixml` 고, 인터넷에 액세스할 수 있는 컴퓨터에서 **psmoduleinfo** 개체를 가져온 다음, `Save-Help` **psmoduleinfo** 개체에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-112">You can save a **PSModuleInfo** object to disk or removable media (such as a USB drive) by running `Export-Clixml` on a computer that does not have internet access, importing the **PSModuleInfo** object on a computer that does have internet access, and then running `Save-Help` on the **PSModuleInfo** object.</span></span> <span data-ttu-id="4228d-113">저장 된 도움말은 이동식 미디어를 사용 하 여 원격으로 연결 되지 않은 컴퓨터에 복사 된 다음를 실행 하 여 설치할 수 있습니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="4228d-113">The saved help can be copied to the remote, disconnected computer by using removable media, and then installed by running `Update-Help`.</span></span> <span data-ttu-id="4228d-114">이러한 기능 향상을 `Save-Help` 통해 어떤 종류의 네트워크 액세스가 없는 컴퓨터에 도움말을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-114">These improvements in `Save-Help` functionality let you install help on computers that are without any kind of network access.</span></span> <span data-ttu-id="4228d-115">새 기능을 사용 하는 방법에 대 한 예제는 `Save-Help` 이 항목의 [파일 공유에서 도움말을 업데이트 하는 방법](#how-to-update-help-from-a-file-share) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4228d-115">For an example of how to use the new `Save-Help` functionality, see [How to update help from a file share](#how-to-update-help-from-a-file-share) in this topic.</span></span>

<span data-ttu-id="4228d-116">업데이트할 수 있는 도움말은 컴퓨터에 도움말 파일이 없는 경우에도 최신 도움말 항목에 대 한 온라인 액세스와 cmdlet에 대 한 기본 도움말도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-116">Updatable Help also supports online access to the newest help topics and basic help for cmdlets, even when there are no help files on the computer.</span></span>

<span data-ttu-id="4228d-117">PowerShell 3.0에는 도움말 파일이 함께 제공 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-117">PowerShell 3.0 does not come with Help files.</span></span> <span data-ttu-id="4228d-118">업데이트할 수 있는 도움말 기능을 사용 하면 기본적으로 PowerShell 및 모든 Windows 모듈에 포함 된 모든 명령에 대 한 도움말 파일을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-118">You can use the Updatable Help feature to install the help files for all of the commands that are included by default in PowerShell and for all Windows modules.</span></span>

## <a name="updatable-help-cmdlets"></a><span data-ttu-id="4228d-119">업데이트할 수 있는 도움말 cmdlet</span><span class="sxs-lookup"><span data-stu-id="4228d-119">Updatable help cmdlets</span></span>

- <span data-ttu-id="4228d-120">`Update-Help`: 인터넷 또는 파일 공유에서 최신 도움말 파일을 다운로드 하 고 로컬 컴퓨터에 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-120">`Update-Help`: Downloads the newest help files from the internet or a file share, and installs them on the local computer.</span></span>

- <span data-ttu-id="4228d-121">`Save-Help`: 인터넷에서 최신 도움말 파일을 다운로드 하 여 파일 시스템 디렉터리 또는 파일 공유에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-121">`Save-Help`: Downloads the newest help files from the internet and saves them in a filesystem directory or file share.</span></span> <span data-ttu-id="4228d-122">컴퓨터에 도움말 파일을 설치 하려면를 사용 `Update-Help` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-122">To install the help files on computers, use `Update-Help`.</span></span>

- <span data-ttu-id="4228d-123">`Get-Help`: 명령줄에 도움말 항목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-123">`Get-Help`: Displays help topics at the command line.</span></span> <span data-ttu-id="4228d-124">컴퓨터의 도움말 파일에서 도움말을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-124">Gets help from the help files on the computer.</span></span> <span data-ttu-id="4228d-125">도움말 파일이 없는 cmdlet 및 함수에 대해 자동 생성 된 도움말을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-125">Displays auto-generated help for cmdlets and functions that do not have help files.</span></span> <span data-ttu-id="4228d-126">기본 인터넷 브라우저에서 cmdlet, 함수, 스크립트 및 워크플로에 대 한 온라인 도움말 항목을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-126">Opens online help topics for cmdlets, functions, scripts, and workflows in your default internet browser.</span></span>

## <a name="auto-generated-help-help-without-help-files"></a><span data-ttu-id="4228d-127">자동 생성 된 도움말: 도움말 파일이 없는 도움말</span><span class="sxs-lookup"><span data-stu-id="4228d-127">Auto-generated help: help without help files</span></span>

<span data-ttu-id="4228d-128">컴퓨터의 cmdlet, 함수 또는 워크플로에 대 한 도움말 파일이 없으면 `Get-Help` cmdlet에서 자동 생성 된 도움말을 표시 하 고 도움말 파일을 다운로드 하거나 온라인으로 읽을 지 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-128">If you do not have the help file for a cmdlet, function, or workflow on the computer, the `Get-Help` cmdlet displays auto-generated help and prompts you to download the help files or read them online.</span></span>

<span data-ttu-id="4228d-129">자동 생성 된 도움말에는 구문과 별칭이 포함 되며, 업데이트할 수 있는 도움말 cmdlet을 사용 하 여 온라인 도움말 항목에 액세스 하는 방법을 설명 하는 설명이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-129">Auto-generated help includes syntax and aliases, and remarks that explain how to use the Updatable Help cmdlets and to access the online help topics.</span></span>

<span data-ttu-id="4228d-130">예를 들어 다음 명령은 cmdlet에 대 한 기본 도움말을 가져옵니다 `Get-Culture` .</span><span class="sxs-lookup"><span data-stu-id="4228d-130">For example, the following command gets basic help for the `Get-Culture` cmdlet.</span></span> <span data-ttu-id="4228d-131">`Get-Help`컴퓨터에 도움말 파일이 없으면 출력에 표시 되는 내용이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-131">The output shows the `Get-Help` display when there are no help files on the computer.</span></span>

```powershell
Get-Help Get-Culture
```

```output
NAME
    Get-Culture

SYNTAX
    Get-Culture [<CommonParameters>]

ALIASES
    None

REMARKS
    To get the latest Help content including descriptions and examples
    type: Update-Help.
```

## <a name="help-files-for-modules"></a><span data-ttu-id="4228d-132">모듈에 대 한 도움말 파일</span><span class="sxs-lookup"><span data-stu-id="4228d-132">Help files for modules</span></span>

<span data-ttu-id="4228d-133">업데이트할 수 있는 도움말의 가장 작은 단위는 모듈에 대 한 도움말입니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-133">The smallest unit of Updatable Help is help for a module.</span></span> <span data-ttu-id="4228d-134">모듈 도움말에는 모듈의 모든 cmdlet, 함수, 워크플로, 공급자, 스크립트 및 개념에 대 한 도움말이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-134">Module help includes help for all of the cmdlets, functions, workflows, providers, scripts, and concepts in a module.</span></span> <span data-ttu-id="4228d-135">현재 세션으로 가져오지 않은 경우에도 컴퓨터에 설치 되어 있는 모든 모듈에 대 한 도움말을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-135">You can update help for all modules that are installed on the computer, even if they are not imported into the current session.</span></span>

<span data-ttu-id="4228d-136">전체 모듈에 대 한 도움말을 업데이트할 수 있지만 개별 cmdlet에 대 한 도움말을 업데이트할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-136">You can update help for the entire module, but you cannot update help for individual cmdlets.</span></span>

<span data-ttu-id="4228d-137">특정 cmdlet이 포함 된 모듈을 찾으려면 다음 명령 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-137">To find the module that contains a particular cmdlet, use the following command format:</span></span>

```powershell
(Get-Command <cmdlet-name>).ModuleName
```

<span data-ttu-id="4228d-138">예를 들어 cmdlet이 포함 된 모듈을 찾으려면 `Set-ExecutionPolicy` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-138">For example, to find the module that contains the `Set-ExecutionPolicy` cmdlet, type:</span></span>

```powershell
(Get-Command Set-ExecutionPolicy).ModuleName
```

<span data-ttu-id="4228d-139">특정 모듈에 대 한 도움말을 업데이트 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-139">To update help for a particular module, type:</span></span>

```powershell
Update-Help -Module <ModuleName>
```

<span data-ttu-id="4228d-140">예를 들어 Set-ExecutionPolicy cmdlet을 포함 하는 모듈에 대 한 도움말을 업데이트 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-140">For example, to update help for the module that contains the Set-ExecutionPolicy cmdlet, type:</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell.Security
```

## <a name="permissions-for-updatable-help"></a><span data-ttu-id="4228d-141">업데이트할 수 있는 도움말에 대 한 사용 권한</span><span class="sxs-lookup"><span data-stu-id="4228d-141">Permissions for updatable help</span></span>

<span data-ttu-id="4228d-142">디렉터리의 모듈에 대 한 도움말을 업데이트 하려면 `$pshome/Modules` 컴퓨터에서 Administrators 그룹의 구성원 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-142">To update help for the modules in the directory `$pshome/Modules`, you must be member of the Administrators group on the computer.</span></span>

<span data-ttu-id="4228d-143">관리자 그룹의 구성원이 아닌 경우 이러한 모듈에 대 한 도움말을 업데이트할 수 없습니다. 그러나 인터넷에 액세스할 수 있는 경우 온라인 도움말을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-143">If you are not a member of the Administrators group, you cannot update help for these modules; but if you have internet access, you can view help online.</span></span>

<span data-ttu-id="4228d-144">디렉터리의 모듈 또는 디렉터리의 다른 하위 디렉터리에 있는 모듈에 대 한 도움말을 업데이트 `$home/Documents/PowerShell/Modules` `$home` 하려면 특별 한 권한이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-144">Updating help for modules in the directory `$home/Documents/PowerShell/Modules` or modules in other subdirectories of the `$home` directory does not require special permissions.</span></span>

<span data-ttu-id="4228d-145">`Update-Help`및 cmdlet에는 `Save-Help` 현재 사용자의 명시적 자격 증명을 제공 하는 **UseDefaultCredentials** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-145">The `Update-Help` and `Save-Help` cmdlets have a **UseDefaultCredentials** parameter that provides the explicit credentials of the current user.</span></span> <span data-ttu-id="4228d-146">이 매개 변수는 보안 인터넷 위치에 액세스 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-146">This parameter is designed for accessing secure internet locations.</span></span>

<span data-ttu-id="4228d-147">`Update-Help`또한 및 `Save-Help` cmdlet에는 원격 컴퓨터에서 명령을 실행 하 고 세 번째 컴퓨터의 파일 공유에 액세스할 수 있는 **자격 증명** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-147">The `Update-Help` and `Save-Help` cmdlets also have a **Credential** parameter that allows you to run the command on a remote computer and access a file share on a third computer.</span></span> <span data-ttu-id="4228d-148">**Credential** 매개 변수는의 SourcePath 또는 **LiteralPath** 매개 변수와 `Update-Help` 의 **DestinationPath** 또는 **LiteralPath** 매개 변수를 사용 하는 경우에만 유효 합니다 `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="4228d-148">The **Credential** parameter is valid only when you use the SourcePath or **LiteralPath** parameters of `Update-Help` and the **DestinationPath** or **LiteralPath** parameters of `Save-Help`.</span></span>

## <a name="how-to-install-and-update-help-files"></a><span data-ttu-id="4228d-149">도움말 파일을 설치 하 고 업데이트 하는 방법</span><span class="sxs-lookup"><span data-stu-id="4228d-149">How to install and update help files</span></span>

<span data-ttu-id="4228d-150">처음으로 도움말 파일을 다운로드 하 여 설치 하거나 컴퓨터에서 도움말 파일을 업데이트 하려면 cmdlet을 사용 합니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="4228d-150">To download and install help files for the first time, or to update the help files on your computer, use the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="4228d-151">`Update-Help`Cmdlet은 다음 작업을 포함 하 여 모든 하드 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-151">The `Update-Help` cmdlet does all of the hard work for you, including the following tasks.</span></span>

- <span data-ttu-id="4228d-152">업데이트할 수 있는 도움말을 지 원하는 모듈을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-152">Determines which modules support Updatable Help.</span></span>
- <span data-ttu-id="4228d-153">각 모듈이 업데이트할 수 있는 도움말 파일을 저장 하는 인터넷 위치를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-153">Finds the internet location where each module stores its Updatable Help files.</span></span>
- <span data-ttu-id="4228d-154">컴퓨터의 각 모듈에 대 한 도움말 파일을 각 모듈에서 사용할 수 있는 최신 도움말 파일과 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-154">Compares the help files for each module on your computer to the newest help files that are available for each module.</span></span>
- <span data-ttu-id="4228d-155">인터넷에서 새 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-155">Downloads the new files from the internet.</span></span>
- <span data-ttu-id="4228d-156">도움말 파일 패키지를의 래핑을 해제.</span><span class="sxs-lookup"><span data-stu-id="4228d-156">Unwraps the help file package.</span></span>
- <span data-ttu-id="4228d-157">파일이 유효한 도움말 파일 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-157">Verifies that the files are valid help files.</span></span>
- <span data-ttu-id="4228d-158">모듈 디렉터리의 언어별 하위 디렉터리에 도움말 파일을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-158">Installs the help files in the language-specific subdirectory of the module directory.</span></span>

<span data-ttu-id="4228d-159">새 도움말 항목에 액세스 하려면 cmdlet을 사용 합니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="4228d-159">To access the new help topics, use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="4228d-160">PowerShell을 다시 시작할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-160">You do not need to restart PowerShell.</span></span>

<span data-ttu-id="4228d-161">업데이트할 수 있는 도움말을 지 원하는 컴퓨터의 모든 모듈에 대 한 도움말을 설치 하거나 업데이트 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-161">To install or update help for all modules on the computer that supports Updatable Help, type:</span></span>

```powershell
Update-Help
```

<span data-ttu-id="4228d-162">특정 모듈에 대 한 도움말을 업데이트 하려면의 **모듈** 매개 변수를 추가 `Update-Help` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-162">To update help for particular modules, add the **Module** parameter of `Update-Help`.</span></span> <span data-ttu-id="4228d-163">모듈 이름에 와일드 카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-163">Wildcard characters are permitted in the module name.</span></span>

<span data-ttu-id="4228d-164">예를 들어 ServerManager 모듈에 대 한 도움말을 업데이트 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-164">For example, to update help for the ServerManager module, type:</span></span>

```powershell
Update-Help -Module ServerManager
```

<span data-ttu-id="4228d-165">매개 변수가 없으면 `Update-Help` 세션의 모든 모듈 및 업데이트할 수 있는 도움말을 지 원하는 모든 설치 된 모듈에 대 한 도움말을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-165">Without parameters, `Update-Help` updates help for all modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="4228d-166">포함 하려면 모듈을 PSModulePath 환경 변수 값에 나열 된 디렉터리에 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-166">To be included, modules must be installed in directories that are listed in the value of the PSModulePath environment variable.</span></span> <span data-ttu-id="4228d-167">"Get-help-ListAvailable" 명령에 의해 반환 되는 모듈 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-167">These are also modules that are returned by a "Get-Help -ListAvailable" command.</span></span>

<span data-ttu-id="4228d-168">**Module** 매개 변수 값이 `*` (all) 이면에서 `Update-Help` 업데이트할 수 있는 도움말을 지원 하지 않는 모듈을 비롯 하 여 설치 된 모든 모듈에 대 한 도움말을 업데이트 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-168">If the value of the **Module** parameter is `*` (all), `Update-Help` attempts to update help for all installed modules, including modules that do not support Updatable Help.</span></span> <span data-ttu-id="4228d-169">이 명령은 일반적으로 cmdlet이 업데이트할 수 있는 도움말을 지원 하지 않는 모듈을 발견할 때 많은 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-169">This command typically generates many errors as the cmdlet encounters modules that do not support Updatable Help.</span></span>

## <a name="how-to-update-help-from-a-file-share"></a><span data-ttu-id="4228d-170">파일 공유에서 도움말을 업데이트 하는 방법</span><span class="sxs-lookup"><span data-stu-id="4228d-170">How to update help from a file share</span></span>

<span data-ttu-id="4228d-171">인터넷에 연결 되지 않은 컴퓨터를 지원 하거나 엔터프라이즈에서 도움말 업데이트를 제어 하거나 간소화 하려면 cmdlet을 사용 `Save-Help` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-171">To support computers that are not connected to the internet, or to control or streamline help updating in an enterprise, use the `Save-Help` cmdlet.</span></span> <span data-ttu-id="4228d-172">이 `Save-Help` cmdlet은 인터넷에서 도움말 파일을 다운로드 하 여 지정한 파일 시스템 디렉터리에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-172">The `Save-Help` cmdlet downloads help files from the internet and saves them in a filesystem directory that you specify.</span></span>

<span data-ttu-id="4228d-173">`Save-Help` 지정 된 디렉터리에 있는 도움말 파일을 각 모듈에서 사용할 수 있는 최신 도움말 파일과 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-173">`Save-Help` compares the help files in the specified directory to the newest help files that are available for each module.</span></span> <span data-ttu-id="4228d-174">모듈에 대 한 도움말 파일이 나 최신 도움말 파일을 디렉터리에 사용할 수 없는 경우이 `Save-Help` cmdlet은 인터넷에서 새 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-174">If the directory has no help files or newer help files are available for the module, the `Save-Help` cmdlet downloads the new files from the internet.</span></span> <span data-ttu-id="4228d-175">그러나 도움말 파일은 래핑을 해제 하거나 설치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-175">However, it does not unwrap or install the help files.</span></span>

<span data-ttu-id="4228d-176">파일 시스템 디렉터리에 저장 된 도움말 파일에서 컴퓨터의 도움말 파일을 설치 하거나 업데이트 하려면 cmdlet의 **SourcePath** 매개 변수를 사용 합니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="4228d-176">To install or update the help files on a computer from help files that were saved to a filesystem directory, use the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span> <span data-ttu-id="4228d-177">`Update-Help`Cmdlet은 최신 도움말 파일을 식별 하 고의 래핑을 해제 및 유효성을 검사 한 다음 모듈 디렉터리의 언어별 하위 디렉터리에 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-177">The `Update-Help` cmdlet identifies the newest help files, unwraps and validates them, and installs them in the language-specific subdirectories of the module directories.</span></span>

<span data-ttu-id="4228d-178">예를 들어 디렉터리에 설치 된 모든 모듈에 대 한 도움말을 저장 하려면 `\\Server\Share` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-178">For example, to save help for all installed modules to the `\\Server\Share` directory, type:</span></span>

```powershell
Save-Help -DestinationPath \\Server\Share
```

<span data-ttu-id="4228d-179">그런 다음 디렉터리에서 도움말을 업데이트 하려면 `\\Server\Share` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-179">Then, to update help from the `\\Server\Share` directory, type:</span></span>

```powershell
Update-Help -SourcePath \\Server\Share
```

<span data-ttu-id="4228d-180">다음 예에서는를 사용 하 여 `Save-Help` 로컬 컴퓨터에 설치 되지 않은 모듈에 대 한 도움말을 저장 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-180">The following examples show the use of `Save-Help` to save help for modules that are not installed on the local computer.</span></span> <span data-ttu-id="4228d-181">이 예에서는 관리자가를 실행 `Save-Help` 하 여 로컬 컴퓨터에 DhcpServer 모듈 또는 DHCP 서버 역할을 설치 하지 않고 인터넷에 연결 된 클라이언트 컴퓨터에서 DhcpServer 모듈에 대 한 도움말을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-181">In this example, the administrator runs `Save-Help` to save the help for the DhcpServer module from an internet-connected client computer, without installing the DhcpServer module or DHCP Server role on the local computer.</span></span>

<span data-ttu-id="4228d-182">옵션 1:을 실행 `Invoke-Command` 하 여 원격 모듈의 **psmoduleinfo** 개체를 가져온 다음 변수에 저장 하 `$m` 고 변수를 `Save-Help` 모듈 이름으로 지정 하 여 **psmoduleinfo** 개체에서 실행 합니다 `$m` .</span><span class="sxs-lookup"><span data-stu-id="4228d-182">Option 1: Run `Invoke-Command` to get the **PSModuleInfo** object for the remote module, save it in a variable, `$m`, and then run `Save-Help` on the **PSModuleInfo** object by specifying the variable `$m` as the module name.</span></span>

```powershell
$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock
{ Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="4228d-183">옵션 2: DHCP 서버 모듈을 실행 하는 컴퓨터에서 대상으로 하는 PSSession을 열고, 모듈에 대 한 **Psmoduleinfo** 개체를 가져오고, 변수에 저장 한 `$m` 후 `Save-Help` 변수에 저장 된 개체에서를 실행 합니다 `$m` .</span><span class="sxs-lookup"><span data-stu-id="4228d-183">Option 2: Open a PSSession targeted at the computer that is running the DHCP Server module, to get the **PSModuleInfo** object for the module, save it in a variable `$m`, and then run `Save-Help` on the object that is saved in the `$m` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName RemoteServer
$m = Get-Module -PSSession $s -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="4228d-184">옵션 3: DHCP 서버 모듈을 실행 하는 컴퓨터에서 대상으로 하는 CIM 세션을 열고 모듈의 **Psmoduleinfo** 개체를 가져온 다음 변수에 저장 된 `$m` `Save-Help` 개체에서 실행 합니다 `$m` .</span><span class="sxs-lookup"><span data-stu-id="4228d-184">Option 3: Open a CIM session, targeted at the computer that is running the DHCP Server module, to get the **PSModuleInfo** object for the module, save it in a variable `$m`, and then run `Save-Help` on the object that is saved in the `$m` variable.</span></span>

```powershell
$c = New-CimSession -ComputerName RemoteServer
$m = Get-Module -CimSession $c -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="4228d-185">다음 예에서는 관리자가 네트워크에 액세스할 수 없는 컴퓨터에 DHCP 서버 모듈에 대 한 도움말을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-185">In the following example, the administrator installs help for the DHCP Server module on a computer that does not have network access.</span></span>

<span data-ttu-id="4228d-186">먼저를 실행 `Export-Clixml` 하 여 **Psmoduleinfo** 개체를 공유 폴더 또는 이동식 미디어로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-186">First, run `Export-Clixml` to export the **PSModuleInfo** object to a shared folder or to removable media.</span></span>

```powershell
$m = Get-Module -Name DhcpServer -ListAvailable
Export-Clixml -Path E:\UsbFlashDrive\DhcpModule.xml -InputObject $m
```

<span data-ttu-id="4228d-187">다음으로, 인터넷에 액세스할 수 있는 컴퓨터에 이동식 미디어를 전송 하 고를 사용 하 여 **Psmoduleinfo** 개체를 가져옵니다 `Import-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="4228d-187">Next, transport the removable media to a computer that has internet access, and then import the **PSModuleInfo** object with `Import-Clixml`.</span></span> <span data-ttu-id="4228d-188">`Save-Help`을 실행 하 여 가져온 DhcpServer 모듈 **Psmoduleinfo** 개체에 대 한 도움말을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-188">Run `Save-Help` to save the Help for the imported DhcpServer module **PSModuleInfo** object.</span></span>

```powershell
$deserialized_m = Import-Clixml E:\UsbFlashDrive\DhcpModule.xml
Save-Help -Module $deserialized_m -DestinationPath E:\UsbFlashDrive\SavedHelp
```

<span data-ttu-id="4228d-189">마지막으로, 네트워크에 액세스할 수 없는 컴퓨터에 이동식 미디어를 다시 전송 하 고를 실행 하 여 도움말을 설치 `Update-Help` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-189">Finally, transport the removable media back to the computer that does not have network access, and then install the help by running `Update-Help`.</span></span>

```powershell
Update-Help -Module DhcpServer -SourcePath E:\UsbFlashDrive\SavedHelp
```

<span data-ttu-id="4228d-190">매개 변수가 없으면 `Save-Help` 세션의 모든 모듈 및 업데이트할 수 있는 도움말을 지 원하는 모든 설치 된 모듈에 대 한 도움말을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-190">Without parameters, `Save-Help` downloads help for all modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="4228d-191">포함 하려면 모듈을 `$env:PSModulePath` 로컬 컴퓨터 또는 도움말을 저장할 원격 컴퓨터의 환경 변수 값에 나열 된 디렉터리에 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-191">To be included, modules must be installed in directories that are listed in the value of the `$env:PSModulePath` environment variable, on either the local computer or on a remote computer for which you want to save help.</span></span> <span data-ttu-id="4228d-192">이는 명령을 실행 하 여 반환 되는 모듈 이기도 `Get-Help -ListAvailable` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-192">These are also modules that are returned by running a `Get-Help -ListAvailable` command.</span></span>

## <a name="how-to-update-help-files-in-different-languages"></a><span data-ttu-id="4228d-193">다른 언어로 도움말 파일을 업데이트 하는 방법</span><span class="sxs-lookup"><span data-stu-id="4228d-193">How to update help files in different languages</span></span>

<span data-ttu-id="4228d-194">기본적으로 `Update-Help` 및 cmdlet은 `Save-Help` 로컬 컴퓨터의 Windows에 대해 설정 된 UI 문화권 및 언어에 대 한 도움말을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-194">By default, the `Update-Help` and `Save-Help` cmdlets download help in the UI culture and language that is set for Windows on the local computer.</span></span> <span data-ttu-id="4228d-195">지정 된 모듈에 대 한 도움말 파일을 로컬 UI 문화권에서 사용할 수 없는 `Update-Help` 경우 `Save-Help` Windows 언어 대체 규칙을 사용 하 여 지원 되는 최상의 언어를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-195">If help files for the specified modules are not available in the local UI culture, `Update-Help` and `Save-Help` use the Windows language fallback rules to find the best supported language.</span></span>

<span data-ttu-id="4228d-196">그러나 및 cmdlet의 **UICulture** 매개 변수를 사용 `Update-Help` 하 여 `Save-Help` 사용 가능한 모든 UI 문화권에서 도움말 파일을 다운로드 하 고 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-196">However, you can use the **UICulture** parameters of the `Update-Help` and `Save-Help` cmdlets to download and install help files in any UI cultures in which they are available.</span></span>

<span data-ttu-id="4228d-197">예를 들어 세션의 모든 모듈에 대 한 최신 도움말 파일을 일본어 (Ja-jp)와 프랑스어 (fr-fr)로 저장 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-197">For example, to save the newest help files for all modules on the session in Japanese (Ja-jp) and French (fr-FR), type:</span></span>

```powershell
Save-Help -Path \Server\Share -UICulture ja-jp, fr-fr
```

<span data-ttu-id="4228d-198">모듈에 대 한 도움말 파일을 지정한 언어로 사용할 수 없는 경우 `Update-Help` 및 `Save-Help` cmdlet은 각 모듈의 도움말이 제공 되는 언어를 나열 하는 오류 메시지를 반환 하므로 사용자 요구에 가장 적합 한 대체 항목을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-198">If help files for the modules are not available in the languages that you specified, the `Update-Help` and `Save-Help` cmdlets return an error message that lists the languages in which help for each module is available so you can choose the alternative that best meets your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="4228d-199">현재, 업데이트 가능한 도움말 콘텐츠는 영어 (en-us)로만 게시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-199">Currently, Updateable Help content is only published in English (en-US).</span></span> <span data-ttu-id="4228d-200">일부 비 Windows 시스템에서는 **UICulture** 매개 변수를 사용 하 여 콘텐츠를 명시적으로 요청 해야 합니다 `en-US` .</span><span class="sxs-lookup"><span data-stu-id="4228d-200">On some non-Windows systems you must use the **UICulture** parameter to explicitly request the `en-US` content.</span></span>

## <a name="how-to-use-online-help"></a><span data-ttu-id="4228d-201">온라인 도움말을 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="4228d-201">How to use online help</span></span>

<span data-ttu-id="4228d-202">로컬 컴퓨터에서 도움말 파일을 업데이트 하지 않거나 업데이트할 수 없는 경우에도 최신 도움말 파일을 온라인으로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-202">If you cannot or choose not to update the help files on your local computer, you can still get the newest help files online.</span></span>

<span data-ttu-id="4228d-203">Cmdlet 또는 함수에 대 한 온라인 도움말 항목을 열려면 cmdlet의 **online** 매개 변수를 사용 합니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="4228d-203">To open the online help topic for any cmdlet or function, use the **Online** parameter of the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="4228d-204">예를 들어 다음 명령은 `Get-Job` 기본 인터넷 브라우저에서 cmdlet에 대 한 온라인 도움말 항목을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-204">For example, the following command opens the online help topic for the `Get-Job` cmdlet in your default internet browser:</span></span>

```powershell
Get-Help Get-Job -Online
```

<span data-ttu-id="4228d-205">스크립트에 대 한 온라인 도움말을 보려면 **온라인** 매개 변수와 스크립트의 전체 경로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-205">To get online help for a script, use the **Online** parameter and the full path to the script.</span></span>

<span data-ttu-id="4228d-206">**Online** 매개 변수는 About 토픽에서 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-206">The **Online** parameter does not work with About topics.</span></span> <span data-ttu-id="4228d-207">Powershell 언어에 대 한 도움말 항목을 포함 하 여 PowerShell에 대 한 정보 항목을 보려면 [Powershell 정보 항목](about.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4228d-207">To see the about topics for PowerShell, including help topics about the PowerShell language, see [PowerShell About Topics](about.md).</span></span>

## <a name="how-to-minimize-or-prevent-internet-downloads"></a><span data-ttu-id="4228d-208">인터넷 다운로드를 최소화 하거나 차단 하는 방법</span><span class="sxs-lookup"><span data-stu-id="4228d-208">How to minimize or prevent internet downloads</span></span>

<span data-ttu-id="4228d-209">인터넷에 연결 되지 않은 사용자에 게 업데이트할 수 있는 도움말을 제공 하 고 인터넷 다운로드를 최소화 하려면 cmdlet을 사용 합니다 `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="4228d-209">To minimize internet downloads and provide Updatable Help to users who are not connected to the internet, use the `Save-Help` cmdlet.</span></span> <span data-ttu-id="4228d-210">인터넷에서 도움말을 다운로드 하 여 네트워크 공유에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-210">Download help from the internet and save it to a network share.</span></span> <span data-ttu-id="4228d-211">그런 다음 `Update-Help` 모든 컴퓨터에서 명령을 실행 하는 그룹 정책 설정 또는 예약 된 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-211">Then, create a Group Policy setting or scheduled job that runs an `Update-Help` command on all computers.</span></span> <span data-ttu-id="4228d-212">Cmdlet의 **SourcePath** 매개 변수 값을 `Update-Help` 네트워크 공유로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-212">Set the value of the **SourcePath** parameter of the `Update-Help` cmdlet to the network share.</span></span>

<span data-ttu-id="4228d-213">인터넷에 액세스할 수 있는 사용자가 인터넷에서 업데이트할 수 있는 도움말을 다운로드 하지 못하게 하려면 **update-help에 대 한 기본 원본 경로 설정** 그룹 정책 설정을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-213">To prevent users who have internet access from downloading Updatable Help from the internet, use the **Set the default source path for Update-Help** Group Policy setting.</span></span>

<span data-ttu-id="4228d-214">이 그룹 정책 설정은 지정 하는 파일 시스템 위치를 사용 하 여 모든 영향을 받는 컴퓨터의 모든 명령에 **SourcePath** 매개 변수를 암시적으로 추가 합니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="4228d-214">This Group Policy setting implicitly adds the **SourcePath** parameter, with the filesystem location that you specify, to every `Update-Help` command on every affected computer.</span></span> <span data-ttu-id="4228d-215">사용자는 **sourcepath** 매개 변수를 명시적으로 사용 하 여 다른 파일 시스템 위치를 지정할 수 있지만 **sourcepath** 매개 변수를 제외 하 고 인터넷에서 도움말을 다운로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-215">Users can use the **SourcePath** parameter explicitly to specify a different filesystem location, but they cannot exclude the **SourcePath** parameter and download help from the internet.</span></span>

> [!NOTE]
> <span data-ttu-id="4228d-216">**컴퓨터 구성** 및 **사용자 구성** 아래에는 **update-help에 대 한 기본 원본 경로 설정** 그룹이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-216">The **Set the default source path for Update-Help** group policy setting appears under **Computer Configuration** and **User Configuration**.</span></span> <span data-ttu-id="4228d-217">그러나 **컴퓨터 구성** 에서 정책 설정만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-217">However, only the policy setting under **Computer Configuration** is effective.</span></span> <span data-ttu-id="4228d-218">**사용자 구성** 에서 정책 설정은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-218">The policy setting under **User Configuration** is ignored.</span></span>

<span data-ttu-id="4228d-219">자세한 내용은 [about_Group_Policy_Settings](about_Group_Policy_Settings.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4228d-219">For more information, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

## <a name="how-to-update-help-for-non-standard-modules"></a><span data-ttu-id="4228d-220">비표준 모듈에 대 한 도움말을 업데이트 하는 방법</span><span class="sxs-lookup"><span data-stu-id="4228d-220">How to update help for non-standard modules</span></span>

<span data-ttu-id="4228d-221">Cmdlet의 **ListAvailable** 매개 변수에서 반환 되지 않은 모듈에 대 한 도움말을 업데이트 하거나 저장 하려면 `Get-Module` 또는 명령을 실행 하기 전에 모듈을 현재 세션으로 가져옵니다 `Update-Help` `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="4228d-221">To update or save help for a module that is not returned by the **ListAvailable** parameter of the `Get-Module` cmdlet, import the module into the current session before running an `Update-Help` or `Save-Help` command.</span></span> <span data-ttu-id="4228d-222">원격 컴퓨터에서 명령을 실행 하기 전에 `Save-Help` 원격 컴퓨터에 연결 된 현재 세션 또는 스크립트 블록으로 모듈을 가져옵니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="4228d-222">On a remote computer, before running the `Save-Help` command, import the module into the current Session, or `Invoke-Command` script block, that is connected to the remote computer.</span></span>

<span data-ttu-id="4228d-223">모듈이 현재 세션에 있는 경우 `Update-Help` `Save-Help` 매개 변수 없이 또는 cmdlet을 실행 하거나 module 매개 변수를 사용  하 여 모듈 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-223">When the module is in the current session, run the `Update-Help` or `Save-Help` cmdlets without parameters, or use the **Module** parameter to specify the module name.</span></span>

<span data-ttu-id="4228d-224">및 cmdlet의 **모듈** 매개 변수에는 `Update-Help` `Save-Help` 모듈 이름만 사용할 수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-224">The **Module** parameters of the `Update-Help` and `Save-Help` cmdlets accept only a module name.</span></span> <span data-ttu-id="4228d-225">모듈 파일에 대 한 경로를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-225">They do not accept the path to a module file.</span></span>

<span data-ttu-id="4228d-226">이 방법을 사용 하 여 cmdlet의 **ListAvailable** 매개 변수 `Get-Module` (예: 환경 변수에 나열 되지 않은 위치에 설치 된 모듈 또는 제대로 구성 되지 않은 모듈)에 대 한 도움말을 업데이트 하거나 저장할 수 `$env:PSModulePath` 있습니다. 모듈 디렉터리에 basename가 디렉터리 이름과 동일한 파일이 하나 이상 포함 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-226">Use this technique to update or save help for any module that is not returned by the **ListAvailable** parameter of the `Get-Module` cmdlet, such as a module that is installed in a location that is not listed in the `$env:PSModulePath` environment variable, or a module that is not well-formed (the module directory does not contain at least one file whose basename is the same as the directory name).</span></span>

## <a name="how-to-support-updatable-help"></a><span data-ttu-id="4228d-227">업데이트할 수 있는 도움말을 지 원하는 방법</span><span class="sxs-lookup"><span data-stu-id="4228d-227">How to support updatable help</span></span>

<span data-ttu-id="4228d-228">모듈을 작성 하는 경우 모듈에 대 한 온라인 도움말 및 업데이트할 수 있는 도움말을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-228">If you author a module, you can support online help and Updatable Help for your modules.</span></span> <span data-ttu-id="4228d-229">자세한 내용은 Microsoft Docs에서 업데이트할 수 있는 [도움말 지원](/powershell/scripting/developer/help/supporting-updatable-help) 및 [온라인 도움말 지원](/powershell/scripting/developer/module/supporting-online-help) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4228d-229">For more information, see [Supporting Updatable Help](/powershell/scripting/developer/help/supporting-updatable-help) and [Supporting Online Help](/powershell/scripting/developer/module/supporting-online-help) in the Microsoft Docs.</span></span>

<span data-ttu-id="4228d-230">PowerShell 스냅인 또는 주석 기반 도움말에서 업데이트할 수 있는 도움말을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-230">Updatable help not available for PowerShell snap-ins or comment-based help.</span></span>

## <a name="remarks"></a><span data-ttu-id="4228d-231">설명</span><span class="sxs-lookup"><span data-stu-id="4228d-231">Remarks</span></span>

<span data-ttu-id="4228d-232">`Update-Help`및 `Save-Help` cmdlet은 Windows 사전 설치 환경 (Windows PE)에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4228d-232">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <a name="see-also"></a><span data-ttu-id="4228d-233">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4228d-233">See also</span></span>

[<span data-ttu-id="4228d-234">Get-Help</span><span class="sxs-lookup"><span data-stu-id="4228d-234">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)

[<span data-ttu-id="4228d-235">Save-Help</span><span class="sxs-lookup"><span data-stu-id="4228d-235">Save-Help</span></span>](xref:Microsoft.PowerShell.Core.Save-Help)

[<span data-ttu-id="4228d-236">Update-Help</span><span class="sxs-lookup"><span data-stu-id="4228d-236">Update-Help</span></span>](xref:Microsoft.PowerShell.Core.Update-Help)
