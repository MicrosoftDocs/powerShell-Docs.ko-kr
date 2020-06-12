---
title: 서식 지정, 별칭, 공급자 및 비교
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: eb23b048a50f10ea83d156c0499772b1be439336
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438004"
---
# <a name="chapter-5---formatting-aliases-providers-comparison"></a>5장 - 서식 지정, 별칭, 공급자 및 비교

## <a name="requirements"></a>요구 사항

이 장에 표시된 일부 예제에 SQL Server PowerShell 모듈이 필요합니다. 이 모듈은 [SMSS(SQL Server Management Studio)][SMSS]의 일부로 설치됩니다. 후속 장에서도 사용됩니다. 이 모듈을 Windows 10 랩 환경 컴퓨터에 다운로드하여 설치합니다.

## <a name="format-right"></a>오른쪽 정렬

4장에서는 가능한 한 왼쪽으로 필터링하는 방법을 배웠습니다. 명령의 출력을 수동으로 서식 지정하는 이 규칙은 출력이 가능한 한 오른쪽에서 발생해야 한다는 점을 제외하면 그 규칙과 비슷합니다.

가장 일반적인 format 명령은 `Format-Table` 및 `Format-List`입니다. `Format-Wide` 및 `Format-Custom`을 사용할 수도 있지만 일반적이지 않습니다.

3장에서 설명한 것처럼 사용자 지정 서식을 사용하지 않는 경우 4개 이상의 속성을 반환하는 명령은 기본적으로 목록으로 지정됩니다.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```Output
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

`Format-Table` cmdlet을 사용하여 서식 지정을 수동으로 재정의하고 목록 대신 테이블에 출력을 표시합니다.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can* |
Format-Table
```

```Output
 Status DisplayName  CanPauseAndContinue CanShutdown CanStop
 ------ -----------  ------------------- ----------- -------
Running Windows Time               False        True    True
```

`Get-Service`의 기본 출력은 테이블의 세 가지 속성입니다.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

`Format-List` cmdlet을 사용하여 기본 서식 지정을 재정의하고 결과를 목록으로 반환합니다.

```powershell
Get-Service -Name w32time | Format-List
```

```Output
Name                : w32time
DisplayName         : Windows Time
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
ServiceType         : Win32ShareProcess
```

단순히 `Get-Service`를 `Format-List`로 파이프하면 추가 속성이 반환됩니다. 특정 명령의 서식 지정이 백그라운드에서 설정되는 방식 때문에 이러한 결과가 모든 명령에서 발생하지는 않습니다.

format cmdlet을 사용할 때 가장 유의할 점은 이들이 PowerShell의 일반 개체와는 다른 형식 개체를 생성한다는 것입니다.

```powershell
Get-Service -Name w32time | Format-List | Get-Member
```

```Output
   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
autosizeInfo                            Property   Microsoft.PowerShell.Commands.Inter...
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
pageFooterEntry                         Property   Microsoft.PowerShell.Commands.Inter...
pageHeaderEntry                         Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEntryData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
formatEntryInfo                         Property   Microsoft.PowerShell.Commands.Inter...
outOfBand                               Property   bool outOfBand {get;set;}
writeStream                             Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
```

즉, format 명령은 대부분의 다른 명령으로 파이프할 수 없습니다. 일부 `Out-*` 명령으로 파이프될 수 있지만 그 이상은 불가능합니다. 이 때문에 줄의 끝부분에서 서식 지정을 수행하는 것이 좋습니다(오른쪽 정렬).

## <a name="aliases"></a>별칭

PowerShell에서 별칭은 특정 명령의 짧은 이름입니다. PowerShell에는 기본 제공 별칭 집합이 포함되어 있으며 사용자 고유의 별칭을 정의할 수도 있습니다.

`Get-Alias` cmdlet은 별칭을 찾는 데 사용됩니다. 명령의 별칭을 이미 알고 있는 경우 **Name** 매개 변수를 사용하여 별칭이 연결된 명령을 확인합니다.

```powershell
Get-Alias -Name gcm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
```

**Name** 매개 변수의 값에 여러 개의 별칭을 지정할 수 있습니다.

```powershell
Get-Alias -Name gcm, gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

**Name** 매개 변수는 위치 매개 변수이기 때문에 생략되는 경우가 종종 있습니다.

```powershell
Get-Alias gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gm -> Get-Member
```

명령의 별칭을 찾으려면 **Definition** 매개 변수를 사용해야 합니다.

```powershell
Get-Alias -Definition Get-Command, Get-Member
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

