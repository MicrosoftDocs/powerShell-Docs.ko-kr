---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Module
ms.openlocfilehash: 50f873e6691ead7c220b6250458f4fdf8a90af22
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215234"
---
# <span data-ttu-id="52931-103">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="52931-103">Publish-Module</span></span>

## <span data-ttu-id="52931-104">개요</span><span class="sxs-lookup"><span data-stu-id="52931-104">SYNOPSIS</span></span>
<span data-ttu-id="52931-105">로컬 컴퓨터에서 지정된 모듈을 온라인 갤러리에 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-105">Publishes a specified module from the local computer to an online gallery.</span></span>

## <span data-ttu-id="52931-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="52931-106">SYNTAX</span></span>

### <span data-ttu-id="52931-107">ModuleNameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="52931-107">ModuleNameParameterSet (Default)</span></span>

```
Publish-Module -Name <String> [-RequiredVersion <String>] [-NuGetApiKey <String>]
 [-Repository <String>] [-Credential <PSCredential>] [-FormatVersion <Version>]
 [-ReleaseNotes <String[]>] [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ProjectUri <Uri>] [-Exclude <String[]>] [-Force] [-AllowPrerelease] [-SkipAutomaticTags]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="52931-108">ModulePathParameterSet</span><span class="sxs-lookup"><span data-stu-id="52931-108">ModulePathParameterSet</span></span>

```
Publish-Module -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-FormatVersion <Version>] [-ReleaseNotes <String[]>]
 [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ProjectUri <Uri>] [-Force]
 [-SkipAutomaticTags] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="52931-109">설명</span><span class="sxs-lookup"><span data-stu-id="52931-109">DESCRIPTION</span></span>

<span data-ttu-id="52931-110">`Publish-Module`Cmdlet은 갤러리에 사용자 프로필의 일부로 저장 된 API 키를 사용 하 여 온라인 NuGet 기반 갤러리에 모듈을 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-110">The `Publish-Module` cmdlet publishes a module to an online NuGet-based gallery by using an API key, stored as part of a user's profile in the gallery.</span></span> <span data-ttu-id="52931-111">모듈의 이름 또는 모듈을 포함하는 폴더의 경로를 통해 게시할 모듈을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52931-111">You can specify the module to publish either by the module's name, or by the path to the folder containing the module.</span></span>

<span data-ttu-id="52931-112">이름으로 모듈을 지정 하면에서를 `Publish-Module` 실행 하 여 발견 되는 첫 번째 모듈을 게시 합니다 `Get-Module -ListAvailable <Name>` .</span><span class="sxs-lookup"><span data-stu-id="52931-112">When you specify a module by name, `Publish-Module` publishes the first module that would be found by running `Get-Module -ListAvailable <Name>`.</span></span> <span data-ttu-id="52931-113">게시할 모듈의 최소 버전을 지정 하는 경우는 `Publish-Module` 지정한 최소 버전 보다 크거나 같은 버전으로 첫 번째 모듈을 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-113">If you specify a minimum version of a module to publish, `Publish-Module` publishes the first module with a version that is greater than or equal to the minimum version that you have specified.</span></span>

<span data-ttu-id="52931-114">모듈을 게시하려면 모듈에 대한 갤러리 페이지에 표시되는 메타데이터가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-114">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="52931-115">필수 메타데이터에는 모듈 이름, 버전, 설명, 만든 이 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="52931-115">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="52931-116">대부분의 메타 데이터는 모듈 매니페스트에서 가져오므로 `Publish-Module` **Tag** , **ReleaseNote** , **IconUri** , **ProjectUri** 및 **LicenseUri** 와 같은 매개 변수는 NuGet 기반 갤러리의 필드와 일치 하므로 일부 메타 데이터는 매개 변수에서 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-116">Although most metadata is taken from the module manifest, some metadata must be specified in `Publish-Module` parameters, such as **Tag** , **ReleaseNote** , **IconUri** , **ProjectUri** , and **LicenseUri** , because these parameters match fields in a NuGet-based gallery.</span></span>

