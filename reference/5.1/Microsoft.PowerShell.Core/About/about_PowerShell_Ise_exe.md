---
description: PowerShell_Ise.exe 명령줄 도구를 사용 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_ise_exe?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Ise_exe
ms.openlocfilehash: c7500eb6d8586b9dca568edc4e805c577e94bec4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223338"
---
# <a name="about-powershell-iseexe"></a><span data-ttu-id="c3bde-104">PowerShell Ise.exe 정보</span><span class="sxs-lookup"><span data-stu-id="c3bde-104">About PowerShell Ise.exe</span></span>

## <a name="short-description"></a><span data-ttu-id="c3bde-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="c3bde-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="c3bde-106">PowerShell_Ise.exe 명령줄 도구를 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-106">Explains how to use the PowerShell_Ise.exe command-line tool.</span></span>

## <a name="long-description"></a><span data-ttu-id="c3bde-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="c3bde-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="c3bde-108">PowerShell_Ise.exe는 Windows PowerShell ISE (통합 스크립팅 환경) 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-108">PowerShell_Ise.exe starts a Windows PowerShell Integrated Scripting Environment (ISE) session.</span></span> <span data-ttu-id="c3bde-109">Cmd.exe 및 Windows PowerShell에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-109">You can run it in Cmd.exe and in Windows PowerShell.</span></span>

<span data-ttu-id="c3bde-110">PowerShell_ISE.exe를 실행 하려면 PowerShell_ISE.exe, PowerShell_ISE 또는 ISE를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-110">To run PowerShell_ISE.exe, type PowerShell_ISE.exe, PowerShell_ISE, or ISE.</span></span>

## <a name="syntax"></a><span data-ttu-id="c3bde-111">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c3bde-111">SYNTAX</span></span>

```
PowerShell_Ise[.exe]
PowerShell_ISE[.exe]
ISE[.exe]
[-File]<FilePath[]> [-NoProfile] [-MTA]
-Help | ? | -? | /? Displays the syntax and describes the command-line switches.
```

## <a name="parameters"></a><span data-ttu-id="c3bde-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c3bde-112">PARAMETERS</span></span>

### <a name="-file"></a><span data-ttu-id="c3bde-113">-File</span><span class="sxs-lookup"><span data-stu-id="c3bde-113">-File</span></span>

<span data-ttu-id="c3bde-114">Windows PowerShell ISE에서 지정 된 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-114">Opens the specified files in Windows PowerShell ISE.</span></span> <span data-ttu-id="c3bde-115">매개 변수 이름 ("-File")은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-115">The parameter name ("-File") is optional.</span></span> <span data-ttu-id="c3bde-116">둘 이상의 파일을 나열 하려면 따옴표로 묶은 텍스트 문자열을 하나 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-116">To list more than one file, enter one text string enclosed in quotation marks.</span></span> <span data-ttu-id="c3bde-117">문자열 내에서 파일 이름을 구분 하려면 쉼표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-117">Use commas to separate the file names within the string.</span></span>

<span data-ttu-id="c3bde-118">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="c3bde-118">For example:</span></span>

<span data-ttu-id="c3bde-119">PowerShell_ISE-파일 "File1.ps1, File2.ps1, File3.xml".</span><span class="sxs-lookup"><span data-stu-id="c3bde-119">PowerShell_ISE -File "File1.ps1,File2.ps1,File3.xml".</span></span>

<span data-ttu-id="c3bde-120">Windows PowerShell에서는 파일 이름 사이에 공백을 사용할 수 있지만 Cmd.exe와 같은 다른 프로그램에서는 올바르게 해석 되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-120">Spaces between the file names are permitted in Windows PowerShell, but might not be interpreted correctly by other programs, such as Cmd.exe.</span></span>

<span data-ttu-id="c3bde-121">이 매개 변수를 사용 하 여 Windows PowerShell 스크립트 파일 및 XML 파일을 비롯 한 모든 텍스트 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-121">You can use this parameter to open any text file, including Windows PowerShell script files and XML files.</span></span>

### <a name="-mta"></a><span data-ttu-id="c3bde-122">-Mta</span><span class="sxs-lookup"><span data-stu-id="c3bde-122">-Mta</span></span>

<span data-ttu-id="c3bde-123">다중 스레드 아파트를 사용 하 여 Windows PowerShell ISE를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-123">Starts Windows PowerShell ISE using a multi-threaded apartment.</span></span> <span data-ttu-id="c3bde-124">이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-124">This parameter is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="c3bde-125">STA (단일 스레드 아파트)가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-125">Single-threaded apartment (STA) is the default.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="c3bde-126">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="c3bde-126">-NoProfile</span></span>

