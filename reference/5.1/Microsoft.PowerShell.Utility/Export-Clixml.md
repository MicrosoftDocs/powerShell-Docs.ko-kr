---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-clixml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Clixml
ms.openlocfilehash: 8485591165cce0425c85d52fbd31d40614af6249
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214065"
---
# <span data-ttu-id="ab624-103">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="ab624-103">Export-Clixml</span></span>

## <span data-ttu-id="ab624-104">개요</span><span class="sxs-lookup"><span data-stu-id="ab624-104">SYNOPSIS</span></span>
<span data-ttu-id="ab624-105">개체의 XML 기반 표시를 만들고 이 표시를 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-105">Creates an XML-based representation of an object or objects and stores it in a file.</span></span>

## <span data-ttu-id="ab624-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ab624-106">SYNTAX</span></span>

### <span data-ttu-id="ab624-107">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="ab624-107">ByPath (Default)</span></span>

```
Export-Clixml [-Path] <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ab624-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="ab624-108">ByLiteralPath</span></span>

```
Export-Clixml -LiteralPath <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ab624-109">설명</span><span class="sxs-lookup"><span data-stu-id="ab624-109">DESCRIPTION</span></span>

<span data-ttu-id="ab624-110">`Export-Clixml`Cmdlet은 개체의 CLI (공용 언어 인프라) XML 기반 표현을 만들고이를 파일에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-110">The `Export-Clixml` cmdlet creates a Common Language Infrastructure (CLI) XML-based representation of an object or objects and stores it in a file.</span></span> <span data-ttu-id="ab624-111">그런 다음 cmdlet을 사용 `Import-Clixml` 하 여 해당 파일의 내용을 기반으로 저장 된 개체를 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-111">You can then use the `Import-Clixml` cmdlet to recreate the saved object based on the contents of that file.</span></span>
<span data-ttu-id="ab624-112">CLI에 대 한 자세한 내용은 [언어 독립성](/dotnet/standard/language-independence)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ab624-112">For more information about CLI, see [Language independence](/dotnet/standard/language-independence).</span></span>

<span data-ttu-id="ab624-113">이 cmdlet은 `ConvertTo-Xml` `Export-Clixml` 결과 XML을 파일에 저장 한다는 점을 제외 하 고와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-113">This cmdlet is similar to `ConvertTo-Xml`, except that `Export-Clixml` stores the resulting XML in a file.</span></span> <span data-ttu-id="ab624-114">`ConvertTo-XML` 는 XML을 반환 하므로 PowerShell에서 계속 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-114">`ConvertTo-XML` returns the XML, so you can continue to process it in PowerShell.</span></span>

<span data-ttu-id="ab624-115">Windows 컴퓨터에서의 중요 한 용도는 `Export-Clixml` 자격 증명과 보안 문자열을 XML로 안전 하 게 내보내는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-115">A valuable use of `Export-Clixml` on Windows computers is to export credentials and secure strings securely as XML.</span></span> <span data-ttu-id="ab624-116">예제를 보려면 예제 3을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ab624-116">For an example, see Example 3.</span></span>

## <span data-ttu-id="ab624-117">예제</span><span class="sxs-lookup"><span data-stu-id="ab624-117">EXAMPLES</span></span>

### <span data-ttu-id="ab624-118">예제 1: 문자열을 XML 파일로 내보내기</span><span class="sxs-lookup"><span data-stu-id="ab624-118">Example 1: Export a string to an XML file</span></span>

<span data-ttu-id="ab624-119">이 예제에서는 현재 디렉터리에를 저장 하는 XML 파일을 만듭니다. **이는 테스트** 의 문자열 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-119">This example creates an XML file that stores in the current directory, a representation of the string **This is a test** .</span></span>

```powershell
"This is a test" | Export-Clixml -Path .\sample.xml
```

<span data-ttu-id="ab624-120">이에 해당 하는 **테스트** 문자열은 파이프라인으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-120">The string **This is a test** is sent down the pipeline.</span></span> <span data-ttu-id="ab624-121">`Export-Clixml`**Path** 매개 변수를 사용 하 여 현재 디렉터리에 라는 XML 파일을 만듭니다 `sample.xml` .</span><span class="sxs-lookup"><span data-stu-id="ab624-121">`Export-Clixml` uses the **Path** parameter to create an XML file named `sample.xml` in the current directory.</span></span>

