---
description: Cmdlet 매개 변수 및 고급 기능에 대 한 사용자 지정 기본값을 설정 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 5/31/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters_default_values?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters_Default_Values
ms.openlocfilehash: 286ffff28a88dbb29ce3ce83cea02b403eafd992
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223370"
---
# <a name="about-parameters-default-values"></a><span data-ttu-id="a6432-104">매개 변수 기본값 정보</span><span class="sxs-lookup"><span data-stu-id="a6432-104">About Parameters Default Values</span></span>

## <a name="short-description"></a><span data-ttu-id="a6432-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="a6432-105">Short description</span></span>

<span data-ttu-id="a6432-106">Cmdlet 매개 변수 및 고급 기능에 대 한 사용자 지정 기본값을 설정 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-106">Describes how to set custom default values for cmdlet parameters and advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="a6432-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-107">Long description</span></span>

<span data-ttu-id="a6432-108">`$PSDefaultParameterValues`기본 설정 변수를 사용 하 여 cmdlet 또는 고급 기능에 대 한 사용자 지정 기본값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-108">The `$PSDefaultParameterValues` preference variable lets you specify custom default values for any cmdlet or advanced function.</span></span> <span data-ttu-id="a6432-109">Cmdlet 및 고급 함수는 명령에 다른 값을 지정 하지 않는 한 사용자 지정 기본값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-109">Cmdlets and advanced functions use the custom default value unless you specify another value in the command.</span></span>

<span data-ttu-id="a6432-110">Cmdlet 및 고급 함수의 작성자는 해당 매개 변수에 대 한 표준 기본값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-110">The authors of cmdlets and advanced functions set standard default values for their parameters.</span></span> <span data-ttu-id="a6432-111">일반적으로 표준 기본값은 유용 하지만 모든 환경에 적합 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-111">Typically, the standard default values are useful, but they might not be appropriate for all environments.</span></span>

<span data-ttu-id="a6432-112">이 기능은 명령을 사용할 때마다 또는 전자 메일 서버 이름이 나 프로젝트 GUID와 같이 특정 매개 변수 값을 기억할 수 없는 경우 거의 동일한 대체 매개 변수 값을 지정 해야 하는 경우에 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-112">This feature is especially useful when you must specify the same alternate parameter value nearly every time you use the command or when a particular parameter value is difficult to remember, such as an email server name or project GUID.</span></span>

<span data-ttu-id="a6432-113">원하는 기본값이 예측 가능 하면 다른 조건에서 매개 변수에 대해 다른 기본값을 제공 하는 스크립트 블록을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-113">If the desired default value varies predictably, you can specify a script block that provides different default values for a parameter under different conditions.</span></span>

<span data-ttu-id="a6432-114">`$PSDefaultParameterValues` 는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-114">`$PSDefaultParameterValues` was introduced in PowerShell 3.0.</span></span>

## <a name="syntax"></a><span data-ttu-id="a6432-115">구문</span><span class="sxs-lookup"><span data-stu-id="a6432-115">Syntax</span></span>

<span data-ttu-id="a6432-116">`$PSDefaultParameterValues`변수는 키 형식에 **대 한** 개체 형식의 유효성을 검사 하는 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-116">The `$PSDefaultParameterValues` variable is a hash table that validates the format of keys as an object type of **System.Management.Automation.DefaultParameterDictionary**.</span></span> <span data-ttu-id="a6432-117">해시 테이블에는 **키/값** 쌍이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-117">The hash table contains **Key/Value** pairs.</span></span> <span data-ttu-id="a6432-118">**키는** 형식입니다 `CmdletName:ParameterName` .</span><span class="sxs-lookup"><span data-stu-id="a6432-118">A **Key** is in the format `CmdletName:ParameterName`.</span></span> <span data-ttu-id="a6432-119">**값** 은 키에 할당 된 **DefaultValue** 또는 **ScriptBlock** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-119">A **Value** is the **DefaultValue** or **ScriptBlock** assigned to the key.</span></span>

