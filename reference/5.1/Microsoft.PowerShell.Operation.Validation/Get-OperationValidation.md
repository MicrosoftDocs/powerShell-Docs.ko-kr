---
external help file: Microsoft.PowerShell.Operation.Validation-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Operation.Validation
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.operation.validation/get-operationvalidation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-OperationValidation
ms.openlocfilehash: 22ff12848fb7aefaa7f684ee5d8723cc723a5879
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214289"
---
# <span data-ttu-id="4e985-103">Get-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="4e985-103">Get-OperationValidation</span></span>

## <span data-ttu-id="4e985-104">개요</span><span class="sxs-lookup"><span data-stu-id="4e985-104">SYNOPSIS</span></span>
<span data-ttu-id="4e985-105">작업 유효성 검사 프레임 워크 테스트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4e985-105">Gets Operation Validation Framework tests.</span></span>

## <span data-ttu-id="4e985-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4e985-106">SYNTAX</span></span>

```
Get-OperationValidation [[-ModuleName] <String[]>] [-TestType <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="4e985-107">설명</span><span class="sxs-lookup"><span data-stu-id="4e985-107">DESCRIPTION</span></span>
<span data-ttu-id="4e985-108">**가져오기 operationvalidation** cmdlet은 설치 된 모듈에 대 한 작업 유효성 검사 프레임 워크 테스트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4e985-108">The **Get-OperationValidation** cmdlet gets Operation Validation Framework tests for installed modules.</span></span>

<span data-ttu-id="4e985-109">진단 폴더를 포함 하는 모듈은 단순 또는 포괄적인 하위 폴더 또는 둘 다에서 Pester 테스트에 대해 검사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e985-109">Modules that include a Diagnostics folder are inspected for Pester tests in the Simple or Comprehensive subfolder, or both.</span></span>

## <span data-ttu-id="4e985-110">예제</span><span class="sxs-lookup"><span data-stu-id="4e985-110">EXAMPLES</span></span>

### <span data-ttu-id="4e985-111">예제 1: 작업 유효성 검사 테스트 가져오기</span><span class="sxs-lookup"><span data-stu-id="4e985-111">Example 1: Get Operation Validation tests</span></span>

```
PS C:\> Get-OperationValidation -ModuleName "C:\temp\modules\AddNumbers"
    Type:     Simple
    File:     addnum.tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Simple\addnum.tests.ps1
    Name:
        Add-Em
        Subtract em
        Add-Numbers
    Type:     Comprehensive
    File:     Comp.Adding.Tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Comprehensive\Comp.Adding.Tests.ps1
    Name:
        Comprehensive Adding Tests
        Comprehensive Subtracting Tests
        Comprehensive Examples
```

<span data-ttu-id="4e985-112">이 명령은 C:\temp\modules 폴더의 AddNumbers 이라는 모듈에서 유효성 검사 테스트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4e985-112">This command gets validation tests from the module named AddNumbers in the C:\temp\modules folder.</span></span>

## <span data-ttu-id="4e985-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4e985-113">PARAMETERS</span></span>

### <span data-ttu-id="4e985-114">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="4e985-114">-ModuleName</span></span>
<span data-ttu-id="4e985-115">모듈의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e985-115">Specifies an array of names of modules.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e985-116">-TestType</span><span class="sxs-lookup"><span data-stu-id="4e985-116">-TestType</span></span>
<span data-ttu-id="4e985-117">테스트 형식의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e985-117">Specifies an array of test types.</span></span>
<span data-ttu-id="4e985-118">유효한 값은 Simple, 포괄적 또는 both입니다.</span><span class="sxs-lookup"><span data-stu-id="4e985-118">Valid values are Simple, Comprehensive, or both.</span></span>
<span data-ttu-id="4e985-119">기본값은 "Simple, 포괄적"입니다.</span><span class="sxs-lookup"><span data-stu-id="4e985-119">The default is "Simple,Comprehensive".</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Simple, Comprehensive

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e985-120">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4e985-120">CommonParameters</span></span>
<span data-ttu-id="4e985-121">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4e985-121">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4e985-122">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e985-122">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4e985-123">입력</span><span class="sxs-lookup"><span data-stu-id="4e985-123">INPUTS</span></span>

### <span data-ttu-id="4e985-124">없음</span><span class="sxs-lookup"><span data-stu-id="4e985-124">None</span></span>
<span data-ttu-id="4e985-125">이 cmdlet에 대 한 입력을 파이프 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4e985-125">You cannot pipe any input to this cmdlet.</span></span>

## <span data-ttu-id="4e985-126">출력</span><span class="sxs-lookup"><span data-stu-id="4e985-126">OUTPUTS</span></span>

### <span data-ttu-id="4e985-127">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="4e985-127">PSCustomObject</span></span>
<span data-ttu-id="4e985-128">**PSCustomObject** 유효성 검사에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e985-128">The **PSCustomObject** describes the validation.</span></span>

## <span data-ttu-id="4e985-129">참고</span><span class="sxs-lookup"><span data-stu-id="4e985-129">NOTES</span></span>

## <span data-ttu-id="4e985-130">관련 링크</span><span class="sxs-lookup"><span data-stu-id="4e985-130">RELATED LINKS</span></span>

[<span data-ttu-id="4e985-131">Invoke-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="4e985-131">Invoke-OperationValidation</span></span>](Invoke-OperationValidation.md)
