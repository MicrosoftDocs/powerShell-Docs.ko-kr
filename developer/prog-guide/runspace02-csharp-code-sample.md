---
title: Runspace02 (C#) 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59a7b8b9-f72e-43fd-9a10-77404441a3f2
caps.latest.revision: 6
ms.openlocfilehash: 0a8fc05db74529e2bfb88820b9cfd988245e0aeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854619"
---
# <a name="runspace02-c-code-sample"></a>Runspace02(C#) 코드 샘플

다음은 C# Runspace02 샘플의 소스 코드입니다. 이 샘플에서는 합니다 [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 실행 하는 클래스는 `Get-Process` cmdlet 동기적으로 합니다. 데이터 바인딩 및 Windows Forms DataGridView 컨트롤에서 결과 표시 하려면 사용 됩니다.

## <a name="code-sample"></a>코드 예제

[!code-csharp[Runspace02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs#L11-L82 "Runspace02.cs")]

## <a name="see-also"></a>참고 항목

[Windows PowerShell SDK](../windows-powershell-reference.md)