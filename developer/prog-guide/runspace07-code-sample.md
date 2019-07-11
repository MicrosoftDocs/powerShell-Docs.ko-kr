---
title: RunSpace07 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 232b282e366c9fad167686337696ef2ccd8b30d8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734951"
---
# <a name="runspace07-code-sample"></a>RunSpace07 코드 샘플

설명 된 Runspace07 샘플에 대 한 소스 코드를 다음과 같습니다 [는 콘솔 응용 프로그램을 추가 명령 파이프라인에 만드는](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e)합니다. 이 샘플 응용 프로그램 runspace를 만들고, 파이프라인을 만듭니다, 그리고 파이프라인에 두 개의 명령을 추가 및 다음 파이프라인을 실행 합니다. 명령 파이프라인에 추가 되는 `Get-Process` 고 `Measure-Object` cmdlet.

> [!NOTE]
> 다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및 Microsoft.NET Framework 3.0 런타임 구성 요소를 사용 하 여 원본 파일 (runspace07.cs). 다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.
>
> 다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.

## <a name="code-sample"></a>코드 예제

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a>참고 항목

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)