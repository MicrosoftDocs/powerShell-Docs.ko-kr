---
title: Cmdlet에 사용자 메시지 추가 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 1e048f6ae94ac226218c18c8f8f7590a4db26226
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370072"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Cmdlet에 사용자 메시지 추가

Cmdlet은 Windows PowerShell 런타임에 의해 사용자에 게 표시 될 수 있는 여러 종류의 메시지를 작성할 수 있습니다. 이러한 메시지에는 다음과 같은 형식이 포함 됩니다.

- 일반 사용자 정보를 포함 하는 자세한 정보 메시지입니다.

- 문제 해결 정보를 포함 하는 메시지를 디버깅 합니다.

- 예기치 않은 결과를 가질 수 있는 작업을 cmdlet에서 수행 하려고 한다는 알림이 포함 된 경고 메시지입니다.

- 시간이 오래 걸리는 작업을 수행할 때 cmdlet이 완료 한 작업량에 대 한 정보가 포함 된 진행률 보고서 메시지입니다.

Cmdlet에서 쓸 수 있는 메시지 수 나 cmdlet이 쓰는 메시지 유형에는 제한이 없습니다. 각 메시지는 cmdlet의 입력 처리 메서드 내에서 특정 호출을 수행 하 여 작성 됩니다.

## <a name="defining-the-cmdlet"></a>Cmdlet 정의

Cmdlet을 만드는 첫 번째 단계는 항상 cmdlet의 이름을 지정 하 고 cmdlet을 구현 하는 .NET 클래스를 선언 하는 것입니다. 모든 종류의 cmdlet은 입력 처리 메서드에서 사용자 알림을 쓸 수 있습니다. 따라서 일반적으로 cmdlet이 수행 하는 시스템 수정을 나타내는 동사를 사용 하 여이 cmdlet의 이름을 지정할 수 있습니다. 승인 된 cmdlet 동사에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)을 참조 하세요.

Stop Proc cmdlet은 시스템을 수정 하도록 디자인 되었습니다. 따라서 .NET 클래스에 대 한 [System.object 특성](/dotnet/api/System.Management.Automation.CmdletAttribute) 선언에는 `SupportsShouldProcess` attribute 키워드가 포함 되 고 `true`로 설정 되어야 합니다.

다음 코드는이 Stop Proc cmdlet 클래스에 대 한 정의입니다. 이 정의에 대 한 자세한 내용은 [시스템을 수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)를 참조 하세요.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>시스템 수정 매개 변수 정의

Stop Proc cmdlet은 `Name`, `Force` 및 `PassThru`의 세 가지 매개 변수를 정의 합니다. 이러한 매개 변수를 정의 하는 방법에 대 한 자세한 내용은 [시스템을 수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)를 참조 하세요.

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

Cmdlet은 입력 처리 메서드를 재정의 해야 합니다. 가장 자주 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)입니다. 이 Stop Proc cmdlet은 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 입력 처리 메서드를 재정의 합니다. 이 Stop Proc cmdlet 구현에서는 자세한 메시지, 디버그 메시지 및 경고 메시지를 기록 하는 호출이 수행 됩니다.

> [!NOTE]
> 이 메서드가 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 및 system.object를 호출 하는 방법에 대 한 자세한 내용은 [시스템을 수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)를 참조 하세요 [..](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)

## <a name="writing-a-verbose-message"></a>자세한 정보 메시지 작성

