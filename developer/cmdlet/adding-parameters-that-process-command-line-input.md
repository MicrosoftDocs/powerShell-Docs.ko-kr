---
title: 명령줄 입력을 처리 하는 매개 변수 추가 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: fb113086ce89e4becff9bcaf3232905fde2bf610
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068813"
---
# <a name="adding-parameters-that-process-command-line-input"></a>명령줄 입력을 처리하는 매개 변수 추가

소스 cmdlet에 대 한 입력 중 하나는 명령줄입니다. 이 항목에서는 매개 변수를 추가 하는 방법을 설명 합니다 **Get-proc** cmdlet (에 설명 되어 있는 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)) cmdlet 기반 명시적으로 로컬 컴퓨터에서 입력을 처리할 수 있도록 개체를 cmdlet에 전달 합니다. 합니다 **Get-proc** cmdlet 설명 여기 해당 이름을 기반으로 하는 프로세스를 검색 한 다음 명령 프롬프트에서 프로세스에 대 한 정보를 표시 합니다.

다음 섹션에서는이 항목은 됩니다.

- [Cmdlet 클래스 정의](#Defining-the-Cmdlet-Class)

- [매개 변수를 선언합니다.](#Declaring-Parameters)

- [매개 변수 유효성 검사를 지원합니다.](#Supporting-Parameter-Validation)

- [입력 처리 메서드를 재정의 합니다.](#Overriding-an-Input-Processing-Method)

- [코드 샘플](#Code-Sample)

- [개체 유형 정의 및 서식 지정](#Defining-Object-Types-and-Formatting)

- [Cmdlet은 빌드](#Building-the-Cmdlet)

- [테스트 Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>Cmdlet 클래스 정의

Cmdlet 만드는 첫 번째 단계에는 cmdlet 및 cmdlet을 구현 하는.NET Framework 클래스의 선언을 것입니다. "Get"입니다. 여기서 선택한 동사 이름 이므로이 cmdlet에 프로세스 정보 검색 (거의 모든 종류의 정보를 검색할 수 있는 cmdlet의 명령줄 입력을 처리할 수 있습니다.) 승인 된 cmdlet 동사에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)합니다.

에 대 한 클래스 선언을 다음은 **Get-proc** cmdlet. 이 정의 대 한 세부 정보에 제공 됩니다 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)합니다.

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>매개 변수를 선언합니다.

Cmdlet 매개 변수를 cmdlet에 대 한 입력을 제공 하도록 사용자를 수 있습니다. 다음 예에서 **Get-proc** 및 `Get-Member` 파이프라인된 cmdlet의 이름 및 `MemberType` 에 대 한 매개 변수는 `Get-Member` cmdlet. 매개 변수 속성이 인수 "."

**PS > 가져오기-proc; `get-member` -membertype 속성**

Cmdlet의 매개 변수를 선언 하려면 먼저 매개 변수를 나타내는 속성을 정의 해야 합니다. 에 **Get-proc** cmdlet을 유일한 매개 변수는 `Name`,이 경우 검색할.NET Framework 프로세스 개체의 이름을 나타내는입니다. 따라서 cmdlet 클래스 이름의 배열에 적용할 문자열 형식 속성을 정의 합니다.

에 대 한 매개 변수 선언은 다음과 같습니다 합니다 `Name` 의 매개 변수를 **Get-proc** cmdlet.

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

이 속성은 Windows PowerShell 런타임에 알리기 위해 합니다 `Name` 매개 변수를 [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성 속성 정의에 추가 됩니다. 이 특성을 선언 하기 위한 기본 구문은 `[Parameter()]`합니다.

> [!NOTE]
> 매개 변수 해야 명시적으로 공용으로 표시 되어야 합니다. 내부 공용 기본으로 표시 되지 않은 하는 Windows PowerShell 런타임에서 찾을 수 없는 매개 변수입니다.

이 cmdlet에 대 한 문자열의 배열을 사용 하 여 `Name` 매개 변수입니다. 가능한 경우 cmdlet도 정의 해야 매개 변수를 배열로 cmdlet이 둘 이상의 항목에 적용할 수 있도록이 때문에 합니다.

#### <a name="things-to-remember-about-parameter-definitions"></a>매개 변수 정의 기억해 야 할 사항

- 미리 정의 된 Windows PowerShell 매개 변수 이름과 데이터 형식은 cmdlet Windows PowerShell cmdlet을 사용 하 여 호환 되는지 확인 하려면 최대한 재사용 않아야 합니다. 예를 들어 미리 정의 된 모든 cmdlet을 사용 하는 경우 `Id` 매개 변수를 사용 하는 어떤 cmdlet에 관계 없이 의미를 이해 하는 매개 변수 이름 리소스에 사용자가 쉽게 식별할 수입니다. 기본적으로 매개 변수 이름은 CLR (공용 언어 런타임)의 변수 이름에 사용 되는 동일한 규칙을 따릅니다. 매개 변수 이름 지정에 대 한 자세한 내용은 참조 하세요. [Cmdlet 매개 변수 이름은](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb)합니다.

- Windows PowerShell은 일관 된 사용자 환경을 제공 하기 위해 몇 가지 매개 변수 이름을 예약 합니다. 이러한 매개 변수 이름을 사용 하지 않는: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`를 `ErrorAction`, `ErrorVariable`를 `OutVariable`, 및 `OutBuffer`합니다. 또한 이러한 매개 변수 이름에 대 한 다음 별칭은 예약 된: `vb`, `db`를 `ea`를 `ev`를 `ov`, 및 `ob`합니다.

- `Name` cmdlet에서 사용 하기 위해 권장 하는 간단 하 고 일반적인 매개 변수 이름이입니다. 특정 cmdlet에 고유 하며 기억 하기 어려운 복잡 한 이름 대신 다음과 같은 매개 변수 이름을 선택 하는 것이 좋습니다.

- 매개 변수는 셸이 기본적으로 대/소문자를 유지 하지만 Windows PowerShell에서 대/소문자를 구분 합니다. 인수는 대/소문자 구분 cmdlet의 작업에 따라 달라 집니다. 인수는 명령줄에서 지정 된 매개 변수에 전달 됩니다.

- 다른 매개 변수 선언의 예를 참조 하세요 [Cmdlet 매개 변수](./cmdlet-parameters.md)합니다.

## <a name="declaring-parameters-as-positional-or-named"></a>위치 또는 명명 된 매개 변수를 선언합니다.

Cmdlet을 설정 해야 각 매개 변수 중 하나로 위치 또는 명명 된 매개 변수를 합니다. 두 종류의 매개 변수 단일 인수를 부울 설정과 쉼표로 구분 된 여러 인수를 수락 합니다. 라고도 부울 매개 변수를 *전환*, 부울 설정을 처리 합니다. 스위치 매개 변수가 있는지 확인 됩니다. 권장 되는 기본값은 `false`합니다.

샘플 **Get-proc** cmdlet을 정의 합니다 `Name` 위치 0 사용 하 여 위치 매개 변수로 매개 변수입니다. 즉, 첫 번째 인수는 사용자가 명령줄에 입력이 매개 변수에 대해 자동으로 삽입 됩니다. 명명 된 매개 변수를 정의 하려는 경우 사용자를 지정 해야 하는 명령줄에서 매개 변수 이름을 둡니다는 `Position` 특성 선언에서 키워드입니다.

> [!NOTE]
> 매개 변수 이름은, 없는 경우에 귀하에 게 가장 많이 사용 하는 매개 변수를 위치 사용자는 매개 변수 이름을 입력 하지 않아도 되도록 하는 것이 좋습니다.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>필수 또는 선택적으로 매개 변수를 선언합니다.

Cmdlet는 선택적인 또는 필수 매개 변수를 각 매개 변수를 설정 해야 합니다. 예제의 **Get-proc** cmdlet을 합니다 `Name` 때문에 매개 변수가 선택 사항으로 정의 된는 `Mandatory` 특성 선언에서 키워드를 설정 하지.

## <a name="supporting-parameter-validation"></a>매개 변수 유효성 검사를 지원합니다.

샘플 **Get-proc** 입력된 유효성 검사 특성을 추가 하는 cmdlet [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute)를 `Name` 매개 변수 유효성 검사를 사용 하도록 설정 하는 입력이 모두 `null` 이거나 비어 있으면 안 됩니다. 이 특성에는 Windows PowerShell에서 제공 하는 여러 유효성 검사 특성 중 하나입니다. 다른 유효성 검사 특성의 예제를 참조 하세요 [매개 변수 입력 유효성 검사](./validating-parameter-input.md)합니다.

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>입력 처리 메서드를 재정의 합니다.

Cmdlet이 명령줄 입력을 처리 하려는 경우, 적절 한 입력 처리 메서드를 재정의 해야 합니다. 에 도입 된 기본 입력된 처리 메서드로 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)합니다.

**Get-proc** cmdlet 재정의 합니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 처리 하는 메서드를 `Name` 사용자 또는 스크립트에서 제공 하는 매개 변수 입력 합니다. 이 메서드는 제공 된 이름이 없는 경우 각 요청된 프로세스 이름 또는 프로세스에 대 한 모든 프로세스를 가져옵니다. 있음을 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)에 대 한 호출 [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 출력은 출력을 보내기 위한 메커니즘을 파이프라인에는 개체입니다. 이 호출의 두 번째 매개 변수 `enumerateCollection`를 `true` 출력 배열을 프로세스 개체를 열거 하 고 명령줄에 한 번에 하나의 프로세스를 작성 하는 Windows PowerShell 런타임에 알리기 위해.

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
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>코드 예제

전체 C# 코드 샘플을 참조 하십시오 [GetProcessSample02 샘플](./getprocesssample02-sample.md)합니다.

## <a name="defining-object-types-and-formatting"></a>개체 유형 정의 및 서식 지정

.NET Framework 개체를 사용 하 여 cmdlet 간에 정보를 전달 하는 Windows PowerShell. 따라서 cmdlet는 고유한 형식을 정의 해야 합니다. 또는 cmdlet을 다른 cmdlet에서 제공 하는 기존 형식을 확장 해야 할 수 있습니다. 새 형식 정의 또는 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 개체 형식 및 서식](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.

## <a name="building-the-cmdlet"></a>Cmdlet은 빌드

Cmdlet을 구현 하면 후 Windows PowerShell 스냅인을 사용 하 여 Windows PowerShell을 사용 하 여 등록 해야 있습니다. Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.

## <a name="testing-the-cmdlet"></a>테스트 Cmdlet

Cmdlet은 Windows PowerShell을 사용 하 여 등록 되 면 명령줄에서 실행 하 여 테스트할 수 있습니다. 샘플 cmdlet에 대 한 코드를 테스트 하려면 두 가지 방법으로 다음과 같습니다. 명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)합니다.

- Windows PowerShell 프롬프트에서 "IEXPLORE." 라고 하는 Internet Explorer 프로세스를 나열 하려면 다음 명령을 사용합니다

    ```powershell
    PS> get-proc -name iexplore
    ```

다음과 같은 출력이 표시 됩니다.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- "OUTLOOK" 및 "NOTEPAD,"는 "IEXPLORE" 라는 Internet Explorer, Outlook 및 메모장 프로세스를 나열 하려면 다음 명령을 사용 합니다. 여러 프로세스의 경우 모두 표시 됩니다.

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

다음과 같은 출력이 표시 됩니다.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a>참고 항목

[프로세스 파이프라인 입력 매개 변수 추가](./adding-parameters-that-process-pipeline-input.md)

[첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)

[확장 개체 형식 및 서식 지정](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell 참조](../windows-powershell-reference.md)

[Cmdlet 샘플](./cmdlet-samples.md)
