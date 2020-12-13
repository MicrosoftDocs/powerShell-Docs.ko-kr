---
ms.date: 08/26/2019
ms.topic: reference
title: Cmdlet 매개 변수에서 와일드카드 문자 지원
description: Cmdlet 매개 변수에서 와일드카드 문자 지원
ms.openlocfilehash: 06693c62cd2613050bdeb9d6b12ad6e9597a9894
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646399"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Cmdlet 매개 변수에서 와일드카드 문자 지원

단일 리소스 대신 리소스 그룹에 대해 실행 되도록 cmdlet을 디자인 해야 하는 경우가 종종 있습니다. 예를 들어 cmdlet은 이름이 나 확장명이 같은 데이터 저장소의 모든 파일을 찾아야 할 수 있습니다. 리소스 그룹에 대해 실행 될 cmdlet을 디자인할 때 와일드 카드 문자에 대 한 지원을 제공 해야 합니다.

> [!NOTE]
> *와일드 카드 사용* 라고도 하는 와일드 카드 문자를 사용 합니다.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>와일드 카드를 사용 하는 Windows PowerShell Cmdlet

 많은 Windows PowerShell cmdlet은 해당 매개 변수 값에 와일드 카드 문자를 지원 합니다. 예를 들어 또는 매개 변수가 있는 거의 모든 cmdlet은 `Name` `Path` 이러한 매개 변수에 대해 와일드 카드 문자를 지원 합니다. 매개 변수를 포함 하는 대부분의 cmdlet에는 `Path` `LiteralPath` 와일드 카드 문자를 지원 하지 않는 매개 변수도 있습니다. 다음 명령은 와일드 카드 문자를 사용 하 여 이름에 Get 동사가 포함 된 현재 세션의 모든 cmdlet을 반환 하는 방법을 보여 줍니다.

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a>지원 되는 와일드 카드 문자

Windows PowerShell은 다음 와일드 카드 문자를 지원 합니다.

| 와일드카드 |                             설명                             |  예제   |     일치하는 항목      | 일치하지 않는 항목 |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | 지정 된 위치에서 시작 하 여 0 개 이상의 문자를 찾습니다. | `a*`       | A, ag, Apple     |                |
| ?        | 지정 된 위치의 모든 문자를 찾습니다.                     | `?n`       | , In, on       | 되었음            |
| [ ]      | 문자 범위를 찾습니다.                                       | `[a-l]ook` | 책, 쿡, 모양 | nook, 걸린 시간     |
| [ ]      | 지정 된 문자와 일치 합니다.                                    | `[bn]ook`  | 서적, nook       | 쿡, 살펴보기     |

와일드 카드 문자를 지 원하는 cmdlet을 디자인 하는 경우 와일드 카드 문자 조합을 허용 합니다. 예를 들어 다음 명령은 cmdlet을 사용 하 여 `Get-ChildItem` c:\Techdocs 폴더에 있고 문자 "a"부터 "l"로 시작 하는 모든 .txt 파일을 검색 합니다.

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

이전 명령은 range 와일드 카드를 사용 하 여 `[a-l]` 파일 이름이 문자 "a"부터 "l"로 시작 하 고, 파일 이름 `*` 및 **.txt** 확장명의 첫 문자 사이에 있는 모든 문자에 대 한 자리 표시자로 와일드 카드 문자를 사용 하도록 지정 합니다.

다음 예제에서는 "d" 문자를 제외 하 고 "a"부터 "f" 까지의 다른 모든 문자를 포함 하는 범위 와일드 카드 패턴을 사용 합니다.

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a>와일드 카드 패턴의 리터럴 문자 처리

지정 하는 와일드 카드 패턴에 와일드 카드 문자로 interpretted 서는 안 되는 리터럴 문자가 포함 된 경우에는 억음 문자 ( `` ` `` )를 이스케이프 문자로 사용 합니다. PowerShell API에서 리터럴 문자를 지정 하는 경우 단일 backtick을 사용 합니다. PowerShell 명령 프롬프트에서 리터럴 문자를 지정 하는 경우 두 개의 backticks을 사용 합니다.

예를 들어 다음 패턴에는 문자 그대로 수행 해야 하는 두 개의 대괄호가 포함 되어 있습니다.

PowerShell API에서 사용 하는 경우 다음을 사용 합니다.

- "John Smith \` [* ']"

PowerShell 명령 프롬프트에서 사용 되는 경우:

- "John Smith \` \` [* \` ']"

이 패턴은 "John Smith [Marketing]" 또는 "John Smith [Development]"와 일치 합니다. 예를 들어:

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a>Cmdlet 출력 및 와일드 카드 문자

Cmdlet 매개 변수가 와일드 카드 문자를 지 원하는 경우이 작업은 일반적으로 배열 출력을 생성 합니다.
사용자가 단일 항목만 사용할 수 있기 때문에 경우에 따라 배열 출력을 지 원하는 것은 바람직하지 않습니다. 예를 들어 `Set-Location` 사용자가 단일 위치만 설정 하므로 cmdlet은 배열 출력을 지원 하지 않습니다. 이 인스턴스에서 cmdlet은 여전히 와일드 카드 문자를 지원 하지만 단일 위치에 대해 해상도를 강제 적용 합니다.

## <a name="see-also"></a>관련 항목

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)

[WildcardPattern 클래스](/dotnet/api/system.management.automation.wildcardpattern)
