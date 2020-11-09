---
title: PowerShell 함수에 자격 증명 지원 추가
description: PowerShell 스크립트, 함수, cmdlet에 자격 증명 매개 변수를 추가하는 방법입니다.
ms.date: 10/29/2020
ms.custom: contributor-JoshDuffney
ms.openlocfilehash: 3e4a3f41ccbca1cf97f2e96fd60f22d89be7bc5a
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354629"
---
# <a name="add-credential-support-to-powershell-functions"></a><span data-ttu-id="6f8de-103">PowerShell 함수에 자격 증명 지원 추가</span><span class="sxs-lookup"><span data-stu-id="6f8de-103">Add Credential support to PowerShell functions</span></span>

> [!NOTE]
> <span data-ttu-id="6f8de-104">이 문서의 [원래 버전][]은 [@joshduffney][]가 작성한 블로그에 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-104">The [original version][] of this article appeared on the blog written by [@joshduffney][].</span></span> <span data-ttu-id="6f8de-105">이 문서는 이 사이트에 포함할 수 있도록 편집되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-105">This article has been edited for inclusion on this site.</span></span> <span data-ttu-id="6f8de-106">PowerShell 팀은 이 콘텐츠를 공유해 준 Josh에게 감사의 말을 전합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-106">The PowerShell team thanks Josh for sharing this content with us.</span></span> <span data-ttu-id="6f8de-107">[duffney.io][]에서 Josh의 블로그를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="6f8de-107">Please check out his blog at [duffney.io][].</span></span>

<span data-ttu-id="6f8de-108">이 문서에서는 PowerShell 함수에 자격 증명 매개 변수를 추가하는 방법과 추가해야 하는 이유를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-108">This article shows you how to add credential parameters to PowerShell functions and why you'd want to.</span></span> <span data-ttu-id="6f8de-109">자격 증명 매개 변수는 함수 또는 cmdlet을 다른 사용자로 실행할 수 있도록 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-109">A credential parameter is to allow you to run the function or cmdlet as a different user.</span></span> <span data-ttu-id="6f8de-110">가장 일반적인 용도는 함수 또는 cmdlet을 관리자 계정으로 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-110">The most common use is to run the function or cmdlet as an elevated user account.</span></span>

<span data-ttu-id="6f8de-111">예를 들어 cmdlet `New-ADUser`에는 도메인에 계정을 만들기 위해 도메인 관리자 자격 증명을 제공할 수 있는 **Credential** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-111">For example, the cmdlet `New-ADUser` has a **Credential** parameter, which you could provide domain admin credentials to create an account in a domain.</span></span> <span data-ttu-id="6f8de-112">PowerShell 세션을 실행하는 일반 계정에 아직 이 액세스 권한이 없는 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-112">Assuming your normal account running the PowerShell session doesn't have that access already.</span></span>

## <a name="creating-credential-object"></a><span data-ttu-id="6f8de-113">자격 증명 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="6f8de-113">Creating credential object</span></span>

<span data-ttu-id="6f8de-114">[PSCredential][] 개체는 사용자 이름 및 암호와 같은 보안 자격 증명 집합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-114">The [PSCredential][] object represents a set of security credentials such as a user name and password.</span></span> <span data-ttu-id="6f8de-115">이 개체는 해당 자격 증명 개체의 사용자 계정으로 실행되는 함수에 매개 변수로 전달될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-115">The object can be passed as a parameter to a function that runs as the user account in that credential object.</span></span> <span data-ttu-id="6f8de-116">자격 증명 개체를 만드는 몇 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-116">There are a few ways that you can create a credential object.</span></span> <span data-ttu-id="6f8de-117">자격 증명 개체를 만드는 첫 번째 방법은 PowerShell cmdlet `Get-Credential`을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-117">The first way to create a credential object is to use the PowerShell cmdlet `Get-Credential`.</span></span> <span data-ttu-id="6f8de-118">매개 변수 없이 실행하는 경우 사용자 이름과 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-118">When you run without parameters, it prompts you for a username and password.</span></span> <span data-ttu-id="6f8de-119">또는 몇 가지 선택적 매개 변수를 사용하여 cmdlet을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-119">Or you can call the cmdlet with some optional parameters.</span></span>

