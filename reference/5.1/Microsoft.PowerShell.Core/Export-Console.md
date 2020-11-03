---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-console?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Console
ms.openlocfilehash: 7b643b5f9b6868a5da988b19b65dead24f986f67
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212058"
---
# <span data-ttu-id="c31f1-103">Export-Console</span><span class="sxs-lookup"><span data-stu-id="c31f1-103">Export-Console</span></span>

## <span data-ttu-id="c31f1-104">개요</span><span class="sxs-lookup"><span data-stu-id="c31f1-104">SYNOPSIS</span></span>
<span data-ttu-id="c31f1-105">현재 세션의 스냅인 이름을 콘솔 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-105">Exports the names of snap-ins in the current session to a console file.</span></span>

## <span data-ttu-id="c31f1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c31f1-106">SYNTAX</span></span>

```
Export-Console [[-Path] <String>] [-Force] [-NoClobber] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c31f1-107">설명</span><span class="sxs-lookup"><span data-stu-id="c31f1-107">DESCRIPTION</span></span>
<span data-ttu-id="c31f1-108">**Export-Console** cmdlet은 현재 세션의 windows powershell 스냅인 이름을 windows powershell 콘솔 파일 (. .psc1)로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-108">The **Export-Console** cmdlet exports the names of the Windows PowerShell snap-ins in the current session to a Windows PowerShell console file (.psc1).</span></span>
<span data-ttu-id="c31f1-109">이 cmdlet을 사용하여 이후의 세션에서 사용하기 위해 스냅인을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-109">You can use this cmdlet to save the snap-ins for use in future sessions.</span></span>

<span data-ttu-id="c31f1-110">.Psc1 콘솔 파일의 스냅인을 세션에 추가 하려면 Cmd.exe 또는 다른 Windows PowerShell 세션을 사용 하 여 명령줄에서 Windows PowerShell (Powershell.exe)을 시작한 다음 Powershell.exe의 *PSConsoleFile* 매개 변수를 사용 하 여 콘솔 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-110">To add the snap-ins in the .psc1 console file to a session, start Windows PowerShell (Powershell.exe) at the command line by using Cmd.exe or another Windows PowerShell session, and then use the *PSConsoleFile* parameter of Powershell.exe to specify the console file.</span></span>

<span data-ttu-id="c31f1-111">Windows PowerShell 스냅인에 대한 자세한 내용은 about_PSSnapins를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c31f1-111">For more information about Windows PowerShell snap-ins, see about_PSSnapins.</span></span>

## <span data-ttu-id="c31f1-112">예제</span><span class="sxs-lookup"><span data-stu-id="c31f1-112">EXAMPLES</span></span>

### <span data-ttu-id="c31f1-113">예 1: 현재 세션에서 스냅인의 이름 내보내기</span><span class="sxs-lookup"><span data-stu-id="c31f1-113">Example 1: Export the names of snap-ins in the current session</span></span>

```
PS C:\> Export-Console -Path $pshome\Consoles\ConsoleS1.psc1
```

<span data-ttu-id="c31f1-114">이 명령은 현재 세션의 Windows PowerShell 스냅인 이름을 Windows PowerShell 설치 폴더의 ConsoleS1 폴더에 있는 .psc1 파일로 내보냅니다 $pshome 합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-114">This command exports the names of Windows PowerShell snap-ins in the current session to the ConsoleS1.psc1 file in the Consoles folder of the Windows PowerShell installation folder, $pshome.</span></span>

### <span data-ttu-id="c31f1-115">예 2: 스냅인의 이름을 가장 최근의 콘솔 파일로 내보내기</span><span class="sxs-lookup"><span data-stu-id="c31f1-115">Example 2: Export the names of snap-ins to the most recent console file</span></span>

```
PS C:\> Export-Console
```

<span data-ttu-id="c31f1-116">이 명령은 현재 세션의 Windows PowerShell 스냅인 이름을 현재 세션에서 가장 최근에 사용된 Windows PowerShell 콘솔 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-116">This command exports the names of Windows PowerShell snap-ins from current session to the Windows PowerShell console file that was most recently used in the current session.</span></span>
<span data-ttu-id="c31f1-117">또한 이전 파일 내용을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-117">It overwrites the previous file contents.</span></span>

<span data-ttu-id="c31f1-118">현재 세션 중에 콘솔 파일을 내보내지 않은 경우 작업을 계속할 권한과 파일 이름을 확인하는 메시지가 차례로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-118">If you have not exported a console file during the current session, you are prompted for permission to continue and then prompted for a file name.</span></span>

### <span data-ttu-id="c31f1-119">예제 3: 스냅인 추가 및 스냅인 이름 내보내기</span><span class="sxs-lookup"><span data-stu-id="c31f1-119">Example 3: Add a snap-in and export the names of snap-ins</span></span>

```
PS C:\> Add-PSSnapin NewPSSnapin
PS C:\> Export-Console -path NewPSSnapinConsole.psc1
PS C:\> powershell.exe -PsConsoleFile NewPsSnapinConsole.psc1
```

<span data-ttu-id="c31f1-120">이 명령은 NewPSSnapin Windows PowerShell 스냅인을 현재 세션에 추가하고 현재 세션의 Windows PowerShell 스냅인 이름을 콘솔 파일로 내보낸 다음 이 파일을 사용하여 Windows PowerShell 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-120">These commands add the NewPSSnapin Windows PowerShell snap-in to the current session, export the names of Windows PowerShell snap-ins in the current session to a console file, and then start a Windows PowerShell session with the console file.</span></span>

<span data-ttu-id="c31f1-121">첫 번째 명령은 **add-pssnapin** cmdlet을 사용 하 여 NewPSSnapin 스냅인을 현재 세션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-121">The first command uses the **Add-PSSnapin** cmdlet to add the NewPSSnapin snap-in to the current session.</span></span>
<span data-ttu-id="c31f1-122">해당 시스템에 등록된 Windows PowerShell 스냅인만 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-122">You can only add Windows PowerShell snap-ins that are registered on your system.</span></span>

<span data-ttu-id="c31f1-123">두 번째 명령은 Windows PowerShell 스냅인 이름을 NewPSSnapinConsole.psc1 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-123">The second command exports the Windows PowerShell snap-in names to the NewPSSnapinConsole.psc1 file.</span></span>

<span data-ttu-id="c31f1-124">세 번째 명령은 NewPSSnapinConsole.psc1 파일을 사용하여 Windows PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-124">The third command starts Windows PowerShell with the NewPSSnapinConsole.psc1 file.</span></span>
<span data-ttu-id="c31f1-125">콘솔 파일에 Windows PowerShell 스냅인 이름이 포함되기 때문에 현재 세션에서 스냅인의 공급자 및 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-125">Because the console file includes the Windows PowerShell snap-in name, the cmdlets and providers in the snap-in are available in the current session.</span></span>

### <span data-ttu-id="c31f1-126">예제 4: 지정 된 위치로 스냅인 이름 내보내기</span><span class="sxs-lookup"><span data-stu-id="c31f1-126">Example 4: Export names of snap-ins to a specified location</span></span>

```
PS C:\> export-console -path Console01
PS C:\> notepad console01.psc1
<?xml version="1.0" encoding="utf-8"?>
<PSConsoleFile ConsoleSchemaVersion="1.0">
  <PSVersion>2.0</PSVersion>
  <PSSnapIns>
     <PSSnapIn Name="NewPSSnapin" />
  </PSSnapIns>
