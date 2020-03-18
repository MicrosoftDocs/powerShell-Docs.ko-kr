---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: JEA 역할 기능
ms.openlocfilehash: 5b5b5977d4fec1ed850f1146fe7c09463908651b
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402400"
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="2f3e9-103">JEA 역할 기능</span><span class="sxs-lookup"><span data-stu-id="2f3e9-103">JEA Role Capabilities</span></span>

<span data-ttu-id="2f3e9-104">JEA 엔드포인트를 만들 때 사용자가 JEA 세션에서 수행할 수 있는 작업을 설명하는 하나 이상의 역할 기능을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-104">When creating a JEA endpoint, you need to define one or more role capabilities that describe what someone can do in a JEA session.</span></span> <span data-ttu-id="2f3e9-105">역할 기능은 연결하는 사용자에게 제공되어야 하는 모든 cmdlet, 함수, 공급자 및 외부 프로그램을 나열하는 PowerShell 데이터 파일로서 확장명은 `.psrc`입니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-105">A role capability is a PowerShell data file with the `.psrc` extension that lists all the cmdlets, functions, providers, and external programs that are made available to connecting users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="2f3e9-106">허용할 명령 결정</span><span class="sxs-lookup"><span data-stu-id="2f3e9-106">Determine which commands to allow</span></span>

<span data-ttu-id="2f3e9-107">역할 기능 파일을 만드는 첫 번째 단계는 사용자가 액세스해야 하는 항목을 고려하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-107">The first step in creating a role capability file is to consider what the users need access to.</span></span> <span data-ttu-id="2f3e9-108">이 요구 사항 수집 프로세스는 시간이 약간 걸릴 수 있지만, 중요한 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-108">The requirements gathering process can take a while, but it's an important process.</span></span> <span data-ttu-id="2f3e9-109">사용자에게 너무 적은 cmdlet 및 함수에 대한 액세스 권한을 부여하면 사용자가 작업을 수행하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-109">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span> <span data-ttu-id="2f3e9-110">너무 많은 cmdlet 및 함수에 액세스를 허용하면 사용자가 의도한 것보다 더 많은 작업을 수행할 수 있으며 보안 태세를 약화시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-110">Allowing access to too many cmdlets and functions can allow users to do more than you intended and weaken your security stance.</span></span>

<span data-ttu-id="2f3e9-111">이 프로세스를 진행하는 방법은 조직과 목표에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-111">How you go about this process depends on your organization and goals.</span></span> <span data-ttu-id="2f3e9-112">다음 팁이 올바른 경로인지 확인하는 데 도움을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-112">The following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="2f3e9-113">**식별**: 사용자가 작업을 수행하는 데 사용하는 명령을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-113">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="2f3e9-114">이 과정에는 IT 직원을 대상으로 설문 조사를 진행하거나 자동화 스크립트를 확인하거나 PowerShell 세션 기록 및 로그를 분석하는 작업이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-114">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts and logs.</span></span>
2. <span data-ttu-id="2f3e9-115">최상의 감사 및 JEA 사용자 지정 환경을 위해 가능한 경우 PowerShell에 해당하는 명령줄 도구를 **업데이트**합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-115">**Update** use of command-line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="2f3e9-116">외부 프로그램은 JEA의 네이티브 PowerShell cmdlet 및 함수만큼 세부적으로 제한할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-116">External programs can't be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="2f3e9-117">특정 매개 변수 또는 매개 변수 값만 허용하도록 cmdlet의 범위를 **제한**합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-117">**Restrict** the scope of the cmdlets to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="2f3e9-118">이는 사용자가 시스템의 일부만 관리해야 하는 경우에 특히 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-118">This is especially important if users should manage only part of a system.</span></span>
4. <span data-ttu-id="2f3e9-119">복잡한 명령이나 JEA에서 제한하기 어려운 명령을 대체할 사용자 지정 함수를 **만듭니다**.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-119">**Create** custom functions to replace complex commands or commands that are difficult to constrain in JEA.</span></span> <span data-ttu-id="2f3e9-120">복잡한 명령을 래핑하거나 추가 유효성 검사 논리를 적용하는 간단한 함수는 관리자 및 최종 사용자의 편의를 위한 추가 제어를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-120">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="2f3e9-121">사용자 또는 자동화 서비스로 허용되는 명령의 범위가 지정된 목록을 **테스트**하고 필요에 따라 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-121">**Test** the scoped list of allowable commands with your users or automation services, and adjust as necessary.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="2f3e9-122">잠재적으로 위험한 명령의 예</span><span class="sxs-lookup"><span data-stu-id="2f3e9-122">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="2f3e9-123">JEA 엔드포인트에서 사용자가 자신의 권한을 상승시킬 수 없도록 하려면 명령을 신중하게 선택하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-123">Careful selection of commands is important to ensure the JEA endpoint doesn't allow the user to elevate their permissions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2f3e9-124">JEA 세션의 사용자 successCommands에 필요한 필수 정보는 승격된 권한으로 실행되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-124">Essential information required for user successCommands in a JEA session are often run with elevated privileges.</span></span>

