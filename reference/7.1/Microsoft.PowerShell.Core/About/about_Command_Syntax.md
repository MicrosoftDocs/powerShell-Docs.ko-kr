---
description: PowerShell에서 사용 되는 구문 다이어그램에 대해 설명 합니다.
keywords: powershell,cmdlet
ms.date: 06/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_syntax?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Syntax
ms.openlocfilehash: a9da31213e76f5d28fbcb2cf4f4f6e9c49d51866
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93224010"
---
# <a name="about-command-syntax"></a><span data-ttu-id="3f887-104">명령 구문 정보</span><span class="sxs-lookup"><span data-stu-id="3f887-104">About Command Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="3f887-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="3f887-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="3f887-106">PowerShell에서 사용 되는 구문 다이어그램에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-106">Describes the syntax diagrams that are used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="3f887-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="3f887-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="3f887-108">[Get-help](xref:Microsoft.PowerShell.Core.Get-Help) 및 [get Command](xref:Microsoft.PowerShell.Core.Get-Command) cmdlet은 명령을 올바르게 생성 하는 데 도움이 되는 구문 다이어그램을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-108">The [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) and [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) cmdlets display syntax diagrams to help you construct commands correctly.</span></span> <span data-ttu-id="3f887-109">이 항목에서는 구문 다이어그램을 해석 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-109">This topic explains how to interpret the syntax diagrams.</span></span>

## <a name="syntax-diagrams"></a><span data-ttu-id="3f887-110">구문 다이어그램</span><span class="sxs-lookup"><span data-stu-id="3f887-110">SYNTAX DIAGRAMS</span></span>

<span data-ttu-id="3f887-111">명령 구문 다이어그램의 각 단락은 명령의 올바른 형태를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-111">Each paragraph in a command syntax diagram represents a valid form of the command.</span></span>

<span data-ttu-id="3f887-112">명령을 생성 하려면 구문 다이어그램의 왼쪽에서 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-112">To construct a command, follow the syntax diagram from left to right.</span></span> <span data-ttu-id="3f887-113">선택적 매개 변수 중에서 하나를 선택 하 고 자리 표시자에 대 한 값을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-113">Select from among the optional parameters and provide values for the placeholders.</span></span>

<span data-ttu-id="3f887-114">PowerShell에서는 구문 다이어그램에 다음 표기법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-114">PowerShell uses the following notation for syntax diagrams.</span></span>

```powershell
<command-name> -<Required Parameter Name> <Required Parameter Value>
[-<Optional Parameter Name> <Optional Parameter Value>]
[-<Optional Switch Parameters>]
[-<Optional Parameter Name>] <Required Parameter Value>
```

<span data-ttu-id="3f887-115">다음은 [새 별칭](xref:Microsoft.PowerShell.Utility.New-Alias) cmdlet에 대 한 구문입니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-115">The following is the syntax for the [New-Alias](xref:Microsoft.PowerShell.Utility.New-Alias) cmdlet.</span></span>

```powershell
New-Alias [-Name] <string> [-Value] <string> [-Description <string>]
[-Force] [-Option {None | ReadOnly | Constant | Private | AllScope}]
[-PassThru] [-Scope <string>] [-Confirm] [-WhatIf] [<CommonParameters>]
```

<span data-ttu-id="3f887-116">구문은 가독성을 위해 대문자로 표기 되지만 PowerShell은 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-116">The syntax is capitalized for readability, but PowerShell is case-insensitive.</span></span>

<span data-ttu-id="3f887-117">구문 다이어그램에는 다음과 같은 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-117">The syntax diagram has the following elements.</span></span>

## <a name="command-name"></a><span data-ttu-id="3f887-118">명령 이름</span><span class="sxs-lookup"><span data-stu-id="3f887-118">Command name</span></span>

<span data-ttu-id="3f887-119">명령은 항상 명령 이름 (예:)으로 시작 `New-Alias` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-119">Commands always begin with a command name, such as `New-Alias`.</span></span> <span data-ttu-id="3f887-120">명령 이름 또는 해당 별칭 (예:의 "gcm")을 입력 합니다 `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="3f887-120">Type the command name or its alias, such a "gcm" for `Get-Command`.</span></span>

## <a name="parameters"></a><span data-ttu-id="3f887-121">매개 변수</span><span class="sxs-lookup"><span data-stu-id="3f887-121">Parameters</span></span>

