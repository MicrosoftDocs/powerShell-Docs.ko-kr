---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/13/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerrestorepoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerRestorePoint
ms.openlocfilehash: 73819aafee9ed1911354daf9af23eedff0a3e14c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215481"
---
# <span data-ttu-id="42e89-103">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="42e89-103">Get-ComputerRestorePoint</span></span>

## <span data-ttu-id="42e89-104">개요</span><span class="sxs-lookup"><span data-stu-id="42e89-104">SYNOPSIS</span></span>
<span data-ttu-id="42e89-105">로컬 컴퓨터에 있는 복원 지점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-105">Gets the restore points on the local computer.</span></span>

## <span data-ttu-id="42e89-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="42e89-106">SYNTAX</span></span>

### <span data-ttu-id="42e89-107">ID (기본값)</span><span class="sxs-lookup"><span data-stu-id="42e89-107">ID (Default)</span></span>

```
Get-ComputerRestorePoint [[-RestorePoint] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="42e89-108">LastStatus</span><span class="sxs-lookup"><span data-stu-id="42e89-108">LastStatus</span></span>

```
Get-ComputerRestorePoint -LastStatus [<CommonParameters>]
```

## <span data-ttu-id="42e89-109">설명</span><span class="sxs-lookup"><span data-stu-id="42e89-109">DESCRIPTION</span></span>

<span data-ttu-id="42e89-110">`Get-ComputerRestorePoint`Cmdlet은 로컬 컴퓨터의 시스템 복원 위치를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-110">The `Get-ComputerRestorePoint` cmdlet gets the local computer's system restore points.</span></span> <span data-ttu-id="42e89-111">또한 가장 최근의 컴퓨터 복원 시도 상태를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-111">And, it can display the status of the most recent attempt to restore the computer.</span></span>

<span data-ttu-id="42e89-112">의 정보를 사용 하 여 `Get-ComputerRestorePoint` 복원 지점을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-112">You can use the information from `Get-ComputerRestorePoint` to select a restore point.</span></span> <span data-ttu-id="42e89-113">예를 들어 시퀀스 번호를 사용 하 여 cmdlet에 대 한 복원 지점을 식별 `Restore-Computer` 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-113">For example, use a sequence number to identify a restore point for the `Restore-Computer` cmdlet.</span></span>

<span data-ttu-id="42e89-114">시스템 복원 지점과 `Get-ComputerRestorePoint` cmdlet은 windows 10, windows 7, Windows Vista 및 WINDOWS XP와 같은 클라이언트 운영 체제 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-114">System restore points and the `Get-ComputerRestorePoint` cmdlet are supported only on client operating systems such as Windows 10, Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="42e89-115">예제</span><span class="sxs-lookup"><span data-stu-id="42e89-115">EXAMPLES</span></span>

### <span data-ttu-id="42e89-116">예제 1: 모든 시스템 복원 시점 가져오기</span><span class="sxs-lookup"><span data-stu-id="42e89-116">Example 1: Get all system restore points</span></span>

<span data-ttu-id="42e89-117">이 예에서는 `Get-ComputerRestorePoint` 로컬 컴퓨터의 시스템 복원 지점이 모두 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-117">In this example, `Get-ComputerRestorePoint` gets all the local computer's system restore points.</span></span>

```powershell
Get-ComputerRestorePoint
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
8/7/2019  12:56:45     Installed PowerShell 6-x64     6                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

### <span data-ttu-id="42e89-118">예제 2: 특정 시퀀스 번호 가져오기</span><span class="sxs-lookup"><span data-stu-id="42e89-118">Example 2: Get specific sequence numbers</span></span>

<span data-ttu-id="42e89-119">이 예에서는 특정 시퀀스 번호에 대 한 시스템 복원 지점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-119">This example gets system restore points for specific sequence numbers.</span></span>

