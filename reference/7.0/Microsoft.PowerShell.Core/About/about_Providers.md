---
description: PowerShell 공급자가 명령줄에서 다른 방법으로 쉽게 액세스할 수 없는 데이터 및 구성 요소에 대 한 액세스를 제공 하는 방법을 설명 합니다. 데이터는 파일 시스템 드라이브와 비슷한 일관 된 형식으로 제공 됩니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_providers?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Providers
ms.openlocfilehash: c0ae976c9f82a8a7481eda2bad136e7ba2689a44
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220650"
---
# <a name="about-providers"></a><span data-ttu-id="2c057-105">공급자 정보</span><span class="sxs-lookup"><span data-stu-id="2c057-105">About Providers</span></span>

## <a name="short-description"></a><span data-ttu-id="2c057-106">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="2c057-106">Short description</span></span>
<span data-ttu-id="2c057-107">PowerShell 공급자가 명령줄에서 다른 방법으로 쉽게 액세스할 수 없는 데이터 및 구성 요소에 대 한 액세스를 제공 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-107">Describes how PowerShell providers provide access to data and components that wouldn't otherwise be easily accessible at the command line.</span></span>
<span data-ttu-id="2c057-108">데이터는 파일 시스템 드라이브와 비슷한 일관 된 형식으로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-108">The data is presented in a consistent format that resembles a file system drive.</span></span>

## <a name="long-description"></a><span data-ttu-id="2c057-109">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-109">Long description</span></span>

<span data-ttu-id="2c057-110">PowerShell 공급자는 보기 및 관리를 용이 하 게 하는 특수 한 데이터 저장소에 대 한 액세스를 제공 하는 .NET 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-110">PowerShell providers are .NET programs that provide access to specialized data stores for easier viewing and management.</span></span> <span data-ttu-id="2c057-111">데이터는 드라이브에 표시 되며 하드 디스크 드라이브와 같은 경로에 있는 데이터에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-111">The data appears in a drive, and you access the data in a path like you would on a hard disk drive.</span></span> <span data-ttu-id="2c057-112">공급자가 지 원하는 기본 제공 cmdlet 중 하나를 사용 하 여 공급자 드라이브의 데이터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-112">You can use any of the built-in cmdlets that the provider supports to manage the data in the provider drive.</span></span> <span data-ttu-id="2c057-113">데이터에 대해 특별히 디자인 된 사용자 지정 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-113">And, you can use custom cmdlets that are designed especially for the data.</span></span>

<span data-ttu-id="2c057-114">공급자는 기본 제공 cmdlet에 동적 매개 변수를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-114">The providers can also add dynamic parameters to the built-in cmdlets.</span></span> <span data-ttu-id="2c057-115">이러한 매개 변수는 공급자 데이터와 함께 cmdlet을 사용 하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-115">These parameters are only available when you use the cmdlet with the provider data.</span></span>

## <a name="built-in-providers"></a><span data-ttu-id="2c057-116">기본 제공 공급자</span><span class="sxs-lookup"><span data-stu-id="2c057-116">Built-in providers</span></span>

<span data-ttu-id="2c057-117">PowerShell에는 다양 한 유형의 데이터 저장소에 액세스 하는 데 사용할 수 있는 기본 제공 공급자 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-117">PowerShell includes a set of built-in providers that you can use to access the different types of data stores.</span></span>

