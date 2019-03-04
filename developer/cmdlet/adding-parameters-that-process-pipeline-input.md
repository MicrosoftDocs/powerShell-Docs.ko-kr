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
- parameters [PowerShell Programer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: c790d20a792bcdb4a34485e53375560e129433a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854539"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>파이프라인 입력을 처리하는 매개 변수 추가

소스 cmdlet에 대 한 입력 중 하나에 업스트림 cmdlet에서 발생 하는 파이프라인에서 개체입니다. 이 섹션에는 Get-proc cmdlet 매개 변수를 추가 하는 방법을 설명 (에서 설명한 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)) cmdlet은 파이프라인 개체를 처리할 수 있도록 합니다.

이 Get-proc cmdlet 사용을 `Name` 파이프라인 개체의 입력을 허용 하는 매개 변수는 제공 된 이름을 기반으로 하는 로컬 컴퓨터에서 프로세스 정보를 검색 하 고 다음 명령줄은 프로세스에 대 한 정보를 표시 합니다.

이 섹션의에서 항목에서는 다음과 같습니다.

- [Cmdlet 클래스 정의](#Defining-the-Cmdlet-Class)

- [파이프라인의 입력 정의](#Defining-Input-from-the-Pipeline)

- [입력 처리 메서드를 재정의 합니다.](#Overriding-an-Input-Processing-Method)

- [코드 샘플](#Code-Sample)

- [개체 유형 정의 및 서식 지정](#Defining-Object-Types-and-Formatting)

- [Cmdlet은 빌드](#Building-the-Cmdlet)

- [테스트 Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>Cmdlet 클래스 정의

Cmdlet 만드는 첫 번째 단계는 항상 cmdlet 이름과 cmdlet을 구현 하는.NET 클래스를 선언 합니다. 이 cmdlet은 "Get" 여기에서 선택한 동사 이름 이므로 프로세스 정보를 검색 합니다. (거의 모든 종류의 정보를 검색할 수 있는 cmdlet의 명령줄 입력을 처리할 수 있습니다.) 승인 된 cmdlet 동사에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)합니다.

다음은이 Get-proc cmdlet에 대 한 정의입니다. 이 정의의 세부 정보에 제공 됩니다 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)합니다.

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a>파이프라인의 입력 정의

이 섹션에는 cmdlet에 대 한 파이프라인에서 입력을 정의 하는 방법을 설명 합니다. Get-proc cmdlet이 나타내는 속성을 정의 합니다 `Name` 에 설명 된 대로 매개 변수 [해당 프로세스 명령줄 입력 매개 변수 추가](./adding-parameters-that-process-command-line-input.md)합니다. (매개 변수를 선언 하는 방법에 대 한 일반 정보에 대 한 해당 항목을 참조 하십시오.)

그러나 cmdlet을 파이프라인 입력을 처리 해야 하는 경우 해당 매개 변수 값을 입력 하는 Windows PowerShell 런타임에 의해 바인딩된 있어야 합니다. 이 작업을 수행 하려면 추가 해야 합니다 `ValueFromPipeline` 키워드 또는 추가 `ValueFromPipelineByProperty` 키워드를를 [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성 선언. 지정 된 `ValueFromPipeline` cmdlet은 전체 입력된 개체에 액세스 하는 경우에 키워드입니다. 지정 된 `ValueFromPipelineByProperty` cmdlet은 개체의 속성에만 액세스 하는 경우.

에 대 한 매개 변수 선언은 같습니다는 `Name` 파이프라인 입력 허용 하는이 Get-proc cmdlet의 매개 변수입니다.

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

이전 선언 집합을 `ValueFromPipeline` 키워드를 `true` 아니면 동일한 형식으로 강제 변환할 수는 Windows PowerShell 런타임에 바인딩될 매개 변수는 들어오는 개체 개체가 매개 변수로 동일한 형식인 경우 되도록 합니다. `ValueFromPipelineByPropertyName` 키워드를도로 설정 됩니다 `true` 는 Windows PowerShell 런타임에 들어오는 개체를 확인 하는 `Name` 속성입니다. 런타임에 바인딩합니다 들어오는 개체에 있는 경우 이러한 속성에는 `Name` 매개 변수를는 `Name` 들어오는 개체의 속성입니다.

> [!NOTE]
> 설정 합니다 `ValueFromPipeline` 매개 변수 설정을 보다 우선 키워드 특성이 `ValueFromPipelineByPropertyName` 키워드입니다.

## <a name="overriding-an-input-processing-method"></a>입력 처리 메서드를 재정의 합니다.

Cmdlet에 파이프라인 입력을 처리할 경우 적절 한 입력 처리 메서드를 재정의 해야 합니다. 에 도입 된 기본 입력된 처리 메서드로 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)합니다.

Get-proc cmdlet이 재정의 [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 처리 하는 메서드는 `Name` 사용자 또는 스크립트에서 제공 하는 매개 변수 입력 합니다. 이 메서드는 제공 된 이름이 없는 경우 각 요청 된 프로세스 이름 또는 모든 프로세스에 대 한 프로세스를 가져옵니다. 내에서 [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)에 대 한 호출 [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) 되는 출력 개체를 파이프라인으로 보내기 위한 메커니즘을 출력 합니다. 이 호출의 두 번째 매개 변수 `enumerateCollection`로 설정 된 `true` 프로세스 개체의 배열을 열거 하 고 명령줄에 한 번에 하나의 프로세스를 작성 하려면 Windows PowerShell 런타임에 알려야 합니다.

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

## <a name="code-sample"></a>코드 예제

전체 C# 코드 샘플을 참조 하십시오 [GetProcessSample03 샘플](./getprocesssample03-sample.md)합니다.

## <a name="defining-object-types-and-formatting"></a>개체 유형 정의 및 서식 지정

Windows PowerShell.Net 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다. 따라서 cmdlet는 고유한 형식을 정의 해야 합니다. 또는 cmdlet을 다른 cmdlet에서 제공 하는 기존 형식을 확장 해야 할 수 있습니다. 새 형식 정의 또는 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 개체 형식 및 서식](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.

## <a name="building-the-cmdlet"></a>Cmdlet은 빌드

Windows PowerShell을 통해 Windows PowerShell을 사용 하 여 등록 해야 하는 cmdlet을 구현 하 고 나면 스냅인. Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.

## <a name="testing-the-cmdlet"></a>테스트 Cmdlet

Windows PowerShell cmdlet에 등록 하는 경우 명령줄에서 실행 하 여 테스트 합니다. 예를 들어 샘플 cmdlet에 대 한 코드를 테스트 합니다. 명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 참조는 [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)합니다.

- Windows PowerShell 프롬프트에서 파이프라인을 통해 프로세스 이름을 검색 하려면 다음 명령을 입력 합니다.

    ```powershell
    PS> type ProcessNames | get-proc
    ```

다음과 같은 출력이 표시 됩니다.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- 한 프로세스 개체를 가져오려면 다음 줄을 입력 하는 `Name` "IEXPLORE" 라는 프로세스에서 속성입니다. 이 예제에서는 `Get-Process` "IEXPLORE" 프로세스를 검색할 업스트림 명령으로 cmdlet (Windows PowerShell에서 제공).

    ```powershell
    PS> get-process iexplore | get-proc
    ```

다음과 같은 출력이 표시 됩니다.

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

[확장 개체 형식 및 서식 지정](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell 참조](../windows-powershell-reference.md)

[Cmdlet 샘플](./cmdlet-samples.md)
