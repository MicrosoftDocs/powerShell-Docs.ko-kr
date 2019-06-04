---
title: 스크립트에서 주석 기반 도움말을 배치 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083232"
---
# <a name="placing-comment-based-help-in-scripts"></a>스크립트에 설명 기반 도움말 배치

이 항목에서는 스크립트에 대 한 설명 기반 도움말을 배치 하는 위치를 설명 하는 `Get-Help` cmdlet 스크립트와 스크립트에 있을 수 있는 모든 함수를 사용 하 여 하지 설명 기반 도움말 항목을 연결 합니다.

## <a name="where-to-place-comment-based-help-for-a-script"></a>스크립트에 대 한 설명 기반 도움말을 배치 하는 위치

- 스크립트 파일의 부분입니다. 스크립트 도움말 스크립트에서 주석 및 빈 줄에 의해서만 올 수 있습니다.

- 스크립트 파일의 끝입니다.

  함수 선언 (도움말) 한 후 스크립트 본문의 첫 번째 항목을 사용 하는 경우 도움말 스크립트의 끝 사이의 함수 선언 두 개 이상의 빈 줄 이어야 합니다. 이 고, 그렇지 도움말은 도움말 스크립트에 대 한 도움말이 없습니다 함수에 대 한 것으로 해석 됩니다.

## <a name="examples-of-help-placement-in-a-script"></a>도움말 배치 스크립트에서의 예

 다음 예제에서는 각 스크립트에 대 한 설명 기반 도움말에 대 한 배치 옵션을 표시 합니다.

### <a name="help-at-the-beginning-of-a-script"></a>스크립트의 시작 부분에 있는 도움말

 다음 예제에서는 스크립트의 시작 부분에서 주석 기반를 보여 줍니다.

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>스크립트의 끝에 있는 도움말

 다음 예제에서는 스크립트의 끝 주석 기반 보여 줍니다.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```