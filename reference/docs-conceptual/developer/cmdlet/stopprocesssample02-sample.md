---
ms.date: 09/13/2016
ms.topic: reference
title: StopProcessSample02 샘플
description: StopProcessSample02 샘플
ms.openlocfilehash: 96171413f9f04d12460d48ba91c2c927e1856fd1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666895"
---
# <a name="stopprocesssample02-sample"></a><span data-ttu-id="823f7-103">StopProcessSample02 샘플</span><span class="sxs-lookup"><span data-stu-id="823f7-103">StopProcessSample02 Sample</span></span>

<span data-ttu-id="823f7-104">이 샘플에서는 로컬 컴퓨터에서 프로세스를 중지 하는 동안 디버그 (WriteDebug), 자세한 정보 표시 (Writedebug) 및 경고 (Writedebug) 메시지를 기록 하는 cmdlet을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-104">This sample shows how to write a cmdlet that writes debug (WriteDebug), verbose (WriteVerbose), and warning (WriteWarning) messages while stopping processes on the local computer.</span></span> <span data-ttu-id="823f7-105">이 cmdlet은 `Stop-Process` Windows PowerShell 2.0에서 제공 하는 cmdlet과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-105">This cmdlet is similar to the `Stop-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

### <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="823f7-106">Visual Studio를 사용 하 여 샘플을 빌드하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="823f7-107">Windows Internet Explorer를 열고 Samples 디렉터리 아래의 StopProcessSample02 디렉터리로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-107">Open Windows Internet Explorer and navigate to the StopProcessSample02 directory under the Samples directory.</span></span>

    <span data-ttu-id="823f7-108">Windows PowerShell 2.0 SDK가 설치 된 상태에서 StopProcessSample02 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-108">With the Windows PowerShell 2.0 SDK installed, navigate to the StopProcessSample02 folder.</span></span> <span data-ttu-id="823f7-109">기본 위치는 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="823f7-109">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample02.</span></span>

2. <span data-ttu-id="823f7-110">솔루션 (.sln) 파일의 아이콘을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-110">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="823f7-111">그러면 Microsoft Visual Studio의 샘플 프로젝트가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-111">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="823f7-112">**빌드** 메뉴에서 **솔루션 빌드** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-112">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="823f7-113">샘플에 대 한 라이브러리는 기본 \bin 또는 \bin\debug 폴더에 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-113">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="823f7-114">샘플을 실행하는 방법</span><span class="sxs-lookup"><span data-stu-id="823f7-114">How to run the sample</span></span>

1. <span data-ttu-id="823f7-115">다음 모듈 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-115">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/StopProcessSample02`

2. <span data-ttu-id="823f7-116">모듈 폴더에 샘플 어셈블리를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-116">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="823f7-117">Windows PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-117">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="823f7-118">다음 명령을 실행 하 여 Windows PowerShell에 어셈블리를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-118">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module stopprossessample02`

5. <span data-ttu-id="823f7-119">다음 명령을 실행 하 여 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-119">Run the following command to run the cmdlet:</span></span>

    `stop-proc`

## <a name="requirements"></a><span data-ttu-id="823f7-120">요구 사항</span><span class="sxs-lookup"><span data-stu-id="823f7-120">Requirements</span></span>

<span data-ttu-id="823f7-121">이 샘플에는 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-121">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="823f7-122">데모</span><span class="sxs-lookup"><span data-stu-id="823f7-122">Demonstrates</span></span>

<span data-ttu-id="823f7-123">이 샘플에서는 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="823f7-124">Cmdlet 특성을 사용 하 여 cmdlet 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="823f7-124">Declaring a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="823f7-125">매개 변수 특성을 사용 하 여 cmdlet 매개 변수 선언</span><span class="sxs-lookup"><span data-stu-id="823f7-125">Declaring a cmdlet parameters by using the Parameter attribute.</span></span>

- <span data-ttu-id="823f7-126">자세한 정보 메시지를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-126">Writing verbose messages.</span></span> <span data-ttu-id="823f7-127">자세한 메시지를 작성 하는 데 사용 되는 방법에 대 한 자세한 내용은 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="823f7-127">For more information about the method used to write verbose messages, see [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

