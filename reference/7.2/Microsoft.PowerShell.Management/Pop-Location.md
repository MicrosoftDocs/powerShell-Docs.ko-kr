---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/pop-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Pop-Location
ms.openlocfilehash: 8a44849f27de80ece486b573f1adccafab51972a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605238"
---
# <span data-ttu-id="4e578-102">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="4e578-102">Pop-Location</span></span>

## <span data-ttu-id="4e578-103">개요</span><span class="sxs-lookup"><span data-stu-id="4e578-103">SYNOPSIS</span></span>
<span data-ttu-id="4e578-104">현재 위치를 가장 최근에 스택에 밀어 넣은 위치로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-104">Changes the current location to the location most recently pushed onto the stack.</span></span>

## <span data-ttu-id="4e578-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4e578-105">SYNTAX</span></span>

```
Pop-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## <span data-ttu-id="4e578-106">설명</span><span class="sxs-lookup"><span data-stu-id="4e578-106">DESCRIPTION</span></span>

<span data-ttu-id="4e578-107">`Pop-Location`Cmdlet은 cmdlet을 사용 하 여 현재 위치를 가장 최근에 스택에 푸시한 위치로 변경 합니다 `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="4e578-107">The `Pop-Location` cmdlet changes the current location to the location most recently pushed onto the stack by using the `Push-Location` cmdlet.</span></span> <span data-ttu-id="4e578-108">기본 스택 또는 명령을 사용 하 여 만든 스택에서 위치를 표시할 수 있습니다 `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="4e578-108">You can pop a location from the default stack or from a stack that you create by using a `Push-Location` command.</span></span>

## <span data-ttu-id="4e578-109">예제</span><span class="sxs-lookup"><span data-stu-id="4e578-109">EXAMPLES</span></span>

### <span data-ttu-id="4e578-110">예제 1: 최신 위치로 변경</span><span class="sxs-lookup"><span data-stu-id="4e578-110">Example 1: Change to most recent location</span></span>

```
PS C:\> Pop-Location
```

<span data-ttu-id="4e578-111">이 명령은 사용자 위치를 가장 최근에 현재 스택에 추가된 위치로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-111">This command changes your location to the location most recently added to the current stack.</span></span>

### <span data-ttu-id="4e578-112">예제 2: 명명 된 스택의 가장 최근 위치로 변경</span><span class="sxs-lookup"><span data-stu-id="4e578-112">Example 2: Change to most recent location in a named stack</span></span>

```
PS C:\> Pop-Location -StackName "Stack2"
```

<span data-ttu-id="4e578-113">이 명령은 사용자 위치를 가장 최근에 Stack2 위치 스택에 추가된 위치로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-113">This command changes your location to the location most recently added to the Stack2 location stack.</span></span>

<span data-ttu-id="4e578-114">위치 스택에 대 한 자세한 내용은 참고를 참조 [하세요.](#notes)</span><span class="sxs-lookup"><span data-stu-id="4e578-114">For more information about location stacks, see the [Notes](#notes).</span></span>

### <span data-ttu-id="4e578-115">예 3: 다른 공급자의 위치 간 이동</span><span class="sxs-lookup"><span data-stu-id="4e578-115">Example 3: Move between locations for different providers</span></span>

```
PS C:\> pushd HKLM:\Software\Microsoft\PowerShell
PS HKLM:\Software\Microsoft\PowerShell> pushd Cert:\LocalMachine\TrustedPublisher
PS cert:\LocalMachine\TrustedPublisher> popd
PS HKLM:\Software\Microsoft\PowerShell> popd
PS C:\>
```

<span data-ttu-id="4e578-116">이러한 명령은 `Push-Location` 및 cmdlet을 사용 `Pop-Location` 하 여 서로 다른 PowerShell 공급자가 지 원하는 위치 간에 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-116">These commands use the `Push-Location` and `Pop-Location` cmdlets to move between locations supported by different PowerShell providers.</span></span> <span data-ttu-id="4e578-117">이 명령은에 별칭을 사용 하 `pushd` `Push-Location` 고 `popd` 에 별칭을 사용 합니다 `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="4e578-117">The commands use the `pushd` alias for `Push-Location` and the `popd` alias for `Pop-Location`.</span></span>

