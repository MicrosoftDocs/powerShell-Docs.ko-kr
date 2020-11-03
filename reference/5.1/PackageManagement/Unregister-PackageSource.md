---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/unregister-packagesource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PackageSource
ms.openlocfilehash: 0825fa0182783e307e143b2ae10c5c744c2d524b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213265"
---
# <span data-ttu-id="395aa-103">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="395aa-103">Unregister-PackageSource</span></span>

## <span data-ttu-id="395aa-104">개요</span><span class="sxs-lookup"><span data-stu-id="395aa-104">SYNOPSIS</span></span>
<span data-ttu-id="395aa-105">등록 된 패키지 소스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-105">Removes a registered package source.</span></span>

## <span data-ttu-id="395aa-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="395aa-106">SYNTAX</span></span>

### <span data-ttu-id="395aa-107">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="395aa-107">SourceBySearch</span></span>

```
Unregister-PackageSource [[-Source] <String>] [-Location <String>] [-Credential <PSCredential>]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="395aa-108">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="395aa-108">SourceByInputObject</span></span>

```
Unregister-PackageSource -InputObject <PackageSource[]> [-Credential <PSCredential>] [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="395aa-109">NuGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="395aa-109">NuGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="395aa-110">NuGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="395aa-110">NuGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="395aa-111">PowerShellGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="395aa-111">PowerShellGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="395aa-112">PowerShellGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="395aa-112">PowerShellGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="395aa-113">설명</span><span class="sxs-lookup"><span data-stu-id="395aa-113">DESCRIPTION</span></span>

<span data-ttu-id="395aa-114">`Unregister-PackageSource`Cmdlet은 등록 된 패키지 원본을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-114">The `Unregister-PackageSource` cmdlet removes a registered package source.</span></span> <span data-ttu-id="395aa-115">패키지 원본은 항상 패키지 공급자에 의해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-115">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="395aa-116">패키지 원본을 찾으려면 cmdlet을 사용 `Get-PackageSource` 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-116">To find package sources, use the `Get-PackageSource` cmdlet.</span></span>

## <span data-ttu-id="395aa-117">예제</span><span class="sxs-lookup"><span data-stu-id="395aa-117">EXAMPLES</span></span>

### <span data-ttu-id="395aa-118">예제 1: Nuget 공급자에 대 한 패키지 소스 등록 취소</span><span class="sxs-lookup"><span data-stu-id="395aa-118">Example 1: Unregister a package source for the Nuget provider</span></span>

<span data-ttu-id="395aa-119">`Unregister-PackageSource`Cmdlet은 로컬 컴퓨터에서 패키지 원본의 등록을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-119">The `Unregister-PackageSource` cmdlet unregisters a package source from the local computer.</span></span> <span data-ttu-id="395aa-120">**위치** 및 **공급자** 매개 변수를 사용 하 여 제거할 소스를 추가로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-120">The **Location** and **Provider** parameters can be used to further specify the source to remove.</span></span>

```
PS> Unregister-PackageSource -Source MyNuGet
```

<span data-ttu-id="395aa-121">`Unregister-PackageSource`Cmdlet은 **source** 매개 변수를 사용 하 여 제거할 소스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-121">The `Unregister-PackageSource` cmdlet uses the **Source** parameter to specify which source to remove.</span></span>

### <span data-ttu-id="395aa-122">예제 2: Register-packagesource 개체를 사용 하 여 패키지 등록 취소</span><span class="sxs-lookup"><span data-stu-id="395aa-122">Example 2: Use a PackageSource object to unregister a package</span></span>

<span data-ttu-id="395aa-123">이 예제에서는 및를 사용 하 여 `Get-PackageSource` `Unregister-PackageSource` 패키지 원본의 등록을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-123">This example uses the `Get-PackageSource` and `Unregister-PackageSource` to unregister a package source.</span></span> <span data-ttu-id="395aa-124">**Register-packagesource** 개체는 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-124">The **PackageSource** object is stored in a variable.</span></span>

```
PS> $pkgsource = Get-PackageSource -Name MyNuGet
PS> Unregister-PackageSource -InputObject $pkgsource
```

<span data-ttu-id="395aa-125">`$pkgsource`변수는 cmdlet에서 만든 **register-packagesource** 를 저장 합니다 `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="395aa-125">The `$pkgsource` variable stores the **PackageSource** created by the `Get-PackageSource` cmdlet.</span></span>
<span data-ttu-id="395aa-126">`Unregister-PackageSource` 를 `$pkgsource` **InputObject** 매개 변수에 대 한 입력으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-126">`Unregister-PackageSource` uses the `$pkgsource` as input to the **InputObject** parameter.</span></span>

<span data-ttu-id="395aa-127">또는 `Unregister-PackageSource` cmdlet에서 **InputObject** 매개 변수에 대 한 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-127">As an alternative, the `Unregister-PackageSource` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Unregister-PackageSource -InputObject ( Get-PackageSource -Name MyNuGet )`

## <span data-ttu-id="395aa-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="395aa-128">PARAMETERS</span></span>

### <span data-ttu-id="395aa-129">-Smi-s</span><span class="sxs-lookup"><span data-stu-id="395aa-129">-ConfigFile</span></span>

<span data-ttu-id="395aa-130">구성 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-130">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="395aa-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="395aa-131">-Credential</span></span>

<span data-ttu-id="395aa-132">컴퓨터에 액세스할 수 있는 권한이 있는 사용자 계정을 지정 하 고 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-132">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="395aa-133">**User01** , **Domain01\User01** 등의 사용자 이름을 입력 하거나, cmdlet에 의해 생성 되는 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="395aa-133">Type a user name, such as **User01** , **Domain01\User01** , or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="395aa-134">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-134">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="395aa-135">**Credential** 매개 변수를 지정 하지 않으면 현재 사용자 계정이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-135">When the **Credential** parameter isn't specified, the current user account is used.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="395aa-136">-Force</span><span class="sxs-lookup"><span data-stu-id="395aa-136">-Force</span></span>

<span data-ttu-id="395aa-137">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-137">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="395aa-138">는 보안을 제외 하 고 다음이 발생 하지 않도록 하는 제한을 재정의 합니다 `Unregister-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="395aa-138">Overrides restrictions that prevent `Unregister-PackageSource` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="395aa-139">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="395aa-139">-ForceBootstrap</span></span>

<span data-ttu-id="395aa-140">PackageManagement가 `Unregister-PackageSource` 지정 **PackageManagement** 된 패키지 원본에 대 한 패키지 공급자를 자동으로 제거 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-140">Indicates that `Unregister-PackageSource` forces **PackageManagement** to automatically uninstall the package provider for the specified package source.</span></span>

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

### <span data-ttu-id="395aa-141">-InputObject</span><span class="sxs-lookup"><span data-stu-id="395aa-141">-InputObject</span></span>

<span data-ttu-id="395aa-142">Cmdlet에서 **register-packagesource** 개체를 지정 하는 파이프라인 입력을 허용 `Get-PackageSource` 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-142">Accepts pipeline input that specifies the **PackageSource** object from the `Get-PackageSource` cmdlet.</span></span> <span data-ttu-id="395aa-143">**InputObject** 에서는 **register-packagesource** 개체를 `Get-PackageSource` 값 또는 개체를 포함 하는 변수로 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-143">**InputObject** accepts the **PackageSource** object as a `Get-PackageSource` value or a variable that contains the object.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.PackageSource[]
Parameter Sets: SourceByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="395aa-144">-Location</span><span class="sxs-lookup"><span data-stu-id="395aa-144">-Location</span></span>

<span data-ttu-id="395aa-145">패키지 원본이 가리키는 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-145">Specifies the location to which a package source points.</span></span> <span data-ttu-id="395aa-146">이 매개 변수 값은 URI, 파일 경로 또는 패키지 공급자가 지 원하는 다른 모든 대상 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-146">The value of this parameter can be a URI, a file path, or any other destination format that is supported by the package provider.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="395aa-147">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="395aa-147">-PackageManagementProvider</span></span>

<span data-ttu-id="395aa-148">**PackageManagement** 공급자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-148">Specifies the **PackageManagement** provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="395aa-149">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="395aa-149">-ProviderName</span></span>

<span data-ttu-id="395aa-150">공급자 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-150">Specifies the provider name.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="395aa-151">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="395aa-151">-PublishLocation</span></span>

<span data-ttu-id="395aa-152">게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-152">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="395aa-153">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="395aa-153">-ScriptPublishLocation</span></span>

<span data-ttu-id="395aa-154">스크립트 게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-154">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="395aa-155">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="395aa-155">-ScriptSourceLocation</span></span>

<span data-ttu-id="395aa-156">스크립트 원본 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-156">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="395aa-157">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="395aa-157">-SkipValidate</span></span>

<span data-ttu-id="395aa-158">패키지 원본에 대 한 자격 증명의 유효성 검사를 건너뛰는 스위치입니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-158">Switch that skips validating the credentials of a package source.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="395aa-159">-Source</span><span class="sxs-lookup"><span data-stu-id="395aa-159">-Source</span></span>

<span data-ttu-id="395aa-160">패키지 원본의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-160">Specifies the friendly name of the package source.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="395aa-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="395aa-161">-Confirm</span></span>

<span data-ttu-id="395aa-162">을 실행 하기 전에 확인 메시지를 표시 `Unregister-PackageSource` 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-162">Prompts you for confirmation before `Unregister-PackageSource` is run.</span></span>

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

### <span data-ttu-id="395aa-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="395aa-163">-WhatIf</span></span>

<span data-ttu-id="395aa-164">Cmdlet이 실행 될 경우 발생 하는 상황을 보여 줍니다 `Unregister-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="395aa-164">Shows what would happen if `Unregister-PackageSource` cmdlet is run.</span></span> <span data-ttu-id="395aa-165">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-165">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="395aa-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="395aa-166">CommonParameters</span></span>

<span data-ttu-id="395aa-167">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="395aa-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="395aa-168">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="395aa-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="395aa-169">입력</span><span class="sxs-lookup"><span data-stu-id="395aa-169">INPUTS</span></span>

### <span data-ttu-id="395aa-170">`Unregister-PackageSource` 파이프라인의 **register-packagesource** 개체를 입력으로 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-170">`Unregister-PackageSource` accepts **PackageSource** objects from the pipeline as input.</span></span>

## <span data-ttu-id="395aa-171">출력</span><span class="sxs-lookup"><span data-stu-id="395aa-171">OUTPUTS</span></span>

### <span data-ttu-id="395aa-172">`Unregister-PackageSource` 는 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-172">`Unregister-PackageSource` doesn't generate any output.</span></span>

## <span data-ttu-id="395aa-173">참고</span><span class="sxs-lookup"><span data-stu-id="395aa-173">NOTES</span></span>

<span data-ttu-id="395aa-174">명령에 패키지 공급자를 포함 하면 cmdlet에서 동적 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-174">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="395aa-175">동적 매개 변수는 패키지 공급자에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-175">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="395aa-176">`Get-Help`Cmdlet은 cmdlet의 매개 변수 집합을 나열 하 고 공급자의 매개 변수 집합을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="395aa-176">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span>

## <span data-ttu-id="395aa-177">관련 링크</span><span class="sxs-lookup"><span data-stu-id="395aa-177">RELATED LINKS</span></span>

[<span data-ttu-id="395aa-178">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="395aa-178">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="395aa-179">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="395aa-179">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="395aa-180">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="395aa-180">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="395aa-181">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="395aa-181">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="395aa-182">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="395aa-182">Set-PackageSource</span></span>](Set-PackageSource.md)
