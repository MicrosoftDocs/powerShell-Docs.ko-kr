---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pstransportoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSTransportOption
ms.openlocfilehash: fa19ee7d1856eee91a6b1d6a8352017457031202
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605221"
---
# <span data-ttu-id="25a0f-102">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="25a0f-102">New-PSTransportOption</span></span>

## <span data-ttu-id="25a0f-103">개요</span><span class="sxs-lookup"><span data-stu-id="25a0f-103">SYNOPSIS</span></span>
<span data-ttu-id="25a0f-104">세션 구성에 대한 고급 옵션을 포함하는 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-104">Creates an object that contains advanced options for a session configuration.</span></span>

## <span data-ttu-id="25a0f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="25a0f-105">SYNTAX</span></span>

```
New-PSTransportOption [-MaxIdleTimeoutSec <Int32>] [-ProcessIdleTimeoutSec <Int32>] [-MaxSessions <Int32>]
 [-MaxConcurrentCommandsPerSession <Int32>] [-MaxSessionsPerUser <Int32>] [-MaxMemoryPerSessionMB <Int32>]
 [-MaxProcessesPerSession <Int32>] [-MaxConcurrentUsers <Int32>] [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [<CommonParameters>]
```

## <span data-ttu-id="25a0f-106">설명</span><span class="sxs-lookup"><span data-stu-id="25a0f-106">DESCRIPTION</span></span>

<span data-ttu-id="25a0f-107">**New-PSTransportOption** cmdlet은 세션 구성에 대한 전송 옵션을 포함하는 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-107">The **New-PSTransportOption** cmdlet creates an object that contains transport options for session configurations.</span></span>
<span data-ttu-id="25a0f-108">Register-PSSessionConfiguration 및 Set-PSSessionConfiguration cmdlet과 같은 세션 구성을 만들거나 변경  하는 cmdlet의 값으로 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-108">You can use the object as the value of the *TransportOption* parameter of cmdlets that create or change a session configuration, such as the Register-PSSessionConfiguration and Set-PSSessionConfiguration cmdlets.</span></span>

<span data-ttu-id="25a0f-109">WSMan: 드라이브에서 세션 구성 속성 값을 편집하여 전송 옵션 설정을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-109">You can also change the transport option settings by editing the values of the session configuration properties in the WSMan: drive.</span></span>
<span data-ttu-id="25a0f-110">자세한 내용은 WSMan 공급자를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="25a0f-110">For more information, see WSMan Provider.</span></span>

<span data-ttu-id="25a0f-111">세션 구성 옵션은 서버 쪽 또는 원격 연결의 수신 끝에서 설정 된 세션 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-111">The session configuration options represent the session values set on the server-side, or receiving end of a remote connection.</span></span>
<span data-ttu-id="25a0f-112">세션을 만들 때 또는 클라이언트에서 세션의 연결을 끊거나 세션에 다시 연결할 때 클라이언트 쪽 또는 연결의 송신 끝에서 세션 옵션 값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-112">The client-side, or sending end of the connection, can set session option values when the session is created, or when the client disconnects from or reconnects to the session.</span></span>
<span data-ttu-id="25a0f-113">달리 명시되지 않은 한 설정 값이 충돌할 경우 클라이언트 쪽 값이 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-113">Unless stated otherwise, when the setting values conflict, the client-side values take precedence.</span></span>
<span data-ttu-id="25a0f-114">그러나 클라이언트 쪽 값은 세션 구성에서 설정된 최대값 및 할당량을 위반할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-114">However, the client-side values cannot violate maximum values and quotas set in the session configuration.</span></span>

<span data-ttu-id="25a0f-115">매개 변수가 없으면 **new-pstransportoption** 는 모든 옵션에 대해 null 값을 갖는 전송 옵션 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-115">Without parameters, **New-PSTransportOption** generates a transport option object that has null values for all of the options.</span></span>
<span data-ttu-id="25a0f-116">매개 변수를 생략하면 해당 매개 변수가 나타내는 개체의 속성 값은 null이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-116">If you omit a parameter, the object has a null value for the property that the parameter represents.</span></span>
<span data-ttu-id="25a0f-117">Null 값은 세션 구성에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-117">A null value does not affect the session configuration.</span></span>

