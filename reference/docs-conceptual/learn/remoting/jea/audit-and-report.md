---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: JEA에 대한 감사 및 보고
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017794"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="635b4-103">JEA에 대한 감사 및 보고</span><span class="sxs-lookup"><span data-stu-id="635b4-103">Auditing and Reporting on JEA</span></span>

<span data-ttu-id="635b4-104">JEA를 배포한 후에는 정기적으로 JEA 구성을 감사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-104">After you've deployed JEA, you need to regularly audit the JEA configuration.</span></span> <span data-ttu-id="635b4-105">감사를 통해 올바른 사용자에게 JEA 엔드포인트에 대한 액세스 권한이 있는지와 할당된 해당 역할이 여전히 적절한지를 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-105">Auditing helps you assess that the correct people have access to the JEA endpoint and their assigned roles are still appropriate.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="635b4-106">컴퓨터에서 등록된 JEA 세션 찾기</span><span class="sxs-lookup"><span data-stu-id="635b4-106">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="635b4-107">컴퓨터에 등록된 JEA 세션을 확인하려면 [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-107">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="635b4-108">엔드포인트에 대한 유효 권한은 **Permission** 속성에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-108">The effective rights for the endpoint are listed in the **Permission** property.</span></span> <span data-ttu-id="635b4-109">이러한 사용자는 JEA 엔드포인트에 연결할 수 있는 권한을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-109">These users have the right to connect to the JEA endpoint.</span></span> <span data-ttu-id="635b4-110">그러나 액세스 권한이 있는 역할과 명령은 엔드포인트를 등록하는 데 사용된 [세션 구성 파일](session-configurations.md)의 **RoleDefinitions** 속성에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-110">However, the roles and commands they have access to is determined by the **RoleDefinitions** property in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span> <span data-ttu-id="635b4-111">**RoleDefinitions** 속성을 확장하여 등록된 JEA 엔드포인트의 역할 매핑을 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-111">Expand the **RoleDefinitions** property to evaluate the role mappings in a registered JEA endpoint.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="635b4-112">컴퓨터에서 사용 가능한 역할 기능 찾기</span><span class="sxs-lookup"><span data-stu-id="635b4-112">Find available role capabilities on the machine</span></span>

<span data-ttu-id="635b4-113">JEA는 PowerShell 모듈 내의 **RoleCapabilities** 폴더에 저장된 `.psrc` 파일에서 역할 기능을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-113">JEA gets role capabilities from the `.psrc` files stored in the **RoleCapabilities** folder inside a PowerShell module.</span></span> <span data-ttu-id="635b4-114">다음 함수는 컴퓨터에서 사용할 수 있는 모든 역할 기능을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-114">The following function finds all role capabilities available on a computer.</span></span>

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="635b4-115">여러 역할 기능에서 같은 이름을 공유하는 경우 이 함수의 결과 순서가 반드시 역할 기능이 선택된 순서인 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-115">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="635b4-116">특정 사용자에 대한 유효 권한 확인</span><span class="sxs-lookup"><span data-stu-id="635b4-116">Check effective rights for a specific user</span></span>

<span data-ttu-id="635b4-117">[Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet은 사용자의 그룹 멤버 자격에 따라 JEA 엔드포인트에서 사용할 수 있는 모든 명령을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-117">The [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumerates all the commands available on a JEA endpoint based on a user's group memberships.</span></span>
<span data-ttu-id="635b4-118">`Get-PSSessionCapability`의 출력은 JEA 세션에서 `Get-Command -CommandType All`을 실행하는 지정된 사용자의 출력과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-118">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="635b4-119">사용자가 추가 JEA 권한을 부여하는 그룹의 영구 구성원이 아닌 경우 이 cmdlet은 이러한 추가 권한을 반영하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-119">If your users aren't permanent members of groups that would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span> <span data-ttu-id="635b4-120">이는 사용자가 보안 그룹에 일시적으로 속할 수 있도록 Just-In-Time 권한 있는 액세스 관리 시스템을 사용할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-120">This happens when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span> <span data-ttu-id="635b4-121">사용자가 해당 작업을 성공적으로 수행하는 데 필요한 액세스 수준만 가져올 수 있도록 역할 및 기능에 대한 사용자 매핑을 신중하게 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-121">Carefully evaluate the mapping of users to roles and capabilities to ensure that users only get the level of access needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="635b4-122">PowerShell 이벤트 로그</span><span class="sxs-lookup"><span data-stu-id="635b4-122">PowerShell event logs</span></span>

<span data-ttu-id="635b4-123">시스템에서 모듈 또는 스크립트 블록 로깅을 사용하도록 설정한 경우 사용자가 JEA 세션에서 실행한 각 명령에 대한 이벤트를 Windows 이벤트 로그에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-123">If you enabled module or script block logging on the system, you can see events in the Windows event logs for each command a user runs in a JEA session.</span></span> <span data-ttu-id="635b4-124">이러한 이벤트를 찾으려면 **Microsoft-Windows-PowerShell/Operational** 이벤트 로그를 열고 이벤트 ID가 **4104**인 이벤트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-124">To find these events, open **Microsoft-Windows-PowerShell/Operational** event log and look for events with event ID **4104**.</span></span>

<span data-ttu-id="635b4-125">각 이벤트 로그 항목에는 명령이 실행된 세션에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-125">Each event log entry includes information about the session in which the command was run.</span></span> <span data-ttu-id="635b4-126">JEA 세션의 경우 이벤트에 **ConnectedUser** 및 **RunAsUser**에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-126">For JEA sessions, the event includes information about the **ConnectedUser** and the **RunAsUser**.</span></span> <span data-ttu-id="635b4-127">**ConnectedUser**는 JEA 세션을 만든 실제 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-127">The **ConnectedUser** is the actual user who created the JEA session.</span></span> <span data-ttu-id="635b4-128">**RunAsUser**는 JEA가 명령을 실행하는 데 사용한 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-128">The **RunAsUser** is the account JEA used to execute the command.</span></span>

<span data-ttu-id="635b4-129">애플리케이션 이벤트 로그는 **RunAsUser**에 의해 변경된 내용을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-129">Application event logs show changes being made by the **RunAsUser**.</span></span> <span data-ttu-id="635b4-130">따라서 모듈 및 스크립트 로깅을 사용하도록 설정하면 **ConnectedUser**로 특정 명령 호출을 다시 추적해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-130">So having module and script logging enabled is required to trace a specific command invocation back to the **ConnectedUser**.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="635b4-131">애플리케이션 이벤트 로그</span><span class="sxs-lookup"><span data-stu-id="635b4-131">Application event logs</span></span>

<span data-ttu-id="635b4-132">외부 애플리케이션 또는 서비스와 상호 작용하는 JEA 세션에서 실행되는 명령은 이벤트를 자체 이벤트 로그에 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-132">Commands run in a JEA session that interact with external applications or services may log events to their own event logs.</span></span> <span data-ttu-id="635b4-133">PowerShell 로그 및 스크립트와 달리 다른 로깅 메커니즘은 JEA 세션의 연결된 사용자를 캡처하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-133">Unlike PowerShell logs and transcripts, other logging mechanisms don't capture the connected user of the JEA session.</span></span> <span data-ttu-id="635b4-134">대신 이러한 애플리케이션은 가상 실행 사용자만 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-134">Instead, those applications only log the virtual run-as user.</span></span>
<span data-ttu-id="635b4-135">명령을 실행한 사용자를 확인하려면 [세션 기록](#session-transcripts)을 확인하거나 애플리케이션 이벤트 로그에 표시된 시간 및 사용자와 PowerShell 이벤트 로그의 상관 관계를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-135">To determine who ran the command, you need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="635b4-136">WinRM 로그는 애플리케이션 이벤트 로그에서 연결한 사용자와 실행 사용자를 연결하는 데 도움을 줄 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-136">The WinRM log can also help you correlate run-as users to the connecting user in an application event log.</span></span> <span data-ttu-id="635b4-137">**Microsoft-Windows-Windows Remote Management/Operational** 로그의 이벤트 ID **193**은 새 JEA 세션마다 연결하는 사용자와 실행하는 사용자의 SID(보안 식별자) 및 계정 이름을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-137">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user for every new JEA session.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="635b4-138">세션 기록</span><span class="sxs-lookup"><span data-stu-id="635b4-138">Session transcripts</span></span>

<span data-ttu-id="635b4-139">각 사용자 세션에 대한 기록을 만들도록 JEA를 구성한 경우 모든 사용자 작업의 텍스트 복사본이 지정된 폴더에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-139">If you configured JEA to create a transcript for each user session, a text copy of every user's actions are stored in the specified folder.</span></span>

<span data-ttu-id="635b4-140">다음 명령(관리자로써)은 모든 기록 디텍터리를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-140">The following command (as an administrator) finds all transcript directories.</span></span>

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="635b4-141">각 기록은 세션이 시작된 시간, 세션에 연결된 사용자 및 해당 사용자에게 할당된 JEA ID에 대한 정보로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-141">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="635b4-142">기록의 본문에는 사용자가 호출한 각 명령에 대한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-142">The body of the transcript contains information about each command the user invoked.</span></span> <span data-ttu-id="635b4-143">PowerShell 원격에 대한 명령이 변환되는 방식으로 인해 JEA 세션에서 사용된 명령의 정확한 구문을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-143">The exact syntax of the command used is unavailable in JEA sessions because of the way commands are transformed for PowerShell remoting.</span></span> <span data-ttu-id="635b4-144">그러나 실행된 유효 명령을 여전히 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-144">However, you can still determine the effective command that was executed.</span></span> <span data-ttu-id="635b4-145">JEA 세션에서 `Get-Service Dns`를 실행한 사용자의 예제 기록 코드 조각은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-145">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="635b4-146">**CommandInvocation** 줄은 사용자가 실행하는 각 명령에 대해 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-146">A **CommandInvocation** line is written for each command a user runs.</span></span> <span data-ttu-id="635b4-147">**ParameterBindings**는 명령과 함께 제공된 각 매개 변수와 값을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-147">**ParameterBindings** record each parameter and value supplied with the command.</span></span> <span data-ttu-id="635b4-148">이전 예제에서 매개 변수 **Name**이 `Get-Service` cmdlet에 대한 값 **Dns**와 함께 제공되었음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-148">In the previous example, you can see that the parameter **Name** was supplied the with value **Dns** for the `Get-Service` cmdlet.</span></span>

<span data-ttu-id="635b4-149">또한 각 명령의 출력은 일반적으로 `Out-Default`로 **CommandInvocation**을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-149">The output of each command also triggers a **CommandInvocation**, usually to `Out-Default`.</span></span> <span data-ttu-id="635b4-150">`Out-Default`의 **InputObject**는 명령에서 반환되는 PowerShell 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-150">The **InputObject** of `Out-Default` is the PowerShell object returned from the command.</span></span> <span data-ttu-id="635b4-151">해당 개체의 세부 정보가 몇 줄 아래에 출력되어 사용자가 보게 되는 내용과 매우 비슷한 내용을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="635b4-151">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="635b4-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="635b4-152">See also</span></span>

[<span data-ttu-id="635b4-153">보안에 관한 *PowerShell ♥ the Blue Team*(PowerShell ♥ Blue Team) 블로그 게시물</span><span class="sxs-lookup"><span data-stu-id="635b4-153">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
