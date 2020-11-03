---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-clixml?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Clixml
ms.openlocfilehash: d33b74101301ec5806f456ddd9cc73bd8b6bb3e1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212977"
---
# <span data-ttu-id="0c263-103">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="0c263-103">Import-Clixml</span></span>

## <span data-ttu-id="0c263-104">개요</span><span class="sxs-lookup"><span data-stu-id="0c263-104">SYNOPSIS</span></span>
<span data-ttu-id="0c263-105">EXPORT-CLIXML 파일을 가져오고 PowerShell에서 해당 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-105">Imports a CLIXML file and creates corresponding objects in PowerShell.</span></span>

## <span data-ttu-id="0c263-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0c263-106">SYNTAX</span></span>

### <span data-ttu-id="0c263-107">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="0c263-107">ByPath (Default)</span></span>

```
Import-Clixml [-Path] <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

### <span data-ttu-id="0c263-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="0c263-108">ByLiteralPath</span></span>

```
Import-Clixml -LiteralPath <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

## <span data-ttu-id="0c263-109">설명</span><span class="sxs-lookup"><span data-stu-id="0c263-109">DESCRIPTION</span></span>

<span data-ttu-id="0c263-110">`Import-Clixml`Cmdlet은 Microsoft .NET Framework 개체를 나타내는 데이터가 포함 된 CLI (공용 언어 인프라) XML 파일을 가져오고 PowerShell 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-110">The `Import-Clixml` cmdlet imports a Common Language Infrastructure (CLI) XML file with data that represents Microsoft .NET Framework objects and creates the PowerShell objects.</span></span> <span data-ttu-id="0c263-111">CLI에 대 한 자세한 내용은 [언어 독립성](/dotnet/standard/language-independence)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0c263-111">For more information about CLI, see [Language independence](/dotnet/standard/language-independence).</span></span>

<span data-ttu-id="0c263-112">Windows 컴퓨터에서의 중요 한 용도는를 `Import-Clixml` 사용 하 여 보안 XML로 내보낸 자격 증명 및 보안 문자열을 가져오는 것입니다 `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="0c263-112">A valuable use of `Import-Clixml` on Windows computers is to import credentials and secure strings that were exported as secure XML using `Export-Clixml`.</span></span> <span data-ttu-id="0c263-113">예제는 예제 2를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0c263-113">For an example, see Example 2.</span></span>

<span data-ttu-id="0c263-114">`Import-Clixml` 는 BOM (바이트 순서 표시)을 사용 하 여 파일의 인코딩 형식을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-114">`Import-Clixml` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="0c263-115">파일에 BOM이 없으면 인코딩이 UTF8 이라고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-115">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="0c263-116">예제</span><span class="sxs-lookup"><span data-stu-id="0c263-116">EXAMPLES</span></span>

### <span data-ttu-id="0c263-117">예제 1: serialize 된 파일 가져오기 및 개체 다시 만들기</span><span class="sxs-lookup"><span data-stu-id="0c263-117">Example 1: Import a serialized file and recreate an object</span></span>

<span data-ttu-id="0c263-118">이 예에서는 cmdlet을 사용 하 `Export-Clixml` 여에서 반환 된 프로세스 정보의 직렬화 된 복사본을 저장 `Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-118">This example uses the `Export-Clixml` cmdlet to save a serialized copy of the process information returned by `Get-Process`.</span></span> <span data-ttu-id="0c263-119">`Import-Clixml` serialize 된 파일의 내용을 검색 하 고 변수에 저장 된 개체를 다시 만듭니다 `$Processes` .</span><span class="sxs-lookup"><span data-stu-id="0c263-119">`Import-Clixml` retrieves the serialized file's contents and recreates an object that is stored in the `$Processes` variable.</span></span>

```powershell
Get-Process | Export-Clixml -Path .\pi.xml
$Processes = Import-Clixml -Path .\pi.xml
```

### <span data-ttu-id="0c263-120">예제 2: 보안 자격 증명 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="0c263-120">Example 2: Import a secure credential object</span></span>