<span data-ttu-id="25a0f-118">세션 옵션에 대 한 자세한 내용은 New-PSSessionOption을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="25a0f-118">For more information about session options, see New-PSSessionOption.</span></span>
<span data-ttu-id="25a0f-119">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="25a0f-119">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="25a0f-120">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="25a0f-121">예제</span><span class="sxs-lookup"><span data-stu-id="25a0f-121">EXAMPLES</span></span>

### <span data-ttu-id="25a0f-122">예제 1: 기본 전송 옵션 생성</span><span class="sxs-lookup"><span data-stu-id="25a0f-122">Example 1: Generate a default transport option</span></span>

```powershell
New-PSTransportOption
```

```Output
ProcessIdleTimeoutSec           :
MaxIdleTimeoutSec               :
MaxSessions                     :
MaxConcurrentCommandsPerSession :
MaxSessionsPerUser              :
MaxMemoryPerSessionMB           :
MaxProcessesPerSession          :
MaxConcurrentUsers              :
IdleTimeoutSec                  :
OutputBufferingMode             :
```

<span data-ttu-id="25a0f-123">이 명령은 매개 변수 없이 **new-pstransportoption** 를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-123">This command runs the **New-PSTransportOption** without parameters.</span></span>
<span data-ttu-id="25a0f-124">출력은 cmdlet에서 모든 속성에 대해 null 값을 갖는 전송 옵션 개체를 생성 함을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-124">The output shows that the cmdlet generates a transport option object that has null values for all properties.</span></span>

### <span data-ttu-id="25a0f-125">예제 2: 세션 구성 옵션 가져오기</span><span class="sxs-lookup"><span data-stu-id="25a0f-125">Example 2: Get session configuration options</span></span>

<span data-ttu-id="25a0f-126">이 예제에서는 전송 옵션 개체를 사용 하 여 세션 구성 옵션을 설정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-126">This example shows how to use a transport options object to set session configuration options.</span></span>

```powershell
$t = New-PSTransportOption -MaxSessions 40
Register-PSSessionConfiguration -Name ITTasks -TransportOption $t
Get-PSSessionConfiguration -Name ITTasks | Format-List -Property *
```

```Output
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITTasks
MaxConcurrentCommandsPerShell : 1000
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 40
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 2
Name                          : ITTasks
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
Enabled                       : True
MaxShellsPerUser              : 25
Permission                    :
```

<span data-ttu-id="25a0f-127">첫 번째 명령은 **New-PSTransportOption** cmdlet을 사용하여 전송 옵션 개체를 만든 다음 $t 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-127">The first command uses the **New-PSTransportOption** cmdlet to create a transport options object, which it saves in the $t variable.</span></span> <span data-ttu-id="25a0f-128">*MaxSessions* 매개 변수를 사용하여 최대 세션 수를 40으로 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-128">The command uses the *MaxSessions* parameter to increase the maximum number of sessions to 40.</span></span>

<span data-ttu-id="25a0f-129">두 번째 명령은 **Register-PSSessionConfiguration** cmdlet을 사용하여 ITTasks 세션 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-129">The second command uses the **Register-PSSessionConfiguration** cmdlet create the ITTasks session configuration.</span></span> <span data-ttu-id="25a0f-130">*TransportOption* 매개 변수를 사용하여 $t 변수의 전송 옵션 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-130">The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.</span></span>

<span data-ttu-id="25a0f-131">세 번째 명령은 Get-PSSessionConfiguration cmdlet을 사용 하 여 ITTasks 세션 구성을 가져오고 Format-List cmdlet을 사용 하 여 세션 구성 개체의 모든 속성을 목록으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-131">The third command uses the Get-PSSessionConfiguration cmdlet to get the ITTasks session configurations and the Format-List cmdlet to display all of the properties of the session configuration object in a list.</span></span> <span data-ttu-id="25a0f-132">출력은 세션 구성의 **MaxShells** 속성 값이 40임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-132">The output shows that the value of the **MaxShells** property of the session configuration is 40.</span></span>

### <span data-ttu-id="25a0f-133">예 3: 전송 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="25a0f-133">Example 3: Setting a transport option</span></span>

