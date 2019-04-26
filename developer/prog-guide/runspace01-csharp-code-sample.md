---
title: Runspace01 (C#) 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 59320365c4a35c3d71af10273eb21b1ce01e5c0c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081464"
---
# <a name="runspace01-c-code-sample"></a>Runspace01(C#) 코드 샘플

에 설명 된 runspace에 대 한 코드 예제는 다음과 같습니다 [콘솔 응용 프로그램을 실행 지정 명령 만들기](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e)합니다. 이렇게 하려면 응용 프로그램 runspace를 호출 하 고 명령을 호출 합니다. (이 응용 프로그램에서 runspace 구성 정보를 지정 하지도 않습니다이 명시적으로 파이프라인 만들기는 note). 호출 되는 명령입니다는 `Get-Process` cmdlet.

> [!NOTE]
> 다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및 Microsoft.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 runspace에 대 한 원본 파일 (runspace01.cs). 다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.
>
> 다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.

## <a name="code-sample"></a>코드 예제

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a>참고 항목

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)