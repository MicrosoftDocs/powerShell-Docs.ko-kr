---
description: Windows PowerShell에서 WMI 개체를 가져오는 데 사용할 수 있는 WQL(WMI Query Language)에 대해 설명합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wql?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WQL
ms.openlocfilehash: c6fd523864d419fb400b7041e92ec8f0733724b7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223186"
---
# <a name="about-wql"></a>WQL 정보

## <a name="short-description"></a>간단한 설명

Windows PowerShell에서 WMI 개체를 가져오는 데 사용할 수 있는 WQL(WMI Query Language)에 대해 설명합니다.

## <a name="long-description"></a>자세한 설명

WQL은 WMI에서 정보를 가져오는 데 사용 되는 언어인 WMI (WMI(Windows Management Instrumentation)) 쿼리 언어입니다.

WQL을 사용 하 여 Windows PowerShell에서 WMI 쿼리를 수행할 필요는 없습니다.
대신 Get-WmiObject 또는 Get-CimInstance cmdlet의 매개 변수를 사용할 수 있습니다. WQL 쿼리는 표준 Get-WmiObject 명령 보다 다소 빠르지만, 명령이 수백 대의 시스템에서 실행 되는 경우 성능이 향상 됩니다. 그러나 성공적인 WQL 쿼리를 작성 하는 데 소요 되는 시간이 성능 향상 보다 더 중요 하지 않아야 합니다.

WQL을 사용 하는 데 필요한 기본 WQL 문은 Select, Where 및 From입니다.

## <a name="when-to-use-wql"></a>WQL을 사용 하는 경우

WMI를 사용할 때 특히 WQL을 사용 하는 경우 Windows PowerShell도 사용 하 고 있다는 것을 잊지 마십시오. WQL 쿼리가 정상적으로 작동 하지 않는 경우가 종종 있지만 표준 Windows PowerShell 명령을 사용 하 여 WQL 쿼리를 디버그 하는 것이 더 쉽습니다.

대역폭이 제한 된 원격 시스템에서 다량의 데이터를 반환 하는 경우가 아니면 약간 느리게 수행 되는 동일한 작업을 수행 하는 완벽 하 게 허용 되는 Windows cmdlet이 있는 경우 복잡 하 고 복잡 WQL 쿼리를 수행 하는 데 시간이 많이 소요 되는 경우가 거의 없습니다.

## <a name="using-the-select-statement"></a>SELECT 문 사용

일반적인 WMI 쿼리는 WMI 클래스의 모든 속성 또는 특정 속성을 가져오는 Select 문으로 시작 합니다. WMI 클래스의 모든 속성을 선택 하려면 별표 ()를 사용 \* 합니다. From 키워드는 WMI 클래스를 지정 합니다.

Select 문의 형식은 다음과 같습니다.

```
Select <property> from <WMI-class>
```

예를 들어 다음 Select 문은 Win32_Bios WMI 클래스의 인스턴스에서 모든 속성 (*)을 선택 합니다.

```
Select * from Win32_Bios
```

WMI 클래스의 특정 속성을 선택 하려면 Select 및 From 키워드 사이에 속성 이름을 추가 합니다.

다음 쿼리는 Win32_Bios WMI 클래스의 BIOS 이름만 선택 합니다. 명령은 $queryName 변수에 쿼리를 저장 합니다.

```
Select Name from Win32_Bios
```

둘 이상의 속성을 선택 하려면 쉼표를 사용 하 여 속성 이름을 구분 합니다.
다음 WMI 쿼리는 Win32_Bios WMI 클래스의 이름 및 버전을 선택 합니다. 명령은 $queryNameVersion 변수에 쿼리를 저장 합니다.

```
Select name, version from Win32_Bios
```

## <a name="using-the-wql-query"></a>WQL 쿼리 사용

Windows PowerShell 명령에서 WQL 쿼리를 사용 하는 방법에는 세 가지가 있습니다.

- Get-WmiObject cmdlet 사용
- Get-CimInstance cmdlet 사용
- [Wmisearcher] 형식 액셀러레이터를 사용 합니다.

