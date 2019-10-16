---
title: StopProcessSample01 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7bed607-369b-4507-87fa-f6011c2f1970
caps.latest.revision: 9
ms.openlocfilehash: 2ce146df05ef876d9c17f560628ebac2c39e57bf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365302"
---
# <a name="stopprocesssample01-sample"></a><span data-ttu-id="46a0f-102">StopProcessSample01 샘플</span><span class="sxs-lookup"><span data-stu-id="46a0f-102">StopProcessSample01 Sample</span></span>

<span data-ttu-id="46a0f-103">이 샘플에서는 프로세스를 중지 하기 전에 사용자에 게 피드백을 요청 하는 cmdlet을 작성 하는 방법과 사용자가 cmdlet을 사용 하 여 개체를 반환 하도록 하는 `PassThru` 매개 변수를 구현 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-103">This sample shows how to write a cmdlet that requests feedback from the user before it attempts to stop a process, and how to implement a `PassThru` parameter indicating that the user wants the cmdlet to return an object.</span></span> <span data-ttu-id="46a0f-104">이 cmdlet은 Windows PowerShell 2.0에서 제공 하는 `Stop-Process` cmdlet과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-104">This cmdlet is similar to the `Stop-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

### <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="46a0f-105">Visual Studio를 사용 하 여 샘플을 빌드하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="46a0f-106">Windows PowerShell 2.0 SDK가 설치 된 상태에서 StopProcessSample01 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-106">With the Windows PowerShell 2.0 SDK installed, navigate to the StopProcessSample01 folder.</span></span> <span data-ttu-id="46a0f-107">기본 위치는 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="46a0f-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample01.</span></span>

2. <span data-ttu-id="46a0f-108">솔루션 (.sln) 파일의 아이콘을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="46a0f-109">그러면 Microsoft Visual Studio의 샘플 프로젝트가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="46a0f-110">**빌드** 메뉴에서 **솔루션 빌드**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-110">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="46a0f-111">샘플에 대 한 라이브러리는 기본 \bin 또는 \bin\debug 폴더에 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="46a0f-112">샘플을 실행 하는 방법</span><span class="sxs-lookup"><span data-stu-id="46a0f-112">How to run the sample</span></span>

1. <span data-ttu-id="46a0f-113">다음 모듈 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-113">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/StopProcessSample01`

2. <span data-ttu-id="46a0f-114">모듈 폴더에 샘플 어셈블리를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-114">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="46a0f-115">Windows PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-115">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="46a0f-116">다음 명령을 실행 하 여 Windows PowerShell에 어셈블리를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-116">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module stopprossessample01`

5. <span data-ttu-id="46a0f-117">다음 명령을 실행 하 여 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-117">Run the following command to run the cmdlet:</span></span>

    `stop-proc`

## <a name="requirements"></a><span data-ttu-id="46a0f-118">요구 사항</span><span class="sxs-lookup"><span data-stu-id="46a0f-118">Requirements</span></span>

<span data-ttu-id="46a0f-119">이 샘플에는 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-119">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="46a0f-120">보여</span><span class="sxs-lookup"><span data-stu-id="46a0f-120">Demonstrates</span></span>

<span data-ttu-id="46a0f-121">이 샘플에서는 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-121">This sample demonstrates the following.</span></span>

- <span data-ttu-id="46a0f-122">Cmdlet 특성을 사용 하 여 cmdlet 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="46a0f-122">Declaring a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="46a0f-123">매개 변수 특성을 사용 하 여 cmdlet 매개 변수 선언</span><span class="sxs-lookup"><span data-stu-id="46a0f-123">Declaring a cmdlet parameters by using the Parameter attribute.</span></span>

- <span data-ttu-id="46a0f-124">확인을 요청 하는 ShouldProcess 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-124">Calling the ShouldProcess method to request confirmation.</span></span>

- <span data-ttu-id="46a0f-125">사용자가 cmdlet을 사용 하 여 개체를 반환 하려고 하는지 여부를 나타내는 0 @no__t 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-125">Implementing a `PassThru` parameter that indicates if the user wants the cmdlet to return an object.</span></span> <span data-ttu-id="46a0f-126">기본적으로이 cmdlet은 개체를 파이프라인에 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-126">By default, this cmdlet does not return an object to the pipeline.</span></span>

## <a name="example"></a><span data-ttu-id="46a0f-127">예제</span><span class="sxs-lookup"><span data-stu-id="46a0f-127">Example</span></span>

<span data-ttu-id="46a0f-128">이 샘플에서는 사용자가 cmdlet에서 개체를 반환 하도록 지정 하는 `PassThru` 매개 변수를 구현 하는 방법과 `ShouldProcess` 및 `ShouldContinue` 메서드를 호출 하 여 사용자 피드백을 요청 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="46a0f-128">This sample shows how to implement a `PassThru` parameter that indicates that the user wants the cmdlet to return an object, and how to request user feedback by calls to the `ShouldProcess` and `ShouldContinue` methods.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Collections;
using Win32Exception = System.ComponentModel.Win32Exception;
using System.Management.Automation;    // Windows PowerShell namespace
using System.Globalization;

