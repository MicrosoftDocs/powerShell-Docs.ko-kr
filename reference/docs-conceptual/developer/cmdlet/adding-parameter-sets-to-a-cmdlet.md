---
title: Cmdlet에 매개 변수 집합 추가 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: 59db96cf03ff7086e8c89fb45bc96fd805078ac8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364592"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Cmdlet에 매개 변수 집합 추가

## <a name="things-to-know-about-parameter-sets"></a>매개 변수 집합에 대해 알아야 할 사항

Windows PowerShell은 함께 작동 하는 매개 변수 그룹으로 매개 변수 집합을 정의 합니다. Cmdlet의 매개 변수를 그룹화 하 여 사용자가 지정 하는 매개 변수 그룹에 따라 해당 기능을 변경할 수 있는 단일 cmdlet을 만들 수 있습니다.

다른 기능을 정의 하는 두 개의 매개 변수 집합을 사용 하는 cmdlet의 예는 Windows PowerShell에서 제공 하는 `Get-EventLog` cmdlet입니다. 이 cmdlet은 사용자가 `List` 또는 `LogName` 매개 변수를 지정할 때 다른 정보를 반환 합니다. @No__t-0 매개 변수가 지정 된 경우 cmdlet은 지정 된 이벤트 로그의 이벤트에 대 한 정보를 반환 합니다. @No__t-0 매개 변수가 지정 된 경우 cmdlet은 로그 파일 자체에 대 한 정보를 반환 합니다 (포함 된 이벤트 정보가 아님). 이 경우 `List` 및 `LogName` 매개 변수는 두 개의 개별 매개 변수 집합을 식별 합니다.

매개 변수 집합에 대해 기억해 야 하는 두 가지 중요 한 사항은 Windows PowerShell 런타임이 특정 입력에 대해 하나의 매개 변수 집합만 사용 하 고 각 매개 변수 집합에 해당 매개 변수 집합에 대해 고유한 매개 변수를 하나 이상 포함 해야 한다는 것입니다.

마지막 지점을 설명 하기 위해이 Stop Proc cmdlet은 `ProcessName`, `ProcessId` 및 `InputObject`의 세 가지 매개 변수 집합을 사용 합니다. 이러한 각 매개 변수 집합에는 다른 매개 변수 집합에 없는 매개 변수가 하나 있습니다. 매개 변수 집합은 다른 매개 변수를 공유할 수 있지만 cmdlet은 고유 매개 변수 `ProcessName`, `ProcessId`, `InputObject`를 사용 하 여 Windows PowerShell 런타임에서 사용 해야 하는 매개 변수 집합을 식별 합니다.

## <a name="declaring-the-cmdlet-class"></a>Cmdlet 클래스 선언

Cmdlet을 만드는 첫 번째 단계는 항상 cmdlet의 이름을 지정 하 고 cmdlet을 구현 하는 .NET 클래스를 선언 하는 것입니다. 이 cmdlet의 경우 cmdlet은 시스템 프로세스를 중지 하므로 수명 주기 동사 "Stop"이 사용 됩니다. 명사 이름 "Proc"는 cmdlet이 프로세스에서 작동 하기 때문에 사용 됩니다. 아래 선언에서 cmdlet 동사와 명사 이름이 cmdlet 클래스의 이름에 반영 되어 있는지 확인 합니다.

> [!NOTE]
> 승인 된 cmdlet 동사 이름에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)을 참조 하세요.

다음 코드는이 Stop Proc cmdlet에 대 한 클래스 정의입니다.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a>Cmdlet의 매개 변수 선언

이 cmdlet은 cmdlet에 대 한 입력으로 필요한 매개 변수 3 개 (매개 변수 집합도 정의)를 정의 하 고 cmdlet이 수행 하는 작업을 관리 하는 `Force` 매개 변수와 cmdlet이 출력 개체를 보낼지 여부를 결정 하는 `PassThru` 매개 변수를 정의 합니다. 파이프라인을 통해. 기본적으로이 cmdlet은 파이프라인을 통해 개체를 전달 하지 않습니다. 이러한 마지막 두 매개 변수에 대 한 자세한 내용은 [시스템을 수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)를 참조 하세요.

### <a name="declaring-the-name-parameter"></a>Name 매개 변수 선언

