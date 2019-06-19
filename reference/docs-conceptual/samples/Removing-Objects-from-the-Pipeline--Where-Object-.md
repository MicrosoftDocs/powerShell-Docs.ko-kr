---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 파이프라인에서 개체 제거(Where Object)
ms.openlocfilehash: c47efd38e2ff40ce3b7bf50b161cc38de922c5da
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030871"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>파이프라인에서 개체 제거(Where-Object)

일반적으로 Windows PowerShell은 필요한 것보다 많은 개체를 만들어 파이프라인에 전달합니다. **Format** cmdlet을 사용하면 표시할 특정 개체의 속성을 지정할 수 있지만 전체 개체를 표시하지 않는 문제에는 도움이 되지 않습니다. 파이프라인 끝에 도달하기 전에 개체를 필터링하여 처음 만들어진 개체의 하위 집합에 대해서만 특정 작업을 수행할 수 있습니다.

Windows PowerShell에는 파이프라인에 있는 각 개체를 테스트하고 특정 테스트 조건을 만족하는 개체만 파이프라인을 통해 전달할 수 있는 `Where-Object` cmdlet이 포함되어 있습니다. 테스트를 통과하지 못한 개체는 파이프라인에서 제거됩니다. 테스트 조건은 `Where-Object` **FilterScript** 매개 변수의 값으로 제공합니다.

## <a name="performing-simple-tests-with-where-object"></a>Where-Object를 사용하여 간단한 테스트 수행

**FilterScript**의 값은 true 또는 false로 계산되는 하나의 *스크립트 블록*(하나 이상의 Windows PowerShell 명령이 중괄호({})로 묶여 있음)입니다. 이러한 스크립트 블록은 매우 간단할 수 있지만 비교 연산자와 같은 다른 Windows PowerShell 개념을 알고 있어야 만들 수 있습니다. 비교 연산자는 자신을 중심으로 양쪽에 표시되는 두 항목을 비교합니다. 비교 연산자의 이름은 '-' 문자로 시작됩니다. 기본 비교 연산자는 거의 모든 유형의 개체에서 작동하지만 고급 비교 연산자는 텍스트나 배열에서만 작동할 수 있습니다.

> [!NOTE]
> 기본적으로 Windows PowerShell 비교 연산자는 텍스트를 비교할 때 대/소문자를 구분합니다.

구문 오류가 발생할 수 있으므로 <, >, = 등의 기호는 비교 연산자로 사용할 수 없고 문자만 비교 연산자로 사용할 수 있습니다. 다음 표에는 기본 비교 연산자가 나와 있습니다.

|비교 연산자|의미|예제(true 반환)|
|-----------------------|-----------|--------------------------|
|-eq|같음|1 -eq 1|
|-ne|같지 않음|1 -ne 2|
|-lt|보다 작음|1 -lt 2|
|-le|작거나 같음|1 -le 2|
|-gt|보다 큼|2 -gt 1|
|-ge|크거나 같음|2 -ge 1|
|-like|비슷함(텍스트의 와일드카드 비교)|"file.doc" -like "f\*.do?"|
|-notlike|비슷하지 않음(텍스트의 와일드카드 비교)|"file.doc" -notlike "p\*.doc"|
|-contains|포함|1,2,3 -contains 1|
|-notcontains|포함 안 함|1,2,3 -notcontains 4|

Where-Object 스크립트 블록은 특수 변수 `$_`를 사용하여 파이프라인에 있는 현재 개체를 참조합니다. 다음은 이러한 동작을 보여 주는 예제입니다. 일련의 숫자 중에서 3보다 작은 숫자만 반환하려면 다음과 같이 Where-Object를 사용하여 숫자를 필터링하면 됩니다.

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a>개체 속성을 기반으로 필터링

`$_`가 현재 파이프라인 개체를 참조하므로 테스트를 위해 이 개체의 속성에 액세스할 수 있습니다.

예를 들어 WMI에서 Win32_SystemDriver 클래스를 살펴보면 특정 시스템에 수백 개의 시스템 드라이버가 있을 수 있지만 현재 실행 중인 드라이버와 같은 특정 시스템 드라이버 집합만 사용할 수 있습니다. Get-Member를 사용하여 Win32_SystemDriver 멤버(**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**)를 보면 관련 속성이 State이고 드라이버가 실행 중일 때 해당 값이 "Running"인 것을 확인할 수 있습니다. 다음과 같이 입력하면 시스템 드라이버를 필터링하여 실행 중인 드라이버만 선택할 수 있습니다.

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

그러나 이 목록에는 아직도 필요한 것보다 많은 항목이 포함되어 있으므로 다음과 같이 StartMode 값도 테스트하여 자동으로 시작되도록 설정된 드라이버만 선택하도록 필터링할 수 있습니다.

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
```

드라이버가 실행 중이라는 것을 앞에서 확인했기 때문에 이 목록에는 아직도 불필요한 정보가 포함되어 있습니다. 사실 이 시점에서 필요한 정보는 이름과 표시 이름뿐입니다. 다음 명령은 목록에 이러한 두 속성만 포함하여 출력을 훨씬 더 간단하게 만듭니다.

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

위의 명령에는 두 개의 Where-Object 요소가 있지만 다음과 같이 -and 논리 연산자를 사용하여 단일 Where-Object 요소로 표시할 수 있습니다.

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

다음 표에는 기본 논리 연산자가 나와 있습니다.

|논리 연산자|의미|예제(true 반환)|
|--------------------|-----------|--------------------------|
|-and|논리곱(둘 다 true일 경우 true임)|(1 -eq 1) -and (2 -eq 2)|
|-or|논리합(둘 중 하나만 true여도 true임)|(1 -eq 1) -or (1 -eq 2)|
|-not|논리 부정(true와 false를 반대로 바꿈)|-not (1 -eq 2)|
|\!|논리 부정(true와 false를 반대로 바꿈)|\!(1 -eq 2)|