**Definition** 매개 변수는 위치 기준으로 사용할 수 없으므로 별도로 지정해야 합니다.

별칭은 키 입력을 줄여주므로 콘솔에 명령을 입력할 때는 좋습니다.
그러나 저장하거나 다른 사용자와 공유하는 스크립트 또는 코드에서는 사용하지 않아야 합니다. 이 책의 앞부분에서 설명한 것처럼 전체 cmdlet 및 매개 변수 이름을 사용하면 이해하기 더 쉽습니다(자체 문서화).

사용자 고유 별칭을 만드는 경우 이러한 별칭은 컴퓨터의 현재 PowerShell 세션에만 존재하므로 주의하세요.

## <a name="providers"></a>공급자

PowerShell의 공급자는 파일 시스템처럼 데이터 저장소에 액세스할 수 있는 인터페이스입니다. PowerShell에는 여러 가지 기본 제공 공급자가 있습니다.

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
Certificate          ShouldProcess                      {Cert}
WSMan                Credentials                        {WSMan}
```

이전 결과에서 볼 수 있듯이 레지스트리, 별칭, 환경 변수, 파일 시스템, 함수, 변수, 인증서 및 WSMan에 대한 기본 제공 공급자가 있습니다.

이러한 공급자가 데이터 저장소를 노출하는 데 사용하는 실제 드라이브는 `Get-PSDrive` cmdlet을 사용하여 확인할 수 있습니다. `Get-PSDrive` cmdlet은 공급자가 제공하는 드라이브를 표시할 뿐 아니라 네트워크 공유에 매핑된 드라이브를 비롯한 Windows 논리 드라이브도 표시합니다.

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
Alias                                  Alias
C                  14.41        112.10 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
WSMan                                  WSMan
```

Active Directory PowerShell 모듈 및 SQLServer PowerShell 모듈과 같은 타사 모듈은 모두 자체 PowerShell 공급자와 PSDrive를 추가합니다.

Active Directory 및 SQL Server PowerShell 모듈을 가져옵니다.

```powershell
Import-Module -Name ActiveDirectory, SQLServer
```

추가 PowerShell 공급자가 추가되었는지 확인합니다.

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
ActiveDirectory      Include, Exclude, Filter, Shoul... {AD}
SqlServer            Credentials                        {SQLSERVER}
```

이전 결과 집합에서 두 개의 새로운 PowerShell 공급자가 있습니다. 하나는 Active Directory용이고 다른 하나는 SQL Server용입니다.

각 모듈의 PSDrive도 추가되었습니다.

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
AD                                     ActiveDire... //RootDSE/
Alias                                  Alias
C                  19.38        107.13 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
SQLSERVER                              SqlServer     SQLSERVER:\
Variable                               Variable
WSMan                                  WSMan
```

PSDrive는 일반 파일 시스템과 마찬가지로 액세스할 수 있습니다.

```powershell
Get-ChildItem -Path Cert:\LocalMachine\CA
```

```Output
   PSParentPath: Microsoft.PowerShell.Security\Certificate::LocalMachine\CA

Thumbprint                                Subject
----------                                -------
FEE449EE0E3965A5246F000E87FDE2A065FD89D4  CN=Root Agency
D559A586669B08F46A30A133F8A9ED3D038E2EA8  OU=www.verisign.com/CPS Incorporated LIABI...
109F1CAED645BB78B3EA2B94C0697C740733031C  CN=Microsoft Windows Hardware Compatibility,...
```

## <a name="comparison-operators"></a>비교 연산자

PowerShell에는 값을 비교하거나 특정 패턴과 일치하는 값을 찾는 데 사용되는 다양한 비교 연산자가 포함되어 있습니다. 표 5-1은 PowerShell의 비교 연산자 목록입니다.

