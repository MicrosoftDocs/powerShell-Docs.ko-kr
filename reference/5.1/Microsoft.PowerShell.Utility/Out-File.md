---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-file?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-File
ms.openlocfilehash: 71602cb0621c835257f556a0a9db15bd754a3aee
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "93220081"
---
# <span data-ttu-id="c9e6d-103">Out-File</span><span class="sxs-lookup"><span data-stu-id="c9e6d-103">Out-File</span></span>

## <span data-ttu-id="c9e6d-104">개요</span><span class="sxs-lookup"><span data-stu-id="c9e6d-104">SYNOPSIS</span></span>
<span data-ttu-id="c9e6d-105">출력을 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-105">Sends output to a file.</span></span>

## <span data-ttu-id="c9e6d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c9e6d-106">SYNTAX</span></span>

### <span data-ttu-id="c9e6d-107">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="c9e6d-107">ByPath (Default)</span></span>

```
Out-File [-FilePath] <string> [[-Encoding] <string>] [-Append] [-Force] [-NoClobber] [-Width <int>]
 [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c9e6d-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="c9e6d-108">ByLiteralPath</span></span>

```
Out-File [[-Encoding] <string>] -LiteralPath <string> [-Append] [-Force] [-NoClobber] [-Width <int>]
 [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c9e6d-109">설명</span><span class="sxs-lookup"><span data-stu-id="c9e6d-109">DESCRIPTION</span></span>

<span data-ttu-id="c9e6d-110">`Out-File`Cmdlet은 출력을 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-110">The `Out-File` cmdlet sends output to a file.</span></span> <span data-ttu-id="c9e6d-111">PowerShell의 형식 지정 시스템을 암시적으로 사용 하 여 파일에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-111">It implicitly uses PowerShell's formatting system to write to the file.</span></span> <span data-ttu-id="c9e6d-112">이 파일은 터미널과 동일한 표시 표현을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-112">The file receives the same display representation as the terminal.</span></span> <span data-ttu-id="c9e6d-113">즉, 모든 입력 개체가 문자열인 경우를 제외 하 고는 출력이 프로그래밍 처리에 적합 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-113">This means that the output may not be ideal for programmatic processing unless all input objects are strings.</span></span>
<span data-ttu-id="c9e6d-114">출력에 대 한 매개 변수를 지정 해야 하는 경우 `Out-File` 리디렉션 연산자 () 대신를 사용 `>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-114">When you need to specify parameters for the output, use `Out-File` rather than the redirection operator (`>`).</span></span> <span data-ttu-id="c9e6d-115">리디렉션에 대 한 자세한 내용은 [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-115">For more information about redirection, see [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).</span></span>

## <span data-ttu-id="c9e6d-116">예제</span><span class="sxs-lookup"><span data-stu-id="c9e6d-116">EXAMPLES</span></span>

### <span data-ttu-id="c9e6d-117">예제 1: 출력 보내기 및 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="c9e6d-117">Example 1: Send output and create a file</span></span>

<span data-ttu-id="c9e6d-118">이 예제에서는 로컬 컴퓨터의 프로세스 목록을 파일로 보내는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-118">This example shows how to send a list of the local computer's processes to a file.</span></span> <span data-ttu-id="c9e6d-119">파일이 없으면 `Out-File` 지정 된 경로에 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-119">If the file does not exist, `Out-File` creates the file in the specified path.</span></span>

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

<span data-ttu-id="c9e6d-120">`Get-Process`Cmdlet은 로컬 컴퓨터에서 실행 중인 프로세스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-120">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="c9e6d-121">**프로세스** 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="c9e6d-121">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="c9e6d-122">`Out-File`**FilePath** 매개 변수를 사용 하 고 **Process.txt** 이라는 현재 디렉터리에 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-122">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="c9e6d-123">`Get-Content`명령은 파일에서 콘텐츠를 가져와 PowerShell 콘솔에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-123">The `Get-Content` command gets content from the file and displays it in the PowerShell console.</span></span>

### <span data-ttu-id="c9e6d-124">예 2: 기존 파일을 덮어쓰지 않도록 방지</span><span class="sxs-lookup"><span data-stu-id="c9e6d-124">Example 2: Prevent an existing file from being overwritten</span></span>

<span data-ttu-id="c9e6d-125">이 예에서는 기존 파일을 덮어쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-125">This example prevents an existing file from being overwritten.</span></span> <span data-ttu-id="c9e6d-126">기본적으로는 `Out-File` 기존 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-126">By default, `Out-File` overwrites existing files.</span></span>

```powershell
Get-Process | Out-File -FilePath .\Process.txt -NoClobber
```

```Output
Out-File : The file 'C:\Test\Process.txt' already exists.
At line:1 char:15
+ Get-Process | Out-File -FilePath .\Process.txt -NoClobber
+               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

<span data-ttu-id="c9e6d-127">`Get-Process`Cmdlet은 로컬 컴퓨터에서 실행 중인 프로세스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-127">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="c9e6d-128">**프로세스** 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="c9e6d-128">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="c9e6d-129">`Out-File`**FilePath** 매개 변수를 사용 하 고 **Process.txt** 이라는 현재 디렉터리의 파일에 쓰려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-129">`Out-File` uses the **FilePath** parameter and attempts to write to a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="c9e6d-130">**NoClobber** 매개 변수는 파일을 덮어쓰지 않도록 방지 하 고 파일이 이미 존재 한다는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-130">The **NoClobber** parameter prevents the file from being overwritten and displays a message that the file already exists.</span></span>

### <span data-ttu-id="c9e6d-131">예제 3: ASCII 형식으로 파일에 출력 보내기</span><span class="sxs-lookup"><span data-stu-id="c9e6d-131">Example 3: Send output to a file in ASCII format</span></span>

<span data-ttu-id="c9e6d-132">이 예제에서는 특정 인코딩 형식을 사용 하 여 출력을 인코딩하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-132">This example shows how to encode output with a specific encoding type.</span></span>

```powershell
$Procs = Get-Process
Out-File -FilePath .\Process.txt -InputObject $Procs -Encoding ASCII -Width 50
```

<span data-ttu-id="c9e6d-133">`Get-Process`Cmdlet은 로컬 컴퓨터에서 실행 중인 프로세스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-133">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="c9e6d-134">**프로세스** 개체는 변수에 저장 됩니다 `$Procs` .</span><span class="sxs-lookup"><span data-stu-id="c9e6d-134">The **Process** objects are stored in the variable, `$Procs`.</span></span> <span data-ttu-id="c9e6d-135">`Out-File`**FilePath** 매개 변수를 사용 하 고 **Process.txt** 이라는 현재 디렉터리에 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-135">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="c9e6d-136">**InputObject** 매개 변수는 `$Procs` **Process.txt** 파일에 프로세스 개체를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-136">The **InputObject** parameter passes the process objects in `$Procs` to the file **Process.txt**.</span></span> <span data-ttu-id="c9e6d-137">**Encoding** 매개 변수는 출력을 **ASCII** 형식으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-137">The **Encoding** parameter converts the output to **ASCII** format.</span></span> <span data-ttu-id="c9e6d-138">**Width** 매개 변수는 파일의 각 줄을 50 자로 제한 하므로 일부 데이터가 잘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-138">The **Width** parameter limits each line in the file to 50 characters so some data might be truncated.</span></span>

### <span data-ttu-id="c9e6d-139">예제 4: 공급자를 사용 하 여 출력을 파일로 보내기</span><span class="sxs-lookup"><span data-stu-id="c9e6d-139">Example 4: Use a provider and send output to a file</span></span>

<span data-ttu-id="c9e6d-140">이 예제에서는 `Out-File` **파일 시스템** 공급자 드라이브에 없는 경우 cmdlet을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-140">This example shows how to use the `Out-File` cmdlet when you are not in a **FileSystem** provider drive.</span></span> <span data-ttu-id="c9e6d-141">Cmdlet을 사용 `Get-PSProvider` 하 여 로컬 컴퓨터의 공급자를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-141">Use the `Get-PSProvider` cmdlet to view the providers on your local computer.</span></span> <span data-ttu-id="c9e6d-142">자세한 내용은 [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-142">For more information, see [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).</span></span>

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

<span data-ttu-id="c9e6d-143">이 `Set-Location` 명령은 **Path** 매개 변수를 사용 하 여 현재 위치를 레지스트리 공급자로 설정 합니다 `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="c9e6d-143">The `Set-Location` command uses the **Path** parameter to set the current location to the registry provider `Alias:`.</span></span> <span data-ttu-id="c9e6d-144">`Get-Location`Cmdlet은에 대 한 전체 경로를 표시 합니다 `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="c9e6d-144">The `Get-Location` cmdlet displays the complete path for `Alias:`.</span></span>
<span data-ttu-id="c9e6d-145">`Get-ChildItem` 파이프라인의 개체를 cmdlet으로 보냅니다 `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="c9e6d-145">`Get-ChildItem` sends objects down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="c9e6d-146">`Out-File`**FilePath** 매개 변수를 사용 하 여 출력에 대 한 전체 경로와 파일 이름을 지정 **C:\TestDir\AliasNames.txt** 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-146">`Out-File` uses the **FilePath** parameter to specify the complete path and filename for the output, **C:\TestDir\AliasNames.txt**.</span></span> <span data-ttu-id="c9e6d-147">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 PowerShell 콘솔에 파일의 콘텐츠를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-147">The `Get-Content` cmdlet uses the **Path** parameter and displays the file's content in the PowerShell console.</span></span>

## <span data-ttu-id="c9e6d-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c9e6d-148">PARAMETERS</span></span>

### <span data-ttu-id="c9e6d-149">-추가</span><span class="sxs-lookup"><span data-stu-id="c9e6d-149">-Append</span></span>

<span data-ttu-id="c9e6d-150">기존 파일의 끝에 출력을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-150">Adds the output to the end of an existing file.</span></span> <span data-ttu-id="c9e6d-151">**인코딩을** 지정 하지 않으면 cmdlet은 기본 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-151">If no **Encoding** is specified, the cmdlet uses the default encoding.</span></span> <span data-ttu-id="c9e6d-152">해당 인코딩은 대상 파일의 인코딩과 일치 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-152">That encoding may not match the encoding of the target file.</span></span> <span data-ttu-id="c9e6d-153">이 동작은 리디렉션 연산자 ()와 동일 합니다 `>>` .</span><span class="sxs-lookup"><span data-stu-id="c9e6d-153">This is the same behavior as the redirection operator (`>>`).</span></span>

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

### <span data-ttu-id="c9e6d-154">-Encoding</span><span class="sxs-lookup"><span data-stu-id="c9e6d-154">-Encoding</span></span>

<span data-ttu-id="c9e6d-155">대상 파일의 인코딩 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-155">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="c9e6d-156">기본값은 `unicode`입니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-156">The default value is `unicode`.</span></span>

<span data-ttu-id="c9e6d-157">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-157">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="c9e6d-158">`ascii` ASCII (7 비트) 문자 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-158">`ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="c9e6d-159">`bigendianunicode` 에서는 u t f-16을 빅 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-159">`bigendianunicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="c9e6d-160">`default` 시스템의 활성 코드 페이지에 해당 하는 인코딩을 사용 합니다 (일반적으로 ANSI).</span><span class="sxs-lookup"><span data-stu-id="c9e6d-160">`default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="c9e6d-161">`oem` 시스템의 현재 OEM 코드 페이지에 해당 하는 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-161">`oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="c9e6d-162">`string`: `unicode`과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-162">`string` Same as `unicode`.</span></span>
- <span data-ttu-id="c9e6d-163">`unicode` 는 u t f-16을 약간 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-163">`unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="c9e6d-164">`unknown`: `unicode`과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-164">`unknown` Same as `unicode`.</span></span>
- <span data-ttu-id="c9e6d-165">`utf7` 는 u t f-7을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-165">`utf7` Uses UTF-7.</span></span>
- <span data-ttu-id="c9e6d-166">`utf8` 는 u t f-8을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-166">`utf8` Uses UTF-8.</span></span>
- <span data-ttu-id="c9e6d-167">`utf32` 는 u t f-32을 작은 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-167">`utf32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: 1
Default value: Unicode
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c9e6d-168">-FilePath</span><span class="sxs-lookup"><span data-stu-id="c9e6d-168">-FilePath</span></span>

<span data-ttu-id="c9e6d-169">출력 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-169">Specifies the path to the output file.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c9e6d-170">-Force</span><span class="sxs-lookup"><span data-stu-id="c9e6d-170">-Force</span></span>

<span data-ttu-id="c9e6d-171">읽기 전용 특성을 재정의 하 고 기존 읽기 전용 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-171">Overrides the read-only attribute and overwrites an existing read-only file.</span></span> <span data-ttu-id="c9e6d-172">**Force** 매개 변수는 보안 제한을 재정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-172">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="c9e6d-173">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c9e6d-173">-InputObject</span></span>

<span data-ttu-id="c9e6d-174">파일에 기록할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-174">Specifies the objects to be written to the file.</span></span> <span data-ttu-id="c9e6d-175">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-175">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="c9e6d-176">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c9e6d-176">-LiteralPath</span></span>

<span data-ttu-id="c9e6d-177">출력 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-177">Specifies the path to the output file.</span></span> <span data-ttu-id="c9e6d-178">**LiteralPath** 매개 변수는 형식화 된 그대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-178">The **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="c9e6d-179">와일드 카드 문자 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-179">Wildcard characters are not accepted.</span></span> <span data-ttu-id="c9e6d-180">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-180">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="c9e6d-181">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-181">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="c9e6d-182">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-182">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c9e6d-183">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="c9e6d-183">-NoClobber</span></span>

<span data-ttu-id="c9e6d-184">**NoClobber** 는 기존 파일을 덮어쓰지 않도록 방지 하 고 파일이 이미 존재 한다는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-184">**NoClobber** prevents an existing file from being overwritten and displays a message that the file already exists.</span></span> <span data-ttu-id="c9e6d-185">기본적으로 지정 된 경로에 파일이 있으면는 `Out-File` 경고 없이 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-185">By default, if a file exists in the specified path, `Out-File` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="c9e6d-186">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="c9e6d-186">-NoNewline</span></span>

<span data-ttu-id="c9e6d-187">파일에 기록 된 콘텐츠가 줄 바꿈 문자로 끝나지 않도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-187">Specifies that the content written to the file does not end with a newline character.</span></span> <span data-ttu-id="c9e6d-188">입력 개체의 문자열 표현은 연결 되어 출력을 형성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-188">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="c9e6d-189">출력 문자열 사이에 공백이 나 줄바꿈 삽입 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-189">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="c9e6d-190">마지막 출력 문자열 뒤에는 줄 바꿈이 추가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-190">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="c9e6d-191">-너비</span><span class="sxs-lookup"><span data-stu-id="c9e6d-191">-Width</span></span>

<span data-ttu-id="c9e6d-192">출력의 각 줄에 포함되는 문자 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-192">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="c9e6d-193">이 문자보다 많으면 잘리거나 다음 줄로 넘어갑니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-193">Any additional characters are truncated, not wrapped.</span></span> <span data-ttu-id="c9e6d-194">이 매개 변수를 사용 하지 않으면 호스트의 특성에 따라 너비가 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-194">If this parameter is not used, the width is determined by the characteristics of the host.</span></span> <span data-ttu-id="c9e6d-195">PowerShell 콘솔의 기본값은 80 자입니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-195">The default for the PowerShell console is 80 characters.</span></span>

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

### <span data-ttu-id="c9e6d-196">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c9e6d-196">-Confirm</span></span>

<span data-ttu-id="c9e6d-197">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-197">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c9e6d-198">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c9e6d-198">-WhatIf</span></span>

<span data-ttu-id="c9e6d-199">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-199">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="c9e6d-200">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-200">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c9e6d-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c9e6d-201">CommonParameters</span></span>

<span data-ttu-id="c9e6d-202">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-202">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c9e6d-203">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-203">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c9e6d-204">입력</span><span class="sxs-lookup"><span data-stu-id="c9e6d-204">INPUTS</span></span>

### <span data-ttu-id="c9e6d-205">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="c9e6d-205">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="c9e6d-206">모든 개체를로 파이프 할 수 있습니다 `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="c9e6d-206">You can pipe any object to `Out-File`.</span></span>

## <span data-ttu-id="c9e6d-207">출력</span><span class="sxs-lookup"><span data-stu-id="c9e6d-207">OUTPUTS</span></span>

### <span data-ttu-id="c9e6d-208">없음</span><span class="sxs-lookup"><span data-stu-id="c9e6d-208">None</span></span>

<span data-ttu-id="c9e6d-209">`Out-File` 는 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-209">`Out-File` does not generate any output.</span></span>

## <span data-ttu-id="c9e6d-210">참고</span><span class="sxs-lookup"><span data-stu-id="c9e6d-210">NOTES</span></span>

<span data-ttu-id="c9e6d-211">입력 개체는 터미널에 있을 때 자동으로 서식이 지정 되지만 cmdlet을 사용 `Format-*` 하 여 파일에 대 한 출력 형식을 명시적으로 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-211">Input objects are automatically formatted as they would be in the terminal, but you can use a `Format-*` cmdlet to explicitly control the formatting of the output to the file.</span></span> <span data-ttu-id="c9e6d-212">예를 들어 `Get-Date | Format-List | Out-File out.txt`</span><span class="sxs-lookup"><span data-stu-id="c9e6d-212">For example, `Get-Date | Format-List | Out-File out.txt`</span></span>

<span data-ttu-id="c9e6d-213">Cmdlet에 PowerShell 명령의 출력을 보내려면 파이프라인을 `Out-File` 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-213">To send a PowerShell command's output to the `Out-File` cmdlet, use the pipeline.</span></span> <span data-ttu-id="c9e6d-214">또는 변수에 데이터를 저장 하 고 **InputObject** 매개 변수를 사용 하 여 cmdlet에 데이터를 전달할 수 있습니다 `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="c9e6d-214">Alternatively, you can store data in a variable and use the **InputObject** parameter to pass data to the `Out-File` cmdlet.</span></span>

<span data-ttu-id="c9e6d-215">`Out-File` 데이터를 파일에 저장 하지만 파이프라인에 대 한 출력 개체를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e6d-215">`Out-File` saves data to a file but it does not produce any output objects to the pipeline.</span></span>

## <span data-ttu-id="c9e6d-216">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c9e6d-216">RELATED LINKS</span></span>

[<span data-ttu-id="c9e6d-217">about_Providers</span><span class="sxs-lookup"><span data-stu-id="c9e6d-217">about_Providers</span></span>](../Microsoft.Powershell.Core/About/about_Providers.md)

[<span data-ttu-id="c9e6d-218">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="c9e6d-218">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="c9e6d-219">Out-Default</span><span class="sxs-lookup"><span data-stu-id="c9e6d-219">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="c9e6d-220">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="c9e6d-220">Out-GridView</span></span>](Out-GridView.md)

[<span data-ttu-id="c9e6d-221">Out-Host</span><span class="sxs-lookup"><span data-stu-id="c9e6d-221">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="c9e6d-222">Out-Null</span><span class="sxs-lookup"><span data-stu-id="c9e6d-222">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="c9e6d-223">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="c9e6d-223">Out-Printer</span></span>](Out-Printer.md)

[<span data-ttu-id="c9e6d-224">Out-String</span><span class="sxs-lookup"><span data-stu-id="c9e6d-224">Out-String</span></span>](Out-String.md)

[<span data-ttu-id="c9e6d-225">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="c9e6d-225">Tee-Object</span></span>](Tee-Object.md)