| <span data-ttu-id="2c057-118">공급자</span><span class="sxs-lookup"><span data-stu-id="2c057-118">Provider</span></span>   |   <span data-ttu-id="2c057-119">개 드라이브</span><span class="sxs-lookup"><span data-stu-id="2c057-119">Drive(s)</span></span>  |<span data-ttu-id="2c057-120">OutputType</span><span class="sxs-lookup"><span data-stu-id="2c057-120">OutputType</span></span>                                                    |
|----------- |------------ |--------------------------------------------------------------|
|<span data-ttu-id="2c057-121">Alias</span><span class="sxs-lookup"><span data-stu-id="2c057-121">Alias</span></span>       |<span data-ttu-id="2c057-122">별칭:</span><span class="sxs-lookup"><span data-stu-id="2c057-122">Alias:</span></span>       |<span data-ttu-id="2c057-123">System.management.automation.aliasinfo.</span><span class="sxs-lookup"><span data-stu-id="2c057-123">System.Management.Automation.AliasInfo</span></span>                        |
|<span data-ttu-id="2c057-124">인증서</span><span class="sxs-lookup"><span data-stu-id="2c057-124">Certificate</span></span> |<span data-ttu-id="2c057-125">인증서:</span><span class="sxs-lookup"><span data-stu-id="2c057-125">Cert:</span></span>        |<span data-ttu-id="2c057-126">Microsoft.powershell.commands.x509storelocation.</span><span class="sxs-lookup"><span data-stu-id="2c057-126">Microsoft.PowerShell.Commands.X509StoreLocation</span></span>               |
|            |             |<span data-ttu-id="2c057-127">System.Security.Cryptography.X509Certificates.X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="2c057-127">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>|
|<span data-ttu-id="2c057-128">Environment</span><span class="sxs-lookup"><span data-stu-id="2c057-128">Environment</span></span> |<span data-ttu-id="2c057-129">Env:</span><span class="sxs-lookup"><span data-stu-id="2c057-129">Env:</span></span>         |<span data-ttu-id="2c057-130">DictionaryEntry</span><span class="sxs-lookup"><span data-stu-id="2c057-130">System.Collections.DictionaryEntry</span></span>                            |
|<span data-ttu-id="2c057-131">FileSystem</span><span class="sxs-lookup"><span data-stu-id="2c057-131">FileSystem</span></span>  |<span data-ttu-id="2c057-132">C: (\*)</span><span class="sxs-lookup"><span data-stu-id="2c057-132">C: (\*)</span></span>       |<span data-ttu-id="2c057-133">System.object</span><span class="sxs-lookup"><span data-stu-id="2c057-133">System.IO.FileInfo</span></span>                                            |
|            |             |<span data-ttu-id="2c057-134">System.io.directoryinfo</span><span class="sxs-lookup"><span data-stu-id="2c057-134">System.IO.DirectoryInfo</span></span>                                       |
|<span data-ttu-id="2c057-135">함수</span><span class="sxs-lookup"><span data-stu-id="2c057-135">Function</span></span>    |<span data-ttu-id="2c057-136">함수:</span><span class="sxs-lookup"><span data-stu-id="2c057-136">Function:</span></span>    |<span data-ttu-id="2c057-137">System.object를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-137">System.Management.Automation.FunctionInfo</span></span>                     |
|<span data-ttu-id="2c057-138">레지스트리</span><span class="sxs-lookup"><span data-stu-id="2c057-138">Registry</span></span>    |<span data-ttu-id="2c057-139">HKLM: HKCU:</span><span class="sxs-lookup"><span data-stu-id="2c057-139">HKLM: HKCU:</span></span>  |<span data-ttu-id="2c057-140">Microsoft Win32 RegistryKey</span><span class="sxs-lookup"><span data-stu-id="2c057-140">Microsoft.Win32.RegistryKey</span></span>                                   |
|<span data-ttu-id="2c057-141">변수</span><span class="sxs-lookup"><span data-stu-id="2c057-141">Variable</span></span>    |<span data-ttu-id="2c057-142">변수:</span><span class="sxs-lookup"><span data-stu-id="2c057-142">Variable:</span></span>    |<span data-ttu-id="2c057-143">System.object입니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-143">System.Management.Automation.PSVariable</span></span>                       |
|<span data-ttu-id="2c057-144">WSMan</span><span class="sxs-lookup"><span data-stu-id="2c057-144">WSMan</span></span>       |<span data-ttu-id="2c057-145">WSMan:</span><span class="sxs-lookup"><span data-stu-id="2c057-145">WSMan:</span></span>       |<span data-ttu-id="2c057-146">에서 wsmanconfigcontainerelement가.</span><span class="sxs-lookup"><span data-stu-id="2c057-146">Microsoft.WSMan.Management.WSManConfigContainerElement</span></span>        |

