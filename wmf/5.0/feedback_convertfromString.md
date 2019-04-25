---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: fcf2adf67f36edb534df3e2a849459fb20e1c2de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085357"
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a>문자열에서 구조화된 개체 추출 및 구문 분석

또한 `ConvertFrom-String` cmdlet에 대해 몇 가지 추가 기능이 도입되었습니다.

- 기본적으로 범위 텍스트 속성을 제거합니다. -IncludeExtent 매개 변수와 함께 포함할 수 있습니다.

- MVP 및 커뮤니티 피드백으로 많은 학습 알고리즘 버그 수정

- 학습 알고리즘의 결과를 템플릿 파일의 설명에 저장하는 새로운 -UpdateTemplate 매개 변수. 이 매개 변수는 학습 프로세스(가장 느린 단계)를 일회 비용으로 만듭니다. 인코딩된 학습 알고리즘이 포함된 템플릿에서 Convert-String을 실행하면 거의 즉각적입니다.

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a>문자열 콘텐츠에서 구조화된 개체 추출 및 구문 분석

[Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F)와 공동 작업으로 새로운 `ConvertFrom-String` cmdlet을 추가했습니다.

이 cmdlet은 기본적인 구분 구문 분석 및 자동 생성된 예제 기반 구문 분석의 두 가지 모드를 지원합니다.

기본적으로 구분 구문 분석에서는 입력을 공백으로 분할하고 결과 그룹에 속성 이름을 할당합니다. 다음과 같이 구분 기호를 사용자 지정할 수 있습니다.

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

또한 cmdlet은 [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F)의 [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) 조사 작업에 따라 자동 생성된 예제 기반 구문 분석도 지원합니다.

텍스트 기반 주소록을 사용하여 시작합니다.

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA
```

몇 가지 예제를 템플릿으로 사용할 파일에 복사합니다.

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

추출하려는 데이터를 중괄호로 묶고 이름을 지정합니다. **이름** 속성(및 연결된 다른 속성)이 여러 번 나타날 수 있으므로 별표(\*)를 사용하여 많은 속성을 하나의 레코드로 추출하지 않고 여러 레코드로 추출함을 나타냅니다.

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

이 예제 집합에서 `ConvertFrom-String`은 입력 파일에서 유사한 구조를 가진 개체 기반 출력을 자동으로 추출할 수 있습니다.

```powershell
Get-Content .\addresses.output.txt | ConvertFrom-String -TemplateFile .\addresses.template.txt | Format-Table -Auto
```

```output
ExtentText                     Name               City     State
----------                     ----               ----     -----
Ana Trujillo...                Ana Trujillo       Redmond  WA
Antonio Moreno...              Antonio Moreno     Renton   WA
Thomas Hardy...                Thomas Hardy       Seattle  WA
Christina Berglund...          Christina Berglund Redmond  WA
Hanna Moos...                  Hanna Moos         Puyallup WA
```

추출된 텍스트에서 추가 데이터 조작을 수행하기 위해 **ExtentText** 속성은 레코드가 추출된 원시 텍스트를 캡처합니다. 이 기능에 대한 사용자 의견을 제공하거나 예제를 작성하는 데 문제가 있는 콘텐츠를 공유하려면 <psdmfb@microsoft.com>으로 메일을 보내주세요.