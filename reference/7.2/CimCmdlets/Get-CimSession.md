---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimSession
ms.openlocfilehash: 0e531b3cc072b7cc1efe0ef06fb741326bf3a72b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601050"
---
# <span data-ttu-id="9155c-102">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="9155c-102">Get-CimSession</span></span>

## <span data-ttu-id="9155c-103">개요</span><span class="sxs-lookup"><span data-stu-id="9155c-103">SYNOPSIS</span></span>
<span data-ttu-id="9155c-104">현재 세션에서 CIM 세션 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-104">Gets the CIM session objects from the current session.</span></span>

## <span data-ttu-id="9155c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9155c-105">SYNTAX</span></span>

### <span data-ttu-id="9155c-106">ComputerNameSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="9155c-106">ComputerNameSet (Default)</span></span>

```
Get-CimSession [[-ComputerName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="9155c-107">SessionIdSet</span><span class="sxs-lookup"><span data-stu-id="9155c-107">SessionIdSet</span></span>

```
Get-CimSession [-Id] <UInt32[]> [<CommonParameters>]
```

### <span data-ttu-id="9155c-108">InstanceIdSet</span><span class="sxs-lookup"><span data-stu-id="9155c-108">InstanceIdSet</span></span>

```
Get-CimSession -InstanceId <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="9155c-109">NameSet</span><span class="sxs-lookup"><span data-stu-id="9155c-109">NameSet</span></span>

```
Get-CimSession -Name <String[]> [<CommonParameters>]
```

## <span data-ttu-id="9155c-110">설명</span><span class="sxs-lookup"><span data-stu-id="9155c-110">DESCRIPTION</span></span>

<span data-ttu-id="9155c-111">기본적으로이 cmdlet은 현재 PowerShell 세션에서 만든 모든 CIM 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-111">By default, the cmdlet gets all of the CIM sessions created in the current PowerShell session.</span></span> <span data-ttu-id="9155c-112">의 매개 변수를 사용 `Get-CimSession` 하 여 특정 컴퓨터에 대 한 세션을 가져오거나 이름 또는 다른 식별자로 세션을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-112">You can use the parameters of `Get-CimSession` to get the sessions that are for particular computers, or you can identify sessions by their names or other identifiers.</span></span> <span data-ttu-id="9155c-113">`Get-CimSession` 다른 PowerShell 세션에서 만들었거나 다른 컴퓨터에서 만들어진 CIM 세션은 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-113">`Get-CimSession` does not get CIM sessions that were created in other PowerShell sessions or that were created on other computers.</span></span>

<span data-ttu-id="9155c-114">CIM 세션에 대 한 자세한 내용은 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9155c-114">For more information about CIM sessions, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

## <span data-ttu-id="9155c-115">예제</span><span class="sxs-lookup"><span data-stu-id="9155c-115">EXAMPLES</span></span>

### <span data-ttu-id="9155c-116">예제 1: 현재 PowerShell 세션에서 CIM 세션 가져오기</span><span class="sxs-lookup"><span data-stu-id="9155c-116">Example 1: Get CIM sessions from the current PowerShell session</span></span>

<span data-ttu-id="9155c-117">이 예제에서는 [CimSession](New-CimSession.md)를 사용 하 여 cim 세션을 만든 다음를 사용 하 여 cim 세션을 가져옵니다 `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="9155c-117">This example creates CIM sessions using [New-CimSession](New-CimSession.md), and then gets the CIM sessions using `Get-CimSession`.</span></span>

```powershell
New-CimSession -ComputerName Server01,Server02
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc3-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="9155c-118">예 2: 특정 컴퓨터에 대 한 CIM 세션 가져오기</span><span class="sxs-lookup"><span data-stu-id="9155c-118">Example 2: Get the CIM sessions to a specific computer</span></span>

<span data-ttu-id="9155c-119">이 예제에서는 **Server02** 이라는 컴퓨터에 연결 된 CIM 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-119">This example gets the CIM sessions that are connected to the computer named **Server02**.</span></span>

```powershell
Get-CimSession -ComputerName Server02
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="9155c-120">예 3: CIM 세션 목록을 가져온 다음 목록의 서식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-120">Example 3: Get a list of CIM sessions and then format the list</span></span>

<span data-ttu-id="9155c-121">이 예에서는 현재 PowerShell 세션의 모든 CIM 세션을 가져오고 **ComputerName** 및 **InstanceID** 속성만 포함 하는 테이블을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-121">This example gets all CIM sessions in the current PowerShell session and displays a table containing only the **ComputerName** and **InstanceID** properties.</span></span>

```powershell
Get-CimSession | Format-Table -Property ComputerName,InstanceId
```

```Output
ComputerName InstanceId
------------ ----------
Server01     d1413bc3-162a-4cb8-9aec-4d2c61253d59
Server02     c0095981-52c5-4e7f-a5bb-c4c680541710
```

### <span data-ttu-id="9155c-122">예제 4: 특정 이름을 가진 모든 CIM 세션 가져오기</span><span class="sxs-lookup"><span data-stu-id="9155c-122">Example 4: Get all the CIM sessions that have specific names</span></span>

<span data-ttu-id="9155c-123">이 예제에서는 이름이 **serv** 로 시작 하는 모든 CIM 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-123">This example gets all CIM sessions that have names that begin with **serv**.</span></span>

```powershell
Get-CimSession -ComputerName Serv*
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="9155c-124">예 5: 특정 CIM 세션 가져오기</span><span class="sxs-lookup"><span data-stu-id="9155c-124">Example 5: Get a specific CIM session</span></span>

