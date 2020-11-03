---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WmiObject
ms.openlocfilehash: 287eb02e7de2f4182e0ecfd7f6b6a7cafb66969e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214545"
---
# <span data-ttu-id="1eb76-103">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="1eb76-103">Remove-WmiObject</span></span>

## <span data-ttu-id="1eb76-104">개요</span><span class="sxs-lookup"><span data-stu-id="1eb76-104">SYNOPSIS</span></span>
<span data-ttu-id="1eb76-105">기존 WMI(Windows Management Instrumentation) 클래스의 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-105">Deletes an instance of an existing Windows Management Instrumentation (WMI) class.</span></span>

## <span data-ttu-id="1eb76-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1eb76-106">SYNTAX</span></span>

### <span data-ttu-id="1eb76-107">클래스 (기본값)</span><span class="sxs-lookup"><span data-stu-id="1eb76-107">class (Default)</span></span>

```
Remove-WmiObject [-Class] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1eb76-108">object</span><span class="sxs-lookup"><span data-stu-id="1eb76-108">object</span></span>

```
Remove-WmiObject -InputObject <ManagementObject> [-AsJob] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="1eb76-109">path</span><span class="sxs-lookup"><span data-stu-id="1eb76-109">path</span></span>

```
Remove-WmiObject -Path <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1eb76-110">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="1eb76-110">WQLQuery</span></span>

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="1eb76-111">Query</span><span class="sxs-lookup"><span data-stu-id="1eb76-111">query</span></span>

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="1eb76-112">list</span><span class="sxs-lookup"><span data-stu-id="1eb76-112">list</span></span>

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="1eb76-113">설명</span><span class="sxs-lookup"><span data-stu-id="1eb76-113">DESCRIPTION</span></span>
<span data-ttu-id="1eb76-114">**Get-wmiobject** cmdlet은 기존 WMI(WINDOWS MANAGEMENT INSTRUMENTATION) (WMI) 클래스의 인스턴스를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-114">The **Remove-WmiObject** cmdlet deletes an instance of an existing Windows Management Instrumentation (WMI)class.</span></span>

## <span data-ttu-id="1eb76-115">예제</span><span class="sxs-lookup"><span data-stu-id="1eb76-115">EXAMPLES</span></span>

### <span data-ttu-id="1eb76-116">예제 1: Win32 프로세스의 모든 인스턴스 닫기</span><span class="sxs-lookup"><span data-stu-id="1eb76-116">Example 1: Close all instances of a Win32 process</span></span>

```
PS C:\> notepad
PS C:\> $np = Get-WmiObject -Query "select * from win32_process where name='notepad.exe'"
PS C:\> $np | Remove-WmiObject
```

<span data-ttu-id="1eb76-117">이 예에서는 Notepad.exe의 모든 인스턴스를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-117">This example closes all the instances of Notepad.exe.</span></span>

<span data-ttu-id="1eb76-118">첫 번째 명령은 메모장의 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-118">The first command starts an instance of Notepad.</span></span>

<span data-ttu-id="1eb76-119">두 번째 명령은 Get-WmiObject cmdlet을 사용 하 여 Notepad.exe에 해당 하는 Win32_Process 인스턴스를 검색 한 다음 $np 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-119">The second command uses the Get-WmiObject cmdlet to retrieve the instances of the Win32_Process that correspond to Notepad.exe, and then stores them in the $np variable.</span></span>

<span data-ttu-id="1eb76-120">세 번째 명령은 $np 변수의 개체를 **get-wmiobject** 에 전달 하 여 Notepad.exe의 모든 인스턴스를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-120">The third command passes the object in the $np variable to **Remove-WmiObject** , which deletes all the instances of Notepad.exe.</span></span>

### <span data-ttu-id="1eb76-121">예 2: 폴더 삭제</span><span class="sxs-lookup"><span data-stu-id="1eb76-121">Example 2: Delete a folder</span></span>

```
PS C:\> $a = Get-WMIObject -Query "Select * From Win32_Directory Where Name ='C:\\Test'"
PS C:\> $a | Remove-WMIObject
```

<span data-ttu-id="1eb76-122">이 명령은 C:\Test 폴더를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-122">This command deletes the C:\Test folder.</span></span>

<span data-ttu-id="1eb76-123">첫 번째 명령은 **get-wmiobject** 를 사용 하 여 C:\Test 폴더를 쿼리 한 다음 개체를 $a 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-123">The first command uses **Get-WMIObject** to query for the C:\Test folder, and then stores the object in the $a variable.</span></span>

<span data-ttu-id="1eb76-124">두 번째 명령은 $a 변수를 **get-wmiobject** 로 파이프 하 여 폴더를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-124">The second command pipes the $a variable to **Remove-WMIObject** , which deletes the folder.</span></span>

## <span data-ttu-id="1eb76-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1eb76-125">PARAMETERS</span></span>

### <span data-ttu-id="1eb76-126">-AsJob</span><span class="sxs-lookup"><span data-stu-id="1eb76-126">-AsJob</span></span>
<span data-ttu-id="1eb76-127">이 cmdlet이 백그라운드 작업으로 실행 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-127">Indicates that this cmdlet run as a background job.</span></span>
<span data-ttu-id="1eb76-128">이 매개 변수를 사용하여 마치는 데 시간이 많이 걸리는 명령을 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="1eb76-128">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="1eb76-129">Windows PowerShell 3.0에 도입된 새 CIM cmdlet은 WMI cmdlet과 동일한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-129">New CIM cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span>
<span data-ttu-id="1eb76-130">CIM cmdlet은 WSMan (WS-Management) 표준과 Windows 운영 체제를 실행 하는 컴퓨터 및 다른 운영 체제를 실행 하는 컴퓨터를 관리 하는 데 동일한 기술을 사용할 수 있도록 하는 CIM (CIM(Common Information Model)) 표준을 준수 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-130">The CIM cmdlets comply with WS-Management (WSMan) standards and with the Common Information Model (CIM) standard, which enables the cmdlets to use the same techniques to manage computers that run the Windows operating system and those running other operating systems.</span></span>
<span data-ttu-id="1eb76-131">**Get-wmiobject** 를 사용 하는 대신 ciminstance 개체로 cmdlet을 사용 하는 것이 좋습니다 https://go.microsoft.com/fwlink/?LinkId=227964 .</span><span class="sxs-lookup"><span data-stu-id="1eb76-131">Instead of using **Remove-WmiObject** , consider using the Remove-CimInstancehttps://go.microsoft.com/fwlink/?LinkId=227964 cmdlet.</span></span>

<span data-ttu-id="1eb76-132">*AsJob* 매개 변수를 사용하는 경우 이 명령은 백그라운드 작업을 나타내는 개체를 반환한 다음 명령 프롬프트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-132">When you use the *AsJob* parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span>
<span data-ttu-id="1eb76-133">작업을 마치는 동안 세션에서 작업을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-133">You can continue to work in the session while the job finishes.</span></span>
<span data-ttu-id="1eb76-134">**Get-wmiobject** 가 원격 컴퓨터에 대해 사용 되는 경우 작업은 로컬 컴퓨터에 만들어지고 원격 컴퓨터의 결과는 로컬 컴퓨터에 자동으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-134">If **Remove-WmiObject** is used against a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="1eb76-135">작업을 관리 하려면 **job** 명사 ( **job** cmdlet)를 포함 하는 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-135">To manage the job, use the cmdlets that contain the **Job** noun (the **Job** cmdlets).</span></span>
<span data-ttu-id="1eb76-136">작업 결과를 가져오려면 Receive-Job cmdlet을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="1eb76-136">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="1eb76-137">원격 컴퓨터에이 매개 변수를 사용 하려면 원격 컴퓨터에 대 한 로컬 및 원격 컴퓨터를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-137">To use this parameter for remote computers, the local and remote computers must be configured for remoting.</span></span>
<span data-ttu-id="1eb76-138">관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-138">Start Windows PowerShell by using the Run as administrator option.</span></span>
<span data-ttu-id="1eb76-139">자세한 내용은 about_Remote_Requirements를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1eb76-139">For more information, see about_Remote_Requirements.</span></span>

<span data-ttu-id="1eb76-140">Windows PowerShell 백그라운드 작업에 대 한 자세한 내용은 about_Jobs 및 about_Remote_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1eb76-140">For more information about Windows PowerShell background jobs, see about_Jobs and about_Remote_Jobs.</span></span>

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

### <span data-ttu-id="1eb76-141">-인증</span><span class="sxs-lookup"><span data-stu-id="1eb76-141">-Authentication</span></span>
<span data-ttu-id="1eb76-142">WMI 연결에 사용할 인증 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-142">Specifies the authentication level to use for the WMI connection.</span></span>
<span data-ttu-id="1eb76-143">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-143">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1eb76-144">-1: 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-144">-1: Unchanged.</span></span>
- <span data-ttu-id="1eb76-145">0: 기본값</span><span class="sxs-lookup"><span data-stu-id="1eb76-145">0: Default.</span></span>
- <span data-ttu-id="1eb76-146">1: 없음.</span><span class="sxs-lookup"><span data-stu-id="1eb76-146">1: None.</span></span>
<span data-ttu-id="1eb76-147">인증이 수행 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-147">No authentication in performed.</span></span>
- <span data-ttu-id="1eb76-148">2: 연결</span><span class="sxs-lookup"><span data-stu-id="1eb76-148">2: Connect.</span></span>
<span data-ttu-id="1eb76-149">인증은 클라이언트가 응용 프로그램과의 관계를 설정 하는 경우에만 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-149">Authentication is performed only when the client establishes a relationship with the application.</span></span>
- <span data-ttu-id="1eb76-150">3:를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-150">3: Call.</span></span>
<span data-ttu-id="1eb76-151">응용 프로그램에서 요청을 받으면 각 호출이 시작 될 때만 인증이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-151">Authentication is performed only at the start of each call when the application receives the request.</span></span>
- <span data-ttu-id="1eb76-152">4: 패킷.</span><span class="sxs-lookup"><span data-stu-id="1eb76-152">4: Packet.</span></span>
<span data-ttu-id="1eb76-153">클라이언트에서 수신 된 모든 데이터에 대해 인증이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-153">Authentication is performed on all the data that is received from the client.</span></span>
- <span data-ttu-id="1eb76-154">5: PacketIntegrity.</span><span class="sxs-lookup"><span data-stu-id="1eb76-154">5: PacketIntegrity.</span></span>
<span data-ttu-id="1eb76-155">클라이언트와 응용 프로그램 간에 전송 되는 모든 데이터는 인증 되 고 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-155">All the data that is transferred between the client and the application is authenticated and verified.</span></span>
- <span data-ttu-id="1eb76-156">6: PacketPrivacy.</span><span class="sxs-lookup"><span data-stu-id="1eb76-156">6: PacketPrivacy.</span></span>
<span data-ttu-id="1eb76-157">다른 인증 수준의 속성을 사용 하 고 모든 데이터를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-157">The properties of the other authentication levels are used, and all the data is encrypted.</span></span>

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

### <span data-ttu-id="1eb76-158">-Authority</span><span class="sxs-lookup"><span data-stu-id="1eb76-158">-Authority</span></span>
<span data-ttu-id="1eb76-159">WMI 연결을 인증하는 데 사용할 권한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-159">Specifies the authority to use to authenticate the WMI connection.</span></span>
<span data-ttu-id="1eb76-160">표준 NTLM 또는 Kerberos 인증을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-160">You can specify standard NTLM or Kerberos authentication.</span></span>
<span data-ttu-id="1eb76-161">NTLM을 사용하려면 권한 설정을 ntlmdomain:\<DomainName\>으로 설정합니다. 여기서 \<DomainName\>은 유효한 NTLM 도메인 이름을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-161">To use NTLM, set the authority setting to ntlmdomain:\<DomainName\>, where \<DomainName\> identifies a valid NTLM domain name.</span></span>
<span data-ttu-id="1eb76-162">Kerberos를 사용 하려면 kerberos를 지정 \<DomainName\> \\ \<ServerName\> 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-162">To use Kerberos, specify kerberos:\<DomainName\>\\\<ServerName\>.</span></span>
<span data-ttu-id="1eb76-163">로컬 컴퓨터에 연결하는 경우 권한 설정을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-163">You cannot include the authority setting when you connect to the local computer.</span></span>

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

### <span data-ttu-id="1eb76-164">-클래스</span><span class="sxs-lookup"><span data-stu-id="1eb76-164">-Class</span></span>
<span data-ttu-id="1eb76-165">이 cmdlet이 삭제 하는 WMI 클래스의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-165">Specifies the name of a WMI class that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="1eb76-166">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="1eb76-166">-ComputerName</span></span>
<span data-ttu-id="1eb76-167">이 cmdlet이 실행 되는 컴퓨터의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-167">Specifies the name of the computer on which this cmdlet runs.</span></span>
<span data-ttu-id="1eb76-168">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-168">The default is the local computer.</span></span>

<span data-ttu-id="1eb76-169">하나 이상 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="1eb76-169">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more computers.</span></span>
<span data-ttu-id="1eb76-170">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 (.) 또는 localhost를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-170">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="1eb76-171">이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-171">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="1eb76-172">원격 명령을 실행하도록 컴퓨터를 구성하지 않은 경우에도 *ComputerName* 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-172">You can use the *ComputerName* parameter even if your computer is not configured to run remote commands.</span></span>

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

### <span data-ttu-id="1eb76-173">-Credential</span><span class="sxs-lookup"><span data-stu-id="1eb76-173">-Credential</span></span>
<span data-ttu-id="1eb76-174">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-174">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="1eb76-175">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-175">The default is the current user.</span></span>

<span data-ttu-id="1eb76-176">User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나 **PSCredential** 개체 (예: Get-Credential cmdlet에 의해 생성 된 개체)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-176">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="1eb76-177">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-177">If you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="1eb76-178">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="1eb76-178">-EnableAllPrivileges</span></span>
<span data-ttu-id="1eb76-179">이 cmdlet은 WMI 호출을 수행 하기 전에 현재 사용자의 모든 권한을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-179">Indicates that this cmdlet enables all the permissions of the current user before the command it makes the WMI call.</span></span>

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

### <span data-ttu-id="1eb76-180">-가장</span><span class="sxs-lookup"><span data-stu-id="1eb76-180">-Impersonation</span></span>
<span data-ttu-id="1eb76-181">사용할 가장 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-181">Specifies the impersonation level to use.</span></span>
<span data-ttu-id="1eb76-182">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-182">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1eb76-183">0: 기본값</span><span class="sxs-lookup"><span data-stu-id="1eb76-183">0: Default.</span></span>
<span data-ttu-id="1eb76-184">기본 가장 수준에 대 한 로컬 레지스트리를 읽습니다. 일반적으로 3: Impersonate로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-184">Reads the local registry for the default impersonation level, which is usually set to 3: Impersonate.</span></span>
- <span data-ttu-id="1eb76-185">1: 익명.</span><span class="sxs-lookup"><span data-stu-id="1eb76-185">1: Anonymous.</span></span>
<span data-ttu-id="1eb76-186">호출자의 자격 증명을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-186">Hides the credentials of the caller.</span></span>
- <span data-ttu-id="1eb76-187">2:를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-187">2: Identify.</span></span>
<span data-ttu-id="1eb76-188">개체가 호출자의 자격 증명을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-188">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="1eb76-189">3: Impersonate</span><span class="sxs-lookup"><span data-stu-id="1eb76-189">3: Impersonate.</span></span>
<span data-ttu-id="1eb76-190">개체가 호출자의 자격 증명을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-190">Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="1eb76-191">4: 대리자.</span><span class="sxs-lookup"><span data-stu-id="1eb76-191">4: Delegate.</span></span>
<span data-ttu-id="1eb76-192">개체가 다른 개체가 호출자의 자격 증명을 사용하도록 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-192">Allows objects to permit other objects to use the credentials of the caller.</span></span>

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

### <span data-ttu-id="1eb76-193">-InputObject</span><span class="sxs-lookup"><span data-stu-id="1eb76-193">-InputObject</span></span>
<span data-ttu-id="1eb76-194">입력으로 사용할 **Managementobject** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-194">Specifies a **ManagementObject** object to use as input.</span></span>
<span data-ttu-id="1eb76-195">이 매개 변수를 사용하면 다른 모든 매개 변수가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-195">When this parameter is used, all other parameters are ignored.</span></span>

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

### <span data-ttu-id="1eb76-196">-Locale</span><span class="sxs-lookup"><span data-stu-id="1eb76-196">-Locale</span></span>
<span data-ttu-id="1eb76-197">WMI 개체의 기본 설정 로캘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-197">Specifies the preferred locale for WMI objects.</span></span>
<span data-ttu-id="1eb76-198">*로캘* 매개 변수는 기본 순서로 MS_ 형식의 배열로 지정 됩니다 \<LCID\> .</span><span class="sxs-lookup"><span data-stu-id="1eb76-198">The *Locale* parameter is specified as an array in the MS_\<LCID\> format in the preferred order.</span></span>

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

### <span data-ttu-id="1eb76-199">-Namespace</span><span class="sxs-lookup"><span data-stu-id="1eb76-199">-Namespace</span></span>
<span data-ttu-id="1eb76-200">*클래스* 매개 변수와 함께 사용 될 때 참조 된 wmi 클래스가 있는 wmi 리포지토리 네임 스페이스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-200">Specifies the WMI repository namespace where the referenced WMI class is located when it is used with the *Class* parameter.</span></span>

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

### <span data-ttu-id="1eb76-201">-Path</span><span class="sxs-lookup"><span data-stu-id="1eb76-201">-Path</span></span>
<span data-ttu-id="1eb76-202">WMI 클래스의 WMI 개체 경로 또는 삭제할 WMI 클래스 인스턴스의 WMI 개체 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-202">Specifies the WMI object path of a WMI class, or specifies the WMI object path of an instance of a WMI class to delete.</span></span>

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

### <span data-ttu-id="1eb76-203">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="1eb76-203">-ThrottleLimit</span></span>
<span data-ttu-id="1eb76-204">이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-204">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="1eb76-205">이 매개 변수는 *AsJob* 매개 변수와 함께 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-205">This parameter is used together with the *AsJob* parameter.</span></span>
<span data-ttu-id="1eb76-206">제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-206">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="1eb76-207">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1eb76-207">-Confirm</span></span>
<span data-ttu-id="1eb76-208">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-208">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1eb76-209">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1eb76-209">-WhatIf</span></span>
<span data-ttu-id="1eb76-210">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-210">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="1eb76-211">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-211">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1eb76-212">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1eb76-212">CommonParameters</span></span>
<span data-ttu-id="1eb76-213">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1eb76-213">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1eb76-214">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1eb76-214">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1eb76-215">입력</span><span class="sxs-lookup"><span data-stu-id="1eb76-215">INPUTS</span></span>

### <span data-ttu-id="1eb76-216">System.object 개체</span><span class="sxs-lookup"><span data-stu-id="1eb76-216">System.Management.ManagementObject</span></span>
<span data-ttu-id="1eb76-217">관리 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-217">You can pipe a management object to this cmdlet.</span></span>

## <span data-ttu-id="1eb76-218">출력</span><span class="sxs-lookup"><span data-stu-id="1eb76-218">OUTPUTS</span></span>

### <span data-ttu-id="1eb76-219">없음, System.web. Remorerejob</span><span class="sxs-lookup"><span data-stu-id="1eb76-219">None, System.Management.Automation.RemotingJob</span></span>
<span data-ttu-id="1eb76-220">*AsJob* 매개 변수를 지정 하는 경우이 cmdlet은 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-220">This cmdlet returns a job object, if you specify the *AsJob* parameter.</span></span>
<span data-ttu-id="1eb76-221">그러지 않으면 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1eb76-221">Otherwise, it does not generate any output.</span></span>

## <span data-ttu-id="1eb76-222">참고</span><span class="sxs-lookup"><span data-stu-id="1eb76-222">NOTES</span></span>

## <span data-ttu-id="1eb76-223">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1eb76-223">RELATED LINKS</span></span>

[<span data-ttu-id="1eb76-224">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="1eb76-224">Get-WmiObject</span></span>](Get-WmiObject.md)

[<span data-ttu-id="1eb76-225">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="1eb76-225">Invoke-WmiMethod</span></span>](Invoke-WmiMethod.md)

[<span data-ttu-id="1eb76-226">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="1eb76-226">Set-WmiInstance</span></span>](Set-WmiInstance.md)
