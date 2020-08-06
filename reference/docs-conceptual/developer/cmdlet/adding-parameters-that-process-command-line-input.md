---
title: 명령줄 입력을 처리 하는 매개 변수 추가 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.openlocfilehash: 6ccc873d9c6b93546b3dae8c0d2e406763fdfb8a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784574"
---
# <a name="adding-parameters-that-process-command-line-input"></a>명령줄 입력을 처리하는 매개 변수 추가

Cmdlet에 대 한 입력의 한 소스는 명령줄입니다. 이 항목에서는 cmdlet에 매개 변수를 추가 하는 방법에 대해 설명 합니다 .이 cmdlet은 cmdlet에 `Get-Proc` 전달 된 명시적 개체를 기반으로 하 여 로컬 컴퓨터의 입력을 처리할 수 있도록 cmdlet에 매개 변수를 추가 하는 [방법에 대해](./creating-a-cmdlet-without-parameters.md)설명 합니다. `Get-Proc`여기에 설명 된 cmdlet은 이름에 따라 프로세스를 검색 한 다음 명령 프롬프트에서 프로세스에 대 한 정보를 표시 합니다.

## <a name="defining-the-cmdlet-class"></a>Cmdlet 클래스 정의

Cmdlet 생성의 첫 번째 단계는 cmdlet 이름 및 cmdlet을 구현 하는 .NET Framework 클래스의 선언입니다. 이 cmdlet은 프로세스 정보를 검색 하므로 여기서 선택한 동사 이름은 "Get"입니다. 정보를 검색할 수 있는 거의 모든 종류의 cmdlet은 명령줄 입력을 처리할 수 있습니다. 승인 된 cmdlet 동사에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)을 참조 하세요.

다음은 cmdlet에 대 한 클래스 선언 `Get-Proc` 입니다. 이 정의에 대 한 세부 정보는 [첫 번째 Cmdlet을 만들](./creating-a-cmdlet-without-parameters.md)때 제공 됩니다.

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>매개 변수 선언

Cmdlet 매개 변수를 사용 하면 사용자가 cmdlet에 입력을 제공할 수 있습니다. 다음 예에서 `Get-Proc` 및는 `Get-Member` 파이프라인 cmdlet의 이름이 고 `MemberType` 는 cmdlet에 대 한 매개 변수입니다 `Get-Member` . 매개 변수의 인수는 "property"입니다.

**PS> get-proc; `get-member`-membertype 속성**

Cmdlet에 대 한 매개 변수를 선언 하려면 먼저 매개 변수를 나타내는 속성을 정의 해야 합니다. Cmdlet에서 `Get-Proc` 유일한 매개 변수는입니다 `Name` .이 경우는 검색할 .NET Framework 프로세스 개체의 이름을 나타냅니다. 따라서 cmdlet 클래스는 이름 배열을 허용 하는 문자열 형식의 속성을 정의 합니다.

다음은 cmdlet의 매개 변수에 대 한 매개 변수 선언 `Name` `Get-Proc` 입니다.

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

Windows PowerShell 런타임에이 속성이 `Name` 매개 변수 임을 알리려면, 속성 정의에 [system.object](/dotnet/api/System.Management.Automation.ParameterAttribute) 를 추가 합니다. 이 특성을 선언 하는 기본 구문은 `[Parameter()]` 입니다.

> [!NOTE]
> 매개 변수는 명시적으로 public으로 표시 되어야 합니다. 공용으로 표시 되지 않는 매개 변수는 Windows PowerShell 런타임에서 찾을 수 없습니다.

이 cmdlet은 매개 변수에 대 한 문자열 배열을 사용 `Name` 합니다. 가능 하면 cmdlet은 매개 변수를 배열로도 정의 해야 합니다. 이렇게 하면 cmdlet이 둘 이상의 항목을 허용할 수 있습니다.

#### <a name="things-to-remember-about-parameter-definitions"></a>매개 변수 정의에 대해 기억할 사항

