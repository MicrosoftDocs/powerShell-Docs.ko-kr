---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Object
ms.openlocfilehash: baaff5a02cc583394019d2fe79a1b4d6210473af
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93209689"
---
# New-Object

## 개요
Microsoft .NET Framework 또는 COM 개체의 인스턴스를 만듭니다.

## SYNTAX

### Net (기본값)

```
New-Object [-TypeName] <String> [[-ArgumentList] <Object[]>] [-Property <IDictionary>] [<CommonParameters>]
```

### C

```
New-Object [-ComObject] <String> [-Strict] [-Property <IDictionary>] [<CommonParameters>]
```

## 설명

`New-Object`Cmdlet은 .NET Framework 또는 COM 개체의 인스턴스를 만듭니다.

COM 개체의 ProgID(프로그래밍 ID)나 .NET Framework 클래스의 유형을 지정할 수 있습니다. 기본적으로 .NET Framework 클래스의 정규화된 이름을 입력하면 cmdlet은 해당 클래스의 인스턴스에 대한 참조를 반환합니다. COM 개체의 인스턴스를 만들려면 **ComObject** 매개 변수를 사용 하 고 개체의 ProgID를 해당 값으로 지정 합니다.

## 예제

### 예제 1: System.object 개체 만들기

이 예제에서는 "1.2.3.4" 문자열을 생성자로 사용 하 여 **system.object** 개체를 만듭니다.

```powershell
New-Object -TypeName System.Version -ArgumentList "1.2.3.4"
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
1      2      3      4
```

### 예제 2: Internet Explorer COM 개체 만들기

이 예제에서는 Internet Explorer 응용 프로그램을 나타내는 COM 개체의 인스턴스 두 개를 만듭니다. 첫 번째 인스턴스는 **Property** 매개 변수 해시 테이블을 사용 하 여 **Navigate2** 메서드를 호출 하 고 개체의 **visible** 속성을로 설정 하 여 `$True` 응용 프로그램이 표시 되도록 합니다.
두 번째 인스턴스는 개별 명령과 동일한 결과를 가져옵니다.

```powershell
$IE1 = New-Object -COMObject InternetExplorer.Application -Property @{Navigate2="www.microsoft.com"; Visible = $True}

# The following command gets the same results as the example above.
$IE2 = New-Object -COMObject InternetExplorer.Application`
$IE2.Navigate2("www.microsoft.com")`
$IE2.Visible = $True`
```

### 예 3: Strict 매개 변수를 사용 하 여 종료 되지 않는 오류 생성

이 예제에서는 **Strict** 매개 변수를 추가 하면 `New-Object` COM 개체에서 interop 어셈블리를 사용 하는 경우 cmdlet이 종료 되지 않는 오류를 생성 하는 것을 보여 줍니다.

```powershell
$A = New-Object -COMObject Word.Application -Strict -Property @{Visible = $True}
```

```Output
New-Object : The object written to the pipeline is an instance of the type
"Microsoft.Office.Interop.Word.ApplicationClass" from the component's primary interop assembly. If
this type exposes different members than the IDispatch members, scripts written to work with this
object might not work if the primary interop assembly is not installed.

At line:1 char:14
+ $A = New-Object  <<<< -COM Word.Application -Strict; $a.visible=$true
```

### 예제 4: Windows 데스크톱을 관리 하는 COM 개체 만들기

이 예제에서는 COM 개체를 만들고 사용하여 Windows 바탕 화면을 관리하는 방법을 보여 줍니다.

첫 번째 명령은 cmdlet의 **ComObject** 매개 변수를 사용 하 여 `New-Object` **Shell. 응용 프로그램** PROGID를 사용 하 여 COM 개체를 만듭니다. 결과 개체를 `$ObjShell` 변수에 저장 합니다. 두 번째 명령은 변수를 `$ObjShell` cmdlet으로 파이프 합니다 `Get-Member` . 그러면이 CMDLET이 COM 개체의 속성 및 메서드를 표시 합니다. 메서드 중에는 **ToggleDesktop** 메서드가 있습니다. 세 번째 명령은 개체의 **ToggleDesktop** 메서드를 호출하여 바탕 화면에 열려 있는 창을 최소화합니다.

```powershell
$Objshell = New-Object -COMObject "Shell.Application"
$objshell | Get-Member
$objshell.ToggleDesktop()
```

```Output
   TypeName: System.__ComObject#{866738b9-6cf2-4de8-8767-f794ebe74f4e}

