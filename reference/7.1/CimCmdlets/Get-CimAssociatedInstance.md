---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimassociatedinstance?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimAssociatedInstance
ms.openlocfilehash: c00507460cb80121c0fc8fc246d7fb3f7d7fe0f3
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218826"
---
# <span data-ttu-id="20759-103">Get-CimAssociatedInstance</span><span class="sxs-lookup"><span data-stu-id="20759-103">Get-CimAssociatedInstance</span></span>

## <span data-ttu-id="20759-104">개요</span><span class="sxs-lookup"><span data-stu-id="20759-104">SYNOPSIS</span></span>
<span data-ttu-id="20759-105">연결에 의해 특정 CIM 인스턴스에 연결 된 CIM 인스턴스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-105">Retrieves the CIM instances that are connected to a specific CIM instance by an association.</span></span>

## <span data-ttu-id="20759-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="20759-106">SYNTAX</span></span>

### <span data-ttu-id="20759-107">ComputerSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="20759-107">ComputerSet (Default)</span></span>

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] [-ComputerName <String[]>] [-KeyOnly] [<CommonParameters>]
```

### <span data-ttu-id="20759-108">SessionSet</span><span class="sxs-lookup"><span data-stu-id="20759-108">SessionSet</span></span>

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] -CimSession <CimSession[]> [-KeyOnly] [<CommonParameters>]
```

## <span data-ttu-id="20759-109">설명</span><span class="sxs-lookup"><span data-stu-id="20759-109">DESCRIPTION</span></span>

<span data-ttu-id="20759-110">`Get-CimAssociatedInstance`Cmdlet은 연결을 통해 원본 인스턴스 라고 하는 특정 cim 인스턴스에 연결 된 cim 인스턴스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-110">The `Get-CimAssociatedInstance` cmdlet retrieves the CIM instances connected to a specific CIM instance, called the source instance, by an association.</span></span>

<span data-ttu-id="20759-111">연결에서 각 CIM 인스턴스는 명명 된 역할을 가지 며 동일한 CIM 인스턴스는 다른 역할의 연결에 참여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20759-111">In an association, each CIM instance has a named role and the same CIM instance can participate in an association in different roles.</span></span>

<span data-ttu-id="20759-112">InputObject 매개 변수를 지정 하지 않으면 cmdlet은 다음 방법 중 하나로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-112">If the InputObject parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="20759-113">**ComputerName** 매개 변수와 **CimSession** 매개 변수를 모두 지정 하지 않으면이 Cmdlet은 COM (구성 요소 개체 모델) 세션을 사용 하 여 WMI (로컬 WMI(Windows Management Instrumentation))에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-113">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="20759-114">**Computername** 매개 변수 또는 **CimSession** 매개 변수를 지정 하는 경우이 cmdlet은 **computername** 매개 변수 또는 **CimSession** 매개 변수로 지정 된 CIM 서버에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-114">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

## <span data-ttu-id="20759-115">예제</span><span class="sxs-lookup"><span data-stu-id="20759-115">EXAMPLES</span></span>

### <span data-ttu-id="20759-116">예 1: 특정 인스턴스의 연결 된 모든 인스턴스 가져오기</span><span class="sxs-lookup"><span data-stu-id="20759-116">Example 1: Get all the associated instances of a specific instance</span></span>

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1]
```

<span data-ttu-id="20759-117">이 명령 집합은 Win32_LogicalDisk 된 클래스의 인스턴스를 검색 하 고 `$disk` cmdlet을 사용 하 여 라는 변수에 정보를 저장 합니다 `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="20759-117">This set of commands retrieves the instances of the class named Win32_LogicalDisk and stores the information in a variable named `$disk` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="20759-118">그러면 변수의 첫 번째 논리 디스크 인스턴스가 cmdlet에 대 한 입력 개체로 사용 되어 지정 된 `Get-CimAssociatedInstance` cim 인스턴스의 모든 연결 된 cim 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="20759-118">The first logical disk instance in the variable is then used as the input object for the `Get-CimAssociatedInstance` cmdlet to get all the associated CIM instances of the specified CIM instance.</span></span>

