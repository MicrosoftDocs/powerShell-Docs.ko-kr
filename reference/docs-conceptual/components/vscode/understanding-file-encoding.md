---
title: VSCode 및 PowerShell에서 파일 인코딩 이해
description: VSCode 및 PowerShell에서 파일 인코딩 구성
ms.date: 02/28/2019
ms.openlocfilehash: 3283e1262c8eb26906429ecf195cfa0b122b330f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74117416"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="d0c31-103">VSCode 및 PowerShell에서 파일 인코딩 이해</span><span class="sxs-lookup"><span data-stu-id="d0c31-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="d0c31-104">VS Code를 사용하여 PowerShell 스크립트를 편집할 때 올바른 문자 인코딩 형식을 사용하여 파일을 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="d0c31-105">파일 인코딩의 정의 및 중요한 이유는 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="d0c31-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="d0c31-106">VSCode는 버퍼에 사람이 입력한 문자의 문자열과 파일 시스템에 대한 바이트의 읽기/쓰기 블록 간의 인터페이스를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="d0c31-107">VSCode는 파일을 저장할 때 텍스트 인코딩을 사용하여 각 문자가 되는 바이트를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-107">When VSCode saves a file, it uses a text encoding to decide what bytes each character becomes.</span></span>

<span data-ttu-id="d0c31-108">마찬가지로, PowerShell이 스크립트를 실행할 때 파일의 바이트를 문자로 변환하여 파일을 PowerShell 프로그램으로 다시 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="d0c31-109">VSCode가 파일을 작성하고 PowerShell이 파일을 읽게 되므로 둘 다 동일한 인코딩 시스템을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="d0c31-110">PowerShell 스크립트를 구문 분석하는 이 프로세스는 다음과 같은 순서로 이루어집니다. *바이트* -> *문자* -> *토큰* -> *추상 구문 트리* -> *실행*</span><span class="sxs-lookup"><span data-stu-id="d0c31-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="d0c31-111">VSCode 및 PowerShell은 모두 적절한 기본 인코딩 구성으로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="d0c31-112">그러나 PowerShell에서 사용되는 기본 인코딩이 PowerShell Core(v6.x)의 릴리스에서 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="d0c31-113">VSCode에서 PowerShell 또는 PowerShell 확장을 사용할 때 문제가 발생하지 않도록 하려면 VSCode 및 PowerShell 설정을 제대로 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="d0c31-114">인코딩 문제의 일반적인 원인</span><span class="sxs-lookup"><span data-stu-id="d0c31-114">Common causes of encoding issues</span></span>

