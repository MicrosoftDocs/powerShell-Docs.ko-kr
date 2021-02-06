---
title: PowerShell 원격 기능
description: 다양한 방법으로 PowerShell의 원격 컴퓨터에 대한 명령을 실행할 수 있습니다.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 0e467a41282b261c56a89578dbc841725f59a6e0
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99601039"
---
# <a name="chapter-8---powershell-remoting"></a>8장 - PowerShell 원격 기능

PowerShell에서는 다양한 방법으로 원격 컴퓨터에 대한 명령을 실행할 수 있습니다. 지난 장에서는 CIM cmdlet을 사용하여 WMI를 원격으로 쿼리하는 방법을 살펴보았습니다. PowerShell은 기본 제공 **ComputerName** 매개 변수가 있는 다양한 cmdlet도 제공합니다.

다음 예제에서처럼 `Get-Command`를 **ParameterName** 매개 변수와 함께 사용하면 **ComputerName** 매개 변수가 있는 명령을 확인합니다.

```powershell
Get-Command -ParameterName ComputerName
```

```Output
CommandType Name                        Version Source
----------- ----                        ------- ------
Cmdlet      Connect-PSSession           7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Connect-WSMan               7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Disconnect-WSMan            7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Enter-PSSession             7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Get-CimAssociatedInstance   7.0.0.0 CimCmdlets
Cmdlet      Get-CimClass                7.0.0.0 CimCmdlets
Cmdlet      Get-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      Get-CimSession              7.0.0.0 CimCmdlets
Cmdlet      Get-Counter                 7.0.0.0 Microsoft.PowerShell.Diagnostics
Cmdlet      Get-HotFix                  7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Get-PSSession               7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Get-WinEvent                7.0.0.0 Microsoft.PowerShell.Diagnostics
Cmdlet      Get-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Invoke-CimMethod            7.0.0.0 CimCmdlets
Cmdlet      Invoke-Command              7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Invoke-WSManAction          7.0.0.0 Microsoft.WSMan.Management
Cmdlet      New-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      New-CimSession              7.0.0.0 CimCmdlets
Cmdlet      New-PSSession               7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      New-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Receive-Job                 7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Receive-PSSession           7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Register-CimIndicationEvent 7.0.0.0 CimCmdlets
Cmdlet      Remove-CimInstance          7.0.0.0 CimCmdlets
Cmdlet      Remove-CimSession           7.0.0.0 CimCmdlets
Cmdlet      Remove-PSSession            7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Remove-WSManInstance        7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Rename-Computer             7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Restart-Computer            7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Send-MailMessage            7.0.0.0 Microsoft.PowerShell.Utility
Cmdlet      Set-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      Set-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Stop-Computer               7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Test-Connection             7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Test-WSMan                  7.0.0.0 Microsoft.WSMan.Management
```

`Get-Process`와 `Get-Hotfix` 같은 명령에는 **ComputerName** 매개 변수가 존재합니다. 원격 컴퓨터에 대한 명령을 실행하는 Microsoft의 장기적 접근법은 아닙니다. **ComputerName** 매개 변수가 있는 명령을 찾았더라도 다른 자격 증명을 지정해야 하며 **Credential** 매개 변수가 없을 확률이 높습니다. 그리고 승격된 계정에서 PowerShell을 실행하면 사용자와 원격 컴퓨터 사이의 방화벽이 요청을 차단할 수 있습니다.

이 장에서 제시되는 PowerShell 원격 명령을 사용하려면 원격 컴퓨터에서 PowerShell 원격 기능을 사용 설정해야 합니다. PowerShell 원격 기능을 사용하려면 `Enable-PSRemoting` cmdlet을 사용하세요.

```powershell
Enable-PSRemoting
```

```Output
WinRM has been updated to receive requests.
WinRM service type changed successfully.
WinRM service started.

WinRM has been updated for remote management.
WinRM firewall exception enabled.
```

## <a name="one-to-one-remoting"></a>일대일 원격 작업

대화형 원격 세션을 만들려면 일대일 원격 작업을 선택하면 됩니다.
이 유형의 원격 작업은 `Enter-PSSession` cmdlet으로 제공됩니다.

지난 장에서 필자는 도메인 관리자 자격 증명을 `$Cred`라는 변수에 저장했습니다. 아직 수행하지 않았다면 도메인 관리자 자격 증명을 `$Cred` 변수에 저장하세요.

이렇게 하면 자격 증명을 한 번만 입력하면 현재 PowerShell 세션이 비활성화될 때까지 명령별로 계속 사용할 수 있습니다.