<span data-ttu-id="a6432-120">`$PSDefaultParameterValues`기본 설정 변수의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-120">The syntax of the `$PSDefaultParameterValues` preference variable is as follows:</span></span>

```
$PSDefaultParameterValues=@{"CmdletName:ParameterName"="DefaultValue"}

$PSDefaultParameterValues=@{ "CmdletName:ParameterName"={{ScriptBlock}} }

$PSDefaultParameterValues["Disabled"]=$True | $False
```

<span data-ttu-id="a6432-121">**CmdletName** 및 **ParameterName** 값에 와일드 카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-121">Wildcard characters are permitted in the **CmdletName** and **ParameterName** values.</span></span>

<span data-ttu-id="a6432-122">에서 특정 **키/값** 쌍을 설정, 변경, 추가 또는 제거 하려면 `$PSDefaultParameterValues` 메서드를 사용 하 여 표준 해시 테이블을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-122">To set, change, add, or remove a specific **Key/Value** pair from `$PSDefaultParameterValues`, use the methods to edit a standard hash table.</span></span> <span data-ttu-id="a6432-123">예를 들어 **Add** 및 **Remove** 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-123">For example, the **Add** and **Remove** methods.</span></span> <span data-ttu-id="a6432-124">이러한 메서드는 해시 테이블의 다른 값을 덮어쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-124">These methods don't overwrite other values in the hash table.</span></span>

<span data-ttu-id="a6432-125">기존 해시 테이블을 덮어쓰지 않는 또 다른 구문이 있습니다 `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="a6432-125">There's another syntax that doesn't overwrite an existing `$PSDefaultParameterValues` hash table.</span></span> <span data-ttu-id="a6432-126">특정 **키/값** 쌍을 추가 하거나 변경 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-126">To add or change a specific **Key/Value** pair, use the following syntax:</span></span>

```
$PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

<span data-ttu-id="a6432-127">**CmdletName** 는 **cmdletbinding** 특성을 사용 하는 cmdlet의 이름 또는 고급 함수의 이름 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-127">The **CmdletName** must be the name of a cmdlet or the name of an advanced function that uses the **CmdletBinding** attribute.</span></span> <span data-ttu-id="a6432-128">`$PSDefaultParameterValues`를 사용 하 여 스크립트 또는 간단한 함수에 대 한 기본값을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-128">You can't use `$PSDefaultParameterValues` to specify default values for scripts or simple functions.</span></span>

<span data-ttu-id="a6432-129">**DefaultValue** 는 개체 또는 스크립트 블록일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-129">The **DefaultValue** can be an object or a script block.</span></span> <span data-ttu-id="a6432-130">값이 스크립트 블록인 경우 PowerShell은 스크립트 블록을 평가 하 고 결과를 매개 변수 값으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-130">If the value is a script block, PowerShell evaluates the script block and uses the result as the parameter value.</span></span> <span data-ttu-id="a6432-131">지정 된 매개 변수가 스크립트 블록 값을 허용 하는 경우 다음과 같이 두 번째 중괄호 집합으로 스크립트 블록 값을 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-131">When the specified parameter accepts a script block value, enclose the script block value in a second set of braces, such as:</span></span>

```powershell
$PSDefaultParameterValues=@{ "Invoke-Command:ScriptBlock"={{Get-Process}} }
```

<span data-ttu-id="a6432-132">자세한 내용은 다음 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a6432-132">For more information, see the following documents:</span></span>

- [<span data-ttu-id="a6432-133">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="a6432-133">about_Hash_Tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="a6432-134">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="a6432-134">about_Script_Blocks</span></span>](about_Script_Blocks.md)
- [<span data-ttu-id="a6432-135">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="a6432-135">about_Preference_Variables</span></span>](about_Preference_Variables.md)

## <a name="examples"></a><span data-ttu-id="a6432-136">예</span><span class="sxs-lookup"><span data-stu-id="a6432-136">Examples</span></span>

