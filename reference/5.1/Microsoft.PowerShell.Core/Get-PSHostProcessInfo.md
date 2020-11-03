---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pshostprocessinfo?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSHostProcessInfo
ms.openlocfilehash: 5f3579e002030715d7e5926de5f6209cd61b0367
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212025"
---
# <span data-ttu-id="076bb-103">Get-PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="076bb-103">Get-PSHostProcessInfo</span></span>

## <span data-ttu-id="076bb-104">개요</span><span class="sxs-lookup"><span data-stu-id="076bb-104">SYNOPSIS</span></span>
<span data-ttu-id="076bb-105">PowerShell 호스트에 대 한 프로세스 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="076bb-105">Gets process information about the PowerShell host.</span></span>

## <span data-ttu-id="076bb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="076bb-106">SYNTAX</span></span>

### <span data-ttu-id="076bb-107">ProcessNameParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="076bb-107">ProcessNameParameterSet (Default)</span></span>

```
Get-PSHostProcessInfo [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="076bb-108">ProcessParameterSet</span><span class="sxs-lookup"><span data-stu-id="076bb-108">ProcessParameterSet</span></span>

```
Get-PSHostProcessInfo [-Process] <Process[]> [<CommonParameters>]
```

### <span data-ttu-id="076bb-109">ProcessIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="076bb-109">ProcessIdParameterSet</span></span>

```
Get-PSHostProcessInfo [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="076bb-110">설명</span><span class="sxs-lookup"><span data-stu-id="076bb-110">DESCRIPTION</span></span>

<span data-ttu-id="076bb-111">`Get-PSHostProcessInfo`Cmdlet은 로컬 컴퓨터에서 실행 되는 PowerShell 호스트 프로세스에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="076bb-111">The `Get-PSHostProcessInfo` cmdlet gets information about PowerShell host processes running on the local computer.</span></span>

<span data-ttu-id="076bb-112">PowerShell 6.2부터이 cmdlet은 Windows 이외의 플랫폼에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="076bb-112">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

## <span data-ttu-id="076bb-113">예제</span><span class="sxs-lookup"><span data-stu-id="076bb-113">EXAMPLES</span></span>

### <span data-ttu-id="076bb-114">1: 시스템에서 실행 되는 PowerShell 호스트의 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="076bb-114">1: Get a list of PowerShell hosts running on the system</span></span>

```powershell
Get-PSHostProcessInfo
```

```Output
ProcessName ProcessId AppDomainName    MainWindowTitle
----------- --------- -------------    ---------------
powershell      14676 DefaultAppDomain Windows PowerShell
powershell       5184 DefaultAppDomain Windows PowerShell
```

### <span data-ttu-id="076bb-115">2: 특정 프로세스에 대 한 PowerShell 호스트 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="076bb-115">2: Get PowerShell host information for a specific process</span></span>

```powershell
Get-PSHostProcessInfo -Id 14676
```

```Output
ProcessName ProcessId AppDomainName    MainWindowTitle
----------- --------- -------------    ---------------
powershell      14676 DefaultAppDomain Windows PowerShell
```

## <span data-ttu-id="076bb-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="076bb-116">PARAMETERS</span></span>

### <span data-ttu-id="076bb-117">-Id</span><span class="sxs-lookup"><span data-stu-id="076bb-117">-Id</span></span>

<span data-ttu-id="076bb-118">프로세스 ID로 프로세스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="076bb-118">Specifies a process by the process ID.</span></span> <span data-ttu-id="076bb-119">프로세스 ID를 가져오려면 cmdlet을 실행 `Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="076bb-119">To get a process ID, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="076bb-120">-Name</span><span class="sxs-lookup"><span data-stu-id="076bb-120">-Name</span></span>

<span data-ttu-id="076bb-121">프로세스 이름으로 프로세스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="076bb-121">Specifies a process by the process name.</span></span> <span data-ttu-id="076bb-122">프로세스 이름을 가져오려면 cmdlet을 실행 `Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="076bb-122">To get a process name, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="076bb-123">-Process</span><span class="sxs-lookup"><span data-stu-id="076bb-123">-Process</span></span>

<span data-ttu-id="076bb-124">프로세스 개체의 프로세스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="076bb-124">Specifies a process by the process object.</span></span> <span data-ttu-id="076bb-125">이 매개 변수를 사용 하는 가장 간단한 방법은 `Get-Process` 변수에 입력 하려는 프로세스를 반환 하는 명령의 결과를 저장 한 다음이 매개 변수의 값으로 변수를 지정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="076bb-125">The simplest way to use this parameter is to save the results of a `Get-Process` command that returns process that you want to enter in a variable, and then specify the variable as the value of this parameter.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="076bb-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="076bb-126">CommonParameters</span></span>

<span data-ttu-id="076bb-127">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="076bb-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="076bb-128">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="076bb-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="076bb-129">입력</span><span class="sxs-lookup"><span data-stu-id="076bb-129">INPUTS</span></span>

### <span data-ttu-id="076bb-130">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="076bb-130">System.Diagnostics.Process</span></span>

<span data-ttu-id="076bb-131">**프로세스** 개체를에서이 cmdlet으로 파이프 할 수 있습니다 `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="076bb-131">You can pipe a **Process** object from `Get-Process` to this cmdlet.</span></span>

## <span data-ttu-id="076bb-132">출력</span><span class="sxs-lookup"><span data-stu-id="076bb-132">OUTPUTS</span></span>

### <span data-ttu-id="076bb-133">Exit-pshostprocessinfo.</span><span class="sxs-lookup"><span data-stu-id="076bb-133">Microsoft.PowerShell.Commands.PSHostProcessInfo</span></span>

## <span data-ttu-id="076bb-134">참고</span><span class="sxs-lookup"><span data-stu-id="076bb-134">NOTES</span></span>

## <span data-ttu-id="076bb-135">관련 링크</span><span class="sxs-lookup"><span data-stu-id="076bb-135">RELATED LINKS</span></span>

[<span data-ttu-id="076bb-136">Get-Process</span><span class="sxs-lookup"><span data-stu-id="076bb-136">Get-Process</span></span>](../Microsoft.PowerShell.Management/get-process.md)
