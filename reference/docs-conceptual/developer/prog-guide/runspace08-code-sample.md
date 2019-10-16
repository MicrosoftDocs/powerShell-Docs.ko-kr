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
ms.openlocfilehash: 20032913969606f722f3768b0433775aeaa8c3a8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366482"
---
# <a name="runspace08-code-sample"></a>RunSpace08 코드 샘플

다음은 [명령에 매개 변수를 추가 하는 콘솔 응용 프로그램 만들기](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba)에서 설명한 Runspace08 샘플의 소스 코드입니다. 이 샘플 응용 프로그램은 runspace를 만들고, 파이프라인을 만들고, 파이프라인에 두 개의 명령을 추가 하 고, 두 번째 명령에 두 개의 매개 변수를 추가한 다음, 파이프라인을 실행 합니다. 파이프라인에 추가 되는 명령은 `Get-Process` 및 `Sort-Object` cmdlet입니다.

## <a name="code-sample"></a>코드 샘플

[!code-csharp[Runspace08.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a>참고 항목

[Windows PowerShell SDK](../windows-powershell-reference.md)
