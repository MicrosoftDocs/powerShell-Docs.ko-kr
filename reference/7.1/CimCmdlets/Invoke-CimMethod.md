---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 01/21/2020
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/invoke-cimmethod?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-CimMethod
ms.openlocfilehash: 691ba3396fee5a32e81ade5979cb5a5ac4bd88eb
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218818"
---
# <span data-ttu-id="3db29-103">Invoke-CimMethod</span><span class="sxs-lookup"><span data-stu-id="3db29-103">Invoke-CimMethod</span></span>

## <span data-ttu-id="3db29-104">개요</span><span class="sxs-lookup"><span data-stu-id="3db29-104">SYNOPSIS</span></span>
<span data-ttu-id="3db29-105">CIM 클래스의 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-105">Invokes a method of a CIM class.</span></span>

## <span data-ttu-id="3db29-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3db29-106">SYNTAX</span></span>

### <span data-ttu-id="3db29-107">ClassNameComputerSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="3db29-107">ClassNameComputerSet (Default)</span></span>

```
Invoke-CimMethod [-ClassName] <String> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="3db29-108">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="3db29-108">ClassNameSessionSet</span></span>

```
Invoke-CimMethod [-ClassName] <String> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="3db29-109">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="3db29-109">ResourceUriComputerSet</span></span>

```
Invoke-CimMethod -ResourceUri <Uri> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="3db29-110">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="3db29-110">CimInstanceSessionSet</span></span>

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3db29-111">CimInstanceComputerSet</span><span class="sxs-lookup"><span data-stu-id="3db29-111">CimInstanceComputerSet</span></span>

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3db29-112">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="3db29-112">ResourceUriSessionSet</span></span>

```
Invoke-CimMethod -ResourceUri <Uri> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="3db29-113">CimClassComputerSet</span><span class="sxs-lookup"><span data-stu-id="3db29-113">CimClassComputerSet</span></span>

```
Invoke-CimMethod [-CimClass] <CimClass> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3db29-114">CimClassSessionSet</span><span class="sxs-lookup"><span data-stu-id="3db29-114">CimClassSessionSet</span></span>

```
Invoke-CimMethod [-CimClass] <CimClass> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3db29-115">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="3db29-115">QueryComputerSet</span></span>

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3db29-116">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="3db29-116">QuerySessionSet</span></span>

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3db29-117">설명</span><span class="sxs-lookup"><span data-stu-id="3db29-117">DESCRIPTION</span></span>

<span data-ttu-id="3db29-118">`Invoke-CimMethod`Cmdlet은 **Arguments** 매개 변수로 지정 된 이름-값 쌍을 사용 하 여 CIM 클래스 또는 cim 인스턴스의 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-118">The `Invoke-CimMethod` cmdlet invokes a method of a CIM class or CIM instance using the name-value pairs specified by the **Arguments** parameter.</span></span>

<span data-ttu-id="3db29-119">**InputObject** 매개 변수를 지정 하지 않으면 cmdlet은 다음 방법 중 하나로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-119">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="3db29-120">**ComputerName** 매개 변수와 **CimSession** 매개 변수를 모두 지정 하지 않으면이 Cmdlet은 COM (구성 요소 개체 모델) 세션을 사용 하 여 WMI (로컬 WMI(Windows Management Instrumentation))에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-120">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="3db29-121">**Computername** 매개 변수 또는 **CimSession** 매개 변수를 지정 하는 경우이 cmdlet은 **computername** 매개 변수 또는 **CimSession** 매개 변수로 지정 된 CIM 서버에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-121">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="3db29-122">**InputObject** 매개 변수를 지정 하는 경우 cmdlet은 다음 방법 중 하나로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-122">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="3db29-123">**ComputerName** 매개 변수와 **CimSession** 매개 변수를 모두 지정 하지 않으면이 cmdlet은 입력 개체의 컴퓨터 이름과 CIM 세션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-123">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="3db29-124">**ComputerName** 매개 변수 또는 **CimSession** 매개 변수 중 하나가 지정 된 경우이 cmdlet은 **CimSession** 매개 변수 값 또는 **ComputerName** 매개 변수 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-124">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the **CimSession** parameter value or **ComputerName** parameter value.</span></span> <span data-ttu-id="3db29-125">이는 일반적인 시나리오가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-125">This is not a common scenario.</span></span>

## <span data-ttu-id="3db29-126">예제</span><span class="sxs-lookup"><span data-stu-id="3db29-126">EXAMPLES</span></span>

### <span data-ttu-id="3db29-127">예제 1: 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="3db29-127">Example 1: Invoke a method</span></span>

<span data-ttu-id="3db29-128">이 예제에서는 **Win32_Process** 클래스의 **Terminate** 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-128">This example invokes the **Terminate** method of the **Win32_Process** class.</span></span>

