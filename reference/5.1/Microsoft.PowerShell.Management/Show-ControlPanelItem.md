---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-ControlPanelItem
ms.openlocfilehash: 368e385d51437f9ac93b700c929b185dce30a644
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214402"
---
# <span data-ttu-id="2640c-103">Show-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="2640c-103">Show-ControlPanelItem</span></span>

## <span data-ttu-id="2640c-104">개요</span><span class="sxs-lookup"><span data-stu-id="2640c-104">SYNOPSIS</span></span>
<span data-ttu-id="2640c-105">제어판 항목을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-105">Opens control panel items.</span></span>

## <span data-ttu-id="2640c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2640c-106">SYNTAX</span></span>

### <span data-ttu-id="2640c-107">RegularName (기본값)</span><span class="sxs-lookup"><span data-stu-id="2640c-107">RegularName (Default)</span></span>

```
Show-ControlPanelItem [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="2640c-108">CanonicalName</span><span class="sxs-lookup"><span data-stu-id="2640c-108">CanonicalName</span></span>

```
Show-ControlPanelItem -CanonicalName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="2640c-109">Get-controlpanelitem</span><span class="sxs-lookup"><span data-stu-id="2640c-109">ControlPanelItem</span></span>

```
Show-ControlPanelItem [[-InputObject] <ControlPanelItem[]>] [<CommonParameters>]
```

## <span data-ttu-id="2640c-110">설명</span><span class="sxs-lookup"><span data-stu-id="2640c-110">DESCRIPTION</span></span>

<span data-ttu-id="2640c-111">`Show-ControlPanelItem`Cmdlet은 로컬 컴퓨터에서 제어판 항목을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-111">The `Show-ControlPanelItem` cmdlet opens control panel items on the local computer.</span></span> <span data-ttu-id="2640c-112">이를 사용 하 여 사용자 인터페이스가 없는 시스템 에서도 이름, 범주 또는 설명으로 제어판 항목을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-112">You can use it to open control panel items by name, category, or description, even on systems that do not have a user interface.</span></span> <span data-ttu-id="2640c-113">Cmdlet의 제어판 항목을로 파이프 할 수 있습니다 `Get-ControlPanelItem` `Show-ControlPanelItem` .</span><span class="sxs-lookup"><span data-stu-id="2640c-113">You can pipe control panel items from the `Get-ControlPanelItem` cmdlet to `Show-ControlPanelItem`.</span></span>

<span data-ttu-id="2640c-114">`Show-ControlPanelItem` 시스템에서 열 수 있는 제어판 항목만 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-114">`Show-ControlPanelItem` searches only control panel items that can be opened on the system.</span></span> <span data-ttu-id="2640c-115">**제어판** 또는 **파일 탐색기** 가 없는 컴퓨터에서는 `Show-ControlPanelItem` 이러한 구성 요소 없이 열 수 있는 제어판 항목만 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-115">On computers that do not have **Control Panel** or **File Explorer** , `Show-ControlPanelItem` searches only control panel items that can open without these components.</span></span>

<span data-ttu-id="2640c-116">이 cmdlet은 Windows PowerShell 3.0에서 도입 되었으며 Windows 8, Windows Server 2012 이상 버전에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-116">This cmdlet was introduced in Windows PowerShell 3.0 and works on Windows 8, Windows Server 2012, and higher versions.</span></span>

## <span data-ttu-id="2640c-117">예제</span><span class="sxs-lookup"><span data-stu-id="2640c-117">EXAMPLES</span></span>

### <span data-ttu-id="2640c-118">예제 1: 제어판 항목 표시</span><span class="sxs-lookup"><span data-stu-id="2640c-118">Example 1: Show a control panel item</span></span>

<span data-ttu-id="2640c-119">이 예제에서는 **자동 재생** 제어판 항목을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-119">This example launches the **AutoPlay** control panel item.</span></span>

```powershell
Show-ControlPanelItem -Name "AutoPlay"
```

### <span data-ttu-id="2640c-120">예제 2:이 cmdlet에 대 한 제어판 항목 파이프</span><span class="sxs-lookup"><span data-stu-id="2640c-120">Example 2: Pipe a control panel item to this cmdlet</span></span>

<span data-ttu-id="2640c-121">이 예에서는 로컬 컴퓨터의 **Windows Defender 방화벽** 제어판 항목을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-121">This example opens the **Windows Defender Firewall** control panel item on the local computer.</span></span>
<span data-ttu-id="2640c-122">Windows 버전에서 Windows 방화벽 제어판 항목의 이름이 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-122">The name of the Windows Firewall control panel item has changed over the versions of Windows.</span></span> <span data-ttu-id="2640c-123">이 예제에서는 와일드 카드 패턴을 사용 하 여 제어판 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-123">This example uses a wildcard pattern to find the control panel item.</span></span>

```powershell
Get-ControlPanelItem -Name "*Firewall" | Show-ControlPanelItem
```

