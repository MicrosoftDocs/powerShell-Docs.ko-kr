---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ControlPanelItem
ms.openlocfilehash: 51bc04b4de901a611330266b6b0f58471f998432
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215474"
---
# <span data-ttu-id="0d23c-103">Get-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="0d23c-103">Get-ControlPanelItem</span></span>

## <span data-ttu-id="0d23c-104">개요</span><span class="sxs-lookup"><span data-stu-id="0d23c-104">SYNOPSIS</span></span>
<span data-ttu-id="0d23c-105">제어판 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-105">Gets control panel items.</span></span>

## <span data-ttu-id="0d23c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0d23c-106">SYNTAX</span></span>

### <span data-ttu-id="0d23c-107">RegularName (기본값)</span><span class="sxs-lookup"><span data-stu-id="0d23c-107">RegularName (Default)</span></span>

```
Get-ControlPanelItem [[-Name] <String[]>] [-Category <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="0d23c-108">CanonicalName</span><span class="sxs-lookup"><span data-stu-id="0d23c-108">CanonicalName</span></span>

```
Get-ControlPanelItem -CanonicalName <String[]> [-Category <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="0d23c-109">설명</span><span class="sxs-lookup"><span data-stu-id="0d23c-109">DESCRIPTION</span></span>

<span data-ttu-id="0d23c-110">`Get-ControlPanelItem`Cmdlet은 로컬 컴퓨터에서 제어판 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-110">The `Get-ControlPanelItem` cmdlet gets control panel items on the local computer.</span></span> <span data-ttu-id="0d23c-111">이 cmdlet을 사용하면 사용자 인터페이스가 없는 시스템에서도 이름, 범주 또는 설명으로 제어판 항목을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-111">You can use it to find control panel items by name, category, or description, even on systems that do not have a user interface.</span></span>

<span data-ttu-id="0d23c-112">이 cmdlet은 시스템에서 열 수 있는 제어판 항목만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-112">This cmdlet gets only the control panel items that can be opened on the system.</span></span> <span data-ttu-id="0d23c-113">제어판 또는 파일 탐색기가 없는 컴퓨터에서는이 cmdlet을 사용 하 여 이러한 구성 요소 없이 열 수 있는 제어판 항목만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-113">On computers that do not have Control Panel or File Explorer, this cmdlet gets only control panel items that can open without these components.</span></span>

<span data-ttu-id="0d23c-114">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-114">This cmdlet was introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="0d23c-115">Windows 8 및 Windows Server 2012 이상 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-115">It works only on Windows 8 and Windows Server 2012 and newer.</span></span>

## <span data-ttu-id="0d23c-116">예제</span><span class="sxs-lookup"><span data-stu-id="0d23c-116">EXAMPLES</span></span>

### <span data-ttu-id="0d23c-117">예제 1: 모든 제어판 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="0d23c-117">Example 1: Get all control panel items</span></span>

<span data-ttu-id="0d23c-118">이 명령은 로컬 컴퓨터에 있는 모든 제어판 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-118">This command gets all control panel items on the local computer.</span></span>

```powershell
Get-ControlPanelItem
```

```Output
Name                          CanonicalName                 Category                      Description
----                          -------------                 --------                      -----------
Action Center                 Microsoft.ActionCenter        {System and Security}         Review recent messages and...
Administrative Tools          Microsoft.AdministrativeTools {System and Security}         Configure administrative s...
AutoPlay                      Microsoft.AutoPlay            {Hardware}                    Change default settings fo...
BitLocker Drive Encryption    Microsoft.BitLockerDriveEn... {System and Security}         Protect your computer usin...
Color Management              Microsoft.ColorManagement     {All Control Panel Items}     Change advanced color mana...
Credential Manager            Microsoft.CredentialManager   {User Accounts}               Manage your Windows Creden...
Date and Time                 Microsoft.DateAndTime         {Clock, Language, and Region} Set the date, time, and ti...
...
```

### <span data-ttu-id="0d23c-119">예 2: 이름별로 제어판 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="0d23c-119">Example 2: Get control panel items by name</span></span>

<span data-ttu-id="0d23c-120">이 예제에서는 이름에 프로그램 또는 앱이 있는 제어판 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-120">This example gets control panel items that have Program or App in their names.</span></span>

```powershell
Get-ControlPanelItem -Name "*Program*", "*App*"
```

### <span data-ttu-id="0d23c-121">예제 3: 범주별로 제어판 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="0d23c-121">Example 3: Get control panel items by category</span></span>

<span data-ttu-id="0d23c-122">이 명령은 범주에서 이름에 보안을 갖는 모든 제어판 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-122">This command gets all control panel items in categories that have Security in their names.</span></span>

```powershell
Get-ControlPanelItem -Category "*Security*"
```

### <span data-ttu-id="0d23c-123">예제 4: 제어판 항목 열기</span><span class="sxs-lookup"><span data-stu-id="0d23c-123">Example 4: Open a control panel item</span></span>

<span data-ttu-id="0d23c-124">이 예제에서는 로컬 컴퓨터에서 Windows 방화벽 제어판 항목을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-124">This example opens the Windows Firewall control panel item on the local computer.</span></span>

```powershell
Get-ControlPanelItem -Name "Windows Firewall" | Show-ControlPanelItem
```

<span data-ttu-id="0d23c-125">`Get-ControlPanelItem`Cmdlet은 제어판 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-125">The `Get-ControlPanelItem` cmdlet gets the control panel item.</span></span> <span data-ttu-id="0d23c-126">`Show-ControlPanelItem`Cmdlet에서 해당 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-126">The `Show-ControlPanelItem` cmdlet opens it.</span></span>

### <span data-ttu-id="0d23c-127">예 5: 원격 컴퓨터에서 제어판 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="0d23c-127">Example 5: Get control panel items on a remote computer</span></span>

<span data-ttu-id="0d23c-128">이 예제에서는 Server01 원격 컴퓨터의 BitLocker 드라이브 암호화 제어판 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-128">This example gets the BitLocker Drive Encryption control panel item on the Server01 remote computer.</span></span>
<span data-ttu-id="0d23c-129">Cmdlet은이 `Invoke-Command` `Get-ControlPanelItem` cmdlet을 원격으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-129">The `Invoke-Command` cmdlet runs the `Get-ControlPanelItem` cmdlet remotely.</span></span>

```powershell
Invoke-Command -ComputerName "Server01" {Get-ControlPanelItem -Name "BitLocker*" }
```

### <span data-ttu-id="0d23c-130">예제 6: 제어판 항목의 설명 검색</span><span class="sxs-lookup"><span data-stu-id="0d23c-130">Example 6: Search the descriptions of control panel items</span></span>

<span data-ttu-id="0d23c-131">이 예에서는 제어판 항목의 **Description** 속성을 검색 하 여 이름 **장치** 를 포함 하는 항목만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-131">This example searches the **Description** property of the control panel items to get only those that contain the name **Device** .</span></span>

```powershell
Get-ControlPanelItem | Where-Object {$_.Description -like "*Device*"}
```

```Output
Name                    CanonicalName                 Category    Description
----                    -------------                 --------    -----------
AutoPlay                Microsoft.AutoPlay            {Hardware}  Change default settings fo...
Devices and Printers    Microsoft.DevicesAndPrinters  {Hardware}  View and manage devices, p...
Sound                   Microsoft.Sound               {Hardware}  Configure your audio devic...
```

<span data-ttu-id="0d23c-132">`Get-ControlPanelItem`Cmdlet은 모든 제어판 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-132">The `Get-ControlPanelItem` cmdlet gets all control panel items.</span></span> <span data-ttu-id="0d23c-133">`Where-Object`Cmdlet은 **Description** 속성의 값을 기준으로 항목을 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-133">The `Where-Object` cmdlet filters the items by the value of the **Description** property.</span></span>

## <span data-ttu-id="0d23c-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0d23c-134">PARAMETERS</span></span>

### <span data-ttu-id="0d23c-135">-CanonicalName</span><span class="sxs-lookup"><span data-stu-id="0d23c-135">-CanonicalName</span></span>

<span data-ttu-id="0d23c-136">이 cmdlet이 가져오는 정식 이름 또는 이름 패턴으로 제어판 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-136">Specifies, as a string array, the control panel items by their canonical names or name patterns that this cmdlet gets.</span></span> <span data-ttu-id="0d23c-137">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-137">Wildcards are permitted.</span></span> <span data-ttu-id="0d23c-138">여러 이름을 입력 하는 경우이 cmdlet은 이름 목록의 항목이 "or" 연산자로 구분 되어 있는 것 처럼 모든 이름과 일치 하는 제어판 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-138">If you enter multiple names, this cmdlet gets control panel items that match any of the names, as though the items in the name list were separated by an "or" operator.</span></span>

<span data-ttu-id="0d23c-139">기본적으로이 cmdlet은 시스템의 모든 제어판 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-139">By default, this cmdlet gets all control panel items in the system.</span></span>

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

### <span data-ttu-id="0d23c-140">-범주</span><span class="sxs-lookup"><span data-stu-id="0d23c-140">-Category</span></span>

<span data-ttu-id="0d23c-141">이 cmdlet이 가져오는 지정 된 범주에 있는 제어판 항목의 범주를 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-141">Specifies, as a string array, the categories of the control panel items in the specified categories that this cmdlet gets.</span></span> <span data-ttu-id="0d23c-142">범주 이름 또는 이름 패턴을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-142">Enter a category name or name pattern.</span></span> <span data-ttu-id="0d23c-143">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-143">Wildcards are permitted.</span></span> <span data-ttu-id="0d23c-144">여러 이름을 입력 하는 경우이 cmdlet은 이름 목록의 항목이 "or" 연산자로 구분 되어 있는 것 처럼 모든 이름과 일치 하는 제어판 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-144">If you enter multiple names, this cmdlet gets control panel items that match any of the names, as though the items in the name list were separated by an "or" operator.</span></span> <span data-ttu-id="0d23c-145">기본적으로이 cmdlet은 시스템의 모든 제어판 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-145">By default, this cmdlet gets all control panel items in the system.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0d23c-146">-Name</span><span class="sxs-lookup"><span data-stu-id="0d23c-146">-Name</span></span>

<span data-ttu-id="0d23c-147">이 cmdlet이 가져오는 컨트롤 패널의 이름 또는 이름 패턴을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-147">Specifies, as a string array, the names or name patterns of the control panel that this cmdlet gets.</span></span>
<span data-ttu-id="0d23c-148">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-148">Wildcards are permitted.</span></span> <span data-ttu-id="0d23c-149">이름 또는 이름 패턴을이 cmdlet으로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-149">You can also pipe a name or name pattern to this cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="0d23c-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0d23c-150">CommonParameters</span></span>

<span data-ttu-id="0d23c-151">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0d23c-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0d23c-152">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0d23c-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0d23c-153">입력</span><span class="sxs-lookup"><span data-stu-id="0d23c-153">INPUTS</span></span>

### <span data-ttu-id="0d23c-154">System.String</span><span class="sxs-lookup"><span data-stu-id="0d23c-154">System.String</span></span>

<span data-ttu-id="0d23c-155">이름 또는 이름 패턴을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-155">You can pipe a name or name pattern to this cmdlet.</span></span>

## <span data-ttu-id="0d23c-156">출력</span><span class="sxs-lookup"><span data-stu-id="0d23c-156">OUTPUTS</span></span>

### <span data-ttu-id="0d23c-157">Get-controlpanelitem.</span><span class="sxs-lookup"><span data-stu-id="0d23c-157">Microsoft.PowerShell.Commands.ControlPanelItem</span></span>

<span data-ttu-id="0d23c-158">이 cmdlet은 로컬 컴퓨터에 있는 제어판 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0d23c-158">This cmdlet gets control panel items on the local computer.</span></span>

## <span data-ttu-id="0d23c-159">참고</span><span class="sxs-lookup"><span data-stu-id="0d23c-159">NOTES</span></span>

## <span data-ttu-id="0d23c-160">관련 링크</span><span class="sxs-lookup"><span data-stu-id="0d23c-160">RELATED LINKS</span></span>

[<span data-ttu-id="0d23c-161">Show-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="0d23c-161">Show-ControlPanelItem</span></span>](Show-ControlPanelItem.md)
