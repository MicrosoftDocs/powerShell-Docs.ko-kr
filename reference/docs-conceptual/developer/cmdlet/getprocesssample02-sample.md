---
title: GetProcessSample02 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364572"
---
# <a name="getprocesssample02-sample"></a>GetProcessSample02 샘플

이 샘플에서는 로컬 컴퓨터의 프로세스를 검색 하는 cmdlet을 작성 하는 방법을 보여 줍니다. 이 클래스는 검색할 프로세스를 지정 하는 데 사용할 수 있는 `Name` 매개 변수를 제공 합니다. 이 cmdlet은 Windows PowerShell 2.0에서 제공 하는 `Get-Process` cmdlet의 단순화 된 버전입니다.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Visual Studio를 사용 하 여 샘플을 빌드하는 방법입니다.

1. Windows PowerShell 2.0 SDK가 설치 된 상태에서 GetProcessSample02 폴더로 이동 합니다. 기본 위치는 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.

2. 솔루션 (.sln) 파일의 아이콘을 두 번 클릭 합니다. 그러면 Visual Studio에서 샘플 프로젝트가 열립니다.

3. **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.

    샘플에 대 한 라이브러리는 기본 \bin 또는 \bin\debug 폴더에 빌드됩니다.

### <a name="how-to-run-the-sample"></a>샘플을 실행하는 방법

1. 다음 모듈 폴더를 만듭니다.

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. 모듈 폴더에 샘플 어셈블리를 복사 합니다.

3. Windows PowerShell을 시작합니다.

4. 다음 명령을 실행 하 여 Windows PowerShell에 어셈블리를 로드 합니다.

    `import-module getprossessample02`

5. 다음 명령을 실행 하 여 cmdlet을 실행 합니다.

    `get-proc`

## <a name="requirements"></a>요구 사항

이 샘플에는 Windows PowerShell 2.0이 필요 합니다.

## <a name="demonstrates"></a>데모

이 샘플에서는 다음을 보여 줍니다.

- Cmdlet 특성을 사용 하 여 cmdlet 클래스 선언

- 매개 변수 특성을 사용 하 여 cmdlet 매개 변수 선언

- 매개 변수의 위치를 지정 하는입니다.

- 매개 변수 입력에 대 한 유효성 검사 특성을 선언 합니다.

## <a name="example"></a>예제

이 샘플은 `Name` 매개 변수를 포함 하는 Get Proc cmdlet의 구현을 보여 줍니다.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return this.processNames; }
      set { this.processNames = value; }
    }

    #endregion Parameters

    #region Cmdlet Overrides

    /// <summary>
    /// The ProcessRecord method calls the Process.GetProcesses
    /// method to retrieve the processes specified by the Name
    /// parameter. Then, the WriteObject method writes the
    /// associated process objects to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