<span data-ttu-id="2c057-147">(\*) 파일 시스템 드라이브는 각 시스템 마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-147">(\*) The FileSystem drives vary on each system.</span></span>

<span data-ttu-id="2c057-148">사용자 고유의 PowerShell 공급자를 만들 수도 있으며, 다른 사용자가 개발 하는 공급자를 설치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-148">You can also create your own PowerShell providers, and you can install providers that others develop.</span></span> <span data-ttu-id="2c057-149">세션에서 사용할 수 있는 공급자를 나열 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-149">To list the providers that are available in your session, type:</span></span>

```powershell
Get-PSProvider
```

## <a name="installing-and-removing-providers"></a><span data-ttu-id="2c057-150">공급자 설치 및 제거</span><span class="sxs-lookup"><span data-stu-id="2c057-150">Installing and removing providers</span></span>

<span data-ttu-id="2c057-151">공급자는 일반적으로 PowerShell 모듈을 통해 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-151">Providers are typically installed via PowerShell modules.</span></span> <span data-ttu-id="2c057-152">모듈을 가져오면 해당 공급자가 세션으로 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-152">Importing the module loads the provider into your session.</span></span> <span data-ttu-id="2c057-153">기본 제공 공급자를 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-153">You can't uninstall the built-in providers.</span></span> <span data-ttu-id="2c057-154">다른 모듈에 의해 로드 된 공급자를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-154">You can uninstall providers loaded by other modules.</span></span>

<span data-ttu-id="2c057-155">Cmdlet을 사용 하 여 현재 세션에서 공급자를 언로드할 수 있습니다 `Remove-Module` .</span><span class="sxs-lookup"><span data-stu-id="2c057-155">You can unload a provider from the current session using the `Remove-Module` cmdlet.</span></span> <span data-ttu-id="2c057-156">이 cmdlet은 공급자를 제거 하지 않지만 해당 공급자를 세션에서 사용할 수 없게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-156">This cmdlet doesn't uninstall the provider, but it makes the provider unavailable in the session.</span></span>

<span data-ttu-id="2c057-157">Cmdlet을 사용 하 여 `Remove-PSDrive` 현재 세션에서 드라이브를 제거할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-157">You can also use the `Remove-PSDrive` cmdlet to remove any drive from the current session.</span></span> <span data-ttu-id="2c057-158">드라이브의이 데이터는 영향을 받지 않지만 해당 세션에서 더 이상 드라이브를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-158">This data on the drive isn't affected, but the drive is no longer available in that session.</span></span>

## <a name="viewing-providers"></a><span data-ttu-id="2c057-159">공급자 보기</span><span class="sxs-lookup"><span data-stu-id="2c057-159">Viewing providers</span></span>

<span data-ttu-id="2c057-160">컴퓨터에서 PowerShell 공급자를 보려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-160">To view the PowerShell providers on your computer, type:</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="2c057-161">출력에는 기본 제공 공급자와 세션에 추가한 공급자가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-161">The output lists the built-in providers and the providers that you added to the session.</span></span>

## <a name="the-provider-cmdlets"></a><span data-ttu-id="2c057-162">공급자 cmdlet</span><span class="sxs-lookup"><span data-stu-id="2c057-162">The provider cmdlets</span></span>

<span data-ttu-id="2c057-163">다음 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-163">The following cmdlets are designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="2c057-164">동일한 방식으로 동일한 cmdlet을 사용 하 여 공급자가 노출 하는 다양 한 데이터 형식을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-164">You can use the same cmdlets in the same way to manage the different types of data that providers expose.</span></span> <span data-ttu-id="2c057-165">한 공급자의 데이터를 관리 하는 방법을 학습 한 후에는 모든 공급자의 데이터와 동일한 절차를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-165">After you learn to manage the data of one provider, you can use the same procedures with the data from any provider.</span></span>

