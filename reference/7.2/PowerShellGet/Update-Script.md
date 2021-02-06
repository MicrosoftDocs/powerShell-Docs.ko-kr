---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Script
ms.openlocfilehash: 0fa537e463464fe055ea14aeab05cbb3ac5d1012
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99602443"
---
# <span data-ttu-id="5469e-102">Update-Script</span><span class="sxs-lookup"><span data-stu-id="5469e-102">Update-Script</span></span>

## <span data-ttu-id="5469e-103">개요</span><span class="sxs-lookup"><span data-stu-id="5469e-103">SYNOPSIS</span></span>
<span data-ttu-id="5469e-104">스크립트를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-104">Updates a script.</span></span>

## <span data-ttu-id="5469e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5469e-105">SYNTAX</span></span>

### <span data-ttu-id="5469e-106">모두</span><span class="sxs-lookup"><span data-stu-id="5469e-106">All</span></span>

```
Update-Script [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5469e-107">설명</span><span class="sxs-lookup"><span data-stu-id="5469e-107">DESCRIPTION</span></span>

<span data-ttu-id="5469e-108">`Update-Script`Cmdlet은 로컬 컴퓨터에 설치 된 스크립트를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-108">The `Update-Script` cmdlet updates a script that is installed on the local computer.</span></span> <span data-ttu-id="5469e-109">업데이트 된 스크립트는 설치 된 버전과 동일한 리포지토리에서 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-109">The updated script is downloaded from the same repository as the installed version.</span></span>

## <span data-ttu-id="5469e-110">예제</span><span class="sxs-lookup"><span data-stu-id="5469e-110">EXAMPLES</span></span>

### <span data-ttu-id="5469e-111">예 1: 지정 된 스크립트를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-111">Example 1: Update the specified script</span></span>

<span data-ttu-id="5469e-112">이 예에서는 설치 된 스크립트를 업데이트 하 고 업데이트 된 버전을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-112">This example updates an installed script and displays the updated version.</span></span>

```powershell
Update-Script -Name UpdateManagement-Template -RequiredVersion 1.1
Get-InstalledScript -Name UpdateManagement-Template
```

```Output
Version   Name                       Repository   Description
-------   ----                       ----------   -----------
1.1       UpdateManagement-Template  PSGallery    This is a template script for Update Management...
```

<span data-ttu-id="5469e-113">`Update-Script`**Name** 매개 변수를 사용 하 여 업데이트할 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-113">`Update-Script` uses the **Name** parameter to specify the script to update.</span></span> <span data-ttu-id="5469e-114">**RequiredVersion** 매개 변수는 스크립트 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-114">The **RequiredVersion** parameter specifies the script version.</span></span> <span data-ttu-id="5469e-115">`Get-InstalledScript` 스크립트의 업데이트 된 버전을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-115">`Get-InstalledScript` displays the updated version of the script.</span></span>

## <span data-ttu-id="5469e-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5469e-116">PARAMETERS</span></span>

### <span data-ttu-id="5469e-117">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="5469e-117">-AcceptLicense</span></span>

<span data-ttu-id="5469e-118">패키지에 필요한 경우 설치 하는 동안 사용권 계약에 자동으로 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-118">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="5469e-119">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="5469e-119">-AllowPrerelease</span></span>

<span data-ttu-id="5469e-120">시험판으로 표시 된 최신 스크립트를 사용 하 여 스크립트를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-120">Allows you to update a script with the newer script marked as a prerelease.</span></span>

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

### <span data-ttu-id="5469e-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5469e-121">-Confirm</span></span>

<span data-ttu-id="5469e-122">실행 하기 전에 확인 메시지를 표시 `Update-Script` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-122">Prompts you for confirmation before running `Update-Script`.</span></span>

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

### <span data-ttu-id="5469e-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="5469e-123">-Credential</span></span>

<span data-ttu-id="5469e-124">스크립트를 업데이트할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-124">Specifies a user account that has permission to update a script.</span></span>

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

### <span data-ttu-id="5469e-125">-Force</span><span class="sxs-lookup"><span data-stu-id="5469e-125">-Force</span></span>

<span data-ttu-id="5469e-126">`Update-Script`사용자 확인을 요청 하지 않고 강제로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-126">Forces `Update-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="5469e-127">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="5469e-127">-MaximumVersion</span></span>

