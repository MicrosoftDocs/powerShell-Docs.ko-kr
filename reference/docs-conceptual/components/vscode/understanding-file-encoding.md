---
title: VSCode 및 PowerShell에서 파일 인코딩 이해
description: VSCode 및 PowerShell에서 파일 인코딩 구성
ms.date: 02/28/2019
ms.openlocfilehash: ec06d8f5d446a92e6cd9d2d70b11260d1d0afda8
ms.sourcegitcommit: 396509cd0d415acc306b68758b6f833406e26bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58320407"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>VSCode 및 PowerShell에서 파일 인코딩 이해

VS Code를 사용하여 PowerShell 스크립트를 편집할 때 올바른 문자 인코딩 형식을 사용하여 파일을 저장해야 합니다.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>파일 인코딩의 정의 및 중요한 이유는 무엇인가요?

VSCode는 버퍼에 사람이 입력한 문자의 문자열과 파일 시스템에 대한 바이트의 읽기/쓰기 블록 간의 인터페이스를 관리합니다. VSCode가 파일을 저장할 때 텍스트 인코딩을 사용하여 해당 작업을 수행합니다.

마찬가지로, PowerShell이 스크립트를 실행할 때 파일의 바이트를 문자로 변환하여 파일을 PowerShell 프로그램으로 다시 구성해야 합니다. VSCode가 파일을 작성하고 PowerShell이 파일을 읽게 되므로 둘 다 동일한 인코딩 시스템을 사용해야 합니다. PowerShell 스크립트를 구문 분석하는 이 프로세스는 다음과 같은 순서로 이루어집니다. *바이트* -> *문자* -> *토큰* -> *추상 구문 트리* -> *실행*

VSCode 및 PowerShell은 모두 적절한 기본 인코딩 구성으로 설치됩니다. 그러나 PowerShell에서 사용되는 기본 인코딩이 PowerShell Core(v6.x)의 릴리스에서 변경되었습니다. VSCode에서 PowerShell 또는 PowerShell 확장을 사용할 때 문제가 발생하지 않도록 하려면 VSCode 및 PowerShell 설정을 제대로 구성해야 합니다.

## <a name="common-causes-of-encoding-issues"></a>인코딩 문제의 일반적인 원인

VSCode를 인코딩하거나 스크립트 파일이 예상되는 PowerShell 인코딩과 일치하지 않는 경우에 인코딩 문제가 발생합니다. PowerShell이 파일 인코딩을 자동으로 결정할 수 있는 방법이 없습니다.

