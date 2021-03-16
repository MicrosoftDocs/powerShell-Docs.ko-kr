---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Location
ms.openlocfilehash: 57535b4f566a3bdd541d2035b61c8162e15b35f3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601240"
---
# <span data-ttu-id="09c24-102">Get-Location</span><span class="sxs-lookup"><span data-stu-id="09c24-102">Get-Location</span></span>

## <span data-ttu-id="09c24-103">개요</span><span class="sxs-lookup"><span data-stu-id="09c24-103">SYNOPSIS</span></span>
<span data-ttu-id="09c24-104">현재 작업 위치 또는 위치 스택에 대한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-104">Gets information about the current working location or a location stack.</span></span>

## <span data-ttu-id="09c24-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="09c24-105">SYNTAX</span></span>

### <span data-ttu-id="09c24-106">Location (기본값)</span><span class="sxs-lookup"><span data-stu-id="09c24-106">Location (Default)</span></span>

```
Get-Location [-PSProvider <String[]>] [-PSDrive <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="09c24-107">스택</span><span class="sxs-lookup"><span data-stu-id="09c24-107">Stack</span></span>

```
Get-Location [-Stack] [-StackName <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="09c24-108">설명</span><span class="sxs-lookup"><span data-stu-id="09c24-108">DESCRIPTION</span></span>

<span data-ttu-id="09c24-109">`Get-Location`Cmdlet은 pwd (인쇄 작업 디렉터리) 명령과 매우 유사 하 게 현재 디렉터리를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-109">The `Get-Location` cmdlet gets an object that represents the current directory, much like the print working directory (pwd) command.</span></span>

<span data-ttu-id="09c24-110">PowerShell 드라이브 간을 이동 하면 PowerShell에서 각 드라이브의 위치를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-110">When you move between PowerShell drives, PowerShell retains your location in each drive.</span></span> <span data-ttu-id="09c24-111">이 cmdlet을 사용 하 여 각 드라이브에서 위치를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-111">You can use this cmdlet to find your location in each drive.</span></span>

<span data-ttu-id="09c24-112">이 cmdlet을 사용 하 여 런타임에 현재 디렉터리를 가져오고 PowerShell 프롬프트에서 현재 디렉터리를 표시 하는 함수 등의 함수 및 스크립트에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-112">You can use this cmdlet to get the current directory at run time and use it in functions and scripts, such as in a function that displays the current directory in the PowerShell prompt.</span></span>

<span data-ttu-id="09c24-113">이 cmdlet을 사용 하 여 위치 스택의 위치를 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-113">You can also use this cmdlet to display the locations in a location stack.</span></span> <span data-ttu-id="09c24-114">자세한 내용은 **Stack** 및 **stackname** 매개 변수에 대 한 참고 및 설명을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="09c24-114">For more information, see the Notes and the descriptions of the **Stack** and **StackName** parameters.</span></span>

## <span data-ttu-id="09c24-115">예제</span><span class="sxs-lookup"><span data-stu-id="09c24-115">EXAMPLES</span></span>

### <span data-ttu-id="09c24-116">예제 1: 현재 드라이브 위치 표시</span><span class="sxs-lookup"><span data-stu-id="09c24-116">Example 1: Display your current drive location</span></span>

<span data-ttu-id="09c24-117">이 명령은 현재 PowerShell 드라이브의 위치를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-117">This command displays your location in the current PowerShell drive.</span></span>

```powershell
PS C:\Windows> Get-Location
```

```Output
Path
----
C:\Windows
```

<span data-ttu-id="09c24-118">예를 들어, `Windows` 드라이브의 디렉터리에 있는 경우 `C:` 해당 디렉터리에 대 한 경로를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-118">For instance, if you are in the `Windows` directory of the `C:` drive, it displays the path to that directory.</span></span>

### <span data-ttu-id="09c24-119">예 2: 다른 드라이브에 대 한 현재 위치 표시</span><span class="sxs-lookup"><span data-stu-id="09c24-119">Example 2: Display your current location for different drives</span></span>

<span data-ttu-id="09c24-120">이 예제에서는를 사용 `Get-Location` 하 여 다른 PowerShell 드라이브에 현재 위치를 표시 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-120">This example demonstrates the use of `Get-Location` to display your current location in different PowerShell drives.</span></span> <span data-ttu-id="09c24-121">`Set-Location` 는 다른 PSDrives에서 여러 다른 경로로 위치를 변경 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-121">`Set-Location` is used to change the location to several different paths on different PSDrives.</span></span>

```powershell
PS C:\> Set-Location C:\Windows
PS C:\Windows> Set-Location HKLM:\Software\Microsoft
PS HKLM:\Software\Microsoft> Set-Location "HKCU:\Control Panel\Input Method"
PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive C

Path
----
C:\Windows

PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive HKLM

Path
----
HKLM:\Software\Microsoft

PS HKCU:\Control Panel\Input Method> Set-Location C:
PS C:\Windows> Get-Location -PSProvider Registry

Path
----
HKCU:\Control Panel\Input Method
```

### <span data-ttu-id="09c24-122">예 3: 스택을 사용 하 여 위치 가져오기</span><span class="sxs-lookup"><span data-stu-id="09c24-122">Example 3: Get locations using stacks</span></span>

<span data-ttu-id="09c24-123">이 예제에서는의 **Stack** 및 **stackname** 매개 변수를 사용 하 여 `Get-Location` 현재 위치 스택과 대체 위치 스택의 위치를 나열 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-123">This example shows how to use the **Stack** and **StackName** parameters of `Get-Location` to list the locations in the current location stack and alternate location stacks.</span></span>

<span data-ttu-id="09c24-124">`Push-Location`Cmdlet은 3 개의 다른 위치로 변경 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-124">The `Push-Location` cmdlet is used to change into three different locations.</span></span> <span data-ttu-id="09c24-125">세 번째 푸시는 다른 스택 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-125">The third push uses a different stack name.</span></span> <span data-ttu-id="09c24-126">의 **stack** 매개 변수는 `Get-Location` 기본 스택의 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-126">The **Stack** parameter of `Get-Location` displays the contents of the default stack.</span></span> <span data-ttu-id="09c24-127">의 **Stackname** 매개 변수는 `Get-Location` 라는 스택의 내용을 표시 합니다 `Stack2` .</span><span class="sxs-lookup"><span data-stu-id="09c24-127">The **StackName** parameter of `Get-Location` displays the contents of the stack named `Stack2`.</span></span>

```powershell
PS C:\> Push-Location C:\Windows
PS C:\Windows>Push-Location System32
PS C:\Windows\System32>Push-Location WindowsPowerShell -StackName Stack2
C:\Windows\System32\WindowsPowerShell>Get-Location -Stack

Path
----
C:\Windows
C:\

C:\Windows\System32\WindowsPowerShell>Get-Location -StackName Stack2

Path
----
C:\Windows\System32
```

### <span data-ttu-id="09c24-128">예제 4: PowerShell 프롬프트 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="09c24-128">Example 4: Customize the PowerShell prompt</span></span>

<span data-ttu-id="09c24-129">이 예제에서는 PowerShell 프롬프트를 사용자 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-129">This example shows how to customize the PowerShell prompt.</span></span>

```powershell
PS C:\>
function prompt { 'PowerShell: ' + (Get-Location) + '> '}
PowerShell: C:\>
```

<span data-ttu-id="09c24-130">프롬프트를 정의 하는 함수에는 `Get-Location` 프롬프트를 콘솔에 표시할 때마다 실행 되는 명령이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-130">The function that defines the prompt includes a `Get-Location` command, which is run whenever the prompt appears in the console.</span></span>

<span data-ttu-id="09c24-131">기본 PowerShell 프롬프트의 형식은 라는 특수 함수에 의해 정의 됩니다 `prompt` .</span><span class="sxs-lookup"><span data-stu-id="09c24-131">The format of the default PowerShell prompt is defined by a special function named `prompt`.</span></span> <span data-ttu-id="09c24-132">이라는 새 함수를 만들어 콘솔의 프롬프트를 변경할 수 있습니다 `prompt` .</span><span class="sxs-lookup"><span data-stu-id="09c24-132">You can change the prompt in your console by creating a new function named `prompt`.</span></span>

<span data-ttu-id="09c24-133">현재 프롬프트 함수를 보려면 다음 명령을 입력 합니다. `Get-Content Function:\prompt`</span><span class="sxs-lookup"><span data-stu-id="09c24-133">To see the current prompt function, type the following command: `Get-Content Function:\prompt`</span></span>

## <span data-ttu-id="09c24-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="09c24-134">PARAMETERS</span></span>

### <span data-ttu-id="09c24-135">-PSDrive</span><span class="sxs-lookup"><span data-stu-id="09c24-135">-PSDrive</span></span>

<span data-ttu-id="09c24-136">지정 된 PowerShell 드라이브의 현재 위치를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-136">Gets the current location in the specified PowerShell drive.</span></span>

<span data-ttu-id="09c24-137">예를 들어, 드라이브에 있는 경우 `Cert:` 이 매개 변수를 사용 하 여 드라이브에서 현재 위치를 찾을 수 있습니다 `C:` .</span><span class="sxs-lookup"><span data-stu-id="09c24-137">For instance, if you are in the `Cert:` drive, you can use this parameter to find your current location in the `C:` drive.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="09c24-138">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="09c24-138">-PSProvider</span></span>

<span data-ttu-id="09c24-139">지정 된 PowerShell 공급자가 지 원하는 드라이브에서 현재 위치를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-139">Gets the current location in the drive supported by the specified PowerShell provider.</span></span>
<span data-ttu-id="09c24-140">지정 된 공급자가 둘 이상의 드라이브를 지 원하는 경우이 cmdlet은 가장 최근에 액세스 한 드라이브의 위치를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-140">If the specified provider supports more than one drive, this cmdlet returns the location on the most recently accessed drive.</span></span>

<span data-ttu-id="09c24-141">예를 들어, 드라이브에 있는 경우 `C:` 이 매개 변수를 사용 하 여 PowerShell **레지스트리** 공급자의 드라이브에서 현재 위치를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-141">For example, if you are in the `C:` drive, you can use this parameter to find your current location in the drives of the PowerShell **Registry** provider.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="09c24-142">-스택</span><span class="sxs-lookup"><span data-stu-id="09c24-142">-Stack</span></span>

<span data-ttu-id="09c24-143">이 cmdlet이 현재 위치 스택에 추가 된 위치를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-143">Indicates that this cmdlet displays the locations added to the current location stack.</span></span> <span data-ttu-id="09c24-144">Cmdlet을 사용 하 여 스택에 위치를 추가할 수 있습니다 `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="09c24-144">You can add locations to stacks by using the `Push-Location` cmdlet.</span></span>

<span data-ttu-id="09c24-145">다른 위치 스택에 위치를 표시 하려면 **Stackname** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-145">To display the locations in a different location stack, use the **StackName** parameter.</span></span> <span data-ttu-id="09c24-146">위치 스택에 대 한 자세한 [내용은 참고를 참조 하세요.](#notes)</span><span class="sxs-lookup"><span data-stu-id="09c24-146">For information about location stacks, see the [Notes](#notes).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09c24-147">-StackName</span><span class="sxs-lookup"><span data-stu-id="09c24-147">-StackName</span></span>

<span data-ttu-id="09c24-148">을 문자열 배열로 명명 된 위치 스택으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-148">Specifies, as a string array, the named location stacks.</span></span> <span data-ttu-id="09c24-149">위치 스택 이름을 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-149">Enter one or more location stack names.</span></span>

<span data-ttu-id="09c24-150">현재 위치 스택의 위치를 표시 하려면 **stack** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-150">To display the locations in the current location stack, use the **Stack** parameter.</span></span> <span data-ttu-id="09c24-151">위치 스택을 현재 위치 스택으로 만들려면 cmdlet을 사용 `Set-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-151">To make a location stack the current location stack, use the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="09c24-152">이 cmdlet은 현재 스택이 아닌 경우 이름 없는 기본 스택의 위치를 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-152">This cmdlet cannot display the locations in the unnamed default stack unless it is the current stack.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="09c24-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="09c24-153">CommonParameters</span></span>

<span data-ttu-id="09c24-154">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="09c24-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="09c24-155">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="09c24-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="09c24-156">입력</span><span class="sxs-lookup"><span data-stu-id="09c24-156">INPUTS</span></span>

### <span data-ttu-id="09c24-157">없음</span><span class="sxs-lookup"><span data-stu-id="09c24-157">None</span></span>

<span data-ttu-id="09c24-158">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-158">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="09c24-159">출력</span><span class="sxs-lookup"><span data-stu-id="09c24-159">OUTPUTS</span></span>

### <span data-ttu-id="09c24-160">System.object 또는 System.web.. d m p. PathInfoStack</span><span class="sxs-lookup"><span data-stu-id="09c24-160">System.Management.Automation.PathInfo or System.Management.Automation.PathInfoStack</span></span>

<span data-ttu-id="09c24-161">**Stack** 또는 **stackname** 매개 변수를 사용 하는 경우이 Cmdlet은 **pathinfostack** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-161">If you use the **Stack** or **StackName** parameters, this cmdlet returns a **PathInfoStack** object.</span></span> <span data-ttu-id="09c24-162">그렇지 않으면 **Pathinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-162">Otherwise, it returns a **PathInfo** object.</span></span>

## <span data-ttu-id="09c24-163">참고</span><span class="sxs-lookup"><span data-stu-id="09c24-163">NOTES</span></span>

<span data-ttu-id="09c24-164">PowerShell은 프로세스 당 여러 runspace를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-164">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="09c24-165">각 runspace에는 자체의 _현재 디렉터리가_ 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-165">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="09c24-166">와는 다릅니다 `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="09c24-166">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="09c24-167">이 동작은 명시적 디렉터리 경로를 제공 하지 않고 .NET Api를 호출 하거나 네이티브 응용 프로그램을 실행할 때 문제가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-167">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>
<span data-ttu-id="09c24-168">`Get-Location`Cmdlet은 현재 PowerShell runspace의 현재 디렉터리를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-168">The `Get-Location` cmdlet returns the current directory of the current PowerShell runspace.</span></span>

<span data-ttu-id="09c24-169">이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-169">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="09c24-170">세션의 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-170">To list the providers in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="09c24-171">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="09c24-171">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="09c24-172">**Psprovider**, **PSDrive**, **Stack** 및 **stackname** 매개 변수가 상호 작용 하는 방법은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-172">The ways that the **PSProvider**, **PSDrive**, **Stack**, and **StackName** parameters interact depends on the provider.</span></span> <span data-ttu-id="09c24-173">드라이브와 해당 드라이브를 노출하지 않는 공급자를 둘 다 지정하는 경우 등 일부 조합에서는 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-173">Some combinations will result in errors, such as specifying both a drive and a provider that does not expose that drive.</span></span> <span data-ttu-id="09c24-174">매개 변수를 지정 하지 않으면이 cmdlet은 현재 작업 위치를 포함 하는 공급자에 대 한 **Pathinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-174">If no parameters are specified, this cmdlet returns the **PathInfo** object for the provider that contains the current working location.</span></span>

<span data-ttu-id="09c24-175">스택은 가장 최근에 추가 된 항목만 액세스할 수 있는 마지막으로 시작 된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-175">A stack is a last-in, first-out list in which only the most recently added item is accessible.</span></span> <span data-ttu-id="09c24-176">사용하는 순서대로 스택에 항목을 추가한 다음 사용을 위해 역순으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-176">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="09c24-177">PowerShell을 사용 하 여 공급자 위치를 위치 스택에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-177">PowerShell lets you store provider locations in location stacks.</span></span> <span data-ttu-id="09c24-178">PowerShell은 이름 없는 기본 위치 스택을 만들고 여러 개의 명명 된 위치 스택을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-178">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="09c24-179">스택 이름을 지정 하지 않으면 PowerShell은 현재 위치 스택을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-179">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="09c24-180">기본적으로 이름 없는 기본 위치는 현재 위치 스택입니다. 하지만 cmdlet을 사용 `Set-Location` 하 여 현재 위치 스택을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-180">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="09c24-181">위치 스택을 관리 하려면 `*-Location` 다음과 같이 PowerShell cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-181">To manage location stacks, use the PowerShell `*-Location` cmdlets, as follows.</span></span>

- <span data-ttu-id="09c24-182">위치 스택에 위치를 추가 하려면 cmdlet을 사용 `Push-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-182">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="09c24-183">위치 스택에서 위치를 가져오려면 cmdlet을 사용 `Pop-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-183">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="09c24-184">현재 위치 스택의 위치를 표시 하려면 cmdlet의 **stack** 매개 변수를 사용 합니다 `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="09c24-184">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span> <span data-ttu-id="09c24-185">명명 된 위치 스택의 위치를 표시 하려면 cmdlet의 **Stackname** 매개 변수를 사용 합니다 `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="09c24-185">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="09c24-186">새 위치 스택을 만들려면 cmdlet의 **Stackname** 매개 변수를 사용 `Push-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-186">To create a new location stack, use the **StackName** parameter of the `Push-Location` cmdlet.</span></span>
  <span data-ttu-id="09c24-187">존재 하지 않는 스택을 지정 하면에서 `Push-Location` 스택을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-187">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="09c24-188">위치 스택을 현재 위치 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 사용 합니다 `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="09c24-188">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="09c24-189">이름 없는 기본 위치 스택은 현재 위치 스택인 경우에만 완전히 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-189">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="09c24-190">명명 된 위치 스택을 현재 위치 스택으로 만든 경우 더 이상 `Push-Location` 또는 cmdlet을 사용 `Pop-Location` 하 여 기본 스택에서 항목을 추가 하거나 가져올 수 없으며이 cmdlet을 사용 하 여 명명 되지 않은 스택의 위치를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-190">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use this cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="09c24-191">명명 되지 않은 스택을 현재 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 `Set-Location` 값 `$null` 이나 빈 문자열 ()로 사용 `""` 합니다.</span><span class="sxs-lookup"><span data-stu-id="09c24-191">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

## <span data-ttu-id="09c24-192">관련 링크</span><span class="sxs-lookup"><span data-stu-id="09c24-192">RELATED LINKS</span></span>

[<span data-ttu-id="09c24-193">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="09c24-193">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="09c24-194">Push-Location</span><span class="sxs-lookup"><span data-stu-id="09c24-194">Push-Location</span></span>](Push-Location.md)

[<span data-ttu-id="09c24-195">Set-Location</span><span class="sxs-lookup"><span data-stu-id="09c24-195">Set-Location</span></span>](Set-Location.md)
