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
ms.openlocfilehash: c3ae45ae9587bd130bbe9bb65ef47dc246f6e465
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417908"
---
# <a name="runspace06-code-sample"></a>RunSpace06 코드 샘플

[Windows PowerShell 스냅인을 사용 하 여 Runspace 구성](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83)에 설명 된 Runspace06 샘플의 소스 코드는 다음과 같습니다. 이 샘플 응용 프로그램은 단일 명령을 사용 하 여 파이프라인을 실행 하는 데 사용 되는 Windows PowerShell 스냅인을 기반으로 runspace를 만듭니다. 이렇게 하기 위해 응용 프로그램은 runspace 구성 정보를 만들고, runspace를 만들고, 단일 명령을 사용 하 여 파이프라인을 만든 다음, 파이프라인을 실행 합니다.

> [!NOTE]
> Windows Vista 용 Windows C# 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여 원본 파일 (runspace06.cs)을 다운로드할 수 있습니다. 다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.
>
> 다운로드 된 원본 파일은 **\<PowerShell Samples >** 디렉터리에서 사용할 수 있습니다.

## <a name="code-sample"></a>코드 예제

[!code-csharp[Runspace06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a>관련 항목

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
