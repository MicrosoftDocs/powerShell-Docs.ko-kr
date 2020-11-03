---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: 0c007f1becd7364806cfd47e18cf05995b81e0f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215402"
---
# <span data-ttu-id="ef600-103">Get-Service</span><span class="sxs-lookup"><span data-stu-id="ef600-103">Get-Service</span></span>

## <span data-ttu-id="ef600-104">개요</span><span class="sxs-lookup"><span data-stu-id="ef600-104">SYNOPSIS</span></span>
<span data-ttu-id="ef600-105">로컬 또는 원격 컴퓨터의 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-105">Gets the services on a local or remote computer.</span></span>

## <span data-ttu-id="ef600-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ef600-106">SYNTAX</span></span>

### <span data-ttu-id="ef600-107">Default (기본값)</span><span class="sxs-lookup"><span data-stu-id="ef600-107">Default (Default)</span></span>

```
Get-Service [[-Name] <String[]>] [-ComputerName <String[]>] [-DependentServices] [-RequiredServices]
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="ef600-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ef600-108">DisplayName</span></span>

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] -DisplayName <String[]>
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="ef600-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="ef600-109">InputObject</span></span>

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## <span data-ttu-id="ef600-110">설명</span><span class="sxs-lookup"><span data-stu-id="ef600-110">DESCRIPTION</span></span>

<span data-ttu-id="ef600-111">**Get-help** cmdlet은 실행 중인 서비스와 중지 된 서비스를 포함 하 여 로컬 컴퓨터 또는 원격 컴퓨터의 서비스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-111">The **Get-Service** cmdlet gets objects that represent the services on a local computer or on a remote computer, including running and stopped services.</span></span>

<span data-ttu-id="ef600-112">서비스의 서비스 이름 또는 표시 이름을 지정 하 여 특정 서비스만 가져오도록이 cmdlet을 지시 하거나, 서비스 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-112">You can direct this cmdlet to get only particular services by specifying the service name or the display name of the services, or you can pipe service objects to this cmdlet.</span></span>

## <span data-ttu-id="ef600-113">예제</span><span class="sxs-lookup"><span data-stu-id="ef600-113">EXAMPLES</span></span>

### <span data-ttu-id="ef600-114">예 1: 컴퓨터의 모든 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="ef600-114">Example 1: Get all services on the computer</span></span>

```powershell
Get-Service
```

<span data-ttu-id="ef600-115">이 명령은 컴퓨터의 모든 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-115">This command gets all of the services on the computer.</span></span>
<span data-ttu-id="ef600-116">입력 한 것 처럼 동작 `Get-Service *` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-116">It behaves as though you typed `Get-Service *`.</span></span>
<span data-ttu-id="ef600-117">기본 표시에서는 각 서비스의 상태, 서비스 이름 및 표시 이름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-117">The default display shows the status, service name, and display name of each service.</span></span>

### <span data-ttu-id="ef600-118">예제 2: 검색 문자열로 시작 하는 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="ef600-118">Example 2: Get services that begin with a search string</span></span>

```powershell
Get-Service "wmi*"
```

<span data-ttu-id="ef600-119">이 명령은 WMI (WMI(Windows Management Instrumentation)의 머리글자어)로 시작 하는 서비스 이름을 사용 하 여 서비스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-119">This command retrieves services with service names that begin with WMI (the acronym for Windows Management Instrumentation).</span></span>

### <span data-ttu-id="ef600-120">예제 3: 검색 문자열을 포함 하는 서비스 표시</span><span class="sxs-lookup"><span data-stu-id="ef600-120">Example 3: Display services that include a search string</span></span>

```powershell
Get-Service -Displayname "*network*"
```

<span data-ttu-id="ef600-121">이 명령은 단어 네트워크를 포함 하는 표시 이름을 포함 하는 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-121">This command displays services with a display name that includes the word network.</span></span>
<span data-ttu-id="ef600-122">표시 이름을 검색하면 xmlprov(Network Provisioning Service)와 같이 서비스 이름에 "Net"이 없는 경우에도 네트워크 관련 서비스를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-122">Searching the display name finds network-related services even when the service name does not include "Net", such as xmlprov, the Network Provisioning Service.</span></span>

### <span data-ttu-id="ef600-123">예제 4: 검색 문자열과 제외로 시작 하는 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="ef600-123">Example 4: Get services that begin with a search string and an exclusion</span></span>

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

<span data-ttu-id="ef600-124">이러한 명령은 WinRM 서비스를 제외 하 고 서비스 이름이 win으로 시작 하는 서비스만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-124">These commands get only the services with service names that begin with win, except for the WinRM service.</span></span>

### <span data-ttu-id="ef600-125">예 5: 현재 활성화 된 서비스 표시</span><span class="sxs-lookup"><span data-stu-id="ef600-125">Example 5: Display services that are currently active</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

<span data-ttu-id="ef600-126">이 명령은 현재 활성화 된 서비스만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-126">This command displays only the services that are currently active.</span></span>
<span data-ttu-id="ef600-127">이 cmdlet은 **get-Service** cmdlet을 사용 하 여 컴퓨터의 모든 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-127">It uses the **Get-Service** cmdlet to get all of the services on the computer.</span></span>
<span data-ttu-id="ef600-128">파이프라인 연산자 (|)가 결과를 Where-Object cmdlet으로 전달 합니다 .이 cmdlet은 실행 중인 상태 속성의 서비스만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-128">The pipeline operator (|) passes the results to the Where-Object cmdlet, which selects only the services with a Status property that equals Running.</span></span>

<span data-ttu-id="ef600-129">Status는 서비스 개체의 속성 중 하나에 불과합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-129">Status is only one property of service objects.</span></span>
<span data-ttu-id="ef600-130">모든 속성을 보려면를 입력 `Get-Service | Get-Member` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-130">To see all of the properties, type `Get-Service | Get-Member`.</span></span>

### <span data-ttu-id="ef600-131">예 6: 원격 컴퓨터에서 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="ef600-131">Example 6: Get the services on a remote computer</span></span>

```powershell
Get-Service -ComputerName "Server02"
```

<span data-ttu-id="ef600-132">이 명령은 Server02 원격 컴퓨터의 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-132">This command gets the services on the Server02 remote computer.</span></span>

<span data-ttu-id="ef600-133">**서비스** 의 *ComputerName* 매개 변수는 windows powershell 원격을 사용 하지 않으므로 windows powershell에서 원격 기능을 사용 하도록 구성 되지 않은 경우에도이 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-133">Because the *ComputerName* parameter of **Get-Service** does not use Windows PowerShell remoting, you can use this parameter even if the computer is not configured for remoting in Windows PowerShell.</span></span>

### <span data-ttu-id="ef600-134">예 7: 종속 서비스가 있는 로컬 컴퓨터의 서비스 나열</span><span class="sxs-lookup"><span data-stu-id="ef600-134">Example 7: List the services on the local computer that have dependent services</span></span>

```powershell
Get-Service |
  Where-Object {$_.DependentServices} |
    Format-List -Property Name, DependentServices, @{
      Label="NoOfDependentServices"; Expression={$_.dependentservices.count}
    }
