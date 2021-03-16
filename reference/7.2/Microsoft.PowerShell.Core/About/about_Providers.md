---
description: PowerShell 공급자가 명령줄에서 다른 방법으로 쉽게 액세스할 수 없는 데이터 및 구성 요소에 대 한 액세스를 제공 하는 방법을 설명 합니다. 데이터는 파일 시스템 드라이브와 비슷한 일관 된 형식으로 제공 됩니다.
Locale: en-US
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_providers?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Providers
ms.openlocfilehash: 6073ef13a6d0a02cded69073d7ffaef903a807ea
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603068"
---
# <a name="about-providers"></a><span data-ttu-id="d75c5-104">공급자 정보</span><span class="sxs-lookup"><span data-stu-id="d75c5-104">About Providers</span></span>

## <a name="short-description"></a><span data-ttu-id="d75c5-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="d75c5-105">Short description</span></span>
<span data-ttu-id="d75c5-106">PowerShell 공급자가 명령줄에서 다른 방법으로 쉽게 액세스할 수 없는 데이터 및 구성 요소에 대 한 액세스를 제공 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-106">Describes how PowerShell providers provide access to data and components that wouldn't otherwise be easily accessible at the command line.</span></span>
<span data-ttu-id="d75c5-107">데이터는 파일 시스템 드라이브와 비슷한 일관 된 형식으로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-107">The data is presented in a consistent format that resembles a file system drive.</span></span>

## <a name="long-description"></a><span data-ttu-id="d75c5-108">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-108">Long description</span></span>

<span data-ttu-id="d75c5-109">PowerShell 공급자는 보기 및 관리를 용이 하 게 하는 특수 한 데이터 저장소에 대 한 액세스를 제공 하는 .NET 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-109">PowerShell providers are .NET programs that provide access to specialized data stores for easier viewing and management.</span></span> <span data-ttu-id="d75c5-110">데이터는 드라이브에 표시 되며 하드 디스크 드라이브와 같은 경로에 있는 데이터에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-110">The data appears in a drive, and you access the data in a path like you would on a hard disk drive.</span></span> <span data-ttu-id="d75c5-111">공급자가 지 원하는 기본 제공 cmdlet 중 하나를 사용 하 여 공급자 드라이브의 데이터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-111">You can use any of the built-in cmdlets that the provider supports to manage the data in the provider drive.</span></span> <span data-ttu-id="d75c5-112">데이터에 대해 특별히 디자인 된 사용자 지정 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-112">And, you can use custom cmdlets that are designed especially for the data.</span></span>

<span data-ttu-id="d75c5-113">공급자는 기본 제공 cmdlet에 동적 매개 변수를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-113">The providers can also add dynamic parameters to the built-in cmdlets.</span></span> <span data-ttu-id="d75c5-114">이러한 매개 변수는 공급자 데이터와 함께 cmdlet을 사용 하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-114">These parameters are only available when you use the cmdlet with the provider data.</span></span>

## <a name="built-in-providers"></a><span data-ttu-id="d75c5-115">기본 제공 공급자</span><span class="sxs-lookup"><span data-stu-id="d75c5-115">Built-in providers</span></span>

<span data-ttu-id="d75c5-116">PowerShell에는 다양 한 유형의 데이터 저장소에 액세스 하는 데 사용할 수 있는 기본 제공 공급자 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-116">PowerShell includes a set of built-in providers that you can use to access the different types of data stores.</span></span>

