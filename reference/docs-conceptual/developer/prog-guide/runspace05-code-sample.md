---
title: RunSpace05 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: 4d9a2db76fe69a8509d33a22124f5f952b1d3c80
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978307"
---
# <a name="runspace05-code-sample"></a>RunSpace05 코드 샘플

다음은 [RunspaceConfiguration를 사용 하 여 Runspace 구성](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2)에 설명 된 Runspace05 샘플에 대 한 소스 코드입니다.
이 샘플에서는 runspace 구성 정보를 만들고, runspace를 만들고, 단일 명령을 사용 하 여 파이프라인을 만들고, 파이프라인을 실행 하는 방법을 보여 줍니다. 실행 되는 명령은 `Get-Process` cmdlet입니다.

> [!NOTE]
> Windows Vista 용 Microsoft C# Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여 원본 파일 (runspace05.cs)을 다운로드할 수 있습니다. 다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.
> 다운로드 된 원본 파일은 **\<PowerShell Samples >** 디렉터리에서 사용할 수 있습니다.

## <a name="code-sample"></a>코드 예제

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs" range="11-86":::

## <a name="see-also"></a>참고 항목

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
