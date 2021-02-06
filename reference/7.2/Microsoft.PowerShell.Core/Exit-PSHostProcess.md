---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: a1a8c6fcc16bcddc3bfcdade56cd75aadd179b74
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605224"
---
# <span data-ttu-id="89c71-102">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="89c71-102">Exit-PSHostProcess</span></span>

## <span data-ttu-id="89c71-103">개요</span><span class="sxs-lookup"><span data-stu-id="89c71-103">SYNOPSIS</span></span>
<span data-ttu-id="89c71-104">로컬 프로세스를 사용 하 여 대화형 세션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="89c71-104">Closes an interactive session with a local process.</span></span>

## <span data-ttu-id="89c71-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="89c71-105">SYNTAX</span></span>

```
Exit-PSHostProcess [<CommonParameters>]
```

## <span data-ttu-id="89c71-106">설명</span><span class="sxs-lookup"><span data-stu-id="89c71-106">DESCRIPTION</span></span>

<span data-ttu-id="89c71-107">`Exit-PSHostProcess`Cmdlet은 cmdlet를 실행 하 여 연 로컬 프로세스와의 대화형 세션을 닫습니다 `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="89c71-107">The `Exit-PSHostProcess` cmdlet closes an interactive session with a local process that you have opened by running the `Enter-PSHostProcess` cmdlet.</span></span> <span data-ttu-id="89c71-108">프로세스 내에서 `Exit-PSHostProcess` 실행 중인 스크립트에 대 한 디버깅 또는 문제 해결이 완료 되 면 프로세스 내에서 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="89c71-108">You run the `Exit-PSHostProcess` cmdlet from within the process, when you are finished debugging or troubleshooting a script that is running within a process.</span></span> <span data-ttu-id="89c71-109">PowerShell 6.2부터이 cmdlet은 Windows 이외의 플랫폼에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="89c71-109">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

## <span data-ttu-id="89c71-110">예제</span><span class="sxs-lookup"><span data-stu-id="89c71-110">EXAMPLES</span></span>

### <span data-ttu-id="89c71-111">예제 1: 프로세스 종료</span><span class="sxs-lookup"><span data-stu-id="89c71-111">Example 1: Exit a process</span></span>

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

<span data-ttu-id="89c71-112">이 예에서는에 설명 된 대로 프로세스의 runspace에서 실행 되는 스크립트를 디버깅 하기 위해 활성 프로세스로 작업 하 고 있습니다 `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="89c71-112">In this example, you have been working in an active process to debug a script running in a runspace in the process, as described in `Enter-PSHostProcess`.</span></span> <span data-ttu-id="89c71-113">명령을 입력 하 여 `exit` 디버거를 종료 한 후 cmdlet을 실행 `Exit-PSHostProcess` 하 여 프로세스와의 대화형 세션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="89c71-113">After you type the `exit` command to exit the debugger, run the `Exit-PSHostProcess` cmdlet to close your interactive session with the process.</span></span>
<span data-ttu-id="89c71-114">Cmdlet은 프로세스에서 세션을 닫고 `PS C:\>` 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="89c71-114">The cmdlet closes your session in the process, and returns you to the `PS C:\>` prompt.</span></span>

## <span data-ttu-id="89c71-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="89c71-115">PARAMETERS</span></span>

### <span data-ttu-id="89c71-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="89c71-116">CommonParameters</span></span>

<span data-ttu-id="89c71-117">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="89c71-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="89c71-118">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89c71-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="89c71-119">입력</span><span class="sxs-lookup"><span data-stu-id="89c71-119">INPUTS</span></span>

## <span data-ttu-id="89c71-120">출력</span><span class="sxs-lookup"><span data-stu-id="89c71-120">OUTPUTS</span></span>

## <span data-ttu-id="89c71-121">참고</span><span class="sxs-lookup"><span data-stu-id="89c71-121">NOTES</span></span>

## <span data-ttu-id="89c71-122">관련 링크</span><span class="sxs-lookup"><span data-stu-id="89c71-122">RELATED LINKS</span></span>

[<span data-ttu-id="89c71-123">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="89c71-123">Enter-PSHostProcess</span></span>](Enter-PSHostProcess.md)

