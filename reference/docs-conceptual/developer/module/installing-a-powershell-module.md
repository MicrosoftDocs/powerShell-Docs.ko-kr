---
ms.date: 09/13/2016
ms.topic: reference
title: PowerShell 모듈 설치
description: PowerShell 모듈 설치
ms.openlocfilehash: 3c7a4413168934ca4de1912c9615a6ae0fc45788
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645335"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="3eb59-103">PowerShell 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="3eb59-103">Installing a PowerShell Module</span></span>

<span data-ttu-id="3eb59-104">PowerShell 모듈을 만든 후에는 사용자가 사용할 수 있도록 시스템에 모듈을 설치해야 할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-104">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="3eb59-105">일반적으로 설치는 모듈 파일(즉, .psm1 또는 이진 어셈블리, 모듈 매니페스트 및 기타 관련 파일)을 해당 컴퓨터의 디렉터리에 복사하는 작업으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-105">Generally speaking, this consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="3eb59-106">소규모 프로젝트라면 Windows 탐색기를 사용하여 파일을 단일 원격 컴퓨터에 복사하여 붙여넣는 정도로 간단할 수 있지만, 대규모 솔루션의 경우에는 더 정교한 설치 프로세스를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-106">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="3eb59-107">모듈을 시스템에 가져오는 방법에 관계없이 PowerShell은 사용자가 모듈을 찾아 사용할 수 있도록 하는 다양한 기술을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-107">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="3eb59-108">따라서 설치에서 기본 문제는 PowerShell이 모듈을 검색할 수 있도록 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-108">Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span> <span data-ttu-id="3eb59-109">자세한 내용은 [PowerShell 모듈 가져오기](./importing-a-powershell-module.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eb59-109">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="3eb59-110">모듈 설치 규칙</span><span class="sxs-lookup"><span data-stu-id="3eb59-110">Rules for Installing Modules</span></span>

<span data-ttu-id="3eb59-111">다음 정보는 사용자가 직접 만든 모듈, 다른 당사자에서 가져온 모듈, 다른 사용자에게 배포하는 모듈을 포함한 모든 모듈에 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-111">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="3eb59-112">PSModulePath에 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="3eb59-112">Install Modules in PSModulePath</span></span>

