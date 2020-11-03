---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-member?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Member
ms.openlocfilehash: 56f5d62115474a9791e139646383b1ae725664bc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216657"
---
# Get-Member

## 개요
개체의 속성 및 메서드를 가져옵니다.

## SYNTAX

```
Get-Member [-InputObject <PSObject>] [[-Name] <String[]>] [-MemberType <PSMemberTypes>]
 [-View <PSMemberViewTypes>] [-Static] [-Force] [<CommonParameters>]
```

## 설명

`Get-Member`Cmdlet은 개체의 멤버, 속성 및 메서드를 가져옵니다.

개체를 지정 하려면 **InputObject** 매개 변수를 사용 하거나 개체를로 파이프 `Get-Member` 합니다. 정적 멤버에 대 한 정보를 얻기 위해 인스턴스가 아닌 클래스의 멤버는 **static** 매개 변수를 사용 합니다. **참고 속성과** 같은 특정 유형의 멤버만 가져오려면 **MemberType** 매개 변수를 사용 합니다.

## 예제

### 예제 1: 프로세스 개체의 멤버 가져오기

이 명령은 cmdlet에 의해 생성 된 서비스 개체의 속성 및 메서드를 표시 합니다 `Get-Service` .

`Get-Member`명령의 일부에는 매개 변수가 없으므로 매개 변수에 대 한 기본값을 사용 합니다. 기본적으로는 `Get-Member` 정적 또는 내장 멤버를 가져오지 않습니다.

```powershell
Get-Service | Get-Member
```

```Output
   TypeName: System.Service.ServiceController#StartupType

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, System.EventArgs)
Close                     Method        void Close()
Continue                  Method        void Continue()
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
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.ServiceControllerSt...
BinaryPathName            Property      System.String {get;set;}
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DelayedAutoStart          Property      System.Boolean {get;set;}
DependentServices         Property      System.ServiceProcess.ServiceController[] DependentServices {get;}
Description               Property      System.String {get;set;}
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle ServiceHandle {get;}
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] ServicesDependedOn {get;}
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType {get;}
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartType {get;}
StartupType               Property      Microsoft.PowerShell.Commands.ServiceStartupType {get;set;}
Status                    Property      System.ServiceProcess.ServiceControllerStatus Status {get;}
UserName                  Property      System.String {get;set;}
ToString                  ScriptMethod  System.Object ToString();
```

### 예제 2: 서비스 개체의 멤버 가져오기

이 예제에서는 `Get-Service` **psbase** , **PSObject** , **get_** 및 **set_** 메서드와 같은 내장 멤버를 포함 하 여 cmdlet에서 검색 된 서비스 개체의 모든 멤버 (속성 및 메서드)를 가져옵니다.

```powershell
Get-Service | Get-Member -Force
(Get-Service Schedule).PSBase
```

이 `Get-Member` 명령은 **Force** 매개 변수를 사용 하 여 개체의 내장 멤버 및 컴파일러에서 생성 된 멤버를 표시에 추가 합니다. 이러한 속성 및 메서드는 조정된 개체 메서드를 사용하는 것과 같은 방식으로 사용할 수 있습니다. 두 번째 명령은 Schedule 서비스의 PSBase 속성 값을 표시하는 방법을 보여 줍니다.

### 예제 3: 서비스 개체의 확장 멤버 가져오기

이 예제에서는 파일이 나 cmdlet을 사용 하 여 확장 된 서비스 개체의 메서드 및 속성을 가져옵니다 `Types.ps1xml` `Add-Member` .

```powershell
Get-Service | Get-Member -View Extended
```

```Output
   TypeName: System.Service.ServiceController#StartupType

Name             MemberType    Definition
----             ----------    ----------
Name             AliasProperty Name = ServiceName
RequiredServices AliasProperty RequiredServices = ServicesDependedOn
ToString         ScriptMethod  System.Object ToString();
```

이 `Get-Member` 명령은 **View** 매개 변수를 사용 하 여 서비스 개체의 확장 된 멤버만 가져옵니다. 이 경우 확장 멤버는 **ServiceName** 속성의 별칭 속성인 **Name** 속성입니다.

