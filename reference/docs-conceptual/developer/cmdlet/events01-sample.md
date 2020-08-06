---
title: Events01 샘플 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c7b0f759ca6f3c078649a462eac1713e8214a237
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774460"
---
# <a name="events01-sample"></a>Events01 샘플

이 샘플에서는 사용자가 [system.web](/dotnet/api/System.IO.FileSystemWatcher)에 의해 발생 한 이벤트를 등록할 수 있도록 하는 cmdlet을 만드는 방법을 보여 줍니다.
이 cmdlet을 사용 하면 사용자가 특정 디렉터리에서 파일을 만들 때 실행할 작업을 등록할 수 있습니다.
이 샘플은 [ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 기본 클래스에서 파생 됩니다.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Visual Studio를 사용 하 여 샘플을 빌드하는 방법입니다.

1. Windows PowerShell 2.0 SDK가 설치 된 상태에서 Events01 폴더로 이동 합니다.
   기본 위치는 `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`입니다.

2. 솔루션 (.sln) 파일의 아이콘을 두 번 클릭 합니다.
   그러면 Microsoft Visual Studio의 샘플 프로젝트가 열립니다.

3. **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.
   샘플에 대 한 라이브러리는 기본 `\bin` 또는 `\bin\debug` 폴더로 빌드됩니다.

### <a name="how-to-run-the-sample"></a>샘플을 실행하는 방법

1. 다음 모듈 폴더를 만듭니다.

    `[user]/documents/windowspowershell/modules/events01`

2. 샘플의 라이브러리 파일을 모듈 폴더에 복사 합니다.

3. Windows PowerShell을 시작합니다.

4. 다음 명령을 실행 하 여 Windows PowerShell에 cmdlet을 로드 합니다.

    ```powershell
    import-module events01
    ```

5. FileSystemEvent cmdlet을 사용 하 여 임시 디렉터리에서 파일을 만들 때 메시지를 기록 하는 작업을 등록할 수 있습니다.

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. 임시 디렉터리 아래에 파일을 만들고 작업이 실행 되었는지 확인 합니다 (메시지가 표시 됨).

다음 단계를 수행 하 여 결과를 생성 하는 샘플 출력입니다.

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

## <a name="requirements"></a>요구 사항

이 샘플에는 Windows PowerShell 2.0이 필요 합니다.

## <a name="demonstrates"></a>데모

이 샘플에서는 다음을 보여 줍니다.

### <a name="how-to-write-a-cmdlet-for-event-registration"></a>이벤트 등록을 위해 cmdlet을 작성 하는 방법

Cmdlet은 cmdlet에 공통적인 매개 변수를 지 원하는 [ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 클래스에서 파생 됩니다. `Register-*Event`
[ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 에서 파생 된 cmdlet은 특정 매개 변수만 정의 하 고 `GetSourceObject` 및 추상 메서드를 재정의 해야 합니다. `GetSourceObjectEventName`

## <a name="example"></a>예제

이 샘플에서는 [system.object](/dotnet/api/System.IO.FileSystemWatcher)에 의해 발생 한 이벤트를 등록 하는 방법을 보여 줍니다.

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

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](writing-a-windows-powershell-cmdlet.md)
