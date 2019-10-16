---
title: Events01 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: 8f745cc0e5ef6db7a6bbdf39d826103f3b8a98ce
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369742"
---
# <a name="events01-sample"></a><span data-ttu-id="0f98b-102">Events01 샘플</span><span class="sxs-lookup"><span data-stu-id="0f98b-102">Events01 Sample</span></span>

<span data-ttu-id="0f98b-103">이 샘플에서는 사용자가 [system.web](/dotnet/api/System.IO.FileSystemWatcher)에 의해 발생 한 이벤트를 등록할 수 있도록 하는 cmdlet을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>
<span data-ttu-id="0f98b-104">이 cmdlet을 사용 하면 사용자가 특정 디렉터리에서 파일을 만들 때 실행할 작업을 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span>
<span data-ttu-id="0f98b-105">이 샘플은 [ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 기본 클래스에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-105">This sample derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="0f98b-106">Visual Studio를 사용 하 여 샘플을 빌드하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="0f98b-107">Windows PowerShell 2.0 SDK가 설치 된 상태에서 Events01 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span>
   <span data-ttu-id="0f98b-108">기본 위치는 `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`입니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-108">The default location is `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span></span>

2. <span data-ttu-id="0f98b-109">솔루션 (.sln) 파일의 아이콘을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-109">Double-click the icon for the solution (.sln) file.</span></span>
   <span data-ttu-id="0f98b-110">그러면 Microsoft Visual Studio의 샘플 프로젝트가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="0f98b-111">**빌드** 메뉴에서 **솔루션 빌드**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-111">In the **Build** menu, select **Build Solution**.</span></span>
   <span data-ttu-id="0f98b-112">샘플에 대 한 라이브러리는 기본 `\bin` 또는 `\bin\debug` 폴더로 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-112">The library for the sample will be built in the default `\bin` or `\bin\debug` folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="0f98b-113">샘플을 실행 하는 방법</span><span class="sxs-lookup"><span data-stu-id="0f98b-113">How to run the sample</span></span>

1. <span data-ttu-id="0f98b-114">다음 모듈 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="0f98b-115">샘플의 라이브러리 파일을 모듈 폴더에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="0f98b-116">Windows PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="0f98b-117">다음 명령을 실행 하 여 Windows PowerShell에 cmdlet을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="0f98b-118">FileSystemEvent cmdlet을 사용 하 여 임시 디렉터리에서 파일을 만들 때 메시지를 기록 하는 작업을 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="0f98b-119">임시 디렉터리 아래에 파일을 만들고 작업이 실행 되었는지 확인 합니다 (메시지가 표시 됨).</span><span class="sxs-lookup"><span data-stu-id="0f98b-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="0f98b-120">다음 단계를 수행 하 여 결과를 생성 하는 샘플 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-120">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="0f98b-121">요구 사항</span><span class="sxs-lookup"><span data-stu-id="0f98b-121">Requirements</span></span>

<span data-ttu-id="0f98b-122">이 샘플에는 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="0f98b-123">보여</span><span class="sxs-lookup"><span data-stu-id="0f98b-123">Demonstrates</span></span>

<span data-ttu-id="0f98b-124">이 샘플에서는 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-124">This sample demonstrates the following.</span></span>

### <a name="how-to-write-a-cmdlet-for-event-registration"></a><span data-ttu-id="0f98b-125">이벤트 등록을 위해 cmdlet을 작성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="0f98b-125">How to write a cmdlet for event registration</span></span>

<span data-ttu-id="0f98b-126">Cmdlet은 `Register-*Event` cmdlet에 공통적인 매개 변수를 지 원하는 [ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 클래스에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-126">The cmdlet derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the `Register-*Event` cmdlets.</span></span>
<span data-ttu-id="0f98b-127">[ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 에서 파생 된 cmdlet은 특정 매개 변수만 정의 하 고 `GetSourceObject` 및 `GetSourceObjectEventName` 추상 메서드를 재정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-127">Cmdlets that are derived from [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="0f98b-128">예제</span><span class="sxs-lookup"><span data-stu-id="0f98b-128">Example</span></span>

<span data-ttu-id="0f98b-129">이 샘플에서는 [system.object](/dotnet/api/System.IO.FileSystemWatcher)에 의해 발생 한 이벤트를 등록 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0f98b-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>

```csharp
namespace Sample
{
    using System;
    using System.IO;
    using System.Management.Automation;
    using System.Management.Automation.Runspaces;
    using Microsoft.PowerShell.Commands;

    [Cmdlet(VerbsLifecycle.Register, "FileSystemEvent")]
    public class RegisterObjectEventCommand : ObjectEventRegistrationBase
    {
        /// <summary>The FileSystemWatcher that exposes the events.</summary>
        private FileSystemWatcher fileSystemWatcher = new FileSystemWatcher();

        /// <summary>Name of the event to which the cmdlet registers.</summary>
        private string eventName = null;

        /// <summary>
        /// Gets or sets the path that will be monitored by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = true, Position = 0)]
        public string Path
        {
            get
            {
                return this.fileSystemWatcher.Path;
            }

            set
            {
                this.fileSystemWatcher.Path = value;
            }
        }

        /// <summary>
        /// Gets or sets the name of the event to which the cmdlet registers.
        /// <para>
        /// Currently System.IO.FileSystemWatcher exposes 6 events: Changed, Created,
        /// Deleted, Disposed, Error, and Renamed. Check the MSDN documentation of
        /// FileSystemWatcher for details on each event.
        /// </para>
        /// </summary>
        [Parameter(Mandatory = true, Position = 1)]
        public string EventName
        {
            get
            {
                return this.eventName;
            }

            set
            {
                this.eventName = value;
            }
        }

        /// <summary>
        /// Gets or sets the filter that will be user by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = false)]
        public string Filter
        {
            get
            {
                return this.fileSystemWatcher.Filter;
            }

            set
            {
                this.fileSystemWatcher.Filter = value;
            }
        }

        /// <summary>
        /// Derived classes must implement this method to return the object that generates
        /// the events to be monitored.
        /// </summary>
        /// <returns> This sample returns an instance of System.IO.FileSystemWatcher</returns>
        protected override object GetSourceObject()
        {
            return this.fileSystemWatcher;
        }

        /// <summary>
        /// Derived classes must implement this method to return the name of the event to
        /// be monitored. This event must be exposed by the input object.
        /// </summary>
        /// <returns> This sample returns the event specified by the user with the -EventName parameter.</returns>
        protected override string GetSourceObjectEventName()
        {
            return this.eventName;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="0f98b-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0f98b-130">See Also</span></span>

<span data-ttu-id="0f98b-131">[Writing a Windows PowerShell Cmdlet](writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="0f98b-131">[Writing a Windows PowerShell Cmdlet](writing-a-windows-powershell-cmdlet.md)</span></span>