---
title: PowerShell-Docs 스타일 가이드
description: 이 문서에서는 PowerShell 설명서 작성을 위한 스타일 규칙을 제공합니다.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 964536c5195c3bb8abd98b5996a96fc7b9362489
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402580"
---
# <a name="powershell-docs-style-guide"></a>PowerShell-Docs 스타일 가이드

이 문서에서는 PowerShell-Docs 콘텐츠에 관한 스타일 지침을 제공합니다. 이 지침은 [개요](overview.md#get-started-writing-docs)에 설명된 정보를 기반으로 합니다.

## <a name="product-terminology"></a>제품 용어

PowerShell에는 몇 가지 변형이 있습니다.
이 표에는 PowerShell을 설명하는 데 사용되는 몇 가지 다양한 용어가 정의되어 있습니다.

- **PowerShell** - 기본값입니다. 앞으로는 PowerShell 7 이상이 유일한 정식 PowerShell로 간주됩니다.

- **PowerShell Core** - .NET Core를 기반으로 빌드된 PowerShell입니다. 용어 **Core**는 Windows PowerShell과 구분해야 하는 경우에만 사용해야 합니다.

- **Windows PowerShell** - .NET Framework를 기반으로 빌드된 PowerShell입니다. Windows PowerShell은 Windows에만 제공되며 전체 Framework가 필요합니다.

일반적으로 설명서의 "Windows PowerShell"에 대한 참조는 "PowerShell"로 변경할 수 있습니다.
Windows 관련 기술을 설명하는 경우 “Windows PowerShell”을 변경해서는 **안 됩니다**.

## <a name="markdown-specifics"></a>Markdown 세부보

설명서를 빌드하는 Microsoft OPS(Open Publishing System)는 [markdig][]를 사용하여 Markdown 문서를 처리합니다. markdig는 최신 [CommonMark][] 사양의 규칙에 따라 문서를 구문 분석합니다.

새 CommonMark 사양은 일부 Markdown 요소 생성에 대해 훨씬 더 엄격하게 적용됩니다. 이 문서에 제공된 세부 정보에 각별히 주의하세요.

### <a name="blank-lines-spaces-and-tabs"></a>빈 줄, 공백, 탭

중복된 빈 줄을 제거합니다. HTML에서는 여러 빈 줄이 하나의 빈 줄로 렌더링되므로 여러 빈 줄을 넣을 필요가 없습니다.

또한 빈 줄은 Markdown에서 블록이 끝난다는 신호입니다. 서로 다른 형식의 Markdown 블록 사이(예: 단락과 목록 또는 헤더 사이)에는 빈 줄이 하나 있어야 합니다.

> [!NOTE]
> Markdown에서는 간격이 중요합니다. 항상 하드 탭 대신 공백을 사용하세요. 줄의 끝부분에서 추가 공백을 제거해야 합니다.

### <a name="titles-and-headings"></a>제목 및 머리글

[ATX 머리글][atx](`=` 또는 `-` 스타일 헤더가 아닌 # 스타일)만 사용합니다.

- 문장의 첫 글자를 대문자로 시작하세요. 고유 명사와 제목 또는 헤더의 첫 글자만 대문자로 시작해야 합니다.
- `#`와 머리글의 첫 문자 사이에는 공백이 하나 있어야 합니다.
- 머리글은 빈 줄 하나로 묶어야 합니다.
- H1은 문서당 하나만 사용합니다.
- 헤더 수준은 1씩 증가해야 합니다. 수준을 건너뛰지 않습니다.
- 헤더에 굵은 글꼴 또는 기타 태그를 사용하지 않습니다.

### <a name="limit-line-length-to-100-characters"></a>줄 길이는 100자로 제한합니다.

이는 개념 문서와 cmdlet 참조에 적용됩니다. about_topics는 80자로 제한됩니다.
줄 길이를 제한하면 git diff 가독성과 기록이 향상됩니다. 또한 다른 작성자가 보다 쉽게 기여할 수 있습니다.

사전 설정된 줄 길이에 맞게 단락을 쉽게 재배치하려면 Visual Studio Code에서 [Reflow Markdown][reflow] 확장을 사용합니다.

### <a name="lists"></a>목록

목록에 여러 문장이나 단락이 포함되어 있으면 목록 대신 하위 수준 헤더를 사용하는 것이 좋습니다.

목록은 빈 줄 하나로 묶어야 합니다.

#### <a name="unordered-lists"></a>순서가 지정되지 않은 목록

목록 항목의 끝에 마침표를 사용하지 않습니다(여러 문장이 있는 경우만 허용). 목록 항목 글머리 기호에 하이픈 문자(`-`)를 사용합니다. 이렇게 하면 별표[`*`]를 사용하는 굵게 또는 기울임꼴 태그와의 혼동을 피할 수 있습니다. 글머리 기호 항목 아래에 단락이나 기타 요소를 포함하려면 줄 바꿈을 삽입하고 글머리 기호 뒤 첫 번째 문자에 들여쓰기를 맞춥니다.

다음은 그 예입니다.

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

글머리 기호 항목 아래 하위 요소를 포함하는 목록입니다.

- 첫 번째 글머리 기호 항목

  첫 번째 글머리 기호를 설명하는 문장입니다.

  - 하위 글머리 기호 항목

    하위 글머리 기호를 설명하는 문장입니다.

- 두 번째 글머리 기호 항목
- 세 번째 글머리 기호 항목

#### <a name="ordered-lists"></a>순서가 지정된 목록

번호 매기기 항목 아래에 단락이나 기타 요소를 포함하려면 항목 번호 뒤 첫 번째 문자에 들여쓰기를 맞춥니다. 번호 매기기 목록의 모든 항목은 각 항목을 증가시키는 것이 아니라 숫자 `1.`을 사용해야 합니다. Markdown 렌더링은 값을 자동으로 증가시킵니다. 이렇게 하면 보다 쉽게 항목 순서를 다시 매기고 하위 콘텐츠의 들여쓰기를 표준화할 수 있습니다.

다음은 그 예입니다.

```markdown
1. For the first element, insert a single space after the 1. Long sentences should be
   wrapped to the next line and must line up with the first character after the numbered
   list marker.

   To include a second element (like this one), insert a line break after the first
   and align indentations. The indentation of the second element must line up with
   the first character after the numbered list marker. For single digit items, like
   this one, you indent to column 4. For double digits items, for example item number
   10, you indent to column 5.

1. The next numbered item starts here.
```

결과 Markdown은 다음과 같이 렌더링됩니다.

1. 첫 번째 요소의 경우 1 뒤에 단일 공백을 삽입합니다. 긴 문장은 다음 줄로 줄바꿈되어야 하며, 번호 매기기 목록 마커 뒤의 첫 번째 문자에 맞춰야 합니다.

   (다음과 같은) 두 번째 요소를 포함하려면 첫 번째 요소 뒤에 줄 바꿈을 삽입하고 들여쓰기를 정렬합니다. 두 번째 요소의 들여쓰기는 번호 매기기 목록 마커 뒤의 첫 번째 문자에 맞춰야 합니다. 이와 같은 한 자리 항목의 경우 열 4로 들여씁니다. 항목 번호 10과 같은 두 자리 항목의 경우 열 5로 들여씁니다.

1. 다음 번호 매기기 항목은 여기에서 시작됩니다.

### <a name="formatting-command-syntax-elements"></a>명령 구문 요소 서식 지정

- cmdlet 및 매개 변수에는 항상 전체 이름을 사용합니다. 특별히 보여 주어야 하는 것이 아니라면 별칭을 사용하지 않습니다.

- 단락 내에서 언어 키워드, cmdlet 이름, 변수, 파일 경로는 역따옴표(`` ` ``) 문자로 래핑해야 합니다. 속성, 매개 변수, 클래스 이름은 **굵게** 표시해야 합니다.

  다음은 그 예입니다.

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

- 이름으로 매개 변수를 참조하는 경우에는 이름을 **굵게** 표시해야 합니다. 하이픈 접두사를 사용하여 매개 변수 사용을 보여 주는 경우, 매개 변수를 역따옴표으로 래핑해야 합니다. 다음은 그 예입니다.

  ```markdown
  The parameter's name is **Name**, but it is typed as `-Name` when used on the command
  line as a parameter.
  ```

- 외부 명령(EXE, 스크립트 등)을 참조하는 경우, 명령 이름은 모두 소문자(문장의 시작 부분인 경우 대문자)로 굵게 표시하고 적절한 파일 확장명을 포함해야 합니다. 다음은 그 예입니다.

  ```markdown
  For example, on Windows systems, you can use the `net start` and `net stop` commands
  to start and stop a service. **Sc.exe** is another service control tool for Windows.
  That name does not fit into the naming pattern for the **net.exe** service commands.
  ```

- 외부 명령의 사용 예제를 표시하는 경우, 예제를 역따옴표로 래핑해야 합니다.
  이름이 별칭과 충돌하는 경우, 명령 예제에 파일 확장명을 포함해야 합니다. 다음은 그 예입니다.

  ```markdown
  To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
  ```

- 참조 콘텐츠가 아닌 개념 문서를 작성할 때, 처음으로 나오는 cmdlet 이름은 하이퍼링크로 cmdlet 설명서에 연결되어야 합니다. 하이퍼링크의 대괄호 안에는 역따옴표, 굵은 글꼴 또는 기타 태그를 사용하지 않습니다.

  다음은 그 예입니다.

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  자세한 내용은 이 문서의 [하이퍼링크](#hyperlinks) 섹션을 참조하세요.

### <a name="images"></a>이미지

이미지를 포함할 구문의 경우:

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

여기서 `alt text`는 이미지에 대한 간략한 설명이고 `<folder path>`는 이미지의 상대 경로입니다. 대체 텍스트는 시각 장애인을 위한 화면 읽기 프로그램에 필요합니다. 대체 텍스트는 이미지를 렌더링할 수 없는 사이트 버그가 있는 경우에도 유용합니다.

이미지는 문서가 있는 폴더 내의 `media/<article-name>` 폴더에 저장해야 합니다.
문서 간에 이미지를 공유하면 안 됩니다. `media` 폴더 아래에 문서의 파일 이름과 일치하는 폴더를 만듭니다. 해당 문서의 이미지를 새 폴더에 복사합니다. 여러 문서에서 이미지를 사용하는 경우, 각 이미지 폴더에는 해당 이미지 파일의 복사본이 있어야 합니다. 이렇게 하면 한 문서의 이미지를 변경해도 다른 문서는 영향을 받지 않습니다.

`*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg` 형식의 이미지 파일이 지원됩니다.

### <a name="markdown-extensions-supported-by-open-publishing"></a>Open Publishing이 지원하는 Markdown 확장

[Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack)에는 Microsoft 게시 시스템에 고유한 기능을 지원하는 도구가 포함되어 있습니다. 경고는 콘텐츠의 중요도를 나타내는 색과 아이콘으로 docs.microsoft.com에서 렌더링되는 블록 따옴표를 만드는 Markdown 확장입니다. 다음 경고 유형이 지원됩니다.

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

이러한 경고는 docs.microsoft.com에서 다음과 같이 표시됩니다.

> [!NOTE]
> 훑어보는 경우에도 사용자가 주목해야 하는 정보입니다.

> [!TIP]
> 사용자의 성공을 돕는 선택적 정보입니다.

> [!IMPORTANT]
> 사용자의 성공에 필요한 필수 정보입니다.

> [!CAUTION]
> 작업에서 발생할 수 있는 부정적 결과입니다.

> [!WARNING]
> 작업의 위험한 특정 결과입니다.

## <a name="hyperlinks"></a>하이퍼링크

- URL을 그대로 사용하지 마세요. 링크는 Markdown 구문 `[friendlyname](url-or-path)`을 사용해야 합니다.
- 필요한 경우 URL을 그대로 사용할 수 있지만 역따옴표로 묶어야 합니다. 다음은 그 예입니다.

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

- URL 링크는 가능하면 HTTPS 형식이어야 합니다.
- 링크에는 일반적으로 연결된 토픽의 제목인 식별 이름이 있어야 합니다.
- 맨 아래의 "관련 링크" 섹션에 있는 항목은 모두 하이퍼링크로 처리해야 합니다.
- 하이퍼링크의 대괄호 안에는 역따옴표, 굵은 글꼴 또는 기타 태그를 사용하지 않습니다.

### <a name="linking-to-other-content"></a>다른 콘텐츠에 연결

게시 시스템에서 지원하는 하이퍼링크의 유형은 두 가지(URL 링크와 파일 링크)입니다.

URL 링크는 docs.microsoft.com의 루트를 기준으로 하는 URL 경로이거나 전체 URL 구문을 포함하는 절대 URL일 수 있습니다. (예: `https:/github.com/MicrosoftDocs/PowerShell-Docs`)

- PowerShell-Docs 외부 콘텐츠에 연결하거나 PowerShell-Docs 내의 cmdlet 참조와 개념 문서 사이를 연결하는 경우 URL 링크를 사용합니다.
- 상대 링크를 만드는 가장 간단한 방법은 브라우저에서 URL을 복사한 다음 Markdown에 붙여넣는 값에서 `https://docs.microsoft.com/en-us`를 제거하는 것입니다.
   - Microsoft 속성에서 URL에 로캘을 포함하지 마세요(예: URL에서 "/en-us"를 제거).
- 외부 웹 사이트에 대한 모든 URL은 대상 사이트에 유효하지 않은 경우가 아니라면 HTTPS를 사용해야 합니다.

파일 링크는 참조 문서를 다른 참조 문서로 또는 개념 문서를 다른 개념 문서로 연결하는 데 사용됩니다. 특정 PowerShell 버전의 참조 문서에 연결해야 하는 경우 URL 링크를 사용해야 합니다.

- 파일 링크에는 상대 파일 경로가 포함됩니다(예: `../folder/file.md`).
- 모든 파일 경로에는 슬래시(`/`) 문자를 사용합니다.

## <a name="formatting-code-samples"></a>코드 샘플 서식 지정

Markdown은 다음 두 가지 코드 스타일을 지원합니다.

- 코드 범위(인라인) - 단일 역따옴표(`` ` ``) 문자로 표시됩니다. 독립 실행형 블록으로 사용되지 않고 단락 내에서 사용됩니다.
- 코드 블록 - 삼중 역따옴표(`` ``` ``) 문자열로 묶인 여러 줄의 블록입니다. 코드 블록에는 역따옴표 뒤에 언어 레이블이 있을 수 있습니다. 언어 레이블로 코드 블록의 내용에 구문 강조 표시를 사용할 수 있습니다.

### <a name="using-code-blocks"></a>코드 블록 사용

Markdown에서는 코드 블록을 나타내기 위한 들여쓰기가 허용되지만 이 패턴은 문제가 될 수 있으므로 피해야 합니다. 모든 코드 블록은 코드 펜스에 포함되어야 합니다. 코드 펜스는 삼중 역따옴표(`` ``` ``) 문자열로 둘러싸인 코드 블록입니다. 코드 펜스 마커는 코드 샘플 앞뒤의 고유한 줄에 있어야 합니다. 코드 블록의 시작 부분에 있는 마커에는 선택적 언어 레이블이 있을 수 있습니다. Microsoft OPS(Open Publishing System)는 언어 레이블을 사용하여 구문 강조 표시 기능을 지원합니다.

또한 OPS는 코드 블록의 내용을 클립보드에 복사하는 **복사** 단추를 추가합니다. 이를 통해 코드 예제 테스트를 위한 스크립트에 코드를 빠르게 붙여넣을 수 있습니다. 하지만 설명서의 모든 예제가 실행을 염두에 두고 제공되는 것은 아닙니다. 일부 코드 블록은 PowerShell 개념의 간단한 예시입니다.

설명서에 사용되는 코드 블록에는 다음 두 가지 유형이 있습니다.

1. 설명 예제
2. 실행 파일 예제

### <a name="syntax-code-blocks"></a>구문 코드 블록

이 예제는 `Get-Command` cmdlet의 가능한 모든 매개 변수를 보여 줍니다.

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
  [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
  [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

이 예제는 일반적인 용어로 `for` 문을 설명합니다.

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a>설명 예제

설명 예제는 PowerShell 개념을 설명하는 데 사용됩니다. 실행을 위해 클립보드로 복사하기 위한 예제가 아닙니다. 이 예제는 쉽게 입력할 수 있는 간단한 예제에 가장 흔히 사용되며
명령의 구문을 설명하는 구문 예제에도 사용됩니다. 코드 블록에는 예시 명령의 예제 출력이 포함될 수 있습니다.

다음은 PowerShell 비교 연산자를 보여 주는 간단한 예제입니다.

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS>  1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

이 예제는 간단한 PowerShell 프롬프트를 포함하며 결과 출력을 보여 줍니다. 이 예제는 독자가 복사하고 실행하는 것이 아닙니다.

### <a name="executable-examples"></a>실행 파일 예제

더 복잡한 예제나 복사 및 실행에 유용한 예제에는 다음 블록 스타일 태그를 사용해야 합니다.

~~~markdown
```powershell
<PowerShell code goes here>
```
~~~

PowerShell 명령이 표시하는 출력은 구문 강조 표시를 방지하기 위해 **출력** 코드 블록으로 묶어야 합니다. 다음은 그 예입니다.

~~~markdown
```powershell
Get-Command -Module Microsoft.PowerShell.Security
```

```Output
CommandType  Name                        Version    Source
-----------  ----                        -------    ------
Cmdlet       ConvertFrom-SecureString    3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       ConvertTo-SecureString      3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-CmsMessage              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Credential              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-PfxCertificate          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       New-FileCatalog             3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Protect-CmsMessage          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Test-FileCatalog            3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Unprotect-CmsMessage        3.0.0.0    Microsoft.PowerShell.Security
```
~~~

**출력** 코드 레이블은 구문 강조 표시 시스템에서 지원하는 공식 "언어"가 아닙니다.
그러나 이 레이블은 OPS가 웹 페이지의 코드 상자 프레임에 "출력" 레이블을 추가하기 때문에 유용합니다. "출력" 코드 상자에는 구문 강조 표시가 없습니다.

## <a name="coding-style-rules"></a>코딩 스타일 규칙

### <a name="avoid-line-continuation-in-code-samples"></a>코드 샘플에서 줄 연속 사용하지 않음

PowerShell 코드 예제에서 줄 연속 문자(`` ` ``)를 사용하지 마세요. 줄 연속 문자는 가독성이 떨어지며, 줄의 끝에 추가 공백이 있는 경우 문제를 일으킬 수 있습니다.

- 매개 변수가 많은 cmdlet의 줄 길이를 줄이려면 PowerShell 스플래팅을 사용합니다.
- 파이프(`|`) 문자 뒤, 여는 중괄호, 괄호, 대괄호 등 PowerShell의 자연스러운 줄 바꿈 방법을 활용하세요.

### <a name="avoid-using-powershell-prompts-in-examples"></a>예제에서 PowerShell 프롬프트 사용 안 함

프롬프트 문자열은 사용하지 않는 것이 좋으며, 명령줄 사용법을 보여 주는 시나리오에만 사용해야 합니다. 이러한 예제 대부분에서 프롬프트 문자열은 `PS>`여야 합니다. 이 프롬프트는 OS별 표시기와는 독립적입니다.

프롬프트는 프롬프트를 변경하는 명령을 보여 주는 예제나 표시 경로가 예시 시나리오에 중요한 경우 필요합니다. 다음 예제는 레지스트리 공급자를 사용할 때 프롬프트가 변경되는 방식을 보여 줍니다.

```powershell
PS C:\> cd HKCU:\System\
PS HKCU:\System\> dir

    Hive: HKEY_CURRENT_USER\System

Name                   Property
----                   --------
CurrentControlSet
GameConfigStore        GameDVR_Enabled                       : 1
                       GameDVR_FSEBehaviorMode               : 2
                       Win32_AutoGameModeDefaultProfile      : {2, 0, 1, 0...}
                       Win32_GameModeRelatedProcesses        : {1, 0, 1, 0...}
                       GameDVR_HonorUserFSEBehaviorMode      : 0
                       GameDVR_DXGIHonorFSEWindowsCompatible : 0
```

### <a name="do-not-use-aliases-in-examples"></a>예제에서 별칭 사용 안 함

별칭에 대해 구체적으로 이야기해야 하는 경우가 아니라면 항상 모든 cmdlet과 매개 변수의 전체 이름을 사용해야 합니다. cmdlet 및 매개 변수 이름은 코드에 정의된 적절한 철자를 사용해야 합니다.

### <a name="using-parameters-in-examples"></a>예제에서 매개 변수 사용

위치 매개 변수 사용 안 함 일반적으로 매개 변수가 위치 매개 변수인 경우에도 항상 매개 변수 이름을 예제에 포함해야 합니다. 이렇게 하면 예제에서 혼동 가능성이 줄어듭니다.

## <a name="next-steps"></a>다음 단계

[cmdlet 참조 편집](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