### 예 4: 이벤트 로그 개체의 스크립트 속성 가져오기

이 예에서는 이벤트 뷰어의 시스템 로그에 있는 이벤트 로그 개체의 스크립트 속성을 가져옵니다.

```powershell
Get-WinEvent -LogName System -MaxEvents 1 | Get-Member -MemberType NoteProperty
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.EventLogRecord

Name    MemberType   Definition
----    ----------   ----------
Message NoteProperty string Message=The machine-default permission settings do not grant Local ...
```

**MemberType** 매개 변수는 `NoteProperty` **MemberType** 속성에 대 한 값이 인 개체만 가져옵니다.

이 명령은 **EventLogRecord** 개체의 **메시지** 속성을 반환 합니다.

### 예 5: 지정 된 속성을 사용 하 여 개체 가져오기

이 예제에서는 cmdlet 목록의 출력에 **MachineName** 속성이 있는 개체를 가져옵니다.

`$list`변수는 평가할 cmdlet의 목록을 포함 합니다. **Foreach** 문은 각 명령을 호출 하 고 결과를로 보냅니다 `Get-Member` . **Name** 매개 변수는의 결과를 `Get-Member` **MachineName** 이름이 인 멤버로 제한 합니다.

```powershell
$list = "Get-Process", "Get-Service", "Get-Culture", "Get-PSDrive", "Get-ExecutionPolicy"
foreach ($cmdlet in $list) {& $cmdlet | Get-Member -Name MachineName}
```

```Output
   TypeName: System.Diagnostics.Process

Name        MemberType Definition
----        ---------- ----------
MachineName Property   string MachineName {get;}

   TypeName: System.Service.ServiceController#StartupType

Name        MemberType Definition
----        ---------- ----------
MachineName Property   string MachineName {get;set;}
```

결과에는 프로세스 개체와 서비스 개체만 **MachineName** 속성이 있음을 보여 줍니다.

### 예제 6: 배열에 대 한 멤버 가져오기

이 예제에서는 개체 배열의 멤버를 찾는 방법을 보여 줍니다. 개체를로 파이프 하 고 배열 하면 `Get-Member` 이 cmdlet은 배열의 각 고유 개체 형식에 대 한 멤버 목록을 반환 합니다.
**InputObject** 매개 변수를 사용 하 여 배열을 전달 하면 배열이 단일 개체로 처리 됩니다.

```powershell
$array = @(1,'hello')
$array | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType Definition
----        ---------- ----------
CompareTo   Method     int CompareTo(System.Object value), int CompareTo(int value), int ICompar...
Equals      Method     bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int...
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
GetTypeCode Method     System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method     bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method     byte IConvertible.ToByte(System.IFormatProvider provider)
...

   TypeName: System.String

Name                 MemberType            Definition
----                 ----------            ----------
Clone                Method                System.Object Clone(), System.Object ICloneable.Clone()
CompareTo            Method                int CompareTo(System.Object value), int CompareTo(str...
Contains             Method                bool Contains(string value), bool Contains(string val...
CopyTo               Method                void CopyTo(int sourceIndex, char[] destination, int ...
EndsWith             Method                bool EndsWith(string value), bool EndsWith(string val...
EnumerateRunes       Method                System.Text.StringRuneEnumerator EnumerateRunes()
Equals               Method                bool Equals(System.Object obj), bool Equals(string va...
GetEnumerator        Method                System.CharEnumerator GetEnumerator(), System.Collect...
GetHashCode          Method                int GetHashCode(), int GetHashCode(System.StringCompa...
...
```

```powershell
Get-Member -InputObject $array
```

```Output
   TypeName: System.Object[]

Name           MemberType            Definition
----           ----------            ----------
Add            Method                int IList.Add(System.Object value)
Address        Method                System.Object&, System.Private.CoreLib, Version=4.0.0.0, Cu...
Clear          Method                void IList.Clear()
Clone          Method                System.Object Clone(), System.Object ICloneable.Clone()
CompareTo      Method                int IStructuralComparable.CompareTo(System.Object other, Sy...
...
```

