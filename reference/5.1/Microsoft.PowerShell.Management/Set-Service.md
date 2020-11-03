---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: df4fda68508e21700235d2b772c6dd43c8e1fe1e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214417"
---
# <span data-ttu-id="b0152-103">Set-Service</span><span class="sxs-lookup"><span data-stu-id="b0152-103">Set-Service</span></span>

## <span data-ttu-id="b0152-104">개요</span><span class="sxs-lookup"><span data-stu-id="b0152-104">SYNOPSIS</span></span>
<span data-ttu-id="b0152-105">서비스를 시작, 중지 및 일시 중단하고 해당 속성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-105">Starts, stops, and suspends a service, and changes its properties.</span></span>

## <span data-ttu-id="b0152-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b0152-106">SYNTAX</span></span>

### <span data-ttu-id="b0152-107">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="b0152-107">Name (Default)</span></span>

```
Set-Service [-ComputerName <String[]>] [-Name] <String> [-DisplayName <String>]
 [-Description <String>] [-StartupType <ServiceStartMode>] [-Status <String>] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b0152-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="b0152-108">InputObject</span></span>

```
Set-Service [-ComputerName <String[]>] [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Status <String>] [-InputObject <ServiceController>] [-PassThru]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b0152-109">설명</span><span class="sxs-lookup"><span data-stu-id="b0152-109">DESCRIPTION</span></span>

<span data-ttu-id="b0152-110">`Set-Service`Cmdlet은 **상태** , **설명** , **DisplayName** , **startuptype** 등의 서비스 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-110">The `Set-Service` cmdlet changes the properties of a service such as the **Status** , **Description** , **DisplayName** , and **StartupType** .</span></span> <span data-ttu-id="b0152-111">`Set-Service` 서비스를 시작, 중지, 일시 중지 또는 일시 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-111">`Set-Service` can start, stop, suspend, or pause a service.</span></span> <span data-ttu-id="b0152-112">서비스를 식별 하려면 해당 서비스 이름을 입력 하거나 서비스 개체를 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-112">To identify a service, enter its service name or submit a service object.</span></span> <span data-ttu-id="b0152-113">또는 파이프라인에서 서비스 이름 또는 서비스 개체를로 보냅니다 `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="b0152-113">Or, send a service name or service object down the pipeline to `Set-Service`.</span></span>

## <span data-ttu-id="b0152-114">예제</span><span class="sxs-lookup"><span data-stu-id="b0152-114">EXAMPLES</span></span>

### <span data-ttu-id="b0152-115">예제 1: 표시 이름 변경</span><span class="sxs-lookup"><span data-stu-id="b0152-115">Example 1: Change a display name</span></span>

<span data-ttu-id="b0152-116">이 예제에서는 서비스의 표시 이름이 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-116">In this example, a service's display name is changed.</span></span> <span data-ttu-id="b0152-117">원래 표시 이름을 보려면를 사용 `Get-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-117">To view the original display name, use `Get-Service`.</span></span>

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

<span data-ttu-id="b0152-118">`Set-Service`**name** 매개 변수를 사용 하 여 서비스의 이름인 **LanmanWorkstation** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-118">`Set-Service` uses the **Name** parameter to specify the service's name, **LanmanWorkstation** .</span></span> <span data-ttu-id="b0152-119">**DisplayName** 매개 변수는 새 표시 이름인 **LanMan Workstation** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-119">The **DisplayName** parameter specifies the new display name, **LanMan Workstation** .</span></span>

### <span data-ttu-id="b0152-120">예 2: 서비스의 시작 유형 변경</span><span class="sxs-lookup"><span data-stu-id="b0152-120">Example 2: Change the startup type of services</span></span>

<span data-ttu-id="b0152-121">이 예제에서는 서비스의 시작 유형을 변경 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-121">This example shows how to change a service's startup type.</span></span>

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

