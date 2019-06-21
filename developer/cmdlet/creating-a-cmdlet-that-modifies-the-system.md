---
title: 시스템을 수정 하는 Cmdlet를 만들 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: 8a65915b88a04e36e773853b903528a65fe11e99
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301396"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>시스템을 수정하는 Cmdlet 만들기

경우에 따라 cmdlet 뿐 아니라 Windows PowerShell 런타임 상태 시스템의 실행 상태를 수정 해야 합니다. 이러한 경우 변경할 것인지 여부를 확인할 수 cmdlet 사용자 허용 해야 합니다.

Cmdlet는 확인을 지원 하기 위해 두 가지 작업을 수행 해야 합니다.

- 지정 하는 경우 cmdlet은 확인을 지원 하는지 선언 된 [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 특성 SupportsShouldProcess 키워드가 설정 하 여 `true`입니다.

- 호출 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) cmdlet (다음 예제와 같이) 실행 중입니다.

확인을 지원 하 여 cmdlet을 표시 합니다 `Confirm` 및 `WhatIf` Windows PowerShell에서 제공 하는 또한 cmdlet에 대 한 개발 지침을 충족 하는 매개 변수 (cmdlet 개발 지침에 대 한 자세한 내용은 참조 [ Cmdlet 개발 지침](./cmdlet-development-guidelines.md).).

## <a name="changing-the-system"></a>시스템 변경

"시스템 변경" act 잠재적으로 Windows PowerShell 외부 시스템의 상태를 변경 하는 cmdlet를 가리킵니다. 예를 들어, 사용자 계정을 사용 하지 않도록 설정 또는 확인 되어야 하는 시스템의 모든 변경 내용이 데이터베이스 테이블에 행 추가 사용 하도록 설정 하는 프로세스를 중지 합니다. 반면에 데이터를 읽거나 일시적인 연결을 설정 하는 작업 시스템 변경 하지 않으며 일반적으로 확인이 필요 하지 않습니다. 확인 효과 제한 되어 Windows PowerShell 런타임 내에서 같은 작업에 필요 하지도 않습니다 `set-variable`합니다. 영구 변경 하지 못할 수 있거나 봐야 할 Cmdlet를 선언 해야 합니다 `SupportsShouldProcess` 호출 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 영구 변경 하려는 경우에 합니다.

> [!NOTE]
> ShouldProcess 확인 cmdlet에만 적용 됩니다. 명령 또는 스크립트를 직접.NET 메서드 또는 속성을 호출 하 여 또는 Windows PowerShell의 외부 호출 응용 프로그램에서 시스템의 실행 상태를 수정, 확인이 폼은 사용할 수 없습니다.

## <a name="the-stopproc-cmdlet"></a>StopProc Cmdlet

이 항목에서는 Get-proc cmdlet을 사용 하 여 검색 되는 프로세스를 중지 하려고 하는 중지 Proc cmdlet에 설명 합니다 (에 설명 된 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)).

## <a name="defining-the-cmdlet"></a>Cmdlet을 정의합니다.

Cmdlet 만드는 첫 번째 단계는 항상 cmdlet 이름과 cmdlet을 구현 하는.NET 클래스를 선언 합니다. 시스템을 변경 하는 cmdlet를 작성 하는 때문에 적절 하 게 명명 해야 합니다. 이 cmdlet은 중지 시스템 프로세스를 "중지"를 선택한 다음 동사 이름 이므로 정의한를 [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) cmdlet은 프로세스 중지를 나타내기 위해 "Proc" 명사를 사용 하 여 클래스입니다. 승인 된 cmdlet 동사에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)합니다.

다음은이 중지 Proc cmdlet에 대 한 클래스 정의 합니다.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

