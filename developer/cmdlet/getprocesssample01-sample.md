---
title: GetProcessSample01 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 00190c7350cb0f1cfc5c389b56e48e9397480446
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859839"
---
# <a name="getprocesssample01-sample"></a>GetProcessSample01 샘플

이 샘플에는 로컬 컴퓨터의 프로세스를 검색 하는 cmdlet을 구현 하는 방법을 보여 줍니다. 이 cmdlet은의 단순화 된 버전을 `Get-Process` Windows PowerShell 2.0에서 제공 하는 cmdlet입니다.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Visual Studio를 사용 하 여 샘플을 빌드하는 방법입니다.

1. Windows PowerShell 2.0 SDK 설치를 사용 하 여 GetProcessSample01 폴더로 이동 합니다. 기본 위치는 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01 합니다.

2. 솔루션 (.sln) 파일의 아이콘을 두 번 클릭 합니다. 이 Microsoft Visual Studio에서 샘플 프로젝트를 엽니다.

3. 에 **빌드** 메뉴에서 **솔루션 빌드**합니다.

  이 샘플에 대 한 라이브러리 기본 \bin 또는 \bin\debug 폴더에 빌드됩니다.

### <a name="how-to-run-the-sample"></a>샘플을 실행 하는 방법

1. 명령 프롬프트 창을 엽니다.

2. 샘플.dll 파일이 포함 된 디렉터리로 이동 합니다.

3. "GetProcessSample01.dll" installutil을 실행 합니다.

4. Windows PowerShell을 시작합니다.

5. 셸에 스냅인을 추가 하려면 다음 명령을 실행 합니다.

   `Add-PSSnapin GetProcPSSnapIn01`

6. Cmdlet을 실행 하려면 다음 명령을 입력 합니다. `get-proc`

   `get-proc`

   이 다음 단계에서 발생 하는 샘플 출력입니다.

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a>요구 사항

이 샘플에는 Windows PowerShell 1.0 이상이 필요합니다.

## <a name="demonstrates"></a>시연

이 샘플에는 다음 방법을 보여 줍니다.

- 기본 샘플 cmdlet을 만드는 중입니다.

- Cmdlet 특성을 사용 하 여 cmdlet 클래스를 정의 합니다.

- Windows PowerShell 2.0 및 Windows PowerShell 1.0을 사용 하 여 작동 하는 스냅인을 만드는 중입니다. 다음에 나오는 샘플 Windows PowerShell 2.0 필요 하므로 스냅인 대신 모듈을 사용 합니다.

## <a name="example"></a>예제

이 샘플에는 간단한 cmdlet 및 해당 스냅인을 만드는 방법을 보여 줍니다.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)