---
title: 시스템을 수정 하는 Cmdlet 만들기 | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365762"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>시스템을 수정하는 Cmdlet 만들기

경우에 따라 cmdlet은 Windows PowerShell 런타임의 상태 뿐만 아니라 시스템의 실행 상태를 수정 해야 합니다. 이 경우 cmdlet을 사용 하 여 사용자가 변경할 수 있는지 여부를 확인할 수 있습니다.

확인을 지원 하려면 cmdlet에서 두 가지 작업을 수행 해야 합니다.

- SupportsShouldProcess 키워드를 `true`으로 설정 하 여 cmdlet이 확인을 지원함을 선언 [합니다.](/dotnet/api/System.Management.Automation.CmdletAttribute)

- 다음 예제와 같이 cmdlet을 실행 하는 동안에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 합니다.

Cmdlet은 확인을 지원 하 여 Windows PowerShell에서 제공 하는 `Confirm` 및 `WhatIf` 매개 변수를 제공 하며 cmdlet에 대 한 개발 지침을 충족 합니다. cmdlet 개발 지침에 대 한 자세한 내용은 [Cmdlet 개발 지침](./cmdlet-development-guidelines.md)을 참조 하십시오.

## <a name="changing-the-system"></a>시스템 변경

"시스템 변경" 작업은 잠재적으로 Windows PowerShell 외부의 시스템 상태를 변경 하는 모든 cmdlet을 의미 합니다. 예를 들어 프로세스 중지, 사용자 계정 사용 또는 사용 안 함 또는 데이터베이스 테이블에 행 추가는 확인 해야 하는 시스템의 모든 변경 내용입니다. 반대로 데이터를 읽거나 임시 연결을 설정 하는 작업은 시스템을 변경 하지 않으며 일반적으로 확인이 필요 하지 않습니다. 또한 `set-variable`와 같은 Windows PowerShell 런타임 내에서 효과가 제한 된 작업에는 확인이 필요 하지 않습니다. 영구적으로 변경 될 수도 있고 그렇지 않을 수도 있는 cmdlet은 `SupportsShouldProcess`를 선언 하 고 영구적으로 변경 하려는 경우에만 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 해야 합니다.

> [!NOTE]
> ShouldProcess 확인은 cmdlet에만 적용 됩니다. 명령 또는 스크립트가 .NET 메서드나 속성을 직접 호출 하거나 Windows PowerShell 외부에서 응용 프로그램을 호출 하 여 시스템의 실행 상태를 수정 하는 경우에는이 형식의 확인을 사용할 수 없습니다.

## <a name="the-stopproc-cmdlet"></a>StopProc Cmdlet

이 항목에서는 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)에 설명 된 것 처럼, Get proc cmdlet을 사용 하 여 검색 된 프로세스를 중지 하는 데 사용 되는 stop proc cmdlet에 대해 설명 합니다.

## <a name="defining-the-cmdlet"></a>Cmdlet 정의

Cmdlet을 만드는 첫 번째 단계는 항상 cmdlet의 이름을 지정 하 고 cmdlet을 구현 하는 .NET 클래스를 선언 하는 것입니다. 시스템을 변경 하는 cmdlet을 작성 하 고 있으므로 이름을 적절 하 게 지정 해야 합니다. 이 cmdlet은 시스템 프로세스를 중지 하므로 여기서 선택한 동사 이름은 [Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) 클래스에 의해 정의 되는 "Stop" 이며,이는 cmdlet이 프로세스를 중지 함을 나타내는 명사 "Proc"로 정의 됩니다. 승인 된 cmdlet 동사에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)을 참조 하세요.

다음은이 Stop Proc cmdlet에 대 한 클래스 정의입니다.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

