---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedscript?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledScript
ms.openlocfilehash: fe5fc0feb34fda87dab987f33140992a346017a1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599605"
---
# <span data-ttu-id="c712e-102">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="c712e-102">Get-InstalledScript</span></span>

## <span data-ttu-id="c712e-103">개요</span><span class="sxs-lookup"><span data-stu-id="c712e-103">SYNOPSIS</span></span>
<span data-ttu-id="c712e-104">설치 된 스크립트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c712e-104">Gets an installed script.</span></span>

## <span data-ttu-id="c712e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c712e-105">SYNTAX</span></span>

```
Get-InstalledScript [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="c712e-106">설명</span><span class="sxs-lookup"><span data-stu-id="c712e-106">DESCRIPTION</span></span>

<span data-ttu-id="c712e-107">**Get-installedscript** Cmdlet은 CurrentUser 및 AllUsers 범위에 대해 설치 된 스크립트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c712e-107">The **Get-InstalledScript** cmdlet gets installed scripts for CurrentUser and AllUsers scopes.</span></span>

## <span data-ttu-id="c712e-108">예제</span><span class="sxs-lookup"><span data-stu-id="c712e-108">EXAMPLES</span></span>

### <span data-ttu-id="c712e-109">예제 1: 설치 된 모든 스크립트 가져오기</span><span class="sxs-lookup"><span data-stu-id="c712e-109">Example 1: Get all installed scripts</span></span>

```
PS C:\> Get-InstalledScript
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     local1               Description for the Script-WithDependencies1 script
```

<span data-ttu-id="c712e-110">이 명령은 설치 된 모든 스크립트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c712e-110">This command gets all installed scripts.</span></span>

### <span data-ttu-id="c712e-111">예제 2: 이름별로 설치 된 스크립트 가져오기</span><span class="sxs-lookup"><span data-stu-id="c712e-111">Example 2: Get installed scripts by name</span></span>

```
PS C:\> Get-InstalledScript -Name "Required-Scri*"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="c712e-112">이 명령은 이름이 필수-스크립팅 (로 시작 하는 스크립트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c712e-112">This command gets scripts where the name begins with Required-Scri.</span></span>

## <span data-ttu-id="c712e-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c712e-113">PARAMETERS</span></span>

### <span data-ttu-id="c712e-114">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="c712e-114">-AllowPrerelease</span></span>

<span data-ttu-id="c712e-115">시험판으로 표시 된 결과 스크립트에를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c712e-115">Includes in the results scripts marked as a prerelease.</span></span>

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

### <span data-ttu-id="c712e-116">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="c712e-116">-MaximumVersion</span></span>

<span data-ttu-id="c712e-117">가져올 스크립트의 최대 또는 최신 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c712e-117">Specifies the maximum, or latest, version of a script to get.</span></span>
<span data-ttu-id="c712e-118">*MaximumVersion* 및 *RequiredVersion* 매개 변수는 함께 사용할 수 없습니다. 동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c712e-118">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="c712e-119">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="c712e-119">-MinimumVersion</span></span>

<span data-ttu-id="c712e-120">가져올 스크립트의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c712e-120">Specifies the minimum version of a script to get.</span></span>
<span data-ttu-id="c712e-121">*MinimumVersion* 및 *RequiredVersion* 매개 변수는 함께 사용할 수 없습니다. 동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c712e-121">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="c712e-122">-Name</span><span class="sxs-lookup"><span data-stu-id="c712e-122">-Name</span></span>

<span data-ttu-id="c712e-123">가져올 스크립트의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c712e-123">Specifies an array of names of scripts to get.</span></span>
<span data-ttu-id="c712e-124">와일드 카드가 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c712e-124">Wildcards are accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="c712e-125">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="c712e-125">-RequiredVersion</span></span>

<span data-ttu-id="c712e-126">가져올 스크립트의 정확한 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c712e-126">Specifies the exact version of a script to get.</span></span>

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

### <span data-ttu-id="c712e-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c712e-127">CommonParameters</span></span>

<span data-ttu-id="c712e-128">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c712e-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c712e-129">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c712e-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c712e-130">입력</span><span class="sxs-lookup"><span data-stu-id="c712e-130">INPUTS</span></span>

### <span data-ttu-id="c712e-131">System.String[]</span><span class="sxs-lookup"><span data-stu-id="c712e-131">System.String[]</span></span>

### <span data-ttu-id="c712e-132">System.String</span><span class="sxs-lookup"><span data-stu-id="c712e-132">System.String</span></span>

## <span data-ttu-id="c712e-133">출력</span><span class="sxs-lookup"><span data-stu-id="c712e-133">OUTPUTS</span></span>

### <span data-ttu-id="c712e-134">System.Object</span><span class="sxs-lookup"><span data-stu-id="c712e-134">System.Object</span></span>

## <span data-ttu-id="c712e-135">참고</span><span class="sxs-lookup"><span data-stu-id="c712e-135">NOTES</span></span>

## <span data-ttu-id="c712e-136">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c712e-136">RELATED LINKS</span></span>

[<span data-ttu-id="c712e-137">Install-Script</span><span class="sxs-lookup"><span data-stu-id="c712e-137">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="c712e-138">제거-스크립트</span><span class="sxs-lookup"><span data-stu-id="c712e-138">Uninstall-Script</span></span>](Uninstall-Script.md)

