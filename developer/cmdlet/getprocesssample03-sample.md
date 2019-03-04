---
title: GetProcessSample03 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc9d80ee-6ebd-48cd-a7ea-53cb2b442a22
caps.latest.revision: 6
ms.openlocfilehash: ec5a8c284dd3fa772261099281aba1fb68c49118
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856479"
---
# <a name="getprocesssample03-sample"></a><span data-ttu-id="dd261-102">GetProcessSample03 샘플</span><span class="sxs-lookup"><span data-stu-id="dd261-102">GetProcessSample03 Sample</span></span>

<span data-ttu-id="dd261-103">이 샘플에는 로컬 컴퓨터의 프로세스를 검색 하는 cmdlet을 구현 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="dd261-104">제공 된 `Name` 파이프라인에서 개체 또는 속성 이름이 매개 변수 이름이 동일 개체의 속성에서 값을 받아들일 수 있는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-104">It provides a `Name` parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span> <span data-ttu-id="dd261-105">이 cmdlet은의 단순화 된 버전을 `Get-Process` cmdlet은 Windows PowerShell 2.0에서 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="dd261-106">Visual Studio를 사용 하 여 샘플을 빌드하는 방법.</span><span class="sxs-lookup"><span data-stu-id="dd261-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="dd261-107">Windows PowerShell 2.0 SDK 설치를 사용 하 여 GetProcessSample03 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample03 folder.</span></span> <span data-ttu-id="dd261-108">기본 위치는 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span></span>

2. <span data-ttu-id="dd261-109">솔루션 (.sln) 파일의 아이콘을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="dd261-110">이 Visual Studio에서 샘플 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="dd261-111">에 **빌드** 메뉴에서 **솔루션 빌드**합니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="dd261-112">이 샘플에 대 한 라이브러리 기본 \bin 또는 \bin\debug 폴더에 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="dd261-113">샘플을 실행 하는 방법</span><span class="sxs-lookup"><span data-stu-id="dd261-113">How to run the sample</span></span>

1. <span data-ttu-id="dd261-114">다음 모듈 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. <span data-ttu-id="dd261-115">모듈 폴더에 샘플 어셈블리를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="dd261-116">Windows PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="dd261-117">Windows PowerShell에는 어셈블리를 로드 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample03`

5. <span data-ttu-id="dd261-118">Cmdlet을 실행 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="dd261-119">요구 사항</span><span class="sxs-lookup"><span data-stu-id="dd261-119">Requirements</span></span>

<span data-ttu-id="dd261-120">이 샘플 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="dd261-121">시연</span><span class="sxs-lookup"><span data-stu-id="dd261-121">Demonstrates</span></span>

<span data-ttu-id="dd261-122">이 샘플에는 다음 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="dd261-123">Cmdlet 특성을 사용 하는 cmdlet 클래스를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="dd261-124">매개 변수 특성을 사용 하는 cmdlet 매개 변수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="dd261-125">매개 변수의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="dd261-126">매개 변수는 파이프라인의 입력을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="dd261-127">입력 개체 또는 속성 이름이 매개 변수 이름이 동일 개체의 속성에서 값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="dd261-128">입력 매개 변수에 대 한 유효성 검사 특성을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-128">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="dd261-129">예제</span><span class="sxs-lookup"><span data-stu-id="dd261-129">Example</span></span>

<span data-ttu-id="dd261-130">이 샘플에 포함 하는 Get-proc cmdlet의 구현을 보여 줍니다는 `Name` 파이프라인에서 입력을 받는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="dd261-130">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter that accepts input from the pipeline.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;           // Windows PowerShell namespace
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
    /// Gets or sets the names of the
    /// process that the cmdlet will retrieve.
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
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to the cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames ...)
    } // End ProcessRecord.

    #endregion Overrides
  } // End GetProcCommand.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="dd261-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dd261-131">See Also</span></span>

<span data-ttu-id="dd261-132">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="dd261-132">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
