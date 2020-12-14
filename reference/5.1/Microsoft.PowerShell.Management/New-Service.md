---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: 758b0a8ef9a5f65f0e7cfa7f3633086cf9f0445d
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891771"
---
# <span data-ttu-id="1a426-103">New-Service</span><span class="sxs-lookup"><span data-stu-id="1a426-103">New-Service</span></span>

## <span data-ttu-id="1a426-104">개요</span><span class="sxs-lookup"><span data-stu-id="1a426-104">SYNOPSIS</span></span>
<span data-ttu-id="1a426-105">새 Windows 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-105">Creates a new Windows service.</span></span>

## <span data-ttu-id="1a426-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1a426-106">SYNTAX</span></span>

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Credential <PSCredential>] [-DependsOn <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1a426-107">설명</span><span class="sxs-lookup"><span data-stu-id="1a426-107">DESCRIPTION</span></span>

<span data-ttu-id="1a426-108">`New-Service`Cmdlet은 레지스트리 및 서비스 데이터베이스에 Windows 서비스에 대 한 새 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-108">The `New-Service` cmdlet creates a new entry for a Windows service in the registry and in the service database.</span></span> <span data-ttu-id="1a426-109">새 서비스에는 서비스 중 실행 되는 실행 파일이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-109">A new service requires an executable file that runs during the service.</span></span>

<span data-ttu-id="1a426-110">이 cmdlet의 매개 변수를 사용하면 서비스의 표시 이름, 설명, 시작 유형 및 종속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-110">The parameters of this cmdlet let you set the display name, description, startup type, and dependencies of the service.</span></span>

## <span data-ttu-id="1a426-111">예제</span><span class="sxs-lookup"><span data-stu-id="1a426-111">EXAMPLES</span></span>

### <span data-ttu-id="1a426-112">예제 1: 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="1a426-112">Example 1: Create a service</span></span>

```powershell
New-Service -Name "TestService" -BinaryPathName '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
```

<span data-ttu-id="1a426-113">이 명령은 TestService 라는 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-113">This command creates a service named TestService.</span></span>

### <span data-ttu-id="1a426-114">예제 2: 설명, 시작 유형 및 표시 이름을 포함 하는 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="1a426-114">Example 2: Create a service that includes description, startup type, and display name</span></span>

```powershell
$params = @{
  Name = "TestService"
  BinaryPathName = '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
  DependsOn = "NetLogon"
  DisplayName = "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
}
New-Service @params
```

<span data-ttu-id="1a426-115">이 명령은 TestService 라는 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-115">This command creates a service named TestService.</span></span> <span data-ttu-id="1a426-116">의 매개 변수를 사용 하 여 `New-Service` 새 서비스의 설명, 시작 유형 및 표시 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-116">It uses the parameters of `New-Service` to specify a description, startup type, and display name for the new service.</span></span>

### <span data-ttu-id="1a426-117">예 3: 새 서비스 보기</span><span class="sxs-lookup"><span data-stu-id="1a426-117">Example 3: View the new service</span></span>

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

<span data-ttu-id="1a426-118">이 명령은 `Get-CimInstance` 를 사용 하 여 새 서비스에 대 한 **Win32_Service** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-118">This command uses `Get-CimInstance` to get the **Win32_Service** object for the new service.</span></span> <span data-ttu-id="1a426-119">이 개체에는 시작 모드와 서비스 설명이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-119">This object includes the start mode and the service description.</span></span>

### <span data-ttu-id="1a426-120">예제 4: 서비스 삭제</span><span class="sxs-lookup"><span data-stu-id="1a426-120">Example 4: Delete a service</span></span>

```powershell
sc.exe delete TestService
# - or -
(Get-CimInstance -Class Win32_Service -Filter "name='TestService'").delete()
```

<span data-ttu-id="1a426-121">이 예제에서는 TestService 서비스를 삭제할 수 있는 두 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-121">This example shows two ways to delete the TestService service.</span></span> <span data-ttu-id="1a426-122">첫 번째 명령은의 delete 옵션을 사용 합니다 `Sc.exe` .</span><span class="sxs-lookup"><span data-stu-id="1a426-122">The first command uses the delete option of `Sc.exe`.</span></span> <span data-ttu-id="1a426-123">두 번째 명령은에서 반환 하는 **Win32_Service** 개체의 **Delete** 메서드를 사용 합니다 `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="1a426-123">The second command uses the **Delete** method of the **Win32_Service** objects that `Get-CimInstance` returns.</span></span>

## <span data-ttu-id="1a426-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1a426-124">PARAMETERS</span></span>

### <span data-ttu-id="1a426-125">-BinaryPathName</span><span class="sxs-lookup"><span data-stu-id="1a426-125">-BinaryPathName</span></span>

<span data-ttu-id="1a426-126">서비스의 실행 파일 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-126">Specifies the path of the executable file for the service.</span></span> <span data-ttu-id="1a426-127">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-127">This parameter is required.</span></span>

<span data-ttu-id="1a426-128">서비스 이진 파일의 정규화 된 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-128">The fully qualified path to the service binary file.</span></span> <span data-ttu-id="1a426-129">경로에 공백이 있는 경우 올바르게 해석 되도록 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-129">If the path contains a space, it must be quoted so that it is correctly interpreted.</span></span> <span data-ttu-id="1a426-130">예를 들어는 `d:\my share\myservice.exe` 로 지정 해야 합니다 `'"d:\my share\myservice.exe"'` .</span><span class="sxs-lookup"><span data-stu-id="1a426-130">For example, `d:\my share\myservice.exe` should be specified as `'"d:\my share\myservice.exe"'`.</span></span>

<span data-ttu-id="1a426-131">경로에는 자동 시작 서비스의 인수도 포함 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-131">The path can also include arguments for an auto-start service.</span></span> <span data-ttu-id="1a426-132">예: `'"d:\myshare\myservice.exe arg1 arg2"'`.</span><span class="sxs-lookup"><span data-stu-id="1a426-132">For example, `'"d:\myshare\myservice.exe arg1 arg2"'`.</span></span> <span data-ttu-id="1a426-133">이러한 인수는 서비스 진입점에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-133">These arguments are passed to the service entry point.</span></span>

<span data-ttu-id="1a426-134">자세한 내용은 [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) API의 **lpBinaryPathName** 매개 변수를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1a426-134">For more information, see the **lpBinaryPathName** parameter of [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) API.</span></span>

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

### <span data-ttu-id="1a426-135">-Credential</span><span class="sxs-lookup"><span data-stu-id="1a426-135">-Credential</span></span>

<span data-ttu-id="1a426-136">서비스에서 [서비스 로그온 계정](/windows/desktop/ad/about-service-logon-accounts)으로 사용 하는 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-136">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="1a426-137">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="1a426-137">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="1a426-138">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-138">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="1a426-139">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-139">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="1a426-140">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="1a426-140">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="1a426-141">-DependsOn</span><span class="sxs-lookup"><span data-stu-id="1a426-141">-DependsOn</span></span>

<span data-ttu-id="1a426-142">새 서비스가 종속되는 다른 서비스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-142">Specifies the names of other services upon which the new service depends.</span></span> <span data-ttu-id="1a426-143">여러 서비스 이름을 입력하려면 쉼표를 사용하여 이름을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-143">To enter multiple service names, use a comma to separate the names.</span></span>

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

### <span data-ttu-id="1a426-144">-Description</span><span class="sxs-lookup"><span data-stu-id="1a426-144">-Description</span></span>

<span data-ttu-id="1a426-145">서비스에 대한 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-145">Specifies a description of the service.</span></span>

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

### <span data-ttu-id="1a426-146">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="1a426-146">-DisplayName</span></span>

<span data-ttu-id="1a426-147">서비스의 표시 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-147">Specifies a display name for the service.</span></span>

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

### <span data-ttu-id="1a426-148">-Name</span><span class="sxs-lookup"><span data-stu-id="1a426-148">-Name</span></span>

<span data-ttu-id="1a426-149">서비스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-149">Specifies the name of the service.</span></span> <span data-ttu-id="1a426-150">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-150">This parameter is required.</span></span>

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

### <span data-ttu-id="1a426-151">-StartupType</span><span class="sxs-lookup"><span data-stu-id="1a426-151">-StartupType</span></span>

<span data-ttu-id="1a426-152">서비스의 시작 유형을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-152">Sets the startup type of the service.</span></span> <span data-ttu-id="1a426-153">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-153">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1a426-154">**자동** -시스템이 시작 되거나 운영 체제에서 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-154">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="1a426-155">자동으로 시작된 서비스가 수동으로 시작된 서비스에 따라 달라지는 경우, 시스템 시작 시 수동으로 시작된 서비스도 자동으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-155">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="1a426-156">**사용 안 함** -서비스를 사용할 수 없으며 사용자 또는 응용 프로그램에서 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-156">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="1a426-157">**수동** -서비스 제어 관리자 또는 응용 프로그램을 사용 하 여 수동으로 또는 사용자가 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-157">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>
- <span data-ttu-id="1a426-158">**Boot** -서비스가 시스템 로더에서 시작한 장치 드라이버 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-158">**Boot** - Indicates that the service is a device driver started by the system loader.</span></span> <span data-ttu-id="1a426-159">이 값은 디바이스 드라이버에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-159">This value is valid only for device drivers.</span></span>
- <span data-ttu-id="1a426-160">**시스템** -서비스가 ' IOInitSystem () ' 함수에서 시작한 장치 드라이버 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-160">**System** - Indicates that the service is a device driver started by the 'IOInitSystem()' function.</span></span> <span data-ttu-id="1a426-161">이 값은 디바이스 드라이버에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-161">This value is valid only for device drivers.</span></span>

 <span data-ttu-id="1a426-162">기본값은 **Automatic** 입니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-162">The default value is **Automatic**.</span></span>

```yaml
Type: System.ServiceProcess.ServiceStartMode
Parameter Sets: (All)
Aliases:
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a426-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1a426-163">-Confirm</span></span>

<span data-ttu-id="1a426-164">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1a426-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1a426-165">-WhatIf</span></span>

<span data-ttu-id="1a426-166">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-166">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1a426-167">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1a426-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1a426-168">CommonParameters</span></span>

<span data-ttu-id="1a426-169">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1a426-169">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1a426-170">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a426-170">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1a426-171">입력</span><span class="sxs-lookup"><span data-stu-id="1a426-171">INPUTS</span></span>

### <span data-ttu-id="1a426-172">없음</span><span class="sxs-lookup"><span data-stu-id="1a426-172">None</span></span>

<span data-ttu-id="1a426-173">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-173">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="1a426-174">출력</span><span class="sxs-lookup"><span data-stu-id="1a426-174">OUTPUTS</span></span>

### <span data-ttu-id="1a426-175">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="1a426-175">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="1a426-176">이 cmdlet은 새 서비스를 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-176">This cmdlet returns an object that represents the new service.</span></span>

## <span data-ttu-id="1a426-177">참고</span><span class="sxs-lookup"><span data-stu-id="1a426-177">NOTES</span></span>

<span data-ttu-id="1a426-178">이 cmdlet을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-178">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

<span data-ttu-id="1a426-179">서비스를 삭제 하려면 Sc.exe를 사용 하거나 cmdlet을 사용 `Get-CimInstance` 하 여 서비스를 나타내는 **Win32_Service** 개체를 가져온 다음 **delete** 메서드를 사용 하 여 서비스를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-179">To delete a service, use Sc.exe, or use the `Get-CimInstance` cmdlet to get the **Win32_Service** object that represents the service and then use the **Delete** method to delete the service.</span></span> <span data-ttu-id="1a426-180">을 반환 하는 개체에는 `Get-Service` 삭제 메서드가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1a426-180">The object that `Get-Service` returns does not have a delete method.</span></span>

## <span data-ttu-id="1a426-181">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1a426-181">RELATED LINKS</span></span>

[<span data-ttu-id="1a426-182">Get-Service</span><span class="sxs-lookup"><span data-stu-id="1a426-182">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="1a426-183">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="1a426-183">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="1a426-184">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="1a426-184">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="1a426-185">Set-Service</span><span class="sxs-lookup"><span data-stu-id="1a426-185">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="1a426-186">Start-Service</span><span class="sxs-lookup"><span data-stu-id="1a426-186">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="1a426-187">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="1a426-187">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="1a426-188">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="1a426-188">Suspend-Service</span></span>](Suspend-Service.md)
