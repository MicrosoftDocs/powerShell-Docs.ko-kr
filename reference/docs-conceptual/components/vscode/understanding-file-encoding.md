---
title: VSCode 및 PowerShell에서 파일 인코딩 이해
description: VSCode 및 PowerShell에서 파일 인코딩 구성
ms.date: 02/28/2019
ms.openlocfilehash: 9cf445ebd0c2bb2dbdf4438f02dafe3df3a5d1e2
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429808"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="363f5-103">VSCode 및 PowerShell에서 파일 인코딩 이해</span><span class="sxs-lookup"><span data-stu-id="363f5-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="363f5-104">VS Code를 사용 하 여 PowerShell 스크립트를 편집 및 만들기를 반드시 올바른 문자 인코딩 형식을 사용 하 여 파일에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="363f5-105">파일 인코딩 및이 중요 한 이유는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="363f5-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="363f5-106">VSCode 버퍼로 문자 입력 문자열을 사용자와 읽기/쓰기 파일 시스템에 바이트 블록 간의 인터페이스를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="363f5-107">VSCode는 파일을 저장 하면 텍스트 인코딩 이렇게 하려면 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-107">When VSCode saves a file, it uses a text encoding to do this.</span></span>

<span data-ttu-id="363f5-108">마찬가지로, PowerShell 스크립트를 실행 하는 경우 파일의 바이트 문자를 PowerShell 프로그램 파일을 다시 만드는 데 변환 해야 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="363f5-109">VSCode는 파일을 기록 하 고 PowerShell 파일을 읽고 있으므로 동일한 인코딩 시스템을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="363f5-110">이 프로세스는 PowerShell 스크립트를 구문 분석 됩니다. *바이트* -> *자* -> *토큰*  ->   *추상 구문 트리* -> *실행*합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="363f5-111">VSCode 및 PowerShell 모두 합당 한 기본 인코딩 구성으로 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="363f5-112">그러나 PowerShell Core (v6.x)의 릴리스를 사용 하 여 PowerShell에서 사용 되는 기본 인코딩을 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="363f5-113">VSCode 및 PowerShell 설정을 구성 해야 할 때 PowerShell 또는 PowerShell 확장을 사용 하 여 VSCode에서 문제가 되도록 제대로 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="363f5-114">인코딩 문제의 일반적인 원인</span><span class="sxs-lookup"><span data-stu-id="363f5-114">Common causes of encoding issues</span></span>

