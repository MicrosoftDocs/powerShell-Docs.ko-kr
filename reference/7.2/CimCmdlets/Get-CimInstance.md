---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/21/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-ciminstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimInstance
ms.openlocfilehash: 0e4a148601f3ef2212f9c97128c54258906106d7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601254"
---
# <span data-ttu-id="21141-102">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="21141-102">Get-CimInstance</span></span>

## <span data-ttu-id="21141-103">개요</span><span class="sxs-lookup"><span data-stu-id="21141-103">SYNOPSIS</span></span>
<span data-ttu-id="21141-104">CIM 서버에서 클래스의 CIM 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="21141-104">Gets the CIM instances of a class from a CIM server.</span></span>

## <span data-ttu-id="21141-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="21141-105">SYNTAX</span></span>

### <span data-ttu-id="21141-106">ClassNameComputerSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="21141-106">ClassNameComputerSet (Default)</span></span>

```
Get-CimInstance [-ClassName] <String> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="21141-107">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="21141-107">ResourceUriSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> -ResourceUri <Uri> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="21141-108">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="21141-108">QuerySessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

### <span data-ttu-id="21141-109">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="21141-109">ClassNameSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ClassName] <String> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="21141-110">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="21141-110">CimInstanceSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### <span data-ttu-id="21141-111">CimInstanceComputerSet</span><span class="sxs-lookup"><span data-stu-id="21141-111">CimInstanceComputerSet</span></span>

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### <span data-ttu-id="21141-112">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="21141-112">ResourceUriComputerSet</span></span>

```
Get-CimInstance -ResourceUri <Uri> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="21141-113">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="21141-113">QueryComputerSet</span></span>

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

## <span data-ttu-id="21141-114">설명</span><span class="sxs-lookup"><span data-stu-id="21141-114">DESCRIPTION</span></span>

<span data-ttu-id="21141-115">`Get-CimInstance`Cmdlet은 cim 서버에서 클래스의 cim 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="21141-115">The `Get-CimInstance` cmdlet gets the CIM instances of a class from a CIM server.</span></span> <span data-ttu-id="21141-116">이 cmdlet에 대 한 쿼리 또는 클래스 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21141-116">You can specify either the class name or a query for this cmdlet.</span></span> <span data-ttu-id="21141-117">이 cmdlet은 cim 서버에 있는 CIM 인스턴스의 스냅숏을 나타내는 CIM 인스턴스 개체를 하나 이상 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-117">This cmdlet returns one or more CIM instance objects representing a snapshot of the CIM instances present on the CIM server.</span></span>

<span data-ttu-id="21141-118">**InputObject** 매개 변수를 지정 하지 않으면 cmdlet은 다음 방법 중 하나로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-118">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="21141-119">**ComputerName** 매개 변수와 **CimSession** 매개 변수를 모두 지정 하지 않으면이 Cmdlet은 COM (구성 요소 개체 모델) 세션을 사용 하 여 WMI (로컬 WMI(Windows Management Instrumentation))에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-119">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="21141-120">**Computername** 매개 변수 또는 **CimSession** 매개 변수를 지정 하는 경우이 cmdlet은 **computername** 매개 변수 또는 **CimSession** 매개 변수로 지정 된 CIM 서버에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-120">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="21141-121">**InputObject** 매개 변수를 지정 하는 경우 cmdlet은 다음 방법 중 하나로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-121">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="21141-122">**ComputerName** 매개 변수와 **CimSession** 매개 변수를 모두 지정 하지 않으면이 cmdlet은 입력 개체의 컴퓨터 이름과 CIM 세션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-122">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="21141-123">**ComputerName** 매개 변수 또는 **CimSession** 매개 변수 중 하나가 지정 된 경우이 cmdlet은 CimSession 매개 변수 값 또는 **ComputerName** 매개 변수 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-123">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the CimSession parameter value or **ComputerName** parameter value.</span></span>

