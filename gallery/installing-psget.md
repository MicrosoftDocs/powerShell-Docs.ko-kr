---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: PowerShellGet 설치
ms.openlocfilehash: a0ef46a9ee4bbf668a58067256d098967bde48c5
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143603"
---
# <a name="installing-powershellget"></a><span data-ttu-id="dd3ab-103">PowerShellGet 설치</span><span class="sxs-lookup"><span data-stu-id="dd3ab-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="dd3ab-104">PowerShellGet은 다음 릴리스에서 제공되는 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="dd3ab-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="dd3ab-105">[Windows 10](https://www.microsoft.com/windows) 이상</span><span class="sxs-lookup"><span data-stu-id="dd3ab-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="dd3ab-106">[Windows Server 2016](/windows-server/windows-server) 이상</span><span class="sxs-lookup"><span data-stu-id="dd3ab-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="dd3ab-107">[WMF(Windows Management Framework) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) 이상</span><span class="sxs-lookup"><span data-stu-id="dd3ab-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="dd3ab-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="dd3ab-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="dd3ab-109">PowerShell 갤러리에서 최신 버전 가져오기</span><span class="sxs-lookup"><span data-stu-id="dd3ab-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="dd3ab-110">**PowerShellGet**을 업데이트하기 전에 항상 최신 **NuGet** 공급자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd3ab-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="dd3ab-111">관리자 권한 PowerShell 세션에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dd3ab-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="dd3ab-112">PowerShell 5.0 이상이 설치된 시스템에 최신 PowerShellGet을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd3ab-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="dd3ab-113">Windows 10, Windows Server 2016, WMF 5.0/5.1이 설치된 시스템 또는 PowerShell 6이 설치된 시스템에서 PowerShellGet을 설치하려면 관리자 권한 PowerShell 세션에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dd3ab-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="dd3ab-114">`Update-Module`을 사용하여 최신 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dd3ab-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-preview"></a><span data-ttu-id="dd3ab-115">PowerShell 3 또는 PowerShell 4를 실행하며 PackageManagement 미리 보기를 설치한 시스템</span><span class="sxs-lookup"><span data-stu-id="dd3ab-115">For systems running PowerShell 3 or PowerShell 4, that have installed the PackageManagement Preview</span></span>

1. <span data-ttu-id="dd3ab-116">관리자 권한 PowerShell 세션에서 `Save-Module`을 사용하여 로컬 디렉터리에 모듈을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="dd3ab-116">From an elevated PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder
   Exit
   ```

1. <span data-ttu-id="dd3ab-117">**PowerShellGet** 및 **PackageManagement** 모듈이 다른 프로세스에서 로드되지 않았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dd3ab-117">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="dd3ab-118">`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 및 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` 폴더에서 콘텐츠 내용을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="dd3ab-118">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="dd3ab-119">관리자 권한으로 PowerShell 콘솔을 다시 열고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dd3ab-119">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```
