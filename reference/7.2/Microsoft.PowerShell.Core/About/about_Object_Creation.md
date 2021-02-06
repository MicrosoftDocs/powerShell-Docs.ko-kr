---
description: PowerShell에서 개체를 만드는 방법을 설명 합니다.
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_object_creation?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Object_Creation
ms.openlocfilehash: 72c0d763fe7f3838c8b2ca68930521e24d0e6139
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601864"
---
# <a name="about-object-creation"></a>개체 만들기 정보

## <a name="short-description"></a>간단한 설명

PowerShell에서 개체를 만드는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell에서 개체를 만들고 명령 및 스크립트에서 만든 개체를 사용할 수 있습니다.

여러 가지 방법으로 개체를 만들 수 있으며,이 목록은 명확 하지 않습니다.

- [새 개체](xref:Microsoft.PowerShell.Utility.New-Object): .NET Framework 개체 또는 COM 개체의 인스턴스를 만듭니다.
- [가져오기-Csv](xref:Microsoft.PowerShell.Utility.Import-Csv) /
   [Convertfrom-csv](xref:Microsoft.PowerShell.Utility.ConvertFrom-Csv): 쉼표로 구분 된 값으로 정의 된 항목에서 사용자 지정 개체 (**PSCustomObject**)를 만듭니다.
- [Convertfrom-csv](xref:Microsoft.PowerShell.Utility.ConvertFrom-Json): JAVASCRIPT OBJECT NOTATION (json)에 정의 된 사용자 지정 개체를 만듭니다.
- [Convertfrom-csv-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData): 키 값 쌍으로 정의 된 사용자 지정 개체를 만듭니다.
- [추가-형식](xref:Microsoft.PowerShell.Utility.Add-Type):를 사용 하 여 인스턴스화할 수 있는 클래스를 PowerShell 세션에서 정의할 수 있습니다 `New-Object` .
- **AsCustomObject** :이 매개 변수는 스크립트 블록을 사용 하 여 정의 하는 사용자 지정 개체를 [만듭니다.](xref:Microsoft.PowerShell.Core.New-Module)
- [멤버 추가](xref:Microsoft.PowerShell.Utility.Add-Member): 기존 개체에 속성을 추가 합니다. `Add-Member`를 사용 하 여와 같은 단순 형식에서 사용자 지정 개체를 만들 수 있습니다 `[System.Int32]` .
- [Select-object](xref:Microsoft.PowerShell.Utility.Select-Object): 개체의 속성을 선택 합니다. `Select-Object`를 사용 하 여 이미 인스턴스화된 개체에서 사용자 지정 및 계산 된 속성을 만들 수 있습니다.

이 문서에서는 다음과 같은 추가 방법을 설명 합니다.

- 정적 메서드를 사용 하 여 형식의 생성자 호출 `new()`
- Typecasting 속성 이름 및 속성 값의 해시 테이블

## <a name="static-new-method"></a>Static new () 메서드

모든 .NET 형식에는 `new()` 인스턴스를 보다 쉽게 구성할 수 있는 메서드가 있습니다. 지정 된 형식에 대해 사용 가능한 생성자를 모두 볼 수도 있습니다.

형식에 대 한 생성자를 보려면 `new` 형식 이름 다음에 메서드 이름을 지정 하 고 키를 누릅니다 `<ENTER>` .

```powershell
[System.Uri]::new
```

```Output
OverloadDefinitions
-------------------
uri new(string uriString)
uri new(string uriString, bool dontEscape)
uri new(uri baseUri, string relativeUri, bool dontEscape)
uri new(string uriString, System.UriKind uriKind)
uri new(uri baseUri, string relativeUri)
uri new(uri baseUri, uri relativeUri)
```

이제 적절 한 생성자를 지정 하 여 **system.uri** 를 만들 수 있습니다.

```powershell
[System.Uri]::new("https://www.bing.com")
```

```Output
AbsolutePath   : /
AbsoluteUri    : https://www.bing.com/
LocalPath      : /
Authority      : www.bing.com
...
```

다음 샘플을 사용 하 여 현재 인스턴스화할 수 있도록 로드 된 .NET 형식을 확인할 수 있습니다.

```powershell
[AppDomain]::CurrentDomain.GetAssemblies() |
  ForEach-Object {
    $_.GetExportedTypes() |
      ForEach-Object { $_.FullName }
  }
```

메서드를 사용 하 여 만든 개체는 `new()` PowerShell cmdlet에 의해 생성 된 것과 동일한 형식의 개체와 동일한 속성을 가질 수 없습니다. PowerShell cmdlet, 공급자 및 확장 유형 시스템은 인스턴스에 추가 속성을 추가할 수 있습니다.

예를 들어 PowerShell의 FileSystem 공급자는에서 반환 된 **system.io.directoryinfo** 개체에 6 개의 **참고 속성** 값을 추가 `Get-Item` 합니다.

```powershell
$PSDirInfo = Get-Item /
$PSDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    6 NoteProperty
    1 ScriptProperty
   18 Method
```

**System.io.directoryinfo** 개체를 직접 만드는 경우에는 이러한 6 개의 **참고 속성** 값이 없습니다.

```powershell
$NewDirInfo = [System.IO.DirectoryInfo]::new('/')
$NewDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    1 ScriptProperty
   18 Method
```

확장 유형 시스템에 대 한 자세한 내용은 [about_Types.ps1xml](about_Types.ps1xml.md)을 참조 하세요.

이 기능은 PowerShell 5.0에 추가 되었습니다.

