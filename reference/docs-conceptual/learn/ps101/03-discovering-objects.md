---
title: 개체 검색, 속성 및 메서드
description: 개체, 속성, 메서드를 이해하고 사용하기 위해 개발자까지 될 필요는 없습니다.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: f226221da7dd3b663f54cf23439dd7f945ed3a2a
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99599557"
---
# <a name="chapter-3---discovering-objects-properties-and-methods"></a>3장 - 개체, 속성 및 메서드 검색

필자가 처음 컴퓨터를 접한 것은 Commodore 64이지만 첫 번째 최신 컴퓨터는 286 12-Mhz IBM 클론이었는데, Microsoft DOS 3.3을 실행하고 메모리 1메가바이트, 하드 드라이브 40메가바이트, 5-1/4 인치 플로피 디스크 드라이브 1개, CGA 모니터 1개가 포함되어 있었습니다.

많은 IT 전문가는 명령줄에는 정통하지만, 개체, 속성, 메서드라는 주체가 등장하면 화들짝 놀란 표정으로 "저는 개발자가 아닙니다."라고 말합니다. 왜 그럴까요? PowerShell에서 성공하기 위해 개발자가 될 필요는 없습니다. 용어에 매몰되지 마세요. 처음에 모든 것을 바로 이해할 수는 없겠지만, 어느 정도 실습을 하고 나면 "아하! 이 책에서 말한 내용이 바로 이거였군"하고 이해되는 순간이 올 것입니다.

이러한 실습 경험을 얻으려면 컴퓨터에서 예제를 직접 시도해야 합니다.

## <a name="requirements"></a>요구 사항

Active Directory PowerShell 모듈이 이 장에 표시된 일부 예제에 필요합니다.
이 모듈은 Windows용 RSAT(원격 서버 관리 도구)의 일부입니다. Windows 1809 이상 빌드에서는 RSAT 도구가 Windows 기능으로 설치됩니다.

- RSAT 도구를 설치하는 방법에 대한 자세한 내용은 [Windows 관리 모듈][]을 참조하세요.
- 이전 버전의 Windows인 경우 [Windows용 RSAT][]를 참조하세요.

## <a name="get-member"></a>Get-Member

`Get-Member`는 명령에 사용할 수 있는 개체, 속성 및 메서드를 검색하는 데 도움이 됩니다.
개체 기반 출력을 생성하는 명령은 모두 `Get-Member`로 파이프할 수 있습니다. 속성은 항목의 특징입니다. 운전면허에는 안구 색상이라는 속성이 있으며 해당 속성에 대한 가장 일반적인 값은 파란색과 갈색입니다. 메서드는 항목에 대해 수행할 수 있는 작업입니다. 계속해서 운전면허를 예로 들면, 메서드 중 하나는 '면허 취소'입니다. 경찰이 운전자의 운전면허를 취소할 수 있기 때문입니다.

### <a name="properties"></a>속성

다음 예제에서는 내 컴퓨터에서 실행되는 Windows 시간 서비스에 대한 정보를 검색하겠습니다.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

이전 결과 집합에 표시된 것처럼 **Status**, **Name** 및 **DisplayName** 이 속성의 예입니다. **Status** 속성의 값은 `Running`이고, **Name** 속성의 값은 `w32time`이고, **DisplayName** 의 값은 `Windows Time`입니다.

이제 동일한 명령을 `Get-Member`로 파이프하겠습니다.

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

이전 예제에서 결과의 첫 번째 줄에는 매우 중요한 정보 하나가 포함되어 있습니다. **TypeName** 은 반환된 개체의 형식을 알려줍니다. 이 예제에서는 **System.ServiceProcess.ServiceController** 개체가 반환되었습니다. 이 개체는 흔히 마지막 마침표 바로 뒷부분인 **TypeName** 으로 축약됩니다. 이 예제에서는 **ServiceController** 입니다.

명령이 생성하는 개체 형식을 알고 있으면 이 정보를 사용하여 해당 형식의 개체를 입력으로 사용하는 명령을 찾을 수 있습니다.

```powershell
Get-Command -ParameterType ServiceController
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
```

이러한 모든 명령에는 **ServiceController** 개체 형식(파이프라인, 매개 변수 입력, 또는 둘 다)을 허용하는 매개 변수가 있습니다.

