---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Module
ms.openlocfilehash: df5056b4402664602409388825c8b2b8acd4e02f
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99601841"
---
# <span data-ttu-id="631ae-102">Save-Module</span><span class="sxs-lookup"><span data-stu-id="631ae-102">Save-Module</span></span>

## <span data-ttu-id="631ae-103">개요</span><span class="sxs-lookup"><span data-stu-id="631ae-103">SYNOPSIS</span></span>
<span data-ttu-id="631ae-104">모듈 및 해당 종속성을 로컬 컴퓨터에 저장 하지만 모듈을 설치 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-104">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

## <span data-ttu-id="631ae-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="631ae-105">SYNTAX</span></span>

### <span data-ttu-id="631ae-106">NameAndPathParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="631ae-106">NameAndPathParameterSet (Default)</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="631ae-107">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="631ae-107">NameAndLiteralPathParameterSet</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="631ae-108">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="631ae-108">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="631ae-109">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="631ae-109">InputObjectAndPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="631ae-110">설명</span><span class="sxs-lookup"><span data-stu-id="631ae-110">DESCRIPTION</span></span>

<span data-ttu-id="631ae-111">`Save-Module`Cmdlet은 모듈 및 등록 된 리포지토리에서 모든 종속성을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-111">The `Save-Module` cmdlet downloads a module and any dependencies from a registered repository.</span></span>
<span data-ttu-id="631ae-112">`Save-Module` 최신 버전의 모듈을 다운로드 하 여 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-112">`Save-Module` downloads and saves the most current version of a module.</span></span> <span data-ttu-id="631ae-113">파일은 로컬 컴퓨터의 지정 된 경로에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-113">The files are saved to a specified path on the local computer.</span></span> <span data-ttu-id="631ae-114">모듈이 설치 되지 않았지만 관리자가 콘텐츠를 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-114">The module isn't installed, but the contents are available for inspection by an administrator.</span></span> <span data-ttu-id="631ae-115">그런 다음 저장 된 모듈을 `$env:PSModulePath` 오프 라인 컴퓨터의 적절 한 위치에 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-115">The saved module can then be copied into the appropriate `$env:PSModulePath` location of the offline machine.</span></span>

<span data-ttu-id="631ae-116">`Get-PSRepository` 로컬 컴퓨터의 등록 된 리포지토리를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-116">`Get-PSRepository` displays the local computer's registered repositories.</span></span> <span data-ttu-id="631ae-117">Cmdlet을 사용 `Find-Module` 하 여 등록 된 리포지토리를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-117">You can use the `Find-Module` cmdlet to search registered repositories.</span></span>

## <span data-ttu-id="631ae-118">예제</span><span class="sxs-lookup"><span data-stu-id="631ae-118">EXAMPLES</span></span>

### <span data-ttu-id="631ae-119">예제 1: 모듈 저장</span><span class="sxs-lookup"><span data-stu-id="631ae-119">Example 1: Save a module</span></span>

<span data-ttu-id="631ae-120">이 예제에서는 모듈 및 해당 종속성이 로컬 컴퓨터에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-120">In this example, a module and its dependencies are saved to the local computer.</span></span>

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

<span data-ttu-id="631ae-121">`Save-Module`**Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-121">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="631ae-122">**Path** 매개 변수는 다운로드 한 모듈을 저장할 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-122">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="631ae-123">**리포지토리** 매개 변수는 등록 된 리포지토리 **PSGallery** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-123">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="631ae-124">다운로드가 완료 되 면는 `Get-ChildItem` 파일이 저장 된 **경로** 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-124">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="631ae-125">예제 2: 모듈의 특정 버전 저장</span><span class="sxs-lookup"><span data-stu-id="631ae-125">Example 2: Save a specific version of a module</span></span>

<span data-ttu-id="631ae-126">이 예에서는 **MaximumVersion** 또는 **RequiredVersion** 과 같은 매개 변수를 사용 하 여 모듈 버전을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-126">This example shows how to use a parameter such as **MaximumVersion**, or **RequiredVersion** to specify a module version.</span></span>

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

