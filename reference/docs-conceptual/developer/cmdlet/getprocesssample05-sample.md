---
ms.date: 09/13/2016
ms.topic: reference
title: GetProcessSample05 샘플
description: GetProcessSample05 샘플
ms.openlocfilehash: d4bfaf52b00bb68cf11d8bbebf72487472d73f6e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646518"
---
# <a name="getprocesssample05-sample"></a><span data-ttu-id="86a40-103">GetProcessSample05 샘플</span><span class="sxs-lookup"><span data-stu-id="86a40-103">GetProcessSample05 Sample</span></span>

<span data-ttu-id="86a40-104">이 샘플에서는 Get-Proc cmdlet의 전체 버전을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-104">This sample shows a complete version of the Get-Proc cmdlet.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="86a40-105">Visual Studio를 사용 하 여 샘플을 빌드하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-105">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="86a40-106">Windows 탐색기를 열고 Samples 디렉터리 아래의 GetProcessSample05 디렉터리로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-106">Open Windows Explorer and navigate to the GetProcessSample05 directory under the Samples directory.</span></span>

   <span data-ttu-id="86a40-107">Windows PowerShell 2.0 SDK가 설치 된 상태에서 GetProcessSample05 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample05 folder.</span></span> <span data-ttu-id="86a40-108">기본 위치는 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample05.</span><span class="sxs-lookup"><span data-stu-id="86a40-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample05.</span></span>

2. <span data-ttu-id="86a40-109">솔루션 (.sln) 파일의 아이콘을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="86a40-110">그러면 Visual Studio에서 샘플 프로젝트가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="86a40-111">**빌드** 메뉴에서 **솔루션 빌드** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-111">In the **Build** menu, select **Build Solution**.</span></span>

   <span data-ttu-id="86a40-112">샘플에 대 한 라이브러리는 기본 \bin 또는 \bin\debug 디렉터리에 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-112">The library for the sample will be built in the default \bin or \bin\debug directories.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="86a40-113">샘플을 실행하는 방법</span><span class="sxs-lookup"><span data-stu-id="86a40-113">How to run the sample</span></span>

1. <span data-ttu-id="86a40-114">다음 모듈 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-114">Create the following module folder:</span></span>

   `[user]/documents/windowspowershell/modules/GetProcessSample05`

2. <span data-ttu-id="86a40-115">모듈 폴더에 샘플 어셈블리를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="86a40-116">Windows PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="86a40-117">다음 명령을 실행 하 여 Windows PowerShell에 어셈블리를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

   `Import-module getprossessample05`

5. <span data-ttu-id="86a40-118">다음 명령을 실행 하 여 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-118">Run the following command to run the cmdlet:</span></span>

   `get-proc`

## <a name="requirements"></a><span data-ttu-id="86a40-119">요구 사항</span><span class="sxs-lookup"><span data-stu-id="86a40-119">Requirements</span></span>

<span data-ttu-id="86a40-120">이 샘플에는 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="86a40-121">데모</span><span class="sxs-lookup"><span data-stu-id="86a40-121">Demonstrates</span></span>

<span data-ttu-id="86a40-122">이 샘플에서는 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="86a40-123">Cmdlet 특성을 사용 하 여 cmdlet 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="86a40-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="86a40-124">매개 변수 특성을 사용 하 여 cmdlet 매개 변수 선언</span><span class="sxs-lookup"><span data-stu-id="86a40-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="86a40-125">매개 변수의 위치 지정</span><span class="sxs-lookup"><span data-stu-id="86a40-125">Specifying positions for parameters.</span></span>

- <span data-ttu-id="86a40-126">해당 매개 변수를 지정 하면 파이프라인에서 입력을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-126">Specifying that parameters can take input from the pipeline.</span></span> <span data-ttu-id="86a40-127">입력은 개체 또는 속성 이름이 매개 변수 이름과 동일한 개체의 속성에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="86a40-128">매개 변수 입력에 대 한 유효성 검사 특성을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-128">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="86a40-129">오류 및 예외 처리</span><span class="sxs-lookup"><span data-stu-id="86a40-129">Handling errors and exceptions.</span></span>

- <span data-ttu-id="86a40-130">디버그 메시지를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-130">Writing debug messages.</span></span>

## <a name="example"></a><span data-ttu-id="86a40-131">예제</span><span class="sxs-lookup"><span data-stu-id="86a40-131">Example</span></span>