## <a name="using-the-get-wmiobject-cmdlet"></a>GET-WMIOBJECT CMDLET 사용

WQL 쿼리를 사용 하는 가장 기본적인 방법은 다음 예제와 같이 따옴표 (문자열)로 묶고 쿼리 문자열을 Get-WmiObject cmdlet의 쿼리 매개 변수 값으로 사용 하는 것입니다.

```powershell
Get-WmiObject -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

다음 명령에 표시 된 것 처럼 WQL 문을 변수에 저장 한 다음이 변수를 쿼리 매개 변수 값으로 사용할 수도 있습니다.

```powershell
$query = "Select * from Win32_Bios"
Get-WmiObject -Query $query
```

모든 WQL 문에 두 형식 중 하나를 사용할 수 있습니다. 다음 명령은 $queryName 변수의 쿼리를 사용 하 여 시스템 BIOS의 이름 및 버전 속성만 가져옵니다.

```powershell
$queryNameVersion = "Select Name, Version from Win32_Bios"
Get-WmiObject -Query $queryNameVersion
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

Get-WmiObject cmdlet의 매개 변수를 사용 하 여 동일한 결과를 얻을 수 있습니다. 예를 들어 다음 명령은 Win32_Bios WMI 클래스 인스턴스의 이름 및 버전 속성 값도 가져옵니다.

```powershell
Get-WmiObject -Class Win32_Bios -Property Name, Version
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

## <a name="using-the-get-ciminstance-cmdlet"></a>CIMINSTANCE 개체로 CMDLET 사용

Windows PowerShell 3.0 부터는 Get-CimInstance cmdlet을 사용 하 여 WQL 쿼리를 실행할 수 있습니다.

Get-CimInstance은 WMI 클래스를 포함 하 여 CIM 규격 클래스의 인스턴스를 가져옵니다. Windows PowerShell 3.0을 소개 하는 CIM cmdlet은 WMI cmdlet과 동일한 작업을 수행 합니다. CIM cmdlet은 WSMan (WS-Management) 표준과 CIM(Common Information Model) (CIM) 표준을 준수 하 여 cmdlet이 동일한 기술을 사용 하 여 다른 운영 체제를 실행 하는 컴퓨터 및 컴퓨터를 관리할 수 있도록 합니다.

다음 명령은 Get-CimInstance cmdlet을 사용 하 여 WQL 쿼리를 실행 합니다.

Get-WmiObject와 함께 사용할 수 있는 모든 WQL 쿼리를 Ciminstance 개체로와 함께 사용할 수도 있습니다.

```powershell
Get-CimInstance -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

Get-CimInstance는 Get-WmiObject 반환 하는 ManagementObject 대신 Ciminstance 개체로 개체를 반환 하지만 개체는 매우 유사 합니다.

```
(Get-CimInstance -Query "Select * from Win32_Bios").GetType().FullName
Microsoft.Management.Infrastructure.CimInstance
(Get-WmiObject -Query "Select * from Win32_Bios").GetType().FullName
System.Management.ManagementObject
```

## <a name="using-the-wmisearcher-type-accelerator"></a>[Wmisearcher] 형식 액셀러레이터 사용

[Wmisearcher] 형식 액셀러레이터는 WQL 문 문자열에서 ManagementObjectSearcher 개체를 만듭니다. ManagementObjectSearcher 개체에는 많은 속성 및 메서드가 있지만 가장 기본적인 메서드는 지정 된 WMI 쿼리를 호출 하 고 결과 개체를 반환 하는 Get 메서드입니다.

[Wmisearcher]를 사용 하 여 ManagementObjectSearcher .NET Framework 클래스에 쉽게 액세스할 수 있습니다. 이렇게 하면 WMI를 쿼리하고 쿼리를 수행 하는 방법을 구성할 수 있습니다.

[Wmisearcher] 유형 가속기를 사용 하려면 다음을 수행 합니다.

1. WQL 문자열을 ManagementObjectSearcher 개체로 캐스팅 합니다.
2. ManagementObjectSearcher 개체의 Get 메서드를 호출 합니다.