[System.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 는 특정 오류 조건과 관련이 없는 일반 사용자 수준 정보를 작성 하는 데 사용 됩니다. 그러면 시스템 관리자는이 정보를 사용 하 여 다른 명령을 계속 처리할 수 있습니다. 또한이 메서드를 사용 하 여 작성 된 모든 정보는 필요에 따라 지역화 되어야 합니다.

이 Stop Proc cmdlet의 다음 코드는 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 재정의 하는 [방법에](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 대 한 두 개의 호출을 보여 줍니다 .입니다.

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>디버그 메시지 작성

이 cmdlet은 cmdlet의 작업 문제를 해결 하는 데 사용할 수 있는 디버그 메시지를 작성 하는 데 사용 [됩니다.](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 호출은 입력 처리 메서드에서 수행 됩니다.

> [!NOTE]
> Windows PowerShell은 자세한 정보와 디버그 정보를 모두 표시 하는 `Debug` 매개 변수도 정의 합니다. Cmdlet에서이 매개 변수를 지 원하는 경우에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)를 호출 하는 것과 같은 코드에서 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 를 호출할 필요가 없습니다.

Sample Stop Proc cmdlet의 다음 두 섹션에서는 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드의 재정의에서 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 를 호출 하는 방법에 대해 설명 하는 다음 두 섹션을 보여 줍니다.

이 디버그 메시지는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하기 직전에 기록 됩니다.

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

이 디버그 메시지는 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 가 호출 되기 직전에 기록 됩니다.

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell은 추적 인프라 및 cmdlet에 대 한 모든 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 를 자동으로 라우팅합니다. 이를 통해 cmdlet 내에서 추가 개발 작업을 수행 하지 않고도 호스팅 응용 프로그램, 파일 또는 디버거로 메서드 호출을 추적할 수 있습니다. 다음 명령줄 항목은 추적 작업을 구현 합니다.

**PS > 추적 식-proc-file proc-command stop-proc notepad**

## <a name="writing-a-warning-message"></a>경고 메시지 작성

Cmdlet이 읽기 전용 파일을 덮어쓰는 등 예기치 않은 결과가 발생할 수 있는 작업을 수행 하려고 할 때 경고를 작성 하는 데 사용 [됩니다.](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)

샘플 Stop-Proc cmdlet의 다음 코드에서는 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드의 재정의에서 [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)를 호출하는 방법에 대해 설명하는 코드를 보여줍니다.

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>진행률 메시지 작성

Cmdlet 작업을 완료 하는 데 시간이 오래 걸리는 경우에는 progress를 사용 [하 여 진행률](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 메시지를 작성 합니다. [Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) 를 호출 하면 사용자에 게 렌더링 하기 위해 호스팅 응용 프로그램으로 전송 되는 [개체가 전달 되](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 고,

> [!NOTE]
> 이 Stop Proc cmdlet에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 를 호출 하는 작업이 포함 되지 않습니다.

다음 코드는 항목 복사를 시도 하는 cmdlet에 의해 작성 된 진행률 메시지의 예입니다.

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a>코드 예제

전체 C# 샘플 코드는 [StopProcessSample02 샘플](./stopprocesssample02-sample.md)을 참조 하세요.

## <a name="define-object-types-and-formatting"></a>개체 형식 및 서식 정의

Windows PowerShell은 .NET 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다. 따라서 cmdlet은 자체 형식을 정의 해야 할 수도 있고, 다른 cmdlet에서 제공 하는 기존 형식을 cmdlet에서 확장 해야 할 수도 있습니다. 새 형식을 정의 하거나 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 [개체 형식 확장 및 서식 지정](/previous-versions//ms714665(v=vs.85))을 참조 하세요.

## <a name="building-the-cmdlet"></a>Cmdlet 빌드

Cmdlet을 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell에 등록 해야 합니다. Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))을 참조 하세요.

## <a name="testing-the-cmdlet"></a>Cmdlet 테스트

Windows PowerShell을 사용 하 여 cmdlet을 등록 한 경우 명령줄에서 실행 하 여 테스트할 수 있습니다. 샘플 중지-프로시저 cmdlet을 테스트해 보겠습니다. 명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 시작](/powershell/scripting/getting-started/getting-started-with-windows-powershell)을 참조 하세요.

- 다음 명령줄 항목에서는 중지-프로세서를 사용 하 여 "NOTEPAD" 라는 프로세스를 중지 하 고 자세한 알림을 제공 하며 디버그 정보를 인쇄 합니다.

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

다음 출력이 표시 됩니다.

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a>참고 항목

[시스템을 수정 하는 Cmdlet을 만듭니다.](./creating-a-cmdlet-that-modifies-the-system.md)

[Windows PowerShell Cmdlet을 만드는 방법](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[개체 형식 및 서식 확장](/previous-versions//ms714665(v=vs.85))

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