[7비트 ASCII 문자 세트](https://ascii.cl/)에 포함되지 않는 문자를 사용할 때 인코딩 문제가 발생할 가능성이 더 높습니다. 예:

- 악센트 부호가 있는 라틴어 문자(`É`, `ü`)
- 키릴 자모와 같은 비라틴어 문자(`Д`, `Ц`)
- 중국어 한자(`脚`, `本`)

인코딩 문제에 대한 일반적인 원인은 다음과 같습니다.

- VSCode 및 PowerShell 인코딩의 기본값은 변경되지 않았습니다. PowerShell 5.1 이하의 경우 기본 인코딩은 VSCode와 다릅니다.
- 다른 편집기가 열리고 새 인코딩으로 파일을 덮어씁니다. 이 문제는 ISE를 사용하는 경우에 자주 발생합니다.
- 파일이 VSCode 또는 PowerShell에서 예상하는 것과 다른 인코딩으로 소스 제어에 체크 인되었습니다. 공동 작업자가 다른 인코딩 구성에서 편집기를 사용할 때 발생할 수 있습니다.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>인코딩 문제가 발생하는 경우를 구별하는 방법

종종 인코딩 오류는 스크립트에서 구문 분석 오류로 표시됩니다. 스크립트에서 이상한 문자 시퀀스를 찾으면 이 경우에 문제가 발생할 수 있습니다. 아래 예제에서는 대시 부호(`–`)가 `â€“` 문자로 표시됩니다.

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

VSCode가 UTF-8인 `–` 문자를 `0xE2 0x80 0x93` 바이트로 인코딩하기 때문에 이 문제가 발생합니다.
이러한 바이트가 Windows-1252로 디코딩되면 `â€“` 문자로 해석됩니다.

표시될 수 있는 몇 가지 이상한 문자 시퀀스는 다음과 같습니다.

<!-- markdownlint-disable MD038 -->
- `â€“` 대신 `–`
- `â€”` 대신 `—`
- `Ã„2` 대신 `Ä`
- ` `(줄 바꿈하지 않는 공백) 대신 `Â`
- `Ã©` 대신 `é`
<!-- markdownlint-enable MD038 -->

이 유용한 [참조](https://www.i18nqa.com/debug/utf8-debug.html)에서는 UTF-8/Windows-1252 인코딩 문제를 나타내는 일반적인 패턴을 나열합니다.

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>VSCode에서 PowerShell 확장이 인코딩과 상호 작용하는 방법

PowerShell 확장은 다음과 같은 여러 가지 방법으로 스크립트와 상호 작용합니다.

1. VSCode에서 스크립트를 편집하면 내용은 VSCode에 의해 확장 프로그램에 전송됩니다. [언어 서버 프로토콜][]은 이 내용이 UTF-8로 전송되도록 지정합니다. 따라서 확장 프로그램이 잘못 인코딩될 수는 없습니다.
2. 스크립트가 통합 콘솔에서 직접 실행되면 PowerShell이 직접 파일을 읽게 됩니다. PowerShell의 인코딩이 VSCode와 다를 경우 여기에서 문제가 발생할 수 있습니다.
3. VSCode에서 열려 있는 스크립트가 VSCode에서 열려 있지 않은 다른 스크립트를 참조하는 경우 확장 프로그램은 파일 시스템에서 해당 스크립트의 내용을 로드하도록 대체됩니다. PowerShell 확장은 UTF-8 인코딩을 기본값으로 지정하지만 [바이트 순서 표시][](또는 BOM) 검색 기능을 사용하여 올바른 인코딩을 선택할 수도 있습니다.

BOM이 없는 형식(예: BOM을 포함하지 않는 [UTF-8][] 및 [Windows-1252][])으로 인코딩한다고 가정하는 경우 이 문제가 발생합니다.
PowerShell 확장은 UTF-8을 기본값으로 지정합니다. 확장 프로그램은 VSCode의 인코딩 설정을 변경할 수 없습니다.
자세한 내용은 [문제 #824](https://github.com/Microsoft/vscode/issues/824)를 참조하세요.

## <a name="choosing-the-right-encoding"></a>맞는 인코딩 선택

여러 시스템 및 애플리케이션마다 다른 인코딩을 사용할 수 있습니다.

- .NET 표준, 웹 및 Linux 분야에서 UTF-8은 이제 가장 많이 사용되는 인코딩입니다.
- 다수의 .NET Framework 애플리케이션이 [UTF-16][]을 사용하고 있습니다. 역사적 이유로 인해 UTF-8 및 UTF-16을 모두 포함하는 광범위한 [표준](https://en.wikipedia.org/wiki/Unicode)을 의미하는 "Unicode"라고도 합니다.
- Windows에서 유니코드보다 앞선 많은 네이티브 애플리케이션이 기본적으로 계속 Windows-1252를 사용하고 있습니다.

유니코드 인코딩에는 BOM(바이트 순서 표시)라는 개념도 포함됩니다. BOM은 텍스트에서 사용하는 인코딩을 디코더에 알려주기 위해 텍스트의 시작 부분에 표시됩니다. 멀티바이트 인코딩의 경우 BOM은 인코딩의 [엔디언](https://en.wikipedia.org/wiki/Endianness)을 나타내기도 합니다. BOM은 유니코드가 아닌 텍스트에서 거의 표시되지 않는 바이트로 설계되었으므로 BOM이 있는 경우 텍스트가 유니코드라고 적절히 추측할 수 있습니다.

UTF-8이라는 신뢰할 수 있는 규칙이 어디서나 사용되기 때문에 BOM은 선택 사항이며 Linux 분야에서 널리 사용되지 않습니다. 대부분의 Linux 애플리케이션에서는 텍스트 입력이 UTF-8로 인코딩된다고 가정합니다. 대부분의 Linux 애플리케이션에서는 BOM을 제대로 인식하고 처리하지만 일부는 그렇지 않으므로 텍스트에서 해당 애플리케이션으로 조작된 아티팩트가 발생합니다.

**따라서 다음 작업을 수행하세요**:

- 주로 Windows 애플리케이션 및 Windows PowerShell으로 작업하는 경우 BOM이 포함된 UTF-8 또는 UTF-16과 같은 인코딩을 사용하는 것이 좋습니다.
- 플랫폼에서 작업하는 경우 BOM이 포함된 UTF-8을 사용하는 것이 좋습니다.
- Linux 관련 컨텍스트에서 주로 작업하는 경우 BOM이 포함되지 않은 UTF-8을 사용하는 것이 좋습니다.
- Windows-1252 및 라틴어-1은 가능하면 피해야 하는 기본적으로 레거시 인코딩입니다.
  그러나 몇 가지 이전 Windows 애플리케이션이 사용할 수 있습니다.
- 스크립트 서명은 [인코딩 종속](https://github.com/PowerShell/PowerShell/issues/3466)적입니다. 즉, 서명된 스크립트에서 인코딩을 변경하면 다시 서명해야 합니다.

## <a name="configuring-vscode"></a>VSCode 구성

VSCode의 기본 인코딩은 BOM이 포함되지 않은 UTF-8입니다.

[VSCode의 인코딩][]을 설정하려면 VSCode 설정(<kbd>Ctrl<kbd>+</kbd>,</kbd>)으로 이동하고 `"files.encoding"` 설정을 설정하세요.

```json
"files.encoding": "utf8bom"
```

가능한 값의 일부는 다음과 같습니다.

- `utf8`: BOM이 포함되지 않은 [UTF-8]
- `utf8bom`: BOM이 포함된 [UTF-8]
- `utf16le`: Little endian [UTF-16]
- `utf16be`: Big endian [UTF-16]
- `windows1252`: [Windows-1252]

GUI 보기로 이에 대한 드롭다운 또는 JSON 보기로 이에 대한 완성을 가져와야 합니다.

가능하면 인코딩을 자동으로 검색하기 위해 다음을 추가할 수도 있습니다.

```json
"files.autoGuessEncoding": true
```

이러한 설정이 모든 파일 형식에 영향을 주지 않으려는 경우 VSCode에서 언어별 구성을 허용할 수도 있습니다. `[<language-name>]` 필드에서 설정을 지정하여 언어별 설정을 만듭니다. 예:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>PowerShell 구성

PowerShell의 기본 인코딩은 버전에 따라 달라집니다.

- PowerShell 6+에서 기본 인코딩은 모든 플랫폼에서 BOM를 포함하지 않는 UTF-8입니다.
- Windows PowerShell에서 기본 인코딩은 일반적으로 Windows-1252이고, [라틴어-1][]의 확장은 ISO 8859-1이라고도 합니다.

PowerShell 5 이상에서는 다음을 포함한 기본 인코딩을 확인할 수 있습니다.

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

다음 [스크립트](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e)를 사용하여 PowerShell 세션이 BOM을 포함하지 않은 스크립트에서 유추한 인코딩을 확인할 수 있습니다.

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

프로필 설정을 사용하여 보다 일반적으로 지정된 인코딩을 사용히도록 PowerShell을 구성할 수 있습니다. 다음 문서를 참조하세요.

- [@mklement0][stackoverflow PowerShell 인코딩에 대 한 응답](https://stackoverflow.com/a/40098904)합니다.
- [PowerShell에서 BOM을 포함하지 않는 UTF-8 입력을 처리하는 방법에 대한 @rkeithhill]의 [블로그 게시물](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/)

PowerShell이 특정 입력 인코딩을 사용하도록 강제할 수 없습니다. PowerShell 5.1 이하에서는 BOM이 없으면 Windows-1252 인코딩을 기본값으로 지정합니다. 상호 운용성을 위해 BOM을 포함한 유니코드 형식으로 스크립트를 저장하는 것이 좋습니다.

> [!IMPORTANT]
> PowerShell 스크립트에 관련된 다른 도구가 인코딩 선택에 따라 달라지거나 다른 인코딩으로 스크립트를 다시 인코딩할 수도 있습니다.

### <a name="existing-scripts"></a>기존 스크립트

파일 시스템에 이미 있는 스크립트를 새로 선택된 인코딩으로 다시 인코딩해야 합니다. VSCode의 아래쪽 막대에서 UTF-8 레이블이 표시됩니다. 해당 항목을 클릭하여 작업 모음을 열고 **인코딩하여 저장**을 선택합니다. 이제 해당 파일에서 새 인코딩을 선택할 수 있습니다. 전체 지침은 [VSCode의 인코딩][]을 참조하세요.

여러 파일을 다시 인코딩해야 하는 경우 다음 스크립트를 사용하면 됩니다.

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>PowerShell ISE(통합 스크립팅 환경)

PowerShell ISE를 사용하여 스크립트를 편집하는 경우 거기에서 인코딩 설정을 동기화해야 합니다.

ISE는 BOM을 적용해야 하지만 리플렉션을 사용하여 [인코딩을 설정](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/)할 수도 있습니다.
이 설정은 시작 시 유지되지 않습니다.

### <a name="source-control-software"></a>소스 제어 소프트웨어

Git와 같은 일부 소스 제어 도구는 인코딩을 무시합니다. Git는 바이트를 추적하기만 합니다.
Azure DevOps 또는 Mercurial과 같은 다른 도구는 그렇지 않습니다. 일부 Git 기반 도구도 디코딩 텍스트를 사용합니다.

이 경우에는 다음을 확인하세요.

- 소스 제어의 텍스트 인코딩이 VSCode 구성과 일치하도록 구성합니다.
- 모든 파일이 관련 인코딩으로 소스 제어에 체크 인되었는지 확인합니다.
- 소스 제어를 통해 수신된 인코딩의 변경 내용에 주의하세요. 여기서 주요 기호는 변경을 나타내는 Diff이지만 변경되지 않은 것처럼 보입니다(바이트는 변경되었지만 문자가 변경되지 않기 때문에).

### <a name="collaborators-environments"></a>공동 작업자 환경

소스 제어를 구성하려면 공유하는 파일에서 공동 작업자가 PowerShell 파일을 다시 인코딩하여 인코딩을 재정의하도록 설정하지 않았는지를 확인합니다.

### <a name="other-programs"></a>다른 프로그램

PowerShell 스크립트를 읽거나 작성하는 다른 프로그램이 해당 항목을 다시 인코딩할 수 있습니다.

몇 가지 예는 다음과 같습니다.

- 클립보드를 사용하여 스크립트를 복사하고 붙여넣습니다. 다음은 같은 시나리오에서 일반적입니다.
  - VM에 스크립트 복사
  - 이메일 또는 웹 페이지에서 스크립트 복사
  - Microsoft Word나 PowerPoint 문서에서/로 스크립트 복사
- 다음과 같은 다른 텍스트 편집기:
  - 메모장
  - vim
  - 다른 PowerShell 스크립트 편집기
- 다음과 같은 텍스트 편집 유틸리티:
  - `Get-Content`/`Set-Content`/`Out-File`
  - `>` 및 `>>`와 같은 PowerShell 리디렉션 연산자
  - `sed`/`awk`
- 다음과 같은 파일 전송 프로그램:
  - 스크립트를 다운로드하는 경우 웹 브라우저
  - 파일 공유

이러한 일부 도구는 텍스트가 아닌 바이트 단위로 처리하지만 나머지는 인코딩 구성을 제공합니다. 인코딩을 구성해야 하는 경우 이러한 문제를 방지하기 위해 인코딩하는 편집기와 동일하게 만들어야 합니다.

## <a name="other-resources-on-encoding-in-powershell"></a>PowerShell에서 인코딩할 다른 리소스

PowerShell에서 인코딩 및 인코딩 구성에 대해 읽을 만한 몇 가지 다른 유용한 게시물은 다음과 같습니다.

- [@mklement0][stackoverflow PowerShell 인코딩의 요약](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- 인코딩 문제과 관련하여 vscode-PowerShell에서 열린 이전 문제:
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [유니코드에 대한 클래식 *Joel on Software* 논평](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [.NET 표준으로 인코딩](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[라틴어-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[바이트 순서 표시]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[언어 서버 프로토콜]: https://microsoft.github.io/language-server-protocol/
[VSCode의 인코딩]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
