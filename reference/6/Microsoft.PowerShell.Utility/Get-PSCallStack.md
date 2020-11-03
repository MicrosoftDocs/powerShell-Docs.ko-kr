---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-pscallstack?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSCallStack
ms.openlocfilehash: 0052543842f97dc1a19caae15222fd1b97d49902
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209128"
---
# <span data-ttu-id="ff1a5-103">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="ff1a5-103">Get-PSCallStack</span></span>

## <span data-ttu-id="ff1a5-104">개요</span><span class="sxs-lookup"><span data-stu-id="ff1a5-104">SYNOPSIS</span></span>
<span data-ttu-id="ff1a5-105">현재 호출 스택을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ff1a5-105">Displays the current call stack.</span></span>

## <span data-ttu-id="ff1a5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ff1a5-106">SYNTAX</span></span>

```
Get-PSCallStack [<CommonParameters>]
```

## <span data-ttu-id="ff1a5-107">설명</span><span class="sxs-lookup"><span data-stu-id="ff1a5-107">DESCRIPTION</span></span>

<span data-ttu-id="ff1a5-108">**Get PSCallStack** cmdlet은 현재 호출 스택을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff1a5-108">The **Get-PSCallStack** cmdlet displays the current call stack.</span></span>

<span data-ttu-id="ff1a5-109">이 cmdlet은 PowerShell 디버거와 함께 사용 하도록 설계 되었지만 디버거 외부의 스크립트 또는 함수에 호출 스택을 표시 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff1a5-109">Although it is designed to be used with the PowerShell debugger, you can use this cmdlet to display the call stack in a script or function outside of the debugger.</span></span>

<span data-ttu-id="ff1a5-110">디버거에서 **Get PSCallStack** 명령을 실행 하려면 또는를 입력 `k` `Get-PSCallStack` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff1a5-110">To run a **Get-PSCallStack** command while in the debugger, type `k` or `Get-PSCallStack`.</span></span>

## <span data-ttu-id="ff1a5-111">예제</span><span class="sxs-lookup"><span data-stu-id="ff1a5-111">EXAMPLES</span></span>

### <span data-ttu-id="ff1a5-112">예제 1: 함수에 대 한 호출 스택 가져오기</span><span class="sxs-lookup"><span data-stu-id="ff1a5-112">Example 1: Get the call stack for a function</span></span>

```
PS C:\> function my-alias {
$p = $args[0]
Get-Alias | where {$_.definition -like "*$p"} | format-table definition, name -auto
}
PS C:\ps-test> Set-PSBreakpoint -Command my-alias
Command    : my-alias
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : prompt PS C:\> my-alias Get-Content

Entering debug mode. Use h or ? for help.
Hit Command breakpoint on 'prompt:my-alias'
my-alias get-content
[DBG]: PS C:\ps-test> s
$p = $args[0]
DEBUG: Stepped to ':    $p = $args[0]    '
[DBG]: PS C:\ps-test> s
get-alias | Where {$_.Definition -like "*$p*"} | format-table Definition,
[DBG]: PS C:\ps-test>get-pscallstack

Name        CommandLineParameters         UnboundArguments              Location
----        ---------------------         ----------------              --------
prompt      {}                            {}                            prompt
my-alias    {}                            {get-content}                 prompt
prompt      {}                            {}                            prompt PS C:\> [DBG]: PS C:\ps-test> o
Definition  Name
----------  ----
Get-Content gc
Get-Content cat
Get-Content type
```

<span data-ttu-id="ff1a5-113">이 명령은 **Get PSCallStack** cmdlet을 사용 하 여 cmdlet 이름의 별칭을 가져오는 간단한 함수인 내 별칭에 대 한 호출 스택을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff1a5-113">This command uses the **Get-PSCallStack** cmdlet to display the call stack for My-Alias, a simple function that gets the aliases for a cmdlet name.</span></span>

<span data-ttu-id="ff1a5-114">첫 번째 명령은 PowerShell 프롬프트에 함수를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff1a5-114">The first command enters the function at the PowerShell prompt.</span></span>
<span data-ttu-id="ff1a5-115">두 번째 명령은 Set-PSBreakpoint cmdlet을 사용하여 My-Alias 함수에 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ff1a5-115">The second command uses the Set-PSBreakpoint cmdlet to set a breakpoint on the My-Alias function.</span></span>
<span data-ttu-id="ff1a5-116">세 번째 명령은 My-Alias 함수를 사용하여 Get-Content cmdlet에 대해 현재 세션의 모든 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ff1a5-116">The third command uses the My-Alias function to get all of the aliases in the current session for the Get-Content cmdlet.</span></span>

<span data-ttu-id="ff1a5-117">디버거는 함수 호출 시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff1a5-117">The debugger breaks in at the function call.</span></span>
<span data-ttu-id="ff1a5-118">연속하는 두 step-into 명령이 함수를 한 줄씩 실행하기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ff1a5-118">Two consecutive step-into (s) commands begin executing the function line by line.</span></span>
<span data-ttu-id="ff1a5-119">그런 다음 **Get PSCallStack** 명령이 호출 스택을 검색 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff1a5-119">Then, a **Get-PSCallStack** command is used to retrieve the call stack.</span></span>

<span data-ttu-id="ff1a5-120">최종 명령은 디버거를 종료하고 스크립트를 완료될 때까지 계속 실행하는 Step-Out 명령(o)입니다.</span><span class="sxs-lookup"><span data-stu-id="ff1a5-120">The final command is a Step-Out command (o) that exits the debugger and continues executing the script to completion.</span></span>

## <span data-ttu-id="ff1a5-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ff1a5-121">PARAMETERS</span></span>

### <span data-ttu-id="ff1a5-122">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ff1a5-122">CommonParameters</span></span>

<span data-ttu-id="ff1a5-123">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ff1a5-123">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ff1a5-124">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ff1a5-124">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ff1a5-125">입력</span><span class="sxs-lookup"><span data-stu-id="ff1a5-125">INPUTS</span></span>

### <span data-ttu-id="ff1a5-126">없음</span><span class="sxs-lookup"><span data-stu-id="ff1a5-126">None</span></span>

<span data-ttu-id="ff1a5-127">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ff1a5-127">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="ff1a5-128">출력</span><span class="sxs-lookup"><span data-stu-id="ff1a5-128">OUTPUTS</span></span>

### <span data-ttu-id="ff1a5-129">System.web. CallStackFrame</span><span class="sxs-lookup"><span data-stu-id="ff1a5-129">System.Management.Automation.CallStackFrame</span></span>

<span data-ttu-id="ff1a5-130">**Get PSCallStack** 은 호출 스택의 항목을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff1a5-130">**Get-PSCallStack** returns an object that represents the items in the call stack.</span></span>

## <span data-ttu-id="ff1a5-131">참고</span><span class="sxs-lookup"><span data-stu-id="ff1a5-131">NOTES</span></span>

## <span data-ttu-id="ff1a5-132">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ff1a5-132">RELATED LINKS</span></span>

[<span data-ttu-id="ff1a5-133">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ff1a5-133">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="ff1a5-134">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ff1a5-134">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="ff1a5-135">Format-Table</span><span class="sxs-lookup"><span data-stu-id="ff1a5-135">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="ff1a5-136">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ff1a5-136">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="ff1a5-137">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ff1a5-137">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="ff1a5-138">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ff1a5-138">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