<span data-ttu-id="5469e-128">업데이트할 스크립트의 최대 또는 최신 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-128">Specifies the maximum, or newest, version of the script to update.</span></span> <span data-ttu-id="5469e-129">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-129">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5469e-130">-Name</span><span class="sxs-lookup"><span data-stu-id="5469e-130">-Name</span></span>

<span data-ttu-id="5469e-131">업데이트할 스크립트 이름 또는 스크립트 이름 배열을 하나 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-131">Specifies one script name or an array of script names to update.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5469e-132">-PassThru</span><span class="sxs-lookup"><span data-stu-id="5469e-132">-PassThru</span></span>

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

### <span data-ttu-id="5469e-133">-프록시</span><span class="sxs-lookup"><span data-stu-id="5469e-133">-Proxy</span></span>

<span data-ttu-id="5469e-134">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-134">Specifies a proxy server for the request rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="5469e-135">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="5469e-135">-ProxyCredential</span></span>

<span data-ttu-id="5469e-136">**프록시** 매개 변수로 지정 된 프록시 서버를 사용할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-136">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="5469e-137">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="5469e-137">-RequiredVersion</span></span>

<span data-ttu-id="5469e-138">업데이트할 스크립트의 정확한 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-138">Specifies the exact version number of the script to update.</span></span> <span data-ttu-id="5469e-139">**MinimumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-139">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5469e-140">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5469e-140">-WhatIf</span></span>

<span data-ttu-id="5469e-141">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Update-Script` .</span><span class="sxs-lookup"><span data-stu-id="5469e-141">Shows what would happen if `Update-Script` runs.</span></span> <span data-ttu-id="5469e-142">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-142">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="5469e-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5469e-143">CommonParameters</span></span>

<span data-ttu-id="5469e-144">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5469e-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5469e-145">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5469e-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5469e-146">입력</span><span class="sxs-lookup"><span data-stu-id="5469e-146">INPUTS</span></span>

### <span data-ttu-id="5469e-147">System.String[]</span><span class="sxs-lookup"><span data-stu-id="5469e-147">System.String[]</span></span>

### <span data-ttu-id="5469e-148">System.String</span><span class="sxs-lookup"><span data-stu-id="5469e-148">System.String</span></span>

### <span data-ttu-id="5469e-149">System.Uri</span><span class="sxs-lookup"><span data-stu-id="5469e-149">System.Uri</span></span>

### <span data-ttu-id="5469e-150">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="5469e-150">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="5469e-151">출력</span><span class="sxs-lookup"><span data-stu-id="5469e-151">OUTPUTS</span></span>

### <span data-ttu-id="5469e-152">System.Object</span><span class="sxs-lookup"><span data-stu-id="5469e-152">System.Object</span></span>

## <span data-ttu-id="5469e-153">참고</span><span class="sxs-lookup"><span data-stu-id="5469e-153">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5469e-154">2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-154">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="5469e-155">TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-155">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="5469e-156">다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5469e-156">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="5469e-157">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5469e-157">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="5469e-158">관련 링크</span><span class="sxs-lookup"><span data-stu-id="5469e-158">RELATED LINKS</span></span>

[<span data-ttu-id="5469e-159">Find-Script</span><span class="sxs-lookup"><span data-stu-id="5469e-159">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="5469e-160">Install-Script</span><span class="sxs-lookup"><span data-stu-id="5469e-160">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="5469e-161">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="5469e-161">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="5469e-162">Save-Script</span><span class="sxs-lookup"><span data-stu-id="5469e-162">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="5469e-163">제거-스크립트</span><span class="sxs-lookup"><span data-stu-id="5469e-163">Uninstall-Script</span></span>](Uninstall-Script.md)
