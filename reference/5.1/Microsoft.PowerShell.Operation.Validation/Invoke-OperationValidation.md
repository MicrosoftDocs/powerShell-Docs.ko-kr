---
external help file: Microsoft.PowerShell.Operation.Validation-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Operation.Validation
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.operation.validation/invoke-operationvalidation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-OperationValidation
ms.openlocfilehash: 6c9d4001392de48032a0fe1ba3667db90ea614fc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214282"
---
# <span data-ttu-id="49608-103">Invoke-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="49608-103">Invoke-OperationValidation</span></span>

## <span data-ttu-id="49608-104">개요</span><span class="sxs-lookup"><span data-stu-id="49608-104">SYNOPSIS</span></span>

<span data-ttu-id="49608-105">작업 유효성 검사 프레임 워크 테스트를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="49608-105">Invokes Operation Validation Framework tests.</span></span>

## <span data-ttu-id="49608-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="49608-106">SYNTAX</span></span>

### <span data-ttu-id="49608-107">FileAndTest (기본값)</span><span class="sxs-lookup"><span data-stu-id="49608-107">FileAndTest (Default)</span></span>

```
Invoke-OperationValidation [-TestInfo <PSObject[]>] [-IncludePesterOutput] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="49608-108">경로</span><span class="sxs-lookup"><span data-stu-id="49608-108">Path</span></span>

```
Invoke-OperationValidation [-testFilePath <String[]>] [-IncludePesterOutput] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="49608-109">UseGetOperationTest</span><span class="sxs-lookup"><span data-stu-id="49608-109">UseGetOperationTest</span></span>

```
Invoke-OperationValidation [-ModuleName <String[]>] [-TestType <String[]>] [-IncludePesterOutput] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="49608-110">설명</span><span class="sxs-lookup"><span data-stu-id="49608-110">DESCRIPTION</span></span>

<span data-ttu-id="49608-111">**Invoke operationvalidation** cmdlet은 지정 된 모듈에 대 한 작업 유효성 검사 프레임 워크 테스트를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="49608-111">The **Invoke-OperationValidation** cmdlet invokes Operation Validation Framework tests for a specified module.</span></span>

## <span data-ttu-id="49608-112">예제</span><span class="sxs-lookup"><span data-stu-id="49608-112">EXAMPLES</span></span>

### <span data-ttu-id="49608-113">예제 1: 작업 유효성 검사 테스트 호출</span><span class="sxs-lookup"><span data-stu-id="49608-113">Example 1: Invoke an Operation Validation test</span></span>

```
PS C:\> Get-OperationValidation -ModuleName "OperationValidation" | Invoke-OperationValidation -IncludePesterOutput
Describing Simple Test Suite
 [+] first Operational test 20ms
 [+] second Operational test 19ms
 [+] third Operational test 9ms
Tests completed in 48ms
Passed: 3 Failed: 0 Skipped: 0 Pending: 0
Describing Scenario targeted tests
   Context The RemoteAccess service
    [+] The service is running 37ms
   Context The Firewall Rules
    [+] A rule for TCP port 3389 is enabled 1.19s
    [+] A rule for UDP port 3389 is enabled 11ms
Tests completed in 1.24s
Passed: 3 Failed: 0 Skipped: 0 Pending: 0




   Module: OperationValidation