## <span data-ttu-id="21141-124">예제</span><span class="sxs-lookup"><span data-stu-id="21141-124">EXAMPLES</span></span>

### <span data-ttu-id="21141-125">예제 1: 지정 된 클래스의 CIM 인스턴스 가져오기</span><span class="sxs-lookup"><span data-stu-id="21141-125">Example 1: Get the CIM instances of a specified class</span></span>

<span data-ttu-id="21141-126">이 예제에서는 **Win32_Process** 이라는 클래스의 CIM 인스턴스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-126">This example retrieves the CIM instances of a class named **Win32_Process**.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Process
```

### <span data-ttu-id="21141-127">예제 2: WMI 서버에서 네임 스페이스 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="21141-127">Example 2: Get a list of namespaces from a WMI server</span></span>

<span data-ttu-id="21141-128">이 예제에서는 WMI 서버의 **루트** 네임 스페이스에서 네임 스페이스 목록을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-128">This example retrieves a list of namespaces under the **Root** namespace on a WMI server.</span></span>

```powershell
Get-CimInstance -Namespace root -ClassName __Namespace
```

### <span data-ttu-id="21141-129">예제 3: 쿼리를 사용 하 여 필터링 된 클래스의 인스턴스 가져오기</span><span class="sxs-lookup"><span data-stu-id="21141-129">Example 3: Get instances of a class filtered by using a query</span></span>

<span data-ttu-id="21141-130">이 예제에서는 **쿼리** 매개 변수로 지정 된 쿼리를 사용 하 여 **Win32_Process** 이라는 클래스의 **P** 문자로 시작 하는 모든 CIM 인스턴스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-130">This example retrieves all the CIM instances that start with the letter **P** of a class named **Win32_Process** using the query specified by a **Query** parameter.</span></span>

```powershell
Get-CimInstance -Query "SELECT * from Win32_Process WHERE name LIKE 'P%'"
```

### <span data-ttu-id="21141-131">예제 4: 클래스 이름 및 필터 식을 사용 하 여 필터링 된 클래스의 인스턴스 가져오기</span><span class="sxs-lookup"><span data-stu-id="21141-131">Example 4: Get instances of a class filtered by using a class name and a filter expression</span></span>

<span data-ttu-id="21141-132">이 예제에서는 Filter 매개 변수를 사용 하 여 **Win32_Process** 이라는 클래스의 **P** 문자로 시작 하는 모든 CIM 인스턴스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-132">This example retrieves all the CIM instances that start with the letter **P** of a class named **Win32_Process** using the Filter parameter.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Process -Filter "Name like 'P%'"
```

### <span data-ttu-id="21141-133">예 5: 키 속성만 채워진 CIM 인스턴스 가져오기</span><span class="sxs-lookup"><span data-stu-id="21141-133">Example 5: Get the CIM instances with only key properties filled in</span></span>

<span data-ttu-id="21141-134">이 예제에서는 key 속성을 사용 하 여 **Win32_Process** 라는 클래스에 대해 메모리에 새 CIM 인스턴스를 만들고 `@{ "Handle"=0 }` 라는 변수에 저장 `$x` 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-134">This example creates a new CIM instance in memory for a class named **Win32_Process** with the key property `@{ "Handle"=0 }` and stores it in a variable named `$x`.</span></span> <span data-ttu-id="21141-135">변수는 `Get-CimInstance` 특정 인스턴스를 가져오기 위해 cmdlet에 CIM 인스턴스로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21141-135">The variable is passed as a CIM instance to the `Get-CimInstance` cmdlet to get a particular instance.</span></span>

```powershell
$x = New-CimInstance -ClassName Win32_Process -Namespace root\cimv2 -Property @{ "Handle"=0 } -Key Handle -ClientOnly
Get-CimInstance -CimInstance $x
```

### <span data-ttu-id="21141-136">예제 6: CIM 인스턴스 검색 및 다시 사용</span><span class="sxs-lookup"><span data-stu-id="21141-136">Example 6: Retrieve CIM instances and reuse them</span></span>

