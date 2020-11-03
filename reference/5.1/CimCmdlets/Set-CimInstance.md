---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/set-ciminstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-CimInstance
ms.openlocfilehash: 7f44ddf52c2ad3ce68c5eccf0e8f952a0fa1873e
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218097"
---
# <span data-ttu-id="a03e2-103">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="a03e2-103">Set-CimInstance</span></span>

## <span data-ttu-id="a03e2-104">개요</span><span class="sxs-lookup"><span data-stu-id="a03e2-104">SYNOPSIS</span></span>
<span data-ttu-id="a03e2-105">Cim 클래스의 ModifyInstance 메서드를 호출 하 여 CIM 서버에서 CIM 인스턴스를 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-105">Modifies a CIM instance on a CIM server by calling the ModifyInstance method of the CIM class.</span></span>

## <span data-ttu-id="a03e2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a03e2-106">SYNTAX</span></span>

### <span data-ttu-id="a03e2-107">CimInstanceComputerSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="a03e2-107">CimInstanceComputerSet (Default)</span></span>

```
Set-CimInstance [-ComputerName <String[]>] [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="a03e2-108">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="a03e2-108">CimInstanceSessionSet</span></span>

```
Set-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="a03e2-109">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="a03e2-109">QuerySessionSet</span></span>