## <a name="create-objects-from-hash-tables"></a>해시 테이블에서 개체 만들기

속성 및 속성 값의 해시 테이블에서 개체를 만들 수 있습니다.

구문은 다음과 같습니다.

```
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

이 메서드는 매개 변수가 없는 생성자가 있는 클래스에 대해서만 작동 합니다. 개체 속성은 public 이어야 하며 설정 가능 해야 합니다.

이 기능은 PowerShell 버전 3.0에 추가 되었습니다.

## <a name="create-custom-objects-from-hash-tables"></a>해시 테이블에서 사용자 지정 개체 만들기

사용자 지정 개체는 매우 유용 하며 해시 테이블 메서드를 사용 하 여 쉽게 만들 수 있습니다. **PSCustomObject** 클래스는이 목적을 위해 특별히 설계 되었습니다.

사용자 지정 개체는 함수 또는 스크립트에서 사용자 지정 된 출력을 반환 하는 좋은 방법입니다. 이는 다른 명령으로 다시 포맷 하거나 파이프 할 수 없는 형식이 지정 된 출력을 반환 하는 것 보다 더 유용 합니다.

의 명령은 `Test-Object function` 일부 변수 값을 설정 하 고 해당 값을 사용 하 여 사용자 지정 개체를 만듭니다. Cmdlet 도움말 항목의 예제 섹션에서 사용 중이 개체를 볼 수 있습니다 `Update-Help` .

```powershell
function Test-Object {
  $ModuleName = "PSScheduledJob"
  $HelpCulture = "en-us"
  $HelpVersion = "3.1.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
  $ModuleName = "PSWorkflow"
  $HelpCulture = "en-us"
  $HelpVersion = "3.0.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
}
Test-Object
```

이 함수의 출력은 기본적으로 테이블로 형식이 지정 된 사용자 지정 개체의 컬렉션입니다.

```Output
ModuleName        UICulture      Version
---------         ---------      -------
PSScheduledJob    en-us          3.1.0.0
PSWorkflow        en-us          3.0.0.0
```

사용자는 표준 개체와 동일한 방식으로 사용자 지정 개체의 속성을 관리할 수 있습니다.

```powershell
(Test-Object).ModuleName
```

```Output
 PSScheduledJob
 PSWorkflow
```

## <a name="create-non-custom-objects-from-hash-tables"></a>해시 테이블에서 사용자 지정 되지 않은 개체 만들기

해시 테이블을 사용 하 여 사용자 지정 클래스가 아닌 클래스에 대 한 개체를 만들 수도 있습니다. 사용자 지정 클래스가 아닌 클래스에 대 한 개체를 만드는 경우 초기 **시스템** 네임 스페이스 구성 요소를 생략할 수 있지만 네임 스페이스로 한정 된 형식 이름이 필요 합니다.

예를 들어 다음 명령은 세션 옵션 개체를 만듭니다.

```powershell
[System.Management.Automation.Remoting.PSSessionOption]@{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
```

해시 테이블 기능의 요구 사항, 특히 매개 변수가 없는 생성자 요구 사항으로 인해 기존 클래스가 많이 제거 되었습니다. 그러나 대부분의 PowerShell _옵션_ 클래스는이 기능과 **ProcessStartInfo** 클래스와 같은 매우 유용한 기타 클래스와 함께 작동 하도록 설계 되었습니다.

```powershell
[System.Diagnostics.ProcessStartInfo]@{
  CreateNoWindow="$true"
  Verb="run as"
}
```

```Output
Arguments               :
ArgumentList            : {}
CreateNoWindow          : True
EnvironmentVariables    : {OneDriveConsumer, PROCESSOR_ARCHITECTURE,
                           CommonProgramFiles(x86), APPDATA...}
Environment             : {[OneDriveConsumer, C:\Users\user1\OneDrive],
                           [PROCESSOR_ARCHITECTURE, AMD64],
                           [CommonProgramFiles(x86),
                           C:\Program Files (x86)\Common Files],
                           [APPDATA, C:\Users\user1\AppData\Roaming]...}
RedirectStandardInput   : False
RedirectStandardOutput  : False
RedirectStandardError   : False
...
```

매개 변수 값을 설정할 때 해시 테이블 기능을 사용할 수도 있습니다. 예를 들어의 **Sessionoption** 매개 변수 값입니다 `New-PSSession` .
cmdlet은 해시 테이블 일 수 있습니다.

```powershell
New-PSSession -ComputerName Server01 -SessionOption @{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
Register-ScheduledJob Name Test -FilePath .\Get-Inventory.ps1 -Trigger @{
  Frequency="Daily"
  At="15:00"
}
```

## <a name="generic-objects"></a>제네릭 개체

PowerShell에서 제네릭 개체를 만들 수도 있습니다. 제네릭은 저장하거나 사용하는 하나 이상의 형식에 대한 자리 표시자(형식 매개 변수)를 포함하는 클래스, 구조체, 인터페이스 및 메서드입니다.

다음 예제에서는 **사전** 개체를 만듭니다.

```powershell
$dict = New-Object 'System.Collections.Generic.Dictionary[String,Int]'
$dict.Add("One", 1)
$dict
```

```Output
Key Value
--- -----
One     1
```

제네릭에 대 한 자세한 내용은 [.net의 제네릭](/dotnet/standard/generics)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[about_Objects](about_Objects.md)

[about_Methods](about_Methods.md)

[about_Properties](about_Properties.md)

[about_Pipelines](about_Pipelines.md)

[about_Types.ps1xml](about_Types.ps1xml.md)
