---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-runspacedebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-RunspaceDebug
ms.openlocfilehash: 589c8cb36a91de510ffc30973fe70729700ad020
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602672"
---
# <span data-ttu-id="97e17-102">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="97e17-102">Disable-RunspaceDebug</span></span>

## <span data-ttu-id="97e17-103">개요</span><span class="sxs-lookup"><span data-stu-id="97e17-103">SYNOPSIS</span></span>
<span data-ttu-id="97e17-104">하나 이상의 runspace에서 디버깅을 사용 하지 않도록 설정 하 고 보류 중인 모든 디버거 중지를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="97e17-104">Disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="97e17-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="97e17-105">SYNTAX</span></span>

### <span data-ttu-id="97e17-106">RunspaceNameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="97e17-106">RunspaceNameParameterSet (Default)</span></span>

```
Disable-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="97e17-107">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="97e17-107">RunspaceParameterSet</span></span>

```
Disable-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="97e17-108">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="97e17-108">RunspaceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="97e17-109">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="97e17-109">RunspaceInstanceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="97e17-110">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="97e17-110">ProcessNameParameterSet</span></span>

```
Disable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="97e17-111">설명</span><span class="sxs-lookup"><span data-stu-id="97e17-111">DESCRIPTION</span></span>

<span data-ttu-id="97e17-112">`Disable-RunspaceDebug`이 cmdlet은 하나 이상의 runspace에서 디버깅을 사용 하지 않도록 설정 하 고 보류 중인 모든 디버거 중지를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="97e17-112">The `Disable-RunspaceDebug` cmdlet disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="97e17-113">예제</span><span class="sxs-lookup"><span data-stu-id="97e17-113">EXAMPLES</span></span>

### <span data-ttu-id="97e17-114">1: 기본 runspace 디버거를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="97e17-114">1: Disable the default runspace debugger</span></span>

```powershell
Disable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="97e17-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="97e17-115">PARAMETERS</span></span>

### <span data-ttu-id="97e17-116">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="97e17-116">-AppDomainName</span></span>

<span data-ttu-id="97e17-117">PowerShell runspace를 호스트 하는 응용 프로그램 도메인의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="97e17-117">The name of the application domain that hosts the PowerShell runspace.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97e17-118">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="97e17-118">-ProcessName</span></span>

<span data-ttu-id="97e17-119">PowerShell runspace를 호스트 하는 프로세스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="97e17-119">The name of the process that hosts the PowerShell runspace.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97e17-120">-Runspace</span><span class="sxs-lookup"><span data-stu-id="97e17-120">-Runspace</span></span>

<span data-ttu-id="97e17-121">사용할 하나 이상의 **Runspace** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="97e17-121">One or more **Runspace** objects to be disabled.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.Runspace[]
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="97e17-122">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="97e17-122">-RunspaceId</span></span>

<span data-ttu-id="97e17-123">하나 이상의 **Runspace** Id 번호를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97e17-123">One or more **Runspace** Id numbers to be disabled.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: RunspaceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97e17-124">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="97e17-124">-RunspaceInstanceId</span></span>

<span data-ttu-id="97e17-125">하나 이상의 **Runspace** guid를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97e17-125">One or more **Runspace** GUIDs to be disabled.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: RunspaceInstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97e17-126">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="97e17-126">-RunspaceName</span></span>

<span data-ttu-id="97e17-127">사용할 하나 이상의 **Runspace** 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="97e17-127">One or more **Runspace** names to be disabled.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RunspaceNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97e17-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="97e17-128">CommonParameters</span></span>

<span data-ttu-id="97e17-129">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="97e17-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="97e17-130">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97e17-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="97e17-131">입력</span><span class="sxs-lookup"><span data-stu-id="97e17-131">INPUTS</span></span>

## <span data-ttu-id="97e17-132">출력</span><span class="sxs-lookup"><span data-stu-id="97e17-132">OUTPUTS</span></span>

## <span data-ttu-id="97e17-133">참고</span><span class="sxs-lookup"><span data-stu-id="97e17-133">NOTES</span></span>

## <span data-ttu-id="97e17-134">관련 링크</span><span class="sxs-lookup"><span data-stu-id="97e17-134">RELATED LINKS</span></span>

[<span data-ttu-id="97e17-135">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="97e17-135">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

[<span data-ttu-id="97e17-136">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="97e17-136">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)

