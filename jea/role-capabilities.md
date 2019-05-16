---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: JEA 역할 기능
ms.openlocfilehash: 528b41c0e2ffdcfed3251fb0f714c649e7290761
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229559"
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="c0d74-103">JEA 역할 기능</span><span class="sxs-lookup"><span data-stu-id="c0d74-103">JEA Role Capabilities</span></span>

> <span data-ttu-id="c0d74-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="c0d74-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="c0d74-105">JEA 엔드포인트를 만들 때 사용자가 JEA 세션에서 수행할 수 있는 *작업*을 설명하는 하나 이상의 "역할 기능"을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-105">When creating a JEA endpoint, you will need to define one or more "role capabilities" which describe *what* someone can do in a JEA session.</span></span>
<span data-ttu-id="c0d74-106">역할 기능은 연결하는 사용자에게 제공되어야 하는 모든 cmdlet, 함수, 공급자 및 외부 프로그램을 나열하는 PowerShell 데이터 파일로서 확장명은 .psrc입니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-106">A role capability is a PowerShell data file with the .psrc extension that lists all the cmdlets, functions, providers, and external programs that should be made available to connecting users.</span></span>

<span data-ttu-id="c0d74-107">이 항목에서는 JEA 사용자에 대한 PowerShell 역할 기능 파일을 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-107">This topic describes how to create a PowerShell role capability file for your JEA users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="c0d74-108">허용할 명령 결정</span><span class="sxs-lookup"><span data-stu-id="c0d74-108">Determine which commands to allow</span></span>

<span data-ttu-id="c0d74-109">역할 기능 파일을 만들 때 첫 번째 단계는 역할이 할당된 사용자에게 무엇에 대한 액세스 권한이 필요한지를 고려하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-109">The first step when creating a role capability file is to consider what the users who are assigned the role will need access to.</span></span>
<span data-ttu-id="c0d74-110">이 요구 사항 수집 프로세스는 시간이 약간 걸릴 수 있지만, 매우 중요한 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-110">This requirements gathering process can take a while, but it is a very important process.</span></span>
<span data-ttu-id="c0d74-111">사용자에게 너무 적은 cmdlet 및 함수에 대한 액세스 권한을 부여하면 사용자가 작업을 수행하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-111">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span>
<span data-ttu-id="c0d74-112">너무 많은 cmdlet 및 함수에 대한 액세스를 허용하면 사용자가 해당 암시적 관리자 권한으로 의도한 것보다 많은 작업을 수행할 수 있게 되어 보안이 약화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-112">Allowing access to too many cmdlets and functions can lead to users doing more than you intended with their implicit admin privileges, weakening your security stance.</span></span>

<span data-ttu-id="c0d74-113">이 프로세스를 어떻게 시작할지는 조직 및 목표에 따라 다르지만, 다음 팁을 참조하면 올바르게 진행하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-113">How you go about this process will depend on your organization and goals, however the following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="c0d74-114">**식별**: 사용자가 작업을 수행하는 데 사용하는 명령을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-114">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="c0d74-115">이 과정에는 IT 직원을 대상으로 설문 조사를 진행하거나 자동화 스크립트를 확인하거나 PowerShell 세션 기록 또는 로그를 분석하는 작업이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-115">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts or logs.</span></span>
2. <span data-ttu-id="c0d74-116">**업데이트**: 최상의 감사 및 JEA 사용자 지정 환경을 위해 가능한 경우 명령줄 도구 사용을 같은 기능을 가진 PowerShell로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-116">**Update** use of command line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="c0d74-117">외부 프로그램은 JEA에서 기본 PowerShell cmdlet 및 함수만큼 세부적으로 제한할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-117">External programs cannot be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="c0d74-118">**제한**: 특정 매개 변수 또는 매개 변수 값만 허용해야 할 경우 cmdlet의 범위를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-118">**Restrict** the scope of the cmdlets if necessary to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="c0d74-119">이는 사용자가 시스템의 일부만 관리할 수 있어야 하는 경우에 특히 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-119">This is particularly important if users should only be able to manage part of a system.</span></span>
4. <span data-ttu-id="c0d74-120">**만들기**: 복잡한 명령이나 JEA에서 제한하기 어려운 명령을 대체할 사용자 지정 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-120">**Create** custom functions to replace complex commands or commands which are difficult to constrain in JEA.</span></span> <span data-ttu-id="c0d74-121">복잡한 명령을 래핑하거나 추가 유효성 검사 논리를 적용하는 간단한 함수는 관리자 및 최종 사용자의 편의를 위한 추가 제어를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-121">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="c0d74-122">**테스트**: 사용자 및/또는 자동화 서비스로 허용되는 명령의 범위가 지정된 목록을 테스트하고 필요에 따라 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-122">**Test** the scoped list of allowable commands with your users and/or automation services and adjust as necessary.</span></span>