```

```Output
Name                  : AudioEndpointBuilder
DependentServices     : {AudioSrv}
NoOfDependentServices : 1

Name                  : Dhcp
DependentServices     : {WinHttpAutoProxySvc}
NoOfDependentServices : 1
...
```

<span data-ttu-id="ef600-135">첫 번째 명령은 **get-help** cmdlet을 사용 하 여 컴퓨터의 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-135">The first command uses the **Get-Service** cmdlet to get the services on the computer.</span></span>
<span data-ttu-id="ef600-136">파이프라인 연산자 (|)가 DependentServices cmdlet으로 서비스를 보냅니다 .이 **cmdlet은 해당** **DependentServices** 속성이 null이 아닌 서비스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-136">A pipeline operator (|) sends the services to the **Where-Object** cmdlet, which selects the services whose **DependentServices** property is not null.</span></span>

<span data-ttu-id="ef600-137">다른 파이프라인 연산자(|)는 결과를 Format-List cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-137">Another pipeline operator sends the results to the Format-List cmdlet.</span></span>
<span data-ttu-id="ef600-138">이 명령은 해당 *Property* 매개 변수를 사용 하 여 서비스의 이름, 종속 된 서비스의 이름 및 각 서비스에 포함 된 종속 서비스의 수를 표시 하는 계산 된 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-138">The command uses its *Property* parameter to display the name of the service, the name of the dependent services, and a calculated property that displays the number of dependent services that each service has.</span></span>

### <span data-ttu-id="ef600-139">예 8: 속성 값으로 서비스 정렬</span><span class="sxs-lookup"><span data-stu-id="ef600-139">Example 8: Sort services by property value</span></span>

```powershell
Get-Service "s*" | Sort-Object status
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  stisvc             Windows Image Acquisition (WIA)
Stopped  SwPrv              MS Software Shadow Copy Provider
Stopped  SysmonLog          Performance Logs and Alerts
Running  Spooler            Print Spooler
Running  srservice          System Restore Service
Running  SSDPSRV            SSDP Discovery Service
Running  ShellHWDetection   Shell Hardware Detection
Running  Schedule           Task Scheduler
Running  SCardSvr           Smart Card
Running  SamSs              Security Accounts Manager
Running  SharedAccess       Windows Firewall/Internet Connectio...
Running  SENS               System Event Notification
Running  seclogon           Secondary Logon
```

<span data-ttu-id="ef600-140">이 명령은 **상태** 속성의 값을 기준으로 오름차순으로 서비스를 정렬 하는 경우 서비스를 실행 하기 전에 중지 된 서비스를 표시 함을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-140">This command shows that when you sort services in ascending order by the value of their **Status** property, stopped services appear before running services.</span></span>
<span data-ttu-id="ef600-141">Status 값이 열거형 이며,이는 중지 된 값이 1이 고 실행 값이 4 인 경우에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-141">This happens because the value of Status is an enumeration, in which Stopped has a value of 1, and Running has a value of 4.</span></span>

<span data-ttu-id="ef600-142">실행 중인 서비스를 먼저 나열 하려면 Sort-Object cmdlet의 *내림차순* 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-142">To list running services first, use the *Descending* parameter of the Sort-Object cmdlet.</span></span>

### <span data-ttu-id="ef600-143">예 9: 여러 컴퓨터에서 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="ef600-143">Example 9: Get services on multiple computers</span></span>

```powershell
Get-Service -Name "WinRM" -ComputerName "localhost", "Server01", "Server02" |
 Format-Table -Property MachineName, Status, Name, DisplayName -auto