<span data-ttu-id="631ae-127">`Save-Module`**Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-127">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="631ae-128">**Path** 매개 변수는 다운로드 한 모듈을 저장할 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-128">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="631ae-129">**리포지토리** 매개 변수는 등록 된 리포지토리 **PSGallery** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-129">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="631ae-130">**MaximumVersion** 은 버전 **2.1.0** 을 다운로드 하 여 저장 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-130">**MaximumVersion** specifies that version **2.1.0** is downloaded and saved.</span></span> <span data-ttu-id="631ae-131">다운로드가 완료 되 면는 `Get-ChildItem` 파일이 저장 된 **경로** 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-131">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="631ae-132">예제 3: 모듈의 특정 버전 찾기 및 저장</span><span class="sxs-lookup"><span data-stu-id="631ae-132">Example 3: Find and save a specific version of a module</span></span>

<span data-ttu-id="631ae-133">이 예제에서는 필수 모듈 버전이 리포지토리에서 검색 되 고 로컬 컴퓨터에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-133">In this example, a required module version is found in the repository and saved to the local computer.</span></span>

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

<span data-ttu-id="631ae-134">`Find-Module`**Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-134">`Find-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="631ae-135">**리포지토리** 매개 변수는 등록 된 리포지토리 **PSGallery** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-135">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="631ae-136">**RequiredVersion** 버전 **1.6.5** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-136">**RequiredVersion** specifies version **1.6.5**.</span></span>

<span data-ttu-id="631ae-137">개체는 파이프라인에서로 전송 됩니다 `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="631ae-137">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="631ae-138">**Path** 매개 변수는 다운로드 한 모듈을 저장할 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-138">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="631ae-139">다운로드가 완료 되 면는 `Get-ChildItem` 파일이 저장 된 **경로** 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-139">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

## <span data-ttu-id="631ae-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="631ae-140">PARAMETERS</span></span>

### <span data-ttu-id="631ae-141">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="631ae-141">-AcceptLicense</span></span>

<span data-ttu-id="631ae-142">패키지에 필요한 경우 사용권 계약에 자동으로 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-142">Automatically accept the license agreement if the package requires it.</span></span>

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

### <span data-ttu-id="631ae-143">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="631ae-143">-AllowPrerelease</span></span>

<span data-ttu-id="631ae-144">시험판으로 표시 된 모듈을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-144">Allows you to save a module marked as a prerelease.</span></span>

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

### <span data-ttu-id="631ae-145">-Confirm</span><span class="sxs-lookup"><span data-stu-id="631ae-145">-Confirm</span></span>

<span data-ttu-id="631ae-146">을 실행 하기 전에 확인 메시지를 표시 `Save-Module` 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-146">Prompts you for confirmation before running the `Save-Module`.</span></span>

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

### <span data-ttu-id="631ae-147">-Credential</span><span class="sxs-lookup"><span data-stu-id="631ae-147">-Credential</span></span>

<span data-ttu-id="631ae-148">모듈을 저장할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-148">Specifies a user account that has rights to save a module.</span></span>

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

### <span data-ttu-id="631ae-149">-Force</span><span class="sxs-lookup"><span data-stu-id="631ae-149">-Force</span></span>

<span data-ttu-id="631ae-150">`Save-Module`사용자 확인을 요청 하지 않고 강제로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-150">Forces `Save-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="631ae-151">-InputObject</span><span class="sxs-lookup"><span data-stu-id="631ae-151">-InputObject</span></span>

<span data-ttu-id="631ae-152">**PSRepositoryItemInfo** 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-152">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="631ae-153">예를 들어 `Find-Module` 변수를 출력 하 고 해당 변수를 **InputObject** 인수로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-153">For example, output `Find-Module` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="631ae-154">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="631ae-154">-LiteralPath</span></span>

<span data-ttu-id="631ae-155">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-155">Specifies a path to one or more locations.</span></span> <span data-ttu-id="631ae-156">**LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-156">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="631ae-157">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-157">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="631ae-158">경로에 이스케이프 문자가 포함 되어 있으면 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-158">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="631ae-159">PowerShell은 작은 따옴표로 묶인 문자를 이스케이프 시퀀스로 해석 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-159">PowerShell does not interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

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

### <span data-ttu-id="631ae-160">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="631ae-160">-MaximumVersion</span></span>