<span data-ttu-id="c0d74-123">JEA 세션의 명령은 일반적으로 관리자(또는 상승된) 권한으로 실행된다는 사실을 기억해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-123">It is important to remember that commands in a JEA session are often run with admin (or otherwise elevated) privileges.</span></span>
<span data-ttu-id="c0d74-124">사용할 수 있는 명령을 신중하게 선택해야 JEA 엔드포인트가 연결하는 사용자가 권한을 상승시킬 수 없도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-124">Careful selection of available commands is important to ensure the JEA endpoint does not allow the connecting user to elevate their permissions.</span></span>
<span data-ttu-id="c0d74-125">다음은 비제한 상태에서 허용되는 경우 악의적으로 사용될 수 있는 명령의 몇 가지 예입니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-125">Below are some examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span>
<span data-ttu-id="c0d74-126">이 목록은 전체 목록이 아니며 경고성 시작 지점으로만 사용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-126">Note that this is not an exhaustive list and should only be used as a cautionary starting point.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="c0d74-127">잠재적으로 위험한 명령의 예</span><span class="sxs-lookup"><span data-stu-id="c0d74-127">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="c0d74-128">위험</span><span class="sxs-lookup"><span data-stu-id="c0d74-128">Risk</span></span> | <span data-ttu-id="c0d74-129">예제</span><span class="sxs-lookup"><span data-stu-id="c0d74-129">Example</span></span> | <span data-ttu-id="c0d74-130">관련 명령</span><span class="sxs-lookup"><span data-stu-id="c0d74-130">Related commands</span></span>
-----|---------|-----------------
<span data-ttu-id="c0d74-131">연결하는 사용자에게 JEA를 바이패스할 수 있는 관리자 권한 부여</span><span class="sxs-lookup"><span data-stu-id="c0d74-131">Granting the connecting user admin privileges to bypass JEA</span></span> | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="c0d74-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="c0d74-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>
<span data-ttu-id="c0d74-133">맬웨어, 익스플로잇 또는 보호를 바이패스하는 사용자 지정 스크립트와 같은 임의의 코드 실행</span><span class="sxs-lookup"><span data-stu-id="c0d74-133">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'` | <span data-ttu-id="c0d74-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="c0d74-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span>

## <a name="create-a-role-capability-file"></a><span data-ttu-id="c0d74-135">역할 기능 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="c0d74-135">Create a role capability file</span></span>