<span data-ttu-id="2f3e9-125">다음 표에는 비제한 상태에서 허용되는 경우 악의적으로 사용될 수 있는 명령의 예가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-125">The following table contains examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span> <span data-ttu-id="2f3e9-126">이는 전체 목록이 아니며 경고성 시작 지점으로만 사용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-126">This isn't an exhaustive list and should only be used as a cautionary starting point.</span></span>

|                                            <span data-ttu-id="2f3e9-127">위험</span><span class="sxs-lookup"><span data-stu-id="2f3e9-127">Risk</span></span>                                            |                                <span data-ttu-id="2f3e9-128">예제</span><span class="sxs-lookup"><span data-stu-id="2f3e9-128">Example</span></span>                                |                                                                              <span data-ttu-id="2f3e9-129">관련 명령</span><span class="sxs-lookup"><span data-stu-id="2f3e9-129">Related commands</span></span>                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="2f3e9-130">연결하는 사용자에게 JEA를 바이패스할 수 있는 관리자 권한 부여</span><span class="sxs-lookup"><span data-stu-id="2f3e9-130">Granting the connecting user admin privileges to bypass JEA</span></span>                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="2f3e9-131">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="2f3e9-131">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>                                                                                                        |
| <span data-ttu-id="2f3e9-132">맬웨어, 익스플로잇 또는 보호를 바이패스하는 사용자 지정 스크립트와 같은 임의의 코드 실행</span><span class="sxs-lookup"><span data-stu-id="2f3e9-132">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'`                   | <span data-ttu-id="2f3e9-133">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="2f3e9-133">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span> |

## <a name="create-a-role-capability-file"></a><span data-ttu-id="2f3e9-134">역할 기능 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="2f3e9-134">Create a role capability file</span></span>

<span data-ttu-id="2f3e9-135">[New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6) cmdlet을 사용하여 새 PowerShell 역할 기능 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-135">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="2f3e9-136">역할에 필요한 명령을 허용하도록 결과 역할 기능 파일을 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-136">The resulting role capability file should be edited to allow the commands required for the role.</span></span> <span data-ttu-id="2f3e9-137">PowerShell 도움말 문서에는 파일을 구성하는 방법의 몇 가지 예제가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-137">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="2f3e9-138">PowerShell cmdlet 및 함수 허용</span><span class="sxs-lookup"><span data-stu-id="2f3e9-138">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="2f3e9-139">사용자에게 PowerShell cmdlet 또는 함수를 실행할 수 있는 권한을 부여하려면 VisibleCmdlets 또는 VisibleFunctions 필드에 cmdlet 또는 함수 이름을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-139">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisibleCmdlets or VisibleFunctions fields.</span></span> <span data-ttu-id="2f3e9-140">명령이 cmdlet인지 또는 함수인지 확실하지 않은 경우 `Get-Command <name>`을 실행하고 출력에서 **CommandType** 속성을 확인하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-140">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the **CommandType** property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="2f3e9-141">때때로 특정 cmdlet 또는 함수의 범위는 사용자의 요구 사항보다 너무 광범위합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-141">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span> <span data-ttu-id="2f3e9-142">예를 들어 DNS 관리자는 DNS 서비스를 다시 시작할 수 있는 권한만 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-142">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span> <span data-ttu-id="2f3e9-143">다중 테넌트 환경에서 테넌트는 셀프 서비스 관리 도구에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-143">In multi-tenant environments, tenants have access to self-service management tools.</span></span> <span data-ttu-id="2f3e9-144">테넌트는 자신의 리소스를 관리하는 것으로 제한되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-144">Tenants should be limited to managing their own resources.</span></span> <span data-ttu-id="2f3e9-145">이러한 경우 cmdlet 또는 함수에서 노출되는 매개 변수를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

