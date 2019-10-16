---
title: Windows PowerShell API를 사용 하 여 작업 예약 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64718f8e-de60-4fb7-894d-2975b5257ff6
caps.latest.revision: 4
ms.openlocfilehash: bdced961d91088dd75be347b7b74b22467c8c9be
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366022"
---
# <a name="scheduling-jobs-with-the-powershell-api"></a><span data-ttu-id="1e418-102">PowerShell API를 사용 하 여 작업 예약</span><span class="sxs-lookup"><span data-stu-id="1e418-102">Scheduling jobs with the PowerShell API</span></span>

<span data-ttu-id="1e418-103">**Set-scheduledjob** 네임 스페이스에서 노출 하는 개체를 사용 하 여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-103">You can use the objects exposed by the **Microsoft.PowerShell.ScheduledJob** namespace to do the following:</span></span>

- <span data-ttu-id="1e418-104">예약 된 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-104">Create a scheduled job.</span></span>
- <span data-ttu-id="1e418-105">작업이 실행 되는 시간을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-105">Define when the job runs.</span></span>
- <span data-ttu-id="1e418-106">완료 된 작업에 대 한 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-106">Get results about the completed job.</span></span>

## <a name="triggering-the-job"></a><span data-ttu-id="1e418-107">작업 트리거</span><span class="sxs-lookup"><span data-stu-id="1e418-107">Triggering the job</span></span>

<span data-ttu-id="1e418-108">예약 된 작업을 만드는 첫 번째 단계는 작업을 실행할 시기를 지정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-108">The first step in creating a scheduled job is specifying when the job should run.</span></span> <span data-ttu-id="1e418-109">**Set-scheduledjob ScheduledJobTrigger** 개체를 만들고 구성 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-109">Do this by creating and configuring a **Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger** object.</span></span> <span data-ttu-id="1e418-110">다음 코드는 나중에 20 초 후에 한 번 실행 되도록 작업을 예약 하는 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-110">The following code creates a trigger that schedules a job to run a single time 20 seconds in the future.</span></span>

```csharp
ScheduledJobTrigger jobTrigger = ScheduledJobTrigger.CreateOnceTrigger(
                    DateTime.Now.AddSeconds(20), // Create trigger to start job in 20 seconds.
                    TimeSpan.Zero,               // No random delay
                    null,                        // No repetition interval time
                    null,                        // No repetition interval duration
                    1,                           // Trigger Id
                    true);                       // Create trigger enabled

```

## <a name="defining-the-job"></a><span data-ttu-id="1e418-111">작업 정의</span><span class="sxs-lookup"><span data-stu-id="1e418-111">Defining the job</span></span>

<span data-ttu-id="1e418-112">매개 변수 사전을 만들어 PowerShell 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-112">You define a PowerShell job by creating a parameter dictionary.</span></span> <span data-ttu-id="1e418-113">지원 되는 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-113">The following parameters are supported:</span></span>

|<span data-ttu-id="1e418-114">매개 변수 이름</span><span class="sxs-lookup"><span data-stu-id="1e418-114">Parameter Name</span></span>|<span data-ttu-id="1e418-115">설명</span><span class="sxs-lookup"><span data-stu-id="1e418-115">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="1e418-116">**이름의**</span><span class="sxs-lookup"><span data-stu-id="1e418-116">**Name**</span></span>|<span data-ttu-id="1e418-117">작업의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-117">The name of the job.</span></span>|
|<span data-ttu-id="1e418-118">**ScriptBock**</span><span class="sxs-lookup"><span data-stu-id="1e418-118">**ScriptBock**</span></span>|<span data-ttu-id="1e418-119">작업에서 수행 하는 작업을 지정 하는 PowerShell 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-119">A PowerShell script block that specifies what the job does.</span></span>|
|<span data-ttu-id="1e418-120">**Null**</span><span class="sxs-lookup"><span data-stu-id="1e418-120">**FilePath**</span></span>|<span data-ttu-id="1e418-121">작업에서 수행 하는 작업을 지정 하는 PowerShell 스크립트 블록을 포함 하는 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-121">Path to a file that contains a PowerShell script block to specify what the job does.</span></span>|
|<span data-ttu-id="1e418-122">**또한 initializationscript**</span><span class="sxs-lookup"><span data-stu-id="1e418-122">**InitializationScript**</span></span>|<span data-ttu-id="1e418-123">작업을 초기화 하는 PowerShell 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-123">A PowerShell script block that initializes the job.</span></span>|
|<span data-ttu-id="1e418-124">**ArgumentList**</span><span class="sxs-lookup"><span data-stu-id="1e418-124">**ArgumentList**</span></span>|<span data-ttu-id="1e418-125">작업에서 수행 하는 인수를 지정 하는 개체의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-125">An array of objects that specify arguments that the job takes.</span></span>|
|<span data-ttu-id="1e418-126">**체제가 있어도 runas32**</span><span class="sxs-lookup"><span data-stu-id="1e418-126">**RunAs32**</span></span>|<span data-ttu-id="1e418-127">작업을 32 비트 프로세스로 실행할지 여부를 지정 하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-127">A boolean value that specifies whether to run the job in a 32-bit process.</span></span>|

