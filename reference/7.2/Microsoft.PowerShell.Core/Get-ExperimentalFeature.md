---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: aad634bb0a917d418aa9c7fa295a53fda280b8a3
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/27/2021
ms.locfileid: "99599752"
---
# <span data-ttu-id="6f7ff-102">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="6f7ff-102">Get-ExperimentalFeature</span></span>

## <span data-ttu-id="6f7ff-103">개요</span><span class="sxs-lookup"><span data-stu-id="6f7ff-103">SYNOPSIS</span></span>
<span data-ttu-id="6f7ff-104">실험적 기능을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-104">Gets experimental features.</span></span>

## <span data-ttu-id="6f7ff-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6f7ff-105">SYNTAX</span></span>

```
Get-ExperimentalFeature [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="6f7ff-106">설명</span><span class="sxs-lookup"><span data-stu-id="6f7ff-106">DESCRIPTION</span></span>

<span data-ttu-id="6f7ff-107">`Get-ExperimentalFeature`Cmdlet은 PowerShell에서 검색 된 모든 실험적 기능을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-107">The `Get-ExperimentalFeature` cmdlet returns all experimental features discovered by PowerShell.</span></span>
<span data-ttu-id="6f7ff-108">실험적 기능은 모듈 또는 PowerShell 엔진에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-108">Experimental features can come from modules or the PowerShell engine.</span></span> <span data-ttu-id="6f7ff-109">사용자는 실험적 기능을 사용 하 여 새로운 기능을 안전 하 게 테스트 하 고, 일반적으로 GitHub를 통해 피드백을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-109">Experimental features allow users to safely test new features and provide feedback (typically via GitHub) before the design is considered complete and any changes can become a breaking change.</span></span>

## <span data-ttu-id="6f7ff-110">예제</span><span class="sxs-lookup"><span data-stu-id="6f7ff-110">EXAMPLES</span></span>

### <span data-ttu-id="6f7ff-111">예제 1</span><span class="sxs-lookup"><span data-stu-id="6f7ff-111">Example 1</span></span>

<span data-ttu-id="6f7ff-112">현재 등록 된 실험적 기능 목록과 현재 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-112">Gets the list of currently registered experimental features and their current state.</span></span>

```powershell
Get-ExperimentalFeature
```

```Output
Name                         Enabled Source      Description
----                         ------- ------      -----------
PSImplicitRemotingBatching   False PSEngine      Batch implicit remoting proxy commands to improve performance
```

## <span data-ttu-id="6f7ff-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6f7ff-113">PARAMETERS</span></span>

### <span data-ttu-id="6f7ff-114">-Name</span><span class="sxs-lookup"><span data-stu-id="6f7ff-114">-Name</span></span>

<span data-ttu-id="6f7ff-115">반환할 특정 실험적 기능의 이름 또는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-115">Name or names of specific experimental features to return.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6f7ff-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6f7ff-116">CommonParameters</span></span>

<span data-ttu-id="6f7ff-117">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6f7ff-118">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6f7ff-119">입력</span><span class="sxs-lookup"><span data-stu-id="6f7ff-119">INPUTS</span></span>

### <span data-ttu-id="6f7ff-120">System.String[]</span><span class="sxs-lookup"><span data-stu-id="6f7ff-120">System.String[]</span></span>

<span data-ttu-id="6f7ff-121">반환할 실험적 기능의 이름 또는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-121">Name or names of experimental features to return.</span></span>

## <span data-ttu-id="6f7ff-122">출력</span><span class="sxs-lookup"><span data-stu-id="6f7ff-122">OUTPUTS</span></span>

### <span data-ttu-id="6f7ff-123">ExperimentalFeature.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-123">System.Management.Automation.ExperimentalFeature</span></span>

<span data-ttu-id="6f7ff-124">지정 된 이름이 없는 경우 요청 된 이름이 나 모든 실험적 기능과 일치 하는 인스턴스를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-124">Returns instances that match the requested names or all experimental features if no name is specified.</span></span>

## <span data-ttu-id="6f7ff-125">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6f7ff-125">RELATED LINKS</span></span>

[<span data-ttu-id="6f7ff-126">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="6f7ff-126">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="6f7ff-127">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="6f7ff-127">Enable-ExperimentalFeature</span></span>](Enable-ExperimentalFeature.md)