Name                 MemberType Definition
----                 ---------- ----------
AddToRecent          Method     void AddToRecent (Variant, string)
BrowseForFolder      Method     Folder BrowseForFolder (int, string, int, Variant)
CanStartStopService  Method     Variant CanStartStopService (string)
CascadeWindows       Method     void CascadeWindows ()
ControlPanelItem     Method     void ControlPanelItem (string)
EjectPC              Method     void EjectPC ()
Explore              Method     void Explore (Variant)
ExplorerPolicy       Method     Variant ExplorerPolicy (string)
FileRun              Method     void FileRun ()
FindComputer         Method     void FindComputer ()
FindFiles            Method     void FindFiles ()
FindPrinter          Method     void FindPrinter (string, string, string)
GetSetting           Method     bool GetSetting (int)
GetSystemInformation Method     Variant GetSystemInformation (string)
Help                 Method     void Help ()
IsRestricted         Method     int IsRestricted (string, string)
IsServiceRunning     Method     Variant IsServiceRunning (string)
MinimizeAll          Method     void MinimizeAll ()
NameSpace            Method     Folder NameSpace (Variant)
Open                 Method     void Open (Variant)
RefreshMenu          Method     void RefreshMenu ()
ServiceStart         Method     Variant ServiceStart (string, Variant)
ServiceStop          Method     Variant ServiceStop (string, Variant)
SetTime              Method     void SetTime ()
ShellExecute         Method     void ShellExecute (string, Variant, Variant, Variant, Variant)
ShowBrowserBar       Method     Variant ShowBrowserBar (string, Variant)
ShutdownWindows      Method     void ShutdownWindows ()
Suspend              Method     void Suspend ()
TileHorizontally     Method     void TileHorizontally ()
TileVertically       Method     void TileVertically ()
ToggleDesktop        Method     void ToggleDesktop ()
TrayProperties       Method     void TrayProperties ()
UndoMinimizeALL      Method     void UndoMinimizeALL ()
Windows              Method     IDispatch Windows ()
WindowsSecurity      Method     void WindowsSecurity ()
WindowSwitcher       Method     void WindowSwitcher ()
Application          Property   IDispatch Application () {get}
Parent               Property   IDispatch Parent () {get}
```

### 예제 5: 생성자에 여러 인수 전달

이 예제에서는 여러 매개 변수를 사용 하는 생성자를 사용 하 여 개체를 만드는 방법을 보여 줍니다. **Argumentlist** 매개 변수를 사용 하는 경우 매개 변수를 배열에 넣어야 합니다.

```powershell
$array = @('One', 'Two', 'Three')
$parameters = @{
    TypeName = 'System.Collections.Generic.HashSet[string]'
    ArgumentList = ([string[]]$array, [System.StringComparer]::OrdinalIgnoreCase)
}
$set = New-Object @parameters
```

PowerShell은 배열의 각 멤버를 생성자의 매개 변수에 바인딩합니다.

> [!NOTE]
> 이 예제에서는 가독성을 위해 스 플랫 매개 변수를 사용 합니다. 자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.

### 예제 6: 배열을 단일 매개 변수로 사용 하는 생성자 호출

이 예제에서는 배열 또는 컬렉션인 매개 변수를 사용 하는 생성자를 사용 하 여 개체를 만드는 방법을 보여 줍니다. 배열 매개 변수는 다른 배열 내에 래핑해야 합니다.

```powershell
$array = @('One', 'Two', 'Three')
# This command throws an exception.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList $array
# This command succeeds.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList (,[string[]]$array)
$set
```

```Output
New-Object : Cannot find an overload for "HashSet`1" and the argument count: "3".
At line:1 char:8
+ $set = New-Object -TypeName 'System.Collections.Generic.HashSet[strin ...
+        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidOperation: (:) [New-Object], MethodException
+ FullyQualifiedErrorId : ConstructorInvokedThrowException,Microsoft.PowerShell.Commands.NewObjectCommand