<span data-ttu-id="25a0f-134">이 명령은 세션 구성에서 전송 옵션을 설정할 경우 세션 구성을 사용하는 세션에 미치는 영향을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-134">This command shows the effect of setting a transport option in a session configuration on the sessions that use the session configuration.</span></span>

```powershell
$t = New-PSTransportOption -IdleTimeoutSec 3600
Set-PSSessionConfiguration -Name ITTasks -TransportOption $t
$s = New-PSSession -Name MyITTasks -ConfigurationName ITTasks
$s | Format-List -Property *
```

```Output
State                  : Opened
IdleTimeout            : 3600000
OutputBufferingMode    : Block
ComputerName           : localhost
ConfigurationName      : ITTasks
InstanceId             : 4110c3f5-68ea-40fa-9bbf-04a433dbb02d
Id                     : 1
Name                   : MyITTasks
Availability           : Available
ApplicationPrivateData : {PSVersionTable}
Runspace               : System.Management.Automation.RemoteRunspace
```

<span data-ttu-id="25a0f-135">첫 번째 명령은 **New-PSTransportOption** cmdlet을 사용하여 전송 옵션 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-135">The first command uses the **New-PSTransportOption** cmdlet to create a transport option object.</span></span> <span data-ttu-id="25a0f-136">*IdleTimeoutSec* 매개 변수를 사용하여 개체의 **IdleTimeoutSec** 속성 값을 1시간(3600초)으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-136">The command uses the *IdleTimeoutSec* parameter to set the **IdleTimeoutSec** property value of the object to one hour (3600 seconds).</span></span> <span data-ttu-id="25a0f-137">이 명령은 전송 옵션 개체를 $t 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-137">The command saves the transport objects object in the $t variable.</span></span>

<span data-ttu-id="25a0f-138">두 번째 명령은 Set-PSSessionConfiguration cmdlet을 사용 하 여 ITTasks 세션 구성의 전송 옵션을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-138">The second command uses the Set-PSSessionConfiguration cmdlet to change the transport options of the ITTasks session configuration.</span></span> <span data-ttu-id="25a0f-139">*TransportOption* 매개 변수를 사용하여 $t 변수의 전송 옵션 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-139">The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.</span></span>

<span data-ttu-id="25a0f-140">세 번째 명령은 New-PSSession cmdlet을 사용 하 여 로컬 컴퓨터에서 MyITTasks 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-140">The third command uses the New-PSSession cmdlet to create the MyITTasks session on the local computer.</span></span> <span data-ttu-id="25a0f-141">**ConfigurationName** 속성을 사용하여 ITTasks 세션 구성을 지정한 다음</span><span class="sxs-lookup"><span data-stu-id="25a0f-141">The command uses the **ConfigurationName** property to specify the ITTasks session configuration.</span></span> <span data-ttu-id="25a0f-142">이 명령은 세션을 $s 변수에 저장 합니다. 이 명령은 **New-PSSession** 의 *sessionoption* 매개 변수를 사용 하 여 세션에 대 한 사용자 지정 유휴 시간 제한 시간을 설정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-142">The command saves the session in the $s variable.Notice that the command does not use the *SessionOption* parameter of **New-PSSession** to set a custom idle time-out for the session.</span></span> <span data-ttu-id="25a0f-143">이 경우 세션 옵션에서 설정 된 유휴 시간 제한 값이 세션 구성의 유휴 시간 제한 설정 보다 우선 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-143">If it did, the idle time-out value set in the session option would take precedence over the idle time-out set in the session configuration.</span></span>

<span data-ttu-id="25a0f-144">네 번째 명령은 Format-List cmdlet을 사용 하 여 세션의 모든 속성을 목록에 있는 $s 변수에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-144">The fourth command uses the Format-List cmdlet to display all properties of the session in the $s variable in a list.</span></span> <span data-ttu-id="25a0f-145">출력은 세션의 유휴 시간 제한이 1 시간 (36만 밀리초) 임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-145">The output shows that the session has an idle time-out of one hour (360,000 milliseconds).</span></span>

## <span data-ttu-id="25a0f-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="25a0f-146">PARAMETERS</span></span>

### <span data-ttu-id="25a0f-147">-IdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="25a0f-147">-IdleTimeoutSec</span></span>

