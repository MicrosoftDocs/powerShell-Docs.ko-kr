---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/get-psreadlineoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSReadLineOption
ms.openlocfilehash: 3b2c789225a1d76391015c39e3fc919ba65f0a1b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600447"
---
# <span data-ttu-id="bfdbe-102">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="bfdbe-102">Get-PSReadLineOption</span></span>

## <span data-ttu-id="bfdbe-103">개요</span><span class="sxs-lookup"><span data-stu-id="bfdbe-103">SYNOPSIS</span></span>
<span data-ttu-id="bfdbe-104">구성할 수 있는 옵션의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bfdbe-104">Gets values for the options that can be configured.</span></span>

## <span data-ttu-id="bfdbe-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bfdbe-105">SYNTAX</span></span>

```
Get-PSReadLineOption [<CommonParameters>]
```

## <span data-ttu-id="bfdbe-106">설명</span><span class="sxs-lookup"><span data-stu-id="bfdbe-106">DESCRIPTION</span></span>

<span data-ttu-id="bfdbe-107">`Get-PSReadLineOption`Cmdlet은 cmdlet을 사용 하 여 구성할 수 있는 설정의 현재 상태를 반환 합니다 `Set-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="bfdbe-107">The `Get-PSReadLineOption` cmdlet returns the current state of the settings that can be configured by using the `Set-PSReadLineOption` cmdlet.</span></span> <span data-ttu-id="bfdbe-108">반환 된 개체를 사용 하 여 **Psreadline** 옵션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfdbe-108">You can use the returned object to change **PSReadLine** options.</span></span> <span data-ttu-id="bfdbe-109">이렇게 하면 여러 종류의 토큰에 대 한 구문 색 지정 옵션을 설정 하는 방법이 약간 더 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfdbe-109">This provides a slightly simpler way to set syntax coloring options for multiple kinds of tokens.</span></span>

## <span data-ttu-id="bfdbe-110">예제</span><span class="sxs-lookup"><span data-stu-id="bfdbe-110">EXAMPLES</span></span>

### <span data-ttu-id="bfdbe-111">예제 1: 옵션 및 해당 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="bfdbe-111">Example 1: Get options and their values</span></span>

```powershell
Get-PSReadLineOption
```

```Output
EditMode                               : Windows
AddToHistoryHandler                    : System.Func`2[System.String,System.Object]
HistoryNoDuplicates                    : True
HistorySavePath                        : C:\Users\username\AppData\Roaming\Microsoft\Windows\
                                         PowerShell\PSReadLine\ConsoleHost_history.txt
HistorySaveStyle                       : SaveIncrementally
HistorySearchCaseSensitive             : False
HistorySearchCursorMovesToEnd          : False
MaximumHistoryCount                    : 4096
ContinuationPrompt                     : >>
ExtraPromptLineCount                   : 0
PromptText                             : {> }
BellStyle                              : Audible
DingDuration                           : 50
DingTone                               : 1221
CommandsToValidateScriptBlockArguments : {ForEach-Object, %, Invoke-Command, icm...}
CommandValidationHandler               :
CompletionQueryItems                   : 100
MaximumKillRingCount                   : 10
ShowToolTips                           : True
ViModeIndicator                        : None
WordDelimiters                         : ;:,.[]{}()/\|^&*-=+'"---
AnsiEscapeTimeout                      : 100
CommandColor                           : "`e[93m"
CommentColor                           : "`e[32m"
ContinuationPromptColor                : "`e[97m"
DefaultTokenColor                      : "`e[97m"
EmphasisColor                          : "`e[96m"
ErrorColor                             : "`e[91m"
KeywordColor                           : "`e[92m"
MemberColor                            : "`e[97m"
NumberColor                            : "`e[97m"
OperatorColor                          : "`e[90m"
ParameterColor                         : "`e[90m"
SelectionColor                         : "`e[30;107m"
StringColor                            : "`e[36m"
TypeColor                              : "`e[37m"
VariableColor                          : "`e[92m"
```

<span data-ttu-id="bfdbe-112">이 명령은 사용 가능한 PSReadLine 옵션과 현재 값의 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfdbe-112">This command returns the list of available PSReadLine options and their current values.</span></span>

## <span data-ttu-id="bfdbe-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bfdbe-113">PARAMETERS</span></span>

### <span data-ttu-id="bfdbe-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bfdbe-114">CommonParameters</span></span>

<span data-ttu-id="bfdbe-115">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bfdbe-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bfdbe-116">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bfdbe-116">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bfdbe-117">입력</span><span class="sxs-lookup"><span data-stu-id="bfdbe-117">INPUTS</span></span>

### <span data-ttu-id="bfdbe-118">없음</span><span class="sxs-lookup"><span data-stu-id="bfdbe-118">None</span></span>

<span data-ttu-id="bfdbe-119">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bfdbe-119">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="bfdbe-120">출력</span><span class="sxs-lookup"><span data-stu-id="bfdbe-120">OUTPUTS</span></span>

### <span data-ttu-id="bfdbe-121">PSConsoleReadLineOptions</span><span class="sxs-lookup"><span data-stu-id="bfdbe-121">Microsoft.PowerShell.PSConsoleReadLineOptions</span></span>

<span data-ttu-id="bfdbe-122">현재 옵션의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="bfdbe-122">An instance of the current options.</span></span> <span data-ttu-id="bfdbe-123">이 개체의 속성 값을 변경 하면를 호출 하지 않고 PSReadLine의 설정을 직접 업데이트 `Set-PSReadLineOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfdbe-123">Changing the property values of this object updates the settings in PSReadLine directly without invoking `Set-PSReadLineOption`.</span></span>

## <span data-ttu-id="bfdbe-124">참고</span><span class="sxs-lookup"><span data-stu-id="bfdbe-124">NOTES</span></span>

## <span data-ttu-id="bfdbe-125">관련 링크</span><span class="sxs-lookup"><span data-stu-id="bfdbe-125">RELATED LINKS</span></span>

[<span data-ttu-id="bfdbe-126">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="bfdbe-126">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="bfdbe-127">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="bfdbe-127">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="bfdbe-128">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="bfdbe-128">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="bfdbe-129">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="bfdbe-129">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