Result  Name
------- --------
Passed  Simple Test Suite::first Operational test
Passed  Simple Test Suite::second Operational test
Passed  Simple Test Suite::third Operational test
Passed  Scenario targeted tests:The RemoteAccess service:The service is running
Passed  Scenario targeted tests:The Firewall Rules:A rule for TCP port 3389 is enabled
Passed  Scenario targeted tests:The Firewall Rules:A rule for UDP port 3389 is enabled
```

<span data-ttu-id="49608-114">이 명령은 OperationValidation 이라는 모듈을 가져온 다음 파이프라인 연산자를 사용 하 여 테스트를 실행 하는 **Invoke operationvalidation** cmdlet에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="49608-114">This command gets the module named OperationValidation, and uses the pipeline operator to pass it to the **Invoke-OperationValidation** cmdlet, which runs the test.</span></span>

## <span data-ttu-id="49608-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="49608-115">PARAMETERS</span></span>

### <span data-ttu-id="49608-116">-IncludePesterOutput</span><span class="sxs-lookup"><span data-stu-id="49608-116">-IncludePesterOutput</span></span>

<span data-ttu-id="49608-117">Pester 테스트 출력을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="49608-117">Includes Pester test output.</span></span>
<span data-ttu-id="49608-118">기본값은 $False입니다.</span><span class="sxs-lookup"><span data-stu-id="49608-118">The default is $False.</span></span>

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

### <span data-ttu-id="49608-119">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="49608-119">-ModuleName</span></span>

<span data-ttu-id="49608-120">모듈의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49608-120">Specifies an array of names of modules.</span></span>

```yaml
Type: System.String[]
Parameter Sets: UseGetOperationTest
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49608-121">-testFilePath</span><span class="sxs-lookup"><span data-stu-id="49608-121">-testFilePath</span></span>

<span data-ttu-id="49608-122">작업 유효성 검사 프레임 워크 테스트 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49608-122">Specifies the path of an Operation Validation Framework test file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="49608-123">-TestInfo</span><span class="sxs-lookup"><span data-stu-id="49608-123">-TestInfo</span></span>

<span data-ttu-id="49608-124">파일의 경로 및 실행할 테스트의 이름을 지정 하는 사용자 지정 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49608-124">Specifies a custom object that specifies the path to the file and the name of the test to run.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: FileAndTest
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="49608-125">-TestType</span><span class="sxs-lookup"><span data-stu-id="49608-125">-TestType</span></span>

<span data-ttu-id="49608-126">테스트 형식의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49608-126">Specifies an array of test types.</span></span>
<span data-ttu-id="49608-127">유효한 값은 Simple, 포괄적 또는 both입니다.</span><span class="sxs-lookup"><span data-stu-id="49608-127">Valid values are Simple, Comprehensive, or both.</span></span>
<span data-ttu-id="49608-128">기본값은 "Simple, 포괄적"입니다.</span><span class="sxs-lookup"><span data-stu-id="49608-128">The default is "Simple,Comprehensive".</span></span>

```yaml
Type: System.String[]
Parameter Sets: UseGetOperationTest
Aliases:
Accepted values: Simple, Comprehensive

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49608-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="49608-129">-Confirm</span></span>

<span data-ttu-id="49608-130">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="49608-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="49608-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="49608-131">-WhatIf</span></span>

<span data-ttu-id="49608-132">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="49608-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="49608-133">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49608-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="49608-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="49608-134">CommonParameters</span></span>
<span data-ttu-id="49608-135">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="49608-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="49608-136">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="49608-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="49608-137">입력</span><span class="sxs-lookup"><span data-stu-id="49608-137">INPUTS</span></span>

### <span data-ttu-id="49608-138">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="49608-138">PSCustomObject</span></span>

<span data-ttu-id="49608-139">이 cmdlet에 대 한 **Get OperationValidation** 의 출력을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49608-139">You can pipe the output of **Get-OperationValidation** to this cmdlet.</span></span>

## <span data-ttu-id="49608-140">출력</span><span class="sxs-lookup"><span data-stu-id="49608-140">OUTPUTS</span></span>

### <span data-ttu-id="49608-141">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="49608-141">PSCustomObject</span></span>

<span data-ttu-id="49608-142">**PSCustomObject** 는 유효성 검사의 성공 여부를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="49608-142">The **PSCustomObject** describes whether the validation was successful.</span></span>

## <span data-ttu-id="49608-143">참고</span><span class="sxs-lookup"><span data-stu-id="49608-143">NOTES</span></span>

## <span data-ttu-id="49608-144">관련 링크</span><span class="sxs-lookup"><span data-stu-id="49608-144">RELATED LINKS</span></span>

[<span data-ttu-id="49608-145">Get-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="49608-145">Get-OperationValidation</span></span>](Get-OperationValidation.md)
