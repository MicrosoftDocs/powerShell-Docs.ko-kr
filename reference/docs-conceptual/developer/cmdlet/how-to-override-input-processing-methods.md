---
title: 입력 처리 메서드를 재정의 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364472"
---
# <a name="how-to-override-input-processing-methods"></a>입력 처리 메서드를 재정의하는 방법

다음 예에서는 cmdlet 내에서 입력 처리 메서드를 덮어쓰는 방법을 보여 줍니다. 이러한 메서드는 다음 작업을 수행 하는 데 사용 됩니다.

- Cmdlet에서 처리 하는 모든 개체에 유효한 일회성 시작 작업을 수행 하는 데에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 를 사용 합니다. Windows PowerShell 런타임은이 메서드를 한 번만 호출 합니다.

- [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드는 Cmdlet에 전달 된 개체를 처리 하는 데 사용 됩니다. Windows PowerShell 런타임은 cmdlet에 전달 된 각 개체에 대해이 메서드를 호출 합니다.

- 일회성 사후 처리 작업을 수행 하는 데에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 를 사용 합니다. Windows PowerShell 런타임은이 메서드를 한 번만 호출 합니다.

## <a name="to-override-the-beginprocessing-method"></a>BeginProcessing 메서드를 재정의 하려면

- 보호 된 재정의를 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 의 재정의 메서드로 선언 합니다.

다음 클래스는 샘플 메시지를 인쇄 합니다. 이 클래스를 사용 하려면 Cmdlet 특성에서 동사 및 명사를 변경 하 고, 새 동사 및 명사를 반영 하도록 클래스의 이름을 변경한 다음, 필요한 기능을 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 를 재정의 하는 데 필요한 기능을 추가 합니다.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a>ProcessRecord 메서드를 재정의 하려면

- [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드의 보호 된 재정의를 선언 합니다.

다음 클래스는 샘플 메시지를 인쇄 합니다. 이 클래스를 사용 하려면 Cmdlet 특성에서 동사 및 명사를 변경 하 고, 새 동사 및 명사를 반영 하도록 클래스의 이름을 변경한 다음, 필요한 기능을 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드의 재정의에 추가 합니다.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a>EndProcessing 메서드를 재정의 하려면

- 보호 된 재정의를 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 로 선언 합니다.

다음 클래스는 샘플을 인쇄 합니다. 이 클래스를 사용 하려면 Cmdlet 특성에서 동사 및 명사를 변경 하 고, 새 동사 및 명사를 반영 하도록 클래스의 이름을 변경한 다음, 필요한 기능을 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 의 재정의에 추가 합니다.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a>참고 항목

[System.object를 처리 합니다.](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.object..](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[ProcessRecord입니다.](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
