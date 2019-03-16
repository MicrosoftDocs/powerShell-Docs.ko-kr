---
title: PowerShell 모듈 설치 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 7c2bfca50de4645676eafc01bbf23d9797e8b758
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059782"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="6a649-102">PowerShell 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="6a649-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="6a649-103">PowerShell 모듈을 만든 후 가능성이 해야 시스템에서 모듈을 설치 하 든 다른 사람이 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="6a649-104">일반적으로이 단순히 이루어져 있습니다 모듈 파일 (ie,은. psm1, 또는 이진 어셈블리, 모듈 매니페스트 및 관련 된 기타 파일이) 디렉터리에 해당 컴퓨터에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-104">Generally speaking, this simply consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="6a649-105">매우 작은 프로젝트의 경우이 수 만큼 간단할 복사 및 붙여넣기를 단일 원격 컴퓨터에 Windows 탐색기를 사용 하 여 파일 그러나 더 큰 솔루션 보다 복잡 한 설치 프로세스를 사용 하는 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="6a649-106">시스템 모듈을 얻는 방법에 관계 없이 PowerShell에는 다양 한 기술 찾아 모듈을 사용 하 여 사용자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="6a649-107">(자세한 내용은 [PowerShell 모듈을 가져오는](./importing-a-powershell-module.md).) 따라서 설치에 대 한 주요 문제는 PowerShell 모듈을 찾을 수 있는지을 보장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-107">(For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).) Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span>

<span data-ttu-id="6a649-108">이 항목에는 다음 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-108">This topic contains the following sections:</span></span>

- <span data-ttu-id="6a649-109">모듈을 설치 하는 것에 대 한 규칙</span><span class="sxs-lookup"><span data-stu-id="6a649-109">Rules for Installing Modules</span></span>

- <span data-ttu-id="6a649-110">모듈을 설치 하는 위치</span><span class="sxs-lookup"><span data-stu-id="6a649-110">Where to Install Modules</span></span>

- <span data-ttu-id="6a649-111">모듈의 여러 버전 설치</span><span class="sxs-lookup"><span data-stu-id="6a649-111">Installing Multiple Versions of a Module</span></span>

- <span data-ttu-id="6a649-112">처리 명령 이름 충돌</span><span class="sxs-lookup"><span data-stu-id="6a649-112">Handling Command Name Conflicts</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="6a649-113">모듈을 설치 하는 것에 대 한 규칙</span><span class="sxs-lookup"><span data-stu-id="6a649-113">Rules for Installing Modules</span></span>

<span data-ttu-id="6a649-114">다음 정보를 직접 사용 하 여, 다른 곳에서 얻을 수 있는 모듈 및 다른 사용자에 게 배포 하는 모듈에 대해 만든 모듈을 포함 하 여 모든 모듈에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-114">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="6a649-115">PSModulePath에서 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-115">Install Modules in PSModulePath</span></span>

<span data-ttu-id="6a649-116">가능 하면에 나열 된 경로에서 모든 모듈을 설치를 **PSModulePath** 환경 변수 또는 모듈 경로를 추가 합니다 **PSModulePath** 환경 변수 값.</span><span class="sxs-lookup"><span data-stu-id="6a649-116">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="6a649-117">합니다 **PSModulePath** 환경 변수 ($Env: PSModulePath) Windows PowerShell 모듈의 위치를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-117">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="6a649-118">Cmdlet 모듈을 찾으려면이 환경 변수의 값에 의존 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-118">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="6a649-119">기본적으로 **PSModulePath** 사용자 모듈 디렉터리를 확인 하 고 다음과 같은 시스템 환경 변수 값에 포함 되어 있지만에 추가 하 고 값을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-119">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="6a649-120">$ PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="6a649-120">$PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="6a649-121">이 위치는 Windows와 함께 제공 되는 모듈에 대해 예약 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-121">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="6a649-122">이 위치에 모듈을 설치 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="6a649-122">Do not install modules to this location.</span></span>

