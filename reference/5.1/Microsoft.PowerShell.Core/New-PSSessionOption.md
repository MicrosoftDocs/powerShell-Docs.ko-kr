---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionOption
ms.openlocfilehash: 566091a53941cd122a10aa2bcb45cddfb1f40cc4
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388624"
---
# <span data-ttu-id="a55f6-103">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="a55f6-103">New-PSSessionOption</span></span>

## <span data-ttu-id="a55f6-104">개요</span><span class="sxs-lookup"><span data-stu-id="a55f6-104">SYNOPSIS</span></span>
<span data-ttu-id="a55f6-105">PSSession에 대한 고급 옵션을 포함하는 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-105">Creates an object that contains advanced options for a PSSession.</span></span>

## <span data-ttu-id="a55f6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a55f6-106">SYNTAX</span></span>

```
New-PSSessionOption [-MaximumRedirection <Int32>] [-NoCompression] [-NoMachineProfile] [-Culture <CultureInfo>]
 [-UICulture <CultureInfo>] [-MaximumReceivedDataSizePerCommand <Int32>] [-MaximumReceivedObjectSize <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-MaxConnectionRetryCount <Int32>]
 [-ApplicationArguments <PSPrimitiveDictionary>] [-OpenTimeout <Int32>] [-CancelTimeout <Int32>]
 [-IdleTimeout <Int32>] [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <AuthenticationMechanism>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [-IncludePortInSPN] [<CommonParameters>]
```

## <span data-ttu-id="a55f6-107">설명</span><span class="sxs-lookup"><span data-stu-id="a55f6-107">DESCRIPTION</span></span>

<span data-ttu-id="a55f6-108">`New-PSSessionOption`Cmdlet은 사용자 관리 세션 ( **PSSession** )에 대 한 고급 옵션을 포함 하는 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-108">The `New-PSSessionOption` cmdlet creates an object that contains advanced options for a user-managed session ( **PSSession** ).</span></span> <span data-ttu-id="a55f6-109">,, 등의 **PSSession** 을 만드는 Cmdlet의 **sessionoption** 매개 변수 값으로 개체를 사용할 수 있습니다 `New-PSSession` `Enter-PSSession` `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="a55f6-109">You can use the object as the value of the **SessionOption** parameter of cmdlets that create a **PSSession** , such as `New-PSSession`, `Enter-PSSession`, and `Invoke-Command`.</span></span>

<span data-ttu-id="a55f6-110">매개 변수가 없는 경우는 `New-PSSessionOption` 모든 옵션에 대 한 기본값을 포함 하는 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-110">Without parameters, `New-PSSessionOption` generates an object that contains the default values for all of the options.</span></span> <span data-ttu-id="a55f6-111">모든 속성을 편집할 수 있으므로 결과 개체를 템플릿으로 사용하고 엔터프라이즈에 대한 표준 옵션 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-111">Because all of the properties can be edited, you can use the resulting object as a template, and create standard option objects for your enterprise.</span></span>

<span data-ttu-id="a55f6-112">기본 설정 변수에 세션 옵션 개체를 저장할 수도 있습니다 `$PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="a55f6-112">You can also save a session option object in the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="a55f6-113">이 변수 값은 세션 옵션에 대한 새 기본값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-113">The values of this variable establish new default values for the session options.</span></span> <span data-ttu-id="a55f6-114">세션에 대해 설정된 세션 옵션이 없을 경우 적용되며 세션 구성에서 설정된 옵션보다 우선하지만 세션을 만드는 cmdlet에서 세션 옵션 또는 세션 옵션 개체를 지정하여 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-114">They effective when no session options are set for the session and they take precedence over options set in the session configuration, but you can override them by specifying session options or a session option object in a cmdlet that creates a session.</span></span> <span data-ttu-id="a55f6-115">기본 설정 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a55f6-115">For more information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="a55f6-116">세션을 만드는 cmdlet에 세션 옵션 개체를 사용할 경우 세션 옵션 값이 $PSSessionOption 기본 설정 변수 및 세션 구성에 설정된 세션의 기본값보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-116">When you use a session option object in a cmdlet that creates a session, the session option values take precedence over default values for sessions set in the $PSSessionOption preference variable and in the session configuration.</span></span> <span data-ttu-id="a55f6-117">그러나 이러한 값은 세션 구성에 설정된 최대값, 할당량 또는 제한보다 우선하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-117">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span> <span data-ttu-id="a55f6-118">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a55f6-118">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="a55f6-119">예제</span><span class="sxs-lookup"><span data-stu-id="a55f6-119">EXAMPLES</span></span>

### <span data-ttu-id="a55f6-120">예 1: 기본 세션 옵션 만들기</span><span class="sxs-lookup"><span data-stu-id="a55f6-120">Example 1: Create a default session option</span></span>

<span data-ttu-id="a55f6-121">이 명령은 모든 기본값을 포함 하는 세션 옵션 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-121">This command creates a session option object that has all of the default values.</span></span>

```powershell
New-PSSessionOption
```

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

### <span data-ttu-id="a55f6-122">예 2: 세션 옵션 개체를 사용 하 여 세션 구성</span><span class="sxs-lookup"><span data-stu-id="a55f6-122">Example 2: Configure a session by using a session option object</span></span>

<span data-ttu-id="a55f6-123">이 예제에서는 세션 옵션 개체를 사용하여 세션을 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-123">This example shows how to use a session option object to configure a session.</span></span>

```powershell
$pso = New-PSSessionOption -Culture "fr-fr" -MaximumReceivedObjectSize 10MB
New-PSSession -ComputerName Server01 -SessionOption $pso
```

<span data-ttu-id="a55f6-124">첫 번째 명령은 새 세션 옵션 개체를 만들어 변수의 값에 저장 합니다 `$pso` .</span><span class="sxs-lookup"><span data-stu-id="a55f6-124">The first command creates a new session option object and saves it in the value of the `$pso` variable.</span></span> <span data-ttu-id="a55f6-125">두 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` Server01 원격 컴퓨터에서 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-125">The second command uses the `New-PSSession` cmdlet to create a session on the Server01 remote computer.</span></span> <span data-ttu-id="a55f6-126">이 명령은 변수의 값에 있는 session 옵션 개체를 `$pso` 명령의 **sessionoption** 매개 변수 값으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-126">The command uses the session option object in the value of the `$pso` variable as the value of the **SessionOption** parameter of the command.</span></span>

