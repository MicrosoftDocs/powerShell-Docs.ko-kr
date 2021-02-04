---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/start-transcript?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transcript
ms.openlocfilehash: 32d8893190489be0a102b2db4dee3482133a4243
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98860844"
---
# <span data-ttu-id="0b191-103">Start-Transcript</span><span class="sxs-lookup"><span data-stu-id="0b191-103">Start-Transcript</span></span>

## <span data-ttu-id="0b191-104">개요</span><span class="sxs-lookup"><span data-stu-id="0b191-104">Synopsis</span></span>
<span data-ttu-id="0b191-105">텍스트 파일에 대 한 PowerShell 세션의 전체 또는 일부에 대 한 레코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-105">Creates a record of all or part of a PowerShell session to a text file.</span></span>

## <span data-ttu-id="0b191-106">구문</span><span class="sxs-lookup"><span data-stu-id="0b191-106">Syntax</span></span>

### <span data-ttu-id="0b191-107">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="0b191-107">ByPath (Default)</span></span>

```
Start-Transcript [[-Path] <String>] [-Append] [-Force] [-NoClobber] [-IncludeInvocationHeader]
 [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="0b191-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="0b191-108">ByLiteralPath</span></span>

```
Start-Transcript [[-LiteralPath] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="0b191-109">ByOutputDirectory</span><span class="sxs-lookup"><span data-stu-id="0b191-109">ByOutputDirectory</span></span>

```
Start-Transcript [[-OutputDirectory] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="0b191-110">설명</span><span class="sxs-lookup"><span data-stu-id="0b191-110">Description</span></span>

<span data-ttu-id="0b191-111">`Start-Transcript`Cmdlet은 텍스트 파일에 대 한 PowerShell 세션의 전체 또는 일부에 대 한 레코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-111">The `Start-Transcript` cmdlet creates a record of all or part of a PowerShell session to a text file.</span></span> <span data-ttu-id="0b191-112">기록에는 사용자가 입력하는 모든 명령과 콘솔에 나타나는 모든 출력이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-112">The transcript includes all command that the user types and all output that appears on the console.</span></span>

<span data-ttu-id="0b191-113">Windows PowerShell 5.0부터 `Start-Transcript` 은 모든 기록의 생성 된 파일 이름에 호스트 이름을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-113">Starting in Windows PowerShell 5.0, `Start-Transcript` includes the hostname in the generated file name of all transcripts.</span></span> <span data-ttu-id="0b191-114">엔터프라이즈 로깅이 중앙 집중화 된 경우 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-114">This is especially useful when your enterprise's logging is centralized.</span></span>
<span data-ttu-id="0b191-115">Cmdlet을 통해 생성 되는 파일에는 `Start-Transcript` 두 개 이상의 기록이 동시에 시작 될 때 잠재적으로 덮어쓰거나 중복 되지 않도록 이름에 임의의 문자가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-115">Files that are created by the `Start-Transcript` cmdlet include random characters in names to prevent potential overwrites or duplication when two or more transcripts are started simultaneously.</span></span>
<span data-ttu-id="0b191-116">또한 중앙 집중식 파일 공유에 저장 된 기록을 무단으로 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-116">This also prevents unauthorized discovery of transcripts that are stored in a centralized file share.</span></span>

<span data-ttu-id="0b191-117">**추가** 매개 변수를 사용 하는 경우 대상 파일에 BOM (바이트 순서 표시)의 `Start-Transcript` 기본값은 `ASCII` 대상 파일에서 인코딩할 수 없는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-117">When using the **Append** parameter, if the target file doesn't have a Byte Order Mark (BOM) `Start-Transcript` defaults to `ASCII` encoding in the target file.</span></span> <span data-ttu-id="0b191-118">이 동작으로 인해 성적 증명서의 mulitbyte 문자가 잘못 인코딩 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-118">This behavior can result in improper encoding of mulitbyte characters in the transcript.</span></span>

## <span data-ttu-id="0b191-119">예제</span><span class="sxs-lookup"><span data-stu-id="0b191-119">Examples</span></span>

### <span data-ttu-id="0b191-120">예제 1: 기본 설정을 사용 하 여 기록 파일 시작</span><span class="sxs-lookup"><span data-stu-id="0b191-120">Example 1: Start a transcript file with default settings</span></span>

```powershell
Start-Transcript
```

<span data-ttu-id="0b191-121">이 명령은 기본 파일 위치에서 기록을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-121">This command starts a transcript in the default file location.</span></span>

### <span data-ttu-id="0b191-122">예제 2: 특정 위치에서 기록 파일 시작</span><span class="sxs-lookup"><span data-stu-id="0b191-122">Example 2: Start a transcript file at a specific location</span></span>

```powershell
Start-Transcript -Path "C:\transcripts\transcript0.txt" -NoClobber
```

<span data-ttu-id="0b191-123">이 명령은의 파일에서 기록을 시작 `Transcript0.txt` `C:\transcripts` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-123">This command starts a transcript in the `Transcript0.txt` file in `C:\transcripts`.</span></span> <span data-ttu-id="0b191-124">**NoClobber** 매개 변수를 사용 하기 때문에 명령은 기존 파일을 덮어쓰지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-124">Since the **NoClobber** parameter is used, the command prevents any existing files from being overwritten.</span></span> <span data-ttu-id="0b191-125">`Transcript0.txt`파일이 이미 있으면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-125">If the `Transcript0.txt` file already exists, the command fails.</span></span>

## <span data-ttu-id="0b191-126">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0b191-126">Parameters</span></span>

### <span data-ttu-id="0b191-127">-추가</span><span class="sxs-lookup"><span data-stu-id="0b191-127">-Append</span></span>

<span data-ttu-id="0b191-128">이 cmdlet이 기존 파일의 끝에 새 기록을 추가 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-128">Indicates that this cmdlet adds the new transcript to the end of an existing file.</span></span> <span data-ttu-id="0b191-129">**Path** 매개 변수를 사용 하 여 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-129">Use the **Path** parameter to specify the file.</span></span>

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

### <span data-ttu-id="0b191-130">-Force</span><span class="sxs-lookup"><span data-stu-id="0b191-130">-Force</span></span>

<span data-ttu-id="0b191-131">cmdlet에서 기록을 기존 읽기 전용 파일에 추가할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-131">Allows the cmdlet to append the transcript to an existing read-only file.</span></span> <span data-ttu-id="0b191-132">읽기 전용 파일에서 사용될 경우 이 cmdlet은 파일 권한을 읽기 및 쓰기로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-132">When used on a read-only file, the cmdlet changes the file permission to read-write.</span></span> <span data-ttu-id="0b191-133">이 매개 변수를 사용 하는 경우 cmdlet은 보안 제한을 재정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-133">The cmdlet cannot override security restrictions when this parameter is used.</span></span>

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

### <span data-ttu-id="0b191-134">-IncludeInvocationHeader</span><span class="sxs-lookup"><span data-stu-id="0b191-134">-IncludeInvocationHeader</span></span>

<span data-ttu-id="0b191-135">명령이 실행 될 때이 cmdlet이 타임 스탬프를 기록 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-135">Indicates that this cmdlet logs the time stamp when commands are run.</span></span>

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

### <span data-ttu-id="0b191-136">-UseMinimalHeader</span><span class="sxs-lookup"><span data-stu-id="0b191-136">-UseMinimalHeader</span></span>

<span data-ttu-id="0b191-137">기본적으로 포함 된 자세한 헤더 대신 간략 한 머리글 앞에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-137">Prepend a short header to the transcript, instead of the detailed header included by default.</span></span> <span data-ttu-id="0b191-138">이 매개 변수는 PowerShell 6.2에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-138">This parameter was added in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="0b191-139">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0b191-139">-LiteralPath</span></span>

<span data-ttu-id="0b191-140">성적 증명서 파일의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-140">Specifies a location to the transcript file.</span></span> <span data-ttu-id="0b191-141">**Path** 매개 변수와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-141">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="0b191-142">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-142">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="0b191-143">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="0b191-143">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="0b191-144">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-144">Single quotation marks inform PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0b191-145">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="0b191-145">-NoClobber</span></span>

<span data-ttu-id="0b191-146">이 cmdlet이 기존 파일을 덮어쓰지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-146">Indicates that this cmdlet will not overwrite of an existing file.</span></span> <span data-ttu-id="0b191-147">기본적으로 기록 파일이 지정 된 경로에 있으면 `Start-Transcript` 는 경고 없이 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-147">By default, if a transcript file exists in the specified path, `Start-Transcript` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="0b191-148">-OutputDirectory</span><span class="sxs-lookup"><span data-stu-id="0b191-148">-OutputDirectory</span></span>

<span data-ttu-id="0b191-149">기록을 저장할 특정 경로 및 폴더를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-149">Specifies a specific path and folder in which to save a transcript.</span></span> <span data-ttu-id="0b191-150">PowerShell에서 자동으로 성적 증명서 이름을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-150">PowerShell automatically assigns the transcript name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByOutputDirectory
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0b191-151">-Path</span><span class="sxs-lookup"><span data-stu-id="0b191-151">-Path</span></span>

<span data-ttu-id="0b191-152">성적 증명서 파일의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-152">Specifies a location to the transcript file.</span></span> <span data-ttu-id="0b191-153">파일 경로를 입력 하십시오 `.txt` .</span><span class="sxs-lookup"><span data-stu-id="0b191-153">Enter a path to a `.txt` file.</span></span> <span data-ttu-id="0b191-154">와일드카드는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-154">Wildcards are not permitted.</span></span>

<span data-ttu-id="0b191-155">경로를 지정 하지 않으면는 `Start-Transcript` 전역 변수 값의 경로를 사용 합니다 `$Transcript` .</span><span class="sxs-lookup"><span data-stu-id="0b191-155">If you do not specify a path, `Start-Transcript` uses the path in the value of the `$Transcript` global variable.</span></span> <span data-ttu-id="0b191-156">이 변수를 만들지 않은 경우는 `Start-Transcript` 파일에 기록을 저장 합니다 `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` .</span><span class="sxs-lookup"><span data-stu-id="0b191-156">If you have not created this variable, `Start-Transcript` stores the transcripts in the `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` files.</span></span>

<span data-ttu-id="0b191-157">경로에 디렉터리가 없으면 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-157">If any of the directories in the path do not exist, the command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0b191-158">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0b191-158">-Confirm</span></span>

<span data-ttu-id="0b191-159">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-159">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0b191-160">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0b191-160">-WhatIf</span></span>

<span data-ttu-id="0b191-161">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-161">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="0b191-162">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-162">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0b191-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0b191-163">CommonParameters</span></span>

<span data-ttu-id="0b191-164">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0b191-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0b191-165">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b191-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0b191-166">입력</span><span class="sxs-lookup"><span data-stu-id="0b191-166">Inputs</span></span>

### <span data-ttu-id="0b191-167">None</span><span class="sxs-lookup"><span data-stu-id="0b191-167">None</span></span>

<span data-ttu-id="0b191-168">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-168">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="0b191-169">출력</span><span class="sxs-lookup"><span data-stu-id="0b191-169">Outputs</span></span>

### <span data-ttu-id="0b191-170">System.String</span><span class="sxs-lookup"><span data-stu-id="0b191-170">System.String</span></span>

<span data-ttu-id="0b191-171">이 cmdlet은 확인 메시지와 출력 파일의 경로를 포함 하는 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-171">This cmdlet returns a string that contains a confirmation message and the path to the output file.</span></span>

## <span data-ttu-id="0b191-172">참고</span><span class="sxs-lookup"><span data-stu-id="0b191-172">Notes</span></span>

<span data-ttu-id="0b191-173">기록을 중지 하려면 cmdlet을 사용 `Stop-Transcript` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-173">To stop a transcript, use the `Stop-Transcript` cmdlet.</span></span>

<span data-ttu-id="0b191-174">전체 세션을 기록 하려면 `Start-Transcript` 프로필에 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b191-174">To record an entire session, add the `Start-Transcript` command to your profile.</span></span> <span data-ttu-id="0b191-175">자세한 내용은 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b191-175">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

## <span data-ttu-id="0b191-176">관련 링크</span><span class="sxs-lookup"><span data-stu-id="0b191-176">Related Links</span></span>

[<span data-ttu-id="0b191-177">Stop-Transcript</span><span class="sxs-lookup"><span data-stu-id="0b191-177">Stop-Transcript</span></span>](Stop-Transcript.md)
