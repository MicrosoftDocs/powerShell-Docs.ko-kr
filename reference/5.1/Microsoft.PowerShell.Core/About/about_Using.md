---
description: 세션에 사용 되는 네임 스페이스를 지정할 수 있습니다.
Locale: en-US
ms.date: 01/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: 2a02ff32b110d369c080dde695a8fc2369b1a5e2
ms.sourcegitcommit: 94d597c4fb38793bc49ca7610e2c9973b1e577c2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98619893"
---
# <a name="about-using"></a>사용 정보

## <a name="short-description"></a>간단한 설명
세션에 사용 되는 네임 스페이스를 지정할 수 있습니다.

## <a name="long-description"></a>자세한 설명

문을 사용 하 여 `using` 세션에서 사용 되는 네임 스페이스를 지정할 수 있습니다. 네임 스페이스를 추가 하면 .NET 클래스 및 멤버를 간단 하 게 사용할 수 있으며 스크립트 모듈 및 어셈블리에서 클래스를 가져올 수 있습니다.

`using`문은 스크립트나 모듈의 다른 문 앞에와 야 합니다. 매개 변수를 포함 하 여 앞에 주석 처리가 제거 문을 사용할 수 없습니다.

`using`문에는 변수가 포함 되지 않아야 합니다.

`using`문은 `using:` 변수에 대 한 범위 한정자와 혼동 해서는 안 됩니다. 자세한 내용은 [about_Remote_Variables](about_Remote_Variables.md)를 참조 하세요.

## <a name="namespace-syntax"></a>네임 스페이스 구문

형식을 확인할 .NET 네임 스페이스를 지정 하려면 다음을 수행 합니다.

```
using namespace <.NET-namespace>
```

네임 스페이스를 지정 하면 약식 이름으로 형식을 쉽게 참조할 수 있습니다.

## <a name="module-syntax"></a>모듈 구문

PowerShell 모듈에서 클래스를 로드 하려면 다음을 수행 합니다.

```
using module <module-name>
```

의 값은 `<module-name>` 모듈 이름, 전체 모듈 사양 또는 모듈 파일에 대 한 경로일 수 있습니다.

`<module-name>`가 경로인 경우 경로는 정규화 되거나 상대적일 수 있습니다. 상대 경로는 using 문을 포함 하는 스크립트를 기준으로 확인 됩니다.

`<module-name>`이 이름 또는 모듈 지정 인 경우 PowerShell은 **PSModulePath** 에서 지정 된 모듈을 검색 합니다.

모듈 사양은 다음과 같은 키를 포함 하는 해시 테이블입니다.

- `ModuleName` - **필수** 모듈 이름을 지정 합니다.
- `GUID` - **선택 사항** 모듈의 GUID를 지정 합니다.
- 또한 아래 세 키 중 하나를 지정 **해야** 합니다. 이러한 키는 함께 사용할 수 없습니다.
  - `ModuleVersion` -모듈의 허용 가능한 최소 버전을 지정 합니다.
  - `RequiredVersion` -필요한 모듈의 정확한 버전을 지정 합니다.
  - `MaximumVersion` -모듈의 허용 되는 최대 버전을 지정 합니다.

`using module`문은 `ModuleToProcess` 스크립트 모듈 또는 이진 모듈의 루트 모듈 ()에서 클래스를 가져옵니다. 모듈에 대 한 점 소스인 스크립트에 정의 된 클래스 또는 중첩 된 모듈에 정의 된 클래스를 일관 되 게 가져오지 않습니다. 모듈 외부의 사용자가 사용할 수 있도록 하려는 클래스는 루트 모듈에서 정의 해야 합니다.

스크립트 모듈을 개발 하는 동안 코드를 변경한 다음 `Import-Module` **Force** 매개 변수를 사용 하 여 새 버전의 모듈을 로드 하는 것이 일반적입니다. 이는 루트 모듈의 함수를 변경 하는 경우에만 작동 합니다. `Import-Module` 중첩 된 모듈을 다시 로드 하지 않습니다. 또한 업데이트 된 클래스를 로드 하는 방법은 없습니다.

최신 버전을 실행 하 고 있는지 확인 하려면 cmdlet을 사용 하 여 모듈을 언로드해야 합니다 `Remove-Module` . `Remove-Module` 모듈에 정의 된 루트 모듈, 모든 중첩 된 모듈 및 클래스를 제거 합니다. 그런 다음 및 문을 사용 하 여 모듈과 클래스를 다시 로드할 수 있습니다 `Import-Module` `using module` .