- 미리 정의 된 Windows PowerShell 매개 변수 이름 및 데이터 형식은 cmdlet이 Windows PowerShell cmdlet과 호환 되도록 가능한 한 많이 다시 사용 해야 합니다. 예를 들어 모든 cmdlet이 미리 정의 된 `Id` 매개 변수 이름을 사용 하 여 리소스를 식별 하는 경우 사용자는 사용 중인 cmdlet에 관계 없이 매개 변수의 의미를 쉽게 이해할 수 있습니다. 기본적으로 매개 변수 이름은 CLR (공용 언어 런타임)의 변수 이름에 사용 되는 것과 동일한 규칙을 따릅니다. 매개 변수 명명에 대 한 자세한 내용은 [Cmdlet 매개 변수 이름](/previous-versions/ms714468(v=vs.85))을 참조 하세요.

- Windows PowerShell은 일관 된 사용자 환경을 제공 하기 위해 몇 가지 매개 변수 이름을 예약 합니다. ,,,,,,, `WhatIf` `Confirm` `Verbose` `Debug` `Warn` `ErrorAction` `ErrorVariable` `OutVariable` 및 `OutBuffer` 매개 변수 이름을 사용 하지 마십시오. 또한 이러한 매개 변수 이름에 대 한 다음 별칭은 예약 되어 있습니다.,, `vb` `db` ,, `ea` `ev` `ov` 및 `ob`

- `Name`는 단순 하 고 일반적인 매개 변수 이름으로, cmdlet에서 사용 하기 위해 권장 됩니다. 특정 cmdlet에 고유 하 고 기억할 수 없는 복잡 한 이름과 같은 매개 변수 이름을 선택 하는 것이 좋습니다.

- 매개 변수는 Windows PowerShell에서 대/소문자를 구분 하지 않지만 기본적으로 셸에서는 대/소문자를 유지 합니다. 인수에 대 한 대/소문자 구분은 cmdlet의 작업에 따라 달라 집니다. 인수는 명령줄에서 지정 된 매개 변수로 전달 됩니다.

- 다른 매개 변수 선언의 예는 [Cmdlet 매개 변수](./cmdlet-parameters.md)를 참조 하세요.

## <a name="declaring-parameters-as-positional-or-named"></a>매개 변수를 위치 또는 이름으로 선언

Cmdlet은 각 매개 변수를 위치 또는 명명 된 매개 변수로 설정 해야 합니다. 두 종류의 매개 변수 모두 단일 인수, 쉼표로 구분 된 여러 인수 및 부울 설정을 허용 합니다. 부울 매개 변수 ( *스위치*라고도 함)는 부울 설정만 처리 합니다. 스위치는 매개 변수가 있는지 확인 하는 데 사용 됩니다. 권장 되는 기본값은 `false` 입니다.

샘플 `Get-Proc` cmdlet은 `Name` 매개 변수를 위치가 인 위치 매개 변수로 정의 합니다.
0. 즉, 사용자가 명령줄에 입력 하는 첫 번째 인수가이 매개 변수에 대해 자동으로 삽입 됩니다. 사용자가 명령줄에서 매개 변수 이름을 지정 해야 하는 명명 된 매개 변수를 정의 하려면 `Position` 키워드를 특성 선언 밖으로 그대로 둡니다.

> [!NOTE]
> 매개 변수 이름을 지정 하지 않는 한 사용자가 매개 변수 이름을 입력할 필요가 없도록 가장 많이 사용 하는 매개 변수 위치를 만드는 것이 좋습니다.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>매개 변수를 필수 또는 선택 사항으로 선언

Cmdlet은 각 매개 변수를 선택적 또는 필수 매개 변수로 설정 해야 합니다. 샘플 cmdlet에서는 `Get-Proc` `Name` `Mandatory` 특성이 특성 선언에 설정 되어 있지 않으므로 매개 변수가 선택 사항으로 정의 됩니다.

## <a name="supporting-parameter-validation"></a>매개 변수 유효성 검사 지원

이 샘플 `Get-Proc` cmdlet은 입력 유효성 검사 특성 [Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute)을 매개 변수에 추가 하 여 입력이 아니고 비어 있지도 `Name` 않은 유효성 검사를 사용 하도록 설정 합니다. `null` 이 특성은 Windows PowerShell에서 제공 하는 여러 유효성 검사 특성 중 하나입니다. 다른 유효성 검사 특성의 예제는 [매개 변수 입력 유효성 검사](./validating-parameter-input.md)를 참조 하세요.

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>입력 처리 메서드 재정의

