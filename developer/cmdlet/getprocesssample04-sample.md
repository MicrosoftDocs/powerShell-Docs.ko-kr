---
title: GetProcessSample04 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068031"
---
# <a name="getprocesssample04-sample"></a>GetProcessSample04 샘플

이 샘플에는 로컬 컴퓨터의 프로세스를 검색 하는 cmdlet을 구현 하는 방법을 보여 줍니다. 프로세스를 검색 하는 동안 오류가 발생 하는 경우 종료 되지 않는 오류를 생성 합니다. 이 cmdlet은의 단순화 된 버전을 `Get-Process` cmdlet은 Windows PowerShell 2.0에서 제공 합니다.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Visual Studio를 사용 하 여 샘플을 빌드하는 방법.

1. Windows PowerShell 2.0 SDK 설치를 사용 하 여 GetProcessSample04 폴더로 이동 합니다. 기본 위치는 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04 합니다.

2. 솔루션 (.sln) 파일의 아이콘을 두 번 클릭 합니다. 이 Visual Studio에서 샘플 프로젝트를 엽니다.

3. 에 **빌드** 메뉴에서 **솔루션 빌드**합니다.

    이 샘플에 대 한 라이브러리 기본 \bin 또는 \bin\debug 폴더에 빌드됩니다.

### <a name="how-to-run-the-sample"></a>샘플을 실행 하는 방법

1. 다음 모듈 폴더를 만듭니다.

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. 모듈 폴더에 샘플 어셈블리를 복사 합니다.

3. Windows PowerShell을 시작합니다.

4. Windows PowerShell에는 어셈블리를 로드 하려면 다음 명령을 실행 합니다.

    `Import-module getprossessample04`

5. Cmdlet을 실행 하려면 다음 명령을 실행 합니다.

    `get-proc`

## <a name="requirements"></a>요구 사항

이 샘플 Windows PowerShell 2.0이 필요 합니다.

## <a name="demonstrates"></a>데모

이 샘플에는 다음 방법을 보여 줍니다.

- Cmdlet 특성을 사용 하는 cmdlet 클래스를 선언 합니다.

- 매개 변수 특성을 사용 하는 cmdlet 매개 변수를 선언 합니다.

- 매개 변수의 위치를 지정 합니다.

- 매개 변수는 파이프라인의 입력을 지정 합니다. 입력 개체 또는 속성 이름이 매개 변수 이름이 동일 개체의 속성에서 값을 가져올 수 있습니다.

- 입력 매개 변수에 대 한 유효성 검사 특성을 선언 합니다.

- 종료 되지 않는 오류를 트래핑 하 고 오류 스트림에 오류 메시지를 작성 합니다.

## <a name="example"></a>예제

이 샘플에는 오류 스트림에 오류 메시지를 쓰고 종료 되지 않는 오류를 처리 하는 cmdlet을 만드는 방법을 보여 줍니다.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Diagnostics;
    using System.Management.Automation;      // Windows PowerShell namespace.
   #region GetProcCommand

   /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Parameters

       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
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
      /// associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
          // If no process names are passed to cmdlet, get all
          // processes.
          if (this.processNames == null)
          {
              WriteObject(Process.GetProcesses(), true);
          }
          else
          {
              // If process names are passed to the cmdlet, get and write
              // the associated processes.
              // If a nonterminating error occurs while retrieving processes,
              // call the WriteError method to send an error record to the
              // error stream.
              foreach (string name in this.processNames)
              {
                  Process[] processes;

                  try
                  {
                      processes = Process.GetProcessesByName(name);
                  }
                  catch (InvalidOperationException ex)
                  {
                      WriteError(new ErrorRecord(
                         ex,
                         "UnableToAccessProcessByName",
                         ErrorCategory.InvalidOperation,
                         name));
                      continue;
                  }

                  WriteObject(processes, true);
              } // foreach (string name...
          } // else
      } // ProcessRecord

      #endregion Overrides
    } // End GetProcCommand class.

   #endregion GetProcCommand
}
```

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