<span data-ttu-id="21141-137">이 예제에서는 **Win32_Process** 된 클래스의 CIM 인스턴스를 가져와 및 변수에 저장 `$x` `$y` 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-137">This example gets the CIM instances of a class named **Win32_Process** and stores them in the variables `$x` and `$y`.</span></span> <span data-ttu-id="21141-138">`$x`그런 다음 변수는 **Name** 및 **KernelModeTime** 속성만 포함 된 테이블에서 **AutoSize** 로 설정 된 테이블로 형식이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21141-138">The variable `$x` is then formatted in a table containing only the **Name** and **KernelModeTime** properties, the table set to **AutoSize**.</span></span>

```powershell
$x,$y = Get-CimInstance -ClassName Win32_Process
$x | Format-Table -Property Name,KernelModeTime -AutoSize
```

```Output
Name                 KernelModeTime
----                 --------------
System Idle Process 157238797968750
```

### <span data-ttu-id="21141-139">예 7: 원격 컴퓨터에서 CIM 인스턴스 가져오기</span><span class="sxs-lookup"><span data-stu-id="21141-139">Example 7: Get CIM instances from remote computer</span></span>

<span data-ttu-id="21141-140">이 예제에서는 **Server01** 및 **Server02** 라는 원격 컴퓨터에서 **Win32_ComputerSystem** 이라는 클래스의 CIM 인스턴스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-140">This example retrieves the CIM instances of a class named **Win32_ComputerSystem** from the remote computers named **Server01** and **Server02**.</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName Server01,Server02
```

### <span data-ttu-id="21141-141">예 8: 모든 속성 대신 키 속성만 가져오기</span><span class="sxs-lookup"><span data-stu-id="21141-141">Example 8: Getting only the key properties, instead of all properties</span></span>

<span data-ttu-id="21141-142">이 예제에서는 개체 및 네트워크 트래픽의 크기를 줄이는 키 속성만 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-142">This example retrieves only the key properties, which reduces the size of the object and network traffic.</span></span>

```powershell
$x = Get-CimInstance -Class Win32_Process -KeyOnly
$x | Invoke-CimMethod -MethodName GetOwner
```

### <span data-ttu-id="21141-143">예 9: 모든 속성 대신 속성의 하위 집합만 가져오기</span><span class="sxs-lookup"><span data-stu-id="21141-143">Example 9: Getting only a subset of properties, instead of all properties</span></span>

<span data-ttu-id="21141-144">이 예제에서는 개체 및 네트워크 트래픽의 크기를 줄이는 속성의 하위 집합만 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-144">This example retrieves only a subset of properties, which reduces the size of the object and network traffic.</span></span>

```powershell
Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x = Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x | Invoke-CimMethod -MethodName GetOwner
```

<span data-ttu-id="21141-145">**Property** 매개 변수를 사용 하 여 검색 된 인스턴스는 다른 CIM 작업 (예: 또는)을 수행 하는 데 사용할 수 있습니다 `Set-CimInstance` `Invoke-CimMethod` .</span><span class="sxs-lookup"><span data-stu-id="21141-145">The instance retrieved with the **Property** parameter can be used to perform other CIM operations, for example `Set-CimInstance` or `Invoke-CimMethod`.</span></span>

### <span data-ttu-id="21141-146">예 10: CIM 세션을 사용 하 여 CIM 인스턴스 가져오기</span><span class="sxs-lookup"><span data-stu-id="21141-146">Example 10: Get the CIM instance using CIM session</span></span>

<span data-ttu-id="21141-147">이 예에서는 cmdlet을 사용 하 여 **Server01** 및 **Server02** 라는 컴퓨터에서 CIM 세션을 만들고 `New-CimSession` 이라는 변수에 세션 정보를 저장 `$s` 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-147">This example creates a CIM session on the computers named **Server01** and **Server02** using the `New-CimSession` cmdlet and stores the session information in a variable named `$s`.</span></span> <span data-ttu-id="21141-148">그런 다음 CimSession 매개 변수를 사용 하 여 변수의 내용을에 전달 하 여 `Get-CimInstance` **Win32_ComputerSystem** 라는 클래스의 CIM 인스턴스를 가져옵니다. </span><span class="sxs-lookup"><span data-stu-id="21141-148">The contents of the variable are then passed to `Get-CimInstance` by using the **CimSession** parameter, to get the CIM instances of the class named **Win32_ComputerSystem**.</span></span>

```powershell
$s = New-CimSession -ComputerName Server01,Server02
Get-CimInstance -ClassName Win32_ComputerSystem -CimSession $s
```

## <span data-ttu-id="21141-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="21141-149">PARAMETERS</span></span>

### <span data-ttu-id="21141-150">-CimSession</span><span class="sxs-lookup"><span data-stu-id="21141-150">-CimSession</span></span>

<span data-ttu-id="21141-151">이 cmdlet에 사용할 CIM 세션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-151">Specifies the CIM session to use for this cmdlet.</span></span> <span data-ttu-id="21141-152">Cim 세션을 포함 하는 변수 또는 CIM 세션을 만들거나 가져오는 명령 (예: 또는 cmdlet)을 입력 `New-CimSession` 합니다 `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="21141-152">Enter a variable that contains the CIM session or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="21141-153">자세한 내용은 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="21141-153">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, CimInstanceSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="21141-154">-ClassName</span><span class="sxs-lookup"><span data-stu-id="21141-154">-ClassName</span></span>