### <span data-ttu-id="20759-119">예제 2: 특정 형식의 모든 연결 된 인스턴스 가져오기</span><span class="sxs-lookup"><span data-stu-id="20759-119">Example 2: Get all the associated instances of a specific type</span></span>

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1] -ResultClass Win32_DiskPartition
```

<span data-ttu-id="20759-120">이 명령 집합은 **Win32_LogicalDisk** 클래스의 모든 인스턴스를 검색 하 여 라는 변수에 저장 `$disk` 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-120">This set of commands retrieves all the instances of the **Win32_LogicalDisk** class and stores them in a variable named `$disk`.</span></span> <span data-ttu-id="20759-121">그런 다음 변수의 첫 번째 논리 디스크 인스턴스는 `Get-CimAssociatedInstance` **Win32_DiskPartition** 지정 된 연결 클래스를 통해 연결 된 모든 연결 된 인스턴스를 가져오기 위해 cmdlet에 대 한 입력 개체로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="20759-121">The first logical disk instance in the variable is then used as the input object for the `Get-CimAssociatedInstance` cmdlet to get all the associated instances that are associated through the specified association class **Win32_DiskPartition**.</span></span>

### <span data-ttu-id="20759-122">예 3: 특정 클래스의 한정자를 통해 연결 된 모든 인스턴스 가져오기</span><span class="sxs-lookup"><span data-stu-id="20759-122">Example 3: Get all the associated instances through qualifier of a specific class</span></span>

```powershell
$s = Get-CimInstance -Query "Select * from Win32_Service where name like 'Winmgmt'"
Get-CimClass -ClassName *Service* -Qualifier "Association"
$c.CimClasName
```

```Output
Win32_LoadOrderGroupServiceDependencies
Win32_DependentService
Win32_SystemServices
Win32_LoadOrderGroupServiceMembers
Win32_ServiceSpecificationService
```

```powershell
Get-CimAssociatedInstance -InputObject $s -Association Win32_DependentService
```

<span data-ttu-id="20759-123">이 명령 집합은 WMI 서비스에 종속 된 서비스를 검색 하 여 라는 변수에 저장 `$s` 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-123">This set of commands retrieves the services that depend on WMI service and stores them in a variable named `$s`.</span></span> <span data-ttu-id="20759-124">**Win32_DependentService** 의 연결 클래스 이름은 Cmdlet으로 연결을 지정 하 여 cmdlet을 사용 하 여 검색 된 `Get-CimClass` 다음 cmdlet에 $s를 전달 하 여 **Association** `Get-CimAssociatedInstance` 검색 된 연결 클래스의 연결 된 모든 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="20759-124">The association class name for the **Win32_DependentService** is retrieved using the `Get-CimClass` cmdlet by specifying **Association** as the qualifier and is then passed with $s to the `Get-CimAssociatedInstance` cmdlet to get all the associated instances of the retrieved association class.</span></span>

## <span data-ttu-id="20759-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="20759-125">PARAMETERS</span></span>

### <span data-ttu-id="20759-126">-연결</span><span class="sxs-lookup"><span data-stu-id="20759-126">-Association</span></span>

<span data-ttu-id="20759-127">연결 클래스의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-127">Specifies the name of the association class.</span></span> <span data-ttu-id="20759-128">이 매개 변수를 지정 하지 않으면 cmdlet은 모든 형식의 기존 연결 개체를 모두 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-128">If you do not specify this parameter, the cmdlet returns all existing association objects of any type.</span></span>

<span data-ttu-id="20759-129">예를 들어, 클래스 A가 AB1 및 AB2의 두 연결을 통해 B 클래스와 연결 된 경우이 매개 변수를 사용 하 여 연결 형식 (AB1 또는 AB2)을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20759-129">For example, if class A is associated with class B through two associations, AB1 and AB2, then this parameter can be used to specify the type of association, either AB1 or AB2.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="20759-130">-CimSession</span><span class="sxs-lookup"><span data-stu-id="20759-130">-CimSession</span></span>

<span data-ttu-id="20759-131">지정 된 CIM 세션을 사용 하 여 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-131">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="20759-132">CIM 세션을 포함 하는 변수 또는 CIM 세션을 만들거나 가져오는 명령 (예: 또는)을 입력 `New-CimSession` `Get-CimSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-132">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as `New-CimSession` or `Get-CimSession`.</span></span> <span data-ttu-id="20759-133">자세한 내용은 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="20759-133">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: SessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="20759-134">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="20759-134">-ComputerName</span></span>

