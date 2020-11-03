---
external help file: Get-DSCConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfiguration
ms.openlocfilehash: 42b24e72de4c4bcc9326d52861c08a05853b18e0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215354"
---
# <span data-ttu-id="cb03a-103">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb03a-103">Get-DscConfiguration</span></span>

## <span data-ttu-id="cb03a-104">개요</span><span class="sxs-lookup"><span data-stu-id="cb03a-104">SYNOPSIS</span></span>
<span data-ttu-id="cb03a-105">노드의 현재 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-105">Gets the current configuration of the nodes.</span></span>

## <span data-ttu-id="cb03a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cb03a-106">SYNTAX</span></span>

```
Get-DscConfiguration [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [<CommonParameters>]
```

## <span data-ttu-id="cb03a-107">설명</span><span class="sxs-lookup"><span data-stu-id="cb03a-107">DESCRIPTION</span></span>
<span data-ttu-id="cb03a-108">Start-dscconfiguration cmdlet은 노드의 현재 구성 (구성이 있는 경우 **)** 을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-108">The **Get-DscConfiguration** cmdlet gets the current configuration of the nodes, if the configuration exists.</span></span>
<span data-ttu-id="cb03a-109">CIM(Common Information Model) 세션을 사용하여 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-109">Specify computers by using Common Information Model (CIM) sessions.</span></span>
<span data-ttu-id="cb03a-110">대상 컴퓨터를 지정하지 않으면 cmdlet이 로컬 컴퓨터의 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-110">If you do not specify a target computer, the cmdlet gets the configuration from the local computer.</span></span>

## <span data-ttu-id="cb03a-111">예제</span><span class="sxs-lookup"><span data-stu-id="cb03a-111">EXAMPLES</span></span>

### <span data-ttu-id="cb03a-112">예 1: 로컬 컴퓨터에 대 한 구성 가져오기</span><span class="sxs-lookup"><span data-stu-id="cb03a-112">Example 1: Get the configuration for the local computer</span></span>

```
PS C:\> Get-DscConfiguration
```

<span data-ttu-id="cb03a-113">이 명령은 로컬 컴퓨터의 현재 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-113">This command gets the current state for the local computer.</span></span>

### <span data-ttu-id="cb03a-114">예 2: 지정 된 컴퓨터에 대 한 구성 가져오기</span><span class="sxs-lookup"><span data-stu-id="cb03a-114">Example 2: Get the configuration for a specified computer</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Get-DscConfiguration -CimSession $Session
```

<span data-ttu-id="cb03a-115">이 예제에서는 CIM 세션에 지정 된 컴퓨터에서 현재 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-115">This example gets the current state from a computer specified by a CIM session.</span></span>
<span data-ttu-id="cb03a-116">또한 cmdlet에 사용하기 위해 이름이 Server01인 컴퓨터에 대한 CIM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-116">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="cb03a-117">또는 지정한 여러 컴퓨터에 cmdlet을 적용하기 위해 CIM 세션 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-117">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="cb03a-118">첫 번째 명령은 **New-CimSession** cmdlet을 사용하여 CIM 세션을 만든 다음 **CimSession** 개체를 **$Session** 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-118">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the **$Session** variable.</span></span>
<span data-ttu-id="cb03a-119">또한 암호를 입력하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-119">The command prompts you for a password.</span></span>
<span data-ttu-id="cb03a-120">자세한 내용을 보려면 `Get-Help New-CimSession`를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="cb03a-120">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="cb03a-121">두 번째 명령은 **$Session** 변수에 저장된 **CimSession** 개체로 식별된 컴퓨터(이 경우 이름이 $Server01인 컴퓨터)의 현재 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-121">The second command gets the current configuration for the computers identified by the **CimSession** objects stored in the **$Session** variable, in this case, the computer named Server01.</span></span>

## <span data-ttu-id="cb03a-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cb03a-122">PARAMETERS</span></span>

### <span data-ttu-id="cb03a-123">-AsJob</span><span class="sxs-lookup"><span data-stu-id="cb03a-123">-AsJob</span></span>
<span data-ttu-id="cb03a-124">이 cmdlet이 명령을 백그라운드 작업으로 실행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-124">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="cb03a-125">-CimSession</span><span class="sxs-lookup"><span data-stu-id="cb03a-125">-CimSession</span></span>
<span data-ttu-id="cb03a-126">원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-126">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="cb03a-127">[CimSession](/powershell/module/cimcmdlets/new-cimsession) 또는 [CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet의 출력과 같은 컴퓨터 이름 또는 세션 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-127">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="cb03a-128">기본값은 로컬 컴퓨터의 현재 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-128">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb03a-129">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="cb03a-129">-ThrottleLimit</span></span>
<span data-ttu-id="cb03a-130">cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-130">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="cb03a-131">이 매개 변수를 생략 하거나 값을 `0` 입력 하면 Windows PowerShell은 컴퓨터에서 실행 되는 CIM cmdlet의 수에 따라 cmdlet에 대 한 최적의 스로틀 제한을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-131">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="cb03a-132">스로틀 제한은 현재 cmdlet에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb03a-132">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb03a-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cb03a-133">CommonParameters</span></span>
<span data-ttu-id="cb03a-134">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cb03a-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cb03a-135">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb03a-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cb03a-136">입력</span><span class="sxs-lookup"><span data-stu-id="cb03a-136">INPUTS</span></span>

## <span data-ttu-id="cb03a-137">출력</span><span class="sxs-lookup"><span data-stu-id="cb03a-137">OUTPUTS</span></span>

## <span data-ttu-id="cb03a-138">참고</span><span class="sxs-lookup"><span data-stu-id="cb03a-138">NOTES</span></span>

## <span data-ttu-id="cb03a-139">관련 링크</span><span class="sxs-lookup"><span data-stu-id="cb03a-139">RELATED LINKS</span></span>

[<span data-ttu-id="cb03a-140">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="cb03a-140">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="cb03a-141">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="cb03a-141">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="cb03a-142">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb03a-142">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="cb03a-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb03a-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="cb03a-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb03a-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
