---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: c27dac11cdd8ebbf1705ac3bba0c0aa5147d4fa8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602236"
---
# <span data-ttu-id="36409-102">Get-Service</span><span class="sxs-lookup"><span data-stu-id="36409-102">Get-Service</span></span>

## <span data-ttu-id="36409-103">개요</span><span class="sxs-lookup"><span data-stu-id="36409-103">SYNOPSIS</span></span>
<span data-ttu-id="36409-104">컴퓨터의 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="36409-104">Gets the services on the computer.</span></span>

## <span data-ttu-id="36409-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="36409-105">SYNTAX</span></span>

### <span data-ttu-id="36409-106">Default (기본값)</span><span class="sxs-lookup"><span data-stu-id="36409-106">Default (Default)</span></span>

```
Get-Service [[-Name] <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="36409-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="36409-107">DisplayName</span></span>

```
Get-Service [-DependentServices] [-RequiredServices] -DisplayName <String[]> [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="36409-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="36409-108">InputObject</span></span>

```
Get-Service [-DependentServices] [-RequiredServices] [-Include <String[]>] [-Exclude <String[]>]
 [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## <span data-ttu-id="36409-109">설명</span><span class="sxs-lookup"><span data-stu-id="36409-109">DESCRIPTION</span></span>

<span data-ttu-id="36409-110">`Get-Service`Cmdlet은 실행 중인 서비스와 중지 된 서비스를 포함 하 여 컴퓨터의 서비스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="36409-110">The `Get-Service` cmdlet gets objects that represent the services on a computer, including running and stopped services.</span></span> <span data-ttu-id="36409-111">기본적으로 `Get-Service` 매개 변수 없이를 실행 하면 모든 로컬 컴퓨터의 서비스가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36409-111">By default, when `Get-Service` is run without parameters, all the local computer's services are returned.</span></span>

<span data-ttu-id="36409-112">서비스의 서비스 이름 또는 표시 이름을 지정 하 여 특정 서비스만 가져오도록이 cmdlet을 지시 하거나, 서비스 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36409-112">You can direct this cmdlet to get only particular services by specifying the service name or the display name of the services, or you can pipe service objects to this cmdlet.</span></span>

## <span data-ttu-id="36409-113">예제</span><span class="sxs-lookup"><span data-stu-id="36409-113">EXAMPLES</span></span>

### <span data-ttu-id="36409-114">예 1: 컴퓨터의 모든 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="36409-114">Example 1: Get all services on the computer</span></span>

<span data-ttu-id="36409-115">이 예제에서는 컴퓨터의 모든 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="36409-115">This example gets all of the services on the computer.</span></span> <span data-ttu-id="36409-116">입력 한 것 처럼 동작 `Get-Service *` 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-116">It behaves as though you typed `Get-Service *`.</span></span> <span data-ttu-id="36409-117">기본 표시에서는 각 서비스의 상태, 서비스 이름 및 표시 이름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="36409-117">The default display shows the status, service name, and display name of each service.</span></span>

```powershell
Get-Service
```

### <span data-ttu-id="36409-118">예제 2: 검색 문자열로 시작 하는 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="36409-118">Example 2: Get services that begin with a search string</span></span>

<span data-ttu-id="36409-119">이 예제에서는 WMI (WMI(Windows Management Instrumentation))로 시작 하는 서비스 이름을 사용 하 여 서비스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-119">This example retrieves services with service names that begin with WMI (Windows Management Instrumentation).</span></span>

```powershell
Get-Service "wmi*"
```

### <span data-ttu-id="36409-120">예제 3: 검색 문자열을 포함 하는 서비스 표시</span><span class="sxs-lookup"><span data-stu-id="36409-120">Example 3: Display services that include a search string</span></span>

<span data-ttu-id="36409-121">이 예에서는 단어 네트워크를 포함 하는 표시 이름을 포함 하는 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-121">This example displays services with a display name that includes the word network.</span></span> <span data-ttu-id="36409-122">표시 이름을 검색 하면 서비스 이름에 네트워크 프로 비전 서비스와 같은 네트워크 (예: xmlprov)가 포함 되지 않은 경우에도 네트워크 관련 서비스가 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36409-122">Searching the display name finds network-related services even when the service name doesn't include Net, such as xmlprov, the Network Provisioning Service.</span></span>

```powershell
Get-Service -Displayname "*network*"
```

### <span data-ttu-id="36409-123">예제 4: 검색 문자열과 제외로 시작 하는 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="36409-123">Example 4: Get services that begin with a search string and an exclusion</span></span>

<span data-ttu-id="36409-124">이 예제에서는 WinRM 서비스를 제외 하 고 서비스 이름이 **win** 으로 시작 하는 서비스만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="36409-124">This example only gets the services with service names that begin with **win**, except for the WinRM service.</span></span>

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

### <span data-ttu-id="36409-125">예 5: 현재 활성화 된 서비스 표시</span><span class="sxs-lookup"><span data-stu-id="36409-125">Example 5: Display services that are currently active</span></span>

<span data-ttu-id="36409-126">이 예에서는 실행 중 상태의 서비스만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-126">This example displays only the services with a status of Running.</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

<span data-ttu-id="36409-127">`Get-Service` 컴퓨터의 모든 서비스를 가져오고 개체를 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="36409-127">`Get-Service` gets all the services on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="36409-128">`Where-Object`Cmdlet은 실행 중인 **상태** 속성의 서비스만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-128">The `Where-Object` cmdlet, selects only the services with a **Status** property that equals Running.</span></span>

<span data-ttu-id="36409-129">Status는 서비스 개체의 속성 중 하나에 불과합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-129">Status is only one property of service objects.</span></span> <span data-ttu-id="36409-130">모든 속성을 보려면를 입력 `Get-Service | Get-Member` 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-130">To see all of the properties, type `Get-Service | Get-Member`.</span></span>

### <span data-ttu-id="36409-131">예 6: 종속 서비스가 있는 컴퓨터의 서비스 나열</span><span class="sxs-lookup"><span data-stu-id="36409-131">Example 6: List the services on the computer that have dependent services</span></span>

<span data-ttu-id="36409-132">이 예제에서는 종속 서비스가 있는 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="36409-132">This example gets services that have dependent services.</span></span>

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

<span data-ttu-id="36409-133">`Get-Service`Cmdlet은 컴퓨터의 모든 서비스를 가져오고 개체를 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="36409-133">The `Get-Service` cmdlet gets all the services on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="36409-134">`Where-Object`Cmdlet은 **DependentServices** 속성이 null이 아닌 서비스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-134">The `Where-Object` cmdlet selects the services whose **DependentServices** property isn't null.</span></span>

<span data-ttu-id="36409-135">결과는 파이프라인에서 cmdlet으로 전송 됩니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="36409-135">The results are sent down the pipeline to the `Format-List` cmdlet.</span></span> <span data-ttu-id="36409-136">**Property** 매개 변수는 서비스의 이름, 종속 된 서비스의 이름 및 각 서비스에 대 한 종속 서비스의 수를 표시 하는 계산 된 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-136">The **Property** parameter displays the name of the service, the name of the dependent services, and a calculated property that displays the number of dependent services for each service.</span></span>

### <span data-ttu-id="36409-137">예제 7: 속성 값으로 서비스 정렬</span><span class="sxs-lookup"><span data-stu-id="36409-137">Example 7: Sort services by property value</span></span>

<span data-ttu-id="36409-138">이 예에서는 서비스를 해당 **상태** 속성 값으로 오름차순으로 정렬 하는 경우 서비스를 실행 하기 전에 중지 된 서비스를 표시 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="36409-138">This example shows that when you sort services in ascending order by the value of their **Status** property, stopped services appear before running services.</span></span> <span data-ttu-id="36409-139">그 이유는 **Status** 값이 열거형 이며,이는 중지 된 값이 1이 고 실행의 값은 4 이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="36409-139">The reason is because the value of **Status** is an enumeration, in which Stopped has a value of 1, and Running has a value of 4.</span></span> <span data-ttu-id="36409-140">자세한 내용은 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36409-140">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

<span data-ttu-id="36409-141">실행 중인 서비스를 먼저 나열 하려면 cmdlet의 **내림차순** 매개 변수를 사용 합니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="36409-141">To list running services first, use the **Descending** parameter of the `Sort-Object` cmdlet.</span></span>

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

### <span data-ttu-id="36409-142">예 8: 서비스의 종속 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="36409-142">Example 8: Get the dependent services of a service</span></span>

<span data-ttu-id="36409-143">이 예제에서는 WinRM 서비스에 필요한 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="36409-143">This example gets the services that the WinRM service requires.</span></span> <span data-ttu-id="36409-144">서비스의 **ServicesDependedOn** 속성 값이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36409-144">The value of the service's **ServicesDependedOn** property is returned.</span></span>

```powershell
Get-Service "WinRM" -RequiredServices
```

### <span data-ttu-id="36409-145">예 9: 파이프라인 연산자를 통해 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="36409-145">Example 9: Get a service through the pipeline operator</span></span>

<span data-ttu-id="36409-146">이 예제에서는 로컬 컴퓨터의 WinRM 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="36409-146">This example gets the WinRM service on the local computer.</span></span> <span data-ttu-id="36409-147">따옴표로 묶인 서비스 이름 문자열은 파이프라인에서로 전송 됩니다 `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="36409-147">The service name string, enclosed in quotation marks, is sent down the pipeline to `Get-Service`.</span></span>

```powershell
"WinRM" | Get-Service
```

## <span data-ttu-id="36409-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="36409-148">PARAMETERS</span></span>

### <span data-ttu-id="36409-149">-DependentServices</span><span class="sxs-lookup"><span data-stu-id="36409-149">-DependentServices</span></span>

<span data-ttu-id="36409-150">이 cmdlet은 지정 된 서비스에 종속 된 서비스만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="36409-150">Indicates that this cmdlet gets only the services that depend upon the specified service.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36409-151">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="36409-151">-DisplayName</span></span>

<span data-ttu-id="36409-152">검색할 서비스의 표시 이름을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-152">Specifies, as a string array, the display names of services to be retrieved.</span></span> <span data-ttu-id="36409-153">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="36409-153">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="36409-154">-제외</span><span class="sxs-lookup"><span data-stu-id="36409-154">-Exclude</span></span>

<span data-ttu-id="36409-155">이 cmdlet이 작업에서 제외 하는 서비스 또는 서비스를 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-155">Specifies, as a string array, a service or services that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="36409-156">이 매개 변수 값은 **Name** 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-156">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="36409-157">이름 요소 또는 패턴 (예:)을 입력 `s*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-157">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="36409-158">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="36409-158">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="36409-159">-포함</span><span class="sxs-lookup"><span data-stu-id="36409-159">-Include</span></span>

<span data-ttu-id="36409-160">이 cmdlet이 작업에 포함 하는 서비스 또는 서비스를 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-160">Specifies, as a string array, a service or services that this cmdlet includes in the operation.</span></span> <span data-ttu-id="36409-161">이 매개 변수 값은 **Name** 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-161">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="36409-162">이름 요소 또는 패턴 (예:)을 입력 `s*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-162">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="36409-163">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="36409-163">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="36409-164">-InputObject</span><span class="sxs-lookup"><span data-stu-id="36409-164">-InputObject</span></span>

<span data-ttu-id="36409-165">검색할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-165">Specifies **ServiceController** objects representing the services to be retrieved.</span></span> <span data-ttu-id="36409-166">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="36409-166">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="36409-167">서비스 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36409-167">You can pipe a service object to this cmdlet.</span></span>

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

### <span data-ttu-id="36409-168">-Name</span><span class="sxs-lookup"><span data-stu-id="36409-168">-Name</span></span>

<span data-ttu-id="36409-169">검색할 서비스의 표시 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-169">Specifies the service names of services to be retrieved.</span></span> <span data-ttu-id="36409-170">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="36409-170">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="36409-171">-RequiredServices</span><span class="sxs-lookup"><span data-stu-id="36409-171">-RequiredServices</span></span>

<span data-ttu-id="36409-172">이 cmdlet은이 서비스에 필요한 서비스만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="36409-172">Indicates that this cmdlet gets only the services that this service requires.</span></span> <span data-ttu-id="36409-173">이 매개 변수는 서비스의 **ServicesDependedOn** 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="36409-173">This parameter gets the value of the **ServicesDependedOn** property of the service.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="36409-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36409-174">CommonParameters</span></span>

<span data-ttu-id="36409-175">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="36409-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="36409-176">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="36409-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="36409-177">입력</span><span class="sxs-lookup"><span data-stu-id="36409-177">INPUTS</span></span>

### <span data-ttu-id="36409-178">ServiceController, System.string입니다.</span><span class="sxs-lookup"><span data-stu-id="36409-178">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="36409-179">서비스 개체 또는 서비스 이름을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36409-179">You can pipe a service object or a service name to this cmdlet.</span></span>

## <span data-ttu-id="36409-180">출력</span><span class="sxs-lookup"><span data-stu-id="36409-180">OUTPUTS</span></span>

### <span data-ttu-id="36409-181">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="36409-181">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="36409-182">이 cmdlet은 컴퓨터의 서비스를 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-182">This cmdlet returns objects that represent the services on the computer.</span></span>

## <span data-ttu-id="36409-183">참고</span><span class="sxs-lookup"><span data-stu-id="36409-183">NOTES</span></span>

<span data-ttu-id="36409-184">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36409-184">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="36409-185">PowerShell 6.0부터 다음 속성이 **ServiceController** 개체에 추가 됩니다. **사용자 이름**, **설명**, **Delayedautostart** 시작, **BinaryPathName** 및 **startuptype** .</span><span class="sxs-lookup"><span data-stu-id="36409-185">Beginning in PowerShell 6.0, the following properties are added to the **ServiceController** objects: **UserName**, **Description**, **DelayedAutoStart**, **BinaryPathName**, and **StartupType** .</span></span>

<span data-ttu-id="36409-186">의 기본 제공 별칭인를 참조할 수도 있습니다 `Get-Service` `gsv` .</span><span class="sxs-lookup"><span data-stu-id="36409-186">You can also refer to `Get-Service` by its built-in alias, `gsv`.</span></span> <span data-ttu-id="36409-187">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36409-187">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="36409-188">이 cmdlet은 현재 사용자가 해당 서비스를 볼 수 있는 권한을 가진 경우에만 서비스를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36409-188">This cmdlet can display services only when the current user has permission to see them.</span></span> <span data-ttu-id="36409-189">이 cmdlet이 서비스를 표시 하지 않는 경우 해당 서비스를 볼 수 있는 권한이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36409-189">If this cmdlet does not display services, you might not have permission to see them.</span></span>

<span data-ttu-id="36409-190">시스템에 있는 각 서비스의 서비스 이름 및 표시 이름을 찾으려면를 입력 `Get-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-190">To find the service name and display name of each service on your system, type `Get-Service`.</span></span> <span data-ttu-id="36409-191">서비스 이름은 Name 열에 나타나고 표시 이름은 **DisplayName** 열에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="36409-191">The service names appear in the Name column, and the display names appear in the **DisplayName** column.</span></span>

<span data-ttu-id="36409-192">**상태** 속성의 값을 기준으로 오름차순으로 정렬 하는 경우 서비스를 실행 하기 전에 중지 된 서비스가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36409-192">When you sort in ascending order by the **Status** property's value, Stopped services appear before Running services.</span></span> <span data-ttu-id="36409-193">서비스의 **status** 속성은 열거형 값이 고 상태 이름은 정수 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="36409-193">The service's **Status** property is an enumerated value and the status names represent integer values.</span></span> <span data-ttu-id="36409-194">정렬 순서는 이름이 아니라 정수 값을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="36409-194">The sort order is based on the integer value, not the name.</span></span> <span data-ttu-id="36409-195">중지 됨은의 값이 1이 고 실행의 값은 4 이기 때문에 중지 된 것으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="36409-195">Stopped appears before because Running because Stopped has a value of 1, and Running has a value of 4.</span></span> <span data-ttu-id="36409-196">자세한 내용은 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36409-196">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

## <span data-ttu-id="36409-197">관련 링크</span><span class="sxs-lookup"><span data-stu-id="36409-197">RELATED LINKS</span></span>

[<span data-ttu-id="36409-198">New-Service</span><span class="sxs-lookup"><span data-stu-id="36409-198">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="36409-199">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="36409-199">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="36409-200">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="36409-200">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="36409-201">Set-Service</span><span class="sxs-lookup"><span data-stu-id="36409-201">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="36409-202">Start-Service</span><span class="sxs-lookup"><span data-stu-id="36409-202">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="36409-203">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="36409-203">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="36409-204">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="36409-204">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="36409-205">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="36409-205">Remove-Service</span></span>](Remove-Service.md)