| <span data-ttu-id="d75c5-117">공급자</span><span class="sxs-lookup"><span data-stu-id="d75c5-117">Provider</span></span>   |   <span data-ttu-id="d75c5-118">개 드라이브</span><span class="sxs-lookup"><span data-stu-id="d75c5-118">Drive(s)</span></span>  |<span data-ttu-id="d75c5-119">OutputType</span><span class="sxs-lookup"><span data-stu-id="d75c5-119">OutputType</span></span>                                                    |
|----------- |------------ |--------------------------------------------------------------|
|<span data-ttu-id="d75c5-120">Alias</span><span class="sxs-lookup"><span data-stu-id="d75c5-120">Alias</span></span>       |<span data-ttu-id="d75c5-121">별칭:</span><span class="sxs-lookup"><span data-stu-id="d75c5-121">Alias:</span></span>       |<span data-ttu-id="d75c5-122">System.management.automation.aliasinfo.</span><span class="sxs-lookup"><span data-stu-id="d75c5-122">System.Management.Automation.AliasInfo</span></span>                        |
|<span data-ttu-id="d75c5-123">인증서</span><span class="sxs-lookup"><span data-stu-id="d75c5-123">Certificate</span></span> |<span data-ttu-id="d75c5-124">인증서:</span><span class="sxs-lookup"><span data-stu-id="d75c5-124">Cert:</span></span>        |<span data-ttu-id="d75c5-125">Microsoft.powershell.commands.x509storelocation.</span><span class="sxs-lookup"><span data-stu-id="d75c5-125">Microsoft.PowerShell.Commands.X509StoreLocation</span></span>               |
|            |             |<span data-ttu-id="d75c5-126">System.Security.Cryptography.X509Certificates.X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="d75c5-126">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>|
|<span data-ttu-id="d75c5-127">환경</span><span class="sxs-lookup"><span data-stu-id="d75c5-127">Environment</span></span> |<span data-ttu-id="d75c5-128">Env:</span><span class="sxs-lookup"><span data-stu-id="d75c5-128">Env:</span></span>         |<span data-ttu-id="d75c5-129">DictionaryEntry</span><span class="sxs-lookup"><span data-stu-id="d75c5-129">System.Collections.DictionaryEntry</span></span>                            |
|<span data-ttu-id="d75c5-130">FileSystem</span><span class="sxs-lookup"><span data-stu-id="d75c5-130">FileSystem</span></span>  |<span data-ttu-id="d75c5-131">C: (\*)</span><span class="sxs-lookup"><span data-stu-id="d75c5-131">C: (\*)</span></span>       |<span data-ttu-id="d75c5-132">System.object</span><span class="sxs-lookup"><span data-stu-id="d75c5-132">System.IO.FileInfo</span></span>                                            |
|            |             |<span data-ttu-id="d75c5-133">System.io.directoryinfo</span><span class="sxs-lookup"><span data-stu-id="d75c5-133">System.IO.DirectoryInfo</span></span>                                       |
|<span data-ttu-id="d75c5-134">함수</span><span class="sxs-lookup"><span data-stu-id="d75c5-134">Function</span></span>    |<span data-ttu-id="d75c5-135">함수:</span><span class="sxs-lookup"><span data-stu-id="d75c5-135">Function:</span></span>    |<span data-ttu-id="d75c5-136">System.object를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-136">System.Management.Automation.FunctionInfo</span></span>                     |
|<span data-ttu-id="d75c5-137">레지스트리</span><span class="sxs-lookup"><span data-stu-id="d75c5-137">Registry</span></span>    |<span data-ttu-id="d75c5-138">HKLM: HKCU:</span><span class="sxs-lookup"><span data-stu-id="d75c5-138">HKLM: HKCU:</span></span>  |<span data-ttu-id="d75c5-139">Microsoft Win32 RegistryKey</span><span class="sxs-lookup"><span data-stu-id="d75c5-139">Microsoft.Win32.RegistryKey</span></span>                                   |
|<span data-ttu-id="d75c5-140">변수</span><span class="sxs-lookup"><span data-stu-id="d75c5-140">Variable</span></span>    |<span data-ttu-id="d75c5-141">변수:</span><span class="sxs-lookup"><span data-stu-id="d75c5-141">Variable:</span></span>    |<span data-ttu-id="d75c5-142">System.object입니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-142">System.Management.Automation.PSVariable</span></span>                       |
|<span data-ttu-id="d75c5-143">WSMan</span><span class="sxs-lookup"><span data-stu-id="d75c5-143">WSMan</span></span>       |<span data-ttu-id="d75c5-144">WSMan:</span><span class="sxs-lookup"><span data-stu-id="d75c5-144">WSMan:</span></span>       |<span data-ttu-id="d75c5-145">에서 wsmanconfigcontainerelement가.</span><span class="sxs-lookup"><span data-stu-id="d75c5-145">Microsoft.WSMan.Management.WSManConfigContainerElement</span></span>        |