### <a name="how-to-set-psdefaultparametervalues"></a><span data-ttu-id="a6432-137">PSDefaultParameterValues 설정 방법 \$</span><span class="sxs-lookup"><span data-stu-id="a6432-137">How to set \$PSDefaultParameterValues</span></span>

<span data-ttu-id="a6432-138">`$PSDefaultParameterValues` 는 기본 설정 변수 이므로 설정 된 세션에만 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-138">`$PSDefaultParameterValues` is a preference variable, so it exists only in the session in which it's set.</span></span> <span data-ttu-id="a6432-139">기본값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-139">It has no default value.</span></span>

<span data-ttu-id="a6432-140">설정 하려면 `$PSDefaultParameterValues` 변수 이름과 하나 이상의 **키/값** 쌍을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-140">To set `$PSDefaultParameterValues`, type the variable name and one or more **Key/Value** pairs.</span></span> <span data-ttu-id="a6432-141">다른 명령을 실행 하 `$PSDefaultParameterValues` 는 경우 기존 해시 테이블을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-141">If you run another `$PSDefaultParameterValues` command, it overwrites the existing hash table.</span></span>

<span data-ttu-id="a6432-142">기존 해시 테이블 값을 덮어쓰지 않고 **키/값** 쌍을 변경 하는 방법에 대 한 예제는 [ \$ PSDefaultParameterValues에 값을 추가](#how-to-add-values-to-psdefaultparametervalues) 하는 방법 또는 [ \$ PSDefaultParameterValues에서 값을 변경](#how-to-change-values-in-psdefaultparametervalues)하는 방법을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a6432-142">For examples about how to change **Key/Value** pairs without overwriting existing hash table values, see [How to add values to \$PSDefaultParameterValues](#how-to-add-values-to-psdefaultparametervalues) or [How to change values in \$PSDefaultParameterValues](#how-to-change-values-in-psdefaultparametervalues).</span></span>

<span data-ttu-id="a6432-143">`$PSDefaultParameterValues`이후 세션을 위해 저장 하려면 `$PSDefaultParameterValues` PowerShell 프로필에 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-143">To save `$PSDefaultParameterValues` for future sessions, add a `$PSDefaultParameterValues` command to your PowerShell profile.</span></span> <span data-ttu-id="a6432-144">자세한 내용은 [about_Profiles](about_Profiles.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a6432-144">For more information, see [about_Profiles](about_Profiles.md).</span></span>

#### <a name="set-a-custom-default-value"></a><span data-ttu-id="a6432-145">사용자 지정 기본값 설정</span><span class="sxs-lookup"><span data-stu-id="a6432-145">Set a custom default value</span></span>

<span data-ttu-id="a6432-146">**키/값** 쌍은 키를 `Send-MailMessage:SmtpServer` **Server123** 의 사용자 지정 기본값으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-146">The **Key/Value** pair sets the `Send-MailMessage:SmtpServer` key to a custom default value of **Server123**.</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
}
```

#### <a name="set-default-values-for-multiple-parameters"></a><span data-ttu-id="a6432-147">여러 매개 변수에 대 한 기본값 설정</span><span class="sxs-lookup"><span data-stu-id="a6432-147">Set default values for multiple parameters</span></span>

<span data-ttu-id="a6432-148">여러 매개 변수에 대 한 기본값을 설정 하려면 각 **키/값** 쌍을 세미콜론 ()으로 구분 `;` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-148">To set default values for multiple parameters, separate each **Key/Value** pair with a semicolon (`;`).</span></span> <span data-ttu-id="a6432-149">`Send-MailMessage:SmtpServer`및 `Get-WinEvent:LogName` 키는 사용자 지정 기본값으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-149">The `Send-MailMessage:SmtpServer` and `Get-WinEvent:LogName` keys are set to custom default values.</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123";
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
}
```

#### <a name="use-wildcards-and-switch-parameters"></a><span data-ttu-id="a6432-150">와일드 카드 및 스위치 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="a6432-150">Use wildcards and switch parameters</span></span>