<span data-ttu-id="6f8de-120">도메인 이름과 사용자 이름을 미리 지정하려면 **Credential** 또는 **UserNaem** 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-120">To specify the domain name and username ahead of time you can use either the **Credential** or **UserName** parameters.</span></span> <span data-ttu-id="6f8de-121">**UserName** 매개 변수를 사용하는 경우 **Message** 값도 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-121">When you use the **UserName** parameter, you're also required to provide a **Message** value.</span></span> <span data-ttu-id="6f8de-122">아래 코드는 cmdlet 사용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-122">The code below demonstrates using the cmdlet.</span></span> <span data-ttu-id="6f8de-123">자격 증명을 여러 번 사용할 수 있도록 자격 증명 개체를 변수에 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-123">You can also store the credential object in a variable so that you can use the credential multiple times.</span></span> <span data-ttu-id="6f8de-124">아래 예제에서 자격 증명 개체는 `$Cred` 변수에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-124">In the example below, the credential object is stored in the variable `$Cred`.</span></span>

```powershell
$Cred = Get-Credential
$Cred = Get-Credential -Credential domain\user
$Cred = Get-Credential -UserName domain\user -Message 'Enter Password'
```

<span data-ttu-id="6f8de-125">이전 예제에 나온 자격 증명 개체를 만드는 대화형 메서드를 사용할 수 없는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-125">Sometimes, you can't use the interactive method of creating credential objects shown in the previous example.</span></span> <span data-ttu-id="6f8de-126">대부분의 자동화 도구에는 비대화형 메서드가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-126">Most automation tools require a non-interactive method.</span></span> <span data-ttu-id="6f8de-127">사용자 상호 작용 없이 자격 증명을 만들려면 암호를 포함하는 보안 문자열을 만드세요.</span><span class="sxs-lookup"><span data-stu-id="6f8de-127">To create a credential without user interaction, create a secure string containing the password.</span></span> <span data-ttu-id="6f8de-128">그런 다음 보안 문자열과 사용자 이름을 `System.Management.Automation.PSCredential()` 메서드에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-128">Then pass the secure string and user name to the `System.Management.Automation.PSCredential()` method.</span></span>

<span data-ttu-id="6f8de-129">다음 명령을 사용하여 암호를 포함하는 보안 문자열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-129">Use the following command to create a secure string containing the password:</span></span>

```powershell
ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
```

<span data-ttu-id="6f8de-130">**AsPlainText** 및 **Force** 매개 변수가 모두 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-130">Both the **AsPlainText** and **Force** parameters are required.</span></span> <span data-ttu-id="6f8de-131">이러한 매개 변수가 없으면 일반 텍스트를 보안 문자열로 전달하면 안 된다는 메시지 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-131">Without those parameters, you receive a message warning that you shouldn't pass plain text into a secure string.</span></span> <span data-ttu-id="6f8de-132">PowerShell이 이 경고를 반환하는 이유는 일반 텍스트 암호가 다양한 로그에 기록되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-132">PowerShell returns this warning because the plain text password gets recorded in various logs.</span></span> <span data-ttu-id="6f8de-133">보안 문자열을 만든 후 이를 `PSCredential()` 메서드로 전달하여 자격 증명 개체를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-133">Once you have a secure string created, you need to pass it to the `PSCredential()` method to create the credential object.</span></span> <span data-ttu-id="6f8de-134">다음 예제에서 `$password` 변수는 자격 증명 개체를 포함하는 `$Cred` 보안 문자열을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-134">In the following example, the variable `$password` contains the secure string `$Cred` contains the credential object.</span></span>

```powershell
$password = ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("username", $password)
```

<span data-ttu-id="6f8de-135">자격 증명 개체를 만드는 방법을 배웠으므로 이제 PowerShell 함수에 자격 증명 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-135">Now that you know how to create credential objects, you can add credential parameters to your PowerShell functions.</span></span>

## <a name="adding-a-credential-parameter"></a><span data-ttu-id="6f8de-136">자격 증명 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="6f8de-136">Adding a Credential Parameter</span></span>

