---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 16b41711e98276fee37d56f77f57e7372daa4cf3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605494"
---
# <span data-ttu-id="6aab0-102">Stop-Transcript</span><span class="sxs-lookup"><span data-stu-id="6aab0-102">Stop-Transcript</span></span>

## <span data-ttu-id="6aab0-103">개요</span><span class="sxs-lookup"><span data-stu-id="6aab0-103">SYNOPSIS</span></span>
<span data-ttu-id="6aab0-104">기록을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="6aab0-104">Stops a transcript.</span></span>

## <span data-ttu-id="6aab0-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6aab0-105">SYNTAX</span></span>

```
Stop-Transcript [<CommonParameters>]
```

## <span data-ttu-id="6aab0-106">설명</span><span class="sxs-lookup"><span data-stu-id="6aab0-106">DESCRIPTION</span></span>

<span data-ttu-id="6aab0-107">Cmdlet은 `Stop-Transcript` cmdlet에 의해 시작 된 기록을 중지 합니다 `Start-Transcript` .</span><span class="sxs-lookup"><span data-stu-id="6aab0-107">The `Stop-Transcript` cmdlet stops a transcript that was started by the `Start-Transcript` cmdlet.</span></span>
<span data-ttu-id="6aab0-108">또는 세션을 종료 하 여 기록을 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6aab0-108">Alternatively, you can end a session to stop a transcript.</span></span>

## <span data-ttu-id="6aab0-109">예제</span><span class="sxs-lookup"><span data-stu-id="6aab0-109">EXAMPLES</span></span>

### <span data-ttu-id="6aab0-110">예제 1: 모든 기록을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6aab0-110">Example 1: Stop all transcripts</span></span>

```powershell
Stop-Transcript
```

<span data-ttu-id="6aab0-111">이 명령은 모든 기록을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6aab0-111">This command stops all transcripts.</span></span>

## <span data-ttu-id="6aab0-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6aab0-112">PARAMETERS</span></span>

### <span data-ttu-id="6aab0-113">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6aab0-113">CommonParameters</span></span>

<span data-ttu-id="6aab0-114">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6aab0-114">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6aab0-115">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6aab0-115">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6aab0-116">입력</span><span class="sxs-lookup"><span data-stu-id="6aab0-116">INPUTS</span></span>

### <span data-ttu-id="6aab0-117">없음</span><span class="sxs-lookup"><span data-stu-id="6aab0-117">None</span></span>

<span data-ttu-id="6aab0-118">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6aab0-118">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="6aab0-119">출력</span><span class="sxs-lookup"><span data-stu-id="6aab0-119">OUTPUTS</span></span>

### <span data-ttu-id="6aab0-120">System.String</span><span class="sxs-lookup"><span data-stu-id="6aab0-120">System.String</span></span>

<span data-ttu-id="6aab0-121">이 cmdlet은 상태 메시지와 출력 파일의 경로를 포함 하는 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6aab0-121">This cmdlet returns a string that contains a status message and the path to the output file.</span></span>

## <span data-ttu-id="6aab0-122">참고</span><span class="sxs-lookup"><span data-stu-id="6aab0-122">NOTES</span></span>

* <span data-ttu-id="6aab0-123">기록이 시작되지 않은 경우에는 명령이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6aab0-123">If a transcript has not been started, the command fails.</span></span>

*

## <span data-ttu-id="6aab0-124">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6aab0-124">RELATED LINKS</span></span>

[<span data-ttu-id="6aab0-125">Start-Transcript</span><span class="sxs-lookup"><span data-stu-id="6aab0-125">Start-Transcript</span></span>](Start-Transcript.md)

