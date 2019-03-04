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
ms.openlocfilehash: 3edbcabeff0c8d84831823df11749d152b347566
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863339"
---
# <a name="events01-sample"></a><span data-ttu-id="7a2a4-102">Events01 샘플</span><span class="sxs-lookup"><span data-stu-id="7a2a4-102">Events01 Sample</span></span>

<span data-ttu-id="7a2a4-103">이 샘플에 의해 발생 되는 이벤트에 대 한 사용자 등록을 허용 하는 cmdlet를 만드는 방법을 보여 줍니다 [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher)합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="7a2a4-104">사용자는이 cmdlet을 사용 하 여 특정 디렉터리에서 파일을 만들 때 실행할 작업을 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="7a2a4-105">이 샘플에서 파생 된 [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-105">This sample derives from the [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="7a2a4-106">Visual Studio를 사용 하 여 샘플을 빌드하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="7a2a4-107">Windows PowerShell 2.0 SDK 설치를 사용 하 여 Events01 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span> <span data-ttu-id="7a2a4-108">기본 위치는 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.</span></span>

2. <span data-ttu-id="7a2a4-109">솔루션 (.sln) 파일의 아이콘을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="7a2a4-110">이 Microsoft Visual Studio에서 샘플 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="7a2a4-111">에 **빌드** 메뉴에서 **솔루션 빌드**합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="7a2a4-112">이 샘플에 대 한 라이브러리 기본 \bin 또는 \bin\debug 폴더에 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="7a2a4-113">샘플을 실행 하는 방법</span><span class="sxs-lookup"><span data-stu-id="7a2a4-113">How to run the sample</span></span>

1. <span data-ttu-id="7a2a4-114">다음 모듈 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="7a2a4-115">모듈 폴더에 샘플에 대 한 라이브러리 파일을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="7a2a4-116">Windows PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="7a2a4-117">Windows PowerShell cmdlet을 로드 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="7a2a4-118">TEMP 디렉터리에서 파일을 만들 때 메시지를 작성 하는 액션을 등록 하려면 등록 FileSystemEvent cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="7a2a4-119">TEMP 디렉터리에서 파일을 만들고 작업을 실행 됩니다 (메시지 표시 됨).</span><span class="sxs-lookup"><span data-stu-id="7a2a4-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="7a2a4-120">이것이 이러한 단계에 따라 발생 하는 샘플 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-120">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="7a2a4-121">요구 사항</span><span class="sxs-lookup"><span data-stu-id="7a2a4-121">Requirements</span></span>

<span data-ttu-id="7a2a4-122">이 샘플 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="7a2a4-123">시연</span><span class="sxs-lookup"><span data-stu-id="7a2a4-123">Demonstrates</span></span>

<span data-ttu-id="7a2a4-124">이 샘플에는 다음 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-124">This sample demonstrates the following.</span></span>

- <span data-ttu-id="7a2a4-125">이벤트 등록 용 cmdlet을 작성 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-125">How to write a cmdlet for event registration.</span></span> <span data-ttu-id="7a2a4-126">Cmdlet에서 파생 되는 [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 클래스 등록-일반 매개 변수에 대 한 지원을 제공 하는 \* 이벤트 cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-126">The cmdlet derives from the [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the Register-\*Event cmdlets.</span></span> <span data-ttu-id="7a2a4-127">파생 되는 Cmdlet [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 특정 매개 변수를 정의 하 고 재정의에 필요 합니다 `GetSourceObject` 및 `GetSourceObjectEventName` 추상 메서드.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-127">Cmdlets that are derived from [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="7a2a4-128">예제</span><span class="sxs-lookup"><span data-stu-id="7a2a4-128">Example</span></span>

<span data-ttu-id="7a2a4-129">이 샘플에서 발생 한 이벤트에 대 한 등록 하는 방법을 보여 줍니다 [System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="7a2a4-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7a2a4-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7a2a4-130">See Also</span></span>

<span data-ttu-id="7a2a4-131">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="7a2a4-131">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>