---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: 6b6d95484ee2aec6fba60f5528a6ef6089d888a0
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342317"
---
# <span data-ttu-id="3887a-103">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="3887a-103">Exit-PSHostProcess</span></span>

## <span data-ttu-id="3887a-104">개요</span><span class="sxs-lookup"><span data-stu-id="3887a-104">SYNOPSIS</span></span>
<span data-ttu-id="3887a-105">로컬 프로세스를 사용 하 여 대화형 세션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="3887a-105">Closes an interactive session with a local process.</span></span>

## <span data-ttu-id="3887a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3887a-106">SYNTAX</span></span>

```
Exit-PSHostProcess [<CommonParameters>]
```

## <span data-ttu-id="3887a-107">설명</span><span class="sxs-lookup"><span data-stu-id="3887a-107">DESCRIPTION</span></span>

<span data-ttu-id="3887a-108">`Exit-PSHostProcess`Cmdlet은 cmdlet를 실행 하 여 연 로컬 프로세스와의 대화형 세션을 닫습니다 `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="3887a-108">The `Exit-PSHostProcess` cmdlet closes an interactive session with a local process that you have opened by running the `Enter-PSHostProcess` cmdlet.</span></span> <span data-ttu-id="3887a-109">프로세스 내에서 `Exit-PSHostProcess` 실행 중인 스크립트에 대 한 디버깅 또는 문제 해결이 완료 되 면 프로세스 내에서 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3887a-109">You run the `Exit-PSHostProcess` cmdlet from within the process, when you are finished debugging or troubleshooting a script that is running within a process.</span></span> <span data-ttu-id="3887a-110">PowerShell 6.2부터이 cmdlet은 Windows 이외의 플랫폼에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3887a-110">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

## <span data-ttu-id="3887a-111">예제</span><span class="sxs-lookup"><span data-stu-id="3887a-111">EXAMPLES</span></span>

### <span data-ttu-id="3887a-112">예제 1: 프로세스 종료</span><span class="sxs-lookup"><span data-stu-id="3887a-112">Example 1: Exit a process</span></span>

```
PS C:\> [Process:1520]: PS C:\>  Exit-PSHostProcess
PS C:\>
```

<span data-ttu-id="3887a-113">이 예에서는에 설명 된 대로 프로세스의 runspace에서 실행 되는 스크립트를 디버깅 하기 위해 활성 프로세스로 작업 하 고 있습니다 `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="3887a-113">In this example, you have been working in an active process to debug a script running in a runspace in the process, as described in `Enter-PSHostProcess`.</span></span> <span data-ttu-id="3887a-114">명령을 입력 하 여 `exit` 디버거를 종료 한 후 cmdlet을 실행 `Exit-PSHostProcess` 하 여 프로세스와의 대화형 세션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="3887a-114">After you type the `exit` command to exit the debugger, run the `Exit-PSHostProcess` cmdlet to close your interactive session with the process.</span></span>
<span data-ttu-id="3887a-115">Cmdlet은 프로세스에서 세션을 닫고 `PS C:\>` 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="3887a-115">The cmdlet closes your session in the process, and returns you to the `PS C:\>` prompt.</span></span>

## <span data-ttu-id="3887a-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3887a-116">PARAMETERS</span></span>

### <span data-ttu-id="3887a-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3887a-117">CommonParameters</span></span>

<span data-ttu-id="3887a-118">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3887a-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3887a-119">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3887a-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3887a-120">입력</span><span class="sxs-lookup"><span data-stu-id="3887a-120">INPUTS</span></span>

## <span data-ttu-id="3887a-121">출력</span><span class="sxs-lookup"><span data-stu-id="3887a-121">OUTPUTS</span></span>

## <span data-ttu-id="3887a-122">참고</span><span class="sxs-lookup"><span data-stu-id="3887a-122">NOTES</span></span>

## <span data-ttu-id="3887a-123">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3887a-123">RELATED LINKS</span></span>

[<span data-ttu-id="3887a-124">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="3887a-124">Enter-PSHostProcess</span></span>](Enter-PSHostProcess.md)