<span data-ttu-id="2c057-166">예를 들어 `New-Item` cmdlet은 새 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-166">For example, the `New-Item` cmdlet creates a new item.</span></span> <span data-ttu-id="2c057-167">`C:` **FileSystem** 공급자가 지 원하는 드라이브에서를 사용 `New-Item` 하 여 새 파일이 나 폴더를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-167">In the `C:` drive that is supported by the **FileSystem** provider, you can use `New-Item` to create a new file or folder.</span></span> <span data-ttu-id="2c057-168">**레지스트리** 공급자가 지 원하는 드라이브에서를 사용 `New-Item` 하 여 새 레지스트리 키를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-168">In the drives that are supported by the **Registry** provider, you can use `New-Item` to create a new registry key.</span></span> <span data-ttu-id="2c057-169">드라이브에서를 `Alias:` 사용 `New-Item` 하 여 새 별칭을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-169">In the `Alias:` drive, you can use `New-Item` to create a new alias.</span></span>

<span data-ttu-id="2c057-170">다음 cmdlet에 대 한 자세한 내용을 보려면 다음을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2c057-170">For detailed information about any of the following cmdlets, type:</span></span>

```
Get-Help <cmdlet-name> -Detailed
```

### <a name="childitem-cmdlets"></a><span data-ttu-id="2c057-171">ChildItem cmdlet</span><span class="sxs-lookup"><span data-stu-id="2c057-171">ChildItem cmdlets</span></span>

