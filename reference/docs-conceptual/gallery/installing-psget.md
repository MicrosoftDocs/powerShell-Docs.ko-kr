---
ms.date: 09/19/2019
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: PowerShellGet 설치
ms.openlocfilehash: f42eb0df101eb63a5dc267196fa9f666747b8e35
ms.sourcegitcommit: 23ea4a36ee85f923684657de5313a5adf0b6b094
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83727798"
---
# <a name="installing-powershellget"></a><span data-ttu-id="7befc-103">PowerShellGet 설치</span><span class="sxs-lookup"><span data-stu-id="7befc-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="7befc-104">PowerShellGet은 다음 릴리스에서 제공되는 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="7befc-105">[Windows 10](https://www.microsoft.com/windows) 이상</span><span class="sxs-lookup"><span data-stu-id="7befc-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="7befc-106">[Windows Server 2016](/windows-server/windows-server) 이상</span><span class="sxs-lookup"><span data-stu-id="7befc-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="7befc-107">[WMF(Windows Management Framework) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) 이상</span><span class="sxs-lookup"><span data-stu-id="7befc-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="7befc-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="7befc-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="7befc-109">PowerShell 갤러리에서 최신 버전 가져오기</span><span class="sxs-lookup"><span data-stu-id="7befc-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="7befc-110">**PowerShellGet**을 업데이트하기 전에 항상 최신 **NuGet** 공급자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="7befc-111">관리자 권한 PowerShell 세션에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="7befc-112">PowerShell 5.0 이상이 설치된 시스템에 최신 PowerShellGet을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="7befc-113">Windows 10, Windows Server 2016, WMF 5.0/5.1이 설치된 시스템 또는 PowerShell 6이 설치된 시스템에서 PowerShellGet을 설치하려면 관리자 권한 PowerShell 세션에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="7befc-114">`Update-Module`을 사용하여 최신 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a><span data-ttu-id="7befc-115">PowerShell 3.0 또는 PowerShell 4.0을 실행하는 컴퓨터의 경우</span><span class="sxs-lookup"><span data-stu-id="7befc-115">For computers running PowerShell 3.0 or PowerShell 4.0</span></span>

<span data-ttu-id="7befc-116">이러한 지침은 **PackageManagement 미리 보기**가 설치되어 있거나 **PowerShellGet** 버전이 설치되어 있지 않은 컴퓨터에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-116">These instructions apply to computers that have the **PackageManagement Preview** installed or don't have any version of **PowerShellGet** installed.</span></span>

<span data-ttu-id="7befc-117">`Save-Module` cmdlet은 두 명령 세트에 모두 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-117">The `Save-Module` cmdlet is used in both sets of instructions.</span></span> <span data-ttu-id="7befc-118">`Save-Module`은 등록된 리포지토리에서 모듈 및 모든 종속성을 다운로드하여 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-118">`Save-Module` downloads and saves a module and any dependencies from a registered repository.</span></span> <span data-ttu-id="7befc-119">모듈의 최신 버전은 로컬 컴퓨터의 지정된 경로에 저장되지만 설치되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-119">The module's most current version is saved to a specified path on the local computer, but isn't installed.</span></span> <span data-ttu-id="7befc-120">PowerShell 3.0 또는 4.0에서 모듈을 설치하려면 모듈이 저장된 폴더를 `$env:ProgramFiles\WindowsPowerShell\Modules`에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-120">To install the modules in PowerShell 3.0 or 4.0, copy the module saved folders to `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span>

<span data-ttu-id="7befc-121">자세한 내용은 [Save-Module](/powershell/module/PowershellGet/Save-Module)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7befc-121">For more information, see [Save-Module](/powershell/module/PowershellGet/Save-Module).</span></span>

> [!NOTE]
> <span data-ttu-id="7befc-122">PowerShell 3.0 및 PowerShell 4.0은 한 가지 버전의 모듈만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-122">PowerShell 3.0 and PowerShell 4.0 only supported one version of a module.</span></span> <span data-ttu-id="7befc-123">PowerShell 5.0부터 모듈은 `<modulename>\<version>`에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-123">Starting in PowerShell 5.0, modules are installed in `<modulename>\<version>`.</span></span> <span data-ttu-id="7befc-124">이렇게 하면 여러 버전을 함께 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-124">This allowed you to install multiple versions side-by-side.</span></span> <span data-ttu-id="7befc-125">`Save-Module`을 사용하여 모듈을 다운로드한 후 파일을 `<modulename>\<version>`에서 대상 머신의 `<modulename>` 폴더로 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-125">After downloading the module using `Save-Module` you must copy the files from the `<modulename>\<version>` to the `<modulename>` folder on the destination machine.</span></span>

#### <a name="computers-with-the-packagemanagement-preview-installed"></a><span data-ttu-id="7befc-126">PackageManagement 미리 보기가 설치된 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="7befc-126">Computers with the PackageManagement Preview installed</span></span>

1. <span data-ttu-id="7befc-127">PowerShell 세션에서 `Save-Module`을 사용하여 로컬 디렉터리에 모듈을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-127">From a PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="7befc-128">**PowerShellGet** 및 **PackageManagement** 모듈이 다른 프로세스에서 로드되지 않았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-128">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="7befc-129">`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 및 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` 폴더에서 콘텐츠 내용을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-129">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="7befc-130">관리자 권한으로 PowerShell 콘솔을 다시 열고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-130">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\<version>\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\<version>\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a><span data-ttu-id="7befc-131">PowerShellGet이 없는 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="7befc-131">Computers without PowerShellGet</span></span>

<span data-ttu-id="7befc-132">**PowerShellGet** 버전이 설치되어 있지 않은 컴퓨터의 경우 모듈을 다운로드하려면 **PowerShellGet**이 설치된 컴퓨터가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-132">For computer's without any version of **PowerShellGet** installed, a computer with **PowerShellGet** installed is needed to download the modules.</span></span>

1. <span data-ttu-id="7befc-133">**PowerShellGet**이 설치된 컴퓨터에서 `Save-Module`를 사용하여 현재 버전의 **PowerShellGet**를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-133">From the computer that has **PowerShellGet** installed, use `Save-Module` to download the current version of **PowerShellGet**.</span></span> <span data-ttu-id="7befc-134">다운로드되는 폴더는 다음의 두 가지입니다. **PowerShellGet** 및 **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="7befc-134">Two folders are downloaded: **PowerShellGet** and **PackageManagement**.</span></span> <span data-ttu-id="7befc-135">각 폴더에는 버전 번호가 있는 하위 폴더가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-135">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="7befc-136">**PowerShellGet** 및 **PackageManagement** 폴더를 **PowerShellGet**가 설치되지 않은 컴퓨터에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-136">Copy the **PowerShellGet** and **PackageManagement** folders to the computer that doesn't have **PowerShellGet** installed.</span></span>

   <span data-ttu-id="7befc-137">대상 디렉터리는 `$env:ProgramFiles\WindowsPowerShell\Modules`입니다.</span><span class="sxs-lookup"><span data-stu-id="7befc-137">The destination directory is: `$env:ProgramFiles\WindowsPowerShell\Modules`</span></span>