</PSConsoleFile>
```

<span data-ttu-id="c31f1-127">이 명령은 현재 세션의 Windows PowerShell 스냅인 이름을 현재 디렉터리의 Console01.psc1 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-127">This command exports the names of the Windows PowerShell snap-ins in the current session to the Console01.psc1 file in the current directory.</span></span>

<span data-ttu-id="c31f1-128">두 번째 명령은 Console01.psc1 파일의 내용을 메모장에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-128">The second command displays the contents of the Console01.psc1 file in Notepad.</span></span>

### <span data-ttu-id="c31f1-129">예 5: 업데이트할 콘솔 파일 결정</span><span class="sxs-lookup"><span data-stu-id="c31f1-129">Example 5: Determine the console file to update</span></span>

```
PS C:\> powershell.exe -PSConsoleFile Console01.psc1
PS C:\> Add-PSSnapin MySnapin
PS C:\> Export-Console NewConsole.psc1
PS C:\> $ConsoleFileName
PS C:\> Add-PSSnapin SnapIn03
PS C:\> Export-Console
```

<span data-ttu-id="c31f1-130">이 예제에서는 $ConsoleFileName 자동 변수를 사용 하 여 *Path* 매개 변수 값 없이 **Export-console** 을 사용 하는 경우 업데이트 되는 콘솔 파일을 확인 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-130">This example shows how to use the $ConsoleFileName automatic variable to determine the console file that will be updated if you use **Export-Console** without a *Path* parameter value.</span></span>

<span data-ttu-id="c31f1-131">첫 번째 명령은 PowerShell.exe의 *PSConsoleFile* 매개 변수를 사용 하 여 console01.psc1 .psc1 파일을 사용 하 여 Windows PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-131">The first command uses the *PSConsoleFile* parameter of PowerShell.exe to open Windows PowerShell with the Console01.psc1 file.</span></span>

<span data-ttu-id="c31f1-132">두 번째 명령은 **add-pssnapin** cmdlet을 사용 하 여 MySnapin Windows PowerShell 스냅인을 현재 세션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-132">The second command uses the **Add-PSSnapin** cmdlet to add the MySnapin Windows PowerShell snap-in to the current session.</span></span>

<span data-ttu-id="c31f1-133">세 번째 명령은 **export-Console** cmdlet을 사용 하 여 세션에 있는 모든 Windows PowerShell 스냅인의 이름을 newconsole 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-133">The third command uses the **Export-Console** cmdlet to export the names of all the Windows PowerShell snap-ins in the session to the NewConsole.psc1 file.</span></span>

<span data-ttu-id="c31f1-134">네 번째 명령은 $ConsoleFileName 변수를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-134">The fourth command displays the $ConsoleFileName variable.</span></span>
<span data-ttu-id="c31f1-135">가장 최근에 사용 된 콘솔 파일을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-135">It contains the most recently used console file.</span></span>
<span data-ttu-id="c31f1-136">샘플 출력에는 NewConsole.ps1이 가장 최근에 사용된 파일로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-136">The sample output shows that NewConsole.ps1 is the most recently used file.</span></span>

<span data-ttu-id="c31f1-137">다섯 번째 명령은 SnapIn03을 현재 콘솔에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-137">The fifth command adds SnapIn03 to the current console.</span></span>

<span data-ttu-id="c31f1-138">여섯 번째 명령은 *Path* 매개 변수 없이 **Export-Console** cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-138">The sixth command uses the **Export-Console** cmdlet without a *Path* parameter.</span></span>
<span data-ttu-id="c31f1-139">이 명령은 현재 세션의 모든 Windows PowerShell 스냅인 이름을 가장 최근에 사용된 파일인 NewConsole.psc1로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-139">This command exports the names of all the Windows PowerShell snap-ins in the current session to the most recently used file, NewConsole.psc1.</span></span>

## <span data-ttu-id="c31f1-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c31f1-140">PARAMETERS</span></span>

### <span data-ttu-id="c31f1-141">-Force</span><span class="sxs-lookup"><span data-stu-id="c31f1-141">-Force</span></span>
<span data-ttu-id="c31f1-142">파일에 읽기 전용 특성이 있는 경우에도이 cmdlet이 경고 없이 콘솔 파일의 데이터를 덮어쓰도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-142">Indicates that this cmdlet overwrites the data in a console file without warning, even if the file has the read-only attribute.</span></span>
<span data-ttu-id="c31f1-143">명령이 완료 되 면 읽기 전용 특성이 변경 되 고 다시 설정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-143">The read-only attribute is changed and is not reset when the command finishes.</span></span>

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

### <span data-ttu-id="c31f1-144">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="c31f1-144">-NoClobber</span></span>
<span data-ttu-id="c31f1-145">이 cmdlet이 기존 콘솔 파일을 덮어쓰지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-145">Indicates that this cmdlet does not overwrite  an existing console file.</span></span>
<span data-ttu-id="c31f1-146">기본적으로 지정 된 경로에서 파일이 발생 하면 **내보내기 콘솔** 은 경고 없이 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-146">By default, if a file occurs in the specified path, **Export-Console** overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c31f1-147">-Path</span><span class="sxs-lookup"><span data-stu-id="c31f1-147">-Path</span></span>
<span data-ttu-id="c31f1-148">콘솔 파일(\*.psc1)의 경로 및 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-148">Specifies a path and file name for the console file (\*.psc1).</span></span>
<span data-ttu-id="c31f1-149">선택적 경로 및 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-149">Enter an optional path and name.</span></span>
<span data-ttu-id="c31f1-150">와일드카드 문자는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-150">Wildcard characters are not permitted.</span></span>

<span data-ttu-id="c31f1-151">파일 이름만 지정 하는 경우에는 **Export-Console** 에서 해당 이름과 .psc1 파일 이름 확장명을 가진 파일을 현재 디렉터리에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-151">If you specify only a file name, **Export-Console** creates a file that has that name and the .psc1 file name extension in the current directory.</span></span>

<span data-ttu-id="c31f1-152">이 매개 변수는 *PSConsoleFile* 매개 변수를 사용 하 여 Windows PowerShell을 열었거나 현재 세션 중에 콘솔 파일을 내보내지 않은 경우에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-152">This parameter is required unless you have opened Windows PowerShell with the *PSConsoleFile* parameter or exported a console file during the current session.</span></span>
<span data-ttu-id="c31f1-153">*NoClobber* 매개 변수를 사용 하 여 현재 콘솔 파일을 덮어쓰지 않도록 하는 경우에도이 매개 변수를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-153">It is also required when you use the *NoClobber* parameter to prevent the current console file from being overwritten.</span></span>

<span data-ttu-id="c31f1-154">이 매개 변수를 생략 하면 **내보내기 콘솔이** 이 세션에서 가장 최근에 사용 된 콘솔 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-154">If you omit this parameter, **Export-Console** overwrites the console file that was used most recently in this session.</span></span>
<span data-ttu-id="c31f1-155">가장 최근에 사용 된 콘솔 파일의 경로는 $ConsoleFileName 자동 변수 값에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-155">The path of the most recently used console file is stored in the value of the $ConsoleFileName automatic variable.</span></span>
<span data-ttu-id="c31f1-156">자세한 내용은 about_Automatic_Variables를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c31f1-156">For more information, see about_Automatic_Variables.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c31f1-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c31f1-157">-Confirm</span></span>
<span data-ttu-id="c31f1-158">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-158">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c31f1-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c31f1-159">-WhatIf</span></span>
<span data-ttu-id="c31f1-160">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c31f1-161">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-161">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c31f1-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c31f1-162">CommonParameters</span></span>
<span data-ttu-id="c31f1-163">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c31f1-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c31f1-164">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c31f1-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c31f1-165">입력</span><span class="sxs-lookup"><span data-stu-id="c31f1-165">INPUTS</span></span>

### <span data-ttu-id="c31f1-166">System.String</span><span class="sxs-lookup"><span data-stu-id="c31f1-166">System.String</span></span>
<span data-ttu-id="c31f1-167">이 cmdlet에 경로 문자열을 파이프 하 여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-167">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="c31f1-168">출력</span><span class="sxs-lookup"><span data-stu-id="c31f1-168">OUTPUTS</span></span>

### <span data-ttu-id="c31f1-169">System.object</span><span class="sxs-lookup"><span data-stu-id="c31f1-169">System.IO.FileInfo</span></span>
<span data-ttu-id="c31f1-170">이 cmdlet은 내보낸 별칭을 포함 하는 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-170">This cmdlet creates a file that contains the exported aliases.</span></span>

## <span data-ttu-id="c31f1-171">참고</span><span class="sxs-lookup"><span data-stu-id="c31f1-171">NOTES</span></span>

* <span data-ttu-id="c31f1-172">콘솔 파일(.psc1)을 사용하여 세션을 시작하는 경우 콘솔 파일의 이름이 $ConsoleFileName 자동 변수에 자동으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-172">When a console file (.psc1) is used to start the session, the name of the console file is automatically stored in the $ConsoleFileName automatic variable.</span></span> <span data-ttu-id="c31f1-173">**내보내기-콘솔** 의 *Path* 매개 변수를 사용 하 여 새 콘솔 파일을 지정할 때 $ConsoleFileName의 값이 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-173">The value of $ConsoleFileName is updated when you use the *Path* parameter of **Export-Console** to specify a new console file.</span></span> <span data-ttu-id="c31f1-174">콘솔 파일을 사용 하지 않으면 $ConsoleFileName에 값 ($Null)이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-174">When no console file is used, $ConsoleFileName has no value ($Null).</span></span>

  <span data-ttu-id="c31f1-175">Windows PowerShell 콘솔 파일을 새 세션에서 사용하려면 다음 구문을 사용하여 Windows PowerShell을 시작하세요.</span><span class="sxs-lookup"><span data-stu-id="c31f1-175">To use a Windows PowerShell console file in a new session, use the following syntax to start Windows PowerShell:</span></span>

  `powershell.exe -PsConsoleFile \<ConsoleFile\>.psc1`

  <span data-ttu-id="c31f1-176">Add-PSSnapin 명령을 Windows PowerShell 프로필에 추가하여 이후 세션을 위해 Windows PowerShell 스냅인을 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c31f1-176">You can also save Windows PowerShell snap-ins for future sessions by adding an Add-PSSnapin command to your Windows PowerShell profile.</span></span>
<span data-ttu-id="c31f1-177">자세한 내용은 about_Profiles를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c31f1-177">For more information, see about_Profiles.</span></span>


## <span data-ttu-id="c31f1-178">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c31f1-178">RELATED LINKS</span></span>

[<span data-ttu-id="c31f1-179">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="c31f1-179">Add-PSSnapin</span></span>](Add-PSSnapin.md)

[<span data-ttu-id="c31f1-180">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="c31f1-180">Get-PSSnapin</span></span>](Get-PSSnapin.md)

[<span data-ttu-id="c31f1-181">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="c31f1-181">Remove-PSSnapin</span></span>](Remove-PSSnapin.md)