<span data-ttu-id="25a0f-148">원격 컴퓨터가 로컬 컴퓨터의 통신을 받지 못하는 경우 각 세션이 열려 있는 기간을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-148">Determines how long each session stays open if the remote computer does not receive any communication from the local computer.</span></span>
<span data-ttu-id="25a0f-149">하트 비트 신호를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-149">This includes the heartbeat signal.</span></span>
<span data-ttu-id="25a0f-150">간격이 만료되면 세션이 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-150">When the interval expires, the session closes.</span></span>

<span data-ttu-id="25a0f-151">유휴 시간 제한 값은 사용자가 세션에서 연결을 끊고 다시 연결 하려는 경우에 매우 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-151">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="25a0f-152">사용자는 세션이 시간 초과되지 않은 경우에만 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-152">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="25a0f-153">*IdleTimeoutSec* 매개 변수는 세션 구성의 **IdleTimeoutMs** 속성에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-153">The *IdleTimeoutSec* parameter corresponds to the **IdleTimeoutMs** property of a session configuration.</span></span>

<span data-ttu-id="25a0f-154">값을 초 단위로 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="25a0f-154">Enter a value in seconds.</span></span>
<span data-ttu-id="25a0f-155">기본값은 7200(2시간)입니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-155">The default value is 7200 (2 hours).</span></span>
<span data-ttu-id="25a0f-156">최소값은 60 (1 분)입니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-156">The minimum value is 60 (1 minute).</span></span>
<span data-ttu-id="25a0f-157">Maximum은 WSMan 구성에서 Shell 개체의 **IdleTimeout** 속성 값 ( `WSMan:\\\<ComputerName\>\Shell\IdleTimeout` )입니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-157">The maximum is the value of the **IdleTimeout** property of Shell objects in the WSMan configuration (`WSMan:\\\<ComputerName\>\Shell\IdleTimeout`).</span></span>
<span data-ttu-id="25a0f-158">기본값은 7200000밀리초(2시간)입니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-158">The default value is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="25a0f-159">세션 옵션 및 세션 구성에 유휴 시간 제한 값이 설정 된 경우 세션 옵션에 설정 된 값이 우선 하지만 세션 구성의 **MaxIdleTimeoutMs** 속성 값을 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-159">If an idle time-out value is set in the session options and in the session configuration, value set in the session options takes precedence, but it cannot exceed the value of the **MaxIdleTimeoutMs** property of the session configuration.</span></span>
<span data-ttu-id="25a0f-160">**MaxIdleTimeoutMs** 속성 값을 설정하려면 *MaxIdleTimeoutSec* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-160">To set the value of the **MaxIdleTimeoutMs** property, use the *MaxIdleTimeoutSec* parameter.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25a0f-161">-Idletimeoutsec</span><span class="sxs-lookup"><span data-stu-id="25a0f-161">-MaxConcurrentCommandsPerSession</span></span>

<span data-ttu-id="25a0f-162">각 세션에서 동시에 실행할 수 있는 명령 수를 지정 된 값으로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-162">Limits the number of commands that can run at the same time in each session to the specified value.</span></span>
<span data-ttu-id="25a0f-163">기본값은 1000입니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-163">The default value is 1000.</span></span>

<span data-ttu-id="25a0f-164">*Idletimeoutsec* 매개 변수는 세션 구성의 **idletimeoutms** 속성에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-164">The *MaxConcurrentCommandsPerSession* parameter corresponds to the **MaxConcurrentCommandsPerShell** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25a0f-165">-MaxConcurrentUsers</span><span class="sxs-lookup"><span data-stu-id="25a0f-165">-MaxConcurrentUsers</span></span>

<span data-ttu-id="25a0f-166">각 세션에서 동시에 명령을 실행할 수 있는 사용자 수를 지정 된 값으로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-166">Limits the number of users who can run commands at the same time in each session to the specified value.</span></span>
<span data-ttu-id="25a0f-167">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-167">The default value is 5.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25a0f-168">-MaxIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="25a0f-168">-MaxIdleTimeoutSec</span></span>