<span data-ttu-id="2f3e9-146">보다 고급 시나리오에서는 사용자가 이러한 매개 변수에 사용할 수 있는 값을 제한해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-146">In more advanced scenarios, you may also need to restrict the values a user may use with these parameters.</span></span> <span data-ttu-id="2f3e9-147">역할 기능을 통해 허용되는 입력을 결정하는 값 세트 또는 정규식 패턴을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-147">Role capabilities let you define a set of values or a regular expression pattern that determine what input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="2f3e9-148">[common PowerShell parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters)(일반적인 PowerShell 매개 변수)는 사용할 수 있는 매개 변수를 제한하는 경우에도 항상 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-148">The [common PowerShell parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="2f3e9-149">그러나 Parameters 필드에 해당 매개 변수를 명시적으로 나열해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="2f3e9-150">아래 표에는 표시되는 cmdlet 또는 함수를 사용자 지정할 수 있는 다양한 방법이 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="2f3e9-151">**VisibleCmdlets** 필드에 다음 중 하나를 조합하여 일치시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-151">You can mix and match any of the below in the **VisibleCmdlets** field.</span></span>

|                                           <span data-ttu-id="2f3e9-152">예제</span><span class="sxs-lookup"><span data-stu-id="2f3e9-152">Example</span></span>                                           |                                                             <span data-ttu-id="2f3e9-153">사용 사례</span><span class="sxs-lookup"><span data-stu-id="2f3e9-153">Use case</span></span>                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="2f3e9-154">`'My-Func'` 또는 `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="2f3e9-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                      | <span data-ttu-id="2f3e9-155">사용자는 매개 변수에 대한 제한 없이 `My-Func`를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>                                                      |
| `'MyModule\My-Func'`                                                                        | <span data-ttu-id="2f3e9-156">사용자는 매개 변수에 대한 제한 없이 `MyModule` 모듈에서 `My-Func`를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>                           |
| `'My-*'`                                                                                    | <span data-ttu-id="2f3e9-157">사용자는 동사 `My`가 포함된 모든 cmdlet 또는 함수를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>                                                                 |
| `'*-Func'`                                                                                  | <span data-ttu-id="2f3e9-158">사용자는 명사 `Func`가 포함된 모든 cmdlet 또는 함수를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | <span data-ttu-id="2f3e9-159">사용자는 `Param1` 및 `Param2` 매개 변수를 사용하여 `My-Func`를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-159">Allows the user to run `My-Func` with the `Param1` and `Param2` parameters.</span></span> <span data-ttu-id="2f3e9-160">매개 변수에 아무 값이나 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-160">Any value can be supplied to the parameters.</span></span>          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | <span data-ttu-id="2f3e9-161">사용자는 `Param1` 매개 변수를 사용하여 `My-Func`를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="2f3e9-162">매개 변수에 "Value1" 및 "Value2"만 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | <span data-ttu-id="2f3e9-163">사용자는 `Param1` 매개 변수를 사용하여 `My-Func`를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="2f3e9-164">매개 변수에 "contoso"로 시작하는 모든 값을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-164">Any value starting with "contoso" can be supplied to the parameter.</span></span> |

> [!WARNING]
> <span data-ttu-id="2f3e9-165">최상의 보안 방식을 위해 표시되는 cmdlet 또는 함수를 정의할 때 와일드카드는 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span> <span data-ttu-id="2f3e9-166">대신 신뢰할 수 있는 각 명령을 명시적으로 나열하여 같은 이름 지정 체계를 공유하는 다른 명령에 의도치 않게 권한이 부여되지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="2f3e9-167">동일한 cmdlet 또는 함수에 **ValidatePattern**과 **ValidateSet**를 둘 다 적용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-167">You can't apply both a **ValidatePattern** and **ValidateSet** to the same cmdlet or function.</span></span>

<span data-ttu-id="2f3e9-168">둘 다 적용할 경우 **ValidatePattern**이 **ValidateSet**를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-168">If you do, the **ValidatePattern** overrides the **ValidateSet**.</span></span>

<span data-ttu-id="2f3e9-169">**ValidatePattern**에 대한 자세한 내용은 [이 *Hey, Scripting Guy!* 게시물](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) 및 [PowerShell 정규식](/powershell/module/microsoft.powershell.core/about/about_regular_expressions) 참조 콘텐츠를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-169">For more information about **ValidatePattern**, check out [this *Hey, Scripting Guy!* post](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](/powershell/module/microsoft.powershell.core/about/about_regular_expressions) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="2f3e9-170">외부 명령 및 PowerShell 스크립트 허용</span><span class="sxs-lookup"><span data-stu-id="2f3e9-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="2f3e9-171">사용자가 JEA 세션에서 실행 파일 및 PowerShell 스크립트(.ps1)를 실행할 수 있게 하려면 **VisibleExternalCommands** 필드에 각 프로그램의 전체 경로를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the **VisibleExternalCommands** field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="2f3e9-172">PowerShell cmdlet 및 함수에서 허용되는 매개 변수를 제어할 수 있으므로, 가능한 경우 권한을 부여하는 외부 실행 파일에 대해 해당 PowerShell cmdlet 또는 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-172">Where possible, to use PowerShell cmdlet or function equivalents for any external executables you authorize since you have control over the parameters allowed with PowerShell cmdlets and functions.</span></span>

<span data-ttu-id="2f3e9-173">많은 실행 파일을 통해 현재 상태를 읽은 다음, 다른 매개 변수를 제공하여 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-173">Many executables allow you to read the current state and then change it by providing different parameters.</span></span>

<span data-ttu-id="2f3e9-174">예를 들어 시스템에서 호스팅되는 네트워크 공유를 관리하는 파일 서버 관리자의 역할을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-174">For example, consider the role of a file server admin that manages network shares hosted on a system.</span></span> <span data-ttu-id="2f3e9-175">공유를 관리하는 한 가지 방법은 `net share`를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-175">One way of managing shares is to use `net share`.</span></span> <span data-ttu-id="2f3e9-176">그러나 사용자가 명령을 사용하여 `net group Administrators unprivilegedjeauser /add`로 관리자 권한을 얻을 수 있으므로 **net.exe**를 허용하는 것은 위험합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-176">However, allowing **net.exe** is dangerous because the user could use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span> <span data-ttu-id="2f3e9-177">더 안전한 옵션은 [Get-SmbShare](/powershell/module/smbshare/get-smbshare)를 허용하는 것으로, 결과는 동일하지만 범위는 훨씬 제한적입니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-177">A more secure option is to allow [Get-SmbShare](/powershell/module/smbshare/get-smbshare), which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="2f3e9-178">JEA 세션에서 사용자가 외부 명령을 사용할 수 있게 하려면 항상 실행 파일의 전체 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-178">When making external commands available to users in a JEA session, always specify the complete path to the executable.</span></span> <span data-ttu-id="2f3e9-179">이렇게 하면 시스템의 다른 위치에 있는 이름이 비슷하거나 잠재적으로 악의적인 프로그램이 실행되는 것을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-179">This prevents the execution of similarly named and potentially malicious programs located elsewhere on the system.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="2f3e9-180">PowerShell 공급자에 대한 액세스 허용</span><span class="sxs-lookup"><span data-stu-id="2f3e9-180">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="2f3e9-181">기본적으로 JEA 세션에서는 PowerShell 공급자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-181">By default, no PowerShell providers are available in JEA sessions.</span></span> <span data-ttu-id="2f3e9-182">이렇게 하면 중요한 정보 및 구성 설정이 연결하는 사용자에게 공개되는 위험이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-182">This reduces the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="2f3e9-183">필요한 경우 `VisibleProviders` 명령을 사용하여 PowerShell 공급자에 대한 액세스를 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-183">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span> <span data-ttu-id="2f3e9-184">전체 공급자 목록을 보려면 `Get-PSProvider`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-184">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="2f3e9-185">파일 시스템, 레지스트리, 인증서 저장소 또는 기타 중요 공급자에 액세스해야 하는 간단한 작업의 경우, 사용자를 대신하여 공급자가 작동하는 사용자 지정 함수 작성을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-185">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, consider writing a custom function that works with the provider on the user's behalf.</span></span> <span data-ttu-id="2f3e9-186">JEA 세션에서 사용할 수 있는 함수, cmdlet 및 외부 프로그램은 JEA와 동일한 제약 조건이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-186">The functions, cmdlets, and external programs available in a JEA session aren't subject to the same constraints as JEA.</span></span> <span data-ttu-id="2f3e9-187">기본적으로 모든 공급자에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-187">They can access any provider by default.</span></span> <span data-ttu-id="2f3e9-188">또한 JEA 엔드포인트 간에 파일을 복사해야 하는 경우 [사용자 드라이브](session-configurations.md#user-drive) 사용을 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-188">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to or from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="2f3e9-189">사용자 지정 함수 만들기</span><span class="sxs-lookup"><span data-stu-id="2f3e9-189">Creating custom functions</span></span>

<span data-ttu-id="2f3e9-190">역할 기능 파일에서 사용자 지정 함수를 작성하여 최종 사용자에 대한 복잡한 작업을 간소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-190">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span> <span data-ttu-id="2f3e9-191">사용자 지정 함수는 cmdlet 매개 변수 값에 대한 고급 유효성 검사 논리가 필요한 경우에도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-191">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span> <span data-ttu-id="2f3e9-192">**FunctionDefinitions** 필드에서 간단한 함수를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-192">You can write simple functions in the **FunctionDefinitions** field:</span></span>

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending |
            Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="2f3e9-193">JEA 사용자가 사용자 지정 함수를 실행할 수 있도록 사용자 지정 함수의 이름을 **VisibleFunctions** 필드에 잊지 말고 추가하세요.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-193">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>

<span data-ttu-id="2f3e9-194">사용자 지정 함수의 본문(스크립트 블록)은 시스템에 대한 기본 언어 모드에서 실행되며 JEA의 언어 제약 조건이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-194">The body (script block) of custom functions runs in the default language mode for the system and isn't subject to JEA's language constraints.</span></span> <span data-ttu-id="2f3e9-195">즉, 함수는 파일 시스템 및 레지스트리에 액세스하고 역할 기능 파일에 표시되도록 설정되지 않은 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-195">This means that functions can access the file system and registry, and run commands that weren't made visible in the role capability file.</span></span> <span data-ttu-id="2f3e9-196">매개 변수를 사용할 때 임의의 코드가 실행되지 않도록 주의하세요.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-196">Take care to avoid running arbitrary code when using parameters.</span></span> <span data-ttu-id="2f3e9-197">사용자 입력을 `Invoke-Expression`과 같은 cmdlet에 직접 연결하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-197">Avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="2f3e9-198">위 예제에서 축약형 `Select-Object` 대신 FQMN(정규화된 모듈 이름) `Microsoft.PowerShell.Utility\Select-Object`가 사용되었다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-198">In the above example, notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="2f3e9-199">역할 기능 파일에 정의된 함수에는 여전히 JEA 세션의 범위가 적용되며 여기에는 JEA가 기존 명령을 제한하기 위해 만드는 프록시 함수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-199">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="2f3e9-200">기본적으로 `Select-Object`는 개체에 대한 임의 속성을 선택할 수 없게 하는, 모든 JEA 세션의 제한된 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-200">By default, `Select-Object` is a constrained cmdlet in all JEA sessions that doesn't allow the selection of arbitrary properties on objects.</span></span> <span data-ttu-id="2f3e9-201">함수에서 비제한 `Select-Object`를 사용하려면 FQMN을 사용하여 전체 구현을 명시적으로 요청해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-201">To use the unconstrained `Select-Object` in functions, you must explicitly request the full implementation using the FQMN.</span></span> <span data-ttu-id="2f3e9-202">JEA 세션에서 제한된 cmdlet에는 함수에서 호출될 때 동일한 제약 조건이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-202">Any constrained cmdlet in a JEA session has the same constraints when invoked from a function.</span></span> <span data-ttu-id="2f3e9-203">자세한 내용은 [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-203">For more information, see [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="2f3e9-204">여러 개의 사용자 지정 함수를 작성하는 경우 PowerShell 스크립트 모듈에 배치하는 것이 더 편리합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-204">If you're writing several custom functions, it's more convenient to put them in a PowerShell script module.</span></span> <span data-ttu-id="2f3e9-205">기본 제공 및 타사 모듈을 사용할 때처럼 **VisibleFunctions** 필드를 사용하여 JEA 세션에서 해당 함수를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-205">You make those functions visible in the JEA session using the **VisibleFunctions** field like you would with built-in and third-party modules.</span></span>

<span data-ttu-id="2f3e9-206">JEA 세션에서 탭 완료가 제대로 작동하려면 **VisibleFunctions** 목록에 기본 제공 함수 `tabexpansion2`를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-206">For tab completion to work properly in JEA sessions you must include the built-in function `tabexpansion2` in the **VisibleFunctions** list.</span></span>

## <a name="make-the-role-capabilities-available-to-a-configuration"></a><span data-ttu-id="2f3e9-207">구성에서 역할 기능을 사용할 수 있도록 설정</span><span class="sxs-lookup"><span data-stu-id="2f3e9-207">Make the role capabilities available to a configuration</span></span>

<span data-ttu-id="2f3e9-208">PowerShell 6 이전의 경우 PowerShell에서 역할 기능 파일을 찾으려면 역할 기능 파일을 PowerShell 모듈의 **RoleCapabilities** 폴더에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-208">Prior to PowerShell 6, for PowerShell to find a role capability file it must be stored in a **RoleCapabilities** folder in a PowerShell module.</span></span> <span data-ttu-id="2f3e9-209">모듈은 `$env:PSModulePath` 환경 변수에 포함된 모든 폴더에 저장할 수 있지만, `$env:SystemRoot\System32` 또는 신뢰할 수 없는 사용자가 파일을 수정할 수 있는 폴더에 배치해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-209">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you shouldn't place it in `$env:SystemRoot\System32` or a folder where untrusted users could modify the files.</span></span>

<span data-ttu-id="2f3e9-210">다음 예에서는 역할 기능 파일을 호스트하기 위해 `$env:ProgramFiles` 경로에 **ContosoJEA**라는 PowerShell 스크립트 모듈을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-210">The following example creates a PowerShell script module called **ContosoJEA** in the `$env:ProgramFiles` path to host the role capabilities file.</span></span>

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest.
# At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

<span data-ttu-id="2f3e9-211">PowerShell 모듈에 대한 자세한 내용은 [PowerShell 모듈 이해](/powershell/scripting/developer/windows-powershell)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-211">For more information about PowerShell modules, see [Understanding a PowerShell Module](/powershell/scripting/developer/windows-powershell).</span></span>

<span data-ttu-id="2f3e9-212">PowerShell 6부터 **RoleDefinitions** 속성이 세션 구성 파일에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-212">Starting in PowerShell 6, the **RoleDefinitions** property was added to the session configuration file.</span></span> <span data-ttu-id="2f3e9-213">이 속성을 사용하여 역할 정의에 대한 역할 구성 파일의 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-213">This property lets you specify the location of a role configuration file for your role definition.</span></span> <span data-ttu-id="2f3e9-214">[New-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile)의 예를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-214">See the examples in [New-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile).</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="2f3e9-215">역할 기능 업데이트</span><span class="sxs-lookup"><span data-stu-id="2f3e9-215">Updating role capabilities</span></span>

<span data-ttu-id="2f3e9-216">역할 기능 파일을 편집하여 언제든지 설정을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-216">You can edit a role capability file to update the settings at any time.</span></span> <span data-ttu-id="2f3e9-217">역할 기능이 업데이트된 후 시작되는 모든 새 JEA 세션은 수정된 기능을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-217">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="2f3e9-218">그러므로 역할 기능 폴더에 대한 액세스를 제어하는 것은 매우 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-218">This is why controlling access to the role capabilities folder is so important.</span></span> <span data-ttu-id="2f3e9-219">매우 신뢰할 수 있는 관리자만 역할 기능 파일을 변경할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-219">Only highly trusted administrators should be allowed to change role capability files.</span></span> <span data-ttu-id="2f3e9-220">신뢰할 수 없는 사용자가 역할 기능 파일을 변경할 수 있는 경우 자신의 권한을 상승시킬 수 있는 cmdlet에 대한 액세스 권한을 쉽게 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-220">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets that allow them to elevate their privileges.</span></span>

<span data-ttu-id="2f3e9-221">역할 기능에 대한 액세스를 제한하려는 관리자의 경우 로컬 시스템에 역할 기능 파일 및 포함하는 모듈에 대한 읽기 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-221">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="2f3e9-222">역할 기능 병합 방법</span><span class="sxs-lookup"><span data-stu-id="2f3e9-222">How role capabilities are merged</span></span>

<span data-ttu-id="2f3e9-223">JEA 세션을 입력할 때 [세션 구성 파일](session-configurations.md)의 일치하는 모든 역할 기능에 대한 액세스 권한이 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-223">Users are granted access to all matching role capabilities in the [session configuration file](session-configurations.md) when they enter a JEA session.</span></span> <span data-ttu-id="2f3e9-224">JEA는 모든 역할에서 허용되는 가장 허용적인 명령 세트를 사용자에게 제공하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-224">JEA tries to give the user the most permissive set of commands allowed by any of the roles.</span></span>

### <a name="visiblecmdlets-and-visiblefunctions"></a><span data-ttu-id="2f3e9-225">VisibleCmdlets 및 VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="2f3e9-225">VisibleCmdlets and VisibleFunctions</span></span>

<span data-ttu-id="2f3e9-226">가장 복잡한 병합 논리는 JEA에서 제한된 매개 변수 및 매개 변수 값을 가질 수 있는 cmdlet 및 함수에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-226">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="2f3e9-227">규칙은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-227">The rules are as follows:</span></span>

1. <span data-ttu-id="2f3e9-228">cmdlet이 한 역할에서만 표시되도록 설정된 경우 적용 가능한 모든 매개 변수 제약 조건이 적용된 상태로 사용자에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-228">If a cmdlet is only made visible in one role, it is visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="2f3e9-229">cmdlet이 둘 이상의 역할에서 표시되도록 설정된 경우 각 역할의 cmdlet에 대한 제약 조건이 같으면 cmdlet은 해당 제약 조건이 적용된 상태로 사용자에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-229">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet is visible to the user with those constraints.</span></span>
3. <span data-ttu-id="2f3e9-230">cmdlet이 둘 이상의 역할로 표시되고 각 역할에서 서로 다른 매개 변수 세트를 허용하는 경우, cmdlet 및 모든 역할에서 정의된 모든 매개 변수가 사용자에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-230">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all the parameters defined across every role are visible to the user.</span></span>
   <span data-ttu-id="2f3e9-231">한 역할에 매개 변수에 대한 제약 조건이 없는 경우 모든 매개 변수가 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-231">If one role doesn't have constraints on the parameters, all parameters are allowed.</span></span>
4. <span data-ttu-id="2f3e9-232">한 역할은 cmdlet 매개 변수에 대한 유효성 검사 집합 또는 유효성 검사 패턴을 정의하고 다른 역할은 매개 변수를 허용하지만 매개 변수 값을 제한하지 않는 경우 유효성 검사 집합 또는 패턴이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-232">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern is ignored.</span></span>
5. <span data-ttu-id="2f3e9-233">유효성 검사 집합이 둘 이상의 역할에서 같은 cmdlet 매개 변수에 대해 정의된 경우 모든 유효성 검사 집합의 모든 값이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-233">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets are allowed.</span></span>
6. <span data-ttu-id="2f3e9-234">유효성 검사 패턴이 둘 이상의 역할에서 같은 cmdlet 매개 변수에 대해 정의된 경우 임의 패턴과 일치하는 모든 값이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-234">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns are allowed.</span></span>
7. <span data-ttu-id="2f3e9-235">유효성 검사 집합이 하나 이상의 역할에서 정의된 경우 같은 cmdlet 매개 변수에 대한 다른 역할에 유효성 검사 패턴이 정의되어 있으면 유효성 검사 집합이 무시되고 나머지 유효성 검사 패턴에는 규칙 (6)이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-235">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="2f3e9-236">다음은 이러한 규칙에 따라 역할이 병합되는 방식의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-236">Below is an example of how roles are merged according to these rules:</span></span>

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service
#   is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use
#   ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

### <a name="visibleexternalcommands-visiblealiases-visibleproviders-scriptstoprocess"></a><span data-ttu-id="2f3e9-237">VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="2f3e9-237">VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess</span></span>

<span data-ttu-id="2f3e9-238">역할 기능 파일의 다른 모든 필드는 허용되는 외부 명령, 별칭, 공급자 및 시작 스크립트의 누적 집합에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-238">All other fields in the role capability file are added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span> <span data-ttu-id="2f3e9-239">한 역할에서 사용할 수 있는 모든 명령, 별칭, 공급자 또는 스크립트는 JEA 사용자에게 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-239">Any command, alias, provider, or script available in one role capability is available to the JEA user.</span></span>

<span data-ttu-id="2f3e9-240">한 역할 기능의 공급자와 다른 역할 기능의 cmdlet/함수/명령이 결합된 집합에서 사용자가 시스템 리소스에 의도치 않게 액세스할 수 있게 하지 않도록 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-240">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another don't allow users unintentional access to system resources.</span></span>
<span data-ttu-id="2f3e9-241">예를 들어 한 역할에서 `Remove-Item` cmdlet을 허용하고 다른 역할에서 `FileSystem` 공급자를 허용하는 경우 JEA 사용자가 컴퓨터의 임의 파일을 삭제할 수 있는 위험이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-241">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span> <span data-ttu-id="2f3e9-242">사용자의 유효 권한을 식별하는 방법에 대한 자세한 내용은 [JEA 감사](audit-and-report.md) 문서에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f3e9-242">Additional information about identifying users' effective permissions can be found in the [auditing JEA](audit-and-report.md) article.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2f3e9-243">다음 단계</span><span class="sxs-lookup"><span data-stu-id="2f3e9-243">Next steps</span></span>

[<span data-ttu-id="2f3e9-244">세션 구성 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="2f3e9-244">Create a session configuration file</span></span>](session-configurations.md)