```powershell
$Cred = Get-Credential
```

dc01이라는 도메인 컨트롤러에 대한 일대일 PowerShell 원격 작업 세션을 만드세요.

```powershell
Enter-PSSession -ComputerName dc01 -Credential $Cred
```

```Output
[dc01]: PS C:\Users\Administrator\Documents>
```

앞의 예제에서는 PowerShell 프롬프트 앞에 `[dc01]`이 옵니다. dc01이라는 원격 컴퓨터에 대한 대화형 PowerShell 세션에 있다는 뜻입니다. 실행하는 모든 명령은 로컬 컴퓨터가 아닌 dc01에서 실행됩니다. 또한 로컬 컴퓨터가 아닌 원격 컴퓨터에 있는 PowerShell 명령에만 액세스할 수 있다는 점을 명심해야 합니다. 즉 컴퓨터에 추가 모듈을 설치한다면 추가 모듈은 원격 컴퓨터에서 액세스할 수 없습니다.

일대일 대화형 PowerShell 원격 작업 세션을 통해 원격 컴퓨터에 연결되었다면 사실상 원격 컴퓨터에 있는 것과 같습니다. 개체는 이 책 전체에서 다루는 것과 같은 일반 개체입니다.

```powershell
[dc01]:  Get-Process | Get-Member
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
[dc01]:
```

원격 컴퓨터 관련 작업이 끝났다면 `Exit-PSSession` cmdlet을 이용해 일대일 원격 작업 세션을 종료하세요.

```powershell
[dc01]:  Exit-PSSession
```

## <a name="one-to-many-remoting"></a>일대다 원격 작업

원격 컴퓨터에서 대화형으로 작업을 수행해야 할 때도 있습니다. 하지만 작업을 여러 원격 컴퓨터에서 동시에 수행할 수 있다면 원격 작업이 훨씬 더 강력해집니다. `Invoke-Command` cmdlet을 사용하여 하나 이상의 원격 컴퓨터를 대상으로 동시에 명령을 실행하세요.

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

이전 예제에서는 Windows 시간 서비스의 상태를 서버 3개에서 쿼리했습니다. `Get-Service` cmdlet은 `Invoke-Command`의 스크립트 블록 내에 배치되었습니다. `Get-Service`는 실제로 원격 컴퓨터에서 실행되며 결과는 로컬 컴퓨터에 역직렬화한 개체로 반환됩니다.

이전 명령을 `Get-Member`에 파이프하면 결과가 실제로 역직렬화된 개체임을 알 수 있습니다.

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred | Get-Member
```

```Output
   TypeName: Deserialized.System.ServiceProcess.ServiceController