<span data-ttu-id="20759-135">CIM 작업을 실행 하려는 컴퓨터의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-135">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="20759-136">FQDN (정규화 된 도메인 이름) 또는 NetBIOS 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20759-136">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="20759-137">이 매개 변수를 지정 하면 cmdlet이 WsMan 프로토콜을 사용 하 여 지정 된 컴퓨터에 대 한 임시 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="20759-137">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="20759-138">이 매개 변수를 지정 하지 않으면 cmdlet은 COM (구성 요소 개체 모델)을 사용 하 여 로컬 컴퓨터에서 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-138">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="20759-139">동일한 컴퓨터에서 여러 작업을 수행 하는 경우 CIM 세션을 사용 하 여 연결 하면 성능이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="20759-139">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20759-140">-InputObject</span><span class="sxs-lookup"><span data-stu-id="20759-140">-InputObject</span></span>

<span data-ttu-id="20759-141">이 cmdlet에 대한 입력을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-141">Specifies the input to this cmdlet.</span></span> <span data-ttu-id="20759-142">이 매개 변수를 사용하거나 이 cmdlet에 입력을 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20759-142">You can use this parameter, or you can pipe the input to this cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="20759-143">-KeyOnly</span><span class="sxs-lookup"><span data-stu-id="20759-143">-KeyOnly</span></span>

<span data-ttu-id="20759-144">키 속성만 채워진 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-144">Returns objects with only key properties populated.</span></span> <span data-ttu-id="20759-145">이렇게 하면 네트워크를 통해 전송 되는 데이터의 양이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="20759-145">This reduces the amount of data that is transferred over the network.</span></span>

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

### <span data-ttu-id="20759-146">-Namespace</span><span class="sxs-lookup"><span data-stu-id="20759-146">-Namespace</span></span>

<span data-ttu-id="20759-147">CIM 작업에 대 한 네임 스페이스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-147">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="20759-148">기본 네임 스페이스는 root/cimv2입니다.</span><span class="sxs-lookup"><span data-stu-id="20759-148">The default namespace is root/cimv2.</span></span>

> [!NOTE]
> <span data-ttu-id="20759-149">PowerShell에서 네임 스페이스 목록을 제공 하기 위해 로컬 WMI 서버에서 네임 스페이스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 네임 스페이스 목록을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20759-149">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="20759-150">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="20759-150">-OperationTimeoutSec</span></span>

<span data-ttu-id="20759-151">Cmdlet이 컴퓨터의 응답을 기다리는 시간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-151">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="20759-152">기본적으로이 매개 변수의 값은 0 이며이는 cmdlet이 서버에 대 한 기본 시간 제한 값을 사용 함을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-152">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="20759-153">**Operationtimeoutsec** 매개 변수가 강력한 연결 다시 시도 시간 제한 3 분 보다 작은 값으로 설정 된 경우, 서버에서 작업을 다시 연결할 수 있기 때문에 **operationtimeoutsec** 매개 변수의 값 보다 마지막으로 네트워크 오류가 복구 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="20759-153">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="20759-154">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="20759-154">-ResourceUri</span></span>

