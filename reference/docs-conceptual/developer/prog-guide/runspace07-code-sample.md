---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace07 코드 샘플
description: RunSpace07 코드 샘플
ms.openlocfilehash: 6e8c9f48a6e9c5a642ecf93bca8a85003b3cfbf8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647390"
---
# <a name="runspace07-code-sample"></a>RunSpace07 코드 샘플

[파이프라인에 명령을 추가 하는 콘솔 응용 프로그램 만들기](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e)에서 설명한 Runspace07 샘플의 소스 코드는 다음과 같습니다.
이 샘플 응용 프로그램은 runspace를 만들고, 파이프라인을 만들고, 파이프라인에 두 개의 명령을 추가한 후 파이프라인을 실행 합니다. 파이프라인에 추가 되는 명령은 `Get-Process` 및 `Measure-Object` cmdlet입니다.

> [!NOTE]
> Windows Vista 용 Microsoft Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여 c # 소스 파일 (runspace07.cs)을 다운로드할 수 있습니다. 다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.
> 다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .

## <a name="code-sample"></a>코드 예제

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs" range="11-108":::

## <a name="see-also"></a>참고 항목

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