- [<span data-ttu-id="2c057-172">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="2c057-172">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="content-cmdlets"></a><span data-ttu-id="2c057-173">콘텐츠 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2c057-173">Content Cmdlets</span></span>

- [<span data-ttu-id="2c057-174">Add-Content</span><span class="sxs-lookup"><span data-stu-id="2c057-174">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="2c057-175">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="2c057-175">Clear-Content</span></span>](xref:Microsoft.PowerShell.Management.Clear-Content)
- [<span data-ttu-id="2c057-176">Get-Content</span><span class="sxs-lookup"><span data-stu-id="2c057-176">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="2c057-177">Set-Content</span><span class="sxs-lookup"><span data-stu-id="2c057-177">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="item-cmdlets"></a><span data-ttu-id="2c057-178">항목 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2c057-178">Item Cmdlets</span></span>

- [<span data-ttu-id="2c057-179">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="2c057-179">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="2c057-180">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="2c057-180">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="2c057-181">Get-Item</span><span class="sxs-lookup"><span data-stu-id="2c057-181">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="2c057-182">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="2c057-182">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="2c057-183">Move-Item</span><span class="sxs-lookup"><span data-stu-id="2c057-183">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="2c057-184">New-Item</span><span class="sxs-lookup"><span data-stu-id="2c057-184">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="2c057-185">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="2c057-185">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="2c057-186">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="2c057-186">Rename-Item</span></span>](xref:Microsoft.PowerShell.Management.Rename-Item)
- [<span data-ttu-id="2c057-187">Set-Item</span><span class="sxs-lookup"><span data-stu-id="2c057-187">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

### <a name="itemproperty-cmdlets"></a><span data-ttu-id="2c057-188">Get-itemproperty cmdlet</span><span class="sxs-lookup"><span data-stu-id="2c057-188">ItemProperty cmdlets</span></span>

- [<span data-ttu-id="2c057-189">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2c057-189">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="2c057-190">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2c057-190">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)
- [<span data-ttu-id="2c057-191">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2c057-191">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="2c057-192">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2c057-192">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)
- [<span data-ttu-id="2c057-193">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2c057-193">New-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.New-ItemProperty)
- [<span data-ttu-id="2c057-194">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2c057-194">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="2c057-195">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2c057-195">Rename-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Rename-ItemProperty)
- [<span data-ttu-id="2c057-196">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="2c057-196">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

### <a name="location-cmdlets"></a><span data-ttu-id="2c057-197">위치 cmdlet</span><span class="sxs-lookup"><span data-stu-id="2c057-197">Location cmdlets</span></span>

- [<span data-ttu-id="2c057-198">Get-Location</span><span class="sxs-lookup"><span data-stu-id="2c057-198">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="2c057-199">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="2c057-199">Pop-Location</span></span>](xref:Microsoft.PowerShell.Management.Pop-Location)
- [<span data-ttu-id="2c057-200">Push-Location</span><span class="sxs-lookup"><span data-stu-id="2c057-200">Push-Location</span></span>](xref:Microsoft.PowerShell.Management.Push-Location)
- [<span data-ttu-id="2c057-201">Set-Location</span><span class="sxs-lookup"><span data-stu-id="2c057-201">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)

### <a name="path-cmdlets"></a><span data-ttu-id="2c057-202">경로 cmdlet</span><span class="sxs-lookup"><span data-stu-id="2c057-202">Path cmdlets</span></span>

- [<span data-ttu-id="2c057-203">Join-Path</span><span class="sxs-lookup"><span data-stu-id="2c057-203">Join-Path</span></span>](xref:Microsoft.PowerShell.Management.Join-Path)
- [<span data-ttu-id="2c057-204">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="2c057-204">Convert-Path</span></span>](xref:Microsoft.PowerShell.Management.Convert-Path)
- [<span data-ttu-id="2c057-205">Split-Path</span><span class="sxs-lookup"><span data-stu-id="2c057-205">Split-Path</span></span>](xref:Microsoft.PowerShell.Management.Split-Path)
- [<span data-ttu-id="2c057-206">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="2c057-206">Resolve-Path</span></span>](xref:Microsoft.PowerShell.Management.Resolve-Path)
- [<span data-ttu-id="2c057-207">Test-Path</span><span class="sxs-lookup"><span data-stu-id="2c057-207">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="psdrive-cmdlets"></a><span data-ttu-id="2c057-208">PSDrive cmdlet</span><span class="sxs-lookup"><span data-stu-id="2c057-208">PSDrive cmdlets</span></span>

- [<span data-ttu-id="2c057-209">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="2c057-209">Get-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [<span data-ttu-id="2c057-210">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="2c057-210">New-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.New-PSDrive)
- [<span data-ttu-id="2c057-211">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="2c057-211">Remove-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Remove-PSDrive)

### <a name="psprovider-cmdlets"></a><span data-ttu-id="2c057-212">PSProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2c057-212">PSProvider Cmdlets</span></span>

- [<span data-ttu-id="2c057-213">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="2c057-213">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)

## <a name="viewing-provider-data"></a><span data-ttu-id="2c057-214">공급자 데이터 보기</span><span class="sxs-lookup"><span data-stu-id="2c057-214">Viewing provider data</span></span>

<span data-ttu-id="2c057-215">공급자의 주요 장점은 친숙 하 고 일관 된 방식으로 데이터를 노출 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-215">The primary benefit of a provider is that it exposes its data in a familiar and consistent way.</span></span> <span data-ttu-id="2c057-216">데이터 프레젠테이션용 모델은 파일 시스템 드라이브입니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-216">The model for data presentation is a file system drive.</span></span>

<span data-ttu-id="2c057-217">공급자를 사용 하면 파일 시스템의 데이터와 동일한 방법으로 데이터 저장소의 항목을 보고, 탐색 하 고, 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-217">The provider allows you to view, navigate, and change items in the data store as though they were data in a file system.</span></span> <span data-ttu-id="2c057-218">데이터 저장소는 지원 되는 드라이브의 이름을 통해 액세스 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-218">The data store is accessed by the name of the drive that it supports.</span></span>

<span data-ttu-id="2c057-219">Cmdlet의 기본 표시에 드라이브가 나열 `Get-PSProvider` 되지만 cmdlet을 사용 하 여 공급자 드라이브에 대 한 정보를 가져올 수 있습니다 `Get-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="2c057-219">The drive is listed in the default display of the `Get-PSProvider` cmdlet, but you can get information about the provider drive using the `Get-PSDrive` cmdlet.</span></span> <span data-ttu-id="2c057-220">예를 들어 Function: drive의 모든 속성을 가져오려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-220">For example, to get all the properties of the Function: drive, type:</span></span>

```powershell
Get-PSDrive Function | Format-List *
```

<span data-ttu-id="2c057-221">파일 시스템 드라이브에 있는 것 처럼 공급자 드라이브의 데이터를 확인 하 고 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-221">You can view and move through the data in a provider drive just as you would on a file system drive.</span></span>

<span data-ttu-id="2c057-222">공급자 드라이브의 내용을 보려면 Get-Item 또는 Get-ChildItem cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-222">To view the contents of a provider drive, use the Get-Item or Get-ChildItem cmdlets.</span></span> <span data-ttu-id="2c057-223">드라이브 이름 뒤에 콜론 (:)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-223">Type the drive name followed by a colon (:).</span></span> <span data-ttu-id="2c057-224">예를 들어 Alias: 드라이브의 내용을 보려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-224">For example, to view the contents of the Alias: drive, type:</span></span>

```powershell
Get-Item alias:
```

<span data-ttu-id="2c057-225">경로에 드라이브 이름을 포함 하 여 다른 드라이브의 모든 드라이브에서 데이터를 보고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-225">You can view and manage the data in any drive from another drive by including the drive name in the path.</span></span> <span data-ttu-id="2c057-226">예를 들어 다른 드라이브의 HKLM: 드라이브에서 HKLM\Software 레지스트리 키를 보려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-226">For example, to view the HKLM\Software registry key in the HKLM: drive from another drive, type:</span></span>

```powershell
Get-ChildItem HKLM:\SOFTWARE\
```

<span data-ttu-id="2c057-227">드라이브를 열려면 Set-Location cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-227">To open the drive, use the Set-Location cmdlet.</span></span> <span data-ttu-id="2c057-228">드라이브 경로를 지정할 때는 콜론을 명심 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2c057-228">Remember the colon when you specify the drive path.</span></span> <span data-ttu-id="2c057-229">예를 들어, 위치를 Cert: 드라이브의 루트 디렉터리로 변경 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-229">For example, to change your location to the root directory of the Cert: drive, type:</span></span>

```powershell
Set-Location cert:
```

<span data-ttu-id="2c057-230">그런 다음, Cert: 드라이브의 내용을 보려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-230">Then, to view the contents of the Cert: drive, type:</span></span>

```powershell
Get-ChildItem
```

## <a name="moving-through-hierarchical-data"></a><span data-ttu-id="2c057-231">계층적 데이터 이동</span><span class="sxs-lookup"><span data-stu-id="2c057-231">Moving through hierarchical data</span></span>

<span data-ttu-id="2c057-232">하드 디스크 드라이브와 마찬가지로 공급자 드라이브를 통해 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-232">You can move through a provider drive just as you would a hard disk drive.</span></span>
<span data-ttu-id="2c057-233">데이터가 항목 내 항목의 계층 구조에 정렬 되어 있는 경우 백슬래시 ()를 사용 `\` 하 여 자식 항목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-233">If the data is arranged in a hierarchy of items within items, use a backslash (`\`) to indicate a child item.</span></span> <span data-ttu-id="2c057-234">이때 다음 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-234">Use the following format:</span></span>

```
drive:\location\child-location\...
```

<span data-ttu-id="2c057-235">예를 들어 HKLM\Software 레지스트리 키에 대 한 위치를 변경 하려면 다음과 같은 Set-Location 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-235">For example, to change your location to the HKLM\Software registry key, type a Set-Location command, such as:</span></span>

```powershell
Set-Location HKLM:\SOFTWARE\
```

<span data-ttu-id="2c057-236">정규화 된 이름의 요소에 공백이 포함 된 경우 이름을 큰따옴표 ()로 묶어야 합니다 `"` .</span><span class="sxs-lookup"><span data-stu-id="2c057-236">If any element in the fully qualified name includes spaces, you must enclose the name in double-quotation marks (`"`).</span></span> <span data-ttu-id="2c057-237">다음 예에서는 공백이 포함 된 정규화 된 경로를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-237">The following example shows a fully qualified path that includes spaces.</span></span>

```
"C:\Program Files\Internet Explorer\iexplore.exe"
```

<span data-ttu-id="2c057-238">위치에 대 한 상대 참조를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-238">You can also use relative references to locations.</span></span> <span data-ttu-id="2c057-239">점 ( `.` )은 현재 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-239">A dot (`.`) represents the current location.</span></span> <span data-ttu-id="2c057-240">예를 들어 레지스트리 키에 있는 경우 `HKLM:\Software\Microsoft` 키에 레지스트리 하위 키를 나열 하려면 `HKLM:\Software\Microsoft\PowerShell` 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-240">For example, if you are in the `HKLM:\Software\Microsoft` registry key, and you want to list the registry subkeys in the `HKLM:\Software\Microsoft\PowerShell` key, type the following command:</span></span>

```powershell
Get-ChildItem .\PowerShell
```

<span data-ttu-id="2c057-241">또한 이중 점 ( `..` )은 현재 위치 바로 위의 디렉터리나 컨테이너를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-241">Also, double-dots (`..`) refers to the directory or container directly above your current location.</span></span> <span data-ttu-id="2c057-242">이중 점 ( `..` )을 사용 하 여 공급자 계층 구조를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-242">You can use double-dots (`..`) to navigate through a provider hierarchy.</span></span>

```
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\> cd ..\..\LanmanWorkstation\Parameters
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters>
```

## <a name="provider-home"></a><span data-ttu-id="2c057-243">공급자 홈</span><span class="sxs-lookup"><span data-stu-id="2c057-243">Provider Home</span></span>

<span data-ttu-id="2c057-244">공급자에는 또한 **홈** 위치가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-244">Providers also have a **Home** location.</span></span>  <span data-ttu-id="2c057-245">이 위치는 공급자가 지 원하는 모든에서 공유 `PSDrives` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-245">This location is shared by all `PSDrives` backed by the provider.</span></span> <span data-ttu-id="2c057-246">공급자의 **Home** 속성을 확인 하 여 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-246">It can be retrieved by viewing the **Home** property of the provider.</span></span>

```powershell
Get-PSProvider | Format-Table Name, Home
```

```Output
Name        Home
----        ----
Registry
Alias
Environment
FileSystem  C:\Users\username
Function
Variable
Certificate
```

<span data-ttu-id="2c057-247">**FileSystem** 공급자는 **홈** 에 대 한 기본값을 가진 유일한 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-247">The **FileSystem** provider is the only provider that has a default value for **Home**.</span></span> <span data-ttu-id="2c057-248">와 동일한 값 `$Home` 입니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-248">It's the same value as `$Home`.</span></span> <span data-ttu-id="2c057-249">자세한 내용은 [about_Automatic_Variables](about_Automatic_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2c057-249">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="2c057-250">속성을 사용 하 여 현재 세션에 대 한 공급자의 **홈** 디렉터리를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-250">You can set the **Home** directory for a provider, for the current session, using its property.</span></span>

```powershell
(Get-PSProvider FileSystem).Home = "C:\"
```

<span data-ttu-id="2c057-251">`~`문자를 사용 하 여 공급자의 홈 디렉터리를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-251">The `~` character can be used to represent the provider's home directory.</span></span>
<span data-ttu-id="2c057-252">공급자에 **홈** 위치가 설정 되어 있지 않으면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-252">If the provider doesn't have a **Home** location set, you see an error.</span></span>

```powershell
Cert:\> Set-Location ~
```

```Output
Set-Location : Home location for this provider isn't set. To set the home
location, call "(get-psprovider 'Certificate').Home = 'path'".
At line:1 char:1
+ Set-Location ~
+ ~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Set-Location],
                              PSInvalidOperationException
...
```

## <a name="finding-dynamic-parameters"></a><span data-ttu-id="2c057-253">동적 매개 변수 찾기</span><span class="sxs-lookup"><span data-stu-id="2c057-253">Finding dynamic parameters</span></span>

<span data-ttu-id="2c057-254">동적 매개 변수는 공급자가 cmdlet에 추가 하는 cmdlet 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-254">Dynamic parameters are cmdlet parameters that are added to a cmdlet by a provider.</span></span> <span data-ttu-id="2c057-255">이러한 매개 변수는 cmdlet이 추가 된 공급자와 함께 사용 되는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-255">These parameters are available only when the cmdlet is used with the provider that added them.</span></span>

<span data-ttu-id="2c057-256">예를 들어, `Cert:` 드라이브는 **Codesigningcert** 매개 변수를 및 cmdlet에 추가 합니다 `Get-Item` `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="2c057-256">For example, the `Cert:` drive adds the **CodeSigningCert** parameter to the `Get-Item` and `Get-ChildItem` cmdlets.</span></span> <span data-ttu-id="2c057-257">이 매개 변수는 `Get-Item` 드라이브에서 또는를 사용할 때만 사용할 수 있습니다 `Get-ChildItem` `Cert:` .</span><span class="sxs-lookup"><span data-stu-id="2c057-257">You can use this parameter only when you use `Get-Item` or `Get-ChildItem` in the `Cert:` drive.</span></span>

<span data-ttu-id="2c057-258">공급자가 지 원하는 동적 매개 변수의 목록은 공급자에 대 한 도움말 파일을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2c057-258">For a list of the dynamic parameters that a provider supports, see the Help file for the provider.</span></span> <span data-ttu-id="2c057-259">형식:</span><span class="sxs-lookup"><span data-stu-id="2c057-259">Type:</span></span>

```
Get-Help <provider-name>
```

<span data-ttu-id="2c057-260">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="2c057-260">For example:</span></span>

```powershell
Get-Help certificate
```

## <a name="learning-about-providers"></a><span data-ttu-id="2c057-261">공급자에 대해 알아보기</span><span class="sxs-lookup"><span data-stu-id="2c057-261">Learning about providers</span></span>

<span data-ttu-id="2c057-262">모든 공급자 데이터가 드라이브에 표시 되 고 동일한 방법을 사용 하 여 이동 하는 경우에도 유사성은 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-262">Although all provider data appears in drives and you use the same methods to move through them, the similarity stops there.</span></span> <span data-ttu-id="2c057-263">공급자가 제공 하는 데이터 저장소는 Active Directory 위치 및 Microsoft Exchange Server 사서함과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c057-263">The data stores that the provider exposes can be as varied as Active Directory locations and Microsoft Exchange Server mailboxes.</span></span>

<span data-ttu-id="2c057-264">개별 PowerShell 공급자에 대 한 자세한 내용을 보려면 다음을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2c057-264">For information about individual PowerShell providers, type:</span></span>

```
Get-Help <ProviderName>
```

<span data-ttu-id="2c057-265">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="2c057-265">For example:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="2c057-266">공급자에 대 한 도움말 항목 목록을 보려면 다음을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2c057-266">For a list of Help topics about the providers, type:</span></span>

```powershell
Get-Help * -Category Provider
```

## <a name="see-also"></a><span data-ttu-id="2c057-267">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c057-267">See also</span></span>

[<span data-ttu-id="2c057-268">about_Locations</span><span class="sxs-lookup"><span data-stu-id="2c057-268">about_Locations</span></span>](about_Locations.md)

[<span data-ttu-id="2c057-269">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="2c057-269">about_Path_Syntax</span></span>](about_Path_Syntax.md)