<span data-ttu-id="0c263-121">이 예에서는 cmdlet을 실행 하 여 변수에 저장 한 자격 증명이 지정 된 경우 `$Credential` `Get-Credential` cmdlet을 실행 하 여 `Export-Clixml` 자격 증명을 디스크에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-121">In this example, given a credential that you've stored in the `$Credential` variable by running the `Get-Credential` cmdlet, you can run the `Export-Clixml` cmdlet to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0c263-122">`Export-Clixml` Windows에서 암호화 된 자격 증명만 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-122">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="0c263-123">MacOS 및 Linux와 같은 Windows 이외의 운영 체제에서는 자격 증명을 일반 텍스트로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-123">On non-Windows operating systems such as macOS and Linux, credentials are exported in plain text.</span></span>

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

<span data-ttu-id="0c263-124">`Export-Clixml`Cmdlet은 Windows [데이터 보호 API](/previous-versions/windows/apps/hh464970(v=win.10))를 사용 하 여 자격 증명 개체를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-124">The `Export-Clixml` cmdlet encrypts credential objects by using the Windows [Data Protection API](/previous-versions/windows/apps/hh464970(v=win.10)).</span></span>
<span data-ttu-id="0c263-125">암호화를 사용 하면 사용자 계정만 자격 증명 개체의 콘텐츠를 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-125">The encryption ensures that only your user account can decrypt the contents of the credential object.</span></span> <span data-ttu-id="0c263-126">내보낸 `CLIXML` 파일은 다른 컴퓨터 또는 다른 사용자가 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-126">The exported `CLIXML` file can't be used on a different computer or by a different user.</span></span>

<span data-ttu-id="0c263-127">이 예에서 자격 증명이 저장 된 파일은로 표시 됩니다 `TestScript.ps1.credential` .</span><span class="sxs-lookup"><span data-stu-id="0c263-127">In the example, the file in which the credential is stored is represented by `TestScript.ps1.credential`.</span></span> <span data-ttu-id="0c263-128">**Testscript** 를 자격 증명을 로드 하는 스크립트의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-128">Replace **TestScript** with the name of the script with which you're loading the credential.</span></span>

<span data-ttu-id="0c263-129">파이프라인의 자격 증명 개체를로 전송 하 `Export-Clixml` 고, `$Credxmlpath` 첫 번째 명령에서 지정한 경로에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-129">You send the credential object down the pipeline to `Export-Clixml`, and save it to the path, `$Credxmlpath`, that you specified in the first command.</span></span>

<span data-ttu-id="0c263-130">스크립트에 자격 증명을 자동으로 가져오려면 최종 두 개의 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-130">To import the credential automatically into your script, run the final two commands.</span></span> <span data-ttu-id="0c263-131">`Import-Clixml`을 실행 하 여 보안 자격 증명 개체를 스크립트로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-131">Run `Import-Clixml` to import the secured credential object into your script.</span></span> <span data-ttu-id="0c263-132">이 가져오기는 스크립트에서 일반 텍스트 암호를 노출 하는 위험을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-132">This import eliminates the risk of exposing plain-text passwords in your script.</span></span>

## <span data-ttu-id="0c263-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0c263-133">PARAMETERS</span></span>

### <span data-ttu-id="0c263-134">-첫 번째</span><span class="sxs-lookup"><span data-stu-id="0c263-134">-First</span></span>

<span data-ttu-id="0c263-135">지정된 수의 개체만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-135">Gets only the specified number of objects.</span></span> <span data-ttu-id="0c263-136">가져올 개체 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-136">Enter the number of objects to get.</span></span>

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0c263-137">-IncludeTotalCount</span><span class="sxs-lookup"><span data-stu-id="0c263-137">-IncludeTotalCount</span></span>

<span data-ttu-id="0c263-138">선택한 개체 다음에 오는 데이터 집합의 총 개체 수를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-138">Reports the total number of objects in the data set followed by the selected objects.</span></span> <span data-ttu-id="0c263-139">Cmdlet이 총 개수를 확인할 수 없는 경우에는 **알 수 없는 총 개수** 를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-139">If the cmdlet can't determine the total count, it displays **Unknown total count** .</span></span> <span data-ttu-id="0c263-140">정수에는 총 개수 값의 안정성을 나타내는 **정확도** 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-140">The integer has an **Accuracy** property that indicates the reliability of the total count value.</span></span> <span data-ttu-id="0c263-141">**정확도** 범위 값은에서 `0.0` 로 지정 됩니다 `1.0` . 여기서은 `0.0` cmdlet이 개체를 계산할 수 없음을 의미 하 고,는 `1.0` 개수가 정확 함을 의미 하며,와 사이의 값은 점점 더 `0.0` `1.0` 안정적인 추정치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-141">The value of **Accuracy** ranges from `0.0` to `1.0` where `0.0` means that the cmdlet couldn't count the objects, `1.0` means that the count is exact, and a value between `0.0` and `1.0` indicates an increasingly reliable estimate.</span></span>

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