### <span data-ttu-id="a55f6-127">예 3: 대화형 세션 시작</span><span class="sxs-lookup"><span data-stu-id="a55f6-127">Example 3: Start an interactive session</span></span>

<span data-ttu-id="a55f6-128">이 명령은 cmdlet을 사용 하 여 `Enter-PSSession` Server01 컴퓨터와의 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-128">This command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

```powershell
Enter-PSSession -ComputerName Server01 -SessionOption (New-PSSessionOption -NoEncryption -NoCompression)
```

<span data-ttu-id="a55f6-129">**Sessionoption** 매개 변수 값은 `New-PSSessionOption` **Noencryption** 및 **noencryption** 매개 변수를 포함 하는 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-129">The value of the **SessionOption** parameter is a `New-PSSessionOption` command that has the **NoEncryption** and **NoCompression** parameters.</span></span>

<span data-ttu-id="a55f6-130">명령은 `New-PSSessionOption` 명령 전에 실행 되도록 괄호로 묶습니다 `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="a55f6-130">The `New-PSSessionOption` command is enclosed in parentheses to make sure that it runs before the `Enter-PSSession` command.</span></span>

### <span data-ttu-id="a55f6-131">예제 4: 세션 옵션 개체 수정</span><span class="sxs-lookup"><span data-stu-id="a55f6-131">Example 4: Modify a session option object</span></span>

<span data-ttu-id="a55f6-132">이 예에서는 세션 옵션 개체를 수정할 수 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-132">This example demonstrates that you can modify the session option object.</span></span> <span data-ttu-id="a55f6-133">모든 속성에 읽기/쓰기 값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-133">All properties have read/write values.</span></span>

```powershell
$a = New-PSSessionOption
$a.OpenTimeout
```

```Output
Days              : 0
Hours             : 0
Minutes           : 3
Seconds           : 0
Milliseconds      : 0
Ticks             : 1800000000
TotalDays         : 0.00208333333333333
TotalHours        : 0.05
TotalMinutes      : 3
TotalSeconds      : 180
TotalMilliseconds : 180000
```

```powershell
$a.UICulture = (Get-UICulture)
$a.OpenTimeout = (New-Timespan -Minutes 4)
$a.MaximumConnectionRedirectionCount = 1
$a
```

```Output
MaximumConnectionRedirectionCount : 1
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         : en-US
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:04:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

<span data-ttu-id="a55f6-134">이 메서드를 사용하여 엔터프라이즈에 대한 표준 세션 개체를 만든 다음 특정 사용을 위해 이 개체의 사용자 지정 버전을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-134">Use this method to create a standard session object for your enterprise, and then create customized versions of it for particular uses.</span></span>

### <span data-ttu-id="a55f6-135">예 5: 기본 설정 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="a55f6-135">Example 5: Create a preference variable</span></span>

<span data-ttu-id="a55f6-136">이 명령은 `$PSSessionOption` 기본 설정 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-136">This command creates a `$PSSessionOption` preference variable.</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -OpenTimeOut 120000
```

<span data-ttu-id="a55f6-137">`$PSSessionOption`기본 설정 변수는 세션에서 발생 하는 경우, 및 cmdlet을 사용 하 여 생성 된 세션의 옵션에 대 한 기본값을 설정 `New-PSSession` `Enter-PSSession` `Invoke-Command` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-137">When the `$PSSessionOption` preference variable occurs in the session, it establishes default values for options in the sessions that are created by using the `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="a55f6-138">`$PSSessionOption`모든 세션에서 변수를 사용할 수 있도록 하려면 powershell 세션 및 powershell 프로필에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-138">To make the `$PSSessionOption` variable available in all sessions, add it to your PowerShell session and to your PowerShell profile.</span></span>

