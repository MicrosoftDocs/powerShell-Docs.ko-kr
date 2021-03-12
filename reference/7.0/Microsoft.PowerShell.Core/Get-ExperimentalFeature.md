---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: 22e1b21f304129d6912557a5dbc825bc4e6202a1
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103193927"
---
# <span data-ttu-id="ada04-102">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="ada04-102">Get-ExperimentalFeature</span></span>

## <span data-ttu-id="ada04-103">개요</span><span class="sxs-lookup"><span data-stu-id="ada04-103">SYNOPSIS</span></span>
<span data-ttu-id="ada04-104">실험적 기능을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ada04-104">Gets experimental features.</span></span>

## <span data-ttu-id="ada04-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ada04-105">SYNTAX</span></span>

```
Get-ExperimentalFeature [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="ada04-106">설명</span><span class="sxs-lookup"><span data-stu-id="ada04-106">DESCRIPTION</span></span>

<span data-ttu-id="ada04-107">`Get-ExperimentalFeature`Cmdlet은 PowerShell에서 검색 된 모든 실험적 기능을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ada04-107">The `Get-ExperimentalFeature` cmdlet returns all experimental features discovered by PowerShell.</span></span>
<span data-ttu-id="ada04-108">실험적 기능은 모듈 또는 PowerShell 엔진에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada04-108">Experimental features can come from modules or the PowerShell engine.</span></span> <span data-ttu-id="ada04-109">사용자는 실험적 기능을 사용 하 여 새로운 기능을 안전 하 게 테스트 하 고, 일반적으로 GitHub를 통해 피드백을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada04-109">Experimental features allow users to safely test new features and provide feedback (typically via GitHub) before the design is considered complete and any changes can become a breaking change.</span></span>

## <span data-ttu-id="ada04-110">예제</span><span class="sxs-lookup"><span data-stu-id="ada04-110">EXAMPLES</span></span>

### <span data-ttu-id="ada04-111">예 1</span><span class="sxs-lookup"><span data-stu-id="ada04-111">Example 1</span></span>

<span data-ttu-id="ada04-112">현재 등록 된 실험적 기능 목록과 현재 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ada04-112">Gets the list of currently registered experimental features and their current state.</span></span>

```powershell
Get-ExperimentalFeature
```

```Output
Name                         Enabled Source      Description
----                         ------- ------      -----------
PSImplicitRemotingBatching   False PSEngine      Batch implicit remoting proxy commands to improve performance
```

## <span data-ttu-id="ada04-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ada04-113">PARAMETERS</span></span>

### <span data-ttu-id="ada04-114">-Name</span><span class="sxs-lookup"><span data-stu-id="ada04-114">-Name</span></span>

<span data-ttu-id="ada04-115">반환할 특정 실험적 기능의 이름 또는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ada04-115">Name or names of specific experimental features to return.</span></span>

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

### <span data-ttu-id="ada04-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ada04-116">CommonParameters</span></span>

<span data-ttu-id="ada04-117">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ada04-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ada04-118">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ada04-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ada04-119">입력</span><span class="sxs-lookup"><span data-stu-id="ada04-119">INPUTS</span></span>

### <span data-ttu-id="ada04-120">System.String[]</span><span class="sxs-lookup"><span data-stu-id="ada04-120">System.String[]</span></span>

<span data-ttu-id="ada04-121">반환할 실험적 기능의 이름 또는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ada04-121">Name or names of experimental features to return.</span></span>

## <span data-ttu-id="ada04-122">출력</span><span class="sxs-lookup"><span data-stu-id="ada04-122">OUTPUTS</span></span>

### <span data-ttu-id="ada04-123">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="ada04-123">ExperimentalFeature</span></span>

<span data-ttu-id="ada04-124">지정 된 이름이 없는 경우 요청 된 이름이 나 모든 실험적 기능과 일치 하는 인스턴스를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ada04-124">Returns instances that match the requested names or all experimental features if no name is specified.</span></span>

## <span data-ttu-id="ada04-125">참고</span><span class="sxs-lookup"><span data-stu-id="ada04-125">NOTES</span></span>

## <span data-ttu-id="ada04-126">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ada04-126">RELATED LINKS</span></span>

[<span data-ttu-id="ada04-127">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="ada04-127">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="ada04-128">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="ada04-128">Enable-ExperimentalFeature</span></span>](Enable-ExperimentalFeature.md)