namespace Microsoft.Samples.PowerShell.Commands
{
   #region StopProcCommand

    /// <summary>
   /// This class implements the stop-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsLifecycle.Stop, "Proc",
       SupportsShouldProcess = true)]
   public class StopProcCommand : Cmdlet
   {
       #region Parameters

      /// <summary>
      /// This parameter provides the list of process names on
      /// which the Stop-Proc cmdlet will work.
      /// </summary>
       [Parameter(
          Position = 0,
          Mandatory = true,
          ValueFromPipeline = true,
          ValueFromPipelineByPropertyName = true
       )]
       public string[] Name
       {
           get { return processNames; }
           set { processNames = value; }
       }
       private string[] processNames;

       /// <summary>
       /// This parameter overrides the ShouldContinue call to force
       /// the cmdlet to stop its operation. This parameter should always
       /// be used with caution.
       /// </summary>
       [Parameter]
       public SwitchParameter Force
       {
           get { return force; }
           set { force = value; }
       }
       private bool force;

       /// <summary>
       /// This parameter indicates that the cmdlet should return
       /// an object to the pipeline after the processing has been
       /// completed.
       /// </summary>
       [Parameter]
       public SwitchParameter PassThru
       {
           get { return passThru; }
           set { passThru = value; }
       }
       private bool passThru;

       #endregion Parameters

       #region Cmdlet Overrides

       /// <summary>
       /// The ProcessRecord method does the following for each of the
       /// requested process names:
       /// 1) Check that the process is not a critical process.
       /// 2) Attempt to stop that process.
       /// If no process is requested then nothing occurs.
       /// </summary>
       protected override void ProcessRecord()
       {
           foreach (string name in processNames)
           {
               // For every process name passed to the cmdlet, get the associated
               // processes.
               // Write a nonterminating error for failure to retrieve
               // a process.
               Process[] processes;

               try
               {
                   processes = Process.GetProcessesByName(name);
               }
               catch (InvalidOperationException ioe)
               {
                   WriteError(new ErrorRecord(ioe,"UnableToAccessProcessByName",
                       ErrorCategory.InvalidOperation, name));

                   continue;
               }

               // Try to stop the processes that have been retrieved.
               foreach (Process process in processes)
               {
                   string processName;

                   try
                   {
                       processName = process.ProcessName;
                   }
                   catch (Win32Exception e)
                   {
                      WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                                           ErrorCategory.ReadError, process));
                      continue;
                   }

                   // Confirm the operation with the user first.
                   // This is always false if the WhatIf parameter is set.
                   if (!ShouldProcess(string.Format(CultureInfo.CurrentCulture,"{0} ({1})", processName,
                               process.Id)))
                   {
                       continue;
                   }

                   // Make sure that the user really wants to stop a critical
                   // process that could possibly stop the computer.
                   bool criticalProcess =
                       criticalProcessNames.Contains(processName.ToLower(CultureInfo.CurrentCulture));

                   if (criticalProcess &&!force)
                   {
                       string message = String.Format
                           (CultureInfo.CurrentCulture,
                                "The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                                    processName);

                       // It is possible that the ProcessRecord method is called
                       // multiple times when objects are received as inputs from
                       // the pipeline. So to retain YesToAll and NoToAll input that
                       // the user may enter across multiple calls to this function,
                       // they are stored as private members of the cmdlet.
                       if (!ShouldContinue(message, "Warning!",
                                               ref yesToAll, ref noToAll))
                       {
                           continue;
                       }
                   } // if (criticalProcess...

                   // Stop the named process.
                   try
                   {
                       process.Kill();
                   }
                   catch (Exception e)
                   {
                       if ((e is Win32Exception) || (e is SystemException) ||
                          (e is InvalidOperationException))
                       {
                           // This process could not be stopped so write
                           // a nonterminating error.
                           WriteError(new ErrorRecord(e, "CouldNotStopProcess",
                                           ErrorCategory.CloseError, process));
                           continue;
                       } // if ((e is...
                       else throw;
                   } // catch

                   // If the PassThru parameter is
                   // specified, return the terminated process.
                   if (passThru)
                   {
                       WriteObject(process);
                   }
               } // foreach (Process...
           } // foreach (string...
       } // ProcessRecord

       #endregion Cmdlet Overrides

       #region Private Data

       private bool yesToAll, noToAll;

       /// <summary>
       /// Partial list of critical processes that should not be
       /// stopped.  Lower case is used for case insensitive matching.
       /// </summary>
       private ArrayList criticalProcessNames = new ArrayList(
          new string[] { "system", "winlogon", "spoolsv" }
       );

       #endregion Private Data

   } // StopProcCommand

   #endregion StopProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="46a0f-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="46a0f-129">See Also</span></span>

<span data-ttu-id="46a0f-130">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="46a0f-130">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
