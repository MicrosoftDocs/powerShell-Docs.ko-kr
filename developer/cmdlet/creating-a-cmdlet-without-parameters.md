---
title: 매개 변수 없이 Cmdlet 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: 75a45e539b45b50714951f2b992d9ecf69de4664
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860649"
---
# <a name="creating-a-cmdlet-without-parameters"></a>매개 변수 없이 Cmdlet 만들기

이 섹션에는 매개 변수를 사용 하지 않고 로컬 컴퓨터에서 정보를 검색 한 다음 파이프라인에 정보를 기록 하는 cmdlet을 만드는 방법을 설명 합니다. 여기에 설명 된 cmdlet은 로컬 컴퓨터의 프로세스에 대 한 정보를 검색 하 고 다음 명령줄에서 해당 정보를 표시 하는 Get-proc cmdlet.

이 섹션의에서 항목에서는 다음과 같습니다.

- [Cmdlet 이름 지정](#Naming-the-Cmdlet)

- [Cmdlet 클래스 정의](#Defining-the-Cmdlet-Class)

- [입력 처리 메서드를 재정의 합니다.](#Overriding-an-Input-Processing-Method)

- [코드 샘플](#Code-Sample)

- [개체 유형 정의 및 서식 지정](#Defining-Object-Types-and-Formatting)

- [Cmdlet은 빌드](#Building-the-Cmdlet)

- [테스트 Cmdlet](#Testing-the-Cmdlet)

> [!NOTE]
> Cmdlet를 작성할 때 Windows PowerShell® 참조 어셈블리를 다운로드 된 디스크에 기본적으로 C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0에 주의 합니다. 이러한 전역 어셈블리 캐시 (GAC)에 설치 되지 않습니다.

## <a name="naming-the-cmdlet"></a>Cmdlet 이름 지정

Cmdlet 이름은 cmdlet 동작 사용 여부를 나타내는 동사와 명사 cmdlet을 실행 하는 항목을 나타내는 구성 됩니다. 이 샘플 Get-proc cmdlet은 프로세스 개체를 검색 하기 때문에 사용 하 여 동사 "Get", 정의한 합니다 [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) 열거 및 명사 "Proc" 항목을 처리에서 cmdlet이 작동 하는지 나타냅니다.

Cmdlet 이름을 지정 하는 경우 사용 하지 마십시오는 다음 문자: #, () {} &-/ \ $;: "' <> &#124; ? @ ` .

### <a name="choosing-a-noun"></a>명사를 선택합니다.

관련 된 명사를 선택 해야 합니다. 제품 이름의 약식된 버전 접두사로 단 수 명사를 사용 하는 것이 좋습니다. 예제에서는 cmdlet이이 종류의 이름은 "`Get-SQLServer`"입니다.

### <a name="choosing-a-verb"></a>동사를 선택합니다.

Cmdlet은 승인 된 동사 이름 집합에서 동사를 사용 해야 합니다. 승인 된 cmdlet 동사에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)합니다.

## <a name="defining-the-cmdlet-class"></a>Cmdlet 클래스 정의

Cmdlet 이름, 선택 했으면 cmdlet을 구현 하는.NET 클래스를 정의 합니다. 이 샘플 Get-proc cmdlet에 대 한 클래스 정의 다음과 같습니다.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

클래스 정의 전에 있음을 합니다 [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 구문 사용 하 여 특성을 `[Cmdlet(verb, noun, ...)]`를 cmdlet으로이 클래스를 식별 하는 데 사용 됩니다. 모든 cmdlet에 대 한 필수 속성 이며 올바르게 호출 하는 Windows PowerShell 런타임에 수 있습니다. 필요한 경우 추가 클래스를 선언 하려면 키워드 특성을 설정할 수 있습니다. 샘플 GetProcCommand 클래스에 대 한 특성 선언을 Get-proc cmdlet의 명사 및 동사 이름 선언 있는지 알아야 합니다.

> [!NOTE]
> Windows PowerShell의 모든 특성 클래스에 설정할 수 있는 키워드는 특성 클래스의 속성에 해당 합니다.

Cmdlet의 클래스 이름 지정 때 클래스 이름에 cmdlet 이름을 반영 하도록 하는 것이 좋습니다. 이렇게 하려면 "VerbNounCommand" 형식을 사용 하 여 및 동사와 명사 cmdlet 이름에 사용 되는 "동사" 및 "명사"를 대체 합니다. 이전 클래스 정의에 표시 된 대로 샘플 Get-proc cmdlet에서 파생 되는 GetProcCommand 라는 클래스를 정의 하는 합니다 [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) 기본 클래스입니다.

> [!IMPORTANT]
> .NET 클래스에서 파생 해야 Windows PowerShell 런타임에 직접 액세스 하는 cmdlet을 정의 하려는 경우는 [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 기본 클래스입니다. 이 클래스에 대 한 자세한 내용은 참조 하세요. [Cmdlet을 해당 정의 매개 변수 집합을 만드는](./adding-parameter-sets-to-a-cmdlet.md)합니다.

> [!NOTE]
> Cmdlet에 대 한 클래스 해야 명시적으로 공용으로 표시 되어야 합니다. 공용으로 표시 되지 않는 클래스는 기본적으로 내부 및 Windows PowerShell 런타임에 의해 찾을 수 없습니다.

Windows PowerShell을 사용 합니다 [Microsoft.Powershell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) 해당 cmdlet 클래스에 대 한 네임 스페이스입니다. 예를 들어 xxx.PS.Commands API 네임 스페이스의 명령 네임 스페이스의 cmdlet 클래스를 배치 하는 것이 좋습니다.

## <a name="overriding-an-input-processing-method"></a>입력 처리 메서드를 재정의 합니다.

합니다 [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) 클래스는 cmdlet를 재정의 해야 하는 중 하나 이상이 세 개의 기본 입력된 처리 메서드를 제공 합니다. Windows PowerShell에서 레코드를 처리 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 작동 방식](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)합니다.

Windows PowerShell 런타임에 입력의 모든 형식에 대 한 호출 [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 처리를 사용 하도록 설정 합니다. Cmdlet에 몇 가지 전처리 또는 설치를 수행 해야 하는 경우이 메서드를 재정의 하 여이 수행할 수 것입니다.

> [!NOTE]
> Windows PowerShell cmdlet를 호출할 때 제공 하는 매개 변수 값의 집합을 설명 "레코드" 라는 용어를 사용 합니다.

Cmdlet가 파이프라인 입력을 수락 재정의 해야 합니다 [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 및 필요에 따라는 [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)메서드. 예를 들어 통해 cmdlet을 사용 하 여 모든 입력 수집 하는 경우 모두 메서드를 재정의할 수 있습니다 [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 한 다음 입력에 하나의 요소가 아닌 전체 번으로 `Sort-Object` cmdlet은 하지 않습니다.

Cmdlet은 파이프라인 입력에 수행 하지 하는 경우 재정의 해야 합니다 [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 메서드. 이 메서드 대신 자주 사용 됩니다 [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 경우 cmdlet은 작업할 수 없습니다. 하나의 요소가 한 번에 정렬 cmdlet의 경우와 마찬가지로 합니다.

재정의 샘플 Get-proc cmdlet이 파이프라인 입력을 수신 해야, 하므로 합니다 [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드 사용에 대 한 기본 구현을 [ System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 하 고 [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)합니다. 합니다 [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 재정의 프로세스를 검색 하 고 사용 하 여 명령줄에 기록 합니다 [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드입니다.

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a>입력된 처리를 기억해 야 할 사항

- 입력에 대 한 기본 소스는 명령줄에서 사용자가 제공한 명시적 개체 (예를 들어, 문자열). 자세한 내용은 [프로세스 명령줄 입력 하는 Cmdlet 만들기](./adding-parameters-that-process-command-line-input.md)합니다.

- 입력 처리 메서드는 파이프라인에는 업스트림 cmdlet의 출력 개체에서 입력을 받을 수도 있습니다. 자세한 내용은 [프로세스 파이프라인 입력 하는 Cmdlet 만들기](./adding-parameters-that-process-pipeline-input.md)합니다. 주의 cmdlet을 조합 명령줄 입력을 수신 하 고 파이프라인 수는 원본입니다.

- 오랜 시간 동안, 또는 전혀 다운스트림 cmdlet 반환 하지 않을 수 있습니다. 따라서 입력 cmdlet에서 메서드를 처리 해야 잠금을 보유 하지 호출 하는 동안 [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)는 범위를 벗어나는 cmdlet 인스턴스 잠금을 특히 합니다.

> [!IMPORTANT]
> Cmdlet을 호출 하지 말아야 [System.Console.Writeline*](/dotnet/api/System.Console.WriteLine) 또는 이와 동등한 합니다.

- Cmdlet을 마치면 정리 하기 위해 개체 변수 있을 수 있습니다 처리 (에서 파일 핸들이 열릴 경우에 예를 들어, 합니다 [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 메서드와 핸들 여 용도로 유지[ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)). 것이 Windows PowerShell 런타임에 항상 호출 하지 않습니다 고려해 야 합니다 [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 개체 정리를 수행 해야 하는 메서드.

예를 들어 [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) cmdlet 중간 취소 되거나 종료 하는 경우 cmdlet의 모든 부분에서 오류가 발생 하는 경우 호출 되지 않을 수 있습니다. 개체를 정리 해야 하는 cmdlet 전체 구현 해야 하므로 [System.Idisposable](/dotnet/api/System.IDisposable) 패턴을 둘 다 런타임에 호출할 수 있도록 종료자를 포함 하 여 [ System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 하 고 [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) 처리의 끝입니다.

## <a name="code-sample"></a>코드 예제

전체 C# 코드 샘플을 참조 하십시오 [GetProcessSample01 샘플](./getprocesssample01-sample.md)합니다.

## <a name="defining-object-types-and-formatting"></a>개체 유형 정의 및 서식 지정

Windows PowerShell.NET 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다. 따라서 cmdlet는 고유한 형식을 정의 해야 합니다. 또는 cmdlet을 다른 cmdlet에서 제공 하는 기존 형식을 확장 해야 할 수 있습니다. 새 형식 정의 또는 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 개체 형식 및 서식](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.

## <a name="building-the-cmdlet"></a>Cmdlet은 빌드

Cmdlet를 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell을 사용 하 여 등록 해야 합니다. Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.

## <a name="testing-the-cmdlet"></a>테스트 Cmdlet

Windows PowerShell cmdlet에 등록 하는 경우 명령줄에서 실행 하 여 테스트할 수 있습니다. 이 샘플 Get-proc cmdlet에 대 한 코드 크지 않지만 Windows PowerShell 런타임 및을 유용 하 게 있는 기존.NET 개체를 계속 사용 합니다. Get-proc 수행할 수 있는 작업 및 해당 출력 사용할 수 있는 방법을 더 잘 이해 하 고 테스트해 보겠습니다. 명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 참조는 [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)합니다.

1. Windows PowerShell을 시작 하 고 컴퓨터에서 실행 중인 현재 프로세스를 가져옵니다.

    ```powershell
    get-proc
    ```

    다음과 같은 출력이 표시 됩니다.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. 보다 쉽게 조작할 cmdlet 결과 변수에 할당 합니다.

    ```powershell
    $p=get-proc
    ```

3. 프로세스의 수를 가져옵니다.

    ```powershell
    $p.length
    ```

    다음과 같은 출력이 표시 됩니다.

    ```output
    63
    ```

4. 특정 프로세스를 검색 합니다.

    ```powershell
    $p[6]
    ```

    다음과 같은 출력이 표시 됩니다.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. 이 프로세스의 시작 시간을 가져옵니다.

    ```powershell
    $p[6].starttime
    ```

    다음과 같은 출력이 표시 됩니다.

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. 핸들 개수는 500을 초과 하는 프로세스를 가져옵니다 하 고 결과 정렬 합니다.

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    다음과 같은 출력이 표시 됩니다.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. 사용 된 `Get-Member` 각 프로세스에 대해 사용할 수 있는 속성을 나열 하는 cmdlet입니다.

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    다음과 같은 출력이 표시 됩니다.

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a>참고 항목

[명령줄 입력을 처리 하는 Cmdlet 만들기](./adding-parameters-that-process-command-line-input.md)

[파이프라인 입력을 처리 하는 Cmdlet 만들기](./adding-parameters-that-process-pipeline-input.md)

[Windows PowerShell Cmdlet을 만드는 방법](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[확장 개체 형식 및 서식 지정](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Windows PowerShell의 작동 원리](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell 참조](../windows-powershell-reference.md)

[Cmdlet 샘플](./cmdlet-samples.md)