---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-EventLog
ms.openlocfilehash: e8dbcf1aa4280c0481714a8a9fb24f2e5ef79ffe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214409"
---
# <span data-ttu-id="1aa93-103">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="1aa93-103">Show-EventLog</span></span>

## <span data-ttu-id="1aa93-104">개요</span><span class="sxs-lookup"><span data-stu-id="1aa93-104">SYNOPSIS</span></span>
<span data-ttu-id="1aa93-105">로컬 또는 원격 컴퓨터의 이벤트 뷰어에 있는 이벤트 로그를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa93-105">Displays the event logs of the local or a remote computer in Event Viewer.</span></span>

## <span data-ttu-id="1aa93-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1aa93-106">SYNTAX</span></span>

```
Show-EventLog [[-ComputerName] <String>] [<CommonParameters>]
```

## <span data-ttu-id="1aa93-107">설명</span><span class="sxs-lookup"><span data-stu-id="1aa93-107">DESCRIPTION</span></span>
<span data-ttu-id="1aa93-108">**이벤트 표시** cmdlet은 로컬 컴퓨터에서 이벤트 뷰어를 열고 로컬 컴퓨터 또는 원격 컴퓨터의 모든 클래식 이벤트 로그에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa93-108">The **Show-EventLog** cmdlet opens Event Viewer on the local computer and displays in it all of the classic event logs on the local computer or a remote computer.</span></span>

<span data-ttu-id="1aa93-109">Windows Vista 이상 버전의 Windows 운영 체제에서 이벤트 뷰어를 열려면 현재 사용자가 로컬 컴퓨터에서 Administrators 그룹의 구성원 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa93-109">To open Event Viewer on Windows Vista and later versions of the Windows operating system, the current user must be a member of the Administrators group on the local computer.</span></span>

<span data-ttu-id="1aa93-110">**Eventlog** 명사를 포함 하는 Cmdlet ( **eventlog** cmdlet)은 클래식 이벤트 로그 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa93-110">The cmdlets that contain the **EventLog** noun (the **EventLog** cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="1aa93-111">Windows Vista 이상 버전의 windows 운영 체제에서 Windows 이벤트 로그 기술을 사용 하는 로그에서 이벤트를 가져오려면 Get-WinEvent cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa93-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of the Windows operating system, use the Get-WinEvent cmdlet.</span></span>

## <span data-ttu-id="1aa93-112">예제</span><span class="sxs-lookup"><span data-stu-id="1aa93-112">EXAMPLES</span></span>

### <span data-ttu-id="1aa93-113">예 1: 로컬 컴퓨터에 대 한 이벤트 로그 표시</span><span class="sxs-lookup"><span data-stu-id="1aa93-113">Example 1: Display event logs for the local computer</span></span>

```
PS C:\> Show-EventLog
```

<span data-ttu-id="1aa93-114">이 명령은 이벤트 뷰어를 열고 로컬 컴퓨터에 있는 기본 이벤트 로그를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa93-114">This command opens Event Viewer and displays in it the classic event logs on the local computer.</span></span>

### <span data-ttu-id="1aa93-115">예 2: 원격 컴퓨터에 대 한 이벤트 로그 표시</span><span class="sxs-lookup"><span data-stu-id="1aa93-115">Example 2: Display event logs for a remote computer</span></span>

```
PS C:\> Show-EventLog -ComputerName "Server01"
```

<span data-ttu-id="1aa93-116">이 명령은 이벤트 뷰어를 열고 Server01 컴퓨터에 있는 기본 이벤트 로그를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa93-116">This command opens Event Viewer and displays in it the classic event logs on the Server01 computer.</span></span>

## <span data-ttu-id="1aa93-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1aa93-117">PARAMETERS</span></span>

### <span data-ttu-id="1aa93-118">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="1aa93-118">-ComputerName</span></span>
<span data-ttu-id="1aa93-119">원격 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa93-119">Specifies a remote computer.</span></span>
<span data-ttu-id="1aa93-120">**표시-** 이벤트 로그를 로컬 컴퓨터의 이벤트 뷰어 지정 된 컴퓨터에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1aa93-120">**Show-EventLog** displays the event logs from the specified computer in Event Viewer on the local computer.</span></span>
<span data-ttu-id="1aa93-121">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="1aa93-121">The default is the local computer.</span></span>

<span data-ttu-id="1aa93-122">원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="1aa93-122">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>

<span data-ttu-id="1aa93-123">이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1aa93-123">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="1aa93-124">원격 명령을 실행하도록 컴퓨터를 구성하지 않은 경우에도 *ComputerName* 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1aa93-124">You can use the *ComputerName* parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aa93-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1aa93-125">CommonParameters</span></span>
<span data-ttu-id="1aa93-126">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1aa93-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1aa93-127">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1aa93-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1aa93-128">입력</span><span class="sxs-lookup"><span data-stu-id="1aa93-128">INPUTS</span></span>

### <span data-ttu-id="1aa93-129">없음</span><span class="sxs-lookup"><span data-stu-id="1aa93-129">None</span></span>
<span data-ttu-id="1aa93-130">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1aa93-130">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="1aa93-131">출력</span><span class="sxs-lookup"><span data-stu-id="1aa93-131">OUTPUTS</span></span>

### <span data-ttu-id="1aa93-132">없음</span><span class="sxs-lookup"><span data-stu-id="1aa93-132">None</span></span>
<span data-ttu-id="1aa93-133">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1aa93-133">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1aa93-134">참고</span><span class="sxs-lookup"><span data-stu-id="1aa93-134">NOTES</span></span>

* <span data-ttu-id="1aa93-135">이벤트 뷰어를 열면 Windows PowerShell 명령 프롬프트가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1aa93-135">The Windows PowerShell command prompt returns as soon as Event Viewer opens.</span></span> <span data-ttu-id="1aa93-136">이벤트 뷰어가 열려 있는 동안 현재 세션에서 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1aa93-136">You can work in the current session while Event Viewer is open.</span></span>

  <span data-ttu-id="1aa93-137">이 cmdlet은 사용자 인터페이스가 필요하므로 Windows Server의 Server Core 설치에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1aa93-137">Because this cmdlet requires a user interface, it does not work on Server Core installations of Windows Server.</span></span>

*

## <span data-ttu-id="1aa93-138">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1aa93-138">RELATED LINKS</span></span>

[<span data-ttu-id="1aa93-139">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="1aa93-139">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="1aa93-140">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="1aa93-140">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="1aa93-141">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="1aa93-141">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="1aa93-142">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="1aa93-142">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="1aa93-143">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="1aa93-143">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="1aa93-144">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="1aa93-144">Write-EventLog</span></span>](Write-EventLog.md)