주의는 [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 선언 합니다 `SupportsShouldProcess` 특성 키워드로 설정 되어 `true` 를 호출 하기 위해 cmdlet을 사용 하도록 설정 하려면 [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 하 고 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)합니다. 이 키워드 집합 없이 합니다 `Confirm` 고 `WhatIf` 매개 변수가 사용자에 게 제공 됩니다.

### <a name="extremely-destructive-actions"></a>매우 안전 하지 않은 작업

일부 작업은 다시 포맷 하는 활성 하드 디스크 파티션 등 야기할입니다. 이러한 경우 cmdlet을 설정 해야 `ConfirmImpact`  =  `ConfirmImpact.High` 선언할 때 합니다 [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 특성입니다. 이 설정을 사용자 지정 하지 하는 경우에 요청 사용자에 게 확인 하려면 cmdlet을 사용 하면를 `Confirm` 매개 변수입니다. 그러나 cmdlet 개발자 안 지나치게 `ConfirmImpact` 사용자 계정 삭제와 같은 잠재적으로 방금 삭제 된 작업에 대 한 합니다. 경우 `ConfirmImpact` 로 설정 된 [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **높은**합니다.

마찬가지로, 일부 작업을 수행할 이론상에서 수정 Windows PowerShell 외부 시스템의 실행 상태 이지만 시스템을 손상 시키는 일 수 없습니다. 이러한 cmdlet을 설정할 수 있습니다 `ConfirmImpact` 하 [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0)합니다. 이 중간 영향 및 강력한 작업을 확인 하 라는 메시지가 표시 된 확인 요청을 무시 됩니다.

## <a name="defining-parameters-for-system-modification"></a>시스템 수정에 대 한 매개 변수를 정의합니다.

이 섹션에는 지원 시스템 수정 하는 데 필요한를 포함 하 여 cmdlet 매개 변수를 정의 하는 방법을 설명 합니다. 참조 [해당 프로세스 명령줄 입력 매개 변수 추가](./adding-parameters-that-process-command-line-input.md) 매개 변수를 정의 하는 방법에 대 한 일반 정보 제공 해야 하는 경우.

세 가지 매개 변수를 정의 하는 중지 Proc cmdlet: `Name`, `Force`, 및 `PassThru`합니다.

합니다 `Name` 에 해당 하는 매개 변수는 `Name` 프로세스 입력된 개체의 속성입니다. 주의는 `Name` 명명 된 프로세스를 중지 되지 않은 경우에 cmdlet이 실패 하는 대로이 샘플의 매개 변수가 필수입니다.

합니다 `Force` 매개 변수로 사용자에 대 한 호출을 재정의할 수 있습니다 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)합니다. 실제로 cmdlet을 호출 하는 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 있어야를 `Force` 매개 변수 있도록 때 `Force` 를 지정 하면 cmdlet에 대 한 호출을 건너뛰고 [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 작업을 진행 합니다. 이 영향을 주지 않습니다에 대 한 호출에 유의 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)합니다.

`PassThru` 매개 변수는 프로세스를 중지 한 후 cmdlet을 파이프라인을 통해 출력 개체를이 예제의 경우 성공 여부를 나타낼 수 있습니다. 이 매개 변수가 cmdlet 대신 자체 속성에 입력된 개체의 연결 되어 있는지 알아야 합니다.

중지 Proc cmdlet에 대 한 매개 변수 선언은 다음과 같습니다.

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a>입력 처리 메서드를 재정의 합니다.

Cmdlet는 입력 처리 메서드를 재정의 해야 합니다. 다음 코드에서는 합니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 샘플 중지 Proc cmdlet에 사용 되는 재정의 합니다. 프로세스 이름, 요청 각각에 대해이 메서드 프로세스 되었는지 확인 하지는 특별 한 프로세스, 프로세스를 중지 하려고 한 경우 다음 출력 개체를 보냅니다는 `PassThru` 매개 변수를 지정 합니다.

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a>ShouldProcess 메서드를 호출합니다.

입력 처리 cmdlet의 메서드를 호출 해야 합니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 변경 (예를 들어, 파일 삭제) 실행 중 상태로 되기 전에 작업의 실행을 확인 하는 방법 시스템입니다. 이 사용 하면 Windows PowerShell 런타임이 셸 내에서 올바른 "WhatIf" 및 "확인" 동작을 제공 합니다.

> [!NOTE]
> Cmdlet을 지 원하는 경우 처리 해야 하 고에 실패 했습니다. 합니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 호출 사용자 시스템을 예기치 않게 수정 될 수 있습니다.

에 대 한 호출 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 명령줄 설정이 나 기본 설정 변수를 고려 하는 Windows PowerShell 런타임에 사용자에 게 변경 될 리소스의 이름을 전송 사용자에 게 표시 되어야 할 사항을 확인 합니다.

다음 예제에 대 한 호출을 보여 줍니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 재정의에서 합니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 예제의 메서드 중지 Proc cmdlet입니다.

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>ShouldContinue 메서드를 호출합니다.

에 대 한 호출을 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 메서드는 사용자에 게 보조 메시지를 보냅니다. 호출한 후에이 호출 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 반환 `true` 경우에 `Force` 매개 변수를 설정 하지 않은 `true`합니다. 사용자 작업을 계속 진행 해야 하는지 여부를에 피드백을 제공할 수 있습니다. Cmdlet 호출 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 잠재적으로 위험한 시스템 수정 또는 사용자에 게 전체 예 및 아니요-모든 옵션을 제공 하려는 경우에 대 한 추가 검사 때문입니다.

다음 예제에 대 한 호출을 보여 줍니다 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 재정의에서 합니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 예제의 메서드 중지 Proc cmdlet입니다.

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a>입력된 처리를 중지 하는 중

입력 처리 메서드 시스템을 수정 하는 cmdlet의 입력 처리를 중지 하는 방법을 제공 해야 합니다. 이 중지 Proc cmdlet의 경우 호출에서 합니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 합니다 [System.Diagnostics.Process.Kill*](/dotnet/api/System.Diagnostics.Process.Kill) 메서드. 때문에 합니다 `PassThru` 매개 변수는 설정 `true`를 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 도 호출 [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 보낼 프로세스 개체를 파이프라인입니다.

## <a name="code-sample"></a>코드 예제

전체 C# 코드 샘플을 참조 하십시오 [StopProcessSample01 샘플](./stopprocesssample01-sample.md)합니다.

## <a name="defining-object-types-and-formatting"></a>개체 유형 정의 및 서식 지정

Windows PowerShell.Net 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다. 따라서 cmdlet는 고유한 형식을 정의 해야 합니다. 또는 cmdlet을 다른 cmdlet에서 제공 하는 기존 형식을 확장 해야 할 수 있습니다. 새 형식 정의 또는 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 개체 형식 및 서식](/previous-versions//ms714665(v=vs.85))합니다.

## <a name="building-the-cmdlet"></a>Cmdlet은 빌드

Cmdlet를 구현한 후 등록 해야 Windows PowerShell을 사용 하 여 Windows PowerShell 스냅인을 통해. Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](/previous-versions//ms714644(v=vs.85))합니다.

## <a name="testing-the-cmdlet"></a>테스트 Cmdlet

Windows PowerShell cmdlet에 등록 하는 경우 명령줄에서 실행 하 여 테스트할 수 있습니다. 중지 Proc cmdlet을 테스트 하는 몇 가지 테스트는 다음과 같습니다. 명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 참조는 [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)합니다.

- Windows PowerShell을 시작 및 중지 Proc cmdlet을 사용 하 여 아래와 같이 처리를 중지 합니다. Cmdlet은 지정 하기 때문에 `Name` 필수 매개 변수, 매개 변수에 대해 cmdlet 쿼리 합니다.

    ```powershell
    PS> stop-proc
    ```

다음과 같은 출력이 표시 됩니다.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- 이제 "NOTEPAD" 라는 프로세스를 중지 하려면 cmdlet을 사용해 보겠습니다. Cmdlet를 사용 하 여 작업을 확인 하려면 묻습니다.

    ```powershell
    PS> stop-proc -Name notepad
    ```

다음과 같은 출력이 표시 됩니다.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- "WINLOGON" 라는 중요 한 프로세스를 중지 하려면 표시 된 것 처럼 중지 프로시저를 사용 합니다. 메시지가 표시 하 고 다시 부팅 하려면 운영 체제를 발생 시키기 때문에이 작업을 수행 하는 방법에 대 한 경고가 표시 됩니다.

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

다음과 같은 출력이 표시 됩니다.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- 경고를 수신 하지 않고 WINLOGON 프로세스를 중지 하려면 이제 사용해 보겠습니다. 이 명령은 항목에서 사용 하는 주의 `Force` 경고 재정의 매개 변수입니다.

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

다음과 같은 출력이 표시 됩니다.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>참고 항목

[명령줄 입력을 처리 하는 매개 변수 추가](./adding-parameters-that-process-command-line-input.md)

[확장 개체 형식 및 서식 지정](/previous-versions//ms714665(v=vs.85))

[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Cmdlet 샘플](./cmdlet-samples.md)