<span data-ttu-id="3f887-122">명령의 매개 변수는 명령이 수행 하는 작업을 결정 하는 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-122">The parameters of a command are options that determine what the command does.</span></span>
<span data-ttu-id="3f887-123">일부 매개 변수는 명령에 대 한 사용자 입력 인 "값"을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-123">Some parameters take a "value" which is user input to the command.</span></span>

<span data-ttu-id="3f887-124">예를 들어 명령에는 `Get-Help` 도움말이 표시 되는 항목의 이름을 지정할 수 있는 **name** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-124">For example, the `Get-Help` command has a **Name** parameter that lets you specify the name of the topic for which help is displayed.</span></span> <span data-ttu-id="3f887-125">토픽 이름은 **name** 매개 변수의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-125">The topic name is the value of the **Name** parameter.</span></span>

<span data-ttu-id="3f887-126">PowerShell 명령에서 매개 변수 이름은 항상 하이픈으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-126">In a PowerShell command, parameter names always begin with a hyphen.</span></span>
<span data-ttu-id="3f887-127">하이픈은 명령의 항목이 매개 변수 이름 임을 PowerShell에 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-127">The hyphen tells PowerShell that the item in the command is a parameter name.</span></span>

<span data-ttu-id="3f887-128">예를 들어의 Name 매개 변수를 사용 하려면 `New-Alias` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-128">For example, to use the Name parameter of `New-Alias`, you type the following:</span></span>

```powershell
-Name
```

<span data-ttu-id="3f887-129">매개 변수는 필수 또는 선택적 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-129">Parameters can be mandatory or optional.</span></span> <span data-ttu-id="3f887-130">구문 다이어그램에서 선택적 항목은 대괄호로 묶여 `[ ]` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-130">In a syntax diagram, optional items are enclosed in brackets `[ ]`.</span></span>

