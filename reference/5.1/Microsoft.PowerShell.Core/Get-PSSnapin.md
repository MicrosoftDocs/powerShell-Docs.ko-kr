---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSnapin
ms.openlocfilehash: 472a4c8fbb9eb0d37827aff4fcfd6bb9a67f4743
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212001"
---
# <span data-ttu-id="afc55-103">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="afc55-103">Get-PSSnapin</span></span>

## <span data-ttu-id="afc55-104">개요</span><span class="sxs-lookup"><span data-stu-id="afc55-104">SYNOPSIS</span></span>
<span data-ttu-id="afc55-105">컴퓨터의 Windows PowerShell 스냅인을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-105">Gets the Windows PowerShell snap-ins on the computer.</span></span>

## <span data-ttu-id="afc55-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="afc55-106">SYNTAX</span></span>

```
Get-PSSnapin [[-Name] <String[]>] [-Registered] [<CommonParameters>]
```

## <span data-ttu-id="afc55-107">설명</span><span class="sxs-lookup"><span data-stu-id="afc55-107">DESCRIPTION</span></span>
<span data-ttu-id="afc55-108">**Add-pssnapin** cmdlet은 현재 세션에 추가 되었거나 시스템에 등록 된 Windows PowerShell 스냅인을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-108">The **Get-PSSnapin** cmdlet gets the Windows PowerShell snap-ins that have been added to the current session or that have been registered on the system.</span></span>
<span data-ttu-id="afc55-109">이 cmdlet은 검색 된 순서 대로 스냅인을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-109">This cmdlet lists the snap-ins in the order in which they are detected.</span></span>