```

```Output
MachineName    Status  Name  DisplayName
------------   ------  ----  -----------
localhost      Running WinRM Windows Remote Management (WS-Management)
Server01       Running WinRM Windows Remote Management (WS-Management)
Server02       Running WinRM Windows Remote Management (WS-Management)
```

<span data-ttu-id="ef600-144">이 명령은 **Get Service** cmdlet을 사용 하 여 두 원격 컴퓨터와 로컬 컴퓨터 ("localhost")에서 Get-Service Winrm 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-144">This command uses the **Get-Service** cmdlet to run a Get-Service Winrm command on two remote computers and the local computer ("localhost").</span></span>

<span data-ttu-id="ef600-145">이 명령은 원격 컴퓨터에서 실행 되 고 결과는 로컬 컴퓨터에 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-145">The command runs on the remote computers, and the results are returned to the local computer.</span></span>
<span data-ttu-id="ef600-146">파이프라인 연산자 (|)가 결과를 **형식 테이블** cmdlet으로 보내면이 cmdlet이 서비스를 테이블로 포맷 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-146">A pipeline operator (|) sends the results to the **Format-Table** cmdlet, which formats the services as a table.</span></span>
<span data-ttu-id="ef600-147">**Format-table** 명령은 *Property* 매개 변수를 사용 하 여 **MachineName** 속성을 포함 하 여 테이블에 표시 되는 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-147">The **Format-Table** command uses the *Property* parameter to specify the properties displayed in the table, including the **MachineName** property.</span></span>

### <span data-ttu-id="ef600-148">예 10: 서비스의 종속 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="ef600-148">Example 10: Get the dependent services of a service</span></span>

```powershell
Get-Service "WinRM" -RequiredServices
```

<span data-ttu-id="ef600-149">이 명령은 WinRM 서비스에 필요한 서비스를 가져오고,</span><span class="sxs-lookup"><span data-stu-id="ef600-149">This command gets the services that the WinRM service requires.</span></span>

<span data-ttu-id="ef600-150">이 명령은 서비스의 **ServicesDependedOn** 속성 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-150">The command returns the value of the **ServicesDependedOn** property of the service.</span></span>

### <span data-ttu-id="ef600-151">예 11: 파이프라인 연산자를 통해 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="ef600-151">Example 11: Get a service through the pipeline operator</span></span>

```powershell
"WinRM" | Get-Service
```

<span data-ttu-id="ef600-152">이 명령은 로컬 컴퓨터의 WinRM 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-152">This command gets the WinRM service on the local computer.</span></span>
<span data-ttu-id="ef600-153">이 예제에서는 서비스 이름 문자열 (따옴표 안에 포함 됨)을 **service** 로 파이프 하는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-153">This example shows that you can pipe a service name string (enclosed in quotation marks) to **Get-Service** .</span></span>

## <span data-ttu-id="ef600-154">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ef600-154">PARAMETERS</span></span>

### <span data-ttu-id="ef600-155">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="ef600-155">-ComputerName</span></span>

<span data-ttu-id="ef600-156">지정된 컴퓨터에서 실행 중인 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-156">Gets the services running on the specified computers.</span></span>
<span data-ttu-id="ef600-157">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-157">The default is the local computer.</span></span>

<span data-ttu-id="ef600-158">원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 FQDN (정규화 된 도메인 이름)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-158">Type the NetBIOS name, an IP address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>
<span data-ttu-id="ef600-159">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 (.) 또는 localhost를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-159">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="ef600-160">이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-160">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="ef600-161">컴퓨터가 원격 명령을 실행 하도록 구성 되지 않은 경우 **에도** *ComputerName* 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-161">You can use the *ComputerName* parameter of **Get-Service** even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ef600-162">-DependentServices</span><span class="sxs-lookup"><span data-stu-id="ef600-162">-DependentServices</span></span>

<span data-ttu-id="ef600-163">이 cmdlet은 지정 된 서비스에 종속 된 서비스만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-163">Indicates that this cmdlet gets only the services that depend upon the specified service.</span></span>

<span data-ttu-id="ef600-164">기본적으로이 cmdlet은 모든 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-164">By default, this cmdlet gets all services.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef600-165">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="ef600-165">-DisplayName</span></span>

<span data-ttu-id="ef600-166">검색할 서비스의 표시 이름을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-166">Specifies, as a string array, the display names of services to be retrieved.</span></span>
<span data-ttu-id="ef600-167">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-167">Wildcards are permitted.</span></span>
<span data-ttu-id="ef600-168">기본적으로이 cmdlet은 컴퓨터의 모든 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-168">By default, this cmdlet gets all services on the computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="ef600-169">-제외</span><span class="sxs-lookup"><span data-stu-id="ef600-169">-Exclude</span></span>

<span data-ttu-id="ef600-170">이 cmdlet이 작업에서 제외 하는 서비스 또는 서비스를 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-170">Specifies, as a string array, a service or services that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="ef600-171">이 매개 변수 값은 *Name* 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-171">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="ef600-172">이름 요소 또는 패턴(예: "*s*")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-172">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="ef600-173">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-173">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="ef600-174">-포함</span><span class="sxs-lookup"><span data-stu-id="ef600-174">-Include</span></span>

<span data-ttu-id="ef600-175">이 cmdlet이 작업에 포함 하는 서비스 또는 서비스를 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-175">Specifies, as a string array, a service or services that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="ef600-176">이 매개 변수 값은 *Name* 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-176">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="ef600-177">이름 요소 또는 패턴(예: "*s*")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-177">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="ef600-178">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-178">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="ef600-179">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ef600-179">-InputObject</span></span>

<span data-ttu-id="ef600-180">검색할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-180">Specifies **ServiceController** objects representing the services to be retrieved.</span></span>
<span data-ttu-id="ef600-181">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="ef600-181">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>
<span data-ttu-id="ef600-182">서비스 개체를이 cmdlet으로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-182">You can also pipe a service object to this cmdlet.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ef600-183">-Name</span><span class="sxs-lookup"><span data-stu-id="ef600-183">-Name</span></span>

<span data-ttu-id="ef600-184">검색할 서비스의 표시 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-184">Specifies the service names of services to be retrieved.</span></span>
<span data-ttu-id="ef600-185">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-185">Wildcards are permitted.</span></span>
<span data-ttu-id="ef600-186">기본적으로이 cmdlet은 컴퓨터의 모든 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-186">By default, this cmdlet gets all of the services on the computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="ef600-187">-RequiredServices</span><span class="sxs-lookup"><span data-stu-id="ef600-187">-RequiredServices</span></span>

<span data-ttu-id="ef600-188">이 cmdlet은이 서비스에 필요한 서비스만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-188">Indicates that this cmdlet gets only the services that this service requires.</span></span>

<span data-ttu-id="ef600-189">이 매개 변수는 서비스의 **ServicesDependedOn** 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-189">This parameter gets the value of the **ServicesDependedOn** property of the service.</span></span>
<span data-ttu-id="ef600-190">기본적으로이 cmdlet은 모든 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-190">By default, this cmdlet gets all services.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="ef600-191">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ef600-191">CommonParameters</span></span>

<span data-ttu-id="ef600-192">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ef600-192">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ef600-193">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef600-193">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ef600-194">입력</span><span class="sxs-lookup"><span data-stu-id="ef600-194">INPUTS</span></span>

### <span data-ttu-id="ef600-195">ServiceController, System.string입니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-195">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="ef600-196">서비스 개체 또는 서비스 이름을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-196">You can pipe a service object or a service name to this cmdlet.</span></span>

## <span data-ttu-id="ef600-197">출력</span><span class="sxs-lookup"><span data-stu-id="ef600-197">OUTPUTS</span></span>

### <span data-ttu-id="ef600-198">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="ef600-198">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="ef600-199">이 cmdlet은 컴퓨터의 서비스를 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-199">This cmdlet returns objects that represent the services on the computer.</span></span>

## <span data-ttu-id="ef600-200">참고</span><span class="sxs-lookup"><span data-stu-id="ef600-200">NOTES</span></span>

<span data-ttu-id="ef600-201">또한 해당 기본 제공 별칭 ("gsv")으로 **서비스** 를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-201">You can also refer to **Get-Service** by its built-in alias, "gsv".</span></span> <span data-ttu-id="ef600-202">자세한 내용은 about_Aliases를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef600-202">For more information, see about_Aliases.</span></span>

<span data-ttu-id="ef600-203">이 cmdlet은 현재 사용자가 해당 서비스를 볼 수 있는 권한을 가진 경우에만 서비스를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-203">This cmdlet can display services only when the current user has permission to see them.</span></span>
<span data-ttu-id="ef600-204">이 cmdlet이 서비스를 표시 하지 않는 경우 해당 서비스를 볼 수 있는 권한이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-204">If this cmdlet does not display services, you might not have permission to see them.</span></span>

<span data-ttu-id="ef600-205">시스템에 있는 각 서비스의 서비스 이름 및 표시 이름을 찾으려면를 입력 `Get-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-205">To find the service name and display name of each service on your system, type `Get-Service`.</span></span>
<span data-ttu-id="ef600-206">서비스 이름은 Name 열에 나타나고 표시 이름은 DisplayName 열에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-206">The service names appear in the Name column, and the display names appear in the DisplayName column.</span></span>

