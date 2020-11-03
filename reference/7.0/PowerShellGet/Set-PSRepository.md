---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/set-psrepository?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSRepository
ms.openlocfilehash: 277bfc0ae4662e0c822ae7c227490eaf887c8ecb
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93209946"
---
# <span data-ttu-id="75c9a-103">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="75c9a-103">Set-PSRepository</span></span>

## <span data-ttu-id="75c9a-104">개요</span><span class="sxs-lookup"><span data-stu-id="75c9a-104">SYNOPSIS</span></span>
<span data-ttu-id="75c9a-105">등록 된 리포지토리에 대 한 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="75c9a-105">Sets values for a registered repository.</span></span>

## <span data-ttu-id="75c9a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="75c9a-106">SYNTAX</span></span>

```
Set-PSRepository [-Name] <String> [[-SourceLocation] <Uri>] [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

## <span data-ttu-id="75c9a-107">설명</span><span class="sxs-lookup"><span data-stu-id="75c9a-107">DESCRIPTION</span></span>

<span data-ttu-id="75c9a-108">`Set-PSRepository`Cmdlet은 등록 된 모듈 리포지토리의 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="75c9a-108">The `Set-PSRepository` cmdlet sets values for a registered module repository.</span></span> <span data-ttu-id="75c9a-109">설정은 현재 사용자에 게 영구적 이며 해당 사용자에 대해 설치 된 모든 버전의 PowerShell에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75c9a-109">The settings are persistent for the current user and apply to all versions of PowerShell installed for that user.</span></span>

## <span data-ttu-id="75c9a-110">예제</span><span class="sxs-lookup"><span data-stu-id="75c9a-110">EXAMPLES</span></span>

### <span data-ttu-id="75c9a-111">예제 1: 리포지토리에 대 한 설치 정책 설정</span><span class="sxs-lookup"><span data-stu-id="75c9a-111">Example 1: Set the installation policy for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -InstallationPolicy Trusted
```

<span data-ttu-id="75c9a-112">이 명령은 **Myinternalsource** 리포지토리의 설치 정책을 **신뢰할** 수 있는로 설정 하므로 해당 원본에서 모듈을 설치 하기 전에 메시지가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="75c9a-112">This command sets the installation policy for the **myInternalSource** repository to **Trusted** , so that you are not prompted before installing modules from that source.</span></span>

### <span data-ttu-id="75c9a-113">예 2: 리포지토리에 대 한 원본 및 게시 위치 설정</span><span class="sxs-lookup"><span data-stu-id="75c9a-113">Example 2: Set the source and publish locations for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -SourceLocation 'https://someNuGetUrl.com/api/v2' -PublishLocation 'https://someNuGetUrl.com/api/v2/packages'
```

<span data-ttu-id="75c9a-114">이 명령은 **Myinternalsource** 의 원본 위치 및 게시 위치를 지정 된 uri로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="75c9a-114">This command sets the source location and publish location for **myInternalSource** to the specified URIs.</span></span>

## <span data-ttu-id="75c9a-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="75c9a-115">PARAMETERS</span></span>

### <span data-ttu-id="75c9a-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="75c9a-116">-Credential</span></span>

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

### <span data-ttu-id="75c9a-117">-InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="75c9a-117">-InstallationPolicy</span></span>

<span data-ttu-id="75c9a-118">설치 정책을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="75c9a-118">Specifies the installation policy.</span></span> <span data-ttu-id="75c9a-119">유효한 값은 **신뢰할 수 있는 신뢰할 수 있는** **값입니다.**</span><span class="sxs-lookup"><span data-stu-id="75c9a-119">Valid values are: **Trusted** , **Untrusted** .</span></span>

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

### <span data-ttu-id="75c9a-120">-Name</span><span class="sxs-lookup"><span data-stu-id="75c9a-120">-Name</span></span>

<span data-ttu-id="75c9a-121">리포지토리의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="75c9a-121">Specifies the name of the repository.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="75c9a-122">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="75c9a-122">-PackageManagementProvider</span></span>

<span data-ttu-id="75c9a-123">패키지 관리 공급자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="75c9a-123">Specifies the package management provider.</span></span>

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

### <span data-ttu-id="75c9a-124">-프록시</span><span class="sxs-lookup"><span data-stu-id="75c9a-124">-Proxy</span></span>

<span data-ttu-id="75c9a-125">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="75c9a-125">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="75c9a-126">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="75c9a-126">-ProxyCredential</span></span>

<span data-ttu-id="75c9a-127">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="75c9a-127">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="75c9a-128">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="75c9a-128">-PublishLocation</span></span>

<span data-ttu-id="75c9a-129">게시 위치의 URI를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="75c9a-129">Specifies the URI of the publish location.</span></span> <span data-ttu-id="75c9a-130">예를 들어 NuGet 기반 리포지토리의 경우 게시 위치는와 유사 `https://someNuGetUrl.com/api/v2/Packages` 합니다.</span><span class="sxs-lookup"><span data-stu-id="75c9a-130">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

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

### <span data-ttu-id="75c9a-131">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="75c9a-131">-ScriptPublishLocation</span></span>

<span data-ttu-id="75c9a-132">스크립트 게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="75c9a-132">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="75c9a-133">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="75c9a-133">-ScriptSourceLocation</span></span>

<span data-ttu-id="75c9a-134">스크립트 원본 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="75c9a-134">Specifies the script source location.</span></span>

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

### <span data-ttu-id="75c9a-135">-로의</span><span class="sxs-lookup"><span data-stu-id="75c9a-135">-SourceLocation</span></span>

<span data-ttu-id="75c9a-136">이 리포지토리에서 모듈을 검색 하 고 설치 하기 위한 URI를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="75c9a-136">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="75c9a-137">예를 들어 NuGet 기반 리포지토리의 경우 원본 위치는와 유사 `https://someNuGetUrl.com/api/v2` 합니다.</span><span class="sxs-lookup"><span data-stu-id="75c9a-137">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="75c9a-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="75c9a-138">CommonParameters</span></span>

<span data-ttu-id="75c9a-139">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="75c9a-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="75c9a-140">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="75c9a-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="75c9a-141">입력</span><span class="sxs-lookup"><span data-stu-id="75c9a-141">INPUTS</span></span>

### <span data-ttu-id="75c9a-142">System.String</span><span class="sxs-lookup"><span data-stu-id="75c9a-142">System.String</span></span>

### <span data-ttu-id="75c9a-143">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="75c9a-143">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="75c9a-144">System.Uri</span><span class="sxs-lookup"><span data-stu-id="75c9a-144">System.Uri</span></span>

## <span data-ttu-id="75c9a-145">출력</span><span class="sxs-lookup"><span data-stu-id="75c9a-145">OUTPUTS</span></span>

### <span data-ttu-id="75c9a-146">System.Object</span><span class="sxs-lookup"><span data-stu-id="75c9a-146">System.Object</span></span>

## <span data-ttu-id="75c9a-147">참고</span><span class="sxs-lookup"><span data-stu-id="75c9a-147">NOTES</span></span>

## <span data-ttu-id="75c9a-148">관련 링크</span><span class="sxs-lookup"><span data-stu-id="75c9a-148">RELATED LINKS</span></span>

[<span data-ttu-id="75c9a-149">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="75c9a-149">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="75c9a-150">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="75c9a-150">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="75c9a-151">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="75c9a-151">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
