---
title: Cmdlet 입력 처리 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670302"
---
# <a name="cmdlet-input-processing-methods"></a>Cmdlet 입력 처리 메서드

Cmdlet은 입력 처리 작업을 수행 하려면이 항목에 설명 된 메서드 중 하나 이상을 재정의 해야 합니다.
이러한 메서드는 사전 처리, 입력된 처리 및 사후 처리 작업을 수행 하는 cmdlet를 사용 합니다.
또한 이러한 메서드를 사용 하면 cmdlet 처리를 중지 합니다.
이러한 메서드를 사용 하는 방법의 자세한 예제를 보려면 [SelectStr 자습서](selectstr-tutorial.md)합니다.

## <a name="pre-processing-operations"></a>전처리 작업

Cmdlet를 재정의 해야 합니다 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) cmdlet에서 나중에 처리할 수 있는 모든 레코드에 대 한 잘못 된 모든 전처리 작업을 추가 하는 방법입니다.
PowerShell 명령 파이프라인을 처리할 때 PowerShell이이 메서드를 호출 되 면 cmdlet에 파이프라인의 각 인스턴스에 대 한 합니다.
PowerShell 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [주기를 처리 하는 Cmdlet](/previous-versions/ms714429(v=vs.85))합니다.

다음 코드를 BeginProcessing 메서드 구현을 보여 줍니다.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>작업을 처리 하는 입력

Cmdlet을 재정의할 수는 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) cmdlet로 전송 되는 입력을 처리 하는 방법입니다.
PowerShell 명령 파이프라인을 처리할 때 PowerShell cmdlet에서 처리 되는 각 입력된 레코드에 대해이 메서드를 호출 합니다.
PowerShell 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [주기를 처리 하는 Cmdlet](/previous-versions/ms714429(v=vs.85))합니다.

다음 코드는 ProcessRecord 메서드의 구현을 보여 줍니다.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>후 처리 작업

Cmdlet를 재정의 해야 합니다 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) cmdlet에서 처리 된 모든 레코드에 유효한 모든 사후 처리 작업을 추가 하는 방법입니다.
예를 들어 cmdlet 할 개체 변수를 완료 한 후 정리를 처리 합니다.

PowerShell 명령 파이프라인을 처리할 때 PowerShell이이 메서드를 호출 되 면 cmdlet에 파이프라인의 각 인스턴스에 대 한 합니다.
그러나 것을 기억해 PowerShell 런타임이 cmdlet은 해당 입력된 처리를 통해 중간 취소 되 면 나 cmdlet의 모든 부분에서 종료 오류가 발생 한 경우 EndProcessing 메서드 호출 하지 것입니다.
이러한 이유로 cmdlet 개체를 정리 해야 하는 전체 구현 해야 [System.IDisposable](/dotnet/api/System.IDisposable) 런타임에서 모두 EndProcessing을 호출할 수 있도록 종료자를 포함 하 여 패턴 및 [ System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) 메서드 끝에 처리 합니다.
PowerShell 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [주기를 처리 하는 Cmdlet](/previous-versions/ms714429(v=vs.85))합니다.

다음 코드의 EndProcessing 메서드 구현을 보여 줍니다.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[SelectStr 자습서](selectstr-tutorial.md)

[System.IDisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