<span data-ttu-id="6f8de-137">다른 매개 변수와 마찬가지로 함수의 `param` 블록에 추가하여 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-137">Just like any other parameter, you start off by adding it in the `param` block of your function.</span></span>
<span data-ttu-id="6f8de-138">기존 PowerShell cmdlet에서 사용되므로 매개 변수 이름을 `$Credential`로 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-138">It's recommended that you name the parameter `$Credential` because that's what existing PowerShell cmdlets use.</span></span> <span data-ttu-id="6f8de-139">매개 변수 형식은 `[System.Management.Automation.PSCredential]`이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-139">The type of the parameter should be `[System.Management.Automation.PSCredential]`.</span></span>

<span data-ttu-id="6f8de-140">다음 예제는 `Get-Something`이라는 함수의 매개 변수 블록을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-140">The following example shows the parameter block for a function called `Get-Something`.</span></span> <span data-ttu-id="6f8de-141">`$Name`과 `$Credential`이라는 두 개의 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-141">It has two parameters: `$Name` and `$Credential`.</span></span>

```powershell
function Get-Something {
    param(
        $Name,
        [System.Management.Automation.PSCredential]$Credential
    )
```

<span data-ttu-id="6f8de-142">이 예제의 코드도 작동하는 자격 증명 매개 변수를 갖기에 충분하지만 보다 강력한 기능을 위해 몇 가지를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-142">The code in this example is enough to have a working credential parameter, however there are a few things you can add to make it more robust.</span></span>

- <span data-ttu-id="6f8de-143">`[ValidateNotNull()]` 유효성 검사 특성을 추가하여 값이 **Credential** 에 전달되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-143">Add the `[ValidateNotNull()]` validation attribute to check that the value being passed to **Credential**.</span></span> <span data-ttu-id="6f8de-144">매개 변수 값이 null인 경우 이 특성을 사용하면 함수가 잘못된 자격 증명으로 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-144">If the parameter value is null, this attribute prevents the function from executing with invalid credentials.</span></span>

- <span data-ttu-id="6f8de-145">`[System.Management.Automation.Credential()]`를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-145">Add `[System.Management.Automation.Credential()]`.</span></span> <span data-ttu-id="6f8de-146">이렇게 하면 사용자 이름을 문자열로 전달하고 암호를 묻는 대화형 프롬프트를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-146">This allows you to pass in a username as a string and have an interactive prompt for the password.</span></span>

- <span data-ttu-id="6f8de-147">`$Credential` 매개 변수의 기본값을 `[System.Management.Automation.PSCredential]::Empty`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-147">Set a default value for the `$Credential` parameter to `[System.Management.Automation.PSCredential]::Empty`.</span></span> <span data-ttu-id="6f8de-148">함수는 이 `$Credential` 개체를 기존 PowerShell cmdlet에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-148">Your function you might be passing this `$Credential` object to existing PowerShell cmdlets.</span></span> <span data-ttu-id="6f8de-149">함수 내에서 호출된 cmdlet에 null 값을 제공하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-149">Providing a null value to the cmdlet called inside your function causes an error.</span></span> <span data-ttu-id="6f8de-150">빈 자격 증명 개체를 제공하면 이 오류가 방지됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-150">Providing an empty credential object avoids this error.</span></span>