|    연산자    |                          정의                          |
| -------------- | ------------------------------------------------------------ |
| `-eq`          | 같음                                                     |
| `-ne`          | 같지 않음                                                 |
| `-gt`          | 초과                                                 |
| `-ge`          | 크거나 같음                                     |
| `-lt`          | 보다 작음                                                    |
| `-le`          | 작거나 같음                                        |
| `-Like`        | `*` 와일드카드 문자를 사용하여 일치                       |
| `-NotLike`     | `*` 와일드카드 문자를 사용하여 일치하지 않음              |
| `-Match`       | 지정된 정규식과 일치                     |
| `-NotMatch`    | 지정된 정규식과 일치하지 않음              |
| `-Contains`    | 컬렉션에 지정된 값이 포함되는지 확인        |
| `-NotContains` | 컬렉션에 특정 값이 포함되지 않는지 확인 |
| `-In`          | 컬렉션에 지정된 값이 있는지 확인           |
| `-NotIn`       | 컬렉션에 지정된 값이 없는지 확인       |
| `-Replace`     | 지정된 값을 대체                                 |

표 5-1에 나열된 모든 연산자는 대/소문자를 구분하지 않습니다. 표 5-1에 나열된 연산자 앞에 `c`를 추가하여 대/소문자를 구분합니다. 예를 들어 `-ceq`는 `-eq` 비교 연산자의 대/소문자 구분 버전입니다.

적절한 대/소문자의 "PowerShell"은 같음 비교 연산자를 사용하는 소문자 "powershell"과 같습니다.

```powershell
'PowerShell' -eq 'powershell'
```

```Output
True
```

같음 비교 연산자의 대/소문자 구분 버전을 사용하는 것과는 다릅니다.

```powershell
'PowerShell' -ceq 'powershell'
```

```Output
False
```

같지 않음 비교 연산자는 조건을 반대로 바꿉니다.

```powershell
'PowerShell' -ne 'powershell'
```

```Output
False
```

보다 큼, 크거나 같음, 보다 작음, 작거나 같음은 모두 문자열 또는 숫자 값에 유효합니다.

```powershell
5 -gt 5
```

```Output
False
```

이전 예제에서 크거나 같음을 사용하면 5는 5와 같기 때문에 **부울**이 true를 반환합니다.

```powershell
5 -ge 5
```

```Output
True
```

이전의 두 예제에서 얻은 결과에서 보다 작음과 작거나 같음이 어떻게 작동하는지 추측할 수 있을 것입니다.

```powershell
5 -lt 10
```

```Output
True
```

숙련된 PowerShell 사용자라도 `-Like` 연산자와 `-Match` 연산자를 혼동할 수 있습니다. `-Like`는 와일드카드 문자 `*` 및 `?`와 함께 사용하여 "like" 일치를 수행합니다.

```powershell
'PowerShell' -like '*shell'
```

```Output
True
```

`-Match`는 정규식을 사용하여 일치를 수행합니다.

```powershell
'PowerShell' -match '^*.shell$'
```

```Output
True
```

범위 연산자를 사용하여 변수에서 1부터 10까지의 숫자를 저장합니다.

```powershell
$Numbers = 1..10
```

```Output
```

`$Numbers` 변수에 15가 포함되어 있는지 확인합니다.

```powershell
$Numbers -contains 15
```

```Output
False
```

숫자 10이 포함되어 있는지 확인합니다.

```powershell
$Numbers -contains 10
```

```Output
True
```

`-NotContains`는 논리를 반대로 바꾸어 `$Numbers` 변수에 특정 값이 포함되지 않는지 확인합니다.

```powershell
$Numbers -notcontains 15
```

```Output
True
```

이전 예제에서는 `$Numbers` 변수에 15가 포함되지 않기 때문에 **부울**이 true를 반환합니다. 하지만 숫자 10을 포함하므로 테스트하면 false 값을 반환합니다.

```powershell
$Numbers -notcontains 10
```

```Output
False
```

"in" 비교 연산자는 PowerShell 버전 3.0에 처음 도입되었습니다. 이는 값이 배열 "내"에 있는지 확인하는 데 사용됩니다. `$Numbers` 변수는 여러 값을 포함하기 때문에 배열로 간주됩니다.

```powershell
15 -in $Numbers
```

```Output
False
```

즉, `-in`은 반대 방향이라는 점을 제외하면 contains 비교 연산자와 동일한 테스트를 수행합니다.

```powershell
10 -in $Numbers
```

```Output
True
```

`$Numbers` 배열에 15가 없으므로 다음 예제에서 false가 반환됩니다.

```powershell
15 -in $Numbers
```

```Output
False
```

`-contains` 연산자와 마찬가지로 `not`은 `-in` 연산자에 대한 논리를 반대로 바꿉니다.

```powershell
10 -notin $Numbers
```

```Output
False
```