<span data-ttu-id="a6432-151">Cmdlet 및 매개 변수 이름에는 와일드 카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-151">The cmdlet and parameter names can contain wildcard characters.</span></span> <span data-ttu-id="a6432-152">및를 사용 `$True` `$False` 하 여 **자세한 정보** 표시와 같은 스위치 매개 변수에 대 한 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-152">Use `$True` and `$False` to set values for switch parameters, such as **Verbose**.</span></span> <span data-ttu-id="a6432-153">일반 매개 변수의 **Verbose** 매개 변수는 `$True` 모든 명령에 대해로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-153">The common parameter's **Verbose** parameter is set to `$True` for all commands.</span></span>

```powershell
$PSDefaultParameterValues = @{"*:Verbose"=$True}
```

#### <a name="use-an-array-for-the-default-value"></a><span data-ttu-id="a6432-154">기본값에 배열을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-154">Use an array for the default value</span></span>

<span data-ttu-id="a6432-155">매개 변수가 여러 값을 사용할 수 있는 경우 여러 값을 기본값으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-155">If a parameter can accept multiple values, an array, you can set multiple values as the default values.</span></span> <span data-ttu-id="a6432-156">키의 기본값은 `Invoke-Command:ComputerName` **Server01** 및 **Server02** 의 배열 값으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-156">The default value of the `Invoke-Command:ComputerName` key is set to an array value of **Server01** and **Server02**.</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Invoke-Command:ComputerName"="Server01","Server02"
}
```

#### <a name="use-a-script-block"></a><span data-ttu-id="a6432-157">스크립트 블록 사용</span><span class="sxs-lookup"><span data-stu-id="a6432-157">Use a script block</span></span>

<span data-ttu-id="a6432-158">스크립트 블록을 사용 하 여 다른 조건에서 매개 변수에 대해 다른 기본값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-158">You can use a script block to specify different default values for a parameter under different conditions.</span></span> <span data-ttu-id="a6432-159">PowerShell은 스크립트 블록을 평가 하 고 그 결과를 기본 매개 변수 값으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-159">PowerShell evaluates the script block and uses the result as the default parameter value.</span></span>

<span data-ttu-id="a6432-160">`Format-Table:AutoSize`키는 매개 변수를 기본값인 **True** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-160">The `Format-Table:AutoSize` key sets that switch parameter to a default value of **True**.</span></span> <span data-ttu-id="a6432-161">문에는가 `If` `$host.Name` PowerShell 콘솔 **ConsoleHost** 해야 하는 조건이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-161">The `If` statement contains a condition that the `$host.Name` must be the PowerShell console, **ConsoleHost**.</span></span>

```powershell
$PSDefaultParameterValues=@{
  "Format-Table:AutoSize"={if ($host.Name -eq "ConsoleHost"){$True}}
}
```

<span data-ttu-id="a6432-162">매개 변수가 스크립트 블록 값을 허용 하는 경우 스크립트 블록을 추가 중괄호 집합으로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-162">If a parameter accepts a script block value, enclose the script block in an extra set of braces.</span></span> <span data-ttu-id="a6432-163">PowerShell에서 외부 스크립트 블록을 평가할 때 결과는 내부 스크립트 블록이 고 기본 매개 변수 값으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-163">When PowerShell evaluates the outer script block, the result is the inner script block, and that is set as the default parameter value.</span></span>

<span data-ttu-id="a6432-164">`Invoke-Command:ScriptBlock`스크립트 블록이 두 번째 중괄호 집합으로 묶여 있으므로 키가 **시스템 이벤트 로그** 의 기본값으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-164">The `Invoke-Command:ScriptBlock` key set to a default value of the **System event log** because the script block is enclosed in a second set of braces.</span></span> <span data-ttu-id="a6432-165">스크립트 블록의 결과는 cmdlet으로 전달 됩니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="a6432-165">The result of the script block is passed to the `Invoke-Command` cmdlet.</span></span>

```powershell
$PSDefaultParameterValues=@{
  "Invoke-Command:ScriptBlock"={{Get-EventLog -Log System}}
}
```

### <a name="how-to-get-psdefaultparametervalues"></a><span data-ttu-id="a6432-166">PSDefaultParameterValues를 가져오는 방법 \$</span><span class="sxs-lookup"><span data-stu-id="a6432-166">How to get \$PSDefaultParameterValues</span></span>

<span data-ttu-id="a6432-167">해시 테이블 값은 PowerShell 프롬프트에서를 입력 하 여 표시 됩니다 `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="a6432-167">The hash table values are displayed by entering `$PSDefaultParameterValues` at the PowerShell prompt.</span></span>

