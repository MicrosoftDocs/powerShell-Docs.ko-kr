---
ms.date: 03/09/2021
ms.topic: reference
title: 작업을 지원하는 방법
description: 작업을 지원하는 방법
ms.openlocfilehash: 1528f5d934605caa4009688845a6caa7b95b86a3
ms.sourcegitcommit: e679533f966f4e97cddae24531a22436da13610c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102532121"
---
# <a name="how-to-support-jobs"></a>작업을 지원하는 방법

이 예제에서는 cmdlet을 작성할 때 작업을 지 원하는 방법을 보여 줍니다. 사용자가 cmdlet을 백그라운드 작업으로 실행 하려면 다음 절차에 설명 된 코드를 포함 해야 합니다. 백그라운드 작업에 대 한 자세한 내용은 [백그라운드 작업](./background-jobs.md)을 참조 하세요.

## <a name="to-support-jobs"></a>작업을 지원 하려면

1. `AsJob`사용자가 cmdlet을 작업으로 실행할지 여부를 결정할 수 있도록 스위치 매개 변수를 정의 합니다.

    다음 예제에서는 AsJob 매개 변수 선언을 보여 줍니다.

    ```csharp
    [Parameter()]
    public SwitchParameter AsJob
    {
      get { return asjob; }
      set { asjob = value; }
    }
    private bool asjob;
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06AsJobParam](msh_samplesGetProc06#GetProc06AsJobParam)]  -->

1. [System.object](/dotnet/api/System.Management.Automation.Job) 클래스에서 파생 되는 개체를 만듭니다. 이 개체는 사용자 지정 작업 개체 이거나 Windows PowerShell에서 제공 하는 작업 개체 (예: [Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) 개체) 중 하나일 수 있습니다.

    다음 예제에서는 사용자 지정 작업 개체를 보여 줍니다.

    ```csharp
    private SampleJob job = new SampleJob("Get-ProcAsJob");
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06JobObject](msh_samplesGetProc06#GetProc06JobObject)]  -->

1. 레코드 처리 방법에서 `if` 문을 추가 하 여 cmdlet을 작업으로 실행할지 여부를 검색 합니다. 다음 코드는 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 사용 합니다.

    ```csharp
    protected override void ProcessRecord()
    {
      if (asjob)
      {
        // Add the job definition to the job repository,
        // return the job object, and then create the thread
        // used to run the job.
        JobRepository.Add(job);
        WriteObject(job);
        ThreadPool.QueueUserWorkItem(WorkItem);
      }
      else
      {
        job.ProcessJob();
        foreach (PSObject p in job.Output)
        {
          WriteObject(p);
        }
      }
    }
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06ProcessRecord](msh_samplesGetProc06#GetProc06ProcessRecord)]  -->

1. 사용자 지정 작업 개체의 경우 작업 클래스를 구현 합니다.

    ```csharp
    private class SampleJob : Job
    {
      internal SampleJob(string command)
          : base(command)
      {
        SetJobState(JobState.NotStarted);
      }
      public override string StatusMessage
      {
        get { throw new NotImplementedException(); }
      }

      public override bool HasMoreData
      {
        get
        {
          return hasMoreData;
        }
      }
      private bool hasMoreData = true;

      public override string Location
      {
        get { throw new NotImplementedException(); }
      }

      public override void StopJob()
      {
        throw new NotImplementedException();
      }

      internal void ProcessJob()
      {
        SetJobState(JobState.Running);
        DoProcessLogic();
        SetJobState(JobState.Completed);
      }

      // Retrieve the processes of the local computer.
      void DoProcessLogic()
      {
        Process[] p = Process.GetProcesses();

        foreach (Process pl in p)
        {
          Output.Add(PSObject.AsPSObject(pl));
        }
        Output.Complete();
      } // End DoProcessLogic.
    } // End SampleJob class.
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06JobClass](msh_samplesGetProc06#GetProc06JobClass)]  -->

1. Cmdlet에서 작업을 수행 하는 경우 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드를 호출 하 여 프로세스 개체를 파이프라인으로 반환 합니다. 작업이 작업으로 수행 되는 경우 자식 작업을 작업에 추가 합니다.

    ```csharp
    void DoProcessLogic(bool asJob)
    {
      Process[] p = Process.GetProcesses();

      foreach (Process pl in p)
      {
        if (!asjob)
        {
          WriteObject(pl);
        }
        else
        {
          job.ChildJobs[0].Output.Add(new PSObject(pl));
        }
      }
    } // End DoProcessLogic.
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06Output](msh_samplesGetProc06#GetProc06Output)]  -->

## <a name="example"></a>예제

다음 샘플 코드는 내부적으로 또는 백그라운드 작업을 사용 하 여 프로세스를 검색할 수 있는 **node.js cmdlet에** 대 한 코드를 보여 줍니다.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;  // Windows PowerShell namespace.
using System.Threading;              // Thread pool namespace for posting work.
using System.Diagnostics;            // Diagnostics namespace for retrieving
                                     // process objects.

// This sample shows a cmdlet whose work can be done by the cmdlet or by using
// a background job. Background jobs are executed in their own thread,
// independent of the pipeline thread in which the cmdlet is executed.
//
// To load this cmdlet, create a module folder and copy the GetProcessSample06.dll
// assembly into the module folder. Make sure that the path to the module folder
// is added to the $PSModulePath environment variable.
// Module folder path:
//    user/documents/WindowsPowerShell/modules/GetProcessSample06
//
// To import the module, run the following command: Import-Module GetProcessSample06.
// To test the cmdlet, run the following command: Get-Proc -name <process name>
//

//
namespace Microsoft.Samples.PowerShell.Commands
{
  /// <summary>
  ///  This cmdlet retrieves process internally or returns
  ///  a job that retrieves the processes.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public sealed class GetProcCommand : PSCmdlet
  {

    #region Parameters
    /// <summary>
    /// Specify the Name parameter. This parameter accepts
    /// process names from the command line.
    /// </summary>
    [Parameter(
               Position = 0,
               ValueFromPipeline = true,
               ValueFromPipelineByPropertyName = true)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return processNames; }
      set { processNames = value; }
    }
    private string[] processNames;

    /// <summary>
    /// Specify the AsJob parameter. This parameter indicates
    /// whether the cmdlet should retrieve the processes internally
    /// or return a Job object that retrieves the processes.
    /// </summary>
    [Parameter()]
    public SwitchParameter AsJob
    {
      get { return asjob; }
      set { asjob = value; }
    }
    private bool asjob;

    #endregion Parameters

    #region Cmdlet Overrides

    // Create a custom job object.
    private SampleJob job = new SampleJob("Get-ProcAsJob");

    /// <summary>
    /// Determines if the processes should be retrieved
    /// internally or if a Job object should be returned.
    /// </summary>
    protected override void ProcessRecord()
    {
      if (asjob)
      {
        // Add the job definition to the job repository,
        // return the job object, and then create the thread
        // used to run the job.
        JobRepository.Add(job);
        WriteObject(job);
        ThreadPool.QueueUserWorkItem(WorkItem);
      }
      else
      {
        job.ProcessJob();
        foreach (PSObject p in job.Output)
        {
          WriteObject(p);
        }
      }
    }
    #endregion Overrides

    // Implement a custom job that derives
    // from the System.Management.Automation.Job class.
    private class SampleJob : Job
    {
      internal SampleJob(string command)
          : base(command)
      {
        SetJobState(JobState.NotStarted);
      }
      public override string StatusMessage
      {
        get { throw new NotImplementedException(); }
      }

      public override bool HasMoreData
      {
        get
        {
          return hasMoreData;
        }
      }
      private bool hasMoreData = true;

      public override string Location
      {
        get { throw new NotImplementedException(); }
      }

      public override void StopJob()
      {
        throw new NotImplementedException();
      }

      internal void ProcessJob()
      {
        SetJobState(JobState.Running);
        DoProcessLogic();
        SetJobState(JobState.Completed);
      }

      // Retrieve the processes of the local computer.
      void DoProcessLogic()
      {
        Process[] p = Process.GetProcesses();

        foreach (Process pl in p)
        {
          Output.Add(PSObject.AsPSObject(pl));
        }
        Output.Complete();
      } // End DoProcessLogic.
    } // End SampleJob class.

    void WorkItem(object dummy)
    {
       job.ProcessJob();
    }

    // Display the results of the work. If not a job,
    // process objects are returned. If a job, the
    // output is added to the job as a child job.
    void DoProcessLogic(bool asJob)
    {
      Process[] p = Process.GetProcesses();

      foreach (Process pl in p)
      {
        if (!asjob)
        {
          WriteObject(pl);
        }
        else
        {
          job.ChildJobs[0].Output.Add(new PSObject(pl));
        }
      }
    } // End DoProcessLogic.
  } //End GetProcCommand
}
```

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesGetProc06#GetProc06All](msh_samplesGetProc06#GetProc06All)]  -->
