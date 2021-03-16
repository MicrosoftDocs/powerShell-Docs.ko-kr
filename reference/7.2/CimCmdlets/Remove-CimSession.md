---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimSession
ms.openlocfilehash: a3ff2132c531df1ab19bf7149a55ea0df4a787a8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600622"
---
# <span data-ttu-id="66ab2-102">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="66ab2-102">Remove-CimSession</span></span>

## <span data-ttu-id="66ab2-103">개요</span><span class="sxs-lookup"><span data-stu-id="66ab2-103">SYNOPSIS</span></span>
<span data-ttu-id="66ab2-104">하나 이상의 CIM 세션을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-104">Removes one or more CIM sessions.</span></span>

## <span data-ttu-id="66ab2-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="66ab2-105">SYNTAX</span></span>

### <span data-ttu-id="66ab2-106">CimSessionSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="66ab2-106">CimSessionSet (Default)</span></span>

```
Remove-CimSession [-CimSession] <CimSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="66ab2-107">ComputerNameSet</span><span class="sxs-lookup"><span data-stu-id="66ab2-107">ComputerNameSet</span></span>

```
Remove-CimSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="66ab2-108">SessionIdSet</span><span class="sxs-lookup"><span data-stu-id="66ab2-108">SessionIdSet</span></span>

```
Remove-CimSession [-Id] <UInt32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="66ab2-109">InstanceIdSet</span><span class="sxs-lookup"><span data-stu-id="66ab2-109">InstanceIdSet</span></span>

```
Remove-CimSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="66ab2-110">NameSet</span><span class="sxs-lookup"><span data-stu-id="66ab2-110">NameSet</span></span>

```
Remove-CimSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="66ab2-111">설명</span><span class="sxs-lookup"><span data-stu-id="66ab2-111">DESCRIPTION</span></span>

<span data-ttu-id="66ab2-112">`Remove-CimSession`Cmdlet은 로컬 PowerShell 세션에서 CIM 세션 개체를 하나 이상 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-112">The `Remove-CimSession` cmdlet removes one or more CIM session objects from the local PowerShell session.</span></span>

## <span data-ttu-id="66ab2-113">예제</span><span class="sxs-lookup"><span data-stu-id="66ab2-113">EXAMPLES</span></span>

### <span data-ttu-id="66ab2-114">예제 1: 모든 CIM 세션 제거</span><span class="sxs-lookup"><span data-stu-id="66ab2-114">Example 1: Remove all the CIM sessions</span></span>

<span data-ttu-id="66ab2-115">이 예제에서는 [CimSession](Get-CimSession.md) cmdlet을 사용 하 여 로컬 컴퓨터에서 사용 가능한 모든 CIM 세션을 검색 한 다음를 사용 하 여 제거 합니다 `Remove-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="66ab2-115">This example retrieves all the available CIM sessions on the local computer using the [Get-CimSession](Get-CimSession.md) cmdlet, and then removes them using the `Remove-CimSession`.</span></span>

```powershell
Get-CimSession | Remove-CimSession
```

### <span data-ttu-id="66ab2-116">예 2: 특정 CIM 세션 제거</span><span class="sxs-lookup"><span data-stu-id="66ab2-116">Example 2: Remove a specific CIM session</span></span>

<span data-ttu-id="66ab2-117">이 예에서는 **Id** 값이 5 인 CIM 세션을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-117">This example removes the CIM session that has an **Id** value of 5.</span></span>

```powershell
Remove-CimSession -Id 5
```

### <span data-ttu-id="66ab2-118">예제 3: WhatIf 매개 변수를 사용 하 여 제거할 CIM 세션 목록 표시</span><span class="sxs-lookup"><span data-stu-id="66ab2-118">Example 3: Show the list of CIM sessions to remove by using the WhatIf parameter</span></span>

<span data-ttu-id="66ab2-119">이 예제에서는 일반 매개 변수 **WhatIf** 를 사용 하 여 제거를 수행 하지 않도록 지정 하지만 완료 된 경우에만 발생 하는 결과를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-119">This example uses the common parameter **WhatIf** to specify that the removal should not be done, but only output what would happen if it were done.</span></span>

```powershell
Remove-CimSession -Name a* -WhatIf
```

## <span data-ttu-id="66ab2-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="66ab2-120">PARAMETERS</span></span>

### <span data-ttu-id="66ab2-121">-CimSession</span><span class="sxs-lookup"><span data-stu-id="66ab2-121">-CimSession</span></span>

<span data-ttu-id="66ab2-122">종료할 CIM 세션의 세션 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-122">Specifies the session objects of the CIM sessions to close.</span></span>

