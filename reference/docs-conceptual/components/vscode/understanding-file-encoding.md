---
title: VSCode 및 PowerShell에서 파일 인코딩 이해
description: VSCode 및 PowerShell에서 파일 인코딩 구성
ms.date: 02/28/2019
ms.openlocfilehash: f3b133b4bee7688821a5960429e2f26b69b01e12
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251479"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>VSCode 및 PowerShell에서 파일 인코딩 이해

VS Code를 사용 하 여 PowerShell 스크립트를 편집 및 만들기를 반드시 올바른 문자 인코딩 형식을 사용 하 여 파일에 저장 됩니다.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>파일 인코딩 및이 중요 한 이유는 무엇 인가요?

VSCode 버퍼로 문자 입력 문자열을 사용자와 읽기/쓰기 파일 시스템에 바이트 블록 간의 인터페이스를 관리합니다. VSCode는 파일을 저장 하면 텍스트 인코딩 이렇게 하려면 사용 합니다.

마찬가지로, PowerShell 스크립트를 실행 하는 경우 파일의 바이트 문자를 PowerShell 프로그램 파일을 다시 만드는 데 변환 해야 하 합니다. VSCode는 파일을 기록 하 고 PowerShell 파일을 읽고 있으므로 동일한 인코딩 시스템을 사용 해야 합니다. 이 프로세스는 PowerShell 스크립트를 구문 분석 됩니다. *바이트* -> *자* -> *토큰*  ->   *추상 구문 트리* -> *실행*합니다.

VSCode 및 PowerShell 모두 합당 한 기본 인코딩 구성으로 설치 됩니다. 그러나 PowerShell Core (v6.x)의 릴리스를 사용 하 여 PowerShell에서 사용 되는 기본 인코딩을 변경 되었습니다. VSCode 및 PowerShell 설정을 구성 해야 할 때 PowerShell 또는 PowerShell 확장을 사용 하 여 VSCode에서 문제가 되도록 제대로 합니다.

## <a name="common-causes-of-encoding-issues"></a>인코딩 문제의 일반적인 원인

인코딩 문제 VSCode 또는 스크립트 파일의 인코딩을 해도 PowerShell의 필요한 인코딩 일치 하지 않는 경우에 발생 합니다. 파일 인코딩을 자동으로 결정 하는 PowerShell에 대 한 방법이 없습니다.

