---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet에 종료되지 않는 오류 보고 추가
description: Cmdlet에 종료되지 않는 오류 보고 추가
ms.openlocfilehash: 883ff2d522266495e409fb0d45f29713baa6f047
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648673"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Cmdlet에 종료되지 않는 오류 보고 추가

Cmdlet은 [WriteError][] 메서드를 호출 하 여 종료 되지 않는 오류를 보고할 수 있으며, 계속 해 서 현재 입력 개체 또는 추가로 들어오는 파이프라인 개체에서 작동 합니다. 이 섹션에서는 입력 처리 방법에서 종료 되지 않는 오류를 보고 하는 cmdlet을 만드는 방법을 설명 합니다.

종료 오류 (및 종료 오류)의 경우 cmdlet은 오류를 식별 하는 [ErrorRecord][] 개체를 전달 해야 합니다. 각 오류 레코드는 "오류 식별자" 라는 고유한 문자열로 식별 됩니다. 식별자 외에도 각 오류의 범주는 [ErrorCategory][] 열거형에 정의 된 상수로 지정 됩니다. 사용자는 `$ErrorView` 변수를 "CategoryView"로 설정 하 여 해당 범주에 따라 오류를 볼 수 있습니다.

오류 레코드에 대 한 자세한 내용은 [Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)를 참조 하십시오.

## <a name="defining-the-cmdlet"></a>Cmdlet 정의

Cmdlet을 만드는 첫 번째 단계는 항상 cmdlet의 이름을 지정 하 고 cmdlet을 구현 하는 .NET 클래스를 선언 하는 것입니다. 이 cmdlet은 프로세스 정보를 검색 하므로 여기에서 선택한 동사 이름은 "Get"입니다. 정보를 검색할 수 있는 거의 모든 종류의 cmdlet은 명령줄 입력을 처리할 수 있습니다. 승인 된 cmdlet 동사에 대 한 자세한 내용은 [Cmdlet 동사 이름](approved-verbs-for-windows-powershell-commands.md)을 참조 하세요.

다음은이 cmdlet에 대 한 정의입니다 `Get-Proc` . 이 정의에 대 한 세부 정보는 [첫 번째 Cmdlet을 만들](creating-a-cmdlet-without-parameters.md)때 제공 됩니다.

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a>매개 변수 정의

필요한 경우 cmdlet은 입력 처리를 위한 매개 변수를 정의 해야 합니다. 이 Get-Proc cmdlet은 [Command-Line 입력을 처리 하는 매개 변수 추가](adding-parameters-that-process-command-line-input.md)에 설명 된 대로 **Name** 매개 변수를 정의 합니다.

다음은이 Get-Proc cmdlet의 **Name** 매개 변수에 대 한 매개 변수 선언입니다.

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

## <a name="overriding-input-processing-methods"></a>입력 처리 메서드 재정의

모든 cmdlet은 [system.object][] 클래스에서 제공 하는 입력 처리 메서드를 하나 이상 재정의 해야 합니다. 이러한 방법은 [첫 번째 Cmdlet 만들기](creating-a-cmdlet-without-parameters.md)에서 설명 합니다.

> [!NOTE]
> Cmdlet은 각 레코드를 가능한 한 독립적으로 처리 해야 합니다.

이 Get-Proc cmdlet은 [ProcessRecord][] 메서드를 재정의 하 여 사용자 또는 스크립트에서 제공 하는 입력에 대 한 **Name** 매개 변수를 처리 합니다. 이 메서드는 요청 된 각 프로세스 이름 또는 모든 프로세스에 대 한 프로세스를 가져옵니다. 이름이 제공 되지 않은 경우에는입니다. 이 재정의에 대 한 세부 정보는 [첫 번째 Cmdlet을 만들](creating-a-cmdlet-without-parameters.md)때 제공 됩니다.

### <a name="things-to-remember-when-reporting-errors"></a>오류를 보고할 때 기억할 사항

오류를 기록할 때 cmdlet이 전달 하는 [ErrorRecord][] 개체에는 코어의 예외가 필요 합니다. 사용할 예외를 결정할 때 .NET 지침을 따릅니다.
기본적으로 오류가 기존 예외와 의미상 동일 하면 cmdlet은 해당 예외를 사용 하거나이를 파생 해야 합니다. 그렇지 않은 경우에는 [system.object][] 클래스에서 직접 새 예외 또는 예외 계층 구조를 파생 시켜야 합니다.

ErrorRecord 클래스의 FullyQualifiedErrorId 속성을 통해 액세스 되는 오류 식별자를 만들 때 다음 사항을 염두에 두어야 합니다.

- 진단 목적으로 대상으로 지정 된 문자열을 사용 하 여 정규화 된 식별자를 검사할 때 오류가 발생 한 위치와 오류가 발생 한 위치를 확인할 수 있습니다.

