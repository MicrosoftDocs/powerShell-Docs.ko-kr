---
title: Cmdlet을 설정 하는 매개 변수 추가 | Microsoft Docs
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
ms.openlocfilehash: f0bff11618c18bf53b9c2a185445795a17306fa3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068840"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Cmdlet에 매개 변수 집합 추가

이 섹션에서는 추가 중지 Proc cmdlet에 매개 변수를 설정 하는 방법에 설명 합니다 (에서 설명한 [시스템을 수정 하는 Cmdlet를 만들](./creating-a-cmdlet-that-modifies-the-system.md)). 이 Programmer's이 Guide에 설명 된 다른 중지 Proc cmdlet와 마찬가지로,이 cmdlet은 하려고 Get-proc cmdlet을 사용 하 여 검색 되는 프로세스를 중지 (에서 설명한 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)).

이 섹션의에서 항목에서는 다음과 같습니다.

- [매개 변수 집합에 대해 알아야 할 내용](#Adding-Parameter-Sets-to-a-Cmdlet)

- [Cmdlet 클래스 선언](#Declaring-the-Cmdlet-Class)

- [Cmdlet의 매개 변수를 선언합니다.](#Declaring-the-Parameters-of-the-Cmdlet)

- [입력 처리 메서드를 재정의 합니다.](#Overriding-an-Input-Processing-Method)

- [코드 샘플](#Declaring-the-Parameters-of-the-Cmdlet)

- [개체 유형 정의 및 서식 지정](#Defining-Object-Types-and-Formatting)

- [Cmdlet은 빌드](#Building-the-Cmdlet)

- [테스트 Cmdlet](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a>매개 변수 집합에 대해 알아야 할 내용

Windows PowerShell은 함께 작동 하는 매개 변수는 그룹으로 설정 매개 변수를 정의 합니다. Cmdlet의 매개 변수를 그룹화 하 여 사용자가 지정 하는 매개 변수 그룹을 기반으로 해당 기능을 변경할 수 있는 단일 cmdlet를 만들 수 있습니다.

두 매개 변수 집합을 사용 하 여 다양 한 기능을 정의 하는 cmdlet의 예로 `Get-EventLog` Windows PowerShell에서 제공 하는 cmdlet입니다. 사용자 지정 하는 경우이 cmdlet은 다른 정보를 반환 합니다 `List` 또는 `LogName` 매개 변수입니다. 경우는 `LogName` 매개 변수가 지정 된, 지정 된 이벤트 로그의 이벤트에 대 한 정보를 반환 합니다. 경우는 `List` 매개 변수 지정 된 경우 cmdlet은 로그에 대 한 정보를 파일 자체가 (이벤트 정보가 아니라 포함)를 반환 합니다. 이 경우에 `List` 및 `LogName` 매개 변수 두 개의 별도 매개 변수 집합을 식별 합니다.

매개 변수 집합에 대 한 기억 하기 두 가지 중요 한 특정 입력에 대해 설정 하는 하나의 매개 변수를 사용 하는 Windows PowerShell 런타임에 각 매개 변수 집합 하나 이상의 매개 변수가 있어야 하는 해당 매개 변수 집합에 대 한 고유 있다는 것입니다.

중지 Proc cmdlet이 해당 마지막 지점을 보여 주기 위해 세 개의 매개 변수 집합을 사용 합니다. `ProcessName`, `ProcessId`, 및 `InputObject`합니다. 각 매개 변수 집합에 다른 매개 변수 집합에 없는 매개 변수가 하나 있습니다. 매개 변수 집합에는 다른 매개 변수를 공유할 수 있지만 고유한 매개 변수를 사용 하는 cmdlet `ProcessName`, `ProcessId`, 및 `InputObject` Windows PowerShell 런타임을 사용 해야 하는 매개 변수 집합을 식별 합니다.

## <a name="declaring-the-cmdlet-class"></a>Cmdlet 클래스 선언

Cmdlet 만드는 첫 번째 단계는 항상 cmdlet 이름과 cmdlet을 구현 하는.NET 클래스를 선언 합니다. 이 cmdlet에 대 한 수명 주기 동사 "Stop" cmdlet은 시스템 프로세스를 중지 하기 때문에 사용 됩니다. Cmdlet은 프로세스에서 작동 하기 때문에 "Proc" 명사 이름 사용 됩니다. 다음 선언에는 cmdlet 클래스 이름을 cmdlet 동사 / 명사 이름이 내용이 반영 되었는지 note 합니다.

> [!NOTE]
> Cmdlet은 승인 된 동사 이름에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)합니다.

다음 코드는이 중지 Proc cmdlet에 대 한 클래스 정의입니다.

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a>Cmdlet의 매개 변수를 선언합니다.

(정의 된 매개 변수 집합 이러한 매개 변수)에 있는 cmdlet에 대 한 입력으로 필요한 세 가지 매개 변수를 정의 하는이 cmdlet은 뿐만 `Force` 가 관리 하는 매개 변수 및 `PassThru` cmdlet를 보낼지 여부를 결정 하는 매개 변수는 파이프라인을 통해 개체를 출력 합니다. 기본적으로이 cmdlet은 파이프라인을 통해 개체를 전달 하지 않습니다. 이러한 마지막 두 매개 변수에 대 한 자세한 내용은 참조 하세요. [시스템을 수정 하는 Cmdlet를 만들](./creating-a-cmdlet-that-modifies-the-system.md)합니다.

### <a name="declaring-the-name-parameter"></a>Name 매개 변수를 선언합니다.

이 입력된 매개 변수를 중지할 프로세스의 이름을 지정할 수 있습니다. `ParameterSetName` 특성의 키워드를 [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성을 지정 합니다 `ProcessName` 이 매개 변수에 대 한 매개 변수를 설정 합니다.

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

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

이 매개 변수를 사용 하는 "ProcessName" 별칭 지정 된는 또한 note 합니다.

### <a name="declaring-the-id-parameter"></a>Id 매개 변수를 선언합니다.

이 입력된 매개 변수를 중지할 프로세스의 식별자를 지정할 수 있습니다. `ParameterSetName` 특성의 키워드를 [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성을 지정 합니다 `ProcessId` 매개 변수 집합입니다.

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

이 매개 변수를 사용 하는 "ProcessId" 별칭 지정 된는 또한 note 합니다.

### <a name="declaring-the-inputobject-parameter"></a>InputObject 매개 변수를 선언합니다.

이 입력된 매개 변수를 중지할 프로세스에 대 한 정보를 포함 하는 입력된 개체를 지정할 수 있습니다. `ParameterSetName` 특성의 키워드를 [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성을 지정 합니다 `InputObject` 이 매개 변수에 대 한 매개 변수를 설정 합니다.

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

이 매개 변수 없는 별칭에도 note 합니다.

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>여러 매개 변수 집합에 대 한 매개 변수를 선언합니다.

각 매개 변수 집합에 대 한 고유한 매개 변수 여야 합니다 하지만 매개 변수 둘 이상의 매개 변수 집합에 속할 수 있습니다. 이러한 경우에 공유 매개 변수를 제공 된 [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성 선언을 각각 설정 하 고 있는 매개 변수에 속하는. 매개 변수는 모든 매개 변수 집합에만 매개 변수 특성을 한 번만 선언 해야를 매개 변수 이름 집합을 지정할 필요가 없습니다.

## <a name="overriding-an-input-processing-method"></a>입력 처리 메서드를 재정의 합니다.

가장 일반적인, 모든 cmdlet을 입력 처리 메서드를 재정의 해야 합니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드. 이 cmdlet에는 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) cmdlet 개수에 관계 없이 프로세스를 처리할 수 있도록 메서드를 재정의 합니다. 사용자는 매개 변수 집합에 따라 다양 한 메서드 호출에 지정 하는 Select 문을 포함 합니다.

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

Select 문에서 호출 하는 도우미 메서드는 여기에서 설명 되지 않지만 구현과 다음 섹션에서 전체 코드 샘플에서을 볼 수 있습니다.

## <a name="code-sample"></a>코드 예제

전체 C# 코드 샘플을 참조 하십시오 [StopProcessSample04 샘플](./stopprocesssample04-sample.md)합니다.

## <a name="defining-object-types-and-formatting"></a>개체 유형 정의 및 서식 지정

Windows PowerShell.NET 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다. 따라서 cmdlet는 고유한 형식을 정의 해야 합니다. 또는 cmdlet을 다른 cmdlet에서 제공 하는 기존 형식을 확장 해야 할 수 있습니다. 새 형식 정의 또는 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 개체 형식 및 서식](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.

## <a name="building-the-cmdlet"></a>Cmdlet은 빌드

Cmdlet를 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell을 사용 하 여 등록 해야 합니다. Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.

## <a name="testing-the-cmdlet"></a>테스트 Cmdlet

Windows PowerShell cmdlet에 등록 하는 경우 명령줄에서 실행 하 여 테스트 합니다. 다음은 몇 가지 테스트 보여 주는 하는 방법을 `ProcessId` 및 `InputObject` 프로세스를 중지 하려면 해당 매개 변수 집합을 테스트 하려면 매개 변수를 사용할 수 있습니다.

- Windows powershell 시작을 사용 하 여 중지 Proc cmdlet을 실행 하는 `ProcessId` 해당 식별자를 기반으로 하는 프로세스를 중지 하려면 매개 변수를 설정 합니다. Cmdlet을 사용 하 여이 경우에 `ProcessId` 프로세스를 중지 하려면 매개 변수를 설정 합니다.

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- 시작 하는 Windows powershell을 사용 하 여 중지 Proc cmdlet을 실행 합니다 `InputObject` 메모장에서 검색 한 개체에 프로세스를 중지 하려면 매개 변수 설정를 `Get-Process` 명령입니다.

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>참고 항목

[시스템을 수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)

[Windows PowerShell Cmdlet을 만드는 방법](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[확장 개체 형식 및 서식 지정](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)
