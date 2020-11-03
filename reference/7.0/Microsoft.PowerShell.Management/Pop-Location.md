---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/pop-location?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Pop-Location
ms.openlocfilehash: 4f5dffdc942112672c3a193fd1fef49b3b5c15d6
ms.sourcegitcommit: 01a1c253f48b61c943f6d6aca4e603118014015f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/06/2020
ms.locfileid: "93219170"
---
# <span data-ttu-id="f7f4d-103">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="f7f4d-103">Pop-Location</span></span>

## <span data-ttu-id="f7f4d-104">개요</span><span class="sxs-lookup"><span data-stu-id="f7f4d-104">SYNOPSIS</span></span>
<span data-ttu-id="f7f4d-105">현재 위치를 가장 최근에 스택에 밀어 넣은 위치로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-105">Changes the current location to the location most recently pushed onto the stack.</span></span>

## <span data-ttu-id="f7f4d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f7f4d-106">SYNTAX</span></span>

```
Pop-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## <span data-ttu-id="f7f4d-107">설명</span><span class="sxs-lookup"><span data-stu-id="f7f4d-107">DESCRIPTION</span></span>

<span data-ttu-id="f7f4d-108">`Pop-Location`Cmdlet은 cmdlet을 사용 하 여 현재 위치를 가장 최근에 스택에 푸시한 위치로 변경 합니다 `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="f7f4d-108">The `Pop-Location` cmdlet changes the current location to the location most recently pushed onto the stack by using the `Push-Location` cmdlet.</span></span> <span data-ttu-id="f7f4d-109">기본 스택 또는 명령을 사용 하 여 만든 스택에서 위치를 표시할 수 있습니다 `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="f7f4d-109">You can pop a location from the default stack or from a stack that you create by using a `Push-Location` command.</span></span>

## <span data-ttu-id="f7f4d-110">예제</span><span class="sxs-lookup"><span data-stu-id="f7f4d-110">EXAMPLES</span></span>

### <span data-ttu-id="f7f4d-111">예제 1: 최신 위치로 변경</span><span class="sxs-lookup"><span data-stu-id="f7f4d-111">Example 1: Change to most recent location</span></span>

```
PS C:\> Pop-Location
```

<span data-ttu-id="f7f4d-112">이 명령은 사용자 위치를 가장 최근에 현재 스택에 추가된 위치로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-112">This command changes your location to the location most recently added to the current stack.</span></span>

### <span data-ttu-id="f7f4d-113">예제 2: 명명 된 스택의 가장 최근 위치로 변경</span><span class="sxs-lookup"><span data-stu-id="f7f4d-113">Example 2: Change to most recent location in a named stack</span></span>

```
PS C:\> Pop-Location -StackName "Stack2"
```

<span data-ttu-id="f7f4d-114">이 명령은 사용자 위치를 가장 최근에 Stack2 위치 스택에 추가된 위치로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-114">This command changes your location to the location most recently added to the Stack2 location stack.</span></span>

<span data-ttu-id="f7f4d-115">위치 스택에 대 한 자세한 내용은 참고를 참조 [하세요.](#notes)</span><span class="sxs-lookup"><span data-stu-id="f7f4d-115">For more information about location stacks, see the [Notes](#notes).</span></span>

### <span data-ttu-id="f7f4d-116">예 3: 다른 공급자의 위치 간 이동</span><span class="sxs-lookup"><span data-stu-id="f7f4d-116">Example 3: Move between locations for different providers</span></span>

```
PS C:\> pushd HKLM:\Software\Microsoft\PowerShell
PS HKLM:\Software\Microsoft\PowerShell> pushd Cert:\LocalMachine\TrustedPublisher
PS cert:\LocalMachine\TrustedPublisher> popd
PS HKLM:\Software\Microsoft\PowerShell> popd
PS C:\>
```

<span data-ttu-id="f7f4d-117">이러한 명령은 `Push-Location` 및 cmdlet을 사용 `Pop-Location` 하 여 서로 다른 PowerShell 공급자가 지 원하는 위치 간에 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-117">These commands use the `Push-Location` and `Pop-Location` cmdlets to move between locations supported by different PowerShell providers.</span></span> <span data-ttu-id="f7f4d-118">이 명령은에 별칭을 사용 하 `pushd` `Push-Location` 고 `popd` 에 별칭을 사용 합니다 `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="f7f4d-118">The commands use the `pushd` alias for `Push-Location` and the `popd` alias for `Pop-Location`.</span></span>

