---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-wmimethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WmiMethod
ms.openlocfilehash: e9743488e86429e5cc3252162e51268a7978b79d
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2020
ms.locfileid: "93217993"
---
# <span data-ttu-id="51c77-103">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="51c77-103">Invoke-WmiMethod</span></span>

## <span data-ttu-id="51c77-104">개요</span><span class="sxs-lookup"><span data-stu-id="51c77-104">SYNOPSIS</span></span>
<span data-ttu-id="51c77-105">WMI 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-105">Calls WMI methods.</span></span>

## <span data-ttu-id="51c77-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="51c77-106">SYNTAX</span></span>

### <span data-ttu-id="51c77-107">클래스 (기본값)</span><span class="sxs-lookup"><span data-stu-id="51c77-107">class (Default)</span></span>

```
Invoke-WmiMethod [-Class] <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="51c77-108">object</span><span class="sxs-lookup"><span data-stu-id="51c77-108">object</span></span>

```
Invoke-WmiMethod -InputObject <ManagementObject> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="51c77-109">path</span><span class="sxs-lookup"><span data-stu-id="51c77-109">path</span></span>

```
Invoke-WmiMethod -Path <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="51c77-110">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="51c77-110">WQLQuery</span></span>

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="51c77-111">Query</span><span class="sxs-lookup"><span data-stu-id="51c77-111">query</span></span>

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="51c77-112">list</span><span class="sxs-lookup"><span data-stu-id="51c77-112">list</span></span>

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="51c77-113">설명</span><span class="sxs-lookup"><span data-stu-id="51c77-113">DESCRIPTION</span></span>

<span data-ttu-id="51c77-114">`Invoke-WmiMethod`Cmdlet은 WMI (WMI(Windows Management Instrumentation)) 개체의 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-114">The `Invoke-WmiMethod` cmdlet calls the methods of Windows Management Instrumentation (WMI) objects.</span></span>

<span data-ttu-id="51c77-115">Windows PowerShell 3.0에 도입 된 새로운 CIM(Common Information Model) (CIM) cmdlet은 WMI cmdlet과 동일한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-115">New Common Information Model (CIM) cmdlets, introduced in Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span> <span data-ttu-id="51c77-116">CIM cmdlet은 WSMan (WS-Management) 표준과 CIM 표준을 준수 하 여 cmdlet이 동일한 기술을 사용 하 여 Windows 컴퓨터 및 다른 운영 체제를 실행 하는 운영 체제를 관리할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-116">The CIM cmdlets comply with WS-Management (WSMan) standards and with the CIM standard, which enables the cmdlets to use the same techniques to manage Windows computers and those running other operating systems.</span></span> <span data-ttu-id="51c77-117">를 사용 하는 대신 `Invoke-WmiMethod` [invoke-cimmethod](../cimcmdlets/invoke-cimmethod.md)를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-117">Instead of using `Invoke-WmiMethod`, consider using [Invoke-CimMethod](../cimcmdlets/invoke-cimmethod.md).</span></span>

## <span data-ttu-id="51c77-118">예제</span><span class="sxs-lookup"><span data-stu-id="51c77-118">EXAMPLES</span></span>

### <span data-ttu-id="51c77-119">예제 1: WMI 개체의 필수 순서 나열</span><span class="sxs-lookup"><span data-stu-id="51c77-119">Example 1: List the required order of WMI objects</span></span>

```powershell
([wmiclass]'Win32_Volume').GetMethodParameters('Format')
```

```Output
__GENUS           : 2
__CLASS           : __PARAMETERS
__SUPERCLASS      :
__DYNASTY         : __PARAMETERS
__RELPATH         :
__PROPERTY_COUNT  : 6
__DERIVATION      : {}
__SERVER          :
__NAMESPACE       :
__PATH            :
ClusterSize       : 0
EnableCompression : False
FileSystem        : NTFS
Label             :
QuickFormat       : False
Version           : 0
PSComputerName    :
```

<span data-ttu-id="51c77-120">이 명령은 개체의 필요한 순서를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-120">This command lists the required order of the objects.</span></span> <span data-ttu-id="51c77-121">PowerShell 3.0에서의 WMI 호출은 다른 메서드와 다르며, 개체 값을 특정 순서로 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-121">To invoke WMI in PowerShell 3.0 differs from alternate methods, and requires that object values are entered in a specific order.</span></span>

### <span data-ttu-id="51c77-122">예제 2: 응용 프로그램의 인스턴스 시작</span><span class="sxs-lookup"><span data-stu-id="51c77-122">Example 2: Start an instance of an application</span></span>

```powershell
([Wmiclass]'Win32_Process').GetMethodParameters('Create')
```

```Output
__GENUS                   : 2
__CLASS                   : __PARAMETERS
__SUPERCLASS              :
__DYNASTY                 : __PARAMETERS
__RELPATH                 :
__PROPERTY_COUNT          : 3
__DERIVATION              : {}
__SERVER                  :
__NAMESPACE               :
__PATH                    :
CommandLine               :
CurrentDirectory          :
ProcessStartupInformation :
PSComputerName            :
```

```powershell
Invoke-WmiMethod -Path win32_process -Name create -ArgumentList notepad.exe
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 2
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ProcessId        : 11312
ReturnValue      : 0
PSComputerName   :
```

<span data-ttu-id="51c77-123">이 명령은 `Create` **Win32_Process** 클래스의 메서드를 호출 하 여 메모장의 인스턴스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-123">This command starts an instance of Notepad by calling the `Create` method of the **Win32_Process** class.</span></span>

<span data-ttu-id="51c77-124">**ReturnValue** 속성은 0으로 채워지고, 명령이 완료 되 면 **ProcessId** 속성이 정수 (다음 프로세스 ID 번호)로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-124">The **ReturnValue** property is populated with a 0, and the **ProcessId** property is populated with an integer (the next process ID number) if the command is completed.</span></span>

### <span data-ttu-id="51c77-125">예제 3: 파일 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="51c77-125">Example 3: Rename a file</span></span>

```powershell
Invoke-WmiMethod -Path "CIM_DataFile.Name='C:\scripts\test.txt'" -Name Rename -ArgumentList "C:\scripts\test_bu.txt"
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ReturnValue      : 0
```

<span data-ttu-id="51c77-126">이 명령은 파일의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-126">This command renames a file.</span></span> <span data-ttu-id="51c77-127">**Path** 매개 변수를 사용 하 여 **CIM_DataFile** 클래스의 인스턴스를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-127">It uses the **Path** parameter to reference an instance of the **CIM_DataFile** class.</span></span> <span data-ttu-id="51c77-128">그다음에 해당 특정 인스턴스에 Rename 메서드를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-128">Then, it applies the Rename method to that particular instance.</span></span>

<span data-ttu-id="51c77-129">명령이 완료 되 면 **ReturnValue** 속성은 0으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-129">The **ReturnValue** property is populated with a 0 if the command is completed.</span></span>

### <span data-ttu-id="51c77-130">예제 4:를 사용 하 여 값 배열 전달 `-ArgumentList`</span><span class="sxs-lookup"><span data-stu-id="51c77-130">Example 4: Passing an array of values using `-ArgumentList`</span></span>

<span data-ttu-id="51c77-131">개체 배열을 사용 하 `$binSD` 고 그 뒤에 값을 사용 하는 예제 `$null` 입니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-131">An example using an array of objects `$binSD` followed by a `$null` value.</span></span>

```powershell
$acl = get-acl test.txt
$binSD = $acl.GetSecurityDescriptorBinaryForm()
Invoke-WmiMethod -class Win32_SecurityDescriptorHelper -Name BinarySDToSDDL -ArgumentList $binSD, $null
```

## <span data-ttu-id="51c77-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="51c77-132">PARAMETERS</span></span>

### <span data-ttu-id="51c77-133">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="51c77-133">-ArgumentList</span></span>

<span data-ttu-id="51c77-134">호출된 메서드에 전달할 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-134">Specifies the parameters to pass to the called method.</span></span> <span data-ttu-id="51c77-135">이 매개 변수 값은 개체의 배열 이어야 하며, 호출 된 메서드에 필요한 순서로 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-135">The value of this parameter must be an array of objects, and they must appear in the order required by the called method.</span></span> <span data-ttu-id="51c77-136">Cmdlet에는 `Invoke-CimCommand` 이러한 제한 사항이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-136">The `Invoke-CimCommand` cmdlet does not have these limitations.</span></span>

<span data-ttu-id="51c77-137">이러한 개체를 나열할 순서를 확인 하려면 `GetMethodParameters()` 이 항목의 끝 부분에 있는 예제 1에 나와 있는 것 처럼 WMI 클래스에서 메서드를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-137">To determine the order in which to list those objects, run the `GetMethodParameters()` method on the WMI class, as illustrated in Example 1, near the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51c77-138">첫 번째 값이 둘 이상의 요소를 포함하는 배열인 경우 두 번째 값 $null이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-138">If the first value is an array that contains more than one element, a second value of $null is required.</span></span> <span data-ttu-id="51c77-139">그러지 않으면 명령에서 "'System.Byte' 형식 개체를 'System.Array' 형식으로 캐스팅할 수 없습니다."와 같은 오류가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-139">Otherwise, the command generates an error, such as "Unable to cast object of type 'System.Byte' to type 'System.Array'.".</span></span> <span data-ttu-id="51c77-140">위의 예 4를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="51c77-140">See example 4 above.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: class, object, path
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51c77-141">-AsJob</span><span class="sxs-lookup"><span data-stu-id="51c77-141">-AsJob</span></span>

<span data-ttu-id="51c77-142">이 cmdlet이 명령을 백그라운드 작업으로 실행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-142">Indicates that this cmdlet runs the command as a background job.</span></span> <span data-ttu-id="51c77-143">이 매개 변수를 사용하여 마치는 데 시간이 많이 걸리는 명령을 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="51c77-143">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="51c77-144">**AsJob** 매개 변수를 사용하는 경우 이 명령은 백그라운드 작업을 나타내는 개체를 반환한 다음 명령 프롬프트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-144">When you use the **AsJob** parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span> <span data-ttu-id="51c77-145">작업을 마치는 동안 세션에서 작업을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-145">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="51c77-146">`Invoke-WmiMethod`가 원격 컴퓨터에 대해 사용 되는 경우 작업은 로컬 컴퓨터에 만들어지고 원격 컴퓨터의 결과는 로컬 컴퓨터에 자동으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-146">If `Invoke-WmiMethod` is used against a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="51c77-147">작업을 관리하려면 Job 명사(Job cmdlets)가 포함된 cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-147">To manage the job, use the cmdlets that contain the Job noun (the Job cmdlets).</span></span> <span data-ttu-id="51c77-148">작업 결과를 가져오려면 Receive-Job cmdlet을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="51c77-148">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="51c77-149">원격 컴퓨터에 이 매개 변수를 사용하려면 원격을 사용하도록 로컬 및 원격 컴퓨터를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-149">To use this parameter with remote computers, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="51c77-150">또한 windows Vista 이상 버전의 windows에서 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-150">Additionally, you must start Windows PowerShell by using the Run as administrator option in Windows Vista and later versions of Windows.</span></span> <span data-ttu-id="51c77-151">자세한 내용은 about_Remote_Requirements를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51c77-151">For more information, see about_Remote_Requirements.</span></span>

<span data-ttu-id="51c77-152">Windows PowerShell 백그라운드 작업에 대 한 자세한 내용은 about_Jobs 및 about_Remote_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="51c77-152">For more information about Windows PowerShell background jobs, see about_Jobs and about_Remote_Jobs.</span></span>

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

### <span data-ttu-id="51c77-153">-인증</span><span class="sxs-lookup"><span data-stu-id="51c77-153">-Authentication</span></span>

<span data-ttu-id="51c77-154">WMI 연결에 사용되는 인증 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-154">Specifies the authentication level to be used with the WMI connection.</span></span> <span data-ttu-id="51c77-155">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="51c77-156">-1: 변경 되지 않음</span><span class="sxs-lookup"><span data-stu-id="51c77-156">-1: Unchanged</span></span>
- <span data-ttu-id="51c77-157">0: 기본값</span><span class="sxs-lookup"><span data-stu-id="51c77-157">0: Default</span></span>
- <span data-ttu-id="51c77-158">1: 없음 (인증이 수행 되지 않음)</span><span class="sxs-lookup"><span data-stu-id="51c77-158">1: None (No authentication in performed.)</span></span>
- <span data-ttu-id="51c77-159">2: 연결 (클라이언트가 응용 프로그램과의 관계를 설정 하는 경우에만 인증이 수행 됨)</span><span class="sxs-lookup"><span data-stu-id="51c77-159">2: Connect (Authentication is performed only when the client establishes a relationship with the application.)</span></span>
- <span data-ttu-id="51c77-160">3: 호출 (응용 프로그램이 요청을 받을 때 각 호출이 시작 될 때만 인증이 수행 됩니다.)</span><span class="sxs-lookup"><span data-stu-id="51c77-160">3: Call (Authentication is performed only at the beginning of each call when the application receives the request.)</span></span>
- <span data-ttu-id="51c77-161">4: 패킷 (클라이언트에서 받은 모든 데이터에 대해 인증이 수행 됩니다.)</span><span class="sxs-lookup"><span data-stu-id="51c77-161">4: Packet (Authentication is performed on all the data that is received from the client.)</span></span>
- <span data-ttu-id="51c77-162">5: PacketIntegrity (클라이언트와 응용 프로그램 간에 전송 되는 모든 데이터는 인증 되 고 확인 됩니다.)</span><span class="sxs-lookup"><span data-stu-id="51c77-162">5: PacketIntegrity (All the data that is transferred between the client and the application is authenticated and verified.)</span></span>
- <span data-ttu-id="51c77-163">6: PacketPrivacy (다른 인증 수준의 속성이 사용 되며 모든 데이터가 암호화 됩니다.)</span><span class="sxs-lookup"><span data-stu-id="51c77-163">6: PacketPrivacy (The properties of the other authentication levels are used, and all the data is encrypted.)</span></span>

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

### <span data-ttu-id="51c77-164">-Authority</span><span class="sxs-lookup"><span data-stu-id="51c77-164">-Authority</span></span>

<span data-ttu-id="51c77-165">WMI 연결을 인증하는 데 사용할 권한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-165">Specifies the authority to use to authenticate the WMI connection.</span></span> <span data-ttu-id="51c77-166">표준 Windows NTLM (NT LAN Manager) 또는 Kerberos 인증을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-166">You can specify standard Windows NT LAN Manager (NTLM) or Kerberos authentication.</span></span> <span data-ttu-id="51c77-167">NTLM을 사용하려면 권한 설정을 ntlmdomain:\<DomainName\>으로 설정합니다. 여기서 \<DomainName\>은 유효한 NTLM 도메인 이름을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-167">To use NTLM, set the authority setting to ntlmdomain:\<DomainName\>, where \<DomainName\> identifies a valid NTLM domain name.</span></span> <span data-ttu-id="51c77-168">Kerberos를 사용하려면 kerberos:\<DomainName\ServerName\>을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-168">To use Kerberos, specify kerberos:\<DomainName\ServerName\>.</span></span> <span data-ttu-id="51c77-169">로컬 컴퓨터에 연결하는 경우 권한 설정을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-169">You cannot include the authority setting when you connect to the local computer.</span></span>

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

### <span data-ttu-id="51c77-170">-클래스</span><span class="sxs-lookup"><span data-stu-id="51c77-170">-Class</span></span>

<span data-ttu-id="51c77-171">호출할 정적 메서드를 포함하는 WMI 클래스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-171">Specifies the WMI class that contains a static method to call.</span></span>

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

### <span data-ttu-id="51c77-172">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="51c77-172">-ComputerName</span></span>

<span data-ttu-id="51c77-173">이 cmdlet이 명령을 실행 하는 컴퓨터를 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-173">Specifies, as a string array, the computers that this cmdlet runs the command on.</span></span> <span data-ttu-id="51c77-174">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-174">The default is the local computer.</span></span>

<span data-ttu-id="51c77-175">하나 이상 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="51c77-175">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more computers.</span></span> <span data-ttu-id="51c77-176">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 (.) 또는 localhost를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-176">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="51c77-177">이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-177">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="51c77-178">원격 명령을 실행하도록 컴퓨터를 구성하지 않은 경우에도 **ComputerName** 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-178">You can use the **ComputerName** parameter even if your computer is not configured to run remote commands.</span></span>

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

### <span data-ttu-id="51c77-179">-Credential</span><span class="sxs-lookup"><span data-stu-id="51c77-179">-Credential</span></span>

<span data-ttu-id="51c77-180">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-180">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="51c77-181">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-181">The default is the current user.</span></span> <span data-ttu-id="51c77-182">사용자 이름 (예:, 또는)을 입력 `User01` `Domain01\User01` `User@Contoso.com` 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-182">Type a user name, such as `User01`, `Domain01\User01`, or `User@Contoso.com`.</span></span> <span data-ttu-id="51c77-183">또는 Get-Credential cmdlet에서 반환 된 개체와 같은 **PSCredential** 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-183">Or, enter a **PSCredential** object, such as an object that is returned by the Get-Credential cmdlet.</span></span> <span data-ttu-id="51c77-184">사용자 이름을 입력하면 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-184">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="51c77-185">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="51c77-185">-EnableAllPrivileges</span></span>

<span data-ttu-id="51c77-186">명령에서 WMI 호출을 수행 하기 전에이 cmdlet이 현재 사용자의 모든 권한을 사용 하도록 설정 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-186">Indicates that this cmdlet enables all the privileges of the current user before the command makes the WMI call.</span></span>

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

### <span data-ttu-id="51c77-187">-가장</span><span class="sxs-lookup"><span data-stu-id="51c77-187">-Impersonation</span></span>

<span data-ttu-id="51c77-188">사용할 가장 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-188">Specifies the impersonation level to use.</span></span> <span data-ttu-id="51c77-189">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-189">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="51c77-190">0: 기본값 (일반적으로 "3: Impersonate"로 설정 되는 기본 가장 수준에 대 한 로컬 레지스트리를 읽습니다.)</span><span class="sxs-lookup"><span data-stu-id="51c77-190">0: Default (Reads the local registry for the default impersonation level, which is usually set to "3: Impersonate".)</span></span>
- <span data-ttu-id="51c77-191">1: Anonymous (호출자의 자격 증명을 숨깁니다.)</span><span class="sxs-lookup"><span data-stu-id="51c77-191">1: Anonymous (Hides the credentials of the caller.)</span></span>
- <span data-ttu-id="51c77-192">2: 식별 (개체가 호출자의 자격 증명을 쿼리할 수 있도록 허용)</span><span class="sxs-lookup"><span data-stu-id="51c77-192">2: Identify (Allows objects to query the credentials of the caller.)</span></span>
- <span data-ttu-id="51c77-193">3: Impersonate (개체가 호출자의 자격 증명을 사용할 수 있도록 허용)</span><span class="sxs-lookup"><span data-stu-id="51c77-193">3: Impersonate (Allows objects to use the credentials of the caller.)</span></span>
- <span data-ttu-id="51c77-194">4: Delegate (개체가 다른 개체에서 호출자의 자격 증명을 사용할 수 있도록 허용)</span><span class="sxs-lookup"><span data-stu-id="51c77-194">4: Delegate (Allows objects to permit other objects to use the credentials of the caller.)</span></span>

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

### <span data-ttu-id="51c77-195">-InputObject</span><span class="sxs-lookup"><span data-stu-id="51c77-195">-InputObject</span></span>

<span data-ttu-id="51c77-196">입력으로 사용할 **Managementobject** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-196">Specifies a **ManagementObject** object to use as input.</span></span> <span data-ttu-id="51c77-197">이 매개 변수를 사용 하면 **Flag** 및 **Argument** 매개 변수를 제외한 다른 모든 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-197">When this parameter is used, all other parameters except the **Flag** and **Argument** parameters are ignored.</span></span>

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

### <span data-ttu-id="51c77-198">-Locale</span><span class="sxs-lookup"><span data-stu-id="51c77-198">-Locale</span></span>

<span data-ttu-id="51c77-199">WMI 개체의 기본 설정 로캘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-199">Specifies the preferred locale for WMI objects.</span></span> <span data-ttu-id="51c77-200">**로캘** 매개 변수의 값을 `MS_<LCID>` 원하는 순서로 형식의 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-200">Specify the value of the **Locale** parameter as an array in the `MS_<LCID>` format in the preferred order.</span></span>

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

### <span data-ttu-id="51c77-201">-Name</span><span class="sxs-lookup"><span data-stu-id="51c77-201">-Name</span></span>

<span data-ttu-id="51c77-202">호출할 메서드의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-202">Specifies the name of the method to be invoked.</span></span> <span data-ttu-id="51c77-203">이 매개 변수는 필수이며 null이거나 비어 있을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-203">This parameter is mandatory and cannot be null or empty.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51c77-204">-Namespace</span><span class="sxs-lookup"><span data-stu-id="51c77-204">-Namespace</span></span>

<span data-ttu-id="51c77-205">**Class** 매개 변수와 함께 사용할 경우이 매개 변수는 참조 된 wmi 클래스 또는 개체가 있는 wmi 리포지토리 네임 스페이스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-205">When used with the **Class** parameter, this parameter specifies the WMI repository namespace where the referenced WMI class or object is located.</span></span>

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

### <span data-ttu-id="51c77-206">-Path</span><span class="sxs-lookup"><span data-stu-id="51c77-206">-Path</span></span>

<span data-ttu-id="51c77-207">WMI 클래스의 WMI 개체 경로를 지정하거나 WMI 클래스 인스턴스의 WMI 개체 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-207">Specifies the WMI object path of a WMI class, or specifies the WMI object path of an instance of a WMI class.</span></span> <span data-ttu-id="51c77-208">지정 하는 클래스나 인스턴스에는 **Name** 매개 변수에 지정 된 메서드가 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-208">The class or the instance that you specify must contain the method that is specified in the **Name** parameter.</span></span>

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

### <span data-ttu-id="51c77-209">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="51c77-209">-ThrottleLimit</span></span>

<span data-ttu-id="51c77-210">동시에 실행할 수 있는 WMI 작업 수에 대 한 제한 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-210">Specifies a throttle value for the number of WMI operations that can be executed simultaneously.</span></span>
<span data-ttu-id="51c77-211">이 매개 변수는 **AsJob** 매개 변수와 함께 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-211">This parameter is used together with the **AsJob** parameter.</span></span> <span data-ttu-id="51c77-212">제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-212">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="51c77-213">-Confirm</span><span class="sxs-lookup"><span data-stu-id="51c77-213">-Confirm</span></span>

<span data-ttu-id="51c77-214">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-214">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="51c77-215">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="51c77-215">-WhatIf</span></span>

<span data-ttu-id="51c77-216">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-216">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="51c77-217">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-217">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="51c77-218">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="51c77-218">CommonParameters</span></span>

<span data-ttu-id="51c77-219">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="51c77-219">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="51c77-220">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51c77-220">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="51c77-221">입력</span><span class="sxs-lookup"><span data-stu-id="51c77-221">INPUTS</span></span>

### <span data-ttu-id="51c77-222">없음</span><span class="sxs-lookup"><span data-stu-id="51c77-222">None</span></span>

<span data-ttu-id="51c77-223">이 cmdlet은 어떠한 입력도 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-223">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="51c77-224">출력</span><span class="sxs-lookup"><span data-stu-id="51c77-224">OUTPUTS</span></span>

### <span data-ttu-id="51c77-225">없음</span><span class="sxs-lookup"><span data-stu-id="51c77-225">None</span></span>

<span data-ttu-id="51c77-226">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51c77-226">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="51c77-227">참고</span><span class="sxs-lookup"><span data-stu-id="51c77-227">NOTES</span></span>

## <span data-ttu-id="51c77-228">관련 링크</span><span class="sxs-lookup"><span data-stu-id="51c77-228">RELATED LINKS</span></span>

[<span data-ttu-id="51c77-229">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="51c77-229">Get-WSManInstance</span></span>](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[<span data-ttu-id="51c77-230">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="51c77-230">Invoke-WSManAction</span></span>](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[<span data-ttu-id="51c77-231">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="51c77-231">New-WSManInstance</span></span>](../Microsoft.WsMan.Management/New-WSManInstance.md)

[<span data-ttu-id="51c77-232">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="51c77-232">Remove-WSManInstance</span></span>](../Microsoft.WsMan.Management/Remove-WSManInstance.md)

[<span data-ttu-id="51c77-233">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="51c77-233">Get-WmiObject</span></span>](Get-WmiObject.md)

[<span data-ttu-id="51c77-234">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="51c77-234">Remove-WmiObject</span></span>](Remove-WmiObject.md)

[<span data-ttu-id="51c77-235">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="51c77-235">Set-WmiInstance</span></span>](Set-WmiInstance.md)