<span data-ttu-id="ef600-207">상태 값을 기준으로 오름차순으로 정렬하는 경우 상태가 "Stopped"인 서비스가 상태가 "Running"인 서비스보다 앞에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-207">When you sort in ascending order by status value, "Stopped" services appear before "Running" services.</span></span>
<span data-ttu-id="ef600-208">서비스의 Status 속성은 상태 이름이 정수 값으로 나타나는 열거형 값입니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-208">The Status property of a service is an enumerated value in which the names of the statuses represent integer values.</span></span>
<span data-ttu-id="ef600-209">정렬 작업은 이름이 아니라 정수 값을 기준으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-209">The sort is based on the integer value, not the name.</span></span>
<span data-ttu-id="ef600-210">"Stopped"는 값이 "1"이고 "Running"은 값이 "4"이기 때문에 "Running"이 "Stopped"보다 앞에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ef600-210">"Running" appears before "Stopped" because "Stopped" has a value of "1", and "Running" has a value of "4".</span></span>

## <span data-ttu-id="ef600-211">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ef600-211">RELATED LINKS</span></span>

[<span data-ttu-id="ef600-212">New-Service</span><span class="sxs-lookup"><span data-stu-id="ef600-212">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="ef600-213">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="ef600-213">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="ef600-214">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="ef600-214">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="ef600-215">Set-Service</span><span class="sxs-lookup"><span data-stu-id="ef600-215">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="ef600-216">Start-Service</span><span class="sxs-lookup"><span data-stu-id="ef600-216">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="ef600-217">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="ef600-217">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="ef600-218">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="ef600-218">Suspend-Service</span></span>](Suspend-Service.md)