<span data-ttu-id="f7f4d-119">첫 번째 명령은 현재 파일 시스템 위치를 스택에 푸시하고 PowerShell 레지스트리 공급자가 지 원하는 HKLM 드라이브로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-119">The first command pushes the current file system location onto the stack and moves to the HKLM drive supported by the PowerShell Registry provider.</span></span>

<span data-ttu-id="f7f4d-120">두 번째 명령은 레지스트리 위치를 스택에 푸시하고 PowerShell 인증서 공급자가 지 원하는 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-120">The second command pushes the registry location onto the stack and moves to a location supported by the PowerShell certificate provider.</span></span>

<span data-ttu-id="f7f4d-121">마지막 두 명령은 스택에서 해당 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-121">The last two commands pop those locations off the stack.</span></span> <span data-ttu-id="f7f4d-122">첫 번째 `popd` 명령은 레지스트리 드라이브로를 반환 하 고, 두 번째 명령은 파일 시스템 드라이브로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-122">The first `popd` command returns to the Registry drive, and the second command returns to the file system drive.</span></span>

## <span data-ttu-id="f7f4d-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f7f4d-123">PARAMETERS</span></span>

### <span data-ttu-id="f7f4d-124">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f7f4d-124">-PassThru</span></span>

<span data-ttu-id="f7f4d-125">위치를 나타내는 개체를 파이프라인으로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-125">Passes an object that represents the location to the pipeline.</span></span> <span data-ttu-id="f7f4d-126">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-126">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="f7f4d-127">-StackName</span><span class="sxs-lookup"><span data-stu-id="f7f4d-127">-StackName</span></span>

<span data-ttu-id="f7f4d-128">위치가 표시되는 위치 스택을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-128">Specifies the location stack from which the location is popped.</span></span> <span data-ttu-id="f7f4d-129">위치 스택 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-129">Enter a location stack name.</span></span>

<span data-ttu-id="f7f4d-130">이 매개 변수를 사용 하지 않으면는 `Pop-Location` 현재 위치 스택의 위치를 팝 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-130">Without this parameter, `Pop-Location` pops a location from the current location stack.</span></span> <span data-ttu-id="f7f4d-131">기본적으로 현재 위치 스택은 PowerShell에서 만드는 이름 없는 기본 위치 스택입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-131">By default, the current location stack is the unnamed default location stack that PowerShell creates.</span></span> <span data-ttu-id="f7f4d-132">위치 스택을 현재 위치 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 사용 합니다 `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="f7f4d-132">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span> <span data-ttu-id="f7f4d-133">위치 스택에 대 한 자세한 내용은 참고를 참조 [하세요.](#notes)</span><span class="sxs-lookup"><span data-stu-id="f7f4d-133">For more information about location stacks, see the [Notes](#notes).</span></span>

<span data-ttu-id="f7f4d-134">`Pop-Location` 현재 위치 스택이 아닌 경우 이름 없는 기본 스택의 위치를 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-134">`Pop-Location` cannot pop a location from the unnamed default stack unless it is the current location stack.</span></span>

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

### <span data-ttu-id="f7f4d-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f7f4d-135">CommonParameters</span></span>

<span data-ttu-id="f7f4d-136">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f7f4d-137">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f7f4d-138">입력</span><span class="sxs-lookup"><span data-stu-id="f7f4d-138">INPUTS</span></span>

### <span data-ttu-id="f7f4d-139">없음</span><span class="sxs-lookup"><span data-stu-id="f7f4d-139">None</span></span>

<span data-ttu-id="f7f4d-140">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-140">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="f7f4d-141">출력</span><span class="sxs-lookup"><span data-stu-id="f7f4d-141">OUTPUTS</span></span>

### <span data-ttu-id="f7f4d-142">None, System.web. PathInfo</span><span class="sxs-lookup"><span data-stu-id="f7f4d-142">None, System.Management.Automation.PathInfo</span></span>

<span data-ttu-id="f7f4d-143">이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 위치를 나타내는 **System.web. pathinfo** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-143">This cmdlet generates a **System.Management.Automation.PathInfo** object that represents the location, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="f7f4d-144">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-144">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f7f4d-145">참고</span><span class="sxs-lookup"><span data-stu-id="f7f4d-145">NOTES</span></span>

<span data-ttu-id="f7f4d-146">PowerShell은 프로세스 당 여러 runspace를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-146">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="f7f4d-147">각 runspace에는 자체의 _현재 디렉터리가_ 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-147">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="f7f4d-148">와는 다릅니다 `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="f7f4d-148">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="f7f4d-149">이 동작은 명시적 디렉터리 경로를 제공 하지 않고 .NET Api를 호출 하거나 네이티브 응용 프로그램을 실행할 때 문제가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-149">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="f7f4d-150">Location cmdlet이 프로세스 차원의 현재 디렉터리를 설정 했더라도 다른 runspace가 언제 든 지 변경 될 수 있으므로이를 종속 시킬 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-150">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="f7f4d-151">현재 runspace와 관련 된 현재 작업 디렉터리를 사용 하 여 경로 기반 작업을 수행 하려면 location cmdlet을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-151">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="f7f4d-152">스택은 가장 최근에 추가한 항목만 액세스할 수 있는 마지막으로 시작 된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-152">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="f7f4d-153">사용하는 순서대로 스택에 항목을 추가한 다음 사용을 위해 역순으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-153">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="f7f4d-154">PowerShell을 사용 하 여 공급자 위치를 위치 스택에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-154">PowerShell lets you store provider locations in location stacks.</span></span>