`$array`변수는 배열이 파이프 될 때 표시 되는 것 처럼 **Int32** 개체 및 **문자열** 개체를 포함 합니다 `Get-Member` . `$array` **InputObject** 매개 변수를 사용 하 여이 전달 되 면 `Get-Member` **Object []** 형식의 멤버를 반환 합니다.

### 예 7: 설정할 수 있는 개체 속성 확인

이 예제에서는 변경할 수 있는 개체의 속성을 결정하는 방법을 보여 줍니다.

```powershell
$File = Get-Item c:\test\textFile.txt
$File.PSObject.Properties | Where-Object isSettable | Select-Object -Property Name
```

```Output
Name
----
PSPath
PSParentPath
PSChildName
PSDrive
PSProvider
PSIsContainer
IsReadOnly
CreationTime
CreationTimeUtc
LastAccessTime
LastAccessTimeUtc
LastWriteTime
LastWriteTimeUtc
Attributes
```

## PARAMETERS

### -Force

내장 멤버 및 컴파일러에서 생성 된 **get_** 및 **set_** 메서드를 표시에 추가 합니다.
다음 목록에서는 **Force** 매개 변수를 사용할 때 추가 되는 속성에 대해 설명 합니다.

- **Psbase** : 확장 또는 조정 하지 않는 .net 개체의 원래 속성입니다. 이러한 속성은 개체 클래스에 대해 정의 된 속성입니다.
- **Psadapted** . PowerShell 확장 유형 시스템에 정의 된 속성 및 메서드입니다.
- **PSExtended** . 파일에 추가 `Types.ps1xml` 되었거나 cmdlet을 사용 하 여 추가 된 속성 및 메서드입니다 `Add-Member` .
- **PSObject** . 기본 개체를 PowerShell **PSObject** 개체로 변환 하는 어댑터입니다.
- **PSTypeNames** . 구체적인 순서로 개체를 설명하는 개체 유형 목록입니다. 개체의 형식을 지정할 때 PowerShell `Format.ps1xml` 은 powershell 설치 디렉터리 ()의 파일에서 형식을 검색 `$PSHOME` 합니다. 가장 먼저 발견되는 유형의 형식 지정 정의를 사용합니다.

기본적으로는 `Get-Member` **기본** 및 조정 된 항목을 제외한 모든 보기 **Adapted** 에서 이러한 속성을 가져오며 표시 하지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

해당 멤버를 검색할 개체를 지정합니다.

**InputObject** 매개 변수를 사용 하는 것은 개체를로 파이프 하는 것과 다릅니다 `Get-Member` . 차이점은 다음과 같습니다.

- 개체의 컬렉션을로 파이프 하는 `Get-Member` 경우 `Get-Member` 컬렉션에 있는 개별 개체의 멤버 (예: 문자열 배열에 있는 각 문자열의 속성)를 가져옵니다.
- **InputObject** 를 사용 하 여 개체 컬렉션을 제출 하는 경우 `Get-Member` 문자열 배열에서 배열의 속성과 같은 컬렉션의 멤버를 가져옵니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MemberType

이 cmdlet이 가져오는 멤버 유형을 지정 합니다. 기본값은 **All** 입니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- AliasProperty
- CodeProperty
- 속성
- NoteProperty
- ScriptProperty
- 속성
- PropertySet
- 메서드
- CodeMethod
- ScriptMethod
- 메서드
- ParameterizedProperty
- 집합
- 이벤트
- 동적
- 모두

이러한 값에 대 한 자세한 내용은 [PSMemberTypes 열거형](/dotnet/api/system.management.automation.psmembertypes)을 참조 하세요.

모든 개체가 모든 멤버 유형을 포함하는 것은 아닙니다. 개체에 없는 멤버 유형을 지정 하는 경우 PowerShell은 null 값을 반환 합니다.