<span data-ttu-id="d0c31-115">VSCode를 인코딩하거나 스크립트 파일이 예상되는 PowerShell 인코딩과 일치하지 않는 경우에 인코딩 문제가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="d0c31-116">PowerShell이 파일 인코딩을 자동으로 결정할 수 있는 방법이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="d0c31-117">[7비트 ASCII 문자 세트](https://ascii.cl/)에 포함되지 않는 문자를 사용할 때 인코딩 문제가 발생할 가능성이 더 높습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="d0c31-118">예:</span><span class="sxs-lookup"><span data-stu-id="d0c31-118">For example:</span></span>

- <span data-ttu-id="d0c31-119">em-dash(`—`), 비 공백(` `) 또는 왼쪽 큰따옴표(`“`)와 같이 확장된 문자가 아닌 문자</span><span class="sxs-lookup"><span data-stu-id="d0c31-119">Extended non-letter characters like em-dash (`—`), non-breaking space (` `) or left double quotation mark (`“`)</span></span>
- <span data-ttu-id="d0c31-120">악센트 부호가 있는 라틴어 문자(`É`, `ü`)</span><span class="sxs-lookup"><span data-stu-id="d0c31-120">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="d0c31-121">키릴 자모와 같은 비라틴어 문자(`Д`, `Ц`)</span><span class="sxs-lookup"><span data-stu-id="d0c31-121">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="d0c31-122">CJK 문자(`本`, `화`, `が`)</span><span class="sxs-lookup"><span data-stu-id="d0c31-122">CJK characters (`本`, `화`, `が`)</span></span>

<span data-ttu-id="d0c31-123">인코딩 문제에 대한 일반적인 원인은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-123">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="d0c31-124">VSCode 및 PowerShell 인코딩의 기본값은 변경되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-124">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="d0c31-125">PowerShell 5.1 이하의 경우 기본 인코딩은 VSCode와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-125">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="d0c31-126">다른 편집기가 열리고 새 인코딩으로 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-126">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="d0c31-127">이 문제는 ISE를 사용하는 경우에 자주 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-127">This often happens with the ISE.</span></span>
- <span data-ttu-id="d0c31-128">파일이 VSCode 또는 PowerShell에서 예상하는 것과 다른 인코딩으로 소스 제어에 체크 인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-128">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="d0c31-129">공동 작업자가 다른 인코딩 구성에서 편집기를 사용할 때 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-129">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="d0c31-130">인코딩 문제가 발생하는 경우를 구별하는 방법</span><span class="sxs-lookup"><span data-stu-id="d0c31-130">How to tell when you have encoding issues</span></span>

<span data-ttu-id="d0c31-131">종종 인코딩 오류는 스크립트에서 구문 분석 오류로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-131">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="d0c31-132">스크립트에서 이상한 문자 시퀀스를 찾으면 이 경우에 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-132">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="d0c31-133">아래 예제에서는 대시 부호(`–`)가 `â€“` 문자로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-133">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="d0c31-134">VSCode가 UTF-8인 `–` 문자를 `0xE2 0x80 0x93` 바이트로 인코딩하기 때문에 이 문제가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-134">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="d0c31-135">이러한 바이트가 Windows-1252로 디코딩되면 `â€“` 문자로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-135">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="d0c31-136">표시될 수 있는 몇 가지 이상한 문자 시퀀스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-136">Some strange character sequences that you might see include:</span></span>

<!-- markdownlint-disable MD038 -->
- <span data-ttu-id="d0c31-137">`â€“` 대신 `–`</span><span class="sxs-lookup"><span data-stu-id="d0c31-137">`â€“` instead of `–`</span></span>
- <span data-ttu-id="d0c31-138">`â€”` 대신 `—`</span><span class="sxs-lookup"><span data-stu-id="d0c31-138">`â€”` instead of `—`</span></span>
- <span data-ttu-id="d0c31-139">`Ã„2` 대신 `Ä`</span><span class="sxs-lookup"><span data-stu-id="d0c31-139">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="d0c31-140">` `(줄 바꿈하지 않는 공백) 대신 `Â`</span><span class="sxs-lookup"><span data-stu-id="d0c31-140">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="d0c31-141">`Ã©` 대신 `é`</span><span class="sxs-lookup"><span data-stu-id="d0c31-141">`Ã©` instead of `é`</span></span>
<!-- markdownlint-enable MD038 -->

<span data-ttu-id="d0c31-142">이 유용한 [참조](https://www.i18nqa.com/debug/utf8-debug.html)에서는 UTF-8/Windows-1252 인코딩 문제를 나타내는 일반적인 패턴을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-142">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="d0c31-143">VSCode에서 PowerShell 확장이 인코딩과 상호 작용하는 방법</span><span class="sxs-lookup"><span data-stu-id="d0c31-143">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="d0c31-144">PowerShell 확장은 다음과 같은 여러 가지 방법으로 스크립트와 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-144">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="d0c31-145">VSCode에서 스크립트를 편집하면 내용은 VSCode에 의해 확장 프로그램에 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-145">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="d0c31-146">[언어 서버 프로토콜][]은 이 내용이 UTF-8로 전송되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-146">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="d0c31-147">따라서 확장 프로그램이 잘못 인코딩될 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-147">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="d0c31-148">스크립트가 통합 콘솔에서 직접 실행되면 PowerShell이 직접 파일을 읽게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-148">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="d0c31-149">PowerShell의 인코딩이 VSCode와 다를 경우 여기에서 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-149">If PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="d0c31-150">VSCode에서 열려 있는 스크립트가 VSCode에서 열려 있지 않은 다른 스크립트를 참조하는 경우 확장 프로그램은 파일 시스템에서 해당 스크립트의 내용을 로드하도록 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-150">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="d0c31-151">PowerShell 확장은 UTF-8 인코딩을 기본값으로 지정하지만 [바이트 순서 표시][](또는 BOM) 검색 기능을 사용하여 올바른 인코딩을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-151">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="d0c31-152">BOM이 없는 형식(예: BOM을 포함하지 않는 [UTF-8][] 및 [Windows-1252][])으로 인코딩한다고 가정하는 경우 이 문제가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-152">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="d0c31-153">PowerShell 확장은 UTF-8을 기본값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-153">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="d0c31-154">확장 프로그램은 VSCode의 인코딩 설정을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-154">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="d0c31-155">자세한 내용은 [문제 #824](https://github.com/Microsoft/vscode/issues/824)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d0c31-155">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="d0c31-156">맞는 인코딩 선택</span><span class="sxs-lookup"><span data-stu-id="d0c31-156">Choosing the right encoding</span></span>

<span data-ttu-id="d0c31-157">여러 시스템 및 애플리케이션마다 다른 인코딩을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-157">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="d0c31-158">.NET 표준, 웹 및 Linux 분야에서 UTF-8은 이제 가장 많이 사용되는 인코딩입니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-158">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="d0c31-159">다수의 .NET Framework 애플리케이션이 [UTF-16][]을 사용하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-159">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="d0c31-160">역사적 이유로 인해 UTF-8 및 UTF-16을 모두 포함하는 광범위한 [표준](https://en.wikipedia.org/wiki/Unicode)을 의미하는 "Unicode"라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-160">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="d0c31-161">Windows에서 유니코드보다 앞선 많은 네이티브 애플리케이션이 기본적으로 계속 Windows-1252를 사용하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-161">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="d0c31-162">유니코드 인코딩에는 BOM(바이트 순서 표시)라는 개념도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-162">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="d0c31-163">BOM은 텍스트에서 사용하는 인코딩을 디코더에 알려주기 위해 텍스트의 시작 부분에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-163">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="d0c31-164">멀티바이트 인코딩의 경우 BOM은 인코딩의 [엔디언](https://en.wikipedia.org/wiki/Endianness)을 나타내기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-164">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="d0c31-165">BOM은 유니코드가 아닌 텍스트에서 거의 표시되지 않는 바이트로 설계되었으므로 BOM이 있는 경우 텍스트가 유니코드라고 적절히 추측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-165">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="d0c31-166">UTF-8이라는 신뢰할 수 있는 규칙이 어디서나 사용되기 때문에 BOM은 선택 사항이며 Linux 분야에서 널리 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-166">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="d0c31-167">대부분의 Linux 애플리케이션에서는 텍스트 입력이 UTF-8로 인코딩된다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-167">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="d0c31-168">대부분의 Linux 애플리케이션에서는 BOM을 제대로 인식하고 처리하지만 일부는 그렇지 않으므로 텍스트에서 해당 애플리케이션으로 조작된 아티팩트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-168">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="d0c31-169">**따라서 다음 작업을 수행하세요**:</span><span class="sxs-lookup"><span data-stu-id="d0c31-169">**Therefore**:</span></span>

- <span data-ttu-id="d0c31-170">주로 Windows 애플리케이션 및 Windows PowerShell으로 작업하는 경우 BOM이 포함된 UTF-8 또는 UTF-16과 같은 인코딩을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-170">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="d0c31-171">플랫폼에서 작업하는 경우 BOM이 포함된 UTF-8을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-171">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="d0c31-172">Linux 관련 컨텍스트에서 주로 작업하는 경우 BOM이 포함되지 않은 UTF-8을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-172">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="d0c31-173">Windows-1252 및 라틴어-1은 가능하면 피해야 하는 기본적으로 레거시 인코딩입니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-173">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="d0c31-174">그러나 몇 가지 이전 Windows 애플리케이션이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-174">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="d0c31-175">스크립트 서명은 [인코딩 종속](https://github.com/PowerShell/PowerShell/issues/3466)적입니다. 즉, 서명된 스크립트에서 인코딩을 변경하면 다시 서명해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-175">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="d0c31-176">VSCode 구성</span><span class="sxs-lookup"><span data-stu-id="d0c31-176">Configuring VSCode</span></span>

<span data-ttu-id="d0c31-177">VSCode의 기본 인코딩은 BOM이 포함되지 않은 UTF-8입니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-177">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="d0c31-178">[VSCode의 인코딩][]을 설정하려면 VSCode 설정(<kbd>Ctrl</kbd>+<kbd>,</kbd>)으로 이동하고 `"files.encoding"` 설정을 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="d0c31-178">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl</kbd>+<kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="d0c31-179">가능한 값의 일부는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-179">Some possible values are:</span></span>

- <span data-ttu-id="d0c31-180">`utf8`: BOM이 포함되지 않은 [UTF-8]</span><span class="sxs-lookup"><span data-stu-id="d0c31-180">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="d0c31-181">`utf8bom`: BOM이 포함된 [UTF-8]</span><span class="sxs-lookup"><span data-stu-id="d0c31-181">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="d0c31-182">`utf16le`: Little endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="d0c31-182">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="d0c31-183">`utf16be`: Big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="d0c31-183">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="d0c31-184">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="d0c31-184">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="d0c31-185">GUI 보기로 이에 대한 드롭다운 또는 JSON 보기로 이에 대한 완성을 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-185">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="d0c31-186">가능하면 인코딩을 자동으로 검색하기 위해 다음을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-186">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="d0c31-187">이러한 설정이 모든 파일 형식에 영향을 주지 않으려는 경우 VSCode에서 언어별 구성을 허용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-187">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="d0c31-188">`[<language-name>]` 필드에서 설정을 지정하여 언어별 설정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-188">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="d0c31-189">예:</span><span class="sxs-lookup"><span data-stu-id="d0c31-189">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="d0c31-190">PowerShell 구성</span><span class="sxs-lookup"><span data-stu-id="d0c31-190">Configuring PowerShell</span></span>

<span data-ttu-id="d0c31-191">PowerShell의 기본 인코딩은 버전에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-191">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="d0c31-192">PowerShell 6+에서 기본 인코딩은 모든 플랫폼에서 BOM를 포함하지 않는 UTF-8입니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-192">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="d0c31-193">Windows PowerShell에서 기본 인코딩은 일반적으로 Windows-1252이고, [라틴어-1][]의 확장은 ISO 8859-1이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-193">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="d0c31-194">PowerShell 5 이상에서는 다음을 포함한 기본 인코딩을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-194">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="d0c31-195">다음 [스크립트](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e)를 사용하여 PowerShell 세션이 BOM을 포함하지 않은 스크립트에서 유추한 인코딩을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-195">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

<span data-ttu-id="d0c31-196">프로필 설정을 사용하여 보다 일반적으로 지정된 인코딩을 사용히도록 PowerShell을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-196">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="d0c31-197">다음 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d0c31-197">See the following articles:</span></span>

- <span data-ttu-id="d0c31-198">[@mklement0] [stackoverflow PowerShell 인코딩에 대 한 응답](https://stackoverflow.com/a/40098904)합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-198">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="d0c31-199">[@rkeithhill] [PowerShell에서 BOM 없는 utf-8 입력을 처리 하는 방법에 대 한 블로그 게시물](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/)합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-199">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="d0c31-200">PowerShell이 특정 입력 인코딩을 사용하도록 강제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-200">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="d0c31-201">PowerShell 5.1 이하에서는 BOM이 없으면 Windows-1252 인코딩을 기본값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-201">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="d0c31-202">상호 운용성을 위해 BOM을 포함한 유니코드 형식으로 스크립트를 저장하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-202">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d0c31-203">PowerShell 스크립트에 관련된 다른 도구가 인코딩 선택에 따라 달라지거나 다른 인코딩으로 스크립트를 다시 인코딩할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-203">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="d0c31-204">기존 스크립트</span><span class="sxs-lookup"><span data-stu-id="d0c31-204">Existing scripts</span></span>

<span data-ttu-id="d0c31-205">파일 시스템에 이미 있는 스크립트를 새로 선택된 인코딩으로 다시 인코딩해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-205">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="d0c31-206">VSCode의 아래쪽 막대에서 UTF-8 레이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-206">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="d0c31-207">해당 항목을 클릭하여 작업 모음을 열고 **인코딩하여 저장**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-207">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="d0c31-208">이제 해당 파일에서 새 인코딩을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-208">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="d0c31-209">전체 지침은 [VSCode의 인코딩][]을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d0c31-209">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="d0c31-210">여러 파일을 다시 인코딩해야 하는 경우 다음 스크립트를 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-210">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="d0c31-211">PowerShell ISE(통합 스크립팅 환경)</span><span class="sxs-lookup"><span data-stu-id="d0c31-211">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="d0c31-212">PowerShell ISE를 사용하여 스크립트를 편집하는 경우 거기에서 인코딩 설정을 동기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-212">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="d0c31-213">ISE는 BOM을 적용해야 하지만 리플렉션을 사용하여 [인코딩을 설정](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/)할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-213">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="d0c31-214">이 설정은 시작 시 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-214">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="d0c31-215">소스 제어 소프트웨어</span><span class="sxs-lookup"><span data-stu-id="d0c31-215">Source control software</span></span>

<span data-ttu-id="d0c31-216">Git와 같은 일부 소스 제어 도구는 인코딩을 무시합니다. Git는 바이트를 추적하기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-216">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="d0c31-217">Azure DevOps 또는 Mercurial과 같은 다른 도구는 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-217">Others, like Azure DevOps or Mercurial, may not.</span></span> <span data-ttu-id="d0c31-218">일부 Git 기반 도구도 디코딩 텍스트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-218">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="d0c31-219">이 경우에는 다음을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="d0c31-219">When this is the case, make sure you:</span></span>

- <span data-ttu-id="d0c31-220">소스 제어의 텍스트 인코딩이 VSCode 구성과 일치하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-220">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="d0c31-221">모든 파일이 관련 인코딩으로 소스 제어에 체크 인되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-221">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="d0c31-222">소스 제어를 통해 수신된 인코딩의 변경 내용에 주의하세요.</span><span class="sxs-lookup"><span data-stu-id="d0c31-222">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="d0c31-223">여기서 주요 기호는 변경을 나타내는 Diff이지만 변경되지 않은 것처럼 보입니다(바이트는 변경되었지만 문자가 변경되지 않기 때문에).</span><span class="sxs-lookup"><span data-stu-id="d0c31-223">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="d0c31-224">공동 작업자 환경</span><span class="sxs-lookup"><span data-stu-id="d0c31-224">Collaborators' environments</span></span>

<span data-ttu-id="d0c31-225">소스 제어를 구성하려면 공유하는 파일에서 공동 작업자가 PowerShell 파일을 다시 인코딩하여 인코딩을 재정의하도록 설정하지 않았는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-225">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="d0c31-226">다른 프로그램</span><span class="sxs-lookup"><span data-stu-id="d0c31-226">Other programs</span></span>

<span data-ttu-id="d0c31-227">PowerShell 스크립트를 읽거나 작성하는 다른 프로그램이 해당 항목을 다시 인코딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-227">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="d0c31-228">몇 가지 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-228">Some examples are:</span></span>

- <span data-ttu-id="d0c31-229">클립보드를 사용하여 스크립트를 복사하고 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-229">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="d0c31-230">다음은 같은 시나리오에서 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-230">This is common in scenarios like:</span></span>
  - <span data-ttu-id="d0c31-231">VM에 스크립트 복사</span><span class="sxs-lookup"><span data-stu-id="d0c31-231">Copying a script into a VM</span></span>
  - <span data-ttu-id="d0c31-232">이메일 또는 웹 페이지에서 스크립트 복사</span><span class="sxs-lookup"><span data-stu-id="d0c31-232">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="d0c31-233">Microsoft Word나 PowerPoint 문서에서/로 스크립트 복사</span><span class="sxs-lookup"><span data-stu-id="d0c31-233">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="d0c31-234">다음과 같은 다른 텍스트 편집기:</span><span class="sxs-lookup"><span data-stu-id="d0c31-234">Other text editors, such as:</span></span>
  - <span data-ttu-id="d0c31-235">메모장</span><span class="sxs-lookup"><span data-stu-id="d0c31-235">Notepad</span></span>
  - <span data-ttu-id="d0c31-236">vim</span><span class="sxs-lookup"><span data-stu-id="d0c31-236">vim</span></span>
  - <span data-ttu-id="d0c31-237">다른 PowerShell 스크립트 편집기</span><span class="sxs-lookup"><span data-stu-id="d0c31-237">Any other PowerShell script editor</span></span>
- <span data-ttu-id="d0c31-238">다음과 같은 텍스트 편집 유틸리티:</span><span class="sxs-lookup"><span data-stu-id="d0c31-238">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="d0c31-239">`>` 및 `>>`와 같은 PowerShell 리디렉션 연산자</span><span class="sxs-lookup"><span data-stu-id="d0c31-239">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="d0c31-240">다음과 같은 파일 전송 프로그램:</span><span class="sxs-lookup"><span data-stu-id="d0c31-240">File transfer programs, like:</span></span>
  - <span data-ttu-id="d0c31-241">스크립트를 다운로드하는 경우 웹 브라우저</span><span class="sxs-lookup"><span data-stu-id="d0c31-241">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="d0c31-242">파일 공유</span><span class="sxs-lookup"><span data-stu-id="d0c31-242">A file share</span></span>

<span data-ttu-id="d0c31-243">이러한 일부 도구는 텍스트가 아닌 바이트 단위로 처리하지만 나머지는 인코딩 구성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-243">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="d0c31-244">인코딩을 구성해야 하는 경우 이러한 문제를 방지하기 위해 인코딩하는 편집기와 동일하게 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-244">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="d0c31-245">PowerShell에서 인코딩할 다른 리소스</span><span class="sxs-lookup"><span data-stu-id="d0c31-245">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="d0c31-246">PowerShell에서 인코딩 및 인코딩 구성에 대해 읽을 만한 몇 가지 다른 유용한 게시물은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0c31-246">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="d0c31-247">[@mklement0] [stackoverflow PowerShell 인코딩의 요약](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="d0c31-247">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="d0c31-248">인코딩 문제과 관련하여 vscode-PowerShell에서 열린 이전 문제:</span><span class="sxs-lookup"><span data-stu-id="d0c31-248">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="d0c31-249">#1308</span><span class="sxs-lookup"><span data-stu-id="d0c31-249">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="d0c31-250">#1628</span><span class="sxs-lookup"><span data-stu-id="d0c31-250">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="d0c31-251">#1680</span><span class="sxs-lookup"><span data-stu-id="d0c31-251">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="d0c31-252">#1744</span><span class="sxs-lookup"><span data-stu-id="d0c31-252">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="d0c31-253">#1751</span><span class="sxs-lookup"><span data-stu-id="d0c31-253">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="d0c31-254">유니코드에 대한 클래식 *Joel on Software* 논평</span><span class="sxs-lookup"><span data-stu-id="d0c31-254">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="d0c31-255">.NET 표준으로 인코딩</span><span class="sxs-lookup"><span data-stu-id="d0c31-255">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[라틴어-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[바이트 순서 표시]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[언어 서버 프로토콜]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[VSCode의 인코딩]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