<span data-ttu-id="631ae-161">저장할 모듈의 최대 또는 최신 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-161">Specifies the maximum, or newest, version of the module to save.</span></span> <span data-ttu-id="631ae-162">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-162">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="631ae-163">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="631ae-163">-MinimumVersion</span></span>

<span data-ttu-id="631ae-164">저장할 단일 모듈의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-164">Specifies the minimum version of a single module to save.</span></span> <span data-ttu-id="631ae-165">여러 모듈을 설치 하려는 경우에는이 매개 변수를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-165">You cannot add this parameter if you are attempting to install multiple modules.</span></span> <span data-ttu-id="631ae-166">**MinimumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-166">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="631ae-167">-Name</span><span class="sxs-lookup"><span data-stu-id="631ae-167">-Name</span></span>

<span data-ttu-id="631ae-168">저장할 모듈의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-168">Specifies an array of names of modules to save.</span></span>

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

### <span data-ttu-id="631ae-169">-Path</span><span class="sxs-lookup"><span data-stu-id="631ae-169">-Path</span></span>

<span data-ttu-id="631ae-170">저장 된 모듈을 저장할 로컬 컴퓨터의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-170">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="631ae-171">와일드 카드 문자를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-171">Accepts wildcard characters.</span></span>

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

### <span data-ttu-id="631ae-172">-프록시</span><span class="sxs-lookup"><span data-stu-id="631ae-172">-Proxy</span></span>

<span data-ttu-id="631ae-173">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-173">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>

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

### <span data-ttu-id="631ae-174">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="631ae-174">-ProxyCredential</span></span>

<span data-ttu-id="631ae-175">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-175">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="631ae-176">-리포지토리</span><span class="sxs-lookup"><span data-stu-id="631ae-176">-Repository</span></span>

<span data-ttu-id="631ae-177">을 실행 하 여 등록 된 리포지토리의 이름을 지정 합니다 `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="631ae-177">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="631ae-178">`Get-PSRepository`등록 된 리포지토리를 표시 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-178">Use `Get-PSRepository` to display registered repositories.</span></span>

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

### <span data-ttu-id="631ae-179">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="631ae-179">-RequiredVersion</span></span>

<span data-ttu-id="631ae-180">저장할 모듈의 정확한 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-180">Specifies the exact version number of the module to save.</span></span>

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

### <span data-ttu-id="631ae-181">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="631ae-181">-WhatIf</span></span>

<span data-ttu-id="631ae-182">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="631ae-182">Shows what would happen if the `Save-Module` runs.</span></span> <span data-ttu-id="631ae-183">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-183">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="631ae-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="631ae-184">CommonParameters</span></span>

<span data-ttu-id="631ae-185">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="631ae-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="631ae-186">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="631ae-186">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="631ae-187">입력</span><span class="sxs-lookup"><span data-stu-id="631ae-187">INPUTS</span></span>

### <span data-ttu-id="631ae-188">System.String[]</span><span class="sxs-lookup"><span data-stu-id="631ae-188">System.String[]</span></span>

### <span data-ttu-id="631ae-189">System.web. PSObject []</span><span class="sxs-lookup"><span data-stu-id="631ae-189">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="631ae-190">System.String</span><span class="sxs-lookup"><span data-stu-id="631ae-190">System.String</span></span>

### <span data-ttu-id="631ae-191">System.Uri</span><span class="sxs-lookup"><span data-stu-id="631ae-191">System.Uri</span></span>

### <span data-ttu-id="631ae-192">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="631ae-192">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="631ae-193">출력</span><span class="sxs-lookup"><span data-stu-id="631ae-193">OUTPUTS</span></span>

### <span data-ttu-id="631ae-194">System.Object</span><span class="sxs-lookup"><span data-stu-id="631ae-194">System.Object</span></span>

## <span data-ttu-id="631ae-195">참고</span><span class="sxs-lookup"><span data-stu-id="631ae-195">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="631ae-196">2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-196">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="631ae-197">TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-197">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="631ae-198">다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="631ae-198">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="631ae-199">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="631ae-199">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="631ae-200">관련 링크</span><span class="sxs-lookup"><span data-stu-id="631ae-200">RELATED LINKS</span></span>