```powershell
Invoke-CimMethod -Query 'select * from Win32_Process where name like "notepad%"' -MethodName "Terminate"
```

### <span data-ttu-id="3db29-129">예제 2: CIM 인스턴스 개체를 사용 하 여 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="3db29-129">Example 2: Invoke a method using CIM instance object</span></span>

<span data-ttu-id="3db29-130">이 예에서는 CIM 인스턴스 개체를 검색 하 여 `$x` cmdlet을 사용 하 여 라는 변수에 저장 합니다 `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="3db29-130">This example retrieves the CIM instance object and stores it in a variable named `$x` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="3db29-131">그러면 변수의 내용이 cmdlet에 대 한 **InputObject** 로 사용 됩니다 `Invoke-CimMethod` .</span><span class="sxs-lookup"><span data-stu-id="3db29-131">The contents of the variable are then used as the **InputObject** for the `Invoke-CimMethod` cmdlet.</span></span> <span data-ttu-id="3db29-132">**Getowner** 메서드가 **ciminstance 개체로** 에 대해 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-132">The **GetOwner** method is invoked for the **CimInstance**.</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Process where name like "notepad%"'
Invoke-CimMethod -InputObject $x -MethodName GetOwner
```

### <span data-ttu-id="3db29-133">예제 3: 인수를 사용 하 여 정적 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="3db29-133">Example 3: Invoke a static method using arguments</span></span>

<span data-ttu-id="3db29-134">이 예제에서는 **Arguments** 매개 변수를 사용 하 여 라는 **Create** 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-134">This example invokes the **Create** method named using the **Arguments** parameter.</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Process -MethodName "Create" -Arguments @{
  CommandLine = 'notepad.exe'; CurrentDirectory = "C:\windows\system32"
}
```

### <span data-ttu-id="3db29-135">예제 4: 클라이언트 쪽 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="3db29-135">Example 4: Client-side validation</span></span>

<span data-ttu-id="3db29-136">이 예제에서는 **CimClass** 개체를에 전달 하 여 **xyz** 메서드에 대 한 클라이언트 쪽 유효성 검사를 수행 `Invoke-CimMethod` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-136">This example performs client-side validation for the **xyz** method by passing a **CimClass** object to `Invoke-CimMethod`.</span></span>

```powershell
$c = Get-CimClass -ClassName Win32_Process
Invoke-CimMethod -CimClass $c -MethodName "xyz" -Arguments @{ CommandLine = 'notepad.exe' }
```

## <span data-ttu-id="3db29-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3db29-137">PARAMETERS</span></span>

### <span data-ttu-id="3db29-138">-Arguments</span><span class="sxs-lookup"><span data-stu-id="3db29-138">-Arguments</span></span>

<span data-ttu-id="3db29-139">호출된 메서드에 전달할 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-139">Specifies the parameters to pass to the called method.</span></span> <span data-ttu-id="3db29-140">이 매개 변수에 대 한 값을 해시 테이블에 저장 된 이름-값 쌍으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-140">Specify the values for this parameter as name-value pairs, stored in a hash table.</span></span> <span data-ttu-id="3db29-141">입력 한 값의 순서는 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-141">The order of the values entered isn't important.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3db29-142">-CimClass</span><span class="sxs-lookup"><span data-stu-id="3db29-142">-CimClass</span></span>

<span data-ttu-id="3db29-143">서버의 CIM 클래스 정의를 나타내는 CIM 클래스 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-143">Specifies a CIM class object that represents a CIM class definition on the server.</span></span> <span data-ttu-id="3db29-144">클래스의 정적 메서드를 호출할 때이 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-144">Use this parameter when invoking a static method of a class.</span></span>

<span data-ttu-id="3db29-145">Cmdlet을 사용 하 여 `Get-CimClass` 서버에서 클래스 정의를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-145">You can use the `Get-CimClass` cmdlet to retrieve a class definition from the server.</span></span>

<span data-ttu-id="3db29-146">이 매개 변수를 사용 하면 클라이언트 쪽 스키마 유효성 검사가 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-146">Using this parameter results in better client side schema validations.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassComputerSet, CimClassSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3db29-147">-CimSession</span><span class="sxs-lookup"><span data-stu-id="3db29-147">-CimSession</span></span>

<span data-ttu-id="3db29-148">지정 된 CIM 세션을 사용 하 여 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-148">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="3db29-149">CIM 세션을 포함 하는 변수 또는 CIM 세션을 만들거나 가져오는 명령 (예: 또는 cmdlet)을 입력 합니다 `New-CimSession` `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="3db29-149">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="3db29-150">자세한 내용은 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3db29-150">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ClassNameSessionSet, CimInstanceSessionSet, CimClassSessionSet, QuerySessionSet, ResourceUriSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3db29-151">-ClassName</span><span class="sxs-lookup"><span data-stu-id="3db29-151">-ClassName</span></span>

