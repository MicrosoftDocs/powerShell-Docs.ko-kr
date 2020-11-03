---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 22298a898bd45a9be5eaf98d4963b98ab1bf063b
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93208992"
---
# <span data-ttu-id="3b2a3-103">Stop-Transcript</span><span class="sxs-lookup"><span data-stu-id="3b2a3-103">Stop-Transcript</span></span>

## <span data-ttu-id="3b2a3-104">개요</span><span class="sxs-lookup"><span data-stu-id="3b2a3-104">SYNOPSIS</span></span>
<span data-ttu-id="3b2a3-105">기록을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="3b2a3-105">Stops a transcript.</span></span>

## <span data-ttu-id="3b2a3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3b2a3-106">SYNTAX</span></span>

```
Stop-Transcript [<CommonParameters>]
```

## <span data-ttu-id="3b2a3-107">설명</span><span class="sxs-lookup"><span data-stu-id="3b2a3-107">DESCRIPTION</span></span>
<span data-ttu-id="3b2a3-108">Cmdlet은 `Stop-Transcript` cmdlet에 의해 시작 된 기록을 중지 합니다 `Start-Transcript` .</span><span class="sxs-lookup"><span data-stu-id="3b2a3-108">The `Stop-Transcript` cmdlet stops a transcript that was started by the `Start-Transcript` cmdlet.</span></span>
<span data-ttu-id="3b2a3-109">또는 세션을 종료 하 여 기록을 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b2a3-109">Alternatively, you can end a session to stop a transcript.</span></span>

## <span data-ttu-id="3b2a3-110">예제</span><span class="sxs-lookup"><span data-stu-id="3b2a3-110">EXAMPLES</span></span>

### <span data-ttu-id="3b2a3-111">예제 1: 모든 기록을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b2a3-111">Example 1: Stop all transcripts</span></span>

```powershell
Stop-Transcript
```

<span data-ttu-id="3b2a3-112">이 명령은 모든 기록을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b2a3-112">This command stops all transcripts.</span></span>

## <span data-ttu-id="3b2a3-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3b2a3-113">PARAMETERS</span></span>

### <span data-ttu-id="3b2a3-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3b2a3-114">CommonParameters</span></span>
<span data-ttu-id="3b2a3-115">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3b2a3-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3b2a3-116">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b2a3-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3b2a3-117">입력</span><span class="sxs-lookup"><span data-stu-id="3b2a3-117">INPUTS</span></span>

### <span data-ttu-id="3b2a3-118">없음</span><span class="sxs-lookup"><span data-stu-id="3b2a3-118">None</span></span>
<span data-ttu-id="3b2a3-119">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3b2a3-119">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="3b2a3-120">출력</span><span class="sxs-lookup"><span data-stu-id="3b2a3-120">OUTPUTS</span></span>

### <span data-ttu-id="3b2a3-121">System.String</span><span class="sxs-lookup"><span data-stu-id="3b2a3-121">System.String</span></span>
<span data-ttu-id="3b2a3-122">이 cmdlet은 상태 메시지와 출력 파일의 경로를 포함 하는 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b2a3-122">This cmdlet returns a string that contains a status message and the path to the output file.</span></span>

## <span data-ttu-id="3b2a3-123">참고</span><span class="sxs-lookup"><span data-stu-id="3b2a3-123">NOTES</span></span>

* <span data-ttu-id="3b2a3-124">기록이 시작되지 않은 경우에는 명령이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3b2a3-124">If a transcript has not been started, the command fails.</span></span>

*

## <span data-ttu-id="3b2a3-125">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3b2a3-125">RELATED LINKS</span></span>

[<span data-ttu-id="3b2a3-126">Start-Transcript</span><span class="sxs-lookup"><span data-stu-id="3b2a3-126">Start-Transcript</span></span>](Start-Transcript.md)