<span data-ttu-id="d75c5-146">(\*) 파일 시스템 드라이브는 각 시스템 마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-146">(\*) The FileSystem drives vary on each system.</span></span>

<span data-ttu-id="d75c5-147">사용자 고유의 PowerShell 공급자를 만들 수도 있으며, 다른 사용자가 개발 하는 공급자를 설치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-147">You can also create your own PowerShell providers, and you can install providers that others develop.</span></span> <span data-ttu-id="d75c5-148">세션에서 사용할 수 있는 공급자를 나열 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-148">To list the providers that are available in your session, type:</span></span>

```powershell
Get-PSProvider
```

## <a name="installing-and-removing-providers"></a><span data-ttu-id="d75c5-149">공급자 설치 및 제거</span><span class="sxs-lookup"><span data-stu-id="d75c5-149">Installing and removing providers</span></span>

<span data-ttu-id="d75c5-150">공급자는 일반적으로 PowerShell 모듈을 통해 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-150">Providers are typically installed via PowerShell modules.</span></span> <span data-ttu-id="d75c5-151">모듈을 가져오면 해당 공급자가 세션으로 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-151">Importing the module loads the provider into your session.</span></span> <span data-ttu-id="d75c5-152">기본 제공 공급자를 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-152">You can't uninstall the built-in providers.</span></span> <span data-ttu-id="d75c5-153">다른 모듈에 의해 로드 된 공급자를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-153">You can uninstall providers loaded by other modules.</span></span>

<span data-ttu-id="d75c5-154">Cmdlet을 사용 하 여 현재 세션에서 공급자를 언로드할 수 있습니다 `Remove-Module` .</span><span class="sxs-lookup"><span data-stu-id="d75c5-154">You can unload a provider from the current session using the `Remove-Module` cmdlet.</span></span> <span data-ttu-id="d75c5-155">이 cmdlet은 공급자를 제거 하지 않지만 해당 공급자를 세션에서 사용할 수 없게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-155">This cmdlet doesn't uninstall the provider, but it makes the provider unavailable in the session.</span></span>

<span data-ttu-id="d75c5-156">Cmdlet을 사용 하 여 `Remove-PSDrive` 현재 세션에서 드라이브를 제거할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-156">You can also use the `Remove-PSDrive` cmdlet to remove any drive from the current session.</span></span> <span data-ttu-id="d75c5-157">드라이브의이 데이터는 영향을 받지 않지만 해당 세션에서 더 이상 드라이브를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-157">This data on the drive isn't affected, but the drive is no longer available in that session.</span></span>

## <a name="viewing-providers"></a><span data-ttu-id="d75c5-158">공급자 보기</span><span class="sxs-lookup"><span data-stu-id="d75c5-158">Viewing providers</span></span>

<span data-ttu-id="d75c5-159">컴퓨터에서 PowerShell 공급자를 보려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-159">To view the PowerShell providers on your computer, type:</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="d75c5-160">출력에는 기본 제공 공급자와 세션에 추가한 공급자가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-160">The output lists the built-in providers and the providers that you added to the session.</span></span>

## <a name="the-provider-cmdlets"></a><span data-ttu-id="d75c5-161">공급자 cmdlet</span><span class="sxs-lookup"><span data-stu-id="d75c5-161">The provider cmdlets</span></span>