<span data-ttu-id="4e578-118">첫 번째 명령은 현재 파일 시스템 위치를 스택에 푸시하고 PowerShell 레지스트리 공급자가 지 원하는 HKLM 드라이브로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-118">The first command pushes the current file system location onto the stack and moves to the HKLM drive supported by the PowerShell Registry provider.</span></span>

<span data-ttu-id="4e578-119">두 번째 명령은 레지스트리 위치를 스택에 푸시하고 PowerShell 인증서 공급자가 지 원하는 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-119">The second command pushes the registry location onto the stack and moves to a location supported by the PowerShell certificate provider.</span></span>

<span data-ttu-id="4e578-120">마지막 두 명령은 스택에서 해당 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-120">The last two commands pop those locations off the stack.</span></span> <span data-ttu-id="4e578-121">첫 번째 `popd` 명령은 레지스트리 드라이브로를 반환 하 고, 두 번째 명령은 파일 시스템 드라이브로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-121">The first `popd` command returns to the Registry drive, and the second command returns to the file system drive.</span></span>

## <span data-ttu-id="4e578-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4e578-122">PARAMETERS</span></span>

### <span data-ttu-id="4e578-123">-PassThru</span><span class="sxs-lookup"><span data-stu-id="4e578-123">-PassThru</span></span>

<span data-ttu-id="4e578-124">위치를 나타내는 개체를 파이프라인으로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-124">Passes an object that represents the location to the pipeline.</span></span> <span data-ttu-id="4e578-125">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-125">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="4e578-126">-StackName</span><span class="sxs-lookup"><span data-stu-id="4e578-126">-StackName</span></span>

<span data-ttu-id="4e578-127">위치가 표시되는 위치 스택을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-127">Specifies the location stack from which the location is popped.</span></span> <span data-ttu-id="4e578-128">위치 스택 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-128">Enter a location stack name.</span></span>

<span data-ttu-id="4e578-129">이 매개 변수를 사용 하지 않으면는 `Pop-Location` 현재 위치 스택의 위치를 팝 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-129">Without this parameter, `Pop-Location` pops a location from the current location stack.</span></span> <span data-ttu-id="4e578-130">기본적으로 현재 위치 스택은 PowerShell에서 만드는 이름 없는 기본 위치 스택입니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-130">By default, the current location stack is the unnamed default location stack that PowerShell creates.</span></span> <span data-ttu-id="4e578-131">위치 스택을 현재 위치 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 사용 합니다 `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="4e578-131">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span> <span data-ttu-id="4e578-132">위치 스택에 대 한 자세한 내용은 참고를 참조 [하세요.](#notes)</span><span class="sxs-lookup"><span data-stu-id="4e578-132">For more information about location stacks, see the [Notes](#notes).</span></span>

<span data-ttu-id="4e578-133">`Pop-Location` 현재 위치 스택이 아닌 경우 이름 없는 기본 스택의 위치를 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-133">`Pop-Location` cannot pop a location from the unnamed default stack unless it is the current location stack.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4e578-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4e578-134">CommonParameters</span></span>

<span data-ttu-id="4e578-135">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4e578-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4e578-136">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e578-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4e578-137">입력</span><span class="sxs-lookup"><span data-stu-id="4e578-137">INPUTS</span></span>

### <span data-ttu-id="4e578-138">없음</span><span class="sxs-lookup"><span data-stu-id="4e578-138">None</span></span>

<span data-ttu-id="4e578-139">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-139">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="4e578-140">출력</span><span class="sxs-lookup"><span data-stu-id="4e578-140">OUTPUTS</span></span>

### <span data-ttu-id="4e578-141">None, System.web. PathInfo</span><span class="sxs-lookup"><span data-stu-id="4e578-141">None, System.Management.Automation.PathInfo</span></span>

<span data-ttu-id="4e578-142">이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 위치를 나타내는 **System.web. pathinfo** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-142">This cmdlet generates a **System.Management.Automation.PathInfo** object that represents the location, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="4e578-143">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-143">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="4e578-144">참고</span><span class="sxs-lookup"><span data-stu-id="4e578-144">NOTES</span></span>

<span data-ttu-id="4e578-145">PowerShell은 프로세스 당 여러 runspace를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-145">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="4e578-146">각 runspace에는 자체의 _현재 디렉터리가_ 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-146">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="4e578-147">와는 다릅니다 `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="4e578-147">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="4e578-148">이 동작은 명시적 디렉터리 경로를 제공 하지 않고 .NET Api를 호출 하거나 네이티브 응용 프로그램을 실행할 때 문제가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-148">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="4e578-149">Location cmdlet이 프로세스 차원의 현재 디렉터리를 설정 했더라도 다른 runspace가 언제 든 지 변경 될 수 있으므로이를 종속 시킬 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-149">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="4e578-150">현재 runspace와 관련 된 현재 작업 디렉터리를 사용 하 여 경로 기반 작업을 수행 하려면 location cmdlet을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-150">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="4e578-151">스택은 가장 최근에 추가한 항목만 액세스할 수 있는 마지막으로 시작 된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-151">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="4e578-152">사용하는 순서대로 스택에 항목을 추가한 다음 사용을 위해 역순으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-152">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="4e578-153">PowerShell을 사용 하 여 공급자 위치를 위치 스택에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-153">PowerShell lets you store provider locations in location stacks.</span></span>