<span data-ttu-id="a6432-168">`$PSDefaultParameterValues`해시 테이블은 3 개의 **키/값** 쌍으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-168">A `$PSDefaultParameterValues` hash table is set with three **Key/Value** pairs.</span></span>
<span data-ttu-id="a6432-169">이 해시 테이블은의 값을 추가, 변경 및 제거 하는 방법을 설명 하는 다음 예제에서 사용 됩니다 `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="a6432-169">This hash table is used in the following examples that describe how to add, change, and remove values from `$PSDefaultParameterValues`.</span></span>

```
PS> $PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
  "Get-*:Verbose"=$True
}

PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

<span data-ttu-id="a6432-170">특정 키의 값을 가져오려면 `CmdletName:ParameterName` 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-170">To get the value of a specific `CmdletName:ParameterName` key, use the following syntax:</span></span>

```
$PSDefaultParameterValues["CmdletName:ParameterName"]
```

<span data-ttu-id="a6432-171">예를 들어 키의 값을 가져올 수 `Send-MailMessage:SmtpServer` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-171">For example, to get the value for the `Send-MailMessage:SmtpServer` key.</span></span>

```
PS> $PSDefaultParameterValues["Send-MailMessage:SmtpServer"]
Server123
```

### <a name="how-to-add-values-to-psdefaultparametervalues"></a><span data-ttu-id="a6432-172">PSDefaultParameterValues에 값을 추가 하는 방법 \$</span><span class="sxs-lookup"><span data-stu-id="a6432-172">How to add values to \$PSDefaultParameterValues</span></span>

<span data-ttu-id="a6432-173">에 값을 추가 하려면 `$PSDefaultParameterValues` **add** 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-173">To add a value to `$PSDefaultParameterValues`, use the **Add** method.</span></span> <span data-ttu-id="a6432-174">값을 추가 해도 해시 테이블의 기존 값에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-174">Adding a value doesn't affect the hash table's existing values.</span></span>

<span data-ttu-id="a6432-175">쉼표 ()를 사용 `,` 하 여 **값** 과 **키** 를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-175">Use a comma (`,`) to separate the **Key** from the **Value**.</span></span> <span data-ttu-id="a6432-176">다음 구문에서는에 대해 **Add** 메서드를 사용 하는 방법을 보여 줍니다 `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="a6432-176">The following syntax shows how to use the **Add** method for `$PSDefaultParameterValues`.</span></span>

```
PS> $PSDefaultParameterValues.Add("CmdletName:ParameterName", "DefaultValue")
```

<span data-ttu-id="a6432-177">이전 예제에서 만든 해시 테이블은 새 **키/값** 쌍으로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-177">The hash table created in the prior example is updated with a new **Key/Value** pair.</span></span> <span data-ttu-id="a6432-178">**Add** 메서드는 키를 `Get-Process:Name` 값 **PowerShell** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-178">The **Add** method sets the `Get-Process:Name` key to the value **PowerShell**.</span></span>

```powershell
$PSDefaultParameterValues.Add("Get-Process:Name", "PowerShell")
```

<span data-ttu-id="a6432-179">다음 구문은 동일한 결과를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-179">The following syntax accomplishes the same result.</span></span>

```powershell
$PSDefaultParameterValues["Get-Process:Name"]="PowerShell"
```

