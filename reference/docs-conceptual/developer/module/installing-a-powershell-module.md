---
title: PowerShell 모듈 설치 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6a4e9ac2884d0b300b5c1ad8b6156525438a1650
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784863"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="428bf-102">PowerShell 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="428bf-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="428bf-103">PowerShell 모듈을 만든 후에는 사용자 또는 다른 사용자가 사용할 수 있도록 시스템에 모듈을 설치 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="428bf-104">일반적으로이는 모듈 파일 (즉, .psm1 또는 이진 어셈블리, 모듈 매니페스트 및 기타 관련 파일)을 해당 컴퓨터의 디렉터리에 복사 하는 것으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-104">Generally speaking, this consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="428bf-105">매우 작은 프로젝트의 경우 Windows 탐색기를 사용 하 여 파일을 단일 원격 컴퓨터에 복사 하 여 붙여 넣는 것 만큼 간단할 수 있습니다. 그러나 대규모 솔루션의 경우 더 복잡 한 설치 프로세스를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="428bf-106">모듈을 시스템에 가져오는 방법에 관계 없이 PowerShell은 사용자가 모듈을 찾아서 사용할 수 있도록 하는 다양 한 기술을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="428bf-107">따라서 설치의 주요 문제는 PowerShell이 모듈을 찾을 수 있는지 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-107">Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span> <span data-ttu-id="428bf-108">자세한 내용은 [PowerShell 모듈 가져오기](./importing-a-powershell-module.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="428bf-108">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="428bf-109">모듈 설치 규칙</span><span class="sxs-lookup"><span data-stu-id="428bf-109">Rules for Installing Modules</span></span>

<span data-ttu-id="428bf-110">사용자가 직접 만든 모듈, 다른 파티에서 가져온 모듈 및 다른 사용자에 게 배포 하는 모듈을 포함 하 여 모든 모듈에 대 한 정보는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-110">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="428bf-111">PSModulePath에 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="428bf-111">Install Modules in PSModulePath</span></span>

<span data-ttu-id="428bf-112">가능 하면 **PSModulePath** 환경 변수에 나열 된 경로에 모든 모듈을 설치 하거나 **PSModulePath** 환경 변수 값에 모듈 경로를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-112">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="428bf-113">**PSModulePath** 환경 변수 ($Env:P SModulePath)에는 Windows PowerShell 모듈의 위치가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-113">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="428bf-114">Cmdlet은이 환경 변수의 값을 사용 하 여 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-114">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="428bf-115">기본적으로 **PSModulePath** 환경 변수 값에는 다음 시스템 및 사용자 모듈 디렉터리가 포함 되지만 값을 추가 하 고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-115">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="428bf-116">`$PSHome\Modules`%Windir%\System32\WindowsPowerShell\v1.0\Modules</span><span class="sxs-lookup"><span data-stu-id="428bf-116">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="428bf-117">이 위치는 Windows와 함께 제공 되는 모듈에 대해 예약 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-117">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="428bf-118">이 위치에 모듈을 설치 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="428bf-118">Do not install modules to this location.</span></span>

- <span data-ttu-id="428bf-119">`$Home\Documents\WindowsPowerShell\Modules`(%UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="428bf-119">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="428bf-120">`$Env:ProgramFiles\WindowsPowerShell\Modules`(%ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="428bf-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="428bf-121">**PSModulePath** 환경 변수의 값을 가져오려면 다음 명령 중 하나를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-121">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="428bf-122">**PSModulePath** 환경 변수 값 값에 모듈 경로를 추가 하려면 다음 명령 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-122">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="428bf-123">이 형식은 **system.object** 클래스의 **SetEnvironmentVariable** 메서드를 사용 하 여 **PSModulePath** 환경 변수에 대 한 세션 독립적 변경을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-123">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="428bf-124">**PSModulePath**에 대 한 경로를 추가한 후에는 변경 내용에 대 한 환경 메시지를 브로드캐스트합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-124">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="428bf-125">변경을 브로드캐스팅 하면 셸과 같은 다른 응용 프로그램에서 변경 내용을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-125">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="428bf-126">변경을 브로드캐스트하려면 제품 설치 코드에서를 **WM_SETTINGCHANGE** `lParam` "환경" 문자열로 설정 하 여 WM_SETTINGCHANGE 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-126">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="428bf-127">모듈 설치 코드에서 **PSModulePath**를 업데이트 한 후 메시지를 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-127">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="428bf-128">올바른 모듈 디렉터리 이름 사용</span><span class="sxs-lookup"><span data-stu-id="428bf-128">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="428bf-129">올바른 형식의 모듈은 모듈 디렉터리에서 하나 이상의 파일에 대 한 기본 이름과 이름이 동일한 디렉터리에 저장 된 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-129">A well-formed module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="428bf-130">모듈이 제대로 구성 되지 않은 경우 Windows PowerShell은 모듈을 인식 하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-130">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="428bf-131">파일의 "기본 이름"은 파일 이름 확장명이 없는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-131">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="428bf-132">잘 구성 된 모듈에서 모듈 파일을 포함 하는 디렉터리의 이름은 모듈에 있는 하나 이상의 파일에 대 한 기본 이름과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-132">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="428bf-133">예를 들어 sample Fabrikam 모듈에서 모듈 파일을 포함 하는 디렉터리의 이름은 "Fabrikam"이 고 하나 이상의 파일에는 "Fabrikam" 기본 이름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-133">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="428bf-134">이 경우 Fabrikam.psd1과 Fabrikam.dll에 모두 "Fabrikam" 기본 이름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-134">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="428bf-135">잘못 된 설치의 영향</span><span class="sxs-lookup"><span data-stu-id="428bf-135">Effect of Incorrect Installation</span></span>

<span data-ttu-id="428bf-136">모듈이 제대로 구성 되지 않은 경우 해당 위치가 **PSModulePath** 환경 변수의 값에 포함 되어 있지 않으면 다음과 같은 Windows PowerShell의 기본 검색 기능이 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-136">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="428bf-137">모듈 자동 로드 기능은 모듈을 자동으로 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-137">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="428bf-138">`ListAvailable`Import-module cmdlet의 매개 [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) 변수는 모듈을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-138">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="428bf-139">Import-module [cmdlet은](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 모듈을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-139">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="428bf-140">모듈을 가져오려면 루트 모듈 파일 또는 모듈 매니페스트 파일의 전체 경로를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-140">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="428bf-141">모듈을 세션으로 가져오지 않은 경우 다음과 같은 추가 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-141">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="428bf-142">**PSModulePath** 환경 변수의 잘 구성 된 모듈에서는 모듈을 세션으로 가져오지 않은 경우에도 이러한 기능이 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-142">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="428bf-143">[Get 명령](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet은 모듈에서 명령을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-143">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="428bf-144">[업데이트-도움말](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 및 [저장-도움말](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet은 모듈에 대 한 도움말을 업데이트 하거나 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-144">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="428bf-145">[표시 명령](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet은 모듈의 명령을 찾아 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-145">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="428bf-146">`Show-Command`Windows POWERSHELL ISE (통합 스크립팅 환경)의 창에 모듈의 명령이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-146">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="428bf-147">모듈을 설치 하는 위치</span><span class="sxs-lookup"><span data-stu-id="428bf-147">Where to Install Modules</span></span>

<span data-ttu-id="428bf-148">이 섹션에서는 Windows PowerShell 모듈을 설치 하는 파일 시스템의 위치에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-148">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="428bf-149">위치는 모듈이 사용 되는 방식에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-149">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="428bf-150">특정 사용자에 대 한 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="428bf-150">Installing Modules for a Specific User</span></span>

<span data-ttu-id="428bf-151">사용자 고유의 모듈을 만들거나 Windows PowerShell 커뮤니티 웹 사이트와 같은 다른 파티에서 모듈을 가져올 경우 해당 모듈을 사용자 계정에만 사용할 수 있도록 하려면 사용자 특정 모듈 디렉터리에 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-151">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

<span data-ttu-id="428bf-152">사용자 전용 모듈 디렉터리는 기본적으로 **PSModulePath** 환경 변수 값에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-152">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="428bf-153">프로그램 파일에 모든 사용자에 대 한 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="428bf-153">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="428bf-154">컴퓨터의 모든 사용자 계정에 모듈을 사용할 수 있도록 하려면 Program Files 위치에 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-154">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> <span data-ttu-id="428bf-155">Program Files 위치는 Windows PowerShell 4.0 이상에서 기본적으로 PSModulePath 환경 변수의 값에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-155">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="428bf-156">이전 버전의 Windows PowerShell에서는 프로그램 파일 위치 ((%ProgramFiles%\WindowsPowerShell\Modules)를 수동으로 만들고 위에서 설명한 대로 PSModulePath 환경 변수에이 경로를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-156">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="428bf-157">제품 디렉터리에 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="428bf-157">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="428bf-158">다른 파티에 모듈을 배포 하는 경우 위에 설명 된 기본 프로그램 파일 위치를 사용 하거나% ProgramFiles% 디렉터리의 고유한 회사 또는 제품별 하위 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-158">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="428bf-159">예를 들어, 가상 회사인 Fabrikam 기술은 Fabrikam 관리자 제품에 대 한 Windows PowerShell 모듈을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-159">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="428bf-160">모듈 설치 관리자는 Fabrikam Manager product 하위 디렉터리에 Modules 하위 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-160">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="428bf-161">Windows PowerShell 모듈 검색 기능을 사용 하 여 Fabrikam 모듈을 찾기 위해 Fabrikam 모듈 설치 관리자는 **PSModulePath** 환경 변수의 값에 모듈 위치를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-161">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="428bf-162">Common Files 디렉터리에 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="428bf-162">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="428bf-163">제품의 여러 구성 요소 또는 여러 버전의 제품에서 모듈을 사용 하는 경우%ProgramFiles%\Common Files\Modules 하위 디렉터리의 모듈별 하위 디렉터리에 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-163">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="428bf-164">다음 예제에서 Fabrikam 모듈은 하위 디렉터리의 Fabrikam 하위 디렉터리에 설치 됩니다 `%ProgramFiles%\Common Files\Modules` .</span><span class="sxs-lookup"><span data-stu-id="428bf-164">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the `%ProgramFiles%\Common Files\Modules` subdirectory.</span></span> <span data-ttu-id="428bf-165">각 모듈은 Modules 하위 디렉터리에 있는 자체 하위 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-165">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

<span data-ttu-id="428bf-166">그런 다음 설치 관리자는 **PSModulePath** 환경 변수의 값에 공용 파일 모듈 하위 디렉터리의 경로를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-166">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

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

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="428bf-167">여러 버전의 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="428bf-167">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="428bf-168">동일한 모듈의 여러 버전을 설치 하려면 다음 절차를 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="428bf-168">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="428bf-169">모듈의 각 버전에 대 한 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-169">Create a directory for each version of the module.</span></span> <span data-ttu-id="428bf-170">디렉터리 이름에 버전 번호를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-170">Include the version number in the directory name.</span></span>
2. <span data-ttu-id="428bf-171">모듈의 각 버전에 대 한 모듈 매니페스트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-171">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="428bf-172">매니페스트의 **ModuleVersion** 키 값에 모듈 버전 번호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-172">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="428bf-173">모듈에 대 한 버전별 디렉터리에 매니페스트 파일 (. psd1)을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-173">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>
3. <span data-ttu-id="428bf-174">다음 예제에 표시 된 것 처럼 **PSModulePath** 환경 변수의 값에 module root 폴더 경로를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-174">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="428bf-175">모듈의 특정 버전을 가져오기 위해 최종 사용자는 `MinimumVersion` `RequiredVersion` [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet의 또는 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-175">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="428bf-176">예를 들어 Fabrikam 모듈을 버전 8.0 및 9.0에서 사용할 수 있는 경우 Fabrikam 모듈 디렉터리 구조는 다음과 유사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-176">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

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

<span data-ttu-id="428bf-177">설치 관리자는 두 모듈 경로를 모두 **PSModulePath** 환경 변수 값에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-177">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="428bf-178">이러한 단계가 완료 되 면 ListAvailable [cmdlet의](/powershell/module/Microsoft.PowerShell.Core/Get-Module) **ListAvailable** 매개 변수가 Fabrikam 모듈을 모두 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-178">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="428bf-179">특정 모듈을 가져오려면 `MinimumVersion` `RequiredVersion` [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet의 또는 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-179">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="428bf-180">두 모듈을 동일한 세션으로 가져올 때 모듈에 동일한 이름의 cmdlet이 포함 된 경우 마지막으로 가져온 cmdlet은 세션에서 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-180">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="428bf-181">명령 이름 충돌 처리</span><span class="sxs-lookup"><span data-stu-id="428bf-181">Handling Command Name Conflicts</span></span>

<span data-ttu-id="428bf-182">명령 이름 충돌은 모듈이 내보내는 명령의 이름이 사용자 세션의 명령과 동일한 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-182">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="428bf-183">세션에 이름이 같은 두 개의 명령이 포함 된 경우 Windows PowerShell은 우선 순위가 높은 명령 유형을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-183">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="428bf-184">세션에 이름과 형식이 같은 명령이 두 개 포함 된 경우 Windows PowerShell은 가장 최근에 세션에 추가 된 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-184">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="428bf-185">기본적으로 실행 되지 않는 명령을 실행 하려면 사용자가 모듈 이름으로 명령 이름을 한정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-185">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="428bf-186">예를 들어 세션에 함수 및 cmdlet이 포함 되어 있으면 `Get-Date` `Get-Date` Windows PowerShell은 기본적으로 함수를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-186">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="428bf-187">Cmdlet을 실행 하려면 명령 앞에 모듈 이름 (예:)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-187">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="428bf-188">이름 충돌을 방지 하기 위해 모듈 작성자는 모듈 매니페스트의 **Defaultcommandprefix** 키를 사용 하 여 모듈에서 내보낸 모든 명령의 명사 접두사를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-188">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="428bf-189">사용자는 cmdlet의 **prefix** 매개 변수를 사용 `Import-Module` 하 여 대체 접두사를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-189">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="428bf-190">**Prefix** 매개 변수 값은 **defaultcommandprefix** 키의 값 보다 우선 합니다.</span><span class="sxs-lookup"><span data-stu-id="428bf-190">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="428bf-191">참고 항목</span><span class="sxs-lookup"><span data-stu-id="428bf-191">See Also</span></span>

[<span data-ttu-id="428bf-192">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="428bf-192">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="428bf-193">Windows PowerShell 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="428bf-193">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
