---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: .NET 및 COM 개체 만들기(New-Object)
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: ef8215303aacd90536d3c2ae57bc3629e202f318
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086373"
---
# <a name="creating-net-and-com-objects-new-object"></a>.NET 및 COM 개체 만들기(New-Object)

많은 시스템 관리 작업을 수행할 수 있게 해주는 .NET Framework 및 COM 인터페이스를 가진 소프트웨어 구성 요소가 있습니다. Windows PowerShell을 통해 이러한 구성 요소를 사용할 수 있으므로 cmdlet을 사용하여 수행할 수 있는 작업으로 제한되지 않습니다. Windows PowerShell 초기 릴리스에 포함된 많은 cmdlet은 원격 컴퓨터에 대해 작동하지 않습니다. Windows PowerShell에서 직접 .NET Framework **System.Diagnostics.EventLog** 클래스를 사용하여 이벤트 로그 관리 시 이 제한을 해결하는 방법을 보여 드리겠습니다.

## <a name="using-new-object-for-event-log-access"></a>이벤트 로그 액세스에 New-Object 사용

.NET Framework 클래스 라이브러리에는 이벤트 로그 관리에 사용할 수 있는 **System.Diagnostics.EventLog** 클래스가 포함되어 있습니다. **TypeName** 매개 변수와 함께 **New-Object** cmdlet을 사용하면 NET Framework 클래스의 새 인스턴스를 만들 수 있습니다. 예를 들어 다음 명령은 이벤트 로그 참조를 만듭니다.

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

명령에서 EventLog 클래스 인스턴스를 만들었지만 해당 인스턴스에는 데이터가 없습니다. 이는 특정 이벤트 로그를 지정하지 않았기 때문입니다. 실제 이벤트 로그를 가져오려면 어떻게 해야 할까요?

### <a name="using-constructors-with-new-object"></a>New-Object와 함께 생성자 사용

특정 이벤트 로그를 참조하려면 로그 이름을 지정해야 합니다. **New-Object**에는 **ArgumentList** 매개 변수가 있습니다. 이 매개 변수에 값으로 전달하는 인수는 개체의 특수 시작 메서드에서 사용됩니다. 메서드는 개체를 생성하는 데 사용되기 때문에 *생성자*라고 합니다. 예를 들어 애플리케이션 로그에 대한 참조를 가져오려면 'Application' 문자열을 인수로 지정합니다.

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> 대부분의 .NET Framework 핵심 클래스는 시스템 네임스페이스에 포함되어 있으므로 Windows PowerShell은 지정한 형식 이름과 일치하는 항목을 찾을 수 없을 경우 자동으로 System 네임스페이스에서 지정한 클래스를 찾으려고 합니다. 즉, System.Diagnostics.EventLog 대신 Diagnostics.EventLog를 지정할 수 있습니다.

### <a name="storing-objects-in-variables"></a>변수에 개체 저장

현재 셸에서 사용할 수 있도록 개체 참조를 저장할 수 있습니다. Windows PowerShell에서는 파이프라인으로 많은 작업을 수행할 수 있지만 때로는 변수에 개체 참조를 저장하는 것이 해당 개체를 조작하는 데 더 편리합니다.

Windows PowerShell을 사용하면 기본적으로 명명된 개체인 변수를 만들 수 있습니다. 모든 유효한 Windows PowerShell 명령의 출력을 변수에 저장할 수 있습니다. 변수 이름은 항상 $로 시작합니다. 애플리케이션 로그 참조를 $AppLog라는 변수에 저장하려는 경우 변수 이름과 등호를 차례로 입력하고 애플리케이션 로그 개체를 만드는 데 사용되는 명령을 입력합니다.

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

그런 다음 $AppLog를 입력하면 애플리케이션 로그가 포함되어 있는 것을 확인할 수 있습니다.

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

### <a name="accessing-a-remote-event-log-with-new-object"></a>New-Object를 사용하여 원격 이벤트 로그 액세스

이전 섹션에서 사용된 명령은 로컬 컴퓨터를 대상으로 합니다. **Get-EventLog** cmdlet으로 이 작업을 수행할 수 있습니다. 원격 컴퓨터의 애플리케이션 로그에 액세스하려면 로그 이름과 컴퓨터 이름(또는 IP 주소)을 인수로 둘 다 제공해야 합니다.

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

이벤트 로그에 대한 참조를 $RemoteAppLog 변수에 저장한 후 어떤 작업을 수행할 수 있을까요?

### <a name="clearing-an-event-log-with-object-methods"></a>개체 메서드를 사용하여 이벤트 로그 지우기

개체에 작업을 수행하기 위해 호출할 수 있는 메서드가 있는 경우가 많습니다. **Get-Member**를 사용하여 개체와 연결된 메서드를 표시할 수 있습니다. 다음 명령과 선택한 출력은 EventLog 클래스의 일부 메서드를 보여 줍니다.

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

