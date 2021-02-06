---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: abc820bd6f8f5c8cd8c6301aacee268c82161d7e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600856"
---
# <span data-ttu-id="13b8d-102">Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="13b8d-102">Get-ComputerInfo</span></span>

## <span data-ttu-id="13b8d-103">개요</span><span class="sxs-lookup"><span data-stu-id="13b8d-103">SYNOPSIS</span></span>
<span data-ttu-id="13b8d-104">시스템 및 운영 체제 속성의 통합 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="13b8d-104">Gets a consolidated object of system and operating system properties.</span></span>

## <span data-ttu-id="13b8d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="13b8d-105">SYNTAX</span></span>

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="13b8d-106">설명</span><span class="sxs-lookup"><span data-stu-id="13b8d-106">DESCRIPTION</span></span>

<span data-ttu-id="13b8d-107">`Get-ComputerInfo`Cmdlet은 시스템 및 운영 체제 속성의 통합 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="13b8d-107">The `Get-ComputerInfo` cmdlet gets a consolidated object of system and operating system properties.</span></span>
<span data-ttu-id="13b8d-108">이 cmdlet은 Windows PowerShell 5.1에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="13b8d-108">This cmdlet was introduced in Windows PowerShell 5.1.</span></span>

## <span data-ttu-id="13b8d-109">예제</span><span class="sxs-lookup"><span data-stu-id="13b8d-109">EXAMPLES</span></span>

### <span data-ttu-id="13b8d-110">예제 1: 모든 컴퓨터 속성 가져오기</span><span class="sxs-lookup"><span data-stu-id="13b8d-110">Example 1: Get all computer properties</span></span>

```powershell
Get-ComputerInfo
```

<span data-ttu-id="13b8d-111">이 명령은 컴퓨터에서 모든 시스템 및 운영 체제 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="13b8d-111">This command gets all system and operating system properties from the computer.</span></span>

### <span data-ttu-id="13b8d-112">예제 2: 모든 컴퓨터 운영 체제 속성 가져오기</span><span class="sxs-lookup"><span data-stu-id="13b8d-112">Example 2: Get all computer operating system properties</span></span>

```powershell
Get-ComputerInfo -Property "os*"
```

<span data-ttu-id="13b8d-113">이 명령은 컴퓨터에서 모든 운영 체제 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="13b8d-113">This command gets all operating system properties from the computer.</span></span>

## <span data-ttu-id="13b8d-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="13b8d-114">PARAMETERS</span></span>

### <span data-ttu-id="13b8d-115">-속성</span><span class="sxs-lookup"><span data-stu-id="13b8d-115">-Property</span></span>

<span data-ttu-id="13b8d-116">이 cmdlet이 표시 되는 컴퓨터 속성을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="13b8d-116">Specifies, as a string array, the computer properties in which this cmdlet displays.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="13b8d-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="13b8d-117">CommonParameters</span></span>

<span data-ttu-id="13b8d-118">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="13b8d-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="13b8d-119">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13b8d-119">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="13b8d-120">입력</span><span class="sxs-lookup"><span data-stu-id="13b8d-120">INPUTS</span></span>

### <span data-ttu-id="13b8d-121">System.String[]</span><span class="sxs-lookup"><span data-stu-id="13b8d-121">System.String[]</span></span>

## <span data-ttu-id="13b8d-122">출력</span><span class="sxs-lookup"><span data-stu-id="13b8d-122">OUTPUTS</span></span>

### <span data-ttu-id="13b8d-123">Microsoft. PowerShell. 관리 정보</span><span class="sxs-lookup"><span data-stu-id="13b8d-123">Microsoft.PowerShell.Management.ComputerInfo</span></span>

## <span data-ttu-id="13b8d-124">참고</span><span class="sxs-lookup"><span data-stu-id="13b8d-124">NOTES</span></span>

<span data-ttu-id="13b8d-125">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13b8d-125">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="13b8d-126">관련 링크</span><span class="sxs-lookup"><span data-stu-id="13b8d-126">RELATED LINKS</span></span>
