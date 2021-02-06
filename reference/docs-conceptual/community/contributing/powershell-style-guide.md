---
title: PowerShell-Docs 스타일 가이드
description: 이 문서에서는 PowerShell 설명서 작성을 위한 스타일 규칙을 제공합니다.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 6f23f63cffc9fed9cbbcf84539875bfaf4247732
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2020
ms.locfileid: "99600615"
---
# <a name="powershell-docs-style-guide"></a>PowerShell-Docs 스타일 가이드

이 문서에서는 PowerShell-Docs 콘텐츠에 관한 스타일 지침을 제공합니다. [개요](overview.md#get-started-writing-docs)에 설명 된 정보를 기반으로 합니다.

## <a name="product-terminology"></a>제품 용어

PowerShell에는 몇 가지 변형이 있습니다.

- **PowerShell** - 기본값입니다. PowerShell 7 이상을 진정한 PowerShell이 아닌 것으로 간주 합니다.
- **PowerShell Core** - .NET Core를 기반으로 빌드된 PowerShell입니다. **핵심** 이라는 용어는 Windows PowerShell과 구분 해야 하는 경우에만 사용 해야 합니다.
- **Windows PowerShell** - .NET Framework를 기반으로 빌드된 PowerShell입니다. Windows PowerShell은 Windows에만 제공되며 전체 Framework가 필요합니다.

  일반적으로 설명서의 "Windows PowerShell"에 대 한 참조를 _PowerShell_ 로 변경할 수 있습니다.
  _Windows powershell_ 특정 동작을 설명 하는 경우 "windows powershell"을 사용 해야 합니다.

관련 제품

- **Visual Studio Code (VS Code)** -Microsoft의 무료 오픈 소스 편집기입니다. 처음 언급할 때는 전체 이름을 사용해야 합니다. 그런 다음 **VS Code** 라고 언급할 수 있습니다. "VSCode"를 사용 하지 마세요.
- **Visual Studio Code에 대한 Powershell 확장** - 확장은 VS Code를 PowerShell의 기본 IDE로 전환합니다. 처음 언급할 때는 전체 이름을 사용해야 합니다. 그런 다음 **PowerShell 확장** 이라고 언급할 수 있습니다.
- **Azure PowerShell** - Azure 서비스를 관리하는 데 사용되는 Powershell 모듈의 컬렉션입니다.
- **Azure Stack PowerShell** - Microsoft의 하이브리드 클라우드 솔루션을 관리하는 데 사용되는 Powershell 모듈의 컬렉션입니다.

## <a name="markdown-specifics"></a>Markdown 세부보

설명서를 빌드하는 Microsoft OPS(Open Publishing System)는 [markdig][]를 사용하여 Markdown 문서를 처리합니다. markdig는 최신 [CommonMark][] 사양의 규칙에 따라 문서를 구문 분석합니다.

새 CommonMark 사양은 일부 Markdown 요소 생성에 대해 훨씬 더 엄격하게 적용됩니다. 이 문서에 제공된 세부 정보에 각별히 주의하세요.

### <a name="blank-lines-spaces-and-tabs"></a>빈 줄, 공백, 탭

또한 빈 줄은 Markdown에서 블록이 끝난다는 신호입니다. 서로 다른 형식의 Markdown 블록 사이(예: 단락과 목록 또는 헤더 사이)에는 빈 줄이 하나 있어야 합니다.

여러 개의 연속 된 빈 줄은 HTML에서 하나의 빈 줄로 렌더링 됩니다. 용도는 아닙니다.
코드 블록 내에서 연속 된 빈 줄은 코드 블록을 중단 합니다.

줄의 끝부분에서 추가 공백을 제거해야 합니다.

> [!NOTE]
> Markdown에서는 간격이 중요합니다. 항상 하드 탭 대신 공백을 사용하세요. 후행 공백은 Markdown이 렌더링하는 방식을 변경할 수 있습니다.

### <a name="titles-and-headings"></a>제목 및 머리글

[ATX 머리글][atx](`=` 또는 `-` 스타일 헤더가 아닌 # 스타일)만 사용합니다.

- 문장의 첫 글자를 대문자로 시작하세요. 고유 명사와 제목 또는 헤더의 첫 글자만 대문자로 시작해야 합니다.
- `#`와 머리글의 첫 문자 사이에는 공백이 하나 있어야 합니다.
- 머리글은 빈 줄 하나로 묶어야 합니다.
- H1은 문서당 하나만 사용합니다.
- 헤더 수준은 1씩 증가해야 합니다. 수준 건너뛰기 안 함
- 머리글에 굵은 또는 기타 태그를 사용 하지 않음

### <a name="limit-line-length-to-100-characters"></a>줄 길이는 100자로 제한합니다.

이는 개념 문서와 cmdlet 참조에 적용됩니다. 줄 길이를 제한하면 git diff의 가독성과 기록이 향상됩니다. 또한 다른 작성자가 보다 쉽게 기여할 수 있습니다.

사전 설정된 줄 길이에 맞게 단락을 쉽게 재배치하려면 Visual Studio Code에서 [Reflow Markdown][reflow] 확장을 사용합니다.

about_topics는 80자로 제한됩니다. 자세한 내용은 [About_ 파일 서식 지정](#formatting-about_-files)을 참조 하세요.

### <a name="lists"></a>목록

목록에 여러 문장이 나 단락이 포함 되어 있으면 목록 대신 하위 수준 헤더를 사용 하는 것이 좋습니다.

목록은 빈 줄 하나로 묶어야 합니다.

#### <a name="unordered-lists"></a>순서가 지정되지 않은 목록

여러 문장을 포함 하지 않는 한 마침표를 사용 하 여 목록 항목을 종료 하지 않습니다. 목록 항목 글머리 기호에 하이픈 문자(`-`)를 사용합니다. 이렇게 하면 별표[`*`]를 사용하는 굵게 또는 기울임꼴 태그와의 혼동을 피할 수 있습니다. 글머리 기호 항목 아래에 단락이나 기타 요소를 포함하려면 줄 바꿈을 삽입하고 글머리 기호 뒤 첫 번째 문자에 들여쓰기를 맞춥니다.

다음은 그 예입니다.

```markdown
This is a list that contain child elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Child bullet item

    Sentence explaining the child bullet.

- Second bullet item
- Third bullet item
```

글머리 기호 항목 아래의 자식 요소를 포함 하는 목록입니다.

- 첫 번째 글머리 기호 항목

  첫 번째 글머리 기호를 설명하는 문장입니다.

  - 자식 글머리 기호 항목

    자식 글머리 기호를 설명 하는 문장입니다.

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

### <a name="images"></a>이미지

이미지를 포함할 구문의 경우:

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

여기서 `alt text`는 이미지에 대한 간략한 설명이고 `<folder path>`는 이미지의 상대 경로입니다. 대체 텍스트는 시각 장애인을 위한 화면 읽기 프로그램에 필요합니다.

이미지는 `media/<article-name>` 문서를 포함 하는 폴더 내의 폴더에 저장 해야 합니다.
문서 간에 이미지를 공유 하지 마세요. `media` 폴더 아래 문서의 파일 이름과 일치하는 폴더를 만듭니다. 해당 문서의 이미지를 해당하는 새 폴더로 복사합니다. 이미지가 여러 문서에서 사용되는 경우 각 이미지 폴더에는 해당 이미지 파일의 복사본이 있어야 합니다. 이 사례에서는 다른 문서에 영향을 주는 문서에서 이미지가 변경되지 않습니다.

다음 이미지 파일 형식이 지원 됩니다. `*.png` ,, `*.gif` `*.jpeg` , `*.jpg` , `*.svg`

### <a name="markdown-extensions-supported-by-open-publishing"></a>공개 게시에서 지원되는 Markdown 확장

[Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) 에는 게시 시스템에 고유한 기능을 지 원하는 도구가 포함 되어 있습니다. 경고는 콘텐츠의 중요도를 강조 하는 색 및 아이콘을 사용 하 여 docs.microsoft.com에서 렌더링 하는 블록 따옴표를 만드는 Markdown 확장입니다. 다음과 같은 경고 유형이 지원됩니다.

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

이러한 경고는 docs.microsoft.com에서 다음과 같이 보입니다.

참고 블록

> [!NOTE]
> Information the user should notice even if skimming.

팁 블록

> [!TIP]
> Optional information to help a user be more successful.

중요 블록

> [!IMPORTANT]
> Essential information required for user success.

주의 블록

> [!CAUTION]
> Negative potential consequences of an action.

경고 블록

> [!WARNING]
> 작업의 위험한 특정 결과입니다.

### <a name="hyperlinks"></a>하이퍼링크

- 하이퍼링크는 Markdown 구문을 사용 해야 합니다 `[friendlyname](url-or-path)` . [링크 참조가][linkref] 지원 됩니다.
- 게시 시스템은 세 가지 유형의 링크를 지원 합니다.
  - URL 링크
  - 파일 링크
  - 상호 참조 링크
- Docs.microsoft.com의 다른 문서에 대 한 링크는 사이트 상대 경로 여야 합니다.
- 외부 웹 사이트에 대 한 모든 Url은 대상 사이트에 대해 유효 하지 않은 경우 HTTPS를 사용 해야 합니다.
- 링크의 이름은 일반적으로 연결 된 아티클의 제목 이어야 합니다.
- 아래쪽에 있는 _관련 링크_ 섹션의 모든 항목에는 하이퍼링크가 지정 되어 있어야 합니다.
- 하이퍼링크의 대괄호 안에는 backticks, 굵게 또는 기타 태그를 사용 하지 마세요.
- 특정 URI를 문서화 하는 경우에는 완전 한 Url을 사용할 수 있습니다. URI는 backticks으로 묶어야 합니다. 다음은 그 예입니다. 

  ```markdown
  By default, if you don't specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content-on-docsmicrosoftcom"></a>Docs.microsoft.com의 다른 콘텐츠에 연결

- Docs.microsoft.com의 다른 아티클에 대 한 **URL 링크** 는 사이트 상대 경로 여야 합니다. 상대 링크를 만드는 가장 간단한 방법은 브라우저에서 URL을 복사한 다음 `https://docs.microsoft.com/en-us` markdown에 붙여넣은 값에서 제거 하는 것입니다. Microsoft 속성의 Url에는 로캘을 포함 하지 않습니다 ( `/en-us` url에서 제거). URL에서 불필요 한 쿼리 매개 변수를 제거 합니다. 제거 해야 하는 예제:

  - `?view=powershell-5.1` -특정 버전의 PowerShell에 연결 하는 데 사용 됩니다.
  - `?redirectedfrom=MSDN` -이전 문서에서 새 위치로 리디렉션되는 경우 URL에 추가 됩니다.

  특정 버전의 문서에 연결 해야 하는 경우 `&preserve_view=true` 쿼리 문자열에 매개 변수를 추가 해야 합니다. 예: `?view=powershell-5.1&preserve_view=true`

- **파일 링크** 를 사용 하 여 참조 문서 간에 연결 하거나 한 개념 문서에서 다른 문서에 연결 합니다. 특정 버전의 PowerShell에 대 한 참조 문서에 연결 해야 하는 경우 URL 링크를 사용 해야 합니다.

  - 파일 링크에 상대 파일 경로 (예:)가 포함 되어 있습니다. `../folder/file.md`
  - 모든 파일 경로에는 슬래시 () 문자를 사용 합니다. `/`

- **상호 참조 링크** 는 게시 시스템에서 지 원하는 특별 한 기능입니다. 개념 문서에서 상호 참조 링크를 사용 하 여 .NET API 또는 cmdlet 참조에 연결할 수 있습니다.

  .NET API 참조에 대 한 링크는 중앙 참가자 가이드에서 [설명서의 사용 링크](/contribute/how-to-write-links#xref-cross-reference-links) 를 참조 하세요.

  Cmdlet 참조 링크의 형식은 `xref:<module-name>.<cmdlet-name>` 다음과 같습니다. 예를 들어,을 (를) `Get-Content` **Microsoft. PowerShell 관리** 모듈의 cmdlet에 연결 합니다.

  `[Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)`

URL 및 파일 링크 모두에 대해 딥 링크를 사용할 수 있습니다. 대상 경로의 끝에 앵커를 추가 합니다.
다음은 그 예입니다. 

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

자세한 내용은 [설명서의 사용 링크](/contribute/how-to-write-links)를 참조 하세요.

## <a name="formatting-command-syntax-elements"></a>명령 구문 요소 서식 지정

- Cmdlet 및 매개 변수에는 항상 전체 이름을 사용 합니다. 별칭을 특별히 설명 하지 않는 한 별칭을 사용 하지 마십시오.

- 속성, 매개 변수, 개체, 형식 이름, 클래스 이름, 클래스 메서드는 **굵게 표시** 되어야 합니다.
  - 속성 및 매개 변수 값은 backtick ()으로 래핑해야 합니다 `` ` `` .
  - 대괄호로 묶은 스타일을 사용 하 여 형식을 참조 하는 경우에는 backticks을 사용 합니다. 예: `[System.Io.FileInfo]`

- 언어 키워드, cmdlet 이름, 함수, 변수, 네이티브 exe, 파일 경로 및 인라인 구문 예제는 억음 ( `` ` `` ) 문자로 래핑해야 합니다.

  다음은 그 예입니다. 

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - 이름으로 매개 변수를 참조하는 경우 이름은 **굵게** 표시되어야 합니다. 하이픈 접두사로 매개 변수 사용을 나타내는 경우 매개 변수는 억음 악센트로 래핑되어야 합니다. 다음은 그 예입니다.

    ```markdown
    The parameter's name is **Name**, but it's typed as `-Name` when used on the command
    line as a parameter.
    ```

  - 외부 명령의 사용 예제를 표시하는 경우 예제는 억음 악센트로 래핑되어야 합니다.
    항상 네이티브 명령에 파일 확장명을 포함 합니다. 다음은 그 예입니다. 

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    파일 확장명을 포함 하면 PowerShell의 명령 우선 순위에 따라 올바른 명령이 실행 됩니다.

- 개념 문서(참조 콘텐츠가 아님)를 작성하는 경우 cmdlet 이름의 첫 번째 인스턴스는 cmdlet 문서에 연결되어야 합니다. 하이퍼링크의 대괄호 안에는 backticks, 굵게 또는 기타 태그를 사용 하지 마세요.

  다음은 그 예입니다. 

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  자세한 내용은이 문서의 [하이퍼링크](#hyperlinks) 섹션을 참조 하세요.

## <a name="markdown-for-code-samples"></a>코드 샘플에 대 한 Markdown

Markdown은 다음 두 가지 코드 스타일을 지원합니다.

- **코드 범위 (인라인)** -단일 억음 ( `` ` `` ) 문자로 표시 됩니다. 독립 실행형 블록이 아닌 단락 내에서 사용 됩니다.
- **코드 블록** -삼중-backtick () 문자열로 묶은 여러 줄 블록 `` ``` `` 입니다. 코드 블록에는 backticks 뒤에 언어 레이블이 있을 수도 있습니다. 언어 레이블은 코드 블록의 내용에 대해 구문 강조 표시를 사용 하도록 설정 합니다.

모든 코드 블록은 코드 펜스에 포함되어야 합니다. 코드 블록에는 들여쓰기를 사용 하지 마십시오. Markdown는이 패턴을 허용 하지만 문제가 될 수 있으므로 피해 야 합니다.

코드 블록은 세 개의 코드 줄로, 삼중-백 틱 ( `` ``` `` ) 코드 펜스로 둘러싸여 있습니다.
코드 펜스 마커는 코드 샘플 앞 및 뒤의 고유한 줄에 있어야 합니다. 코드 블록 시작 부분의 마커에는 선택적 언어 레이블이 포함될 수 있습니다. Microsoft의 OPS(Open Publishing System)는 언어 레이블을 사용하여 구문 강조 표시 기능을 지원합니다.

지원 되는 언어 태그의 전체 목록은 중앙의 참여자 가이드에서 [친 코드 블록](/contribute/code-in-docs#fenced-code-blocks) 을 참조 하세요.

또한 OPS는 코드 블록의 콘텐츠를 클립보드에 복사하는 **복사** 단추를 추가합니다. 이렇게 하면 코드를 스크립트에 신속 하 게 붙여넣어 코드 샘플을 테스트할 수 있습니다. 그러나 설명서의 모든 예제를 그대로 실행 하기 위한 것은 아닙니다. 일부 코드 블록은 PowerShell 개념을 간단히 보여 줍니다.

설명서에 사용 되는 세 가지 유형의 코드 블록이 있습니다.

1. 구문 블록
1. 설명 예제
1. 실행 가능한 예제

### <a name="syntax-code-blocks"></a>구문 코드 블록

구문 코드 블록은 명령의 구문 구조를 설명 하는 데 사용 됩니다. 코드 fence에서 언어 태그를 사용 하지 마세요. 이 예제는 `Get-Command` cmdlet의 가능한 모든 매개 변수를 보여 줍니다.

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

이 예제는 `for` 문을 일반화된 용어로 설명합니다.

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a>설명 예제

설명 예제는 PowerShell 개념을 설명하는 데 사용됩니다. 실행을 위해 클립보드로 복사 되지 않습니다. 이러한 기능은 쉽게 입력 하 고 이해 하기 쉬운 간단한 예제에 가장 일반적으로 사용 됩니다. 코드 블록에는 PowerShell 프롬프트와 예제 출력이 포함 될 수 있습니다.

PowerShell 비교 연산자를 보여 주는 간단한 예제는 다음과 같습니다. 이 경우 독자가 이 예제를 복사하고 실행할 수 없습니다.

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

### <a name="executable-examples"></a>실행 가능한 예제

복사 및 실행 하기 위한 복잡 한 예제 또는 예제는 다음과 같은 블록 스타일 태그를 사용 해야 합니다.

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

PowerShell 명령으로 표시되는 출력은 구문 강조 표시를 방지하기 위해 **출력** 코드 블록으로 묶어야 합니다. 다음은 그 예입니다. 

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

**출력** 코드 레이블은 구문 강조 표시 시스템에서 지 원하는 공식 "언어"가 아닙니다.
그러나 OPS는 웹 페이지의 코드 상자 프레임에 "출력" 레이블을 추가 하기 때문에이 레이블은 유용 합니다. "출력" 코드 상자에는 강조 표시 된 구문이 없습니다.

## <a name="coding-style-rules"></a>코딩 스타일 규칙

### <a name="avoid-line-continuation-in-code-samples"></a>코드 샘플에 줄 연속을 사용하지 않음

PowerShell 코드 예제에서 줄 연속 문자(`` ` ``)를 사용하지 마세요. 줄 연속 문자는 확인하기 어려우며 줄 끝에 추가 공백이 있는 경우 문제를 초래할 수 있습니다.

- PowerShell 스 플랫을 사용 하 여 여러 매개 변수가 있는 cmdlet의 줄 길이를 줄입니다.
- 파이프 ( `|` ) 문자, 여는 중괄호 ( `{` ), 괄호 ( `(` ) 및 대괄호 ()와 같은 PowerShell의 자연 스러운 줄 바꿈 기회를 활용 `[` 합니다.

### <a name="avoid-using-powershell-prompts-in-examples"></a>예제에서 PowerShell 프롬프트를 사용하지 않음

프롬프트 문자열은 사용 하지 않는 것이 좋습니다. 명령줄 사용법을 보여 주는 시나리오로 제한 되어야 합니다. 대부분의 예제에서 프롬프트 문자열은 이어야 합니다 `PS>` . 이 프롬프트는 OS 특정 표시기와 관계가 없습니다.

프롬프트를 변경 하거나 표시 되는 경로가 시나리오에 중요 한 경우에는 프롬프트를 변경 하는 명령을 보여 주는 프롬프트가 필요 합니다. 다음 예제에서는 레지스트리 공급자를 사용할 때 프롬프트가 어떻게 변경되는지 보여 줍니다.

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

### <a name="dont-use-aliases-in-examples"></a>예제에서 별칭 사용 안 함

특별히 별칭을 문서화 하지 않는 한 모든 cmdlet 및 매개 변수의 전체 이름을 사용 합니다.
Cmdlet 및 매개 변수 이름은 적절 한 [파스칼식 대/소문자][] 이름을 사용 해야 합니다.

### <a name="using-parameters-in-examples"></a>예제에서 매개 변수 사용

위치 매개 변수를 사용하지 마세요. 일반적으로 매개 변수가 위치 이더라도 예에서는 매개 변수 이름을 항상 포함 해야 합니다. 이렇게 하면 예제에서 혼동할 가능성이 줄어듭니다.

## <a name="formatting-cmdlet-reference-articles"></a>서식 지정 cmdlet 참조 문서

Cmdlet 참조 문서에는 특정 구조가 있습니다. 이 구조는 [PlatyPS][]에 의해 정의됩니다.
PlatyPS는 Markdown의 PowerShell 모듈에 대 한 cmdlet 도움말을 생성 합니다. Markdown 파일을 편집한 후 PlatyPS는 `Get-Help` cmdlet에서 사용되는 MAML 도움말 파일을 만드는 데 사용됩니다.

PlatyPS에는 코드로 작성되는 cmdlet 참조용 하드 코드된 스키마가 있습니다. [platyPS.schema.md][] 문서는 이 구조를 설명하려고 합니다. 스키마 위반으로 인해 기여를 수락하기 전에 수정해야 하는 빌드 오류가 발생합니다.

- ATX 헤더 구조를 제거 하지 마세요. PlatyPS에는 특정 헤더 세트가 필요합니다.
- **입력 형식** 및 **출력 형식** 헤더에는 형식이 있어야 합니다. Cmdlet이 입력을 취하지 않거나 값을 반환 하지 않는 경우에는 값을 사용 `None` 합니다.
- 인라인 코드 범위는 모든 단락에서 사용할 수 있습니다.
- 친 코드 블록은 **예제** 섹션 에서만 허용 됩니다.

PlatyPS 스키마에서 **예제** 는 H2 헤더입니다. 각 예제는 H3 헤더입니다. 예제에서 스키마는 코드 블록을 단락으로 구분할 수 없도록 합니다. 스키마는 다음과 같은 구조를 허용 합니다.

```
### Example X - Title sentence

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

각 예제에 번호를 매기고 간단한 제목을 추가합니다.

다음은 그 예입니다. 

~~~markdown
### Example 1: Get cmdlets, functions, and aliases

This command gets the PowerShell cmdlets, functions, and aliases that are installed on the
computer.

```powershell
Get-Command
```

### Example 2: Get commands in the current session

```powershell
Get-Command -ListImported
```
~~~

## <a name="formatting-about_-files"></a>About_ 파일 서식 지정

`About_*` 파일은 Markdown로 작성 되지만 일반 텍스트 파일로 제공 됩니다. Markdown을 일반 텍스트로 변환 하는 [데 사용 됩니다][] . `About_*` 파일은 모든 버전의 PowerShell 및 게시 도구를 사용 하 여 최상의 호환성을 위해 포맷 됩니다.

기본 서식 지정 지침:

- 표준 줄을 80 자로 제한
- 코드 블록은 76 자로 제한 됩니다.
- 블록 따옴표 (및 경고)는 78 자로 제한 됩니다.
- 이러한 특수 한 메타 문자, 및를 사용 하는 경우 `\` `$` `<` :
  - 헤더 내에서 이러한 문자는 선행 문자를 사용 하 여 이스케이프 `\` 되거나 backtick ()을 사용 하 여 코드 범위에 포함 되어야 합니다. `` ` ``
  - 단락 내에서 이러한 문자를 코드 범위에 넣어야 합니다. 다음은 그 예입니다. 

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- 테이블이 76 자 이내에 부합 해야 합니다.
  - 여러 줄에서 셀 콘텐츠를 수동으로 래핑
  - 각 줄에서 여는 및 닫는 `|` 문자 사용
  - 다음 예에서는 셀 내에서 여러 줄로 래핑하는 정보가 포함 된 테이블을 올바르게 생성 하는 방법을 보여 줍니다.

    ~~~markdown
    ```
    |Operator|Description                |Example                          |
    |--------|---------------------------|---------------------------------|
    |`-is`   |Returns TRUE when the input|`(get-date) -is [DateTime]`      |
    |        |is an instance of the      |`True`                           |
    |        |specified .NET type.       |                                 |
    |`-isNot`|Returns TRUE when the input|`(get-date) -isNot [DateTime]`   |
    |        |not an instance of the     |`False`                          |
    |        |specified.NET type.        |                                 |
    |`-as`   |Converts the input to the  |`"5/7/07" -as [DateTime]`        |
    |        |specified .NET type.       |`Monday, May 7, 2007 12:00:00 AM`|
    ```
    ~~~

    > [!NOTE]
    > 76 열 제한은 항목에만 적용 됩니다 `About_*` . 개념 또는 cmdlet 참조 문서에서 넓은 열을 사용할 수 있습니다.

## <a name="next-steps"></a>다음 단계

[편집 검사 목록](editorial-checklist.md)

<!-- link references -->
[atx]: https://github.github.com/gfm/#atx-headings
[CommonMark]: https://spec.commonmark.org/
[markdig]: https://github.com/lunet-io/markdig
[Pandoc]: https://pandoc.org
[파스칼식-대/소문자]: https://en.wikipedia.org/wiki/PascalCase
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[PlatyPS]: https://github.com/powershell/platyps
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
[linkref]: https://spec.commonmark.org/0.29/#link-reference-definitions
