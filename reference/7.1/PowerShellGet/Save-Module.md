---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Module
ms.openlocfilehash: 88ce556a366e67a911bf32eb5c13161a543f103f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215641"
---
# <span data-ttu-id="68e18-103">Save-Module</span><span class="sxs-lookup"><span data-stu-id="68e18-103">Save-Module</span></span>

## <span data-ttu-id="68e18-104">개요</span><span class="sxs-lookup"><span data-stu-id="68e18-104">SYNOPSIS</span></span>
<span data-ttu-id="68e18-105">모듈 및 해당 종속성을 로컬 컴퓨터에 저장 하지만 모듈을 설치 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-105">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

## <span data-ttu-id="68e18-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="68e18-106">SYNTAX</span></span>

### <span data-ttu-id="68e18-107">NameAndPathParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="68e18-107">NameAndPathParameterSet (Default)</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="68e18-108">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="68e18-108">NameAndLiteralPathParameterSet</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="68e18-109">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="68e18-109">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="68e18-110">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="68e18-110">InputObjectAndPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="68e18-111">설명</span><span class="sxs-lookup"><span data-stu-id="68e18-111">DESCRIPTION</span></span>

<span data-ttu-id="68e18-112">`Save-Module`Cmdlet은 모듈 및 등록 된 리포지토리에서 모든 종속성을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-112">The `Save-Module` cmdlet downloads a module and any dependencies from a registered repository.</span></span>
<span data-ttu-id="68e18-113">`Save-Module` 최신 버전의 모듈을 다운로드 하 여 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-113">`Save-Module` downloads and saves the most current version of a module.</span></span> <span data-ttu-id="68e18-114">파일은 로컬 컴퓨터의 지정 된 경로에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-114">The files are saved to a specified path on the local computer.</span></span> <span data-ttu-id="68e18-115">모듈이 설치 되지 않았지만 관리자가 콘텐츠를 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-115">The module isn't installed, but the contents are available for inspection by an administrator.</span></span> <span data-ttu-id="68e18-116">그런 다음 저장 된 모듈을 `$env:PSModulePath` 오프 라인 컴퓨터의 적절 한 위치에 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-116">The saved module can then be copied into the appropriate `$env:PSModulePath` location of the offline machine.</span></span>

<span data-ttu-id="68e18-117">`Get-PSRepository` 로컬 컴퓨터의 등록 된 리포지토리를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-117">`Get-PSRepository` displays the local computer's registered repositories.</span></span> <span data-ttu-id="68e18-118">Cmdlet을 사용 `Find-Module` 하 여 등록 된 리포지토리를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-118">You can use the `Find-Module` cmdlet to search registered repositories.</span></span>

## <span data-ttu-id="68e18-119">예제</span><span class="sxs-lookup"><span data-stu-id="68e18-119">EXAMPLES</span></span>

### <span data-ttu-id="68e18-120">예제 1: 모듈 저장</span><span class="sxs-lookup"><span data-stu-id="68e18-120">Example 1: Save a module</span></span>

<span data-ttu-id="68e18-121">이 예제에서는 모듈 및 해당 종속성이 로컬 컴퓨터에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-121">In this example, a module and its dependencies are saved to the local computer.</span></span>

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery
Get-ChildItem -Path C:\Test\Modules
```

```Output
    Directory: C:\Test\Modules

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:31                PackageManagement
d-----         7/1/2019     13:31                PowerShellGet
```

<span data-ttu-id="68e18-122">`Save-Module`**Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-122">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet** .</span></span> <span data-ttu-id="68e18-123">**Path** 매개 변수는 다운로드 한 모듈을 저장할 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-123">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="68e18-124">**리포지토리** 매개 변수는 등록 된 리포지토리 **PSGallery** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-124">The **Repository** parameter specifies a registered repository, **PSGallery** .</span></span> <span data-ttu-id="68e18-125">다운로드가 완료 되 면는 `Get-ChildItem` 파일이 저장 된 **경로** 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-125">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="68e18-126">예제 2: 모듈의 특정 버전 저장</span><span class="sxs-lookup"><span data-stu-id="68e18-126">Example 2: Save a specific version of a module</span></span>

<span data-ttu-id="68e18-127">이 예에서는 **MaximumVersion** 또는 **RequiredVersion** 과 같은 매개 변수를 사용 하 여 모듈 버전을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-127">This example shows how to use a parameter such as **MaximumVersion** , or **RequiredVersion** to specify a module version.</span></span>

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery -MaximumVersion 2.1.0
Get-ChildItem -Path C:\Test\Modules\PowerShellGet\
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:40                2.1.0
```

