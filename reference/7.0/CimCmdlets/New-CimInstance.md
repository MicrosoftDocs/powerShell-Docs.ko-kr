---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-ciminstance?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimInstance
ms.openlocfilehash: a2374e7bcd9399f2699d186537b8f674fd6c899b
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218529"
---
# <span data-ttu-id="92c07-103">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="92c07-103">New-CimInstance</span></span>

## <span data-ttu-id="92c07-104">개요</span><span class="sxs-lookup"><span data-stu-id="92c07-104">SYNOPSIS</span></span>
<span data-ttu-id="92c07-105">CIM 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-105">Creates a CIM instance.</span></span>

## <span data-ttu-id="92c07-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="92c07-106">SYNTAX</span></span>

### <span data-ttu-id="92c07-107">ClassNameComputerSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="92c07-107">ClassNameComputerSet (Default)</span></span>

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="92c07-108">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="92c07-108">ClassNameSessionSet</span></span>

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="92c07-109">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="92c07-109">ResourceUriSessionSet</span></span>

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="92c07-110">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="92c07-110">ResourceUriComputerSet</span></span>

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="92c07-111">CimClassSessionSet</span><span class="sxs-lookup"><span data-stu-id="92c07-111">CimClassSessionSet</span></span>

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="92c07-112">CimClassComputerSet</span><span class="sxs-lookup"><span data-stu-id="92c07-112">CimClassComputerSet</span></span>

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="92c07-113">설명</span><span class="sxs-lookup"><span data-stu-id="92c07-113">DESCRIPTION</span></span>

<span data-ttu-id="92c07-114">`New-CimInstance`Cmdlet은 로컬 컴퓨터 또는 원격 컴퓨터의 클래스 정의를 기반으로 하는 CIM 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-114">The `New-CimInstance` cmdlet creates an instance of a CIM class based on the class definition on either the local computer or a remote computer.</span></span> <span data-ttu-id="92c07-115">기본적으로 cmdlet은 `New-CimInstance` 로컬 컴퓨터에 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-115">By default, the `New-CimInstance` cmdlet creates an instance on the local computer.</span></span>

## <span data-ttu-id="92c07-116">예제</span><span class="sxs-lookup"><span data-stu-id="92c07-116">EXAMPLES</span></span>

### <span data-ttu-id="92c07-117">예제 1: CIM 클래스의 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="92c07-117">Example 1: Create an instance of a CIM class</span></span>

<span data-ttu-id="92c07-118">이 예제에서는 컴퓨터의 root/cimv2 네임 스페이스에 win32_environment 라는 CIM 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-118">This example creates an instance of a CIM Class named win32_environment in the root/cimv2 namespace on the computer.</span></span>

```powershell
New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";VariableValue="testvalue";UserName="domain\user"}
```

<span data-ttu-id="92c07-119">클래스가 없거나 속성이 올바르지 않거나 서버에서 호출을 거부 하는 경우 클라이언트 쪽 유효성 검사가 수행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-119">No client side validation is performed if the class does not exist, the properties are wrong, or if the server rejects the call.</span></span> <span data-ttu-id="92c07-120">인스턴스가 성공적으로 만들어지면 cmdlet은 새로 만든 인스턴스를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-120">If the instance is created successfully, the cmdlet outputs the newly created instance.</span></span>

### <span data-ttu-id="92c07-121">예제 2: 클래스 스키마를 사용 하 여 CIM 클래스의 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="92c07-121">Example 2: Create an instance of a CIM class using a class schema</span></span>

<span data-ttu-id="92c07-122">이 예제에서는 CIM 클래스 개체를 검색 하 여 라는 변수에 저장 `$class` 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-122">This example retrieves a CIM class object and stores it in a variable named `$class`.</span></span> <span data-ttu-id="92c07-123">그런 다음 변수의 내용이 cmdlet에 전달 됩니다 `New-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="92c07-123">The contents of the variable are then passed to the `New-CimInstance` cmdlet.</span></span>

```powershell
$class = Get-CimClass -ClassName Win32_Environment
New-CimInstance -CimClass $class -Property @{Name="testvar";VariableValue="testvalue";UserName="Contoso\User1"}
```

### <span data-ttu-id="92c07-124">예 3: 클라이언트에서 동적 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="92c07-124">Example 3: Create a dynamic instance on the client</span></span>