<span data-ttu-id="d75c5-162">다음 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-162">The following cmdlets are designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="d75c5-163">동일한 방식으로 동일한 cmdlet을 사용 하 여 공급자가 노출 하는 다양 한 데이터 형식을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-163">You can use the same cmdlets in the same way to manage the different types of data that providers expose.</span></span> <span data-ttu-id="d75c5-164">한 공급자의 데이터를 관리 하는 방법을 학습 한 후에는 모든 공급자의 데이터와 동일한 절차를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-164">After you learn to manage the data of one provider, you can use the same procedures with the data from any provider.</span></span>

<span data-ttu-id="d75c5-165">예를 들어 `New-Item` cmdlet은 새 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-165">For example, the `New-Item` cmdlet creates a new item.</span></span> <span data-ttu-id="d75c5-166">`C:` **FileSystem** 공급자가 지 원하는 드라이브에서를 사용 `New-Item` 하 여 새 파일이 나 폴더를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-166">In the `C:` drive that is supported by the **FileSystem** provider, you can use `New-Item` to create a new file or folder.</span></span> <span data-ttu-id="d75c5-167">**레지스트리** 공급자가 지 원하는 드라이브에서를 사용 `New-Item` 하 여 새 레지스트리 키를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-167">In the drives that are supported by the **Registry** provider, you can use `New-Item` to create a new registry key.</span></span> <span data-ttu-id="d75c5-168">드라이브에서를 `Alias:` 사용 `New-Item` 하 여 새 별칭을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-168">In the `Alias:` drive, you can use `New-Item` to create a new alias.</span></span>

<span data-ttu-id="d75c5-169">다음 cmdlet에 대 한 자세한 내용을 보려면 다음을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d75c5-169">For detailed information about any of the following cmdlets, type:</span></span>

```
Get-Help <cmdlet-name> -Detailed
```

### <a name="childitem-cmdlets"></a><span data-ttu-id="d75c5-170">ChildItem cmdlet</span><span class="sxs-lookup"><span data-stu-id="d75c5-170">ChildItem cmdlets</span></span>