<span data-ttu-id="9155c-125">이 예제에서는 **Id** 가 2 인 CIM 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-125">This example gets the CIM session that has an **Id** of 2.</span></span>

```powershell
Get-CimSession -ID 2
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

## <span data-ttu-id="9155c-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9155c-126">PARAMETERS</span></span>

### <span data-ttu-id="9155c-127">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="9155c-127">-ComputerName</span></span>

<span data-ttu-id="9155c-128">연결 된 CIM 세션을 가져올 컴퓨터의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-128">Specifies the name of the computer to get CIM sessions connected to.</span></span> <span data-ttu-id="9155c-129">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-129">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="9155c-130">-Id</span><span class="sxs-lookup"><span data-stu-id="9155c-130">-Id</span></span>

<span data-ttu-id="9155c-131">가져올 CIM 세션의 식별자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-131">Specifies the identifier of the CIM session to get.</span></span> <span data-ttu-id="9155c-132">여러 Id의 경우 쉼표를 사용 하 여 Id를 구분 하거나 범위 연산자 ()를 사용 하 여 `..` id 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-132">For multiple IDs, use commas to separate the IDs or use the range operator (`..`) to specify a range of IDs.</span></span> <span data-ttu-id="9155c-133">**Id** 는 현재 PowerShell 세션 내에서 CIM 세션을 고유 하 게 식별 하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-133">An **Id** is an integer that uniquely identifies the CIM session within the current PowerShell session.</span></span>

<span data-ttu-id="9155c-134">범위 연산자에 대 한 자세한 내용은 [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9155c-134">For more information about the range operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span></span>

```yaml
Type: System.UInt32[]
Parameter Sets: SessionIdSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9155c-135">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="9155c-135">-InstanceId</span></span>

<span data-ttu-id="9155c-136">가져올 CIM 세션의 인스턴스 Id를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-136">Specifies the instance IDs of the CIM session to get.</span></span>

<span data-ttu-id="9155c-137">**InstanceId** 는 CIM 세션을 고유 하 게 식별 하는 guid (globally unique identifier)입니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-137">**InstanceId** is a globally-unique identifier (GUID) that uniquely identifies a CIM session.</span></span> <span data-ttu-id="9155c-138">**InstanceId** 는 PowerShell에서 여러 세션을 실행 하는 경우에도 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-138">The **InstanceId** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="9155c-139">**Instanceid** 는 CIM 세션을 나타내는 개체의 **instanceid** 속성에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-139">The **InstanceId** is stored in the **InstanceId** property of the object that represents a CIM session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9155c-140">-Name</span><span class="sxs-lookup"><span data-stu-id="9155c-140">-Name</span></span>

<span data-ttu-id="9155c-141">지정 된 이름을 포함 하는 CIM 세션을 하나 이상 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-141">Gets one or more CIM sessions which contain the specified friendly names.</span></span> <span data-ttu-id="9155c-142">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9155c-142">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="9155c-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9155c-143">CommonParameters</span></span>
<span data-ttu-id="9155c-144">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9155c-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9155c-145">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9155c-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9155c-146">입력</span><span class="sxs-lookup"><span data-stu-id="9155c-146">INPUTS</span></span>

### <span data-ttu-id="9155c-147">없음</span><span class="sxs-lookup"><span data-stu-id="9155c-147">None</span></span>

## <span data-ttu-id="9155c-148">출력</span><span class="sxs-lookup"><span data-stu-id="9155c-148">OUTPUTS</span></span>

### <span data-ttu-id="9155c-149">Microsoft.Management.Infrastructure.CimSession</span><span class="sxs-lookup"><span data-stu-id="9155c-149">Microsoft.Management.Infrastructure.CimSession</span></span>

## <span data-ttu-id="9155c-150">참고</span><span class="sxs-lookup"><span data-stu-id="9155c-150">NOTES</span></span>

## <span data-ttu-id="9155c-151">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9155c-151">RELATED LINKS</span></span>

[<span data-ttu-id="9155c-152">Format-Table</span><span class="sxs-lookup"><span data-stu-id="9155c-152">Format-Table</span></span>](../microsoft.powershell.utility/format-table.md)

[<span data-ttu-id="9155c-153">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="9155c-153">New-CimSession</span></span>](New-CimSession.md)

[<span data-ttu-id="9155c-154">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="9155c-154">Remove-CimSession</span></span>](remove-cimsession.md)

[<span data-ttu-id="9155c-155">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="9155c-155">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)