## <a name="assembly-syntax"></a>어셈블리 구문

.NET 어셈블리에서 형식을 미리 로드 하려면 다음을 수행 합니다.

```
using assembly <.NET-assembly-path>
using assembly <.NET-namespace>
```

어셈블리를 로드 하면 구문 분석 시 어셈블리의 .NET 형식이 스크립트에 미리 로드 됩니다. 이를 통해 미리 로드 된 어셈블리의 형식을 사용 하는 새 PowerShell 클래스를 만들 수 있습니다.

Windows PowerShell 5.1에서는 경로 이름 또는 이름을 기준으로 어셈블리를 로드할 수 있습니다. 이름을 사용 하는 경우 PowerShell은 .NET GAC (전역 어셈블리 캐시)에서 연결 된 어셈블리를 검색 합니다.

새 PowerShell 클래스를 만들지 않는 경우 대신 cmdlet을 사용 `Add-Type` 합니다. 자세한 내용은 [추가-형식](xref:Microsoft.PowerShell.Utility.Add-Type)을 참조 하세요.

## <a name="examples"></a>예제

### <a name="example-1---add-namespaces-for-typename-resolution"></a>예제 1-typename 확인에 대 한 네임 스페이스 추가

다음 스크립트는 "헬로 월드" 문자열에 대 한 암호화 해시를 가져옵니다.

및에서 및의에 대 한 참조를 간소화 하는 방법을 확인 `using namespace System.Text` `using namespace System.IO` `[UnicodeEncoding]` `System.Text` `[Stream]` `[MemoryStream]` `System.IO` 합니다.

```powershell
using namespace System.Text
using namespace System.IO

[string]$string = "Hello World"
## Valid values are "SHA1", "SHA256", "SHA384", "SHA512", "MD5"
[string]$algorithm = "SHA256"

[byte[]]$stringbytes = [UnicodeEncoding]::Unicode.GetBytes($string)

[Stream]$memorystream = [MemoryStream]::new($stringbytes)
$hashfromstream = Get-FileHash -InputStream $memorystream `
  -Algorithm $algorithm
$hashfromstream.Hash.ToString()
```

### <a name="example-2---load-classes-from-a-script-module"></a>예제 2-스크립트 모듈에서 클래스 로드

이 예제에는 다음 클래스를 정의 하는 클래스 \ **게임** 이라는 PowerShell 스크립트 모듈이 있습니다.

- **게임 데크**
- **게임 카드**

`Import-Module` 및 `#requires` 문은 모듈에서 정의한 대로 모듈 함수, 별칭 및 변수만 가져옵니다. 클래스는 가져올 수 없습니다. 이 `using module` 명령은 모듈을 가져오고 클래스 정의도 로드 합니다.

```powershell
using module CardGames
using namespace CardGames

[Deck]$deck = [Deck]::new()
$deck.Shuffle()
[Card[]]$hand1 = $deck.Deal(5)
[Card[]]$hand2 = $deck.Deal(5)
[Card[]]$hand3 = $deck.Deal(5)
```

### <a name="example-3---load-classes-from-an-assembly"></a>예제 3-어셈블리에서 클래스 로드

이 예제에서는 해당 클래스를 사용 하 여 새 PowerShell 클래스를 만들 수 있도록 어셈블리를 로드 합니다. 다음 스크립트는 **Directorycontext** 클래스에서 파생 되는 새 PowerShell 클래스를 만듭니다.

```powershell
using assembly 'C:\Program Files\PowerShell\7\System.DirectoryServices.dll'
using namespace System.DirectoryServices.ActiveDirectory

class myDirectoryClass : System.DirectoryServices.ActiveDirectory.DirectoryContext
{

  [DirectoryContext]$domain

  myDirectoryClass([DirectoryContextType]$ctx) : base($ctx)
  {
    $this.domain = [DirectoryContext]::new([DirectoryContextType]$ctx)
  }

}

$myDomain = [myDirectoryClass]::new([DirectoryContextType]::Domain)
$myDomain
```

```Output
domain                                                    Name UserName ContextType
------                                                    ---- -------- -----------
System.DirectoryServices.ActiveDirectory.DirectoryContext                    Domain
```
