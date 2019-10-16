---
title: 함수에 주석 기반 도움말 배치 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367782"
---
# <a name="placing-comment-based-help-in-functions"></a>함수에 설명 기반 도움말 배치

이 항목에서는 `Get-Help` cmdlet이 주석 기반 도움말 항목을 올바른 함수와 연결 하도록 함수에 대 한 주석 기반 도움말을 저장 하는 위치에 대해 설명 합니다.

## <a name="where-to-place-comment-based-help-for-a-function"></a>함수에 대 한 주석 기반 도움말을 넣을 위치

- 함수 본문의 시작 부분에 있습니다.

- 함수 본문의 끝에 있습니다.

- @No__t-0 키워드 앞에 있습니다. 함수가 스크립트나 스크립트 모듈에 있는 경우 주석 기반 도움말의 마지막 줄과 `Function` 키워드 사이에 빈 줄이 둘 이상 있을 수 없습니다. 그렇지 않으면 `Get-Help`은 함수가 아닌 스크립트와 도움말을 연결 합니다.

## <a name="examples-of-help-placement-in-a-function"></a>함수의 도움말 배치 예

 다음 예제에서는 함수에 대 한 주석 기반 도움말의 세 가지 배치 옵션을 각각 보여 줍니다.

### <a name="help-at-the-beginning-of-a-function-body"></a>함수 본문의 시작 부분에 있는 도움말

 다음 예제에서는 함수 본문의 시작 부분에 있는 주석 기반을 보여 줍니다.

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a>함수 본문의 끝에 있는 도움말

 다음 예제에서는 함수 본문의 끝에 있는 주석 기반을 보여 줍니다.

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a>Function 키워드 앞의 도움말

 다음 예제에서는 함수 키워드 앞의 줄을 기반으로 하는 주석 기반을 보여 줍니다.

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```