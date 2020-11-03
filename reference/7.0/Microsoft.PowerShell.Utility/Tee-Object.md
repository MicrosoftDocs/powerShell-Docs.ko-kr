---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/tee-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Tee-Object
ms.openlocfilehash: 47c1eb6b31f762e3950c07f9edec81a081ce616e
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211425"
---
# <span data-ttu-id="6c9ef-103">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="6c9ef-103">Tee-Object</span></span>

## <span data-ttu-id="6c9ef-104">개요</span><span class="sxs-lookup"><span data-stu-id="6c9ef-104">SYNOPSIS</span></span>
<span data-ttu-id="6c9ef-105">명령 출력을 파일 또는 변수에 저장하고 파이프라인으로도 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-105">Saves command output in a file or variable and also sends it down the pipeline.</span></span>

## <span data-ttu-id="6c9ef-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6c9ef-106">SYNTAX</span></span>

### <span data-ttu-id="6c9ef-107">File (기본값)</span><span class="sxs-lookup"><span data-stu-id="6c9ef-107">File (Default)</span></span>

```
Tee-Object [-InputObject <PSObject>] [-FilePath] <String> [-Append] [<CommonParameters>]
```

### <span data-ttu-id="6c9ef-108">LiteralFile</span><span class="sxs-lookup"><span data-stu-id="6c9ef-108">LiteralFile</span></span>

```
Tee-Object [-InputObject <PSObject>] -LiteralPath <String> [<CommonParameters>]
```

### <span data-ttu-id="6c9ef-109">변수</span><span class="sxs-lookup"><span data-stu-id="6c9ef-109">Variable</span></span>

```
Tee-Object [-InputObject <PSObject>] -Variable <String> [<CommonParameters>]
```

## <span data-ttu-id="6c9ef-110">설명</span><span class="sxs-lookup"><span data-stu-id="6c9ef-110">DESCRIPTION</span></span>

<span data-ttu-id="6c9ef-111">`Tee-Object`Cmdlet은 출력을 리디렉션합니다. 즉, 명령의 출력을 두 방향으로 전송 합니다 (예: 문자 T).</span><span class="sxs-lookup"><span data-stu-id="6c9ef-111">The `Tee-Object` cmdlet redirects output, that is, it sends the output of a command in two directions (like the letter T).</span></span> <span data-ttu-id="6c9ef-112">이 명령은 출력을 파일 또는 변수에 저장하고 파이프라인으로도 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-112">It stores the output in a file or variable and also sends it down the pipeline.</span></span> <span data-ttu-id="6c9ef-113">`Tee-Object`이 파이프라인에서 마지막 명령이 면 명령 출력이 프롬프트에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-113">If `Tee-Object` is the last command in the pipeline, the command output is displayed at the prompt.</span></span>

## <span data-ttu-id="6c9ef-114">예제</span><span class="sxs-lookup"><span data-stu-id="6c9ef-114">EXAMPLES</span></span>

### <span data-ttu-id="6c9ef-115">예제 1: 파일 및 콘솔에 프로세스 출력</span><span class="sxs-lookup"><span data-stu-id="6c9ef-115">Example 1: Output processes to a file and to the console</span></span>

<span data-ttu-id="6c9ef-116">이 예제에서는 컴퓨터에서 실행 중인 프로세스 목록을 가져와 그 결과를 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-116">This example gets a list of the processes running on the computer and sends the result to a file.</span></span>
<span data-ttu-id="6c9ef-117">두 번째 경로를 지정하지 않았으므로 해당 프로세스가 콘솔에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-117">Because a second path is not specified, the processes are also displayed in the console.</span></span>

```powershell
Get-Process | Tee-Object -FilePath "C:\Test1\testfile2.txt"
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
83       4     2300       4520    39     0.30    4032 00THotkey
272      6     1400       3944    34     0.06    3088 alg
81       3      804       3284    21     2.45     148 ApntEx
81       4     2008       5808    38     0.75    3684 Apoint
...
```

### <span data-ttu-id="6c9ef-118">예제 2: 변수를 변수로 출력 `Select-Object`</span><span class="sxs-lookup"><span data-stu-id="6c9ef-118">Example 2: Output processes to a variable and `Select-Object`</span></span>

