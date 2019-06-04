---
title: RunSpace06 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: d0330f082262b68486a582ed95c7a520be1e184c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081311"
---
# <a name="runspace06-code-sample"></a>RunSpace06 코드 샘플

에 설명 된 Runspace06 샘플에 대 한 소스 코드입니다 [Windows PowerShell 스냅인을 사용 하 여 Runspace 구성](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83)합니다. 이 샘플 응용 프로그램 기준으로 Windows PowerShell 스냅인, 단일 명령을 사용 하 여 파이프라인 실행을 사용 하는 runspace를 만듭니다. 이 위해 응용 프로그램 runspace 구성 정보를 생성, runspace를 만드는, 단일 명령을 사용 하 여 파이프라인을 만듭니다 및 다음 파이프라인을 실행 합니다.

> [!NOTE]
> 다운로드할 수 있습니다는 C# Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및 Microsoft.NET Framework 3.0 런타임 구성 요소를 사용 하 여 원본 파일 (runspace06.cs). 다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.
>
> 다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.

## <a name="code-sample"></a>코드 예제

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a>참고 항목

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)