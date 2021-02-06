---
description: 원격 명령에서 로컬 및 원격 변수를 사용하는 방법을 설명합니다.
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Variables
ms.openlocfilehash: 1cd6d0c4562fcd63fc56f103ec41aa6f0bb4c01c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603286"
---
# <a name="about-remote-variables"></a><span data-ttu-id="e151b-103">원격 변수 정보</span><span class="sxs-lookup"><span data-stu-id="e151b-103">About Remote Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="e151b-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="e151b-104">Short description</span></span>

<span data-ttu-id="e151b-105">원격 명령에서 로컬 및 원격 변수를 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-105">Explains how to use local and remote variables in remote commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="e151b-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-106">Long description</span></span>

<span data-ttu-id="e151b-107">원격 컴퓨터에서 실행 하는 명령에서 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-107">You can use variables in commands that you run on remote computers.</span></span> <span data-ttu-id="e151b-108">변수에 값을 할당 한 다음 값 대신 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-108">Assign a value to the variable and then use the variable in place of the value.</span></span>

<span data-ttu-id="e151b-109">기본적으로 원격 명령의 변수는 명령을 실행 하는 세션에서 정의 된 것으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-109">By default, the variables in remote commands are assumed to be defined in the session that runs the command.</span></span> <span data-ttu-id="e151b-110">로컬 세션에 정의 된 변수는 명령에서 지역 변수로 식별 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-110">Variables that are defined in a local session, must be identified as local variables in the command.</span></span>

## <a name="using-remote-variables"></a><span data-ttu-id="e151b-111">원격 변수 사용</span><span class="sxs-lookup"><span data-stu-id="e151b-111">Using remote variables</span></span>

<span data-ttu-id="e151b-112">PowerShell에서는 명령이 실행 되는 세션에서 원격 명령에 사용 된 변수가 정의 되어 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-112">PowerShell assumes that the variables used in remote commands are defined in the session in which the command runs.</span></span>

<span data-ttu-id="e151b-113">이 예제에서 변수는 `$ps` 명령이 실행 되는 임시 세션에서 정의 됩니다 `Get-WinEvent` .</span><span class="sxs-lookup"><span data-stu-id="e151b-113">In this example, the `$ps` variable is defined in the temporary session in which the `Get-WinEvent` command runs.</span></span>

```powershell
Invoke-Command -ComputerName S1 -ScriptBlock {
  $ps = "*PowerShell*"; Get-WinEvent -LogName $ps
}
```

<span data-ttu-id="e151b-114">명령이 영구 세션 **PSSession** 에서 실행 되는 경우 해당 세션에서 원격 변수를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-114">When the command runs in a persistent session, **PSSession**, the remote variable must be defined in that session.</span></span>

```powershell
$s = New-PSSession -ComputerName S1
Invoke-Command -Session $s -ScriptBlock {$ps = "*PowerShell*"}
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $ps}
```

## <a name="using-local-variables"></a><span data-ttu-id="e151b-115">지역 변수 사용</span><span class="sxs-lookup"><span data-stu-id="e151b-115">Using local variables</span></span>

<span data-ttu-id="e151b-116">원격 명령의 지역 변수를 사용할 수 있지만 변수는 로컬 세션에서 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-116">You can use local variables in remote commands, but the variable must be defined in the local session.</span></span>

<span data-ttu-id="e151b-117">PowerShell 3.0부터 범위 한정자를 사용 하 여 `Using` 원격 명령에서 지역 변수를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-117">Beginning in PowerShell 3.0, you can use the `Using` scope modifier to identify a local variable in a remote command.</span></span>

<span data-ttu-id="e151b-118">의 구문은 다음과 같습니다 `Using` .</span><span class="sxs-lookup"><span data-stu-id="e151b-118">The syntax of `Using` is as follows:</span></span>

```
$Using:<VariableName>
```