이전 예제에서는 `$Numbers` 배열에 10이 포함되어 있고 조건이 10이 포함되지 않은 것을 확인하는 테스트였기 때문에 false를 반환합니다.

15는 `$Numbers` 배열 "내에 없으므로" **부울**은 true를 반환합니다.

```powershell
15 -notin $Numbers
```

```Output
True
```

`-replace` 연산자는 당연한 작업을 수행합니다. 즉, 무언가를 바꾸는 데 사용됩니다. 값을 하나만 지정하면 해당 값이 없어집니다. 다음 예제에서는 "Shell"이 없어집니다.

```powershell
'PowerShell' -replace 'Shell'
```

```Output
Power
```

값을 다른 값으로 바꾸려면 바꾸려는 패턴 뒤에 새 값을 지정합니다. SQL Saturday in Baton Rouge는 필자가 매년 강연을 하려고 노력하는 행사입니다. 다음 예제에서는 "Saturday"라는 단어를 약어인 "Sat"로 바꿉니다.

```powershell
'SQL Saturday - Baton Rouge' -Replace 'saturday','Sat'
```

```Output
SQL Sat - Baton Rouge
```

replace 연산자가 작동하는 방식과 비슷하게 항목을 바꾸는 데 사용할 수 있는 **Replace()** 같은 메서드도 있습니다. 그러나 `-Replace` 연산자는 기본적으로 대/소문자를 구분하지 않으며 **Replace()** 메서드는 대/소문자를 구분합니다.

```powershell
'SQL Saturday - Baton Rouge'.Replace('saturday','Sat')
```

```Output
SQL Saturday - Baton Rouge
```

이전 예제에서 "Saturday"라는 단어는 바뀌지 않았습니다. 원래와 다른 대/소문자로 지정되었기 때문입니다. "Saturday"라는 단어를 원래와 동일한 대/소문자로 지정하면 **Replace()** 메서드가 예상대로 값을 바꿉니다.

```powershell
'SQL Saturday - Baton Rouge'.Replace('Saturday','Sat')
```

```Output
SQL Sat - Baton Rouge
```

메서드를 사용하여 데이터를 변환할 때는 터키 테스트 실패와 같은 예기치 않은 문제가 발생할 수 있으므로 주의해야 합니다. 예를 들어 [Pester를 사용하여 다른 문화권에서 PowerShell 코드 테스트][]라는 블로그 문서를 참조하세요. 이러한 유형의 문제를 방지하려면 가능한 경우 메서드 대신 연산자를 사용하는 것이 좋습니다.

이전 예제와 같이 비교 연산자를 사용할 수 있지만 필자는 일반적으로 `Where-Object` cmdlet과 함께 사용하여 일부 유형의 필터링을 수행합니다.

## <a name="summary"></a>요약

이 장에서는 오른쪽 정렬, 별칭, 공급자 및 비교 연산자를 포함하는 다양한 항목을 배웠습니다.

## <a name="review"></a>검토

1. 가능한 한 오른쪽으로 서식 지정을 수행해야 하는 이유는 무엇인가요?
1. `%` 별칭에 대한 실제 cmdlet이 무엇인지 확인하는 방법은 무엇인가요?
1. 저장하는 스크립트나 다른 사용자와 공유하는 코드에서 별칭을 사용하면 안 되는 이유는 무엇인가요?
1. 레지스트리 공급자 중 하나와 연결된 드라이브에 대한 디렉터리 목록을 수행합니다.
1. replace 메서드 대신 replace 연산자를 사용할 경우의 주요 이점 중 하나는 무엇인가요?

## <a name="recommended-reading"></a>권장 참조 항목

- [Format-Table][]
- [Format-List][]
- [Format-Wide][]
- [about_Aliases][]
- [about_Providers][]
- [about_Comparison_Operators][]
- [about_Arrays][]

<!-- link references -->
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
[Format-Table]: /powershell/module/microsoft.powershell.utility/format-table
[Format-List]: /powershell/module/microsoft.powershell.utility/format-list
[Format-Wide]: /powershell/module/microsoft.powershell.utility/format-wide
[about_Aliases]: /powershell/module/microsoft.powershell.core/about/about_aliases
[about_Providers]: /powershell/module/microsoft.powershell.core/about/about_providers
[about_Comparison_Operators]: /powershell/module/microsoft.powershell.core/about/about_comparison_operators
[about_Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Pester를 사용하여 다른 문화권에서 PowerShell 코드 테스트]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/