<span data-ttu-id="6c9ef-119">이 예제에서는 컴퓨터에서 실행 중인 프로세스 목록을 가져와 `$proc` 변수에 저장 한 다음로 파이프 `Select-Object` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-119">This example gets a list of the processes running on the computer, saves them to the `$proc` variable, and pipes them to `Select-Object`.</span></span>

```powershell
Get-Process notepad | Tee-Object -Variable proc | Select-Object processname,handles
```

```Output
ProcessName                              Handles
-----------                              -------
notepad                                  43
notepad                                  37
notepad                                  38
notepad                                  38
```

<span data-ttu-id="6c9ef-120">`Select-Object`Cmdlet은 **ProcessName** 및 **Handles** 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-120">The `Select-Object` cmdlet selects the **ProcessName** and **Handles** properties.</span></span> <span data-ttu-id="6c9ef-121">변수에는에 `$proc` 의해 반환 되는 기본 정보가 포함 됩니다 `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="6c9ef-121">Note that the `$proc` variable includes the default information returned by `Get-Process`.</span></span>

### <span data-ttu-id="6c9ef-122">예 3: 두 개의 로그 파일에 시스템 파일 출력</span><span class="sxs-lookup"><span data-stu-id="6c9ef-122">Example 3: Output system files to two log files</span></span>

<span data-ttu-id="6c9ef-123">이 예에서는 두 개의 로그 파일 (누적 파일과 현재 파일)에 시스템 파일의 목록을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-123">This example saves a list of system files in a two log files, a cumulative file and a current file.</span></span>

```powershell
Get-ChildItem -Path D: -File -System -Recurse |
  Tee-Object -FilePath "c:\test\AllSystemFiles.txt" -Append |
    Out-File c:\test\NewSystemFiles.txt
```

<span data-ttu-id="6c9ef-124">이 명령은 cmdlet을 사용 하 여 `Get-ChildItem` D: 드라이브에서 시스템 파일에 대 한 재귀 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-124">The command uses the `Get-ChildItem` cmdlet to do a recursive search for system files on the D: drive.</span></span> <span data-ttu-id="6c9ef-125">파이프라인 연산자 (|)는 목록을 `Tee-Object` AllSystemFiles.txt 파일에 추가 하 고 파이프라인의 목록을 파이프라인으로 전달 하 여 `Out-File` NewSystemFiles.txt 파일에 목록을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-125">A pipeline operator (|) sends the list to `Tee-Object`, which appends the list to the AllSystemFiles.txt file and passes the list down the pipeline to the `Out-File` cmdlet, which saves the list in the NewSystemFiles.txt file.</span></span>

## <span data-ttu-id="6c9ef-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6c9ef-126">PARAMETERS</span></span>

### <span data-ttu-id="6c9ef-127">-추가</span><span class="sxs-lookup"><span data-stu-id="6c9ef-127">-Append</span></span>

<span data-ttu-id="6c9ef-128">Cmdlet이 지정 된 파일에 출력을 추가 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-128">Indicates that the cmdlet appends the output to the specified file.</span></span> <span data-ttu-id="6c9ef-129">이 매개 변수를 지정하지 않으면 새 내용이 경고 없이 파일의 기존 내용을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-129">Without this parameter, the new content replaces any existing content in the file without warning.</span></span>

<span data-ttu-id="6c9ef-130">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-130">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6c9ef-131">-FilePath</span><span class="sxs-lookup"><span data-stu-id="6c9ef-131">-FilePath</span></span>

<span data-ttu-id="6c9ef-132">이 cmdlet이 개체를 와일드 카드 문자에 저장 하도록 허용 하지만 단일 파일로 확인 해야 하는 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-132">Specifies a file that this cmdlet saves the object to Wildcard characters are permitted, but must resolve to a single file.</span></span>