<span data-ttu-id="3eb59-113">가능하면 **PSModulePath** 환경 변수에 나열된 경로에 모든 모듈을 설치하거나 **PSModulePath** 환경 변수 값에 모듈 경로를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-113">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="3eb59-114">**PSModulePath** 환경 변수($Env:PSModulePath)에는 Windows PowerShell 모듈의 위치가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-114">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="3eb59-115">Cmdlet은 이 환경 변수의 값을 사용하여 모듈을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-115">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="3eb59-116">기본적으로 **PSModulePath** 환경 변수 값에는 다음 시스템 및 사용자 모듈 디렉터리가 포함되지만 이 값은 추가하고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-116">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="3eb59-117">`$PSHome\Modules`(%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="3eb59-117">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="3eb59-118">이 위치는 Windows와 함께 제공되는 모듈을 위해 예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-118">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="3eb59-119">이 위치에 모듈을 설치하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="3eb59-119">Do not install modules to this location.</span></span>

- <span data-ttu-id="3eb59-120">`$Home\Documents\WindowsPowerShell\Modules`(%UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="3eb59-120">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="3eb59-121">`$Env:ProgramFiles\WindowsPowerShell\Modules`(%ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="3eb59-121">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="3eb59-122">**PSModulePath** 환경 변수의 값을 가져오려면 다음 명령 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-122">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="3eb59-123">**PSModulePath** 환경 변수 값의 값에 모듈 경로를 추가하려면 다음 명령 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-123">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="3eb59-124">이 형식은 **System.Environment** 클래스의 **SetEnvironmentVariable** 메서드를 사용하여 **PSModulePath** 환경 변수를 세션 독립적으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-124">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="3eb59-125">**PSModulePath** 에 경로를 추가한 후에는 변경 내용에 대한 환경 메시지를 브로드캐스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-125">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="3eb59-126">변경 내용을 브로드캐스트하면 셸과 같은 다른 애플리케이션에서 변경 내용을 반영할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-126">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="3eb59-127">변경 내용을 브로드캐스트하려면 제품 설치 코드에서 `lParam`를 문자열 "Environment"로 설정하여 **WM_SETTINGCHANGE** 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-127">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="3eb59-128">메시지는 모듈 설치 코드가 **PSModulePath** 를 업데이트한 후에 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-128">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="3eb59-129">올바른 모듈 디렉터리 이름 사용</span><span class="sxs-lookup"><span data-stu-id="3eb59-129">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="3eb59-130">잘 구성된(Well-Formed) 모듈은 모듈 디렉터리에 있는 하나 이상의 파일의 기본 이름과 동일한 이름을 갖는 디렉터리에 저장된 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-130">A well-formed module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="3eb59-131">모듈이 제대로 구성되지 않은 경우 Windows PowerShell이 모듈을 인식하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-131">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="3eb59-132">파일의 "기본 이름"은 파일 이름 확장명이 없는 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-132">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="3eb59-133">잘 구성된(Well-Formed) 모듈에서 모듈 파일이 포함된 디렉터리의 이름은 모듈에 있는 하나 이상의 파일에 대한 기본 이름과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-133">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="3eb59-134">예를 들어 샘플 Fabrikam 모듈에서 모듈 파일이 포함된 디렉터리의 이름은 "Fabrikam"이고 하나 이상의 파일에는 "Fabrikam" 기본 이름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-134">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="3eb59-135">이 경우 Fabrikam.psd1 및 Fabrikam.dll 모두에 "Fabrikam" 기본 이름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-135">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="3eb59-136">잘못된 설치의 영향</span><span class="sxs-lookup"><span data-stu-id="3eb59-136">Effect of Incorrect Installation</span></span>

<span data-ttu-id="3eb59-137">모듈이 제대로 구성되지 않고 해당 위치가 **PSModulePath** 환경 변수의 값에 포함되어 있지 않으면 다음과 같은 Windows PowerShell의 기본 검색 기능이 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-137">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="3eb59-138">모듈 자동 로드 기능이 모듈을 자동으로 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-138">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="3eb59-139">[Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet의 `ListAvailable` 매개 변수가 모듈을 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-139">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="3eb59-140">[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet이 모듈을 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-140">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="3eb59-141">모듈을 가져오려면 루트 모듈 파일 또는 모듈 매니페스트 파일의 전체 경로를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-141">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="3eb59-142">모듈을 세션으로 가져오지 않은 경우 다음과 같은 추가 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-142">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="3eb59-143">**PSModulePath** 환경 변수의 잘 구성된(Well-Formed) 모듈에서는 모듈을 세션으로 가져오지 않은 경우에도 이러한 기능이 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-143">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="3eb59-144">[Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet이 모듈의 명령을 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-144">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="3eb59-145">[Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 및 [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet이 모듈에 대한 도움말을 업데이트하거나 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-145">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="3eb59-146">[Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet이 모듈의 명령을 검색하여 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-146">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="3eb59-147">모듈의 명령이 Windows PowerShell ISE(통합 스크립팅 환경)의 `Show-Command` 창에서 누락됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-147">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="3eb59-148">모듈을 설치하는 위치</span><span class="sxs-lookup"><span data-stu-id="3eb59-148">Where to Install Modules</span></span>

<span data-ttu-id="3eb59-149">이 섹션에서는 파일 시스템에서 Windows PowerShell 모듈을 설치할 위치에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-149">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="3eb59-150">이 위치는 모듈이 사용되는 방식에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-150">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="3eb59-151">특정 사용자용 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="3eb59-151">Installing Modules for a Specific User</span></span>

<span data-ttu-id="3eb59-152">사용자 고유의 모듈을 만들거나 Windows PowerShell 커뮤니티 웹 사이트와 같은 다른 당사자에서 모듈을 가져와 사용자 계정에서만 사용할 수 있도록 하려면 사용자별 Modules 디렉터리에 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-152">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

<span data-ttu-id="3eb59-153">사용자별 Modules 디렉터리는 기본적으로 **PSModulePath** 환경 변수의 값에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-153">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="3eb59-154">Program Files에 모든 사용자용 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="3eb59-154">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="3eb59-155">컴퓨터의 모든 사용자 계정에서 모듈을 사용할 수 있도록 하려면 Program Files 위치에 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-155">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> <span data-ttu-id="3eb59-156">Program Files 위치는 Windows PowerShell 4.0 이상에서 기본적으로 PSModulePath 환경 변수의 값에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-156">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="3eb59-157">이전 버전의 Windows PowerShell에서는 수동으로 Program Files 위치(%ProgramFiles%\WindowsPowerShell\Modules)를 만들고 위에서 설명한 대로 PSModulePath 환경 변수에 이 경로를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-157">For earlier versions of Windows PowerShell, you can manually create the Program Files location (%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="3eb59-158">Product 디렉터리에 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="3eb59-158">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="3eb59-159">다른 당사자에게 모듈을 배포하는 경우 위에 설명된 기본 Program Files 위치를 사용하거나 %ProgramFiles% 디렉터리의 회사별 또는 제품별 하위 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-159">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="3eb59-160">예를 들어, 가상 회사인 Fabrikam Technologies는 Fabrikam Manager 제품용 Windows PowerShell 모듈을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-160">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="3eb59-161">Fabrikam 모듈 설치 관리자는 Fabrikam Manager 제품 하위 디렉터리에 Modules 하위 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-161">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="3eb59-162">Windows PowerShell 모듈 검색 기능을 사용하여 Fabrikam 모듈을 찾기 위해 Fabrikam 모듈 설치 관리자는 **PSModulePath** 환경 변수의 값에 모듈 위치를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-162">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="3eb59-163">Common Files 디렉터리에 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="3eb59-163">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="3eb59-164">제품의 여러 구성 요소 또는 여러 버전의 제품에서 한 모듈을 사용하는 경우 %ProgramFiles%\Common Files\Modules 하위 디렉터리의 모듈별 하위 디렉터리에 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-164">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="3eb59-165">다음 예제에서 Fabrikam 모듈은 `%ProgramFiles%\Common Files\Modules` 하위 디렉터리의 Fabrikam 하위 디렉터리에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-165">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the `%ProgramFiles%\Common Files\Modules` subdirectory.</span></span> <span data-ttu-id="3eb59-166">각 모듈은 Modules 하위 디렉터리 아래의 자체 하위 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-166">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

<span data-ttu-id="3eb59-167">그런 다음 설치 관리자는 **PSModulePath** 환경 변수의 값에 Common Files Modules 하위 디렉터리의 경로를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-167">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

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

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="3eb59-168">여러 버전의 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="3eb59-168">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="3eb59-169">동일한 모듈의 여러 버전을 설치하려면 다음 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-169">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="3eb59-170">각 모듈 버전에 대한 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-170">Create a directory for each version of the module.</span></span> <span data-ttu-id="3eb59-171">디렉터리 이름에 버전 번호를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-171">Include the version number in the directory name.</span></span>
2. <span data-ttu-id="3eb59-172">각 모듈 버전에 대한 모듈 매니페스트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-172">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="3eb59-173">매니페스트의 **ModuleVersion** 키 값에 모듈 버전 번호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-173">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="3eb59-174">모듈의 버전별 디렉터리에 매니페스트 파일(. psd1)을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-174">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>
3. <span data-ttu-id="3eb59-175">다음 예제와 같이 **PSModulePath** 환경 변수의 값에 모듈 루트 폴더 경로를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-175">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="3eb59-176">특정 버전의 모듈을 가져오기 위해 최종 사용자는 [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet의 `MinimumVersion` 또는 `RequiredVersion` 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-176">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="3eb59-177">예를 들어 Fabrikam 모듈의 버전 8.0 및 9.0을 사용할 수 있는 경우 Fabrikam 모듈 디렉터리 구조는 다음과 비슷할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-177">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

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

<span data-ttu-id="3eb59-178">설치 관리자는 **PSModulePath** 환경 변수 값에 두 모듈 경로를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-178">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="3eb59-179">이러한 단계가 완료되면 [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet의 **ListAvailable** 매개 변수가 두 Fabrikam 모듈을 모두 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-179">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="3eb59-180">특정 모듈을 가져오려면 [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet의 `MinimumVersion` 또는 `RequiredVersion` 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-180">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="3eb59-181">두 모듈을 동일한 세션으로 가져올 때 모듈에 동일한 이름의 cmdlet이 포함된 경우 마지막으로 가져온 cmdlet이 세션에서 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-181">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="3eb59-182">명령 이름 충돌 처리</span><span class="sxs-lookup"><span data-stu-id="3eb59-182">Handling Command Name Conflicts</span></span>

<span data-ttu-id="3eb59-183">명령 이름 충돌은 모듈이 내보내는 명령의 이름이 사용자 세션의 명령과 동일한 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-183">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="3eb59-184">한 세션에 이름이 같은 명령이 두 개 포함된 경우 Windows PowerShell은 우선 순위가 높은 명령 유형을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-184">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="3eb59-185">한 세션에 이름 및 유형이 같은 명령이 두 개 포함된 경우 Windows PowerShell은 가장 최근에 세션에 추가된 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-185">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="3eb59-186">기본적으로 실행되지 않는 명령을 실행하려면 사용자가 모듈 이름을 사용하여 명령 이름을 한정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-186">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="3eb59-187">예를 들어 세션에 `Get-Date` 함수와 `Get-Date` cmdlet이 포함되어 있으면 Windows PowerShell은 기본적으로 함수를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-187">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="3eb59-188">Cmdlet을 실행하려면 명령 앞에 다음과 같은 모듈 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-188">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="3eb59-189">이름 충돌을 방지하기 위해 모듈 작성자는 모듈 매니페스트에 **DefaultCommandPrefix** 키를 사용하여 모듈에서 내보낸 모든 명령에 대한 명사 접두사를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-189">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="3eb59-190">사용자는 `Import-Module` cmdlet의 **Prefix** 매개 변수를 사용하여 대체 접두사를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-190">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="3eb59-191">**Prefix** 매개 변수 값은 **DefaultCommandPrefix** 키보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb59-191">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="3eb59-192">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3eb59-192">See Also</span></span>

[<span data-ttu-id="3eb59-193">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="3eb59-193">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="3eb59-194">Windows PowerShell 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="3eb59-194">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