<span data-ttu-id="68e18-128">`Save-Module`**Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-128">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet** .</span></span> <span data-ttu-id="68e18-129">**Path** 매개 변수는 다운로드 한 모듈을 저장할 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-129">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="68e18-130">**리포지토리** 매개 변수는 등록 된 리포지토리 **PSGallery** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-130">The **Repository** parameter specifies a registered repository, **PSGallery** .</span></span> <span data-ttu-id="68e18-131">**MaximumVersion** 은 버전 **2.1.0** 을 다운로드 하 여 저장 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-131">**MaximumVersion** specifies that version **2.1.0** is downloaded and saved.</span></span> <span data-ttu-id="68e18-132">다운로드가 완료 되 면는 `Get-ChildItem` 파일이 저장 된 **경로** 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-132">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="68e18-133">예제 3: 모듈의 특정 버전 찾기 및 저장</span><span class="sxs-lookup"><span data-stu-id="68e18-133">Example 3: Find and save a specific version of a module</span></span>

<span data-ttu-id="68e18-134">이 예제에서는 필수 모듈 버전이 리포지토리에서 검색 되 고 로컬 컴퓨터에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-134">In this example, a required module version is found in the repository and saved to the local computer.</span></span>

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery -RequiredVersion 1.6.5 |
  Save-Module -Path C:\Test\Modules
Get-ChildItem -Path C:\Test\Modules\PowerShellGet
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     14:04                1.6.5
```

<span data-ttu-id="68e18-135">`Find-Module`**Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-135">`Find-Module` uses the **Name** parameter to specify the module, **PowerShellGet** .</span></span> <span data-ttu-id="68e18-136">**리포지토리** 매개 변수는 등록 된 리포지토리 **PSGallery** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-136">The **Repository** parameter specifies a registered repository, **PSGallery** .</span></span> <span data-ttu-id="68e18-137">**RequiredVersion** 버전 **1.6.5** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-137">**RequiredVersion** specifies version **1.6.5** .</span></span>

<span data-ttu-id="68e18-138">개체는 파이프라인에서로 전송 됩니다 `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="68e18-138">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="68e18-139">**Path** 매개 변수는 다운로드 한 모듈을 저장할 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-139">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="68e18-140">다운로드가 완료 되 면는 `Get-ChildItem` 파일이 저장 된 **경로** 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-140">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

## <span data-ttu-id="68e18-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="68e18-141">PARAMETERS</span></span>

### <span data-ttu-id="68e18-142">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="68e18-142">-AcceptLicense</span></span>

<span data-ttu-id="68e18-143">패키지에 필요한 경우 사용권 계약에 자동으로 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-143">Automatically accept the license agreement if the package requires it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="68e18-144">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="68e18-144">-AllowPrerelease</span></span>

<span data-ttu-id="68e18-145">시험판으로 표시 된 모듈을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-145">Allows you to save a module marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="68e18-146">-Confirm</span><span class="sxs-lookup"><span data-stu-id="68e18-146">-Confirm</span></span>

<span data-ttu-id="68e18-147">을 실행 하기 전에 확인 메시지를 표시 `Save-Module` 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-147">Prompts you for confirmation before running the `Save-Module`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="68e18-148">-Credential</span><span class="sxs-lookup"><span data-stu-id="68e18-148">-Credential</span></span>

<span data-ttu-id="68e18-149">모듈을 저장할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-149">Specifies a user account that has rights to save a module.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68e18-150">-Force</span><span class="sxs-lookup"><span data-stu-id="68e18-150">-Force</span></span>

<span data-ttu-id="68e18-151">`Save-Module`사용자 확인을 요청 하지 않고 강제로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-151">Forces `Save-Module` to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="68e18-152">-InputObject</span><span class="sxs-lookup"><span data-stu-id="68e18-152">-InputObject</span></span>

<span data-ttu-id="68e18-153">**PSRepositoryItemInfo** 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-153">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="68e18-154">예를 들어 `Find-Module` 변수를 출력 하 고 해당 변수를 **InputObject** 인수로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-154">For example, output `Find-Module` to a variable and use that variable as the **InputObject** argument.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObjectAndLiteralPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="68e18-155">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="68e18-155">-LiteralPath</span></span>