기본적으로 표시되는 것보다 많은 속성이 있습니다. 이러한 추가 속성은 기본적으로 표시되지 않지만 명령을 `Select-Object` cmdlet으로 파이프하고 **Property** 매개 변수를 사용하여 파이프라인에서 선택할 수 있습니다. 다음 예제에서는 `Get-Service`의 결과를 `Select-Object`로 파이프하고 `*` 와일드카드 문자를 **Property** 매개 변수에 대한 값으로 지정하여 모든 속성을 선택합니다.

```powershell
Get-Service -Name w32time | Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

**속성** 매개 변수의 값에 대해 쉼표로 구분된 목록을 사용하여 특정 속성을 선택할 수도 있습니다.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, Name, DisplayName, ServiceType
```

```Output
 Status Name    DisplayName        ServiceType
 ------ ----    -----------        -----------
Running w32time Windows Time Win32ShareProcess
```

기본적으로 4개 속성은 테이블로 반환되고 5개 이상의 속성은 목록으로 반환됩니다. 일부 명령은 사용자 지정 형식을 사용하여 기본적으로 테이블에 표시되는 속성 수를 재정의합니다.
이러한 기본값을 수동으로 재정의하는 데 사용할 수 있는 몇 가지 `Format-*` cmdlet이 있습니다. 가장 일반적인 것은 `Format-Table` 및 `Format-List`이며 둘 다 이후의 장에서 다룹니다.