**Clear()** 메서드를 사용하여 이벤트 로그를 지울 수 있습니다. 메서드를 호출할 때는 메서드에 인수가 필요하지 않는 경우에도 메서드 이름 뒤에 항상 괄호를 추가해야 합니다. 이렇게 하면 Windows PowerShell에서 메서드와 동일한 이름을 가진 잠재적인 속성을 구분합니다. 다음과 같이 입력하여 **Clear** 메서드를 호출합니다.

```
PS> $RemoteAppLog.Clear()
```

다음과 같이 입력하여 로그를 표시합니다. 이벤트 로그가 지워지고 이제 262개가 아니라 0개 항목이 있는 것을 확인할 수 있습니다.

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

## <a name="creating-com-objects-with-new-object"></a>New-Object를 사용하여 COM 개체 만들기
**New-Object**를 사용하여 COM(구성 요소 개체 모델) 구성 요소로 작업할 수 있습니다. 구성 요소는 WSH(Windows 스크립트 호스트)에 포함된 다양한 라이브러리부터 대부분의 시스템에 설치되어 있는 Internet Explorer와 같은 ActiveX 애플리케이션에 이르기까지 다양합니다.

**New-Object**는 .NET Framework 런타임 호출 가능 래퍼를 사용하여 COM 개체를 만들기 때문에 .NET Framework에서 COM 개체를 호출할 때와 동일한 제한 사항이 있습니다. COM 개체를 만들려면 사용하려는 COM 클래스의 *ProgId* 또는 프로그래밍 방식 식별자와 함께 **ComObject** 매개 변수를 지정해야 합니다. COM 사용의 제한 사항과 시스템에서 사용할 수 있는 ProgId 확인 방법에 대한 자세한 설명은 이 사용자 가이드의 범위를 벗어나지만 WSH와 같은 환경에서 잘 알려진 대부분의 개체는 Windows PowerShell 내에서 사용할 수 있습니다.

다음 progid를 지정하여 WSH 개체를 만들 수 있습니다. **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, **Scripting.FileSystemObject**. 이러한 개체를 만드는 명령은 다음과 같습니다.

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

이러한 클래스의 기능은 대부분 Windows PowerShell에서 다른 방법으로 제공되지만 바로 가기 만들기와 같은 몇 가지 작업은 WSH 클래스를 통해 수행하는 것이 더 쉽습니다.

## <a name="creating-a-desktop-shortcut-with-wscriptshell"></a>WScript.Shell을 사용하여 바탕 화면 바로 가기 만들기

COM 개체를 사용하여 신속하게 수행할 수 있는 작업 중 하나는 바로 가기 만들기입니다. Windows PowerShell 홈 폴더에 연결하는 바로 가기를 바탕 화면에 만든다고 가정합니다. 먼저 **$WshShell** 변수에 저장할 **WScript.Shell** 참조를 만들어야 합니다.

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

Get-Member는 COM 개체로 작업하므로 다음과 같이 입력하여 개체의 멤버를 탐색할 수 있습니다.

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

**Get-Member**에는 파이프 대신 사용하여 **Get-Member**에 입력을 제공할 수 있는 선택적 **InputObject** 매개 변수가 있습니다. **Get-Member -InputObject $WshShell** 명령을 대신 사용한 경우 위와 동일한 출력이 표시됩니다. **InputObject**를 사용하는 경우 해당 인수가 단일 항목으로 처리됩니다. 즉, 변수에 여러 개체가 있는 경우 **Get-Member**는 개체 배열로 처리합니다. 예:

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

**WScript.Shell CreateShortcut** 메서드는 만들려는 바로 가기 파일의 경로인 단일 인수를 사용합니다. 바탕 화면의 전체 경로를 입력할 수도 있지만 더 쉬운 방법이 있습니다. 바탕 화면은 일반적으로 현재 사용자의 홈 폴더 안에 있는 바탕 화면 폴더로 표시됩니다. Windows PowerShell에는 이 폴더의 경로를 포함하는 **$Home** 변수가 있습니다. 이 변수를 사용하여 홈 폴더의 경로를 지정한 후 다음과 같이 입력하여 바탕 화면 폴더의 이름과 만들려는 바로 가기의 이름을 추가할 수 있습니다.

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

큰따옴표 안에 변수 이름처럼 보이는 항목을 사용하면 Windows PowerShell에서 일치하는 값을 대체하려고 합니다. 작은따옴표를 사용하면 Windows PowerShell에서 변수 값을 대체하지 않습니다. 예를 들어 다음 명령을 입력해 보세요.

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