### <span data-ttu-id="ab624-122">예제 2: XML 파일로 개체 내보내기</span><span class="sxs-lookup"><span data-stu-id="ab624-122">Example 2: Export an object to an XML file</span></span>

<span data-ttu-id="ab624-123">이 예제에서는 개체를 XML 파일로 내보낸 다음 파일에서 XML을 가져와 개체를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-123">This example shows how to export an object to an XML file and then create an object by importing the XML from the file.</span></span>

```powershell
Get-Acl C:\test.txt | Export-Clixml -Path .\FileACL.xml
$fileacl = Import-Clixml -Path .\FileACL.xml
```

<span data-ttu-id="ab624-124">`Get-Acl`Cmdlet은 파일의 보안 설명자를 가져옵니다 `Test.txt` .</span><span class="sxs-lookup"><span data-stu-id="ab624-124">The `Get-Acl` cmdlet gets the security descriptor of the `Test.txt` file.</span></span> <span data-ttu-id="ab624-125">보안 설명자를 전달할 파이프라인에서 개체를 보냅니다 `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="ab624-125">It sends the object down the pipeline to pass the security descriptor to `Export-Clixml`.</span></span> <span data-ttu-id="ab624-126">개체의 XML 기반 표현은 이라는 파일에 저장 됩니다 `FileACL.xml` .</span><span class="sxs-lookup"><span data-stu-id="ab624-126">The XML-based representation of the object is stored in a file named `FileACL.xml`.</span></span>

<span data-ttu-id="ab624-127">`Import-Clixml`Cmdlet은 파일의 XML에서 개체를 만듭니다 `FileACL.xml` .</span><span class="sxs-lookup"><span data-stu-id="ab624-127">The `Import-Clixml` cmdlet creates an object from the XML in the `FileACL.xml` file.</span></span> <span data-ttu-id="ab624-128">그런 다음 개체를 `$fileacl` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-128">Then, it saves the object in the `$fileacl` variable.</span></span>

### <span data-ttu-id="ab624-129">예제 3: 내보낸 자격 증명 개체 암호화</span><span class="sxs-lookup"><span data-stu-id="ab624-129">Example 3: Encrypt an exported credential object</span></span>

<span data-ttu-id="ab624-130">이 예에서는 cmdlet을 실행 하 여 변수에 저장 한 자격 증명이 지정 된 경우 `$Credential` `Get-Credential` cmdlet을 실행 하 여 `Export-Clixml` 자격 증명을 디스크에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-130">In this example, given a credential that you've stored in the `$Credential` variable by running the `Get-Credential` cmdlet, you can run the `Export-Clixml` cmdlet to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ab624-131">`Export-Clixml` Windows에서 암호화 된 자격 증명만 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-131">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="ab624-132">MacOS 및 Linux와 같은 Windows 이외의 운영 체제에서는 자격 증명을 일반 텍스트로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-132">On non-Windows operating systems such as macOS and Linux, credentials are exported in plain text.</span></span>

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

<span data-ttu-id="ab624-133">`Export-Clixml`Cmdlet은 Windows [데이터 보호 API](/previous-versions/windows/apps/hh464970(v=win.10))를 사용 하 여 자격 증명 개체를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-133">The `Export-Clixml` cmdlet encrypts credential objects by using the Windows [Data Protection API](/previous-versions/windows/apps/hh464970(v=win.10)).</span></span>
<span data-ttu-id="ab624-134">암호화를 사용 하면 해당 컴퓨터의 사용자 계정만 자격 증명 개체의 콘텐츠를 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-134">The encryption ensures that only your user account on only that computer can decrypt the contents of the credential object.</span></span> <span data-ttu-id="ab624-135">내보낸 `CLIXML` 파일은 다른 컴퓨터 또는 다른 사용자가 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-135">The exported `CLIXML` file can't be used on a different computer or by a different user.</span></span>

<span data-ttu-id="ab624-136">이 예에서 자격 증명이 저장 된 파일은로 표시 됩니다 `TestScript.ps1.credential` .</span><span class="sxs-lookup"><span data-stu-id="ab624-136">In the example, the file in which the credential is stored is represented by `TestScript.ps1.credential`.</span></span> <span data-ttu-id="ab624-137">**Testscript** 를 자격 증명을 로드 하는 스크립트의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-137">Replace **TestScript** with the name of the script with which you're loading the credential.</span></span>

<span data-ttu-id="ab624-138">파이프라인의 자격 증명 개체를로 전송 하 `Export-Clixml` 고, `$Credxmlpath` 첫 번째 명령에서 지정한 경로에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-138">You send the credential object down the pipeline to `Export-Clixml`, and save it to the path, `$Credxmlpath`, that you specified in the first command.</span></span>

<span data-ttu-id="ab624-139">스크립트에 자격 증명을 자동으로 가져오려면 최종 두 개의 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-139">To import the credential automatically into your script, run the final two commands.</span></span> <span data-ttu-id="ab624-140">`Import-Clixml`을 실행 하 여 보안 자격 증명 개체를 스크립트로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-140">Run `Import-Clixml` to import the secured credential object into your script.</span></span> <span data-ttu-id="ab624-141">이 가져오기는 스크립트에서 일반 텍스트 암호를 노출 하는 위험을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-141">This import eliminates the risk of exposing plain-text passwords in your script.</span></span>

## <span data-ttu-id="ab624-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ab624-142">PARAMETERS</span></span>

### <span data-ttu-id="ab624-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ab624-143">-Confirm</span></span>

<span data-ttu-id="ab624-144">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-144">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ab624-145">-깊이</span><span class="sxs-lookup"><span data-stu-id="ab624-145">-Depth</span></span>

<span data-ttu-id="ab624-146">XML 표시에 포함되는 포함 개체 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-146">Specifies how many levels of contained objects are included in the XML representation.</span></span> <span data-ttu-id="ab624-147">기본값은 `2`입니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-147">The default value is `2`.</span></span>

<span data-ttu-id="ab624-148">파일의 개체 형식에 대 한 기본값을 재정의할 수 있습니다 `Types.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="ab624-148">The default value can be overridden for the object type in the `Types.ps1xml` files.</span></span> <span data-ttu-id="ab624-149">자세한 내용은 [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ab624-149">For more information, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ab624-150">-Encoding</span><span class="sxs-lookup"><span data-stu-id="ab624-150">-Encoding</span></span>

<span data-ttu-id="ab624-151">대상 파일의 인코딩 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-151">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="ab624-152">기본값은 **Unicode** 입니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-152">The default value is **Unicode** .</span></span>

<span data-ttu-id="ab624-153">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-153">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="ab624-154">`ASCII` ASCII (7 비트) 문자 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-154">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="ab624-155">`BigEndianUnicode` 에서는 u t f-16을 빅 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-155">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="ab624-156">`Default` 시스템의 활성 코드 페이지에 해당 하는 인코딩을 사용 합니다 (일반적으로 ANSI).</span><span class="sxs-lookup"><span data-stu-id="ab624-156">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="ab624-157">`OEM` 시스템의 현재 OEM 코드 페이지에 해당 하는 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-157">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="ab624-158">`Unicode` 는 u t f-16을 약간 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-158">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="ab624-159">`UTF7` 는 u t f-7을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-159">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="ab624-160">`UTF8` 는 u t f-8을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-160">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="ab624-161">`UTF32` 는 u t f-32을 작은 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-161">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Unicode
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ab624-162">-Force</span><span class="sxs-lookup"><span data-stu-id="ab624-162">-Force</span></span>

<span data-ttu-id="ab624-163">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-163">Forces the command to run without asking for user confirmation.</span></span>

<span data-ttu-id="ab624-164">필요한 경우 Cmdlet을 사용하여 출력 파일의 읽기 전용 특성을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-164">Causes the cmdlet to clear the read-only attribute of the output file if necessary.</span></span> <span data-ttu-id="ab624-165">명령이 완료되면 cmdlet이 읽기 전용 특성을 다시 설정하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-165">The cmdlet will attempt to reset the read-only attribute when the command completes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ab624-166">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ab624-166">-InputObject</span></span>

<span data-ttu-id="ab624-167">변환할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-167">Specifies the object to be converted.</span></span> <span data-ttu-id="ab624-168">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="ab624-168">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="ab624-169">개체를로 파이프 할 수도 있습니다 `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="ab624-169">You can also pipe objects to `Export-Clixml`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ab624-170">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ab624-170">-LiteralPath</span></span>

<span data-ttu-id="ab624-171">개체의 XML 표시를 저장할 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-171">Specifies the path to the file where the XML representation of the object will be stored.</span></span> <span data-ttu-id="ab624-172">**Path** 와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-172">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="ab624-173">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-173">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="ab624-174">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="ab624-174">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="ab624-175">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-175">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ab624-176">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="ab624-176">-NoClobber</span></span>

<span data-ttu-id="ab624-177">Cmdlet이 기존 파일의 내용을 덮어쓰지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-177">Indicates that the cmdlet doesn't overwrite the contents of an existing file.</span></span> <span data-ttu-id="ab624-178">기본적으로 지정 된 경로에 파일이 있으면는 `Export-Clixml` 경고 없이 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-178">By default, if a file exists in the specified path, `Export-Clixml` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ab624-179">-Path</span><span class="sxs-lookup"><span data-stu-id="ab624-179">-Path</span></span>

<span data-ttu-id="ab624-180">개체의 XML 표시를 저장할 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-180">Specifies the path to the file where the XML representation of the object will be stored.</span></span>

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

### <span data-ttu-id="ab624-181">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ab624-181">-WhatIf</span></span>

<span data-ttu-id="ab624-182">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-182">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ab624-183">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-183">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="ab624-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ab624-184">CommonParameters</span></span>

<span data-ttu-id="ab624-185">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ab624-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ab624-186">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab624-186">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ab624-187">입력</span><span class="sxs-lookup"><span data-stu-id="ab624-187">INPUTS</span></span>

### <span data-ttu-id="ab624-188">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="ab624-188">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="ab624-189">모든 개체를로 파이프라인 할 수 있습니다 `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="ab624-189">You can pipeline any object to `Export-Clixml`.</span></span>

## <span data-ttu-id="ab624-190">출력</span><span class="sxs-lookup"><span data-stu-id="ab624-190">OUTPUTS</span></span>

### <span data-ttu-id="ab624-191">System.object</span><span class="sxs-lookup"><span data-stu-id="ab624-191">System.IO.FileInfo</span></span>

<span data-ttu-id="ab624-192">`Export-Clixml` XML이 포함 된 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab624-192">`Export-Clixml` creates a file that contains the XML.</span></span>

## <span data-ttu-id="ab624-193">참고</span><span class="sxs-lookup"><span data-stu-id="ab624-193">NOTES</span></span>

## <span data-ttu-id="ab624-194">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ab624-194">RELATED LINKS</span></span>

[<span data-ttu-id="ab624-195">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="ab624-195">ConvertTo-Html</span></span>](ConvertTo-Html.md)

[<span data-ttu-id="ab624-196">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="ab624-196">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="ab624-197">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="ab624-197">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="ab624-198">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="ab624-198">Import-Clixml</span></span>](Import-Clixml.md)

[<span data-ttu-id="ab624-199">Join-Path</span><span class="sxs-lookup"><span data-stu-id="ab624-199">Join-Path</span></span>](../Microsoft.PowerShell.Management/Join-Path.md)

[<span data-ttu-id="ab624-200">디스크에 자격 증명을 안전 하 게 저장</span><span class="sxs-lookup"><span data-stu-id="ab624-200">Securely Store Credentials on Disk</span></span>](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[<span data-ttu-id="ab624-201">PowerShell을 사용 하 여 레거시 시스템에 자격 증명 전달</span><span class="sxs-lookup"><span data-stu-id="ab624-201">Use PowerShell to Pass Credentials to Legacy Systems</span></span>](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

[<span data-ttu-id="ab624-202">Windows.Security.Cryptography.DataProtection</span><span class="sxs-lookup"><span data-stu-id="ab624-202">Windows.Security.Cryptography.DataProtection</span></span>](/uwp/api/windows.security.cryptography.dataprotection)