cmdlet이 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 및 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)로 호출할 수 있도록 [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 선언에서 `SupportsShouldProcess` 특성 키워드가 `true`로 설정됨을 명심하십시오. 이 키워드를 설정 하지 않으면 사용자가 `Confirm` 및 `WhatIf` 매개 변수를 사용할 수 없습니다.

### <a name="extremely-destructive-actions"></a>매우 파괴적인 작업

활성 하드 디스크 파티션을 다시 포맷 하는 등의 일부 작업은 매우 파괴적인 작업입니다. 이러한 경우, cmdlet은 `ConfirmImpact` = `ConfirmImpact.High`를 설정 해야 합니다 .이 [특성을](/dotnet/api/System.Management.Automation.CmdletAttribute) 선언할 때. 이 설정은 사용자가 `Confirm` 매개 변수를 지정 하지 않은 경우에도 cmdlet이 강제로 사용자 확인을 요청 합니다. 그러나 cmdlet 개발자는 사용자 계정 삭제와 같이 잠재적으로 파괴적인 인 작업에 대해 과도 `ConfirmImpact`를 피해 야 합니다. `ConfirmImpact`이 **High**로 설정 되어 있으면이 고, 그렇지 [않으면입니다.](/dotnet/api/System.Management.Automation.ConfirmImpact)

마찬가지로, 이론적으로는 Windows PowerShell 외부 시스템의 실행 상태를 수정 하지만 일부 작업은 안전 하지 않을 수 있습니다. 이러한 cmdlet은 `ConfirmImpact`를 System.object로 설정할 수 있습니다 [. 낮음](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0). 이렇게 하면 사용자가 중간 영향 및 높은 영향의 작업만 확인 하도록 요청한 확인 요청이 무시 됩니다.

## <a name="defining-parameters-for-system-modification"></a>시스템 수정 매개 변수 정의

이 섹션에서는 시스템 수정 작업을 지 원하는 데 필요한 cmdlet 매개 변수를 포함 하 여 cmdlet 매개 변수를 정의 하는 방법을 설명 합니다. 매개 변수 정의에 대 한 일반 정보가 필요한 경우 [명령줄 입력을 처리 하는 매개 변수 추가](./adding-parameters-that-process-command-line-input.md) 를 참조 하세요.

Stop Proc cmdlet은 `Name`, `Force`및 `PassThru`의 세 가지 매개 변수를 정의 합니다.

`Name` 매개 변수는 프로세스 입력 개체의 `Name` 속성에 해당 합니다. 이 샘플의 `Name` 매개 변수는 필수 항목입니다. 중지 하는 명명 된 프로세스가 없으면 cmdlet이 실패 합니다.

사용자는 `Force` 매개 변수를 사용 하 여 호출을 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)로 재정의할 수 있습니다. 실제로 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 하는 모든 cmdlet에는 `Force` 매개 변수를 사용 하 여 `Force` 지정 된 경우 Cmdlet에서 system.object에 대 한 호출을 건너뛰고 작업을 [계속](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 진행 합니다. 이는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)에 대 한 호출에 영향을 주지 않습니다.

사용자는 `PassThru` 매개 변수를 사용 하 여 cmdlet이 파이프라인 (이 경우에는 프로세스가 중지 된 후)을 통해 출력 개체를 전달 하는지 여부를 지정할 수 있습니다. 이 매개 변수는 입력 개체의 속성이 아니라 cmdlet 자체에 연결 됩니다.

다음은 Stop Proc cmdlet에 대 한 매개 변수 선언입니다.

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

## <a name="overriding-an-input-processing-method"></a>입력 처리 메서드 재정의

Cmdlet은 입력 처리 메서드를 재정의 해야 합니다. 다음 코드는 샘플 ProcessRecord Cmdlet에서 사용되는 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 재정의를 보여줍니다. 요청 된 각 프로세스 이름에 대해이 메서드는 프로세스를 특수 프로세스가 아닌 것으로 확인 하 고, 프로세스를 중지 한 다음 `PassThru` 매개 변수가 지정 된 경우 출력 개체를 보냅니다.

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

## <a name="calling-the-shouldprocess-method"></a>ShouldProcess 메서드 호출

Cmdlet의 입력 처리 메서드는 시스템의 실행 상태를 변경 (예: 파일 삭제) 하기 전에 작업 실행을 확인 하기 위해 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 의 입력 처리 메서드를 호출 해야 합니다. 이를 통해 Windows PowerShell 런타임은 올바른 "WhatIf" 및 "Confirm" 동작을 셸 내에 제공할 수 있습니다.