<span data-ttu-id="b0152-122">`Set-Service`**name** 매개 변수를 사용 하 여 서비스의 이름 ( **비트** )을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-122">`Set-Service` uses the **Name** parameter to specify the service's name, **BITS** .</span></span> <span data-ttu-id="b0152-123">**Startuptype** 매개 변수는 서비스를 **자동** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-123">The **StartupType** parameter sets the service to **Automatic** .</span></span>

<span data-ttu-id="b0152-124">`Get-Service`**Name** 매개 변수를 사용 하 여 **BITS** 서비스를 지정 하 고 개체를 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-124">`Get-Service` uses the **Name** parameter to specify the **BITS** service and sends the object down the pipeline.</span></span> <span data-ttu-id="b0152-125">`Select-Object`**Property** 매개 변수를 사용 하 여 **BITS** 서비스의 상태를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-125">`Select-Object` uses the **Property** parameter to display the **BITS** service's status.</span></span>

### <span data-ttu-id="b0152-126">예 3: 서비스에 대 한 설명 변경</span><span class="sxs-lookup"><span data-stu-id="b0152-126">Example 3: Change the description of a service</span></span>

<span data-ttu-id="b0152-127">이 예에서는 BITS 서비스의 설명을 변경 하 고 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-127">This example changes the BITS service's description and displays the result.</span></span>

<span data-ttu-id="b0152-128">`Get-CimInstance`Cmdlet은 서비스의 **설명을** 포함 하는 **Win32_Service** 개체를 반환 하기 때문에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-128">The `Get-CimInstance` cmdlet is used because it returns a **Win32_Service** object that includes the service's **Description** .</span></span>

```powershell
Get-CimInstance Win32_Service -Filter 'Name = "BITS"'  | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth. If the service is
              disabled, then any applications that depend on BITS, such as Windows Update or MSN
              Explorer, will be unable to automatically download programs and other information.
```

```powershell
Set-Service -Name BITS -Description "Transfers files in the background using idle network bandwidth."
Get-CimInstance Win32_Service -Filter 'Name = "BITS"' | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth.
```

<span data-ttu-id="b0152-129">`Get-CimInstance` 개체를 파이프라인에서 아래로 보내고 `Format-List` 서비스의 이름과 설명을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-129">`Get-CimInstance` sends the object down the pipeline to `Format-List` and displays the service's name and description.</span></span> <span data-ttu-id="b0152-130">비교를 위해이 명령은 설명이 업데이트 되기 전후에 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-130">For comparison purposes, the command is run before and after the description is updated.</span></span>

<span data-ttu-id="b0152-131">`Set-Service`**Name** 매개 변수를 사용 하 여 **BITS** 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-131">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="b0152-132">**Description** 매개 변수는 서비스 설명에 대 한 업데이트 된 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-132">The **Description** parameter specifies the updated text for the services' description.</span></span>

### <span data-ttu-id="b0152-133">예제 4: 서비스 시작</span><span class="sxs-lookup"><span data-stu-id="b0152-133">Example 4: Start a service</span></span>

<span data-ttu-id="b0152-134">이 예제에서는 서비스가 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-134">In this example, a service is started.</span></span>

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

<span data-ttu-id="b0152-135">`Set-Service`**Name** 매개 변수를 사용 하 여 **WinRM** 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-135">`Set-Service` uses the **Name** parameter to specify the service, **WinRM** .</span></span> <span data-ttu-id="b0152-136">**Status** 매개 변수는 **실행** 값을 사용 하 여 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-136">The **Status** parameter uses the value **Running** to start the service.</span></span> <span data-ttu-id="b0152-137">**PassThru** 매개 변수는 결과를 표시 하는 **ServiceController** 개체를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-137">The **PassThru** parameter outputs a **ServiceController** object that displays the results.</span></span>

### <span data-ttu-id="b0152-138">예 5: 서비스 일시 중단</span><span class="sxs-lookup"><span data-stu-id="b0152-138">Example 5: Suspend a service</span></span>

<span data-ttu-id="b0152-139">이 예제에서는 파이프라인을 사용 하 여 서비스를 일시 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-139">This example uses the pipeline to pause to service.</span></span>

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