<span data-ttu-id="92c07-125">이 예제에서는 서버에서 인스턴스를 가져오지 않고 클라이언트 컴퓨터에 **Win32_Process** 라는 CIM 클래스의 동적 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-125">This example creates a dynamic instance of a CIM class named **Win32_Process** on the client computer without getting the instance from the server.</span></span> <span data-ttu-id="92c07-126">새 인스턴스는 변수에 저장 됩니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="92c07-126">The new instance is stored in the variable `$a`.</span></span> <span data-ttu-id="92c07-127">이 키가 있는 인스턴스가 서버에 있는 경우이 동적 인스턴스를 사용 하 여 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-127">This dynamic instance can be used to perform operations if the instance with this key exists on the server.</span></span>

```powershell
$a = New-CimInstance -ClassName Win32_Process -Property @{Handle=0} -Key Handle -ClientOnly
Get-CimInstance -CimInstance $a
Invoke-CimMethod -CimInstance $a -MethodName GetOwner
```

```Output
ProcessId Name                HandleCount WorkingSetSize VirtualSize
--------- ----                ----------- -------------- -----------
0         System Idle Process 0           8192           8192

Domain         :
ReturnValue    : 2
User           :
PSComputerName :
```

<span data-ttu-id="92c07-128">`Get-CimInstance`그런 다음 cmdlet은 특정 단일 인스턴스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-128">The `Get-CimInstance` cmdlet then retrieves a particular single instance.</span></span> <span data-ttu-id="92c07-129">`Invoke-CimMethod`Cmdlet은 검색 된 인스턴스의 **getowner** 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-129">The `Invoke-CimMethod` cmdlet calls the **GetOwner** method on the retrieved instance.</span></span>

### <span data-ttu-id="92c07-130">예제 4: 특정 네임 스페이스의 CIM 클래스에 대 한 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="92c07-130">Example 4: Create an instance for a CIM class of a specific namespace</span></span>

<span data-ttu-id="92c07-131">이 예제에서는 네임 스페이스 **루트/어딘가에** 있는 **MSFT_Something** 라는 CIM 클래스의 인스턴스를 가져와 라는 변수에 저장 `$class` 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-131">This example gets an instance of a CIM class named **MSFT_Something** in the namespace **root/somewhere** and stores it in a variable named `$class`.</span></span> <span data-ttu-id="92c07-132">변수는 `New-CimInstance` 새 CIM 인스턴스를 만들고 새 인스턴스에서 클라이언트 쪽 유효성 검사를 수행 하기 위해 cmdlet에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-132">The variable is passed to the `New-CimInstance` cmdlet to create a new CIM instance and perform client side validations on the new instance.</span></span>

```powershell
$class = Get-CimClass -ClassName MSFT_Something -Namespace root/somewhere
New-CimInstance -CimClass $class -Property @{"Prop1"=1;"Prop2"="value"} -ClientOnly
```

<span data-ttu-id="92c07-133">이 예에서는 **ClassName** 매개 변수 대신 **CimClass** 매개 변수를 사용 하 여 **Prop1** 및 **Prop2** 이 실제로 존재 하 고 키가 올바르게 표시 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-133">In this example, using the **CimClass** parameter instead of the **ClassName** parameter validates that **Prop1** and **Prop2** actually exist and that the keys are marked correctly.</span></span>

<span data-ttu-id="92c07-134">**ComputerName** 또는 **CimSession** 매개 변수는 **clientonly** 매개 변수와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-134">You cannot use the **ComputerName** or **CimSession** parameter with the **ClientOnly** parameter.</span></span>

## <span data-ttu-id="92c07-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="92c07-135">PARAMETERS</span></span>

### <span data-ttu-id="92c07-136">-CimClass</span><span class="sxs-lookup"><span data-stu-id="92c07-136">-CimClass</span></span>

<span data-ttu-id="92c07-137">인스턴스의 유형을 나타내는 CIM 클래스 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-137">Specifies a CIM class object that represents the type of the instance.</span></span> <span data-ttu-id="92c07-138">Cmdlet을 사용 `Get-CimClass` 하 여 컴퓨터에서 클래스 선언을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-138">Use the `Get-CimClass` cmdlet to retrieve the class declaration from a computer.</span></span> <span data-ttu-id="92c07-139">이 매개 변수를 사용 하면 클라이언트 쪽 스키마 유효성 검사가 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-139">Using this parameter results in better client side schema validations.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassSessionSet, CimClassComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="92c07-140">-CimSession</span><span class="sxs-lookup"><span data-stu-id="92c07-140">-CimSession</span></span>

