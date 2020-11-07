---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: 81920303d130a306674033b2b1ba57a3e71c949c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347434"
---
# <span data-ttu-id="8419c-103">New-Service</span><span class="sxs-lookup"><span data-stu-id="8419c-103">New-Service</span></span>

## <span data-ttu-id="8419c-104">개요</span><span class="sxs-lookup"><span data-stu-id="8419c-104">SYNOPSIS</span></span>
<span data-ttu-id="8419c-105">새 Windows 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-105">Creates a new Windows service.</span></span>

## <span data-ttu-id="8419c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8419c-106">SYNTAX</span></span>

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-SecurityDescriptorSddl <String>] [-StartupType <ServiceStartupType>] [-Credential <PSCredential>]
 [-DependsOn <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8419c-107">설명</span><span class="sxs-lookup"><span data-stu-id="8419c-107">DESCRIPTION</span></span>

<span data-ttu-id="8419c-108">`New-Service`Cmdlet은 레지스트리 및 서비스 데이터베이스에 Windows 서비스에 대 한 새 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-108">The `New-Service` cmdlet creates a new entry for a Windows service in the registry and in the service database.</span></span> <span data-ttu-id="8419c-109">새 서비스에는 서비스 중 실행 되는 실행 파일이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-109">A new service requires an executable file that runs during the service.</span></span>

<span data-ttu-id="8419c-110">이 cmdlet의 매개 변수를 사용하면 서비스의 표시 이름, 설명, 시작 유형 및 종속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-110">The parameters of this cmdlet let you set the display name, description, startup type, and dependencies of the service.</span></span>

## <span data-ttu-id="8419c-111">예제</span><span class="sxs-lookup"><span data-stu-id="8419c-111">EXAMPLES</span></span>

### <span data-ttu-id="8419c-112">예제 1: 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="8419c-112">Example 1: Create a service</span></span>

```powershell
New-Service -Name "TestService" -BinaryPathName "C:\WINDOWS\System32\svchost.exe -k netsvcs"
```

<span data-ttu-id="8419c-113">이 명령은 TestService 라는 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-113">This command creates a service named TestService.</span></span>

### <span data-ttu-id="8419c-114">예제 2: 설명, 시작 유형 및 표시 이름을 포함 하는 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="8419c-114">Example 2: Create a service that includes description, startup type, and display name</span></span>

```powershell
$params = @{
  Name = "TestService"
  BinaryPathName = "C:\WINDOWS\System32\svchost.exe -k netsvcs"
  DependsOn = "NetLogon"
  DisplayName = "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
}
New-Service @params
```

<span data-ttu-id="8419c-115">이 명령은 TestService 라는 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-115">This command creates a service named TestService.</span></span> <span data-ttu-id="8419c-116">의 매개 변수를 사용 하 여 `New-Service` 새 서비스의 설명, 시작 유형 및 표시 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-116">It uses the parameters of `New-Service` to specify a description, startup type, and display name for the new service.</span></span>

### <span data-ttu-id="8419c-117">예 3: 새 서비스 보기</span><span class="sxs-lookup"><span data-stu-id="8419c-117">Example 3: View the new service</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -Filter "Name='testservice'"
```

```Output
ExitCode  : 0
Name      : testservice
ProcessId : 0
StartMode : Auto
State     : Stopped
Status    : OK
```

<span data-ttu-id="8419c-118">이 명령은 `Get-CimInstance` 를 사용 하 여 새 서비스에 대 한 **Win32_Service** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-118">This command uses `Get-CimInstance` to get the **Win32_Service** object for the new service.</span></span> <span data-ttu-id="8419c-119">이 개체에는 시작 모드와 서비스 설명이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-119">This object includes the start mode and the service description.</span></span>

### <span data-ttu-id="8419c-120">예제 4: 만들 때 서비스의 SecurityDescriptor 설정</span><span class="sxs-lookup"><span data-stu-id="8419c-120">Example 4: Set the SecurityDescriptor of a service when creating.</span></span>

<span data-ttu-id="8419c-121">이 예에서는 생성 되는 서비스의 **SecurityDescriptor** 를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-121">This example adds the **SecurityDescriptor** of the service being created.</span></span>

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
$params = @{
  BinaryPathName = "C:\WINDOWS\System32\svchost.exe -k netsvcs"
  DependsOn = "NetLogon"
  DisplayName "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
  SecurityDescriptorSddl = $SDDL
}
New-Service @params
```

<span data-ttu-id="8419c-122">**SecurityDescriptor** 은 변수에 저장 됩니다 `$SDDLToSet` .</span><span class="sxs-lookup"><span data-stu-id="8419c-122">The **SecurityDescriptor** is stored in the `$SDDLToSet` variable.</span></span> <span data-ttu-id="8419c-123">**SecurityDescriptorSddl** 매개 변수는 `$SDDL` 를 사용 하 여 새 서비스의 **SecurityDescriptor** 을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-123">The **SecurityDescriptorSddl** parameter uses `$SDDL` to set the **SecurityDescriptor** of the new service.</span></span>

## <span data-ttu-id="8419c-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8419c-124">PARAMETERS</span></span>

### <span data-ttu-id="8419c-125">-BinaryPathName</span><span class="sxs-lookup"><span data-stu-id="8419c-125">-BinaryPathName</span></span>

<span data-ttu-id="8419c-126">서비스의 실행 파일 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-126">Specifies the path of the executable file for the service.</span></span> <span data-ttu-id="8419c-127">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-127">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8419c-128">-Credential</span><span class="sxs-lookup"><span data-stu-id="8419c-128">-Credential</span></span>

<span data-ttu-id="8419c-129">서비스에서 [서비스 로그온 계정](/windows/desktop/ad/about-service-logon-accounts)으로 사용 하는 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-129">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="8419c-130">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="8419c-130">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="8419c-131">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-131">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="8419c-132">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-132">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="8419c-133">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="8419c-133">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="8419c-134">-DependsOn</span><span class="sxs-lookup"><span data-stu-id="8419c-134">-DependsOn</span></span>

<span data-ttu-id="8419c-135">새 서비스가 종속되는 다른 서비스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-135">Specifies the names of other services upon which the new service depends.</span></span> <span data-ttu-id="8419c-136">여러 서비스 이름을 입력하려면 쉼표를 사용하여 이름을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-136">To enter multiple service names, use a comma to separate the names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8419c-137">-Description</span><span class="sxs-lookup"><span data-stu-id="8419c-137">-Description</span></span>

<span data-ttu-id="8419c-138">서비스에 대한 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-138">Specifies a description of the service.</span></span>

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

### <span data-ttu-id="8419c-139">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="8419c-139">-DisplayName</span></span>

<span data-ttu-id="8419c-140">서비스의 표시 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-140">Specifies a display name for the service.</span></span>

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

### <span data-ttu-id="8419c-141">-Name</span><span class="sxs-lookup"><span data-stu-id="8419c-141">-Name</span></span>

<span data-ttu-id="8419c-142">서비스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-142">Specifies the name of the service.</span></span> <span data-ttu-id="8419c-143">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-143">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8419c-144">-StartupType</span><span class="sxs-lookup"><span data-stu-id="8419c-144">-StartupType</span></span>

<span data-ttu-id="8419c-145">서비스의 시작 유형을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-145">Sets the startup type of the service.</span></span> <span data-ttu-id="8419c-146">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8419c-147">**자동** -시스템이 시작 되거나 운영 체제에서 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-147">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="8419c-148">자동으로 시작된 서비스가 수동으로 시작된 서비스에 따라 달라지는 경우, 시스템 시작 시 수동으로 시작된 서비스도 자동으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-148">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="8419c-149">자동 **Delayedstart** -시스템이 부팅 된 후 바로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-149">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="8419c-150">**사용 안 함** -서비스를 사용할 수 없으며 사용자 또는 응용 프로그램에서 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-150">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="8419c-151">**Invalidvalue** -이 값은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-151">**InvalidValue** - This value is not supported.</span></span> <span data-ttu-id="8419c-152">이 값을 사용 하면 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-152">Using this value results in an error.</span></span>
- <span data-ttu-id="8419c-153">**수동** -서비스 제어 관리자 또는 응용 프로그램을 사용 하 여 수동으로 또는 사용자가 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-153">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

 <span data-ttu-id="8419c-154">기본값은 **Automatic** 입니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-154">The default value is **Automatic**.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases:
Accepted values: Automatic, Manual, Disabled, AutomaticDelayedStart, InvalidValue

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8419c-155">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="8419c-155">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="8419c-156">**Sddl** 형식으로 서비스에 대 한 **SecurityDescriptor** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-156">Specifies the **SecurityDescriptor** for the service in **Sddl** format.</span></span>

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

### <span data-ttu-id="8419c-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8419c-157">-Confirm</span></span>

<span data-ttu-id="8419c-158">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8419c-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8419c-159">-WhatIf</span></span>

<span data-ttu-id="8419c-160">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-160">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="8419c-161">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8419c-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8419c-162">CommonParameters</span></span>

<span data-ttu-id="8419c-163">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8419c-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8419c-164">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8419c-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8419c-165">입력</span><span class="sxs-lookup"><span data-stu-id="8419c-165">INPUTS</span></span>

### <span data-ttu-id="8419c-166">없음</span><span class="sxs-lookup"><span data-stu-id="8419c-166">None</span></span>

<span data-ttu-id="8419c-167">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-167">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="8419c-168">출력</span><span class="sxs-lookup"><span data-stu-id="8419c-168">OUTPUTS</span></span>

### <span data-ttu-id="8419c-169">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="8419c-169">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="8419c-170">이 cmdlet은 새 서비스를 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-170">This cmdlet returns an object that represents the new service.</span></span>

## <span data-ttu-id="8419c-171">참고</span><span class="sxs-lookup"><span data-stu-id="8419c-171">NOTES</span></span>

<span data-ttu-id="8419c-172">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-172">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="8419c-173">이 cmdlet을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8419c-173">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="8419c-174">관련 링크</span><span class="sxs-lookup"><span data-stu-id="8419c-174">RELATED LINKS</span></span>

[<span data-ttu-id="8419c-175">Get-Service</span><span class="sxs-lookup"><span data-stu-id="8419c-175">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="8419c-176">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="8419c-176">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="8419c-177">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="8419c-177">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="8419c-178">Set-Service</span><span class="sxs-lookup"><span data-stu-id="8419c-178">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="8419c-179">Start-Service</span><span class="sxs-lookup"><span data-stu-id="8419c-179">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="8419c-180">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="8419c-180">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="8419c-181">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="8419c-181">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="8419c-182">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="8419c-182">Remove-Service</span></span>](Remove-Service.md)