모든 확장된 멤버와 같이 멤버의 관련 형식을 가져오려면 **View** 매개 변수를 사용합니다. **MemberType** 매개 변수를 **Static** 또는 **View** 매개 변수와 함께 사용 하는 경우 `Get-Member` 두 집합에 모두 속하는 멤버를 가져옵니다.

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

개체의 속성 또는 메서드 이름을 하나 이상 지정합니다. `Get-Member` 지정 된 속성 및 메서드만 가져옵니다.

**Name** 매개 변수를 **MemberType** , **View** 또는 **Static** 매개 변수와 함께 사용 하는 경우 `Get-Member` 모든 매개 변수의 조건을 충족 하는 멤버만 가져옵니다.

정적 멤버를 이름별로 가져오려면 **static** 매개 변수를 **name** 매개 변수와 함께 사용 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Static

이 cmdlet은 개체의 정적 속성 및 메서드만 가져옵니다. 정적 속성 및 메서드는 클래스의 특정 인스턴스가 아닌 개체의 클래스에 정의됩니다.

**Static** 매개 변수를 **view** 매개 변수와 함께 사용 하는 경우 **view** 매개 변수는 무시 됩니다.
**MemberType** 매개 변수를 사용 하 여 **Static** 매개 변수를 사용 하는 경우는 `Get-Member` 두 집합에 모두 속하는 멤버만 가져옵니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -보기

이 cmdlet이 특정 형식의 속성 및 메서드만을 가져오는 것으로 지정 합니다. 하나 이상의 값을 지정합니다. 기본값 **은 조정 됨** , **확장** 됨입니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- 밑입니다. .NET 개체의 원래 속성 및 메서드만 가져옵니다 (확장 또는 적응 없음).
- 적용. PowerShell 확장 유형 시스템에 정의 된 속성 및 메서드만 가져옵니다.
- 확장이. 파일에 추가 `Types.ps1xml` 되었거나 cmdlet을 사용 하 여 추가 된 속성 및 메서드만 가져옵니다 `Add-Member` .
- 모두. Base, Adapted 및 Extended 보기의 멤버를 가져옵니다.

**View** 매개 변수는 해당 멤버를 표시 하는 것이 아니라 검색 된 멤버를 결정 합니다.

스크립트 속성과 같은 특정 멤버 유형을 가져오려면 **MemberType** 매개 변수를 사용 합니다. 동일한 명령에서 **MemberType** 및 **View** 매개 변수를 사용 하는 경우 `Get-Member` 두 집합에 모두 속하는 멤버를 가져옵니다. 동일한 명령에서 **Static** 및 **view** 매개 변수를 사용 하는 경우 **view** 매개 변수는 무시 됩니다.

```yaml
Type: System.Management.Automation.PSMemberViewTypes
Parameter Sets: (All)
Aliases:
Accepted values: Extended, Adapted, Base, All

Required: False
Position: Named
Default value: Adapted, Extended
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

모든 개체를로 파이프 할 수 있습니다 `Get-Member` .

## 출력

### Microsoft. PowerShell. MemberDefinition

`Get-Member` 가 가져오는 각 속성 또는 메서드에 대 한 개체를 반환 합니다.

## 참고

**InputObject** 매개 변수를 사용 하거나 쉼표를 앞에 오는 개체를로 파이프 하 여 컬렉션 개체에 대 한 정보를 가져올 수 있습니다 `Get-Member` .

`$This`새 속성 및 메서드의 값을 정의 하는 스크립트 블록에서 자동 변수를 사용할 수 있습니다. `$This`변수는 속성 및 메서드가 추가 되는 개체의 인스턴스를 참조 합니다. 변수에 대 한 자세한 내용은 `$This` [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)를 참조 하세요.

형식 리터럴 (예:)과 같은 _형식을_ 나타내는 개체를 전달 하는 `[int]` 경우 `Get-Member` 해당 형식에 대 한 정보를 반환 `[System.RuntimeType]` 합니다. 그러나 **정적** 매개 변수를 사용 하는 경우 `Get-Member` 인스턴스에서 나타내는 특정 형식의 정적 멤버를 반환 합니다 `System.RuntimeType` .

## 관련 링크

[Add-Member](Add-Member.md)
