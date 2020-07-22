---
title: 설명 기반 도움말 구문
ms.date: 09/12/2016
ms.openlocfilehash: 950afecc39f9d27207f77547679faab700481458
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893223"
---
# <a name="syntax-of-comment-based-help"></a>설명 기반 도움말 구문

이 섹션에서는 주석 기반 도움말의 구문에 대해 설명 합니다.

## <a name="syntax-diagram"></a>구문 다이어그램

 주석 기반 도움말의 구문은 다음과 같습니다.

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a>구문 설명

 주석 기반 도움말은 일련의 주석으로 작성 됩니다. 주석의 각 줄 앞에 주석 기호 ()를 입력 `#` 하거나 `<#` 및 기호를 사용 하 여 `#>` 주석 블록을 만들 수 있습니다. 주석 블록 내의 모든 줄은 주석으로 해석 됩니다.

 주석 기반 도움말의 각 섹션은 키워드로 정의 되며 각 키워드 앞에 점 ( `.` )이 있습니다. 키워드는 순서에 관계 없이 나타날 수 있습니다. 키워드 이름은 대/소문자를 구분 하지 않습니다.

 주석 블록은 하나 이상의 도움말 키워드를 포함 해야 합니다. **예제**와 같은 일부 키워드는 동일한 주석 블록에 여러 번 나타날 수 있습니다. 각 키워드에 대 한 도움말 콘텐츠는 키워드 뒤의 줄에서 시작 하 여 여러 줄에 걸쳐 있을 수 있습니다.

 주석 기반 도움말 항목의 모든 줄은 연속적 이어야 합니다. 주석 기반 도움말 항목이 도움말 항목에 포함 되지 않은 주석을 따르는 경우에는 마지막으로 지원 되지 않는 주석 줄과 주석 기반 도움말의 시작 부분 사이에 하나 이상의 빈 줄이 있어야 합니다.

 예를 들어 다음 주석 기반 도움말 항목에는가 포함 되어 있습니다. 함수 또는 스크립트에 대 한 설명 인 description 키워드와 해당 값입니다.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```