<span data-ttu-id="b0152-140">`Get-Service`**Name** 매개 변수를 사용 하 여 **일정** 서비스를 지정 하 고 개체를 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-140">`Get-Service` uses the **Name** parameter to specify the **Schedule** service, and sends the object down the pipeline.</span></span> <span data-ttu-id="b0152-141">`Set-Service`**Status** 매개 변수를 사용 하 여 서비스를 **일시 중지 됨으로** 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-141">`Set-Service` uses the **Status** parameter to set the service to **Paused** .</span></span>

### <span data-ttu-id="b0152-142">예 6: 서비스 중지</span><span class="sxs-lookup"><span data-stu-id="b0152-142">Example 6: Stop a service</span></span>

<span data-ttu-id="b0152-143">이 예에서는 변수를 사용 하 여 서비스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-143">This example uses a variable to stop a service.</span></span>

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

<span data-ttu-id="b0152-144">`Get-Service`**Name** 매개 변수를 사용 하 여 서비스, **예약** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-144">`Get-Service` uses the **Name** parameter to specify the service, **Schedule** .</span></span> <span data-ttu-id="b0152-145">개체는 변수에 저장 됩니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="b0152-145">The object is stored in the variable, `$S`.</span></span> <span data-ttu-id="b0152-146">`Set-Service`**InputObject** 매개 변수를 사용 하 고 저장 된 개체를 지정 합니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="b0152-146">`Set-Service` uses the **InputObject** parameter and specifies the object stored `$S`.</span></span> <span data-ttu-id="b0152-147">**상태** 매개 변수는 서비스를 **중지 됨** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-147">The **Status** parameter sets the service to **Stopped** .</span></span>

## <span data-ttu-id="b0152-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b0152-148">PARAMETERS</span></span>

### <span data-ttu-id="b0152-149">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="b0152-149">-ComputerName</span></span>

<span data-ttu-id="b0152-150">컴퓨터를 하나 이상 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-150">Specifies one or more computers.</span></span> <span data-ttu-id="b0152-151">원격 컴퓨터의 경우 NetBIOS 이름, IP 주소 또는 정규화 된 도메인 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-151">For remote computers, type the NetBIOS name, an IP address, or a fully qualified domain name.</span></span> <span data-ttu-id="b0152-152">**ComputerName** 매개 변수가 지정 되지 않은 경우 명령은 로컬 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-152">If the **ComputerName** parameter isn't specified, the command runs on the local computer.</span></span>

<span data-ttu-id="b0152-153">이 매개 변수는 PowerShell 원격을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-153">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="b0152-154">컴퓨터에서 원격 명령을 실행 하도록 구성 되지 않은 경우에도 **ComputerName** 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-154">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b0152-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b0152-155">-Confirm</span></span>