에 없는 문자를 사용 하는 경우 문제를 인코딩 할 가능성이 더 합니다 [7 비트 ASCII 문자 집합](https://ascii.cl/)합니다. 예:

- 악센트 부호가 있는 라틴어 문자 (`É`, `ü`)
- 비 라틴 문자 처럼 키릴 자모 (`Д`, `Ц`)
- Han 중국어 (`脚`, `本`)

인코딩 문제에 대 한 일반적인 원인은 다음과 같습니다.

- VSCode 및 PowerShell 인코딩의 기본값에서 변경 되지 않았습니다. PowerShell 5.1 및 기본 아래 인코딩입니다는 VSCode의 다릅니다.
- 다른 편집기가 열리고 새 인코딩으로 파일을 덮어씁니다. ISE를 사용 하 여 자주 발생합니다.
- 파일 어떤 VSCode 또는 PowerShell에서 예상 하는 다른 인코딩을 소스 제어에 체크 인 합니다. 이 공동 작업자 편집기를 사용 하 여 서로 다른 인코딩 구성을 사용 하는 경우 발생할 수 있습니다.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>인코딩 문제 경우를 구별 하는 방법

종종 인코딩 오류 스크립트에서 오류를 구문 분석 하는 대로 직접 제공 합니다. 스크립트에 이상한 문자 시퀀스를 찾아야 하는 경우이 문제를 수 있습니다. 대시-아래 예제에서는 (`–`) 문자로 표시 `â€“`:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

VSCode 인코딩합니다 문자 때문에이 문제가 발생 `–` u t F-8 바이트와 `0xE2 0x80 0x93`합니다.
이러한 바이트가 Windows-1252로 디코딩, 문자로 해석 되기 `â€“`합니다.

표시 될 수 있는 몇 가지 이상한 문자 시퀀스는 다음과 같습니다.

- `â€“` 대신 `–`
- `â€”` 대신 `—`
- `Ã„2` 대신 `Ä`
- `Â` 대신 ` ` (줄 바꿈하지 않는 공백)
- `Ã©` 대신 `é`

이 유용한 [참조](https://www.i18nqa.com/debug/utf8-debug.html) u t F-8/Windows-1252 인코딩 문제를 나타내는 일반적인 패턴을 나열 합니다.

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>VSCode에서 PowerShell 확장 인코딩을 사용 하 여 상호 작용 하는 방법

PowerShell 확장 스크립트는 여러 가지 방법으로에서 상호 작용 합니다.

1. VSCode에서 스크립트를 편집 하면 내용은 VSCode에서 확장 프로그램에 전송 됩니다. 합니다 [언어 서버 프로토콜][] u t F-8이이 콘텐츠를 전송 하도록 지정 합니다. 따라서 잘못 된 인코딩이 가져오려는 확장에 대 한 가능한 아닙니다.
2. 스크립트는 통합 콘솔에서 직접 실행 되 면 읽기 파일에서 PowerShell에서 직접. VSCode의에서 다른 Tf PowerShell 인코딩이, 무언가 문제가 발생할 수 있는 여기입니다.
3. VSCode에서 열려 있는 스크립트 VSCode에서 열려 있지 않은 다른 스크립트를 참조 하는 경우 확장 파일 시스템에서 해당 스크립트의 콘텐츠를 로드로 대체 합니다. PowerShell 확장 u t F-8 인코딩, 기본적으로 사용 되지만 사용 [바이트 순서 표시가][], 또는 BOM에 검색 기능이 올바른 인코딩을 선택 합니다.

BOM 없는 형식의 인코딩을 가정 하는 경우 문제가 발생 (같은 [UTF-8][] BOM을 사용 하 여 및 [Windows-1252][]).
PowerShell 확장 기본값은 u t F-8입니다. 확장은 VSCode의 인코딩 설정을 변경할 수 없습니다.
자세한 내용은 [#824 발급](https://github.com/Microsoft/vscode/issues/824)합니다.

## <a name="choosing-the-right-encoding"></a>올바른 인코딩 선택

여러 시스템 및 응용 프로그램 마다 다른 인코딩을 사용할 수 있습니다.

- .NET Standard에 Linux 분야에는 웹에서 u t F-8는 이제 기준 인코딩입니다.
- 많은.NET Framework 응용 프로그램 사용 [UTF-16][]합니다. 기록을 위해가 "Unicode" 라고에 이제 이라는 용어를 광범위 [표준](https://en.wikipedia.org/wiki/Unicode) utf-8 및 u t F-16을 모두 포함 합니다.
- Windows에서 유니코드는 많은 네이티브 응용 프로그램 계속 기본적으로 Windows-1252를 사용 합니다.

유니코드 인코딩도의 개념이 바이트 순서 표시 (BOM). 텍스트를 사용 하 여 인코딩을 디코더를 구별 하는 텍스트의 시작 부분에 Bom이 발생 합니다. 멀티 바이트 인코딩은 BOM 수도 나타냅니다 [엔디언](https://en.wikipedia.org/wiki/Endianness) 인코딩. Bom은 거의 텍스트는 유니코드 BOM이 있는 경우 적절 한 추측을 허용 하 고 유니코드가 아닌 텍스트에서 발생 하는 바이트 수 있도록 나타냅니다.

Bom은 선택 사항 하는 해당 도입은 Linux 분야에서 인기 있는 u t F-8의 신뢰할 수 있는 규칙을 모든 곳에서 사용 되기 때문입니다. 대부분의 Linux 응용 프로그램 텍스트 입력 u t F-8에서 인코딩 되는 것을 가정 합니다. 대부분의 Linux 응용 프로그램 인식을 BOM을 제대로 처리를 하는 동안 숫자 하지 해당 응용 프로그램을 사용 하 여 조작 하는 텍스트의 아티팩트에 선행 합니다.

**따라서 다음 작업을 수행하세요**:

- Windows 응용 프로그램 및 Windows PowerShell 사용 하 여 주로 작업 하는 경우 BOM 또는 u t F-16을 사용 하 여 u t F-8과 같은 인코딩을 하는 것이 좋습니다.
- 플랫폼에서 작업 하는 경우 BOM 사용 하 여 u t F-8이 좋습니다.
- Linux 관련 상황에서 주로 작업 하는 경우 BOM 없이 u t F-8이 좋습니다.
- Windows-1252 및 라틴어-1은 가능 하면 피해 야 하는 기본적으로 레거시 인코딩.
  그러나 일부 이전 Windows 응용 프로그램 에서도 달라질 수 있습니다.
- 스크립트 서명에 주목할 만한 이기도 [인코딩 종속](https://github.com/PowerShell/PowerShell/issues/3466), 다시 서명 해야 서명 된 스크립트에서 인코딩을의 변경을 의미 합니다.

## <a name="configuring-vscode"></a>VSCode를 구성합니다.

VSCode의 기본 인코딩은 BOM 없이 u t F-8입니다.

설정할 [VSCode의 인코딩][]VSCode 설정으로 이동 (<kbd>Ctrl<kbd>+</kbd>를</kbd>) 설정 및는 `"files.encoding"` 설정:

```json
"files.encoding": "utf8bom"
```

몇 가지 가능한 값은:

- `utf8`: [UTF-8] BOM 없이
- `utf8bom`: [UTF-8] BOM을 사용 하 여
- `utf16le`: Little endian [UTF-16]
- `utf16be`: Big endian [UTF-16]
- `windows1252`: [Windows-1252]

가져와야 드롭다운이 GUI 뷰에서 보거나 JSON에서에 대 한 완성 합니다.

또한 가능한 경우 인코딩 자동 검색에 다음을 추가할 수 있습니다.

```json
"files.autoGuessEncoding": true
```

모든 파일 형식에 영향을 하기 위해 이러한 설정을 사용 하지 않으려는 경우 VSCode 언어별 구성을 수도 있습니다. 설정에 배치 하 여 언어별 설정 만들기는 `[<language-name>]` 필드입니다. 예:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>PowerShell 구성

PowerShell의 기본 인코딩 버전에 따라 달라 집니다.

- PowerShell 6 +에서 기본 인코딩은 모든 플랫폼에서 BOM 없는 utf-8입니다.
- Windows PowerShell에서 기본 인코딩은 일반적으로 Windows-1252와의 확장인 [latin-1][], ISO 8859-1 라고도 합니다.

PowerShell 5 이상에서이 사용 하 여 기본 인코딩을 확인할 수 있습니다.

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

다음 [스크립트](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) BOM 없이 스크립트에 대해 유추 하 여 PowerShell 세션을 인코딩 항목을 확인 하기 위해 사용할 수 있습니다.

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

보다 일반적으로 프로필 설정을 사용 하 여 지정 된 인코딩을 사용 하려면 PowerShell을 구성 하는 것이 가능 합니다. 다음 문서를 참조하세요.

- [@mklement0][stackoverflow PowerShell 인코딩에 대 한 응답](https://stackoverflow.com/a/40098904)합니다.
- [@rkeithhill][PowerShell에서 BOM 없는 utf-8 입력을 처리 하는 방법에 대 한 블로그 게시물](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/)합니다.

특정 입력 인코딩을 사용 하려면 PowerShell을 적용할는 것이 불가능 합니다. PowerShell 5.1 및 기본적으로 Windows-1252 인코딩은 BOM이 있으면 아래. 상호 운용성을 위해 BOM 사용 하 여 유니코드 형식으로 스크립트를 저장 하는 것이 적합 합니다.

> [!IMPORTANT]
> 다른 도구는 터치 PowerShell 스크립트 인코딩 선택 항목에 따라 달라질 수 있습니다 또는 다른 인코딩으로 스크립트를 다시 인코딩할 해야 합니다.

### <a name="existing-scripts"></a>기존 스크립트

파일 시스템에 이미 있는 스크립트를 새 선택 인코딩을 다시 인코딩할 해야 합니다. 아래쪽 막대의 VSCode에서 u t F-8 레이블이 표시 됩니다. 클릭 하 여 작업 모음을 열고 선택 **인코딩하여 저장**합니다. 이제 해당 파일에 대 한 새 인코딩을 선택할 수 있습니다. 참조 [VSCode의 인코딩][] 전체 지침에 대 한 합니다.

여러 파일을 다시 인코딩하는 경우에 다음 스크립트를 사용할 수 있습니다.

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>PowerShell ISE(통합 스크립팅 환경)

또한 PowerShell ISE를 사용 하 여 스크립트를 편집 하면 해당 인코딩 설정을 동기화 해야 합니다.

ISE BOM을 적용 해야 하지만 또한 리플렉션을 사용 하 여 [인코딩을 설정](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/)합니다.
신생 업체 간에 유지 하지 않습니다.이 note 합니다.

### <a name="source-control-software"></a>원본 제어 소프트웨어

Git와 같은 일부 원본 제어 도구 인코딩을 무시합니다 git에는 방금 바이트 수를 추적합니다.
다른 TFS 또는 Mercurial, 같은 행위입니다. Git 기반 도구 일부 텍스트를 디코딩 의존 합니다.

이 경우 다음을 확인 합니다

- 텍스트 인코딩을 VSCode 구성과 일치 하도록 원본 제어에 구성 합니다.
- 모든 파일 관련 인코딩 형식으로 원본 제어에 체크 인을 확인 합니다.
- 변경 내용을 원본 제어를 통해 받은 인코딩을에 주의 하십시오. 이 키 기호를 변경 하지만 (하는데 때문에 바이트 문자를 하지 않은) 변경 된 것으로 보이지 나타내는 차이입니다.

### <a name="collaborators-environments"></a>협력자 환경

소스 제어를 구성 하는 데 기반으로 공유 하는 파일에서 공동 PowerShell 파일을 다시 인코딩하여 인코딩을 재정의 하는 설정이 없는를 확인 합니다.

### <a name="other-programs"></a>다른 프로그램

읽거나 PowerShell 스크립트를 작성 하는 다른 프로그램이 인코딩합니다 다시 수 있습니다.

몇 가지 예는 다음과 같습니다.

- 클립보드를 사용 하 여 복사 하 여 스크립트를 붙여 넣습니다. 다음은 같은 시나리오에서 일반적입니다.
  - VM에 스크립트 복사
  - 전자 메일 또는 웹 페이지에서 스크립트를 복사합니다.
  - Microsoft Word 나 PowerPoint 문서 안팎으로 스크립트를 복사합니다.
- 다른 텍스트 편집기와 같은:
  - 메모장
  - vim
  - 다른 PowerShell 스크립트 편집기
- 텍스트와 같은 유틸리티를 편집 합니다.
  - `Get-Content`/`Set-Content`/`Out-File`
  - PowerShell 리디렉션 연산자와 같은 `>` 및 `>>`
  - `sed`/`awk`
- 와 같은 전송 프로그램 파일:
  - 스크립트를 다운로드 하는 경우 웹 브라우저
  - 파일 공유

이러한 도구 중 일부 텍스트가 아닌 바이트 단위로 처리 하지만 다른 인코딩 구성을 제공 합니다. 인코딩을 구성 해야 하는 경우 이러한 문제를 방지 하기 위해 인코딩을 편집기와 동일 하 게 확인 해야 합니다.

## <a name="other-resources-on-encoding-in-powershell"></a>다른 리소스를 PowerShell에서 인코딩

몇 가지 다른 유용한 게시물 인코딩 및 PowerShell에서 인코딩 구성 읽기 만한 가지가 있습니다.

- [@mklement0][stackoverflow PowerShell 인코딩의 요약](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- 이전 문제 vscode-인코딩 문제에 대 한 PowerShell에서 열립니다.
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [클래식 *Joel on Software* 유니코드에 대 한 작성](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [.NET Standard의 인코딩](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[바이트 순서 표시가]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[언어 서버 프로토콜]: https://microsoft.github.io/language-server-protocol/
[VSCode의 인코딩]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support