One
Two
Three
```

이 예제에서 개체를 만드는 첫 번째 시도가 실패 합니다. PowerShell에서 세 개의 멤버를 `$array` 생성자의 매개 변수에 바인딩하려고 했지만 생성자는 세 개의 매개 변수를 사용 하지 않습니다. `$array`다른 배열로 래핑하여 PowerShell에서의 세 멤버를 `$array` 생성자의 매개 변수에 바인딩하지 못하게 합니다.

## PARAMETERS

### -ArgumentList

.NET Framework 클래스의 생성자에 전달할 인수의 배열을 지정 합니다. 생성자가 배열인 단일 매개 변수를 사용 하는 경우 해당 매개 변수를 다른 배열 내에 래핑해야 합니다. 다음은 그 예입니다. 

`$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate -ArgumentList (,$bytes)`

**Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays)를 참조 하세요.

**ArgumentList** 의 별칭은 **Args** 입니다.

```yaml
Type: System.Object[]
Parameter Sets: Net
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComObject

COM 개체의 ProgID(프로그래밍 ID)를 지정합니다.

```yaml
Type: System.String
Parameter Sets: Com
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -속성

속성 값을 설정하고 새 개체의 메서드를 호출합니다.

키가 속성 또는 메서드의 이름이고 값이 속성 값이나 메서드 인수인 해시 테이블을 입력합니다. `New-Object` 개체를 만들고 각 속성 값을 설정 하 고 해시 테이블에 나타나는 순서 대로 각 메서드를 호출 합니다.

새 개체가 **PSObject** 클래스에서 파생 되 고 개체에 존재 하지 않는 속성을 지정 하는 경우는 지정 된 속성을 `New-Object` 개체에 메모 속성으로 추가 합니다. 개체가 **PSObject** 가 아닌 경우 명령은 종료 되지 않는 오류를 생성 합니다.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Strict

만들려는 COM 개체에서 interop 어셈블리를 사용 하는 경우 cmdlet에서 종료 되지 않는 오류를 생성 함을 나타냅니다. 이 기능은 실제 COM 개체를 COM 호출 가능 래퍼를 사용하는 .NET Framework 개체와 구분합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Com
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

.NET Framework 클래스의 정규화된 이름을 지정합니다. **TypeName** 매개 변수와 **ComObject** 매개 변수를 모두 지정할 수는 없습니다.

```yaml
Type: System.String
Parameter Sets: Net
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### Object

`New-Object` 만들어진 개체를 반환 합니다.

## 참고

- `New-Object` VBScript CreateObject 함수에서 가장 일반적으로 사용 되는 기능을 제공 합니다. VBScript에서와 같은 문은 `Set objShell = CreateObject("Shell.Application")` PowerShell에서로 변환할 수 있습니다 `$objShell = New-Object -COMObject "Shell.Application"` .
- `New-Object` 는 명령줄 및 스크립트 내에서 .NET Framework 개체를 쉽게 사용할 수 있도록 하 여 Windows 스크립트 호스트 환경에서 사용할 수 있는 기능을 확장 합니다.

## 관련 링크

[about_Object_Creation](../Microsoft.PowerShell.Core/About/about_Object_Creation.md)

[Compare-Object](Compare-Object.md)

[Group-Object](Group-Object.md)

[Measure-Object](Measure-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Tee-Object](Tee-Object.md)