<span data-ttu-id="b0152-156">실행 하기 전에 확인 메시지를 표시 `Set-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-156">Prompts you for confirmation before running `Set-Service`.</span></span>

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

### <span data-ttu-id="b0152-157">-Description</span><span class="sxs-lookup"><span data-stu-id="b0152-157">-Description</span></span>

<span data-ttu-id="b0152-158">서비스에 대한 새 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-158">Specifies a new description for the service.</span></span>

<span data-ttu-id="b0152-159">서비스 설명은 **컴퓨터 관리, 서비스** 에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-159">The service description appears in **Computer Management, Services** .</span></span> <span data-ttu-id="b0152-160">**설명은** `Get-Service` **ServiceController** 개체의 속성이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-160">The **Description** isn't a property of the `Get-Service` **ServiceController** object.</span></span> <span data-ttu-id="b0152-161">서비스 설명을 보려면 `Get-CimInstance` 서비스를 나타내는 **Win32_Service** 개체를 반환 하는를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-161">To see the service description, use `Get-CimInstance` that returns a **Win32_Service** object that represents the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0152-162">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="b0152-162">-DisplayName</span></span>

<span data-ttu-id="b0152-163">서비스의 새 표시 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-163">Specifies a new display name for the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: DN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0152-164">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b0152-164">-InputObject</span></span>

<span data-ttu-id="b0152-165">변경할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-165">Specifies a **ServiceController** object that represents the service to change.</span></span> <span data-ttu-id="b0152-166">개체를 포함 하는 변수를 입력 하거나 개체를 가져오는 명령 또는 식 (예: 명령)을 입력 합니다 `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="b0152-166">Enter a variable that contains the object, or type a command or expression that gets the object, such as a `Get-Service` command.</span></span> <span data-ttu-id="b0152-167">파이프라인을 사용 하 여 서비스 개체를로 보낼 수 있습니다 `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="b0152-167">You can use the pipeline to send a service object to `Set-Service`.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b0152-168">-Name</span><span class="sxs-lookup"><span data-stu-id="b0152-168">-Name</span></span>

<span data-ttu-id="b0152-169">변경할 서비스의 서비스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-169">Specifies the service name of the service to be changed.</span></span> <span data-ttu-id="b0152-170">와일드 카드 문자는 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-170">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="b0152-171">파이프라인을 사용 하 여 서비스 이름을로 보낼 수 있습니다 `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="b0152-171">You can use the pipeline to send a service name to `Set-Service`.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b0152-172">-PassThru</span><span class="sxs-lookup"><span data-stu-id="b0152-172">-PassThru</span></span>

<span data-ttu-id="b0152-173">변경 된 서비스를 나타내는 **ServiceController** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-173">Returns a **ServiceController** object that represents the services that were changed.</span></span> <span data-ttu-id="b0152-174">기본적으로는 `Set-Service` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-174">By default, `Set-Service` doesn't generate any output.</span></span>

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

### <span data-ttu-id="b0152-175">-StartupType</span><span class="sxs-lookup"><span data-stu-id="b0152-175">-StartupType</span></span>

<span data-ttu-id="b0152-176">서비스의 시작 유형을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-176">Sets the startup type of the service.</span></span> <span data-ttu-id="b0152-177">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-177">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b0152-178">**자동** -시스템이 시작 되거나 운영 체제에서 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-178">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="b0152-179">자동으로 시작된 서비스가 수동으로 시작된 서비스에 따라 달라지는 경우, 시스템 시작 시 수동으로 시작된 서비스도 자동으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-179">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="b0152-180">**사용 안 함** -서비스를 사용할 수 없으며 사용자 또는 응용 프로그램에서 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-180">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="b0152-181">**수동** -서비스 제어 관리자 또는 응용 프로그램을 사용 하 여 수동으로 또는 사용자가 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-181">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>
- <span data-ttu-id="b0152-182">**Boot** -서비스가 시스템 로더에서 시작한 장치 드라이버 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-182">**Boot** - Indicates that the service is a device driver started by the system loader.</span></span> <span data-ttu-id="b0152-183">이 값은 디바이스 드라이버에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-183">This value is valid only for device drivers.</span></span>
- <span data-ttu-id="b0152-184">**시스템** -서비스가 ' IOInitSystem () ' 함수에서 시작한 장치 드라이버 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-184">**System** - Indicates that the service is a device driver started by the 'IOInitSystem()' function.</span></span> <span data-ttu-id="b0152-185">이 값은 디바이스 드라이버에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-185">This value is valid only for device drivers.</span></span>

 <span data-ttu-id="b0152-186">기본값은 **Automatic** 입니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-186">The default value is **Automatic** .</span></span>