```yaml
Type: System.String
Parameter Sets: File
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="6c9ef-133">-InputObject</span><span class="sxs-lookup"><span data-stu-id="6c9ef-133">-InputObject</span></span>

<span data-ttu-id="6c9ef-134">저장 및 표시할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-134">Specifies the object to be saved and displayed.</span></span> <span data-ttu-id="6c9ef-135">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-135">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="6c9ef-136">개체를로 파이프 할 수도 있습니다 `Tee-Object` .</span><span class="sxs-lookup"><span data-stu-id="6c9ef-136">You can also pipe an object to `Tee-Object`.</span></span>

<span data-ttu-id="6c9ef-137">에 **inputobject** 매개 변수를 사용 하는 경우 `Tee-Object` 명령 결과를로 파이프 하는 대신 `Tee-Object` **inputobject** 값은 값이 컬렉션인 경우에도 단일 개체로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-137">When you use the **InputObject** parameter with `Tee-Object`, instead of piping command results to `Tee-Object`, the **InputObject** value is treated as a single object even if the value is a collection.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6c9ef-138">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6c9ef-138">-LiteralPath</span></span>

<span data-ttu-id="6c9ef-139">이 cmdlet이 개체를 저장 하는 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-139">Specifies a file that this cmdlet saves the object to.</span></span> <span data-ttu-id="6c9ef-140">**FilePath** 와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-140">Unlike **FilePath** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="6c9ef-141">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-141">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="6c9ef-142">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-142">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="6c9ef-143">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-143">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6c9ef-144">-Variable</span><span class="sxs-lookup"><span data-stu-id="6c9ef-144">-Variable</span></span>

<span data-ttu-id="6c9ef-145">Cmdlet이 개체를 저장 하는 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-145">Specifies a variable that the cmdlet saves the object to.</span></span> <span data-ttu-id="6c9ef-146">앞에 달러 기호 ()를 사용 하지 않고 변수 이름을 입력 `$` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-146">Enter a variable name without the preceding dollar sign (`$`).</span></span>

```yaml
Type: System.String
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6c9ef-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6c9ef-147">CommonParameters</span></span>

<span data-ttu-id="6c9ef-148">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6c9ef-149">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6c9ef-150">입력</span><span class="sxs-lookup"><span data-stu-id="6c9ef-150">INPUTS</span></span>

### <span data-ttu-id="6c9ef-151">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="6c9ef-151">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="6c9ef-152">개체를로 파이프 할 수 있습니다 `Tee-Object` .</span><span class="sxs-lookup"><span data-stu-id="6c9ef-152">You can pipe objects to `Tee-Object`.</span></span>

## <span data-ttu-id="6c9ef-153">출력</span><span class="sxs-lookup"><span data-stu-id="6c9ef-153">OUTPUTS</span></span>

### <span data-ttu-id="6c9ef-154">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="6c9ef-154">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="6c9ef-155">`Tee-Object` 는 리디렉션되는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-155">`Tee-Object` returns the object that it redirects.</span></span>

## <span data-ttu-id="6c9ef-156">참고</span><span class="sxs-lookup"><span data-stu-id="6c9ef-156">NOTES</span></span>

<span data-ttu-id="6c9ef-157">`Out-File`Cmdlet 또는 리디렉션 연산자를 사용할 수도 있습니다 .이 연산자는 출력을 파일에 저장 하지만 파이프라인으로는 보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-157">You can also use the `Out-File` cmdlet or the redirection operator, both of which save the output in a file but do not send it down the pipeline.</span></span>

<span data-ttu-id="6c9ef-158">PowerShell 6부터 `Tee-Object` 은 파일에 쓸 때 BOM LESS utf-8 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-158">Beginning in PowerShell 6, `Tee-Object` uses BOM-less UTF-8 encoding when it writes to files.</span></span> <span data-ttu-id="6c9ef-159">다른 인코딩이 필요한 경우에는 `Out-File` **encoding** 매개 변수와 함께 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c9ef-159">If you need a different encoding, use the `Out-File` cmdlet with the **Encoding** parameter.</span></span>

## <span data-ttu-id="6c9ef-160">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6c9ef-160">RELATED LINKS</span></span>

[<span data-ttu-id="6c9ef-161">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="6c9ef-161">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="6c9ef-162">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="6c9ef-162">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="6c9ef-163">Group-Object</span><span class="sxs-lookup"><span data-stu-id="6c9ef-163">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="6c9ef-164">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="6c9ef-164">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="6c9ef-165">New-Object</span><span class="sxs-lookup"><span data-stu-id="6c9ef-165">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="6c9ef-166">Select-Object</span><span class="sxs-lookup"><span data-stu-id="6c9ef-166">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="6c9ef-167">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="6c9ef-167">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="6c9ef-168">Where-Object</span><span class="sxs-lookup"><span data-stu-id="6c9ef-168">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

[<span data-ttu-id="6c9ef-169">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="6c9ef-169">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)
