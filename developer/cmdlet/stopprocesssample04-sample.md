---
title: StopProcessSample04 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac4903f5-fd40-4f1c-b1d1-18923c16ce45
caps.latest.revision: 8
ms.openlocfilehash: 26e882dad839af43945f84d4cdd6cda7bdb2d587
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067340"
---
# <a name="stopprocesssample04-sample"></a>StopProcessSample04 샘플

이 샘플에는 매개 변수 집합을 선언, 기본 매개 변수를 설정 하 고 입력된 개체를 받을 수를 지정 하는 cmdlet을 작성 하는 방법을 보여 줍니다. 이 cmdlet은 비슷합니다는 `Stop-Process` cmdlet은 Windows PowerShell 2.0에서 제공 합니다.

### <a name="how-to-build-the-sample-by-using-visual-studio"></a>Visual Studio를 사용 하 여 샘플을 빌드하는 방법입니다.

1. Windows PowerShell 2.0 SDK 설치를 사용 하 여 StopProcessSample04 폴더로 이동 합니다. 기본 위치는 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample04 합니다.

2. 솔루션 (.sln) 파일의 아이콘을 두 번 클릭 합니다. 이 Microsoft Visual Studio에서 샘플 프로젝트를 엽니다.

3. 에 **빌드** 메뉴에서 **솔루션 빌드**합니다.

    이 샘플에 대 한 라이브러리 기본 \bin 또는 \bin\debug 폴더에 빌드됩니다.

### <a name="how-to-run-the-sample"></a>샘플을 실행 하는 방법

1. 다음 모듈 폴더를 만듭니다.

    `[user]/documents/windowspowershell/modules/StopProcessSample04`

2. 모듈 폴더에 샘플 어셈블리를 복사 합니다.

3. Windows PowerShell을 시작합니다.

4. Windows PowerShell에는 어셈블리를 로드 하려면 다음 명령을 실행 합니다.

    `import-module stopprossessample04`

5. Cmdlet을 실행 하려면 다음 명령을 실행 합니다.

    `stop-proc`

## <a name="requirements"></a>요구 사항

이 샘플 Windows PowerShell 2.0이 필요 합니다.

## <a name="demonstrates"></a>데모

이 샘플에는 다음 방법을 보여 줍니다.

- Cmdlet 특성을 사용 하 여 cmdlet 클래스를 선언 합니다.

- 매개 변수 특성을 사용 하 여 cmdlet 매개 변수를 선언 합니다.

- 입력된 개체를 허용 하는 매개 변수를 추가 합니다.

- 매개 변수 집합에는 매개 변수 추가

- 집합 기본 매개 변수를 지정 합니다.

## <a name="example"></a>예제

다음 코드에는 매개 변수 집합을 선언, 기본 매개 변수를 설정 하 고 입력된 개체를 받을 수를 지정 하는 중지 Proc cmdlet의 구현을 보여 줍니다.

