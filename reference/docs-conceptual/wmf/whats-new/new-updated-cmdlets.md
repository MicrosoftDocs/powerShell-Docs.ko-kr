---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: 새로 제공되거나 업데이트된 cmdlet
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147593"
---
# <a name="new-and-updated-cmdlets"></a><span data-ttu-id="e91fc-103">새로 제공되거나 업데이트된 cmdlet</span><span class="sxs-lookup"><span data-stu-id="e91fc-103">New and updated cmdlets</span></span>

<span data-ttu-id="e91fc-104">커뮤니티 피드백에 따라 새로운 cmdlet을 추가하고 기존 cmdlet을 업데이트했습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-104">We have added new and updated existing cmdlets based on feedback from the community.</span></span>

## <a name="archive-cmdlets"></a><span data-ttu-id="e91fc-105">보관 cmdlet</span><span class="sxs-lookup"><span data-stu-id="e91fc-105">Archive cmdlets</span></span>

<span data-ttu-id="e91fc-106">두 가지 새 cmdlet `Compress-Archive` 및 `Expand-Archive`를 사용하여 ZIP 파일을 압축하고 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-106">Two new cmdlets, `Compress-Archive` and `Expand-Archive`, let you compress and expand ZIP files.</span></span>

<span data-ttu-id="e91fc-107">자세한 내용은 [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) 모듈 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e91fc-107">For more information, see the [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) module documentation.</span></span>

## <a name="catalog-cmdlets"></a><span data-ttu-id="e91fc-108">카탈로그 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e91fc-108">Catalog Cmdlets</span></span>

<span data-ttu-id="e91fc-109">두 개의 새로운 cmdlet을 Microsoft.PowerShell.Security 모듈에 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-109">Two new cmdlets have been added in the Microsoft.PowerShell.Security module.</span></span>