Cmdlet이 명령줄 입력을 처리 하려면 적절 한 입력 처리 메서드를 재정의 해야 합니다. 기본 입력 처리 방법은 [첫 번째 Cmdlet을 만드는 데](./creating-a-cmdlet-without-parameters.md)도입 되었습니다.

`Get-Proc`Cmdlet은 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 재정의 하 여 `Name` 사용자 또는 스크립트에서 제공 하는 매개 변수 입력을 처리 합니다. 이 메서드는 요청 된 각 프로세스 이름에 대 한 프로세스를 가져오거나, 이름이 제공 되지 않은 경우에는 모든 프로세스에 대 한 프로세스를 가져옵니다. [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)에서 [WriteObject% 28System% 2csystem %29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 을 (를) 호출 하면 출력 개체를 파이프라인으로 전송 하는 데 사용할 수 있는 출력 메커니즘이 표시 됩니다. 이 호출의 두 번째 매개 변수는 `enumerateCollection` `true` 프로세스 개체의 출력 배열을 열거 하 고 명령줄에 프로세스를 한 번에 하나씩 쓰도록 Windows PowerShell 런타임에 알리기 위해로 설정 됩니다.

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

전체 c # 샘플 코드는 [GetProcessSample02 샘플](./getprocesssample02-sample.md)을 참조 하세요.

## <a name="defining-object-types-and-formatting"></a>개체 형식 및 서식 정의

Windows PowerShell은 .NET Framework 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다. 따라서 cmdlet은 자체 형식을 정의 해야 할 수도 있고, 다른 cmdlet이 제공 하는 기존 형식을 cmdlet에서 확장 해야 할 수도 있습니다. 새 형식을 정의 하거나 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 [개체 형식 확장 및 서식 지정](/previous-versions/ms714665(v=vs.85))을 참조 하세요.

## <a name="building-the-cmdlet"></a>Cmdlet 빌드

Cmdlet을 구현한 후 Windows PowerShell 스냅인을 사용 하 여 Windows PowerShell에 등록 해야 합니다. Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions/ms714644(v=vs.85))을 참조 하세요.

## <a name="testing-the-cmdlet"></a>Cmdlet 테스트

Windows PowerShell을 사용 하 여 cmdlet을 등록 한 경우 명령줄에서 실행 하 여 테스트할 수 있습니다. 다음은 샘플 cmdlet에 대 한 코드를 테스트 하는 두 가지 방법입니다. 명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 시작](/powershell/scripting/getting-started/getting-started-with-windows-powershell)을 참조 하세요.

- Windows PowerShell 프롬프트에서 다음 명령을 사용 하 여 "IEXPLORE.EXE" 라는 Internet Explorer 프로세스를 나열 합니다.

  ```powershell
  get-proc -name iexplore
  ```

  다음 출력이 표시됩니다.

  ```Output
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
  -------  ------  -----   -----  -----   ------ --   -----------
      354      11  10036   18992    85   0.67   3284   iexplore
  ```

- "IEXPLORE.EXE", "OUTLOOK" 및 "NOTEPAD" 라는 Internet Explorer, Outlook 및 메모장 프로세스를 나열 하려면 다음 명령을 사용 합니다. 여러 프로세스가 있는 경우 모든 프로세스가 표시 됩니다.

  ```powershell
  get-proc -name iexplore, outlook, notepad
  ```

  다음 출력이 표시됩니다.

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
  -------  ------  -----   -----  -----  ------   --   -----------
      732      21  24696    5000    138   2.25  2288   iexplore
      715      19  20556   14116    136   1.78  3860   iexplore
     3917      62  74096   58112    468 191.56  1848   OUTLOOK
       39       2   1024    3280     30   0.09  1444   notepad
       39       2   1024     356     30   0.08  3396   notepad
  ```

## <a name="see-also"></a>참고 항목

[파이프라인 입력을 처리하는 매개 변수 추가](./adding-parameters-that-process-pipeline-input.md)

[첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)

[개체 형식 및 서식 확장](/previous-versions/ms714665(v=vs.85))

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell 참조](../windows-powershell-reference.md)

[Cmdlet 샘플](./cmdlet-samples.md)
