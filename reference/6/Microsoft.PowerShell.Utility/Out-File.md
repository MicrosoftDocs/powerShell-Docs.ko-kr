---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-file?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-File
ms.openlocfilehash: f3cd58bffde8bcb6dab488a9e40e69d7435133e4
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "93220065"
---
# <span data-ttu-id="25f9c-103">Out-File</span><span class="sxs-lookup"><span data-stu-id="25f9c-103">Out-File</span></span>

## <span data-ttu-id="25f9c-104">개요</span><span class="sxs-lookup"><span data-stu-id="25f9c-104">SYNOPSIS</span></span>
<span data-ttu-id="25f9c-105">출력을 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-105">Sends output to a file.</span></span>

## <span data-ttu-id="25f9c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="25f9c-106">SYNTAX</span></span>

### <span data-ttu-id="25f9c-107">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="25f9c-107">ByPath (Default)</span></span>

```
Out-File [-FilePath] <string> [[-Encoding] <Encoding>] [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="25f9c-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="25f9c-108">ByLiteralPath</span></span>

```
Out-File [[-Encoding] <Encoding>] -LiteralPath <string> [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="25f9c-109">설명</span><span class="sxs-lookup"><span data-stu-id="25f9c-109">DESCRIPTION</span></span>

<span data-ttu-id="25f9c-110">`Out-File`Cmdlet은 출력을 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-110">The `Out-File` cmdlet sends output to a file.</span></span> <span data-ttu-id="25f9c-111">PowerShell의 형식 지정 시스템을 암시적으로 사용 하 여 파일에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-111">It implicitly uses PowerShell's formatting system to write to the file.</span></span> <span data-ttu-id="25f9c-112">이 파일은 터미널과 동일한 표시 표현을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-112">The file receives the same display representation as the terminal.</span></span> <span data-ttu-id="25f9c-113">즉, 모든 입력 개체가 문자열인 경우를 제외 하 고는 출력이 프로그래밍 처리에 적합 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-113">This means that the output may not be ideal for programmatic processing unless all input objects are strings.</span></span>
<span data-ttu-id="25f9c-114">출력에 대 한 매개 변수를 지정 해야 하는 경우 `Out-File` 리디렉션 연산자 () 대신를 사용 `>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-114">When you need to specify parameters for the output, use `Out-File` rather than the redirection operator (`>`).</span></span> <span data-ttu-id="25f9c-115">리디렉션에 대 한 자세한 내용은 [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="25f9c-115">For more information about redirection, see [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).</span></span>

## <span data-ttu-id="25f9c-116">예제</span><span class="sxs-lookup"><span data-stu-id="25f9c-116">EXAMPLES</span></span>

### <span data-ttu-id="25f9c-117">예제 1: 출력 보내기 및 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="25f9c-117">Example 1: Send output and create a file</span></span>

<span data-ttu-id="25f9c-118">이 예제에서는 로컬 컴퓨터의 프로세스 목록을 파일로 보내는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-118">This example shows how to send a list of the local computer's processes to a file.</span></span> <span data-ttu-id="25f9c-119">파일이 없으면 `Out-File` 지정 된 경로에 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-119">If the file does not exist, `Out-File` creates the file in the specified path.</span></span>

```powershell
Get-Process | Out-File -FilePath .\Process.txt
Get-Content -Path .\Process.txt
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     29    22.39      35.40      10.98   42764   9 Application
     53    99.04     113.96       0.00   32664   0 CcmExec
     27    96.62     112.43     113.00   17720   9 Code
```

<span data-ttu-id="25f9c-120">`Get-Process`Cmdlet은 로컬 컴퓨터에서 실행 중인 프로세스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-120">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="25f9c-121">**프로세스** 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="25f9c-121">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="25f9c-122">`Out-File`**FilePath** 매개 변수를 사용 하 고 **Process.txt** 이라는 현재 디렉터리에 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-122">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="25f9c-123">`Get-Content`명령은 파일에서 콘텐츠를 가져와 PowerShell 콘솔에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-123">The `Get-Content` command gets content from the file and displays it in the PowerShell console.</span></span>

### <span data-ttu-id="25f9c-124">예 2: 기존 파일을 덮어쓰지 않도록 방지</span><span class="sxs-lookup"><span data-stu-id="25f9c-124">Example 2: Prevent an existing file from being overwritten</span></span>

<span data-ttu-id="25f9c-125">이 예에서는 기존 파일을 덮어쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-125">This example prevents an existing file from being overwritten.</span></span> <span data-ttu-id="25f9c-126">기본적으로는 `Out-File` 기존 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-126">By default, `Out-File` overwrites existing files.</span></span>

```powershell
Get-Process | Out-File -FilePath .\Process.txt -NoClobber
```

```Output
Out-File : The file 'C:\Test\Process.txt' already exists.
At line:1 char:15
+ Get-Process | Out-File -FilePath .\Process.txt -NoClobber
+               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

<span data-ttu-id="25f9c-127">`Get-Process`Cmdlet은 로컬 컴퓨터에서 실행 중인 프로세스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-127">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="25f9c-128">**프로세스** 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="25f9c-128">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="25f9c-129">`Out-File`**FilePath** 매개 변수를 사용 하 고 **Process.txt** 이라는 현재 디렉터리의 파일에 쓰려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-129">`Out-File` uses the **FilePath** parameter and attempts to write to a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="25f9c-130">**NoClobber** 매개 변수는 파일을 덮어쓰지 않도록 방지 하 고 파일이 이미 존재 한다는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-130">The **NoClobber** parameter prevents the file from being overwritten and displays a message that the file already exists.</span></span>

### <span data-ttu-id="25f9c-131">예제 3: ASCII 형식으로 파일에 출력 보내기</span><span class="sxs-lookup"><span data-stu-id="25f9c-131">Example 3: Send output to a file in ASCII format</span></span>

<span data-ttu-id="25f9c-132">이 예제에서는 특정 인코딩 형식을 사용 하 여 출력을 인코딩하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-132">This example shows how to encode output with a specific encoding type.</span></span>

```powershell
$Procs = Get-Process
Out-File -FilePath .\Process.txt -InputObject $Procs -Encoding ASCII -Width 50
```

<span data-ttu-id="25f9c-133">`Get-Process`Cmdlet은 로컬 컴퓨터에서 실행 중인 프로세스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-133">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="25f9c-134">**프로세스** 개체는 변수에 저장 됩니다 `$Procs` .</span><span class="sxs-lookup"><span data-stu-id="25f9c-134">The **Process** objects are stored in the variable, `$Procs`.</span></span> <span data-ttu-id="25f9c-135">`Out-File`**FilePath** 매개 변수를 사용 하 고 **Process.txt** 이라는 현재 디렉터리에 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-135">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="25f9c-136">**InputObject** 매개 변수는 `$Procs` **Process.txt** 파일에 프로세스 개체를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-136">The **InputObject** parameter passes the process objects in `$Procs` to the file **Process.txt**.</span></span> <span data-ttu-id="25f9c-137">**Encoding** 매개 변수는 출력을 **ASCII** 형식으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-137">The **Encoding** parameter converts the output to **ASCII** format.</span></span> <span data-ttu-id="25f9c-138">**Width** 매개 변수는 파일의 각 줄을 50 자로 제한 하므로 일부 데이터가 잘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-138">The **Width** parameter limits each line in the file to 50 characters so some data might be truncated.</span></span>

### <span data-ttu-id="25f9c-139">예제 4: 공급자를 사용 하 여 출력을 파일로 보내기</span><span class="sxs-lookup"><span data-stu-id="25f9c-139">Example 4: Use a provider and send output to a file</span></span>

<span data-ttu-id="25f9c-140">이 예제에서는 `Out-File` **파일 시스템** 공급자 드라이브에 없는 경우 cmdlet을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-140">This example shows how to use the `Out-File` cmdlet when you are not in a **FileSystem** provider drive.</span></span> <span data-ttu-id="25f9c-141">Cmdlet을 사용 `Get-PSProvider` 하 여 로컬 컴퓨터의 공급자를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-141">Use the `Get-PSProvider` cmdlet to view the providers on your local computer.</span></span> <span data-ttu-id="25f9c-142">자세한 내용은 [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25f9c-142">For more information, see [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).</span></span>

```
PS> Set-Location -Path Alias:

PS> Get-Location

Path
----
Alias:\

PS> Get-ChildItem | Out-File -FilePath C:\TestDir\AliasNames.txt

PS> Get-Content -Path C:\TestDir\AliasNames.txt

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           cat -> Get-Content
```

<span data-ttu-id="25f9c-143">이 `Set-Location` 명령은 **Path** 매개 변수를 사용 하 여 현재 위치를 레지스트리 공급자로 설정 합니다 `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="25f9c-143">The `Set-Location` command uses the **Path** parameter to set the current location to the registry provider `Alias:`.</span></span> <span data-ttu-id="25f9c-144">`Get-Location`Cmdlet은에 대 한 전체 경로를 표시 합니다 `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="25f9c-144">The `Get-Location` cmdlet displays the complete path for `Alias:`.</span></span>
<span data-ttu-id="25f9c-145">`Get-ChildItem` 파이프라인의 개체를 cmdlet으로 보냅니다 `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="25f9c-145">`Get-ChildItem` sends objects down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="25f9c-146">`Out-File`**FilePath** 매개 변수를 사용 하 여 출력에 대 한 전체 경로와 파일 이름을 지정 **C:\TestDir\AliasNames.txt** 합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-146">`Out-File` uses the **FilePath** parameter to specify the complete path and filename for the output, **C:\TestDir\AliasNames.txt**.</span></span> <span data-ttu-id="25f9c-147">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 PowerShell 콘솔에 파일의 콘텐츠를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-147">The `Get-Content` cmdlet uses the **Path** parameter and displays the file's content in the PowerShell console.</span></span>

## <span data-ttu-id="25f9c-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="25f9c-148">PARAMETERS</span></span>

### <span data-ttu-id="25f9c-149">-추가</span><span class="sxs-lookup"><span data-stu-id="25f9c-149">-Append</span></span>

<span data-ttu-id="25f9c-150">기존 파일의 끝에 출력을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-150">Adds the output to the end of an existing file.</span></span>

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

### <span data-ttu-id="25f9c-151">-Encoding</span><span class="sxs-lookup"><span data-stu-id="25f9c-151">-Encoding</span></span>

<span data-ttu-id="25f9c-152">대상 파일의 인코딩 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-152">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="25f9c-153">기본값은 `utf8NoBOM`입니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-153">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="25f9c-154">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-154">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="25f9c-155">`ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-155">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="25f9c-156">`bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-156">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="25f9c-157">`oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-157">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="25f9c-158">`unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-158">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="25f9c-159">`utf7`: UTF-7 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-159">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="25f9c-160">`utf8`: UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-160">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="25f9c-161">`utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-161">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="25f9c-162">`utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-162">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="25f9c-163">`utf32`: U t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-163">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="25f9c-164">PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="25f9c-164">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="25f9c-165">자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="25f9c-165">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: 1
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="25f9c-166">-FilePath</span><span class="sxs-lookup"><span data-stu-id="25f9c-166">-FilePath</span></span>

<span data-ttu-id="25f9c-167">출력 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-167">Specifies the path to the output file.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="25f9c-168">-Force</span><span class="sxs-lookup"><span data-stu-id="25f9c-168">-Force</span></span>

<span data-ttu-id="25f9c-169">읽기 전용 특성을 재정의 하 고 기존 읽기 전용 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-169">Overrides the read-only attribute and overwrites an existing read-only file.</span></span> <span data-ttu-id="25f9c-170">**Force** 매개 변수는 보안 제한을 재정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-170">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="25f9c-171">-InputObject</span><span class="sxs-lookup"><span data-stu-id="25f9c-171">-InputObject</span></span>

<span data-ttu-id="25f9c-172">파일에 기록할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-172">Specifies the objects to be written to the file.</span></span> <span data-ttu-id="25f9c-173">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="25f9c-173">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="25f9c-174">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="25f9c-174">-LiteralPath</span></span>

<span data-ttu-id="25f9c-175">출력 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-175">Specifies the path to the output file.</span></span> <span data-ttu-id="25f9c-176">**LiteralPath** 매개 변수는 형식화 된 그대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-176">The **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="25f9c-177">와일드 카드 문자 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-177">Wildcard characters are not accepted.</span></span> <span data-ttu-id="25f9c-178">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="25f9c-178">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="25f9c-179">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-179">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="25f9c-180">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="25f9c-180">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="25f9c-181">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="25f9c-181">-NoClobber</span></span>

<span data-ttu-id="25f9c-182">**NoClobber** 는 기존 파일을 덮어쓰지 않도록 방지 하 고 파일이 이미 존재 한다는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-182">**NoClobber** prevents an existing file from being overwritten and displays a message that the file already exists.</span></span> <span data-ttu-id="25f9c-183">기본적으로 지정 된 경로에 파일이 있으면는 `Out-File` 경고 없이 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-183">By default, if a file exists in the specified path, `Out-File` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="25f9c-184">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="25f9c-184">-NoNewline</span></span>

<span data-ttu-id="25f9c-185">파일에 기록 된 콘텐츠가 줄 바꿈 문자로 끝나지 않도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-185">Specifies that the content written to the file does not end with a newline character.</span></span> <span data-ttu-id="25f9c-186">입력 개체의 문자열 표현은 연결 되어 출력을 형성 합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-186">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="25f9c-187">출력 문자열 사이에 공백이 나 줄바꿈 삽입 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-187">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="25f9c-188">마지막 출력 문자열 뒤에는 줄 바꿈이 추가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-188">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="25f9c-189">-너비</span><span class="sxs-lookup"><span data-stu-id="25f9c-189">-Width</span></span>

<span data-ttu-id="25f9c-190">출력의 각 줄에 포함되는 문자 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-190">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="25f9c-191">이 문자보다 많으면 잘리거나 다음 줄로 넘어갑니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-191">Any additional characters are truncated, not wrapped.</span></span> <span data-ttu-id="25f9c-192">이 매개 변수를 사용 하지 않으면 호스트의 특성에 따라 너비가 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-192">If this parameter is not used, the width is determined by the characteristics of the host.</span></span> <span data-ttu-id="25f9c-193">PowerShell 콘솔의 기본값은 80 자입니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-193">The default for the PowerShell console is 80 characters.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="25f9c-194">-Confirm</span><span class="sxs-lookup"><span data-stu-id="25f9c-194">-Confirm</span></span>

<span data-ttu-id="25f9c-195">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-195">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="25f9c-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="25f9c-196">-WhatIf</span></span>

<span data-ttu-id="25f9c-197">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-197">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="25f9c-198">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-198">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="25f9c-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="25f9c-199">CommonParameters</span></span>

<span data-ttu-id="25f9c-200">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="25f9c-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="25f9c-201">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25f9c-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="25f9c-202">입력</span><span class="sxs-lookup"><span data-stu-id="25f9c-202">INPUTS</span></span>

### <span data-ttu-id="25f9c-203">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="25f9c-203">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="25f9c-204">모든 개체를로 파이프 할 수 있습니다 `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="25f9c-204">You can pipe any object to `Out-File`.</span></span>

## <span data-ttu-id="25f9c-205">출력</span><span class="sxs-lookup"><span data-stu-id="25f9c-205">OUTPUTS</span></span>

### <span data-ttu-id="25f9c-206">없음</span><span class="sxs-lookup"><span data-stu-id="25f9c-206">None</span></span>

<span data-ttu-id="25f9c-207">`Out-File` 는 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-207">`Out-File` does not generate any output.</span></span>

## <span data-ttu-id="25f9c-208">참고</span><span class="sxs-lookup"><span data-stu-id="25f9c-208">NOTES</span></span>

<span data-ttu-id="25f9c-209">입력 개체는 터미널에 있을 때 자동으로 서식이 지정 되지만 cmdlet을 사용 `Format-*` 하 여 파일에 대 한 출력 형식을 명시적으로 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-209">Input objects are automatically formatted as they would be in the terminal, but you can use a `Format-*` cmdlet to explicitly control the formatting of the output to the file.</span></span> <span data-ttu-id="25f9c-210">예를 들어 `Get-Date | Format-List | Out-File out.txt`</span><span class="sxs-lookup"><span data-stu-id="25f9c-210">For example, `Get-Date | Format-List | Out-File out.txt`</span></span>

<span data-ttu-id="25f9c-211">Cmdlet에 PowerShell 명령의 출력을 보내려면 파이프라인을 `Out-File` 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-211">To send a PowerShell command's output to the `Out-File` cmdlet, use the pipeline.</span></span> <span data-ttu-id="25f9c-212">또는 변수에 데이터를 저장 하 고 **InputObject** 매개 변수를 사용 하 여 cmdlet에 데이터를 전달할 수 있습니다 `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="25f9c-212">Alternatively, you can store data in a variable and use the **InputObject** parameter to pass data to the `Out-File` cmdlet.</span></span>

<span data-ttu-id="25f9c-213">`Out-File` 데이터를 파일에 저장 하지만 파이프라인에 대 한 출력 개체를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25f9c-213">`Out-File` saves data to a file but it does not produce any output objects to the pipeline.</span></span>

## <span data-ttu-id="25f9c-214">관련 링크</span><span class="sxs-lookup"><span data-stu-id="25f9c-214">RELATED LINKS</span></span>

[<span data-ttu-id="25f9c-215">about_Providers</span><span class="sxs-lookup"><span data-stu-id="25f9c-215">about_Providers</span></span>](../Microsoft.Powershell.Core/About/about_Providers.md)

[<span data-ttu-id="25f9c-216">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="25f9c-216">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="25f9c-217">Out-Default</span><span class="sxs-lookup"><span data-stu-id="25f9c-217">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="25f9c-218">Out-Host</span><span class="sxs-lookup"><span data-stu-id="25f9c-218">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="25f9c-219">Out-Null</span><span class="sxs-lookup"><span data-stu-id="25f9c-219">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="25f9c-220">Out-String</span><span class="sxs-lookup"><span data-stu-id="25f9c-220">Out-String</span></span>](Out-String.md)

[<span data-ttu-id="25f9c-221">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="25f9c-221">Tee-Object</span></span>](Tee-Object.md)