<span data-ttu-id="363f5-115">인코딩 문제 VSCode 또는 스크립트 파일의 인코딩을 해도 PowerShell의 필요한 인코딩 일치 하지 않는 경우에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="363f5-116">파일 인코딩을 자동으로 결정 하는 PowerShell에 대 한 방법이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="363f5-117">에 없는 문자를 사용 하는 경우 문제를 인코딩 할 가능성이 더 합니다 [7 비트 ASCII 문자 집합](https://ascii.cl/)합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="363f5-118">예:</span><span class="sxs-lookup"><span data-stu-id="363f5-118">For example:</span></span>

- <span data-ttu-id="363f5-119">악센트 부호가 있는 라틴어 문자 (`É`, `ü`)</span><span class="sxs-lookup"><span data-stu-id="363f5-119">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="363f5-120">비 라틴 문자 처럼 키릴 자모 (`Д`, `Ц`)</span><span class="sxs-lookup"><span data-stu-id="363f5-120">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="363f5-121">Han 중국어 (`脚`, `本`)</span><span class="sxs-lookup"><span data-stu-id="363f5-121">Han Chinese (`脚`, `本`)</span></span>

<span data-ttu-id="363f5-122">인코딩 문제에 대 한 일반적인 원인은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-122">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="363f5-123">VSCode 및 PowerShell 인코딩의 기본값에서 변경 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-123">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="363f5-124">PowerShell 5.1 및 기본 아래 인코딩입니다는 VSCode의 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-124">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="363f5-125">다른 편집기가 열리고 새 인코딩으로 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-125">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="363f5-126">ISE를 사용 하 여 자주 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-126">This often happens with the ISE.</span></span>
- <span data-ttu-id="363f5-127">파일 어떤 VSCode 또는 PowerShell에서 예상 하는 다른 인코딩을 소스 제어에 체크 인 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-127">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="363f5-128">이 공동 작업자 편집기를 사용 하 여 서로 다른 인코딩 구성을 사용 하는 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-128">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="363f5-129">인코딩 문제 경우를 구별 하는 방법</span><span class="sxs-lookup"><span data-stu-id="363f5-129">How to tell when you have encoding issues</span></span>

<span data-ttu-id="363f5-130">종종 인코딩 오류 스크립트에서 오류를 구문 분석 하는 대로 직접 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-130">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="363f5-131">스크립트에 이상한 문자 시퀀스를 찾아야 하는 경우이 문제를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-131">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="363f5-132">대시-아래 예제에서는 (`–`) 문자로 표시 `â€“`:</span><span class="sxs-lookup"><span data-stu-id="363f5-132">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="363f5-133">VSCode 인코딩합니다 문자 때문에이 문제가 발생 `–` u t F-8 바이트와 `0xE2 0x80 0x93`합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-133">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="363f5-134">이러한 바이트가 Windows-1252로 디코딩, 문자로 해석 되기 `â€“`합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-134">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="363f5-135">표시 될 수 있는 몇 가지 이상한 문자 시퀀스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-135">Some strange character sequences that you might see include:</span></span>

- <span data-ttu-id="363f5-136">`â€“` 대신 `–`</span><span class="sxs-lookup"><span data-stu-id="363f5-136">`â€“` instead of `–`</span></span>
- <span data-ttu-id="363f5-137">`â€”` 대신 `—`</span><span class="sxs-lookup"><span data-stu-id="363f5-137">`â€”` instead of `—`</span></span>
- <span data-ttu-id="363f5-138">`Ã„2` 대신 `Ä`</span><span class="sxs-lookup"><span data-stu-id="363f5-138">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="363f5-139">`Â` 대신 ` ` (줄 바꿈하지 않는 공백)</span><span class="sxs-lookup"><span data-stu-id="363f5-139">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="363f5-140">`Ã©` 대신 `é`</span><span class="sxs-lookup"><span data-stu-id="363f5-140">`Ã©` instead of `é`</span></span>

<span data-ttu-id="363f5-141">이 유용한 [참조](https://www.i18nqa.com/debug/utf8-debug.html) u t F-8/Windows-1252 인코딩 문제를 나타내는 일반적인 패턴을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-141">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="363f5-142">VSCode에서 PowerShell 확장 인코딩을 사용 하 여 상호 작용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="363f5-142">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="363f5-143">PowerShell 확장 스크립트는 여러 가지 방법으로에서 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-143">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="363f5-144">VSCode에서 스크립트를 편집 하면 내용은 VSCode에서 확장 프로그램에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-144">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="363f5-145">합니다 [언어 서버 프로토콜][] u t F-8이이 콘텐츠를 전송 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-145">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="363f5-146">따라서 잘못 된 인코딩이 가져오려는 확장에 대 한 가능한 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-146">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="363f5-147">스크립트는 통합 콘솔에서 직접 실행 되 면 읽기 파일에서 PowerShell에서 직접.</span><span class="sxs-lookup"><span data-stu-id="363f5-147">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="363f5-148">PowerShell의 인코딩 VSCode의 다를 경우 수 문제가 여기 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-148">If PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="363f5-149">VSCode에서 열려 있는 스크립트 VSCode에서 열려 있지 않은 다른 스크립트를 참조 하는 경우 확장 파일 시스템에서 해당 스크립트의 콘텐츠를 로드로 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-149">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="363f5-150">PowerShell 확장 u t F-8 인코딩, 기본적으로 사용 되지만 사용 [바이트 순서 표시가][], 또는 BOM에 검색 기능이 올바른 인코딩을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-150">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="363f5-151">BOM 없는 형식의 인코딩을 가정 하는 경우 문제가 발생 (같은 [utf-8][] BOM을 사용 하 여 및 [Windows-1252][]).</span><span class="sxs-lookup"><span data-stu-id="363f5-151">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="363f5-152">PowerShell 확장 기본값은 u t F-8입니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-152">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="363f5-153">확장은 VSCode의 인코딩 설정을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-153">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="363f5-154">자세한 내용은 [#824 발급](https://github.com/Microsoft/vscode/issues/824)합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-154">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="363f5-155">올바른 인코딩 선택</span><span class="sxs-lookup"><span data-stu-id="363f5-155">Choosing the right encoding</span></span>

<span data-ttu-id="363f5-156">여러 시스템 및 응용 프로그램 마다 다른 인코딩을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-156">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="363f5-157">.NET Standard에 Linux 분야에는 웹에서 u t F-8는 이제 기준 인코딩입니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-157">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="363f5-158">많은.NET Framework 응용 프로그램 사용 [utf-16][]합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-158">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="363f5-159">기록을 위해가 "Unicode" 라고에 이제 이라는 용어를 광범위 [표준](https://en.wikipedia.org/wiki/Unicode) utf-8 및 u t F-16을 모두 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-159">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="363f5-160">Windows에서 유니코드는 많은 네이티브 응용 프로그램 계속 기본적으로 Windows-1252를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-160">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="363f5-161">유니코드 인코딩도의 개념이 바이트 순서 표시 (BOM).</span><span class="sxs-lookup"><span data-stu-id="363f5-161">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="363f5-162">텍스트를 사용 하 여 인코딩을 디코더를 구별 하는 텍스트의 시작 부분에 Bom이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-162">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="363f5-163">멀티 바이트 인코딩은 BOM 수도 나타냅니다 [엔디언](https://en.wikipedia.org/wiki/Endianness) 인코딩.</span><span class="sxs-lookup"><span data-stu-id="363f5-163">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="363f5-164">Bom은 거의 텍스트는 유니코드 BOM이 있는 경우 적절 한 추측을 허용 하 고 유니코드가 아닌 텍스트에서 발생 하는 바이트 수 있도록 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-164">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="363f5-165">Bom은 선택 사항 하는 해당 도입은 Linux 분야에서 인기 있는 u t F-8의 신뢰할 수 있는 규칙을 모든 곳에서 사용 되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-165">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="363f5-166">대부분의 Linux 응용 프로그램 텍스트 입력 u t F-8에서 인코딩 되는 것을 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-166">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="363f5-167">대부분의 Linux 응용 프로그램 인식을 BOM을 제대로 처리를 하는 동안 숫자 하지 해당 응용 프로그램을 사용 하 여 조작 하는 텍스트의 아티팩트에 선행 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-167">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="363f5-168">**따라서 다음 작업을 수행하세요**:</span><span class="sxs-lookup"><span data-stu-id="363f5-168">**Therefore**:</span></span>

- <span data-ttu-id="363f5-169">Windows 응용 프로그램 및 Windows PowerShell 사용 하 여 주로 작업 하는 경우 BOM 또는 u t F-16을 사용 하 여 u t F-8과 같은 인코딩을 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-169">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="363f5-170">플랫폼에서 작업 하는 경우 BOM 사용 하 여 u t F-8이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-170">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="363f5-171">Linux 관련 상황에서 주로 작업 하는 경우 BOM 없이 u t F-8이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-171">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="363f5-172">Windows-1252 및 라틴어-1은 가능 하면 피해 야 하는 기본적으로 레거시 인코딩.</span><span class="sxs-lookup"><span data-stu-id="363f5-172">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="363f5-173">그러나 일부 이전 Windows 응용 프로그램 에서도 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-173">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="363f5-174">스크립트 서명에 주목할 만한 이기도 [인코딩 종속](https://github.com/PowerShell/PowerShell/issues/3466), 다시 서명 해야 서명 된 스크립트에서 인코딩을의 변경을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-174">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="363f5-175">VSCode를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-175">Configuring VSCode</span></span>

<span data-ttu-id="363f5-176">VSCode의 기본 인코딩은 BOM 없이 u t F-8입니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-176">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="363f5-177">설정할 [VSCode의 인코딩][]VSCode 설정으로 이동 (<kbd>Ctrl<kbd>+</kbd>를</kbd>) 설정 및는 `"files.encoding"` 설정:</span><span class="sxs-lookup"><span data-stu-id="363f5-177">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl<kbd>+</kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="363f5-178">몇 가지 가능한 값은:</span><span class="sxs-lookup"><span data-stu-id="363f5-178">Some possible values are:</span></span>

- <span data-ttu-id="363f5-179">`utf8`: [UTF-8] BOM 없이</span><span class="sxs-lookup"><span data-stu-id="363f5-179">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="363f5-180">`utf8bom`: [UTF-8] BOM을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="363f5-180">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="363f5-181">`utf16le`: Little endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="363f5-181">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="363f5-182">`utf16be`: Big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="363f5-182">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="363f5-183">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="363f5-183">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="363f5-184">가져와야 드롭다운이 GUI 뷰에서 보거나 JSON에서에 대 한 완성 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-184">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="363f5-185">또한 가능한 경우 인코딩 자동 검색에 다음을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-185">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="363f5-186">모든 파일 형식에 영향을 하기 위해 이러한 설정을 사용 하지 않으려는 경우 VSCode 언어별 구성을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-186">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="363f5-187">설정에 배치 하 여 언어별 설정 만들기는 `[<language-name>]` 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-187">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="363f5-188">예:</span><span class="sxs-lookup"><span data-stu-id="363f5-188">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="363f5-189">PowerShell 구성</span><span class="sxs-lookup"><span data-stu-id="363f5-189">Configuring PowerShell</span></span>

<span data-ttu-id="363f5-190">PowerShell의 기본 인코딩 버전에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-190">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="363f5-191">PowerShell 6 +에서 기본 인코딩은 모든 플랫폼에서 BOM 없는 utf-8입니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-191">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="363f5-192">Windows PowerShell에서 기본 인코딩은 일반적으로 Windows-1252와의 확장인 [latin-1][], ISO 8859-1 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-192">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="363f5-193">PowerShell 5 이상에서이 사용 하 여 기본 인코딩을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-193">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="363f5-194">다음 [스크립트](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) BOM 없이 스크립트에 대해 유추 하 여 PowerShell 세션을 인코딩 항목을 확인 하기 위해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-194">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

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

<span data-ttu-id="363f5-195">보다 일반적으로 프로필 설정을 사용 하 여 지정 된 인코딩을 사용 하려면 PowerShell을 구성 하는 것이 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-195">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="363f5-196">다음 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="363f5-196">See the following articles:</span></span>

- <span data-ttu-id="363f5-197">[@mklement0][stackoverflow PowerShell 인코딩에 대 한 응답](https://stackoverflow.com/a/40098904)합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-197">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="363f5-198">[@rkeithhill][PowerShell에서 BOM 없는 utf-8 입력을 처리 하는 방법에 대 한 블로그 게시물](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/)합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-198">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="363f5-199">특정 입력 인코딩을 사용 하려면 PowerShell을 적용할는 것이 불가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-199">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="363f5-200">PowerShell 5.1 및 기본적으로 Windows-1252 인코딩은 BOM이 있으면 아래.</span><span class="sxs-lookup"><span data-stu-id="363f5-200">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="363f5-201">상호 운용성을 위해 BOM 사용 하 여 유니코드 형식으로 스크립트를 저장 하는 것이 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-201">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="363f5-202">다른 도구는 터치 PowerShell 스크립트 인코딩 선택 항목에 따라 달라질 수 있습니다 또는 다른 인코딩으로 스크립트를 다시 인코딩할 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-202">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="363f5-203">기존 스크립트</span><span class="sxs-lookup"><span data-stu-id="363f5-203">Existing scripts</span></span>

<span data-ttu-id="363f5-204">파일 시스템에 이미 있는 스크립트를 새 선택 인코딩을 다시 인코딩할 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-204">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="363f5-205">아래쪽 막대의 VSCode에서 u t F-8 레이블이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-205">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="363f5-206">클릭 하 여 작업 모음을 열고 선택 **인코딩하여 저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-206">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="363f5-207">이제 해당 파일에 대 한 새 인코딩을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-207">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="363f5-208">참조 [VSCode의 인코딩][] 전체 지침에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-208">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="363f5-209">여러 파일을 다시 인코딩하는 경우에 다음 스크립트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-209">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="363f5-210">PowerShell ISE(통합 스크립팅 환경)</span><span class="sxs-lookup"><span data-stu-id="363f5-210">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="363f5-211">또한 PowerShell ISE를 사용 하 여 스크립트를 편집 하면 해당 인코딩 설정을 동기화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-211">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="363f5-212">ISE BOM을 적용 해야 하지만 또한 리플렉션을 사용 하 여 [인코딩을 설정](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/)합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-212">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="363f5-213">신생 업체 간에 유지 하지 않습니다.이 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-213">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="363f5-214">원본 제어 소프트웨어</span><span class="sxs-lookup"><span data-stu-id="363f5-214">Source control software</span></span>

<span data-ttu-id="363f5-215">Git와 같은 일부 원본 제어 도구 인코딩을 무시합니다 git에는 방금 바이트 수를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-215">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="363f5-216">다른 TFS 또는 Mercurial, 같은 행위입니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-216">Others, like TFS or Mercurial, may not.</span></span> <span data-ttu-id="363f5-217">Git 기반 도구 일부 텍스트를 디코딩 의존 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-217">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="363f5-218">이 경우 다음을 확인 합니다</span><span class="sxs-lookup"><span data-stu-id="363f5-218">When this is the case, make sure you:</span></span>

- <span data-ttu-id="363f5-219">텍스트 인코딩을 VSCode 구성과 일치 하도록 원본 제어에 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-219">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="363f5-220">모든 파일 관련 인코딩 형식으로 원본 제어에 체크 인을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-220">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="363f5-221">변경 내용을 원본 제어를 통해 받은 인코딩을에 주의 하십시오.</span><span class="sxs-lookup"><span data-stu-id="363f5-221">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="363f5-222">이 키 기호를 변경 하지만 (하는데 때문에 바이트 문자를 하지 않은) 변경 된 것으로 보이지 나타내는 차이입니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-222">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="363f5-223">협력자 환경</span><span class="sxs-lookup"><span data-stu-id="363f5-223">Collaborators' environments</span></span>

<span data-ttu-id="363f5-224">소스 제어를 구성 하는 데 기반으로 공유 하는 파일에서 공동 PowerShell 파일을 다시 인코딩하여 인코딩을 재정의 하는 설정이 없는를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-224">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="363f5-225">다른 프로그램</span><span class="sxs-lookup"><span data-stu-id="363f5-225">Other programs</span></span>

<span data-ttu-id="363f5-226">읽거나 PowerShell 스크립트를 작성 하는 다른 프로그램이 인코딩합니다 다시 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-226">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="363f5-227">몇 가지 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-227">Some examples are:</span></span>

- <span data-ttu-id="363f5-228">클립보드를 사용 하 여 복사 하 여 스크립트를 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-228">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="363f5-229">다음은 같은 시나리오에서 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-229">This is common in scenarios like:</span></span>
  - <span data-ttu-id="363f5-230">VM에 스크립트 복사</span><span class="sxs-lookup"><span data-stu-id="363f5-230">Copying a script into a VM</span></span>
  - <span data-ttu-id="363f5-231">전자 메일 또는 웹 페이지에서 스크립트를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-231">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="363f5-232">Microsoft Word 나 PowerPoint 문서 안팎으로 스크립트를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-232">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="363f5-233">다른 텍스트 편집기와 같은:</span><span class="sxs-lookup"><span data-stu-id="363f5-233">Other text editors, such as:</span></span>
  - <span data-ttu-id="363f5-234">메모장</span><span class="sxs-lookup"><span data-stu-id="363f5-234">Notepad</span></span>
  - <span data-ttu-id="363f5-235">vim</span><span class="sxs-lookup"><span data-stu-id="363f5-235">vim</span></span>
  - <span data-ttu-id="363f5-236">다른 PowerShell 스크립트 편집기</span><span class="sxs-lookup"><span data-stu-id="363f5-236">Any other PowerShell script editor</span></span>
- <span data-ttu-id="363f5-237">텍스트와 같은 유틸리티를 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-237">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="363f5-238">PowerShell 리디렉션 연산자와 같은 `>` 및 `>>`</span><span class="sxs-lookup"><span data-stu-id="363f5-238">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="363f5-239">와 같은 전송 프로그램 파일:</span><span class="sxs-lookup"><span data-stu-id="363f5-239">File transfer programs, like:</span></span>
  - <span data-ttu-id="363f5-240">스크립트를 다운로드 하는 경우 웹 브라우저</span><span class="sxs-lookup"><span data-stu-id="363f5-240">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="363f5-241">파일 공유</span><span class="sxs-lookup"><span data-stu-id="363f5-241">A file share</span></span>

<span data-ttu-id="363f5-242">이러한 도구 중 일부 텍스트가 아닌 바이트 단위로 처리 하지만 다른 인코딩 구성을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-242">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="363f5-243">인코딩을 구성 해야 하는 경우 이러한 문제를 방지 하기 위해 인코딩을 편집기와 동일 하 게 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-243">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="363f5-244">다른 리소스를 PowerShell에서 인코딩</span><span class="sxs-lookup"><span data-stu-id="363f5-244">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="363f5-245">몇 가지 다른 유용한 게시물 인코딩 및 PowerShell에서 인코딩 구성 읽기 만한 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-245">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="363f5-246">[@mklement0][stackoverflow PowerShell 인코딩의 요약](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="363f5-246">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="363f5-247">이전 문제 vscode-인코딩 문제에 대 한 PowerShell에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="363f5-247">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="363f5-248">#1308</span><span class="sxs-lookup"><span data-stu-id="363f5-248">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="363f5-249">#1628</span><span class="sxs-lookup"><span data-stu-id="363f5-249">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="363f5-250">#1680</span><span class="sxs-lookup"><span data-stu-id="363f5-250">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="363f5-251">#1744</span><span class="sxs-lookup"><span data-stu-id="363f5-251">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="363f5-252">#1751</span><span class="sxs-lookup"><span data-stu-id="363f5-252">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="363f5-253">클래식 *Joel on Software* 유니코드에 대 한 작성</span><span class="sxs-lookup"><span data-stu-id="363f5-253">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="363f5-254">.NET Standard의 인코딩</span><span class="sxs-lookup"><span data-stu-id="363f5-254">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[바이트 순서 표시가]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[언어 서버 프로토콜]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[VSCode의 인코딩]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
