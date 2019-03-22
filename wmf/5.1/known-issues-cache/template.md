---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: 알려진 문제 및 제한 사항 기록에 대한 예제 템플릿
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794497"
---
 >참고: 제안된 설명이 포함된 제목과 간단한 설명을 제공합니다.

## <a name="example-erroneous-executionpolicy-errors"></a>예: 잘못된 ExecutionPolicy 오류
Windows 7에서 PowerShell 모듈 및 DSC 리소스를 사용하면 ExecutionPolicy에 대해 오류가 보고될 수 있습니다.

### <a name="resolution"></a>해결 방법

해결하려면 다음 명령을 관리자 권한 PowerShell 세션에서 실행(관리자 권한으로 실행)하여 **ExecutionPolicy**를 **RemoteSigned**로 설정합니다.

```powershell
Set-ExecutionPolicy RemoteSigned
```