## <span data-ttu-id="52931-117">예제</span><span class="sxs-lookup"><span data-stu-id="52931-117">EXAMPLES</span></span>

### <span data-ttu-id="52931-118">예제 1: 모듈 게시</span><span class="sxs-lookup"><span data-stu-id="52931-118">Example 1: Publish a module</span></span>

<span data-ttu-id="52931-119">이 예제에서 MyDscModule는 모듈 소유자의 온라인 갤러리 계정을 나타내는 API 키를 사용 하 여 온라인 갤러리에 게시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52931-119">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's online gallery account.</span></span> <span data-ttu-id="52931-120">MyDscModule가 이름, 버전, 설명 및 작성자를 지정 하는 유효한 매니페스트 모듈이 아닌 경우 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-120">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73"
```

### <span data-ttu-id="52931-121">예제 2: 갤러리 메타 데이터를 사용 하 여 모듈 게시</span><span class="sxs-lookup"><span data-stu-id="52931-121">Example 2: Publish a module with gallery metadata</span></span>

<span data-ttu-id="52931-122">이 예제에서 MyDscModule는 모듈 소유자의 갤러리 계정을 나타내는 API 키를 사용 하 여 온라인 갤러리에 게시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52931-122">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's gallery account.</span></span> <span data-ttu-id="52931-123">제공 된 추가 메타 데이터는 갤러리의 모듈에 대 한 웹 페이지에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52931-123">The additional metadata provided is displayed on the webpage for the module in the gallery.</span></span> <span data-ttu-id="52931-124">소유자는 모듈에 대 한 두 개의 검색 태그를 추가 하 여 Active Directory와 관련 합니다. 간략 한 릴리스 정보를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-124">The owner adds two search tags for the module, relating it to Active Directory; a brief release note is added.</span></span> <span data-ttu-id="52931-125">MyDscModule가 이름, 버전, 설명 및 작성자를 지정 하는 유효한 매니페스트 모듈이 아닌 경우 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-125">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73" -LicenseUri "http://contoso.com/license" -Tag "Active Directory","DSC" -ReleaseNote "Updated the ActiveDirectory DSC Resources to support adding users."
```

## <span data-ttu-id="52931-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="52931-126">PARAMETERS</span></span>

### <span data-ttu-id="52931-127">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="52931-127">-AllowPrerelease</span></span>

<span data-ttu-id="52931-128">시험판으로 표시 된 모듈을 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52931-128">Allows modules marked as prerelease to be published.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52931-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="52931-129">-Confirm</span></span>

<span data-ttu-id="52931-130">을 실행 하기 전에 확인 메시지를 표시 `Publish-Module` 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-130">Prompts you for confirmation before running the `Publish-Module`.</span></span>

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

### <span data-ttu-id="52931-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="52931-131">-Credential</span></span>

<span data-ttu-id="52931-132">지정 된 패키지 공급자나 원본에 대해 모듈을 게시할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-132">Specifies a user account that has rights to publish a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="52931-133">-제외</span><span class="sxs-lookup"><span data-stu-id="52931-133">-Exclude</span></span>

<span data-ttu-id="52931-134">게시 된 모듈에서 제외할 파일을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-134">Defines files to exclude from the published module.</span></span> <span data-ttu-id="52931-135">**Exclude** 매개 변수 지원은 **PowershellGet** 버전 2.0.0에서 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52931-135">**Exclude** parameter support is add in **PowershellGet** version 2.0.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52931-136">-Force</span><span class="sxs-lookup"><span data-stu-id="52931-136">-Force</span></span>

<span data-ttu-id="52931-137">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-137">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52931-138">-FormatVersion</span><span class="sxs-lookup"><span data-stu-id="52931-138">-FormatVersion</span></span>

<span data-ttu-id="52931-139">**ValidateSet** 특성에 지정 된 유효한 값만 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-139">Accepts only valid values specified by the **ValidateSet** attribute.</span></span>

