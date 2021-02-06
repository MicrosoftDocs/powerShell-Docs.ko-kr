---
description: PowerShell에서 개체 속성을 사용 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_properties?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Properties
ms.openlocfilehash: c5cc7abdd580a0fa57134f9c79616d1d8290a7e1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601046"
---
# <a name="about-properties"></a>속성 정보

## <a name="short-description"></a>간단한 설명
PowerShell에서 개체 속성을 사용 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell은 개체 라고 하는 구조화 된 정보 컬렉션을 사용 하 여 데이터 저장소의 항목 또는 컴퓨터의 상태를 나타냅니다. 일반적으로 Microsoft .NET 프레임 워크의 일부인 개체로 작업 하지만 PowerShell에서 사용자 지정 개체를 만들 수도 있습니다.

항목과 해당 개체 간의 연결이 매우 가깝습니다. 개체를 변경 하는 경우 일반적으로 해당 개체를 나타내는 항목이 변경 됩니다. 예를 들어 PowerShell에서 파일을 가져올 때 실제 파일을 가져오지 않습니다. 대신 파일을 나타내는 FileInfo 개체를 가져옵니다. FileInfo 개체를 변경 하면 파일도 변경 됩니다.

대부분의 개체에는 속성이 있습니다. 속성은 개체에 연결 된 데이터입니다. 개체 유형에 따라 속성이 다릅니다. 예를 들어 파일을 나타내는 FileInfo 개체는 파일에 읽기 전용 특성이 있는 경우 $True 포함 된 **IsReadOnly** 속성을 포함 하 고, 그렇지 않은 경우 $False 합니다.
파일 시스템 디렉터리를 나타내는 System.io.directoryinfo 개체에는 부모 디렉터리의 경로를 포함 하는 부모 속성이 있습니다.

### <a name="object-properties"></a>개체 속성

