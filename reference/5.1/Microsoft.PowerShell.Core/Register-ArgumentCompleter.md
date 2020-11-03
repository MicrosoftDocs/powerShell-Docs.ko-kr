---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-argumentcompleter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ArgumentCompleter
ms.openlocfilehash: 1cc6f9f62efc92005c02865ac91cad04164f7655
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212801"
---
# <span data-ttu-id="e7bf6-103">Register-ArgumentCompleter</span><span class="sxs-lookup"><span data-stu-id="e7bf6-103">Register-ArgumentCompleter</span></span>

## <span data-ttu-id="e7bf6-104">개요</span><span class="sxs-lookup"><span data-stu-id="e7bf6-104">SYNOPSIS</span></span>

<span data-ttu-id="e7bf6-105">Completer 사용자 지정 인수를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-105">Registers a custom argument completer.</span></span>

## <span data-ttu-id="e7bf6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e7bf6-106">SYNTAX</span></span>

### <span data-ttu-id="e7bf6-107">NativeSet</span><span class="sxs-lookup"><span data-stu-id="e7bf6-107">NativeSet</span></span>

```
Register-ArgumentCompleter -CommandName <String[]> -ScriptBlock <ScriptBlock> [-Native]
 [<CommonParameters>]
```

### <span data-ttu-id="e7bf6-108">PowerShellSet</span><span class="sxs-lookup"><span data-stu-id="e7bf6-108">PowerShellSet</span></span>

```
Register-ArgumentCompleter [-CommandName <String[]>] -ParameterName <String>
 -ScriptBlock <ScriptBlock> [<CommonParameters>]
```

## <span data-ttu-id="e7bf6-109">설명</span><span class="sxs-lookup"><span data-stu-id="e7bf6-109">DESCRIPTION</span></span>

<span data-ttu-id="e7bf6-110">`Register-ArgumentCompleter`Cmdlet은 사용자 지정 인수 completer을 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-110">The `Register-ArgumentCompleter` cmdlet registers a custom argument completer.</span></span> <span data-ttu-id="e7bf6-111">인수 completer를 사용 하면 런타임에 사용자가 지정 하는 명령에 대해 동적 탭 완성 기능을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-111">An argument completer allows you to provide dynamic tab completion, at run time for any command that you specify.</span></span>

## <span data-ttu-id="e7bf6-112">예제</span><span class="sxs-lookup"><span data-stu-id="e7bf6-112">EXAMPLES</span></span>

### <span data-ttu-id="e7bf6-113">예제 1: 사용자 지정 인수 completer 등록</span><span class="sxs-lookup"><span data-stu-id="e7bf6-113">Example 1: Register a custom argument completer</span></span>

<span data-ttu-id="e7bf6-114">다음 예에서는 cmdlet의 **Id** 매개 변수에 completer 인수를 등록 합니다 `Set-TimeZone` .</span><span class="sxs-lookup"><span data-stu-id="e7bf6-114">The following example registers an argument completer for the **Id** parameter of the `Set-TimeZone` cmdlet.</span></span>

```powershell
$scriptBlock = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)

    (Get-TimeZone -ListAvailable).Id | Where-Object {
        $_ -like "$wordToComplete*"
    } | ForEach-Object {
          "'$_'"
    }
}
Register-ArgumentCompleter -CommandName Set-TimeZone -ParameterName Id -ScriptBlock $scriptBlock
```