- 잘 구성 된 정규화 된 오류 식별자는 다음과 같을 수 있습니다.

  `CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

앞의 예제에서 오류 식별자 (첫 번째 토큰)는 오류가 무엇 인지를 지정 하 고 나머지 부분은 오류가 발생 한 위치를 나타냅니다.

- 더 복잡 한 시나리오의 경우 오류 식별자는 검사 시 구문 분석할 수 있는 점으로 구분 된 토큰이 될 수 있습니다. 이를 통해 오류 식별자 및 오류 범주에 대 한 오류 식별자 부분을 너무 분기할 수 있습니다.

Cmdlet은 특정 오류 식별자를 다른 코드 경로에 할당 해야 합니다. 오류 식별자 할당에 대 한 다음 정보를 염두에 두십시오.

- 오류 식별자는 cmdlet 수명 주기 전체에서 일정 하 게 유지 되어야 합니다. Cmdlet 버전 간에 오류 식별자의 의미 체계를 변경 하지 마십시오.
- 보고 되는 오류에 해당 하는 오류 식별자에 tersely 텍스트를 사용 합니다. 공백 또는 문장 부호를 사용 하지 마십시오.
- Cmdlet에서 재현 가능한 오류 식별자만 생성 하도록 합니다. 예를 들어 프로세스 식별자를 포함 하는 식별자를 생성 해서는 안 됩니다. 오류 식별자는 동일한 문제가 발생 한 다른 사용자에 게 표시 되는 식별자에 해당 하는 경우에만 사용자에 게 유용 합니다.

처리 되지 않은 예외는 다음 조건에서 PowerShell에 의해 catch 되지 않습니다.

- Cmdlet이 새 스레드를 만들고 해당 스레드에서 실행 중인 코드가 처리 되지 않은 예외를 throw 하는 경우 PowerShell은 오류를 catch 하지 않고 프로세스를 종료 합니다.
- 개체의 소멸자 나 처리 되지 않은 예외를 발생 시키는 Dispose 메서드에 코드가 있으면 PowerShell에서 오류를 catch 하지 않고 프로세스를 종료 합니다.

## <a name="reporting-nonterminating-errors"></a>종료 되지 않는 오류 보고

입력 처리 방법 중 하나는 [WriteError][] 메서드를 사용 하 여 출력 스트림에 종료 되지 않는 오류를 보고할 수 있습니다.

ProcessRecord 메서드 재정의 내에서 [WriteError][] 에 대 한 호출을 보여 주는이 Get-Proc cmdlet의 코드 예제는 다음과 같습니다. [][] 메서드를 재정의 합니다. 이 경우 cmdlet에서 지정 된 프로세스 식별자에 대 한 프로세스를 찾을 수 없는 경우 호출이 수행 됩니다.

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a>종료 되지 않는 오류를 기록 하는 방법에 대해 알아야 할 사항

종료 되지 않는 오류의 경우 cmdlet은 각 특정 입력 개체에 대해 특정 오류 식별자를 생성 해야 합니다.

Cmdlet은 종료 되지 않는 오류에 의해 생성 된 PowerShell 작업을 수정 해야 하는 경우가 많습니다. `ErrorAction`및 매개 변수를 정의 하 여이 작업을 수행할 수 있습니다 `ErrorVariable` . 매개 변수를 정의 하는 경우 `ErrorAction` cmdlet은 사용자 옵션 [][]을 표시 합니다. 즉, 변수를 설정 하 여 작업에 직접 영향을 줄 수 있습니다 `$ErrorActionPreference` .

Cmdlet은 `ErrorVariable` 의 설정에 의해 영향을 받지 않는 매개 변수를 사용 하 여 종료 되지 않는 오류를 변수에 저장할 수 있습니다 `ErrorAction` . 변수 이름 앞에 더하기 기호 (+)를 추가 하 여 기존 오류 변수에 오류를 추가할 수 있습니다.

## <a name="code-sample"></a>코드 예제

전체 c # 샘플 코드는 [GetProcessSample04 샘플](./getprocesssample04-sample.md)을 참조 하세요.

## <a name="define-object-types-and-formatting"></a>개체 형식 및 서식 정의

PowerShell은 .NET 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다. 따라서 cmdlet은 자체 형식을 정의 해야 할 수도 있고, 다른 cmdlet에서 제공 하는 기존 형식을 cmdlet에서 확장 해야 할 수도 있습니다. 새 형식을 정의 하거나 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 [개체 형식 확장 및 서식 지정](/previous-versions/ms714665(v=vs.85))을 참조 하세요.

## <a name="building-the-cmdlet"></a>Cmdlet 빌드

Cmdlet을 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell에 등록 해야 합니다. Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))을 참조 하세요.

## <a name="testing-the-cmdlet"></a>Cmdlet 테스트

PowerShell을 사용 하 여 cmdlet을 등록 한 경우 명령줄에서 실행 하 여 테스트할 수 있습니다. 샘플 Get-Proc cmdlet을 테스트 하 여 오류를 보고 하는지 확인 합니다.

- PowerShell을 시작 하 고 Get-Proc cmdlet을 사용 하 여 "TEST" 라는 프로세스를 검색 합니다.

  ```powershell
  get-proc -name test
  ```

  다음 출력이 표시됩니다.

  ```
  get-proc : Operation is not valid due to the current state of the object.
  At line:1 char:9
  + get-proc  <<<< -name test
  ```

## <a name="see-also"></a>참고 항목

[파이프라인 입력을 처리하는 매개 변수 추가](./adding-parameters-that-process-pipeline-input.md)

[Command-Line 입력을 처리 하는 매개 변수 추가](./adding-parameters-that-process-command-line-input.md)

[첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)

[개체 형식 및 서식 확장](/previous-versions/ms714665(v=vs.85))

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell 참조](../windows-powershell-reference.md)

[Cmdlet 샘플](./cmdlet-samples.md)

[시스템 예외]: /dotnet/api/System.Exception
[System.object 기본 설정]: /dotnet/api/System.Management.Automation.ActionPreference
[ProcessRecord입니다.]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[WriteError입니다.]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.object.]: /dotnet/api/System.Management.Automation.Cmdlet
[ErrorCategory.]: /dotnet/api/System.Management.Automation.ErrorCategory
[ErrorRecord.]: /dotnet/api/System.Management.Automation.ErrorRecord
