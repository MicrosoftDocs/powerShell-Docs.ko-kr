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
ms.openlocfilehash: dfaaa19fd3d4eb65a3fd335fb984a69874688f27
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861489"
---
# <a name="cmdlet-input-processing-methods"></a>Cmdlet 입력 처리 메서드

Cmdlet은 입력 처리 작업을 수행 하려면이 항목에 설명 된 메서드 중 하나 이상을 재정의 해야 합니다. 이러한 메서드는 전처리 작업, 입력 처리 작업 및 후 처리 작업을 수행 하는 cmdlet를 사용 합니다. 또한 이러한 메서드를 사용 하면 cmdlet 처리를 중지 합니다.

## <a name="pre-processing-tasks"></a>전처리 작업

Cmdlet를 재정의 해야 합니다 [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) cmdlet에서 나중에 처리할 수 있는 모든 레코드에 대 한 잘못 된 모든 전처리 작업을 추가 하는 방법입니다. Windows PowerShell 명령 파이프라인을 처리할 때 Windows PowerShell이이 메서드를 호출 되 면 cmdlet에 파이프라인의 각 인스턴스에 대 한 합니다. Windows PowerShell 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [주기를 처리 하는 Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)합니다.

다음 코드의 구현을 보여 줍니다는 [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) 메서드.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

사용 하는 방법의 자세한 예제는 [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) 메서드를 참조 하세요 [SelectStr 자습서](./selectstr-tutorial.md)합니다. 이 자습서에서는 합니다 **선택 Str** cmdlet을 사용 합니다 [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) 검색 입력 레코드를 처리 하는 데 사용 되는 정규식을 생성 하는 방법입니다.

## <a name="input-processing-tasks"></a>처리 태스크를 입력 합니다.

Cmdlet을 재정의할 수는 [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) cmdlet로 전송 되는 입력을 처리 하는 방법입니다. Windows PowerShell 명령 파이프라인을 처리할 때 Windows PowerShell cmdlet에서 처리 되는 각 입력된 레코드에 대해이 메서드를 호출 합니다. Windows PowerShell 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [주기를 처리 하는 Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)합니다.
Cmdlet을 재정의할 수는 [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) cmdlet로 전송 되는 입력을 처리 하는 방법입니다. Windows PowerShell 명령 파이프라인을 처리할 때 Windows PowerShell cmdlet에서 처리 되는 각 입력된 레코드에 대해이 메서드를 호출 합니다. Windows PowerShell 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [주기를 처리 하는 Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)합니다.

다음 코드의 구현을 보여 줍니다는 [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) 메서드.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

사용 하는 방법의 자세한 예제는 [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) 메서드를 참조 하세요 [SelectStr 자습서](./selectstr-tutorial.md)합니다.

## <a name="post-processing-tasks"></a>사후 처리 작업

Cmdlet를 재정의 해야 합니다 [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) cmdlet에서 처리 된 모든 레코드에 유효한 모든 사후 처리 작업을 추가 하는 방법입니다. 예를 들어 cmdlet 할 개체 변수를 완료 한 후 정리를 처리 합니다.

Windows PowerShell 명령 파이프라인을 처리할 때 Windows PowerShell이이 메서드를 호출 되 면 cmdlet에 파이프라인의 각 인스턴스에 대 한 합니다. 그러나는 것이 Windows PowerShell 런타임을 호출 하지 것입니다 고려해 야 합니다 [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) 메서드 cmdlet은 해당 입력된 처리를 통해 중간 취소 되거나 종료 하는 경우 cmdlet의 모든 부분에서 오류가 발생 합니다. 이러한 이유로 cmdlet 개체를 정리 해야 하는 전체 구현 해야 [System.Idisposable](/dotnet/api/System.IDisposable) 둘 다 런타임에 호출할 수 있도록 종료자를 포함 하 여 패턴을 [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) 하 고 [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) 메서드 끝에 처리 합니다. Windows PowerShell 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [주기를 처리 하는 Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)합니다.
Windows PowerShell 명령 파이프라인을 처리할 때 Windows PowerShell이이 메서드를 호출 되 면 cmdlet에 파이프라인의 각 인스턴스에 대 한 합니다. 그러나는 것이 Windows PowerShell 런타임을 호출 하지 것입니다 고려해 야 합니다 [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) 메서드 cmdlet은 해당 입력된 처리를 통해 중간 취소 되거나 종료 하는 경우 cmdlet의 모든 부분에서 오류가 발생 합니다. 이러한 이유로 cmdlet 개체를 정리 해야 하는 전체 구현 해야 [System.Idisposable](/dotnet/api/System.IDisposable) 둘 다 런타임에 호출할 수 있도록 종료자를 포함 하 여 패턴을 [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) 하 고 [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) 메서드 끝에 처리 합니다. Windows PowerShell 명령 파이프라인을 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [주기를 처리 하는 Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)합니다.

다음 코드의 구현을 보여 줍니다는 [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) 메서드.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

사용 하는 방법의 자세한 예제는 [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) 메서드를 참조 하세요 [SelectStr 자습서](./selectstr-tutorial.md)합니다.

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[System.Idisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
