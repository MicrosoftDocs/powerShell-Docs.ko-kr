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
ms.openlocfilehash: abf19d848f6150d005c63bb0fc2ffbe1de405e2a
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734964"
---
# <a name="runspace05-code-sample"></a>RunSpace05 코드 샘플

여기에 설명 된 Runspace05 샘플에 대 한 소스 코드를입니다 [Runspace를 사용 하 여 RunspaceConfiguration 구성](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2)합니다. 이 샘플 runspace 구성 정보를 runspace, 단일 명령으로 파이프라인을 만들 만들고 파이프라인을 실행 한 다음 방법을 보여 줍니다. 실행 되는 명령입니다는 `Get-Process` cmdlet.

> [!NOTE]
> 다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및 Microsoft.NET Framework 3.0 런타임 구성 요소를 사용 하 여 원본 파일 (runspace05.cs). 다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.
>
> 다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.

## <a name="code-sample"></a>코드 예제

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a>관련 항목

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)