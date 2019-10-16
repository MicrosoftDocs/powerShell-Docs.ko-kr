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
ms.openlocfilehash: db7ff3a2dbd92f562379d206db494ab92ef08736
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367302"
---
# <a name="windows-powershell02-sample"></a>Windows PowerShell02 샘플

이 샘플에서는 runspace 풀의 runspace을 사용 하 여 비동기적으로 명령을 실행 하는 방법을 보여 줍니다. 이 샘플에서는 명령 목록을 생성 한 다음, Windows PowerShell 엔진이 필요할 때 풀에서 runspace를 열 때 해당 명령을 실행 합니다.

## <a name="requirements"></a>요구 사항

- 이 샘플에는 Windows PowerShell 2.0이 필요 합니다.

## <a name="demonstrates"></a>보여

이 샘플은 다음을 보여 줍니다.

- 최소 및 최대 runspace 수를 사용 하 여 RunspacePool 개체를 만들고 동시에 열 수 있도록 허용 합니다.

- 명령 목록을 만듭니다.

- 비동기적으로 명령을 실행 합니다.

- [Runspace Runspacepool. Getavailablerunspaces *](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) 메서드를 호출 하 여 사용 가능한 runspace의 수를 확인 합니다.

- [System.object](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) 를 사용 하 여 명령 출력을 캡처합니다.

## <a name="example"></a>예제

이 샘플에서는 runspace 풀의 runspace를 여는 방법과 이러한 runspace에서 비동기적으로 명령을 실행 하는 방법을 보여 줍니다.

[!code-csharp[PowerShell02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>참고 항목

[Windows PowerShell 호스트 응용 프로그램 작성](./writing-a-windows-powershell-host-application.md)