> [!NOTE]
> 지원 되는 cmdlet 상태를 처리 하 고이를 실행 [하는 데](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 실패 하는 경우 사용자는 시스템을 예기치 않게 수정할 수 있습니다.

Windows PowerShell 런타임은 사용자에 게 표시 되는 항목을 결정 하는 데 필요한 모든 명령줄 설정이 나 기본 설정 변수를 고려 하 여 사용자에 게 변경 될 리소스의 [이름을 보냅니다.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

다음 예제에서는 샘플 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) cmdlet의 재정의에서 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하는 방법에 대해 설명 하는 예제를 보여 줍니다.

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>ShouldContinue 메서드 호출

[System.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 하면 두 번째 메시지가 사용자에 게 전송 됩니다. 이 호출은 [`true`를 호출 하 고](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) `Force` 매개 변수가 `true`로 설정 되지 않은 경우에 수행 됩니다. 그런 다음 사용자는 작업을 계속 해야 하는지 여부에 대 한 피드백을 제공할 수 있습니다. Cmdlet은 잠재적으로 위험한 시스템 수정에 대 한 추가 검사 나 사용자에 게 예-모두 및 모두 사용 안 함 옵션을 제공 하려고 [합니다.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)

다음 예제에서는 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 에 대 한 호출을 보여 줍니다 .이 cmdlet은 sample Stop-Proc cmdlet의 재정의에서 [계속](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 됩니다.

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

## <a name="stopping-input-processing"></a>입력 처리 중지

시스템 수정 작업을 수행 하는 cmdlet의 입력 처리 메서드는 입력 처리를 중지 하는 방법을 제공 해야 합니다. 이 Stop Proc cmdlet의 경우 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드에서 [system. Kill *](/dotnet/api/System.Diagnostics.Process.Kill) 메서드로 호출을 호출 하 게 됩니다 (예를 들어). `PassThru` 매개 변수는 `true`로 설정 되어 있기 때문에 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) [. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 도 호출 하 여 프로세스 개체를 파이프라인으로 보냅니다.

## <a name="code-sample"></a>코드 예제

전체 C# 샘플 코드는 [StopProcessSample01 샘플](./stopprocesssample01-sample.md)을 참조 하세요.

## <a name="defining-object-types-and-formatting"></a>개체 형식 및 서식 정의

Windows PowerShell은 .Net 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다. 따라서 cmdlet은 자체 형식을 정의 해야 할 수도 있고, 다른 cmdlet에서 제공 하는 기존 형식을 cmdlet에서 확장 해야 할 수도 있습니다. 새 형식을 정의 하거나 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 [개체 형식 확장 및 서식 지정](/previous-versions//ms714665(v=vs.85))을 참조 하세요.

## <a name="building-the-cmdlet"></a>Cmdlet 빌드

Cmdlet을 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell에 등록 해야 합니다. Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))을 참조 하세요.

## <a name="testing-the-cmdlet"></a>Cmdlet 테스트

Windows PowerShell을 사용 하 여 cmdlet을 등록 한 경우 명령줄에서 실행 하 여 테스트할 수 있습니다. 다음은 Stop Proc cmdlet을 테스트 하는 여러 테스트입니다. 명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 시작](/powershell/scripting/getting-started/getting-started-with-windows-powershell)을 참조 하세요.

- Windows PowerShell을 시작 하 고 아래와 같이 Stop Proc cmdlet을 사용 하 여 처리를 중지 합니다. Cmdlet은 `Name` 매개 변수를 필수로 지정 하기 때문에 cmdlet은 매개 변수를 쿼리 합니다.

    ```powershell
    PS> stop-proc
    ```

다음 출력이 표시됩니다.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- 이제 cmdlet을 사용 하 여 "NOTEPAD" 라는 프로세스를 중지 하겠습니다. Cmdlet은 작업을 확인 하 라는 메시지를 표시 합니다.

    ```powershell
    PS> stop-proc -Name notepad
    ```

다음 출력이 표시됩니다.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- 표시 된 대로 Stop Proc를 사용 하 여 "WINLOGON" 이라는 중요 한 프로세스를 중지 합니다. 이 작업을 수행 하면 운영 체제가 재부팅 되기 때문에이 작업을 수행 하 라는 메시지가 표시 됩니다.

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

다음 출력이 표시됩니다.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- 이제 경고를 받지 않고 WINLOGON 프로세스를 중지 해 보겠습니다. 이 명령 항목은 `Force` 매개 변수를 사용 하 여 경고를 재정의 합니다.

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

다음 출력이 표시됩니다.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>참고 항목

[명령줄 입력을 처리 하는 매개 변수 추가](./adding-parameters-that-process-command-line-input.md)

[개체 형식 및 서식 확장](/previous-versions//ms714665(v=vs.85))

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Cmdlet 샘플](./cmdlet-samples.md)