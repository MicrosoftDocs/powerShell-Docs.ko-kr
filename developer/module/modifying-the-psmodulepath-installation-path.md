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
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082212"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="34629-102">PSModulePath 설치 경로 수정</span><span class="sxs-lookup"><span data-stu-id="34629-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="34629-103">`PSModulePath` 환경 변수는 디스크에 설치 된 모듈의 위치로 경로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="34629-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="34629-104">Windows PowerShell이이 변수를 사용 하 여 사용자는 모듈의 전체 경로 지정 하지 않은 경우 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="34629-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="34629-105">이 변수에서 경로 순서 대로 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34629-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="34629-106">Windows PowerShell 시작 되 면 `PSModulePath` 다음 기본값을 사용 하 여 시스템 환경 변수를으로 만들어집니다: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`합니다.</span><span class="sxs-lookup"><span data-stu-id="34629-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="34629-107">PSModulePath 변수를 보려면</span><span class="sxs-lookup"><span data-stu-id="34629-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="34629-108">에 지정 된 경로를 보려면를 `PSModulePath` 변수인 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="34629-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="34629-109">PSModulePath 변수에 위치를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="34629-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="34629-110">경로이 변수를 추가 하려면 다음 방법 중 하나를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="34629-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="34629-111">현재 세션에 대해서만 사용할 수 있는 임시 값을 추가 하려면 명령줄에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="34629-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="34629-112">영구 세션을 열 때마다 사용할 수 있는 값을 추가 하려면 다음 명령을 Windows PowerShell 프로필에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="34629-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="34629-113">프로필에 대 한 자세한 내용은 참조 하세요. [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) Microsoft TechNet 라이브러리에서.</span><span class="sxs-lookup"><span data-stu-id="34629-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="34629-114">영구 변수를 레지스트리에 추가 라는 새로운 사용자 환경 변수를 만듭니다 `PSModulePath` 에서 환경 변수 편집기를 사용 하 여 **시스템 속성** 대화 상자.</span><span class="sxs-lookup"><span data-stu-id="34629-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="34629-115">스크립트를 사용 하 여 영구 변수를 추가 하려면 사용 합니다 **SetEnvironmentVariable** Environment 클래스는 메서드.</span><span class="sxs-lookup"><span data-stu-id="34629-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="34629-116">예를 들어, 다음 스크립트 경로 추가 "C:\Program Files\Fabrikam\Module 컴퓨터용 PSModulePath 환경 변수의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="34629-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="34629-117">경로 사용자 PSModulePath 환경 변수를 추가 하려면 대상을 "User"로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="34629-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="34629-118">PSModulePath 위치를 제거 하려면</span><span class="sxs-lookup"><span data-stu-id="34629-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="34629-119">이와 유사한 메서드를 사용 하 여 변수에서 경로 제거할 수 있습니다: 예를 들어 `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` 제거 됩니다는 **c:\ModulePath** 현재 세션에서 경로.</span><span class="sxs-lookup"><span data-stu-id="34629-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="34629-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34629-120">See Also</span></span>

[<span data-ttu-id="34629-121">Windows PowerShell 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="34629-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