<span data-ttu-id="92c07-141">지정 된 CIM 세션을 사용 하 여 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-141">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="92c07-142">CIM 세션을 포함 하는 변수 또는 CIM 세션을 만들거나 가져오는 명령 (예: 또는 cmdlet)을 입력 합니다 `New-CimSession` `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="92c07-142">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="92c07-143">자세한 내용은 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="92c07-143">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ClassNameSessionSet, ResourceUriSessionSet, CimClassSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="92c07-144">-ClassName</span><span class="sxs-lookup"><span data-stu-id="92c07-144">-ClassName</span></span>

<span data-ttu-id="92c07-145">작업에서 인스턴스를 만드는 CIM 클래스의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-145">Specifies the name of the CIM class of which the operation creates an instance.</span></span> <span data-ttu-id="92c07-146">참고: PowerShell은 클래스 이름 목록을 제공 하기 위해 로컬 WMI 서버에서 클래스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 클래스 목록을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-146">NOTE: You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

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

### <span data-ttu-id="92c07-147">-ClientOnly</span><span class="sxs-lookup"><span data-stu-id="92c07-147">-ClientOnly</span></span>

<span data-ttu-id="92c07-148">인스턴스가 CIM 서버로 이동 하지 않고 PowerShell 에서만 생성 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-148">Indicates that the instance is only created in PowerShell without going to the CIM server.</span></span> <span data-ttu-id="92c07-149">이 매개 변수를 사용 하 여 후속 PowerShell 작업에서 사용할 메모리 내 CIM 인스턴스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-149">You can use this parameter to create an in-memory CIM instance for use in subsequent PowerShell operations.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, CimClassSessionSet, CimClassComputerSet
Aliases: Local

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="92c07-150">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="92c07-150">-ComputerName</span></span>

<span data-ttu-id="92c07-151">CIM 작업을 실행 하려는 컴퓨터의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-151">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="92c07-152">FQDN (정규화 된 도메인 이름), NetBIOS 이름 또는 IP 주소를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-152">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="92c07-153">이 매개 변수를 지정 하면 cmdlet이 WSMan 프로토콜을 사용 하 여 지정 된 컴퓨터에 대 한 임시 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-153">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WSMan protocol.</span></span>

<span data-ttu-id="92c07-154">이 매개 변수를 지정 하지 않으면 cmdlet은 COM (구성 요소 개체 모델)을 사용 하 여 로컬 컴퓨터에서 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-154">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="92c07-155">동일한 컴퓨터에서 여러 작업을 수행 하는 경우 CIM 세션을 사용 하 여 연결 하면 성능이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-155">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="92c07-156">-키</span><span class="sxs-lookup"><span data-stu-id="92c07-156">-Key</span></span>

<span data-ttu-id="92c07-157">키로 사용 되는 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-157">Specifies the properties that are used as keys.</span></span> <span data-ttu-id="92c07-158">**키** 가 지정 된 경우에는 **CimSession** 및 **ComputerName** 을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-158">**CimSession** and **ComputerName** cannot be used when **Key** is specified.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="92c07-159">-Namespace</span><span class="sxs-lookup"><span data-stu-id="92c07-159">-Namespace</span></span>

<span data-ttu-id="92c07-160">새 인스턴스에 대 한 클래스의 네임 스페이스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-160">Specifies the namespace of the class for the new instance.</span></span> <span data-ttu-id="92c07-161">기본 네임 스페이스는 **root/cimv2** 입니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-161">The default namespace is **root/cimv2**.</span></span>
<span data-ttu-id="92c07-162">PowerShell에서 네임 스페이스 목록을 제공 하기 위해 로컬 WMI 서버에서 네임 스페이스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 네임 스페이스 목록을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-162">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="92c07-163">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="92c07-163">-OperationTimeoutSec</span></span>

<span data-ttu-id="92c07-164">Cmdlet이 CIM 서버의 응답을 기다리는 시간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-164">Specifies the amount of time that the cmdlet waits for a response from the CIM server.</span></span> <span data-ttu-id="92c07-165">기본적으로이 매개 변수의 값은 0 이며이는 cmdlet이 서버에 대 한 기본 시간 제한 값을 사용 함을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-165">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span> <span data-ttu-id="92c07-166">**Operationtimeoutsec** 매개 변수가 강력한 연결 다시 시도 시간 제한 3 분 보다 작은 값으로 설정 된 경우, 서버에서 작업을 다시 연결할 수 있기 때문에 **operationtimeoutsec** 매개 변수의 값 보다 마지막으로 네트워크 오류가 복구 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-166">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="92c07-167">-속성</span><span class="sxs-lookup"><span data-stu-id="92c07-167">-Property</span></span>