<span data-ttu-id="21141-155">CIM 인스턴스를 검색할 CIM 클래스의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-155">Specifies the name of the CIM class for which to retrieve the CIM instances.</span></span> <span data-ttu-id="21141-156">PowerShell은 클래스 이름 목록을 제공 하기 위해 로컬 WMI 서버에서 클래스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 클래스 목록을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21141-156">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21141-157">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="21141-157">-ComputerName</span></span>

<span data-ttu-id="21141-158">CIM 작업을 실행 하려는 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-158">Specifies computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="21141-159">FQDN (정규화 된 도메인 이름), NetBIOS 이름 또는 IP 주소를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21141-159">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="21141-160">이 매개 변수를 지정 하지 않으면 cmdlet은 COM (구성 요소 개체 모델)을 사용 하 여 로컬 컴퓨터에서 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-160">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="21141-161">이 매개 변수를 지정 하면 cmdlet이 WsMan 프로토콜을 사용 하 여 지정 된 컴퓨터에 대 한 임시 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="21141-161">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="21141-162">동일한 컴퓨터에서 여러 작업을 수행 하는 경우 더 나은 성능을 위해 CIM 세션을 사용 하 여 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-162">If multiple operations are being performed on the same computer, connect using a CIM session for better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, CimInstanceComputerSet, ResourceUriComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21141-163">-Filter</span><span class="sxs-lookup"><span data-stu-id="21141-163">-Filter</span></span>

<span data-ttu-id="21141-164">필터로 사용할 where 절을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-164">Specifies a where clause to use as a filter.</span></span> <span data-ttu-id="21141-165">**WQL** 또는 **CQL** 쿼리 언어에서 절을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-165">Specify the clause in either the **WQL** or the **CQL** query language.</span></span> <span data-ttu-id="21141-166">`WHERE`매개 변수 값에 키워드를 포함 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="21141-166">Do not include the `WHERE` keyword in the value of the parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21141-167">-InputObject</span><span class="sxs-lookup"><span data-stu-id="21141-167">-InputObject</span></span>

<span data-ttu-id="21141-168">입력으로 사용할 CIM 인스턴스 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-168">Specifies a CIM instance object to use as input.</span></span>

