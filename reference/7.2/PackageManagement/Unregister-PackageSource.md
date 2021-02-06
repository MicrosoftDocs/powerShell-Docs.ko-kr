---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/unregister-packagesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PackageSource
ms.openlocfilehash: 6ef89e9143fe8883bc98723d10775bf739fe72f9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599335"
---
# <span data-ttu-id="96a66-102">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="96a66-102">Unregister-PackageSource</span></span>

## <span data-ttu-id="96a66-103">개요</span><span class="sxs-lookup"><span data-stu-id="96a66-103">SYNOPSIS</span></span>
<span data-ttu-id="96a66-104">등록 된 패키지 소스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-104">Removes a registered package source.</span></span>

## <span data-ttu-id="96a66-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="96a66-105">SYNTAX</span></span>

### <span data-ttu-id="96a66-106">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="96a66-106">SourceBySearch</span></span>

```
Unregister-PackageSource [[-Source] <String>] [-Location <String>] [-Credential <PSCredential>]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="96a66-107">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="96a66-107">SourceByInputObject</span></span>

```
Unregister-PackageSource -InputObject <PackageSource[]> [-Credential <PSCredential>] [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="96a66-108">NuGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="96a66-108">NuGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="96a66-109">NuGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="96a66-109">NuGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="96a66-110">PowerShellGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="96a66-110">PowerShellGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="96a66-111">PowerShellGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="96a66-111">PowerShellGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="96a66-112">설명</span><span class="sxs-lookup"><span data-stu-id="96a66-112">DESCRIPTION</span></span>

<span data-ttu-id="96a66-113">`Unregister-PackageSource`Cmdlet은 등록 된 패키지 원본을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-113">The `Unregister-PackageSource` cmdlet removes a registered package source.</span></span> <span data-ttu-id="96a66-114">패키지 원본은 항상 패키지 공급자에 의해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-114">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="96a66-115">패키지 원본을 찾으려면 cmdlet을 사용 `Get-PackageSource` 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-115">To find package sources, use the `Get-PackageSource` cmdlet.</span></span>

## <span data-ttu-id="96a66-116">예제</span><span class="sxs-lookup"><span data-stu-id="96a66-116">EXAMPLES</span></span>

### <span data-ttu-id="96a66-117">예제 1: Nuget 공급자에 대 한 패키지 소스 등록 취소</span><span class="sxs-lookup"><span data-stu-id="96a66-117">Example 1: Unregister a package source for the Nuget provider</span></span>

<span data-ttu-id="96a66-118">`Unregister-PackageSource`Cmdlet은 로컬 컴퓨터에서 패키지 원본의 등록을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-118">The `Unregister-PackageSource` cmdlet unregisters a package source from the local computer.</span></span> <span data-ttu-id="96a66-119">**위치** 및 **공급자** 매개 변수를 사용 하 여 제거할 소스를 추가로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-119">The **Location** and **Provider** parameters can be used to further specify the source to remove.</span></span>

```
PS> Unregister-PackageSource -Source MyNuGet
```

<span data-ttu-id="96a66-120">`Unregister-PackageSource`Cmdlet은 **source** 매개 변수를 사용 하 여 제거할 소스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-120">The `Unregister-PackageSource` cmdlet uses the **Source** parameter to specify which source to remove.</span></span>

### <span data-ttu-id="96a66-121">예제 2: Register-packagesource 개체를 사용 하 여 패키지 등록 취소</span><span class="sxs-lookup"><span data-stu-id="96a66-121">Example 2: Use a PackageSource object to unregister a package</span></span>

<span data-ttu-id="96a66-122">이 예제에서는 및를 사용 하 여 `Get-PackageSource` `Unregister-PackageSource` 패키지 원본의 등록을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-122">This example uses the `Get-PackageSource` and `Unregister-PackageSource` to unregister a package source.</span></span> <span data-ttu-id="96a66-123">**Register-packagesource** 개체는 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-123">The **PackageSource** object is stored in a variable.</span></span>

```
PS> $pkgsource = Get-PackageSource -Name MyNuGet
PS> Unregister-PackageSource -InputObject $pkgsource
```

<span data-ttu-id="96a66-124">`$pkgsource`변수는 cmdlet에서 만든 **register-packagesource** 를 저장 합니다 `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="96a66-124">The `$pkgsource` variable stores the **PackageSource** created by the `Get-PackageSource` cmdlet.</span></span>
<span data-ttu-id="96a66-125">`Unregister-PackageSource` 를 `$pkgsource` **InputObject** 매개 변수에 대 한 입력으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-125">`Unregister-PackageSource` uses the `$pkgsource` as input to the **InputObject** parameter.</span></span>

<span data-ttu-id="96a66-126">또는 `Unregister-PackageSource` cmdlet에서 **InputObject** 매개 변수에 대 한 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-126">As an alternative, the `Unregister-PackageSource` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Unregister-PackageSource -InputObject ( Get-PackageSource -Name MyNuGet )`

## <span data-ttu-id="96a66-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="96a66-127">PARAMETERS</span></span>

### <span data-ttu-id="96a66-128">-Smi-s</span><span class="sxs-lookup"><span data-stu-id="96a66-128">-ConfigFile</span></span>

<span data-ttu-id="96a66-129">구성 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-129">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="96a66-130">-Credential</span><span class="sxs-lookup"><span data-stu-id="96a66-130">-Credential</span></span>

<span data-ttu-id="96a66-131">컴퓨터에 액세스할 수 있는 권한이 있는 사용자 계정을 지정 하 고 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-131">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="96a66-132">**User01**, **Domain01\User01** 등의 사용자 이름을 입력 하거나, cmdlet에 의해 생성 되는 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="96a66-132">Type a user name, such as **User01**, **Domain01\User01**, or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="96a66-133">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-133">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="96a66-134">**Credential** 매개 변수를 지정 하지 않으면 현재 사용자 계정이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-134">When the **Credential** parameter isn't specified, the current user account is used.</span></span>

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

### <span data-ttu-id="96a66-135">-Force</span><span class="sxs-lookup"><span data-stu-id="96a66-135">-Force</span></span>

<span data-ttu-id="96a66-136">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-136">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="96a66-137">는 보안을 제외 하 고 다음이 발생 하지 않도록 하는 제한을 재정의 합니다 `Unregister-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="96a66-137">Overrides restrictions that prevent `Unregister-PackageSource` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="96a66-138">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="96a66-138">-ForceBootstrap</span></span>

<span data-ttu-id="96a66-139">PackageManagement가 `Unregister-PackageSource` 지정  된 패키지 원본에 대 한 패키지 공급자를 자동으로 제거 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-139">Indicates that `Unregister-PackageSource` forces **PackageManagement** to automatically uninstall the package provider for the specified package source.</span></span>

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

### <span data-ttu-id="96a66-140">-InputObject</span><span class="sxs-lookup"><span data-stu-id="96a66-140">-InputObject</span></span>

<span data-ttu-id="96a66-141">Cmdlet에서 **register-packagesource** 개체를 지정 하는 파이프라인 입력을 허용 `Get-PackageSource` 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-141">Accepts pipeline input that specifies the **PackageSource** object from the `Get-PackageSource` cmdlet.</span></span> <span data-ttu-id="96a66-142">**InputObject** 에서는 **register-packagesource** 개체를 `Get-PackageSource` 값 또는 개체를 포함 하는 변수로 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-142">**InputObject** accepts the **PackageSource** object as a `Get-PackageSource` value or a variable that contains the object.</span></span>

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

### <span data-ttu-id="96a66-143">-Location</span><span class="sxs-lookup"><span data-stu-id="96a66-143">-Location</span></span>

<span data-ttu-id="96a66-144">패키지 원본이 가리키는 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-144">Specifies the location to which a package source points.</span></span> <span data-ttu-id="96a66-145">이 매개 변수 값은 URI, 파일 경로 또는 패키지 공급자가 지 원하는 다른 모든 대상 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-145">The value of this parameter can be a URI, a file path, or any other destination format that is supported by the package provider.</span></span>

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

### <span data-ttu-id="96a66-146">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="96a66-146">-PackageManagementProvider</span></span>

<span data-ttu-id="96a66-147">**PackageManagement** 공급자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-147">Specifies the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="96a66-148">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="96a66-148">-ProviderName</span></span>

<span data-ttu-id="96a66-149">공급자 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-149">Specifies the provider name.</span></span>

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

### <span data-ttu-id="96a66-150">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="96a66-150">-PublishLocation</span></span>

<span data-ttu-id="96a66-151">게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-151">Specifies the publish location.</span></span>

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

### <span data-ttu-id="96a66-152">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="96a66-152">-ScriptPublishLocation</span></span>

<span data-ttu-id="96a66-153">스크립트 게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-153">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="96a66-154">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="96a66-154">-ScriptSourceLocation</span></span>

<span data-ttu-id="96a66-155">스크립트 원본 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-155">Specifies the script source location.</span></span>

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

### <span data-ttu-id="96a66-156">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="96a66-156">-SkipValidate</span></span>

<span data-ttu-id="96a66-157">패키지 원본에 대 한 자격 증명의 유효성 검사를 건너뛰는 스위치입니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-157">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="96a66-158">-Source</span><span class="sxs-lookup"><span data-stu-id="96a66-158">-Source</span></span>

<span data-ttu-id="96a66-159">패키지 원본의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-159">Specifies the friendly name of the package source.</span></span>

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

### <span data-ttu-id="96a66-160">-Confirm</span><span class="sxs-lookup"><span data-stu-id="96a66-160">-Confirm</span></span>

<span data-ttu-id="96a66-161">을 실행 하기 전에 확인 메시지를 표시 `Unregister-PackageSource` 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-161">Prompts you for confirmation before `Unregister-PackageSource` is run.</span></span>

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

### <span data-ttu-id="96a66-162">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="96a66-162">-WhatIf</span></span>

<span data-ttu-id="96a66-163">Cmdlet이 실행 될 경우 발생 하는 상황을 보여 줍니다 `Unregister-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="96a66-163">Shows what would happen if `Unregister-PackageSource` cmdlet is run.</span></span> <span data-ttu-id="96a66-164">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-164">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="96a66-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="96a66-165">CommonParameters</span></span>

<span data-ttu-id="96a66-166">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="96a66-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="96a66-167">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="96a66-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="96a66-168">입력</span><span class="sxs-lookup"><span data-stu-id="96a66-168">INPUTS</span></span>

### <span data-ttu-id="96a66-169">`Unregister-PackageSource` 파이프라인의 **register-packagesource** 개체를 입력으로 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-169">`Unregister-PackageSource` accepts **PackageSource** objects from the pipeline as input.</span></span>

## <span data-ttu-id="96a66-170">출력</span><span class="sxs-lookup"><span data-stu-id="96a66-170">OUTPUTS</span></span>

### <span data-ttu-id="96a66-171">`Unregister-PackageSource` 는 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-171">`Unregister-PackageSource` doesn't generate any output.</span></span>

## <span data-ttu-id="96a66-172">참고</span><span class="sxs-lookup"><span data-stu-id="96a66-172">NOTES</span></span>

<span data-ttu-id="96a66-173">명령에 패키지 공급자를 포함 하면 cmdlet에서 동적 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-173">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="96a66-174">동적 매개 변수는 패키지 공급자에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-174">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="96a66-175">`Get-Help`Cmdlet은 cmdlet의 매개 변수 집합을 나열 하 고 공급자의 매개 변수 집합을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="96a66-175">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span>

## <span data-ttu-id="96a66-176">관련 링크</span><span class="sxs-lookup"><span data-stu-id="96a66-176">RELATED LINKS</span></span>

[<span data-ttu-id="96a66-177">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="96a66-177">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="96a66-178">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="96a66-178">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="96a66-179">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="96a66-179">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="96a66-180">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="96a66-180">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="96a66-181">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="96a66-181">Set-PackageSource</span></span>](Set-PackageSource.md)