- <span data-ttu-id="823f7-128">오류 메시지를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-128">Writing error messages.</span></span> <span data-ttu-id="823f7-129">오류 메시지를 작성 하는 데 사용 되는 방법에 대 한 자세한 내용은 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="823f7-129">For more information about the method used to write error messages, see [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError).</span></span>

- <span data-ttu-id="823f7-130">경고 메시지를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="823f7-130">Writing warning messages.</span></span> <span data-ttu-id="823f7-131">경고 메시지를 작성 하는 데 사용 되는 방법에 대 한 자세한 내용은 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="823f7-131">For more information about the method used to write warning messages, see [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning).</span></span>

## <a name="example"></a><span data-ttu-id="823f7-132">예제</span><span class="sxs-lookup"><span data-stu-id="823f7-132">Example</span></span>

<span data-ttu-id="823f7-133">이 샘플에서는 `WriteDebug` , 및 메서드를 사용 하 여 디버그, 자세한 정보 및 경고 메시지를 작성 하는 방법을 보여 줍니다 `WriteVerbose` `WriteWarning` .</span><span class="sxs-lookup"><span data-stu-id="823f7-133">This sample shows how to write debug, verbose, and warning messages by using the `WriteDebug`, `WriteVerbose`, and `WriteWarning` methods.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Collections;
using Win32Exception = System.ComponentModel.Win32Exception;
using System.Management.Automation;             //Windows PowerShell namespace
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
               string message = null;

               // For every process name passed to the cmdlet, get the associated
               // processes.
               // Write a nonterminating error for failure to retrieve
               // a process.

               // Write a user-friendly verbose message to the pipeline. These
               // messages are intended to give the user detailed information
               // on the operations performed by the cmdlet. These messages will
               // appear with the -Verbose option.
               message = String.Format(CultureInfo.CurrentCulture,
                              "Attempting to stop process \"{0}\".", name);
               WriteVerbose(message);

               Process[] processes;

               try
               {
                   processes = Process.GetProcessesByName(name);
               }
               catch (InvalidOperationException ioe)
               {
                   WriteError(new ErrorRecord(ioe,
                                     "UnableToAccessProcessByName",
                                         ErrorCategory.InvalidOperation,
                                             name));
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
                                         ErrorCategory.ObjectNotFound, process));
                       continue;
                   }

                   // Write a debug message to the host that can be used when
                   // troubleshooting a problem. All debug messages will appear
                   // with the -Debug option.
                   message = String.Format(CultureInfo.CurrentCulture,
                                 "Acquired name for pid {0} : \"{1}\"",
                                        process.Id, processName);
                   WriteDebug(message);

                   // Confirm the operation first.
                   // This is always false if the WhatIf parameter is specified.
                   if (!ShouldProcess(string.Format(CultureInfo.CurrentCulture,
                                        "{0} ({1})",
                                            processName, process.Id)))
                   {
                       continue;
                   }

                   // Make sure that the user really wants to stop a critical
                   // process that can possibly stop the computer.
                   bool criticalProcess = criticalProcessNames.Contains(processName.ToLower(CultureInfo.CurrentCulture));

                   if (criticalProcess && !force)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
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

                   // Display a warning message if the cmdlet is stopping a
                   // critical process.
                   if (criticalProcess)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
                                     "Stopping the critical process \"{0}\".",
                                          processName);
                       WriteWarning(message);
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
                           WriteError(new ErrorRecord(
                                            e,
                                            "CouldNotStopProcess",
                                            ErrorCategory.CloseError,
                                            process)
                                      );
                           continue;
                       } // if ((e is...
                           else throw;
                   } // catch

                   message = String.Format(CultureInfo.CurrentCulture,
                                  "Stopped process \"{0}\", pid {1}.",
                                        processName, process.Id);

                   WriteVerbose(message);

                   // If the PassThru parameter is specified,
                   // return the terminated process object to the pipeline.
                   if (passThru)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
                                     "Writing process \"{0}\" to pipeline",
                                          processName);
                       WriteDebug(message);
                       WriteObject(process);
                   } // if (passThru...
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

## <a name="see-also"></a><span data-ttu-id="823f7-134">관련 항목</span><span class="sxs-lookup"><span data-stu-id="823f7-134">See Also</span></span>

[<span data-ttu-id="823f7-135">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="823f7-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