<span data-ttu-id="afc55-110">**Add-pssnapin** 는 등록 된 스냅인만 가져옵니다. Windows PowerShell 스냅인을 등록 하려면 Microsoft .NET Framework 2.0에 포함 된 Installutil.exe 도구를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-110">**Get-PSSnapin** gets only registered snap-ins. To register a Windows PowerShell snap-in, use the InstallUtil tool included with the Microsoft .NET Framework 2.0.</span></span>
<span data-ttu-id="afc55-111">자세한 내용은 MSDN library에서 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](https://go.microsoft.com/fwlink/?LinkID=143619) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="afc55-111">For more information, see [How to Register Cmdlets, Providers, and Host Applications](https://go.microsoft.com/fwlink/?LinkID=143619) in the MSDN library.</span></span>

<span data-ttu-id="afc55-112">Windows PowerShell 3.0 부터는 Windows PowerShell에 포함 된 핵심 명령이 모듈에 패키지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-112">Starting in Windows PowerShell 3.0, the core commands that are included in Windows PowerShell are packaged in modules.</span></span>
<span data-ttu-id="afc55-113">단, 스냅인(PSSnapin)인 **Microsoft.PowerShell.Core** 는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-113">The exception is **Microsoft.PowerShell.Core** , which is a snap-in (PSSnapin).</span></span>
<span data-ttu-id="afc55-114">기본적으로 **Microsoft.PowerShell.Core** 스냅인만 세션에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-114">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span>
<span data-ttu-id="afc55-115">모듈은 처음 사용할 때 자동으로 가져오며 Import-Module cmdlet을 사용 하 여 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-115">Modules are imported automatically on first use and you can use the Import-Module cmdlet to import them.</span></span>

## <span data-ttu-id="afc55-116">예제</span><span class="sxs-lookup"><span data-stu-id="afc55-116">EXAMPLES</span></span>

### <span data-ttu-id="afc55-117">예제 1: 현재 로드 된 스냅인 가져오기</span><span class="sxs-lookup"><span data-stu-id="afc55-117">Example 1: Get snap-ins that are currently loaded</span></span>

```
PS C:\> Get-PSSnapIn
```

<span data-ttu-id="afc55-118">이 명령은 세션에 현재 로드된 Windows PowerShell 스냅인을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-118">This command gets the Windows PowerShell snap-ins that are currently loaded in the session.</span></span>
<span data-ttu-id="afc55-119">여기에는 Windows PowerShell과 함께 설치된 스냅인과 세션에 추가된 스냅인이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-119">This includes the snap-ins that are installed with Windows PowerShell and those that have been added to the session.</span></span>

### <span data-ttu-id="afc55-120">예제 2: 등록 된 스냅인 가져오기</span><span class="sxs-lookup"><span data-stu-id="afc55-120">Example 2: Get snap-ins that have been registered</span></span>

```
PS C:\> get-PSSnapIn -Registered
```

<span data-ttu-id="afc55-121">이 명령은 세션에 이미 추가된 스냅인을 비롯하여 컴퓨터에 등록된 Windows PowerShell 스냅인을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-121">This command gets the Windows PowerShell snap-ins that have been registered on the computer, including those that have already been added to the session.</span></span>
<span data-ttu-id="afc55-122">Windows PowerShell과 함께 설치된 스냅인이나 시스템에 아직 등록되지 않은 Windows PowerShell 스냅인 DLL(동적 연결 라이브러리)은 출력에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-122">The output does not include snap-ins that are installed with Windows PowerShell or Windows PowerShell snap-in dynamic-link libraries (DLLs) that have not yet been registered on the system.</span></span>

### <span data-ttu-id="afc55-123">예제 3: 문자열과 일치 하는 현재 스냅인 가져오기</span><span class="sxs-lookup"><span data-stu-id="afc55-123">Example 3: Get current snap-ins that match a string</span></span>

```
PS C:\> Get-PSSnapIn -Name smp*
```

<span data-ttu-id="afc55-124">이 명령은 현재 세션에서 이름이 smp로 시작 하는 Windows PowerShell 스냅인을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-124">This command gets the Windows PowerShell snap-ins in the current session that have names that begin with smp.</span></span>

## <span data-ttu-id="afc55-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="afc55-125">PARAMETERS</span></span>

### <span data-ttu-id="afc55-126">-Name</span><span class="sxs-lookup"><span data-stu-id="afc55-126">-Name</span></span>
<span data-ttu-id="afc55-127">스냅인 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-127">Specifies an array of snap-in names.</span></span>
<span data-ttu-id="afc55-128">이 cmdlet은 지정 된 Windows PowerShell 스냅인만 가져옵니다. 와일드 카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-128">This cmdlet gets only the specified Windows PowerShell snap-ins. Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afc55-129">-등록 됨</span><span class="sxs-lookup"><span data-stu-id="afc55-129">-Registered</span></span>
<span data-ttu-id="afc55-130">이 cmdlet은 세션에 아직 추가 되지 않은 경우에도 시스템에 등록 된 Windows PowerShell 스냅인을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-130">Indicates that this cmdlet gets the Windows PowerShell snap-ins that have been registered on the system even if they have not yet been added to the session.</span></span>

<span data-ttu-id="afc55-131">Windows PowerShell과 함께 설치된 스냅인은 이 목록에 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-131">The snap-ins that are installed with Windows PowerShell do not appear in this list.</span></span>

<span data-ttu-id="afc55-132">이 매개 변수를 **사용** 하지 않으면 add-pssnapin은 세션에 추가 된 Windows PowerShell 스냅인을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-132">Without this parameter, **Get-PSSnapin** gets the Windows PowerShell snap-ins that have been added to the session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afc55-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="afc55-133">CommonParameters</span></span>
<span data-ttu-id="afc55-134">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="afc55-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="afc55-135">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="afc55-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="afc55-136">입력</span><span class="sxs-lookup"><span data-stu-id="afc55-136">INPUTS</span></span>

### <span data-ttu-id="afc55-137">없음</span><span class="sxs-lookup"><span data-stu-id="afc55-137">None</span></span>
<span data-ttu-id="afc55-138">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-138">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="afc55-139">출력</span><span class="sxs-lookup"><span data-stu-id="afc55-139">OUTPUTS</span></span>

### <span data-ttu-id="afc55-140">PSSnapInInfo.</span><span class="sxs-lookup"><span data-stu-id="afc55-140">System.Management.Automation.PSSnapInInfo</span></span>
<span data-ttu-id="afc55-141">Get-PSSnapin은 가져오는 각 스냅인에 대한 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-141">Get-PSSnapin returns an object for each snap-in that it gets.</span></span>

## <span data-ttu-id="afc55-142">참고</span><span class="sxs-lookup"><span data-stu-id="afc55-142">NOTES</span></span>

* <span data-ttu-id="afc55-143">Windows PowerShell 3.0 부터는 Windows PowerShell과 함께 설치 되는 핵심 명령이 모듈에 패키지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-143">Starting in Windows PowerShell 3.0, the core commands that are installed with Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="afc55-144">Windows PowerShell 2.0 및 이후 버전의 Windows PowerShell에서 이전 스타일의 세션을 만드는 호스트 프로그램에서 핵심 명령은 스냅인 ( **add-pssnapin** )으로 패키지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-144">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of Windows PowerShell, the core commands are packaged in snap-ins ( **PSSnapin** ).</span></span> <span data-ttu-id="afc55-145">예외는 항상 스냅인 인 **Microsoft. PowerShell. Core** 입니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-145">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="afc55-146">또한 New-PSSession cmdlet에서 시작한 것과 같은 원격 세션은 코어 스냅인을 포함 하는 이전 스타일의 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="afc55-146">Also, remote sessions, such as those started by the New-PSSession cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="afc55-147">핵심 모듈을 사용 하 여 최신 스타일의 세션을 만드는 **initialsessionstate.createdefault2** 메서드에 대 한 자세한 내용은 MSDN Library의 [initialsessionstate.createdefault2 메서드](https://msdn.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.createdefault2) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="afc55-147">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](https://msdn.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.createdefault2) in the MSDN library.</span></span>

## <span data-ttu-id="afc55-148">관련 링크</span><span class="sxs-lookup"><span data-stu-id="afc55-148">RELATED LINKS</span></span>

[<span data-ttu-id="afc55-149">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="afc55-149">Add-PSSnapin</span></span>](Add-PSSnapin.md)

[<span data-ttu-id="afc55-150">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="afc55-150">Remove-PSSnapin</span></span>](Remove-PSSnapin.md)
