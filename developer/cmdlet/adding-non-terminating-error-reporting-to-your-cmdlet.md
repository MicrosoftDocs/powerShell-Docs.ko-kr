---
title: 비종료 오류 보고를 Cmdlet에 추가 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 2f3bb481722363557c93ebbc5e6df62baeff2555
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862009"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Cmdlet에 종료되지 않는 오류 보고 추가

Cmdlet를 호출 하 여 종료 되지 않는 오류를 보고할 수는 [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드 계속 해 서 추가로 들어오는 또는 현재 입력된 개체에서 작동 하 고 개체를 파이프라인. 이 섹션에는 해당 입력된 처리 메서드를 종료 되지 않는 오류를 보고 하는 cmdlet을 만드는 방법을 설명 합니다.

종료 되지 않는 오류 (뿐만 아니라 종료 오류), cmdlet 통과 해야 합니다는 [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) 오류를 식별 하는 개체입니다. 각 오류 레코드 "오류 식별자입니다."를 호출 하는 고유 문자열에 의해 식별 됩니다. 식별자 외에도 각 오류의 범주 된 정의 된 상수는 [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) 열거형입니다. 사용자는 설정 하 여 해당 범주에 따라 오류를 볼 수는 `$ErrorView` "CategoryView" 변수입니다.

오류 레코드에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)합니다.

이 섹션의에서 항목에서는 다음과 같습니다.