<span data-ttu-id="4e578-154">PowerShell은 이름 없는 기본 위치 스택을 만들고 여러 개의 명명 된 위치 스택을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-154">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="4e578-155">스택 이름을 지정 하지 않으면 PowerShell은 현재 위치 스택을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-155">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="4e578-156">기본적으로 이름 없는 기본 위치는 현재 위치 스택입니다. 하지만 cmdlet을 사용 `Set-Location` 하 여 현재 위치 스택을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-156">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="4e578-157">위치 스택을 관리 하려면 다음과 `*-Location` 같이 PowerShell cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-157">To manage location stacks, use the PowerShell `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="4e578-158">위치 스택에 위치를 추가 하려면 cmdlet을 사용 `Push-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-158">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="4e578-159">위치 스택에서 위치를 가져오려면 cmdlet을 사용 `Pop-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-159">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="4e578-160">현재 위치 스택의 위치를 표시 하려면 cmdlet의 **stack** 매개 변수를 사용 합니다 `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="4e578-160">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="4e578-161">명명 된 위치 스택의 위치를 표시 하려면 cmdlet의 **Stackname** 매개 변수를 사용 합니다 `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="4e578-161">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="4e578-162">새 위치 스택을 만들려면 cmdlet의 **Stackname** 매개 변수를 사용 `Push-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-162">To create a new location stack, use the **StackName** parameter of the `Push-Location` cmdlet.</span></span> <span data-ttu-id="4e578-163">존재 하지 않는 스택을 지정 하면에서 `Push-Location` 스택을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-163">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="4e578-164">위치 스택을 현재 위치 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 사용 합니다 `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="4e578-164">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="4e578-165">이름 없는 기본 위치 스택은 현재 위치 스택인 경우에만 완전히 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-165">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="4e578-166">명명 된 위치 스택을 현재 위치 스택으로 만들면 `Push-Location` 또는 cmdlet을 사용 `Pop-Location` 하 여 기본 스택에서 항목을 추가 하거나 가져올 수 없으며 cmdlet을 사용 하 여 `Get-Location` 명명 되지 않은 스택의 위치를 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-166">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="4e578-167">명명 되지 않은 스택을 현재 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 `Set-Location` 값 `$Null` 이나 빈 문자열 ()로 사용 `""` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-167">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$Null` or an empty string (`""`).</span></span>

<span data-ttu-id="4e578-168">의 기본 제공 별칭인를 참조할 수도 있습니다 `Pop-Location` `popd` .</span><span class="sxs-lookup"><span data-stu-id="4e578-168">You can also refer to `Pop-Location` by its built-in alias, `popd`.</span></span> <span data-ttu-id="4e578-169">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4e578-169">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="4e578-170">`Pop-Location` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-170">`Pop-Location` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="4e578-171">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e578-171">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="4e578-172">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e578-172">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="4e578-173">관련 링크</span><span class="sxs-lookup"><span data-stu-id="4e578-173">RELATED LINKS</span></span>

[<span data-ttu-id="4e578-174">Get-Location</span><span class="sxs-lookup"><span data-stu-id="4e578-174">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="4e578-175">Push-Location</span><span class="sxs-lookup"><span data-stu-id="4e578-175">Push-Location</span></span>](Push-Location.md)

[<span data-ttu-id="4e578-176">Set-Location</span><span class="sxs-lookup"><span data-stu-id="4e578-176">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="4e578-177">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="4e578-177">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="4e578-178">about_Providers</span><span class="sxs-lookup"><span data-stu-id="4e578-178">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
