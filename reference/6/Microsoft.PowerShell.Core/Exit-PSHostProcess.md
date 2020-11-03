---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: 0f076d21ce590b4f1d3eb5b06e891d753dbea638
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209107"
---
# <span data-ttu-id="12c04-103">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="12c04-103">Exit-PSHostProcess</span></span>

## <span data-ttu-id="12c04-104">개요</span><span class="sxs-lookup"><span data-stu-id="12c04-104">SYNOPSIS</span></span>
<span data-ttu-id="12c04-105">로컬 프로세스를 사용 하 여 대화형 세션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="12c04-105">Closes an interactive session with a local process.</span></span>

## <span data-ttu-id="12c04-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="12c04-106">SYNTAX</span></span>

```
Exit-PSHostProcess [<CommonParameters>]
```

## <span data-ttu-id="12c04-107">설명</span><span class="sxs-lookup"><span data-stu-id="12c04-107">DESCRIPTION</span></span>

<span data-ttu-id="12c04-108">**PSHostProcess** cmdlet은 Enter-PSHostProcess cmdlet을 실행 하 여 연 로컬 프로세스와의 대화형 세션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="12c04-108">The **Exit-PSHostProcess** cmdlet closes an interactive session with a local process that you have opened by running the Enter-PSHostProcess cmdlet.</span></span> <span data-ttu-id="12c04-109">프로세스 내에서 실행 중인 스크립트에 대 한 디버깅 또는 문제 해결이 완료 되 면 프로세스 내에서 **PSHostProcess** cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="12c04-109">You run the **Exit-PSHostProcess** cmdlet from within the process, when you are finished debugging or troubleshooting a script that is running within a process.</span></span>

## <span data-ttu-id="12c04-110">예제</span><span class="sxs-lookup"><span data-stu-id="12c04-110">EXAMPLES</span></span>

### <span data-ttu-id="12c04-111">예제 1: 프로세스 종료</span><span class="sxs-lookup"><span data-stu-id="12c04-111">Example 1: Exit a process</span></span>

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

<span data-ttu-id="12c04-112">이 예제에서는 PSHostProcess에 설명 된 대로 프로세스의 runspace에서 실행 되는 스크립트를 디버깅 하기 위해 활성 프로세스로 작업 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12c04-112">In this example, you have been working in an active process to debug a script running in a runspace in the process, as described in Enter-PSHostProcess.</span></span> <span data-ttu-id="12c04-113">**끝내기** 명령을 입력 하 여 디버거를 종료 한 후 **PSHostProcess** cmdlet을 실행 하 여 프로세스와의 대화형 세션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="12c04-113">After you type the **exit** command to exit the debugger, run the **Exit-PSHostProcess** cmdlet to close your interactive session with the process.</span></span>
<span data-ttu-id="12c04-114">Cmdlet은 프로세스에서 세션을 닫고 PS C: \\ \> 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="12c04-114">The cmdlet closes your session in the process, and returns you to the PS C:\\\> prompt.</span></span>

## <span data-ttu-id="12c04-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="12c04-115">PARAMETERS</span></span>

### <span data-ttu-id="12c04-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12c04-116">CommonParameters</span></span>

<span data-ttu-id="12c04-117">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="12c04-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12c04-118">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12c04-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="12c04-119">입력</span><span class="sxs-lookup"><span data-stu-id="12c04-119">INPUTS</span></span>

## <span data-ttu-id="12c04-120">출력</span><span class="sxs-lookup"><span data-stu-id="12c04-120">OUTPUTS</span></span>

## <span data-ttu-id="12c04-121">참고</span><span class="sxs-lookup"><span data-stu-id="12c04-121">NOTES</span></span>

## <span data-ttu-id="12c04-122">관련 링크</span><span class="sxs-lookup"><span data-stu-id="12c04-122">RELATED LINKS</span></span>

[<span data-ttu-id="12c04-123">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="12c04-123">Enter-PSHostProcess</span></span>](Enter-PSHostProcess.md)