예를 들어 다음 명령은 "모두 선택" 쿼리를 캐스팅 하 고 결과를 $bios 변수에 저장 한 다음 $bios 변수에 ManagementObjectSearcher 개체의 Get 메서드를 호출 합니다.

```powershell
$bios = [wmisearcher]"Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

참고: 선택한 개체 속성만 기본적으로 표시 됩니다. 이러한 속성은 Types.ps1xml 파일에 정의 되어 있습니다.

[Wmisearcher] 형식 액셀러레이터를 사용 하 여 쿼리 또는 변수를 캐스팅할 수 있습니다. 다음 예제에서는 [wmisearcher] 형식 액셀러레이터를 사용 하 여 변수를 캐스팅 합니다. 결과는 동일 합니다.

```powershell
[wmisearcher]$bios = "Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

[Wmisearcher] 형식 액셀러레이터를 사용 하는 경우 다음 명령에 표시 된 것 처럼 쿼리 문자열을 ManagementObjectSearcher 개체로 변경 합니다.

```
$a = "Select * from Win32_Bios"
$a.GetType().FullName
System.String

$a = [wmisearcher]"Select * from Win32_Bios"
$a.GetType().FullName
System.Management.ManagementObjectSearcher
```

이 명령 형식은 모든 쿼리에서 작동 합니다. 다음 명령은 Win32_Bios WMI 클래스의 Name 속성 값을 가져옵니다.

```powershell
$biosname = [wmisearcher]"Select Name from Win32_Bios"
$biosname.Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

이 작업을 단일 명령으로 수행할 수 있지만이 명령은 해석 하기가 약간 더 어렵습니다.

이 형식에서는 [wmisearcher] 형식 액셀러레이터를 사용 하 여 WQL 쿼리 문자열을 ManagementObjectSearcher로 캐스팅 한 다음 개체에 대해 Get 메서드를 호출 합니다. 모두 단일 명령으로 호출 합니다. 메서드를 호출 하기 전에 Windows PowerShell에서 문자열을 캐스트 하도록 캐스트 된 문자열을 묶는 괄호 ()입니다.

```powershell
([wmisearcher]"Select name from Win32_Bios").Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

## <a name="using-the-basic-wql-where-statement"></a>기본 WQL WHERE 문 사용

Where 문은 Select 문이 반환 하는 데이터에 대 한 조건을 설정 합니다.

Where 문의 형식은 다음과 같습니다.

```
where <property> <operator> <value>
```

다음은 그 예입니다. 

```
where Name = 'Notepad.exe'
```

Where 문은 다음 예제와 같이 Select 문에 사용 됩니다.

```
Select * from Win32_Process where Name = 'Notepad.exe'
```

Where 문을 사용 하는 경우 속성 이름 및 값은 정확 해야 합니다.

예를 들어 다음 명령은 로컬 컴퓨터에서 메모장 프로세스를 가져옵니다.

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad.exe'"
```

그러나 프로세스 이름에 ".exe" 파일 이름 확장명이 포함 되어 있으므로 다음 명령은 실패 합니다.

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad'"
```

## <a name="where-statement-comparison-operators"></a>WHERE 문 비교 연산자

WQL Where 문에는 다음과 같은 연산자를 사용할 수 있습니다.

```
Operator    Description
-----------------------
=           Equal
!=          Not equal
<>          Not equal
<           Less than
>           Greater than
<=          Less than or equal
>=          Greater than or equal
LIKE        Wildcard match
IS          Evaluates null
ISNOT       Evaluates not null
ISA         Evaluates a member of a WMI class
```

다른 연산자가 있지만 비교를 수행 하는 데 사용 되는 연산자입니다.

예를 들어 다음 쿼리는 Win32_Process 클래스에서 프로세스 우선 순위가 11 이상인 프로세스의 이름 및 우선 순위 속성을 선택 합니다. Get-WmiObject cmdlet은 쿼리를 실행 합니다.

```powershell
$highPriority = "Select Name, Priority from Win32_Process " +
  "where Priority >= 11"
Get-WmiObject -Query $highPriority
```

## <a name="using-the-wql-operators-in-the-filter-parameter"></a>FILTER 매개 변수에 WQL 연산자 사용