<span data-ttu-id="c0d74-136">[New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet을 사용하여 새 PowerShell 역할 기능 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-136">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="c0d74-137">결과 역할 기능 파일을 텍스트 편집기에서 열어 역할에 대해 원하는 명령을 허용하도록 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-137">The resulting role capability file can be opened in a text editor and modified to allow the desired commands for the role.</span></span>
<span data-ttu-id="c0d74-138">PowerShell 도움말 문서에는 파일을 구성하는 방법의 몇 가지 예제가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-138">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="c0d74-139">PowerShell cmdlet 및 함수 허용</span><span class="sxs-lookup"><span data-stu-id="c0d74-139">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="c0d74-140">사용자에게 PowerShell cmdlet 또는 함수를 실행할 수 있는 권한을 부여하려면 VisibleCmdlets 또는 VisibleFunctions 필드에 cmdlet 또는 함수 이름을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-140">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisibleCmdlets or VisibleFunctions fields.</span></span>
<span data-ttu-id="c0d74-141">명령이 cmdlet인지 또는 함수인지 확실하지 않은 경우 `Get-Command <name>`을 실행하고 출력에서 "CommandType" 속성을 확인하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-141">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the "CommandType" property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="c0d74-142">때때로 특정 cmdlet 또는 함수의 범위는 사용자의 요구 사항보다 너무 광범위합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-142">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span>
<span data-ttu-id="c0d74-143">예를 들어 DNS 관리자는 DNS 서비스를 다시 시작할 수 있는 권한만 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-143">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span>
<span data-ttu-id="c0d74-144">테넌트에 셀프 서비스 관리 도구에 대한 액세스 권한이 부여되는 다중 테넌트 환경에서 테넌트는 해당 리소스 관리로만 제한되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-144">In a multi-tenant environment where tenants are granted access to self-service management tools, tenants should be limited to managing with their own resources.</span></span>
<span data-ttu-id="c0d74-145">이러한 경우 cmdlet 또는 함수에서 노출되는 매개 변수를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

<span data-ttu-id="c0d74-146">고급 시나리오에서는 사용자가 이러한 매개 변수에 제공할 수 있는 값을 제한해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-146">In more advanced scenarios, you may also need to restrict which values someone can supply to these parameters.</span></span>
<span data-ttu-id="c0d74-147">역할 기능을 사용하면 지정된 입력이 허용되는지를 결정하기 위해 평가되는 정규식 패턴이나 허용되는 값 집합을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-147">Role capabilities let you define a set of allowed values or a regular expression pattern that is evaluated to determine if a given input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="c0d74-148">[common PowerShell parameters](https://technet.microsoft.com/library/hh847884.aspx)(일반적인 PowerShell 매개 변수)는 사용할 수 있는 매개 변수를 제한하는 경우에도 항상 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-148">The [common PowerShell parameters](https://technet.microsoft.com/library/hh847884.aspx) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="c0d74-149">그러나 Parameters 필드에 해당 매개 변수를 명시적으로 나열해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="c0d74-150">아래 표에는 표시되는 cmdlet 또는 함수를 사용자 지정할 수 있는 다양한 방법이 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="c0d74-151">VisibleCmdlets 필드에 아래의 cmdlet 또는 함수를 원하는 대로 조합해서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-151">You can mix and match any of the below in the VisibleCmdlets field.</span></span>

<span data-ttu-id="c0d74-152">예제</span><span class="sxs-lookup"><span data-stu-id="c0d74-152">Example</span></span>                                                                                      | <span data-ttu-id="c0d74-153">사용 사례</span><span class="sxs-lookup"><span data-stu-id="c0d74-153">Use case</span></span>
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="c0d74-154">`'My-Func'` 또는 `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="c0d74-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                       | <span data-ttu-id="c0d74-155">사용자는 매개 변수에 대한 제한 없이 `My-Func`를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>
`'MyModule\My-Func'`                                                                         | <span data-ttu-id="c0d74-156">사용자는 매개 변수에 대한 제한 없이 `MyModule` 모듈에서 `My-Func`를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>
`'My-*'`                                                                                     | <span data-ttu-id="c0d74-157">사용자는 동사 `My`가 포함된 모든 cmdlet 또는 함수를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>
`'*-Func'`                                                                                   | <span data-ttu-id="c0d74-158">사용자는 명사 `Func`가 포함된 모든 cmdlet 또는 함수를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | <span data-ttu-id="c0d74-159">사용자는 `Param1` 및/또는 `Param2` 매개 변수를 사용하여 `My-Func`를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-159">Allows the user to run `My-Func` with the `Param1` and/or `Param2` parameters.</span></span> <span data-ttu-id="c0d74-160">매개 변수에 아무 값이나 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-160">Any value can be supplied to the parameters.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | <span data-ttu-id="c0d74-161">사용자는 `Param1` 매개 변수를 사용하여 `My-Func`를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="c0d74-162">매개 변수에 "Value1" 및 "Value2"만 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | <span data-ttu-id="c0d74-163">사용자는 `Param1` 매개 변수를 사용하여 `My-Func`를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="c0d74-164">매개 변수에 "contoso"로 시작하는 모든 값을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-164">Any value starting with "contoso" can be supplied to the parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="c0d74-165">최상의 보안 방식을 위해 표시되는 cmdlet 또는 함수를 정의할 때 와일드카드는 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span>
> <span data-ttu-id="c0d74-166">대신 신뢰할 수 있는 각 명령을 명시적으로 나열하여 같은 이름 지정 체계를 공유하는 다른 명령에 의도치 않게 권한이 부여되지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="c0d74-167">같은 cmdlet 또는 함수에 ValidatePattern과 ValidateSet를 둘 다 적용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-167">You cannot apply both a ValidatePattern and ValidateSet to the same cmdlet or function.</span></span>

<span data-ttu-id="c0d74-168">둘 다 적용할 경우 ValidatePattern이 ValidateSet를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-168">If you do, the ValidatePattern will override the ValidateSet.</span></span>

<span data-ttu-id="c0d74-169">ValidatePattern에 대한 자세한 내용은 [이 *Hey, Scripting Guy!* 게시물](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) 및 [PowerShell 정규식](https://technet.microsoft.com/library/hh847880.aspx) 참조 콘텐츠를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="c0d74-169">For more information about ValidatePattern, check out [this *Hey, Scripting Guy!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](https://technet.microsoft.com/library/hh847880.aspx) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="c0d74-170">외부 명령 및 PowerShell 스크립트 허용</span><span class="sxs-lookup"><span data-stu-id="c0d74-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="c0d74-171">사용자가 JEA 세션에서 실행 파일 및 PowerShell 스크립트(.ps1)를 실행할 수 있게 하려면 VisibleExternalCommands 필드에 각 프로그램의 전체 경로를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the VisibleExternalCommands field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="c0d74-172">PowerShell cmdlet/함수에서 허용되는 매개 변수를 제어하는 것은 관리자이므로, 가능한 경우 권한을 부여하는 외부 실행 파일과 같은 기능을 가진 PowerShell cmdlet/함수를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-172">It is advised, where possible, to use PowerShell cmdlet/function equivalents of any external executables you authorize since you have control over which parameters are allowed with PowerShell cmdlets/functions.</span></span>

<span data-ttu-id="c0d74-173">많은 실행 파일은 현재 상태를 읽은 다음 다른 매개 변수를 제공하는 것만으로 현재 상태를 변경할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-173">Many executables allow you to both read the current state and then change it just by providing different parameters.</span></span>

<span data-ttu-id="c0d74-174">예를 들어 로컬 컴퓨터에서 호스트되는 네트워크 공유를 확인하려는 파일 서버 관리자의 역할을 생각해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-174">For example, consider the role of a file server admin who wants to check which network shares are hosted by the local machine.</span></span>
<span data-ttu-id="c0d74-175">확인하는 한 가지 방법은 `net share`를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-175">One way to check is to use `net share`.</span></span>
<span data-ttu-id="c0d74-176">그러나 관리자가 `net group Administrators unprivilegedjeauser /add`로 관리자 권한을 얻는 명령을 쉽게 사용할 수 있으므로 net.exe를 허용하는 것은 매우 위험합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-176">However, allowing net.exe is very dangerous because the admin could just as easily use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span>
<span data-ttu-id="c0d74-177">같은 결과를 생성하지만 훨씬 더 제한된 범위를 가지는 [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx)를 허용하는 것이 더 낫습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-177">A better approach is to allow [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="c0d74-178">JEA 세션에서 외부 명령을 사용자가 사용할 수 있도록 할 때 항상 실행 파일의 전체 경로를 지정하여 시스템의 다른 위치에 있는 유사한 이름(그리고 잠재적으로 악성)의 프로그램이 대신 실행되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-178">When making external commands available to users in a JEA session, always specify the complete path to the executable to ensure a similarly named (and potentially malicious) program placed elsewhere on the system does not get executed instead.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="c0d74-179">PowerShell 공급자에 대한 액세스 허용</span><span class="sxs-lookup"><span data-stu-id="c0d74-179">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="c0d74-180">기본적으로 JEA 세션에서는 PowerShell 공급자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-180">By default, no PowerShell providers are available in JEA sessions.</span></span>

<span data-ttu-id="c0d74-181">이렇게 하는 이유는 기본적으로 중요 정보 및 구성 설정이 연결하는 사용자에게 공개되는 위험을 줄이기 위함입니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-181">This is primarily to reduce the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="c0d74-182">필요한 경우 `VisibleProviders` 명령을 사용하여 PowerShell 공급자에 대한 액세스를 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-182">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span>
<span data-ttu-id="c0d74-183">전체 공급자 목록을 보려면 `Get-PSProvider`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-183">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="c0d74-184">파일 시스템, 레지스트리, 인증서 저장소 또는 기타 중요 공급자에 액세스해야 하는 간단한 작업의 경우 사용자를 대신하여 공급자와 작동하는 사용자 지정 함수 작성을 고려할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-184">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, you can also consider writing a custom function that works with the provider on the user's behalf.</span></span>
<span data-ttu-id="c0d74-185">JEA 세션에서 사용할 수 있는 함수, cmdlet 및 외부 프로그램은 JEA와 같은 제약 조건이 적용되지 않으며 기본적으로 모든 공급자에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-185">Functions, cmdlets, and external programs that are available in a JEA session are not subject to the same constraints as JEA -- they can access any provider by default.</span></span>
<span data-ttu-id="c0d74-186">또한 JEA 엔드포인트로/에서 파일을 복사해야 할 경우 [사용자 드라이브](session-configurations.md#user-drive) 사용을 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="c0d74-186">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to/from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="c0d74-187">사용자 지정 함수 만들기</span><span class="sxs-lookup"><span data-stu-id="c0d74-187">Creating custom functions</span></span>

<span data-ttu-id="c0d74-188">역할 기능 파일에서 사용자 지정 함수를 작성하여 최종 사용자에 대한 복잡한 작업을 간소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-188">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span>
<span data-ttu-id="c0d74-189">사용자 지정 함수는 cmdlet 매개 변수 값에 대한 고급 유효성 검사 논리가 필요한 경우에도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-189">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span>
<span data-ttu-id="c0d74-190">**FunctionDefinitions** 필드에서 간단한 함수를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-190">You can write simple functions in the **FunctionDefinitions** field:</span></span>

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="c0d74-191">JEA 사용자가 사용자 지정 함수를 실행할 수 있도록 사용자 지정 함수의 이름을 **VisibleFunctions** 필드에 잊지 말고 추가하세요.</span><span class="sxs-lookup"><span data-stu-id="c0d74-191">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>

<span data-ttu-id="c0d74-192">사용자 지정 함수의 본문(스크립트 블록)은 시스템에 대한 기본 언어 모드에서 실행되며 JEA의 언어 제약 조건이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-192">The body (script block) of custom functions runs in the default language mode for the system and is not subject to JEA's language constraints.</span></span>
<span data-ttu-id="c0d74-193">즉, 함수는 파일 시스템 및 레지스트리에 액세스하고 역할 기능 파일에 표시되도록 설정되지 않은 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-193">This means that functions can access the file system and registry, and run commands that were not made visible in the role capability file.</span></span>
<span data-ttu-id="c0d74-194">매개 변수를 사용할 때 임의의 코드 실행을 허용하지 않도록 주의하고 `Invoke-Expression`과 같은 cmdlet에 사용자 입력을 직접 파이프하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-194">Take care to avoid allowing arbitrary code to be run when using parameters and avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="c0d74-195">위 예제에서 축약형 `Select-Object` 대신 FQMN(정규화된 모듈 이름) `Microsoft.PowerShell.Utility\Select-Object`가 사용된 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-195">In the above example, you will notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="c0d74-196">역할 기능 파일에 정의된 함수에는 여전히 JEA 세션의 범위가 적용되며 여기에는 JEA가 기존 명령을 제한하기 위해 만드는 프록시 함수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-196">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="c0d74-197">Select-Object는 개체에 대한 임의 속성을 선택할 수 없게 하는, 모든 JEA 세션의 기본, 제한된 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-197">Select-Object is a default, constrained cmdlet in all JEA sessions that doesn't allow you to select arbitrary properties on objects.</span></span>
<span data-ttu-id="c0d74-198">함수에서 비제한 Select-Object를 사용하려면 FQMN을 지정하여 전체 구현을 명시적으로 요청해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-198">To use the unconstrained Select-Object in functions, you must explicitly request the full implementation by specifying the FQMN.</span></span>
<span data-ttu-id="c0d74-199">JEA 세션에서 제한된 모든 cmdlet은 함수에서 호출될 때 PowerShell의 [command precedence](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence)(명령 우선 순위)와 같은 동작을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-199">Any constrained cmdlet in a JEA session will exhibit the same behavior when invoked from a function, in line with PowerShell's [command precedence](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="c0d74-200">많은 사용자 지정 함수를 작성하는 경우 사용자 지정 함수를 [PowerShell Script Module](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx)(PowerShell 스크립트 모듈)에 배치하는 것이 더 쉬울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-200">If you are writing a lot of custom functions, it may be easier to put them in a [PowerShell Script Module](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).</span></span>
<span data-ttu-id="c0d74-201">그런 다음 기본 제공 및 타사 모듈을 사용할 때처럼 VisibleFunctions 필드를 사용하여 JEA 세션에 해당 함수를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-201">You can then make those functions visible in the JEA session using the VisibleFunctions field like you would with built-in and third party modules.</span></span>

<span data-ttu-id="c0d74-202">JEA 세션에서 탭 완료가 제대로 작동하려면 **VisibleFunctions** 목록에 기본 제공 함수 `tabexpansion2`를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-202">For tab completion to work properly in JEA sessions you must include the built-in function `tabexpansion2` in the **VisibleFunctions** list.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="c0d74-203">모듈에 역할 기능 배치</span><span class="sxs-lookup"><span data-stu-id="c0d74-203">Place role capabilities in a module</span></span>

<span data-ttu-id="c0d74-204">PowerShell에서 역할 기능 파일을 찾도록 하려면 역할 기능 파일을 PowerShell 모듈의 "RoleCapabilities" 폴더에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-204">In order for PowerShell to find a role capability file, it must be stored in a "RoleCapabilities" folder in a PowerShell module.</span></span>
<span data-ttu-id="c0d74-205">모듈은 `$env:PSModulePath` 환경 변수에 포함된 모든 폴더에 저장할 수 있지만, System32(기본 제공 모듈용으로 예약됨) 또는 신뢰할 수 없는 연결하는 사용자가 파일을 수정할 수 있는 폴더에 배치해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-205">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you should not place it in System32 (reserved for built-in modules) or a folder where the untrusted, connecting users could modify the files.</span></span>
<span data-ttu-id="c0d74-206">다음은 "Program Files" 경로에 *ContosoJEA*라는 기본 PowerShell 스크립트 모듈을 만드는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-206">Below is an example of creating a basic PowerShell script module called *ContosoJEA* in the "Program Files" path.</span></span>

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

<span data-ttu-id="c0d74-207">PowerShell 모듈, 모듈 매니페스트 및 PSModulePath 환경 변수에 대한 자세한 내용은 [Understanding a PowerShell Module](https://msdn.microsoft.com/library/dd878324.aspx)(PowerShell 모듈 이해)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0d74-207">See [Understanding a PowerShell Module](https://msdn.microsoft.com/library/dd878324.aspx) for more information about PowerShell modules, module manifests, and the PSModulePath environment variable.</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="c0d74-208">역할 기능 업데이트</span><span class="sxs-lookup"><span data-stu-id="c0d74-208">Updating role capabilities</span></span>

<span data-ttu-id="c0d74-209">역할 기능 파일에 변경 내용을 저장하여 언제든지 역할 기능 파일을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-209">You can update a role capability file at any time by simply saving changes to the role capability file.</span></span>
<span data-ttu-id="c0d74-210">역할 기능이 업데이트된 후 시작되는 모든 새 JEA 세션은 수정된 기능을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-210">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="c0d74-211">그러므로 역할 기능 폴더에 대한 액세스를 제어하는 것은 매우 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-211">This is why controlling access to the role capabilities folder is so important.</span></span>
<span data-ttu-id="c0d74-212">매우 신뢰할 수 있는 관리자만 역할 기능 파일을 변경할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-212">Only highly trusted administrators should be able to change role capability files.</span></span>
<span data-ttu-id="c0d74-213">신뢰할 수 없는 사용자가 역할 기능 파일을 변경할 수 있는 경우 자신의 권한을 상승시킬 수 있는 cmdlet에 대한 액세스 권한을 자신에게 손쉽게 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-213">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets which allow them to elevate their privileges.</span></span>

<span data-ttu-id="c0d74-214">역할 기능에 대한 액세스를 제한하려는 관리자의 경우 로컬 시스템에 역할 기능 파일 및 포함하는 모듈에 대한 읽기 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-214">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="c0d74-215">역할 기능 병합 방법</span><span class="sxs-lookup"><span data-stu-id="c0d74-215">How role capabilities are merged</span></span>

<span data-ttu-id="c0d74-216">사용자는 [세션 구성 파일](session-configurations.md)의 역할 매핑에 따라 JEA 세션에 들어갈 때 여러 역할 기능에 대한 액세스 권한을 부여받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-216">Users can be granted access to multiple role capabilities when they enter a JEA session depending on the role mappings in the [session configuration file](session-configurations.md).</span></span>
<span data-ttu-id="c0d74-217">이 경우 JEA에서는 사용자에게 모든 역할에서 허용하는 *최대로 허용되는* 명령 집합을 제공하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-217">When this happens, JEA tries to give the user the *most permissive* set of commands allowed by any of the roles.</span></span>

<span data-ttu-id="c0d74-218">**VisibleCmdlets 및 VisibleFunctions**</span><span class="sxs-lookup"><span data-stu-id="c0d74-218">**VisibleCmdlets and VisibleFunctions**</span></span>

<span data-ttu-id="c0d74-219">가장 복잡한 병합 논리는 JEA에서 제한된 매개 변수 및 매개 변수 값을 가질 수 있는 cmdlet 및 함수에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-219">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="c0d74-220">규칙은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-220">The rules are as follows:</span></span>

1. <span data-ttu-id="c0d74-221">cmdlet이 한 역할에서만 표시되도록 설정된 경우 적용 가능한 모든 매개 변수 제약 조건이 적용된 상태로 사용자에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-221">If a cmdlet is only made visible in one role, it will be visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="c0d74-222">cmdlet이 둘 이상의 역할에서 표시되도록 설정된 경우 각 역할의 cmdlet에 대한 제약 조건이 같으면 cmdlet은 해당 제약 조건이 적용된 상태로 사용자에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-222">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet will be visible to the user with those constraints.</span></span>
3. <span data-ttu-id="c0d74-223">cmdlet이 둘 이상의 역할에서 표시되도록 설정된 경우 각 역할에서 서로 다른 매개 변수 집합을 허용하면 cmdlet 및 모든 역할에서 정의된 모든 매개 변수가 사용자에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-223">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all of the parameters defined across every role will be visible to the user.</span></span> <span data-ttu-id="c0d74-224">한 역할에 매개 변수에 대한 제약 조건이 없는 경우 모든 매개 변수가 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-224">If one role doesn't have constraints on the parameters, all parameters will be allowed.</span></span>
4. <span data-ttu-id="c0d74-225">한 역할은 cmdlet 매개 변수에 대한 유효성 검사 집합 또는 유효성 검사 패턴을 정의하고 다른 역할은 매개 변수를 허용하지만 매개 변수 값을 제한하지 않는 경우 유효성 검사 집합 또는 패턴이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-225">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern will be ignored.</span></span>
5. <span data-ttu-id="c0d74-226">유효성 검사 집합이 둘 이상의 역할에서 같은 cmdlet 매개 변수에 대해 정의된 경우 모든 유효성 검사 집합의 모든 값이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-226">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets will be allowed.</span></span>
6. <span data-ttu-id="c0d74-227">유효성 검사 패턴이 둘 이상의 역할에서 같은 cmdlet 매개 변수에 대해 정의된 경우 임의 패턴과 일치하는 모든 값이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-227">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns will be allowed.</span></span>
7. <span data-ttu-id="c0d74-228">유효성 검사 집합이 하나 이상의 역할에서 정의된 경우 같은 cmdlet 매개 변수에 대한 다른 역할에 유효성 검사 패턴이 정의되어 있으면 유효성 검사 집합이 무시되고 나머지 유효성 검사 패턴에는 규칙 (6)이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-228">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="c0d74-229">다음은 이러한 규칙에 따라 역할이 병합되는 방식의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-229">Below is an example of how roles are merged according to these rules:</span></span>

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

<span data-ttu-id="c0d74-230">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span><span class="sxs-lookup"><span data-stu-id="c0d74-230">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span></span>

<span data-ttu-id="c0d74-231">역할 기능 파일의 다른 모든 필드는 허용되는 외부 명령, 별칭, 공급자 및 시작 스크립트의 누적 집합에 그냥 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-231">All other fields in the role capability file are simply added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span>
<span data-ttu-id="c0d74-232">한 역할에서 사용할 수 있는 모든 명령, 별칭, 공급자 또는 스크립트는 JEA 사용자에게 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-232">Any command, alias, provider, or script available in one role capability will be available to the JEA user.</span></span>

<span data-ttu-id="c0d74-233">한 역할 기능의 공급자와 다른 역할 기능의 cmdlet/함수/명령이 결합된 집합이 연결하는 사용자가 시스템 리소스에 의도치 않게 액세스할 수 있게 하지 않도록 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-233">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another do not allow connecting users unintentional access to system resources.</span></span>
<span data-ttu-id="c0d74-234">예를 들어 한 역할에서 `Remove-Item` cmdlet을 허용하고 다른 역할에서 `FileSystem` 공급자를 허용하는 경우 JEA 사용자가 컴퓨터의 임의 파일을 삭제할 수 있는 위험이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-234">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span>
<span data-ttu-id="c0d74-235">사용자의 유효 권한을 식별하는 방법에 대한 자세한 내용은 [JEA 감사 항목](audit-and-report.md)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d74-235">Additional information about identifying users' effective permissions can be found in the [auditing JEA topic](audit-and-report.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c0d74-236">다음 단계</span><span class="sxs-lookup"><span data-stu-id="c0d74-236">Next steps</span></span>

- [<span data-ttu-id="c0d74-237">세션 구성 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="c0d74-237">Create a session configuration file</span></span>](session-configurations.md)
