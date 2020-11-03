---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-ciminstance?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimInstance
ms.openlocfilehash: f236956b1da5f9632ff163cbf8a818bf190fd29a
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218322"
---
# <span data-ttu-id="fe0bd-103">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="fe0bd-103">Remove-CimInstance</span></span>

## <span data-ttu-id="fe0bd-104">개요</span><span class="sxs-lookup"><span data-stu-id="fe0bd-104">SYNOPSIS</span></span>
<span data-ttu-id="fe0bd-105">컴퓨터에서 CIM 인스턴스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-105">Removes a CIM instance from a computer.</span></span>

## <span data-ttu-id="fe0bd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fe0bd-106">SYNTAX</span></span>

### <span data-ttu-id="fe0bd-107">CimInstanceComputerSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="fe0bd-107">CimInstanceComputerSet (Default)</span></span>

```
Remove-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fe0bd-108">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="fe0bd-108">CimInstanceSessionSet</span></span>

```
Remove-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fe0bd-109">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="fe0bd-109">QuerySessionSet</span></span>

```
Remove-CimInstance -CimSession <CimSession[]> [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="fe0bd-110">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="fe0bd-110">QueryComputerSet</span></span>

```
Remove-CimInstance [-ComputerName <String[]>] [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="fe0bd-111">설명</span><span class="sxs-lookup"><span data-stu-id="fe0bd-111">DESCRIPTION</span></span>

<span data-ttu-id="fe0bd-112">이 cmdlet은 cim 서버에서 CIM 인스턴스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-112">This cmdlet removes a CIM instance from a CIM server.</span></span> <span data-ttu-id="fe0bd-113">Cmdlet에서 검색 된 CIM 인스턴스 개체를 사용 `Get-CimInstance` 하거나 쿼리를 지정 하 여 제거할 cim 인스턴스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-113">You can specify the CIM instance to remove by using either a CIM instance object retrieved by the `Get-CimInstance` cmdlet, or by specifying a query.</span></span>

<span data-ttu-id="fe0bd-114">**InputObject** 매개 변수를 지정 하지 않으면 cmdlet은 다음 방법 중 하나로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-114">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="fe0bd-115">**ComputerName** 매개 변수와 **CimSession** 매개 변수를 모두 지정 하지 않으면이 Cmdlet은 COM (구성 요소 개체 모델) 세션을 사용 하 여 WMI (로컬 WMI(Windows Management Instrumentation))에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-115">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="fe0bd-116">**Computername** 매개 변수 또는 **CimSession** 매개 변수를 지정 하는 경우이 cmdlet은 **computername** 매개 변수 또는 **CimSession** 매개 변수로 지정 된 CIM 서버에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-116">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

## <span data-ttu-id="fe0bd-117">예제</span><span class="sxs-lookup"><span data-stu-id="fe0bd-117">EXAMPLES</span></span>

### <span data-ttu-id="fe0bd-118">예제 1: CIM 인스턴스 제거</span><span class="sxs-lookup"><span data-stu-id="fe0bd-118">Example 1: Remove the CIM instance</span></span>

<span data-ttu-id="fe0bd-119">이 예제에서는 **Query** 매개 변수를 사용 하 여 **Win32_Environment** 이라는 클래스에서 **TESTVAR** 문자열로 시작 하는 CIM 인스턴스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-119">This example use the **Query** parameter to remove CIM instances from the class named **Win32_Environment** that start with the character string **testvar** .</span></span>

```powershell
Remove-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"'
```

### <span data-ttu-id="fe0bd-120">예 2: CIM 인스턴스 개체를 사용 하 여 CIM 인스턴스 제거</span><span class="sxs-lookup"><span data-stu-id="fe0bd-120">Example 2: Remove the CIM instance using CIM instance object</span></span>

<span data-ttu-id="fe0bd-121">이 예에서는 **쿼리** 매개 변수를 사용 하 여 필터링 된 CIM 인스턴스 개체를 검색 하 고 `$var` cmdlet을 사용 하 여 명명 된 변수에 저장 합니다 `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="fe0bd-121">This example retrieves the CIM instance objects filtered by the **Query** parameter and stores them in variable named `$var` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="fe0bd-122">그러면 변수의 내용이 cmdlet에 전달 되어 `Remove-CimInstance` CIM 인스턴스가 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-122">The contents of the variable are then passed to the `Remove-CimInstance` cmdlet, which removes the CIM instances.</span></span>

```powershell
notepad.exe
$var = Get-CimInstance -Query 'Select * from Win32_Process where name LIKE "notepad%"'
Remove-CimInstance -InputObject $var
```

## <span data-ttu-id="fe0bd-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fe0bd-123">PARAMETERS</span></span>

### <span data-ttu-id="fe0bd-124">-CimSession</span><span class="sxs-lookup"><span data-stu-id="fe0bd-124">-CimSession</span></span>

<span data-ttu-id="fe0bd-125">지정 된 CIM 세션을 사용 하 여 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-125">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="fe0bd-126">CIM 세션을 포함 하는 변수 또는 CIM 세션을 만들거나 가져오는 명령 (예: 또는 cmdlet)을 입력 합니다 `New-CimSession` `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="fe0bd-126">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="fe0bd-127">자세한 내용은 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-127">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

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

### <span data-ttu-id="fe0bd-128">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="fe0bd-128">-ComputerName</span></span>

<span data-ttu-id="fe0bd-129">CIM 작업을 실행 하려는 컴퓨터의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-129">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="fe0bd-130">FQDN (정규화 된 도메인 이름) 또는 NetBIOS 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-130">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="fe0bd-131">이 매개 변수를 지정 하면 cmdlet이 WsMan 프로토콜을 사용 하 여 지정 된 컴퓨터에 대 한 임시 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-131">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="fe0bd-132">이 매개 변수를 지정 하지 않으면 cmdlet은 COM (구성 요소 개체 모델)을 사용 하 여 로컬 컴퓨터에서 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-132">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="fe0bd-133">동일한 컴퓨터에서 여러 작업을 수행 하는 경우 CIM 세션을 사용 하 여 연결 하면 성능이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-133">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

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

### <span data-ttu-id="fe0bd-134">-InputObject</span><span class="sxs-lookup"><span data-stu-id="fe0bd-134">-InputObject</span></span>

<span data-ttu-id="fe0bd-135">CIM 서버에서 제거할 CIM 인스턴스 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-135">Specifies a CIM instance object to be removed from the CIM server.</span></span> <span data-ttu-id="fe0bd-136">Cmdlet에 전달 된 개체는 변경 되지 않으며 CIM 서버의 인스턴스만 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-136">The object passed to the cmdlet is not changed, only the instance in the CIM server is removed.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fe0bd-137">-Namespace</span><span class="sxs-lookup"><span data-stu-id="fe0bd-137">-Namespace</span></span>

<span data-ttu-id="fe0bd-138">CIM 작업에 대 한 네임 스페이스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-138">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="fe0bd-139">기본 네임 스페이스는 **root/cimv2** 입니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-139">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="fe0bd-140">PowerShell에서 네임 스페이스 목록을 제공 하기 위해 로컬 WMI 서버에서 네임 스페이스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 네임 스페이스 목록을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-140">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fe0bd-141">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="fe0bd-141">-OperationTimeoutSec</span></span>

<span data-ttu-id="fe0bd-142">Cmdlet이 컴퓨터의 응답을 기다리는 시간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-142">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="fe0bd-143">기본적으로이 매개 변수의 값은 0 이며이는 cmdlet이 서버에 대 한 기본 시간 제한 값을 사용 함을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-143">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="fe0bd-144">**Operationtimeoutsec** 매개 변수가 강력한 연결 다시 시도 시간 제한 3 분 보다 작은 값으로 설정 된 경우, 서버에서 작업을 다시 연결할 수 있기 때문에 **operationtimeoutsec** 매개 변수의 값 보다 마지막으로 네트워크 오류가 복구 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-144">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="fe0bd-145">-Query</span><span class="sxs-lookup"><span data-stu-id="fe0bd-145">-Query</span></span>

<span data-ttu-id="fe0bd-146">CIM 서버에서 실행할 쿼리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-146">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="fe0bd-147">**Querydialect** 매개 변수를 사용 하 여 쿼리 언어를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-147">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

<span data-ttu-id="fe0bd-148">지정 된 값에 큰따옴표 ( `"` ), 작은따옴표 () `'` 또는 백슬래시 ()가 포함 된 경우 `\` 백슬래시 () 문자를 접두사로 사용 하 여 해당 문자를 이스케이프 해야 합니다 `\` .</span><span class="sxs-lookup"><span data-stu-id="fe0bd-148">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="fe0bd-149">지정 된 값이 WQL LIKE 연산자를 사용 하는 경우 대괄호 ( `[]` ): 백분율 ( `%` ), 밑줄 ( `_` ) 또는 여는 대괄호 ()로 묶어 다음 문자를 이스케이프 해야 합니다 `[` .</span><span class="sxs-lookup"><span data-stu-id="fe0bd-149">If the value specified uses the WQL LIKE operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fe0bd-150">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="fe0bd-150">-QueryDialect</span></span>

<span data-ttu-id="fe0bd-151">쿼리 매개 변수에 사용 되는 쿼리 언어를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-151">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="fe0bd-152">이 매개 변수에 허용 되는 값은 **WQL** 또는 **CQL** 입니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-152">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span> <span data-ttu-id="fe0bd-153">기본값은 **WQL** 입니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-153">The default value is **WQL**.</span></span>

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

### <span data-ttu-id="fe0bd-154">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="fe0bd-154">-ResourceUri</span></span>

<span data-ttu-id="fe0bd-155">리소스 클래스 또는 인스턴스의 리소스 URI (uniform resource identifier)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-155">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="fe0bd-156">URI는 컴퓨터에서 특정 유형의 리소스(예: 디스크 또는 프로세스)를 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-156">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="fe0bd-157">URI는 접두사와 리소스 경로로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-157">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="fe0bd-158">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="fe0bd-158">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="fe0bd-159">기본적으로이 매개 변수를 지정 하지 않으면 DMTF 표준 리소스 URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 가 사용 되 고 클래스 이름이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-159">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="fe0bd-160">ResourceURI는 WSMan 프로토콜을 사용 하 여 만든 CIM 세션에만 사용할 수 있으며, ComputerName 매개 변수를 지정 하는 경우에만 WSMan을 사용 하 여 CIM 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-160">ResourceURI can only be used with CIM sessions created using the WSMan protocol, or when specifying the ComputerName parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="fe0bd-161">ComputerName 매개 변수를 지정 하지 않고이 매개 변수를 지정 하거나 DCOM 프로토콜을 사용 하 여 만든 CIM 세션을 지정 하는 경우 DCOM 프로토콜이 ResourceURI 매개 변수를 지원 하지 않기 때문에 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-161">If you specify this parameter without specifying the ComputerName parameter, or if you specify a CIM session created using DCOM protocol, you get an error, because the DCOM protocol does not support the ResourceURI parameter.</span></span>

<span data-ttu-id="fe0bd-162">**ResourceUri** 매개 변수와 **필터** 매개 변수를 모두 지정 하면 **필터** 매개 변수가 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-162">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

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

### <span data-ttu-id="fe0bd-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fe0bd-163">-Confirm</span></span>

<span data-ttu-id="fe0bd-164">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="fe0bd-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fe0bd-165">-WhatIf</span></span>

<span data-ttu-id="fe0bd-166">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-166">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="fe0bd-167">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="fe0bd-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fe0bd-168">CommonParameters</span></span>

<span data-ttu-id="fe0bd-169">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-169">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fe0bd-170">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-170">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fe0bd-171">입력</span><span class="sxs-lookup"><span data-stu-id="fe0bd-171">INPUTS</span></span>

### <span data-ttu-id="fe0bd-172">없음</span><span class="sxs-lookup"><span data-stu-id="fe0bd-172">None</span></span>

<span data-ttu-id="fe0bd-173">이 cmdlet은 입력 개체를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-173">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="fe0bd-174">출력</span><span class="sxs-lookup"><span data-stu-id="fe0bd-174">OUTPUTS</span></span>

### <span data-ttu-id="fe0bd-175">없음</span><span class="sxs-lookup"><span data-stu-id="fe0bd-175">None</span></span>

<span data-ttu-id="fe0bd-176">이 cmdlet은 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe0bd-176">This cmdlet produces no outputs.</span></span>

## <span data-ttu-id="fe0bd-177">참고</span><span class="sxs-lookup"><span data-stu-id="fe0bd-177">NOTES</span></span>

## <span data-ttu-id="fe0bd-178">관련 링크</span><span class="sxs-lookup"><span data-stu-id="fe0bd-178">RELATED LINKS</span></span>

[<span data-ttu-id="fe0bd-179">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="fe0bd-179">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="fe0bd-180">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="fe0bd-180">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="fe0bd-181">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="fe0bd-181">Set-CimInstance</span></span>](Set-CimInstance.md)