사용자는이 입력 매개 변수를 사용 하 여 중지할 프로세스의 이름을 지정할 수 있습니다. [System.object](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성의 `ParameterSetName` attribute 키워드는이 매개 변수에 대해 설정 된 `ProcessName` 매개 변수를 지정 합니다.

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

또한이 매개 변수에는 "ProcessName" 별칭이 지정 됩니다.

### <a name="declaring-the-id-parameter"></a>Id 매개 변수 선언

사용자는이 입력 매개 변수를 사용 하 여 중지할 프로세스의 식별자를 지정할 수 있습니다. [System.object](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성의 `ParameterSetName` attribute 키워드는 `ProcessId` 매개 변수 집합을 지정 합니다.

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

또한이 매개 변수에는 별칭 "ProcessId"가 제공 됩니다.

### <a name="declaring-the-inputobject-parameter"></a>InputObject 매개 변수 선언

사용자는이 입력 매개 변수를 사용 하 여 중지할 프로세스에 대 한 정보를 포함 하는 입력 개체를 지정할 수 있습니다. [System.object](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성의 `ParameterSetName` attribute 키워드는이 매개 변수에 대해 설정 된 `InputObject` 매개 변수를 지정 합니다.

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

또한이 매개 변수에는 별칭이 없습니다.

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>여러 매개 변수 집합에서 매개 변수 선언

각 매개 변수 집합에 대 한 고유한 매개 변수가 있어야 하지만 매개 변수는 둘 이상의 매개 변수 집합에 속할 수 있습니다. 이러한 경우 매개 변수가 속한 각 집합에 대해 shared 매개 변수를 [system.object](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성 선언으로 지정 합니다. 매개 변수가 모든 매개 변수 집합에 있는 경우 매개 변수 특성을 한 번만 선언 하면 되며 매개 변수 집합 이름을 지정할 필요가 없습니다.

## <a name="overriding-an-input-processing-method"></a>입력 처리 메서드 재정의

모든 cmdlet은 입력 처리 메서드를 재정의 해야 합니다. 대부분의 경우 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드가 가장 일반적입니다. 이 cmdlet에서는 cmdlet이 원하는 수의 프로세스를 처리할 수 있도록 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 재정의 합니다. 사용자가 지정한 매개 변수 집합에 따라 다른 메서드를 호출 하는 Select 문이 포함 되어 있습니다.

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

Select 문에서 호출 하는 도우미 메서드는 여기서 설명 하지 않지만, 다음 섹션의 전체 코드 샘플에서 해당 구현을 볼 수 있습니다.

## <a name="code-sample"></a>코드 샘플

전체 C# 샘플 코드는 [StopProcessSample04 샘플](./stopprocesssample04-sample.md)을 참조 하세요.

## <a name="defining-object-types-and-formatting"></a>개체 형식 및 서식 정의

Windows PowerShell은 .NET 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다. 따라서 cmdlet은 자체 형식을 정의 해야 할 수도 있고, 다른 cmdlet에서 제공 하는 기존 형식을 cmdlet에서 확장 해야 할 수도 있습니다. 새 형식을 정의 하거나 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 [개체 형식 확장 및 서식 지정](/previous-versions//ms714665(v=vs.85))을 참조 하세요.

## <a name="building-the-cmdlet"></a>Cmdlet 빌드

Cmdlet을 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell에 등록 해야 합니다. Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))을 참조 하세요.

## <a name="testing-the-cmdlet"></a>Cmdlet 테스트

Windows PowerShell을 사용 하 여 cmdlet을 등록 한 경우 명령줄에서 실행 하 여 테스트 합니다. @No__t-0 및 `InputObject` 매개 변수를 사용 하 여 프로세스를 중지 하는 매개 변수 집합을 테스트 하는 방법을 보여 주는 몇 가지 테스트가 있습니다.

- Windows PowerShell이 시작 되 면 `ProcessId` 매개 변수 집합을 사용 하 여 Stop Proc cmdlet을 실행 하 여 해당 식별자를 기반으로 프로세스를 중지 합니다. 이 경우 cmdlet은 `ProcessId` 매개 변수 집합을 사용 하 여 프로세스를 중지 합니다.

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Windows PowerShell을 시작한 상태에서 `InputObject` 매개 변수 집합을 사용 하 여 `Get-Process` 명령으로 검색 된 메모장 개체의 프로세스를 중지 하는 Stop Proc cmdlet을 실행 합니다.

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>참고 항목

[시스템을 수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)

[Windows PowerShell Cmdlet을 만드는 방법](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[개체 형식 및 서식 확장](/previous-versions//ms714665(v=vs.85))

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