<span data-ttu-id="68e18-156">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-156">Specifies a path to one or more locations.</span></span> <span data-ttu-id="68e18-157">**LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-157">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="68e18-158">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-158">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="68e18-159">경로에 이스케이프 문자가 포함 되어 있으면 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-159">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="68e18-160">PowerShell은 작은 따옴표로 묶인 문자를 이스케이프 시퀀스로 해석 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-160">PowerShell does not interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndLiteralPathParameterSet, InputObjectAndLiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68e18-161">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="68e18-161">-MaximumVersion</span></span>

<span data-ttu-id="68e18-162">저장할 모듈의 최대 또는 최신 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-162">Specifies the maximum, or newest, version of the module to save.</span></span> <span data-ttu-id="68e18-163">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-163">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68e18-164">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="68e18-164">-MinimumVersion</span></span>

<span data-ttu-id="68e18-165">저장할 단일 모듈의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-165">Specifies the minimum version of a single module to save.</span></span> <span data-ttu-id="68e18-166">여러 모듈을 설치 하려는 경우에는이 매개 변수를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-166">You cannot add this parameter if you are attempting to install multiple modules.</span></span> <span data-ttu-id="68e18-167">**MinimumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-167">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68e18-168">-Name</span><span class="sxs-lookup"><span data-stu-id="68e18-168">-Name</span></span>

<span data-ttu-id="68e18-169">저장할 모듈의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-169">Specifies an array of names of modules to save.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68e18-170">-Path</span><span class="sxs-lookup"><span data-stu-id="68e18-170">-Path</span></span>

<span data-ttu-id="68e18-171">저장 된 모듈을 저장할 로컬 컴퓨터의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-171">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="68e18-172">와일드 카드 문자를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-172">Accepts wildcard characters.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="68e18-173">-프록시</span><span class="sxs-lookup"><span data-stu-id="68e18-173">-Proxy</span></span>

<span data-ttu-id="68e18-174">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-174">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68e18-175">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="68e18-175">-ProxyCredential</span></span>

<span data-ttu-id="68e18-176">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-176">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68e18-177">-리포지토리</span><span class="sxs-lookup"><span data-stu-id="68e18-177">-Repository</span></span>

<span data-ttu-id="68e18-178">을 실행 하 여 등록 된 리포지토리의 이름을 지정 합니다 `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="68e18-178">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="68e18-179">`Get-PSRepository`등록 된 리포지토리를 표시 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-179">Use `Get-PSRepository` to display registered repositories.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68e18-180">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="68e18-180">-RequiredVersion</span></span>

<span data-ttu-id="68e18-181">저장할 모듈의 정확한 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-181">Specifies the exact version number of the module to save.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68e18-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="68e18-182">-WhatIf</span></span>

<span data-ttu-id="68e18-183">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="68e18-183">Shows what would happen if the `Save-Module` runs.</span></span> <span data-ttu-id="68e18-184">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="68e18-184">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="68e18-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="68e18-185">CommonParameters</span></span>

<span data-ttu-id="68e18-186">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="68e18-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="68e18-187">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="68e18-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="68e18-188">입력</span><span class="sxs-lookup"><span data-stu-id="68e18-188">INPUTS</span></span>

### <span data-ttu-id="68e18-189">System.String[]</span><span class="sxs-lookup"><span data-stu-id="68e18-189">System.String[]</span></span>

### <span data-ttu-id="68e18-190">System.web. PSObject []</span><span class="sxs-lookup"><span data-stu-id="68e18-190">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="68e18-191">System.String</span><span class="sxs-lookup"><span data-stu-id="68e18-191">System.String</span></span>

### <span data-ttu-id="68e18-192">System.Uri</span><span class="sxs-lookup"><span data-stu-id="68e18-192">System.Uri</span></span>

### <span data-ttu-id="68e18-193">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="68e18-193">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="68e18-194">출력</span><span class="sxs-lookup"><span data-stu-id="68e18-194">OUTPUTS</span></span>

### <span data-ttu-id="68e18-195">System.Object</span><span class="sxs-lookup"><span data-stu-id="68e18-195">System.Object</span></span>

## <span data-ttu-id="68e18-196">참고</span><span class="sxs-lookup"><span data-stu-id="68e18-196">NOTES</span></span>

## <span data-ttu-id="68e18-197">관련 링크</span><span class="sxs-lookup"><span data-stu-id="68e18-197">RELATED LINKS</span></span>

