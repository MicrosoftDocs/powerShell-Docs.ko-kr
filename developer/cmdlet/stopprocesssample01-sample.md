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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059204"
---
# <a name="stopprocesssample01-sample"></a><span data-ttu-id="76fbf-102">StopProcessSample01 샘플</span><span class="sxs-lookup"><span data-stu-id="76fbf-102">StopProcessSample01 Sample</span></span>

<span data-ttu-id="76fbf-103">이 샘플에서는 프로세스를 중지 하려고 시도 하기 전에 사용자 로부터 피드백을 요청 하는 cmdlet을 작성 하는 방법 및 구현 하는 방법을 보여 줍니다.는 `PassThru` 나타내는 사용자가 cmdlet 개체를 반환 하는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-103">This sample shows how to write a cmdlet that requests feedback from the user before it attempts to stop a process, and how to implement a `PassThru` parameter indicating that the user wants the cmdlet to return an object.</span></span> <span data-ttu-id="76fbf-104">이 cmdlet은 비슷합니다는 `Stop-Process` cmdlet은 Windows PowerShell 2.0에서 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-104">This cmdlet is similar to the `Stop-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

### <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="76fbf-105">Visual Studio를 사용 하 여 샘플을 빌드하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="76fbf-106">Windows PowerShell 2.0 SDK 설치를 사용 하 여 StopProcessSample01 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-106">With the Windows PowerShell 2.0 SDK installed, navigate to the StopProcessSample01 folder.</span></span> <span data-ttu-id="76fbf-107">기본 위치는 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample01 합니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample01.</span></span>

2. <span data-ttu-id="76fbf-108">솔루션 (.sln) 파일의 아이콘을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="76fbf-109">이 Microsoft Visual Studio에서 샘플 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="76fbf-110">에 **빌드** 메뉴에서 **솔루션 빌드**합니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-110">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="76fbf-111">이 샘플에 대 한 라이브러리 기본 \bin 또는 \bin\debug 폴더에 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="76fbf-112">샘플을 실행 하는 방법</span><span class="sxs-lookup"><span data-stu-id="76fbf-112">How to run the sample</span></span>

1. <span data-ttu-id="76fbf-113">다음 모듈 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-113">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/StopProcessSample01`

2. <span data-ttu-id="76fbf-114">모듈 폴더에 샘플 어셈블리를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-114">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="76fbf-115">Windows PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-115">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="76fbf-116">Windows PowerShell에는 어셈블리를 로드 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-116">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module stopprossessample01`

5. <span data-ttu-id="76fbf-117">Cmdlet을 실행 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-117">Run the following command to run the cmdlet:</span></span>

    `stop-proc`

## <a name="requirements"></a><span data-ttu-id="76fbf-118">요구 사항</span><span class="sxs-lookup"><span data-stu-id="76fbf-118">Requirements</span></span>

<span data-ttu-id="76fbf-119">이 샘플 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-119">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="76fbf-120">시연</span><span class="sxs-lookup"><span data-stu-id="76fbf-120">Demonstrates</span></span>

<span data-ttu-id="76fbf-121">이 샘플에는 다음 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-121">This sample demonstrates the following.</span></span>

- <span data-ttu-id="76fbf-122">Cmdlet 특성을 사용 하 여 cmdlet 클래스를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-122">Declaring a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="76fbf-123">매개 변수 특성을 사용 하 여 cmdlet 매개 변수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-123">Declaring a cmdlet parameters by using the Parameter attribute.</span></span>

- <span data-ttu-id="76fbf-124">확인을 요청 하는 ShouldProcess 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-124">Calling the ShouldProcess method to request confirmation.</span></span>

- <span data-ttu-id="76fbf-125">구현 된 `PassThru` 사용자가 cmdlet이 개체를 반환 하는 경우를 나타내는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-125">Implementing a `PassThru` parameter that indicates if the user wants the cmdlet to return an object.</span></span> <span data-ttu-id="76fbf-126">기본적으로이 cmdlet은 개체를 파이프라인에 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76fbf-126">By default, this cmdlet does not return an object to the pipeline.</span></span>

## <a name="example"></a><span data-ttu-id="76fbf-127">예제</span><span class="sxs-lookup"><span data-stu-id="76fbf-127">Example</span></span>

<span data-ttu-id="76fbf-128">이 샘플에서는 구현 하는 방법을 보여 줍니다.는 `PassThru` 사용자가 개체를 반환 하는 cmdlet을 호출 하 여 사용자에 게 피드백을 요청 하는 방법을 나타내는 매개 변수를 `ShouldProcess` 및 `ShouldContinue` 메서드.</span><span class="sxs-lookup"><span data-stu-id="76fbf-128">This sample shows how to implement a `PassThru` parameter that indicates that the user wants the cmdlet to return an object, and how to request user feedback by calls to the `ShouldProcess` and `ShouldContinue` methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="76fbf-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76fbf-129">See Also</span></span>

<span data-ttu-id="76fbf-130">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="76fbf-130">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
