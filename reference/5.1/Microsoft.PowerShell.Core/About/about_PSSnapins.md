---
description: Windows PowerShell 스냅인에 대해 설명 하 고이 스냅인을 사용 하 고 관리 하는 방법을 보여 줍니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSnapins
ms.openlocfilehash: cc22f8de0b9d8a55dcfa12f3b47f3852d891e67b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222665"
---
# <a name="about-pssnapins"></a><span data-ttu-id="c2e2e-104">PSSnapins 정보</span><span class="sxs-lookup"><span data-stu-id="c2e2e-104">About PSSnapins</span></span>

## <a name="short-description"></a><span data-ttu-id="c2e2e-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="c2e2e-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="c2e2e-106">Windows PowerShell 스냅인에 대해 설명 하 고이 스냅인을 사용 하 고 관리 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-106">Describes  Windows PowerShell snap-ins and shows how to use and manage them.</span></span>

## <a name="long-description"></a><span data-ttu-id="c2e2e-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="c2e2e-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="c2e2e-108">Windows PowerShell 스냅인은 Windows PowerShell 공급자 및 또는 cmdlet을 포함 하는 Microsoft .NET 프레임 워크 어셈블리입니다 \/ .</span><span class="sxs-lookup"><span data-stu-id="c2e2e-108">A Windows PowerShell snap-in is a Microsoft .NET Framework assembly that contains Windows PowerShell providers and\/or cmdlets.</span></span> <span data-ttu-id="c2e2e-109">Windows PowerShell에는 일련의 기본 스냅인이 포함 되어 있지만 사용자가 만들거나 다른 사용자가 가져온 공급자와 cmdlet을 포함 하는 스냅인을 추가 하 여 Windows PowerShell의 기능과 가치를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-109">Windows PowerShell includes a set of basic snap-ins, but you can extend the power and value of Windows PowerShell by adding snap-ins that contain providers and cmdlets that you create or get from others.</span></span>

<span data-ttu-id="c2e2e-110">스냅인을 추가 하면 해당 스냅인에 포함 된 cmdlet 및 공급자가 현재 세션에서 즉시 사용할 수 있지만 변경 내용은 현재 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-110">When you add a snap-in, the cmdlets and providers that it contains are immediately available for use in the current session, but the change affects only the current session.</span></span>

<span data-ttu-id="c2e2e-111">모든 이후 세션에 스냅인을 추가 하려면 Windows PowerShell 프로필에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-111">To add the snap-in to all future sessions, save it in your Windows PowerShell profile.</span></span> <span data-ttu-id="c2e2e-112">Export-Console cmdlet을 사용 하 여 스냅인 이름을 콘솔 파일에 저장 한 다음 이후 세션에서 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-112">You can also use the Export-Console cmdlet to save the snap-in names to a console file and then use it in future sessions.</span></span> <span data-ttu-id="c2e2e-113">각각 서로 다른 스냅인 집합을 사용 하 여 여러 콘솔 파일을 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-113">You can even save multiple console files, each with a different set of snap-ins.</span></span>