```yaml
Type: System.ServiceProcess.ServiceStartMode
Parameter Sets: (All)
Aliases: StartMode, SM, ST
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0152-187">-상태</span><span class="sxs-lookup"><span data-stu-id="b0152-187">-Status</span></span>

<span data-ttu-id="b0152-188">서비스의 상태를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-188">Specifies the status for the service.</span></span>

<span data-ttu-id="b0152-189">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-189">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="b0152-190">**일시 중지 됨** .</span><span class="sxs-lookup"><span data-stu-id="b0152-190">**Paused** .</span></span> <span data-ttu-id="b0152-191">서비스를 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-191">Suspends the service.</span></span>
- <span data-ttu-id="b0152-192">**실행 중** .</span><span class="sxs-lookup"><span data-stu-id="b0152-192">**Running** .</span></span> <span data-ttu-id="b0152-193">서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-193">Starts the service.</span></span>
- <span data-ttu-id="b0152-194">**중지 됨** .</span><span class="sxs-lookup"><span data-stu-id="b0152-194">**Stopped** .</span></span> <span data-ttu-id="b0152-195">서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-195">Stops the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Paused, Running, Stopped

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0152-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b0152-196">-WhatIf</span></span>

<span data-ttu-id="b0152-197">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="b0152-197">Shows what would happen if `Set-Service` runs.</span></span> <span data-ttu-id="b0152-198">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-198">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="b0152-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b0152-199">CommonParameters</span></span>

<span data-ttu-id="b0152-200">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b0152-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b0152-201">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b0152-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b0152-202">입력</span><span class="sxs-lookup"><span data-stu-id="b0152-202">INPUTS</span></span>

### <span data-ttu-id="b0152-203">ServiceController, System.string입니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-203">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="b0152-204">파이프라인을 사용 하 여 서비스 개체 또는 서비스 이름이 포함 된 문자열을로 보낼 수 있습니다 `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="b0152-204">You can use the pipeline to send a service object or a string that contains a service name to `Set-Service`.</span></span>

## <span data-ttu-id="b0152-205">출력</span><span class="sxs-lookup"><span data-stu-id="b0152-205">OUTPUTS</span></span>

### <span data-ttu-id="b0152-206">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="b0152-206">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="b0152-207">기본적으로는 `Set-Service` 개체를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-207">By default, `Set-Service` doesn't return any objects.</span></span> <span data-ttu-id="b0152-208">**PassThru** 매개 변수를 사용 하 여 **ServiceController** 개체를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-208">Use the **PassThru** parameter to output a **ServiceController** object.</span></span>

## <span data-ttu-id="b0152-209">참고</span><span class="sxs-lookup"><span data-stu-id="b0152-209">NOTES</span></span>

<span data-ttu-id="b0152-210">`Set-Service` 높은 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-210">`Set-Service` requires elevated permissions.</span></span> <span data-ttu-id="b0152-211">**관리자 권한으로 실행** 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-211">Use the **Run as administrator** option.</span></span>

<span data-ttu-id="b0152-212">`Set-Service` 현재 사용자에 게 서비스를 관리할 수 있는 권한이 있는 경우에만 서비스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-212">`Set-Service` can only control services when the current user has permissions to manage services.</span></span> <span data-ttu-id="b0152-213">명령이 제대로 작동 하지 않는 경우 필요한 권한이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-213">If a command doesn't work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="b0152-214">서비스의 서비스 이름 또는 표시 이름을 찾으려면를 사용 `Get-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-214">To find a service's service name or display name, use `Get-Service`.</span></span> <span data-ttu-id="b0152-215">서비스 이름은 **Name** 열에 있고 표시 이름은 **DisplayName** 열에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0152-215">The service names are in the **Name** column and the display names are in the **DisplayName** column.</span></span>

## <span data-ttu-id="b0152-216">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b0152-216">RELATED LINKS</span></span>

[<span data-ttu-id="b0152-217">Get-Service</span><span class="sxs-lookup"><span data-stu-id="b0152-217">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="b0152-218">New-Service</span><span class="sxs-lookup"><span data-stu-id="b0152-218">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="b0152-219">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="b0152-219">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="b0152-220">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="b0152-220">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="b0152-221">Start-Service</span><span class="sxs-lookup"><span data-stu-id="b0152-221">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="b0152-222">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="b0152-222">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="b0152-223">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="b0152-223">Suspend-Service</span></span>](Suspend-Service.md)
