---
title: Windows PowerShell02 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082518"
---
# <a name="windows-powershell02-sample"></a>Windows PowerShell02 샘플

이 샘플에서는 runspace 풀의 runspace를 사용 하 여 명령을 비동기적으로 실행 하는 방법을 보여 줍니다. 샘플 명령의 목록을 생성 하 고 필요할 때 풀에서 runspace는 Windows PowerShell 엔진 열립니다 하는 동안 다음 해당 명령을 실행 합니다.

## <a name="requirements"></a>요구 사항

- 이 샘플 Windows PowerShell 2.0이 필요 합니다.

## <a name="demonstrates"></a>데모

이 샘플에는 다음 방법을 보여 줍니다.

- 최소 및 최대 수가 동시에 열 수를 허용 하는 runspace RunspacePool 개체를 만드는 중입니다.

- 명령 목록을 만드는 중입니다.

- 비동기적으로 명령을 실행 합니다.

- 호출 된 [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) 메서드를 얼마나 많은 runspace는 무료입니다.

- 명령 출력을 캡처하는 [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) 메서드.

## <a name="example"></a>예제

이 샘플에서는 runspace 풀을 runspace를 여는 방법 및 해당 runspace에서 명령을 비동기적으로 실행 하는 방법을 보여 줍니다.

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>참고 항목

[Windows PowerShell 호스트 응용 프로그램 작성](./writing-a-windows-powershell-host-application.md)