<span data-ttu-id="25a0f-169">각 세션에 대 한 유휴 제한 시간 집합을 지정 된 값으로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-169">Limits the idle time-out set for each session to the specified value.</span></span>
<span data-ttu-id="25a0f-170">기본값은 \[ Int \] :: int32.maxvalue (~ 25 일)입니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-170">The default value is \[Int\]::MaxValue (~25 days).</span></span>

<span data-ttu-id="25a0f-171">유휴 시간 제한 값은 사용자가 세션에서 연결을 끊고 다시 연결 하려는 경우에 매우 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-171">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="25a0f-172">사용자는 세션이 시간 초과되지 않은 경우에만 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-172">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="25a0f-173">*MaxIdleTimeoutSec* 매개 변수는 세션 구성의 **MaxIdleTimeoutMs** 속성에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-173">The *MaxIdleTimeoutSec* parameter corresponds to the **MaxIdleTimeoutMs** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25a0f-174">-MaxMemoryPerSessionMB</span><span class="sxs-lookup"><span data-stu-id="25a0f-174">-MaxMemoryPerSessionMB</span></span>

<span data-ttu-id="25a0f-175">각 세션에서 사용하는 메모리를 지정된 값으로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-175">Limits the memory used by each session to the specified value.</span></span>
<span data-ttu-id="25a0f-176">값을 메가바이트 단위로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-176">Enter a value in megabytes.</span></span>
<span data-ttu-id="25a0f-177">기본값은 1024메가바이트(1GB)입니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-177">The default value is 1024 megabytes (1 GB).</span></span>

<span data-ttu-id="25a0f-178">*&lt;system&gt;IdleTimeoutSec&lt;/system&gt;* 매개 변수는 세션 구성의 **&lt;system&gt;IdleTimeoutMs&lt;/system&gt;** 속성에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-178">The *MaxMemoryPerSessionMB* parameter corresponds to the **MaxMemoryPerShellMB** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25a0f-179">-MaxProcessesPerSession</span><span class="sxs-lookup"><span data-stu-id="25a0f-179">-MaxProcessesPerSession</span></span>

<span data-ttu-id="25a0f-180">각 세션에서 실행되는 프로세스 수를 지정된 값으로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-180">Limits the number of processes running in each session to the specified value.</span></span>
<span data-ttu-id="25a0f-181">기본값은 15입니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-181">The default value is 15.</span></span>

<span data-ttu-id="25a0f-182">*MaxProcessesPerSession* 매개 변수는 세션 구성의 **MaxProcessesPerShell** 속성에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-182">The *MaxProcessesPerSession* parameter corresponds to the **MaxProcessesPerShell** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25a0f-183">-MaxSessions</span><span class="sxs-lookup"><span data-stu-id="25a0f-183">-MaxSessions</span></span>

<span data-ttu-id="25a0f-184">세션 구성을 사용하는 세션 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-184">Limits the number of sessions that use the session configuration.</span></span>
<span data-ttu-id="25a0f-185">기본값은 25입니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-185">The default value is 25.</span></span>

<span data-ttu-id="25a0f-186">*MaxSessions* 매개 변수는 세션 구성의 **maxshells** 속성에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-186">The *MaxSessions* parameter corresponds to the **MaxShells** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25a0f-187">-MaxSessionsPerUser</span><span class="sxs-lookup"><span data-stu-id="25a0f-187">-MaxSessionsPerUser</span></span>

<span data-ttu-id="25a0f-188">세션 구성을 사용하고 지정된 사용자의 자격 증명으로 실행되는 세션 수를 지정된 값으로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-188">Limits the number of sessions that use the session configuration and run with the credentials of a given user to the specified value.</span></span>
<span data-ttu-id="25a0f-189">기본값은 25입니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-189">The default value is 25.</span></span>

<span data-ttu-id="25a0f-190">이 값을 지정 하는 경우 많은 사용자가 실행 사용자의 자격 증명을 사용 하 고 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-190">When you specify this value, consider that many users might be using the credentials of a run as user.</span></span>

<span data-ttu-id="25a0f-191">*Maxsessionsperuser* 매개 변수는 세션 구성의 **maxsessionsperuser** 속성에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-191">The *MaxSessionsPerUser* parameter corresponds to the **MaxShellsPerUser** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25a0f-192">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="25a0f-192">-OutputBufferingMode</span></span>