<span data-ttu-id="21141-169">이미 CIM 인스턴스 개체로 작업 하는 경우이 매개 변수를 사용 하 여 cim 서버에서 최신 스냅숏을 가져오기 위해 CIM 인스턴스 개체를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21141-169">If you are already working with a CIM instance object, you can use this parameter to pass the CIM instance object in order to get the latest snapshot from the CIM server.</span></span> <span data-ttu-id="21141-170">CIM 인스턴스 개체를 입력으로 전달 하는 경우 `Get-CimInstance` 열거 또는 쿼리 작업 대신 cim 가져오기 작업을 사용 하 여 서버에서 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-170">When you pass a CIM instance object as an input, `Get-CimInstance` returns the object from server using a get CIM operation, instead of an enumerate or query operation.</span></span> <span data-ttu-id="21141-171">CIM 가져오기 작업을 사용 하면 모든 인스턴스를 검색 한 다음 필터링 하는 것 보다 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="21141-171">Using a get CIM operation is more efficient than retrieving all instances and then filtering them.</span></span>

<span data-ttu-id="21141-172">CIM 클래스가 get 작업을 구현 하지 않는 경우 **InputObject** 매개 변수를 지정 하면 오류가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21141-172">If the CIM class does not implement the get operation, then specifying the **InputObject** parameter returns an error.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceSessionSet, CimInstanceComputerSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="21141-173">-KeyOnly</span><span class="sxs-lookup"><span data-stu-id="21141-173">-KeyOnly</span></span>

<span data-ttu-id="21141-174">키 속성이 채워진 개체만 반환 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="21141-174">Indicates that only objects with key properties populated are returned.</span></span> <span data-ttu-id="21141-175">**Keyonly** 매개 변수를 지정 하면 네트워크를 통해 전송 되는 데이터의 양이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="21141-175">Specifying the **KeyOnly** parameter reduces the amount of data transferred over the network.</span></span>

<span data-ttu-id="21141-176">**Keyonly** 매개 변수를 사용 하 여 또는 cmdlet과 같은 다른 작업에 사용할 수 있는 개체의 작은 부분만 반환 합니다 `Set-CimInstance` `Get-CimAssociatedInstance` .</span><span class="sxs-lookup"><span data-stu-id="21141-176">Use the **KeyOnly** parameter to return only a small portion of the object, which can be used for other operations, such as the `Set-CimInstance` or `Get-CimAssociatedInstance` cmdlets.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21141-177">-Namespace</span><span class="sxs-lookup"><span data-stu-id="21141-177">-Namespace</span></span>

<span data-ttu-id="21141-178">CIM 클래스의 네임 스페이스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-178">Specifies the namespace of CIM class.</span></span>

<span data-ttu-id="21141-179">기본 네임 스페이스는 **root/cimv2** 입니다.</span><span class="sxs-lookup"><span data-stu-id="21141-179">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="21141-180">PowerShell에서 네임 스페이스 목록을 제공 하기 위해 로컬 WMI 서버에서 네임 스페이스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 네임 스페이스 목록을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21141-180">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21141-181">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="21141-181">-OperationTimeoutSec</span></span>

<span data-ttu-id="21141-182">Cmdlet이 컴퓨터의 응답을 기다리는 시간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-182">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="21141-183">기본적으로이 매개 변수의 값은 0 이며이는 cmdlet이 서버에 대 한 기본 시간 제한 값을 사용 함을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-183">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="21141-184">**Operationtimeoutsec** 매개 변수가 강력한 연결 다시 시도 시간 제한 3 분 보다 작은 값으로 설정 된 경우, 서버에서 작업을 다시 연결할 수 있기 때문에 **operationtimeoutsec** 매개 변수의 값 보다 마지막으로 네트워크 오류가 복구 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21141-184">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21141-185">-속성</span><span class="sxs-lookup"><span data-stu-id="21141-185">-Property</span></span>

