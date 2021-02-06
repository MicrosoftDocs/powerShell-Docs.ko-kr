---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/set-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSRepository
ms.openlocfilehash: d6f3901ba389ff910dcc808d2e4296032617052c
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99600428"
---
# <span data-ttu-id="1f641-102">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="1f641-102">Set-PSRepository</span></span>

## <span data-ttu-id="1f641-103">개요</span><span class="sxs-lookup"><span data-stu-id="1f641-103">SYNOPSIS</span></span>
<span data-ttu-id="1f641-104">등록 된 리포지토리에 대 한 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-104">Sets values for a registered repository.</span></span>

## <span data-ttu-id="1f641-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1f641-105">SYNTAX</span></span>

```
Set-PSRepository [-Name] <String> [[-SourceLocation] <Uri>] [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

## <span data-ttu-id="1f641-106">설명</span><span class="sxs-lookup"><span data-stu-id="1f641-106">DESCRIPTION</span></span>

<span data-ttu-id="1f641-107">`Set-PSRepository`Cmdlet은 등록 된 모듈 리포지토리의 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-107">The `Set-PSRepository` cmdlet sets values for a registered module repository.</span></span> <span data-ttu-id="1f641-108">설정은 현재 사용자에 게 영구적 이며 해당 사용자에 대해 설치 된 모든 버전의 PowerShell에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-108">The settings are persistent for the current user and apply to all versions of PowerShell installed for that user.</span></span>

## <span data-ttu-id="1f641-109">예제</span><span class="sxs-lookup"><span data-stu-id="1f641-109">EXAMPLES</span></span>

### <span data-ttu-id="1f641-110">예제 1: 리포지토리에 대 한 설치 정책 설정</span><span class="sxs-lookup"><span data-stu-id="1f641-110">Example 1: Set the installation policy for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -InstallationPolicy Trusted
```

<span data-ttu-id="1f641-111">이 명령은 **Myinternalsource** 리포지토리의 설치 정책을 **신뢰할** 수 있는로 설정 하므로 해당 원본에서 모듈을 설치 하기 전에 메시지가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-111">This command sets the installation policy for the **myInternalSource** repository to **Trusted**, so that you are not prompted before installing modules from that source.</span></span>

### <span data-ttu-id="1f641-112">예 2: 리포지토리에 대 한 원본 및 게시 위치 설정</span><span class="sxs-lookup"><span data-stu-id="1f641-112">Example 2: Set the source and publish locations for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -SourceLocation 'https://someNuGetUrl.com/api/v2' -PublishLocation 'https://someNuGetUrl.com/api/v2/packages'
```

<span data-ttu-id="1f641-113">이 명령은 **Myinternalsource** 의 원본 위치 및 게시 위치를 지정 된 uri로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-113">This command sets the source location and publish location for **myInternalSource** to the specified URIs.</span></span>

## <span data-ttu-id="1f641-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1f641-114">PARAMETERS</span></span>

### <span data-ttu-id="1f641-115">-Credential</span><span class="sxs-lookup"><span data-stu-id="1f641-115">-Credential</span></span>

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

### <span data-ttu-id="1f641-116">-InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="1f641-116">-InstallationPolicy</span></span>

<span data-ttu-id="1f641-117">설치 정책을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-117">Specifies the installation policy.</span></span> <span data-ttu-id="1f641-118">유효한 값은 **신뢰할 수 있는 신뢰할 수 있는** **값입니다.**</span><span class="sxs-lookup"><span data-stu-id="1f641-118">Valid values are: **Trusted**, **Untrusted**.</span></span>

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

### <span data-ttu-id="1f641-119">-Name</span><span class="sxs-lookup"><span data-stu-id="1f641-119">-Name</span></span>

<span data-ttu-id="1f641-120">리포지토리의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-120">Specifies the name of the repository.</span></span>

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

### <span data-ttu-id="1f641-121">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="1f641-121">-PackageManagementProvider</span></span>

<span data-ttu-id="1f641-122">패키지 관리 공급자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-122">Specifies the package management provider.</span></span>

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

### <span data-ttu-id="1f641-123">-프록시</span><span class="sxs-lookup"><span data-stu-id="1f641-123">-Proxy</span></span>

<span data-ttu-id="1f641-124">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-124">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="1f641-125">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="1f641-125">-ProxyCredential</span></span>

<span data-ttu-id="1f641-126">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-126">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="1f641-127">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="1f641-127">-PublishLocation</span></span>

<span data-ttu-id="1f641-128">게시 위치의 URI를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-128">Specifies the URI of the publish location.</span></span> <span data-ttu-id="1f641-129">예를 들어 NuGet 기반 리포지토리의 경우 게시 위치는와 유사 `https://someNuGetUrl.com/api/v2/Packages` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-129">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

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

### <span data-ttu-id="1f641-130">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="1f641-130">-ScriptPublishLocation</span></span>

<span data-ttu-id="1f641-131">스크립트 게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-131">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="1f641-132">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="1f641-132">-ScriptSourceLocation</span></span>

<span data-ttu-id="1f641-133">스크립트 원본 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-133">Specifies the script source location.</span></span>

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

### <span data-ttu-id="1f641-134">-로의</span><span class="sxs-lookup"><span data-stu-id="1f641-134">-SourceLocation</span></span>

<span data-ttu-id="1f641-135">이 리포지토리에서 모듈을 검색 하 고 설치 하기 위한 URI를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-135">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="1f641-136">예를 들어 NuGet 기반 리포지토리의 경우 원본 위치는와 유사 `https://someNuGetUrl.com/api/v2` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-136">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

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

### <span data-ttu-id="1f641-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1f641-137">CommonParameters</span></span>

<span data-ttu-id="1f641-138">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1f641-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1f641-139">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1f641-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1f641-140">입력</span><span class="sxs-lookup"><span data-stu-id="1f641-140">INPUTS</span></span>

### <span data-ttu-id="1f641-141">System.String</span><span class="sxs-lookup"><span data-stu-id="1f641-141">System.String</span></span>

### <span data-ttu-id="1f641-142">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="1f641-142">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="1f641-143">System.Uri</span><span class="sxs-lookup"><span data-stu-id="1f641-143">System.Uri</span></span>

## <span data-ttu-id="1f641-144">출력</span><span class="sxs-lookup"><span data-stu-id="1f641-144">OUTPUTS</span></span>

### <span data-ttu-id="1f641-145">System.Object</span><span class="sxs-lookup"><span data-stu-id="1f641-145">System.Object</span></span>

## <span data-ttu-id="1f641-146">참고</span><span class="sxs-lookup"><span data-stu-id="1f641-146">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1f641-147">2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-147">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="1f641-148">TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-148">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="1f641-149">다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1f641-149">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="1f641-150">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1f641-150">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="1f641-151">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1f641-151">RELATED LINKS</span></span>

[<span data-ttu-id="1f641-152">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="1f641-152">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="1f641-153">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="1f641-153">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="1f641-154">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="1f641-154">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