<span data-ttu-id="25a0f-193">출력 버퍼가 가득 찰 경우 연결이 끊긴 세션에서 명령 출력을 관리하는 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-193">Determines how command output is managed in disconnected sessions when the output buffer becomes full.</span></span>
<span data-ttu-id="25a0f-194">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-194">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="25a0f-195">차단.</span><span class="sxs-lookup"><span data-stu-id="25a0f-195">Block.</span></span>
<span data-ttu-id="25a0f-196">출력 버퍼가 가득 찰 경우 버퍼를 지울 때까지 실행이 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-196">When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="25a0f-197">Drop.</span><span class="sxs-lookup"><span data-stu-id="25a0f-197">Drop.</span></span>
<span data-ttu-id="25a0f-198">출력 버퍼가 가득 차도 실행이 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-198">When the output buffer is full, execution continues.</span></span>
<span data-ttu-id="25a0f-199">새 출력이 저장되면 가장 오래된 출력을 버립니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-199">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="25a0f-200">없음</span><span class="sxs-lookup"><span data-stu-id="25a0f-200">None.</span></span>
<span data-ttu-id="25a0f-201">출력 버퍼링 모드를 지정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-201">No output buffering mode is specified.</span></span>

<span data-ttu-id="25a0f-202">Sessions의 **OutputBufferingMode** 속성 기본값은 Block입니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-202">The default value of the **OutputBufferingMode** property of sessions is Block.</span></span>

```yaml
Type: System.Nullable`1[System.Management.Automation.Runspaces.OutputBufferingMode]
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25a0f-203">-ProcessIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="25a0f-203">-ProcessIdleTimeoutSec</span></span>

<span data-ttu-id="25a0f-204">각 호스트 프로세스에 대 한 제한 시간을 지정 된 값으로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-204">Limits the time-out for each host process to the specified value.</span></span>
<span data-ttu-id="25a0f-205">기본값 0은 프로세스에 대 한 시간 제한 값이 없음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-205">The default value, 0, means that there is no time-out value for the process.</span></span>

<span data-ttu-id="25a0f-206">다른 세션 구성에는 프로세스별 시간 제한 값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-206">Other session configurations have per-process time-out values.</span></span>
<span data-ttu-id="25a0f-207">예를 들어, **Microsoft PowerShell 워크플로** 세션 구성에는 프로세스별 시간 제한 값 28800 초 (8 시간)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-207">For example, the **Microsoft.PowerShell.Workflow** session configuration has a per-process time-out value of 28800 seconds (8 hours).</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25a0f-208">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="25a0f-208">CommonParameters</span></span>

<span data-ttu-id="25a0f-209">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="25a0f-209">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="25a0f-210">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25a0f-210">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="25a0f-211">입력</span><span class="sxs-lookup"><span data-stu-id="25a0f-211">INPUTS</span></span>

### <span data-ttu-id="25a0f-212">없음</span><span class="sxs-lookup"><span data-stu-id="25a0f-212">None</span></span>

<span data-ttu-id="25a0f-213">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-213">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="25a0f-214">출력</span><span class="sxs-lookup"><span data-stu-id="25a0f-214">OUTPUTS</span></span>

### <span data-ttu-id="25a0f-215">Microsoft. PowerShell. WSManConfigurationOption</span><span class="sxs-lookup"><span data-stu-id="25a0f-215">Microsoft.PowerShell.Commands.WSManConfigurationOption</span></span>

## <span data-ttu-id="25a0f-216">참고</span><span class="sxs-lookup"><span data-stu-id="25a0f-216">NOTES</span></span>

- <span data-ttu-id="25a0f-217">세션 구성 개체의 속성은 세션 구성에 대해 설정된 옵션과 해당 옵션 값에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-217">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="25a0f-218">또한 세션 구성 파일을 사용하는 세션 구성에는 추가 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a0f-218">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="25a0f-219">관련 링크</span><span class="sxs-lookup"><span data-stu-id="25a0f-219">RELATED LINKS</span></span>

[<span data-ttu-id="25a0f-220">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="25a0f-220">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="25a0f-221">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="25a0f-221">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="25a0f-222">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="25a0f-222">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="25a0f-223">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="25a0f-223">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

