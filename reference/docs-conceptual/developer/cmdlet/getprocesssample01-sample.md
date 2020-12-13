---
ms.date: 09/13/2016
ms.topic: reference
title: GetProcessSample01 샘플
description: GetProcessSample01 샘플
ms.openlocfilehash: 159c277d17a8551d2b5c52377a230babacafc9ab
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652761"
---
# <a name="getprocesssample01-sample"></a><span data-ttu-id="11ab9-103">GetProcessSample01 샘플</span><span class="sxs-lookup"><span data-stu-id="11ab9-103">GetProcessSample01 Sample</span></span>

<span data-ttu-id="11ab9-104">이 샘플에서는 로컬 컴퓨터의 프로세스를 검색 하는 cmdlet을 구현 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-104">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="11ab9-105">이 cmdlet은 `Get-Process` Windows PowerShell 2.0에서 제공 하는 cmdlet의 단순화 된 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-105">This cmdlet is a simplified version of the `Get-Process` cmdlet that is provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="11ab9-106">Visual Studio를 사용 하 여 샘플을 빌드하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="11ab9-107">Windows PowerShell 2.0 SDK가 설치 된 상태에서 GetProcessSample01 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample01 folder.</span></span> <span data-ttu-id="11ab9-108">기본 위치는 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="11ab9-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span></span>

2. <span data-ttu-id="11ab9-109">솔루션 (.sln) 파일의 아이콘을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="11ab9-110">그러면 Microsoft Visual Studio의 샘플 프로젝트가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="11ab9-111">**빌드** 메뉴에서 **솔루션 빌드** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-111">In the **Build** menu, select **Build Solution**.</span></span>

  <span data-ttu-id="11ab9-112">샘플에 대 한 라이브러리는 기본 \bin 또는 \bin\debug 폴더에 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="11ab9-113">샘플을 실행하는 방법</span><span class="sxs-lookup"><span data-stu-id="11ab9-113">How to run the sample</span></span>

1. <span data-ttu-id="11ab9-114">명령 프롬프트 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-114">Open a Command Prompt window.</span></span>

2. <span data-ttu-id="11ab9-115">샘플 .dll 파일이 포함 된 디렉터리로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-115">Navigate to the directory containing the sample .dll file.</span></span>

3. <span data-ttu-id="11ab9-116">Installutil.exe "GetProcessSample01.dll"를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-116">Run installutil "GetProcessSample01.dll".</span></span>

4. <span data-ttu-id="11ab9-117">Windows PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-117">Start Windows PowerShell.</span></span>

5. <span data-ttu-id="11ab9-118">다음 명령을 실행 하 여 셸에 스냅인을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-118">Run the following command to add the snap-in to the shell.</span></span>

   `Add-PSSnapin GetProcPSSnapIn01`

6. <span data-ttu-id="11ab9-119">다음 명령을 입력 하 여 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-119">Enter the following command to run the cmdlet.</span></span> `get-proc`

   `get-proc`

   <span data-ttu-id="11ab9-120">다음은 이러한 단계를 수행 하 여 생성 되는 샘플 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-120">This is a sample output that results from following these steps.</span></span>

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a><span data-ttu-id="11ab9-121">요구 사항</span><span class="sxs-lookup"><span data-stu-id="11ab9-121">Requirements</span></span>

<span data-ttu-id="11ab9-122">이 샘플에는 Windows PowerShell 1.0 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-122">This sample requires Windows PowerShell 1.0 or later.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="11ab9-123">데모</span><span class="sxs-lookup"><span data-stu-id="11ab9-123">Demonstrates</span></span>

<span data-ttu-id="11ab9-124">이 샘플에서는 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-124">This sample demonstrates the following.</span></span>

- <span data-ttu-id="11ab9-125">기본 샘플 cmdlet을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-125">Creating a basic sample cmdlet.</span></span>

- <span data-ttu-id="11ab9-126">Cmdlet 특성을 사용 하 여 cmdlet 클래스 정의</span><span class="sxs-lookup"><span data-stu-id="11ab9-126">Defining a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="11ab9-127">Windows PowerShell 1.0 및 Windows PowerShell 2.0 둘 다에서 작동 하는 스냅인 만들기</span><span class="sxs-lookup"><span data-stu-id="11ab9-127">Creating a snap-in that works with both Windows PowerShell 1.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="11ab9-128">이후 샘플에서는 스냅인 대신 모듈을 사용 하므로 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-128">Subsequent samples use modules instead of snap-ins so they require Windows PowerShell 2.0.</span></span>

## <a name="example"></a><span data-ttu-id="11ab9-129">예제</span><span class="sxs-lookup"><span data-stu-id="11ab9-129">Example</span></span>

<span data-ttu-id="11ab9-130">이 샘플에서는 간단한 cmdlet 및 해당 스냅인을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="11ab9-130">This sample shows how to create a simple cmdlet and its snap-in.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a><span data-ttu-id="11ab9-131">관련 항목</span><span class="sxs-lookup"><span data-stu-id="11ab9-131">See Also</span></span>

[<span data-ttu-id="11ab9-132">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="11ab9-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