이제 새 바로 가기 참조를 포함하는 **$lnk** 변수가 있습니다. 해당 멤버를 확인하려는 경우 **Get-Member**에 파이프할 수 있습니다. 아래 출력은 바로 가기 만들기를 완료하는 데 사용해야 하는 멤버를 보여 줍니다.

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

Windows PowerShell의 애플리케이션 폴더인 **TargetPath**를 지정한 다음 **Save** 메서드를 호출하여 **$lnk** 바로 가기를 저장해야 합니다. Windows PowerShell 애플리케이션 폴더 경로는 **$PSHome** 변수에 저장되므로 다음과 같이 입력하면 됩니다.

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

## <a name="using-internet-explorer-from-windows-powershell"></a>Windows PowerShell에서 Internet Explorer 사용

COM을 사용하여 많은 애플리케이션(Microsoft Office 애플리케이션 제품군 및 Internet Explorer 포함)을 자동화할 수 있습니다. Internet Explorer는 COM 기반 애플리케이션 작업과 관련된 몇 가지 일반적인 방법과 문제를 보여 줍니다.

Internet Explorer ProgId인 **InternetExplorer.Application**을 지정하여 Internet Explorer 인스턴스를 만듭니다.

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

이 명령은 Internet Explorer를 시작하지만 표시하지는 않습니다. Get-Process를 입력하면 iexplore라는 프로세스가 실행되고 있는 것을 확인할 수 있습니다. 실제로 Windows PowerShell을 종료해도 프로세스는 계속 실행됩니다. iexplore 프로세스를 종료하려면 컴퓨터를 다시 부팅하거나 작업 관리자와 같은 도구를 사용해야 합니다.

> [!NOTE]
> 별도 프로세스로 시작되며, 흔히 *ActiveX 실행 파일*이라고 불리는 COM 개체는 시작될 때 사용자 인터페이스 창을 표시할 수도 있고, 표시하지 않을 수도 있습니다. Internet Explorer처럼 창을 만들지만 표시하지 않는 경우 일반적으로 포커스가 Windows 바탕 화면으로 이동하며, 창을 조작하려면 표시해야 합니다.

**$ie | Get-Member**를 입력하면 Internet Explorer의 속성과 메서드를 볼 수 있습니다. Internet Explorer 창을 보려면 다음과 같이 입력하여 Visible 속성을 $true로 설정합니다.

```powershell
$ie.Visible = $true
```

그런 다음 Navigate 메서드를 사용하여 특정 웹 주소로 이동할 수 있습니다.

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

Internet Explorer 개체 모델의 다른 멤버를 사용하여 웹 페이지에서 텍스트 콘텐츠를 검색할 수 있습니다. 다음 명령은 현재 웹 페이지의 본문에 있는 HTML 텍스트를 표시합니다.

```powershell
$ie.Document.Body.InnerText
```

PowerShell 내에서 Internet Explorer를 닫으려면 Quit() 메서드를 호출합니다.

```powershell
$ie.Quit()
```

이렇게 하면 강제로 닫힙니다. $ie 변수가 여전히 COM 개체로 표시되지만 더 이상 유효한 참조를 포함하지 않습니다. 이 변수를 사용하려고 하면 다음과 같은 자동화 오류 메시지가 나타납니다.

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

$ie = $null과 같은 명령을 사용하여 나머지 참조를 제거하거나, 다음과 같이 입력하여 변수를 완전히 제거할 수 있습니다.

```powershell
Remove-Variable ie
```

> [!NOTE]
> 해당 참조를 제거할 때 ActiveX 실행 파일을 종료할지 아니면 계속 실행할지에 대한 일반적인 표준은 없습니다. 애플리케이션이 표시되는지 여부, 애플리케이션에서 편집한 문서의 실행 여부 및 Windows PowerShell의 실행 여부와 같은 상황에 따라 애플리케이션이 종료될 수도 있고, 종료되지 않을 수도 있습니다. 따라서 Windows PowerShell에서 사용할 각 ActiveX 실행 파일의 종료 동작을 테스트해야 합니다.

## <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a>.NET Framework-Wrapped COM 개체에 대한 경고 보기

경우에 따라 COM 개체에는 **New-Object**가 사용하는 .NET Framework RCW(*런타임 호출 가능 래퍼*)가 포함되어 있을 수 있습니다. RCW의 동작이 일반적인 COM 개체와 다를 수 있기 때문에 **New-Object**에는 RCW 액세스에 대해 경고하는 **Strict** 매개 변수가 포함되어 있습니다. **Strict** 매개 변수를 지정한 다음 RCW를 사용하는 COM 개체를 만들면 다음과 같은 경고 메시지가 나타납니다.

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

개체가 만들어진 후에도 표준 COM 개체가 아니라는 경고 메시지는 계속 나타납니다.