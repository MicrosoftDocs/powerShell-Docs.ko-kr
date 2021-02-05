---
title: 편집 검사 목록
description: PowerShell 설명서를 편집하기 위한 규칙의 요약된 목록입니다.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: b5baf7366239084779d34e23f218e5e6222ed1a3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "81624740"
---
# <a name="editors-checklist"></a>편집자 검사 목록

새 문서를 작성하거나 기존 문서를 업데이트할 때 적용할 규칙의 요약입니다. 이러한 규칙에 대한 자세한 설명과 예제는 참가자 가이드의 다른 문서를 참조하세요.

## <a name="metadata"></a>메타데이터

- `ms.date`: **MM/DD/YYYY** 형식이어야 함
  - 주요 또는 팩트 업데이트가 있는 날짜 변경
    - 문서 재구성
    - 실제 오류 수정
    - 새 정보 추가
  - 주요 업데이트가 아닌 경우 날짜를 변경하지 않음
    - 오타 또는 서식 수정
- `title`: 공백 포함 43~59자의 고유한 문자열
  - 사이트 식별자를 포함하지 않음(자동 생성됨)
  - 문장 대문자 사용 - 첫 번째 단어와 고유명사만 대문자로 시작
- `description`: 115~145자(공백 포함) - 이 요약이 검색 결과에 표시됨

## <a name="formatting"></a>서식 지정

- 단락 안에 인라인으로 표시되는 역따옴표 구문 요소
  - Cmdlet 이름 `Verb-Noun`
  - 변수 `$counter`
  - 구문 예제 `Verb-Noun -Parameter`
  - 파일 경로 `C:\Program Files\PowerShell`, `/usr/bin/pwsh`
  - 문서에서 클릭할 수 없는 URL
  - 속성 또는 매개 변수 값
- 속성 이름, 매개 변수 이름, 클래스 이름, 모듈 이름, 엔터티 이름, 개체 또는 형식 이름을 굵게 표시
  - 굵게는 강조 표시가 아니라 의미 체계 태그에 사용
  - 굵게 - 별표 `**` 사용
- 기울임꼴 - 밑줄 `_` 사용
  - 의미 체계 태그가 아니라 강조 표시에만 사용
- 100열에서 줄 바꿈(또는 **about_Topics** 의 경우 80열)
- 하드 탭 없음 - 공백만 사용
- 줄에 후행 공백 없음

### <a name="headers"></a>headers

- H1이 첫 번째 - H1은 문서당 1개만
- [ATX 헤더](https://github.github.com/gfm/#atx-headings)만 사용
- 모든 헤더에 문장 대문자 사용
- 수준 건너뛰지 않음 - H2 없이 H3 없음
- H3 또는 H4의 최대 깊이
- 앞뒤의 빈 줄
- PlatyPS는 해당 스키마에 특정 헤더를 적용 - 헤더를 추가 또는 제거하지 마세요.

### <a name="code-blocks"></a>코드 블록

- 앞뒤의 빈 줄
- 태그가 지정된 코드 펜스를 사용 - **powershell**, **Output** 또는 기타 적절한 언어 ID
- 태그가 없는 펜스 - 구문 블록 또는 기타 셸
- 개별 코드 블록에 출력을 배치(독자가 **Copy** 단추를 사용할 필요가 없는 간단한 예제는 제외)
- [지원되는 언어](/contribute/code-in-docs#supported-languages) 목록 참조

### <a name="lists"></a>목록

- 올바르게 들여쓰기
- 첫 번째 항목 앞과 마지막 항목 뒤의 빈 줄
- 글머리 기호 - 별표(`*`)가 아니라 하이픈(`-`)을 사용 - 강조와 혼동하기 쉬움
- 번호가 매겨진 목록의 경우 모든 숫자는 "1."입니다.

## <a name="terminology"></a>용어

- PowerShell vs. Windows PowerShell vs. PowerShell Core
- [제품 용어](powershell-style-guide.md#product-terminology) 참조

## <a name="cmdlet-reference-examples"></a>Cmdlet 참조 예제

- Cmdlet 참조에는 하나 이상의 예제가 있어야 합니다.
- 예제는 사용법을 보여 주는 코드면 충분합니다.
- PowerShell 구문
  - Cmdlet 및 매개 변수에 별칭이 아니라 전체 이름을 사용합니다.
  - 명령줄이 너무 길면 매개 변수에 스플랫을 사용합니다.
  - 줄 연속 역따옴표는 가급적 사용하지 않습니다(필요할 때만 사용).
- 예제에 필요한 경우를 제외하고 PowerShell 프롬프트(`PS>`)를 제거 또는 단순화합니다.
- Cmdlet 참조 예제는 다음 PlatyPS 스키마를 따라야 합니다.

  ~~~Markdown
  ### Example 1 - Descriptive title

  Zero or more short descriptive paragraphs explaining the context of the example followed by one or
  more code blocks. Recommend at least one and no more than two.

  ```powershell
  ... one or more PowerShell code statements ...
  ```

  ```Output
  Example output of the code above.
  ```

  Zero or more optional follow up paragraphs that explain the details of the code and output.
  ~~~

- 코드 블록 사이에 단락을 넣지 마십시오. 모든 설명 콘텐츠는 코드 블록 앞 또는 뒤에 와야 합니다.

## <a name="linking-to-other-documents"></a>다른 문서 연결

- Docset 외부 또는 cmdlet 참조와 개념 간에 연결
  - docs.microsoft.com에 연결할 때 상대 URL을 사용합니다(`https://docs.microsoft.com/en-us`를 제거).
  - Microsoft 속성의 Url에 로캘을 포함하지 않습니다(예: URL에서 `/en-us`를 제거).
  - 외부 웹 사이트에 대한 모든 URL은 대상 사이트에 유효하지 않은 경우가 아니라면 HTTPS를 사용해야 합니다.
- Docset 내에서
  - 파일 경로에 대한 링크(예: `../folder/file.md`)
  - 모든 파일 경로에 슬래시(`/`) 문자를 사용
- 이미지 링크에는 고유한 대체 텍스트가 있어야 합니다.
