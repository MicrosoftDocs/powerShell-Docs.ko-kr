---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: 라이선스 동의가 필요한 모듈
ms.openlocfilehash: a2f7ed72aae8579a6723f65b86dd0993f1a22afd
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "80082824"
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="dfdb9-103">라이선스 동의가 필요한 모듈</span><span class="sxs-lookup"><span data-stu-id="dfdb9-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="dfdb9-104">개요</span><span class="sxs-lookup"><span data-stu-id="dfdb9-104">SYNOPSIS</span></span>

<span data-ttu-id="dfdb9-105">일부 모듈 게시자의 법률 부서에서는 고객이 PowerShell 갤러리에서 모듈을 설치하기 전에 명시적으로 라이선스에 동의하도록 요구합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="dfdb9-106">사용자가 직접 또는 다른 패키지에 대한 종속성을 통해 PowerShellGet을 사용하여 모듈을 설치, 업데이트 또는 저장할 때 해당 모듈에서 사용자가 라이선스에 동의할 것을 요구하는 경우 사용자는 라이선스에 동의해야 합니다. 동의하지 않으면 작업에 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another package, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="dfdb9-107">모듈에 요구 사항 게시</span><span class="sxs-lookup"><span data-stu-id="dfdb9-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="dfdb9-108">사용자에게 라이선스 동의를 요구하는 모듈은 다음 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="dfdb9-109">모듈 매니페스트의 PSData 섹션에 RequireLicenseAcceptance = $True가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="dfdb9-110">모듈의 루트 디렉터리에 license.txt 파일이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="dfdb9-111">모듈 매니페스트에 라이선스 URI가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="dfdb9-112">모듈은 PowerShellGet 형식 버전 2.0 이상으로 게시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="dfdb9-113">Install/Save/Update-Module에 미치는 영향</span><span class="sxs-lookup"><span data-stu-id="dfdb9-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="dfdb9-114">Install/Save/Update cmdlet은 사용자가 라이선스를 확인한 것처럼 동작하는 새 매개 변수 **AcceptLicense**를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-114">Install/Save/Update cmdlets support a new parameter **AcceptLicense** that behaves as though the user saw the license.</span></span>
- <span data-ttu-id="dfdb9-115">**RequiredLicenseAcceptance**가 True이고 **AcceptLicense**가 지정되지 않은 경우 사용자에게 `license.txt`가 표시되고 `Do you accept these license terms
  (Yes/No/YesToAll/NoToAll)`라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-115">If **RequiredLicenseAcceptance** is True and **AcceptLicense** is not specified, the user is shown the `license.txt`, and prompted with: `Do you accept these license terms
  (Yes/No/YesToAll/NoToAll)`.</span></span>
  - <span data-ttu-id="dfdb9-116">라이선스에 동의하는 경우</span><span class="sxs-lookup"><span data-stu-id="dfdb9-116">If the license is accepted</span></span>
    - <span data-ttu-id="dfdb9-117">**Save-Module:** 모듈이 사용자의 시스템에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-117">**Save-Module:** the module is copied to the user's system</span></span>
    - <span data-ttu-id="dfdb9-118">**Install-Module:** 모듈이 사용자의 시스템에서 적절한 폴더(범위 기준)에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-118">**Install-Module:** the module is copied to the user's system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="dfdb9-119">**Update-Module:** 모듈이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-119">**Update-Module:** the module is updated.</span></span>
  - <span data-ttu-id="dfdb9-120">라이선스에 동의하지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="dfdb9-120">If the license is declined.</span></span>
    - <span data-ttu-id="dfdb9-121">작업이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-121">Operation is canceled.</span></span>
    - <span data-ttu-id="dfdb9-122">모든 cmdlet은 라이선스 동의가 필요한 메타데이터(**requireLicenseAcceptance** 및 형식 버전)를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-122">All cmdlets check for the metadata (**requireLicenseAcceptance** and Format Version) that says a license acceptance is required</span></span>
    - <span data-ttu-id="dfdb9-123">클라이언트의 형식 버전이 2.0보다 이전 버전인 경우 작업에 실패하고 사용자에게 클라이언트를 업데이트하도록 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-123">If format version of client is older than 2.0, operation fails and asks the user to update the client.</span></span>
    - <span data-ttu-id="dfdb9-124">모듈이 2.0보다 낮은 형식 버전으로 게시된 경우 requireLicenseAcceptance 플래그가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag is ignored.</span></span>

## <a name="module-dependencies"></a><span data-ttu-id="dfdb9-125">모듈 종속성</span><span class="sxs-lookup"><span data-stu-id="dfdb9-125">Module Dependencies</span></span>

- <span data-ttu-id="dfdb9-126">설치/저장/업데이트 작업 중 종속 모듈(모듈에 종속되는 작업)에 라이선스 동의가 필요한 경우 라이선스 동의 동작(위)이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) is required.</span></span>
- <span data-ttu-id="dfdb9-127">시스템에 설치되면서 모듈 버전이 로컬 카탈로그에 이미 나열되어 있는 경우 라이선스 확인을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="dfdb9-128">설치/저장/업데이트 작업 중 종속 모듈에 라이선스가 필요한데 사용자가 라이선스에 동의하지 않은 경우, 작업에 실패하고 패키지 설치/저장/업데이트 실패에 대한 일반적인 프로세스가 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation fails and follows normal processes for the package failed to install/save/update.</span></span>

## <a name="impact-on--force"></a><span data-ttu-id="dfdb9-129">-Force에 대한 영향</span><span class="sxs-lookup"><span data-stu-id="dfdb9-129">Impact on -Force</span></span>

<span data-ttu-id="dfdb9-130">`–Force`를 지정하여 라이선스에 동의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-130">Specifying `–Force` is NOT sufficient to accept a license.</span></span> <span data-ttu-id="dfdb9-131">설치 권한에 대해 `–AcceptLicense`가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-131">`–AcceptLicense` is required for permission to install.</span></span> <span data-ttu-id="dfdb9-132">`–Force`가 지정되고 RequiredLicenseAcceptance가 True이고 `–AcceptLicense`가 지정되지 않으면 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-132">If `–Force` is specified, RequiredLicenseAcceptance is True, and `–AcceptLicense` is NOT specified, the operation fails.</span></span>

## <a name="examples"></a><span data-ttu-id="dfdb9-133">예제</span><span class="sxs-lookup"><span data-stu-id="dfdb9-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="dfdb9-134">예제 1: 모듈 매니페스트를 업데이트하여 라이선스 동의 요구</span><span class="sxs-lookup"><span data-stu-id="dfdb9-134">Example 1: Update Module Manifest to require license acceptance</span></span>

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

<span data-ttu-id="dfdb9-135">이 명령은 매니페스트 파일을 업데이트하고 RequireLicenseAcceptance 플래그를 true로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>

### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="dfdb9-136">예제 2: 라이선스 동의가 필요한 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="dfdb9-136">Example 2: Install Module requiring license acceptance</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```Output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="dfdb9-137">이 명령은 `license.txt` 파일의 라이선스를 표시하고 사용자에게 라이선스에 동의하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-137">This command shows the license from `license.txt` file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="dfdb9-138">예제 3: -AcceptLicense로 라이선스 동의가 필요한 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="dfdb9-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="dfdb9-139">라이선스에 동의하라는 메시지가 표시되지 않고 모듈이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="dfdb9-140">예제 4: -Force로 라이선스 동의가 필요한 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="dfdb9-140">Example 4: Install Module requiring license acceptance with -Force</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -Force
```

```Output
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="dfdb9-141">예제 5: 라이선스 동의가 필요한 종속성이 있는 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="dfdb9-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>

