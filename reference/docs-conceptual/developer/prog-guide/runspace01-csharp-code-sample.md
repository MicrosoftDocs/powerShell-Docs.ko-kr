---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace01(C#) 코드 샘플
description: Runspace01(C#) 코드 샘플
ms.openlocfilehash: e6121c144e1a4c1a1d9460d01119f44ee5835821
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657156"
---
# <a name="runspace01-c-code-sample"></a>Runspace01(C#) 코드 샘플

다음은 [지정 된 명령을 실행 하는 콘솔 응용 프로그램 만들기](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program)에서 설명 하는 runspace에 대 한 코드 샘플입니다.
이렇게 하기 위해 응용 프로그램은 runspace를 호출한 다음 명령을 호출 합니다. 이 응용 프로그램은 runspace 구성 정보를 지정 하지 않으며 파이프라인을 명시적으로 만들지 않습니다. 호출 되는 명령은 `Get-Process` cmdlet입니다.

> [!NOTE]
> Windows Vista 용 Microsoft Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 runspace에 대 한 c # 소스 파일 (runspace01.cs)을 다운로드할 수 있습니다.
> 다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.
> 다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .

## <a name="code-sample"></a>코드 예제

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs" range="11-62":::

## <a name="see-also"></a>참고 항목

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
