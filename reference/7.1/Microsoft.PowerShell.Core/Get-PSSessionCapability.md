---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessioncapability?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionCapability
ms.openlocfilehash: 891c62692ce694e7e7238814a4dc30da59f7c98a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217673"
---
# <span data-ttu-id="9bd84-103">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="9bd84-103">Get-PSSessionCapability</span></span>

## <span data-ttu-id="9bd84-104">개요</span><span class="sxs-lookup"><span data-stu-id="9bd84-104">SYNOPSIS</span></span>
<span data-ttu-id="9bd84-105">제한 된 세션 구성에 대 한 특정 사용자의 기능을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9bd84-105">Gets the capabilities of a specific user on a constrained session configuration.</span></span>

## <span data-ttu-id="9bd84-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9bd84-106">SYNTAX</span></span>

```
Get-PSSessionCapability [-ConfigurationName] <String> [-Username] <String> [-Full] [<CommonParameters>]
```

## <span data-ttu-id="9bd84-107">설명</span><span class="sxs-lookup"><span data-stu-id="9bd84-107">DESCRIPTION</span></span>

<span data-ttu-id="9bd84-108">**Get PSSessionCapability** cmdlet은 제한 된 세션 구성에 대 한 특정 사용자의 기능을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9bd84-108">The **Get-PSSessionCapability** cmdlet gets the capabilities of a specific user on a constrained session configuration.</span></span>
<span data-ttu-id="9bd84-109">이 cmdlet을 사용 하 여 사용자에 대 한 사용자 지정 세션 구성을 감사 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd84-109">Use this cmdlet to audit customized session configurations for users.</span></span>

<span data-ttu-id="9bd84-110">Windows PowerShell 5.0부터 세션 구성 파일 (.psc)의 **Roledefinitions** 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd84-110">Starting in Windows PowerShell 5.0, you can use the **RoleDefinitions** property in a session configuration (.pssc) file.</span></span>
<span data-ttu-id="9bd84-111">이 속성을 사용 하면 그룹 멤버 자격에 따라 제한 된 단일 끝점에 대 한 다양 한 기능을 사용자에 게 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd84-111">Using this property lets you grant users different capabilities on a single constrained endpoint based on group membership.</span></span>
<span data-ttu-id="9bd84-112">**Get PSSessionCapability** cmdlet은 사용자에 게 부여 된 정확한 기능을 확인할 수 있도록 허용 하 여 이러한 끝점을 감사할 때 복잡성을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="9bd84-112">The **Get-PSSessionCapability** cmdlet reduces complexity when auditing these endpoints by letting you determine the exact capabilities granted to a user.</span></span>

<span data-ttu-id="9bd84-113">기본적으로 **Get PSSessionCapability** cmdlet은 지정 된 사용자가 지정 된 끝점에서 실행할 수 있는 명령 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd84-113">By default, the **Get-PSSessionCapability** cmdlet returns a list of commands the specified user can run in the specified endpoint.</span></span>
<span data-ttu-id="9bd84-114">이는 지정 된 끝점에서 **Get 명령을** 실행 하는 사용자와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd84-114">This is equivalent to the user running **Get-Command** in the specified endpoint.</span></span>
<span data-ttu-id="9bd84-115">*Full* 매개 변수를 사용 하 여 실행 하는 경우이 Cmdlet은 **InitialSessionState** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd84-115">When run with the *Full* parameter, this cmdlet returns an **InitialSessionState** object.</span></span>
<span data-ttu-id="9bd84-116">이 개체에는 지정 된 끝점에 대해 지정 된 사용자가 상호 작용 하는 PowerShell runspace에 대 한 세부 정보가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bd84-116">This object contains details about the PowerShell runspace the specified user would interact with for the specified endpoint.</span></span>
<span data-ttu-id="9bd84-117">여기에는 언어 모드, 실행 정책, 환경 변수 등의 정보가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bd84-117">It includes information such as Language Mode, Execution Policy, and Environmental Variables.</span></span>