<span data-ttu-id="a6432-180">`$PSDefaultParameterValues`변수는 업데이트 된 해시 테이블을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-180">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="a6432-181">`Get-Process:Name`키를 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-181">The `Get-Process:Name` key was added.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-Process:Name               PowerShell
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-remove-values-from-psdefaultparametervalues"></a><span data-ttu-id="a6432-182">PSDefaultParameterValues에서 값을 제거 하는 방법 \$</span><span class="sxs-lookup"><span data-stu-id="a6432-182">How to remove values from \$PSDefaultParameterValues</span></span>

<span data-ttu-id="a6432-183">에서 값을 제거 하려면 `$PSDefaultParameterValues` 해시 테이블의 **remove** 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-183">To remove a value from `$PSDefaultParameterValues`, use the **Remove** method of hash tables.</span></span> <span data-ttu-id="a6432-184">값을 제거 해도 해시 테이블의 기존 값에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-184">Removing a value doesn't affect the hash table's existing values.</span></span>

<span data-ttu-id="a6432-185">다음 구문에서는에서 **Remove** 메서드를 사용 하는 방법을 보여 줍니다 `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="a6432-185">The following syntax shows how to use the **Remove** method on `$PSDefaultParameterValues`.</span></span>

```
PS> $PSDefaultParameterValues.Remove("CmdletName:ParameterName")
```

<span data-ttu-id="a6432-186">이 예제에서는 이전 예제에서 만든 해시 테이블을 업데이트 하 여 **키/값** 쌍을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-186">In this example, the hash table created in the prior example is updated to remove a **Key/Value** pair.</span></span> <span data-ttu-id="a6432-187">**Remove** 메서드는 키를 제거 합니다 `Get-Process:Name` .</span><span class="sxs-lookup"><span data-stu-id="a6432-187">The **Remove** method removes the `Get-Process:Name` key.</span></span>

```powershell
$PSDefaultParameterValues.Remove("Get-Process:Name")
```

<span data-ttu-id="a6432-188">`$PSDefaultParameterValues`변수는 업데이트 된 해시 테이블을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-188">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="a6432-189">`Get-Process:Name`키가 제거 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-189">The `Get-Process:Name` key was removed.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-change-values-in-psdefaultparametervalues"></a><span data-ttu-id="a6432-190">PSDefaultParameterValues의 값을 변경 하는 방법 \$</span><span class="sxs-lookup"><span data-stu-id="a6432-190">How to change values in \$PSDefaultParameterValues</span></span>

<span data-ttu-id="a6432-191">특정 값에 대 한 변경 내용은 기존 해시 테이블 값에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-191">Changes to a specific value don't affect existing hash table values.</span></span> <span data-ttu-id="a6432-192">에서 특정 **키/값** 쌍을 변경 하려면 `$PSDefaultParameterValues` 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-192">To change a specific **Key/Value** pair in `$PSDefaultParameterValues`, use the following syntax:</span></span>

```
PS> $PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

<span data-ttu-id="a6432-193">이 예제에서는 이전 예제에서 만든 해시 테이블을 업데이트 하 여 **키/값** 쌍을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-193">In this example, the hash table created in the prior example is updated to change a **Key/Value** pair.</span></span> <span data-ttu-id="a6432-194">다음 명령은 `Send-MailMessage:SmtpServer` 키를 새 값 **serverxyz** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-194">The following command changes the `Send-MailMessage:SmtpServer` key to a new value of **ServerXYZ**.</span></span>

```powershell
$PSDefaultParameterValues["Send-MailMessage:SmtpServer"]="ServerXYZ"
```

<span data-ttu-id="a6432-195">`$PSDefaultParameterValues`변수는 업데이트 된 해시 테이블을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-195">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="a6432-196">`Send-MailMessage:SmtpServer`키가 새 값으로 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-196">The `Send-MailMessage:SmtpServer` key was changed to a new value.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

### <a name="how-to-disable-and-re-enable-psdefaultparametervalues"></a><span data-ttu-id="a6432-197">PSDefaultParameterValues를 사용 하지 않도록 설정 하 고 다시 사용 하도록 설정 하는 방법 \$</span><span class="sxs-lookup"><span data-stu-id="a6432-197">How to disable and re-enable \$PSDefaultParameterValues</span></span>