- <span data-ttu-id="6a649-123">$ Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="6a649-123">$Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="6a649-124">$Env: ProgramFiles\WindowsPowerShell\Modules (%ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="6a649-124">$Env:ProgramFiles\WindowsPowerShell\Modules (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="6a649-125">값을 검색할 합니다 **PSModulePath** 환경 변수를 다음 명령 중 하나를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-125">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="6a649-126">값에는 모듈 경로를 추가 합니다 **PSModulePath** 환경 변수 값, 다음 명령 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-126">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="6a649-127">이 형식은 사용 하 여는 **SetEnvironmentVariable** 메서드는 **System.Environment** 클래스를 세션에 관계 없이 변경 하는 **PSModulePath** 환경 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-127">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="6a649-128">에 대 한 경로 추가한 후 **PSModulePath**를 변경 하는 방법에 대 한 환경 메시지를 브로드캐스트 해야 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-128">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="6a649-129">변경 브로드캐스트를 셸과 같은 다른 응용 프로그램의 변경 내용을 반영 하도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-129">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="6a649-130">변경 브로드캐스트를 보낼 제품 설치 코드를 **WM_SETTINGCHANGE** 메시지 `lParam` 문자열 "환경"로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-130">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="6a649-131">모듈 설치 코드 업데이트 후에 메시지를 송신 해야 **PSModulePath**합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-131">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="6a649-132">올바른 모듈 디렉터리 이름을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="6a649-132">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="6a649-133">"올바른된" 모듈은 모듈을 모듈 디렉터리에 하나 이상의 파일의 기본 이름으로 동일한 이름을 가진 디렉터리에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-133">A "well-formed" module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="6a649-134">모듈을 제대로 구성 하지 않으면 Windows PowerShell 인식 하지 못합니다 해당 모듈로.</span><span class="sxs-lookup"><span data-stu-id="6a649-134">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="6a649-135">"기본" 파일의 이름은 파일 이름 확장명이 없는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-135">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="6a649-136">올바른 형식의 모듈을 모듈 파일이 포함 된 디렉터리의 이름을 모듈에서 하나 이상의 파일의 기본 이름과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-136">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="6a649-137">예를 들어 샘플 Fabrikam 모듈에서 모듈 파일이 포함 된 디렉터리에 "Fabrikam" 라고 합니다. 및 하나 이상의 파일에 "Fabrikam" 기본 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-137">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="6a649-138">이 경우 모두 Fabrikam.psd1 Fabrikam.dll 있고 "Fabrikam" 기본 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-138">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="6a649-139">잘못 된 설치의 효과</span><span class="sxs-lookup"><span data-stu-id="6a649-139">Effect of Incorrect Installation</span></span>

<span data-ttu-id="6a649-140">모듈 형식이 잘못 되었습니다. 해당 위치 값에 포함 되지 않은 경우는 **PSModulePath** 환경 변수를 다음과 같은 Windows PowerShell의 기본 검색 기능이 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-140">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="6a649-141">모듈 자동 로드 기능 모듈을 자동으로 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-141">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="6a649-142">합니다 `ListAvailable` 의 매개 변수를 [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 모듈을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-142">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="6a649-143">합니다 [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 모듈을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-143">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="6a649-144">모듈을 가져오려면 루트 모듈 파일 또는 모듈 매니페스트 파일의 전체 경로 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-144">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="6a649-145">모듈을 세션으로 가져오지 않는 한 다음과 같은 추가 기능을 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-145">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="6a649-146">올바른 형식의 모듈에 **PSModulePath** 모듈은 세션으로 가져오지 않습니다 하는 경우에 환경 변수를 이러한 기능이 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-146">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="6a649-147">합니다 [Get-command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet 모듈의 명령을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-147">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="6a649-148">합니다 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 하 고 [Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet 업데이트 하거나 모듈에 대 한 도움말을 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-148">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="6a649-149">합니다 [Show-command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet 모듈의 명령을 표시을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-149">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="6a649-150">모듈의 명령에서 누락 된는 `Show-Command` 창에서 Windows PowerShell 통합 스크립팅 환경 (ISE).</span><span class="sxs-lookup"><span data-stu-id="6a649-150">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="6a649-151">모듈을 설치 하는 위치</span><span class="sxs-lookup"><span data-stu-id="6a649-151">Where to Install Modules</span></span>

<span data-ttu-id="6a649-152">이 섹션에서는 Windows PowerShell 모듈을 설치 하려면 파일 시스템에 위치를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-152">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="6a649-153">위치는 모듈을 사용 하는 방법에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-153">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="6a649-154">특정 사용자에 대 한 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-154">Installing Modules for a Specific User</span></span>

<span data-ttu-id="6a649-155">사용자 고유의 모듈을 만들거나 Windows PowerShell 커뮤니티 웹 사이트와 같은 다른 파티에서 모듈을 가져올 하려는 경우 사용자 계정의 사용 가능 하도록 모듈을 사용자 고유의 모듈 디렉터리에 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-155">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

<span data-ttu-id="6a649-156">사용자 고유의 모듈 디렉터리의 값에 추가 됩니다는 **PSModulePath** 기본적으로 환경 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-156">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="6a649-157">Program Files의 모든 사용자에 대 한 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-157">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="6a649-158">컴퓨터의 모든 사용자 계정에 사용 가능 하도록 모듈을 사용 하도록 하려는 경우 Program Files 위치에 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-158">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> <span data-ttu-id="6a649-159">프로그램 파일 위치를 Windows PowerShell 4.0 이상에서 기본적으로 PSModulePath 환경 변수의 값에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-159">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="6a649-160">Windows PowerShell의 버전을 수동으로 만들고 Program Files 위치 ((%ProgramFiles%\WindowsPowerShell\Modules) 하 위에서 설명한 대로이 경로를 PSModulePath 환경 변수에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-160">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="6a649-161">제품 디렉터리에 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-161">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="6a649-162">타사 모듈을 배포 하는 경우 위에서 설명한 기본 프로그램 파일 위치를 사용 하거나 % ProgramFiles % 디렉터리의 고유한 회사 또는 제품 관련 하위 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-162">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="6a649-163">예를 들어, Fabrikam 기술을 회사인 Fabrikam Manager 제품에 대 한 Windows PowerShell 모듈으로 배송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-163">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="6a649-164">모듈 설치 관리자가 Fabrikam Manager 제품 하위 디렉터리에 모듈 하위 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-164">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="6a649-165">Fabrikam 모듈을 찾으려면 Windows PowerShell 모듈 검색 기능을 사용 하려면 Fabrikam 모듈 설치 관리자의 값에 모듈 위치를 추가 합니다 **PSModulePath** 환경 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-165">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="6a649-166">공통 파일 디렉터리에 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-166">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="6a649-167">모듈 여러 버전의 제품 또는 제품의 여러 구성 요소를 사용 하면 %ProgramFiles%\Common Files\Modules 하위 디렉터리의 모듈의 특정 하위 디렉터리에 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-167">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="6a649-168">다음 예제에서는 Fabrikam 모듈 %ProgramFiles%\Common Files\Modules 하위 디렉터리의 Fabrikam 하위 디렉터리에 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-168">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span> <span data-ttu-id="6a649-169">각 모듈 모듈 하위 디렉터리에는 자체 하위 디렉터리에 상주 하는 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-169">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

<span data-ttu-id="6a649-170">설치 관리자의 값을 보장 하는 다음의 **PSModulePath** 환경 변수는 일반적인 파일 모듈 하위 디렉터리의 경로 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-170">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="6a649-171">모듈의 여러 버전 설치</span><span class="sxs-lookup"><span data-stu-id="6a649-171">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="6a649-172">동일한 모듈의 여러 버전을 설치 하려면 다음 절차를 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="6a649-172">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="6a649-173">모듈의 각 버전에 대 한 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-173">Create a directory for each version of the module.</span></span> <span data-ttu-id="6a649-174">디렉터리 이름에 버전 번호가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-174">Include the version number in the directory name.</span></span>

2. <span data-ttu-id="6a649-175">모듈의 각 버전에 대 한 모듈 매니페스트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-175">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="6a649-176">값에는 **ModuleVersion** 매니페스트에서 키, 모듈 버전 번호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-176">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="6a649-177">매니페스트 파일 (.psd1) 모듈에 대 한 버전별 디렉터리에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-177">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>

3. <span data-ttu-id="6a649-178">값으로 모듈 루트 폴더 경로 추가 합니다 **PSModulePath** 환경 변수를 다음 예에서 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-178">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="6a649-179">모듈의 특정 버전을 가져오려면 최종 사용자가 사용할 수는 `MinimumVersion` 나 `RequiredVersion` 의 매개 변수를 [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6a649-179">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="6a649-180">예를 들어, Fabrikam 모듈 버전 8.0 및 9.0에에서 사용 가능한 경우 Fabrikam 모듈 디렉터리 구조는 다음과 같을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-180">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

<span data-ttu-id="6a649-181">모듈 경로를 모두 설치 관리자를 추가 합니다 **PSModulePath** 환경 변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-181">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="6a649-182">이러한 단계가 완료 되 면 합니다 **ListAvailable** 의 매개 변수를 [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet은 Fabrikam 모듈은 모두 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-182">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="6a649-183">특정 모듈을 가져오려면 합니다 `MinimumVersion` 또는 `RequiredVersion` 의 매개 변수를 [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6a649-183">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="6a649-184">모듈을 모두 동일한 세션으로 가져온 모듈 같은 이름의 cmdlet을 포함 하 고 마지막으로 가져온 cmdlet은 세션에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-184">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="6a649-185">처리 명령 이름 충돌</span><span class="sxs-lookup"><span data-stu-id="6a649-185">Handling Command Name Conflicts</span></span>

<span data-ttu-id="6a649-186">명령 이름 충돌은 모듈이 내보내는 명령을 사용자의 세션의 명령과 동일한 이름이 있는 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-186">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="6a649-187">세션에 동일한 이름을 가진 두 개의 명령이 포함 된 Windows PowerShell에 우선적으로 적용 하는 명령 유형을 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-187">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="6a649-188">세션을 동일한 이름과 형식이 같은 두 가지 명령에 포함 되어 있으면 Windows PowerShell 세션을 가장 최근에 추가 된 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-188">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="6a649-189">기본적으로 실행 되지 않는 명령을 실행 하려면 사용자는 모듈 이름으로 명령 이름을 한정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-189">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="6a649-190">예를 들어 세션에는 `Get-Date` 함수 및 `Get-Date` cmdlet을 Windows PowerShell은 기본적으로 함수를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-190">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="6a649-191">Cmdlet을 실행 하려면 명령 앞에 모듈 이름 예:</span><span class="sxs-lookup"><span data-stu-id="6a649-191">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="6a649-192">모듈 작성자 이름 충돌을 방지 하려면 사용 합니다 **DefaultCommandPrefix** 모듈에서 내보낸 모든 명령의 명사 접두사를 지정 하는 모듈 매니페스트에서 키.</span><span class="sxs-lookup"><span data-stu-id="6a649-192">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="6a649-193">사용자가 사용할 수는 **접두사** 의 매개 변수는 `Import-Module` 대체 접두사를 사용 하는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-193">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="6a649-194">값을 **접두사** 매개 변수 값 보다 우선 합니다 **DefaultCommandPrefix** 키입니다.</span><span class="sxs-lookup"><span data-stu-id="6a649-194">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a649-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a649-195">See Also</span></span>

[<span data-ttu-id="6a649-196">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="6a649-196">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="6a649-197">Windows PowerShell 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="6a649-197">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
