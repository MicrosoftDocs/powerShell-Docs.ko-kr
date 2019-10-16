---
title: 파이프라인 입력을 처리 하는 매개 변수 추가 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: 9ecb73a4138a5853fa5fb378874da2d81c5dbdba
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364602"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>파이프라인 입력을 처리하는 매개 변수 추가

Cmdlet에 대 한 입력의 한 원본은 업스트림 cmdlet에서 발생 하는 파이프라인의 개체입니다. 이 섹션에서는 cmdlet이 파이프라인 개체를 처리할 수 있도록 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)에 설명 된 대로 매개 변수를 Get Proc cmdlet에 추가 하는 방법에 대해 설명 합니다.

이 cmdlet은 파이프라인 개체의 입력을 허용 하 고, 제공 된 이름에 따라 로컬 컴퓨터에서 프로세스 정보를 검색 하 고, 명령줄에서 프로세스에 대 한 정보를 표시 하는 `Name` 매개 변수를 사용 합니다.

## <a name="defining-the-cmdlet-class"></a>Cmdlet 클래스 정의

Cmdlet을 만드는 첫 번째 단계는 항상 cmdlet의 이름을 지정 하 고 cmdlet을 구현 하는 .NET 클래스를 선언 하는 것입니다. 이 cmdlet은 프로세스 정보를 검색 하므로 여기에서 선택한 동사 이름은 "Get"입니다. 정보를 검색할 수 있는 거의 모든 종류의 cmdlet은 명령줄 입력을 처리할 수 있습니다. 승인 된 cmdlet 동사에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)을 참조 하세요.

다음은이 In-proc cmdlet에 대 한 정의입니다. 이 정의에 대 한 세부 정보는 [첫 번째 Cmdlet을 만들](./creating-a-cmdlet-without-parameters.md)때 제공 됩니다.

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a>파이프라인에서 입력 정의

이 섹션에서는 cmdlet에 대 한 파이프라인에서 입력을 정의 하는 방법을 설명 합니다. 이 In-proc cmdlet은 [명령줄 입력을 처리 하는 매개 변수 추가](./adding-parameters-that-process-command-line-input.md)에 설명 된 대로 `Name` 매개 변수를 나타내는 속성을 정의 합니다. 매개 변수 선언에 대 한 일반 정보는 해당 항목을 참조 하세요.

그러나 cmdlet이 파이프라인 입력을 처리 해야 하는 경우에는 Windows PowerShell 런타임에서 입력 값에 바인딩된 매개 변수를 포함 해야 합니다. 이렇게 하려면 `ValueFromPipeline` 키워드를 추가 하거나 `ValueFromPipelineByProperty` 키워드를 [system.object](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성 선언에 추가 해야 합니다. Cmdlet이 전체 입력 개체에 액세스 하는 경우 `ValueFromPipeline` 키워드를 지정 합니다. Cmdlet이 개체의 속성에만 액세스 하는 경우 `ValueFromPipelineByProperty`을 지정 합니다.

다음은 파이프라인 입력을 허용 하는이 In-proc cmdlet의 `Name` 매개 변수에 대 한 매개 변수 선언입니다.

[!code-csharp[GetProcessSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

이전 선언은 `ValueFromPipeline` 키워드를 `true`로 설정 하 여 개체가 매개 변수와 동일한 형식 이거나 동일한 형식으로 강제 변환할 수 있는 경우 Windows PowerShell 런타임이 들어오는 개체에 매개 변수를 바인딩합니다. 또한 `ValueFromPipelineByPropertyName` 키워드는 Windows PowerShell 런타임에서 들어오는 개체에서 `Name` 속성을 확인 하도록 `true`로 설정 됩니다. 들어오는 개체에 이러한 속성이 있는 경우 런타임에서는 `Name` 매개 변수를 들어오는 개체의 `Name` 속성에 바인딩합니다.

> [!NOTE]
> 매개 변수에 대 한 `ValueFromPipeline` attribute 키워드의 설정은 `ValueFromPipelineByPropertyName` 키워드의 설정 보다 우선 합니다.

## <a name="overriding-an-input-processing-method"></a>입력 처리 메서드 재정의

Cmdlet이 파이프라인 입력을 처리 하려면 적절 한 입력 처리 메서드를 재정의 해야 합니다. 기본 입력 처리 방법은 [첫 번째 Cmdlet을 만드는 데](./creating-a-cmdlet-without-parameters.md)도입 되었습니다.

이 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 재정의 하 여 사용자 또는 스크립트에서 제공 하는 @no__t 1 매개 변수 입력을 처리 합니다. 이 메서드는 요청 된 각 프로세스 이름 또는 모든 프로세스에 대 한 프로세스를 가져옵니다. 이름이 제공 되지 않은 경우에는입니다. [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)내에서 [WriteObject (system.string, system.string)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 호출은 파이프라인에 출력 개체를 전송 하는 데 필요한 출력 메커니즘을 가집니다. 이 호출의 두 번째 매개 변수 `enumerateCollection`은 `true`로 설정 하 여 프로세스 개체의 배열을 열거 하도록 Windows PowerShell 런타임에 지시 하 고 명령줄에 프로세스를 한 번에 하나씩 작성 합니다.

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument of this call tells
      // PowerShell to enumerate the array, and send one process at a
      // time to the pipeline.
      WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>코드 샘플

전체 C# 샘플 코드는 [GetProcessSample03 샘플](./getprocesssample03-sample.md)을 참조 하세요.

## <a name="defining-object-types-and-formatting"></a>개체 형식 및 서식 정의

Windows PowerShell은 .Net 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다. 따라서 cmdlet은 자체 형식을 정의 해야 할 수도 있고, 다른 cmdlet에서 제공 하는 기존 형식을 cmdlet에서 확장 해야 할 수도 있습니다. 새 형식을 정의 하거나 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 [개체 형식 확장 및 서식 지정](/previous-versions//ms714665(v=vs.85))을 참조 하세요.

## <a name="building-the-cmdlet"></a>Cmdlet 빌드

Cmdlet을 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell에 등록 해야 합니다. Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))을 참조 하세요.

## <a name="testing-the-cmdlet"></a>Cmdlet 테스트

Windows PowerShell을 사용 하 여 cmdlet을 등록 한 경우 명령줄에서 실행 하 여 테스트 합니다. 예를 들어 샘플 cmdlet에 대 한 코드를 테스트 합니다. 명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 시작](/powershell/scripting/getting-started/getting-started-with-windows-powershell)을 참조 하세요.

- Windows PowerShell 프롬프트에서 다음 명령을 입력 하 여 파이프라인을 통해 프로세스 이름을 검색 합니다.

    ```powershell
    PS> type ProcessNames | get-proc
    ```

다음 출력이 표시 됩니다.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- 다음 줄을 입력 하 여 "IEXPLORE.EXE" 라는 프로세스에서 `Name` 속성이 있는 프로세스 개체를 가져옵니다. 이 예에서는 Windows PowerShell에서 제공 하는 `Get-Process` cmdlet을 업스트림 명령으로 사용 하 여 "IEXPLORE.EXE" 프로세스를 검색 합니다.

    ```powershell
    PS> get-process iexplore | get-proc
    ```

다음 출력이 표시 됩니다.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a>참고 항목

[명령줄 입력을 처리 하는 매개 변수 추가](./adding-parameters-that-process-command-line-input.md)

[첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)

[개체 형식 및 서식 확장](/previous-versions//ms714665(v=vs.85))

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell 참조](../windows-powershell-reference.md)

[Cmdlet 샘플](./cmdlet-samples.md)