<span data-ttu-id="e7bf6-115">첫 번째 명령은 사용자가 <kbd>Tab</kbd>키를 누를 때 전달 되는 필수 매개 변수를 사용 하는 스크립트 블록을 만듭니다. 자세한 내용은 **ScriptBlock** 매개 변수 설명을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-115">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="e7bf6-116">스크립트 블록 내에서 **Id** 에 사용할 수 있는 값은 cmdlet을 사용 하 여 검색 됩니다 `Get-TimeZone` .</span><span class="sxs-lookup"><span data-stu-id="e7bf6-116">Within the script block, the available values for **Id** are retrieved using the `Get-TimeZone` cmdlet.</span></span> <span data-ttu-id="e7bf6-117">각 표준 시간대에 대 한 **Id** 속성은 cmdlet으로 파이프 됩니다 `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="e7bf6-117">The **Id** property for each Time Zone is piped to the `Where-Object` cmdlet.</span></span> <span data-ttu-id="e7bf6-118">`Where-Object`Cmdlet은에서 제공 하는 값으로 시작 하지 않는 모든 id를 필터링 합니다 .이 값은 `$wordToComplete` 사용자가 <kbd>Tab</kbd>키를 눌러 입력 한 텍스트를 나타냅니다. 필터링 된 id는 `For-EachObject` 값에 공백이 포함 되어 있는 경우 각 값을 따옴표로 묶는 cmdlet으로 파이프 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-118">The `Where-Object` cmdlet filters out any ids that do not start with the value provided by `$wordToComplete`, which represents the text the user typed before they pressed <kbd>Tab</kbd>. The filtered ids are piped to the `For-EachObject` cmdlet which encloses each value in quotes, should the value contain spaces.</span></span>

<span data-ttu-id="e7bf6-119">두 번째 명령은 scriptblock, **ParameterName** **Id** 및 **CommandName** 을 전달 하 여 completer 인수를 등록 합니다 `Set-TimeZone` .</span><span class="sxs-lookup"><span data-stu-id="e7bf6-119">The second command registers the argument completer by passing the scriptblock, the **ParameterName** **Id** and the **CommandName** `Set-TimeZone`.</span></span>

### <span data-ttu-id="e7bf6-120">예제 2: 탭 완성 값에 세부 정보 추가</span><span class="sxs-lookup"><span data-stu-id="e7bf6-120">Example 2: Add details to your tab completion values</span></span>

<span data-ttu-id="e7bf6-121">다음 예에서는 cmdlet의 **Name** 매개 변수에 대 한 탭 완성을 덮어쓰고 `Stop-Service` 실행 중인 서비스만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-121">The following example overwrites tab completion for the **Name** parameter of the `Stop-Service` cmdlet and only returns running services.</span></span>

```powershell
$s = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)
    $services = Get-Service | Where-Object {$_.Status -eq "Running" -and $_.Name -like "$wordToComplete*"}
    $services | ForEach-Object {
        New-Object -Type System.Management.Automation.CompletionResult -ArgumentList $_.Name,
            $_.Name,
            "ParameterValue",
            $_.Name
    }
}
Register-ArgumentCompleter -CommandName Stop-Service -ParameterName Name -ScriptBlock $s
```

<span data-ttu-id="e7bf6-122">첫 번째 명령은 사용자가 <kbd>Tab</kbd>키를 누를 때 전달 되는 필수 매개 변수를 사용 하는 스크립트 블록을 만듭니다. 자세한 내용은 **ScriptBlock** 매개 변수 설명을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-122">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="e7bf6-123">스크립트 블록 내에서 첫 번째 명령은 cmdlet을 사용 하 여 실행 중인 모든 서비스를 검색 합니다 `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="e7bf6-123">Within the script block, the first command retrieves all running services using the `Where-Object` cmdlet.</span></span> <span data-ttu-id="e7bf6-124">서비스는 cmdlet으로 파이프 됩니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="e7bf6-124">The services are piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="e7bf6-125">`ForEach-Object`Cmdlet은 새 개체를 만들어 [`[System.Management.Automation.CompletionResult]`](/dotnet/api/system.management.automation.completionresult) 현재 서비스 (파이프라인 변수로 표시 됨)의 값으로 채웁니다 `$_` .</span><span class="sxs-lookup"><span data-stu-id="e7bf6-125">The `ForEach-Object` cmdlet creates a new [`[System.Management.Automation.CompletionResult]`](/dotnet/api/system.management.automation.completionresult) object and populates it with the values of the current service (represented by the pipeline variable `$_`).</span></span>

<span data-ttu-id="e7bf6-126">가 중 **결과** 개체를 사용 하 여 반환 된 각 값에 추가 세부 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-126">The **CompletionResult** object allows you to provide additional details to each returned value:</span></span>