<span data-ttu-id="92c07-168">해시 테이블 (이름-값 쌍)을 사용 하 여 CIM 인스턴스의 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-168">Specifies the properties of the CIM instance using a hash table (name-value pairs).</span></span>

<span data-ttu-id="92c07-169">**CimClass** 매개 변수를 지정 하면 `New-CimInstance` cmdlet이 클라이언트에서 속성 유효성 검사를 수행 하 여 지정 된 속성이 서버의 클래스 선언과 일치 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-169">If you specify the **CimClass** parameter, then the `New-CimInstance` cmdlet performs a property validation on the client to make sure that the properties specified are consistent with the class declaration on the server.</span></span> <span data-ttu-id="92c07-170">**CimClass** 매개 변수를 지정 하지 않으면 서버에서 속성 유효성 검사가 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-170">If the **CimClass** parameter is not specified, then the property validation is done on the server.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases: Arguments

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="92c07-171">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="92c07-171">-ResourceUri</span></span>

<span data-ttu-id="92c07-172">리소스 클래스 또는 인스턴스의 리소스 URI (uniform resource identifier)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-172">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="92c07-173">URI는 컴퓨터에서 특정 유형의 리소스(예: 디스크 또는 프로세스)를 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-173">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="92c07-174">URI는 접두사와 리소스 경로로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-174">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="92c07-175">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="92c07-175">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="92c07-176">기본적으로이 매개 변수를 지정 하지 않으면 DMTF 표준 리소스 URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 가 사용 되 고 클래스 이름이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-176">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="92c07-177">**ResourceURI** 는 wsman 프로토콜을 사용 하 여 만든 cim 세션에만 사용할 수 있으며, **ComputerName** 매개 변수를 지정 하는 경우에만 wsman을 사용 하 여 cim 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-177">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="92c07-178">**ComputerName** 매개 변수를 지정 하지 않고이 매개 변수를 지정 하거나 dcom 프로토콜을 사용 하 여 만든 CIM 세션을 지정 하는 경우 Dcom 프로토콜이 **ResourceURI** 매개 변수를 지원 하지 않으므로 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-178">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="92c07-179">**ResourceUri** 매개 변수와 **필터** 매개 변수를 모두 지정 하면 **필터** 매개 변수가 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-179">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="92c07-180">-Confirm</span><span class="sxs-lookup"><span data-stu-id="92c07-180">-Confirm</span></span>

<span data-ttu-id="92c07-181">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-181">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="92c07-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="92c07-182">-WhatIf</span></span>

<span data-ttu-id="92c07-183">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-183">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="92c07-184">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-184">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="92c07-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="92c07-185">CommonParameters</span></span>

<span data-ttu-id="92c07-186">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="92c07-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="92c07-187">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92c07-187">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="92c07-188">입력</span><span class="sxs-lookup"><span data-stu-id="92c07-188">INPUTS</span></span>

### <span data-ttu-id="92c07-189">없음</span><span class="sxs-lookup"><span data-stu-id="92c07-189">None</span></span>

<span data-ttu-id="92c07-190">이 cmdlet은 입력 개체를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-190">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="92c07-191">출력</span><span class="sxs-lookup"><span data-stu-id="92c07-191">OUTPUTS</span></span>

### <span data-ttu-id="92c07-192">System.Object</span><span class="sxs-lookup"><span data-stu-id="92c07-192">System.Object</span></span>

<span data-ttu-id="92c07-193">이 cmdlet은 CIM 인스턴스 정보를 포함 하는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="92c07-193">This cmdlet returns an object that contains the CIM instance information.</span></span>

## <span data-ttu-id="92c07-194">참고</span><span class="sxs-lookup"><span data-stu-id="92c07-194">NOTES</span></span>

## <span data-ttu-id="92c07-195">관련 링크</span><span class="sxs-lookup"><span data-stu-id="92c07-195">RELATED LINKS</span></span>

[<span data-ttu-id="92c07-196">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="92c07-196">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="92c07-197">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="92c07-197">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="92c07-198">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="92c07-198">Remove-CimInstance</span></span>](remove-ciminstance.md)

[<span data-ttu-id="92c07-199">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="92c07-199">Set-CimInstance</span></span>](Set-CimInstance.md)