## <span data-ttu-id="9bd84-118">예제</span><span class="sxs-lookup"><span data-stu-id="9bd84-118">EXAMPLES</span></span>

### <span data-ttu-id="9bd84-119">예제 1: 사용자에 대해 사용할 수 있는 명령 가져오기</span><span class="sxs-lookup"><span data-stu-id="9bd84-119">Example 1: Get commands available for a user</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User'
```

<span data-ttu-id="9bd84-120">이 예에서는 로컬 컴퓨터의 Endpoint1 제약 된 끝점에 연결할 때 사용자 CONTOSO\User에 사용할 수 있는 명령을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd84-120">This example returns the commands available to the user CONTOSO\User when connecting to the Endpoint1 constrained endpoint on the local computer.</span></span>

### <span data-ttu-id="9bd84-121">예제 2: 사용자에 대 한 runspace에 대 한 세부 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="9bd84-121">Example 2: Get details about a runspace for a user</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User' -Full
```

<span data-ttu-id="9bd84-122">이 예에서는 Endpoint1 제약 된 끝점에 연결할 때 사용자 CONTOSO\User가 상호 작용 하는 runspace에 대 한 세부 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd84-122">This example returns details about the runspace the user CONTOSO\User would interact with when connecting to the Endpoint1 constrained endpoint.</span></span>

## <span data-ttu-id="9bd84-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9bd84-123">PARAMETERS</span></span>

### <span data-ttu-id="9bd84-124">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="9bd84-124">-ConfigurationName</span></span>

<span data-ttu-id="9bd84-125">검사 하 고 있는 제한 된 세션 구성 (끝점)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd84-125">Specifies the constrained session configuration (endpoint) that you are inspecting.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9bd84-126">-Full</span><span class="sxs-lookup"><span data-stu-id="9bd84-126">-Full</span></span>

<span data-ttu-id="9bd84-127">이 cmdlet이 지정 된 제한 된 끝점에서 지정 된 사용자에 대 한 전체 초기 세션 상태를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9bd84-127">Indicates that this cmdlet returns the entire initial session state for the specified user at the specified constrained endpoint.</span></span>

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

### <span data-ttu-id="9bd84-128">-Username</span><span class="sxs-lookup"><span data-stu-id="9bd84-128">-Username</span></span>

<span data-ttu-id="9bd84-129">검사 하 고 있는 기능의 사용자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd84-129">Specifies the user whose capabilities you are inspecting.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9bd84-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9bd84-130">CommonParameters</span></span>

<span data-ttu-id="9bd84-131">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9bd84-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9bd84-132">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9bd84-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9bd84-133">입력</span><span class="sxs-lookup"><span data-stu-id="9bd84-133">INPUTS</span></span>

## <span data-ttu-id="9bd84-134">출력</span><span class="sxs-lookup"><span data-stu-id="9bd84-134">OUTPUTS</span></span>

### <span data-ttu-id="9bd84-135">System.management.automation.aliasinfo.</span><span class="sxs-lookup"><span data-stu-id="9bd84-135">System.Management.Automation.AliasInfo</span></span>

### <span data-ttu-id="9bd84-136">System.object를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd84-136">System.Management.Automation.FunctionInfo</span></span>

### <span data-ttu-id="9bd84-137">System.Management.Automation.Runspaces.InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="9bd84-137">System.Management.Automation.Runspaces.InitialSessionState</span></span>

## <span data-ttu-id="9bd84-138">참고</span><span class="sxs-lookup"><span data-stu-id="9bd84-138">NOTES</span></span>

## <span data-ttu-id="9bd84-139">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9bd84-139">RELATED LINKS</span></span>

[<span data-ttu-id="9bd84-140">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="9bd84-140">New-PSRoleCapabilityFile</span></span>](New-PSRoleCapabilityFile.md)