```powershell
Get-ComputerRestorePoint -RestorePoint 4, 5
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

<span data-ttu-id="42e89-120">`Get-ComputerRestorePoint`**RestorePoint** 매개 변수를 사용 하 여 쉼표로 구분 된 시퀀스 번호 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-120">`Get-ComputerRestorePoint` uses the **RestorePoint** parameter to specify a comma-separated array of sequence numbers.</span></span>

### <span data-ttu-id="42e89-121">예 3: 시스템 복원 상태 표시</span><span class="sxs-lookup"><span data-stu-id="42e89-121">Example 3: Display the status of a system restore</span></span>

<span data-ttu-id="42e89-122">이 예에서는 로컬 컴퓨터의 가장 최근 시스템 복원 상태를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-122">This example displays the status of the most recent system restore on the local computer.</span></span>

```powershell
Get-ComputerRestorePoint -LastStatus
```

```Output
The last attempt to restore the computer failed.
```

<span data-ttu-id="42e89-123">`Get-ComputerRestorePoint`**LastStatus** 매개 변수를 사용 하 여 최근 시스템 복원의 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-123">`Get-ComputerRestorePoint` uses the **LastStatus** parameter to display the result of the most recent system restore.</span></span>

### <span data-ttu-id="42e89-124">예제 4: 식를 사용 하 여 CreationTime 변환</span><span class="sxs-lookup"><span data-stu-id="42e89-124">Example 4: Use an expression to convert the CreationTime</span></span>

<span data-ttu-id="42e89-125">`Get-ComputerRestorePoint`**CreationTime** 을 WMI (WMI(Windows Management Instrumentation)) 날짜 및 시간 문자열로 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-125">`Get-ComputerRestorePoint` outputs the **CreationTime** as a Windows Management Instrumentation (WMI) date and time string.</span></span>

<span data-ttu-id="42e89-126">이 예에서는 변수가 **CreationTime** 문자열을 **DateTime** 개체로 변환 하는 식을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-126">In this example, a variable stores an expression that converts the **CreationTime** string to a **DateTime** object.</span></span> <span data-ttu-id="42e89-127">변환 하기 전에 **CreationTime** 문자열을 보려면과 같은 명령을 사용 `((Get-ComputerRestorePoint).CreationTime)` 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-127">To view **CreationTime** strings before they're converted, use a command such as `((Get-ComputerRestorePoint).CreationTime)`.</span></span> <span data-ttu-id="42e89-128">WMI 날짜 및 시간 문자열에 대 한 자세한 내용은 [CIM_DATETIME](/windows/win32/wmisdk/cim-datetime)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42e89-128">For more information about the WMI date and time string, see [CIM_DATETIME](/windows/win32/wmisdk/cim-datetime).</span></span>

```powershell
$date = @{Label="Date"; Expression={$_.ConvertToDateTime($_.CreationTime)}}
Get-ComputerRestorePoint | Select-Object -Property SequenceNumber, $date, Description
```

```Output
SequenceNumber   Date                 Description
--------------   ----                 -----------
             4   7/30/2019 09:17:24   Windows Update
             5   8/5/2019  08:15:37   Installed PowerShell 7-preview-x64
             6   8/7/2019  12:56:45   Installed PowerShell 6-x64
