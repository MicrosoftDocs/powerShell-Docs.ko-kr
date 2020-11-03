---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-wmiinstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WmiInstance
ms.openlocfilehash: 03288a2ffbef416937b2c92a7d08a5aed49ffb43
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214410"
---
# <span data-ttu-id="4e52d-103">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="4e52d-103">Set-WmiInstance</span></span>

## <span data-ttu-id="4e52d-104">개요</span><span class="sxs-lookup"><span data-stu-id="4e52d-104">SYNOPSIS</span></span>
<span data-ttu-id="4e52d-105">기존 WMI(Windows Management Instrumentation) 클래스의 인스턴스를 만들거나 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-105">Creates or updates an instance of an existing Windows Management Instrumentation (WMI) class.</span></span>

## <span data-ttu-id="4e52d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4e52d-106">SYNTAX</span></span>

### <span data-ttu-id="4e52d-107">클래스 (기본값)</span><span class="sxs-lookup"><span data-stu-id="4e52d-107">class (Default)</span></span>

```
Set-WmiInstance [-Class] <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4e52d-108">object</span><span class="sxs-lookup"><span data-stu-id="4e52d-108">object</span></span>

```
Set-WmiInstance -InputObject <ManagementObject> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4e52d-109">path</span><span class="sxs-lookup"><span data-stu-id="4e52d-109">path</span></span>

```
Set-WmiInstance -Path <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4e52d-110">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="4e52d-110">WQLQuery</span></span>

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4e52d-111">Query</span><span class="sxs-lookup"><span data-stu-id="4e52d-111">query</span></span>

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4e52d-112">list</span><span class="sxs-lookup"><span data-stu-id="4e52d-112">list</span></span>

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4e52d-113">설명</span><span class="sxs-lookup"><span data-stu-id="4e52d-113">DESCRIPTION</span></span>
<span data-ttu-id="4e52d-114">`Set-WmiInstance`Cmdlet은 기존 WMI(Windows Management Instrumentation) (WMI) 클래스의 인스턴스를 만들거나 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-114">The `Set-WmiInstance` cmdlet creates or updates an instance of an existing Windows Management Instrumentation (WMI) class.</span></span>
<span data-ttu-id="4e52d-115">만들거나 업데이트한 인스턴스는 WMI 리포지토리에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-115">The created or updated instance is written to the WMI repository.</span></span>

<span data-ttu-id="4e52d-116">Windows PowerShell 3.0에 도입된 새 CIM cmdlet은 WMI cmdlet과 동일한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-116">New CIM cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span>
<span data-ttu-id="4e52d-117">CIM cmdlet은 WSMan (WS-Management) 표준과 CIM(Common Information Model) (CIM) 표준을 준수 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-117">The CIM cmdlets comply with WS-Management (WSMan) standards and with the Common Information Model (CIM) standard.</span></span>
<span data-ttu-id="4e52d-118">이렇게 하면 cmdlet이 동일한 기술을 사용 하 여 Windows 기반 컴퓨터 및 다른 운영 체제를 실행 하는 컴퓨터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-118">this enables cmdlets to use the same techniques to manage Windows-based computers and those running other operating systems.</span></span>
<span data-ttu-id="4e52d-119">를 사용 하는 대신 `Set-WmiInstance` [Ciminstance 개체로](/powershell/module/cimcmdlets/set-ciminstance) 또는 [ciminstance 개체로](/powershell/module/cimcmdlets/new-ciminstance) cmdlet을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-119">Instead of using `Set-WmiInstance`, consider using the [Set-CimInstance](/powershell/module/cimcmdlets/set-ciminstance) or [New-CimInstance](/powershell/module/cimcmdlets/new-ciminstance) cmdlets.</span></span>

## <span data-ttu-id="4e52d-120">예제</span><span class="sxs-lookup"><span data-stu-id="4e52d-120">EXAMPLES</span></span>

### <span data-ttu-id="4e52d-121">예제 1: WMI 로깅 수준 설정</span><span class="sxs-lookup"><span data-stu-id="4e52d-121">Example 1: Set WMI logging level</span></span>

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2}
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
```

