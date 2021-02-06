---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSRepository
ms.openlocfilehash: 66f840d99b107da22b6771e6327ab68d33a1b368
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601267"
---
# <span data-ttu-id="6b913-102">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="6b913-102">Get-PSRepository</span></span>

## <span data-ttu-id="6b913-103">개요</span><span class="sxs-lookup"><span data-stu-id="6b913-103">SYNOPSIS</span></span>
<span data-ttu-id="6b913-104">PowerShell 리포지토리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6b913-104">Gets PowerShell repositories.</span></span>

## <span data-ttu-id="6b913-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6b913-105">SYNTAX</span></span>

```
Get-PSRepository [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="6b913-106">설명</span><span class="sxs-lookup"><span data-stu-id="6b913-106">DESCRIPTION</span></span>

<span data-ttu-id="6b913-107">**Set-psrepository** cmdlet은 현재 사용자에 대해 등록 된 PowerShell 모듈 리포지토리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6b913-107">The **Get-PSRepository** cmdlet gets PowerShell module repositories that are registered for the current user.</span></span>

## <span data-ttu-id="6b913-108">예제</span><span class="sxs-lookup"><span data-stu-id="6b913-108">EXAMPLES</span></span>

### <span data-ttu-id="6b913-109">예제 1: 모든 모듈 리포지토리 가져오기</span><span class="sxs-lookup"><span data-stu-id="6b913-109">Example 1: Get all module repositories</span></span>

```
PS C:\> Get-PSRepository
Name                                     SourceLocation                                     OneGetProvider       InstallationPolicy
----                                     --------------                                     --------------       ------------------
PSGallery                                http://go.micro...                                 NuGet                Untrusted
myNuGetSource                            https://myget.c...                                 NuGet                Trusted
```

<span data-ttu-id="6b913-110">이 명령은 현재 사용자에 대해 등록 된 모든 모듈 리포지토리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6b913-110">This command gets all module repositories registered for the current user.</span></span>

### <span data-ttu-id="6b913-111">예 2: 이름별로 모듈 리포지토리 가져오기</span><span class="sxs-lookup"><span data-stu-id="6b913-111">Example 2: Get module repositories by name</span></span>

```
PS C:\> Get-PSRepository -Name "*NuGet*"
```

<span data-ttu-id="6b913-112">이 명령은 이름에 NuGet이 포함 된 모든 모듈 리포지토리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6b913-112">This command gets all module repositories that include NuGet in their names.</span></span>

### <span data-ttu-id="6b913-113">예 3: 모듈 리포지토리 가져오기 및 출력 형식 지정</span><span class="sxs-lookup"><span data-stu-id="6b913-113">Example 3: Get a module repository and format the output</span></span>

```
PS C:\> Get-PSRepository -Name "Local01" | Format-List * -Force
Name                      : local01
SourceLocation            : http://manikb-dev:8765/api/v2/
Trusted                   : True
Registered                : True
InstallationPolicy        : Trusted
PackageManagementProvider : NuGet
PublishLocation           : http://pattif-dev:8765/api/v2/package/
ScriptSourceLocation      : http://pattif-dev:8765/api/v2/artifacts/psscript
ScriptPublishLocation     : http://pattif-dev:8765/api/v2/package/
ProviderOptions           : {}
```

<span data-ttu-id="6b913-114">이 명령은 Local01 이라는 리포지토리를 가져온 다음 파이프라인 연산자를 사용 하 여 해당 개체를 Format-List cmdlet에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b913-114">This command gets the repository named Local01 and uses the pipeline operator to pass that object to the Format-List cmdlet.</span></span>

## <span data-ttu-id="6b913-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6b913-115">PARAMETERS</span></span>

### <span data-ttu-id="6b913-116">-Name</span><span class="sxs-lookup"><span data-stu-id="6b913-116">-Name</span></span>

<span data-ttu-id="6b913-117">가져올 리포지토리의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b913-117">Specifies the names of the repositories to get.</span></span>

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

### <span data-ttu-id="6b913-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6b913-118">CommonParameters</span></span>

<span data-ttu-id="6b913-119">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6b913-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6b913-120">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b913-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6b913-121">입력</span><span class="sxs-lookup"><span data-stu-id="6b913-121">INPUTS</span></span>

### <span data-ttu-id="6b913-122">System.String[]</span><span class="sxs-lookup"><span data-stu-id="6b913-122">System.String[]</span></span>

## <span data-ttu-id="6b913-123">출력</span><span class="sxs-lookup"><span data-stu-id="6b913-123">OUTPUTS</span></span>

### <span data-ttu-id="6b913-124">System.Object</span><span class="sxs-lookup"><span data-stu-id="6b913-124">System.Object</span></span>

## <span data-ttu-id="6b913-125">참고</span><span class="sxs-lookup"><span data-stu-id="6b913-125">NOTES</span></span>

## <span data-ttu-id="6b913-126">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6b913-126">RELATED LINKS</span></span>

[<span data-ttu-id="6b913-127">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="6b913-127">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="6b913-128">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="6b913-128">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="6b913-129">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="6b913-129">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)

