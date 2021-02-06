---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/set-ciminstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-CimInstance
ms.openlocfilehash: 041ef2d5b5541c250b98003099fe58018df155c2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600621"
---
# <span data-ttu-id="ca45f-102">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="ca45f-102">Set-CimInstance</span></span>

## <span data-ttu-id="ca45f-103">개요</span><span class="sxs-lookup"><span data-stu-id="ca45f-103">SYNOPSIS</span></span>
<span data-ttu-id="ca45f-104">Cim 클래스의 ModifyInstance 메서드를 호출 하 여 CIM 서버에서 CIM 인스턴스를 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-104">Modifies a CIM instance on a CIM server by calling the ModifyInstance method of the CIM class.</span></span>

## <span data-ttu-id="ca45f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ca45f-105">SYNTAX</span></span>

### <span data-ttu-id="ca45f-106">CimInstanceComputerSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="ca45f-106">CimInstanceComputerSet (Default)</span></span>

```
Set-CimInstance [-ComputerName <String[]>] [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="ca45f-107">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="ca45f-107">CimInstanceSessionSet</span></span>

```
Set-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="ca45f-108">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="ca45f-108">QuerySessionSet</span></span>

```
Set-CimInstance -CimSession <CimSession[]> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="ca45f-109">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="ca45f-109">QueryComputerSet</span></span>

```
Set-CimInstance [-ComputerName <String[]>] [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="ca45f-110">설명</span><span class="sxs-lookup"><span data-stu-id="ca45f-110">DESCRIPTION</span></span>

<span data-ttu-id="ca45f-111">이 cmdlet은 CIM 서버에서 CIM 인스턴스를 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-111">This cmdlet modifies a CIM instance on a CIM server.</span></span>

<span data-ttu-id="ca45f-112">**InputObject** 매개 변수를 지정 하지 않으면 cmdlet은 다음 방법 중 하나로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-112">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="ca45f-113">**ComputerName** 매개 변수와 **CimSession** 매개 변수를 모두 지정 하지 않으면이 Cmdlet은 COM (구성 요소 개체 모델) 세션을 사용 하 여 WMI (로컬 WMI(Windows Management Instrumentation))에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-113">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="ca45f-114">**Computername** 매개 변수 또는 **CimSession** 매개 변수를 지정 하는 경우이 cmdlet은 **computername** 매개 변수 또는 **CimSession** 매개 변수로 지정 된 CIM 서버에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-114">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="ca45f-115">**InputObject** 매개 변수를 지정 하는 경우 cmdlet은 다음 방법 중 하나로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-115">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="ca45f-116">**ComputerName** 매개 변수와 **CimSession** 매개 변수를 모두 지정 하지 않으면이 cmdlet은 입력 개체의 컴퓨터 이름과 CIM 세션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-116">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="ca45f-117">**ComputerName** 매개 변수 또는 **CimSession** 매개 변수 중 하나가 지정 된 경우이 cmdlet은 **CimSession** 매개 변수 값 또는 **ComputerName** 매개 변수 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-117">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the **CimSession** parameter value or **ComputerName** parameter value.</span></span> <span data-ttu-id="ca45f-118">이는 그다지 일반적이 지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-118">This is not very common.</span></span>

## <span data-ttu-id="ca45f-119">예제</span><span class="sxs-lookup"><span data-stu-id="ca45f-119">EXAMPLES</span></span>

### <span data-ttu-id="ca45f-120">예제 1: CIM 인스턴스 설정</span><span class="sxs-lookup"><span data-stu-id="ca45f-120">Example 1: Set the CIM instance</span></span>

<span data-ttu-id="ca45f-121">이 예에서는 **쿼리** 매개 변수를 사용 하 여 **VariableValue** 속성의 값을 **abcd** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-121">This example sets the value of the **VariableValue** property to **abcd** using the **Query** parameter.</span></span> <span data-ttu-id="ca45f-122">WQL (WMI(Windows Management Instrumentation) Query Language) 쿼리와 일치 하는 인스턴스를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-122">You can modify instances matching a Windows Management Instrumentation Query Language (WQL) query.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"}
```

### <span data-ttu-id="ca45f-123">예 2: 파이프라인을 사용 하 여 CIM 인스턴스 속성 설정</span><span class="sxs-lookup"><span data-stu-id="ca45f-123">Example 2: Set the CIM instance property using pipeline</span></span>

<span data-ttu-id="ca45f-124">이 예에서는 cmdlet을 사용 하 여 **쿼리** 매개 변수를 통해 필터링 된 CIM 인스턴스 개체를 검색 합니다 `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="ca45f-124">This example retrieves the CIM instance object filtered by the **Query** parameter using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="ca45f-125">`Set-CimInstance`Cmdlet은 **VariableValue** 속성의 값을 **abcd** 로 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-125">The `Set-CimInstance` cmdlet modifies the value of **VariableValue** property to **abcd**.</span></span>

```powershell
Get-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' |
  Set-CimInstance -Property @{VariableValue="abcd"}
```

### <span data-ttu-id="ca45f-126">예제 3: input 개체를 사용 하 여 CIM 인스턴스 속성 설정</span><span class="sxs-lookup"><span data-stu-id="ca45f-126">Example 3: Set the CIM instance property using input object</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where Name="testvar"'
Set-CimInstance -InputObject $x -Property @{VariableValue="somevalue"} -PassThru
```

<span data-ttu-id="ca45f-127">이 예에서는를 사용 하 여 변수에서 쿼리 매개 변수로 필터링 된 CIM 인스턴스 개체를 검색 한 `$x` `Get-CimInstance` 다음 변수의 내용을 cmdlet에 전달 합니다 `Set-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="ca45f-127">This example retrieves the CIM instance objects filtered by the Query parameter in to a variable `$x` using `Get-CimInstance`, and then passes the contents of the variable to the `Set-CimInstance` cmdlet.</span></span> <span data-ttu-id="ca45f-128">`Set-CimInstance` 그런 다음 **VariableValue** 속성을 **somevalue** 로 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-128">`Set-CimInstance` then modifies the **VariableValue** property to **somevalue**.</span></span> <span data-ttu-id="ca45f-129">**Passthru** 매개 변수를 사용 하기 때문에이 예에서는 수정 된 CIM 인스턴스 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-129">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

### <span data-ttu-id="ca45f-130">예제 4: CIM 인스턴스 속성 설정</span><span class="sxs-lookup"><span data-stu-id="ca45f-130">Example 4: Set the CIM instance property</span></span>

<span data-ttu-id="ca45f-131">이 예에서는 cmdlet을 사용 하 여 **쿼리** 매개 변수에 지정 된 CIM 인스턴스 개체를 변수로 검색 하 `$x` `Get-CimInstance` 고 변경할 개체의 **VariableValue** 속성 값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-131">This example retrieves the CIM instance object that is specified in the **Query** parameter into a variable `$x` using the `Get-CimInstance` cmdlet, and changes the **VariableValue** property value of the object to change.</span></span> <span data-ttu-id="ca45f-132">그런 다음 cmdlet을 사용 하 여 CIM 인스턴스 개체를 저장 합니다 `Set-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="ca45f-132">The CIM instance object is then saved using the `Set-CimInstance` cmdlet.</span></span>
<span data-ttu-id="ca45f-133">**Passthru** 매개 변수를 사용 하기 때문에이 예에서는 수정 된 CIM 인스턴스 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-133">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where name="testvar"'
$x.VariableValue = "Change"
Set-CimInstance -CimInstance $x -PassThru
```

### <span data-ttu-id="ca45f-134">예 5: WhatIf를 사용 하 여 수정할 CIM 인스턴스 목록 표시</span><span class="sxs-lookup"><span data-stu-id="ca45f-134">Example 5: Show the list of CIM instances to modify using WhatIf</span></span>

<span data-ttu-id="ca45f-135">이 예제에서는 일반 매개 변수 **WhatIf** 를 사용 하 여 수정 작업을 수행 하지 않도록 지정 하지만 완료 된 경우에만 발생 하는 결과를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-135">This example uses the common parameter **WhatIf** to specify that the modification should not be done, but only output what would happen if it were done.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -WhatIf
```

### <span data-ttu-id="ca45f-136">예 6: 사용자의 확인 후 CIM 인스턴스 설정</span><span class="sxs-lookup"><span data-stu-id="ca45f-136">Example 6: Set the CIM instance after confirmation from the user</span></span>

<span data-ttu-id="ca45f-137">이 예에서는 일반 매개 변수 **확인** 을 사용 하 여 사용자가 확인 한 후에만 수정 작업을 수행 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-137">This example uses the common parameter **Confirm** to specify that the modification should be done only after confirmation from the user.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -Confirm
```

### <span data-ttu-id="ca45f-138">예 7: 만든 CIM 인스턴스 설정</span><span class="sxs-lookup"><span data-stu-id="ca45f-138">Example 7: Set the created CIM instance</span></span>

<span data-ttu-id="ca45f-139">이 예에서는 cmdlet을 사용 하 여 지정 된 속성을 사용 하 여 CIM 인스턴스를 만들고 `New-CimInstance` 해당 내용을 변수에 검색 `$x` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-139">This example creates a CIM instance with the specified properties using the `New-CimInstance` cmdlet, and retrieves its contents in to a variable `$x`.</span></span> <span data-ttu-id="ca45f-140">그런 다음 변수는 cmdlet으로 전달 되어 `Set-CimInstance` **VariableValue** 속성의 값을 **somevalue** 로 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-140">The variable is then passed to the `Set-CimInstance` cmdlet, which modifies the value of **VariableValue** property to **somevalue**.</span></span>
<span data-ttu-id="ca45f-141">**Passthru** 매개 변수를 사용 하기 때문에이 예에서는 수정 된 CIM 인스턴스 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-141">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

```powershell
$x = New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";UserName="domain\user"} -Keys Name,UserName -ClientOnly
Set-CimInstance -CimInstance $x -Property @{VariableValue="somevalue"} -PassThru
```

## <span data-ttu-id="ca45f-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ca45f-142">PARAMETERS</span></span>

### <span data-ttu-id="ca45f-143">-CimSession</span><span class="sxs-lookup"><span data-stu-id="ca45f-143">-CimSession</span></span>

<span data-ttu-id="ca45f-144">원격 컴퓨터에서 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-144">Runs the cmdlets on a remote computer.</span></span> <span data-ttu-id="ca45f-145">컴퓨터 이름 또는 세션 개체 (예: 또는 cmdlet의 출력)를 입력 `New-CimSession` 합니다 `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="ca45f-145">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimInstanceSessionSet, QuerySessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ca45f-146">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="ca45f-146">-ComputerName</span></span>

<span data-ttu-id="ca45f-147">CIM 작업을 실행 하려는 컴퓨터의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-147">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="ca45f-148">FQDN (정규화 된 도메인 이름) 또는 NetBIOS 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-148">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="ca45f-149">이 매개 변수를 지정 하지 않으면 cmdlet은 COM (구성 요소 개체 모델)을 사용 하 여 로컬 컴퓨터에서 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-149">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="ca45f-150">이 매개 변수를 지정 하면 cmdlet이 WsMan 프로토콜을 사용 하 여 지정 된 컴퓨터에 대 한 임시 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-150">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="ca45f-151">동일한 컴퓨터에서 여러 작업을 수행 하는 경우 CIM 세션을 사용 하 여 연결 하면 성능이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-151">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ca45f-152">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ca45f-152">-InputObject</span></span>

<span data-ttu-id="ca45f-153">입력으로 사용할 CIM 인스턴스 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-153">Specifies a CIM instance object to use as input.</span></span>

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

### <span data-ttu-id="ca45f-154">-Namespace</span><span class="sxs-lookup"><span data-stu-id="ca45f-154">-Namespace</span></span>

<span data-ttu-id="ca45f-155">CIM 작업에 대 한 네임 스페이스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-155">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="ca45f-156">기본 네임 스페이스는 root/cimv2입니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-156">The default namespace is root/cimv2.</span></span> <span data-ttu-id="ca45f-157">PowerShell에서 네임 스페이스 목록을 제공 하기 위해 로컬 WMI 서버에서 네임 스페이스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 네임 스페이스 목록을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-157">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ca45f-158">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="ca45f-158">-OperationTimeoutSec</span></span>

<span data-ttu-id="ca45f-159">Cmdlet이 컴퓨터의 응답을 기다리는 시간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-159">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="ca45f-160">기본적으로이 매개 변수의 값은 0 이며이는 cmdlet이 서버에 대 한 기본 시간 제한 값을 사용 함을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-160">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="ca45f-161">**Operationtimeoutsec** 매개 변수가 강력한 연결 다시 시도 시간 제한 3 분 보다 작은 값으로 설정 된 경우, 서버에서 작업을 다시 연결할 수 있기 때문에 **operationtimeoutsec** 매개 변수의 값 보다 마지막으로 네트워크 오류가 복구 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-161">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="ca45f-162">-PassThru</span><span class="sxs-lookup"><span data-stu-id="ca45f-162">-PassThru</span></span>

<span data-ttu-id="ca45f-163">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-163">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="ca45f-164">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-164">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="ca45f-165">-속성</span><span class="sxs-lookup"><span data-stu-id="ca45f-165">-Property</span></span>

<span data-ttu-id="ca45f-166">이름-값 쌍을 사용 하 여 CIM 인스턴스의 속성을 해시 테이블로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-166">Specifies the properties of the CIM instance as a hash table (using name-value pairs).</span></span> <span data-ttu-id="ca45f-167">이 매개 변수를 사용 하 여 지정한 속성만 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-167">Only the properties specified using this parameter are changed.</span></span> <span data-ttu-id="ca45f-168">CIM 인스턴스의 다른 속성은 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-168">Other properties of the CIM instance are not changed.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet, QuerySessionSet, QueryComputerSet
Aliases: Arguments

Required: True (QuerySessionSet, QueryComputerSet), False (CimInstanceComputerSet, CimInstanceSessionSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ca45f-169">-Query</span><span class="sxs-lookup"><span data-stu-id="ca45f-169">-Query</span></span>

<span data-ttu-id="ca45f-170">Cmdlet을 실행할 CIM 인스턴스를 검색 하기 위해 CIM 서버에서 실행할 쿼리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-170">Specifies a query to run on the CIM server to retrieve CIM instances on which to run the cmdlet.</span></span> <span data-ttu-id="ca45f-171">QueryDialect 매개 변수를 사용 하 여 쿼리 언어를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-171">You can specify the query dialect using the QueryDialect parameter.</span></span>

<span data-ttu-id="ca45f-172">지정 된 값에 큰따옴표 ( `"` ), 작은따옴표 () `'` 또는 백슬래시 ()가 포함 된 경우 `\` 백슬래시 () 문자를 접두사로 사용 하 여 해당 문자를 이스케이프 해야 합니다 `\` .</span><span class="sxs-lookup"><span data-stu-id="ca45f-172">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="ca45f-173">지정 된 값이 WQL **LIKE** 연산자를 사용 하는 경우 대괄호 ( `[]` ): 백분율 ( `%` ), 밑줄 ( `_` ) 또는 여는 대괄호 ()로 묶어 다음 문자를 이스케이프 해야 합니다 `[` .</span><span class="sxs-lookup"><span data-stu-id="ca45f-173">If the value specified uses the WQL **LIKE** operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ca45f-174">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="ca45f-174">-QueryDialect</span></span>

<span data-ttu-id="ca45f-175">쿼리 매개 변수에 사용 되는 쿼리 언어를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-175">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="ca45f-176">이 매개 변수에 허용 되는 값은 **WQL** 또는 **CQL** 입니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-176">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span> <span data-ttu-id="ca45f-177">기본값은 **WQL** 입니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-177">The default value is **WQL**.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ca45f-178">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="ca45f-178">-ResourceUri</span></span>

<span data-ttu-id="ca45f-179">리소스 클래스 또는 인스턴스의 리소스 URI (uniform resource identifier)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-179">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="ca45f-180">URI는 컴퓨터에서 특정 유형의 리소스(예: 디스크 또는 프로세스)를 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-180">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="ca45f-181">URI는 접두사와 리소스 경로로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-181">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="ca45f-182">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="ca45f-182">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="ca45f-183">기본적으로이 매개 변수를 지정 하지 않으면 DMTF 표준 리소스 URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 가 사용 되 고 클래스 이름이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-183">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="ca45f-184">ResourceURI는 WSMan 프로토콜을 사용 하 여 만든 CIM 세션에만 사용할 수 있으며, ComputerName 매개 변수를 지정 하는 경우에만 WSMan을 사용 하 여 CIM 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-184">ResourceURI can only be used with CIM sessions created using the WSMan protocol, or when specifying the ComputerName parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="ca45f-185">ComputerName 매개 변수를 지정 하지 않고이 매개 변수를 지정 하거나 DCOM 프로토콜을 사용 하 여 만든 CIM 세션을 지정 하는 경우 DCOM 프로토콜이 ResourceURI 매개 변수를 지원 하지 않으므로 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-185">If you specify this parameter without specifying the ComputerName parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the ResourceURI parameter.</span></span>

<span data-ttu-id="ca45f-186">**ResourceUri** 매개 변수와 **필터** 매개 변수를 모두 지정 하면 **필터** 매개 변수가 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-186">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ca45f-187">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ca45f-187">-Confirm</span></span>

<span data-ttu-id="ca45f-188">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-188">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ca45f-189">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ca45f-189">-WhatIf</span></span>

<span data-ttu-id="ca45f-190">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-190">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ca45f-191">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-191">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ca45f-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ca45f-192">CommonParameters</span></span>

<span data-ttu-id="ca45f-193">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ca45f-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ca45f-194">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca45f-194">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="ca45f-195">입력</span><span class="sxs-lookup"><span data-stu-id="ca45f-195">INPUTS</span></span>

### <span data-ttu-id="ca45f-196">Ciminstance 개체로.</span><span class="sxs-lookup"><span data-stu-id="ca45f-196">Microsoft.Management.Infrastructure.CimInstance</span></span>

## <span data-ttu-id="ca45f-197">출력</span><span class="sxs-lookup"><span data-stu-id="ca45f-197">OUTPUTS</span></span>

### <span data-ttu-id="ca45f-198">Ciminstance 개체로.</span><span class="sxs-lookup"><span data-stu-id="ca45f-198">Microsoft.Management.Infrastructure.CimInstance</span></span>

<span data-ttu-id="ca45f-199">**Passthru** 매개 변수를 지정 하면이 cmdlet이 수정 된 CIM 인스턴스 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca45f-199">When the **Passthru** parameter is specified, this cmdlet returns a modified CIM instance object.</span></span>

## <span data-ttu-id="ca45f-200">참고</span><span class="sxs-lookup"><span data-stu-id="ca45f-200">NOTES</span></span>

## <span data-ttu-id="ca45f-201">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ca45f-201">RELATED LINKS</span></span>

[<span data-ttu-id="ca45f-202">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="ca45f-202">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="ca45f-203">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="ca45f-203">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="ca45f-204">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="ca45f-204">Remove-CimInstance</span></span>](remove-ciminstance.md)

