---
title: PSModulePath 설치 경로 수정 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: b176d8439025ac132962859f79e72ae6f9703e82
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78405047"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="9ff05-102">PSModulePath 설치 경로 수정</span><span class="sxs-lookup"><span data-stu-id="9ff05-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="9ff05-103">`PSModulePath` 환경 변수는 디스크에 설치 된 모듈의 위치에 대 한 경로를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff05-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="9ff05-104">PowerShell에서는 사용자가 모듈의 전체 경로를 지정 하지 않은 경우이 변수를 사용 하 여 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff05-104">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="9ff05-105">이 변수의 경로는 표시 된 순서 대로 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff05-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="9ff05-106">PowerShell이 시작 되 면 다음과 같은 기본값을 사용 하는 시스템 환경 변수로 `PSModulePath` 만들어집니다. Windows 및 Linux 또는 Mac에서 `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` Windows PowerShell의 경우 `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="9ff05-106">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` on Windows and `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` on Linux or Mac, and `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="9ff05-107">사용자 고유의 **CurrentUser** 위치는 사용자 프로필의 **문서** 위치에 있는 `WindowsPowerShell\Modules` 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff05-107">The user-specific **CurrentUser** location is the `WindowsPowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="9ff05-108">해당 위치의 특정 경로는 Windows의 버전에 따라 다르며 폴더 리디렉션을 사용 하는지 여부에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="9ff05-108">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="9ff05-109">기본적으로 Windows 10에서는 해당 위치가 `$HOME\Documents\WindowsPowerShell\Modules`됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff05-109">By default, on Windows 10, that location is `$HOME\Documents\WindowsPowerShell\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="9ff05-110">PSModulePath 변수를 보려면</span><span class="sxs-lookup"><span data-stu-id="9ff05-110">To view the PSModulePath variable</span></span>

<span data-ttu-id="9ff05-111">`PSModulePath` 변수에 지정 된 경로를 보려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff05-111">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="9ff05-112">PSModulePath 변수에 위치를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="9ff05-112">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="9ff05-113">이 변수에 경로를 추가 하려면 다음 방법 중 하나를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff05-113">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="9ff05-114">현재 세션에 대해서만 사용할 수 있는 임시 값을 추가 하려면 명령줄에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff05-114">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="9ff05-115">세션이 열릴 때마다 사용할 수 있는 영구 값을 추가 하려면 위의 명령을 PowerShell 프로필 파일 (`$PROFILE`)에 추가 ></span><span class="sxs-lookup"><span data-stu-id="9ff05-115">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="9ff05-116">프로필에 대한 자세한 내용은 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ff05-116">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="9ff05-117">레지스트리에 영구 변수를 추가 하려면 **시스템 속성** 대화 상자에서 환경 변수 편집기를 사용 하 여 `PSModulePath` 이라는 새 사용자 환경 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ff05-117">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="9ff05-118">스크립트를 사용 하 여 영구 변수를 추가 하려면 [system.web](https://docs.microsoft.com/dotnet/api/system.environment) 클래스에서 .Net 메서드 [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff05-118">To add a persistent variable by using a script, use the .Net method [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](https://docs.microsoft.com/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="9ff05-119">예를 들어 다음 스크립트는 컴퓨터의 `PSModulePath` 환경 변수 값에 `C:\Program Files\Fabrikam\Module` 경로를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff05-119">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="9ff05-120">사용자 `PSModulePath` 환경 변수에 대 한 경로를 추가 하려면 대상을 "User"로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff05-120">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="9ff05-121">PSModulePath에서 위치를 제거 하려면</span><span class="sxs-lookup"><span data-stu-id="9ff05-121">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="9ff05-122">유사한 메서드를 사용 하 여 변수에서 경로를 제거할 수 있습니다. 예를 들어 `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"`는 현재 세션에서 **C:\modulepath** 경로를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff05-122">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ff05-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ff05-123">See Also</span></span>

[<span data-ttu-id="9ff05-124">Windows PowerShell 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="9ff05-124">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="9ff05-125">about_Modules</span><span class="sxs-lookup"><span data-stu-id="9ff05-125">about_Modules</span></span>](/powershell/module/microsoft.powershell.core/about/about_modules)
