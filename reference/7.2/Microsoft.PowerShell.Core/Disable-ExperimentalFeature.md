---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-experimentalfeature?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ExperimentalFeature
ms.openlocfilehash: 47cae5d0c3ddd1800e5a8ae33282677773dc50d5
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195168"
---
# <span data-ttu-id="e8739-102">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="e8739-102">Disable-ExperimentalFeature</span></span>

## <span data-ttu-id="e8739-103">개요</span><span class="sxs-lookup"><span data-stu-id="e8739-103">SYNOPSIS</span></span>
<span data-ttu-id="e8739-104">PowerShell의 새 인스턴스를 시작할 때 실험적 기능을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8739-104">Disable an experimental feature on startup of new instance of PowerShell.</span></span>

## <span data-ttu-id="e8739-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e8739-105">SYNTAX</span></span>

```
Disable-ExperimentalFeature [-Name] <String[]> [-Scope <ConfigScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e8739-106">설명</span><span class="sxs-lookup"><span data-stu-id="e8739-106">DESCRIPTION</span></span>

<span data-ttu-id="e8739-107">`Disable-ExperimentalFeature`Cmdlet은 `powershell.config.json` PowerShell 시작 시 읽은 설정 파일에서 명명 된 실험적 기능을 제거 하 여 실험적 기능을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8739-107">The `Disable-ExperimentalFeature` cmdlet disables experimental features by removing the named experimental features from the `powershell.config.json` settings file read on PowerShell startup.</span></span>

<span data-ttu-id="e8739-108">이 cmdlet은 PowerShell 6.2에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8739-108">This cmdlet was introduced in PowerShell 6.2.</span></span>

> [!NOTE]
> <span data-ttu-id="e8739-109">실험적 기능 상태에 대 한 변경 내용은 PowerShell을 다시 시작 하는 경우에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8739-109">Any changes to experimental feature state only takes effect on restart of PowerShell</span></span>

## <span data-ttu-id="e8739-110">예제</span><span class="sxs-lookup"><span data-stu-id="e8739-110">EXAMPLES</span></span>

### <span data-ttu-id="e8739-111">예제 1: 실험적 기능 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="e8739-111">Example 1: Disable an experimental feature</span></span>

<span data-ttu-id="e8739-112">이 예에서는 이전에이 실험적 기능을 사용 하도록 설정한 경우 `powershell.config.json` PowerShell이 다시 시작 되 면 사용자가 해당 기능을 사용 하도록 설정 하지 않도록 파일이 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8739-112">In this example, if this experimental feature was previously enabled, then the `powershell.config.json` file is updated for the user to not enable that feature once PowerShell is restarted.</span></span>
<span data-ttu-id="e8739-113">성공 하면 파이프라인이 파이프라인으로 출력 되지 않고 경고 메시지만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8739-113">Upon success nothing is output to the pipeline and only a warning message is displayed.</span></span>

```powershell
PS C:\> Disable-ExperimentalFeature PSImplicitRemotingBatching
```

```Output
WARNING: Enabling and disabling experimental features do not take effect until next start of PowerShell.
```

## <span data-ttu-id="e8739-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e8739-114">PARAMETERS</span></span>

### <span data-ttu-id="e8739-115">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e8739-115">-Confirm</span></span>

<span data-ttu-id="e8739-116">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="e8739-116">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8739-117">-Name</span><span class="sxs-lookup"><span data-stu-id="e8739-117">-Name</span></span>

<span data-ttu-id="e8739-118">사용 하지 않도록 설정할 실험적 기능의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e8739-118">The name or names of the experimental features to disable.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e8739-119">-범위</span><span class="sxs-lookup"><span data-stu-id="e8739-119">-Scope</span></span>

<span data-ttu-id="e8739-120">`powershell.config.json`모든 사용자에 게 영향을 주는지 아니면 현재 사용자 에게만 영향을 주는지 여부를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8739-120">Determines which `powershell.config.json` to update whether it affects all users or just the current user.</span></span>

```yaml
Type: System.Management.Automation.Configuration.ConfigScope
Parameter Sets: (All)
Aliases:
Accepted values: AllUsers, CurrentUser

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8739-121">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e8739-121">-WhatIf</span></span>

<span data-ttu-id="e8739-122">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e8739-122">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e8739-123">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8739-123">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8739-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e8739-124">CommonParameters</span></span>

<span data-ttu-id="e8739-125">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e8739-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e8739-126">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8739-126">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e8739-127">입력</span><span class="sxs-lookup"><span data-stu-id="e8739-127">INPUTS</span></span>

### <span data-ttu-id="e8739-128">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="e8739-128">ExperimentalFeature</span></span>

<span data-ttu-id="e8739-129">Cmdlet에서 ExperimentalFeature의 파이프 인스턴스 `Get-ExperimentalFeature` 를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8739-129">Pipe instances of ExperimentalFeature from `Get-ExperimentalFeature` cmdlet to disable.</span></span>

## <span data-ttu-id="e8739-130">출력</span><span class="sxs-lookup"><span data-stu-id="e8739-130">OUTPUTS</span></span>

### <span data-ttu-id="e8739-131">None</span><span class="sxs-lookup"><span data-stu-id="e8739-131">None</span></span>

<span data-ttu-id="e8739-132">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8739-132">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="e8739-133">참고</span><span class="sxs-lookup"><span data-stu-id="e8739-133">NOTES</span></span>

<span data-ttu-id="e8739-134">실험적 기능의 상태 변경은 PowerShell을 다시 시작 하는 경우에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8739-134">Changes to state of an experimental feature only take effect on restart of PowerShell.</span></span>

## <span data-ttu-id="e8739-135">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e8739-135">RELATED LINKS</span></span>

[<span data-ttu-id="e8739-136">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="e8739-136">Enable-ExperimentalFeature</span></span>](Enable-ExperimentalFeature.md)

[<span data-ttu-id="e8739-137">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="e8739-137">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