<span data-ttu-id="4e52d-122">이 명령은 WMI 로깅 수준을 2로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-122">This command sets the WMI logging level to 2.</span></span>
<span data-ttu-id="4e52d-123">이 명령은 인수 매개 변수에 설정 된 속성 및 값 쌍으로 간주 되는 값을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-123">The command passes the property to be set and the value, together considered a value pair, in the argument parameter.</span></span>
<span data-ttu-id="4e52d-124">매개 변수는 @{property = value} 생성으로 정의된 해시 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-124">The parameter takes a hash table that is defined by the @{property = value} construction.</span></span>
<span data-ttu-id="4e52d-125">반환된 클래스 정보에는 새 값이 반영됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-125">The class information that is returned reflects the new value.</span></span>

### <span data-ttu-id="4e52d-126">예제 2: 환경 변수 및 해당 값 만들기</span><span class="sxs-lookup"><span data-stu-id="4e52d-126">Example 2: Create an environment variable and its value</span></span>

```
PS C:\> Set-WmiInstance -Class win32_environment -Argument @{Name="testvar";VariableValue="testvalue";UserName="<SYSTEM>"}
__GENUS          : 2
__CLASS          : Win32_Environment
__SUPERCLASS     : CIM_SystemResource
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Environment.Name="testvar",UserName="<SYSTEM>"
__PROPERTY_COUNT : 8
__DERIVATION     : {CIM_SystemResource, CIM_LogicalElement, CIM_ManagedSystemElement}
__SERVER         : SYSTEM01
__NAMESPACE      : root\cimv2
__PATH           : \\SYSTEM01\root\cimv2:Win32_Environment.Name="testvar",UserName="<SYSTEM>"
Caption          : <SYSTEM>\testvar
Description      : <SYSTEM>\testvar
InstallDate      :
Name             : testvar
Status           : OK
SystemVariable   : True
UserName         : <SYSTEM>
VariableValue    : testvalue
```

<span data-ttu-id="4e52d-127">이 명령은 testvar 값을 가진 testvar 환경 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-127">This command creates the testvar environment variable that has the value testvalue.</span></span>
<span data-ttu-id="4e52d-128">**Win32_Environment** WMI 클래스의 새 인스턴스를 만들어이를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-128">It does this by creating a new instance of the **Win32_Environment** WMI class.</span></span>
<span data-ttu-id="4e52d-129">이 작업을 수행 하려면 적절 한 자격 증명이 필요 하며 새 환경 변수를 보기 위해 Windows PowerShell을 다시 시작 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-129">This operation requires appropriate credentials and that you may have to restart Windows PowerShell to see the new environment variable.</span></span>

