---
description: 메서드를 사용 하 여 PowerShell에서 개체에 대 한 작업을 수행 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_methods?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_methods
ms.openlocfilehash: 35eaafcec5d645be6fe88f506bc0971344406273
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602684"
---
# <a name="about-methods"></a>메서드 정보

## <a name="short-description"></a>간단한 설명
메서드를 사용 하 여 PowerShell에서 개체에 대 한 작업을 수행 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell은 개체를 사용 하 여 데이터 저장소의 항목 또는 컴퓨터의 상태를 나타냅니다. 예를 들어, FileInfo 개체는 파일 시스템 드라이브의 파일을 나타내고 ProcessInfo 개체는 컴퓨터의 프로세스를 나타냅니다.

개체에는 개체에 대 한 데이터를 저장 하는 속성과 개체를 변경할 수 있는 메서드가 있습니다.

"메서드"는 개체에서 수행할 수 있는 작업을 지정 하는 일련의 명령입니다. 예를 들어 개체에는 `FileInfo` `CopyTo` 개체가 나타내는 파일을 복사 하는 메서드가 포함 되어 있습니다 `FileInfo` .

개체의 메서드를 가져오려면 cmdlet을 사용 합니다 `Get-Member` . 값이 "Method" 인 **MemberType** 속성을 사용 합니다. 다음 명령은 개체를 처리 하는 메서드를 가져옵니다.

```powershell
Get-Process | Get-Member -MemberType Method
```

```Output
TypeName: System.Diagnostics.Process

Name                      MemberType Definition
----                      ---------- ----------
BeginErrorReadLine        Method     System.Void BeginErrorReadLine()
BeginOutputReadLine       Method     System.Void BeginOutputReadLine()
...
Kill                      Method     System.Void Kill()
Refresh                   Method     System.Void Refresh()
Start                     Method     bool Start()
ToString                  Method     string ToString()
WaitForExit               Method     bool WaitForExit(int milliseconds), ...
WaitForInputIdle          Method     bool WaitForInputIdle(int millisecon...
```

개체의 메서드를 수행 하거나 "호출" 하려면 점 (.), 메서드 이름 및 괄호 ("()") 집합을 입력 합니다. 메서드에 인수가 있는 경우 인수 값을 괄호 안에 넣습니다. 인수를 포함 하지 않는 경우에도 모든 메서드 호출에 괄호가 필요 합니다. 메서드가 여러 인수를 사용 하는 경우 쉼표로 구분 해야 합니다.

예를 들어 다음 명령은 프로세스의 Kill 메서드를 호출 하 여 컴퓨터에서 메모장 프로세스를 종료 합니다.

```powershell
$notepad = Get-Process notepad
$notepad.Kill()
```

위의 문을 결합 하 여이 예를 줄일 수 있습니다.

```powershell
(Get-Process Notepad).Kill()
```

`Get-Process`명령은 Kill 메서드를 호출 하기 전에 실행 되도록 괄호로 묶습니다. `Kill`그런 다음 반환 된 개체에서 메서드를 호출 합니다 `Process` .

또 다른 유용한 방법은 `Replace` 문자열의 메서드입니다. `Replace`메서드는 문자열 내에서 텍스트를 바꿉니다. 아래 예제에서 점 (.)은 문자열의 끝 따옴표 바로 뒤에 배치 될 수 있습니다.

```powershell
'this is rocket science'.Replace('rocket', 'rock')
```

```Output
this is rock science
```

앞의 예제와 같이 명령을 사용 하 여 가져온 개체에 대해 메서드를 호출 하거나, 변수의 개체를 사용 하거나, 개체를 생성 하는 모든 항목 (예: 인용 부호의 문자열)을 호출할 수 있습니다.

PowerShell 4.0부터 동적 메서드 이름을 사용한 메서드 호출이 지원 됩니다.

### <a name="learning-about-methods"></a>메서드 학습

