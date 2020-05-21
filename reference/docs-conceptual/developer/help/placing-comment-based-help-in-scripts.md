---
title: 스크립트에 주석 기반 도움말 배치 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: 1bebfbd822963830363012060067c656d7709543
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565529"
---
# <a name="placing-comment-based-help-in-scripts"></a>스크립트에 설명 기반 도움말 배치

이 항목에서는 스크립트 `Get-Help` 에서 주석 기반 도움말 항목을 스크립트에 연결 하 고 스크립트에 포함 될 수 있는 함수와 연결 하지 않도록 스크립트에 대 한 주석 기반 도움말을 넣을 위치에 대해 설명 합니다.

## <a name="where-to-place-comment-based-help-for-a-script"></a>스크립트에 대 한 주석 기반 도움말을 넣을 위치

- 스크립트 파일의 시작 부분에 있습니다. 스크립트 도움말은 주석 및 빈 줄만 스크립트에 추가할 수 있습니다.

- 스크립트 파일의 끝에 있습니다.

  스크립트 본문의 첫 번째 항목 (도움말)이 함수 선언 인 경우 스크립트 도움말과 함수 선언 끝 사이에 두 개 이상의 빈 줄이 있어야 합니다. 그렇지 않으면 도움말은 스크립트에 대 한 도움말이 아니라 함수에 대 한 도움말로 해석 됩니다.

## <a name="examples-of-help-placement-in-a-script"></a>스크립트의 도움말 배치 예

 다음 예에서는 스크립트에 대 한 주석 기반 도움말의 각 배치 옵션을 보여 줍니다.

### <a name="help-at-the-beginning-of-a-script"></a>스크립트의 시작 부분에 있는 도움말

 다음 예에서는 스크립트의 시작 부분에 있는 주석 기반을 보여 줍니다.

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>스크립트의 끝에 있는 도움말

 다음 예에서는 스크립트의 끝에 있는 주석 기반을 보여 줍니다.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```