- [<span data-ttu-id="e91fc-110">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="e91fc-110">New-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [<span data-ttu-id="e91fc-111">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="e91fc-111">Test-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

<span data-ttu-id="e91fc-112">이 두 가지 cmdlet은 Windows 카탈로그 파일을 생성하고 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-112">These generate and validate Windows catalog files.</span></span>

## <a name="clipboard-cmdlets"></a><span data-ttu-id="e91fc-113">클립보드 cmdlet</span><span class="sxs-lookup"><span data-stu-id="e91fc-113">Clipboard cmdlets</span></span>

<span data-ttu-id="e91fc-114">`Get-Clipboard` 및 `Set-Clipboard`를 사용하면 Windows PowerShell 세션 간에 콘텐츠를 더 쉽게 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-114">`Get-Clipboard` and `Set-Clipboard` make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="e91fc-115">클립보드 cmdlet은 이미지, 오디오 파일, 파일 목록 및 텍스트를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-115">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

<span data-ttu-id="e91fc-116">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e91fc-116">For more information, see:</span></span>

- [<span data-ttu-id="e91fc-117">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="e91fc-117">Get-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [<span data-ttu-id="e91fc-118">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="e91fc-118">Set-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="e91fc-119">암호화 메시지 구문(CMS) cmdlet</span><span class="sxs-lookup"><span data-stu-id="e91fc-119">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="e91fc-120">암호화 메시지 구문 cmdlet은 [RFC5652](https://tools.ietf.org/html/rfc5652.html) 문서에 기록된 대로 메시지를 암호로 보호하기 위해 IETF 표준 형식을 사용하는 콘텐츠의 암호화 및 암호 해독을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-120">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="e91fc-121">CMS 암호화 표준은 공개 키 암호화를 구현하는데, 여기서는 콘텐츠를 암호화하는 데 사용되는 키(‘공개 키’)와 콘텐츠를 암호 해독하는 데 사용되는 키(‘프라이빗 키’)가 구분됩니다.  </span><span class="sxs-lookup"><span data-stu-id="e91fc-121">The CMS encryption standard implements public key cryptography, where the key used to encrypt content (the *public key*) and the key used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="e91fc-122">공개 키는 광범위하게 공유할 수 있으며 중요한 데이터가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-122">Your public key can be shared widely and is not sensitive data.</span></span> <span data-ttu-id="e91fc-123">공개 키로 암호화된 모든 콘테츠는 프라이빗 키로만 암호 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-123">Any content encrypted with the public key can only be decrypted using the private key.</span></span> <span data-ttu-id="e91fc-124">자세한 내용은 [공개 키 암호화](https://en.wikipedia.org/wiki/Public-key_cryptography)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e91fc-124">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="e91fc-125">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e91fc-125">For more information see:</span></span>

- [<span data-ttu-id="e91fc-126">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="e91fc-126">Get-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [<span data-ttu-id="e91fc-127">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="e91fc-127">Protect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [<span data-ttu-id="e91fc-128">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="e91fc-128">Unprotect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

<span data-ttu-id="e91fc-129">PowerShell에서 인증서가 데이터 암호화 인증서로 식별되려면 고유 키 사용 식별자(EKU)(예: ‘코드 서명' 또는 ‘암호화된 메일’)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-129">Certificates require a unique key usage identifier (EKU), such as 'Code Signing' or 'Encrypted Mail', to identify them as data encryption certificates in PowerShell.</span></span> <span data-ttu-id="e91fc-130">인증서 공급자에서 문서 암호화 인증서를 보려면 `Get-ChildItem`의 **DocumentEncryptionCert** 동적 매개 변수를 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-130">To view document encryption certificates in the certificate provider, you can use the **DocumentEncryptionCert** dynamic parameter of `Get-ChildItem`:</span></span>

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a><span data-ttu-id="e91fc-131">문자열 콘텐츠에서 구조적 개체 추출 및 구문 분석</span><span class="sxs-lookup"><span data-stu-id="e91fc-131">Extract and parse structured objects from string content</span></span>

### <a name="convertfrom-string"></a><span data-ttu-id="e91fc-132">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="e91fc-132">ConvertFrom-String</span></span>

<span data-ttu-id="e91fc-133">새 `ConvertFrom-String` cmdlet은 다음 두 가지 모드를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-133">The new `ConvertFrom-String` cmdlet supports two modes:</span></span>

- <span data-ttu-id="e91fc-134">기본 구분 기호로 분리된 구문 분석</span><span class="sxs-lookup"><span data-stu-id="e91fc-134">Basic delimited parsing</span></span>
- <span data-ttu-id="e91fc-135">자동 생성된 예제 기반 구문 분석</span><span class="sxs-lookup"><span data-stu-id="e91fc-135">Auto generated example-driven parsing</span></span>

<span data-ttu-id="e91fc-136">기본적으로 구분 구문 분석에서는 입력을 공백으로 분할하고 결과 그룹에 속성 이름을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-136">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="e91fc-137">**UpdateTemplate** 매개 변수는 학습 알고리즘의 결과를 템플릿 파일의 설명에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-137">The **UpdateTemplate** parameter saves the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="e91fc-138">이 매개 변수는 학습 프로세스(가장 느린 단계)를 일회 비용으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-138">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="e91fc-139">인코딩된 학습 알고리즘이 포함된 템플릿에서 `ConvertFrom-String`을 실행하면 거의 즉각적입니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-139">Running `ConvertFrom-String` with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

<span data-ttu-id="e91fc-140">자세한 내용은 [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e91fc-140">For more information, see [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span></span>

### <a name="convert-string"></a><span data-ttu-id="e91fc-141">Convert-String</span><span class="sxs-lookup"><span data-stu-id="e91fc-141">Convert-String</span></span>

<span data-ttu-id="e91fc-142">`Convert-String`을 사용하여 텍스트가 어떻게 표시되는지에 대한 이전 및 이후 예제를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-142">`Convert-String` allows you to provide before and after examples of how you want text to look.</span></span> <span data-ttu-id="e91fc-143">이 cmdlet은 자동으로 텍스트 서식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-143">The cmdlet formats your text automatically.</span></span>

<span data-ttu-id="e91fc-144">자세한 내용은 [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e91fc-144">For more information, see [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span></span>

## <a name="updates-to-fileinfo-object"></a><span data-ttu-id="e91fc-145">FileInfo 개체에 대한 업데이트</span><span class="sxs-lookup"><span data-stu-id="e91fc-145">Updates to FileInfo object</span></span>

<span data-ttu-id="e91fc-146">파일 버전 정보는 잘못될 수 있습니다. 특히 파일이 패치된 경우는 더욱 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-146">File version information can be misleading, especially in cases where the file was patched.</span></span> <span data-ttu-id="e91fc-147">WMF 5.0에서는 새로운 **FileVersionRaw** 및 **ProductVersionRaw** 스크립트 속성을 **FileInfo** 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-147">WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to **FileInfo** objects.</span></span>
<span data-ttu-id="e91fc-148">다음은 powershell.exe에 대해 표시되는 속성입니다($pid는 PowerShell 프로세스의 ID로 간주).</span><span class="sxs-lookup"><span data-stu-id="e91fc-148">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a><span data-ttu-id="e91fc-149">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="e91fc-149">Format-Hex</span></span>

<span data-ttu-id="e91fc-150">`Format-Hex`를 사용하면 텍스트 또는 이진 데이터를 16진수 형식으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-150">`Format-Hex` lets you view text or binary data in hexadecimal format.</span></span>

<span data-ttu-id="e91fc-151">자세한 내용은 [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e91fc-151">For more information, see [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span></span>

## <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="e91fc-152">Get-ChildItem의 -Depth 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e91fc-152">Get-ChildItem has -Depth parameter</span></span>

<span data-ttu-id="e91fc-153">이제 `Get-ChildItem`은 **Recurse**와 함께 사용되어 재귀를 제한하는 **Depth** 매개 변수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-153">`Get-ChildItem` now has a **Depth** parameter for use with **Recurse** to limit the recursion:</span></span>

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="e91fc-154">모듈의 버전 범위 선언(1.\* 등) 지원</span><span class="sxs-lookup"><span data-stu-id="e91fc-154">Modules support for declaring version ranges (1.\*, etc)</span></span>

<span data-ttu-id="e91fc-155">이제 **MinimumVersion** 및 **MaximumVersion**을 결합하여 특정 범위 내의 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-155">You can now combine **MinimumVersion** and **MaximumVersion** to import module within specific range.</span></span> <span data-ttu-id="e91fc-156">또한 매개 변수는 와일드 카드를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-156">The parameters also support wildcards.</span></span>

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a><span data-ttu-id="e91fc-157">New-Guid</span><span class="sxs-lookup"><span data-stu-id="e91fc-157">New-Guid</span></span>

<span data-ttu-id="e91fc-158">고유 식별자에 필요한 많은 시나리오가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-158">There are many scenarios where youneed for unique identifier.</span></span> <span data-ttu-id="e91fc-159">`New-GUID` cmdlet은 새 GUID를 만드는 간단한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-159">The `New-GUID` cmdlet provides a simple way to create a new GUID.</span></span>

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a><span data-ttu-id="e91fc-160">NoNewLine 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e91fc-160">NoNewLine parameter</span></span>

<span data-ttu-id="e91fc-161">이제 `Out-File`, `Add-Content` 및 `Set-Content`는 출력 뒤에 오는 새 줄을 생략하는 새로운 **NoNewline** 스위치를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-161">`Out-File`, `Add-Content`, and `Set-Content` now have a new **NoNewline** switch which omits a new line after the output.</span></span> <span data-ttu-id="e91fc-162">예:</span><span class="sxs-lookup"><span data-stu-id="e91fc-162">For example:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

<span data-ttu-id="e91fc-163">**NoNewline**을 지정하지 않으면 각 조각이 별도의 줄에 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-163">Without **NoNewline** specified, each fragment would be on a separate line:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a><span data-ttu-id="e91fc-164">향상된 Item cmdlet을 사용하여 기호화된 링크 조작</span><span class="sxs-lookup"><span data-stu-id="e91fc-164">Interact with Symbolic links using improved Item cmdlets</span></span>

<span data-ttu-id="e91fc-165">바로 가기 링크를 지원하기 위해 Item cmdlet과 몇 가지 관련 cmdlet이 확장되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-165">The Item cmdlet and a few related cmdlets have been extended to support symbolic links.</span></span>

### <a name="symbolic-link-files"></a><span data-ttu-id="e91fc-166">바로 가기 링크 파일</span><span class="sxs-lookup"><span data-stu-id="e91fc-166">Symbolic link files</span></span>

<span data-ttu-id="e91fc-167">이 예제에서는 C:\Temp에서 $pshome\profile.ps1에 연결되는 MySymLinkFile.txt라는 새로운 바로 가기 링크 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-167">In this example, we create a new symbolic link file named MySymLinkFile.txt in C:\Temp which links to $pshome\profile.ps1.</span></span> <span data-ttu-id="e91fc-168">세 가지 예제에서 모두 동일한 결과가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-168">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a><span data-ttu-id="e91fc-169">바로 가기 링크 디렉터리</span><span class="sxs-lookup"><span data-stu-id="e91fc-169">Symbolic link directories</span></span>

<span data-ttu-id="e91fc-170">이 예제에서는 C:\Temp에서 $pshome 폴더에 연결되는 MySymLinkDir이라는 새로운 바로 가기 링크 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-170">In this example, we create a new symbolic link directory named MySymLinkDir in C:\Temp which links to the $pshome folder.</span></span> <span data-ttu-id="e91fc-171">세 가지 예제에서 모두 동일한 결과가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-171">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a><span data-ttu-id="e91fc-172">하드 링크</span><span class="sxs-lookup"><span data-stu-id="e91fc-172">Hard links</span></span>

<span data-ttu-id="e91fc-173">위에서 설명한 대로 허용되는 **경로** 및 **이름**의 동일한 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-173">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a><span data-ttu-id="e91fc-174">디렉터리 연결</span><span class="sxs-lookup"><span data-stu-id="e91fc-174">Directory junctions</span></span>

<span data-ttu-id="e91fc-175">위에서 설명한 대로 허용되는 **경로** 및 **이름**의 동일한 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-175">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a><span data-ttu-id="e91fc-176">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="e91fc-176">Get-ChildItem</span></span>

<span data-ttu-id="e91fc-177">이제 `Get-ChildItem`은 **Mode** 속성에서 'l'를 표시하여 바로 가기 링크 파일 또는 디렉터리를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-177">`Get-ChildItem` now displays an 'l' in the **Mode** property to indicate a symbolic link file or directory.</span></span>

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a><span data-ttu-id="e91fc-178">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="e91fc-178">Remove-Item</span></span>

<span data-ttu-id="e91fc-179">다른 항목 형식을 제거하는 것처럼 바로 가기 링크를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-179">Removing symbolic links works like removing any other item type.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

<span data-ttu-id="e91fc-180">**Force** 매개 변수를 사용하여 대상 디렉터리의 파일과 바로 가기 링크를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-180">Use the **Force** parameter to remove the files in the target directory and the symbolic link.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a><span data-ttu-id="e91fc-181">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="e91fc-181">New-TemporaryFile</span></span>

<span data-ttu-id="e91fc-182">경우에 따라 스크립트에서 임시 파일을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-182">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="e91fc-183">이제 `New-TemporaryFile` cmdlet으로 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-183">You can now do this with the `New-TemporaryFile` cmdlet:</span></span>

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a><span data-ttu-id="e91fc-184">PowerShell을 사용하여 네트워크 스위치 관리</span><span class="sxs-lookup"><span data-stu-id="e91fc-184">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="e91fc-185">WMF 5.0에서 도입된 네트워크 스위치 cmdlet을 사용하면 스위치, VLAN(가상 LAN) 및 기본 계층 2 네트워크 스위치 포트 구성을 Windows Server 2012 R2 로고 인증 네트워크 스위치에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-185">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="e91fc-186">이러한 cmdlet을 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-186">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="e91fc-187">다음과 같은 전역 스위치 구성:</span><span class="sxs-lookup"><span data-stu-id="e91fc-187">Global switch configuration, such as:</span></span>
  - <span data-ttu-id="e91fc-188">호스트 이름 설정</span><span class="sxs-lookup"><span data-stu-id="e91fc-188">Set host name</span></span>
  - <span data-ttu-id="e91fc-189">스위치 배너 설정</span><span class="sxs-lookup"><span data-stu-id="e91fc-189">Set switch banner</span></span>
  - <span data-ttu-id="e91fc-190">구성 유지</span><span class="sxs-lookup"><span data-stu-id="e91fc-190">Persist configuration</span></span>
  - <span data-ttu-id="e91fc-191">기능을 사용하거나 사용하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="e91fc-191">Enable or disable feature</span></span>

- <span data-ttu-id="e91fc-192">VLAN 구성:</span><span class="sxs-lookup"><span data-stu-id="e91fc-192">VLAN configuration:</span></span>
  - <span data-ttu-id="e91fc-193">VLAN 만들기 또는 제거</span><span class="sxs-lookup"><span data-stu-id="e91fc-193">Create or remove VLAN</span></span>
  - <span data-ttu-id="e91fc-194">VLAN을 사용하거나 사용하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="e91fc-194">Enable or disable VLAN</span></span>
  - <span data-ttu-id="e91fc-195">VLAN 열거</span><span class="sxs-lookup"><span data-stu-id="e91fc-195">Enumerate VLAN</span></span>
  - <span data-ttu-id="e91fc-196">VLAN의 식별 이름 설정</span><span class="sxs-lookup"><span data-stu-id="e91fc-196">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="e91fc-197">계층 2 포트 구성:</span><span class="sxs-lookup"><span data-stu-id="e91fc-197">Layer 2 port configuration:</span></span>
  - <span data-ttu-id="e91fc-198">포트 열거</span><span class="sxs-lookup"><span data-stu-id="e91fc-198">Enumerate ports</span></span>
  - <span data-ttu-id="e91fc-199">포트를 사용하거나 사용하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="e91fc-199">Enable or disable ports</span></span>
  - <span data-ttu-id="e91fc-200">포트 모드 및 속성 설정</span><span class="sxs-lookup"><span data-stu-id="e91fc-200">Set port modes and properties</span></span>
  - <span data-ttu-id="e91fc-201">포트의 트렁크 또는 액세스에 VLAN 추가 또는 연결</span><span class="sxs-lookup"><span data-stu-id="e91fc-201">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="e91fc-202">자세한 내용은 [NetworkSwitchManager](/powershell/module/networkswitchmanager/) 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e91fc-202">For more information, see the [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentation.</span></span>

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="e91fc-203">ODataUtils를 사용하여 OData 엔드포인트에 따라 PowerShell cmdlet 생성</span><span class="sxs-lookup"><span data-stu-id="e91fc-203">Generate PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="e91fc-204">ODataUtils 모듈에서는 OData를 지원하는 REST 엔드포인트에서 PowerShell cmdlet을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-204">The ODataUtils module allows generation of PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="e91fc-205">Microsoft.PowerShell.ODataUtils 모듈에는 다음 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-205">The Microsoft.PowerShell.ODataUtils module includes the following features:</span></span>

- <span data-ttu-id="e91fc-206">서버 쪽 엔드포인트와 클라이언트 쪽 사이에서 추가 정보 연결</span><span class="sxs-lookup"><span data-stu-id="e91fc-206">Channel additional information from server-side endpoint to client side.</span></span>
- <span data-ttu-id="e91fc-207">클라이언트 쪽 페이징 지원</span><span class="sxs-lookup"><span data-stu-id="e91fc-207">Client-side paging support</span></span>
- <span data-ttu-id="e91fc-208">-Select 매개 변수를 사용하여 서버 쪽 필터링</span><span class="sxs-lookup"><span data-stu-id="e91fc-208">Server-side filtering by using the -Select parameter</span></span>
- <span data-ttu-id="e91fc-209">웹 요청 헤더에 대한 지원</span><span class="sxs-lookup"><span data-stu-id="e91fc-209">Support for web request headers</span></span>

<span data-ttu-id="e91fc-210">`Export-ODataEndPointProxy` cmdlet에서 생성된 프록시 cmdlet은 **정보** 스트림의 서버 쪽 OData 엔드포인트에서 추가 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-210">The proxy cmdlets generated by the `Export-ODataEndPointProxy` cmdlet provide additional information from the server-side OData endpoint on the **Information** stream.</span></span>

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

<span data-ttu-id="e91fc-211">다음 예제에서는 최상위 제품을 검색하고 `$infoStream` 변수로 출력을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-211">In the following example, we are retrieving top product and capturing the output in the `$infoStream` variable.</span></span>

<span data-ttu-id="e91fc-212">**IncludeTotalResponseCount** 매개 변수를 지정하여 서버에서 사용할 수 있는 모든 **Product** 레코드의 총 개수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-212">By specifying **IncludeTotalResponseCount** parameter, we get the total count of all the **Product** records available on the server.</span></span>

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

<span data-ttu-id="e91fc-213">클라이언트 쪽 페이징 지원을 사용하여 서버에서 레코드를 일괄 처리로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-213">You can get the records from the server in batches using client-side paging support.</span></span> <span data-ttu-id="e91fc-214">이 방법은 네트워크를 통해 서버에서 많은 양의 데이터를 가져와야 하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-214">This is useful when you must get a large amount of data from the server over the network.</span></span>

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

<span data-ttu-id="e91fc-215">생성된 프록시 cmdlet은 클라이언트에 필요한 레코드 속성만 받는 필터로 사용되는 **Select** 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-215">The generated proxy cmdlets support the **Select** parameter that is used as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="e91fc-216">필터링은 서버에서 수행되므로 네트워크를 통해 전송되는 데이터의 양이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-216">The filtering occurs on the server, which reduces the amount of data that is transferred over the network.</span></span>

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="e91fc-217">이제 `Export-ODataEndpointProxy` cmdlet 및 이 cmdlet에서 생성된 프록시 cmdlet은 **Headers** 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-217">The `Export-ODataEndpointProxy` cmdlet, and the proxy cmdlets generated by it, now support the **Headers** parameter.</span></span> <span data-ttu-id="e91fc-218">OData 엔드포인트에 필요한 추가 정보를 채널로 보내는 데 헤더를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-218">The header can be used to channel additional information expected by the OData endpoint.</span></span>

<span data-ttu-id="e91fc-219">다음 예제에서는 구독 키가 포함된 해시 테이블이 **Headers** 매개 변수에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-219">In the following example, a hash table containing a Subscription key is provided to the **Headers** parameter.</span></span> <span data-ttu-id="e91fc-220">이 예제는 인증에 구독 키가 필요한 서비스에 대한 일반적인 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="e91fc-220">This is a typical example for services that are expecting a Subscription key for authentication.</span></span>

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
