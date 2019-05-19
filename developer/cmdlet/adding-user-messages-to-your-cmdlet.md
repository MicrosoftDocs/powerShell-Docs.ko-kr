---
title: 사용자 메시지를 Cmdlet에 추가 | Microsoft Docs
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
ms.openlocfilehash: 138c6a43937e72fffaa2a09243e500e9822e6111
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854930"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Cmdlet에 사용자 메시지 추가

Cmdlet는 여러 가지 Windows PowerShell 런타임에 의해 사용자에 게 표시 될 수 있는 메시지를 작성할 수 있습니다. 이러한 메시지 유형은 다음과 같습니다.

- 일반 사용자 정보를 포함 하는 자세한 정보 메시지입니다.

- 문제 해결 정보를 포함 하는 메시지를 디버그 합니다.

- 경고 메시지에 대 한 작업을 수행할 수 있는 cmdlet에는 알림을 포함 하는 예기치 않은 결과입니다.

- 메시지 크기에 대 한 정보를 포함 하는 cmdlet은 작업 진행률 보고서는 오래 걸리는 작업을 수행 하는 경우 완료 되었습니다.

Cmdlet에 쓸 수 있는 메시지 수 또는 cmdlet에 기록 하는 메시지의 형식에는 한도가 있습니다. 각 메시지 처리 방법 cmdlet의 입력 내에서 특정를 호출 하 여 기록 됩니다.

## <a name="defining-the-cmdlet"></a>Cmdlet을 정의합니다.

Cmdlet 만드는 첫 번째 단계는 항상 cmdlet 이름과 cmdlet을 구현 하는.NET 클래스를 선언 합니다. Cmdlet의 모든 정렬 메서드를 처리 하는 입력 으로부터의 사용자 알림을 작성할 수 있습니다. 따라서 일반적으로 cmdlet은 시스템 수정 사항이 무엇 인지를 나타내는 모든 동사를 사용 하 여이 cmdlet를 명명할 수 있습니다. 승인 된 cmdlet 동사에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)합니다.

시스템을 수정 하려면 중지 Proc cmdlet은 따라서 합니다 [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .NET 클래스에 대 한 선언을 포함 해야 합니다는 `SupportsShouldProcess` 키워드를 특성 및 설정할 `true`.

다음 코드는이 중지 Proc cmdlet 클래스에 대 한 정의입니다. 이 정의 대 한 자세한 내용은 참조 하십시오 [시스템을 수정 하는 Cmdlet를 만들](./creating-a-cmdlet-that-modifies-the-system.md)합니다.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>시스템 수정에 대 한 매개 변수를 정의합니다.

세 가지 매개 변수를 정의 하는 중지 Proc cmdlet: `Name`, `Force`, 및 `PassThru`합니다. 이러한 매개 변수를 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [시스템을 수정 하는 Cmdlet를 만들](./creating-a-cmdlet-that-modifies-the-system.md)합니다.

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

Cmdlet는 입력 처리 메서드를 재정의 해야, 가장 자주 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)합니다. 중지 Proc cmdlet이 재정의 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 처리 방법을 입력 합니다. 중지 Proc cmdlet의이 구현에서 자세한 정보 메시지, 디버그 메시지 및 경고 메시지를 쓸 호출은 수행 됩니다.

> [!NOTE]
> 이 메서드를 호출 하는 방법에 대 한 자세한 내용은 합니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 하 고 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 메서드 참조 [시스템을 수정 하는 Cmdlet를 만들](./creating-a-cmdlet-that-modifies-the-system.md)합니다.

## <a name="writing-a-verbose-message"></a>자세한 정보 메시지를 작성합니다.

