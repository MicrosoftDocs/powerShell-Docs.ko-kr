---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-PSSnapin
ms.openlocfilehash: a21c2974fd66a9b02929752ae487c8995579b8a7
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388827"
---
# <span data-ttu-id="fd6b0-103">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="fd6b0-103">Add-PSSnapin</span></span>

## <span data-ttu-id="fd6b0-104">개요</span><span class="sxs-lookup"><span data-stu-id="fd6b0-104">SYNOPSIS</span></span>
<span data-ttu-id="fd6b0-105">하나 이상의 Windows PowerShell 스냅인을 현재 세션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-105">Adds one or more Windows PowerShell snap-ins to the current session.</span></span>

## <span data-ttu-id="fd6b0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fd6b0-106">SYNTAX</span></span>

```
Add-PSSnapin [-Name] <String[]> [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="fd6b0-107">설명</span><span class="sxs-lookup"><span data-stu-id="fd6b0-107">DESCRIPTION</span></span>

<span data-ttu-id="fd6b0-108">`Add-PSSnapin`Cmdlet은 등록 된 Windows PowerShell 스냅인을 현재 세션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-108">The `Add-PSSnapin` cmdlet adds registered Windows PowerShell snap-ins to the current session.</span></span> <span data-ttu-id="fd6b0-109">스냅인이 추가되고 나면 현재 세션에서 스냅인이 지원하는 공급자와 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-109">After the snap-ins are added, you can use the cmdlets and providers that the snap-ins support in the current session.</span></span>

<span data-ttu-id="fd6b0-110">모든 향후 Windows PowerShell 세션에 스냅인을 추가 하려면 `Add-PSSnapin` Windows powershell 프로필에 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-110">To add the snap-in to all future Windows PowerShell sessions, add an `Add-PSSnapin` command to your Windows PowerShell profile.</span></span> <span data-ttu-id="fd6b0-111">자세한 내용은 [about_Profiles](about/about_Profiles.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-111">For more information, see [about_Profiles](about/about_Profiles.md).</span></span>

<span data-ttu-id="fd6b0-112">Windows PowerShell 3.0부터는 Windows PowerShell에 포함되는 핵심 명령이 모듈에 패키지됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-112">Beginning in Windows PowerShell 3.0, the core commands that are included in Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="fd6b0-113">단, 스냅인(PSSnapin)인 **Microsoft.PowerShell.Core** 는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-113">The exception is **Microsoft.PowerShell.Core** , which is a snap-in (PSSnapin).</span></span>
<span data-ttu-id="fd6b0-114">기본적으로 **Microsoft.PowerShell.Core** 스냅인만 세션에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-114">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span> <span data-ttu-id="fd6b0-115">모듈은 처음 사용할 때 자동으로 가져오며 Import-Module cmdlet을 사용 하 여 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-115">Modules are imported automatically on first use and you can use the Import-Module cmdlet to import them.</span></span>

## <span data-ttu-id="fd6b0-116">예제</span><span class="sxs-lookup"><span data-stu-id="fd6b0-116">EXAMPLES</span></span>

### <span data-ttu-id="fd6b0-117">예제 1: 스냅인 추가</span><span class="sxs-lookup"><span data-stu-id="fd6b0-117">Example 1: Add snap-ins</span></span>

```powershell
PS C:\> Add-PSSnapIn -Name Microsoft.Exchange, Microsoft.Windows.AD
```

<span data-ttu-id="fd6b0-118">이 명령은 Microsoft Exchange 및 Active Directory 스냅인을 현재 세션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-118">This command adds the Microsoft Exchange and Active Directory snap-ins to the current session.</span></span>

### <span data-ttu-id="fd6b0-119">예제 2: 등록 된 모든 스냅인 추가</span><span class="sxs-lookup"><span data-stu-id="fd6b0-119">Example 2: Add all the registered snap-ins</span></span>

```powershell
PS C:\> Get-PSSnapin -Registered | Add-PSSnapin -Passthru
```

<span data-ttu-id="fd6b0-120">이 명령은 등록된 모든 Windows PowerShell 스냅인을 세션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-120">This command adds all of the registered Windows PowerShell snap-ins to the session.</span></span> <span data-ttu-id="fd6b0-121">**등록 된 매개 변수와 함께** Get-PSSnapin cmdlet을 사용 하 여 등록 된 각 스냅인을 나타내는 개체를 가져옵니다. 파이프라인 연산자 (|)는 결과를에 전달 하 여 `Add-PSSnapin` 세션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-121">It uses the Get-PSSnapin cmdlet with the **Registered** parameter to get objects representing each of the registered snap-ins. The pipeline operator (|) passes the result to `Add-PSSnapin`, which adds them to the session.</span></span> <span data-ttu-id="fd6b0-122">**PassThru** 매개 변수는 추가 된 각 스냅인을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-122">The **PassThru** parameter returns objects that represent each of the added snap-ins.</span></span>

### <span data-ttu-id="fd6b0-123">예제 3: 스냅인 등록 및 추가</span><span class="sxs-lookup"><span data-stu-id="fd6b0-123">Example 3: Register a snap-in and add it</span></span>

<span data-ttu-id="fd6b0-124">첫 번째 명령은 Windows PowerShell과 함께 설치 된 스냅인을 포함 하는 현재 세션에 추가 된 스냅인을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-124">The first command gets snap-ins that have been added to the current session that include the snap-ins that are installed with Windows PowerShell.</span></span> <span data-ttu-id="fd6b0-125">이 예제에서 ManagementFeatures는 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-125">In this example, ManagementFeatures is not returned.</span></span> <span data-ttu-id="fd6b0-126">이는 ManagementFeatures가 세션에 추가되지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-126">This indicates that it has not been added to the session.</span></span>

<span data-ttu-id="fd6b0-127">두 번째 명령은 세션에 이미 추가 된 스냅인을 포함 하 여 시스템에 등록 된 스냅인을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-127">The second command gets snap-ins that have been registered on your system, which includes those that have already been added to the session.</span></span> <span data-ttu-id="fd6b0-128">Windows PowerShell과 함께 설치 된 스냅인은 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-128">It does not include the snap-ins that are installed with Windows PowerShell.</span></span> <span data-ttu-id="fd6b0-129">이 경우 명령은 스냅인을 반환 하지 않습니다. 이는 ManagementFeatures 스냅인이 시스템에 등록 되지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-129">In this case, the command does not return any snap-ins. This indicates that the ManagementFeatures snapin has not been registered on the system.</span></span>

<span data-ttu-id="fd6b0-130">세 번째 명령은 .NET Framework에서 Installutil.exe 도구의 경로에 대 한 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-130">The third command creates an alias, installutil, for the path of the InstallUtil tool in .NET Framework.</span></span>

<span data-ttu-id="fd6b0-131">네 번째 명령은 Installutil.exe 도구를 사용 하 여 스냅인을 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-131">The fourth command uses the InstallUtil tool to register the snap-in.</span></span> <span data-ttu-id="fd6b0-132">명령은 ManagementCmdlets.dll의 경로, 파일 이름 또는 스냅인의 모듈 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-132">The command specifies the path of ManagementCmdlets.dll, the filename or module name of the snap-in.</span></span>

<span data-ttu-id="fd6b0-133">다섯 번째 명령은 두 번째 명령과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-133">The fifth command is the same as the second command.</span></span> <span data-ttu-id="fd6b0-134">이번에는 이 명령을 사용하여 ManagementCmdlets 스냅인이 등록되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-134">This time, you use it to verify that the ManagementCmdlets snap-in is registered.</span></span>

<span data-ttu-id="fd6b0-135">여섯 번째 명령은 cmdlet을 사용 하 여 `Add-PSSnapin` ManagementFeatures 스냅인을 세션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-135">The sixth command uses the `Add-PSSnapin` cmdlet to add the ManagementFeatures snap-in to the session.</span></span> <span data-ttu-id="fd6b0-136">이 명령은 파일 이름이 아니라 스냅인의 이름인 ManagementFeatures를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-136">It specifies the name of the snap-in, ManagementFeatures, not the file name.</span></span>

<span data-ttu-id="fd6b0-137">스냅인이 세션에 추가 되었는지 확인 하기 위해 일곱 번째 명령은 Get-Command cmdlet의 **Module** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-137">To verify that the snap-in is added to the session, the seventh command uses the **Module** parameter of the Get-Command cmdlet.</span></span> <span data-ttu-id="fd6b0-138">이 명령은 스냅인이나 모듈에서 세션에 추가한 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-138">It displays the items that were added to the session by a snap-in or module.</span></span>

<span data-ttu-id="fd6b0-139">Cmdlet이 반환 하는 개체의 **add-pssnapin** 속성을 사용 하 여 `Get-Command` cmdlet이 시작 된 스냅인 또는 모듈을 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-139">You can also use the **PSSnapin** property of the object that the `Get-Command` cmdlet returns to find the snap-in or module in which a cmdlet originated.</span></span> <span data-ttu-id="fd6b0-140">여덟 번째 명령은 점 표기법을 사용 하 여 Set-Alias cmdlet의 Add-pssnapin 속성 값을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-140">The eighth command uses dot notation to find the value of the PSSnapin property of the Set-Alias cmdlet.</span></span>

```powershell
PS C:\> Get-PSSnapin
PS C:\> Get-PSSnapin -Registered
PS C:\> Set-Alias installutil $env:windir\Microsoft.NET\Framework\v2.0.50727\installutil.exe
PS C:\> installutil C:\Dev\Management\ManagementCmdlets.dll
PS C:\> Get-PSSnapin -Registered
PS C:\> add-pssnapin ManagementFeatures
PS C:\> Get-Command -Module ManagementFeatures
PS C:\> (Get-Command Set-Alias).pssnapin
```

<span data-ttu-id="fd6b0-141">이 예제에서는 시스템에서 스냅인을 등록한 다음 세션에 추가하는 프로세스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-141">This example demonstrates the process of registering a snap-in on your system and then adding it to your session.</span></span> <span data-ttu-id="fd6b0-142">ManagementCmdlets.dll 이라는 파일에 구현 된 가상의 스냅인 인 ManagementFeatures를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-142">It uses ManagementFeatures, a fictitious snap-in implemented in a file that is named ManagementCmdlets.dll.</span></span>

## <span data-ttu-id="fd6b0-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fd6b0-143">PARAMETERS</span></span>

### <span data-ttu-id="fd6b0-144">-Name</span><span class="sxs-lookup"><span data-stu-id="fd6b0-144">-Name</span></span>

<span data-ttu-id="fd6b0-145">스냅인의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-145">Specifies the name of the snap-in.</span></span> <span data-ttu-id="fd6b0-146">AssemblyName 또는 ModuleName이 아닌 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-146">This is the Name, not the AssemblyName or ModuleName.</span></span> <span data-ttu-id="fd6b0-147">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-147">Wildcards are permitted.</span></span>

<span data-ttu-id="fd6b0-148">시스템에서 등록 된 스냅인의 이름을 찾으려면를 입력 `Get-PSSnapin -Registered` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-148">To find the names of the registered snap-ins on your system, type `Get-PSSnapin -Registered`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="fd6b0-149">-PassThru</span><span class="sxs-lookup"><span data-stu-id="fd6b0-149">-PassThru</span></span>

<span data-ttu-id="fd6b0-150">이 cmdlet이 추가 된 각 스냅인을 나타내는 개체를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-150">Indicates that this cmdlet returns an object that represents each added snap-in.</span></span> <span data-ttu-id="fd6b0-151">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-151">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="fd6b0-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fd6b0-152">CommonParameters</span></span>

<span data-ttu-id="fd6b0-153">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fd6b0-154">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fd6b0-155">입력</span><span class="sxs-lookup"><span data-stu-id="fd6b0-155">INPUTS</span></span>

### <span data-ttu-id="fd6b0-156">없음</span><span class="sxs-lookup"><span data-stu-id="fd6b0-156">None</span></span>
<span data-ttu-id="fd6b0-157">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-157">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="fd6b0-158">출력</span><span class="sxs-lookup"><span data-stu-id="fd6b0-158">OUTPUTS</span></span>

### <span data-ttu-id="fd6b0-159">없음 또는 PSSnapInInfo</span><span class="sxs-lookup"><span data-stu-id="fd6b0-159">None or System.Management.Automation.PSSnapInInfo</span></span>

<span data-ttu-id="fd6b0-160">이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 스냅인을 나타내는 PSSnapInInfo 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-160">This cmdlet returns a PSSnapInInfo object that represents the snap-in if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="fd6b0-161">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-161">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="fd6b0-162">참고</span><span class="sxs-lookup"><span data-stu-id="fd6b0-162">NOTES</span></span>

- <span data-ttu-id="fd6b0-163">Windows PowerShell 3.0부터 Windows PowerShell과 함께 설치된 핵심 명령이 모듈에 패키지됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-163">Beginning in Windows PowerShell 3.0, the core commands that are installed with Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="fd6b0-164">Windows PowerShell 2.0 및 이후 버전의 Windows PowerShell에서 이전 스타일의 세션을 만드는 호스트 프로그램에서 핵심 명령은 스냅인 (PSSnapins)으로 패키지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-164">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of Windows PowerShell, the core commands are packaged in snap-ins (PSSnapins).</span></span> <span data-ttu-id="fd6b0-165">예외는 항상 스냅인 인 **Microsoft. PowerShell. Core** 입니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-165">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="fd6b0-166">또한 New-PSSession cmdlet에서 시작한 것과 같은 원격 세션은 코어 스냅인을 포함 하는 이전 스타일의 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-166">Also, remote sessions, such as those started by the New-PSSession cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="fd6b0-167">핵심 모듈과 함께 최신 스타일의 세션을 만드는 **initialsessionstate.createdefault2** 메서드에 대 한 자세한 내용은 [initialsessionstate.createdefault2 메서드](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-167">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2).</span></span>

- <span data-ttu-id="fd6b0-168">스냅인에 대 한 자세한 내용은 [about_PSSnapins](About/about_PSSnapins.md) 및 [Windows PowerShell 스냅인을 만드는 방법](/powershell/scripting/developer/cmdlet/how-to-create-a-windows-powershell-snap-in)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-168">For more information about snap-ins, see [about_PSSnapins](About/about_PSSnapins.md) and [How to Create a Windows PowerShell Snap-in](/powershell/scripting/developer/cmdlet/how-to-create-a-windows-powershell-snap-in).</span></span>
- <span data-ttu-id="fd6b0-169">`Add-PSSnapin` 현재 세션에만 스냅인을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-169">`Add-PSSnapin` adds the snap-in only to the current session.</span></span> <span data-ttu-id="fd6b0-170">모든 Windows PowerShell 세션에 스냅인을 추가하려면 스냅인을 Windows PowerShell 프로필에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-170">To add the snap-in to all Windows PowerShell sessions, add it to your Windows PowerShell profile.</span></span> <span data-ttu-id="fd6b0-171">자세한 내용은 about_Profiles를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-171">For more information, see about_Profiles.</span></span>
- <span data-ttu-id="fd6b0-172">Microsoft .NET Framework 설치 유틸리티를 사용 하 여 등록 된 모든 스냅인을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-172">You can add any snap-in that has been registered using the Microsoft .NET Framework install utility.</span></span> <span data-ttu-id="fd6b0-173">자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-173">For more information, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>
- <span data-ttu-id="fd6b0-174">컴퓨터에 등록 된 스냅인 목록을 가져오려면를 입력 `Get-PSSnapin -Registered` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-174">To get a list of snap-ins that are registered on your computer, type `Get-PSSnapin -Registered`.</span></span>
- <span data-ttu-id="fd6b0-175">스냅인을 추가 하기 전에는 `Add-PSSnapin` 스냅인의 버전을 확인 하 여 현재 버전의 Windows PowerShell과 호환 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-175">Before adding a snap-in, `Add-PSSnapin` checks the version of the snap-in to verify that it is compatible with the current version of Windows PowerShell.</span></span> <span data-ttu-id="fd6b0-176">스냅인이 버전 확인에 실패하면 Windows PowerShell에서 오류를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="fd6b0-176">If the snap-in fails the version check, Windows PowerShell reports an error.</span></span>

## <span data-ttu-id="fd6b0-177">관련 링크</span><span class="sxs-lookup"><span data-stu-id="fd6b0-177">RELATED LINKS</span></span>

[<span data-ttu-id="fd6b0-178">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="fd6b0-178">Get-PSSnapin</span></span>](Get-PSSnapin.md)

[<span data-ttu-id="fd6b0-179">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="fd6b0-179">Remove-PSSnapin</span></span>](Remove-PSSnapin.md)