Name                MemberType   Definition
----                ----------   ----------
GetType             Method       type GetType()
ToString            Method       string ToString(), string ToString(string format, Sys...
Name                NoteProperty string Name=W32time
PSComputerName      NoteProperty string PSComputerName=sql02
PSShowComputerName  NoteProperty bool PSShowComputerName=True
RequiredServices    NoteProperty Deserialized.System.ServiceProcess.ServiceController[...
RunspaceId          NoteProperty guid RunspaceId=570313c4-ac84-4109-bf67-c6b33236af0a
CanPauseAndContinue Property     System.Boolean {get;set;}
CanShutdown         Property     System.Boolean {get;set;}
CanStop             Property     System.Boolean {get;set;}
Container           Property      {get;set;}
DependentServices   Property     Deserialized.System.ServiceProcess.ServiceController[...
DisplayName         Property     System.String {get;set;}
MachineName         Property     System.String {get;set;}
ServiceHandle       Property     System.String {get;set;}
ServiceName         Property     System.String {get;set;}
ServicesDependedOn  Property     Deserialized.System.ServiceProcess.ServiceController[...
ServiceType         Property     System.String {get;set;}
Site                Property      {get;set;}
StartType           Property     System.String {get;set;}
Status              Property     System.String {get;set;}
```

대부분의 메서드에는 역직렬화된 개체가 없음에 주목하세요. 라이브 개체가 아니라 비활성 개체라는 뜻입니다. 역직렬화된 개체를 사용하여 서비스를 시작하거나 중지할 수는 없습니다.원격 컴퓨터에서 명령을 실행한 순간의 개체 상태 스냅샷이기 때문입니다.

하지만 `Invoke-Command`가 있는 메서드로 서비스를 시작하거나 중지할 수 없다는 뜻은 아닙니다. 메서드를 원격 세션에서 호출해야 한다는 뜻일 뿐입니다.

이를 증명하기 위해 **Stop()** 메서드를 사용하여 원격 서버 3개 모두에서 Windows 시간 서비스를 중지하겠습니다.

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {(Get-Service -Name W32time).Stop()} -Credential $Cred
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

이전 장에서 설명했듯이 작업을 완수할 수 있는 cmdlet이 있다면 메서드 대신 이 cmdlet 사용을 권장합니다. 앞의 시나리오에서는 stop 메서드 대신 `Stop-Service` cmdlet을 사용하는 것이 좋습니다. 필자는 **Stop()** 메서드를 사용하여 이 점을 증명했습니다. 많은 사람들이 PowerShell 원격 작업을 사용할 때는 메서드를 호출할 수 없다고 착각하기 때문입니다. 역직렬화되기 때문에 반환되는 개체에서는 호출할 수 없지만 원격 세션 자체에서는 호출할 수 있습니다.

## <a name="powershell-sessions"></a>PowerShell 세션

이전 섹션의 마지막 예제에서는 `Invoke-Command` cmdlet을 사용하여 명령 두 개를 실행했습니다.
두 가지 명령을 실행하려면 개별 세션 두 개를 설정하고 분리해야 한다는 뜻입니다.

7장에서 설명하는 CIM 세션처럼, 원격 컴퓨터에 대한 PowerShell 세션에서는 명령별로 새 세션을 만들지 않고도 원격 데이터를 대상으로 여러 명령을 실행할 수 있습니다.

이 장에서 다루는 컴퓨터 3대인 DC01, SQL02, WEB01 각각에 대한 PowerShell 세션을 만드세요.

```powershell
$Session = New-PSSession -ComputerName dc01, sql02, web01 -Credential $Cred
```

이제 `$Session`이라는 변수를 사용하여 메서드를 이용해 Windows 시간 서비스를 시작하고 서비스의 상태를 확인하세요.

```powershell
Invoke-Command -Session $Session {(Get-Service -Name W32time).Start()}
Invoke-Command -Session $Session {Get-Service -Name W32time}
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

다른 자격 증명으로 세션을 만들었다면 명령이 실행될 때마다 자격 증명을 지정하지 않아도 됩니다.

세션 사용이 끝나면 세션을 반드시 제거해야 합니다.

```powershell
Get-PSSession | Remove-PSSession
```

## <a name="summary"></a>요약

이 장에서는 PowerShell 원격 작업의 개념, 원격 컴퓨터 1대를 사용하여 대화형 세션에서 명령을 실행하는 방법, 일대다 원격 작업을 사용하여 여러 컴퓨터를 대상으로 명령을 실행하는 방법을 알아보았습니다. 또한 같은 원격 컴퓨터를 대상으로 여러 명령을 실행할 때 PowerShell 세션을 사용하면 어떤 이점이 있는지도 살펴보았습니다.

## <a name="review"></a>검토

1. PowerShell 원격 작업을 사용 설정하려면 어떻게 해야 하나요?
1. 원격 컴퓨터를 사용하여 대화형 세션을 시작하는 PowerShell 명령은 무엇인가요?
1. 각각의 명령을 이용해 컴퓨터 이름을 지정하는 방법과 비교하면 PowerShell 원격 작업 세션 사용에는 어떤 이점이 있나요?
1. PowerShell 원격 작업 세션을 일대일 원격 작업 세션과 함께 사용할 수 있나요?
1. cmdlet에서 반환하는 개체 유형과 같은 cmdlet을 `Invoke-Command`를 사용하여 원격 컴퓨터를 대상으로 실행했을 때 반환되는 개체 유형의 차이는 무엇인가요?

## <a name="recommended-reading"></a>권장 참조 항목

- [about_Remote][]
- [about_Remote_FAQ][]
- [about_Remote_Output][]
- [about_Remote_Requirements][]
- [about_Remote_Troubleshooting][]
- [about_Remote_Variables][]

<!-- link references -->
[about_Remote]: /powershell/module/microsoft.powershell.core/about/about_remote
[about_Remote_FAQ]: /powershell/module/microsoft.powershell.core/about/about_remote_faq
[about_Remote_Output]: /powershell/module/microsoft.powershell.core/about/about_remote_output
[about_Remote_Requirements]: /powershell/module/microsoft.powershell.core/about/about_remote_requirements
[about_Remote_Troubleshooting]: /powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting
[about_Remote_Variables]: /powershell/module/microsoft.powershell.core/about/about_remote_variables
[Breaking changes in PowerShell 6.0]: /powershell/scripting/whats-new/breaking-changes-ps6#remove--protocol-from--computer-cmdlets-5277