<span data-ttu-id="3db29-152">작업을 수행할 CIM 클래스의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-152">Specifies the name of the CIM class for which to perform the operation.</span></span> <span data-ttu-id="3db29-153">이 매개 변수는 정적 메서드에만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-153">This parameter is only used for static methods.</span></span> <span data-ttu-id="3db29-154">PowerShell은 클래스 이름 목록을 제공 하기 위해 로컬 WMI 서버에서 클래스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 클래스 목록을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-154">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases: Class

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3db29-155">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="3db29-155">-ComputerName</span></span>

<span data-ttu-id="3db29-156">CIM 작업을 실행 하려는 컴퓨터의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-156">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="3db29-157">FQDN (정규화 된 도메인 이름), NetBIOS 이름 또는 IP 주소를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-157">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="3db29-158">이 매개 변수를 사용 하는 경우 cmdlet은 WsMan 프로토콜을 사용 하 여 지정 된 컴퓨터에 대 한 임시 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-158">When using this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span> <span data-ttu-id="3db29-159">그렇지 않으면 cmdlet은 COM (구성 요소 개체 모델)을 사용 하 여 로컬 컴퓨터에서 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-159">Otherwise, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="3db29-160">동일한 컴퓨터에서 여러 작업을 수행 하는 경우 더 나은 성능을 위해 CIM 세션을 사용 하 여 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-160">Connect using a CIM session for better performance when multiple operations are being performed on the same computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet, CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3db29-161">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3db29-161">-InputObject</span></span>

<span data-ttu-id="3db29-162">메서드를 호출 하기 위한 입력으로 사용할 CIM 인스턴스 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-162">Specifies a CIM instance object to use as input to invoke a method.</span></span> <span data-ttu-id="3db29-163">이 매개 변수는 인스턴스 메서드를 호출 하는 데만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-163">This parameter can only be used to invoke instance methods.</span></span> <span data-ttu-id="3db29-164">클래스의 정적 메서드를 호출 하려면 **클래스** 매개 변수 또는 **CimClass** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-164">To invoke class static methods, use the **Class** parameter or the **CimClass** parameter.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3db29-165">-MethodName</span><span class="sxs-lookup"><span data-stu-id="3db29-165">-MethodName</span></span>

<span data-ttu-id="3db29-166">호출할 CIM 메서드의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-166">Specifies the name of the CIM method to invoke.</span></span> <span data-ttu-id="3db29-167">이 매개 변수는 필수이며 null이거나 비어 있을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-167">This parameter is mandatory and cannot be null or empty.</span></span> <span data-ttu-id="3db29-168">CIM 클래스의 정적 메서드를 호출 하려면 **ClassName** 또는 **CimClass** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-168">To invoke static method of a CIM class use the **ClassName** or the **CimClass** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Name

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3db29-169">-Namespace</span><span class="sxs-lookup"><span data-stu-id="3db29-169">-Namespace</span></span>

<span data-ttu-id="3db29-170">CIM 작업에 대 한 네임 스페이스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-170">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="3db29-171">기본 네임 스페이스는 **root/cimv2** 입니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-171">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="3db29-172">PowerShell에서 네임 스페이스 목록을 제공 하기 위해 로컬 WMI 서버에서 네임 스페이스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 네임 스페이스 목록을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-172">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriComputerSet, ResourceUriSessionSet, QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3db29-173">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="3db29-173">-OperationTimeoutSec</span></span>

<span data-ttu-id="3db29-174">Cmdlet이 컴퓨터의 응답을 기다리는 시간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-174">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="3db29-175">기본적으로이 값은 0입니다. 즉, cmdlet이 서버에 대 한 기본 시간 제한 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-175">By default, the value is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="3db29-176">**Operationtimeoutsec** 매개 변수가 기본 연결 다시 시도 시간 제한 3 분 보다 작은 값으로 설정 된 경우 **operationtimeoutsec** 매개 변수 값 보다 마지막으로 지난 네트워크 오류는 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-176">If the **OperationTimeoutSec** parameter is set to a value less than the default connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable.</span></span>

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

### <span data-ttu-id="3db29-177">-Query</span><span class="sxs-lookup"><span data-stu-id="3db29-177">-Query</span></span>

<span data-ttu-id="3db29-178">CIM 서버에서 실행할 쿼리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-178">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="3db29-179">쿼리 결과로 받은 인스턴스에서 메서드가 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-179">A method is invoked on the instances received as a result of the query.</span></span> <span data-ttu-id="3db29-180">**Querydialect** 매개 변수를 사용 하 여 쿼리 언어를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-180">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