<span data-ttu-id="a55f6-139">기본 설정 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a55f6-139">For more information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>
<span data-ttu-id="a55f6-140">프로필에 대한 자세한 내용은 [about_Profiles](About/about_Profiles.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a55f6-140">For more information about profiles, see [about_Profiles](About/about_Profiles.md).</span></span>

### <span data-ttu-id="a55f6-141">예 6: 원격 세션 구성에 대 한 요구 사항 충족</span><span class="sxs-lookup"><span data-stu-id="a55f6-141">Example 6: Fulfill the requirements for a remote session configuration</span></span>

<span data-ttu-id="a55f6-142">이 예제에서는 **SessionOption** 개체를 사용하여 원격 세션 구성에 대한 요구 사항을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-142">This example shows how to use a **SessionOption** object to fulfill the requirements for a remote session configuration.</span></span>

```powershell
$skipCN = New-PSSessionOption -SkipCNCheck
New-PSSession -ComputerName 171.09.21.207 -UseSSL -Credential Domain01\User01 -SessionOption $SkipCN
```

<span data-ttu-id="a55f6-143">첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSessionOption` **Skipcncheck** 속성이 있는 세션 옵션 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-143">The first command uses the `New-PSSessionOption` cmdlet to create a session option object that has the **SkipCNCheck** property.</span></span> <span data-ttu-id="a55f6-144">이 명령은 결과 세션 개체를 변수에 저장 합니다 `$skipCN` .</span><span class="sxs-lookup"><span data-stu-id="a55f6-144">The command saves the resulting session object in the `$skipCN` variable.</span></span>

<span data-ttu-id="a55f6-145">두 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` 원격 컴퓨터에서 새 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-145">The second command uses the `New-PSSession` cmdlet to create a new session on a remote computer.</span></span> <span data-ttu-id="a55f6-146">`$skipCN`Check 변수는 **sessionoption** 매개 변수 값에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-146">The `$skipCN` check variable is used in the value of the **SessionOption** parameter.</span></span>

<span data-ttu-id="a55f6-147">컴퓨터는 IP 주소로 식별 되므로 **ComputerName** 매개 변수 값이 SSL(SECURE SOCKETS LAYER) (SSL)에 사용 되는 인증서의 일반 이름과 일치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-147">Because the computer is identified by its IP address, the value of the **ComputerName** parameter does not match any of the common names in the certificate that is used for Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="a55f6-148">따라서 **SkipCNCheck** 옵션은 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-148">As a result, the **SkipCNCheck** option is required.</span></span>

### <span data-ttu-id="a55f6-149">예 7: 원격 세션에서 인수를 사용할 수 있도록 설정</span><span class="sxs-lookup"><span data-stu-id="a55f6-149">Example 7: Make arguments available to a remote session</span></span>

<span data-ttu-id="a55f6-150">이 예에서는 cmdlet의 **Applicationarguments** 매개 변수를 사용 하 여 `New-PSSessionOption` 원격 세션에서 추가 데이터를 사용할 수 있도록 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-150">This example shows how to use the **ApplicationArguments** parameter of the `New-PSSessionOption` cmdlet to make additional data available to the remote session.</span></span>

```powershell
$team = @{Team="IT"; Use="Testing"}
$TeamOption = New-PSSessionOption -ApplicationArguments $team
$s = New-PSSession -ComputerName Server01 -SessionOption $TeamOption
Invoke-Command -Session $s {$PSSenderInfo.ApplicationArguments}
```

```Output
Name                 Value
----                 -----
Team                 IT
Use                  Testing
PSVersionTable       {CLRVersion, BuildVersion, PSVersion, WSManStackVersion...}
```

```powershell
Invoke-Command -Session $s {
  if ($PSSenderInfo.ApplicationArguments.Use -ne "Testing") {
    .\logFiles.ps1
  }
  else {
    "Just testing."
  }
}
```

```Output
Just testing.
```

<span data-ttu-id="a55f6-151">첫 번째 명령은 **팀** 과 **사용** 이라는 두 개의 키가 있는 해시 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-151">The first command creates a hash table with two keys, **Team** and **Use**.</span></span> <span data-ttu-id="a55f6-152">이 명령은 해시 테이블을 변수에 저장 합니다 `$team` .</span><span class="sxs-lookup"><span data-stu-id="a55f6-152">The command saves the hash table in the `$team` variable.</span></span> <span data-ttu-id="a55f6-153">해시 테이블에 대한 자세한 내용은 [about_Hash_Tables](about/about_Hash_Tables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a55f6-153">For more information about hash tables, see [about_Hash_Tables](about/about_Hash_Tables.md).</span></span>

<span data-ttu-id="a55f6-154">그런 다음 `New-PSSessionOption` **applicationarguments** 매개 변수를 사용 하는 cmdlet은 변수에 저장 된 세션 옵션 개체를 만듭니다 `$team` .</span><span class="sxs-lookup"><span data-stu-id="a55f6-154">Next, the `New-PSSessionOption` cmdlet, using the **ApplicationArguments** parameter, creates a session option object saved in the `$team` variable.</span></span> <span data-ttu-id="a55f6-155">에서는 `New-PSSessionOption` 세션 옵션 개체를 만들 때 **applicationarguments** 매개 변수 값의 해시 테이블을 기본 사전으로 자동 변환 하므로 데이터를 원격 세션으로 안정적으로 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-155">When `New-PSSessionOption` creates the session option object, it automatically converts the hash table in the value of the **ApplicationArguments** parameter to a primitive dictionary so the data can be reliably transmitted to the remote session.</span></span>

<span data-ttu-id="a55f6-156">`New-PSSession`Cmdlet은 Server01 컴퓨터에서 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-156">The `New-PSSession` cmdlet starts a session on the Server01 computer.</span></span> <span data-ttu-id="a55f6-157">**Sessionoption** 매개 변수를 사용 하 여 변수에 옵션을 포함 `$teamOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-157">It uses the **SessionOption** parameter to include the options in the `$teamOption` variable.</span></span>

<span data-ttu-id="a55f6-158">`Invoke-Command`이 cmdlet은 변수의 데이터를 `$team` 원격 세션의 명령에서 사용할 수 있다는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-158">The `Invoke-Command` cmdlet demonstrates that the data in the `$team` variable is available to commands in the remote session.</span></span> <span data-ttu-id="a55f6-159">자동 변수의 **Applicationarguments** 속성에 데이터가 나타납니다 `$PSSenderInfo` .</span><span class="sxs-lookup"><span data-stu-id="a55f6-159">The data appears in the **ApplicationArguments** property of the `$PSSenderInfo` automatic variable.</span></span>

<span data-ttu-id="a55f6-160">마지막에는 `Invoke-Command` 데이터를 사용 하는 방법이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-160">The final `Invoke-Command` shows how the data might be used.</span></span>

## <span data-ttu-id="a55f6-161">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a55f6-161">PARAMETERS</span></span>

### <span data-ttu-id="a55f6-162">-ApplicationArguments</span><span class="sxs-lookup"><span data-stu-id="a55f6-162">-ApplicationArguments</span></span>

<span data-ttu-id="a55f6-163">원격 세션으로 전송되는 기본 사전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-163">Specifies a primitive dictionary that is sent to the remote session.</span></span> <span data-ttu-id="a55f6-164">세션 구성의 시작 스크립트를 포함 하 여 원격 세션의 명령 및 스크립트는 자동 변수의 **Applicationarguments** 속성에서이 사전을 찾을 수 있습니다 `$PSSenderInfo` .</span><span class="sxs-lookup"><span data-stu-id="a55f6-164">Commands and scripts in the remote session, including startup scripts in the session configuration, can find this dictionary in the **ApplicationArguments** property of the `$PSSenderInfo` automatic variable.</span></span> <span data-ttu-id="a55f6-165">이 매개 변수를 사용하여 데이터를 원격 세션으로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-165">You can use this parameter to send data to the remote session.</span></span>

<span data-ttu-id="a55f6-166">자세한 내용은 [about_Hash_Tables](about/about_Hash_Tables.md), [about_Session_Configurations](About/about_Session_Configurations.md)및 [about_Automatic_Variables](about/about_Automatic_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a55f6-166">For more information, see [about_Hash_Tables](about/about_Hash_Tables.md), [about_Session_Configurations](About/about_Session_Configurations.md), and [about_Automatic_Variables](about/about_Automatic_Variables.md).</span></span>

```yaml
Type: System.Management.Automation.PSPrimitiveDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-167">-CancelTimeout</span><span class="sxs-lookup"><span data-stu-id="a55f6-167">-CancelTimeout</span></span>

<span data-ttu-id="a55f6-168">PowerShell이 종료 되기 전에 취소 작업 (CTRL + C)이 완료 될 때까지 대기 하는 시간을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-168">Determines how long PowerShell waits for a cancel operation (CTRL+C) to finish before ending it.</span></span>
<span data-ttu-id="a55f6-169">값을 밀리초 단위로 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="a55f6-169">Enter a value in milliseconds.</span></span>

<span data-ttu-id="a55f6-170">기본값은 60000(1분)입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-170">The default value is 60000 (one minute).</span></span> <span data-ttu-id="a55f6-171">값이 0이면 시간 제한이 없으며 명령이 무기한 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-171">A value of 0 (zero) means no time-out; the command continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: CancelTimeoutMSec

Required: False
Position: Named
Default value: 60000
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-172">-문화권</span><span class="sxs-lookup"><span data-stu-id="a55f6-172">-Culture</span></span>

<span data-ttu-id="a55f6-173">세션에 사용할 문화권을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-173">Specifies the culture to use for the session.</span></span> <span data-ttu-id="a55f6-174">`<languagecode2>-<country/regioncode2>`형식 (예:)의 문화권 이름 `ja-JP` , **cultureinfo** 개체가 포함 된 변수 또는 **cultureinfo** 개체를 가져오는 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-174">Enter a culture name in `<languagecode2>-<country/regioncode2>` format (like `ja-JP`), a variable that contains a **CultureInfo** object, or a command that gets a **CultureInfo** object.</span></span>

<span data-ttu-id="a55f6-175">기본값은 이며 `$Null` 운영 체제에 설정 된 문화권이 세션에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-175">The default value is `$Null`, and the culture that is set in the operating system is used in the session.</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-176">-IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="a55f6-176">-IdleTimeout</span></span>

<span data-ttu-id="a55f6-177">원격 컴퓨터가 로컬 컴퓨터의 통신을 받지 못하는 경우 세션이 열린 상태로 유지 되는 기간을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-177">Determines how long the session stays open if the remote computer does not receive any communication from the local computer.</span></span> <span data-ttu-id="a55f6-178">하트 비트 신호를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-178">This includes the heartbeat signal.</span></span> <span data-ttu-id="a55f6-179">간격이 만료되면 세션이 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-179">When the interval expires, the session closes.</span></span>

<span data-ttu-id="a55f6-180">유휴 시간 제한 값은 세션의 연결을 끊고 다시 연결 하려는 경우에 매우 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-180">The idle time-out value is of significant importance if you intend to disconnect and reconnect to a session.</span></span> <span data-ttu-id="a55f6-181">세션이 시간 초과되지 않은 경우에만 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-181">You can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="a55f6-182">값을 밀리초 단위로 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="a55f6-182">Enter a value in milliseconds.</span></span> <span data-ttu-id="a55f6-183">최소값은 60000(1분)입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-183">The minimum value is 60000 (1 minute).</span></span> <span data-ttu-id="a55f6-184">최대값은 세션 구성의 **MaxIdleTimeoutms** 속성 값입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-184">The maximum is the value of the **MaxIdleTimeoutms** property of the session configuration.</span></span> <span data-ttu-id="a55f6-185">기본값-1은 유휴 시간 제한 값을 설정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-185">The default value, -1, does not set an idle time-out.</span></span>

<span data-ttu-id="a55f6-186">세션은 세션 옵션에 설정 된 유휴 시간 제한 (있는 경우)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-186">The session uses the idle time-out that is set in the session options, if any.</span></span> <span data-ttu-id="a55f6-187">(-1)가 설정 되지 않은 경우 세션은 세션 구성의 **IdleTimeoutMs** 속성 값 이나 WSMan 셸 시간 제한 값 ( `WSMan:\<ComputerName>\Shell\IdleTimeout` ) 중에서 가장 짧은 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-187">If none is set (-1), the session uses the value of the **IdleTimeoutMs** property of the session configuration or the WSMan shell time-out value (`WSMan:\<ComputerName>\Shell\IdleTimeout`), whichever is shortest.</span></span>

<span data-ttu-id="a55f6-188">세션 옵션에서 설정된 유휴 시간 제한이 세션 구성의 **MaxIdleTimeoutMs** 속성 값을 초과할 경우 세션을 만드는 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-188">If the idle timeout set in the session options exceeds the value of the **MaxIdleTimeoutMs** property of the session configuration, the command to create a session fails.</span></span>

<span data-ttu-id="a55f6-189">기본 **IdleTimeoutMs** 세션 구성의 값은 720만 밀리초 (2 시간) **입니다.**</span><span class="sxs-lookup"><span data-stu-id="a55f6-189">The **IdleTimeoutMs** value of the default **Microsoft.PowerShell** session configuration is 7200000 milliseconds (2 hours).</span></span> <span data-ttu-id="a55f6-190">**MaxIdleTimeoutMs** 값은 2147483647 밀리초 ( \> 24 일)입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-190">Its **MaxIdleTimeoutMs** value is 2147483647 milliseconds (\>24 days).</span></span> <span data-ttu-id="a55f6-191">WSMan 셸 유휴 시간 제한 ()의 기본값은 `WSMan:\<ComputerName>\Shell\IdleTimeout` 720만 밀리초 (2 시간)입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-191">The default value of the WSMan shell idle time-out (`WSMan:\<ComputerName>\Shell\IdleTimeout`) is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="a55f6-192">세션에서 연결을 끊거나 세션에 다시 연결할 때 세션의 유휴 시간 제한 값을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-192">The idle time-out value of a session can also be changed when disconnecting from a session or reconnecting to a session.</span></span> <span data-ttu-id="a55f6-193">자세한 내용은 `Disconnect-PSSession` 및 `Connect-PSSession`를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a55f6-193">For more information, see `Disconnect-PSSession` and `Connect-PSSession`.</span></span>

<span data-ttu-id="a55f6-194">Windows PowerShell 2.0에서 **IdleTimeout** 매개 변수의 기본값은 240000(4분)입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-194">In Windows PowerShell 2.0, the default value of the **IdleTimeout** parameter is 240000 (4 minutes).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: IdleTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-195">-IncludePortInSPN</span><span class="sxs-lookup"><span data-stu-id="a55f6-195">-IncludePortInSPN</span></span>

<span data-ttu-id="a55f6-196">Kerberos 인증에 사용 되는 SPN (서비스 사용자 이름)의 포트 번호를 포함 합니다 (예:) `HTTP://<ComputerName>:5985` .</span><span class="sxs-lookup"><span data-stu-id="a55f6-196">Includes the port number in the Service Principal Name (SPN) used for Kerberos authentication, for example, `HTTP://<ComputerName>:5985`.</span></span> <span data-ttu-id="a55f6-197">이 옵션은 기본값이 아닌 SPN을 사용하는 클라이언트가 Kerberos 인증을 사용하는 원격 컴퓨터에 인증할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-197">This option allows a client that uses a non-default SPN to authenticate against a remote computer that uses Kerberos authentication.</span></span>

<span data-ttu-id="a55f6-198">Kerberos 인증을 지원하는 여러 서비스가 서로 다른 사용자 계정으로 실행되는 엔터프라이즈를 위한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-198">The option is designed for enterprises where multiple services that support Kerberos authentication are running under different user accounts.</span></span> <span data-ttu-id="a55f6-199">예를 들어 Kerberos 인증을 허용 하는 IIS 응용 프로그램에서 컴퓨터 계정과 다른 사용자 계정에 기본 SPN을 등록 하도록 요구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-199">For example, an IIS application that allows for Kerberos authentication can require the default SPN to be registered to a user account that differs from the computer account.</span></span> <span data-ttu-id="a55f6-200">이러한 경우 PowerShell remoting은 컴퓨터 계정에 등록 된 SPN이 필요 하므로 Kerberos를 사용 하 여 인증할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-200">In such cases, PowerShell remoting cannot use Kerberos to authenticate because it requires an SPN that is registered to the computer account.</span></span> <span data-ttu-id="a55f6-201">이 문제를 해결 하기 위해 관리자는 다른 사용자 계정에 등록 된 **Setspn.exe** 를 사용 하는 등의 다양 한 spn을 만들 수 있으며 spn에 포트 번호를 포함 하 여 서로 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-201">To resolve this problem, administrators can create different SPNs, such as by using **Setspn.exe** , that are registered to different user accounts and can distinguish between them by including the port number in the SPN.</span></span>

<span data-ttu-id="a55f6-202">자세한 내용은 [Setspn Overview](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10))를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a55f6-202">For more information, see [Setspn Overview](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).</span></span>

<span data-ttu-id="a55f6-203">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-203">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a55f6-204">-MaxConnectionRetryCount</span><span class="sxs-lookup"><span data-stu-id="a55f6-204">-MaxConnectionRetryCount</span></span>

<span data-ttu-id="a55f6-205">네트워크 문제로 인해 현재 시도에 실패 하는 경우 PowerShell에서 대상 컴퓨터에 연결을 시도 하는 횟수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-205">Specifies the number of times that PowerShell attempts to make a connection to a target machine if the current attempt fails due to network issues.</span></span> <span data-ttu-id="a55f6-206">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-206">The default value is 5.</span></span>

<span data-ttu-id="a55f6-207">이 매개 변수는 PowerShell 버전 5.0에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-207">This parameter was added for PowerShell version 5.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-208">-MaximumReceivedDataSizePerCommand</span><span class="sxs-lookup"><span data-stu-id="a55f6-208">-MaximumReceivedDataSizePerCommand</span></span>

<span data-ttu-id="a55f6-209">로컬 컴퓨터가 단일 명령으로 원격 컴퓨터에서 수신할 수 있는 최대 바이트 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-209">Specifies the maximum number of bytes that the local computer can receive from the remote computer in a single command.</span></span> <span data-ttu-id="a55f6-210">값을 바이트 단위로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-210">Enter a value in bytes.</span></span> <span data-ttu-id="a55f6-211">기본적으로 데이터 크기 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-211">By default, there is no data size limit.</span></span>

<span data-ttu-id="a55f6-212">이 옵션은 클라이언트 컴퓨터의 리소스를 보호하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-212">This option is designed to protect the resources on the client computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-213">-MaximumReceivedObjectSize</span><span class="sxs-lookup"><span data-stu-id="a55f6-213">-MaximumReceivedObjectSize</span></span>

<span data-ttu-id="a55f6-214">로컬 컴퓨터가 원격 컴퓨터에서 수신할 수 있는 개체의 최대 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-214">Specifies the maximum size of an object that the local computer can receive from the remote computer.</span></span> <span data-ttu-id="a55f6-215">이 옵션은 클라이언트 컴퓨터의 리소스를 보호하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-215">This option is designed to protect the resources on the client computer.</span></span> <span data-ttu-id="a55f6-216">값을 바이트 단위로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-216">Enter a value in bytes.</span></span>

<span data-ttu-id="a55f6-217">Windows PowerShell 2.0에서 이 매개 변수를 생략하면 개체 크기 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-217">In Windows PowerShell 2.0, if you omit this parameter, there is no object size limit.</span></span> <span data-ttu-id="a55f6-218">Windows PowerShell 3.0부터 이 매개 변수를 생략할 경우 기본값은 200MB입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-218">Beginning in Windows PowerShell 3.0, if you omit this parameter, the default value is 200 MB.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 200 MB
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-219">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="a55f6-219">-MaximumRedirection</span></span>

<span data-ttu-id="a55f6-220">연결에 실패 하기 전에 PowerShell에서 연결을 대체 URI (Uniform Resource Identifier)로 리디렉션하는 횟수를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-220">Determines how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="a55f6-221">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-221">The default value is 5.</span></span> <span data-ttu-id="a55f6-222">값 0은 모든 리디렉션을 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-222">A value of 0 (zero) prevents all redirection.</span></span>

<span data-ttu-id="a55f6-223">이 옵션은 세션을 만드는 명령에 **Allowredirection** 매개 변수가 사용 되는 경우에만 세션에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-223">This option is used in the session only when the **AllowRedirection** parameter is used in the command that creates the session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-224">-NoCompression</span><span class="sxs-lookup"><span data-stu-id="a55f6-224">-NoCompression</span></span>

<span data-ttu-id="a55f6-225">세션에서 패킷 압축을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-225">Turns off packet compression in the session.</span></span> <span data-ttu-id="a55f6-226">압축하면 프로세서 주기가 더 많이 사용되지만 전송 속도가 빨라집니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-226">Compression uses more processor cycles, but it makes transmission faster.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-227">-NoEncryption</span><span class="sxs-lookup"><span data-stu-id="a55f6-227">-NoEncryption</span></span>

<span data-ttu-id="a55f6-228">데이터 암호화를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-228">Turns off data encryption.</span></span>

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

### <span data-ttu-id="a55f6-229">-NoMachineProfile</span><span class="sxs-lookup"><span data-stu-id="a55f6-229">-NoMachineProfile</span></span>

<span data-ttu-id="a55f6-230">사용자의 Windows 사용자 프로필이 로드되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-230">Prevents loading the user's Windows user profile.</span></span> <span data-ttu-id="a55f6-231">따라서 세션을 더 빨리 만들 수 있지만 사용자별 레지스트리 설정, 환경 변수와 같은 항목 및 인증서를 세션에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-231">As a result, the session might be created faster, but user-specific registry settings, items such as environment variables, and certificates are not available in the session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-232">-OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="a55f6-232">-OpenTimeout</span></span>

<span data-ttu-id="a55f6-233">클라이언트 컴퓨터가 세션 연결이 설정될 때까지 기다리는 기간을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-233">Determines how long the client computer waits for the session connection to be established.</span></span> <span data-ttu-id="a55f6-234">간격이 만료되면 연결 설정 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-234">When the interval expires, the command to establish the connection fails.</span></span> <span data-ttu-id="a55f6-235">값을 밀리초 단위로 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="a55f6-235">Enter a value in milliseconds.</span></span>

<span data-ttu-id="a55f6-236">기본값은 180000(3분)입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-236">The default value is 180000 (3 minutes).</span></span> <span data-ttu-id="a55f6-237">값이 0이면 시간 제한이 없으며 명령이 무기한 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-237">A value of 0 (zero) means no time-out; the command continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OpenTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-238">-OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="a55f6-238">-OperationTimeout</span></span>

<span data-ttu-id="a55f6-239">세션의 작업이 실행될 수 있는 최대 시간을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-239">Determines the maximum time that any operation in the session can run.</span></span> <span data-ttu-id="a55f6-240">간격이 만료되면 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-240">When the interval expires, the operation fails.</span></span> <span data-ttu-id="a55f6-241">값을 밀리초 단위로 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="a55f6-241">Enter a value in milliseconds.</span></span>

<span data-ttu-id="a55f6-242">기본값은 180000(3분)입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-242">The default value is 180000 (3 minutes).</span></span> <span data-ttu-id="a55f6-243">값이 0이면 시간 제한이 없으며 작업이 무기한 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-243">A value of 0 (zero) means no time-out; the operation continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-244">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="a55f6-244">-OutputBufferingMode</span></span>

<span data-ttu-id="a55f6-245">출력 버퍼가 가득 찰 경우 연결이 끊긴 세션에서 명령 출력을 관리하는 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-245">Determines how command output is managed in disconnected sessions when the output buffer becomes full.</span></span>

<span data-ttu-id="a55f6-246">출력 버퍼링 모드가 세션 또는 세션 구성에서 설정되지 않은 경우 기본값은 **Block** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-246">If the output buffering mode is not set in the session or in the session configuration, the default value is **Block**.</span></span> <span data-ttu-id="a55f6-247">사용자가 세션에서 연결을 끊을 때 출력 버퍼링 모드를 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-247">Users can also change the output buffering mode when disconnecting the session.</span></span>

<span data-ttu-id="a55f6-248">이 매개 변수를 생략 하는 경우 세션 옵션 개체의 **OutputBufferingMode** 값은 None입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-248">If you omit this parameter, the value of the **OutputBufferingMode** of the session option object is None.</span></span> <span data-ttu-id="a55f6-249">**Block** 또는 **Drop** 값은 세션 구성에서 설정된 출력 버퍼링 모드 전송 옵션을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-249">A value of **Block** or **Drop** overrides the output buffering mode transport option set in the session configuration.</span></span> <span data-ttu-id="a55f6-250">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-250">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a55f6-251">차단.</span><span class="sxs-lookup"><span data-stu-id="a55f6-251">Block.</span></span> <span data-ttu-id="a55f6-252">출력 버퍼가 가득 찰 경우 버퍼를 지울 때까지 실행이 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-252">When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="a55f6-253">Drop.</span><span class="sxs-lookup"><span data-stu-id="a55f6-253">Drop.</span></span> <span data-ttu-id="a55f6-254">출력 버퍼가 가득 차도 실행이 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-254">When the output buffer is full, execution continues.</span></span> <span data-ttu-id="a55f6-255">새 출력이 저장되면 가장 오래된 출력을 버립니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-255">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="a55f6-256">없음</span><span class="sxs-lookup"><span data-stu-id="a55f6-256">None.</span></span> <span data-ttu-id="a55f6-257">출력 버퍼링 모드를 지정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-257">No output buffering mode is specified.</span></span>

<span data-ttu-id="a55f6-258">출력 버퍼링 모드 전송 옵션에 대 한 자세한 내용은을 참조 하십시오 `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="a55f6-258">For more information about the output buffering mode transport option, see `New-PSTransportOption`.</span></span>

<span data-ttu-id="a55f6-259">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-259">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-260">-System.management.automation.remoting.proxyaccesstype</span><span class="sxs-lookup"><span data-stu-id="a55f6-260">-ProxyAccessType</span></span>

<span data-ttu-id="a55f6-261">호스트 이름을 확인하는 데 사용되는 메커니즘을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-261">Determines which mechanism is used to resolve the host name.</span></span> <span data-ttu-id="a55f6-262">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-262">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a55f6-263">IEConfig</span><span class="sxs-lookup"><span data-stu-id="a55f6-263">IEConfig</span></span>
- <span data-ttu-id="a55f6-264">WinHttpConfig</span><span class="sxs-lookup"><span data-stu-id="a55f6-264">WinHttpConfig</span></span>
- <span data-ttu-id="a55f6-265">자동 검색</span><span class="sxs-lookup"><span data-stu-id="a55f6-265">AutoDetect</span></span>
- <span data-ttu-id="a55f6-266">NoProxyServer</span><span class="sxs-lookup"><span data-stu-id="a55f6-266">NoProxyServer</span></span>
- <span data-ttu-id="a55f6-267">없음</span><span class="sxs-lookup"><span data-stu-id="a55f6-267">None</span></span>

<span data-ttu-id="a55f6-268">기본값은 None입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-268">The default value is None.</span></span>

<span data-ttu-id="a55f6-269">이 매개 변수 값에 대 한 자세한 내용은 [System.management.automation.remoting.proxyaccesstype 열거형](/dotnet/api/system.management.automation.remoting.proxyaccesstype)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a55f6-269">For information about the values of this parameter, see [ProxyAccessType Enumeration](/dotnet/api/system.management.automation.remoting.proxyaccesstype).</span></span>

```yaml
Type: System.Management.Automation.Remoting.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: None, IEConfig, WinHttpConfig, AutoDetect, NoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-270">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="a55f6-270">-ProxyAuthentication</span></span>

<span data-ttu-id="a55f6-271">프록시 확인에 사용되는 인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-271">Specifies the authentication method that is used for proxy resolution.</span></span> <span data-ttu-id="a55f6-272">이 매개 변수에 허용 되는 값은 **Basic** , **Digest** 및 **Negotiate** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-272">The acceptable values for this parameter are: **Basic** , **Digest** , and **Negotiate**.</span></span> <span data-ttu-id="a55f6-273">기본값은 **Negotiate** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-273">The default value is **Negotiate**.</span></span>

<span data-ttu-id="a55f6-274">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a55f6-274">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Negotiate
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-275">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a55f6-275">-ProxyCredential</span></span>

<span data-ttu-id="a55f6-276">프록시 인증에 사용할 자격 증명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-276">Specifies the credentials to use for proxy authentication.</span></span> <span data-ttu-id="a55f6-277">**Pscredential** 개체를 포함 하는 변수 또는 **pscredential** 개체를 가져오는 명령 (예: 명령)을 입력 `Get-Credential` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-277">Enter a variable that contains a **PSCredential** object or a command that gets a **PSCredential** object, such as a `Get-Credential` command.</span></span> <span data-ttu-id="a55f6-278">이 옵션을 설정하지 않으면 자격 증명이 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-278">If this option is not set, no credentials are specified.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-279">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="a55f6-279">-SkipCACheck</span></span>

<span data-ttu-id="a55f6-280">HTTPS를 통해 연결할 때 클라이언트가 서버 인증서가 신뢰할 수 있는 CA (인증 기관)에 의해 서명 되었는지 확인 하지 않도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-280">Specifies that when it connects over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>

<span data-ttu-id="a55f6-281">이 옵션은 원격 컴퓨터가 물리적으로 안전하고 격리된 네트워크에 속해 있거나 원격 컴퓨터가 WinRM 구성에 신뢰할 수 있는 호스트로 나열되어 있는 경우와 같이 원격 컴퓨터를 다른 메커니즘으로 신뢰할 수 있는 경우에만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-281">Use this option only when the remote computer is trusted by using another mechanism, such as when the remote computer is part of a network that is physically secure and isolated or when the remote computer is listed as a trusted host in a WinRM configuration.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-282">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="a55f6-282">-SkipCNCheck</span></span>

<span data-ttu-id="a55f6-283">서버의 인증서 CN (일반 이름)이 서버의 호스트 이름과 일치할 필요가 없도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-283">Specifies that the certificate common name (CN) of the server does not have to match the host name of the server.</span></span> <span data-ttu-id="a55f6-284">이 옵션은 HTTPS 프로토콜을 사용하는 원격 작업에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-284">This option is used only in remote operations that use the HTTPS protocol.</span></span>

<span data-ttu-id="a55f6-285">신뢰할 수 있는 컴퓨터에 대해서만 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-285">Use this option only for trusted computers.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-286">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="a55f6-286">-SkipRevocationCheck</span></span>

<span data-ttu-id="a55f6-287">서버 인증서의 해지 상태를 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-287">Does not validate the revocation status of the server certificate.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-288">-UICulture</span><span class="sxs-lookup"><span data-stu-id="a55f6-288">-UICulture</span></span>

<span data-ttu-id="a55f6-289">세션에 사용할 UI 문화권을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-289">Specifies the UI culture to use for the session.</span></span>

<span data-ttu-id="a55f6-290">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-290">Valid values include:</span></span>

- <span data-ttu-id="a55f6-291">형식의 문화권 이름 `<languagecode2>-<country/regioncode2>` (예:) `ja-JP`</span><span class="sxs-lookup"><span data-stu-id="a55f6-291">A culture name in `<languagecode2>-<country/regioncode2>` format, such as `ja-JP`</span></span>
- <span data-ttu-id="a55f6-292">**CultureInfo** 개체를 포함 하는 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-292">A variable that contains a **CultureInfo** object</span></span>
- <span data-ttu-id="a55f6-293">**CultureInfo** 개체를 가져오는 명령 (예:)`Get-Culture`</span><span class="sxs-lookup"><span data-stu-id="a55f6-293">A command that gets a **CultureInfo** object, such as `Get-Culture`</span></span>

<span data-ttu-id="a55f6-294">기본값은 이며 `$null` , 세션을 만들 때 운영 체제에서 설정한 UI 문화권이 세션에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-294">The default value is `$null`, and the UI culture that is set in the operating system when the session is created is used in the session.</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a55f6-295">-UseUTF16</span><span class="sxs-lookup"><span data-stu-id="a55f6-295">-UseUTF16</span></span>

<span data-ttu-id="a55f6-296">이 cmdlet은 UTF8 형식 대신 UTF16 형식으로 요청을 인코드 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-296">Indicates that this cmdlet encodes the request in UTF16 format instead of UTF8 format.</span></span>

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

### <span data-ttu-id="a55f6-297">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a55f6-297">CommonParameters</span></span>

<span data-ttu-id="a55f6-298">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a55f6-298">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a55f6-299">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a55f6-299">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a55f6-300">입력</span><span class="sxs-lookup"><span data-stu-id="a55f6-300">INPUTS</span></span>

### <span data-ttu-id="a55f6-301">없음</span><span class="sxs-lookup"><span data-stu-id="a55f6-301">None</span></span>

<span data-ttu-id="a55f6-302">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-302">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a55f6-303">출력</span><span class="sxs-lookup"><span data-stu-id="a55f6-303">OUTPUTS</span></span>

### <span data-ttu-id="a55f6-304">System.object.. a p.</span><span class="sxs-lookup"><span data-stu-id="a55f6-304">System.Management.Automation.Remoting.PSSessionOption</span></span>

## <span data-ttu-id="a55f6-305">참고</span><span class="sxs-lookup"><span data-stu-id="a55f6-305">NOTES</span></span>

<span data-ttu-id="a55f6-306">명령에서 **Sessionoption** 매개 변수를 사용 하 여 **PSSession** 을 만드는 경우 세션 옵션은 기본 설정 변수의 속성 값에 의해 결정 됩니다 `$PSSessionOption` (설정 된 경우).</span><span class="sxs-lookup"><span data-stu-id="a55f6-306">If the **SessionOption** parameter is not used in a command to create a **PSSession** , the session options are determined by the property values of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="a55f6-307">변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a55f6-307">For more information about the `$PSSessionOption` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="a55f6-308">세션 구성 개체의 속성은 세션 구성에 대해 설정된 옵션과 해당 옵션 값에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-308">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="a55f6-309">또한 세션 구성 파일을 사용하는 세션 구성에는 추가 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a55f6-309">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="a55f6-310">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a55f6-310">RELATED LINKS</span></span>

[<span data-ttu-id="a55f6-311">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="a55f6-311">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="a55f6-312">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="a55f6-312">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="a55f6-313">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="a55f6-313">New-PSSession</span></span>](New-PSSession.md)
