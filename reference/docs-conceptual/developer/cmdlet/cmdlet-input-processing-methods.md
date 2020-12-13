---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 입력 처리 메서드
description: Cmdlet 입력 처리 메서드
ms.openlocfilehash: e1a7b58517d6285250edbf16d14810388c242218
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653392"
---
# <a name="cmdlet-input-processing-methods"></a>Cmdlet 입력 처리 메서드

Cmdlet은 작업을 수행 하기 위해이 항목에서 설명 하는 하나 이상의 입력 처리 방법을 재정의 해야 합니다.
이러한 메서드를 통해 cmdlet은 전처리, 입력 처리 및 사후 처리 작업을 수행할 수 있습니다.
이러한 메서드를 사용 하 여 cmdlet 처리를 중지할 수도 있습니다.
이러한 메서드를 사용 하는 방법에 대 한 자세한 예제는 [Selectstr 자습서](selectstr-tutorial.md)를 참조 하세요.

## <a name="pre-processing-operations"></a>전처리 작업

Cmdlet은 나중에 cmdlet에 의해 처리 되는 모든 레코드에 유효한 전처리 작업을 추가 하기 위해 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 를 재정의 해야 합니다.
PowerShell에서 명령 파이프라인을 처리할 때 PowerShell은 파이프라인에서 cmdlet의 각 인스턴스에 대해이 메서드를 한 번씩 호출 합니다.
PowerShell에서 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 [Cmdlet 처리 수명 주기](/previous-versions/ms714429(v=vs.85))를 참조 하세요.

다음 코드에서는 BeginProcessing 메서드의 구현을 보여 줍니다.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>입력 처리 작업

Cmdlet은 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 재정의 하 여 cmdlet으로 전송 되는 입력을 처리할 수 있습니다.
PowerShell에서 명령 파이프라인을 처리할 때 cmdlet에 의해 처리 되는 각 입력 레코드에 대해이 메서드를 호출 합니다.
PowerShell에서 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 [Cmdlet 처리 수명 주기](/previous-versions/ms714429(v=vs.85))를 참조 하세요.

다음 코드에서는 ProcessRecord 메서드의 구현을 보여 줍니다.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>후 처리 작업

Cmdlet은 cmdlet에 의해 처리 된 모든 레코드에 유효한 후 처리 작업을 추가 하기 위해 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 를 재정의 해야 합니다.
예를 들어 cmdlet은 처리를 완료 한 후 개체 변수를 정리 해야 할 수 있습니다.

PowerShell에서 명령 파이프라인을 처리할 때 PowerShell은 파이프라인에서 cmdlet의 각 인스턴스에 대해이 메서드를 한 번씩 호출 합니다.
그러나 cmdlet이 입력 처리를 통해 중간에 취소 되거나 cmdlet의 일부에서 종료 오류가 발생 하는 경우에는 PowerShell 런타임이 EndProcessing 메서드를 호출 하지 않는다는 점을 기억해 야 합니다.
이러한 이유로 개체 정리를 필요로 하는 cmdlet은 종료자를 포함 하 [여 전체 system.string](/dotnet/api/System.IDisposable) 패턴을 구현 해야 합니다. 이렇게 하면 런타임에서 처리가 끝날 때 EndProcessing 및 [system.string 메서드를](/dotnet/api/System.IDisposable.Dispose) 모두 호출할 수 있습니다.
PowerShell에서 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 [Cmdlet 처리 수명 주기](/previous-versions/ms714429(v=vs.85))를 참조 하세요.

다음 코드에서는 EndProcessing 메서드의 구현을 보여 줍니다.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>참고 항목

[System.object를 처리 합니다.](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[ProcessRecord입니다.](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.object..](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[SelectStr 자습서](selectstr-tutorial.md)

[System.IDisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
