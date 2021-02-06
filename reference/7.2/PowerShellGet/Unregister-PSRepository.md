---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/unregister-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSRepository
ms.openlocfilehash: 908a43506bfbff964cfbdd8eea270b1fa42c3e77
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601438"
---
# <span data-ttu-id="93788-102">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="93788-102">Unregister-PSRepository</span></span>

## <span data-ttu-id="93788-103">개요</span><span class="sxs-lookup"><span data-stu-id="93788-103">SYNOPSIS</span></span>
<span data-ttu-id="93788-104">리포지토리 등록을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="93788-104">Unregisters a repository.</span></span>

## <span data-ttu-id="93788-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="93788-105">SYNTAX</span></span>

```
Unregister-PSRepository [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="93788-106">설명</span><span class="sxs-lookup"><span data-stu-id="93788-106">DESCRIPTION</span></span>

<span data-ttu-id="93788-107">`Unregister-PSRepository`Cmdlet은 현재 사용자의 리포지토리 등록을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="93788-107">The `Unregister-PSRepository` cmdlet unregisters a repository for the current user.</span></span>

## <span data-ttu-id="93788-108">예제</span><span class="sxs-lookup"><span data-stu-id="93788-108">EXAMPLES</span></span>

### <span data-ttu-id="93788-109">예제 1: 리포지토리 등록 취소</span><span class="sxs-lookup"><span data-stu-id="93788-109">Example 1: Unregister a repository</span></span>

<span data-ttu-id="93788-110">이 예제에서는 myNuGetSource 이라는 리포지토리의 등록을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="93788-110">This example unregisters the repository named myNuGetSource.</span></span>

```powershell
Unregister-PSRepository -Name "myNuGetSource"
```

### <span data-ttu-id="93788-111">예제 2: 모든 리포지토리 등록 취소</span><span class="sxs-lookup"><span data-stu-id="93788-111">Example 2: Unregister all repositories</span></span>

<span data-ttu-id="93788-112">이 예제에서는 `Get-PSRepository` 를 사용 하 여 등록 된 모든 리포지토리를 가져온 다음 파이프라인 연산자를 사용 하 여이를 `Unregister-PSRepository` 등록 취소 하기 위해 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="93788-112">This example uses `Get-PSRepository` to get all registered repositories, and uses the pipeline operator to pass them to `Unregister-PSRepository` to unregister them.</span></span>

```powershell
Get-PSRepository | Unregister-PSRepository
```

## <span data-ttu-id="93788-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="93788-113">PARAMETERS</span></span>

### <span data-ttu-id="93788-114">-Name</span><span class="sxs-lookup"><span data-stu-id="93788-114">-Name</span></span>

<span data-ttu-id="93788-115">제거할 리포지토리의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93788-115">Specifies an array of names of the repositories to remove.</span></span>

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

### <span data-ttu-id="93788-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="93788-116">CommonParameters</span></span>

<span data-ttu-id="93788-117">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="93788-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="93788-118">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93788-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="93788-119">입력</span><span class="sxs-lookup"><span data-stu-id="93788-119">INPUTS</span></span>

### <span data-ttu-id="93788-120">System.String[]</span><span class="sxs-lookup"><span data-stu-id="93788-120">System.String[]</span></span>

## <span data-ttu-id="93788-121">출력</span><span class="sxs-lookup"><span data-stu-id="93788-121">OUTPUTS</span></span>

### <span data-ttu-id="93788-122">System.Object</span><span class="sxs-lookup"><span data-stu-id="93788-122">System.Object</span></span>

## <span data-ttu-id="93788-123">참고</span><span class="sxs-lookup"><span data-stu-id="93788-123">NOTES</span></span>

## <span data-ttu-id="93788-124">관련 링크</span><span class="sxs-lookup"><span data-stu-id="93788-124">RELATED LINKS</span></span>

[<span data-ttu-id="93788-125">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="93788-125">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="93788-126">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="93788-126">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="93788-127">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="93788-127">Set-PSRepository</span></span>](Set-PSRepository.md)
