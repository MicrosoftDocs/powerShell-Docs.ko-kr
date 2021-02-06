---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Error
ms.openlocfilehash: 7e4f4adf60a4f6386c646d92ada0003f239f05f4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599345"
---
# <span data-ttu-id="1251e-102">Get-Error</span><span class="sxs-lookup"><span data-stu-id="1251e-102">Get-Error</span></span>

## <span data-ttu-id="1251e-103">개요</span><span class="sxs-lookup"><span data-stu-id="1251e-103">SYNOPSIS</span></span>

<span data-ttu-id="1251e-104">현재 세션에서 가장 최근의 오류 메시지를 가져오고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1251e-104">Gets and displays the most recent error messages from the current session.</span></span>

## <span data-ttu-id="1251e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1251e-105">SYNTAX</span></span>

### <span data-ttu-id="1251e-106">최신 (기본값)</span><span class="sxs-lookup"><span data-stu-id="1251e-106">Newest (Default)</span></span>

```
Get-Error [[-Newest] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="1251e-107">Error</span><span class="sxs-lookup"><span data-stu-id="1251e-107">Error</span></span>

```
Get-Error [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="1251e-108">설명</span><span class="sxs-lookup"><span data-stu-id="1251e-108">DESCRIPTION</span></span>

<span data-ttu-id="1251e-109">`Get-Error`Cmdlet은 세션에서 발생 한 마지막 오류에서 현재 오류 정보를 나타내는 **PSExtendedError** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1251e-109">The `Get-Error` cmdlet gets a **PSExtendedError** object that represents the current error details from the last error that occurred in the session.</span></span>

<span data-ttu-id="1251e-110">`Get-Error` **최신** 매개 변수를 사용 하 여 현재 세션에서 발생 한 지정 된 수의 오류를 표시 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1251e-110">You can use `Get-Error` to display a specified number of errors that have occurred in the current session using the **Newest** parameter.</span></span>

<span data-ttu-id="1251e-111">`Get-Error`또한 cmdlet은와 같은 컬렉션에서 오류 개체를 받아 `$Error` 현재 세션의 여러 오류를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1251e-111">The `Get-Error` cmdlet also receives error objects from a collection, such as `$Error`, to display multiple errors from the current session.</span></span>

## <span data-ttu-id="1251e-112">예제</span><span class="sxs-lookup"><span data-stu-id="1251e-112">EXAMPLES</span></span>

### <span data-ttu-id="1251e-113">예 1: 최신 오류 세부 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="1251e-113">Example 1: Get the most recent error details</span></span>

<span data-ttu-id="1251e-114">이 예에서는 `Get-Error` 현재 세션에서 발생 한 최신 오류의 세부 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1251e-114">In this example, `Get-Error` displays the details of the most recent error that occurred in the current session.</span></span>

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

### <span data-ttu-id="1251e-115">예 2: 현재 세션에서 발생 한 지정 된 수의 오류 메시지 가져오기</span><span class="sxs-lookup"><span data-stu-id="1251e-115">Example 2: Get the specified number of error messages that occurred in the current session</span></span>

<span data-ttu-id="1251e-116">이 예제에서는를 `Get-Error` **최신** 매개 변수와 함께 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1251e-116">This example shows how to use `Get-Error` with the **Newest** parameter.</span></span> <span data-ttu-id="1251e-117">이 예제에서 **최신** 은이 세션에서 발생 한 최신 오류의 3 개에 대 한 세부 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1251e-117">In this example, **Newest** returns the details of the 3 newest errors that occurred in this session.</span></span>

```powershell
Get-Error -Newest 3
```

### <span data-ttu-id="1251e-118">예제 3: 자세한 메시지를 수신 하는 오류 컬렉션 보내기</span><span class="sxs-lookup"><span data-stu-id="1251e-118">Example 3: Send a collection of errors to receive detailed messages</span></span>

<span data-ttu-id="1251e-119">`$Error`자동 변수는 현재 세션에 있는 오류 개체의 배열을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="1251e-119">The `$Error` automatic variable contains an array of error objects in the current session.</span></span> <span data-ttu-id="1251e-120">개체의 배열을로 파이프 하 여 `Get-Error` 자세한 오류 메시지를 수신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1251e-120">The array of objects can be piped to `Get-Error` to receive detailed error messages.</span></span>

<span data-ttu-id="1251e-121">이 예에서는 `$Error` 가 cmdlet으로 파이프 됩니다 `Get-Error` .</span><span class="sxs-lookup"><span data-stu-id="1251e-121">In this example, `$Error` is piped to the `Get-Error` cmdlet.</span></span> <span data-ttu-id="1251e-122">결과는 예 1의 결과와 유사한 자세한 오류 메시지의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="1251e-122">the result is list of detailed error messages, similar to the result of Example 1.</span></span>

```powershell
$Error | Get-Error
```

## <span data-ttu-id="1251e-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1251e-123">PARAMETERS</span></span>

### <span data-ttu-id="1251e-124">-최신</span><span class="sxs-lookup"><span data-stu-id="1251e-124">-Newest</span></span>

<span data-ttu-id="1251e-125">현재 세션에서 발생 한 오류 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1251e-125">Specifies the number of errors to display that have occurred in the current session.</span></span>

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

### <span data-ttu-id="1251e-126">-InputObject</span><span class="sxs-lookup"><span data-stu-id="1251e-126">-InputObject</span></span>

<span data-ttu-id="1251e-127">이 매개 변수는 파이프라인 입력에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1251e-127">This parameter is used for pipeline input.</span></span>

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

### <span data-ttu-id="1251e-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1251e-128">CommonParameters</span></span>

<span data-ttu-id="1251e-129">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1251e-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1251e-130">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1251e-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1251e-131">입력</span><span class="sxs-lookup"><span data-stu-id="1251e-131">INPUTS</span></span>

### <span data-ttu-id="1251e-132">PSObject</span><span class="sxs-lookup"><span data-stu-id="1251e-132">PSObject</span></span>

<span data-ttu-id="1251e-133">는 모든 **PSObject** 의 입력을 지원 하지만 **ErrorRecord** 또는 **Exception** 개체를 제공 하지 않으면 결과가 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="1251e-133">Supports input from any **PSObject**, but results vary unless either an **ErrorRecord** or **Exception** object are supplied.</span></span>

## <span data-ttu-id="1251e-134">출력</span><span class="sxs-lookup"><span data-stu-id="1251e-134">OUTPUTS</span></span>

### <span data-ttu-id="1251e-135">ErrorRecord # PSExtendedError</span><span class="sxs-lookup"><span data-stu-id="1251e-135">System.Management.Automation.ErrorRecord#PSExtendedError</span></span>

<span data-ttu-id="1251e-136">**PSExtendedError** 개체의 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="1251e-136">Output in a **PSExtendedError** object.</span></span>

## <span data-ttu-id="1251e-137">참고</span><span class="sxs-lookup"><span data-stu-id="1251e-137">NOTES</span></span>

<span data-ttu-id="1251e-138">`Get-Error` 파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1251e-138">`Get-Error` accepts pipeline input.</span></span> <span data-ttu-id="1251e-139">예를 들어 `$Error | Get-Error`입니다.</span><span class="sxs-lookup"><span data-stu-id="1251e-139">For example, `$Error | Get-Error`.</span></span>

## <span data-ttu-id="1251e-140">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1251e-140">RELATED LINKS</span></span>

[<span data-ttu-id="1251e-141">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="1251e-141">about_Try_Catch_Finally</span></span>](../Microsoft.PowerShell.Core/About/about_Try_Catch_Finally.md)