<span data-ttu-id="2640c-124">`Get-ControlPanelItem` 제어판 항목을 가져오고 `Show-ControlPanelItem` cmdlet이 항목을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-124">`Get-ControlPanelItem` gets the control panel item and the `Show-ControlPanelItem` cmdlet opens it.</span></span>

### <span data-ttu-id="2640c-125">예제 3: 파일 이름을 사용 하 여 제어판 항목 열기</span><span class="sxs-lookup"><span data-stu-id="2640c-125">Example 3: Use a file name to open a control panel item</span></span>

<span data-ttu-id="2640c-126">이 예제에서는 응용 프로그램 이름을 사용 하 여 **프로그램 및 기능** 제어판 항목을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-126">This example opens the **Programs and Features** control panel item by using its application name.</span></span>

```powershell
appwiz.cpl
```

<span data-ttu-id="2640c-127">이 메서드는 명령을 사용 하는 대신 사용할 수 `Show-ControlPanelItem` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-127">This method is an alternative to using a `Show-ControlPanelItem` command.</span></span>

> [!NOTE]
> <span data-ttu-id="2640c-128">PowerShell에서 제어판 파일의 .cpl 파일 확장명은 환경 변수의 값에 포함 되어 있으므로 생략할 수 있습니다. `$env:PathExt`</span><span class="sxs-lookup"><span data-stu-id="2640c-128">In PowerShell, you can omit the .cpl file extension for control panel files because it's included in the value of the `$env:PathExt` environment variable.</span></span>

## <span data-ttu-id="2640c-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2640c-129">PARAMETERS</span></span>

### <span data-ttu-id="2640c-130">-CanonicalName</span><span class="sxs-lookup"><span data-stu-id="2640c-130">-CanonicalName</span></span>

<span data-ttu-id="2640c-131">지정 된 정식 이름 또는 이름 패턴을 사용 하 여 제어판 항목을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-131">Specifies control panel items by using the specified canonical names or name patterns.</span></span> <span data-ttu-id="2640c-132">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-132">Wildcard characters are permitted.</span></span> <span data-ttu-id="2640c-133">여러 이름을 입력 하는 경우이 cmdlet은 이름 목록의 항목이 **OR** 연산자로 구분 된 것 처럼 이름 중 하 나와 일치 하는 제어판 항목을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-133">If you enter multiple names, this cmdlet opens control panel items that match any of the names, as if the items in the name list were separated by an **OR** operator.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CanonicalName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2640c-134">-InputObject</span><span class="sxs-lookup"><span data-stu-id="2640c-134">-InputObject</span></span>

<span data-ttu-id="2640c-135">제어판 항목 개체를 제출 하 여 열 제어판 항목을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-135">Specifies control panel items to open by submitting control panel item objects.</span></span> <span data-ttu-id="2640c-136">제어판 항목 개체를 포함 하는 변수를 입력 하거나 제어판 항목 개체를 가져오는 명령 또는 식 (예:)을 입력 `Get-ControlPanelItem` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-136">Enter a variable that contains control panel item objects, or type a command or expression that gets control panel item objects, such as `Get-ControlPanelItem`.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ControlPanelItem[]
Parameter Sets: ControlPanelItem
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2640c-137">-Name</span><span class="sxs-lookup"><span data-stu-id="2640c-137">-Name</span></span>

<span data-ttu-id="2640c-138">제어판 항목의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-138">Specifies names of control panel items.</span></span> <span data-ttu-id="2640c-139">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="2640c-140">여러 이름을 입력 하는 경우이 cmdlet은 이름 목록의 항목이 **OR** 연산자로 구분 된 것 처럼 이름 중 하 나와 일치 하는 제어판 항목을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-140">If you enter multiple names, this cmdlet opens control panel items that match any of the names, as if the items in the name list were separated by an **OR** operator.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="2640c-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2640c-141">CommonParameters</span></span>

<span data-ttu-id="2640c-142">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2640c-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2640c-143">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2640c-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2640c-144">입력</span><span class="sxs-lookup"><span data-stu-id="2640c-144">INPUTS</span></span>

### <span data-ttu-id="2640c-145">Get-controlpanelitem, Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2640c-145">System.String, Microsoft.PowerShell.Commands.ControlPanelItem</span></span>

<span data-ttu-id="2640c-146">이름 또는 제어판 항목 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-146">You can pipe a name or control panel item object to this cmdlet.</span></span>

## <span data-ttu-id="2640c-147">출력</span><span class="sxs-lookup"><span data-stu-id="2640c-147">OUTPUTS</span></span>

### <span data-ttu-id="2640c-148">없음</span><span class="sxs-lookup"><span data-stu-id="2640c-148">None</span></span>

<span data-ttu-id="2640c-149">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2640c-149">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="2640c-150">참고</span><span class="sxs-lookup"><span data-stu-id="2640c-150">NOTES</span></span>

## <span data-ttu-id="2640c-151">관련 링크</span><span class="sxs-lookup"><span data-stu-id="2640c-151">RELATED LINKS</span></span>

[<span data-ttu-id="2640c-152">Get-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="2640c-152">Get-ControlPanelItem</span></span>](Get-ControlPanelItem.md)