개체의 메서드에 대 한 정의를 찾으려면 개체 형식에 대 한 도움말 항목으로 이동 하 여 해당 메서드 페이지를 찾습니다. 예를 들어 다음 페이지 [에서는 개체를](/dotnet/api/system.diagnostics.process#methods)처리 하는 프로세스의 메서드를 설명 합니다.

메서드의 인수를 확인 하려면 PowerShell cmdlet의 구문 다이어그램과 같은 메서드 정의를 검토 합니다.

메서드 정의에는 PowerShell cmdlet의 매개 변수 집합과 같은 하나 이상의 메서드 서명이 있을 수 있습니다. 시그니처는 메서드를 호출 하는 명령에 대 한 모든 유효한 형식을 표시 합니다.

예를 `CopyTo` 들어 클래스의 메서드에는 `FileInfo` 다음과 같은 두 가지 메서드 시그니처가 포함 되어 있습니다.

```
    CopyTo(String destFileName)
    CopyTo(String destFileName, Boolean overwrite)
```

첫 번째 메서드 시그니처는 대상 파일 이름 및 경로를 사용 합니다. 다음 예제에서는 첫 번째 메서드를 사용 하 여 `CopyTo` `Final.txt` 파일을 디렉터리에 복사 `C:\Bin` 합니다.

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt")
```

> [!NOTE]
> PowerShell의 _인수_ 모드와 달리 개체 메서드는 powershell이 빌드되는 .net framework에 대 한 통과 인 _식_ 모드에서 실행 됩니다. _식_ 모드에서는 **bareword** 인수 (따옴표 붙지 않은 문자열)를 사용할 수 없습니다. 경로를 매개 변수로 사용 하 고 경로를 인수로 사용 하는 경우 이러한 차이를 확인할 수 있습니다. 에서 구문 분석 모드에 대해 자세히 알아볼 수 있습니다 [about_Parsing](about_Parsing.md)

두 번째 메서드 시그니처는 대상 파일 이름 및 대상 파일을 덮어쓸지 여부를 결정 하는 부울 값 (이미 있는 경우)을 사용 합니다.

다음 예제에서는 두 번째 방법을 사용 하 여 `CopyTo` `Final.txt` 디렉터리에 파일을 복사 하 `C:\Bin` 고 기존 파일을 덮어씁니다.

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt", $true)
```

### <a name="methods-of-scalar-objects-and-collections"></a>스칼라 개체 및 컬렉션의 메서드

특정 형식의 한 ("스칼라") 개체의 메서드는 일반적으로 동일한 형식의 개체 컬렉션 메서드와 다릅니다.

예를 들어 모든 프로세스에는 `Kill` 메서드가 있지만 프로세스 컬렉션에는 Kill 메서드가 없습니다.

PowerShell 3.0부터 PowerShell은 스칼라 개체 및 컬렉션의 다른 방법으로 인해 발생 하는 스크립팅 오류를 방지 하려고 합니다.

컬렉션을 제출 하지만 단일 ("스칼라") 개체에만 존재 하는 메서드를 요청 하는 경우 PowerShell은 컬렉션의 모든 개체에 대해 메서드를 호출 합니다.

메서드가 개별 개체 및 컬렉션에 있으면 컬렉션의 메서드만 호출 됩니다.

이 기능은 스칼라 개체 및 컬렉션의 속성에도 적용 됩니다. 자세한 내용은 [about_Properties](about_Properties.md)를 참조 하세요.

### <a name="examples"></a>예

다음 예제에서는 개체의 컬렉션에 있는 개별 프로세스 개체의 **Kill** 메서드를 실행 합니다.

첫 번째 명령은 메모장 프로세스의 세 가지 인스턴스를 시작 합니다. `Get-Process` 메모장 프로세스의 세 인스턴스를 모두 가져온 다음 `$p` 변수에 저장 합니다.

```powershell
Notepad; Notepad; Notepad
$p = Get-Process Notepad
$p.Count
```

```Output
3
```

다음 명령은 변수의 세 프로세스 모두에서 **Kill** 메서드를 실행 합니다 `$p` . 이 명령은 프로세스 컬렉션에 메서드가 없는 경우에도 작동 `Kill` 합니다.

```powershell
$p.Kill()
Get-Process Notepad
```

`Get-Process`명령은 메서드가 작동 하는지 확인 합니다 `Kill` .

```Output
Get-Process : Cannot find a process with the name "notepad". Verify the proc
ess name and call the cmdlet again.
At line:1 char:12
+ Get-Process <<<<  notepad
    + CategoryInfo          : ObjectNotFound: (notepad:String) [Get-Process]
, ProcessCommandException
    + FullyQualifiedErrorId : NoProcessFoundForGivenName,Microsoft.PowerShel
l.Commands.GetProcessCommand
```

이 예제는 cmdlet을 사용 하 여 `Foreach-Object` 컬렉션의 각 개체에 대해 메서드를 실행 하는 것과 기능적으로 동일 합니다.

```powershell
$p | ForEach-Object {$_.Kill()}
```

### <a name="foreach-and-where-methods"></a>ForEach 및 Where 메서드

PowerShell 4.0부터 메서드 구문을 사용한 컬렉션 필터링이 지원 됩니다. 이를 통해 컬렉션 및를 처리할 때 두 가지 새로운 메서드를 사용할 수 있습니다 `ForEach` `Where` .

[about_arrays](about_arrays.md)의 이 메서드에 대해 자세히 알아볼 수 있습니다.

### <a name="calling-a-specific-method-when-multiple-overloads-exist"></a>여러 오버 로드가 있는 경우 특정 메서드 호출

.NET 메서드를 호출할 때 다음 시나리오를 고려 하십시오. 메서드가 개체를 사용 하지만 더 구체적인 형식을 사용 하는 인터페이스를 통해 오버 로드가 있는 경우 PowerShell은 해당 인터페이스로 명시적으로 캐스팅 하지 않는 한 개체를 허용 하는 메서드를 선택 합니다.

```powershell
Add-Type -TypeDefinition @'

   // Interface
   public interface IFoo {
     string Bar(int p);
   }

   // Type that implements the interface
   public class Foo : IFoo {

   // Direct member method named 'Bar'
   public string Bar(object p) { return $"object: {p}"; }

   // *Explicit* implementation of IFoo's 'Bar' method().
   string IFoo.Bar(int p) {
       return $"int: {p}";
   }

}
'@
```

이 예제에서는 `object` **Bar** 메서드의 오버 로드가 더 이상 선택 되지 않았습니다.

```powershell
[Foo]::new().Bar(1)
```

```Output
object: 1
```

이 예제에서는 메서드를 interface **IFoo** 로 캐스팅 하 여 **Bar** 메서드의 구체적인 오버 로드를 선택 합니다.

```powershell
([IFoo] [Foo]::new()).Bar(1)
```

```Output
int: 1
```

## <a name="see-also"></a>참고 항목

[about_Objects](about_Objects.md)

[about_Properties](about_Properties.md)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)