개체의 속성을 가져오려면 cmdlet을 사용 합니다 `Get-Member` . 예를 들어 **fileinfo** 개체의 속성을 가져오려면 cmdlet을 사용 하 여 `Get-ChildItem` 파일을 나타내는 FileInfo 개체를 가져옵니다. 그런 다음 파이프라인 연산자 (&#124;)를 사용 하 여 **FileInfo** 개체를로 보냅니다 `Get-Member` . 다음 명령은 PowerShell.exe 파일을 가져와로 보냅니다 `Get-Member` .
\$Pshome 자동 변수는 PowerShell 설치 디렉터리의 경로를 포함 합니다.

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member
```

명령의 출력에는 **FileInfo** 개체의 멤버가 나열 됩니다.
멤버에는 속성과 메서드가 모두 포함 됩니다. PowerShell에서 작업 하는 경우 개체의 모든 멤버에 액세스할 수 있습니다.

메서드가 아니라 개체의 속성만 가져오려면 `Get-Member` 다음 예제와 같이 "property" 값을 사용 하 여 cmdlet의 MemberType 매개 변수를 사용 합니다.

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member -MemberType property
```

```Output
TypeName: System.IO.FileInfo

Name              MemberType Definition
----              ---------- ----------
Attributes        Property   System.IO.FileAttributes Attributes {get;set;}
CreationTime      Property   System.DateTime CreationTime {get;set;}
CreationTimeUtc   Property   System.DateTime CreationTimeUtc {get;set;}
Directory         Property   System.IO.DirectoryInfo Directory {get;}
DirectoryName     Property   System.String DirectoryName {get;}
Exists            Property   System.Boolean Exists {get;}
Extension         Property   System.String Extension {get;}
FullName          Property   System.String FullName {get;}
IsReadOnly        Property   System.Boolean IsReadOnly {get;set;}
LastAccessTime    Property   System.DateTime LastAccessTime {get;set;}
LastAccessTimeUtc Property   System.DateTime LastAccessTimeUtc {get;set;}
LastWriteTime     Property   System.DateTime LastWriteTime {get;set;}
LastWriteTimeUtc  Property   System.DateTime LastWriteTimeUtc {get;set;}
Length            Property   System.Int64 Length {get;}
Name              Property   System.String Name {get;}
```

속성을 찾은 후 PowerShell 명령에서 사용할 수 있습니다.

## <a name="property-values"></a>속성 값

특정 형식의 모든 개체에 동일한 속성이 있지만 해당 속성의 값은 특정 개체를 설명 합니다. 예를 들어 모든 FileInfo 개체에는 CreationTime 속성이 있지만 각 파일에 대해 해당 속성의 값이 다릅니다.

개체의 속성 값을 가져오는 가장 일반적인 방법은 점 메서드를 사용 하는 것입니다. 개체를 포함 하는 변수와 같은 개체에 대 한 참조 나 개체를 가져오는 명령을 입력 합니다. 그런 다음 점 (.)과 속성 이름을 차례로 입력 합니다.

예를 들어 다음 명령은 PowerShell.exe 파일의 CreationTime 속성 값을 표시 합니다. `Get-ChildItem`명령은 PowerShell.exe 파일을 나타내는 FileInfo 개체를 반환 합니다. 명령은 속성에 액세스 하기 전에 실행 되도록 하기 위해 괄호로 묶여 있습니다. `Get-ChildItem`명령은 다음과 같이 CreationTime 속성의 점과 이름을 차례로 입력 합니다.

```powershell
(Get-ChildItem $pshome\PowerShell.exe).creationtime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

다음 예제와 같이 개체를 변수에 저장 한 다음 점 메서드를 사용 하 여 해당 속성을 가져올 수도 있습니다.

```powershell
$a = Get-ChildItem $pshome\PowerShell.exe
$a.CreationTime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

`Select-Object`및 cmdlet을 사용 하 여 `Format-List` 개체의 속성 값을 표시할 수도 있습니다. `Select-Object` 및에 `Format-List` 는 각각 **속성** 매개 변수가 있습니다. **Property** 매개 변수를 사용 하 여 속성 및 해당 값을 하나 이상 지정할 수 있습니다. 또는 와일드 카드 문자 ()를 사용 \* 하 여 모든 속성을 나타낼 수 있습니다.

예를 들어 다음 명령은 PowerShell.exe 파일의 모든 속성 값을 표시 합니다.

```powershell
Get-ChildItem $pshome\PowerShell.exe | Format-List -Property *
```

```output
PSPath            : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0\PowerShell.exe
PSParentPath      : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0
PSChildName       : PowerShell.exe
PSDrive           : C
PSProvider        : Microsoft.PowerShell.Core\FileSystem
PSIsContainer     : False
Mode              : -a----
VersionInfo       : File:             C:\Windows\System32\WindowsPowerShell\
                    v1.0\PowerShell.exe
                    InternalName:     POWERSHELL
                    OriginalFilename: PowerShell.EXE.MUI
                    FileVersion:      10.0.16299.15 (WinBuild.160101.0800)
                    FileDescription:  Windows PowerShell
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.16299.15
                    Debug:            False
                    Patched:          False
                    PreRelease:       False
                    PrivateBuild:     False
                    SpecialBuild:     False
                    Language:         English (United States)

BaseName          : PowerShell
Target            : {C:\Windows\WinSxS\amd64_microsoft-windows-powershell-ex
                    e_31bf3856ad364e35_10.0.16299.15_none_8c022aa6735716ae\p
                    owershell.exe}
LinkType          : HardLink
Name              : PowerShell.exe
Length            : 449024
DirectoryName     : C:\Windows\System32\WindowsPowerShell\v1.0
Directory         : C:\Windows\System32\WindowsPowerShell\v1.0
IsReadOnly        : False
Exists            : True
FullName          : C:\Windows\System32\WindowsPowerShell\v1.0\PowerShell.ex
Extension         : .exe
CreationTime      : 9/29/2017 6:43:19 AM
CreationTimeUtc   : 9/29/2017 1:43:19 PM
LastAccessTime    : 9/29/2017 6:43:19 AM
LastAccessTimeUtc : 9/29/2017 1:43:19 PM
LastWriteTime     : 9/29/2017 6:43:19 AM
LastWriteTimeUtc  : 9/29/2017 1:43:19 PM
Attributes        : Archive
```

### <a name="static-properties"></a>정적 속성

PowerShell에서 .NET 클래스의 정적 속성을 사용할 수 있습니다. 정적 속성은 개체의 속성인 표준 속성과 달리 클래스의 속성입니다.

클래스의 정적 속성을 가져오려면 Get-Member cmdlet의 Static 매개 변수를 사용 합니다.

예를 들어 다음 명령은 클래스의 정적 속성을 가져옵니다 `System.DateTime` .

```powershell
Get-Date | Get-Member -MemberType Property -Static
```

```Output
TypeName: System.DateTime

Name     MemberType Definition
----     ---------- ----------
MaxValue Property   static datetime MaxValue {get;}
MinValue Property   static datetime MinValue {get;}
Now      Property   datetime Now {get;}
Today    Property   datetime Today {get;}
UtcNow   Property   datetime UtcNow {get;}
```

정적 속성의 값을 가져오려면 다음 구문을 사용 합니다.

```
[<ClassName>]::<Property>
```

예를 들어 다음 명령은 클래스의 UtcNow static 속성 값을 가져옵니다 `System.DateTime` .

```powershell
[System.DateTime]::UtcNow
```

### <a name="properties-of-scalar-objects-and-collections"></a>스칼라 개체 및 컬렉션의 속성

특정 형식의 한 개의 ("스칼라") 개체 속성은 일반적으로 동일한 형식의 개체 컬렉션 속성과는 다릅니다.
예를 들어 모든 서비스에 **displayname** 속성이 있지만 서비스 컬렉션에 **displayname** 속성이 없습니다.

다음 명령은 ' Audiosrv ' 서비스의 **DisplayName** 속성 값을 가져옵니다.

```powershell
(Get-Service Audiosrv).DisplayName
```

```output
Windows Audio
```

PowerShell 3.0부터 PowerShell은 스칼라 개체 및 컬렉션의 서로 다른 속성으로 인해 발생 하는 스크립팅 오류를 방지 하려고 합니다. 동일한 명령은를 반환 하는 모든 서비스의 **DisplayName** 속성 값을 반환 합니다 `Get-Service` .

```powershell
(Get-Service).DisplayName
```

```output
Application Experience
Application Layer Gateway Service
Windows All-User Install Agent
Application Identity
Application Information
...
```

컬렉션을 제출할 때 단일 ("스칼라") 개체에만 존재 하는 속성을 요청 하는 경우 PowerShell은 컬렉션의 모든 개체에 대해 해당 속성의 값을 반환 합니다.

모든 컬렉션에는 컬렉션에 있는 개체 수를 반환 하는 **Count** 속성이 있습니다.

```powershell
(Get-Service).Count
```

```output
176
```

PowerShell 3.0부터 0 개의 개체나 하나의 개체의 Count 또는 Length 속성을 요청 하는 경우 PowerShell은 올바른 값을 반환 합니다.

```powershell
(Get-Service Audiosrv).Count
```

```output
1
```

속성이 개별 개체 및 컬렉션에 있으면 컬렉션의 속성만 반환 됩니다.

 ```powershell
 $collection = @(
 [pscustomobject]@{length = "foo"}
 [pscustomobject]@{length = "bar"}
 )
 # PowerShell returns the collection's Length.
 $collection.length
 ```

 ```output
 2
 ```

이 기능은 스칼라 개체 및 컬렉션의 메서드에도 적용 됩니다. 자세한 내용은 [about_Methods](about_methods.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[about_Methods](about_Methods.md)

[about_Objects](about_Objects.md)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)

[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object)

[Format-List](xref:Microsoft.PowerShell.Utility.Format-List)