- <span data-ttu-id="e7bf6-127">**완성도 텍스트** (String)-자동 완성 결과로 사용할 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-127">**completionText** (String) - The text to be used as the auto completion result.</span></span> <span data-ttu-id="e7bf6-128">이 값은 명령으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-128">This is the value sent to the command.</span></span>
- <span data-ttu-id="e7bf6-129">**listitemtext** (String)-사용자가 <kbd>Ctrl</kbd>Space를 누르는 경우와 같이 목록에 표시 되는 텍스트 + <kbd>Space</kbd>입니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-129">**listItemText** (String) - The text to be displayed in a list, such as when the user presses <kbd>Ctrl</kbd>+<kbd>Space</kbd>.</span></span> <span data-ttu-id="e7bf6-130">이는 표시 용 으로만 사용 되며 선택한 경우 명령에 전달 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-130">This is used for display only and is not passed to the command when selected.</span></span>
- <span data-ttu-id="e7bf6-131">**resultType** ( [완성도 resultType](/dotnet/api/system.management.automation.completionresulttype))-완료 결과의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-131">**resultType** ([CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)) - The type of completion result.</span></span>
- <span data-ttu-id="e7bf6-132">**tooltip** (String)-개체에 대 한 세부 정보가 표시 되는 도구 설명 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-132">**toolTip** (String) - The text for the tooltip with details to be displayed about the object.</span></span>
  <span data-ttu-id="e7bf6-133">이는 <kbd>Ctrl</kbd>Space를 누른 후 사용자가 항목을 선택할 때 표시 됩니다 + <kbd>Space</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-133">This is visible when the user selects an item after pressing <kbd>Ctrl</kbd>+<kbd>Space</kbd>.</span></span>

<span data-ttu-id="e7bf6-134">마지막 명령은 중지 된 서비스를 계속 cmdlet에 수동으로 전달할 수 있음을 보여 줍니다 `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="e7bf6-134">The last command demonstrates that stopped services can still be passed in manually to the `Stop-Service` cmdlet.</span></span> <span data-ttu-id="e7bf6-135">탭 완성은 영향을 받는 유일한 측면입니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-135">The tab completion is the only aspect affected.</span></span>

### <span data-ttu-id="e7bf6-136">예제 3: 사용자 지정 네이티브 인수 등록 completer</span><span class="sxs-lookup"><span data-stu-id="e7bf6-136">Example 3: Register a custom Native argument completer</span></span>

<span data-ttu-id="e7bf6-137">**네이티브 매개 변수** 를 사용 하 여 네이티브 명령에 대 한 탭 완성 기능을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-137">You can use the **Native** parameter to provide tab-completion for a native command.</span></span> <span data-ttu-id="e7bf6-138">다음 예제에서는 `dotnet` CLI (명령줄 인터페이스)에 대 한 탭 완성 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-138">The following example adds tab-completion for the `dotnet` Command Line Interface (CLI).</span></span>

> [!NOTE]
> <span data-ttu-id="e7bf6-139">`dotnet complete`이 명령은 dotnet cli 버전 2.0 이상 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-139">The `dotnet complete` command is only available in version 2.0 and greater of the dotnet cli.</span></span>

```powershell
$scriptblock = {
    param($wordToComplete, $commandAst, $cursorPosition)
        dotnet complete --position $cursorPosition $commandAst.ToString() | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
        }
}
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock $scriptblock
```

<span data-ttu-id="e7bf6-140">첫 번째 명령은 사용자가 <kbd>Tab</kbd>키를 누를 때 전달 되는 필수 매개 변수를 사용 하는 스크립트 블록을 만듭니다. 자세한 내용은 **ScriptBlock** 매개 변수 설명을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-140">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="e7bf6-141">스크립트 블록 내에서 `dotnet complete` 명령은 탭 완성을 수행 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-141">Within the script block, the `dotnet complete` command is used to perform the tab completion.</span></span>
<span data-ttu-id="e7bf6-142">결과는 cmdlet으로 파이프 됩니다. `ForEach-Object` 이 cmdlet은 각 값에 대해 새로운 [메이 션](/dotnet/api/system.management.automation.completionresult) 개체를 만들기 위해 **새** 정적 메서드를 사용 하 여 **CompletionResult** 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-142">The results are piped to the `ForEach-Object` cmdlet which use the **new** static method of the [System.Management.Automation.CompletionResult](/dotnet/api/system.management.automation.completionresult) class to create a new **CompletionResult** object for each value.</span></span>

## <span data-ttu-id="e7bf6-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e7bf6-143">PARAMETERS</span></span>

### <span data-ttu-id="e7bf6-144">-CommandName</span><span class="sxs-lookup"><span data-stu-id="e7bf6-144">-CommandName</span></span>

<span data-ttu-id="e7bf6-145">명령의 이름을 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-145">Specifies the name of the commands as an array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NativeSet, PowerShellSet
Aliases:

Required: True (NativeSet), False (PowerShellSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7bf6-146">-네이티브</span><span class="sxs-lookup"><span data-stu-id="e7bf6-146">-Native</span></span>

<span data-ttu-id="e7bf6-147">Completer 인수가 PowerShell에서 매개 변수 이름을 완료할 수 없는 네이티브 명령에 대 한 것임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-147">Indicates that the argument completer is for a native command where PowerShell cannot complete parameter names.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NativeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7bf6-148">-ParameterName</span><span class="sxs-lookup"><span data-stu-id="e7bf6-148">-ParameterName</span></span>

<span data-ttu-id="e7bf6-149">인수를 완료할 매개 변수의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-149">Specifies the name of the parameter whose argument is being completed.</span></span> <span data-ttu-id="e7bf6-150">지정 된 매개 변수 이름은 cmdlet의 **ForegroundColor** 매개 변수와 같은 열거 값일 수 없습니다 `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="e7bf6-150">The parameter name specified cannot be an enumerated value, such as the **ForegroundColor** parameter of the `Write-Host` cmdlet.</span></span>