<span data-ttu-id="3f887-131">매개 변수에 대 한 자세한 내용은 [about_Parameters](about_Parameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3f887-131">For more information about parameters, see [about_Parameters](about_Parameters.md).</span></span>

## <a name="parameter-values"></a><span data-ttu-id="3f887-132">매개 변수 값</span><span class="sxs-lookup"><span data-stu-id="3f887-132">Parameter Values</span></span>

<span data-ttu-id="3f887-133">매개 변수 값은 매개 변수가 사용 하는 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-133">A parameter value is the input that the parameter takes.</span></span> <span data-ttu-id="3f887-134">Windows PowerShell은 Microsoft .NET 프레임 워크를 기반으로 하기 때문에 매개 변수 값은 구문 다이어그램에서 .NET 형식으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-134">Because Windows PowerShell is based on the Microsoft .NET Framework, parameter values are represented in the syntax diagram by their .NET type.</span></span>

<span data-ttu-id="3f887-135">예를 들어의 Name 매개 변수는 `Get-Help` "string" 값을 사용 합니다 .이 값은 단일 단어 또는 따옴표로 묶인 여러 단어와 같은 텍스트 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-135">For example, the Name parameter of `Get-Help` takes a "String" value, which is a text string, such as a single word or multiple words enclosed in quotation marks.</span></span>

```powershell
[-Name] <string>
```

<span data-ttu-id="3f887-136">매개 변수 값의 .NET 형식은 꺾쇠 괄호로 묶어 `< >` 명령에 입력 하는 리터럴이 아니라 값에 대 한 자리 표시자 임을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-136">The .NET type of a parameter value is enclosed in angle brackets `< >` to indicate that it is placeholder for a value and not a literal that you type in a command.</span></span>

<span data-ttu-id="3f887-137">매개 변수를 사용 하려면 .NET 형식 자리 표시자를 지정 된 .NET 형식의 개체로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-137">To use the parameter, replace the .NET type placeholder with an object that has the specified .NET type.</span></span>

<span data-ttu-id="3f887-138">예를 들어 **name** 매개 변수를 사용 하려면 다음과 같이 "-name"을 입력 한 다음 문자열을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-138">For example, to use the **Name** parameter, type "-Name" followed by a string, such as the following:</span></span>

```powershell
-Name MyAlias
```

## <a name="parameters-with-no-values"></a><span data-ttu-id="3f887-139">값이 없는 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3f887-139">Parameters with no values</span></span>

<span data-ttu-id="3f887-140">일부 매개 변수는 입력을 허용 하지 않으므로 매개 변수 값이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-140">Some parameters do not accept input, so they do not have a parameter value.</span></span>
<span data-ttu-id="3f887-141">값이 없는 매개 변수는 설정/해제 스위치 처럼 작동 하므로 "스위치 매개 변수" 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-141">Parameters without values are called "switch parameters" because they work like on/off switches.</span></span> <span data-ttu-id="3f887-142">이러한 항목을 포함 하거나 명령에서 생략할 수 있습니다 (꺼짐).</span><span class="sxs-lookup"><span data-stu-id="3f887-142">You include them (on) or you omit them (off) from a command.</span></span>

<span data-ttu-id="3f887-143">스위치 매개 변수를 사용 하려면 매개 변수 이름을 하이픈 앞에 입력 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-143">To use a switch parameter, just type the parameter name, preceded by a hyphen.</span></span>

<span data-ttu-id="3f887-144">예를 들어 cmdlet의 **WhatIf** 매개 변수를 사용 하려면 `New-Alias` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-144">For example, to use the **WhatIf** parameter of the `New-Alias` cmdlet, type the following:</span></span>

```powershell
-WhatIf
```

## <a name="parameter-sets"></a><span data-ttu-id="3f887-145">매개 변수 집합</span><span class="sxs-lookup"><span data-stu-id="3f887-145">Parameter Sets</span></span>

<span data-ttu-id="3f887-146">명령의 매개 변수는 매개 변수 집합에 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-146">The parameters of a command are listed in parameter sets.</span></span> <span data-ttu-id="3f887-147">매개 변수 집합은 구문 다이어그램의 단락과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-147">Parameter sets look like the paragraphs of a syntax diagram.</span></span>

<span data-ttu-id="3f887-148">Cmdlet에는 `New-Alias` 하나의 매개 변수 집합이 있지만 많은 cmdlet에는 여러 매개 변수 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-148">The `New-Alias` cmdlet has one parameter set, but many cmdlets have multiple parameter sets.</span></span> <span data-ttu-id="3f887-149">일부 cmdlet 매개 변수는 매개 변수 집합에 대해 고유 하며, 다른 매개 변수는 여러 매개 변수 집합에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-149">Some of the cmdlet parameters are unique to a parameter set, and others appear in multiple parameter sets.</span></span> <span data-ttu-id="3f887-150">각 매개 변수 집합은 유효한 명령의 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-150">Each parameter set represents the format of a valid command.</span></span> <span data-ttu-id="3f887-151">매개 변수 집합에는 명령에 함께 사용할 수 있는 매개 변수만 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-151">A parameter set includes only parameters that can be used together in a command.</span></span> <span data-ttu-id="3f887-152">동일한 명령에서 매개 변수를 사용할 수 없는 경우 별도의 매개 변수 집합에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-152">If parameters cannot be used in the same command, they appear in separate parameter sets.</span></span>

<span data-ttu-id="3f887-153">예를 들어, [Get Random](xref:Microsoft.PowerShell.Utility.Get-Random) cmdlet에는 다음과 같은 매개 변수 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-153">For example, the [Get-Random](xref:Microsoft.PowerShell.Utility.Get-Random) cmdlet has the following parameter sets:</span></span>

```powershell
Get-Random [[-Maximum] <Object>] [-Minimum <Object>] [-SetSeed <int>]
[<CommonParameters>]

Get-Random [-InputObject] <Object[]> [-Count <int>] [-SetSeed <int>]
[<CommonParameters>]
```

<span data-ttu-id="3f887-154">난수를 반환 하는 첫 번째 매개 변수 집합에는 **최소** 및 **최대** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-154">The first parameter set, which returns a random number, has the **Minimum** and **Maximum** parameters.</span></span> <span data-ttu-id="3f887-155">개체 집합에서 무작위로 선택 된 개체를 반환 하는 두 번째 매개 변수 집합에는 **InputObject** 및 **Count** 매개 변수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-155">The second parameter set, which returns a randomly selected object from a set of objects, includes the **InputObject** and **Count** parameters.</span></span> <span data-ttu-id="3f887-156">두 매개 변수 집합 모두에는 **Setseed** 매개 변수와 일반 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-156">Both parameter sets have the **SetSeed** parameter and the common parameters.</span></span>

<span data-ttu-id="3f887-157">이러한 매개 변수 집합은 동일한 명령에서 **InputObject** 및 **count** 매개 변수를 사용할 수 있지만 동일한 명령에서 **Maximum** 및 **count** 매개 변수를 사용할 수 없음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-157">These parameter sets indicate that you can use the **InputObject** and **Count** parameters in the same command, but you cannot use the **Maximum** and **Count** parameters in the same command.</span></span>

<span data-ttu-id="3f887-158">해당 매개 변수 집합에서 매개 변수를 사용 하 여 사용 하려는 매개 변수 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-158">You indicate which parameter set you want to use by using the parameters in that parameter set.</span></span>

<span data-ttu-id="3f887-159">그러나 모든 cmdlet에는 기본 매개 변수 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-159">However, every cmdlet also has a default parameter set.</span></span> <span data-ttu-id="3f887-160">기본 매개 변수 집합은 매개 변수 집합에 고유한 매개 변수를 지정 하지 않을 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-160">The default parameter set is used when you do not specify parameters that are unique to a parameter set.</span></span> <span data-ttu-id="3f887-161">예를 들어 `Get-Random` 매개 변수 없이를 사용 하는 경우 Windows PowerShell은 사용자가 **number** 매개 변수 집합을 사용 하 고 있으며 난수를 반환 한다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-161">For example, if you use `Get-Random` without parameters, Windows PowerShell assumes that you are using the **Number** parameter set and it returns a random number.</span></span>

<span data-ttu-id="3f887-162">각 매개 변수 집합에서 매개 변수는 위치 순서 대로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-162">In each parameter set, the parameters appear in position order.</span></span> <span data-ttu-id="3f887-163">명령의 매개 변수 순서는 선택적 매개 변수 이름을 생략 하는 경우에만 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-163">The order of parameters in a command matters only when you omit the optional parameter names.</span></span> <span data-ttu-id="3f887-164">매개 변수 이름을 생략 하면 PowerShell은 위치 및 유형별로 매개 변수에 값을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-164">When parameter names are omitted, PowerShell assigns values to parameters by position and type.</span></span> <span data-ttu-id="3f887-165">매개 변수 위치에 대 한 자세한 내용은을 참조 하십시오 `about_Parameters` .</span><span class="sxs-lookup"><span data-stu-id="3f887-165">For more information about parameter position, see `about_Parameters`.</span></span>

## <a name="symbols-in-syntax-diagrams"></a><span data-ttu-id="3f887-166">구문 다이어그램의 기호</span><span class="sxs-lookup"><span data-stu-id="3f887-166">Symbols in Syntax Diagrams</span></span>

<span data-ttu-id="3f887-167">구문 다이어그램은 명령 이름, 명령 매개 변수 및 매개 변수 값을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-167">The syntax diagram lists the command name, the command parameters, and the parameter values.</span></span> <span data-ttu-id="3f887-168">또한 기호를 사용 하 여 유효한 명령을 생성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-168">It also uses symbols to show how to construct a valid command.</span></span>

<span data-ttu-id="3f887-169">구문 다이어그램은 다음 기호를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-169">The syntax diagrams use the following symbols:</span></span>

- <span data-ttu-id="3f887-170">하이픈은 `-` 매개 변수 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-170">A hyphen `-` indicates a parameter name.</span></span> <span data-ttu-id="3f887-171">구문 다이어그램에 표시 된 것 처럼 명령에 공백을 사용 하지 않고 매개 변수 이름 바로 앞에 하이픈을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-171">In a command, type the hyphen immediately before the parameter name with no intervening spaces, as shown in the syntax diagram.</span></span>

  <span data-ttu-id="3f887-172">예를 들어의 **Name** 매개 변수를 사용 하려면 `New-Alias` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-172">For example, to use the **Name** parameter of `New-Alias`, type:</span></span>

  ```powershell
  -Name
  ```

- <span data-ttu-id="3f887-173">꺾쇠 괄호는 `<>` 자리 표시자 텍스트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-173">Angle brackets `<>` indicate placeholder text.</span></span> <span data-ttu-id="3f887-174">명령에 꺾쇠 괄호 또는 자리 표시자 텍스트를 입력 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-174">You do not type the angle brackets or the placeholder text in a command.</span></span> <span data-ttu-id="3f887-175">대신이 항목을 설명 하는 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-175">Instead, you replace it with the item that it describes.</span></span>

  <span data-ttu-id="3f887-176">꺾쇠 괄호는 매개 변수에서 사용 하는 값의 .NET 유형을 식별 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-176">Angle brackets are used to identify the .NET type of the value that a parameter takes.</span></span> <span data-ttu-id="3f887-177">예를 들어 cmdlet의 **Name** 매개 변수를 사용 하려면 `New-Alias` 를 `<string>` 문자열로 바꿉니다 .이 문자열은 단일 단어나 따옴표로 묶인 단어 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-177">For example, to use the **Name** parameter of the `New-Alias` cmdlet, you replace the `<string>` with a string, which is a single word or a group of words that are enclosed in quotation marks.</span></span>

- <span data-ttu-id="3f887-178">대괄호는 `[ ]` 선택적 항목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-178">Brackets `[ ]` indicate optional items.</span></span> <span data-ttu-id="3f887-179">매개 변수 및 해당 값은 선택 사항이 될 수 있으며, 필수 매개 변수의 이름은 선택 사항 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-179">A parameter and its value can be optional, or the name of a required parameter can be optional.</span></span>

  <span data-ttu-id="3f887-180">예를 들어의 **Description** 매개 변수 `New-Alias` 및 해당 값은 모두 선택 사항 이므로 대괄호로 묶여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-180">For example, the **Description** parameter of `New-Alias` and its value are enclosed in brackets because they are both optional.</span></span>

  ```powershell
  [-Description <string>]
  ```

  <span data-ttu-id="3f887-181">대괄호는 또한 Name 매개 변수 값이 필요 하다는 것 `<string>` 을 나타내지만 매개 변수 이름 "name"은 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-181">The brackets also indicate that the Name parameter value `<string>` is required, but the parameter name, "Name", is optional.</span></span>

  ```powershell
  [-Name] <string>
  ```

- <span data-ttu-id="3f887-182">.NET 형식에 오른쪽 및 왼쪽 대괄호가 추가 된 경우 `[]` 매개 변수가 해당 형식의 값을 하나 또는 여러 개 사용할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-182">A right and left bracket `[]` appended to a .NET type indicates that the parameter can accept one or multiple values of that type.</span></span> <span data-ttu-id="3f887-183">쉼표로 구분된 목록으로 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-183">Enter the values in a comma-separated list.</span></span>

  <span data-ttu-id="3f887-184">예를 들어 cmdlet의 **name** 매개 변수는 `New-Alias` 하나의 문자열만 사용 하지만, [Get-Process](xref:Microsoft.PowerShell.Management.Get-Process) 의 **name** 매개 변수는 하나 이상의 문자열을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-184">For example, the **Name** parameter of the `New-Alias` cmdlet takes only one string, but the **Name** parameter of [Get-Process](xref:Microsoft.PowerShell.Management.Get-Process) can take one or many strings.</span></span>

  ```powershell
  New-Alias [-Name] <string>

  New-Alias -Name MyAlias
  ```

  ```powershell
  Get-Process [-Name] <string[]>

  Get-Process -Name Explorer, Winlogon, Services
  ```

- <span data-ttu-id="3f887-185">중괄호는 `{}` 매개 변수의 유효한 값 집합인 "열거형"을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-185">Braces `{}` indicate an "enumeration," which is a set of valid values for a parameter.</span></span>

  <span data-ttu-id="3f887-186">중괄호의 값은 세로 막대로 구분 됩니다 `|` .</span><span class="sxs-lookup"><span data-stu-id="3f887-186">The values in the braces are separated by vertical bars `|`.</span></span> <span data-ttu-id="3f887-187">이러한 막대는 "배타적 OR" 선택을 나타냅니다. 즉, 중괄호 안에 나열 된 값 집합에서 값을 하나만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-187">These bars indicate an "exclusive OR" choice, meaning that you can choose only one value from the set of values that are listed inside the braces.</span></span>

  <span data-ttu-id="3f887-188">예를 들어 cmdlet에 대 한 구문에는 `New-Alias` **Option** 매개 변수에 대 한 다음 값 열거형이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-188">For example, the syntax for the `New-Alias` cmdlet includes the following value enumeration for the **Option** parameter:</span></span>

  ```powershell
  -Option {None | ReadOnly | Constant | Private | AllScope}
  ```

  <span data-ttu-id="3f887-189">중괄호 및 세로 막대는 **Option** 매개 변수에 대해 나열 된 값 중 하나 (예: "ReadOnly" 또는 "AllScope")를 선택할 수 있음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-189">The braces and vertical bars indicate that you can choose any one of the listed values for the **Option** parameter, such as "ReadOnly" or "AllScope".</span></span>

  ```powershell
  -Option ReadOnly
  ```

## <a name="optional-items"></a><span data-ttu-id="3f887-190">선택적 항목</span><span class="sxs-lookup"><span data-stu-id="3f887-190">Optional Items</span></span>

<span data-ttu-id="3f887-191">대괄호는 `[]` 선택적 항목을 둘러쌉니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-191">Brackets `[]` surround optional items.</span></span> <span data-ttu-id="3f887-192">예를 들어 `New-Alias` cmdlet 구문 설명에서 **Scope** 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-192">For example, in the `New-Alias` cmdlet syntax description, the **Scope** parameter is optional.</span></span> <span data-ttu-id="3f887-193">이는 매개 변수 이름 및 유형을 괄호로 묶어 구문에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-193">This is indicated in the syntax by the brackets around the parameter name and type:</span></span>

```powershell
[-Scope <string>]
```

<span data-ttu-id="3f887-194">다음은 cmdlet의 올바른 사용 예입니다 `New-Alias` .</span><span class="sxs-lookup"><span data-stu-id="3f887-194">Both the following examples are correct uses of the `New-Alias` cmdlet:</span></span>

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd -Value Update-TypeData -Scope Global
```

<span data-ttu-id="3f887-195">매개 변수 이름은 해당 매개 변수의 값이 필요한 경우에도 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-195">A parameter name can be optional even if the value for that parameter is required.</span></span> <span data-ttu-id="3f887-196">이는 cmdlet의이 예제와 같이 매개 변수 이름 주위의 대괄호에 의해 구문에서 표시 됩니다 `New-Alias` .</span><span class="sxs-lookup"><span data-stu-id="3f887-196">This is indicated in the syntax by the brackets around the parameter name but not the parameter type, as in this example from the `New-Alias` cmdlet:</span></span>

```powershell
[-Name] <string> [-Value] <string>
```

<span data-ttu-id="3f887-197">다음 명령은 cmdlet을 올바르게 사용 합니다 `New-Alias` .</span><span class="sxs-lookup"><span data-stu-id="3f887-197">The following commands correctly use the `New-Alias` cmdlet.</span></span> <span data-ttu-id="3f887-198">명령은 동일한 결과를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-198">The commands produce the same result.</span></span>

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd Update-TypeData
New-Alias utd -Value Update-TypeData
New-Alias utd Update-TypeData
```

<span data-ttu-id="3f887-199">매개 변수 이름이 문에 형식으로 포함 되지 않은 경우 Windows PowerShell은 인수 위치를 사용 하 여 매개 변수에 값을 할당 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-199">If the parameter name is not included in the statement as typed, Windows PowerShell tries to use the position of the arguments to assign the values to parameters.</span></span>

<span data-ttu-id="3f887-200">다음 예제는 완전 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-200">The following example is not complete:</span></span>

```powershell
New-Alias utd
```

<span data-ttu-id="3f887-201">이 cmdlet에는 **Name** 및 **Value** 매개 변수 모두에 대 한 값이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-201">This cmdlet requires values for both the **Name** and **Value** parameters.</span></span>

<span data-ttu-id="3f887-202">구문 예제에서는 괄호를 사용 하 여 .NET Framework 형식에 대 한 이름 지정 및 캐스팅에도 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-202">In syntax examples, brackets are also used in naming and casting to .NET Framework types.</span></span> <span data-ttu-id="3f887-203">이 컨텍스트에서 대괄호는 요소가 선택 사항임을 나타내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f887-203">In this context, brackets do not indicate an element is optional.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f887-204">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3f887-204">SEE ALSO</span></span>

- [<span data-ttu-id="3f887-205">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="3f887-205">about_Parameters</span></span>](about_Parameters.md)
- [<span data-ttu-id="3f887-206">Get-Command</span><span class="sxs-lookup"><span data-stu-id="3f887-206">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)
- [<span data-ttu-id="3f887-207">Get-Help</span><span class="sxs-lookup"><span data-stu-id="3f887-207">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)