<span data-ttu-id="f7f4d-155">PowerShell은 이름 없는 기본 위치 스택을 만들고 여러 개의 명명 된 위치 스택을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-155">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="f7f4d-156">스택 이름을 지정 하지 않으면 PowerShell은 현재 위치 스택을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-156">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="f7f4d-157">기본적으로 이름 없는 기본 위치는 현재 위치 스택입니다. 하지만 cmdlet을 사용 `Set-Location` 하 여 현재 위치 스택을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-157">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="f7f4d-158">위치 스택을 관리 하려면 다음과 `*-Location` 같이 PowerShell cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-158">To manage location stacks, use the PowerShell `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="f7f4d-159">위치 스택에 위치를 추가 하려면 cmdlet을 사용 `Push-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-159">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="f7f4d-160">위치 스택에서 위치를 가져오려면 cmdlet을 사용 `Pop-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-160">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="f7f4d-161">현재 위치 스택의 위치를 표시 하려면 cmdlet의 **stack** 매개 변수를 사용 합니다 `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="f7f4d-161">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="f7f4d-162">명명 된 위치 스택의 위치를 표시 하려면 cmdlet의 **Stackname** 매개 변수를 사용 합니다 `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="f7f4d-162">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="f7f4d-163">새 위치 스택을 만들려면 cmdlet의 **Stackname** 매개 변수를 사용 `Push-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-163">To create a new location stack, use the **StackName** parameter of the `Push-Location` cmdlet.</span></span> <span data-ttu-id="f7f4d-164">존재 하지 않는 스택을 지정 하면에서 `Push-Location` 스택을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-164">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="f7f4d-165">위치 스택을 현재 위치 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 사용 합니다 `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="f7f4d-165">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="f7f4d-166">이름 없는 기본 위치 스택은 현재 위치 스택인 경우에만 완전히 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-166">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="f7f4d-167">명명 된 위치 스택을 현재 위치 스택으로 만들면 `Push-Location` 또는 cmdlet을 사용 `Pop-Location` 하 여 기본 스택에서 항목을 추가 하거나 가져올 수 없으며 cmdlet을 사용 하 여 `Get-Location` 명명 되지 않은 스택의 위치를 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-167">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="f7f4d-168">명명 되지 않은 스택을 현재 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 `Set-Location` 값 `$Null` 이나 빈 문자열 ()로 사용 `""` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-168">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$Null` or an empty string (`""`).</span></span>

<span data-ttu-id="f7f4d-169">의 기본 제공 별칭인를 참조할 수도 있습니다 `Pop-Location` `popd` .</span><span class="sxs-lookup"><span data-stu-id="f7f4d-169">You can also refer to `Pop-Location` by its built-in alias, `popd`.</span></span> <span data-ttu-id="f7f4d-170">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-170">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="f7f4d-171">`Pop-Location` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-171">`Pop-Location` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="f7f4d-172">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-172">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="f7f4d-173">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7f4d-173">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="f7f4d-174">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f7f4d-174">RELATED LINKS</span></span>

[<span data-ttu-id="f7f4d-175">Get-Location</span><span class="sxs-lookup"><span data-stu-id="f7f4d-175">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="f7f4d-176">Push-Location</span><span class="sxs-lookup"><span data-stu-id="f7f4d-176">Push-Location</span></span>](Push-Location.md)

[<span data-ttu-id="f7f4d-177">Set-Location</span><span class="sxs-lookup"><span data-stu-id="f7f4d-177">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="f7f4d-178">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="f7f4d-178">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="f7f4d-179">about_Providers</span><span class="sxs-lookup"><span data-stu-id="f7f4d-179">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