<span data-ttu-id="c2e2e-114">참고: windows powershell 스냅인 (PSSnapins)은 Windows powershell 3.0 및 Windows PowerShell 2.0에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-114">NOTE: Windows PowerShell snap-ins (PSSnapins) are available for use in Windows PowerShell 3.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="c2e2e-115">이후 버전에서 변경 되거나 사용할 수 없게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-115">They might be altered or unavailable in subsequent versions.</span></span> <span data-ttu-id="c2e2e-116">Windows PowerShell cmdlet 및 공급자를 패키징하려면 모듈을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-116">To package Windows PowerShell cmdlets and providers, use modules.</span></span> <span data-ttu-id="c2e2e-117">모듈을 만들고 스냅인을 모듈로 변환 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 모듈 작성](/powershell/scripting/developer/module/writing-a-windows-powershell-module)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-117">For information about creating modules and converting snap-ins to modules, see [Writing a Windows PowerShell Module](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span></span>

### <a name="finding-snap-ins"></a><span data-ttu-id="c2e2e-118">스냅인 찾기</span><span class="sxs-lookup"><span data-stu-id="c2e2e-118">FINDING SNAP-INS</span></span>

<span data-ttu-id="c2e2e-119">컴퓨터의 Windows PowerShell 스냅인 목록을 가져오려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-119">To get a list of the  Windows PowerShell snap-ins on your computer, type:</span></span>

```powershell
Get-PSSnapin
```

<span data-ttu-id="c2e2e-120">각 Windows PowerShell 공급자에 대 한 스냅인을 가져오려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-120">To get the snap-in for each  Windows PowerShell provider, type:</span></span>

```powershell
Get-PSProvider | Format-List name, pssnapin
```

<span data-ttu-id="c2e2e-121">Windows PowerShell 스냅인에서 cmdlet 목록을 가져오려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-121">To get a list of the cmdlets in a  Windows PowerShell snap-in, type:</span></span>

```powershell
Get-Command -Module <snap-in_name>
```

### <a name="installing-a-snap-in"></a><span data-ttu-id="c2e2e-122">스냅인 설치</span><span class="sxs-lookup"><span data-stu-id="c2e2e-122">INSTALLING A SNAP-IN</span></span>

<span data-ttu-id="c2e2e-123">기본 제공 스냅인이 시스템에 등록 되 고 Windows PowerShell을 시작할 때 기본 세션에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-123">The built-in snap-ins are registered in the system and added to the default session when you start Windows PowerShell.</span></span> <span data-ttu-id="c2e2e-124">그러나 다른 사용자가 만들거나 가져온 스냅인을 등록 한 다음 세션에 스냅인을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-124">However, you have to register snap-ins that you create or obtain from others and then add the snap-ins to your session.</span></span>

### <a name="registering-a-snap-in"></a><span data-ttu-id="c2e2e-125">스냅인 등록</span><span class="sxs-lookup"><span data-stu-id="c2e2e-125">REGISTERING A SNAP-IN</span></span>

<span data-ttu-id="c2e2e-126">Windows PowerShell 스냅인은 .dll 파일로 컴파일되는 .NET Framework 언어로 작성 된 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-126">A Windows PowerShell snap-in is a program written in a .NET Framework language that is compiled into a .dll file.</span></span> <span data-ttu-id="c2e2e-127">스냅인에서 공급자 및 cmdlet을 사용 하려면 먼저 스냅인을 등록 해야 합니다 (레지스트리에 추가).</span><span class="sxs-lookup"><span data-stu-id="c2e2e-127">To use the providers and cmdlets in a snap-in, you must first register the snap-in (add it to the registry).</span></span>

<span data-ttu-id="c2e2e-128">대부분의 스냅인에는 .dll 파일을 등록 하는 설치 프로그램 (.exe 또는 .msi 파일)이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-128">Most snap-ins include an installation program (an .exe or .msi file) that registers the .dll file for you.</span></span> <span data-ttu-id="c2e2e-129">그러나 스냅인을 .dll 파일로 받는 경우 시스템에 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-129">However, if you receive a snap-in as a .dll file, you can register it on your system.</span></span> <span data-ttu-id="c2e2e-130">자세한 내용은 MSDN library에서 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](https://go.microsoft.com/fwlink/?LinkID=143619) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-130">For more information, see [How to Register Cmdlets, Providers, and Host Applications](https://go.microsoft.com/fwlink/?LinkID=143619) in the MSDN library.</span></span>

<span data-ttu-id="c2e2e-131">시스템에서 등록 된 모든 스냅인을 가져오거나 스냅인이 등록 되었는지 확인 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-131">To get all the registered snap-ins on your system or to verify that a snap-in is registered, type:</span></span>

```powershell
Get-PSSnapin -registered
```

### <a name="adding-the-snap-in-to-the-current-session"></a><span data-ttu-id="c2e2e-132">현재 세션에 스냅인 추가</span><span class="sxs-lookup"><span data-stu-id="c2e2e-132">ADDING THE SNAP-IN TO THE CURRENT SESSION</span></span>

<span data-ttu-id="c2e2e-133">현재 세션에 등록 된 스냅인을 추가 하려면 Add-PsSnapin cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-133">To add a registered snap-in to the current session, use the Add-PsSnapin cmdlet.</span></span> <span data-ttu-id="c2e2e-134">예를 들어 세션에 Microsoft SQL Server 스냅인을 추가 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-134">For example, to add the Microsoft SQL Server snap-in to the session, type:</span></span>

```powershell
Add-PSSnapin sql
```

<span data-ttu-id="c2e2e-135">명령이 완료 되 면 스냅인의 공급자 및 cmdlet을 세션에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-135">After the command is completed, the providers and cmdlets in the snap-in are available in the session.</span></span> <span data-ttu-id="c2e2e-136">그러나 저장 하지 않는 한 현재 세션 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-136">However, they are available only in the current session unless you save them.</span></span>

### <a name="saving-the-snap-ins"></a><span data-ttu-id="c2e2e-137">스냅인 저장</span><span class="sxs-lookup"><span data-stu-id="c2e2e-137">SAVING THE SNAP-INS</span></span>

<span data-ttu-id="c2e2e-138">이후 Windows PowerShell 세션에서 스냅인을 사용 하려면 Windows PowerShell 프로필에 Add-PsSnapin 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-138">To use a snap-in in future Windows PowerShell sessions, add the Add-PsSnapin command to your Windows PowerShell profile.</span></span> <span data-ttu-id="c2e2e-139">또는 스냅인 이름을 콘솔 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-139">Or, export the snap-in names to a console file.</span></span>

<span data-ttu-id="c2e2e-140">프로필에 Add-PSSnapin 명령을 추가 하면 이후의 모든 Windows PowerShell 세션에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-140">If you add the Add-PSSnapin command to your profile, it is available in all future Windows PowerShell sessions.</span></span> <span data-ttu-id="c2e2e-141">세션에서 스냅인의 이름을 내보내는 경우 스냅인이 필요한 경우에만 내보내기 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-141">If you export the names of the snap-ins in your session, you can use the export file only when you need the snap-ins.</span></span>

<span data-ttu-id="c2e2e-142">Windows PowerShell 프로필에 Add-PsSnapin 명령을 추가 하려면 프로필을 열고 명령을 붙여넣거나 입력 한 다음 프로필을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-142">To add the Add-PsSnapin command to your Windows PowerShell profile, open your profile, paste or type the command, and then save the profile.</span></span> <span data-ttu-id="c2e2e-143">자세한 내용은 about_Profiles를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-143">For more information, see about_Profiles.</span></span>

<span data-ttu-id="c2e2e-144">콘솔 파일 (. .psc1)의 세션에서 스냅인을 저장 하려면 Export-Console cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-144">To save the snap-ins from a session in console file (.psc1), use the Export-Console cmdlet.</span></span> <span data-ttu-id="c2e2e-145">예를 들어 현재 세션 구성의 스냅인을 현재 디렉터리의 NewConsole 파일에 저장 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-145">For example, to save the snap-ins in the current session configuration to the NewConsole.psc1 file in the current directory, type:</span></span>

```powershell
Export-Console NewConsole
```

<span data-ttu-id="c2e2e-146">자세한 내용은 내보내기-콘솔을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-146">For more information, see Export-Console.</span></span>

### <a name="opening-windows-powershell-with-a-console-file"></a><span data-ttu-id="c2e2e-147">콘솔 파일을 사용 하 여 WINDOWS POWERSHELL 열기</span><span class="sxs-lookup"><span data-stu-id="c2e2e-147">OPENING WINDOWS POWERSHELL WITH A CONSOLE FILE</span></span>

<span data-ttu-id="c2e2e-148">스냅인이 포함 된 콘솔 파일을 사용 하려면 Cmd.exe의 명령 프롬프트나 다른 Windows PowerShell 세션에서 Windows PowerShell (PowerShell.exe)을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-148">To use a console file that includes the snap-in, start Windows PowerShell (PowerShell.exe) from the command prompt in Cmd.exe or in another Windows PowerShell session.</span></span> <span data-ttu-id="c2e2e-149">PsConsoleFile 매개 변수를 사용 하 여 스냅인이 포함 된 콘솔 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-149">Use the PsConsoleFile parameter to specify the console file that includes the snap-in.</span></span> <span data-ttu-id="c2e2e-150">예를 들어 다음 명령은 NewConsole. .psc1 콘솔 파일을 사용 하 여 Windows PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-150">For example, the following command starts Windows PowerShell with the NewConsole.psc1 console file:</span></span>

```powershell
PowerShell.exe -psconsolefile NewConsole.psc1
```

<span data-ttu-id="c2e2e-151">이제 세션에서 스냅인의 공급자 및 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-151">The providers and cmdlets in the snapin are now available for use in the session.</span></span>

### <a name="removing-a-snap-in"></a><span data-ttu-id="c2e2e-152">스냅인 제거</span><span class="sxs-lookup"><span data-stu-id="c2e2e-152">REMOVING A SNAP-IN</span></span>

<span data-ttu-id="c2e2e-153">현재 세션에서 Windows PowerShell 스냅인을 제거 하려면 Remove-PsSnapin cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-153">To remove a Windows PowerShell snap-in from the current session, use the Remove-PsSnapin cmdlet.</span></span> <span data-ttu-id="c2e2e-154">예를 들어 현재 세션에서 SQL Server 스냅인을 제거 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-154">For example, to remove the SQL Server snap-in from the current session, type:</span></span>

```powershell
Remove-PSSnapin sql
```

<span data-ttu-id="c2e2e-155">이 cmdlet은 세션에서 스냅인을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-155">This cmdlet removes the snap-in from the session.</span></span> <span data-ttu-id="c2e2e-156">스냅인은 여전히 로드 되지만 지원 되는 공급자 및 cmdlet은 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-156">The snap-in is still loaded, but the providers and cmdlets that it supports are no longer available.</span></span>

### <a name="built-in-commands"></a><span data-ttu-id="c2e2e-157">기본 제공 명령</span><span class="sxs-lookup"><span data-stu-id="c2e2e-157">BUILT-IN COMMANDS</span></span>

<span data-ttu-id="c2e2e-158">Windows powershell 2.0 및 windows powershell 3.0 이상의 이전 스타일 호스트 프로그램에서 windows PowerShell과 함께 설치 되는 기본 제공 명령은 모든 Windows PowerShell 세션에 자동으로 추가 되는 스냅인에 패키지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-158">In Windows PowerShell 2.0 and in older-style host programs in Windows PowerShell 3.0 and later, the built-in commands that are installed with Windows PowerShell are packaged in snap-ins that are added automatically to every Windows PowerShell session.</span></span>

<span data-ttu-id="c2e2e-159">Windows PowerShell 3.0 부터는 InitialSessionState. Initialsessionstate.createdefault2 메서드를 사용 하 여 세션을 시작 하는 최신 스타일의 호스트 프로그램--기본 제공 명령이 모듈에 패키지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-159">Beginning in Windows PowerShell 3.0, in newer-style host programs -- those that start sessions by using the InitialSessionState.CreateDefault2 method -- the built-in commands are packaged in modules.</span></span> <span data-ttu-id="c2e2e-160">예외는 항상 스냅인으로 나타나는 Microsoft. PowerShell. Core입니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-160">The exception is Microsoft.PowerShell.Core, which always appears as a snap-in.</span></span> <span data-ttu-id="c2e2e-161">코어 스냅인은 기본적으로 모든 세션에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-161">The Core snap-in is included in every session by default.</span></span> <span data-ttu-id="c2e2e-162">기본 제공 모듈은 처음 사용할 때 자동으로 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-162">The built-in modules are loaded automatically on first-use.</span></span>

<span data-ttu-id="c2e2e-163">참고: New-PSSession cmdlet을 사용 하 여 시작 된 세션을 포함 하 여 원격 세션은 기본 제공 명령이 스냅인에 패키지 된 이전 스타일의 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-163">NOTE: Remote sessions, including sessions that are started by using the New-PSSession cmdlet, are older-style sessions in which the built-in commands are packaged in snap-ins.</span></span>

<span data-ttu-id="c2e2e-164">다음 스냅인 (또는 모듈)은 Windows PowerShell과 함께 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-164">The following snap-ins (or modules) are installed with Windows PowerShell.</span></span>

- <span data-ttu-id="c2e2e-165">Microsoft. PowerShell-Windows PowerShell의 기본 기능을 관리 하는 데 사용 되는 공급자 및 cmdlet을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-165">Microsoft.PowerShell.Core - Contains providers and cmdlets used to manage the basic features of Windows PowerShell.</span></span> <span data-ttu-id="c2e2e-166">여기에는 파일 시스템, 레지스트리, 별칭, 환경, 함수 및 변수 공급자와 Get-help, Get-help 및 Get 기록과 같은 기본 cmdlet이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-166">It includes the FileSystem, Registry, Alias, Environment, Function, and Variable providers and basic cmdlets like Get-Help, Get-Command, and Get-History.</span></span>

- <span data-ttu-id="c2e2e-167">Windows PowerShell 호스트에서 사용 하는 cmdlet (예: Start-Transcript 및 중지 기록)이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-167">Microsoft.PowerShell.Host - Contains cmdlets used by the Windows PowerShell host, such as Start-Transcript and Stop-Transcript.</span></span>

- <span data-ttu-id="c2e2e-168">Microsoft. 관리-Windows 기반 기능을 관리 하는 데 사용 되는 Get-Service 및 Get-ChildItem와 같은 cmdlet을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-168">Microsoft.PowerShell.Management - Contains cmdlets such as Get-Service and Get-ChildItem that are used to manage Windows-based features.</span></span>

- <span data-ttu-id="c2e2e-169">Get-authenticodesignature-Acl, Get-및 Convertto-html와 같은 Windows PowerShell 보안을 관리 하는 데 사용 되는 인증서 공급자 및 cmdlet을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-169">Microsoft.PowerShell.Security - Contains the Certificate provider and cmdlets used to manage Windows PowerShell security, such as Get-Acl, Get-AuthenticodeSignature, and ConvertTo-SecureString.</span></span>

- <span data-ttu-id="c2e2e-170">Microsoft. PowerShell에는 개체 및 데이터를 조작 하는 데 사용 되는 cmdlet (예: Get Member, Write Host 및 Format-List)이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-170">Microsoft.PowerShell.Utility - Contains cmdlets used to manipulate objects and data, such as Get-Member, Write-Host, and Format-List.</span></span>

- <span data-ttu-id="c2e2e-171">Enable-wsmancredssp-Connect-WSMan 및와 같은 Windows 원격 관리 서비스를 관리 하는 WSMan 공급자 및 cmdlet을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-171">Microsoft.WSMan.Management - Contains the WSMan provider and cmdlets that manage the Windows Remote Management service, such as Connect-WSMan and Enable-WSManCredSSP.</span></span>

## <a name="logging-snap-in-events"></a><span data-ttu-id="c2e2e-172">스냅인 이벤트 로깅</span><span class="sxs-lookup"><span data-stu-id="c2e2e-172">LOGGING SNAP-IN EVENTS</span></span>

<span data-ttu-id="c2e2e-173">Windows PowerShell 3.0부터 모듈 및 스냅인의 LogPipelineExecutionDetails 속성을 TRUE로 설정 하 여 Windows PowerShell 모듈 및 스냅인에서 cmdlet에 대 한 실행 이벤트를 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-173">Beginning in Windows PowerShell 3.0, you can record execution events for the cmdlets in Windows PowerShell modules and snap-ins by setting the LogPipelineExecutionDetails property of modules and snap-ins to TRUE.</span></span> <span data-ttu-id="c2e2e-174">자세한 내용은 [about_EventLogs](about_EventLogs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-174">For more information, see [about_EventLogs](about_EventLogs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c2e2e-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c2e2e-175">SEE ALSO</span></span>

[<span data-ttu-id="c2e2e-176">Add-pssnapin</span><span class="sxs-lookup"><span data-stu-id="c2e2e-176">Add-PsSnapin</span></span>](xref:Microsoft.PowerShell.Core.Add-PSSnapin)

[<span data-ttu-id="c2e2e-177">Add-pssnapin</span><span class="sxs-lookup"><span data-stu-id="c2e2e-177">Get-PsSnapin</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSnapin)

[<span data-ttu-id="c2e2e-178">Add-pssnapin</span><span class="sxs-lookup"><span data-stu-id="c2e2e-178">Remove-PsSnapin</span></span>](xref:Microsoft.PowerShell.Core.Remove-PSSnapin)

[<span data-ttu-id="c2e2e-179">Export-Console</span><span class="sxs-lookup"><span data-stu-id="c2e2e-179">Export-Console</span></span>](xref:Microsoft.PowerShell.Core.Export-Console)

[<span data-ttu-id="c2e2e-180">Get-Command</span><span class="sxs-lookup"><span data-stu-id="c2e2e-180">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)

[<span data-ttu-id="c2e2e-181">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="c2e2e-181">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="c2e2e-182">about_Modules</span><span class="sxs-lookup"><span data-stu-id="c2e2e-182">about_Modules</span></span>](about_Modules.md)

## <a name="keywords"></a><span data-ttu-id="c2e2e-183">어</span><span class="sxs-lookup"><span data-stu-id="c2e2e-183">KEYWORDS</span></span>

<span data-ttu-id="c2e2e-184">about_Snapins, about_Snap_ins, about_Snap 기능</span><span class="sxs-lookup"><span data-stu-id="c2e2e-184">about_Snapins, about_Snap_ins, about_Snap-ins</span></span>