<span data-ttu-id="dfdb9-142">모듈 **ModuleWithDependency**는 모듈 **ModuleRequireLicenseAcceptance**에 종속됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-142">Module **ModuleWithDependency** depends on module **ModuleRequireLicenseAcceptance**.</span></span> <span data-ttu-id="dfdb9-143">사용자에게 라이선스에 동의하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-143">User is prompted to accept license.</span></span>

```powershell
Install-Module -Name ModuleWithDependency
```

```Output
License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="dfdb9-144">예제 6: 라이선스 동의 및 -AcceptLicense가 필요한 종속성이 있는 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="dfdb9-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="dfdb9-145">모듈 **ModuleWithDependency**는 모듈 **ModuleRequireLicenseAcceptance**에 종속됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-145">Module **ModuleWithDependency** depends on module **ModuleRequireLicenseAcceptance**.</span></span> <span data-ttu-id="dfdb9-146">**AcceptLicense**가 지정되면 사용자에게 라이선스에 동의하라는 메시지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-146">User is not prompted to accept license as **AcceptLicense** is specified.</span></span>

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="dfdb9-147">예제 7: PSGetFormatVersion 2.0 이전의 클라이언트에서 라이선스 동의가 필요한 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="dfdb9-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```Output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion
'2.0' is not supported by the current version of PowerShellGet. Get the latest version of the
PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="dfdb9-148">예제 8: 라이선스 동의가 필요한 모듈 저장</span><span class="sxs-lookup"><span data-stu-id="dfdb9-148">Example 8: Save Module requiring license acceptance</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved
```

```Output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="dfdb9-149">이 명령은 `license.txt` 파일의 라이선스를 표시하고 사용자에게 라이선스에 동의하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-149">This command shows the license from `license.txt` file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="dfdb9-150">예제 9: -AcceptLicense로 라이선스 동의가 필요한 모듈 저장</span><span class="sxs-lookup"><span data-stu-id="dfdb9-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

<span data-ttu-id="dfdb9-151">라이선스에 동의하라는 메시지가 표시되지 않고 모듈이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="dfdb9-152">예제 10: 라이선스 동의가 필요한 모듈 업데이트</span><span class="sxs-lookup"><span data-stu-id="dfdb9-152">Example 10: Update Module requiring license acceptance</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance
```

```Output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="dfdb9-153">이 명령은 `license.txt` 파일의 라이선스를 표시하고 사용자에게 라이선스에 동의하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-153">This command shows the license from `license.txt` file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="dfdb9-154">예제 11: -AcceptLicense로 라이선스 동의가 필요한 모듈 업데이트</span><span class="sxs-lookup"><span data-stu-id="dfdb9-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="dfdb9-155">라이선스에 동의하라는 메시지가 표시되지 않고 모듈이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfdb9-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="dfdb9-156">자세한 내용</span><span class="sxs-lookup"><span data-stu-id="dfdb9-156">More details</span></span>

[<span data-ttu-id="dfdb9-157">스크립트에 대한 라이선스 동의 필요</span><span class="sxs-lookup"><span data-stu-id="dfdb9-157">Require License Acceptance for Scripts</span></span>](./script-license-acceptance.md)

[<span data-ttu-id="dfdb9-158">PowerShellGallery에서 라이선스 동의 지원 필요</span><span class="sxs-lookup"><span data-stu-id="dfdb9-158">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[<span data-ttu-id="dfdb9-159">Azure Automation에 배포에 대한 라이선스 동의 필요</span><span class="sxs-lookup"><span data-stu-id="dfdb9-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