<span data-ttu-id="e151b-119">다음 예에서는 `$ps` 변수가 로컬 세션에서 만들어지지만 명령이 실행 되는 세션에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-119">In the following example, the `$ps` variable is created in the local session, but is used in the session in which the command runs.</span></span> <span data-ttu-id="e151b-120">`Using`범위 한정자는를 `$ps` 지역 변수로 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-120">The `Using` scope modifier identifies `$ps` as a local variable.</span></span>

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  Get-WinEvent -LogName $Using:ps
}
```

<span data-ttu-id="e151b-121">`Using`범위 한정자는 **PSSession** 에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-121">The `Using` scope modifier can be used in a **PSSession**.</span></span>

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $Using:ps}
```

<span data-ttu-id="e151b-122">와 같은 변수 참조는 `$using:var` 호출자의 컨텍스트에서 변수 값으로 확장 `$var` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-122">A variable reference such as `$using:var` expands to the value of variable `$var` from the caller's context.</span></span> <span data-ttu-id="e151b-123">호출자의 변수 개체에 대 한 액세스 권한을 얻을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-123">You do not get access to the caller's variable object.</span></span>
<span data-ttu-id="e151b-124">`Using`범위 한정자는 **PSSession** 내에서 지역 변수를 수정 하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-124">The `Using` scope modifier cannot be used to modify a local variable within the **PSSession**.</span></span> <span data-ttu-id="e151b-125">예를 들어 다음 코드는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-125">For example, the following code does not work:</span></span>

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {$Using:ps = 'Cannot assign new value'}
```

<span data-ttu-id="e151b-126">에 대 한 자세한 내용은 `Using` 을 참조 하십시오 [about_Scopes](./about_Scopes.md)</span><span class="sxs-lookup"><span data-stu-id="e151b-126">For more information about `Using`, see [about_Scopes](./about_Scopes.md)</span></span>

### <a name="using-splatting"></a><span data-ttu-id="e151b-127">스 플랫 사용</span><span class="sxs-lookup"><span data-stu-id="e151b-127">Using splatting</span></span>

<span data-ttu-id="e151b-128">PowerShell 스 플랫는 매개 변수 이름 및 값의 컬렉션을 명령에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-128">PowerShell splatting passes a collection of parameter names and values to a command.</span></span> <span data-ttu-id="e151b-129">자세한 내용은 [about_Splatting](about_Splatting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e151b-129">For more information, see [about_Splatting](about_Splatting.md).</span></span>

<span data-ttu-id="e151b-130">이 예에서 스 플랫 변수는 `$Splat` 로컬 컴퓨터에 설정 된 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-130">In this example, the splatting variable, `$Splat` is a hash table that is set up on the local computer.</span></span> <span data-ttu-id="e151b-131">는 `Invoke-Command` 원격 컴퓨터 세션에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-131">The `Invoke-Command` connects to a remote computer session.</span></span> <span data-ttu-id="e151b-132">**ScriptBlock** 은 `Using` Scope 한정자와 At () 기호를 사용 하 여 `@` splatted 변수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-132">The **ScriptBlock** uses the `Using` scope modifier with the At (`@`) symbol to represent the splatted variable.</span></span>

```powershell
$Splat = @{ Name = "Win*"; Include = "WinRM" }
Invoke-Command -Session $s -ScriptBlock { Get-Service @Using:Splat }
```

### <a name="other-situations-where-the-using-scope-modifier-is-needed"></a><span data-ttu-id="e151b-133">' Using ' 범위 한정자가 필요한 다른 상황</span><span class="sxs-lookup"><span data-stu-id="e151b-133">Other situations where the 'Using' scope modifier is needed</span></span>

<span data-ttu-id="e151b-134">세션에서 실행 되지 않는 스크립트나 명령의 경우 범위 한정자를 사용 하 여 `Using` 호출 세션 범위의 변수 값을 포함 해야 합니다. 이렇게 하면 세션 외부 코드에서 해당 값에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-134">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span> <span data-ttu-id="e151b-135">`Using`범위 한정자는 다음 컨텍스트에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-135">The `Using` scope modifier is supported in the following contexts:</span></span>

- <span data-ttu-id="e151b-136">원격으로 실행 되는 명령, `Invoke-Command` **ComputerName**, **HostName**, **SSHConnection** 또는 **Session** 매개 변수를 사용 하 여 시작 (원격 세션)</span><span class="sxs-lookup"><span data-stu-id="e151b-136">Remotely executed commands, started with `Invoke-Command` using the **ComputerName**, **HostName**, **SSHConnection** or **Session** parameters (remote session)</span></span>
- <span data-ttu-id="e151b-137">백그라운드 작업, 시작 `Start-Job` (out-of-process 세션)</span><span class="sxs-lookup"><span data-stu-id="e151b-137">Background jobs, started with `Start-Job` (out-of-process session)</span></span>
- <span data-ttu-id="e151b-138">스레드 작업, `Start-ThreadJob` 또는 `ForEach-Object -Parallel` (개별 스레드 세션)를 통해 시작</span><span class="sxs-lookup"><span data-stu-id="e151b-138">Thread jobs, started via `Start-ThreadJob` or `ForEach-Object -Parallel` (separate thread session)</span></span>

<span data-ttu-id="e151b-139">컨텍스트에 따라 포함 된 변수 값은 호출자의 범위에 있는 데이터의 독립적인 복사본 이거나이에 대 한 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-139">Depending on the context, embedded variable values are either independent copies of the data in the caller's scope or references to it.</span></span> <span data-ttu-id="e151b-140">원격 및 out-of-process 세션에서 항상 독립적인 복사본입니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-140">In remote and out-of-process sessions, they are always independent copies.</span></span> <span data-ttu-id="e151b-141">스레드 세션에서는 참조로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-141">In thread sessions, they are passed by reference.</span></span>

## <a name="serialization-of-variable-values"></a><span data-ttu-id="e151b-142">변수 값의 Serialization</span><span class="sxs-lookup"><span data-stu-id="e151b-142">Serialization of variable values</span></span>

<span data-ttu-id="e151b-143">원격으로 실행 되는 명령 및 백그라운드 작업은 out-of-process로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-143">Remotely executed commands and background jobs run out-of-process.</span></span>
<span data-ttu-id="e151b-144">Out-of-process 세션은 XML 기반 serialization 및 deserialization을 사용 하 여 프로세스 경계를 넘어 변수 값을 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-144">Out-of-process sessions use XML-based serialization and deserialization to make the values of variables available across the process boundaries.</span></span> <span data-ttu-id="e151b-145">Serialization 프로세스는 개체를 원래 개체 속성이 있지만 메서드는 포함 하지 않는 **PSObject** 로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-145">The serialization process converts objects to a **PSObject** that contains the original objects properties but not its methods.</span></span>

<span data-ttu-id="e151b-146">제한 된 형식 집합의 경우 deserialization 리하이드레이션 할 개체를 원래 형식으로 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-146">For a limited set of types, deserialization rehydrates objects back to the original type.</span></span> <span data-ttu-id="e151b-147">원래 개체 인스턴스의 복사본입니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-147">The rehydrated object is a copy of the original object instance.</span></span>
<span data-ttu-id="e151b-148">형식 속성 및 메서드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-148">It has the type properties and methods.</span></span> <span data-ttu-id="e151b-149">**System.object** 와 같은 단순 형식의 경우 복사본은 정확 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-149">For simple types, such as **System.Version**, the copy is exact.</span></span> <span data-ttu-id="e151b-150">복합 형식의 경우 복사본은 아직까지 완벽입니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-150">For complex types, the copy is imperfect.</span></span> <span data-ttu-id="e151b-151">예를 들어, 공개 된 인증서 개체에는 개인 키가 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-151">For example, rehydrated certificate objects do not include the private key.</span></span>

<span data-ttu-id="e151b-152">다른 모든 형식의 인스턴스는 **PSObject** 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-152">Instances of all other types are **PSObject** instances.</span></span> <span data-ttu-id="e151b-153">**PSTypeNames** 속성에는 **deserialize**(예:Deserialized.System) 접두사가 붙은 원래 형식 이름이 포함 **됩니다. 데이터 DataTable**</span><span class="sxs-lookup"><span data-stu-id="e151b-153">The **PSTypeNames** property contains the original type name prefixed with **Deserialized**, for example, **Deserialized.System.Data.DataTable**</span></span>

## <a name="using-local-variables-with-argumentlist-parameter"></a><span data-ttu-id="e151b-154">**Argumentlist** 매개 변수를 사용 하 여 지역 변수 사용</span><span class="sxs-lookup"><span data-stu-id="e151b-154">Using local variables with **ArgumentList** parameter</span></span>

<span data-ttu-id="e151b-155">원격 명령에 대 한 매개 변수를 정의 하 고 cmdlet의 **Argumentlist** 매개 변수를 사용 하 여 지역 변수를 `Invoke-Command` 매개 변수 값으로 지정 하 여 원격 명령에서 로컬 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-155">You can use local variables in a remote command by defining parameters for the remote command and using the **ArgumentList** parameter of the `Invoke-Command` cmdlet to specify the local variable as the parameter value.</span></span>

- <span data-ttu-id="e151b-156">키워드를 사용 `param` 하 여 원격 명령에 대 한 매개 변수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-156">Use the `param` keyword to define parameters for the remote command.</span></span> <span data-ttu-id="e151b-157">매개 변수 이름은 지역 변수의 이름과 일치 하지 않아도 되는 자리 표시자입니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-157">The parameter names are placeholders that don't need to match the local variable's name.</span></span>

- <span data-ttu-id="e151b-158">명령에서 키워드로 정의 된 매개 변수를 사용 `param` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-158">Use the parameters defined by the `param` keyword in the command.</span></span>

- <span data-ttu-id="e151b-159">Cmdlet의 **Argumentlist** 매개 변수를 사용 `Invoke-Command` 하 여 지역 변수를 매개 변수 값으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-159">Use the **ArgumentList** parameter of the `Invoke-Command` cmdlet to specify the local variable as the parameter value.</span></span>

<span data-ttu-id="e151b-160">예를 들어 다음 명령은 `$ps` 로컬 세션에서 변수를 정의한 다음 원격 명령에 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-160">For example, the following commands define the `$ps` variable in the local session and then use it in a remote command.</span></span> <span data-ttu-id="e151b-161">`$log`이 명령은 매개 변수 이름과 지역 변수를 `$ps` 해당 값으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e151b-161">The command uses `$log` as the parameter name and the local variable, `$ps`, as its value.</span></span>

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  param($log)
  Get-WinEvent -LogName $log
} -ArgumentList $ps
```

## <a name="see-also"></a><span data-ttu-id="e151b-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e151b-162">See also</span></span>

[<span data-ttu-id="e151b-163">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="e151b-163">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="e151b-164">about_Remote</span><span class="sxs-lookup"><span data-stu-id="e151b-164">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="e151b-165">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="e151b-165">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="e151b-166">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="e151b-166">about_Splatting</span></span>](about_Splatting.md)

[<span data-ttu-id="e151b-167">about_Variables</span><span class="sxs-lookup"><span data-stu-id="e151b-167">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="e151b-168">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="e151b-168">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="e151b-169">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="e151b-169">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="e151b-170">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="e151b-170">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="e151b-171">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="e151b-171">Start-ThreadJob</span></span>](xref:ThreadJob.Start-ThreadJob)

@Microsoft.PowerShell.Core.ForEach-Object