합니다 [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 메서드는 특정 오류 조건에 관련 된 일반 사용자 수준 정보를 쓰는 데 있습니다. 다른 명령 처리를 계속 하려면 시스템 관리자가 해당 정보를 사용할 수 있습니다. 또한이 메서드를 사용 하 여 기록 된 정보는 필요에 따라 지역화 해야 합니다.

이 중지 Proc cmdlet에서 다음 코드를 두 번 호출을 보여 줍니다 합니다 [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 재정의 메서드에서 [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드.

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>디버그 메시지를 작성합니다.

[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 메서드 cmdlet의 작업 문제 해결에 사용할 수 있는 디버그 메시지 쓰기를 사용 합니다. 메서드를 처리 하는 입력에서 호출 됩니다.

> [!NOTE]
> Windows PowerShell도 정의 `Debug` 모두 자세한 정보를 제공 하 고 디버그 정보를 제공 하는 매개 변수입니다. Cmdlet이 매개이 변수를 지 원하는 경우 되지 않아도 호출 [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 를 호출 하는 동일한 코드 [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .

코드 샘플 중지 Proc cmdlet에서 다음 두 섹션에 대 한 호출을 표시 합니다 [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 재정의 메서드에서 [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드.

이 디버그 메시지는 바로 앞에 쓰여집니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 라고 합니다.

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

이 디버그 메시지는 바로 앞에 쓰여집니다 [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 라고 합니다.

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell에 모든 항목을 자동으로 라우팅합니다 [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 추적 인프라 및 cmdlet을 호출 합니다. 이 cmdlet에서 추가 개발 작업을 수행 하지 않아도 호스팅 응용 프로그램, 파일 또는 디버거를 추적할 메서드 호출을 허용 합니다. 다음 명령줄 항목 추적 작업을 구현합니다.

**PS > 식을 추적 중지 proc-proc.log 파일-명령 중지 proc 메모장**

## <a name="writing-a-warning-message"></a>경고 메시지를 작성합니다.

합니다 [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) 메서드 cmdlet 예기치 않은 결과 예를 들어, 읽기 전용 파일을 덮어쓸 수 있는 작업을 수행 하려고 할 때 경고를 작성 하는 합니다.

샘플 프로시저 중지 cmdlet에서 다음 코드에 대 한 호출을 보여 줍니다 합니다 [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) 재정의 메서드에서 [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드.

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>진행률 메시지를 작성합니다.

합니다 [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) cmdlet 작업 소요 시간을 들여야 하는 경우 진행률 메시지를 쓰는 데 사용 됩니다. 에 대 한 호출 [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 전달 된 [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) 사용자에 게 렌더링에 대 한 호스팅 응용 프로그램에 전송 되는 개체입니다.

> [!NOTE]
> 이 프로시저 중지 cmdlet에 대 한 호출을 다루지 않습니다 합니다 [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 메서드.

다음 코드는 항목을 복사 하려고 하는 cmdlet에 의해 기록 되는 진행률 메시지의 예입니다.

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

전체 C# 코드 샘플을 참조 하십시오 [StopProcessSample02 샘플](./stopprocesssample02-sample.md)합니다.

## <a name="define-object-types-and-formatting"></a>개체 유형 및 서식을 정의합니다

Windows PowerShell.NET 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다. 따라서 cmdlet는 고유한 형식을 정의 해야 합니다. 또는 cmdlet을 다른 cmdlet에서 제공 하는 기존 형식을 확장 해야 할 수 있습니다. 새 형식 정의 또는 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 개체 형식 및 서식](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.

## <a name="building-the-cmdlet"></a>Cmdlet은 빌드

Cmdlet를 구현한 후 등록 해야 Windows PowerShell을 사용 하 여 Windows PowerShell 스냅인을 통해. Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.

## <a name="testing-the-cmdlet"></a>테스트 Cmdlet

Windows PowerShell cmdlet에 등록 하는 경우 명령줄에서 실행 하 여 테스트할 수 있습니다. 샘플 프로시저 중지 cmdlet를 테스트해 보겠습니다. 명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 참조는 [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)합니다.

- 다음 명령줄 항목 "NOTEPAD" 라는 프로세스를 중지, 자세한 알림을 제공 하 고 디버그 정보를 인쇄 하려면 중지 프로시저를 사용 합니다.

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

다음과 같은 출력이 표시 됩니다.

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

[시스템을 수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)

[Windows PowerShell Cmdlet을 만드는 방법](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[확장 개체 형식 및 서식 지정](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)