<span data-ttu-id="e7bf6-151">열거형에 대 한 자세한 내용은 [about_Enum](./About/about_Enum.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-151">For more information on enums, see [about_Enum](./About/about_Enum.md).</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7bf6-152">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="e7bf6-152">-ScriptBlock</span></span>

<span data-ttu-id="e7bf6-153">탭 완성을 수행 하기 위해 실행할 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-153">Specifies the commands to run to perform tab completion.</span></span> <span data-ttu-id="e7bf6-154">사용자가 제공 하는 스크립트 블록은 입력을 완료 하는 값을 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-154">The script block you provide should return the values that complete the input.</span></span> <span data-ttu-id="e7bf6-155">스크립트 블록은 파이프라인 ( `ForEach-Object` , 등 `Where-Object` ) 또는 다른 적합 한 메서드를 사용 하 여 값을 언 롤 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-155">The script block must unroll the values using the pipeline (`ForEach-Object`, `Where-Object`, etc.), or another suitable method.</span></span> <span data-ttu-id="e7bf6-156">값의 배열을 반환 하면 PowerShell에서 전체 배열을 **하나의** 탭 완성 값으로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-156">Returning an array of values causes PowerShell to treat the entire array as **one** tab completion value.</span></span>

<span data-ttu-id="e7bf6-157">스크립트 블록은 아래 지정 된 순서 대로 다음 매개 변수를 허용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-157">The script block must accept the following parameters in the order specified below.</span></span> <span data-ttu-id="e7bf6-158">PowerShell이 위치에 따라 값을 전달 하므로 매개 변수 이름은 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-158">The names of the parameters aren't important because PowerShell passes in the values by position.</span></span>

- <span data-ttu-id="e7bf6-159">`$commandName` (위치 0)-이 매개 변수는 스크립트 블록에서 탭 완성 기능을 제공 하는 명령 이름으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-159">`$commandName` (Position 0) - This parameter is set to the name of the command for which the script block is providing tab completion.</span></span>
- <span data-ttu-id="e7bf6-160">`$parameterName` (위치 1)-이 매개 변수는 값이 탭 완성이 필요한 매개 변수로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-160">`$parameterName` (Position 1) - This parameter is set to the parameter whose value requires tab completion.</span></span>
- <span data-ttu-id="e7bf6-161">`$wordToComplete` (위치 2)-이 매개 변수는 <kbd>Tab</kbd>키를 누를 때 사용자가 제공한 값으로 설정 됩니다. 스크립트 블록은이 값을 사용 하 여 탭 완성 값을 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-161">`$wordToComplete` (Position 2) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="e7bf6-162">`$commandAst` (위치 3)-이 매개 변수는 현재 입력 줄에 대 한 AST (추상 구문 트리)로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-162">`$commandAst` (Position 3) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="e7bf6-163">자세한 내용은 [Ast 클래스](/dotnet/api/system.management.automation.language.ast)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-163">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="e7bf6-164">`$fakeBoundParameters` (위치 4)-이 매개 변수는 `$PSBoundParameters` 사용자가 <kbd>Tab</kbd>키를 눌러 cmdlet에 대 한를 포함 하는 해시 테이블로 설정 됩니다. 자세한 내용은 [about_Automatic_Variables](./About/about_Automatic_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-164">`$fakeBoundParameters` (Position 4) - This parameter is set to a hashtable containing the `$PSBoundParameters` for the cmdlet, before the user pressed <kbd>Tab</kbd>. For more information, see [about_Automatic_Variables](./About/about_Automatic_Variables.md).</span></span>

<span data-ttu-id="e7bf6-165">**네이티브** 매개 변수를 지정 하는 경우 스크립트 블록은 지정 된 순서로 다음 매개 변수를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-165">When you specify the **Native** parameter, the script block must take the following parameters in the specified order.</span></span> <span data-ttu-id="e7bf6-166">PowerShell이 위치에 따라 값을 전달 하므로 매개 변수 이름은 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-166">The names of the parameters aren't important because PowerShell passes in the values by position.</span></span>

- <span data-ttu-id="e7bf6-167">`$wordToComplete` (위치 0)-이 매개 변수는 <kbd>Tab</kbd>키를 누르기 전에 사용자가 제공한 값으로 설정 됩니다. 스크립트 블록은이 값을 사용 하 여 탭 완성 값을 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-167">`$wordToComplete` (Position 0) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="e7bf6-168">`$commandAst` (위치 1)-이 매개 변수는 현재 입력 줄에 대 한 AST (추상 구문 트리)로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-168">`$commandAst` (Position 1) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="e7bf6-169">자세한 내용은 [Ast 클래스](/dotnet/api/system.management.automation.language.ast)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-169">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="e7bf6-170">`$cursorPosition` (위치 2)-이 매개 변수는 사용자가 <kbd>Tab</kbd>키를 누를 때 커서의 위치로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-170">`$cursorPosition` (Position 2) - This parameter is set to the position of the cursor when the user pressed <kbd>Tab</kbd>.</span></span>

<span data-ttu-id="e7bf6-171">**ArgumentCompleter** 를 매개 변수 특성으로 제공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-171">You can also provide an **ArgumentCompleter** as a parameter attribute.</span></span> <span data-ttu-id="e7bf6-172">자세한 내용은 [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-172">For more information, see [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7bf6-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e7bf6-173">CommonParameters</span></span>

<span data-ttu-id="e7bf6-174">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e7bf6-175">자세한 내용은 [about_CommonParameters](./About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-175">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="e7bf6-176">입력</span><span class="sxs-lookup"><span data-stu-id="e7bf6-176">INPUTS</span></span>

### <span data-ttu-id="e7bf6-177">없음</span><span class="sxs-lookup"><span data-stu-id="e7bf6-177">None</span></span>

<span data-ttu-id="e7bf6-178">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-178">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="e7bf6-179">출력</span><span class="sxs-lookup"><span data-stu-id="e7bf6-179">OUTPUTS</span></span>

### <span data-ttu-id="e7bf6-180">없음</span><span class="sxs-lookup"><span data-stu-id="e7bf6-180">None</span></span>

<span data-ttu-id="e7bf6-181">이 cmdlet은 출력을 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-181">This cmdlet returns no output.</span></span>

## <span data-ttu-id="e7bf6-182">참고</span><span class="sxs-lookup"><span data-stu-id="e7bf6-182">NOTES</span></span>

## <span data-ttu-id="e7bf6-183">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e7bf6-183">RELATED LINKS</span></span>