<span data-ttu-id="20759-155">리소스 클래스 또는 인스턴스의 리소스 URI (uniform resource identifier)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-155">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="20759-156">URI는 컴퓨터에서 특정 유형의 리소스(예: 디스크 또는 프로세스)를 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="20759-156">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="20759-157">URI는 접두사와 리소스 경로로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="20759-157">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="20759-158">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="20759-158">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="20759-159">기본적으로이 매개 변수를 지정 하지 않으면 DMTF 표준 리소스 URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 가 사용 되 고 클래스 이름이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="20759-159">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="20759-160">**ResourceURI** 는 wsman 프로토콜을 사용 하 여 만든 cim 세션에만 사용할 수 있으며, **ComputerName** 매개 변수를 지정 하는 경우에만 wsman을 사용 하 여 cim 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20759-160">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="20759-161">**ComputerName** 매개 변수를 지정 하지 않고이 매개 변수를 지정 하거나 dcom 프로토콜을 사용 하 여 만든 CIM 세션을 지정 하는 경우 Dcom 프로토콜이 **ResourceURI** 매개 변수를 지원 하지 않기 때문에 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-161">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="20759-162">**ResourceUri** 매개 변수와 **필터** 매개 변수를 모두 지정 하면 **필터** 매개 변수가 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="20759-162">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20759-163">-ResultClassName</span><span class="sxs-lookup"><span data-stu-id="20759-163">-ResultClassName</span></span>

<span data-ttu-id="20759-164">연결 된 인스턴스의 클래스 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-164">Specifies the class name of the associated instances.</span></span> <span data-ttu-id="20759-165">CIM 인스턴스는 하나 이상의 CIM 인스턴스와 연결 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20759-165">A CIM instance can be associated with one or more CIM instances.</span></span> <span data-ttu-id="20759-166">결과 클래스 이름을 지정 하지 않으면 연결 된 모든 CIM 인스턴스가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="20759-166">All associated CIM instances are returned if you do not specify the result class name.</span></span>

<span data-ttu-id="20759-167">기본적으로이 매개 변수의 값은 null 이며 연결 된 모든 CIM 인스턴스가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="20759-167">By default, the value of this parameter is null, and all associated CIM instances are returned.</span></span>

<span data-ttu-id="20759-168">특정 클래스 이름과 일치 하도록 연결 결과를 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20759-168">You can filter the association results to match a specific class name.</span></span> <span data-ttu-id="20759-169">서버에서 필터링이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="20759-169">Filtering happens on the server.</span></span> <span data-ttu-id="20759-170">이 매개 변수를 지정 하지 않으면 `Get-CIMAssociatedInstance` 기존 연결을 모두 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-170">If this parameter is not specified, `Get-CIMAssociatedInstance` returns all existing associations.</span></span> <span data-ttu-id="20759-171">예를 들어 클래스 A가 B, C 및 D 클래스와 연결 된 경우이 매개 변수를 사용 하 여 출력을 특정 형식 (B, C 또는 D)으로 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20759-171">For example, if class A is associated with classes B, C and D, then this parameter can be used to restrict the output to a specific type (B, C or D).</span></span>

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

### <span data-ttu-id="20759-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="20759-172">CommonParameters</span></span>

<span data-ttu-id="20759-173">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="20759-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="20759-174">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="20759-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="20759-175">입력</span><span class="sxs-lookup"><span data-stu-id="20759-175">INPUTS</span></span>

### <span data-ttu-id="20759-176">없음</span><span class="sxs-lookup"><span data-stu-id="20759-176">None</span></span>

<span data-ttu-id="20759-177">이 cmdlet은 입력 개체를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="20759-177">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="20759-178">출력</span><span class="sxs-lookup"><span data-stu-id="20759-178">OUTPUTS</span></span>

### <span data-ttu-id="20759-179">System.Object</span><span class="sxs-lookup"><span data-stu-id="20759-179">System.Object</span></span>

<span data-ttu-id="20759-180">이 cmdlet은 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="20759-180">This cmdlet returns an object.</span></span>

## <span data-ttu-id="20759-181">참고</span><span class="sxs-lookup"><span data-stu-id="20759-181">NOTES</span></span>

## <span data-ttu-id="20759-182">관련 링크</span><span class="sxs-lookup"><span data-stu-id="20759-182">RELATED LINKS</span></span>

[<span data-ttu-id="20759-183">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="20759-183">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="20759-184">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="20759-184">Get-CimInstance</span></span>](get-ciminstance.md)