이 샘플에는 입력된 개체, 매개 변수 집합을 선언 하는 방법 및 사용 하도록 설정 하는 기본 매개 변수를 지정 하는 방법을 보여 줍니다.

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
       DefaultParameterSetName = "ProcessId",
       SupportsShouldProcess = true)]
   public class StopProcCommand : PSCmdlet
   {
       #region Parameters

      /// <summary>
      /// This parameter provides the list of process names on
      /// which the Stop-Proc cmdlet will work.
      /// </summary>
       [Parameter(
          Position = 0,
          ParameterSetName = "ProcessName",
          Mandatory = true,
          ValueFromPipeline = true,
          ValueFromPipelineByPropertyName = true,
          HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
       )]
       [Alias("ProcessName")]
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
       [Parameter(
          HelpMessage = "If set the process(es) will be passed to the pipeline after stopped."
       )]
       public SwitchParameter PassThru
       {
           get { return passThru; }
           set { passThru = value; }
       }
       private bool passThru;

      /// This parameter provides the list of process identifiers on
      /// which the Stop-Proc cmdlet will work.
       [Parameter(
          ParameterSetName = "ProcessId",
          Mandatory = true,
          ValueFromPipelineByPropertyName = true,
          ValueFromPipeline = true
       )]
       [Alias("ProcessId")]
       public int[] Id
       {
           get { return processIds; }
           set { processIds = value; }
       }
       private int[] processIds;

       /// <summary>
       /// This parameter accepts an array of Process objects from the
       /// the pipeline. This object contains the processes to stop.
       /// </summary>
       /// <value>Process objects</value>
       [Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
       public Process[] InputObject
       {
           get { return inputObject; }
           set { inputObject = value; }
       }
       private Process[] inputObject;

       #endregion Parameters

       #region CmdletOverrides

       /// <summary>
       /// The ProcessRecord method does the following for each of the
       /// requested process names:
       /// 1) Check that the process is not a critical process.
       /// 2) Attempt to stop that process.
       /// If no process is requested then nothing occurs.
       /// </summary>
       protected override void ProcessRecord()
       {
           switch (ParameterSetName)
           {
               case "ProcessName":
                   ProcessByName();
               break;

               case "ProcessId":
                   ProcessById();
                   break;

               case "InputObject":
                   foreach (Process process in inputObject)
                   {
                       SafeStopProcess(process);
                   }
                   break;

               default:
                   throw new ArgumentException("Bad ParameterSet Name");
           } // switch (ParameterSetName...
       } // ProcessRecord

       #endregion Cmdlet Overrides

       #region Helper Methods

       /// <summary>
       /// Returns all processes with matching names.
       /// </summary>
       /// <param name="processName">
       /// The name of the processes to return.
       /// </param>
       /// <param name="allProcesses">An array of all
       /// computer processes.</param>
       /// <returns>An array of matching processes.</returns>
       internal ArrayList SafeGetProcessesByName(string processName,
                                ref ArrayList allProcesses)
       {
           // Create and array to store the matching processes.
           ArrayList matchingProcesses = new ArrayList();

           // Create the wildcard for pattern matching.
           WildcardOptions options = WildcardOptions.IgnoreCase |
                                     WildcardOptions.Compiled;
           WildcardPattern wildcard = new WildcardPattern(processName, options);

           // Walk all of the machine processes.
           foreach(Process process in allProcesses)
           {
               string processNameToMatch = null;
               try
               {
                   processNameToMatch = process.ProcessName;
               }
               catch (Win32Exception e)
               {
                   // Remove the process from the list so that it is not
                   // checked again.
                   allProcesses.Remove(process);

                   string message =
                         String.Format(CultureInfo.CurrentCulture, "The process \"{0}\" could not be found",
                                             processName);
                   WriteVerbose(message);
                   WriteError(new ErrorRecord(e, "ProcessNotFound",
                                    ErrorCategory.ObjectNotFound, processName));

                   continue;
               }

               if (!wildcard.IsMatch(processNameToMatch))
               {
                   continue;
               }

               matchingProcesses.Add(process);
           } // foreach(Process...

           return matchingProcesses;
       } // SafeGetProcessesByName

       /// <summary>
       /// Safely stops a named process.  Used as standalone function
       /// to declutter the ProcessRecord method.
       /// </summary>
       /// <param name="process">The process to stop.</param>
       private void SafeStopProcess(Process process)
       {
           string processName = null;

           try
           {
               processName = process.ProcessName;
           }
           catch (Win32Exception e)
           {
               WriteError(new ErrorRecord(e, "ProcessNotFound",
                                ErrorCategory.OpenError, processName));

               return;
           }

           // Confirm the operation first.
           // This is always false if the WhatIf parameter is specified.
           if (!ShouldProcess(string.Format(CultureInfo.CurrentCulture,
                    "{0} ({1})", processName, process.Id)))
           {
               return;
           }

           // Make sure that the user really wants to stop a critical
           // process that can possibly stop the computer.
           bool criticalProcess = criticalProcessNames.Contains(processName.ToLower(CultureInfo.CurrentCulture));

           string message = null;
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
                   return;
               }
           } // if (criticalProcess...

           // Display a warning message if stopping a critical
           // process.
           if (criticalProcess)
           {
               message =
                 String.Format(CultureInfo.CurrentCulture,
                                "Stopping the critical process \"{0}\".",
                                    processName);
               WriteWarning(message);
           } // if (criticalProcess...

           try
           {
               // Stop the process.
               process.Kill();
           }
           catch (Exception e)
           {
               if ((e is Win32Exception) || (e is SystemException) ||
                   (e is InvalidOperationException))
               {
                   // This process could not be stopped so write
                   // a non-terminating error.
                   WriteError(new ErrorRecord(e, "CouldNotStopProcess",
                                    ErrorCategory.CloseError,
                                    process)
                              );

                   return;
               } // if ((e is...
               else throw;
           } // catch

           // Write a user-level verbose message to the pipeline. These are
           // intended to give the user detailed information on the
           // operations performed by the cmdlet. These messages will
           // appear with the -Verbose option.
           message = String.Format(CultureInfo.CurrentCulture,
                                        "Stopped process \"{0}\", pid {1}.",
                                            processName, process.Id);

           WriteVerbose(message);

           // If the PassThru parameter is specified, return the terminated
           // process to the pipeline.
           if (passThru)
           {
               // Write a debug message to the host that can be used
               // when troubleshooting a problem. All debug messages
               // will appear with the -Debug option
               message =
                   String.Format(CultureInfo.CurrentCulture,
                                    "Writing process \"{0}\" to pipeline",
                                        processName);
               WriteDebug(message);
               WriteObject(process);
           } // if (passThru..
       } // SafeStopProcess

       /// <summary>
       /// Stop processes based on their names (using the
       /// ParameterSetName as ProcessName)
       /// </summary>
       private void ProcessByName()
       {
           ArrayList allProcesses = null;

           // Get a list of all processes.
           try
           {
               allProcesses = new ArrayList(Process.GetProcesses());
           }
           catch (InvalidOperationException ioe)
           {
               base.ThrowTerminatingError(new ErrorRecord(
                    ioe, "UnableToAccessProcessList",
                    ErrorCategory.InvalidOperation, null));
           }

           // If a process name is passed to the cmdlet, get
           // the associated processes.
           // Write a nonterminating error for failure to
           // retrieve a process.
           foreach (string name in processNames)
           {
               // The allProcesses array list is passed as a reference because
               // any process whose name cannot be obtained will be removed
               // from the list so that its not compared the next time.
               ArrayList processes =
                   SafeGetProcessesByName(name, ref allProcesses);

               // If no processes were found write a non-
               // terminating error.
               if (processes.Count == 0)
               {
                   WriteError(new ErrorRecord(
                       new Exception("Process not found."),
                       "ProcessNotFound",
                       ErrorCategory.ObjectNotFound,
                       name));
               } // if (processes...
               // Otherwise terminate all processes in the list.
               else
               {
                   foreach (Process process in processes)
                   {
                       SafeStopProcess(process);
                   } // foreach (Process...
               } // else
           } // foreach (string...
       } // ProcessByName

       /// <summary>
       /// Stop processes based on their identifiers (using the
       /// ParameterSetName as ProcessIds)
       /// </summary>
       internal void ProcessById()
       {
           foreach (int processId in processIds)
           {
               Process process = null;
               try
               {
                   process = Process.GetProcessById(processId);

                   // Write a debug message to the host that can be used
                   // when troubleshooting a problem. All debug messages
                   // will appear with the -Debug option
                   string message =
                       String.Format(CultureInfo.CurrentCulture,
                                        "Acquired process for pid : {0}",
                                            process.Id);
                   WriteDebug(message);
               }
               catch (ArgumentException ae)
               {
                   string
                       message = String.Format(CultureInfo.CurrentCulture,
                                            "The process id {0} could not be found",
                                                processId);
                   WriteVerbose(message);
                   WriteError(new ErrorRecord(ae, "ProcessIdNotFound",
                                    ErrorCategory.ObjectNotFound, processId));
                   continue;
               }

               SafeStopProcess(process);
           } // foreach (int...
       } // ProcessById

       #endregion Helper Methods

       #region Private Data

       private bool yesToAll, noToAll;

       /// <summary>
       /// Partial list of critical processes that should not be
       /// stopped.  Lower case is used for case insensitive matching.
       /// </summary>
       private ArrayList criticalProcessNames = new ArrayList(
          new string[] { "system", "winlogon", "spoolsv", "calc" }
       );

       #endregion Private Data

   } // StopProcCommand

   #endregion StopProcCommand
}
```

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