<span data-ttu-id="a6432-198">일시적으로 사용 하지 않도록 설정한 다음 다시 사용 하도록 설정할 수 있습니다 `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="a6432-198">You can temporarily disable and then re-enable `$PSDefaultParameterValues`.</span></span>
<span data-ttu-id="a6432-199">비활성화 `$PSDefaultParameterValues` 는 다른 기본 매개 변수 값이 필요한 스크립트를 실행 하는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-199">Disabling `$PSDefaultParameterValues` is useful if you're running scripts that need different default parameter values.</span></span>

<span data-ttu-id="a6432-200">비활성화 하려면 `$PSDefaultParameterValues` 값이 True 인의 키를 추가 `Disabled` 합니다 **True**.</span><span class="sxs-lookup"><span data-stu-id="a6432-200">To disable `$PSDefaultParameterValues`, add a key of `Disabled` with a value of **True**.</span></span> <span data-ttu-id="a6432-201">의 값은 `$PSDefaultParameterValues` 유지 되지만 유효 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-201">The values in `$PSDefaultParameterValues` are preserved, but aren't effective.</span></span>

```
PS> $PSDefaultParameterValues.Add("Disabled", $True)
```

<span data-ttu-id="a6432-202">다음 구문은 동일한 결과를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-202">The following syntax accomplishes the same result.</span></span>

```
PS> $PSDefaultParameterValues["Disabled"]=$True
```

<span data-ttu-id="a6432-203">`$PSDefaultParameterValues`변수는 키 값을 사용 하 여 업데이트 된 해시 테이블을 표시 합니다 `Disabled` .</span><span class="sxs-lookup"><span data-stu-id="a6432-203">The `$PSDefaultParameterValues` variable displays the updated hash table with the value for the `Disabled` key.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       True
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

<span data-ttu-id="a6432-204">다시 사용 하도록 설정 하려면 `$PSDefaultParameterValues` **사용 하지 않도록** 설정 된 키를 제거 하거나 **사용 하지 않도록 설정** 된 키의 값을로 변경 `$False` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-204">To re-enable `$PSDefaultParameterValues`, remove the **Disabled** key or change the value of the **Disabled** key to `$False`.</span></span> <span data-ttu-id="a6432-205">의 이전 값은 `$PSDefaultParameterValues` 다시 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-205">The previous value of `$PSDefaultParameterValues` is effective again.</span></span>

```
PS> $PSDefaultParameterValues.Remove("Disabled")
```

<span data-ttu-id="a6432-206">다음 구문은 동일한 결과를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-206">The following syntax accomplishes the same result.</span></span>

```
PS> $PSDefaultParameterValues["Disabled"]=$False
```

<span data-ttu-id="a6432-207">`$PSDefaultParameterValues`변수는 업데이트 된 해시 테이블을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-207">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="a6432-208">**Remove** 메서드를 사용 하면 `Disabled` 출력에서 키가 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-208">When the **Remove** method is used, the `Disabled` key is removed from the output.</span></span>
<span data-ttu-id="a6432-209">대체 구문을 사용 하도록 다시 설정 하는 경우 `$PSDefaultParameterValues` `Disabled` 키가 **False** 로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6432-209">If the alternate syntax was used to re-enable `$PSDefaultParameterValues`, the `Disabled` key is displayed as **False**.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       False
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

## <a name="see-also"></a><span data-ttu-id="a6432-210">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a6432-210">See also</span></span>

[<span data-ttu-id="a6432-211">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a6432-211">about_CommonParameters</span></span>](https://go.microsoft.com/fwlink/?LinkID=113216)

[<span data-ttu-id="a6432-212">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="a6432-212">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="a6432-213">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="a6432-213">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="a6432-214">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="a6432-214">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="a6432-215">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="a6432-215">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="a6432-216">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="a6432-216">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="a6432-217">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="a6432-217">about_Script_Blocks</span></span>](about_Script_Blocks.md)