WQL 연산자는 Get-WmiObject 또는 Get-CimInstance cmdlet의 Filter 매개 변수 값 뿐만 아니라 이러한 cmdlet의 쿼리 매개 변수 값에도 사용할 수 있습니다.

예를 들어 다음 명령은 ProcessID 값이 1004 보다 큰 마지막 5 개 프로세스의 이름 및 ProcessID 속성을 가져옵니다. 이 명령은 Filter 매개 변수를 사용 하 여 ProcessID 조건을 지정 합니다.

```powershell
Get-WmiObject -Class Win32_Process `
-Property Name, ProcessID -Filter "ProcessID >= 1004" |
Sort ProcessID | Select Name, ProcessID -Last 5
```

```output
Name                                 ProcessID
----                                 ---------
SROSVC.exe                                4220
WINWORD.EXE                               4664
TscHelp.exe                               4744
SnagIt32.exe                              4748
WmiPrvSE.exe                              5056
```

## <a name="using-the-like-operator"></a>LIKE 연산자 사용

Like 연산자를 사용 하면 와일드 카드 문자를 사용 하 여 WQL 쿼리 결과를 필터링 할 수 있습니다.

```
Like Operator  Description
--------------------------------------------------
[]             Character in a range [a-f] or a set
               of characters [abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

^              Character not in a range [^a-f] or
               not in a set [^abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

%              A string of zero or more characters

_              One character.
(underscore)   NOTE: To use a literal underscore
               in a query string, enclose it in
               square brackets [_].
```

와일드 카드 문자 또는 범위 연산자 없이 Like 연산자를 사용 하는 경우 같음 연산자 (=) 처럼 동작 하며 패턴과 정확히 일치 하는 경우에만 개체를 반환 합니다.

Range 연산을 백분율 와일드 카드 문자와 결합 하 여 간단 하면서도 강력한 필터를 만들 수 있습니다.

### <a name="like-operator-examples"></a>LIKE 연산자 예제

#### <a name="example-1-range"></a>예 1: [ \<range> ]

다음 명령을 사용 하 여 메모장을 시작한 다음 이름이 "H"와 "N" (대/소문자 구분 안 함)로 시작 하는 Win32_Process 클래스의 인스턴스를 검색 합니다.

쿼리가 Notepad.exe를 통해 Hotpad.exe의 모든 프로세스를 반환 해야 합니다.

```powershell
Notepad   # Starts Notepad
$query = "Select * from win32_Process where Name LIKE '[H-N]otepad.exe'"
Get-WmiObject -Query $query | Select Name, ProcessID
```

```output
Name                                ProcessID
----                                ---------
notepad.exe                              1740
```

#### <a name="example-2-range-and-"></a>예 2: [ \<range> ] 및%

다음 명령은 이름과 P (대/소문자 구분 안 함) 사이에 있는 문자로 시작 하는 모든 프로세스와 임의의 조합에서 0 개 이상의 문자로 시작 하는 모든 프로세스를 선택 합니다.

Get-WmiObject cmdlet은 쿼리를 실행 하 고, Select-Object cmdlet은 Name 및 ProcessID 속성을 가져오며, Sort-Object cmdlet은 이름을 기준으로 결과를 사전순으로 정렬 합니다.

```powershell
$query = "Select * from win32_Process where name LIKE '[A-P]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-3-not-in-range-"></a>예 3: 범위에 없음 (^)

다음 명령은 이름이 A, S, W, P, R, C, U, N 중 하나로 시작 하지 않는 프로세스를 가져옵니다.

0 개 이상의 문자를 팔 로우 합니다.

```powershell
$query = "Select * from win32_Process where name LIKE '[^ASWPRCUN]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-4-any-characters----or-none-"></a>예 4: 모든 문자 또는 없음 (%)

다음 명령은 이름이 "calc"로 시작 하는 프로세스를 가져옵니다.
WQL 의% 기호는 \* 정규식의 별표 () 기호와 같습니다.

```powershell
$query = "Select * from win32_Process where Name LIKE 'calc%'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                               ProcessID
----                               ---------
calc.exe                                4424
```

#### <a name="example-5-one-character-_"></a>예 5: 한 문자 (_)

다음 명령은 "c_lc.exe" 패턴이 있는 이름을 가진 프로세스를 가져옵니다. 여기서 밑줄 문자는 한 문자를 나타냅니다. 이 패턴은 calc.exe czlc.exe 또는 c9lc.exe를 통해 모든 이름을 찾지만 "c"와 "l"이 둘 이상의 문자로 구분 된 이름과는 일치 하지 않습니다.

```powershell
$query = "Select * from Win32_Process where Name LIKE 'c_lc.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                                 ProcessID
----                                 ---------
calc.exe                                  4424
```

#### <a name="example-6-exact-match"></a>예 6: 정확히 일치

다음 명령은 WLIDSVC.exe 이라는 프로세스를 가져옵니다. 쿼리에서 Like 키워드를 사용 하는 경우에도 값에 와일드 카드 문자가 포함 되지 않으므로 정확히 일치 해야 합니다.

```powershell
$query = "Select * from win32_Process where name LIKE 'WLIDSVC.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```powershell

```output
Name                                 ProcessID
----                                 ---------
WLIDSVC.exe                                84
```

## <a name="using-the-or-operator"></a>OR 연산자 사용

여러 독립 조건을 지정 하려면 또는 키워드를 사용 합니다. Where 절에 또는 키워드가 표시 됩니다. 두 개 이상의 조건에 대해 포괄적 OR 연산을 수행 하 고 조건을 충족 하는 항목을 반환 합니다.

Or 연산자의 형식은 다음과 같습니다.

```
Where <property> <operator> <value> or <property> <operator> <value> ...
```

예를 들어 다음 명령은 Win32_Process WMI 클래스의 모든 인스턴스를 가져오지만 프로세스 이름이 winword.exe 또는 excel.exe 경우에만 반환 합니다.

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe'"
Get-WmiObject -Query $q
```

또는 문은 세 개 이상의 조건에서 사용할 수 있습니다. 다음 쿼리에서 또는 문은 Winword.exe, Excel.exe 또는 Powershell.exe를 가져옵니다.

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe' or Name='powershell.exe'"
```

## <a name="using-the-and-operator"></a>AND 연산자 사용

여러 관련 조건을 지정 하려면 및 키워드를 사용 합니다. 및 키워드가 Where 절에 나타납니다. 모든 조건을 충족 하는 항목을 반환 합니다.

And 연산자의 형식은 다음과 같습니다.

```
Where <property> <operator> <value> and <property> <operator> <value> ...
```

예를 들어 다음 명령은 이름이 "Winword.exe"이 고 프로세스 ID가 6512 인 프로세스를 가져옵니다.

명령은 Get-CimInstance cmdlet을 사용 합니다.

```powershell
$q = "Select * from Win32_Process where Name = 'winword.exe' " +
  "and ProcessID =6512"
Get-CimInstance -Query $q
```

```output
ProcessId   Name             HandleCount      WorkingSetSize   VirtualSize
---------   ----             -----------      --------------   -----------
# 6512      WINWORD.EXE      768              117170176        633028608
```

Like 연산자를 비롯 한 모든 연산자는 Or 및 And 연산자와 함께 사용할 수 있습니다. 그리고 먼저 처리할 절을 Windows PowerShell에 지시 하는 괄호를 사용 하 여 단일 쿼리에서 Or 및 And 연산자를 결합할 수 있습니다.

이 명령은 Windows PowerShell 연속 문자 (')를 사용 하 여 명령을 두 줄로 나눕니다.

```powershell
$q = "Select * from Win32_Process `
where (Name = 'winword.exe' or Name = 'excel.exe') and HandleCount > 700"
Get-CimInstance -Query $q
```

```output
ProcessId    Name             HandleCount      WorkingSetSize   VirtualSize
---------    ----             -----------      --------------   -----------
     6512    WINWORD.EXE      797              117268480        634425344
     9610    EXCEL.EXE        727               38858752        323227648
```

## <a name="searching-for-null-values"></a>NULL 값 검색

예기치 않은 결과가 발생할 수 있으므로 WMI에서 null 값을 검색 하는 것은 어려운 일입니다. Null이 0이 아닌 경우 또는 빈 문자열과 일치 하지 않습니다. 일부 WMI 클래스 속성은 초기화 되 고 다른 속성은 초기화 되지 않으므로 null에 대 한 검색이 모든 속성에 대해 작동 하지 않을 수 있습니다.

Null 값을 검색 하려면 "null" 값을 포함 하는 Is 연산자를 사용 합니다.

예를 들어 다음 명령은 IntallDate 속성에 대해 null 값이 있는 프로세스를 가져옵니다. 명령은 많은 프로세스를 반환 합니다.

```powershell
$q = "Select * from Win32_Process where InstallDate is null"
Get-WmiObject -Query $q
```

반면, 다음 명령은 Description 속성에 대해 null 값이 있는 사용자 계정을 가져옵니다. 대부분의 사용자 계정에 Description 속성에 대 한 값이 없는 경우에도이 명령은 사용자 계정을 반환 하지 않습니다.

```powershell
$q = "Select * from Win32_UserAccount where Description is null"
Get-WmiObject -Query $q
```

Description 속성에 대 한 값이 없는 사용자 계정을 찾으려면 같음 연산자를 사용 하 여 빈 문자열을 가져옵니다. 빈 문자열을 나타내려면 두 개의 연속 작은따옴표를 사용 합니다.

```powershell
$q = "Select * from Win32_UserAccount where Description = '' "
```

## <a name="using-true-or-false"></a>TRUE 또는 FALSE 사용

WMI 개체의 속성에서 부울 값을 가져오려면 True 및 False를 사용 합니다.
대소문자를 구분하지 않습니다.

다음 WQL 쿼리는 도메인에 가입 된 컴퓨터에서 로컬 사용자 계정만 반환 합니다.

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = True"
Get-CimInstance -Query $q
```

도메인 계정을 찾으려면 다음 예에 표시 된 것 처럼 False 값을 사용 합니다.

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = False"
Get-CimInstance -Query $q
```

## <a name="using-the-escape-character"></a>이스케이프 문자 사용

WQL은 이스케이프 문자로 백슬래시를 사용 \) 합니다. 이는 억음 문자 (')를 사용 하는 Windows PowerShell과 다릅니다.

따옴표와 따옴표에 사용 되는 문자는 잘못 해석 되지 않도록 이스케이프 처리 해야 하는 경우가 많습니다.

이름이 작은따옴표로 묶여 있는 사용자를 찾으려면 다음 명령에 표시 된 것 처럼 백슬래시를 사용 하 여 작은따옴표를 이스케이프 합니다.

```powershell
$q = "Select * from Win32_UserAccount where Name = 'Tim O\'Brian'"
Get-CimInstance -Query $q
```

```output
Name             Caption          AccountType      SID              Domain
----             -------          -----------      ---              ------
Tim O'Brian      FABRIKAM\TimO    512              S-1-5-21-1457... FABRIKAM
```

경우에 따라 백슬래시도 이스케이프 해야 합니다. 예를 들어 다음 명령은 Caption 값의 백슬래시로 인해 잘못 된 쿼리 오류를 생성 합니다.

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\TimO'"
Get-CimInstance -Query $q
```

```output
Get-CimInstance : Invalid query
At line:1 char:1
+ Get-CimInstance -Query $q
+ ~~~~~~~~~~~
  + CategoryInfo          : InvalidArgument: (:) [Get-CimInstance], CimExcep
  + FullyQualifiedErrorId : HRESULT 0x80041017,Microsoft.Management.Infrastr
```

백슬래시를 이스케이프 하려면 다음 명령에 표시 된 것 처럼 두 번째 백슬래시 문자를 사용 합니다.

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\\TimO'"
Get-CimInstance -Query $q
```

## <a name="see-also"></a>참고 항목

[about_Special_Characters](about_Special_Characters.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_WMI](about_WMI.md)

[about_WMI_Cmdlets](about_WMI_Cmdlets.md)
