---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-clixml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Clixml
ms.openlocfilehash: 7a0c25197ba00fb05089f855592e7744ef10e9b9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600134"
---
# <span data-ttu-id="84aee-102">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="84aee-102">Export-Clixml</span></span>

## <span data-ttu-id="84aee-103">개요</span><span class="sxs-lookup"><span data-stu-id="84aee-103">SYNOPSIS</span></span>
<span data-ttu-id="84aee-104">개체의 XML 기반 표시를 만들고 이 표시를 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-104">Creates an XML-based representation of an object or objects and stores it in a file.</span></span>

## <span data-ttu-id="84aee-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="84aee-105">SYNTAX</span></span>

### <span data-ttu-id="84aee-106">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="84aee-106">ByPath (Default)</span></span>

```
Export-Clixml [-Depth <Int32>] [-Path] <String> -InputObject <PSObject> [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="84aee-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="84aee-107">ByLiteralPath</span></span>

```
Export-Clixml [-Depth <Int32>] -LiteralPath <String> -InputObject <PSObject> [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="84aee-108">설명</span><span class="sxs-lookup"><span data-stu-id="84aee-108">DESCRIPTION</span></span>

<span data-ttu-id="84aee-109">`Export-Clixml`Cmdlet은 개체의 CLI (공용 언어 인프라) XML 기반 표현을 만들고이를 파일에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-109">The `Export-Clixml` cmdlet creates a Common Language Infrastructure (CLI) XML-based representation of an object or objects and stores it in a file.</span></span> <span data-ttu-id="84aee-110">그런 다음 cmdlet을 사용 `Import-Clixml` 하 여 해당 파일의 내용을 기반으로 저장 된 개체를 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-110">You can then use the `Import-Clixml` cmdlet to recreate the saved object based on the contents of that file.</span></span>
<span data-ttu-id="84aee-111">CLI에 대 한 자세한 내용은 [언어 독립성](/dotnet/standard/language-independence)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="84aee-111">For more information about CLI, see [Language independence](/dotnet/standard/language-independence).</span></span>

<span data-ttu-id="84aee-112">이 cmdlet은 `ConvertTo-Xml` `Export-Clixml` 결과 XML을 파일에 저장 한다는 점을 제외 하 고와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-112">This cmdlet is similar to `ConvertTo-Xml`, except that `Export-Clixml` stores the resulting XML in a file.</span></span> <span data-ttu-id="84aee-113">`ConvertTo-XML` 는 XML을 반환 하므로 PowerShell에서 계속 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-113">`ConvertTo-XML` returns the XML, so you can continue to process it in PowerShell.</span></span>

<span data-ttu-id="84aee-114">Windows 컴퓨터에서의 중요 한 용도는 `Export-Clixml` 자격 증명과 보안 문자열을 XML로 안전 하 게 내보내는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-114">A valuable use of `Export-Clixml` on Windows computers is to export credentials and secure strings securely as XML.</span></span> <span data-ttu-id="84aee-115">예제를 보려면 예제 3을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="84aee-115">For an example, see Example 3.</span></span>

## <span data-ttu-id="84aee-116">예제</span><span class="sxs-lookup"><span data-stu-id="84aee-116">EXAMPLES</span></span>

### <span data-ttu-id="84aee-117">예제 1: 문자열을 XML 파일로 내보내기</span><span class="sxs-lookup"><span data-stu-id="84aee-117">Example 1: Export a string to an XML file</span></span>

<span data-ttu-id="84aee-118">이 예제에서는 현재 디렉터리에를 저장 하는 XML 파일을 만듭니다. **이는 테스트** 의 문자열 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-118">This example creates an XML file that stores in the current directory, a representation of the string **This is a test**.</span></span>

```powershell
"This is a test" | Export-Clixml -Path .\sample.xml
```

<span data-ttu-id="84aee-119">문자열이 `This is a test` 파이프라인으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-119">The string `This is a test` is sent down the pipeline.</span></span> <span data-ttu-id="84aee-120">`Export-Clixml`**Path** 매개 변수를 사용 하 여 현재 디렉터리에 라는 XML 파일을 만듭니다 `sample.xml` .</span><span class="sxs-lookup"><span data-stu-id="84aee-120">`Export-Clixml` uses the **Path** parameter to create an XML file named `sample.xml` in the current directory.</span></span>

### <span data-ttu-id="84aee-121">예제 2: XML 파일로 개체 내보내기</span><span class="sxs-lookup"><span data-stu-id="84aee-121">Example 2: Export an object to an XML file</span></span>

<span data-ttu-id="84aee-122">이 예제에서는 개체를 XML 파일로 내보낸 다음 파일에서 XML을 가져와 개체를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-122">This example shows how to export an object to an XML file and then create an object by importing the XML from the file.</span></span>

```powershell
Get-Acl C:\test.txt | Export-Clixml -Path .\FileACL.xml
$fileacl = Import-Clixml -Path .\FileACL.xml
```

<span data-ttu-id="84aee-123">`Get-Acl`Cmdlet은 파일의 보안 설명자를 가져옵니다 `Test.txt` .</span><span class="sxs-lookup"><span data-stu-id="84aee-123">The `Get-Acl` cmdlet gets the security descriptor of the `Test.txt` file.</span></span> <span data-ttu-id="84aee-124">보안 설명자를 전달할 파이프라인에서 개체를 보냅니다 `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="84aee-124">It sends the object down the pipeline to pass the security descriptor to `Export-Clixml`.</span></span> <span data-ttu-id="84aee-125">개체의 XML 기반 표현은 이라는 파일에 저장 됩니다 `FileACL.xml` .</span><span class="sxs-lookup"><span data-stu-id="84aee-125">The XML-based representation of the object is stored in a file named `FileACL.xml`.</span></span>

<span data-ttu-id="84aee-126">`Import-Clixml`Cmdlet은 파일의 XML에서 개체를 만듭니다 `FileACL.xml` .</span><span class="sxs-lookup"><span data-stu-id="84aee-126">The `Import-Clixml` cmdlet creates an object from the XML in the `FileACL.xml` file.</span></span> <span data-ttu-id="84aee-127">그런 다음 개체를 `$fileacl` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-127">Then, it saves the object in the `$fileacl` variable.</span></span>

### <span data-ttu-id="84aee-128">예제 3: Windows에서 내보낸 자격 증명 개체 암호화</span><span class="sxs-lookup"><span data-stu-id="84aee-128">Example 3: Encrypt an exported credential object on Windows</span></span>

<span data-ttu-id="84aee-129">이 예에서는 cmdlet을 실행 하 여 변수에 저장 한 자격 증명이 지정 된 경우 `$Credential` `Get-Credential` cmdlet을 실행 하 여 `Export-Clixml` 자격 증명을 디스크에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-129">In this example, given a credential that you've stored in the `$Credential` variable by running the `Get-Credential` cmdlet, you can run the `Export-Clixml` cmdlet to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84aee-130">`Export-Clixml` Windows에서 암호화 된 자격 증명만 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-130">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="84aee-131">MacOS 및 Linux와 같은 Windows 이외의 운영 체제에서는 자격 증명을 유니코드 문자 배열로 저장 된 일반 텍스트로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-131">On non-Windows operating systems such as macOS and Linux, credentials are exported as a plain text stored as a Unicode character array.</span></span> <span data-ttu-id="84aee-132">이는 일부 난독 처리를 제공 하지만 암호화를 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-132">This provides some obfuscation but does not provide encryption.</span></span>

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

<span data-ttu-id="84aee-133">`Export-Clixml`Cmdlet은 Windows [데이터 보호 API](/previous-versions/windows/apps/hh464970(v=win.10))를 사용 하 여 자격 증명 개체를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-133">The `Export-Clixml` cmdlet encrypts credential objects by using the Windows [Data Protection API](/previous-versions/windows/apps/hh464970(v=win.10)).</span></span> <span data-ttu-id="84aee-134">암호화를 사용 하면 해당 컴퓨터의 사용자 계정만 자격 증명 개체의 콘텐츠를 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-134">The encryption ensures that only your user account on only that computer can decrypt the contents of the credential object.</span></span>
<span data-ttu-id="84aee-135">내보낸 `CLIXML` 파일은 다른 컴퓨터 또는 다른 사용자가 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-135">The exported `CLIXML` file can't be used on a different computer or by a different user.</span></span>

<span data-ttu-id="84aee-136">이 예에서 자격 증명이 저장 된 파일은로 표시 됩니다 `TestScript.ps1.credential` .</span><span class="sxs-lookup"><span data-stu-id="84aee-136">In the example, the file in which the credential is stored is represented by `TestScript.ps1.credential`.</span></span> <span data-ttu-id="84aee-137">**Testscript** 를 자격 증명을 로드 하는 스크립트의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-137">Replace **TestScript** with the name of the script with which you're loading the credential.</span></span>

<span data-ttu-id="84aee-138">파이프라인의 자격 증명 개체를로 전송 하 `Export-Clixml` 고, `$Credxmlpath` 첫 번째 명령에서 지정한 경로에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-138">You send the credential object down the pipeline to `Export-Clixml`, and save it to the path, `$Credxmlpath`, that you specified in the first command.</span></span>

<span data-ttu-id="84aee-139">스크립트에 자격 증명을 자동으로 가져오려면 최종 두 개의 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-139">To import the credential automatically into your script, run the final two commands.</span></span> <span data-ttu-id="84aee-140">`Import-Clixml`을 실행 하 여 보안 자격 증명 개체를 스크립트로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-140">Run `Import-Clixml` to import the secured credential object into your script.</span></span> <span data-ttu-id="84aee-141">이 가져오기는 스크립트에서 일반 텍스트 암호를 노출 하는 위험을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-141">This import eliminates the risk of exposing plain-text passwords in your script.</span></span>

### <span data-ttu-id="84aee-142">예제 4: Linux 또는 macOS에서 자격 증명 개체 내보내기</span><span class="sxs-lookup"><span data-stu-id="84aee-142">Example 4: Exporting a credential object on Linux or macOS</span></span>

<span data-ttu-id="84aee-143">이 예제에서는 cmdlet을 사용 하 여 변수에 **PSCredential** 을 만듭니다 `$Credential` `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="84aee-143">In this example, we create a **PSCredential** in the `$Credential` variable using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="84aee-144">그런 다음 `Export-Clixml` 를 사용 하 여 디스크에 자격 증명을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-144">Then we use `Export-Clixml` to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84aee-145">`Export-Clixml` Windows에서 암호화 된 자격 증명만 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-145">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="84aee-146">MacOS 및 Linux와 같은 Windows 이외의 운영 체제에서는 자격 증명을 유니코드 문자 배열로 저장 된 일반 텍스트로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-146">On non-Windows operating systems such as macOS and Linux, credentials are exported as a plain text stored as a Unicode character array.</span></span> <span data-ttu-id="84aee-147">이는 일부 난독 처리를 제공 하지만 암호화를 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-147">This provides some obfuscation but does not provide encryption.</span></span>

```powershell
PS> $Credential = Get-Credential

PowerShell credential request
Enter your credentials.
User: User1
Password for user User1: ********

PS> $Credential | Export-Clixml ./cred2.xml
PS> Get-Content ./cred2.xml

...
    <Props>
      <S N="UserName">User1</S>
      <SS N="Password">700061007300730077006f0072006400</SS>
    </Props>
...

PS> 'password' | Format-Hex -Encoding unicode

   Label: String (System.String) <52D60C91>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 70 00 61 00 73 00 73 00 77 00 6F 00 72 00 64 00 p a s s w o r d
```

<span data-ttu-id="84aee-148">`Get-Content`이 예제의 출력은 XML 파일의 자격 증명 정보에 초점을 맞추기 위해 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-148">The output of `Get-Content` in this example has been truncate to focus on the credential information in the XML file.</span></span> <span data-ttu-id="84aee-149">암호의 일반 텍스트 값은에 의해 검증 된 대로 XML 파일에 유니코드 문자 배열로 저장 됩니다 `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="84aee-149">Note that the plain text value of the password is stored in the XML file as a Unicode character array as proven by `Format-Hex`.</span></span> <span data-ttu-id="84aee-150">따라서 값은 인코딩되어 암호화 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-150">So the value is encoded but not encrypted.</span></span>

## <span data-ttu-id="84aee-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="84aee-151">PARAMETERS</span></span>

### <span data-ttu-id="84aee-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="84aee-152">-Confirm</span></span>

<span data-ttu-id="84aee-153">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="84aee-154">-깊이</span><span class="sxs-lookup"><span data-stu-id="84aee-154">-Depth</span></span>

<span data-ttu-id="84aee-155">XML 표시에 포함되는 포함 개체 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-155">Specifies how many levels of contained objects are included in the XML representation.</span></span> <span data-ttu-id="84aee-156">기본값은 `2`입니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-156">The default value is `2`.</span></span>

<span data-ttu-id="84aee-157">파일의 개체 형식에 대 한 기본값을 재정의할 수 있습니다 `Types.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="84aee-157">The default value can be overridden for the object type in the `Types.ps1xml` files.</span></span> <span data-ttu-id="84aee-158">자세한 내용은 [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="84aee-158">For more information, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span>

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

### <span data-ttu-id="84aee-159">-Encoding</span><span class="sxs-lookup"><span data-stu-id="84aee-159">-Encoding</span></span>

<span data-ttu-id="84aee-160">대상 파일의 인코딩 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-160">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="84aee-161">기본값은 `utf8NoBOM`입니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-161">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="84aee-162">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-162">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="84aee-163">`ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-163">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="84aee-164">`bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-164">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="84aee-165">`bigendianutf32`: 빅 endian 바이트 순서를 사용 하 여 u t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-165">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="84aee-166">`oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-166">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="84aee-167">`unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-167">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="84aee-168">`utf7`: UTF-7 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-168">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="84aee-169">`utf8`: UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-169">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="84aee-170">`utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-170">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="84aee-171">`utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-171">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="84aee-172">`utf32`: U t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-172">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="84aee-173">PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="84aee-173">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="84aee-174">자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="84aee-174">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="84aee-175">**U t f-7** _은 더 이상 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-175">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="84aee-176">PowerShell 7.1에서는 `utf7` _ *Encoding*\* 매개 변수에 대해를 지정 하는 경우 경고가 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-176">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="84aee-177">-Force</span><span class="sxs-lookup"><span data-stu-id="84aee-177">-Force</span></span>

<span data-ttu-id="84aee-178">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-178">Forces the command to run without asking for user confirmation.</span></span>

<span data-ttu-id="84aee-179">필요한 경우 Cmdlet을 사용하여 출력 파일의 읽기 전용 특성을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-179">Causes the cmdlet to clear the read-only attribute of the output file if necessary.</span></span> <span data-ttu-id="84aee-180">명령이 완료되면 cmdlet이 읽기 전용 특성을 다시 설정하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-180">The cmdlet will attempt to reset the read-only attribute when the command completes.</span></span>

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

### <span data-ttu-id="84aee-181">-InputObject</span><span class="sxs-lookup"><span data-stu-id="84aee-181">-InputObject</span></span>

<span data-ttu-id="84aee-182">변환할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-182">Specifies the object to be converted.</span></span> <span data-ttu-id="84aee-183">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="84aee-183">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="84aee-184">개체를로 파이프 할 수도 있습니다 `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="84aee-184">You can also pipe objects to `Export-Clixml`.</span></span>

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

### <span data-ttu-id="84aee-185">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="84aee-185">-LiteralPath</span></span>

<span data-ttu-id="84aee-186">개체의 XML 표시를 저장할 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-186">Specifies the path to the file where the XML representation of the object will be stored.</span></span> <span data-ttu-id="84aee-187">**Path** 와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-187">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="84aee-188">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-188">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="84aee-189">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="84aee-189">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="84aee-190">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-190">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="84aee-191">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="84aee-191">-NoClobber</span></span>

<span data-ttu-id="84aee-192">Cmdlet이 기존 파일의 내용을 덮어쓰지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-192">Indicates that the cmdlet doesn't overwrite the contents of an existing file.</span></span> <span data-ttu-id="84aee-193">기본적으로 지정 된 경로에 파일이 있으면는 `Export-Clixml` 경고 없이 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-193">By default, if a file exists in the specified path, `Export-Clixml` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="84aee-194">-Path</span><span class="sxs-lookup"><span data-stu-id="84aee-194">-Path</span></span>

<span data-ttu-id="84aee-195">개체의 XML 표시를 저장할 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-195">Specifies the path to the file where the XML representation of the object will be stored.</span></span>

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

### <span data-ttu-id="84aee-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="84aee-196">-WhatIf</span></span>

<span data-ttu-id="84aee-197">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-197">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="84aee-198">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-198">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="84aee-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="84aee-199">CommonParameters</span></span>

<span data-ttu-id="84aee-200">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="84aee-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="84aee-201">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="84aee-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="84aee-202">입력</span><span class="sxs-lookup"><span data-stu-id="84aee-202">INPUTS</span></span>

### <span data-ttu-id="84aee-203">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="84aee-203">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="84aee-204">모든 개체를로 파이프라인 할 수 있습니다 `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="84aee-204">You can pipeline any object to `Export-Clixml`.</span></span>

## <span data-ttu-id="84aee-205">출력</span><span class="sxs-lookup"><span data-stu-id="84aee-205">OUTPUTS</span></span>

### <span data-ttu-id="84aee-206">System.object</span><span class="sxs-lookup"><span data-stu-id="84aee-206">System.IO.FileInfo</span></span>

<span data-ttu-id="84aee-207">`Export-Clixml` XML이 포함 된 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="84aee-207">`Export-Clixml` creates a file that contains the XML.</span></span>

## <span data-ttu-id="84aee-208">참고</span><span class="sxs-lookup"><span data-stu-id="84aee-208">NOTES</span></span>

## <span data-ttu-id="84aee-209">관련 링크</span><span class="sxs-lookup"><span data-stu-id="84aee-209">RELATED LINKS</span></span>

[<span data-ttu-id="84aee-210">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="84aee-210">ConvertTo-Html</span></span>](ConvertTo-Html.md)

[<span data-ttu-id="84aee-211">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="84aee-211">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="84aee-212">내보내기-Csv</span><span class="sxs-lookup"><span data-stu-id="84aee-212">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="84aee-213">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="84aee-213">Import-Clixml</span></span>](Import-Clixml.md)

[<span data-ttu-id="84aee-214">Join-Path</span><span class="sxs-lookup"><span data-stu-id="84aee-214">Join-Path</span></span>](../Microsoft.PowerShell.Management/Join-Path.md)

[<span data-ttu-id="84aee-215">디스크에 자격 증명을 안전 하 게 저장</span><span class="sxs-lookup"><span data-stu-id="84aee-215">Securely Store Credentials on Disk</span></span>](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[<span data-ttu-id="84aee-216">PowerShell을 사용 하 여 레거시 시스템에 자격 증명 전달</span><span class="sxs-lookup"><span data-stu-id="84aee-216">Use PowerShell to Pass Credentials to Legacy Systems</span></span>](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

[<span data-ttu-id="84aee-217">Windows.Security.Cryptography.DataProtection</span><span class="sxs-lookup"><span data-stu-id="84aee-217">Windows.Security.Cryptography.DataProtection</span></span>](/uwp/api/windows.security.cryptography.dataprotection)
