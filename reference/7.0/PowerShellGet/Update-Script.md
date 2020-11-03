---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-script?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Script
ms.openlocfilehash: c6034e740f1b4af340f29ee61fdc9922d85b7f2e
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211505"
---
# <span data-ttu-id="ee739-103">Update-Script</span><span class="sxs-lookup"><span data-stu-id="ee739-103">Update-Script</span></span>

## <span data-ttu-id="ee739-104">개요</span><span class="sxs-lookup"><span data-stu-id="ee739-104">SYNOPSIS</span></span>
<span data-ttu-id="ee739-105">스크립트를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-105">Updates a script.</span></span>

## <span data-ttu-id="ee739-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ee739-106">SYNTAX</span></span>

### <span data-ttu-id="ee739-107">모두</span><span class="sxs-lookup"><span data-stu-id="ee739-107">All</span></span>

```
Update-Script [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ee739-108">설명</span><span class="sxs-lookup"><span data-stu-id="ee739-108">DESCRIPTION</span></span>

<span data-ttu-id="ee739-109">`Update-Script`Cmdlet은 로컬 컴퓨터에 설치 된 스크립트를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-109">The `Update-Script` cmdlet updates a script that is installed on the local computer.</span></span> <span data-ttu-id="ee739-110">업데이트 된 스크립트는 설치 된 버전과 동일한 리포지토리에서 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-110">The updated script is downloaded from the same repository as the installed version.</span></span>

## <span data-ttu-id="ee739-111">예제</span><span class="sxs-lookup"><span data-stu-id="ee739-111">EXAMPLES</span></span>

### <span data-ttu-id="ee739-112">예 1: 지정 된 스크립트를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-112">Example 1: Update the specified script</span></span>

<span data-ttu-id="ee739-113">이 예에서는 설치 된 스크립트를 업데이트 하 고 업데이트 된 버전을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-113">This example updates an installed script and displays the updated version.</span></span>

```powershell
Update-Script -Name UpdateManagement-Template -RequiredVersion 1.1
Get-InstalledScript -Name UpdateManagement-Template
```

```Output
Version   Name                       Repository   Description
-------   ----                       ----------   -----------
1.1       UpdateManagement-Template  PSGallery    This is a template script for Update Management...
```

<span data-ttu-id="ee739-114">`Update-Script`**Name** 매개 변수를 사용 하 여 업데이트할 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-114">`Update-Script` uses the **Name** parameter to specify the script to update.</span></span> <span data-ttu-id="ee739-115">**RequiredVersion** 매개 변수는 스크립트 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-115">The **RequiredVersion** parameter specifies the script version.</span></span> <span data-ttu-id="ee739-116">`Get-InstalledScript` 스크립트의 업데이트 된 버전을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-116">`Get-InstalledScript` displays the updated version of the script.</span></span>

## <span data-ttu-id="ee739-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ee739-117">PARAMETERS</span></span>

### <span data-ttu-id="ee739-118">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="ee739-118">-AcceptLicense</span></span>

<span data-ttu-id="ee739-119">패키지에 필요한 경우 설치 하는 동안 사용권 계약에 자동으로 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-119">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="ee739-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="ee739-120">-AllowPrerelease</span></span>

<span data-ttu-id="ee739-121">시험판으로 표시 된 최신 스크립트를 사용 하 여 스크립트를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-121">Allows you to update a script with the newer script marked as a prerelease.</span></span>

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

### <span data-ttu-id="ee739-122">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ee739-122">-Confirm</span></span>

<span data-ttu-id="ee739-123">실행 하기 전에 확인 메시지를 표시 `Update-Script` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-123">Prompts you for confirmation before running `Update-Script`.</span></span>

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

### <span data-ttu-id="ee739-124">-Credential</span><span class="sxs-lookup"><span data-stu-id="ee739-124">-Credential</span></span>

<span data-ttu-id="ee739-125">스크립트를 업데이트할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-125">Specifies a user account that has permission to update a script.</span></span>

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

### <span data-ttu-id="ee739-126">-Force</span><span class="sxs-lookup"><span data-stu-id="ee739-126">-Force</span></span>

<span data-ttu-id="ee739-127">`Update-Script`사용자 확인을 요청 하지 않고 강제로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-127">Forces `Update-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="ee739-128">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="ee739-128">-MaximumVersion</span></span>