> [!TIP]
> <span data-ttu-id="6f8de-151">자격 증명 매개 변수를 허용하는 일부 cmdlet은 예상과 달리 `[System.Management.Automation.PSCredential]::Empty`를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-151">Some cmdlets that accept a credential parameter do not support `[System.Management.Automation.PSCredential]::Empty` as they should.</span></span> <span data-ttu-id="6f8de-152">해결 방법은 [레거시 cmdlet 처리](#dealing-with-legacy-cmdlets) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f8de-152">See the [Dealing with Legacy Cmdlets](#dealing-with-legacy-cmdlets) section for a workaround.</span></span>

## <a name="using-credential-parameters"></a><span data-ttu-id="6f8de-153">자격 증명 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="6f8de-153">Using credential parameters</span></span>

<span data-ttu-id="6f8de-154">다음 예제는 매개 변수를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-154">The following example demonstrates how to use credential parameters.</span></span> <span data-ttu-id="6f8de-155">이 예제는 [The Pester Book][]에서 가져온 `Set-RemoteRegistryValue`라는 함수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-155">This example shows a function called `Set-RemoteRegistryValue`, which is out of [The Pester Book][].</span></span> <span data-ttu-id="6f8de-156">이 함수는 이전 섹션에 설명된 방법을 사용하여 자격 증명 매개 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-156">This function defines the credential parameter using the techniques describe in the previous section.</span></span> <span data-ttu-id="6f8de-157">이 함수는 함수가 만든 `$Credential` 변수를 사용하여 `Invoke-Command`를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-157">The function calls `Invoke-Command` using the `$Credential` variable created by the function.</span></span> <span data-ttu-id="6f8de-158">이렇게 하면 `Invoke-Command`를 실행하는 사용자를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-158">This allows you to change the user who's running `Invoke-Command`.</span></span> <span data-ttu-id="6f8de-159">`$Credential`의 기본값이 빈 자격 증명이므로 자격 증명을 제공하지 않아도 함수를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-159">Because the default value of `$Credential` is an empty credential, the function can run without providing credentials.</span></span>

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )
        $null = Invoke-Command -ComputerName $ComputerName -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } -Credential $Credential
}
```

<span data-ttu-id="6f8de-160">다음 섹션에서는 `Set-RemoteRegistryValue`에 자격 증명을 제공하는 다양한 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-160">The following sections show different methods of providing credentials to `Set-RemoteRegistryValue`.</span></span>

### <a name="prompting-for-credentials"></a><span data-ttu-id="6f8de-161">자격 증명 입력 요구</span><span class="sxs-lookup"><span data-stu-id="6f8de-161">Prompting for credentials</span></span>

<span data-ttu-id="6f8de-162">런타임에 `()` 괄호 안에 `Get-Credential`을 사용하면 `Get-credential`이 먼저 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-162">Using `Get-Credential` in parentheses `()` at run time causes the `Get-credential` to run first.</span></span> <span data-ttu-id="6f8de-163">사용자 이름과 암호를 묻는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-163">You are prompted for a username and password.</span></span> <span data-ttu-id="6f8de-164">`Get-credential`의 **Credential** 또는 **UserName** 매개 변수를 사용하여 사용자 이름과 도메인을 미리 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-164">You could use the **Credential** or **UserName** parameters of `Get-credential` to pre-populate the username and domain.</span></span> <span data-ttu-id="6f8de-165">다음 예제에서는 스플래팅이라는 방법을 사용하여 매개 변수를 `Set-RemoteRegistryValue` 함수에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-165">The following example uses a technique called splatting to pass parameters to the `Set-RemoteRegistryValue` function.</span></span> <span data-ttu-id="6f8de-166">스플래팅에 대한 자세한 내용은 [about_Splatting][] 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f8de-166">For more information about splatting, check out the [about_Splatting][] article.</span></span>

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential (Get-Credential)
```

![런타임에 자격 증명 가져오기](./media/add-credentials-to-powershell-functions/GetCredAtRunTime.gif)