### <span data-ttu-id="0c263-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0c263-142">-LiteralPath</span></span>

<span data-ttu-id="0c263-143">XML 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-143">Specifies the path to the XML files.</span></span> <span data-ttu-id="0c263-144">**Path** 와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-144">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="0c263-145">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="0c263-146">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="0c263-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="0c263-147">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0c263-148">-Path</span><span class="sxs-lookup"><span data-stu-id="0c263-148">-Path</span></span>

<span data-ttu-id="0c263-149">XML 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-149">Specifies the path to the XML files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0c263-150">-Skip</span><span class="sxs-lookup"><span data-stu-id="0c263-150">-Skip</span></span>

<span data-ttu-id="0c263-151">지정된 개체 수를 무시하고 남은 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-151">Ignores the specified number of objects and then gets the remaining objects.</span></span> <span data-ttu-id="0c263-152">건너뛸 개체 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-152">Enter the number of objects to skip.</span></span>

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0c263-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0c263-153">CommonParameters</span></span>

<span data-ttu-id="0c263-154">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0c263-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0c263-155">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0c263-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0c263-156">입력</span><span class="sxs-lookup"><span data-stu-id="0c263-156">INPUTS</span></span>

### <span data-ttu-id="0c263-157">System.String</span><span class="sxs-lookup"><span data-stu-id="0c263-157">System.String</span></span>

<span data-ttu-id="0c263-158">에 대 한 경로를 포함 하는 문자열을 파이프라인으로 만들 수 있습니다 `Import-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="0c263-158">You can pipeline a string that contains a path to `Import-Clixml`.</span></span>

## <span data-ttu-id="0c263-159">출력</span><span class="sxs-lookup"><span data-stu-id="0c263-159">OUTPUTS</span></span>

### <span data-ttu-id="0c263-160">PSObject</span><span class="sxs-lookup"><span data-stu-id="0c263-160">PSObject</span></span>

<span data-ttu-id="0c263-161">`Import-Clixml` 저장 된 XML 파일에서 deserialize 된 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-161">`Import-Clixml` returns objects that were deserialized from the stored XML files.</span></span>

## <span data-ttu-id="0c263-162">참고</span><span class="sxs-lookup"><span data-stu-id="0c263-162">NOTES</span></span>

<span data-ttu-id="0c263-163">매개 변수에 여러 값을 지정할 때는 쉼표를 사용하여 값을 구분하세요.</span><span class="sxs-lookup"><span data-stu-id="0c263-163">When specifying multiple values for a parameter, use commas to separate the values.</span></span> <span data-ttu-id="0c263-164">예들 들어 `<parameter-name> <value1>, <value2>`입니다.</span><span class="sxs-lookup"><span data-stu-id="0c263-164">For example, `<parameter-name> <value1>, <value2>`.</span></span>

## <span data-ttu-id="0c263-165">관련 링크</span><span class="sxs-lookup"><span data-stu-id="0c263-165">RELATED LINKS</span></span>

[<span data-ttu-id="0c263-166">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="0c263-166">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="0c263-167">XML serialization 소개</span><span class="sxs-lookup"><span data-stu-id="0c263-167">Introducing XML Serialization</span></span>](/dotnet/standard/serialization/introducing-xml-serialization)

[<span data-ttu-id="0c263-168">Join-Path</span><span class="sxs-lookup"><span data-stu-id="0c263-168">Join-Path</span></span>](../Microsoft.PowerShell.Management/Join-Path.md)

[<span data-ttu-id="0c263-169">디스크에 자격 증명을 안전 하 게 저장</span><span class="sxs-lookup"><span data-stu-id="0c263-169">Securely Store Credentials on Disk</span></span>](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[<span data-ttu-id="0c263-170">PowerShell을 사용 하 여 레거시 시스템에 자격 증명 전달</span><span class="sxs-lookup"><span data-stu-id="0c263-170">Use PowerShell to Pass Credentials to Legacy Systems</span></span>](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