### <span data-ttu-id="4e52d-130">예 3: 여러 원격 컴퓨터에 대 한 WMI 로깅 수준 설정</span><span class="sxs-lookup"><span data-stu-id="4e52d-130">Example 3: Set WMI logging level for several remote computers</span></span>

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2} -Computername "system01", "system02", "system03"
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
...
```

<span data-ttu-id="4e52d-131">이 명령은 WMI 로깅 수준을 2로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-131">This command sets the WMI logging level to 2.</span></span>
<span data-ttu-id="4e52d-132">이 명령은 인수 매개 변수에 설정 된 속성 및 값 쌍으로 간주 되는 값을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-132">The command passes the property to be set and the value, together considered a value pair, in the argument parameter.</span></span>
<span data-ttu-id="4e52d-133">매개 변수는 @{property = value} 생성으로 정의된 해시 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-133">The parameter takes a hash table that is defined by the @{property = value} construction.</span></span>
<span data-ttu-id="4e52d-134">반환된 클래스 정보에는 새 값이 반영됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-134">The returned class information reflects the new value.</span></span>

## <span data-ttu-id="4e52d-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4e52d-135">PARAMETERS</span></span>

### <span data-ttu-id="4e52d-136">-Arguments</span><span class="sxs-lookup"><span data-stu-id="4e52d-136">-Arguments</span></span>
<span data-ttu-id="4e52d-137">변경할 속성 이름과 해당 속성의 새 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-137">Specifies the name of the property to be changed and the new value for that property.</span></span>
<span data-ttu-id="4e52d-138">이름 및 값은 이름-값 쌍 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-138">The name and value must be a name-value pair.</span></span>
<span data-ttu-id="4e52d-139">이름-값 쌍은 명령줄에서 해시 테이블로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-139">The name-value pair is passed on the command line as a hash table.</span></span>
<span data-ttu-id="4e52d-140">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="4e52d-140">For example:</span></span>

`@{Setting1=1; Setting2=5; Setting3="test"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: class, object, path
Aliases: Args, Property

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e52d-141">-AsJob</span><span class="sxs-lookup"><span data-stu-id="4e52d-141">-AsJob</span></span>
<span data-ttu-id="4e52d-142">이 cmdket 백그라운드 작업으로 실행 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-142">Indicates that this cmdket runs as a background job.</span></span>
<span data-ttu-id="4e52d-143">이 매개 변수를 사용하여 마치는 데 시간이 많이 걸리는 명령을 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="4e52d-143">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="4e52d-144">*AsJob* 매개 변수를 지정 하면이 명령은 백그라운드 작업을 나타내는 개체를 반환한 다음 명령 프롬프트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-144">When you specify the *AsJob* parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span>
<span data-ttu-id="4e52d-145">작업을 마치는 동안 세션에서 작업을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-145">You can continue to work in the session while the job finishes.</span></span>
<span data-ttu-id="4e52d-146">원격 컴퓨터에 대해 **set-wmiinstance** 를 사용 하는 경우에는 로컬 컴퓨터에 작업이 생성 되 고 원격 컴퓨터의 결과가 로컬 컴퓨터에 자동으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-146">If **Set-WmiInstance** is used for a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="4e52d-147">작업을 관리 하려면 **job** 명사 ( **job** cmdlet)를 포함 하는 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-147">To manage the job, use the cmdlets that contain the **Job** noun (the **Job** cmdlets).</span></span>
<span data-ttu-id="4e52d-148">작업 결과를 가져오려면 Receive-Job cmdlet을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="4e52d-148">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="4e52d-149">이 매개 변수를 원격 컴퓨터와 함께 사용 하려면 원격 컴퓨터에 대 한 로컬 및 원격 컴퓨터를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-149">To use this parameter together with remote computers, the local and remote computers must be configured for remoting.</span></span>
<span data-ttu-id="4e52d-150">또한 windows Vista 이상 버전의 windows 운영 체제에서 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-150">Additionally, you must start Windows PowerShell by using the Run as administrator option in Windows Vista and later versions of the Windows operating system.</span></span>
<span data-ttu-id="4e52d-151">자세한 내용은 about_Remote_Requirements를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e52d-151">For more information, see about_Remote_Requirements.</span></span>

<span data-ttu-id="4e52d-152">Windows PowerShell 백그라운드 작업에 대 한 자세한 내용은 about_Jobs 및 about_Remote_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4e52d-152">For more information about Windows PowerShell background jobs, see about_Jobs and about_Remote_Jobs.</span></span>

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

### <span data-ttu-id="4e52d-153">-인증</span><span class="sxs-lookup"><span data-stu-id="4e52d-153">-Authentication</span></span>
<span data-ttu-id="4e52d-154">WMI 연결에 사용 해야 하는 인증 수준을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-154">Specifies the authentication level that must be used with the WMI connection.</span></span>
<span data-ttu-id="4e52d-155">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4e52d-156">-1: 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-156">-1: Unchanged.</span></span>
- <span data-ttu-id="4e52d-157">0: 기본값</span><span class="sxs-lookup"><span data-stu-id="4e52d-157">0: Default.</span></span>
- <span data-ttu-id="4e52d-158">1: 없음.</span><span class="sxs-lookup"><span data-stu-id="4e52d-158">1: None.</span></span>
<span data-ttu-id="4e52d-159">인증이 수행 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-159">No authentication in performed.</span></span>
- <span data-ttu-id="4e52d-160">2: 연결</span><span class="sxs-lookup"><span data-stu-id="4e52d-160">2: Connect.</span></span>
<span data-ttu-id="4e52d-161">인증은 클라이언트가 응용 프로그램과의 관계를 설정 하는 경우에만 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-161">Authentication is performed only when the client establishes a relationship with the application.</span></span>
- <span data-ttu-id="4e52d-162">3:를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-162">3: Call.</span></span>
<span data-ttu-id="4e52d-163">응용 프로그램에서 요청을 받으면 각 호출이 시작 될 때만 인증이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-163">Authentication is performed only at the start of each call when the application receives the request.</span></span>
- <span data-ttu-id="4e52d-164">4: 패킷.</span><span class="sxs-lookup"><span data-stu-id="4e52d-164">4: Packet.</span></span>
<span data-ttu-id="4e52d-165">클라이언트에서 수신 된 모든 데이터에 대해 인증이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-165">Authentication is performed on all the data that is received from the client.</span></span>
- <span data-ttu-id="4e52d-166">5: PacketIntegrity.</span><span class="sxs-lookup"><span data-stu-id="4e52d-166">5: PacketIntegrity.</span></span>
<span data-ttu-id="4e52d-167">클라이언트와 응용 프로그램 간에 전송 되는 모든 데이터는 인증 되 고 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-167">All the data that is transferred between the client and the application is authenticated and verified.</span></span>
- <span data-ttu-id="4e52d-168">6: PacketPrivacy.</span><span class="sxs-lookup"><span data-stu-id="4e52d-168">6: PacketPrivacy.</span></span>
<span data-ttu-id="4e52d-169">다른 인증 수준의 속성을 사용 하 고 모든 데이터를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-169">The properties of the other authentication levels are used, and all the data is encrypted.</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e52d-170">-Authority</span><span class="sxs-lookup"><span data-stu-id="4e52d-170">-Authority</span></span>
<span data-ttu-id="4e52d-171">WMI 연결을 인증하는 데 사용할 권한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-171">Specifies the authority to use to authenticate the WMI connection.</span></span>
<span data-ttu-id="4e52d-172">표준 NTLM 또는 Kerberos 인증을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-172">You can specify standard NTLM or Kerberos authentication.</span></span>
<span data-ttu-id="4e52d-173">NTLM을 사용하려면 권한 설정을 ntlmdomain:\<DomainName\>으로 설정합니다. 여기서 \<DomainName\>은 유효한 NTLM 도메인 이름을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-173">To use NTLM, set the authority setting to ntlmdomain:\<DomainName\>, where \<DomainName\> identifies a valid NTLM domain name.</span></span>
<span data-ttu-id="4e52d-174">Kerberos를 사용 하려면 kerberos를 지정 \<DomainName\> \\ \<ServerName\> 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-174">To use Kerberos, specify kerberos:\<DomainName\>\\\<ServerName\>.</span></span>
<span data-ttu-id="4e52d-175">로컬 컴퓨터에 연결하는 경우 권한 설정을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-175">You cannot include the authority setting when you connect to the local computer.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e52d-176">-클래스</span><span class="sxs-lookup"><span data-stu-id="4e52d-176">-Class</span></span>
<span data-ttu-id="4e52d-177">WMI 클래스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-177">Specifies the name of a WMI class.</span></span>

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e52d-178">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="4e52d-178">-ComputerName</span></span>
<span data-ttu-id="4e52d-179">이 cmdlet이 실행 되는 컴퓨터의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-179">Specifies the name of the computer on which this cmdlet runs.</span></span>
<span data-ttu-id="4e52d-180">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-180">The default is the local computer.</span></span>

<span data-ttu-id="4e52d-181">하나 이상 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="4e52d-181">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more computers.</span></span>
<span data-ttu-id="4e52d-182">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 (.) 또는 localhost를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-182">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="4e52d-183">이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-183">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="4e52d-184">원격 명령을 실행하도록 컴퓨터를 구성하지 않은 경우에도 *ComputerName* 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-184">You can use the *ComputerName* parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: class, path, WQLQuery, query, list
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e52d-185">-Credential</span><span class="sxs-lookup"><span data-stu-id="4e52d-185">-Credential</span></span>
<span data-ttu-id="4e52d-186">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-186">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="4e52d-187">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-187">The default is the current user.</span></span>

<span data-ttu-id="4e52d-188">User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나 **PSCredential** 개체 (예: Get-Credential cmdlet에 의해 생성 된 개체)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-188">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="4e52d-189">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-189">If you type a user name, this cmdlet prompts for a password.</span></span>

<span data-ttu-id="4e52d-190">이 매개 변수는 Windows PowerShell과 함께 설치 된 모든 공급자가 매개 변수와 함께 설치 된 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-190">This parameter is not supported by any providers installed with parameter is not supported by any providers installed with Windows PowerShell.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e52d-191">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="4e52d-191">-EnableAllPrivileges</span></span>
<span data-ttu-id="4e52d-192">이 cmdlet은 WMI 호출을 수행 하기 전에 현재 사용자의 모든 권한을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-192">Indicates that this cmdlet enables all the permissions of the current user before the command it makes the WMI call.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e52d-193">-가장</span><span class="sxs-lookup"><span data-stu-id="4e52d-193">-Impersonation</span></span>
<span data-ttu-id="4e52d-194">사용할 가장 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-194">Specifies the impersonation level to use.</span></span>
<span data-ttu-id="4e52d-195">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-195">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4e52d-196">0: 기본값</span><span class="sxs-lookup"><span data-stu-id="4e52d-196">0: Default.</span></span>
<span data-ttu-id="4e52d-197">기본 가장 수준에 대 한 로컬 레지스트리를 읽습니다. 일반적으로 3: Impersonate로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-197">Reads the local registry for the default impersonation level, which is usually set to 3: Impersonate.</span></span>
- <span data-ttu-id="4e52d-198">1: 익명.</span><span class="sxs-lookup"><span data-stu-id="4e52d-198">1: Anonymous.</span></span>
<span data-ttu-id="4e52d-199">호출자의 자격 증명을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-199">Hides the credentials of the caller.</span></span>
- <span data-ttu-id="4e52d-200">2:를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-200">2: Identify.</span></span>
<span data-ttu-id="4e52d-201">개체가 호출자의 자격 증명을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-201">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="4e52d-202">3: Impersonate</span><span class="sxs-lookup"><span data-stu-id="4e52d-202">3: Impersonate.</span></span>
<span data-ttu-id="4e52d-203">개체가 호출자의 자격 증명을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-203">Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="4e52d-204">4: 대리자.</span><span class="sxs-lookup"><span data-stu-id="4e52d-204">4: Delegate.</span></span>
<span data-ttu-id="4e52d-205">개체가 다른 개체가 호출자의 자격 증명을 사용하도록 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-205">Allows objects to permit other objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e52d-206">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4e52d-206">-InputObject</span></span>
<span data-ttu-id="4e52d-207">입력으로 사용할 **Managementobject** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-207">Specifies a **ManagementObject** object to use as input.</span></span>
<span data-ttu-id="4e52d-208">이 매개 변수를 사용 하는 경우 *Arguments* 매개 변수를 제외한 다른 모든 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-208">When this parameter is used, all other parameters ,except the *Arguments* parameter, are ignored.</span></span>

```yaml
Type: System.Management.ManagementObject
Parameter Sets: object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4e52d-209">-Locale</span><span class="sxs-lookup"><span data-stu-id="4e52d-209">-Locale</span></span>
<span data-ttu-id="4e52d-210">WMI 개체의 기본 설정 로캘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-210">Specifies the preferred locale for WMI objects.</span></span>
<span data-ttu-id="4e52d-211">*로캘* 매개 변수는 MS_ 형식의 배열에서 \<LCID\> 기본 순서로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-211">The *Locale* parameter is specified in an array in the MS_\<LCID\> format in the preferred order.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e52d-212">-Namespace</span><span class="sxs-lookup"><span data-stu-id="4e52d-212">-Namespace</span></span>
<span data-ttu-id="4e52d-213">*클래스* 매개 변수와 함께 사용 될 때 참조 된 wmi 클래스가 있는 wmi 리포지토리 네임 스페이스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-213">Specifies the WMI repository namespace where the referenced WMI class is located when it is used with the *Class* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e52d-214">-Path</span><span class="sxs-lookup"><span data-stu-id="4e52d-214">-Path</span></span>
<span data-ttu-id="4e52d-215">만들거나 업데이트 하려는 인스턴스의 WMI 개체 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-215">Specifies a WMI object path of the instance that you want to create or update.</span></span>

```yaml
Type: System.String
Parameter Sets: path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e52d-216">-PutType</span><span class="sxs-lookup"><span data-stu-id="4e52d-216">-PutType</span></span>
<span data-ttu-id="4e52d-217">WMI 인스턴스를 만들지 또는 업데이트할지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-217">Indicates whether to create or update the WMI instance.</span></span>
<span data-ttu-id="4e52d-218">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-218">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4e52d-219">UpdateOnly.</span><span class="sxs-lookup"><span data-stu-id="4e52d-219">UpdateOnly.</span></span>
<span data-ttu-id="4e52d-220">기존 WMI 인스턴스를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-220">Updates an existing WMI instance.</span></span>
- <span data-ttu-id="4e52d-221">CreateOnly.</span><span class="sxs-lookup"><span data-stu-id="4e52d-221">CreateOnly.</span></span>
<span data-ttu-id="4e52d-222">새 WMI 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-222">Creates a new WMI instance.</span></span>
- <span data-ttu-id="4e52d-223">UpdateOrCreate.</span><span class="sxs-lookup"><span data-stu-id="4e52d-223">UpdateOrCreate.</span></span>
<span data-ttu-id="4e52d-224">WMI 인스턴스가 있을 경우 업데이트하고 인스턴스가 없을 경우 새 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-224">Updates the WMI instance if it exists or creates a new instance if an instance does not exist.</span></span>

```yaml
Type: System.Management.PutType
Parameter Sets: (All)
Aliases:
Accepted values: None, UpdateOnly, CreateOnly, UpdateOrCreate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e52d-225">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="4e52d-225">-ThrottleLimit</span></span>
<span data-ttu-id="4e52d-226">이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-226">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="4e52d-227">이 매개 변수는 *AsJob* 매개 변수와 함께 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-227">This parameter is used together with the *AsJob* parameter.</span></span>
<span data-ttu-id="4e52d-228">제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-228">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="4e52d-229">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4e52d-229">-Confirm</span></span>
<span data-ttu-id="4e52d-230">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-230">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e52d-231">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4e52d-231">-WhatIf</span></span>
<span data-ttu-id="4e52d-232">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-232">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4e52d-233">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-233">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e52d-234">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4e52d-234">CommonParameters</span></span>
<span data-ttu-id="4e52d-235">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4e52d-235">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4e52d-236">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e52d-236">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4e52d-237">입력</span><span class="sxs-lookup"><span data-stu-id="4e52d-237">INPUTS</span></span>

### <span data-ttu-id="4e52d-238">없음</span><span class="sxs-lookup"><span data-stu-id="4e52d-238">None</span></span>
<span data-ttu-id="4e52d-239">이 cmdlet은 입력을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-239">This cmdlet does not accept input.</span></span>

## <span data-ttu-id="4e52d-240">출력</span><span class="sxs-lookup"><span data-stu-id="4e52d-240">OUTPUTS</span></span>

### <span data-ttu-id="4e52d-241">없음</span><span class="sxs-lookup"><span data-stu-id="4e52d-241">None</span></span>
<span data-ttu-id="4e52d-242">이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4e52d-242">This cmdlet does not generate output.</span></span>

## <span data-ttu-id="4e52d-243">참고</span><span class="sxs-lookup"><span data-stu-id="4e52d-243">NOTES</span></span>

## <span data-ttu-id="4e52d-244">관련 링크</span><span class="sxs-lookup"><span data-stu-id="4e52d-244">RELATED LINKS</span></span>

[<span data-ttu-id="4e52d-245">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="4e52d-245">Get-WmiObject</span></span>](Get-WmiObject.md)

[<span data-ttu-id="4e52d-246">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="4e52d-246">Invoke-WmiMethod</span></span>](Invoke-WmiMethod.md)

[<span data-ttu-id="4e52d-247">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="4e52d-247">Remove-WmiObject</span></span>](Remove-WmiObject.md)
