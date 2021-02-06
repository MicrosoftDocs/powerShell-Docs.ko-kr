---
title: 부록 A - 도움말 구문
description: 이 문서에서는 Get-Help에서 제공하는 cmdlet의 구문을 읽고 이해하는 방법을 설명합니다.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: b8fe218f2a9af1ad1ee6b88740414ecede0194bd
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99601828"
---
# <a name="appendix-a---help-syntax"></a>부록 A - 도움말 구문

다음 예제에서는 `Get-EventLog` cmdlet 도움말의 **SYNTAX** 섹션을 확인할 수 있습니다.

```powershell
help Get-EventLog
```

```Output
NAME
    Get-EventLog

SYNOPSIS
    Gets the events in an event log, or a list of the event logs, on the local or remote
    computers.


SYNTAX
    Get-EventLog [-LogName] <String> [[-InstanceId] <Int64[]>] [-After <DateTime>]
    [-AsBaseObject] [-Before <DateTime>] [-ComputerName <String[]>] [-EntryType {Error |
    Information | FailureAudit | SuccessAudit | Warning}] [-Index <Int32[]>] [-Message
    <String>] [-Newest <Int32>] [-Source <String[]>] [-UserName <String[]>]
    [<CommonParameters>]

    Get-EventLog [-AsString] [-ComputerName <String[]>] [-List] [<CommonParameters>]
```

이 예제에서는 도움말 중 관련된 부분만 표시합니다.

구문은 주로 다양한 여는 대괄호와 닫는 대괄호(`[]`) 집합으로 구성됩니다. 이것은 사용 방법에 따라 두 가지 의미를 갖습니다. 대괄호 안에 있는 모든 항목은 빈 대괄호 집합(`[]`)일 때를 제외하면 모두 선택 사항입니다. 빈 대괄호는 `<string[]>` 같은 데이터 유형 뒤에만 표시됩니다. 특정 매개 변수가 해당 형식의 값을 두 개 이상 사용할 수 있다는 뜻입니다.

`Get-EventLog`의 첫 번째 매개 변수 집합에 있는 첫 번째 매개 변수는 **LogName** 입니다. LogName은 대괄호로 묶여 있는데 이는 위치 매개 변수라는 뜻입니다. 다시 말해 올바른 위치에 지정되어 있다면 매개 변수 자체의 이름을 지정하는 것은 선택 사항입니다. 매개 변수 이름 다음에 있는 꺾쇠 괄호(`<>`)의 정보는 단일 **문자열** 값이 필요함을 나타냅니다. 전체 매개 변수 이름과 데이터 유형은 대괄호로 묶여 있지 않으므로 이 매개 변수 집합을 사용할 때는 **LogName** 매개 변수가 필요합니다.

```powershell
Get-EventLog [-LogName] <String>
```

두 번째 매개 변수는 **InstanceId** 입니다. 매개 변수 이름과 데이터 유형이 모두 대괄호로 묶여 있다는 사실에 주목하세요. **InstanceId** 매개 변수가 필수가 아닌 선택 사항이라는 뜻입니다. **InstanceId** 가 자체 대괄호로 묶여 있다는 사실도 주목해야 합니다. **LogName** 매개 변수처럼 이 매개 변수도 위치적이라는 뜻입니다. 데이터 유형 뒤에 마지막 대괄호 집합이 있습니다. 배열이나 쉼표로 구분된 목록 형태의 값을 두 개 이상 사용할 수 있다는 뜻입니다.

```
[[-InstanceId] <Int64[]>]
```

두 번째 매개 변수 집합에는 **List** 매개 변수가 있습니다. 매개 변수 이름 다음에 데이터 유형이 없기 때문에 스위치 매개 변수입니다. **List** 매개 변수가 지정되었다면 값은 **True** 입니다. 지정하지 않았다면 값은 **False** 입니다.

```
[-List]
```

명령의 구문 정보는 **Syntax** 매개 변수를 사용하는 `Get-Command`로 검색할 수도 있습니다. 필자가 자주 사용하는 편리한 지름길입니다. 도움말 정보의 여러 페이지를 살펴보지 않고도 명령 사용 방법을 빠르게 확인할 수 있습니다. 추가 정보가 필요하다면 필자는 다시 실제 도움말 콘텐츠를 사용합니다.

```powershell
Get-Command -Name Get-EventLog -Syntax
```

```Output
Get-EventLog [-LogName] <string> [[-InstanceId] <long[]>] [-ComputerName <string[]>] [-Newest <int>]
 [-After <datetime>] [-Before <datetime>] [-UserName <string[]>] [-Index <int[]> ]
 [-EntryType <string[]>] [-Source <string[]>] [-Message <string>] [-AsBaseObject]
 [<CommonParameters>]

Get-EventLog [-ComputerName <string[]>] [-List] [-AsString] [<CommonParameters>]
```

PowerShell에서 도움말 시스템을 많이 사용할수록 미묘한 차이를 쉽게 기억할 수 있습니다. 나중에는 거의 무의식적으로 사용할 수 있게 됩니다.