```

<span data-ttu-id="42e89-129">`$date`변수는 **ConvertToDateTime** 메서드를 사용 하는 식을 사용 하 여 해시 테이블을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-129">The `$date` variable stores a hash table with the expression that uses the **ConvertToDateTime** method.</span></span> <span data-ttu-id="42e89-130">식은 **CreationTime** 속성의 값을 WMI 문자열에서 **DateTime** 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-130">The expression converts the **CreationTime** property's value from a WMI string to a **DateTime** object.</span></span>

<span data-ttu-id="42e89-131">`Get-ComputerRestorePoint` 시스템 복원 지점 개체를 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-131">`Get-ComputerRestorePoint` sends the system restore point objects down the pipeline.</span></span> <span data-ttu-id="42e89-132">`Select-Object`**Property** 매개 변수를 사용 하 여 표시할 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-132">`Select-Object` uses the **Property** parameter to specify the properties to display.</span></span> <span data-ttu-id="42e89-133">파이프라인의 각 개체에 대해의 식은 `$date` **CreationTime** 를 변환 하 고 **Date** 속성의 결과를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-133">For each object in the pipeline, the expression in `$date` converts the **CreationTime** and outputs the result in the **Date** property.</span></span>

### <span data-ttu-id="42e89-134">예 5: 속성을 사용 하 여 시퀀스 번호 가져오기</span><span class="sxs-lookup"><span data-stu-id="42e89-134">Example 5: Use a property to get a sequence number</span></span>

<span data-ttu-id="42e89-135">이 예에서는 **SequenceNumber** 속성 및 배열 인덱스를 사용 하 여 시퀀스 번호를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-135">This example gets a sequence number by using the **SequenceNumber** property and an array index.</span></span> <span data-ttu-id="42e89-136">출력에는 시퀀스 번호만 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-136">The output only contains the sequence number.</span></span>

```powershell
((Get-ComputerRestorePoint).SequenceNumber)[-1]
```

```Output
6
```

<span data-ttu-id="42e89-137">`Get-ComputerRestorePoint` 배열 인덱스에 **SequenceNumber** 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-137">`Get-ComputerRestorePoint` uses the **SequenceNumber** property with an array index.</span></span> <span data-ttu-id="42e89-138">의 배열 인덱스는 `-1` 배열에서 가장 최근의 시퀀스 번호를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-138">The array index of `-1` gets the most recent sequence number in the array.</span></span>

## <span data-ttu-id="42e89-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="42e89-139">PARAMETERS</span></span>

### <span data-ttu-id="42e89-140">-LastStatus</span><span class="sxs-lookup"><span data-stu-id="42e89-140">-LastStatus</span></span>

<span data-ttu-id="42e89-141">에서 `Get-ComputerRestorePoint` 가장 최근의 시스템 복원 작업의 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-141">Indicates that `Get-ComputerRestorePoint` gets the status of the most recent system restore operation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LastStatus
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="42e89-142">-RestorePoint</span><span class="sxs-lookup"><span data-stu-id="42e89-142">-RestorePoint</span></span>

<span data-ttu-id="42e89-143">시스템 복원 지점의 시퀀스 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-143">Specifies the sequence numbers of the system restore points.</span></span> <span data-ttu-id="42e89-144">단일 시퀀스 번호 또는 쉼표로 구분 된 일련 번호 배열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-144">You can specify either a single sequence number or a comma-separated array of sequence numbers.</span></span>

<span data-ttu-id="42e89-145">**RestorePoint** 매개 변수를 지정 하지 않으면는 `Get-ComputerRestorePoint` 로컬 컴퓨터의 시스템 복원 지점이 모두 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-145">If the **RestorePoint** parameter isn't specified, `Get-ComputerRestorePoint` returns all the local computer's system restore points.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: ID
Aliases:

Required: False
Position: 0
Default value: All restore points
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="42e89-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="42e89-146">CommonParameters</span></span>

<span data-ttu-id="42e89-147">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="42e89-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="42e89-148">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42e89-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="42e89-149">입력</span><span class="sxs-lookup"><span data-stu-id="42e89-149">INPUTS</span></span>

### <span data-ttu-id="42e89-150">없음</span><span class="sxs-lookup"><span data-stu-id="42e89-150">None</span></span>

<span data-ttu-id="42e89-151">파이프라인에서로 개체를 보낼 수 없습니다 `Get-ComputerRestorePoint` .</span><span class="sxs-lookup"><span data-stu-id="42e89-151">You can't send objects down the pipeline to `Get-ComputerRestorePoint`.</span></span>

## <span data-ttu-id="42e89-152">출력</span><span class="sxs-lookup"><span data-stu-id="42e89-152">OUTPUTS</span></span>

### <span data-ttu-id="42e89-153">System.object # root\default\SystemRestore 또는 String</span><span class="sxs-lookup"><span data-stu-id="42e89-153">System.Management.ManagementObject#root\default\SystemRestore or String</span></span>

<span data-ttu-id="42e89-154">`Get-ComputerRestorePoint`WMI (WMI(Windows Management Instrumentation)) **SystemRestore** 클래스 인스턴스인 **SystemRestore** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-154">`Get-ComputerRestorePoint` returns a **SystemRestore** object, which is an instance of the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

<span data-ttu-id="42e89-155">**LastStatus** 매개 변수를 사용 하는 경우는 `Get-ComputerRestorePoint` 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-155">When you use the **LastStatus** parameter, `Get-ComputerRestorePoint` returns a string.</span></span>

## <span data-ttu-id="42e89-156">참고</span><span class="sxs-lookup"><span data-stu-id="42e89-156">NOTES</span></span>

<span data-ttu-id="42e89-157">`Get-ComputerRestorePoint`Windows Vista 및 이후 버전의 windows에서 명령을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-157">To run a `Get-ComputerRestorePoint` command on Windows Vista and later versions of Windows, open PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="42e89-158">`Get-ComputerRestorePoint` WMI **SystemRestore** 클래스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="42e89-158">`Get-ComputerRestorePoint` uses the WMI **SystemRestore** class.</span></span>

## <span data-ttu-id="42e89-159">관련 링크</span><span class="sxs-lookup"><span data-stu-id="42e89-159">RELATED LINKS</span></span>

[<span data-ttu-id="42e89-160">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="42e89-160">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="42e89-161">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="42e89-161">about_Arrays</span></span>](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[<span data-ttu-id="42e89-162">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="42e89-162">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="42e89-163">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="42e89-163">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="42e89-164">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="42e89-164">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="42e89-165">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="42e89-165">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="42e89-166">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="42e89-166">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="42e89-167">SystemRestore</span><span class="sxs-lookup"><span data-stu-id="42e89-167">SystemRestore</span></span>](/windows/win32/sr/systemrestore)
