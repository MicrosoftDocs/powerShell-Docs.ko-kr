---
title: 주석 기반 도움말 구문의 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855549"
---
# <a name="syntax-of-comment-based-help"></a>설명 기반 도움말 구문

이 섹션에 설명 기반 도움말의 구문을 설명합니다.

## <a name="syntax-diagram"></a>구문 다이어그램

 주석 기반 도움말에 대 한 구문은 다음과 같습니다.

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

 주석 기반 도움말은 일련의 주석으로 기록 됩니다. 주석, 각 줄 앞에 주석 기호 (#)를 입력 하거나 사용할 수는 "\<#" 및 "#>" 기호를 주석 블록을 만듭니다. 주석 블록 내에서 모든 줄을 주석으로 해석 됩니다.

 각 섹션에 설명 기반 도움말 키워드 정의한 각 키워드는 점 (.) 뒤에 키워드는 임의의 순서로 나타날 수 있습니다. 키워드 이름은 대/소문자 구분 하지 않습니다.

 주석 블록에는 도움말 키워드를 하나 이상 있어야 합니다. 동일한 주석 블록에 여러 번 나타날 수 일부의 예제와 같은 키워드입니다. 각 키워드에 대 한 도움말 콘텐츠를 키워드 다음 줄에서 시작 하 고 여러 줄으로 나누어 입력할 수 있습니다.

 주석 기반 도움말 항목의 줄을 모두 연속적 이어야 합니다. 주석 기반 도움말 항목의 도움말 항목을 포함 되지 않은 주석 같이 마지막 아닌 도움말 주석 줄과 설명 기반 도움말의 시작 부분 사이의 빈 줄을 하나 이상 이어야 합니다.

 예를 들어, 다음 설명 기반 도움말 항목을 포함 합니다. 설명 키워드와 해당 값은 함수 또는 스크립트의 설명입니다.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```