<span data-ttu-id="52931-140">자세한 내용은 [ValidateSet Attribute 선언](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) 및 [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52931-140">For more information, see [ValidateSet Attribute Declaration](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) and [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute).</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:
Accepted values: 2.0

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52931-141">-IconUri</span><span class="sxs-lookup"><span data-stu-id="52931-141">-IconUri</span></span>

<span data-ttu-id="52931-142">모듈에 대 한 아이콘의 URL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-142">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="52931-143">지정 된 아이콘은 모듈에 대 한 갤러리 웹 페이지에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52931-143">The specified icon is displayed on the gallery webpage for the module.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52931-144">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="52931-144">-LicenseUri</span></span>

<span data-ttu-id="52931-145">게시할 모듈에 대 한 라이선스 조건의 URL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-145">Specifies the URL of licensing terms for the module you want to publish.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52931-146">-Name</span><span class="sxs-lookup"><span data-stu-id="52931-146">-Name</span></span>

<span data-ttu-id="52931-147">게시할 모듈의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-147">Specifies the name of the module that you want to publish.</span></span> <span data-ttu-id="52931-148">`Publish-Module` 에서 지정 된 모듈 이름을 검색 `$Env:PSModulePath` 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-148">`Publish-Module` searches for the specified module name in `$Env:PSModulePath`.</span></span>

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="52931-149">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="52931-149">-NuGetApiKey</span></span>

<span data-ttu-id="52931-150">온라인 갤러리에 모듈을 게시 하는 데 사용 하려는 API 키를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-150">Specifies the API key that you want to use to publish a module to the online gallery.</span></span> <span data-ttu-id="52931-151">API 키는 온라인 갤러리에 있는 프로필의 일부 이며 갤러리의 사용자 계정 페이지에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52931-151">The API key is part of your profile in the online gallery, and can be found on your user account page in the gallery.</span></span> <span data-ttu-id="52931-152">API 키는 NuGet 관련 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="52931-152">The API key is NuGet-specific functionality.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52931-153">-Path</span><span class="sxs-lookup"><span data-stu-id="52931-153">-Path</span></span>

<span data-ttu-id="52931-154">게시할 모듈의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-154">Specifies the path to the module that you want to publish.</span></span> <span data-ttu-id="52931-155">이 매개 변수는 모듈이 포함 된 폴더의 경로를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-155">This parameter accepts the path to the folder that contains the module.</span></span>

```yaml
Type: System.String
Parameter Sets: ModulePathParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="52931-156">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="52931-156">-ProjectUri</span></span>

<span data-ttu-id="52931-157">이 프로젝트에 대 한 웹 페이지의 URL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-157">Specifies the URL of a webpage about this project.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52931-158">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="52931-158">-ReleaseNotes</span></span>

<span data-ttu-id="52931-159">이 모듈 버전의 사용자가 사용할 수 있도록 하려는 릴리스 정보 또는 주석이 포함 된 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-159">Specifies a string containing release notes or comments that you want to be available to users of this version of the module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52931-160">-리포지토리</span><span class="sxs-lookup"><span data-stu-id="52931-160">-Repository</span></span>

<span data-ttu-id="52931-161">을 실행 하 여 등록 된 리포지토리의 이름을 지정 합니다 `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="52931-161">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="52931-162">리포지토리에는 유효한 NuGet URI 인 **PublishLocation** 이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-162">The repository must have a **PublishLocation** , which is a valid NuGet URI.</span></span>
<span data-ttu-id="52931-163">**PublishLocation** 는를 실행 하 여 설정할 수 있습니다 `Set-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="52931-163">The **PublishLocation** can be set by running `Set-PSRepository`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52931-164">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="52931-164">-RequiredVersion</span></span>

<span data-ttu-id="52931-165">게시할 단일 모듈의 정확한 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-165">Specifies the exact version of a single module to publish.</span></span>

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52931-166">-SkipAutomaticTags</span><span class="sxs-lookup"><span data-stu-id="52931-166">-SkipAutomaticTags</span></span>

<span data-ttu-id="52931-167">태그로 포함 되지 않도록 명령 및 리소스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-167">Removes commands and resources from being included as tags.</span></span> <span data-ttu-id="52931-168">모듈에 태그를 자동으로 추가 하는 것을 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="52931-168">Skips automatically adding tags to a module.</span></span> <span data-ttu-id="52931-169">**SkipAutomaticTags** 매개 변수 지원은 **PowerShellGet** 버전 2.0.0에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52931-169">**SkipAutomaticTags** parameter support is added in **PowerShellGet** version 2.0.0</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52931-170">-태그</span><span class="sxs-lookup"><span data-stu-id="52931-170">-Tags</span></span>

<span data-ttu-id="52931-171">게시 하는 모듈에 하나 이상의 태그를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-171">Adds one or more tags to the module that you are publishing.</span></span> <span data-ttu-id="52931-172">예제 태그에는 DesiredStateConfiguration, DSC, DSCResourceKit 또는 PSModule이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52931-172">Example tags include DesiredStateConfiguration, DSC, DSCResourceKit, or PSModule.</span></span> <span data-ttu-id="52931-173">여러 태그를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-173">Separate multiple tags with commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52931-174">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="52931-174">-WhatIf</span></span>

<span data-ttu-id="52931-175">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Publish-Module` .</span><span class="sxs-lookup"><span data-stu-id="52931-175">Shows what would happen if the `Publish-Module` runs.</span></span> <span data-ttu-id="52931-176">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52931-176">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="52931-177">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="52931-177">CommonParameters</span></span>

<span data-ttu-id="52931-178">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="52931-178">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="52931-179">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52931-179">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="52931-180">입력</span><span class="sxs-lookup"><span data-stu-id="52931-180">INPUTS</span></span>

### <span data-ttu-id="52931-181">System.String</span><span class="sxs-lookup"><span data-stu-id="52931-181">System.String</span></span>

### <span data-ttu-id="52931-182">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="52931-182">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="52931-183">출력</span><span class="sxs-lookup"><span data-stu-id="52931-183">OUTPUTS</span></span>

### <span data-ttu-id="52931-184">System.Object</span><span class="sxs-lookup"><span data-stu-id="52931-184">System.Object</span></span>

## <span data-ttu-id="52931-185">참고</span><span class="sxs-lookup"><span data-stu-id="52931-185">NOTES</span></span>

<span data-ttu-id="52931-186">`Publish-Module` powershell 3.0 이상 버전의 PowerShell, windows 7 또는 Windows 2008 R2 이상 버전에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52931-186">`Publish-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="52931-187">모듈을 게시하려면 모듈에 대한 갤러리 페이지에 표시되는 메타데이터가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="52931-187">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="52931-188">필수 메타데이터에는 모듈 이름, 버전, 설명, 만든 이 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="52931-188">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="52931-189">대부분의 메타 데이터는 모듈 매니페스트에서 가져오므로 `Publish-Module` **Tag** , **ReleaseNote** , **IconUri** , **ProjectUri** 및 **LicenseUri** 와 같은 매개 변수에 일부 메타 데이터를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52931-189">Most metadata is taken from the module manifest, but some metadata can be specified in `Publish-Module` parameters, such as **Tag** , **ReleaseNote** , **IconUri** , **ProjectUri** , and **LicenseUri** .</span></span> <span data-ttu-id="52931-190">자세한 내용은 [POWERSHELL 갤러리 UI에 영향을 주는 패키지 매니페스트 값](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52931-190">For more information, see [Package manifest values that impact the PowerShell Gallery UI](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui).</span></span>

## <span data-ttu-id="52931-191">관련 링크</span><span class="sxs-lookup"><span data-stu-id="52931-191">RELATED LINKS</span></span>

[<span data-ttu-id="52931-192">Find-Module</span><span class="sxs-lookup"><span data-stu-id="52931-192">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="52931-193">Install-Module</span><span class="sxs-lookup"><span data-stu-id="52931-193">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="52931-194">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="52931-194">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="52931-195">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="52931-195">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="52931-196">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="52931-196">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="52931-197">Update-Module</span><span class="sxs-lookup"><span data-stu-id="52931-197">Update-Module</span></span>](Update-Module.md)
