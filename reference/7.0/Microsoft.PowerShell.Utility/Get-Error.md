---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Error
ms.openlocfilehash: 1a8e278e03d8aea4129c172d786d285d6b55b083
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211842"
---
# <span data-ttu-id="5260d-103">Get-Error</span><span class="sxs-lookup"><span data-stu-id="5260d-103">Get-Error</span></span>

## <span data-ttu-id="5260d-104">개요</span><span class="sxs-lookup"><span data-stu-id="5260d-104">SYNOPSIS</span></span>

<span data-ttu-id="5260d-105">현재 세션에서 가장 최근의 오류 메시지를 가져오고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5260d-105">Gets and displays the most recent error messages from the current session.</span></span>

## <span data-ttu-id="5260d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5260d-106">SYNTAX</span></span>

### <span data-ttu-id="5260d-107">최신 (기본값)</span><span class="sxs-lookup"><span data-stu-id="5260d-107">Newest (Default)</span></span>

```
Get-Error [[-Newest] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="5260d-108">오류</span><span class="sxs-lookup"><span data-stu-id="5260d-108">Error</span></span>

```
Get-Error [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="5260d-109">설명</span><span class="sxs-lookup"><span data-stu-id="5260d-109">DESCRIPTION</span></span>

<span data-ttu-id="5260d-110">`Get-Error`Cmdlet은 세션에서 발생 한 마지막 오류에서 현재 오류 정보를 나타내는 **PSExtendedError** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5260d-110">The `Get-Error` cmdlet gets a **PSExtendedError** object that represents the current error details from the last error that occurred in the session.</span></span>

<span data-ttu-id="5260d-111">`Get-Error` **최신** 매개 변수를 사용 하 여 현재 세션에서 발생 한 지정 된 수의 오류를 표시 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5260d-111">You can use `Get-Error` to display a specified number of errors that have occurred in the current session using the **Newest** parameter.</span></span>

<span data-ttu-id="5260d-112">`Get-Error`또한 cmdlet은와 같은 컬렉션에서 오류 개체를 받아 `$Error` 현재 세션의 여러 오류를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5260d-112">The `Get-Error` cmdlet also receives error objects from a collection, such as `$Error`, to display multiple errors from the current session.</span></span>

## <span data-ttu-id="5260d-113">예제</span><span class="sxs-lookup"><span data-stu-id="5260d-113">EXAMPLES</span></span>

### <span data-ttu-id="5260d-114">예 1: 최신 오류 세부 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="5260d-114">Example 1: Get the most recent error details</span></span>

<span data-ttu-id="5260d-115">이 예에서는 `Get-Error` 현재 세션에서 발생 한 최신 오류의 세부 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5260d-115">In this example, `Get-Error` displays the details of the most recent error that occurred in the current session.</span></span>

```powershell
Get-Childitem -path /NoRealDirectory
Get-Error
```

```
Get-ChildItem: Cannot find path 'C:\NoRealDirectory' because it does not exist.

Exception             :
    ErrorRecord          :
        Exception             :
            Message : Cannot find path 'C:\NoRealDirectory' because it does not exist.
            HResult : -2146233087
        TargetObject          : C:\NoRealDirectory
        CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [], ParentContainsErrorRecordException
        FullyQualifiedErrorId : PathNotFound
    ItemName             : C:\NoRealDirectory
    SessionStateCategory : Drive
    TargetSite           :
        Name          : GetChildItems
        DeclaringType : System.Management.Automation.SessionStateInternal
        MemberType    : Method
        Module        : System.Management.Automation.dll
    StackTrace           :
   at System.Management.Automation.SessionStateInternal.GetChildItems(String path, Boolean recurse, UInt32 depth,
CmdletProviderContext context)
   at System.Management.Automation.ChildItemCmdletProviderIntrinsics.Get(String path, Boolean recurse, UInt32
depth, CmdletProviderContext context)
   at Microsoft.PowerShell.Commands.GetChildItemCommand.ProcessRecord()
    Message              : Cannot find path 'C:\NoRealDirectory' because it does not exist.
    Source               : System.Management.Automation
    HResult              : -2146233087
TargetObject          : C:\NoRealDirectory
CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [Get-ChildItem], ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
InvocationInfo        :
    MyCommand        : Get-ChildItem
    ScriptLineNumber : 1
    OffsetInLine     : 1
    HistoryId        : 57
    Line             : Get-Childitem -path c:\NoRealDirectory
    PositionMessage  : At line:1 char:1
                       + Get-Childitem -path c:\NoRealDirectory
                       + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    InvocationName   : Get-Childitem
    CommandOrigin    : Internal
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo :
```

### <span data-ttu-id="5260d-116">예 2: 현재 세션에서 발생 한 지정 된 수의 오류 메시지 가져오기</span><span class="sxs-lookup"><span data-stu-id="5260d-116">Example 2: Get the specified number of error messages that occurred in the current session</span></span>

<span data-ttu-id="5260d-117">이 예제에서는를 `Get-Error` **최신** 매개 변수와 함께 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5260d-117">This example shows how to use `Get-Error` with the **Newest** parameter.</span></span> <span data-ttu-id="5260d-118">이 예제에서 **최신** 은이 세션에서 발생 한 최신 오류의 3 개에 대 한 세부 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5260d-118">In this example, **Newest** returns the details of the 3 newest errors that occurred in this session.</span></span>

```powershell
Get-Error -Newest 3
```

### <span data-ttu-id="5260d-119">예제 3: 자세한 메시지를 수신 하는 오류 컬렉션 보내기</span><span class="sxs-lookup"><span data-stu-id="5260d-119">Example 3: Send a collection of errors to receive detailed messages</span></span>

<span data-ttu-id="5260d-120">`$Error`자동 변수는 현재 세션에 있는 오류 개체의 배열을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="5260d-120">The `$Error` automatic variable contains an array of error objects in the current session.</span></span> <span data-ttu-id="5260d-121">개체의 배열을로 파이프 하 여 `Get-Error` 자세한 오류 메시지를 수신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5260d-121">The array of objects can be piped to `Get-Error` to receive detailed error messages.</span></span>

<span data-ttu-id="5260d-122">이 예에서는 `$Error` 가 cmdlet으로 파이프 됩니다 `Get-Error` .</span><span class="sxs-lookup"><span data-stu-id="5260d-122">In this example, `$Error` is piped to the `Get-Error` cmdlet.</span></span> <span data-ttu-id="5260d-123">결과는 예 1의 결과와 유사한 자세한 오류 메시지의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="5260d-123">the result is list of detailed error messages, similar to the result of Example 1.</span></span>

```powershell
$Error | Get-Error
```

## <span data-ttu-id="5260d-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5260d-124">PARAMETERS</span></span>

### <span data-ttu-id="5260d-125">-최신</span><span class="sxs-lookup"><span data-stu-id="5260d-125">-Newest</span></span>

<span data-ttu-id="5260d-126">현재 세션에서 발생 한 오류 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5260d-126">Specifies the number of errors to display that have occurred in the current session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Newest
Aliases: Last

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5260d-127">-InputObject</span><span class="sxs-lookup"><span data-stu-id="5260d-127">-InputObject</span></span>

<span data-ttu-id="5260d-128">이 매개 변수는 파이프라인 입력에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5260d-128">This parameter is used for pipeline input.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Error
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5260d-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5260d-129">CommonParameters</span></span>

<span data-ttu-id="5260d-130">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5260d-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5260d-131">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5260d-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5260d-132">입력</span><span class="sxs-lookup"><span data-stu-id="5260d-132">INPUTS</span></span>

### <span data-ttu-id="5260d-133">PSObject</span><span class="sxs-lookup"><span data-stu-id="5260d-133">PSObject</span></span>

<span data-ttu-id="5260d-134">는 모든 **PSObject** 의 입력을 지원 하지만 **ErrorRecord** 또는 **Exception** 개체를 제공 하지 않으면 결과가 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="5260d-134">Supports input from any **PSObject** , but results vary unless either an **ErrorRecord** or **Exception** object are supplied.</span></span>

## <span data-ttu-id="5260d-135">출력</span><span class="sxs-lookup"><span data-stu-id="5260d-135">OUTPUTS</span></span>

### <span data-ttu-id="5260d-136">ErrorRecord # PSExtendedError</span><span class="sxs-lookup"><span data-stu-id="5260d-136">System.Management.Automation.ErrorRecord#PSExtendedError</span></span>

<span data-ttu-id="5260d-137">**PSExtendedError** 개체의 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="5260d-137">Output in a **PSExtendedError** object.</span></span>

## <span data-ttu-id="5260d-138">참고</span><span class="sxs-lookup"><span data-stu-id="5260d-138">NOTES</span></span>

<span data-ttu-id="5260d-139">`Get-Error` 파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5260d-139">`Get-Error` accepts pipeline input.</span></span> <span data-ttu-id="5260d-140">예들 들어 `$Error | Get-Error`입니다.</span><span class="sxs-lookup"><span data-stu-id="5260d-140">For example, `$Error | Get-Error`.</span></span>

## <span data-ttu-id="5260d-141">관련 링크</span><span class="sxs-lookup"><span data-stu-id="5260d-141">RELATED LINKS</span></span>

[<span data-ttu-id="5260d-142">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="5260d-142">about_Try_Catch_Finally</span></span>](../Microsoft.PowerShell.Core/About/about_Try_Catch_Finally.md)
