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
ms.openlocfilehash: eff40a01b60985788ae0e21156fec7ec4e27fcf1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855919"
---
# <a name="how-to-override-input-processing-methods"></a>입력 처리 메서드를 재정의하는 방법

이러한 예제에는 입력 처리 cmdlet 내에서 메서드를 덮어쓰는 방법을 보여 줍니다. 이러한 메서드는 다음 작업을 수행 하는 데 사용 됩니다.

- 합니다 [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 메서드 cmdlet에서 처리 하는 모든 개체에 대 한 유효한 일회성 시작 작업을 수행 하는 합니다. Windows PowerShell 런타임에이 메서드를 한 번만 호출합니다.

- 합니다 [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) cmdlet에 전달 된 개체를 처리할 메서드를 사용 합니다. Windows PowerShell 런타임에 cmdlet에 전달 되는 각 개체에 대 한이 메서드를 호출 합니다.

- 합니다 [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 메서드는 일회성 사후 처리 작업을 수행 하는 데 사용 됩니다. Windows PowerShell 런타임에이 메서드를 한 번만 호출합니다.

## <a name="to-override-the-beginprocessing-method"></a>BeginProcessing 메서드를 재정의 하려면

- 보호 된 재정의 선언 합니다 [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 메서드.

다음 클래스에는 샘플 메시지를 인쇄합니다. 이 클래스를 사용 하려면 동사와 명사 Cmdlet 특성 변경, 새 동사와 명사를 반영 하도록 클래스의 이름을 변경 및 재정의에 필요한 기능을 추가 하 여 [System.Management.Automation.Cmdlet.Beginprocessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 메서드.

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

- 보호 된 재정의 선언 합니다 [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드.

다음 클래스에는 샘플 메시지를 인쇄합니다. 이 클래스를 사용 하려면 동사와 명사 Cmdlet 특성 변경, 새 동사와 명사를 반영 하도록 클래스의 이름을 변경 및 재정의에 필요한 기능을 추가 하 여 [System.Management.Automation.Cmdlet.Processrecord* ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드.

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

- 보호 된 재정의 선언 합니다 [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 메서드.

다음 클래스는 샘플을 인쇄합니다. 이 클래스를 사용 하려면 동사와 명사 Cmdlet 특성 변경, 새 동사와 명사를 반영 하도록 클래스의 이름을 변경 및 재정의에 필요한 기능을 추가 하 여 [System.Management.Automation.Cmdlet.Endprocessing* ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 메서드.

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

[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
