---
title: about_Character_Encoding
description: PowerShell에서 문자열 데이터의 입력 및 출력에 문자 인코딩을 사용 하는 방법을 설명 합니다.
ms.date: 10/21/2020
Locale: en-US
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_character_encoding?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
ms.openlocfilehash: 6e2f515f774d7bc333baf6346cd6c8bd517cb6fa
ms.sourcegitcommit: df80c558e9a4b89c9798f084bd04012ece15155c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2020
ms.locfileid: "93225153"
---
# <a name="about_character_encoding"></a><span data-ttu-id="cf586-103">about_Character_Encoding</span><span class="sxs-lookup"><span data-stu-id="cf586-103">about_Character_Encoding</span></span>

## <a name="short-description"></a><span data-ttu-id="cf586-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="cf586-104">Short description</span></span>
<span data-ttu-id="cf586-105">PowerShell에서 문자열 데이터의 입력 및 출력에 문자 인코딩을 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-105">Describes how PowerShell uses character encoding for input and output of string data.</span></span>

## <a name="long-description"></a><span data-ttu-id="cf586-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-106">Long description</span></span>

<span data-ttu-id="cf586-107">유니코드는 전 세계 문자 인코딩 표준입니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-107">Unicode is a worldwide character-encoding standard.</span></span> <span data-ttu-id="cf586-108">시스템에서는 문자 및 문자열 조작을 위해 유니코드를 독점적으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-108">The system uses Unicode exclusively for character and string manipulation.</span></span> <span data-ttu-id="cf586-109">유니코드의 모든 측면에 대 한 자세한 내용은 [Unicode Standard](https://www.unicode.org/standard/standard.html)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cf586-109">For a detailed description of all aspects of Unicode, refer to [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>

<span data-ttu-id="cf586-110">Windows는 유니코드 및 기존 문자 집합을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-110">Windows supports Unicode and traditional character sets.</span></span> <span data-ttu-id="cf586-111">Windows 코드 페이지와 같은 기존 문자 집합은 8 비트 값 또는 8 비트 값의 조합을 사용 하 여 특정 언어 또는 지리적 지역 설정에서 사용 되는 문자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-111">Traditional character sets, such as Windows code pages, use 8-bit values or combinations of 8-bit values to represent the characters used in a specific language or geographical region settings.</span></span>

<span data-ttu-id="cf586-112">PowerShell은 기본적으로 유니코드 문자 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-112">PowerShell uses a Unicode character set by default.</span></span> <span data-ttu-id="cf586-113">그러나 여러 cmdlet에는 다른 문자 집합에 대 한 인코딩을 지정할 수 있는 **인코딩** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-113">However, several cmdlets have an **Encoding** parameter that can specify encoding for a different character set.</span></span> <span data-ttu-id="cf586-114">이 매개 변수를 사용 하 여 다른 시스템 및 응용 프로그램과의 상호 운용성을 위해 필요한 특정 문자 인코딩을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-114">This parameter allows you to choose the specific the character encoding you need for interoperability with other systems and applications.</span></span>

<span data-ttu-id="cf586-115">다음 cmdlet에는 **Encoding** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-115">The following cmdlets have the **Encoding** parameter:</span></span>

- <span data-ttu-id="cf586-116">Microsoft.PowerShell.Management</span><span class="sxs-lookup"><span data-stu-id="cf586-116">Microsoft.PowerShell.Management</span></span>
  - <span data-ttu-id="cf586-117">Add-Content</span><span class="sxs-lookup"><span data-stu-id="cf586-117">Add-Content</span></span>
  - <span data-ttu-id="cf586-118">Get-Content</span><span class="sxs-lookup"><span data-stu-id="cf586-118">Get-Content</span></span>
  - <span data-ttu-id="cf586-119">Set-Content</span><span class="sxs-lookup"><span data-stu-id="cf586-119">Set-Content</span></span>
- <span data-ttu-id="cf586-120">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="cf586-120">Microsoft.PowerShell.Utility</span></span>
  - <span data-ttu-id="cf586-121">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="cf586-121">Export-Clixml</span></span>
  - <span data-ttu-id="cf586-122">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="cf586-122">Export-Csv</span></span>
  - <span data-ttu-id="cf586-123">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="cf586-123">Export-PSSession</span></span>
  - <span data-ttu-id="cf586-124">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="cf586-124">Format-Hex</span></span>
  - <span data-ttu-id="cf586-125">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="cf586-125">Import-Csv</span></span>
  - <span data-ttu-id="cf586-126">Out-File</span><span class="sxs-lookup"><span data-stu-id="cf586-126">Out-File</span></span>
  - <span data-ttu-id="cf586-127">Select-String</span><span class="sxs-lookup"><span data-stu-id="cf586-127">Select-String</span></span>
  - <span data-ttu-id="cf586-128">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="cf586-128">Send-MailMessage</span></span>

## <a name="the-byte-order-mark"></a><span data-ttu-id="cf586-129">바이트 순서 표시입니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-129">The byte-order-mark</span></span>

<span data-ttu-id="cf586-130">BOM (바이트 순서 표시)은 파일 또는 텍스트 스트림의 처음 몇 바이트에 있는 _유니코드 서명_ 으로, 데이터에 사용 되는 유니코드 인코딩을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-130">The byte-order-mark (BOM) is a _Unicode signature_ in the first few bytes of a file or text stream that indicate which Unicode encoding used for the data.</span></span> <span data-ttu-id="cf586-131">자세한 내용은 위키백과에서 [바이트 순서 표시](https://wikipedia.org/wiki/Byte_order_mark) 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cf586-131">For more information, see the [Byte order mark](https://wikipedia.org/wiki/Byte_order_mark) article in Wikipedia.</span></span>

<span data-ttu-id="cf586-132">Windows PowerShell에서를 제외한 모든 유니코드 인코딩은 `UTF7` 항상 BOM을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-132">In Windows PowerShell, any Unicode encoding, except `UTF7`, always creates a BOM.</span></span> <span data-ttu-id="cf586-133">PowerShell Core는 기본적으로 `utf8NoBOM` 모든 텍스트 출력에 대해로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-133">PowerShell Core defaults to `utf8NoBOM` for all text output.</span></span>

<span data-ttu-id="cf586-134">최상의 전반적인 호환성을 위해 u t f-8 파일에 Bom을 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="cf586-134">For best overall compatibility, avoid using BOMs in UTF-8 files.</span></span> <span data-ttu-id="cf586-135">Windows 플랫폼에도 사용 되는 unix 플랫폼 및 Unix heritage 유틸리티는 Bom을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-135">Unix platforms and Unix-heritage utilities also used on Windows Platforms don't support BOMs.</span></span>

<span data-ttu-id="cf586-136">마찬가지로 `UTF7` encoding을 피해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-136">Similarly, `UTF7` encoding should be avoided.</span></span> <span data-ttu-id="cf586-137">U t f-7은 표준 유니코드 인코딩이 아니므로 모든 버전의 PowerShell에서 BOM 없이 작성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-137">UTF-7 is not a standard Unicode encoding and is written without a BOM in all versions of PowerShell.</span></span>

<span data-ttu-id="cf586-138">Unix와 같은 플랫폼에서 PowerShell 스크립트를 만들거나 Visual Studio Code와 같이 Windows에서 플랫폼 간 편집기를 사용 하 여 파일을로 인코딩합니다 `UTF8NoBOM` .</span><span class="sxs-lookup"><span data-stu-id="cf586-138">Creating PowerShell scripts on a Unix-like platform or using a cross-platform editor on Windows, such as Visual Studio Code, results in a file encoded using `UTF8NoBOM`.</span></span> <span data-ttu-id="cf586-139">이러한 파일은 PowerShell Core에서 잘 작동 하지만 파일에 비 Ascii 문자가 포함 된 경우 Windows PowerShell에서 중단 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-139">These files work fine on PowerShell Core, but may break in Windows PowerShell if the file contains non-Ascii characters.</span></span>

<span data-ttu-id="cf586-140">스크립트에서 Ascii가 아닌 문자를 사용 해야 하는 경우 BOM을 사용 하 여 u t f-8로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-140">If you need to use non-Ascii characters in your scripts, save them as UTF-8 with BOM.</span></span> <span data-ttu-id="cf586-141">BOM이 없으면 Windows PowerShell에서 스크립트를 레거시 "ANSI" 코드 페이지에서 misinterprets 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-141">Without the BOM, Windows PowerShell misinterprets your script as being encoded in the legacy "ANSI" codepage.</span></span> <span data-ttu-id="cf586-142">반대로 UTF-8 BOM이 있는 파일은 Unix와 비슷한 플랫폼에서 문제가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-142">Conversely, files that do have the UTF-8 BOM can be problematic on Unix-like platforms.</span></span> <span data-ttu-id="cf586-143">`cat`, `sed` , 및와 같은 `awk` 일부 편집기는 BOM을 처리 하 `gedit` 는 방법을 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-143">Many Unix tools such as `cat`, `sed`, `awk`, and some editors such as `gedit` don't know how to treat the BOM.</span></span>

## <a name="character-encoding-in-windows-powershell"></a><span data-ttu-id="cf586-144">Windows PowerShell의 문자 인코딩</span><span class="sxs-lookup"><span data-stu-id="cf586-144">Character encoding in Windows PowerShell</span></span>

<span data-ttu-id="cf586-145">PowerShell 5.1에서 **Encoding** 매개 변수는 다음 값을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-145">In PowerShell 5.1, the **Encoding** parameter supports the following values:</span></span>

- <span data-ttu-id="cf586-146">`Ascii` Ascii (7 비트) 문자 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-146">`Ascii` Uses Ascii (7-bit) character set.</span></span>
- <span data-ttu-id="cf586-147">`BigEndianUnicode` 에서는 u t f-16을 빅 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-147">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="cf586-148">`BigEndianUTF32` 는 빅 endian 바이트 순서를 사용 하 여 u t f-32을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-148">`BigEndianUTF32` Uses UTF-32 with the big-endian byte order.</span></span>
- <span data-ttu-id="cf586-149">`Byte` 문자 집합을 바이트 시퀀스로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-149">`Byte` Encodes a set of characters into a sequence of bytes.</span></span>
- <span data-ttu-id="cf586-150">`Default` 시스템의 활성 코드 페이지에 해당 하는 인코딩을 사용 합니다 (일반적으로 ANSI).</span><span class="sxs-lookup"><span data-stu-id="cf586-150">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="cf586-151">`Oem` 시스템의 현재 OEM 코드 페이지에 해당 하는 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-151">`Oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="cf586-152">`String`: `Unicode`과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-152">`String` Same as `Unicode`.</span></span>
- <span data-ttu-id="cf586-153">`Unicode` 는 u t f-16을 약간 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-153">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="cf586-154">`Unknown`: `Unicode`과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-154">`Unknown` Same as `Unicode`.</span></span>
- <span data-ttu-id="cf586-155">`UTF32` 는 u t f-32을 작은 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-155">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>
- <span data-ttu-id="cf586-156">`UTF7` 는 u t f-7을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-156">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="cf586-157">`UTF8` 는 u t f-8 (BOM 포함)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-157">`UTF8` Uses UTF-8 (with BOM).</span></span>

<span data-ttu-id="cf586-158">일반적으로 Windows PowerShell은 기본적으로 유니코드 [UTF-utf-16le](https://wikipedia.org/wiki/UTF-16) 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-158">In general, Windows PowerShell uses the Unicode [UTF-16LE](https://wikipedia.org/wiki/UTF-16) encoding by default.</span></span> <span data-ttu-id="cf586-159">그러나 Windows PowerShell에서 cmdlet에 사용 되는 기본 인코딩은 일치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-159">However, the default encoding used by cmdlets in Windows PowerShell is not consistent.</span></span>

> [!NOTE]
> <span data-ttu-id="cf586-160">를 제외 하 고 모든 유니코드 인코딩을 사용 하 여 `UTF7` 은 항상 BOM을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-160">Using any Unicode encoding, except `UTF7`, always creates a BOM.</span></span>

<span data-ttu-id="cf586-161">파일에 출력을 기록 하는 cmdlet의 경우:</span><span class="sxs-lookup"><span data-stu-id="cf586-161">For cmdlets that write output to files:</span></span>

- <span data-ttu-id="cf586-162">`Out-File` 및와는 `>` `>>` 달리 utf-16le을 만듭니다 `Set-Content` `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="cf586-162">`Out-File` and the redirection operators `>` and `>>` create UTF-16LE, which notably differs from `Set-Content` and `Add-Content`.</span></span>

- <span data-ttu-id="cf586-163">`New-ModuleManifest``Export-CliXml`또한 utf-16le 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-163">`New-ModuleManifest` and `Export-CliXml` also create UTF-16LE files.</span></span>

- <span data-ttu-id="cf586-164">대상 파일이 비어 있거나 존재 하지 않는 경우 `Set-Content` 및 `Add-Content` `Default` 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-164">When the target file is empty or doesn't exist, `Set-Content` and `Add-Content` use `Default` encoding.</span></span> <span data-ttu-id="cf586-165">`Default` 활성 시스템 로캘의 ANSI 레거시 코드 페이지에서 지정 하는 인코딩입니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-165">`Default` is the encoding specified by the active system locale's ANSI legacy code page.</span></span>

- <span data-ttu-id="cf586-166">`Export-Csv``Ascii` **추가** 매개 변수를 사용할 때 파일을 만들지만 다른 인코딩을 사용 합니다 (아래 참조).</span><span class="sxs-lookup"><span data-stu-id="cf586-166">`Export-Csv` creates `Ascii` files but uses different encoding when using **Append** parameter (see below).</span></span>

- <span data-ttu-id="cf586-167">`Export-PSSession` 기본적으로 BOM을 사용 하 여 UTF-8 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-167">`Export-PSSession` creates UTF-8 files with BOM by default.</span></span>

- <span data-ttu-id="cf586-168">`New-Item -Type File -Value` BOM less UTF-8 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-168">`New-Item -Type File -Value` creates a BOM-less UTF-8 file.</span></span>

- <span data-ttu-id="cf586-169">`Send-MailMessage` 에서는 `Default` 기본적으로 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-169">`Send-MailMessage` uses `Default` encoding by default.</span></span>

- <span data-ttu-id="cf586-170">`Start-Transcript``Utf8`BOM을 사용 하 여 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-170">`Start-Transcript` creates `Utf8` files with a BOM.</span></span> <span data-ttu-id="cf586-171">**추가** 매개 변수를 사용 하는 경우 인코딩은 다를 수 있습니다 (아래 참조).</span><span class="sxs-lookup"><span data-stu-id="cf586-171">When the **Append** parameter is used, the encoding can be different (see below).</span></span>

<span data-ttu-id="cf586-172">기존 파일에 추가 하는 명령:</span><span class="sxs-lookup"><span data-stu-id="cf586-172">For commands that append to an existing file:</span></span>

- <span data-ttu-id="cf586-173">`Out-File -Append` 그리고 `>>` 리디렉션 연산자는 기존 대상 파일의 내용에 대 한 인코딩을 일치 시 키 지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-173">`Out-File -Append` and the `>>` redirection operator make no attempt to match the encoding of the existing target file's content.</span></span> <span data-ttu-id="cf586-174">대신 **encoding** 매개 변수를 사용 하지 않는 한 기본 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-174">Instead, they use the default encoding unless the **Encoding** parameter is used.</span></span> <span data-ttu-id="cf586-175">콘텐츠를 추가할 때 원래 파일 인코딩을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-175">You must use the files original encoding when appending content.</span></span>

- <span data-ttu-id="cf586-176">명시적 **인코딩** 매개 변수가 없는 경우는 `Add-Content` 기존 인코딩을 검색 하 고 새 내용에 자동으로 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-176">In the absence of an explicit **Encoding** parameter, `Add-Content` detects the existing encoding and automatically applies it to the new content.</span></span> <span data-ttu-id="cf586-177">기존 콘텐츠에 BOM이 없으면 `Default` ANSI 인코딩이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-177">If the existing content has no BOM, `Default` ANSI encoding is used.</span></span> <span data-ttu-id="cf586-178">의 동작은 `Add-Content` 기본 인코딩이 인 경우를 제외 하 고 PowerShell Core (v6 이상)에서 동일 합니다 `Utf8` .</span><span class="sxs-lookup"><span data-stu-id="cf586-178">The behavior of `Add-Content` is the same in PowerShell Core (v6 and higher) except the default encoding is `Utf8`.</span></span>

- <span data-ttu-id="cf586-179">`Export-Csv -Append` 대상 파일에 BOM이 포함 되어 있을 때 기존 인코딩과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-179">`Export-Csv -Append` matches the existing encoding when the target file contains a BOM.</span></span> <span data-ttu-id="cf586-180">BOM이 없으면 `Utf8` 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-180">In the absence of a BOM, it uses `Utf8` encoding.</span></span>

- <span data-ttu-id="cf586-181">`Start-Transcript -Append` BOM을 포함 하는 파일의 기존 인코딩과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-181">`Start-Transcript -Append` matches the existing encoding of files that include a BOM.</span></span> <span data-ttu-id="cf586-182">BOM이 없으면 기본값은 `Ascii` encoding입니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-182">In the absence of a BOM, it defaults to `Ascii` encoding.</span></span> <span data-ttu-id="cf586-183">이 인코딩은 기록의 데이터에 멀티 바이트 문자가 포함 된 경우 데이터 손실 또는 문자 손상이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-183">This encoding can result in data loss or character corruption when the data in the transcript contains multibyte characters.</span></span>

<span data-ttu-id="cf586-184">BOM이 없을 때 문자열 데이터를 읽는 cmdlet의 경우:</span><span class="sxs-lookup"><span data-stu-id="cf586-184">For cmdlets that read string data in the absence of a BOM:</span></span>

- <span data-ttu-id="cf586-185">`Get-Content` 및 `Import-PowerShellDataFile` 는 `Default` ANSI 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-185">`Get-Content` and `Import-PowerShellDataFile` uses the `Default` ANSI encoding.</span></span> <span data-ttu-id="cf586-186">ANSI는 파일에서 소스 코드를 읽을 때 PowerShell 엔진에서 사용 하는 역할도 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-186">ANSI is also what the PowerShell engine uses when it reads source code from files.</span></span>

- <span data-ttu-id="cf586-187">`Import-Csv`, `Import-CliXml` 및 `Select-String` `Utf8` 는 BOM이 없을 때를 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-187">`Import-Csv`, `Import-CliXml`, and `Select-String` assume `Utf8` in the absence of a BOM.</span></span>

## <a name="character-encoding-in-powershell-core"></a><span data-ttu-id="cf586-188">PowerShell Core의 문자 인코딩</span><span class="sxs-lookup"><span data-stu-id="cf586-188">Character encoding in PowerShell Core</span></span>

<span data-ttu-id="cf586-189">PowerShell Core (v6 이상)에서 **Encoding** 매개 변수는 다음 값을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-189">In PowerShell Core (v6 and higher), the **Encoding** parameter supports the following values:</span></span>

- <span data-ttu-id="cf586-190">`ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-190">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="cf586-191">`bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-191">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="cf586-192">`oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-192">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="cf586-193">`unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-193">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="cf586-194">`utf7`: UTF-7 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-194">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="cf586-195">`utf8`: UTF-8 형식으로 인코딩합니다 (BOM 없음).</span><span class="sxs-lookup"><span data-stu-id="cf586-195">`utf8`: Encodes in UTF-8 format (no BOM).</span></span>
- <span data-ttu-id="cf586-196">`utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-196">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="cf586-197">`utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-197">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="cf586-198">`utf32`: U t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-198">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="cf586-199">PowerShell Core `utf8NoBOM` 는 모든 출력에 대해 기본적으로로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-199">PowerShell Core defaults to `utf8NoBOM` for all output.</span></span>

<span data-ttu-id="cf586-200">PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="cf586-200">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="cf586-201">자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage)대 한 .net 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cf586-201">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage).</span></span>

## <a name="changing-the-default-encoding"></a><span data-ttu-id="cf586-202">기본 인코딩 변경</span><span class="sxs-lookup"><span data-stu-id="cf586-202">Changing the default encoding</span></span>

<span data-ttu-id="cf586-203">PowerShell에는 기본 인코딩 동작을 변경 하는 데 사용할 수 있는 두 가지 기본 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-203">PowerShell has two default variables that can be used to change the default encoding behavior.</span></span>

- `$PSDefaultParameterValues`
- `$OutputEncoding`

<span data-ttu-id="cf586-204">자세한 내용은 [about_Preference_Variables](about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cf586-204">For more information, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="cf586-205">PowerShell 5.1부터 리디렉션 연산자 ( `>` 및 `>>` )가 cmdlet을 호출 합니다 `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="cf586-205">Beginning in PowerShell 5.1, the redirection operators (`>` and `>>`) call the `Out-File` cmdlet.</span></span> <span data-ttu-id="cf586-206">따라서 `$PSDefaultParameterValues` 다음 예제와 같이 기본 설정 변수를 사용 하 여 기본 인코딩을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-206">Therefore, you can set the default encoding of them using the `$PSDefaultParameterValues` preference variable as shown in this example:</span></span>

```powershell
$PSDefaultParameterValues['Out-File:Encoding'] = 'utf8'
```

<span data-ttu-id="cf586-207">다음 문을 사용 하 여 **encoding** 매개 변수가 있는 모든 cmdlet에 대 한 기본 인코딩을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-207">Use the following statement to change the default encoding for all cmdlets that have the **Encoding** parameter.</span></span>

```powershell
$PSDefaultParameterValues['*:Encoding'] = 'utf8'
```

> [!IMPORTANT]
> <span data-ttu-id="cf586-208">PowerShell 프로필에이 명령을 배치 하면 인코딩을 명시적으로 지정 하지 않는 모든 명령 및 스크립트에 영향을 주는 기본 설정이 세션 전역 설정으로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-208">Putting this command in your PowerShell profile makes the preference a session-global setting that affects all commands and scripts that do not explicitly specify an encoding.</span></span>
>
> <span data-ttu-id="cf586-209">마찬가지로 동일한 방식으로 동작 하려는 스크립트나 모듈에 이러한 명령을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-209">Similarly, you should include such commands in your scripts or modules that you want to behave the same way.</span></span> <span data-ttu-id="cf586-210">이러한 명령을 사용 하 여 다른 사용자, 다른 컴퓨터 또는 다른 PowerShell 버전에서 실행 하는 경우에도 cmdlet이 동일한 방식으로 동작 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-210">Using these commands ensure that cmdlets behave the same way even when run by another user, on a different computer, or in a different version of PowerShell.</span></span>

<span data-ttu-id="cf586-211">자동 변수는 `$OutputEncoding` PowerShell이 외부 프로그램과 통신 하는 데 사용 하는 인코딩에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-211">The automatic variable `$OutputEncoding` affects the encoding PowerShell uses to communicate with external programs.</span></span> <span data-ttu-id="cf586-212">출력 리디렉션 연산자와 PowerShell cmdlet이 파일에 저장 하는 데 사용 하는 인코딩에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf586-212">It has no effect on the encoding that the output redirection operators and PowerShell cmdlets use to save to files.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf586-213">참조</span><span class="sxs-lookup"><span data-stu-id="cf586-213">See also</span></span>

- [<span data-ttu-id="cf586-214">.NET의 문자 인코딩 소개</span><span class="sxs-lookup"><span data-stu-id="cf586-214">Introduction to character encoding in .NET</span></span>](/dotnet/standard/base-types/character-encoding-introduction)
- [<span data-ttu-id="cf586-215">코드 페이지-Win32 앱</span><span class="sxs-lookup"><span data-stu-id="cf586-215">Code Pages - Win32 apps</span></span>](/windows/win32/intl/code-pages)
- [<span data-ttu-id="cf586-216">유니코드 표준</span><span class="sxs-lookup"><span data-stu-id="cf586-216">The Unicode Standard</span></span>](https://www.unicode.org/standard/standard.html)
- [<span data-ttu-id="cf586-217">Encoding. CodePage</span><span class="sxs-lookup"><span data-stu-id="cf586-217">Encoding.CodePage</span></span>](/dotnet/api/system.text.encoding.codepage)
- [<span data-ttu-id="cf586-218">UTF-16LE</span><span class="sxs-lookup"><span data-stu-id="cf586-218">UTF-16LE</span></span>](https://wikipedia.org/wiki/UTF-16)
- [<span data-ttu-id="cf586-219">바이트 순서 표시</span><span class="sxs-lookup"><span data-stu-id="cf586-219">Byte order mark</span></span>](https://wikipedia.org/wiki/Byte_order_mark)
- [<span data-ttu-id="cf586-220">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="cf586-220">about_Preference_Variables</span></span>](about_Preference_Variables.md)