<span data-ttu-id="6f8de-168">`(Get-Credential)` 사용은 번거로워 보입니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-168">Using `(Get-Credential)` seems cumbersome.</span></span> <span data-ttu-id="6f8de-169">일반적으로 사용자 이름만으로 **Credential** 매개 변수를 사용하면 cmdlet은 자동으로 암호를 묻는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-169">Normally, when you use the **Credential** parameter with only a username, the cmdlet automatically prompts for the password.</span></span> <span data-ttu-id="6f8de-170">`[System.Management.Automation.Credential()]` 특성은 이 동작을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-170">The `[System.Management.Automation.Credential()]` attribute enables this behavior.</span></span>

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential duffney
```

![자격 증명 확인](./media/add-credentials-to-powershell-functions/GetCredsPrompt.gif)

> [!NOTE]
> <span data-ttu-id="6f8de-172">표시되는 레지스트리 값을 설정하기 위해 이 예제에서는 Windows의 **웹 서버** 기능이 설치되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-172">To set the registry value shown, these examples assume you have the **Web Server** features of Windows installed.</span></span> <span data-ttu-id="6f8de-173">필요한 경우 `Install-WindowsFeature Web-Server`와 `Install-WindowsFeature web-mgmt-tools`를 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="6f8de-173">Run `Install-WindowsFeature Web-Server` and `Install-WindowsFeature web-mgmt-tools` if required.</span></span>

### <a name="provide-credentials-in-a-variable"></a><span data-ttu-id="6f8de-174">변수에서 자격 증명 제공</span><span class="sxs-lookup"><span data-stu-id="6f8de-174">Provide credentials in a variable</span></span>

<span data-ttu-id="6f8de-175">미리 자격 증명 변수를 채우고 `Set-RemoteRegistryValue` 함수의 **Credential** 매개 변수에 전달할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-175">You can also populate a credential variable ahead of time and pass it to the **Credential** parameter of `Set-RemoteRegistryValue` function.</span></span> <span data-ttu-id="6f8de-176">Jenkins, TeamCity, Octopus Deploy와 같은 CI/CD(연속 통합/지속적인 배포) 도구에 이 메서드를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="6f8de-176">Use this method with Continuous Integration / Continuous Deployment (CI/CD) tools such as Jenkins, TeamCity, and Octopus Deploy.</span></span> <span data-ttu-id="6f8de-177">Jenkins를 사용하는 예제는 Hodge의 블로그 [Automating with Jenkins and PowerShell on Windows - Part 2][] 게시물을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f8de-177">For an example using Jenkins, check out Hodge's blog post [Automating with Jenkins and PowerShell on Windows - Part 2][].</span></span>

<span data-ttu-id="6f8de-178">이 예제는 .NET 메서드를 사용하여 암호에 전달할 보안 문자열과 자격 증명 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-178">This example uses the .NET method to create the credential object and a secure string to pass in the password.</span></span>

```powershell
$password = ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("duffney", $password)

$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential $Cred
```

<span data-ttu-id="6f8de-179">이 예제에서는 일반 텍스트 암호를 사용하여 보안 문자열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-179">For this example, the secure string is created using a clear text password.</span></span> <span data-ttu-id="6f8de-180">앞에서 언급한 모든 CI/CD에는 런타임에 해당 암호를 제공하는 안전한 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-180">All of the previously mentioned CI/CD have a secure method of providing that password at run time.</span></span> <span data-ttu-id="6f8de-181">이러한 도구를 사용하는 경우 사용하는 CI/CD 도구 내에서 정의된 변수로 일반 텍스트 암호를 바꾸세요.</span><span class="sxs-lookup"><span data-stu-id="6f8de-181">When using those tools, replace the plain text password with the variable defined within the CI/CD tool you use.</span></span>

### <a name="run-without-credentials"></a><span data-ttu-id="6f8de-182">자격 증명 없이 실행</span><span class="sxs-lookup"><span data-stu-id="6f8de-182">Run without credentials</span></span>

<span data-ttu-id="6f8de-183">`$Credential`은 빈 자격 증명 개체가 기본값이므로 다음 예제와 같이 자격 증명 없이 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-183">Since `$Credential` defaults to an empty credential object, you can run the command without credentials, as shown in this example:</span></span>

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams
```

## <a name="dealing-with-legacy-cmdlets"></a><span data-ttu-id="6f8de-184">레거시 cmdlet 처리</span><span class="sxs-lookup"><span data-stu-id="6f8de-184">Dealing with legacy cmdlets</span></span>

<span data-ttu-id="6f8de-185">모든 cmdlet이 자격 증명 개체를 지원하거나 빈 자격 증명을 허용하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-185">Not all cmdlets support credential objects or allow empty credentials.</span></span> <span data-ttu-id="6f8de-186">대신 cmdlet은 사용자 이름 및 암호 매개 변수가 문자열이기를 원합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-186">Instead, the cmdlet wants username and password parameters as strings.</span></span> <span data-ttu-id="6f8de-187">이 제한 사항을 해결하는 몇 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-187">There are a few ways to work around this limitation.</span></span>

### <a name="using-if-else-to-handle-empty-credentials"></a><span data-ttu-id="6f8de-188">if-else를 사용하여 빈 자격 증명 처리</span><span class="sxs-lookup"><span data-stu-id="6f8de-188">Using if-else to handle empty credentials</span></span>

