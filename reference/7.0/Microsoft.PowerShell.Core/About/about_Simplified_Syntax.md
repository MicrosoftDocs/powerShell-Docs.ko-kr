---
description: 개체 컬렉션에 대 한 스크립팅 필터를 보다 쉽고 자연 스러운 방식으로 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_simplified_syntax?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Simplified_Syntax
ms.openlocfilehash: 9c9587a2030abeb892115c5e604b4cac921c5a99
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220586"
---
# <a name="about_simplified_syntax"></a>about_Simplified_Syntax

## <a name="short-description"></a>간단한 설명
개체 컬렉션에 대 한 스크립팅 필터를 보다 쉽고 자연 스러운 방식으로 설명 합니다.

## <a name="long-description"></a>자세한 설명

Windows PowerShell 3.0에 도입 된 간단한 구문을 사용 하면 스크립트 블록을 사용 하지 않고 일부 필터 명령을 작성할 수 있습니다. 단순화 된 구문은 자연어와 거의 유사 하며, 주로 명령과 `Where-Object` `ForEach-Object` 해당 별칭 및로 파이프 하는 개체의 컬렉션에 유용 합니다 `where` `foreach` .

스크립트 블록 내에서 자동 변수를 참조 하지 않고 컬렉션 (가장 일반적으로는 배열)의 멤버에 대해 메서드를 사용할 수 있습니다 `$_` .

다음 두 호출을 고려 합니다.

### <a name="standard-syntax"></a>표준 구문

```powershell
dir Cert:\LocalMachine\Root | where { $_.FriendlyName -eq 'Verisign' }
dir Cert:\ -Recurse | foreach { $_.GetKeyAlgorithm() }```

### Simplified syntax

Under the simplified syntax, comparison operators that work on members of objects in a
collection are treated as parameters. You can invoke a method on objects in a
collection without referring to the automatic variable `$_` inside a script block.
Compare the following two invocations to those of the previous example:

```powershell
dir Cert:\LocalMachine\Root | where FriendlyName -eq 'Verisign'
dir Cert:\ -Recurse | foreach GetKeyAlgorithm
```

두 구문이 모두 작동 하는 동안 간소화 된 구문은 스크립트 블록 내의 자동 변수를 참조 하지 않고 결과를 반환 합니다 `$_` .
메서드 이름은 `GetKeyAlgorithm` 의 매개 변수로 처리 됩니다 `ForEach-Object` .
단순한 구문은 지정 된 인수가 적용 되지 않은 항목에 대해 결과를 반환 하지 않기 때문에 두 번째 명령은 오류 없이 동일한 결과를 반환 합니다.

이 예제에서 속성은 `Process` `Description` 명령에 멤버 이름 매개 변수로 전달 됩니다 `ForEach-Object` . 결과는 활성 프로세스에 대 한 설명입니다.

```powershell
Get-Process | foreach Description
```

이 예제에서 메서드는 `DirectoryInfo` `GetFiles` 명령의 멤버 이름 매개 변수로 전달 됩니다 `ForEach-Object` .  
검색 패턴 매개 변수를 사용 하 여 메서드를 호출 합니다 `.*` .  
결과는 `FileInfo` 사용자 홈 디렉터리에 있는 모든 Unix 스타일의 숨김 파일에 대 한 레코드입니다.

```powershell
Get-ChildItem /home -Directory | foreach GetFiles .*
```

## <a name="see-also"></a>참고 항목

- [about_Comparison_Operators](about_Comparison_Operators.md)
- [about_Foreach](about_Foreach.md)
- [Where-Object](xref:Microsoft.PowerShell.Core.Where-Object)
- [Foreach-개체](xref:Microsoft.PowerShell.Core.ForEach-Object)
