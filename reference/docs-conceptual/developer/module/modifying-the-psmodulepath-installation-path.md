---
title: PSModulePath 설치 경로 수정 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 795f2bd52aeceddd3c0ca092d0c0cf2ef44bcf23
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784846"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="8e103-102">PSModulePath 설치 경로 수정</span><span class="sxs-lookup"><span data-stu-id="8e103-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="8e103-103">`PSModulePath`환경 변수는 디스크에 설치 된 모듈의 위치에 대 한 경로를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e103-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="8e103-104">PowerShell에서는 사용자가 모듈의 전체 경로를 지정 하지 않은 경우이 변수를 사용 하 여 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8e103-104">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="8e103-105">이 변수의 경로는 표시 된 순서 대로 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e103-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="8e103-106">PowerShell이 시작 되 면 `PSModulePath` 는 `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` Windows 및 `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` Linux, Mac 및 `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` windows PowerShell의 기본 값을 사용 하 여 시스템 환경 변수로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="8e103-106">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` on Windows and `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` on Linux or Mac, and `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="8e103-107">사용자 고유의 **CurrentUser** 위치는 `WindowsPowerShell\Modules` 사용자 프로필의 **문서** 위치에 있는 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="8e103-107">The user-specific **CurrentUser** location is the `WindowsPowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="8e103-108">해당 위치의 특정 경로는 Windows의 버전에 따라 다르며 폴더 리디렉션을 사용 하는지 여부에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="8e103-108">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="8e103-109">기본적으로 Windows 10의 경우 해당 위치는 `$HOME\Documents\WindowsPowerShell\Modules` 입니다.</span><span class="sxs-lookup"><span data-stu-id="8e103-109">By default, on Windows 10, that location is `$HOME\Documents\WindowsPowerShell\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="8e103-110">PSModulePath 변수를 보려면</span><span class="sxs-lookup"><span data-stu-id="8e103-110">To view the PSModulePath variable</span></span>

<span data-ttu-id="8e103-111">변수에 지정 된 경로를 보려면 `PSModulePath` 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e103-111">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="8e103-112">PSModulePath 변수에 위치를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="8e103-112">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="8e103-113">이 변수에 경로를 추가 하려면 다음 방법 중 하나를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e103-113">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="8e103-114">현재 세션에 대해서만 사용할 수 있는 임시 값을 추가 하려면 명령줄에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e103-114">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="8e103-115">세션이 열릴 때마다 사용할 수 있는 영구 값을 추가 하려면 위의 명령을 PowerShell 프로필 파일 ()에 추가 `$PROFILE` ></span><span class="sxs-lookup"><span data-stu-id="8e103-115">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="8e103-116">프로필에 대한 자세한 내용은 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8e103-116">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="8e103-117">레지스트리에 영구 변수를 추가 하려면 `PSModulePath` **시스템 속성** 대화 상자에서 환경 변수 편집기를 사용 하 여 라는 새 사용자 환경 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8e103-117">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="8e103-118">스크립트를 사용 하 여 영구 변수를 추가 하려면 [system.web](/dotnet/api/system.environment) 클래스에서 .Net 메서드 [SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e103-118">To add a persistent variable by using a script, use the .Net method [SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="8e103-119">예를 들어 다음 스크립트는 컴퓨터의 `C:\Program Files\Fabrikam\Module` 환경 변수 값에 대 한 경로를 추가 합니다 `PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="8e103-119">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="8e103-120">사용자 환경 변수에 대 한 경로를 추가 하려면 `PSModulePath` 대상을 "user"로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e103-120">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="8e103-121">PSModulePath에서 위치를 제거 하려면</span><span class="sxs-lookup"><span data-stu-id="8e103-121">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="8e103-122">유사한 메서드를 사용 하 여 변수에서 경로를 제거할 수 있습니다. 예를 들어 `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` 는 현재 세션에서 **C:\modulepath** 경로를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e103-122">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e103-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e103-123">See Also</span></span>

[<span data-ttu-id="8e103-124">Windows PowerShell 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="8e103-124">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="8e103-125">about_Modules</span><span class="sxs-lookup"><span data-stu-id="8e103-125">about_Modules</span></span>](/powershell/module/microsoft.powershell.core/about/about_modules)
