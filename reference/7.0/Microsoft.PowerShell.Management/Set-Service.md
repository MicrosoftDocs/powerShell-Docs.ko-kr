---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: d58d26a93e9b785bcba425537ea570feeffa1606
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210625"
---
# <span data-ttu-id="5521f-103">Set-Service</span><span class="sxs-lookup"><span data-stu-id="5521f-103">Set-Service</span></span>

## <span data-ttu-id="5521f-104">개요</span><span class="sxs-lookup"><span data-stu-id="5521f-104">SYNOPSIS</span></span>
<span data-ttu-id="5521f-105">서비스를 시작, 중지 및 일시 중단하고 해당 속성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-105">Starts, stops, and suspends a service, and changes its properties.</span></span>

## <span data-ttu-id="5521f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5521f-106">SYNTAX</span></span>

### <span data-ttu-id="5521f-107">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="5521f-107">Name (Default)</span></span>

```
Set-Service [-Name] <String> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-Status <String>]
 [-SecurityDescriptorSddl <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5521f-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="5521f-108">InputObject</span></span>

```
Set-Service [-InputObject] <ServiceController> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-SecurityDescriptorSddl <String>]
 [-Status <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5521f-109">설명</span><span class="sxs-lookup"><span data-stu-id="5521f-109">DESCRIPTION</span></span>

<span data-ttu-id="5521f-110">`Set-Service`Cmdlet은 **상태** , **설명** , **DisplayName** , **startuptype** 등의 서비스 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-110">The `Set-Service` cmdlet changes the properties of a service such as the **Status** , **Description** , **DisplayName** , and **StartupType** .</span></span> <span data-ttu-id="5521f-111">`Set-Service` 서비스를 시작, 중지, 일시 중지 또는 일시 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-111">`Set-Service` can start, stop, suspend, or pause a service.</span></span> <span data-ttu-id="5521f-112">서비스를 식별 하려면 해당 서비스 이름을 입력 하거나 서비스 개체를 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-112">To identify a service, enter its service name or submit a service object.</span></span> <span data-ttu-id="5521f-113">또는 파이프라인에서 서비스 이름 또는 서비스 개체를로 보냅니다 `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="5521f-113">Or, send a service name or service object down the pipeline to `Set-Service`.</span></span>

## <span data-ttu-id="5521f-114">예제</span><span class="sxs-lookup"><span data-stu-id="5521f-114">EXAMPLES</span></span>

### <span data-ttu-id="5521f-115">예제 1: 표시 이름 변경</span><span class="sxs-lookup"><span data-stu-id="5521f-115">Example 1: Change a display name</span></span>

<span data-ttu-id="5521f-116">이 예제에서는 서비스의 표시 이름이 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-116">In this example, a service's display name is changed.</span></span> <span data-ttu-id="5521f-117">원래 표시 이름을 보려면를 사용 `Get-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-117">To view the original display name, use `Get-Service`.</span></span>

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

<span data-ttu-id="5521f-118">`Set-Service`**name** 매개 변수를 사용 하 여 서비스의 이름인 **LanmanWorkstation** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-118">`Set-Service` uses the **Name** parameter to specify the service's name, **LanmanWorkstation** .</span></span> <span data-ttu-id="5521f-119">**DisplayName** 매개 변수는 새 표시 이름인 **LanMan Workstation** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-119">The **DisplayName** parameter specifies the new display name, **LanMan Workstation** .</span></span>

### <span data-ttu-id="5521f-120">예 2: 서비스의 시작 유형 변경</span><span class="sxs-lookup"><span data-stu-id="5521f-120">Example 2: Change the startup type of services</span></span>

<span data-ttu-id="5521f-121">이 예제에서는 서비스의 시작 유형을 변경 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-121">This example shows how to change a service's startup type.</span></span>

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

<span data-ttu-id="5521f-122">`Set-Service`**name** 매개 변수를 사용 하 여 서비스의 이름 ( **비트** )을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-122">`Set-Service` uses the **Name** parameter to specify the service's name, **BITS** .</span></span> <span data-ttu-id="5521f-123">**Startuptype** 매개 변수는 서비스를 **자동** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-123">The **StartupType** parameter sets the service to **Automatic** .</span></span>

<span data-ttu-id="5521f-124">`Get-Service`**Name** 매개 변수를 사용 하 여 **BITS** 서비스를 지정 하 고 개체를 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-124">`Get-Service` uses the **Name** parameter to specify the **BITS** service and sends the object down the pipeline.</span></span> <span data-ttu-id="5521f-125">`Select-Object`**Property** 매개 변수를 사용 하 여 **BITS** 서비스의 상태를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-125">`Select-Object` uses the **Property** parameter to display the **BITS** service's status.</span></span>

### <span data-ttu-id="5521f-126">예 3: 서비스에 대 한 설명 변경</span><span class="sxs-lookup"><span data-stu-id="5521f-126">Example 3: Change the description of a service</span></span>

<span data-ttu-id="5521f-127">이 예에서는 BITS 서비스의 설명을 변경 하 고 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-127">This example changes the BITS service's description and displays the result.</span></span>

<span data-ttu-id="5521f-128">`Get-CimInstance`Cmdlet은 서비스의 **설명을** 포함 하는 **Win32_Service** 개체를 반환 하기 때문에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-128">The `Get-CimInstance` cmdlet is used because it returns a **Win32_Service** object that includes the service's **Description** .</span></span>

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

<span data-ttu-id="5521f-129">`Get-CimInstance` 개체를 파이프라인에서 아래로 보내고 `Format-List` 서비스의 이름과 설명을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-129">`Get-CimInstance` sends the object down the pipeline to `Format-List` and displays the service's name and description.</span></span> <span data-ttu-id="5521f-130">비교를 위해이 명령은 설명이 업데이트 되기 전후에 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-130">For comparison purposes, the command is run before and after the description is updated.</span></span>

<span data-ttu-id="5521f-131">`Set-Service`**Name** 매개 변수를 사용 하 여 **BITS** 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-131">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="5521f-132">**Description** 매개 변수는 서비스 설명에 대 한 업데이트 된 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-132">The **Description** parameter specifies the updated text for the services' description.</span></span>

### <span data-ttu-id="5521f-133">예제 4: 서비스 시작</span><span class="sxs-lookup"><span data-stu-id="5521f-133">Example 4: Start a service</span></span>

<span data-ttu-id="5521f-134">이 예제에서는 서비스가 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-134">In this example, a service is started.</span></span>

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

<span data-ttu-id="5521f-135">`Set-Service`**Name** 매개 변수를 사용 하 여 **WinRM** 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-135">`Set-Service` uses the **Name** parameter to specify the service, **WinRM** .</span></span> <span data-ttu-id="5521f-136">**Status** 매개 변수는 **실행** 값을 사용 하 여 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-136">The **Status** parameter uses the value **Running** to start the service.</span></span> <span data-ttu-id="5521f-137">**PassThru** 매개 변수는 결과를 표시 하는 **ServiceController** 개체를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-137">The **PassThru** parameter outputs a **ServiceController** object that displays the results.</span></span>

### <span data-ttu-id="5521f-138">예 5: 서비스 일시 중단</span><span class="sxs-lookup"><span data-stu-id="5521f-138">Example 5: Suspend a service</span></span>

<span data-ttu-id="5521f-139">이 예제에서는 파이프라인을 사용 하 여 서비스를 일시 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-139">This example uses the pipeline to pause to service.</span></span>

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

<span data-ttu-id="5521f-140">`Get-Service`**Name** 매개 변수를 사용 하 여 **일정** 서비스를 지정 하 고 개체를 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-140">`Get-Service` uses the **Name** parameter to specify the **Schedule** service, and sends the object down the pipeline.</span></span> <span data-ttu-id="5521f-141">`Set-Service`**Status** 매개 변수를 사용 하 여 서비스를 **일시 중지 됨으로** 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-141">`Set-Service` uses the **Status** parameter to set the service to **Paused** .</span></span>

### <span data-ttu-id="5521f-142">예 6: 서비스 중지</span><span class="sxs-lookup"><span data-stu-id="5521f-142">Example 6: Stop a service</span></span>

<span data-ttu-id="5521f-143">이 예에서는 변수를 사용 하 여 서비스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-143">This example uses a variable to stop a service.</span></span>

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

<span data-ttu-id="5521f-144">`Get-Service`**Name** 매개 변수를 사용 하 여 서비스, **예약** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-144">`Get-Service` uses the **Name** parameter to specify the service, **Schedule** .</span></span> <span data-ttu-id="5521f-145">개체는 변수에 저장 됩니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="5521f-145">The object is stored in the variable, `$S`.</span></span> <span data-ttu-id="5521f-146">`Set-Service`**InputObject** 매개 변수를 사용 하 고 저장 된 개체를 지정 합니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="5521f-146">`Set-Service` uses the **InputObject** parameter and specifies the object stored `$S`.</span></span> <span data-ttu-id="5521f-147">**상태** 매개 변수는 서비스를 **중지 됨** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-147">The **Status** parameter sets the service to **Stopped** .</span></span>

### <span data-ttu-id="5521f-148">예 7: 원격 시스템에서 서비스 중지</span><span class="sxs-lookup"><span data-stu-id="5521f-148">Example 7: Stop a service on a remote system</span></span>

<span data-ttu-id="5521f-149">이 예제에서는 원격 컴퓨터에서 서비스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-149">This example stops a service on a remote computer.</span></span>
<span data-ttu-id="5521f-150">자세한 내용은 [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5521f-150">For more information, see [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```powershell
$Cred = Get-Credential
$S = Get-Service -Name Schedule
Invoke-Command -ComputerName server01.contoso.com -Credential $Cred -ScriptBlock {
  Set-Service -InputObject $S -Status Stopped
}
```

<span data-ttu-id="5521f-151">`Get-Credential` 사용자 이름 및 암호를 묻는 메시지를 표시 하 고 변수에 자격 증명을 저장 `$Cred` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-151">`Get-Credential` prompts for a username and password, and stores the credentials in the `$Cred` variable.</span></span> <span data-ttu-id="5521f-152">`Get-Service`**Name** 매개 변수를 사용 하 여 **일정** 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-152">`Get-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="5521f-153">개체는 변수에 저장 됩니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="5521f-153">The object is stored in the variable, `$S`.</span></span>

<span data-ttu-id="5521f-154">`Invoke-Command`**ComputerName** 매개 변수를 사용 하 여 원격 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-154">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer.</span></span> <span data-ttu-id="5521f-155">**Credential** 매개 변수는 변수를 사용 하 여 컴퓨터에 로그온 `$Cred` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-155">The **Credential** parameter uses the `$Cred` variable to sign on to the computer.</span></span> <span data-ttu-id="5521f-156">**ScriptBlock** 은를 호출 `Set-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-156">The **ScriptBlock** calls `Set-Service`.</span></span> <span data-ttu-id="5521f-157">**InputObject** 매개 변수는 저장 된 서비스 개체를 지정 합니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="5521f-157">The **InputObject** parameter specifies the service object stored `$S`.</span></span> <span data-ttu-id="5521f-158">**상태** 매개 변수는 서비스를 **중지 됨** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-158">The **Status** parameter sets the service to **Stopped** .</span></span>

### <span data-ttu-id="5521f-159">예 8: 서비스의 자격 증명 변경</span><span class="sxs-lookup"><span data-stu-id="5521f-159">Example 8: Change credential of a service</span></span>

<span data-ttu-id="5521f-160">이 예에서는 서비스를 관리 하는 데 사용 되는 자격 증명을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-160">This example changes the credentials that are used to manage a service.</span></span>

```powershell
$credential = Get-Credential
Set-Service -Name Schedule -Credential $credential
```

<span data-ttu-id="5521f-161">`Get-Credential` 사용자 이름 및 암호를 묻는 메시지를 표시 하 고 변수에 자격 증명을 저장 `$credential` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-161">`Get-Credential` prompts for a username and password, and stores the credentials in the `$credential` variable.</span></span> <span data-ttu-id="5521f-162">`Set-Service`**Name** 매개 변수를 사용 하 여 **일정** 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-162">`Set-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="5521f-163">**Credential** 매개 변수는 변수를 사용 하 `$credential` 고 **일정** 서비스를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-163">The **Credential** parameter uses the `$credential` variable and updates the **Schedule** service.</span></span>

### <span data-ttu-id="5521f-164">예 9: 서비스의 SecurityDescriptor 변경</span><span class="sxs-lookup"><span data-stu-id="5521f-164">Example 9: Change the SecurityDescriptor of a service</span></span>

<span data-ttu-id="5521f-165">이 예에서는 서비스의 **SecurityDescriptor** 를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-165">This example changes a service's **SecurityDescriptor** .</span></span>

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
Set-Service -Name "BITS" -SecurityDescriptorSddl $SDDL
```

<span data-ttu-id="5521f-166">**SecurityDescriptor** 은 변수에 저장 됩니다 `$SDDL` .</span><span class="sxs-lookup"><span data-stu-id="5521f-166">The **SecurityDescriptor** is stored in the `$SDDL` variable.</span></span> <span data-ttu-id="5521f-167">`Set-Service`**Name** 매개 변수를 사용 하 여 **BITS** 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-167">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="5521f-168">**SecurityDescriptorSddl** 매개 변수는 `$SDDL` 를 사용 하 여 **BITS** 서비스의 **SecurityDescriptor** 을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-168">The **SecurityDescriptorSddl** parameter uses `$SDDL` to change the **SecurityDescriptor** for the **BITS** service.</span></span>

## <span data-ttu-id="5521f-169">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5521f-169">PARAMETERS</span></span>

### <span data-ttu-id="5521f-170">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5521f-170">-Confirm</span></span>

<span data-ttu-id="5521f-171">실행 하기 전에 확인 메시지를 표시 `Set-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-171">Prompts you for confirmation before running `Set-Service`.</span></span>

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

### <span data-ttu-id="5521f-172">-Credential</span><span class="sxs-lookup"><span data-stu-id="5521f-172">-Credential</span></span>

<span data-ttu-id="5521f-173">서비스에서 [서비스 로그온 계정](/windows/desktop/ad/about-service-logon-accounts)으로 사용 하는 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-173">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="5521f-174">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="5521f-174">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="5521f-175">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-175">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="5521f-176">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-176">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="5521f-177">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="5521f-177">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

<span data-ttu-id="5521f-178">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-178">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="5521f-179">-Description</span><span class="sxs-lookup"><span data-stu-id="5521f-179">-Description</span></span>

<span data-ttu-id="5521f-180">서비스에 대한 새 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-180">Specifies a new description for the service.</span></span>

<span data-ttu-id="5521f-181">서비스 설명은 **컴퓨터 관리, 서비스** 에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-181">The service description appears in **Computer Management, Services** .</span></span> <span data-ttu-id="5521f-182">**설명은** `Get-Service` **ServiceController** 개체의 속성이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-182">The **Description** isn't a property of the `Get-Service` **ServiceController** object.</span></span> <span data-ttu-id="5521f-183">서비스 설명을 보려면 `Get-CimInstance` 서비스를 나타내는 **Win32_Service** 개체를 반환 하는를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-183">To see the service description, use `Get-CimInstance` that returns a **Win32_Service** object that represents the service.</span></span>

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

### <span data-ttu-id="5521f-184">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="5521f-184">-DisplayName</span></span>

<span data-ttu-id="5521f-185">서비스의 새 표시 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-185">Specifies a new display name for the service.</span></span>

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

### <span data-ttu-id="5521f-186">-Force</span><span class="sxs-lookup"><span data-stu-id="5521f-186">-Force</span></span>

<span data-ttu-id="5521f-187">서비스의 중지 모드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-187">Specifies the Stop mode of the service.</span></span> <span data-ttu-id="5521f-188">이 매개 변수는가 사용 되는 경우에만 작동 `-Status Stopped` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-188">This parameter only works when `-Status Stopped` is used.</span></span> <span data-ttu-id="5521f-189">사용 하도록 설정 하면 `Set-Service` 대상 서비스가 중지 되기 전에 종속 서비스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-189">If enabled, `Set-Service` stops the dependent services before the target service is stopped.</span></span> <span data-ttu-id="5521f-190">기본적으로 실행 중인 다른 서비스가 대상 서비스에 종속 되는 경우 예외가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-190">By default, exceptions are raised when other running services depend on the target service.</span></span>

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

### <span data-ttu-id="5521f-191">-InputObject</span><span class="sxs-lookup"><span data-stu-id="5521f-191">-InputObject</span></span>

<span data-ttu-id="5521f-192">변경할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-192">Specifies a **ServiceController** object that represents the service to change.</span></span> <span data-ttu-id="5521f-193">개체를 포함 하는 변수를 입력 하거나 개체를 가져오는 명령 또는 식 (예: 명령)을 입력 합니다 `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="5521f-193">Enter a variable that contains the object, or type a command or expression that gets the object, such as a `Get-Service` command.</span></span> <span data-ttu-id="5521f-194">파이프라인을 사용 하 여 서비스 개체를로 보낼 수 있습니다 `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="5521f-194">You can use the pipeline to send a service object to `Set-Service`.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5521f-195">-Name</span><span class="sxs-lookup"><span data-stu-id="5521f-195">-Name</span></span>

<span data-ttu-id="5521f-196">변경할 서비스의 서비스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-196">Specifies the service name of the service to be changed.</span></span> <span data-ttu-id="5521f-197">와일드 카드 문자는 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-197">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="5521f-198">파이프라인을 사용 하 여 서비스 이름을로 보낼 수 있습니다 `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="5521f-198">You can use the pipeline to send a service name to `Set-Service`.</span></span>

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

### <span data-ttu-id="5521f-199">-PassThru</span><span class="sxs-lookup"><span data-stu-id="5521f-199">-PassThru</span></span>

<span data-ttu-id="5521f-200">변경 된 서비스를 나타내는 **ServiceController** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-200">Returns a **ServiceController** object that represents the services that were changed.</span></span> <span data-ttu-id="5521f-201">기본적으로는 `Set-Service` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-201">By default, `Set-Service` doesn't generate any output.</span></span>

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

### <span data-ttu-id="5521f-202">-StartupType</span><span class="sxs-lookup"><span data-stu-id="5521f-202">-StartupType</span></span>

<span data-ttu-id="5521f-203">서비스의 시작 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-203">Specifies the start mode of the service.</span></span>

<span data-ttu-id="5521f-204">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-204">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="5521f-205">**자동** -시스템이 시작 되거나 운영 체제에서 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-205">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="5521f-206">자동으로 시작된 서비스가 수동으로 시작된 서비스에 따라 달라지는 경우, 시스템 시작 시 수동으로 시작된 서비스도 자동으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-206">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="5521f-207">자동 **Delayedstart** -시스템이 부팅 된 후 바로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-207">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="5521f-208">**사용 안 함** -서비스를 사용할 수 없으며 사용자 또는 응용 프로그램에서 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-208">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="5521f-209">**Invalidvalue** -적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-209">**InvalidValue** - Has no effect.</span></span> <span data-ttu-id="5521f-210">이 cmdlet은 오류를 반환 하지 않지만 서비스의 StartupType은 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-210">The cmdlet does not return an error but the StartupType of the service is not changed.</span></span>
- <span data-ttu-id="5521f-211">**수동** -서비스 제어 관리자 또는 응용 프로그램을 사용 하 여 수동으로 또는 사용자가 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-211">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases: StartMode, SM, ST, StartType
Accepted values: Automatic, AutomaticDelayedStart, Disabled, InvalidValue, Manual

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5521f-212">-상태</span><span class="sxs-lookup"><span data-stu-id="5521f-212">-Status</span></span>

<span data-ttu-id="5521f-213">서비스의 상태를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-213">Specifies the status for the service.</span></span>

<span data-ttu-id="5521f-214">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-214">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="5521f-215">**일시 중지 됨** .</span><span class="sxs-lookup"><span data-stu-id="5521f-215">**Paused** .</span></span> <span data-ttu-id="5521f-216">서비스를 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-216">Suspends the service.</span></span>
- <span data-ttu-id="5521f-217">**실행 중** .</span><span class="sxs-lookup"><span data-stu-id="5521f-217">**Running** .</span></span> <span data-ttu-id="5521f-218">서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-218">Starts the service.</span></span>
- <span data-ttu-id="5521f-219">**중지 됨** .</span><span class="sxs-lookup"><span data-stu-id="5521f-219">**Stopped** .</span></span> <span data-ttu-id="5521f-220">서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-220">Stops the service.</span></span>

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

### <span data-ttu-id="5521f-221">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="5521f-221">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="5521f-222">**Sddl** 형식으로 서비스에 대 한 **SecurityDescriptor** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-222">Specifies the **SecurityDescriptor** for the service in **Sddl** format.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sd

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5521f-223">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5521f-223">-WhatIf</span></span>

<span data-ttu-id="5521f-224">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="5521f-224">Shows what would happen if `Set-Service` runs.</span></span> <span data-ttu-id="5521f-225">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-225">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="5521f-226">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5521f-226">CommonParameters</span></span>

<span data-ttu-id="5521f-227">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5521f-227">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5521f-228">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5521f-228">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5521f-229">입력</span><span class="sxs-lookup"><span data-stu-id="5521f-229">INPUTS</span></span>

### <span data-ttu-id="5521f-230">ServiceController, System.string입니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-230">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="5521f-231">파이프라인을 사용 하 여 서비스 개체 또는 서비스 이름이 포함 된 문자열을로 보낼 수 있습니다 `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="5521f-231">You can use the pipeline to send a service object or a string that contains a service name to `Set-Service`.</span></span>

## <span data-ttu-id="5521f-232">출력</span><span class="sxs-lookup"><span data-stu-id="5521f-232">OUTPUTS</span></span>

### <span data-ttu-id="5521f-233">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="5521f-233">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="5521f-234">기본적으로는 `Set-Service` 개체를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-234">By default, `Set-Service` doesn't return any objects.</span></span> <span data-ttu-id="5521f-235">**PassThru** 매개 변수를 사용 하 여 **ServiceController** 개체를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-235">Use the **PassThru** parameter to output a **ServiceController** object.</span></span>

## <span data-ttu-id="5521f-236">참고</span><span class="sxs-lookup"><span data-stu-id="5521f-236">NOTES</span></span>

<span data-ttu-id="5521f-237">`Set-Service` 높은 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-237">`Set-Service` requires elevated permissions.</span></span> <span data-ttu-id="5521f-238">**관리자 권한으로 실행** 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-238">Use the **Run as administrator** option.</span></span>

<span data-ttu-id="5521f-239">`Set-Service` 현재 사용자에 게 서비스를 관리할 수 있는 권한이 있는 경우에만 서비스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-239">`Set-Service` can only control services when the current user has permissions to manage services.</span></span> <span data-ttu-id="5521f-240">명령이 제대로 작동 하지 않는 경우 필요한 권한이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-240">If a command doesn't work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="5521f-241">서비스의 서비스 이름 또는 표시 이름을 찾으려면를 사용 `Get-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-241">To find a service's service name or display name, use `Get-Service`.</span></span> <span data-ttu-id="5521f-242">서비스 이름은 **Name** 열에 있고 표시 이름은 **DisplayName** 열에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5521f-242">The service names are in the **Name** column and the display names are in the **DisplayName** column.</span></span>

## <span data-ttu-id="5521f-243">관련 링크</span><span class="sxs-lookup"><span data-stu-id="5521f-243">RELATED LINKS</span></span>

[<span data-ttu-id="5521f-244">Get-Service</span><span class="sxs-lookup"><span data-stu-id="5521f-244">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="5521f-245">New-Service</span><span class="sxs-lookup"><span data-stu-id="5521f-245">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="5521f-246">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="5521f-246">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="5521f-247">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="5521f-247">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="5521f-248">Start-Service</span><span class="sxs-lookup"><span data-stu-id="5521f-248">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="5521f-249">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="5521f-249">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="5521f-250">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="5521f-250">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="5521f-251">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="5521f-251">Remove-Service</span></span>](Remove-Service.md)
