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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360672"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="98e77-102">PSModulePath 설치 경로 수정</span><span class="sxs-lookup"><span data-stu-id="98e77-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="98e77-103">@No__t-0 환경 변수는 디스크에 설치 된 모듈의 위치에 대 한 경로를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="98e77-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="98e77-104">사용자가 모듈의 전체 경로를 지정 하지 않은 경우 Windows PowerShell에서이 변수를 사용 하 여 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="98e77-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="98e77-105">이 변수의 경로는 표시 된 순서 대로 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98e77-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="98e77-106">Windows PowerShell이 시작 되 면 `PSModulePath`이 다음 기본값을 가진 시스템 환경 변수로 만들어집니다. `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="98e77-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="98e77-107">PSModulePath 변수를 보려면</span><span class="sxs-lookup"><span data-stu-id="98e77-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="98e77-108">@No__t-0 변수에 지정 된 경로를 보려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="98e77-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="98e77-109">PSModulePath 변수에 위치를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="98e77-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="98e77-110">이 변수에 경로를 추가 하려면 다음 방법 중 하나를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="98e77-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="98e77-111">현재 세션에 대해서만 사용할 수 있는 임시 값을 추가 하려면 명령줄에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="98e77-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="98e77-112">세션이 열릴 때마다 사용할 수 있는 영구 값을 추가 하려면 Windows PowerShell 프로필에 다음 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="98e77-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="98e77-113">프로필에 대 한 자세한 내용은 Microsoft TechNet library의 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="98e77-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="98e77-114">레지스트리에 영구 변수를 추가 하려면 **시스템 속성** 대화 상자의 환경 변수 편집기를 사용 하 여 `PSModulePath` 이라는 새 사용자 환경 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="98e77-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="98e77-115">스크립트를 사용 하 여 영구 변수를 추가 하려면 Environment 클래스에서 **SetEnvironmentVariable** 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="98e77-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="98e77-116">예를 들어 다음 스크립트는 컴퓨터의 PSModulePath 환경 변수 값에 "C:\Program Files\Fabrikam\Module path를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="98e77-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="98e77-117">사용자 PSModulePath 환경 변수에 대 한 경로를 추가 하려면 대상을 "User"로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="98e77-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="98e77-118">PSModulePath에서 위치를 제거 하려면</span><span class="sxs-lookup"><span data-stu-id="98e77-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="98e77-119">유사한 메서드를 사용 하 여 변수에서 경로를 제거할 수 있습니다. 예를 들어 `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"`은 현재 세션에서 **C:\modulepath** 경로를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="98e77-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="98e77-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98e77-120">See Also</span></span>

[<span data-ttu-id="98e77-121">Windows PowerShell 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="98e77-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
