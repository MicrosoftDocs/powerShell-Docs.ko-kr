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
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="0059f-102">문자열에서 구조화된 개체 추출 및 구문 분석</span><span class="sxs-lookup"><span data-stu-id="0059f-102">Extract and Parse Structured Objects out of String</span></span>

<span data-ttu-id="0059f-103">또한 `ConvertFrom-String` cmdlet에 대해 몇 가지 추가 기능이 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0059f-103">This also introduces some additional functionality for the `ConvertFrom-String` cmdlet:</span></span>

- <span data-ttu-id="0059f-104">기본적으로 범위 텍스트 속성을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0059f-104">Removes the extent text property by default.</span></span> <span data-ttu-id="0059f-105">-IncludeExtent 매개 변수와 함께 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0059f-105">You can include it with the -IncludeExtent parameter.</span></span>

- <span data-ttu-id="0059f-106">MVP 및 커뮤니티 피드백으로 많은 학습 알고리즘 버그 수정</span><span class="sxs-lookup"><span data-stu-id="0059f-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

- <span data-ttu-id="0059f-107">학습 알고리즘의 결과를 템플릿 파일의 설명에 저장하는 새로운 -UpdateTemplate 매개 변수.</span><span class="sxs-lookup"><span data-stu-id="0059f-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="0059f-108">이 매개 변수는 학습 프로세스(가장 느린 단계)를 일회 비용으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0059f-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="0059f-109">인코딩된 학습 알고리즘이 포함된 템플릿에서 Convert-String을 실행하면 거의 즉각적입니다.</span><span class="sxs-lookup"><span data-stu-id="0059f-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="0059f-110">문자열 콘텐츠에서 구조화된 개체 추출 및 구문 분석</span><span class="sxs-lookup"><span data-stu-id="0059f-110">Extract and parse structured objects out of string content</span></span>

<span data-ttu-id="0059f-111">[Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F)와 공동 작업으로 새로운 `ConvertFrom-String` cmdlet을 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="0059f-111">In collaboration with [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), a new `ConvertFrom-String` cmdlet has been added.</span></span>

<span data-ttu-id="0059f-112">이 cmdlet은 기본적인 구분 구문 분석 및 자동 생성된 예제 기반 구문 분석의 두 가지 모드를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0059f-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="0059f-113">기본적으로 구분 구문 분석에서는 입력을 공백으로 분할하고 결과 그룹에 속성 이름을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="0059f-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="0059f-114">다음과 같이 구분 기호를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0059f-114">You can customize the delimiter:</span></span>

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

<span data-ttu-id="0059f-115">또한 cmdlet은 [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F)의 [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) 조사 작업에 따라 자동 생성된 예제 기반 구문 분석도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0059f-115">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) research work in [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).</span></span>

<span data-ttu-id="0059f-116">텍스트 기반 주소록을 사용하여 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0059f-116">To get started, consider a text-based address book:</span></span>

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

<span data-ttu-id="0059f-117">몇 가지 예제를 템플릿으로 사용할 파일에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="0059f-117">Copy a few examples into a file, which you will use as your template:</span></span>

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

<span data-ttu-id="0059f-118">추출하려는 데이터를 중괄호로 묶고 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0059f-118">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="0059f-119">**이름** 속성(및 연결된 다른 속성)이 여러 번 나타날 수 있으므로 별표(\*)를 사용하여 많은 속성을 하나의 레코드로 추출하지 않고 여러 레코드로 추출함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0059f-119">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

<span data-ttu-id="0059f-120">이 예제 집합에서 `ConvertFrom-String`은 입력 파일에서 유사한 구조를 가진 개체 기반 출력을 자동으로 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0059f-120">From this set of examples, `ConvertFrom-String` can now automatically extract object-based output from input files with similar structure.</span></span>

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

<span data-ttu-id="0059f-121">추출된 텍스트에서 추가 데이터 조작을 수행하기 위해 **ExtentText** 속성은 레코드가 추출된 원시 텍스트를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="0059f-121">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="0059f-122">이 기능에 대한 사용자 의견을 제공하거나 예제를 작성하는 데 문제가 있는 콘텐츠를 공유하려면 <psdmfb@microsoft.com>으로 메일을 보내주세요.</span><span class="sxs-lookup"><span data-stu-id="0059f-122">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>