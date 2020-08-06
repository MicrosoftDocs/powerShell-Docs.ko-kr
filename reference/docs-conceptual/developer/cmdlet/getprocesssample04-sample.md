---
title: GetProcessSample04 샘플 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4858c44302f7315625be02dd0dc1d335b9c3f158
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774425"
---
# <a name="getprocesssample04-sample"></a><span data-ttu-id="ed46e-102">GetProcessSample04 샘플</span><span class="sxs-lookup"><span data-stu-id="ed46e-102">GetProcessSample04 Sample</span></span>

<span data-ttu-id="ed46e-103">이 샘플에서는 로컬 컴퓨터의 프로세스를 검색 하는 cmdlet을 구현 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="ed46e-104">프로세스를 검색 하는 동안 오류가 발생 하는 경우 종료 되지 않는 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-104">It generates a nonterminating error if an error occurs while retrieving a process.</span></span> <span data-ttu-id="ed46e-105">이 cmdlet은 `Get-Process` Windows PowerShell 2.0에서 제공 되는 cmdlet의 단순화 된 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="ed46e-106">Visual Studio를 사용 하 여 샘플을 빌드하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="ed46e-107">Windows PowerShell 2.0 SDK가 설치 된 상태에서 GetProcessSample04 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample04 folder.</span></span> <span data-ttu-id="ed46e-108">기본 위치는 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="ed46e-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span></span>

2. <span data-ttu-id="ed46e-109">솔루션 (.sln) 파일의 아이콘을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="ed46e-110">그러면 Visual Studio에서 샘플 프로젝트가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="ed46e-111">**빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="ed46e-112">샘플에 대 한 라이브러리는 기본 \bin 또는 \bin\debug 폴더에 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="ed46e-113">샘플을 실행하는 방법</span><span class="sxs-lookup"><span data-stu-id="ed46e-113">How to run the sample</span></span>

1. <span data-ttu-id="ed46e-114">다음 모듈 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. <span data-ttu-id="ed46e-115">모듈 폴더에 샘플 어셈블리를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="ed46e-116">Windows PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="ed46e-117">다음 명령을 실행 하 여 Windows PowerShell에 어셈블리를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample04`

5. <span data-ttu-id="ed46e-118">다음 명령을 실행 하 여 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="ed46e-119">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ed46e-119">Requirements</span></span>

<span data-ttu-id="ed46e-120">이 샘플에는 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ed46e-121">데모</span><span class="sxs-lookup"><span data-stu-id="ed46e-121">Demonstrates</span></span>

<span data-ttu-id="ed46e-122">이 샘플에서는 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="ed46e-123">Cmdlet 특성을 사용 하 여 cmdlet 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="ed46e-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="ed46e-124">매개 변수 특성을 사용 하 여 cmdlet 매개 변수 선언</span><span class="sxs-lookup"><span data-stu-id="ed46e-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="ed46e-125">매개 변수의 위치를 지정 하는입니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="ed46e-126">매개 변수가 파이프라인의 입력을 사용 하도록 지정 하는입니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="ed46e-127">입력은 개체 또는 속성 이름이 매개 변수 이름과 동일한 개체의 속성에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="ed46e-128">매개 변수 입력에 대 한 유효성 검사 특성을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-128">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="ed46e-129">종료 되지 않는 오류를 트래핑 하 고 오류 메시지를 오류 스트림에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-129">Trapping a nonterminating error and writing an error message to the error stream.</span></span>

## <a name="example"></a><span data-ttu-id="ed46e-130">예제</span><span class="sxs-lookup"><span data-stu-id="ed46e-130">Example</span></span>

<span data-ttu-id="ed46e-131">이 샘플에서는 종료 되지 않는 오류를 처리 하 고 오류 메시지를 오류 스트림에 쓰는 cmdlet을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ed46e-131">This sample shows how to create a cmdlet that handles nonterminating errors and writes error messages to the error stream.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ed46e-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ed46e-132">See Also</span></span>

[<span data-ttu-id="ed46e-133">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="ed46e-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