- [Cmdlet을 정의합니다.](#Defining-the-Cmdlet)

- [매개 변수를 정의합니다.](#Defining-Parameters)

- [입력 처리 메서드를 재정의 합니다.](#Overriding-Input-Processing-Methods)

- [종료 되지 않는 오류를 보고합니다.](#Reporting-Nonterminating-Errors)

- [코드 샘플](#Code-Sample)

- [개체 유형 정의 및 서식 지정](#Define-Object-Types-and-Formatting)

- [Cmdlet은 빌드](#Building-the-Cmdlet)

- [테스트 Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Cmdlet을 정의합니다.

Cmdlet 만드는 첫 번째 단계는 항상 cmdlet 이름과 cmdlet을 구현 하는.NET 클래스를 선언 합니다. 이 cmdlet은 "Get" 여기에서 선택한 동사 이름 이므로 프로세스 정보를 검색 합니다. (거의 모든 종류의 정보를 검색할 수 있는 cmdlet의 명령줄 입력을 처리할 수 있습니다.) 승인 된 cmdlet 동사에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)합니다.

다음은이 Get-proc cmdlet에 대 한 정의입니다. 이 정의의 세부 정보에 제공 됩니다 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)합니다.

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a>매개 변수를 정의합니다.

필요한 경우 cmdlet에 입력을 처리 하는 것에 대 한 매개 변수를 정의 해야 합니다. Get-proc cmdlet이 정의 `Name` 에 설명 된 대로 매개 변수 [해당 프로세스 명령줄 입력 매개 변수 추가](./adding-parameters-that-process-command-line-input.md)합니다.

에 대 한 매개 변수 선언은 같습니다는 `Name` 이 Get-proc cmdlet의 매개 변수입니다.

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

## <a name="overriding-input-processing-methods"></a>입력 처리 메서드를 재정의 합니다.

모든 cmdlet 입력 처리에서 제공 하는 메서드 중 하나 이상을 재정의 해야 합니다 [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) 클래스입니다. 이러한 메서드는 나오는 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)합니다.

> [!NOTE]
> Cmdlet에 처리 해야 하지 각 레코드 최대한 독립적으로 합니다.

Get-proc cmdlet이 재정의 [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 처리 하는 메서드는 `Name` 스크립트나 사용자가 제공한 입력에 대 한 매개 변수입니다. 이 메서드는 제공 된 이름이 없는 경우 각 요청 된 프로세스 이름 또는 모든 프로세스에 대 한 프로세스를 가져옵니다. 이 재정의의 세부 정보에 제공 됩니다 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)합니다.

#### <a name="things-to-remember-when-reporting-errors"></a>오류를 보고할 때 고려해 야 할 사항

합니다 [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) cmdlet 전달의 핵심 예외가 필요한 오류를 작성 하는 경우는 개체입니다. 사용 하는 예외를 결정할 때.NET 지침을 따릅니다. 기본적으로 오류 의미상 동일한 경우 기존 예외로, cmdlet를 사용 하거나 해당 예외에서 파생 됩니다. 그렇지 않은 경우 새 예외 또는 예외 계층에서 직접 파생 되어야 합니다 [System.Exception](/dotnet/api/System.Exception) 클래스입니다.

오류 식별자 (ErrorRecord 클래스의 FullyQualifiedErrorId 속성을 통해 액세스)를 만들 때 다음 사항에 유의 해야 합니다.

- 생성 된 오류와 진단 목적으로 정규화 된 식별자를 검사 하는 경우 어떤 오류를 확인할 수 있습니다이 대 한 대상으로 하는 사용 하 여 문자열입니다.

- 잘 구성 된 정규화 된 오류 식별자는 다음과 같을 수 있습니다.

`CommandNotFoundException,Micrososft.PowerShell.Commands.GetCommanddCommand.`

이전 예제에서는 오류 식별자 (첫 번째 토큰)를 지정 오류가 무엇 인지 확인 하 고 남은 부분에서 오류가 발생 한 위치를 나타냅니다.

- 복잡 한 시나리오에 대 한 오류 식별자에는 검사에서 구문 분석할 수 있는 점으로 구분 된 토큰 수 있습니다. 이 오류 식별자와 오류 범주 뿐만 아니라 오류 식별자 부분에 너무 분기할 수 있습니다.

Cmdlet은 다른 코드 경로에 특정 오류 식별자를 할당 해야 합니다. 다음 정보를 고려 오류 식별자 할당 하십시오.

- 오류 식별자 cmdlet 수명 주기에 걸쳐 일정 하 게 유지 해야 합니다. Cmdlet 버전 간의 오류 식별자의 의미 체계를 변경 하지 마세요.

- 상품 보고 된 오류에 해당 하는 오류 식별자에 대 한 텍스트를 사용 합니다. 공백 또는 문장 부호를 사용 하지 마세요.

- 재현할 수 있는 오류 식별자만을 생성 하는 cmdlet에 있어야 합니다. 예를 들어 프로세스 식별자를 포함 하는 식별자를 생성 하지 말아야 합니다. 오류 식별자는 동일한 문제가 발생 한 다른 사용자가 표시 되는 식별자에 해당 하는 경우에 사용자에 게 유용 합니다.

처리 되지 않은 예외는 다음 조건에서 Windows PowerShell에서 잡히지:

- Cmdlet에서 처리 되지 않은 예외를 throw 하는 스레드는 실행 되는 코드를 새 스레드를 만드는 경우 Windows PowerShell은 오류를 catch 하지 않습니다 및 프로세스를 종료 합니다.

- 개체가 소멸자 또는 Dispose 메서드는 처리 되지 않은 예외를 발생 시킨 코드를 사용 하면 Windows PowerShell은 오류를 catch 하지 않습니다 및 프로세스를 종료 합니다.

## <a name="reporting-nonterminating-errors"></a>종료 되지 않는 오류를 보고합니다.

입력 처리 메서드 중 하나를 사용 하 여 출력 스트림을 종료 되지 않는 오류를 보고할 수 있습니다 합니다 [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드. 에 대 한 호출을 보여 주는이 Get-proc cmdlet의 코드 예제는 다음과 같습니다 [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 에서 재정의 내는 [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드. 이 경우 cmdlet은 지정 된 프로세스 식별자에 대 한 프로세스를 찾을 수 없는 경우에 호출이 수행 됩니다.

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

#### <a name="things-to-remember-about-writing-nonterminating-errors"></a>종료 되지 않는 오류를 작성 하는 방법에 대 한 고려해 야 할 사항

종료 되지 않는 오류를 cmdlet에는 각 특정 입력된 개체에 대 한 특정 오류 식별자를 생성 해야 합니다.

Cmdlet은 자주 종료 되지 않는 오류로 인해 생성 된 Windows PowerShell 작업을 수정 해야 합니다. 정의 하 여이 수행할 수는 `ErrorAction` 고 `ErrorVariable` 매개 변수입니다. 정의 하는 경우는 `ErrorAction` 매개 변수를 cmdlet 사용자 옵션을 제공 합니다 [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference)를 설정 하 여 작업을 직접 조작할 수 있습니다는 `$ErrorActionPreference` 변수입니다.

Cmdlet을 사용 하 여 변수 종료 되지 않는 오류를 저장할 수는 `ErrorVariable` 매개 변수를 설정 하 여 영향을 받지 않는 `ErrorAction`합니다. 오류 추가할 수 있는 기존 오류 변수는 더하기 기호 (+)를 추가 하 여 변수 이름의 맨 앞으로 합니다.

## <a name="code-sample"></a>코드 예제

전체 C# 코드 샘플을 참조 하십시오 [GetProcessSample04 샘플](./getprocesssample04-sample.md)합니다.

## <a name="define-object-types-and-formatting"></a>개체 유형 및 서식을 정의합니다

Windows PowerShell.NET 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다. 따라서 cmdlet는 고유한 형식을 정의 해야 합니다. 또는 cmdlet을 다른 cmdlet에서 제공 하는 기존 형식을 확장 해야 할 수 있습니다. 새 형식 정의 또는 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 개체 형식 및 서식](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.

## <a name="building-the-cmdlet"></a>Cmdlet은 빌드

Cmdlet를 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell을 사용 하 여 등록 해야 합니다. Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.

## <a name="testing-the-cmdlet"></a>테스트 Cmdlet

Windows PowerShell cmdlet에 등록 하는 경우 명령줄에서 실행 하 여 테스트할 수 있습니다. 오류를 보고 하는지 여부를 확인 하려면 샘플 Get-proc cmdlet를 테스트해 보겠습니다.

- Windows PowerShell을 시작 하 고 "TEST" 라는 프로세스를 검색할 Get-proc cmdlet을 사용 합니다.

    ```powershell
    PS> get-proc -name test
    ```

다음과 같은 출력이 표시 됩니다.

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a>참고 항목

[프로세스 파이프라인 입력 매개 변수 추가](./adding-parameters-that-process-pipeline-input.md)

[명령줄 입력을 처리 하는 매개 변수 추가](./adding-parameters-that-process-command-line-input.md)

[첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)

[확장 개체 형식 및 서식 지정](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell 참조](../windows-powershell-reference.md)

[Cmdlet 샘플](./cmdlet-samples.md)