- [<span data-ttu-id="d75c5-171">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="d75c5-171">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="content-cmdlets"></a><span data-ttu-id="d75c5-172">콘텐츠 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d75c5-172">Content Cmdlets</span></span>

- [<span data-ttu-id="d75c5-173">Add-Content</span><span class="sxs-lookup"><span data-stu-id="d75c5-173">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="d75c5-174">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="d75c5-174">Clear-Content</span></span>](xref:Microsoft.PowerShell.Management.Clear-Content)
- [<span data-ttu-id="d75c5-175">Get-Content</span><span class="sxs-lookup"><span data-stu-id="d75c5-175">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="d75c5-176">Set-Content</span><span class="sxs-lookup"><span data-stu-id="d75c5-176">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="item-cmdlets"></a><span data-ttu-id="d75c5-177">항목 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d75c5-177">Item Cmdlets</span></span>

- [<span data-ttu-id="d75c5-178">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="d75c5-178">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="d75c5-179">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="d75c5-179">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="d75c5-180">Get-Item</span><span class="sxs-lookup"><span data-stu-id="d75c5-180">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="d75c5-181">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="d75c5-181">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="d75c5-182">Move-Item</span><span class="sxs-lookup"><span data-stu-id="d75c5-182">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="d75c5-183">New-Item</span><span class="sxs-lookup"><span data-stu-id="d75c5-183">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="d75c5-184">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="d75c5-184">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="d75c5-185">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="d75c5-185">Rename-Item</span></span>](xref:Microsoft.PowerShell.Management.Rename-Item)
- [<span data-ttu-id="d75c5-186">Set-Item</span><span class="sxs-lookup"><span data-stu-id="d75c5-186">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

### <a name="itemproperty-cmdlets"></a><span data-ttu-id="d75c5-187">Get-itemproperty cmdlet</span><span class="sxs-lookup"><span data-stu-id="d75c5-187">ItemProperty cmdlets</span></span>

- [<span data-ttu-id="d75c5-188">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d75c5-188">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="d75c5-189">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d75c5-189">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)
- [<span data-ttu-id="d75c5-190">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d75c5-190">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="d75c5-191">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d75c5-191">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)
- [<span data-ttu-id="d75c5-192">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d75c5-192">New-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.New-ItemProperty)
- [<span data-ttu-id="d75c5-193">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d75c5-193">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="d75c5-194">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d75c5-194">Rename-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Rename-ItemProperty)
- [<span data-ttu-id="d75c5-195">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="d75c5-195">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

### <a name="location-cmdlets"></a><span data-ttu-id="d75c5-196">위치 cmdlet</span><span class="sxs-lookup"><span data-stu-id="d75c5-196">Location cmdlets</span></span>

- [<span data-ttu-id="d75c5-197">Get-Location</span><span class="sxs-lookup"><span data-stu-id="d75c5-197">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="d75c5-198">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="d75c5-198">Pop-Location</span></span>](xref:Microsoft.PowerShell.Management.Pop-Location)
- [<span data-ttu-id="d75c5-199">Push-Location</span><span class="sxs-lookup"><span data-stu-id="d75c5-199">Push-Location</span></span>](xref:Microsoft.PowerShell.Management.Push-Location)
- [<span data-ttu-id="d75c5-200">Set-Location</span><span class="sxs-lookup"><span data-stu-id="d75c5-200">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)

### <a name="path-cmdlets"></a><span data-ttu-id="d75c5-201">경로 cmdlet</span><span class="sxs-lookup"><span data-stu-id="d75c5-201">Path cmdlets</span></span>

- [<span data-ttu-id="d75c5-202">Join-Path</span><span class="sxs-lookup"><span data-stu-id="d75c5-202">Join-Path</span></span>](xref:Microsoft.PowerShell.Management.Join-Path)
- [<span data-ttu-id="d75c5-203">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="d75c5-203">Convert-Path</span></span>](xref:Microsoft.PowerShell.Management.Convert-Path)
- [<span data-ttu-id="d75c5-204">Split-Path</span><span class="sxs-lookup"><span data-stu-id="d75c5-204">Split-Path</span></span>](xref:Microsoft.PowerShell.Management.Split-Path)
- [<span data-ttu-id="d75c5-205">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="d75c5-205">Resolve-Path</span></span>](xref:Microsoft.PowerShell.Management.Resolve-Path)
- [<span data-ttu-id="d75c5-206">Test-Path</span><span class="sxs-lookup"><span data-stu-id="d75c5-206">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="psdrive-cmdlets"></a><span data-ttu-id="d75c5-207">PSDrive cmdlet</span><span class="sxs-lookup"><span data-stu-id="d75c5-207">PSDrive cmdlets</span></span>

- [<span data-ttu-id="d75c5-208">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="d75c5-208">Get-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [<span data-ttu-id="d75c5-209">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="d75c5-209">New-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.New-PSDrive)
- [<span data-ttu-id="d75c5-210">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="d75c5-210">Remove-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Remove-PSDrive)

### <a name="psprovider-cmdlets"></a><span data-ttu-id="d75c5-211">PSProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d75c5-211">PSProvider Cmdlets</span></span>

- [<span data-ttu-id="d75c5-212">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="d75c5-212">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)

## <a name="viewing-provider-data"></a><span data-ttu-id="d75c5-213">공급자 데이터 보기</span><span class="sxs-lookup"><span data-stu-id="d75c5-213">Viewing provider data</span></span>

<span data-ttu-id="d75c5-214">공급자의 주요 장점은 친숙 하 고 일관 된 방식으로 데이터를 노출 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-214">The primary benefit of a provider is that it exposes its data in a familiar and consistent way.</span></span> <span data-ttu-id="d75c5-215">데이터 프레젠테이션용 모델은 파일 시스템 드라이브입니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-215">The model for data presentation is a file system drive.</span></span>

<span data-ttu-id="d75c5-216">공급자를 사용 하면 파일 시스템의 데이터와 동일한 방법으로 데이터 저장소의 항목을 보고, 탐색 하 고, 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-216">The provider allows you to view, navigate, and change items in the data store as though they were data in a file system.</span></span> <span data-ttu-id="d75c5-217">데이터 저장소는 지원 되는 드라이브의 이름을 통해 액세스 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-217">The data store is accessed by the name of the drive that it supports.</span></span>

<span data-ttu-id="d75c5-218">Cmdlet의 기본 표시에 드라이브가 나열 `Get-PSProvider` 되지만 cmdlet을 사용 하 여 공급자 드라이브에 대 한 정보를 가져올 수 있습니다 `Get-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="d75c5-218">The drive is listed in the default display of the `Get-PSProvider` cmdlet, but you can get information about the provider drive using the `Get-PSDrive` cmdlet.</span></span> <span data-ttu-id="d75c5-219">예를 들어 Function: drive의 모든 속성을 가져오려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-219">For example, to get all the properties of the Function: drive, type:</span></span>

```powershell
Get-PSDrive Function | Format-List *
```

<span data-ttu-id="d75c5-220">파일 시스템 드라이브에 있는 것 처럼 공급자 드라이브의 데이터를 확인 하 고 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-220">You can view and move through the data in a provider drive just as you would on a file system drive.</span></span>

<span data-ttu-id="d75c5-221">공급자 드라이브의 내용을 보려면 Get-Item 또는 Get-ChildItem cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-221">To view the contents of a provider drive, use the Get-Item or Get-ChildItem cmdlets.</span></span> <span data-ttu-id="d75c5-222">드라이브 이름 뒤에 콜론 (:)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-222">Type the drive name followed by a colon (:).</span></span> <span data-ttu-id="d75c5-223">예를 들어 Alias: 드라이브의 내용을 보려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-223">For example, to view the contents of the Alias: drive, type:</span></span>

```powershell
Get-Item alias:
```

<span data-ttu-id="d75c5-224">경로에 드라이브 이름을 포함 하 여 다른 드라이브의 모든 드라이브에서 데이터를 보고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-224">You can view and manage the data in any drive from another drive by including the drive name in the path.</span></span> <span data-ttu-id="d75c5-225">예를 들어 다른 드라이브의 HKLM: 드라이브에서 HKLM\Software 레지스트리 키를 보려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-225">For example, to view the HKLM\Software registry key in the HKLM: drive from another drive, type:</span></span>

```powershell
Get-ChildItem HKLM:\SOFTWARE\
```

<span data-ttu-id="d75c5-226">드라이브를 열려면 Set-Location cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-226">To open the drive, use the Set-Location cmdlet.</span></span> <span data-ttu-id="d75c5-227">드라이브 경로를 지정할 때는 콜론을 명심 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d75c5-227">Remember the colon when you specify the drive path.</span></span> <span data-ttu-id="d75c5-228">예를 들어, 위치를 Cert: 드라이브의 루트 디렉터리로 변경 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-228">For example, to change your location to the root directory of the Cert: drive, type:</span></span>

```powershell
Set-Location cert:
```

<span data-ttu-id="d75c5-229">그런 다음, Cert: 드라이브의 내용을 보려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-229">Then, to view the contents of the Cert: drive, type:</span></span>

```powershell
Get-ChildItem
```

## <a name="moving-through-hierarchical-data"></a><span data-ttu-id="d75c5-230">계층적 데이터 이동</span><span class="sxs-lookup"><span data-stu-id="d75c5-230">Moving through hierarchical data</span></span>

<span data-ttu-id="d75c5-231">하드 디스크 드라이브와 마찬가지로 공급자 드라이브를 통해 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-231">You can move through a provider drive just as you would a hard disk drive.</span></span>
<span data-ttu-id="d75c5-232">데이터가 항목 내 항목의 계층 구조에 정렬 되어 있는 경우 백슬래시 ()를 사용 `\` 하 여 자식 항목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-232">If the data is arranged in a hierarchy of items within items, use a backslash (`\`) to indicate a child item.</span></span> <span data-ttu-id="d75c5-233">이때 다음 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-233">Use the following format:</span></span>

```
drive:\location\child-location\...
```

<span data-ttu-id="d75c5-234">예를 들어 HKLM\Software 레지스트리 키에 대 한 위치를 변경 하려면 다음과 같은 Set-Location 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-234">For example, to change your location to the HKLM\Software registry key, type a Set-Location command, such as:</span></span>

```powershell
Set-Location HKLM:\SOFTWARE\
```

<span data-ttu-id="d75c5-235">정규화 된 이름의 요소에 공백이 포함 된 경우 이름을 큰따옴표 ()로 묶어야 합니다 `"` .</span><span class="sxs-lookup"><span data-stu-id="d75c5-235">If any element in the fully qualified name includes spaces, you must enclose the name in double-quotation marks (`"`).</span></span> <span data-ttu-id="d75c5-236">다음 예에서는 공백이 포함 된 정규화 된 경로를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-236">The following example shows a fully qualified path that includes spaces.</span></span>

```
"C:\Program Files\Internet Explorer\iexplore.exe"
```

<span data-ttu-id="d75c5-237">위치에 대 한 상대 참조를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-237">You can also use relative references to locations.</span></span> <span data-ttu-id="d75c5-238">점 ( `.` )은 현재 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-238">A dot (`.`) represents the current location.</span></span> <span data-ttu-id="d75c5-239">예를 들어 레지스트리 키에 있는 경우 `HKLM:\Software\Microsoft` 키에 레지스트리 하위 키를 나열 하려면 `HKLM:\Software\Microsoft\PowerShell` 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-239">For example, if you are in the `HKLM:\Software\Microsoft` registry key, and you want to list the registry subkeys in the `HKLM:\Software\Microsoft\PowerShell` key, type the following command:</span></span>

```powershell
Get-ChildItem .\PowerShell
```

<span data-ttu-id="d75c5-240">또한 이중 점 ( `..` )은 현재 위치 바로 위의 디렉터리나 컨테이너를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-240">Also, double-dots (`..`) refers to the directory or container directly above your current location.</span></span> <span data-ttu-id="d75c5-241">이중 점 ( `..` )을 사용 하 여 공급자 계층 구조를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-241">You can use double-dots (`..`) to navigate through a provider hierarchy.</span></span>

```
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\> cd ..\..\LanmanWorkstation\Parameters
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters>
```

## <a name="provider-home"></a><span data-ttu-id="d75c5-242">공급자 홈</span><span class="sxs-lookup"><span data-stu-id="d75c5-242">Provider Home</span></span>

<span data-ttu-id="d75c5-243">공급자에는 또한 **홈** 위치가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-243">Providers also have a **Home** location.</span></span>  <span data-ttu-id="d75c5-244">이 위치는 공급자가 지 원하는 모든에서 공유 `PSDrives` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-244">This location is shared by all `PSDrives` backed by the provider.</span></span> <span data-ttu-id="d75c5-245">공급자의 **Home** 속성을 확인 하 여 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-245">It can be retrieved by viewing the **Home** property of the provider.</span></span>

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

<span data-ttu-id="d75c5-246">**FileSystem** 공급자는 **홈** 에 대 한 기본값을 가진 유일한 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-246">The **FileSystem** provider is the only provider that has a default value for **Home**.</span></span> <span data-ttu-id="d75c5-247">와 동일한 값 `$Home` 입니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-247">It's the same value as `$Home`.</span></span> <span data-ttu-id="d75c5-248">자세한 내용은 [about_Automatic_Variables](about_Automatic_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d75c5-248">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="d75c5-249">속성을 사용 하 여 현재 세션에 대 한 공급자의 **홈** 디렉터리를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-249">You can set the **Home** directory for a provider, for the current session, using its property.</span></span>

```powershell
(Get-PSProvider FileSystem).Home = "C:\"
```

<span data-ttu-id="d75c5-250">`~`문자를 사용 하 여 공급자의 홈 디렉터리를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-250">The `~` character can be used to represent the provider's home directory.</span></span>
<span data-ttu-id="d75c5-251">공급자에 **홈** 위치가 설정 되어 있지 않으면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-251">If the provider doesn't have a **Home** location set, you see an error.</span></span>

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

## <a name="finding-dynamic-parameters"></a><span data-ttu-id="d75c5-252">동적 매개 변수 찾기</span><span class="sxs-lookup"><span data-stu-id="d75c5-252">Finding dynamic parameters</span></span>

<span data-ttu-id="d75c5-253">동적 매개 변수는 공급자가 cmdlet에 추가 하는 cmdlet 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-253">Dynamic parameters are cmdlet parameters that are added to a cmdlet by a provider.</span></span> <span data-ttu-id="d75c5-254">이러한 매개 변수는 cmdlet이 추가 된 공급자와 함께 사용 되는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-254">These parameters are available only when the cmdlet is used with the provider that added them.</span></span>

<span data-ttu-id="d75c5-255">예를 들어, `Cert:` 드라이브는 **Codesigningcert** 매개 변수를 및 cmdlet에 추가 합니다 `Get-Item` `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="d75c5-255">For example, the `Cert:` drive adds the **CodeSigningCert** parameter to the `Get-Item` and `Get-ChildItem` cmdlets.</span></span> <span data-ttu-id="d75c5-256">이 매개 변수는 `Get-Item` 드라이브에서 또는를 사용할 때만 사용할 수 있습니다 `Get-ChildItem` `Cert:` .</span><span class="sxs-lookup"><span data-stu-id="d75c5-256">You can use this parameter only when you use `Get-Item` or `Get-ChildItem` in the `Cert:` drive.</span></span>

<span data-ttu-id="d75c5-257">공급자가 지 원하는 동적 매개 변수의 목록은 공급자에 대 한 도움말 파일을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d75c5-257">For a list of the dynamic parameters that a provider supports, see the Help file for the provider.</span></span> <span data-ttu-id="d75c5-258">유형:</span><span class="sxs-lookup"><span data-stu-id="d75c5-258">Type:</span></span>

```
Get-Help <provider-name>
```

<span data-ttu-id="d75c5-259">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="d75c5-259">For example:</span></span>

```powershell
Get-Help certificate
```

## <a name="learning-about-providers"></a><span data-ttu-id="d75c5-260">공급자에 대해 알아보기</span><span class="sxs-lookup"><span data-stu-id="d75c5-260">Learning about providers</span></span>

<span data-ttu-id="d75c5-261">모든 공급자 데이터가 드라이브에 표시 되 고 동일한 방법을 사용 하 여 이동 하는 경우에도 유사성은 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-261">Although all provider data appears in drives and you use the same methods to move through them, the similarity stops there.</span></span> <span data-ttu-id="d75c5-262">공급자가 제공 하는 데이터 저장소는 Active Directory 위치 및 Microsoft Exchange Server 사서함과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75c5-262">The data stores that the provider exposes can be as varied as Active Directory locations and Microsoft Exchange Server mailboxes.</span></span>

<span data-ttu-id="d75c5-263">개별 PowerShell 공급자에 대 한 자세한 내용을 보려면 다음을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d75c5-263">For information about individual PowerShell providers, type:</span></span>

```
Get-Help <ProviderName>
```

<span data-ttu-id="d75c5-264">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="d75c5-264">For example:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="d75c5-265">공급자에 대 한 도움말 항목 목록을 보려면 다음을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d75c5-265">For a list of Help topics about the providers, type:</span></span>

```powershell
Get-Help * -Category Provider
```

## <a name="see-also"></a><span data-ttu-id="d75c5-266">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d75c5-266">See also</span></span>

[<span data-ttu-id="d75c5-267">about_Locations</span><span class="sxs-lookup"><span data-stu-id="d75c5-267">about_Locations</span></span>](about_Locations.md)

[<span data-ttu-id="d75c5-268">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="d75c5-268">about_Path_Syntax</span></span>](about_Path_Syntax.md)
