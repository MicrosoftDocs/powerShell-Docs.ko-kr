---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uiculture?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-UICulture
ms.openlocfilehash: 3e1ae99f3e2bd52d26e9c567fcc8184b07c71a4a
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209296"
---
# <span data-ttu-id="cabf1-103">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="cabf1-103">Get-UICulture</span></span>

## <span data-ttu-id="cabf1-104">개요</span><span class="sxs-lookup"><span data-stu-id="cabf1-104">SYNOPSIS</span></span>
<span data-ttu-id="cabf1-105">운영 체제의 현재 UI 문화권 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cabf1-105">Gets the current UI culture settings in the operating system.</span></span>

## <span data-ttu-id="cabf1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cabf1-106">SYNTAX</span></span>

```
Get-UICulture [<CommonParameters>]
```

## <span data-ttu-id="cabf1-107">설명</span><span class="sxs-lookup"><span data-stu-id="cabf1-107">DESCRIPTION</span></span>

<span data-ttu-id="cabf1-108">`Get-UICulture`Cmdlet은 Windows의 현재 UI (사용자 인터페이스) 문화권 설정에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cabf1-108">The `Get-UICulture` cmdlet gets information about the current user interface (UI) culture settings for Windows.</span></span>
<span data-ttu-id="cabf1-109">UI 문화권에 따라 메뉴, 메시지 등의 사용자 인터페이스 요소에 사용되는 텍스트 문자열이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cabf1-109">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span>

<span data-ttu-id="cabf1-110">`Get-Culture`시스템의 현재 문화권을 가져오는 cmdlet을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cabf1-110">You can also use the `Get-Culture` cmdlet, which gets the current culture on the system.</span></span>
<span data-ttu-id="cabf1-111">문화권에 따라 숫자, 통화, 날짜 등의 항목 표시 형식이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cabf1-111">The culture determines the display format of items such as numbers, currency, and dates.</span></span>

## <span data-ttu-id="cabf1-112">예제</span><span class="sxs-lookup"><span data-stu-id="cabf1-112">EXAMPLES</span></span>

### <span data-ttu-id="cabf1-113">예제 1: UI 문화권 가져오기</span><span class="sxs-lookup"><span data-stu-id="cabf1-113">Example 1: Get the UI culture</span></span>

```powershell
Get-UICulture
```

<span data-ttu-id="cabf1-114">이 명령은 현재 UI 문화권 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cabf1-114">This command gets the current UI culture information.</span></span>

### <span data-ttu-id="cabf1-115">예제 2: UI 문화권 가져오기 및 결과 서식 지정</span><span class="sxs-lookup"><span data-stu-id="cabf1-115">Example 2: Get the UI culture and format the results</span></span>

```powershell
Get-UICulture | Format-List *
```

<span data-ttu-id="cabf1-116">이 명령은 현재 UI 문화권의 모든 속성에 대한 값을 목록에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cabf1-116">This command displays the values of all of the properties of the current UI culture in a list.</span></span>

### <span data-ttu-id="cabf1-117">예 3: Calendar 속성 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="cabf1-117">Example 3: Get the value of the Calendar property</span></span>

```powershell
(Get-UICulture).Calendar
```

<span data-ttu-id="cabf1-118">이 명령은 현재 UI 문화권의 **Calendar** 속성에 대 한 현재 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="cabf1-118">This command displays the current values for the **Calendar** property of the current UI culture.</span></span>
<span data-ttu-id="cabf1-119">Calendar는 UI 문화권의 한 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="cabf1-119">Calendar is just one property of UI culture.</span></span>
<span data-ttu-id="cabf1-120">모든 속성을 보려면를 입력 `Get-UICulture | Get-Member` 합니다.</span><span class="sxs-lookup"><span data-stu-id="cabf1-120">To see all of the properties, type `Get-UICulture | Get-Member`.</span></span>

### <span data-ttu-id="cabf1-121">예제 4: 간단한 날짜 패턴 가져오기</span><span class="sxs-lookup"><span data-stu-id="cabf1-121">Example 4: Get the short date pattern</span></span>

```powershell
(Get-UICulture).DateTimeFormat.ShortDatePattern
```

<span data-ttu-id="cabf1-122">이 명령은 현재 UI 문화권의 간단한 날짜 표기 패턴을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cabf1-122">This command displays the short date pattern for the current UI culture.</span></span>
<span data-ttu-id="cabf1-123">UI 문화권의 **DateTimeFormat** 속성에 대 한 모든 하위 속성을 보려면를 입력 `(Get-UICulture).DateTimeFormat | gm` 합니다.</span><span class="sxs-lookup"><span data-stu-id="cabf1-123">To see all of the subproperties of the **DateTimeFormat** property of the UI culture, type `(Get-UICulture).DateTimeFormat | gm`.</span></span>

## <span data-ttu-id="cabf1-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cabf1-124">PARAMETERS</span></span>

### <span data-ttu-id="cabf1-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cabf1-125">CommonParameters</span></span>

<span data-ttu-id="cabf1-126">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cabf1-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cabf1-127">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cabf1-127">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="cabf1-128">입력</span><span class="sxs-lookup"><span data-stu-id="cabf1-128">INPUTS</span></span>

### <span data-ttu-id="cabf1-129">없음</span><span class="sxs-lookup"><span data-stu-id="cabf1-129">None</span></span>

<span data-ttu-id="cabf1-130">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cabf1-130">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="cabf1-131">출력</span><span class="sxs-lookup"><span data-stu-id="cabf1-131">OUTPUTS</span></span>

### <span data-ttu-id="cabf1-132">VistaCultureInfo, Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cabf1-132">System.Globalization.CultureInfo, Microsoft.PowerShell.VistaCultureInfo</span></span>

<span data-ttu-id="cabf1-133">`Get-UICulture` 현재 UI 문화권을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cabf1-133">`Get-UICulture` returns an object that represents the current UI culture.</span></span>
<span data-ttu-id="cabf1-134">Windows PowerShell 3.0에서는 **CultureInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cabf1-134">In Windows PowerShell 3.0, it returns a **CultureInfo** object.</span></span>
<span data-ttu-id="cabf1-135">Windows PowerShell 2.0에서는 **VistaCultureInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cabf1-135">In Windows PowerShell 2.0, it returns a **VistaCultureInfo** object.</span></span>

## <span data-ttu-id="cabf1-136">참고</span><span class="sxs-lookup"><span data-stu-id="cabf1-136">NOTES</span></span>

- <span data-ttu-id="cabf1-137">및 변수를 사용할 수도 `$PsCulture` 있습니다 `$PsUICulture` .</span><span class="sxs-lookup"><span data-stu-id="cabf1-137">You can also use the `$PsCulture` and `$PsUICulture` variables.</span></span> <span data-ttu-id="cabf1-138">`$PsCulture`변수는 현재 문화권의 이름을 저장 하 고 `$PsUICulture` 변수는 현재 UI 문화권의 이름을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="cabf1-138">The `$PsCulture` variable stores the name of the current culture, and the `$PsUICulture` variable stores the name of the current UI culture.</span></span>

## <span data-ttu-id="cabf1-139">관련 링크</span><span class="sxs-lookup"><span data-stu-id="cabf1-139">RELATED LINKS</span></span>