```
Set-CimInstance -CimSession <CimSession[]> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="a03e2-110">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="a03e2-110">QueryComputerSet</span></span>

```
Set-CimInstance [-ComputerName <String[]>] [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="a03e2-111">설명</span><span class="sxs-lookup"><span data-stu-id="a03e2-111">DESCRIPTION</span></span>

<span data-ttu-id="a03e2-112">이 cmdlet은 CIM 서버에서 CIM 인스턴스를 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-112">This cmdlet modifies a CIM instance on a CIM server.</span></span>

<span data-ttu-id="a03e2-113">**InputObject** 매개 변수를 지정 하지 않으면 cmdlet은 다음 방법 중 하나로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-113">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="a03e2-114">**ComputerName** 매개 변수와 **CimSession** 매개 변수를 모두 지정 하지 않으면이 Cmdlet은 COM (구성 요소 개체 모델) 세션을 사용 하 여 WMI (로컬 WMI(Windows Management Instrumentation))에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-114">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="a03e2-115">**Computername** 매개 변수 또는 **CimSession** 매개 변수를 지정 하는 경우이 cmdlet은 **computername** 매개 변수 또는 **CimSession** 매개 변수로 지정 된 CIM 서버에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-115">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="a03e2-116">**InputObject** 매개 변수를 지정 하는 경우 cmdlet은 다음 방법 중 하나로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-116">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="a03e2-117">**ComputerName** 매개 변수와 **CimSession** 매개 변수를 모두 지정 하지 않으면이 cmdlet은 입력 개체의 컴퓨터 이름과 CIM 세션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-117">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="a03e2-118">**ComputerName** 매개 변수 또는 **CimSession** 매개 변수 중 하나가 지정 된 경우이 cmdlet은 **CimSession** 매개 변수 값 또는 **ComputerName** 매개 변수 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-118">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the **CimSession** parameter value or **ComputerName** parameter value.</span></span> <span data-ttu-id="a03e2-119">이는 그다지 일반적이 지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-119">This is not very common.</span></span>

## <span data-ttu-id="a03e2-120">예제</span><span class="sxs-lookup"><span data-stu-id="a03e2-120">EXAMPLES</span></span>

### <span data-ttu-id="a03e2-121">예제 1: CIM 인스턴스 설정</span><span class="sxs-lookup"><span data-stu-id="a03e2-121">Example 1: Set the CIM instance</span></span>

<span data-ttu-id="a03e2-122">이 예에서는 **쿼리** 매개 변수를 사용 하 여 **VariableValue** 속성의 값을 **abcd** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-122">This example sets the value of the **VariableValue** property to **abcd** using the **Query** parameter.</span></span> <span data-ttu-id="a03e2-123">WQL (WMI(Windows Management Instrumentation) Query Language) 쿼리와 일치 하는 인스턴스를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-123">You can modify instances matching a Windows Management Instrumentation Query Language (WQL) query.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"}
```

### <span data-ttu-id="a03e2-124">예 2: 파이프라인을 사용 하 여 CIM 인스턴스 속성 설정</span><span class="sxs-lookup"><span data-stu-id="a03e2-124">Example 2: Set the CIM instance property using pipeline</span></span>

<span data-ttu-id="a03e2-125">이 예에서는 cmdlet을 사용 하 여 **쿼리** 매개 변수를 통해 필터링 된 CIM 인스턴스 개체를 검색 합니다 `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="a03e2-125">This example retrieves the CIM instance object filtered by the **Query** parameter using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="a03e2-126">`Set-CimInstance`Cmdlet은 **VariableValue** 속성의 값을 **abcd** 로 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-126">The `Set-CimInstance` cmdlet modifies the value of **VariableValue** property to **abcd**.</span></span>

```powershell
Get-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' |
  Set-CimInstance -Property @{VariableValue="abcd"}
```

### <span data-ttu-id="a03e2-127">예제 3: input 개체를 사용 하 여 CIM 인스턴스 속성 설정</span><span class="sxs-lookup"><span data-stu-id="a03e2-127">Example 3: Set the CIM instance property using input object</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where Name="testvar"'
Set-CimInstance -InputObject $x -Property @{VariableValue="somevalue"} -PassThru
```

<span data-ttu-id="a03e2-128">이 예에서는를 사용 하 여 변수에서 쿼리 매개 변수로 필터링 된 CIM 인스턴스 개체를 검색 한 `$x` `Get-CimInstance` 다음 변수의 내용을 cmdlet에 전달 합니다 `Set-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="a03e2-128">This example retrieves the CIM instance objects filtered by the Query parameter in to a variable `$x` using `Get-CimInstance`, and then passes the contents of the variable to the `Set-CimInstance` cmdlet.</span></span> <span data-ttu-id="a03e2-129">`Set-CimInstance` 그런 다음 **VariableValue** 속성을 **somevalue** 로 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-129">`Set-CimInstance` then modifies the **VariableValue** property to **somevalue**.</span></span> <span data-ttu-id="a03e2-130">**Passthru** 매개 변수를 사용 하기 때문에이 예에서는 수정 된 CIM 인스턴스 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-130">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

### <span data-ttu-id="a03e2-131">예제 4: CIM 인스턴스 속성 설정</span><span class="sxs-lookup"><span data-stu-id="a03e2-131">Example 4: Set the CIM instance property</span></span>

<span data-ttu-id="a03e2-132">이 예에서는 cmdlet을 사용 하 여 **쿼리** 매개 변수에 지정 된 CIM 인스턴스 개체를 변수로 검색 하 `$x` `Get-CimInstance` 고 변경할 개체의 **VariableValue** 속성 값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-132">This example retrieves the CIM instance object that is specified in the **Query** parameter into a variable `$x` using the `Get-CimInstance` cmdlet, and changes the **VariableValue** property value of the object to change.</span></span> <span data-ttu-id="a03e2-133">그런 다음 cmdlet을 사용 하 여 CIM 인스턴스 개체를 저장 합니다 `Set-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="a03e2-133">The CIM instance object is then saved using the `Set-CimInstance` cmdlet.</span></span>
<span data-ttu-id="a03e2-134">**Passthru** 매개 변수를 사용 하기 때문에이 예에서는 수정 된 CIM 인스턴스 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-134">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where name="testvar"'
$x.VariableValue = "Change"
Set-CimInstance -CimInstance $x -PassThru
```

### <span data-ttu-id="a03e2-135">예 5: WhatIf를 사용 하 여 수정할 CIM 인스턴스 목록 표시</span><span class="sxs-lookup"><span data-stu-id="a03e2-135">Example 5: Show the list of CIM instances to modify using WhatIf</span></span>

<span data-ttu-id="a03e2-136">이 예제에서는 일반 매개 변수 **WhatIf** 를 사용 하 여 수정 작업을 수행 하지 않도록 지정 하지만 완료 된 경우에만 발생 하는 결과를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-136">This example uses the common parameter **WhatIf** to specify that the modification should not be done, but only output what would happen if it were done.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -WhatIf
```

### <span data-ttu-id="a03e2-137">예 6: 사용자의 확인 후 CIM 인스턴스 설정</span><span class="sxs-lookup"><span data-stu-id="a03e2-137">Example 6: Set the CIM instance after confirmation from the user</span></span>

<span data-ttu-id="a03e2-138">이 예에서는 일반 매개 변수 **확인** 을 사용 하 여 사용자가 확인 한 후에만 수정 작업을 수행 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-138">This example uses the common parameter **Confirm** to specify that the modification should be done only after confirmation from the user.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -Confirm
```

### <span data-ttu-id="a03e2-139">예 7: 만든 CIM 인스턴스 설정</span><span class="sxs-lookup"><span data-stu-id="a03e2-139">Example 7: Set the created CIM instance</span></span>

<span data-ttu-id="a03e2-140">이 예에서는 cmdlet을 사용 하 여 지정 된 속성을 사용 하 여 CIM 인스턴스를 만들고 `New-CimInstance` 해당 내용을 변수에 검색 `$x` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-140">This example creates a CIM instance with the specified properties using the `New-CimInstance` cmdlet, and retrieves its contents in to a variable `$x`.</span></span> <span data-ttu-id="a03e2-141">그런 다음 변수는 cmdlet으로 전달 되어 `Set-CimInstance` **VariableValue** 속성의 값을 **somevalue** 로 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-141">The variable is then passed to the `Set-CimInstance` cmdlet, which modifies the value of **VariableValue** property to **somevalue**.</span></span>
<span data-ttu-id="a03e2-142">**Passthru** 매개 변수를 사용 하기 때문에이 예에서는 수정 된 CIM 인스턴스 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-142">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

```powershell
$x = New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";UserName="domain\user"} -Keys Name,UserName -ClientOnly
Set-CimInstance -CimInstance $x -Property @{VariableValue="somevalue"} -PassThru
```

## <span data-ttu-id="a03e2-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a03e2-143">PARAMETERS</span></span>

### <span data-ttu-id="a03e2-144">-CimSession</span><span class="sxs-lookup"><span data-stu-id="a03e2-144">-CimSession</span></span>

<span data-ttu-id="a03e2-145">원격 컴퓨터에서 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-145">Runs the cmdlets on a remote computer.</span></span> <span data-ttu-id="a03e2-146">컴퓨터 이름 또는 세션 개체 (예: 또는 cmdlet의 출력)를 입력 `New-CimSession` 합니다 `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="a03e2-146">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: QuerySessionSet, CimInstanceSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a03e2-147">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="a03e2-147">-ComputerName</span></span>

<span data-ttu-id="a03e2-148">CIM 작업을 실행 하려는 컴퓨터의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-148">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="a03e2-149">FQDN (정규화 된 도메인 이름) 또는 NetBIOS 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-149">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="a03e2-150">이 매개 변수를 지정 하지 않으면 cmdlet은 COM (구성 요소 개체 모델)을 사용 하 여 로컬 컴퓨터에서 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-150">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="a03e2-151">이 매개 변수를 지정 하면 cmdlet이 WsMan 프로토콜을 사용 하 여 지정 된 컴퓨터에 대 한 임시 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-151">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="a03e2-152">동일한 컴퓨터에서 여러 작업을 수행 하는 경우 CIM 세션을 사용 하 여 연결 하면 성능이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-152">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

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

### <span data-ttu-id="a03e2-153">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a03e2-153">-InputObject</span></span>

<span data-ttu-id="a03e2-154">입력으로 사용할 CIM 인스턴스 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-154">Specifies a CIM instance object to use as input.</span></span>

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

### <span data-ttu-id="a03e2-155">-Namespace</span><span class="sxs-lookup"><span data-stu-id="a03e2-155">-Namespace</span></span>

<span data-ttu-id="a03e2-156">CIM 작업에 대 한 네임 스페이스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-156">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="a03e2-157">기본 네임 스페이스는 root/cimv2입니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-157">The default namespace is root/cimv2.</span></span> <span data-ttu-id="a03e2-158">PowerShell에서 네임 스페이스 목록을 제공 하기 위해 로컬 WMI 서버에서 네임 스페이스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 네임 스페이스 목록을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-158">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

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

### <span data-ttu-id="a03e2-159">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="a03e2-159">-OperationTimeoutSec</span></span>

<span data-ttu-id="a03e2-160">Cmdlet이 컴퓨터의 응답을 기다리는 시간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-160">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="a03e2-161">기본적으로이 매개 변수의 값은 0 이며이는 cmdlet이 서버에 대 한 기본 시간 제한 값을 사용 함을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-161">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="a03e2-162">**Operationtimeoutsec** 매개 변수가 강력한 연결 다시 시도 시간 제한 3 분 보다 작은 값으로 설정 된 경우, 서버에서 작업을 다시 연결할 수 있기 때문에 **operationtimeoutsec** 매개 변수의 값 보다 마지막으로 네트워크 오류가 복구 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-162">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="a03e2-163">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a03e2-163">-PassThru</span></span>

<span data-ttu-id="a03e2-164">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-164">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="a03e2-165">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-165">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="a03e2-166">-속성</span><span class="sxs-lookup"><span data-stu-id="a03e2-166">-Property</span></span>

<span data-ttu-id="a03e2-167">이름-값 쌍을 사용 하 여 CIM 인스턴스의 속성을 해시 테이블로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-167">Specifies the properties of the CIM instance as a hash table (using name-value pairs).</span></span> <span data-ttu-id="a03e2-168">이 매개 변수를 사용 하 여 지정한 속성만 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-168">Only the properties specified using this parameter are changed.</span></span> <span data-ttu-id="a03e2-169">CIM 인스턴스의 다른 속성은 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-169">Other properties of the CIM instance are not changed.</span></span>

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

### <span data-ttu-id="a03e2-170">-Query</span><span class="sxs-lookup"><span data-stu-id="a03e2-170">-Query</span></span>

<span data-ttu-id="a03e2-171">Cmdlet을 실행할 CIM 인스턴스를 검색 하기 위해 CIM 서버에서 실행할 쿼리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-171">Specifies a query to run on the CIM server to retrieve CIM instances on which to run the cmdlet.</span></span> <span data-ttu-id="a03e2-172">QueryDialect 매개 변수를 사용 하 여 쿼리 언어를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-172">You can specify the query dialect using the QueryDialect parameter.</span></span>

<span data-ttu-id="a03e2-173">지정 된 값에 큰따옴표 ( `"` ), 작은따옴표 () `'` 또는 백슬래시 ()가 포함 된 경우 `\` 백슬래시 () 문자를 접두사로 사용 하 여 해당 문자를 이스케이프 해야 합니다 `\` .</span><span class="sxs-lookup"><span data-stu-id="a03e2-173">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="a03e2-174">지정 된 값이 WQL **LIKE** 연산자를 사용 하는 경우 대괄호 ( `[]` ): 백분율 ( `%` ), 밑줄 ( `_` ) 또는 여는 대괄호 ()로 묶어 다음 문자를 이스케이프 해야 합니다 `[` .</span><span class="sxs-lookup"><span data-stu-id="a03e2-174">If the value specified uses the WQL **LIKE** operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

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

### <span data-ttu-id="a03e2-175">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="a03e2-175">-QueryDialect</span></span>

<span data-ttu-id="a03e2-176">쿼리 매개 변수에 사용 되는 쿼리 언어를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-176">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="a03e2-177">이 매개 변수에 허용 되는 값은 **WQL** 또는 **CQL** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-177">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span> <span data-ttu-id="a03e2-178">기본값은 **WQL** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-178">The default value is **WQL**.</span></span>

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

### <span data-ttu-id="a03e2-179">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="a03e2-179">-ResourceUri</span></span>

<span data-ttu-id="a03e2-180">리소스 클래스 또는 인스턴스의 리소스 URI (uniform resource identifier)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-180">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="a03e2-181">URI는 컴퓨터에서 특정 유형의 리소스(예: 디스크 또는 프로세스)를 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-181">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="a03e2-182">URI는 접두사와 리소스 경로로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-182">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="a03e2-183">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a03e2-183">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="a03e2-184">기본적으로이 매개 변수를 지정 하지 않으면 DMTF 표준 리소스 URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 가 사용 되 고 클래스 이름이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-184">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="a03e2-185">ResourceURI는 WSMan 프로토콜을 사용 하 여 만든 CIM 세션에만 사용할 수 있으며, ComputerName 매개 변수를 지정 하는 경우에만 WSMan을 사용 하 여 CIM 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-185">ResourceURI can only be used with CIM sessions created using the WSMan protocol, or when specifying the ComputerName parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="a03e2-186">ComputerName 매개 변수를 지정 하지 않고이 매개 변수를 지정 하거나 DCOM 프로토콜을 사용 하 여 만든 CIM 세션을 지정 하는 경우 DCOM 프로토콜이 ResourceURI 매개 변수를 지원 하지 않으므로 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-186">If you specify this parameter without specifying the ComputerName parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the ResourceURI parameter.</span></span>

<span data-ttu-id="a03e2-187">**ResourceUri** 매개 변수와 **필터** 매개 변수를 모두 지정 하면 **필터** 매개 변수가 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-187">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

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

### <span data-ttu-id="a03e2-188">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a03e2-188">-Confirm</span></span>

<span data-ttu-id="a03e2-189">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-189">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a03e2-190">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a03e2-190">-WhatIf</span></span>

<span data-ttu-id="a03e2-191">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-191">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a03e2-192">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-192">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a03e2-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a03e2-193">CommonParameters</span></span>

<span data-ttu-id="a03e2-194">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a03e2-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a03e2-195">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a03e2-195">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a03e2-196">입력</span><span class="sxs-lookup"><span data-stu-id="a03e2-196">INPUTS</span></span>

### <span data-ttu-id="a03e2-197">Ciminstance 개체로.</span><span class="sxs-lookup"><span data-stu-id="a03e2-197">Microsoft.Management.Infrastructure.CimInstance</span></span>

## <span data-ttu-id="a03e2-198">출력</span><span class="sxs-lookup"><span data-stu-id="a03e2-198">OUTPUTS</span></span>

### <span data-ttu-id="a03e2-199">Ciminstance 개체로.</span><span class="sxs-lookup"><span data-stu-id="a03e2-199">Microsoft.Management.Infrastructure.CimInstance</span></span>

<span data-ttu-id="a03e2-200">**Passthru** 매개 변수를 지정 하면이 cmdlet이 수정 된 CIM 인스턴스 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a03e2-200">When the **Passthru** parameter is specified, this cmdlet returns a modified CIM instance object.</span></span>

## <span data-ttu-id="a03e2-201">참고</span><span class="sxs-lookup"><span data-stu-id="a03e2-201">NOTES</span></span>

## <span data-ttu-id="a03e2-202">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a03e2-202">RELATED LINKS</span></span>

[<span data-ttu-id="a03e2-203">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="a03e2-203">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="a03e2-204">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="a03e2-204">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="a03e2-205">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="a03e2-205">Remove-CimInstance</span></span>](remove-ciminstance.md)