<span data-ttu-id="c3bde-127">Windows PowerShell 프로필을 실행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-127">Does not run Windows PowerShell profiles.</span></span> <span data-ttu-id="c3bde-128">기본적으로 Windows PowerShell 프로필은 모든 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-128">By default, Windows PowerShell profiles are run in every session.</span></span>

<span data-ttu-id="c3bde-129">다른 프로필을 사용 하는 시스템에서 실행 되는 함수 및 스크립트와 같은 공유 콘텐츠를 작성 하는 경우이 매개 변수를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-129">This parameter is recommended when you are writing shared content, such as functions and scripts that will be run on systems with different profiles.</span></span>
<span data-ttu-id="c3bde-130">자세한 내용은 [about_Profiles](about_Profiles.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3bde-130">For more information, see [about_Profiles](about_Profiles.md).</span></span>

### <a name="-help---"></a><span data-ttu-id="c3bde-131">-Help-?,/?</span><span class="sxs-lookup"><span data-stu-id="c3bde-131">-Help -?, /?</span></span>

<span data-ttu-id="c3bde-132">PowerShell_ISE.exe에 대 한 도움말을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-132">Displays help for PowerShell_ISE.exe.</span></span>

## <a name="examples"></a><span data-ttu-id="c3bde-133">예제</span><span class="sxs-lookup"><span data-stu-id="c3bde-133">EXAMPLES</span></span>

<span data-ttu-id="c3bde-134">이러한 명령은 Windows PowerShell ISE 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-134">These commands start Windows PowerShell ISE.</span></span> <span data-ttu-id="c3bde-135">이러한 명령은 동일하므로 서로 바꿔 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-135">The commands are equivalent and can be used interchangeably.</span></span>

```
PS C:> PowerShell_ISE.exe
PS C:> PowerShell_ISE
PS C:> ISE
```

<span data-ttu-id="c3bde-136">이러한 명령은 Windows PowerShell ISE에서 Get-Profile.ps1 스크립트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-136">These commands open the Get-Profile.ps1 script in Windows PowerShell ISE.</span></span>
<span data-ttu-id="c3bde-137">이러한 명령은 동일하므로 서로 바꿔 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-137">The commands are equivalent and can be used interchangeably.</span></span>

```
PS C:> PowerShell_ISE.exe -File .\Get-Profile.ps1
PS C:> ISE -File .\Get-Profile.ps1
PS C:> ISE .\Get-Profile.ps1
```

<span data-ttu-id="c3bde-138">이 명령은 Windows PowerShell ISE에서 Get-Backups.ps1 및 Get-BackupInstance.ps1 스크립트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-138">This command opens the Get-Backups.ps1 and Get-BackupInstance.ps1 scripts in Windows PowerShell ISE.</span></span> <span data-ttu-id="c3bde-139">둘 이상의 파일을 열려면 쉼표를 사용 하 여 파일 이름을 구분 하 고 전체 파일 이름 값을 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-139">To open more than one file, use a comma to separate the file names and enclose the entire file name value in quotation marks.</span></span>

```
PS C:> ISE -File ".\Get-Backups.ps1,Get-BackupInstance.ps1"
```

<span data-ttu-id="c3bde-140">이 명령은 프로필 없이 Windows PowerShell ISE를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-140">This command starts Windows PowerShell ISE with no profiles.</span></span>

```
PS C:> ISE -NoProfile
```

<span data-ttu-id="c3bde-141">이 명령은 PowerShell_ISE.exe에 대 한 도움말을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c3bde-141">This command gets help for PowerShell_ISE.exe.</span></span>

```
PS C:> ISE -help
```

## <a name="see-also"></a><span data-ttu-id="c3bde-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3bde-142">SEE ALSO</span></span>

[<span data-ttu-id="c3bde-143">about_PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="c3bde-143">about_PowerShell.exe</span></span>](about_PowerShell_exe.md)

[<span data-ttu-id="c3bde-144">about_Windows_PowerShell_ISE</span><span class="sxs-lookup"><span data-stu-id="c3bde-144">about_Windows_PowerShell_ISE</span></span>](about_Windows_PowerShell_ISE.md)

[<span data-ttu-id="c3bde-145">Windows PowerShell ISE (통합 스크립팅 환경)</span><span class="sxs-lookup"><span data-stu-id="c3bde-145">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>](/powershell/scripting/windows-powershell/ise/introducing-the-windows-powershell-ise)