<span data-ttu-id="21141-186">검색할 인스턴스 속성의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-186">Specifies a set of instance properties to retrieve.</span></span> <span data-ttu-id="21141-187">반환 되는 개체의 크기를 메모리 또는 네트워크를 통해 줄여야 할 때이 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-187">Use this parameter when you need to reduce the size of the object returned, either in memory or over the network.</span></span> <span data-ttu-id="21141-188">반환 된 개체에는 **속성** 매개 변수를 사용 하 여 목록에 나열 되지 않은 경우에도 키 속성도 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21141-188">The object returned also contains the key properties even if you have not listed them using the **Property** parameter.</span></span> <span data-ttu-id="21141-189">클래스의 다른 속성이 있지만 채워지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21141-189">Other properties of the class are present but they are not populated.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases: SelectProperties

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21141-190">-Query</span><span class="sxs-lookup"><span data-stu-id="21141-190">-Query</span></span>

<span data-ttu-id="21141-191">CIM 서버에서 실행할 쿼리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-191">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="21141-192">지정 된 값에 큰따옴표 `"` , 작은따옴표 또는 백슬래시가 포함 된 경우 `'` `\` 백슬래시 문자를 접두사로 사용 하 여 해당 문자를 이스케이프 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-192">If the value specified contains double quotes `"`, single quotes `'`, or a backslash `\`, you must escape those characters by prefixing them with the backslash character.</span></span> <span data-ttu-id="21141-193">지정 된 값이 WQL **LIKE** 연산자를 사용 하는 경우 대괄호 ( `[]` 백분율 `%` , 밑줄 `_` 또는 여는 대괄호)로 묶어 다음 문자를 이스케이프 해야 `[` 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-193">If the value specified uses the WQL **LIKE** operator, then you must escape the following characters by enclosing them in square brackets `[]`: percent `%`, underscore `_`, or opening square bracket `[`.</span></span>

<span data-ttu-id="21141-194">메타 데이터 쿼리를 사용 하 여 클래스 또는 이벤트 쿼리 목록을 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21141-194">You cannot use a metadata query to retrieve a list of classes or an event query.</span></span> <span data-ttu-id="21141-195">클래스 목록을 검색 하려면 cmdlet을 사용 `Get-CimClass` 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-195">To retrieve a list of classes, use the `Get-CimClass` cmdlet.</span></span> <span data-ttu-id="21141-196">이벤트 쿼리를 검색 하려면 cmdlet을 사용 `Register-CimIndicationEvent` 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-196">To retrieve an event query, use the `Register-CimIndicationEvent` cmdlet.</span></span>

<span data-ttu-id="21141-197">**Querydialect** 매개 변수를 사용 하 여 쿼리 언어를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21141-197">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21141-198">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="21141-198">-QueryDialect</span></span>

<span data-ttu-id="21141-199">쿼리 매개 변수에 사용 되는 쿼리 언어를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-199">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="21141-200">이 매개 변수에 허용 되는 값은 **WQL** 또는 **CQL** 입니다.</span><span class="sxs-lookup"><span data-stu-id="21141-200">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span> <span data-ttu-id="21141-201">기본값은 **WQL** 입니다.</span><span class="sxs-lookup"><span data-stu-id="21141-201">The default value is **WQL**.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QuerySessionSet, ClassNameSessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21141-202">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="21141-202">-ResourceUri</span></span>

<span data-ttu-id="21141-203">리소스 클래스 또는 인스턴스의 리소스 URI (uniform resource identifier)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-203">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="21141-204">URI는 컴퓨터에서 특정 유형의 리소스(예: 디스크 또는 프로세스)를 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="21141-204">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="21141-205">URI는 접두사와 리소스 경로로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="21141-205">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="21141-206">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="21141-206">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="21141-207">기본적으로이 매개 변수를 지정 하지 않으면 DMTF 표준 리소스 URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 가 사용 되 고 클래스 이름이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21141-207">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="21141-208">**ResourceURI** 는 wsman 프로토콜을 사용 하 여 만든 cim 세션에만 사용할 수 있으며, **ComputerName** 매개 변수를 지정 하는 경우에만 wsman을 사용 하 여 cim 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21141-208">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="21141-209">**ComputerName** 매개 변수를 지정 하지 않고이 매개 변수를 지정 하거나 dcom 프로토콜을 사용 하 여 만든 CIM 세션을 지정 하는 경우 Dcom 프로토콜이 **ResourceURI** 매개 변수를 지원 하지 않으므로 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-209">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="21141-210">**ResourceUri** 매개 변수와 **필터** 매개 변수를 모두 지정 하면 **필터** 매개 변수가 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21141-210">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet, QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21141-211">-단순</span><span class="sxs-lookup"><span data-stu-id="21141-211">-Shallow</span></span>

<span data-ttu-id="21141-212">자식 클래스의 인스턴스를 포함 하지 않고 클래스 인스턴스가 반환 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="21141-212">Indicates that the instances of a class are returned without including the instances of any child classes.</span></span> <span data-ttu-id="21141-213">기본적으로 cmdlet은 클래스 및 해당 자식 클래스의 인스턴스를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-213">By default, the cmdlet returns the instances of a class and its child classes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21141-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="21141-214">CommonParameters</span></span>

<span data-ttu-id="21141-215">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="21141-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="21141-216">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21141-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="21141-217">입력</span><span class="sxs-lookup"><span data-stu-id="21141-217">INPUTS</span></span>

### <span data-ttu-id="21141-218">CIM 인스턴스</span><span class="sxs-lookup"><span data-stu-id="21141-218">CIM Instance</span></span>

<span data-ttu-id="21141-219">이 cmdlet은 InputObject 매개 변수를 사용 하 여 지정 된 입력 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-219">This cmdlet accepts an input objects specified with the InputObject parameter.</span></span>

## <span data-ttu-id="21141-220">출력</span><span class="sxs-lookup"><span data-stu-id="21141-220">OUTPUTS</span></span>

### <span data-ttu-id="21141-221">CIM 인스턴스</span><span class="sxs-lookup"><span data-stu-id="21141-221">CIM Instance</span></span>

<span data-ttu-id="21141-222">이 cmdlet은 cim 서버에서 CIM 인스턴스의 스냅숏을 나타내는 CIM 인스턴스 개체를 하나 이상 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="21141-222">This cmdlet returns one or more CIM instance objects representing a snapshot of the CIM instances on the CIM server.</span></span>

## <span data-ttu-id="21141-223">참고</span><span class="sxs-lookup"><span data-stu-id="21141-223">NOTES</span></span>

## <span data-ttu-id="21141-224">관련 링크</span><span class="sxs-lookup"><span data-stu-id="21141-224">RELATED LINKS</span></span>

[<span data-ttu-id="21141-225">Format-Table</span><span class="sxs-lookup"><span data-stu-id="21141-225">Format-Table</span></span>](../microsoft.powershell.utility/format-table.md)

[<span data-ttu-id="21141-226">Get-CimAssociatedInstance</span><span class="sxs-lookup"><span data-stu-id="21141-226">Get-CimAssociatedInstance</span></span>](Get-CimAssociatedInstance.md)

[<span data-ttu-id="21141-227">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="21141-227">Get-CimClass</span></span>](Get-CimClass.md)

[<span data-ttu-id="21141-228">Invoke-CimMethod</span><span class="sxs-lookup"><span data-stu-id="21141-228">Invoke-CimMethod</span></span>](invoke-cimmethod.md)

[<span data-ttu-id="21141-229">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="21141-229">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="21141-230">Register-CimIndicationEvent</span><span class="sxs-lookup"><span data-stu-id="21141-230">Register-CimIndicationEvent</span></span>](Register-CimIndicationEvent.md)

[<span data-ttu-id="21141-231">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="21141-231">Remove-CimInstance</span></span>](remove-ciminstance.md)

[<span data-ttu-id="21141-232">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="21141-232">Set-CimInstance</span></span>](Set-CimInstance.md)

