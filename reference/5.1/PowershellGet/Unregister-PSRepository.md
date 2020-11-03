---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/unregister-psrepository?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSRepository
ms.openlocfilehash: 0d98d7bbb26d5a50542f0e125e912ea6333714c1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215178"
---
# <span data-ttu-id="b0c45-103">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="b0c45-103">Unregister-PSRepository</span></span>

## <span data-ttu-id="b0c45-104">개요</span><span class="sxs-lookup"><span data-stu-id="b0c45-104">SYNOPSIS</span></span>
<span data-ttu-id="b0c45-105">리포지토리 등록을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="b0c45-105">Unregisters a repository.</span></span>

## <span data-ttu-id="b0c45-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b0c45-106">SYNTAX</span></span>

```
Unregister-PSRepository [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="b0c45-107">설명</span><span class="sxs-lookup"><span data-stu-id="b0c45-107">DESCRIPTION</span></span>

<span data-ttu-id="b0c45-108">`Unregister-PSRepository`Cmdlet은 현재 사용자의 리포지토리 등록을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0c45-108">The `Unregister-PSRepository` cmdlet unregisters a repository for the current user.</span></span>

## <span data-ttu-id="b0c45-109">예제</span><span class="sxs-lookup"><span data-stu-id="b0c45-109">EXAMPLES</span></span>

### <span data-ttu-id="b0c45-110">예제 1: 리포지토리 등록 취소</span><span class="sxs-lookup"><span data-stu-id="b0c45-110">Example 1: Unregister a repository</span></span>

<span data-ttu-id="b0c45-111">이 예제에서는 myNuGetSource 이라는 리포지토리의 등록을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0c45-111">This example unregisters the repository named myNuGetSource.</span></span>

```powershell
Unregister-PSRepository -Name "myNuGetSource"
```

### <span data-ttu-id="b0c45-112">예제 2: 모든 리포지토리 등록 취소</span><span class="sxs-lookup"><span data-stu-id="b0c45-112">Example 2: Unregister all repositories</span></span>

<span data-ttu-id="b0c45-113">이 예제에서는 `Get-PSRepository` 를 사용 하 여 등록 된 모든 리포지토리를 가져온 다음 파이프라인 연산자를 사용 하 여이를 `Unregister-PSRepository` 등록 취소 하기 위해 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0c45-113">This example uses `Get-PSRepository` to get all registered repositories, and uses the pipeline operator to pass them to `Unregister-PSRepository` to unregister them.</span></span>

```powershell
Get-PSRepository | Unregister-PSRepository
```

## <span data-ttu-id="b0c45-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b0c45-114">PARAMETERS</span></span>

### <span data-ttu-id="b0c45-115">-Name</span><span class="sxs-lookup"><span data-stu-id="b0c45-115">-Name</span></span>

<span data-ttu-id="b0c45-116">제거할 리포지토리의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0c45-116">Specifies an array of names of the repositories to remove.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b0c45-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b0c45-117">CommonParameters</span></span>

<span data-ttu-id="b0c45-118">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b0c45-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b0c45-119">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b0c45-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b0c45-120">입력</span><span class="sxs-lookup"><span data-stu-id="b0c45-120">INPUTS</span></span>

### <span data-ttu-id="b0c45-121">System.String[]</span><span class="sxs-lookup"><span data-stu-id="b0c45-121">System.String[]</span></span>

## <span data-ttu-id="b0c45-122">출력</span><span class="sxs-lookup"><span data-stu-id="b0c45-122">OUTPUTS</span></span>

### <span data-ttu-id="b0c45-123">System.Object</span><span class="sxs-lookup"><span data-stu-id="b0c45-123">System.Object</span></span>

## <span data-ttu-id="b0c45-124">참고</span><span class="sxs-lookup"><span data-stu-id="b0c45-124">NOTES</span></span>

## <span data-ttu-id="b0c45-125">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b0c45-125">RELATED LINKS</span></span>

[<span data-ttu-id="b0c45-126">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="b0c45-126">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="b0c45-127">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="b0c45-127">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="b0c45-128">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="b0c45-128">Set-PSRepository</span></span>](Set-PSRepository.md)
