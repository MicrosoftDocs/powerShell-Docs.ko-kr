---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WmiObject
ms.openlocfilehash: ed759ff3d0dd35cd55f9dac5a2d76e36eac4dc6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215393"
---
# <span data-ttu-id="8294f-103">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="8294f-103">Get-WmiObject</span></span>

## <span data-ttu-id="8294f-104">개요</span><span class="sxs-lookup"><span data-stu-id="8294f-104">SYNOPSIS</span></span>
<span data-ttu-id="8294f-105">WMI(Windows Management Instrumentation) 클래스 인스턴스 또는 사용 가능한 클래스에 대한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-105">Gets instances of Windows Management Instrumentation (WMI) classes or information about the available classes.</span></span>

## <span data-ttu-id="8294f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8294f-106">SYNTAX</span></span>

### <span data-ttu-id="8294f-107">쿼리 (기본값)</span><span class="sxs-lookup"><span data-stu-id="8294f-107">query (Default)</span></span>

```
Get-WmiObject [-Class] <String> [[-Property] <String[]>] [-Filter <String>] [-Amended] [-DirectRead]
 [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="8294f-108">list</span><span class="sxs-lookup"><span data-stu-id="8294f-108">list</span></span>

```
Get-WmiObject [[-Class] <String>] [-Recurse] [-Amended] [-List] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="8294f-109">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="8294f-109">WQLQuery</span></span>

```
Get-WmiObject [-Amended] [-DirectRead] -Query <String> [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="8294f-110">class</span><span class="sxs-lookup"><span data-stu-id="8294f-110">class</span></span>

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="8294f-111">path</span><span class="sxs-lookup"><span data-stu-id="8294f-111">path</span></span>

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

## <span data-ttu-id="8294f-112">설명</span><span class="sxs-lookup"><span data-stu-id="8294f-112">DESCRIPTION</span></span>

<span data-ttu-id="8294f-113">PowerShell 3.0부터이 cmdlet은로 대체 되었습니다 `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="8294f-113">Starting in PowerShell 3.0, this cmdlet has been superseded by `Get-CimInstance`.</span></span>

<span data-ttu-id="8294f-114">`Get-WmiObject`Cmdlet은 wmi 클래스의 인스턴스 또는 사용 가능한 wmi 클래스에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-114">The `Get-WmiObject` cmdlet gets instances of WMI classes or information about the available WMI classes.</span></span> <span data-ttu-id="8294f-115">원격 컴퓨터를 지정하려면 **ComputerName** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-115">To specify a remote computer, use the **ComputerName** parameter.</span></span> <span data-ttu-id="8294f-116">**List** 매개 변수를 지정하면 cmdlet에서 지정된 네임 스페이스에서 사용할 수 있는 WMI 클래스에 대한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-116">If the **List** parameter is specified, the cmdlet gets information about the WMI classes that are available in a specified namespace.</span></span> <span data-ttu-id="8294f-117">**Query** 매개 변수를 지정한 경우 cmdlet이 WQL(WMI Query Language) 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-117">If the **Query** parameter is specified, the cmdlet runs a WMI query language (WQL) statement.</span></span>

<span data-ttu-id="8294f-118">`Get-WmiObject`이 cmdlet은 원격 작업을 수행 하는 데 Windows PowerShell 원격을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-118">The `Get-WmiObject` cmdlet does not use Windows PowerShell remoting to perform remote operations.</span></span>
<span data-ttu-id="8294f-119">**ComputerName** `Get-WmiObject` 컴퓨터가 windows powershell 원격에 대 한 요구 사항을 충족 하지 않거나 windows powershell에서 원격 기능에 대해 구성 되지 않은 경우에도 cmdlet의 ComputerName 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-119">You can use the **ComputerName** parameter of the `Get-WmiObject` cmdlet even if your computer does not meet the requirements for Windows PowerShell remoting or is not configured for remoting in Windows PowerShell.</span></span>

<span data-ttu-id="8294f-120">Windows PowerShell 3.0부터을 반환 하는 개체의 **__Server** 속성에는 `Get-WmiObject` **PSComputerName** 별칭이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-120">Beginning in Windows PowerShell 3.0, the **__Server** property of the object that `Get-WmiObject` returns has a **PSComputerName** alias.</span></span> <span data-ttu-id="8294f-121">따라서 출력 및 보고서에 원본 컴퓨터 이름을 더 쉽게 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-121">This makes it easier to include the source computer name in output and reports.</span></span>