<span data-ttu-id="ee739-129">업데이트할 스크립트의 최대 또는 최신 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-129">Specifies the maximum, or newest, version of the script to update.</span></span> <span data-ttu-id="ee739-130">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-130">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="ee739-131">-Name</span><span class="sxs-lookup"><span data-stu-id="ee739-131">-Name</span></span>

<span data-ttu-id="ee739-132">업데이트할 스크립트 이름 또는 스크립트 이름 배열을 하나 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-132">Specifies one script name or an array of script names to update.</span></span>

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

### <span data-ttu-id="ee739-133">-PassThru</span><span class="sxs-lookup"><span data-stu-id="ee739-133">-PassThru</span></span>

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

### <span data-ttu-id="ee739-134">-프록시</span><span class="sxs-lookup"><span data-stu-id="ee739-134">-Proxy</span></span>

<span data-ttu-id="ee739-135">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-135">Specifies a proxy server for the request rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="ee739-136">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="ee739-136">-ProxyCredential</span></span>

<span data-ttu-id="ee739-137">**프록시** 매개 변수로 지정 된 프록시 서버를 사용할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-137">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="ee739-138">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="ee739-138">-RequiredVersion</span></span>

<span data-ttu-id="ee739-139">업데이트할 스크립트의 정확한 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-139">Specifies the exact version number of the script to update.</span></span> <span data-ttu-id="ee739-140">**MinimumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-140">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="ee739-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ee739-141">-WhatIf</span></span>

<span data-ttu-id="ee739-142">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Update-Script` .</span><span class="sxs-lookup"><span data-stu-id="ee739-142">Shows what would happen if `Update-Script` runs.</span></span> <span data-ttu-id="ee739-143">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ee739-143">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="ee739-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ee739-144">CommonParameters</span></span>

<span data-ttu-id="ee739-145">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ee739-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ee739-146">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee739-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ee739-147">입력</span><span class="sxs-lookup"><span data-stu-id="ee739-147">INPUTS</span></span>

### <span data-ttu-id="ee739-148">System.String[]</span><span class="sxs-lookup"><span data-stu-id="ee739-148">System.String[]</span></span>

### <span data-ttu-id="ee739-149">System.String</span><span class="sxs-lookup"><span data-stu-id="ee739-149">System.String</span></span>

### <span data-ttu-id="ee739-150">System.Uri</span><span class="sxs-lookup"><span data-stu-id="ee739-150">System.Uri</span></span>

### <span data-ttu-id="ee739-151">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="ee739-151">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="ee739-152">출력</span><span class="sxs-lookup"><span data-stu-id="ee739-152">OUTPUTS</span></span>

### <span data-ttu-id="ee739-153">System.Object</span><span class="sxs-lookup"><span data-stu-id="ee739-153">System.Object</span></span>

## <span data-ttu-id="ee739-154">참고</span><span class="sxs-lookup"><span data-stu-id="ee739-154">NOTES</span></span>

## <span data-ttu-id="ee739-155">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ee739-155">RELATED LINKS</span></span>

[<span data-ttu-id="ee739-156">Find-Script</span><span class="sxs-lookup"><span data-stu-id="ee739-156">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="ee739-157">Install-Script</span><span class="sxs-lookup"><span data-stu-id="ee739-157">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="ee739-158">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="ee739-158">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="ee739-159">Save-Script</span><span class="sxs-lookup"><span data-stu-id="ee739-159">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="ee739-160">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="ee739-160">Uninstall-Script</span></span>](Uninstall-Script.md)
