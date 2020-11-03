---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 5f02f59e778c55b2292bb4533cf2f8aaab2dbb7d
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93208984"
---
# <span data-ttu-id="2a032-103">Stop-Transcript</span><span class="sxs-lookup"><span data-stu-id="2a032-103">Stop-Transcript</span></span>

## <span data-ttu-id="2a032-104">개요</span><span class="sxs-lookup"><span data-stu-id="2a032-104">SYNOPSIS</span></span>
<span data-ttu-id="2a032-105">기록을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="2a032-105">Stops a transcript.</span></span>

## <span data-ttu-id="2a032-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2a032-106">SYNTAX</span></span>

```
Stop-Transcript [<CommonParameters>]
```

## <span data-ttu-id="2a032-107">설명</span><span class="sxs-lookup"><span data-stu-id="2a032-107">DESCRIPTION</span></span>

<span data-ttu-id="2a032-108">Cmdlet은 `Stop-Transcript` cmdlet에 의해 시작 된 기록을 중지 합니다 `Start-Transcript` .</span><span class="sxs-lookup"><span data-stu-id="2a032-108">The `Stop-Transcript` cmdlet stops a transcript that was started by the `Start-Transcript` cmdlet.</span></span>
<span data-ttu-id="2a032-109">또는 세션을 종료 하 여 기록을 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a032-109">Alternatively, you can end a session to stop a transcript.</span></span>

## <span data-ttu-id="2a032-110">예제</span><span class="sxs-lookup"><span data-stu-id="2a032-110">EXAMPLES</span></span>

### <span data-ttu-id="2a032-111">예제 1: 모든 기록을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a032-111">Example 1: Stop all transcripts</span></span>

```powershell
Stop-Transcript
```

<span data-ttu-id="2a032-112">이 명령은 모든 기록을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a032-112">This command stops all transcripts.</span></span>

## <span data-ttu-id="2a032-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2a032-113">PARAMETERS</span></span>

### <span data-ttu-id="2a032-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2a032-114">CommonParameters</span></span>

<span data-ttu-id="2a032-115">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2a032-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2a032-116">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a032-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2a032-117">입력</span><span class="sxs-lookup"><span data-stu-id="2a032-117">INPUTS</span></span>

### <span data-ttu-id="2a032-118">없음</span><span class="sxs-lookup"><span data-stu-id="2a032-118">None</span></span>

<span data-ttu-id="2a032-119">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a032-119">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="2a032-120">출력</span><span class="sxs-lookup"><span data-stu-id="2a032-120">OUTPUTS</span></span>

### <span data-ttu-id="2a032-121">System.String</span><span class="sxs-lookup"><span data-stu-id="2a032-121">System.String</span></span>

<span data-ttu-id="2a032-122">이 cmdlet은 상태 메시지와 출력 파일의 경로를 포함 하는 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a032-122">This cmdlet returns a string that contains a status message and the path to the output file.</span></span>

## <span data-ttu-id="2a032-123">참고</span><span class="sxs-lookup"><span data-stu-id="2a032-123">NOTES</span></span>

* <span data-ttu-id="2a032-124">기록이 시작되지 않은 경우에는 명령이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a032-124">If a transcript has not been started, the command fails.</span></span>

*

## <span data-ttu-id="2a032-125">관련 링크</span><span class="sxs-lookup"><span data-stu-id="2a032-125">RELATED LINKS</span></span>

[<span data-ttu-id="2a032-126">Start-Transcript</span><span class="sxs-lookup"><span data-stu-id="2a032-126">Start-Transcript</span></span>](Start-Transcript.md)