## <span data-ttu-id="8294f-122">예제</span><span class="sxs-lookup"><span data-stu-id="8294f-122">EXAMPLES</span></span>

### <span data-ttu-id="8294f-123">예 1: 로컬 컴퓨터에서 프로세스 가져오기</span><span class="sxs-lookup"><span data-stu-id="8294f-123">Example 1: Get processes on the local computer</span></span>

<span data-ttu-id="8294f-124">이 예제에서는 로컬 컴퓨터의 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-124">This example get the processes on the local computer.</span></span>

```powershell
Get-WmiObject -Class Win32_Process
```

### <span data-ttu-id="8294f-125">예 2: 원격 컴퓨터의 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-125">Example 2: Gets services on a remote computer</span></span>

<span data-ttu-id="8294f-126">이 예제에서는 원격 컴퓨터의 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-126">This example gets the services on a remote computer.</span></span> <span data-ttu-id="8294f-127">**ComputerName** 매개 변수는 원격 컴퓨터의 IP 주소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-127">The **ComputerName** parameter specifies the IP address of a remote computer.</span></span> <span data-ttu-id="8294f-128">기본적으로 현재 사용자 계정은 원격 컴퓨터에서 **Administrators** 그룹의 구성원 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-128">By default, the current user account must be a member of the **Administrators** group on the remote computer.</span></span>

```powershell
Get-WmiObject -Class Win32_Service -ComputerName 10.1.4.62
```

### <span data-ttu-id="8294f-129">예제 3: 로컬 컴퓨터의 루트 또는 기본 네임 스페이스에 WMI 클래스 가져오기</span><span class="sxs-lookup"><span data-stu-id="8294f-129">Example 3: Get WMI classes in the root or default namespace of the local computer</span></span>

<span data-ttu-id="8294f-130">이 예제에서는 로컬 컴퓨터의 루트 또는 기본 네임 스페이스에 있는 WMI 클래스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-130">This example gets the WMI classes in the root or default namespace of the local computer.</span></span>

```powershell
Get-WmiObject -Namespace "root/default" -List
```

### <span data-ttu-id="8294f-131">예제 4: 여러 컴퓨터에 명명 된 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="8294f-131">Example 4: Get a named service on multiple computers</span></span>

<span data-ttu-id="8294f-132">이 예제에서는 **ComputerName** 매개 변수 값으로 지정 된 컴퓨터의 WinRM 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-132">This example gets the WinRM service on the computers specified by the value of the **ComputerName** parameter.</span></span>

```powershell
Get-WmiObject -Query "select * from win32_service where name='WinRM'" -ComputerName Server01, Server02 |
  Format-List -Property PSComputerName, Name, ExitCode, Name, ProcessID, StartMode, State, Status
```

```Output
PSComputerName : SERVER01
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 844
StartMode      : Auto
State          : Running
Status         : OK

PSComputerName : SERVER02
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 932
StartMode      : Auto
State          : Running
Status         : OK
```

<span data-ttu-id="8294f-133">파이프라인 연산자 (|)가 출력을 cmdlet으로 전송 합니다 `Format-List` . 그러면이 cmdlet이 **PSComputerName** 속성을 기본 출력에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-133">A pipeline operator (|) sends the output to the `Format-List` cmdlet, which adds the **PSComputerName** property to the default output.</span></span> <span data-ttu-id="8294f-134">**PSComputerName** 는을 반환 하는 개체의 **__Server** 속성에 대 한 별칭입니다 `Get-WmiObject` .</span><span class="sxs-lookup"><span data-stu-id="8294f-134">**PSComputerName** is an alias of the **__Server** property of the objects that `Get-WmiObject` returns.</span></span> <span data-ttu-id="8294f-135">이 별칭은 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-135">This alias was introduced in PowerShell 3.0.</span></span>

### <span data-ttu-id="8294f-136">예 5: 원격 컴퓨터에서 서비스 중지</span><span class="sxs-lookup"><span data-stu-id="8294f-136">Example 5: Stop a service on a remote computer</span></span>

<span data-ttu-id="8294f-137">이 예제에서는 원격 컴퓨터의 WinRM 서비스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-137">This example stops the WinRM service on a remote computer.</span></span> <span data-ttu-id="8294f-138">`Get-WmiObject` Server01에 있는 WinRM 서비스 개체의 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-138">`Get-WmiObject` gets the instance of the WinRM service object on Server01.</span></span> <span data-ttu-id="8294f-139">그런 다음 해당 개체에 **Win32_Service** WMI 클래스의 **StopService** 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-139">Then, it invokes the **StopService** method of the **Win32_Service** WMI class on that object.</span></span>