<span data-ttu-id="66ab2-123">CIM 세션을 포함 하는 변수 또는 CIM 세션을 만들거나 가져오는 명령 (예: 또는 cmdlet)을 입력 합니다 [`New-CimSession`](New-CimSession.md) [`Get-CimSession`](Get-CimSession.md) .</span><span class="sxs-lookup"><span data-stu-id="66ab2-123">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the [`New-CimSession`](New-CimSession.md) or [`Get-CimSession`](Get-CimSession.md) cmdlets.</span></span>
<span data-ttu-id="66ab2-124">자세한 내용은 [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66ab2-124">For more information, see [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="66ab2-125">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="66ab2-125">-ComputerName</span></span>

<span data-ttu-id="66ab2-126">컴퓨터 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-126">Specifies an array of names of computers.</span></span> <span data-ttu-id="66ab2-127">지정 된 컴퓨터에 연결 되는 세션을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-127">Removes the sessions that connect to the specified computers.</span></span> <span data-ttu-id="66ab2-128">FQDN (정규화 된 도메인 이름) 또는 NetBIOS 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-128">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="66ab2-129">-Id</span><span class="sxs-lookup"><span data-stu-id="66ab2-129">-Id</span></span>

<span data-ttu-id="66ab2-130">제거할 CIM 세션의 ID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-130">Specifies the ID of the CIM session to remove.</span></span> <span data-ttu-id="66ab2-131">하나 이상의 Id를 쉼표로 구분 하 여 지정 하거나 범위 연산자 ()를 사용 `..` 하 여 id 범위를 지정 하십시오.</span><span class="sxs-lookup"><span data-stu-id="66ab2-131">Specify one or more IDs separated by commas, or use the range operator (`..`) to specify a range of IDs.</span></span> <span data-ttu-id="66ab2-132">**Id** 는 현재 PowerShell 세션에서 CIM 세션을 고유 하 게 식별 하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-132">An **Id** is an integer that uniquely identifies the CIM session in the current PowerShell session.</span></span>

<span data-ttu-id="66ab2-133">범위 연산자에 대 한 자세한 내용은 [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66ab2-133">For more information about the range operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span></span>

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

### <span data-ttu-id="66ab2-134">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="66ab2-134">-InstanceId</span></span>

<span data-ttu-id="66ab2-135">제거할 CIM 세션의 인스턴스 ID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-135">Specifies the instance ID of the CIM session to remove.</span></span> <span data-ttu-id="66ab2-136">**InstanceId** 는 CIM 세션을 고유 하 게 식별 하는 Guid (Globally Unique Identifier)입니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-136">**InstanceId** is a Globally Unique Identifier (GUID) that uniquely identifies a CIM session.</span></span> <span data-ttu-id="66ab2-137">**InstanceId** 는 PowerShell에서 여러 세션을 실행 하는 경우에도 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-137">The **InstanceId** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="66ab2-138">**Instanceid** 는 CIM 세션을 나타내는 개체의 **instanceid** 속성에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-138">The **InstanceId** is stored in the **InstanceId** property of the object that represents a CIM session.</span></span>

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

### <span data-ttu-id="66ab2-139">-Name</span><span class="sxs-lookup"><span data-stu-id="66ab2-139">-Name</span></span>

<span data-ttu-id="66ab2-140">제거할 CIM 세션의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-140">Specifies the friendly name of the CIM session to remove.</span></span> <span data-ttu-id="66ab2-141">이 매개 변수와 함께 와일드 카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-141">You can use wildcard characters with this parameter.</span></span>

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

### <span data-ttu-id="66ab2-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="66ab2-142">-Confirm</span></span>

<span data-ttu-id="66ab2-143">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="66ab2-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="66ab2-144">-WhatIf</span></span>

<span data-ttu-id="66ab2-145">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-145">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="66ab2-146">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="66ab2-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="66ab2-147">CommonParameters</span></span>

<span data-ttu-id="66ab2-148">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="66ab2-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="66ab2-149">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66ab2-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="66ab2-150">입력</span><span class="sxs-lookup"><span data-stu-id="66ab2-150">INPUTS</span></span>

### <span data-ttu-id="66ab2-151">없음</span><span class="sxs-lookup"><span data-stu-id="66ab2-151">None</span></span>

<span data-ttu-id="66ab2-152">이 cmdlet은 입력 개체를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-152">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="66ab2-153">출력</span><span class="sxs-lookup"><span data-stu-id="66ab2-153">OUTPUTS</span></span>

### <span data-ttu-id="66ab2-154">System.Object</span><span class="sxs-lookup"><span data-stu-id="66ab2-154">System.Object</span></span>

<span data-ttu-id="66ab2-155">이 cmdlet은 CIM 세션 정보를 포함 하는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab2-155">This cmdlet returns an object that contains CIM session information.</span></span>

## <span data-ttu-id="66ab2-156">참고</span><span class="sxs-lookup"><span data-stu-id="66ab2-156">NOTES</span></span>

## <span data-ttu-id="66ab2-157">관련 링크</span><span class="sxs-lookup"><span data-stu-id="66ab2-157">RELATED LINKS</span></span>

[<span data-ttu-id="66ab2-158">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="66ab2-158">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="66ab2-159">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="66ab2-159">New-CimSession</span></span>](New-CimSession.md)

[<span data-ttu-id="66ab2-160">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="66ab2-160">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)