<span data-ttu-id="1e418-128">다음 코드는 매개 변수 사전 개체를 만들고 **Name** 및 **ScriptBlock** 매개 변수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-128">The following code creates a parameter dictionary object and sets the **Name** and **ScriptBlock** parameters.</span></span>

```csharp
string schedJobDefName = "MySampleSchedJob";
  Dictionary<string, object> jobDefParameters = new Dictionary<string, object>();
  jobDefParameters.Add("Name", schedJobDefName);      // Unique name is required.

  ScriptBlock scriptBlock = ScriptBlock.Create(@"1..5 | foreach {sleep 1; ""SchedJobOutput $_""}");
  jobDefParameters.Add("ScriptBlock", scriptBlock);  // A scriptblock or script FilePath
                                                    // is required.

```

## <a name="creating-the-invocation-and-job-definition-objects"></a><span data-ttu-id="1e418-129">호출 및 작업 정의 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="1e418-129">Creating the invocation and job definition objects</span></span>

<span data-ttu-id="1e418-130">그런 다음 `ScheduledJobInvocationInfo` 및 `ScheduledJobDefinition` 개체를 만들어 다음 예제와 같이 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-130">You then create `ScheduledJobInvocationInfo` and `ScheduledJobDefinition` objects to run the job as shown in the following example:</span></span>

```csharp
ScheduledJobInvocationInfo jobInvocationInfo = new ScheduledJobInvocationInfo(
    new JobDefinition(typeof(ScheduledJobSourceAdapter), scriptBlock.ToString(), schedJobDefName),
    jobDefParameters);

    schedJobDefinition = new ScheduledJobDefinition(
    jobInvocationInfo,                          // Defines the PowerShell job to run.
    new ScheduledJobTrigger[1] { jobTrigger },  // Defines when to run the PowerShell job.
    null,                                       // No custom options. We accept default.
    null);                                      // No credentials. PowerShell job is run
                                                // in default Task Scheduler process, account.

```

## <a name="registering-the-job-with-the-task-scheduler"></a><span data-ttu-id="1e418-131">작업 스케줄러에 작업 등록</span><span class="sxs-lookup"><span data-stu-id="1e418-131">Registering the job with the task scheduler</span></span>