```powershell
(Get-WmiObject -Class Win32_Service -Filter "name='WinRM'" -ComputerName Server01).StopService()
```

<span data-ttu-id="8294f-140">Cmdlet을 사용 하는 것과 같습니다 `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="8294f-140">This is equivalent to using the `Stop-Service` cmdlet.</span></span>

### <span data-ttu-id="8294f-141">예 6: 로컬 컴퓨터에서 BIOS 가져오기</span><span class="sxs-lookup"><span data-stu-id="8294f-141">Example 6: Get the BIOS on the local computer</span></span>

<span data-ttu-id="8294f-142">이 예제에서는 로컬 컴퓨터에서 BIOS 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-142">This example gets the BIOS information from the local computer.</span></span> <span data-ttu-id="8294f-143">Cmdlet의 **Property** 매개 변수는 `Format-List` 반환 된 개체의 모든 속성을 목록으로 표시 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-143">The **Property** parameter of the `Format-List` cmdlet is used to display all properties of the returned object in a list.</span></span> <span data-ttu-id="8294f-144">기본적으로 구성 파일에 정의 된 속성의 하위 집합만 `Types.ps1xml` 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-144">By default, only the subset of properties defined in the `Types.ps1xml` configuration file are displayed.</span></span>

```powershell
Get-WmiObject -Class Win32_Bios | Format-List -Property *
```

```Output
Status                : OK
Name                  : Phoenix ROM BIOS PLUS Version 1.10 A05
Caption               : Phoenix ROM BIOS PLUS Version 1.10 A05
SMBIOSPresent         : True
__GENUS               : 2
__CLASS               : Win32_BIOS
__SUPERCLASS          : CIM_BIOSElement
__DYNASTY             : CIM_ManagedSystemElement
__RELPATH             : Win32_BIOS.Name="Phoenix ROM BIOS PLUS Version 1.10
__PROPERTY_COUNT      : 27
__DERIVATION          : {CIM_BIOSElement, CIM_SoftwareElement, CIM_LogicalElement,
__SERVER              : Server01
__NAMESPACE           : root\cimv2
__PATH                : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
BiosCharacteristics   : {7, 9, 10, 11...}
BIOSVersion           : {DELL   - 15, Phoenix ROM BIOS PLUS Version 1.10 A05}
BuildNumber           :
CodeSet               :
CurrentLanguage       : en|US|iso8859-1
Description           : Phoenix ROM BIOS PLUS Version 1.10 A05
IdentificationCode    :
InstallableLanguages  : 1
InstallDate           :
LanguageEdition       :
ListOfLanguages       : {en|US|iso8859-1}
Manufacturer          : Dell Inc.
OtherTargetOS         :
PrimaryBIOS           : True
ReleaseDate           : 20101103000000.000000+000
SerialNumber          : 8VDM9P1
SMBIOSBIOSVersion     : A05
SMBIOSMajorVersion    : 2
SMBIOSMinorVersion    : 6
SoftwareElementID     : Phoenix ROM BIOS PLUS Version 1.10 A05
SoftwareElementState  : 3
TargetOperatingSystem : 0
Version               : DELL   - 15
Scope                 : System.Management.ManagementScope
Path                  : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
Options               : System.Management.ObjectGetOptions
ClassPath             : \\JUNE-PC\root\cimv2:Win32_BIOS
Properties            : {BiosCharacteristics, BIOSVersion, BuildNumber, Caption...}
SystemProperties      : {__GENUS, __CLASS, __SUPERCLASS, __DYNASTY...}
Qualifiers            : {dynamic, Locale, provider, UUID}
Site                  :
Container             :
```

### <span data-ttu-id="8294f-145">예 7: 원격 컴퓨터에서 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="8294f-145">Example 7: Get the services on a remote computer</span></span>

<span data-ttu-id="8294f-146">이 예에서는 cmdlet의 **Credential** 매개 변수를 사용 하 여 `Get-WmiObject` 원격 컴퓨터의 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-146">This example uses the **Credential** parameter of the `Get-WmiObject` cmdlet to get the services on a remote computer.</span></span> <span data-ttu-id="8294f-147">**Credential** 매개 변수 값은 사용자 계정 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-147">The value of the **Credential** parameter is a user account name.</span></span> <span data-ttu-id="8294f-148">암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-148">The user is prompted for a password.</span></span>

```powershell
Get-WmiObject Win32_Service -Credential FABRIKAM\administrator -ComputerName Fabrikam
```

> [!NOTE]
> <span data-ttu-id="8294f-149">로컬 컴퓨터를 대상으로 하는 경우 자격 증명을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-149">Credentials cannot be used when targeting the local computer.</span></span>

## <span data-ttu-id="8294f-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8294f-150">PARAMETERS</span></span>

### <span data-ttu-id="8294f-151">-수정</span><span class="sxs-lookup"><span data-stu-id="8294f-151">-Amended</span></span>

<span data-ttu-id="8294f-152">WMI에서 반환되는 개체에 수정된 정보가 포함될지를 나타내는 값을 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-152">Gets or sets a value that indicates whether the objects that are returned from WMI should contain amended information.</span></span> <span data-ttu-id="8294f-153">일반적으로 수정된 정보는 지역화할 수 있는 정보(예: WMI 개체에 연결된 개체 및 속성 설명)입니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-153">Typically, amended information is localizable information, such as object and property descriptions, that is attached to the WMI object.</span></span>

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

### <span data-ttu-id="8294f-154">-AsJob</span><span class="sxs-lookup"><span data-stu-id="8294f-154">-AsJob</span></span>

<span data-ttu-id="8294f-155">명령을 백그라운드 작업으로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-155">Runs the command as a background job.</span></span> <span data-ttu-id="8294f-156">이 매개 변수를 사용하여 마치는 데 시간이 많이 걸리는 명령을 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="8294f-156">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="8294f-157">**AsJob** 매개 변수를 사용하는 경우 이 명령은 백그라운드 작업을 나타내는 개체를 반환한 다음 명령 프롬프트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-157">When you use the **AsJob** parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span> <span data-ttu-id="8294f-158">작업을 마치는 동안 세션에서 작업을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-158">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="8294f-159">`Get-WmiObject`가 원격 컴퓨터에서 사용 되는 경우 작업은 로컬 컴퓨터에 만들어지고 원격 컴퓨터의 결과는 로컬 컴퓨터에 자동으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-159">If `Get-WmiObject` is used on a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="8294f-160">작업을 관리하려면 Job cmdlet을 포함하는 cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-160">To manage the job, use the cmdlets that contain the Job cmdlets.</span></span> <span data-ttu-id="8294f-161">작업 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="8294f-161">To get the job results, use the `Receive-Job` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="8294f-162">원격 컴퓨터에 이 매개 변수를 사용하려면 원격을 사용하도록 로컬 및 원격 컴퓨터를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-162">To use this parameter with remote computers, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="8294f-163">또한 Windows Vista 이상 버전의 Windows에서 "관리자 권한으로 실행" 옵션을 사용하여 Windows PowerShell을 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-163">Additionally, you must start Windows PowerShell by using the "Run as administrator" option in Windows Vista and later versions of Windows.</span></span> <span data-ttu-id="8294f-164">자세한 내용은 [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8294f-164">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="8294f-165">Windows PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md) 및 [about_Remote_Jobs](../Microsoft.PowerShell.Core/about/about_Remote_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8294f-165">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/about/about_Remote_Jobs.md).</span></span>

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

### <span data-ttu-id="8294f-166">-인증</span><span class="sxs-lookup"><span data-stu-id="8294f-166">-Authentication</span></span>

<span data-ttu-id="8294f-167">WMI 연결에 사용되는 인증 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-167">Specifies the authentication level to be used with the WMI connection.</span></span>
<span data-ttu-id="8294f-168">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-168">Valid values are:</span></span>

- <span data-ttu-id="8294f-169">-1: 변경 되지 않음</span><span class="sxs-lookup"><span data-stu-id="8294f-169">-1: Unchanged</span></span>
- <span data-ttu-id="8294f-170">0: 기본값</span><span class="sxs-lookup"><span data-stu-id="8294f-170">0: Default</span></span>
- <span data-ttu-id="8294f-171">1: 없음 (인증이 수행 되지 않음)</span><span class="sxs-lookup"><span data-stu-id="8294f-171">1: None (No authentication in performed.)</span></span>
- <span data-ttu-id="8294f-172">2: 연결 (클라이언트가 응용 프로그램과의 관계를 설정 하는 경우에만 인증이 수행 됨)</span><span class="sxs-lookup"><span data-stu-id="8294f-172">2: Connect (Authentication is performed only when the client establishes a relationship with the application.)</span></span>
- <span data-ttu-id="8294f-173">3: 호출 (응용 프로그램이 요청을 받을 때 각 호출이 시작 될 때만 인증이 수행 됩니다.)</span><span class="sxs-lookup"><span data-stu-id="8294f-173">3: Call (Authentication is performed only at the beginning of each call when the application receives the request.)</span></span>
- <span data-ttu-id="8294f-174">4: 패킷 (클라이언트에서 받은 모든 데이터에 대해 인증이 수행 됩니다.)</span><span class="sxs-lookup"><span data-stu-id="8294f-174">4: Packet (Authentication is performed on all the data that is received from the client.)</span></span>
- <span data-ttu-id="8294f-175">5: PacketIntegrity (클라이언트와 응용 프로그램 간에 전송 되는 모든 데이터는 인증 되 고 확인 됩니다.)</span><span class="sxs-lookup"><span data-stu-id="8294f-175">5: PacketIntegrity (All the data that is transferred between the client and the application is authenticated and verified.)</span></span>
- <span data-ttu-id="8294f-176">6: PacketPrivacy (다른 인증 수준의 속성이 사용 되며 모든 데이터가 암호화 됩니다.)</span><span class="sxs-lookup"><span data-stu-id="8294f-176">6: PacketPrivacy (The properties of the other authentication levels are used, and all the data is encrypted.)</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8294f-177">-Authority</span><span class="sxs-lookup"><span data-stu-id="8294f-177">-Authority</span></span>

<span data-ttu-id="8294f-178">WMI 연결을 인증하는 데 사용할 권한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-178">Specifies the authority to use to authenticate the WMI connection.</span></span> <span data-ttu-id="8294f-179">표준 NTLM 또는 Kerberos 인증을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-179">You can specify standard NTLM or Kerberos authentication.</span></span> <span data-ttu-id="8294f-180">NTLM을 사용 하려면 권한 설정을로 설정 합니다 `ntlmdomain:<DomainName>` . 여기서은 `<DomainName>` 유효한 NTLM 도메인 이름을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-180">To use NTLM, set the authority setting to `ntlmdomain:<DomainName>`, where `<DomainName>` identifies a valid NTLM domain name.</span></span> <span data-ttu-id="8294f-181">Kerberos를 사용 하려면를 지정 `kerberos:<DomainName>\<ServerName>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-181">To use Kerberos, specify `kerberos:<DomainName>\<ServerName>`.</span></span> <span data-ttu-id="8294f-182">로컬 컴퓨터에 연결하는 경우 권한 설정을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-182">You cannot include the authority setting when you connect to the local computer.</span></span>

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

### <span data-ttu-id="8294f-183">-클래스</span><span class="sxs-lookup"><span data-stu-id="8294f-183">-Class</span></span>

<span data-ttu-id="8294f-184">WMI 클래스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-184">Specifies the name of a WMI class.</span></span> <span data-ttu-id="8294f-185">이 매개 변수를 사용하면 WMI 클래스의 인스턴스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-185">When this parameter is used, the cmdlet retrieves instances of the WMI class.</span></span>

```yaml
Type: System.String
Parameter Sets: query, list
Aliases: ClassName

Required: True (query), False (list)
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8294f-186">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="8294f-186">-ComputerName</span></span>

<span data-ttu-id="8294f-187">관리 작업의 대상 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-187">Specifies the target computer for the management operation.</span></span> <span data-ttu-id="8294f-188">FQDN (정규화 된 도메인 이름), NetBIOS 이름 또는 IP 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-188">Enter a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="8294f-189">원격 컴퓨터가 로컬 컴퓨터와 다른 도메인에 있는 경우 정규화된 도메인 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-189">When the remote computer is in a different domain than the local computer, the fully qualified domain name is required.</span></span>

<span data-ttu-id="8294f-190">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-190">The default is the local computer.</span></span> <span data-ttu-id="8294f-191">컴퓨터 이름 목록 등과 같은 형식으로 로컬 컴퓨터를 지정하려면 "localhost", 로컬 컴퓨터 이름 또는 점(.)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-191">To specify the local computer, such as in a list of computer names, use "localhost", the local computer name, or a dot (.).</span></span>

<span data-ttu-id="8294f-192">이 매개 변수는 WS-Management를 사용하는 Windows PowerShell 원격 기능을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-192">This parameter does not rely on Windows PowerShell remoting, which uses WS-Management.</span></span> <span data-ttu-id="8294f-193">**ComputerName** `Get-WmiObject` 컴퓨터가 원격 명령 WS-Management 실행 하도록 구성 되지 않은 경우에도의 ComputerName 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-193">You can use the **ComputerName** parameter of `Get-WmiObject` even if your computer is not configured to run WS-Management remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8294f-194">-Credential</span><span class="sxs-lookup"><span data-stu-id="8294f-194">-Credential</span></span>

<span data-ttu-id="8294f-195">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-195">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="8294f-196">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-196">The default is the current user.</span></span> <span data-ttu-id="8294f-197">사용자 이름 (예: "User01", "Domain01\User01")을 입력 User@Contoso.com 합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-197">Type a user name, such as "User01", "Domain01\User01", or User@Contoso.com.</span></span> <span data-ttu-id="8294f-198">또는 cmdlet에서 반환 된 개체와 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="8294f-198">Or, enter a **PSCredential** object, such as an object that is returned by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="8294f-199">사용자 이름을 입력하면 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-199">When you type a user name, you are prompted for a password.</span></span> <span data-ttu-id="8294f-200">로컬 컴퓨터를 대상으로 하는 경우 자격 증명을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-200">Credentials cannot be used when targeting the local computer.</span></span>

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

### <span data-ttu-id="8294f-201">-DirectRead</span><span class="sxs-lookup"><span data-stu-id="8294f-201">-DirectRead</span></span>

<span data-ttu-id="8294f-202">지정된 클래스에 대해 해당 기본 클래스나 파생 클래스와 관계없이 WMI 공급자에 대한 직접 액세스가 요청되었는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-202">Specifies whether direct access to the WMI provider is requested for the specified class without any regard to its base class or to its derived classes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: query, WQLQuery
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8294f-203">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="8294f-203">-EnableAllPrivileges</span></span>

<span data-ttu-id="8294f-204">명령에서 WMI 호출을 수행하기 전에 현재 사용자의 모든 권한을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-204">Enables all the privileges of the current user before the command makes the WMI call.</span></span>

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

### <span data-ttu-id="8294f-205">-Filter</span><span class="sxs-lookup"><span data-stu-id="8294f-205">-Filter</span></span>

<span data-ttu-id="8294f-206">필터로 사용할 **Where** 절을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-206">Specifies a **Where** clause to use as a filter.</span></span> <span data-ttu-id="8294f-207">WQL(WMI Query Language) 언어 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-207">Uses the syntax of the WMI Query Language (WQL).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8294f-208">매개 변수 값에 **Where** 키워드를 포함하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="8294f-208">Do not include the **Where** keyword in the value of the parameter.</span></span> <span data-ttu-id="8294f-209">예를 들어 다음 명령은 **DeviceID** 가 'c:'인 논리 디스크와 **Where** 키워드를 사용하지 않는 'WinRM' 이름의 서비스만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-209">For example, the following commands return only the logical disks that have a **DeviceID** of 'c:' and services that have the name 'WinRM' without using the **Where** keyword.</span></span>

`Get-WmiObject Win32_LogicalDisk -filter "DeviceID = 'c:' "`

`Get-WmiObject win32_service -filter "name='WinRM'"`

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8294f-210">-가장</span><span class="sxs-lookup"><span data-stu-id="8294f-210">-Impersonation</span></span>

<span data-ttu-id="8294f-211">사용할 가장 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-211">Specifies the impersonation level to use.</span></span>

<span data-ttu-id="8294f-212">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-212">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8294f-213">0: 기본값</span><span class="sxs-lookup"><span data-stu-id="8294f-213">0: Default.</span></span> <span data-ttu-id="8294f-214">기본 가장 수준에 대 한 로컬 레지스트리를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-214">Reads the local registry for the default impersonation level.</span></span> <span data-ttu-id="8294f-215">기본값은 일반적으로 **Impersonate** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-215">The default is usually set to **Impersonate** .</span></span>
- <span data-ttu-id="8294f-216">1: 익명.</span><span class="sxs-lookup"><span data-stu-id="8294f-216">1: Anonymous.</span></span> <span data-ttu-id="8294f-217">호출자의 자격 증명을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-217">Hides the credentials of the caller.</span></span>
- <span data-ttu-id="8294f-218">2:를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-218">2: Identify.</span></span> <span data-ttu-id="8294f-219">개체가 호출자의 자격 증명을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-219">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="8294f-220">3: Impersonate</span><span class="sxs-lookup"><span data-stu-id="8294f-220">3: Impersonate.</span></span> <span data-ttu-id="8294f-221">개체가 호출자의 자격 증명을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-221">Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="8294f-222">4: 대리자.</span><span class="sxs-lookup"><span data-stu-id="8294f-222">4: Delegate.</span></span> <span data-ttu-id="8294f-223">개체가 다른 개체가 호출자의 자격 증명을 사용하도록 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-223">Allows objects to permit other objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8294f-224">-목록</span><span class="sxs-lookup"><span data-stu-id="8294f-224">-List</span></span>

<span data-ttu-id="8294f-225">**Namespace** 매개 변수로 지정된 WMI 리포지토리 네임 스페이스의 WMI 클래스의 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-225">Gets the names of the WMI classes in the WMI repository namespace that is specified by the **Namespace** parameter.</span></span>

<span data-ttu-id="8294f-226">**List** 매개 변수를 지정 하 고 **Namespace** 매개 변수는 지정 하지 않으면는 `Get-WmiObject` 기본적으로 **Root\Cimv2** 네임 스페이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-226">If you specify the **List** parameter, but not the **Namespace** parameter, `Get-WmiObject` uses the **Root\Cimv2** namespace by default.</span></span> <span data-ttu-id="8294f-227">이 cmdlet은 레지스트리 키의 **기본 네임 스페이스** 레지스트리 항목을 사용 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WBEM\Scripting` 하 여 기본 네임 스페이스를 결정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-227">This cmdlet does not use the **Default Namespace** registry entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WBEM\Scripting` registry key to determine the default namespace.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8294f-228">-Locale</span><span class="sxs-lookup"><span data-stu-id="8294f-228">-Locale</span></span>

<span data-ttu-id="8294f-229">WMI 개체의 기본 설정 로캘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-229">Specifies the preferred locale for WMI objects.</span></span>
<span data-ttu-id="8294f-230">MS_\<LCID\> 형식으로 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-230">Enter a value in MS_\<LCID\> format.</span></span>

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

### <span data-ttu-id="8294f-231">-Namespace</span><span class="sxs-lookup"><span data-stu-id="8294f-231">-Namespace</span></span>

<span data-ttu-id="8294f-232">**Class** 매개 변수와 함께 사용하는 경우 **Namespace** 매개 변수가 지정된 WMI 클래스가 있는 리포지토리 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-232">When used with the **Class** parameter, the **Namespace** parameter specifies the WMI repository namespace where the specified WMI class is located.</span></span> <span data-ttu-id="8294f-233">**List** 매개 변수와 함께 사용하는 경우 이 매개 변수는 WMI 클래스 정보를 수집할 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-233">When used with the **List** parameter, it specifies the namespace from which to gather WMI class information.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8294f-234">-속성</span><span class="sxs-lookup"><span data-stu-id="8294f-234">-Property</span></span>

<span data-ttu-id="8294f-235">이 cmdlet이 정보를 가져오는 WMI 클래스 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-235">Specifies the WMI class properties that this cmdlet gets information from.</span></span> <span data-ttu-id="8294f-236">속성 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-236">Enter the property names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: query
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8294f-237">-Query</span><span class="sxs-lookup"><span data-stu-id="8294f-237">-Query</span></span>

<span data-ttu-id="8294f-238">지정된 WQL(WMI Query Language) 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-238">Runs the specified WMI Query Language (WQL) statement.</span></span> <span data-ttu-id="8294f-239">이 매개 변수는 이벤트 쿼리를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-239">This parameter does not support event queries.</span></span>

```yaml
Type: System.String
Parameter Sets: WQLQuery
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8294f-240">-재귀</span><span class="sxs-lookup"><span data-stu-id="8294f-240">-Recurse</span></span>

<span data-ttu-id="8294f-241">**Class** 매개 변수로 지정된 클래스 이름의 현재 네임스페이스 및 기타 모든 네임스페이스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-241">Searches the current namespace and all other namespaces for the class name that is specified by the **Class** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8294f-242">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="8294f-242">-ThrottleLimit</span></span>

<span data-ttu-id="8294f-243">동시에 실행할 수 있는 최대 WMI 작업의 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-243">Specifies the maximum number of WMI operations that can be executed simultaneously.</span></span> <span data-ttu-id="8294f-244">이 매개 변수는 **AsJob** 매개 변수가 명령에 사용 되는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-244">This parameter is valid only when the **AsJob** parameter is used in the command.</span></span>

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

### <span data-ttu-id="8294f-245">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8294f-245">CommonParameters</span></span>

<span data-ttu-id="8294f-246">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8294f-246">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8294f-247">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8294f-247">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8294f-248">입력</span><span class="sxs-lookup"><span data-stu-id="8294f-248">INPUTS</span></span>

### <span data-ttu-id="8294f-249">없음</span><span class="sxs-lookup"><span data-stu-id="8294f-249">None</span></span>

<span data-ttu-id="8294f-250">입력을로 파이프 할 수 없습니다 `Get-WmiObject` .</span><span class="sxs-lookup"><span data-stu-id="8294f-250">You cannot pipe input to `Get-WmiObject`.</span></span>

## <span data-ttu-id="8294f-251">출력</span><span class="sxs-lookup"><span data-stu-id="8294f-251">OUTPUTS</span></span>

### <span data-ttu-id="8294f-252">PSObject 또는 System.web. Remorerejob</span><span class="sxs-lookup"><span data-stu-id="8294f-252">PSObject or System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="8294f-253">**AsJob** 매개 변수를 사용하는 경우 이 cmdlet 에서 작업 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-253">When you use the **AsJob** parameter, the cmdlet returns a job object.</span></span> <span data-ttu-id="8294f-254">그렇지 않으면를 반환 하는 개체는 `Get-WmiObject` **클래스** 매개 변수의 값에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-254">Otherwise, the object that `Get-WmiObject` returns depends on the value of the **Class** parameter.</span></span>

## <span data-ttu-id="8294f-255">참고</span><span class="sxs-lookup"><span data-stu-id="8294f-255">NOTES</span></span>

<span data-ttu-id="8294f-256">원격 컴퓨터의 WMI 정보에 액세스하려면 해당 컴퓨터의 로컬 관리자 그룹의 구성원인 계정으로 cmdlet을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-256">To access WMI information on a remote computer, the cmdlet must run under an account that is a member of the local administrators group on the remote computer.</span></span> <span data-ttu-id="8294f-257">또는 다른 계정에 대한 액세스 권한을 제공하기 위해 원격 리포지토리의 WMI 네임스페이스에 대한 기본 액세스 제어를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-257">Or, the default access control on the WMI namespace of the remote repository can be changed to give access rights to other accounts.</span></span>

<span data-ttu-id="8294f-258">기본적으로 각 WMI 클래스의 일부 속성만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-258">Only some of the properties of each WMI class are displayed by default.</span></span> <span data-ttu-id="8294f-259">각 WMI 클래스에 대해 표시되는 속성 집합은 Types.ps1xml 구성 파일에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-259">The set of properties that is displayed for each WMI class is specified in the Types.ps1xml configuration file.</span></span> <span data-ttu-id="8294f-260">WMI 개체의 모든 속성을 가져오려면 또는 cmdlet을 사용 `Get-Member` `Format-List` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8294f-260">To get all properties of a WMI object, use the `Get-Member` or `Format-List` cmdlets.</span></span>

## <span data-ttu-id="8294f-261">관련 링크</span><span class="sxs-lookup"><span data-stu-id="8294f-261">RELATED LINKS</span></span>

[<span data-ttu-id="8294f-262">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="8294f-262">Invoke-WmiMethod</span></span>](Invoke-WmiMethod.md)

[<span data-ttu-id="8294f-263">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="8294f-263">Remove-WmiObject</span></span>](Remove-WmiObject.md)

[<span data-ttu-id="8294f-264">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="8294f-264">Set-WmiInstance</span></span>](Set-WmiInstance.md)

[<span data-ttu-id="8294f-265">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8294f-265">Get-WSManInstance</span></span>](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[<span data-ttu-id="8294f-266">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="8294f-266">Invoke-WSManAction</span></span>](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[<span data-ttu-id="8294f-267">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8294f-267">New-WSManInstance</span></span>](../Microsoft.WsMan.Management/New-WSManInstance.md)

[<span data-ttu-id="8294f-268">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8294f-268">Remove-WSManInstance</span></span>](../Microsoft.WsMan.Management/Remove-WSManInstance.md)