`Select-Object`를 사용하여 속성 이름을 지정할 때 와일드카드 문자를 사용할 수 있습니다.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```powershell
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

이전 예제에서 `Can*`은 **Property** 매개 변수에 대한 값 중 하나로 사용되어 `Can`으로 시작하는 모든 속성을 반환합니다. 여기에는 **CanPauseAndContinue**, **CanShutdown**, **CanStop** 이 포함됩니다.

### <a name="methods"></a>메서드

메서드는 수행할 수 있는 작업입니다. **MemberType** 매개 변수를 사용하여 `Get-Service`에 대한 메서드만 표시하도록 `Get-Member` 결과의 범위를 좁힐 수 있습니다.

```powershell
Get-Service -Name w32time | Get-Member -MemberType Method
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType Definition
----                      ---------- ----------
Close                     Method     void Close()
Continue                  Method     void Continue()
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type ...
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Equals                    Method     bool Equals(System.Object obj)
ExecuteCommand            Method     void ExecuteCommand(int command)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Pause                     Method     void Pause()
Refresh                   Method     void Refresh()
Start                     Method     void Start(), void Start(string[] args)
Stop                      Method     void Stop()
WaitForStatus             Method     void WaitForStatus(System.ServiceProcess.ServiceC...
```

여기에서 볼 수 있듯이 많은 메서드가 있습니다. **Stop** 메서드를 사용하여 Windows 서비스를 중지할 수 있습니다.

```powershell
(Get-Service -Name w32time).Stop()
```

이제 Windows 시간 서비스가 정말 중지되었는지 확인해보겠습니다.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  w32time            Windows Time
```

필자가 메서드를 사용하는 경우는 많지 않지만 여러분은 잘 알고 있어야 합니다. 항목을 수정하기 위한 해당하는 명령이 없는 `Get-*` 명령과 마주치는 경우가 있습니다.
흔히 메서드를 사용하여 항목을 수정하는 작업을 수행할 수 있습니다. SqlServer PowerShell 모듈의 `Get-SqlAgentJob` cmdlet은 그 좋은 예입니다. 이 모듈은 [SMSS(SQL Server Management Studio)][SMSS]의 일부로 설치됩니다. 해당하는 `Set-*` cmdlet은 없지만 메서드를 사용하여 동일한 작업을 완료할 수 있습니다.

메서드를 잘 이해해야 하는 또 다른 이유는 많은 초보자가 `Get-*` 명령은 파괴적인 변경을 초래할 수 없다고 생각하는 것입니다. 그러나 이 명령을 잘못 사용하는 경우 매우 심각한 문제가 발생할 수 있습니다.

있는 경우 cmdlet을 사용하여 작업을 수행하는 것이 좋습니다. 계속해서 Windows 시간 서비스를 시작합니다. 단, 이번에는 cmdlet을 사용하여 서비스를 시작합니다.

```powershell
Get-Service -Name w32time | Start-Service -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

기본적으로 `Start-Service`는 `Get-Service`의 시작 메서드와 마찬가지로 아무 결과도 반환하지 않습니다.
하지만 cmdlet을 사용하는 이점 중 하나는 cmdlet이 메서드와 함께 사용할 수 없는 추가 기능을 제공한다는 것입니다. 이전 예제에서는 **PassThru** 매개 변수가 사용되었습니다. 이 때문에 일반적으로 출력을 생성하지 않는 cmdlet이 출력을 생성합니다.

Cmdlet의 출력에 대한 가정은 신중히 해야 합니다. 우리 모두는 무언가를 가정할 때 어떤 일이 벌어지는지 잘 알고 있습니다. Windows 10 랩 환경 컴퓨터에서 실행되는 PowerShell 프로세스에 대한 정보를 검색하겠습니다.

```powershell
Get-Process -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    922      48   107984     140552       2.84   9020   1 powershell

```

이제 동일한 명령을 Get-Member로 파이프하겠습니다.

```powershell
Get-Process -Name PowerShell | Get-Member
```

```Output
   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
NPM                        AliasProperty  NPM = NonpagedSystemMemorySize64
PM                         AliasProperty  PM = PagedMemorySize64
SI                         AliasProperty  SI = SessionId
VM                         AliasProperty  VM = VirtualMemorySize64
WS                         AliasProperty  WS = WorkingSet64
Disposed                   Event          System.EventHandler Disposed(System.Object, ...
ErrorDataReceived          Event          System.Diagnostics.DataReceivedEventHandler ...
Exited                     Event          System.EventHandler Exited(System.Object, Sy...
OutputDataReceived         Event          System.Diagnostics.DataReceivedEventHandler ...
BeginErrorReadLine         Method         void BeginErrorReadLine()
BeginOutputReadLine        Method         void BeginOutputReadLine()
CancelErrorRead            Method         void CancelErrorRead()
CancelOutputRead           Method         void CancelOutputRead()
Close                      Method         void Close()
CloseMainWindow            Method         bool CloseMainWindow()
CreateObjRef               Method         System.Runtime.Remoting.ObjRef CreateObjRef(...
Dispose                    Method         void Dispose(), void IDisposable.Dispose()
Equals                     Method         bool Equals(System.Object obj)
GetHashCode                Method         int GetHashCode()
GetLifetimeService         Method         System.Object GetLifetimeService()
GetType                    Method         type GetType()
InitializeLifetimeService  Method         System.Object InitializeLifetimeService()
Kill                       Method         void Kill()
Refresh                    Method         void Refresh()
Start                      Method         bool Start()
ToString                   Method         string ToString()
WaitForExit                Method         bool WaitForExit(int milliseconds), void Wai...
WaitForInputIdle           Method         bool WaitForInputIdle(int milliseconds), boo...
__NounName                 NoteProperty   string __NounName=Process
BasePriority               Property       int BasePriority {get;}
Container                  Property       System.ComponentModel.IContainer Container {...
EnableRaisingEvents        Property       bool EnableRaisingEvents {get;set;}
ExitCode                   Property       int ExitCode {get;}
ExitTime                   Property       datetime ExitTime {get;}
Handle                     Property       System.IntPtr Handle {get;}
HandleCount                Property       int HandleCount {get;}
HasExited                  Property       bool HasExited {get;}
Id                         Property       int Id {get;}
MachineName                Property       string MachineName {get;}
MainModule                 Property       System.Diagnostics.ProcessModule MainModule ...
MainWindowHandle           Property       System.IntPtr MainWindowHandle {get;}
MainWindowTitle            Property       string MainWindowTitle {get;}
MaxWorkingSet              Property       System.IntPtr MaxWorkingSet {get;set;}
MinWorkingSet              Property       System.IntPtr MinWorkingSet {get;set;}
Modules                    Property       System.Diagnostics.ProcessModuleCollection M...
NonpagedSystemMemorySize   Property       int NonpagedSystemMemorySize {get;}
NonpagedSystemMemorySize64 Property       long NonpagedSystemMemorySize64 {get;}
PagedMemorySize            Property       int PagedMemorySize {get;}
PagedMemorySize64          Property       long PagedMemorySize64 {get;}
PagedSystemMemorySize      Property       int PagedSystemMemorySize {get;}
PagedSystemMemorySize64    Property       long PagedSystemMemorySize64 {get;}
PeakPagedMemorySize        Property       int PeakPagedMemorySize {get;}
PeakPagedMemorySize64      Property       long PeakPagedMemorySize64 {get;}
PeakVirtualMemorySize      Property       int PeakVirtualMemorySize {get;}
PeakVirtualMemorySize64    Property       long PeakVirtualMemorySize64 {get;}
PeakWorkingSet             Property       int PeakWorkingSet {get;}
PeakWorkingSet64           Property       long PeakWorkingSet64 {get;}
PriorityBoostEnabled       Property       bool PriorityBoostEnabled {get;set;}
PriorityClass              Property       System.Diagnostics.ProcessPriorityClass Prio...
PrivateMemorySize          Property       int PrivateMemorySize {get;}
PrivateMemorySize64        Property       long PrivateMemorySize64 {get;}
PrivilegedProcessorTime    Property       timespan PrivilegedProcessorTime {get;}
ProcessName                Property       string ProcessName {get;}
ProcessorAffinity          Property       System.IntPtr ProcessorAffinity {get;set;}
Responding                 Property       bool Responding {get;}
SafeHandle                 Property       Microsoft.Win32.SafeHandles.SafeProcessHandl...
SessionId                  Property       int SessionId {get;}
Site                       Property       System.ComponentModel.ISite Site {get;set;}
StandardError              Property       System.IO.StreamReader StandardError {get;}
StandardInput              Property       System.IO.StreamWriter StandardInput {get;}
StandardOutput             Property       System.IO.StreamReader StandardOutput {get;}
StartInfo                  Property       System.Diagnostics.ProcessStartInfo StartInf...
StartTime                  Property       datetime StartTime {get;}
SynchronizingObject        Property       System.ComponentModel.ISynchronizeInvoke Syn...
Threads                    Property       System.Diagnostics.ProcessThreadCollection T...
TotalProcessorTime         Property       timespan TotalProcessorTime {get;}
UserProcessorTime          Property       timespan UserProcessorTime {get;}
VirtualMemorySize          Property       int VirtualMemorySize {get;}
VirtualMemorySize64        Property       long VirtualMemorySize64 {get;}
WorkingSet                 Property       int WorkingSet {get;}
WorkingSet64               Property       long WorkingSet64 {get;}
PSConfiguration            PropertySet    PSConfiguration {Name, Id, PriorityClass, Fi...
PSResources                PropertySet    PSResources {Name, Id, Handlecount, WorkingS...
Company                    ScriptProperty System.Object Company {get=$this.Mainmodule....
CPU                        ScriptProperty System.Object CPU {get=$this.TotalProcessorT...
Description                ScriptProperty System.Object Description {get=$this.Mainmod...
FileVersion                ScriptProperty System.Object FileVersion {get=$this.Mainmod...
Path                       ScriptProperty System.Object Path {get=$this.Mainmodule.Fil...
Product                    ScriptProperty System.Object Product {get=$this.Mainmodule....
ProductVersion             ScriptProperty System.Object ProductVersion {get=$this.Main...
```

기본적으로 표시되는 것보다 많은 속성이 나열된 것을 알 수 있습니다. `Get-Member`의 결과를 보면 표시된 기본 속성 중 여러 개가 속성으로 나타나지 않습니다. `NPM(K)`, `PM(K)`, `WS(K)`, `CPU(s)` 등 여러 개의 표시된 값이 계산된 속성이기 때문입니다. 실제 속성 이름을 확인하려면 명령을 `Get-Member`로 파이프해야 합니다.

명령이 출력을 생성하지 않는 경우에는 `Get-Member`로 파이프할 수 없습니다. `Start-Service`는 기본적으로 출력을 생성하지 않기 때문에 `Get-Member`로 파이프하려고 하면 오류가 생성됩니다.

```powershell
Start-Service -Name w32time | Get-Member
```

```Output
Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:31
+ Start-Service -Name w32time | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMembe
   rCommand
```

`Start-Service` cmdlet에서 **PassThru** 매개 변수를 사용하여 출력을 생성하도록 지정하면 오류 없이 `Get-Member`로 파이프할 수 있습니다.

```powershell
Start-Service -Name w32time -PassThru | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

`Get-Member`로 파이프하려면 명령이 개체 기반 출력을 생성해야 합니다.

```powershell
Get-Service -Name w32time | Out-Host | Get-Member
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time

Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:40
+ Get-Service -Name w32time | Out-Host | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMemberCommand
```

`Out-Host`는 PowerShell 호스트에 직접 기록하지만 파이프라인에 대한 개체 기반 출력을 생성하지는 않습니다. 따라서 `Get-Member`로 파이프할 수 없습니다.

## <a name="active-directory"></a>Active Directory

> [!NOTE]
> 이 섹션을 완료하려면 이 장의 요구 사항 섹션에 나열된 원격 서버 관리 도구가 필요합니다. 또한 이 책의 서론에 설명된 대로 Windows 10 랩 환경 컴퓨터가 랩 환경 도메인의 멤버여야 합니다.

`Get-Command`를 **Module** 매개 변수와 함께 사용하여 원격 서버 관리 도구가 설치되었을 때 ActiveDirectory PowerShell 모듈의 일부로 추가된 명령을 확인합니다.

```powershell
Get-Command -Module ActiveDirectory
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Add-ADCentralAccessPolicyMember                    1.0.0.0    ActiveDi...
Cmdlet          Add-ADComputerServiceAccount                       1.0.0.0    ActiveDi...
Cmdlet          Add-ADDomainControllerPasswordReplicationPolicy    1.0.0.0    ActiveDi...
Cmdlet          Add-ADFineGrainedPasswordPolicySubject             1.0.0.0    ActiveDi...
Cmdlet          Add-ADGroupMember                                  1.0.0.0    ActiveDi...
Cmdlet          Add-ADPrincipalGroupMembership                     1.0.0.0    ActiveDi...
Cmdlet          Add-ADResourcePropertyListMember                   1.0.0.0    ActiveDi...
Cmdlet          Clear-ADAccountExpiration                          1.0.0.0    ActiveDi...
Cmdlet          Clear-ADClaimTransformLink                         1.0.0.0    ActiveDi...
Cmdlet          Disable-ADAccount                                  1.0.0.0    ActiveDi...
...
```

ActiveDirectory PowerShell 모듈의 일부로 총 147개 명령이 추가되었습니다. 이 중 일부 명령은 기본적으로 사용 가능한 속성의 일부만 반환합니다.

이 모듈의 명령 이름에 무언가 다른 점이 있다는 것을 눈치채셨나요? 명령의 명사 부분에 AD 접두사가 있습니다. 이는 대부분의 모듈 명령에서 일반적입니다. 접두사는 이름 충돌을 방지하도록 설계되었습니다.

```powershell
Get-ADUser -Identity mike | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name              MemberType            Definition
----              ----------            ----------
Contains          Method                bool Contains(string propertyName)
Equals            Method                bool Equals(System.Object obj)
GetEnumerator     Method                System.Collections.IDictionaryEnumerator GetEn...
GetHashCode       Method                int GetHashCode()
GetType           Method                type GetType()
ToString          Method                string ToString()
Item              ParameterizedProperty Microsoft.ActiveDirectory.Management.ADPropert...
DistinguishedName Property              System.String DistinguishedName {get;set;}
Enabled           Property              System.Boolean Enabled {get;set;}
GivenName         Property              System.String GivenName {get;set;}
Name              Property              System.String Name {get;}
ObjectClass       Property              System.String ObjectClass {get;set;}
ObjectGUID        Property              System.Nullable`1[[System.Guid, mscorlib, Vers...
SamAccountName    Property              System.String SamAccountName {get;set;}
SID               Property              System.Security.Principal.SecurityIdentifier S...
Surname           Property              System.String Surname {get;set;}
UserPrincipalName Property              System.String UserPrincipalName {get;set;}
```

Active Directory에 대해 약간의 지식만 있더라도 사용자 계정에는 이 예제에 표시된 것보다 많은 속성이 있다는 것을 알 수 있습니다.

`Get-ADUser` cmdlet에는 반환하려는 추가(기본값이 아닌) 속성을 지정하는 데 사용되는 **Properties** 매개 변수가 있습니다. `*` 와일드카드 문자를 지정하면 모든 속성을 반환합니다.

```powershell
Get-ADUser -Identity mike -Properties * | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name                                 MemberType            Definition
----                                 ----------            ----------
Contains                             Method                bool Contains(string proper...
Equals                               Method                bool Equals(System.Object obj)
GetEnumerator                        Method                System.Collections.IDiction...
GetHashCode                          Method                int GetHashCode()
GetType                              Method                type GetType()
ToString                             Method                string ToString()
Item                                 ParameterizedProperty Microsoft.ActiveDirectory.M...
AccountExpirationDate                Property              System.DateTime AccountExpi...
accountExpires                       Property              System.Int64 accountExpires...
AccountLockoutTime                   Property              System.DateTime AccountLock...
AccountNotDelegated                  Property              System.Boolean AccountNotDe...
AllowReversiblePasswordEncryption    Property              System.Boolean AllowReversi...
AuthenticationPolicy                 Property              Microsoft.ActiveDirectory.M...
AuthenticationPolicySilo             Property              Microsoft.ActiveDirectory.M...
BadLogonCount                        Property              System.Int32 BadLogonCount ...
badPasswordTime                      Property              System.Int64 badPasswordTim...
badPwdCount                          Property              System.Int32 badPwdCount {g...
CannotChangePassword                 Property              System.Boolean CannotChange...
CanonicalName                        Property              System.String CanonicalName...
Certificates                         Property              Microsoft.ActiveDirectory.M...
City                                 Property              System.String City {get;set;}
CN                                   Property              System.String CN {get;}
codePage                             Property              System.Int32 codePage {get;...
Company                              Property              System.String Company {get;...
CompoundIdentitySupported            Property              Microsoft.ActiveDirectory.M...
Country                              Property              System.String Country {get;...
countryCode                          Property              System.Int32 countryCode {g...
Created                              Property              System.DateTime Created {get;}
createTimeStamp                      Property              System.DateTime createTimeS...
Deleted                              Property              System.Boolean Deleted {get;}
Department                           Property              System.String Department {g...
Description                          Property              System.String Description {...
DisplayName                          Property              System.String DisplayName {...
DistinguishedName                    Property              System.String Distinguished...
Division                             Property              System.String Division {get...
DoesNotRequirePreAuth                Property              System.Boolean DoesNotRequi...
dSCorePropagationData                Property              Microsoft.ActiveDirectory.M...
EmailAddress                         Property              System.String EmailAddress ...
EmployeeID                           Property              System.String EmployeeID {g...
EmployeeNumber                       Property              System.String EmployeeNumbe...
Enabled                              Property              System.Boolean Enabled {get...
Fax                                  Property              System.String Fax {get;set;}
GivenName                            Property              System.String GivenName {ge...
HomeDirectory                        Property              System.String HomeDirectory...
HomedirRequired                      Property              System.Boolean HomedirRequi...
HomeDrive                            Property              System.String HomeDrive {ge...
HomePage                             Property              System.String HomePage {get...
HomePhone                            Property              System.String HomePhone {ge...
Initials                             Property              System.String Initials {get...
instanceType                         Property              System.Int32 instanceType {...
isDeleted                            Property              System.Boolean isDeleted {g...
KerberosEncryptionType               Property              Microsoft.ActiveDirectory.M...
LastBadPasswordAttempt               Property              System.DateTime LastBadPass...
LastKnownParent                      Property              System.String LastKnownPare...
lastLogoff                           Property              System.Int64 lastLogoff {ge...
lastLogon                            Property              System.Int64 lastLogon {get...
LastLogonDate                        Property              System.DateTime LastLogonDa...
lastLogonTimestamp                   Property              System.Int64 lastLogonTimes...
LockedOut                            Property              System.Boolean LockedOut {g...
logonCount                           Property              System.Int32 logonCount {ge...
LogonWorkstations                    Property              System.String LogonWorkstat...
Manager                              Property              System.String Manager {get;...
MemberOf                             Property              Microsoft.ActiveDirectory.M...
MNSLogonAccount                      Property              System.Boolean MNSLogonAcco...
MobilePhone                          Property              System.String MobilePhone {...
Modified                             Property              System.DateTime Modified {g...
modifyTimeStamp                      Property              System.DateTime modifyTimeS...
msDS-User-Account-Control-Computed   Property              System.Int32 msDS-User-Acco...
Name                                 Property              System.String Name {get;}
nTSecurityDescriptor                 Property              System.DirectoryServices.Ac...
ObjectCategory                       Property              System.String ObjectCategor...
ObjectClass                          Property              System.String ObjectClass {...
ObjectGUID                           Property              System.Nullable`1[[System.G...
objectSid                            Property              System.Security.Principal.S...
Office                               Property              System.String Office {get;s...
OfficePhone                          Property              System.String OfficePhone {...
Organization                         Property              System.String Organization ...
OtherName                            Property              System.String OtherName {ge...
PasswordExpired                      Property              System.Boolean PasswordExpi...
PasswordLastSet                      Property              System.DateTime PasswordLas...
PasswordNeverExpires                 Property              System.Boolean PasswordNeve...
PasswordNotRequired                  Property              System.Boolean PasswordNotR...
POBox                                Property              System.String POBox {get;set;}
PostalCode                           Property              System.String PostalCode {g...
PrimaryGroup                         Property              System.String PrimaryGroup ...
primaryGroupID                       Property              System.Int32 primaryGroupID...
PrincipalsAllowedToDelegateToAccount Property              Microsoft.ActiveDirectory.M...
ProfilePath                          Property              System.String ProfilePath {...
ProtectedFromAccidentalDeletion      Property              System.Boolean ProtectedFro...
pwdAnswer                            Property              System.String pwdAnswer {ge...
pwdLastSet                           Property              System.Int64 pwdLastSet {ge...
pwdQuestion                          Property              System.String pwdQuestion {...
SamAccountName                       Property              System.String SamAccountNam...
sAMAccountType                       Property              System.Int32 sAMAccountType...
ScriptPath                           Property              System.String ScriptPath {g...
sDRightsEffective                    Property              System.Int32 sDRightsEffect...
ServicePrincipalNames                Property              Microsoft.ActiveDirectory.M...
SID                                  Property              System.Security.Principal.S...
SIDHistory                           Property              Microsoft.ActiveDirectory.M...
SmartcardLogonRequired               Property              System.Boolean SmartcardLog...
sn                                   Property              System.String sn {get;set;}
State                                Property              System.String State {get;set;}
StreetAddress                        Property              System.String StreetAddress...
Surname                              Property              System.String Surname {get;...
Title                                Property              System.String Title {get;set;}
TrustedForDelegation                 Property              System.Boolean TrustedForDe...
TrustedToAuthForDelegation           Property              System.Boolean TrustedToAut...
UseDESKeyOnly                        Property              System.Boolean UseDESKeyOnl...
userAccountControl                   Property              System.Int32 userAccountCon...
userCertificate                      Property              Microsoft.ActiveDirectory.M...
UserPrincipalName                    Property              System.String UserPrincipal...
uSNChanged                           Property              System.Int64 uSNChanged {get;}
uSNCreated                           Property              System.Int64 uSNCreated {get;}
whenChanged                          Property              System.DateTime whenChanged...
whenCreated                          Property              System.DateTime whenCreated...
```

이제 더 비슷하게 보입니다.

Active Directory 사용자 계정의 속성은 기본적으로 이렇게 제한되는 이유를 생각할 수 있으신가요? 예를 들어 여러분이 프로덕션 Active Directory 환경의 모든 사용자 계정에 대해 모든 속성을 반환하는 경우 이로 인해 도메인 컨트롤러 자체뿐만 아니라 네트워크에서도 발생할 수 있는 성능 저하를 생각해 보세요. 실제로 여러분에게 모든 속성이 필요한지도 의문입니다. 단일 사용자 계정에서 모든 속성을 반환하는 것은 존재하는 속성을 확인하려고 할 때 완벽하게 이해가 갑니다.

명령의 프로토타입을 생성할 때 명령을 여러 번 실행하는 것은 드문 일이 아닙니다. 상당히 규모가 큰 쿼리를 수행하려는 경우 한 번 쿼리를 실행하고 결과를 변수에 저장합니다. 그런 다음 비용이 많이 드는 쿼리를 반복적으로 사용하는 대신 변수의 내용으로 작업합니다.

```powershell
$Users = Get-ADUser -Identity mike -Properties *
```

이전 명령을 여러 번 실행하는 대신 `$Users` 변수의 내용을 사용합니다.
단, Active Directory에서 해당 사용자가 변경되면 이 변수의 내용이 업데이트되지 않습니다.

`$Users` 변수를 `Get-Member`로 파이프하여 사용 가능한 속성을 검색할 수 있습니다.

```powershell
$Users | Get-Member
```

그런 다음 Active Directory를 두 번 이상 쿼리하지 않고도 `$Users`를 `Select-Object`로 파이프하여 개별 속성을 선택합니다.

```powershell
$Users | Select-Object -Property Name, LastLogonDate, LastBadPasswordAttempt
```

Active Directory를 두 번 이상 쿼리하려면 **Properties** 매개 변수를 사용하여 원하는 기본값이 아닌 속성을 지정합니다.

```powershell
Get-ADUser -Identity mike -Properties LastLogonDate, LastBadPasswordAttempt
```

```Output
DistinguishedName      : CN=Mike F. Robbins,OU=Sales,DC=mikefrobbins,DC=com
Enabled                : True
GivenName              : Mike
LastBadPasswordAttempt : 2/4/2017 10:46:15 AM
LastLogonDate          : 2/18/2017 12:45:14 AM
Name                   : Mike F. Robbins
ObjectClass            : user
ObjectGUID             : a82a8c58-1332-4a57-a6e2-68e0c750ea56
SamAccountName         : mike
SID                    : S-1-5-21-2989741381-570885089-3319121794-1108
Surname                : Robbins
UserPrincipalName      : miker@mikefrobbins.com
```

## <a name="summary"></a>요약

이 장에서는 명령이 생성하는 개체의 형식을 확인하는 방법, 명령에 사용할 수 있는 속성 및 메서드를 결정하는 방법, 기본적으로 반환되는 속성을 제한하는 명령을 사용하는 방법을 배웠습니다.

## <a name="review"></a>검토

1. `Get-Process` cmdlet은 어떤 형식의 개체를 생성하나요?
1. 명령에 사용할 수 있는 속성을 확인하려면 어떻게 해야 하나요?
1. 특정 항목을 가져오지만 동일한 항목을 설정하지는 않는 명령이 존재하는 경우 확인해야 할 사항은 무엇인가요?
1. 기본적으로 출력을 생성하지 않는 일부 명령에서 출력을 생성하도록 하려면 어떻게 해야 하나요?
1. 방대한 양의 출력을 생성하는 명령의 결과를 사용하려면 무엇을 고려해야 하나요?

## <a name="recommended-reading"></a>권장 참조 항목

- [Get-Member][]
- [개체 구조 보기(Get-Member)][]
- [about_Objects][]
- [about_Properties][]
- [about_Methods][]
- [항목을 시작 하거나 중지 하는 PowerShell Cmdlet이 없습니다. Get Cmdlet에서 메서드를 확인 하는 것을 잊지 마세요.][use-methods]

<!-- link references -->
[Windows용 RSAT]: https://support.microsoft.com/help/2693643
[Windows 관리 모듈]: /powershell/scripting/whats-new/module-compatibility#windows-management-modules
[Get-Member]: /powershell/module/microsoft.powershell.utility/get-member
[개체 구조 보기(Get-Member)]: /powershell/scripting/samples/viewing-object-structure--get-member-
[about_Objects]: /powershell/module/microsoft.powershell.core/about/about_objects
[about_Properties]: /powershell/module/microsoft.powershell.core/about/about_properties
[about_Methods]: /powershell/module/microsoft.powershell.core/about/about_methods
[use-methods]: https://mikefrobbins.com/2016/12/15/no-powershell-cmdlet-to-start-or-stop-something-dont-forget-to-check-for-methods-on-the-get-cmdlets/
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
