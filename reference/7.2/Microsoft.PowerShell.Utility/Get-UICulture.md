---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uiculture?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-UICulture
ms.openlocfilehash: 4bd912db3f86ffa8b495faf3e62259f207340938
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599350"
---
# <span data-ttu-id="8a4a7-102">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="8a4a7-102">Get-UICulture</span></span>

## <span data-ttu-id="8a4a7-103">개요</span><span class="sxs-lookup"><span data-stu-id="8a4a7-103">SYNOPSIS</span></span>
<span data-ttu-id="8a4a7-104">운영 체제의 현재 UI 문화권 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-104">Gets the current UI culture settings in the operating system.</span></span>

## <span data-ttu-id="8a4a7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8a4a7-105">SYNTAX</span></span>

```
Get-UICulture [<CommonParameters>]
```

## <span data-ttu-id="8a4a7-106">설명</span><span class="sxs-lookup"><span data-stu-id="8a4a7-106">DESCRIPTION</span></span>

<span data-ttu-id="8a4a7-107">`Get-UICulture`Cmdlet은 Windows의 현재 UI (사용자 인터페이스) 문화권 설정에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-107">The `Get-UICulture` cmdlet gets information about the current user interface (UI) culture settings for Windows.</span></span>
<span data-ttu-id="8a4a7-108">UI 문화권에 따라 메뉴, 메시지 등의 사용자 인터페이스 요소에 사용되는 텍스트 문자열이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-108">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span>

<span data-ttu-id="8a4a7-109">`Get-Culture`시스템의 현재 문화권을 가져오는 cmdlet을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-109">You can also use the `Get-Culture` cmdlet, which gets the current culture on the system.</span></span>
<span data-ttu-id="8a4a7-110">문화권에 따라 숫자, 통화, 날짜 등의 항목 표시 형식이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-110">The culture determines the display format of items such as numbers, currency, and dates.</span></span>

## <span data-ttu-id="8a4a7-111">예제</span><span class="sxs-lookup"><span data-stu-id="8a4a7-111">EXAMPLES</span></span>

### <span data-ttu-id="8a4a7-112">예제 1: UI 문화권 가져오기</span><span class="sxs-lookup"><span data-stu-id="8a4a7-112">Example 1: Get the UI culture</span></span>

```powershell
Get-UICulture
```

<span data-ttu-id="8a4a7-113">이 명령은 현재 UI 문화권 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-113">This command gets the current UI culture information.</span></span>

### <span data-ttu-id="8a4a7-114">예제 2: UI 문화권 가져오기 및 결과 서식 지정</span><span class="sxs-lookup"><span data-stu-id="8a4a7-114">Example 2: Get the UI culture and format the results</span></span>

```powershell
Get-UICulture | Format-List *
```

<span data-ttu-id="8a4a7-115">이 명령은 현재 UI 문화권의 모든 속성에 대한 값을 목록에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-115">This command displays the values of all of the properties of the current UI culture in a list.</span></span>

### <span data-ttu-id="8a4a7-116">예 3: Calendar 속성 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="8a4a7-116">Example 3: Get the value of the Calendar property</span></span>

```powershell
(Get-UICulture).Calendar
```

<span data-ttu-id="8a4a7-117">이 명령은 현재 UI 문화권의 **Calendar** 속성에 대 한 현재 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-117">This command displays the current values for the **Calendar** property of the current UI culture.</span></span>
<span data-ttu-id="8a4a7-118">Calendar는 UI 문화권의 한 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-118">Calendar is just one property of UI culture.</span></span>
<span data-ttu-id="8a4a7-119">모든 속성을 보려면를 입력 `Get-UICulture | Get-Member` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-119">To see all of the properties, type `Get-UICulture | Get-Member`.</span></span>

### <span data-ttu-id="8a4a7-120">예제 4: 간단한 날짜 패턴 가져오기</span><span class="sxs-lookup"><span data-stu-id="8a4a7-120">Example 4: Get the short date pattern</span></span>

```powershell
(Get-UICulture).DateTimeFormat.ShortDatePattern
```

<span data-ttu-id="8a4a7-121">이 명령은 현재 UI 문화권의 간단한 날짜 표기 패턴을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-121">This command displays the short date pattern for the current UI culture.</span></span>
<span data-ttu-id="8a4a7-122">UI 문화권의 **DateTimeFormat** 속성에 대 한 모든 하위 속성을 보려면를 입력 `(Get-UICulture).DateTimeFormat | gm` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-122">To see all of the subproperties of the **DateTimeFormat** property of the UI culture, type `(Get-UICulture).DateTimeFormat | gm`.</span></span>

## <span data-ttu-id="8a4a7-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8a4a7-123">PARAMETERS</span></span>

### <span data-ttu-id="8a4a7-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8a4a7-124">CommonParameters</span></span>

<span data-ttu-id="8a4a7-125">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8a4a7-126">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-126">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="8a4a7-127">입력</span><span class="sxs-lookup"><span data-stu-id="8a4a7-127">INPUTS</span></span>

### <span data-ttu-id="8a4a7-128">없음</span><span class="sxs-lookup"><span data-stu-id="8a4a7-128">None</span></span>

<span data-ttu-id="8a4a7-129">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-129">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="8a4a7-130">출력</span><span class="sxs-lookup"><span data-stu-id="8a4a7-130">OUTPUTS</span></span>

### <span data-ttu-id="8a4a7-131">VistaCultureInfo, Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-131">System.Globalization.CultureInfo, Microsoft.PowerShell.VistaCultureInfo</span></span>

<span data-ttu-id="8a4a7-132">`Get-UICulture` 현재 UI 문화권을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-132">`Get-UICulture` returns an object that represents the current UI culture.</span></span>
<span data-ttu-id="8a4a7-133">Windows PowerShell 3.0에서는 **CultureInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-133">In Windows PowerShell 3.0, it returns a **CultureInfo** object.</span></span>
<span data-ttu-id="8a4a7-134">Windows PowerShell 2.0에서는 **VistaCultureInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-134">In Windows PowerShell 2.0, it returns a **VistaCultureInfo** object.</span></span>

## <span data-ttu-id="8a4a7-135">참고</span><span class="sxs-lookup"><span data-stu-id="8a4a7-135">NOTES</span></span>

- <span data-ttu-id="8a4a7-136">및 변수를 사용할 수도 `$PsCulture` 있습니다 `$PsUICulture` .</span><span class="sxs-lookup"><span data-stu-id="8a4a7-136">You can also use the `$PsCulture` and `$PsUICulture` variables.</span></span> <span data-ttu-id="8a4a7-137">`$PsCulture`변수는 현재 문화권의 이름을 저장 하 고 `$PsUICulture` 변수는 현재 UI 문화권의 이름을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a4a7-137">The `$PsCulture` variable stores the name of the current culture, and the `$PsUICulture` variable stores the name of the current UI culture.</span></span>

## <span data-ttu-id="8a4a7-138">관련 링크</span><span class="sxs-lookup"><span data-stu-id="8a4a7-138">RELATED LINKS</span></span>