<span data-ttu-id="86a40-132">이 샘플에서는 지정 된 프로세스 목록을 표시 하는 cmdlet을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="86a40-132">This sample shows how to create a cmdlet that displays a list of specified processes.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Collections.Generic;
    using System.Diagnostics;
    using System.Management.Automation;    // Windows PowerShell namespace.
    using System.Security.Permissions;
    using Win32Exception = System.ComponentModel.Win32Exception;
    #region GetProcCommand

    /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc",
      DefaultParameterSetName = "ProcessName")]
   public class GetProcCommand : PSCmdlet
   {
       #region Fields
       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

       /// <summary>
       /// The identifiers of the processes to act on.
       /// </summary>
       private int[] processIds;

       /// <summary>
       /// The process objects to act on.
       /// </summary>
       private Process[] inputObjects;

       #endregion Fields

       #region Parameters

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ParameterSetName = "ProcessName",
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
      [ValidateNotNullOrEmpty]
      public string[] Name
      {
         get { return this.processNames; }
         set { this.processNames = value; }
      }

      /// <summary>
      /// Gets or sets the list of process identifiers on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         ParameterSetName = "Id",
         Mandatory = true,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true,
         HelpMessage = "The unique id of the process to get.")]
      public int[] Id
      {
         get { return this.processIds; }
         set { this.processIds = value; }
      }

      /// <summary>
      /// Gets or sets Process objects directly. If the input is a
      /// stream of [collection of] Process objects, the cmdlet bypasses the
      /// ProcessName and Id parameters and reads the Process objects
      /// directly.  This allows the cmdlet to deal with processes that have
      /// wildcard characters in their name.
      /// <value>Process objects</value>
      /// </summary>
      [Parameter(
         ParameterSetName = "InputObject",
         Mandatory = true,
         ValueFromPipeline = true)]
      public Process[] Input
      {
         get { return this.inputObjects; }
         set { this.inputObjects = value; }
      }

      #endregion Parameters

      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes. Then, the WriteObject
      /// method writes the associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         List<Process> matchingProcesses;

         WriteDebug("Obtaining the list of matching process objects.");

         switch (ParameterSetName)
         {
            case "Id":
               matchingProcesses = this.GetMatchingProcessesById();
               break;
            case "ProcessName":
               matchingProcesses = this.GetMatchingProcessesByName();
               break;
            case "InputObject":
               matchingProcesses = this.GetProcessesByInput();
               break;
            default:
               ThrowTerminatingError(
                   new ErrorRecord(
                       new ArgumentException("Bad ParameterSetName"),
                       "UnableToAccessProcessList",
                       ErrorCategory.InvalidOperation,
                       null));
               return;
         } // switch (ParameterSetName)

         WriteDebug("Outputting the matching process objects.");

         matchingProcesses.Sort(ProcessComparison);

         foreach (Process process in matchingProcesses)
         {
            WriteObject(process);
         }
      } // ProcessRecord

      #endregion Overrides

      #region protected Methods and Data

      /// <summary>
      /// Retrieves the list of all processes matching the ProcessName
      /// parameter and generates a nonterminating error for each
      /// specified process name which is not found even though the name
      /// contains no wildcards.
      /// </summary>
      /// <returns>The matching processes.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetMatchingProcessesByName()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> allProcesses =
            new List<Process>(Process.GetProcesses());

         // The keys dictionary is used for rapid lookup of
         // processes that are already in the matchingProcesses list.
         Dictionary<int, byte> keys = new Dictionary<int, byte>();

         List<Process> matchingProcesses = new List<Process>();

         if (null == this.processNames)
         {
             matchingProcesses.AddRange(allProcesses);
         }
         else
         {
             foreach (string pattern in this.processNames)
             {
                 WriteVerbose("Finding matches for process name \""
                    + pattern + "\".");

                 // WildCard search on the available processes
                 WildcardPattern wildcard =
                    new WildcardPattern(
                        pattern,
                        WildcardOptions.IgnoreCase);

                 bool found = false;

                 foreach (Process process in allProcesses)
                 {
                     if (!keys.ContainsKey(process.Id))
                     {
                         string processName = SafeGetProcessName(process);

                         // Remove the process from the allProcesses list
                         // so that it is not tested again.
                         if (processName.Length == 0)
                         {
                             allProcesses.Remove(process);
                         }

                         // Perform a wildcard search on this particular
                         // process name and check whether it matches the
                         // pattern specified.
                         if (!wildcard.IsMatch(processName))
                         {
                             continue;
                         }

                         WriteDebug("Found matching process id "
                            + process.Id + ".");

                         // A match is found.
                         found = true;

                         // Store the process identifier so that the same process
                         // is not added twice.
                         keys.Add(process.Id, 0);

                         // Add the process to the processes list.
                         matchingProcesses.Add(process);
                     }
                 } // foreach (Process...

                 if (!found &&
                   !WildcardPattern.ContainsWildcardCharacters(pattern))
                 {
                     WriteError(new ErrorRecord(
                        new ArgumentException("Cannot find process name "
                           + "\"" + pattern + "\"."),
                        "ProcessNameNotFound",
                        ErrorCategory.ObjectNotFound,
                        pattern));
                 }
             } // foreach (string...
         } // if (null...

         return matchingProcesses;
      } // GetMatchingProcessesByName

      /// <summary>
      /// Returns the name of a process.  If an error occurs, a blank
      /// string is returned.
      /// </summary>
      /// <param name="process">The process whose name is
      /// returned.</param>
      /// <returns>The name of the process.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand, Unrestricted = true)]
      protected static string SafeGetProcessName(Process process)
      {
         new EnvironmentPermission(PermissionState.Unrestricted).Assert();
         string name = String.Empty;

         if (process != null)
         {
            try
            {
                return process.ProcessName;
            }
            catch (Win32Exception)
            {
            }
            catch (InvalidOperationException)
            {
            }
         }

         return name;
     } // SafeGetProcessName

      #endregion Cmdlet Overrides

      #region Private Methods

      /// <summary>
      /// Function to sort by process name first, and then by
      /// the process identifier.
      /// </summary>
      /// <param name="x">First process object.</param>
      /// <param name="y">Second process object.</param>
      /// <returns>
      /// Returns less than zero if x is less than y,
      /// greater than 0 if x is greater than y, and 0 if x == y.
      /// </returns>
      private static int ProcessComparison(Process x, Process y)
      {
         int diff = String.Compare(
            SafeGetProcessName(x),
            SafeGetProcessName(y),
            StringComparison.CurrentCultureIgnoreCase);

         if (0 != diff)
         {
             return diff;
         }
         else
         {
             return x.Id.CompareTo(y.Id);
         }
      }

      /// <summary>
      /// Retrieves the list of all processes matching the Id
      /// parameter and generates a nonterminating error for
      /// each specified process identifier which is not found.
      /// </summary>
      /// <returns>
      /// An array of processes that match the given identifier.
      /// </returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetMatchingProcessesById()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> matchingProcesses = new List<Process>();

         if (null != this.processIds)
         {
            // The keys dictionary is used for rapid lookup of the
            // processes already in the matchingProcesses list.
            Dictionary<int, byte> keys = new Dictionary<int, byte>();

            foreach (int processId in this.processIds)
            {
               WriteVerbose("Finding match for process id "
                  + processId + ".");

               if (!keys.ContainsKey(processId))
               {
                  Process process;
                  try
                  {
                      process = Process.GetProcessById(processId);
                  }
                  catch (ArgumentException ex)
                  {
                     WriteError(new ErrorRecord(
                        ex,
                        "ProcessIdNotFound",
                        ErrorCategory.ObjectNotFound,
                        processId));
                     continue;
                  }

                  WriteDebug("Found matching process.");

                  matchingProcesses.Add(process);
                  keys.Add(processId, 0);
               }
            }
         }

         return matchingProcesses;
      } // GetMatchingProcessesById

      /// <summary>
      /// Retrieves the list of all processes matching the InputObject
      /// parameter.
      /// </summary>
      /// <returns>The matching processes.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetProcessesByInput()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> matchingProcesses = new List<Process>();

         if (null != this.Input)
         {
            // The keys dictionary is used for rapid lookup of the
            // processes already in the matchingProcesses list.
            Dictionary<int, byte> keys = new Dictionary<int, byte>();

            foreach (Process process in this.Input)
            {
               WriteVerbose("Refreshing process object.");

               if (!keys.ContainsKey(process.Id))
               {
                  try
                  {
                      process.Refresh();
                  }
                  catch (Win32Exception)
                  {
                  }
                  catch (InvalidOperationException)
                  {
                  }

                  matchingProcesses.Add(process);
               }
            }
         }

         return matchingProcesses;
      } // GetProcessesByInput
      #endregion Private Methods
    } // End GetProcCommand class.

    #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="86a40-133">관련 항목</span><span class="sxs-lookup"><span data-stu-id="86a40-133">See Also</span></span>

[<span data-ttu-id="86a40-134">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="86a40-134">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
