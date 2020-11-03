---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/register-psrepository?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSRepository
ms.openlocfilehash: be7ffa38a0409fa7ef0d01649b863a32732e34de
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211082"
---
# <span data-ttu-id="afad5-103">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="afad5-103">Register-PSRepository</span></span>

## <span data-ttu-id="afad5-104">개요</span><span class="sxs-lookup"><span data-stu-id="afad5-104">SYNOPSIS</span></span>
<span data-ttu-id="afad5-105">PowerShell 리포지토리를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-105">Registers a PowerShell repository.</span></span>

## <span data-ttu-id="afad5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="afad5-106">SYNTAX</span></span>

### <span data-ttu-id="afad5-107">NameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="afad5-107">NameParameterSet (Default)</span></span>

```
Register-PSRepository [-Name] <String> [-SourceLocation] <Uri> [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

### <span data-ttu-id="afad5-108">PSGalleryParameterSet</span><span class="sxs-lookup"><span data-stu-id="afad5-108">PSGalleryParameterSet</span></span>

```
Register-PSRepository [-Default] [-InstallationPolicy <String>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="afad5-109">설명</span><span class="sxs-lookup"><span data-stu-id="afad5-109">DESCRIPTION</span></span>

<span data-ttu-id="afad5-110">`Register-PSRepository`Cmdlet은 PowerShell 모듈에 대 한 기본 리포지토리를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-110">The `Register-PSRepository` cmdlet registers the default repository for PowerShell modules.</span></span> <span data-ttu-id="afad5-111">리포지토리를 등록 한 후에는, 및 cmdlet에서 리포지토리를 참조할 수 있습니다 `Find-Module` `Install-Module` `Publish-Module` .</span><span class="sxs-lookup"><span data-stu-id="afad5-111">After a repository is registered, you can reference it from the `Find-Module`, `Install-Module`, and `Publish-Module` cmdlets.</span></span> <span data-ttu-id="afad5-112">등록 된 리포지토리는 및의 기본 리포지토리가 `Find-Module` 됩니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="afad5-112">The registered repository becomes the default repository in `Find-Module` and `Install-Module`.</span></span>

<span data-ttu-id="afad5-113">등록된 리포지토리는 사용자별 리포지토리입니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-113">Registered repositories are user-specific.</span></span> <span data-ttu-id="afad5-114">시스템 차원의 컨텍스트에는 등록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-114">They are not registered in a system-wide context.</span></span>

<span data-ttu-id="afad5-115">등록 된 각 리포지토리는 **PackageManagementProvider** 매개 변수로 지정 된 oneget 패키지 공급자와 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-115">Each registered repository is associated with a OneGet package provider, which is specified with the **PackageManagementProvider** parameter.</span></span> <span data-ttu-id="afad5-116">각 OneGet 공급자는 특정 리포지토리 형식과 상호 작용 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-116">Each OneGet provider is designed to interact with a specific type of repository.</span></span> <span data-ttu-id="afad5-117">예를 들어 nuget 공급자는 NuGet 기반 리포지토리와 상호 작용 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-117">For example, the NuGet provider is designed to interact with NuGet-based repositories.</span></span> <span data-ttu-id="afad5-118">등록 하는 동안 OneGet 공급자를 지정 하지 않으면 PowerShellGet에서 지정 된 원본 위치를 처리할 수 있는 OneGet 공급자를 찾으려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-118">If a OneGet provider is not specified during registration, PowerShellGet attempts to find a OneGet provider that can handle the specified source location.</span></span>

## <span data-ttu-id="afad5-119">예제</span><span class="sxs-lookup"><span data-stu-id="afad5-119">EXAMPLES</span></span>

### <span data-ttu-id="afad5-120">예제 1: 리포지토리 등록</span><span class="sxs-lookup"><span data-stu-id="afad5-120">Example 1: Register a repository</span></span>

```powershell
$parameters = @{
  Name = "myNuGetSource"
  SourceLocation = "https://www.myget.org/F/powershellgetdemo/api/v2"
  PublishLocation = "https://www.myget.org/F/powershellgetdemo/api/v2/Packages"
  InstallationPolicy = 'Trusted'
}
Register-PSRepository @parameters
Get-PSRepository
```

```Output
Name                SourceLocation          OneGetProvider       InstallationPolicy
----                --------------          --------------       ------------------
PSGallery           http://go.micro...      NuGet                Untrusted
myNuGetSource       https://myget.c...      NuGet                Trusted
```

<span data-ttu-id="afad5-121">첫 번째 명령은 `https://www.myget.org/F/powershellgetdemo/` 현재 사용자에 대 한 리포지토리로 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-121">The first command registers `https://www.myget.org/F/powershellgetdemo/` as a repository for the current user.</span></span> <span data-ttu-id="afad5-122">MyNuGetSource를 등록 한 후 모듈을 검색, 설치 및 게시할 때이를 명시적으로 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-122">After myNuGetSource is registered, you can explicitly reference it when searching for, installing, and publishing modules.</span></span> <span data-ttu-id="afad5-123">**PackageManagementProvider** 매개 변수가 지정 되지 않았기 때문에 리포지토리는 oneget 패키지 공급자와 명시적으로 연결 되지 않으므로 PowerShellGet에서 사용 가능한 패키지 공급자를 폴링하고 NuGet 공급자와 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-123">Because the **PackageManagementProvider** parameter isn't specified, the repository is not explicitly associated with a OneGet package provider, so PowerShellGet polls available package providers and associates it with the NuGet provider.</span></span>

<span data-ttu-id="afad5-124">두 번째 명령은 등록 된 리포지토리를 가져오고 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-124">The second command gets registered repositories and displays the results.</span></span>

## <span data-ttu-id="afad5-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="afad5-125">PARAMETERS</span></span>

### <span data-ttu-id="afad5-126">-Credential</span><span class="sxs-lookup"><span data-stu-id="afad5-126">-Credential</span></span>

<span data-ttu-id="afad5-127">리포지토리를 등록할 수 있는 권한이 있는 계정의 자격 증명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-127">Specifies credentials of an account that has rights to register a repository.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="afad5-128">-Default</span><span class="sxs-lookup"><span data-stu-id="afad5-128">-Default</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PSGalleryParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afad5-129">-InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="afad5-129">-InstallationPolicy</span></span>

<span data-ttu-id="afad5-130">설치 정책을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-130">Specifies the installation policy.</span></span> <span data-ttu-id="afad5-131">유효한 값은 신뢰할 수 있는 신뢰할 수 있는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-131">Valid values are: Trusted, UnTrusted.</span></span> <span data-ttu-id="afad5-132">기본값은 신뢰할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-132">The default value is UnTrusted.</span></span>

<span data-ttu-id="afad5-133">리포지토리의 설치 정책은 해당 리포지토리에서 설치할 때 PowerShell 동작을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-133">A repository's installation policy specifies PowerShell behavior when installing from that repository.</span></span> <span data-ttu-id="afad5-134">신뢰할 수 없는 리포지토리의 모듈을 설치 하는 경우 사용자에 게 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-134">When installing modules from an UnTrusted repository, the user is prompted for confirmation.</span></span>

<span data-ttu-id="afad5-135">Cmdlet을 사용 하 여 **InstallationPolicy** 를 설정할 수 있습니다 `Set-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="afad5-135">You can set the **InstallationPolicy** with the `Set-PSRepository` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Trusted, Untrusted

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afad5-136">-Name</span><span class="sxs-lookup"><span data-stu-id="afad5-136">-Name</span></span>

<span data-ttu-id="afad5-137">등록할 리포지토리의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-137">Specifies the name of the repository to register.</span></span> <span data-ttu-id="afad5-138">이 이름을 사용 하 여 및와 같은 cmdlet에 리포지토리를 지정할 수 있습니다 `Find-Module` `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="afad5-138">You can use this name to specify the repository in cmdlets such as `Find-Module` and `Install-Module`.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afad5-139">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="afad5-139">-PackageManagementProvider</span></span>

<span data-ttu-id="afad5-140">OneGet 패키지 공급자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-140">Specifies a OneGet package provider.</span></span> <span data-ttu-id="afad5-141">이 매개 변수에 대 한 값을 지정 하지 않으면 PowerShellGet은 사용 가능한 패키지 공급자를 폴링하고이 리포지토리를 리포지토리를 처리할 수 있음을 나타내는 첫 번째 패키지 공급자와 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-141">If you don't specify a value for this parameter, PowerShellGet polls available package providers and associates this repository with the first package provider that indicates it can handle the repository.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afad5-142">-프록시</span><span class="sxs-lookup"><span data-stu-id="afad5-142">-Proxy</span></span>

<span data-ttu-id="afad5-143">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-143">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="afad5-144">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="afad5-144">-ProxyCredential</span></span>

<span data-ttu-id="afad5-145">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-145">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="afad5-146">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="afad5-146">-PublishLocation</span></span>

<span data-ttu-id="afad5-147">게시 위치의 URI를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-147">Specifies the URI of the publish location.</span></span> <span data-ttu-id="afad5-148">예를 들어 NuGet 기반 리포지토리의 경우 게시 위치는와 유사 `https://someNuGetUrl.com/api/v2/Packages` 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-148">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afad5-149">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="afad5-149">-ScriptPublishLocation</span></span>

<span data-ttu-id="afad5-150">스크립트 게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-150">Specifies the script publish location.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afad5-151">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="afad5-151">-ScriptSourceLocation</span></span>

<span data-ttu-id="afad5-152">스크립트 원본 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-152">Specifies the script source location.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afad5-153">-로의</span><span class="sxs-lookup"><span data-stu-id="afad5-153">-SourceLocation</span></span>

<span data-ttu-id="afad5-154">이 리포지토리에서 모듈을 검색 하 고 설치 하기 위한 URI를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-154">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="afad5-155">URI는 NuGet 서버 피드 (가장 일반적인 상황), HTTP, HTTPS, FTP 또는 파일 위치가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-155">A URI can be a NuGet server feed (most common situation), HTTP, HTTPS, FTP or file location.</span></span>

<span data-ttu-id="afad5-156">예를 들어 NuGet 기반 리포지토리의 경우 원본 위치는와 유사 `https://someNuGetUrl.com/api/v2` 합니다.</span><span class="sxs-lookup"><span data-stu-id="afad5-156">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afad5-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="afad5-157">CommonParameters</span></span>

<span data-ttu-id="afad5-158">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="afad5-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="afad5-159">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="afad5-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="afad5-160">입력</span><span class="sxs-lookup"><span data-stu-id="afad5-160">INPUTS</span></span>

### <span data-ttu-id="afad5-161">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="afad5-161">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="afad5-162">System.Uri</span><span class="sxs-lookup"><span data-stu-id="afad5-162">System.Uri</span></span>

## <span data-ttu-id="afad5-163">출력</span><span class="sxs-lookup"><span data-stu-id="afad5-163">OUTPUTS</span></span>

### <span data-ttu-id="afad5-164">System.Object</span><span class="sxs-lookup"><span data-stu-id="afad5-164">System.Object</span></span>

## <span data-ttu-id="afad5-165">참고</span><span class="sxs-lookup"><span data-stu-id="afad5-165">NOTES</span></span>

## <span data-ttu-id="afad5-166">관련 링크</span><span class="sxs-lookup"><span data-stu-id="afad5-166">RELATED LINKS</span></span>

[<span data-ttu-id="afad5-167">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="afad5-167">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="afad5-168">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="afad5-168">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="afad5-169">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="afad5-169">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