<span data-ttu-id="3db29-181">지정 된 값에 큰따옴표 ( `"` ), 작은따옴표 () `'` 또는 백슬래시 ()가 포함 된 경우 `\` 백슬래시 () 문자를 접두사로 사용 하 여 해당 문자를 이스케이프 해야 합니다 `\` .</span><span class="sxs-lookup"><span data-stu-id="3db29-181">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="3db29-182">지정 된 값이 WQL LIKE 연산자를 사용 하는 경우 대괄호 ( `[]` ): 백분율 ( `%` ), 밑줄 ( `_` ) 또는 여는 대괄호 ()로 묶어 다음 문자를 이스케이프 해야 합니다 `[` .</span><span class="sxs-lookup"><span data-stu-id="3db29-182">If the value specified uses the WQL LIKE operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

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

### <span data-ttu-id="3db29-183">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="3db29-183">-QueryDialect</span></span>

<span data-ttu-id="3db29-184">쿼리 매개 변수에 사용 되는 쿼리 언어를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-184">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="3db29-185">이 매개 변수에 허용 되는 값은 **WQL** 또는 **CQL** 입니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-185">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span>

<span data-ttu-id="3db29-186">기본값은 **WQL** 입니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-186">The default value is **WQL**.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: WQL
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3db29-187">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="3db29-187">-ResourceUri</span></span>

<span data-ttu-id="3db29-188">리소스 클래스 또는 인스턴스의 리소스 URI (uniform resource identifier)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-188">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="3db29-189">URI는 컴퓨터에서 특정 유형의 리소스(예: 디스크 또는 프로세스)를 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-189">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="3db29-190">URI는 접두사와 리소스 경로로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-190">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="3db29-191">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="3db29-191">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="3db29-192">기본적으로이 매개 변수를 지정 하지 않으면 DMTF 표준 리소스 URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 가 사용 되 고 클래스 이름이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-192">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="3db29-193">**ResourceURI** 는 wsman 프로토콜을 사용 하 여 만든 cim 세션에만 사용할 수 있으며, **ComputerName** 매개 변수를 지정 하는 경우에만 wsman을 사용 하 여 cim 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-193">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span>

<span data-ttu-id="3db29-194">**ComputerName** 매개 변수를 지정 하지 않고이 매개 변수를 지정 하거나 DCOM 프로토콜을 사용 하 여 만든 CIM 세션을 지정 하면 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-194">When you specify this parameter without specifying the **ComputerName** parameter, or when you specify a CIM session created using DCOM protocol, you get an error.</span></span> <span data-ttu-id="3db29-195">DCOM 프로토콜은 **ResourceURI** 매개 변수를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-195">The DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="3db29-196">**ResourceUri** 매개 변수와 **필터** 매개 변수를 모두 지정 하면 **필터** 매개 변수가 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-196">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3db29-197">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3db29-197">-Confirm</span></span>

<span data-ttu-id="3db29-198">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-198">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3db29-199">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3db29-199">-WhatIf</span></span>

<span data-ttu-id="3db29-200">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-200">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="3db29-201">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-201">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="3db29-202">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3db29-202">CommonParameters</span></span>

<span data-ttu-id="3db29-203">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3db29-203">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3db29-204">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3db29-204">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3db29-205">입력</span><span class="sxs-lookup"><span data-stu-id="3db29-205">INPUTS</span></span>

### <span data-ttu-id="3db29-206">CIM 클래스</span><span class="sxs-lookup"><span data-stu-id="3db29-206">CIM class</span></span>

<span data-ttu-id="3db29-207">이 cmdlet은 CIM 클래스를 입력 개체로 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-207">This cmdlet accepts a CIM class as an input object.</span></span>

### <span data-ttu-id="3db29-208">CIM 인스턴스</span><span class="sxs-lookup"><span data-stu-id="3db29-208">CIM instance</span></span>

<span data-ttu-id="3db29-209">이 cmdlet은 CIM 인스턴스를 입력 개체로 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-209">This cmdlet accepts a CIM instance as an input object.</span></span>

## <span data-ttu-id="3db29-210">출력</span><span class="sxs-lookup"><span data-stu-id="3db29-210">OUTPUTS</span></span>

### <span data-ttu-id="3db29-211">PSCustomObject.</span><span class="sxs-lookup"><span data-stu-id="3db29-211">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="3db29-212">이 cmdlet은 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db29-212">This cmdlet returns an object.</span></span>

## <span data-ttu-id="3db29-213">참고</span><span class="sxs-lookup"><span data-stu-id="3db29-213">NOTES</span></span>

## <span data-ttu-id="3db29-214">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3db29-214">RELATED LINKS</span></span>

[<span data-ttu-id="3db29-215">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="3db29-215">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="3db29-216">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="3db29-216">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="3db29-217">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="3db29-217">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="3db29-218">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="3db29-218">New-CimSession</span></span>](New-CimSession.md)