<span data-ttu-id="1e418-132">다음 코드는 작업을 [Windows 작업 스케줄러](https://go.microsoft.com/fwlink/?LinkId=251817)에 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-132">The following code registers the job with the [Windows Task Scheduler](https://go.microsoft.com/fwlink/?LinkId=251817).</span></span>

```csharp
schedJobDefinition.Register();
    registrationSucceeded = true;
    Console.WriteLine("Scheduled job is registered. Waiting 30 seconds for it to run.");

```

## <a name="complete-code-example"></a><span data-ttu-id="1e418-133">전체 코드 예제</span><span class="sxs-lookup"><span data-stu-id="1e418-133">Complete code Example</span></span>

<span data-ttu-id="1e418-134">다음은 이전 코드 조각이 만들어진 전체 코드 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="1e418-134">The following is the complete code example from which the previous snippets were taken.</span></span>

```csharp
using System;
using System.Threading;
using System.Collections.Generic;
using System.Management.Automation;             // PowerShell namespace.
using Microsoft.PowerShell.ScheduledJob;        // PowerShell ScheduledJob namespace.

namespace Microsoft.Samples.PowerShell.ScheduledJob
{
    /// <summary>
    /// This class contains the Main entry point for the application.
    /// </summary>
    public class ScheduledJobSample
    {
        /// <summary>
        /// This sample shows how to use the PowerShell ScheduledJob API to create
        /// a simple PowerShell scheduled job, register it with a trigger object
        /// that defines when the job will run and retrieve job run results from
        /// the job file store.
        /// </summary>
        /// <param name="args"></param>
        public static void Main(string[] args)
        {
            // ScheduledJobDefinition contains all elements of a PowerShell scheduled
            // job including the PowerShell job script or script file path, scheduling
            // triggers, and scheduling options.
            ScheduledJobDefinition schedJobDefinition = null;
            bool registrationSucceeded = false;

            try
            {
                // First create a scheduled job trigger object.  This object will
                // define when the PowerShell job is scheduled to run.  For this
                // example we will create a trigger to run the job just one time
                // 20 seconds after the trigger object is created.
                // Note: If you are stepping through this code in a debugger you
                // may want to increase the 20 seconds value so that the trigger time
                // remains in the future once you register the scheduled job.
                ScheduledJobTrigger jobTrigger = ScheduledJobTrigger.CreateOnceTrigger(
                    DateTime.Now.AddSeconds(20),      // Create trigger to start job in 20 seconds.
                    TimeSpan.Zero,                    // No random delay
                    null,                             // No repetition interval time
                    null,                             // No repetition interval duration
                    1,                                // Trigger Id
                    true);                            // Create trigger enabled

                // Create a parameter dictionary that defines the PowerShell job.
                // For this example we will create a simple script that runs for
                // 5 seconds generating output.
                // Here are the parameters supported to define the PowerShell job.
                // Name                 - Job name string.
                // ScriptBlock          - PowerShell ScriptBlock type.
                // FilePath             - PowerShell script file path string.
                // InitializationScript - PowerShell Scriptblock type.
                // ArgumentList         - object[] type.
                // RunAs32              - Switch (boolean type).
                string schedJobDefName = "MySampleSchedJob";
                Dictionary<string, object> jobDefParameters = new Dictionary<string, object>();
                jobDefParameters.Add("Name", schedJobDefName);      // Unique name is required.

                ScriptBlock scriptBlock = ScriptBlock.Create(@"1..5 | foreach {sleep 1; ""SchedJobOutput $_""}");
                jobDefParameters.Add("ScriptBlock", scriptBlock);  // A scriptblock or script FilePath is required.

                // Now create a JobInvocation object that contains all information about the PowerShell job to run.
                ScheduledJobInvocationInfo jobInvocationInfo = new ScheduledJobInvocationInfo(
                    new JobDefinition(typeof(ScheduledJobSourceAdapter), scriptBlock.ToString(), schedJobDefName),
                    jobDefParameters);

                // Finally create the scheduled job definition object that pulls all
                // of this information together.
                schedJobDefinition = new ScheduledJobDefinition(
                   jobInvocationInfo,                          // Defines the PowerShell job to run.
                   new ScheduledJobTrigger[1] { jobTrigger },  // Defines when to run the job.
                   null,                                       // No custom options. Accept default.
                   null);                                      // No credentials. PowerShell job is
                                                               // run in default Task Scheduler
                                                               // process, account.

                // Next we register this scheduled job object with Windows Task Scheduler.
                // The Task Scheduler runs the PowerShell script based on the provided job trigger.
                schedJobDefinition.Register();
                registrationSucceeded = true;
                Console.WriteLine("Scheduled job is registered. Waiting 30 seconds for it to run.");

                // You can see this PowerShell job task registered in the Task Scheduler UI.
                // Look under path:
                // Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs

                // Wait for Task Scheduler to run the PowerShell job.
                // This should happen in 20 seconds and then the job takes about 5 seconds to run.
                // If PowerShell job task doesn't run try increasing the trigger time in the
                // ScheduledJobTrigger object.
                // You can run this task manually from the Task Scheduler UI.
                for (int count = 1; count < 31; ++count)
                {
                    Thread.Sleep(1000);
                    Console.WriteLine(count + " seconds elapsed");
                }

                Console.WriteLine();
                Console.WriteLine("Job run results.");
                Console.WriteLine();

                // Since the PowerShell job runs in a non-interactive Task Scheduler
                // process the job status and output data is written to a file based
                // job store and the directory location is the current user local app
                // data ($env:LOCALAPPDATA).
                // This job store can be accessed through the ScheduledJobSourceAdapter class.
                ScheduledJobSourceAdapter schedJobSourceAdapter = new ScheduledJobSourceAdapter();
                IList<Job2> jobRuns = schedJobSourceAdapter.GetJobs();
                foreach (var jobRun in jobRuns)
                {
                    // Check for jobs in finished state.
                    // Note that job data is not written to the job store until the job
                    // has reached a finished state.
                    JobState jobState = jobRun.JobStateInfo.State;
                    if (jobState == JobState.Completed ||
                        jobState == JobState.Stopped ||
                        jobState == JobState.Failed)
                    {
                        // Write job run finished state.
                        Console.WriteLine("Job Status: " + jobRun.JobStateInfo.State);
                        Console.WriteLine();
                        Console.WriteLine("Job Data");

                        // Write output data.
                        foreach (var item in jobRun.Output)
                        {
                            Console.WriteLine(item.ToString());
                        }

                        // Write any errors.
                        foreach (var item in jobRun.Error)
                        {
                            Console.WriteLine(item.ToString());
                        }
                    }
                }

                Console.WriteLine();
                Console.WriteLine("Press any key to continue...");
                Console.ReadKey();
            }
            catch (ScheduledJobException e)
            {
                Console.WriteLine("Error: " + e.Message);
            }
            finally
            {
                // Unregister this scheduled job or an error will be thrown when
                // running this sample code again (scheduled job already exists.)
                // because all registered scheduled jobs must have a unique name.
                if (registrationSucceeded)
                {
                    schedJobDefinition.Remove(true);
                }
            }
        }
    }
}

```
