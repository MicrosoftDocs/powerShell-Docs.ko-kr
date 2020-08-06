---
title: GetProcessSample02 샘플 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: fa10774508b70f4aab4546cf4d6fbe8978032f1b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784234"
---
# <a name="getprocesssample02-sample"></a><span data-ttu-id="35958-102">GetProcessSample02 샘플</span><span class="sxs-lookup"><span data-stu-id="35958-102">GetProcessSample02 Sample</span></span>

<span data-ttu-id="35958-103">이 샘플에서는 로컬 컴퓨터의 프로세스를 검색 하는 cmdlet을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="35958-103">This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="35958-104">`Name`검색할 프로세스를 지정 하는 데 사용할 수 있는 매개 변수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="35958-104">It provides a `Name` parameter that can be used to specify the processes to be retrieved.</span></span> <span data-ttu-id="35958-105">이 cmdlet은 `Get-Process` Windows PowerShell 2.0에서 제공 되는 cmdlet의 단순화 된 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="35958-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="35958-106">Visual Studio를 사용 하 여 샘플을 빌드하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="35958-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="35958-107">Windows PowerShell 2.0 SDK가 설치 된 상태에서 GetProcessSample02 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="35958-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample02 folder.</span></span> <span data-ttu-id="35958-108">기본 위치는 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="35958-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span></span>

2. <span data-ttu-id="35958-109">솔루션 (.sln) 파일의 아이콘을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="35958-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="35958-110">그러면 Visual Studio에서 샘플 프로젝트가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="35958-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="35958-111">**빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="35958-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="35958-112">샘플에 대 한 라이브러리는 기본 \bin 또는 \bin\debug 폴더에 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="35958-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="35958-113">샘플을 실행하는 방법</span><span class="sxs-lookup"><span data-stu-id="35958-113">How to run the sample</span></span>

1. <span data-ttu-id="35958-114">다음 모듈 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="35958-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. <span data-ttu-id="35958-115">모듈 폴더에 샘플 어셈블리를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="35958-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="35958-116">Windows PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="35958-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="35958-117">다음 명령을 실행 하 여 Windows PowerShell에 어셈블리를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="35958-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module getprossessample02`

5. <span data-ttu-id="35958-118">다음 명령을 실행 하 여 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="35958-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="35958-119">요구 사항</span><span class="sxs-lookup"><span data-stu-id="35958-119">Requirements</span></span>

<span data-ttu-id="35958-120">이 샘플에는 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="35958-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="35958-121">데모</span><span class="sxs-lookup"><span data-stu-id="35958-121">Demonstrates</span></span>

<span data-ttu-id="35958-122">이 샘플에서는 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="35958-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="35958-123">Cmdlet 특성을 사용 하 여 cmdlet 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="35958-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="35958-124">매개 변수 특성을 사용 하 여 cmdlet 매개 변수 선언</span><span class="sxs-lookup"><span data-stu-id="35958-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="35958-125">매개 변수의 위치를 지정 하는입니다.</span><span class="sxs-lookup"><span data-stu-id="35958-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="35958-126">매개 변수 입력에 대 한 유효성 검사 특성을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="35958-126">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="35958-127">예제</span><span class="sxs-lookup"><span data-stu-id="35958-127">Example</span></span>

<span data-ttu-id="35958-128">이 샘플에서는 매개 변수를 포함 하는 Get Proc cmdlet의 구현을 보여 줍니다 `Name` .</span><span class="sxs-lookup"><span data-stu-id="35958-128">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
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
    /// associated process objects to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="35958-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="35958-129">See Also</span></span>

[<span data-ttu-id="35958-130">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="35958-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
