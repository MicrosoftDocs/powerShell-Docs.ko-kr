---
title: RunSpace08 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 1a09cfee3bb317de6c1ca4dde86a87d72a498e6e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081277"
---
# <a name="runspace08-code-sample"></a>RunSpace08 코드 샘플

에 설명 된 Runspace08 샘플에 대 한 소스 코드를 다음과 같습니다 [는 콘솔 응용 프로그램을 추가 매개 변수를 만드는 명령](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba)입니다. 이 샘플 응용 프로그램 runspace, 파이프라인을 만듭니다, 그리고 파이프라인에 두 개의 명령을 추가, 두 번째 명령은 두 개의 매개 변수 추가 만들고 파이프라인을 실행 합니다. 파이프라인에 추가 되는 명령은 합니다 `Get-Process` 고 `Sort-Object` cmdlet.

## <a name="code-sample"></a>코드 예제

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a>참고 항목

[Windows PowerShell SDK](../windows-powershell-reference.md)