<span data-ttu-id="6f8de-189">이 시나리오에서 실행할 cmdlet은 빈 자격 증명 개체를 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-189">In this scenario, the cmdlet you want to run doesn't accept an empty credential object.</span></span> <span data-ttu-id="6f8de-190">이 예제는 **Credential** 매개 변수가 비어 있지 않은 경우에만 `Invoke-Command`에 이를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-190">This example adds the **Credential** parameter to `Invoke-Command` only if it's not empty.</span></span> <span data-ttu-id="6f8de-191">비어 있으면 **Credential** 매개 변수 없이 `Invoke-Command`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-191">Otherwise, it runs the `Invoke-Command` without the **Credential** parameter.</span></span>

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

    if($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
        Invoke-Command -ComputerName:$ComputerName -Credential:$Credential  {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    } else {
        Invoke-Command -ComputerName:$ComputerName {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    }
}
```

### <a name="using-splatting-to-handle-empty-credentials"></a><span data-ttu-id="6f8de-192">스플래팅을 사용하여 빈 자격 증명 처리</span><span class="sxs-lookup"><span data-stu-id="6f8de-192">Using splatting to handle empty credentials</span></span>

<span data-ttu-id="6f8de-193">이 예제는 매개 변수 스플래팅을 사용하여 레거시 cmdlet을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-193">This example uses parameter splatting to call the legacy cmdlet.</span></span> <span data-ttu-id="6f8de-194">`$Credential` 개체는 조건부로 스플래팅 해시 테이블에 추가되며, `Invoke-Command` 스크립트 블록을 반복하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-194">The `$Credential` object is conditionally added to the hash table for splatting and avoids the need to repeat the `Invoke-Command` script block.</span></span> <span data-ttu-id="6f8de-195">함수 내에서의 스플래팅에 대한 자세한 내용은 [Splatting Parameters Inside Advanced Functions][] 블로그 게시물을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f8de-195">To learn more about splatting inside functions, see the [Splatting Parameters Inside Advanced Functions][] blog post.</span></span>

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $Splat = @{
            ComputerName = $ComputerName
        }

        if ($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
            $Splat['Credential'] = $Credential
        }

        $null = Invoke-Command -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } @splat
}
```

### <a name="working-with-string-passwords"></a><span data-ttu-id="6f8de-196">문자열 암호 사용</span><span class="sxs-lookup"><span data-stu-id="6f8de-196">Working with string passwords</span></span>

<span data-ttu-id="6f8de-197">`Invoke-Sqlcmd` cmdlet은 문자열을 암호로 허용하는 cmdlet의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-197">The `Invoke-Sqlcmd` cmdlet is an example of a cmdlet that accepts a string as a password.</span></span>
<span data-ttu-id="6f8de-198">`Invoke-Sqlcmd`를 사용하면 간단한 SQL insert, update, delete 문을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-198">`Invoke-Sqlcmd` allows you to run simple SQL insert, update, and delete statements.</span></span> <span data-ttu-id="6f8de-199">`Invoke-Sqlcmd`에서는 더 안전한 자격 증명 개체보다는 일반 텍스트 사용자 이름 및 암호를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-199">`Invoke-Sqlcmd` requires a clear-text username and password rather than a more secure credential object.</span></span> <span data-ttu-id="6f8de-200">이 예제는 자격 증명 개체에서 사용자 이름 및 암호를 추출하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-200">This example shows how to extract the username and password from a credential object.</span></span>

<span data-ttu-id="6f8de-201">이 예제의 `Get-AllSQLDatabases` 함수는 `Invoke-Sqlcmd` cmdlet을 호출하여 SQL Server에서 모든 해당 데이터베이스를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-201">The `Get-AllSQLDatabases` function in this example calls the `Invoke-Sqlcmd` cmdlet to query a SQL server for all its databases.</span></span> <span data-ttu-id="6f8de-202">이 함수는 이전 예제에서 사용된 것과 동일한 특성을 사용하여 **Credential** 매개 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-202">The function defines a **Credential** parameter with the same attribute used in the previous examples.</span></span> <span data-ttu-id="6f8de-203">사용자 이름과 암호가 `$Credential` 변수 내에 있기 때문에 `Invoke-Sqlcmd`에 사용할 값을 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-203">Since the username and password exist within the `$Credential` variable, you can extract those values for use with `Invoke-Sqlcmd`.</span></span>

<span data-ttu-id="6f8de-204">사용자 이름은 `$Credential` 변수의 **UserName** 속성에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-204">The user name is available from the **UserName** property of the `$Credential` variable.</span></span> <span data-ttu-id="6f8de-205">암호를 가져오려면 `$Credential` 개체의 `GetNetworkCredential()` 메서드를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-205">To obtain the password, you have to use the `GetNetworkCredential()` method of the `$Credential` object.</span></span> <span data-ttu-id="6f8de-206">값은 `Invoke-Sqlcmd`에 대한 매개 변수 스플래팅에 사용되는 해시 테이블에 추가되는 변수로 추출됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-206">The values are extracted into variables that are added to a hash table used for splatting parameters to `Invoke-Sqlcmd`.</span></span>

```powershell
function Get-AllSQLDatabases {
    param(
        $SQLServer,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $UserName = $Credential.UserName
        $Password = $Credential.GetNetworkCredential().Password

        $splat = @{
            UserName = $UserName
            Password = $Password
            ServerInstance = 'SQLServer'
            Query = "Select * from Sys.Databases"
        }

        Invoke-Sqlcmd @splat
}

$credSplat = @{
    TypeName = 'System.Management.Automation.PSCredential'
    ArgumentList = 'duffney',('P@ssw0rd' | ConvertTo-SecureString -AsPlainText -Force)
}
$Credential= New-Object @credSplat
ConvertTo-SecureString -AsPlainText -Force)

Get-AllSQLDatabases -SQLServer SQL01 -Credential $Credential
```

## <a name="continued-learning-credential-management"></a><span data-ttu-id="6f8de-207">자격 증명 관리 학습 계속</span><span class="sxs-lookup"><span data-stu-id="6f8de-207">Continued learning credential management</span></span>

<span data-ttu-id="6f8de-208">자격 증명 개체를 안전하게 만들고 저장하는 것은 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-208">Creating and storing credential objects securely can be difficult.</span></span> <span data-ttu-id="6f8de-209">다음 리소스는 PowerShell 자격 증명을 유지하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f8de-209">The following resources can help you maintain PowerShell credentials.</span></span>

- <span data-ttu-id="6f8de-210">[BetterCredentials][]</span><span class="sxs-lookup"><span data-stu-id="6f8de-210">[BetterCredentials][]</span></span>
- <span data-ttu-id="6f8de-211">[Azure Key Vault][]</span><span class="sxs-lookup"><span data-stu-id="6f8de-211">[Azure Key Vault][]</span></span>
- <span data-ttu-id="6f8de-212">[Vault Project][]</span><span class="sxs-lookup"><span data-stu-id="6f8de-212">[Vault Project][]</span></span>
- <span data-ttu-id="6f8de-213">[SecretManagement 모듈][]</span><span class="sxs-lookup"><span data-stu-id="6f8de-213">[SecretManagement module][]</span></span>

<!-- link references -->
[원래 버전]: https://duffney.io/addcredentialstopowershellfunctions/
[original version]: https://duffney.io/addcredentialstopowershellfunctions/
[@joshduffney]: https://twitter.com/joshduffney
[duffney.io]: https://duffney.io/posts/
[BetterCredentials]: https://www.powershellgallery.com/packages/BetterCredentials/
[Azure Key Vault]: https://azure.microsoft.com/services/key-vault/
[Vault Project]: https://www.vaultproject.io/
[Splatting Parameters Inside Advanced Functions]: https://duffney.io/Splatting-Parameters-Within-AdvancedFunctions
[Automating with Jenkins and PowerShell on Windows - Part 2]: https://hodgkins.io/automating-with-jenkins-and-powershell-on-windows-part-2
[PSCredential]: /dotnet/api/system.management.automation.pscredential
[The Pester Book]: https://leanpub.com/the-pester-book
[about_Splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[SecretManagement 모듈]: https://devblogs.microsoft.com/powershell/secretmanagement-and-secretstore-updates/
[SecretManagement module]: https://devblogs.microsoft.com/powershell/secretmanagement-and-secretstore-updates/
